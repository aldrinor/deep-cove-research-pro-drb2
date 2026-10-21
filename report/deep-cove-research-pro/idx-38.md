# Environmental Control Algorithms for Modern Agricultural Greenhouses: A 2014–2023 Review and Research Cases

**The best controller depends on the task.** Across the 2014–2023 literature, PID and basic feedback control provide practical baseline regulation; fuzzy control incorporates expert knowledge; adaptive control responds to changing dynamics; Model Predictive Control (MPC) coordinates predictions, constraints, and resource objectives; neural networks learn nonlinear behavior from data; and hybrid control combines these capabilities. Neural networks and MPC were active research areas during 2017–2023, but their achievements differ: much neural-network evidence concerns prediction, whereas MPC studies more directly evaluate climate–energy–crop decisions. Concrete results include a neural-assisted ventilation field comparison reducing temperature RMSE from 3.01 to 2.45 °C, and an MPC model comparison reporting approximately 30% lower electric power use than relay control over 20 hours. [1][2]

## Comparison of the seven control algorithms

| Control Algorithm | Basic Principle | Advantages | Disadvantages | Application Scenarios |
|---|---|---|---|---|
| PID control [3] | Combine present, accumulated, and changing setpoint error | Simple implementation; little computation; effective when well tuned | Difficult tuning under nonlinear coupling; no explicit resource optimization or constraint handling | Temperature, humidity, and CO₂ loops; heating, ventilation, fogging, and injection |
| Fuzzy control [4] | Convert measurements into linguistic rules and actuator commands | Incorporates expertise; handles nonlinear relationships without a complete physical model | Process-specific rules; rule-base growth; disturbance handling depends on design | Temperature–humidity regulation; heating, cooling, irrigation, shading, and lighting |
| Feedback control [5] | Measure conditions, compare with targets, and correct deviations | Continuous automatic correction; straightforward sensor–actuator integration | Basic independent loops struggle with delays, coupling, and competing objectives | Zone climate, temperature, humidity, light, CO₂, soil moisture, and irrigation |
| Adaptive control [6] | Update controller or model parameters during operation | Accommodates uncertain and changing dynamics; supports multivariable regulation | Identification and stability design add complexity; disturbances can affect adaptation | Changing temperature, humidity, and CO₂ dynamics; uncertain greenhouse microclimates |
| Model Predictive Control [7] | Predict, optimize subject to constraints, apply first action, and repeat | Coordinates coupled variables; explicitly handles bounds and resource objectives | Requires an adequate model, forecasts, and repeated optimization | Climate, heating, ventilation, lighting, CO₂, energy, water, and crop objectives |
| Neural network control [8] | Learn nonlinear prediction or control mappings from data | Represents complex dynamics; supports forecasting, estimation, and learned control | Training-data dependence; extrapolation and seasonal transfer challenges; limited transparency | Temperature, humidity, CO₂, ventilation, climate forecasting, and controller modeling |
| Hybrid control [9] | Coordinate complementary controllers, models, or operating modes | Combines simple regulation with learning, adaptation, or optimization | More interfaces, tuning choices, and coordination requirements | Fuzzy-PID heating; neural–fuzzy climate control; VPD and integrated energy–water management |

**The report follows three questions.** First, how does each algorithm generate greenhouse control actions? Second, which trade-offs determine its suitability? Third, what do concrete neural-network and MPC studies from 2017–2023 actually demonstrate? The following sections develop these questions and translate the findings into selection guidance.

**Additional documented evidence**

The supported result is that the retained 2014–2023 review and 2017–2023 case evidence cannot support one cross-case performance ranking. Each comparison must retain the controlled variable and unit, target/setpoint versus measured state, denominator and baseline, crop and facility, evidence type, observation period, sampling interval, prediction or control horizon, and metric definition. Otherwise, reported “improvements” are not comparable.

For example, a 2021 PID indoor-greenhouse simulation reported temperature settling of **3.67 s**, humidity settling of **0.554 s**, **7.86%** overshoot, and **3.1 kWh/month** for a 100-module array [195]. A 2018 adaptive study was simulation-based and jointly addressed temperature, humidity, CO₂, tracking error, and energy allocation [92]. These are different objectives and evidence contexts, not a pooled benchmark. A 2023 MPC–RL study used 5-minute weather data, a 15-minute control step, a 6-hour prediction horizon, and a 40-day simulation horizon; its reported EPI was **1.843 Hfl m⁻² for MPC** versus **1.788 Hfl m⁻² for RL**, with computation times of **305.04 s** and **2.36 s**, respectively [162]. By contrast, a 2023 LSTM-RNN soft sensor estimated vent opening from climate inputs over **81 recorded days** at **30 s** sampling and reported **4.45% MAE**; this is prediction or soft sensing, not direct actuator-control performance [141]. Operational greenhouse forecasting results likewise should not be treated as controller results [142][148].

## Scope and the greenhouse control problem

### Time windows and international coverage

**Two publication windows govern the review.** The general algorithm discussion covers literature published during **2014–2023 inclusive**. The concrete neural-network and MPC cases fall within **2017–2023 inclusive**; publication or conference years identify the cases, while measurement periods are distinguished where relevant. No country, crop, greenhouse structure, or cultivation medium is imposed as an inclusion restriction.

**The applications are internationally diverse.** Examples include greenhouse climate control near Enna and in Albenga, Italy; mango-greenhouse CO₂ prediction in Boryeong, Korea; and temperature–humidity prediction using an Ethiopian research greenhouse. [10][2][11][12]

**Other settings broaden the comparison.** These include a tomato greenhouse in Agadir, Morocco; a northeastern Chinese greenhouse simulation; a semiclosed-greenhouse case in New York City, United States; and integrated greenhouse energy–water management in a Mapuche community in southern Chile. These settings demonstrate the breadth of applications, rather than a geographical ranking of algorithm adoption. [13][14][15][16]

### Why greenhouse conditions challenge controllers

**One actuator changes several variables.** Ventilation exchanges heat, water vapor, and CO₂ with outside air. Fogging influences both humidity and temperature, while heating changes the relationship between air temperature and relative humidity. Crop transpiration, solar radiation, wind, greenhouse geometry, and equipment operation therefore create a coupled, nonlinear system. Escamilla-García et al. describe these interacting internal and external influences in their 2020 review. [8]

**Delay makes reaction alone difficult.** A heating system may need time to warm its pipes, and air conditions may continue changing after a ventilation command. A controller responding only to the current temperature can consequently act too late or continue acting too long. Song et al.’s 2019 temperature–humidity prediction study explicitly connects these delays to the motivation for forecasting future greenhouse conditions. [17]

**The objective is not always exact tracking.** Keeping temperature extremely close to one setpoint can consume more resources than maintaining an acceptable crop-specific interval. Su, Xu, and Goodman’s 2017 fuzzy adaptive controller deliberately permits bounded tracking error to create opportunities for energy saving. This distinction separates environmental regulation—maintaining suitable conditions—from optimization—choosing suitable conditions and actions economically. [18]

### How the seven categories overlap

**Feedback describes an architecture, not one law.** PID is a particular feedback controller, and practical MPC, adaptive, neural, and hybrid controllers can also operate in feedback loops. In the comparison table, “feedback control” therefore means basic measured-condition-to-corrective-action regulation, rather than every sophisticated controller containing a feedback path. Pei and Modigh describe this architecture through sensors, target ranges, controllers, and actuators. [19]

**Hybrid labels describe combinations of responsibilities.** A fuzzy-neural controller belongs to neural-network research while also being hybrid; a neural greenhouse model can operate inside MPC; and a PID loop can receive its setpoint from a supervisory optimizer. Preserving the seven requested categories is useful for comparison, provided they are not mistaken for mutually exclusive technologies. The 2017 neural–fuzzy system and 2023 neural-model–MPC–fuzzy optimization system illustrate this overlap directly. [10][16]

The practical takeaway is to compare what each component contributes—correction, rules, adaptation, prediction, or optimization—not merely its label.

## Basic principles, strengths, and applications

### PID control: a practical error-driven baseline

**Three error terms generate the command.** A proportional–integral–derivative controller compares a desired condition with its measured value. For a heating loop, the error could be desired air temperature minus measured air temperature; the resulting command adjusts heating intensity. The greenhouse PID literature applies this principle to temperature, humidity, CO₂, and ventilation regulation. [20]

A compact expression is:

\[u(t)=K_p e(t)+K_i\int_0^t e(\tau)\,d\tau+K_d\frac{de(t)}{dt},\qquad e(t)=r(t)-y(t).\]

**Each term has a distinct role.** Proportional action responds to the current error: a larger temperature deficit produces a larger heating response. Integral action accumulates persistent error, helping remove an offset that proportional action alone may leave. Derivative action responds to how quickly the error changes, providing damping when temperature approaches its target rapidly; this is different from predicting future weather. [19]

**Simplicity is the main advantage.** The control law does not require an explicit greenhouse prediction model during operation, and its arithmetic is modest. Su, Yu, and Zeng’s 2020 study describes PID as simple, easy to implement, reliable, and robust when its parameters are correctly selected. These properties make it a strong baseline for individual heater, ventilation, fogging, or CO₂-injection loops. [3]

**Coupling complicates otherwise simple tuning.** A ventilation change intended to correct temperature also changes humidity and CO₂, so independently tuned controllers can interact. Fixed gains selected for one operating regime may perform poorly when weather, crop conditions, or equipment behavior changes substantially. The same 2020 study identifies strong nonlinearity and multiple-input/multiple-output coupling as important challenges for conventional PID. [3]

**Self-tuning extends the baseline approach.** In that study, three greenhouse outputs—temperature, humidity, and CO₂—were transformed into four equivalent outputs regulated by four PID controllers. A Levenberg–Marquardt algorithm adjusted the parameters, and simulations driven by real weather data showed good performance. This demonstrates how a familiar controller can be extended, although the transformation and tuning machinery contribute part of the achievement. [3]

**Choose PID for well-defined regulation.** It is especially suitable when the required actuator–variable relationship is manageable and the main objective is setpoint tracking. The judgment shifts toward coordinated or predictive control when explicit actuator constraints, several interacting outputs, and energy or crop objectives dominate the problem. Hu and You’s 2022 MPC discussion identifies precisely these issues as motivations for moving beyond independent PID loops. [7]

PID remains a defensible first choice for straightforward loops, but its simplicity should not be confused with automatic multivariable optimization.

**Additional documented evidence**

**Principle and bounded status**

PID control is an established/common, but conditional, greenhouse environmental-control method during 2014–2023. A 2023 review characterizes PID as a widely used feedback technique for greenhouse climate regulation, while 2020 greenhouse evidence describes it as a typical model-free method used in practice [244, 291]. This supports its inclusion as a mainstream comparator, not a claim that PID is universally optimal. A reported figure of approximately 95% refers to PID use in **process industries**, not to greenhouse control loops, and therefore should not be generalized to greenhouses [45].

PID (proportional–integral–derivative) control maps setpoint error to an actuator command. With \(e(t)=r(t)-y(t)\), the proportional term responds to the current error, the integral term accumulates error to reduce steady-state offset, and the derivative term responds to the error’s rate of change to anticipate plant behavior; their weighted sum forms the control signal [246, 291]. PID is model-free and does not require an explicit greenhouse process model, but it does require measured variables, setpoints, actuators, and suitably tuned gains [58]. In a 2020 self-tuning implementation, inside temperature, humidity, and CO₂ concentration were transformed into four equivalent outputs controlled by four PID loops for heating, fogging, CO₂ injection, and ventilation; the Levenberg–Marquardt algorithm tuned the parameters [58].

**Advantages and limitations**

PID control’s main advantages are a simple structure, straightforward implementation, familiarity, and good reliability and robustness when its three parameters are correctly set [244, 291]. It can provide effective regulation without a detailed model and is therefore attractive where greenhouse dynamics or weather disturbances are difficult to model. In a 2020 commercial-greenhouse study, tuning produced a smooth closed-loop response and removed steady-state error; a real-time test over one short **18-day production cycle** reported temperature and humidity fluctuations within permissible limits, with robustness examined under **2–5% parameter changes** [45]. A 2019 virtual-greenhouse benchmark likewise found that PID eventually kept temperature closer to the optimum than several tested methods and fluctuated less than the fuzzy controller, although it fluctuated more often than the neural-network controller; this result is simulation-specific rather than a general ranking [56].

The main limitation is tuning sensitivity. Fixed gains may fail to ensure stability or convergence in strongly nonlinear systems, and conventional PID is difficult to apply directly to coupled MIMO greenhouse dynamics; decoupling or multiple coordinated loops are often needed [291, 228]. PID is also reactive: it responds to present error rather than forecasting future state or exogenous weather, so it is less suitable for advanced applications requiring anticipation, constraints, or explicit energy optimization [57]. Parameter identification may need to be repeated when external conditions change unexpectedly [46]. A 2015 aquaculture-greenhouse study reported unsatisfactory traditional-PID temperature control under nonlinearity, large delay, and time variation [39]. Even self-tuning variants retain qualifications: the 2020 STPID method depended on optimizer convergence, and its equivalent transformation could trade temperature and humidity tracking; full-gradient tuning improved accuracy but increased energy and CO₂ use and actuator cycling, whereas incomplete-gradient tuning produced smoother actuator operation [58]. A 2023 greenhouse simulation illustrates the trade-off: PID eliminated steady-state error, but its reference response required **2,200 s (36.67 min)** to settle and its disturbance response reached **49.8 °C** and required **2,800 s** to settle [44].

**Application scenarios and comparison role**

Typical PID applications include low-level regulation of greenhouse temperature, relative humidity, CO₂ concentration, ventilation, heating, fogging, and injection systems [244, 291]. Examples include pump control for heating, window opening for humidity control, CO₂ injectors, roof-vent positioning to maintain an overpressure setpoint in semi-closed greenhouses, and ventilation control based on temperature error [7, 286]. A real-greenhouse proportional/PD-band experiment during **April–May 2017** used solar radiation, outside temperature, wind speed, and time-slot-specific coefficients for ventilation temperature control; optimized coefficients produced an RMSE of **1.25 °C**, but required long experiments and might be specific to that greenhouse [42]. PID is also reported in commercial, aquaculture, indoor modular, and networked greenhouse settings [8, 52, 248].

For the first comparison table, PID should therefore be represented as an error-based, model-free P/I/D feedback law; its advantages as simplicity, easy implementation, and conditional reliability; its disadvantages as gain-tuning dependence, weak native handling of nonlinear MIMO coupling and future disturbances, and possible sluggish or energy-intensive responses; and its scenarios as low-level temperature, humidity, CO₂, heating, fogging, ventilation, and greenhouse-climate loops [244, 291]. PID-related studies from 2017–2023, such as the nonlinear fuzzy-immune PID temperature/relative-humidity study by **Revathi et al. (2017)** and the parameter self-tuning PID study by **Su et al. (2020)**, are useful comparator evidence but are not standalone evidence that PID is an MPC or neural-network research hotspot [241, 291].

Within 2014–2023, PID control is an established greenhouse baseline: evidence includes climate control (2014) [48], classic PID versus Fuzzy FID (2017) [40], and an energy-cost design (2018) [60]; a 2023 review calls PID widely used for temperature, humidity, CO₂ and ventilation [49].

PID compares setpoint with measured value; P, I and D use present, accumulated and changing error to command actuators [47][59]. It is model-light, cheap and simple [47], while the 2018 design targeted feasible energy-cost reduction [60]. Tuning becomes difficult with nonlinear MIMO dynamics, delay, disturbances and constraints [50][61][66]. One simulation reported maximum errors of 3.6 °C for temperature and 8% for humidity [51].

PID—P/I/D respond to current, accumulated and changing error; low-cost, widely used for greenhouse temperature, humidity, CO₂ and lighting [52][54]. 2014 fuzzy-PID, 2020 self-tuning PID and 2023 simulated 25°C/60% cases are reported, but PID is not an NN/MPC row [53][64][63]. MIMO coupling, disturbances, actuator delay and tuning limit it [41][55].

PID—2024 Single-Neuron PID computed error and I-P-D terms, learned gains, drove vents for temperature/humidity in Dandong [65]. Tomato tests (25±1°C): SNPID vs PID gave RMSE 0.734 vs 1.594 and in-range readings 90.2% vs 40% [65]. Trial-and-error tuning and a simplified delayed model limit generalization; outside 2014–2023, no verified 2017–2023 case [65].

Within 2014–2023, a 2017 greenhouse comparison and 2023 review support PID as a mainstream baseline: it is described as a widely used feedback technique and among the most realistic approaches; proportional, integral, and derivative terms reduce error in temperature, humidity, CO₂, and ventilation [40][43][61][56]. It is practical and low-cost/simple for range-based control, but coefficient/identification tuning, model uncertainty and nonlinearity, long actuator response, disturbances, noise, delay, and saturation limit complex-greenhouse performance; use it as a baseline, not inherently optimal [62][61][46][43][47][42].

In the section’s comparison table, the PID row gives sensor-feedback error summed through proportional, integral, and derivative terms; advantages are effective, low-cost/simple range regulation; disadvantages are tuning/model, nonlinearity, noise/dead-time, and actuator-saturation risks; scenarios are greenhouse temperature/humidity control through heating, cooling, humidification, dehumidification, ventilation, or fog systems, including crop-growth energy-cost management; a 2023 simulation returned set points to 25°C and 60% [56][62][43][47][63][60].

For the requested 2017–2023 hotspot check, PID evidence does not confirm neural-network control and MPC as current greenhouse hotspots: it mentions a neural-network comparator and machine-learning PID tuning, but no MPC case or direct trend comparison [56][43]. The motivation is therefore unconfirmed here.

### Fuzzy control: translating expertise into actions

**Linguistic rules replace an exact mapping.** Fuzzy control expresses measured conditions using categories such as “low,” “medium,” or “high,” with degrees of membership between zero and one. An inference mechanism applies expert rules, combines their consequences, and converts the result into an actuator command. The main stages are fuzzification, rule inference, aggregation, and defuzzification. [10]

**Membership enables graded responses.** Unlike a strictly binary threshold, a measurement can partially belong to neighboring linguistic categories. The controller can consequently produce intermediate ventilation, heating, or cooling actions instead of only fully on or fully off commands. In Nicolosi, Volpe, and Messineo’s 2017 system, fuzzy controllers determine fan-coil air speed and air temperature from greenhouse and forecast information. [10]

**Expert knowledge is the key resource.** Faouzi et al.’s 2016 multivariable greenhouse study summarizes performance objectives and actions as plain-language expertise rules. Its attraction is that operators can encode useful relationships without first identifying every heat- and mass-transfer parameter. This is particularly relevant when a greenhouse is nonlinear but its practical operating behavior is familiar. [4]

**Rules become harder to maintain at scale.** Adding more inputs and linguistic categories creates more combinations that the rule base may need to cover. Faouzi et al. identify this combinatorial growth as a practical problem and investigate simplification and parameter optimization. The 2023 greenhouse-control review also notes difficulty handling sudden disturbances, showing that model independence does not itself establish robustness. [4][21]

**Applications extend across greenhouse equipment.** Reported fuzzy-control uses include temperature and humidity regulation, heating, cooling, irrigation, lighting, and shading. Fuzzy systems can also serve narrower functions inside compound controllers, such as approximating actuator-saturation effects. The latter role appears in Su, Xu, and Goodman’s 2017 fuzzy adaptive scheme. [22][18]

**Choose fuzzy control when expertise is strong.** Its advantage over fixed-gain regulation is the ability to encode nonlinear, operating-condition-dependent responses transparently. That advantage weakens when rules become numerous, contradictory, or difficult to transfer between greenhouse designs. Learning-assisted tuning or predictive supervision can then provide a useful extension.

Fuzzy control is most persuasive when a compact, understandable rule base captures the important greenhouse operating relationships.

**Additional documented evidence**

**Fuzzy control: principle and contribution**

**Fuzzy control (fuzzy logic control, FLC)** is a documented greenhouse environmental-control family in the 2014–2023 evidence base, with applications reported in greenhouse climate, irrigation, lighting, and ventilation systems [69][71][89]. It is especially relevant when greenhouse dynamics are nonlinear, multivariable, uncertain, or difficult to represent with an accurate physical model [72][66].

Its basic principle is to convert measured states or errors—such as temperature, humidity, substrate moisture, pH, or electrical conductivity—into linguistic membership values; evaluate expert-defined *if–then* rules through fuzzy inference; aggregate the rule outputs; and defuzzify them into crisp actuator commands [70][81][89]. In greenhouse implementations, temperature and humidity errors can produce commands for ventilation, heating, humidification, or dehumidification [70]. Some FLC systems therefore encode operator knowledge directly rather than requiring a pre-established mathematical plant model [71][89].

**Advantages and evidence**

Fuzzy control’s principal advantages are interpretability, relatively simple implementation, flexibility, and the ability to combine qualitative expert knowledge with numerical sensor data. It can provide useful control without a precise model and can be implemented on low-cost hardware with manual, automatic, or remote operation [71][72][89]. In a 2017 greenhouse prototype, fuzzy logic controlled temperature, relative humidity, soil moisture, and lighting without a mathematical model of the plant; the system also supported web-based monitoring and actuator control [89].

Reported outcomes are conditional on the study design. In a 2020 basil experiment lasting 40 days, the FLC greenhouse had temperature RMSE of **1.33 °C** versus **5.71 °C** in the On/Off control greenhouse, and humidity RMSE of **2.29%** versus **19.45%**; basil dry and fresh weights were respectively **50%** and **35%** higher than in the control greenhouse [83]. In a 2023 hydroponic-greenhouse study, genetic-algorithm optimization of fuzzy control changed reported mean daytime temperature from **34.25 °C** to **31.17 °C** and daytime humidity from **39.4%** to **60.22%**, while nighttime values changed from **23.22 °C** to **21.96 °C** and from **56.5%** to **74.59%**, respectively [82]. These are study-specific results, not a cross-study performance ranking.

**Limitations and application conditions**

Fuzzy control depends substantially on the quality of its membership functions, rule base, input selection, and expert abstraction. Too few linguistic levels can make control too coarse, whereas too many enlarge the rule matrix and increase reasoning and implementation difficulty [72]. A greenhouse fuzzy-PID simulation reported smoother action and faster settling than conventional PID, but rule tuning was complex and relied heavily on expert knowledge [45]. Another 2023 assessment notes that increasing rule complexity may improve accuracy while reducing dynamic performance and increasing dependence on expert management experience [66].

FLC may also respond poorly to sudden disturbances, strongly coupled variables, or conditions outside the rule-design experience [80]. Ventilation, for example, affects temperature and humidity simultaneously, can be suitable for one variable but unsuitable for the other, and may produce overshoot or fail to converge when its rate is inappropriate [71]. A 2017 greenhouse simulation controlled temperature and humidity under external perturbations but reported instability during the December–January winter period; the result remained simulation-based [85]. Broader deployment requires testing across climates, crop types, greenhouse sizes, and real operating conditions [73].

Typical scenarios are temperature–humidity regulation through ventilation, heating, humidification, and dehumidification [70][71]; low-cost remote monitoring and control of lighting, soil moisture, and irrigation [89]; hydroponic strawberry irrigation using substrate humidity, pH, and electrical conductivity [81]; and crop- and season-dependent control of irrigation, shading, heating, humidification, and ventilation [73]. Thus, fuzzy control contributes an interpretable and comparatively accessible way to turn greenhouse sensing and operator knowledge into actuator decisions, while remaining a conditional alternative rather than proof of universal superiority.

Within the separate 2017–2023 neural-network/MPC case collection, a fuzzy-only study is not itself a qualifying neural-network or MPC row. A relevant hybrid example is the **2017 parallel control fuzzy scheme (PCFS) coupled with an ANN/NNARX predictor and two FLCs**; it controlled fan-coil air speed and temperature using forecast greenhouse conditions, dynamically managed a simulated 24-hour period, and used simulated targets of **25 °C** in summer and **20 °C** in winter [79]. The supplied evidence does not provide an author-and-year-only attribution for that hybrid case, so that field remains **not reported** rather than inferred.

**Applications, evidence, and limits**

Fuzzy control (FLC; fuzzy-logic/fuzzy-inference control) converts measured greenhouse conditions into linguistic membership values, applies expert if–then rules, and defuzzifies them into actuator commands. Unlike binary thresholds, it varies heating, ventilation, humidification, cooling, irrigation, lighting, shading, or CO₂ action with error magnitude [51][77]. It suits nonlinear, coupled and uncertain dynamics, and may be combined with PID, neural networks, adaptive logic, or MPC [53][87][86].

Recurring 2014–2023 examples—fuzzy-PID, commercial VPD, wireless-sensor, climate-model, supervisory and organic-tomato control—support “established applied comparator,” not universal superiority [53][67][77][88][74][68]. A Punjab field system reported energy-optimized, mostly optimal and uniform climate under varying weather [67]. In Elazig, temperature, relative humidity, soil moisture and light were inputs; from 1 December 2017 to 31 March 2018, fuzzy heating used 29.72 kW versus 50.77 kW for the comparator, with about 25% reported heat-energy saving [77].

Fuzzy-only studies are comparator evidence, not rows in the 2017–2023 NN/MPC table. Alaviyan et al.’s **Fuzzy Inference Controller** was a 2020 smart-greenhouse case, but target variables and outcome were not reported [74]. Jomaa et al. (2019) used a **fuzzy logic method** for greenhouse air temperature and humidity, with heating, ventilation, humidification and cooling to obtain a suitable microclimate [88]. The 2023 hybrid **MPC based on fuzzy optimization** controlled temperature, relative humidity and window opening; simulated temperature stayed in the security zone for >95% of time, while Hsec was 83.61% (summer) and 67.21% (winter); the model lacked real-data validation [86]. It informs the MPC comparison, not a fuzzy hotspot count; 2024/2026 FLC results are out of scope [76][75].

Within the comprehensive 2014–2023 review of the requested named mainstream algorithm families, Fuzzy control is a supported current entry: a 2014 greenhouse paper used a Mamdani controller for temperature and air humidity, and a 2023 hydroponic study controlled temperature, humidity and carbon dioxide. These cases justify inclusion but not a claim of broad mainstream prevalence [69][82].

Across the bounded 2014–2023 mainstream review, Fuzzy control fuzzifies sensor error, applies expert IF–THEN/Mamdani rules, defuzzifies the result and drives actuators. It offers model-free nonlinear regulation with robust, flexible, low-cost remote implementation; however, process structure must be understood, because too few linguistic levels make control rough while too many enlarge the rule matrix and reasoning burden [72][78][71][69][82].

In the comparison-table row, Fuzzy control is represented by sensor inputs mapped through linguistic rules to defuzzified actuator commands; advantages are model-free nonlinear control, robustness, flexibility and low-cost remote operation, while the disadvantage is linguistic-rule design sensitivity. Typical scenarios are greenhouse temperature/humidity, soil-moisture and lighting control, plus heating, ventilation, irrigation and carbon-dioxide management in hydroponic systems [72][78][82][84].

**Additional documented evidence**

**Control algorithm and basic principle.** The source-supported labels are fuzzy logic controller, fuzzy logic control, FLC, and fuzzy controller [69]. Fuzzy control uses membership functions and rule-based group decisions to translate qualitative states into control actions; one greenhouse simulation used separate fuzzy controllers for temperature and humidity [69]. In a 2017 fuzzy-immune-PID design, fuzzy reasoning realized the nonlinear function of an immune proportional controller, while fuzzy and immune-feedback rules adjusted controller parameters online [134].

### Feedback control: continuous correction from measurements

**The loop closes through the greenhouse.** Sensors measure an environmental output; a controller compares it with a setpoint or acceptable range; the resulting error determines corrective action; and the changed environment is measured again. The feedback path is essential because it reveals whether the commanded action actually corrected the deviation. Pei and Modigh describe this sensor–controller–actuator sequence explicitly. [19]

**Basic feedback supports practical automation.** A temperature controller can activate heating below a threshold and stop it after reaching the target. A humidity or soil-moisture loop follows the same general pattern with different sensors and actuators. A 2023 systematic review describes continuous greenhouse sensing of temperature, humidity, light, and soil moisture followed by automatic corrective actions. [5]

**Correction reduces dependence on fixed schedules.** Timed operation applies an action whether or not current conditions require it; feedback adjusts actions to the measured greenhouse state. Walczuch et al.’s 2022 overview identifies reduced susceptibility to overshoot, undershoot, and disturbances as reasons for using closed-loop greenhouse systems. These benefits depend on an appropriately designed controller and useful measurements. [23]

**Simple loops have limited coordination.** A basic controller may recognize that temperature is too high without evaluating whether ventilation would waste injected CO₂ or interfere with humidity targets. The 2023 review’s criticism of feedback under complex multivariable conditions is best understood as applying to such simple regulation, not to feedback as an entire control-theory category. Advanced MPC and neural controllers can address these interactions while retaining feedback. [21]

**The feedback signal need not be air climate.** A 2017 automatic irrigation study, identified in the greenhouse-automation review, used a drainage hydrograph as its feedback signal for soilless cultivation. This illustrates a broader principle: useful feedback measures the process response relevant to the task, which may be drainage or substrate moisture rather than temperature alone. [24]

**Choose the architecture before the law.** Feedback is the foundation for correcting real deviations; PID, fuzzy, adaptive, and MPC methods determine how intelligently that correction is calculated. The choice changes when a basic error-to-action relationship no longer captures the important interactions or future consequences.

Feedback is essential infrastructure for regulation, while the quality of the controller inside the loop determines its capabilities.

### Adaptive control: updating behavior during operation

**Parameters change as evidence accumulates.** Adaptive control updates controller gains, model parameters, or another part of the control law while the greenhouse operates. Its purpose is to maintain useful behavior despite uncertainty or changes in the relationship between actuator commands and environmental outputs. Gerasimov and Lyzlova’s 2014 study provides an explicit greenhouse example. [6]

**Online identification supplies the update.** Their controller represents the greenhouse with parametrically uncertain nonlinear differential equations and uses a cascade-control design. An online identification algorithm adjusts controller parameters using an integral cost function, with fast parametric convergence described in the study. Temperature, air humidity, and CO₂ are regulated together, and closed-loop properties are evaluated in MATLAB/Simulink. [6]

**Adaptation addresses changing dynamics directly.** A fixed controller assumes its selected parameters remain suitable, whereas an adaptive controller revises them using operating information. This is useful when the greenhouse response differs from its initial calibration or changes with crop and environmental conditions. The benefit is not simply “more intelligence”; it is a specific mechanism for updating an uncertain control relationship.

**Adaptation differs from disturbance rejection.** A weather change can be an external disturbance even when the greenhouse’s underlying response parameters remain unchanged. An adaptive algorithm must therefore distinguish useful evidence of parameter change from transient effects that should be rejected. Su et al.’s 2020 discussion identifies complexity and disturbance sensitivity in some adaptive PID approaches, rather than establishing that every adaptive controller has the same weakness. [3]

**Learning can implement the adaptation.** Dahmani et al.’s 2019 adaptive neural controller changes feedforward-network connection weights online. This places a neural implementation inside the adaptive category: the important distinction is that its behavior updates during operation, rather than remaining fixed after offline training. [25]

**Choose adaptation for persistent operating change.** Adaptive control is attractive when uncertainty or time variation is central and sufficient measurements support parameter identification. The recommendation weakens if adaptation mainly reacts to noise or disturbances, or if its added design burden exceeds the benefit over a tuned conventional controller. Explicit constraints and resource optimization may still require an additional supervisory layer.

Adaptive control is a targeted response to changing dynamics, not an automatic substitute for forecasting or constrained optimization.

**Additional documented evidence**

**Principle and bounded status**

Adaptive control is a recurring 2014–2023 greenhouse environmental-control approach, but the permitted evidence supports an established or specialized research family rather than proven dominant routine deployment. In-window examples include adaptive microclimate control (2014), neuron-adaptive PID (2015), adaptive lighting and fuzzy-adaptive climate control (2017), adaptive GPC/control allocation and lettuce receding-horizon control (2018), adaptive neural control (2019), self-tuning PID (2020), adaptive hybrid control (2022), and adaptive monitoring/control (2023) [98][95][90][107][105][92][104][99][58][103][73]. This recurrence makes adaptive control relevant to the requested 2014–2023 review. It does not prove broad operational prevalence: conventional PID is still described as the mainly developed greenhouse approach, while advanced-control simulations are difficult to reproduce on PLC systems because algorithmic complexity limits adoption [96][93]. A 2023 greenhouse study mentioned adaptation only as future work, not as its implemented controller [94].

Adaptive control updates controller parameters or a plant model from measured behavior, so the control law responds to changing or uncertain dynamics rather than fixed gains. A 2014 study modeled greenhouse air temperature, humidity, and CO₂ with parametric uncertainty and adjusted parameters online through identification and an integral cost function; verification was performed in Matlab/Simulink [98]. A 2018 adaptive GPC study used recursive least squares on measured input/output data to update greenhouse parameters and calculate a real-time control law [105]. Control-allocation adaptive control derives a law for an uncertain greenhouse climate and distributes heat- and mass-flux demands to actuators; the reported approach did not require a priori uncertainty bounds [92]. Adaptive PID is one implementation: Lyapunov-based methods treat PID gains as adaptive parameters, whereas 2020 self-tuning PID used Levenberg–Marquardt tuning after transforming temperature, humidity, and CO₂ outputs into four equivalent unit outputs [58].

The variants should remain explicit. The 2017 fuzzy-adaptive design combines feedback linearization, a fuzzy system for actuator-saturation differences, robust compensation for disturbance and model uncertainty, and Lyapunov analysis [107]. A 2019 adaptive-neural controller adjusted feed-forward-network weights online and reported improved greenhouse performance [99]. A 2021 Chinese-solar-greenhouse scheme used an RBF network to estimate unmodelled dynamics, generalized-minimum-variance laws to set incremental-PID parameters, and switching between linear and neural nonlinear adaptive PID; simulation reported excellent performance [97]. A 2022 adaptive hybrid method used a neural network to estimate time-varying climate-model parameters, an adaptive law for heating, fogging, and CO₂ injection, and expert rules for ventilation, shading, and thermal screens; it reported good performance and economic efficiency in simulation [103]. The 2023 adaptive fuzzy method adapted monitoring and control to illumination, crop rotation, crop type, and vegetation period, mapping environmental states to heating, shading, ventilation, humidification, irrigation, and soil heating [73].

**Benefits, limits, and scenarios**

Greenhouse-specific benefits are conditional. In the 2018 adaptive-GPC comparison, adaptive GPC showed better stability, robustness, and fewer overshoot oscillations than adaptive GMV while both tracked temperature and humidity setpoints; GMV nevertheless required less control effort [105]. A 2015 single-neuron adaptive PID used Hebb learning, was reported as easy to implement, and achieved better closed-loop performance than conventional PID [95]. Control allocation minimized tracking error and energy use, and multiobjective optimization saved more energy in simulation [92]. For lettuce, the adaptive two-time-scale receding-horizon controller significantly reduced constraint violations and was reported as feasible for real-time PC implementation, although profit increased only marginally [104].

In a 2017 supplemental-lighting study, adaptive PWM measured photosynthetic photon flux (PPF) and adjusted LED duty cycle to a threshold: five-minute averages were typically within 0.2 mmol m⁻² s⁻¹, and electricity use fell 20–92% versus 14 hours per day of full-power lighting, depending on the threshold and sunlight daily light integral [90]. This is a lighting result, not a general climate-control effect. The 2020 self-tuning-PID evidence was a one-day simulation using real weather data from a Venlo tomato greenhouse in Shanghai; it reported good control performance but not operational deployment [58].

Costs and failure conditions are material. Greenhouse evidence describes adaptive methods as complex and their reliability as vulnerable to external disturbance [58]. Multivariable coupling can make one output’s setpoint change disturb another, and the controller depends on online identification and a mathematical model [105]. Broader greenhouse-control evidence reports matrix-processing requirements, special libraries, and powerful processors; results from dedicated simulations are difficult to reproduce on commercial PLCs [93]. The fuzzy-adaptive energy-saving strategy assumes that crops tolerate short-term tracking error and is supported by simulation evidence [107]. Adaptive lighting responds only to instantaneous PPF; without weather, climate, crop-value, or electricity-price inputs, it may require crop-specific photosynthesis–PPF curves and photoperiod constraints [90]. The 2023 monitoring method still called for hardware implementation, tests across climates, more crops and greenhouse sizes, and larger sensor datasets [73].

Typical scenarios are multivariable temperature/humidity/CO₂ regulation using heating, ventilation, fogging, or CO₂ injection [98][92]; Chinese solar-greenhouse temperature control under nonlinear disturbance [97]; lettuce cultivation [104]; supplemental LED lighting in commercial or research greenhouses [90]; and crop-specific microclimate monitoring [73]. These should remain labeled as simulation, real-time-PC, or field/lighting evidence rather than being pooled as equivalent deployment.

Adaptive control’s concrete in-window evidence includes a 2020 greenhouse-temperature study that processed 90 data groups over three months and reported convergence toward a reference model . A 2020 commercial butterhead-lettuce PAR/DLI trial estimated 26% annual supplemental-lighting savings (8.1 kWh/ft²) versus a time-clock baseline [91]. A 2017 record identifies supplemental LED lighting as an adaptive-greenhouse scenario [102]. Limits are omitted uncertainty, sensor/actuator problems, and limited uptake; adaptive lighting remained emerging in 2020 [91]. These limits support a specialized, not universal, mainstream status. Adaptive-only evidence is contextual, not a row in the separate NN/MPC case table.

Adaptive control belongs in the requested algorithm framework, but 2014–2023 evidence supports a qualified rather than unequivocally mainstream status: it is repeatedly proposed for greenhouse regulation, while adaptive lighting is described as “emerging” with minimal commercial penetration [96][91]. A bounded synthesis is online/self-tuning adjustment to changing microclimate, with temperature/humidity set-point regulation and sunlight-responsive LED lighting as scenarios; it adapts to changing model conditions, but requires online identification and added computational burden and faces sensor, low-sunlight-capacity, interruption, and fixture-compatibility risks [106][105][93][91].

Adaptive control estimates greenhouse-process parameters online and retunes the control law when microclimate dynamics change, so under ill-known or time-varying parameters it can keep temperature near its desired set point [105]. In the comparison table, its advantages are adjustment to changing conditions and uncertainty, its disadvantages are model/identification and matrix-computation dependence plus lighting-sensor, low-sunlight, interruption, and fixture risks, and its scenarios are temperature/humidity set-point regulation and adaptive supplemental LED lighting; evidence supports interest in neural-network control and MPC but not a comparative current-hotspot ranking—2019 evidence reports ANN field testing and a 2018 review covers MPC and greenhouse climate control [105][93][91][106][101][100].

**Additional documented evidence**

**Advantages and limitations.** The 2015 greenhouse study reports easy implementation, self-adjustment, and better closed-loop performance than conventional PID [95]. A cited 2017 study uses fuzzy adaptive controls to conserve and reallocate energy among greenhouse subsystems and includes temperature and humidity among the controlled variables [135]; because the method is specifically fuzzy adaptive control, it should not be treated as evidence for every adaptive architecture. Generic adaptive-control material identifies regulation, tracking, nonlinear, distributed, multivariable, and multiple-model applications [139], while another source emphasizes that practical implementation requires suitable adaptation parameters and sampling periods [136]. A non-greenhouse benchmark reports poor performance or instability for unsuitable adaptation-parameter values and explicitly concerns machine-tool control, not greenhouse climate; it is therefore a limitation of transferability, not greenhouse-specific outcome evidence [138].

The documented greenhouse scenarios are climate control, temperature and humidity regulation, heating and energy allocation, and adaptive PID control [135][95]. A 2012 RBF-network adaptive-PID citation confirms earlier greenhouse use but falls outside the 2014–2023 review window [137][42]. The available in-window evidence supports adaptive control as a documented specialized strategy, but does not establish sufficient recurrence to label it broadly mainstream. Likewise, the 2025 reinforcement-learning/RBFNN adaptive-PID case and its reported **19.7%** average energy-efficiency improvement are outside the requested period and must not be used for the 2014–2023 comparison [140].

### Model Predictive Control: optimizing future actions

**Prediction informs a constrained decision.** MPC uses a dynamic model to predict greenhouse behavior over a finite future horizon. It evaluates candidate control sequences against an objective and operating constraints, applies the first action, and repeats the calculation at the next control interval using updated information. This repeated procedure is called receding-horizon control. [7]

**The horizon connects actions with consequences.** A heating decision changes not only the current temperature but also future thermal conditions and energy requirements. Ventilation affects several future climate variables, while lighting contributes to both crop response and resource demand. MPC can evaluate these consequences together instead of making each decision solely from the present error. [22]

**Constraints enter the optimization explicitly.** Examples include maximum water flow, heat-pump power, supply-water temperature, actuator positions, and acceptable climate ranges. Bersani et al.’s 2021 formulation includes physical equipment limits, while Hu and You’s 2022 framework addresses uncertainty in greenhouse and crop control. This explicit representation of bounds is a central distinction from an unaugmented PID law. [2][7]

**The objective determines the behavior.** MPC can prioritize setpoint tracking, energy consumption, water use, photosynthesis, crop production, or combinations of these. A controller minimizing temperature error is solving a different problem from one maximizing crop output per unit resource. Achour et al.’s 2020 supervisory controller explicitly connects climate regulation with photosynthesis, water, and energy objectives. [26]

**Model quality remains consequential.** Predictions can be wrong because of uncertain parameters, incomplete crop dynamics, or inaccurate weather forecasts. More detailed nonlinear models also make repeated optimization more demanding. Robust MPC, data-driven identification, and alternative optimization methods are responses to these problems, not reasons to assume that ordinary MPC automatically resolves them. [3][7]

**Choose MPC for coordinated constrained operation.** Its strongest fit is a greenhouse where actuator limits and competing resource or crop objectives materially affect decisions. Its advantage narrows if the available model predicts poorly over the useful horizon or the optimization cannot finish within the required control interval. Simpler lower-level controllers may remain useful beneath MPC supervision.

MPC is particularly valuable when the greenhouse problem is not merely correcting error, but choosing an efficient feasible course of action.

**Additional documented evidence**

**Principle and bounded status**

Model Predictive Control (MPC) is an established and actively researched greenhouse-control family in 2014–2023 evidence: a 2023 study calls it the most commonly used approach in the scientific literature for greenhouse climate control, while a 2020 review describes high interest but limited greenhouse-specific literature [117][116]. This supports “established in the literature,” not universal commercial-deployment dominance.

At each sampling time, MPC uses measured or estimated greenhouse state to propagate a mechanistic or data-driven model across a finite prediction horizon, minimizes a cost for tracking and resource objectives subject to input, state, output, rate, or disturbance constraints, applies only the first optimized move, then updates the state and repeats through a receding horizon [117][57].

**Advantages and limits**

With a suitable model and feasible solver, MPC’s key advantage is coordinated multivariable optimization: it can balance temperature or humidity tracking against energy, water, yield, and operating-cost objectives while enforcing actuator and environmental limits [117][116]. Robust variants explicitly address disturbances; the 2018 particle-swarm-optimization (PSO) study reported better precision and robustness than conventional MPC in simulation [129].

The trade-off is implementation dependence. MPC needs a sufficiently accurate model, useful disturbance or weather forecasts, tuned weights and constraints, and enough computation to finish optimization within the sampling interval. Unknown disturbances and model mismatch can reduce effectiveness; propagating uncertainty and nonlinear optimization can be expensive, while more complex models increase calibration, instrumentation, and real-time burdens [117][116][129]. Results therefore do not transfer automatically across crops, greenhouse designs, climates, or deployment modes.

**Greenhouse scenarios and representative evidence**

- **Chen et al. (2018):** PSO-based robust MPC controlled greenhouse temperature; under simulated disturbances, it tracked the desired trajectory with more suitable control variables, precision, and robustness than conventional MPC [129].
- **Bersani et al. (2021):** MPC tracked indoor-air temperature and optimized ground-coupled-heat-pump water flow in an Italian smart greenhouse; over a **20 h** horizon, it saved **about 30% of electric power** versus relay control while maintaining a consistent temperature profile [57].
- **2023 hierarchical ME-MPC case:** economic and multi-energy MPC were combined with low-level PID control; in a simulation proof of concept, gas use fell from **80.79 t to 76.03 t** and grid-electricity imports from **17.80 MWh to 15.88 MWh** versus a rule-based controller, while greenhouse climate requirements were maintained [121].

Together, these 2018–2023 cases show MPC’s direct contribution to greenhouse environmental-control research: it converts climate and resource objectives into constrained actuator decisions, but its benefits remain model-, disturbance-, and implementation-dependent [129][57][121].

**Evidence and status**

MPC is a recurring greenhouse-control family in 2014–2023 evidence: a 2018 agriculture review covers greenhouse climate control, and a 2021 paper calls it an emerging technique [100][127].

Hamidane et al. (2023) simulated constrained MPC within 15–30 °C and 50–70% RH, with fan/heater inputs of 0–4.3/0–5 V and lower computational complexity [126]. Hu and You (2022) used data-driven robust MPC with weather-error sets; power-use efficiency rose 3.61–7.32% and crop production 0.76–16.25% [131].

García-Mañas et al. (2023) used stochastic multi-scenario MPC for Mediterranean tomatoes; profit exceeded an average-price scenario [118]. Together, 2017–2023 evidence indicates active interest, not a universal ranking: model error, limited data and stochastic weather impair tracking, while robust formulations can be conservative [118][86].

The 2015–2023 record supports treating Model Predictive Control (MPC) as an established, specialized greenhouse method, but not as universally deployed: permitted studies cover MLD, real-time, robust, neural-network, energy–water and nonlinear variants [108][122][110][125][109]. MPC predicts future states with a model, optimizes a finite-horizon cost under state/input constraints, applies the first move, and repeats after new measurements [108][119].

MPC coordinates temperature, humidity, CO₂, ventilation, heating/cooling, lighting, irrigation and energy/water. A 2015 MLD study predicted outside weather, solved an MIQP and switched open/closed windows in simulation [108]. Endo et al. (2023) used one-month water-demand and short-term climate optimization for irrigation, tank refilling and ventilation; energy use fell and irrigation was optimized in an isolated-community case [109].

Advantages are anticipatory multivariable optimization, constraint handling and resource trade-offs. Robust PSO-MPC achieved set-point tracking under disturbances with higher precision and robustness than conventional MPC in 2018 simulation [110]. In Italy (2021), MPC saved about 30% electric power versus relay control over a 20 h horizon while tracking temperature [123]; a 2023 Brooklyn rooftop-greenhouse simulation reported 15.2% average energy savings over 60-day seasonal runs [119].

Limits include model calibration, weather/state data and online computation; deterministic MPC may be insufficient under crop–climate uncertainty, and forecast errors can cause constraint violations [50][110][119]. Jung et al. (2020) OFNN-MPC ventilation reduced field RMSE from 3.01 to 2.45 °C over six days; Kerkhof and Keviczky (2021) compared NMPC with DeePC in simulation, while Gong et al. (2023) used PSO-MPC for heating, lighting and ventilation [125][132][124]. These cases show activity, not by themselves a hotspot ranking [112].

Mahmood et al. (2023) reported robust-MPC energy reductions of 9.67% (winter) and 23.61% (summer), with temperature RMSEs of 0.32°C and 0.60°C over two-day simulations [111]. Together with 2018–2021 PSO, hierarchical, Venlo and data-driven studies, this supports active MPC research, not a universal ranking [113][120].

MPC is established in 2014–2023 greenhouse research; it predicts, minimizes cost under constraints, applies one action and repeats [128][115]. MPC needs models/data and costly uncertainty handling [115][55]. Chen–You 2021 DDRMPC controlled temperature/humidity/CO₂; cost was 14% below rule-based and 4% below robust MPC, with 0.39% violations [133].

Within the requested 2014–2023 window, MPC is documented as an emerging technique used for greenhouse climate control, so it is the MPC entry in the seven-family review; the available evidence does not establish a comprehensive mainstream ranking [127][111]. The bounded synthesis links MPC to multi-input/multi-output climate, temperature, energy–water and crop-production optimization and draws on multiple dated greenhouse cases through 2023 [109][113][114][57][124].

MPC is a model-based, constrained receding-horizon optimizer: it predicts greenhouse behavior, solves an objective over a horizon, applies the first control move, and repeats [130][118]. In the comparison table, the MPC row lists advantages—multivariable constraint handling and explicit yield–energy/resource trade-offs—disadvantages—model or forecast error, uncertainty-related infeasibility or conservatism, computational burden and weight dependence—and scenarios—greenhouse climate/temperature, heating–ventilation, energy–water and crop-production control [114][115][118][57][109].

For MPC, the hotspot claim should be qualified: evidence shows active 2023 research and several variants, but cannot establish a cross-algorithm hotspot ranking [118][111]. The focused table collects exact cases within 2017–2023: data-driven robust MPC (2023), nonlinear sample-based MPC (2021), robust sample-based MPC (2022), stochastic multi-scenario MPC (2023), and PSO-MPC (2023), with additional references in 2018 and 2020 [113][117][118][124].

Focused-case rows are: data-driven robust MPC—greenhouse temperature and energy use; Mahmood et al. (2023) reported RMSE values of 0.32 °C in winter and 0.60 °C in summer and energy reductions of 9.67% in winter and 23.61% in summer under uncertainty over a two-day simulation [111]. PSO-MPC—heating, lighting and ventilation; Gong et al. (2023) reported superior performance and energy efficiency versus traditional control, with PSO outperforming genetic-algorithm optimization while maximizing yield and minimizing energy cost [124].

### Neural network control: learning prediction or control mappings

**Training replaces a hand-specified relationship.** An artificial neural network (ANN) learns a mapping by adjusting weighted connections from examples. Inputs may include weather, current greenhouse measurements, previous states, and actuator commands; outputs can be future climate conditions, estimated states, controller parameters, or actuator actions. Escamilla-García et al.’s 2020 review documents these different greenhouse applications. [8]

**The network’s role must be identified.** A neural predictor estimates what the greenhouse will do, but another component must decide how to act. A direct neural controller instead maps desired conditions and operating information to control commands. A neural model can also support an optimizer or an inverse controller, so “neural-network control” covers several distinct architectures.

**Temporal networks represent operating history.** A multilayer perceptron (MLP) is a feedforward network; time history can be supplied through delayed inputs. A recurrent neural network (RNN) contains internal recurrent connections that retain temporal information. Long short-term memory (LSTM), an RNN architecture with gated memory, helps preserve relevant information over longer sequences. [8][11]

**Nonlinear representation is the main attraction.** Greenhouse responses depend on interactions that can be difficult to capture with a compact explicit physical model. Neural networks can learn these relationships from operating data, including the combined effects of outside climate and actuator states. González Pérez and Calderón’s 2018 red-pepper greenhouse models provide a concrete example. [27]

**Training coverage governs practical reliability.** A model trained on one season, crop state, or operating range may perform differently elsewhere. Missing actuator information is especially consequential when deliberate interventions create conditions not predictable from weather alone. Moon et al.’s 2020 CO₂ forecasting results and the 2023 seasonal temperature study show these dependencies in different forms. [11][28]

**Choose neural methods for data-rich nonlinear tasks.** Their strongest role may initially be prediction or estimation inside an existing controller, rather than complete replacement of the control system. A direct learned controller becomes more attractive when its training coverage and closed-loop behavior match the intended deployment. Explicit operating constraints still need to be addressed by the architecture.

Neural networks are valuable because they can learn difficult greenhouse relationships, but predictive accuracy and effective actuator control remain different achievements.

### Hybrid control: coordinating complementary methods

**Responsibilities are deliberately divided.** Hybrid control combines methods so that different components handle different tasks or operating ranges. Examples include fuzzy tuning of PID, an ANN predictor feeding fuzzy controllers, and a neural weather model supporting MPC with fuzzy optimization. The combination is meaningful when the role of each component is clear. [29][10][16]

**Fuzzy-PID retains familiar local regulation.** A 2014 greenhouse study combines expert-derived fuzzy rules with PID theory to regulate temperature and humidity. Its simulations report improved response and disturbance resistance. The general attraction is to preserve PID’s compact corrective law while making the overall response more suitable for nonlinear, changing conditions. [29]

**Neural–fuzzy control separates prediction from action.** In Nicolosi et al.’s 2017 system, a neural model supplies a short-term temperature forecast and two fuzzy controllers choose fan-coil speed and air temperature. Prediction provides anticipation; fuzzy inference translates that information into equipment settings. This is more specific than saying that two intelligent algorithms are simply combined. [10]

**Operating-range combinations provide another pattern.** A 2022 hardware-in-the-loop study combines on–off, PID, and fuzzy proportional–integral control to regulate greenhouse vapor-pressure deficit (VPD). VPD expresses the difference between saturation vapor pressure at air temperature and actual water-vapor pressure, linking temperature and humidity in one control variable. The study uses operating points of 0.55 kPa for heating and 1.0 kPa for cooling. [9]

**A combined variable does not replace every objective.** VPD regulation can simplify temperature–humidity coordination, but different temperature–humidity combinations can produce a similar VPD. Accordingly, the usefulness of this simplification depends on whether separate temperature and humidity requirements also remain satisfied. The broader engineering lesson is that reducing complexity changes what is directly controlled.

**Coordination introduces its own trade-offs.** More components mean more interfaces, tuning choices, and opportunities for one component’s assumptions to conflict with another’s. Su et al.’s 2020 equivalent-decoupling design explicitly describes performance loss from transforming the coupled greenhouse into simpler subsystems. Hybridization can therefore provide a useful compromise without preserving every advantage of the original components. [3]

**Choose hybrids for complementary requirements.** They are particularly relevant when a greenhouse needs straightforward local regulation alongside nonlinear prediction, adaptation, or resource management. The combination is justified when its added component solves an identifiable problem and the coordinated system is evaluated as a whole.

Hybrid control is best understood as a division of useful functions, not a guarantee that combining algorithms will improve performance.

## Trade-offs that determine algorithm choice

### Model dependence, computation, and interpretability

**The knowledge burden shifts between methods.** PID needs suitable gains; fuzzy control needs useful rules; adaptive control needs an identifiable update mechanism; MPC needs predictive dynamics and objectives; and neural methods need representative training examples. Avoiding a complete physical model therefore does not remove the need for greenhouse-specific knowledge. The following comparison follows directly from the architectures described above. [3][8]

| Algorithm | Main information requirement | Constraint treatment | Online computation | Interpretability |
|---|---|---|---|---|
| PID | Error history and tuned gains | Additional limit-handling logic | Basic arithmetic | Error terms and gains are inspectable |
| Fuzzy | Membership functions and expert rules | Encoded through rules or added mechanisms | Rule inference | Linguistic rules are readable |
| Basic feedback | Measurements and target ranges | Thresholds and equipment interlocks | Comparisons and corrective logic | Usually straightforward |
| Adaptive | Measurements and an identification/update law | Depends on controller design | Identification plus regulation | Update law can be examined |
| MPC | Dynamic model, objectives, bounds, and forecasts | Explicit optimization constraints | Repeated prediction and optimization | Objectives and bounds are explicit |
| Neural network | Representative training data and inputs | Requires an appropriate control architecture | Trained-network evaluation | Relationships reside in distributed weights |
| Hybrid | Requirements of its components | Depends on supervisory coordination | Component-dependent | Depends on the combination |

**Training and runtime are different burdens.** Neural-network training may be substantial, while evaluating an already trained network can be much simpler than repeatedly solving an optimization problem. MPC places its optimization work within the operating cycle, although the burden depends on model size, horizon, constraints, and solver. Consequently, “neural networks are computationally demanding” and “MPC is computationally demanding” describe different parts of their workflows.

**Transparency also has several meanings.** A fuzzy rule can be understandable to a grower, while an MPC objective makes the trade-off between energy and climate tracking explicit. Neither property alone proves that the controller behaves correctly under all conditions. Neural weights are less directly interpretable, making operating-domain coverage and behavior testing particularly important; the 2022 deep-learning review identifies interpretability as a relevant direction for controlled-environment agriculture. [30]

**Practical suitability follows the available knowledge.** A site with little historical data but strong operational expertise may favor PID or fuzzy control. A well-characterized greenhouse with clear resource objectives is a stronger MPC candidate. A data-rich greenhouse with difficult nonlinear dynamics may benefit from neural modeling, either independently or within a hybrid controller.

### Tracking and disturbance handling are separate questions

**Good tracking does not establish robustness.** Tracking measures how closely a controlled variable follows a target under the evaluated conditions. Robustness concerns maintaining acceptable behavior despite model error, disturbances, or operating changes. A low temperature error in one simulation therefore answers a narrower question than reliable performance across seasons or greenhouse structures.

**Each approach reacts through a different mechanism.** Basic feedback and PID correct measured deviations; fuzzy rules change responses with the operating state; adaptive control updates parameters; and MPC incorporates predicted consequences. Neural networks contribute learned relationships, while robust MPC variants explicitly represent uncertainty. These mechanisms can complement one another, which explains the frequency of compound designs in the greenhouse literature. [18][7]

**Delay strengthens the case for anticipation.** If an actuator’s effect arrives after a significant interval, reacting to current error may be less useful than anticipating the future state. Nevertheless, a longer forecast horizon is helpful only while predictions remain informative. The recurrent-network comparisons below show that errors and architecture preferences can change with horizon, so anticipation must be evaluated at the timescale relevant to the equipment. [17]

**The selection changes with disturbance structure.** Persistent changes in model parameters favor adaptation; uncertain future weather motivates robust prediction; and unreliable measurements motivate estimation or filtering. Treating all three problems as a generic need for a “smarter controller” obscures the actual engineering requirement.

### Resource efficiency requires an appropriate objective

**Accurate tracking is not automatically economical.** A controller can maintain a tight temperature setpoint while using excessive heating or frequent equipment switching. Conversely, reducing heating indiscriminately may save power while allowing unacceptable climate deviations. Bersani et al.’s 2021 comparison evaluates these competing objectives together instead of treating either one as sufficient. [2]

**Crop responses change the optimization target.** An environment that is easy to regulate is not necessarily the most productive or profitable. Achour et al. incorporate photosynthesis objectives, while Gong, Yu, and Kollias connect greenhouse climate with a crop-yield model. These approaches evaluate environmental control through its agricultural consequences, rather than assuming that setpoint accuracy alone captures crop benefit. [26][22]

**Simpler controllers can still save resources.** Su, Xu, and Goodman’s fuzzy adaptive scheme uses acceptable environmental intervals to reduce energy demand. Thus, resource efficiency is not exclusive to MPC. MPC’s distinguishing capability is the systematic representation of future dynamics, bounds, and objectives within one optimization problem. [18]

The central decision is whether the task requires local correction, changing-parameter regulation, reliable prediction, or coordinated resource optimization.

## Neural-network research cases, 2017–2023

### Concrete cases and their main findings

**The cases cover different neural roles.** The table includes control-oriented simulations, climate prediction, and sensor-state estimation. ANN denotes artificial neural network; MLP denotes multilayer perceptron; RNN denotes recurrent neural network; LSTM denotes long short-term memory; and FNN denotes fuzzy neural network. Root mean square error (RMSE) and mean square error (MSE) summarize errors, while \(R\) is a correlation coefficient and \(R^2\) is a coefficient of determination.

| Specific Control Algorithm Used | Target Control Parameters | Main Conclusions or Achievements | Year of Research | Reference (Author and Year Only) |
|---|---|---|---|---|
| ANN/NNARX predictor plus parallel fuzzy controllers | Air temperature; fan-coil speed and air temperature | Simulation improved climate adjustment; 25 °C summer target | 2017 | Nicolosi, Volpe & Messineo (2017) [10] |
| Neural-network climate model | Predicted indoor temperature and relative humidity | Modeled red-pepper greenhouse climate from weather and actuator states | 2018 | González Pérez & Calderón (2018) [27] |
| Multidimensional LSTM versus conventional RNN | Predicted temperature and humidity | Evaluated 5-, 30-, and 60-minute forecasts using 27 inputs | 2019 | Song et al. (2019) [17] |
| RNN-LSTM | Predicted temperature, humidity, pressure, and dew point | One-year forecasting study; authors reported low RMSE and runtime | 2019 | Ali & Hassanein (2019) [31] |
| Elman RNN | Predicted indoor temperature and relative humidity | 18,000 records; MSE 0.0218; reported accuracy 98% | 2020 | Aytenfsu, Beyene & Getaneh (2020) [12] |
| LSTM | Predicted greenhouse CO₂ concentration | Two-hour forecasts; test \(R^2=0.78\); high-CO₂ underestimation | 2020; data 2017–2018 | Moon et al. (2020) [11] |
| ANN-enhanced Kalman filtering | Estimated temperature, humidity, and CO₂ readings | Improved prediction over conventional filtering in two error-model cases | 2020 | Ullah et al. (2020) [32] |
| Fuzzy neural network controller | Temperature and humidity | Simulation: temperature error <1 °C; humidity error approximately 2% | 2021 | Jia (2021) [33] |
| Deep Elman model plus deep MLP inverse controller | Internal temperature and hygrometry | Cascade simulation achieved error criterion \(E_t=129.89\) | 2021 | Salah & Fourati (2021) [34] |
| MLPNN with Levenberg–Marquardt training | Predicted indoor temperature and relative humidity | 4,000 values; test RMSE 4.637304; test \(R=0.990269\) | 2021 proceedings; 2022 copyright | Choab et al. (2022) [13] |

### Control-oriented studies: how predictions become actions

**Nicolosi’s system connects forecasting with equipment.** The neural model predicts the next temperature state, and two parallel fuzzy controllers determine fan-coil air speed and air temperature. The demonstrated control task is principally temperature regulation, with humidity and other weather variables contributing to the broader microclimate description. This is a clear example of a neural model participating in control without directly issuing all actuator commands. [10]

**Its settings make the mechanism concrete.** The summer simulations use a 25 °C target and fan-coil air-temperature settings of 5, 10, and 15 °C. Reported fan-coil air velocities include 1, 2, and 3 m/s, allowing cooling action to vary through both airflow and supply temperature. A winter example regulates around 20 °C, demonstrating that the target is an operating choice rather than a universal crop requirement. [10]

**The contribution is coordinated anticipation.** A conventional thermostat reacts after a threshold is crossed, whereas the neural–fuzzy arrangement uses a forecast when selecting present equipment settings. Its value consequently depends on both forecast quality and the fuzzy mapping from predicted conditions to actuator decisions. The network is trained offline in the reported implementation, so the paper’s adaptive terminology should be understood through its forecast-responsive combined design.

**Jia evaluates a more direct controller.** The 2021 FNN-based remote-control design regulates greenhouse temperature and humidity and compares its Simulink behavior with traditional PID and genetic-algorithm-plus-fuzzy-PID systems. It reports temperature error below 1 °C and humidity error of approximately 2%, with stable changes in the error values. The result supports the usefulness of the tested fuzzy-neural combination for that modeled climate-control task. [33]

**Fuzzy and neural functions are complementary.** Fuzzy structure supplies a way to express control relationships, while neural learning provides adjustable parameters. This differs from the Nicolosi architecture, where forecasting and rule-based control are separate modules. The distinction matters when choosing whether to improve an existing rule controller or introduce a dedicated predictive model.

**Salah and Fourati learn inverse control.** Their 2021 study models direct greenhouse dynamics with a Deep Elman network and trains a deep feedforward MLP to represent inverse dynamics. The networks are connected in cascade for temperature and hygrometry control. The evaluated greenhouse model has a surface area of 40 m² and volume of 120 m³, with heating, shutter, curtain, and spraying inputs. [34]

**The reported criterion improves substantially.** The two-hidden-layer neural controller achieves \(E_t=129.89\), compared with 344.12 for the earlier cascade used as a comparator. That is a calculated reduction of approximately 62.3% in this criterion: \((344.12-129.89)/344.12\times100\). The calculation concerns the study’s error criterion, not a percentage reduction in temperature, energy consumption, or crop loss. [34]

**Field ventilation supplies a complementary result.** A 2020 *Sensors* study compares conventional ventilation logic with output-feedback neural-network predictive control in two greenhouses. Temperature RMSE falls from 3.01 to 2.45 °C—an absolute improvement of 0.56 °C and a calculated relative reduction of 18.6%, using \(0.56/3.01\times100\). Here the neural model contributes to actual ventilation decisions, linking neural modeling with predictive control. [1]

**Architecture matters more than family labels.** These examples use neural networks as a forecaster, part of a fuzzy controller, an inverse controller, and a predictive ventilation model. Their shared achievement is the representation of nonlinear greenhouse relationships. The practical choice depends on which relationship the existing control system handles poorly.

### Recurrent forecasts: performance changes with horizon

**Song’s results resist a universal winner.** The 2019 study uses one-minute records from January–March 2018 in a tomato-oriented smart greenhouse. Its 27-dimensional input combines control and environmental information; each seven-day training block contains 10,080 records, followed by evaluation over five days. Forecast horizons of 5, 30, and 60 minutes are compared with a conventional RNN. [17]

**January shows a useful counterexample.** LSTM has lower temperature RMSE at five minutes, but the conventional RNN has slightly lower temperature RMSE at 30 and 60 minutes. Humidity favors LSTM at all three January horizons. The following values reproduce the study’s tabulated RMSE scale. [17]

| Forecast horizon | Temperature RMSE: RNN | Temperature RMSE: LSTM | Humidity RMSE: RNN | Humidity RMSE: LSTM |
|---|---:|---:|---:|---:|
| 5 minutes | 0.02141 | 0.01884 | 0.06635 | 0.06557 |
| 30 minutes | 0.05138 | 0.05465 | 0.09743 | 0.08755 |
| 60 minutes | 0.08562 | 0.08684 | 0.08851 | 0.08172 |

**The broader pattern still favors LSTM.** Counting the paper’s three months and three horizons gives nine temperature comparisons: LSTM has lower tabulated RMSE in seven of nine. It has lower humidity RMSE in all nine comparisons. These within-study counts support an overall advantage while preserving the two temperature counterexamples, rather than turning a general trend into an absolute claim. [17]

**Equipment timescales determine the useful horizon.** A slowly responding heating component may benefit from a longer lead time than an actuator with a faster response. However, the longer forecast must remain accurate enough to improve the decision. Song et al. explicitly connect their multiple horizons with equipment delays, making horizon selection an engineering decision rather than simply a forecasting competition. [17]

**A second comparison adds variable dependence.** Jung et al.’s 2020 study compares ANN, nonlinear autoregressive networks with external inputs (NARX), and RNN-LSTM for temperature, humidity, and CO₂ prediction over 5–30 minutes. At 30 minutes, LSTM leads on temperature and humidity, while it ties NARX on the reported CO₂ \(R^2\). [35]

| Model | Temperature \(R^2\), 30 minutes | Humidity \(R^2\), 30 minutes | CO₂ \(R^2\), 30 minutes |
|---|---:|---:|---:|
| ANN | 0.94 | 0.78 | 0.70 |
| NARX | 0.86 | 0.71 | 0.81 |
| RNN-LSTM | 0.96 | 0.80 | 0.81 |

**Temporal memory is useful, not sufficient.** LSTM’s memory mechanism helps represent delayed and sequential relationships, but its advantage still depends on the target variable, inputs, and forecast interval. Both comparative studies therefore favor evaluating candidate architectures at the intended operating horizon instead of selecting LSTM solely because it is more elaborate.

**Ali’s longer horizon addresses another task.** Ali and Hassanein’s 2019 RNN-LSTM study predicts temperature, humidity, barometric pressure, and dew point for tomato-greenhouse conditions over an entire year ahead. It varies neurons, hidden layers, and transfer functions, reporting low RMSE and computation time. This broad forecasting task should be distinguished from the minute-scale predictions used to schedule immediate actuator responses. [31]

### Inputs, crop state, and sensor quality explain results

**CO₂ forecasting exposes missing causal information.** Moon et al.’s 2020 study uses a 1,032 m² double-span greenhouse containing 100 four-year-old mango trees in Boryeong, Korea. Environmental inputs from nine sensors support LSTM forecasts at ten-minute intervals up to two hours ahead. Measurements span February 2017–May 2018, producing 69,684 records evaluated with five-fold cross-validation. [11]

**Prediction errors grow across the sequence.** The test \(R^2\) is 0.78, and RMSE across the time-series outputs ranges from 19.257 to 65.297 µmol/mol. The model especially underestimates CO₂ around 1,000 µmol/mol. The authors connect these high concentrations with deliberate CO₂ enrichment, which environmental factors alone could not adequately predict. [11]

**The mechanism suggests a concrete improvement.** A model using weather and environmental history may represent ordinary variation well but miss a deliberate injection event. Including actuator-state information is therefore important when the purpose is to predict the effects of control interventions. González Pérez and Calderón’s red-pepper models explicitly use window-opening and other actuator-state signals alongside external temperature, humidity, and radiation. [27]

**Plant information is another relevant distinction.** Moon et al.’s CO₂ model does not use plant-growth data, although crop processes influence greenhouse gas exchange. Their recommendation to evaluate other cultivation sites follows naturally from the model’s dependence on its particular input coverage and greenhouse conditions. This is a reason to consider crop state when developing a transferable model, not evidence that one architecture universally requires every possible crop variable. [11]

**Sensor estimation solves a different problem.** Ullah et al.’s 2020 system couples ANN learning modules with Kalman filters for temperature, humidity, and CO₂. The ANN estimates changing sensor error associated with external conditions and internal actuator operation, updating the observation-error covariance \(R\) used by the filter. Its two case studies use average-based and maximum-based error models and report improved prediction over conventional filtering. [32]

**Better state information benefits every controller.** A controller may issue an inappropriate action because its measurement is misleading, not because its control law is inadequate. Ullah et al.’s architecture addresses that upstream information problem. Its contribution should consequently be understood as improved estimation supporting control, rather than a replacement actuator-control algorithm.

**The Ethiopian case demonstrates recurrent modeling.** Aytenfsu, Beyene, and Getaneh use an Elman RNN to predict indoor temperature and relative humidity from wind velocity, CO₂, outside temperature, and outside humidity. Their 18,000-record dataset comes from the Ethiopian Environmental and Forest Research Institute greenhouse. Hidden-neuron selection using a convergence theorem produces reported MSE of 0.0218 and accuracy of 98%. [12]

**High correlation and error answer different questions.** Choab et al.’s Moroccan tomato-greenhouse model uses 4,000 values and an MLPNN trained with Levenberg–Marquardt backpropagation. Its training, validation, and testing results are shown below. Correlation describes how predicted and observed changes move together, while RMSE describes the magnitude of discrepancies on the evaluation scale. [13]

| Data partition | Reported aggregate RMSE | Correlation coefficient \(R\) |
|---|---:|---:|
| Training | 4.686367 | 0.989980 |
| Validation | 5.152746 | 0.987724 |
| Testing | 4.637304 | 0.990269 |

**Dataset size alone does not rank models.** The 4,000-value and 18,000-record studies concern different systems, inputs, and evaluation conventions. Their useful common finding is that feedforward and recurrent models can represent greenhouse temperature–humidity relationships. Their relative suitability must be assessed against the intended greenhouse and control task, rather than inferred from record count or a single headline metric.

### Why neural networks became a research hotspot

**The motivation is strongly greenhouse-specific.** The 2023 environmental-control review identifies data-driven methods as a research hotspot because greenhouse datasets can support single-factor, multifactor, and multiobjective regulation models. Neural networks are attractive when conventional equations leave important nonlinear relationships difficult to identify. The same review emphasizes universality and economic benefit as deciding issues for practical regulation models. [21]

**Broad deep-learning interest exceeds climate control.** The 2022 systematic review covers 72 studies published from 2019 through April 2022, with 82% focused on greenhouses. Yield estimation and growth monitoring account for 31% and 21%, respectively, while five studies are classified under greenhouse microclimate prediction. This supports strong research interest in greenhouse learning methods without implying that closed-loop neural climate control dominated the broader literature. [30]

**The 2023 seasonal study sharpens the issue.** An *Applied Sciences* comparison forecasts greenhouse temperature up to one hour ahead using LSTM-RNN and XGBoost. It divides July 2020–June 2021 observations into four seasons and conducts eight experiments. The summer LSTM-RNN result reaches \(R^2=0.9994\), RMSE 0.2698 °C, and mean absolute error 0.1449 °C, meeting the study’s ±2 °C hysteresis acceptability criterion. [28]

**Seasonal specialization changes the selection.** The authors find that season-specific algorithms can benefit prediction and that errors tend to increase over extended forecast periods. Thus, a very strong summer result does not establish the best architecture for every season or horizon. The practical implication is to match training and evaluation with the climate regimes in which the controller will operate. [28]

**A short-data study adds a contrast.** Another 2023 study compares deep neural networks, LSTM, and one-dimensional convolutional networks using one week of indoor-hydroponic greenhouse measurements from 16–23 March. Temperature, humidity, and CO₂ are sampled every minute, with an 80% training and 20% testing split and comparisons at 1-, 5-, 10-, and 15-minute intervals. LSTM performs strongly at shorter intervals, and performance changes as the interval increases. [36]

**Representativeness is more important than novelty.** That hydroponic study explicitly identifies its one-week span and exclusion of external weather and plant growth as boundaries of the model. Together with the seasonal study, it shows why broader operating coverage matters when moving from an accurate predictor to a dependable controller. More complex architecture alone does not resolve a training dataset that omits consequential conditions. [36]

The neural-network evidence supports strong nonlinear prediction and several useful control architectures, with deployment decisions governed by input coverage, operating horizon, and demonstrated closed-loop behavior.

**Additional documented evidence**

| Entity | Research Case | Specific control algorithm used | Target control parameters (As reported) | Main conclusions or achievements of the… | Year of research | Reference (author and year only) | Case eligibility/status | Evidence Context |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Jung et al. (2020), Model Predictive Control via Output Feedback Neural Network for Improved Multi-Window Greenhouse Ventilation Control | Jung et al. (2020) MPC-output-feedback NN[171] | no evidence found | Temperature, humidity, CO2; units/status unclear[157] | 96 m 2[173] | 2020[157] | no evidence found | Qualifying 2017-2023 case[171] | no evidence found |
| Gong et al. (2023), Optimizing Crop Yield and Reducing Energy Consumption in Greenhouse Control Using PSO-MPC Algorithm | no evidence found | PSO-MPC algorithm [185] | no evidence found | 96 m 2[173] | 2023 [165] | no evidence found | Provisional; verification unresolved [175] | no evidence found |
| Morales-García et al. (2023), Data-driven evaluation of machine learning models for climate control in operational smart greenhouses | no evidence found | no evidence found | no evidence found | MAPE improvement >8% vs single model[142] | 2023 calendar year[141] | no evidence found | Uncertain: prediction, not verified controller[161] | no evidence found |

Across the rows, Jung et al. (2020) is listed as an MPC plus output-feedback neural-network case for temperature, humidity, and CO2 in multi-window greenhouse ventilation; its conclusion field is unreported and its focused-case eligibility is marked unverified [157][194][168], while Gong et al. (2023) is listed as a provisional PSO-MPC case with target and conclusion evidence unreported and verification unresolved [178][185][175]. Morales-García et al. (2023) is listed as a deep-regression neural-network prediction case whose controller is unverified and whose evidence concerns prediction rather than confirmed control [148][163].

**Eligibility screen and date basis**

A focused case qualifies only when the permitted evidence shows that neural-network control, MPC, or a clearly labeled hybrid is central to greenhouse environmental regulation—not merely to climate prediction. For MPC, the evidence should show a predictive model, objective or cost function, optimization, and a control action applied to greenhouse actuators; for neural-network control, the learned model must participate in the control or actuator-decision pathway. A neural network used only to forecast temperature or humidity remains uncertain under this rule.[183][184]

Publication year is the default inclusion date. The focused window is inclusive **2017–2023**; experiment, simulation, and deployment dates are retained separately when reported. Jung et al. was published in **2020**, with a field test conducted **18–24 May 2018**; Gong et al. was published on **7 May 2023**; and the Morales-García candidate is listed as a **2023** publication, although no separate research or deployment date is verified.[181][185][156]

**Candidate cases and requested fields**

| Case / evidence status | Specific control algorithm used | Target control parameters | Main conclusions or achievements | Year | Reference (author and year only) | Evidence context and limits |
|---|---|---|---|---|---|---|
| **Jung et al., “Model Predictive Control via Output Feedback Neural Network for Improved Multi-Window Greenhouse Ventilation Control” — eligible**.[181] | **Model-based MPC with an output-feedback neural network (OFNN)**. The artificial neural network predicts inside temperature 30 minutes ahead from 15 sensor and controller-history inputs; the prediction is fed to an optimization node that selects the ventilation control signal for six window-opening behaviors.[181] | **Inside greenhouse temperature, °C**, with ventilation-window opening as the manipulated action. The source does not report a separate unit for window opening or a numeric temperature setpoint in the retained evidence.[181] | The prediction model achieved **R² = 0.94** in the abstract; validation over approximately **11,000 samples** reported **R² = 0.99** and **RMSE = 0.78 °C**. In a six-day field experiment, the OFNN-based controller produced a target-temperature **RMSE of 2.45 °C**, compared with **3.01 °C** for conventional ventilation control.[181] | **2020**.[181] | Jung et al. (2020) | Multi-window strawberry greenhouses in Korea; three simulation case studies and a two-greenhouse field comparison. The study directly links learned prediction and optimization to actuator control, but the field test lasted only six days; the authors identify further parameter optimization and testing across other greenhouse structures as future work.[181] |
| **Gong, Yu, and Kollias, “Optimizing Crop Yield and Reducing Energy Consumption in Greenhouse Control Using PSO-MPC Algorithm” — provisionally eligible**.[185][172] | **Particle-swarm-optimization MPC (PSO-MPC)**. MPC uses greenhouse-climate and crop-yield models, while PSO searches for optimal controllable parameters.[185] | Heating, lighting, and ventilation levels are the reported controllable parameters. The supplied abstract does not report numeric temperature, humidity, or CO₂ targets, units, setpoints, horizons, or sampling periods.[185][172] | The study reports that PSO-MPC improves performance and energy efficiency relative to a traditional control algorithm; PSO also outperforms traditional genetic-algorithm optimization for finding MPC control parameters. The supplied evidence reports potential to increase crop yield while minimizing energy costs, but no comparable effect size is available.[185] | **2023**.[185] | Gong et al. (2023) | Smart-greenhouse control study. The title, method, application, and qualitative achievement are supported, but the retained evidence is an abstract/metadata record rather than a complete primary-text extraction; crop, facility, geography, evidence type, and exact environmental setpoints remain not reported here.[172][185] |
| **Morales-García et al., “Data-driven evaluation of machine learning models for climate control in operational smart greenhouses” — uncertain**.[156][161] | The candidate record identifies a data-driven machine-learning evaluation, but **does not verify an ANN, RNN, LSTM, MPC, or other controller that generates actuator commands**.[156][161] | **Not verified.** The candidate metadata does not establish which environmental variables were directly controlled, whether any variable was a target or setpoint, or whether the models were predictors only.[156][161] | **Not verified.** The retained evidence does not establish controller performance, an actuator intervention, or a result attributable to neural-network or MPC control. It remains a relevant operational-greenhouse lead, not an eligible populated NN/MPC case.[156][161] | **2023**.[156] | Morales-García et al. (2023) | The title indicates operational smart-greenhouse climate-control data, but crop, geography, exact model, actuator pathway, baseline, and evidence type are not verified in the available record. The row is retained as **uncertain**, not silently converted into a predictor or controller case.[156][161] |

The deciding condition is method centrality: **Jung et al. qualifies because the OFNN prediction is embedded in an MPC ventilation-control loop; Gong et al. is a strong but incompletely extracted PSO-MPC candidate; Morales-García remains uncertain because the available record does not establish actuator control**. A title containing “climate control” or “machine learning” is insufficient by itself.

**Case-specific interpretation**

**Jung et al. (2020)** directly contributes to the requested greenhouse-control research by combining a neural-network process model with MPC optimization and testing the resulting ventilation logic in strawberry greenhouses. The controller predicts the future inside temperature, evaluates the predicted state through an optimization node, and uses the result to determine window-opening actions.[181] The reported **2.45 °C versus 3.01 °C** field-test RMSE comparison is a controller result from two comparable greenhouses over **18–24 May 2018**, whereas the **R²** and prediction-model RMSE values describe model validation and should not be treated as interchangeable control metrics.[181] In the first comparison table, this study should be represented as a **hybrid MPC–neural-network case**, not as an eighth algorithm family and not as two independent studies.

**Gong et al. (2023)** contributes a distinct MPC case centered on the joint objective of crop-yield maximization and energy-cost minimization. PSO is the parameter-search or optimization component, while MPC is the primary control family.[185] The evidence supports heating, lighting, and ventilation as controllable inputs and supports qualitative improvement over traditional control and genetic-algorithm optimization, but it does not support a numerical yield, energy, or tracking comparison in the retained slice.[185][172] In the first comparison table, the study belongs primarily under **MPC**, with PSO retained as an explicit component rather than counted as a separate control-family observation.

**Morales-García et al. (2023)** is relevant to the overall purpose because it concerns machine-learning evaluation in an operational smart-greenhouse setting, but its relationship to environmental-control algorithms remains unresolved. It should not be replaced with results from other 2023 greenhouse prediction papers, and its missing controller fields should remain visibly marked as not verified.[156][161]

**Additional in-window MPC evidence**

The three-row table preserves the initial candidate identities, while the following permitted studies provide additional concrete evidence of 2017–2023 MPC activity and help qualify the interpretation of the two verified or provisional cases.

- **Chen et al. (2018), robust PSO-MPC for greenhouse temperature**, used a nonlinear physical temperature model and a minimax robust-MPC formulation. The PSO solver handled the constrained optimization problem. Simulation results reported set-point attainment under disturbances, higher control precision, and stronger robustness than conventional MPC.[110] This is distinct from Gong et al. (2023): both use PSO with MPC, but the 2018 study focuses on robust temperature control, whereas Gong et al. focus on crop yield and energy cost.

- **Adaptive T–S fuzzy MPC**, listed with an issue year of **2018** and online publication on **13 December 2017**, used an adaptive Takagi–Sugeno fuzzy model inside an MPC scheme. Heating and ventilation regulated internal temperature and humidity; simulation results reported that both variables remained around desired setpoints under disturbances, with comparison against MPC using a single linear model.[167] This is a qualifying MPC–fuzzy hybrid example, but the available record does not supply the complete author-year case fields required for the frozen three-row table.

- **Morcego et al. (2023), “Reinforcement Learning versus Model Predictive Control on greenhouse climate control,”** compared MPC with a DDPG-based reinforcement-learning controller on a simulated lettuce greenhouse. The retained study evidence reports higher economic return for MPC (**1.843 Hfl m⁻²** versus **1.788 Hfl m⁻²** for the DDPG agent) and more accurate humidity control under MPC, while the RL agent performed better for indoor temperature and slightly higher production in the reported simulation.[151][162] These results are simulation-specific and should not be interpreted as a universal MPC ranking.

- **Endo et al. (2023)** used an MPC-based energy–water management system with a fuzzy optimizer for a greenhouse in a Mapuche Indigenous Community. Medium-term optimization over **one month** estimated water demand, while short-term optimization selected climate conditions for irrigation, reserve-water-tank refilling, and ventilation. Experiments in an isolated-community case reported reduced energy consumption and optimized irrigation.[109] The case demonstrates that greenhouse MPC can coordinate climate and resource decisions, but the retained evidence does not provide a directly comparable temperature or humidity effect size.

- **Chen and You (2023)** applied nonlinear MPC to an integrated rooftop greenhouse and host building in Brooklyn, New York. The framework regulated temperature, humidity, and CO₂ through fans, pad cooling, shades, heating, ventilation and air conditioning, CO₂ injection, and lighting. The case study reported **15.2% average energy savings** from integration with the host building.[150] This is an integrated-building case study, so its energy denominator and transferability differ from stand-alone greenhouse studies.

- **Mahmood et al. (2023)** used an artificial-neural-network system model inside a data-driven robust MPC framework, with a minimax objective and PSO for uncertainty handling. The target was greenhouse temperature; over a **two-day simulation**, RMSE was **0.32 °C in winter** and **0.60 °C in summer**, while energy reduction was **9.67% in winter** and **23.61% in summer**. The comparison was against an existing greenhouse climate-management system and basic MPC.[111] These are simulation results, not field-deployment measurements.

- **Hu and You (2023)** combined a physics-informed neural network with data-driven robust MPC for greenhouse-related tomato cultivation environments in Ithaca, New York, and Tucson, Arizona. The framework predicted indoor climate and crop states from temperature, humidity, CO₂, irrigation, and fertilization controls; robust MPC used those predictions to make actuator decisions under changing weather. The reported result was maintenance of the ideal cultivation environment and an average **46.4% cost reduction** relative to conventional control approaches.[154] The neural network is a predictive component within a robust MPC controller, so this is a hybrid case and should not be counted independently as both a pure neural-network and a pure MPC study.

- An economic MPC study using Pretoria, South Africa, weather data modeled temperature, relative humidity, CO₂ concentration, and incoming radiation power. The controller used **prediction and control horizons \(N_p=N_c=5\)** and was evaluated under **1%, 5%, and 10%** simulated system disturbances. At 10% disturbance, the reported average tracking errors were **8.27% for temperature**, **6.90% for relative humidity**, **5.73% for CO₂ concentration**, and **5.01% for radiation power**. Relative to a baseline that minimized operating cost, the proposed method increased operating cost by **R186**, reduced total cost by **R827**, and reduced carbon emissions by **1.16 tons**; experimental validation was identified as future work.[179] The retained card does not establish the study’s publication year, so it is not assigned to the 2017–2023 case table.

Several further records identify in-window MPC research without supplying all requested fields: Bersani et al. (2020) on near-zero-energy smart greenhouses, Ito and Tabei (2021) on greenhouse temperature and humidity control with ventilation, Lin et al. (2021) on Venlo-type greenhouse energy, water, and CO₂ consumption, Mahmood et al. (2021) on data-driven MPC for a semi-closed greenhouse, and Hu and You (2022) on MPC and machine learning for greenhouse energy and crop-production optimization.[166][183] These records establish additional study leads, but their exact target variables, results, and context are not populated here from complete supporting spans.

**Neural-network control evidence and predictor-only boundaries**

A direct neural-network control example beyond the frozen candidate rows is the **2019 remote greenhouse AI experiment**. Five AI teams controlled all actuators in separate cucumber-greenhouse compartments, while a sixth compartment was operated by Dutch growers as a reference. The compartments were **96 m²** at ground level, with **76.8 m²** of crop-growing area, and the experiment ran for approximately **four months**. Setpoints and measurements were exchanged at **five-minute intervals**. Reported controllable variables included heating and ventilation temperatures, minimum ventilation opening, humidity-deficit setpoint, screen positions, artificial lighting, CO₂ concentration, and irrigation interval.[173]

The teams used different supervised, unsupervised, and reinforcement-learning approaches. The source identifies CNN and RNN architectures, GANs, Bayesian reinforcement learning, and DDPG, but does not map every architecture to a particular team.[173] Climate and irrigation decisions were made autonomously at different intervals, while expert agents corrected extreme decisions; most leaf-pruning decisions remained under expert policies. The study therefore provides greenhouse neural-network-associated control evidence, but exact architecture-to-controller attribution must remain qualified. In the reported crop-model comparison, the iGrow team realized approximately **36 kg m⁻²** of cucumber; under another team’s lighting strategy, predicted production was approximately **40 kg m⁻²**, whereas a different lighting strategy yielded approximately **33 kg m⁻²** in the counterfactual analysis.[173] Those values are crop-production comparisons under specified strategy substitutions, not pooled estimates of neural-network controller performance.

A 2017 reference titled **“Smart frost control in greenhouses by neural networks models”** supplies title-level evidence of greenhouse neural-network research, but the retained reference does not provide its exact controller, target variables, or results.[166] Conversely, multiple in-window neural-network studies are prediction-only and should not be counted as controller cases:

- A **2022** tomato-greenhouse study used LSTM, CNN, and CNN–LSTM models to predict evapotranspiration and humidity. It reported humidity-prediction RMSE of **2.87** on the test data and ET-prediction RMSE of **0.00317 kg m⁻² s⁻¹** in training and **0.00356 kg m⁻² s⁻¹** in testing, but stated only that the results could support future irrigation planning and humidity control; it did not verify a neural-network actuator controller.[169]

- A **2023** operational-greenhouse TinyML study used MLP and CNN models to forecast indoor temperature for the next **three hours**. RMSE was generally **2–3 °C**, MAE **1–2 °C**, and CNN models reached approximately **R² = 0.85**; the models were evaluated as prediction benchmarks on edge-computing devices, not as closed-loop controllers.[148]

- A **2023** commercial-greenhouse study in Agadir, Morocco, evaluated ANN, SVM, bagging, boosting, and CFD methods for predicting inside temperature and relative humidity from October and March data. Predictive models reported **R > 0.98** and **nRMSE < 7%**, while a combined-data model reported **R > 0.98** and **nRMSE < 9%**. These are modeling outcomes, not actuator-control outcomes.[174]

- A 2023 LSTM-RNN soft sensor estimated greenhouse vent opening from climate measurements, with **R² = 0.80**, **RMSE = 9.13%**, **MAE = 4.45%**, and **MaxAE = 62.94%**. The result supports sensing and decision support, but the retained evidence does not establish that the soft sensor itself issued control commands.[141]

These distinctions explain why the Morales-García row remains uncertain and why the Jung case is stronger: prediction accuracy alone does not establish environmental control, whereas Jung et al. report a feedback path from predicted temperature to optimized window actuation.[181]

**Date and domain exclusions**

A 2025 adaptive GA-BPNN study demonstrates direct neural-network ventilation control by converting real-time greenhouse parameters into fan and vent signals, but its publication date is **5 December 2025**, outside the focused window.[164] Similarly, 2024 MPC-based greenhouse studies are methodologically relevant but cannot populate a 2017–2023 row under the adopted publication-year rule.[170][180]

MPC and neural-network combinations from other domains are also excluded even when the controller architecture is otherwise relevant: a 2019 vehicle cooperative-adaptive-cruise-control dissertation, a 2014 polymerization-reactor neural-state MPC study, and a 2023 hydraulic-plant neural network emulating NMPC do not concern greenhouse environmental control.[159][160][149] A 2022 PSO-MPC intelligent-vehicle study and a 2024 MPC-PSO wind-energy study likewise fail the greenhouse-relevance condition.[176][177] These counterexamples reinforce that both **date** and **greenhouse environmental-control application** are required.

**Implication for the hotspot claim**

The permitted 2017–2023 evidence demonstrates substantial MPC activity across robust temperature control, greenhouse energy management, climate-resource coordination, integrated-building operation, and neural-network-assisted prediction. Neural-network control is represented by the Jung field case and the 2019 AI greenhouse experiment, but many other neural-network greenhouse papers in the evidence set remain predictors, soft sensors, or model-evaluation studies.[110][150][111][154][173][181] Thus, the cases support describing both MPC and neural-network control as active research areas, but they do **not** establish a publication-frequency ranking or prove hotspot status from an exhaustive count. Hybrid studies should remain labeled by their components and should not be counted as independent evidence for every component.

**Additional verified cases and identity checks**

Eligibility is controller-centred: a focused case must use MPC or neural-network control for greenhouse environmental control, not merely predict climate; the 2023 lettuce study explicitly formulates and evaluates MPC [115].

| Case/status | Specific control algorithm | Target parameters | Main conclusion and context | Year | Reference |
|---|---|---|---|---|---|
| Jung—*Model Predictive Control via Output Feedback Neural Network for Improved Multi-Window Greenhouse Ventilation Control* | Eligible hybrid: model-based MPC with an ANN temperature predictor and OFNN optimization for six windows [41]. | Inside temperature; 30-minute prediction; window openings are actuators [41]. | The model achieved \(R^2=0.94\); in a six-day Korean strawberry-greenhouse field comparison, temperature RMSE was 2.45 °C with the proposed logic versus 3.01 °C conventionally [41]. | 2020 | Jung et al. 2020 |
| Gong—*Optimizing Crop Yield and Reducing Energy Consumption in Greenhouse Control Using PSO-MPC Algorithm* | Provisional PSO-MPC identity; the supplied record verifies the title, authors and year but not the full controller implementation [192]. | Not reported or verified in the supplied evidence. | Main achievement and baseline are not reported in the supplied record; do not infer them from the title [192]. | 2023 | Gong et al. 2023 |

Other verified in-window cases show broader MPC activity. Chen et al. (2018) used PSO-based robust MPC for greenhouse temperature; simulation showed disturbance tracking and better precision and robustness than conventional MPC [129]. Kerkhof and Keviczky (2021) compared data-driven DeePC with nonlinear MPC for greenhouse-air-temperature tracking in numerical simulation, including changing dynamics and computation time [132]. Mahmood et al. (2023) used an ANN-model data-driven robust MPC for temperature; two-day winter and summer simulations reported RMSEs of 0.32 and 0.60 °C and energy reductions of 9.67% and 23.61%, respectively [147]. García-Mañas et al. (2023) used stochastic multi-scenario MPC to determine temperature references for Mediterranean tomatoes with natural ventilation and heating, reporting higher economic profit than an average-price scenario [118]. Morcego et al. (2023) compared MPC with DDPG-based reinforcement learning in a simulated lettuce greenhouse: MPC controlled humidity more accurately and returned 1.843 versus 1.788 Hf l m−2, but required 305.04 versus 2.36 s of computation [114].

The verified Jung result is field-tested but narrow: the controller was trained for the tested greenhouse, applied only to ventilation, and required a server because the Raspberry Pi-based controller overloaded [61]. A separate bibliography identifies *Time-serial analysis of deep neural network models for prediction of climatic conditions inside a greenhouse* by Jung et al. (2020); it reports ANN, NARX and RNN-LSTM prediction of temperature, humidity and CO₂, but does not verify the OFNN-MPC ventilation case [157]. These identities should remain separate. A 2017 adaptive-neuro-fuzzy greenhouse-temperature citation is only a title-level lead; its targets and conclusions remain unverified [186].

**Further case evidence**


- **Chen & You (2021):** DDRMPC regulated temperature, RH and CO₂ in a semiclosed New York greenhouse; cost was 14% below rule control, 4% below L1-robust MPC, with 0.39% constraint-violation probability [133].
- **Hu & You (2022):** Robust MPC with PCA/KDE uncertainty managed a simulated tomato greenhouse in Ithaca; versus MPC without machine learning, renewable-energy use fell 0.7–66.9% and crop production rose 0.7–16.1 wt% [155].
- **Morcego et al. (2023):** Nonlinear MPC versus DDPG optimized dry matter, CO₂, air temperature and RH in a lettuce-greenhouse simulation using a 6-hour horizon and 15-minute sampling [113][182].
- **Jung et al. (2020):** MPC/OFNN optimized six window behaviours in a strawberry greenhouse; R²=0.94, while six-day field RMSE was 3.01 versus 2.45°C for conventional versus developed logic [193].

Other leads include a 2023 Chilean MPC/fuzzy EWMS for temperature/RH, irrigation and ventilation (relative yield >0.986 in simulation) [128], and Chen et al. (2018) on PSO-robust MPC for greenhouse temperature [191]. Neural-network cases include 2023 PSO-BP-PID control (0.5°C temperature and 1% RH errors) [187] and 2018 GA-trained fuzzy-NN CO₂ control, effective in Matlab simulation [87]. A 35-study NN review found 74% prediction, 9% energy optimization and 17% other uses; FFNN/RNN/other architectures comprised 46%/20%/32%, while deep or hybrid NNs were rare and many studies were simulation-only [189]. A 2020 “MPC” meaning an 89s52 microcontroller is excluded [146].

Neural-network control is represented by a 2020 multi-window strawberry-greenhouse case in which a neural-network temperature-prediction model fed an output-feedback neural-network optimizer to generate ventilation signals; the method reported better control signals only in the greenhouse where it was trained and was proposed as potentially applicable to irrigation and heating/cooling [188][41].

Greenhouse MPC evidence spans cases dated 2020, 2021, and 2023 [193][132][111]. A robust MPC case reported 14% and 4% lower total cost than comparison strategies [133], while a PSO-based MPC study reported that its parameter search outperformed traditional genetic-algorithm optimization and could increase crop yield while minimizing energy costs [185]; MPC also coordinates energy and water management for irrigation, tank refilling, and ventilation [109].

The evidence documents neural-network involvement in greenhouse-control research in 2018 and 2022 [87][169] and describes substantial activity in greenhouse microclimate prediction and control [189]. This supports classifying neural-network control as an active research area, but not as a formally ranked hotspot, because the evidence does not provide a comparable cross-algorithm ranking [173].

MPC has sustained hotspot evidence: it is described as a widely accepted standard [158], one source reports 73 articles [152], and greenhouse MPC work is represented in 2018, 2021, 2022, and 2023 [167][132][161][162]. This supports classifying MPC as an established, active research focus, but without a normalized comparison with neural-network control it does not prove that MPC is the uniquely leading hotspot.

The Gong PSO-MPC study connects directly to greenhouse environmental-control research by using PSO to identify optimal MPC control parameters; it reports that this search outperformed traditional genetic-algorithm optimization and presents the approach as having potential to increase crop yield while minimizing energy costs [185].

rejected: no_entity. Reason: Morales-García et al. (2023) is relevant as a GAN-assisted greenhouse climate-prediction study: synthetic data were used for a temperature-focused prediction system with horizons from the next 24 hours up to two months [145][143]. Because the evidence describes prediction rather than a verified controller, the candidate should remain uncertain for a focused control-case table [144]. Allowed numbers: next 24 hours up to two months; 2020 year; 14%; 4%; 2020; 2021; empty; 2023 calendar year; 2023; 2024 calendar year. Allowed citations: [143][144][145][147][149][150][153][157][170][185][117][118][190][132][193][133]. Allowed entities: Morales-García et al. (2023), Data-driven evaluation of machine learning models for climate control in operational smart greenhouses; Jung et al. (2020), Model Predictive Control via Output Feedback Neural Network for Improved Multi-Window Greenhouse Ventilation Control; Model Predictive Control (MPC).

The Gong candidate contributes to the overall purpose by applying PSO to MPC parameter selection for greenhouse control; the reported comparison shows that the PSO search outperformed traditional genetic-algorithm optimization and links it to potential yield gains with lower energy costs [185].

MPC is explicitly labeled research-hotspot evidence in 2021 [132], but the material does not establish a comparable hotspot status for neural-network control; the combined-hotspot statement should therefore be treated as a qualified motivation, not an established classification.

Gong's PSO-MPC candidate advances the greenhouse-control purpose by optimizing control parameters against crop-yield and energy-cost objectives; its reported PSO search outperformed traditional genetic-algorithm optimization [185].

MPC is explicitly identified as research-hotspot evidence in 2021 [132], and a 2023 greenhouse MPC contribution shows continued activity [118]. This supports an active-focus classification, but not a comparative claim that MPC is the leading hotspot across the whole window.

The Gong PSO-MPC result is evidence of active MPC research because its PSO search outperformed traditional genetic-algorithm optimization and was linked to potential crop-yield improvement with lower energy costs [185]. It does not by itself establish the combined neural-network/MPC hotspot claim, so that motivation should remain qualified.

rejected: no_entity. Reason: Using a common calendar-year basis, the Jung et al. case is assigned 2020 as its research year; no separate publication or experiment year is supplied, so the inclusion year should not be conflated with either [157]. Allowed numbers: empty; 2020 year; 14%; 4%; 2020; 2021; 2023 calendar year; 2023; 2024 calendar year. Allowed citations: [147][149][150][153][157][170][185][117][118][190][132][193][133]. Allowed entities: Jung et al. (2020), Model Predictive Control via Output Feedback Neural Network for Improved Multi-Window Greenhouse Ventilation Control; Model Predictive Control (MPC).

rejected: no_entity. Reason: Jung et al. (2020) provides a dated greenhouse-control case [157][194], but that case alone does not establish current hotspot status for neural-network control or MPC; the hotspot statement should remain a motivation for further comparison rather than a conclusion. Allowed numbers: empty; 2020; 2020 year; Et ¼ 129.89; 14%; 4%; 2021; 2023 calendar year; 2023; 2024 calendar year. Allowed citations: [147][149][150][153][157][170][185][117][118][190][132][193][133][194]. Allowed entities: Jung et al. (2020), Model Predictive Control via Output Feedback Neural Network for Improved Multi-Window Greenhouse Ventilation Control; Model Predictive Control (MPC).

rejected: no_entity. Reason: Jung et al. (2020) provides a dated greenhouse-control case [157][194], but that case alone does not establish current hotspot status for neural-network control or MPC; the hotspot statement should remain a motivation for further comparison rather than a conclusion. Allowed numbers: empty; 2020; 2020 year; Et ¼ 129.89; 14%; 4%; 2021; 2023 calendar year; 2023; 2024 calendar year. Allowed citations: [147][149][150][153][157][170][185][117][118][190][132][193][133][194]. Allowed entities: Jung et al. (2020), Model Predictive Control via Output Feedback Neural Network for Improved Multi-Window Greenhouse Ventilation Control; Model Predictive Control (MPC).

rejected: no_entity. Reason: Jung et al. (2020) provides a dated greenhouse-control case [157][194], but that case alone does not establish current hotspot status for neural-network control or MPC; the hotspot statement should remain a motivation for further comparison rather than a conclusion. Allowed numbers: empty; 2020; 2020 year; Et ¼ 129.89; 14%; 4%; 2021; 2023 calendar year; 2023; 2024 calendar year. Allowed citations: [147][149][150][153][157][170][185][117][118][190][132][193][133][194]. Allowed entities: Jung et al. (2020), Model Predictive Control via Output Feedback Neural Network for Improved Multi-Window Greenhouse Ventilation Control; Model Predictive Control (MPC).

## Model Predictive Control research cases, 2017–2023

### Concrete cases and their main findings

**MPC cases increasingly connect several objectives.** The five examples below cover supervisory resource coordination, temperature–electricity management, weather uncertainty, yield–energy optimization, and nonlinear multivariable regulation. Particle swarm optimization (PSO) and genetic algorithms (GA) are optimization methods used within particular MPC formulations, rather than separate top-level control categories.

| Specific Control Algorithm Used | Target Control Parameters | Main Conclusions or Achievements | Year of Research | Reference (Author and Year Only) |
|---|---|---|---|---|
| Supervisory MPC | Lighting, CO₂ rate, temperature, and humidity | Numerical cases maintained acceptable climate while optimizing photosynthesis, water, and energy | 2020 | Achour et al. (2020) [26] |
| Multiobjective receding-horizon MPC | Indoor temperature through heat-pump water flow | Site-informed model comparison: approximately 30% lower electric power versus relay over 20 hours | 2021 | Bersani et al. (2021) [2] |
| Data-driven robust MPC with clustered uncertainty sets | Temperature, humidity, CO₂, and crop growth | Case-study gains: power-usage efficiency 3.61–7.32%; crop production 0.76–16.25% | 2022 | Hu & You (2022) [7] |
| PSO-MPC with climate and crop-yield models | Heating, lighting, and ventilation | Simulation used less energy for the same yield than rule-based control; outperformed tested GA | 2023 | Gong, Yu & Kollias (2023) [37] |
| GA-based nonlinear MPC | Temperature, humidity, and CO₂ | Simulation showed better control performance and stability than traditional PID | 2023 | Wang et al. (2023) [14] |

### Supervisory MPC: connecting climate with resources

**Achour’s controller coordinates existing regulation.** The 2020 supervisory MPC design is intended for integration with existing greenhouse regulatory systems. It maintains artificial lighting, CO₂ rate, indoor temperature, and humidity within acceptable limits while considering crop photosynthesis, water, and energy. Its numerical cases include intermittent renewable energy and uncertainty in external atmospheric conditions. [26]

**Supervision changes the decision level.** A local temperature controller responds to a temperature requirement, whereas supervisory control can coordinate that requirement with lighting, CO₂, and resource availability. The contribution is therefore not merely a more sophisticated heater command. It is an architecture for choosing compatible environmental and resource decisions above the individual equipment loops.

**The mechanism addresses competing consequences.** Climate actions have agricultural benefits and resource costs, and renewable-energy availability can vary over time. A predictive optimizer can represent these relationships over a horizon and select actions that remain compatible with the stated climate limits. This is the main reason the study is relevant to the food–energy–water connection rather than temperature control alone. [26]

**The appropriate application is coordinated management.** This design is especially relevant when a greenhouse already has functioning regulatory equipment but needs better coordination among its operating objectives. Its advantage depends on whether the supervisory model captures the relationships that materially affect those decisions. Improving one local loop may be sufficient when the wider coordination problem is small.

Achour et al. illustrate MPC’s value as a supervisory decision layer that can complement, rather than necessarily replace, conventional regulation.

### Temperature–electricity control: interpreting the 30% result

**Bersani’s reported saving is approximately 30%.** The 2021 study uses a nonlinear greenhouse and heating-system model informed by the instrumented SamLab greenhouse in Albenga, Italy. It compares MPC with relay control over 20 hours, reporting approximately 30% lower electric power use while maintaining a consistent temperature profile. The greenhouse measures 15.3 by 9.9 m, with an average height of 4.5 m. [2]

**The manipulated variable is water flow.** A ground-coupled heat pump supplies an air-handling unit, and MPC determines the water mass-flow command associated with greenhouse heating. Outdoor temperature and solar irradiance drive the prediction, while indoor temperature follows a predefined profile. The evaluated horizon uses three-minute intervals: 20 hours × 60 minutes ÷ 3 minutes gives 400 intervals. [2]

**Three objectives shape the control action.** The formulation penalizes changes in electric power between consecutive intervals, power use over the horizon, and temperature deviation from the tracked profile. These terms respectively discourage abrupt equipment behavior, reduce resource demand, and preserve environmental performance. Adjustable weights determine their relative importance. [2]

**The physical mechanism explains the saving.** Relay control repeatedly switches heating on and off, producing fluctuations in water temperature and power. MPC operates the modeled heat pump with lower supply-water temperature—approximately 312 K compared with 323 K in the reactive case—supporting a higher coefficient of performance. The coefficient of performance is the ratio of useful heating output to electrical input. [2]

**Energy reduction is compared with tracking.** Reducing relay output can lower power use, but the study shows that this can also weaken temperature tracking. Its comparison therefore examines the trade-off between electrical use and deviation, rather than judging a controller simply by whichever consumes least. The MPC solutions dominate the relay solutions in the reported simulation comparisons. [2]

**The best reported setting reaches 31%.** For the study’s selected comparison with \(\gamma=550\) and relay parameter \(crt=1.3\), the reported power saving is approximately 31%. This is consistent with the abstract’s approximately 30% summary; the two values describe a broad finding and a particular setting, rather than conflicting effects. [2]

**The application fit is equipment-specific.** A greenhouse with a heat pump and meaningful efficiency variation has a clear reason to optimize operating conditions as well as on/off timing. A different heating plant, thermal mass, or forecast quality can change the achievable benefit. The result supports this predictive operating mechanism, not a transferable 30% saving for every greenhouse.

Bersani et al. provide a concrete explanation of how predictive coordination can improve the relationship between climate tracking and electrical demand.

### Robust MPC: incorporating uncertain weather

**Hu and You quantify two outcomes.** Their 2022 greenhouse case reports increases of **3.61–7.32% in power-usage efficiency** and **0.76–16.25% in crop production**. The framework combines greenhouse and crop dynamics, data-driven system identification, and robust MPC. Crop growth is included among the modeled states, connecting environmental decisions with production outcomes. [7]

**Historical forecast errors define uncertainty.** Rather than treating future weather as exact, the method constructs uncertainty sets from historical weather-forecast errors. K-means clustering forms a group of disjunctive sets, while machine-learning methods help construct the individual sets. The intention is to capture plausible disturbance patterns without making every control action excessively conservative. [7]

**Conservatism is a practical trade-off.** A controller protecting against an unnecessarily broad collection of simultaneous worst cases may use resources inefficiently. A controller protecting against too narrow a disturbance description may fail to preserve the intended climate bounds. Data-driven uncertainty representation attempts to improve that balance by describing weather errors more selectively.

**The percentage outcomes remain distinct.** Power-usage efficiency is not the same quantity as electricity consumption, and crop production is another outcome again. The reported ranges therefore should not be added together or described as one overall efficiency increase. Their significance is that the controller evaluates resource and production consequences within the same greenhouse case.

**A related case offers another perspective.** A 2021 data-driven robust MPC study constructs weather-error uncertainty sets using support-vector clustering for ambient temperature, solar radiation, and humidity forecasts. In a semiclosed-greenhouse case in New York City, it reports 14% lower total cost than rule-based control and 4% lower cost than robust MPC using an \(L_1\)-norm uncertainty set. [15]

**Constraint behavior is evaluated explicitly.** That study reports greenhouse-state constraint violations during 0.39% of the growing period. This is useful alongside the cost comparisons because it shows how environmental feasibility is assessed, rather than presenting resource savings alone. It also illustrates why practical constraint performance should be described with the model, uncertainty treatment, and evaluation period attached. [15]

**Robust designs fit consequential forecast error.** They are especially relevant when weather uncertainty materially changes decisions about heating, ventilation, humidity, or crop conditions. The judgment changes if the uncertainty model is poorly matched to future conditions or if the protection it introduces costs more than it saves. Robust MPC is consequently a design family with choices, not a single fixed algorithm.

Hu and You’s case demonstrates why uncertainty representation became an important part of greenhouse MPC research.

### Nonlinear optimization: PSO-MPC and GA-MPC

**Gong’s controller optimizes yield and energy.** The 2023 PSO-MPC study combines a greenhouse climate model with a crop-yield model. Heating, lighting, and ventilation are optimized to increase crop yield while reducing energy-consumption costs. The crop model links climate variables with photosynthesis, carbohydrate allocation, and harvested dry matter. [22]

**The crop model changes the objective.** A climate controller could maintain suitable temperature without accounting for how lighting and CO₂ influence growth. By connecting climate prediction with a crop model, the optimization evaluates actions through their predicted production consequences. The resulting decision is therefore a yield–resource compromise, not simply a tighter environmental setpoint.

**Actual weather drives simulated outcomes.** The evaluation uses a real-greenhouse configuration and ten days of weather information, including irradiation, temperature, vapor concentration, CO₂, and wind. Indoor climate and crop yield are generated by the models. The study reports that PSO-MPC uses less energy than rule-based control for the same yield over the evaluated intervals. [22]

**PSO searches candidate actuator combinations.** The optimizer uses a population of ten particles and five generations in the reported implementation. Candidate control values are bounded between zero and one for the modeled equipment settings. This optimization layer is what selects the control sequence; it is not itself the greenhouse dynamics model. [22]

**The optimizer comparison is setting-dependent.** Under the same population and generation settings, the tested GA produces negative growth in the reported comparison, while PSO finds positive-growth solutions. This supports PSO for that particular formulation and computational setup. It does not establish that GA is generally unsuitable for greenhouse predictive control, especially because a different 2023 study reports successful GA-based nonlinear MPC. [22][14]

**Wang’s study targets coupled climate regulation.** The northeastern-China greenhouse simulation combines a GA with nonlinear MPC for temperature, humidity, and CO₂. It reports better control performance and stability than traditional PID and states that the modeled greenhouse demand is met. Its principal comparison is climate-control behavior, whereas Gong et al.’s principal emphasis is the yield–energy relationship. [14]

**Model assumptions influence the preferred solution.** Gong et al.’s climate model assumes no spatial differences in temperature, vapor pressure, and CO₂ within its represented compartments and separates air above and below a thermal screen. Such simplification makes optimization more manageable but determines which greenhouse behavior the controller can represent. A spatially uneven greenhouse could change the importance of those assumptions. [22]

**The useful comparison concerns the full formulation.** Choosing between PSO-MPC, GA-MPC, or another nonlinear MPC implementation requires considering the dynamic model, objectives, constraints, horizon, and optimization budget together. The algorithm name alone does not explain why one implementation performs better. These studies are most informative when read as completed comparisons within specific models.

The two 2023 cases support nonlinear MPC’s flexibility while showing that optimizer rankings belong to particular problem settings.

### Neural networks and MPC can work together

**The approaches solve complementary problems.** Neural modeling learns difficult relationships, while MPC selects actions under stated objectives and constraints. The Chilean 2023 energy–water management system explicitly combines neural-network modeling, MPC, and fuzzy optimization. It illustrates a practical route from the two research hotspots toward one integrated architecture. [16]

**Separate networks forecast external climate.** MLP networks predict ambient temperature, relative humidity, and solar irradiance using up to 144 regressors, equivalent to one day of information. Each network contains a hidden layer and an output layer, with 40–200 hidden neurons considered. A phenomenological model translates external forecasts into internal greenhouse climate estimates. [16]

**Two timescales divide the management task.** Short-term prediction spans 48 hours with a ten-minute sample time. Medium-term prediction spans 28 days with a one-day sample time, supporting estimates of crop water demand. Associated decisions include irrigation, reserve-tank refilling, ventilation, window opening, and pump operation. [16]

**The division follows different process speeds.** Immediate climate operation and water demand over a growing period are related but do not require identical decision intervals. Coordinating their timescales helps connect greenhouse environmental control with water reserves and energy management. The case study in the José Painecura Hueñalihuen Mapuche community reports reduced energy consumption and optimized irrigation. [16]

**Hybridization transfers rather than removes burdens.** Neural forecasting introduces dependence on weather data and training coverage; the internal climate model introduces physical assumptions; and MPC introduces optimization requirements. The integration is valuable when these components address different consequential parts of the greenhouse problem. Its practical merit depends on the coordinated system, not on the presence of three advanced techniques.

### Why MPC became a research hotspot

**Its appeal follows the decision structure.** Modern greenhouse operation combines nonlinear climate dynamics, equipment limits, resource costs, uncertain weather, and crop objectives. MPC offers an explicit way to connect these considerations over time. The reviewed cases show this progression from temperature management toward photosynthesis, water coordination, crop growth, and uncertain energy conditions. [26][7]

**Published attention provides a coarse indicator.** Bersani et al.’s 2020 review reports approximately 3,500 Google Scholar keyword results for greenhouse MPC during 2015–2020, compared with approximately 2,200 for 2000–2015. These unequal-duration keyword-result windows indicate research attention, not counts of unique eligible greenhouse experiments, deployment rates, or a publication-growth estimate. [38]

**The remaining challenge is reliable execution.** A useful predictive controller needs a model that remains informative, forecasts that support decisions, and optimization that fits the operating interval. Robust formulations address uncertainty, while neural models and hybrid architectures can address difficult dynamics or prediction tasks. None of these additions eliminates the need to demonstrate the behavior of the complete control loop.

The MPC evidence is strongest for its ability to formulate coordinated climate–resource decisions, with actual benefits determined by the greenhouse, model, objectives, and comparison baseline.

**Additional documented evidence**

For MPC, the permitted evidence supports **bounded research prominence**, not proven commercial dominance. A 2023 greenhouse-control study calls MPC the most commonly used approach in the scientific literature for greenhouse climate control and compares it with reinforcement learning, but the comparison is simulation-based [162]. Repeated in-window examples include Jung et al.’s **2020** output-feedback neural-network MPC ventilation study, 2021 predictive-control work, and 2023 PSO-MPC studies [188][132][196][118]. This supports “research-active” or “prominent,” not a publication-count ranking or deployment-prevalence claim.

Neural-network control is also active, but its hotspot status is less secure when controller centrality is required. A review of 35 greenhouse studies reports **46%** feedforward, **20%** recurrent, and **32%** other neural-network investigations; much of the literature concerns microclimate prediction rather than autonomous control [189]. The strongest direct case is Jung et al. (2020), where output-feedback neural-network prediction and optimization reduced ventilation-temperature RMSE from **3.01 °C** under conventional logic to **2.45 °C** in a six-day field comparison [188]. Prediction-only and soft-sensor studies demonstrate activity but do not establish a controller hotspot [141][142][148].

## Selection guidance for greenhouse applications

### Match the method to the dominant requirement

**Start with the actual decision problem.** If the requirement is a stable temperature or humidity loop with manageable coupling, PID offers a clear baseline. If the task is maintaining a measured variable within a simple range, basic feedback may suffice. Introducing a more elaborate controller is justified when it resolves a specific problem such as delay, parameter variation, actuator interaction, or competing resource objectives.

**Use rules when expertise is actionable.** Fuzzy control is attractive where operators understand how combinations of conditions should influence equipment but a reliable mathematical model is difficult to obtain. Its interpretability is useful only while the rules remain coherent and manageable. If rule maintenance becomes the main burden, learning-assisted tuning or a different architecture may be preferable.

**Use adaptation for changing relationships.** Adaptive control fits situations where fixed parameters repeatedly lose suitability as greenhouse dynamics change. Its update mechanism should address that persistent change rather than merely chase transient weather fluctuations. When the main issue is uncertain future weather instead, robust predictive control addresses a different and often more appropriate requirement.

**Use neural models for difficult prediction.** A greenhouse with substantial operating data can benefit from neural forecasts or estimation before adopting direct learned actuator control. The Song, Moon, González Pérez, and Ullah cases illustrate distinct prediction and information-quality contributions. The strongest architecture is the one whose inputs and forecast horizon represent the intended decisions, not necessarily the deepest network. [17][27]

**Use MPC for interacting constrained choices.** MPC is particularly appropriate when heating, ventilation, lighting, CO₂, water, and crop outcomes need coordinated decisions. Its advantages are most consequential when equipment bounds and resource trade-offs materially affect what the controller should do. Achour et al.’s supervisory architecture also shows that this capability can be added above existing regulatory systems. [26]

### What the evidence implies for research and deployment

**Combination is a supported direction.** The 2017 neural–fuzzy system and the 2023 neural-model–MPC–fuzzy optimization system demonstrate complementary roles for prediction and decision-making. They support investigating integrated architectures where each component solves an identifiable task. They do not imply that every greenhouse needs the same combination.

**Control outcomes should guide model choice.** A predictor that improves average RMSE is useful when that improvement leads to better actuator decisions, fewer consequential deviations, or more efficient resource use. Conversely, small prediction differences may matter little if both controllers remain within an acceptable crop interval. Su et al.’s interval-based energy-saving approach provides a concrete reason to evaluate environmental acceptability alongside tracking precision. [18]

**The deciding conditions are operational.** Stronger recommendations for neural, MPC, or hybrid control depend on representative seasonal and crop data, informative models and forecasts, feasible computation, and benefits that persist in the intended greenhouse. Changes in these conditions can reverse the preferred choice. This is why the literature supports fit-for-purpose selection more strongly than a universal ranking.

**Measurement bases remain study-specific.** This is a representative comparative review, not a publication-frequency census. Prediction tests, control simulations, hardware-in-the-loop evaluations, and field trials support different conclusions. Aytenfsu’s MSE, Choab’s aggregate RMSE, and Song’s tabulated RMSE retain their original evaluation scales; Jia’s humidity error retains the published “%” notation. Correlation \(R\), determination \(R^2\), tracking error, power, efficiency, cost, and crop production are separate measures. Choab’s record distinguishes 2021 proceedings from 2022 copyright. Gong et al.’s narrative gives 21-, 41-, and 61-hour tests, while its third comparison-table caption says 81 hours. Derived reductions and interval counts above are labeled calculations, not new experiments.

**The overall judgment is conditional but clear.** PID and basic feedback remain sound foundations; fuzzy and adaptive methods address particular nonlinear or changing behavior; neural networks contribute learned prediction and control relationships; and MPC provides a strong basis for coordinated constrained optimization. For demanding greenhouse applications, the most useful development is often a carefully evaluated combination of these roles.

## References

[1] <https://doi.org/10.3390/s20061756> Ventilation field study; Neural-assisted ventilation field comparison
[2] <https://www.mdpi.com/1996-1073/14/11/3353> Greenhouse MPC comparison; Italian MPC system; Equipment-constrained MPC; Tracking–power trade-off; Albenga MPC comparison; Model and sampling details; Multiob…
[3] <https://doi.org/10.1109/access.2020.3030416> Self-tuning PID study; PID tuning and coupling; Four-loop self-tuning design; Adaptive PID trade-offs; Model uncertainty discussion; Decoupling trade-off; Cont…
[4] <https://doi.org/10.17265/1934-7332/2016.06.002> Multivariable fuzzy-control study; Rule-base complexity
[5] <https://doi.org/10.1109/access.2023.3346436> Smart-greenhouse sensing and correction
[6] <https://doi.org/10.1134/s1064230714050074> Adaptive microclimate control; Adaptive MIMO controller mechanism
[7] <https://doi.org/10.1109/adconip55568.2022.9894133> PID–MPC trade-offs; MPC definition and implementation principle; Robust greenhouse MPC; Data-driven uncertainty treatment; Robust predictive control; Robust MP…
[8] <https://www.mdpi.com/2076-3417/10/11/3835> Greenhouse dynamics review; ANN principles and applications; Feedforward and recurrent architectures; Neural model development
[9] <https://doi.org/10.3390/agriculture12111916> Hybrid VPD regulation
[10] <https://www.mdpi.com/1996-1073/10/5/722> Italian neural–fuzzy system; Neural–fuzzy control; Fuzzy greenhouse controller architecture; Parallel fuzzy control; Neural–fuzzy design; Forecast-driven fuzzy…
[11] <https://www.hst-j.org/articles/pdf/ozK9/kshs-2020-038-02-8.pdf> Korean mango greenhouse; LSTM memory mechanism; CO₂ forecasting behavior; Mango-greenhouse LSTM study; CO₂ prediction results; Crop-input and site consideratio…
[12] <https://doi.org/10.1109/worlds450073.2020.9210373> Ethiopian recurrent-network study; Elman greenhouse prediction
[13] <https://www.scitepress.org/Papers/2021/107274/107274.pdf> Moroccan prediction study; MLPNN thermal-behavior prediction
[14] <https://doi.org/10.1109/ccdc58219.2023.10326486> Chinese nonlinear MPC study; GA-based nonlinear MPC; Nonlinear GA-MPC comparison
[15] <https://doi.org/10.1109/tcst.2021.3094999> New York robust MPC case; New York robust MPC comparison; Constraint-violation result
[16] <https://doi.org/10.3390/app13084734> Chilean energy–water system; Integrated predictive control; Integrated predictive design; Integrated energy–water controller; Neural weather-model design; Pred…
[17] <https://doi.org/10.7736/kspe.2019.36.3.239> Prediction and equipment delays; Forecast-horizon comparison; Multidimensional LSTM experiment; January forecast comparison; Full monthly results; Horizon sele…
[18] <https://link.springer.com/article/10.1007/s12555-016-0220-6> Interval-based energy-saving control; Saturation compensation; Fuzzy adaptive control; Fuzzy adaptive energy management; Crop-interval control objective
[19] <https://www.diva-portal.org/smash/get/diva2:1353095/FULLTEXT01.pdf> Greenhouse feedback architecture; PID operating principle; Closed-loop greenhouse regulation
[20] <https://doi.org/10.12972/pastj.20230008> PID climate-regulation review
[21] <https://www.sciopen.com/article/10.11975/j.issn.1002-6819.202310214> Disturbance-handling discussion; Application-based control comparison; Data-driven regulation trends
[22] <https://www.mdpi.com/1999-4893/16/5/243> Multi-actuator applications; Greenhouse climate and crop optimization; Yield–energy MPC; PSO-MPC study; Evaluation setting and comparison; PSO implementation d…
[23] <https://doi.org/10.1109/coins54846.2022.9854938> Closed-loop control overview
[24] <https://doi.org/10.14483/22484728.18439> Drainage-feedback irrigation example
[25] <https://doi.org/10.1109/sta.2019.8717273> Online neural adaptation
[26] <https://doi.org/10.1109/access.2020.3037222> Supervisory food–energy–water control; Photosynthesis-oriented MPC; Supervisory greenhouse MPC; Integrated objectives and uncertainty; Supervisory objectives;…
[27] <https://doi.org/10.17979/spudc.9788497497565.0875> Data-driven climate modeling; Actuator-aware climate modeling; Actuator-aware modeling
[28] <https://doi.org/10.3390/app132212341> Seasonal temperature forecasting; Seasonal forecasting results; Season and horizon effects
[29] <https://doi.org/10.4028/www.scientific.net/amm.687-691.3395> Fuzzy-PID design; 2014 fuzzy-PID greenhouse study
[30] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9612366/> Deep-learning challenges; Deep learning in controlled environments
[31] <https://doi.org/10.1109/smartnets48225.2019.9069766> Long-horizon greenhouse forecasting
[32] <https://ieeexplore.ieee.org/ielx7/6287639/8948470/09166496.pdf> ANN-enhanced greenhouse estimation
[33] <https://doi.org/10.20965/ijat.2021.p0243> FNN comparison
[34] <https://doi.org/10.1080/08839514.2021.1995232> Deep neural greenhouse control; Cascade-control results
[35] <https://snu.elsevierpure.com/en/publications/time-serial-analysis-of-deep-neural-network-models-for-prediction/> Time-series greenhouse comparison
[36] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10304734/> Hydroponic greenhouse model comparison; Dataset and input considerations
[37] <https://doi.org/10.3390/a16050243>
[38] <https://doi.org/10.3390/en13143647> MPC research-interest discussion
[39] <https://doi.org/10.13031/aim.20152188033>
[40] <https://doi.org/10.1109/gecs.2017.8066169>
[41] <https://www.mdpi.com/1424-8220/20/6/1756>
[42] <https://www.hst-j.org/articles/xml/ZzWo/>
[43] <https://www.past.or.kr/articles/article/rBR0/>
[44] <https://www.ijeijournal.com/papers/Vol12-Issue9/1209156167.pdf>
[45] <https://doi.org/10.5194/ms-11-299-2020>
[46] <https://rroij.com/open-access/feedback-techniques-using-pid-and-piintelligentfor-greenhouse-temperature-control.pdf>
[47] <https://www.zhinst.com/en/resources/principles-of-pid-controllers/>
[48] <https://doi.org/10.1109/saci.2014.6840039>
[49] <https://www.kci.go.kr/kciportal/ci/sereArticleSearch/ciSereArtiView.kci?sereArticleSearchBean.artiId=ART003024543>
[50] <https://doi.org/10.1016/j.compag.2023.108578>
[51] <https://www.jstage.jst.go.jp/article/ijat/15/2/15_243/_pdf>
[52] <https://doi.org/10.12972/pastj.20230008>
[53] <https://doi.org/10.4028/www.scientific.net/amm.687-691.3395>
[54] <https://scholarworks.umt.edu/cgi/viewcontent.cgi?article=13166&context=etd>
[55] <https://edepot.wur.nl/646861>
[56] <https://www.diva-portal.org/smash/get/diva2:1353095/FULLTEXT01.pdf>
[57] <https://www.mdpi.com/1996-1073/14/11/3353>
[58] <https://doi.org/10.1109/access.2020.3030416>
[59] <https://en.wikipedia.org/wiki/PID_controller>
[60] <https://doi.org/10.34163/jkits.2018.13.1.001>
[61] <https://search.proquest.com/openview/6a81ec0b23c9e2b95351321f9196367a/1?cbl=2032333&pq-origsite=gscholar>
[62] <https://iopscience.iop.org/article/10.1088/1742-6596/2510/1/012022/pdf>
[63] <https://doi.org/10.46792/fuoyejet.v8i4.1144>
[64] <https://www.frontiersin.org/journals/sustainable-food-systems/articles/10.3389/fsufs.2023.1074419/full>
[65] <https://www.mdpi.com/2079-9292/13/11/2083>
[66] <https://doi.org/10.3390/app13127151>
[67] <https://doi.org/10.5307/jbe.2017.42.1.023>
[68] <https://doi.org/10.35741/issn.0258-2724.58.3.14>
[69] <https://www.academia.edu/49038717/Climate_Control_of_Greenhouse_Using_Fuzzy_Logic_and_PID_Controllers>
[70] <https://www.mdpi.com/2076-3417/10/4/1350>
[71] <https://doi.org/10.31026/j.eng.2015.02.07>
[72] <https://doi.org/10.2991/icismme-15.2015.157>
[73] <https://doi.org/10.22364/bjmc.2023.11.1.12>
[74] <https://doi.org/10.3390/en14113353>
[75] <https://riviste.fupress.net/index.php/IJAm/article/view/3502>
[76] <https://www.mdpi.com/2624-6511/7/3/55>
[77] <https://www.atlantis-press.com/journals/ijcis/125905641/view>
[78] <https://doi.org/10.3390/electronics6040071>
[79] <https://www.mdpi.com/1996-1073/10/5/722>
[80] <https://www.sciopen.com/article/10.11975/j.issn.1002-6819.202310214>
[81] <https://www.mdpi.com/1424-8220/23/8/4088>
[82] <https://doi.org/10.5424/sjar/2023211-19392>
[83] <https://doi.org/10.47176/jspi.11.2.19011>
[84] <https://doi.org/10.12700/aph.11.06.2014.06.4>
[85] <https://doi.org/10.5815/ijmsc.2017.03.02>
[86] <https://doi.org/10.3390/app13084734>
[87] <https://doi.org/10.1109/imcec.2018.8469546>
[88] <https://etasr.com/index.php/ETASR/article/view/2871>
[89] <https://www.mdpi.com/2079-9292/6/4/71>
[90] <https://doi.org/10.21273/hortsci11385-16>
[91] <https://www.nyserda.ny.gov/-/media/Project/Nyserda/Files/Publications/Research/Other-Technical-Reports/21-19-Adaptive-Lighting-Controller-Technology-for-Greenhouses.pdf>
[92] <https://www.tandfonline.com/doi/full/10.1080/00207721.2018.1440025>
[93] <https://www.mdpi.com/2073-4395/10/7/936>
[94] <https://doi.org/10.1016/j.ifacol.2023.10.668>
[95] <https://www.tandfonline.com/doi/full/10.1080/21681015.2015.1048752>
[96] <https://doi.org/10.3390/app10113835>
[97] <https://doi.org/10.1109/ccdc52312.2021.9601368>
[98] <https://doi.org/10.1134/s1064230714050074>
[99] <https://doi.org/10.1109/sta.2019.8717273>
[100] <https://doi.org/10.1016/j.compag.2018.06.004>
[101] <https://doi.org/10.3390/en12091749>
[102] <https://www.mdpi.com/2073-4433/13/8/1258>
[103] <https://eurekamag.com/research/094/855/094855090.php>
[104] <https://dl.acm.org/doi/10.1016/j.compag.2018.02.001>
[105] <https://doi.org/10.14569/ijacsa.2018.090147>
[106] <https://onlinelibrary.wiley.com/doi/10.1155/2018/2071585>
[107] <https://link.springer.com/article/10.1007/s12555-016-0220-6>
[108] <https://doi.org/10.1109/chicc.2015.7259981>
[109] <https://www.water-energy-food.org/resources/research-article-energy-water-management-system-based-on-mpc-for-a-greenhouse-in-a-mapuche-indigenous-community>
[110] <https://doi.org/10.1016/j.inpa.2018.04.003>
[111] <https://ideas.repec.org/a/eee/appene/v343y2023ics0306261923005548.html>
[112] <https://doi.org/10.1109/jiot.2022.3196053>
[113] <https://arxiv.org/html/2303.06110v1>
[114] <https://upcommons.upc.edu/bitstreams/621b9d96-23d5-46dc-875c-08be8c7fc928/download>
[115] <https://dl.acm.org/doi/10.1016/j.compag.2023.108372>
[116] <https://doi.org/10.3390/en13143647>
[117] <https://doi.org/10.48550/arxiv.2303.06110>
[118] <https://doi.org/10.1109/tase.2023.3271896>
[119] <https://www.cetjournal.it/cet/23/103/019.pdf>
[120] <https://doi.org/10.1109/access.2023.3346436>
[121] <https://www.sciencedirect.com/science/article/abs/pii/S0306261923012047>
[122] <https://doi.org/10.14257/ijca.2018.11.10.02>
[123] <https://psecommunity.org/wp-content/plugins/wpor/includes/file/2304/LAPSE-2023.32802-1v1.pdf>
[124] <https://sah.borca.ai/papers/258572444>
[125] <https://khu.elsevierpure.com/en/publications/model-predictive-control-via-output-feedback-neural-network-for-i/>
[126] <https://doi.org/10.1016/j.inpa.2023.04.003>
[127] <https://doi.org/10.1051/e3sconf/202122901001>
[128] <https://www.mdpi.com/2076-3417/13/8/4734>
[129] <https://www.sciencedirect.com/science/article/pii/S2214317317301828>
[130] <https://www.sciencedirect.com/science/chapter/bookseries/abs/pii/B9780323958790501764>
[131] <https://doi.org/10.1109/adconip55568.2022.9894133>
[132] <https://pure.tudelft.nl/ws/portalfiles/portal/124689178/Predictive_Control_of_Autonomous_Greenhouses_A_Data_Driven_Approach.pdf>
[133] <https://doi.org/10.1109/tcst.2021.3094999>
[134] <https://doi.org/10.23919/acc.2017.7963065>
[135] <https://doi.org/10.22541/essoar.167979157.76638109/v1>
[136] <https://link.springer.com/book/10.1007/978-0-85729-664-1>
[137] <https://www.mdpi.com/1424-8220/16/7/1018>
[138] <https://www-personal.umich.edu/~ykoren/uploads/Principal_development_in_AC.pdf>
[139] <https://www.eolss.net/sample-chapters/c18/E6-43-15-00.pdf>
[140] <https://www.fujipress.jp/jaciii/jc/jacii002900061464/>
[141] <https://doi.org/10.3390/s23031250>
[142] <https://doi.org/10.1016/j.compag.2023.108537>
[143] <https://repositorio.ucam.edu/bitstream/handle/10952/10260/2024%20-%20JAISE%20-%20GreenhouseGuard%20Enabling%20real-time%20warning%20prediction%20for%20smart%20greenhouse%20management.pdf?isAllowed=y&sequence=1>
[144] <https://doi.org/10.2139/ssrn.4618440>
[145] <https://link.springer.com/article/10.1007/s10489-023-04783-2>
[146] <https://www.americaspg.com/article/391/pdf/stream>
[147] <https://doi.org/10.1016/j.apenergy.2023.121190>
[148] <https://doi.org/10.1007/s11227-023-05076-8>
[149] <https://doi.org/10.23919/ecc57647.2023.10178137>
[150] <https://www.cetjournal.it/index.php/cet/article/view/CET23103019>
[151] <https://www.alphaxiv.org/abs/2506.13278>
[152] <https://www.academia.edu/91188537/Modeling_and_optimization_of_environment_in_agricultural_greenhouses_for_improving_cleaner_and_sustainable_crop_production>
[153] <https://dash.harvard.edu/bitstreams/c828e84b-0508-46e8-bc13-0fdc40e573b9/download>
[154] <https://ideas.repec.org/a/eee/appene/v348y2023ics0306261923008140.html>
[155] <https://ideas.repec.org/a/eee/rensus/v168y2022ics1364032122006748.html>
[156] <https://scholar.google.com/citations?user=NI46C-cAAAAJ&hl=es>
[157] <https://www.tandfonline.com/doi/pdf/10.1080/08839514.2021.1995232>
[158] <https://doi.org/10.1109/ecc.2014.6862215>
[159] <https://doi.org/10.33915/etd.3828>
[160] <https://doi.org/10.1007/978-3-319-04229-9_4>
[161] <https://www.frontiersin.org/journals/plant-science/articles/10.3389/fpls.2026.1742689/full>
[162] <https://arxiv.org/pdf/2303.06110>
[163] <https://doi.org/10.3390/en18215821>
[164] <https://www.nature.com/articles/s41598-025-27333-x>
[165] <https://www.mdpi.com/2311-7524/12/7/765>
[166] <https://www.mdpi.com/2071-1050/14/5/3062>
[167] <https://www.inderscience.com/info/inarticle.php?artid=88604>
[168] <https://doi.org/10.1109/ithings/greencom/cpscom/smartdata.2019.00059>
[169] <https://www.mdpi.com/2073-4395/12/9/2169>
[170] <https://scixplorer.org/abs/2024arXiv240912789M/abstract>
[171] <https://scholar.google.co.il/citations?hl=th&user=cv2tlzUAAAAJ>
[172] <https://scite.ai/reports/optimizing-crop-yield-and-reducing-EWrwAbr1>
[173] <https://doi.org/10.3390/s19081807>
[174] <https://doi.org/10.1016/j.sciaf.2023.e01578>
[175] <https://exaly.com/article/163195869>
[176] <https://doi.org/10.1109/cgee62671.2024.10955933>
[177] <https://doi.org/10.1109/ahpcai57455.2022.10087391>
[178] <https://doi.org/10.1016/j.enbuild.2024.115252>
[179] <https://repository.up.ac.za/server/api/core/bitstreams/51c088ad-4eb0-4760-88f9-67f79043c2eb/content>
[180] <https://arxiv.org/abs/2410.23793>
[181] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7146503/>
[182] <https://arxiv.org/abs/2303.06110>
[183] <https://www.sciopen.com/article/10.25165/j.ijabe.20241705.8241>
[184] <https://trepo.tuni.fi/bitstream/10024/122232/2/GladKaarle.pdf>
[185] <https://tlooto.com/paper/150262905235>
[186] <https://doi.org/10.3390/electronics13112083>
[187] <https://doi.org/10.1049/cth2.12467>
[188] <https://mdpi-res.com/d_attachment/sensors/sensors-20-01756/article_deploy/sensors-20-01756.pdf?version=1584865256>
[189] <https://www.mdpi.com/2076-3417/10/11/3835>
[190] <https://doi.org/10.1109/ccdc58219.2023.10326486>
[191] <https://www.sciengine.com/doi/pdf/CF8DFA925A0948E0A245894EDA68F994>
[192] <https://www.csauthors.net/liyun-gong/>
[193] <https://www.scilit.com/publications/f8e996b6263547670768a6883907a583>
[194] <https://doi.org/10.1609/aaai.v37i13.26867>
[195] <https://doi.org/10.1109/iciafs52090.2021.9605945>
[196] <https://www.mdpi.com/1999-4893/16/5/243>
