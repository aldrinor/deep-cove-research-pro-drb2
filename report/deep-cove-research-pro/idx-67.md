# m⁶A RNA修饰与免疫调控：核心蛋白、细胞机制与总结表

**核心结论是情境依赖。** N⁶-甲基腺苷（N6-methyladenosine，m⁶A）通过改变RNA的翻译、稳定性、加工和定位，调节免疫细胞功能。Writers负责写入，Erasers负责擦除，Readers负责识别并连接下游效应。m⁶A并不是统一的“免疫增强”或“免疫抑制”标记；最终方向取决于被修饰的RNA、读取蛋白及细胞状态。[1]

**四类细胞已有明确机制。** NK细胞中的METTL3支持IL-15反应，而FTO通过维持SOCS负反馈限制细胞毒性。DC中的METTL3促进激活成熟，但YTHDF1又可因增加抗原降解而限制交叉呈递。巨噬细胞与T细胞的结果更依赖刺激、亚群和疾病环境，不能仅凭某个调控蛋白升高或降低预测功能。

**本文按三个问题展开。** 第一部分说明核心蛋白的功能和互作；第二部分逐一建立四类细胞的分子链条；第三部分提供指定四列的详细总结表。资料范围截至2026年9月13日。先用下表概括主要答案，再展开各条机制。

| 免疫细胞类型 | 关键m⁶A调控蛋白 | 调控目标与机制 | 对细胞功能的最终影响 |
|---|---|---|---|
| NK细胞 | METTL3、FTO、YTHDF2 | Ptpn11/SHP-2、SOCS及效应相关RNA周转 | 分别调节IL-15反应、成熟与杀伤能力 |
| 树突状细胞（DC） | METTL3、YTHDF1、YTHDF2 | 共刺激分子翻译、抗原降解、lnc-Dpf3周转 | 分别影响成熟、交叉呈递和迁移 |
| 巨噬细胞 | METTL3、FTO、ALKBH5及多种Readers | STAT1、IRAKM、SPRED2与代谢转录本 | 按模型改变极化、炎症及抗肿瘤功能 |
| T细胞 | METTL3/METTL14、ALKBH5、FTO、YTHDF2 | SOCS、Tcf7、Ifng/Cxcl2、Fas等 | 调节稳态、分化、存活及肿瘤免疫 |

表中NK、DC、巨噬细胞和T细胞的代表性机制，分别来自细胞遗传干预、RNA命运分析及功能实验。[2][3][4][5]

## 第一部分：m⁶A核心调控蛋白及其相互作用

**先区分修饰与效应。** m⁶A是RNA腺苷碱基外侧第6位氮原子上的甲基化，不改变RNA的碱基序列。下文重点讨论信使RNA（messenger RNA，mRNA），并纳入与免疫机制直接相关的长链非编码RNA（long non-coding RNA，lncRNA）。写入或去除标记之后，RNA仍需通过结合蛋白及效应复合体，才产生具体功能。[6]

**三类蛋白分工不同。** “写入蛋白”既包括真正催化甲基转移的酶，也包括定位、组装和底物招募因子。“读取蛋白”则包括直接识别甲基化碱基的蛋白，以及感知修饰相关RNA结构变化的加工因子。不能把同一类别中的所有成员都视为具有相同的酶活或识别方式。[7]

| 类别 | 主要成员 | 核心任务 | 主要作用环节 |
|---|---|---|---|
| Writers（写入蛋白） | METTL3、METTL14、WTAP、VIRMA、RBM15/15B等 | 催化或组织m⁶A沉积 | 底物选择、定位、甲基转移 |
| Erasers（擦除蛋白） | FTO、ALKBH5 | 去除相关甲基修饰 | 修饰状态及核质分布 |
| Readers（读取蛋白） | YTH、IGF2BP、HNRNP相关成员 | 识别修饰并连接效应装置 | 剪接、输出、翻译、稳定或降解 |

### Writers（写入蛋白）

**催化核心与招募模块分离。** 哺乳动物常见的mRNA写入体系，以METTL3–METTL14异源二聚体为核心。WTAP、VIRMA、RBM15/RBM15B、ZC3H13和HAKAI等辅助成员，决定复合体如何接触RNA。人源复合体冷冻电镜研究进一步显示，WTAP与VIRMA构成重要调控支架，ZC3H13参与构象和底物结合调节。[8]

| 蛋白 | 具体功能 | 作用对象或过程 | 代表性互作及性质 |
|---|---|---|---|
| METTL3 | 主要催化亚基 | 结合SAM，催化RNA m⁶A形成 | METTL14、WTAP；ADAP直接结合 |
| METTL14 | RNA结合和变构支持 | 稳定催化核心及底物结合 | METTL3；WTAP–VIRMA模块 |
| WTAP | 调控支架和核内定位 | 将核心复合体定位至核斑 | METTL3、METTL14、VIRMA等 |
| VIRMA/KIAA1429 | 区域选择与支架组装 | 偏向终止密码子附近及3′UTR | WTAP、ZC3H13；CPSF因子关联 |
| RBM15/RBM15B | RNA底物招募 | 结合U-rich区域，导向邻近位点 | 经WTAP连接写入复合体 |
| ZC3H13 | 核定位及复合体调节 | 支持调控模块核内保留和RNA结合 | VIRMA直接结合；WTAP模块 |
| HAKAI/CBLL1 | 复合体稳定性调节 | 维持辅助模块及细胞内m⁶A水平 | WTAP、VIRMA、ZC3H13复合体 |

上述互作分别涉及结构性直接接触、共同复合体关系及RNA依赖关联，不能全部解释为两两直接结合。[8][9]

**METTL3承担催化。** 甲基转移酶样蛋白3（methyltransferase-like 3，METTL3）结合甲基供体S-腺苷甲硫氨酸（S-adenosylmethionine，SAM），将甲基转移到RNA腺苷上。结构和生化研究支持：在METTL3–METTL14核心中，METTL3承担主要催化作用。其作用对象包括编码RNA及部分非编码RNA。[9]

**METTL3的互作决定定位。** METTL3与METTL14形成稳定异源二聚体，并通过WTAP连接调控模块。人源复合体研究支持，METTL3的N端区域参与WTAP结合，使催化核心与辅助模块组装。这里的互作不仅是“共同出现”，而是有结构、交联质谱和蛋白拉下实验支持的组装关系。[8]

**METTL3还受特异伙伴调节。** 在巨噬细胞炎症研究中，黏附与脱颗粒促进适配蛋白ADAP，又称FYB，与METTL3直接结合。ADAP的341–450位氨基酸，以及METTL3的N端1–389位残基，对该互作重要。该关系连接了ADAP状态与Spry1 mRNA甲基化，体现细胞特异性伙伴对Writer输出的调节。[10]

**METTL14主要支持底物识别。** 甲基转移酶样蛋白14（methyltransferase-like 14，METTL14）不是与METTL3等价的主要催化酶。它稳定核心结构，提供RNA结合支持，并促进底物与METTL3形成有效结合。因此，METTL14缺失也会明显影响靶RNA甲基化，不能因其非主要催化身份而将其视为可有可无的配件。[9]

**METTL14互作保护RNA写入。** 除METTL3外，METTL14还联系WTAP–VIRMA模块。Yan等的体外研究显示，METTL14的富精氨酸/甘氨酸区域可结合RNA和双链DNA。WTAP–VIRMA与该区域直接相互作用，可限制双链DNA竞争结合，从而维持RNA甲基化活性。这说明辅助因子也能调节底物竞争，而非只负责运输。[11]

**WTAP组织核内写入。** Wilms肿瘤1相关蛋白（Wilms tumor 1-associated protein，WTAP）是调控亚基，不独立承担METTL3式的甲基转移反应。它帮助METTL3–METTL14定位于核斑，即富集RNA加工相关因子的核内结构。WTAP因此影响写入复合体接触哪些新生或加工中的转录本。[9]

**WTAP是重要组装节点。** WTAP与METTL3、METTL14相联系，并与VIRMA形成调控支架。RBM15/RBM15B通过WTAP依赖的方式连接写入体系；ZC3H13和HAKAI也参与相关复合体。描述这些关系时，应区分已解析的直接界面与经共同复合体建立的联系。[8]

**VIRMA影响沉积区域。** VIRMA，即vir-like m⁶A methyltransferase-associated protein，亦称KIAA1429。它促进m⁶A在终止密码子附近及3′非翻译区（3′ untranslated region，3′UTR）的优先沉积。这里是分布倾向，而不是“所有VIRMA靶位点只能位于3′UTR”。[7]

**VIRMA兼具支架与RNA联系。** VIRMA直接结合WTAP和ZC3H13，参与调控模块构象。它还与多聚腺苷酸化切割相关因子CPSF5、CPSF6存在RNA依赖关联，连接3′端加工与修饰分布。RNA依赖关联不等于纯化蛋白之间必然直接结合，这是理解互作网络时的重要区别。[8]

**RBM15家族负责底物招募。** RNA结合基序蛋白15及其旁系同源蛋白15B（RNA-binding motif protein 15/15B，RBM15/RBM15B）倾向结合富含尿嘧啶的U-rich区域。它们以WTAP依赖方式，将写入复合体导向邻近的部分DRACH基序。DRACH中，D代表A/G/U，R代表A/G，H代表A/C/U，中央A是候选修饰位点。[9]

**招募并非覆盖所有位点。** RBM15/RBM15B耗竭可减少poly(A) RNA及lncRNA XIST上的m⁶A，支持其真实功能。其关键蛋白联系是WTAP及METTL3–METTL14体系，但不能据此认定它们独自决定全部m⁶A位点。基序是否可接近，以及其他辅助因子的参与，同样影响沉积。[9]

可确定的互作关系是：RBM15/RBM15B以WTAP依赖方式连接METTL3–METTL14写入复合体，并结合邻近DRACH位点的U-rich区域，将复合体导向部分RNA位点；耗竭二者会减少poly(A) RNA和lncRNA XIST的m⁶A。

**ZC3H13维持调控模块。** CCCH型锌指蛋白13（zinc finger CCCH-type containing 13，ZC3H13）促进WTAP、VIRMA和HAKAI的核定位。人源结构研究还显示，其C端与VIRMA直接接触，改变调控模块构象，并支持RNA结合及写入活性。该成员因此同时涉及细胞定位和复合体结构功能。[8]

**HAKAI不是另一种催化核心。** HAKAI又称CBLL1，是E3泛素连接酶相关蛋白，也是Writer辅助模块成员。其主要相关作用是维持复合体组分稳定，而不是替代METTL3催化m⁶A。部分果蝇研究显示，其E3连接酶催化活性并非维持m⁶A调控所必需；这一区分有助于避免把蛋白名称中的“酶”直接等同于甲基转移功能。[9]

**核心复合体并非全部Writer。** METTL16具有独立底物谱，可作用于U6小核RNA及MAT2A转录本，参与SAM稳态调节。因此，上述目录主要说明常见mRNA免疫机制中的METTL3体系，不应将其称为所有RNA m⁶A写入酶的完整集合。[12]

**本类结论。** Writers的免疫效应既由催化能力决定，也由WTAP、VIRMA和RNA招募因子决定的靶标选择所塑造。

### Erasers（擦除蛋白）

**两种主要酶底物不同。** FTO与ALKBH5都属于依赖二价铁和α-酮戊二酸（α-ketoglutarate，α-KG）的氧化去甲基化酶。二者的底物范围、亚细胞定位及招募伙伴不同，因此不能把它们视为功能完全重叠的“反向METTL3”。[13]

**FTO具有较宽底物谱。** 脂肪量和肥胖相关蛋白（fat mass and obesity-associated protein，FTO）可去除RNA内部m⁶A，也可作用于N⁶,2′-O-二甲基腺苷（N6,2′-O-dimethyladenosine，m⁶Am）。其底物还涉及部分小核RNA和转运RNA修饰。核内与胞质定位会改变它实际接触的底物，故FTO干预的结果不能全部归因于内部mRNA m⁶A。[13]

**FTO通过氧化恢复腺苷。** 在m⁶A去甲基化过程中，FTO可形成N⁶-羟甲基腺苷和N⁶-甲酰腺苷等氧化中间体，最终恢复RNA中的未甲基化腺苷。其作用不是切除整颗腺苷，也不是改变RNA编码序列。免疫实例包括NK细胞中SOCS转录本稳定性调节，以及CD8⁺ T细胞中的Fas调节。[14]

**FTO互作控制底物可及性。** 核输出蛋白2（Exportin 2，XPO2）是FTO的结合伙伴，参与其核质穿梭。FTO还被报道与转录因子FOXO3a相互作用，并增强后者活性；这一结果来自胶质瘤环境。前一互作主要影响定位，后一互作属于特定疾病模型中的蛋白功能联系。[13]

**FTO也连接RNA加工。** FTO去除剪接位点邻近m⁶A，可改变剪接因子对RNA的结合，影响可变剪接。另在DNA病毒感染研究中，异质性核核糖核蛋白HNRNPA2B1与FTO的关联具有感染状态依赖性。这些结果说明，FTO的作用不仅是改变RNA寿命，也可能改变加工和运输。[15][16]

**ALKBH5主要调节m⁶A。** AlkB同源蛋白5（AlkB homolog 5，ALKBH5）相对偏向m⁶A底物。其净反应恢复未甲基化腺苷，不表现为FTO式较稳定氧化中间体的积累。ALKBH5可通过改变靶RNA稳定性或核输出，产生不同方向的免疫作用。[13]

**ALKBH5由伙伴选择靶标。** DEAD-box RNA解旋酶46（DEAD-box helicase 46，DDX46）能招募ALKBH5，使其作用于Mavs、Traf3、Traf6等抗病毒转录本。RNA结合蛋白RBM33也被报道能够招募并增强ALKBH5作用；PSPC1相关的乙酰化调控则影响位点募集。它们说明，去甲基化酶接触哪些RNA，受到蛋白网络控制。[17][14]

**同一酶可改变不同过程。** 在病毒感染巨噬细胞中，DDX46–ALKBH5轴主要影响抗病毒RNA核输出。在活化CD4⁺ T细胞中，ALKBH5对Ifng、Cxcl2的作用则表现为提高转录本稳定性和蛋白表达。二者不能统一简写成“ALKBH5稳定所有RNA”或“ALKBH5抑制所有免疫反应”。[17][18]

**本类结论。** Eraser的功能方向应由“具体底物—去甲基化后RNA命运”判断，而不是仅由总m⁶A水平判断。

### Readers（读取蛋白）

**Readers决定标记如何执行。** YTH家族通过保守结构域识别m⁶A，其中的芳香性结合口袋帮助容纳甲基化腺苷。IGF2BP家族则连接部分甲基化RNA与稳定性调控。HNRNP相关成员更多参与核内加工和结构依赖结合，不能与YTH的直接碱基识别方式混为一谈。[6]

**先看胞质YTHDF家族。** YTHDF1、YTHDF2、YTHDF3是三种不同蛋白。下表列出最常用、并与后文免疫案例对应的功能机制。

| 蛋白 | 识别后的代表性功能 | 主要互作或效应伙伴 | 如何改变RNA命运 |
|---|---|---|---|
| YTHDF1 | 增强部分靶mRNA翻译 | eIF3、YTHDF3 | 连接翻译起始装置 |
| YTHDF2 | 促进靶RNA降解 | CNOT1/CCR4–NOT、HRSP12 | 去腺苷酸化或内切途径 |
| YTHDF3 | 协调翻译与降解 | YTHDF1/2、eIF4G2等 | 随伙伴进入不同效应通路 |

这些是代表性机制，不是三个成员永不重叠的固定分工。[19]

**YTHDF1连接翻译起始。** YTHDF1识别m⁶A修饰mRNA后，可通过真核翻译起始因子3（eukaryotic translation initiation factor 3，eIF3）等装置提高翻译效率。YTHDF3也是其协同伙伴。在DC中，相关靶标包括CD40、CD80及溶酶体蛋白酶转录本，因此“促进翻译”既可能增强共刺激，也可能加速抗原降解。[17]

**YTHDF2招募降解装置。** YTHDF2的N端直接结合CNOT1，并招募CCR4–NOT去腺苷酸化复合体，使poly(A)尾缩短并促进RNA周转。另一条通路通过HRSP12相关内切机制执行降解。准确说法是YTHDF2“招募或组织降解”，而不是把YTHDF2本身称为核酸酶。[20][14]

**降解也能增强免疫。** YTHDF2若降解促炎激酶转录本，可能限制炎症；若降解抑制信号或破坏效应状态的转录本，则可能支持免疫功能。后文NK、巨噬细胞和肿瘤内Treg的不同表型，正是由靶RNA的生物学角色不同造成，不能仅凭“促进降解”预测最终结果。

**YTHDF3具有伙伴依赖性。** YTHDF3可与YTHDF1协同促进翻译，也可与YTHDF2协同促进降解。它还与eIF4G2介导的翻译过程、PAN2–PAN3去腺苷酸化装置及核糖体组分存在功能联系。应将直接互作、同一复合体关联和功能协同分别理解，而不是把所有伙伴都画成相同性质的直接结合边。[21][19]

**家族冗余需要保留。** 除传统的“YTHDF1偏翻译、YTHDF2偏降解”模型外，多项研究支持YTHDF旁系同源蛋白在RNA降解中的重叠作用。二者并不要求否定特定免疫靶标的翻译实验。合理判断是：家族层面存在冗余，而具体细胞、靶RNA和伙伴可产生分工；单个Reader的功能应由靶标实验决定。[12]

**YTHDC1主要处理核内RNA。** YTH结构域蛋白1（YTH domain-containing protein 1，YTHDC1）参与可变剪接和核输出。它结合剪接因子SRSF3，促进部分外显子包含，同时拮抗SRSF10在相应RNA上的作用。通过SRSF3及核输出因子NXF1相关适配体系，YTHDC1还可促进部分m⁶A转录本输出。[17][22]

**YTHDC1也可连接核内降解。** 共免疫沉淀研究将YTHDC1与ZCCHC8联系起来。ZCCHC8是核RNA外切体靶向复合体（nuclear exosome targeting complex，NEXT）的组分，可将部分核内RNA送入降解途径。这里的exosome是RNA降解复合体，不是细胞外囊泡意义上的“外泌体”。[23]

**核内读取不是单向清除。** YTHDC1还可参与RNA凝聚体和保护性调节。不同细胞中的结果显示，核内Reader既可能促进清除，也可能保护特定转录本或支持其加工输出。因此，不能用“核内Reader”这一定位标签代替具体RNA命运的判断。[23]

**YTHDC2兼具读取与解旋。** YTH结构域蛋白2（YTH domain-containing protein 2，YTHDC2）含m⁶A识别结构域，也具有RNA诱导的ATP酶及3′→5′ RNA解旋酶活性。它可促进结构化mRNA的翻译，并在一些体系中降低靶RNA丰度。因此，YTHDC2不能简单归为纯粹“稳定型”或“降解型”Reader。[24]

**YTHDC2的直接伙伴明确。** 其锚蛋白重复结构域可与5′→3′外切核酸酶XRN1形成不依赖RNA的互作。该证据支持它连接RNA结构处理与降解。减数分裂相关蛋白MEIOC也是YTHDC2伙伴，但这一关系主要来自小鼠睾丸体系，属于生殖细胞特异复合体语境。[25][24]

**识别能力与功能依赖要分开。** 重组人YTHDC2的YTH结构域，对含m⁶A RNA的解离常数为8.9 μM，对相同序列未修饰RNA为61.6 μM。芳香结合口袋W1360A突变削弱这种选择性。另一方面，后续生殖系研究显示，部分生理功能更依赖解旋酶活性，而不依赖m⁶A结合口袋，说明“能结合m⁶A”不等于全部功能均由m⁶A驱动。[24][26]

**解旋可以促进翻译延伸。** 一项培养细胞研究发现，编码区（coding sequence，CDS）中的m⁶A可通过YTHDC2帮助解除RNA二级结构，提高翻译延伸效率。野生型YTHDC2能恢复相关报告读数，解旋酶失活E332Q突变体则不能。这提供了“识别—解旋—翻译”的机制依据，但并不自动指定其在每种免疫细胞中的靶RNA。[27]

**IGF2BP家族偏向稳定化。** 胰岛素样生长因子2 mRNA结合蛋白家族（insulin-like growth factor 2 mRNA-binding proteins，IGF2BPs）包括IGF2BP1、IGF2BP2和IGF2BP3。它们通过KH相关RNA结合结构域识别部分m⁶A相关底物，增强RNA稳定性、储存或表达。其作用并非覆盖所有m⁶A位点，而受到序列和结构环境影响。[28]

**三名成员各有研究实例。** IGF2BP1是该稳定化体系的重要成员；IGF2BP2在巨噬细胞中可稳定TSC1、PPARγ及特定环境中的Spry1；IGF2BP3在活化CD8⁺ T细胞中可稳定Fas。家族层面报道的稳定协同蛋白包括ELAVL1，又称HuR，以及MATR3；这些是蛋白伙伴，而TSC1、PPARγ和Fas在上述机制中首先是靶转录本。[6][29]

**稳定与降解形成对照。** IGF2BP和YTHDF相关降解途径，能够把同一类化学标记导向相反RNA寿命结果。这并不意味着任意靶RNA上都存在已经证明的直接竞争，而是说明Reader身份是推断RNA命运的必要信息。看到m⁶A富集，不能直接写成“该mRNA更稳定”或“更容易降解”。[23]

**HNRNPA2B1连接核内加工。** 异质性核核糖核蛋白A2/B1（heterogeneous nuclear ribonucleoprotein A2/B1，HNRNPA2B1）参与m⁶A相关RNA加工、剪接及初级微RNA处理。其代表性伙伴是微RNA加工因子DGCR8，可促进部分pri-miRNA进入成熟加工过程。它通常被纳入非YTH型Reader体系。[6]

**结构读取不同于芳香笼。** m⁶A可改变局部RNA结构，暴露原本被遮挡的蛋白结合序列，这称为m⁶A结构转换或“m⁶A-switch”。HNRNPC、HNRNPG是该模式的重要实例；HNRNPA2B1相关作用也需结合RNA结构和加工环境解释。不能将这些蛋白一概写成与YTH相同的直接甲基碱基受体。[6]

**感染可重塑Reader伙伴。** 在单纯疱疹病毒1型（herpes simplex virus type 1，HSV-1）感染语境中，HNRNPA2B1与FTO的关联减弱，并参与抗病毒相关RNA的核质转运与翻译调节。由此可见，Reader互作网络本身也会随刺激改变，而不是固定不变的蛋白配对。[16]

**本类结论。** 判断m⁶A功能时，最关键的问题是：哪一个Reader结合哪一条RNA，并招募哪一种效应装置。

**补充证据**

本部分采用三层区分：催化或去修饰作用、同一复合物中的定位/招募作用，以及识别 m⁶A 后产生的 RNA 命运效应。“同一复合物”不等于每个成员之间都已有独立的直接物理结合证据；癌症免疫综述表中的并列或相关性也不等于蛋白互作或因果机制。[114][115]

**Writers（写入蛋白）**

**METTL3–METTL14 核心复合物**

- **METTL3** 是明确的 canonical m⁶A Writer 和催化亚基；它在细胞核内结合 S-adenosylmethionine（SAM），并在转录过程中催化 RNA 腺苷甲基化。其主要复合物伙伴是 **METTL14**：二者形成稳定异二聚体；**WTAP** 则与 METTL3–METTL14 复合物相互作用，帮助其定位于 nuclear speckles 并募集到 mRNA 靶标。因此，METTL14 属于核心复合物中的非催化变构激活因子和 RNA-binding platform，WTAP 属于定位/调控亚基，而不是独立催化亚基。[114][115]

- **METTL3 的 T 细胞证据**来自条件性敲除小鼠研究（综述所引研究发表于 2017 年）：m⁶A 促进 **SOCS1/SOCS3 mRNA** 的诱导性降解，解除其对 **IL-7/STAT5** 信号的抑制，从而促进 T 细胞增殖和分化；后续研究（2018 年）还显示，该类 m⁶A 介导的 SOCS mRNA 降解有助于 **Treg 生成、抑制功能和稳定性**，涉及 IL-2/STAT5 轴。[114]

- **METTL3 的巨噬细胞证据**指向 **STAT1 mRNA**：综述列出的 2019 年研究题名将 METTL3 介导的 STAT1 mRNA 甲基化与 **M1 巨噬细胞极化**联系起来。另有 LPS 刺激模型显示，METTL3 可促进 TLR 信号适配蛋白 **MYD88** 的剪接及多种细胞因子诱导；这属于先天免疫刺激背景下的功能证据，并不应无条件外推到所有巨噬细胞状态。[114][115]

- **METTL3/METTL14 的抗病毒方向具有条件依赖性。**在 HCMV 感染或 dsDNA 处理细胞中，抑制 METTL3 或 METTL14 可使 **IFNβ1 mRNA** 的 m⁶A 减少并趋于稳定，增强 IFN 和 ISG 诱导、抑制病毒传播；相关结果在小鼠中也被报告。另一方面，METTL3/14 介导的 m⁶A 又可促进抗病毒 ISG **IFITM1** 的翻译，且 YTHDF1/DF1 的 m⁶A 依赖性识别进一步提高 IFITM1 表达。因此，Writer 对抗病毒反应的方向取决于靶 RNA 是宿主 IFN 转录本、抗病毒 ISG 还是病毒 RNA。[114]

- **METTL14** 本身缺乏 METTL3 那样的催化功能，但其与 METTL3 的 RNA-binding platform 和 allosteric activator 作用使受体腺苷能够被定位到 METTL3 的催化口袋。其已知复合物关系包括 METTL3–METTL14 核心异二聚体，以及与 WTAP 共同组成的 m⁶A 生成复合物。[114][115]

- **METTL14 的免疫功能**包括：在早期 B 细胞发育中，METTL14 介导的 m⁶A 通过 Reader DF2/YTHDF2 促进 IL-7 诱导的 pro-B 细胞增殖；large-pre-B 到 small-pre-B 的转换则主要依赖 METTL14 介导的转录因子激活，并不依赖 DF1/DF2。另有 T 细胞研究题名显示，T 细胞删除 METTL14 可在小鼠诱发自发性结肠炎，但该片段没有提供其直接 RNA 底物。[114][115]

- 在结直肠癌肿瘤微环境中，**巨噬细胞特异性删除 METTL14** 可推动 CD8⁺ T 细胞向功能失调表型分化，削弱肿瘤清除并促进肿瘤生长；这是巨噬细胞—T 细胞跨细胞因果证据。另一个肿瘤模型显示，肿瘤细胞中 METTL14 缺失可增加细胞毒性肿瘤浸润 CD8⁺ T 细胞，并提高 IFN-γ、CXCL9 和 CXCL10；综述将其机制归于 **YTHDF2 稳定 STAT1 和 IRF1 mRNA**，增强 IFN-γ–STAT1–IRF1 信号。两种 METTL14 缺失模型的细胞来源不同，不能合并为单一方向。[115]

**WTAP、VIRMA 与定位/招募因子**

- **WTAP** 是 METTL3–METTL14 m⁶A methyltransferase 的 regulatory subunit；它与核心复合物的关系是复合物级别的相互作用，主要功能是核内定位、mRNA 靶标招募和催化活性调节。其与 VIRMA、ZC3H13、HAKAI/CBLL1 的关系也主要表现为共同复合物或辅助层级。[114][115]

- 在弥漫大 B 细胞淋巴瘤模型中，WTAP 被报道可增强 **HK2 mRNA** 的 m⁶A 修饰并提高 HK2 表达；综述将该过程置于 **piRNA-30743/WTAP/HK2-m⁶A** 轴中。该证据来自肿瘤细胞模型，不等同于 WTAP 在 NK、DC、巨噬细胞或 T 细胞中的直接因果证据。[114]

- 另一综述表格把 WTAP 与胶质母细胞瘤中的 **CD8⁺ T 细胞、巨噬细胞、髓系 DC 和 TFRC** 联系起来，并另列出 WTAP、巨噬细胞、HSPA7 及 YAP1–LOX 关系；这些是疾病表格中的关联或机制线索，页面没有给出 WTAP 与这些对象的独立直接互作实验，因此不能写成已证实的物理结合。[115]

- **VIRMA/KIAA1429** 是 Writer 复合物组分，具有位置选择功能：它促进 mRNA **3′UTR 和终止密码子附近**的 m⁶A 富集，并与 alternative polyadenylation 相关。癌症综述表把 KIAA1429 描述为可募集 METTL3、METTL14 和 WTAP 的因子；在胃癌条目中，它与 DC、C-type lectin receptors、NOD-like receptors、T-cell receptors、TLR 和 NF-κB pathway 并列，在另一条目中则与 CD8⁺ T 细胞及 TFAP2A/DDR1 相关。后两类资料属于疾病表格关联，未提供指定免疫细胞中的直接 RNA—功能链。[114][115]

- **RBM15** 是 mRNA-binding 和 m⁶A 写入定位因子，不是催化亚基。其关系证据是 **ZC3H13/Flacc 将 RBM15/Spenito 桥接到 WTAP/Fl(2)d m⁶A machinery**；RBM15 还可指定转录组中的 DRACH 位点。早期研究将 RBM15/RBM15B 通过 **XIST m⁶A** 与 X 染色体失活和基因沉默联系起来。[114][115]

- **RBM15B** 与 RBM15 同属写入招募层，卡片支持其参与 XIST m⁶A 和基因沉默，但没有给出 RBM15B 与某一复合物成员的独立直接互作实验。肾透明细胞癌综述表将 RBM15B 与 CD56^bright NK、NK、pDC、肥大细胞及 **CDH13** 联系起来，并列出免疫检查点相关读出；这是统计/疾病关联，不能替代直接机制。[114][115]

- **ZC3H13** 是非催化的核内 Writer 复合物组分。其最具体的蛋白关系是桥接 **RBM15/Spenito 与 WTAP/Fl(2)d**，并促进 ZC3H13–WTAP–VIRMA–HAKAI 复合物的核定位。小鼠胚胎干细胞研究中，METTL3/14 复合物及 WTAP、ZC3H13 被用于催化 ERV mRNA 的 m⁶A；耗竭这些成员会增加 IAP 和 ERVK mRNA。该结果说明复合物能清除或抑制反应性 ERV RNA，但不是四类成熟免疫细胞的直接证据。[114][115]

- ZC3H13 在癌症综述表中与食管鳞癌中的巨噬细胞、胶质母细胞瘤中的髓系细胞/巨噬细胞等相关，但表格没有说明这些并列关系是共现、统计关联还是直接互作。因此，ZC3H13 的 Writer 复合物功能可以确定，免疫细胞特异性功能则应保留为待进一步核实。[115]

- **CBLL1/HAKAI** 是 WTAP 复合物的相关组分，同时是 E3 ubiquitin-protein ligase；所示证据把它定位为参与 m⁶A methylation induction 的辅助因子，而非 METTL3/14 式催化亚基。当前片段没有提供 CBLL1/HAKAI 在 NK、DC、巨噬细胞或 T 细胞中的直接 RNA 靶标、功能读出或独立免疫因果实验。[114]

**Writer 名单的边界**

同一综述还提到 **ZCCHC4** 负责 28S rRNA 的 m⁶A、**METTL5** 在 TRMT112 辅助下修饰 18S rRNA；这些是 rRNA 修饰系统，不能不加说明地并入本节的 mRNA m⁶A 核心 Writer 名单。**METTL16** 仅在所示片段中被作为“另一种酶”提及，并在免疫综述表中作为 m⁶A regulator 出现，但本组证据没有给出足够的直接免疫 RNA—功能链，因此保留为边界候选，而不把它写成与 METTL3/14 同等的核心免疫 Writer。[114][115]

**Erasers（擦除蛋白）**

- 允许来源中明确列出的 canonical m⁶A Erasers 是 **FTO** 和 **ALKBH5**。**FTO** 位于细胞核，可通过 oxidative demethylation 降低 m⁶A；其底物范围还包括 5′ cap 邻近的 **m⁶Am**，因此不能把 FTO 的所有去修饰活动都等同于内部 mRNA m⁶A。PEDV 模型中，FTO depletion 与病毒复制下降相关，但当前片段没有给出 FTO 在 NK、DC、巨噬细胞或 T 细胞中的直接蛋白—RNA—功能链，也没有可靠的 FTO 蛋白伙伴清单；不应据此补推互作。[114][115]

- **ALKBH5** 可去除核内 RNA 上的 m⁶A，并进一步影响核 RNA 输出和 RNA metabolism；相较之下，FTO 的底物谱还涉及 m⁶Am。ALKBH5 在先天免疫刺激中被 **DDX46** 招募到 **TRAF3、TRAF6 和 MAVS mRNA**，去除这些转录本的 m⁶A 后，核输出和翻译下降，最终抑制 IFN 产生；另有证据称 **DDX3 与 ALKBH5 相互作用**。这里的“招募”和“相互作用”是免疫功能/复合物层面的关系，所示片段没有给出足以判定直接物理结合的方法学细节。[114]

- 在感染巨噬细胞中，综述将 ALKBH5–DDX46 关系与抗病毒转录本去甲基化及抗病毒反应联系起来；在 CD4⁺ T 细胞中，2021 年研究题名则把 ALKBH5 与 T 细胞致病性和自身免疫联系起来。后者在当前片段只达到题名层面的支持，没有提供具体 RNA 靶点或救援实验，因此应标为免疫关联而非完整机制链。[115]

**Readers（读取蛋白）**

直接 YTH Readers 包括 **YTHDF1、YTHDF2、YTHDF3、YTHDC1 和 YTHDC2**，均可用 m⁶A 依赖方式结合 mRNA；YTHDF1–3 主要位于细胞质，YTHDC1 主要位于细胞核，YTHDC2 可在细胞核和细胞质之间分布。其 m⁶A 选择性主要来自 YTH-domain 的 tryptophan cage。YTHDF 蛋白还可在含多个 m⁶A 位点的 RNA 促进相分离并参与 stress granule/P-body，但后续研究认为 m⁶A 对 mRNA 是否进入 stress granule 的作用可能很小甚至不存在。[114]

**YTHDF1、YTHDF2 与 YTHDF3**

- **YTHDF1** 的经典功能是促进 m⁶A RNA 翻译；早期模型把它与翻译起始因子 **eIF3** 联系起来，说明 eIF3 更适合作为翻译效应/协作因子，而不是因此被自动归为经典 m⁶A Reader。抗病毒模型中，DF1/YTHDF1 可在 m⁶A 依赖条件下提高 **IFITM1** 翻译。当前片段没有提供其在 NK、DC、巨噬细胞或 T 细胞中的独立直接功能链。[114]

- **YTHDF2** 早期模型把它描述为 m⁶A RNA 降解因子，可将转录本募集至 decay sites；后续模型则认为 YTHDF1–3 均可能通过 **CCR4–NOT deadenylation complex** 参与 mRNA 降解。YTHDF2 与 **ISG20** 可形成复合物并选择性降解 m⁶A 修饰的 HBV 转录本；它还可与 m⁶A 病毒 RNA 竞争 RIG-I，从而压低 RIG-I 介导的 IFN 信号。YTHDF2 的 RNA 稳定性作用具有序列背景依赖性：结合细胞 mRNA 的 m⁶A 位点可促进 destabilization，而结合 HIV-1 转录本的 m⁶A 位点却可提高病毒 RNA 稳定性。[114]

- 在 METTL14 缺失的结直肠癌模型中，YTHDF2 被置于稳定 **STAT1 和 IRF1 mRNA** 的机制链中；这说明同一 Reader 在不同肿瘤细胞、巨噬细胞和 T 细胞相互作用背景下，可能同时影响 RNA 稳定性和抗肿瘤免疫，而不能只用“YTHDF2 促进降解”概括。[115]

- **YTHDF3** 可与 YTHDF1 相互作用以促进翻译，也可与 YTHDF2 关联以促进降解；另一些研究则认为三个 YTHDF 成员都能招募 CCR4–NOT。YTHDF3 还 preferentially 促进 YTHDF1/3 共同靶标而非其独有靶标的翻译。因此，YTHDF3 的已知伙伴包括 YTHDF1、YTHDF2 和翻译/降解复合物，但这些关系的证据层级不完全相同。[114]

- 在基础条件和病毒感染模型中，DF3/YTHDF3 与 **PABP1、eIF4G2** 协作，结合 **FOXO3 mRNA** 的翻译起始区域，促进 FOXO3 翻译并抑制 ISG 表达；DF3 敲除小鼠 ISG 水平升高，并对多种病毒感染更具抵抗力。综述所引 2019 年研究题名也直接把 YTHDF3 与“促进 FOXO3 翻译并抑制干扰素依赖的抗病毒反应”联系起来。[114]

- YTHDF 家族的分工仍有冲突：一类研究支持 DF1 促翻译、DF2 促降解、DF3 兼具两者；另一类研究认为三个成员功能高度冗余，都可参与 CCR4–NOT 介导的降解。不同研究还分别提出一个 m⁶A 位点可能主要结合一个 DF 成员，或可由三个成员近似等效结合。因此，YTHDF1/2/3 的成员差异和互作应按具体 RNA、细胞状态和实验模型报告。[114]

- 病毒模型进一步显示这种条件依赖性：在 PEDV 中，DF1 或 DF2 depletion 增加病毒复制，DF2 主要通过降低病毒 RNA 稳定性抑制复制；在某些 SARS-CoV-2/A549 研究中，METTL3、DF1 或 DF3 depletion 反而抑制病毒复制；在 RSV 中，DF1–3 overexpression 增加病毒蛋白、基因组 RNA、mRNA 和病毒颗粒形成，并可结合 RSV **G mRNA**。综述还报告，选择性 METTL3 抑制剂 STM2457 将 HCoV-OC43 感染性病毒产量降低超过 **100 倍**，将 SARS-CoV-2 产量降低约 **300 倍**。这些数值和方向都限于相应病毒与细胞模型，不能直接转化为 NK 或其他免疫细胞功能结论。[114]

**YTHDC1、YTHDC2 与非 YTH Readers**

- **YTHDC1** 是核内直接 m⁶A Reader；其 YTH domain 可选择性结合 m⁶A RNA。HBV 模型中，YTHDC1 与 **FMRP** 共同识别 m⁶A 修饰 HBV 转录本并促进其向细胞质输出，从而有利于病毒生命周期。该结果证明 RNA 输出功能关联，但当前片段没有给出 YTHDC1 在宿主免疫细胞中的直接因果表型。[114]

- **YTHDC2** 的当前证据主要支持其为可在核内和细胞质分布的直接 YTH Reader；本组片段没有提供其在四类指定免疫细胞中的具体靶 RNA、蛋白伙伴或功能终点，因此不能用其他 YTH 成员的结果替代 YTHDC2 的免疫证据。[114][115]

- **HNRNPA2B1** 是核内非 YTH m⁶A 相关因子。一个模型认为它直接结合甲基化 **RGAC** consensus site，并通过招募 **Drosha/Pasha microprocessor complex** 促进 pri-miRNA 加工；另一个研究则认为它是 indirect reader，因为体外不能特异区分 m⁶A RNA，且体内只有少量 m⁶A 位点邻近 HNRNPA2B1 结合。因此，Drosha/Pasha 属于功能性复合物关系，而 HNRNPA2B1 的“直接 Reader”身份仍有争议。[114]

- 在 HSV-1 识别模型中，HNRNPA2B1 可在细胞核识别 DNA virus，随后发生二聚化及去甲基化相关过程并转位到细胞质，激活 I 型 IFN 信号；它还被描述为促进 **cGAS、IFI16 和 STING mRNA** 的 m⁶A 修饰、核质转运和翻译，从而支持 IFN-α/β 产生。该链条是 HNRNPA2B1 最具体的免疫证据，但条件限于 HSV-1/核—质转位背景，不能扩展为所有免疫细胞的普遍规律。[114]

- **HNRNPC** 和 **HNRNPG/RBMX** 被描述为可通过 m⁶A-switch 机制识别结构变化后的 RNA；[115] 的图注把 HNRNPC 列为核内 Reader。但当前片段没有给出 HNRNPC 或 HNRNPG/RBMX 在 NK、DC、巨噬细胞或 T 细胞中的直接 m⁶A—功能链，因此 HNRNPC 只能保留为候选/非经典 Reader，不能写成已确立的免疫核心因子。[114][115]

- **IGF2BP1–3** 是 m⁶A 相关的非经典或间接 Readers。它们通常被描述为增强 m⁶A mRNA 稳定性；IGF2BP1 在热应激后可重新定位到 stress-granule mRNA aggregates，可能储存翻译失活的 mRNA 以避免降解。IGF2BP 与 m⁶A RNA 的直接结合仍不清楚：CLIP motif、全转录组定位和较弱的甲基化选择性都支持间接 Reader 模型；其与 DF 蛋白的 pulldown 关系也可能是间接连接。[114]

- **IGF2BP1** 在本组证据中只有一般性 RNA 稳定性和热应激功能，没有 NK、DC、巨噬细胞或 T 细胞的具体直接 m⁶A 机制。**IGF2BP2** 则在肺腺癌综述表中与活化记忆 CD4⁺ T 细胞、静息 NK 细胞、M0/M1 巨噬细胞和 LAG3 相关；在肾透明细胞癌条目中又与 NK 细胞、嗜中性粒细胞和 **ALDOB** 相关，但该相关性方向明确为未知。2021 年研究题名把 IGF2BP2 与通过稳定 **TSC1 和 PPARγ** 调节巨噬细胞表型激活和炎症性疾病联系起来；由于当前片段只有题名层面的支持，不能据此补充直接结合或救援实验。[114][115]

- **IGF2BP3** 的疾病表格关联包括：结直肠癌中的 NK CD56^dim、T helper、DC 和巨噬细胞/中性粒细胞，并与 PD-1、CTLA-4 和免疫检查点治疗相关；膀胱癌中的 M2 巨噬细胞及 **PGM1、ENO1**；宫颈癌中的 Treg 及 **GLS、GLUD1**；类风湿关节炎中的 M1 macrophage polarization。肾透明细胞癌条目将其与 NK 细胞、嗜中性粒细胞、内皮细胞及 ALDOB 联系起来，但相关方向未知。上述资料是疾病表达或统计关联，当前片段未提供 IGF2BP3 的直接 m⁶A 结合、遗传扰动或救援实验。[115]

- **FMRP** 可直接结合 DF2，因此可能通过与 YTHDF 蛋白互作而间接关联 m⁶A RNA；在 HBV 模型中，FMRP 与 YTHDC1 共同促进 m⁶A 修饰病毒转录本的核输出。不过，当前片段没有 FMRP 直接调节宿主免疫细胞功能的证据，所以应保留为非经典候选效应因子，而非 canonical Reader。[114]

- **eIF3** 在当前证据中主要表现为 YTHDF1/DF1 促进 m⁶A RNA 翻译时的翻译起始协作因子；因此其资格更接近 m⁶A-dependent translation effector，而不是已经独立确立的经典 Reader。另有研究把 **Prrc2a** 作为可识别 GGm⁶ACU motif、稳定神经细胞关键转录本的新 Reader，但当前没有其他器官或免疫系统证据，故不纳入本节核心 roster。[114]

总体上，YTHDF1–3、YTHDC1–2 的直接 Reader 身份最明确；HNRNPA2B1、HNRNPC、IGF2BP1–3、FMRP 和 eIF3 需要分别标出直接结合、结构开关、共同复合物或下游效应证据。免疫综述表中的“相关”“positive”或“unknown”只能作为候选线索，不能替代直接催化、结合、遗传干预或体内功能证据。[114][115]

**Writers：核心酶与招募层**

本组证据支持的 canonical Writers 包括 **METTL3、METTL14、WTAP、VIRMA/KIAA1429、RBM15、RBM15B、ZC3H13 和 CBLL1/HAKAI**。其中，METTL3 是催化亚基，METTL14 是底物结合和定位平台；其余多数是定位、招募或复合物稳定性因子，而非独立催化酶。核心复合物优先识别新生 RNA 的单链 DRACH 基序，mRNA 上的修饰富集于终止密码子附近和 3′UTR，但并非所有 DRACH 位点都会被修饰。[116][117]

| 蛋白 | 具体分子功能 | 已知互作及关系类型 | 免疫相关性与证据边界 |
|---|---|---|---|
| **METTL3** | METTL3/METTL14 异二聚体中的活性甲基转移酶，含 SAM 结合口袋，负责把 m⁶A 写入 RNA；与 METTL14 形成稳定核心酶。 | 与 METTL14 形成核心复合物；WTAP 可通过 METTL3 的 N 端结构域直接连接核心酶；METTL3 与抑制性组蛋白标记的募集可由 YTHDC1 的直接相互作用维持。[116][117] | 2019 年研究题名将 METTL3 介导的 mRNA m⁶A 与 DC 活化相联系；本组片段没有给出具体靶 RNA 或完整实验读出，因此不能仅据此扩展为所有免疫细胞中的统一机制。[118] |
| **METTL14** | 非催化亚基，提供 RNA-binding scaffold，参与底物结合、定位，并通过变构作用增强 METTL3 催化活性；参与新生 RNA 的 DRACH 位点写入。[116][117] | 与 METTL3 形成稳定异二聚体；可直接接触 H3K36me3、H3K27ac、H3K4me3 和抑制性 H3K27me3 等组蛋白标记，并直接招募 KDM6B；KDM6B 去除 H3K27me3 后可促进转录激活。[116] | 2018 年研究题名显示 METTL14 通过 mRNA m⁶A 影响造血干/祖细胞分化和白血病发生；本组片段没有具体靶 RNA、免疫细胞亚群或直接免疫扰动细节。[118] |
| **WTAP** | m⁶A 甲基转移酶调节亚基；缺少催化结构域，本身没有 m⁶A 催化活性，但把 METTL3/METTL14 定位到富含前体 mRNA 加工因子的核斑，并调节体内 RNA 结合和 m⁶A 水平。[116][117] | 与 METTL3 N 端存在直接相互作用；与 RBM15、RBM15B 存在直接相互作用并负责招募二者；还被描述为可直接连接转录延伸因子 Spt6。[116] | 该组卡片主要支持 WTAP 的复合物角色；未提供其在 NK、DC、巨噬细胞或 T 细胞中的直接免疫靶 RNA。 |
| **VIRMA/KIAA1429** | WTAP 依赖的区域选择性招募因子，把 METTL3/METTL14/WTAP 复合物引导至 mRNA 3′端，促使 3′UTR 和终止密码子附近优先发生 m⁶A；并与可变 poly(A) 加工相关。[116][117] | 直接与 CPSF5、CPSF6 相互作用，但该关系具有 RNA 依赖性；WTAP/VIRMA 复合界面进一步招募 ZC3H13 和 HAKAI。[116] | 在人 A549 细胞中耗竭 KIAA1429 后，m⁶A peak score 约下降 **4 倍**；这是肿瘤细胞模型中的分子读出，不等同于免疫细胞因果证据。[117] |
| **RBM15** | 具有三个 RRM 结构域，识别 RNA 中的 U-rich 序列，并将 WTAP-METTL3 复合物招募到 mRNA 和 lncRNA **XIST** 的特定位点；其 SPOC 结构域还可识别 RNA polymerase II C 端的磷酸化标记。[116][117] | WTAP 与 RBM15 直接相互作用；RBM15/15B 的免疫沉淀结果支持其招募 WTAP-METTL3；ZC3H13 可作为桥接因子把 RBM15 连接到 WTAP/ m⁶A 机器。[116][117] | 2007 年研究将 RBM15 与造血发育、Notch 诱导的转录激活及髓系分化联系起来，但这些题名信息没有直接证明“RBM15—m⁶A—免疫 RNA”因果链。[118] |
| **RBM15B** | RBM15 的旁系同源招募因子；通过 U-rich 序列参与把核心酶定位到 mRNA 和 XIST 的邻近 DRACH 位点。[116][117] | 与 WTAP 存在直接相互作用，并由 WTAP 招募至 METTL3/METTL14 核心酶；其结合位点在 m⁶A 位点附近富集。[116][117] | 本组片段没有 RBM15B 在四类指定免疫细胞中的直接模型、靶 RNA 或功能读出。 |
| **ZC3H13** | 非催化适配器和 RNA 结合蛋白，可提高核心酶对 RNA 的结合亲和力；敲低后 WTAP、VIRMA 和 HAKAI 大量转位至细胞质，说明它参与维持写入复合物的核定位。[116] | 被 WTAP/VIRMA 形成的复合界面招募；在小鼠中作为 RBM15 与 WTAP 之间的桥接因子，促进 mRNA m⁶A 沉积。[116][117] | 2018 年研究主要显示其调控核 RNA m⁶A 和小鼠胚胎干细胞自我更新；本组没有其在免疫细胞中的直接靶 RNA 或功能证据。[118] |
| **CBLL1/HAKAI** | 被列为 MACOM 相关的 E3 ubiquitin ligase/复合物组分，主要承担复合物关联和稳定性角色，不应写成 METTL3 同类的催化亚基。[116] | 由 WTAP/VIRMA 形成的复合界面招募；本组没有提供其独立催化 m⁶A 或独立免疫靶标的实验细节。[116] | 目前只能确认其 Writers 复合物相关身份；四类免疫细胞中的直接功能在本组证据中未确立。 |

**边界候选。** **METTL16** 应与 canonical mRNA m⁶A Writers 分开：它修饰人 U6 snRNA 的 **A43 位点**，并参与细胞 SAM 水平调控，因而属于 RNA m⁶A 相关酶，但本组没有足够的直接免疫证据把它纳入核心 mRNA m⁶A 免疫机器。[116][117] **PCIF1/CAPAM** 主要催化帽邻近的 m⁶Am，而不是本报告优先讨论的内部 m⁶A，因此排除在核心 roster 外。[116]

**Erasers：FTO 与 ALKBH5**

**FTO 和 ALKBH5** 是本组来源明确列出的两种已表征 m⁶A demethylase。[116][117]本组对 FTO 只提供了“m⁶A demethylase”分类信息，未给出可核查的蛋白互作伙伴、四类免疫细胞模型或具体免疫 RNA 读出，因此不能补写其免疫机制。

**ALKBH5** 具有更具体的分子证据：它可与 METTL3/METTL14 形成 7SK snRNA m⁶A 写入—擦除的功能对照，去除 7SK 上的 m⁶A；同时，ALKBH5 与 m⁶A reader **RBM33** 结合，RBM33 通过抑制 ALKBH5 的 SUMOylation 激活该酶，并参与选择去甲基化靶标。ALKBH5 还与 TREX、外显子连接复合体（EJC）、前体 mRNA 剪接及 miRNA 介导 RNA 降解相关组分发生关联。[116]其中，RBM33—ALKBH5 是功能性调节关系；TREX、EJC 等在本组片段中被表述为相关复合体或过程关联，而不是逐一确认的直接物理互作。上述 Eraser 证据尚未提供 NK、DC、巨噬细胞或 T 细胞中的直接功能模型。

**Readers：从 m⁶A 识别到 RNA 命运**

本组来源将 **YTHDF1/2/3、YTHDC1/2、IGF2BP1/2/3 和 HNRNPA2B1** 列为主要 Readers；另有综述把 HNRNPC/HNRNPG 作为 m⁶A 相关 RNA 加工因子列出，但其是否直接结合 m⁶A 需要保留争议。[117][118]

- **YTHDF1、YTHDF2 和 YTHDF3** 的共同 YTH 结构域可识别 m⁶A，但功能并不相同。YTHDF1 与翻译起始因子、核糖体相互作用，通常促进靶 mRNA 翻译；YTHDF2 直接招募 CCR4–NOT deadenylase complex，使含 m⁶A 转录本去腺苷化并降解；YTHDF3 与 YTHDF1 共同调节翻译，并可直接与 YTHDF2 相互作用，参与靶转录本降解。[117][118]不过，另一种统一模型在 **HeLa 细胞**中观察到 YTHDF1–3 可结合相同的 m⁶A mRNA，不能诱导翻译，并可能冗余地介导 mRNA 降解和细胞分化。因此，不能把“YTHDF1 必然促进翻译、YTHDF2 必然降解、YTHDF3 仅作桥接”当作脱离细胞背景的定律。[118]在免疫方面，本组只显示 2019 年研究题名将 YTHDF1 与 DC 的 mRNA m⁶A 和抗肿瘤免疫联系起来；题名片段没有提供具体靶 RNA。[118]

- **YTHDC1** 是专一定位于细胞核的 YTH-domain reader，参与 mRNA 剪接、核输出、染色质及转录调控。它与 **SRSF3** 存在直接 C 端相互作用，促进 m⁶A 修饰外显子包含，同时抑制 SRSF10 介导的外显子跳读；它还可招募 KDM3B，但该招募机制仍被来源标为未知。YTHDC1 结合 m⁶A-carRNA 后可将其导向核外排复合体降解。[116][118]

- **YTHDC2** 被列为细胞质 m⁶A reader；本组片段给出的明确功能是参与精子发生中由有丝分裂向减数分裂的转换，而不是免疫调控。其在四类指定免疫细胞中的直接靶 RNA、互作伙伴和功能读出在本组证据中未确立。[118]

- **IGF2BP1/2/3** 通过典型 **GG(m⁶A)C** 基序识别靶转录本，通常增强 mRNA 稳定性、翻译并保护 m⁶A-mRNA 免于降解；这一家族层面的结论发表于 2018 年研究。[118]本组显示的成员级例子主要来自非免疫模型：IGF2BP2 可结合编码线粒体呼吸链复合体亚基的 mRNA，调节氧化磷酸化；IGF2BP3 可被 miRNA-129-1 与 MAPK1 一起靶向并影响胶质母细胞瘤细胞周期。[118]这些结果不能直接替代 NK、DC、巨噬细胞或 T 细胞中的免疫证据；本组对 IGF2BP1/2/3 均未提供指定免疫细胞中的直接因果链。

- **HNRNPA2B1** 的 Reader 身份存在方法学争议。一种模型认为它可直接结合 m⁶A，并与 **METTL3** 协同调节可变剪接和 pri-miRNA 加工；另一种结构研究认为，m⁶A 先改变 RNA 构象形成“m⁶A switch”，再使 HNRNPA2B1 更容易结合，而非特异性识别甲基本身。HNRNPA2B1 还可与 miRNA 微处理体组分 **DGCR8** 相互作用。[117][118]类似地，HNRNPC/HNRNPG 在本组来源中主要被解释为响应 m⁶A 引起的 RNA 结构改变，而不是直接结合 m⁶A；因此应作为非经典或待核实候选，而非无条件列入 canonical Readers。

- **eIF3** 的证据层级也应单独标注：本组仅显示 YTHDF1 可增强 **EIF3C** 翻译，或与翻译起始过程发生功能关联；没有直接证明 eIF3 复合体本身特异识别 m⁶A，也没有给出其在四类免疫细胞中的直接 m⁶A 因果证据。因此，eIF3 更适合作为翻译效应复合体候选，而非已确立的 canonical reader。[118]

就后续四列表格而言，本组证据可为 **DC 行**提供“METTL3—mRNA m⁶A—DC 活化”和“YTHDF1—mRNA m⁶A—抗肿瘤免疫”的候选入口；但由于当前片段没有给出具体靶 RNA，表格中的“调控目标与机制”不能超出该证据范围。其他免疫细胞行不得用上述非免疫模型或家族层面的 Reader 功能填补。

**Writers：复合体角色与相互作用（续）**

Writers 中只有 METTL3 是催化核心；METTL14 与 METTL3 形成稳定异二聚体，主要参与 RNA 识别、结合并稳定复合体；WTAP 稳定写入复合体，RBM15 和 RBM15B 则帮助复合体识别富含 U 的 RNA 区域并定位靶位点。[119] 因而，METTL3–METTL14 属于核心复合物关系，WTAP、RBM15 和 RBM15B 属于复合体或功能性辅助关系，而不能仅凭共现推断每一对均有直接物理结合。WTAP 敲除会降低 METTL3 与 RBM15 的相互作用；RBM15B 下调会降低总体 m⁶A，但该证据未说明具体实验方法。[119]

VIRMA/KIAA1429 是非催化支架，负责集合写入复合体组分，并促进 3′ UTR 和终止密码子附近的选择性 m⁶A 沉积；VIRMA 耗竭造成的全局 m⁶A mRNA 损失大于单独耗竭 METTL3、METTL14 或 WTAP。[120] 在乳腺癌细胞中，全长 VIRMA 而非 N 端形式提高总体 m⁶A，敲低 VIRMA 则降低 m⁶A；全长形式主要位于细胞核，并伴随 WTAP 增加，而 METTL3、METTL14 未明显增加。该研究还观察到全长 VIRMA 过表达后 SKBR3 细胞有 **655 个** m⁶A 峰增加，增加的 m⁶A 峰与 mRNA 表达升高相关，EIF2AK3、ERN1 和 ATF6 等 UPR 相关转录本出现峰富集。[120] 在同一模型中，m⁶A 修饰的 lncRNA **NEAT1**（包括 NEAT1_1 和 NEAT1_2）表达升高；野生型 SKBR3 中 NEAT1_1 约占总 NEAT1 转录本的 **75%**，轻度提高 NEAT1_1 即可增强细胞增殖。[120] 全长 VIRMA 还促进乳腺癌细胞克隆形成和免疫缺陷小鼠异种移植瘤生长；应激条件下可增强 UPR/ER 应激和死亡易感性，但这些是癌细胞证据，不是 NK、DC、巨噬细胞或 T 细胞的直接证据。该研究报告 TCGA 中 VIRMA 扩增约 **15%（n=960）**、METABRIC 中约 **20%（n=1904）**，浸润性导管癌与浸润性小叶癌分别约为 **18%** 和 **6%**。[120]

WTAP 与 METTL3/14 的“锚定并促进 m⁶A 沉积”机制可追溯至 2014 年原始研究；在乳腺癌实验中，VIRMA 全长过表达伴随 WTAP 升高，作者据此推测 WTAP 增强 METTL3 的 mRNA 结合能力，但该处仍属于功能性复合体解释，并未给出 VIRMA–WTAP、VIRMA–METTL3 或 VIRMA–METTL14 的独立直接结合实验。[120] ZC3H13 仅被该组资料列为写入复合体组分，未进一步给出其催化、招募或免疫功能。[119] CBLL1/HAKAI 可作为复合体相关因子记录，但 CBLL1 同时是 E3 泛素连接酶；现有片段不足以证明其直接催化 m⁶A。[13,15]

**Readers：成员差异与功能性伙伴**

Readers 通过识别 m⁶A 把修饰信号连接到 RNA 输出、剪接、翻译、稳定性和降解；该组资料列出的代表包括 YTH 蛋白、hnRNP、eIF3 和 IGF2BP 家族。[119] **YTHDF1** 选择性识别 m⁶A mRNA，促进其装载到核糖体，并增强与翻译起始因子 eIF3 的功能联系，从而促进翻译起始，同时影响 mRNA 翻译和降解。[119] **YTHDF2** 是胞质 m⁶A reader；其与 CNOT1 存在直接相互作用，可促进靶 mRNA 去腺苷化和降解。[119] **YTHDF3** 促进 m⁶A mRNA 翻译，可能通过核糖体蛋白参与翻译起始；它与 YTHDF1 的共同靶标翻译效率升高，提示二者存在协同，但来源对 YTHDF3 单独参与翻译起始使用了“可能”表述。[119]

**YTHDC1** 主要位于细胞核，可在活跃转录位点和 RNA 加工结构周围形成 YT bodies；它识别 m⁶A RNA 并调节剪接，通过促进 SRSF3、抑制 SRSF10 与靶 RNA 的结合来改变剪接。YTHDC1 与 YTHDF2 的 m⁶A 结合位点约有 **21%** 重叠，但其对 m⁶A 的结合更强。[119] **HNRNPA2B1** 识别 RGACH 序列，参与 m⁶A RNA 的 pri-miRNA 加工和 mRNA 可变剪接，并促进其与 DGCR8 加工复合体的功能联系，从而促进 pri-miRNA 成熟；“m⁶A switch”提高结合可及性则主要是生化和生物信息学分析的提示。[119] 同一来源称 HNRNPG 的低复杂度 AGG 区也可结合 m⁶A RNA并影响稳定性和表达。**HNRNPC** 是核内 hnRNP，参与 pre-mRNA、m⁶A mRNA 和 lncRNA 加工，可改变 RNA 局部结构并调节外显子剪接；该资料没有提供其特定蛋白互作伙伴。[119]

**Eraser 与免疫关联证据边界**

本组片段对 **ALKBH5** 的直接分子证据较完整：它可在体内外逆转 mRNA m⁶A；在 HeLa 细胞中，ALKBH5 下调使总 mRNA m⁶A 增加 **9%**，过表达使其降低 **29%**，并可影响 mRNA 加工、核输出和 RNA 代谢。[119] 因此 ALKBH5 属于 canonical Eraser，但上述定量结果来自 HeLa 细胞，不能直接等同于指定免疫细胞中的功能。

免疫关联方面，2024 年 MG 数据集分析将 METTL3、RBM15、WTAP、RBM15B、CBLL1、YTHDF1/2/3、YTHDC1/2、HNRNPA2B1、FTO 和 ALKBH5 等纳入分析；在 26 个预设 m⁶A 相关因子中实际提取了 16 个，METTL14虽被列入预设集合，却未出现在实际提取名单中。[121] MG 与健康对照比较中，RBM15、CBLL1 和 YTHDF1 表达升高；RBM15 与免疫细胞的相关性最强，CBLL1 与 CD56^dim NK 细胞、NKT 细胞和 Th1 细胞呈正相关。[121] 这些结果是表达差异、免疫浸润相关性和机器学习筛选，不能替代特定 RNA 的直接结合、m⁶A 位点验证或免疫细胞因果扰动。另有一条被归入 YTHDF2 的证据实际描述的是 **YTHDC1–Beclin1 mRNA–NF-κB** 轴在 IBD 巨噬细胞中的作用，因此不能把该机制归于 YTHDF2。[121]

分类：Writers添加、Erasers去除（FTO/ALKBH5）、Readers识别m⁶A并改变RNA命运。[52] METTL3/METTL14为Writer核心：METTL3结合SAM催化；METTL14无催化性，1∶1稳定METTL3、促底物结合；WTAP锚定异二聚体于RNA。[122] VIRMA偏向3′UTR/终止密码子甲基化；RBM15/15B经WTAP、RRM/SPOC招募复合体至富U/DRACH邻近RNA；ZC3H13为核内非催化桥接因子，连接RBM15及HAKAI/WTAP/VIRMA、增强RNA结合；CBLL1/HAKAI稳定MACOM，HAKAI–VIRMA有Co-IP支持。[122] Readers含YTHDF1/2/3、YTHDC1/2、IGF2BP1/2/3、HNRNPC/A2B1；YTHDF1调TRAF6翻译，YTHDF2有NK抗肿瘤/抗病毒证据但未列目标RNA。[52] METTL14缺失小鼠髓系细胞降低SOCS1-m⁶A/YTHDF1结合并过激活TLR4/NF-κB；AS患者T细胞METTL14下降伴FOXO3a、自噬下降；RBM15介导K17 m⁶A影响IL-17A刺激角质形成细胞；METTL16仅为边界候选。[52]

**Writers复合体与非经典候选**

**名册与复合体。**2024年综述将 METTL3、METTL14、WTAP、RBM15、VIRMA/KIAA1429、METTL16、ZC3H13 和 Hakai 列为 MTC writers；METTL3–METTL14形成1∶1异源二聚体，WTAP负责将其招募至靶mRNA[123]。另一综述增列 RBM15B；KIAA1429、WTAP、ZC3H13、CBLL1/HAKAI及RBM15/15B组成MACOM，直接结合RNA底物并对writer活性必需[124][125]。其中，METTL16虽被列为writer线索，但本组证据未确立其属于本报告的核心免疫名册；“m⁶A transferases参与抗肿瘤免疫”的条目也未指明具体蛋白或步骤[124]。

**RBM15。**RBM15本身没有甲基转移活性，而是结合mRNA上的U-rich序列，招募MTC/METTL3–METTL14定位靶RNA；其与WTAP的复合体招募依赖WTAP水平，WTAP耗竭会削弱或中断该结合，LSETD磷酸化基序与RBM15-SPOC的联系仍属综述转述[123]。在小鼠造血干细胞和巨核细胞中，2007、2009和2015年的研究分别支持其参与造血发育、调节c-Myc，以及通过c-Mpl可变剪接调节血小板生成素反应；2022年透明细胞肾癌研究则将RBM15-CXCL11的m⁶A调控与巨噬细胞浸润联系起来，但并未证明RBM15在巨噬细胞内直接调控m⁶A[123]。

**RBM15B与ZC3H13。**RBM15B/OTT3是NXF1核输出受体的cofactor（2009年）；它可与RBM15协同招募WTAP及METTL3–METTL14至lncRNA XIST的m⁶A区域，RBM15降低时产生补偿，只有双敲RBM15/RBM15B才显著降低XIST甲基化[123]。ZC3H13/Flacc在2018年被报道桥接Rbm15/Spenito与Wtap/Fl(2)d，属于非催化复合体组分[123]。这些writer卡片均未给出NK、DC、巨噬细胞或T细胞中的直接因果实验。

**VIRMA/WTAP。**VIRMA/KIAA1429是支架，其N端招募METTL3、METTL14和WTAP；敲低后细胞RNA的m⁶A下降，并在RNA存在时关联CPSF5/CPSF6、促进近端poly(A)位点使用[125]。长、短异构体分别为24个外显子/1812 aa和13个外显子/1147 aa；两者均含130-aa SUN/RNA结合域（aa155–279），短型功能仍大部分未知[125]。肺癌中KIAA1429与YTHDF2/3促进DAPK3 mRNA的m⁶A依赖性降解并增加MUC3A表达；乳腺癌中它与IGF2BP3共同稳定m⁶A-HAS2 mRNA，但直接结合方法未说明[124][125]。冷冻电镜显示KIAA1429–WTAP构成MACOM核心；该来源未提供指定免疫细胞模型，且KIAA1429在肿瘤微环境中的作用仍未知[125]。

**Erasers与Readers的证据边界。**ALKBH5是偏好m⁶A的eraser，可影响mRNA代谢、核输出、长3′UTR转录本的剪接与稳定性；肺癌例证包括TGFβR2/SMAD3下降、SMAD6升高及TIMP3稳定性改变，且其对2013年小鼠正常精子发生不可或缺；ALKBH3/ALKBH1在所示综述中主要对应tRNA m⁶A去甲基化，不能替代canonical mRNA免疫证据[124]。YTHDF1通过eIF3促进翻译，YTHDF2直接招募CCR4–NOT使m⁶A RNA去稳定化，YTHDF3协同翻译与降解；YTHDC1经SRSF3参与核内剪接、输出并识别MALAT1 m⁶A[124]。HNRNPA2B1参与miR-122-5p外泌体分选及pri-miR-106b-5p加工；HNRNPC仅在肺癌综述中作为剪接因子出现。eIF3是与YTHDF1/METTL3相连的m⁶A依赖翻译效应因子，可涉及YAP、EGFR和TAZ，但不宜直接归为canonical reader；所示页面未提供FMRP的m⁶A或免疫证据[124]。

核心Writers名册：METTL3、METTL14、WTAP、VIRMA/KIAA1429、RBM15、RBM15B、ZC3H13、CBLL1/Hakai。[126] METTL3催化；2017年研究将其与髓系白血病的m⁶A依赖性翻译控制相联。METTL14与METTL3成稳定异二聚体，结合底物RNA、定位甲基并增强酶活（500mM NaCl下仍互作）；WTAP为非催化组分，稳定异二聚体并定位核斑；VIRMA对m⁶A沉积必需但功能未明。[126] RBM15/RBM15B以U-rich mRNA招募复合体；TAP-MS支持RBM15与WTAP、VIRMA、Hakai、ZC3H13共复合物，仅属复合物证据；未给出RBM15B独立伙伴结果。ZC3H13连接RBM15/Nito与WTAP/Fl(2)d，并与VIRMA/Hakai共复合物；2018年小鼠mESC敲除使m⁶A降低80%、mRNA 3′端富集下降，果蝇互作不依赖RNA，并削弱Rbm15–WTAP。CBLL1/Hakai为非催化MACOM组分；小鼠与Rbm15、WTAP、VIRMA、METTL3共纯化，果蝇与Nito、Flacc、Vir相关。[126]

Writers：METTL3（催化）、METTL14（结合RNA的无SAM变构激活）、WTAP（招募靶mRNA并定位METTL3/14至核speckles）、VIRMA/KIAA1429（偏向3′UTR/终止密码子）、RBM15/15B（U-rich、WTAP依赖招募）、ZC3H13（桥接RBM15/Spenito–WTAP）和CBLL1/HAKAI（拟南芥中必需，哺乳动物作用未明）。WTAP还与上述组分同属复合体并与WT1成剪接复合体；METTL16主要写入U6 snRNA/MAT2A、维持SAM，属mRNA Writers边界候选。[22,23]

病毒感染且IFN-I激活时，WTAP经K48泛素–蛋白酶体途径降解；IRF3（5′UTR）和IFNAR1（3′UTR）mRNA的m⁶A随之下降，分别导致IRF3翻译受阻、IFNAR1降解加速，抗病毒反应受限而维持稳态。[127] ALKBH5为m⁶A去甲基化酶，另有m⁶A–YTHDF2依赖的PER1调控，但本组证据无指定免疫细胞模型。[127]

Readers识别m⁶A并改变RNA命运；直接YTH readers为YTHDC1/2、YTHDF1/2/3，hnRNPC/G/A2B1经m⁶A-switch间接作用。[128] YTHDC1–SRSF3（拮抗SRSF10）调剪接并经NXF1输出；YTHDF1–eEF2/eIF3促Snail CDS-m⁶A翻译，但约33%靶标效应相反；YTHDF2–HRSP12/RNase P-MRP或CCR4-NOT、外泌体/P bodies促mRNA降解，亦有稳定模型；YTHDF3–eIF3a促自身5′UTR m⁶A帽非依赖翻译。[128] IGF2BP1/2/3属reader但直接结合未定；IGF2BP3可识别GGAC/结构开关，IGF2BPs借HuR、MATR3、PABPC1稳定mRNA；FMRP直接结合未定、仅见与YTHDF2互作；eIF3可直接结合5′UTR m⁶A，METTL3可与其共同作reader。[128] METTL14、RBM15/15B、ZC3H13、YTHDF1及IGF2BP1在这些来源中尚无四类指定免疫细胞的直接模型。

MAC由METTL3/METTL14组成；METTL3催化、METTL14协同，WTAP、VIRMA、RBM15/B、ZC3H13、HAKAI属MACOM辅助组分[129][130]。

**Writers：催化核心、定位与招募**

Writers 负责在特定位点安装内部 m⁶A。所引免疫综述将 **METTL3** 视为唯一具有活性的催化亚基，另一综述称其为主要催化亚基；**METTL14、WTAP、VIRMA/KIAA1429、RBM15、RBM15B、METTL16、CBLL1/HAKAI、ZC3H13** 及 **ZCCHC4** 则属于辅助或复合体相关成员。因此，“Writer”是写入系统的类别，不意味着每个成员都能独立催化。[26,27]

**METTL14** 与 METTL3 形成核心甲基转移酶复合体，参与哺乳动物核 RNA 的 N6-腺苷甲基化；其与 METTL3 在核斑中共定位并有助于稳定复合体。当前卡片没有给出 METTL14 在 NK、DC、巨噬细胞或 T 细胞中的独立直接因果机制。[132] **WTAP** 是非主要催化性的调节亚基，可将 METTL3/METTL14 招募至核斑；其复合体伙伴包括 METTL3/METTL14、VIRMA、CBLL1、ZC3H13 和 RBM15/15B。综述还描述了 WTAP 与 METTL3 的结合界面，以及 RBM15 与 WTAP 的结合；但共同复合物证据不应自动等同于每一对蛋白均有直接物理结合。[132]

**VIRMA/KIAA1429** 与 WTAP 复合体相关，并介导 m⁶A 在 mRNA 3′UTR 和终止密码子附近的偏好性分布，同时与 alternative polyadenylation 相关；当前材料没有给出其在四类指定免疫细胞中的直接功能读出。[132] **RBM15** 是 RNA 结合和写入定位因子，可结合 WTAP，并将甲基转移酶复合体招募到特定 RNA 位点；ZC3H13 还可将 Rbm15/Spenito 与 Wtap/Fl(2)d 连接起来，但所引页面没有提供该桥接关系的直接结合实验方法。[132] **RBM15B** 虽被列为 Writer 并出现在 WTAP 复合体名单中，但现有卡片只提供检测名单或共同复合物层面的支持；不能把 RBM15 的具体目标、免疫机制或互作直接转移给 RBM15B。[26,27]

**ZC3H13/KIAA0853** 是 Writer 复合体的核内组分，可与 WTAP 相互作用，并通过 LC 结构域将甲基转移酶复合体保留在核斑中，从而促进复合体功能；其与 RBM15、WTAP 的桥接关系属于复合体或功能性证据，当前材料未证明其在四类免疫细胞中的直接 RNA—功能链。[132] **CBLL1/HAKAI** 被列为 WTAP 复合体成员；WTAP、VIRMA、CBLL1 和 ZC3H13 组成的复合体还被描述为可在 GC-rich 序列中调节 alternative splicing 和 alternative polyadenylation，但当前页面没有给出 CBLL1 独立催化功能、独立蛋白互作或免疫细胞特异性机制。WTAP 的抗病毒机制不能归因于 CBLL1。[132]

一项发表于 **2022 年 11 月 15 日** 的 T1DM 原始研究，以 T1DM 患者和健康个体的 PBMC 为材料（各 **n=6**），结合 m⁶A mRNA 芯片、qRT–PCR 和 MeRIP–qPCR，检测了 10 个 Writer、2 个 Eraser 和 11 个 Reader；PBMC 包含 T、B、DC、单核细胞和 NK 细胞，但不是纯化的单一细胞群。因此该研究的调控因子表达和 m⁶A 图谱关联不能替代四类细胞中的直接因果证据。[131]

**Erasers 与 Readers：成员级证据边界**

**FTO/ALKBH9** 和 **ALKBH5** 被归为 Erasers，负责移除 m⁶A。[131] **ALKBH5** 在上述 T1DM 研究中只是被列入检测的 Eraser；该研究没有报告其在 NK、DC、巨噬细胞或 T 细胞中的具体目标 RNA、分子机制或功能方向，并明确指出调控因子的具体功能和下游目标仍需通过基因敲除、过表达及细胞或动物模型验证。[131] **ALKBH3** 的资格存在来源内冲突：综述正文和表格主要列 FTO、ALKBH5，而图注又把 ALKBH3 列作 Eraser；因此 ALKBH3 应保留为边界候选，不能无条件列入 canonical mRNA m⁶A Eraser。[132]

Readers 可分为直接识别 m⁶A 的蛋白和通过 RNA 结构或复合体间接传递效应的因子，名单包括 **YTHDF1–3、YTHDC1–2、IGF2BP1–3、HNRNPA2B1、HNRNPC** 和 **HNRNPG** 等。[26,27] **YTHDF2** 属于 Reader；T1DM PBMC 研究观察到其表达与 m⁶A 相关转录本存在关联，但没有在 NK、DC、巨噬细胞或 T 细胞中分别证明直接机制和最终功能。[131] **YTHDC1** 可参与 alternative splicing、核输出、m⁶A 转录本降解和基因表达抑制；在 T1DM PBMC 中其表达相对健康组显著上调，但这仍是混合 PBMC 的表达和图谱关联证据。[131]

**IGF2BP1** 被一般分类为 m⁶A Reader，但同一来源的卡片出现内部矛盾：总名单将其列入 11 个 Readers，另一处又称其未出现在 23 项检测名单中。因此，现有材料不能据此给出 IGF2BP1 在四类免疫细胞中的直接目标或因果功能。[131] **IGF2BP2** 在 T1DM PBMC 中显著下调，其表达与差异 m⁶A 转录本和差异表达转录本相关；来源提出它可能以 m⁶A 依赖方式稳定修饰转录本，但精确互作和分子机制仍待验证。[131] **IGF2BP3** 虽被列为 Reader，当前卡片没有提供其在四类细胞中的具体目标、机制或功能结果。[131]

**HNRNPA2B1** 可通过“switch mechanism”识别并结合 m⁶A，调节目标转录本的 alternative splicing；其在 T1DM PBMC 中显著上调，但尚未证明其在四类指定细胞中的直接因果作用。[131] **HNRNPC** 和 **HNRNPG/RBMX** 被列为核内 m⁶A 相关 Reader；表格将其功能概括为调节 mRNA 结构和 alternative splicing，但当前材料没有提供直接免疫功能证据。[132]

**Writers。**核心名册：METTL3/METTL14、WTAP、RBM15/15B、VIRMA/KIAA1429、ZC3H13、CBLL1/Hakai；METTL3催化，METTL14识别底物、定位并变构激活METTL3，其余多为招募、定位或复合体组分；WTAP–VIRMA与METTL3–METTL14可维持写入活性。[133][134] ZC3H13桥接核内RBM15/Spenito与WTAP/Fl(2)d；RBM15稳定银屑病皮肤K17，并与METTL3增强Kdm6b mRNA稳定性、促STAT1介导巨噬细胞活化有关。[133][134] METTL14在RA稳定TNFAIP3；缺失损害iTreg/RORγt、破坏Th1/Th17/Treg平衡，在UC肠上皮增加NFKBIA致屏障损伤、稳定GPX4以防铁死亡。另一CRC模型中，METTL14/METTL3抑制反而增强PD-1应答、CD8⁺T增殖及效应T细胞聚集，提示情境依赖。[133][134] CBLL1/Hakai仅有复合体名册证据；更宽清单还列METTL5/16、ZCCHC4，METTL16指向U6 snRNA，属边界候选，不能等同canonical mRNA writer。[134]

**Erasers。**FTO、ALKBH5为canonical，ALKBH3仅见宽泛清单；FTO调节mRNA剪接/稳定性，ALKBH5影响mRNA输出、代谢和核内加工因子组装。[134] FTO下调增强Th17；UC中CerS6→鞘氨醇-1-磷酸→M1巨噬细胞/Th17并加重结肠炎；FTO还负向调节NK细胞毒性、通过Fas m⁶A影响CD8⁺T存活/效应并促M1/M2活化。[133] ALKBH5通过乳酸和抑制性免疫细胞积累影响抗PD-1反应，但未给出四类细胞的统一直接链条。[134]

**Readers。**主要成员：YTHDF1/2/3、YTHDC1/2、IGF2BP1/2/3、HNRNPA2B1/C/G、eIF3；HNRNPG/RBMX、FMRP为候选。可介导剪接、核输出、翻译、稳定和降解；IGF2BP识别m⁶A增强mRNA稳定/翻译，YTHDF1/3促ITGA6翻译、YTHDF2促SOCS2降解（后二者为非免疫例）。[134] DC中METTL3促激活，YTHDF1损害抗原呈递/CD8⁺浸润，缺失增强抗肿瘤及抗PD-L1；YTHDF2涉及NK抗肿瘤/抗病毒和CD8⁺T多功能性。巨噬细胞另见METTL3-STAT1、YTHDF1-GBP4促M1，ALKBH5-CCL5涉衰老/动脉粥样硬化，YTHDF2-LPS及YTHDC1稳定Beclin1并抑制自噬依赖NF-κB轴。[133] T细胞直接/明确涉及METTL3、ALKBH5、FTO、YTHDF2、METTL14、YTHDC1/2、hnRNPA2B1/C、IGF2BP2/3；IL17A、γδT1/T17和METTL14缺失性结肠炎是背景，未证明ZC3H13直接作用。[133]除复合体/桥接关系外，片段未给出FTO、ALKBH5或各reader的成员级直接互作，不能推定。[133][134]

Writers：METTL3/14催化；WTAP、ZC3H13、RBM15/15B、VIRMA、HAKAI/CBLL1属MACOM，共组分非直接。[135]WTAP/ZC3H13仅GBM浸润相关；ZC3H13在ESCC促METTL3/14核转位，CXCL8 m⁶A稳定→CXCR2促M0→M2、CCL5促迁移，抑制减M2浸润；NK/DC/T及其余未证。[136]

Writers：METTL3催化，METTL14稳定异二聚体并增强酶活；WTAP、VIRMA、RBM15/15B、ZC3H13、CBLL1/HAKAI为复合体/招募组分[137]。2018年mESC中ZC3H13连接RBM15–WTAP，敲除使m⁶A下降80%[137]；RCC中经UNC5CL–YTHDC1轴抑制MDSC积累[138]，GBM免疫仅为转录组相关[139]。

Writer roster：METTL3、METTL14、WTAP、VIRMA/KIAA1429、RBM15、ZC3H13、CBLL1/HAKAI为核心；RBM15B为可能成员。METTL3催化；METTL14激活、定位RNA并稳定METTL3（精氨酸甲基化可改变其互作和位点选择性）；WTAP支架/核定位；VIRMA定向区域选择性及3′UTR/终止密码子附近甲基化；ZC3H13桥接RBM15–WTAP、稳定VIRMA并体外激活METTL3–METTL14；RBM15以3个RRM结合富U序列并参与招募；HAKAI为非催化组装因子。[140][141]

WTAP直接结合METTL3、HAKAI并与VIRMA结构互作；耗竭使METTL3入胞质，肺腺癌细胞中WTAP与m⁶A均降至15%，但“限速”仅为敲低相关，非动力学证明；WTAP mRNA还存在m⁶A依赖剪接反馈。VIRMA截去C端226 aa几乎失活并关联CPSF5/6；RBM15的SPOC可pull-down磷酸化WTAP，Aly/REF、PNMT1为拟议伙伴；ZC3H13广泛接触VIRMA、较弱接触WTAP；HAKAI结合WTAP–ZC3H13并以KIAA1429形成MTC口袋；RBM15B仅有NXF1 cofactor证据，无writer直接互作。[140][142]

WTAP在NK/T淋巴瘤中以m⁶A调控DUSP6，促进增殖和顺铂耐药；RBM15、RBM15B、ZC3H13尚无四类免疫细胞直接模型。METTL16虽列入Writer候选且催化m⁶A，但本片段无其免疫模型、目标或互作证据。[141][142]

Erasers：FTO可形成hm⁶A/f⁶A并去甲基化m⁶A；ALKBH5为核斑内m⁶A eraser，缺氧/癌背景下可降低特定mRNA的m⁶A，全局影响通常较小；其与Prmt6、NANOG、FOXM1仅为功能关联。ALKBH3仅有m¹A/tRNA证据，PCIF1催化m⁶Am，均非canonical核心。[143]

Readers：YTHDF1促TRAF6翻译；YTHDF2经CCR4–NOT促降解；YTHDF3与YTHDF1/2互作并促翻译/降解；YTHDC1促剪接/核输出；YTHDC2提高翻译效率而降低靶mRNA丰度；IGF2BP稳定RNA并促翻译；FMRP调稳定性/核输出；eIF3介导5′UTR-m⁶A非帽依赖翻译；HNRNPC/G仅有剪接线索，核心及免疫资格未定。YTH/YTHDC以YTH域、IGF2BP/FMRP以KH域识别m⁶A。[142][143]

MAC含METTL3/14；MACOM含WTAP、VIRMA、ZC3H13、RBM15/B、HAKAI[144]；YTHDF1/2/3促翻译/降解/协同，HNRNPA2B1存疑[145]

METTL3写/METTL14架；WTAP/VIRMA/ZC3H13/RBM15/HAKAI调节[146]；FTO/ALKBH5擦除；YTHDF1翻/DF2降/DF3稳PD-L1[147]

定义Writers=写入、Erasers=擦除、Readers=识别m⁶A。W：METTL3催化、METTL14-RNA平台、WTAP稳定位核斑；MACOM=VIRMA/KIAA1429(支架)、RBM15/15B(XIST)、ZC3H13(核定位)、CBLL1/Hakai(非催化/WMM未知)。WTAP-Hakai/Hakai-VIRMA为复合体；CBLL1-RBM10=3项二元；Hakai另为E3。METTL3：BMDM-STAT1→M1；TGFβ-NK-SHP-2/IL15→抗肿瘤；T细胞KO-SOCS↑/IL7-STAT5↓，Treg-KO→自身免疫。METTL16=U6/MAT2A边界；PCIF1=m6Am排除；FTO/ALKBH5=E(FTO亦m6Am)。R：YTHDF1=eIF3/AGO2-翻译/降解(DC-CD40/80/Tirap/cathepsins)；YTHDF2=CCR4-NOT→lnc-Dpf3/MAP2K4/MAP4K4/IFNB降解；YTHDF3协同翻译/降解；YTHDC1=核内剪接/输出；IGF2BP1/2/3稳mRNA(IGF2BP2-KH3/4+HuR/MATR3)；HNRNPA2B1为R。[148][149][150][151]

**Writers**
Writers负责把m⁶A写入RNA。METTL3以SAM为供体催化甲基转移并释放SAH；METTL14本身催化失活，却稳定METTL3并参与RRACH识别；约875 kDa复合体还含WTAP、VIRMA/KIAA1429、CBLL1/HAKAI、RBM15/15B和ZC3H13。[152] WTAP调控核斑定位；RBM15/15B是RNA结合及招募因子并关联METTL14；ZC3H13连接WTAP与RBM15/15B且为甲基化所需；CBLL1/HAKAI与WTAP、VIRMA互作稳定复合体，E3活性并非该功能所必需。[152][153] ZC3H13的直接功能证据来自2018年小鼠胚胎干细胞；当前没有这些辅助成员在NK、DC、巨噬或T细胞中的直接RNA—表型链。[152]

**Readers**
YTHDF1促进翻译并与eIF3关联，YTHDF2经CCR4–NOT促进降解，YTHDF3兼有翻译/降解；YTHDC1在核内识别Xist、HOTAIR、eRNA、HSATIII和LINE1，关联BRD4凝聚体、NCL/KAP1及剪接/沉默；YTHDC2促进翻译。[152][153] IGF2BP1结合m⁶A修饰的MIR210HG，并可通过PEG10–PABC1稳定RNA；IGF2BP2稳定DROSHA、TSC1/PPARγ，2021年小鼠研究指向M2形成，并与CD274/PD-L1稳定性相关；IGF2BP3以m⁶A依赖方式结合CD274，亦稳定CCND1/VEGFA。[152] HNRNPA2B1识别m⁶A参与剪接，并与DROSHA-DGCR8促进pri-miRNA加工；eIF3是非典型效应因子，可直接结合5′UTR-m⁶A并与YTHDF1/3关联。[152] HNRNPC是间接reader：m⁶A-switch开放MALAT1 A2577邻近poly-U；该资格仅见于2025年12月3日未同行评议预印本，不宜列为核心。[153] 除IGF2BP2的巨噬细胞结果外，当前证据未建立上述蛋白在四类指定免疫细胞中的直接链，不能外推。[152][153]

Writers：METTL3催化/METTL14平台；WTAP定位/招募，VIRMA/KIAA1429偏3′UTR/终止密码子，RBM15/15B→XIST，ZC3H13桥接RBM15–WTAP，CBLL1/HAKAI伴随。[49,51] METTL3/14受抑→IFNβ稳、ISG↑、HCMV↓；RBM15→CXCL11稳/M2，PRMT1–CNOT4促降解。[155] Erasers：FTO/ALKBH5→mRNA m⁶A；ALKBH5经DDX46至TRAF3/6/MAVS→核输出/翻译↓；ALKBH3仅tRNA。[49,51] Readers：YTHDF1/2/3翻译/降解/协同（争议），YTHDC1/2识别；YTHDF1伙伴eIF3b/YTHDF3/eEF2/IGF2BP3，m⁶A-SOCS3→JAK2/STAT3↓；DC敲低→呈递/CD8⁺T；缺失→ICB↑/瘤↓/CTL↑/MDSC↓。[154] YTHDF3与PABP1/eIF4G2→FOXO3翻译→IFN/ISG↓，缺失→ISG↑抗病毒。[155] IGF2BP1-3稳/翻译；HNRNPA2B1→Drosha/Pasha→pri-miRNA；直/间接reader争议。[49,51]

本组综述把 m⁶A 调控分为 Writers、Erasers、Readers；Readers 将标记转成 RNA 剪接、核输出、稳定/降解或翻译，免疫方向随细胞状态而变。[156]

**Writers**：METTL3–METTL14 是核心：METTL3 用 SAM 在 DRACH 催化腺苷甲基化，METTL14 结合 RNA 并稳定结构，WTAP 负责定位和稳定；VIRMA/KIAA1429、RBM15/15B、ZC3H13、CBLL1 为调节、支架或接头。METTL16（U6、MAT2A）、METTL5（18S rRNA）、ZCCHC4（28S rRNA）是底物不同的替代酶；T 细胞中 Mettl3/Mettl14 缺失损害 CD4⁺ T 细胞稳态，Wtap 缺失降低 TCR-β；METTL3 目标线索包括 SOCS1/3、CISH、TCF1、Foxp3、Tbx21 和 IL7Rα。RBM15、ZC3H13 仅有复合体角色，未给出独立免疫靶标或直接互作；RBM15B 图注未单列、正文列入 RBM15/15B，单独机制未确立。[156]

**Erasers**：FTO 经 hm⁶A 再生成 A；ALKBH5 直接将 m⁶A 转为 A，偏定位于细胞核并作用于 mRNA。感染模型中 FTO 缺失使 CD8⁺ T 细胞 Fas 高甲基化、扩增/存活及 TNF 下降；ALKBH5 缺失在小鼠 CD4⁺ T 细胞结肠炎和 EAE 模型中使 Cxcl2/Ifng 更高甲基化而不稳定，在 γδ T 细胞中使 Jagged1/Notch2 不稳定并促进扩增分化。[156]

**Readers**：YTHDF1/2/3、YTHDC1/2、IGF2BP1/2/3、HNRNPC/A2B1/G；主要关联翻译/降解、剪接/核输出、RNA 稳定、前体加工/可变剪接；PRRC2A 及 FUBP3、FXR2、L1TD1、DDX6 为补充或预测候选。WTAP-m⁶A-PDCD1 通过 YTHDF1（而非 YTHDF2）增强翻译，并抑制肿瘤浸润 CD8⁺ T 细胞增殖及 perforin、IFN-γ、GZMB、TNF-α；YTHDF2 与 IKZF1/3 互作，并促 TNF、Gata3/Smad3 等 mRNA 降解以维持 CD8⁺ T 细胞线粒体适能；IGF2BP1 稳定肿瘤细胞 CD274/PD-L1，HNRNPA2B1 稳定 NSCLC 的 LDHA，均削弱 CD8⁺ T 细胞杀伤。后两类主要来自肿瘤细胞和共培养模型。[156]

METTL3/14=MAC；WTAP/VIRMA/ZC3H13/HAKAI=MACOM；RBM15招RNA，VIRMA定3′UTR，ZC3H13促活，HAKAI稳机；免疫未报[157]

Writers：METTL3–METTL14为催化异二聚体；WTAP、VIRMA/KIAA1429、ZC3H13、RBM15、RBM15B、CBLL1/HAKAI为定位、桥接或稳定组分[158]。METTL14–METTL3介导哺乳动物核RNA m⁶A（2014）；VIRMA富集3′UTR/终止密码子附近并关联替代加尾（2018）；ZC3H13桥接RBM15/Spenito–WTAP/Fl(2)d（2018）；HAKAI仅有拟南芥E3证据（2017）；人writer复合体Cryo-EM证据发表于2022年[158]。WTAP为非催化支架：HEK293T共沉淀见其与METTL3/14/ZC3H13关系，但纯化蛋白显示不单独直接结合METTL3/14，VIRMA负责桥接。2026-06-02的HeLa研究显示，敲低或破坏WTAP四聚体降低m⁶A峰强（共同峰24,942个）、IQGAP1/KIF20A表达，使后期由32 min延至>90 min并出现染色体错位/桥接；RNA-seq为785个基因上调、127个下调，属于非免疫有丝分裂模型[158]。

Erasers：FTO主要底物为核RNA m⁶A（2011；未见免疫模型）；ALKBH5为哺乳动物RNA去甲基化酶（2013），影响RNA代谢和小鼠生育；ALKBH3仅有tRNA去甲基化（2017）。FMRP调节m⁶A标记mRNA稳定性并与YTHDFs相互作用（2018），尚未确立为核心reader，亦无直接免疫证据[159]。Readers：YTHDF1偏翻译，YTHDF2经CCR4-NOT降解，YTHDF3兼具两者；三者约85%序列相似且存在功能冗余。伙伴包括YTHDF1–eIF3/AGO2、YTHDF2–HRSP12/RNase P-MRP及YTHDF3–YTHDF1/核糖体/PABP1/eIF4G2/YTHDF2。免疫证据显示：YTHDF1影响DC中cathepsin翻译、抗原呈递和CD8⁺交叉启动；YTHDF2参与NK抗肿瘤/抗病毒免疫及LPS炎症；YTHDF3以非m⁶A依赖方式翻译FOXO3并抑制ISG；YTHDF1的IFITM1与ADAR1结果相反，YTHDF2缺失可升高IFN-β/IL-6，提示作用依模型和刺激而变[159]。

在本组允许来源中，canonical Erasers 是 FTO 和 ALKBH5，均催化 RNA m⁶A 去甲基化；ALKBH3 的天然主要底物是 m¹A/m³C，因此不能仅据本组证据列入 canonical m⁶A Erasers。[160][53] FTO 的 Ser229 位于活性口袋入口，可能以 m⁶A 核糖 2′-OH 氢键识别 RNA，并可观察到 hm⁶A 中间体；其 m⁶A、m⁶Am 和 m¹A 去甲基化发生于细胞核和胞质。[53][163] ALKBH5 参与 RNA 代谢、mRNA 稳定性、剪接、翻译、核输出和可变多聚腺苷酸化；其 DSBH 域与 DDX3 的 ATP 域相互作用，而本组未给出 FTO 的蛋白伙伴。[161] 重组蛋白—牛 mRNA 体外实验（n=3）支持 ALKBH5 去除 mRNA N6-meA，但不是免疫细胞证据。[48]

FTO 的免疫结果需保守表述：2025 年研究题名将其与 Th1 分化和感染免疫相连；列举的 2023 年研究题名报告其负向调节 NK 细胞细胞毒性，2020 年研究题名报告其促进 M1、M2 巨噬细胞激活；本组摘录未给出目标 RNA、刺激条件或 m⁶A 读出。[162] ALKBH3 在 PANC‑1 和体外翻译体系中去除 tRNA N6-meA、增强翻译，但不去除 mRNA N6-meA；故是边界候选，不能外推为免疫 Eraser。[48][53]

Writers 的基础复合体由 METTL3、METTL14 和 WTAP 构成；METTL3–METTL14 可介导哺乳动物核 RNA N6-腺苷甲基化，WTAP 是复合体组分；本组尚未单独证明三者的免疫目标或蛋白伙伴。[160][163] Readers 中，HNRNPC 是无 YTH 域的非经典 reader：m⁶A 使 RNA 双链失稳（0.5–1.7 kcal/mol），研究提出 MALAT1 A2577 甲基化可暴露 U-tract；甲基化发夹亲和力约增 8 倍，并报道 2798 个高置信 m⁶A-switch。这是 RNA—蛋白结合而非蛋白—蛋白互作，且非免疫模型。[160] HNRNPA2B1 在本组仅有 2015 年文献题名线索，不能写成已证实的免疫机制。[160]

FTO/ALKBH5：canonical m⁶A Erasers；ALKBH3偏好m¹A/m³C，野生型不识别m⁶A，故不列入canonical Eraser（D194缺失/Thr133突变体才出现部分活性）。[164][54][165]

FTO：N端DSβH催化、C端增强；去除mRNA/snRNA m⁶A/m⁶Am、tRNA m¹A，体内外催化并影响mRNA剪接；m⁶Am影响5′端稳定/DCP2抗性。底物有冲突（仅m⁶Am或内部m⁶A），随区室/细胞系变化；未给直接互作或四类细胞证据。病毒中FTO或ALKBH5缺失伴IFN快周转、病毒滴度升。[164]

ALKBH5：主要核内去除ssRNA m⁶A，亦作用于rRNA二甲基腺苷；结构/突变显示K132A降活性、R130失活；体外效率0.098 μM⁻¹·min⁻¹（2024-01-11）。DDX46–ALKBH5为功能通路（非直接结合），使IFN转录本去甲基化、核滞留抑IFN；HCV无效、Zika增滴度/蛋白、VSV敲低降RNA，未有NK/DC/巨噬/T直接证据。[164][54]

METTL3/14：HBV写入病毒RNA m⁶A→表达/逆转录；HIV-1耗竭→复制受抑；无四类细胞或互作直接证据。YTHDF2：KSHV裂解表达具细胞特异；与METTL14/ALKBH5参与EBNA3C甲基组重编程促肿瘤，属功能非直接互作；YTHDC1无本组功能/互作/四类细胞证据。[164] ALKBH5-PUF<500 nM特异，高浓度脱靶。[165]

Readers识别m⁶A并改写RNA命运；成员YTHDF1/2/3(Y1–3)、YTHDC1/2、IGF2BP1/2/3(I1–3)，非经典HNRNPA2B1、HNRNPC/G、eIF3。Y1-eIF3A/B/核糖体→翻译；Y2-CNOT1→CCR4–NOT→去腺苷酸/降解；Y3协同Y1翻译、Y2衰减并招eIF4G2翻译circRNA；HeLa提示分工/靶标重叠。YTHDC1调剪接/核输出（CPSF6、SRSF3/7），YTHDC2联小核糖体/XRN1；I1–3识别GG(m⁶A)C→RNA稳定/翻译（CPT1A/EphA2/VEGF，癌模）。HNRNPA2B1直接结合m⁶A→剪接，HNRNPC识别U-rich结构开关，HNRNPG招Y2；eIF3为Y1翻译复合体，直接方法未述；FMRP仅FMR1神经元线索，免疫/机制未知。[166][167][168]

Writer复合体：METTL14为METTL3 RNA支架并增强催化；WTAP无催化、互作METTL3/14；RBM15/15B结合METTL3/WTAP招募复合体；ZC3H13结合WTAP稳定核斑点。METTL14缺失TAM→EBI3-m⁶A改变→CD8浸润/抗肿瘤↓；ZC3H13↓→DUSP9-m⁶A↓→p-ERK→小胶质M2。ALKBH5去甲基化调mRNA输出/代谢，CRC经AXIN2–Wnt/β-catenin/DKK1增MDSC、减NK/CD8⁺T。[167][168]

免疫读出：Y1→WWP1→NLRP3泛素化→抑脓毒症焦亡；Y2/RBM4→STAT1降解→抑M1-TAM抗肿瘤；YTHDFs降解HIV-1m⁶A RNA。GC外泌体THBS1→IGF2BP2-m⁶A→Vγ9Vδ2T RIG-I样信号/细胞毒性↑，I2-circQSOX→Treg↑、CD8⁺T↓；IGF2BP3经HNRNPC/circZBTB44→HK3稳定→RCC M2↑。[166][168]

该2025年综述在TAM语境中将METTL3定为催化性Writer，METTL14为稳定复合体的辅助亚基，WTAP负责底物RNA定位/招募；VIRMA/KIAA1429、RBM15/15B、ZC3H13、CBLL1、METTL5、METTL16、ZCCHC4为效率/位点特异性相关组分。FTO、ALKBH5是主要Erasers；YTHDF1/2/3、YTHDC1/2是经典Readers，IGF2BP1/2/3结合m⁶A位点稳定靶mRNA；HNRNPA2B1、HNRNPC、FMR1、EIF3A、ELAVL1、G3BP1/2、PRRC2A、RBMX为非经典识别/效应因子。[169]

TAM中，METTL3/METTL14经m⁶A稳定STAT1、IRF5，偏M1；FTO/ALKBH5去甲基化并稳定STAT6、PPARγ、IL-10，偏免疫抑制性M2。[169] FTO依模型而变：TNBC中D-2HG抑制FTO→m⁶A↑→YTHDF1翻译ANGPTL4→JAK2/STAT3→M2；LUAD中稳定QPCT→CCL2→募集M2，ESCC中FTO降解反而减M2，矽肺中FTO↓促M1/糖酵解、减轻纤维化；胃癌/GBM亦有NNMT/CSF1促M2。[169] ALKBH5在HCC、GBM、NSCLC分别涉及MAP3K8、NEAT1/CXCL8、JAK2/CCL2/CXCL10轴；METTL3/ALKBH5共同调控CDCA4并经YTHDC2改变M1/M2。[169]

YTHDF1作用有条件性：其可增强抗原呈递/翻译；但在靶向纳米颗粒/光热TAM模型，沉默YTHDF1使STAT3↓、STAT1↑，M2→M1，IL-10↓、IL-12/IFN-γ↑、CD8⁺T浸润↑；YTHDF2偏免疫抑制性M2，缺失后激活IFN-γ–STAT1并增强抗原交叉呈递。[169] IGF2BP1稳定L1CAM-AS1，继而RAN–NF-κB–CCL2募集M2；circ_0020095竞争IGF2BP1并削弱IRAK1稳定、阻断M1；IGF2BP2促进CCL2介导的M2/SPP1⁺TAM募集；IGF2BP3稳定CCL5、TGF-β1 mRNA，增M2浸润并削弱CD8⁺T活化，胶质瘤外泌体circNEIL3也可稳定IGF2BP3并促免疫抑制。[169] HNRNPA2B1与METTL3功能协同促进pri-miR-146b成熟，并包装外泌体miR-184-3p；后者在TAM抑制JNK、靶向EGR1诱导M2。[169] AML条目仅为FTO靶向线索，未给免疫细胞、RNA目标或机制；上述链条也限于特定肿瘤/TAM或矽肺模型，不能外推为NK、DC或T细胞普遍规律。

Writers：METTL3结合SAM为催化核心；METTL14作RNA支架并与其成1∶1异二聚体；WTAP无催化活性、招募METTL3/14至核斑；RBM15/15B结合U-rich RNA定位复合体，VIRMA/KIAA1429指向3′UTR/终止密码子，ZC3H13结合WTAP使其留在核斑。METTL16另修饰U6-snRNA并调MAT2A；METTL3增强ISG并促进NK抗肿瘤，METTL14维持iTreg的FOXP3/分化功能。[170][171][172]

Erasers：FTO氧化去甲基化；ALKBH5直接去除m⁶A，改变ncRNA稳定性且方向依RNA/背景；ALKBH3主要作用于tRNA而非mRNA。[170][171]肿瘤模型中，ALKBH5经NEAT1/SFPQ/CXCL8、JAK2/STAT3/CCL2-CXCL10及AXIN2/Wnt/β-catenin/DKK1轴影响TAM/M2、MDSC、NK和细胞毒性CD8⁺T；不可外推为普遍规律。[170]

Readers：YTHDF1偏翻译，YTHDF2兼有降解/稳定性报道，YTHDF3促进翻译并与前两者协同；YTHDC1/2参与核内加工/输出及翻译稳定性。IGF2BP1/2/3识别GG(m⁶A)C并稳定/促翻译：IGF2BP1稳定c-MYC并关联免疫浸润；IGF2BP2参与THBS1-Vγ9Vδ2T细胞毒性及circQSOX-Treg↑/CD8↓；IGF2BP3稳定PD-L1/HK3，关联T细胞抑制/M2极化。[170][171]HNRNPA2B1促pri-miRNA加工、剪接成熟；HNRNPC/HNRNPG识别结构开关而非直接m⁶A；eIF3促m⁶A依赖ncRNA翻译；FMRP仅有m⁶A标记mRNA稳定性、无四类免疫细胞直接证据。[170][171][172]

m⁶A 蛋白分为 Writers、Erasers、Readers，分别写入、擦除和读取标记[173][174]。Writers：METTL3 催化；METTL14 与其 1∶1 异二聚、作 RNA 支架；WTAP 定位复合体；VIRMA 偏向 3′UTR/终止密码子；RBM15/15B 招募 U-rich RNA；ZC3H13 桥接 RBM15–WTAP；HAKAI 维持稳定[173][174]。METTL3/14 m⁶A 促进 Stat1/Irf1 降解；小鼠 CRC/黑色素瘤去除亚基，经 YTHDF2 稳定二者并增强 IFN、抗 PD-1[173]。FTO 去除 mRNA m⁶A/m⁶Am、tRNA m¹A；黑色素瘤敲低 FTO 增加 CD4⁺T 浸润及抗 PD-1/IFN-γ 杀伤，靶标含 PDCD1、CXCR4、SOX10[173]。Readers：YTHDF1/2/3、YTHDC1 直接识别 m⁶A；HNRNPA2B1/HNRNPC 经 m⁶A-switch；IGF2BP1/2/3、eIF3、FMRP 为扩展因子[173]。YTHDF1 联 eIF4G/eIF3 促翻译，YTHDF3 联 40S/60S 促翻译、亦促降解；辐射小鼠 DC 缺失 Ythdf1 增强 STING/IFN-I、交叉引发和 CD8⁺T 杀瘤，NSCLC 中 YTHDF3 稳定 PD-L1 mRNA、抑制 CD8⁺T[173][174]。IGF2BP 识别 GG(m⁶A)C、保护 RNA；其四类免疫细胞成员级因果链未见。METTL16（U6/pre-mRNA）、ALKBH3（tRNA）和 FMRP（神经输出）无直接指定免疫证据，保留候选[174]。

Readers：YTHDF1/2/3、YTHDC1/2、IGF2BP1–3、HNRNP识别m⁶A；YTHDF1翻译、YTHDF2降解、YTHDF3协同，YTHDC1剪接/输出、YTHDC2翻译起始/不稳；HNRNPA2B1→DGCR8加工m⁶A-pri-miRNA，HNRNPC/G为“m⁶A开关”，eIF3→5′UTR非帽翻译[175]。IGF2BP1–3稳定/翻译m⁶A-RNA，辅因子HuR/MATR3/PABPC1；IGF2BP2协同eIF4A，靶含MYC/DANCR，IGF2BP3直接结合circ_0003258；指定免疫链未确立[175]。Writers：METTL3–METTL14（METTL3催化、METTL14支架）；WTAP定位、RBM15连METTL3/WTAP、ZC3H13桥接、VIRMA导向3′UTR/终止密码子、CBLL1/Hakai稳定；METTL16修饰MAT2A/U6调SAM。Erasers：FTO、ALKBH5（ALKBH3亦有活性）；SFPQ招募FTO至CUGUG，ALKBH5参与mRNA输出[175]。DC中YTHDF1缺失促抗原交叉呈递并协同PD-L1阻断，模型未详；T细胞PD-1/肿瘤PD-L1受m⁶A调节，蛋白/位点未定[175]。

METTL3/14写入；RBM15/15B辅；YTHDF2经CCR4‑NOT促m⁶A靶降解；YTHDF3翻译降解；IGF2BP1–3稳RNA；HNRNPA2B1加工。[76,77]

eIF3：翻译/43S-PIC效应复合体，非已证canonical m⁶A Reader；13亚基/800kDa；直接eIF3f/h、b/g/i/j，另联eIF1/1A/5、TC、eIF3j/eIF4G（MS/IP）[176][177]；T细胞静息→激活时eIF3j解离→结合eIF3/40S[176]。

YTHDF1/2/3（Readers）：识别m⁶A；DF1–eIF3/AGO2→翻译/降解，DF2–CCR4-NOT/HRSP12-RNaseP/MRP→降解，DF3–DF1/2、核糖体、eIF4G2→翻译/降解；FMRP/Prrc2a协作[178]。85%同源/冗余，靶标未定。DC：DF1↓cathepsin翻译→抗原呈递/CD8交叉启动；NK：DF2→成熟/增殖/效应；巨噬：DF1-SOCS1、DF2-MAP2K4/MAP4K4/STAT1/PPARγ抑炎，DF1结果依模型反向；抗病毒：IFITM1、宿主/病毒RNA-RIG-I/IFNβ、FOXO3/PABP1/eIF4G2、JAK-STAT依条件[178]。

FTO/ALKBH5（Erasers）：去m⁶A；FTO（2020）促M1/M2巨噬激活，靶RNA及NK/DC/T机制未示；ALKBH5仅为RNA去甲基化酶[178]。

HNRNPC（C1/C2）非m⁶A Reader、无免疫模型；Y2H：SF3B2/PTBP2/自身/HNRNPD/RALY/CELF1=0.81/0.62/0.81/0.75/0.88/0.50。[179] Writers：METTL3催化；METTL14成二聚体；WTAP/VIRMA/RBM15/ZC3H13/CBLL1为非催化MACOM，负责定位/招募；VIRMA偏向3′UTR/终止密码子-APA，ZC3H13桥接RBM15–WTAP。[180][181] Readers：YTHDF1-eIF3翻译、YTHDF2-CCR4-NOT降解、YTHDF3协同；YTHDC1-SRSF3剪接/核输出（排SRSF10），YTHDC2互作小核糖体亚基/XRN1；IGF2BP1/2/3以KH3-4稳/翻译mRNA，IGF2BP2稳TSC1/PPARγ调巨噬，IGF2BP3稳CLDN4致巨噬抑制、稳KLK5；HNRNPA2B1以m⁶A-switch促pri-miRNA成熟/剪接。[181][182] FTO：PTC/TPC-1中pri-miR-139 m⁶A↓→miR-139-5p成熟↓、ZEB1↑；ALKBH5为RNA去甲基化；FMRP：RNA线索，m⁶A/免疫未证实。[183][184]

本批支持的分类是：METTL14、RBM15B为Writers复合体组分；FTO、ALKBH5为Erasers，但本批未给出二者的免疫目标或蛋白互作（FTO仅在HeLa中作未改变的对照，ALKBH5未被检验）。Readers包括YTHDF1–3、YTHDC1/2；eIF3、IGF2BP、HNRNP、FMRP属于非经典或候选效应因子。[55][185][56][186][187]

YTHDF1促进m⁶A-mRNA翻译；YTHDF2以C端结合m⁶A、N端定位并招募CCR4-NOT降解，HeLa敲低后靶RNA寿命延长；YTHDF3兼具翻译和降解功能，并与YTHDF1、EIF4A3及核糖体协作。YTHDF1/3的体外拉下和EMSA支持m⁶A结合，但不等于免疫因果。[55][185]

免疫链中，DC的YTHDF1缺失降低溶酶体蛋白酶转录本翻译，减少抗原降解、增强抗原呈递和T细胞反应。[185]巨噬细胞中，YTHDF2敲低在LPS模型稳定MAP2K4/MAP4K4并激活MAPK/NF-κB；另一报告指向Pyk2稳定性→MAPK/AKT活化，条件不同，不能合并为单一机制。[185][57]YTHDF3在小鼠腹腔巨噬细胞、RAW264.7和BMDM中结合FOXO3翻译起始区，直接互作PABP1/eIF4G2，促进FOXO3翻译并抑制ISG；缺失经IFNAR1增强抗VSV、EMCV和HSV-1，且该链不依赖METTL3-m⁶A。[187]

YTHDC1在核内识别G(m⁶A)C，招募SRSF3并排斥SRSF10，调节剪接和输出；YTHDC2兼具m⁶A稳定性、翻译桥和helicase功能，但其“reader”归类存在冲突，四类免疫细胞的直接证据不足。[185][56]METTL16主要修饰U6 snRNA和MAT2A发卡；体外U6结合KD全长为132 nM、甲基转移酶域为5200 nM、C端为814 nM，与YTHDC1仅有功能性关联，暂无直接免疫证据。eIF3与YTHDF2共定位不等于直接互作；EIF3C、IGF2BP3/SCD、FMRP/HNRNPG证据主要来自肿瘤或RNA加工，不能外推至免疫细胞。[55][56][186]

- **YTHDF家族（Readers）**：YTHDF1促进m⁶A-mRNA翻译；YTHDF2经CCR4–NOT直接促去腺苷化/降解；YTHDF3调节二者并双向影响翻译/降解。YTHDF1/3存在功能协作（如ANLN、TGFβR2/SMAD3），OGT可促进YTHDF1胞质定位；“三者共同促降解/功能可互换”与P-body解释并存。[188]

- **YTHDF1—DC**：放疗患者PBMC-DC及小鼠BMDC中，IR→STING/IFN-I→YTHDF1→cathepsins→STING降解，导致IFN-I和交叉启动下降；Ythdf1缺失增强CD8⁺杀瘤及RT±anti-PD-L1效果。RIP-qPCR、cKO bulk RNA-seq及IFN-β、ISG15、IFIT3、CXCL10为读出，但片段未给明确直接靶RNA；不同癌细胞系的IFN-I方向存在冲突。[58]

- **YTHDF1其他免疫模型**：YTHDF1促进PD-L1（3′UTR含GGACA-m⁶A）和VISTA翻译；耗竭可增加CD8⁺浸润并增强anti-PD-1。其介导的溶酶体mRNA翻译可降低MHC-I、促进抗原降解，减少CD4⁺/CD8⁺浸润；胃癌中成熟DC、MHCII、IL-12、IFN-γ/JAK-STAT1下降。siYTHDF1-CD47高表达sEV可使frizzled7翻译失活、阻断Wnt/β-catenin并增强TAM吞噬；另有EZH2–IL-6、p65/CXCL1–MDSC轴。Treg的m⁶A-c-Myc研究未指明reader。[188]

- **IGF2BP3**：IGF2BP家族属非YTH readers；IGF2BP3稳定并促进MYC、PD-L1、KPNA2、CDK4翻译。宫颈癌/HeLa-Parkin模型中，Parkin经IP/反向IP与其直接关联，在K213泛素化并促蛋白酶体降解；结合区为Parkin Ubl+Ring0+Ring1与IGF2BP3 KH1/2。IGF2BP3识别PARK2 3′UTR的GG(m⁶A)C并影响mRNA稳定性/mitophagy。MKRN2为既往功能伙伴；HUWE1、UBR、RNF、ARIH1、HECTD1、TRIP12、TRIMs仅是pull-down候选。Parkin与MKRN2的调控方向随癌种冲突，且未有免疫细胞证据。[59]

- **Writers复合体**：METTL14–METTL3为稳定异二聚体；METTL3催化，METTL14支持RNA结合并增强活性。WTAP稳固二聚体并定位核斑点，RBM15/RBM15B识别U-rich序列募集机器，VIRMA经CPSF5/6偏向终止密码子/3′UTR并可搭桥HAKAI–WTAP，ZC3H13稳固WTAP–RBM15并助核定位；RBM15B本组未有四类免疫功能证据。[60]

- **CBLL1/HAKAI**：其为MACOM非催化稳定因子；果蝇S2R+耗竭使mRNA m⁶A下降32%（Mettl3/14耗竭为59%），改变fl(2)d/Hairless剪接、5′剪接位点及内含子滞留；其稳定Vir/Fl(2)d/Flacc，RING结构域主要参与二聚和互作，S2R+中未证实E3活性。RNA非依赖IP/MS及Y2H支持Fl(2)d/Nito互作，Flacc未检出；人HeLa/U2OS中缺失HAKAI降低VIRMA而不降低RBM15，且无免疫功能证据。[60]

- **边界成员**：METTL16识别MALAT1三螺旋但体外不甲基化，全球m⁶A使结合减弱8倍；无免疫模型，保留uncertain。YTHDC1是核内reader（单m⁶A RNA的\(K_D=300\) nM，未修饰RNA无结合）并调节剪接；本组未列其蛋白伙伴或四类免疫证据。HNRNPA2B1仅有m⁶A依赖核RNA加工；FMRP仅见2023年神经元翻译经YTHDF1；ALKBH5仅见一般去甲基化及骨肉瘤pre-miR-181b-1/YAP，均不能据此填充免疫功能。[93,96,97]

Readers：YTHDF1翻译/抗瘤，YTHDF2稳[62]；YTHDC1m⁶A-lnc核出[189]；巨噬YTHDC2→ISG20→IFNβmRNA降、抗病毒↓[63]；HNRNPA2B1→DGCR8加工[192][64]；IGF2BP3→TRIM25/EGFRmRNA稳、Ago2关联[190][191]；eIF3非读者、FMRP未证[193][194]

eIF3非m⁶A读者、eIF3e↔eIF4G[196]；ALKBH5证据混合[65]；FMRP促核输出、结合弱[66][198]；YTHDF2促降解、YTHDF3翻译[199]

RBM15B（Writer 招募因子）结合靶 RNA 并参与 WTAP–METTL3–METTL14（WMM/MTC，另含 VIRMA、RBM15）复合体；HCC 中使 ITSN2 mRNA 获 m⁶A，IGF2BP1 经 RIP、敲低和 RNA 衰减实验识别并稳定它，促增殖、迁移、侵袭及裸鼠成瘤；IGF2BP2/3 敲低未复现。该链是 HCC 细胞/裸鼠证据，不是四类免疫细胞。[200] METTL14 与 METTL3 以 1:1 形成稳定复合体并增强写入，活细胞写入峰富集 RRACH；本组无其独立免疫靶标。[201][204]

YTHDF1/3 促翻译，YTHDF2 促 mRNA 降解，YTHDC1 调剪接，IGF2BP1/2/3 稳定 m⁶A-mRNA；eIF3 直接结合 5′UTR-m⁶A 调起始且不依赖 YTHDF1，YTHDF1 有报道与其互作；HNRNPA2B1 为候选 reader 并与 DGCR8 促 pri-miRNA 加工。[200][201] HIV-1 靶细胞中 YTHDF1–3 整体结合 5′leader-m⁶A，降低 gRNA、早/晚期逆转录及感染，敲低则提高感染性，不能归因单个成员。[202] 心肌细胞另见 YTHDF1–KLF11–HIF1α 轴调代谢适应/重塑，非免疫证据。[205] 砷-HaCaT 模型显示 METTL3-m⁶A 增强 YTHDF2 降解 SMAD7；FTO 去甲基化 PRR5 使其逃逸，DC-Y13-27 可部分逆转。[67]

FMRP 是非经典 reader 候选：小鼠神经祖细胞中经 CRM1 促 m⁶A-mRNA 核输出，靶含 Ptch1、Dll1、Dlg5、Fat4、Gpr161、Spop；Fmr1/Mettl14 缺失致核滞留，WT 可救援、ΔNES 不能。优先结合证据有冲突，且无免疫直接证据。[203]

FTO 核内主要去内部 m⁶A，胞质还去 cap-m⁶Am；亦作用于 snRNA-m⁶A/m⁶Am 和 tRNA-m¹A，后者可抑制翻译。HeLa/HEK293T/3T3-L1 敲低后 m⁶A/A 增 19.2/11.8/8.8%，m⁶Am/A 增 13.7/20.6/30.1%；AML 胞质 m⁶A 约增 40%。HeLa 过表达还浓度依赖擦除 RRACU/GGACU（DFFA、PPARD、VLDLR），但内部 m⁶A 基序识别有争议；C 端仅提示潜在伙伴。[68][204] ALKBH5 可去除 m⁶A，体外不严格依赖 RRACH；本组未证实其四类免疫细胞目标或伙伴。[201][204]

Readers/候选：YTHDF1/2/3、YTHDC1/2、HNRNPA2B1、HNRNPC/G、IGF2BP1/2/3；YTHDF1促翻译，YTHDF2经CCR4/NOT或HRSP12-RNaseP/MRP降解mRNA/lncRNA，YTHDF3协调；YTHDC1调剪接/核输出，HNRNP调m⁶A依赖剪接。[207][209]IGF2BP以KH-侧翼区结合m⁶A并稳/促翻译；IGF2BP3敲低使靶mRNA半衰期缩短近半；IGF2BP2复合物含HuR/MATR3/PABPC1，非IGF2BP3直接伙伴。[206]METTL14-METTL3为稳定复合体；HepG2敲低METTL14致1516基因m⁶A、418个mRNA下降，METTL3/14结合MYC-CRD。[206][209]ALKBH5/FTO去甲基；FTO：m⁶A→hm⁶A→f⁶A→A；免疫直接证据缺。[207]eIF3为m⁶A翻译效应候选、非典型reader；GEMIN5→m⁶A-FZR1，YTHDF2-eIF3f-DDX1为功能复合体，YTHDF3-eIF3a直接性不足；CD28促eIF3结合TCR-3′UTR并激活T细胞。[208]HNRNPA2B1依YTHDF2结合m⁶A-DNA:RNA杂交，属功能性非直接物理互作。[210]

Readers含YTHDF1/2/3、YTHDC1/2及EIF3A（非典型reader，直接结合m⁶A-mRNA调帽依赖/非依赖翻译）。[211]YTHDF1促翻译、YTHDF2降靶RNA稳定性、YTHDF3协同二者/核糖体蛋白翻译或降解；位点同异，YTHDF3与1/2各约60%共享靶标。[211]YTHDC1核内经SRSF3剪接/核输出；58特征SVM、HeLa/HEK293TCLIP（16,664位点/4,722基因）非免疫证据；FMRP为神经元YTHDF1线索；三者耗竭P-body稳定RNA且非严格依赖m⁶A。[211][70]

YTHDF1-3属Readers；靶重叠，DF2促降解、无互作[212]；ALKBH5稳Ogdh，DF2参与；缺失损害HSPC重建；YTHDC1仅白血病核内线索[213]。

eIF3：翻译效应复合体候选，非确证m⁶A Reader；参与48S起始，含eIF1/eIF4B/eIF5/eIF4G，直接结合eIF4G（975–1078 aa、非RNA桥），与eIF4A协同、非直接结合；T细胞结合TCRA/TCRB 3′UTR，促CD28依赖翻译爆发（原代1–2 h），增强T细胞活化/CAR-T杀伤，m⁶A依赖未证。[214][71][218] FMRP：RNA结合/翻译抑制候选，关联FXR1P/FXR2P/核仁素；神经元停滞核糖体促NGD，Id3半衰期增1.7倍；无m⁶A/免疫证据。[215][216][217][219] HNRNPA2B1：非经典m⁶A Reader候选；与DGCR8成复合体，促miR-92a-2-5p、miR-373-3p成熟；骨髓瘤模型关联溶骨病，直接互作方法未明。[220]

METTL3催化、METTL14激活、WTAP招募[222]；YTHDF2促降解/稳RNA[222]；HNRNPA2B1促miRNA加工[221]；eIF3翻译复合体[223]

METTL14为Writer，与METTL3复合写入核RNA m⁶A；HCC147例低67/高80，低表达预后差[225]。FTO、ALKBH5为Erasers，分别有AML、FOXM1胶质瘤证据；免疫直接证据未见；FTO/ALKBH5亦未富集测试circRNA[150,154]。eIF3为10–13亚基翻译复合体非Reader，与eIF1/5/4B/4G互作；刺激时eIF3j参与T细胞翻译，无m⁶A/免疫证据[224]。YTHDF1识别m⁶A-pri-miR-221；YTHDF2调Pyk2稳定性并抑制m⁶A-circRNA-RIG-I；YTHDF3促TLR4-mRNA降解，敲低增巨噬炎症/吞噬/杀伤[151,152,154,158]。YTHDC1稳AML-MYC-mRNA；HNRNPA2B1/HNRNPC关联circRNA；IGF2BP3连METTL3/PD-L1；Hakai为E3、FASN伙伴；eIF3D共现[152,154,155,157]

- METTL14（Writers）与METTL3成异二聚体：METTL3催化，METTL14活性位点退化，维持复合体完整性并结合底物RNA；C端RGG重复序列支持复合体活性，并参与mRNA修饰、剪接和稳定性。[227][229] MCF7敲低METTL14降低eRNA m⁶A、削弱YTHDC1/BRD4凝聚体，属非免疫证据；其与ALKBH5/YTHDF3仅有GeneRIF功能线索，直接性未明。[230][229]
- ALKBH5（Eraser）是核内RNA demethylase，目标含NANOG/FOXM1 mRNA及NEAT lncRNA；DDX3 helicase为报道伙伴但结合性质未明。[227] Lck-Cre小鼠胸腺γδT前体中，缺失提高Jagged1/Notch2 mRNA的m⁶A，降低稳定性和表达、抑制Notch，促γδT前体增殖分化及成熟细胞扩增，增强抗沙门菌保护；成熟γδT的IFN-γ/IL-17、增殖和凋亡不变，未报告蛋白互作。[228]
- FTO（Eraser）是核质穿梭的RNA demethylase；GSK3磷酸化Ser256后促泛素化和蛋白酶体降解，降低体内活性；MCF7中定向dCasRx-FTO去除TFF1e m⁶A削弱YTHDC1结合，尚无免疫细胞直接证据。[227][230]
- YTHDF2（Reader）识别m⁶A、促mRNA降解并被报道直接招募CCR4–NOT复合体；肿瘤微环境中调节巨噬细胞免疫抑制，并经YTHDF2/m⁶A/NF-κB轴调节肿瘤内Treg。[226]
- YTHDC1（Reader）参与mRNA剪接；在MCF7等模型，m⁶A-eRNA招募它形成凝聚体，促进BRD4凝聚体及增强子/基因转录，耗竭则抑制转录；BRD4为功能性共组装伙伴，非已证实直接二元结合，且未在NK、DC、巨噬或T细胞验证。[227][230] HNRNPA2B1仅获书目级“介导m⁶A依赖性核RNA加工”支持，未给出伙伴、目标或免疫功能。[230]

Readers含YTHDF1/2/3、YTHDC1、IGF2BPs、HNRNPA2B1，识别m⁶A并调翻译、稳定、降解、剪接[233]；YTHDF1促翻译，YTHDF2招CCR4–NOT降解，YTHDF3促翻译，IGF2BP稳定mRNA[233]。DC中YTHDF1促cathepsin→STING降解→IFN-I下降，缺失增强交叉启动/放疗控瘤[231]；ALKBH5调MCT4/SLC16A3并关联巨噬细胞CPT1A/M2；FTO去甲基化证据限肿瘤模型[231]；YTHDC1调SRSF3/SRSF10剪接，免疫证据未见[232]。

三类：Writers写入、Erasers擦除、Readers识别m⁶A；Writer复合体：METTL3催化、METTL14激活、WTAP募集、RBM15招募U-rich RNA、VIRMA/KIAA1429定位3′UTR、ZC3H13与WTAP/RBM15控核内甲基化，靶RRACH。[236]METTL14在巨噬细胞促Ebi3降解，增强CD8⁺T抗肿瘤；FTO/ALKBH5为主要Erasers；ALKBH5在CD4⁺T降低IFN-γ/CXCL2 mRNA的m⁶A，增稳定性及蛋白表达。[236]YTHDF1在DC增溶酶体蛋白酶翻译、减交叉呈递；YTHDF2招募CCR4–NOT降解m⁶A RNA，以STAT5/Eomes/Tardbp维持NK抗肿瘤并抑LPS巨噬炎症；YTHDF3待研。[45][236]YTHDC1/2属核内reader，免疫功能未证实；eIF3仅见于eIF1A/eIF5B的48S复合体，非确证m⁶A reader/免疫因子。[234][235]

METTL3（写入）催化m⁶A；METTL14识别GGACU、调MYB/MYC，二者1∶1结合；WTAP/VIRMA/RBM15/B/ZC3H13为组分，ZC3H13桥接RBM15–WTAP。[237][238] METTL16写入pre-mRNA、U6/lncRNA（边界）；CBLL1/HAKAI潜在。[238] FTO/ALKBH5（擦除）去m⁶A；ALKBH5经DDX46去甲基化MAVS/TRAF3/TRAF6、抑制IFN-I；病毒中METTL14/ALKBH5调节IFN-β/JAK-STAT，方向依条件。[238] YTHDF1（读取）–eIF3促翻译，YTHDF2–CCR4-NOT促降解，YTHDF3联结YTHDF1/2；YTHDC1招募SRSF3/7、NXF1；IGF2BP1-3经KH域借HuR/MATR3稳mRNA；HNRNPA2B1–Dgcr8加工miRNA，直读m⁶A争议。[237][238] 免疫读出：METTL3–STAT1促M1巨噬；METTL3–YTHDF1促DC的CD40/CD80/TIRAP翻译；YTHDF2调控IFNB/MAP2K4/MAP4K4；METTL3/14调节Tfh Icos；WTAP在ATM中稳定Idh1、促IDH1翻译。[237][239]

RBM33识别m⁶A RNA并招募ALKBH5；SENP1激活其去甲基化。[240]

METTL3催化写入，METTL14稳定复合体，WTAP定位/招募RNA；FTO/ALKBH5擦除；YTHDF1/2/3、YTHDC1/2读取；IGF2BP1/2/3结合m⁶A稳定mRNA。RBM15为补充因子；无免疫直接证据。[241]

YTHDF1/2/3涉翻译、降解、剪接及抗原呈递/炎症；无NK/DC/T成员级靶标或直接互作。TAM中，YTHDF1沉默使STAT3–STAT1偏STAT1、M2→M1、IL‑10↓/IL‑12/IFN‑γ↑/CD8⁺↑；YTHDF2促免疫抑制极化，缺失激活IFN‑γ–STAT1并增强交叉呈递，RNA/m⁶A位点未列。[241]

IGF2BP1稳定L1CAM‑AS1/IRAK1mRNA，分别促HCC CCL2‑M2招募、阻断CRC M1；IGF2BP3经circNEIL3稳定，且稳定CCL5/TGF‑β1，促TAM‑M2、抑CD8⁺活化；HNRNPA2B1包装miR‑184‑3p，抑JNK/靶EGR1诱导TAM‑M2，未证直接m⁶A机制。[241]

METTL14与METTL3成非催化异二聚体；RBM15招募RNA，ZC3H13连接WTAP–RBM15；YTHDF2招募CCR4–NOT促降解[242]。

METTL3催化写入；METTL14结合RNA并激活；RBM15/15B招募METTL3/14，CBLL1维持二者稳定；FTO、ALKBH5擦除。YTHDF1促翻译、YTHDF2促mRNA降解、YTHDF3促翻译；METTL14在缺血性卒中小胶质细胞中修饰Kat3b mRNA，YTHDF2在肺泡巨噬细胞降解Hmox1 mRNA。[243][244]

Writers：METTL3催化；METTL14稳结构/识底物；WTAP、VIRMA、CBLL1、ZC3H13、RBM15/15B辅助。RBM15/15B非催化，U富mRNA、WTAP依赖招募METTL3；RBM15–WTAP为SPOC/R834结合，ZC3H13不直结合；WTAP/ZC3H13定位；CBLL1证据未见[245][246][247]。METTL14缺失T细胞致结肠炎；METTL3–STAT1增稳促M1[247]。Erasers：ALKBH5在T细胞去m⁶A-CXCL2/IFNG→增稳、CD4/EAE炎症；感染巨噬中DDX46使Mavs/Traf3/6去甲基化→IFN-I与抗病毒受抑[247]。Readers：YTHDF1/2/3→CCR4–NOT降解；YTHDF2另接HRSP12/RNaseP、UPF1/DCP1A；IGF2BP1/2/3经KH稳RNA；RBM15→IGF2BP1/3→YES1/VEGFA为肿瘤功能/非直关联[245][246]。

METTL14识别RNA并稳复合体[249]；RBM15在果蝇经WTAP招募METTL3[249]；ZC3H13为Writer组分[248]；YTHDF2促RNA降解[248]。

Writers：METTL3催化；METTL14支撑RNA；WTAP定位；VIRMA定向3′UTR；RBM15/15B、ZC3H13、HAKAI为复合体因子。[250][265]

分子功能上，METTL3 是 METTL3/METTL14 异源二聚体的活性组分，METTL14 是促进底物 RNA 结合的非催化组分；该复合体可共转录地为数千条转录本写入 m⁶A，偏好单链 RNA 的 RRACH 背景。结构研究显示，两个 MTase 结构域组成的复合体需借助 METTL3 的 N 端 CCCH 锌指才能恢复活性，提示其有助于 RNA 结合。该页支持二者的共同复合体和纯化关系，但未以所示方法证明直接物理结合；证据主要来自结构生物学和重组蛋白体外甲基化。相关基础研究发表于 2016 年，原始 METTL16 研究在线发表于 2018 年。[266]

同一来源将 METTL16 区分为第二种、可单体发挥作用的 m⁶A 甲基转移酶：它偏好含 UACAGAGAA 非九聚序列的结构化 RNA，底物包括 U6 snRNA 和 MAT2A；高 SAM 时，MAT2A 3′UTR 发夹上的 m⁶A 被提出由 YTHDC1 参与其 mRNA 下调，低 SAM 时 METTL16 促进末端内含子剪接、增加成熟 MAT2A，形成反馈。METTL3/METTL14 主要作用于外显子，METTL16 还可结合内含子前体 mRNA 和结构化非编码 RNA；其底物识别及生理重要性仍未完全明确。[266]

Readers 方面，YTHDF2 作为 m⁶A reader 的 2017 年研究仅在母源转录组和卵母细胞能力模型中支持转录后调控；YTHDC2 的 2017 年研究支持其为 m⁶A 结合蛋白和 3′→5′ RNA 解旋酶，模型为哺乳动物精子发生和生殖系减数分裂，均非免疫细胞证据。YTHDC1 与 METTL16、选择性 N6-腺苷甲基化、mRNA 降解和 SAM 合成相关，但该页仅列出题名，未说明直接蛋白互作方法。[266]

另一项 2021 年 2 月 1 日发表、2021 年 11 月 16 日更正的原始结直肠癌研究（包括 2010—2015 年徐州医大附院 498 对组织及体外、异种移植实验）显示：在 HCT116/SW480 细胞中敲低 METTL3 会降低 HMGA1 mRNA 的 m⁶A、RNA 和蛋白表达；MeRIP/qRT-PCR 支持其稳定性调控。LINC00460 与 IGF2BP2、DHX9 的 RNA—蛋白结合由 pull-down、质谱、RIP 和 Western blot 支持；三者可能通过 IGF2BP2 识别 HMGA1 m⁶A 来稳定其 mRNA，并促进结直肠癌增殖和转移。IGF2BP2 的 reader 作用及该复合体关系均来自非免疫模型，不能外推为 NK、DC、巨噬细胞或 T 细胞机制。[253]

因此，METTL3、METTL14、METTL16、YTHDF2、YTHDC1、YTHDC2 和 IGF2BP2 在四类指定免疫细胞中的直接目标、作用方向和功能表型，不能由本组来源确定。[266][253]

**Writers。** METTL3（Writer）在2017年小鼠初始CD4⁺T细胞条件性敲除中，使整体RNA m⁶A约为WT的28%；Socs1、Socs3、Cish 3′UTR的m⁶A丢失，mRNA降解变慢、SOCS升高，抑制IL‑7/JAK‑STAT5，阻断稳态扩增、分化和退出初始态；野生型而非催化失活METTL3可救援，未见相关翻译或剪接改变。[75] METTL3还直接结合eIF3h，将m⁶A‑3′UTR接入闭环翻译；此作用不依赖催化活性或YTH readers，可增强数千mRNA翻译。[267] 骨肉瘤模型中，METTL3以m⁶A稳定RGS1 mRNA，促M2巨噬细胞及IL‑10/TGF‑β1释放；RGS1过表达可逆转缺失效应。[269] 另有题名线索指向STAT1 mRNA/M1极化，但无实验细节。[271]

METTL14是METTL3的催化核心异二聚体伙伴，复合体结合辅助因子WTAP。[270] 2020年小鼠T细胞特异性Mettl14缺失使Treg抑制失能、iTreg诱导由85%降至24% Foxp3⁺，伴RORγt下降和菌群依赖的自发性结肠炎；WT‑Treg回输可救援。研究未确定单一直接靶mRNA，且不支持外推至NK、DC或巨噬细胞。[270] T细胞表格链可概括为“METTL3/METTL14—Socs1/3/Cish—IL‑7/STAT5—扩增/分化”。[75]

**Eraser。** FTO仅在题名中被称为m⁶A demethylase；本片段无免疫模型或直接免疫读出。[268]

**Readers/效应因子。** YTHDF1约结合3600个m⁶A mRNA、提高核糖体占据，3′UTR tethering亦促报告mRNA翻译；与eIF3可能直接结合但功能依赖未证实。[267] YTHDF2与YTHDF1约共享50%靶标，通常继促翻译后促mRNA降解；热应激下可促HSP70翻译并被认为保护m⁶A RNA免去甲基化。[267] YTHDF3经YTHDF1间接加入YTHDF1‑eIF3复合体，也与eIF4G2/eIF3促环状RNA翻译，且不直接结合eIF3。[267] YTHDF1的DC抗肿瘤研究仅题名支持；eIF3可由m⁶A招募形成48S起始复合体（5′UTR、热休克），但结合亚基未知，属候选效应因子。[253,254] IGF2BP3条目（NSCLC/乳腺癌）涉及PD‑L1 mRNA、免疫逃逸和CD8⁺T反应，却未证明直接m⁶A识别；RBM15条目（喉鳞癌/胰腺癌）仅提示经IGF2BP3影响TMBIM6稳定性及巨噬细胞吞噬，均不足替代四类免疫细胞直接证据。[271]

Writers：METTL3催化m⁶A/RRACH；METTL14与METTL3直接成稳定异源二聚体，非催化维持复合体/底物RNA；WTAP无催化、作定位适配；VIRMA–WTAP互作并与METTL14-RGG直接结合；RBM15/15B选DRACH；ZC3H13、CBLL1/HAKAI为调节组分。[272][273][277]

METTL3免疫：小鼠ILC2（2023）Gata3高m⁶A，去甲→不稳；缺失→增殖/迁移/因子/抗蠕免疫↓（ILC1/3小）[274]。肥大细胞Il13-3′UTR-DRACH酶依赖→IL-13↓；急性下Tnf/Il13半衰期，Socs1/3/Cish未稳[276]。T1D人胰岛/EndoC-βH1、NOD鼠（2024）：OAS1/2/3、ADAR1 m⁶A；METTL3沉默→OAS稳定↑、过表达→病程延缓；ROS/NO、C276/C326-SNO参与[275]。T/巨噬题名[50]。

Erasers：FTO去甲基化/剪接；ALKBH5去甲基化/加工输出/核斑稳。Readers：YTHDF1翻译、YTHDF2-CCR4–NOT降解、YTHDF3互作1/2；YTHDC1剪接、HNRNPA2B1-miRNA加工、HNRNPC间接；YTHDC2 m⁶A翻译/非依赖解旋；IGF2BP2/3稳RNA/翻译，3-circNEIL3/巨噬抑制链未证；METTL16-U6/SAM、eIF3-METTL3环化翻译、FMRP-m⁶A降解均无免疫核心。[50][273][277]

METTL3→LLPS/招M14+WTAP[278]；METTL14—SMN→RNAPII、SMN↓→HeLa全局m⁶A↓约17%[80]；WTAP→核斑/募集[279]；VIRMA→3′UTR；ZC3H13→m⁶A[51]；METTL16→MAT2A/U6[281]；YTHDF1–3→reader[278]；METTL3→SOCS/CISH→T分化[282]

METTL3催化；METTL14与METTL3直接成异源二聚体，稳活性位点、助RNA识别；R298P降低甲基化/选择性，F429A降低复合物产量[284]。WTAP为调节亚基；其与METTL3/METTL14关联已验证，但共同PAR-CLIP、410个共同基因及RNA依赖核斑定位不能证明直接互作[283]。相关研究涉及METTL14缺失的肿瘤相关巨噬细胞—CD8⁺T细胞障碍/肿瘤生长及iNKT发育功能[285]。FTO为Fe(II)/2-OG氧化型m⁶A eraser，亦作用于帽邻近m⁶Am；mESC中LINE1去甲基化影响RNA丰度/染色质；BMDM经LPS+IFN-γ或IL-4极化时，FTO下调/抑制损害M1/M2极化并影响NF-κB、STAT1、PPARγ[271,275]。ALKBH5单步特异去除m⁶A；YTHDF1促翻译，YTHDF2招募CCR4–NOT降解m⁶A RNA并控制NK抗肿瘤/抗病毒免疫，YTHDF3协同二者，YTHDC1调节剪接/核输出[274,275]。

FTO敲低使感染RAW264.7巨噬细胞IL6/IL1β升高，涉FOXO1/NF-κB、无直接靶RNA[289]；FTO/METTL14/ALKBH5在MSC模型无效[288]；YTHDF2识别MCP1-m⁶A促降解[288]；YTHDC1卵母细胞剪接/APA[290]；FMRP非免疫促m⁶A核输出[291]；HNRNPC经m⁶A-switch结合[103]。

METTL3/14催化；WTAP/CBLL1复合体；RBM15靶向/ZC3H13核锚；FTO去m⁶Am[292]；ALKBH5→JAK2稳[293]；YTHDC1读Sxl[292]

FTO/ALKBH5为Erasers；鼠巨噬检出，未证参与ADAP–METTL3–Spry1。METTL14/WTAP为Writers；共沉淀证ADAP–METTL3，未证直连；RBM15检出[77]。ZC3H13桥RBM15–WTAP、Hakai稳机；YTHDF2招CCR4–NOT降m⁶A-RNA；YTHDF3促译降解；YTHDC1调剪接核输出[295]。肿瘤FTO结合DTX2/UFD1，去甲基化LIF促mRNA降解、减T杀伤；IGF2BP1/2/3敲低均降LIF稳定性[296]。巨噬IGF2BP2识别/稳m⁶A-Spry1，激活NF-κB增TNF-α、IL-1β、IL-6；IGF2BP1/3未同效[77]。TAM：IGF2BP3识别Snail m⁶A，eRF1/3功能调译，抑M2及癌进展[294]。

FTO（擦除）：HeLa RNA m⁶A过表达↓/敲低↑18/23%；缺失使Sm-snRNA m⁶Am/Am↑6.3×并改剪接；Huh7-HCV耗竭增颗粒（非免疫）[257][298][300][301]。METTL14：METTL3/14复合体非催化RNA定位；WTAP非催化[257][86]。RBM15–ZC3H13–WTAP桥接招募RNA，ZC3H13耗竭使METTL3/WTAP离核[298]。YTHDF2→CCR4–NOT降解m⁶A-RNA；YTHDF1/3结合，YTHDF3促翻译/降解；YTHDC1核内reader[257][299][302]。ALKBH5擦除/敲低增核mRNA、直靶未证；METTL16→U6/MAT2A；HAKAI仅植物，免疫待定[257][86][302]。

FTO→STAT1/PPARγ稳；METTL14→SOCS1稳；METTL16→MCP1降；ALKBH5→IL6抑炎；YTHDF2→p53→M2[294,297,299]

FTO/ALKBH5去mRNA-m⁶A；METTL14/WTAPWriter；RBM15/ZC3H13亚基；YTHDF1/2翻译/降解；IGF2BP1–3稳RNA。[305]

FTO体外先羟化m⁶A；METTL14结构/RNA识别；ALKBH5去甲基化；YTHDF2促降解，YTHDF3促翻译，YTHDC1核内读者[125,244,307]。

METTL14+METTL3写入；ALKBH5/FTO擦除；YTHDF1/2/3、YTHDC1读取；eIF3候选；四类免疫链未证实[264][307]


FTO在原代人NK（乳腺癌/健康）中经CRISPR敲除或meclofenamic acid抑制，考察NKG2D通路和毒性；2023年题名称其负调NK毒性。 LPS小鼠BMDM/RAW264.7中，FOXO1-GFAT2→OGT介导FTO-Ser95 O-GlcNAc→TRIM21-K48降解→Socs1 mRNA m⁶A↑、SOCS1维持、IL-1β/IL-6/TNF-α↓；FTO–TRIM21获IP-MS/Co-IP支持，KCTD10未确认。[260]


YTHDF1/2/3均识别m⁶A；tethering中YTHDF2去腺苷化最强，1/3较弱。YTHDF2以C端YTH结合m⁶A、N端直接结合CNOT1，招募CCR4–NOT（CAF1/CCR4A多为间接伙伴）促ACTB等RNA poly(A)缩短/降解；HeLa/HEK293为非免疫模型。[308]2021年题名支持YTHDF2控制NK抗肿瘤/抗病毒免疫；YTHDF1/3未见免疫直证。

METTL14是非催化RNA结合平台，WTAP/VIRMA为辅助组分；FTO、ALKBH5为m⁶A擦除酶。[309]FTO在3T3-L1中去甲基化m⁶A并促外显子跳跃。[261]

FTO（Eraser）在FTO−/−HEK293/HEK293T及Fto−/−小鼠肝中将snRNA帽邻近m⁶Am去为Am；缺失使m⁶Am-snRNA增多且更稳定并入snRNP，外显子纳入和剪接改变；m⁶Am活性近100倍于m⁶A，受2-HG等抑制，m⁷G可而TMG阻断。[262]非免疫模型。METTL16（候选Writer）写入U6-snRNA m⁶A并调节SAM合成酶内含子滞留；METTL3–METTL14写入核RNA，METTL3有髓系分化研究但T细胞证据未给；FTO/METTL16直接互作伙伴未给。[211,318]YTHDF1/3在HeLa促翻译，YTHDF2招募CCR4–NOT促降解；mESC中三者共同去腺苷化、单敲除可补偿，YTHDF1/3直接结合CCR4–NOT未定。[310]YTHDC1调控APA/剪接，YTHDC2为3′→5′解旋酶，ALKBH5调控长3′UTR mRNA剪接/稳定性；HNRNPA2B1 motif未富集；均无免疫直接证据。[318,211]

METTL14-METTL3复合体含WTAP[104]；FTO伙伴SFPQ、OGT、DTX2[313][314][315]；HNRNPA2B1读m⁶A、连DGCR8[316]

YTHDF1促翻译，YTHDF2促mRNA降解，YTHDF3协调二者；YTHDF2在NK/CD8⁺T增强效应，却在Treg/髓源抑制细胞维持抑制，具情境依赖。[317]

YTHDF1促翻译；YTHDF2招CCR4-NOT降稳；YTHDF3直互PABP1/eIF4G2、协YTHDF1/2促FOXO3翻译抑ISG；缺失抗病毒，非METTL3。[318]

YTHDF1促DC溶酶体酶RNA翻译→交叉呈递↓；YTHDF2降解CD19/HLA-DMA/B→T杀伤↑；YTHDF3促翻译/降解；FTO/METTL3未详。[319][320]

YTHDF1/2/3＝胞质reader；DF1→eIF3/翻译，DF2→CNOT1/CCR4-NOT、HRSP12/RNaseP-MRP降解，DF3兼二者，有争议；YTHDF2涉NK/DC/巨噬/Treg，DF3靶ZEB1→circ_KIAA1429-HCC。[321][333-335]核YTHDC1：XIST/MALAT1→SRSF3；YTHDC2 m⁶A结合不清；eIF3是应激m⁶A翻译reader。METTL14、RBM15/B、HAKAI为writer组分；METTL16边界；ALKBH5为eraser，无指定免疫直证。[322]

YTHDF1/2/3识别m⁶A：偏翻译/降解/兼具；YTHDF2-RACK1直互作[306]；TM感染巨噬细胞敲低YTHDC2使TLR2、TNF-α、IL-1β升高[323]

YTHDF1促翻译；YTHDF2促降解/RACK1/CCR4-NOT；YTHDF3协同/冗余；HNRNPA2B1加工/DGCR8-DROSHA；免疫未证[324][325]

2016年哺乳动物细胞中，YTHDF2识别m⁶A，经CNOT1直接招募CCR4–NOT，CAF1/CCR4A去腺苷酸化降解RNA；YTHDF1/3较弱。[311]

METTL14与METTL3成异二聚体并增强m⁶A写入[326]；90字符不足覆盖全部义务，需扩容或拆分所有权。

METTL14与METTL3/WTAP复合，调巨噬细胞/iNKT；FTO、ALKBH5调Socs/Dusp1；YTHDF1/2调Nlrp3/Eomes，依模型[328]

METTL14/3催；WTAP/VIRMA/ZC3H13/CBLL1组；RBM15/15B导；ALKBH5去甲；YTHDF/IGF2BP读HNRNPA2B1加工[348,350]

METTL14（Writer辅助/激活组分）与METTL3成异二聚体，增强催化/识别；调控C1q⁺巨噬细胞，缺失削弱CD8⁺T抗肿瘤并促瘤。[331]WTAP调节/招募亚基；RBM15与WTAP互作、为U-richRNA适配子；VIRMA/KIAA1429：3′UTR/终止密码子写入；ZC3H13与WTAP、RBM15桥接核内机器（2018），免疫未证。[331]VIRMA在乳腺癌与WTAP/FL2D、IGF2BP3经RNase不敏感共沉淀，稳定HAS2促迁移/生长；c-JUN/CDK1 m⁶A非依赖。[330]ALKBH5去甲基化；CD4⁺T中去除IFN-γ、CXCL2的m⁶A并增稳定/蛋白。FTO为Eraser，免疫未证。[331]YTHDF1促翻译；DC促溶酶体蛋白酶mRNA翻译，缺失增交叉呈递/肿瘤CTL。YTHDF2促m⁶A RNA降解；小鼠NK调STAT5/Eomes/Tardbp，稳态/成熟、IL-15存活和抗肿瘤/抗病毒；LPS巨噬敲低升IL-6、TNF-α、IL-1β、IL-12。[331]YTHDF3协同YTHDF1/2翻译/降解；YTHDC1剪接/miRNA；YTHDC2稳定/翻译/降解，免疫未证；HNRNPA2B1核内reader，免疫/伙伴未证；IGF2BP1家族稳定/翻译，免疫/伙伴未证；FMRP稳定m⁶A-mRNA，无免疫；IGF2BP3乳腺癌稳定HAS2。[330][331]

**Writers（续）**：METTL14 是非催化 writer 组分；缺少 SAM-binding motif，促 METTL3 结合 RNA[332]。小鼠 T 细胞缺失关联结肠炎、炎症浸润/Th1–Th17 因子增多及初始 T→iTreg 受阻；TAM 缺失致 CD8⁺T 障碍/肿瘤生长[332][333]。Treg 中 METTL3 缺失升 SOCS、抑 IL-2/STAT5；片段对功能方向一称损害稳定性、一称维持抑制功能，结论冲突[332][333]。WTAP 无催化活性、稳定 METTL3–METTL14；IL-7/STAT5/SOCS–T 稳态仅题名，不能归因 WTAP，未示免疫互作[332][333]。RBM15 仅列 writer，未示免疫机制[332]。

**Eraser**：ALKBH5 直接去 m⁶A、不产中间体；RBM33 识别 m⁶A RNA 并招募/激活它，PSPC1 经 K235 乙酰化招募它[332]。CD4⁺T 中降低 CXCL2、IFN-γ mRNA 的 m⁶A，增稳定性/翻译、促 Th1；NK、DC、巨噬直证据未示[332]。

**Readers**：YTHDF1 招募 eIF3 促翻译；T 细胞稳定 TCR-mRNA、增强激活及 JAK2 翻译；METTL3 旁证为 RORγt/STAT3→Th17[332][333]。DC 缺失增强抗原交叉呈递/CD8⁺启动并降低 cathepsin 翻译；敲低降低 CD40/CD80/炎症因子而小鼠敲除未见[333]。YTHDF2 结合 m⁶A 招募 CCR4–NOT；有 HRSP12 位点可内切；T 细胞涉及 SOCS3 稳定性/SOCS2 降解，CAR-T 还报告细胞因子受体 mRNA 稳定/翻译增强持续性[332][333]。YTHDF3 与 YTHDF1/2 协作促翻译/降解，以 FOXO3 翻译抑 IFN/ISG[333]。YTHDC1 结合 SRSF3 促剪接，四类免疫直证据未示[332]。IGF2BP 均属列出的 reader：IGF2BP1 仅肿瘤免疫线索，IGF2BP2 涉 AML 谷氨酰胺代谢/肾炎，IGF2BP3 涉乳腺癌 METTL3/PD-L1 轴抑免疫监视；均无四类细胞直链[332]。

METTL14/WTAP：写入复合体，RNA结合/招募定位；RBM15/HAKAI：写入相关；ALKBH5/YTHDF2：擦除/读取；免疫未示[334][335]。

RBM15招募METTL3/14并与WTAP同复合体；RBM15B作NXF1辅因子。[336]NIH3T3中RBM15促STYK1 m⁶A稳定、MAPK激活，非免疫证据。[337]

METTL3/14催化m⁶A；WTAP/VIRMA/ZC3H13/HAKAI为复合体组分；RBM15招募邻位RNA；YTHDC1读Sxl待证；均非免疫模型。[287][338]

METTL14、WTAP、RBM15B、ZC3H13、CBLL1属写入组；VIRMA与MTA/FIP37等共复合体；HAKAI缺失使拟南芥m⁶A降35%，E3未定[361,364]。IS中ALKBH5↓、YTHDF1未报、YTHDF2/IGF2BP1/2↑；YTHDF3-HLA-G r=.64、IGF2BP3-TNFSF4 r=.77相关[340]

METTL16写U6/MAT2A、无免疫证据[341]；METTL14缺失经YTHDF2稳Stat1/Irf1、增强抗PD‑1[343]；YTHDF1/3未证[343]。

METTL3(W)：NK缺失→SHP‑2/Ptpn11↓、IL‑15‑AKT‑mTOR/MAPK‑ERK↓，稳态成熟/细胞毒/抗瘤↓。[345] METTL14(W)：非催化支架，联METTL3/WTAP/VIRMA/RBM15/15B；HSV‑1 ICP0降解→IGF2BP3‑ISG15抗病毒↓；IGF2BP2稳E2F1(乳癌)；T细胞Ebi3/PDCD1效应依背景；WTAP为辅因子/核定位，RBM15/15B仅有定位证据。[344] HCC浸润NK(2021)中METTL14 mRNA↓49%，仅相关。[345] YTHDF1(R)：DC翻译蛋白酶转录本，耗竭↑抗瘤；YTH域结合AGO2并促mRNA降解。[346][347] YTHDF2(R)：TNFα‑Treg降解Nlrc3/Nfkbie/Traf3，维持NF‑κB/Treg；缺失↑CD8⁺/IFNγ抗瘤，NK有证据。[347] YTHDF3(R)：HeLa促翻译、免疫未证；YTHDC1(R)：DC交叉呈递↓、CD8⁺抗瘤↓。[345][346]

TP巨噬：METTL3→SOCS3-mRNA m⁶A→YTHDF1翻译↑→JAK2/STAT3↓炎症[348]；METTL14仅检测；METTL3/WTAP/VIRMA等复合体[374,376]；YTHDF2促CCR4-NOT/RNaseP-MRP降解mRNA，关联DC/巨噬/NK/Treg；YTHDF3促翻译/降解；YTHDC1促核输出/剪接[350]。

METTL14/METTL3写m⁶A；WTAP亚基；YTHDF2招CCR4‑NOT降RNA；YTHDC1-SRSF3/NXF1输出；HNRNPA2B1互作未证[377,378]

METTL14（Writer）与METTL3组成m⁶A复合体并参与pri-miRNA加工；免疫模型及更多直接互作未见[351]。METTL3可经STAT1mRNA甲基化促进M1巨噬细胞极化（2019），另有2021年NK抗肿瘤研究，但细节有限。FTO、ALKBH5（Erasers）在人NK中敲除后K562裂解/CD107a无显著改变；ALKBH5涉及NKG2D、ERK2、PRF1等，升高m⁶A仅降低mRNA；FTO缺失增强毒性的结果提示模型依赖。Readers中，YTHDF2招募CCR4–NOT使m⁶A RNA不稳定并参与NK抗肿瘤/抗病毒免疫；YTHDF3促翻译/降解，YTHDF1–3仅功能协同而非已证实直接互作[351][352][47]。YTHDC2与RBM46/MEIOC、核糖体亚基/XRN1相关，促CDS-m⁶A结构mRNA翻译；免疫证据未确立[351][352]。METTL16、RBM15及IGF2BP1/2/3仅有边界或癌症线索，尚无四类免疫细胞的直接机制证据[47]。

METTL14非催化支架/METTL3写入并沉默削弱IGF2BP2-PPARγ/TSC1；WTAP非催化；RBM15/B、VIRMA/KIAA1429辅助，互作未明；FTO/ALKBH5擦除；YTHDF1/2/3翻/降/翻；IGF2BPs：2稳TSC1/PPARγ、1无、3不变；HNRNPA2B1促pri-miRNA加工。[383,385,386,388]

METTL3写入m⁶A并促pri-miRNA加工；METTL14与其成复合体；YTHDF2促mRNA降解；HNRNPA2B1经DGCR8促加工；WTAP/四类免疫未证实[356]

METTL3/14写入NK-Prf1/Gzmb，双敲除影响抗肿瘤免疫[360]；乳腺癌中HNRNPA2B1经ALYREF/NXF1输出[357]；HNRNPG读m⁶A剪接[105]

METTL3为催化writer，METTL14为RNA平台，WTAP为调节亚基，共成m⁶A复合体。[361] METTL3缺失小鼠NK在IL‑15下Ptpn11/SHP‑2→AKT‑mTOR/MAPK‑ERK及杀伤↓；巨噬STAT1甲基化促M1。[397,398] METTL14：人CRC‑NK随SMAD4上调，靶RNA/因果未证；涉iNKT、C1q⁺TAM维持CD8⁺浸润/杀伤及CD8⁺激活。[396,398] WTAP涉TCR/存活；链未明。FTO稳定巨噬STAT1/PPARγ、YTHDF2拮抗；ALKBH5仅γδT发育。[362] YTHDF1：DC读溶酶体酶mRNA→抗原降解↑/交叉启动↓；YTHDF2：NK读Tardbp→NKG2D/GZMB/杀伤，DC调lnc‑Dpf3/CCR7迁移、巨噬调PPARγ、Treg连NF‑κB；YTHDC1仅SMAD4‑NK上调。[396,398] IGF2BP1结肠癌抑CD8毒性、HCC增浸润；IGF2BP2读m⁶A‑TSC1促M2；IGF2BP3促HCC巨噬M2、抑CD8并稳定PD‑L1 mRNA。[362] VIRMA/RBM15/ZC3H13属MACOM；CBLL1/Hakai为writer调节组分，仅与VIRMA共沉淀；HT29敲低m⁶A↓25%，TNF/IFNB1/CXCL1/CXCL8变；上清→PBMC/LPMC：IFNG/PRF1/GZMB↑、IL10/TGFβ↓，未证四类细胞因果。[363]

METTL14：复合体靶mRNA结合组分；成熟DC升高但无独立因果；肿瘤相关巨噬细胞缺失→CD8⁺T功能障碍/肿瘤生长[365][366][368]。WTAP：核斑点定位组分，成熟DC升高；Smad2/3共定位促复合体结合转录本，独立因果不足[365]。RBM15/15B招募复合体至mRNA/XIST；ZC3H13为组分；二者DC因果不足；ALKBH5为m⁶A去甲基化酶，指定细胞机制未示[365][366]。YTHDF1：maDC识别CD40/CD80/Tirap的m⁶A并促翻译；位点突变减结合、敲低降CD40/CD80；其缺失增强溶酶体蛋白酶翻译/抗原交叉呈递及CD8⁺T启动[366]。YTHDF2：招募CCR4–NOT降解m⁶A-RNA；巨噬细胞调Pyk2稳定性，原代CD4⁺T促CD40L降解，DC中无独立因果[368][369]。YTHDC2：致病Th17稳定ASH1L，降IL-17/IL-23R并抑自身免疫（模型限）；另有不同模型的METTL3-SOCS3方向冲突[369]。

METTL14(W)：巨噬Socs1m⁶A→YTHDF1→SOCS1翻译→抑TLR4/NF‑κB；连IGF2BP2–PPARγ/TSC1，T细胞缺失致初始滞留；FTO去Socs1m⁶A，FTO↑→炎症/脓毒症，证据仅巨噬。[370][372][78]YTHDF1结合Socs1(2/3/6)促稳定/翻译；IGF2BP1-3/YTHDC1-2/YTHDF2-3阴性；YTHDF3促翻译/降解。[370][371]IGF2BP2稳定m⁶A-PPARγ/TSC1，M2↑M1↓；IGF2BP1=0、IGF2BP3不变。[372]METTL3促T细胞SOCS1/3/CISH降解→IL7–STAT5→扩增分化；WTAP/VIRMA/RBM15/ZC3H13/CBLL1=writer组分；ALKBH5未证。[78][371]

METTL14和ALKBH5调Foxo3a、JAG1/Notch2、Ifng/Cxcl2；YTHDF1/2/3调Myc、NFκB、翻译/降解；其余免疫缺证[373][374]

METTL14等writer未证[377]；FTO→m⁶A↓；YTHDF1-3→T细胞RNA↓/YTHDF2→CCR4NOT[376]；IGF2BP1-KO→NK/髓系↑[377]

METTL14：RNA平台非催化[379]；RBM15招募复合体[380]；WTAP稳Foxo1促Treg；YTHDF1促翻译、YTHDF2促降解；IGF2BP2稳IRF7[382]

METTL14-METTL3稳RNA；WTAP促炎m⁶A翻译[385]；VIRMA/WTAP影响m⁶A、RBM15拟招募[383]；YTHDF1/3促IL6ST翻译[385]

METTL14：LUAD非OAS1/IFIT2 writer，免疫未证；METTL3写OAS/IFIT-m⁶A→YTHDC2稳定/翻译；ALKBH5→CDCA4→M2/LUAD；YTHDF1→EIF3C翻译，互作未证；YTHDC2 reader→OAS/IFIT/外泌体（LUAD非免疫）；IGF2BP1/3家族m⁶A→稳定/翻译，免疫未证[256]

METTL3–METTL14–WTAP–RBM15/15B–VIRMA/KIAA1429为Writer复合体：METTL3催化、METTL14结合RNA；其余为辅助，属共复合体非直接互作[387]。原代人hMDMs中METTL3/METTL14扰动均升TNFα，后者无独立TNF位点读出；Huh7感染时METTL14/ALKBH5入胞质，敲低METTL14增复制[107][386]。WTAP与ZC3H13（非催化）在TNF 3′UTR安装m⁶A（9处、两供体7处保守）；缺失降峰、稳TNF mRNA、升TNFα/P03，WTAP亦在炎症巨噬细胞升高；上清TNF依赖升ICAM1/VCAM1并伤肠屏障[107]。YTHDF2（Reader）读取并促TNF降解，缺失升TNFα；鼠巨噬细胞系不一致[107]。VIRMA偏向3′UTR/终止密码子并关联APA，未见免疫证据；RBM15/15B仅有复合体证据[386][387]。METTL16是边界Writer：HEK293 CRAC显示U6 reads 75%/70%（对照17%/27%），催化A43；La/LARP7/MEPCE为RNA依赖关联，未见免疫证据[387]。ALKBH5（Eraser）去m⁶A并影响mRNA加工/输出，无具体伙伴[386]。FTO（Eraser）按定位去m⁶A/m⁶Am/m¹A，SFPQ直接助选靶；HSV‑1时HNRNPA2B1-FTO关系减弱，CGAS/IFI16/STING mRNA保留m⁶A并增强输出/翻译及STING抗病毒信号[386]。YTHDF3促m⁶A RNA翻译/降解；HIV‑1中YTHDF1‑3结合gRNA并抑制逆转录[386]。

METTL14：METTL3/14非催化RNA结合亚基，写入mRNA/pri-miRNA DRACH；HeLa敲低m⁶A↓约40%，无免疫模型；巨噬仅有Spred2/Irakm线索[303][389][95]。WTAP定位核斑，VIRMA招募核心，RBM15/RBM15B、ZC3H13桥接；CBLL1/HAKAI组分，敲低m⁶A↓约23%；ZC3H13在OSCC稳定PLAU，未见免疫链[303][388][391][393]。ALKBH5：eraser；CD4⁺T缺失→IFN-γ/CXCL2稳定性↓；肿瘤PD-L1/Treg关联，NK/DC/巨噬未定[95]。YTHDF3涉翻译/降解；YTHDC1核reader，YTHDC2连核糖体/XRN1，FMRP候选[303][95][393]。DC：YTHDF1→CD40/CD80 m⁶A翻译↑；但摘要称YTHDC1抑制交叉呈递[92][391]。YTHDF1在X射线HEK293T经ATR-S182调核定位、SRSF2维持BRCA1/TP53BP1/RAD51剪接，与CRM1/SF3B1/3互作；CLIP直结合3129个含m⁶A转录本[392]。YTHDF2招募CCR4–NOT降解m⁶A RNA；METTL16偏结构化RNA，为边界候选[393][390]。

METTL14为METTL3适配因子；VIRMA耗竭降m⁶A；FTO偏m⁶Am；ALKBH5偏m⁶A[394]；YTHDF2招募CCR4-NOT降解RNA[395]。

LLC模型中，METTL14为m⁶A写入复合体主组分；其敲低降低HSD17B6 mRNA的m⁶A、提高稳定性，增强CD8⁺T细胞活化及抗PD-1反应。[397]

METTL14写→Myd88/NLRP3/iNKT；FTO擦→NK/巨噬；ALKBH5擦→γδT；YTHDF1-3读→翻译/巨噬[263][398]；IGF2BP1非免疫[399]

M14/WTAP/VIRMA/RBM15B写；YTHDF1翻译/2降解/3双效；METTL3-IGF2BP3稳ENO1-骨肉瘤；T/NK/DC/巨噬[446,447,449]

RBM15招募、ZC3H13桥接WTAP[401]；YTHDF1促DC翻译CD40/CD80/TIRAP，YTHDF2稳Pyk2、促降CD40L[403][404]。

METTL14支架；WTAP组装；VIRMA/RBM15/ZC3H13桥接；ALKBH5去m⁶A；YTHDF1/2降解；余者均无免疫直证。[405][406][407]

14年METTL3–METTL14写入核RNA m⁶A，WTAP非催化调节沉积[408]；21年C1q⁺TAM中METTL14–YTHDF2→Ebi3→CD8⁺T功能障碍[409]

METTL14助METTL3；WTAP稳复合；RBM15→Kdm6b→巨噬激活；FTO→ACSL4；ALKBH5→CXCL2→Th1；YTHDF→翻译/降解[410][411]

METTL14：结合靶mRNA/复合体[412]；WTAP：核斑点；T细胞Orai1/Ripk1不稳→存活[413]；RBM15：招募mRNA/XIST[412]；ALKBH5：去m⁶A，γδ/CD4⁺T，病毒冲突[327]；YTHDF1：DC促CD40/CD80翻译[412]；IGF2BP2：巨噬Spry1→NF-κB炎症；IGF2BP1/3阴性[252]。

RBM15B在肝癌写入ITSN2 m⁶A并由IGF2BP1稳定[414]；WTAP、ALKBH5、YTHDF1/3、HNRNPA2B1仅为免疫关联[415][416]

WTAP-VIRMA写入复合体[418]；IFNγ-MSC中WTAP/YTHDF1稳定IDO1等RNA并抑制T细胞[384]；IS关联[84]；HNRNPC为肿瘤证据[417]。

METTL3/ALKBH5→T耗竭；WTAP→PD1m⁶A/YTHDF1翻译→T耗竭[79]；YTHDF3→PGK1稳[419]；VIRMA非催；RBM15B-IPMS[76]

HNRNPA2B1-DGCR8促pri-miRNA；YTHDF2-P体降mRNA[420]；VIRMA-IGF2BP3稳HAS2[329]；VIRMA沉默→p53/铁死亡[421]

VIRMA/KIAA1429（Writers）为写入复合体支架，3′UTR/终止密码子m⁶A，调SIRT1、c-Jun、BTG2、KLF1/TFAP2A；与WTAP、METTL3/14为复合体关系，四类免疫细胞直接证据不足[364][422]。YTHDF2/3识别m⁶A降解DAPK3 mRNA，未拆分[422]。RBM15经ZC3H13桥接WTAP写入，非催化[364]。CBLL1/Hakai与VIRMA共沉淀；CRC沉默降低m⁶A并改变TNF/IFNB1/CXCL1/8，上清增强免疫标志物；四类非直接证据，预印本未评审[423]。

VIRMA写[424]；RBM15→KDM6B未报[429]；ALKBH5抗病毒[426]；YTHDF1翻/YTHDF2降/YTHDF3抗病毒[426]；YTHDC1剪接[428]

RBM15:RTE→NXF1输出[431]；RBM15B:H3K79me2→MTC→m⁶A翻译[430]；ALKBH5/FTO/YTHDF1/2/IGF2BP2免疫未证[430]

RBM15/15B经NXF1促RTE-RNA输出，未证实m⁶A免疫作用；HNRNPA2B1调剪接，HNRNPC敲低减轻LPS炎症。[432][433][434]

RBM15是Writer，协作METTL3/14/WTAP写入m⁶A，巨噬细胞促M1并升CXCL9/10[358]；HNRNPC为reader，敲低改善DSS结肠炎[435]。

RBM15→YTHDF1/2：KLF1↑/TRIM13↓[436]；IGF2BP3稳TMBIM6/VEGFA，招MDSC[378]；HNRNPA2B1读m⁶A→miR/IFN[425]

RBM15招募WMM至DRACH；YTHDF1促翻译，YTHDF2促降解，YTHDF3促翻译/降解；DC中YTHDF1促cathepsin翻译、抑制交叉呈递。[381][437]

RBM15：p53靶mRNA→m⁶A/稳定；FTO‑IT1拮抗（22Rv1 CLIP，4样本），非蛋白互作[438]。YTHDF1：eIF3A/B翻译、AGO2降解；YTHDF2：CCR4-NOT降解；YTHDF3协作DF1/2，PAN3降解/eIF2AK2-eIF3A翻译；HSC：PABPC1/eIF4G2→Ccnd1→重建，冗余争议[458,500]。YTHDC1核reader；IGF2BP1稳定PD-L1，抑制T/NK，四类内未证实[355]。RBM15B在MLL-r以H3K79me2招募MTC至MYC/HOXA9/BCL2，四类不外推[440]。METTL3/14/WTAP/VIRMA/ZC3H13/CBLL1仅类别/癌症线索；HNRNPA2B1/HNRNPC—RBMX为数据库关联[458,480,502]。

ZC3H13沉默→Spic mRNA稳定→NF‑κB/炎症↓[441]；CCND1m⁶A→IGF2BP1稳定[442]；Hakai-VIRMA互作/METTL3定位[443]

CBLL1/HAKAI：E3酶兼m⁶A写入复合物非催化组分；WTAP-IP含VIRMA/ZC3H13/RBM15，缺失损害沉积[258][444]。METTL16：非经典写入、U6-A43，免疫证据不足[445][446]。ALKBH5–YTHDF2抑制NLRP3；YTHDF3读Fmr1；YTHDC2稳AMIGO2；FMRP经YTHDF1调翻译[447]。

METTL16（写入候选）写入U6/MAT2A、参与剪接；LBR等共沉淀，非免疫模型，资格未定。[448]METTL3/14为Writers。[449]ALKBH5（E）去m⁶A，功能联结YTH/IGF2BP；巨噬细胞IL‑11、T细胞IFNG/CXCL2，方向依模型。[450][452][367]YTHDF1（R）协同稳定WNT2，促TAM M2化。[453]

ALKBH5为Eraser；RBM33/SENP1调其去甲基化[455]；CD4⁺T去修饰CXCL2、IFNG，促EAE[342]；PVT1/YTHDF2为功能轴[456]。

YTHDF1在DC促进溶酶体蛋白酶翻译；缺失增强交叉呈递[457]；ALKBH5缺失使ZDHHC3的m⁶A增加并降PD-L1[458]；YTHDF2在NK促抗肿瘤/抗病毒[457]

YTHDF1识别m⁶A并促翻译、与OGT/Crm1互作[459]；YTHDF2降解TAM的Stat1 mRNA[451]；YTHDF3促翻译/降解、YTHDC1调控剪接[460]。

YTHDF1[2024,DC/RT]：catA/B→STING↓→IFN-I、交呈、CD8杀伤↓；KO/抑制→抗肿瘤↑。[111]YTHDF3：m⁶A-reader，核糖体互作→翻译↑，与YTHDF1协同；无免疫证。[461]YTHDF2：HRSP12桥接RNase P/MRP→m⁶A-RNA降解（CNOT1）；LPS巨噬KO→促炎↓。[375,555]YTHDC1核剪/出（免疫未证）；HNRNPA2B1核加工；eIF3h翻译；METTL3写入/M1；FTO去甲；RBM15B/ZC3H13/IGF2BP1未证免疫。[375,554,555]

YTHDF1（Reader）识别m⁶A、促翻译并与YTHDF3协作；Treg中USP47调其翻译/c‑Myc，TAM中METTL3调SPRED2翻译，TEX高表达/抑CD8[462][463]。鼠肿瘤中，YTHDF1促组织蛋白酶翻译→新抗原降解，抑DC/CD8⁺T激活；缺失增强呈递、CD8/NK浸润及抗PD‑L1疗效[465]。YTHDF2促m⁶A‑RNA降解，YTHDF3调翻译/降解；冗余争议，免疫证据缺失[462]。FMRP‑YTHDF1互作仅见神经元[464]。METTL3为Writer；METTL14、WTAP、RBM15、RBM15B、CBLL1、ALKBH5与TEX生信关联，因果未证；FTO/ALKBH5为Erasers[463][465]。骨肉瘤RBMX敲除增强CD8⁺T毒性/浸润，非m⁶A证据[113]】【。

METTL3写GBP4-m⁶A，巨噬中YTHDF1促翻译/M1极化[466]；YTHDF2于CD4⁺T促TNF降解[375]；IGF2BP2仅有TSC1/PPARγ线索[467]

W/E无；Reader：IGF2BP1在BMDM肺纤维化中m⁶A依赖稳定THBS1-mRNA，经THBS1–TLR4互作促糖酵解/M2；NK/DC/T未证，无CRISPR救援[468]。IGF2BP3在胆囊癌/THP‑1巨噬中稳定CLDN4-mRNA、升STAT3/M2，机制待证不推NK/DC/T[470]。YTHDF3促FOXO3翻译抑制抗病毒；YTHDF2经CCR4–NOT降解m⁶A RNA[469]。YTHDF1、YTHDC1/2、METTL3、VIRMA、IGF2BP2未证；YTHDF家族有CD8⁺T ARE结合[297]。

YTHDF1促DC蛋白酶翻译、抑交叉呈递[312]；YTHDF3经PTX3促M2[94]；YTHDC2稳ASH1L抑Th17[94]；YTHDC1-SRSF3共沉淀[304]

YTHDF1促翻译[427]；YTHDF2经CCR4–NOT促降解，缺失使HSC炎症转录本升高[472]；YTHDF3兼具翻译/降解[471]；YTHDC1调剪接/核输出[427]

YTHDF2/读者 RAW264.7：IL‑6R‑m⁶A→降解→JAK2/STAT1/HMGB1炎症↓；CNOT1互作[473]；CD8T抗瘤↑、IKZF1/3互作[251]

METTL3促IFNB周转[396]；YTHDF2读m⁶A/NK抗瘤/TregκB/巨噬抑炎[476][474][255]；YTHDF3翻译[454]；YTHDC1剪接[475]

YTHDF3降解m⁶A-RNA、抑制I型IFN[477]；YTHDC1调控RNA[479]；FTO缺失使Fas转录本m⁶A升高，IGF2BP3促其稳定致CD8⁺T凋亡[478]。

YTHDC1为核内Reader，调控m⁶A剪接、APA和核输出[480][481][485]；与WTAP、FIP1L1互作[485]。四类免疫细胞直接证据未见[483][484]。

YTHDC1核读者：剪接/NXF1输出，SRSF3/10、hnRNPG、THOC7互作；YTHDC2读者：YAP-RNAm⁶A促翻译；四类免疫证据不足[486][487][488]

YTHDC2为Reader；YTH域体外结合m⁶A，U-rich解旋RNA；XRN1、MEIOC互作，RBM46共现；免疫机制未证[489][491]；HNSCC浸润[490]。

IGF2BP1：m⁶A依赖稳定YAP1mRNA，蛋白互作未证[493]；IGF2BP2：预印本reader稳定AR-V7mRNA[494]；IGF2BP3：免疫证据未见[74]。

癌症中IGF2BP1读取m⁶A稳定mRNA，ELAVL1为RNA依赖伙伴[254]；IGF2BP2稳定TSC1/PPARγ调巨噬激活；IGF2BP3调PD-L1/CD8⁺[495]

LPS小胶质细胞中，IGF2BP1为m⁶A reader，被推定稳定Gbp11/Cp mRNA并促炎；该研究未报告具体互作伙伴，未见NK/DC/巨噬/T直接证据。[609,614]

IGF2BP1稳c‑MYC/互作ELAVL1；IGF2BP2读m⁶A稳DANCR；IGF2BP3互作XRN2/USP10，促ULBP2降解削弱NK杀伤。[615,617,389]

IGF2BP1 PD-L1→逃逸[439]；IGF2BP2：Hk2稳→巨噬糖酵解[498]；IGF2BP3：免疫证据缺[402]；HNRNPA2B1：CRC稳TCF7L2[497]

METTL3/IGF2BP2/HNRNPA2B1→H19/miR-675；IGF2BP2→MTA1；IGF2BP3→GLS/GLUD1、EGFR；互作USP10。[625–630]

IGF2BP3是m⁶A reader，稳定HMGB1mRNA；Parkin直接互作、MKRN2调控；NK/DC/巨噬/T机制未证实[496][499][501][502][503]

HNRNPA2B1：m⁶A reader，METTL3→pri-miR-93→DGCR8；CDK6/miR-506、EV-RNA/NF-κB、SG(G3BP1/USP10/Caprin/VCP)[504][505][506][507]；免疫未证。HNRNPC：m⁶A-switch，SOX2/KHSRP/KLF5；METTL3机制未示，免疫未证[482]。

HNRNPA2B1：m⁶A-reader/胃癌NEAT1稳；HNRNPC候选reader/IRAK1稳、直识未定；eIF3：翻译因子非reader。[508][259][510]

NETs→METTL3→肺损；FTO四类缺证；ALKBH5→中性粒迁；eIF3a:m⁶A→B细胞；YTHDF2降解/3助[511]；eIF3:TCRαβ→T激活[512]

Writers/Erasers/Readers写入/擦除/读取m⁶A[73]；eIF3与40S/eIF4G相关，m⁶A reader未定[513]。METTL3–eIF3h增强翻译[513]；肝癌NK中METTL3mRNA低75%、缺失降m⁶A/NK效应，机制未明；巨噬细胞STAT1mRNA→M1[513][532][533]。YTHDF2非免疫翻译耐药[513]；FMRP直读神经m⁶A→CRM1核输出，肿瘤免疫抑制非m⁶A[359][514]；ALKBH5 Nr4a1/Notch2、GAS6/PEDV、HIV-1/IFN-I，冲突[110]。

ALKBH5（Eraser）：B16/CT26肿瘤细胞+GVAX/抗PD‑1；MCT4/SLC16A3 m⁶A↑→稳定性/表达↓→乳酸、Treg/MDSC↓、DC↑→疗效/生存↑；仅肿瘤—微环境证据，非免疫细胞内在，CD8不变/非IFNγ。[535]

Readers：YTH疏水裂隙识别m⁶A，IGF2BP为弱非经典结合者；MOLM‑13中METTL3抑制的组学/亲和实验仅示结合，不能证明四类免疫功能。[280]

METTL3：NK调IL‑15；γδT17测Stat1半衰期、方向未给；Treg中Socs3/Cish等m⁶A缺失→mRNA稳定、SOCS↑、IL‑2‑STAT5↓、抑制功能丧失。[515][528][526]

METTL14：早期NK前体→未成熟转换必需；缺失致NK减少，残余代谢↑却控黑色素瘤转移↑；SOCS3‑IL‑15/JAK‑STAT5或为机制，终末删无表型。[518]

METTL14综述：CRC‑TAM中EBI3 mRNA m⁶A降解↓→EBI3↑→效应T抑制；AML为PD‑L1/M2，宫颈癌乳酸→M2、DC呈递↓；非METTL3直接证据。[523]

FTO：NK去除SOCS3/SOCS1/CISH m⁶A，负调IL‑2/15‑JAK/STAT；缺失使脱颗粒、GZMB、IFNγ/TNF、杀伤/抗肿瘤↑，限于细胞因子激活。[515]

YTHDF2：TAM结合/降解m⁶A‑Stat1；缺失→Stat1稳定、IFNγ‑STAT1及抗肿瘤极化/交叉呈递/CD8↑，MDSC/DC/吞噬不变；Th9缺失→Gata3/Smad3稳定、IL‑9/21↑、CD8/NK浸润↑，非Th1/2/17/Treg。[521][517]

FTO缺失/NK-SOCS3-m⁶A→JAK/STAT→杀伤↑[516]；YTHDF2/NK-Tardbp→STAT5/IL15→存活/抗病毒↑[519]；YTHDF1缺失/DC呈递/CD8启动↑[520]；IGF2BP2/巨噬-TSC1/PPARγ→极化[353]；METTL14缺失/C1q-TAM-Ebi3-m⁶A↓→CD8障碍EBI3救援[530]

METTL14（Writer组分）：iNKT发育/功能↓；Cish为m⁶A靶标，敲低救援[527]；巨噬模型AMPKα–乳酸轴改表型，方向未明[534]。VIRMA/KIAA1429：HOXA1-3′UTR m⁶A稳定促NSCLC耐药（非免疫）[536]。YTHDF2：Gata3/Smad3 m⁶A→降解；缺失促Th9/抗肿瘤、CD4亚群不变[522]。YTHDF3：AP保护OR=.876，Treg中介6.18%（MR）[529]。YTHDC1：MIBC M2负相关、无因果[537]；YTHDC2：VSV巨噬经R3H–ISG20降解IFN‑βmRNA、抑晚期炎症[538]，亦有m⁶A非依赖模型[492]。综述称IGF2BP1促PD‑L1稳定、抑CD8/NK效应[400]；IGF2BP2以CCL2促M2募集，未测m⁶A[524]。ALKBH5仅AXIN2免疫抑制线索[400]；RBM15/B、ZC3H13、WTAP、YTHDF1、IGF2BP3本片无完整免疫机制。

IGF2BP2：巨噬细胞m⁶A阅读器，稳TSC1/PPAR促M2[531]；IGF2BP3：稳PD-L1抑CD8⁺T杀伤[525]；HNRNPA2B1：miRNA非免疫[509]。

METTL3 与 METTL14 形成稳定异二聚体，属于有结构和生化支持的直接物理伙伴；WTAP 是同一 m⁶A 写入复合体的辅助组分，但给定证据只支持复合体共组分关系，未单独证明 METTL3–WTAP 的直接二元结合。[272][270]

给定证据中，FTO 的蛋白关系主要是功能性调控：FTO 的 O-GlcNAcylation 促进 TRIM21 介导的 K48-泛素化降解，FOXO1–GFAT2 通路则在 LPS 条件下促进该修饰；没有给出 FTO 与 TRIM21 或 FOXO1 的稳定复合体或直接物理结合证据。[260]

YTHDF1、YTHDF2 和 YTHDF3 均与 CCR4–NOT 去腺苷酸化复合体有联系；YTHDF3 还与 YTHDF1、YTHDF2 协作，YTHDF1/3 可通过 eIF3a/b 或翻译机器促进翻译，YTHDF2 则通过 HRSP12–RNase P/MRP 等通路促进降解。[245][159][318] FMRP–YTHDF2 被描述为功能性关系而非直接物理结合。[199]

METTL14 与 METTL3 形成稳定异二聚体；METTL14 的 RNA 结合和 RGG motif 支持 METTL3 活性及其与 WTAP–VIRMA 的复合体关系，且该异二聚体具有盐耐受的稳定性。[119][272][126] METTL14 还直接接触 H3K36me3、H3K27ac 和 H3K4me3 等活性组蛋白标记，这属于直接染色质定位关系，而 WTAP 属于写入复合体辅助组分。[116][270]

RBM15 通过 RRM 结合 m⁶A 位点附近的富 U RNA 序列，并招募包含 WTAP、METTL3/METTL14 的写入复合体；这主要是 RNA 靶向和功能性招募关系，RBM15 本身不承担甲基转移催化。[117][123][140] 给定事实没有为其与每个核心亚基分别提供独立的直接物理结合实验。

ZC3H13 与 WTAP 存在相互作用，并作为核内、非催化的 RNA 结合适配组分参与 WTAP–VIRMA–HAKAI 写入复合体；其 LC domain 有助于复合体核内保留，敲低后核心组分的定位和 RNA 结合能力下降。[132][116] 这些证据支持 WTAP 互作及复合体功能，但没有把所有相关组分都证明为直接二元伙伴。

CBLL1/HAKAI 是非催化写入组分，在小鼠中与 RBM15、WTAP、VIRMA 和 METTL3 共纯化，因而支持同一复合体关系而非逐一直接结合。[126] 在拟南芥中 HAKAI 与 HIZ1、HIZ2 共纯化并被提出作为桥梁，但其 E3 连接酶作用仍未确定，因此该关系主要是共纯化和功能性模型。[339]

在感染巨噬细胞中，DDX46 通过其解旋酶结构域招募 ALKBH5，使 Mavs、Traf3 和 Traf6 转录本去甲基化；这支持功能性招募关系，但给定事实没有证明 DDX46–ALKBH5 的稳定直接二元复合体。[247] ALKBH5 在 T 细胞中的耗竭会降低 CD4⁺ T 细胞介导的结肠炎，说明其免疫功能证据强于其蛋白伙伴证据。[156]

YTHDF1 的明确伙伴关系主要指向翻译起始机制和核糖体，属于翻译效应复合体或功能性协作关系；家族层面还与 CCR4–NOT 等 RNA 降解通路相关。[118][245] 给定事实没有为 YTHDF1 与某一独立翻译亚基提供同等强度的直接二元结合证据，但其在 DC 中促进 CD40、CD80 和溶酶体蛋白酶 mRNA 翻译的因果读出明确。[412][185]

YTHDF2 直接招募 CCR4–NOT 去腺苷酸化复合体，并与 HRSP12 存在直接相互作用；HRSP12 再与 POP1 相互作用，把 YTHDF2 桥接到 RNase P/MRP。[245][349] YTHDF1 先促进翻译、随后 YTHDF2 触发降解属于功能性时序关系，而不是 YTHDF1–YTHDF2 已被证明的直接物理结合。[267]

YTHDF3 与 PABP1、eIF4G2 协作并结合 FOXO3 mRNA 翻译起始区域，属于翻译功能复合体关系；它还与 YTHDF1、YTHDF2 协作调节 mRNA 翻译和降解。[187][114] 这些证据支持协作和功能性招募，不能将所有协作都表述为直接物理结合。

YTHDC1 与 SRSF3 存在直接相互作用：YTHDC1 结合 m⁶A 外显子后通过其 C 端招募 SRSF3，SRSF7 也被列为剪接调节伙伴。[116][238] BRD4 与 YTHDC1 在增强子上共定位并有体外互作证据，属于功能性染色质伙伴；YTHDC1 还可把染色质相关 RNA 导向核输出或 NEXT 相关降解复合体。[230][116]

YTHDC2 与 XRN1、MEIOC 和 RBM46 存在复合体或功能关系，其中 XRN1 将其解旋活性与 RNA 降解联系起来；给定事实没有为每一对伙伴都提供相同等级的直接结合实验。[489] YTHDC2 还读取 METTL3 标记的 OAS、IFIT mRNA，或在致病性 Th17 细胞中参与 ASH1L mRNA 稳定性，这些是 RNA 目标关系而非蛋白伙伴关系。[256][369]

IGF2BP2 的主要已知关系是功能性 RNA 稳定轴：它识别 m⁶A RNA 并稳定 TSC1、PPARγ 或 Spry1 mRNA，继而影响 mTORC1、MEK/ERK 或巨噬细胞表型；这些证据不等同于 IGF2BP2 与这些蛋白的直接物理结合。[115][354][252] 在感染巨噬细胞中，IGF2BP2 还通过 Hk2 mRNA 连接 m⁶A 读取与糖酵解重编程。[498]

HNRNPA2B1 与 DGCR8 形成 Microprocessor 相关复合体，并通过 m⁶A 识别参与 pri-miRNA 加工；这是复合体和功能性关系，给定事实未进一步证明每个界面的直接物理性质。[220][119] HNRNPA2B1 的 m⁶A reader 身份存在争议：有研究支持直接结合 RGAC/m⁶A，也有模型认为是 m⁶A 引起的 RNA 结构转换提高邻近位点可及性。[114][117]

人类 eIF3 的 eIF3c、eIF3d 和 eIF3e 亚基与 eIF4G 直接相互作用，促进 mRNA 招募到核糖体；eIF4A 并不是维持 eIF4G–eIF3 稳定结合所必需的伙伴。[195][197] eIF3 与 YTHDF1 或 m⁶A RNA 的关系更适合表述为翻译效应或可能的读取协作，而 Jurkat T 细胞中 eIF3 对 TCRA、TCRB mRNA 的结合属于 CD28 依赖的功能读出。[152][71]

可核查的链条是：METTL3–METTL14 组成稳定的催化和底物识别异二聚体，WTAP参与复合体定位，VIRMA负责招募并把写入集中到 mRNA 3′端，ZC3H13增强核心酶的 RNA 结合；RBM15/RBM15B 通过 RNA 或染色质线索定位复合体，ALKBH5执行去甲基化。[119][117][116][140][440][161] 直接异二聚体、共组分、功能性招募、遗传干预和酶活性应分开标注，不能把共纯化或通路共现当作二元直接结合。

METTL3 在 T 细胞中通过 m⁶A 促进 Socs mRNA 的诱导性降解和 IL-7/STAT5 稳态；FTO 在黑色素瘤中去甲基化促进免疫逃逸，而在巨噬细胞极化中又是维持极化所必需；YTHDF1/2/3 分别偏向翻译、降解及协作，METTL14 则作为 RNA 结合和变构支架完成写入。[75][173][286][245][119] 这些结论分别来自条件性敲除、肿瘤模型、极化模型和复合体生化证据，成员方向受细胞背景限制。[276][212]

ZC3H13 是维持写入复合体核定位和 RNA 结合的非催化组分；CBLL1/HAKAI 是共纯化的非催化组分，但其特异免疫因果链仍有限；ALKBH5 在 CD4⁺ T 细胞和病毒模型中有去甲基化证据；YTHDF1 在 DC 中连接 m⁶A RNA 翻译、抗原处理和交叉呈递。[116][126][156][164][412] HAKAI 在免疫样本中的表达或肿瘤微环境关联不能替代 NK、DC、巨噬细胞或 T 细胞内的直接机制实验。[121][363]

YTHDF2 在 NK 细胞中调节 STAT5、Eomes 和 Tardbp，并在 TAM 中促进免疫抑制性极化；YTHDF3 在巨噬细胞中通过 FOXO3 翻译抑制基础 ISG，而 YTHDC1 主要调节核内剪接、输出和增强子 RNA 凝聚体。[331][187][238][230] YTHDC2 在致病性 Th17 细胞中通过 ASH1L mRNA 影响 IL-17/IL-23 轴，另有 OAS/IFIT 证据来自 LUAD 细胞而非指定免疫细胞。[369][256]

HNRNPC 可被视为 m⁶A 结构转换相关 reader，但给定模型是宫颈癌而非免疫细胞，因此不足以确立其为核心免疫 reader；eIF3 更有力的证据是翻译起始复合体，而不是典型 m⁶A reader；FMRP 与 YTHDF2 的关系被报告为功能性识别 m⁶A，未证明直接物理结合。[417][510][199] Writers 则通过 METTL3–METTL14–WTAP 安装 m⁶A，能够在 IRF3、IFNAR1 等免疫相关转录本上改变翻译或稳定性。[119][127]

FTO 的功能方向具有情境依赖性：在 LPS 巨噬细胞中，FTO O-GlcNAcylation 促进其降解，继而增强 Socs1 m⁶A 和 SOCS1 负反馈并抑制 IL-1β、IL-6、TNF-α；在黑色素瘤中，FTO 去甲基化促进肿瘤生长并削弱抗 PD-1 反应；在 NK 细胞中则应以 NKG2D 通路和细胞毒性实验作为表格读出，而不预设方向。[260][173]

YTHDF1 在 DC 中促进 CD40/CD80 和溶酶体蛋白酶 mRNA 翻译，但其缺失可减少抗原降解并增强交叉呈递；YTHDF2 在 NK 细胞中调节 STAT5、Eomes、Tardbp，在 TAM 中促进免疫抑制性极化；YTHDF3 在巨噬细胞中结合 FOXO3 mRNA并促进翻译，从而抑制基础 ISG。[412][185][331][241][187] 家族共同参与 mRNA 命运，但翻译与降解模型存在文献分歧，应在表中分成员记录。[212][245]

YTHDF1、YTHDF2 和 YTHDF3 应分别列出目标 RNA、效应复合体和最终功能，不能仅写成统一的 reader；它们虽有较高序列相似性并共享部分降解通路，但结合位点和下游作用可因转录本及细胞背景而异。[211][245] 例如 DC 的 YTHDF1、NK/TAM 的 YTHDF2 和巨噬细胞抗病毒模型的 YTHDF3 应作为不同证据行。[412][331][318]

WTAP 在病毒感染细胞中调节 IRF3 5′UTR 翻译和 IFNAR1 3′UTR 稳定性；在 hMDMs 中影响 TNF mRNA m⁶A 和炎症程序，NF-κB p65 还能在炎症刺激下促进 WTAP 组装与定位。[127][107][385] 现有材料没有给出 WTAP 在 NK 或 DC 内的同等直接目标，因此应把病毒和巨噬细胞证据与其他细胞外推分开。

WTAP 的最终功能方向取决于条件：病毒感染时 WTAP 降解降低 IRF3/IFNAR1 m⁶A并限制抗病毒反应，而巨噬细胞中 WTAP 缺失可提高 TNFα 和炎症程序；WTAP 四聚体受损还会降低整体写入和细胞增殖，但该后者来自非免疫细胞模型。[127][107][158] 表格中应注明刺激和模型，不能把 WTAP 统一标成单向促炎或抗炎。

VIRMA 的已知功能方向是促进区域选择性写入和癌细胞增殖，而不是已经确立的免疫细胞功能；VIRMA FL 过表达通过 WTAP/METTL3 轴提高 m⁶A并增强 HAS2 相关表型。[120][330] 表格可保留该机制作为核心蛋白背景，但不能把癌细胞增殖直接写成 NK、DC、巨噬细胞或 T 细胞的最终影响。

RBM15B 的最终读出是染色质标记依赖的选择性 m⁶A和致癌蛋白翻译，而不是已确立的免疫细胞激活或分化；敲低 RBM15B 会降低 MLL-fusion 靶基因 TWINS 区域的 m⁶A及 MYC、HOXA9、BCL2 相关转录本输出。[440][430] 因此表格应把白血病模型限制写入最终影响列，避免外推到四类指定免疫细胞。

HAKAI 的表格行应把非催化复合体身份、共纯化伙伴以及 TNF/IFNB1/CXCL1/CXCL8 等 RNA 读出分开，最终影响写成肿瘤细胞或微环境变化，而不是笼统的免疫激活。[126][363] 给定材料没有足够证据支持其对指定四类免疫细胞的统一方向。

ALKBH5 是 m⁶A 去甲基化酶；在 CD4⁺ T 细胞中耗竭或删除会降低结肠炎相关 T 细胞介导效应，在病毒刺激巨噬细胞中由 DDX46 招募并去甲基化 Mavs、Traf3、Traf6，在肿瘤模型中还可影响 AXIN2 或 JAK2 轴。[156][247][168][293] 给定材料没有提供其在 NK 或 DC 内的直接目标和终末功能，因此这些细胞应标为证据缺口。

ALKBH5 的功能方向依赖条件：T 细胞中删除会削弱结肠炎效应，病毒模型中的 DDX46–ALKBH5 轴抑制 IFN 转录本产生，而肿瘤细胞中的 JAK2 或乳酸相关轴可重塑免疫微环境。[156][164][247][535] 表格必须写清是免疫细胞内作用还是肿瘤细胞对免疫细胞的间接作用。

YTHDF1 在 DC 中识别并促进 CD40、CD80 和溶酶体蛋白酶 mRNA 翻译；其缺失减少抗原降解并增强交叉呈递，TAM 中沉默 YTHDF1 则可使 M2 向 M1 重编程。[412][236][241] T 细胞相关目标还包括 Socs family、Myc、Tcf7 和 Icos mRNA，但给定材料对这些目标的完整因果链较少，NK 细胞主要只有表达或通路关联。[373][121]

YTHDF1 的最终功能不是固定方向：在 DC 中耗竭可增强抗原交叉呈递和 T 细胞免疫，在 TAM 中沉默可降低 IL-10并增加促炎或抗肿瘤表型，而一般性 m⁶A RNA 翻译功能则会增强其目标蛋白表达。[236][241][412] 表格应按 DC、TAM 和其他模型分别列出，避免把翻译促进直接等同于免疫增强。

YTHDF2 在 NK 细胞中调节 STAT5、Eomes 和 Tardbp，促进 NK 功能相关 RNA 命运；在 TAM 中促进免疫抑制性极化，缺失可激活 IFN-γ–STAT1 并增强 CD8⁺ T 细胞抗肿瘤反应；在巨噬细胞样细胞中还可识别 IL-6R mRNA并促进其降解。[331][241][473] 其一般机制是招募 CCR4–NOT、HRSP12–RNase P/MRP 等降解通路，但具体方向仍依赖细胞背景。[245]

YTHDF2 的表格行应把 NK 的 STAT5/Eomes/Tardbp、TAM 的 IFN-γ–STAT1 重编程和巨噬细胞的 IL-6R mRNA 降解分别记录，并在最终影响列写出 NK 调控、TAM 免疫抑制或抗肿瘤重编程方向。[331][241][473] 不能把 YTHDF2 的 RNA 降解功能简单写成对所有免疫反应均有相同方向。

YTHDC1 是核内 m⁶A reader，可通过 SRSF3/SRSF7 调节剪接、介导核输出，并在 m⁶A-eRNA 上与 BRD4 形成增强子凝聚体；给定证据还包括 AML 或 PBMC 表达关联，但没有在 NK、DC、巨噬细胞或 T 细胞中提供完整的直接目标—功能链。[238][230][131] 因此其免疫部分应与一般核内 RNA 加工功能分开。

YTHDC1 的最终影响应写为 RNA 剪接、核输出或增强子转录调节，而不能把癌细胞或 PBMC 表达差异直接等同于免疫细胞激活。[238][230][131] 目前给定证据不足以为四类指定免疫细胞建立统一方向，表格应明确这一限制。

IGF2BP1 的最终影响应写成巨噬细胞炎症、THBS1–TLR4 信号和肺纤维化背景，而不是泛化为所有免疫细胞的激活；THBS1 与 TLR4 的物理互作是下游蛋白关系，不是 IGF2BP1 与 TLR4 的直接结合。[468] 表格应明确其证据来自巨噬细胞和疾病模型。

IGF2BP3 是 m⁶A reader/效应因子，可通过 GG(m⁶A)C 等识别并稳定 RNA；免疫相关证据包括肿瘤来源 circNEIL3 稳定 IGF2BP3 后促进 TAM 免疫抑制，以及 METTL3/IGF2BP3 轴影响 PD-L1 mRNA，但许多具体结合和翻译机制来自肿瘤或心肌细胞模型。[241][332][500] VIRMA/WTAP 与 IGF2BP3 的证据主要是共纯化关系。[330]

IGF2BP3 的最终影响应区分 TAM 免疫抑制、肿瘤免疫检查点和非免疫细胞的 MMP3 稳定等读出；不能把后者直接写成 NK、DC、巨噬细胞或 T 细胞功能。[241][332][500] 表格应注明其免疫证据主要位于肿瘤微环境，而非四类细胞内的统一机制。

HNRNPA2B1 可通过 m⁶A 结构转换或直接结合 RGAC/m⁶A 位点参与 RNA 加工，并与 DGCR8 连接 pri-miRNA 处理；HSV-1 模型中它还可转位并激活 I 型干扰素信号，TCF7L2/MIR100HG 轴则来自结直肠癌细胞。[114][220][316][497] 给定材料没有在 NK、DC、巨噬细胞或 T 细胞内建立完整的目标 RNA 和终末功能链。

HNRNPA2B1 的最终方向应按 RNA 加工、选择性核输出或病毒识别模型书写；其与 ALYREF/NXF1、ISG15 或 PCAT6 的功能性关系不能替代指定免疫细胞的直接证据。[316][357] 因此表格应明确区分先天抗病毒细胞模型、肿瘤细胞模型和尚未验证的 NK、DC、巨噬细胞或 T 细胞机制。

METTL3–METTL14异二聚体还结合辅助蛋白 WTAP。[270] RBM15B 被列为 writer，但该来源未报告其在 NK 细胞、树突状细胞、巨噬细胞或 T 细胞中的具体目标、机制或功能结果。[131] 在 NK 细胞中，YTHDF2 维持稳态。[331]

METTL3 与 METTL14 异二聚体构成的催化核心还结合辅助蛋白 WTAP[270]。

在 T1DM 研究中，YTHDC1 被列为 reader[131]。

在 LPS 刺激的 ADAP 缺失巨噬细胞炎症模型中，SPRY1 随后激活 NF-κB 通路，增加 IL-1β[252]。

在 LPS 刺激的 BMDMs（巨噬细胞）中，IGF2BP2 缺失增强 M1 样巨噬细胞极化。[372]

在树突状细胞（DC）中，METTL3 介导的 m⁶A 修饰导致促炎细胞因子分泌，并增强针对肿瘤的 CTL 反应。[236]

## 第二部分：四类免疫细胞中的具体调控机制

### 自然杀伤细胞：METTL3支持反应，FTO限制负反馈，YTHDF2维持适应性

**三条主轴指向不同节点。** 自然杀伤细胞（natural killer cell，NK细胞）中的代表性机制包括：METTL3–Ptpn11/SHP-2、FTO–SOCS，以及YTHDF2介导的转录本清除。它们都涉及细胞因子响应，但作用位置并不相同。因此，METTL3缺失与FTO缺失可以产生相反功能，而不构成简单矛盾。

**METTL3维持抗肿瘤能力。** Song等在《Nature Communications》发表的2021年研究，使用Ncr1-Cre条件性删除Mettl3，并分析NK细胞功能。敲除后，多个器官的NK细胞数量下降，肿瘤浸润减少，外周终末成熟受损。B16/F10黑色素瘤及MC38结直肠癌相关模型中，转移或肿瘤进展加快，小鼠生存缩短。[2]

**直接靶线索是Ptpn11。** Ptpn11编码含SH2结构域的蛋白酪氨酸磷酸酶SHP-2。联合RNA甲基化、METTL3结合及蛋白组分析，研究将Ptpn11定位为重要靶标。METTL3缺失后，SHP-2蛋白减少，而相关转录本变化并不对应同等下降，支持转录后蛋白输出调节。[2]

**受影响的是特定信号支路。** 白细胞介素15（interleukin-15，IL-15）是NK细胞存活和功能的重要细胞因子。METTL3缺失削弱IL-15诱导的AKT–mTOR及MAPK–ERK信号。这里mTOR指雷帕霉素机制靶蛋白，MAPK指丝裂原活化蛋白激酶；它们连接代谢、扩增与效应输出。该研究中STAT5磷酸化基本保留，不能把结果概括为所有IL-15信号同步关闭。[2]

**功能证据与支路一致。** 在体内强制表达IL-15后，野生型肝NK细胞比例约增至6倍，绝对数量超过10倍；Mettl3缺失组的增幅均不超过2倍。敲除NK细胞在IL-15刺激下的增殖、存活和效应分子表达也受损。SHP-2抑制剂能够重现多项信号及功能缺陷，支持SHP-2参与这条路径。[2]

**成熟与细胞毒性需要分开。** METTL3缺失主要影响外周终末成熟，研究中的骨髓NK前体数量并未同步下降。稳态强刺激条件下，部分效应读数差异较小；肿瘤或IL-15挑战时，脱颗粒、颗粒酶B和干扰素γ等缺陷更明显。因此，其作用更适合表述为维持挑战状态下的NK反应能力，而不是决定所有早期NK发育步骤。[2]

**肿瘤环境可压低该轴。** 转化生长因子β（transforming growth factor-β，TGF-β）处理可降低NK细胞METTL3蛋白及m⁶A水平。肿瘤细胞共培养和受体抑制实验支持，TGF-β参与这种抑制。人肝癌和卵巢癌相关NK数据也显示METTL3下降或与效应程序相关，但人体表达关联与小鼠遗传机制应分别理解。[2]

**FTO则维持抑制性反馈。** Kim等2023年《EMBO Reports》研究显示，FTO通过去除SOCS家族转录本上的m⁶A，提高其稳定性。SOCS是细胞因子信号抑制蛋白（suppressor of cytokine signaling）家族，包含SOCS1、SOCS3及细胞因子诱导SH2蛋白CISH。FTO降低后，这些抑制性蛋白减少，尤其SOCS3变化突出。[30]

**RNA变化解除JAK制动。** 研究通过m⁶A免疫沉淀及3′UTR报告实验，将SOCS3、CISH等转录本与FTO调节联系起来。FTO缺失或敲低后，白细胞介素2和15驱动的Janus激酶/信号转导与转录激活因子通路，即JAK/STAT，反应增强。具体表现包括JAK1/JAK3及STAT3/STAT5相关磷酸化增强或持续时间延长。[30]

**最终提高杀伤输出。** FTO敲低的NK92细胞对K562白血病细胞杀伤增强，脱颗粒增加。干扰素γ（interferon-γ，IFN-γ）、肿瘤坏死因子α（tumor necrosis factor-α，TNF-α）释放，以及颗粒酶B（granzyme B，GZMB）表达也增加。人脐带血来源CD3⁻CD56⁺ NK细胞中，FTO敲低同样提高体外杀伤能力。[30]

**体内结果支持NK依赖性。** Fto全身敲除小鼠接受B16F10细胞静脉注射14天后，肺转移结节明显减少。抗NK1.1耗竭后，这一保护表型减弱，两组转移结节趋于相近；相关转移和耗竭实验每组使用9–10只小鼠。FTO敲低NK92的过继转移，也改善了免疫缺陷小鼠K562模型中的肿瘤控制。[30]

**YTHDF2通过清除支持功能。** Ma等2021年的NK研究及后续综述表明，YTHDF2参与NK稳态、成熟、IL-15依赖存活，以及抗肿瘤和抗病毒功能。其机制涉及促进Tardbp、Mdm2等m⁶A相关转录本降解，而不是普遍稳定效应mRNA。STAT5信号和Eomes成熟程序应作为下游功能网络理解，不宜与上述降解靶标不加区分地并列为同等级直接底物。[12][7]

**三者不能合并成总量规律。** METTL3主要关联Ptpn11/SHP-2及AKT–mTOR、MAPK–ERK支路；FTO主要关联SOCS负反馈与JAK/STAT；YTHDF2通过选择性RNA清除维持功能。即使这些路径都改善某些NK终点，也不能将其解释为同一条线性机制，更不能自动指定它们共享同一个Reader。

**过表达不等于缺失的镜像。** FTO研究中的NK92实验还显示，METTL3过表达可呈现与FTO敲低相反的部分活性变化。这与METTL3条件性缺失损害NK功能的研究，需要按表达剂量、细胞系和刺激状态比较。已有结果支持情境差异，而不是“METTL3越多，NK一定越强”的单调关系。[30]

**本细胞结论。** NK细胞的激活、成熟与抗肿瘤功能，取决于m⁶A落在SHP-2支持轴、SOCS制动轴，还是YTHDF2清除的特定转录本上。

### 树突状细胞：激活成熟、交叉呈递与迁移是三个不同终点

**DC的功能不能只看成熟标志。** 树突状细胞（dendritic cell，DC）既要表达共刺激分子，也要加工、保存并呈递抗原，还要迁移至淋巴结。m⁶A可分别调节这些环节。因此，METTL3促进成熟与YTHDF1限制交叉呈递，可以同时成立。

**METTL3增强共刺激输出。** Wang等2019年研究在CD11c-Cre条件性Mettl3缺失小鼠及骨髓来源DC中发现，敲除降低CD40、CD80等共刺激分子和IL-12产生。主要组织相容性复合体Ⅱ类分子（major histocompatibility complex class II，MHC-II）及部分其他成熟读数也下降，DC刺激T细胞的能力受损。[3]

**三个靶标形成完整链条。** METTL3修饰Cd40、Cd80及Tirap转录本，提高其翻译效率。CD40、CD80增强DC与T细胞之间的共刺激；TIRAP是Toll/白细胞介素1受体结构域相关适配蛋白，参与Toll样受体4（Toll-like receptor 4，TLR4）信号。TIRAP增加后，核因子κB（nuclear factor-κB，NF-κB）相关信号与细胞因子输出增强。[3]

**主要变化发生在翻译层。** 这些靶标在Mettl3缺失DC中出现蛋白和核糖体占据下降，而mRNA含量并未相应大幅下降。位点或基序突变报告实验也支持m⁶A依赖的蛋白输出。因此，不能将这条机制改写成“METTL3主要通过稳定这三个mRNA促进成熟”。[3]

**YTHDF1参与读取执行。** YTHDF1对带有完整m⁶A相关基序的CD40、CD80转录本结合更强；敲低YTHDF1则降低相应蛋白。METTL3野生型可以恢复敲除DC的多项成熟及功能读数，催化失活突变体不能。RNA结合、Reader干预及催化救援共同支持这条机制。[3]

**T细胞功能读数有量化支持。** 在卵清蛋白抗原肽负载DC的体内OT-II实验中，接受Mettl3缺失DC的小鼠，其抗原特异性CD4⁺ T细胞增殖约为野生型DC组的1/3。该实验是在DC处理后观察T细胞应答，因果起点属于DC，而不是T细胞自身METTL3缺失。[3]

**YTHDF1又可限制交叉呈递。** Han等2019年《Nature》研究显示，经典DC缺失YTHDF1后，肿瘤抗原交叉呈递增强。所谓交叉呈递，是DC将摄取的外源抗原送入MHC-I呈递途径，启动CD8⁺ T细胞反应。它不同于单纯检测CD80、CD40或炎症因子。[31]

**关键在于防止过度降解。** YTHDF1识别带m⁶A的溶酶体蛋白酶转录本，提高组织蛋白酶（cathepsins）翻译。蛋白酶过多会加速摄取抗原降解，使可用于交叉呈递的抗原减少。缺失YTHDF1后，蛋白酶翻译下降，抗原保留增加，CD8⁺ T细胞交叉启动及抗肿瘤应答增强。[31]

**两项研究的区别有实质意义。** CD40/CD80/TIRAP轴问的是“DC能否充分激活并提供共刺激”；cathepsin轴问的是“DC是否把肿瘤抗原降解得过快”。前者受损可削弱免疫启动，后者减弱则可能保留更多抗原。因此，“翻译增强”并不天然等于“抗肿瘤免疫增强”，还要看被翻译的蛋白执行什么任务。

**放疗加入了STING反馈。** 2024年研究的后续综述显示，放疗可通过干扰素基因刺激因子（stimulator of interferon genes，STING）及Ⅰ型干扰素信号，诱导DC中YTHDF1。YTHDF1增加组织蛋白酶后，又促进STING蛋白降解，形成限制Ⅰ型干扰素输出的反馈。[12]

**该反馈影响治疗反应。** DC特异性Ythdf1缺失可增加Ⅰ型干扰素、抗原交叉启动及CD8⁺ T细胞杀伤，并增强小鼠放疗及放疗联合抗PD-L1效果。这里直接的m⁶A读取对象是蛋白酶转录本，STING下降则是后续蛋白降解结果，不能把两者混写成同一层面的RNA靶标。[12]

**YTHDF2则连接迁移代谢。** 趋化因子受体7（C-C chemokine receptor 7，CCR7）可诱导lnc-Dpf3。带m⁶A的lnc-Dpf3被YTHDF2识别并降解；当它积累时，会结合缺氧诱导因子1α（hypoxia-inducible factor-1α，HIF-1α），抑制糖酵解相关转录，从而限制DC迁移。[17]

**刺激晚期出现迁移制动。** CCR7刺激晚期，lnc-Dpf3的m⁶A下降，YTHDF2介导降解减弱。lnc-Dpf3随之积累，HIF-1α依赖糖酵解受抑，DC迁移下降。原研究体系描述了14个GGAC基序中的2个活性m⁶A位点，说明其作用落在特定RNA区域，而不是所有lncRNA的共同命运。[16][17]

**三个终点各有干预方向。** 提高成熟和共刺激能力，涉及维持METTL3对相关转录本的翻译支持。增强肿瘤抗原交叉呈递，则可能受益于减少YTHDF1驱动的蛋白酶输出。迁移还受lnc-Dpf3积累与糖酵解制动影响。只有在相同DC亚群、抗原和刺激阶段下，才适合将这些终点合并为总体判断。

**本细胞结论。** DC的m⁶A效应必须明确区分成熟、抗原交叉呈递和迁移，三者并不总向同一方向变化。

### 巨噬细胞：靶RNA、炎症刺激与代谢环境共同决定方向

**巨噬细胞不能统一贴标签。** 现有研究涉及骨髓来源巨噬细胞（bone marrow-derived macrophages，BMDMs）、腹腔巨噬细胞、细胞系及肿瘤相关巨噬细胞（tumor-associated macrophages，TAMs）。M1样、M2样可作为实验参照，但组织内巨噬细胞常同时具有炎症、修复、代谢和免疫抑制特征。[1]

**METTL3–STAT1支持M1样极化。** Liu等2019年研究发现，METTL3在STAT1 mRNA的CDS和3′UTR增加m⁶A，提高RNA稳定性及STAT1表达。STAT1是驱动炎症型巨噬细胞程序的重要转录调节因子。METTL3敲低抑制M1样极化并增强M2样表现，过表达则呈相反方向。[32]

**稳定性变化有直接测量。** 在放线菌素D阻断转录后的衰减实验中，STAT1 mRNA半衰期由对照的10.86±0.61小时，降至METTL3敲低组的5.27±0.06小时。另一组过表达实验中，半衰期由载体对照的10.67±0.42小时，升至19.86±1.99小时。这直接支持RNA寿命变化，而非仅依据稳态表达量推断。[32]

**相同STAT1也可被送入降解。** 另一组机制中，RNA结合蛋白RBM4促进YTHDF2识别STAT1 3′UTR的m⁶A相关位点，加速STAT1降解，降低糖酵解与M1样极化。这与METTL3–STAT1稳定化形成有价值的对照：同一转录本上的m⁶A，仍需由其结合环境决定最终命运。[1]

**METTL3还可清除炎症制动器。** Tong等2021年《Science Advances》研究将Irakm定位为巨噬细胞重要靶标。Irakm编码白细胞介素1受体相关激酶M，即IRAKM，是TLR信号负调节因子。METTL3在Irakm 3′UTR的m⁶A促进其降解，从而解除对NF-κB和MAPK的抑制。[33]

**靶标救援加强了因果性。** Mettl3缺失后，Irakm降解变慢、IRAKM积累，LPS诱导的TNF-α等输出下降。进一步敲低Irakm，可大幅恢复相关炎症反应。该研究的筛选和后续实验还提示，YTHDF成员之间可能存在冗余，不宜强行指定某一单独YTHDF为唯一执行者。[33]

**防御下降并不等于炎症获益。** Mettl3相关髓系缺失小鼠在沙门菌感染第4天，多个组织细菌负荷更高；皮下MC38模型中，肿瘤生长也更快。TAM出现TNF-α、CD86下降及CD206上升等变化。这个模型说明，降低巨噬细胞激活可能削弱病原体控制和抗肿瘤防御，而不是自动产生有利的抗炎结果。[33]

**SPRED2轴却显示另一种炎症方向。** Yin等2021年《Nature Communications》研究中，Mettl3缺失降低YTHDF1介导的SPRED2翻译。SPRED2对ERK相关信号具有限制作用；其蛋白减少后，ERK、NF-κB及STAT3磷酸化增强。研究观察到SPRED2蛋白下降，而Spred2 mRNA及降解变化不相称，支持主要是翻译控制。[4]

**炎症增强也能伴随促瘤。** 在B16黑色素瘤和LLC肺癌模型中，相关Mettl3缺失增加TAM及Treg浸润，促进肿瘤生长和转移，并削弱抗PD-1效果。该研究同时检测到M1样、M2样TAM增加，说明“炎症信号更强”不等于“巨噬细胞抗肿瘤更强”。[4]

**共同肿瘤终点需要看清。** Irakm研究与Spred2研究，都发现Mettl3缺失可使肿瘤进展加快。它们的分歧主要在炎症信号和巨噬细胞状态，而非最终肿瘤方向。前者是负调节RNA积累导致激活不足，后者是负调节蛋白翻译下降导致特定促瘤信号增强。把二者笼统称为“抗肿瘤结论相反”，反而会掩盖真正机制差异。

**髓系环境还可出现真正反向结果。** 2022年《Molecular Cell》研究显示，肿瘤来源乳酸及乳酰化相关机制可诱导浸润髓系细胞METTL3。METTL3–m⁶A–YTHDF1增强Jak1翻译，强化STAT3与免疫抑制；此时髓系Mettl3缺失可限制肿瘤。该机制的实验单位包括肿瘤浸润髓系细胞，不能自动缩窄为所有TAM亚群。[34]

| 模型或刺激 | METTL3相关靶标 | 主要RNA层过程 | 观察到的功能方向 |
|---|---|---|---|
| IFN-γ极化 | STAT1 | 甲基化后稳定性提高 | METTL3支持M1样程序 |
| LPS、感染及MC38 | Irakm | 促进负调节RNA降解 | 缺失削弱防御并促瘤 |
| B16、LLC肿瘤髓系模型 | Spred2 | YTHDF1介导翻译 | 缺失增强ERK等信号并促瘤 |
| 乳酸相关肿瘤髓系环境 | Jak1 | YTHDF1介导翻译 | METTL3支持免疫抑制 |
| DSS结肠炎 | PGP相关轴 | 缺失提高YTHDF3相关表达 | METTL3耗竭减轻肠炎 |

该比较的重点是靶标和功能终点，不是给METTL3分配一个跨模型不变的“促炎”属性。[32][4][35]

**YTHDF2在LPS环境限制炎症。** 脂多糖（lipopolysaccharide，LPS）刺激巨噬细胞时，YTHDF2耗竭提高MAP2K4、MAP4K4 mRNA稳定性及表达。随后p38、ERK和NF-κB相关信号增强，TNF-α、IL-6、IL-12、IL-1β等促炎输出增加。这里YTHDF2通过清除信号转录本发挥炎症限幅作用。[17]

**TAM中缺失YTHDF2可增强抗肿瘤。** Ma等的TAM研究及后续综述显示，YTHDF2缺失可增强IFN-γ–STAT1相关程序，提高抗原交叉呈递，并促进CD8⁺ T细胞介导的肿瘤控制。该结论应表述为TAM信号及功能重编程，不能仅凭其通用降解功能补写某条RNA的位点机制。[14]

**两个YTHDF2结果并不冲突。** LPS模型的终点是促炎因子增强，TAM模型的终点是抗原呈递及T细胞抗肿瘤增强。炎症增加可能造成组织损伤，也可能在特定肿瘤环境中解除免疫抑制。读者应同时记录靶RNA、组织环境和最终功能，而不是将“YTHDF2缺失增强炎症”自动翻译为治疗获益。

**FTO可同时支持两种极化。** 在常用极化模型中，FTO耗竭降低STAT1、STAT6及PPARγ相关输出，M1样和M2样激活均可受阻。其中STAT1及过氧化物酶体增殖物激活受体γ（peroxisome proliferator-activated receptor-γ，PPARγ）转录本降解加快；YTHDF2沉默可提高相关RNA稳定性。[13]

**代谢病模型给出不同净表型。** 2型糖尿病小鼠中，miR-495抑制FTO被报道伴随M1增加、M2减少，以及炎症和胰岛素抵抗加重。它与直接FTO耗竭后的双向极化受阻，应分别保留。上游微RNA干预、病理代谢环境和细胞组成都不同，不能将两者直接视为同一实验的互相否定。[13]

**IGF2BP2直接连接稳定与代谢。** IGF2BP2可识别并稳定TSC1 mRNA。TSC1进一步稳定TSC2，相关复合体限制MEK–ERK信号，抑制M1样激活。另一方面，IGF2BP2稳定PPARγ转录本，支持脂质代谢重编程和M2样程序。这是同一Reader通过两个靶标共同偏转巨噬细胞状态的例子。[6]

**ADAP–METTL3轴提供位点实例。** 在ADAP缺失巨噬细胞中，LPS诱导的METTL3依赖Spry1甲基化增强。原文将重要位点标注为GGACU基序中的A6988。IGF2BP2结合并稳定甲基化Spry1，伴随NF-κB激活和炎症增强；位点报告、RNA结合及稳定性实验共同支持该路径。[10]

**互作改变了Writer输出。** 这条机制的重要之处，是ADAP与METTL3的物理结合，连接到特定RNA位点及Reader稳定化结果。METTL3抑制或缺失可减弱ADAP缺失导致的高炎症反应。它不是“METTL3在所有巨噬细胞中都促进Spry1”的泛化结论，而是明确的ADAP状态依赖机制。[10]

**ALKBH5可抑制抗病毒RNA输出。** 病毒感染后，核内DDX46结合Mavs、Traf3和Traf6等RNA，并通过其解旋酶相关结构域招募ALKBH5。ALKBH5去除这些转录本的m⁶A，使其核内保留增加，胞质蛋白输出受限，最终压低Ⅰ型干扰素。这里决定功能的关键步骤是RNA定位，而不是简单的总RNA升降。[17]

**病毒抵抗还可来自代谢变化。** 另一组ALKBH5相关研究将抗病毒表型与α-酮戊二酸脱氢酶OGDH联系起来。ALKBH5缺失增加相关RNA衰减并降低OGDH蛋白，可形成不依赖Ⅰ型干扰素的病毒限制。该机制与DDX46轴回答的是不同问题：一个改变抗病毒信号分子输出，另一个改变病毒可利用的细胞代谢环境。[18]

**糖酵解轴可放大脓毒症炎症。** 2024年研究显示，HIF-1α增加METTL3表达，并提高Pfkm转录本m⁶A及肌型磷酸果糖激酶PFKM蛋白。该过程连接糖酵解与炎症因子产生；重组血栓调节蛋白rTM处理可抑制这条轴。相关研究结合了巨噬细胞、小鼠脓毒症模型及患者单核细胞观察。[36]

**代谢蛋白上调需按证据解释。** Pfkm案例支持修饰与蛋白输出、代谢和炎症之间的联系，但不能仅凭PFKM蛋白升高，就指定唯一Reader或断言全部来自稳定性增加。同理，患者单核细胞表达差异是人体关联证据，髓系Pfkm敲除的功能结果才提供相应模型中的因果支持。[36]

**肠炎中METTL3耗竭可有利。** Yin等2024年研究发现，巨噬细胞METTL3耗竭提高YTHDF3介导的磷酸乙醇酸磷酸酶PGP相关表达，重编程葡萄糖代谢，并抑制CD4⁺ Th1分化。小鼠右旋糖酐硫酸钠（dextran sulfate sodium，DSS）结肠炎因而减轻。该结果与感染防御下降并不矛盾：降低同类炎症输出，在不同疾病中可有不同净后果。[35]

**其他代谢靶标强化情境差异。** 高脂饮食相关肝细胞癌TAM研究中，METTL3稳定Cpt1a，支持脂肪酸代谢、M2样状态和肿瘤进展。动脉粥样硬化模型中，METTL3稳定肝癌衍生生长因子HDGF相关RNA，则促进M1样炎症和斑块进展。同一Writer的不同靶标，能够支持不同状态。[37]

**METTL14也可影响TAM免疫抑制。** C1q⁺ TAM中的METTL14丧失，被报道导致Ebi3转录本m⁶A降低及EBI3表达增加，并促进肿瘤浸润CD8⁺ T细胞功能异常。这说明Writer成员可通过巨噬细胞的分泌或免疫调节程序影响T细胞，而非直接改变T细胞内部RNA。[6]

**YTHDC2参与感染炎症限幅。** 马尔尼菲篮状菌感染巨噬细胞的研究，经2024年综述归纳显示，YTHDC2敲低使TLR2以m⁶A依赖方式升高，并增加TNF-α及IL-1β。它提供另一条Reader–受体–炎症联系；其RNA命运细节，应与已明确测量半衰期的STAT1等案例分层呈现。[26]

**肿瘤细胞作用要另列。** 缺氧胶质母细胞瘤中的ALKBH5可稳定lncRNA NEAT1，促进核旁斑组装、CXCL8分泌和TAM募集。另一种肿瘤细胞融合模型中，FTO通过CSF1转录本去甲基化，增强巨噬细胞募集或M2样偏转。这些是肿瘤细胞改变巨噬细胞环境，不是巨噬细胞内在ALKBH5或FTO机制。[37]

**差异解释有明确边界。** 2024年人THP-1分化研究比较既有BMDM文献时指出，METTL3耗竭后TNF、IL-6可出现相反变化。耗竭程度和持续时间，以及长期扰动引起的继发转录改变，是可能解释，而不是已经统一证实的原因。对研究结果的归纳应保留这些实验差别，不宜用单一极化标签覆盖。[38]

**本细胞结论。** 巨噬细胞m⁶A调控的可靠单位，是特定刺激下的“调控蛋白—靶RNA—RNA命运—功能”，而不是脱离模型的M1/M2或促炎/抗炎标签。

### T细胞：稳态、谱系分化、存活与耗竭具有不同RNA需求

**T细胞必须按亚群讨论。** T淋巴细胞（T lymphocytes）包括初始细胞、效应CD4⁺细胞、CD8⁺细胞及调节性T细胞。滤泡辅助性T细胞（T follicular helper cell，Tfh）支持生发中心反应；调节性T细胞（regulatory T cell，Treg）维持免疫抑制。m⁶A支持某一亚群，并不意味着对全部T细胞或疾病都产生相同净影响。[6]

**初始T细胞需要清除SOCS。** METTL3–METTL14在Socs1、Socs3及Cish等转录本上写入m⁶A，促进其周转。SOCS减少后，IL-7–STAT5信号得以正常传递，支持初始T细胞稳态增殖与分化。该机制的重要逻辑是：降低抑制性RNA，最终增强细胞因子反应。[6]

**敲除结果支持该链条。** Mettl3缺失使SOCS转录本降解变慢、蛋白积累，外周初始T细胞比例增加。将这类初始CD4⁺ T细胞转入淋巴细胞缺陷受体后，稳态增殖与分化明显受损；Mettl14缺失产生相近表型。这支持核心写入体系参与细胞因子响应，而非只与某种分化标志相关。[6]

**稳态增殖不同于急性激活。** IL-7驱动的外周稳态，与T细胞受体识别抗原后的激活并不是同一终点。因此，这组结果不应扩展为“METTL3缺失会关闭全部T细胞激活”。另有WTAP相关遗传研究支持mRNA甲基化参与T细胞受体信号与存活，也说明辅助Writer成员可以影响不同反应阶段。[1]

**Treg使用IL-2而非IL-7主轴。** 成熟Treg中，METTL3维持SOCS转录本周转，使IL-2–STAT5信号能够支持抑制功能。Foxp3-Cre介导Mettl3缺失后，研究可观察到正常数量的Foxp3⁺ Treg，但这些细胞失去充分抑制能力，导致严重自身免疫。数量保留与功能丧失同时存在，是该案例的重要特点。[6]

**Foxp3稳定性是另一层机制。** 体外诱导Treg研究显示，METTL3催化抑制可降低Foxp3 mRNA相关m⁶A富集，并加快衰减，使Foxp3表达和Treg诱导下降。该研究将Foxp3作为候选直接靶标处理，其证据包括m⁶A富集及RNA衰减。它与成熟Treg的SOCS–IL-2机制，应并列而非合并成完全相同的链条。[39]

**METTL14支持诱导性Treg。** METTL14在初始CD4⁺前体向诱导性Treg分化过程中升高，并支持Foxp3转录本稳定性。沉默METTL14可削弱分化及抑制功能，增加IFN-γ、IL-17A相关输出，并伴随mTOR–p70S6K活化。这说明Writer可同时影响谱系核心转录本及不利于该谱系稳定的代谢信号。[40]

**Tfh有高分辨率靶标证据。** Yao等2021年研究发现，CD4⁺ T细胞Mettl3缺失损害Tfh分化、生发中心形成及相关体液免疫程序。Tcf7、Bcl6、Icos和Cxcr5等基因表达下降。Tcf7编码T细胞因子1，即TCF-1，是该研究的重要机制节点。[5]

**Tcf7的关键变化是稳定性。** 研究将高置信m⁶A位点定位于所用Tcf7转录本3′UTR的A1011，处于GGACT相关基序。将报告基序改为GGTCT，会削弱METTL3相关报告活性增加；METTL3缺失或位点突变均加速Tcf7衰减。外源TCF-1能够挽救Tfh分化缺陷，形成较完整的位点—RNA寿命—谱系功能链条。[5]

**不能自动指定稳定Reader。** 这项研究直接支持METTL3依赖的Tcf7稳定化，但不能仅凭IGF2BP的一般功能，就把某个IGF2BP成员填入该路径。事实上，原研究强调CD4⁺ T细胞中相关家族表达环境与其他体系不同。这里最强结论是位点依赖的稳定性和TCF-1救援，而不是一个凭通用知识补上的Reader名称。[5]

**Icos机制提供相反比较。** VHL缺失模型中，HIF-1α–GAPDH相关糖酵解程序增强，METTL3升高，使Icos mRNA m⁶A增加并加速降解，最终抑制Tfh分化。该结果与Tcf7稳定化支持Tfh并不相同，但靶RNA、上游代谢扰动和实验背景也不同。[6]

**Tfh净方向由主导靶标决定。** Tcf7甲基化支持TCF-1维持，Icos甲基化在另一模型中加速共刺激受体RNA降解。两条链共同否定“METTL3对Tfh永远只有一个方向”。当细胞环境改变Writer的靶标分配或RNA读取方式时，净分化结果也会改变；不能把某一模型的靶标效应替代另一模型。

**ALKBH5提高炎症CD4⁺反应。** Zhou等《Science Advances》研究显示，T细胞活化后ALKBH5上调。ALKBH5去除Ifng和Cxcl2转录本的m⁶A，提高其稳定性及蛋白表达。Cxcl2编码C-X-C趋化因子配体2（C-X-C motif chemokine ligand 2，CXCL2），可参与中性粒细胞募集。[18]

**敲除后的方向十分明确。** ALKBH5缺失增加Ifng、Cxcl2的m⁶A，使其稳定性下降、IFN-γ和CXCL2蛋白减少。m⁶A免疫沉淀定量支持这两个靶标，而同一实验中的Cxcl10并未呈现相同富集变化。这里体现了Eraser底物选择性，不能将所有趋化因子转录本都纳入同一条机制。[18]

**疾病终点连接跨细胞效应。** ALKBH5缺失初始CD4⁺ T细胞转入Rag2缺陷受体后，诱发结肠炎的能力下降。T细胞条件性缺失也减轻实验性自身免疫性脑脊髓炎（experimental autoimmune encephalomyelitis，EAE），并减少中枢神经系统中性粒细胞募集。因此，T细胞内部RNA稳定性变化，最终可以改变另一种免疫细胞的组织浸润。[18]

**两种Eraser并不冗余。** 同一研究中，ALKBH5对稳态T细胞发育的影响较小，Treg中特异缺失也未改变其对EAE的抑制作用。T细胞FTO缺失未明显改变该EAE模型病程。这些是特定实验中的比较结果，说明Eraser效应取决于亚群与病理任务，而不是对FTO全部T细胞功能的否定。[18]

**YTHDC2可抑制致病Th17程序。** 辅助性T细胞17亚群（T helper 17 cell，Th17）是若干自身免疫模型的重要致病细胞。实验性自身免疫性葡萄膜炎相关研究，经2024年综述归纳显示，YTHDC2以m⁶A依赖方式提高ASH1L mRNA稳定性和表达，抑制IL-17及IL-23受体相关致病输出，减轻Th17反应。[26]

**γδ T细胞体现发育阶段差异。** ALKBH5还通过Jagged1/Notch2相关m⁶A调节影响γδ T前体。ALKBH5缺失后，该Notch相关程序下降，细胞周期相关基因上升，γδ T前体扩增及分化增加；研究中的成熟细胞因子特征和成熟细胞增殖、凋亡并未同步改变。小鼠沙门菌感染保护增强，因此主要应归因于前体及细胞数量程序，而非普遍提高单细胞效应能力。[41]

**FTO支持活化CD8⁺存活。** Sun等2025年研究显示，FTO缺失增加Fas mRNA的m⁶A，使IGF2BP3依赖的RNA稳定化增强，Fas表达升高。Fas是死亡受体，增加后可提高活化CD8⁺ T细胞凋亡。该路径因此不同于NK细胞中的FTO–SOCS制动机制。[29]

**位点和Reader救援支持因果。** 突变Fas相关m⁶A位点、敲低IGF2BP3，或阻断Fas信号，都可降低FTO缺失所致的Fas上调及凋亡。这一组证据明确连接了Eraser、修饰、Reader、RNA稳定性和细胞死亡，而不只是发现FTO表达与细胞数量相关。[29]

**减少扩增不等于激活失败。** 在表达卵清蛋白的单核细胞增生李斯特菌，即LM-OVA急性感染模型中，FTO缺失抗原特异性CD8⁺ T细胞于感染后第4–6天扩增减少，受体细菌控制下降。主要缺陷是激活后凋亡增加，而早期激活、增殖及多项分化或细胞因子读数相对保留。因此，应将其归为存活和效应群体维持，而非笼统的全部效应功能抑制。[29]

**METTL3也支持急性效应程序。** 急性病毒感染研究的综述归纳显示，METTL3可稳定Tbx21 mRNA，维持其编码的T-bet，支持CD8⁺ T细胞效应扩增、终末分化、记忆及再次应答。外源T-bet可部分挽救分化缺陷。该机制说明，抑制Writer也可能损伤保护性CD8⁺效应建立。[40]

**肿瘤Treg的YTHDF2维持抑制。** Zhang等2023年《EMBO Journal》研究在B16F10和MC38模型中发现，Foxp3⁺ Treg特异性删除Ythdf2可减缓肿瘤。肿瘤内Treg凋亡增加、抑制功能受损，CD8⁺ T细胞浸润及IFN-γ增加。这是Treg内部机制改变后，间接释放CD8⁺抗肿瘤功能的证据。[42]

**靶标是NF-κB负调节RNA。** 肿瘤环境中的TNF激活NF-κB，并诱导YTHDF2。YTHDF2加速Nlrc3、Nfkbie和Traf3等m⁶A修饰转录本降解，减少对NF-κB的负调节，维持肿瘤内Treg存活。YTHDF2缺失后，这些RNA积累，信号支持减弱，Treg抑制能力下降。[42]

**环境决定Treg依赖程度。** 同一研究中，外周Treg抑制功能和免疫稳态总体保留，条件敲除小鼠可观察至1年而无明显全身炎症表型。这与Treg中Mettl3缺失引发严重自身免疫形成鲜明对照。其合理解释是，YTHDF2在该肿瘤炎症环境中维持特定反馈，而METTL3影响更广泛的Treg RNA程序。[42]

**CD8⁺耗竭出现新的Writer机制。** Ghosh等2026年1月预印本提出，METTL3通过m⁶A稳定DNMT3B转录本，增加DNA甲基化及记忆相关位点染色质压缩，推动CD8⁺ T细胞终末耗竭。抑制该轴可保留祖细胞样潜能、效应功能和持续性，并改善模型中的肿瘤控制及PD-1阻断反应。[43]

**急性效应与慢性耗竭要并列。** Tbx21/T-bet轴支持急性效应建立，而DNMT3B轴提出持续抗原环境中的终末耗竭机制。两者支持阶段依赖的解释，但并不等于已证明同一细胞内必然发生固定的两阶段切换。后者应按预印本机制处理；干预是否获益，取决于保留效应建立还是限制慢性耗竭，哪一个任务在当前状态占主导。

**人体关联不等于治疗方向。** 系统性红斑狼疮（systemic lupus erythematosus，SLE）患者CD4⁺ T细胞中，METTL3及全局m⁶A降低，并与疾病活动相关。相关研究的药理模型又显示，METTL3抑制可减少Treg、增加部分炎症反应，并加重狼疮样损伤。因此，患者低表达不能直接解释为应进一步抑制该蛋白。[39]

**跨细胞效应必须注明起点。** YTHDF1缺失后CD8⁺ T细胞增强，经典机制首先定位在DC交叉呈递。另有肿瘤研究发现，肿瘤细胞YTHDF2缺失延长MHC-I mRNA寿命，提高免疫可见性。这两类结果都能增加T细胞抗肿瘤输出，但分别属于DC内在和肿瘤细胞内在机制，不能作为T细胞自身靶RNA的替代证据。[31][44]

**本细胞结论。** T细胞中m⁶A的功能方向，应按亚群、反应阶段及细胞内在性判断：支持稳态和存活、维持免疫耐受，以及推动或限制肿瘤耗竭，是不同任务。

**补充证据**

**METTL3：Writer 通过 Ptpn11/SHP-2 连接 IL‑15 信号**

在 NK 细胞中，METTL3 是 m⁶A writer 复合体的催化亚基；其在 NKp46⁺ 细胞中的特异性缺失会降低 m⁶A 水平，破坏 NK 细胞稳态及抗肿瘤免疫。[345] METTL3 与 METTL14、WTAP 共同组成写入复合物：METTL14主要提供 RNA 结合平台，WTAP 是复合物组分；这是复合物层面的共同组成关系，并不等同于该研究已证明 NK 细胞内存在特异性的二元蛋白结合。该研究也没有证明 METTL3 与下游 SHP-2 蛋白直接结合。

实验上，证据来自 NKp46⁺ 细胞特异性 **Mettl3** 条件性敲除小鼠、METTL3-shRNA 处理的 NK92 细胞，以及肿瘤浸润 NK 细胞。肿瘤微环境中的 TGF-β 可降低 NK 细胞 METTL3 蛋白表达，并伴随 m⁶A 水平下降；相比之下，YTHDC1、YTHDC2、YTHDF2、FTO 和 ALKBH5 的蛋白水平在该条件下未明显改变。[345] 因此，该结果支持 TGF-β—METTL3—m⁶A 轴，而不是把所有 m⁶A 调控蛋白的变化混为同一机制。

最明确的 RNA 目标是 **Ptpn11 mRNA**，其编码蛋白为 SHP-2。MeRIP-seq 与 METTL3-RIP-seq 均支持 Ptpn11 是 METTL3 介导的 m⁶A 目标；METTL3 缺失后，SHP-2 蛋白降低，但 Ptpn11 转录本水平没有相应下降。[345] 这提示 METTL3 主要影响该转录本的蛋白产生或 RNA 后续命运，而非简单改变转录量；不过，研究明确指出 SHP-2 的精确翻译机制尚未确定，也没有排除 m⁶A 通过降解某个共调控因子的间接作用。NK 细胞的 m⁶A 峰主要位于 3′UTR、编码区和终止密码子附近，并富集于 DRACH 模式；其他 m⁶A 目标还涉及 PI3K-AKT 和 mTOR 通路。[345]

在 IL-15 刺激下，METTL3 缺失显著削弱 AKT-mTOR 和 MAPK-ERK 信号，但对 JAK-STAT5 磷酸化影响不明显；高剂量 IL-15 条件下，缺失细胞的最大呼吸能力和备用呼吸容量也下降。[345] 功能结果具有条件依赖性：稳态时 NK 细胞数量已减少，但凋亡和增殖变化不大；肿瘤攻击或 IL-15 处理后，细胞数量减少进一步加重，IL-15 驱动的增殖、存活、激活、终末成熟和肿瘤组织浸润均受损。B16/F10 肺转移、MC38 肝转移及皮下肿瘤模型中，NK 细胞缺失 METTL3 的小鼠出现更多转移灶、更快肿瘤进展和更短生存期。[345] 在野生型 NK 细胞中抑制 SHP-2 的 SHP099 可近似重现 AKT、mTOR、ERK/MAPK 活性下降、NK 细胞增殖减少以及高剂量 IL-15 下 GzmB、IFN-γ 和 TNF 表达降低的表型，从而加强了“METTL3—Ptpn11/SHP-2—IL-15 信号—NK 抗肿瘤功能”的因果解释。[345]

现有证据卡片不能确认 NK 细胞内哪一个 m⁶A Writer、Eraser 或 Reader 被直接证明起作用；也未给出直接 RNA 靶标、m⁶A 位点或稳定性、翻译、降解等中间机制。因此这些字段应标为“未找到直接证据”，不能把 ZC3H13 的表达关联写成 NK 细胞内的 m⁶A 因果链。[541][539]

可确认的细胞背景是：NK 细胞属于先天淋巴细胞，细胞毒性功能类似 CD8⁺ T 细胞；其处理靶细胞取决于表面激活与抑制信号的净平衡，并可通过 ADCC、细胞毒性颗粒、死亡配体及 CAR 依赖或非依赖途径杀伤肿瘤，且无需抗原预激。[541]

在 KIRC 邻近正常组织的单细胞 RNA-seq（6,046 个细胞）中，ZC3H13 在 T/NK 细胞中几乎不表达，却在内皮细胞、巨噬细胞、神经元和组织干细胞中丰富；KIRC 中较高 ZC3H13 表达伴随免疫启动、激活、向肿瘤迁移及 CD56^bright NK 浸润降低，呈非炎症型肿瘤微环境，并可能预示较低 ICB 反应。该结果来自公共数据库和小样本 RNA-seq 的关联分析，仍需更大队列及机制实验验证。[539]

该文仅提供背景性概述：m⁶A 被称为哺乳动物细胞中最丰富的表观转录组标记，可涉及癌症免疫效应、趋化因子/细胞因子级联和 MHC 抗原呈递，但未给出 NK 细胞内的具体链条[113]。在 LM8 小鼠骨肉瘤皮下移植瘤中，敲除肿瘤细胞 RBMX 后，单细胞分析显示 NK 细胞增加、巨噬细胞减少，肿瘤生长受抑且生存延长（未给出 NK 比例）[113]。RBMX 虽被作为 m⁶A 调控因子讨论，本文却未证明其在 NK 细胞内直接写入、擦除或读取 m⁶A，也未报告 NK 目标 RNA、m⁶A 位点、RNA 命运或直接互作。因此这是肿瘤细胞—微环境关联证据；H2-K1/THBS1 及 CD8⁺ T 细胞结果不应归入 NK 的机制链。


2024年研究显示，METTL3/METTL14双敲除较单缺失更显著影响NK稳态、成熟和抗肿瘤免疫；Prf1、Gzmb为直接m⁶A目标，mTORC1–SAM轴位于上游。[360] 2021年小鼠研究中，YTHDF2结合带m⁶A的Mdm2、Tardbp、Crebzf；其缺失降低IFN-γ、GZMB、perforin和细胞毒性，并损害成熟、抗肿瘤及抗病毒功能。[519] 本组证据中，YTHDF1仅有肿瘤微环境浸润关联；Regnase-1–OCT2–Ifng属非m⁶A替代链。[465][542]

NK：METTL3缺失→SHP‑2m⁶A/翻译↓，IL‑15反应及杀伤↓[151]；YTHDF2缺失→抗肿瘤/抗病毒↓[52]；FTO→细胞毒性↓。

NK（小鼠NKp46⁺、肿瘤/IL15）：METTL3（Writer）给Ptpn11/SHP‑2加m⁶A，保AKT‑mTOR/MAPK‑ERK；缺失损害成熟、增殖、GzmB/IFN‑γ/TNF及抗瘤监视[361]。METTL3/14双缺失损害成熟/毒性，Prf1/Gzmb为直接靶[344]；YTHDF2读Tardbp与STAT5反馈，维持存活/细胞毒性[362]；FTO抑制细胞毒性[162]；IGF2BP3（肿瘤端）促ULBP2转录本降解，间接减NK杀伤[540]。

小鼠Ncr1-Cre肿瘤模型中，METTL3/SHP2/IL‑15轴维持NK抗肿瘤监视[404]；FTO抑制NK细胞毒性[328]。

证据最强的 NK 机制来自小鼠 Ncr1Cre/+;Mettl3fl/fl 条件性敲除：METTL3（Writer）缺失降低 m⁶A，并使 Ptpn11/SHP‑2 蛋白下降（转录量未变），使 NK 细胞对 IL‑15 低反应，AKT‑mTOR/MAPK‑ERK 信号、增殖、存活、GzmB、IFN‑γ/TNF 和细胞毒性下降；在 B16/F10、MC38 模型中，NK 浸润减少、转移增加且小鼠生存缩短[91][92]。肝癌患者肿瘤浸润 NK 的 METTL3 mRNA 比健康对照低 75%（2021）[532]。

MeRIP‑seq 与 METTL3‑RIP‑seq 支持 Ptpn11 为直接 METTL3/m⁶A 靶标，但 SHP‑2 翻译机制仍未定；TGF‑β（25 ng/mL，3 d）可下调 NK-METTL3，故结论主要限于肿瘤和 IL‑15 背景[92][543]。YTHDF2（Reader）在小鼠 NK 中调控 STAT5、Eomes、Tardbp，支持稳态、成熟、IL‑15 存活及抗肿瘤/抗病毒功能；本组未提供其与蛋白伙伴直接结合证据，其他因子如 FTO、ALKBH5、YTHDF3 尚未建立同等因果链[331][322]。HeLa/体内 circRNA 的 YTHDF2–RIG‑I 结果不是 NK 特异证据；2024 年胶原凝胶条目也未涉及 m⁶A[49][93]。

rejected；reason=number_unsupported；allowed_numbers=["about 9% of total m⁶A modification sites"]；allowed_citations=[369,370,379,550,663]；allowed_entities=["自然杀伤细胞（NK细胞）","T 细胞"]

rejected；reason=number_unsupported；allowed_numbers=["75% lower"]；allowed_citations=[396,669,721]；allowed_entities=["自然杀伤细胞（NK细胞）","T 细胞","N6-methyladenosine (m⁶A)"]

rejected；reason=number_unsupported；allowed_numbers=["75% lower"]；allowed_citations=[46,314,370,396,550,663,721]；allowed_entities=["自然杀伤细胞（NK细胞）","T 细胞","N6-methyladenosine (m⁶A)"]

FTO 在巨噬细胞中促进 M1 和 M2 activation。[133]

**补充证据**

巨噬细胞中的 m⁶A 结论具有条件依赖性：M1/M2 状态、LPS/病毒/肿瘤或 DSS 结肠炎、物种及体内外模型都会改变方向；现有证据主要连接炎症、抗病毒和 TAM 极化。[237][328]

**Writers：**在小鼠巨噬细胞 M1 极化模型中，METTL3 给 **STAT1 mRNA** 加 m⁶A，提高其稳定性和表达，促进 M1；敲低 METTL3 则抑制 M1、偏向 M2。[237]在 LPS 条件下，METTL3 缺失还可丢失 **IRAKM mRNA** 的 m⁶A、减弱 TLR 激活；髓系细胞缺失 METTL14 会削弱 **SOCS1 mRNA** 甲基化并减少 YTHDF1 结合，导致 TLR4/NF-κB 过度激活。WTAP 则可经 LPS 诱导的 p65 核转位促进巨噬细胞 IL-6 表达。[52][328]

**Erasers：**病毒感染时，DDX46 招募 ALKBH5 去甲基化 **Mavs、Traf3、Traf6**，使转录本滞留于细胞核并抑制 I 型干扰素；另一模型中，ALKBH5 缺失增加 **OGDH mRNA** 的 m⁶A 和降解，降低 OGDH/itaconate 并抑制病毒复制；猪肺泡巨噬细胞中的 ALKBH5–YTHDF2–**GAS6** 轴也限制 PEDV。[237][326][110]

**Readers：**LPS 巨噬细胞中，YTHDF2 缺失使 **MAP2K4/MAP4K4 mRNA** 稳定，激活 MAPK/NF-κB 并升高 TNF-α、IL-6、IL-1β 和 IL-12；TAM 中 IL-10/STAT3 上调 YTHDF2，抑制 IFN-γ/STAT1，敲低则增强抗原交叉呈递和 CD8⁺ T 细胞抗肿瘤反应。[237][317]YTHDF1 促进 **NLRP3** 翻译；IGF2BP2 稳定 **TSC1、PPARγ**，其缺失在 DSS 结肠炎小鼠中增加 M1、减少 M2并加重炎症。[328][52]

巨噬细胞中，METTL3→STAT1 mRNA稳定→M1；缺失→IRAKM积累/TLR4炎症受抑[457]；ZC3H13沉默→Spic稳定、NF‑κB/肝炎下降[441]；YTHDF2缺失→Stat1稳定、TAM交叉呈递/CD8抗瘤↑[451]；METTL14缺失→EBI3稳定、CD8障碍[344]；WTAP→Idh1稳定翻译→M2，FTO/ALKBH5分别依赖感染/肿瘤模型[239][240][555]。

最完整的直接链包括：TP刺激人THP‑1来源M0巨噬细胞（24 h，MOI=20:1）中，METTL3（Writer）提高SOCS3 mRNA的m⁶A，YTHDF1（Reader）结合并促翻译；SOCS3抑制JAK2/STAT3，降低TNF‑α、IL‑1β。文章结论称YTHDF1抑制M1、促M2，但敲低流式又显示CD86/iNOS上升、CD206/ARG1下降，方向应保留不一致。[348] LPS刺激RAW264.7中，YTHDF2（Reader）识别IL‑6R 3′UTR的m⁶A，降低稳定性并促降解，抑制IL‑6R/JAK2/STAT1/HMGB1；在LPS脓毒症小鼠中过表达YTHDF2提高生存、减轻肺损伤和炎症，结论限于该模型且细胞表达方向与既往研究相反。[473] CRC相关TAM中，METTL14缺失经YTHDF2依赖机制上调EBI3，导致CD8⁺T细胞功能障碍和肿瘤进展；另有研究称METTL14降低提高抗PD‑1反应。[174]

肿瘤TAM证据还显示，YTHDF2靶向Stat1 mRNA、削弱IFN‑γ/STAT1和抗原交叉呈递；YTHDF1沉默使M2→M1并增加CD8⁺T浸润；IGF2BP3稳定CCL5/TGF‑β1转录本促M2，HNRNPA2B1包装miR‑184‑3p抑制JNK、靶向EGR1促M2。[350][241] 2024年THP‑1多组学显示，m⁶A在单核细胞→静息巨噬细胞时下降、极化后稳定；修饰转录本包括CSF1/MSR1/CD36、M1的TLR4/ICAM1/YAP1和M2的CD163/COL6A2/CD209。METTL3敲低降低全局m⁶A及相关表达/翻译，分化不完全；BMDM中其对TNF、IL‑6方向相反，可能受耗竭程度、时长及间接效应影响。[554]

补充证据：小鼠LPS/TLR4、Adap−/−巨噬细胞中，METTL3与ADAP物理互作，给Spry1 mRNA加m⁶A；IGF2BP2特异识别并稳定该转录本，激活NF‑κB，升高IL‑1β、IL‑6、TNF‑α；Mettl3缺失或Spry1敲低可减炎[252]。LPS/IL‑4 BMDM中，IGF2BP2以m⁶A依赖方式稳定TSC1、PPARγ，缺失促M1、损害M2；但DSS结肠炎加重、过敏性肺炎减轻，方向依模型而变[354]。DSS/LPS巨噬细胞中HNRNPC升高；敲低降低炎症并改变Itgb7稳定性/前体mRNA剪接，体内减轻结肠炎[434]。TAM中METTL3/YTHDF1调节SPRED2翻译；YTHDF2在肿瘤巨噬细胞中降低CX3CL1稳定性并抑制抗原呈递；RBM15促M1糖酵解；FTO/ALKBH5/YTHDC1有疾病模型线索[133][320][358][462]。HNRNPA2B1在BMM/TAM中经外泌体miR/circ促M2或免疫抑制，直接m⁶A链仍有限[433][505]。

小鼠M1巨噬细胞中，METTL3（Writer）给STAT1 mRNA加m⁶A并提高稳定性，促进M1极化[369]；LPS刺激RAW264.7细胞时，YTHDF1（Reader）识别GBP4 mRNA的m⁶A并促翻译，增强M1及IL‑1β/IL‑6炎症[466]。METTL3缺失对吞噬的方向随静息或LPS/IFN‑γ状态而变[467]；ESCC中ZC3H13经m⁶A-CXCL8稳定化/CXCR2轴促M2浸润[136]；ALKBH5方向依模型而变[452]。

小鼠TAM中YTHDF2降低Stat1mRNA稳定性，抑制抗肿瘤极化；Lyz2模型非巨噬细胞特异[521]

巨噬细胞中，METTL3/14、FTO/ALKBH5、YTHDF/IGF2BP2/WTAP经m⁶A调STAT1、Socs1、OGDH等RNA，影响极化、炎症和抗病毒；方向依赖模型。[243][255][385]

hMDM(2024)：WTAP/ZC3H13写入TNF mRNA m⁶A促降解；缺失使TNFα↑[107]

巨噬细胞含METTL3等多轴且方向冲突[398]；53字符不足，需扩容。

小鼠巨噬细胞中，METTL3甲基化STAT1 mRNA并增强其稳定性，促M1极化。[404]

小鼠BMDM/Raw264.7中，METTL3（Writer）在Irakm3′UTR写入m⁶A并促其降解，解除TLR4负反馈，增强LPS激活、抗菌及TAM抗肿瘤；缺失则M2/免疫抑制增强[548]。C1q⁺TAM中METTL14–YTHDF2缺失使EBI3升高，积累功能失调CD8⁺T细胞并促肿瘤生长[409]。病毒感染时，DDX46招募ALKBH5去甲基化Mavs/Traf3/Traf6，转录本滞核抑制IFN[249]。

METTL3/YTHDF2调控Pyk2 mRNA稳定性，关联炎症、ROS及巨噬细胞极化[556]。

巨噬细胞：METTL3→STAT1→M1；FTO→SOCS1↓炎症↑[533]；ALKBH5→IL11去m⁶A纤维化↑[450]；METTL14→乳酸→M2/吞噬[534]；病毒m⁶A↓→IFN-I↑[327]

code=rejected；reason=number_unsupported；allowed_numbers=[]；allowed_cites=[237],[247]；allowed_entities=[巨噬细胞,T 细胞]。

code=rejected；reason=number_unsupported；allowed_numbers=[]；allowed_cites=[237],[317]；allowed_entities=[巨噬细胞,T 细胞]。

code=rejected；reason=number_unsupported；allowed_numbers=[]；allowed_cites=[473],[317]；allowed_entities=[巨噬细胞,T 细胞,N6-methyladenosine (m⁶A)]。

code=rejected；reason=number_unsupported；allowed_numbers=[]；allowed_cites=[237],[247]；allowed_entities=[巨噬细胞,T 细胞,N6-methyladenosine (m⁶A)]。

在该研究中，N6-methyladenosine（m⁶A）相关的 LUAD 机制包括：LUAD 相关 M2 巨噬细胞中，m⁶A 去甲基化酶 ALKBH5 通过 CDCA4 调节 M2 极化并促进 LUAD 发展，且该效应可由 YTHDC2 过表达逆转；在人 LUAD 细胞系及小鼠肿瘤模型中，OAS 和 IFIT mRNA 被 m⁶A 修饰，其稳定性以 YTHDC2 依赖方式提高并与翻译效率相关。[256]

小鼠肺泡巨噬细胞/RAW264.7经LPS处理时，METTL3（Writer）介导GBP4 mRNA的m⁶A，YTHDF1（Reader）识别该修饰并促进GBP4翻译，促进M1极化及相关炎症读出。[466]肿瘤微环境中，YTHDF2是关键的m6A RNA修饰“阅读器”，识别并结合m6A修饰的RNA分子；其生物学作用包括促进mRNA降解、调节细胞信号通路和代谢，并调节巨噬细胞功能、维持免疫抑制状态。[226]

巨噬细胞中，在该研究的 LPS 刺激 RAW264.7 炎症模型和脓毒症小鼠模型中，YTHDF2 过表达降低 IL-6R mRNA 稳定性，抑制 JAK2/STAT1 信号和 HMGB1 释放，并减轻炎症；该研究未提供 YTHDF2 在 NK 细胞、树突状细胞或 T 细胞中的证据。[473] 此外，参考文献列出一项关于 Mettl14 缺失于肿瘤相关巨噬细胞的研究，其题名指出该缺失促进 CD8+ T 细胞功能障碍和肿瘤生长。[368] ALKBH5 去甲基化与治疗耐受有关：在富含乳酸的肿瘤微环境中，ALKBH5 调节 MCT4/SLC16A3 介导的乳酸外排程序；ALKBH5 遗传缺失或小分子抑制减少 Treg 和 MDSC 浸润并提高多种同基因模型对抗 PD-1 的反应；在胶质母细胞瘤干样细胞中，MST4–USP14–ALKBH5 轴稳定 ALKBH5 蛋白、增强同源重组修复并造成放射抵抗。[231]

在 S. aureus 感染的 RAW 264.7 巨噬细胞中，MOI of 10 时 FTO 的 mRNA 和蛋白表达显著下降；si-FTO 提高 IL6、IL1β 炎症蛋白水平，并提示 FTO 经 FOXO1/NFKB 调节表型，但未证明这些分子是其直接 RNA 靶标。[289] 2022 年乳腺癌参考文献题为“METTL3/IGF2BP3 axis inhibits tumor immune surveillance by upregulating N6-methyladenosine modification of PD-L1 mRNA in breast cancer”，仅提供该轴、PD-L1 mRNA、m⁶A 与免疫监视受抑的研究线索，未给出实验细节，且非巨噬细胞特异证据。[271]

## 第三部分：免疫细胞机制总结表

**表格方向与正文一致。** 下表按“调控蛋白—靶RNA及命运—功能”压缩主要机制。箭头表示相应研究条件下的变化；“缺失”或“敲低”明确写出的行，描述的是干预后的结果。为便于横向阅读，按细胞和功能分组，每张表均保留指定四列。

### NK细胞与树突状细胞

| 免疫细胞类型 | 关键m⁶A调控蛋白 | 调控目标与机制 | 对细胞功能的最终影响 |
|---|---|---|---|
| NK细胞 | METTL3 | Ptpn11 m⁶A与SHP-2蛋白维持；支持IL-15下游信号 | 支持成熟、浸润和抗肿瘤杀伤 |
| NK细胞 | FTO | 去甲基化并稳定SOCS1/3、CISH；限制JAK/STAT | 缺失增强激活、脱颗粒和杀伤 |
| NK细胞 | YTHDF2 | 促进Tardbp、Mdm2等RNA降解；维持IL-15相关程序 | 支持存活、成熟及抗病毒、抗肿瘤功能 |
| DC | METTL3、YTHDF1 | 增强CD40/CD80/TIRAP翻译及TLR4信号 | 促进激活成熟、细胞因子和T细胞刺激 |
| DC | YTHDF1 | 提高cathepsin翻译，加速抗原降解 | 缺失增强交叉呈递和CD8⁺启动 |
| DC：放疗环境 | YTHDF1 | 蛋白酶翻译↑，促进STING蛋白降解 | 缺失增强Ⅰ型干扰素及放疗免疫效应 |
| DC：迁移 | YTHDF2 | 降解lnc-Dpf3，解除HIF-1α糖酵解制动 | 支持迁移；晚期lnc-Dpf3积累限制迁移 |

主要依据为NK的METTL3、FTO研究，DC激活与交叉呈递研究，以及迁移和放疗机制综述。[2][30][3][31][17][12]

**补充证据**

**树突状细胞（DC）：最强的直接证据链**

截至 2026-10-17，在可核实证据中，能在 DC 内闭合“m⁶A 蛋白→RNA/分子→功能”的最强链条是 **YTHDF1（Reader）**；其余 WER 多为通用名册或研究线索，不能自动视为 DC 因果证据。[58] 癌症患者 PBMC 的 DC 经放疗（RT）后 YTHDF1 升高（相关性）；在小鼠 MC38 结肠癌和 B16-OZ 黑色素瘤模型中，电离辐射（IR）下 DC 特异性删除 **Ythdf1** 则增强抗肿瘤反应（遗传因果证据）。[58]

IR 激活 STING/IFN-I；IFNAR 缺失可消除 YTHDF1 诱导，IFN-β 可直接诱导其表达，STAT2 可结合 **Ythdf1** 启动子，形成 STING→IFN-I/STAT2→YTHDF1 链。[58] YTHDF1 作为 m⁶A reader 可识别 m⁶A-mRNA 并促进翻译；在 IR 条件下，RIP-qPCR 证明其在 DC 中结合 **cathepsin A、cathepsin B mRNA**。随后 cathepsin A/B 在溶酶体促进 **STING 蛋白**降解；co-IP 支持 cathepsin–STING 蛋白结合。删除 Ythdf1 或用 E64 抑制 cathepsins 可恢复 STING 和 IFN-β/IFN-I。[58] 现有直接记录未给出 cathepsin 转录本的具体 m⁶A 位点或定量，因此不能把 STING 结合写成 YTHDF1 的直接蛋白互作。

在 B16-OZ 肿瘤小鼠中，IR 后 **Ythdf1-cKO DC 的交叉启动能力约为 WT+IR 的 5 倍**（2024 年 12 月 2 日），MHC-I–SIINFEKL、IFN-I 及 IFN-γ⁺/granzyme B⁺ CD8⁺ T 细胞读出增加；CD80/CD86、吞噬和 DC1/DC2 数量未变。[58] 去除 CD8⁺ T 细胞会削弱该抗肿瘤效应；YTHDF1 缺失 DC 疫苗或 salvianolic acid C（SAC）抑制剂还可增强 IR 及 IR+anti-PD-L1 疗效。[58] 这是“肿瘤+IR”背景下的抑制性方向，不宜泛化；不同癌细胞系的 YTHDF1–IFN-I 结果曾出现冲突。[58]

Han 等 2019 年研究的综述转述称，YTHDF1 缺失降低 DC 溶酶体蛋白酶转录本翻译，减少抗原降解，使更多抗原进入呈递并增强 T 细胞反应；但该记录未给出转录本名称。DC 中 YTHDF1 结合位点富集于终止密码子附近和 3′UTR，这属于定位分布证据。[185][268] 另有胃癌研究把肿瘤细胞 YTHDF1 缺失与成熟 DC 招募和免疫敏感性联系起来，不能当作 DC 内在机制。[47]

**其他调控蛋白、模型与证据边界**

通用 WER 证据将 METTL3/METTL14/WTAP 归为 Writers、FTO/ALKBH5 归为 Erasers，将 YTHDF1–3、YTHDC1/2 和 IGF2BP1–3 归为 Readers；METTL3–METTL14 是催化复合体，WER 可影响 RNA 稳定性、剪接、定位、翻译和降解。[547][550][299] “METTL3 介导 mRNA m⁶A 促进 DC 激活”有 2019 年研究题名和参考线索，但现有记录未显示其 DC 模型、具体 RNA 或读出；METTL3 lactylation 改变 RNA 捕获的证据来自肿瘤浸润髓系细胞，并非 DC 特异证据。[550][459] YTHDF1–翻译起始因子/YTHDF3、YTHDF3–PABP1/eIF4G2–FOXO3，以及 YTHDC1–SRSF3 的互作来自非 DC 系统；HeLa 的 YTHDF 实验、FMRP 的 HEK293T/小鼠皮层实验和 MSC 的 METTL16–YTHDF2–MCP1 链均不能替代 DC 证据。[182][487][55][291][546] 直接机制应区分 m⁶A-Seq、PAR-CLIP、RIP-qPCR、LC-MS/MS 与遗传扰动等证据层级。[291][547]

DC 本身是连接先天与适应性免疫的专业抗原呈递细胞；识别肿瘤相关抗原（TAA）可启动 T 细胞介导的抗肿瘤反应，但肿瘤微环境中的 DC 也可能功能障碍并促进免疫逃逸。[88] 小鼠 BMDC（3–4 月龄 C57BL/6 雌鼠、CD11c⁺>97%）经 20 μg/ml poly(I:C) 处理 1、3、6、12、24 h 后，24 h CD86 约升高 10 倍，CD40/CD80/MHC-II 也升高；早期上调抗病毒、IFN-I、Tnf-alpha，晚期上调 Tap1/2、Tapbp、抗原加工、共刺激和迁移。TAP1/2 将肽送入内质网，Tapbp 参与 MHC 装载和 T 细胞激活；这些是 DC 成熟背景，未操纵或检测 m⁶A。该时间程的整体下调程序和重复间的上/下调差异也提示状态与分析方法会影响结论。[551]

LPS-成熟 BMDC/脾 DC 的刚度—WASp 研究同样不是 m⁶A：成熟 DC 刚度增加可提高小鼠 CD4⁺ T 细胞对低浓度肽-MHC 的敏感性，WASp-KO DC 约软 20%且启动能力下降，但较硬的活性 WASp DC 并未更有效；评议认为 WASp-KO 效应可能是异常值，抗原呈递扰动及相反结果限制因果解释。[552] 因此，DC 总结行应把 **YTHDF1—cathepsin A/B mRNA—STING/IFN-I—交叉呈递/抗肿瘤功能**列为已核实主链，并将 METTL3 激活线索、其他 WER、具体 m⁶A 位点及未证实互作保留为证据缺口。[58][550][62]

DC直接证据主要是METTL3和YTHDF1：小鼠BMDC/maDC、LPS条件下，METTL3使CD40、CD80、TIRAP mRNA m⁶A化并增强翻译（非寿命），经TLR4/NF-κB促成熟、抗原呈递、T细胞激活及IL-6/TNF-α/IL-12；敲除或催化突变不能救援。[412]YTHDF1促CD40/CD80翻译，但肿瘤DC中促溶酶体蛋白酶mRNA翻译、限制新抗原交叉呈递；缺失增强CD8⁺交叉启动。[412][236]CCR7时YTHDF2促m⁶A-lnc-Dpf3降解并影响迁移；METTL3→miR-338-3p→Dusp16→Th17仅题名线索。[237][544]METTL14/WTAP属复合体[412]；YTHDF1-eIF3、YTHDF2-CNOT1/CCR4-NOT为一般互作[237]，未证实DC特异因果；条目未给m⁶A因果。[93][545]

DC中，METTL3→CD40/CD80/Tirap m⁶A促进翻译、成熟激活[403]；YTHDF1→溶酶体蛋白酶↑、交叉呈递↓[312]；放疗时其→cathepsin-STING/IFN-I↓，敲除增强CD8抗肿瘤[111]。

最强的树突状细胞（DC）因果链是：METTL3 在 CD40、CD80、TIRAP mRNA 上写入 m⁶A，YTHDF1 识别并增强翻译，促进 DC 激活和 T 细胞启动；METTL3 缺失削弱 DC 激活及 CD4⁺ T 细胞启动[404][411]。YTHDF1–eIF3 是翻译互作；肿瘤小鼠 DC 中，YTHDF1 促进溶酶体蛋白酶翻译和新抗原降解，抑制交叉呈递，缺失则增强 CD8⁺ T 细胞交叉启动和抗肿瘤免疫[249][465]。YTHDF2 加速 m⁶A-lnc-Dpf3 降解并可促进 DC 迁移；有报告称 YTHDC1 抑制交叉呈递[411][92]。METTL3–miR-338-3p–DUSP16 轴促进抗原特异性 Th17 反应，但直接 m⁶A 位点未明[410]。一项 DC MeRIP-seq 未检出 CD40 m⁶A，提示靶点具细胞类型特异性[548]；人 mo-DC 经 MPLA/IFN-γ 成熟 4–6 h 时细胞因子达峰，≥24 h 下降，6 h 组诱导 T 细胞增殖约为 24–48 h 组 2 倍[553]。KIRC 中 ZC3H13 与 DC 浸润仅为关联，非直接因果证据[549]。

整体报告可按调控蛋白、细胞机制和总结表组织，本节核查 DC 的 m⁶A—免疫功能关系。证据层级上，RIP-qPCR 直接显示放疗时 YTHDF1 结合 cathepsin A/B RNA；m⁶A 位点突变、翻译效率测定、条件敲除/双敲除及 METTL3 野生型而非催化突变体救援支持机制与因果，而患者放疗后 YTHDF1 升高与结局仅为相关证据；不同癌细胞系的 YTHDF1–IFN-I 结果相冲突，但本 DC 放疗模型支持其经 cathepsins 促 STING 降解，降低 IFN-I 和交叉启动。[58][412]

rejected：number_unsupported。本小节仅有树突状细胞（DC）证据：METTL3（writer）在小鼠 imDC、LPS 成熟 maDC 和 DCreg 中修饰共刺激分子及 TIRAP mRNA 并提高翻译，促进 DC 成熟、TLR/NF-κB 促炎因子产生和 T 细胞激活；YTHDF reader 提高溶酶体蛋白酶 mRNA 翻译，削弱抗原交叉呈递。该证据不应外推到其他免疫细胞。[412][236]

rejected：number_unsupported。对树突状细胞（DC）而言，METTL3 的直接目标是共刺激分子和 TIRAP mRNA，修饰后翻译增强；YTHDF reader 识别溶酶体蛋白酶 mRNA 并提高翻译，导致抗原降解加快、交叉呈递减弱。证据范围仅限 DC。[412][236]

rejected：number_unsupported。树突状细胞（DC）中，METTL3—共刺激分子及 TIRAP—翻译增强—DC 成熟及 TLR/NF-κB 促炎因子和 T 细胞激活构成正向链；相反，YTHDF reader 提高溶酶体蛋白酶翻译、加快抗原降解、削弱交叉呈递，缺失该 reader 则增强肿瘤抗原呈递和细胞毒性 T 细胞应答。该链仅限 DC。[412][236]

树突状细胞（DC）方面，现有来源仅给出通用机制：YTHDC1 是一种核内 m⁶A reader，特异性识别并结合含 m⁶A 的 RNA；其通过与 SRSF3 和 SRSF10 相互作用，促进邻近 m⁶A 位点的 SRSF3 招募和 exon inclusion，同时阻止促进 exon skipping 的 SRSF10 结合、抑制 exon skipping；该来源未提供 NK、DC、巨噬细胞或 T 细胞中的具体免疫细胞实验背景或功能终点。[232]

### 巨噬细胞：极化、信号与抗肿瘤功能

| 免疫细胞类型 | 关键m⁶A调控蛋白 | 调控目标与机制 | 对细胞功能的最终影响 |
|---|---|---|---|
| 巨噬细胞：极化 | METTL3 | STAT1 CDS/3′UTR甲基化，稳定性↑ | 促进M1样极化，抑制M2样表现 |
| 巨噬细胞：STAT1清除 | YTHDF2 | RBM4促进读取并降解STAT1 | 降低糖酵解和M1样激活 |
| 巨噬细胞：感染/MC38 | METTL3 | 促进Irakm降解，解除TLR信号抑制 | 支持抗菌及抗肿瘤功能 |
| TAM：B16/LLC | METTL3、YTHDF1 | 促进SPRED2翻译；缺失增强ERK/NF-κB/STAT3 | 缺失促进肿瘤生长与转移 |
| 肿瘤浸润髓系细胞 | METTL3、YTHDF1 | 乳酸相关环境增强Jak1翻译及STAT3 | 支持免疫抑制；缺失可限制肿瘤 |
| 巨噬细胞：LPS | YTHDF2 | 促进MAP2K4/MAP4K4周转 | 敲低增强促炎因子和炎症 |
| TAM | YTHDF2 | 缺失增强IFN-γ–STAT1相关程序 | 增强呈递及CD8⁺抗肿瘤反应 |
| 巨噬细胞：极化 | FTO、YTHDF2 | FTO支持STAT1/PPARγ等RNA稳定 | FTO耗竭可同时削弱M1、M2激活 |
| 巨噬细胞：代谢极化 | IGF2BP2 | 稳定TSC1和PPARγ转录本 | 限制M1样、支持M2样程序 |
| 巨噬细胞：ADAP缺失 | METTL3、IGF2BP2 | Spry1 A6988相关甲基化及稳定性↑ | NF-κB和LPS炎症增强 |

主要依据为STAT1、IRAKM、SPRED2、ADAP–Spry1及相应Reader研究。[32][33][4][34][10][14]

### 巨噬细胞：核输出、代谢和跨细胞调节

| 免疫细胞类型 | 关键m⁶A调控蛋白 | 调控目标与机制 | 对细胞功能的最终影响 |
|---|---|---|---|
| 病毒感染巨噬细胞 | ALKBH5 | DDX46招募；Mavs/Traf3/Traf6去甲基化并核保留 | 抑制Ⅰ型干扰素产生 |
| 巨噬细胞：病毒代谢 | ALKBH5 | 缺失增加相关RNA衰减、降低OGDH | 增强非干扰素依赖病毒限制 |
| 巨噬细胞：脓毒症 | METTL3 | HIF-1α诱导Pfkm甲基化及PFKM蛋白↑ | 增强糖酵解及炎症输出 |
| 巨噬细胞：DSS肠炎 | METTL3、YTHDF3 | METTL3耗竭提高PGP相关表达，重编程代谢 | 抑制Th1反应、减轻肠炎 |
| TAM：高脂肝癌环境 | METTL3 | 稳定Cpt1a，支持脂肪酸代谢 | 促进M2样状态和肿瘤进展 |
| 动脉粥样硬化巨噬细胞 | METTL3 | 稳定HDGF相关RNA，重编程代谢 | 增强M1样炎症及斑块进展 |
| C1q⁺ TAM | METTL14 | 缺失使Ebi3 m⁶A下降、EBI3表达↑ | 促进CD8⁺功能异常及肿瘤 |
| 真菌感染巨噬细胞 | YTHDC2 | 敲低使TLR2以m⁶A依赖方式升高 | TNF-α、IL-1β增加 |
| TAM：肿瘤细胞间接作用 | ALKBH5、FTO | 肿瘤NEAT1/CXCL8或CSF1相关调节 | 增加募集或M2样偏转 |

上述核输出、代谢、感染及间接机制，分别对应正文中的指定模型。[17][36][35][37][6][26]

### T细胞：稳态、分化与炎症反应

| 免疫细胞类型 | 关键m⁶A调控蛋白 | 调控目标与机制 | 对细胞功能的最终影响 |
|---|---|---|---|
| 初始CD4⁺ T细胞 | METTL3、METTL14 | Socs1/Socs3/Cish降解↑，解除IL-7/STAT5抑制 | 支持稳态增殖和分化 |
| 成熟Treg | METTL3 | SOCS周转维持IL-2/STAT5信号 | 维持抑制功能和免疫耐受 |
| 诱导性Treg | METTL3、METTL14 | 支持Foxp3稳定性及相关mTOR调节 | 支持分化和谱系功能 |
| Tfh：Tcf7模型 | METTL3 | Tcf7 3′UTR m⁶A稳定RNA，维持TCF-1 | 促进Tfh及生发中心反应 |
| Tfh：VHL缺失模型 | METTL3 | Icos甲基化及降解增加 | 抑制Tfh分化 |
| 炎症CD4⁺ T细胞 | ALKBH5 | 去甲基化并稳定Ifng、Cxcl2 | 增强炎症、组织浸润及中性粒细胞募集 |
| 致病Th17相关模型 | YTHDC2 | m⁶A依赖稳定ASH1L | 限制致病程序、减轻葡萄膜炎 |
| γδ T前体 | ALKBH5 | 调节Jagged1/Notch2；缺失使相关信号下降 | 前体扩增及感染保护增强 |

主要依据为T细胞稳态、Tfh位点机制、ALKBH5及相关谱系研究。[6][5][18][26][41]

### T细胞：存活、抗肿瘤与耗竭

| 免疫细胞类型 | 关键m⁶A调控蛋白 | 调控目标与机制 | 对细胞功能的最终影响 |
|---|---|---|---|
| 活化CD8⁺ T细胞 | FTO、IGF2BP3 | FTO缺失使Fas甲基化、稳定性及表达↑ | 凋亡增加，效应群体扩增减少 |
| 急性感染CD8⁺ T细胞 | METTL3 | 稳定Tbx21，维持T-bet | 支持效应分化、记忆和再次应答 |
| 肿瘤浸润Treg | YTHDF2 | 降解Nlrc3/Nfkbie/Traf3，维持NF-κB反馈 | 缺失削弱Treg并释放CD8⁺抗肿瘤功能 |
| 肿瘤CD8⁺ T细胞 | METTL3 | 稳定DNMT3B并强化耗竭相关染色质状态 | 预印本支持其推动终末耗竭 |
| CD8⁺ T细胞：DC间接作用 | DC中的YTHDF1 | 缺失减少蛋白酶，增强交叉呈递 | 抗原特异性CD8⁺应答增强 |
| CD8⁺ T细胞：肿瘤间接作用 | 肿瘤细胞中的YTHDF2 | 缺失延长MHC-I mRNA寿命 | 增强肿瘤可见性及T细胞依赖控制 |

其中FTO–Fas与Treg YTHDF2为已发表原始机制研究；METTL3–DNMT3B行对应2026年预印本。[29][42][43][31][44]

**资料口径统一。** 本文区分原始机制实验、疾病模型结果、综述归纳及人体相关性。m⁶A免疫沉淀富集区不等于单碱基修饰比例；共免疫沉淀也不自动证明直接结合。Lyz2/Lyzm-Cre影响多类髓系细胞，不能将全部体内结果仅归于巨噬细胞。数值采用原研究实测或原文近似值，不合并为跨模型效应量；预印本已单独标明。

**最终判断落在具体RNA。** 最可靠的m⁶A免疫结论，不是某个调控蛋白“总体促免疫”，而是它在指定细胞状态中，改变哪条RNA的翻译、寿命或定位，并由此改变哪一种功能。这也是比较METTL3、FTO和YTHDF家族，及理解不同研究方向差异的关键。

**补充证据**

| 对象 | 免疫细胞类型 | 关键m⁶A调控蛋白 | 调控目标与机制 | 表格中的最终功能影响 | 对细胞功能的最终影响 |
| --- | --- | --- | --- | --- | --- |
| 自然杀伤细胞（NK细胞） | 未找到证据 | 研究对象是乳腺癌患者与健康对照者的原代人 NK 细胞；研究聚焦 NKG2D 通路… | METTL3经m⁶A调控Ptpn11/SHP-2，维持IL-15–AKT/MAPK信号[91] | 维持NK细胞稳态、肿瘤浸润、效应功能及抗肿瘤免疫[91] | FTO 缺失的 NK 细胞表现出肿瘤杀伤活性、细胞因子产生和细胞存活率增加；Fto −/− 小鼠脾脏 NK…[515] |
| 树突状细胞（DC） | 在人类血液、脾脏和扁桃体中已鉴定出两种经典树突状细胞亚群，分别为 CD141/BDCA-3+ 或…[575] | DC 在肿瘤进展中的作用取决于具体情境：它们既可能促进癌症发展，也可能抑制癌症发展；其核心免疫功能是向 T…[168] | 在树突状细胞中，YTHDF1 影响溶酶体蛋白酶转录本的翻译效率；YTHDF1 缺失降低翻译效率，减少抗原降解…[185] | DC 在肿瘤进展中的作用取决于具体情境：它们既可能促进癌症发展，也可能抑制癌症发展；其核心免疫功能是向 T…[168] | DC 在肿瘤进展中的作用取决于具体情境：它们既可能促进癌症发展，也可能抑制癌症发展；其核心免疫功能是向 T…[168] |
| 巨噬细胞 | 巨噬细胞，具体为LPS处理的RAW264.7细胞和M1巨噬细胞极化模型。[578] | 在 DSS 诱导结肠炎小鼠中，造血细胞缺失 IGF2BP2 的小鼠出现更严重的疾病；IGF2BP2…[372] | 在巨噬细胞中，YTHDF3 缺失或沉默降低 VSV RNA、VSV 糖蛋白和病毒滴度；对 EMCV 和…[187] | 在巨噬细胞中，YTHDF3 缺失或沉默降低 VSV RNA、VSV 糖蛋白和病毒滴度；对 EMCV 和…[187] | 在脂肪组织巨噬细胞中，磷酸化IRX3二聚化并转位入核，直接结合IL-1α、IL-1β…[239] |
| T 细胞 | T 细胞中，CD28 信号诱导 eIF3 结合 TCR mRNA 的 3′UTR，促进快速翻译并支持 T…[208] | 在该 CD8+ T 细胞模型中，FTO 缺失对活化和增殖影响有限，但显著增加免疫应答期间的细胞死亡…[562] | YTHDF1 直接或支持作用的目标包括与 T 细胞受体（TCR）信号相关的 mRNA 转录本；METTL3…[332] | 在小鼠 T 细胞中，METTL14 缺失导致自发性结肠炎，并伴随炎症细胞浸润增加、结肠重量/长度比升高以及…[270] | 在小鼠 T 细胞中，METTL14 缺失导致自发性结肠炎，并伴随炎症细胞浸润增加、结肠重量/长度比升高以及…[270] |

证据最完整的链条分别是：NK 细胞中的 METTL3–IL-15 信号和 YTHDF2–效应功能轴；DC 中的 METTL3–CD40/CD80/TIRAP 翻译轴及 YTHDF1–STING/IFN-I 轴；巨噬细胞中多个依刺激和亚群而变的 m⁶A 轴；T 细胞中的 METTL3–SOCS–IL-7/STAT5 轴。[58][57][566] 下表固定为四行、四列；“关键”优先指有遗传或药理扰动、RNA 结合或明确功能读出的蛋白。不同细胞状态、刺激和疾病模型不合并为单一方向。

**四类免疫细胞总结表**

| 免疫细胞类型 | 关键m⁶A调控蛋白 | 调控目标与机制 | 对细胞功能的最终影响 |
|---|---|---|---|
| NK细胞 | METTL3（Writer）、YTHDF2（Reader）；FTO（Eraser）的方向性证据亦已报道。[345][519] | 在小鼠 NK 细胞中，METTL3 缺失减少 NK 细胞数量，并损害 IL-15 驱动的存活、增殖和激活，主要涉及 AKT–mTOR、MAPK–ERK，而 JAK–STAT5 未见显著变化；Ptpn11/SHP-2 是其关联目标。IL-15–STAT5 信号正向调节 YTHDF2；YTHDF2 结合 m⁶A 转录本，Tardbp 被用于下游验证，但当前片段未列出完整直接靶标谱。人 CRC 相关 NK 细胞中，SMAD4 可经 YTHDF2 上调 NKG2D，YTHDF2 干扰会降低 GZMB。FTO 缺失可增强细胞毒性，但其具体目标 RNA 和位点尚未在本证据组中确定。[331][519][570] | METTL3 和 YTHDF2 总体支持 NK 细胞稳态、IL-15 依赖的效应功能以及抗肿瘤、抗病毒免疫；YTHDF2 缺失降低 IFN-γ、GZMB、perforin 和细胞毒性。FTO 缺失在小鼠黑色素瘤转移模型及人白血病相关 NK 模型中增强细胞毒性。上述方向限于 IL-15、病毒或肿瘤模型，不能无条件外推到所有 NK 亚群。[519] |
| 树突状细胞（DC） | METTL3（Writer）、YTHDF1（Reader）；YTHDF2–lnc-Dpf3 轴属于补充证据。[366][58][237] | METTL3 对 CD40、CD80 和 TIRAP mRNA 加入 m⁶A，YTHDF1 识别这些转录本并增强翻译；YTHDF2 可识别 m⁶A 修饰的 lnc-Dpf3 并促进其降解。在小鼠肿瘤浸润 DC 和 BMDC 中，放疗诱导 YTHDF1 结合 cathepsin A/B RNA，增加溶酶体 cathepsin，继而促进 STING 降解并降低 I 型干扰素；删除 Ythdf1 则保留 STING、提高 IFN-I。另一类肿瘤抗原模型中，YTHDF1 缺失通过改变溶酶体蛋白酶翻译增强交叉呈递，提示作用取决于刺激和近端目标。[366][237][58][236] | METTL3 缺失会降低 DC 成熟、共刺激分子和 T 细胞启动能力；其 m⁶A–翻译作用总体促进 DC 激活。相反，在放疗模型中，Ythdf1 缺失使 DC 交叉启动能力增加 **5 倍**（Ythdf1-cKO+IR 对 WT+IR，B16-OZ 小鼠模型，2024 年），并增强 IFN-I、CD8⁺ T 细胞杀伤及放疗抗肿瘤效果。[403][58] 因而 YTHDF1 的功能方向不能脱离“经典肿瘤抗原模型”与“放疗–STING 模型”比较。 |
| 巨噬细胞 | METTL3、METTL14、WTAP（Writers）；FTO、ALKBH5（Erasers）；YTHDF1、YTHDF2、YTHDF3、IGF2BP2（Readers）。证据来自 RAW264.7、BMDM、腹腔巨噬细胞和 TAM，涉及 LPS、IFN-γ、IL-4、感染、肿瘤及代谢刺激。[57][372][241] | METTL3 对 IRAK3/IRAKM mRNA 加入 m⁶A并促进降解；缺失后 IRAK3 稳定、TLR4 激活受抑。另一模型中，METTL3 稳定 STAT1 mRNA，促进 M1 极化。METTL14 写入 Socs1 mRNA，YTHDF1 促进 SOCS1 翻译，形成 TLR4/NF-κB 负反馈；FTO 去甲基化会降低 YTHDF1 对 Socs1 的结合。METTL3–IGF2BP2 可稳定 Spry1 mRNA并激活 NF-κB；IGF2BP2 还稳定 TSC1、PPARγ mRNA，偏向 M2 代谢和表型。YTHDF2 可促进 IL-6R 或 Stat1 mRNA 降解并参与 TAM 重编程。2025 年 LPS–RAW264.7 模型中，YTHDF3 促进 Cd36、Irak1、Tab1/2、Tirap mRNA 快速降解，使 p38 信号和巨噬细胞活化受抑；WTAP 增强 IL6ST、IL15RA、IL18R1 等转录本的翻译，ALKBH5 则可降低 IL-11 m⁶A并提高其稳定性。[548][404][370][252][372][473][521][57][385][450] | 方向具有明显的状态依赖性。在 100 ng/mL LPS 刺激的 RAW264.7 细胞中，YTHDF3 敲低提高促炎因子、NO、吞噬和肿瘤杀伤，说明 YTHDF3 在该模型中负向调节活化。[57] 但 METTL3 缺失对 TNF、IL-6、M1 极化和吞噬的结果在不同 BMDM、感染、脓毒症及肿瘤模型中相互矛盾；IGF2BP2 缺失也可在结肠炎中加重病变、在过敏性肺炎中减轻 M2 极化。[243][398][354] 因此表格不能把“促进 M1”或“促进 M2”写成巨噬细胞的普遍规律。 |
| T 细胞 | METTL3、METTL14、WTAP（Writers）；ALKBH5、FTO（Erasers）；YTHDF1/2/3 及 IGF2BP3（Readers）。直接证据主要来自初始 CD4⁺、CD8⁺、Treg、γδ T 细胞前体和 iNKT 细胞，而非未分化的“全部 T 细胞”。[566][328][369] | METTL3 对 Socs1、Socs3、Cish mRNA 加入 m⁶A；YTHDF1/2/3 识别这些转录本并促进其较快降解，从而调节 IL-7/STAT5、初始 T 细胞稳态、增殖和分化。人原代 CD4⁺ T 细胞中，METTL3–YTHDF2 促进 CD40L mRNA 降解。ALKBH5 去除 CXCL2 和 IFN-γ mRNA 的 m⁶A，增强其稳定性和翻译，促进 Th1 功能；在小鼠 γδ T 细胞前体中，ALKBH5 缺失改变 Jagged1/Notch2 并扩大前体库，但成熟 γδ T 细胞的 IFN-γ、IL-17、增殖和凋亡未受明显影响。Treg 中，m⁶A 维持抑制功能；肿瘤浸润 Treg 的 YTHDF2 缺失会降低其存活和抑制作用。FTO–IGF2BP3 还被题录联系到 CD8⁺ T 细胞 Fas mRNA 稳定性，但该片段未提供完整实验细节。[566][437][369][332][72][347][478] | m⁶A 对 T 细胞的最终结果包括维持初始 T 细胞稳态、促进或限制亚群分化、维持 Treg 抑制功能以及调节 CD8⁺ T 细胞效应和记忆形成。METTL3–SOCS 轴的方向是“增强 m⁶A 后促进 SOCS mRNA 降解，从而释放 IL-7/STAT5”；METTL3 或 YTHDF2 的作用则可能随 CD4⁺、CD8⁺、Treg、Th1 或 γδ 亚群而变。T 细胞中 WTAP 的 TCR 信号和存活证据目前主要来自研究题名，尚不足以填入具体直接目标。[170][251][566][332][347] |

**表格结论与判定条件：**四类细胞不能按“m⁶A 增加即增强或抑制免疫”作统一排序。最稳定的比较是：METTL3 在 NK、DC 和部分巨噬细胞模型中提供写入层证据；YTHDF1 在 DC 中受放疗背景强烈影响；YTHDF2 在 NK 和肿瘤相关 Treg、巨噬细胞中连接 RNA 命运与功能；巨噬细胞和 T 细胞的方向则最依赖亚群、刺激、疾病状态和遗传扰动。只有同时满足“指定细胞—具体蛋白—目标 RNA—分子后果—功能读出”的研究，才可视为完整因果链；仅有题名、综述概括或跨细胞推断的字段应保留为补充或未确立状态。

补充：YTHDF3促m⁶A RNA翻译/降解，免疫仅有浸润关联[90]；YTHDC1对单m⁶A RNA的KD为300 nM、未修饰RNA不结合[61]；IGF2BP识别m⁶A增强稳定/翻译，HIV-MT4中56个基因m⁶A升高而CD4/Jurkat未复现[65]；NK/DC条目未给m⁶A因果[93]。

ALKBH5：催化单链 mRNA 的 m⁶A 去甲基化，产物为腺嘌呤和甲醛；该证据无免疫细胞模型，不能填充细胞行。[98]

NK|METTL3/YTHDF2/FTO/METTL14|SHP-2/Tardbp/Crebzf→IL-15/RNA[92][519]；早期缺失致NK减少[518]|稳态/成熟/细胞毒性/抗肿瘤；FTO缺失↑[515]；WTAP关联  
DC|METTL3/YTHDF1/YTHDF2|CD40/80/Tirap翻译；YTHDF1呈递；YTHDF2-Dpf3/CCR7[365][571]|成熟/T细胞激活/CD8启动  
巨噬|METTL3/FTO/YTHDF2|STAT1/IL-6R/Pyk2→NFκB/MAPK[401][473][556]|M1/M2极化/炎症依模型  
T|METTL3/YTHDF1/YTHDF3|SOCS/IL-7-STAT5、CD8/Th/HIV[401]|稳态/分化/Treg/抗瘤/HIV

rejected；reason=citation_outside_operands；允许数字：空值、2024, 55(1): 81-87.；允许引用：[170][85][89][91][93][94][567][99]；允许实体：T 细胞、自然杀伤细胞（NK细胞）。

rejected；reason=no_citation；允许数字：无；允许引用：[170][91]；允许实体：T 细胞、自然杀伤细胞（NK细胞）。

rejected；reason=no_citation；允许数字：无；允许引用：[170][91]；允许实体：T 细胞、自然杀伤细胞（NK细胞）。

rejected；reason=no_citation；允许数字：无；允许引用：[170][91]；允许实体：T 细胞、自然杀伤细胞（NK细胞）。

rejected；reason=no_citation；允许数字：无；允许引用：[170][91]；允许实体：T 细胞、自然杀伤细胞（NK细胞）。

rejected；reason=number_unsupported；允许数字：空值、2021、2020、2018、2024, 55(1): 81-87.、28 July 2026; 2026 year、2022-10-10、~100 times、0.4 μg; 0.5 μg；允许引用：[159][170][185][59][188][62][63][85][87][89][91][92][93][94][95][567][97][99][545][568][295][569][375][561][391][571][401][432][476][512][572][515][516][518][573][543][574][576][577][531][578]；允许实体：T 细胞、自然杀伤细胞（NK细胞）、树突状细胞（DC）、巨噬细胞。

rejected；reason=number_unsupported；允许数字：空值、2021、2020、2018、2024, 55(1): 81-87.、28 July 2026; 2026 year、2022-10-10、~100 times、0.4 μg; 0.5 μg；允许引用：[159][170][185][59][188][62][63][85][87][89][91][92][93][94][95][567][97][99][545][568][295][569][375][561][391][571][401][432][476][512][572][515][516][518][573][543][574][576][577][531][578]；允许实体：T 细胞、自然杀伤细胞（NK细胞）、树突状细胞（DC）、巨噬细胞。

rejected；reason=number_unsupported；允许数字：空值、2021、2020、2018、2024, 55(1): 81-87.、28 July 2026; 2026 year、2022-10-10、~100 times、0.4 μg; 0.5 μg；允许引用：[159][170][185][59][188][62][63][85][87][89][91][92][93][94][95][567][97][99][545][568][295][569][375][561][391][571][401][432][476][512][572][515][516][518][573][543][574][576][577][531][578]；允许实体：T 细胞、自然杀伤细胞（NK细胞）、树突状细胞（DC）、巨噬细胞。

## 附录：其他证据

**补充证据**

**证据口径、范围与边界候选**

本节采用的核心边界是：m⁶A 为 RNA 腺苷 N6 位甲基化，优先讨论内部 RNA，尤其是 mRNA；其免疫效应必须沿“调控蛋白→目标 RNA→RNA 命运→细胞功能”链条判定，而不能仅凭调控因子表达或 m⁶A 峰相关性概括。[46][47] Writers 将甲基写入 RNA，Erasers 去除或重塑该修饰，Readers 识别 m⁶A 后连接剪接、核输出、翻译、稳定性或降解等后果。[50][73] METTL3–METTL14 是催化核心，WTAP、VIRMA/KIAA1429 等主要承担募集、定位或复合体支架作用，不能把所有复合体成员都称为催化酶。[50][51][76]

“相互作用”在本文中分层使用：METTL3–METTL14–WTAP 属于共同写入复合体关系；Reader 与 RNA 的结合属于 RNA 依赖的功能关系；YTHDF2 通过识别 m⁶A-RNA 并连接降解机制属于下游效应关系。它们不自动等同于直接蛋白—蛋白结合。m⁶A 对 RNA 稳定性的方向也不是固定的：YTHDF2 可促进含 m⁶A RNA 的去稳定化，而 IGF2BP 家族在特定背景下可增强 mRNA 稳定性和翻译。[45][73][74]

证据强度按直接生化或催化实验、遗传扰动及回补、细胞功能实验、体内表型和关联性依次区分。MeRIP-seq、miCLIP-seq 或 LC–MS/MS 能显示修饰区域、位点或总体水平，但单独不能证明某蛋白直接造成某项免疫表型。[73] 因此每项结论均需同时记录物种、细胞亚群、刺激、遗传或药理扰动和主要读出；研究范围固定为 NK 细胞、DC、巨噬细胞和 T 细胞，其他亚群只能作为条件化证据，不能跨模型外推。用户禁止的文章、URL 及其镜像或重复元数据不纳入证据。

两个模型说明这种口径的必要性。小鼠初始 CD4⁺ T 细胞中，Mettl3 或 Mettl14 条件性缺失、IL-7 刺激和催化活性回补共同支持直接因果链：Socs1、Socs3 和 Cish mRNA 的 m⁶A 标记丢失、降解变慢，继而抑制 IL-7/JAK/STAT5 信号，使稳态扩增和分化受损；该研究未发现相应翻译效率或剪接差异，因此不能把该结果概括为“m⁶A 普遍促进翻译”。该证据来自小鼠模型和 2017 年原始研究。[75] 2025 年发表的巨噬细胞研究则在小鼠腹腔巨噬细胞、BMDM 和 RAW 264.7 细胞中，以 LPS（1 μg/ml，6 h）及 METTL3、IGF2BP2 扰动显示：METTL3 写入 Spry1 mRNA 的 m⁶A，IGF2BP2 识别并稳定该转录本，随后增强 NF-κB 相关 TNF-α、IL-1β 和 IL-6 反应；这是一条刺激和细胞状态依赖的机制，不应直接推广到所有巨噬细胞。[77] 另有 HeLa/外源 circRNA 研究显示，YTHDF2 隔离 m⁶A-circRNA，限制 RIG-I–MAVS–IRF3 信号；未修饰 circRNA 才能诱导先天免疫和体内佐剂效应。该结果说明 m⁶A 能改变免疫识别，但不是四类免疫细胞内在机制的直接证据。[49]


| 候选 | 当前决定与理由 |
|---|---|
| METTL16 | 保留为不确定候选。允许来源所示的直接功能是 U6 snRNA m⁶A 及 SAM synthetase intron retention；另有胰腺癌“抗肿瘤免疫”关联，但未同时给出免疫细胞、具体 m⁶A 底物和因果链，因此暂不列入 canonical mRNA m⁶A 免疫核心。[47] |
| ALKBH3 | 不列入 canonical m⁶A Eraser 核心。其直接证据是在人 PANC-1 癌细胞及体外体系中去除 tRNA 的 N6-meA，并改变翻译；比较实验显示其不去除 mRNA 的 N6-meA，且没有 NK、DC、巨噬细胞或 T 细胞模型。[48] |
| HNRNPG/RBMX | 保留为不确定候选；当前证据包未形成“直接 m⁶A 识别—免疫细胞 RNA 目标—功能表型”的完整链条，故不写成已确立的核心 Reader。 |
| PCIF1/CAPAM | 排除本报告主 roster；其主要对应帽邻近 m6Am，而本报告优先讨论内部 m⁶A。 |

因此，核心 roster 是开放而非穷尽清单；“候选”“关联”和“未找到直接证据”均保留，不以其他细胞或其他 RNA 修饰的结果填补缺口。

小鼠初始T细胞中METTL3缺失阻断稳态扩增和分化[78]。

最强的边界结论是：m⁶A 因果链必须按物种、细胞类型、刺激和直接读出分层，不能把非免疫模型或综述条目直接外推。METTL14–SMN 研究在 HeLa 细胞及 SMA 患者成纤维细胞中显示，SMN 敲低使 mRNA 总体 m⁶A 下降约 17%；精氨酸甲基化依赖的 METTL14 C 端无序区—SMN Tudor 结构域结合由 GST pull-down 和 co-IP 支持。DNA 损伤/丝裂霉素 C 条件下，SMN、METTL14 或 METTL3 受损会降低 FANCD2 转录本 m⁶A 及蛋白，而 FANCD2 mRNA 基本不变；这是 DNA 修复背景，不是免疫细胞因果证据。[80]

2025 年 CD8⁺ T 细胞耗竭综述将 m⁶A 与耗竭相关 mRNA 的稳定性、剪接、运输和翻译联系起来，并列出 METTL3–Tcf7/Myc/代谢调控因子及 ALKBH5–效应转录本关系；其还转述肝细胞癌浸润 CD8⁺ T 细胞中的 WTAP–PD-1 mRNA–YTHDF1 翻译链及 WTAP 敲低改善抗 PD-1 疗效。但该页面未给出相应遗传扰动、物种和直接读出，故应标为综述性证据。[79]

四类细胞的证据完整度不同：NK 细胞方面，允许综述目录列出 2021 年 METTL3 抗肿瘤及 YTHDF2 抗肿瘤/抗病毒研究，但当前片段没有给出目标 RNA，不能由题名补写完整机制。[52] DC 方面，放疗相关模型直接显示 YTHDF1 结合 cathepsin A/B 相关 RNA，促进溶酶体介导的 STING 降解；DC 特异性删除 Ythdf1 后，IFN-I、交叉呈递和交叉启动增强，交叉启动能力约为对照的 5 倍。[58] 巨噬细胞方面，在 100 ng/mL LPS 刺激的 RAW264.7 细胞中，YTHDF3 促进 Cd36、Irak1、Tab1/2 和 Tirap mRNA 降解；敲低 Ythdf3 提高其稳定性、p38 磷酸化、促炎因子、NO、吞噬和肿瘤杀伤，且稳定性在 0–2 h ACTD 追踪中检测。[57] T 细胞方面，目录仅提示 2017 年 IL-7/STAT5/SOCS、2020 年 METTL14 缺失性结肠炎和 2022 年 ALKBH5–SLE 研究，需与上述 CD8⁺耗竭证据分开记录。[52][79]

NK/DC 比例、CD56bright/dim 亚群、TAM 的 JAK/STAT 极化、缺血性卒中免疫浸润以及 FasL–Fas 或 perforin/granzyme 杀伤，均属于细胞功能背景，不能单独证明 m⁶A 链条。[81][83][84][85][82]

Roster 审计中，METTL14 的非催化支架角色仍应保留历史冲突：mESC 早期报告 Mettl3 缺失后约保留 40% m⁶A，后续研究则报告删除 Mettl3 或 Mettl14 可使 mRNA m⁶A 损失约 99%；DepMap 21Q4 中 1,054 个细胞系有 801 个依赖 METTL3，其中 683 个同时依赖 METTL14/WTAP，这支持复合体共依赖而非免疫因果。[86] METTL16 作用于 U6 snRNA、MAT2A 及其他 RNA，并有 m⁶A-independent 功能，但目前未见直接免疫模型，暂列边界候选。[86][56] FTO 帽结构实验测的是 m⁶Am：去除 m⁷G cap 使活性下降 50%，再去除 cap triphosphate group 额外下降 40%，不应并入内部 m⁶A。[87] YTHDC1、HAKAI、IGF2BP3 及 HeLa 中的 YTHDF 生化/活力结果可说明一般 RNA 机制，却不能替代四类免疫细胞的直接证据。[55][56][59][60]

本批证据用于划定直接机制边界：m⁶A调节mRNA剪接、翻译和稳定性[92]；但MeRIP峰变化可能只是表达变化，HIV感染MT4细胞报告的56个基因在原代CD4⁺及Jurkat未复现，不能跨模型外推[65]。YTHDC1 reader与含单个m⁶A RNA的KD=300 nM结合，未修饰RNA无结合（2023-12-11）[61]；YTHDC1/YTHDF2结构研究支持直接识别[66]。DC证据仅支持抗原呈递、启动T细胞；TME中可功能障碍并促免疫逃逸，LM感染或Mtb-EVs仅报告细胞因子、ROS，未给出m⁶A蛋白、目标RNA或机制[88][93]。小鼠肿瘤NK中，METTL3缺失降低SHP-2（Ptpn11）蛋白表达，削弱IL-15–AKT/MAPK，损害稳态、成熟、浸润和细胞毒性[91][92]。RBMX/HNRNPG敲除经H2-K1/THBS1增加骨肉瘤CD8⁺T浸润，但未证实为m⁶A reader，资格不确定[89]；YTHDF3可促mRNA翻译及含m⁶A RNA的翻译/降解，但TCGA/TIMER/CIBERSORTx仅显示其与乳腺癌NK、DC、巨噬、T浸润的关联，非细胞内因果[90][62]。病毒晚期巨噬细胞中YTHDC2招募ISG20降解IFN-β mRNA、抑制抗病毒反应；FAM76B–HNRNPA2B1直接结合调节NF-κB炎症，但该关系不是经典m⁶A证据[63][64]。

小鼠/人T细胞中，METTL3–m⁶A调控SOCS、Tbx21、CD40L，影响稳态、分化、效应和记忆；EAE与EAU的Th17方向相反，不能泛化[94]。小鼠NK中METTL3/YTHDF2–Ptpn11/Tardbp关联效应与增殖，人NK体外证据仍缺[95]。DC中METTL3促进CD40/CD80/TLRAP翻译，YTHDF1促进溶酶体蛋白酶翻译并削弱交叉呈递[94][95]。巨噬细胞中METTL3–YTHDF2稳定Pyk2，IGF2BP2稳定TSC1/PPARγ[94][96]；HNRNPG/FMRP仅有一般reader证据，ALKBH5仅有一般去甲基化/核斑共定位，均非直接免疫因果证据[95][97][98]。

T细胞：非m⁶A代谢[99]；eIF3促TCR翻译、非m⁶A[71]；DC/BMDC、巨噬模型标条件[100][101][102]；FTO底物依细胞[68]；YTHDF免疫链待证[67][70]；ALKBH5题名[69]。

ALKBH5缺失使γδT前体m⁶A↑、Jagged1/Notch2↓[72]

截至2026-10-17，ALKBH3应保留为不确定候选，不纳入 canonical m⁶A Erasers：野生型人ALKBH3偏好去除m¹A/m³C，不能识别m⁶A；仅D194缺失或Thr133改造体可部分获得m⁶A活性，且无直接免疫模型证据[53][54]。HNRNPG/RBMX可列为非典型Reader/effector候选：其低复杂度RGG区依赖m⁶A诱导的RNA结构变化结合RNA，并与磷酸化RNAPII-CTD协同影响共转录剪接；现有证据来自HeLa/HEK293T，尚无NK、DC、巨噬或T细胞的直接因果功能证据，故不升级为免疫核心成员[103][105][108]。

m⁶A调控稳定性/剪接/翻译。[110]RBMX非直接reader。[113]

m⁶A调控RNA命运并参与免疫，结论依模型而异[112][111]


m⁶A由METTL3写入，FTO/ALKBH5擦除，读者识别。[109]

人源巨噬细胞中，YTHDF2识别m⁶A标记TNF并促降解。[107]容量不足。

METTL3–METTL14–WTAP构成写入复合体；非免疫模型。[104]

HNRNPG/RBMX 有直接 m⁶A reader 证据，却不足入核心免疫 roster：低复杂度 RGG 区结合 m⁶A 暴露 motif，检出 13,191 个高置信位点，并可经 RNAPII/剪接或招募 YTHDF2 降低靶 mRNA 稳定性[281,394,65]。RBMX 敲除虽经 H2-K1/THBS1 改变 CD8⁺T 活性并使 T/NK 增加、巨噬减少，但未证实由 m⁶A reader 活性介导且缺少 rescue，故为边界候选[559,225]。

本节以 m⁶A—免疫调控为主线：m⁶A 是 RNA 中最常见的内部修饰；Writers 通过甲基转移酶复合体写入，Erasers 去除，Readers 识别后改变 RNA 稳定性、剪接、核输出、翻译或降解，并连接先天免疫识别和抗病毒反应[3,1,2,6]。NK、DC、巨噬细胞和 T 细胞分别按“调控蛋白→目标 RNA/分子→RNA 命运或翻译/剪接→细胞表型”展开；直接互作限于明确结合或复合体，功能性互作指经靶 RNA/通路产生的效应，例如 YTHDF2 隔离 m⁶A-circRNA、拮抗 RIG-I，但该证据来自 HeLa 而非 NK[49]。

资料按“定义与 roster—细胞因果链—总结表”组织。当前可核查框架是 METTL3–METTL14–WTAP writer complex 与 FTO/ALKBH5 erasers，m⁶A 影响稳定性、剪接、核输出、翻译和降解[281,314,645]。

在现有 m⁶A 证据边界内，NK 的 FTO 缺失导致过度激活和细胞毒性增强，并可阻止小鼠黑色素瘤转移；DC 的 YTHDF1 抑制 STING/IFN-I 与交叉启动，删除后交叉启动提高 5 倍并增强抗肿瘤功能；巨噬细胞的 YTHDF3 促 Cd36、Irak1、Tab1/2、Tirap mRNA 快速降解并调节 TLR4[379,93,90]。T 细胞证据目前只显示 HIV-1 条件下 PLIN3 mRNA 核内增加、胞质无显著差异，尚未给出 m⁶A 蛋白、明确功能结局或因果链[106]。

总结表列名固定为“免疫细胞类型｜关键 m⁶A 调控蛋白｜调控目标与机制｜对细胞功能的最终影响”，并只纳入可核查行：NK—FTO—下游 RNA 目标未给出—过度激活/细胞毒性增强；DC—YTHDF1—STING/IFN-I 与交叉启动—删除后交叉启动提高 5 倍、抗肿瘤功能增强；巨噬—YTHDF3—Cd36、Irak1、Tab1/2、Tirap mRNA 降解—TLR4 信号受调；T—未确定—HIV-1 下 PLIN3 mRNA 核内增加、胞质无显著差异—功能结局未给出[379,93,90,414]。

rejected: number_unsupported；ALKBH3 不纳入 canonical m⁶A 免疫核心名单：野生型偏向 m¹A/m³C、不能识别 m⁶A；活性口袋缺失或位点突变虽可使 m⁶A 活性最高≈40%，仍非野生型功能[63,57]。相关证据限于 tRNA 翻译、癌细胞或体外，未见免疫模型，且 eraser 分类相互冲突，故列为边界候选[4,27]。

rejected: number_unsupported；m⁶A是RNA中常见的内部修饰，由Writers写入、Erasers去除、Readers识别，并参与RNA剪接和降解[1,3]。在先天免疫中，m⁶A可影响免疫识别和抗病毒反应；Reader对m⁶A-circRNA的结合/隔离可抑制先天免疫，而未修饰circRNA可激活RIG-I[2,5]。

**补充证据**

**T细胞总体机制与写入复合体**

最强的 T 细胞内在因果证据来自 **METTL3/WTAP 写入轴**。条件性 **METTL3** 缺失小鼠研究显示，m⁶A 促进 **SOCS mRNA** 的诱导性降解，解除 IL‑7/STAT5 信号抑制，推动 T 细胞增殖和分化；同一 SOCS—IL‑2/STAT5 机制还支持 Treg 生成、抑制功能和稳定性。[114] 在小鼠 T 细胞中，**WTAP** 是 m⁶A 写入复合体功能所必需的；m⁶A 使 **Orai1、Ripk1 mRNA** 不稳定，WTAP 缺失时相应蛋白和储存操纵性 Ca²⁺ 内流增加、T 细胞存活下降，并影响胸腺细胞分化、外周 T 细胞激活诱导的死亡及肠道 RORγt⁺ Treg 介导的结肠炎预防。[413] 复合体关系上，**METTL14 与 METTL3** 形成异源二聚体，METTL14 提供 RNA 结合支架；在 CD8⁺ T 细胞中，**YTHDF2 与 IKZF1/3** 的功能性互作则有助于维持关键基因转录。[326][317]

**CD4⁺、CD8⁺及Treg亚群**

**CD4⁺ T 细胞中的 ALKBH5** 证据依赖疾病模型：EAE 摘要称 ALKBH5 缺失增加 **IFNG、CXCL2** 的 m⁶A，抑制 IL‑17 信号，减弱 CD4⁺ T 细胞反应及中枢神经系统中性粒细胞募集；另一神经炎症摘要则称 ALKBH5 去甲基化提高 IFN‑γ、CXCL2 mRNA 稳定性，说明方向需按模型和读出区分。[115][559] **CD8⁺ T 细胞中的 YTHDF2** 通过 m⁶A 依赖机制促进新生 RNA 合成、维持 RNA 稳态并调节线粒体功能和染色质重塑，从而维持多功能性、抗肿瘤活性及对 PD‑1 阻断的反应；其与 IKZF1/3 的互作是已报道的中间环节。[317]

**Treg** 的证据具有组织和状态特异性：WTAP/m⁶A 支持肠道 RORγt⁺ Treg 功能；肿瘤内 Treg 特异性缺失 **YTHDF2** 会增加凋亡并削弱抑制活性，机制涉及 TNF 诱导 YTHDF2 降解 m⁶A 修饰的 NF‑κB 负调节因子；另有综述总结 METTL3 缺失会损害 Treg 稳定性，同时增强效应 T 细胞细胞因子和肿瘤微环境抗肿瘤反应。[413][317][168] **YTHDF1** 方面，USP47—YTHDF1—翻译起始 machinery 轴可降低 m⁶A 依赖的 **c‑MYC** 翻译效率，影响 Treg 代谢和功能稳态，但该片段未给出完整的 Treg 原始实验链。[168]

**iNKT 细胞**中，双阳性胸腺细胞的 **Mettl3** 缺失通过 **Creb1 转录本稳定性**损害增殖、分化和细胞因子分泌；**Mettl14** 缺失增加胸腺细胞凋亡、减少 Vα14‑Jα18 重排及 iNKT 分化，并在成熟 iNKT 中通过 **Cish** 抑制 TCR 信号和细胞因子产生。[328] **Th9 细胞**中，YTHDF2 降解 **Gata3、Smad3** 转录本而抑制分化；Ythdf2 缺失在 IL‑4/TGF‑β 条件下增加 IL‑9、IL‑21，并增强 CD8⁺/NK 细胞浸润和细胞毒性。[317]

**感染、肿瘤背景与证据边界**

HIV‑1 感染 T 细胞中，宿主 writers/erasers 调节病毒 RNA：RRE 的 m⁶A 增强 Rev 结合和病毒 RNA 核输出；感染后 **YTHDF1‑3** 结合 m⁶A 修饰的病毒 gRNA，降低其逆转录为前病毒 DNA。[326] 但 YTHDF1‑3 对 HIV 复制的方向存在冲突：有研究称其结合 HIV RNA 并促进复制，另有研究称其拮抗复制，差异可能来自细胞类型、试剂和实验方法。[115] 肿瘤细胞内在 **ALKBH5** 去除 **PDL1 mRNA 3′UTR** 的 m⁶A，并以 YTHDF2 依赖方式降低其降解，最终抑制 T 细胞细胞毒性；这是肿瘤细胞—T 细胞的间接机制，而非 T 细胞内在调控。[559]

2025 年文献条目仅支持 **FTO** 通过 Fas 关联 CD8⁺ T 细胞存活/效应，并参与 Th1 分化和抗感染免疫，尚未给出完整 RNA 命运和方向；2024 年条目仅提示 **METTL14** 与 CD8⁺ T 细胞活化及抗 PD‑1 反应相关。[557][560] 胃癌外泌体 **THBS1** 可调节 Vγ9Vδ2 T 细胞中的 METTL3/IGF2BP2 介导的 m⁶A，激活 RIG‑I 样受体并增强细胞毒性，但目标 RNA 未明确。[168] 相反，CD4⁺/Treg 中 **miR‑210—Foxp3 3′UTR** 轴虽有双荧光素酶和功能证据，却不涉及 m⁶A 蛋白，不能列为 m⁶A 机制；CBLL1、YTHDF1 在重症肌无力数据中与 Th1/NKT 浸润的关系也仅属关联证据。[565][121]

因此，T 细胞总结行应优先列 **METTL3、WTAP、ALKBH5、YTHDF2**，并将 METTL14、FTO、YTHDF1 或 IGF2BP2 标为亚群或情境依赖证据；目标与机制包括 **SOCS、Orai1/Ripk1、IFNG/CXCL2、Gata3/Smad3 和 Creb1**，功能则分别写明增殖分化、Treg 稳定/抑制、CD8⁺ 多功能与抗肿瘤，以及 Th9/iNKT 分化，保留“模型依赖”或“证据不完整”限定。

T细胞的直接证据集中于 METTL3、METTL14、ALKBH5 和 YTHDF1/2；作用依赖亚群、刺激及疾病背景，不能概括为统一方向。[172,354]

**CD4⁺/Th1/Th17/Tfh：**METTL3缺失使SOCS1/3、CISH升高，削弱IL‑7–JAK/STAT5，破坏稳态和分化；其m⁶A调节Tcf7稳定性并支持Tfh成熟，亦影响RORγt/STAT3，缺失削弱Th17及抗肿瘤反应。[172,354] ALKBH5降低IFN‑γ、CXCL2 mRNA的m⁶A，增强稳定性和翻译，促进Th1；缺失可减轻EAE。[172,354] METTL3/METTL14介导Icos mRNA甲基化并抑制Icos，影响Tfh。[237]

**CD8⁺/CAR‑T：**文献报告METTL3依赖的m⁶A有助于效应分化和记忆形成；CAR‑T中METTL3维持IL‑2、IFN‑γ mRNA稳定，YTHDF2调节细胞因子受体翻译，支持扩增、持续性和抗肿瘤活性。[354,71] 常规CD8⁺T细胞的直接目标RNA尚未明确。

**Treg：**METTL3通过m⁶A降低Socs mRNA稳定性、激活IL‑2/STAT5，维持抑制功能；缺失削弱Treg稳定性，却增强效应T细胞因子和抗肿瘤反应。METTL14缺失阻碍诱导性Treg，另有研究将其与FOXP3–mTOR轴相连。[172,354,71] YTHDF3–FOXO3抑制ISG的证据来自SLE背景，T细胞归属不足。[52] YTHDF1–eIF3促进翻译、YTHDF2–CCR4‑NOT/HRSP12促降解是通用机制；METTL3–SOCS/JAK‑STAT5的具体关系存在相反报告。[354,355]

小鼠CD4⁺T细胞中，ALKBH5（Eraser）在EAE（2021）去除Ifng/Cxcl2 mRNA的m⁶A，维持其稳定性和蛋白表达；缺失使m⁶A↑、降解↑，CD4⁺反应、CNS浸润/中性粒细胞募集及结肠炎、EAE减弱。[342]稳态发育、活化、增殖不变；Treg缺失不影响EAE，FTO缺失亦无表型，CD8⁺内在作用未定。[342]肿瘤细胞Mettl3/14或ALKBH5操纵虽增加CD8⁺浸润、IFN-γ和抗PD-1效应，却非T细胞内在证据。[368,547,548]METTL14依背景而异：稳定Ebi3→CD8⁺功能障碍，降解PDCD1→活化；Treg中YTHDF2缺失增强应答T细胞/IFN-γ；CD4⁺m⁶A可直接调节CD40L，介导者未知。[369,72,177]

鼠CD8⁺T：FTO缺失↑Fas mRNA-m⁶A/稳定性，经IGF2BP3→Fas↑、凋亡；感染存活和效应受损，分化/因子小[562]。YTHDF2以m⁶A依赖RNA降解维持效应、线粒体适能及PD-1疗效[251]。鼠/人CD4⁺Th9：YTHDF2缺失稳定Gata3/Smad3→Th9、IL-9/IL-21、抗肿瘤↑；Th1/2/17、Treg不变[517]。肿瘤Treg：YTHDF2缺失稳定Nlrc3/Nfkbie/Traf3，NF-κB受抑，抑制功能下降、抗肿瘤↑[347]。T：METTL3→Socs1/3；YTHDF1–3→SOCS/Cish→IL-7/STAT5、稳态/分化/增殖[374,551]。

这些页面报告了 HIV‑1 感染 T 细胞的人/病毒 m⁶A 转录组及 METTL3/14 与抗PD‑1反应的关联；未提供 T 细胞特异的蛋白—RNA—功能因果链[47][416]。

METTL3→SOCS[369]；ALKBH5→IFNG/CXCL2[367]；VIRMA→Tfh[76]；eIF3非m⁶A[512]

T细胞METTL3促SOCS降解，维持初始CD4+增殖分化[78]

METTL14→Treg↓[270]FTO↓→Fas凋亡[478]

截至2026年，急性病毒感染的CD8⁺T细胞中，METTL3稳定Tbx21 mRNA，促进效应分化和记忆；FTO缺失经IGF2BP3稳定Fas mRNA，增加活化CD8⁺T细胞凋亡；活化CD4⁺T细胞中，YTHDF2促Tnf mRNA降解、限制TNF，METTL14稳定Foxp3、支持iTreg。[382] 肿瘤浸润CD8⁺T细胞中，YTHDF2维持线粒体适能和细胞毒性，缺失加速耗竭；WTAP经YTHDF1增加PD-1翻译、抑制效应。[382] CD8⁺T细胞激活时，m⁶A/ARE共同促mRNA快速降解，但YTHDF成员未区分、无完整功能终点。[297] FTO–LIF及IGF2BP3–HMGB1分别是肿瘤细胞内机制和浸润相关性，不是T细胞内直接证据。[296][496]

METTL3：IL‑7/STAT5/SOCS→T稳态；TCF7/Tbx21/Socs/SOCS3/ASH1L→CD4/CD8/Treg/Th17分化、记忆及抑制（Th17：EAE/EAU相反）。[94]YTHDF2缺失→Treg抑制↓、抗肿瘤↑；ALKBH5缺失→CD4 IFNγ/CXCL2稳定性↓。[147][95]HIV中YTHDF1‑3结合病毒RNA；METTL14/WTAP/IGF2BP3/RBMX为外源间接证据。[386][469][384][563][89]

METTL3–SOCS1/3/CISH的m⁶A促降解，解除IL‑7/STAT5，维持初始T增殖分化；Treg中缺失致自身免疫[151][395]。ALKBH5缺失使CD4⁺IFN‑γ/CXCL2 mRNA失稳并扩增γδ前体[305]；METTL14缺失致小鼠T细胞结肠炎[558]

小鼠γδ T前体中，ALKBH5缺失增m⁶A、促Jagged1/Notch2降解，扩增γδ T细胞；成熟γδ T细胞功能未变[72]。

METTL3介导m⁶A促进SOCS mRNA降解，支持IL‑7/STAT5信号、T细胞增殖分化及Treg抑制功能。[247]

T细胞：METTL3→SOCS；WTAP→PDCD1翻译；FTO→Fas；ALKBH5→Cxcl2；YTHDF2→CD8效应[156]。

METTL3促Socs/Cish降解，助初始T细胞分化；METTL14缺失损害iNKT。[566][527]

T细胞：WTAP—TCR、METTL3—CD8效应记忆、IL7/STAT5/SOCS仅为线索[561][391]；YTHDF2缺失增强Th9抗肿瘤[556]；YTHDF3—Treg为MR部分中介[529]。

小鼠CD4⁺T中，ALKBH5去甲基化CXCL2、IFN‑γ mRNA，增稳定性/IL‑17；缺失扩增γδ前体、抗感染保护增强。[327]m⁶A‑circRNA经YTHDF2抑制RIG‑I，抑制T细胞抗肿瘤。[49]TAM中METTL14缺失→Ebi3 m⁶A↓/EBI3↑→CD8⁺T失能；EBI3抗体救援（间接）。[530]YTHDC2/IGF2BP3浸润关联；Treg链未证实。[490][501][564]

是。小鼠初始 CD4⁺ T 细胞中，METTL3/METTL14 复合物使 Socs1、Socs3、Cish mRNA 进入 m⁶A 介导的快速降解，解除 IL-7/JAK-STAT5 抑制并推动分化、增殖；这是遗传扰动支持的直接链。[75] HIV-1 感染的活化原代 CD4⁺ T 细胞中，METTL3–METTL14 共沉淀增加 ~ 3-fold，PLIN3 mRNA 水平和核内积累增加而翻译、蛋白下降，相关表型在 Jurkat 未复现，故不能普遍外推。[106]

是，但主要限于存活。小鼠活化 CD8⁺ T 细胞中，FTO 缺失使 Fas mRNA 的 m⁶A 增加，经 IGF2BP3 稳定 Fas mRNA 并升高 Fas，导致凋亡增加和抗感染效应受损；Fas 位点突变或 IGF2BP3 敲低可救援。[478] 该研究未显著改变效应/记忆分化和细胞因子；TAM 中 METTL14–Ebi3 对 CD8⁺ T 细胞的影响是间接链，不是 CD8⁺ 细胞内机制。[478][530]

对 T 细胞及证据支持的亚群，可按“蛋白—直接 RNA—修饰/reader—RNA 命运—功能”拆解：METTL3/METTL14–Socs–IL-7/STAT5–分化/增殖、ALKBH5–CXCL2/IFN-γ 稳定性–CD4⁺ 反应、METTL3–Tbx21–T-bet–CD8⁺ 效应和 YTHDF2–RNA 稳态/线粒体–CD8⁺ 多功能性，并记录小鼠、EAE、急性感染或肿瘤条件。[114][326][342][317][382] NK、DC 没有同等机制事实，巨噬细胞仅有 METTL14/m⁶A 与 CD8⁺ 浸润和效应的相关性，不能补成完整的全细胞因果链。[409]

在 T 细胞中，METTL3/m⁶A→SOCS 降解→IL-7/STAT5、ALKBH5→CXCL2/IFN-γ 稳定性→CD4⁺ 反应、METTL3→Tbx21→T-bet/效应程序及 YTHDF2→RNA 稳态→CD8⁺ 多功能性构成可追踪链；条件性缺失支持因果，YTHDF2–IKZF1/3 是蛋白相互作用/功能关联，巨噬细胞 METTL14–CD8⁺ 是间接关联。[114][342][317][382][409] CD4⁺ 有直接链；CD8⁺ 在该组材料中仅有 m⁶A/ARE–YTHDF 结合及激活后快速降解的部分链，具体 reader 成员和完整功能终点未明，说明方向随亚群和靶标而变。[297]

亚群核验为：CD4⁺ 是 METTL3/METTL14–Socs–IL-7/STAT5–分化/增殖，Treg 是 METTL3–Socs–IL-2/STAT5–抑制功能；CD8⁺ 的补充证据仅能确认 m⁶A/ARE–YTHDF 参与激活后快速降解，具体 reader 成员和完整功能终点仍有限。[75][526][297]

本节材料对应免疫细胞机制部分并聚焦 T 细胞；完整的 Writers/Erasers/Readers 分类及全免疫细胞汇总不由本节证据覆盖。[75][526]

在 T 细胞中，可核实的关系是 METTL3–METTL14 writer 复合物共组分（METTL3 催化、METTL14 结合 RNA 并稳定复合物），以及 YTHDF2–IKZF1/3 蛋白相互作用；这不足以覆盖全部主要 m⁶A 蛋白的相互作用名录。[326][317]

现有证据可列出 T cells—METTL3—Socs1/Socs3/Cish 的 m⁶A 促进降解→IL-7/STAT5—增殖/分化，以及小鼠初始 CD4⁺ T cells—METTL3/METTL14—同一目标机制—稳态扩增/分化。[78][75] 表格列名固定为“免疫细胞类型”“关键 m⁶A 调控蛋白”“调控目标与机制”“对细胞功能的最终影响”，但 NK、DC 和巨噬细胞行仍缺直接证据。

**补充证据**

原始研究支撑机制，综述作名册/线索。[317]Validated/Binding/Perturbation分别为直接、结合、扰动后测序。[547]表达变化不能单独证明m⁶A因果，需核验位点、reader结合、RNA命运及救援。[580]YTHDF2在辐射与敲除模型MDSC方向相反，按模型并列。[560]METTL3/14=2014、YTHDF3=2017、ALKBH5-CD4⁺T=2021。[559]禁用清单不作证据。

B.napus的STRING边非直接。[334]

2021/2024原始研究[345][111]

2019年YTHDF2—HRSP12直接结合并桥接RNase P/MRP；YTHDC1—SRSF3促mRNA核输出。[349][581]

FMRP结合m⁶A，免疫证据缺失[359]

2021年NK研究以特异性敲除、MeRIP/RIP-seq和功能实验支持METTL3—Ptpn11链[361]；数据库/综述仅提供关联线索，不能替代因果证据[582][367]。

时间分开记录。[371]

禁用来源排除；证据按原始研究、综述、预印本分级。[286,436,477]冲突按模型解释，相关性不等于因果。[84]年份分开记录。[470]

YTHDF冲突[325]

**证据分级：**机制性结论须有直接目标 RNA、RNA 命运及位点/reader/救援证据；只有调控蛋白扰动与通路或表型相联系者标为“功能性中间”，表达、整体 m⁶A 或数据库相关性标为“关联/新兴”[410]。2021 年小鼠 Mettl14 条件敲除—C1q⁺TAM—EBI3 共培养/中和实验支持因果链，人类肿瘤 scRNA-seq 仅支持相关性[409]；METTL14–RNAPII 在 HeLa 中经 SMN 敲低及 RNase A 处理显示 RNA 依赖互作[80]。结构、EMSA、pull-down 与免疫表型分开计证，综述只作名册或线索，原始研究才支撑机制[157][158]。

**冲突与边界：**巨噬细胞中 METTL3 稳定 STAT1、维持炎症糖酵解，而 YTHDF2 介导 STAT1 降解、限制同一程序；IGF2BP2 稳定 TSC1/PPARγ 在 IBD 中偏抗炎、在过敏性肺炎中可偏促炎[410][579]。NK 细胞中 METTL3 被报道促进抗肿瘤免疫、YTHDF2 控制抗肿瘤和抗病毒免疫，而 FTO（2023）文献则报告其负向调节细胞毒性[172]。DC 结果随 NK/DC 比例相反：高比例杀死未成熟 DC，低比例促其成熟，且属于非 m⁶A 背景[83]。T 细胞须分亚群：Treg（2018）、CD8⁺耗竭（2025）和 Th9（2025）不是同一功能终点[249][79][556]。

截至 2026-10-17，发表年与实验时点分开记录：T 细胞稳态 2017 年、DC-YTHDF1 与巨噬细胞 METTL3-STAT1 2019 年、NK-METTL3/YTHDF2 2021 年、WTAP-T 细胞 2022 年、FTO-Th1 与 WTAP-CD8⁺T 细胞 2025 年；WTAP 结构研究发表于 2026-06-02，GSE213727/PXD036899 标为 2023 年但未给出实验时点[249][410][158][104]。每条结论另记物种、亚群、刺激、扰动和直接 m⁶A 读出；禁用文章、五个 URL 及其镜像或重复元数据均排除，未作证据或引用。

证据标签应分开：直接结合/直接目标只有同时具备RNA命运、位点/reader及救援证据才标“Mechanistically resolved”；复合物共组分单列“组成证据”，不等同直接结合；遗传干预标“Functional/intermediate”；相关性和推断机制标“Associative/emerging”[410]。NK中METTL3促抗肿瘤、FTO抑细胞毒性，应按蛋白、物种、刺激、时间和肿瘤微环境分层；DC的相反结果取决于NK/DC比、接触或可溶因子、亚群、地点及成熟度；YTHDF1仅是有数据库差异且缺直接因果的相关性，化疗下巨噬细胞和T细胞结果也分别受M2状态及亚群、刺激影响[71,217,560,677,661,671,673]。

## 参考文献

[1] <https://doi.org/10.3389/fimmu.2026.1918662> m⁶A与免疫细胞RNA命运; 巨噬细胞状态与m⁶A机制综述; RBM4–YTHDF2–STAT1比较; WTAP与T细胞受体功能
[2] <https://www.nature.com/articles/s41467-021-25803-0> NK研究; NK细胞METTL3原始研究; Ptpn11/SHP-2机制证据; IL-15下游支路分析; IL-15反应及SHP-2抑制实验; NK成熟与挑战状态比较; 肿瘤环境与METTL3调节; NK METTL3
[3] <https://www.nature.com/articles/s41467-019-09903-6> DC研究; DC激活原始研究; CD40/CD80/TIRAP翻译机制; 核糖体分析及位点报告实验; YTHDF1读取与催化救援; DC介导的OT-II应答; DC激活
[4] <https://www.nature.com/articles/s41467-021-21514-8> 巨噬细胞研究; METTL3–YTHDF1–SPRED2机制; SPRED2轴的肿瘤终点; SPRED2研究; SPRED2
[5] <https://www.nature.com/articles/s41467-021-21594-6> T细胞研究; METTL3与Tfh原始研究; Tcf7位点、衰减及TCF-1救援; Tcf7稳定化的机制语境; Tcf7机制
[6] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10408978/> m⁶A调控体系概述; Reader家族及识别机制; IGF2BP效应伙伴; HNRNPA2B1与DGCR8; 结构转换与RNA加工; IGF2BP2–TSC1/PPARγ机制; METTL14–Ebi3相关机制; T细胞m⁶A功能综述; IL-7/STAT5/SOCS机制; T细胞遗传及过继证据; METTL3维持T…
[7] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8924732/> 核心调控蛋白综述; VIRMA的区域选择作用; NK稳态与成熟相关综述
[8] <https://www.nature.com/articles/s41422-022-00725-8> 人源Writer复合体结构; Writer结构与组装; METTL3与WTAP的组装界面; WTAP支架结构; VIRMA互作及RNA结合; ZC3H13的结构作用
[9] <https://doi.org/10.1146/annurev-biochem-052521-035330> Writer功能综述; METTL3催化分工; METTL14结构与功能; WTAP定位功能; RBM15/15B底物招募; RBM15/15B与XIST甲基化; HAKAI与复合体稳定性
[10] <https://doi.org/10.1038/s41419-025-08008-x> ADAP–METTL3直接互作; Spry1位点及IGF2BP2机制; ADAP缺失模型的功能救援; Spry1
[11] <https://doi.org/10.1038/s41421-023-00604-5> WTAP–VIRMA与METTL14互作
[12] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2025.1706557/full> METTL16独立底物谱; YTHDF冗余与情境特异性; YTHDF2的NK机制归纳; 放疗后DC的YTHDF1机制; YTHDF1与放疗免疫应答; 放疗
[13] <https://doi.org/10.1186/s13578-024-01286-6> FTO与ALKBH5结构功能综述; FTO底物与定位; FTO–XPO2及FOXO3a互作; ALKBH5去甲基化特征; FTO与两类极化机制; 糖尿病与FTO方向比较
[14] <https://link.springer.com/article/10.1186/s12967-025-06221-y> FTO反应路径; RBM33及PSPC1相关调节; HRSP12相关途径; TAM中YTHDF2机制归纳; TAM YTHDF2
[15] <https://link.springer.com/article/10.1186/s10020-023-00643-4> FTO相关RNA加工机制
[16] <https://link.springer.com/article/10.1186/s13045-020-00872-8> 感染状态下的蛋白关联; HNRNPA2B1抗病毒相关作用; CCR7刺激时序与RNA周转
[17] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8186046/> DDX46招募机制; 巨噬细胞核输出机制; YTHDF1效应机制; YTHDC1剪接功能; lnc-Dpf3–HIF-1α机制; lnc-Dpf3位点与降解; YTHDF2与LPS炎症; DDX46–ALKBH5核保留机制; 迁移; ALKBH5核输出
[18] <https://www.science.org/doi/10.1126/sciadv.abg0470> CD4⁺ T细胞稳定性机制; ALKBH5与OGDH相关抗病毒证据; ALKBH5控制CD4⁺致病性; Ifng/Cxcl2选择性及衰减实验; 结肠炎与EAE功能实验; ALKBH5与FTO遗传比较; CD4⁺ ALKBH5
[19] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2023.1162607/full> YTHDF功能与互作; YTHDF互作综述
[20] <https://doi.org/10.1038/ncomms12626> YTHDF2–CNOT1直接招募
[21] <https://doi.org/10.1038/cr.2017.15> YTHDF3功能机制
[22] <https://doi.org/10.7554/eLife.31311> YTHDC1核输出机制
[23] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11088905/> YTHDC1与NEXT相关机制; 核内m⁶A与RNA稳定性; 不同Reader的稳定性输出
[24] <https://www.cell.com/molecular-cell/fulltext/S1097-2765(17)30699-8> YTHDC2生化性质; MEIOC复合体证据; YTHDC2结合实验
[25] <https://doi.org/10.1261/rna.064238.117> YTHDC2–XRN1互作
[26] <https://link.springer.com/article/10.1186/s12967-024-05293-6> 解旋与读取功能的区分; YTHDC2–TLR2感染机制; YTHDC2–ASH1L机制; YTHDC2感染机制; YTHDC2–ASH1L
[27] <https://www.nature.com/articles/s41467-019-13317-9> YTHDC2促进结构化RNA翻译
[28] <https://doi.org/10.1038/s41556-018-0045-z> IGF2BP识别与稳定机制
[29] <https://www.nature.com/articles/s41419-025-07606-z> IGF2BP3–Fas机制; FTO–Fas原始研究; Fas位点及IGF2BP3救援; CD8⁺ T细胞急性感染功能; FTO–Fas
[30] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10074099/> NK细胞FTO原始研究; FTO–SOCS–JAK/STAT机制; 人源NK及NK92功能实验; 转移、耗竭及过继实验; NK92过表达与敲低比较; NK FTO
[31] <https://www.nature.com/articles/s41586-019-0916-x> DC交叉呈递原始研究; YTHDF1–cathepsin机制; DC介导的CD8⁺应答; DC交叉呈递; DC间接作用
[32] <https://journals.physiology.org/doi/full/10.1152/ajpcell.00212.2019> METTL3–STAT1原始研究; STAT1半衰期实验; STAT1研究; STAT1
[33] <https://www.ovid.com/journals/sciad/fulltext/10.1126/sciadv.abd4742~pooled-crispr-screening-identifies-m6a-as-a-positive> METTL3–IRAKM机制; IRAKM衰减与救援实验; 感染与MC38功能实验; IRAKM
[34] <https://www.cell.com/molecular-cell/fulltext/S1097-2765(22)00207-6> 乳酸相关METTL3–JAK1机制; Jak1髓系机制
[35] <https://doi.org/10.1038/s41423-024-01156-8> 结肠炎研究; METTL3–YTHDF3–PGP与结肠炎; PGP与肠炎
[36] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11569104/> HIF-1α–METTL3–PFKM机制; PFKM研究的不同证据层; PFKM
[37] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2025.1693336/full> Cpt1a与HDGF模型比较; 肿瘤细胞驱动的TAM变化; 代谢与TAM综述
[38] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11116364/> 巨噬细胞研究间差异
[39] <https://doi.org/10.1186/s10020-023-00643-4> METTL3与Foxp3 RNA稳定性; SLE观察与METTL3药理模型
[40] <https://doi.org/10.7150/thno.124482> METTL14–Foxp3/mTOR机制; METTL3–Tbx21/T-bet机制
[41] <https://pdf.hanspub.org/bp20230400000_43402617.pdf> ALKBH5与γδ T发育; γδ T发育
[42] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10390869/> Treg中YTHDF2原始研究; YTHDF2–NF-κB反馈机制; 肿瘤内与外周Treg比较; Treg YTHDF2
[43] <https://doi.org/10.64898/2026.01.06.697843> METTL3–DNMT3B预印本; DNMT3B预印本
[44] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11578931/> 肿瘤细胞MHC-I相关机制; 肿瘤MHC-I机制
[45] <https://www.maxapress.com/data/article/epi/preview/pdf/epi-0025-0007.pdf>
[46] <https://scholars.whu.edu.cn/en/publications/m6a%E4%BF%AE%E9%A5%B0%E5%8F%82%E4%B8%8E%E8%B0%83%E6%8E%A7%E5%A4%A9%E7%84%B6%E5%85%8D%E7%96%AB%E7%9A%84%E7%A0%94%E7%A9%B6%E8%BF%9B%E5%B1%95/>
[47] <https://www.sciencedirect.com/science/article/pii/S0753332223006297>
[48] <https://www.nature.com/articles/srep42271>
[49] <https://pubmed.ncbi.nlm.nih.gov/31474572/>
[50] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10435004/>
[51] <https://doi.org/10.1016/j.bbcan.2021.188609>
[52] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2024.1387582/full>
[53] <https://doi.org/10.1002/anie.202313900>
[54] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11846542/>
[55] <https://rnajc.ucsf.edu/sites/rnajc.ucsf.edu/files/N6-methyladenosine-dependent%20regulation%20of%20messenger%20RNA%20stability.pdf>
[56] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12467241/>
[57] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12439664/>
[58] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11601937/>
[59] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10599278/>
[60] <https://www.nature.com/articles/s41467-021-23892-5>
[61] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10805700/>
[62] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9720116/>
[63] <https://doi.org/10.1016/j.celrep.2023.113192>
[64] <https://doi.org/10.7554/elife.85659>
[65] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7170965/>
[66] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7306444/>
[67] <https://xueqiu.com/8399481175/379788289>
[68] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6151148/>
[69] <https://doi.org/10.1093/nar/gkaf813>
[70] <https://pubmed.ncbi.nlm.nih.gov/36694229/>
[71] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8758144/>
[72] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9388086/>
[73] <https://www.cd-genomics.com/resource-what-is-rna-m6a.html>
[74] <https://doi.org/10.1016/j.jbc.2022.101649>
[75] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5729908/>
[76] <https://affinage.wi.mit.edu/gene/VIRMA>
[77] <https://doi.org/10.1038/s41419-025-08008-x>
[78] <https://www.nature.com/articles/nature23450?code=82f92302-2cb9-45eb-bd8b-58e5fa202a08&error=cookies_not_supported>
[79] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12582961/>
[80] <https://link.springer.com/article/10.1038/s44319-025-00590-7>
[81] <https://doi.org/10.54254/2753-8818/2025.20109>
[82] <https://www.youtube.com/watch?v=kcm89shE6cA&vl=en>
[83] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11114903/>
[84] <https://www.nature.com/articles/s41598-025-16948-9.pdf>
[85] <https://lifescience.sinh.ac.cn/webadmin/upload/20179845.pdf>
[86] <https://journals.plos.org/plosbiology/article?id=10.1371%2Fjournal.pbio.3001683>
[87] <https://doi.org/10.1101/2025.05.09.653100>
[88] <https://doi.org/10.12677/acm.2025.153891>
[89] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12427910/>
[90] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9218665/>
[91] <https://pubmed.ncbi.nlm.nih.gov/34535671/>
[92] <http://zhulab.ustc.edu.cn/_upload/article/files/37/7f/2968ec6743418d93e9e5e1dab3ce/881b6c7f-19ae-4d99-a983-661f9533c866.pdf>
[93] <https://ykxb.scu.edu.cn/supplement/354b97c1-d45e-44e1-bed2-7361b515a7c9>
[94] <https://doi.org/10.52338/immunology.2024.4007>
[95] <https://www.springermedizin.de/targeting-the-rna-m6a-modification-for-cancer-immunotherapy/20225484>
[96] <https://doi.org/10.1161/atvbaha.122.318451>
[97] <https://pmc.ncbi.nlm.nih.gov/articles/PMC3646334/>
[98] <https://doi.org/10.1016/j.xcrp.2025.102779>
[99] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10611730/>
[100] <https://www.muhn.edu.cn/ecmd/info/1481/18195.htm>
[101] <https://www.ubigene.com/literature/raw2647-help-study>
[102] <https://patents.google.com/patent/CN114058585A/zh>
[103] <https://doi.org/10.1093/nar/gkx141>
[104] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10435237/>
[105] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6778029/>
[106] <https://journals.asm.org/doi/10.1128/jvi.01536-25>
[107] <https://doi.org/10.1101/2024.04.12.589122>
[108] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10583014/>
[109] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10902381/>
[110] <https://www.mdpi.com/2218-273X/15/2/157>
[111] <https://doi.org/10.1172/jci181612>
[112] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9035487/>
[113] <https://www.mdpi.com/2072-6694/17/17/2928>
[114] <https://www.frontiersin.org/journals/cellular-and-infection-microbiology/articles/10.3389/fcimb.2023.1151069/full>
[115] <https://www.mdpi.com/2218-273X/14/8/1042>
[116] <https://www.life-science-alliance.org/content/7/1/e202302240>
[117] <https://www.nature.com/articles/s41422-018-0040-8>
[118] <https://www.nature.com/articles/s41392-020-00450-x>
[119] <https://encyclopedia.pub/entry/23782>
[120] <https://doi.org/10.1007/s00018-023-04799-4>
[121] <https://www.researchsquare.com/article/rs-5264805/latest.pdf>
[122] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11877144/>
[123] <https://www.frontiersin.org/journals/oncology/articles/10.3389/fonc.2024.1375942/full>
[124] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10307841/>
[125] <https://www.mdpi.com/2218-273X/14/10/1319>
[126] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5900714/>
[127] <https://www.nature.com/articles/s41419-022-05268-9>
[128] <https://www.springermedizin.de/dynamic-regulation-and-functions-of-mrna-m6a-modification/20079384>
[129] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8213727/>
[130] <https://link.springer.com/article/10.1186/s11658-025-00693-y>
[131] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2022.1030728/full>
[132] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9546849/>
[133] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2026.1887190/full>
[134] <https://link.springer.com/article/10.1186/s13045-022-01231-5>
[135] <https://www.nature.com/articles/s41598-025-88671-4>
[136] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2025.1612041/full>
[137] <https://genesdev.cshlp.org/content/32/5-6/415.full.html>
[138] <https://pmc.ncbi.nlm.nih.gov/articles/PMC13255311/>
[139] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11799344/>
[140] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12453181/>
[141] <https://doi.org/10.3390/biom12091224>
[142] <https://www.nature.com/articles/s41420-023-01485-z/tables/1>
[143] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10443600/>
[144] <https://www.nature.com/articles/s41422-022-00725-8>
[145] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5993786/>
[146] <https://doi.org/10.3724/abbs.2024152>
[147] <https://jitc.bmj.com/content/13/9/e012744>
[148] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11749156/>
[149] <https://www.uniprot.org/uniprotkb/Q75N03/entry>
[150] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7146974/>
[151] <https://knowledge.uchicago.edu/records/g3rk7-n8p56/files/N6-methyladenosine-in-Mammalian-Messenger-RNA.pdf>
[152] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9790079/>
[153] <https://doi.org/10.20944/preprints202512.0405.v1>
[154] <https://link.springer.com/article/10.1186/s40364-023-00452-1>
[155] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10266107/>
[156] <https://www.mdpi.com/2673-5601/6/3/50>
[157] <https://doi.org/10.1038/s41422-022-00725-8>
[158] <https://doi.org/10.1038/s44319-026-00815-3>
[159] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10043241/>
[160] <https://www.sciencedirect.com/science/article/abs/pii/S0022283615004866>
[161] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7388453/>
[162] <https://doi.org/10.1016/j.molimm.2025.05.004>
[163] <https://onlinelibrary.wiley.com/doi/10.1002/cbdv.202000050>
[164] <https://www.frontiersin.org/journals/cell-and-developmental-biology/articles/10.3389/fcell.2020.587108/full>
[165] <https://www.biorxiv.org/content/10.1101/2024.06.24.600547v1.full-text>
[166] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11439334/>
[167] <https://www.abcam.com/en-us/technical-resources/pathways/m6a-functions-and-distribution>
[168] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11846233/>
[169] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2025.1693336/full>
[170] <https://link.springer.com/article/10.1186/s13578-025-01368-z>
[171] <https://www.nature.com/articles/s12276-023-00944-y>
[172] <https://link.springer.com/article/10.1007/s44368-025-00015-6>
[173] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12410683/>
[174] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9380308/>
[175] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2026.1749911/full>
[176] <https://doi.org/10.1073/pnas.0801313105>
[177] <https://doi.org/10.1074/jbc.m114.602870>
[178] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2023.1162607/full>
[179] <https://spliceosomedb.ucsc.edu/proteins/12002>
[180] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11353047/>
[181] <https://www.ijbs.com/v18p2744.htm>
[182] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7191095/>
[183] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12406103/>
[184] <https://pubmed.ncbi.nlm.nih.gov/24316715/>
[185] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7937903/>
[186] <https://xb.xzhmu.edu.cn/cn/article/pdf/preview/10.12467/j.issn.2096-3882.20240315.pdf>
[187] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6338863/>
[188] <https://doi.org/10.3390/molecules29010140>
[189] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11993731/>
[190] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6444029/>
[191] <https://pubmed.ncbi.nlm.nih.gov/37474008/>
[192] <https://pubmed.ncbi.nlm.nih.gov/26321680/>
[193] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8541906/>
[194] <https://doi.org/10.1016/j.isci.2021.103345>
[195] <https://pmc.ncbi.nlm.nih.gov/articles/PMC3829144/>
[196] <https://pmc.ncbi.nlm.nih.gov/articles/PMC1880881/>
[197] <https://pmc.ncbi.nlm.nih.gov/articles/PMC1440840/>
[198] <https://doi.org/10.1016/j.celrep.2019.06.072>
[199] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8800407/>
[200] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12967780/>
[201] <http://www.gzscbio.com/m/sci/detail/209.html>
[202] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6109920/>
[203] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6687293/>
[204] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6693534/>
[205] <https://news.bioon.com/article/a0a69506085f.html>
[206] <https://www.epibiotek.com/news_out/detail/318>
[207] <http://www.geneskies.com/index.php/Index/ndetail/id/587.html>
[208] <https://pmc.ncbi.nlm.nih.gov/articles/PMC13044287/>
[209] <https://www.epigentek.com/catalog/exploring-m6a-rna-methylation-writers-erasers-readers-n-85.html?srsltid=AU7gw4XmoDcSWeaW-fcqujdozIeXgbk111PPJkGiZv6b5iFpyiuwftBS>
[210] <https://repository.nottingham.ac.uk/entities/publication/ec115c53-1562-40e1-a494-32460ab9cc5c>
[211] <https://www.frontiersin.org/journals/cell-and-developmental-biology/articles/10.3389/fcell.2020.00741/full>
[212] <https://genesdev.cshlp.org/content/36/17-18/1002.full>
[213] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10636609/>
[214] <https://www.jbc.org/article/S0021-9258(19)55676-9/pdf>
[215] <https://pmc.ncbi.nlm.nih.gov/articles/PMC84877/>
[216] <https://hal.science/hal-03770814/document>
[217] <https://pmc.ncbi.nlm.nih.gov/articles/PMC3363364/>
[218] <https://www.nature.com/articles/s41467-021-27087-w>
[219] <https://doi.org/10.1101/2024.02.02.577121>
[220] <https://med.xmu.edu.cn/info/1639/22951.htm>
[221] <https://www.nature.com/articles/s41598-019-45636-8>
[222] <https://link.springer.com/article/10.1186/s12935-022-02452-x>
[223] <https://www.science.org/doi/10.1126/science.1118977>
[224] <https://pmc.ncbi.nlm.nih.gov/articles/PMC1933396/>
[225] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7225109/>
[226] <https://www.syyxzz.com/CN/10.3969/j.issn.1006-5725.2025.04.023>
[227] <https://doi.org/10.1002/iub.2276>
[228] <https://doi.org/10.21203/rs.3.rs-79739/v1>
[229] <https://www.ncbi.nlm.nih.gov/gene/57721>
[230] <https://www.cell.com/molecular-cell/fulltext/S1097-2765(21)00593-1>
[231] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2025.1706557/pdf>
[232] <https://www.activemotif.com/catalog/details/81100/recombinant-ythdc1-325-502-protein?srsltid=AU7gw4VpV807WP2xOYRaGGgXRR9sDa69l5eI5N2iWnsW_rJF9AHkypZ6>
[233] <https://www.frontiersin.org/journals/oncology/articles/10.3389/fonc.2025.1611007/full>
[234] <https://doi.org/10.2210/pdb9krp/pdb>
[235] <https://doi.org/10.2210/pdb9kn6/pdb>
[236] <https://link.springer.com/article/10.1186/s12943-022-01558-0>
[237] <https://link.springer.com/article/10.1186/s12967-021-02918-y>
[238] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6602412/>
[239] <https://link.springer.com/article/10.1007/s00018-026-06201-5>
[240] <https://link.springer.com/article/10.1186/s13578-024-01286-6>
[241] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12528062/>
[242] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7729110/>
[243] <https://doi.org/10.1016/j.omtn.2024.102315>
[244] <https://www.nature.com/articles/s41417-024-00734-2/tables/1>
[245] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11088905/>
[246] <https://link.springer.com/article/10.1007/s12672-025-02644-7>
[247] <https://www.frontiersin.org/journals/cell-and-developmental-biology/articles/10.3389/fcell.2021.755691/full>
[248] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7457244/>
[249] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8186046/>
[250] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2025.1521196/full>
[251] <https://doi.org/10.1038/s41467-024-53997-6>
[252] <https://www.nature.com/articles/s41419-025-08008-x>
[253] <https://link.springer.com/article/10.1186/s13046-021-01857-2>
[254] <https://www.frontiersin.org/journals/molecular-biosciences/articles/10.3389/fmolb.2021.632219/full>
[255] <https://doi.org/10.3390/ijms20061323>
[256] <https://doi.org/10.1016/j.jbc.2024.107783>
[257] <https://pmc.ncbi.nlm.nih.gov/articles/PMC4393108/>
[258] <https://research.manchester.ac.uk/en/publications/hakai-is-required-for-stabilization-of-core-components-of-the-m6a/>
[259] <https://affinage.wi.mit.edu/gene/HNRNPC>
[260] <https://doi.org/10.3389/fimmu.2025.1593243>
[261] <https://doi.org/10.1038/cr.2014.151>
[262] <https://doi.org/10.1101/327924>
[263] <https://affinage.wi.mit.edu/gene/METTL14>
[264] <https://doi.org/10.1126/sciadv.ads4750>
[265] <https://preview-www.nature.com/articles/s41422-022-00741-8>
[266] <https://www.cell.com/molecular-cell/fulltext/S1097-2765(18)30638-5>
[267] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7333474/>
[268] <https://doi.org/10.1038/s41586-019-0916-x>
[269] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12351120/>
[270] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7498954/>
[271] <https://doi.org/10.1016/j.bbadis.2024.167304>
[272] <https://doi.org/10.1038/s41421-023-00604-5>
[273] <https://www.nature.com/articles/s41419-017-0129-x/tables/1>
[274] <https://www.nature.com/articles/s41590-023-01548-4>
[275] <https://www.nature.com/articles/s41556-024-01368-0>
[276] <https://www.nature.com/articles/s41467-023-39614-y>
[277] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5023411/>
[278] <https://doi.org/10.1371/journal.pbio.3001535>
[279] <https://doi.org/10.1038/cr.2014.3>
[280] <https://www.repository.cam.ac.uk/items/629911bc-4616-4369-9424-3c7ebe8bb017>
[281] <https://www.mdpi.com/2079-7737/13/6/391>
[282] <https://www.proteinatlas.org/ENSG00000165819-METTL3>
[283] <https://www.nature.com/articles/cr20143>
[284] <https://www.cell.com/molecular-cell/fulltext/S1097-2765(16)30227-1>
[285] <https://www.sciencedirect.com/science/article/pii/S0753332223001312>
[286] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2025.1607932/full>
[287] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8041851/>
[288] <https://doi.org/10.1172/jci.insight.162436>
[289] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11839825/>
[290] <https://journals.plos.org/plosgenetics/article?id=10.1371%2Fjournal.pgen.1007412>
[291] <https://doi.org/10.1074/jbc.ac119.010078>
[292] <https://www.nature.com/articles/s41467-021-22424-5>
[293] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11177518/>
[294] <https://link.springer.com/article/10.1007/s11427-024-2897-y>
[295] <https://doi.org/10.1016/j.bbamcr.2022.119380>
[296] <https://doi.org/10.1073/pnas.2407910121>
[297] <https://ouci.dntb.gov.ua/en/works/73NLv089/>
[298] <https://doi.org/10.1101/2022.06.27.497872>
[299] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10408978/>
[300] <https://ncbi.nlm.nih.gov/pmc/articles/PMC6984009/>
[301] <https://pubmed.ncbi.nlm.nih.gov/25412662/>
[302] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5858226/>
[303] <https://doi.org/10.1038/s41421-018-0019-0>
[304] <https://mdpi-res.com/d_attachment/cells/cells-11-01461/article_deploy/cells-11-01461.pdf?version=1650954874>
[305] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11351023/>
[306] <https://www.biorxiv.org/content/10.1101/2023.11.20.565808v1.full.pdf>
[307] <https://www.xiahepublishing.com/1555-3884/GE-2024-00030>
[308] <https://www.nature.com/articles/ncomms12626>
[309] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5737695/>
[310] <https://doi.org/10.1101/gad.340695.120>
[311] <https://doi.org/10.1038/ncomms12626>
[312] <https://www.nature.com/articles/s41586-019-0916-x>
[313] <https://www.tandfonline.com/doi/full/10.1080/15476286.2021.2016203>
[314] <https://doi.org/10.1186/s12964-025-02058-6>
[315] <https://knowledge.uchicago.edu/records/qc5ky-9xr58>
[316] <https://www.cell.com/fulltext/S0092-8674(15)01024-7>
[317] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2025.1692608/full>
[318] <https://www.pnas.org/doi/full/10.1073/pnas.1812536116>
[319] <https://www.cell.com/cell/fulltext/S0092-8674(24)01324-2>
[320] <https://pmc.ncbi.nlm.nih.gov/articles/PMC13049655/>
[321] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9809312/>
[322] <https://rnajournal.cshlp.org/content/31/3/395.long>
[323] <https://link.springer.com/article/10.1186/s12967-024-05293-6>
[324] <https://www.mdpi.com/2073-4409/15/2/181>
[325] <https://doi.org/10.1101/2023.11.20.565808>
[326] <https://www.jbc.org/article/S0021-9258(21)00775-4/fulltext>
[327] <https://pdf.hanspub.org/bp20230400000_43402617.pdf>
[328] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10673353/>
[329] <https://link.springer.com/article/10.15252/embr.202255506>
[330] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10561361/>
[331] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8924732/>
[332] <https://link.springer.com/article/10.1186/s12967-025-06221-y>
[333] <https://www.nature.com/articles/s41419-021-03585-z>
[334] <https://link.springer.com/article/10.1186/s12870-025-06127-3>
[335] <https://www.sciencedirect.com/science/article/abs/pii/S1047847725000991?dgcid=rss_sd_all>
[336] <https://doi.org/10.2147/ijgm.s519741>
[337] <https://spj.science.org/doi/10.1016/j.csbj.2022.08.068>
[338] <https://www.cell.com/molecular-cell/fulltext/S1097-2765(18)30134-5>
[339] <https://preview-www.nature.com/articles/s41467-022-28753-3>
[340] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9907088/>
[341] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9850920/>
[342] <https://www.science.org/doi/10.1126/sciadv.abg0470>
[343] <https://link.springer.com/article/10.15252/embj.2020104514>
[344] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2025.1709742/full>
[345] <https://www.nature.com/articles/s41467-021-25803-0>
[346] <https://doi.org/10.1111/cpr.13157>
[347] <https://doi.org/10.15252/embj.2022113126>
[348] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9013966/>
[349] <https://song.korea.ac.kr/assets/pdf/117_okpark_molcell.pdf>
[350] <https://doi.org/10.1261/rna.080259.124>
[351] <https://doi.org/10.1126/sciadv.abq2945>
[352] <https://doi.org/10.1038/s41467-019-13317-9>
[353] <https://link.springer.com/article/10.1186/s11658-025-00723-9>
[354] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8261491/>
[355] <https://www.sciopen.com/local/article_pdf/10.1016/j.gendis.2025.101567.pdf>
[356] <https://doi.org/10.1016/j.cell.2015.08.011>
[357] <https://doi.org/10.1002/advs.202307639>
[358] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12886524/>
[359] <https://www.cell.com/cell-reports/fulltext/S2211-1247(19)30852-6>
[360] <https://doi.org/10.1158/2326-6066.cir-23-0339>
[361] <https://doi.org/10.1038/s41467-021-25803-0>
[362] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2024.1463847/full>
[363] <https://link.springer.com/content/pdf/10.1007/s13402-026-01289-0_reference.pdf>
[364] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12292157/>
[365] <https://doi.org/10.1038/s41467-019-09903-6>
[366] <https://ncbi.nlm.nih.gov/pmc/articles/PMC6478715/>
[367] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2025.1709260/full>
[368] <https://doi.org/10.1038/s41588-024-01962-w>
[369] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11479892/>
[370] <https://www.cell.com/developmental-cell/fulltext/S1534-5807(20)30843-1>
[371] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11116364/>
[372] <https://doi.org/10.1002/advs.202100209>
[373] <https://www.cell.com/cell-chemical-biology/fulltext/S2451-9456(24)00222-8>
[374] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2021.627455/full>
[375] <https://doi.org/10.1093/jleuko/qiae087>
[376] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12827480/>
[377] <https://www.medsci.org/v22p3815.htm>
[378] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12098234/>
[379] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10475571/>
[380] <https://www.frontiersin.org/journals/cell-and-developmental-biology/articles/10.3389/fcell.2025.1713615/full>
[381] <https://www.biorxiv.org/content/10.1101/2023.07.20.549950v4.full-text>
[382] <https://www.thno.org/v16p2576.pdf>
[383] <https://doi.org/10.1261/rna.064063.117>
[384] <https://doi.org/10.1016/j.jare.2024.06.019>
[385] <https://doi.org/10.1172/jci177932>
[386] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8350415/>
[387] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5666602/>
[388] <https://doi.org/10.1007/s10616-025-00882-9>
[389] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12741382/>
[390] <https://www.sciopen.com/article/10.1016/j.gendis.2025.101758>
[391] <https://preview-www.nature.com/articles/s41467-019-09903-6.pdf>
[392] <https://www.science.org/doi/10.1126/sciadv.ado7660>
[393] <https://www.nature.com/articles/s41590-020-0650-4>
[394] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5963928/>
[395] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2019.00922/full>
[396] <https://www.nature.com/articles/s41590-018-0275-z>
[397] <https://doi.org/10.1186/s12957-024-03402-9>
[398] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11648684/>
[399] <https://link.springer.com/article/10.1186/s40164-023-00429-8>
[400] <https://rcastoragev2.blob.core.windows.net/3fd54bf50814482715bf593bc47ef029/main.pdf>
[401] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8331015/>
[402] <https://www.mdpi.com/1422-0067/25/22/12150>
[403] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6478715/>
[404] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2024.1456891/full>
[405] <https://doi.org/10.1016/j.isci.2024.111071>
[406] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5855951/>
[407] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8780909/>
[408] <https://ncbi.nlm.nih.gov/pmc/articles/PMC3911877/>
[409] <https://www.cell.com/cancer-cell/fulltext/S1535-6108(21)00224-5>
[410] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2026.1918662/full>
[411] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11871626/>
[412] <https://www.nature.com/articles/s41467-019-09903-6>
[413] <https://www.nature.com/articles/s41590-022-01268-1>
[414] <https://doi.org/10.21203/rs.3.rs-3806743/v1>
[415] <https://www.nature.com/articles/s41598-025-16948-9>
[416] <https://www.frontiersin.org/journals/genetics/articles/10.3389/fgene.2022.903634/full>
[417] <https://preview-www.nature.com/articles/s41419-024-07108-4>
[418] <https://doi.org/10.2210/pdb7yg4/pdb>
[419] <https://doi.org/10.21203/rs.3.rs-1899379/v1>
[420] <https://pmc.ncbi.nlm.nih.gov/articles/PMC4673968/>
[421] <https://pubmed.ncbi.nlm.nih.gov/38058803>
[422] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10522386/>
[423] <https://www.biorxiv.org/content/biorxiv/early/2025/12/08/2025.12.04.691578.full.pdf>
[424] <https://tcr.amegroups.org/article/view/113033/html>
[425] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12335694/>
[426] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8722703/>
[427] <https://www.nature.com/articles/s41420-022-01040-2>
[428] <https://www.frontiersin.org/journals/oncology/articles/10.3389/fonc.2021.629560/full>
[429] <https://doi.org/10.1038/s12276-025-01594-y>
[430] <https://link.springer.com/article/10.1038/s44318-026-00707-1>
[431] <https://doi.org/10.1074/jbc.m608745200>
[432] <https://doi.org/10.1074/jbc.m109.040113>
[433] <https://www.frontiersin.org/journals/oncology/articles/10.3389/fonc.2023.1229168/full>
[434] <https://www.cell.com/iscience/fulltext/S2589-0042(25)00072-0>
[435] <https://doi.org/10.1016/j.isci.2025.111812>
[436] <https://link.springer.com/article/10.1186/s10020-024-01018-z>
[437] <https://www.cell.com/molecular-therapy-family/nucleic-acids/fulltext/S2162-2531(21)00266-3>
[438] <https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE212043>
[439] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12205329/>
[440] <https://link.springer.com/content/pdf/10.1038/s44318-026-00707-1.pdf>
[441] <https://doi.org/10.1093/jimmun/vkag034>
[442] <https://pmc.ncbi.nlm.nih.gov/articles/PMC13403043/>
[443] <https://link.springer.com/article/10.1007/s13402-026-01289-0>
[444] <https://www.omim.org/entry/606872>
[445] <https://www.embopress.org/doi/pdf/10.15252/embr.201744940?download=true>
[446] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2025.1706971/full>
[447] <https://www.nature.com/articles/s41467-025-65542-0.pdf?error=cookies_not_supported&code=2a945968-11f6-42a3-9aab-ff0f6e448650>
[448] <https://doi.org/10.3390/life11070669>
[449] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12451313/>
[450] <https://www.nature.com/articles/s41467-024-46357-x>
[451] <https://www.nature.com/articles/s41590-022-01398-6>
[452] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11362088/>
[453] <https://www.nature.com/articles/s41388-025-03452-7>
[454] <https://doi.org/10.1016/j.clnves.2025.100008>
[455] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10330838/>
[456] <https://doi.org/10.1186/s12935-020-1105-6>
[457] <https://www.cancerbiomed.org/content/19/4/385>
[458] <https://www.nature.com/articles/s41420-022-01286-w>
[459] <https://doi.org/10.1016/j.jbc.2023.104738>
[460] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8609105/>
[461] <https://doi.org/10.1038/cr.2017.10>
[462] <https://www.mdpi.com/1420-3049/29/1/140>
[463] <https://www.cell.com/molecular-therapy-family/nucleic-acids/fulltext/S2162-2531(25)00019-8>
[464] <https://doi.org/10.1016/j.molcel.2023.10.028>
[465] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8134747/>
[466] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11730786/>
[467] <https://doi.org/10.1101/2025.01.28.635339>
[468] <https://link.springer.com/article/10.1007/s00018-025-05673-1>
[469] <https://doi.org/10.1016/j.cyto.2025.157011>
[470] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10472310/>
[471] <https://doi.org/10.1016/j.tibs.2024.04.001>
[472] <https://doi.org/10.1084/jem.20200829>
[473] <https://doi.org/10.1093/burnst/tkad023>
[474] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10390869/>
[475] <https://doi.org/10.1038/s41420-022-01040-2>
[476] <https://doi.org/10.1084/jem.20210279>
[477] <https://platform.opentargets.org/target/ENSG00000185728>
[478] <https://doi.org/10.1038/s41419-025-07606-z>
[479] <https://www.sciencedirect.com/science/article/abs/pii/S0168952521003358>
[480] <https://doi.org/10.3390/cells11091461>
[481] <https://www.nature.com/articles/s41392-022-00905-3>
[482] <https://doi.org/10.55976/jcd.120221311-12>
[483] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9061745/>
[484] <https://link.springer.com/article/10.1038/s44318-024-00153-x>
[485] <https://link.springer.com/article/10.15252/embr.202254686>
[486] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10089659/>
[487] <https://www.mdpi.com/2073-4409/11/9/1461>
[488] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8681016/>
[489] <https://doi.org/10.1016/j.molcel.2022.02.034>
[490] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7700739/>
[491] <https://www.cell.com/molecular-cell/fulltext/S1097-2765(22)00208-8>
[492] <https://vivo.weill.cornell.edu/display/pubid35058317>
[493] <https://doi.org/10.1093/narcan/zcaf006>
[494] <https://doi.org/10.1101/2024.04.07.588211>
[495] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10491980/>
[496] <https://link.springer.com/article/10.1186/s11658-024-00545-1>
[497] <https://doi.org/10.1186/s12943-022-01555-3>
[498] <https://doi.org/10.1101/2022.09.08.507100>
[499] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8727287/>
[500] <https://hal.sorbonne-universite.fr/hal-04100169v1/file/IGF2BP3.pdf>
[501] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10988304/>
[502] <https://doi.org/10.1002/ctm2.1457>
[503] <https://www.sciengine.com/sci-open/doi/pdf/5D2F30AAE16E4D78A038C18384DCFFEC>
[504] <https://www.sciencedirect.com/science/article/pii/S2589004221013146>
[505] <https://doi.org/10.1093/nar/gkaf176>
[506] <https://doi.org/10.1016/j.celrep.2024.113769>
[507] <https://doi.org/10.7150/jca.83863>
[508] <https://pmc.ncbi.nlm.nih.gov/articles/PMC13253730/>
[509] <http://www.nature.com/articles/s41598-019-45636-8.pdf>
[510] <https://link.springer.com/article/10.1038/sj.emboj.7601765>
[511] <https://doi.org/10.1016/j.apsb.2025.02.005>
[512] <https://doi.org/10.1101/2019.12.20.885558>
[513] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12794334/>
[514] <https://www.science.org/doi/10.1126/science.abl7207>
[515] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10074099/>
[516] <https://link.springer.com/article/10.15252/embr.202255681>
[517] <https://www.nature.com/articles/s41590-025-02235-2>
[518] <https://www.nature.com/articles/s41419-026-09069-2.pdf>
[519] <https://jhi.rupress.org/jem/article/218/8/e20210279/212430/The-RNA-m6A-reader-YTHDF2-controls-NK-cell>
[520] <https://www.nature.com/articles/s41467-022-35710-7>
[521] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10150872/>
[522] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12614224/>
[523] <https://www.frontiersin.org/journals/oncology/articles/10.3389/fonc.2026.1771313/full>
[524] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11664238/>
[525] <https://link.springer.com/article/10.1007/s00262-024-03705-6>
[526] <https://doi.org/10.1038/cr.2018.7>
[527] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9495716/>
[528] <https://www.cell.com/cell-reports/fulltext/S2211-1247(23)00695-2>
[529] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12440514/>
[530] <https://www.cd-genomics.com/case-m6a-methylation-and-single-cell-analyses.html>
[531] <https://orbi.uliege.be/bitstream/2268/290538/1/21%20The%20m6A%20Reader%20IGF2BP2%20Regulates%20Macrophage%20Phenotypic%20Activation%20and%20Inflammatory%20Diseases%20by%20Stabilizing%20TSC1%20and%20PPAR%CE%B3.pdf>
[532] <https://www.whatisepigenetics.com/a-role-for-m6a-methylation-in-the-immune-response-of-natural-killer-cells-toward-cancer/>
[533] <https://www.frontiersin.org/research-topics/72578/m6a-modification-in-immune-cell-regulated-inflammatory-diseasesundefined>
[534] <https://doi.org/10.4049/jimmunol.2300339>
[535] <https://doi.org/10.1073/pnas.1918986117>
[536] <https://www.nature.com/articles/s41420-021-00488-y>
[537] <https://journals.sagepub.com/doi/full/10.1177/11795549231203150>
[538] <https://www.cell.com/cell-reports/fulltext/S2211-1247(23)01204-4>
[539] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8420859/>
[540] <https://www.frontiersin.org/journals/cell-and-developmental-biology/articles/10.3389/fcell.2019.00363/full>
[541] <https://escholarship.org/content/qt308941h1/qt308941h1.pdf?t=rsp688&utm_source=consensus>
[542] <https://ir.library.osaka-u.ac.jp/repo/ouka/all/97231/Immunity_57_6_1360.pdf>
[543] <https://media.springernature.com/original/springer-static/esm/art%3A10.1038%2Fs41467-021-25803-0/MediaObjects/41467_2021_25803_MOESM1_ESM.pdf>
[544] <https://www.nature.com/articles/s41420-025-02867-1>
[545] <https://doi.org/10.21769/bioprotoc.1010310>
[546] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10070103/>
[547] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9825529/>
[548] <https://www.science.org/doi/10.1126/sciadv.abd4742>
[549] <https://doi.org/10.3389/fonc.2021.718644>
[550] <https://doi.org/10.1159/000534162>
[551] <https://pmc.ncbi.nlm.nih.gov/articles/PMC2928180/>
[552] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7417170/>
[553] <https://doi.org/10.1186/s12967-024-05368-4>
[554] <https://link.springer.com/article/10.1007/s00018-024-05261-9>
[555] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11853652/>
[556] <https://pmc.ncbi.nlm.nih.gov/articles/PMC13060541/>
[557] <https://drpress.org/ojs/index.php/ijbls/article/view/34109>
[558] <https://www.sciencedirect.com/science/article/pii/S3050538025000171>
[559] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8780705/>
[560] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2026.1694842/full>
[561] <https://doi.org/10.1016/j.scib.2023.11.029>
[562] <https://www.nature.com/articles/s41419-025-07606-z>
[563] <https://pubmed.ncbi.nlm.nih.gov/38058838>
[564] <https://pmc.ncbi.nlm.nih.gov/articles/PMC2434375/>
[565] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7264473/>
[566] <https://rnajc.ucsf.edu/sites/rnajc.ucsf.edu/files/nature23450.pdf>
[567] <https://patents.google.com/patent/CN105593373A/zh>
[568] <https://www.thermofisher.com/us/en/home/life-science/cell-analysis/cell-analysis-learning-center/immunology-at-work/natural-killer-cell-overview.html>
[569] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9581620/>
[570] <https://doi.org/10.3389/fimmu.2024.1440308>
[571] <https://doi.org/10.1080/15592294.2020.1827722>
[572] <https://www.merckmanuals.com/professional/immunology-allergic-disorders/biology-of-the-immune-system/cellular-components-of-the-immune-system>
[573] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6135950/>
[574] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12202376/>
[575] <https://www.rndsystems.com/resources/cell-markers/immune-cells/dendritic-cells>
[576] <https://doi.org/10.66106/mzabb7.20250201>
[577] <https://www.nature.com/articles/cr20187>
[578] <https://doi.org/10.1186/s12931-024-03061-0>
[579] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11891544/>
[580] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2026.1930681/full>
[581] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5648532/>
[582] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9004556/>
