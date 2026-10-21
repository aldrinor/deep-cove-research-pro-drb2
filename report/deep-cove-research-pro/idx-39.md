# 普通摄像头面部视频生命体征监测：截至2024年初的技术、性能与公开数据集

**核心结论明确。**截至2024年初，普通摄像头面部视频测量中，心率（HR）的研究成熟度最高。血压（BP）和血氧饱和度（SpO2）已有明确的定量成果，但仍属于条件受限的估计技术。HR在部分公开基准上的平均绝对误差可低于2 bpm；BP在小型受控实验中的低误差，与医院数据中明显较大的误差并存；SpO2在正常范围内常见约1—2个百分点误差，但低氧范围表现明显下降。[1][2][3]

**研究精度有边界。**三类体征的关键区别，不只是算法复杂度。HR主要识别脉搏的周期；BP需要从波形或传播时间推断绝对压力；SpO2需要稳定的跨颜色通道信息。公开数据中的人群、运动、设备和异常生理范围覆盖，又进一步拉大了三者的验证差距。

| 问题 | 决定性结果 | 证据基础 | 当前判断 |
|---|---|---|---|
| 研究范围 | 普通RGB摄像头、面部视频；论文窗口2020—2023年 | 全球研究与公开基准 | 红外、专用成像另行分层 |
| HR性能 | PFE-TFA三库MAE为0.76、1.44、1.31 bpm | UBFC-rPPG、PURE、COHFACE | 研究成熟度最高 |
| BP性能 | Wu等SBP/DBP MAE为9.13/8.76 mmHg | 1,138人自建队列、受试者划分 | 绝对值泛化仍困难 |
| BP临床表现 | 医院数据SBP/DBP MAE为18.15/10.49 mmHg | 463个配对BP读数 | 低实验误差不等于临床替代 |
| SpO2性能 | VIPL-HR总体MAE/RMSE为1.012/1.473个百分点 | 受试者级70∶30划分 | 正常范围结果较好 |
| SpO2低氧表现 | VIPL-HR低于95%时MAE升至3.077个百分点 | 正常与异常范围分层 | 低氧验证是关键短板 |
| 数据集选择 | HR资源较多；BP、SpO2标签集中于少数库 | PURE、VIPL-HR、MMSE-HR、V4V、Vital Videos等 | 先按标签和条件选库 |
| 泛化风险 | TS-CAN跨库行走MAE达24.91—27.21 bpm | MMPD手机视频 | 内库低误差不能代表真实场景 |

表中性能分别来自PFE-TFA [1]、Wu等BP研究[4]、医院评估[2]、VIPL-HR血氧基准[3]和MMPD [5]。

**阅读路线如下。**下文先固定测量对象和指标口径，再分别比较HR、BP与SpO2的技术及关键论文。随后给出公开数据集目录，最后解释成熟度差异，以及数据集如何限制深度学习模型的跨主体、跨设备和跨数据集泛化。

## 一、研究边界与性能指标

### 1.1 普通摄像头究竟测到了什么

**核心输入是面部视频。**本文重点讨论智能手机前置摄像头、网络摄像头、笔记本摄像头及普通商用RGB摄像头。输入可以是完整人脸，也可以是额头、脸颊等感兴趣区域，即ROI。专用高速、多波段、近红外或热成像结果，只作为补充比较，不与普通RGB方案混合评价。[6]

**核心信号是血容量变化。**光电容积描记术简称PPG。心脏搏动改变皮肤浅层组织中的血容量，进而改变皮肤反射光。摄像头记录这些微弱变化，就形成远程PPG，即rPPG；相关研究也使用iPPG、vPPG或cPPG等名称。其恢复的脉搏波常称为血容量脉搏信号BVP。[7]

**三项目标并不等价。**恢复一个具有正确主频的BVP，已经能支持平均HR估计；但这并不自动证明能测准BP或SpO2。后两者还需要保留波形形态、通道幅度关系，或获得可靠的个体映射。

| 体征 | 主要视觉线索 | 典型推断过程 | 最敏感的信息 |
|---|---|---|---|
| HR | 周期性颜色变化或细微头动 | 脉搏主频、峰间距→每分钟搏动数 | 周期和峰位置 |
| BP | 多ROI时差、脉搏形态 | 特征或深度模型→SBP、DBP | 波形细节、时差、个体校准 |
| SpO2 | 不同颜色通道的脉动与基线 | AC/DC比、通道比或网络→血氧 | 跨通道幅度和光谱稳定性 |

上述机制分别见rPPG方法综述[7]和临床视觉监测综述[8]。

**运动路线也需区分。**心冲击描记术BCG利用血液循环引起的非自主细微头动。它与依赖颜色强度变化的rPPG不是同一种观测方式。BCG可提供心搏周期，但主动转头、说话和表情运动容易淹没微小机械位移。[9]

### 1.2 时间、地域与数据来源

**时间边界固定。**技术状态以2024年初为界，关键方法论文集中于2020—2023年。更早文献用于解释机制或数据集来源。2024年1月的公开数据综述用于校准概念和访问类型，不把后续新算法的成绩写入这一时间截面。[9]

**地域范围是全球研究。**本文纳入亚洲、欧洲、北美的算法与数据资源，也包含印度和英国的医院评估。全球适用性的判断，则取决于跨地区招募、肤色与年龄结构，以及统一协议下的外部测试。机构分布广，不等于受试者对全球人口具有代表性。[5][2][10]

**数据属性分开记录。**“公开数据集”包括直接获取和签署研究协议后获取两种情形；“自建”表示作者自行采集，并不自动表示公开。合成视频、接触式PPG和临床面部视频也分别记录。特别是MIMIC中的PPG、ECG和动脉血压，属于接触式生理数据，不是面部视频。[9][11]

### 1.3 怎样理解MAE、RMSE和“准确率”

**误差单位跟随体征。**HR以bpm，即次/分钟表示；BP分为收缩压SBP和舒张压DBP，单位为mmHg。SpO2读数以百分数表示，但两个读数之差宜写成“百分点”。例如97%与95%的差为2个百分点，而不是相对误差2%。

令参考值为 \(y_i\)，估计值为 \(\hat y_i\)，样本数为 \(N\)，常用定义为：

\[
\mathrm{MAE}=\frac{1}{N}\sum_{i=1}^{N}|\hat y_i-y_i|
\]

\[
\mathrm{RMSE}=\sqrt{\frac{1}{N}\sum_{i=1}^{N}(\hat y_i-y_i)^2}
\]

\[
\mathrm{MAPE}=\frac{100\%}{N}\sum_{i=1}^{N}\left|\frac{\hat y_i-y_i}{y_i}\right|
\]

这些定义及视频级HR评价见rPPG-Toolbox [12]。

**各指标回答不同问题。**MAE描述平均绝对偏差；RMSE对少数大误差更敏感；MAPE按参考值归一化。平均误差ME保留正负号，可能因正负误差抵消而很小。Pearson相关系数 \(r\) 或 \(\rho\) 为无量纲指标，只说明变化是否同步，不能代替绝对误差和一致性。

**准确率必须带阈值。**BP“误差小于10 mmHg的比例”，与HR“落在±5 bpm内的比例”，不是同一个指标。SpO2的Arms表示均方根准确度，也不等于“准确率为某个百分数”。Bland–Altman分析则报告平均偏差及一致性界限，用于观察个体测量差异。[13][14]

**本节判断。**后续比较优先对齐目标、指标、单位、参考设备和测试协议；不把三个不同体征的误差合成一个“总准确率”。

## 二、心率：公开基准最充分，但复杂条件仍显著退化

### 2.1 关键论文与定量结果

**HR已有多条成熟路线。**2020—2023年的主要进展包括时空表示、特征解耦、时序注意力、生成式增强、Transformer和轻量化网络。以下先列逐篇结果，再解释它们分别解决了什么问题。

表中的“条件bpm”表示：相关转载表给出HR误差数值，按HR采用bpm尺度进行条件性量纲标注；其数值不用于宣称跨论文的绝对最佳性能。

| 论文、作者与年份 | 核心方法 | 数据集及属性 | 划分与参考 | 关键性能 |
|---|---|---|---|---|
| Niu等，CVD，2020 | MSTmap、多任务、特征解耦 | VIPL-HR，公开 | 五折受试者独立；PPG/HR | MAE/RMSE 5.02/7.97 bpm |
| Lee等，Meta-rPPG，2020 | CNN-LSTM、元学习适配 | 自建训练；公开UBFC测试 | 2秒无标签适配；PPG参考 | MAE/RMSE 5.97/7.42，条件bpm |
| Liu等，TS-CAN，2020 | 双分支注意力、时间移位 | BP4D+→公开UBFC/PURE | POS伪标签训练；目标库PPG | MAE 4.69/1.29 bpm |
| Lu、Han、Zhou，Dual-GAN，2021 | BVP与噪声联合建模 | UBFC/PURE，公开 | 数据集内评估；PPG参考 | UBFC 0.44/0.67，条件bpm |
| Song等，PulseGAN，2021 | 生成对抗脉搏波重建 | UBFC-rPPG，公开 | 30/12主体协议；PPG参考 | MAE/RMSE 1.19/2.10，条件bpm |
| Hsieh等，RErPPG-Net，2022 | 擦除/嵌入、双循环增强 | 公开UBFC/PURE及Aug-rPPG | UBFC 35/7；PURE 7/3主体 | UBFC 0.41/0.56，条件bpm |

CVD数值来自Niu等原论文[15]。Meta-rPPG的方法来自Lee等原论文[16]，其表列结果以及Dual-GAN、PulseGAN和RErPPG-Net结果来自Hsieh等比较表[17]。TS-CAN为2020年方法，表列数字明确采用rPPG-Toolbox后续基准协议[12]。

| 论文、作者与年份 | 核心方法 | 数据集及属性 | 验证或实验条件 | 关键性能 |
|---|---|---|---|---|
| Yu等，PhysFormer，2022 | 时间差分Transformer | 公开UBFC-Phys | 2023再评测；讲话/算术 | MAE 11.89/12.85 bpm |
| Speth等，口罩研究，2022 | 3DCNN/RPNet、遮挡增强 | DDPM及MPM实验队列 | 指夹参考；真实口罩 | 3DCNN MAE/RMSE 3.73/9.65 bpm |
| Qiao等，ReViSe，2022 | 多ROI、BVP提取与滤波 | TokyoTech、PURE公开；Video-HR自建 | 20秒视频；参考生理设备 | MAE 1.73/3.95/2.49 bpm |
| Li、Yu、Shi，PFE-TFA，2023 | 生理特征、光流对齐 | UBFC、PURE、COHFACE，公开 | 正常面部分辨率；生理参考 | MAE 0.76/1.44/1.31 bpm |
| Liu等，EfficientPhys，2023 | 帧差归一化、轻量时空网络 | UBFC、UCLA、UBFC-Phys公开 | 2023统一再评测 | MAE 5.11/0.57/4.35 bpm |
| Lin等，视频放大研究，2023 | ROI跟踪、视频放大 | 自建面部/颈部视频 | 288段；Omron HEM-7124 | 偏差−0.2 bpm；r=0.988 |
| Talukdar等，Vastmindz，2022 | 面部BGR-rPPG、固定SDK | 医院自建队列 | 240个HR配对读数 | MAE/RMSE 3.09/5.72 bpm |

对应来源为PhysFormer原论文[18]、2023统一再评测[19]、Speth等口罩研究[20]、ReViSe [21]、PFE-TFA [1]、Lin等[22]和医院评估[2]。

**论文题目可直接定位。**Niu等的论文为《Video-based Remote Physiological Measurement via Cross-verified Feature Disentangling》；Lee等为《Meta-rPPG: Remote Heart Rate Estimation Using a Transductive Meta-Learner》；Liu等2020年方法为《Multi-task Temporal Shift Attention Networks for On-device Contactless Vitals Measurement》。三者分别代表解耦、适配和端侧时序建模。

**增强论文各有对象。**Lu等的《Dual-GAN: Joint BVP and Noise Modeling for Remote Physiological Measurement》建模脉搏与噪声；Song等的《PulseGAN: Learning to Generate Realistic Pulse Waveforms in Remote Photoplethysmography》重建波形；Hsieh等的《Augmentation of rPPG Benchmark Datasets: Learning to Remove and Embed rPPG Signals via Double Cycle Consistent Learning from Unpaired Facial Videos》扩展训练视频。[17]

### 2.2 传统方法仍是必要的比较对象

**传统路线无需训练。**常见流程是人脸检测与跟踪、ROI颜色平均、去趋势与滤波、信号分离，最后提取主频或峰间距。ICA寻找统计独立成分，PCA寻找主要变化方向；CHROM利用色度组合，POS将颜色信号投影到与肤色方向正交的平面。[6]

| 路线 | 主要处理 | 优点 | 典型边界 |
|---|---|---|---|
| GREEN | 绿色通道平均与滤波 | 实现简单、计算低 | 容易混入光照和运动 |
| ICA/PCA | RGB信号分解 | 不需生理训练标签 | 强周期噪声可能被选中 |
| CHROM/POS | 光学先验与颜色投影 | 可解释、无需训练 | 光谱、遮挡和大运动仍影响 |
| 学习式混合方法 | STMap或BVP加网络 | 可结合先验与非线性映射 | 依赖输入表示和训练域 |
| 端到端网络 | 视频到波形或HR | 联合学习时空特征 | 数据偏差与外部退化风险 |

**频率到HR有明确换算。**若脉搏主频为 \(f\) Hz，则：

\[
\mathrm{HR}=60f\quad\mathrm{bpm}
\]

因此0.75—2.5 Hz对应45—150 bpm；0.7—4 Hz对应42—240 bpm。不同带通范围会改变异常心率是否进入评价，也会改变噪声峰被保留的机会。[12][23]

**同协议下深度模型占优。**2023年的统一再评测截取每段视频中间16秒，降采样至20 fps，再使用0.75—2.5 Hz二阶Butterworth滤波。该条件下，EfficientPhys在三个常规测试集上的MAE均低于POS。[19]

| 测试集 | POS MAE（bpm） | EfficientPhys MAE（bpm） | EfficientPhys RMSE（bpm） | MAPE |
|---|---:|---:|---:|---:|
| UBFC-rPPG | 9.75 | 5.11 | 13.05 | 4.75% |
| UCLA-rPPG | 1.46 | 0.57 | 1.74 | 0.81% |
| UBFC-Phys T1休息 | 6.03 | 4.35 | 9.46 | 6.65% |

**优势不是恒定属性。**同一研究向UBFC-rPPG加入高斯噪声后，EfficientPhys的MAE从5.11升至19.69 bpm；POS为18.66 bpm。由此可见，原始测试条件中的优势，可以在输入退化后改变。这里比较的是指定噪声实验，不是所有真实噪声的共同规律。[19]

### 2.3 时空表示、解耦与适配解决了什么

**CVD改善了干扰分离。**Niu等将多区域、多尺度颜色变化构造成MSTmap，并同时监督平均HR与rPPG波形。跨验证特征解耦CVD旨在分离生理与非生理因素。在VIPL-HR消融实验中，加入完整多任务与解耦设计后，MAE由5.55降至5.02 bpm，RMSE由9.03降至7.97 bpm。[15]

**跨库证据比内库更重要。**同一方法在OBF的100名受试者、200段视频上进行十折受试者独立验证，RMSE为1.26 bpm，\(r=0.996\)。以VIPL-HR训练、直接测试MMSE-HR时，RMSE为6.04 bpm，\(r=0.84\)。前者是同库划分，后者才直接考验训练分布之外的表现。[15]

**Meta-rPPG改变部署适配。**Lee、Chen与Lee将模型拆为CNN特征提取器和LSTM估计器，再加入合成梯度与原型距离约束。其2秒warm-start允许模型用目标视频的无标签信息适应分布。该设计与“固定模型直接测试新用户”属于不同协议，比较时应保留这一适配条件。[16]

**元学习不等于免验证。**Meta-rPPG使用作者自采数据训练，并在公开MAHNOB-HCI和UBFC-rPPG评估。Hsieh等比较表引述的UBFC结果为MAE/RMSE数值5.97/7.42，相关系数0.53。该结果提供适配路线的性能锚点，但不能与采用另一主体划分的增强模型直接形成名次。[17]

### 2.4 生成增强扩展样本，但不扩展真实人群

**RErPPG-Net先擦后写。**Removal-Net先去除输入视频固有的脉搏变化，Embedding-Net再嵌入指定PPG。双循环一致性用于约束微弱生理信号与面部外观。Aug-rPPG由76段训练视频及对应信号组合，生成 \(76^2=5,776\) 段视频，来自42名原始受试者。[17]

**增强收益依赖目标域。**其UBFC训练到PURE测试的MAE/RMSE数值，从14.18/20.20降至4.36/6.69。按原表相同尺度计算，MAE相对降低约69.3%，即 \((14.18-4.36)/14.18\)。但UBFC与PURE训练后测试VIPL-HR，增强前后MAE数值为28.94与25.40，仍然较高。[17]

**低误差伴随划分差异。**RErPPG-Net在UBFC的主要结果采用35名训练、7名测试；PURE采用7名训练、3名测试。其UBFC“原始加增强”设置为0.41/0.56，\(R=0.994\)；PURE为0.38/0.54，\(R=0.96\)。同一论文使用UBFC 30/12主体划分时，误差数值又发生变化。这说明“哪个模型最低”必须附带主体列表和HR分布。[17]

**生成多样性有上限。**合成5,776段视频，增加的是视频—信号组合，而不是5,776名独立参与者。它能缓解训练样本不足，却不能自动补充老年患者、深色皮肤、疾病状态或新设备的真实光学响应。

### 2.5 对齐、Transformer与轻量化的取舍

**PFE-TFA针对空间变化。**Li、Yu与Shi的《Learning Motion-Robust Remote Photoplethysmography through Arbitrary Resolution Videos》使用PFE处理不同面部分辨率，再用TFA进行时序面部对齐。其正常分辨率设置下，UBFC、PURE和COHFACE的MAE/RMSE分别为0.76/1.62、1.44/2.50和1.31/3.92 bpm。[1]

**对齐保护同一皮肤区域。**头动会使固定像素在不同帧落到不同组织或背景。TFA利用光流缓解这种空间混合，跨分辨率约束则要求同一生理片段在不同尺寸下输出一致。它解决的是输入几何变化，并不等于已经解决所有光照和设备变化。

**PhysFormer强调长短时关系。**Yu等2022年的《PhysFormer: Facial Video-Based Physiological Measurement with Temporal Difference Transformer》使用时间差分注意力，结合标签分布学习和频域课程约束。其目标是强化局部与全局rPPG特征，而不是只增加网络规模。[18]

**再评测显示模型各有所长。**在2023年统一协议中，PhysFormer在UBFC-Phys讲话、算术任务上低于EfficientPhys；但在UBFC、UCLA和休息任务上，EfficientPhys更好。以下数字属于同一再评测，而非PhysFormer原论文四库成绩。[19]

| 条件 | EfficientPhys MAE（bpm） | PhysFormer MAE（bpm） | PhysFormer RMSE（bpm） | 较低MAE |
|---|---:|---:|---:|---|
| UBFC-rPPG | 5.11 | 23.81 | 27.96 | EfficientPhys |
| UCLA-rPPG | 0.57 | 9.23 | 11.53 | EfficientPhys |
| UBFC-Phys休息 | 4.35 | 12.89 | 15.98 | EfficientPhys |
| UBFC-Phys讲话 | 15.32 | 11.89 | 14.26 | PhysFormer |
| UBFC-Phys算术 | 15.65 | 12.85 | 15.76 | PhysFormer |

**EfficientPhys适合端侧研究。**Liu等2023年的《EfficientPhys: Enabling Simple, Fast and Accurate Camera-Based Cardiac Measurement》减少手工预处理，将帧差和可学习归一化纳入模型。其卷积与视觉Transformer设计面向移动和边缘计算。轻量化减少部署负担，但不会消除训练域偏差。[24]

### 2.6 口罩、情绪任务与临床读数

**遮挡直接减少信号像素。**Speth等《Remote Pulse Estimation in the Presence of Face Masks》采用指夹波形作为参考，并使用30秒滑窗FFT估计HR。3DCNN OF无口罩时MAE/RMSE为1.96/6.99 bpm，真实口罩时为3.73/9.65 bpm；同一真实口罩条件下，CHROM为12.59/16.34 bpm。[20]

**合成遮挡能部分缓解。**使用图案化合成口罩增强及Bulat标记器的3DCNN AB+P，在真实口罩视频上达到MAE/RMSE 3.55/8.75 bpm。收益来自训练时学习利用额头和眼周等保留区域，但还受人脸标记稳定性影响。[20]

**连续评价比平均值更严格。**Revanur等2021年的V4V挑战采用逐帧HR误差，而不是每30秒输出一个平均HR。V4V包含情绪诱发和显著头动，训练、验证、测试按受试者隔离。以下cMAE、cRMSE的bpm量纲由其帧级HR误差定义得到。[25]

| V4V方法 | 核心方法 | cMAE（bpm） | cRMSE（bpm） | cR |
|---|---|---:|---:|---:|
| Stent、Gideon，2021 | 自监督3DCNN、对比学习 | 9.22 | 14.18 | 0.47 |
| Hill、Liu、McDuff，2021 | Hybrid-CAN-RNN | 9.37 | 14.59 | 0.44 |
| Kossack，2021 | 多ROI质量选择、POS | 10.15 | 15.38 | 0.44 |
| Ouzar等，2021 | 3D深度可分离卷积 | 11.60 | 14.90 | 0.20 |
| GREEN基线 | 绿色通道处理 | 15.45 | 20.73 | 0.05 |

**V4V结果不能当纯架构赛。**Stent与Gideon的《Estimating Heart Rate from Unlabelled Video》包含测试阶段无标签学习；Hill等《Beat-to-Beat Cardiac Pulse Rate Measurement From Video》使用额外训练数据。挑战名次同时反映训练资源、适配和后处理，而不只是网络结构。[25]

**临床读数提供另一层证据。**Talukdar等2022年对固定Vastmindz 3.0 SDK开展医院评估，240个HR读数的ME、MAE、RMSE分别为−1.19、3.09、5.72 bpm。采集要求受试者静止正视、相机距脸60 cm，并提供至少250 lux环形补光。因此它是临床人群中的受控采集，而非自由活动监测。[2]

**一致性需要单独评价。**Lin等2023年《Estimation of Vital Signs from Facial Videos via Video Magnification and Deep Learning》在288段自建视频上报告HR相关系数0.988，平均差−0.2 bpm，一致性界限−4.0至3.6 bpm。这里的参考为Omron HEM-7124；相关性和一致性分别提供信息，不能互相替代。[22]

**本节判断。**HR最适合开展可复现基准与普通摄像头原型研究；实际部署能力仍应由讲话、行走、遮挡和新设备条件下的误差决定。

## 三、血压：受控误差已有进展，绝对压力与跨域验证仍是难点

### 3.1 关键论文与SBP、DBP性能

**BP必须分开报告双压。**同一模型可能在SBP和DBP上表现不同。以下统一按“SBP/DBP”顺序列数值，并将MAE与RMSE明确分开。

| 论文、作者与年份 | 核心方法 | 数据集及属性 | 验证与参考 | SBP/DBP性能 |
|---|---|---|---|---|
| Wu等，2022 | 双ROI CHROM、编码器—解码器、InfoGAN | 台湾自建rPPG，1,138人 | 961/177主体；水银血压计 | MAE 9.13/8.76 mmHg |
| Qiao等，ReViSe，2022 | 多ROI BVP、深度回归 | 公开PPG训练；Video-BP自建 | 视频端验证；同步医疗参考 | MAE 6.7/9.6 mmHg |
| Talukdar等，2022 | BGR-rPPG、Vastmindz 3.0 | 医院自建，463个读数 | 多设备BP参考；固定SDK | MAE 18.15/10.49 mmHg |
| Zhuang、Chen等，BPE-Net，2023 | 改进YUV、STMap切片、LSTM | MPM-BP私有，132人 | 五折；OMRON/Biopac | MAE 8.07/6.78 mmHg |
| InfoGAN扩展研究，2023 | 时间差、多模型、条件合成 | 自建rPPG；TVGH院内 | 与未增强方案比较 | 自建MAE 8.78/6.16 mmHg |
| 闫昊等，2023 | CDF、ICA、特征选择、SVR | MIMIC公开；视频自建5人 | 100组视频；BIOPAC MP160 | MAE 4.9/4.6 mmHg |
| Kim等，2023 | U-Net生成、迁移学习 | MIMIC-II公开；Leipzig 17人 | 5秒输入、8∶2划分 | MAE 6.90/4.43 mmHg |
| Lin等，2023 | 面部/颈部放大、特征、CNN | 自建原始视频；申请访问 | 测试集；Omron HEM-7124 | RMSE 4.11/3.75 mmHg |

对应来源为Wu等2022 [4]、ReViSe [21]、Talukdar等[2]、BPE-Net [13]、2023年InfoGAN扩展[26]、闫昊等[27]、Kim等[11]和Lin等[22]。

**跨库成绩应提前看。**BPE-Net的论文题目为《Remote Blood Pressure Estimation via the Spatiotemporal Mapping of Facial Videos》。其MPM-BP内部MAE为8.07/6.78 mmHg；MPM-BP训练、MMSE-HR测试的论文微调设定下，MAE为12.35/9.54 mmHg，RMSE为16.55/12.22 mmHg。[13]

**同体征比较仍需条件。**闫昊等的4.9/4.6 mmHg、Kim等的6.90/4.43 mmHg和Wu等的9.13/8.76 mmHg，都是MAE，却分别来自5人视频验证、17人迁移数据和177人独立测试队列。数值更低，不足以单独判定总体性能更强。

**补充证据**

| 对象 | 论文题名与引用信息 | 论文正式出版日期 | 出版类型 | 核心技术方法族 | 使用的数据集 | 数据集访问属性 | 性能指标记录（bpm或论文原始单位） | 验证协议 | 数据集证据状态 | 论文发表年份 | 论文目标体征 | 核心方法机制 | 性能指标名称 | 性能指标数值 | 性能单位 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2020—2023年HR关键论文集合 | 未找到证据 | 未找到证据 | 未找到证据 | 研究采用基于多ROI的RGB视频频谱分析：从右脸颊、左脸颊和前额提取心脏脉搏信号…[240] | 30 fps[240] | 30 fps[240] | 未找到证据 | 未找到证据 | 未找到证据 | 2022year[239] | 2022year[240] | 研究采用基于多ROI的RGB视频频谱分析：从右脸颊、左脸颊和前额提取心脏脉搏信号…[240] | 未找到证据 | 0.69bpm[240] | 未找到证据 |
| ReViSe: Remote Vital Signs Measurement Using Smartphone Camera | 未找到证据 | 未找到证据 | 未找到证据 | HR估计采用CHROM脉搏提取、合成时空特征图和ResNet-18回归；模型先用合成特征图预训练…[270] | Video-BP是ReViSe作者自建的视频数据集；该页没有提供公开下载、注册说明、官方仓库或完整访问入口…[282] | Video-BP是ReViSe作者自建的视频数据集；该页没有提供公开下载、注册说明、官方仓库或完整访问入口…[282] | 在UBFC的4秒、6秒和8秒非重叠窗口中，模型分别报告：4秒窗口HR MAE 1.72 bpm、RMSE…[235] | 处理流程包括ROI检测、脉搏提取、峰值检测和HRV计算；OpenFace用于获得面部二维标志点…[237] | 未找到证据 | 2022年[228] | BP的核心输入可为RGB摄像头捕获的面部肤色变化，或视频中不同面部区域脉搏波之间的时间差（PTT）…[214] | HR估计采用CHROM脉搏提取、合成时空特征图和ResNet-18回归；模型先用合成特征图预训练…[270] | 该研究的rPPG数据来自莱比锡大学医院的50名计划接受手术的受试者；使用工业USB摄像头IDS…[141] | 未找到证据 | 该研究的rPPG数据来自莱比锡大学医院的50名计划接受手术的受试者；使用工业USB摄像头IDS…[141] |
| Estimation of vital signs from facial videos via video magnification and deep learning | Lin等人的研究正式引用为：Lin B., Tao J., Xu J., He L., Liu N.… | 未找到证据 | Lin等人的研究正式引用为：Lin B., Tao J., Xu J., He L., Liu N.… | 该研究从单个面部视频提取面部和颈部两个ROI，自动检测、跟踪并放大ROI；将每个ROI划分为多个区块…[266] | 论文使用本文采集的原始面部视频数据；研究报告了HR、舒张压和收缩压，但本页未提供SpO2的实验数据…[266] | 论文使用本文采集的原始面部视频数据；研究报告了HR、舒张压和收缩压，但本页未提供SpO2的实验数据…[266] | 论文使用本文采集的原始面部视频数据；研究报告了HR、舒张压和收缩压，但本页未提供SpO2的实验数据…[266] | 处理流程包括ROI检测、脉搏提取、峰值检测和HRV计算；OpenFace用于获得面部二维标志点…[237] | 未找到证据 | 2023年[265] | 该研究从单个面部视频提取面部和颈部两个ROI，自动检测、跟踪并放大ROI；将每个ROI划分为多个区块…[266] | 该研究从单个面部视频提取面部和颈部两个ROI，自动检测、跟踪并放大ROI；将每个ROI划分为多个区块…[266] | Lin研究的HR性能证据为RMSE 5.33；来源未说明单位、测试分母、数据集或测试划分。[265] | r=0.988[278]；CI（−4.0,3.6）[278]；平均差0.2[278] | Lin研究的HR性能证据为RMSE 5.33；来源未说明单位、测试分母、数据集或测试划分。[265] |
| 2020—2023年关键研究论文候选集合 | 未找到证据 | 未找到证据 | 期刊论文[244]、arXiv预印本[257] | 页面指出，食物和运动等刺激会影响交感神经系统并升高血压；相关实验包括静息条件、运动活动…[120] | 未找到证据 | 未找到证据 | 49.39%[249] | 432,002datasets[249] | 页面呼吁在全球范围内收集具有较大多样性和规模的公开数据集，以使基于摄像头的生命体征监测足够稳健…[120] | 2020—2021年[107]、2022年[43]、2023年[179] | 页面记载，Zhou等人应用ICA和峰值检测识别波形的峰与谷，分别用于估计收缩压和舒张压。[120] | PhysFormer采用端到端视频Transformer架构，通过聚合局部和全局时空特征增强rPPG表示…[294] | 未找到证据 | 463[43] | 未找到证据 |

**HR：方法链与证据边界**

截至2024年1月31日，在普通RGB智能手机或网络摄像头拍摄的面部视频中，HR的主流路线是远程光电容积描记（rPPG）：心搏引起皮肤血容量和反射光的周期变化，系统从面部视频恢复脉搏相关信号，并以频谱峰值频率乘以60换算为bpm。[105]

典型流程为：人脸检测与跟踪→选择全脸、额头或脸颊等ROI→对ROI内RGB像素做空间平均→使用GREEN、CHROM、ICA、PCA或POS抑制肤色、光照和运动噪声→FFT/DFT及带通滤波→峰值检测得到HR。文献中给出的带通范围示例为0.65–3.5 Hz；非皮肤区域、遮挡和ROI漂移会降低信号质量。[105] 额头和脸颊通常提供较大的平坦皮肤区域；网络摄像头管线还可通过面部模型估计头部运动并进行滤波。[182]

深度学习路线包括CNN、RNN/LSTM和Transformer：CNN学习空间特征，RNN/LSTM建模时间上下文，Transformer通过多头注意力建模长程时空关系。[105] 进一步的路线包括MSTmap与生理/非生理特征解耦、PulseGAN的时频—对抗去噪、3DCNN对比学习，以及不依赖同步PPG标签的频率自监督学习。[183] 这些方法仍共享同一限制：rPPG信号幅度很小，容易受到头部运动、光照变化、摄像头差异、压缩和肤色影响。[183]

**2020—2023年论文发现线索。**允许使用的文献索引列出了Song等（2020，时空表示与CNN）、Zhang等（2020，视频加速放大）、Wang等（2020，消费级摄像头细节保持脉搏波提取）、Liu等（2021，MANet运动驱动注意力）、Ryu等（2021，头部运动状态估计）、Lee等（2022，移动成像PPG）、Li等（2022，短时面部视频深度学习rPPG）、Hu等（2022，时空注意力）、Das等（2022，2D-VMD）、Zheng等（2022，口罩面部视频）和Gao等（2022，信号质量注意力）等研究。[105] 当前片段仅提供这些条目的书目信息，没有逐篇给出MAE、RMSE或测试分母，因此它们只能作为候选导航，不能直接作为最终性能表中的合格论文证据。

本片段中可定位的数值证据包括：MetaPhys从18秒无标签视频进行个体化跨数据集适应，报告误差降低42%–44%；PulseGAN在UBFC-RPPG跨数据库测试中，AVNN的MAE相对DAE和CHROM分别改善20.85%和41.19%，SDNN的MAE分别改善20.28%和37.53%。这些是相对改善百分比，并非统一的绝对HR误差，不能与不同协议下的bpm数值直接排名。[183] Labvanced页面则声称其网络摄像头rPPG与实际HR的预期差异为1%–3%，但明确说明这是专有算法的预计值、尚未完成独立验证，因此不属于关键论文性能结果。[47]

验证条件会显著改变结果：一个网页所述实验包含25名受试者，并以BIOPAC ECG和PPG作参考；静止时rPPG与参考结果无差异，而进食造成的面部运动会产生偏差。[182] 另一项2022年摄像头验证协议使用距离面部60 cm、至少250 lux环形光源、每次扫描60秒，并要求受试者静止直视摄像头；低照度、明显头动以及低端摄像头的帧率和分辨率都可能造成信号失真。[49]因此，HR性能必须同时报告摄像头、ROI、窗口、参考设备和受试者独立划分；rPPG向BP或SpO2的扩展属于共享信号基础，具体性能应在相应体征章节单独讨论。[184]

在当前可核验的HR结果中，静止或高质量视频上的误差可低至1.3–1.64 bpm；加入头部运动、谈话、运动恢复、压缩或低照度后，误差可升至约4.76–7.5 bpm以上，说明HR性能高度依赖采集条件。[107][186]

| 研究（年份/状态） | 方法、数据集与属性 | HR性能 |
|---|---|---|
| **TSS：Heart rate estimation from facial videos with motion interference using T-SNE-based signal separation**（年份未在所示片段核验） | 人脸跟踪、空间像素平均提取RGB-rPPG，T-SNE分离脉搏向量与运动噪声，再以频谱峰值和FFT估计HR；使用自建数据集（25人、100段视频，Logitech C920，30 fps、640×480，PPG/指夹参考）及公开UBFC-RPPG、VIPL-HR。[107] | UBFC-RPPG：MAE **1.64 bpm**、RMSE **3.89 bpm**、ρ=0.94；VIPL-HR：MAE **4.76 bpm**、RMSE **11.03 bpm**、ρ=0.75；连续头动、圆周头动和运动恢复场景的MAE分别为**2.39、3.19、4.89 bpm**。[107] |
| **Face2PPG：An unsupervised pipeline for blood-volume-pulse extraction from faces**（arXiv:2202.04101，年份需由原始记录进一步核验） | 无监督面部归一化、动态ROI筛选和OMIT（基于QR分解的RGB-to-rPPG转换），针对噪声、伪影和视频压缩；在LGI-PPGI等多数据库上评估。[186] | LGI-PPGI中，Resting、Rotation、Talking、Gym场景MAE分别为**1.3±1.3、5.1±2.8、5.8±3.9、7.5±4.8 bpm**；对应RMSE为**1.7、7.6、7.5、11.1 bpm**。[186] |
| **Pulse rate estimation based on facial videos**（所示片段未核验出版日期） | 面部检测、8个局部ROI及融合ROI 9；比较ICA、Chrom、POS和Single Channel，采用Lab色彩空间、30 s窗口、FFT与SNR=0.3；数据包括公开PURE、COH、MCI、DEAP及自建MSSD。[109] | PURE的MAE为**1.763**、PCC=**0.989**、TPR=**0.949**；MSSD的MAE为**1.962**、PCC=**0.885**、TPR=**0.929**。所示片段未明确MAE的HR单位，故该单位标为**待核验**，不作严格横向比较。[109] |

另一个VIPL-HR端到端通道注意力与空间—时间注意力模型采用85名受试者的1,923段视频训练、22名受试者的455段视频测试；其受试者独立测试MAE为**5.40 bpm**、RMSE为**7.99 bpm**、MER为**6.70%**、相关系数为0.66。[106] VIPL-HR本身还包含107名受试者的2,378段彩色视频和752段近红外视频；MMSE-HR包含40名受试者、102段视频，HR真值由ECG计算。[106]

候选论文名录还包括2020年的*Detail-preserving pulse wave extraction from facial videos using consumer-level camera*、*RhythmNet*，以及2021年的*Detecting pulse rates from facial videos recorded in unstable lighting conditions*；所示证据仅提供书目信息，未提供完整性能数字，暂不作为最终数值条目。[107] *Cross-Verified Feature Disentangling*（2020）、*MetaPhys*和*EfficientPhys*（2021）、*Multi-ROI Spectral Approach*（2022）同样只能作为候选导航。[108] 2024年10月发表的SS-Net来源超出2024-01-31截止日，不能用于本报告的历史性能排名，也不能替代ReViSe的原始论文证据。[185]

**HR方法与定量证据（续）**

截至2024年初，HR的核心可观测信号是rPPG：血容量周期变化引起面部皮肤反射光变化；常见流程为人脸跟踪、ROI/皮肤分割、RGB或色度信号提取、滤波及时频分析，最后由脉搏周期计算HR。主流方法包括GREEN、ICA/PCA、CHROM、POS、PBV、LGI，以及监督式DNN/Transformer；自监督方法则可用频率增强和局部区域聚合减少对同步PPG标签的依赖。[110]

| 论文（年份） | 方法、数据集与访问属性 | HR测试结果 |
|---|---|---|
| *Video-based Remote Physiological Measurement via Self-supervised Learning*（2022） | LFA频率增强、REA局部rPPG专家聚合；使用公开UBFC-rPPG、PURE、DEAP和MMVS；采用5折受试者独立交叉验证 | UBFC-rPPG：MAE/RMSE/r=0.58/0.94/0.99；PURE：1.23/2.01/0.99；DEAP：4.20/5.18/0.90；MMVS：2.93/4.16/0.94（MAE、RMSE单位均为bpm，r为Pearson相关系数）。[110] |
| *ReViSe: Remote Vital Signs Measurement Using Smartphone Camera*（2022） | 智能手机面部视频的端到端rPPG框架；页面将HR数据集写作“this dataset”，名称、公开状态、参考信号和测试划分未报告 | HR MAE=2.49 bpm；完整测试协议未报告。[187] |
| *CPulse: Heart Rate Estimation From RGB Videos Under Realistic Conditions*（2023） | 面部质量子ROI、同态滤波、RGB绿色通道与LAB色度A通道、经验小波变换和PCA；PURE、UBFC、COHFACE为公开集，ASIPL为自建集 | PURE、UBFC、COHFACE、ASIPL的MAE分别为0.98、1.06、1.99、1.81 bpm；实验包含光照、运动和肤色变化。[189] |

同一自监督研究还报告：UBFC-rPPG含42段视频（640×480、30 fps），DEAP含22名受试者和874段视频（720×576、50 fps），MMVS含129名受试者和745段视频（1920×1080、25 fps，PPG采样60 Hz）。[110] 因此，上表结果支持“HR在公开基准和受试者独立测试下已较成熟”，但不能据不同数据集的MAE直接排名；真正的判定条件仍是跨设备、跨肤色、跨光照和真实运动场景验证。

2021年Yang等的HR结果为：PhysNet在UBFC-rPPG（Logitech webcam，640×480、20 fps，脉搏血氧仪参考、变光照）MAE=2.33 bpm；同实验比较GC、ICA、POS、CHROM。[190] 面部RGB-rPPG主链为ROI→GREEN/ICA/PCA/CHROM/POS→滤波/FFT；40–220 bpm范围理论最低约8 fps，常见30 fps、640×480。[190] 2021年另一框架报告ICA/CHROM/Green的HR百分比误差分别为7.56%、9.70%、15.87%。[191]

2023 PFE-TFA（光流+跨分辨率）公开UBFC/PURE/COHFACE：MAE/RMSE=.76/.78、1.44/1.62、1.31/1.44 bpm[194]；2023 GRGB/LGI-PGGI四条件|ΔBPM|=1.91/6.84/7.98/12.90（7.41）[115]；自适应子ROI-EEMD/PCA三集MAE=1.16/1.56/2.10 bpm[195]；ARPOS 40人RGB/IR/深度：静息HR RMSE7.8 bpm(r=.85)，活动13/15，SpO2 2.3/2.5%[192]；2023自监督rPPG五基准未报数值[193]

HR主流管线是面部ROI跟踪→RGB时序→ICA/CHROM/POS或2D/3D-CNN、Transformer→频谱/脉搏波。[116][196] CalibrationPhys（arXiv:2310.15043，2023预印本）采用自监督多摄像头对比学习与PhysNet-2DCNN；自建20人集使用C920n/Pixel 5（1920×1080、30 fps、50 cm，OxyTrue A参考），含静息、屏气、跺脚、说话任务；公开UBFC-rPPG跨集测试MAE=1.83 bpm、RMSE=3.77 bpm，手机测试MAE=4.28 bpm，预训练后为4.09 bpm。[116] FaSeNet研究在公开PURE上取得MAE=2.82 bpm；上述结果不能脱离各自协议横向排名。[196]

2022年TSS（T-SNE-based signal separation）以消费级摄像头面部ROI的RGB均值分离脉搏/运动噪声，再滤波+傅里叶估HR；自建25人100段（Logitech C920，30fps、640×480，PPG/指夹参考），并测UBFC-RPPG、VIPL-HR。MAE：突发/连续/环动1.08/2.39/3.19、恢复4.89、UBFC 1.64、VIPL 4.76 bpm。[117] ReViSe（2022）是智能手机面部端到端rPPG，目标含HR、HRV、SpO2、BP；所示资料未报告HR性能或数据访问属性。[197] WaveHRV（2023）面向HRV而非HR；小波散射+带通+IBI在UBFC-rPPG上的RMSSD/SDNN MAE为10.5/6.15 ms。[198]

HR链条：ROI→RGB(G)/CHROM/POS/ICA→BVP→滤波/频谱→bpm；心搏改变血容量和漫反射，深度路线含MSTmap双头回归。[63][68]  
2020 CNN时空图+合成rPPG迁移：公开MAHNOB-HCI跨库MAE5.98 bpm、误差率7.97%。[199]  
2022 LSTM误差3.26 bpm（G/ICA/POS=6.49/3.02/2.61），红外可用，数据集NR。[63]  
2023 ChPOS（CHROM+POS；公开UBFC-RPPG/PURE）MAE/RMSE=5.71/7.27、5.39/6.61 bpm；运动、光照和肤色会影响结果。[200]  
2023手机前摄自建10人、理想光照：60–90 bpm；Arms3.91、MAE3.24±2.11 bpm。[181] ARPOS（2022，RGB/IR/深度）家庭自建40人：HR RMSE7.8 bpm、r=.85；活动RMSE13 bpm。[201]  
VIPL-HR公开：107人/2378段/25–30fps，五折独立MAE5.02、RMSE7.97 bpm、r=.79；PURE公开：10人/60段/30fps/640×480、CMS50E、六头动。[68][100]

HR视频管线是“ROI检测/跟踪→颜色分解与滤波→BVP/rPPG→峰值或频谱估计”；方法包括GREEN、ICA/PCA、CHROM、POS，以及CNN/3D-CNN时空注意力网络。[120][205]绿光520–580 nm与血红蛋白吸收相关；低照度、距离增加、姿态/运动、遮挡和压缩会削弱信号。[120]

2020年候选包括 *Siamese-RPPG Network*、Hsu等的 *A Deep Learning Framework…*、Liu等的 *Detecting Pulse Wave…* 和 *HeartTrack*；2021年候选包括 ETA-rPPGNet、AND-rPPG。[120][202]本组证据仅给出题名、年份或方法，未给逐篇数值、单位、数据划分和参考设备，故均标为待核验线索。受控RGB研究概述的HR误差为 **<5 bpm**；2022年RGB面部模型以商用脉搏血氧仪为参考，PR（HR代理）偏差为 **−1.4 bpm**、精度为 **±3.1 bpm**。[120][121]

数据角色：TokyoTech Remote PPG为9名受试者、视频数未报告，RGB/NIR原型相机、300 fps、640×480、接触式PPG；PURE为10名、每人6项任务、视频总数未报告，640×480，综述记30 fps而官方页记60 Hz，使用指尖血氧仪、约1.1 m距离并含说话和头动。[120][203]UBFC-rPPG为42名；Dataset 2含46段、共享42段，C920、30 fps、640×480、CMS50E，室内混合光。[204]COHFACE为40名、20 fps、640×480、C525、BVP传感器和呼吸带；MAHNOB-HCI为27名、60 fps、780×580、RGB/ECG；VIPL-HR为107名，多设备25–30 fps、640×480至1920×1080、CMS60C。[120]这些固定小样本和设备条件便于复现，却不能证明跨设备、跨场景泛化。

自适应SSA在MAHNOB-HCI上MAE为2.05 bpm、RMSE为5.27 bpm（ρ=0.96）。[124]流程为ROI→RGB/绿色通道→ICA/PCA或CHROM/POS→FFT/带通→BVP→HR；深度模型采用CNN、STmap及时序学习。[206][207]

HR链：ROI→RGB/rPPG→滤波/FFT；传统GREEN、CHROM、POS、ICA，深度CNN/3D-CNN/时序注意力。rPPG捕捉心搏致肤色/血容量周期变化；常用0.7–4 Hz（42–240 bpm）、15–30 s窗。[208][125][127]

2104.02260（2021）：光流ROI+3D时空卷积；UBFC/COHFACE/自建集MAE=2.15/5.57/1.75 bpm；FaceBio-v1训/测240/60人，MAE=1.75 bpm；跨集UBFC/COHFACE的MAE/RMSE=2.15/3.82、5.57/9.50 bpm。[208]

V4V-ROI-POS（2021）：五ROI-POS、10 s窗；V4V的1,358段视频上MAE=8.324 bpm。[72]

照明评估（2021）：公开UBFC、受试者独立37/5段训练/测试；Physnet MAE=2.33（单位未报告）；中照下CHROM/Physnet MAE=1.04/5.37 bpm。[127]

GBR-HR（2023）：CHROM→GBR-BVP→ST-CNN；公开UBFC（42人、640×480、30 fps、CMS50E）MAR=4.75 bpm；自建UJN（13人）MAR=4.24 bpm，BVP相关均值CHROM/GBR=.586/.831。[126]

UBFC-rPPG另报50段视频（28–30 Hz、640×480；8段静止、42段算术游戏）；UBFC-Phys为56人/168段视频、35 fps、1024²，含休息/演讲/算术；运动、光照、压缩、遮挡会降低rPPG性能。[125]

HR主流管线为ROI颜色/色度信号、ICA/CHROM/POS及时空深网，再以频谱或回归输出HR[76][77]。2020年《Deep-HR》用ROI信号refiner和轻量DNN回归HR：公开MAHNOB（27人、527段、ECG）三折验证RMSE=3.41、r=92%；自建HR-D（75段、22 fps、800×480）RMSE=6.58、r=81%，RMSE单位均未报告[76]。2023年MMPD含33人、11小时/1152K帧手机视频，覆盖肤色、运动和光照；静止POS的MAE=7.69、RMSE=11.95、MAPE=11.45（单位未报告），完整集称现有方法难准确预测HR[77]。逆注意力+LSTM报告SNR最多增加5.8 dB、HR/BR误差最多降30%，且RGB→NIR无需重训[211]。Project_ICA（2019）、SAMC（2016）和MAR-rPPG（2024）仅作背景，不纳入2020—2023清单[75][210][209]。

HR：ROI→RGB→rPPG→PSD/FFT；Green、CHROM、POS、ICA/PCA；2020框架视频/真值10/7s。[130]PURE：10人、60段1min、30fps、640×480，CMS50E参考60Hz，含静止/说话/平移/旋转。[213]绿|ΔBPM|=7.17(PURE)/16.16(Talking)/3.31(Translation)。[212]

COHFACE上，DeepPhys（2020）HR的MAE约5 bpm，手工方法约15 bpm、POS约24 bpm[133]；面部ROI跟踪→颜色/rPPG→去噪抑制运动→波形重建，常用ICA、CHROM、POS及深度模型[215][134]。MMPD含33人、660段1分钟手机视频（30fps、同步PPG），含4种光照和4种活动[216]。

HR由普通面部RGB视频的rPPG估计，ROI、ICA/CHROM/POS、CNN和Meta-rPPG负责信号/时序处理；肤色、光照、运动会致域偏移。[217][85][222] Meta-rPPG（2020）在MAHNOB-HCI、UBFC-rPPG测试时自适应，但所示片段无数值，仅作方法线索。[85] Yang等（2021）在UBFC-rPPG（Logitech，640×480、20fps）用PhysNet得MAE=2.33bpm。[223] BH-rPPG（2022，35人、低/中/高照明、血氧仪参考）中照CHROM MAE=1.04bpm；亮度增强改善鲁棒性。[218] Visual HR（2022）性能未报告，不纳入数值表。[180] VIPL-HR/V2：107人、2378VIS/752NIR；500人、2500RGB/960×720；MMPD：33人、1152K帧，多域集难准确预测HR。[220][136][137]

普通RGB面部HR以rPPG为主：ROI→RGB/BVP→Green、CHROM、POS、PCA/ICA、FFT/PSD或CNN/3D-CNN。[224][225] 2021年Green/POS研究用OpenFace/HSV取ROI，滤波0.7–2.5 Hz；>500 lux、>30 fps且限制头动有利于HR/HRV。[226] 2022年多设备验证（60 cm、≥250 lux、60 s）HR样本n=240：ME −1.19 bpm、MAE 3.09 bpm、RMSE 5.72 bpm、RMSPE 7.43%。[86] 2023年HR-rtCNN用5个ROI、40帧（2 s）RGB/3D-CNN，在3个公开集和1个自建集测试，性能未报告；Li等（2023）在UBFC-rPPG、COHFACE、PURE上用PFE/TFA处理运动与分辨率，所给片段无数值，暂列候选。[225][147] PyVHR/Polar H10实验的HR MAE（明亮/中等/黑暗）为3.20/16.12/23.81，原片段未标单位；照明差异显著。[227]

Ramakrishnan等《Visual HR》（日期/类型未核验）：RGB面部光谱反射、Faster-RCNN/KLT/ICA；MAHNOB-HCI公开、Polar H10、60 FPS；μerror 4.1（单位未报）、RMSE 6.6%、≤5 bpm为94.1%、r=.86，10分钟每10秒RMSE 0.5%[234]。RePSS（2020 CVPRW）：VIPL-HR-V2/OBF各500、共1000个测试样本，BVP参考；Mixanik的MAE为6.94 bpm、RMSE为10.68 bpm、R=.75，OBF最佳MAE为2.56 bpm[148]。短时面部rPPG深度网络（日期未报告）：3D多尺度时空注意；OBF MAE/RMSE=.742/1.19 bpm，COHFACE=2.788/4.926 bpm，UBFC跨集=1.97/3.62 bpm；PHY-100为自建100人/100视频[235]。2021年《Evaluation...》采用OpenFace/HSV与Green/POS，3名健康男性、720×540 RGB+ECG；RRI MAE在固定、静止、说话条件下分别为23.9/26.1/53.9 ms[237]。Gupta–Etemad（2023）在PURE/UBFC采用区域提取、像素打乱和模糊，未报告HR误差，仅报告人脸识别准确率下降超过60%[238]。Antoniou等（2023）为食指贴镜头而非面部的范围外对照；VIPL-HR含107人、2378个VIS和752个NIR视频，但实际公开状态未核验[233][236]。

- **Molinaro等，*Multi-ROI Spectral Approach*（2022）**：iPhone6s RGB面部多ROI（双颊/额头）rPPG，比较Green、modwtmra、CHROM、POS、ICA、PCA；18人、4×约90 s、0.5/1.0 m及自然/人工光，BioHarness ECG 250 Hz；自建、仅按请求获取。MAE 0.7–6 bpm、RMSE 1.2–9.11 bpm；POS在0.5 m补光下MAE 0.65 bpm；未覆盖肤色和运动伪影。[240]
- **Vastmindz/Cureus（2022）**：普通摄像头rPPG临床评估，463人；扫描60 s、距离60 cm、光照≥250 lux，受试者静止直视，医疗设备作参考。HR有效样本\(n=240\)：ME −1.19、MAE 3.09、RMSE 5.72 bpm，RMSPE 7.43%。[43] 另有203人手机Face PPG实验，相对心脏监护仪的HR误差为：Xiaomi N9 5.758、N8 −2.103、Oppo 0.362、Samsung M31 1.982 /min（bpm）。[239]
- **频率启发式自监督研究**：以空间增强生成正样本、频率增强生成负样本，并用局部rPPG专家聚合；在UBFC-rPPG、PURE、DEAP、MMVS和BP4D+上进行5-fold受试者独立评估，MAE/RMSE/r依次为0.58/0.94/.99、1.23/2.01/.99、4.20/5.18/.90、2.93/4.16/.94和3.22/4.47/.91（片段未显示单位，待核验）。PURE为10人、60视频、30 fps、640×480、PPG 60 Hz并含六类头动；UBFC为42视频、30 fps、640×480。[149]
- **CalibrationPhys**正式出版标为2024，排除出2020—2023论文表；其跨集UBFC-rPPG测试MAE 1.83 bpm、RMSE 3.77 bpm（自建20人训练、公开42人测试，10 s窗）。[241]
- 其他候选包括RhythmNet、Meta-rPPG（2020）、Dual-GAN/PulseGAN/ETA-rPPGNet（2021）、PhysFormer（2022）及PhysFormer++/Arbitrary-Resolution（2023）；本片段仅有书目、无逐篇性能数值，暂待原文核验。[149]

Lie等人（2023-07-01，《Heart Rate Estimation from Facial Image Sequences of a Dual-Modality RGB-NIR Camera》）以MASF、WD、RPCA和ICA提取面部rPPG；公开PURE与自建CCUHR。CCUHR（22人、116段、640×480、30 fps、BIOPAC PPG 100C参考）10/20 s视频的MAE/RMSE为4.45/6.18 bpm；PURE 60 s RGB视频为3.24/4.10 bpm；CCUHR无运动与运动20 s分别为2.79/3.85和6.27/8.83 bpm。[242]

《Learning Motion-Robust Remote Photoplethysmography through Arbitrary Resolution Videos》使用PFE、TFA和cross-resolution constraint，在UBFC-rPPG、PURE、COHFACE上以160帧非重叠片段评估，MAE/RMSE分别为0.76/1.62、1.44/2.50、1.31/3.92 bpm；该页未报告出版日期和类型。[245] 其数据背景为：UBFC-rPPG有42段、每段约2 min、PPG参考采样60 Hz；PURE有10人60段、六种头动；COHFACE有40人160段1-min视频，含studio/natural light并经MPEG-4重压缩。[245]

Talukdar等（2023-04-03，medRxiv预印本）从额头及双颊RGB ROI经POS和卷积滤波估计HR；UCLA视频与指夹脉搏血氧仪同步，过滤后339个样本、90名受试者，整体MAE为3 bpm；Fitzpatrick 1–2、3–4、5–6组MAE分别为2.53、3.05、3.79 bpm。数据描述报告98人489段，而方法段报告498段；数据须联系作者并可能签署使用协议。[247]

普通笔记本网络摄像头的HSV-Hue前额频谱法在25名健康受试者、每人20 s面部视频上测试；640×480、30 fps（实时处理约9 fps），以Hexoskin ECG作HR参考，100 s采集、每5 s比较，HR RMSE为2.9558（结论写作2.95）。[248]

HRVCam（2021）和WaveHRV（2023）主要测HRV而非HR：HRVCam采用iPPG、PFDM、自适应带通滤波和DESA；16人、30 fps、脉搏血氧仪60 Hz，覆盖静坐、阅读、观看和交谈，交谈场景SDNN MAE为9±8 ms、RMSSD为14±11 ms。[252] WaveHRV以FaceMesh、皮肤分割、meanRGB、POS、Wavelet Scattering和IBI分析，在UBFCrPPG上RMSSD MAE为10.5 ms、SDNN MAE为6.15 ms。[246]

ReViSe（Qiao等，IEEE Access 2022）采用智能手机面部视频和rPPG；其PURE对比表报告MAE=3.95 bpm，RMSE未报告。[242] 仅有题名或无原始数值的候选包括Song等2021、Villarroel等2020、AutoHR、HeartTrack、DeepHeart、Deep-HR、PhysFormer、PhysFormer++、TransPPG及2023年E-Health研究；不作为核心性能行。[244][251][253][254] Bae等2022虽报告MAPE=1.6%±4.3%，但输入是手指接触后置摄像头；2019年高度压缩视频论文亦不在2020—2023窗口内。[243][250]

2020候选VITAL=54人/432视频，误差未报告；2021合成增广：MMSE-HR深肤10%，MAE降31%、偏差缓解46%。[53][257]

2021 webcam：JBSS+反射投影/绿通道FFT；30 fps/640×480，18浅肤+10深肤、指夹10 s；静止/恢复/摆头/HCI的MAD/RMSE=6.76/10.01、23.42/23.42、7.26/9.72、6.86/10.67 bpm。[255]

ReViSe（2022）：手机rPPG→地标/多ROI/BVP滤波；TokyoTech/PURE的HR MAE=1.73/3.95 bpm，日常Video-HR的MAE=2.49 bpm。[153]

PhysFormer++（2023）：SlowFast时差Transformer；VIPL-HR受试者独立5折MAE/RMSE=4.88/7.62 bpm，大幅摆头RMSE=10.25 bpm；UBFC跟踪比较（2023）中42人、30 fps/640×480，MPFM最佳，示例109.98对110 bpm。[258][256]

Green/POS条件研究：30 fps、500 lux下RRI-MAE=23.9/26.1/53.9 ms（固定/静止/说话）；EVM+R视频研究（2022）含5人45段，视频-PPG平均误差<1 bpm、RMSE=1.0971 bpm；小样本、自然光和整脸ROI限制泛化。[260][259]

ReViSe（Remote Vital Signs Measurement Using Smartphone Camera，2022，arXiv）采用手机面部端到端rPPG：深度关键点→多ROI→BVP滤波；TokyoTech、PURE为公开集，Video-HR为日常生活自建集；HR MAE分别为1.73、3.95、2.49 bpm。[262] 2023年RGB-NIR（非纯RGB）面部HR论文采用MASF/小波/RPCA/ICA；PURE公开、CCUHR/RealSense自建：CCUHR（10/20 s）MAE/RMSE=4.45/6.18，PURE（60 s RGB）=3.24/4.1 bpm。[154] PURE公开集上的PulseGan（2021）、EfficientGAN（2022）、SA-F（2022）为DL方法；RMSE/MAE分别为4.29/2.28、2.30/1.83、2.83/2.13 bpm，题名/协议NR。[154]

ReViSe（Qiao等，2022年6月13日提交、12月22日修订的arXiv预印本）以智能手机面部视频为输入，采用端到端rPPG流程：深度网络实时定位面部标志点，提取多个ROI，再用滤波器抑制BVP信号噪声；目标包括HR、HRV、SpO2和BP。[263]

| 研究 | 数据集属性与方法 | 已报告结果 |
|---|---|---|
| ReViSe（2022） | TokyoTech rPPG、PURE：公开数据集；Video-HR：作者在日常生活环境中自建；BP训练使用未命名的指尖传感器数据，测试使用自建Video-BP。[263] | TokyoTech HR MAE **1.73 bpm**、PURE HR MAE **3.95 bpm**、Video-HR HR MAE **2.49 bpm**；PURE SpO2 MAE **1.64%**；Video-BP的SBP MAE **6.7 mmHg**、DBP MAE **9.6 mmHg**。[263] |

ReViSe还报告TokyoTech和PURE上的HRV MAE分别为**18.55 ms**和**25.03 ms**；HRV不是本节的HR误差。摘要未报告HR测试分母、受试者独立性、窗口和参考设备；Video-HR的受试者数、视频数、规格、标签和下载状态也未核实。PURE的SpO2视频子集及参考设备、Video-BP的校准和详细测试协议同样未报告。[263]

Lin等人的原始论文为“Estimation of vital signs from facial videos via video magnification and deep learning”（iScience，2023年9月6日），采用面部ROI自动检测、跟踪与放大，从稳定波形提取HR、PTT和脉搏波形特征，再由小型CNN估计BP。[162]后截止汇总将其数据记为Private（288个视频），并列出HR、SBP、DBP的RMSE为**5.33、4.11、3.75**；但该汇总未说明三值之外的单位、测试分母、参考设备或划分，故暂标为待原文核验，不与上述带单位结果横比。[265]

后截止综述仅提供候选线索：Siamese-rPPG Network（2020，双3D-CNN）、AutoHR（2020）、PulseNet（2022，皮肤分割与注意力）、PhysFormer++（2023，SlowFast时差Transformer）、Yue等的自监督学习和Zhao等的全局—局部时空脉搏表示；本组片段未给出可核实的数值性能，故不作为核心性能行。[264]

Lin等（2023，iScience）用面部/颈部ROI自动跟踪放大，分块灰度序列经PCA取稳定波；HR融合双ROI，特征入小型CNN估BP[266]。自建视频以Omron HEM-7124为参考；288段视频HR RMSE=2.13 bpm、MAPE=2.85%、r=.988；SpO2数据集、公开性及独立划分未报告[266]。

ReViSe（Qiao等，2022，IEEE Access）以智能手机面部视频做rPPG：标志点→多ROI→BVP滤波→Welch-PSD估HR；TokyoTech、PURE公开，Video-HR自建。三者HR MAE依次1.73、3.95、2.49 bpm；PURE的SpO2 MAE=1.64%，结论另报1.60%，未统一[267]。BP以公开PPG训练、Video-BP验证[267]。

Video-HR含15人（10–80岁），每人2段20秒，Galaxy Note9、iPhone 6s/X/11 Pro；日常环境、不同光照/姿势，脉搏血氧仪作参考，未见公开下载证据[267]。TokyoTech为9人、三段1分钟再切20秒，cPPG 2048 Hz；低噪声下HR MAE=1.73 bpm、HRV MAE=18.55 ms[267]。另表报9段、20–29岁、300 fps/640×480，口径冲突，不合并[268]。

HR链为人脸/ROI→rPPG→频率/峰值检测；GREEN、ICA/PCA、CHROM、POS为经典方法，端到端/混合深度模型需大量数据且难验证[155]。Lin实验光照理想，未覆盖低/不均匀光照；运动、相机噪声和数据不足限制泛化[266]。

HR：ReViSe（2022）MAE2.49bpm[269]。

PURE静止RobustPPG RMSE1.56bpm[271]

ReViSe（2022预印本）：手机面部视频→ROI/BVP→HR、SpO2、BP；BP=ResNet三分支（BVP及一/二阶导数）+迁移。[156] HR MAE（公开TokyoTech/PURE/自建Video-HR）=1.48/4.20/2.49 bpm；PURE SpO2=1.60%；Video-BP测试集SBP/DBP=6.7/9.6 mmHg；BP训练指尖集名称/公开性未报告。[156] TokyoTech/PURE：9/10人、3×1min/60段、PPG2048Hz/视频30fps·640×480、六动作；Video-HR：15人、2×20s、日常光照、非公开。[156] DRP/BBP用面/腕相位rPPG；MMSE-HR/V4V的HR MAE=1.78/3.83 bpm，SBP/DBP=10.19/7.09、13.64/9.4 mmHg。[272] ResNet PPG独立/混合SBP/DBP MAE=16.4/8.5、7.7/4.4；rPPG微调/个体化SBP=14.1/12.7 mmHg。[141]

HR：rPPG提取脉搏；POS四类活动中3类最佳[157]

ReViSe：面部rPPG；HRMAE2.49bpm[274]；BP自建SBP/DBPMAE7.9/5.8mmHg[230]

ReViSe（Qiao等，2022；智能手机面部视频）用人脸关键点、多ROI及滤波BVP估计HR；TokyoTech/PURE（公开）HR MAE=1.73/3.95 bpm，PURE SpO2 MAE=1.64%（%口径未明）；日常环境自建Video-HR的HR MAE=2.49 bpm，BP另用指尖信号/Video-BP。[276]

TokyoTech：9人；放松—握力—放松各60 s，指夹PPG 2048 Hz，闪光同步偏移0.32 s，EULA取数；视频数、帧率和分辨率未报告。[277]

HR方法主族为BSS/ICA、CHROM/PBV/POS及CNN/Transformer；弱rPPG受运动、光照和肤色干扰。[161] 双模态RGB-NIR研究结合皮肤分割、滤波、ICA和FFT，在CCUHR（10/20 s）MAE/RMSE=4.45/6.18 bpm、PURE RGB（60 s）=3.24/4.10 bpm；前者不等同普通RGB。[275]

UBFC-rPPG：42人42视频，640×480、约1 m、数学游戏/自然运动；CK（10 s窗、5 s重叠）MAE=2.292、RMSE=3.803 bpm。[161] 自建集仅15名亚洲受试者、450段视频/ECG（2.7K/30 fps，0.5—3 m）；240p/2.7K中位RMSE=2.4—12.8/1.4—4.6 bpm。[161]

Lin等2023仅确认视频放大、CNN和面部ROI，HR数值未报告；其他候选目前仅有题录，不能以题录替代性能。[273]

ReViSe（2022）以智能手机面部视频、标志点多ROI和滤波提取BVP；TokyoTech/PURE的HR MAE分别为1.73/3.95 bpm，Video-HR为2.49 bpm[280]。Lin等（2023）用面颈ROI视频放大、PCA和两阶段小型CNN；288样本HR与Omron HEM-7124的r=0.988；数据按请求提供，未报告SpO2[278]。

ReViSe（2022预印本；来源日期为13 Jun/23 Dec）以智能手机面部视频作rPPG：landmark→多RoI→滤波BVP；HR/HRV/SpO2用公开TokyoTech、PURE，BP用未命名指尖信号集训练并自建Video-BP。[281][282] HR MAE为TokyoTech 1.73、PURE 3.95、日常Video-HR 2.49 bpm；PURE的SpO2 MAE为1.64%（百分比/百分点、血氧仪、范围、分母和划分未报告）；Video-BP的SBP/DBP MAE为6.7/9.6 mmHg（测试范围、参考设备和分母未报告）。[282][283]

TokyoTech含9人（8男1女，20–60岁），三段1 min视频切为3×20 s，exercise前握力，指夹cPPG采样2048 Hz；实验室噪声较低，HR MAE为1.73 bpm。[283] PURE含10人（8男2女）、60×1 min序列（59可用），30 fps、640×480、距1.1 m；CMS50E同步记录PPG/SpO2（60 Hz），日光受云层影响，含静止、说话、平移和旋转，脉搏42–148 BPM且均静息。[284][285] Video-HR为自建15人（10–80岁），每人2×20 s，使用四种手机、不同光照/活动姿势并同步脉搏血氧仪；公开状态未说明。[283]

MMPD含33人、11 h/1152K帧，覆盖肤色、身体运动、光照及8类标签；full为370G、320×240，mini为48G、80×60，仅限学术使用。[286]最简单场景（单位未注明，依次MAE/RMSE/MAPE/Pearson）：ICA 8.75/12.35/12.26/.21；POS 7.69/11.95/11.45/.19；TS-CAN(PURE) 1.78/3.57/2.47/.93；TS-CAN(UBFC) 1.46/3.13/2.04/.94。全集POS、PhysNet(PURE)、PhysNet(UBFC)分别为12.34/17.70/14.43/.17、13.22/19.61/14.73/.23、10.24/16.54/12.46/.29。[286]

2021年《Contactless Heart Rate Estimation From Facial Video Using Skin Detection and Multi-resolution Analysis》采用CNN皮肤检测+DWT，在UBFC-rPPG上MAE为5.32 bpm；2023年《Heart Rate Estimation From Remote Photoplethysmography Based on Light-Weight U-Net and Attention Modules》采用MSTmap、SE和多头注意力，RMSE为0.78 bpm、相关系数为0.99。[46]2020年Gudi等《Real-time webcam heart-rate and variability estimation…》在本片段仅为线索，未提供性能。[283]

2022 ReViSe以面部视频rPPG提取BVP；公开TokyoTech/PURE的HR-MAE为1.73/3.95 bpm，日常自建Video-HR为2.49 bpm[292]

2023年HR：网络摄像头rPPG，MAE2.8bpm[170]

HR：RGB面部ROI→Butterworth→FFT/ICA/PCA；FastICA准确率额头92.67%、脸颊92.33%（10名男性、webcam0.8m、2021）[229]。运动/光照致噪声[229]。SB-CWT在MMSE-HR 101段：SNR 6.63–10.39 dB、R² 0.81–0.91[231]。MMPD（2023）33人/660个1分钟手机视频，30 fps、1280×720→320×240，PPG；肤色3–6、静止/转头/说话/走动，肤色4–6的MAE>10（单位NR）[174]。公开UBFC-Phys：56人、每人3视频，BVP/EDA 64/4 Hz，休息/演讲/算术[287]。

2022年，TS-CAN（时间移位注意力网络）在PURE的HR MAE为3.69±1.74 bpm。[288]

rPPG以普通RGB摄像头逐帧汇总面部ROI颜色；方法包括GREEN、ICA、CHROM、POS、SSR、PBV、LGI。CHROM抑制反射噪声，POS投影到肤色正交平面，PBV区分脉搏颜色变化与运动噪声；脸颊、前额为较优ROI。[164] ROI评估在UBFC上POS/CHROM的MAE为1.85/1.50、PCC为0.80/0.87；LGI-PPGI上MAE为3.61/2.93、PCC为0.34/0.59，MAE单位未报告。[164]

2020年Boccignone等《An Open Framework》为方法评估框架；Sahin等（2021）用面部视频颜色强度测HR，Kim等（2020/2021）用非接触传感器迁移学习或移动端面部图像系统，但这些条目均未提供可核验HR数值，仅作候选。[164] Niu等（2020）交叉验证特征解耦方法使用VIPL-HR，代码支持MSTmap和面部关键点检测，性能未报告。[221]

UBFC-rPPG含50段视频（静止8、数学游戏42），30 fps、640×480、约1 m，CMS50E提供PPG/脉搏率/SpO2参考，人数未报告。[279] COHFACE含40人、160段1分钟RGB序列，20 Hz、640×480，同步BVP和呼吸率。[289] 编码、非均匀光照及仅Fitzpatrick I–II样本限制泛化。[164]

MAHNOB27人/527视频/61fps/AV偏.5s[232][290]；VIPL107人/2378VIS+752NIR/9条件[293]；MMPD33人/1152K帧/ICA/POS/CHROM=18.57/12.34/13.63bpm[291]

HR18年RMSE7.4bpm；79.2%<5bpm[165]

Video-HR是ReViSe为日常生活环境HR验证创建的自建数据集，包含15名参与者、每人两段20秒面部视频，并同步用脉搏血氧仪取得参考HR；其HR MAE为2.49 bpm。[156][280] 所给证据未确认官方下载或访问状态，因此应作为自建验证集单列，不能未经核验列入公开数据集主表。[262][250]

HR已有重复基准、较大样本和真实环境证据：ReViSe在TokyoTech、PURE和Video-HR上的HR MAE分别为1.73、3.95和2.49 bpm；另有107名受试者、2,378段视频及5-fold验证记录。[280][68][272] 但数据集、分割分母和受试者独立性并未统一报告，且跨数据集测试会明显退化，所以这些结果支持HR验证链较成熟，却不能组成同一口径的普遍排行榜。[242][156]

ReViSe把智能手机面部视频与rPPG端到端连接起来：实时提取面部地标和多ROI，滤波得到BVP，再统一估计HR、HRV、SpO2和BP，目标是日常生活中的低成本非接触监测。[156][274] 它不是只验证HR，而是以HR为较成熟入口，将同一前端扩展到血氧和血压。[267]

TokyoTech、PURE、UBFC-rPPG和COHFACE等基准为论文复现提供视频—生理参考对：PURE含10人、60个1分钟序列，视频30 Hz、640×480、参考60 Hz；UBFC-rPPG列有50段、30 fps、640×480，COHFACE列有40名受试者。[213][279][120] 相比之下，Video-HR是日常环境的自建验证集，含15名参与者、每人两段20秒视频、脉搏血氧仪HR标签，MAE为2.49 bpm；其访问状态未核实，应与已确认公开集分开。[156][262]

候选公开名录可按下载入口、许可证、参考信号和任务条件筛选复现基准：UBFC-rPPG提供完整下载及读取脉搏血氧仪真值的实现，rPPG-Toolbox列出多种基准，COHFACE也有明确取数入口。[204][205][289] 但MMSE-HR许可证被标为Unknown，MAHNOB-HCI视频因共享权利不能提供，因此名录出现不等于每个数据集都能直接复现。[219][290]

ReViSe在本调研中充当普通手机面部视频的端到端示范：面部地标确定多ROI、滤波提取BVP，并在TokyoTech、PURE及日常Video-HR上验证HR，MAE分别为1.73、3.95和2.49 bpm。[262][156] 同一框架把BVP用于BP和SpO2，从而把HR的成熟前端、数据集角色和跨体征扩展放在同一验证链中。[261][280]

技术性能上，HR主流链条是颜色/ROI信号、滤波或BSS、FFT/频谱峰，GREEN、ICA、CHROM、POS、视频放大及深度模型并存；ReViSe在TokyoTech、PURE和Video-HR上的HR MAE为1.73、3.95和2.49 bpm，PURE上的SpO2 MAE为1.64%，而BP以BVP及其一、二阶导数经三分支ResNet回归SBP/DBP。[120][156][280] 逐篇表格应把方法、公开或自建数据集、协议、指标和单位绑定记录：HR用bpm、SpO2用百分比、SBP/DBP用mmHg，并保留脉搏血氧仪或PPG参考，不能把不同体征的误差直接混比。[156][280]

横向比较必须同时保留指标、单位、数据集、窗口/分母和协议：ReViSe的HR MAE为TokyoTech 1.73、PURE 3.95、Video-HR 2.49 bpm，但公开实验室集与日常自建集条件不同；材料还记录了5-fold验证，且跨数据集性能会明显下降，不能据此排列统一排行榜。[280][156][272][242] 本节宜按技术与性能、公开数据集、综合泛化限制展开：HR/rPPG提供信号链，候选集发现研究，ReViSe提供跨体征数值，Lin的2023年私有288段视频补充视频放大加CNN的BP路线。[154][265][278]

Lin等人的2023年论文使用私有288段视频，以面部/颈部视频放大、PCA稳定片段和小型CNN估计HR、PTT、SBP和DBP，并报告HR相关系数r=0.988；TokyoTech和PURE是公开rPPG基准，ReViSe在其上的HR MAE分别为1.73和3.95 bpm、PURE的SpO2 MAE为1.64%。[265][278][280] Video-HR则是作者在日常环境建立的自建集，含15名参与者、每人两段20秒视频、脉搏血氧仪HR参考和2.49 bpm MAE，适合真实场景验证但不应当作已核验公开集。[156][262]

公开数据集名录可用下载、许可证、参考信号和任务条件筛选复现集：UBFC-rPPG有下载和读取脉搏血氧仪真值的实现，rPPG-Toolbox列出多种基准，但MMSE-HR许可未知、MAHNOB-HCI视频不能共享。[204][205][219][290] 论文候选集可把HR、BP和SpO2分别填入方法—数据集—指标表；现有证据最充分的是HR的1.73、3.95、2.49 bpm和SpO2的1.64%，BP可确认BVP/导数—ResNet路线，但不能用缺失的逐篇数值补表。[280][156][107][154]

rejected: citation_outside_operands；心率（HR）的Pulse Rate Detection (PURE) dataset仅含10个人、60个1 min的序列（30 Hz、640×480像素、60 Hz参考）；参考信号噪声和跨数据集性能下降会使深度模型学习设备/场景捷径，削弱外部泛化。[213][246][242]

rejected: citation_outside_operands；心率（HR）是远程光电容积描记术（rPPG）在普通面部视频中的直接目标：面部ROI的RGB变化经盲源分离、频谱分析和峰值检测得到脉搏频率并换算为bpm；这条链构成HR技术、数据集验证和泛化分析的前端。[105][106]

rejected: citation_outside_operands；远程光电容积描记术（rPPG）从面部ROI的颜色变化恢复BVP，随后用频谱或模型把信号用于生命体征估计；面部归一化、动态ROI和基于QR分解的OMIT分别稳定位置、剔除噪声并增强对压缩伪影的鲁棒性。[186][188][184]

rejected: no_entity；2020—2023年关键研究论文候选集合可按2020—2023年HR关键论文集合、2020—2023年BP关键论文集合和2020—2023年SpO2关键论文集合分别记录方法、数据集及性能，并用跨数据集训练—测试筛选候选。[107][149]

rejected: no_entity；Estimation of vital signs from facial videos via video magnification and deep learning于2023-09-06从面部和颈部ROI形成时间序列并用PCA盲源分离，使用自建288 videos，补充了普通摄像头面部视频的生命体征估计路线。[266][265]

rejected: citation_outside_operands；Video-HR dataset仅有15 participants、two 20 seconds face videos，HR MAE为2.49 bpm；ReViSe的跨数据集性能显著下降，参考信号噪声进一步削弱外部泛化。[156][267][242][246]

rejected: citation_outside_operands；MAHNOB-HCI dataset包含27 subjects、20 frontal face videos、527 videos、61 fps；公开数据集的真实场景覆盖、参考标签质量和跨域可比性受限，VIPL-HR dataset的压缩、昏暗光照、头部运动和说话会加重这一问题。[232][246][242]

rejected: citation_outside_operands；Estimation of vital signs from facial videos via video magnification and deep learning的私有288 videos和理想光照协议，加上ReViSe的跨数据集测试性能显著下降，会使深度模型学习摄像头/场景捷径而非可迁移生理特征，限制外部泛化。[266][242]

rejected: citation_outside_operands；Estimation of vital signs from facial videos via video magnification and deep learning用面部ROI视频放大和PCA盲源分离处理面部视频信号，数据仅288 videos且光照理想；单一协议下的结果不能直接代表跨场景成熟度。[266][242]

rejected: citation_outside_operands；Estimation of vital signs from facial videos via video magnification and deep learning使用私有288 videos，理想光照且额外数据需申请；Video-HR dataset仅15 participants、two 20 seconds face videos，规模、开放性和代表性限制复现。[266][156][262]

rejected: citation_outside_operands；Estimation of vital signs from facial videos via video magnification and deep learning的288 videos和单一理想光照协议、Video-HR dataset的15 participants与two 20 seconds face videos压缩了训练覆盖并增加过拟合风险；跨数据集性能下降使深度模型外部泛化受限。[266][156][262][242]

rejected: citation_outside_operands；Video-HR dataset只有15 participants、two 20 seconds face videos，HR MAE为2.49bpm；Estimation of vital signs from facial videos via video magnification and deep learning另有私有288 videos，因此小样本和开放性不足，不能把HR结果外推到其他体征。[156][267][266][262]

rejected: citation_outside_operands；Video-HR dataset有15 participants、two 20 seconds face videos，HR MAE为2.49bpm并采用k =10验证；访问属性未明确，小样本限制公开复现和泛化。[156][267][262]

rejected: citation_outside_operands；Video-HR dataset的15 participants、two 20 seconds face videos和k =10协议对应HR MAE 2.49bpm；小样本及协议差异会放大跨域风险，而跨数据集性能下降要求受试者独立、真实场景评估。[156][267][262][242]

rejected: citation_outside_operands；2020年到2023年的HR关键论文集合可围绕远程光电容积描记术（rPPG）、Pulse Rate Detection (PURE) dataset和UBFC-rPPG dataset等公开基准筛选；常见样本量为n = 10–30，但现有证据不足以为三项体征逐篇同时给出方法、数据集属性和带单位性能。[194][107][186][120]

rejected: citation_outside_operands；Pulse Rate Detection (PURE) dataset为10个人、60个1 min的序列（30 Hz、640×480像素、60 Hz参考），UBFC-rPPG dataset为50个视频数据、30 fps、640 × 480 像素；运动、光照、设备和参考信号差异使HR跨域成熟度比较不稳。[213][204][120]

rejected: citation_outside_operands；Pulse Rate Detection (PURE) dataset和UBFC-rPPG dataset分别只有10个人、60个1 min的序列（30 Hz、640×480像素、60 Hz参考）与50个视频数据（30 fps、640 × 480 像素）；规模、设备、标签及运动/光照条件不一致，限制深度模型跨域泛化和可复现性。[213][204][120]

**补充证据**

| 对象 | 论文题名与引用信息 | 论文正式出版日期 | 出版类型 | 核心技术方法族 | 使用的数据集 | 数据集访问属性 | 性能指标记录（mmHg或论文原始单位） | 验证协议 | 数据集证据状态 | 论文发表年份 | 论文目标体征 | 核心方法机制 | 性能指标名称 | 性能指标数值 | 性能单位 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2020—2023年BP关键论文集合 | Pandit、Lores、Batlle，Cuffless blood pressure monitoring[318] | 2020—2023年[318][239] | (2020)year[318] | 页面指出，食物和运动等刺激会影响交感神经系统并升高血压；相关实验包括静息条件、运动活动…[120] | 未找到证据 | 未找到证据 | Model 2（CNN-LSTM）在五折交叉验证中的平均 SBP MAE 为 3.99 mmHg、STD…[320] | Model 2（CNN-LSTM）在五折交叉验证中的平均 SBP MAE 为 3.99 mmHg、STD…[320] | 页面呼吁在全球范围内收集具有较大多样性和规模的公开数据集，以使基于摄像头的生命体征监测足够稳健…[120] | 2020year[239] | 页面记载，Zhou等人应用ICA和峰值检测识别波形的峰与谷，分别用于估计收缩压和舒张压。[120] | 未找到证据 | Model 2（CNN-LSTM）在五折交叉验证中的平均 SBP MAE 为 3.99 mmHg、STD…[320] | 6.91 mmHg[120] | Model 2（CNN-LSTM）在五折交叉验证中的平均 SBP MAE 为 3.99 mmHg、STD…[320] |
| ReViSe: Remote Vital Signs Measurement Using Smartphone Camera | ReViSe：智能手机摄像头远程生命体征测量；Qiao等；IEEE Access，2022[334] | 2022-12-15（期刊）[267]；2022-06-13（预印本）[263] | 期刊论文（IEEE Access）[334]；arXiv预印本[263] | HR估计采用CHROM脉搏提取、合成时空特征图和ResNet-18回归；模型先用合成特征图预训练…[270] | Video-BP是ReViSe作者自建的视频数据集；该页没有提供公开下载、注册说明、官方仓库或完整访问入口…[282] | Video-BP是ReViSe作者自建的视频数据集；该页没有提供公开下载、注册说明、官方仓库或完整访问入口…[282] | 在UBFC的4秒、6秒和8秒非重叠窗口中，模型分别报告：4秒窗口HR MAE 1.72 bpm、RMSE…[235] | 处理流程包括ROI检测、脉搏提取、峰值检测和HRV计算；OpenFace用于获得面部二维标志点…[237] | 期刊条目；IEEE Access 10:131656–131670[334]；未提供逐篇证据状态[334] | 2020year[53] | BP的核心输入可为RGB摄像头捕获的面部肤色变化，或视频中不同面部区域脉搏波之间的时间差（PTT）…[214] | HR估计采用CHROM脉搏提取、合成时空特征图和ResNet-18回归；模型先用合成特征图预训练…[270] | 该研究的rPPG数据来自莱比锡大学医院的50名计划接受手术的受试者；使用工业USB摄像头IDS…[141] | SBP 6.7mmHg[267]；DBP 9.6mmHg[267] | 该研究的rPPG数据来自莱比锡大学医院的50名计划接受手术的受试者；使用工业USB摄像头IDS…[141] |
| Estimation of vital signs from facial videos via video magnification and deep learning | 通过视频放大和深度学习从面部视频估计生命体征—Lin等，iScience 26:107845[334] | 2023-09-06[278] | Lin等人的研究正式引用为：Lin B., Tao J., Xu J., He L., Liu N.… | 视频放大＋深度学习CNN[264] | 论文使用本文采集的原始面部视频数据；研究报告了HR、舒张压和收缩压，但本页未提供SpO2的实验数据…[266] | 论文使用本文采集的原始面部视频数据；研究报告了HR、舒张压和收缩压，但本页未提供SpO2的实验数据…[266] | 论文使用本文采集的原始面部视频数据；研究报告了HR、舒张压和收缩压，但本页未提供SpO2的实验数据…[266] | 处理流程包括ROI检测、脉搏提取、峰值检测和HRV计算；OpenFace用于获得面部二维标志点…[237] | 期刊论文；证据不完整[334] | 2023year[265] | 该研究从单个面部视频提取面部和颈部两个ROI，自动检测、跟踪并放大ROI；将每个ROI划分为多个区块…[266] | ROI双路径波形＋小型CNN预测BP[327] | Lin研究的HR性能证据为RMSE 5.33；来源未说明单位、测试分母、数据集或测试划分。[265] | SBP 4.11；DBP 3.75[265] | Lin研究的HR性能证据为RMSE 5.33；来源未说明单位、测试分母、数据集或测试划分。[265] |
| Video-BP dataset | ReViSe：手机摄像头远程生命体征测量[326] | 未找到证据 | 144 data samples[156] | 页面称没有用于面部视频BP测量的公开rPPG数据集，因此使用含指尖传感器信号的数据集训练基于深度学习的BP估…[263] | 页面称没有用于面部视频BP测量的公开rPPG数据集，因此使用含指尖传感器信号的数据集训练基于深度学习的BP估…[263] | 页面称没有用于面部视频BP测量的公开rPPG数据集，因此使用含指尖传感器信号的数据集训练基于深度学习的BP估…[263] | SBP/DBP MAE 6.7/9.6mmHg；Video-BP测试集，90:10划分[156][158] | 标准化BP流程要求受试者坐姿、背部和手臂有支撑，双脚平放；测量前至少休息5分钟，测量期间不得交谈…[319] | 作者自建；无公开面部视频BP数据集[156] | 144 data samples[156] | BP：SBP、DBP[156] | 页面称没有用于面部视频BP测量的公开rPPG数据集，因此使用含指尖传感器信号的数据集训练基于深度学习的BP估…[263] | 页面称没有用于面部视频BP测量的公开rPPG数据集，因此使用含指尖传感器信号的数据集训练基于深度学习的BP估…[263] | 6.7mmHg（SBP）；9.6mmHg（DBP）[158] | 页面称没有用于面部视频BP测量的公开rPPG数据集，因此使用含指尖传感器信号的数据集训练基于深度学习的BP估…[263] |
| ReViSe用于血压训练的指尖传感器数据集（未命名） | 2020year[53] | 2022year[197] | 2022year[197] | HR估计采用CHROM脉搏提取、合成时空特征图和ResNet-18回归；模型先用合成特征图预训练…[270] | Video-BP是ReViSe作者自建的视频数据集；该页没有提供公开下载、注册说明、官方仓库或完整访问入口…[282] | Video-BP是ReViSe作者自建的视频数据集；该页没有提供公开下载、注册说明、官方仓库或完整访问入口…[282] | 在UBFC的4秒、6秒和8秒非重叠窗口中，模型分别报告：4秒窗口HR MAE 1.72 bpm、RMSE…[235] | 处理流程包括ROI检测、脉搏提取、峰值检测和HRV计算；OpenFace用于获得面部二维标志点…[237] | 13 Jun 2022[263] | 2020year[53] | BP的核心输入可为RGB摄像头捕获的面部肤色变化，或视频中不同面部区域脉搏波之间的时间差（PTT）…[214] | HR估计采用CHROM脉搏提取、合成时空特征图和ResNet-18回归；模型先用合成特征图预训练…[270] | 该研究的rPPG数据来自莱比锡大学医院的50名计划接受手术的受试者；使用工业USB摄像头IDS…[141] | 4.09[325] | 该研究的rPPG数据来自莱比锡大学医院的50名计划接受手术的受试者；使用工业USB摄像头IDS…[141] |
| 2020—2023年关键研究论文候选集合 | RGB相机血压测量：U-Net Basic生成模型[249] | 2023-09-06[249] | 正式出版论文[249] | RGB摄像头＋rPPG＋U-Net Basic生成模型[249] | 5个测试数据集[249] | (7852, 625)[249] | DBP MAE 4.43；SBP MAE 6.9 mmHg[249] | 5秒窗口；5数据集K折交叉验证；非个体化[249] | 页面呼吁在全球范围内收集具有较大多样性和规模的公开数据集，以使基于摄像头的生命体征监测足够稳健…[120] | 2023年[249] | 页面记载，Zhou等人应用ICA和峰值检测识别波形的峰与谷，分别用于估计收缩压和舒张压。[120] | 未找到证据 | SBP/DBP MAE；BHS阈值比例[249] | 463[43] | mmHg[249] |

rejected: number_unsupported；表中可核实的ReViSe: Remote Vital Signs Measurement Using Smartphone Camera/Video-BP结果为SBP/DBP MAE 6.7mmHg/9.6mmHg；关键论文集合、Estimation of vital signs from facial videos via video magnification and deep learning及候选集合的其他行在数据集、开放性、参考信号或单位上不完整，ReViSe用于血压训练的指尖传感器数据集（未命名）没有可核实条目，因此不同数据集和协议的结果不能直接排序。[158][265][249]

**血压（BP）：测量对象与技术链条**

截至2024年初，普通RGB面部视频对BP的估计仍是**间接估计**：摄像头先从面部皮肤反射光中恢复与血容量变化相关的远程光电容积描记（rPPG）或血容量脉搏（BVP）信号，再由波形形态、传播时间或学习模型推断收缩压（SBP）和舒张压（DBP）；两者均以mmHg报告。[184][312]

| 技术路线 | 从面部视频到BP的主要步骤 | 关键条件与限制 |
|---|---|---|
| rPPG与脉搏波分析（PWA） | 检测面部、裁剪ROI并进行皮肤分割；从RGB或绿色通道，或经ICA/PCA处理的颜色序列中提取rPPG；滤波后检测峰、足点和重搏切迹，计算时域/频域及波形形态特征，再用回归、CNN或RNN分别估计SBP和DBP。[184][296] | 对光照、肤色、化妆、摄像头距离和受试者运动敏感；噪声会直接改变波形幅度、斜率和峰间时间。[184] |
| PTT、PAT与PWV | PTT利用压力波在两个部位间的传播时间；PAT通常取ECG的R峰与PPG特征点之间的时间差；PWV则由传播距离和时间差计算。面部视频研究还曾用面部与手部序列估计相对传播时间。[184][312] | PTT通常需要两个同步信号或两个身体部位，PWV受个体动脉弹性和血管长度影响，均存在校准负担；一个面部视频、普通帧率摄像头不能直接等同于高帧率多部位测量。已有示例使用420fps高速摄像头。[184] |
| 空间模式与端到端深度学习 | 将多个面部ROI的脉搏波组成空间输入，或直接使用面部视频的时空特征；CNN、LSTM及其他深度模型学习rPPG/BVP与SBP、DBP之间的统计映射。部分集成实现同时输入RGB和YUV，由PhysNet或PhysFormer恢复PPG，再由两个回归节点输出SBP和DBP。[184][295] | 需要大量、同步且覆盖足够BP范围的配对视频—袖带标签；端到端模型容易把设备、光照或受试者身份等非生理特征当作预测线索。[184] |
| 合成数据与个体化校准 | Wu等提出用GAN生成合成rPPG数据以缓解BP视频样本不足；其他路线通过回归系数校准、迁移学习或受试者特异数据进行个体化。[184] | OLS、Deming回归和稳健回归等校准效果依赖数据集；个体化通常需要额外测量、计算资源和隐私保护。[184] |

**论文证据与性能边界**

2021年Wu等的《Contactless Blood Pressure Measurement via Remote Photoplethysmography With Synthetic Data Generation Using Generative Adversarial Network》在现有证据中可确认的核心方法是“rPPG+GAN合成数据”，但本片段没有给出可定位的SBP或DBP数值，因此性能字段应标为**NR（未报告/当前证据未核验）**，不能作为满足用户数值要求的关键论文。[184]

2022年Chen的《Estimating Cuff-less Continuous Blood Pressure from Fingertip Photoplethysmogram Signals with Deep Neural Network Model》是未同行评审的预印本，使用PhysioNet的MIMIC-II接触式指尖PPG和桡动脉导管ABP，而不是普通摄像头面部视频；其CNN—残差LSTM模型报告SBP平均误差为0.21±6.40mmHg、DBP平均误差为0.19±4.71mmHg，并采用五折交叉验证，按AAMI和BHS标准均达到相应要求。[312]这些结果只能作为“PPG到BP”邻近对照，不能直接代表面部rPPG性能。

一项面部视频基线研究在45名受试者上采用Sony HDR-CX405摄像机（1920×1080、50fps）和Omron HBP1300参考设备；流程为红色通道、PCA重建、0.5–5Hz带通滤波、峰/足点/重搏切迹检测、21个时频特征和多项式核回归。9折交叉验证的平均SBP MAE为3.90mmHg、误差标准差（ESD）为5.37mmHg；DBP MAE为3.72mmHg、ESD为5.08mmHg。[296]由于当前片段未核验其正式出版日期，暂只能作为受控小样本基线，不能直接列入2020—2023年关键论文表。

**BP数据集的公开性边界**

允许使用的BP资料列出的MIMIC（超过90名ICU患者、121条记录）、MIMIC-III（38,597名成人、49,785次住院）、MIMIC-B（4,000条记录、约1.5亿个样本）、UQVS（32名受试者）、Figshare（219名受试者、657个PPG片段）以及22名受试者数据，均不是公开的面部视频BP数据集，而是接触式PPG、ECG或ABP数据。[184]HCI-tagging/MAHNOB含面部视频和生理信号，UBFC-RPPG含面部视频、PPG、HR和SpO2，但这些数据不含BP标签，不能替代面部视频—SBP/DBP配对数据。[184]

因此，BP公开数据集表中必须把“普通面部视频、SBP/DBP标签、视频数量、帧率、分辨率和公开下载状态”分别核验；不能用MIMIC等接触式记录填充面部视频字段，也不能把仅有HR或SpO2标签的数据集误列为BP数据集。

BP需间接映射：面部ROI提取rPPG，以PTT/PWV或PWA特征估计SBP/DBP；连续估计需袖带校准。[190][139]

2021年面部rPPG框架用SPA去趋势、BMI估计SBP/DBP，数据集未报告，误差2.42%/5.53%。[191] 2022年iPPG2BP用公开BP4D+子集（57人、157视频、4123个2.56-s片段），U-Net/ResNeXt101+CWT重建BP；患者独立三折fold1的SBP MAE/RMSE=9.79/12.64、DBP=8.28/11.78 mmHg。[307]

BP4D+原始任务运动强，研究仅保留高SNR片段，性能不宜外推日常场景。[307] 2017年Kaggle无创BP集：26人；PCG/ECG/指尖PPG/FSR均1kHz，含SBP/DBP标签，仅接触式、非面部视频。[297]

BP的核心结果是：普通RGB面部视频可经皮肤ROI提取IPPG/rPPG/BVP，再分别估计收缩压（SBP）和舒张压（DBP）；但它不是直接压力测量，性能必须绑定参考袖带或ABP、校准方式、时间窗及受试者独立划分。[308]

**BP方法与逐项性能证据**

|研究/数据集|方法、输入与验证条件|SBP/DBP结果|
|---|---|---|
|2023年 IPPG-BP（公开）|外部摄像头面部视频；Dlib定位ROI，RGB/IPPG经小波与带通滤波后输入CNN+BiGRU，联合学习波形形态、时序及SBP–DBP关系。115名受试者、2120个片段；60 fps、1920×1080、约0.5 m、稳定光源；81人/1484片段训练，34人/636片段测试。|多阶段模型SBP MAE为5.33 mmHg，DBP MAE为3.92 mmHg；性能表另称使用30% validation set，故该测试口径存在需保留的表述差异。[308]|
|ReViSe（2022）|端到端rPPG框架，使用智能手机面部视频估计包括BP在内的多项体征；BP输出拆分为SBP和DBP。[197]|该来源确认方法、目标和年份，但未提供可核验的SBP/DBP数值；不能用该页面补填性能字段。|

IPPG-BP以符合ESH和AAMI标准的Yuyue YE670A血压计同步获取参考标签，并公开了数据集入口。[308]其受试者主要为18–40岁、无已知心血管疾病者；因此个体化校准仍需额外采集个人IPPG与BP数据，异常血压的外推能力有限。研究还指出，DBP通常比SBP更易估计，可能与SBP波动更大有关。[308]

作为模态边界对照，改进U-net在指尖PPG而非面部视频上报告SBP MAE为3.68±4.42 mmHg、DBP MAE为1.97±2.92 mmHg；该结果不能冒充普通摄像头BP性能。[88]BP验证还应报告平均差与标准差；AAMI/ANSI/ISO示例阈值为平均差≤5 mmHg、标准差≤8 mmHg。[299]

普通摄像头面部BP估计的主链是“面部反射光→PPG/rPPG→波形形态或PTT→SBP/DBP回归”：PTT是间接压力代理，必须用个体压力读数校准；常见分支包括CHROM、POS、ICA、PCA、TOI及CNN/MLP。[90] 综述列示的受控基线（年份未在片段中给出）中，TOI用iPhone 6采集17个面部区域、2 min视频，提取126个脉搏特征和29个元特征，经PCA保留30个向量输入MLP；准确率约95%，SBP偏差0.39±7.30 mmHg、DBP偏差−0.20±6.00 mmHg。[90] 另一项45名受试者的PCA基线报告SBP MAE 3.90±5.37、DBP MAE 3.72±5.08 mmHg。[90] 2020年Anura手机视频条目仅记录ANSI/AAMI/ISO81060-2:2013标准，未给SBP/DBP数值，不能作为满足数值门槛的关键论文。[90] BP验证应分列SBP/DBP；AAMI/ESH/ISO第一阶段要求平均差≤5 mmHg、标准差≤8 mmHg，协议样本为85名并覆盖规定压力范围。[313]

**BP证据续**

普通RGB面部视频BP采用iPTT/PTT/PWV、波形特征与时频分析、rPPG迁移学习及CNN/LSTM/Transformer回归SBP/DBP；相位偏移rPPG的DRP-Net/BBP-Net在MMSE-HR、V4V页面未给出BP数值。[309][141]

- **2020 iPTT研究**：以前额—下巴脉搏波估计iPTT，发现其与BP负相关；SBP/DBP误差未报告，属机制背景。[315]
- **2021 Assessment**：POS-rPPG取额头/脸颊信号；临床50人、32 fps、约2 h，床旁BP按每分钟标注。受试者独立ResNet-PPG的SBP/DBP MAE为16.4/8.5 mmHg，混合划分为7.7/4.4 mmHg；rPPG微调使SBP由28.9降至14.1、个体化后为12.7 mmHg。[141]
- **2022**：Wu等的免校准DNN融合三通道rPPG和7项生理指标，3个数据集共1143人、2291条数据，完整测试SBP/DBP MAE为11.54/8.09 mmHg；空间脉搏波-CNN在自建10名健康人数据上mean-BP相关系数为0.85、MAE为5.4 mmHg；Hybrid D1DCnet以前额iPPG输入，814人、8 s窗口，SBP/DBP MAE为8.36±6.22/5.69±3.97 mmHg。[301][314][70]
- **2023**：CVD临床研究用绿色rPPG和1D-CNN，132次就诊、5折受试者独立验证；SBP为r=.47、平均误差−0.47±15.5 mmHg，DBP为r=.16、−0.80±8.1 mmHg。[300] 手机CNN-LSTM/V4V方案使用7 s窗口并剔除SNR<−7 dB片段，但未报告具体MAE；另一中文条目作者为穆继文、唐晓英而非Lin，年份和参考设备未核验，自建集按111/14/14划分，SBP/DBP MAE为5.98±5.22/4.30±3.39 mmHg。[123][302]
- **数据角色**：ReViSe自建Video-BP的SBP/DBP MAE为6.7/9.6 mmHg；指尖训练集名称、公开性及面部视频属性未报告。[268] VitalVideos-Europe为开放数据，850人、每人2段30 s视频，同步PPG及一次BP；受试者静止直视，运动和说话泛化未验证。[140]
- MAHNOB-HCI仅提供24人、20段视频的情绪多模态记录，未给BP性能；2024-02-10研究及CNN/Transformer集成稿晚于2024-01-31，均不纳入本截面，后者片段亦未显示RMSE。[71][310][311][73]

BP是间接估计：RGB面部视频→BVP，经ICA/CHROM/POS等提取脉搏，再用时间差、波形形态或深度模型分别回归SBP/DBP（mmHg）。[130][93]

|研究|数据/方法（公开性）|性能|
|---|---|---|
|Spatial pulse-wave BP（2022）|自建；10名健康志愿者；连续BP+面部RGB；空间脉搏波→CNN|mean BP：r=0.85，MAE=5.4 mmHg。[304]|
|ReViSe（2022）|公开PPG（非面部训练）；FingerVideo-BP/FaceVideo-BP自建；rPPG→BVP+深度模型|Finger SBP/DBP MAE=10.3/8.2；Face=7.9/5.8 mmHg。[230]|
|Contactless BP via rPPG（2023）|30 fps；时间差+多模型/InfoGAN；自建集、TVGH夜间红外集|自建SBP 15.49→8.78、DBP 10.56→6.16；TVGH SBP 21.58→11.12、DBP 9.74→7.59 mmHg。[93]|

“Video-BP”未被ReViSe页面命名；公开性、人数、视频数、规格、参考设备及下载入口均未报告，故不列为确认公开集。[230] BP证据稀疏：消费级相机综述截至2020年9月仅3/26项研究测BP（12%），未作BP荟萃；两组Anura的SBP/DBP偏差±SD为0.39±7.30/−0.20±6.00和−0.4±6.7/1.2±7.0 mmHg，均在AAMI 5±8内，但MAE不可跨集排名，须看独立受试者、同步参考与校准。[131]

|研究/数据|方法与结果（SBP；DBP）|
|---|---|
|Rong、Li（2021）|Logitech webcam（1280×720、30 fps），色彩rPPG+ML；实验室191人、袖带参考：MAE 9.97±3.35（ME 2.1）mmHg；7.59±2.58（ME 0.79）mmHg。[223]|
|BPM-Net|15 s面部视频；额头/脸颊4个ROI、YUVT、残差CNN+BiLSTM；私有ASPD（124人、Mate30、1920×1080/30 fps）训练，MMSE-HR（102段/40人、25 fps）测试：MAE 12.35 mmHg；9.50 mmHg；ASPD内部为8.07/6.78 mmHg。[305]|
|相移rPPG补充|面部/末梢双rPPG、6 s窗口；MMSE-HR的MAE为10.19/7.09 mmHg，V4V为13.64/9.40 mmHg。[316]|

机制上，BP是间接估计：面部RGB先恢复rPPG，再用波形、PTT/PWV或模型回归SBP/DBP；PTT偏向SBP，PWV可对应二者，常用距离为0.4–3 m、30 fps。[134][223]多数摄像头BP验证仍在实验室静止条件下，真实场景测试较少。[134]MIMIC-III Transformer（1732名患者）为SBP/DBP MAE 2.41/1.31 mmHg；PulseDB含5361人和5245454个10 s ECG/PPG/ABP片段，均非面部视频，不能与视觉BP横比。[82][83]

截至2024年初，普通RGB面部视频对BP的估计仍属于“代理映射”：先从前额、脸颊、前臂或手掌ROI提取脉搏波的时间、面积、幅度和导数特征，再用ICA、峰谷检测或双ROI的脉搏传导时间（PTT）推断SBP/DBP。现有实验主要在静息、深蹲或冷刺激等实验室条件下进行，尚缺少真实场景验证。[120]  

2022年智能手机BP综述筛得7篇研究，排除1篇webcam研究；常用模型为人工神经网络和支持向量机，输入特征数为5–233个、受试者数为17–5,992人，多以袖带值验证；连续BP回归主要报告MAE或ME±SDE，分类任务则报告准确率。[317]

|实体（日期/状态）|核心方法、数据集与访问属性|性能及限制|
|---|---|---|
|**ReViSe**（2022）|端到端rPPG；智能手机面部视频；Video-BP为作者自建集，BP训练另使用未命名的指尖传感器数据，后者不是面部视频，公开性未报告。|Video-BP上SBP MAE为**6.7 mmHg**、DBP MAE为**9.6 mmHg**；测试分割、参考设备和血压范围未报告。[153]|
|**Zhou等**（题名、年份待核验）|RGB相机；ICA与峰值检测分别识别波形峰、谷以估计SBP、DBP。无运动、距离60 cm时测试；距离改变为30–90 cm、照度为75–500 lux。|SBP RMSE **6.91 mmHg**，DBP RMSE **4.88 mmHg**。因题名和年份未核验，暂不列为正式2020–2023关键论文。[120]|
|**Factors that affect Camera based Self-Monitoring of Vitals in the Wild**（2023）|203名健康受试者；四种手机的Face PPG，受控明亮房间，前置摄像头固定并拍摄完整面部；Yonker心脏监护仪作金标准。|表中Face PPG的SBP/DBP误差（误差±SD，mmHg）为：Xi N9 **−2.929±20.70/−2.596±13.60**，Xi N8 **−2.929±18.76/−2.403±13.835**，Oppo **−2.070±17.251/−0.824±12.937**，Sm 31 **−1.964±18.10/−3.157±12.80**；并非MAE。[239]|
|**Yoon等，Blood Pressure Measurement Based on the Camera and Inertial Measurement Unit of a Smartphone**（2023）|AlwaysBP用手指PPG加胸部IMU计算PTT，再由Bramwell–Hill和Moens–Korteweg方程估计SBP/DBP；87名19–70岁受试者，3次个体校准、261组配对测量，袖带式人工肱动脉测量作参考。该研究不是面部视频，故仅作范围对照。|SBP测试—参考差异为**1.2±7.1 mmHg**，DBP为**−1.0±6.0 mmHg**；SBP误差低于5/10/15 mmHg的比例为57.5%/84.3%/94.6%，DBP为75.5%/93.9%/97.3%。[322]|
|**2020–2023 BP候选集合**|Baek等2020年的手机传感器FCN研究、Schrumpf等2021年的PPG/rPPG深度学习研究可作为候选，但当前证据片段只提供书目信息，面部视频适用性和SBP/DBP数值均未核验，因此不作为正式性能证据。[239]|

**PulseDB**（2023）是公开的接触式BP基准而非面部视频数据集：包含5,361名受试者和5,245,454个10秒ECG/PPG/ABP片段；片段SBP、DBP分别按ABP逐搏峰值与转折点的平均值定义，整体均值为**121.42±22.10 mmHg**和**61.87±13.01 mmHg**。其提供受试者独立、校准式和校准自由划分，但MIMIC-III部分跨信号错位最高达**500 ms**，因此只能作为BP标签与验证协议参考。[95]

为避免误读，2025年后的面部rPPG迁移学习研究即使报告SBP/DBP MAE **8.721/8.653 mmHg**，也不纳入截至2024年初的论文清单；该研究在同一数据集上显示，存在受试者重叠时误差可降至**6.9/4.43 mmHg**，说明数据划分会显著影响BP结果。[321] 照明同样必须随性能报告：另一项摄像头实验在明亮条件下相对Polar H10的HR平均PCC仅为**0.28**，中暗照明下性能更差。[227]

BP不能从单帧肤色直接读出；常见链路是“面部ROI→BVP/rPPG或时空图→特征回归/端到端模型”，分别输出SBP和DBP。校准方法用袖带值或人口统计学变量映射到mmHg，非校准方法省略该步骤；面部/手部PTT、波形时频特征和深度网络均有应用。[323][324]

|研究|方法、数据集与条件|SBP/DBP性能|
|---|---|---|
|Luo等TOI研究|Apple iPhone 6拍摄2分钟面部视频；约>1,328名受试者、17个面部ROI；PCA+ANN，以袖带BP为参考，15%留作测试；数据集公开性未报告。|SBP ME±SDE=0.39±7.30 mmHg；DBP=−0.20±6.00 mmHg。[150]|
|Vastmindz，2022，《Evaluation of a Camera-Based Monitoring Solution…》|普通摄像头/rPPG，临床采集463名受试者；距离60 cm、环形灯至少250 lux，静止直视，单次60 s；公开性未报告。|SBP（n=463）MAE=18.15、RMSE=22.77 mmHg；DBP MAE=10.49、RMSE=13.71 mmHg；RMSPE分别为17.59%和17.38%（表3未重复标注误差单位，摘要给出±10 mmHg标准）。[43]|
|Chen等，2023，《Remote Blood Pressure Estimation via the Spatiotemporal Mapping of Facial Videos》|BPE-Net：额头/脸颊4个ROI、时空图、modified-YUV、残差网络+BiLSTM+区间分类器/计算器；私有MPM-BP训练（132人，Huawei Mate30，30 fps、1920×1080），公开MMSE-HR测试（40人、102段、25 fps）。|跨数据集SBP MAE/RMSE=12.35/16.55 mmHg；DBP=9.54/12.22 mmHg。[151]|
|《RGB Camera-Based Blood Pressure Measurement Using U-Net Basic Generative Model》，2023|RGB-rPPG与U-Net Basic；训练源含接触式MIMIC-II PPG/ECG/ABP及Leipzig面部rPPG（17人、USB摄像头、125 Hz、7 s，训练取5 s）；5个测试集K-fold、无个体化。|DBP MAE=4.43 mmHg，SBP MAE=6.90 mmHg；数据访问属性未报告。[249]|

文献汇总还报告：17个ROI+多层感知器的SBP/DBP平均误差为0.39/−0.20 mmHg，红通道PCA+线性回归MAE为3.9/3.7 mmHg，面部—手掌iPTT+预训练网络MAE为3.1/2.6 mmHg，但原始测试协议未统一。[323]另一临床rPPG队列仅纳入50人、32 fps、约2小时记录，25人因运动或弱光排除；剩余数据按7次心跳分窗并剔除SNR低于−7 dB窗口，14人微调时按12/1/1划分，且未达到BHS/AAMI要求。[323]因此，BP性能必须同时看SBP/DBP、校准、全范围分布、受试者独立性及运动和光照条件，不能按MAE跨研究直接排名。

BP：面部rPPG估计SBP/DBP。ReViSe（Video-BP）SBP/DBP=6.7/9.6mmHg[274]；网页框架（5人）SBP/DBP=9.4/3.8mmHg[328]；指尖PPG参考=3.99/2.65mmHg[320]，非面部不可直比。

**BP信号链与评价口径**

BP必须拆分为收缩压（SBP）和舒张压（DBP）：SBP是心脏收缩时的动脉压力，DBP是两次心跳之间的压力，二者均以mmHg表示。[330][333] AHA的成人参考分类为：正常低于120/80 mmHg，升高为SBP 120–129 mmHg且DBP低于80 mmHg，1期为SBP 130–139 mmHg或DBP 80–89 mmHg，2期为SBP至少140 mmHg或DBP至少90 mmHg；这些是临床分层阈值，不是视觉模型的性能标准。[330] 传统袖带参考测量通常要求测量前静坐3–5分钟，袖带置于裸露上臂并高于肘弯约1英寸，以约2 mm/s放气；首次听到搏动确定SBP，搏动声消失确定DBP。[331] 上臂自动设备通常优于腕式或指式设备，重复读数之间建议间隔1分钟。[332]

普通RGB面部视频的BP流程通常是“面部检测与ROI跟踪—颜色变化提取—rPPG/BVP恢复—波形特征或深度模型—分别输出SBP和DBP”。与HR只需频率峰值不同，BP需要更高质量的脉搏波形，尤其是舒张峰和切迹，因此运动、光照和ROI漂移会更直接地破坏BP估计。[157] 可用的非深度rPPG路线包括POS、LGI、CHROM、OMIT、GREEN、ICA、PCA和PBV；典型流程使用额头、左右脸颊等ROI计算RGB均值，再转换为rPPG并进行0.65–4 Hz带通滤波。[157]

**关键BP研究与数据证据**

| 研究/实体 | 核心方法、数据角色与访问属性 | BP性能及验证条件 |
|---|---|---|
| **ReViSe: Remote Vital Signs Measurement Using Smartphone Camera**（2022年预印本） | 以智能手机前置摄像头采集面部视频；BlazeFace和MediaPipe Face Mesh定位面部并预测478个标志点，分割前额、脸颊/鼻部及去除嘴部的大ROI。各ROI的绿色通道均值形成BVP，经SNR筛选、去噪、归一化、ICA、去趋势、移动平均和Welch PSD处理。BP部分采用ResNet三分支，分别输入BVP及其一阶、二阶导数，再拼接并由全连接层输出SBP和DBP；因面部视频样本有限，使用迁移学习。[156] | **Video-BP测试集：SBP MAE=6.7 mmHg，DBP MAE=9.6 mmHg**。BP模型以公开PPG数据训练，并在作者自建Video-BP上测试；论文未报告个体校准参数、完整测试分母和受试者独立划分。[156][158] |
| **Video-BP**（ReViSe自建数据资产） | 49名受试者（15名男性、34名女性，11–78岁）产生144个数据样本；Samsung Galaxy Note 9面部视频约25秒、30 fps，在充足日光下采集，手机可手持、放在表面或固定于三脚架。参考BP由Andesfit Health BP Monitor记录；SBP范围为85–168 mmHg，DBP范围为50–103 mmHg。[156] | 论文报告90:10训练—测试划分，并在训练中使用10折交叉验证；但没有说明是否按受试者独立划分。Video-BP被明确称为作者自建数据集，且截至该研究所述时间没有已知的、同时含面部视频和BP读数的开放公共数据集，因此截至2024-01-31不能将其确认为公开面部视频数据集。[156][158] |

ReViSe对训练数据的表述存在需要保留的访问边界：论文将其称为公开PPG/PPG-BP数据集，但所给材料没有提供数据集名称、完整下载入口、具体信号类型或训练测试划分；另一处仅说明其信号来自指尖传感器。因此，该数据只能作为接触式训练/参考信号，不能冒充公开面部视频BP数据集。[156]

**补充对照：相位偏移与双部位rPPG**

一项补充研究提出两阶段DRP-Net和BBP-Net：DRP-Net分别从面部与肢端区域估计相位偏移的rPPG，BBP-Net利用两类信号的时间特征和相位差，并将BVP的一阶、二阶导数表示为VPG/APG，再以多尺度特征融合和缩放sigmoid限制SBP、DBP输出范围。[272] 该研究在同步面部图像和连续BP信号上报告：MMSE-HR的SBP MAE/RMSE为10.19/13.01 mmHg，DBP为7.09/8.86 mmHg；V4V的SBP为13.64/16.782 mmHg，DBP为9.402/11.903 mmHg。MMSE-HR含102个样本、17名男性和23名女性，平均信号长30秒；V4V含1,358个样本，划分为724个训练、276个验证和358个测试样本，来自179名受试者，RGB视频为1040×1392像素、25 fps，BP信号采样率1000 Hz，任务包括引发 amusement、pain、anger 和 disgust。[272] 该结果作为补充对照，不与2020—2023年核心论文的ReViSe结果直接合并；其BHS阈值比例也应单独解释：MMSE-HR的SBP在误差≤5/≤10/≤15 mmHg内分别为46.02%/65.49%/75.22%，DBP为81.42%/92.04%/94.69%；V4V的SBP为65.24%/72.94%/81.39%，DBP为64.17%/80.11%/86.63%。[272]

**参考标签与证据边界**

一个情绪诱发面部视频数据集同时记录了SBP、DBP和MAP，但三项均来自非优势手第三指的接触式传感器，生理信号采样率为400 Hz，视频任务为约9分钟的情绪影片；该资料没有报告BP估计MAE、mmHg性能、袖带校准或独立测试划分，因此只能作为参考标签示例，不能作为BP关键性能论文。[329] 另一个双模态RGB–NIR资料对ReViSe仅列出HR结果（MAE 3.95 bpm），没有SBP或DBP方法、参考设备和性能数字，故不用于填充BP证据表。[275]

面部视频对BP首先提供rPPG/BVP信号；由于BVP时间特征与BP之间是非线性关系，研究通常再用机器学习或深度网络分别回归SBP和DBP。[267]

| 论文/实体（日期、类型） | 方法与数据集状态 | SBP/DBP性能与验证口径 |
|---|---|---|
| Qiao等，**ReViSe: Remote Vital Signs Measurement Using Smartphone Camera**（2022，IEEE Access） | 智能手机面部视频；深度网络检测面部标志点、提取多个ROI并滤波得到BVP；BP网络输入BVP及一、二阶导数，经ResNet分支输出SBP/DBP。训练使用公开PPG/指尖传感器数据，验证使用作者自建Video-BP，非已确认公开集。[267] | Video-BP测试集：SBP MAE **6.7 mmHg**、DBP MAE **9.6 mmHg**；49人、144个样本，约25 s、30 fps，Samsung Galaxy Note 9、充足日光，Andesfit Health BP Monitor作真值，SBP范围85–168 mmHg、DBP范围50–103 mmHg；90:10划分并以10折交叉验证训练。[267] |
| Lin等，**Estimation of Vital Signs from Facial Videos via Video Magnification and Deep Learning**（2023，iScience） | 视频放大与CNN双路径处理面部ROI，提取HR、PTT和波形特征；数据标为Private/Self-constructed，另有表格报告288个视频。[265][162] | SBP RMSE **4.11**、MAPE **3.73%**；DBP RMSE **3.75**、MAPE **4.95%**。支持片段未标出RMSE单位，也未给出独立测试划分和参考设备，故RMSE单位及协议记NR。[265][162] |
| **Predicting blood pressure from face videos using face diagnosis theory and deep neural networks technique**（Xing等，2023） | 面部视频与深度神经网络方法线索已确认；数据集、参考设备、SBP/DBP数值及单位未核验。[264] | NR，不作为核心数值论文。 |
| **Remote Blood Pressure Estimation via the Spatiotemporal Mapping of Facial Videos**（2023-03-09） | 面部视频生成时空图；深度残差网络与BiLSTM提取特征，再由BP区间分类器和数值计算器输出结果；私有MPM-BP训练、公开MMSE-HR测试，并用过采样平衡BP区间。[337] | 跨数据集测试（MPM-BP 132个样本训练、MMSE-HR测试、150帧切片）：SBP MAE/RMSE **12.35/16.55 mmHg**，DBP MAE/RMSE **9.54/12.22 mmHg**。[337] |

MPM-BP含132名18–24岁受试者；Huawei Mate30面部视频为30 fps、1920×1080、约1分钟、距离约0.5 m，并与Biopac M160和OMRON HEM-1020同步。MMSE-HR为公开集，含40人、102段面部视频、25 fps，记录平均HR/BP并包含面部表情和头部运动条件。[337] MPM-BP五折消融中，modified-YUV、150帧切片与LSTM得到SBP MAE/RMSE/SD **8.07/9.94/9.81 mmHg**，DBP为**6.78/8.45/8.28 mmHg**。[337]

ReViSe所用未命名指尖数据仅能确认用于BP训练，属于接触式PPG信号而非面部视频；名称、公开状态和划分未报告。页面另举“107个指尖PPG特征+ReliefF+GPR”估计SBP/DBP的例子，但不能归因于ReViSe本身。[267] BP结果还受运动、光照和设备异质性影响；不同参考设备、袖带、样本量和验证协议不能直接互换。[335][338] 因此，2022–2023年候选论文中标为NR者不应被填补或与有完整单位的结果无条件排名。

作为截止日前的补充，2024-01-09公开的DRP-Net/BBP-Net研究（不计入2020–2023核心论文表）在MMSE-HR上报告SBP MAE/RMSE **10.19/13.01 mmHg**、DBP **7.09/8.86 mmHg**，使用面部与ABP配对数据。[336]

ReViSe（2022）Video-BP的SBP/DBP MAE=6.7/9.6mmHg[280]；智能手机面部rPPG提取ROI/BVP，指尖信号作BP训练，Video-BP自建且公开性未证。2023消费级iPPG-BNN（220名患者）误差9±13/7±10mmHg[339]；2020食指PTT（非面部，6人/180试次）MAE=2.07±2.06/2.12±1.85mmHg[340]。

ReViSe（2022）：面部rPPG/Video-BP自建，SBP/DBP MAE=6.7/9.6mmHg；指尖PPG训练，公开未报告。[282] Lin（2023）：放大CNN、自建视频，SBP/DBP RMSE=4.11/3.75mmHg。[266]

ReViSe(2022)手机面部rPPG→BVP及一/二阶导数→ResNet迁移学习；论文称无公开面部BP-rPPG集，公开指尖PPG训练、自建Video-BP验证：49人/144样本，25s、30fps、日光、Andesfit；SBP85–168、DBP50–103mmHg，MAE6.7/9.6mmHg，公开性未证[283]。Lin(2023)面/颈ROI视频放大+PCA+小CNN估计BP；原始视频仅申请，数据集/划分/数值未报告[278]。RGB-U-Net：DBP/SBP MAE4.43/6.9mmHg、BHS A/C；面部集17人，另用MIMIC-II接触PPG/ECG/ABP训练[341]。

Video-BP被描述为作者自建、尚未核实为公开的面部视频数据集；视频约25秒、30 fps，包含49 people和144 data samples，以SBP/DBP为目标标签，训练采用k=10，并报告SBP MAE 6.7 mmHg、DBP MAE 9.6 mmHg。[152][267][156][283] 但公开访问入口、具体参考设备和同步/受试者独立协议未被同时核验，故不能直接纳入公开数据集主表。[152][156]

BP服务于普通摄像头面部视频的非接触健康监测时，应拆成SBP和DBP，均以mmHg报告，并以袖带式测量作参考；两者还可分别训练、互不共享权重。[298][123] 技术上可从面部ROI提取rPPG/BVP，使用RGB→YUV、PhysNet/PhysFormer和回归头输出SBP/DBP，或采用PTT/PAT、波形特征回归及校准/迁移学习。[295][184][190]

未命名指尖传感器数据集只承担接触式PPG/BVP的BP训练或参考信号角色，不是ReViSe的面部视频输入；其名称、公开状态、传感器类型及是否含面部视频均未说明。[280][156] 因而它不能替代公开的面部视频—SBP/DBP配对数据，只能支撑从接触信号训练到Video-BP验证的迁移链条。[280]

在BP论文层面，ReViSe采用面部ROI→BVP→一阶/二阶导数→ResNet，先用公开PPG-BP样本训练、再以自建Video-BP验证，报告SBP/DBP MAE 6.7/9.6 mmHg；Video-BP为25 seconds、30 fps、49 people、144 data samples，训练使用k=10。[267][156][283] 这些事实覆盖BP论文的方法、数据集角色和性能字段，但不足以补齐HR与SpO2的同口径论文清单。

就BP子范围，主流技术可按颜色/ROI取rPPG、PTT/PAT与波形特征回归、深度或混合网络、以及校准/个性化分类；适用性取决于是否恢复足够高质量的压力相关波形。[190][184][295] BP验证应分别记录SBP/DBP、mmHg及袖带参考信号；现有材料未补齐HR和SpO2的完整定义与性能。

BP横向比较必须固定MAE/RMSE/ME/SDE、mmHg单位、参考设备/信号、受试者独立划分、窗口、数据集、实验条件和统计分母；PulseDB分开提供calibration-based与calibration-free测试，说明划分会影响泛化结论。[83] ReViSe在自建Video-BP上报告SBP 6.7 mmHg和DBP 9.6 mmHg，但与其他数据集结果不能无条件排名；本节按技术性能、数据集、综合分析展开。[267][283]

BP路线可概括为面部rPPG/BVP、PTT/PAT、波形回归、深度网络和校准/个性化；ReViSe用公开PPG训练、用自建Video-BP验证，报告SBP/DBP MAE 6.7/9.6 mmHg。[295][184][267] Video-BP提供面部视频性能锚点，而未命名指尖数据只提供接触式训练/参考信号，不能当作公开面部视频数据集或外部验证集。[280][156]

Video-BP在BP论文中是自建面部视频验证集，提供SBP/DBP MAE 6.7/9.6 mmHg；指尖传感器数据集则是接触式PPG/BVP训练来源，二者分别对应视觉测试与接触训练，不能混写为同一个公开数据集。[156][280][267]

Video-BP报告SBP/DBP MAE 6.7/9.6 mmHg，来自49 people、144 data samples、SBP 85-168 mmHg和DBP 50-103 mmHg的日光/可变设备场景；其自建和内部训练验证条件支持可行性，却不能独立证明外部泛化。[267][156]

普通摄像头面部视频可通过手机前摄、人脸标志点和多ROI提取BVP，再估计HR、SpO2和BP；ReViSe把该链条扩展到日常环境，Video-BP用于SBP/DBP验证。[263][280][156]

Video-BP的可核实规模为49 people和144 data samples，视频约25 seconds、30 fps，设备可手持、放在表面或三脚架上，环境为充足日光，SBP/DBP范围为85-168/50-103 mmHg；它是作者自建，公开下载入口未被证实。[156][267][263] 这暴露出人口覆盖、设备/环境、参考标签同步和开放复现方面的局限。

49 people、144 data samples且面部样本有限，促使Video-BP采用迁移学习；日光、可变设备放置和自建数据会混入设备、光照与主体差异，使内部误差难以代表跨设备/跨人群泛化。[156][283][267] 缺少公开访问和统一面部视频BP基准，还限制独立复现、受试者独立评估与外部迁移。[263][280]

rejected: citation_outside_operands；PTT是不同部位PPG波形的时间差，需借助PWV和血管因素，并用BP=a·PTT+b校准为压力；SBP和DBP还依赖舒张峰、切迹等高质量形态，因此比仅做频率或峰值检测更苛刻。[90][223][157] 面部rPPG在光照、肤色和运动模糊条件下受干扰，面部图像加BP的公开数据缺口及实验室窄范围限制跨域验证。[316][272][179]

公开BP数据的限制包括Face-Hand仅26 subjects，人口多样性和环境变化带来噪声/人口统计偏差；不少方法只在实验室和狭窄BP范围测试，接触式电极、腕带或外部压力也削弱真实场景代表性。[297][179] PulseDB虽有5,361 subjects、5,245,454个10-s ECG/PPG/ABP片段，但不是面部视频，且MIMIC-III跨信号错位可达500 ms；所以开放性不等于面部标签和跨域可用性。[83][184]

这些局限会让深度网络把人口、设备、光照或参考信号差异学成BP线索；缺少公开面部视频＋BP配对数据又限制独立训练、校准和外部评估，校准式与免校准式结果必须分开解释。[179][272][83][184] 高低BP范围和跨信号同步会改变误差，单一实验室MAE不能代表跨设备/人群泛化；因此需要扩大标准化数据并持续采集人脸视频、PPG和生命体征以支持个体校准。[90][184]

BP主流路线包括从面部ROI提取rPPG/iPPG、分析波形形态或多ROI PTT/PAT并回归SBP和DBP；端到端模型也可将RGB/YUV面部视频经PhysNet/PhysFormer生成PPG，再由回归头输出两项压力。[190][306][295] 校准通常依赖数据集微调回归系数，并可结合个体化或迁移学习；ReViSe/Video-BP测试报告SBP/DBP MAE为6.7mmHg/9.6mmHg，参考可用符合ESH和AAMI的血压计，但HR和SpO2的性能与验证条件仍缺具体证据。[184][158][308]

血压是血液作用于血管壁的压力；SBP表示心脏收缩时的最大压力，DBP表示舒张时的最低压力，二者应分别以mmHg记录。[308][330][333][303] 参考测量可采用袖带或动脉导管协议，也可使用符合ESH和AAMI的血压计；HR的bpm定义及SpO2的百分比或百分点和脉搏血氧仪参考仍缺具体证据。[299][308]

**补充证据**

| 对象 | 论文题名与引用信息 | 论文正式出版日期 | 出版类型 | 核心技术方法族 | 使用的数据集 | 数据集访问属性 | 性能指标记录（%、百分点或论文原始单位） | 验证协议 | 数据集证据状态 | 论文发表年份 | 论文目标体征 | 核心方法机制 | 性能指标名称 | 性能指标数值 | 性能单位 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2020—2023年SpO2关键论文集合 | 该SpO2研究报告了明确的数值性能，但研究输入为手部视频而非面部视频，因此不满足普通RGB面部视频纳入范围…[369] | 未找到证据 | 2%[376] | 该SpO2研究报告了明确的数值性能，但研究输入为手部视频而非面部视频，因此不满足普通RGB面部视频纳入范围…[369] | 14recordings[368] | 14recordings[368] | MAE 0.62%[119]（60点）；SpO2误差0.029±1.141%[361]（LOOCV） | LOOCV、商用血氧仪[361]；300–650 lux、60 cm[376]；14段训练/7段测试[368] | 未找到证据 | 未找到证据 | 该SpO2研究报告了明确的数值性能，但研究输入为手部视频而非面部视频，因此不满足普通RGB面部视频纳入范围…[369] | 该研究于2023年发表，使用普通网络摄像头拍摄面部前额区域，基于RPPG提取红光和蓝光信号…[376] | 该研究报告的平均绝对误差（MAE）为0.62%。[119] | 0.62%[119] | 该研究与其他研究的比较结果为：Bhattacharjee 的平均绝对误差为1.4%，本研究为0.62%…[119] |
| ReViSe: Remote Vital Signs Measurement Using Smartphone Camera | 未找到证据 | 未找到证据 | 未找到证据 | HR估计采用CHROM脉搏提取、合成时空特征图和ResNet-18回归；模型先用合成特征图预训练…[270] | Video-BP是ReViSe作者自建的视频数据集；该页没有提供公开下载、注册说明、官方仓库或完整访问入口…[282] | Video-BP是ReViSe作者自建的视频数据集；该页没有提供公开下载、注册说明、官方仓库或完整访问入口…[282] | 在UBFC的4秒、6秒和8秒非重叠窗口中，模型分别报告：4秒窗口HR MAE 1.72 bpm、RMSE…[235] | 处理流程包括ROI检测、脉搏提取、峰值检测和HRV计算；OpenFace用于获得面部二维标志点…[237] | 未找到证据 | 2020year[53] | BP的核心输入可为RGB摄像头捕获的面部肤色变化，或视频中不同面部区域脉搏波之间的时间差（PTT）…[214] | HR估计采用CHROM脉搏提取、合成时空特征图和ResNet-18回归；模型先用合成特征图预训练…[270] | 该研究的rPPG数据来自莱比锡大学医院的50名计划接受手术的受试者；使用工业USB摄像头IDS…[141] | 未找到证据 | 该研究的rPPG数据来自莱比锡大学医院的50名计划接受手术的受试者；使用工业USB摄像头IDS…[141] |
| Estimation of vital signs from facial videos via video magnification and deep learning | Lin等人的研究正式引用为：Lin B., Tao J., Xu J., He L., Liu N.… | 2023-09-06[278] | Lin等人的研究正式引用为：Lin B., Tao J., Xu J., He L., Liu N.… | 该研究从单个面部视频提取面部和颈部两个ROI，自动检测、跟踪并放大ROI；将每个ROI划分为多个区块…[266] | 论文使用本文采集的原始面部视频数据；研究报告了HR、舒张压和收缩压，但本页未提供SpO2的实验数据…[266] | 论文使用本文采集的原始面部视频数据；研究报告了HR、舒张压和收缩压，但本页未提供SpO2的实验数据…[266] | 论文使用本文采集的原始面部视频数据；研究报告了HR、舒张压和收缩压，但本页未提供SpO2的实验数据…[266] | 处理流程包括ROI检测、脉搏提取、峰值检测和HRV计算；OpenFace用于获得面部二维标志点…[237] | 未找到证据 | 2023year[265] | 该研究从单个面部视频提取面部和颈部两个ROI，自动检测、跟踪并放大ROI；将每个ROI划分为多个区块…[266] | 该研究从单个面部视频提取面部和颈部两个ROI，自动检测、跟踪并放大ROI；将每个ROI划分为多个区块…[266] | Lin研究的HR性能证据为RMSE 5.33；来源未说明单位、测试分母、数据集或测试划分。[265] | 2.31[375] | Lin研究的HR性能证据为RMSE 5.33；来源未说明单位、测试分母、数据集或测试划分。[265] |
| 2020—2023年关键研究论文候选集合 | 未找到证据 | 未找到证据 | 未找到证据 | 页面指出，食物和运动等刺激会影响交感神经系统并升高血压；相关实验包括静息条件、运动活动…[120] | 未找到证据 | 未找到证据 | 未找到证据 | 未找到证据 | 页面呼吁在全球范围内收集具有较大多样性和规模的公开数据集，以使基于摄像头的生命体征监测足够稳健…[120] | 未找到证据 | 页面记载，Zhou等人应用ICA和峰值检测识别波形的峰与谷，分别用于估计收缩压和舒张压。[120] | 未找到证据 | 未找到证据 | 463[43] | 未找到证据 |

**技术路线与证据边界**

截至2024年1月31日，面部视频估计SpO2的主要流程是“面部ROI提取—RGB/多波长时序信号—rPPG或VPG—双波长吸收比、经验校准或深度模型”。SpO2反映氧合血红蛋白占总血红蛋白的比例；传统脉搏血氧仪通常利用约660 nm红光和940 nm近红外光的差异。普通RGB摄像头不能直接获得940 nm近红外信息，因此RGB方法通常以蓝通道近似替代红外通道，再计算红、蓝信号的AC/DC比值（ratio-of-ratios）；也有研究使用RGB+IR、滤光片或多光谱相机。[98][190]

面部ROI通常取额头、鼻子和左右脸颊。算法先对ROI像素做空间平均，得到颜色或亮度时间序列，再用滤波、ICA、PCA、CHROM、POS或FFT提取脉搏成分；深度学习方法则将多ROI序列编码为时空图（STMap），分别学习DC/AC成分并回归SpO2。[98][190][354] 由于SpO2需要光谱和个体校准，运动、光照、肤色、低氧范围及参考脉搏血氧仪误差都会影响结果。

**2020—2023年数值证据**

- **Mathew等，2021，《Remote Blood Oxygen Estimation From Videos Using Neural Networks》**：使用CNN处理智能手机RGB视频，14名受试者的报告表给出SpO2 RMSE **<3.1%**。[190] 但原始证据明确说明其采集对象是手掌/手背而非面部，因此只能作为普通手机血氧估计的非面部对照；数据集公开性和具体访问状态在当前证据中未报告。
- **《A Facial Video based Framework to Estimate Physiological Parameters using Remote Photoplethysmography》，2021**：从面部ROI去趋势并提取RGB通道，结合滤波、ICA、CHROM和绿色通道处理SpO2；报告平均SpO2误差 **1.4%**。[191] 当前片段未给出其数据集名称、公开/自建属性或参考血氧仪，故不能与其他结果直接排名。
- **ARPOS，2022**：使用额头、嘴唇和脸颊ROI，融合RGB、红外和深度数据，并采用FFT、辐射测量、去趋势、插值、Hamming窗及FastICA；40名参与者的SpO2 RMSE为**2.3%**，活动状态下PCAICA结果为**2.5%**。[348][192] 同一来源的结果表还列出静息FastICA为**2.5%**，说明摘要和分状态表存在统计口径差异；该系统含IR和深度通道，不应视为纯普通RGB面部摄像头结果。
- **CNN-Filter/CNN-EndToEnd，2023（arXiv:2212.07116）**：以Logitech C920n网络摄像头30 fps采集面部视频，以OxyTrue A脉搏血氧仪作参考；自采集数据含50名受试者，SpO2范围为85%–100%，40人训练、10人测试，受试者进行屏气以产生低氧变化。CNN-Filter报告MAE **1.17**、RMSE **1.40**、相关系数 **0.474**；CNN-EndToEnd报告MAE **1.18**、RMSE **1.40**、相关系数 **0.496**。[98] 这些误差对应SpO2百分比量纲；现有表格片段未单独标注“百分点”，应在引用原文时再次核对单位。

作为边界对照，另一项手机后置摄像头研究使用50条记录，在测试集报告SpO2 MAE **1.1%**，但输入是手指反射式PPG而非面部视频，因此不纳入核心面部视觉证据。[353] SUMS来源页则称其包含10名高原受试者、80条同步面部和手指视频，视频为1280×720、60 fps，参考设备为CMS50E+，实验包括运动和缺氧恢复；面部与手指融合使SpO2 MAE较单独面部或手指输入分别降低7.6%和10.6%，多指标训练使MAE降低17.8%，但该页未给出绝对MAE或版本日期。[342]

因此，**1.17、1.4、2.3和2.5不能直接构成性能排名**：它们混合了纯RGB、RGB+IR+深度、手部输入与面部输入，也采用了不同的SpO2范围、参考设备和受试者划分。只有在输入均为普通RGB面部视频、参考血氧仪同步、SpO2范围和误差定义一致，并采用受试者独立测试时，才适合横向比较。

2020年Casalino等以普通摄像头面部RGB→rPPG、色度/FIR及红蓝RoR估计SpO₂；作者自采21名健康受试者，指夹血氧仪参考，每人10次，AE=0（8次）、≤1（6次）、≤2个百分点（7次）[349]。2023年Zhu等RGB-rPPG/RoR低氧实验仅2人，最低81%，RMSE=1.93%、PCC=0.97[99]；同年多光谱VPG/PCA研究暗室15人RMSE=2.55%，环境光20人RMSE<4%，但均为中棕肤色[355]。2021年候选论文性能未核验[356]；2024年3月结果不纳入截止截面[345]。

**SpO₂的信号链与方法边界**

SpO₂估计的物理基础是氧合与脱氧血红蛋白在不同波长下的吸收差异；传统脉搏血氧仪使用约660 nm红光和940 nm近红外光，而普通RGB面部视频通常以红、蓝或红、绿通道的 AC/DC ratio-of-ratios（RoR）代替，并通过参考血氧仪校准。[119] 面部视频管线通常为人脸检测与ROI跟踪、RGB信号提取、滤波或色度变换、rPPG恢复，再计算RoR或输入回归模型；ICA、CHROM、POS、STMap、带通滤波和去趋势用于抑制光照、运动和遮挡噪声。[100][205][207][208][231] 仅使用面部IPPG的CNN–LSTM或CNN–BiGRU研究目标是SBP/DBP而非SpO₂；其IPPG-BP数据含115名志愿者、2120个信号片段，不能作为SpO₂数据集。[308][123]

**2020—2023年数值证据**

- **Nishidate等，2022，RGB camera-based simultaneous measurements…**：用数字RGB摄像头和皮肤光传输模型估计氧合、脱氧及总血红蛋白，再以FIR滤波和脉搏波幅比值结合商用指夹血氧仪校准SpO₂。13名健康志愿者（22–45岁）接受9分钟、其中FiO₂=11%持续4分钟的低氧实验；平均偏差为0.5%，精密度为±4.3%，RMSE为4.3%，与参考设备相关系数为0.76。[121]

- **Petersen、Kjær与Sørensen，2023，Remote Estimation of Peripheral Oxygen Saturation and Pulse Rate From Facial Analysis Using a Smartphone Camera**：智能手机前置摄像头拍摄前额面部视频，以rPPG和图像/信号处理估计SpO₂；作者采集10名健康受试者在理想光照和不同呼吸模式下的数据，SpO₂范围为92%–99%，Arms为1.34%，MAE为1.26±0.68个百分点。当前可定位片段未说明参考血氧仪型号。[94]

- **Estimating SpO₂ with Deep Oxygen Desaturations from Facial Video…，2023**：消费级RGB摄像头在四种色温/亮度条件下采集面部视频，利用rPPG及Red/Blue、Red/Green两种RoR；通过口管、鼻夹和受控吸气诱导低氧，SpO₂最低达81%，参考为Transfer Standard Pulse Oximeter。在暖色温、正常亮度条件下，两名受试者进行留一受试者交叉验证，RMSE为1.93%，PCC为0.97。[101]

- **Using Contactless Facial Image Recognition Technology to Detect Blood Oxygen Saturation，2023**：普通网络摄像头拍摄额头ROI，提取红、蓝光并带通滤波，以均值、标准差及经验公式`SpO₂=125−28R`计算结果；与台湾认证血氧仪比较，结果段报告30名受试者、60个测试点，光照500–650、距离65 cm，MAE为0.62%。方法示例另写一名大学职员，存在受试者口径冲突；应以“30名/60点”作为结果分母。[119]

- **A Study of Machine Learning Regression Techniques…，2023**：这是红外单通道而非普通RGB路线；对面部视频作EVM运动放大，提取额头和双颊三个ROI的12个统计特征，并比较OxygeNN、3D-CNN、ViViT及传统回归。作者自建21名参与者、每人两次2分钟实验，以商用脉搏血氧仪作参考；最佳RMSE为1.331%，R²为0.465。[350] 论文提到的ISO口径为脉搏血氧仪RMS准确度不超过SpO₂范围的2%，测试对的均方误差不超过4%。[350]

- **ARPOS，2022**：使用面部额头、嘴唇和脸颊ROI的RGB、红外与深度数据，经去趋势、插值、Hamming窗、FastICA、FFT和辐射测量同时估计HR与SpO₂；40名参与者的SpO₂ RMSE报告为2.3，但可见片段未明确单位。该多模态/红外深度路线不等同于普通RGB摄像头。[201]

2020年Bui等的手机**指尖**视频研究使用RGB、FFT和RoR，但19名健康受试者、3种手机的参考SpO₂仅为95%–99%，RoR跨个体和手机变化近三个数量级，作者未形成SpO₂回归性能指标；因此不能替代面部视频证据。[357] Takahashi等2021年多波段视频条目在当前证据中只有书目信息，未提供性能数字；2022年面部视频深度学习多模型融合研究也仅确认题名和方法，数据集与指标未核验，均不作为满足“关键论文数值性能”要求的条目。[351][202]此外，Cheng等论文页面同时标注2024-03-04和“Bioengineering 2023”，存在日期冲突且晚于2024-01-31，故不纳入本报告截止期；其后续VIPL-HR结果不用于本节历史结论。[358]

补充证据：SpO₂需双波长AC/DC比及标定（传统660/940 nm）；普通RGB面部视频通常为ROI→rPPG→滤波→RoR/回归或CNN；网络摄像头前额红蓝RPPG也可用均值、标准差求值，但该片段未给出数值性能。[134][224][145]

- Kim等（2021，YCgCr-RGB）：KCF/YCbCr皮肤ROI、Cg/Cr与Beer–Lambert校准；10名健康韩国人、CMS50E、5分钟录像及1分钟屏气（参考SpO₂平均下降10%）；MAE 0.537、RMSE 0.692（原文未明示为%或百分点），PCC 0.86、ICC 0.922。[78]
- van Gastel和Verkruysse（2022）：MOSSE+APBV/RoR；自采Dataset I（19人分析、70%–100%、402分钟）校准、Dataset II（10人、240分钟）验证；坐姿误差<4个百分点，站立约8个百分点。[45]
- 2022年公开VIPL-HR基准：STMap+EfficientNet-B3（RGB+YUV）MAE 1.012%、RMSE 1.473%；RoR基线MAE 3.334%/1.838%、RMSE 5.137%/2.489%。[144]
- 2023年视频放大+3D-CNN研究：18名健康人，YOLOv5 ROI+Hermite放大，与接触式血氧仪一致性98%，但MAE/RMSE未报告；同年环境光/肤色研究含31人、200–500 lux，仅报告使用RMSE，数值未核验。[104][102]
- Mathew等（2021）手机CNN在14人手部视频上RMSE<3.1%，非面部输入，仅作边界对照。[223]

PURE公开集含10人、60段视频（59段可用）、30 fps、640×480；CMS50E以60 Hz同步提供脉搏波和SpO₂，包含6种头动。[359] RGB相机PPG调制强度比接触探头低10–100倍，宽谱环境光、镜面反射/肤色、运动、小样本及屏气延迟均限制外推；参考血氧仪也可能受肤色和设备差异影响。[45][103][224]

**关键SpO2研究的补充证据**

机制上，心动引起皮下血容量变化，进而改变面部皮肤的光反射；典型流程是人脸检测/跟踪、ROI取样、RGB信号滤波或色度变换，再由rPPG波形估计SpO2。血红蛋白和氧合血红蛋白在约520–580 nm有吸收峰，但普通RGB相机缺少理想的红光—近红外双波长，因此必须校准[146][86]。

| 研究（年份与范围） | 方法、数据集与公开性 | SpO2性能、参考与条件 |
|---|---|---|
| Sun等《Robust non-contact…》（2021；非面部边界） | 手机RGB相机+闪光灯，红/绿ratio-of-ratios与MLR；5名健康志愿者手背自采，公开性未报告；SpO2控制在90%–100%，以医疗级血氧仪作参考。 | 总体误差为0.029±1.141%，组内误差为0±1.07%（百分比误差）；组内测试者参与训练，不能等同于独立外部测试[361]。 |
| 《Evaluating the robustness…》（2021；PURE公开） | 面部三ROI加跟踪ROI，RGB均值、滤波、chrominance及红/蓝分量计算；PURE含10名受试者、60段视频，30 Hz、640×480，CMS50E血氧仪60 Hz；静止、说话及4类头部运动。 | 总MAE为1.332%，RMSE为1.637%，Pearson \(r=0.535\)；低照度导致慢平移和小旋转条件误差增大[244]。 |
| ReViSe（2022；面部） | 端到端手机面部rPPG；使用公开TokyoTech rPPG和PURE。 | PURE上的SpO2 MAE为1.60%；该值应与其特定公开集和评估口径绑定，不能外推至临床低氧[158]。 |
| van Gastel、Verkruysse《Contactless SpO2…》（2022；面部） | 普通RGB相机加低成本COTS组件；面部跟踪并估计PPG相对振幅比；低氧实验用于校准，志愿者实验用于spot-check，范围70%–100%。 | 坐姿、可有头部支撑和/或环境光的现实筛查中误差小于4个百分点；摘要未给出受试者数、参考仪器、分母及数据公开状态[363][364]。 |
| 《Peripheral Oxygen Saturation Measurement Using an RGB Camera》（2023；面部ROI未核验） | KNN；两个数据集分别在3150 m和海拔102 m采集，共60名受试者，使用手机、网络摄像头和工业相机；LOSO验证。 | 手机、网络摄像头和工业相机的MAE分别为4.39%、4.45%和4.22%；参考血氧仪、视频分母、面部ROI及数据公开性未由摘要说明[360]。 |
| Camera-Based Monitoring Solution临床评估（2022） | 人脸地标/ROI，逐帧采集BGR并转为一维信号；Logitech webcam、Samsung M32、OnePlus 9、iPhone 11和iPad 9；235个SpO2样本，参考医疗设备。 | 90%–100%范围内ME为0.3%、MAE为1.21%、RMSE为1.77%、RMSPE为1.85%；60 cm、至少250 lux、60 s、受试者静止，低于90%的样本有限[86]。 |
| 2023面部视频候选（Lin等；题名和SpO2字段待核） | 当前证据页显示为额头/脸颊ROI、自监督对比学习、3D CNN，ROI为64×64像素、128帧窗口、步长8帧，并以PPG微调；页面实际报告的是HR/rPPG。 | SpO2方法、数据集、公开性、参考血氧仪和数值性能均未报告，不能用其HR结果填充SpO2表格[362]。 |
| 其他候选（e021） | Bui等2020论文涉及波长分离和色素补偿；Radiant（2023）涉及信号嵌入与Transformer；Dual-path TokenLearner（2023）涉及面部视频rPPG。 | 当前片段只有书目信息，没有逐篇SpO2数值，均保留为候选而不列为定量证据[367][362]。 |

因此，PURE上的1.332%–1.637%误差与ReViSe的1.60%只能在相近数据、参考设备和统计口径下比较；LOSO跨设备结果达到4.22%–4.45%，显示设备、人群和采集域会显著改变结果。决定性条件是面部ROI、低氧范围、受试者独立划分及参考血氧仪。

边界证据中，2023年手机DNN研究使用公开的**指尖**视频（约70%–100%、LOO），报告MAE 1.97%、RMSE 2.92%，但不属于面部视频；另一项2023年指尖研究纳入35名志愿者，参考SpO2仅95%–99%，ratio-of-ratios与血氧仪无相关性，未继续回归，故没有可用SpO2性能[366][367]。PMDE数据采集工具则把RGB面部视频与ECG（500 Hz）及SpO2（125 Hz）同步，50 fps视频同步误差小于40 ms，但数据集公开状态尚未确认[352]。2026年发布的MPU-rPPG资料晚于本报告截止日，不纳入历史截面[365]。

**研究证据与范围边界**

ReViSe（Qiao等，2022）是本节中同时符合“普通智能手机面部视频—SpO₂—带数值性能”条件的直接证据：端到端 rPPG 通过深度网络定位面部标志点、生成多个 ROI，并滤波恢复 BVP；在公开 PURE 上报告 SpO₂ MAE=1.64%（原始摘要未说明参考血氧仪、SpO₂范围、主体划分、统计分母及百分点定义）[152]。

|研究|方法、数据与结果|
|---|---|
|Jalil与Lionetti，2023，*E-Health monitoring using camera*|普通 RGB/HD webcam 面部视频；Viola–Jones 人脸检测→ROI空间平均→中值/带通滤波→POS-iPPG。PURE含10人（8男、2女），30 Hz、640×480像素、约1.1 m，指夹式脉搏血氧仪提供SpO₂/HR参考；另采集15 s、30 Hz、轻微头动和变光照视频。结果仅称与参考值“similar/consistent”，未报告MAE、RMSE、MAPE或准确率，故不作为定量关键论文[253]。|
|Mathew等，2023，*Remote Blood Oxygen Estimation From Videos Using Neural Networks*|CNN从RGB时间序列估计SpO₂，但输入为手部而非面部视频；自采14人、56段、iPhone 7 Plus（30 fps），CMS-50E作参考，屏气范围89%–99%。参与者特异性Model 1–3的MAE（PD/PU）为2.12/2.16%、2.09/1.96%、1.93/1.81%；留一参与者测试中最佳PU/PD为1.97%/2.33%，属于范围外对照[368]。|
|Tian等，2021，*A Multi-Channel Ratio-of-Ratios Method for Noncontact Hand Video Based SpO₂ Monitoring*|多通道 ratio-of-ratios、HR引导自适应带通滤波和SVR，使用智能手机手部视频及CMS-50E参考；palm-up/palm-down的MAE分别为1.26%/1.28%，相关系数ρ为0.68/0.65，因非面部输入不纳入面部论文清单[369]。|

截至2020年9月的消费级面部视频综述纳入26项研究，但其中SpO₂研究为0项，显示早期公开证据明显不足[254]。2024年3月发表的VIPL-HR/STMap研究报告EfficientNet-B3+RGB的MAE=1.274%、RMSE=1.710%，并采用五折受试者交叉验证；该结果晚于2024-01-31，仅作边界参照，不纳入2020—2023年清单[370]。

Cheng等（2023）《Using Contactless Facial Image Recognition Technology to Detect Blood Oxygen Saturation》：普通网络摄像头拍摄额头ROI，提取R/B通道并滤波；自建30人、60个测试点，以台湾认证血氧仪为参考，SpO2 MAE=0.62%、最大误差2%（60 cm、300–650 lux、静止）。[376]

红外研究（2023）采用EVM+红外摄像头，21人、每次2 min、1920×1080/30 fps，固定距离并进行正常呼吸/屏气；Extra Trees的RMSE=1.171%、MAE=0.960%、MAPE=0.010（单位未报告），属非RGB对照。[374]

2023年神经网络研究以预训练CNN+XGBoost，在UBFC-rPPG/VIPL-HR上的SpO2 MAE为0.84/1.17（单位未报告，候选证据）。 Lin等（2023）仅报告HR、SBP和DBP，SpO2未报告，私有288段视频不构成SpO2证据。[278][265]

ReViSe（2022）用手机面部rPPG以R/IR的AC/DC估计SpO2；公开PURE以指夹血氧仪作参考，MAE为1.64%（90–100%）[267]。

**补充的 SpO₂ 证据与可比性**

|研究（年份）|普通摄像头输入、方法与数据集|SpO₂结果与条件|
|---|---|---|
|ReViSe（Qiao等，2022）|智能手机面部视频；深度学习提取面部关键点，多ROI提取BVP并滤波；TokyoTech rPPG与PURE为公开数据集，SpO₂在PURE上验证|PURE上SpO₂ MAE为 **1.64%** [153]。原文未说明“%”是百分比还是百分点，也未报告参考血氧仪、SpO₂范围、训练/测试划分或统计分母；框架另在日常生活环境中验证。|
|*Evaluation of a Camera-Based Monitoring Solution…*（2022）|面部摄像扫描；摄像头距面部60 cm，固定三脚架并使用至少250 lux环形灯；受试者去除面部遮挡、静止直视摄像头60 s；脉搏血氧仪等医疗设备作参考；SpO₂样本235个，样本公开性未报告|在 **90%–100%** 范围内，ME为 **0.3%**；MAE为 **1.21**、RMSE为 **1.77**（该摘录未标明二者单位），RMSPE为 **1.85%** [43]；低于90%的样本有限，因此低氧验证不足。|

PURE包含10名受试者、60段约1分钟RGB视频，分辨率640×480、帧率30 Hz，含受控头部运动和室内自然光；参考脉搏信号由指夹式脉搏血氧仪获取[371]。另一资料将SpO₂参考设备列为CMS-50E、范围列为90%–100%，但不能补足ReViSe未报告的测试划分[372]。

普通RGB网络摄像头的交流分量具有低信噪比，RGB组合也可能引入缺陷；盲源分离、混合矩阵能量系数和稳定片段选择可改善抗噪性，但所示片段未报告MAE或RMSE，因此仅作为方法证据，不参与性能排名[168]。医疗设备PPG输入的MIMIC-III模型虽在1,732名受试者上报告SpO₂ MAE **0.58±0.79%**，但不是面部视频，不能与上述结果直接比较[82]。同理，2024年3月VIPL-HR研究的MAE **1.274%**、RMSE **1.71%**晚于2024-01-31，不纳入本节历史截面[373]。

ReViSe（2022）以智能手机面部视频rPPG在公开PURE上测SpO₂，MAE为1.60%[158]；Lin等（2023）未报告SpO₂结果[266]。

rejected: number_unsupported；血氧饱和度（SpO2）目前更适合判为“可行但条件性成熟”，而非临床成熟：面部/手机路线报告MAE 0.62%，ReViSe报告1.64%，另有留一受试者总体误差0 ± 1.141%[119][267][361]。结果依赖脉搏血氧仪参考、520 – 580 nm的颜色吸收条件及受试者留出测试，故不能据此与其他体征作无条件成熟度排序[146][267][361]。

SpO2使普通摄像头面部视频成为可验证的非接触任务：在人脸ROI逐帧汇聚RGB/BGR形成rPPG，再按颜色/波长吸收比或CNN回归百分比；已有RGB面部方法报告平均误差1.4%[86][146][97][191]。结果应与指夹式脉搏血氧仪的红光/红外读数同步比较，并明确百分比或百分点口径；动脉血气得到的SaO2是更严格的金标准，研究范围示例为85–100%[62][98][347]。

本节能统一的定义是SpO2为血氧百分比，以指夹脉搏血氧仪的红光/红外吸收为常用参考，动脉血气是更准确的参考；HR的bpm、SBP/DBP的mmHg及其参考设备未在本节形成同口径事实[343][346]。按信号/模型，SpO2可分为颜色通道与ROI-rPPG（RGB/BGR、GREEN、ICA/CHROM/POS）、RoR/AC–DC及时频分析，以及视频放大、STMap、CNN和中后期/端到端融合；前者恢复脉动/吸收比，后者学习时空映射，但均受光照、距离、运动和设备差异约束[190][192][98][376][344]。

SpO2及其论文候选直接服务总体目标：普通摄像头面部ROI→rPPG/PPG→吸收比或CNN，既可回归连续百分比，也可按阈值筛查[86][97]。2023手机面部研究报告MAE 0.62%，2022 ReViSe在公开PURE上报告1.64%，并以脉搏血氧仪作参考，因而同时贡献方法、数据集属性和数值性能证据[94][119][152][267]。

可核验的SpO2论文信息为：Petersen等2023手机面部RGB/rPPG+CNN，MAE 0.62%，数据集信息未找到证据；2022 ReViSe采用端到端面部rPPG，在公开PURE上MAE 1.64%，并另建Video数据；STMap+2D-CNN候选使用公开VIPL-HR和五折受试者验证，MAE 1.274%、RMSE 1.71%，但出版日期列有2024/2023冲突[94][119][152][267][358]。因此方法、数据集公开/自建属性、协议和单位只能部分填齐，日期和缺失信息应保留为证据缺口，不能把候选结果当作已确认的2020—2023论文[358]。

原因机制是SpO2依赖Hb/HbO2的多波长吸收，而普通RGB与环境光提供的是宽带、易变的反射信号；反射式弱信号、运动、照明/距离和肤色会改变rPPG或脉搏血氧仪标签[190][344][343][103]。深度模型和RoR归一化可学习或校正跨用户、摄像头和光照差异，但小型、健康、受控数据仍限制外部泛化[190][356]。

公开数据证据中有71名健康志愿者、110段记录、50Hz和1080P，另有条目仅15名/40次或5名受试者，说明人口、设备和样本规模仍窄；SpO2参考多为脉搏血氧仪，公开性和设备组合也不统一[377][343]。固定光照、背景和距离不能代表野外，肤色、低氧分布和参考设备偏差会使深度模型学习域/设备捷径，削弱跨人和跨设备泛化；单中心或单设备设计进一步限制外部验证[377][103][172]。

### 3.2 主流路线及其可观测信息

**BP是间接估计任务。**rPPG主要反映局部血容量变化，而不是直接测量血管内压力。BP还受心脏泵血、动脉弹性、外周阻力和血容量影响。因此，从面部颜色到绝对SBP/DBP，存在个体差异显著的映射。[27]

| 路线 | 输入信息 | 代表研究 | 主要优势 | 主要代价 |
|---|---|---|---|---|
| PTT/相位差 | 两部位或多ROI脉搏时差 | Wu等、Lin等 | 有传播时间依据 | 时差精度与校准敏感 |
| 波形特征回归 | 时间、幅值、面积、频谱 | 闫昊等 | 特征可解释、适合小数据 | 波形细节容易失真 |
| 视频时空回归 | 多ROI颜色时空图 | BPE-Net | 联合学习时空特征 | 容易依赖训练BP分布 |
| 合成增强 | 真实波形加条件生成 | Wu等、InfoGAN扩展 | 扩大训练分布 | 合成真实性影响外推 |
| 接触式迁移 | 大规模PPG预训练再迁移 | ReViSe、Kim等 | 利用既有生理数据库 | 接触与远程模态存在差异 |

**PTT需要真实传播信息。**脉搏传导时间PTT描述脉搏在不同位置间的传播时差。两个面部ROI的相位差可以成为预测特征，但不应自动等同于沿已知动脉路径测得的标准PTT。只拍单一面部ROI时，更难获得独立传播路径的信息。[8]

**普通帧率限制时差观测。**30 fps的相邻帧间隔为 \(1000/30=33.3\) ms；60 fps为16.7 ms。插值可以细化数值采样网格，却不会凭空增加原始摄像头的时间信息。对平均HR而言，若干周期已可用于估计主频；对细小传播时差而言，采样、曝光与同步要求更高。

**波形正确比频率正确难。**闫昊等比较视频脉搏与指尖PPG时发现，部分视频波形重搏波消失。其特征表中，若干谱特征的误差较小，而单周期半幅宽等形态特征的MAPE达到68.800%和84.283%。这说明“主频相近”并不保证所有BP相关形态都被保留。[27]

### 3.3 大队列与生成增强：Wu等研究

**2022年队列规模较突出。**Wu等《Contactless Blood Pressure Measurement via Remote Photoplethysmography with Synthetic Data》在台湾与医疗机构合作，采集1,138名18—92岁参与者。包括860名男性、278名女性，也包含高血压、糖尿病和心脏病患者。[4]

**主体隔离比片段数量重要。**每人录制80秒，Logitech C920距脸约60 cm，以640×480、30 fps、8-bit无损格式采集。训练与测试分别为961人和177人，血压参考为水银血压计。它比把同一个人的相邻视频片段随机分开，更直接检验新受试者上的预测。[4]

**模型联合利用两类线索。**研究从上、下半脸提取CHROM-rPPG，以带对称跳跃连接的编码器—解码器处理信号。InfoGAN按年龄和BMI等条件生成波形，缓解真实数据稀缺。最终视频rPPG测试MAE为SBP 9.13 mmHg、DBP 8.76 mmHg。[4]

**2023年扩展改善内部误差。**《Contactless Blood Pressure Measurement via Remote Photoplethysmography with Synthetic Data Generation Using Generative Adversarial Networks》结合30 fps面部信号的时间差、多模型设计、InfoGAN及受试者BP信息。自建数据中，SBP MAE由15.49降至8.78 mmHg，DBP由10.56降至6.16 mmHg。[26]

**改善幅度可以计算。**按论文端点，SBP相对降低约43.3%，即 \((15.49-8.78)/15.49\)；DBP约降低41.7%，即 \((10.56-6.16)/10.56\)。这是同研究增强前后的收益，不是与其他论文之间的相对优势。

**夜间结果属于另一成像层。**该方法在TVGH夜间红外数据上，将SBP/DBP MAE从21.58/9.74降至11.12/7.59 mmHg。它说明生成增强也可能帮助夜间应用，但使用红外照明，不能直接代表普通手机RGB前置摄像头的夜间能力。[26]

### 3.4 时空回归：BPE-Net的内部与跨库差距

**BPE-Net直接处理时空图。**研究使用额头和脸颊ROI，构建改进YUV时空图，再切成片段交给残差网络和LSTM。输出先判断BP区间，再计算区间内具体数值。其设计意图是让回归具有区间参照，并通过过采样处理BP分布不平衡。[13]

**最优切片并非越长越好。**在MPM-BP五折实验中，150帧切片达到SBP/DBP MAE 8.07/6.78 mmHg，RMSE 9.94/8.45 mmHg。30 fps下150帧对应5秒，计算为 \(150/30=5\) 秒。论文认为更长切片可能纳入更多非生理扰动。[13]

| BPE-Net设置 | SBP MAE（mmHg） | DBP MAE（mmHg） | SBP RMSE（mmHg） | DBP RMSE（mmHg） |
|---|---:|---:|---:|---:|
| MPM-BP内部、150帧 | 8.07 | 6.78 | 9.94 | 8.45 |
| MPM-BP→MMSE-HR、150帧 | 12.35 | 9.54 | 16.55 | 12.22 |
| MPM-BP→MMSE-HR、225帧 | 13.15 | 按论文区间回归设置 | 17.12 | 13.22 |

**跨库结果改变用途判断。**内部验证支持模型能从本队列提取BP相关信息；跨库结果则表明，设备、年龄和标签分布变化后，误差仍会上升。MPM-BP集中于18—24岁，使用Huawei Mate30、1920×1080、30 fps，距脸约0.5 m；MMSE-HR包含不同表情、头动与人口构成。[13]

**正常区间更易预测。**论文指出SBP 110—130 mmHg、DBP 60—80 mmHg的预测更好，并将其与训练分布不平衡联系起来。重复采样能调整训练权重，却不能替代真实的高低血压参与者。对临床用途而言，极端区间的误差常比总体均值更有决定性。[13]

### 3.5 小样本特征回归与迁移学习

**闫昊等保留可解释特征。**其2023年论文《基于视频流的非接触式连续血压检测算法研究》使用CDF与ICA提取视频脉搏，再对78项时间、幅值、面积和变换域特征进行集成选择。最终以6项较能跨PPG与vPPG保持一致的特征输入SVR。[27]

**训练与视频验证分两层。**研究筛选MIMIC的102名受试者数据进行模型与特征分析。视频验证则来自5人、100组约2分钟记录，Canon EOS 60D以1280×720、60 fps拍摄，BIOPAC MP160采集连续BP与指尖PPG。最终视频SBP/DBP MAE为4.9/4.6 mmHg，STD为5.9/5.0 mmHg。[27]

**低误差支持受控可行性。**这组结果说明经过筛选的频谱与时间特征，可以在特定采集条件下转移到视频信号。它不等于已经覆盖大量新个体。100组视频依然只有5个独立主体，重复记录主要增加主体内变化。

**Kim等利用接触式大数据。**其2023年U-Net Basic研究先处理公开MIMIC-II数据，再迁移至Leipzig医院来源的17人面部rPPG。论文的MIMIC-II部分含125 Hz的PPG、ECG和ABP，切成528,753个5秒片段。面部rPPG部分为7,852个处理样本，采用5秒输入与8∶2划分。[11]

**采样频率不是视频帧率。**该研究将处理后的rPPG信号描述为125 Hz，这不能直接解释为USB摄像头以125 fps录制。模型最终MAE为SBP 6.90 mmHg、DBP 4.43 mmHg，BHS分级为SBP C级、DBP A级。片段划分结果与“完全未见主体”的验证应分别理解。[11]

**先前迁移结果并不总是更低。**Kim等转述Schrumpf等2021年《Assessment of Non-Invasive Blood Pressure Prediction from PPG and rPPG Signals Using Deep Learning》：接触式模型经rPPG重训后，SBP/DBP MAE为13.6/10.3 mmHg；个性化后约为12.7/10.5 mmHg。个性化改善SBP，并未同时改善DBP，说明校准收益不能笼统外推。[11]

**Lin等组合多种线索。**其自建数据使用面部和颈部ROI，视频放大后提取HR、PTT及波形特征，再由小型两阶段CNN估计BP。以Omron HEM-7124为参考，测试集SBP/DBP RMSE为4.11/3.75 mmHg，MAPE为3.73%/4.95%。这些结果属于理想照明下的自建实验。[22]

### 3.6 医院结果与标准：为什么平均偏差会误导

**医院结果揭示绝对误差。**Talukdar等论文《Evaluation of a Camera-Based Monitoring Solution Against Regulated Medical Devices to Measure Heart Rate, Respiratory Rate, Oxygen Saturation, and Blood Pressure》包含463个BP配对读数。SBP/DBP参考来自OMRON、CIRCA MICRO LIFE和NIDEK等设备。[2]

| BP指标 | ME（mmHg） | MAE（mmHg） | RMSE（mmHg） | RMSPE |
|---|---:|---:|---:|---:|
| SBP | −5.27 | 18.15 | 22.77 | 17.59% |
| DBP | −3.95 | 10.49 | 13.71 | 17.38% |

**小偏差不等于小误差。**SBP平均偏差为−5.27 mmHg，看似接近零，但MAE达到18.15 mmHg。正负误差抵消可以满足宽松的ME目标，却不能保证单个患者读数可靠。论文摘要所称达到“±10 mmHg平均误差假设”，应按ME理解，不能改写成MAE小于10 mmHg。[2]

**极端区间更具挑战。**该研究SBP高于130 mmHg组的MAE为24.69 mmHg，DBP高于90 mmHg组为20.68 mmHg。结果提示模型存在向常见范围收缩的风险；但仅凭误差表，尚不能把这种模式完全归因于训练分布、校准或某个特定算法环节。[2]

**标准是整套验证协议。**BHS分级依据不同误差阈值下的累计比例。按闫昊等列示的BHS口径，A级要求如下。[27]

| BHS等级 | 误差≤5 mmHg | 误差≤10 mmHg | 误差≤15 mmHg |
|---|---:|---:|---:|
| A | ≥60% | ≥85% | ≥95% |
| B | ≥50% | ≥75% | ≥90% |
| C | ≥40% | ≥65% | ≥85% |

**单一阈值不能代表认证。**BPE-Net报告误差小于10 mmHg的比例为SBP 74.2%、DBP 78.8%，低于其引用的85%比较门槛。AAMI/ESH/ISO评价还涉及样本组成、重复测量和完整流程。因此，论文中“误差满足某数值要求”，与设备完成规范临床验证，是不同层次的结论。[13]

**小样本尤其需要谨慎。**闫昊等按其误差结果称符合AAMI及BHS A级，但同文列出的AAMI人数要求为至少85人，而最终视频验证为5人。合理的表述是：其受控视频误差达到论文采用的比较范围；不能把这一结果扩大为完整的视频设备认证。

**本节判断。**BP已有清晰的算法进展和mmHg级研究结果，但其成熟度主要受绝对值映射、个体校准、标签与外部人群验证制约。

## 四、血氧：普通RGB已能估计，但低氧与光谱稳定性决定实用边界

### 4.1 关键论文与定量结果

**SpO2总体误差常在低位。**公开VIPL-HR、PURE以及部分小型受控实验，报告过约1—2个百分点的MAE或RMSE。决定用途的不是这一总体数字，而是测试血氧范围、低氧样本占比、光照及受试者隔离方式。

Qiao等（2022）的ReViSe使用智能手机面部视频、多ROI rPPG/BVP和深度模型，在公开PURE上报告SpO2 MAE为1.64个百分点。

| 论文、作者与年份 | 核心方法 | 数据集及属性 | 实验与参考 | 关键性能 |
|---|---|---|---|---|
| Qiao等，ReViSe，2022 | 多ROI rPPG、滤波与估计 | PURE，公开 | PURE同步脉搏血氧参考 | MAE 1.64个百分点 |
| Cheng等，2022 | STMap、EfficientNet-B3 | VIPL-HR，公开 | 70∶30主体划分；CMS60C | MAE/RMSE 1.012/1.473个百分点 |
| DC/AC-STMap作者组，2022预印本 | ResNet18、DC/AC双分支 | 自建50人面部视频 | 五折40/10人；OxyTrue A | Filter 1.17/1.40，条件百分点 |
| Talukdar等，2022 | BGR-rPPG、固定SDK | 医院自建队列 | 235个读数；脉搏血氧仪 | MAE/RMSE 1.21/1.77个百分点 |
| Chan等，2023 | 红/蓝、红/绿RoR | 自建2人降氧实验 | LOSO；Transfer Standard血氧仪 | RMSE 1.93个百分点；PCC 0.97 |
| Petersen等，2023 | 手机额头rPPG、信号处理 | 自建10名健康人 | 理想照明；92%—99% | Arms 1.34；MAE 1.26个百分点 |
| Stogiannopoulos等，2023 | 红外EVM、特征回归 | 自建21人红外视频 | 正常呼吸/屏息；JPD-500D | RMSE 1.331个百分点；R² 0.465 |

来源依次为ReViSe [21]、Cheng等基准[3]、DC/AC-STMap [28]、医院评估[2]、Chan等[29]、Petersen等[14]和Stogiannopoulos等[30]。

**普通RGB与红外分层。**上表最后一项采用Nest Cam红外常开模式，属于补充成像证据。其低误差说明特定红外数据可进行统计回归，但不证明普通RGB摄像头具备相同光谱信息。

### 4.2 双波长思想如何转为RGB通道方法

**SpO2需要光谱差异。**氧合与脱氧血红蛋白对不同波长的吸收不同。接触式脉搏血氧仪利用双波长观测，将脉动成分与背景成分分离，再经标定得到SpO2。普通RGB方案借用这一思路，但RGB通道是宽频带响应，不是理想的窄带测量。[7]

**红蓝通道不是红外替身。**普通相机中的蓝通道不等于940 nm近红外。红/蓝或红/绿方案使用的是可见光条件下的替代光谱观测，需要针对光源、相机响应和数据进行标定或学习。由RGB计算出的通道比，与专用红光—红外硬件的物理条件并不相同。[29]

**AC与DC各有作用。**AC表示随心搏变化的脉动分量，DC表示慢变基线。比值之比RoR先在每个通道内归一化脉动强度，再比较两个通道。以红、蓝通道为例，可概括为：

\[
R=\frac{AC_{\mathrm{red}}/DC_{\mathrm{red}}}{AC_{\mathrm{blue}}/DC_{\mathrm{blue}}}
\]

**校准关系不是通用常数。**传统方法再使用经验线性关系或回归，将 \(R\) 映射到SpO2。Cheng等在VIPL-HR上比较两组RoR系数，得到明显不同的误差，说明参数不能脱离相机和照明直接移植。[3]

| VIPL-HR方法 | 输入或参数 | MAE（百分点） | RMSE（百分点） |
|---|---|---:|---:|
| RoR基线一 | A=125，B=26 | 3.334 | 5.137 |
| RoR基线二 | A=101.6，B=5.834 | 1.838 | 2.489 |
| EfficientNet-B3 | RGB与YUV时空图 | 1.012 | 1.473 |

**深度模型学习更复杂映射。**RGB+YUV模型在这一主体划分下优于两组RoR基线，说明数据驱动映射能利用额外时空信息。但其优势也可能依赖训练分布与设备条件，不能由此推导在任何光源下都胜过物理比值方法。

### 4.3 公开基准：Cheng等的正常与异常差距

**公开血氧基准具有价值。**Cheng等2022年《An Algorithmic Benchmark for Contactless SpO2 Measurement from Facial Videos》将225个连续帧编码为STMap，使用2D CNN回归。VIPL-HR按受试者做70∶30训练与测试划分，避免同一人的不同视频同时进入两侧。[3]

Cheng等（2022）将225个连续帧编码为STMap，并用2D CNN的EfficientNet-B3在公开VIPL-HR的70∶30受试者级划分上回归SpO2；RGB+YUV输入的MAE/RMSE为1.012/1.473个百分点，正常范围为0.978/1.288个百分点，异常范围为3.077/3.563个百分点。

**异常范围误差明显升高。**EfficientNet-B3的RGB+YUV输入总体MAE为1.012个百分点；正常范围SpO2≥95%时为0.978，低于95%时为3.077个百分点。RMSE也从1.288升至3.563个百分点。[3]

**差距不只是小幅波动。**按论文数值，异常范围MAE约为正常范围的3.15倍，计算为 \(3.077/0.978\)。作者将这一现象与低血氧训练样本较少联系起来。对读者而言，整体MAE约1个百分点，不能直接理解为低氧报警也有同等误差。

**设备比较仍是混合域测试。**VIPL-HR包括Logitech C310、Huawei P9和RealSense F200 RGB输入。研究在各设备分层中比较模型，认为低分辨率可能影响RoR表现。但混合设备上的主体划分，不等同于完全留出一种新相机的外部验证。[3]

### 4.4 生理先验网络与多模型融合

**DC/AC网络保留测氧结构。**《Blood Oxygen Saturation Estimation from Facial Video via DC and AC Components of Spatio-temporal Map》显式分离时空图的DC和AC，再由预训练ResNet18分支提取特征。CNN-Filter采用滤波提取，CNN-EndToEnd将成分提取纳入可学习流程。[28]

**主体独立设置较明确。**研究自建50人数据，每人录制3分钟，使用Logitech C920n HD PRO、30 fps，并以OxyTrue A记录SpO2。每个约60秒周期包含约30秒屏息和30秒休息，共重复3次。五折验证每次40人训练、10人测试，输入为300帧即10秒。[28]

| 模型 | MAE数值 | RMSE数值 | 相关系数 | 单位解释 |
|---|---:|---:|---:|---|
| CNN-Filter | 1.17 | 1.40 | 0.474 | SpO2百分数尺度下为百分点 |
| CNN-EndToEnd | 1.18 | 1.40 | 0.496 | SpO2百分数尺度下为百分点 |

**先验有助于小数据学习。**显式DC/AC结构限制了网络的搜索空间，使模型围绕脉搏血氧的主要观测关系学习。两种模型误差接近，说明端到端提取可以在此队列中接近显式滤波。但约0.47—0.50的相关系数也提示：较低平均误差不必然代表很好地跟踪个体血氧变化。[28]

**融合路线结合两类信息。**Hu等2023年《Contactless Blood Oxygen Estimation from Face Videos: A Multi-model Fusion Method Based on Deep Learning》使用残差与坐标注意力网络RCA，结合颜色通道模型CCM、网络模型NBM及多模型融合MMFM。其CCM重建红蓝通道并利用AC/DC比，数据来自公开PURE与VIPL-HR。[31]

**阈值与观测值分开。**该研究讨论MAE为2个百分点的临床要求判据。这里将2个百分点保留为判据，不把它冒充模型实测误差；其方法位置则由同一公开数据路线中的ReViSe MAE 1.64个百分点、Cheng等MAE 1.012个百分点提供量化参照。前者衡量信号处理与多ROI方案，后者衡量STMap深度回归，均不是MMFM自身误差的替代值。

### 4.5 主动降氧、手机与红外实验

**Chan等扩大了血氧范围。**其2023年消费级RGB实验关闭自动调参，在四种光照下比较红/蓝和红/绿RoR。研究通过受控吸入气体将SpO2降至81%，使用Transfer Standard Pulse Oximeter作参考。两名受试者LOSO中，暖色温、正常亮度条件的RMSE为1.93个百分点，PCC为0.97。[29]

**范围宽与人群广不同。**降至81%比只测试健康正常范围更直接触及低氧问题，但两名参与者仍不足以覆盖肤色、年龄和血管差异。相反，大样本正常血氧数据可支持人口分析，却不一定支持低氧性能判断。两类实验各补一种信息，不能互相替代。

**Petersen等验证完整手机链。**Petersen、Kjær与Sørensen的《Remote Estimation of Peripheral Oxygen Saturation and Pulse Rate From Facial Analysis Using a Smartphone Camera》使用手机前置摄像头和额头rPPG。10名健康参与者在理想照明下执行不同呼吸模式，SpO2范围92%—99%，Arms为1.34个百分点，MAE±STD为1.26±0.68个百分点。[14]

**同一手机实验也报告脉率。**其60—90 bpm范围内的脉率Arms为3.91 bpm，MAE±STD为3.24±2.11 bpm。该结果支持消费级前置相机完成端到端采集的可行性，但指标范围和理想照明是其性能定义的一部分。[14]

**红外EVM属于补充证据。**Stogiannopoulos、Cheimariotis与Mitianoudis自建21人数据，每人正常呼吸和屏息各2分钟。Nest Cam使用红外常开、1920×1080、30 fps，距离75 cm，以JPD-500D脉搏血氧仪为参考。研究从额头和双颊提取12项放大PPG特征，比较GAM、Extra Trees、3D CNN和ViViT，最佳RMSE为1.331个百分点，\(R^2=0.465\)。[30]

**低误差不证明光谱可辨识。**单通道红外回归可以利用与血氧相关的统计变化，但它与双波长吸收比法的可观测信息不同。若训练数据同时包含屏息、呼吸模式和血氧变化，模型也可能利用这些相关因素。要判断其是否稳定识别血氧本身，需要看独立条件下的表现。

**更宽设备实验给出反例。**2023年一项KNN普通RGB研究在海拔3,150 m和102 m构建数据，60人参与。LOSO下，手机、网络摄像头、工业相机的MAE分别为4.39、4.45、4.22个百分点。这是普通RGB多设备的边界参照；其面部适用性以ROI确为面部为条件，不与前述面部专门基准混排。[32]

### 4.6 医院血氧结果：总体误差怎样掩盖低氧风险

**分层结果比总体更有用。**Talukdar等的235个SpO2读数，总体MAE/RMSE为1.21/1.77个百分点。但90%—95%与高于95%的结果差异明显。[2]

| 参考SpO2范围 | 配对读数 | ME（百分点） | MAE（百分点） | RMSE（百分点） |
|---|---:|---:|---:|---:|
| 全部读数 | 235 | 0.30 | 1.21 | 1.77 |
| 90%＜SpO2≤95% | 28 | 3.64 | 3.64 | 3.80 |
| SpO2＞95% | 207 | −0.15 | 0.88 | 1.26 |

**低氧样本少但误差集中。**28/235约为11.9%的读数处于90%—95%组。它们贡献约35.9%的绝对误差总和，计算为 \((28×3.64)/(28×3.64+207×0.88)\)。因此总体MAE被大量正常读数显著拉低。

**偏差方向影响安全意义。**低氧组ME与MAE同为正3.64个百分点，表明该组存在明显高估。对于希望发现血氧下降的应用，高估比同样大小的随机正负误差更值得关注。这里的结果说明该版本和协议的风险，不应泛化为所有视觉血氧算法的固定偏差。

**本节判断。**SpO2已经具备普通RGB可行性和公开基准，但临床意义取决于低氧范围的偏差、动态跟踪与跨光照、跨设备稳定性。

## 五、公开数据集：规模、视频规格、参考信号与任务适用性

### 5.1 常用真实面部视频基准

**先按标签选数据。**用于HR训练的数据，不一定包含BP或SpO2标签。数据集中使用了“脉搏血氧仪”，也不自动意味着发布文件包含可直接训练的SpO2时间序列。下表把真实采集库与后面的合成库、申请资源分开。

| 数据集与访问类型 | 受试者数量 | 视频/样本数量 | 视频规格 | 生理信号 | 主要条件 |
|---|---:|---|---|---|---|
| UBFC-rPPG，公开研究库 | 主集42；合并记载50人 | 主集42；两子集8+42=50段 | 28—30 fps；640×480 | PPG、HR | 静止、限时数学游戏 |
| PURE，公开研究库 | 10人，8男2女 | 60段，每人6段 | 30 fps；640×480 | PPG、SpO2、脉率 | 静止、说话、平移、转头 |
| VIPL-HR，公开研究库 | 107人 | RGB 2,378；NIR 752段 | 25—30 fps；多分辨率 | PPG、HR、SpO2 | 九类场景、多设备 |
| MMSE-HR，公开研究库 | 40人 | 102段 | 25 fps；原幅按帧头口径 | HR、BP | 表情、头动、无妆 |
| COHFACE，公开研究库 | 40人，12女28男 | 160段，每段1分钟 | 20 fps；640×480 | BVP、HR、呼吸 | 自然/工作室光、强压缩 |
| OBF，公开研究基准 | 100健康人；6例AF扩展 | 健康RGB 200段 | RGB 60 fps；1920×1080 | ECG、BVP、呼吸 | 静息、运动后、复律前后 |
| UBFC-Phys，公开研究库 | 56人，46女10男 | 168段 | 35 fps；1024×1024 | BVP、EDA、皮温 | 休息、讲话、算术 |
| MMPD，公开研究库 | 33人 | 660段，每段1分钟 | 30 fps；720p→320×240 | 同步PPG | 四种肤色、光照、活动 |
| MAHNOB-HCI，申请研究库 | 27人，15女12男 | 527段视频序列 | 61 fps；780×580 | ECG及其他生理信号 | 情绪视频刺激、重压缩 |
| UCLA-rPPG，公开评测资源 | 98人 | 清理后488段 | 30 fps；约1分钟/段 | 同步HR参考 | 多段录制、未压缩视频 |

主要来源为UBFC官方说明[33]、PURE原始规格的论文描述[17]、VIPL-HR原始说明[34]、MMSE-HR说明[13]、COHFACE官方页[35]、OBF原论文[36]、MMPD原论文[5]、CameraVitals目录[37]及UCLA/UBFC-Phys评测说明[19]。

**VIPL-HR并非单一视频规格。**Logitech C310为960×720、25 fps；Huawei P9前置摄像头为1920×1080、30 fps；RealSense F200的RGB为1920×1080、30 fps，NIR为640×480、30 fps。RGB实验包含稳定坐姿、大幅头动、朗读、明暗光、距离变化、运动后和手持手机等条件。[34]

该库的107名受试者中，79名为男性、28名为女性，年龄约22—41岁。

按基准论文的细分，VIPL-HR包含九类RGB场景：稳定坐姿、大幅头动、朗读、暗/亮环境、1.5 m距离、运动后、手持手机及手持手机并大幅头动；该库主要支持HR，也支持SpO2基准。

**PURE运动可控但人数少。**六项任务为静止、说话、慢速平移、快速平移、较小转头和较大转头，转角约20°与35°。其优势是可以比较运动类型；主要统计单位仍然是10名参与者，而不是60段独立人群样本。[17]

**UBFC版本应明确。**常见HR论文使用第二子集共享的42段视频；另有评测把8段静止子集与42段游戏子集合并为50段。选择42段还是50段，会改变输入场景和测试集合，不能只写“在UBFC上验证”而省略子集。[33]

**OBF提供较强参考体系。**其RGB、NIR、ECG、BVP与呼吸同步采集；NIR为640×480、30 fps，ECG/BVP/呼吸采样率为256/128/32 Hz。原版包括100名健康人和6名房颤患者，每人两次5分钟。按该协议，患者扩展对应 \(6×2=12\) 段每模态记录，健康部分对应200段。[36]

**OBF并非自然场景库。**采集使用固定1 m距离、两侧灯光与受控坐姿，适合分析较干净的波形和心搏间期。运动后采集也不等于边运动边拍摄。它与MMPD行走自拍所检验的难点不同。

**MMPD贴近手机域。**数据由Samsung Galaxy S22 Ultra采集，原始1280×720、30 fps，发布处理为320×240。660段各60秒，共11小时；帧数计算为 \(660×60×30=1,188,000\) 帧，与论文一致。PPG由200 Hz降至30 Hz对齐视频。[5]

**条件覆盖不是完整交叉。**MMPD包含四种光照、四种活动及运动后场景，但不能把660段简单解释为所有人、肤色、光照和动作的完整均衡组合。分析应使用其条件标签，避免把不同因素的分组结果当作独立因果效应。

### 5.2 BP、多任务与合成资源

| 数据集与访问类型 | 受试者数量 | 视频/样本数量 | 视频规格 | 生理或合成标签 | 主要条件 |
|---|---:|---|---|---|---|
| BP4D+，研究数据 | 140人 | 1,400 trials及视频 | 24—25 fps；1040×1392 | 脉压波、BP、HR、呼吸、EDA | 10项情绪诱发任务 |
| V4V，公开挑战数据 | 179人 | 1,358段 | 25 fps；1040×1392 | HR、呼吸、连续BP | 情绪、自发表情、头动 |
| SCAMPS，公开合成库 | 0名真实受试者 | 2,800段；约168万帧 | 平均600帧/段；渲染文件口径 | 合成PPG、心搏、呼吸、面部动作 | 合成光照、表情、头动 |
| Aug-rPPG，公开增强库 | 42名原始主体 | 5,776段 | 面部200×200 | 嵌入指定PPG | 原视频与脉搏交叉组合 |
| Vital Videos/VV-Large，申请 | 近900人 | 约1,800段，估计 | 30 fps；1920×1200 | PPG、HR、SpO2、单次BP | 多地点室内、正视静止 |

来源为BP4D+工具箱说明[12]、V4V原论文[25]、SCAMPS及模拟标签说明[8]、Aug-rPPG [17]和Vital Videos [10]。

**V4V划分可以复现。**其179名参与者年龄18—66岁，覆盖多个族裔群体。训练、验证、测试分别为100/39/40人，对应724/276/358段视频；人数与视频数分别相加为179和1,358。T6—T10常出现大于10°的头动。[25]

**BP标签来自接触式参考。**V4V采用Biopac NIBP100D获取SBP、DBP及1000 Hz连续BP波形，并由该波形提取HR。训练发布内容包含原始BP波形。它能够支持视觉BP研究，但挑战本身的参赛结果集中于HR，数据标签的存在与BP算法成绩应分别判断。[25]

**BP4D+不能当标准PPG。**其指套脉压波与PPG具有相同心搏周期，但波形形态与相位不同。rPPG-Toolbox因此提供POS伪标签训练选项。对于HR周期学习，这种处理可以有用；对于BP形态学习，则必须保留标签的压力性质。[12]

**合成库不等于临床队列。**SCAMPS提供精确同步的心脏、呼吸和面部动作信号，便于研究理想条件下的学习。其2,800段、168万帧对应平均 \(1,680,000/2,800=600\) 帧/段。该版本不包含真实BP或SpO2监督，不能承担这两项目标的临床验证。[8]

**Vital Videos覆盖三项目标。**Toye于2023年发布的《Vital Videos: A Dataset of Face Videos with PPG and BP Ground Truths》使用Basler acA1920-40uc，以1920×1200、30 fps录制。Contec CMS50D+提供60 Hz PPG及1 Hz HR/SpO2；Omron M7提供上臂袖带BP。[10]

**视频数量是近似计算。**每人两段30秒视频，近900名参与者，因此约 \(900×2≈1,800\) 段，属于估计总量。采集地点包含图书馆、养老院、购物中心和社区中心，但均为室内。每人BP只测一次，主要与第二段录制对应。

**访问条件影响使用决策。**Vital Videos提供VV-Small、VV-Medium、VV-Large：前两者分别为100和250人，Large为近900人。符合公开发表代码和模型等条件的非营利研究可申请免费使用，商业获益用途另谈许可和费用。[10]

### 5.3 HR、BP与SpO2任务适用性

**直接监督与预训练分开。**下表“直接”表示有对应目标标签或已明确用于该任务；“表征预训练”表示可利用视频或脉搏训练前端，但不能把它写成目标体征的监督成绩。“字段条件”表示能否直接监督，由发布的SpO2字段及许可决定。

| 数据集 | HR | BP | SpO2 | 最合适的用途 |
|---|---|---|---|---|
| UBFC-rPPG | 直接 | 表征预训练 | 字段条件 | 低成本HR基准 |
| PURE | 直接 | 表征预训练 | 直接 | 头动HR、面部SpO2 |
| VIPL-HR | 直接 | 表征预训练 | 直接 | 多设备与多场景 |
| MMSE-HR | 直接 | 直接 | 表征预训练 | 表情、头动、BP迁移 |
| COHFACE | 直接 | 表征预训练 | 表征预训练 | 光照与压缩影响 |
| OBF | 直接 | 表征预训练 | 表征预训练 | ECG对照、波形与HRV |
| UBFC-Phys | 直接 | 表征预训练 | 表征预训练 | 讲话、压力、算术 |
| MMPD | 直接 | 表征预训练 | 字段条件 | 手机、肤色与自然活动 |
| MAHNOB-HCI | ECG监督 | 表征预训练 | 表征预训练 | 情绪与压缩视频 |
| UCLA-rPPG | 直接 | 表征预训练 | 表征预训练 | 多主体HR评测 |

任务依据见公开数据目录[37]、rPPG-Toolbox [12]、MMSE-HR说明[13]和SpO2公开基准[3]。

| 数据集 | HR | BP | SpO2 | 标签解释 |
|---|---|---|---|---|
| BP4D+ | 直接 | 压力波监督 | 表征预训练 | 指套脉压波非PPG |
| V4V | 直接 | 连续BP监督 | 表征预训练 | 训练集含BP波形 |
| SCAMPS | 合成监督 | 表征预训练 | 表征预训练 | 该版不含BP/SpO2模拟标签 |
| Aug-rPPG | 嵌入PPG监督 | 表征预训练 | 表征预训练 | 扩充脉搏，不新增人群 |
| Vital Videos | 直接 | 单次袖带标签 | 直接 | BP对应一次测量 |

**同名版本不能相加。**VIPL-HR与VIPL-HR-V2不是同一套人数统计。V2官方页给出500人、2,500个RGB片段、960×720；每人从30秒视频按5秒步长切出5段10秒片段。它增加的是主体规模与短片段基准，不能把2,500段解释成2,500次独立采集。[38]

**许可也属于数据属性。**VIPL-HR-V2官方明确限大学和科研机构研究使用，不向公司提供。对工程团队而言，算法能否复现与数据能否用于产品开发，是两个独立判断。[38]

### 5.4 如何在这些数据之间作选择

**HR应组合不同难度。**UBFC与PURE适合建立基础性能；VIPL-HR增加设备与光照变化；UBFC-Phys增加讲话和压力；MMPD检验手机、肤色及行走。只在一个容易的数据集上降低MAE，不能回答后面几种条件下是否有效。

在统一评测中，UBFC-Phys讲话和算术条件下，EfficientPhys的MAE分别为15.32和15.65 bpm，PhysFormer分别为11.89和12.85 bpm；MMPD行走条件下，TS-CAN在UBFC/PURE训练下的MAE分别为24.91和27.21 bpm。

**BP应优先看标签结构。**MMSE-HR、BP4D+/V4V和Vital Videos都能支持BP相关研究，但分别强调视频与BP记录、连续压力波、单次袖带读数。连续波形适合研究动态关系；单次袖带标签主要检验个体绝对值，二者不可作为同一种监督样本。

**SpO2需要额外关注范围。**PURE与VIPL-HR能支持公开比较，Vital Videos能增加主体与地点。但如果目标是低氧预警，数据选择还必须看低于95%乃至更低范围的样本，而不是只看参与者总数。

**本节判断。**最有用的数据组合，不是视频最多的组合，而是目标标签、受试者隔离和真实使用条件最匹配的组合。

## 六、成熟度比较：HR领先，BP与SpO2的先后取决于评价轴

### 6.1 先比较证据，而不是混合误差单位

**HR领先有多重依据。**Selvaraju等2022年综述覆盖2018年1月至2021年4月，共104篇，其中单目标分类为HR 60篇、BP 6篇、SpO2 1篇，另有15篇多体征研究。这说明该综述窗口中的研究积累明显偏向HR，不是截至2023年底的完整文献计数。[39]

**不同综述的计数不能拼接。**Gupta等2022年面部HR/SpO2综述纳入50项，其中42项仅HR、5项仅SpO2、3项同时测两者。它与上述综述的纳入范围、时间和成像条件不同。两者共同支持HR证据更多，却不能用来直接计算统一市场份额或全球论文总量。[40]

| 比较轴 | HR | BP | SpO2 |
|---|---|---|---|
| 公开数据基础 | 多库、跨库、工具箱较充分 | 标签库较少且类型不一 | PURE/VIPL-HR已有基准 |
| 受控性能锚点 | PFE-TFA MAE 0.76—1.44 bpm | Wu MAE 9.13/8.76 mmHg | Cheng MAE 1.012个百分点 |
| 外部困难锚点 | 行走MAE 24.91—27.21 bpm | 医院MAE 18.15/10.49 mmHg | 低氧MAE 3.077个百分点 |
| 临床参考 | 已有ECG对照与医院评估 | 标准BP参考，但一致性差异大 | 脉搏血氧参考为主 |
| 核心推断难度 | 从周期求频率 | 从间接线索求绝对压力 | 从跨通道关系求氧合比例 |
| 成熟度判断 | 相对高，最接近实用 | 中低，绝对值验证受限 | 早期，低氧验证受限 |

表中锚点分别来自PFE-TFA [1]、MMPD [5]、Wu等BP [4]、医院评估[2]和血氧基准[3]。

**临床汇总支持但不包办结论。**2023年成人临床cPPG综述，在4项、148名患者的可比研究中得到HR平均偏差−0.13 bpm，95%置信区间−1.22至0.96 bpm。该合并证据含多摄像头及眼底等扩展成像，应作为临床成像背景；普通RGB面部任务更直接的锚点，是前文240个HR读数的MAE 3.09 bpm。[41]

**平均一致性不是全部可靠性。**合并平均偏差接近零，仍不能说明所有个体误差很小。运动导致的数据丢失、失败片段、异常心率和参考同步，同样决定临床可用性。成熟度判断因此要同时考虑准确性、覆盖条件和可复现程度。

### 6.2 生理与成像机制怎样造成差距

**HR保留周期即可获益。**即使波形幅度变化，或部分形态被压缩，主频仍可能正确。多个ROI空间平均、颜色投影和时间累积都能增强周期。因此，HR可从相对有限的信息中得到稳定平均值。

**BP需要更多不可见变量。**相同HR不对应唯一BP，相近PPG形态也不一定对应同一绝对压力。年龄、动脉僵硬、药物和外周阻力都可能改变映射。模型若只看到面部视频，必须通过训练数据或个体校准间接吸收这些因素。[27]

**SpO2依赖颜色关系稳定。**HR主要寻找共同周期，SpO2还需要比较不同通道中微弱脉动相对于基线的大小。自动曝光、白平衡、照明光谱和压缩若改变通道比例，就可能污染氧合线索。将RGB转换成YUV可以改变表示，却不会新增传感器本来未捕获的波长信息。

**更强网络不能补回信息。**深度学习可以更好地利用相关特征，也可能学习稳健表示。但如果训练只包含正常血氧，或BP标签每人只有一个值，网络并不能仅靠参数数量建立可靠的低氧动力学或个体内BP响应。

### 6.3 BP与SpO2为什么不作无条件第二、第三名

**按研究积累可偏向BP。**部分综述窗口中BP论文多于SpO2，且BP已有千人级自建面部队列。若问题是“哪项有更多算法与队列积累”，BP具有一定优势。[39][4]

**按医院平均误差可偏向SpO2。**在同一Vastmindz医院评估中，SpO2总体MAE为1.21个百分点，而BP的SBP/DBP MAE为18.15/10.49 mmHg。虽然不能跨单位直接相减，但相对于各自用途，BP绝对值偏差显然更突出；SpO2则在较低范围暴露高估问题。[2]

**严格先后取决于条件。**若评价目标是普通RGB临床监测，BP与SpO2的先后应由同一人群、同一摄像头和采集环境下的头对头结果决定。还需事先明确BP区间、低氧覆盖、是否个体校准，以及误差和失败率的评价标准。本文据此给出分级，而不以不同单位的小数大小排队。

**用途判断应有层次。**HR适合优先开展远程健康监测与场景化验证；BP适合研究绝对值、趋势和个体校准之间的关系；SpO2适合研究低氧分层与光谱稳健性。三者都不能仅凭单库平均误差，直接替代相应临床参考设备。

**本节判断。**最稳健的成熟度结论是HR明确领先；BP和SpO2分别受绝对压力映射与低氧光谱观测制约，不能共享一条简单的精度排名。

综合公开基准和低氧分层，SpO2截至2024年初可列为早期：已有约1%量级的结果，但研究数量少、低氧样本少、运动与光照外部验证不足，且不少论文依赖小型自建数据。

## 七、公开数据集的局限与深度学习泛化

### 7.1 小样本与片段膨胀

**有效规模看独立主体。**PURE有60段视频但只有10人；闫昊等有100组视频但只有5人；Kim等处理出7,852个面部rPPG样本，来源仍是17人。切片可以增加优化次数，却不会按相同比例增加年龄、血管状态和肤色多样性。

**旧有研究确以小队列为主。**Gupta等检索截至2021年5月的综述中，34项HR研究使用自建数据库，人数为4—117，均值25.82±25.11；SpO2自建队列人数为4—46，均值20.5±16.78。这个历史统计解释了增强与迁移学习为何受到重视，也不能覆盖后来所有新队列。[40]

**片段划分容易学到主体。**若同一人的邻近片段进入训练和测试，模型可能利用肤色、脸型、设备或该人的典型体征范围。即使没有明确身份标签，视频外观也可能泄露身份。受试者独立划分因此是跨主体泛化的最低要求。

**跨主体仍不是终点。**同一机构、同一相机、同一照明下的新受试者，只检验部分泛化。真正的家庭手机使用还叠加设备、拍摄距离、压缩和活动变化。应把“主体独立”和“跨数据集”作为两个独立结果，而不是互相替代。

### 7.2 人口、肤色与疾病分布

**人口报告本身不充分。**Gupta等50项面部研究中，只有3项即6%在临床条件下进行；14项即28%报告族群、皮肤颜色或肤色。21项即42%没有报告年龄。这样的数据结构，使“对所有人有效”缺少直接的人群依据。[40]

**肤色差异可见于跨库误差。**MMPD提供Fitzpatrick 3—6型。以UBFC或PURE训练的TS-CAN，在类型3上较好，在部分较深肤色组误差明显增加。[5]

| MMPD肤色组 | POS MAE（bpm） | UBFC训练TS-CAN（bpm） | PURE训练TS-CAN（bpm） |
|---|---:|---:|---:|
| Fitzpatrick 3 | 5.76 | 3.60 | 3.06 |
| Fitzpatrick 4 | 9.06 | 14.45 | 8.94 |
| Fitzpatrick 5 | 12.78 | 10.06 | 12.39 |
| Fitzpatrick 6 | 11.17 | 14.88 | 15.43 |

**不能把全部差异归于肤色。**MMPD的分组实验排除了部分运动、自然光和运动后条件，以减少混杂。但不同参与者仍具有其他差异，发布视频又经历压缩。因此这些结果证明相关条件下存在性能差距，不是对黑色素单一因果效应的精确估计。

**健康分布限制异常判断。**若HR大多处于正常范围、BP集中于常见区间、SpO2接近饱和，模型预测中间值就可能得到不错的总体MAE。BPE-Net正常BP区间更准确，以及两项血氧研究低氧误差升高，都与这一统计风险一致。[13][2]

**地域多样性不能只看名义。**Vital Videos虽覆盖多种肤色与年龄，作者仍指出西欧招募使皮肤颜色分布不平衡。人工Fitzpatrick标注也带有主观性。跨地区数据不仅增加人群，还可能增加照明、设备和操作习惯的差异。[10]

### 7.3 光照、头动、情绪与遮挡

**自然运动比设计动作复杂。**PURE的平移和转头有利于控制实验，但手机行走自拍包含相机与脸部的共同运动、曝光变化和背景变化。模型在一种运动上训练，不必然学会另一种运动。[5]

| MMPD活动 | POS MAE（bpm） | UBFC训练TS-CAN（bpm） | PURE训练TS-CAN（bpm） |
|---|---:|---:|---:|
| 静止 | 9.70 | 5.34 | 5.91 |
| 转头 | 7.50 | 11.73 | 8.92 |
| 说话 | 8.05 | 7.35 | 8.32 |
| 行走 | 17.05 | 24.91 | 27.21 |

**行走暴露训练分布边界。**TS-CAN在静止时优于POS，在行走时则落后。这个对比说明，深度模型在熟悉条件下可以更准确，但传统方法可能在陌生域保留相对优势。它并不意味着传统方法在所有自然条件下都更可靠。

**情绪同时改变信号和干扰。**V4V的恐惧、疼痛、愤怒等任务可改变真实HR，也会引发头动和面部表情。UBFC-Phys的讲话、算术任务同样叠加生理变化与视觉运动。模型若把动作强度当作HR线索，可能在实验任务内有效，却在真实生活中失效。

**遮挡会改变ROI选择。**口罩降低脸颊和口周可用像素，眼镜或眼部遮挡影响上半脸追踪。前文口罩实验说明，增加遮挡训练能部分恢复性能，但恢复程度还依赖人脸标记器。对BP与SpO2而言，遮挡还可能改变可比较的ROI或颜色统计。

**光照不是单一亮度参数。**相同照度下，不同光谱、方向、阴影和高光也会改变RGB响应。HR可借共同周期抵抗部分变化；SpO2通道比对光谱变化更直接敏感；BP波形微小细节则容易在低信噪比下失真。只记录“室内”或“自然光”，不足以充分解释差异。

### 7.4 设备、分辨率与压缩的混杂

**相机链会重写生理线索。**传感器光谱响应、自动曝光、白平衡、降噪、美颜、编码与帧率控制，都会影响微弱颜色变化。高分辨率增加像素，并不自动保证更高生理信噪比；清晰的人脸视频，也可能丢失用于rPPG的细小变化。[23]

**压缩对外观和生理目标不同。**COHFACE使用MPEG-4 Visual强压缩，MAHNOB-HCI也存在重压缩；MMPD从720p处理到320×240。压缩以视觉质量和码率为主要目标，而rPPG关注的是肉眼不易察觉的变化。两者的最优条件不一致。[1]

**肤色与压缩可能交互。**PhysBench质量审计指出，暗色皮肤样本中较弱的生理信号可能受到更明显压缩损害。因此，仅观察压缩后视频中的肤色差异，难以完全区分光学信号差距、编码损失与模型偏差。[42]

**统一缩放只能统一形状。**把不同视频都裁成72×72或200×200，可以统一网络输入，但不能统一原始传感器、曝光、压缩历史和真实皮肤像素数量。模型仍可能学到数据集特有的颜色或噪声统计。

**固定相机与手机有域差。**Vital Videos使用固定Basler相机，方便无损采集和同步；作者也指出，手持手机更贴近未来使用。固定工业相机上的好结果，转为自动调参的手机前置摄像头时，需要单独检验。[10]

### 7.5 标签噪声、同步与参考标准

**参考标签也会出错。**接触式PPG会受手指运动影响，ECG与PPG的波峰时间也不相同。连续压力波、袖带单次读数和设备显示HR，分别有不同时间尺度。模型学习到的目标，不仅由真实生理决定，也由参考设备及标签生成算法决定。

**同步误差直接污染训练。**波形监督要求视频与参考信号对齐。PhysBench的扰动实验表明，加入0—0.2秒随机偏移就会明显降低表现。以1 Hz心搏作示例，0.2秒相当于周期的20%、相位72°，计算为 \(0.2×360°\)；这解释了为何看似很短的偏移也可能重要。[42]

**真实大库仍有参考伪影。**Vital Videos报告约70%—75%的60秒PPG波形干净，约20%有1—3秒运动伪影，约5%有10—15秒大扰动。其比例为近似报告，不应把低端范围强行补成精确100%。这些伪影会把错误监督传给网络。[10]

**伪标签适合周期但有限形态。**rPPG-Toolbox用POS、带通滤波和包络归一化生成伪PPG，可以得到较强周期信号。但紧滤波与归一化会限制形态信息。它能辅助HR训练，却不能自然升级为BP形态或SpO2通道幅度的可靠标签。[12]

**单次BP限制动态学习。**Vital Videos每人只有一次BP，能够建立个体视频与袖带值的配对，却难以检验同一个人BP升降时模型是否跟随。模型也可能主要学习个体间年龄、外观与BP的相关性，而不是个体内的即时压力变化。

### 7.6 验证协议怎样改变“领先模型”

**后处理足以改变误差。**滤波范围、窗口长度、FFT或峰检测、视频级平均方式，都会影响HR结果。rPPG-Toolbox指出，不同研究还采用各自方式从ECG或PPG计算HR标签。因此，表面性能差异可能来自前处理、标签、训练或后处理，而不仅是模型。[12]

**清理规则决定测试难度。**V4V会剔除接触参考明显噪声的视频；rPPG-Toolbox使用UBFC-Phys原作者建议的主体筛选。其各任务分别排除14、30、23人。按56人计算，保留42、26、33段，总计101段，即168−14−30−23；约60.1%的原始任务视频进入该筛选口径。[12]

**筛选后精度还要看覆盖。**清理错误标签可以提高评价可信度，但也可能去掉最难的场景。应同时说明原始视频数、保留数、排除依据和最终成功输出比例。否则，“有效样本上的低误差”可能掩盖频繁失败。

**跨库误差提供直接证据。**运动增强UBFC训练的TS-CAN，在PURE、UBFC-Phys、MMPD上的MAE分别为1.07、5.03、12.59 bpm，MAPE为1.20%、6.36%、13.77%，相关系数为0.97、0.75、0.23。数据域越接近训练条件，结果通常越好；但这种关联仍包含设备、动作和参考差异的共同影响。[12]

### 7.7 对模型训练与使用判断的具体启示

**改进方向应对应失效原因。**仅增加模型深度，无法同时修复人群缺口、标签偏移和设备域差。下面将数据问题与模型后果、评价要求对应起来，作为解释现有研究结果的判断依据。

| 数据问题 | 模型容易学到什么 | 典型泛化后果 | 应优先报告或控制 |
|---|---|---|---|
| 同主体重复片段多 | 身份与典型体征范围 | 新主体误差上升 | 主体级隔离、主体数 |
| 正常值占多数 | 向常见范围回归 | 高BP、低氧误差增大 | 区间样本数、分层偏差 |
| 单设备与固定光照 | 相机和颜色捷径 | 新相机、自然光退化 | 留出设备、跨库测试 |
| 运动与情绪耦合 | 动作强度代理体征 | 自然行为下失效 | 动作分层与真实体征变化 |
| 标签有偏移或伪影 | 错相位、噪声波形 | 波形与峰定位变差 | 同步方法、标签质量 |
| 大量合成、真实主体少 | 合成规律与渲染特征 | 真实域表现受限 | 真实外部测试 |
| 仅保留成功片段 | 只适应容易条件 | 输出覆盖率降低 | 失败率、排除率 |

**数据多样性比视频数量关键。**新增真实主体、异常生理范围和新设备，与复制或合成更多相似片段，带来的信息不同。增强应被视为补充真实覆盖的方法，而不是证明真实人群多样性的证据。

**报告应面向使用场景。**HR重点是活动条件、异常心率和成功输出比例；BP重点是主体隔离、校准、重复参考与高低压区间；SpO2重点是低氧样本数、偏差方向、动态变化及设备光谱条件。只有这些信息齐全，研究人员才知道低误差对应什么能力。

**上调成熟度有明确条件。**当模型在独立主体、留出设备和外部临床数据上，同时保持接近受控实验的误差，并报告较高有效输出覆盖，才有理由扩大用途。对BP，还要证明个体内变化和绝对值都可靠；对SpO2，还要证明异常低氧范围不再明显落后于正常范围。

**数值口径统一说明。**本文保留各研究原有验证协议，原始论文、后续再评测和跨库结果分别解释。Meta-rPPG、Dual-GAN、PulseGAN及RErPPG-Net转载表的bpm，以及DC/AC-STMap表的百分点，属于相应HR或SpO2尺度下的条件性量纲标注。PURE按直接实验描述采用视频30 fps、参考PPG 60 Hz；UBFC按子集区分42与50段，BP4D+保留24—25 fps资料口径。MMSE-HR原幅尺寸、SCAMPS帧率与尺寸由发行文件帧头及时间戳定义；UBFC/MMPD的直接SpO2监督由发布字段和许可决定。约1,800段Vital Videos为近900人乘每人两段的估计，文中其他标明计算的数量、比例均由相邻来源数值推得。

**最终判断。**截至2024年初，普通摄像头面部视频已经较充分证明“可以测得心搏周期”，也证明了BP与SpO2估计的研究可行性。距离可靠应用更近的路线，是围绕目标场景检验信号、标签与外部人群，而不是把一个公开数据集上的最低误差，解释成三类生命体征都已具备临床替代能力。

**补充证据**

结论先行：截至2024-01-31，公开面部视频数据集的主要瓶颈是人群、场景和设备域狭窄，以及标签和划分信息不完整；窗口级高分不能等同于跨受试者、跨摄像头或临床泛化。下述[406][334][430][434]均为截止日后的回溯性汇总，只用于核对既有数据，不改变历史截面。

公开数据集多为健康成年人，年龄通常18–60岁，视频多不超过5分钟（BIDMC最长8分钟），分辨率约640×480至1920×1080像素；男性比例常偏高，肤色常未报告或偏向浅肤色。视频多由普通RGB相机采集，HR参考多为指夹血氧仪或腕戴设备，ECG因成本和设置复杂而较少使用[406][334][430]。因此，训练样本难覆盖疾病状态、年龄、肤色和长期环境；当前证据也未充分报告受试者独立划分，不能据此宣称跨主体泛化。

- **TokyoTech rPPG**：10名、20–29岁受试者，在受控运动和光照下采集；视频数量、设备细节和独立划分在当前证据中未报告，故不宜外推到日常场景[430]。
- **PURE**：10名受试者（8男、2女）、60段面部视频，每段60秒；记录为640×480、60 fps，摄像头字段为eco274，HR参考为CMS50E。六种条件包括静止、说话、慢/快速平移及慢/中速旋转；该性别和规模分布限制跨人群泛化，划分信息仍应标为未报告[406][334]。
- **MAHNOB-HCI**：27人（12男、15女，19–40岁），每人两次约30分钟session；含面部视频、ECG、EEG、呼吸和皮肤电，ECG参考采样率256 Hz，主要是情绪和身体反应实验，不能代表自然场景[430]。
- **UBFC-rPPG**在室内受控照明、变化日光和答题任务下采集；**VIPL-HR**含九种头部运动和光照条件，通常误差更高，适合检验稳定性而非代表日常部署[334]。
- **UBFC-Phys**：56人（46女、10男），3分钟视频，35 fps、1024×1024，EO-23121C RGB摄像机和Empatica E4腕带，条件为静息、讲话和算术；**COHFACE**：40人（12女、28男，35–60岁），Logitech HD C525、20 fps、640×480、约1分钟，参考SA9308/SA9311；两者视频总数在当前证据中未完整报告[434]。
- **MMPD**的2023年数据集论文和名称可确认[406]；回溯资料显示33人、约11小时、Samsung Galaxy S22 Ultra、30 fps，同步HKG-07C血氧仪PPG，覆盖不同肤色、四种光照及静止、转头、说话、走路和运动，但单一手机限制跨设备结论，视频数未报告[430]。**MMSE-HR**被认为是多族群数据集但使用不足，并已有BBP-Net用于SBP/DBP估计[434][316]。

设备域差异同样关键：rPPG可用网络摄像头、手机或工业相机，但受摄像头距离、光谱、传感器、分辨率、压缩、运动、表情、肤色和照明影响；高压缩及空间平均会引入噪声[430]。一个普通摄像头实验中，静止状态RMSE为5.56 bpm（150 lx）和5.58 bpm（300 lx）；头转、混合动作、走近摄像头分别为8.09/9.96/8.60 bpm（150 lx）和7.36/9.88/7.72 bpm（300 lx）[430]。2023年另一项33人、129次测量的研究在约0.8 m、自然光且限制大动作时，将运动伪影处理后的MAE从15.2降至2.8 bpm、RMSE从17.2降至3.41 bpm[170]，说明受控条件下的算法增益不等于真实场景鲁棒性。

对深度学习而言，小样本、短时段、人口偏差和未公开划分会造成过拟合、主体泄漏和过于乐观的测试结果；BP/SpO2部分方法还仅含ICU患者、不含健康者，监督范围与真实应用不匹配[430]。公开rPPG集的规模通常比通用视觉训练集小一至两个数量级，后续研究需采用跨站点、统一协议、充分记录肤色与性别、跨设备和受试者独立测试，并增加长时段数据、合成数据或自监督预训练[434]。

公开集呈现“样本多、人口窄、条件受控”的错位：PURE为10人、60个1分钟序列（另一汇总记59个可用视频），640×480@30 fps、参考PPG 60 Hz，含静止、说话、平移和旋转；UBFC-rPPG为42人、42视频，640×480@30 fps、PPG 30/60 Hz、室内游戏；COHFACE为40人、164视频，480p@20 fps、PPG 256 Hz、聚光灯/自然光；MMSE-HR为40人、102序列，1040×1392@25 fps、连续ABP 1 kHz、情绪诱发。[213][160][269] 视频数不等于人口数；年龄、健康、肤色/族群和日常场景未系统报告，不能以视频量代替多样性。

MMPD的截止后汇总列660视频、4种照明、4种活动和4种肤色；VIPL-HR列2378视频及3类头动/光照/手持手机条件，但页面未完整报告人口、设备、参考信号或划分；UBFC-Phys仅确认是社会压力心理生理多模态数据库，人数、规格、同步、标签和访问状态均未报告。[405][425][432] 后发表或不完整页面仅作核查线索；私有集、隐私和许可限制复现与公平基准。[160][264]

HR/rPPG中，跨集运动量及受控静止/光照与日常场景不一致；肤色改变光吸收，头动、强光和压缩造成模糊噪声，模型可能学到主体或设备伪影。ECG/PPG需与视频同步，错位、丢失或不精确标签造成监督噪声；标注不足使CNN过拟合，合成—真实差异削弱泛化。[160][405] ReViSe所涉学习型方法受训练量、现实条件和压缩影响；截止后综述对Lin等视频放大/深度学习方法的归纳还指出，单一训练集、长BP测量、分辨率及缺少肤色变化/高血压样本会限制外部泛化。[264]

BP的面部视频标签更稀缺；SpO2虽在PURE列有血氧值，但同步、校准和低氧范围未报告，不能外推临床范围。应按受试者而非窗口划分以防数据泄漏，做外部验证，并补充同步参考、人口多样性和动态状态；Huang等（2023）的临床转化语境进一步要求“受控验证→代表性试点→前瞻试验”，公开集单次测试不足。[405][435]

**规模、人口与采集域**

公开数据集的共同瓶颈是人口、设备和真实场景覆盖不足：多数样本来自欧洲、美国或中国，浅肤色、年轻且窄年龄范围占主导；摄像头距离、环境、规格及接触式标签偏差也常未充分处理，监督模型因而依赖训练分布。[436] 摄像头的频段、位深、分辨率、帧率、自动控制和压缩还可能损失细微颜色变化，暗或极浅肤色可能发生像素饱和。[436]

ReViSe混用公开的TokyoTech rPPG、PURE与自建的Video-HR、Video-BP；其BP模型以公开PPG训练、以自建面部视频验证，并强调日常环境比实验室更易受光照和运动影响。[267]

- **TokyoTech rPPG**：9人（8男、1女，20–60岁），每人3段1分钟视频，再切为3段20秒；relax–exercise–relax，2048 Hz指夹接触PPG提供BVP真值。实验室低运动、低光照噪声，主要支持受控HR/HRV，不能单独外推BP或SpO2。[267]
- **PURE**：10人（8男、2女）、60段1分钟视频，含steady、talking、平移和旋转六种设置；30 fps、640×480，60 Hz指夹血氧仪同步提供pulse与SpO2。运动覆盖仍不等于日常场景，人口规模也有限。[267]
- **Video-HR**：自建15人（10–80岁），每人两段20秒手机面部视频，覆盖不同光照和活动姿势，使用Note 9、iPhone 6s/X/11 Pro，脉搏血氧仪作HR真值；HR MAE为2.49 bpm，但无公开下载证据。[267]
- **Video-BP**：自建49人、144样本；Note 9约25秒、30 fps、充足日光，设备手持、置于平面或三脚架，Andesfit设备作BP真值；SBP范围85–168 mmHg、DBP范围50–103 mmHg，SBP/DBP MAE分别为6.7/9.6 mmHg；仅报告90:10划分和10-fold交叉验证，主体独立性未明确。[267]
- **其他数据集**：COHFACE为40人、160段1分钟RGB视频，同步HR和呼吸信号，但同步精度、帧率和具体条件未报告。[426] VIPL-HR为107人、2,378个VIS和752个NIR视频，含头动、光照及设备变化；另有名录记录V1为107人/3,130视频、V2为500人/2,500视频且需申请，规格仍不完整。[236][424] UBFC-rPPG为42人/42视频且需申请；UBFC-Phys为56人/168视频，另一表则记为56人、504分钟、1个PPG部位，显示计数口径和元数据仍不统一。[424][423] MAHNOB-HCI仅确认被公开用于HR研究，MMSE-HR为40人/102视频且需申请，MMPD为33人/660分钟/1个PPG部位且不含全身视频。[234][436][424][423]

BP研究仍多依赖小型、非公开数据集；已有综述建议建立带SBP/DBP标签的公开自拍视频基准，且实时运动引起的BP变化常未被测量。[317]

**对深度学习训练与泛化的直接后果**

视频—标签延迟、帧数有限和对特定数据集的依赖会削弱长期估计及跨域学习。[375] 同一MSPM训练的RPNet在DDPM、PURE、UBFC-rPPG和BP4D+上的MAE分别为12.790±2.949、1.601±0.664、1.786±0.339和6.111±0.307 bpm；加入显示器闪烁红绿光攻击后，部分跨集模型MAE升至约36–37 bpm。[423] 因此，单一受控集上的高分不能替代受试者独立、跨设备、跨光照和真实运动环境的外部验证；后续应建设人口均衡、条件多样且含完整同步与设备元数据的公共基准，并公开SBP/DBP面部视频及代码。[436][317]

局限的因果链是：监督式DNN需同步面部视频–PPG，而采集要求接触传感器和静止姿势，故场景多样性受限；光照、表情、头动、肤色会污染rPPG[149]。PURE（10人/60视频、六种预设头动）与COHFACE（40人/160视频；20fps、640×480；自然光不均、MPEG-4压缩）样本小且受控[149][362]；DEAP（22人/874视频）头戴EEG/EOG/EMG遮挡皮肤，削弱rPPG[149]。UBFC-rPPG（42视频）同步不足造成固定误差；UBFC-Phys（56人/168视频）大幅运动使真值噪声增多[418][427]。MMPD（33人/660手机视频）含4种光照/活动，却仅肤色3–6；肤色4–6、行走和自然光下多数模型MAE>10，PURE/UBFC训练的监督模型泛化受限[429]。VIPL-HR（107人、2378 VIS/752 NIR）规格未报告[428]。这些规模、设备、标签和场景偏差使深度模型易过拟合、域内成绩难外推；BP研究样本17–5992人且多为小型非公开集，难比较，需统一基准[150]。

主要限制是分布而非视频条数：MMSE-HR深色皮肤受试者约占10%，不均衡训练会削弱未见受试者泛化并造成群体偏差[257]；VIPL-HR含107名受试者、2,378段RGB视频，覆盖头动、光照和设备变化，但相关模型仅用10%或50%训练样本时RMSE均>10 bpm[258]。

口径和场景也限制比较：MAHNOB-HCI常用测试子集为27人、527段、61 fps、每段取30 s，原始HCI-Tagging记录却为30人、3,490段；情绪刺激、坐姿和专业照明不等同日常[232][391]。COHFACE为40人、160段、640×480、20 fps，studio训练→natural测试的相关系数仅−0.24、−0.03、0.00[391]。

V4V虽有179人、1,358段和>10°头动，却剔除接触设备噪声读数[398]；BP面部库稀缺：MMSE-HR仅40人/102段，MPM-BP为132名18–24岁私有样本，BP分布不均且SBP 110–130、DBP 60–80 mmHg区间更准[337]。因此需公开同步标签、按受试者划分并做跨设备/场景外测，否则深度模型易学到设备或任务捷径[232][258]。

截至2024年初，公开数据集代表性有限：PURE仅10名受试者、60段视频（30 Hz、640×480；CMS50E同步HR/SpO₂），覆盖静止、说话及四类头动；慢平移中3/10段低光，rPPG误差升高。[244] UBFC-rPPG为42名受试者、每视频约60秒的webcam集，跨集评估受人种及HR范围差异影响。[241] 小样本与受控域使深度模型跨人群/场景泛化受限。[242]

公开集的主要瓶颈是小样本、人口和场景单一：PURE（10人，受控头动/变光照）、UBFC-rPPG（42段视频，静止环境光）、COHFACE（40人、两种光照）、UBFC-Phys（56人、压力任务）、MAHNOB-HCI（27人、情绪视频）和MMSE-HR（40人、自发情绪）难代表日常环境[421]。VIPL-HR（107人、2,378段可见光视频，含肤色/头动/光照）与MMPD（70人、1920×1080、90fps，PPG/HR/SpO2）较丰富，仍缺统一BP、RR、ECG真值[415]。ReViSe手机与Lin等视频放大-CNN方案仍受环境变化、数据稀缺限制；webcam可能低分辨率、低帧率（<5Hz）[44]。标签稀缺、运动/光照/设备域偏移及同步校准误差会使rPPG/深度模型过拟合，削弱跨人群、设备和场景泛化；应采用受试者独立划分、跨设备外部验证和多样标注数据[421]。

截至2024-01-31，公开面部视频rPPG数据集多在实验室采集，光照、运动和距离受控，真实场景及开放数据/代码稀缺；肤色多集中于Fitzpatrick I–III，年龄、族群、化妆和面部毛发覆盖不足，模型易过拟合，跨受试者、设备、光照和场景泛化受损[105]。MAHNOB-HCI仅含轻微运动，表情会增大信号波动，大角度运动可使ROI跟踪失败；PURE、UBFC-rPPG、COHFACE、MMSE-HR在该证据中仅列名，规模、设备、标签和划分未报告[105]。SpO2研究除一项40人研究外多少于15人，部分仅在0.5 m距离测量；ARPOS误差为±2%，仍需临床验证[105]。BP缺少带面部视频和可靠标注的公开数据集，限制训练与外部验证[184]。

智能手机研究仅有HR/SpO2 50条、BP 15条记录训练测试；虽报SpO2 MAE 1.1%、SBP/DBP MAE 5.1/7.5 mmHg，证据仍不足以代表临床跨人群泛化[353][417]。BP4D+筛后仅57人、157段视频、4123个2.56 s片段，按片段70%/15%/15%随机划分；清晰iPPG筛选、运动噪声缺失和BP范围不均衡使留一患者验证性能下降[307]。公开PURE、UBFC、COHFACE分别含表情、运动或光照/肤色条件，现实域会降绩[195]；相机芯片/压缩会削弱BVP，ROI须清晰且>128×128 px[388]；BP袖带标签有固有误差、参考不一，且缺少覆盖广泛BP、年龄和肤色的大型rPPG库[139]。内部验证不足以保证临床适用，须做时间、地域和领域外部验证；同一受试者跨训练测试集会泄漏并高估性能[379][402]。

数据集偏窄会令模型学习个体/设备伪影：手机SpO₂仅6人（1深/5浅肤），<70%样本剔除，厚茧者MAE=8.56%[97]；VitalVideos-Europe-1虽850人，却仅欧洲、受控室内且需许可[407]；3人校准RMSE1.47%（无校准5.02%），环境光增1%[355]；IPPG-BP有115人/2120段，年轻健康、稳定光照[308]。

截至2024年初，公开集普遍规模/人口/场景多样性不足、室内固定采集且有压缩；端到端rPPG易过拟合，域偏移削弱跨集泛化[207]。UBFC-rPPG：42人/42视频/BVP；MMSE-HR：40人/102视频/HR；VIPL-HR：107人/2378视频/HR+BVP+SpO2，虽含多光照/相机仍不足训练大网[207]。UBFC-Phys：56人/168视频[207]，压力标签非瞬时，难迁移日常[437]；Vital Videos(2023)：850人、每人仅1次BP、静止直视、肤色不均[140]；SpO2(2023)：30人/60点，MAE0.62%，受控光照/65cm[119]。

V4V：100名受试者、724段视频（25 fps，BP信号1 kHz），年轻且正常SBP/DBP占多，上采样仍不均衡，易过拟合[123]。COHFACE：40人、160段视频（20 fps），高压缩使rPPG性能显著低于未压缩数据[208]。RGB-SpO₂数据集样本少、肤色和年龄变化小，屏气运动混淆SpO₂下降与运动伪影[45]。

公开集共性瓶颈是小而偏、条件受控且缺乏异常状态：PURE仅10人、60段1分钟序列（8男2女），全为静息和受控头动，30 Hz/640×480、指夹PPG/SpO2同步[285]；COHFACE仅40人160段，30/1/9按人划分，深色肤色和眼镜样本少[133][384]。rPPG受光照、运动、肤色、分辨率/帧率影响，小集易过拟合[224][138][217]；公开数据常缺少<85%低氧和高BP，BP的规模、预处理及校准划分不一，未见受试者泛化受限[138][83]。

2023年PMDE为网络摄像头同步面部视频、ECG（500 Hz）和SpO2（125 Hz），同步误差约40 ms，但其动机正是缺少训练数据，且设备域不能代表手机[352]。rPPG信号幅度小，头动、光照、距离、分辨率和传感器差异会造成伪影；受控公开集通常缺少年龄、肤色和文化多样性，深度模型跨受试者/场景泛化受限[183]。2023年SpO2自建集仅50人、20—50岁、屏气产生85—100%标签，40/10跨人测试；4秒血氧读数又插值为1 Hz，CNN-Filter仍报MAE 1.17、RMSE 1.40，难外推日常场景[98]。2018年MAHNOB-HCI虽有30人、600视频和256-Hz ECG，却把头动、闪烁光、表情、肤色和遮挡置于受控挑战子集；PURE、UBFC-rPPG、COHFACE也主要是基准条件，公开卡片未报告完整划分，不能代替外部验证[165][183]。

公开集普遍“小而受控”：PURE仅10人/60段、COHFACE40人/160段、MAHNOB-HCI27人/527段、MMPD33人/11小时[359][203][412][413]。光照、运动、遮挡、设备差异和视频噪声削弱训练，跨人/设备/场景泛化受限[76][203]；BP面部标签未核实，SpO2低氧范围未报告，需独立同步验证[64][359]。

公开集小且受控，标签划分不一：PURE10人/60视频；UBFC-rPPG50视频、人数NR[279]；COHFACE40/160、UBFC-Phys56/56、MMSE-HR40/102、MMPD33/660[416]。VIPL-HR107人、2378VIS+752NIR、9种头动/光照，五折按人测但须机构申请[220]。暗光/运动/压缩/肤色致域偏移，最深肤色13.58、其余2.14–4.09BPM[227]；BP自建111/14/14例，SBP/DBPMAE5.98±5.22/4.30±3.39mmHg、无外部验证[302]；SpO2MAE1.274%、RMSE1.71%，受RGB/设备/范围影响[345]；深度模型易过拟合、跨域泛化受限。

规模/肤色/光照/划分→泛化受限[53][403]。

MMPD完整多域集：33人、11h、1152K帧、320×240；全域HR/PPG难准确[77]。篇幅不足，需拆分或扩容。

数据集局限很具体：MMPD仅33人、1152K帧，完整集370G且须申请；全域现有方法仍不能准确预测PPG/HR[404]。PURE仅10人、60段1分钟、30Hz，且全为静息[284]；VIPL-HR虽107人/2378段，跨库MMSE-HR仍达10.10 bpm RMSE[106]。BP受头动、光照和数据稀缺制约；SpO2多为10名健康人、受控低氧/光照，跨人群、场景泛化证据不足[305][78][94]。

PURE/UBFC-rPPG/COHFACE分别仅10/42/40人；公开集多小且同质，多为受控室内，肤色/年龄/室外光照覆盖不足，头动使SpO2真实验证受限[385][155][394]；COHFACE重压缩致噪声[155]。样本及同步标签不足使深度模型训练验证受限、跨人群/设备/场景泛化弱[193]；MMPD含33人、11小时手机记录和八类标签，但规格/公开状态未明[433]。

PURE仅10人、60视频[156]；TokyoTech仅9人[156]；BP面部库稀缺[151]；标签噪声和划分泄漏限制深度模型泛化[141]

截至2024年初，数据集仍小且受控：TokyoTech 9人、每人3段1分钟；PURE仅10人、60段（30 fps、640×480；六种头动，脉搏/SpO₂标签60 Hz），UBFC-rPPG仅42人（30 fps、640×480、PPG）[420]。Video-HR（15人）和Video-BP（49人、144样本）为自建，难复核、难外推[158]。运动、遮挡、光照会淹没微弱信号；临床数据又受隐私、单中心和病理范围不足限制，深度模型跨人群/设备/场景泛化受限[396][159]。

公开集的缺陷是样本、域与标签不足。PURE(10人/60段，30fps、640×480、PPG/SpO₂、六种头动)与UBFC-rPPG(42段、室内坐姿)难证跨人/设备/光照泛化[196][186]；COHFACE元数据冲突(40人/160段/20Hz压缩vs100人/>5000段/1080p)，MAHNOB-HCI27人/527情绪视频且重压缩，MMSE-HR40人/102段、强头动[186][431][196]。VIPL-HR107人、2378RGB+752NIR、四设备九场景，却肤色III–IV/低氧不足；异常SpO₂ MAE/RMSE0.978/1.288%→3.077/3.563%[373]。MMPD33人/660段，70/10/20%划分可泄漏[408]。TokyoTech公开(HR-MAE1.73bpm)、元数据/访问未全；Video-HR/BP自建、字段未报，MAE2.49bpm；BP用指尖标签训练，SBP/DBP MAE6.7/9.6mmHg[262][292]。临床：HR充分、SpO₂新兴、BP实验性[409]。标签/隐私与域偏移使模型学设备捷径；域内高分≠外域，应按人、跨设备测[186]。

PURE（2014）仅10人、60段视频；肤色、真实运动和光照单一，限制深度模型跨域泛化。[216]MMPD（2023）33人、660段手机视频；肤色4–6多数MAE>10，行走/自然光亦差。[216]

PURE小而受控、ROI失败[175]；UBFC-rPPG肤色2–3，跨域MMPD的MAE12.59bpm[438]；UBFC-Phys任务运动增噪[399]；COHFACE压缩[225]；MAHNOB-HCI情绪噪声、VIPL-HR设备光照、MMSE-HR范围不足过拟合[169]；Video-HR/BP自建、规模/公开性未报，BP训练用指尖信号[280]。共享不足，易过拟合域偏移，须外部验证[142]。

截至2024-01-31：UBFC-rPPG42人/50视频[125][127]；UBFC-Phys56人/168视频[125]；MMPD33人/1152K帧、需许可[286]；域偏移限制DL泛化（容量冲突）

HR/BP/SpO₂公开集有小样本、压缩/暗光/运动及窄SpO₂范围；标签噪声与样本切分致过拟合，跨人群/设备泛化未证；需独立划分外部验证。[246][249][254][368]

公开数据的输入域并不统一：VIPL-HR为25 FPS、960×720，UBFC-rPPG为30 fps、640×480[415][419]；编码、光照、运动和摄像头等级会改变弱rPPG，激进压缩甚至可能完全破坏信号特征[111]。模型若在受控设备和光照上训练，换设备或未知采集设置时会把域伪影当作生理模式；跨数据集上RPNet对PURE和UBFC-rPPG较好、对BP4D+较弱且对DDPM困难，排除攻击片段后才改善[423]，而采集距离的独立效应仍未量化。

按视频或窗口随机划分时，若同一受试者的相邻片段同时进入训练和测试，脸型、肤色、背景及设备噪声会泄漏，使性能高估而不能代表跨受试者泛化；VIPL-HR虽有107名受试者、2,378段30s视频和五折协议[106]，但五折本身不等于主体独立。现有材料没有给出泄漏造成的高估幅度；跨数据集上RPNet对PURE和UBFC-rPPG较好、对DDPM困难[423]，故应报告主体独立和外部测试。

视频数不能替代独立主体：VIPL-HR有107 subjects、2,378 videos、30s片段，而MMSE-HR有40 subjects、102 videos、30s片段，且HR分布不平衡[106]；MMSE-HR深色皮肤受试者约10%，训练损失和校准会偏向多数群体，未见主体的误差与偏差随之上升[257]。BP数据常小且不公开，RGB-SpO2研究又受受试者很少、肤色和年龄变化不足及屏气伴随头动的混杂限制[317][45]，所以增加窗口数量或过采样不能替代人口与生理范围覆盖。

不同体征的瓶颈路径不同：HR在受控实验室、轻微运动条件下容易学到场景而非运动和光照不变性，表情会造成信号高变，大角度运动还会使ROI跟踪失败[105]；BP因缺少覆盖广泛BP范围、医学史、人口学、年龄和肤色的大型库而缺少训练与校准分布[139]。SpO2现有资料仅明确到“at least 10 people”，低氧范围和人口覆盖未量化[346]；rPPG又要求ECG/PPG金标准与视频同步[405]，因此这些模型都可能域内高分而外部泛化弱。

基于视觉的非接触式生命体征监测技术的公开数据边界首先是覆盖不足：BP缺少覆盖广泛血压范围、医学史、人口学、年龄和肤色的大型数据库[139]，RGB-SpO2数据又常有小样本、肤色和年龄不足及屏气时头动与PPG振幅混淆[45]；有监督rPPG还依赖与面部视频同步的ECG/PPG金标准[405]。这些缺口使深度网络把人群、设备和实验条件当作捷径，跨受试者和设备性能不稳；跨数据集上RPNet去除攻击片段后才改善，且对PURE和UBFC-rPPG较好、对BP4D+较弱、对DDPM困难[423]，所以应采用主体独立、多设备、多环境和同步参考的公开基准。

rejected；reason=number_unsupported；allowed_numbers=960×720、25 Hz、1920×1080、30 Hz、640×480、30 fps；allowed_cites=[111][118][183][138]；allowed_entities=普通摄像头、远程光电容积描记术（rPPG）。

面部视频中的运动、光照、遮挡和ROI选择会降低局部SNR；头发、头巾或斜视角可遮住单一ROI，手大幅遮脸或离开画面时估计通常失败[171][165]。中性演讲数据不覆盖情绪激发或自然运动[54]，公开面部视频还常见低清晰度、抖动或拖影、多脸、手或物体进入画面及文字噪声[87]；有监督rPPG还要求ECG/PPG金标准与视频同步，金标准丢失或错位会使监督标签错配[405]，所以训练监督和真实场景域都不完整，跨场景泛化风险高。

HR公开数据的独立主体与人口覆盖需谨慎解读：VIPL-HR明确为107 subjects、960×720、25 FPS[415]，而MMSE-HR深色皮肤受试者约10%[257]；这种人口不平衡会使损失和校准偏向多数群体。MAHNOB-HCI来自受控实验室且只有轻微运动，表情造成信号高变、大角度运动会使ROI跟踪失败[105]；有监督HR还要求ECG/PPG与面部视频同步[405]，而UBFC-Phys未报告规模、人口、参考信号或数据划分[432]，所以视频或窗口结果不能替代主体独立外部测试，跨数据集泛化仍可能不对称[423]。

BP公开数据的生理范围与人口覆盖不足：已有记录的范围为SBP 108–180 mmHg、DBP 60–108 mmHg[303]，而rPPG领域缺少覆盖广泛BP范围、病史、人口学、年龄和肤色的大型库[139]，使SBP/DBP回归和校准易局限于采集人群。参考标签依赖上臂袖带的示波或听诊测量，标准协议要求静坐5分钟后测量3次、间隔1分钟[91]；给定资料没有统一样本量或主体独立划分，故袖带内高准确率不能直接推出跨受试者泛化。

SpO2参考与RGB信号并非同一光学域：指夹脉搏血氧仪用红光和红外光吸收作参考[343]，而面部RGB方法可用R/B通道并考虑光强与背景亮度[119]，所以波长响应、照明和个体反射差异会使校准跨设备漂移。现有资料对样本只明确到“at least 10 people”[346]，未给出低氧范围、年龄或肤色分布以及主体独立划分；即使以3秒RGB视频输入CNN[97]，也不能证明低氧条件下的外部泛化，需建立同步脉搏血氧仪标签的多人口、多设备基准。

rPPG要在0.4 Hz to 4 Hz的生理频段内从皮肤反射光的细微变化恢复BVP[410][414]；运动、光照、ROI和压缩会把环境变化混入时空特征，网络可能学习伪影而非脉搏，跨域稳定性因此下降[411][130][401]。有监督训练依赖ECG/PPG金标准与面部视频同步，金标准丢失或错位会形成时序标签噪声；弱监督或无监督可减少标注需求但不能自动消除设备和场景域偏移[405]，所以同步、信号质量和外部域测试必须成为评估条件。

ReViSe使用公开的TokyoTech rPPG、PURE和PPG-BP，同时使用自建Video-HR与Video-BP[158]；PURE只有10名受试者、60段1分钟视频，视频为30 fps、640×480且参考PPG为60 Hz[268][371]，BP资料还只覆盖110–130 mmHg与60–80 mmHg[337]，难以支撑覆盖日常人群和设备的深度模型。恒定室内或静止数据遇到室外光照、轻微震颤或相机抖动会降性能，跨数据集测试表现显著恶化[310][242]；SpO2研究还受小规模标注、隐私导致不公开以及头动或光照未充分考虑限制[422]，所以ReViSe面向日常环境的目标仍需更大、更多样且主体独立的外部基准。

## 附录：其他证据

**补充证据**

**研究边界、定义与统一证据口径**

本报告的核心范围是：使用普通可见光/RGB智能手机、网络摄像头或消费级相机拍摄的面部视频，通过非接触方式估计HR、BP和SpO2；ECG、接触式PPG、指夹式脉搏血氧仪和袖带仅作为参考或标签，热成像、雷达、NIR及指尖视频另行标注，不作为普通面部视频核心证据。技术状态按2024年1月31日截止，关键实证论文按2020—2023年筛选。[43][46]

HR（heart rate）是每分钟心跳次数，单位为bpm；BP必须拆分为收缩压SBP和舒张压DBP，单位为mmHg；SpO2表示血红蛋白的氧饱和程度，通常以%或百分点表示，参考可为脉搏血氧仪，临床特殊场景也可能使用动脉血气。[50][51]

rPPG（remote photoplethysmography）从面部皮肤反射光的逐帧RGB变化中恢复由心脏活动调制的血容量脉搏信号。典型管线依次为视频帧提取、人脸/ROI检测与跟踪、颜色信号处理、生命体征估计；帧率、分辨率、低照度和头部运动都会影响信号质量。[43]本报告将方法分为颜色通道与传统信号法（GREEN、ICA、CHROM、POS、PBV、LGI、OMIT）、时频分析、视频放大、端到端深度模型（如DeepPhys、PhysNet、TS-CAN、Transformer）及混合方法；BP另记录基于脉搏波形、PTT/PWV或面部区域时间差的映射方法，但不把方法类别本身等同于性能。

普通设备的部署条件必须与误差一起记录。一个2022年多设备评估使用Logitech网络摄像头、Samsung M32、OnePlus 9、iPhone 11和iPad 9，覆盖Android、iOS、Windows和macOS；实验中摄像头距面部60 cm、照度至少250 lux，每次扫描60 s，受试者需保持静止、直视摄像头并移除面部遮挡。[49]网络摄像头资料中“低帧率低于5 Hz、低分辨率增加视频分析难度”的证据来自非生命体征运动检测研究，不能当作HR、BP或SpO2性能结果。[44]

作为统一口径示例，2022年11月18日的摄像头—医疗设备比较研究报告如下；这些结果仅用于说明指标、分母和条件，不能跨协议排名。[49]

|目标|样本量|与医疗设备参考值比较的结果|
|---|---:|---|
|HR|240|ME −1.19 bpm；MAE 3.09 bpm；RMSE 5.72 bpm；RMSPE 7.43%|
|SBP|463|ME −5.27 mmHg；MAE 18.15 mmHg；RMSE 22.77 mmHg；RMSPE 17.59%|
|DBP|463|ME −3.95 mmHg；MAE 10.49 mmHg；RMSE 13.71 mmHg；RMSPE 17.38%|
|SpO2|235|ME 0.3%；MAE 1.21 个百分点；RMSE 1.77 个百分点；RMSPE 1.85%|

同一研究认为HR在低值和正常范围内可维持约±3单位标准，但极端HR及运动伪影会增加误差；BP在SBP高于150 mmHg或DBP高于90 mmHg时更困难；SpO2结果主要覆盖90%—100%，低于90%的样本有限。[43][49]

论文和数据集的公开性也必须分开记录。ReViSe（2022-06-13）以智能手机面部视频和rPPG为输入，在公开TokyoTech rPPG与PURE上报告HR MAE分别为1.73和3.95 bpm、HRV MAE分别为18.55和25.03 ms，并在PURE上报告SpO2 MAE 1.64%；其自建Video-HR的HR MAE为2.49 bpm，Video-BP的SBP/DBP MAE分别为6.7和9.6 mmHg，BP模型训练还使用了指尖传感器数据。[46]这些数字需保留数据集角色，不能把自建Video-HR或Video-BP列为公开面部视频数据集。

SpO2是特殊的RGB光学问题。van Gastel和Verkruysse的2022年研究使用额头ROI跟踪、ratio-of-ratios和APBV，并以指尖、耳部脉搏血氧仪作参考；其RGB摄像头配合滤光片、偏振器和外部光源，视频为15 Hz、3328×2464像素、约80 cm距离，因此应标作“RGB摄像头加辅助光学组件”，而非裸手机或裸网络摄像头。[45]RGB方案会受环境光谱、深色皮肤镜面反射、红绿光对比度不足、波长穿透深度差异、设备光谱响应和较低信噪比影响；其摄像头PPG信号强度可比接触式探头低约10—100倍。[45]

较早的普通手机示例使用Samsung SGH-i437前置摄像头采集10名受试者、480×640像素、14.99 fps、每段1 min视频，并以200 Hz指尖PPG作参考；ICA和GrabCut用于从面部ROI分离信号，30 s窗口、1 s步长估计HR，静止与轻微运动视频误差分别为3.4±0.6和2.0±1.6 bpm，但该研究不属于2020—2023关键论文窗口。[52]2020年的Diverse R-PPG预印本则报告54名不同肤色受试者、432段视频（约864 min）和真实场景物理驱动算法；所示摘要未给出明确误差数值，故只能作为候选线索而非满足性能字段的核心论文。[53]临床汇总表还显示：Barde（2023）在60名房颤患者、Samsung S10/S3、30 fps和不同照度下报告HR 0.05±1.4 bpm；Huang（2021）在257名新生儿、640×480像素、30 fps下报告−0.21±5.32，但表中未标单位；Jorge（2022）使用850 nm NIR、100 fps并报告HR MAE 2.5，因模态不是普通RGB而仅作对照。[55]

商业或应用页面的数字不替代原始论文：FaceHeart页面声称2023年FDA 510(k)许可的HR误差为±3 bpm、BP≤10 mmHg、Oxygen Saturation≤3.5%，但未给出SBP/DBP拆分、参考设备、分母或SpO2误差定义。[48]LabVanced页面描述网络摄像头rPPG输出BPM、时间戳和置信区间，并预计与实际HR相差1%—3%，但同时明确独立验证尚未完成。[47]

rPPG为面部ROI的RGB时间波动→HR/SpO₂；HR参照ECG/指端PPG（bpm，60/120 s），SpO₂参照脉搏血氧仪（%，120 s）；静息同步30/60/120 s，ICC含95%CI，按年龄、性别、六种皮肤光型调整。[56][67] 2020 Siamese-rPPG用双ROI、3D-CNN和negative-Pearson loss端到端恢复rPPG，使用COHFACE/UBFC/PURE；片段无bpm结果，仅作方法线索。[57] VIPL-HR用额头/脸颊ROI、RGB/YUV-MSTmap、解耦双头网络回归rPPG/HR；107人、2378段视频（25–30 fps）、BVP标签；五折受试者独立：MAE 5.02、RMSE 7.97、Std 7.92 bpm，r=.79。[68] 2022 LSTM报告3.26 bpm，G/ICA/POS为6.49/3.02/2.61 bpm，红外仍可用；数据集和分母未报。[63] 30-Hz手机绿色通道SPPG为接触式指尖输入，非面部而排除；与ECG差0.011 bpm、相关>0.99。[64] 商业页主张因无参照/分母不横比；2025年后资料超截止日排除。[58][59][61][62][66]

证据边界结论：核心只纳入普通RGB智能手机/网络摄像头的面部视频；ECG、接触式PPG/ABP及脉搏血氧仪只作参考或标签，接触式波形结果不算面部视频性能。[83] 截止日按2024-01-31。2025年iSelfie研究（579人、30秒智能手机眼周视频、Philips SureSigns VS2/Masimo W1参考、每人15点校准）报告HR MAE 4.42 bpm、SBP 8.94 mmHg、DBP 7.50 mmHg、SpO2 1.16%；其为截止期外线索，不纳入。[69]

2024年Lifelight研究同样使用40–50 cm消费级摄像头和面部rPPG（0.125–4 Hz滤波），报告脉率RMSE 1.9 bpm、SBP平均误差/SD为1.2/15.9 mmHg、DBP为−3.2/13.1 mmHg；虽用独立临床实验室验证，仍不改变历史截面。[74]

典型管线是人脸检测/跟踪→ROI→GREEN、ICA、CHROM/POS或深度模型→频域/回归。V4V中POS处理5个ROI、10秒窗，训练/验证平均MAE为8.324 BPM；数据集有1358段视频和25 Hz帧级HR标签。[72] Hybrid D1DCnet以1D卷积、注意力LSTM和MLP处理前额iPPG，814人、8秒窗，SBP MAE为8.36±6.22、DBP为5.69±3.97 mmHg。[70] HR、SBP/DBP、SpO2分别用bpm、mmHg、%或百分点记录。

2019年Project_ICA仅作背景：自建28人、112段、30 fps、640×480视频并同步指夹血氧仪；静止浅肤色MAD/RMSE为1.31/1.87 bpm，运动恢复深肤色为17.09/24.20 bpm，条件不能省略。[75] Deep-HR在MAHNOB的RMSE_D为3.41、r为92%，但未给bpm单位；MMPD 2023静止人工光下POS的MAE/RMSE/MAPE为7.69/11.95/11.45，TS-CAN（UBFC）为1.46/3.13/2.04，均不作跨研究排名。[76][77]

综述只作导航：rPPG可从环境光面部视频提取脉搏，涵盖无监督/监督模型和基准集，性能须回到原始论文。[79] COHFACE提供接触PPG/BPM标签但未报告误差；MAHNOB-HCI为24人、20视频、6机60 fps，含256 Hz ECG等多模态信号、20部情绪电影及前后30秒条件。[80][71] PulseDB虽有5361人、5245454个10秒ECG/PPG/ABP片段，却不是面部视频，排除。[81][83]

普通RGB面部视频的可执行流程是：逐帧检测人脸地标并建立ROI，提取ROI的RGB/BGR时间序列，经PCA/ICA等盲源分离、色度法或POS恢复rPPG，再估计HR、SBP/DBP或SpO2；低照度、头动、帧率和分辨率会造成信号失真。[86] 受控示例同时采用Logitech webcam及Samsung M32、One Plus 9、iPhone 11和iPad 9，距脸60 cm、正面照度至少250 lux、扫描60 s并保持静止直视；这不是日常场景默认性能。[86] 允许使用的2022年HR综述把ROI、Video Magnification、EVM-CNN和VGG-16列为方法线索，并识别11个数据集、20篇相关论文，但仅作导航，性能必须回到原始论文核验。[84] 2020年Meta-rPPG在MAHNOB-HCI和UBFC-rPPG上采用测试时无标签自适应，并指出肤色、光照和面部结构会造成域偏移；当前片段未给出可核实误差，故不作性能证据。[85] 本报告以普通可见光面部视频为核心，接触式ECG/PPG、袖带和脉搏血氧仪仅作参考；HR为bpm，SBP/DBP为mmHg，SpO2为%或百分点，截止日为2024-01-31。

血压（BP）必须拆为收缩压（SBP，心室收缩时动脉最高压）与舒张压（DBP，两次搏动间最低压），均用mmHg；MAP另列，不能以总BP代替二者。[88] 普通摄像头路线是“面部视频→BVP/rPPG→波形或时空特征→SBP、DBP”；运动、环境光、视角和距离会污染弱信号，额头/面颊ROI、改进YUV及时空切片可减噪。[65][90] PTT不是压力单位，须用多次压力—PTT配对进行个体校准；因此指尖PPG/ABP的modified U-net结果（2021年、100人）SBP MAE为3.68±4.42、DBP MAE为1.97±2.92 mmHg，只能作接触式基线。[88] 视觉BP结果必须注明参考袖带、休息及重复测量条件；Omron HEM-907XL协议为静息5分钟、间隔1分钟测3次。[91] 2026年PPG/ECG证据不纳入2024-01-31截面。[89]

BP须拆为SBP/DBP，单位mmHg；面部视频可经ROI、rPPG及CNN/Transformer估计[73]。2023年30fps自建rPPG集改进后SBP/DBP MAE为8.78/6.16mmHg，TVGH夜间为11.12/7.59mmHg[93]。SpO2：2023年手机面部视频10名健康者、92%–99%，MAE=1.26±0.68%、Arms=1.34%[94]；医疗PPG结果不替代面部视频证据[82]。

口径：BP拆为SBP/DBP；PulseDB每个10 s片段以ABP逐搏均值为参考（SBP 121:42±22:10、DBP 61:87±13:01 mmHg）；AAMI：ME/SDE≤5/8 mmHg；校准自由测试才检验未见受试者泛化。[95]普通摄像头面部管线为RGB皮肤色→BVP→FFT/ICA/PCA，手机为多ROI滤波BVP。[96][153]SpO2为SaO2百分比估计，参考脉搏血氧仪；面部RGB可用ROI-rPPG、DC/AC或RoR与CNN。[60][98]PURE公开基准：10人、60视频、30Hz、640×480、CMS50E同步HR/SpO2，MAE/RMSE=1.332/1.637百分点。[100]2023面部自采集50人/30fps：Filter/EndToEnd MAE=1.17/1.18%、RMSE均1.40%。[98]两人LOSO暖光RMSE=1.93%、PCC=.97。[99]手指手机非面部：6人LOOCV CNN MAE/RMSE=5.00/5.55%。[97]

模态边界与证据口径：可见光数字摄像机覆盖380–750 nm；核心仅纳入普通RGB手机/网络摄像头面部视频，手部/躯干视频及指尖接触传感器只作排除或对照。[108][172] SpO2以百分比读数；健康个体通常为95–100%，但脉搏血氧仪本身可能偏差，90%读数可能对应真实动脉饱和度86–94%，故必须注明参考设备和误差单位。[103]

2021年YCgCr-RGB研究以面部ROI、KCF跟踪、Cg/Cr与Beer–Lambert法估计SpO2；10名健康韩国受试者、30 fps、CMS-50E、屏气低氧和500 lux条件下MAE为0.537、RMSE为0.692，原文未明确是%还是百分点，不能自行换算。[78] 2022年受控RGB面部研究使用300×300像素额头ROI、640×480/15 Hz；13名志愿者的SpO2平均偏差为0.5%、RMSE为4.3%、相关系数为0.76。[121] 2023年RGB+rPPG研究用R/B、R/G RoR，在暖色温/正常亮度、两名受试者LOSO下RMSE为1.93%、PCC为0.97；四种照明和最低81%低氧是前提。[101] 同年《A Study on Impacts of Ambient Lights and Skin Tone》含31名参与者、三项活动，采用人脸ROI、R/B的AC/DC和线性回归，需200–500 lux中等照明，但只报告RMSE名称、未给数值。[102] 2023年视频放大+YOLOv5 ROI+3D-CNN研究无需逐人校准，含18名健康受试者，仅报告98%一致性、未给MAE/RMSE，故仅作方法线索。[104] 2025年后续手机vPPG证据超出截至2024-01-31的时间截面，不纳入论文清单。[173]

截至2024-01-31，范围为普通RGB手机/网络摄像头面部视频；接触式信号仅作参考，指尖视频排除。rPPG为ROI颜色→PCA/ICA/CHROM/POS→FFT/滤波。[124] HR=bpm，BP分SBP/DBP（mmHg），SpO2=%/百分点并注明参考设备；面颊ROI可用CNN-LSTM分别回归。[123] 截至2020-09综述的26项研究中，HR22（92%）、BP3、SpO2 0；HR汇总r=.962、均值差=.36（单位未注明）、I²=93%。[131] V4V test set 1的SBP MAE为12.408/14.491/14.174、DBP为12.652/11.371/16.071（MAE单位未报），准确率分别89.1/87.3/87.8%和83.4/85.2/79.5%。[123] 2020—2023论文须有原文数值。

面部视频的共同观测对象是普通 RGB 摄像头的面部 ROI：逐帧颜色变化恢复 BVP，再估计 HR（bpm）；ROI 影响信号质量和计算量，脸颊与前额通常较优[164]。2022-02-18 的《Contactless Vital Signs Monitoring From Videos Recorded With Digital Cameras: An Overview》将可见光（380–750 nm）摄像头估计 HR、BP、SpO2 列为导航范围；其数字不能替代原始论文性能[112][113]。

主流 rPPG 包括 GREEN、ICA、CHROM、SSR、POS、PBV、LGI：CHROM 以颜色差分归一化抑制反射噪声，POS 投影到肤色正交平面，PBV 区分脉搏颜色变化与运动噪声[164]。典型链条是人脸/ROI 跟踪→RGB 空间池化→ICA/PCA 盲源分离→FFT 与带通滤波（示例 0.65–3.5 Hz）→峰频×60 换算 BPM[105]。并行路线包括视频放大及端到端或混合深度模型（2D/3D CNN、CNN-RNN、GAN）[105][155]。2021 年 ROI 比较中，UBFC 上 POS/CHROM 的 MAE 分别为 1.85/1.5、PCC 为 0.80/0.87；LGI-PPGI 上 MAE 为 3.61/2.93、PCC 为 0.34/0.59，MAE 单位未报告[164]。

普通手机/网络摄像头的弱 rPPG 受光照、运动、肤色、压缩和帧率影响；该实验仅覆盖 Fitzpatrick I–II 型[164][155]。一个网络摄像头 SpO2 示例以额头 ROI 和红蓝 rPPG 对照认证血氧仪，MAE 为 0.62%，最佳距离为 60 cm、光照为 550 lux，不能外推手机或自然场景[145]。常见帧率为 15/30/60 fps，实际设备算力会改变信号质量[105]；2020 年《Real-time vital signs measurement system using facial image on Mobile》、2021 年《Real-time Vital Signs Measurement System using Facial Image Data》和《Non-Contact Heart Rate Monitoring from Face Video Utilizing Color Intensity》在当前证据中只有书目信息或方法线索，未给出性能、数据集或协议，故不作为关键实证[164]。

截至2023年，普通手机/网络摄像头面部ROI经RGB均值、CHROM/ICA/POS、滤波与FFT恢复rPPG/BVP并估计HR；CNN/注意力以200×200、5×5时空图抗运动[106][109]。消费相机常见30 fps；光照、运动、肤色和压缩影响质量，BP需校准、SpO2受波长限制[139][142]。


普通摄像头面部去噪HR-MAE2.8bpm2023[170]。

普通摄像头面部视频可非接触经ROI、RGB/rPPG、滤波及FFT估计HR；手机30fps/1920×1080[165]，网络摄像头30fps/640×480、25人/100段[117]。

范围：普通RGB手机/网络摄像头面部视频；接触式PPG、ECG和血氧仪仅作参考。流程为人脸检测/ROI→RGB→滤波/FFT→rPPG/BVP→HR、BP或SpO2；HR常取脸颊，BP取前额/脸颊，SpO2取前额；分辨率、帧率、距离和照度会影响质量。[120] ReViSe（2022）手机30fps、1280×720、20s：HR MAE 1.48/4.20/2.49 bpm（TokyoTech/PURE/Video-HR），SpO2 1.60%，SBP/DBP 6.7/9.6 mmHg。[156] 2023网络摄像头R/B额头法：30人、60点，SpO2 MAE 0.62%。[119]

普通摄像头结果受采集条件支配：低成本 webcam 的 rPPG 受光照、头动限制；BH-rPPG 中等照度下 CHROM 的 HR-MAE 为 1.04 bpm，较 PhysNet 低 80%[127]；VIPL-HR 暗光下 RGB RMSE 由明亮条件的 8.14 升至 17.7 bpm，NIR 同环境为 12 bpm[166]。2022 年 Galaxy S10 前摄为 30 fps，Haar/SSD/YOLO 人脸检测率为 28/22/17 fps；室内数据为 25 人、375 段 60 s、640×480 视频[143]。

面部视频管线通常是“人脸/68点→ROI→RGB变换或时空图→滤波/FFT→估计”：MTCNN+ERT、GREEN、ICA、CHROM、PBV、POS、LGI及深度CNN均属此路线[125]；MediaPipe实验覆盖额头、双颊及组合ROI，六阶带通为0.65–4 Hz[157]；BPE-Net以四ROI平均像素、残差网络+BiLSTM、区间分类器/计算器输出BP[151]。

2023年BP数据区分公开MMSE-HR（40人、102视频、25 fps）和私有MPM-BP（132名18–24岁，Huawei Mate30，30 fps、1920×1080，Biopac时间戳同步）[151]；MMPD（2023）用手机采集33人、660段1 min视频，30 fps、原始1280×720/发布版320×240，配PPG、4种光照和4种活动[174]。Vital Videos固定Basler；手机更贴近日常但更难与PPG同步[140]。因此帧率、分辨率、距离、照度、运动、ROI、压缩及参考信号均不可省略，受控误差不能直接外推到日常场景。

普通RGB面部视频经ROI、rPPG和频谱分析估计生命体征；运动、光照、分辨率/距离影响信号。[144][130][161]

普通手机/网络摄像头面部视频：ROI→rPPG（Green/ICA/PCA/CHROM/POS/CNN）→HR；BP由波形/PTT/PWV推SBP/DBP，SpO2靠双波长比值校准。[134][138]；VIPL-HR（2020）107人、3130视频（VIS2378/NIR752），webcam/RealSense/手机，25–30fps、960×720/1920×1080，HR/SpO2/BVP同步、9种头动/变光条件。[159][167]约1m、30fps、640×480；运动、光照、肤色、遮挡降低质量；无数值论文仅作导航。[134][171]

普通RGB面部视频经人脸/ROI跟踪、皮肤分割和RGB/ICA/CHROM/POS提取rPPG，再由频域峰值估计HR；2015年研究用30fps、1280×1024、0.5m、500lux。[146]运动、低照度、肤色和压缩会降SNR；PURE（2021）10人、59段、30fps、640×480，参考脉搏血氧仪，说话RMSE13.46–15.10bpm。[175]

普通网络摄像头面部视频640×480、30fps；光照/运动/遮挡扰动ROI，滤波后估计HR。[126][160]

RGB面部视频经rPPG提取脉搏，估计HR；非接触。[115]

普通RGB面部视频的典型管线是人脸检测/ROI跟踪→皮肤RGB均值→滤波、ICA/CHROM/POS恢复rPPG/BVP→FFT峰求HR；端到端CNN、RNN或3D-CNN学习时空特征。COHFACE比较中，DeepPhys平均HR MAE约5 bpm，手工方法约15 bpm、POS约24 bpm。[133] ReViSe以478个标志点分割额头、脸颊/鼻部ROI，去噪、ICA和Welch-PSD选BVP；TokyoTech HR MAE报告1.73 bpm（同源另报1.48），Video-BP的SBP/DBP MAE为6.7/9.6 mmHg。[158] BP还可学习形态/时频特征或PTT/PAT/PWV；严格受试者划分的PPG-ResNet SBP/DBP MAE为16.4/8.5 mmHg。[141] SpO2可把RGB面部信号转YCgCr，按Cg/Cr与Beer–Lambert关系线性校准；报告MAE/RMSE为0.537/0.692（原片段未明示单位）。[129] Lin等用面部/颈部双ROI放大、PCA和小型CNN估计HR/BP，SBP/DBP MAPE为3.73%/4.95%。[162]

**证据边界与候选登记**

本报告将“截至2024年初”操作化为2024-01-31，关键论文窗口为2020-01-01—2023-12-31。核心输入仅是普通可见光/RGB消费级相机（智能手机、webcam）的面部视频；ECG、接触式PPG、脉搏血氧仪和袖带只作参考或标签，手指贴镜头、NIR/红外及非面部视频另行标注，不充当核心证据。HR、SBP/DBP、SpO2分别用bpm、mmHg、%或百分点记录；只有目标、参考设备、主体划分、窗口、分母和实验条件相容时才比较误差。[152]

方法分类包括颜色通道或盲源分离（GREEN、CHROM、ICA、POS）、时空深度模型（CNN、RNN/Transformer）以及视频放大和混合模型；这些是方法类别，不等同于单篇论文结果。[149][176] 原始实证全文是纳入门槛；综述或参考文献表只能发现候选，不能用定性描述补齐缺失的性能数字。[150][176]

| 对象 | 截至截止日的候选与证据状态 |
|---|---|
| HR | 候选包括2020年的AutoHR、Cross-Verified Feature Disentangling，2022年的PhysFormer及2023年的PhysFormer++和Arbitrary-Resolution rPPG。[149][147] RePSS挑战测试集（1000个片段）中Mixanik的MAE为6.94 bpm、RMSE为10.68 bpm、相关系数R=0.75；OBF子集最佳MAE为2.56 bpm。[148] |
| BP | 候选包括Windkessel波形特征模型（2022）、GAN合成数据rPPG模型和面部视频深度网络（2023）。ReViSe使用智能手机面部视频和rPPG，在自建Video-BP上报告SBP MAE 6.7 mmHg、DBP MAE 9.6 mmHg；模型训练另使用指尖传感器信号。[176][152] |
| SpO2 | 2023年候选包括面部视频神经网络；“红外运动放大面部视频”属于非核心红外模态。ReViSe在PURE上报告SpO2 MAE 1.64%，但来源未给出参考血氧仪、主体划分和统计分母，须保留这些限制。[176][152] |

数据集边界核验示例：PURE为10名受试者、60段面部视频，30 fps、640×480，含六种头部运动，指夹式血氧仪参考PPG采样率60 Hz。[149] COHFACE为40名受试者、160段约1分钟RGB面部视频，并同步HR和呼吸率信号。[132] VIPL-HR-V2为500名受试者、2500段RGB视频，分辨率960×720；每人由30秒原视频切出5段10秒片段，访问需研究机构申请。[136] 原版VIPL-HR另报告107名受试者、2378段VIS和752段NIR视频，按个案提供研究访问。[163][135] UBFC-Phys为56名受试者，含视频、BVP和EDA，设置休息、演讲及算术任务，并公开下载。[122] MMPD为33名受试者、约1152K帧，覆盖肤色、身体运动和光照等多域条件。[137]

普通摄像头承担面部视频的非接触光学采集角色：消费级相机捕捉皮肤颜色的微小变化，由IPPG/rPPG提取脉搏波，网络摄像头可输出HR（BPM）[124][47]。但低帧率和较差成像质量会降低HR等参数准确率，运动与环境光会污染弱BVP，并使证据难以外推到对成像质量要求更高的SpO2[177][65]。

面部视频是HR、BP和SpO2共用的光学观测层：rPPG从RGB帧间皮肤颜色变化反映血容量，经过帧提取、ROI检测、信号处理和体征估计；ROI可取整脸、额头或脸颊[43][164]。运动、光照、模糊和遮挡会使ROI不稳并污染信号，单一额头或脸颊ROI还可能因头发、头巾或斜视角失效[171][114]。

rejected: no_entity；智能手机作为普通摄像头时，面部视频可在30fps、640×480或30fps、1920×1080下采集；帧率、分辨率、照明、距离和背景会改变视频质量，运动与环境光污染弱BVP，较深肤色也会使HR估计变差，RGB在低照度和波动光照下不如NIR稳健，而RGB–NIR改善低光HR需双模态相机[117][121][165][65][118][116][154]。

网络摄像头结果应保留帧率、分辨率、照明、距离、运动和同步参考：典型协议要求受试者静息、安静、直视摄像头，并与标准系统同步，摄像头距面部60cm[43][56]。低光、头部运动、低分辨率和低帧率会降低或扰乱rPPG质量，因此受控条件下的HR、BP和SpO2结果不宜直接外推到真实场景[111][44][118]。

面部视频管线通常是逐帧取脸、ROI跟踪与空间池化、去噪/滤波、信号提取和体征估计；GREEN、ICA、CHROM、POS等使用整脸或皮肤ROI，HR可由颜色峰值获得，SpO2由颜色通道估计，BP可由时空图和BPE-Net的深度特征、区间分类及数值计算器输出[43][164][114][151]。运动模糊会使标志点和ROI不确定，Wiener恢复、mLMS滤波及运动鲁棒的时空表示可减轻该限制[114][169]。

范围限定为普通智能手机或网络摄像头拍摄的面部视频：摄像头捕捉皮肤颜色变化，rPPG形成BVP并估计HR，其他视觉模态或非面部输入另行标注；普通网络摄像头的低帧率和成像质量会压低准确率，因此HR、BP、SpO2的技术与性能应分开报告并保留采集条件[43][47][177][65]。

统一口径是HR用BPM；BP拆为SBP和DBP，分别表示收缩期最大压力和舒张期两次搏动间最低压力，参考可记录侵入式动脉压力；SpO2用百分比，并记录参考脉搏血氧仪及≤3.5%的报告界限[47][88][48][56]。方法可按颜色/绿色通道、ICA、CHROM、POS等rPPG、ROI策略及时空特征图组织；HR适合颜色峰值，SpO2依赖颜色通道，BP适用性需另行验证[164][114][65]。

报告结构按范围与定义、HR/BP/SpO2技术与性能、公开数据集、综合比较依次展开；每项结果同时保留参考设备、采集条件和指标单位，普通摄像头面部视频是主线[43]。

研究范围是普通摄像头、面部视频、ROI/rPPG和体征估计：摄像头负责采集，面部视频提供皮肤颜色变化，rPPG形成BVP并支持HR；BP和SpO2在同一视觉输入上分别保留波形或颜色通道路径[124][43][114][65]。

智能手机扩大了Android、iOS和Web部署，并可与笔记本或网络摄像头并列验证；但光照、帧率、分辨率、距离和运动会改变弱BVP，低质量消费级设备尤其限制SpO2外推[49][117][177][65]。

网络摄像头结果应同时报告分辨率、帧率、照明、距离、姿态和同步参考；静息、安静并与标准系统同步适合初步对照，但低光、运动和平台质量差异限制外推[56][118][44]。面部处理则依次进行帧提取、ROI检测、信号处理和估计；BP可采用时空图切片、ResNet-BiLSTM特征提取、区间分类和数值计算器[43][151]。

现有材料能确认网络摄像头rPPG输出BPM、BPE-Net输出血压区间与数值，以及与脉搏血氧测量同步的SpO2流程，但未形成HR、BP、SpO2可直接横比的MAE、RMSE、MAPE或准确率口径；逐篇报告时应保留原指标、单位、样本和条件，不应补算[47][151][56]。

数据方面，面部视频的样本总数、人口和场景披露并不总是完整；有研究只说明按参与者和场景组织并含年龄、性别、Fitzpatrick肤色等元数据，另有普通摄像头研究仅在理想光照或受控人群上验证[178][173]。这会使模型学习设备、肤色、光照或静息协议等捷径，削弱训练评估和跨设备、跨人群泛化[107][110]。

面部视频方法可按GREEN、ICA、CHROM、SSR、POS、PBV、LGI分类；ROI质量受解剖结构、皮肤厚度、光照、遮挡和运动影响，严重运动会使手工特征假设失效，而面部对齐、三角patch和自适应patch可减轻跟踪伪影[164][116][165]。

rejected: no_entity；现有证据不足以完整列出HR、BP和SpO2在所要求发表区间内的逐篇论文、数据集开放性及性能；普通摄像头的颜色、白平衡、曝光、内部处理和采集条件会造成HR估计差异，手机硬件、系统或应用限制、低采样率、手持抖动、较深肤色以及SpO2交流分量低信噪比和RGB组合缺陷会削弱信号，复杂光照和运动仍是HR挑战[116][64][168][107]。

rejected: no_entity；现有证据不足以完成按HR、BP和SpO2的逐篇论文筛选；面部视频数据集存在受控任务和窄场景：某数据集含150段、每段60秒、60fps、1080p视频，保持中性表情且无显著头动；大规模面部视频数据集虽超过1,000小时，主要是talking faces，排除eating或crying且非East Asian样本有限[54][128][87]。视频压缩、低SNR、遮挡和肤色差异会使深度模型学习数据集特有线索，限制跨场景泛化[164][165]。

rejected: no_entity；公开面部视频数据集的规模、人口和任务覆盖仍受窄场景限制：受控数据集含150段、每段60秒、60fps、1080p视频，且同步标签仅覆盖122/150段（81.3%）；大规模面部视频数据集虽超过1,000小时，主要是talking faces，排除eating或crying且非East Asian样本有限。部分数据的学术子集需申请，商业研发需联系获取[54][128][87][92]。

rejected: no_entity；受控任务、窄人口和有限动作使面部视频数据难以覆盖自然运动、情绪和跨人群条件；视频压缩、低SNR、遮挡及肤色差异会使深度模型学习数据集特有线索，因而限制技术发展、跨场景评估和泛化能力[54][128][87][164][165]。

**补充证据**

**成熟度结论与判定**

在同一项面部视频—医疗设备对照研究中，HR（240个测量样本）MAE为3.09 bpm、RMSE为5.72 bpm；SpO2（235个）MAE为1.21个百分点、RMSE为1.77个百分点；SBP（463个）MAE为18.15 mmHg、RMSE为22.77 mmHg，DBP（463个）MAE为10.49 mmHg、RMSE为13.71 mmHg[49]。因此，在相同协议内，HR证据最成熟，SpO2在90%–100%范围内次之，BP最不成熟；但bpm、百分点和mmHg不可直接横向排名。关键判定条件包括参考设备、目标范围、受试者独立划分、窗口及光照和运动协议。

普通RGB面部视频的rPPG主要捕获心搏引起的皮肤血容量和颜色微变，HR因此是较直接的周期估计；SpO2还依赖光谱信息与标定，现有研究在90%–100%才显示可接受一致性，低于90%的样本有限[49]。BP则需由脉搏代理间接回归SBP/DBP，在SBP>150或DBP>90时误差更大[49]。另一项受控45人、50 fps摄像机、9折按受试者验证的面部视频实验报告SBP/DBP MAE为3.90/3.72 mmHg，但目标范围仅95–130/60–90 mmHg，不能外推真实场景[296]。低照度、头动以及低端摄像头的帧率和分辨率还会扭曲rPPG[49]。

测试集：手机后摄PPG给出HR MAE 1.4 bpm、SpO2 MAE 1.1%；BP用摄像头PPG+麦克风PCG的PTT，15条记录的SBP/DBP MAE 5.1/7.5 mmHg，HR/SpO2用50条记录训练测试[353]。共同人群、参考设备和独立分割未报告，故不宜排名。须区分内外部验证；外部验证需在新时间、地点或领域检验迁移性[379][387]。SpO2需约660/940 nm双波长，受RGB、照明和肤色影响；BP受血管顺应性影响，rPPG常缺失重搏切迹且通常需袖带校准[112][139]。建议窗口HR 5–10 s、SpO2 2–10 s、BP 5–20 s；库覆盖BP 40–240 mmHg、SpO2 70–100%，RGB照度>50 lux[388]；BP多为≤20名健康正常血压者，限制外推[139]。UBFC 2 m时HR MAE 7.5 BPM，验证仅少量健康志愿者[382]。

成熟度需分层：HR证据相对最多，但运动、光照、肤色和帧率会改变误差；ARPOS（2022，40人，彩色+IR+深度）报告HR RMSE 7.8、活动13（原文列HR/BPM），SpO2 RMSE 2.3、活动2.5（SpO2(%)）[348]。BP由PTT/iPPG波形间接推断；iPPG2BP在57人、157段视频的患者独立Fold 2中，SBP MAE 11.43、MAP MAE 16.41 mmHg[307]。RGB面部视频的运动/振动会污染ROI和颜色信号[114]；rPPG临床方案计划1045人但尚无结果[56]。

截至2024-01-31，成熟度只能条件化判断：HR证据最广，SpO2受控可行但部署受限，BP不可与其直接排名。消费级RGB面部视频HR在PURE、UBFC、COHFACE的MAE分别为1.16、1.56、2.10 bpm[195]；运动、光照和肤色会降低现实可靠性[195]。面部多光谱（非普通RGB）SpO2暗室RMSE为2.55%、环境光仍<4%，但暗室仅15人、肤色单一且用屏气诱发低氧；无参考校准时3人RMSE为5.02%，前30秒校准后为1.47%[354]。2022手机CNN的5.00% MAE/5.55% RMSE来自手指而非面部[97]；2024-03 VIPL-HR结果晚于截止日，不计入历史结论[383]。BP的SBP/DBP验证阈值5/10/15 mmHg不等价[338]。

SpO₂：2023面部VPG法暗室RMSE 2.55%、环境光下<4%；15人（14男1女）、指夹参考，受控结果不能外推临床。[355]

跨设备相机验证：0.5–8 Hz内，Samsung A33、iPhone XR、Pixel 10的平均RMSE（无量纲）分别为0.0170、0.0483、0.0718，均低于0.11阈值[389]；这仅是相机响应，不等于三项体征精度。

截至2024年初，面部IPPG-BP在115人数据（34人测试）中SBP/DBP MAE为5.33/3.92 mmHg[308]；红外面部SpO2在21人数据中RMSE为1.331%[350]；模态、肤色与协议差异使三者不能按误差直接排名[350][308][347]。

HR（ARPOS，2022，rPPG）：静息RMSE 7.8 bpm（r=0.85），活动15 bpm；SpO2静息/活动RMSE 2.3/2.5个百分点[201]。SpO2（2023，网络摄像头）：MAE 0.62个百分点（30人、60点），仅500–650 lux、65 cm、静止[119]。BP（面部视频跨库）：SBP/DBP MAE 12.35/9.54、RMSE 16.55/12.22 mmHg；<10 mmHg仅74.2%/78.8%，低于85%[65]，不可直接排名。

比较须统一目标、单位、参考信号、受试者独立划分、窗口与分母；MAE、RMSE、SD和相关系数不可互换[207]。HR成熟：高质量集PulseGAN/UBFC-rPPG的MAE为1.19 bpm、rPPGNet/OBF的RMSE为1.8 bpm；VIPL-HR上RhythmNet的MAE/RMSE为8.11/5.30 bpm，DeepPhys为11/13.8 bpm，性能依赖场景[207]。2023年BPE-Net跨集（MPM-BP训、MMSE-HR测）SBP/DBP MAE为12.35/9.54 mmHg，误差<10 mmHg仅74.2%/78.8%，未达85%门槛，BP较不成熟，仍受运动、光照和数据少影响[151]。PURE为10人、60视频；Vital Videos为850人、每人两段30秒视频，但未见SpO2误差，不能排序[231][140]。

HR6.67bpm；SBP/DBP6.06/7.05%；SpO₂1.012%，不横比。[126][380][144]

在普通RGB面部视频的可比条件下，成熟度为HR最高、BP次之、SpO2最弱：COHFACE（2020）受试者独立测试中，DeepPhys平均MAE约5 bpm，手工法约15 bpm、POS约24 bpm[133]；BP自建10名健康志愿者的mean BP相关系数0.85、MAE 5.4 mmHg[304]；消费级SpO2截至2020年9月无纳入研究[131]。PURE含10人、60段序列及同步指夹血氧仪（30 Hz、640×480、参考60 Hz），但未报告视觉SpO2/BP性能[285]。光照、运动、分辨率、帧率、肤色和遮挡扰动rPPG[384]；BP为间接估计、SpO2受波长约束，不能无条件横排。

[86]2022：MAE:HR3.09bpm；SBP/DBP18.15/10.49mmHg；SpO₂1.21%

HR：UBFC-RPPG MAE 1.64 bpm[107]；BP未见集RMSE 12.95 mmHg[295]；SpO₂参考有肤色偏差[103]，不可直接排名。

BP仍早期[306]

在同一口径下不能强行排名：HR在MAHNOB-HCI的487段视频上RMSE为7.4 bpm、绝对误差<5 bpm比例为79.2%（ECG参考）[165]；BP在10名健康志愿者上mean-BP MAE为5.4 mmHg、r=0.85[314]；SpO₂在70–100%校准范围内误差<4个百分点[364]。三者测试协议不同，数值不可直接横比。

HR较成熟：2020年PURE全场景旋转校正MAE/RMSE=2.031/2.7974 bpm[213]；BP：2022年814人、8s面部iPPG，SBP/DBP MAE=8.36±6.22/5.69±3.97 mmHg[70]。iPTT仅负相关未报误差[315]；运动/光照/遮挡污染rPPG[72]。

HR受控可测性较强但不可外推临床：2021年UBFC-Phys（56人、168视频）MAE 0.95/3.96/2.36 bpm（静息/演讲/算术），PCC 0.83/0.42/0.61，运动增噪[399]；接触式BP无校准泛化弱[83]；该SpO2页面未报可比误差[386]。


HR研究多但多为受控小样本[105]；BP需由血流/血容量间接推断[397]；2021年SpO2：RGB/YCgCr、10名受试者、85–100%，MAE 0.537、RMSE 0.692个百分点[78]；2022年RGB信号弱10–100倍且受光照、肤色、运动影响[45]。

HR证据最广；SpO₂研究较少，BP尚缺同协议数值，不能直接排名[192]。CPulse在PURE/UBFC/COHFACE的MAE为0.98/1.06/1.99 bpm[189]；PFE‑TFA在PURE/COHFACE为1.44/1.31 bpm[194]。ARPOS家庭场景SpO₂ RMSE为2.3%，活动时为2.5%[192]；运动、光照和设备差异会污染弱rPPG[169]。

HR跨库MAE=5.98bpm（2020）；不宜与BP/SpO2直排。[199]

结论：HR在受控面部视频上可达MAE 1.75 bpm，但跨集升至UBFC-RPPG 2.15、COHFACE 5.57 bpm；压缩、光照、运动和ROI漂移是关键混杂因素[208]。该研究未给BP/SpO2数值，不能据此直接排名[124]。

截至2024年初，HR证据较广：5个公开视频数据集评估8种rPPG方法，最佳四法差异不显著[130]；受控MAE 1.04 bpm，HCI为4.79 bpm[395]。BP的SBP/DBP MAE为9.97/7.59 mmHg[223]；SpO2一项研究仅14人、RMSE<3.1%[223]，两者外部验证不足。

结论：HR证据最广、多受控；运动、光照、距离会降效。[171]2023年PURE（10人、59/60段、30fps）稳态MAE1.200bpm、PCC.996、TPR1.000；ReViSe的MAE3.95bpm、RMSE未报。[109][154]BP为间接波形/PTT映射，静止60cm时SBP/DBP RMSE6.91/4.88mmHg，骑行升至25.7mmHg；SpO2研究少，RGB受血容量、血管收缩、温度影响，不能硬排。[120]

RhythmNet在VIPL-HR彩色视频上的HR MAE为5.79 bpm、RMSE为8.94 bpm；跨库MMSE-HR测试的RMSE为10.58 bpm[167]。

HR较成熟：跨库MAE 5.98 bpm[270]；BP仍新兴，SBP/DBP MAE 10.19/7.09 mmHg[269]，且受肤色、光照、运动及小样本验证限制[184]；SpO₂低氧RGB筛查误差<4个百分点[364]，不同协议不可直接排名。

HR证据较充分：42/50项研究[390]；BP实验室（2021）SBP/DBP MAE9.97/7.59mmHg[190]；SpO₂仅5/50项[390]。

HR公开集报告MAE 1.64、5.02 bpm[117][68]；PTT型BP需个体校准[90]；SpO2理想光照MAE 1.26±0.68个百分点（10人）[181]

HR较稳健；BP更具挑战；SpO2低氧证据不足。[43][141]


HR12.59bpm[288]BP5人[214]；SpO₂1.171%[374]

HR较成熟[134]

结论：截至2024-01-31，在普通RGB面部视频中，HR受控测量最成熟，BP证据最弱；SpO2在校准和正常范围内误差可小，但低氧、跨设备验证不足，不能按单一MAE排名。2025急诊研究、2026综述均越过截止日，不纳入本截面。[381]

HR的rPPG直接从面部颜色变化恢复BVP/脉搏频率。ReViSe（2022）在TokyoTech、PURE和自建Video-HR上的HR MAE分别为1.73、3.95、2.49 bpm；TokyoTech为9人，PURE为10人、原始60段（研究使用59段）、30 fps/640×480，含静息、说话、平移和旋转；Video-HR为日常环境15人，MAE为2.49 bpm。[267][401] 2021年ROI比较中，PURE某组合RMSE由静息1.08升至说话4.09 bpm，脉搏提取成功率为88.37%–100%，表明运动、ROI失败和窗口定义会改变结果。[175]

BP需把BVP时域特征经非线性模型或校准映射为SBP/DBP。ReViSe以公开指尖PPG训练、以自建Video-BP测试：49人、144样本，SBP/DBP范围85–168/50–103 mmHg，MAE为6.7/9.6 mmHg，且当时无公开“面部视频+BP”数据集。[267] 静止、60 cm时SBP/DBP RMSE为6.91/4.88 mmHg，骑行时升至25.7 mmHg；BMI框架报告相对误差2.42%/5.53%，但口径不同，不能横比。[394][191]

SpO2依赖红蓝通道比值与校准，并受血容量、血管收缩和温度影响。[394] ReViSe在PURE的MAE为1.64%，但SpO2范围仅90–100%；2021框架平均误差为1.4%。2023年LOSO（60人）中，手机、网络摄像头和工业相机MAE分别为4.39%、4.45%和4.22%，显示设备域差异。[267][191][360] 综述筛选的2018–2021证据中，HR/BP/SpO2文章数为60/6/1，证据广度不对称。[394]

Lin等（2023）私有288视频的汇总RMSE为5.33、4.11、3.75，但未绑定目标单位或划分；RhythmNet（2020）当前片段也无性能数值，二者只能作部分证据，不能排名。[265][401]

截至2024年初，ReViSe：TokyoTech/PURE/Video-HR的HR MAE=1.48/4.20/2.49 bpm，PURE的SpO2 MAE=1.60%[156]；自建Video-BP的SBP/DBP MAE=6.7/9.6 mmHg（49人、144样本）[156]。协议异质，勿排名。2023年220名心血管病患者研究的SBP/DBP MAE±STD=9±13/7±10 mmHg[339]。

ReViSe(2022)报告：HR MAE为TokyoTech1.48、PURE4.20bpm；SpO2（PURE）1.60%；SBP/DBP（Video-BP）6.7/9.6mmHg[158]。BP仅自建49人、144样本；HR相对成熟，BP/SpO2须跨主体、低氧及临床验证，不可跨单位比较[158][396]。

截至2024-01-31，HR证据最充分但依赖受控协议：ReViSe在TokyoTech、PURE、自建Video-HR上的MAE为1.73、3.95、2.49 bpm；PURE仅10人、6种运动、脉搏血氧仪参考[326][271]。SpO2在PURE为1.64% MAE（百分比/百分点口径未明）[326]；BP在自建Video-BP为SBP/DBP 6.7/9.6 mmHg，训练用指尖信号[393]。HR只需频率，BP需完整波形切迹，不能按误差直排[157]；运动、光照、肤色限制泛化[271]。

Lin等（2023）HR与Omron参考相关系数0.988（288样本）[278]；ReViSe在TokyoTech、PURE、日常Video-HR的HR MAE为1.73、3.95、2.49 bpm（2022）[280]；其Video-BP的SBP/DBP MAE为6.7/9.6 mmHg，PURE的SpO2 MAE为1.64%，但参考、分母和百分点口径未明[280]。

结论：HR较成熟：ReViSe在TokyoTech/PURE的MAE为1.73/3.95 bpm，V4V连续cMAE9.22–15.45；BP仅自建Video-BP（SBP/DBP MAE 6.7/9.6 mmHg），SpO2在PURE为1.64%。PURE仅10人/60段，运动、光照、肤色、分辨率和标签不足造成域偏移；COHFACE studio→natural相关−0.24/−0.03/0.00。[392][398][284][391][232]


在同一指标的单位、参考设备和测试条件可比时，HR证据更广且更稳健：公开COHFACE上DeepPhys平均MAE约5 bpm，手工方法约15 bpm、POS约24 bpm；PURE旋转校正全场景MAE为2.031 bpm。[133][213] BP在45名受试者、9折交叉验证中SBP/DBP MAE为3.90/3.72 mmHg，但跨数据集分别为12.35/9.54 mmHg，误差小于10 mmHg的比例仅74.2%/78.8%，低于85%标准，故外部验证和部署鲁棒性弱于HR。[296][151]

HR相对SpO2成熟度更高：HR在PURE旋转校正全场景MAE为2.031 bpm、RMSE为2.797 4 bpm，并有跨库MAHNOB-HCI测试MAE 5.98 bpm；SpO2在家庭或受控RGB条件下虽有RMSE 2.3%及Cg/Cr路线MAE/RMSE 0.537/0.692，但70–100%范围的CNN仍为MAE 5.00%、RMSE 5.55%，高于3.5%标准。[213][270][201][78][97] 由于bpm与百分比不是共同单位，不能按误差绝对值硬排；按公开数据、跨库验证和场景数量，HR领先SpO2。[201]

BP与SpO2缺乏可无条件横比的共同协议：BP在静止、60 cm时SBP/DBP RMSE为6.91/4.88 mmHg，骑行时升至25.7 mmHg，跨数据集MAE为12.35/9.54 mmHg；SpO2在受控RGB条件下Cg/Cr路线MAE/RMSE为0.537/0.692，但局限于85–100%范围，环境光还使RMSE增加约1%。[120][151][78][354] BP有较明确的跨数据集检验，SpO2则有较低的受控误差却更受波长、校准和测量范围限制；两者部署鲁棒性均不足，BP还受远程波形缺失重搏切迹影响。[394][139]

HR主要利用周期性BVP，面部ROI、ICA/峰值检测或深度时空模型即可估计频率；但rPPG变化可仅为0.01%–10%，运动、光照、摄像头和ROI误差会淹没信号。[400][169][224] BP是间接估计，常由PTT/PWV拟合BP=a·PTT+b，远程波形又常丢失重搏切迹，故需校准且SBP比DBP更难；SpO2需两个波长或颜色的吸光度比，波长和反射路径会改变结果，而监督深度学习还要求大规模、严格同步的接触式标签，限制跨场景泛化。[223][139][308][224][385][116]

普通摄像头可在环境光下提取HR/RR，但低帧率和较差成像质量降低准确率，且难满足SpO2的成像要求；RGB对光照变化敏感，NIR更稳健，RGB–NIR融合虽改善低光HR，却不再是单一普通RGB部署。[177][154] 实际设置横跨30 fps、640×480或1920×1080、约60 cm或0.5 m；帧率、分辨率、背景、距离和照度共同改变ROI信噪比，BP在50–60 cm、150–200 lux等受控条件下表现最好，限制三项体征的真实环境泛化。[96][165][118][120]

面部视频通常经历人脸检测、ROI跟踪、空间池化、滤波和信号提取；运动、表情、光照、遮挡及头发、头巾或斜视角会使ROI不稳并污染BVP，造成HR、BP和SpO2估计误差。[43][164][171][78] 监督式模型依赖视频与接触式标签严格同步，而公开数据还存在任务单一和标签不完整，例如150段视频中仅122段（81.3%）可用；在30帧/s、10 s等短窗口上训练的模型因此难以跨运动、设备和光照泛化。[116][54][378]

所列HR论文显示，HR算法和跨库验证最成熟：COHFACE上DeepPhys平均MAE约5 bpm，手工方法约15 bpm、POS约24 bpm；PURE旋转校正全场景MAE/RMSE为2.031/2.797 4 bpm，中幅旋转为1.615/2.070 4 bpm，VIPL-HR与UBFC训练、MAHNOB-HCI测试的MAE为5.98 bpm（CAN为4.57 bpm）。[133][213][270] BP在受控研究可报SBP/DBP MAE 5.33/3.92 mmHg，但跨数据集为12.35/9.54 mmHg；SpO2虽有普通摄像头RMSE 2.3%或智能手机MAE 1.1%的结果，却受受控协议、校准和较少公开验证约束，因此总体上HR领先，BP与SpO2均需更多外部验证，不能按不同单位误差硬排。[308][151][201][353]

**补充证据**

审计口径（截至2024-01-31）：原始论文/官方数据页优先。ReViSe（Qiao等，IEEE Access 2022，DOI 10.1109/ACCESS.2022.3229977）报告TokyoTech/PURE HR MAE 1.73/3.95 bpm、PURE SpO2 MAE 1.64%、Video-HR 2.49 bpm、Video-BP SBP/DBP MAE 6.7/9.6 mmHg。[267] Lin等（iScience 2023）以288视频、Omron HEM-7124为参考，BP DBP/SBP RMSE 3.75/4.11、MAPE 4.95%/3.73%。[278] RGB-SpO2原始论文（2022）仅核得“百分点”误差，具体值待核。[45] VIPL-HR-V2：500人、2500 RGB视频、960×720，协议申请[136]；UBFC-Phys：公开56人，休息/演讲/算术、视频+BVP/EDA[122]；MAHNOB-HCI：27人、20情绪视频、网页提供[439]。其余书目/二手线索、后截止来源、接触式传感器及HRV结果不替代目标证据。[434][172][246]

已定位到 ReViSe 的可核验来源 DOI 10.1109/ACCESS.2022.3229977[267]；其余论文、数据集、性能和表格字段在证据不足处应标为 NR、未报告、未核验、不适用或冲突，不得用常识、二手摘要或相邻数据集数值填补，并按用户要求依次组织技术与性能、公开数据集和综合分析。

## 参考文献

[1] <https://ojs.aaai.org/index.php/AAAI/article/view/25217/24989> HR公开基准研究; PFE-TFA; COHFACE与分辨率研究
[2] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9760129/> 医院多体征评估; 医院评估; 医院HR结果与设置; 医院验证全文; 医院结果表与讨论; 医院BP分层结果; 医院SpO2分层表; 同系统多体征医院评估; SpO2分层
[3] <https://www.behealth.hk/wp-content/uploads/2023/12/An-Algorithmic-Benchmark-for-Contactless-SPO2-Measurement-from-Facial-Videos.pdf> SpO2公开基准; RoR基准比较; Cheng等方法与划分; SpO2范围分层; 设备分层结果
[4] <https://openaccess.thecvf.com/content/CVPR2022W/CVPM/papers/Wu_Contactless_Blood_Pressure_Measurement_via_Remote_Photoplethysmography_With_Synthetic_Data_CVPRW_2022_paper.pdf> Wu等数据组成; 采集与划分; 模型与结果; 千人BP队列
[5] <https://arxiv.org/pdf/2302.03840> MMPD; MMPD规格; MMPD跨肤色实验; MMPD动机与协议
[6] <https://link.springer.com/article/10.1007/s11042-023-16794-9> 面部视频rPPG范围综述; 传统处理与学习式分类
[7] <https://www.frontiersin.org/journals/physiology/articles/10.3389/fphys.2022.801709/full> 可见光生理监测机制; SpO2生理与成像原理
[8] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10721846/> BP路径综述; 合成数据能力边界
[9] <https://doi.org/10.1109/jiot.2024.3351838> 视觉与BCG分类; 2024年1月数据综述; 数据访问类型
[10] <https://export.arxiv.org/pdf/2306.11891v1.pdf> Vital Videos; Vital Videos硬件与标签; Vital Videos访问条款; Vital Videos人口与标注; Vital Videos设备反思; Vital Videos信号质量
[11] <https://www.mdpi.com/2079-9292/12/18/3771> 接触式到rPPG迁移; Kim等数据与模型; Kim等结果; 迁移学习结果比较
[12] <https://arxiv.org/html/2210.00716v3> 工具箱后处理协议; BP4D+标签与伪标签; 伪标签生成机制; 标准化问题; UBFC-Phys筛选列表; 工具箱跨库结果
[13] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10055237/> BPE-Net阈值结果; BPE-Net摘要及表5; BPE-Net方法; 切片消融; 两个数据集的差异; BP区间分析; BPE-Net标准讨论; BP分布分析
[14] <https://doi.org/10.1109/EMBC40787.2023.10340995> 手机SpO2研究; 手机面部血氧研究; 同研究脉率结果
[15] <https://vipl.ict.ac.cn/publications/2020/conf/202212/P020221229824014728205.pdf> CVD消融实验; CVD多库结果
[16] <https://www.ecva.net/papers/eccv_2020/papers_ECCV/papers/123720392.pdf> Meta-rPPG
[17] <https://www.ecva.net/papers/eccv_2022/papers_ECCV/papers/136760351.pdf> 方法与比较结果; Meta-rPPG结果引述; 增强方法与数据组成; 跨数据集增强结果; 划分与分布分析; PURE任务与主体划分
[18] <https://openaccess.thecvf.com/content/CVPR2022/papers/Yu_PhysFormer_Facial_Video-Based_Physiological_Measurement_With_Temporal_Difference_Transformer_CVPR_2022_paper.pdf> PhysFormer
[19] <https://ar5iv.labs.arxiv.org/html/2304.14789> 统一处理与结果; 噪声退化结果; 统一再评测
[20] <https://openaccess.thecvf.com/content/CVPR2022W/CVPM/papers/Speth_Remote_Pulse_Estimation_in_the_Presence_of_Face_Masks_CVPRW_2022_paper.pdf> 真实口罩实验; 口罩增强结果
[21] <https://doi.org/10.1109/access.2022.3229977>
[22] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10542939/> Lin等HR分析; Lin等BP结果
[23] <https://www.mdpi.com/2227-9709/9/3/57> HR信号处理综述; 设备与信号综述
[24] <https://openaccess.thecvf.com/content/WACV2023/papers/Liu_EfficientPhys_Enabling_Simple_Fast_and_Accurate_Camera-Based_Cardiac_Measurement_WACV_2023_paper.pdf> EfficientPhys原论文
[25] <https://ar5iv.labs.arxiv.org/html/2109.10471> V4V评价公式与结果; V4V方法说明; V4V划分与条件; V4V参考系统
[26] <https://doi.org/10.1109/jbhi.2023.3265857> 2023年扩展结果; TVGH夜间实验
[27] <https://doi.org/10.7507/1001-5515.202211071> 血压与脉搏生理机制; vPPG特征差异; 闫昊等全文; 数据与视频结果; BHS分级表; BP生理机制与特征
[28] <https://arxiv.org/html/2212.07116v2> DC/AC-STMap论文; 采集与五折设置; DC/AC模型结果
[29] <https://doi.org/10.1109/EMBC40787.2023.10340025> 消费级RGB通道比实验; Chan等降氧实验
[30] <https://doi.org/10.3390/info14060301> 红外EVM研究
[31] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9735266/> 多模型融合研究
[32] <https://doi.org/10.1109/jsen.2023.3284196> KNN多设备研究
[33] <https://sites.google.com/view/ybenezeth/ubfcrppg> UBFC官方子集说明
[34] <https://arxiv.org/html/1810.04927v2> VIPL-HR多设备参数
[35] <https://www.idiap.ch/en/dataset/cohface>
[36] <https://oulurepo.oulu.fi/bitstream/handle/10024/25678/nbnfi-fe2019080623583.pdf?sequence=1> OBF组成与采样
[37] <https://cameravitals.github.io/datasets.html>
[38] <https://vipl.ict.ac.cn/en/resources/databases/202007/t20200714_32718.html> VIPL-HR-V2官方说明; V2使用协议
[39] <https://doi.org/10.3390/s22114097> 研究数量统计; 研究统计
[40] <https://digituma.uma.pt/server/api/core/bitstreams/054fe1b9-c70a-4d49-8109-deffc7339e33/content> 面部研究综述; 样本规模统计; 人口与临床条件统计
[41] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10260340/> 临床HR荟萃分析
[42] <https://raw.githubusercontent.com/KegangWangCCNU/PICS/main/FullBench.pdf> 数据质量审计; 同步扰动实验
[43] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9760129/>
[44] <https://doi.org/10.1109/icpr.2010.888>
[45] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9774849/>
[46] <https://www.academia.edu/60000656/Contactless_Heart_Rate_Estimation_From_Facial_Video_Using_Skin_Detection_and_Multi_resolution_Analysis>
[47] <https://www.labvanced.com/content/technology/zh/remote-physiological-measurement/>
[48] <https://faceheart.com/research>
[49] <https://www.cureus.com/articles/119946-evaluation-of-a-camera-based-monitoring-solution-against-regulated-medical-devices-to-measure-heart-rate-respiratory-rate-oxygen-saturation-and-blood-pressure>
[50] <https://www.hopkinsmedicine.org/health/conditions-and-diseases/vital-signs-body-temperature-pulse-rate-respiration-rate-blood-pressure>
[51] <https://nursingcecentral.com/lessons/measuring-recording-and-reporting-vital-signs/>
[52] <https://web.stanford.edu/class/cs231a/prev_projects_2016/finalReport.pdf>
[53] <https://arxiv.org/abs/2010.12769>
[54] <https://doi.org/10.3758/s13428-022-01951-z>
[55] <http://www.nature.com/articles/s41746-023-00973-x/tables/2>
[56] <https://doi.org/10.1136/bmjopen-2020-047896>
[57] <https://dl.acm.org/doi/10.1145/3341105.3373905>
[58] <https://panoptic.ai/technology>
[59] <https://doi.org/10.1016/j.annemergmed.2025.06.138>
[60] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8884444/>
[61] <https://smartscanpro.ai/all-metrics.html>
[62] <https://gwinnettlung.com/blog/decoding-pulse-oximetry-readings-what-each-number-means/>
[63] <https://www.sciencedirect.com/science/article/pii/S1746809421010545>
[64] <https://upcommons.upc.edu/bitstreams/ab885958-aae8-458c-946f-8024b7c42ace/download>
[65] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10055237/>
[66] <https://arxiv.org/html/2502.02229v1>
[67] <https://samproell.io/posts/yarppg/yarppg-intro/>
[68] <https://vipl.ict.ac.cn/publications/2020/conf/202212/P020221229824014728205.pdf>
[69] <https://smj.researchcommons.org/cgi/viewcontent.cgi?article=8723&context=journal>
[70] <https://doi.org/10.1109/jsen.2022.3230210>
[71] <https://pdfs.semanticscholar.org/3750/b635d455fee489305b24ead4b7e9233b7209.pdf>
[72] <https://openaccess.thecvf.com/content/ICCV2021W/V4V/papers/Kossack_Automatic_Region-Based_Heart_Rate_Measurement_Using_Remote_Photoplethysmography_ICCVW_2021_paper.pdf>
[73] <https://ceur-ws.org/Vol-3750/paper6.pdf>
[74] <https://d-nb.info/1333436637/34>
[75] <https://doi.org/10.1088/1361-6579/ab2c9f>
[76] <https://ar5iv.labs.arxiv.org/html/2002.04821>
[77] <https://github.com/McJackTang/MMPD_rPPG_dataset>
[78] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8470331/>
[79] <http://jultika.oulu.fi/files/nbnfi-fe2021120959958.pdf>
[80] <https://www.idiap.ch/software/bob/docs/bob/docs/v5.0.0/bob.db.cohface/doc/index.html>
[81] <https://www.idiap.ch/software/beat/docs/bob/docs/v6.1.2/bob/bob.db.cohface/doc/index.html>
[82] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10362790/>
[83] <https://www.frontiersin.org/journals/digital-health/articles/10.3389/fdgth.2022.1090854/full>
[84] <http://arxiv.org/abs/2202.08913v1>
[85] <http://arxiv.org/abs/2007.06786v1>
[86] <https://doi.org/10.1101/2022.10.20.22281306>
[87] <https://arxiv.org/html/2410.07151v1>
[88] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7962188/>
[89] <https://link.springer.com/article/10.1007/s44163-026-01610-8>
[90] <https://www.frontiersin.org/journals/digital-health/articles/10.3389/fdgth.2021.770096/full>
[91] <https://wwwn.cdc.gov/nchs/data/nhanes/public/2019/manuals/2019-Blood-Pressure-Procedures-Manual-508.pdf>
[92] <https://vitalvideos.org/>
[93] <https://doi.org/10.1109/jbhi.2023.3265857>
[94] <https://doi.org/10.1109/embc40787.2023.10340995>
[95] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9944565/>
[96] <https://ep.liu.se/ecp/129/002/ecp16129002.pdf>
[97] <https://www.nature.com/articles/s41746-022-00665-y>
[98] <https://arxiv.org/html/2212.07116v2>
[99] <https://sra.samsung.com/publications/estimating-spo2-with-deep-oxygen-desaturations-from-facial-video-under-various-lighting-conditions-a-feasibility-study/>
[100] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8758222/>
[101] <https://doi.org/10.1109/embc40787.2023.10340025>
[102] <https://doi.org/10.1109/delcon57910.2023.10127508>
[103] <https://www.tga.gov.au/news/safety-updates/limitations-pulse-oximeters-and-effect-skin-pigmentation>
[104] <https://doi.org/10.1109/sipaim56729.2023.10373518>
[105] <https://www.medrxiv.org/content/10.1101/2023.10.12.23296882.full>
[106] <https://vipl.ict.ac.cn/publications/2019/conf/202212/P020221230382713111817.pdf>
[107] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9484436/>
[108] <https://doi.org/10.1109/icac3n56670.2022.10074569>
[109] <https://www.tmrjournals.com/public/articleHTML/TMR/TMR20230704001/index.html>
[110] <https://arxiv.org/html/2210.15401v2>
[111] <https://link.springer.com/article/10.1007/s10489-024-05354-9>
[112] <https://www.frontiersin.org/articles/10.3389/fphys.2022.801709/pdf>
[113] <https://www.iris.unicampus.it/handle/20.500.12610/70063>
[114] <https://doi.org/10.1109/tbme.2019.2908349>
[115] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9952130/>
[116] <https://arxiv.org/html/2310.15043>
[117] <https://opg.optica.org/boe/abstract.cfm?uri=boe-13-9-4494>
[118] <https://doi.org/10.3758/s13428-024-02398-0>
[119] <https://doi.org/10.3390/bioengineering10050524>
[120] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9185528/>
[121] <https://www.frontiersin.org/journals/physiology/articles/10.3389/fphys.2022.933397/full>
[122] <https://sites.google.com/view/ybenezeth/ubfc-phys>
[123] <https://doi.org/10.3390/s23041753>
[124] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7173900/>
[125] <https://ar5iv.labs.arxiv.org/html/2304.14789>
[126] <https://dl.acm.org/doi/fullHtml/10.1145/3592686.3592696>
[127] <https://arxiv.org/html/2107.13193v2>
[128] <https://arxiv.org/html/2410.07151v2>
[129] <https://www.mdpi.com/1424-8220/21/18/6120>
[130] <https://doi.org/10.1109/access.2020.3040936>
[131] <https://doi.org/10.1007/s10877-021-00734-9>
[132] <https://zenodo.org/records/4081054>
[133] <http://arxiv.org/pdf/2005.11101>
[134] <https://www.frontiersin.org/journals/physiology/articles/10.3389/fphys.2022.801709/full>
[135] <https://vipl.ict.ac.cn/resources/databases/201811/P020250418547807532053.pdf>
[136] <https://vipl.ict.ac.cn/en/resources/databases/202007/t20200714_32718.html>
[137] <https://github.com/THU-CS-PI-LAB/MMPD_rPPG_Dataset>
[138] <https://arxiv.org/pdf/2110.13362v2.pdf>
[139] <https://www.oaepublish.com/articles/chatmed.2022.25>
[140] <https://doi.org/10.48550/arxiv.2306.11891>
[141] <https://www.mdpi.com/1424-8220/21/18/6022>
[142] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6697643/>
[143] <https://www.mdpi.com/1424-8220/22/23/9373>
[144] <https://www.behealth.hk/wp-content/uploads/2023/12/An-Algorithmic-Benchmark-for-Contactless-SPO2-Measurement-from-Facial-Videos.pdf>
[145] <https://www.academia.edu/113122413/Using_Contactless_Facial_Image_Recognition_Technology_to_Detect_Blood_Oxygen_Saturation>
[146] <https://pmc.ncbi.nlm.nih.gov/articles/PMC4467696/>
[147] <https://ojs.aaai.org/index.php/AAAI/article/view/25217>
[148] <https://openaccess.thecvf.com/content_CVPRW_2020/papers/w19/Li_The_1st_Challenge_on_Remote_Physiological_Signal_Sensing_RePSS_CVPRW_2020_paper.pdf>
[149] <https://arxiv.org/pdf/2210.15401>
[150] <https://www.frontiersin.org/journals/cardiovascular-medicine/articles/10.3389/fcvm.2022.894224/full>
[151] <https://www.mdpi.com/1424-8220/23/6/2963>
[152] <https://matilda.science/work/b6fac684-41e4-4ae1-ac0b-cd68ab3f925c>
[153] <https://doi.org/10.1109/access.2022.3229977>
[154] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10346879/>
[155] <https://www.mdpi.com/1424-8220/21/18/6296>
[156] <https://arxiv.org/pdf/2206.08748v2.pdf>
[157] <https://www.mdpi.com/2306-5354/9/10/485>
[158] <https://ieeexplore.ieee.org/document/9989351>
[159] <http://vipl.ict.ac.cn/publications/2020/jour/202212/P020221229804125486669.pdf>
[160] <https://www.mdpi.com/2227-9709/9/3/57>
[161] <https://renchengsong.github.io/papers/resol_dist_rPPG.pdf>
[162] <https://doi.org/10.1016/j.isci.2023.107845>
[163] <https://doi.org/10.1109/tip.2019.2947204>
[164] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8659899/>
[165] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5947898/>
[166] <https://arxiv.org/pdf/1910.11515>
[167] <https://arxiv.org/html/1810.04927v2>
[168] <https://doi.org/10.1364/boe.423508>
[169] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9671618/>
[170] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10088718/>
[171] <https://www.medrxiv.org/content/10.1101/2023.10.12.23296882v1.full.pdf>
[172] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9939538/>
[173] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12505149/>
[174] <https://arxiv.org/pdf/2302.03840>
[175] <https://doi.org/10.3390/app11083467>
[176] <https://doi.org/10.1038/s41746-023-00973-x>
[177] <https://signal.ejournal.org.cn/cn/article/pdf/preview/10.16798/j.issn.1003-0530.2017.3A.012.pdf>
[178] <https://huggingface.co/datasets/pjtoye/VitalVideos-Worldwide>
[179] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11781723/>
[180] <http://arxiv.org/abs/2208.04947v1>
[181] <https://orbit.dtu.dk/en/publications/remote-estimation-of-peripheral-oxygen-saturation-and-pulse-rate-/>
[182] <https://www.noldus.com.cn/what-is-rppg%EF%BC%9F/>
[183] <https://github.com/Z-Xiong/rPPG-Trends/blob/main/export.bib>
[184] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9601911/>
[185] <https://www.mdpi.com/2076-3417/14/20/9551>
[186] <https://ar5iv.labs.arxiv.org/html/2202.04101v3>
[187] <https://www.semanticscholar.org/paper/ReViSe%3A-Remote-Vital-Signs-Measurement-Using-Camera-Qiao-Ayesha/86c9717390297e06865855f6f6c72d430cf74c1b>
[188] <https://arxiv.org/html/2404.05003>
[189] <https://doi.org/10.1109/tim.2023.3303504>
[190] <https://www.iris.unicampus.it/retrieve/94cc756a-9a2a-4e96-a289-4bd4e7d7b4af/20.500.12610-70063.pdf>
[191] <https://doi.org/10.1109/icaect49130.2021.9392503>
[192] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9269826/>
[193] <https://dl.acm.org/doi/10.1109/TPAMI.2023.3298650>
[194] <https://doi.org/10.1609/aaai.v37i1.25217>
[195] <https://www.sciencedirect.com/science/article/abs/pii/S0208521623000736>
[196] <https://link.springer.com/article/10.1007/s12652-023-04607-8>
[197] <https://www.semanticscholar.org/paper/Face-video-based-touchless-blood-pressure-and-heart-Jain-Deb/59f42a3895b69bdcf91615c044292098e7f37b7e>
[198] <https://doi.org/10.3390/bioengineering10070851>
[199] <https://doi.org/10.1109/tim.2020.2984168>
[200] <https://doi.org/10.1109/issc59246.2023.10162125>
[201] <https://mdpi-res.com/d_attachment/sensors/sensors-22-04974/article_deploy/sensors-22-04974-v3.pdf?version=1657267469>
[202] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9735266/>
[203] <https://cameravitals.github.io/datasets.html>
[204] <https://sites.google.com/view/ybenezeth/ubfcrppg>
[205] <https://github.com/ubicomplab/rPPG-Toolbox>
[206] <https://www.mdpi.com/2076-3417/10/23/8630>
[207] <https://oulurepo.oulu.fi/bitstream/10024/29574/1/nbnfi-fe2021120959958.pdf>
[208] <https://arxiv.org/pdf/2104.02260v2.pdf>
[209] <https://openaccess.thecvf.com/content/CVPR2024W/CVPM/papers/Zhao_Toward_Motion_Robustness_A_Masked_Attention_Regularization_Framework_in_Remote_CVPRW_2024_paper.pdf>
[210] <https://openaccess.thecvf.com/content_cvpr_2016/papers/Tulyakov_Self-Adaptive_Matrix_Completion_CVPR_2016_paper.pdf>
[211] <https://github.com/AnonymousCodeSubmission/Benefit_of_Distraction>
[212] <https://www.frontiersin.org/journals/physiology/articles/10.3389/fphys.2023.1296277/full>
[213] <https://www.cjig.cn/zh/article/doi/10.11834/jig.200314/>
[214] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12944147/>
[215] <https://pi.cs.tsinghua.edu.cn/lab/people/YuntaoWang/zh/projects/facephys/>
[216] <https://arxiv.org/pdf/2302.03840v1>
[217] <https://link.springer.com/article/10.1007/s00607-021-00937-7>
[218] <http://arxiv.org/abs/2107.13193v2>
[219] <https://codewithpapers.app/dataset/mmse-hr>
[220] <https://vipl.ict.ac.cn/en/resources/databases/201811/t20181129_32716.html>
[221] <https://github.com/HanHuCAS/rPPG-HeartRate>
[222] <https://thesai.org/Downloads/Volume13No5/Paper_46-Non_contact_Facial_based_Vital_Sign_Estimation.pdf>
[223] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8895203/>
[224] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6431353/>
[225] <https://openaccess.thecvf.com/content/CVPR2023W/CVPM/papers/Hansen_Real-Time_Estimation_of_Heart_Rate_in_Situations_Characterized_by_Dynamic_CVPRW_2023_paper.pdf>
[226] <https://mdpi-res.com/d_attachment/sensors/sensors-21-08357/article_deploy/sensors-21-08357-v2.pdf?version=1639621329>
[227] <https://doi.org/10.3390/app13148482>
[228] <https://doi.org/10.1016/j.heliyon.2024.e26007>
[229] <https://www.jmis.org/archive/view_article?pid=jmis-8-1-1>
[230] <https://queensu.scholaris.ca/items/557a63cd-6895-40d9-904a-fb6f073abfb5>
[231] <https://doi.org/10.7717/peerj.5859/table-1>
[232] <https://renchengsong.github.io/papers/rPPG_review.pdf>
[233] <https://www.mdpi.com/1424-8220/23/2/737>
[234] <https://arxiv.org/html/2208.04947>
[235] <https://oulurepo.oulu.fi/bitstream/handle/10024/44705/nbnfi-fe2023041135743.pdf?isAllowed=y&sequence=1>
[236] <https://doi.org/10.48550/arxiv.1810.04927>
[237] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8704576/>
[238] <http://arxiv.org/abs/2306.01141v1>
[239] <https://ar5iv.labs.arxiv.org/html/2301.12943>
[240] <https://www.mdpi.com/1424-8220/22/7/2539>
[241] <https://arxiv.org/pdf/2310.15043v2.pdf>
[242] <https://mdpi-res.com/d_attachment/sensors/sensors-23-06079/article_deploy/sensors-23-06079.pdf?version=1688202185>
[243] <https://pubmed.ncbi.nlm.nih.gov/35603304/>
[244] <https://doi.org/10.1007/s12652-021-03635-6>
[245] <https://ar5iv.labs.arxiv.org/html/2211.16922>
[246] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10376629/>
[247] <https://doi.org/10.1101/2023.04.02.23288057>
[248] <https://ar5iv.labs.arxiv.org/html/2106.02669>
[249] <https://doi.org/10.3390/electronics12183771>
[250] <https://www.cnblogs.com/wujianming-110117/p/12625462.html>
[251] <https://doi.org/10.1088/1361-6579/ad1458>
[252] <https://doi.org/10.1117/1.jbo.26.2.022707>
[253] <https://iris.santannapisa.it/retrieve/c9745885-898f-4c80-8f52-d4ee71c1686d/E-Health_monitoring_using_camera_Measurement_of_vital_parameters_in_a_noisy_environment.pdf>
[254] <https://link.springer.com/content/pdf/10.1007/s10877-021-00734-9.pdf?error=cookies_not_supported&code=5873c333-b729-4cda-8c2d-8d0be104fd20>
[255] <https://doi.org/10.1155/2021/9995871>
[256] <https://doi.org/10.1109/icecet58911.2023.10389182>
[257] <http://arxiv.org/abs/2106.06007v1>
[258] <https://oulurepo.oulu.fi/bitstream/handle/10024/45255/nbnfi-fe2023040334642.pdf?isAllowed=y&sequence=1>
[259] <https://www.mdpi.com/1424-8220/22/13/4690>
[260] <https://doi.org/10.3390/s21248357>
[261] <https://arxiv.org/pdf/2208.09916>
[262] <https://arxiv.org/abs/2206.08748>
[263] <https://doi.org/10.48550/arxiv.2206.08748>
[264] <https://www.frontiersin.org/journals/bioengineering-and-biotechnology/articles/10.3389/fbioe.2024.1420100/full>
[265] <https://www.mdpi.com/2673-7426/5/1/6>
[266] <https://www.cell.com/iscience/fulltext/S2589-0042(23)01922-3>
[267] <https://arxiv.org/pdf/2206.08748>
[268] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12181896/>
[269] <https://arxiv.org/html/2401.04560v4>
[270] <https://renchengsong.github.io/papers/HR_CNN.pdf>
[271] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9664884/>
[272] <https://arxiv.org/html/2401.04560v1>
[273] <https://www.academia.edu/115521462/Review_on_remote_heart_rate_measurements_using_photoplethysmography>
[274] <https://www.researchgate.net/publication/377408752_Contactless_face_video_based_vital_signs_detection_framework_for_continuous_health_monitoring_using_feature_optimization_and_hybrid_neural_network>
[275] <https://www.mdpi.com/1424-8220/23/13/6079>
[276] <https://www.scholarfeed.org/paper/2206.08748v2>
[277] <http://www.ok.sc.e.titech.ac.jp/res/VitalSensing/remoteIBI/Dataset.html>
[278] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10542939/>
[279] <https://teamofmis.github.io/IHSLab/dataset/ubfc-rppg>
[280] <http://arxiv.org/abs/2206.08748v2>
[281] <https://fugumt.com/fugumt/paper_check/2206.08748v1>
[282] <https://tomesphere.com/paper/2206.08748.md>
[283] <https://export.arxiv.org/pdf/2206.08748v2.pdf>
[284] <https://www.tu-ilmenau.de/en/university/departments/department-of-computer-science-and-automation/profile/institutes-and-groups/institute-of-computer-and-systems-engineering/group-for-neuroinformatics-and-cognitive-robotics/data-sets-code/pulse-rate-detection-dataset-pure>
[285] <https://www.tu-ilmenau.de/universitaet/fakultaeten/fakultaet-informatik-und-automatisierung/profil/institute-und-fachgebiete/institut-fuer-technische-informatik-und-ingenieurinformatik/fachgebiet-neuroinformatik-und-kognitive-robotik/data-sets-code/pulse-rate-detection-dataset-pure>
[286] <https://github.com/THU-CS-PI/MMPD_rPPG_dataset>
[287] <https://search-data.ubfc.fr/ube/FR-18008901306731-2022-05-05_UBFC-Phys-A-Multimodal-Dataset-For.html>
[288] <https://arxiv.org/html/2210.00716v3>
[289] <https://www.idiap.ch/en/dataset/cohface>
[290] <https://mahnob-db.eu/hci-tagging/media/uploads/manual.pdf>
[291] <https://github.com/thuhci/MMPD_rPPG_Dataset>
[292] <https://arxiv.gg/abs/2206.08748>
[293] <https://vipl.ict.ac.cn/resources/databases/201811/t20181129_32716.html>
[294] <https://arxiv.org/abs/2111.12082>
[295] <https://liangli-zhen.github.io/assets/pdf/RePPS_BP.pdf>
[296] <https://www.iiitd.edu.in/noc/wp-content/uploads/2017/11/07813389.pdf>
[297] <https://www.kaggle.com/datasets/mkachuee/noninvasivebp>
[298] <https://doi.org/10.21203/rs.3.rs-9247196/v1>
[299] <https://wearablebp.github.io/standards/>
[300] <https://doi.org/10.1097/01.hjh.0000938916.81752.7f>
[301] <https://doi.org/10.1109/tim.2022.3165827>
[302] <http://dianda.cqvip.com/Qikan/Article/Detail?id=00002FCOL33G7JP0MJDO4JP16JR>
[303] <https://doi.org/10.1097/mbp.0b013e328330d3f8>
[304] <https://pubmed.ncbi.nlm.nih.gov/36733727/>
[305] <https://arxiv.org/html/2203.03634v3>
[306] <https://arxiv.org/html/2412.10679v1>
[307] <https://doi.org/10.1016/j.bspc.2022.103895>
[308] <https://doi.org/10.3390/s23125528>
[309] <https://github.com/GyutaeHwang/phase_shifted_rPPG>
[310] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10906170/>
[311] <https://www.cell.com/heliyon/fulltext/S2405-8440(24)02038-3>
[312] <https://www.medrxiv.org/content/10.1101/2022.03.14.22272354v1.full-text>
[313] <https://www.mdpi.com/2075-4426/13/1/9>
[314] <https://doi.org/10.1364/boe.473166>
[315] <https://link.springer.com/article/10.1007/s10015-020-00622-6?code=afeb63f7-094b-45ce-baf9-4e71ea604f5b&error=cookies_not_supported>
[316] <https://arxiv.org/html/2401.04560v3>
[317] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9234172/>
[318] <https://www.frontiersin.org/journals/digital-health/articles/10.3389/fdgth.2025.1511667/full>
[319] <https://wwwn.cdc.gov/nchs/data/nhanes/public/2021/manuals/2021-BloodPressureProcedures-508.pdf>
[320] <https://doi.org/10.1101/2022.03.14.22272354>
[321] <https://panoptic.ai/research/Remote%20Blood%20Pressure%20Estimation%20from%20Facial%20Videos%20Using%20Transfer%20Learning%20Leveraging%20PPG%20to%20rPPG%20Conversion.pdf>
[322] <https://mhealth.jmir.org/2023/1/e44147>
[323] <https://arxiv.org/pdf/2104.09313v1.pdf>
[324] <https://research-management.mq.edu.au/ws/portalfiles/portal/230779062/Publisher_version_open_access_.pdf>
[325] <https://arxiv.org/html/2503.03783v2>
[326] <https://www.alphaxiv.org/abs/2206.08748>
[327] <https://sah.borca.ai/papers/261600097>
[328] <https://ar5iv.labs.arxiv.org/html/2208.09916>
[329] <https://vhil.stanford.edu/sites/g/files/sbiybj29011/files/media/file/bailenson-evoked-emotion.pdf>
[330] <https://www.heart.org/en/health-topics/high-blood-pressure/understanding-blood-pressure-readings>
[331] <https://www.mayoclinic.org/diseases-conditions/high-blood-pressure/multimedia/how-to-measure-blood-pressure/vid-20084748>
[332] <https://www.healthline.com/health/blood-pressure-chart>
[333] <https://www.khanacademy.org/science/health-and-medicine/circulatory-system-diseases/hypertension/v/what-is-hypertension>
[334] <https://www.nature.com/articles/s41746-025-01814-9>
[335] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11298756/>
[336] <https://www.emergentmind.com/papers/2401.04560>
[337] <https://mdpi-res.com/d_attachment/sensors/sensors-23-02963/article_deploy/sensors-23-02963.pdf?version=1678349986>
[338] <https://www.frontiersin.org/journals/cardiovascular-medicine/articles/10.3389/fcvm.2022.1001878/full>
[339] <https://ieeexplore.ieee.org/document/10155494>
[340] <https://doi.org/10.1109/access.2020.2965082>
[341] <https://www.mdpi.com/2079-9292/12/18/3771>
[342] <https://github.com/thuhci/SUMS/>
[343] <https://magazine.medlineplus.gov/article/getting-an-accurate-read-on-pulse-oximeters>
[344] <https://welltory.com/blog/blood-oxygen-measuring>
[345] <https://researchportal.hkust.edu.hk/en/publications/contactless-blood-oxygen-saturation-estimation-from-facial-videos/>
[346] <https://opencriticalcare.org/faq/how-to-interpret-open-oximetry-testing-results-on-the-device-data-page/>
[347] <https://www.fda.gov/media/176236/download>
[348] <https://doi.org/10.3390/s22134974>
[349] <https://doi.org/10.1109/iscc50000.2020.9219718>
[350] <https://doi.org/10.3390/info14060301>
[351] <https://dlnext.acm.org/doi/10.1016/j.dsp.2023.104288>
[352] <https://doi.org/10.21203/rs.3.rs-3588812/v1>
[353] <https://www.ubmi.fekt.vut.cz/en/monitoring-heart-rate-blood-oxygen-saturation-and-blood-pressure-using-smartphone>
[354] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10712673/>
[355] <https://doi.org/10.1109/jtehm.2023.3318643>
[356] <https://doi.org/10.1109/icassp48485.2024.10446435>
[357] <https://mdpi-res.com/d_attachment/sensors/sensors-23-00737/article_deploy/sensors-23-00737-v2.pdf?version=1673312402>
[358] <https://doi.org/10.3390/bioengineering11030251>
[359] <https://www.tmrjournals.com/public/articleSUB/20231008/2bc870cdb5f7f6f30c7d3232856944ba.pdf>
[360] <https://doi.org/10.1109/jsen.2023.3284196>
[361] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7984770/>
[362] <https://doi.org/10.48550/arxiv.2310.15388>
[363] <https://doi.org/10.1364/boe.471332>
[364] <https://research.tue.nl/en/publications/contactless-sposub2sub-with-an-rgb-camera-experimental-proof-of-c/>
[365] <https://www.nature.com/articles/s41597-026-07310-3>
[366] <https://doi.org/10.1109/tim.2023.3306832>
[367] <https://doi.org/10.3390/s23020737>
[368] <https://doi.org/10.1109/jbhi.2023.3236631>
[369] <https://www.scribd.com/document/844883633/A-Multi-Channel-Ratio-of-Ratios-Method-for-Noncont>
[370] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10968547/>
[371] <https://link.springer.com/chapter/10.1007/978-3-031-84158-3_8>
[372] <https://oa.upm.es/88994/1/10277349.pdf>
[373] <https://www.ieda.ust.hk/dfaculty/so/pdf/Cheng-et-al-2024-SPO2.pdf>
[374] <https://www.mdpi.com/2078-2489/14/6/301>
[375] <https://doi.org/10.14569/ijacsa.2022.0130546>
[376] <https://mdpi-res.com/d_attachment/bioengineering/bioengineering-10-00524/article_deploy/bioengineering-10-00524.pdf?version=1682495950>
[377] <https://arxiv.org/html/2503.01699v1>
[378] <http://www.yndxxb.ynu.edu.cn/yndxxbzrkxb/cn/article/pdf/preview/10.7540/j.ynu.20260055.pdf>
[379] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10163568/>
[380] <https://doi.org/10.1101/2023.01.14.23284548>
[381] <https://www.ieda.ust.hk/dfaculty/so/pdf/Lam-et-al-2025-Annals-EM.pdf>
[382] <https://dare-lab.com/images/publications/Mobile%20robotic%20platform%20for%20contactless%20vital%20sign%20monitoring.pdf>
[383] <https://www.mdpi.com/2306-5354/11/3/251>
[384] <https://arxiv.org/pdf/2005.11101v1.pdf>
[385] <https://link.springer.com/content/pdf/10.1007/s12652-021-03635-6.pdf?error=cookies_not_supported&code=050dab7e-88dd-4fc5-9ec1-0c3d94e3b541>
[386] <https://circadify.com/see-research>
[387] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10414079/>
[388] <https://www.nature.com/articles/s41746-023-00973-x/tables/1>
[389] <https://www.mdpi.com/3042-7886/2/2/3>
[390] <https://digituma.uma.pt/bitstreams/054fe1b9-c70a-4d49-8109-deffc7339e33/download>
[391] <https://doi.org/10.48550/arxiv.1709.00962>
[392] <https://www.emergentmind.com/papers/2206.08748>
[393] <https://scixplorer.org/abs/2022arXiv220608748Q/abstract>
[394] <https://www.mdpi.com/1424-8220/22/11/4097>
[395] <https://doi.org/10.3390/s21206764>
[396] <https://www.nature.com/articles/s41746-023-00973-x>
[397] <https://shen.ai/blog/what-is-rppg>
[398] <https://doi.org/10.1109/iccvw54120.2021.00310>
[399] <https://doi.org/10.1109/taffc.2021.3056960>
[400] <https://www.frontiersin.org/journals/bioengineering-and-biotechnology/articles/10.3389/fbioe.2018.00033/full>
[401] <https://raw.githubusercontent.com/KegangWangCCNU/PICS/main/PhysBench.pdf>
[402] <https://www.nature.com/articles/s41746-022-00592-y>
[403] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8896412/>
[404] <https://www.kaggle.com/datasets/jacktangthu/mmpd-rppg>
[405] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11955325/>
[406] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12297079/>
[407] <https://huggingface.co/datasets/pjtoye/VitalVideos-Europe-1>
[408] <https://arxiv.org/html/2506.21855>
[409] <https://scanner.vitalhealthglobal.com/science>
[410] <https://arxiv.org/html/2602.23771v1>
[411] <https://arxiv.org/html/2507.06080v2>
[412] <https://openaccess.thecvf.com/content_cvpr_2014/papers/Li_Remote_Heart_Rate_2014_CVPR_paper.pdf>
[413] <https://www.semanticscholar.org/paper/MMPD%3A-Multi-Domain-Mobile-Video-Physiology-Dataset-Tang-Chen/a4e3d1a78052b2fbecdd073d139d15e0dce7ba4e>
[414] <https://www.alphaxiv.org/zh/abs/2403.06947>
[415] <https://openaccess.thecvf.com/content/ICCV2025W/CVPM/papers/Toye_VitalVideos-Worldwide_A_large_and_diverse_rPPG_dataset_with_rich_ground_ICCVW_2025_paper.pdf>
[416] <https://www.nature.com/articles/s41746-025-01814-9/tables/1>
[417] <https://europepmc.org/article/pmc/pmc10721846>
[418] <https://doi.org/10.11834/jig.230428>
[419] <https://link.springer.com/article/10.1007/s10916-026-02412-2>
[420] <https://liangli-zhen.github.io/assets/pdf/RePPS_HR.pdf>
[421] <https://www.mdpi.com/1424-8220/25/15/4792>
[422] <https://doi.org/10.3390/bioengineering11020113>
[423] <https://ar5iv.labs.arxiv.org/html/2402.02224>
[424] <https://github.com/Z-Xiong/rPPG-Trends>
[425] <https://vipl.ict.ac.cn/en/resources/>
[426] <https://explore.openaire.eu/search/dataset?pid=10.34777%2Fff3f-ba56>
[427] <https://github.com/KegangWangCCNU/PhysBench_Archived>
[428] <https://rsipe.wordpress.com/2019/04/16/vipl-hr%EF%BC%9A%E7%94%A8%E4%BA%8E%E4%BB%8E%E8%BE%83%E5%B0%91%E7%BA%A6%E6%9D%9F%E7%9A%84%E9%9D%A2%E9%83%A8%E8%A7%86%E9%A2%91%E8%BF%9B%E8%A1%8C%E8%84%89%E5%86%B2%E4%BC%B0%E8%AE%A1%E7%9A%84%E5%A4%9A/>
[429] <https://arxiv.org/html/2302.03840v2>
[430] <https://link.springer.com/article/10.1186/s12938-025-01405-5>
[431] <https://arxiv.org/html/2311.05371v2>
[432] <https://ube.hal.science/hal-03239520>
[433] <https://arxiv.org/abs/2302.03840>
[434] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12491395/>
[435] <https://www.nature.com/articles/s41746-026-02715-1>
[436] <https://link.springer.com/article/10.1007/s11042-023-16794-9>
[437] <https://chatppg.com/research/datasets/ubfc-phys>
[438] <https://export.arxiv.org/pdf/2302.03840v2.pdf>
[439] <https://archive-ouverte.unige.ch/unige:47406>
