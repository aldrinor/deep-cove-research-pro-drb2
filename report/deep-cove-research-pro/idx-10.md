# Deep Learning in Financial Asset Management: Models, Applications, and Evaluation, 2018–2023

**Task-dependent gains across financial decisions** characterize deep learning research published between 2018 and 2023. Feed-forward networks and autoencoders support characteristic-based investing and feature extraction; convolutional, recurrent, attention-based, and graph models exploit local, temporal, multimodal, and relational information; and deep reinforcement learning connects these representations to trading, execution, and allocation decisions. The clearest application distinction is between the accounting and economic information emphasized in value/factor investing and the price, volume, and order-book information emphasized in forecasting and trading. Portfolio management adds a separate question: how much capital to allocate, when to rebalance, and which risks to control. [1]

**Economic performance remains the decisive test**: better prediction accuracy does not automatically produce better investment results. The literature supports evaluating forecasts alongside compounded returns, risk-adjusted performance, drawdowns, transaction costs, and appropriate benchmarks, rather than declaring one DL architecture universally superior. [2]

| Model family | Core mechanism | Typical inputs | Typical output | Best-fit financial use |
|---|---|---|---|---|
| ANN | Layered nonlinear mapping | Firm characteristics; market features | Forecast, class, factor score | Nonlinear factor construction and selection |
| AE | Encoding and reconstruction | High-dimensional features; charts | Compressed representation | Feature extraction and latent factors |
| CNN | Shared local filters | Price–volume arrays; charts; order books | Local features or predictions | Technical patterns and market microstructure |
| GAN | Adversarial learning | Returns, correlations, latent noise | Synthetic scenarios | Simulation, stress testing, robust allocation |
| GNN | Relational aggregation | Asset features and financial networks | Relational scores or embeddings | Connected-stock prediction and selection |
| RNN, LSTM, GRU | Recurrent temporal state | Prices, returns, sequential features | Sequential forecast or representation | Forecasting and temporal trading signals |
| Transformers | Attention across observations | Market sequences; text; other modalities | Forecast or contextual representation | Long-range and multimodal modeling |
| DRL, especially DQN | Reward-driven sequential decisions | Market state, positions, costs | Trading action or portfolio policy | Trading, execution, and rebalancing |

**The report follows the investment questions** behind this table. It first explains the eight model families and their principal subtypes, then compares research on value/factor investing, algorithmic trading, portfolio management, and price forecasting. The final section supplies the requested eight portfolio metrics, six regression-forecasting measures, and four classification measures, with their calculations, meanings, and practical interpretation.

## 1. Deep learning models and their financial applications

**Architecture should follow information structure** rather than model novelty. A firm-characteristic dataset, an order-book sequence, a network of connected companies, and a portfolio-rebalancing problem contain different kinds of structure. The reviewed literature uses specialized architectures to capture those differences, often combining several architectures within one investment system. [1]

**These families are not mutually exclusive**. CNNs, RNNs, and Transformers are neural-network architectures; an autoencoder describes an encoding-and-reconstruction design; a GAN describes adversarial training; and DRL describes a decision-learning framework. A trading agent can therefore use a CNN or LSTM inside a DQN, while a generative model can contain recurrent or Transformer blocks. This distinction is important when interpreting studies classified as “hybrid,” “recurrent,” or “reinforcement learning.” [2]

### Artificial Neural Networks: nonlinear mappings from features to financial outputs

**ANNs provide the general predictive foundation**. An artificial neuron forms a weighted combination of its inputs, adds a bias, and applies an activation function. Layers of these units create a mapping from input features to an output; training adjusts the weights through forward computation and back-propagation to reduce a chosen loss. In this report, “ANN” primarily denotes a feed-forward multilayer perceptron, distinguishing it from the more specialized architectures below. A shallow ANN is not automatically a deep-learning model. [3]

**Their strength is nonlinear feature interaction**. In factor investing, for example, the relationship between valuation and expected returns may depend on profitability, risk, or other characteristics. A feed-forward network can learn such conditional interactions without requiring the researcher to specify every interaction term beforehand. Feng, Polson, and Xu’s 2018 deep-factor study used firm characteristics to construct learned factors and minimize pricing errors, illustrating an economically structured application of this flexibility. [4]

**Typical financial outputs are diverse**. ANNs are used for continuous price or return forecasts, classifications of market patterns, stock-selection scores, and characteristic-based factor construction. Fioribello and Giribone’s 2018 financial-pattern study combined shallow and deep ANNs with a convolutional network, selecting among classifiers for technical-analysis problems. [5]

**Flexibility creates a regularization trade-off**. A feed-forward network has no built-in temporal memory or explicit representation of company relationships, so those structures must enter through engineered inputs or additional modules. Its capacity is useful when nonlinear interactions are economically relevant, but a simpler model remains a meaningful competitor when the sample is small or the signal weak. The asset-management literature consequently emphasizes regularization and out-of-sample performance rather than training fit alone. [1]

### Autoencoders: learning compact financial representations

**Autoencoders compress before making decisions**. An encoder maps an input vector into a latent representation, commonly through a bottleneck containing fewer dimensions. A decoder reconstructs the original input from that representation. Training therefore learns which combinations of features are sufficient for reconstruction, rather than directly learning a future return or trading label. [2]

**Financial applications emphasize dimensionality reduction**. Financial datasets can contain many correlated indicators or characteristics. An AE can summarize them before a forecasting network or trading agent processes the representation. In Soleymani and Paquet’s DeepBreath application, published in 2020, a restricted stacked autoencoder reduced an 11-feature input to three features before a CNN within a DRL portfolio-management framework. [2]

**Compression also supports alternative representations**. Hu and colleagues’ 2018 convolutional-autoencoder application transformed candlestick charts into numerical stock representations for similarity analysis. The relevant financial task was not merely predicting one stock’s next price: it was learning a representation with which stocks could be compared. [2]

**Latent factors extend the same idea**. Gu, Kelly, and Xiu’s *Autoencoder Asset Pricing Models* appeared in 2021, placing autoencoder-based representation learning within asset pricing rather than only preprocessing. This line of work connects high-dimensional characteristics and returns to a smaller latent structure. [1]

**Reconstruction quality and investment usefulness differ**. A compact representation may preserve dominant variation while discarding a small but valuable predictive signal. Accordingly, an AE should be judged through the downstream forecasting, selection, or allocation task as well as its reconstruction objective. Its strongest rationale is reducing redundant information; its economic value depends on what survives that reduction.

### Convolutional Neural Networks: local market patterns

**CNNs learn reusable local features**. Convolutional layers apply learned filters across a structured input, sharing filter weights across positions. Pooling layers may then reduce the feature-map dimensions. Unlike a fully connected network, a CNN explicitly exploits local arrangement, whether that arrangement is spatial in a chart or temporal in a numerical sequence. [1]

**Financial inputs need not be images**. A CNN can process a candlestick chart, a matrix of technical indicators, or an array of recent prices and volumes. Open, high, low, close, and volume—OHLCV—are particularly common market inputs. A one-dimensional convolution can identify local temporal patterns directly, without converting numerical observations into pictures. [6]

**Chart analysis is one established scenario**. Candlesticks visually encode open, high, low, and close prices, making them compatible with image-oriented CNN designs. Kusuma and colleagues’ 2019 application used candlestick images for stock prediction. The financial rationale is automated extraction of local chart patterns, rather than reliance on hand-coded pattern definitions. [2]

**Order books provide another natural structure**. DeepLOB, published in 2019, combined convolutional feature extraction with LSTM sequence modeling. Its CNN component captured local structure in limit-order-book data, while the LSTM captured temporal dependencies. This division illustrates why CNN–RNN combinations recur in market-microstructure research. [2]

**Representation choice must earn its complexity**. Converting prices into a chart does not itself add information. The relevant comparison is whether the visual representation and convolutional structure improve the final task relative to raw numerical inputs. The stock-market survey specifically observes that the candlestick application lacked that raw-data comparison, making the architectural contribution more informative than a general claim of image superiority. [2]

### Generative Adversarial Networks: scenarios and adversarial objectives

**GANs learn through competing networks**. In a conventional generative adversarial network, a generator transforms latent noise into synthetic observations, while a discriminator attempts to distinguish generated observations from real ones. The generator improves by producing samples that are harder to distinguish. The financial objective is usually learning a distribution or scenario-generating mechanism, not simply minimizing next-period point-forecast error. [7]

**Scenario generation supports risk-sensitive decisions**. Historical data provide only one realized path. A generative model can produce additional return sequences, price-trend scenarios, or cross-asset correlation structures for strategy evaluation and portfolio construction. The 2019 PAGAN preprint learned a joint distribution of asset price trends and used simulations to select diversification intended to balance risk and expected return. [8]

**CorrGAN targets cross-asset dependence directly**. Presented at ICASSP in 2020, CorrGAN sampled financial correlation matrices and recovered many stylized properties of empirical matrices estimated from asset returns. Its stated applications included trading-strategy enhancement and portfolio stress testing. This matters because a portfolio’s risk depends on joint asset behavior, not only the distribution of each asset separately. [9]

**Adversarial training can also target robustness**. Pun, Wang, and Wong’s 2020 GANr added a regressor that learned portfolio solutions from real and generated scenarios. Their objective was resilience under adverse financial conditions, linking scenario generation directly to portfolio choice. [7]

**Asset-pricing adversaries serve a different purpose**. Chen, Pelger, and Zhu’s 2023 model used an adversarial approach to construct informative test assets under the no-arbitrage condition. Here, adversarial learning challenges the pricing model with difficult portfolios; it should not be interpreted as merely creating synthetic market prices. [10]

**Distributional realism determines practical usefulness**. Financial GANs must reproduce economically relevant dependence, volatility clustering, and tail behavior, rather than only visually plausible paths. A 2021 financial-GAN presentation identified mode collapse, unstable training, and inadequate evaluation measures as recurring difficulties. Scenario diversity is useful only when the generated scenarios preserve the properties relevant to the investment decision. [11]

### Graph Neural Networks: learning from financial relationships

**GNNs add relationships to asset features**. A graph represents entities as nodes and relationships as edges. Graph convolution or attention combines information from connected entities to update their representations, allowing a stock’s prediction to depend on relevant neighboring companies as well as its own history. This is commonly described as neighborhood aggregation or message passing. [12]

**Financial graphs encode different economic links**. Examples include ownership networks, industry membership, company relationships, and covariance-based connections. Chen and colleagues’ 2018 application constructed a graph of 3,024 listed companies from investment relationships and used a three-layer graph-convolutional network for prediction. The added structure represented inter-company connectivity that isolated price models would omit. [12]

**Stock selection benefits from relational context**. The 2023 H-GAT preprint combined technical and fundamental sequences with an LSTM, then used graph attention to represent higher-order relationships and predict stock-return ranks. Rather than asking only which company has the strongest individual features, the model asked how those features interact with a wider relational structure. [13]

**Portfolio construction uses relationships differently**. Mercury, published in 2023, constructed a hypergraph from covariance information and stock-industry relationships. A hypergraph can connect a group of assets through a shared relationship rather than representing every connection only as a separate pair. Mercury used this structure to inform stock screening and portfolio generation. [14]

**Related financial applications extend beyond investing**. The financial-GNN review also describes 2019 applications to loan-guarantee risk and online financial anti-fraud. These cases illustrate the architecture’s broader relevance wherever financial outcomes depend on connected borrowers, customers, transactions, or firms, although the asset-management focus here remains stock prediction and portfolios. [15]

**Graph quality matters as much as depth**. A graph based on economically meaningful relationships can add information; a graph based on unstable or poorly timed correlations can propagate noise. Computation also becomes more demanding as graphs grow, while sampling can improve efficiency at the cost of losing structural information. The appropriate judgment is therefore conditional on the quality, timing, and scalability of the relationship data. [15]

### RNNs, LSTMs, and GRUs: temporal state and gated memory

**Recurrent models carry information through time**. An RNN updates a hidden state from the current observation and the preceding state. This makes the ordering of observations part of the model itself, which is useful for prices, returns, order-book updates, and other financial sequences. [16]

| Architecture | Memory mechanism | Main computational characteristic | Typical financial role |
|---|---|---|---|
| RNN | Recurrent hidden state | Simple recurrence; difficult long-memory training | Sequential forecasting and market representation |
| LSTM | Cell state; input, forget, output gates | More elaborate control of retained information | Longer-dependency forecasts and trading features |
| GRU | Hidden state; reset and update gates | Fewer parameters than comparable LSTM | Efficient sequence forecasting and allocation features |

**Vanilla recurrence struggles with long dependencies**. During training, gradients propagated over many time steps can become extremely small or large, making distant relationships difficult to learn. LSTM and GRU designs address this numerical problem through gated updates, rather than establishing that financial markets necessarily contain exploitable long-memory signals. [17]

**LSTM separates memory from exposed output**. Its input gate regulates new information, its forget gate regulates retained information, and its output gate regulates what is passed onward from the cell state. This structure supports retaining selected information over longer sequences and reduces the vanishing-gradient difficulty of a basic RNN. [18]

**LSTM applications span several investment stages**. They include next-period prices, return direction, temporal features for trading agents, and financial-statement-based value extraction. Huang’s DeepValue framework used LSTM within a system that extracted company value and selected stocks using a value–price gap, demonstrating that recurrent networks are not confined to technical price forecasting. [19]

**GRU provides a simpler gated alternative**. Its reset gate controls how previous information enters a candidate state, while its update gate regulates the balance between retained and new information. With fewer parameters than an otherwise comparable LSTM, a GRU can reduce training cost while preserving a mechanism for learning temporal dependencies. [16]

**Financial uses reflect that efficiency trade-off**. GRUs appear in price forecasting, multifactor stock selection, and portfolio-state representation. The 2022 CS-GRU stock-selection study combined financial, technical, and sentiment factors, while the 2023 risk-return reinforcement-learning study used GRU features before choosing portfolio weights. [20][21]

**LSTM and GRU require task-specific comparison**. The choice depends on sequence length, sample size, model width, and computational constraints. One 2021 trading study used LSTM for short-term forecasts and GRU for medium-term forecasts, but that allocation was a study design, not a universal rule assigning forecast horizons to architectures. [18]

### Transformers: attention over financial sequences and modalities

**Transformers model content-dependent interactions directly**. Attention assigns different weights to observations or representations according to their relevance to one another. This gives the model a way to connect distant sequence positions without relying solely on information passing through a recurrent hidden state. [16]

**The distinction is not equal versus unequal memory**. RNNs share recurrent parameters over time, but their changing hidden states and gates can still give different observations different influence. Transformers instead make the relevance-weighting operation explicit through attention. Their financial appeal is flexible modeling of interactions across times, assets, or information sources.

**Applications include direction and volatility forecasting**. The 2022 stock-prediction survey records a 2020 Transformer application using prices and indicators for price-movement prediction on NASDAQ and CSI-500 data. It also records a 2020 application combining price, text, audio, and video to forecast volatility using S&P 500 earnings-call data. [22]

**Attention can also enter allocation systems**. The 2023 reinforcement-learning review describes a relation-aware Transformer whose encoder extracts sequential features and whose decoder supports portfolio decisions. Its experiments covered two cryptocurrency datasets and one stock dataset, showing that attention can support decision representations as well as standalone forecasts. [23]

**Longer context is an opportunity, not evidence**. Attention can represent long-range relationships, but those relationships must still improve forecasts against simpler alternatives. The 2022 forecast-evaluation study’s exchange-rate examples show why a sophisticated Transformer should be compared with a naïve last-observation forecast before its predictive value is accepted. [24]

### Deep Reinforcement Learning, especially Deep Q-Networks

**DRL learns actions rather than labels**. An agent observes a state, selects an action, receives a reward, and learns a policy or value function intended to maximize cumulative discounted reward. A deep neural network represents the policy, the value function, or the market information used by them. [2]

**The state includes investment consequences**. In finance, useful state information can include prices, indicators, current holdings, remaining execution time, and previous portfolio weights. Actions may be buy, sell, hold, order size, or a vector of asset allocations. Rewards can reflect profit, risk-adjusted performance, drawdown, or costs, making the reward definition an economic modeling choice rather than a minor implementation detail. [23]

**DQN estimates the value of actions**. A Deep Q-Network uses a neural network to approximate the action-value function: the expected future reward associated with taking an action in a state. Experience replay stores transitions and samples training minibatches from them, while a target network stabilizes the learning target. [25][26]

**Discrete choices fit DQN naturally**. Buy–hold–sell decisions and discrete reallocation choices are direct examples. DQN is not restricted to CNN encoders: the reviewed Trading Deep Q-Network used a feed-forward network, illustrating that action-value learning and feature architecture are separate design decisions. [2]

**Variants address specific estimation problems**. Double DQN separates action selection from value estimation to reduce overestimation. Dueling architectures estimate a state-value component and an action-advantage component separately. Lucarelli and Borrotti’s 2020 portfolio study compared DQN, Double DQN, and Dueling Double DQN within a multi-agent cryptocurrency framework. [26]

**Continuous weights favor different formulations**. A portfolio with many continuously varying asset weights is not naturally a small discrete-action problem. Actor–critic methods such as Deep Deterministic Policy Gradient, or DDPG, learn continuous actions directly, while policy-gradient approaches optimize portfolio policies without enumerating every allocation. Hegde, Kumar, and Singh’s 2018 study explicitly used DDPG to address continuous-action portfolio construction. [27]

**Simulation assumptions influence learned behavior**. A policy is optimized for the environment and reward presented during training. If transaction costs, liquidity, or market impact are poorly represented, the policy can exploit those simplifications. The 2023 RL review identifies realistic market simulation and large-action-space allocation as important practical boundaries. [23]

### Choosing models across the four financial applications

**Reported prevalence depends on the question**. Jiang’s 2021 stock-prediction survey found recurrent models historically most frequent, with their share declining as additional architectures emerged. A separate 2023 quantitative-finance overview reported approximately 39% reinforcement-learning and 25% hybrid approaches in its sample of more than 70 papers. These findings describe different populations and different classifications: an RL system can itself contain an LSTM or a hybrid network. [12][6]

**The four applications optimize different objects**. Stock selection produces rankings or inclusion decisions; algorithmic trading produces positions and executions; portfolio management produces capital weights; and forecasting produces estimates of future variables. Their model, data, and metric choices follow those outputs.

| Application | Main objective | Common DL emphasis | Primary data emphasis | Main evaluation emphasis |
|---|---|---|---|---|
| Value/factor investing | Factors, valuation, stock ranking | Feed-forward DNNs; AE; recurrent selection models | Firm characteristics, statements, returns | Alpha, pricing errors, returns, Sharpe |
| Algorithmic trading | Signals, positions, execution | LSTM/CNN hybrids; DQN and other DRL | OHLCV, indicators, ticks, order books | Net returns, Sharpe, MDD, execution costs |
| Portfolio management | Weights and rebalancing | Policy/actor–critic DRL; recurrent and graph features | Multi-asset prices, returns, relationships | Wealth, risk-adjusted return, drawdown, tail risk |
| Price forecasting | Levels, returns, direction, volatility | RNN/LSTM/GRU; CNN hybrids; attention | Price histories, OHLCV, selected alternative data | RMSE, MAPE, MAE; classification measures |

**The architectural takeaway is conditional**: use nonlinear mappings for feature interactions, recurrence or attention for sequences, graphs for relationships, generators for scenarios, and DRL when sequential actions are the actual object of optimization.

## 2. Value and factor investing: research status, 2018–2023

### Objectives and commonly used models

**Factor research learns economically relevant signals**. Its principal objectives are predicting conditional returns, constructing nonlinear factors, reducing asset-pricing errors, and ranking securities for investment. Value investing is a particular part of this broader area: it emphasizes the relationship between an estimate of company value and its market price. Factor investing also encompasses signals such as momentum, quality, liquidity, and risk. [1]

**Feed-forward networks are an established core** because firm characteristics naturally form a cross-sectional feature vector. Their role is to transform noisy, numerous, correlated predictors into return estimates or learned factors. Autoencoders support latent-component learning, while LSTM and GRU designs become relevant when sequences of accounting, technical, or other factors are explicitly modeled. Graph-attention hybrids add inter-company relationships to that temporal information. [1][13]

**Economic objectives distinguish this domain** from generic price regression. Feng, Polson, and Xu’s 2018 approach used deep networks to construct characteristic-sorted long–short factors and minimize pricing alpha. Chen, Pelger, and Zhu’s 2023 approach instead used no-arbitrage restrictions and adversarially selected test assets to estimate a flexible asset-pricing model. Both connected network learning to a financial criterion, not just an unrestricted statistical fit. [4][10]

| Study | Main objective | DL design | Principal inputs | Evaluation focus |
|---|---|---|---|---|
| Feng, Polson & Xu, 2018 | Construct priced factors | Feed-forward deep factor model | Returns; 56 firm characteristics | Pricing alpha; out-of-sample R² |
| DeepValue, 2022 | Value-based stock selection | Deep mapping, multitask learning, LSTM | Financial statements | Market and EPS-selection comparisons |
| CS-GRU, 2022 | Multifactor stock selection | Optimized GRU | Financial, technical, sentiment factors | Return, Sharpe, MDD |
| H-GAT, 2023 preprint | Rank stock returns | LSTM and graph attention | Technical, fundamental, relational data | Profitability and Sharpe |
| Chen, Pelger & Zhu, 2023 | Estimate asset-pricing model | Deep networks with adversarial testing | Stock conditioning data; macroeconomic series | Sharpe, explained variation, pricing errors |

**Selection need not require precise prices**. A model can be useful if it correctly ranks investment opportunities even when its absolute return forecasts remain noisy. DeepValue selected stocks using a learned value–price gap; H-GAT predicted return ranks; and characteristic-sorted factor models converted learned characteristics into long–short portfolio exposures. These outputs are closer to security selection than an isolated next-day price estimate. [19][13]

### Data and representative findings

**Fundamentals supply the domain’s distinctive information**. Common inputs include valuation ratios, profitability and quality measures, financial statements, and other firm characteristics. Historical returns and prices remain important for constructing targets, estimating risks, and testing selections. Blitz and colleagues’ 2023 practitioner-oriented review describes broad predictor sets containing past-return signals, valuation, quality, and risk measures, often exceeding 50 features. [28]

**Technical indicators are complementary transformations**. They derive from prices and volumes rather than from company accounts. In the 2022 CS-GRU study, the factor database contained 26 inputs: 16 financial-index factors, nine technical indicators, and one public-opinion sentiment factor. The composition demonstrates a substantive combination of fundamental and market information, rather than treating all predictors as interchangeable numerical columns. [20]

**The original deep-factor experiment provides scale**. Feng, Polson, and Xu’s 2018 study used the annually largest 3,000 US firms and 56 published characteristics, with training over 1975–2004 and prediction over 2005–2017. Its reported improvements depended on the pricing benchmark against which learned factors were assessed. [4]

| Pricing benchmark | Reported relative improvement in out-of-sample R² |
|---|---:|
| CAPM | 12.5% |
| Fama–French three-factor model | 1.0% |
| Fama–French five-factor model | 2.1% |

**Benchmark strength changes the apparent gain**. These are relative improvements in the study’s out-of-sample R² measure, not percentage-point increases in annual returns. Their practical significance is that learned factors added more explanatory improvement against the simpler CAPM than against either multifactor benchmark. The result supports nonlinear factor augmentation in that experiment, rather than a general investment-performance ranking.

**DeepValue illustrates a different selection mechanism**. Huang’s 2022 study used four feature sets drawn from 11 years of financial statements for 90 semiconductor companies listed on the Taiwan Stock Exchange. Its multitask structure shared information across firms, while LSTM supported value extraction. The study reported recommendation lists outperforming both the market and earnings-per-share-based selection, tying the result to a specific industry and comparison. [19]

**CS-GRU links factors to a trading portfolio**. Its CSI 300 dataset ran from November 2012 through February 2021, with training through December 2019 and testing from January 2020. The paper reported a 40.66% annualized return and a 17.38% maximum-drawdown magnitude for its stated full backtest period. Its reported Sharpe value of 127.08% corresponds, by percentage-to-ratio conversion, to 1.2708; these full-period statistics should be distinguished from the separately specified holdout interval. [20]

**Point-in-time accounting data are essential**. Statements become public after their accounting periods end and may subsequently be revised. A selection model must use the version and publication timing that an investor could actually have observed. Otherwise, apparent skill can arise from information entering the dataset earlier than it entered the market. [2]

### Evaluation and research judgment

**Pricing success and investment success differ**. A good pricing model seeks to reduce unexplained pricing errors or test-asset alphas. A successful investment strategy seeks attractive returns, potentially including positive alpha relative to a specified benchmark. These are different uses of “alpha”: reducing a pricing model’s residual alpha is not the same objective as reducing a manager’s investment alpha.

**Statistical fit is therefore insufficient**. Feng and colleagues explicitly caution that adding factors can increase regression R² without reducing pricing intercepts. Chen, Pelger, and Zhu’s 2023 evaluation consequently combined out-of-sample explained variation with pricing errors and Sharpe ratios. The appropriate assessment examines both economic restrictions and the portfolio consequences of the learned signal. [4][10]

**Common measures reflect these dual objectives**. Return, Sharpe ratio, and maximum drawdown assess selected portfolios; R² and explained variation assess predictive or explanatory fit; and pricing errors and alpha-based comparisons assess the asset-pricing model. Returns are the most common financial measure in the broader backtested stock-market survey, with Sharpe and drawdown also prominent. [2]

**The strongest case is structured nonlinearity**. DL is particularly plausible when many characteristics interact and when an economic objective constrains what the model learns. It is less persuasive when a more complex network merely improves training fit or produces a stock ranking whose performance disappears under realistic investment restrictions. The 2022 asset-management review also records an ANN factor study with strong in-sample but mediocre out-of-sample performance, providing a direct counterexample to automatic DL superiority. [1]

**The factor-investing takeaway is economic alignment**: judge learned characteristics by benchmark-relative pricing and out-of-sample portfolio usefulness, not by network depth or fit alone.

**Additional documented evidence**

Value/factor investing (2018–2023): objectives—factor discovery/integration, stock selection, return/risk-premium prediction, pricing-error reduction, anomaly detection and long–short portfolios [48][49]. Boundary—asset-price/return modelling; portfolio management combines forecasts with risk models, while trading/forecasting emphasize price–volume data; overlap remains [48]. Models—NNs/deep NNs recur; MLP, LSTM/GAN, PCA, RF/SVM/shallow NNs appear; RNNs limited [48]. Data—monthly prices/returns; firm characteristics/factors (Fama–French, anomalies, CRSP); fundamentals, technical/past-performance, macro, news/text and satellite imagery; US/world/Chinese equities [48][49]. Metrics—returns, Sharpe, MDD, R²/OOS R², p-values, MSE, RMSE, MAPE [48]. Denominator—the review searched 2015–2021; it lists 18/91 value-investing references and retains 60 final articles (~130 identified), so 2018–2023 prevalence is open [48]. Limits—publication/p-hacking bias, omitted factors, noise, look-ahead, costs, fading anomalies, herding and out-of-sample weakness [48][49].

Background only—Value/factor investing: objective—factor ranking/weighting, diversification, risk reduction and returns; data—fundamentals [88]. DL models/metrics: no prevalence or eligible 2018–2023 denominator is established [323–325]. Caveats: cyclicality, data mining/sample dependence, costs, liquidity, capacity and turnover [88].

Value/factor investing contributes to DL financial asset management through stock ranking/selection, factor-index or portfolio-weight construction, and return, price, trade-signal, or bubble prediction. A June 2023 quality-factor update describes selecting and weighting healthy-fundamental stocks subject to investor objectives and capacity, supporting diversification and risk/return management [90]; a 2024 guide (outside the window) describes capturing factor premiums for long-term excess return or a desired risk profile [50]. A 2026 review (also outside the window) reports medium/long-horizon selection and closer valuation/profitability–return alignment [78]. Hence no eligible 2018–2023 denominator or defensible “most common” DL-model ranking for value/factor investing is established here [113][78].

The out-of-window review reports primary inputs of P/E/P/B, EPS/ROA, profitability, growth and cash-flow measures, analyst ratings, sector/ownership variables, technical indicators, and financial news or analyst reports; fundamentals suit medium/long horizons and technicals short timing [78]. Reported contexts include U.S. and Chinese A-share markets [78]. Related comparison evidence characterizes portfolio management as return prediction, stock selection, signals and allocation using fundamentals, technicals, news, sector/industry and derived market data; price forecasting targets closing prices, returns, direction classes and bubbles using price/return, fundamental, technical, textual and derived inputs. LSTM is associated with price forecasting, but the evidence is not an eligible 2018–2023 prevalence estimate [78].

The denominator remains open: one survey covers 32 papers from 2011–2022, while the 2026 review covers 54 studies from 2014–2025 [113][78]. Its reported counts—RMSE 11, MAE 9, MAPE 7, Accuracy 19, Recall 10, F1 9, Sharpe 6—cannot be transferred to the requested window [78]. The 2023 source separates its June update from observations including December 2000–March 2023 and November 2002–March 2023 [90]. Caveats include hypothetical backtests and omitted fees, sector/investability/capacity, transaction costs, tracking error, factor correlation, regime dependence, multicollinearity, quarterly–daily timing, look-ahead risk, and overfitting [90][78].

Value/factor DL: stock sorting, latent/long–short factors, pricing-error minimization. A 2023 U.S. structural DNN maps firm characteristics (earnings surprise, book-to-market, zero trades) to factors and returns [60]. Monthly stock/test portfolios span 50 years; evaluation includes out-of-sample Sharpe = 2.49 and 3.00 (2012–2021) [60]. One study; denominator open; factor construction ≠ direct forecasting [60].

Value/factor investing (2018–19): objectives—factor/risk models, integration, ranking/returns [91][65]; models—PCA, RF/SVM, shallow NN; RNN uncommon [91]; inputs: macro/firm traits, P/B, momentum [91][65]. Evidence is partial, not a dedicated corpus.

Value/factor: predict/rank/select; NF-Score uses fundamentals+prices [68], DFN: 68 firm features [46]. Data: macro/fundamental/technical/sentiment/price [72]. Metrics: returns/α/SR/R²/RMSE/MAPE [46][77]; corpus/date scope open

An eligible 2023 study uses an augmented deep-factor model: hidden layers generate latent factors from high-dimensional firm characteristics, and an economic-guided loss minimizes pricing errors for cross-sectional returns and long–short weights [56]. It demonstrates a DL factor application, but one study supplies no prevalence denominator or modality taxonomy [56]. A 2020 AlphaPortfolio DRL working paper is an adjacent lead [56]; the factor-investing guide updated 17 July 2023 is non-exhaustive [93]. Later out-of-window examples mention Factor-GAN (LSTM/CNN), R²/RMSE, return/Sharpe/MDD, IC/alpha/Sortino/Calmar and costs; neither supports 2018–2023 prevalence [79][92].

2019 value/factor: ANN combined factors beyond OLS; no corpus prevalence; training noise overwhelmed signal [94].

V/factor: rank;NN; data;R²;prev?[95].

Value/factor DL targets factor/stock selection and portfolio construction [45]. Inputs: price data, financials, technical/fundamental, firm/regime variables [62][43]. Metrics: return, IR/ICIR, drawdown, turnover [45]. Biases: weight/liquidity, costs, survivorship/horizon; 18–23 denominator open [96][87]

Factor investing: US factor data (Jul 1963–Dec 2019); NN allocates long-only ETFs; 5% CVaR measures tail risk [67].

Algorithmic trading targets buy/sell, allocation, market making and execution; uses price, volume, LOB, text. Models: DQN/PPO, LSTM, Transformer, GNN; metrics: returns, Sharpe, MAE/MAPE, hit rate; 2018–23 prevalence open [54][98].

Algorithmic trading/price forecasting: signals/exec/HFT; price/return/direction/volatility; CNN/LSTM/GRU/DQN; price/tech/fund/text inputs [59]; 2018–23 DL metrics open; leakage/overfit/live-gap; sentiment qualified [57][74].

Algorithmic trading (2018–23): forecasts/signals and execution use prices/indicators/fundamentals/news/sentiment; 92% reviewed: single-output [63].

AT signals; PM weights; prices[66]

Algo trading: DRL/LSTM; returns [70].

Algorithmic trading: 2018–23 no denom.; MAPE/RMSE/MAE 9/6/2; hit rate9 [98]

Algorithmic trading: CNN/LSTM; mkt/news→price; acc/ret; 16–19 [99][100]

Algo trading: DL/DRL; denom open [101]


AT: DL/RL/Q; alt; A/P/R/F1; open[102]


Algorithmic trading: no ranking [103].

RL review:20 trade;7/27 forecast [104]

Portfolio management: price/text [61]

Algo trading: prices/text/graphs [47]

Value/factor evidence compares carry, value, trend and reversal portfolios; portfolio management sets weights for return/risk under drawdown [41][42][73]. Inputs: prices/returns, volatility, sentiment and scenarios [51][52]. A 2022 autoencoder used daily bid closes for 21 G10 pairs (2010–2020), while a 2023 Transformer/SHAP study allocated Chinese stocks [73][81]; forecasts may feed selection [53]. Illustrative: backtest, look-ahead and turnover limit inference [42][51][73].


Factor investing: DL timing 2023 [106]

Portfolio: RL leads; corpus open [107]

Value/factor: denominator open [109].

2018–23 portfolio: DL selection/weights [80]; inputs: prices, fundamentals, tech indicators, sentiment [58][75]

2023 NYSE FANG+ evidence uses adjusted closes and news polarity for rebalancing [84]; Sharpe, VaR/CVaR and MDD are reported [84][108][111]. No DL-only 2018–2023 denominator supports prevalence claims [110][112].

Price forecasting: 2018–2023; price/direction/risk; LSTM/GRU/CNN/Transformer; price/news; metrics open [55][64]

Value investing buys cheap shares[89]

Portfolio weights[44];prices[76];Transformer23[85];sentiment/crypto?[71]

Across 2018–2023 [49][56], value/factor investing links DL to asset management by learning nonlinear relations from firm characteristics and factors, then using forecasts to rank or select securities, generate or integrate factors, set portfolio allocations, and evaluate return and risk [48][72]. This makes the domain a bridge from DL modelling to investable decisions, including downside assessment at 5% CVaR [67], although publication and replication bias, transaction costs, changing factor behaviour, and out-of-sample deterioration when market noise overwhelms learned relations limit the evidence [48].

In 2023 [86], the interpretable Transformer study applied Transformers to asset allocation and portfolio selection [82]. Its attention-based sequence-to-sequence mechanism captures long-range dependencies and cross-asset interactions [85], while the associated Time2Vec–Transformer design fuses heterogeneous information for portfolio construction [83].

Online-source sentiment data functions as an alternative input by converting articles and social-media content into asset-aligned sentiment features: VADER and FinBERT add public or expert opinions to market variables for market-state classification and DL portfolio decisions [71][69][105]. It broadens analysis beyond price-only data, but production use requires collection and preprocessing pipelines and fine-grained sentiment for each asset rather than generic aggregation [71].

Cryptocurrency asset management should be included conditionally as an asset-class context: digital assets are treated as a distinct class, and crypto is connected to portfolio construction and hedging research [97]. To make it evidence for this report, a study within the stated publication window must show DL using crypto observations for portfolio-management decisions; otherwise, retain it as contextual scope rather than a domain finding [97].

## 3. Algorithmic trading: research status, 2018–2023

### Objectives and commonly used models

**Trading research turns information into actions**. Its main objectives include generating buy–sell signals, timing positions, exploiting statistical arbitrage, optimizing strategy parameters, and improving execution. Wang and Yan’s 2021 survey emphasizes forecasting and arbitrage, while the 2023 RL review separates algorithmic trading from portfolio management, order execution, and market making. [29][23]

**Two principal learning routes recur**. Supervised systems predict prices, directions, or trading labels, which a separate rule converts into positions. DRL systems instead learn position or execution actions from rewards. Recurrent networks and CNN–LSTM hybrids are common in the first route and often serve as state encoders in the second; DQN and actor–critic or policy-gradient methods learn decisions around those representations. [2]

| Trading task | Main objective | Common models | Primary inputs | Decisive evaluation |
|---|---|---|---|---|
| Forecast-based trading | Convert forecasts into positions | ANN, CNN, LSTM, GRU hybrids | Prices, indicators, selected news | Net return, Sharpe, MDD |
| Learned trading policy | Optimize sequential position decisions | DQN and other DRL | Market features, holdings, costs | Reward, net return, risk |
| Optimal execution | Complete an order at low cost | DQN variants; PPO–LSTM | Order books, remaining shares and time | Execution cost and benchmark price |
| Statistical arbitrage | Exploit relative-price relationships | CNN and recurrent systems | Paired or cross-asset market histories | Net profitability and risk |

**Execution is not another price forecast**. A manager instructed to buy a fixed number of shares within a deadline faces a constrained cost-minimization problem. The direction and total quantity are largely predetermined; the decisions concern timing and order size. This differs from a trading signal that decides whether the asset should be bought at all. [25]

**DQN can also optimize a subsystem**. In the 2022 NMC-BERT-LSTM-DQN-X study, DQN optimized parameters of a forecasting architecture, using forecasting performance as a reward. The overall system combined market-state modeling, Transformer-based representations, and LSTM-based dynamic historical windows. Thus, the presence of DQN does not necessarily mean the final buy–sell policy is learned directly end to end. [30]

### Data and representative findings

**Market histories dominate trading inputs**. Daily OHLCV supports lower-frequency strategies, while ticks and limit-order-book records support intraday prediction and execution. Technical indicators—including moving-average convergence divergence, relative strength index, Bollinger bands, and stochastic oscillators—summarize price and volume patterns. Selected systems add news, sentiment, or accounting information, particularly where the holding horizon permits slower-moving information to matter. [6]

**Fundamentals play a horizon-dependent role**. They are central to value investing but less directly aligned with very short-lived order-book opportunities. The AFM’s report, updated in 2023 from a 2022 snapshot, found that the surveyed Dutch proprietary firms mainly used order-book information rather than fundamentals, often with 100–1,000 features. Those firms relied heavily on supervised learning rather than reinforcement learning. [31]

**Academic emphasis and market practice differ**. Research publications prominently explore DRL and increasingly elaborate hybrid designs, whereas the AFM snapshot emphasizes supervised learning in its professional population. This is not a contradiction: publications describe proposed methods, while the firm survey describes reported deployment choices within one market segment. Complexity that is attractive experimentally may impose operational, monitoring, or simulation burdens in production. [23][31]

**The Moroccan study connects prediction and trading**. Published in 2021, it trained LSTM/GRU predictors using US and French market data and validated and tested the strategy on Moroccan equities. It retained 32 relatively liquid stocks from 76 available, reflecting discontinuous trading and liquidity concerns. The strategy used historical prices and forecast-based rules, with estimated brokerage fees deducted from each transaction. [18]

| Strategy or benchmark | Annualized return, March 2019–March 2021 |
|---|---:|
| Proposed LSTM/GRU strategy | 27.13% |
| Pharmaceutical-industry indices | 19.94% |
| Distributor-sector indices | 15.24% |
| Moroccan All Share Index | 0.43% |

**The result is economically meaningful but specific**. The strategy exceeded the broad index and the two sector comparisons shown, after the study’s estimated brokerage deductions. It did not exceed the Software & IT Services index during the COVID-19 period. That counterexample matters because a strategy’s success against a broad benchmark is not equivalent to dominating every sector or investment opportunity. [18]

**PPO–LSTM illustrates sequential execution research**. A June 2023 study trained a proximal policy optimization agent with an LSTM in a proprietary simulator built from historical level-3 Korea Stock Exchange data. It evaluated 50 stocks, execution horizons of 165–380 minutes, and dynamic target volumes, reporting improvement against volume-weighted average price, or VWAP. [25]

**The execution mechanism explains DRL’s appeal**. Submitting a large order immediately can move the market and create slippage. Splitting it into smaller orders creates sequential choices: trading more now reduces the remaining quantity but may increase immediate impact, while waiting preserves flexibility but leaves more to complete later. A recurrent state representation can summarize changing market conditions while the policy balances those consequences. [25]

**Computational feasibility constrains model selection**. The NMC-BERT-LSTM-DQN-X paper describes its recursive model’s increasing computational burden and the difficulty of collecting exogenous variables at high frequency, limiting its proposed application to daily trading. This provides a useful contrast with order-book models designed around short-horizon updates: “algorithmic” does not mean every model is suitable for high-frequency trading. [30]

### Evaluation and research judgment

**Trading needs both signal and strategy metrics**. RMSE, MAE, and MAPE evaluate continuous forecasts; accuracy, precision, recall, and F1 evaluate directional or trading labels. But accumulated and annualized returns, Sharpe or Sortino ratios, maximum drawdown, and win rate evaluate the strategy produced from those signals. The broader stock-market survey identifies returns as most common, with Sharpe and drawdown also widely used. [2]

**Execution requires task-specific economic measures**. A fixed-order execution agent should be assessed by execution cost, slippage, completion behavior, and comparison with an execution benchmark such as VWAP—not solely by a directional classification score. Conversely, a profitable directional strategy should not be assessed as though it were obligated to execute a fixed quantity.

**Costs create the link to tradability**. A small predictive advantage can disappear when every signal triggers spread payments, fees, and market impact. Trading frequency and position changes therefore connect forecast quality to net performance. DRL can incorporate these consequences in its reward, but that advantage depends on the training environment representing them credibly. [23]

**Realistic execution remains a demanding boundary**. The 2023 RL review observes that some execution experiments use relatively long windows, modest asset universes, or assumptions that do not capture substantial market impact. An agent that performs well under those conditions has not thereby established effectiveness for very large orders completed over much shorter windows. [23]

**The resulting judgment favors decision clarity**. Supervised forecasting remains a strong starting point when the target is well defined and the forecast-to-position rule is transparent. DRL becomes especially compelling when current actions affect later costs, inventory, or opportunities. The preference should change if matched, cost-inclusive out-of-sample comparisons show that a simpler forecasting-and-rule system produces better net outcomes.

**The trading takeaway is implementation-adjusted performance**: the relevant success is a useful action after costs and execution constraints, not an accurate signal in isolation.

**Additional documented evidence**

Algorithmic trading is an in-scope DL asset-management application: it extracts signals, forecasts returns or direction, selects actions and position weights, automates execution, and optimizes profit or risk-adjusted performance under risk and turnover constraints [116][117][124].

**Models.** A bounded 176-paper “Neural Network Trading” topic (literature through Q1 2020; review published 23 October 2024) reports 80 neural-network, 62 RL-related, 13 LSTM, 8 CNN and 7 RNN occurrences; its asset mentions are stocks 104, indices 61, commodities 14, currencies 11, bonds 3 and crypto 3 [126]. In-window examples use DRL and LSTM–RL [122][123]; LSTM supports temporal prediction and signal/weight generation [116][122]. No eligible window-wide ranking is established.

**Data/metrics.** Inputs include prices/returns, OHLCV, technical indicators and volume, order flow, limit-order-book data, news, social sentiment, fundamentals and multimodal features [116][122][123][124]. Reported portfolio measures are PnL/returns, annualized return, Sharpe, MDD and turnover; forecast measures include directional accuracy, RMSE, MAE, MAPE and Theil’s U (U1/U2). Theil’s benchmark, horizon and preferred direction are unspecified; accuracy has no eligible corpus-wide ranking [116][117][118][124][126].

**Evidence/caveats.** No eligible 2018–2023 denominator is established: an older, date-unresolved E-mini study citing 2011/2012 work used 10 accounts and 800 trajectories [117]; an ineligible one-paper 2026 Binance study used 61 cryptocurrencies during January 2022–July 2025 [116]; and a 2025 review reported 62 publications [74]. The 2024 review is not period-specific, while a market report supplies revenue—not research—evidence [118][126]. Nonstationarity, data leakage/look-ahead bias, survivorship bias, multiple testing/overfitting, hyperparameter sensitivity, transaction costs/slippage/market impact, liquidity and benchmark choice can make backtests fail live [123][74][124][127].

Algorithmic trading: automated orders; DL/DRL, Q-learning, CNN/RNN, hybrids; signals/prediction/execution; price, tech/fund/text data; accuracy/prec/rec/F1, returns/Sharpe; overfit/unstable/opaque; 2023 review:24 papers (2008–22) [99]. No eligible 2018–23 denominator: 27 exp. (1994–2019; MAPE/RMSE/MAE/hit-rate=9/6/2/9) + 1,567 scr./208 sel. (2015–24) [98][128]

AT:LSTM/CNN;market/news→price;47+/50 papers;50/21≠18–23[100]

Algorithmic trading (2023): DRL targets returns [129].

Algorithmic trading automates orders and monitors risk [130].

AT: long/short; models/data [131]; metrics open; 2025 [132].


Algorithmic trading: 27 papers; 20 traded; 7 forecast [104].

Algorithmic trading: LSTM=70.6%(2018–23); P&L; data/risk[63]

Algorithmic trading: orders/risk [119]; ANN/DRL, prices/news, accuracy/Sharpe/MDD [114][120]; open prevalence; OOS [120].

Algorithmic trading, 2018–2023: buy/sell and execution; RNN/LSTM, CNN, GNN, RL use prices, indicators, text, order books; returns, Sharpe, accuracy, MAE/RMSE recur; corpus open [47].

Algorithmic trading—signals;DRL;px/news;profit factor;risk[115]

Across 2018–2023, algorithmic trading demonstrates deep learning in asset management by converting historical and order-book data into price predictions, trading parameters, and automated buy/hold/sell decisions [63][125][121]. This links feature learning and reward optimization to profit seeking and faster or better execution, while weak accuracy, inadequate risk monitoring, technical failures, and market volatility can produce unintended trades and losses [125][118].

## 4. Portfolio management: research status, 2018–2023

### Objectives and commonly used models

**Portfolio research determines capital allocation**. Its central objectives are choosing asset weights, sizing positions, rebalancing through time, and balancing return against volatility, drawdown, or tail losses. A collection of individually attractive stocks is not automatically an attractive portfolio because their losses can occur together. [1]

**Two allocation routes organize the literature**. Predict-then-optimize systems first estimate returns, risks, or directions and then apply an allocation method. Direct-learning systems map market information to portfolio weights or reallocation actions, optimizing an investment-related objective more directly. Hegde, Kumar, and Singh’s 2018 study explicitly contrasted conventional risk/reward prediction followed by quadratic allocation with direct DDPG allocation. [27]

| Allocation route | Learned object | Typical DL role | Principal advantage | Main trade-off |
|---|---|---|---|---|
| Predict then optimize | Returns, directions, or risk | ANN, CNN, LSTM, GRU forecasts | Separates estimation and constraints | Forecast loss may misalign with portfolio value |
| Direct weight/policy learning | Allocation or rebalancing policy | Policy-gradient and actor–critic DRL | Targets sequential investment outcomes | Sensitive to reward and market simulation |

**Policy-based RL fits weight determination naturally**. The 2023 RL review identifies policy-based methods as the most widely applied RL family in portfolio management because a portfolio is a distribution of weights over assets. Actor–critic methods are also prominent. This is a statement about the portfolio-RL literature, not a claim that one algorithm leads every portfolio-management study. [23]

**DQN remains useful for discretized reallocation**. Its action-value formulation suits a finite set of trading or allocation choices. Continuous actor–critic methods such as DDPG instead avoid requiring every possible weight vector to be represented as a discrete action. Recurrent, graph, and attention modules can support either route by improving the state representation. [32]

### Data, weight determination, and representative research

**Historical returns remain the primary foundation**. Portfolio studies commonly use daily prices, returns, OHLCV, or closing prices across multiple assets. Cryptocurrency experiments also use hourly histories. Technical features are included in some systems, while others operate directly on returns or learned price–volume representations. [32]

**Additional inputs address different allocation needs**. Firm characteristics can inform expected returns; macroeconomic variables can characterize market conditions; industry and covariance information can inform diversification. These are distinct information types: an industry link is relational metadata, not a substitute for a balance sheet, and covariance measures joint return behavior rather than company fundamentals. [28][14]

| Study | Allocation mechanism | Inputs and universe | Decision setting | Evaluation emphasis |
|---|---|---|---|---|
| Hegde et al., 2018 | DDPG continuous allocation | Twenty-stock portfolio | Direct allocation | Return and Sortino |
| Lucarelli & Borrotti, 2020 | Multi-agent DQN variants | Four cryptocurrencies; hourly closes | Repeated reallocation | Net return and Sharpe-related rewards |
| GANr, 2020 | Scenario-informed portfolio learning | Daily returns; 408 S&P 500 components | Robust portfolio selection | Adverse-scenario resilience |
| R3L, 2023 | Actor–critic with GRU features | Four ETFs or four stocks, plus risk-free asset | Weekly weight adjustment | Return, volatility, Sharpe, Sortino, VaR |
| Mercury, 2023 | Joint screening and policy learning | China A-shares; covariance and industry links | Weights and investment proportion | Return and maximum drawdown |

**Compounding makes the task sequential**. A portfolio’s period return is a weighted combination of constituent returns, while wealth compounds across periods. Consequently, maximizing the sum of isolated attractive forecasts is not identical to maximizing terminal wealth. Yang’s 2023 formulation explicitly represents portfolio wealth as a continued product and treats allocation as a sequential policy. [32]

**Previous weights influence current decisions**. Rebalancing costs depend on how far the desired allocation differs from the existing allocation. A model that ignores holdings can repeatedly recommend attractive-looking weights while generating excessive trading. The 2023 RL review describes portfolio-vector memory and cost-sensitive reward designs intended to incorporate this dependence. [23]

**The 2018 DDPG study establishes the continuous-action rationale**. Hegde and colleagues simulated a twenty-stock portfolio and evaluated rate of return and Sortino ratio. Their reported benefit from a risk-aware objective illustrates that the financial objective—not merely the ability to output weights—can change the resulting portfolio. The study also identified stability challenges for existing DRL approaches. [27]

**Multi-agent DQN offers another decomposition**. Lucarelli and Borrotti’s 2020 system assigned local agents to Bitcoin, Litecoin, Ethereum, and XRP, with a global reward coordinating the portfolio. It used hourly price movements but considered closing prices as inputs. This modular design reduced the task into asset-level decisions linked by a portfolio objective, rather than treating each asset’s prediction as independently sufficient. [26]

**R3L combines temporal features and explicit risk**. The 2023 mean–VaR study used a GRU to represent daily market histories and an actor–critic system to choose weights. Its ETF universe contained SPY, QQQ, DIA, and IWM plus a risk-free asset; a separate stock universe contained ORCL, AAPL, TSLA, and GOOG plus a risk-free asset. Training used 2008–2018 data, with testing in 2019–2022, and the investment setting used weekly adjustments over one-year horizons. [21]

| ETF benchmark | R3L final portfolio value relative to benchmark |
|---|---:|
| Sell-and-hold | 19.51% higher |
| Random selection | 18.0% higher |
| Mean–variance model | 8.1% higher |
| Buy-and-hold | 7.9% higher |

**These comparisons measure final wealth** relative to each named benchmark, not annualized-return percentage-point differences. The paper separately reported a Sharpe ratio 18.0% higher than buy-and-hold. Keeping the 7.9% final-value comparison separate from the 18.0% Sharpe comparison preserves the economic meaning of each result. [21]

**Graph models target portfolio-wide context**. Mercury jointly trained screening, relationship modeling, and portfolio-generation modules on China A-share data, evaluating a 50-stock quantitative portfolio across 3,305 trading days. Its portfolio network produced both asset weights and an investment proportion, allowing exposure to rise or fall with assessed opportunities. Its reward combined portfolio return with negative maximum drawdown. [14]

**Generative models address scenario robustness**. GANr evaluated 408 S&P 500 components in recession and boom periods, using the recent year of daily returns for training. Its reported resilience against adverse scenarios, relative to CLSGAN and LASSO portfolios, illustrates a different objective from maximizing an average forecast score. The generator’s contribution was to the distribution of conditions under which the portfolio was learned. [7]

### Evaluation and research judgment

**Portfolio metrics must evaluate portfolio outcomes**. Accumulated return, annualized growth, volatility, Sharpe, Sortino, and maximum drawdown are principal measures. VaR and CVaR add tail-risk perspectives when those risks are part of the objective. Turnover and transaction costs explain whether an apparently superior allocation is practically implementable. [21][33]

**The chosen risk measure changes behavior**. Volatility penalizes both upside and downside variability; downside deviation focuses on unfavorable outcomes; drawdown evaluates the realized wealth path; and VaR or CVaR evaluates a specified loss tail. Optimizing one does not establish superiority on the others. The R3L study implemented mean–VaR optimization and proposed CVaR as an extension, so its reported results should not be described as CVaR-optimized portfolios. [21]

**Direct learning improves objective alignment** but does not eliminate estimation error. Blitz and colleagues’ 2023 review contrasts the common practice of minimizing return-prediction MSE with approaches directly maximizing portfolio risk-adjusted return. It also notes that portfolio-level targets reduce the number of effective training observations, making direct optimization statistically demanding. [28]

**Predict-then-optimize retains important advantages**. Separating forecasts from allocation makes it easier to inspect expected returns, impose portfolio constraints, and compare alternative risk models. Direct policies can model sequential costs and decisions more naturally, but their benefits should be demonstrated against that modular alternative under the same investment universe and cost assumptions.

**Scaling changes the problem materially**. The 2023 RL review observes that many studies construct portfolios from relatively small asset pools, whereas real markets contain thousands of securities. Asset relationships and action-space size therefore become central when moving from a four-asset experiment to a broad investment mandate. Graph representations and stock-screening modules address parts of this challenge, but they also introduce additional estimation and computational choices. [23]

**The portfolio takeaway is objective-consistent allocation**: prefer the design that produces superior cost-inclusive wealth and risk outcomes under the investor’s constraints, whether it learns weights directly or uses forecasts followed by optimization.

## 5. Price forecasting: research status, 2018–2023

### Objectives and commonly used models

**Forecasting research predicts several different quantities**. Price levels, returns, direction, volatility, and return distributions answer different financial questions. A model predicting tomorrow’s close is not performing the same task as one predicting the next five-minute return or next-period volatility. Timmermann’s 2018 review explicitly distinguishes forecasting the mean, variance, and probability distribution of asset returns. [34]

| Forecast target | Financial question | Common DL designs | Main data | Appropriate evaluation |
|---|---|---|---|---|
| Price level | What will the future price be? | ANN, LSTM, GRU, CNN hybrids | Prices and OHLCV | RMSE, MAE, MAPE, R² |
| Return | How large will the change be? | DNN, recurrent, graph models | Returns, characteristics, market features | RMSE, MAE, benchmark-relative fit |
| Direction | Will the asset rise or fall? | CNN, recurrent, attention hybrids | Prices, indicators, selected text | Accuracy, precision, recall, F1 |
| Volatility or distribution | How uncertain or severe are outcomes? | Recurrent hybrids; multimodal attention | Returns, price ranges, earnings information | Forecast losses and tail-risk evaluation |

**Recurrent models are the historical mainstay**. Jiang’s 2021 review reports RNN models as most frequently used in its stock-prediction literature, including LSTM, GRU, stacked and bidirectional recurrent designs, and CNN–LSTM hybrids. The broader asset-management review similarly identifies LSTM as especially common where time-series dependence is important. [12][1]

**Additional architectures expand the information set**. CNNs learn local patterns; autoencoders compress or filter representations; GANs support adversarial forecasting or scenario generation; GNNs incorporate company relationships; and Transformers support attention over market sequences or alternative data. These additions are most convincing when they address a specific information problem, rather than simply increasing model complexity. [22]

### Data, horizons, and representative comparisons

**Historical prices and volumes dominate**. Common inputs include closes, returns, daily OHLCV, index histories, ticks, and limit-order-book records. Technical indicators and price–volume transformations extend these histories. News, social-media sentiment, and earnings-call text, audio, or video appear in selected multimodal models. [6][22]

**Fundamentals are less frequent but relevant**. Their lower reporting frequency, publication lags, and revisions complicate alignment with daily or intraday targets. This helps explain their lower prominence in price-focused studies compared with factor investing; it does not imply that accounting or macroeconomic information lacks forecasting value. [2]

**Sampling interval and horizon must be separated**. A model observing data every three seconds may predict five minutes ahead; a daily model may use 42 past days to predict one or five future days. Observation frequency, look-back length, forecast horizon, and investment holding period are different design choices. Comparing models without separating them can obscure what each reported result means.

**Song and Choi provide a controlled neural comparison**. Their 2023 study forecast DAX, Dow Jones, and S&P 500 closing prices using CNN–LSTM, GRU–CNN, and recurrent ensembles, with RNN, LSTM, GRU, and WaveNet benchmarks. Look-back windows were five, 21, and 42 days, while forecast horizons were one and five days. [17]

**One configuration shows why rankings change**. The following results are from the study’s S&P 500 sample for 2019–2021, using a five-day look-back, open/high/low/volume inputs, and Adam optimization. Errors are on the study’s normalized target scale, so they are not index-point or monetary errors. [17]

| Model | One-day MSE | One-day MAE | Five-day MSE | Five-day MAE |
|---|---:|---:|---:|---:|
| Recurrent ensemble | 0.0003 | 0.0143 | 0.0009 | 0.0230 |
| GRU | 0.0049 | 0.0674 | 0.0015 | 0.0224 |
| CNN–LSTM | 0.0032 | 0.0544 | 0.1112 | 0.3303 |
| WaveNet | 0.0189 | 0.1235 | 0.4606 | 0.6762 |

**The horizon changes the architecture comparison**. CNN–LSTM outperformed GRU on both one-day measures in this configuration, but GRU performed better on both five-day measures. At the five-day horizon, the ensemble had lower MSE while GRU had lower MAE. Thus, even within one dataset and study, the preferred model depends on the horizon and the loss function—not just the architecture’s name.

**High-frequency research adds operational constraints**. The 2023 O-LGT study combined LSTM, GRU, and Transformer layers in an online model using 26 features from limit-order-book data. Its dataset covered 100 CSI Smallcap 500 stocks over 22 trading days in November 2021, sampled every three seconds, with a five-minute-ahead percentage-price-change target. [16]

**Reported speed is relevant but specific**. At the study’s target accuracy, O-LGT required 0.0579 milliseconds versus at least 2.21 milliseconds for the best reviewed comparison on the same computer. The reported times imply approximately 38 times the computational speed, calculated as 2.21 divided by 0.0579; the paper describes this approximately as 40 times. This is a model-computation comparison, not a measurement of complete trading-system latency. [16]

**Cross-asset studies broaden the evidence**. Mroua and Lamine’s 2023 LSTM study covered equity indices, US bond indices, and commodity indices using data from January 1998 through September 2020, with the first 80% of each series for training and the final 20% for testing. It reported lower RMSE and MAE than ARIMA for almost all compared assets, with natural gas as an explicit exception. [35]

**Point-volatility gains need separate risk assessment**. A 2023 GRU–GARCH preprint combined GRUs with standard GARCH, EGARCH, GJR-GARCH, and APARCH for the S&P 500, gold, and Bitcoin. It generally improved point-volatility forecasts but not necessarily VaR or Expected Shortfall forecasts at 5% and 1% tail-probability levels. Better estimation of typical volatility therefore did not automatically improve extreme-loss forecasts. [36]

### Evaluation, counterexamples, and research judgment

**Regression errors are the common starting point**. The 2022 stock-prediction survey identifies RMSE and MAPE as the most frequently used regression measures, followed by MAE and MSE. For movement classification, accuracy and F1 are most frequent, followed by precision, recall, and other class-sensitive measures. R² and forecast-comparison tests answer additional questions rather than replacing those errors. [22]

**A naïve forecast is a demanding baseline**. Persistent price or exchange-rate levels can make sophisticated models appear accurate even when simply repeating the last observation is better. The relevant question is not whether a predicted curve resembles the observed series, but whether its errors improve on a meaningful benchmark at the same forecast origin and horizon.

**The exchange-rate reproduction demonstrates this directly**. The 2022 forecast-evaluation study compared published and reproduced results for Autoformer and FiLM against a naïve forecast on an exchange-rate benchmark at a 720-step horizon. The errors below retain that dataset’s evaluation scale. [24]

| Forecast | MSE | MAE | Result basis |
|---|---:|---:|---|
| Naïve last-observation forecast | 0.817 | 0.694 | Benchmark |
| Autoformer, original result | 1.447 | 0.941 | Published result |
| Autoformer, rerun | 1.552 | 0.963 | Reproduced result |
| FiLM, original result | 0.727 | 0.669 | Published result |
| FiLM, reproduction range | 1.100–1.491 | 0.798–0.940 | Five reported trials |

**The supported conclusion is benchmark-specific**. The naïve forecast beat both Autoformer results, and all five FiLM reproduction trials performed worse than the naïve baseline despite FiLM’s originally reported advantage. This is evidence against those superiority claims in that setup, not against every Transformer or every financial forecasting application. It demonstrates why architecture novelty is weaker evidence than reproducible benchmark improvement.

**Nonstationarity explains part of the difficulty**. Financial predictive relationships can change as investors learn, competition alters opportunities, and market regimes shift. Timmermann’s 2018 review identifies low signal-to-noise ratios, persistent predictors, and unstable relationships as central obstacles. A model can therefore fit historical patterns without possessing a durable forecasting advantage. [34]

**Chronological evaluation addresses the actual question**. Fixed-origin evaluation trains up to one date and evaluates later observations; rolling-origin evaluation moves the forecast origin forward and can refit as new data arrive. The latter evaluates repeated forecasting decisions rather than one fortunate split. Randomly mixing future and past observations does not reproduce the information available to a forecaster at each historical date. [24]

**Forecast usefulness remains distinct from profitability**. A model can reduce price-level errors without identifying sufficiently large, correctly timed changes to cover trading costs. A direction model can correctly predict many small increases while missing a few large declines. Consequently, an asset-management application should connect forecasting metrics to the selection, trading, or allocation decision that will use the forecast. [1]

**The forecasting takeaway is benchmark-relative validity**: an architecture is useful when its improvement survives chronological testing, appropriate naïve comparisons, and the economic requirements of its intended application.

## 6. Performance evaluation metrics

**Evaluation must match the model’s output**. Portfolio measures describe wealth and risk; regression measures describe continuous-target fit or forecasting errors; classification measures describe label predictions. Theil’s U2 evaluates accuracy relative to a benchmark, while the Diebold–Mariano test evaluates whether two forecasts differ in expected loss. These measures answer complementary questions rather than forming one universal score.

### Portfolio performance metrics

**Portfolio calculations require consistent conventions**. Let \(V_0\) and \(V_T\) denote initial and final portfolio value, \(r_t\) the simple periodic portfolio return, \(T\) the number of observations, and \(Y\) the elapsed number of years. Values should include distributions consistently, and investment comparisons should identify whether returns are gross or net of costs. The wealth-ratio formulas below assume no external contributions or withdrawals, or an appropriately cash-flow-adjusted return series. [21]

| Metric | Textual calculation formula | Financial significance |
|---|---|---|
| Portfolio-accumulated returns | Divide final value minus initial value by initial value: \(V_T/V_0-1\); equivalently, multiply periodic gross returns and subtract one. | Total wealth gain or loss over the evaluation period. |
| Compound Annual Growth Rate — CAGR | Divide final value by initial value, raise the ratio to \(1/Y\), then subtract one. | Constant annual compound growth rate connecting initial and final wealth. |
| Standard Deviation of Returns | Subtract mean return from each periodic return, square deviations, average using the stated variance convention, then take the square root. | Total return variability; a volatility-based risk measure. |
| Sharpe ratio | Subtract the matching-period risk-free rate from mean portfolio return, then divide by return standard deviation. | Excess return per unit of total volatility. |
| Sortino Ratio | Subtract the stated target return from mean return, then divide by downside deviation relative to that target. | Return above target per unit of downside risk. |
| Value at Risk — VaR | For a stated horizon, take the loss distribution’s quantile at confidence level \(\alpha\). | Loss threshold exceeded with probability approximately \(1-\alpha\). |
| Conditional Value at Risk — cVaR/CVaR | Average the worst \(1-\alpha\) fraction of horizon losses, weighting scenarios appropriately. | Expected severity of losses in the selected tail; also called Expected Shortfall. |
| Maximum Drawdown — MDD | At each date, divide the decline from the previous running wealth peak by that peak; take the largest decline. | Worst realized peak-to-trough percentage loss. |

**The return and ratio definitions follow** the 2023 R3L study and the stock-market survey; the CAGR expression is the algebraic annualization of the initial-to-final wealth ratio. CVaR’s downside-tail interpretation is stated in the 2021 portfolio review and the 2022 asset-management review. [21][2][33][1]

**Compounding differs from averaging returns**. Kolari, Liu, and Pynnönen’s 2023 example starts with $200, loses 20%, and then gains 30%, ending at $208. The cumulative return is 4%, while the geometric average return per period is approximately 1.98%, not the arithmetic average of 5%. If those two periods are years, the same geometric calculation is CAGR. [37]

$$R_{\mathrm{cum}}=(1-0.20)(1+0.30)-1=0.04,\qquad g=\left[(1-0.20)(1+0.30)\right]^{1/2}-1\approx0.0198.$$

**Sharpe and Sortino measure different risks**. Sharpe uses total variability, while Sortino excludes favorable deviations from its downside-risk denominator. In the R3L study, the Sortino target is the risk-free rate; other applications can state a minimum acceptable return instead. For variable risk-free rates, the Sharpe calculation should consistently use the excess-return series. Neither ratio by itself describes the severity of rare losses. [21]

**Downside deviation needs a stated denominator**. A common convention averages squared shortfalls below the target over all observations, assigning zero shortfall to returns above the target, and then takes the square root. Using only below-target observations produces a different denominator. The convention should therefore remain consistent when comparing Sortino ratios. [37]

**Annualization must preserve the measurement period**. A daily volatility or Sharpe ratio is not directly comparable with an annual figure. The familiar square-root-of-frequency scaling relies on assumptions about return dependence and stability; it should not be applied mechanically to strongly serially dependent strategy returns. CAGR, meanwhile, is geometric growth and should not be substituted for the arithmetic mean in a standard Sharpe calculation.

**VaR is a threshold, not a maximum**. At 95% confidence, VaR marks a loss boundary associated with the worst 5% tail, but losses beyond it can be much larger. CVaR asks how severe losses are on average within that tail. For discrete scenarios, averaging the specified tail fraction can require partial weighting at the quantile boundary. [1]

**Tail risk and drawdown are distinct**. VaR and CVaR describe a horizon-specific loss distribution; MDD describes the worst decline along a realized wealth path. Drawdown depends on the sequence of gains and losses, including extended declines across multiple periods. A strategy can therefore have moderate one-period loss quantiles and still experience a substantial cumulative drawdown. [2]

**CVaR also has an optimization advantage**. The 2021 portfolio review characterizes it as a coherent downside-risk measure, whereas the R3L paper notes that VaR is not coherent. In practical terms, VaR does not generally provide the same diversification-consistent risk properties. Nevertheless, selecting CVaR as an objective still requires a credible estimate of the tail distribution. [33][21]

**Additional documented evidence**

| Entity | Metric category | Metric name | Calculation-formula description | Financial significance / what it measur… |
| --- | --- | --- | --- | --- |
| Compound Annual Growth Rate (CAGR) | CAGR belongs to the portfolio-performance metrics…[214] | The page uses the metric name “CAGR” and expands it as…[134] | The source reports a CAGR value and forecast interval…[201] | The page reports a CAGR of 30.1% for the global deep…[145] |
| Standard Deviation of Returns | Standard deviation of returns is an aggregate…[77] | The source uses the term standard deviation of returns.[226] | no evidence found | Standard deviation is presented as a volatility or…[225] |
| Sharpe ratio | Sharpe ratio belongs to the portfolio performance…[195] | The source uses the term Sharpe ratio.[226] | Sharpe ratio belongs to the portfolio performance…[183] | The Sharpe ratio is a measure of risk-adjusted returns.[188] |
| Sortino Ratio | no evidence found | The standard metric name is Sortino ratios.[159] | (Rp−Rf)/downside deviation; original target MAR[190] | The source characterizes Sortino ratio as one of the…[181] |
| Value at Risk (VaR) | Value at Risk (VaR) belongs to the portfolio…[277] | VaR is defined by the loss CDF as VaR1−p = inf{x \| Fₗ…[223] | VaR is defined by the loss CDF as VaR1−p = inf{x \| Fₗ…[223] | VaR measures a specified lower-tail probability of…[146] |
| Conditional Value at Risk (cVaR) | Value at Risk (VaR) belongs to the portfolio…[277] | VaR is defined by the loss CDF as VaR1−p = inf{x \| Fₗ…[223] | VaR is defined by the loss CDF as VaR1−p = inf{x \| Fₗ…[223] | VaR measures a specified lower-tail probability of…[146] |
| Maximum Drawdown (MDD) | MDD belongs to the portfolio-performance metrics…[150] | MDD measures the maximum peak-to-trough portfolio loss.[208] | no evidence found | Largest peak-to-trough loss [208] |

Portfolio-accumulated returns measure cumulative portfolio wealth over an investment horizon. A 2023 portfolio-management formulation represents terminal wealth as a product of period-return factors, \(P_H=P_0\prod_{t=1}^{H}r_t\), and discounted accumulated return as \(G=\sum_{t=1}^{H}\gamma^t r_t\); logarithms convert the product into a sum [144]. The measure therefore evaluates wealth generated by repeated asset-weight decisions and rewards and supports benchmark comparison [144][178].

| Category | Metric | Textual calculation formula | Financial significance |
|---|---|---|---|
| Portfolio performance | **Portfolio-accumulated returns** (also reported as accumulated, discounted accumulated, or cumulative portfolio returns) [144][178] | Compound the period-return factors through the evaluation horizon; the cited evidence also gives discounted accumulated return \(G=\sum\gamma^t r_t\). | Measures cumulative portfolio growth or wealth and the outcome of a portfolio policy; it can compare a DL strategy with a benchmark [144][178][191]. |
| Portfolio performance | **Sharpe ratio** | Excess portfolio return divided by portfolio-return standard deviation: \((E[r_p]-r_f)/\sigma_p\). One cited implementation uses \((PY-0.001)/Std(R_1,\ldots,R_T)\), with an annualized risk-free return of **0.001** [144][177]. | Measures annualized return adjusted for total volatility; the risk-free rate, return frequency, and annualization basis must be stated [144]. |
| Portfolio performance | **Sortino Ratio** | Excess portfolio return divided by downside standard deviation: \((E[r_p]-r_f)/\sigma_d\), where the cited convention uses the risk-free rate as the reference return [177]. | Measures downside-risk-adjusted profitability; unlike Sharpe, it penalizes downside dispersion rather than all return dispersion [177]. |
| Portfolio performance | **Maximum Drawdown (MDD)** | For a specified investment window, take the largest peak-to-trough decline, represented as \((PV-LV)/PV\), or equivalently \(\max_t[(C_{\max}(t)-C(t))/C_{\max}(t)]\) [144]. | Measures the worst observed portfolio decline and downside risk. It can also be imposed as a portfolio constraint, such as \(MDD(k)\le MDD\), when selecting weights [191]. |
| Portfolio performance | **Compound Annual Growth Rate (CAGR)** — percentage, investment interval \(n\) years [212] | **Formula:** \((EV/BV)^{1/n}-1\): divide ending value by beginning value, take the \(n\)th root, subtract 1, and multiply by 100 when reporting percent; assumes reinvested gains and steady compounding [210]. | **Measures:** annualized compounded growth for comparing investments or benchmarks. It smooths the return path and does not measure volatility or risk; transaction timing can also be discarded, so pair it with risk measures [212][197]. |
| Portfolio performance | **Standard Deviation of Returns** — return-unit scale, stated return frequency [212] | **Measurement description:** dispersion of periodic returns around the expected or mean return (the cited example uses annual returns); greater variation produces a higher value. State frequency and annualization for comparison; the sample/population denominator is not specified in the cited span [212]. | **Measures:** return volatility or variability and relative investment risk, complementing CAGR [212]. |

Return conventions materially affect comparisons: one source uses 100-trading-day reward windows and a 252-trading-day annualization basis [144], whereas another reports monthly rebalancing and monthly returns [178]. Higher values are generally interpreted as better for return and risk-adjusted measures, but not for MDD, where lower is preferable [144].

**Compound Annual Growth Rate (CAGR)** is identified as the portfolio-performance label “Ann Ret (CAGR)” [178]. The supplied span establishes its name and category but does not state its formula or a value, so those fields remain unspecified here rather than being inferred.

Additional portfolio evidence uses ensemble learning and subset resampling to determine weights under a maximum-drawdown constraint; its FF48 data contain stocks from **48 industries** listed on the NYSE, AMEX, and NASDAQ [191]. A separate allocation passage reports an Evolino-RNN ensemble as effective in portfolio management and suggests RNN for future asset-allocation research, while noting that its own tested model was HMM [178].

A supplied later Transformer example reports Sortino ratios **47%** and **28%** above buy-and-hold for equal- and value-weighted portfolios during the pandemic [177]. Because that study falls outside the requested 2018–2023 publication window, those performance figures are excluded from the eligible comparison; the cited formula is retained only as a timeless metric definition.

The deciding condition for comparing these metrics is consistent return frequency, annualization and, for downside measures, consistent target, confidence, horizon and tail definitions. The 2023 LSTM example used historical quotes and technical, fundamental and sector indicators to rank S&P 500 Consumer Staples stocks into long and short portfolios, rebalance weekly, and compare results with sector and market benchmarks; performance slowed during COVID-19 [181]. Thus, portfolio metrics evaluate realized strategy outcomes, not forecast error alone.

All rows below are assigned to **Portfolio Performance Metrics**.

Conventions: state return frequency, gross/net and compounding treatment, annualization (252 daily or 21 monthly trading days), risk-free/target return, confidence and horizon, tail, and drawdown window [206].

Illustratively, a DRL study reports accumulated returns of $33,960 ± $4,473 (baseline), $89,782 ± $18,980 (technical indicators), and $115,591 ± $17,721 (indicators plus news sentiment), averaged over five runs; test data gave $110,308 versus $66,949 with selling disabled during 2016–2018, with annual Sharpe 2.68 [179]. Continued learning on test data limits comparability [179]. Post-2023 market CAGR figures and the 2013 investment example are terminology context only, not eligible 2018–2023 asset-management evidence [134][145][147][201][202][204][205].

These are timeless metric conventions; empirical comparisons remain restricted to 2018–2023. The entries below belong to the **Portfolio Performance Metrics** category.

- **Compound Annual Growth Rate (CAGR)** — \(R_G=[\prod_{t=1}^{T}(1+R_t)]^{1/T}-1\). One implementation annualizes a total return as \(R_{\mathrm{ann}}=(1+R)^{1/y}-1\), where \(y=\mathrm{days}/365.25\); it rejects windows shorter than 30 days and returns −1 for a total loss [208][209]. CAGR measures annualized compounded or historical portfolio growth and evaluates growth produced by a DL-managed portfolio [207][208]. A survey lists CAGR as a performance criterion for an S&P 500 top-five portfolio study using LSTM, auto-encoding and smart indexing, although its study period is unspecified [155]; another source gives only the unabbreviated term [158].

- **Standard Deviation of Returns** — The evidence identifies it as annualized portfolio volatility; a daily implementation uses sample standard deviation with \(ddof=1\) and annualizes as \(\sigma_{\mathrm{daily}}\sqrt{252}\), whereas monthly annualization uses \(\sqrt{12}\). Treating upside and downside symmetrically is valid only under a normal-distribution assumption [207][208][209]. It measures return dispersion, volatility and total risk, and supplies the risk denominator in the Sharpe ratio; consequently, it evaluates risk in DL-managed portfolios [207].

- **Sharpe Ratio** — \(S=(R_p-R_f)/\sigma_p\): excess portfolio return over the risk-free rate divided by total portfolio volatility [208]. A daily implementation sets \(R_f=0\) and annualizes with \(\sqrt{252}\); monthly calculations use \(\sqrt{12}\) [207][209]. The ratio measures excess return per unit of total risk; a higher value indicates more return for each unit of total volatility and supports risk-adjusted evaluation of DL portfolios [207].

- **Sortino Ratio** — \( (R_p-MAR)/\sigma_d\), where \(MAR\) is the minimum acceptable return and \(\sigma_d\) is downside deviation; one implementation instead uses daily returns, \(R_f=0\), \(\sqrt{252}\), and \(\sigma_d=\sqrt{\operatorname{mean}[\min(r,0)^2]}\) [208][209]. It measures return per unit of downside risk, penalizing harmful shortfalls rather than all volatility, and evaluates downside-sensitive DL portfolio performance [207]. A 2025 RL-allocation source treats Sortino as a portfolio-weight reward, but that empirical context is outside the requested window [186].

- **Value at Risk (VaR)** — VaR is a specified loss quantile over a stated confidence level and horizon. The supplied parametric example uses 99% confidence and one day: \(-(\bar R-2.326\sigma_{\mathrm{daily}})\times\) portfolio value; it interprets the result as a 1% probability of exceeding the loss threshold, with a worked fixed-income example of €1,375,500 [208]. VaR measures potential portfolio loss and evaluates DL asset-management risk, but it does not describe losses beyond the threshold [208]. Another implementation note supplies no VaR formula, confidence level or horizon and mentions it only indirectly through CDaR [209].

- **Conditional Value at Risk (cVaR), also Expected Shortfall (CVaR)** — \(ES_\alpha=-E[R\mid R<VaR_\alpha]\); it measures expected loss in the tail beyond the VaR threshold. Under the cited normal 99% example, ES is approximately \(2.665\sigma\), compared with \(2.326\sigma\) for VaR [208]. Thus cVaR evaluates DL-portfolio tail risk rather than only a loss cutoff. A related implementation gives CDaR—the average of the worst \(\alpha=.05\) fraction, \(k=\lceil\alpha N\rceil\)—but does not provide portfolio cVaR; CDaR must not be substituted for cVaR [209].

- **Maximum Drawdown (MDD)** — Under the peak-to-trough convention, \(MDD=(P_{\mathrm{peak}}-P_{\mathrm{trough}})/P_{\mathrm{peak}}\); a €115 peak followed by a €94 trough gives 18.26% [208]. Equivalently, \(DD(d)=\Gamma(d)/\max_{\tau\le d}\Gamma(\tau)-1\), with MDD selecting the minimum drawdown; recovery is the first later date at which the peak is reached, otherwise it is undefined [209]. MDD measures the worst observed peak-to-trough decline and drawdown risk against which DL-portfolio outcomes and annualized returns can be evaluated [207][208].

Comparisons should disclose return frequency, simple versus compound returns, annualization factor, risk-free rate, MAR or target return, VaR confidence and horizon, tail and loss-sign conventions, and the drawdown window [208]. A related convention card states that beta is estimated by OLS regression on market returns but gives no forecast target or horizon [208]. The survey separately lists Recall and F1-score as performance criteria in financial classification studies; their purposes belong in the classification table rather than this portfolio table [155]. Empirical metric examples from the 2025 DRL source are excluded from the 2018–2023 synthesis [186].

A conditional-autoencoder asset-pricing study of the Korean stock market reported CAGR alongside standard deviation, Sharpe, MDD, and win rate for portfolios; its tables used monthly observations from January 2006–December 2020 to compare long–short strategies [135]. This is study-specific portfolio-evaluation evidence, not a prevalence claim. The deciding conditions are consistent return frequency and annualization, and whether interim cash flows make transaction timing material.

Portfolio/DL: CAGR=[(end/start)¹/ʸ−1]×100→ann. growth [215]; SD of returns=√[Σ(r−mean)²/n]→volatility [216]; Sharpe ratio=(Rp−Rf)/σ→reward/risk [136].

StdDev of returns:√(Σ(r−r̄)²/N)=vol[219]; Sharpe ratio:(R−Rf)/σ[188]; Sortino:mean/downside[218]; VaR:loss probability≠size[218]; MDD:peak–trough[218]

Portfolio: Standard Deviation of Returns: σp=σ√(1/N+ρ(N−1)/N) (equal-weight); volatility, annualize by frequency [474,328]. Sharpe ratio: excess return over risk-free rate ÷ volatility [224]. VaR: loss quantile at given confidence/horizon [474,59]. cVaR: weighted average of VaR and losses beyond VaR [138].

Std Dev of returns:disp./risk; Sharpe:excess/vol. [139]; Sortino:downside risk [225]; VaR:alternative risk; cVaR:ES only [141]; MDD:peak-trough loss [226]

Standard Deviation of Returns — SD of periodic returns×√periods/yr; dispersion [229]. Sharpe ratio — excess return/annualized SD; risk-adjusted return [194]. Sortino Ratio — (return−MAR)/downside deviation×√periods/yr; return/downside risk [228]. Conditional Value at Risk (cVaR) — 95% ES: mean at/below VaR cutoff (worst ~5%), 1-period [229]. Maximum Drawdown (MDD) — wealth/running peak−1; max peak-to-trough fall; open unrecovered [229].

Portfolio metrics: Standard Deviation of Returns—dispersion around mean/volatility [233]; Sharpe—return/volatility [234]; Sortino—excess return/downside deviation [234]; VaR—loss quantile by confidence/horizon [234]; cVaR—mean loss beyond VaR [232]; MDD—(trough−peak)/peak, worst peak-to-trough loss [233].

Portfolio: SD=return dispersion[193];Sharpe=excess(risk-free)/SD[235];VaR=conf.-horizon loss[235];cVaR=VaR+exceedances[235];MDD=peak–trough loss[193].

**Standard Deviation of Returns**—periodic-return SD (volatility/risk), annualized ×√N (√12 monthly; √252 daily) [198][236]; XGBoost(c) 12.53% vs market 15.86% (1973:01–2021:12) [165]. **Sharpe ratio**—(return−risk-free rate)/SD, annualized; return per total risk [198][163]; XGBoost(c) 1.80 vs market 0.47 (1973–2021) [165]; lower MSE need not improve Sharpe [161]. **Sortino Ratio**—return relative to downside SD (negative returns), often ×√252; return per downside risk [163]. **Conditional Value at Risk (cVaR)**—Expected Shortfall beyond VaR; daily returns, 99% confidence, σ=1 [164]. **Maximum Drawdown (MDD)**—maximum peak-to-trough loss; XGBoost(c) 15.70% vs market 54.36% (1973–2021) [165]. VaR/performance figures are hypothetical and unaudited [161].

**Standard Deviation of Returns**: √mean squared deviations from mean [240]; √time annualization is invalid for ordinary but valid for log returns [238]. Dispersion/volatility, not direction [240]. Normality: ≥30 returns ⇒ 68%/95% at 1/2 SD; non-normality, <30 or weighting can mislead [237].

Sharpe ratio—portfolio: expected/avg benchmark diff/SD; return/risk [242]. Serial corr./annualization and omitted corr. matter; DL use is generic [242].

Portfolio: Standard Deviation of Returns—√variance [148]; Sharpe ratio—excess/SD [96]; Sortino Ratio—excess/downside [243]; MDD—peak–trough loss [192].

P: SD√Var/vol.; VaR max loss@conf./horizon; cVaR tail mean loss>VaR [246]; MDD peak–trough [159]; Sortino (R−T)/DD, excess/downside; T match [244][245]

Portfolio: VaR is a loss quantile at confidence α; cVaR/expected shortfall is conditional mean loss beyond VaR [247][166][137][248]; definition only.

VaR: horizon/confidence loss quantile [220][221]; cVaR/ES: tail loss beyond VaR [220][221]; MDD: Maximum Drawdown [116]; MAE: mean absolute error [221].

VaR (Value at Risk) is a confidence/horizon loss quantile, not the tail maximum [133][249]. cVaR/Expected Shortfall averages losses beyond VaR [222].

VaR: loss quantile at confidence/horizon [223]; cVaR/ES: tail loss beyond VaR [223]; SD returns: annualized dispersion [140]; MDD: peak–trough loss [140].

VaR: max expected loss over horizon/confidence [149]; losses beyond its quantile are missed [149]. cVaR/ES: mean tail loss; 2024 source calls it ES [176].

Portfolio metrics: Value at Risk (VaR)=loss threshold at confidence/horizon; Conditional Value at Risk (cVaR/CVaR)=mean loss beyond VaR, tail risk [151]

- **Value at Risk (VaR)** — *portfolio-performance metric*: maximum potential loss over a stated horizon at a predetermined confidence/tolerance level (e.g., 5% or 1%); it gives one downside-risk figure and excludes losses beyond the threshold [152].
- **Conditional Value at Risk (cVaR; CVaR/Expected Shortfall)** — *portfolio-performance metric*: expected (average) loss conditional on exceeding VaR; report confidence, horizon, payoff/loss sign, and tail convention [152][167]. It measures tail-loss severity for DL portfolio-risk evaluation, complementing VaR [152].

cVaR (Conditional Value at Risk): portfolio metric; average worst α% of terminal wealth (α=1/5%), not loss—tail risk and NN-portfolio protection [67]; 2019 selection [67]. Standard deviation measures return dispersion; cost effects may be ambiguous [67]. Sharpe is annualized/out-of-sample [174]. VaR limits floor-breach probability, not loss size [189]. MDD (portfolio)=(trough−peak)/peak, the peak-to-trough loss—not frequency/recovery [175][150].

**CAGR.** The supplied card confirms the name and abbreviation but not a portfolio formula; its 33.0% figure is deep-learning-market growth for 2026–2035, not portfolio performance, and should not be transferred to portfolio CAGR. [203]

| Metric | Supported definition and purpose |
|---|---|
| **R-squared (R²)** | R² is the proportion of outcome variance explained by a regression model: \(R²=1-\mathrm{SSE}/\mathrm{SST}\), relative to a mean or constant benchmark [258][270]. Introductory definitions give a 0–1 scale (0 = no improvement; 1 = perfect fit), whereas forecast formulations can be negative, with lower bound −∞, when errors exceed the mean benchmark [270][257]. It measures fit, not correctness, causality, unbiasedness, or guaranteed out-of-sample performance; added predictors can inflate it, so adjusted R² is preferable when model sizes differ [271][258]. |
| **Root Mean Squared Error (RMSE)** | RMSE is \(\sqrt{(1/h)\sum(y-\hat y)^2}\): squared forecast errors are averaged over test horizon \(h\) and square-rooted. It measures error magnitude in the target’s units; lower values are better, and squaring makes it more sensitive to large errors than MAE [256][168]. Compare RMSE across models only for the same target variable and scale [143]. |
| **Mean Absolute Error (MAE)** | MAE is \((1/h)\sum|y-\hat y|\), the average absolute forecast error over horizon \(h\). It reports average error magnitude in target units, with lower values better [256][251]. Its linear, L1 treatment is less sensitive to outliers than RMSE, but metric choice remains dependent on the loss context and outlier pattern [142][259]. |
| **Mean Absolute Percentage Error (MAPE)** | MAPE is \((100/N)\sum|(A-F)/A|\), the average absolute percentage error [252][256]. One overview describes it as scale-independent [259], while a forecasting reference warns of scale sensitivity [256]. Zero actuals make it undefined (or Inf under default inclusion), near-zero denominators can produce extreme values, and meaningful-zero, asymmetry, and underforecast-bias conditions limit interpretation [252][259][256]. |

For cross-metric comparisons, report the target scale, forecast horizon, benchmark, loss function, denominator and zero handling; the cited material leaves any financial target, horizon, benchmark, and loss convention unspecified [270][252].

**Regression metrics.** **RMSE (Root Mean Squared Error)**: \(\sqrt{\text{mean}(error^2)}\); measures forecast-error magnitude, emphasizing large errors/outliers; lower is better for the same series [170][264]. **MAE (Mean Absolute Error)**: mean \(|error|\); remains in target units, weights errors equally, and is less outlier-sensitive [170][260]. **MAPE (Mean Absolute Percentage Error)**: mean \(|error/actual|\times100\); scale-relative, but zero actuals are undefined and near-zero denominators are unstable [262][264]. **Theil’s U2**: usually model RMSE versus a naive no-change RMSE (<1 is better, >1 worse) [263]; another convention uses root squared errors/root squared actuals (nearer 0 is better; unbounded) [264]. **Diebold–Mariano (DM) test** tests equal predictive loss; squared or absolute loss may be selected, with horizon/sample and covariance-stationarity assumptions [230][231].

**Classification metrics.** **Accuracy**: \((TP+TN)/\text{all}\), overall correctness; class imbalance can mislead. **Precision**: \(TP/(TP+FP)\), correctness among predicted positives. **Recall**: \(TP/(TP+FN)\), detection of actual positives. **F1 score**: harmonic mean of precision and recall, ranging from 0 to 1; useful under imbalance. Define the positive class, threshold, and averaging convention before comparison [261].

RMSE (Root Mean Squared Error): square root of mean squared error; penalizes large errors and stays in target units [265]. MAE (Mean Absolute Error): mean absolute forecast error in target units; lower is better, but scale-dependent [266][267]. MAPE (Mean Absolute Percentage Error): mean absolute error relative to actuals; zero/near-zero actuals may make it extreme [268]. Theil’s U2: second U statistic, a forecast-quality measure; benchmark convention unspecified [269]. Diebold–Mariano (DM) test: tests whether mean loss difference between two forecasts is zero; state loss/horizon; HAC h>1 [253].

The Diebold–Mariano (DM) test is a regression-forecast comparison, not a model-comparison, test: define the loss differential \(d_t=L(e_{1t})-L(e_{2t})\) and test \(H_0:E[d_t]=0\). State the loss function, forecast horizon \(h\), and serial-correlation treatment; short horizons and nested models require caution [254]. For classification, **Accuracy** is \((TP+TN)/(TP+TN+FP+FN)\) but can conceal minority-class failure [272]; **Precision** is \(TP/(TP+FP)\), **Recall** is \(TP/P\), and **F1 score** is the precision–recall harmonic mean [273][169]. Report the positive class, decision threshold, and macro/micro or class-wise averaging [169].

Classification metrics: Accuracy=(TP+TN)/(TP+TN+FP+FN), overall correctness; imbalance or unequal error costs can mislead [274]. Precision=TP/(TP+FP), correctness among predicted positives [187]; a source using reversed class labels writes TN/(TN+FN), so its notation must be retained [173]. Recall=TP/(TP+FN), actual-positive detection [274]. F1=2PR/(P+R), harmonic mean of precision (P) and recall (R) [274]. State the positive class, threshold, balance, averaging, and label convention; values change with threshold [274].

Accuracy: correct overall; Precision: correct predicted positives; Recall: actual positives found; F1: harmonic mean of P/R; imbalance matters[153][154]

Accuracy: correct; Precision: positive correctness; Recall: actual-positive detection; F1 score: harmonic P/R; imbalance/threshold caveat [166,602,219].

Precision: TP/(TP+FP), correct positive predictions [255]; Recall: TP/(TP+FN), actual-positive detection [275]; F1: harmonic mean of P/R [276].

Portfolio-performance entries below use timeless definitions, not new 2018–2023 empirical evidence. CAGR means Compound Annual Growth Rate; a DL portfolio study lists it as a criterion but gives no formula [61]. The 13.6% in [118] is projected 2026–2033 market growth, not portfolio performance. Standard Deviation of Returns uses \(s=\sqrt{\sum(R_i-\bar R)^2/(N-1)}\) to measure return volatility [79]. Sharpe ratio is \((\bar R-R_f)/s\): excess return per risk [64][160]. Value at Risk (VaR) is a confidence/horizon loss threshold; Conditional VaR (cVaR) is expected loss beyond it [180]. Maximum Drawdown (MDD) is the largest peak-to-trough decline [160][162]. State frequency, annualization, confidence, horizon, tail, and drawdown window.

Portfolio-performance category: **Portfolio-accumulated returns**—compound periodic returns over the window; cumulative growth [129]. **CAGR**—\((V_T/V_0)^{1/n}-1\), where \(n\) is years; annualized growth [48]. **Standard Deviation of Returns**—dispersion of periodic returns; volatility [129]. **Sharpe ratio**—(annualized return−risk-free rate)/annualized \(\sigma\); excess return per total risk [200]. **Sortino Ratio**—excess return/downside deviation below target; downside-risk-adjusted return [200]. **Value at Risk (VaR)**—loss quantile at stated confidence/horizon; potential-loss threshold [182]. **Conditional Value at Risk (cVaR)**—mean tail loss beyond VaR; expected extreme loss [48]. **Maximum Drawdown (MDD)**—largest peak-to-trough wealth decline; path-dependent downside risk [48].

Portfolio metrics: Portfolio-accumulated returns=total return [199]; Standard Deviation of Returns=risk [199]; Sharpe ratio=excess÷SD [199]; Sortino Ratio=excess÷downside SD [196]; VaR=loss at risk level/horizon [108]; cVaR=VaR-quantile/mean risk [109]; MDD=peak/trough loss [108]. VaR/CVaR: probability level needed [109].

R², RMSE, MAE and MAPE are regression; Accuracy, Precision, Recall and F1 are classification [184][278]. Portfolio-accumulated return: 130% over 252 trading days [102]; standard deviation is return variability around the mean [279]; Sharpe is used in portfolio optimization [77]; MDD is an aggregate portfolio metric [77]. VaR estimates potential loss; its 2025 source makes it convention-only, not 2018–2023 evidence [280].

Portfolio-accumulated returns evaluate a DL portfolio or trading policy by measuring accumulated wealth or cumulative growth and the profits or rewards generated over the investment period or episode; in portfolio-management backtesting, accumulated wealth is read alongside reward ratios, so higher accumulated returns generally indicate better performance [144][179].

CAGR evaluates a DL-managed portfolio by converting beginning and ending values into a steady annualized compounded return, CAGR = (Ending Value / Beginning Value)^(1 / n) − 1, assuming reinvestment; it supports comparison of multi-period growth but does not capture volatility and is primarily suited to long-term assessment [61][197][210][212][213].

Standard Deviation of Returns evaluates a DL portfolio by measuring the dispersion of periodic returns and therefore total volatility or risk, serving as the risk term in the Sharpe ratio; lower standard deviation indicates lower risk, but the measure treats upside and downside variation equally and can be limited when returns are non-normal [79][217][157][228][216].

The Sharpe ratio evaluates a DL strategy by relating mean excess portfolio return over the risk-free rate or benchmark differential to return standard deviation, thereby measuring excess return per unit of total risk; higher values support strategy comparison, but comparisons require a common measurement period and annualization, and the total-risk denominator can penalize positive spikes [218][211][241][239][228].

The Sortino Ratio evaluates a DL portfolio’s return per unit of downside risk: (Rp − Rf) divided by downside deviation, or excess return over a target or minimum acceptable return divided by downside deviation; higher values indicate better relative risk-adjusted performance, but the target must be held constant and historical Sortino values are less reliable for highly volatile investments [227][190][239][148].

Value at Risk (VaR) evaluates DL asset-management risk by setting a specified loss quantile over a stated confidence level and holding horizon, thereby indicating a potential downside threshold; it does not describe the size or severity of losses beyond that threshold, so it should not stand alone for tail-risk evaluation [151][250][166].

Conditional Value at Risk (cVaR) evaluates a DL portfolio by averaging losses once they lie beyond the VaR cutoff, measuring expected severity in the worst (1 − α)% tail; this provides a tail-risk and downside-control measure that is more informative about loss severity than a threshold alone [222][67][167].

Maximum Drawdown (MDD) evaluates a DL portfolio’s drawdown risk as the largest peak-to-trough loss, equivalently the minimum of DD(d) where DD(d)=Γ(d)/max_{τ≤d}Γ(τ)−1≤0; it complements return evaluation by exposing the worst decline, but does not show how often losses occur or how long recovery takes [209][191][207][175].

The portfolio-performance table uses separate named rows for Portfolio-accumulated returns and CAGR and gives each a prose formula and financial-significance interpretation: accumulated returns represent portfolio wealth or cumulative growth, whereas CAGR is (Ending Value / Beginning Value)^(1 / n) − 1 and expresses annualized compounded growth [144][156][197][210].

Value at Risk (VaR) is included as a portfolio-performance row and is described by a selected loss quantile over a stated confidence level and horizon; the displayed conventions include 95% for one period and 99% for one day [229][208].

Conditional Value at Risk (cVaR) is included as the portfolio tail-risk row, using a conditional average of losses beyond the VaR cutoff; its displayed convention is 95 percent for one period [67][229].

Comparisons should preserve the metric conventions: accumulated return reflects compounded wealth [144], CAGR assumes reinvested gains and annualizes growth [197][210], Standard Deviation of Returns measures return dispersion [185], and Sortino uses a risk-free or target return with downside deviation and a displayed √252 annualization factor [190][163]. VaR is shown at 95% for one period or 99% for one day and cVaR at 95 percent for one period; at that coverage, cVaR 95 percent versus VaR 95% percent has difference 0 and ratio 1, which compares coverage labels rather than loss magnitudes [229][208].

Within DL asset-management evaluation, a portfolio policy allocates weights to maximize accumulated wealth [144], accumulated return and CAGR report profitability [144][197], Standard Deviation of Returns reports dispersion and risk [185], Sharpe ratio reports return per total volatility [60], Sortino Ratio reports return per downside volatility [190], and VaR reports a potential-loss threshold at a chosen confidence and horizon [229].

cVaR evaluates DL portfolio tail risk by averaging losses beyond VaR and exposing expected tail-loss severity for downside control, whereas MDD evaluates drawdown risk through the worst peak-to-trough decline against which annualized return can be judged [222][167][191][207].

The detailed portfolio-performance table frames the metrics as evidence for evaluating portfolio and strategy outcomes and uses distinct name, formula-description, and financial-significance columns; its roster is Portfolio-accumulated returns, CAGR, Standard Deviation of Returns, Sharpe ratio, Sortino Ratio, VaR, cVaR, and MDD [144][197][185][60][190][229][67][191].

Portfolio-accumulated returns give cumulative wealth or profits in backtesting [144][179], whereas CAGR gives a smoothed annual compounded growth measure for comparing strategy performance over time [197][210].

VaR supplies a quantile loss threshold at a chosen confidence level and horizon [229][208], while cVaR averages losses beyond that threshold and captures their expected tail severity [222][67].

MDD receives an entity-specific portfolio-risk treatment: it measures the largest loss from a previous peak and evaluates drawdown exposure against which portfolio returns can be judged [191][207].

Portfolio-accumulated returns use compounded wealth [144], while CAGR uses beginning and ending values, reinvested gains, and annualized compounding [197][210]; these assumptions must be stated because the two measures summarize growth over an investment period rather than the same return path.

The portfolio table keeps Portfolio-accumulated returns and CAGR in distinct named rows: the former represents cumulative investment wealth, whereas the latter reports annualized compounded growth from beginning to ending value [144][197][210].

VaR evaluates a specified portfolio-loss threshold [208][247], cVaR evaluates the expected loss beyond that threshold and its tail severity [67][222], and MDD evaluates the largest peak-to-trough decline over the investment period [191].

Across the requested 2018–2023 review scope, Portfolio-accumulated returns connect DL asset-management applications to an observable portfolio outcome by reporting accumulated wealth or profits in backtesting [144][179].

Standard Deviation of Returns evaluates a DL portfolio as return dispersion and volatility, with higher variation indicating greater risk; it treats positive and negative variation symmetrically and can rely on a normality assumption that may not fit financial returns [185][228][216].

The Sharpe ratio evaluates DL strategy efficiency by relating excess return to total return risk, and higher ratios are preferred for comparison; its interpretation depends on the measurement period and annualization convention [136][171][228][242].

Sortino Ratio evaluates risk-adjusted return by dividing excess return over a risk-free or target return by downside deviation, so it focuses on harmful volatility rather than total variation; a common target is required for meaningful comparison [244][228][245].

Value at Risk (VaR) is assigned to the portfolio-performance risk category because it is a loss quantile over a holding period and measures potential portfolio loss, rather than forecast accuracy [223][250].

The VaR row uses the technically precise name Value at Risk (VaR), a quantile-based loss definition over a holding period, and a financial interpretation as potential portfolio loss [149][248][250].

In a cited 2019 deep-learning factor-investing application, cVaR was used at 5% CVaR with annual rebalancing [67]. Its principle is to average losses beyond VaR to measure tail-loss severity, making it a downside-risk criterion for evaluating the strategy [222][247][167].

Conditional Value at Risk (cVaR) is assigned to the portfolio-performance risk category and is also called Expected Shortfall; the table should retain that terminology while defining it as tail loss beyond VaR [172][247][223].

Maximum Drawdown (MDD) applies the peak-to-trough principle to portfolio risk: MDD is the minimum of DD(d), with DD(d)=Γ(d)/max_{τ≤d}Γ(τ)−1≤0, so the row exposes the largest decline and complements return measures in evaluating drawdown control [209][191][207].

### Regression forecasting metrics

**Forecast errors need a defined scale**. Let \(y_t\) be the observed target, \(\hat y_t\) its forecast, \(e_t=y_t-\hat y_t\), and \(n\) the number of forecast observations. For a price target, RMSE and MAE are in price units; for a return target, their units follow the return convention. Errors calculated after normalization should not be interpreted as monetary amounts or compared directly with errors on another scale. [38]

| Metric | Calculation or definition | Purpose and interpretation |
|---|---|---|
| R-squared — R² | One minus squared prediction errors divided by squared deviations of observations from their mean. | Measures fit relative to the mean benchmark; higher is better, and negative values indicate worse squared-error fit. |
| Root Mean Squared Error — RMSE | Square root of the mean of squared errors. | Measures error in target units, emphasizing large errors. |
| Mean Absolute Error — MAE | Mean of absolute errors. | Measures average error magnitude in target units with less outlier emphasis than RMSE. |
| Mean Absolute Percentage Error — MAPE | Mean absolute error divided observation-by-observation by actual values, multiplied by 100. | Measures relative percentage error for strictly positive targets. |
| Theil’s U2 | Benchmark-normalized forecast-error measure using a stated naïve forecast. | Tests whether accuracy improves on the benchmark: below 1 is better, 1 a tie, above 1 worse. |
| Diebold–Mariano — DM test | Statistical test of whether two forecasts have zero expected loss differential. | Assesses whether their predictive-accuracy difference is statistically significant under the selected loss. |

**R² can describe fit or prediction**. Applied to fitted training values, it summarizes in-sample fit; applied to held-out forecasts, it summarizes performance on new observations under its stated denominator. Out-of-sample financial studies also use benchmark-relative R² definitions, so the reference forecast must be identified. The standard mean-based form can be negative and has a maximum of one. [38][1]

**Higher fit need not mean better prediction**. Feng and colleagues’ factor-model discussion shows the economic version of this problem: regression R² can increase without reducing pricing alpha. This reinforces the need to assess predictive fit on held-out periods and to connect it to the financial objective. [4]

**RMSE and MAE emphasize different errors**. RMSE penalizes large mistakes more heavily because errors are squared before averaging. MAE weights error magnitudes linearly. On the same observations, MSE and RMSE produce identical rankings because taking a square root is monotonic; MAE can produce a different ranking, as the five-day ensemble-versus-GRU example demonstrated. [38]

**MAPE is poorly suited to returns**. Prices are often strictly positive, but returns can be zero or negative. Percentage errors also become unstable when actual values are near zero, and MAPE can favor low forecasts asymmetrically. Its scale-free appearance should therefore not override the suitability of the denominator for the target. [38]

**Theil’s U2 makes the benchmark explicit**. The table uses the naïve-benchmark interpretation, with one representing benchmark-level error. For financial price levels, a natural no-change benchmark repeats the latest observed value. Whether errors are calculated on levels or relative changes must be stated consistently; U2’s purpose is benchmark-relative accuracy, not an absolute percentage-error interpretation. The in-period forecasting literature lists Theil-type measures alongside other accuracy criteria. [22][39]

**The DM test compares paired losses**. For forecasts A and B, define a loss differential using the same dates and horizon. Squared-error or absolute-error loss can be used:

$$d_t=\ell(e_{A,t})-\ell(e_{B,t}),\qquad H_0:E[d_t]=0.$$

**Its significance depends on the loss definition**. A negative average differential favors A under the expression above, but statistical evidence also depends on the uncertainty around that average. The DM procedure uses a variance estimate that accounts for dependence in loss differentials, especially with overlapping multi-step forecasts. The 2019 ITISE paper and 2022 forecast-accuracy review describe this distinction between error magnitudes and a formal equal-accuracy test. [40][39]

**Statistical significance is not economic value**. Rejecting equal forecast accuracy does not establish profitable trading after costs. Failing to reject it does not prove the forecasts are identical. Furthermore, selecting the best result from many attempted models creates a separate multiple-testing problem, emphasized in Timmermann’s 2018 financial-forecasting review. [34]

**Additional documented evidence**

| Entity | Metric category | Metric name | Purpose description |
| --- | --- | --- | --- |
| R-squared (R²) | R-squared (R²) belongs to the regression forecasting…[317] | The source uses the metric notation “R²” and refers…[300] | R-squared (R²) belongs to the regression forecasting…[317] |
| Root Mean Squared Error (RMSE) | RMSE is used with MAPE to determine validation and…[297] | RMSE measures the square root of mean squared error…[257] | RMSE is used with MAPE to determine validation and…[297] |
| Mean Absolute Error (MAE) | MAE was employed by nine studies to compare model…[78] | MAE was employed by nine studies to compare model…[78] | MAE was employed by nine studies to compare model…[78] |
| Mean Absolute Percentage Error (MAPE) | MAPE was used in 7 review papers; it calculates the…[78] | MAPE was used in 7 review papers; it calculates the…[78] | MAPE was used in 7 review papers; it calculates the…[78] |
| Theil's U2 | Theil's U2 belongs to the regression forecasting… | The standard metric name is Theil's U2, written as U2.[263] | U2 is described as a measure of forecast quality…[269] |
| Diebold-Mariano (DM) test | no evidence found | The source names the Diebold-Mariano Test.[263] | no evidence found |

Across the rows, R-squared reports explained variance, RMSE and MAE report regression error, and MAPE reports relative percentage error [257][295][142]. Theil's U2 adds naive-benchmark comparison, while the DM test adds loss-differential comparison between forecasts [301][314].

**Regression-metric conventions**

Regression forecasting metrics evaluate continuous financial targets by comparing a prediction \(\hat y_t\) with the realized value \(y_t\) over a stated evaluation sample. Interpretation depends on the target, forecast horizon, scale, denominator, benchmark, and loss function. R² primarily describes fit or explained variation, whereas RMSE and MAE describe forecast-error magnitude; raw error values should not be compared across different target scales or datasets [306][304]. The older methodological evidence is used only for timeless metric definitions, not for 2018–2023 research-status claims; the financial illustration below is from 2022 [283][301]. The methodological source also draws on journal articles, books, statistical-computing documentation, supplementary materials, and data/code repositories [283].

| Category | Metric name | Purpose and interpretation |
|---|---|---|
| Regression forecasting | **R-squared (R²)**, also called the coefficient of determination | Under the conventional definition, R² compares the model’s squared residuals with those from a null model that predicts the mean, or summarizes the proportion of variation explained by the model. Higher values, with 1 representing perfect fit under that definition, indicate stronger fit on the same target and evaluation sample [306]. A factor-exposure source similarly states that values higher and closer to 1 indicate that the included factors explain more variation in strategy returns [302]. However, R² is not automatically a measure of out-of-sample forecast accuracy: its meaning depends on the training or test set, intercept/origin convention, and benchmark; it should therefore be reported with the exact definition and sample [306]. |
| Regression forecasting | **Root Mean Squared Error (RMSE)** | RMSE is the square root of mean squared prediction error, \(\sqrt{\frac{1}{n}\sum e_t^2}\). It remains in the response variable’s units and measures the magnitude of residuals; squaring gives large absolute errors more influence than they receive under MAE [304][306]. Because it is scale-dependent, comparisons require the same target definition, units, horizon, and evaluation sample [306][307]. |
| Regression forecasting | **Mean Absolute Error (MAE)** | MAE is the mean absolute prediction error, \(\frac{1}{n}\sum |e_t|\). It remains in the response variable’s units and measures average deviation between predicted and observed values. Relative to RMSE, it gives less additional influence to a single large error [304][306]. A 2022 financial forecasting study used MAE among its volatility-forecast evaluation measures [301]. |
| Regression forecasting | **Mean Absolute Percentage Error (MAPE)** | MAPE expresses absolute forecast distance relative to the realized target as a percentage. A 2022 financial study reported MAPE values between 53% and 55% and, under its cited convention, treated values above 50 as unreliable [301]. Because the realized target is the denominator, zero or near-zero targets require an explicit handling rule; MAPE values are not comparable unless that rule and the target scale are stated. |
| Regression forecasting | **Theil’s U2** | Theil’s inequality coefficient U2 is a forecast-quality measure relative to a naive benchmark. Values below 1 indicate higher predictive accuracy than the naive technique, whereas values above 1 suggest performance similar to the naive forecast [301]. The benchmark, forecast horizon, and loss convention must accompany the statistic. |

As a financial illustration rather than evidence of deep-learning superiority, a 2022 study forecast volatility for MSCI EFM Asia, Europe, Africa, and Latin America and the Caribbean using a rolling window of 805 trading days and an out-of-sample period from 1 January 2018 to 31 December 2019 (522 trading days). In that market order, its historical-variance comparison reported R² values of 0.011, 0.003, 0.001, and 0.005; MAE values of 0.007, 0.008, 0.010, and 0.009; MAPE values of 57.605%, 53.136%, 54.210%, and 55.081%; and U2 values of 1.032, 1.089, 1.043, and 1.053 [301]. The alternative BEKK–GARCH comparison reported U2 values of 0.808, 0.744, 0.721, and 0.789, all below 1, and reported MAPE values below 50 under that study’s convention [301]. The deciding condition is therefore the evaluation design: use R² for explicitly defined fit or explained variation, RMSE and MAE for errors on a common scale, MAPE only when its denominator is safe and specified, and U2 only with a named naive benchmark.

| Category | Metric | Purpose |
|---|---|---|
| Regression | **R-squared (R²)** | Explained variance, \(1-\)unexplained/total; 1 perfect, 0 none, negative poorer fit; not adequacy alone—inspect residuals. [309][257] |
| Regression | **RMSE** | Square root of MSE; 0 best, larger values mean greater error. [257] |
| Regression | **MAE** | Mean absolute error; 0 best; test-set outliers can impair it. [257] |
| Regression | **MAPE** | Relative percentage error; 0 best; requires positive actuals, so zero/near-zero denominators need care; may bias low forecasts. [257] |

A 2026 GNN example reports declining validation RMSE/MAE, but is outside the window and excluded. [300]


| Metric | Purpose and interpretation |
|---|---|
| **R-squared (R²)** | R-squared, or the coefficient of determination, measures target variance explained by predictors: \(R^2=1-\mathrm{SSE}/\mathrm{SST}\). The cited convention gives 1 as a perfect fit and 0 as no explained variation; in finance it can evaluate asset-pricing-model fit. High sample R² may reflect overfitting, so it does not establish out-of-sample accuracy by itself. [258] |
| **Root Mean Squared Error (RMSE)** | RMSE is \(\sqrt{h^{-1}\sum_{j=1}^{h}(y_{t+j}-\hat y_{t+j})^2}\) over the stated test horizon. It uses the target’s units, lower values are better, and squaring gives large errors greater weight than MAE. Compare it only for the same target and scale. [168][143][256] |
| **Mean Absolute Error (MAE)** | MAE is \(h^{-1}\sum_{j=1}^{h}|y_{t+j}-\hat y_{t+j}|\): the average error magnitude in target units. Lower is better, with linear rather than squared error weighting. Metric choice is distribution-dependent: RMSE is associated with Gaussian errors, whereas MAE is associated with Laplacian errors. [142][256] |
| **Mean Absolute Percentage Error (MAPE)** | MAPE averages \(|y-\hat y|/y\) across the forecast horizon and reports percentage error. Zero actuals make it undefined, near-zero actuals can produce extreme values, and it can favor underforecasting. One source describes it as scale-independent, while another warns that unit scaling changes the result; therefore, report units and denominator handling. [256][259] |
| **Diebold–Mariano (DM) test** | The DM test compares out-of-sample loss differences between two forecasts; its null is equal predictive accuracy. Under the cited orientation, a positive, statistically significant DM statistic favors the column forecast over the row forecast. The loss function, horizon, and comparison sample must be reported. [281] |

Illustrations are not universal benchmarks: R² fell from 0.9092 to 0.8899 (2.16%) between April and May and was 11.23% below its average on April 29; an EMA/S&P-index example reported MAE 453.52 (about 450 units), RMSE 582.24 (about 580), and MAPE 12.7% (about 13%). [258][251]

These regression measures evaluate DL price/return forecasts; portfolio returns require separate metrics.

| Category | Metric name | Purpose and convention |
|---|---|---|
| Regression forecasting | Root Mean Squared Error (RMSE) [252] | Square root of mean squared actual–forecast error; \(N\) is the observation count. It uses target units and weights large errors/outliers more heavily [170]. |
| Regression forecasting | Mean Absolute Error (MAE) [170] | Mean absolute actual–forecast error in target units; it is less sensitive to extremes than RMSE [310]. |
| Regression forecasting | Mean Absolute Percentage Error (MAPE) [252] | \(100/N\sum |(A-F)/A|\), a scale-relative percentage error. With `includezero`, zero actuals produce Inf; `omitzero` excludes them, while an all-zero dimension produces NaN [252]. |
| Regression forecasting | Theil’s U2 [285] | Compares a chosen forecast with a naïve random-walk (previous-period) forecast: U2<1 favors the chosen forecast; U2>1 favors the naïve forecast [285]. |

A 2023 example used DeepAR/DeepFactor forecasts from daily prices of 14 indices (1990–2019) in mean–variance portfolios: RMSE found no benchmark winner, MAE favored DeepAR, and MAPE selected parameters [299].

Regression: RMSE (Root Mean Squared Error)—√mean squared forecast error; target units; large errors weigh more [305]. MAE (Mean Absolute Error)—mean absolute error; equal weights, target units [311]. MAPE (Mean Absolute Percentage Error)—absolute error/actual averaged as %; undefined/unstable at zero or near zero [303]. Theil’s U2—RMSE/naïve no-change benchmark: <1 better, >1 worse; undefined if flat [263]. Diebold–Mariano (DM) test—tests significant difference in two forecast accuracies [263].

- **RMSE (Root Mean Squared Error):** √mean squared error; lower is better [265].
- **MAE (Mean Absolute Error):** mean absolute error in target units; lower is better [265].
- **MAPE (Mean Absolute Percentage Error):** \(|error|/actual×100\); zero or near-zero actuals invalidate or distort it [264][265].
- **Theil’s U2:** √Σerror²/√Σactual²; nearer 0 is better; unbounded [264].
- **Diebold–Mariano (DM) test:** compares forecast losses; H₀ is equal expected loss, assuming a stated loss and covariance-stationary differential [230].

RMSE: √MSE in target units; lower is better [255][293]. MAE: mean |error|; lower is better [76]. MAPE: mean % error; zero/near-zero values distort [292]. DM (Diebold-Mariano): loss differential vs benchmark; rejection indicates different accuracy [76].

Examples: MAE accompanies directional accuracy and profitability [289], covers 22 stocks and 9 ETFs [290], and evaluates GARCH–GRU volatility . An LSTM portfolio study reports MAE 0.01634, MSE 0.00047, and directional accuracy 95.8% over ten periods in 2021–H1 2022 for 50 EURO STOXX 50 stocks [296]; these are not prevalence counts.

Regression: Mean Absolute Error (MAE)—absolute error [291]; Mean Absolute Percentage Error (MAPE)—percentage error; near-zero actuals distort it [312]; Theil’s U2—forecast quality; <1 beats benchmark [269][294]; Diebold–Mariano (DM) test—compares loss differentials [177].


| Category | Metric | Purpose description |
|---|---|---|
| Regression forecasting | **R-squared (R²)** | The coefficient of determination measures the proportion of target variance accounted for by the predictions. In financial forecasting it indicates model fit or explanatory power, but not causality or guaranteed out-of-sample accuracy; adding predictors can increase R² without improving fit. [48][270][271] |
| Regression forecasting | **Root Mean Squared Error (RMSE)** | RMSE is the square root of the mean squared forecast error: \(\sqrt{\sum (y_i-\hat y_i)^2/n}\). It measures error magnitude in the target’s units and gives greater influence to large errors; lower values indicate smaller errors when target, scale, and horizon are comparable. [286] |
| Regression forecasting | **Mean Absolute Error (MAE)** | MAE averages absolute forecast errors, \(\sum|y_i-\hat y_i|/n\). It is an interpretable measure of typical forecast deviation and is used to compare financial price and return forecasts; lower values indicate smaller average errors. [62][288] |
| Regression forecasting | **Mean Absolute Percentage Error (MAPE)** | MAPE averages absolute errors relative to the observed target and multiplies by 100: \(100\sum |(y_i-\hat y_i)/y_i|/n\). It expresses forecast error as a percentage; zero or near-zero observed values make the denominator undefined or unstable, so the handling rule must be stated. [286][287] |
| Regression forecasting | **Theil’s U2** | Theil’s U2 is a benchmark-relative measure for comparing forecasting methods. The comparison benchmark, normalization, horizon, and preferred-value direction must be reported: the cited material establishes the method-comparison purpose but no universal U2 convention. Theil’s U (not explicitly U2) is described as closer to 0 for more accurate forecasts and 1 for poor performance. [316][287] |
| Regression forecasting | **Diebold–Mariano (DM) test** | The DM test compares two forecasts through the loss differential \(d_t=L(y_t,\hat y_{1t})-L(y_t,\hat y_{2t})\) and tests \(H_0:E[d_t]=0\), namely equal predictive accuracy. Report the forecast horizon, loss function or power (usually 1 or 2), alternative hypothesis, and long-run variance estimator; available implementations support autocorrelation or Bartlett estimators. [314][313] |

A financial-forecasting review identifies RMSE, MAE, and MAPE as widely used regression measures and notes that combining metrics can reduce dependence on any one measure’s sensitivity. [62] **Conclusion:** R² evaluates fit, RMSE/MAE/MAPE quantify forecast error, Theil’s U2 supports benchmark-relative comparison, and the DM test assesses whether two forecasts differ statistically. The deciding condition for cross-study comparison is consistent target, scale, horizon, benchmark, loss, and denominator conventions; a DM conclusion additionally depends on the declared hypothesis and significance rule, not on the statistic’s magnitude alone. [314][287]

R-squared (R²)—regression; coefficient of determination for test-set/return fit [77][282]. RMSE—regression; root-mean-square error; lower means smaller error [298]. MAE—regression error/loss; purpose unspecified [315].

R-squared (R²) evaluates a DL financial-asset-management regression forecast by measuring the proportion of target variance explained by its inputs (R² = 1 − SSE/SST); values nearer +1 indicate better fit [258][257]. A high value can still reflect in-sample overfitting rather than generalizable forecast quality, so R-squared should accompany other error measures [258].

RMSE evaluates a DL financial forecast by taking the square root of mean squared error, returning error to target units while giving large misses more weight [259][265]. For the same time series, lower RMSE is better (best 0; worst +∞), but scale dependence limits comparisons across variables [257][264].

MAE evaluates a DL financial forecast by averaging absolute actual–predicted differences in the original units [303][265]. It weights errors equally and is less affected by extremes than squared-error measures; lower MAE indicates better predictive performance [260][76].

MAPE evaluates a DL forecast by averaging absolute errors divided by actual values and expressing them as percentages, making relative accuracy intuitive [256][257]. It is undefined or unstable for zero or near-zero actuals because of the denominator, and its asymmetric penalty requires context [284][312].

Theil's U2 evaluates a DL forecast against a naive no-change benchmark by comparing the model's RMSE for relative changes with the benchmark's RMSE; U2 < 1 means better accuracy and U2 > 1 worse [263]. It is undefined when the naive forecast has zero period-to-period variation [263].

The regression-forecasting table includes R-squared, RMSE, MAE, MAPE, Theil's U2 and the DM test; the supplied definitions characterize R-squared by explained variance, RMSE by square-rooted squared error, MAPE by relative percentage error, U2 by naive-benchmark accuracy, and DM by competing forecast losses [257][295][142][301][314]. R-squared is preferable nearer 1, while U2 is interpreted against its naive benchmark [302][301].

For the requested 2018–2023 review, the DM test receives entity-specific treatment in the regression table: it compares the losses of a DL forecast and a competing forecast and tests equal predictive accuracy [313][314]. R-squared, RMSE, and MAE are separately treated as regression-evaluation measures for explained variance, squared-error magnitude, and absolute-error magnitude [257][142].

MAPE, Theil's U2, and the DM test form complementary regression-forecasting evaluation entries: MAPE gives relative percentage error, U2 compares forecast quality with a naive benchmark, and DM compares predictive losses between competing forecasts [257][301][314].

R-squared (R²) is calculated as 1 minus unexplained variation divided by total variation and measures the proportion of target variance predictable from the independent variables; values closer to 1 indicate better fit [308][257][258]. A high in-sample R² can overstate generalizability when insignificant terms inflate the measure and produce overfitting, so it should not be treated as sufficient evidence of out-of-sample forecasting quality [258].

Root Mean Squared Error (RMSE) is the square root of the mean squared difference between actual and forecast values, retains the target’s units, and emphasizes large errors [261][142][260]. Lower is better, with a best value of 0 and a worst value of +∞; because RMSE is sensitive to outliers, unusual large misses can dominate its evaluation [257][285].

### Classification forecasting metrics

**Classification requires an explicit positive class**. For illustration, let “positive” mean that an asset rises over the specified future horizon. True positives, or TP, are correctly predicted rises; false positives, FP, are predicted rises that do not occur; false negatives, FN, are actual rises the model misses; and true negatives, TN, are correctly predicted non-rises. Other applications can define the positive class as a buy signal, a decline, or another event, but the interpretation must follow that definition. [3]

| Metric | Calculation | Purpose and financial interpretation |
|---|---|---|
| Accuracy | \((TP+TN)/(TP+TN+FP+FN)\) | Overall fraction of correct classifications. |
| Precision | \(TP/(TP+FP)\) | Reliability of positive predictions; how often a predicted opportunity is genuine. |
| Recall | \(TP/(TP+FN)\) | Coverage of actual positives; how many genuine opportunities are detected. |
| F1 score | \(2TP/(2TP+FP+FN)\) | Harmonic balance of precision and recall. |

**Accuracy can reward the majority class**. If “hold” or “flat” dominates the labels, a classifier can achieve substantial overall accuracy while detecting few actionable events. Precision and recall reveal different failures: false opportunities reduce precision, while missed opportunities reduce recall. F1 summarizes their balance but does not incorporate the sizes of subsequent gains and losses. [6]

**Label construction changes the reported score**. The 2022 TSMC GRU–Attention study reported 79.2% accuracy with RSI transition labels based on 20–80 thresholds versus 76.4% with 30–70 thresholds. These are evaluations under different indicator-label definitions, not interchangeable measurements of profitable next-period price-direction prediction. The example shows why the class definition belongs beside any accuracy claim. [3]

**Multiclass reporting should preserve class differences**. Buy, hold, and sell predictions should be examined by class, with any macro or frequency-weighted averaging stated. Macro averaging gives equal weight to classes, while frequency weighting gives greater influence to common classes. Neither approach makes a classification score equivalent to a strategy’s return or risk.

**The complete evaluation combines complementary evidence**. Forecasting quality should be established against an appropriate benchmark; trading and allocation should then be evaluated through net wealth, risk-adjusted performance, drawdown, and relevant tail losses. Classification measures help explain the signal, while portfolio measures establish whether acting on it was financially useful. [22]

**The evidence is read consistently throughout**: publication dates fall within 2018–2023, while underlying market histories can begin earlier; identified preprints remain distinct from journal and conference publications. Model-prevalence statements describe their respective review populations, and numerical performance comparisons retain their original targets, horizons, and measurement bases. CAGR is the standard algebraic annualization, CVaR is presented as a tail-average calculation, and U2 uses the declared naïve-benchmark interpretation rather than attributing a specific denominator to papers reporting only “Theil U.” Percentage-to-ratio and computational-speed conversions are identified as calculations, while estimated trading fees remain study assumptions rather than measured live costs.

**The overall judgment is selective adoption**: DL’s contribution during 2018–2023 was the ability to represent complex financial information and connect it to investment decisions, with its value established by credible out-of-sample economic performance—not complexity alone.

## Appendix: Further Evidence

**Additional documented evidence**

2018–23 evidence: ANN 2020 [318], RNN 2023 [41], MDD 2022 [150], Transformer 2023 [83]; gaps; blocked URLs excluded.

2023 evidence [41]; grey literature [319].

## References

[1] <https://www.mdpi.com/2227-9091/10/4/84> Asset-management review, 2022; Asset-pricing literature and references, 2022; CNN mechanisms, 2022 review; Asset-management evidence, 2022; Portfolio-managemen…
[2] <https://link.springer.com/article/10.1007/s10462-022-10226-0> Stock-market DL survey, 2023; Autoencoder explanation, 2023 survey; DeepBreath example in the 2023 survey; Chart-based representation learning, 2018 applicatio…
[3] <https://doi.org/10.3390/app12031007> Neural-network mechanisms, 2022; Financial classification definitions, 2022; TSMC classification study, 2022
[4] <https://acfr.aut.ac.nz/__data/assets/pdf_file/0003/190641/FengPolsonXu_2018.pdf> Deep-factor study, 2018; Deep-factor experiment, 2018; Deep-factor interpretation, 2018; Fit-versus-pricing interpretation, 2018
[5] <https://doi.org/10.1142/s2424786318500317> Financial-pattern classification, 2018
[6] <https://www.mdpi.com/2076-3417/13/3/1956> Quantitative-finance overview, 2023; Trading-data overview, 2023; Forecasting-data overview, 2023; Classification and label imbalance, 2023
[7] <https://www.ijcai.org/proceedings/2020/0637.pdf> GANr architecture, 2020; Robust portfolio selection with GANr, 2020; GANr portfolio experiments, 2020
[8] <https://doi.org/10.48550/arxiv.1909.10578> PAGAN preprint, 2019
[9] <https://doi.org/10.1109/icassp40776.2020.9053276> CorrGAN, 2020
[10] <https://pubsonline.informs.org/doi/10.1287/mnsc.2023.4695> Deep learning in asset pricing, 2023; Adversarial asset pricing, 2023; Asset-pricing evaluation, 2023
[11] <https://cfe.columbia.edu/sites/default/files/content/20210910_Generative_Adversarial_Networks_Osterrieder_et_al.pdf> Financial time-series GAN discussion, 2021
[12] <https://ar5iv.labs.arxiv.org/html/2003.01859> Graph-based stock prediction review, 2021; GNN application described by Jiang, 2021; Stock-prediction review, 2021
[13] <https://doi.org/10.48550/arxiv.2306.15526> H-GAT preprint, 2023; H-GAT, 2023
[14] <https://doi.org/10.1109/access.2023.3298562> Mercury, 2023; Mercury’s relational inputs, 2023; Mercury design and experiment, 2023
[15] <https://arxiv.org/html/2111.15367v2> Financial GNN review, 2021; GNN scalability discussion, 2021
[16] <https://doi.org/10.3390/econometrics11020013> Recurrent-network explanation, 2023; GRU–LSTM comparison, 2023; Attention mechanisms in financial forecasting, 2023; O-LGT study, 2023; O-LGT computational com…
[17] <https://www.mdpi.com/2076-3417/13/7/4644> Sequence-model comparison, 2023; Index-forecasting study, 2023; One- and five-step results, 2023
[18] <https://link.springer.com/article/10.1186/s40537-021-00512-z> LSTM mechanisms, 2021; LSTM/GRU trading strategy, 2021; Cross-market LSTM/GRU strategy, 2021; Moroccan holdout results, 2021
[19] <https://link.springer.com/article/10.1007/s10614-021-10151-4> DeepValue, 2022
[20] <https://www.mdpi.com/2227-7390/10/4/566> CS-GRU, 2022; CS-GRU stock selection, 2022; CS-GRU results, 2022
[21] <https://doi.org/10.1109/access.2023.3259108> Risk-return portfolio learning, 2023; R3L design, 2023; R3L ETF results, 2023; Portfolio evaluation, 2023; Risk-objective distinction, 2023; Portfolio-return d…
[22] <https://arxiv.org/html/2212.12717v2> Transformer applications in the 2022 survey; Stock-prediction model inventory, 2022; Multimodal forecasting inventory, 2022; Forecasting-metric usage, 2022; St…
[23] <https://dl.acm.org/doi/10.1145/3582560> Relation-aware portfolio Transformer, 2023 review; Reinforcement learning for quantitative trading, 2023; Quantitative-trading review, 2023; Cost-sensitive tra…
[24] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9718476/> Forecast-evaluation study, 2022; Forecast-evaluation and reproduction study, 2022; Out-of-sample evaluation designs, 2022
[25] <https://doi.org/10.3390/fintech2030023> DQN explanation, 2023; Optimal execution formulation, 2023; PPO–LSTM execution study, 2023; Execution costs and order splitting, 2023
[26] <https://d-nb.info/122104463X/34> DQN variants in portfolio management, 2020; Multi-agent deep-Q portfolios, 2020; Multi-agent cryptocurrency portfolios, 2020
[27] <https://doi.org/10.1109/ssci.2018.8628791> Continuous-action portfolio learning, 2018; Direct continuous-action allocation, 2018; DDPG portfolio study, 2018
[28] <https://eprints.lancs.ac.uk/id/eprint/199224/1/BlitzHoogteijlingLohreMessow2023_SSRN.pdf> Quantitative asset-management review, 2023; Characteristic-based allocation review, 2023; Portfolio-objective comparison, 2023
[29] <https://www.aimspress.com/article/doi/10.3934/DSFE.2021019?viewType=HTML> Algorithmic-trading survey, 2021
[30] <https://dlnext.acm.org/doi/10.1145/3488378> Hybrid quantitative-trading architecture, 2022; Daily-versus-high-frequency boundary, 2022
[31] <https://www.afm.nl/~/profmedia/files/rapporten/2023/report-machine-learning-trading-algorithms.pdf> AFM trading-algorithm report, 2023; AFM report, 2023
[32] <https://nicelab.swufe.edu.cn/__local/2/95/A6/BC133ABE8BE1A1CF423D86D482B_4224FF97_325905.pdf> Portfolio decision architectures, 2023; Portfolio-data discussion, 2023; Portfolio wealth and policy formulation, 2023
[33] <https://doi.org/10.1109/access.2021.3058133> Portfolio-risk review, 2021; CVaR interpretation, 2021
[34] <https://www.annualreviews.org/content/journals/10.1146/annurev-financial-110217-022713> Financial forecasting review, 2018; Financial predictability assessment, 2018; Forecast comparison and data mining, 2018
[35] <https://www.nature.com/articles/s41599-023-02042-w> Cross-asset LSTM comparison, 2023
[36] <https://doi.org/10.48550/arxiv.2310.01063> GRU–GARCH preprint, 2023
[37] <https://doi.org/10.1007/978-3-031-48169-7_6> Compounding example, 2023; Lower-partial risk measures, 2023
[38] <https://doi.org/10.7717/peerj-cs.623> Regression-metric review, 2021; R² definition, 2021; Error-metric comparison, 2021; MAPE interpretation, 2021
[39] <https://doi.org/10.3390/jrfm15010001> Forecast-accuracy review, 2022; DM dependence discussion, 2022
[40] <https://itise.ugr.es/Springer2019/paper_283.pdf> DM loss comparison, 2019
[41] <https://dl.acm.org/doi/abs/10.1016/j.eswa.2023.120934>
[42] <https://www.frontiersin.org/journals/artificial-intelligence/articles/10.3389/frai.2023.1177702/pdf>
[43] <https://globalmarkets.statestreet.com/research/service/public/v1/article/insights/pdf/v2/c27cc8fe-457d-4116-92fc-5c0408cccde1/jfds_investable_and_interpretable_ml_for_equities.pdf>
[44] <https://arxiv.org/html/2206.03246>
[45] <https://dl.acm.org/doi/pdf/10.1145/3604237.3626848>
[46] <https://quantpedia.com/deep-learning-insights-for-factor-investing/>
[47] <https://arxiv.org/html/2212.12717v2>
[48] <https://www.mdpi.com/2227-9091/10/4/84>
[49] <https://www.cfainstitute.org/sites/default/files/-/media/documents/book/rf-lit-review/2020/rflr-artificial-intelligence-in-asset-management.pdf>
[50] <https://www.nepc.com/a-guide-to-factor-investing/>
[51] <https://lup.lub.lu.se/student-papers/record/9205798/file/9205806.pdf>
[52] <https://etd.ohiolink.edu/acprod/odb_etd/ws/send_file/send?accession=ouhonors1745245846160433&disposition=inline>
[53] <https://www.atlantis-press.com/article/125999546.pdf>
[54] <https://www.cureusjournals.com/articles/12720-deep-reinforcement-learning-for-stock-portfolio-and-crypto-trading-insights-and-trends-2020-2025>
[55] <https://www.sciencedirect.com/science/article/abs/pii/S0957417421002414>
[56] <https://www.cambridge.org/core/journals/journal-of-financial-and-quantitative-analysis/article/abs/deep-learning-in-characteristicssorted-factor-models/DD410814792E49E271957E8C87C1D763>
[57] <https://air.unimi.it/retrieve/8c51830b-465b-4527-8824-8e272955d246/1-s2.0-S1059056025008822-main.pdf>
[58] <https://link.springer.com/article/10.1057/s41260-021-00237-x>
[59] <https://www.scribd.com/document/713930330/Financial-applications-of-machine-learning-A-literature-review>
[60] <https://ar5iv.labs.arxiv.org/html/1805.01104>
[61] <https://doi.fyicenter.com/Download-Paper.php?ID=1003549>
[62] <https://projects.cs.uct.ac.za/honsproj/cgi-bin/view/2021/dhansay_pillay.zip/assets/res/CSC4019Z_COGSPMS_Literature_Review_PLLKIA010.pdf>
[63] <https://repositorio.unini.edu.mx/id/eprint/9698/1/A_Systematic_Survey_of_AI_Models_in_Financial_Market_Forecasting_for_Profitability_Analysis.pdf>
[64] <https://doi.org/10.48550/arxiv.1909.10578>
[65] <https://alphaarchitect.com/machine-learning-classification-methods-and-factor-investing/>
[66] <https://dl.acm.org/doi/10.1145/3582560>
[67] <https://cs.uwaterloo.ca/~paforsyt/Factor_NN.pdf>
[68] <https://doi.org/10.1016/j.frl.2019.101367>
[69] <https://www.mdpi.com/1911-8074/18/8/412>
[70] <https://link.springer.com/article/10.1007/s10462-022-10226-0>
[71] <https://arxiv.org/html/2309.16679>
[72] <http://www.mlfactor.com/factor.html>
[73] <https://www.jstage.jst.go.jp/article/jsaisigtwo/2022/FIN-028/2022_73/_pdf>
[74] <https://arxiv.org/html/2512.10913v1>
[75] <https://amslaurea.unibo.it/id/eprint/24245/1/federico_bertani_tesi.pdf>
[76] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10614642/>
[77] <https://rpc.cfainstitute.org/sites/default/files/docs/research-reports/rf_aiinassetmanagement_full-monograph_online.pdf>
[78] <https://link.springer.com/article/10.1007/s44163-026-01635-z>
[79] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11198854/>
[80] <https://www.sciencedirect.com/science/article/abs/pii/S0275531923000624>
[81] <https://www.cfrn.com.cn/dzqk/detail/12327.html>
[82] <https://www.sciencedirect.com/science/article/abs/pii/S1057521923003927>
[83] <https://dlnext.acm.org/doi/10.1016/j.eswa.2022.119020>
[84] <https://doi.org/10.1007/s00354-023-00231-4>
[85] <https://research-center.amundi.com/article/time-series-forecasting-transformer-models-and-application-asset-management>
[86] <https://www.semanticscholar.org/paper/e8ed8883c20e8b1f16b20d6fd941f7abccf01199>
[87] <https://acfr.aut.ac.nz/__data/assets/pdf_file/0008/573128/AlphaPortfolio-updated.pdf>
[88] <https://www.msci.com/documents/1296102/1336482/Foundations_of_Factor_Investing.pdf>
[89] <https://am.jpmorgan.com/us/en/asset-management/adv/resources/glossary-of-investment-terms/>
[90] <https://www.msci.com/documents/10199/4c5bd381-5b29-453e-ad73-6df24290a172>
[91] <https://doi.org/10.3390/risks10040084>
[92] <https://arxiv.org/html/2603.14288v2>
[93] <https://www.mlfactor.com/>
[94] <https://doi.org/10.3905/joi.2019.1.108>
[95] <https://arxiv.org/html/2108.02283v3>
[96] <https://doi.org/10.1002/rfe.1185>
[97] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12883517/>
[98] <https://link.springer.com/article/10.1007/s41060-021-00245-5>
[99] <https://doi.org/10.5815/ijeme.2023.06.05>
[100] <https://doi.org/10.24325/issn.2446-5763.v6i17p237-268>
[101] <https://link.springer.com/article/10.1016/j.jksuci.2024.102015>
[102] <https://www.mecs-press.org/ijeme/ijeme-v13-n6/IJEME-V13-N6-5.pdf>
[103] <https://doi.org/10.1016/j.techfore.2024.123746>
[104] <https://www.mdpi.com/2306-5729/4/3/110>
[105] <https://arxiv.org/abs/2309.16679>
[106] <https://ideas.repec.org/a/bla/acctfi/v63y2023i1p485-505.html>
[107] <https://ideas.repec.org/a/eme/jalpps/jal-07-2023-0119.html>
[108] <https://doi.org/10.1007/978-3-031-48169-7_6>
[109] <https://www.mdpi.com/1911-8074/12/1/48>
[110] <https://ar5iv.labs.arxiv.org/html/1906.07786>
[111] <https://doi.org/10.5267/j.ac.2022.12.003>
[112] <https://bura.brunel.ac.uk/bitstream/2438/27044/1/FullText.pdf>
[113] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9834034/>
[114] <https://link.springer.com/chapter/10.1007/978-3-031-33309-5_5?code=8af47931-41e7-45c8-a748-b1ff20bfb54d&error=cookies_not_supported>
[115] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12835427/>
[116] <https://arxiv.org/html/2509.04541v2>
[117] <https://www.cftc.gov/sites/default/files/idc/groups/public/%40economicanalysis/documents/file/oce_algorithmictradingstrateg.pdf>
[118] <https://www.grandviewresearch.com/industry-analysis/algorithmic-trading-market-report>
[119] <https://www.turing.ac.uk/sites/default/files/2019-04/artificial_intelligence_in_finance_-_turing_report_0.pdf>
[120] <https://www.kuntara.net/uploads/1/1/4/9/114945401/classification_bai_and_pukthuanthong_2020_v5_ed_20210107.pdf>
[121] <https://ar5iv.labs.arxiv.org/html/2106.00123>
[122] <https://www.mdpi.com/2227-7390/11/17/3626>
[123] <https://www.mdpi.com/2306-5729/6/11/119>
[124] <https://jklst.org/index.php/home/article/download/188/161>
[125] <https://www.afm.nl/~/profmedia/files/rapporten/2023/report-machine-learning-trading-algorithms.pdf>
[126] <https://arxiv.org/html/2411.05013v1>
[127] <https://medium.com/@alister.scott/best-machine-learning-models-for-algorithmic-trading-explained-simply-6c7fbe874fa5>
[128] <https://ideas.repec.org/a/prg/jnlaip/v2025y2025i3id276p506-534.html>
[129] <https://doi.org/10.61186/ijf.2023.364455.1369>
[130] <https://www.sec.gov/files/algo_trading_report_2020.pdf>
[131] <https://link.springer.com/article/10.1007/s43546-023-00618-x>
[132] <https://ijrpr.com/uploads/V6ISSUE1/IJRPR38107.pdf>
[133] <https://www.columbia.edu/~amm26/lecture%20files/VaR.pdf>
[134] <https://www.grandviewresearch.com/industry-analysis/artificial-intelligence-ai-market>
[135] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10389732/>
[136] <https://openstax.org/books/principles-finance/pages/15-4-applications-in-performance-measurement>
[137] <https://sas.uwaterloo.ca/~wang/papers/2020Liu-Wang-MOR.pdf>
[138] <https://pages.stern.nyu.edu/~adamodar/pdfiles/papers/VAR.pdf>
[139] <https://openfin.engineering.columbia.edu/sites/default/files/content/publications/ensemble.pdf>
[140] <https://escholarship.org/content/qt98f9410b/qt98f9410b.pdf>
[141] <https://d1b4gd4m8561gs.cloudfront.net/sites/default/files/publicaciones/archivos/borra520.pdf>
[142] <https://doi.org/10.5194/gmd-15-5481-2022>
[143] <https://www.sciencedirect.com/topics/engineering/root-mean-squared-error>
[144] <https://nicelab.swufe.edu.cn/__local/2/95/A6/BC133ABE8BE1A1CF423D86D482B_4224FF97_325905.pdf>
[145] <https://www.grandviewresearch.com/industry-analysis/deep-learning-market>
[146] <https://www.financialriskforecasting.com/files/Danielsson-Financial-Risk-Forecasting-Slides-5.pdf>
[147] <https://www.precedenceresearch.com/deep-learning-market>
[148] <https://rpc.cfainstitute.org/sites/default/files/-/media/documents/code/gips/the-sortino-ratio.pdf>
[149] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9006212/>
[150] <https://www.sciencedirect.com/science/article/abs/pii/S1544612321003500>
[151] <https://doi.org/10.4018/jgim.293288>
[152] <https://link.springer.com/article/10.1007/s00500-022-07161-1>
[153] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10550141/>
[154] <https://en.wikipedia.org/wiki/Precision_and_recall>
[155] <https://ar5iv.labs.arxiv.org/html/2002.05786>
[156] <https://www.mdpi.com/2076-3417/13/3/1956>
[157] <https://dl.acm.org/doi/full/10.1145/3768292.3770353>
[158] <https://www.theia.org/sites/default/files/2024-10/Investment%20Management%20in%20the%20UK%202023-2024.pdf>
[159] <https://arxiv.org/html/2412.15448v1>
[160] <https://link.springer.com/article/10.1007/s10462-024-11066-w>
[161] <https://alphaarchitect.com/machine-learning-financial-market-prediction-time-series-prediction-sklearn-keras/>
[162] <https://cdn.arenafi.org/papers/arxiv/2003.06365v1.pdf>
[163] <https://discovery.ucl.ac.uk/id/eprint/10190621/1/Medda_articolo2023FinalIzzoMedda.pdf>
[164] <https://medium.com/@abatrek059/deep-learning-portfolio-analysis-revisited-part-three-452ebc868a1a>
[165] <https://www.edhec.edu/sites/default/files/2026-02/Scientific%20paper.%20ssrn-4628462.pdf>
[166] <https://personal.ntu.edu.sg/nprivault/MH8331/expected_shortfall.pdf>
[167] <https://en.wikipedia.org/wiki/Expected_shortfall>
[168] <https://github.com/sktime/sktime/blob/main/sktime/performance%5Fmetrics/forecasting/%5Fmse.py>
[169] <https://cran.r-project.org/web/packages/metrica/vignettes/available_metrics_classification.html>
[170] <https://codefinity.com/courses/v2/df30ac7b-a08c-4606-b8ce-fb927b2f2df3/d4792817-3c9a-400d-80ef-74e86c90c28e/8befc179-318a-4ea7-ae59-c90a2de4d61b>
[171] <https://doi.org/10.1002/for.2999>
[172] <https://alcapitaladvisory.com/research/frameworks/cvar.html>
[173] <https://www.nber.org/system/files/working_papers/w26165/w26165.pdf>
[174] <https://repository.hkust.edu.hk/ir/bitstream/1783.1-143437/1/991013340350303412.pdf>
[175] <https://www.investopedia.com/terms/m/maximum-drawdown-mdd.asp>
[176] <https://link.springer.com/article/10.1186/s40854-023-00564-5>
[177] <https://arxiv.org/html/2505.01575v1>
[178] <https://doi.org/10.3390/jrfm12040168>
[179] <https://ar5iv.labs.arxiv.org/html/2208.07165>
[180] <https://www.nature.com/articles/s41598-025-26337-x>
[181] <https://doi.org/10.3390/ijfs11020057>
[182] <https://medium.com/@gwrx2005/digitalassetportfolioanalysis-an-open-source-framework-for-cryptocurrency-portfolio-management-and-8db85dbae51a>
[183] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8531567/>
[184] <https://www.mlfactor.com/valtune.html>
[185] <https://www.iimb.ac.in/sites/default/files/inline-files/Empirical%20Asset-Pricing-Machine-Learning.pdf>
[186] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12753089/>
[187] <https://bradleyboehmke.github.io/uc-bana-4080/book/24-classification-evaluation.html>
[188] <https://ar5iv.labs.arxiv.org/html/1802.04413>
[189] <https://business.columbia.edu/sites/default/files-efs/pubfiles/6358/drawdownminimization.pdf>
[190] <https://www.schwab.com/learn/story/using-sortino-ratio-to-gauge-downside-risk>
[191] <https://https-sage-cnpereading-com-443.webvpn1.xju.edu.cn/doi/10.3233/JIFS-179654>
[192] <https://gaurav-adarshi.medium.com/understanding-portfolio-performance-using-different-portfolio-metrics-bca92beb8b1b>
[193] <https://www.fe.training/free-resources/portfolio-management/how-to-monitor-portfolio-performance/>
[194] <https://www.hlhunt.org/uncategorized/risk-adjusted-performance-metrics-in-portfolio-management-hl-hunt-financial/>
[195] <https://doi.org/10.1111/joes.12532>
[196] <https://doi.org/10.3390/app12084067>
[197] <https://www.mycapitally.com/blog/measuring-investment-performance>
[198] <https://www.dol.gov/sites/dolgov/files/EBSA/researchers/analysis/retirement/volatility-metrics-for-mutual-funds.pdf>
[199] <https://doi.org/10.1609/aaai.v35i1.16095>
[200] <https://doi.org/10.4108/eai.2-6-2023.2334655>
[201] <https://www.persistencemarketresearch.com/market-research/deep-learning-market.asp>
[202] <https://www.rootsanalysis.com/reports/deep-learning-in-drug-discovery-market/156.html>
[203] <https://www.marketresearchfuture.com/reports/deep-learning-market-6058>
[204] <https://www.financialplanningassociation.org/article/journal/JUN13-intuitive-examination-downside-risk>
[205] <https://www.strategyand.pwc.com/de/en/industries/financial-services/asset-management.html>
[206] <https://www.pfolio.io/help/the-metrics-we-use>
[207] <https://github.com/joellewis/finance_skills/blob/main/plugins/wealth-management/skills/performance-metrics/SKILL.md>
[208] <https://docenti.unimc.it/mihaela.nicolau/teaching/2025/33135/files/portfolio-performance-evaluation>
[209] <https://github.com/disin7c9/asset-management/blob/main/MATH.md>
[210] <https://www.investopedia.com/terms/c/cagr.asp>
[211] <https://portfoliometrics.net/blog/risk-adjusted-metrics>
[212] <https://www.investopedia.com/investing/compound-annual-growth-rate-what-you-should-know/>
[213] <https://bankofbaroda.bank.in/banking-mantra/investment/articles/what-is-cagr>
[214] <https://www.etf.com/sections/etfcom-analysis/growth-rates-etf-performance-math>
[215] <https://seekingalpha.com/article/4516791-compound-annual-growth-rate-cagr>
[216] <https://study.com/academy/lesson/video/standard-deviation-of-returns-investment-volatility.html>
[217] <https://rpc.cfainstitute.org/sites/default/files/-/media/documents/code/gips/sharpe-ratio-and-the-information-ratio.pdf>
[218] <https://www.gilgamath.com/pdfs/a_short_sharpe_course.pdf>
[219] <https://study.com/academy/lesson/standard-deviation-of-returns-investment-volatility.html>
[220] <https://faculty.washington.edu/ezivot/econ589/cha19-riskmanagement.pdf>
[221] <https://public.econ.duke.edu/~ap172/Patton_Ziegel_Chen_JoE_2019.pdf>
[222] <https://www.garp.org/hubfs/Whitepapers/a1Z1W0000054xEpUAI.pdf>
[223] <https://www.math.ttu.edu/~atrindad/stat6351/lec9.pdf>
[224] <https://www.blackwellpublishing.com/content/bpl_images/content_store/sample_chapter/9780631227090/Allen_C01.pdf>
[225] <https://autodiscover.bps.go.id/chap/link/100626/L46H847421/the_sortino-framework_for-constructing_portfolios__focusing_on-desired__target__returntm_to__optimize-upside__potential-relative-to-downside_risk-by-frank_a_sortino__2009__11-09.pdf>
[226] <https://doi.org/10.1017/s0021900200014108>
[227] <https://www.recipeinvesting.com/sortino-ratio/>
[228] <https://www.longspeakadvisory.com/blog/what-is-the-sortino-ratio>
[229] <https://www.smartretirecalc.com/methodology/backtesting/risk-analytics>
[230] <https://thesis.eur.nl/pub/62056/Thesis_Msc_Final_568620.pdf>
[231] <https://stats.stackexchange.com/questions/553426/meaning-of-diebold-mariano-dm-test-for-other-accuracy-measures-mda-r2>
[232] <https://medium.com/@simonleung5jobs/risk-management-in-financial-portfolio-710e270bf0e1>
[233] <https://ryanoconnellfinance.com/maximum-drawdown/>
[234] <https://interactiveadvisors.com/learn-more/performance-metrics>
[235] <https://blog.quantinsti.com/performance-metrics-risk-metrics-optimization/>
[236] <https://admainnew.morningstar.com/directhelp/Methodology_StDev_Sharpe.pdf>
[237] <https://rpc.cfainstitute.org/research/cfa-digest/2015/07/why-do-we-abuse-misuse-and-confuse-standard-deviation-digest-summary>
[238] <https://rpc.cfainstitute.org/en/research/cfa-digest/2013/11/whats-wrong-with-multiplying-by-the-square-root-of-twelve-digest-summary>
[239] <https://www.mfdf.org/docs/default-source/default-document-library/publications/white-papers/measuringrisk.pdf?sfvrsn=d00b8398_2>
[240] <https://diefondsplattform.de/fileadmin/webinare/14247/2016-12-Amundi-Volatility-Academy.pdf>
[241] <https://stanford.edu/~wfsharpe/art/sr/sr.htm>
[242] <https://web.stanford.edu/~wfsharpe/art/sr/sr.htm>
[243] <https://en.heth.ink/QuantStat/>
[244] <https://www.investopedia.com/terms/s/sortinoratio.asp>
[245] <https://www.ecassets.com/learn/sortino-ratio>
[246] <https://blog.quantinsti.com/standard-deviation/>
[247] <https://faculty.washington.edu/ezivot/econ589/me20-1-4.pdf>
[248] <https://ar5iv.labs.arxiv.org/html/cond-mat/0203558>
[249] <https://www.rba.gov.au/publications/rdp/1997/9708/value-at-risk.html>
[250] <https://www.math-it.org/Publikationen/ValueAtRisk.pdf>
[251] <https://openstax.org/books/principles-data-science/pages/5-4-forecast-evaluation-methods>
[252] <https://docs.octave.org/latest/Forecasting-Metrics.html>
[253] <https://metricgate.com/docs/diebold-mariano-forecast/>
[254] <https://www.lem.sssup.it/phd/documents/Lesson19.pdf>
[255] <https://scikit-learn.org/stable/modules/model_evaluation.html>
[256] <https://openforecast.org/adam/errorMeasures.html>
[257] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8279135/>
[258] <https://arize.com/blog-course/r-squared-understanding-the-coefficient-of-determination/>
[259] <https://developer.nvidia.com/blog/a-comprehensive-overview-of-regression-evaluation-metrics/>
[260] <https://www.yvonnebadulescu.com/post/which-forecast-accuracy-measures-should-you-use-and-when-does-it-actually-matter>
[261] <https://finsrise.com/learn/cfa-level-2/cfa-level-ii-exam/big-data-projects/model-training-and-performance-evaluation>
[262] <https://www.openlayer.com/blog/mape-mean-absolute-percentage-error>
[263] <https://metricgate.com/docs/theil-u-forecast-accuracy/>
[264] <https://www.econstor.eu/bitstream/10419/173726/1/wp-nb-rm-2017-06.pdf>
[265] <https://www.jedox.com/en/blog/error-metrics-how-to-evaluate-forecasts/>
[266] <https://sktime-backup.readthedocs.io/en/stable/api_reference/auto_generated/sktime.performance_metrics.forecasting.MeanAbsoluteError.html>
[267] <https://link.springer.com/article/10.1007/s10618-022-00894-5>
[268] <https://doi.org/10.1016/j.ijforecast.2015.12.003>
[269] <https://www.statisticshowto.com/u-statistic-theils/>
[270] <https://cscu.cornell.edu/wp-content/uploads/regfit.pdf>
[271] <https://www.casrai.org/guides/regression-analysis>
[272] <https://dictionaryofml.org/terms/accuracy.html>
[273] <https://doi.org/10.1049/ic.2011.0016>
[274] <https://developers.google.com/machine-learning/crash-course/classification/accuracy-precision-recall>
[275] <https://scikit-learn.org/stable/modules/generated/sklearn.metrics.recall_score.html>
[276] <https://scikit-learn.org/stable/modules/generated/sklearn.metrics.f1_score.html>
[277] <https://doi.org/10.21511/imfi.20(4).2023.09>
[278] <https://vplevris.net/pdf_files/publications/C_50.pdf>
[279] <https://investor.vanguard.com/investor-resources-education/portfolio-management/performance-details>
[280] <https://www.linkedin.com/pulse/understanding-regression-finance-powerful-tool-decision-ayushi-patra-qefhe>
[281] <https://arxiv.org/html/2511.18578v1>
[282] <https://dspace.mit.edu/bitstream/handle/1721.1/164095/Deep-learning%20models%20for%20forecasting%20financial%20risk%20premia%20and%20their%20interpretations.pdf?sequence=2&isAllowed=y>
[283] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5570302/>
[284] <https://en.wikipedia.org/wiki/Mean_absolute_percentage_error>
[285] <https://dialnet.unirioja.es/descarga/articulo/4744242.pdf>
[286] <https://doi.org/10.1186/s11782-020-00082-6>
[287] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8941655/>
[288] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9283061/>
[289] <https://doi.org/10.1016/j.eswa.2023.119854>
[290] <https://www.tandfonline.com/doi/full/10.1080/14697688.2023.2299466>
[291] <https://link.springer.com/article/10.1007/s10614-024-10702-5>
[292] <https://www.vexpower.com/brief/mean-absolute-percentage-error>
[293] <https://doi.org/10.46254/ev01.20230037>
[294] <https://stats.stackexchange.com/questions/345178/interpretation-of-theils-u2-statistic-forecasting-methods-and-applications>
[295] <https://ejournal.pancawidya.or.id/index.php/galaksi/article/download/41/31>
[296] <https://doi.org/10.4995/bmt2023.2023.16513>
[297] <https://link.springer.com/article/10.1186/s40537-022-00597-0>
[298] <https://www.frontiersin.org/journals/earth-science/articles/10.3389/feart.2023.1087385/full>
[299] <https://fsc.stevens.edu/forecasting-time-series-in-portfolio-management/>
[300] <https://pmc.ncbi.nlm.nih.gov/articles/PMC13127960/>
[301] <https://doi.org/10.1080/23322039.2022.2114163>
[302] <https://meketa.com/wp-content/uploads/2020/05/Factor-Exposure-Analysis.pdf>
[303] <https://auto.gluon.ai/stable/tutorials/timeseries/forecasting-metrics.html>
[304] <https://www.sparks-chemometrics.com/open-lab/regression-metrics>
[305] <https://arkieva.com/blog/rmse-definition-formula-interpretation/>
[306] <https://pmc.ncbi.nlm.nih.gov/articles/PMC4530125/>
[307] <https://journals.plos.org/plosone/article/file?id=10.1371%2Fjournal.pone.0183250&type=printable>
[308] <https://www.investopedia.com/terms/r/r-squared.asp>
[309] <https://people.duke.edu/~rnau/rsquared.htm>
[310] <https://fairmodel.econ.yale.edu/RAYFAIR/pdf/1984B8.PDF>
[311] <https://www.geeksforgeeks.org/machine-learning/regression-metrics/>
[312] <https://fpp.robjhyndman.com/hyndsight/smape/index.html>
[313] <https://pkg.robjhyndman.com/forecast/reference/dm.test.html>
[314] <https://public.econ.duke.edu/~ap172/Patton_Diebold_JBES_discussion_21apr14.pdf>
[315] <https://www.youtube.com/watch?v=TrzUlo4BImM>
[316] <https://doi.org/10.1016/0169-2070(92)90015-2>
[317] <https://doi.org/10.1109/lt64002.2025.10941436>
[318] <https://doi.org/10.4018/ijoris.2020070104>
[319] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9682961/>
