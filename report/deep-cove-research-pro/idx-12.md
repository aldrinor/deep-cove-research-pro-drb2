# AI-Enhanced Portfolio Management: Theory, Methods, and Evidence Through April 2024

**AI enhances several distinct decisions.** Through 30 April 2024, AI-enhanced portfolio management combines classical theories of risk and pricing with machine learning for forecasting, diversification, information extraction, constrained optimization, and dynamic allocation. The strongest evidence supports task-specific improvements—not a universally superior algorithm. Forecast reliability, estimation error, changing market conditions, liquidity, and trading costs determine whether a statistical improvement becomes an investment benefit [1].

**Four questions organize this report.** What do the foundational theories say about risk, information, and investor behavior? How do AI/ML methods produce useful forecasts, asset groupings, and enriched features? How can portfolio selection reflect liquidity, sustainability, growth, and other investor objectives? Finally, which optimization and rebalancing methods translate those inputs into feasible, cost-aware portfolios?

**Which portfolio-management problem is being solved?**

| Portfolio problem | Principal methods | Model output | Investment decision |
|---|---|---|---|
| Define risk and pricing | Mean–variance, CAPM, factors, risk budgets | Risk exposures and required returns | Choose objectives and benchmarks |
| Generate investment signals | Regularized regression, trees, neural and time-series models | Returns, volatility, or regime forecasts | Select assets and tactical tilts |
| Discover diversification structure | Clustering, networks, HRP | Groups, connections, and risk allocations | Reduce redundant exposures |
| Incorporate investor priorities | AHP, TOPSIS, outranking, fuzzy methods | Preference weights and portfolio rankings | Select acceptable trade-offs |
| Construct and maintain portfolios | Mathematical optimization, metaheuristics, MPC, reinforcement learning | Feasible weights and trades | Allocate capital and rebalance |

## Classic Theoretical Frameworks

### Chronological overview

**The frameworks answer different questions.** Mean–variance theory addresses portfolio choice; CAPM and multifactor models address expected-return compensation; EMH addresses information incorporation; behavioral finance and AMH address investor behavior and changing efficiency. Black–Litterman combines a benchmark with views, while risk-based allocation changes the allocation objective. Their differences make them complementary components of portfolio management rather than interchangeable competitors.

**The early foundations developed sequentially.** The following chronology distinguishes an original contribution from a later synthesis or formalization.

| Framework | Proposal or milestone | Originator or principal proponents | Core portfolio idea | Distinctive assumption or contribution |
|---|---|---|---|---|
| MPT / Mean–Variance Model | March 1952 | Harry Markowitz | Optimize expected return jointly with variance | Covariance creates diversification benefits |
| CAPM | 1964–1966 formalizations | Sharpe, Treynor, Lintner, Mossin | Required excess return follows market beta | Market equilibrium prices systematic risk |
| EMH | 1970 canonical synthesis | Eugene Fama; Paul Samuelson as an antecedent | Prices reflect a specified information set | Information efficiency constrains abnormal returns |
| APT | 1976 | Stephen Ross | Expected returns relate to common-factor exposures | No-arbitrage restrictions replace a single market factor |
| Behavioral Finance | 1979 foundation; 1990s expansion | Kahneman, Tversky; later Shiller, Thaler, Shefrin, Statman | Reference points, biases, and arbitrage frictions affect decisions | Investor behavior need not follow fully rational choice |

The dated foundations are documented in Markowitz’s original paper [2], Perold’s CAPM history [3], Fama’s information-efficiency framework [4], Huberman and Wang’s APT account [5], and Kahneman and Tversky’s 1979 publication [6].

**Later developments changed portfolio implementation.** The next entries are ordered by their first listed milestone; risk parity’s 1996 practitioner milestone therefore precedes AMH, although the term “risk parity” dates to 2005.

| Framework | Proposal or milestone | Originator or principal proponents | Core portfolio idea | Distinctive assumption or contribution |
|---|---|---|---|---|
| Black–Litterman | October 1991 report; 1992 publication | Fischer Black and Robert Litterman | Blend equilibrium returns with confidence-weighted views | Partial and relative views can influence a complete allocation |
| Three-Factor Model | 1992 evidence; 1993 formal model | Eugene Fama and Kenneth French | Explain equity returns with market, size, and value factors | Tradable factor portfolios proxy common return drivers |
| Risk Parity | 1996 fund/analysis; 2005 terminology | Bridgewater, Robert Litterman, Edward Qian | Allocate risk contributions rather than capital equally | Expected-return forecasts can be omitted |
| AMH | 2004 | Andrew Lo | Efficiency and strategy profitability change with market ecology | Competition and adaptation are context-dependent |
| Five-Factor Model | 2015 | Eugene Fama and Kenneth French | Add profitability and investment to the three-factor model | Broaden empirical descriptions of expected equity returns |

These milestones are supported by the Black–Litterman report [7], Fama–French’s 1993 paper [8], risk-parity history [9], Lo’s AMH paper [10], and the factor-model review [11].

**Dates identify particular intellectual contributions.** Fama’s 1970 milestone is the canonical review and information-set taxonomy, building on earlier work rather than marking the first appearance of every efficiency argument. Likewise, prospect theory supplies a precise 1979 foundation for behavioral finance, while the broader field developed through multiple contributors. Black–Litterman’s 1991 report and 1992 publication precede the detailed He–Litterman descriptions of 1999 and 2002 [12].

### 1952: Modern Portfolio Theory and mean–variance selection

**Diversification depends on joint behavior.** Markowitz’s decisive contribution was to evaluate securities as components of a portfolio rather than as isolated investments. For weights \(w\), expected asset returns \(\mu\), and covariance matrix \(\Sigma\), expected portfolio return and variance are:

$$\mu_p=w^\top\mu,\qquad \sigma_p^2=w^\top\Sigma w.$$

**Covariance changes the allocation problem.** Two assets with imperfectly correlated returns can produce lower portfolio volatility than a calculation that simply adds their individual volatilities. This does not mean that a long-only portfolio must have a higher expected return than its highest-return constituent. It means that combining assets can improve the feasible relationship between return and risk—the efficient frontier [2].

**Portfolio choice follows belief formation.** Markowitz explicitly separated observation and experience, which produce beliefs about future securities performance, from the subsequent choice of portfolio. This distinction remains central to AI-enhanced management: a forecasting model can improve the first stage while a conventional optimizer continues to perform the second.

**Input estimation is the practical weakness.** Expected returns and covariances must describe the intended holding period, not merely summarize past observations. Small changes in estimated returns can cause large changes in optimized weights. Markowitz’s original presentation also assumed static probability beliefs and illustrated three- and four-security cases geometrically; these are historical boundaries of the original paper, not restrictions on modern numerical optimization [2].

**AI changes inputs, not diversification arithmetic.** Machine learning can estimate conditional returns, volatility, or covariance structure, but an optimizer can still magnify errors in those estimates. Forecast uncertainty, shrinkage, position limits, and transaction-cost penalties therefore remain important even when the forecasting model becomes more sophisticated [12].

### 1964–1970: CAPM and information efficiency

**CAPM prices market exposure.** Treynor contributed early groundwork, followed by Sharpe’s 1964, Lintner’s 1965, and Mossin’s 1966 formalizations. CAPM relates an asset’s expected excess return to its exposure to the diversified market portfolio:

$$E[r_i]-r_f=\beta_i\bigl(E[r_m]-r_f\bigr),\qquad \beta_i=\frac{\operatorname{Cov}(r_i,r_m)}{\operatorname{Var}(r_m)}.$$

**Only non-diversifiable risk earns compensation.** The mechanism is that investors can diversify away asset-specific risk, so total standalone volatility is not the relevant pricing quantity. Market beta measures the component that remains after diversification. CAPM consequently supplies a benchmark for expected returns and for distinguishing market exposure from estimated alpha [13].

**Equilibrium requires restrictive assumptions.** Sharpe explicitly invoked common borrowing and lending terms and homogeneous expectations about returns, volatilities, and correlations. Standard formulations also assume a common investment horizon and omit taxes and transaction costs. These assumptions make CAPM a disciplined baseline, but they do not describe all the institutional differences or information advantages that an AI system might exploit [13].

**EMH concerns information, not optimization.** Fama’s 1970 synthesis organizes market efficiency by the information already incorporated into prices. Its portfolio implication is that an information set should not provide repeatable abnormal risk-adjusted profits merely because an investor processes it differently [4].

| EMH form | Information reflected in prices | Implication for AI-based signals |
|---|---|---|
| Weak | Past prices and returns | Historical-price patterns face an efficiency benchmark |
| Semistrong | Publicly available information | Public fundamentals, news, and macro data must add incremental value |
| Strong | Public and private information | Even exclusive information would not generate abnormal returns |

**Predictability does not automatically reject efficiency.** Volatility can be forecastable, and expected returns can vary with risk compensation, without creating a free trading opportunity. Moreover, an apparent abnormal return depends on the risk model used to measure it. AI forecasting and asset-pricing interpretation must therefore remain separate: accurate prediction does not establish whether the prediction reflects risk, mispricing, or trading frictions.

**The empirical challenge is substantive.** Shiller’s 2003 review describes the transition from strong academic confidence in efficient markets during the 1970s toward anomalies, excess-volatility evidence, and behavioral explanations. The appropriate conclusion is qualified rather than binary: information efficiency is a demanding benchmark, while observed departures require an explanation of risk, information, and implementability [14].

### 1976–1979: APT and behavioral explanations

**APT broadens the pricing structure.** Stephen Ross’s 1976 Arbitrage Pricing Theory assumes that returns follow a relatively low-dimensional factor structure. In the notation summarized by Huberman and Wang:

$$r=\mu+Bf+\varepsilon,\qquad E[f]=0,\qquad E[\varepsilon]=0.$$

**No-arbitrage links returns to factors.** With many assets relative to the number of common factors, suitable diversification and no-arbitrage conditions imply an approximately linear relationship between expected returns and factor loadings. Unlike CAPM, APT does not require the market portfolio to be the only priced source of common risk [5].

**Factor flexibility creates identification risk.** APT does not specify which factors to use. Empirical implementations employ statistical factors, such as principal components, or economically selected variables, such as interest-rate changes, inflation, and industrial production. A successful factor regression is consequently a joint result about the selected factor structure and the pricing restriction; it is not proof that the chosen factors are uniquely correct.

**Dynamic portfolios require additional care.** Huberman and Wang emphasize that the original one-period APT does not necessarily preclude arbitrage across dynamic trading strategies. This matters when evaluating AI-managed portfolios whose exposures change through time or whose payoffs resemble options. A static factor alpha can be an incomplete description of such strategies [5].

**Behavioral finance changes investor assumptions.** Kahneman and Tversky’s March 1979 prospect theory evaluates gains and losses relative to a reference point rather than only final wealth. Loss aversion and differing attitudes toward gains and losses help explain why an investor’s preferences may diverge from conventional mean–variance choice [6].

**Mispricing can survive rational opposition.** Behavioral explanations also require limits to arbitrage: informed investors face fundamental risk, financing constraints, short-selling difficulties, and implementation costs. Byrne and Brooks summarize Mitchell, Pulvino, and Stafford’s 82 cases in which a parent company’s market value was below the value of its subsidiary stake, with persistence indicating that an apparent discrepancy need not be quickly eliminated [15].

**Return patterns admit competing explanations.** The same review discusses momentum lasting up to 12 months and reversals over three to five years, drawing on Jegadeesh–Titman and De Bondt–Thaler, among others. Behavioral mechanisms include conservatism, overconfidence, and slow information diffusion. Risk-based explanations and sensitivity to portfolio construction remain relevant counterarguments, so these patterns should motivate testable signals rather than automatic trading rules [15].

**Portfolio goals can be psychologically layered.** Shefrin and Statman’s Behavioral Portfolio Theory describes portfolios organized around aspirations and safety needs. Its efficient frontier generally differs from the mean–variance frontier, and CAPM’s two-fund separation need not hold. For AI-enhanced advice, this supports modeling goals and acceptable shortfalls explicitly instead of assuming that one volatility preference captures every investor objective [16].

### 1991–1993: Black–Litterman and empirical equity factors

**Black–Litterman stabilizes the use of views.** Black and Litterman’s October 1991 report, followed by the 1992 publication, uses equilibrium risk premiums as a center of gravity. Investors can specify a few absolute or relative return views and their confidence, rather than forecast every asset independently [7].

**The benchmark supplies a prior.** In a conventional implementation, implied equilibrium excess returns are \(\pi=\delta\Sigma w_b\), where \(w_b\) contains benchmark weights and \(\delta\) represents risk aversion. Views are represented by \(P\mu=q+\varepsilon\), with view-error covariance \(\Omega\); \(\tau\Sigma\) describes uncertainty around the prior. The posterior mean is:

$$\bar{\mu}=\left[(\tau\Sigma)^{-1}+P^\top\Omega^{-1}P\right]^{-1}\left[(\tau\Sigma)^{-1}\pi+P^\top\Omega^{-1}q\right].$$

**Confidence controls the portfolio response.** More uncertain views exert less influence, while more precise views pull expected returns away from the prior. Correlations also transmit a view about one asset to related assets. This makes Black–Litterman a natural interface for ML forecasts: predicted returns can become views, while forecast-error estimates determine their influence [12].

**An empirical comparison illustrates the mechanism.** Hirani and Wallström used 23 Swedish stocks, with a 2004–2013 investment period and preceding data for estimation. At zero brokerage costs, 20-trading-day rebalancing, risk aversion of 2.5, and \(\tau=0.05\), their default results were:

| Portfolio | Annual log return | Annual volatility | Sharpe ratio | Tracking-error volatility |
|---|---:|---:|---:|---:|
| Market-capitalization weighted | 13.50% | 23.66% | 0.4925 | 0.00% by definition |
| Black–Litterman | 14.79% | 23.89% | 0.5419 | 5.01% |
| Mean–variance | 14.17% | 26.40% | 0.4668 | 10.99% |

The source reports continuously compounded annual returns and annualized standard deviations [12].

**Stability is not independent investment skill.** The comparison shows how confidence-weighted views can produce a less extreme allocation, but its investment result also depends on the dividend-yield strategy generating those views. The thesis found sensitivity to view strength, rebalancing frequency, and costs. Black–Litterman is most attractive when the benchmark is economically appropriate and forecast confidence can be calibrated.

**Three factors broaden equity attribution.** Fama and French’s 1992 evidence challenged the adequacy of market beta alone, while their 1993 paper formalized the familiar equity model: market excess return, small-minus-big capitalization returns, and high-minus-low book-to-market returns—SMB and HML. Their tests included 25 size/book-to-market stock portfolios over July 1963–December 1991 [8].

**Factor portfolios are empirical constructions.** The authors formed six portfolios from two size groups and three book-to-market groups, then constructed SMB and HML spreads. They explicitly described the grouping choices as arbitrary rather than uniquely optimal. In AI-enhanced management, these factors provide useful exposure controls and performance benchmarks, while ML can investigate conditional or nonlinear relationships beyond the fixed sorts.

### 1996–2015: Risk parity, AMH, and five-factor pricing

**Risk parity changes what is balanced.** Bridgewater’s All Weather fund and Litterman’s risk-contribution analysis provide 1996 practitioner milestones; Edward Qian introduced the term “risk parity” in 2005. The central observation is that capital balance does not imply risk balance: a 60% equity/40% bond portfolio can remain predominantly exposed to equity risk [9].

**AMH makes efficiency context-dependent.** Andrew Lo’s 2004 Adaptive Markets Hypothesis links investment opportunities to competition, adaptation, and the changing market environment. A strategy can lose profitability and later regain it when conditions become favorable again. This provides a conceptual rationale for regime detection and adaptive model weighting, but it does not itself specify a forecasting algorithm [10].

**Changing predictability is the empirical illustration.** Lo examined rolling 60-month first-order autocorrelations of monthly S&P Composite returns from January 1871 through April 2003. Efficiency, measured by this proxy, varied cyclically rather than improving monotonically. The implication is to evaluate a strategy’s environmental dependence, not to assume that historical profitability is permanent.

**Five factors extend the empirical model.** Fama and French’s 2015 model adds robust-minus-weak profitability, RMW, and conservative-minus-aggressive investment, CMA, to market, size, and value. CMA contrasts relatively conservative investment with aggressive investment; it should not be interpreted as a generic reward for higher asset growth [11].

**The two “five-factor” descriptions differ.** The 1993 paper studied three stock-market factors plus two bond-market factors, related to maturity and default. That stock-and-bond analysis is not the same model as the 2015 five-factor equity specification. Neither the three-factor nor the five-factor equity model includes momentum as one of its named factors [8].

**Model rankings depend on the task.** A 2018 comparison reported the following time-series ranking:

| Time-series rank | Model | Model year |
|---|---|---:|
| 1 | Stambaugh–Yuan four-factor | 2016 |
| 2 | Hou–Xue–Zhang q-factor | 2015 |
| Joint 3 | Fama–French five-factor | 2015 |
| Joint 3 | Barillas–Shanken six-factor | 2018 |

In cross-sectional comparisons, the q-factor, Fama–French four- and five-factor, and Barillas–Shanken six-factor models instead tied for first under the reported tests [17]. A pricing-model ranking therefore should not be treated as a ranking of investable portfolio returns.

### Risk parity and other risk-based allocation methods

**Risk budgeting has a precise definition.** For portfolio volatility \(\sigma_p=\sqrt{w^\top\Sigma w}\), asset \(i\)’s component contribution is \(w_i(\Sigma w)_i/\sigma_p\). Its share of total volatility is:

$$b_i(w)=\frac{w_i(\Sigma w)_i}{w^\top\Sigma w},\qquad \sum_i b_i(w)=1.$$

**Equal contributions are a special case.** General risk budgeting chooses target shares \(b_i\); equal risk contribution, ERC, sets each to \(1/n\). Equal capital weights, inverse-volatility weights, and ERC are therefore different constructions except under particular covariance structures [18].

| Method | Development milestone | Allocation mechanism | Portfolio application |
|---|---|---|---|
| Minimum variance | Markowitz foundation; Clarke et al., 2006 application | Minimize \(w^\top\Sigma w\) | Reduce risk without forecasting returns |
| Maximum diversification | Choueifaty–Coignard, 2008 | Maximize standalone-to-portfolio volatility ratio | Reduce overlapping correlated exposure |
| ERC | Maillard–Roncalli–Teiletche, 2010 | Equalize component risk contributions | Asset-class or security risk parity |
| Risk budgeting | Leote de Carvalho et al.; Bruder–Roncalli, 2012 | Match manager-defined risk budgets | Strategic allocation and alternative indices |
| HRP | López de Prado, 2016 | Cluster assets and allocate recursively | Structure-aware diversification |
| Equal Risk Bounding | Cesarone–Tardella, 2017 | Equalize an upper risk-contribution bound | Permit selective asset exclusion |
| Alpha risk parity | Generalized-barrier extension, 2022 study | Adjust the balance between diversity and minimum risk | Equity, bond, and commodity futures allocation |

The principal covariance-based methods and their milestones are summarized in the risk-based allocation study [19].

**Minimum variance can become concentrated.** Omitting expected-return forecasts addresses an important source of estimation error, but minimizing variance can place large weights in a small set of low-volatility assets. A low-variance portfolio is not necessarily well diversified by holdings, sectors, or economic exposures [20].

**Maximum diversification optimizes a ratio.** Its defining ratio is the weighted average of individual asset volatilities divided by portfolio volatility: \(D(w)=w^\top\sigma/\sqrt{w^\top\Sigma w}\). The numerator represents standalone risk before diversification; the denominator incorporates covariance. The method rewards combinations with substantial risk cancellation, rather than maximizing the number of holdings. Its usefulness consequently depends on stable volatility and correlation estimates, as do the other covariance-based methods [19].

**Risk budgets express allocation priorities.** Bruder and Roncalli describe applications to strategic allocation, risk-parity funds, and equity and bond indexing. Under their formulation, risk-budgeting volatility lies between minimum-variance and corresponding weight-budgeting portfolio volatility. The investor avoids return forecasts but still chooses the risk distribution [18].

**HRP uses hierarchical structure.** Hierarchical Risk Parity converts correlations into distances, clusters assets, orders the covariance matrix to reveal that hierarchy, and recursively divides allocations using cluster-risk estimates. It avoids relying on direct inversion of the complete covariance matrix. However, hierarchical allocation does not imply that every asset’s final global risk contribution is exactly equal, and single-linkage clustering can produce concentrated allocations [19].

**Extensions alter the diversity requirement.** Alpha risk parity connects equal weighting, risk budgeting, and minimum variance through a generalized log-barrier controlling allocation diversity. Equal Risk Bounding instead permits some assets to be excluded; its theoretical comparison with risk parity concerns the specified risk criterion and short-selling conditions, not guaranteed investment outperformance [21][22].

**Risk-based allocation remains an active choice.** It is appropriate when return estimates are particularly unreliable, but leverage, financing costs, covariance shifts, and rebalancing can offset its diversification benefits. Its relative attractiveness declines when credible expected-return differences are sufficiently large to justify taking unequal risk exposures [21].

**Theory should determine the learning task.** AI is most useful when its outputs address a clearly specified forecasting, risk, preference, or control problem within these frameworks.

**Additional documented evidence**

| Entity | Theory or framework name | Originator or development lineage | Core ideas | Proposal or canonical-publication year | Portfolio-management implication |
| --- | --- | --- | --- | --- | --- |
| Modern Portfolio Theory (MPT) / Mean-Variance Model | The page lists Harry Markowitz's 1952 publication…[131] | Harry Markowitz is identified as the founder of Modern…[81] | MPT formalizes the trade-off between risk and…[194] | 1952[138] | MPT formalizes the trade-off between risk and…[194] |
| Capital Asset Pricing Model (CAPM) | Capital Asset Pricing Model (CAPM)[138] | Sharpe (1964); Lintner (1965); Mossin (1966)[143] | Return linear in beta; only systematic risk priced[161] | 1964[138] | Risk-return benchmark; estimates cost of capital[161] |
| Arbitrage Pricing Theory (APT) | The Arbitrage Pricing Theorem was developed by Ross…[51] | The references list Ross’s 1976 paper, “The arbitrage…[95] | The references list Ross’s 1976 paper, “The arbitrage…[95] | 1976[83] | The references list Ross’s 1976 paper, “The arbitrage…[95] |
| Efficient Market Hypothesis (EMH) | The source records Fama as the author of “Efficient…[91] | The source records Fama as the author of “Efficient…[91] | Prices reflect information; excess returns are elusive[142] | 1970[53] | Passive investing and broad diversification favored[142] |
| Three-Factor Model | Fama–French Three-Factor Model[183] | Eugene Fama and Kenneth French[183] | Market, size, and value (SMB, HML); extends CAPM[139] | 1993[62] | Treat size and value as systematic risk factors[138] |
| Five-Factor Model | The Fama–French five-factor model was introduced by…[120] | The Fama–French five-factor model was introduced by…[120] | Market, size, value, profitability, and investment[125] | 2015[125] | Factor inputs for return estimation and optimization[125] |
| Behavioral Finance | The source records Shefrin and Statman as authors of…[91] | The source records Shefrin and Statman as authors of…[91] | Systematic biases, mispricing, and limited arbitrage[142] | 1985[91] | Account for bias, sentiment, and excessive trading[141] |
| Adaptive Market Hypothesis (AMH) | Adaptive Market Hypothesis (AMH)[179] | Andrew W. Lo (2004, 2005)[67] | Dynamic efficiency; investors learn, compete, and adapt[175] | 1976a, 1976b calendar year[84] | The references list Ross’s 1976 paper, “The arbitrage…[95] |
| Black-Litterman Model | The source's references identify Global portfolio…[187] | The source attributes development of the…[55] | Equilibrium + views; confidence-weighted weights[96] | 1992 calendar year[107] | Views + equilibrium produce diversified weights[123] |
| Risk Parity | Risk Parity is represented in the source by Qian's…[188] | Qian (2005); Maillard et al. (2010) [155] | Equal risk budgets; matched risk contributions [56] | 2013 calendar year[197] | Risk Parity is represented in the source by Qian's…[188] |
| Minimum-Variance Allocation | Minimum-variance portfolio composition is documented…[75] | Minimum-variance portfolio composition is documented…[75] | Minimum-variance portfolio composition is documented…[75] | 1952[129] | Optimize weights from expected returns and covariances[129] |
| Equal Risk Contribution | Risk Parity is represented in the source by Qian's…[188] | Maillard, Roncalli & Teïletche (2010) [127] | Equalize risk contributions; long-only weights sum to…[198] | 2013 calendar year[197] | Risk Parity is represented in the source by Qian's…[188] |
| Risk Budgeting | Risk Budgeting [58] | Roncalli (2013) [56] | Risk contributions match prespecified budgets [58] | 1952 calendar year[104] | Diversification and allocation stability [99] |
| Maximum Diversification | The page cites “Toward Maximum Diversification,” a…[113] | Choueifaty (2006); Choueifaty & Coignard (2008) [100] | Maximize diversification ratio; covariance-based [100] | 2006 (introduced); 2008 (developed) [100] | Risk-based allocation; stabilize inverse covariance [167] |

| Entity | Risk-based method name | Risk-method originator or lineage | Risk-method origin or development year | Risk measure or budget | Risk-allocation mechanism | Risk-allocation objective | Risk-method examples | Risk-method limitations | Originator or development lineage | Proposal or canonical-publication year |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Risk Parity | Risk Parity (ERC)[61] | Dalio/Bridgewater; Qian; Maillard et al.[54][60][70] | 2013 calendar year[197] | Volatility; equal risk budget 1/n[58] | Weights equalize asset risk contributions[61] | Diversification and allocation stability[58] | Risk Parity is represented in the source by Qian's…[188] | Ignores expected returns; constraints alter ERC[58][61] | Qian (2005); Maillard, Roncalli & Teiletche (2008)[70] | 2013 calendar year[197] |
| Other risk-based allocation methods | Risk Parity and related methods [99] | Risk-budgeting lineage; generalized risk budgeting [61] | 2014–2015 (formulation/implementation) [102] | Risk budgets; volatility, VaR/CVaR [61][99] | Equal/unequal risk budgets; risk contributions [99] | Diversify and control risk [103] | Risk Parity, ERC, min variance, max diversification [103] | Covariance error, unintended risk, turnover costs [50][102] | Behavioral-response-driven RDAA [67] | 2010 calendar year[163] |
| Minimum-Variance Allocation | Minimum-Variance Allocation [60] | Markowitz; generalized risk budgeting [61] | 2010 calendar year[163] | Portfolio variance/volatility [129] | Closed-form covariance-based weights [100] | Minimize portfolio variance [122] | Risk Budgeting; Diversified Minimum Variance [61][102] | Concentration; turnover; tail risk [100][71] | Minimum-variance portfolio composition is documented…[75] | 1952 [68] |
| Equal Risk Contribution | Equal Risk Contribution [102] | Maillard, Roncalli & Teïletche [102] | 2010 calendar year [102] | Volatility; equal total risk contributions [198] | no evidence found | no evidence found | Risk Parity is represented in the source by Qian's…[188] | no evidence found | Maillard, Roncalli & Teïletche [74] | 2013 calendar year[197] |
| Risk Budgeting | Risk Budgeting [58] | Qian (2005); Maillard et al. (2010) [58] | 2005 (documented lineage) [58] | Relative risk budgets; standard deviation/ES/VaR [58][155] | Weights satisfy RCi/R = bi [75] | Diversify aggregate risk via target budgets [155] | Risk parity; ERC; min-var; max diversification [59][99] | Constraints can prevent exact budget matching [58] | Edward Qian; Maillard-Roncalli lineage [58] | 1952 calendar year[104] |
| Maximum Diversification | Maximum Diversification [60] | Choueifaty (2006); Choueifaty & Coignard (2008) [100] | 2006 (origin); 2008 (development) [100] | Diversification ratio [60] | Covariance matrix and volatilities [100] | Maximize diversification ratio [60] | Risk Parity; Inverse Volatility; ERC [50][100] | Covariance errors; transaction costs; constraints [50][100] | Choueifaty; Choueifaty & Coignard [100] | 2006 calendar year[100] |
| Inverse-Volatility Allocation | Inverse-Volatility Allocation [54] | 2008 calendar year[100] | 1952 calendar year[50] | Asset volatility [103] | Weights proportional to inverse volatility [54] | Equalize stand-alone volatility [103] | Risk Parity; Min-Variance; Max Diversification [75][60] | Ignores correlations; diagonal covariance [103] | Documented in Winter 2024 [145] | 2006 calendar year[100] |

**Scope and chronology**

A 2024 bibliographic lead is Renzi-Ricci, Harvey, and Baynes, **“From Risk Parity to Outcome Risk Parity: A Review and Extension of the Risk Parity Portfolio with Return Predictability,”** *The Journal of Portfolio Management*, 50(5), 73–102, DOI 10.3905/jpm.2024.50.5.073 [49]. Its accessible page establishes only the citation; it does not establish Risk Parity’s origin, mechanism, or findings.

**Chronological foundations**

- **Modern Portfolio Theory (MPT) / Mean–Variance Model — 1952.** Harry Markowitz’s *Portfolio Selection* is the canonical publication; James Tobin’s **1958** work is a material extension. MPT combines returns above a risk-free asset with risk measured through asset covariation, making diversification and portfolio construction explicit. In an AI workflow, forecasts of returns or covariance can feed the mean–variance allocation step; the supplied CovRegpy evidence explicitly connects covariance forecasting with Markowitz methods [51].

**Risk-based allocation and its AI connection**

**Minimum-Variance Allocation — 1952 lineage.** It minimizes \(w^\top\Sigma w\) subject to a long-only, full-investment portfolio with weights summing to one [50]. **Inverse-Volatility Allocation — 2012/2013 cited lineage.** It assigns \(w_i=(1/\sigma_i)/\sum_j(1/\sigma_j)\), so lower-historical-volatility assets receive higher weights [50]. **Equal Risk Contribution — no separate canonical year established in the pre-cutoff card.** Its defining answer is equal relative risk contribution using covariance information [51]. **Maximum Diversification — 2008 cited lineage.** It maximizes the diversification ratio, weighted asset volatility divided by portfolio volatility, thereby exploiting imperfect correlations [50].

The pre-cutoff CovRegpy workflow shows the AI link: extract implicit factors, forecast them, forecast covariance through regularized covariance regression, then weight the portfolio by risk appetite [51]. In its FTSE 100 case (**1 October 2003–1 April 2023**), high-, mid-, and low-frequency covariance forecasts drive RPP weights; risk-aversion levels of **1.2, 1.4, and 1.6** reduce the funded allocation as aversion rises, while forecast frequency changes with GDP-growth versus stagnation conditions [51].

**Efficiency, factors and views**

CAPM—Lintner’s 1965 paper is a development landmark [52]. EMH—Samuelson’s first formal argument (1965), Roberts’s term (1967), Fama’s canonical review (1970; “Efficient markets,” 1991) [53][52]. Prices fully reflect an information set: disclosure should not move price or yield systematic information profit. Costly information (Grossman–Stiglitz, 1980), the 20-Jan-2011 review’s “just under half” support, overreaction, momentum/reversals and predictable returns qualify EMH [53].

**Risk-based allocation**

Risk Parity—All Weather 1996 → Dalio 2004 → Maillard–Roncalli–Teïletche, Summer 2010; equalizes correlation-aware TRC (=MRC×weight), with cited long-only 0≤w≤1, Σw=1; covariance estimation each rebalance is difficult [54]. Minimum variance—a mean-variance subset—minimizes variance; constraints may break equal MRC. Inverse volatility uses w∝1/σ, simpler/correlation-blind, matching Risk Parity with equal correlations or two assets. Risk budgeting permits unequal TRCs, expected returns and Gaussian VaR/ES; maximum diversification maximizes weighted-average σ/portfolio σ; tail-loss parity and duration-volatility are variants [54].

Risk budgeting, no single origin (1996–2013): RCᵢ=bᵢR; bᵢ,xᵢ>0; Σb=Σx=1; minimize SD/VaR; constraints alter ex-post budgets. 60/40: stocks/bonds 90.3%/9.7% risk (Jan 1926–Jun 2004). [56][57][58]

MPT (Markowitz 1952): μ/σ² [64]; CAPM (Treynor/Sharpe/Lintner/Mossin 1961–66): β/sys.risk [63]; EMH (Fama 1970; Regnault 1863): info→prices;3 forms [63]; APT (Ross 1976): no-arb.; X factors [63]; 3-factor (Fama–French 1992/93): Mkt/SMB/HML [62]; Black–Litterman: forecasts→views [64]; Risk parity (1996/2006/2010): ERC; GRB: unequal/overlap budgets; min-var [61]

Black–Litterman(Dec1999):CAPM+views→market;constraints→mean–variance [65]. EMH(Fama/Malkiel1970):weak/semi/strong;passive;bias/friction [66]. AMH(Lo,2004/05):adaptive regimes [67]. RDAA:short-term-volatility weights [67]. Minimum variance(Markowitz,1952/59):covariance-only [68]. Risk Parity(2010/24):S&P500/505 11-sector monthly[69].

Chronology: MPT/Markowitz 1952; CAPM/Sharpe 1964–Lintner 1965; APT/Ross 1976; BL/Black & Litterman 1991; FF3 1993; AMH/Lo 2005; Risk Parity/Qian 2005, risk-budgeting reference/Black 2005, Maillard et al. 2010; FF5 2015 [73][74]. MPT: stochastic returns, variance risk, risk-averse MVO; CAPM: factor pricing; AMH: adaptive efficiency, EMH subset [73][74]. Risk Parity balances risk, not dollars; Euler contributions sum to total risk; equal/arbitrary budgets use volatility, downside or CVaR [71]. Minimum variance minimizes risk but may be nonunique/concentrated; inverse volatility is a Risk Parity variant [71][72]. Alpha Risk Parity: −1=budgeting, 1=min-risk, −∞→budget weights; related: ERC, maximum diversification, factor Risk Parity, volatility timing [71][74]. Gava–Turc (2022): weekly multi-asset data, 156-week covariance, four-week rebalance/one-week lag, no look-ahead; α=−0.2 best Sharpe (1997–2022) [71]. Blomqvist (2017): ERC beat inverse volatility; Risk Parity underperformed in rising-rate regimes [72].

MPT—Markowitz 1952 [79]; CAPM—Sharpe 1963 lineage [77]; APT—Ross 1976: factor pricing; factor choice open [83]; Risk parity/ERC equal risk; minimum variance minimizes risk [75]; kurtosis parity [76].

MPT/Markowitz 1952—mean–variance [94]; CAPM/Sharpe 1964—beta [95]; EMH/Samuelson–Roberts–Fama 1965/67/70—information [92]; APT/Ross 1976—no-arbitrage factors [97]; Behavioral Finance—multi-landmark biases [92][98]; Black–Litterman 1991–92—equilibrium/views [93]; AMH/Lo 2004—adaptive efficiency [92].

MPT (Markowitz, 1952/1959) relies on estimated inputs; MD maximizes weighted-average/portfolio volatility and equals Risk Parity if correlations constant [100]. HRP (2016), ERC (2018), risk budgeting (2024) cluster risk [101].

- **MPT/mean–variance—Harry Markowitz (1952):** expected return, variance and covariance; minimize variance for target return with \(\sum w=1,w_i\ge0\), forming the efficient frontier. Static one-period baseline; higher moments and costs omitted [160][159].
- **CAPM—Sharpe (1964), Lintner (1965), Black (1972):** \(E[R_i]=R_f+\beta_i(E[R_M]-R_f)\); beta-risk pricing supplies MVO inputs, but assumptions and performance are restrictive [161][119].
- **APT—Stephen Ross (1976):** multiple factors explain excess returns; no-arbitrage excludes unexplained specific alpha [124].
- **Fama–French three-factor—Fama and French (1993; 1996):** market, SMB and HML (size/value) address CAPM’s missed variation; premia are noisy and momentum omitted [161].
- **Black–Litterman—Black and Litterman (1990; expanded 1991–1992):** Bayesian equilibrium-plus-views blending, confidence-weighted, yields diversified weights and can take AI views [123].
- **AMH:** learning and adaptation make efficiency time-varying; the cited case is post-cutoff—not substantive evidence—but reports alternating efficiency and inefficiency [144].

MPT/Markowitz 1952: MV [109]; CAPM/Sharpe 1964: β/α [150,328]; EMH/Fama 1970: info [137]; APT/Ross 1976: factors [161,553]; Fama-French 3F M/S/V 1993; 5F 2015 [109]; risk parity/ERC: equal RC [164]; min-var: cov [157]; max-div Choueifaty-Coignard 2008: RQE/var [164].

MPT/MV—Markowitz 1952: return/variance [147]; CAPM—Sharpe 1964: market beta [167]; APT—Ross 1976 [165]; FF3—Fama/French 1993: M/SMB/HML [149]; FF5—Fama/French 2015 (detail unresolved) [149]; Behavioral Finance: heterog./partial moments [151]; MVP=min covariance; MD=max div. ratio [167].

MPT—Markowitz (1952): maximize return at fixed variance or minimize variance at fixed return; covariance/diversification are central, and ML forecasts can feed expected returns [121][133]. CAPM—Sharpe (1964), with Lintner/Mossin: beta prices systematic risk against the risk-free rate [121][169]. APT—Ross (1976): multiple macro-factor sensitivities and premia [121]. The Three-Factor Model supports dynamic factor mining; Fama–French’s Five-Factor Model (2015) supplies a broader factor basis [133]. EMH—Fama (1970s): weak, semi-strong and strong forms [169]. Black–Litterman (1992) Bayesianly combines equilibrium returns with investor views [121][133]. Risk parity equalizes holding risk while excluding returns [168].

MPT Markowitz 1952 μ/σ² [174]; CAPM Sharpe 1964 β [108]; APT Ross 1976/RR 1980 factors [173]; EMH Fama/Malkiel 1970 info [136]; FF3 F&F 1993 M/SMB/HML [150]; FF5 F&F 2015 +RMW/CMA [150]; BF mid/late80s multi-origin biases [173]; BL B/L 1991 Bayes [130]; RP Maillard 2010 equal-RC [174]; MinVar minσ² [132]; ERC equal-RC [174]; MaxDiv ratio, year? [132]. AI: forecasts/factors/views→goals [162][130].

MPT—Markowitz (1952): risk-weighted expected-return optimization; GMVP uses covariance only [125][146]. APT—Ross (1976): factor exposures price returns and diversify idiosyncratic risk; factor identification is uncertain [176]. EMH—Bachelier (1900), Fama (1970): information is priced in weak/semi-strong/strong forms [177][178]. FF3 (1993) and FF5 (2015: market, size, value, profitability, investment) supply factor inputs [125]. AMH—Lo (2004/05): episodic efficiency; behavioral finance: bias/emotion [112][175]. BL (1990/1992) combines equilibrium and views [125].

- **EMH—Samuelson/Fama (1965/1970); Roberts (1967; weak/strong):** prices reflect information; anticipated changes are unforecastable, but costs/evidence qualify it [148][181][182].
- **Behavioral finance—Allais/Ellsberg (1953/1961); Kahneman–Tversky (1979):** challenges simple optimization; sentiment, herding, heuristics and noise affect prices [152].
- **AMH—Andrew W. Lo (proposal year not established):** evolutionary learning and natural selection make efficiency and predictability environment-dependent; allocation adapts [180][154].
- **Fama–French 3/5-factor models (1992/2015):** market, size, value, then profitability/investment inform forecasts and covariance; some portfolios remain unexplained [139][158].
- **MPT/minimum variance:** minimize forecast \(w′Σw\) under budget; an S&P 500 study used 430 stocks, daily 5-minute data (2006–11), 1,000-window rolling forecasts and 473 out-of-sample days [158].

BL—Fischer Black/Robert Litterman: 1990; 1991/92 pubs; Bayesian equilibrium+views/confidence→weights; ML/DRL views (2023–24); Gaussian/generalization limits [153][105][111]. Risk Parity/ERC (Qian 2011): equalizes correlated risk; HRP/STOXX600, 1-y lookback, OOS SR 0.66 [188][116][140]. Max-div: vol/correlation-only; inv-vol 1/σ, closed-form, no returns/cov; duplicates clusters; Risk-budgeting preferred [117][189]. MV cmp [114].

Risk Parity (origin year unresolved; 2021-03-03 review) equalizes asset-class risk contributions; variants change risk metric, leverage and tactical allocation, with implementation/performance caveats [192]. Covariance-based methods include GMV, ERC and Maximum Diversification [191]: GMV minimizes variance under unit budget and omits means; ERC equalizes total-risk contributions [115]. Maximum Diversification maximizes diversification ratio; Choueifaty–Coignard, 2008 [191][135]. Inverse volatility \(w∝1/σ\) equalizes stand-alone, not total, risk [193]. Risk Budgeting uses investor-set budgets; pre-cutoff evidence unresolved [190].

MPT/GMV—Markowitz 1952: mean/variance [129]; CAPM—Sharpe 1964: β/systematic risk [88]; APT—Ross 1976: factors [195]; Behavioral Finance—biases, disposition effect 1985 [196]; Black–Litterman—Black/Litterman 1990: views/equilibrium [129]; Risk Parity/ERC—Spinu 2013: equal contributions [197][134].

Show milestone dates with labels rather than collapsing lineages: EMH has a 1900 precursor, 1965 contribution, 1967 term milestone and 1970 canonical formulation; Behavioral Finance has a 1985 consensus versus a later 1994 alternative; and Black–Litterman has 1990 introduction, 1991 expansion and 1992 canonical publication [177][53][181][91][123]. Risk Parity is a 1990s lineage with 2004 documentation, 2005/2010 formulations and a 2013 milestone; list Minimum-Variance (1952/1960s), Risk Budgeting (2005/2013), Maximum Diversification (2006/2008), Equal Risk Contribution (2010) and Inverse-Volatility (2008/2010/2011/2012) as separately labelled methods [60][54][70][61][197][129][58][100][198].

Modern Portfolio Theory/Mean–Variance Model is Markowitz’s 1952 framework: expected return, variance, covariance and diversification define the risk–return trade-off used to choose weights [128][187][166]. It is the AI-management baseline for improved risk/return estimation and causal or machine-learning diversification, but correlation and forecast-input sensitivity can make allocations unstable, especially in downturns [126][80][79].

CAPM’s development lineage is Sharpe (1964), Lintner (1965) and Mossin (1966); expected return is linear in market beta/systematic risk, so non-diversifiable rather than idiosyncratic risk is priced [143][88][170]. It benchmarks AI-enhanced expected-return, cost-of-capital and selection decisions, with covariance/volatility estimation as an extensible input, but depends on market-efficiency and risk-free-rate assumptions [78][77][171].

APT (Stephen Ross, 1976) is a no-arbitrage multifactor framework: expected returns are linear in economic/financial-factor sensitivities, and well-diversified portfolios with the same beta should have equal expected returns [83][85][86]. AI can use factor analysis/PCA and beta estimation for allocation and performance evaluation, but APT leaves factors unspecified; data collection is costly, and a wrong factor structure can yield a non–mean-variance-efficient portfolio [83][82][84][85][89].

EMH’s lineage runs from a 1900 precursor through Samuelson (1965), Roberts (1967) and Fama’s 1970 canonical formulation; prices reflect available information, so competition removes information-based excess returns under idealized frictionless, costless trading [177][53][181][138][92]. For AI management, EMH is the efficiency benchmark for forecasts and rebalancing, while costly information and crisis behavior challenge strict efficiency, including the 2007–2010 crisis [173][136][53][63].

Fama–French Three-Factor Model (1993) extends CAPM with market, size (SMB) and value (HML) exposures to capture systematic return patterns [139][183][167]. It gives AI management a benchmark for return prediction, stock selection and simulation, but SMB/HML are empirically motivated rather than investor-state factors, so their explanations remain model-dependent [110][118][161].

Fama–French Five-Factor Model (Fama and French, 2015) adds profitability and investment to market, size and value because the Three-Factor Model left expected returns insufficiently explained; the additions follow dividend-discount reasoning [125][106][185]. It supplies AI portfolio construction with factor inputs and alpha benchmarks, improves coverage of size/value/profitability/investment patterns, but misses low average returns of small, heavily investing, low-profitability firms [156][172][184][185].

Behavioral Finance is a cumulative challenge to EMH: Kahneman–Tversky’s Prospect Theory (1979), De Bondt–Thaler’s 1985 overreaction work and the alternative 1994 starting date show why no unique origin should be imposed; psychology and limits to arbitrage explain sentiment, limited attention and overconfidence [175][87][91][90][186]. For AI management, it motivates sentiment/bias features and safeguards against emotional decisions, while warning that these mechanisms can move prices away from fundamentals and weaken purely rational strategies [186][180][142].

Adaptive Market Hypothesis (Andrew W. Lo, 2004; 2005) synthesizes EMH and behavioral finance through evolutionary competition, adaptation and natural selection: learning investors make efficiency and predictability vary with environmental, behavioral, structural and information conditions [180][175][87]. AI management should therefore use regime-aware allocation and volatility-persistence tools such as GARCH, treating any predictive edge as conditional and potentially temporary after shocks or adaptation [144][112][175].

rejected: no_entity. Black-Litterman Model was introduced in 1990, expanded in 1991, and canonically published in 1992; its Bayesian combination of equilibrium returns and investor views produces diversified allocations [123]. AI can generate views or risk inputs through predictive regressions, volatility and sentiment models, and recurrent or Transformer networks; constrained implementations require a separate optimization stage [105][111][65].

Risk Parity/Equal Risk Contribution (Qian 2005; Maillard et al. 2010) is a risk-budget framework using volatility, covariance and Euler decomposition to equalize each asset’s total risk contribution without expected-return forecasts [155][198][71][75]. For AI management it is a return-agnostic, algorithmic and network-extensible benchmark, but it can ignore expected returns and remains exposed to covariance error and constraint-driven departures from exact parity [117][190][115][58][50].

## Review of AI/ML Applications

### Signal generation: objectives and portfolio consequences

**Signals must lead to identifiable decisions.** Portfolio-management signals generally predict expected returns, conditional volatility, relative asset attractiveness, or market states. Return forecasts can determine rankings or active weights; volatility forecasts can change risk budgets or leverage; classification outputs can determine whether a tactical allocation favors one asset class over another [1].

**Forecast accuracy and investment value differ.** A small improvement in average prediction error can matter greatly if it identifies rare, large losses. Conversely, accurate price-level forecasts may offer little trading value if they mainly reproduce persistent price levels. Portfolio evaluation must therefore consider the forecast target, holding period, risk exposure, turnover, and decision rule connecting predictions to trades.

**Two forecasting dimensions should be separated.** High-dimensional modeling addresses many simultaneous predictors, while time-series modeling addresses temporal dependence. A model can do both: an elastic-net regression can use many lagged variables, and an LSTM can process a multivariate feature sequence. The distinction is about the problem being addressed, not an exclusive taxonomy.

### High-dimensional forecasting based on linear models

**Regularization controls unstable coefficient estimates.** When many predictors are correlated or numerous relative to the effective time-series sample, ordinary least squares can fit noise and produce unstable forecasts. A common penalized linear specification is:

$$\hat{\beta}=\arg\min_{\beta}\left\{\frac{1}{T}\lVert y-X\beta\rVert_2^2+\lambda_1\lVert\beta\rVert_1+\lambda_2\lVert\beta\rVert_2^2\right\}.$$

**The penalties encode different preferences.** Ridge uses the squared-coefficient penalty to shrink estimates; lasso uses the absolute-coefficient penalty and can set coefficients to zero; elastic net combines both. These methods remain linear in their chosen predictors, although those predictors may include transformations or interactions [1].

| Method | Main mechanism | Representative research | Portfolio use |
|---|---|---|---|
| Ridge | Shrink correlated coefficients | Martin–Nagel, 2022 | Stabilize return forecasts |
| Lasso | Select a sparse predictor set | Chinco et al.; Freyberger et al., 2020 | Identify short-lived signals or relevant characteristics |
| Elastic net | Combine shrinkage and selection | Gu et al., 2020; Kozak et al., 2020 | Forecast returns or regularize factor portfolios |
| PCA | Compress predictor covariance | Gu et al., 2020 | Create lower-dimensional inputs |
| Principal component regression | Regress returns on principal components | Gu et al., 2020 | Forecast using compressed features |
| Partial least squares | Extract target-relevant components | Gu et al., 2020 | Compress predictors toward return prediction |

These applications are described in Bagnara’s [1].

**Ridge favors stability over selection.** It is useful when predictive information is distributed across correlated variables rather than concentrated in a few independently strong signals. Martin and Nagel’s study, using individual-stock data over 1926–2019, demonstrates the central difficulty: high-dimensional predictability can look persuasive in sample and become much weaker out of sample. Regularization controls estimation variance; it does not create a durable information advantage.

**Lasso can reveal economically meaningful sparsity.** Chinco and coauthors used lagged returns from the NYSE universe to predict one-minute-ahead returns, estimating models over rolling 30-minute windows with the preceding three minutes of returns as candidate predictors. Bagnara reports out-of-sample adjusted \(R^2\) of 2.47% and an annualized strategy Sharpe ratio of 1.79. Selected predictors were short-lived—typically retained for no more than 15 minutes—and associated with recent fundamental news [1].

**The application determines operational demands.** A predictor that lasts minutes creates a latency and execution problem, unlike a monthly characteristic used for strategic stock selection. Freyberger and coauthors’ adaptive group-lasso work instead studied 62 firm characteristics over 1965–2014 and investigated which characteristics contain independent predictive information. The resulting portfolio application is feature selection and conditional stock ranking rather than high-frequency execution [1].

**Elastic net addresses correlated signal groups.** Lasso can choose inconsistently among strongly correlated variables, whereas elastic net combines selection with coefficient shrinkage. Gu and coauthors include it in their return-forecasting comparison. Kozak and coauthors use related regularization for the stochastic discount factor—the object linking uncertain future payoffs to current prices—rather than simply forecasting each stock’s next return. Their finding that many characteristics remain useful challenges the assumption that the relevant factor structure must always be sparse [1].

**Dimension reduction solves a different problem.** Principal component analysis, PCA, finds linear combinations explaining predictor variation; principal component regression, PCR, then uses selected components to forecast the target. Partial least squares, PLS, instead makes the target relevant to component extraction. PCA can be effective under collinearity, but a high-variance component need not be the most useful return predictor, and components can change when the predictor set or scaling changes.

**Component selection must respect time.** Standardization, component estimation, feature selection, and penalty tuning should use information preceding the forecast evaluation period. Bagnara emphasizes that conventional randomly mixed cross-validation can break time-series dependence; expanding-window or sequential validation is better aligned with investment forecasting [1].

**Simple models remain meaningful counterexamples.** Cukrowski’s 2022 comparison used one logged U.S. producer-price-index series, PPIACO, with 24 lags. Lasso performed best under lasso-based lag selection, while ordinary least squares had the best mean squared error without that selection; SARIMA performed worst in that particular comparison. This is evidence about a macroeconomic forecasting exercise, not a portfolio-return result, but it illustrates why model complexity should not substitute for task-specific comparison [23].

### Nonlinear forecasting and economically structured learning

**Nonlinear methods capture conditional interactions.** Trees, random forests, boosting, and neural networks can represent relationships such as momentum working differently across liquidity or volatility conditions. Their contribution is not merely fitting a curved response to one variable; interactions among predictors can be economically important.

| Method family | Mechanism | Representative application | Decision output |
|---|---|---|---|
| Random forest | Average decorrelated trees | Moritz–Zimmermann, 2016 | Conditional stock rankings |
| Boosted trees | Sequentially correct weak learners | Gu et al., 2020 | Expected-return predictions |
| Feedforward neural networks | Learn nonlinear feature mappings | Gu et al., 2020; Bianchi et al., 2021 | Equity or bond-return forecasts |
| Instrumented PCA | Let characteristics determine factor loadings | Kelly et al., 2019 | Conditional factor exposures |
| Conditional autoencoders | Learn nonlinear factors and loadings | Gu et al., 2021 | Expected returns and factor portfolios |
| Adversarial pricing networks | Fit pricing restrictions against difficult test assets | Chen and coauthors | A learned stochastic discount factor |

The mechanisms and applications are summarized in the asset-pricing literature review [1].

**Large comparisons support conditional leadership.** Gu and coauthors’ 2020 study examined individual-stock predictions over 1957–2016, using 94 characteristics, 74 industry dummy variables, and eight macroeconomic variables. Neural networks and boosted trees were leading methods in the reviewed comparison, with past returns, liquidity, risk measures, and valuation ratios repeatedly important [1].

**Ensembling can reduce model uncertainty.** Mekelburg’s 2023 dissertation combined forecasting procedures using more than 300 firm-level variables, shrinkage, and nonlinear methods. It reported an average annualized Sharpe ratio of 0.47 versus 0.37 for buy-and-hold over a 48-year U.S. evaluation period. The result supports the particular ensemble and allocation design; the reported difference is 0.10 Sharpe-ratio units [24].

**Economic structure improves interpretation.** Instrumented PCA allows factor exposures to vary with company characteristics, while conditional autoencoders allow those relationships to become nonlinear. Risk-premium PCA modifies ordinary statistical factor extraction so that factors with relatively weak time-series variation but meaningful expected-return information can matter. These methods connect learning to factor pricing rather than treating every predictor as an unexplained source of alpha [1].

**Asset classes require different information.** Bianchi and coauthors’ Treasury-bond comparison found that many methods performed poorly when given only yields. Forward rates and macroeconomic inputs changed the comparison, with a group-ensembled neural network performing best in the reviewed study. Inflation, money, and credit were important predictors. Similarly, instrumented PCA applications to index options relate exposures to option characteristics and the implied-volatility surface [1].

**Investability can reverse apparent advantages.** Avramov and coauthors’ comparisons, summarized by Bagnara, show that excluding microcaps, distressed firms, or firms without credit ratings can reduce network-based risk-adjusted returns by more than half, while instrumented PCA produces more robust strategies. High turnover and extreme positions create additional implementation concerns. A model’s value therefore depends on where its gains arise, not only on its average forecasting score [1].

### Time Series Forecasting

**Temporal models address different targets.** Classical time-series methods remain important baselines inside AI-enhanced systems. ARIMA models conditional mean dynamics; GARCH models conditional variance; hidden-state models infer regimes; recurrent networks and transformers learn more flexible sequential relationships.

| Method | Temporal mechanism | Forecast target | Representative application |
|---|---|---|---|
| ARIMA / SARIMA | Autoregression, differencing, moving-average errors, seasonality | Prices, returns, macro variables | Hiransha et al., 2018 comparison |
| GARCH | Variance responds to past shocks and variance | Conditional volatility | Vanguard’s 2022 forecasting engine |
| State-space / HMM | Infer an unobserved state from observations | Regimes and conditional moments | Nystrup et al., 2017 |
| RNN / LSTM | Recurrent state and gated memory | Prices, returns, sequential signals | LSTM-enhanced rebalancing study |
| CNN | Learn local patterns in sequences | Price or movement signals | Hiransha et al., 2018 |
| Transformer | Attention across sequence positions | Index forecasts | Wang et al., 2022 |
| k-nearest neighbors | Match current conditions to past observations | Relative asset-class regime | Runde, February 2024 |

Representative applications appear in the stock-prediction survey [25], Vanguard’s analytical study [26], and Nystrup’s regime-based allocation paper [27].

**ARIMA remains a useful mean benchmark.** Autoregressive Integrated Moving Average models combine lagged observations, differencing, and lagged forecast errors; SARIMA adds seasonal structure. Hiransha and coauthors’ 2018 comparison reported stronger neural-network price forecasts than ARIMA across five stock series associated with the Indian National Stock Exchange and New York Stock Exchange. The portfolio implication is a candidate signal improvement, not an automatic conclusion about trading returns [25].

**GARCH forecasts risk rather than direction.** Generalized Autoregressive Conditional Heteroskedasticity models capture volatility clustering: large recent shocks raise forecast variance, while persistence carries that variance forward. A basic specification is:

$$h_t=\omega+a\varepsilon_{t-1}^{2}+bh_{t-1}.$$

**Risk forecasts can change feasible exposure.** Higher forecast volatility can reduce a position under a fixed risk budget, subject to correlations and other constraints. Vanguard’s 2022 framework uses GARCH within a regression-based Monte Carlo engine that forecasts returns, volatilities, and correlations jointly. GARCH itself is a classical statistical model; its use inside an automated allocation system should not be confused with a neural-network architecture [26].

**State-space methods model hidden conditions.** A hidden Markov model, HMM, is a discrete-state state-space model: observations depend on an unobserved state, which evolves according to transition probabilities. Nystrup and coauthors use a two-state, time-varying HMM to forecast means, variances, and correlations, then feed those quantities into portfolio control. The application directly connects latent-state inference to allocation [27].

**LSTM learns gated temporal dependence.** Long Short-Term Memory networks extend recurrent neural networks with gates controlling which information is retained or discarded. They can combine recent prices with longer histories and external features. In the rebalancing study discussed below, LSTM price forecasts become inputs to a reinforcement-learning allocation policy, making the decision link explicit [28].

**Transformers were already represented by 2022.** Wang and coauthors applied a deep transformer to the CSI 300, S&P 500, Hang Seng, and Nikkei 225 indices. Its encoder–decoder architecture and multi-head attention provide a different way to model relationships across a sequence than recurrent memory. The stock-prediction survey reports stronger forecasting performance than the compared traditional approaches; portfolio usefulness still depends on how the predictions determine positions [25].

**A regime classifier need not be recurrent.** Runde’s February 2024 tactical-allocation study used k-nearest neighbors, or kNN, to find historical macroeconomic situations resembling the current one. Its source database contained 127 monthly FRED-MD series; the selected configuration used nine principal components from 82 retained variables and 11 neighbors [29].

**Balanced accuracy reveals asymmetric performance.** For monthly model forecasts from February 1993 through May 2022, the kNN recalls were 78% for equity-outperformance months and 40% for government-bond-outperformance months. Balanced accuracy was therefore \((78\%+40\%)/2=59\%\), compared with 50% for an always-equity classifier. The always-equity rule’s approximately 60% ordinary accuracy reflected the longer historical frequency of equity outperformance, illustrating why ordinary accuracy alone can mislead.

**The portfolio rule uses relative conviction.** Agreement between the ML signal and the existing tactical recommendation increases active positioning; disagreement reduces it. This is more informative than simply declaring the model “59% accurate,” because the relevant question is how its errors and correct forecasts alter portfolio exposure. The study’s separate, fully unseen signal period begins in June 2022 [29].

**Volatility and selection have additional examples.** Usmani and coauthors’ KSE study combined market history, commodity prices, currency information, news, and sentiment with neural networks and support vector machines; the multilayer perceptron led their volatility comparison. Kumar and coauthors’ five-stock study found different leaders across stocks—random forest for Amazon, Bata, and Bosch, and Naive Bayes for Cipla and Eicher—using technical indicators and five to ten years of history [25].

### Asset Clustering and Network Analysis

**Unsupervised learning addresses redundant exposure.** Assets can be numerous yet economically similar. Clustering seeks groups with common return behavior, while network analysis describes which assets or groups are strongly interconnected. The resulting structure can guide representative-asset selection, allocation across clusters, and risk monitoring without requiring an expected-return forecast.

| Method | Structure identified | Construction mechanism | Portfolio application |
|---|---|---|---|
| Correlation blockmodel | Similar within- and outside-cluster correlations | Estimate groups with shared dependence profiles | Select representative stocks |
| Hierarchical clustering / HRP | Nested asset groups | Distance tree and recursive allocation | Spread risk across correlated groups |
| Minimum spanning tree | A sparse market backbone | Retain a connected tree of strongest relationships | Identify central and peripheral assets |
| Louvain / NetMod | Communities | Optimize network modularity | Allocate across and within communities |
| DCCA / DPCCA | Detrended and partial dependence | Compare nonstationary series across scales | Construct alternative dependence networks |
| Spectral portfolios | Common movement in matrix eigenstructure | Unsupervised spectral representation | Diversification-oriented construction |

The applications are documented in the correlation-blockmodel study [30], network-allocation analysis [19], centrality-based ERC study [20], and Ibanez’s spectral-portfolios paper [31].

**Blockmodels connect clustering to asset selection.** The 2022 correlation-blockmodel study seeks a small stock subset approximating the diversification of the full universe. Assets in a modeled cluster are highly correlated internally and have similar correlation profiles with assets outside the cluster. Selecting representatives can therefore reduce redundant holdings rather than merely reducing portfolio size arbitrarily [30].

**Network topology makes relationships visible.** Mantegna’s 1999 market graphs represent assets as nodes and correlations as links; a minimum spanning tree, MST, compresses the complete network into a connected backbone. Betweenness centrality measures how frequently a node lies on paths connecting other nodes. Such measures can identify assets occupying systemically connected positions [20].

**Correlation distances support hierarchical construction.** One normalized distance used in the network-allocation literature is:

$$d_{ij}=\sqrt{\frac{1-\rho_{ij}}{2}}.$$

**HRP and community allocation differ.** HRP builds a hierarchy and recursively divides capital according to estimated cluster risk. NetMod instead links sufficiently correlated assets, detects communities with Louvain modularity, and divides weights equally across communities and then equally within them. With \(G\) communities and \(n_g\) assets in community \(g\), the latter rule gives each member \(1/(Gn_g)\), preventing a large cluster from receiving more capital merely because it contains more securities [19].

**Dependence measurement changes the resulting structure.** Pearson correlation measures linear association, and a fixed estimation window implicitly treats dependence as locally stable. Detrended Cross-Correlation Analysis, DCCA, addresses detrended relationships in nonstationary series; Detrended Partial Cross-Correlation Analysis, DPCCA, additionally controls for other series. These alternatives can change clusters and edges, but partial dependence should not be read as proof of causality [19].

**Centrality can enter the allocation objective.** A January 2024 study scaled covariance as \(Q=D\Sigma D\), with diagonal multipliers derived from MST betweenness centrality. Lower multipliers for peripheral assets reduce their modeled risk and increase their ERC allocations. Using adjusted daily prices from December 1998–December 2022, the study retained 75 S&P100 assets and began backtesting in December 2003 [20].

**The reported benefit is regime-sensitive.** Centrality-adjusted ERC improved returns relative to base ERC at broadly similar risk, but its risk could exceed base ERC during bear markets. Separately, the NetMod study used 32 simulated assets, 520 observations, re-estimation intervals of 60 observations, and 100 runs per simulation corpus, reporting strong results in many scenarios [20][19].

**Topology is a representation, not new information.** When a graph is built from the same correlation matrix used by an optimizer, the graph does not create an independent data source. Its value is to impose a useful structure or allocation rule. The judgment changes if rolling communities become unstable, clustering concentrates weights, or correlations rise together during stress; historical work found market trees contracting during crises [20].

### Feature Enrichment

**Enrichment expands the information set.** Feature enrichment includes transforming existing data, combining sources, extracting structured signals from text or images, and dealing with sparse observations. Its portfolio value comes from supplying information that is timely and relevant to a decision—not from increasing the number of columns in a dataset.

| Data family | Concrete inputs | Enrichment method | Portfolio use |
|---|---|---|---|
| Market data | Open, high, low, close, volume | Returns, momentum, volatility, technical indicators | Timing and stock ranking |
| Fundamentals | Revenue, EPS, dividends, capitalization, earnings dates | Ratios, growth rates, reporting-event alignment | Expected returns and quality assessment |
| Macroeconomics | Output, labor, credit, rates, prices | Scaling, components, lagged regime features | Asset-class allocation |
| Text and attention | News, filings, tweets, Google Trends | NLP sentiment, tone, uncertainty, activity measures | Return, volatility, and event signals |
| Alternative operating data | Transactions, sales indicators, satellite imagery | Aggregation and company-level mapping | Earlier estimates of business conditions |
| ESG and regulatory data | Disclosure scores, controversies, regulatory information | Scores, classifications, policy indicators | Screening, preferences, and constraints |

The data families are described in the deep-learning market-data survey [32] and the alternative-data study [33].

**Technical features remain useful engineered inputs.** Moving averages, relative-strength measures, volume trends, and volatility estimates summarize raw market observations at different horizons. Their inclusion can help a model learn nonlinear interactions, but the indicator itself is not an AI method. Kumar and coauthors’ comparison, for example, used 10- and 50-day moving averages alongside momentum, volatility, and other indicators [25].

**NLP converts language into decision variables.** Natural language processing can turn news or social-media content into sentiment, fear, optimism, uncertainty, or event features. Refinitiv was described as offering approximately 220 datasets across 15 categories, including conventional market data. MarketPsych Analytics processed more than 4,000 news and social-media sources into text-derived scores [33].

**Filtering is part of the mechanism.** One interviewed firm covering approximately 4,000 U.S. stocks accessed more than 500 million tweets per day and filtered approximately 90% for duplicates and spam. It used a dictionary of roughly 20,000 unigrams and 400 bigrams, aggregated sentiment over rolling 24-hour windows at one-minute intervals, and normalized it with 20-day Z-scores. These figures describe an information-processing system; they do not measure investment profitability [33].

**Upstream fundamentals offer a timing mechanism.** A hedge-fund interview describes acquiring operating information before it reaches financial statements: sales observations can inform cash-flow expectations before formal release. The path to a portfolio decision is concrete—operating observations update an earnings or cash-flow forecast, which changes expected returns, a Black–Litterman view, or a security ranking [33].

**Point-in-time availability determines validity.** Financial statements and macroeconomic releases arrive with lags, and subsequent revisions can change historical datasets. Features must be aligned to when they became publicly usable, rather than simply to accounting-period labels or database indexing dates. Otherwise, an apparently predictive enriched feature can contain future information [32].

**Sparse data change the modeling choice.** Pooling observations across companies through global models can be more practical than fitting separate models to short quarterly histories. Dense features can also be engineered from sparse observations, while multi-task-inspired guidance can borrow information across related forecasting tasks. Active acquisition adds a further decision: whether the expected usefulness of a feature justifies its potentially unequal acquisition cost [34].

**Data quality can outweigh data novelty.** The alternative-data literature reports mixed sentiment results and identifies manipulated content, missing histories, mislabeling, low-resolution imagery, acquisition costs, and privacy obligations as material issues. A sentiment feature may represent investor beliefs, marketing activity, bots, or manipulation; those competing mechanisms imply different portfolio responses [33].

**Usefulness depends on incremental information.** Enrichment is most persuasive when it improves the actual allocation decision after timing alignment, existing-feature controls, and data costs. If the information is already reflected in prices or merely duplicates a conventional predictor, more elaborate processing need not improve the portfolio.

**The strongest AI application is decision-specific.** Forecasting, clustering, and enrichment should each be judged by the portfolio decision they improve and the conditions under which that improvement survives.

**Additional documented evidence**

| Entity | Technology category | Specific application or method name | AI/ML mechanism | Data, features, or graph inputs | Prediction or structural targets | Portfolio-management role | Specific applications | Representative research | Research publication date (ISO date) | AI/ML limitations and validation | Network-topology measures | Feature-enrichment sources | AI/ML method catalog |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Signal Generation | Signal generation[205] | Return/volatility forecasting; stock selection[227] | Convert model forecasts into selections and weights[205] | Prices, returns, macro factors and financial indicators[106] | Asset returns, volatility and price movements[227] | Selection, allocation and trading[220][205] | Return prediction; stock selection | Taguchi et al. (2023)[213] | 2023-09-11[213] | Nonstationarity, overfitting; OOS/CV tests[205] | Network-based indicators for market prediction[276] | Financial news and social media | Elastic nets, PCA/PLS, RF, boosting, ANNs, NLP/LLMs[205] |
| High-Dimensional Forecasting Based on Linear Models | Signal generation [203] | High-dimensional linear forecasting [205] | Regularization and dimensionality reduction [205] | Returns, factors, liquidity, valuation ratios [205] | Next-month returns; realized volatility [205][230] | Stock selection and portfolio construction [205] | Return forecasting; stock selection [205] | Kelly & Pruitt (2015); Tibshirani (1996) [205] | 2024-01-20 [203] | Noisy data; overfitting; out-of-sample validation [205][230] | no evidence found | no evidence found | OLS, LASSO, ridge, elastic net, PLS [205] |
| Time Series Forecasting | Time Series Forecasting [273] | N-HiTS [273] | Forecast t inputs for t+1 returns [116] | Prices, volume, technical indicators [235] | Stock prices and returns [273][116] | Form portfolios from return forecasts [116] | Price forecasting; long-short portfolios [273][116] | Deep TS forecasting for index tracking [239] | 2020-12-27 [239] | Chronological holdout; no walk-forward  | Time-series forecasting measures and analyzes…[237] | SMA, EMA, RSI, Bollinger Bands [235] | ARIMA, VAR, RNN, LSTM, N-BEATS, TS-Mixer [106] |
| Asset Clustering and Network Analysis | Unsupervised asset clustering and network analysis [205][241] | The page cites Mantegna's 1999 work on hierarchical…[228] | Clusters reveal structure; constrain portfolio weights [241] | Log returns, correlations, network nodes and edges [254] | Asset communities and market structure [241] | Diversification and portfolio optimization [241] | Community portfolios; centrality allocation [241][264] | The page cites Mantegna's 1999 work on hierarchical…[228] | 1 December 2025[236] | Robust across periods; unreliable covariance [241][254] | The page cites Mantegna's 1999 work on hierarchical…[228] | Prices, macro data, news, social trends [223] | The page cites Mantegna's 1999 work on hierarchical…[228] |
| Unsupervised Learning | Unsupervised learning[263] | Cluster analysis[263] | Network-based and clustering-related quantitative…[74] | Historical returns, volatility, correlations[246] | Network-based and clustering-related quantitative…[74] | Network-based and clustering-related quantitative…[74] | Asset selection and portfolio formation[240] | Cerqueti, D’Urso, De Giovanni, Giacalone, and Mattera…[245] | October 2020[187] | Human supervision; spurious clusters possible[243] | A representative pre-cutoff study is Francisco A.…[272] | Macroeconomic indicators[265] | K-means; hierarchical clustering[257][247] |
| Network Topology Analysis | Network topology analysis[256] | MST, PMFG and graph kernels[250][256] | Graph edges and centrality guide allocation[248] | Asset-return correlations as graph edges[253] | Market structure, centrality and systemic risk[253][248] | Diversification, allocation and risk management[248] | MST/PMFG portfolio construction[252] | Wang, Xie & Stanley (2018), MST-Pearson/Partial[249][254] | 2016-10-19[249] | Adjusted Rand Index; look-back sensitivity[242] | Degree, closeness, betweenness, eigenvector[248] | ESG profiles, node attributes and edge weights[256] | MST, Asset Graph and PMFG[250] |
| Feature Enrichment | Feature enrichment[205] | Feature engineering[205] | Select, transform, create features[205] | Historical price, market, macro, text data[205][222][108] | Returns, volatility, stock rankings[94][108][234] | Selection, allocation, risk estimation[205] | Return forecasts, selection, rebalancing[94][205][218] | Yun et al. (2021) GA-XGBoost[269] | 2024-01-01[202] | Leakage control, regularization, overfitting risk[94][205] | Feature enrichment in AI-enhanced portfolio management…[201] | News, social media, satellite, geospatial data[217] | Feature engineering, NLP, sentiment[205][217][222] |
| Asset-Return Prediction | The cited deep-learning study uses return prediction… | The cited deep-learning study uses return prediction… | The cited deep-learning study uses return prediction… | 86 technical/fundamental predictors[116] | The cited deep-learning study uses return prediction… | The cited deep-learning study uses return prediction… | The cited deep-learning study uses return prediction… | Heston & Sinha (2017)[205] | 2021-11-12[226] | no evidence found | Asset-return prediction is represented by…[219] | 86 technical/fundamental predictors[116] | The cited deep-learning study uses return prediction… |
| Volatility Prediction | Signal generation [270] | Volatility prediction [270] | Forecast volatility sets weights [270] | 886 U.S. stock returns [230] | S&P 500 volatility [270] | Target-volatility allocation [270] | VaR, risk parity, volatility timing [221][108] | Donaldson & Kamstra (1997) [205] | 2024-04-22 [230] | Out-of-sample R2, QLIKE; target adherence [270] | The source directly identifies volatility prediction…[219] | Return-factor structure (proposed) [219] | GARCH, ANN-GARCH, DCC [205][221] |
| Potential-Asset Selection | Genetic Algorithm [266] | Potential-asset selection via Genetic Algorithm [266] | AI screens market; establishes investable universe [220] | Financial parameters [262]; 100,000 random assets [266] | Potentially profitable constituents [220] | Screen market; establish investable universe [220] | AI market screening before portfolio construction [220] | Predicting stock/index movement (2015) [225] | 2009 [271] | Weight-vector sensitive; greater complexity [274] | The study applies correlation-based network analysis…[214] | News and consumer sentiment [138] | Louvain, MST, K-means, hierarchical clustering [244] |
| Regularized Linear and Factor Forecasting | Signal generation [232] | Ridge regression + random Fourier features [232] | Lagged predictors to timing portfolios [227][232] | 194 factors: value, quality, momentum, growth…[205] | Excess returns and volatility [227] | Market timing; factor-portfolio construction [109][232] | High-dimensional return forecasting and market timing [232] | Rapach & Zhou (2020) [232] | 2020 [232] | Out-of-sample; five-fold CV; noise/overfitting [231][232] | Network analysis may require partial or proxy data…[276] | Macroeconomic and macro-financial data [276] | Ridge/RFF; LASSO; Elastic Net; IPCA [227][109][232] |
| Classical Statistical Time-Series Models | Signal generation [270] | Classical statistical time-series models [237] | Regression-based time-series forecasting [270] | Asset returns and realized variance [221][270] | Returns, variance and covariance [278][221] | Portfolio construction, signals and VaR [237][221][158] | Return and volatility forecasting; VaR/ES [278] | ARIMA/GARCH for India SRI stocks [277] | 2024-02-15 [277] | OOS MAE/RMSE; three-firm scope [221][277] | Correlation matrices; minimum spanning trees [255] | Dividend-price ratio; realized variance [268][270] | ARIMA, ARCH/GARCH, EGARCH, DCC, BEKK [221][237] |
| Deep Sequence Forecasting Models | Signal generation; sequence forecasting[267] | CNN-BiLSTM predictions are used to derive views for…[105] | CNN-BiLSTM predictions are transformed into views…[105] | The source cites “Predicting stock prices using…[204] | CNN-BiLSTM predictions are transformed into views…[105] | CNN-BiLSTM predictions are transformed into views…[105] | CNN-BiLSTM predictions are used to derive views for…[105] | The source cites “Predicting stock prices using…[204] | January 2, 2015[229] | Out-of-sample; costs erode gains[238] | Graphical-lasso adjacency matrix[216] | Online social-network data[275] | CNN-BiLSTM predictions are used to derive views for…[105] |
| Unsupervised Asset Clustering | no evidence found | The page cites Mantegna's 1999 work on hierarchical…[228] | no evidence found | Historical returns, volatility, correlations [246] | no evidence found | Diversification and portfolio allocation [242] | no evidence found | Wu et al. (2022); 105-ETF K-means (2024) [276][244] | 1 December 2025[236] | Silhouette/Dunn checks; initialization-sensitive [243][276] | The page cites Mantegna's 1999 work on hierarchical…[228] | no evidence found | The page cites Mantegna's 1999 work on hierarchical…[228] |
| Correlation-Network Filtering | Asset Clustering and Network Analysis [242] | Correlation-Network Filtering [248] | Correlation-to-distance graph; MST filtering [248] | Rolling return-correlation matrices [248] | Pairwise/partial correlation structure [249] | Diversification and portfolio construction [242][251] | PMFG allocation; centrality-based portfolios [209][210] | Network Risk Parity (2024) [251] | June 10, 2005[211] | Filter-sensitive topology; full matrix best [212][253] | Degree, edge, eigenvector centrality [212][251] | SEC 10-K filings; Doc2Vec embeddings [210] | MST, PMFG, TMFG, community detection [212][242] |
| Financial Feature Families | Feature enrichment[215] | Financial feature families[116] | Features feed models for stock-return prediction[116] | Fundamentals, technicals, sectors, market data[116] | Stock-return prediction[116] | Portfolio construction and weighting[276] | Return and distress prediction[116][205] | Lam (2004); Feng et al. (2017)[222] | 2022-02-23[116] | Task/data-specific; bias needs evaluation[222][215] | Feature enrichment in AI-enhanced portfolio management…[201] | Financial statements, market data, ESG, text[208][116] | no evidence found |
| AI-Enhanced Portfolio Management: Leveraging Machine Learning for Optimized Investment Strategies in 2024 | AI/ML portfolio management [200] | The page identifies a research case titled…[261] | KG embeddings; multitask learning-to-rank [234] | Heterogeneous data; knowledge graphs; Taiwan data [234] | Momentum portfolio ranking [234] | no evidence found | Market-trend prediction [200] | Momentum portfolio selection; learning-to-rank [234] | 2024-03-22 [234] | no evidence found | no evidence found | no evidence found | no evidence found |
| The Role of AI Recommendations in Extending the Black-Litterman Approach | no evidence found | The research lead is titled “The role of AI…[260] | The research lead is titled “The role of AI…[260] | The research lead is titled “The role of AI…[260] | The research lead is titled “The role of AI…[260] | no evidence found | no evidence found | Excluded post-cutoff AI-BL study [260] | 2025-12-06 (post-cutoff) [260] | no evidence found | no evidence found | no evidence found | no evidence found |
| Artificial Intelligence in Financial Portfolio Management Candidate Thesis | AI/ML portfolio management [224] | Neural network; PCA; LOF; Isolation Forest [224] | Feature reduction and anomaly detection [224] | High-dimensional financial data [224] | Market anomalies and relevant features [224] | Portfolio selection and risk management [224] | Anomaly detection; dimensionality reduction [224] | no evidence found | 2025-01-01; May 2023 [223] | Human oversight; transparency and reliability limits [224] | The candidate thesis is a Bachelor’s thesis published…[224] | The candidate thesis is a Bachelor’s thesis published…[224] | PCA; LOF; Isolation Forest; SVM [224] |
| Graph Neural Networks for Asset Networks | Asset clustering and network analysis [106] | Graph neural networks for asset networks [233] | Asset graphs to GNN embeddings to portfolio signals [233] | News relations; ownership, sectors, supply chains [233][106] | Stock movements and asset relationships [233][106] | Stock selection and portfolio construction [233] | Stock selection and portfolio optimization [106][259] | GNNs for deep portfolio optimization (2023) [259] | 2023-07-22 [259] | Nonstationarity; improved versus recurrent models [259] | Sparse adjacency; correlation networks [216][106] | Financial news, ownership, sectors, supply chains [233][106] | Graph neural networks; graph convolution and attention [106] |
| Large-Language-Model or Text-Embedding Features for Portfolio Construction | no evidence found | Explainable text-driven neural network [258] | GPT-3.5 extracts 10-K insights for ML [215] | 10-K filings and historical market data [215] | Stock prediction and movement [215][258] | Inform investment strategies [215] | no evidence found | Explainable text-driven neural network, 2018 [258] | 2020 calendar year[258] | BERT/FinBERT bias; careful evaluation [215] | no evidence found | 10-K filings and historical market data [215] | no evidence found |

Scope here is neural networks, machine-learning models, and natural-language processing used to analyze portfolio performance and optimize asset allocation, risk management, and predictive analytics across developed, emerging, and frontier markets [199]. The EPRA/EBMS AI-portfolio source (DOI 10.36713/epra18874) was published on 2024-11-05 [199], after the inclusive 2024-04-30 cutoff, so it is excluded from substantive evidence. Its abstract proposes—not reports—a mixed-methods framework using secondary data (market reports, financial databases, prior studies) to analyze scenarios and generate recommendations for volatility, liquidity, and regulatory risks; asset class/population, frequency/horizon, benchmark, sample split/walk-forward validation, costs, leakage, and stopping rule are unspecified [199].

**Signal generation and forecasting**

**Signal Generation** maps information available at time \(t\) to a return, volatility, rank, or weight. Supervised regressors predict prices or returns; classifiers predict direction, sign, or return rank; the output supports systematic trading, screening, allocation, or risk control. Return forecasts can feed mean–variance or Omega optimization, while volatility forecasts can determine conditional-risk estimates or inverse-volatility weights. Regime probabilities may shift a 60/40 portfolio to cash, rotate equities and bonds, or add commodities/gold. **Asset-Return Prediction** is represented by Heston and Sinha (2017), **Volatility Prediction** by Donaldson and Kamstra (1997), and **Potential-Asset Selection** by Rasekhschaffe and Jones (2019), all reported in [205].

**High-dimensional forecasting based on linear models**

**High-Dimensional Linear Forecasting** includes OLS and “kitchen-sink” regressions, historical-average forecasts, PLS and sparse PLS, ridge, LASSO, elastic net, penalized generalized linear models, PCA, and the three-pass regression filter; graphical LASSO supplies sparse precision/covariance estimation. Kelly and Pruitt’s three-pass regression filter (2015) is a many-predictor forecasting example, while Tibshirani’s LASSO (1996) provides the regularization and variable-selection method. [205]

**Time-series forecasting**

**Unsupervised structure discovery and feature enrichment**

**Validation and evidence status**

**Cutoff screen.** No substantive claim from this source group is eligible through 2024-04-30. *Machine Learning in Portfolio Decisions* is Working Paper 233, October 2024 (draft 13 October) [205]; the time-series review is explicitly post-cutoff [206]; and the portfolio-optimization article is dated 5 September 2024 [207]. These records are discovery leads/exclusions only.

- **Signal Generation, return prediction and potential-asset selection:** LLM sentiment, scores, stock lists and weights are not established in-scope; target, horizon, portfolio mapping, benchmark and validation remain unavailable here [205][206].
- **High-dimensional/regularized linear forecasting:** LASSO, OLS and three-pass-regression labels are unresolved leads only; no eligible predictors, target, horizon or out-of-sample result is established [205].
- **Time Series Forecasting (classical/deep):** SVR, LSTM/CNN, Transformer and TSF labels are excluded leads; sampling frequency, window, leakage control and portfolio result are not established [205][206].
- **Asset Clustering/Network Analysis and Unsupervised Learning:** K-means, hierarchical clustering and the 2023 pairs-trading citation are not retained as evidence; no eligible distance/graph rule, diversification metric or stability test is established [206][207].
- **Feature Enrichment/Financial Feature Families:** NLP/text, ESG, technical, fundamental and macro features are post-cutoff leads; timing, missingness, leakage and selection controls are not established [205]. **Volatility Prediction:** no eligible standalone forecast, unit, horizon or portfolio use is established in this group [205].

## Multi-Criteria Decision Making (MCDM)

### Extending selection beyond risk and return

**MCDM makes additional objectives explicit.** The traditional mean–variance problem does not, by itself, capture every requirement of an investment mandate. Multi-Criteria Decision Making can incorporate liquidity, social responsibility, growth, profitability, valuation, operational complexity, and investor preferences through weighting, ranking, constraints, or multiple objectives [4].

| Criterion | Example measurement | Portfolio representation | Practical consequence |
|---|---|---|---|
| Liquidity | Daily trades, market turnover, marketability | Ranking criterion or minimum requirement | Improve entry and exit flexibility |
| Social responsibility | Ethical ratings, ESG disclosure or risk scores | Objective, screen, or constraint | Align holdings with the mandate |
| Growth | EPS, profit, and revenue growth | Security or portfolio criterion | Reflect business-development preferences |
| Profitability | EPS, net margin, return on assets | Financial-quality criterion | Favor selected earnings characteristics |
| Other requirements | Beta, valuation, holding count, trading costs | Scores, targets, or feasibility limits | Control exposures and implementation |

The concrete criteria appear in the Zagreb liquidity study [35], Tehran FANP study [36], and multicriteria decision-support system [37].

**Criteria, forecasts, and constraints differ.** An ESG preference need not be a forecast of higher returns. A liquidity minimum can be a feasibility requirement rather than a benefit that investors are willing to trade away. Similarly, a minimum number of holdings addresses a construction requirement that a high security-ranking score does not automatically satisfy.

**Measurement direction must be defined.** A higher ESG disclosure score and a lower ESG-risk score both may be preferred, but they are not the same measure. Growth, profitability, and valuation also overlap economically, creating potential double counting. MCDM makes these choices visible; it does not make them preference-free.

### Techniques and application scenarios

**Different techniques produce different decision objects.** Some estimate criterion weights, some rank a fixed list, and others construct portfolios meeting several goals. Their outputs should not be confused.

| Technique | Main mechanism | Application scenario | Selection output |
|---|---|---|---|
| AHP | Pairwise comparisons in a hierarchy | Ethical scoring; investor priorities | Criterion and alternative weights |
| TOPSIS | Distance from ideal and anti-ideal profiles | Liquidity–risk–profitability selection | A ranked portfolio list |
| ELECTRE III | Concordance, discordance, and veto thresholds | Securities with conflicting financial criteria | Outranking relationships |
| PROMETHEE | Pairwise preference functions and flows | Liquidity-aware share selection | Security or portfolio ranking |
| Fuzzy MCDM | Represent imprecise judgments with fuzzy quantities | Ethical and financial quality assessment | Scores or feasible compromises |
| ANP / FANP | Model dependence among criteria; add fuzzy judgments | Growth–profitability–risk assessment | Dependence-adjusted rankings |
| MAUT | Aggregate attribute-specific utility functions | Preference-aware security selection | Utility-based ordering |
| Goal programming | Minimize deviations from aspiration levels | Return, liquidity, or ethical targets | A goal-balanced allocation |
| SMAA–TOPSIS | Sample uncertain preferences and evaluate rankings | ESG portfolios with uncertain weights | Rank-acceptability probabilities |

The applications are documented in Hanine and coauthors’ framework [38], Xidonas and coauthors’ system [37], and the preference-robust mutual-fund study [39].

**AHP elicits structured preferences.** The Analytic Hierarchy Process, associated with Thomas Saaty and a 1977 development milestone in Hanine and coauthors’ account, compares criteria and alternatives pairwise. Judgments are translated into relative weights, with consistency checks; the Casablanca application uses a consistency-ratio threshold below 0.10. AHP is convenient for hierarchical problems, while ANP is more appropriate when criteria influence one another [38].

**TOPSIS selects a relative compromise.** The Technique for Order Preference by Similarity to Ideal Solution favors alternatives close to an ideal profile and far from an anti-ideal profile. The Colombian application combined AHP weights with TOPSIS over liquidity, risk, and profitability-related criteria using April 2012–April 2017 data. Its selected portfolio held CEMARGOS CB at 34.5% and EEB CB at 65.5% [4].

**A high ranking need not diversify.** The Colombian result is a two-stock portfolio, illustrating the distinction between preference fit and broad diversification. Moreover, AHP alone and AHP–TOPSIS selected different first choices, even though their leading three alternatives overlapped. The aggregation rule can therefore change the decision alongside the criterion weights.

**Outranking permits structured disagreement.** ELECTRE III evaluates whether sufficient evidence supports one alternative over another while recognizing strong disadvantages or vetoes. PROMETHEE aggregates pairwise preference strengths into flows. These approaches are useful when an investor does not want a serious weakness on one criterion to be automatically offset by small advantages on several others.

**Liquidity has a concrete portfolio outcome.** The Zagreb PROMETHEE application incorporated average daily trades and average daily market turnover. Including those criteria increased portfolio liquidity, particularly after 2019, without producing significantly different returns from the comparison excluding liquidity. This is a useful result even without a return premium: the stated objective was improved tradability [35].

**Fuzzy methods represent imprecise assessments.** Hanine, Tkiouat, and Lahrichi combined AHP ethical scores, fuzzy financial-quality assessment using short- and long-term return and risk, and interactive fuzzy programming for Casablanca portfolios. Their socially responsible portfolio achieved ethical objectives with similar returns and a slight financial sacrifice [38].

**Goal programming works with aspiration levels.** Rather than ranking every possible combination, it seeks allocations that minimize weighted deviations from specified goals. Interactive programming allows investors to revise those goals as trade-offs become visible, while stochastic programming represents probabilistic scenarios. Hanine and coauthors’ literature inventory contained 11 goal-programming articles and eight fuzzy mathematical-programming articles; these are application counts, not rankings of effectiveness.

**Additional tools structure the preference problem.** Multi-Attribute Utility Theory, MAUT, combines attribute-specific utilities. The Decision-Making Trial and Evaluation Laboratory, DEMATEL, maps influences among criteria, while modified Delphi procedures build expert agreement on which criteria matter. ANP and fuzzy ANP then accommodate dependence and linguistic uncertainty; these tools support preference construction rather than forecasting market returns [36].

### Growth, profitability, and ESG case results

**FANP explicitly represents interdependent criteria.** Rahiminezhad Galankashi, Mokhatab Rafiei, and Ghezelbash’s 2020 Tehran study combined literature-based criteria, expert questionnaires, and fuzzy Analytic Network Process rankings. Profitability included EPS, net profit margin, and return on assets; growth included EPS, net profit, and revenue growth. The complete ranking of its ten alternatives was:

| Rank | Portfolio |
|---:|---|
| 1 | A6 |
| 2 | A7 |
| 3 | A2 |
| 4 | A4 |
| 5 | A8 |
| 6 | A1 |
| 7 | A5 |
| 8 | A3 |
| 9 | A9 |
| 10 | A10 |

The ranking reflects the study’s criteria and decision-maker judgments, with A6 the recommended alternative [36].

**ESG can form a third objective.** A 2019 fuzzy multicriteria study optimized expected return, expected ESG score, and downside risk using 29 Dow Jones Industrial Average companies. Its estimation sample contained 203 weekly observations from February 2014–December 2017, and admissible portfolios contained ten holdings, each bounded between 5% and 30%, with full investment and no short selling [40].

**The efficient set exposes genuine trade-offs.** The study used the Non-dominated Sorting Genetic Algorithm II, NSGA-II, to generate portfolios for which improving one objective requires worsening another. A credibilistic Sortino ratio then selected a portfolio from that set. Its January–December 2018 comparison with the DIA exchange-traded fund reported favorable return, value-at-risk, and ESG differences, printing the comparison figures as “1.007, 729 and 25 bps,” respectively [40].

**Uncertain preferences can produce probabilistic rankings.** Garcia-Bernabeu and coauthors combined a multiobjective genetic algorithm, AHP preference elicitation, and stochastic multicriteria acceptability analysis with TOPSIS. Their socially responsible mutual-fund application used January 2011–December 2016 for estimation and January 2017–December 2019 for out-of-sample evaluation.

| Dataset | Funds | Estimation months | Evaluation months | Non-dominated portfolios |
|---|---:|---:|---:|---:|
| Fund Manager 1 | 35 | 72 | 36 | 606 |
| Fund Manager 2 | 16 | 72 | 36 | 356 |
| Fund Manager 3 | 14 | 72 | 36 | 1,145 |

These are separate fund-manager datasets and their generated efficient sets [39].

**Rank acceptability measures preference robustness.** For Fund Manager 2 and the finance-oriented aggressive profile, FIN–agg, portfolio a17 had a 30.7% probability of ranking first and a 98.8% probability of ranking in the top ten, with reported rank-distribution barycenter 2.7. These probabilities describe how rankings respond to uncertain preference weights; they are not probabilities of achieving investment returns [39].

### Integrating MCDM with AI forecasts and optimization

**Ranking and weighting should remain separate.** Xidonas, Doukas, and Sarmas’s 2021 decision-support system first applies PROMETHEE II, ELECTRE III, MAUT, and TOPSIS to security evaluation. It then uses mixed-integer quadratic programming, goal programming, genetic algorithms, or a multiobjective PROMETHEE formulation for portfolio construction [37].

**AI can estimate criterion values.** ML forecasts can populate expected-return, liquidity, financial-quality, or ESG-related inputs. MCDM then expresses investor priorities, while optimization ensures that the chosen allocation satisfies budget, position, and diversification constraints. This separation prevents a predictive model from silently determining preferences that should belong to the investor.

**Preference stability determines ranking stability.** Normalization, correlated criteria, and changing weights can alter rankings. The mutual-fund study’s four fixed profiles—FIN–con, FIN–agg, ESG–awa, and ESG–mot—illustrate a manageable design, but a fixed profile may cease to describe the investor when circumstances change [39].

**MCDM is appropriate when trade-offs matter.** Its strongest contribution is an auditable connection between a mandate and the selected portfolio, with the conclusion changing when preferences, criterion measurements, or feasibility requirements change.

**Additional documented evidence**

| Entity | MCDM technique name | MCDM criteria | MCDM application scenario | MCDM mechanism | Representative MCDM research | MCDM limitations | Relation to risk-return baseline | MCDM technique catalog | AI integration in MCDM |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Multi-Criteria Decision Making (MCDM) Methods | The source contributes a pre-May-2024 summary of MCDM…[286] | The source contributes a pre-May-2024 summary of MCDM…[286] | The source contributes a pre-May-2024 summary of MCDM…[286] | The source contributes a pre-May-2024 summary of MCDM…[286] | The source contributes a pre-May-2024 summary of MCDM…[286] | The source contributes a pre-May-2024 summary of MCDM…[286] | The source contributes a pre-May-2024 summary of MCDM…[286] | The source contributes a pre-May-2024 summary of MCDM…[286] | LSTM ranking; adaptive weights; Q-learning [362][366] |
| Analytic Hierarchy Process | Analytical Hierarchy Process (AHP) is identified as…[301] | no evidence found | no evidence found | no evidence found | Jawad, Naz & Muqaddus, JORS 2024[373] | no evidence found | no evidence found | Analytical Hierarchy Process (AHP) is identified as…[301] | no evidence found |
| Technique for Order Preference by Similarity to Ideal Solution | TOPSIS is identified as an MCDM technique for project…[297] | TOPSIS is identified as an MCDM technique for project…[297] | TOPSIS is identified as an MCDM technique for project…[297] | TOPSIS is identified as an MCDM technique for project…[297] | Chang et al. (2010) extended TOPSIS [296] | no evidence found | TOPSIS is identified as an MCDM technique for project…[297] | The source names VIKOR, AHP, TOPSIS, and ELECTRE as…[362] | TOPSIS is identified as an MCDM technique for project…[297] |
| ELECTRE | no evidence found | no evidence found | no evidence found | no evidence found | Emamat et al., TSE ELECTRE-TRI study (2022) [305] | Incomparability; threshold sensitivity; selection only [305] | no evidence found | no evidence found | no evidence found |
| PROMETHEE | PROMETHEE is one of the main methods covered under…[263] | no evidence found | The source names VIKOR, AHP, TOPSIS, and ELECTRE as…[362] | PROMETHEE is identified as a preference-ranking method.[305] | The page provides a general PROMETHEE method source…[305] | no evidence found | no evidence found | PROMETHEE is one of the main methods covered under…[263] | no evidence found |
| VIKOR | VIKOR is associated with compromise solutions in…[305] | no evidence found | VIKOR is represented by “VIKOR METHOD WITH Z-NUMBER…[363] | VIKOR is associated with compromise solutions in…[305] | Tarmudi et al. (2024-04-01), Z-number VIKOR[317] | no evidence found | Adds criteria and compromise beyond risk-return[306] | The page cites a comparative study titled “Compromise…[263] | no evidence found |
| Fuzzy MCDM | The source contributes a pre-May-2024 summary of MCDM…[286] | The source contributes a pre-May-2024 summary of MCDM…[286] | The source contributes a pre-May-2024 summary of MCDM…[286] | The source contributes a pre-May-2024 summary of MCDM…[286] | The source contributes a pre-May-2024 summary of MCDM…[286] | Imprecise judgments; computation-heavy [302] | The source contributes a pre-May-2024 summary of MCDM…[286] | The source contributes a pre-May-2024 summary of MCDM…[286] | The source contributes a pre-May-2024 summary of MCDM…[286] |
| Goal Programming | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | Mixed SRI results; CCP data demands[320] | no evidence found | no evidence found | no evidence found |
| Analytic Network Process | no evidence found | Financial/nonfinancial criteria; dependencies[299] | no evidence found | Pairwise comparisons; supermatrix priorities[296] | Portfolio selection: A fuzzy-ANP approach (2020)[376] | Subjective pairwise judgments; CR <0.1[296] | no evidence found | ANP, FANP, DEMATEL, VIKOR, TOPSIS[299][304] | Analytic Network Process (ANP), and its fuzzy…[299] |
| DEMATEL | no evidence found | DEMATEL evaluates the importance and causal…[300] | no evidence found | DEMATEL evaluates the importance and causal…[300] | Jeng & Huang: DEMATEL+ANP+Delphi (2015)[299] | Inability to handle uncertainty[311] | no evidence found | no evidence found | no evidence found |

**MCDM beyond risk and return**

Pre-cutoff evidence includes Ehrgott, Klamroth and Schwehm’s *An MCDM approach to portfolio optimization* (16 June 2004): five attributes used decision-maker-specific utilities and an additive global utility; fuzzy inputs and non-convexity required heuristics [288]. Steuer, Qi and Hirschberger’s 2006 work records the multi-attribute extension [287]. A DSS published 2020-12-02 ranked securities with PROMETHEE II, ELECTRE III, MAUT and TOPSIS, then used MIQP, GP, a genetic algorithm and multiobjective PROMETHEE flow across several markets and sectors [289].

**Criteria and method evidence**

| Method | Supported portfolio answer |
|---|---|
| **AHP** | Hierarchy of goals, criteria, subcriteria, and alternatives; pairwise expert priorities; fuzzy variants address uncertainty [290]. |
| **TOPSIS** | TOPSIS plus a Bayes model selected profitable, low-risk stocks among 100 NSE firms; AHP–TOPSIS covered Colombia, 2012–2017 [290]. |
| **ELECTRE** | Named for investment portfolios; a pre-cutoff mechanism or application is not established [290]. |
| **VIKOR** | Named for portfolio decisions [290]; the detailed fuzzy study is dated 2024-09-10 and excluded [291]. |
| **PROMETHEE** | The supplied record reports 2020 group/green-supplier examples, but is post-cutoff; eligible portfolio use is unestablished [291]. |
| **Fuzzy MCDM** | IFAHP encodes membership, non-membership, and hesitation for imprecise mixed criteria and ranks portfolios; post-COVID and uncertain selection are also cited [290]. |
| **Goal Programming** | An intuitionistic-fuzzy multiobjective version is cited for portfolio selection; objectives and validation are unavailable [290]. |

MCDM ranks return, risk, liquidity, stability and preferences, extending risk–return; GP/optimization handles allocation and constraints [295]. Liquidity is average daily traded volume in local currency, with a monthly minimum screen [116]. Growth is capital growth/income [295]; in Brazilian equities (Jan 2003–Dec 2018), two growth indicators were top-ten ML predictors [116]. ESG adds environmental, social and governance scores; one study converted 12 rating levels to 12–1, selected higher-ESG assets with return/risk, and reported a return–volatility trade-off [240].

Goal Programming (GP) minimizes weighted, normalized deviations from aspiration levels; weighted, lexicographic, MiniMax, fuzzy, stochastic, imprecise, robust, interactive, compromise and chance-constrained variants cover portfolio, index-tracking, multistage and SRI cases [295]. Fuzzy/interactive GP admits imprecise goals and expert judgment via satisfaction functions [295]. Limits are preference/weight sensitivity, vague goals, incomplete data and uncertain dynamic markets [295]. AHP, TOPSIS, ELECTRE, VIKOR and fuzzy MCDM remain candidate rows; shown application records are post-cutoff (2025-10-02, 2024-05-31 and September 2024) and excluded [292][293][294]. ML supplies financial features here; adaptive method weights are not established [116].

MCDM: return/risk plus criteria; profile sorting selects stocks, while allocation needs multiobjective/goal programming [263]. AHP=pairwise weights; TOPSIS=compromise rank; port unknown; ELECTRE=outranking/veto (Tehran, 2022-02-03: 50 companies/8 criteria/3 groups; incomparability, veto poor); PROMETHEE/FlowSort=weighted profiles/thresholds [263]. VIKOR=2004 compromise, portfolio use unknown; fuzzy MCDM=models imprecision; ANP=2020 fuzzy-ANP portfolio; DEMATEL=2011 CAPM model; ESG/social=2014 FlowSort fund; growth=indirect only [263]

VIKOR 2016: fuzzy compromise ranking; 5 pharma/6 criteria/3 judges; IFWA→PIS/NIS→S,R,Q [306]. MCDM: linguistic uncertainty; fuzzy-AHP 2023; 2026 excluded [307]. PROMETHEE: Brans 1982, outranking; stocks 2007 [308][309]

DEMATEL→ANP weights→TOPSIS top-30 [310][311]; VIKOR fuzzy S/R→Q compromise [312][314]; PROMETHEE I/II partial/complete [313]; AHP weights/TOPSIS ideal-distance [316]; GP minmax/weighted [315].

VIKOR: normalized S+R→Q; Tehran 2007–10 ranked 56 stocks on profitability/liquidity/leverage/efficiency/market [318]. PROMETHEE uses pairwise outranking [321]; fuzzy MCDM handles vague weights; goal programming adds ESG [319][320]. AI supplies inputs [317].

US ETFs (2016–23): MV–L uses AveVol/Amihud/KO/CVVol; reciprocals of the last three are weighted liquidity indicators. It minimizes ½σ² with μ≥M, liq≥L, budget, w≥0; 2016–22 fit/2023 OOS finds tighter liquidity lowers risk but can reduce KO/CVVol diversification [328]. RL/XAI: liquidity ratio/exposure, leverage, VaR, drawdown, horizon, frequency, accuracy and costs [351][284]. Filters/objectives/screening improve investability [328][333]; Tobin 1956/58 [336]. 49 FTSE RAFI indexes (20 Mar 2019) imply ≈30 bps per 10% ADV; turnover concentration raises cost [332]. ESG uses fuzzy scores or NLP (disclosures/sentiment/greenwashing); ratings vary by scope/measurement/weights [344][205]. Growth uses business size + 20% banding/seasoning [334], or RF/PCA/regression: 30 of >200 factors, five CSI-800 groups (2019–Apr 2023) [327]. HFS/intuitionistic fuzzy, three-way, outranking/CVaR address preference/uncertainty: scenario-tree 2018, CVaR 2000, worst-case CVaR 2009, sustainable/three-way fuzzy 2023 [344]. 2025 BIST AHP/TOPSIS/DEA/VIKOR and NEPSE-Feb-2025 are excluded [358][175].

MCDM extends mean–variance with liquidity, diversification, entropy, skewness/kurtosis; criteria are normalized, weighted or constrained [359]. Liquidity uses volume/liquidation constraints; tighter liquidity raises risk [350]. AHP (2013) pairwise-ranks portfolio assets; AI can supply fuzzy criteria/expert weights [359]. GP handles conflicting return–risk–liquidity, 1970s–2014 [338].

MCDM adds liquidity/ESG to risk–return [340][360][256]. Growth: random-forest value/growth timing [331]. Liquidity = cash-conversion probability; NYSE/B3 tests (2005–2019) allowed 0–40% low-liquidity exposure [147]. ESG screening of S&P500 assets (2016–2022; 2024-04-16) used graph kernels; max-Sharpe optimization could reverse rankings [256]. Goal Programming combines return/risk/liquidity; ANP links behavioural/MiFID criteria and Choquet-aggregates experts [360][352]. AHP/TOPSIS/ELECTRE/PROMETHEE/VIKOR/Fuzzy-MCDM/DEMATEL: eligible evidence not established.

Asset Growth=AT/AT−12; 10 deciles, long low/short high [158]. Capacity conflict: MCDM obligations exceed 121 characters.

**Methods/status:** AHP—pairwise normalized weights; eligible example is AV-risk, not portfolio [364]. TOPSIS—ideal similarity; post-cutoff portfolio lead only [363]. VIKOR—normalized compromise; lower score preferred [364]. Fuzzy MCDM—uncertain criteria; post-cutoff lead only [363]. Goal Programming—multiple goals; 2019 entropy/higher-moment lead only in a post-cutoff source [346]. ELECTRE, PROMETHEE, ANP and DEMATEL remain candidate rows; AI adaptive-weight/feedback claims are post-cutoff [362].

MCDM baseline: expected return↑/SD↓; use risk-adjusted or target-risk forms [127]. Liquidity: 116 Spanish stocks, Jan 1991–Dec 2004; Amihud high/low return 0.0151/0.0105, Sharpe 0.2050/0.1721; bid–ask liquidation cap 1% [345][129]. ESG: third return/risk objective, holding bounds and client filters; NLP/CSR reports yield assessments [330][208][281]. Growth: sales/earnings-growth inputs enter random-forest next-return forecasts [322].

**Methods:** AHP—hierarchy/pairs, spherical-fuzzy consistency; Pakistan Stock Exchange (2024) [373]. ELECTRE III—CBR ranks Thai stocks by reference similarity/ICB; Roy 1978; outperformed traditional method [367]. VIKOR—intuitionistic-fuzzy IFWA plus compromise ranking; practical portfolio selection; date unavailable [368]. Goal Programming—target-deviation minimization; 11 models and Sharpe/Treynor evaluation; ANP-GP adds economic, environmental and social targets in a 2016 automotive-supplier case [369][365]. ANP—434 studies (2012–21), >80% multimethod; fuzzy-ANP portfolio study (2020). DEMATEL-ANP—organizational action portfolio to 2030, not financial/AI [371][370]. Fuzzy MCDM—2010 lead; portfolio use unestablished [342]. Post-cutoff liquidity/ESG records are excluded [329][323][138][280][282].

ESG: data/constraints [94]; ESG-AI framing excluded [279]. Growth: Kelly56 log-wealth, CVaR≤γ, risk+growth; frac-Kelly curbs drawdown [375][374][324]. Baseline: return↑|σ fixed or σ↓|return fixed [339][361]. PROMETHEE→portfolio selection,2011; GP→enhanced index,2007 [372][285]. FANP/ANP→rank 10 TSE portfolios; profitability/growth/market/risk,2020; source 2009/2018 [376][377]. Unknown fields.

Multi-Criteria Decision Making (MCDM) Methods provide the decision layer for AI-enhanced portfolio management: they rank portfolio alternatives against financial and non-financial criteria rather than only return and risk, making conflicting objectives and investor preferences explicit [355][262]. Under uncertainty, IFAHP combines quantitative and qualitative criteria, converts verbal judgments into quantitative equivalents, and weights and prioritizes alternatives; machine-learning integration is proposed to improve prediction [290].

Liquidity Criterion extends liquidity-integrated Modern Portfolio Theory (MPT): liquidity may be implemented by filtering, a liquidity constraint, or a mean–variance–liquidity model alongside return and risk [157][328]. Average daily traded volume sets a minimum screen that excludes assets too illiquid for realistic trading [116]; liquidity-aware portfolios can vary low-liquidity participation from 0% to 40% with similar return–risk performance and better liquidity, while AI/ML uses liquidity variables for security metrics, execution, and preemptive risk mitigation [147][205][284].

Social Responsibility / ESG Criterion extends risk–return selection into the ESG-integration framework, treating return, risk, and sustainability as a three-criterion problem and using ESG scores, factor loadings, or exclusion; integration is superior to exclusion with all other factors held constant [325][326][293]. ML/NLP can classify sustainability disclosures, analyze sentiment, and detect greenwashing for ESG-constrained construction and risk models [205][353]; this enables preference-aware screening, but direct ESG targeting may reduce risk-adjusted performance [240][122].

Growth Criterion changes a return–risk screen into a multi-criteria/FANP framework in which Growth joins Profitability, Market, and Risk; its three subcriteria are revenue growth, earnings-per-share growth, and sales growth [358][299][290]. A screen can require at least 10% year-over-year growth for eight consecutive quarters, while random-forest factor timing makes growth signals a dynamic allocation input [341][331].

Traditional Risk-Return Dual Objectives remain the baseline: mean–variance optimization balances expected return and variance, volatility proxies uncertainty, and the Sharpe ratio measures risk-adjusted performance [109][108][348]. AI-enhanced management should retain this core but add MCDM scoring/filtering and constraints such as liquidity, because the risk–return trade-off weakens as market volatility rises [292][343][335].

Analytic Hierarchy Process (AHP), developed in 1980, is a hierarchical MCDM framework: it decomposes portfolio selection into a goal, criteria/subcriteria, and alternatives, uses pairwise comparisons to derive normalized weights and test consistency, and ranks alternatives [290][347][299]. It can supply investor-preference weights to TOPSIS/GRA and fuzzy portfolio workflows [357][325][337], but expert subjectivity, ignored inter-criterion links, and consistency/cognitive-load burdens motivate fuzzy AHP/ANP and BWM extensions [349][299][356].

Technique for Order Preference by Similarity to Ideal Solution (TOPSIS), developed in 1981, is a distance-based MCDM framework: it normalizes and weights criteria, identifies positive- and negative-ideal solutions, and ranks alternatives by shortest distance to the positive ideal and longest distance from the negative ideal [303][298][357]. It supports AI-enhanced stock, fund, and ESG selection through fuzzy TOPSIS [283][354], but AHP/TOPSIS calculations become time-consuming as criteria, subcriteria, and alternatives increase [302].

## Portfolio Optimization and Rebalancing

### Risk objectives, estimation, and constrained construction

**An optimizer requires a specified objective.** Better forecasts do not uniquely determine a portfolio. A manager still must choose how to measure risk, whether to express uncertainty about inputs, and which trading or mandate constraints to impose.

| Objective or risk measure | What it measures | Suitable application | Optimization consequence |
|---|---|---|---|
| Variance | Dispersion around expected return | Symmetric risk–return trade-offs | Convex quadratic formulation under standard constraints |
| Semivariance / downside deviation | Adverse deviations below a reference level | Shortfall-sensitive investors | Focus on downside outcomes |
| Value at Risk, VaR | A loss quantile at a specified horizon | Loss-limit reporting | Does not describe losses beyond the quantile |
| CVaR / Expected Shortfall | Average loss in the worst tail fraction | Tail-risk-sensitive allocation | Scenario formulations can be tractable |
| Mean absolute deviation | Average absolute dispersion | Alternative risk representation | Supports linear-programming formulations |
| Minimax / safety-first | Worst outcomes or target-shortfall probability | Capital-protection objectives | Changes the definition of acceptable risk |
| Higher-moment models | Skewness and kurtosis as well as dispersion | Asymmetric or heavy-tailed returns | Can introduce nonconvex objectives |

These alternatives are reviewed in Chen, Zhao, and Yuan’s portfolio-model overview [41].

**Risk choice changes the investment solution.** Variance treats upside and downside deviations symmetrically. Expected Shortfall addresses the severity of tail losses, while safety-first rules focus on falling below a specified target. Higher-moment and prospect-theory models can represent preferences that a mean–variance objective does not capture. AI can estimate the necessary distributions or scenarios, but the risk criterion remains a modeling and mandate choice.

**Estimation improvements can precede algorithm changes.** Covariance shrinkage and factor structures reduce the burden of estimating a large unrestricted covariance matrix. Bayesian approaches and Black–Litterman blend information rather than treating each estimated return as exact. Robust formulations instead evaluate allocations against adverse inputs within a defined uncertainty set. These approaches address model uncertainty, whereas faster optimization primarily addresses computation [5].

**Ordinary bounds do not create hardness.** A mean–variance problem with a positive-semidefinite covariance matrix, full investment, long-only weights, and ordinary linear position bounds remains a convex quadratic program. Discrete inclusion decisions, conditional minimum positions, fixed trading charges, and other nonconvex features change the problem substantially.

**Cardinality introduces binary selection.** If \(z_i\) indicates whether asset \(i\) is held, a typical constrained construction includes:

$$\mathbf{1}^{\top}w=1,\qquad l_i z_i\leq w_i\leq u_i z_i,\qquad \sum_i z_i\leq K,\qquad z_i\in\{0,1\}.$$

**The constraints represent real decisions.** \(K\) limits the number of holdings; conditional lower bounds prevent uneconomically small positions; upper bounds control concentration. Additional constraints can limit portfolio turnover, sector or asset-class exposure, round lots, short selling, and ESG characteristics. Cardinality-constrained quadratic portfolio problems belong to the difficult mixed-integer class motivating approximate search methods [42].

### Metaheuristics Optimization: algorithms and applications

**Metaheuristics search difficult feasible sets.** They maintain either one evolving solution or a population of candidate portfolios and use structured randomness, neighborhood moves, selection, or learning rules to improve solutions. They can accommodate realistic objectives and constraints, but they do not generally certify global optimality [43].

**Evolutionary and local methods have distinct roles.**

| Algorithm | Search mechanism | Portfolio formulation | Representative application |
|---|---|---|---|
| Genetic algorithm, GA | Selection, crossover, mutation | Cardinality and position-constrained allocation | Xidonas DSS; Nikiporenko comparison |
| Differential evolution, DE | Difference-based mutation and recombination | Budgeted continuous and multiobjective weights | Krink–Paterlini DEMPO; Yıldız comparison |
| Simulated annealing, SA | Accept some worsening moves while cooling | Cardinality-constrained mean–variance | Crama–Schyns; Nikiporenko |
| Tabu search, TS | Neighborhood search with memory | Constrained asset selection and sizing | Nikiporenko comparison |
| NSGA-II | Nondominated sorting and diversity preservation | Return–risk–ESG with cardinality and bounds | 2019 fuzzy ESG portfolio study |
| ev-MOGA | Multiobjective evolutionary approximation | Fully invested mean–variance–ESG allocation | Garcia-Bernabeu mutual-fund study |
| MOEA/D | Decompose objectives into scalar subproblems | Multiobjective portfolio weights | Applications reviewed by Chen et al. |

The applications appear in the decision-support study [37], time-limited comparison [42], swarm/evolutionary overview [41], and Yıldız’s 2022 comparison [44].

**Swarm methods offer alternative search dynamics.**

| Algorithm | Search mechanism | Portfolio formulation | Representative application |
|---|---|---|---|
| Particle swarm, PSO | Move candidates using personal and group bests | Mean–variance, mixed-integer, cardinality constraints | Chen et al.; Liang–Qu; Zhao et al. |
| Ant colony, ACO | Construct selections using learned pheromone values | Budget-constrained combinatorial selection | Doerner et al., 2004 Pareto ACO |
| Artificial bee colony, ABC | Explore and exploit candidate regions | Cardinality-constrained mean–variance | Tuba–Bacanin ABC–firefly hybrid |
| Grey wolf, GWO | Update candidates using leading solutions | Equity allocation and risk control | Mazumdar et al. |
| Firefly, FA | Attraction-based search among candidates | Fuzzy and multiperiod constrained portfolios | Chen et al.; Lu et al. hybrids |
| Fireworks, FWA | Local and broad searches around explosions | Constrained mean–variance and mean–VaR/CVaR | Zhang–Liu; Bacanin–Tuba |

These families and applications are described in the 2022 overview [41], ABC–firefly study [45], and portfolio-comparison references [44].

**Constraint handling remains essential.** A search algorithm does not automatically preserve full investment, cardinality, or position bounds. Implementations need feasible encodings, repair operations, projection, penalties, or dedicated local subproblems. Consequently, two implementations with the same algorithm name can behave differently because they handle feasibility and continuous weight sizing differently.

**GA and PSO are widely used.** A 2023 review covering more than 140 studies published over 1993–2023 identified genetic algorithms and particle swarm optimization as the most popular choices. Popularity provides evidence of application breadth, not proof of superior solutions [46].

**PSO has large-universe examples.** Introduced by Kennedy and Eberhart in 1995, PSO represents portfolios as particles whose positions and velocities respond to individual and collective experience. Liang and Qu’s dynamic multi-swarm work evaluated portfolios with 200 and 500 assets; the reviewed literature also includes mixed-integer and cardinality-constrained PSO formulations [41].

**DE has concrete portfolio applications.** Krink and Paterlini’s DEMPO is a multiobjective differential-evolution method for portfolio optimization. Yıldız’s 2022 study separately compared PSO, DE, and ABC using 30 BIST30 stocks and daily closing prices from December 2016–December 2017, evaluating portfolio variances. These are specific uses of DE; they do not establish a common cross-market performance ranking [41][44].

**ACO naturally addresses discrete selection.** Doerner and coauthors’ Pareto ACO work provides a representative combinatorial portfolio-selection application. Its construction logic is well matched to deciding which items enter a budgeted portfolio. Continuous financial weight sizing remains a separate modeling issue, so combinatorial-selection results should not be interpreted automatically as trading-strategy performance.

**GWO and firefly methods have distinct examples.** The 2022 overview describes Mazumdar and coauthors’ grey-wolf approach to equity portfolio construction and unsystematic-risk optimization. It also describes multiobjective firefly applications to fuzzy portfolios and a firefly–symbiotic-organism-search hybrid for a multiperiod model with cardinality and liquidity constraints [41].

**Optimization can also occur upstream.** Chen and coauthors’ 2021 two-stage application used an improved firefly algorithm to tune XGBoost hyperparameters before stock-price prediction. This is an optimization contribution to the forecasting stage, not evidence that firefly directly optimized portfolio weights [46].

### Comparative results and algorithm choice

**Time limits can change algorithm rankings.** Nikiporenko’s 2023 comparison tested SA, TS, and GA under one-, five-, and 25-second limits on weekly historical datasets from 1992–1997:

| Dataset | Assets |
|---|---:|
| Hang Seng | 31 |
| DAX-100 | 85 |
| FTSE-100 | 89 |
| S&P-100 | 98 |
| Nikkei-225 | 225 |

**SA led that particular comparison.** It found near-optimal solutions within five seconds on four of the five datasets, while GA produced the lowest-quality solutions among the tested implementations. The result concerns computation time and objective quality under the study’s cardinality-constrained formulation, rather than a universal ranking of investment returns [42].

**Hybrids can improve search behavior.** Tuba and Bacanin combined ABC with firefly search to address ABC’s slow convergence toward promising regions. On standard benchmark data, the hybrid improved solution quality relative to GA, SA, TS, and PSO, particularly using distance from a reference efficient frontier. Fireworks applications also reported improvements in accuracy, speed, and stability relative to classical GA in their tested formulations [45][41].

**Multiobjective algorithms return a set.** NSGA-II and related evolutionary methods approximate a Pareto frontier rather than identify one preference-free winner. The return–risk–ESG study’s ten-holding, 5%–30% position-bounded problem is a concrete example. MCDM or another explicit preference rule must then select among the resulting efficient portfolios [40].

**The best solver depends on structure.** Convex programming is attractive when the actual constraints remain tractable; mixed-integer methods are valuable when solution bounds or certificates matter; metaheuristics become attractive when realistic nonconvex models must be solved within limited time. A practical algorithm comparison should distinguish objective quality, feasibility, runtime, stochastic variability, and investment performance rather than combine them into one undifferentiated score.

### Dynamic Rebalancing Strategies: triggers, targets, and costs

**Rebalancing contains several separate decisions.** A calendar or threshold rule determines when to trade; strategic or tactical allocation determines how targets change; full or gradual adjustment determines the destination. These dimensions can be combined. Constant-mix, for example, can be implemented on a calendar or with tolerance bands.

| Strategy | Trigger | Weight-adjustment rule | AI/ML contribution | Cost treatment |
|---|---|---|---|---|
| Buy-and-hold | No routine active trigger | Let weights drift | Risk monitoring | Low rebalancing turnover |
| Constant-mix | Chosen dates or bands | Restore fixed target proportions | Optional risk estimates | Trade only under implementation rule |
| Calendar | Fixed schedule | Restore current targets | Update target inputs | Frequency trades tracking against costs |
| Threshold / band | Allocation deviation breaches a band | Move toward target or chosen destination | Estimate risk and trading conditions | Skip small deviations |
| Calendar plus threshold | Scheduled observation and band breach | Trade only after both conditions | Adapt inputs at review dates | Avoid automatic scheduled trades |
| Strategic allocation | Mandate or long-term policy review | Maintain long-run allocation | Support risk and scenario analysis | Use a separate execution rule |
| Tactical allocation | Forecast or relative-value signal | Tilt strategic weights | Return or regime classification | Constrain active positions and turnover |
| Volatility / regime-based | Risk or state update | Adjust exposure or risk budgets | GARCH, HMM, regime classifiers | Include trading penalties and limits |
| Reinforcement learning | Sequential policy decision | Choose feasible trades from current state | Learn state-dependent actions | Include costs in reward or wealth dynamics |

The calendar/band taxonomy comes from Zhang and coauthors [26]; strategic/tactical and learned implementations are illustrated in the LSTM–RL study [28].

**Portfolio drift is mechanical.** Without intervening cash flows or trades, a previously chosen weight changes as constituent assets earn different returns:

$$\tilde{w}_{i,t}=\frac{w_{i,t-1}(1+r_{i,t})}{1+\sum_j w_{j,t-1}r_{j,t}}.$$

**Constant-mix restores proportions after drift.** At each selected rebalance, the manager sets the post-trade weights back to \(w^*\). The rule sells relative winners and buys relative losers, unlike buy-and-hold, which allows winners to become larger positions. Its outcome depends on return paths and costs: repeated reversals and persistent trends create different consequences. The fixed-target calendar and threshold rules in Zhang and coauthors provide implementations of this allocation logic [26].

**Calendar rules emphasize operational simplicity.** More frequent restoration usually reduces deviations from target but creates more trading, absent cash flows that help rebalance. Threshold rules instead tolerate controlled drift and act when the deviation becomes meaningful; continuous or daily monitoring is part of the implementation considered by Vanguard. Calendar-plus-threshold rules reduce the monitoring requirement by checking on selected dates.

**Annual rebalancing has a conditional result.** Zhang and coauthors maximize expected utility of wealth after modeled trading costs. In their setting, monthly or quarterly calendar rebalancing was too frequent and two-year rebalancing too infrequent; annual rebalancing was optimal for investors without tax-loss harvesting or tight benchmark-tracking requirements, such as passive funds-of-funds [26].

**Costs should respond to market conditions.** Vanguard modeled bid–ask-related transaction costs as sensitive to volatility, reporting adjusted \(R^2\) above 87% for explained transaction-cost variability. That statistic concerns a cost model, not return-prediction accuracy. Its importance is that the same trade can have a different economic justification in calm and stressed markets.

### AI-enabled tactical and regime-based rebalancing

**AI can modify conviction instead of direction.** Runde’s tactical study starts with a 40% U.S.-equity/60% government-bond benchmark and base active allocations of ±10 percentage points. Agreement between the ML and base signals can multiply the active position by 1.25; disagreement can reduce it using a 0.75 multiplier.

**The weight arithmetic is transparent.** For a base recommendation favoring equities, the source parameters imply the following conditional allocations:

| Implementation | Equity calculation | Equity weight | Bond weight |
|---|---|---:|---:|
| Base recommendation | \(40\%+10\%\) | 50.0% | 50.0% |
| BOOST overlay | \(40\%+1.25\times10\%\) | 52.5% | 47.5% |
| CUT overlay | \(40\%+0.75\times10\%\) | 47.5% | 52.5% |

These are worked allocations from the reported parameters, not return forecasts [29].

**The reported added value was simulated.** Over March 1993–July 2023, the preferred overlay added approximately 20–30 basis points per year to the modeled base approach. The study generated approximately 10,000 base-recommendation paths constrained to a 60% success rate, rather than reconstructing a 30-year live recommendation history. It also reported relative drawdowns lasting more than a year and reaching approximately −46 basis points [29].

**Regime detection can feed forward-looking control.** Nystrup, Madsen, and Lindström’s 2017 method combines a two-state time-varying HMM with Model Predictive Control, MPC. The HMM updates beliefs about market conditions; MPC uses forecast means and variances to optimize allocations over a horizon, implements the current action, and repeats the calculation as new information arrives [27].

**The relevant comparison includes implementation friction.** In the reported live-sample tests, MPC achieved higher returns and significantly lower risk than buy-and-hold across major stock-market indices, outperforming a static regime-based allocation rule. The setup included transaction costs, a one-day implementation delay, and zero-interest cash as the alternative asset; a trading penalty improved robustness by reducing trades.

**The mechanism is anticipatory rather than reactive.** A simple regime switch changes allocation after a state classification. MPC additionally evaluates likely future states, risk, and trading costs. Its relative advantage weakens when conditional forecasts are unreliable or the model’s proposed exposure changes are too costly to implement.

### Reinforcement learning and multiperiod neural optimization

**Reinforcement learning learns an allocation policy.** An agent observes a state—potentially prices, forecasts, volatility, existing holdings, and costs—and chooses an action such as target weights or trades. Rewards evaluate the consequences over time. Existing holdings must be represented because the cost of reaching a new portfolio depends on where the portfolio starts.

**Net wealth should drive the reward.** If \(C_t\) is a trading-cost fraction paid before the next holding period, a simplified self-financing wealth relationship is:

$$W_{t+1}=W_t\left[1-C_t(w_t-\tilde{w}_t)\right]\left(1+w_t^\top r_{t+1}\right).$$

**The objective can reflect the mandate.** A learned policy can optimize net growth, utility, downside risk, or a combination. Full-investment, leverage, concentration, and turnover requirements must constrain the action space or be enforced through a valid transformation. Transaction costs embedded in wealth should not be silently omitted from the reward.

**A factorial comparison separates design choices.** The LSTM-enhanced reinforcement-learning study tested four combinations on 2014–2018 data:

| Method | Price-prediction input | Adjustment mechanism |
|---|---|---|
| Full rebalancing | Without LSTM prediction | Move to the selected composition immediately |
| Full rebalancing with prediction | LSTM | Move to the selected composition immediately |
| Gradual rebalancing | Without LSTM prediction | Change composition incrementally |
| Gradual rebalancing with prediction | LSTM | Change composition incrementally |

**Gradual LSTM-enabled allocation led the experiment.** The study used three constructed portfolios—one of global indices and two of relatively uncorrelated stocks—with $300,000 initial value per portfolio and a 0.125% commission on each rebalancing transaction. Gradual rebalancing with LSTM produced returns approximately 27.9%–93.4% higher than full rebalancing without prediction. These are relative return improvements across the experiment, not annualized percentage-point additions [28].

**Gradual actions can manage forecast uncertainty.** Smaller changes reduce the immediate consequence of an incorrect forecast and may reduce unnecessary full-portfolio switching. However, gradual execution also delays movement toward a genuinely better allocation. The experiment supports its combined design; it does not isolate a universal advantage for either LSTM forecasting or gradual trading in every market.

**Dynamic programming addresses the sequential trade-off.** A multiperiod optimizer evaluates the current action through its effect on both current wealth and future opportunities. Its state must include variables needed for those future decisions, which creates the curse of dimensionality as assets, states, and time steps increase.

**Neural approximations can assist dynamic optimization.** The INFORMS study combines dynamic programming with a recurrent neural network, using the dynamic program to provide strong starting solutions. It optimized a hidden Markov setting with linear transaction costs and tested problems with 50–250 time steps and up to 11 risky assets, finding computational benefits relative to standalone dynamic programs or neural networks [47].

**Computational gains and trading gains differ.** Efficiently solving a specified multiperiod model is valuable, but its investment outcome still depends on the model’s return process, state estimation, and cost assumptions. A neural policy can approximate a difficult optimization problem without proving that its assumed investment environment is correct.

### Signal-priority rebalancing under turnover limits

**Limited turnover creates a trade-selection problem.** Even when desired target weights are known, a manager may lack the turnover budget to execute every indicated trade. The 2024 *Smart Rebalancing* study compares three rules:

| Rule | Buy priority | Sell priority | Typical reported position |
|---|---|---|---|
| Priority-best | Strongest attractive signals first | Least attractive holdings first | First |
| Proportional | Scale indicated purchases proportionally | Scale indicated sales proportionally | Second |
| Priority-worst | Weakest buy signals first | Weakest sell signals first | Third |

The ordering is the study’s typical result rather than an unconditional theorem [48].

**Priority rules complement ML predictions.** The signal may come from a factor score or an ML model; the rebalancing rule determines which forecast differences deserve scarce trading capacity. Priority-best works when more attractive signals correspond monotonically to higher expected returns. The paper traced failures to non-monotonic signal–return relationships, showing why forecast calibration matters alongside ranking.

**A lower-turnover result is economically informative.** Using CRSP and Compustat data with factor returns from July 1964–December 2020, the value portfolio reached 2.9% annual CAPM alpha under a 20% annual turnover limit. Its unconstrained counterpart had 2.7% alpha with an additional 19 percentage points of turnover. The 20-basis-point alpha difference was not statistically significant [48].

**Trading-cost arithmetic clarifies the stakes.** As a conditional illustration, applying the RL study’s 0.125% commission to 20% one-way annual turnover—20% purchased and 20% sold—implies \(0.00125\times(0.20+0.20)=0.0005\), or an estimated five basis points of annual commissions. This calculation combines stated anchors under an explicit turnover convention; it is not a re-estimate of either study and excludes spreads, impact, financing, and taxes.

### Overall assessment

**Appropriate complexity follows the decision problem.** Risk-based allocation is attractive when expected returns are unreliable; confidence-weighted forecasting becomes useful when signals are credible; MCDM is useful when the mandate contains genuine competing objectives. Metaheuristics address difficult feasible sets, while MPC, reinforcement learning, and multiperiod neural methods address the consequences of changing allocations through time.

**Evidence retains its original measurement basis.** The reported results include theoretical properties, historical backtests, model-based simulations, forecasting comparisons, and practitioner descriptions. Sharpe ratios, classification accuracy, optimization quality, and preference-ranking probabilities measure different outcomes. A basis point is 0.01 percentage point; annualization and cost conventions remain study-specific. The 2019 DIA comparison’s mixed unit notation is retained without conversion, and the worked overlay allocations and commission estimate are calculations rather than independently tested investment results.

**The practical judgment is conditional.** Through April 2024, the strongest case for AI-enhanced portfolio management is a clearly connected process: information produces calibrated signals, signals and preferences determine feasible targets, and trading rules preserve value after costs. The preferred methods change when forecast reliability, market structure, investor priorities, or implementation conditions change.

## References

[1] <https://onlinelibrary.wiley.com/doi/full/10.1111/joes.12532> asset-pricing review; ML application review; regularization mechanisms; critical asset-pricing review; high-frequency lasso application; regularization studies…
[2] <https://www.investmenttheory.org/uploads/3/4/8/2/34825752/portfolioselection.pdf> Markowitz, 1952; original formulation
[3] <https://www.aeaweb.org/articles?id=10.1257/0895330042162340>
[4] <https://www.mdpi.com/2227-9091/10/1/4> EMH history and taxonomy; MCDM portfolio overview; Colombian application
[5] <https://www.newyorkfed.org/medialibrary/media/research/staff_reports/sr216.html> APT formulation; APT applications and boundaries; model-uncertainty discussion
[6] <https://kahneman.scholar.princeton.edu/sites/g/files/toruqf3831/files/kahneman/files/prospect_theory.pdf> prospect-theory publication
[7] <https://people.duke.edu/~charvey/Teaching/BA453_2006/Black_Litterman_GAA_1991.pdf> original global-allocation report
[8] <https://www.bauer.uh.edu/rsusmel/phd/Fama-French_JFE93.pdf> Fama–French, 1993; original stock-and-bond analysis
[9] <https://portfoliooptimizationbook.com/book/11.2-from-dollar-to-risk-diversification.html> risk-parity development
[10] <https://web.mit.edu/Alo/www/Papers/JPM2004_Pub.pdf> Lo’s original article
[11] <https://www.mdpi.com/2227-9091/10/4/84> five-factor overview
[12] <https://liu.diva-portal.org/smash/get/diva2:758241/FULLTEXT01.pdf> historical model account; implementation discussion; model formulation and interpretation; Swedish portfolio comparison
[13] <https://onlinelibrary.wiley.com/doi/10.1111/j.1540-6261.1964.tb02865.x> Sharpe’s equilibrium model; CAPM assumptions
[14] <https://doi.org/10.1257/089533003321164967> Shiller’s reassessment
[15] <https://www.cannonfinancial.com/uploads/main/Behavioral_Finance-Theories_Evidence.pdf> behavioral-finance evidence; momentum and reversal discussion
[16] <https://www.cambridge.org/core/journals/journal-of-financial-and-quantitative-analysis/article/behavioral-portfolio-theory/87E1D1AE8C8A8365B38CEA952EC28DF6> Behavioral Portfolio Theory
[17] <https://www.cambridge.org/core/journals/journal-of-financial-and-quantitative-analysis/article/abs/best-of-the-best-a-comparison-of-factor-models/B48456FE562673C373C23A062E6A10C8> factor-model comparison
[18] <http://www.thierry-roncalli.com/download/risk-budgeting.pdf> Bruder and Roncalli’s risk-budgeting formulation; risk-budgeting properties
[19] <https://link.springer.com/article/10.1007/s10614-022-10288-w> risk-allocation comparison; HRP procedure; network-based allocation rules; dependence-method comparison; NetMod evaluation
[20] <https://doi.org/10.3390/risks12010008> risk-estimation and concentration discussion; market-graph development; centrality–ERC construction; centrality results; network interpretation
[21] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9689940/> alpha risk parity; implementation trade-offs
[22] <https://doi.org/10.1007/s10898-016-0477-6> Equal Risk Bounding
[23] <https://medium.com/@michacukrowski/ridge-lasso-and-elastic-net-vs-d73e24208057> PPI forecasting experiment
[24] <https://digitalcommons.du.edu/cgi/viewcontent.cgi?article=3210&context=etd> ensemble forecasting study
[25] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10909160/> forecasting comparison; transformer application; task-specific forecasting examples; technical-feature application
[26] <https://www.vanguardmexico.com/content/dam/intl/americas/documents/latam/en/2022/10/mx-sa-2558523-rational-rebalancing-an-analytical-approach.pdf> joint forecasting framework; fixed-target rebalancing framework; utility-based comparison
[27] <https://backend.orbit.dtu.dk/ws/files/139272081/Dynamic_Portfolio_Optimization_Across_Hidden_Market_Regimes_ACCEPTED.pdf> HMM–MPC study; HMM–MPC mechanism
[28] <https://link.springer.com/article/10.1007/s00521-021-06853-3> LSTM-enabled allocation; RL comparison
[29] <https://www.generali-investments.com/uploads/4f813c1a-28ce-a956-8faa-837e2cd27704/GenAM-CM_Machine-Learning-and-Tactical-Asset-Allocation--Part-I-.pdf> macro-regime classifier; classification and implementation results; overlay design; TAA simulation results
[30] <https://dl.acm.org/doi/10.1016/j.eswa.2022.116558> blockmodel mechanism
[31] <https://doi.org/10.3905/jfds.2023.1.118>
[32] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9245389/> fundamental-data timing
[33] <https://journals.sagepub.com/doi/10.1177/20539517211070701> vendor examples; practitioner NLP pipeline; upstream-information example; alternative-data evidence
[34] <http://hdl.handle.net/2078.1/288072> sparse-feature framework
[35] <https://ojs.srce.hr/crorr/article/view/26302> Zagreb results
[36] <https://doi.org/10.1186/s40854-020-00175-4> related multicriteria methods; Tehran FANP results
[37] <https://www.rairo-ro.org/articles/ro/pdf/2021/01/ro200347.pdf> integrated decision-support system
[38] <https://www.ijahp.org/index.php/IJAHP/article/download/831/747> AHP application; Casablanca framework
[39] <https://riunet.upv.es/server/api/core/bitstreams/72968e29-99cf-40b4-9412-b6a6a9ff8f3c/content> mutual-fund application; rank-acceptability example; profile dependence
[40] <https://www.mdpi.com/2071-1050/11/9/2496> fuzzy ESG formulation; ESG portfolio comparison; NSGA-II ESG application
[41] <https://doi.org/10.1155/2022/4241049> PSO applications; DEMPO overview; GWO and firefly applications; fireworks applications
[42] <https://arxiv.org/pdf/2307.04045.pdf> constrained optimization discussion; time-limited results
[43] <https://pure.port.ac.uk/ws/portalfiles/portal/15712056/1_s2.0_S2214716019300399_main.pdf> metaheuristic survey
[44] <https://dergipark.org.tr/tr/pub/jssa/issue/70774/1087926> BIST30 comparison
[45] <https://doi.org/10.12785/amis/080619> ABC–firefly comparison
[46] <https://link.springer.com/article/10.1007/s00500-023-08177-x> evolutionary and swarm review; hybrid prediction pipeline
[47] <https://pubsonline.informs.org/doi/10.1287/ijoo.2021.0053> hybrid multiperiod optimizer
[48] <https://www.tandfonline.com/doi/full/10.1080/0015198X.2024.2317323> priority-rule comparison; turnover-constrained results
[49] <https://doi.org/10.3905/jpm.2024.50.5.073>
[50] <https://doi.org/10.2139/ssrn.4758251>
[51] <https://doi.org/10.1017/s1748499524000101>
[52] <https://people.hec.edu/rosu/wp-content/uploads/sites/43/2023/09/Fama-French-Common-risk-factors-1993.pdf>
[53] <http://www.cs.ucl.ac.uk/fileadmin/UCL-CS/images/Research_Student_Information/RN_11_04.pdf>
[54] <http://hdl.handle.net/10362/16857>
[55] <https://www.youtube.com/watch?v=RGw2qYWPigA&xstg=CAMSBhUDzO3xHw%3D%3D>
[56] <https://arxiv.org/pdf/1311.4057>
[57] <https://faculty.washington.edu/ezivot/econ589/ssrn-id684221.pdf>
[58] <https://ar5iv.labs.arxiv.org/html/1902.05710>
[59] <https://export.arxiv.org/pdf/2210.00969v1.pdf>
[60] <https://www.hillsdaleinv.com/uploads/Risk_Parity%2C_Maximum_Diversification%2C_and_Minimum_Variance-_An_Analytic_Perspective.pdf>
[61] <http://www.columbia.edu/~mh2078/A_generalized_risk_budgeting_approach.pdf>
[62] <https://elearning15.unibg.it/pluginfile.php/357092/mod_folder/content/0/References%20on%20Multifactor%20Models/Fama%20%20French%20%281996%29%20Multifactor%20Explanations%20of%20Asset%20Pricing%20Anomalies.pdf?forcedownload=1>
[63] <http://arno.uvt.nl/show.cgi?fid=129382>
[64] <https://doi.org/10.1016/j.eswa.2022.119370>
[65] <https://people.duke.edu/~charvey/Teaching/BA453_2006/GS_The_intuition_behind.pdf>
[66] <https://www.cqf.com/blog/quant-finance-101/what-is-the-efficient-markets-hypothesis>
[67] <https://www.hillsdaleinv.com/uploads/Adaptive_Markets_and_the_New_World_Order%2C_Andrew_W._Lo%2C_Financial_Analysts_Journal%2C_Corrected_May_2012%2C_Pages_18-29.pdf>
[68] <https://doi.org/10.1007/978-3-031-48169-7_7>
[69] <https://doi.org/10.1109/access.2024.3444479>
[70] <https://reference-global.com/download/article/10.2478/ejels-2023-0013.pdf>
[71] <https://doi.org/10.3390/e24111631>
[72] <https://oulurepo.oulu.fi/handle/10024/9576>
[73] <https://doi.org/10.1093/oso/9780199681143.001.0001>
[74] <https://www.mdpi.com/2227-7390/12/18/2897>
[75] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9689940/>
[76] <https://www.tandfonline.com/doi/abs/10.1080/14697688.2022.2145988>
[77] <https://doi.org/10.31933/dijdbm.v1i2.128>
[78] <https://doi.org/10.54097/k1rkh175>
[79] <https://en.wikipedia.org/wiki/Modern_portfolio_theory>
[80] <https://causalens.com/causal-ai/portfolio-optimization-beyond-machine-learning>
[81] <https://www.learnsignal.com/blog/what-is-modern-portfolio-theory/>
[82] <https://viking.som.yale.edu/an-introduction-to-investment-theory/chapter-vi-the-arbitrage-pricing-theory/>
[83] <https://www.newyorkfed.org/medialibrary/media/research/staff_reports/sr216.html>
[84] <https://business.columbia.edu/sites/default/files-efs/citation_file_upload/APT-Huberman-Wang.pdf>
[85] <https://blog.edda.co/2024/01/04/unlocking-investment-strategies-with-arbitrage-pricing-theory/>
[86] <https://quizlet.com/study-guides/arbitrage-pricing-theory-overview-and-applications-7336ec75-4afa-47e2-8c89-29ace3beda2b>
[87] <https://web.mit.edu/Alo/www/Papers/JPM2004_Pub.pdf>
[88] <https://garfield.library.upenn.edu/classics1979/A1979HE73200001.pdf>
[89] <https://www.newyorkfed.org/medialibrary/media/research/staff_reports/sr216.pdf>
[90] <https://www.nber.org/system/files/working_papers/w9222/w9222.pdf>
[91] <https://doi.org/10.26531/vnbu2017.239.028>
[92] <http://www-stat.wharton.upenn.edu/%7Esteele/Courses/434/434Context/EfficientMarket/AndyLoJPM2004.pdf>
[93] <https://www.sciencedirect.com/science/article/abs/pii/S0377221716309705>
[94] <https://journalcps.com/index.php/volumes/article/download/739/743/2427>
[95] <https://www.federalreserve.gov/econres/feds/files/2024014pap.pdf>
[96] <https://link.springer.com/article/10.1007/s10614-024-10702-5?code=9618e4d4-3227-46c8-a4f9-0f73ba2703e9&error=cookies_not_supported>
[97] <https://doi.org/10.2307/2328953>
[98] <https://doi.org/10.1016/s1574-0102(03)01027-6>
[99] <http://thierry-roncalli.com/download/risk-budgeting.pdf>
[100] <https://www.econstor.eu/bitstream/10419/194751/1/1029436177.pdf>
[101] <https://doi.org/10.32614/cran.package.hierportfolios>
[102] <https://www.degruyterbrill.com/document/doi/10.1515/snde-2023-0012/html>
[103] <https://portfoliooptimizationbook.com/book/6.5-risk-based-portfolios.html>
[104] <https://onlinelibrary.wiley.com/doi/10.1111/mafi.12419>
[105] <https://doi.org/10.1016/j.eswa.2023.122924>
[106] <https://arxiv.org/html/2403.06779>
[107] <https://arxiv.org/html/2504.14345v2>
[108] <https://run.unl.pt/server/api/core/bitstreams/9a3aa963-8c36-479a-be0d-cd4df80bfd00/content>
[109] <https://doi.org/10.1080/26941899.2023.2295539>
[110] <https://doi.org/10.62051/ijgem.v4n2.15>
[111] <https://doi.org/10.48550/arxiv.2402.16609>
[112] <https://www.mdpi.com/2227-7390/12/19/3066>
[113] <https://doi.org/10.4236/jmf.2024.143016>
[114] <https://ideas.repec.org/a/eee/finlet/v58y2023ipcs1544612323008875.html>
[115] <https://www.mdpi.com/2227-9091/12/1/8>
[116] <https://doi.org/10.1016/j.ememar.2022.100891>
[117] <https://www.invesco.com/content/dam/invesco/emea/en/pdf/portfolio-construction.pdf>
[118] <https://arxiv.org/html/2412.11575v2>
[119] <https://doi.org/10.54691/bcpbm.v35i.3390>
[120] <https://www.aimspress.com/article/doi/10.3934/DSFE.2025009?viewType=HTML>
[121] <https://link.springer.com/article/10.1007/s00521-024-09456-w>
[122] <http://www.efmaefm.org/0EFMAMEETINGS/EFMA%20ANNUAL%20MEETINGS/2024-Lisbon/papers/Balancing_Returns_and_Responsibility_Full.pdf>
[123] <https://people.duke.edu/~charvey/Teaching/BA453_2006/Idzorek_onBL.pdf>
[124] <https://www.math.fsu.edu/~kercheva/papers/portfolio_selection.pdf>
[125] <https://arxiv.org/pdf/2307.03391>
[126] <https://doi.org/10.14711/thesis-991013340350303412>
[127] <https://arxiv.org/abs/2401.05080>
[128] <http://wp.lancs.ac.uk/fofi2024/files/2024/04/FoFI-2024-157-Rasmus-Lonn.pdf>
[129] <https://storage.prod.researchhub.com/uploads/papers/2024/01/11/2401.05080v1.pdf>
[130] <https://www.sciencedirect.com/science/article/abs/pii/S1042443124000155>
[131] <https://link.springer.com/article/10.1057/s41260-025-00420-4>
[132] <https://www.tobam.fr/wp-content/uploads/2014/12/TOBAM-JoPM-Maximum-Div-2008.pdf>
[133] <https://hrcak.srce.hr/file/435164>
[134] <https://gupea.ub.gu.se/bitstreams/44b8b4f2-20ea-426b-8b79-3aecd99c4307/download>
[135] <https://doi.org/10.3390/axioms11020042>
[136] <https://journals.uvu.edu/index.php/jbi/article/download/90/70>
[137] <https://www.mdpi.com/1999-4893/17/12/570>
[138] <https://researchdiscovery.drexel.edu/view/pdfCoverPage?instCode=01DRXU_INST&filePid=13592724790004721&download=true>
[139] <https://en.wikipedia.org/wiki/Fama%E2%80%93French_three-factor_model>
[140] <https://www.tandfonline.com/doi/abs/10.1080/1331677X.2021.1875865>
[141] <https://www.cannonfinancial.com/uploads/main/Behavioral_Finance-Theories_Evidence.pdf>
[142] <https://ryanoconnellfinance.com/efficient-market-hypothesis/>
[143] <https://www.tidy-finance.org/python/capital-asset-pricing-model.html>
[144] <https://repositorio.uniandes.edu.co/entities/publication/52ad93dc-b82b-4022-8549-6361035b044a>
[145] <https://www.pm-research.com/content/iijjfds/6/1/43>
[146] <https://doi.org/10.1093/jjfinec/nbae017>
[147] <https://doi.org/10.4236/tel.2022.122027>
[148] <https://www.pnas.org/doi/full/10.1073/pnas.96.18.9991>
[149] <https://www.acaciafund.org/markets/research/fama-french-1993-three-factor-model/>
[150] <https://doi.org/10.5937/intrev2202021k>
[151] <https://www.sciencedirect.com/science/article/abs/pii/S2214635014000136>
[152] <https://business.columbia.edu/sites/default/files-efs/pubfiles/1814/BehavFin_Review_Huberman.pdf>
[153] <https://www.goldmansachs.com/our-firm/history/moments/1990-black-litterman-model>
[154] <https://academic.oup.com/book/56096>
[155] <https://arxiv.org/pdf/2302.01196>
[156] <https://link.springer.com/article/10.1007/s11579-024-00366-y>
[157] <https://hal.science/hal-03647881v1/file/elsarticle-template.pdf>
[158] <https://arxiv.org/pdf/2303.16151v1.pdf>
[159] <https://ieeexplore.ieee.org/document/11295284>
[160] <https://dl.acm.org/doi/10.4018/IJAMC.362001>
[161] <https://mba.tuck.dartmouth.edu/bespeneckbo/default/AFA611-Eckbo%20web%20site/AFA611-S6B-FamaFrench-CAPM-JEP04.pdf>
[162] <https://arxiv.org/html/2402.06635v2>
[163] <https://www.grahamcapital.com/wp-content/uploads/2023/07/Equal-Risk-Contribution-April-2019.pdf>
[164] <http://crrep.ca/sites/crrep.ca/files/fichier_publications/crrep-2015-09.pdf>
[165] <https://bura.brunel.ac.uk/bitstream/2438/10867/1/FulltextThesis.pdf>
[166] <https://lup.lub.lu.se/student-papers/record/9178260/file/9178261.pdf>
[167] <https://www.econ.queensu.ca/sites/econ.queensu.ca/files/wpaper/qed_wp_1450.pdf>
[168] <https://www.fe.training/free-resources/portfolio-management/portfolio-optimization/>
[169] <https://link.springer.com/article/10.1007/s11063-024-11582-4>
[170] <https://richard-herron.quarto.pub/fina-6333-2024-spring/herron_03_lecture.html>
[171] <https://doi.org/10.47535/1991auoes33(1)037>
[172] <https://www.aea.ru/data/pdf/fama2015.pdf>
[173] <https://www.worldscientific.com/doi/pdf/10.1142/9789813231573_0001>
[174] <https://www.ecb.europa.eu/pub/pdf/scpwps/ecb.wp2803~47f6833539.en.pdf>
[175] <https://nepjol.info/index.php/nrber/article/download/92673/70384>
[176] <https://www.kellogg.northwestern.edu/faculty/korajczy/ftp/wp139.pdf>
[177] <https://thehedgefundjournal.com/the-generalised-efficient-market-hypothesis/>
[178] <https://www.wallstreetprep.com/knowledge/efficient-market-hypothesis-emh/>
[179] <https://doi.org/10.4038/cbj.v15i1.172>
[180] <https://rpc.cfainstitute.org/blogs/enterprising-investor/2017/the-adaptive-markets-hypothesis-a-financial-ecosystems-survival-guide>
[181] <http://www.cs.ucl.ac.uk/fileadmin/UCL-CS/research/Research_Notes/RN_11_04.pdf>
[182] <http://www.e-m-h.org/definition.html>
[183] <https://www.robeco.com/en-int/insights/2024/10/fama-french-5-factor-model-why-more-is-not-always-better>
[184] <http://wp.lancs.ac.uk/fofi2024/files/2024/04/FoFI-2024-067-Sebastian-Weibels.pdf>
[185] <https://blog.quantinsti.com/fama-french-five-factor-asset-pricing-model/>
[186] <http://escholarship.org/uc/item/58s0w0c7>
[187] <https://ar5iv.labs.arxiv.org/html/2010.04404>
[188] <https://doi.org/10.21511/imfi.14(2-1).2017.03>
[189] <https://www.foliolab.ai/docs/guide/methods/inverse-volatility>
[190] <https://arxiv.org/html/2411.12323>
[191] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8995926/>
[192] <https://doi.org/10.3905/jpm.2021.1.228>
[193] <https://rpc.cfainstitute.org/blogs/enterprising-investor/2024/how-to-build-better-low-volatility-equity-strategies>
[194] <https://www.tidy-finance.org/chapters/modern-portfolio-theory.html>
[195] <https://business.columbia.edu/sites/default/files-efs/pubfiles/1802/1802.pdf>
[196] <https://www.financialplanningassociation.org/article/journal/MAY17-behavioral-finance-20-financial-psychology>
[197] <https://github.com/convexfi/riskparity.py/>
[198] <https://portfoliooptimizer.io/blog/cluster-risk-parity-equalizing-risk-contributions-between-and-within-asset-classes/>
[199] <https://doi.org/10.36713/epra18874>
[200] <https://www.semanticscholar.org/paper/The-role-of-AI-recommendations-in-portfolio-Hoang-Dey/93899102a159389def0683ddf8af593bf8092cb4>
[201] <https://doi.org/10.1038/s44387-025-00030-w>
[202] <https://doi.org/10.33545/27076571.2024.v5.i1b.168>
[203] <https://link.springer.com/article/10.1007/s43546-023-00618-x>
[204] <https://doi.org/10.1109/access.2020.3013097>
[205] <https://repec.unibocconi.it/baffic/baf/papers/cbafwp24233.pdf>
[206] <https://doi.org/10.54254/2755-2721/96/20241351>
[207] <https://rpc.cfainstitute.org/blogs/enterprising-investor/2024/how-machine-learning-is-transforming-portfolio-optimization>
[208] <https://www.esma.europa.eu/sites/default/files/library/ESMA50-164-6247-AI_in_securities_markets.pdf>
[209] <https://doi.org/10.1002/ijfe.2820>
[210] <https://doi.org/10.1155/2022/9430919>
[211] <https://tdm.sites.er.kcl.ac.uk/Articoli_web/PNAS_vol102_n30_10421-10426_2005.pdf>
[212] <https://journals.plos.org/plosone/article?id=10.1371%2Fjournal.pone.0273830>
[213] <https://doi.org/10.1007/s00354-023-00231-4>
[214] <https://www.researchgate.net/publication/380499814_Portfolio_optimization_based_on_network_centralities_Which_centrality_is_better_for_asset_selection_during_global_crises>
[215] <https://web.media.mit.edu/~xdong/paper/jpm24b.pdf>
[216] <https://repository.bilkent.edu.tr/server/api/core/bitstreams/a248862f-0b3e-45f7-a6ec-48bb1eeb9b12/content>
[217] <https://www.cfainstitute.org/sites/default/files/-/media/documents/survey/AI-Pioneers-in-Investment-Management.pdf>
[218] <https://doi.org/10.1016/j.asoc.2024.111233>
[219] <https://doi.org/10.1016/j.jempfin.2021.07.009>
[220] <https://www.paris-december.eu/sites/default/files/papers/2024/5502_mpraxmarer_2024_complete.pdf>
[221] <https://pubs.sciepub.com/jfe/12/1/1/index.html>
[222] <https://www.cfainstitute.org/sites/default/files/-/media/documents/book/rf-lit-review/2020/rflr-artificial-intelligence-in-asset-management.pdf>
[223] <http://theseus.fi/handle/10024/880420>
[224] <https://www.theseus.fi/server/api/core/bitstreams/0538e378-3912-439b-a387-d78687c89c6d/content>
[225] <https://doi.org/10.48550/arxiv.2304.11856>
[226] <https://doi.org/10.1057/s41260-021-00237-x>
[227] <https://ar5iv.labs.arxiv.org/html/2003.00656>
[228] <https://doi.org/10.1007/s11408-024-00455-4>
[229] <https://link.springer.com/article/10.1007/s10614-024-10604-6>
[230] <https://public.econ.duke.edu/~ap172/Patton_Zhang_BespokeRV_apr24.pdf>
[231] <https://doi.org/10.1093/jjfinec/nbae002>
[232] <https://economics.yale.edu/sites/default/files/2024-01/The%20Journal%20of%20Finance%20-%202023%20-%20KELLY%20-%20The%20Virtue%20of%20Complexity%20in%20Return%20Prediction%20(1).pdf>
[233] <https://export.arxiv.org/pdf/2306.03763v4.pdf>
[234] <https://link.springer.com/article/10.1007/s10489-024-05377-2>
[235] <https://dl.acm.org/doi/fullHtml/10.1145/3695080.3695125>
[236] <https://www.mdpi.com/1911-8074/18/12/687>
[237] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8870867/>
[238] <https://www.sciencedirect.com/science/article/abs/pii/S0377221717310652>
[239] <https://www.tandfonline.com/doi/full/10.1080/00036846.2020.1854451>
[240] <https://doi.org/10.1016/j.omega.2023.102975>
[241] <https://link.springer.com/article/10.1007/s11403-024-00426-y>
[242] <https://arxiv.org/html/2407.04500>
[243] <https://doi.org/10.47535/1991auoes33(1)036>
[244] <https://fsc.stevens.edu/network-and-clustering-based-portfolio-optimization-enhancing-risk-adjusted-performance-through-diversification/>
[245] <https://link.springer.com/content/pdf/10.1007/s43681-026-01238-5.pdf>
[246] <https://www.sciencedirect.com/org/science/article/pii/S0144358524000567>
[247] <https://doi.org/10.1016/j.procs.2017.05.185>
[248] <https://www.mdpi.com/2227-7099/12/7/164>
[249] <https://link.springer.com/article/10.1007/s10614-016-9627-7?code=a24afb64-6a05-4270-85a9-212647f95e02&error=cookies_not_supported>
[250] <https://livrepository.liverpool.ac.uk/id/eprint/3003623/1/Analysis%20of%20Correlation%20Networks_Revised2.pdf>
[251] <https://link.springer.com/article/10.1057/s41260-023-00347-8>
[252] <https://www.ml4trading.io/third-edition/chapters/17_portfolio_construction/>
[253] <https://web.stanford.edu/~nykh/file/correlation-networks.pdf>
[254] <https://arxiv.org/html/2311.09536v2>
[255] <https://eprints.soton.ac.uk/447213/1/Rank_Correlation_MST_paper_2_.pdf>
[256] <https://journals.plos.org/plosone/article?id=10.1371%2Fjournal.pone.0301804>
[257] <https://arxiv.org/html/2410.14841v1>
[258] <https://www.mdpi.com/2227-7390/12/21/3376>
[259] <https://link.springer.com/article/10.1007/s00521-023-08862-w?code=1877af82-88a5-4871-bf4c-7dbb56187a5a&error=cookies_not_supported>
[260] <https://doi.org/10.1108/ijicc-03-2025-0137>
[261] <https://jier.org/index.php/journal/article/view/1487>
[262] <https://link.springer.com/article/10.1007/s10479-023-05811-7>
[263] <https://link.springer.com/article/10.1186/s40854-021-00318-1>
[264] <https://iopscience.iop.org/article/10.1088/2632-072X/ad49fe>
[265] <https://doi.org/10.54097/zdzf0652>
[266] <https://repository.rit.edu/cgi/viewcontent.cgi?article=12624&context=theses>
[267] <https://link.springer.com/content/pdf/10.1007/s00521-021-06853-3.pdf?error=cookies_not_supported&code=49157ec2-3ebc-4a87-bf06-be7aefadff92>
[268] <https://link.springer.com/article/10.1007/s11408-022-00419-6>
[269] <https://link.springer.com/content/pdf/10.1007/s10614-024-10555-y.pdf>
[270] <https://app.clickdimensions.com/blob/dimensionalcom-agdc5/files/forecastingandmanagingvolitility_ridglp.pdf?m=11%2F11%2F2024+9%3A58%3A39+PM>
[271] <http://www.iba.t.u-tokyo.ac.jp/papers/2009/caranha2GECCO2009.pdf>
[272] <https://doi.org/10.3905/jfds.2023.1.118>
[273] <https://arxiv.org/html/2401.13126v2>
[274] <https://www.mdpi.com/2075-1680/13/10/660>
[275] <https://community.portfolio123.com/uploads/short-url/kyKEC6Z1GqoAiUAbc1sQLt0fnAx.pdf>
[276] <https://rpc.cfainstitute.org/sites/default/files/docs/research-reports/rf_aiinassetmanagement_full-monograph_online.pdf>
[277] <https://businessperspectives.org/journals/investment-management-and-financial-innovations/issue-447/predictive-modeling-of-return-volatility-in-sustainable-investments-an-in-depth-analysis-of-arima-garch-and-arch-techniques>
[278] <http://www.columbia.edu/%7Emh2078/QRM/TimeSeries_RiskManagement.pdf>
[279] <https://preview-www.nature.com/articles/s44387-025-00030-w>
[280] <https://researchhub.id/index.php/optimal/article/download/6541/3683/20339>
[281] <https://assets.ctfassets.net/tl4x668xzide/5tYd1K2cq0p3SbNRWXulmw/e130297205b1f4481041297451315c54/20231231-the-current-state-of-ai-in-asset-management.pdf>
[282] <https://doi.org/10.54254/2754-1169/2024.18332>
[283] <https://www.mdpi.com/2227-7390/14/13/2287>
[284] <https://doi.org/10.33545/26175754.2024.v7.i2g.627>
[285] <https://doi.org/10.1080/14697688.2024.2356239>
[286] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8961419/>
[287] <https://mcdm.ue.katowice.pl/index.php?id=SteuQiHirs05&page=publications>
[288] <https://www.sciencedirect.com/science/article/abs/pii/S0377221702008810>
[289] <https://doi.org/10.1051/ro/2020140>
[290] <https://www.aimspress.com/aimspress-data/gf/2024/2/PDF/GF-06-01-009.pdf>
[291] <https://doi.org/10.21203/rs.3.rs-4885143/v1>
[292] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12491627/>
[293] <https://repository.up.ac.za/server/api/core/bitstreams/b67f8628-b7d4-4708-bb0c-002c1201e98a/content>
[294] <https://workplace.vanguard.com/content/dam/inst/iig-transformation/insights/pdf/2024/the-vanguard-asset-allocation-model.pdf>
[295] <https://www.naturalspublishing.com/download.asp?ArtcID=28721>
[296] <https://doi.org/10.5267/j.msl.2012.07.019>
[297] <https://doi.org/10.5267/j.dsl.2014.8.003>
[298] <https://dergipark.org.tr/tr/pub/tojsat/issue/22650/241920>
[299] <https://doi.org/10.1186/s40854-020-00175-4>
[300] <https://doi.org/10.1016/j.proeng.2012.06.421>
[301] <https://doi.org/10.1109/inforino53888.2022.9782959>
[302] <https://springerplus.springeropen.com/articles/10.1186/s40064-016-1888-z>
[303] <https://www.mdpi.com/2227-7390/11/2/415>
[304] <https://doi.org/10.52783/jier.v4i3.1539>
[305] <https://jfin-swufe.springeropen.com/track/pdf/10.1186/s40854-021-00318-1.pdf>
[306] <https://ijfs.usb.ac.ir/article_2286_459119c7ea81ef16c1dc2c156e716ea4.pdf>
[307] <https://dmap-journal.org/index.php/dmap/article/download/1-15/54>
[308] <https://www.econstor.eu/bitstream/10419/237008/1/1752580664.pdf>
[309] <https://www.cin.ufpe.br/~if703/aulas/promethee.pdf>
[310] <https://qjma.atu.ac.ir/article_1132_en.html>
[311] <https://doi.org/10.1057/s41264-022-00141-4>
[312] <https://doi.org/10.22111/ijfs.2016.2286>
[313] <https://doi.org/10.1007/978-3-642-75935-2_10>
[314] <https://onlineoutput.com/fuzzy-vikor-method/>
[315] <https://doi.org/10.4018/979-8-3693-6502-1.ch012>
[316] <https://doi.org/10.13033/isahp.y2022.034>
[317] <https://doi.org/10.24191/mjoc.v9i1.26052>
[318] <https://growingscience.com/msl/Vol2/msl_2012_186.pdf>
[319] <https://pzs.dstu.dp.ua/DataMining/fuzzy/bibl/kahraman_c_ed_fuzzy_multi_criteria_decision_making_theory_an.pdf>
[320] <https://doi.org/10.7166/35-1-2922>
[321] <https://doi.org/10.33552/ijebm.2023.01.000502>
[322] <https://bcds.ch/articles/2023/issue%203/2343-1.pdf>
[323] <https://arxiv.org/html/2601.05428v1>
[324] <https://www.actuaries.org/app/uploads/2025/07/ICA2010_AFIR_32_final-paper_Jarvis.pdf>
[325] <https://doi.org/10.1016/j.orp.2024.100305>
[326] <https://doi.org/10.1007/s10479-024-06189-w>
[327] <https://doi.org/10.56028/aemr.11.1.121.2024>
[328] <https://www.mdpi.com/2227-7390/12/15/2424>
[329] <https://doi.org/10.12660/rbfin.v22n2.2024.90713>
[330] <https://link.springer.com/article/10.1007/s10489-022-03169-0>
[331] <https://www.mercer.com/assets/global/en/shared-assets/global/attachments/pdf-2024-Mercer-AI-integration-in-investment-management-2024-global-manager-survey-report-03212024.pdf>
[332] <https://www.tandfonline.com/doi/full/10.1080/0015198X.2019.1567190>
[333] <https://doi.org/10.20944/preprints202403.0859.v1>
[334] <https://www.tandfonline.com/doi/full/10.1080/0015198X.2023.2173506>
[335] <https://doi.org/10.1111/jofi.13395>
[336] <https://ideas.repec.org/a/bla/mathfi/v34y2024i3p896-924.html>
[337] <https://doi.org/10.30798/makuiibf.1469103>
[338] <http://ideas.repec.org/a/eee/ejores/v234y2014i2p536-545.html>
[339] <https://doi.org/10.1007/s13218-024-00870-9>
[340] <https://oercollective.caul.edu.au/business-finance/chapter/oer-topic-2-risk-and-return-part-i/>
[341] <https://www.mdpi.com/2571-9394/6/4/53>
[342] <https://doi.org/10.22436/jmcs.010.02.01>
[343] <https://iapress.org/index.php/soic/article/download/1961/1095/>
[344] <https://doi.org/10.1002/mde.4300>
[345] <https://doi.org/10.1007/s13209-010-0025-4>
[346] <https://www.mdpi.com/2227-7390/13/20/3303>
[347] <https://www.mdpi.com/2227-9091/10/1/4>
[348] <https://arxiv.org/html/2406.09578>
[349] <http://iors.ir/journal/article-1-27-en.pdf>
[350] <https://link.springer.com/article/10.1007/s10614-019-09957-0>
[351] <https://doi.org/10.48550/arxiv.2311.04946>
[352] <https://doi.org/10.18642/jmsaa_7100122287>
[353] <http://www.thierry-roncalli.com/>
[354] <https://doi.org/10.1007/s10614-022-10327-6>
[355] <https://doi.org/10.17758/eirai.f1017120>
[356] <https://doi.org/10.5267/j.ac.2024.7.001>
[357] <https://www.cbcg.me/repec/cbk/journl/vol13no3-7.pdf>
[358] <https://dergipark.org.tr/en/download/article-file/4344841>
[359] <https://doi.org/10.1109/access.2021.3082529>
[360] <https://doi.org/10.1007/978-3-540-77926-1_3>
[361] <https://www.mdpi.com/1911-8074/17/12/533>
[362] <https://link.springer.com/article/10.1007/s44196-025-00733-7>
[363] <https://link.springer.com/article/10.1007/s12652-024-04886-9>
[364] <https://kirj.ee/wp-content/plugins/kirj/pub/proc-2-2024-116-123_20240531034533.pdf>
[365] <https://doi.org/10.1108/md-05-2015-0191>
[366] <https://www.sciopen.com/article/10.3934/math.20241324>
[367] <https://onlinelibrary.wiley.com/doi/10.1111/ajfs.12260>
[368] <https://ijfs.usb.ac.ir/article_2286.html>
[369] <https://doi.org/10.1007/978-3-319-54416-8_7>
[370] <https://doi.org/10.1109/skima57145.2022.10029464>
[371] <https://dlnext.acm.org/doi/10.1016/j.eswa.2023.121415>
[372] <https://doi.org/10.1002/ijfe.2086>
[373] <https://ideas.repec.org/a/taf/tjorxx/v75y2024i1p85-98.html>
[374] <https://proceedings.mlr.press/v84/uziel18a/uziel18a.pdf>
[375] <https://www.foliolab.ai/docs/guide/methods/kelly>
[376] <https://www.econstor.eu/handle/10419/237203>
[377] <https://www.cambridge.org/core/books/abs/analytic-hierarchy-and-network-processes/theoretical-and-methodological-aspects-of-the-ahpanp-methods/00CC12FD7CCD69948F4FB00002162B8A>
