# Cloud Auto-Scaling: Technologies, Challenges, and Research Solutions

**Auto-scaling divides most clearly by timing.** Reactive methods change resources after observing demand or performance changes; proactive methods act before expected demand, using schedules, forecasts, or anticipatory policies. Threshold rules, feedback control, queue-based optimization, and learned reactive controllers belong in the first group. Scheduled scaling, statistical forecasting, predictive machine learning, and anticipatory reinforcement learning belong in the second. Hybrid systems combine the two, so an algorithm’s name alone does not determine its category. [1]

**The central trade-off is safe efficiency.** Reactive control avoids dependence on workload forecasts but must accommodate detection and provisioning delays. Proactive control can prepare capacity earlier, but prediction errors can create shortages or waste. Across energy management, telecommunications, big-data processing, graph analytics, and workload prediction, effective solutions connect demand estimation to the actual constraints of resource activation, application state, placement, and service performance. [2]

**The report answers two questions.** Part One explains how the main methods work, their advantages and limitations, and when each is appropriate. Part Two examines the five requested challenges, beginning with each problem’s concrete manifestation and then explaining a published research solution. Coverage concerns mainstream cloud auto-scaling and relevant research available through **13 September 2026**; older studies are identified as technical foundations or application examples, not descriptions of every current platform implementation.

## Auto-Scaling Technology Classification

**Timing and algorithm are separate dimensions.** A neural network that estimates the consequences of changing today’s capacity can support a reactive controller. The same kind of network can support proactive scaling when it forecasts tomorrow’s demand and initiates capacity changes beforehand. Queueing models and control theory also appear in both categories. Classification therefore depends on what triggers the action and whether resources are being prepared for a future requirement. [3]

**Selection depends on operational conditions.** The following comparison captures the main differences. Microsoft’s architecture guidance supports combining live-metric rules with scheduled or predictive scaling, while Amazon Web Services identifies recurring demand and long application initialization as particularly suitable cases for prediction. [4][5]

| Approach | Response latency | Prediction dependence | Operational overhead | Best workload fit |
|---|---|---|---|---|
| Reactive | Observation, decision, and startup delay | No future-demand forecast required | Low for rules; higher for models | Irregular demand with adequate headroom |
| Proactive | Capacity can precede demand | Schedule knowledge or forecast quality | Low for schedules; higher for learning | Recurring demand or slow initialization |
| Hybrid | Advance preparation plus corrective response | Forecasts with live feedback | Coordination of both mechanisms | Predictable baseline plus unexpected changes |

**Scaling direction is an independent choice.** Horizontal scaling adds or removes instances, virtual machines—VMs—or application replicas. Vertical scaling changes an existing resource’s capacity, such as processor allocation or memory. Either direction can be reactive or proactive. Horizontal scaling often preserves service through existing instances while new ones start; vertical resizing can require disruption, depending on the platform and resource involved. [4]

**Application readiness matters more than allocation.** Creating a VM does not immediately make its application useful. Software may still need to initialize, join a cluster, receive state, and become eligible for traffic. In container platforms, application replicas and underlying nodes are also separate scaling layers: Azure’s guidance distinguishes Kubernetes Horizontal Pod Autoscaler decisions from node-capacity provisioning. Increasing replica demand therefore does not guarantee that sufficient execution capacity already exists. [4]

**The service objective defines success.** A service-level agreement, or SLA, specifies contractual commitments; a service-level objective, or SLO, is a measurable operational target. An autoscaler might minimize resource cost while maintaining a response-time SLO, meet a batch-job deadline, or reduce energy without compromising availability. High resource utilization is consequently a means rather than the final objective: pushing utilization upward can reduce spare capacity precisely when demand becomes difficult to predict. [2]

**Every controller contains several delays.** A useful engineering accounting relation is that reactive response delay includes observation, decision, provisioning, and application-readiness time:

\[
D_{\mathrm{reactive}}=T_{\mathrm{observation}}+T_{\mathrm{decision}}+T_{\mathrm{provisioning}}+T_{\mathrm{readiness}}.
\]

All terms represent elapsed time in the same unit. A proactive forecast must provide enough usable lead time to cover the remaining decision and activation work. This explains why a sophisticated forecast with an unsuitable horizon may help less than a simple forecast aligned with actual startup time. The 2026 *Load-aware predictive auto-scaling framework for cloud environments* explicitly forecasts capacity at the point when newly provisioned VMs will become available. [6]

**Operational maturity varies across methods.** Metric rules, target-metric control, schedules, and provider-managed prediction are established operational mechanisms. Azure documents threshold, event-driven, scheduled, and predictive options, while AWS provides historical-load-based predictive scaling for EC2 Auto Scaling groups. More specialized systems discussed below—such as optimized queue policies, MLScale, and RLPAS—illustrate published research designs rather than interchangeable built-in cloud products. [4][5]

**The common structure is a control loop.** Qu, Calheiros, and Buyya describe auto-scaling through Monitoring, Analysis, Planning, and Execution, commonly abbreviated MAPE. Monitoring collects observations; analysis identifies a capacity problem; planning selects the resource change; execution performs it. This separation is useful because forecasting improves only part of the system: good analysis still needs a suitable capacity model and a reliable execution mechanism. [2]

### Reactive Methods

**Reactive methods respond to observed conditions.** Their practical strength is that they do not need to predict the arrival of every workload change. Their principal weakness is temporal: once a shortage has been detected, some requests may already be waiting while additional capacity becomes ready. The methods below differ mainly in how they interpret current conditions and calculate the size of the response.

| Method | Category | Core working principle | Main advantages | Main limitations |
|---|---|---|---|---|
| Threshold-based rules | Reactive | Apply actions when live metrics cross limits | Simple; transparent; platform-supported | Tuning, oscillation, delayed response |
| Feedback control | Reactive | Adjust resources from target-performance error | Explicit targets; disturbance correction | Stability tuning and activation delays |
| Queue-based optimization | Reactive | Optimize activation thresholds from queue state | Joint energy and service-cost reasoning | Queue assumptions and state-space growth |
| Supervised learned control: MLScale | Reactive | Predict performance under candidate resource changes | Multi-metric; application-agnostic | Training dependence; horizontal-only scope |

**Threshold-based rules provide explicit control.** The controller monitors a metric and applies an associated action when a condition persists or crosses a configured boundary. Signals can include central processing unit—CPU—utilization, memory use, network bandwidth, request rate, queue backlog, and application response time. Actions may add a fixed number of instances, remove instances, or adjust capacity according to the magnitude of the observed change. [1]

**A provider example shows the mechanism.** Azure’s architecture guidance illustrates scaling out by one instance when average CPU exceeds 70%, and scaling in by one instance when CPU falls below 50%. The two values create a gap between expansion and contraction. Both directions require appropriate rules; otherwise a configuration can keep scaling only one way until it reaches its configured capacity boundary. [4]

**Hysteresis reduces unnecessary reversals.** Hysteresis means using different conditions for increasing and decreasing capacity. Without it, a metric fluctuating near one boundary can repeatedly trigger opposing actions. A cooldown or stabilization interval can also allow the effect of a previous change to become visible before another decision is made. These mechanisms trade some responsiveness for fewer unnecessary changes; they do not eliminate the need to choose sensible thresholds and action sizes. [7]

**The advantages are simplicity and explainability.** Rules are easy to inspect, connect directly to monitoring systems, and offer predictable administrative control over minimum and maximum capacity. They are especially effective when the selected metric has a stable relationship with application demand and performance. A small team can often operate such a policy without maintaining a forecasting service or training pipeline. [1]

**Metric selection is the main weakness.** CPU saturation is useful for a processor-bound service but less informative when requests wait on storage, a database, or another service. Conversely, high CPU can reflect a software fault rather than legitimate demand. A 2024 IEEE Access study on service-function-chain scaling explicitly warns that pod-level utilization can be affected by container composition or software problems, making one infrastructure metric an imperfect indicator of microservice demand. [8]

**Event-driven scaling belongs in this family.** An event-based controller reacts to current HTTP traffic, messages, or other event-source measurements rather than necessarily relying on CPU. Azure Container Apps, for example, uses Kubernetes Event-driven Autoscaling, or KEDA, with HTTP traffic, event sources, CPU, and memory signals. Its advantage is closer alignment with actual work awaiting service; its limitation is that the observed event still has to be translated into sufficient ready capacity. Scaling to zero additionally depends on the rules and minimum replica configuration. [4]

**Unpredictability does not make rules useless.** Azure recommends metric-based scaling for unpredictable demand because a fixed calendar cannot capture it. That recommendation is compatible with research showing that thresholds struggle with abrupt spikes: live rules can handle irregular demand when reserve capacity and activation speed are sufficient, but cannot retroactively prevent the initial shortage caused by a faster-than-response surge. Adaptive thresholds improve policy tuning, yet remain reactive when actions still follow observed changes. [4][6]

**Feedback control regulates a measurable target.** Instead of expressing every situation as a separate rule, a feedback controller measures an output, compares it with a desired value, and computes an adjustment to resource input. The output might be response time, utilization, or stream-processing performance. The controller repeatedly observes the result of its own actions and corrects the remaining error. [3]

**The advantage is systematic correction.** A well-designed controller can respond to disturbances and return the system toward its target without an operator enumerating every possible workload condition. Control-theoretic design also makes stability and settling time explicit concerns. Stability here means avoiding sustained oscillation or divergence; settling time concerns how quickly performance returns near its desired operating point. [3]

**Streaming research provides a concrete example.** The published study *Feedback-Control & Queueing Theory-Based Resource Management for Streaming Applications* combines feedback control with queueing analysis to provision VMs against stream-specific performance targets. Its CometCloud evaluation also accounts for differences among execution sites, including capabilities, execution cost, and resilience-related characteristics. This extends the decision beyond “CPU is high” to whether available processing capacity can satisfy a particular data stream’s needs. [9]

**Delayed effects complicate controller tuning.** If an autoscaler adds capacity but checks again before that capacity becomes useful, the measured error may remain high. Repeated corrections can then allocate too much capacity. When all pending additions eventually become ready, the controller may reverse direction too aggressively. The practical challenge is therefore not simply making the loop fast, but making its decisions consistent with the system’s delayed response. [3]

**Feedback is not automatically predictive.** A controller responding only to measured error belongs under reactive methods, even if its mathematics is sophisticated. It becomes proactive when it incorporates an explicit prediction or look-ahead model that initiates action before the anticipated requirement. Feedback is preferable to a collection of independent rules when a meaningful target and a sufficiently reliable resource-performance relationship can be established; prediction becomes more valuable as activation delay increases.

**Queue-based optimization connects demand with service.** A queue model represents requests arriving, waiting, and receiving service from active resources. The autoscaler observes the number of requests and active servers, then decides whether to activate another server, deactivate one, or leave capacity unchanged. Unlike an arbitrary CPU threshold, the decision can be derived from a cost function that combines resource operation, waiting, rejected requests, and switching actions. [7]

**Little’s Law explains the performance connection.** Under stable averaging conditions, the mean number of admitted requests in a system equals its admitted arrival rate multiplied by mean time in the system:

\[
L=\lambda W.
\]

Here \(L\) is measured in requests, \(\lambda\) in requests per second, and \(W\) in seconds. This relationship helps connect queue observations with average response time. It does not, by itself, guarantee a tail-latency target such as a limit on the slowest 5% of requests. The queue-threshold study uses this kind of reasoning to connect occupancy and service commitments. [7]

**A published optimizer improves threshold selection.** *Efficient Computation of Optimal Thresholds in Cloud Auto-scaling Systems* compares local-search methods based on Markov-chain analysis with Markov decision process, or MDP, algorithms. An MDP represents states, available actions, transition behavior, and associated costs. The study optimizes hysteresis policies that use different activation and deactivation thresholds, reporting better numerical accuracy and computation times for its MDP approaches than for the compared local-search heuristics. [7]

**Its benefit is explicit multi-objective reasoning.** Keeping an extra VM active costs resources and energy, but deactivating it can increase waiting or require a later restart. The optimizer makes those competing consequences part of one decision rather than treating energy and service quality as unrelated afterthoughts. Optimized values can then be installed in a comparatively simple threshold-based execution policy. The optimization machinery and the runtime trigger are thus different parts of the same system.

**Model assumptions constrain its application.** The study’s controlled queue assumes Poisson arrivals, independent exponentially distributed service times, and equivalent server service rates. Its activation and deactivation actions are instantaneous in the model. It also excludes VM placement and migration. Those choices make threshold computation tractable, but a deployment with long startup times, strong resource heterogeneity, or expensive state transfer requires additional modeling. [7]

**Optimization time also grows with scale.** In the study’s high-scale numerical tests, the optimized hysteresis algorithm took about 2.4 seconds for 64 servers and a 400-request system capacity, but 22,850 seconds—about 6.3 hours—for 1,024 servers and a 6,400-request capacity. The useful conclusion is that structured optimization can support frequent policy recomputation at suitable sizes, not that every large cloud can recompute an exact policy instantaneously. [7]

**Supervised learning can remain entirely reactive.** MLScale, introduced by Wajahat and colleagues and examined in Lemke and Majumdar’s 2022 comparison, learns how resource and application metrics relate to response time. It monitors eight application-independent inputs, including request rate and average CPU use. A neural network estimates response time from those current observations. [10]

**Candidate actions receive performance estimates.** When the estimated response time indicates that capacity should change, MLScale uses multiple linear regression to estimate what its input metrics would look like after a candidate scaling operation. The neural network then evaluates the expected response time under those estimated post-scaling metrics. This allows the controller to choose a horizontal resource change based on a learned consequence model rather than only a manually chosen step size. [10]

**Its advantages concern generality and simplicity.** The method does not require detailed application internals, and the reviewed implementation uses a small network that can be trained in a few seconds. Multiple inputs can capture relationships that one or two manual thresholds overlook. Lemke and Majumdar report substantial improvements over manual threshold-based autoscalers in the studies they compare. [10]

**Fast training still requires useful data.** The same comparison describes collecting labeled examples from normal application behavior, ideally covering a variety of workload levels and scaling actions. A short training computation therefore does not remove the need to observe representative operating conditions. Application independence also does not mean that one trained model is automatically valid after an application or infrastructure changes.

**Its limits expose the timing distinction.** MLScale predicts performance under a decision, not the future arrival of an unseen surge. The reviewed design supports horizontal but not vertical scaling, and its reported evaluation incurred up to 5.9% SLA violations during large, sudden request spikes. Learned sizing can improve the response to a shortage while leaving the shortage’s initial detection delay unresolved. [10]

**Reactive selection should follow the bottleneck.** Threshold rules are attractive when operational simplicity and transparent guardrails dominate. Feedback control is stronger when the objective is continuous regulation around a target. Queue optimization is useful when waiting, resource activation, and service penalties can be modeled credibly; supervised control is useful when a learned multi-metric performance model improves action sizing. If demand can outrun the entire reaction path, each needs spare capacity, anticipation, or both.

**Additional documented evidence**

Threshold-based auto-scaling belongs to the Reactive category because it modifies resource availability in reaction to a predefined threshold value. [127]

Threshold-based auto-scaling is Reactive because it scales resources according to a predefined threshold; the study explicitly describes this as reactive auto-scaling using threshold-based rules. [102]

The source describes threshold-based autoscaling as a rule-based technique that makes a scaling decision when system performance exceeds predefined thresholds. This supports placement under Reactive when the verified criterion is decision timing, because the decision follows observed system performance rather than a forecast; the source does not itself use the label “Reactive.” [91]

The page classifies threshold-based autoscaling as a rule-based technique; it does not explicitly assign it to Reactive or Proactive under the requested two-category decision-timing taxonomy. [91]

The page provides evidence that threshold-based auto-scaling appears in a 2023 IEEE SmartData classification as a Proactive method, with SLA Assurance and Resource Efficiency as objectives. This supports current-method relevance, but the page does not itself establish mainstream status as of 2026-10-17. 2023 (the cited threshold-based classification; classification table). [103]

Threshold-based auto-scaling is repeatedly represented as an established heuristic method in the survey, including reactive threshold-based entries from 2021, 2022, and 2023, and the survey describes early approaches as basic threshold- and heuristic-based methods. This supports established research treatment, but the page alone does not establish the complete current-mainstream criterion as of 2026-10-17. 2021 (year of a threshold-based reactive entry; 2021; surveyed auto-scaling studies; survey classification). 2023 (year of threshold-based reactive entries; 2023; surveyed auto-scaling studies; survey classification). [103]

Threshold-based auto-scaling belongs to the Reactive category under the source's control-timing evidence: traditional heuristic-based approaches rely on predefined thresholds and reactive policies. [103]

The page describes threshold-based auto-scaling's analogous rule-driven principle as responding when a specified condition occurs: “If ‘X’ happens, send an alert.” [128]

Threshold-based autoscaling uses current performance and resource signals, including CPU utilization, memory consumption, network traffic, response time, request rate, and queue length. It triggers scaling when one or more metrics exceed predefined thresholds and removes excess resources when utilization falls below specified thresholds. The page gives an example of provisioning additional instances when CPU utilization exceeds 70% for a specified duration and terminating instances when CPU utilization remains below 30% for an extended duration. 70% % (CPU utilization; cloud applications using threshold-based autoscaling; threshold policy example). [96]

threshold-based auto-scaling: The rule-based comparison used maximum CPU utilization when the SLO was met as the HPA threshold; VPA used its default Auto mode. [129]

threshold-based autoscaling: Threshold-based auto-scaling reacts to current signals such as CPU/GPU utilization and queue depth; these lagging indicators trigger scaling, but the source says performance may already have degraded by then. [130]

threshold-based autoscaling: Threshold-based auto-scaling is a reactive, rule-based method. It uses predefined events and user-defined thresholds such as average memory consumption, memory usage, CPU utilization, and an 80% threshold in the evaluation. It is simple to implement but can mishandle rapidly varying workloads, over-provision stable workloads, provide poor QoS indication, require domain expertise, and make application-to-system metric mapping nontrivial. 80% % (threshold level; evaluation; reactive solutions in AWS/RUBiS evaluation; reactive threshold scaling). [34]

Threshold-based autoscaling compares observed system or workload metrics with preset thresholds and triggers scale-out or scale-in actions when the relevant thresholds are reached. [88]

threshold-based autoscaling: Threshold-based auto-scaling is reactive: it triggers scaling after threshold violations, using observed utilization or service signals to decide resource changes. Its main limitation is the temporal lag between a load surge and capacity adjustment. [131]

threshold-based autoscaling: Threshold-based auto-scaling belongs to the Reactive category because it modifies resource availability in reaction to a predefined threshold value. [127]

The paper contrasts predictive control with classical threshold-based autoscaling rules: the predictive controller uses forecasted and instantaneous metrics to make decisions that anticipate workload surges rather than relying only on current threshold crossings. [57]

threshold-based autoscaling: Reported limitations include cumbersome tuning for each service, possible over- or under-provisioning, delayed reaction to changing workloads, inability to account for metric dynamics, sensitivity to transient peaks and fluctuations, and delayed provisioning when new instances take time to start. In the experiment, three consecutive threshold violations and a 6-minute VM start delay caused the new VM to serve requests only after the cluster had been overloaded for about 8 minutes, producing heavy performance degradation. 3 consecutive violations violations (threshold violations required before scale-out; cluster scaling experiment; reactive threshold-based scaling). 6 minutes minutes (additional delay before new instance could serve requests; experiment; new VM in experiment; OpenStack experiment). about 8 minutes minutes (overload duration before new VM served requests; experiment; cluster in experiment; OpenStack experiment). [57]

Threshold-based autoscaling uses observed performance metrics such as CPU utilization or memory consumption; scaling starts when a defined threshold is passed. The policy is reactive and rule-based, responding to current or historical system metrics. [105]

threshold-based autoscaling: Threshold-based auto-scaling is relevant as a reactive scaling policy: it is simple, but it is prone to flapping. [133]

Threshold-based autoscaling uses customer arrivals and departures, system requests, active-server levels, activation thresholds F or Fk, and deactivation thresholds R or Rk as its principal inputs. [134]

threshold-based autoscaling: In the page's operational scope, auto-scaling adjusts cloud resources in response to observed or predicted system conditions; conventional scaling is reactive when metrics breach thresholds, while predictive auto-scaling triggers actions from forecasts of target metrics. [135]

threshold-based autoscaling: The page reports that ScaleX generally performs better than the industrial approaches, while rule-based and step-based approaches are among the industrial baselines; the reported comparison uses SLA violations and allocated cores as criteria. [136]

threshold-based autoscaling: Kubernetes HPA is presented as a comparable implementation of a static threshold-based scaling policy, while Smart HPA is described as a hierarchical extension with Microservice Managers, a Microservice Capacity Analyzer, and an Adaptive Resource Manager. The page therefore supports treating HPA as an implementation mechanism or policy example rather than, by itself, a separate algorithm family. [104]

Threshold-based autoscaling belongs in the Reactive category because scaling operations are triggered only after observed performance metrics exceed predefined thresholds. [98]

| Entity | Method name | Method category | Trigger or input signal | Core working principle | Advantages | Limitations | Method evidence scope | Evidence quality |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| threshold-based autoscaling | Threshold-based autoscaling[83] | Reactive[104] | CPU, memory, network, response time, request rate, queue length; preset thresholds[96] | Monitors metrics over a time window, compares them with preset thresholds, and triggers scale-out/in after violations[124] | Simple, widely used, and effective under stable demand or loose SLAs[83][107] | Manual threshold tuning; delayed burst response; over/under-provisioning, oscillation, and QoS/SLA violations[135][105] | Established and widely used across cloud platforms; cutoff-specific evidence indirect[90][83] | Published primary study plus review evidence — A Queueing Model for Threshold-Based Scaling of UPF Instances in 5G Core, IEEE Access (2021)[37][83] |

One selected study proposes an innovative algorithm for dynamic management and optimization of 5G network resources in a Kubernetes cluster: it monitors User Plane Function (UPF) metrics and makes real-time deployment decisions; exceeding LimitA (67% CPU consumption) deploys one new UPF, while exceeding LimitB (87% CPU consumption) deploys two. [121]

Threshold-based autoscaling: auto-scaling adjusts cloud resources in response to observed or predicted system conditions; conventional scaling is reactive when metrics breach thresholds, while predictive auto-scaling triggers actions from forecasts of one or more target metrics. [135]  
Its evidence includes an authoritative published 2021 IEEE Access study on scaling UPF instances. [37]

Threshold-based autoscaling: data assets’ 10% spike in transaction volume—Friday normal, Tuesday-morning red flag. [128] 5G Kubernetes simulation: intermittent sync delay; traffic growth, insufficient scaling; graceful pod termination, unavailable resources; physical unavailability, no scale-out. [132]

Reactive autoscaling is distinguished by changing behavior when a change occurs in the execution context, whereas proactive autoscaling anticipates changes using historical knowledge and observed trends; proactive approaches are typically also reactive, while reactive approaches may not also be proactive when changes or uncertainties cannot be predicted. [125]

Threshold-based auto-scaling's 2013 configuration specified a QoS classification threshold of 95% of target scale-out value for a tier. [124] The HPA baseline used CPU usage thresholds as input triggers and scaled when CPU usage exceeded the specified threshold in the Sock Shop benchmark on 02 Feb 2024. [126]

Under the evaluated workload—a 48hr -body MPI job on a CPU cluster during the study evaluation—threshold-based suspend-resume saved 45% carbon compared to the carbon-agnostic policy by exploiting temporal flexibility, but increased job completion time by 4×. [137]

Threshold-based autoscaling for 5G microservice pods intermittently averages pod CPU-usage measurements (15 seconds by default), compares the average with upper and lower thresholds, and changes the desired number of replicas when the average is outside those bounds; values inside the threshold do not trigger autoscaling. [132]

**Placement and decision rule**

**Signals and operating variants**

**Advantages**

Reactive Methods serve the overarching cloud-autoscaling research purpose by modeling self-adaptive systems that change behavior when their execution context changes; they use real-time host data, commonly apply rule- or policy-based decisions, and select an adaptation option to meet adaptation goals [125]. MAPE-K provides the control-loop framework for organizing this analysis and comparing reactive artifacts in published studies [125].

In the requested Reactive/Proactive classification, Reactive Methods are the post-change branch: they change behavior when the execution context or current system changes, whereas Proactive Methods use historical knowledge and observed trends to anticipate future changes [125][115]. This distinction makes Reactive Methods the relevant category for changes or uncertainties that cannot be predicted, although they do not themselves anticipate those events [125].

Reactive Methods offer a practical strength for method analysis: they use current or real-time measurements and rule- or policy-based decisions to scale in or out, and they are described as a popular cloud-autoscaling type [125][114]. Their material weakness is delayed response: because scaling takes time, an SLA violation may already be underway; in request-driven big-data scheduling, waiting or pre-emption can cause performance degradation, while adaptive-threshold reinforcement learning remains reactive with similar weaknesses [114][86][122].

Threshold-based autoscaling is a reactive, rule-based baseline: it compares an aggregate monitored metric with a configured threshold over a time window and triggers scale-in or scale-out within instance limits [124]. Its advantage is automatic resource increase under high demand and release of underutilized resources when demand falls [120], while its status as a traditional baseline for predictive comparisons—and a 2025-01-20 Kubernetes HPA study applying the mechanism to cloud-native application instances—makes it useful for current research; under rapidly increasing demand, latency can cause under-provisioning, degraded user experience and possible SLA violations, whereas falling demand can leave costly over-provisioning [97][37][98].

Feedback-control-based autoscaling links demand and response-time SLO feedback to dynamic adjustment of Kubernetes service replicas in containerized applications, making it a reactive contribution to cloud auto-scaling research [123]. The prototype reports improved scaling accuracy and a better performance–resource-utilization trade-off over standard Kubernetes HPA and another autoscaling methodology [123].

For feedback-control (control-theoretic) auto-scaling, the survey states that queuing models are widely applied for QoS modeling in the cloud; they model cloud-based services as a single queue or a collection of interacting queues and correlate response time or throughput with CPU, number of VMs, and workload [112].

### Proactive Methods

**Proactive methods prepare capacity before demand.** They differ in the source of their advance information: a known schedule, an extrapolated time series, a learned workload model, or an anticipatory decision policy. Reinforcement learning—RL—belongs here only when the particular controller acts in anticipation; learning from rewards alone does not automatically make a policy proactive. Hybrid control is included as the bridge between the two requested categories.

| Method | Category | Core working principle | Main advantages | Main limitations |
|---|---|---|---|---|
| Scheduled scaling | Proactive | Change capacity before known demand periods | Simple; predictable advance preparation | Fixed schedules miss unexpected changes |
| Statistical and model-based prediction | Proactive | Forecast load and translate it into capacity | Startup-aware; often lightweight | Pattern and model dependence |
| Predictive machine learning | Proactive | Learn future demand from multiple signals | Nonlinear and context-sensitive prediction | Data, training, drift, integration costs |
| Anticipatory RL: RLPAS | Proactive implementation | Learn actions from cumulative resource-performance reward | Adaptive sequential decisions | Exploration risk and convergence time |
| Reactive–proactive hybrid | Both | Combine advance planning with live correction | Anticipation plus contingency response | Coordination and conflicting decisions |

**Scheduled scaling uses known future events.** The controller changes capacity according to a calendar or workload timetable. Examples include preparing resources before a daily business opening or a known recurring processing period. The scale action can be scheduled early enough to accommodate normal initialization, without requiring a statistical model to infer when the event will occur. Azure explicitly recommends schedules for predictable demand. [4]

**Its advantage is low modeling overhead.** A schedule is easy to explain and audit, and it can capture business knowledge that historical telemetry has not yet recorded. It is particularly useful when operators know both the timing and approximate scale of recurring demand. Compared with a continuously trained predictor, the main operational work is maintaining the schedule and matching it to the application’s actual readiness delay.

**Its limitation is fixed anticipation.** A calendar action does not automatically adapt when demand starts earlier, grows more than expected, disappears, or occurs outside the planned period. The 2024 IEEE Access study defines schedule-based scaling in terms of daily workload patterns and explicitly identifies unexpected changes as its weakness. A schedule can therefore prepare a baseline, but live rules remain important when actual demand differs from the timetable. [8]

**Scheduled control is a strong baseline.** A complex predictor must offer something beyond what an accurate calendar already supplies. If business events dominate demand and change infrequently, schedules may provide most of the practical value at lower operating cost. If timing or magnitude changes continuously, statistical or learned prediction becomes more attractive. The decisive issue is whether additional modeling improves the capacity decision, not whether its algorithm is more elaborate.

**Statistical forecasting learns temporal structure.** Time-series methods use ordered historical observations to extrapolate trends, recurring patterns, or transitions among demand states. An autoregressive moving average, or ARMA, model combines information from earlier observations and forecast errors. Other approaches identify periodic behavior or use state-transition probabilities when a stable repeating pattern is absent. The forecast then becomes an input to a capacity-planning decision. [6]

**A forecast still needs a capacity model.** Predicting requests per second does not directly specify how many VMs are required. The controller must relate predicted work to service capacity, existing backlog, and the desired performance margin. Model-based approaches may use queueing networks or performance models for that translation. A Kalman filter can update model parameters that are difficult to observe directly, helping a model follow changes in the application or infrastructure. [6]

**Look-ahead control includes future consequences.** Receding-horizon control repeatedly predicts demand over a future interval, evaluates candidate resource plans, executes an immediate decision, and updates the calculation when new observations arrive. The related-work analysis in the 2026 load-aware study describes an approach using a second-order ARMA forecast and performance analysis to minimize allocation cost. Its benefit is that resource choices are evaluated across time rather than as isolated present-state changes. [6]

**AWS provides an operational example.** EC2 Predictive Scaling analyzes historical load for daily or weekly traffic patterns and forecasts future capacity requirements. AWS identifies cyclical traffic, recurring on-and-off workloads, and applications with long initialization as suitable cases. The practical advantage is not that a VM starts faster, but that its startup can begin before the capacity is needed. [5]

**A lightweight study illustrates horizon alignment.** Zanussi and colleagues’ 2026 *Load-aware predictive auto-scaling framework for cloud environments* uses rolling historical measurements to forecast arrivals and determine resource requirements. In its simulation settings, measurements arrive every 15 seconds, the history covers 300 seconds, and the forecast horizon is 60 seconds—the same as the modeled VM boot time. The selected predictor is a second-degree polynomial regression rather than a deep neural network. [6]

**Backlog changes the required resource count.** The same framework considers unfinished requests as well as predicted new arrivals. This matters because a system that has already fallen behind needs enough capacity to process both. It also accounts for previously scheduled additions so that successive control decisions do not repeatedly request capacity that is already on its way. Scale-in is more conservative: persistent excess capacity must be predicted, ongoing expansion is considered, and active requests are allowed to complete before deallocation. [6]

**The reported gains favor purposeful modeling.** In simulation using a flight-seat-availability workload, the framework’s total VM leasing time was 2,627 VM-hours, reported as 12% below the compared Average Load reactive policy. Mean response time was approximately an order of magnitude shorter. Its decision computation averaged about 3 milliseconds per invocation on the study’s workstation. These findings show that matching prediction, backlog, and startup delay can be effective without a computationally large predictor. [6]

**Model error remains the principal constraint.** Historical periodicity can break, service capacity can change, and an inaccurate relationship between workload and resources can invalidate an otherwise accurate arrival forecast. Model-based prediction is attractive when its assumptions remain useful over the activation horizon. Its value decreases when behavior changes faster than the model adapts or when activation delay is so short that current-state feedback already meets the service objective.

**Predictive machine learning learns richer relationships.** These systems train models to forecast future workload or resource demand from historical and current observations. Inputs may include CPU, memory, network activity, request counts, and workload context. Depending on the design, the output can be future requests, future resource utilization, or an aggregate demand indicator that a separate controller converts into scaling actions. [11]

**Its advantage is nonlinear and contextual modeling.** A learned predictor can represent interactions that a single-metric rule ignores and can distinguish workload regimes that require different forecasting behavior. Hanieh Alipour’s 2019 thesis, *Model-Driven Machine Learning for Predictive Cloud Auto-scaling*, demonstrates a continuous training-and-inference architecture on AWS and Azure. Forecast output is integrated with provisioning and cluster configuration rather than left as a stand-alone prediction. [11]

**Context-aware selection avoids one fixed predictor.** Cañete and colleagues integrate a framework that identifies increasing, decreasing, or fluctuating workload contexts and selects among linear regression, support-vector regression, and neural networks. The underlying context-aware predictor is reported to fit workloads at least 10% better than comparison approaches. Its important design contribution is changing the predictor with the workload regime, rather than assuming one model is best under all conditions. [12]

**Multi-resource forecasting addresses different bottlenecks.** A 2024 IEEE Access study forecasts future CPU, memory, and bandwidth requirements for virtual network functions using a combined multilayer-perceptron and long short-term memory model. Long short-term memory, or LSTM, is a recurrent neural-network design for learning temporal dependencies. The system also uses anomaly identification and online autoregressive correction, illustrating how a predictive component can coexist with corrective mechanisms. [8]

**Integration can outweigh model construction.** Alipour separates monitoring, training, validation, model selection, prediction, and deployment responsibilities into cooperating services. The thesis reports lower workload-instance costs than general threshold-based scaling, while also identifying separate costs for running the inference infrastructure. It further emphasizes the configuration work needed for a new instance to join a data-management cluster. Thus, better forecasts must offset the cost and complexity of the complete predictive system. [11]

**Data and maintenance are substantial limitations.** Machine-learning approaches require suitable training observations, feature choices, model tuning, and updates when workloads change. Deep learning can impose significant data and computation requirements. A 2024 Cluster Computing study emphasizes both the nonlinear modeling benefits and these operational burdens, particularly when prediction expands from one resource to several interdependent resources. [13]

**Predictive learning should justify its complexity.** It is most compelling when multiple signals materially improve advance capacity decisions, simpler forecasts fail on relevant patterns, and the team can maintain the model lifecycle. It is less attractive when the workload is small, the schedule is already reliable, or the cost of monitoring and inference approaches the resource savings. Forecasting accuracy should be assessed together with service performance and total operating cost.

**Reinforcement learning learns a decision policy.** An RL agent observes the system, chooses a scaling action, receives a reward, and updates its behavior to improve cumulative reward. The reward can favor meeting performance targets while penalizing unnecessary resources or service violations. Unlike supervised forecasting, the principal learned object is the policy connecting states to actions, although some systems also incorporate workload prediction. [14]

**RLPAS is an anticipatory implementation.** Bibal Benifa and Dejey’s *RLPAS: Reinforcement Learning-based Proactive Auto-Scaler for Resource Provisioning in Cloud Environment*, published in *Mobile Networks and Applications* in 2019, uses SARSA—state–action–reward–state–action—learning. Its parallel-learning design shares learning information to improve resource-allocation decisions. The authors report validation with real workloads and improvements in CPU utilization, response time, and throughput over the compared approaches. [15]

**Its state and actions are concrete.** Lemke and Majumdar describe four RLPAS state variables: request count, allocated-VM percentage, response time, and throughput. Its three action types are increasing capacity, decreasing capacity, and making no change. An action can specify both VM count and VM type, giving the reviewed design horizontal and vertical scaling choices. [10]

**The benefit is sequential adaptation.** Resource decisions have effects that persist across control intervals: adding capacity has a cost now but can prevent later congestion, while removing capacity can save resources but create subsequent recovery work. RL can learn these consequences without requiring operators to write every rule explicitly. RLPAS is classified here because its design is intended to anticipate workload developments; a policy that only corrects a present violation would remain reactive.

**Exploration creates an operational risk.** Early in learning, an agent may choose poorly because it has not yet learned the consequences of its actions. Larger state and action spaces can also require longer convergence. The 2022 MLScale–RLPAS comparison reports acceptable RLPAS convergence only up to 16 VMs per application in the reviewed experiments. That is a boundary of those experiments, not a general architectural ceiling on every RL autoscaler. [10]

**Reward design does not remove service constraints.** A penalty for an SLA violation makes that event undesirable, but does not make it impossible during exploration or after an environmental change. A production design should therefore constrain unsafe actions and retain a dependable fallback while learning proceeds. Parallel learning and function approximation address computation and convergence, but they do not substitute for application-safe execution.

**Scaling and scheduling remain distinct problems.** A 2020 RL survey found that none of its surveyed works jointly solved both resource scaling and task scheduling. This is important when transferring a learned policy to data-intensive systems: selecting a resource count is different from deciding where work and data should run. RL is strongest when sequential adaptation offers clear value and safe learning is feasible; it is harder to justify when a simple, already stable controller meets the objective. [14]

**Hybrid control combines anticipation with correction.** A proactive component plans capacity for expected demand, while a reactive component responds to deviations. A 2017 Journal of Cloud Computing study describes separating proactive decisions over longer periods, such as hours or days, from shorter-timescale reactive decisions. The practical benefit is to prepare for recurring demand without making service protection depend entirely on the forecast. [1]

**Different directions can use different mechanisms.** Hybrid does not necessarily mean that two controllers perform identical duties. Azure’s guidance describes predictive scale-out complemented by metric-based rules for unexpected demand and scale-in. Other designs use reactive expansion and predictive contraction, checking whether apparent excess capacity is likely to persist before removing it. Both are hybrids because observed and anticipated conditions participate in the overall decision process. [4][6]

**Coordination is its principal limitation.** Independent controllers can disagree: one may request removal while another is already adding capacity. A sound implementation needs a consistent view of ready resources, pending actions, minimum capacity, and application-safe removal. As an architectural recommendation, one decision-reconciliation mechanism should own the final capacity target rather than allowing competing components to issue unrelated commands.

**Hybrid advantages are workload-dependent.** Verma’s 2025 technical analysis of microservices autoscaling favors hybrid designs for balancing prediction with adaptation in enterprise deployments. The underlying mechanism is persuasive where demand has both a learnable baseline and meaningful surprises. The additional coordination is less valuable when a workload is entirely schedule-driven or a fast reactive controller already satisfies its performance requirements. [16]

**Conditional selection is the resulting judgment.** Prefer reactive control when future demand is difficult to infer and activation is fast enough relative to the service’s tolerance. Prefer proactive control when there is trustworthy advance information and startup delay is consequential. Prefer a hybrid when both conditions occur together. The strongest design is the least complicated one that can meet the objective while accounting for readiness delays, forecast errors, and application state.

**Additional documented evidence**

Auto-Scaling technology in cloud computing: The page presents auto-scaling as dynamically scaling an enterprise application across multiple clouds without user intervention, and reports that the approach applies to web/services-based enterprise workflows or applications on the cloud. [29]

Auto-Scaling technology in cloud computing: The page describes the subject as dynamic deployment and auto-scaling of enterprise applications on the cloud, joining multi-cloud deployment with optimization-based resource provisioning and deployment configuration. [29]

cloud computing: The page describes cloud elasticity as an intrinsic cloud feature and discusses auto-scaling as the dynamic scaling of cloud-hosted enterprise applications; it does not provide a formal definition distinguishing the two concepts. [29]

Auto-Scaling technology in cloud computing: The page covers enterprise applications and web/services-based enterprise workflows on public clouds, including applications with a single scalable component and workflows using parallel and exclusive control structures. It concerns multi-cloud deployment, resource provisioning, deployment configuration, and scaling across multiple clouds, evaluated on Amazon cloud infrastructure. [29]

The page places the subject in public-cloud computing, where service-oriented architecture and resource virtualization support scalability for enterprise applications with highly dynamic load. [29]

Reactive autoscaling scales a group based on observed changes in load in real time. Predictive autoscaling differs by using historical data to forecast future load while also incorporating real-time data for current load. [30]

Auto-Scaling technology in cloud computing: The supported scope includes computational resources in cloud environments and cloud-hosted applications. The page also identifies serverless and container-based architectures, microservice-level scaling, and multi-cloud and hybrid-cloud environments as relevant auto-scaling settings. [31]

Auto-Scaling technology in cloud computing: The source covers distributed cloud and edge applications, software components deployed as containers or VMs, compute, storage and network resources, application and infrastructure graphs, geo-distributed resource environments, and horizontal and vertical adaptation across edge/fog/cloud infrastructure. [33]

cloud computing: The source places the relevant scope in cloud and grid computing with distributed graph processing on configurable virtual machines; it does not define cloud auto-scaling itself. [35]

Auto-Scaling technology in cloud computing: The source describes cloud auto-scaling as automatically allocating computational resources based on system demand and recommends automated and dynamic scaling to optimize resource usage. [36]

The source describes auto-scaling as using a resource scaling algorithm to scale the number of application instances up or down depending on variations in offered customer traffic. [37]

The page identifies an energy-efficiency-related published study, “Energy aware consolidation for cloud computing,” by S Srikantaiah, published in the Proc of HotPower in 2008. The page provides the study title, author attribution, venue and year, but does not state the study’s specific autoscaling manifestation, proposed solution, evaluation evidence, or publication day. [38]

Auto-Scaling technology in cloud computing: For this report, cloud auto-scaling can be bounded as an automatic-scaling capability of cloud applications operating within a cloud model that provides on-demand access to shared configurable resources and rapidly provisions and releases those resources. [38]

The source presents cloud computing as a paradigm whose boundaries and definition require clarification. It describes Clouds as a pool of virtualized computer resources that support dynamic scale-in and scale-out through provisioning and de-provisioning, and monitoring for dynamic load-balancing and reallocations. This provides a clear operational basis for explaining cloud auto-scaling, its advantages, and its limitations. [39]

Cloud elasticity allows resources to match changing workload: without elasticity, peak provisioning wastes resources during nonpeak periods, while underprovisioning sacrifices revenue and can cause permanent customer loss. [40]

cloud computing: Public cloud advantages include the appearance of infinite computing resources on demand, elimination of up-front commitment, short-term pay-per-use computing, economies of scale, higher utilization through workload multiplexing, and simplified operation through resource virtualization. [40]

Auto-Scaling technology in cloud computing: Auto-scaling automatically adjusts resources in response to system demand; in the described system, GCE Autoscaler is used for some stateless components to improve resource utilization. [41]

The page presents cloud-computing modeling research as a systematic effort to classify and summarize research directions, providing a basis for further research relevant to Auto-Scaling technology in cloud computing. 71 articles articles (selected primary studies; between 2008 and January 2017; articles published between 2008 and January 2017 in journals and conferences; A systematic mapping study combined with a systematic literature review). [43]

Cloud computing is the application context in which resources are shared and provided, and its complexity motivates modeling research and further research directions. [43]

The source includes vertical scaling as an autoscaling implementation context: it considers “vertical scaling with each service hosted on its own dedicated replica” and adjusts cores and memory to achieve response-time targets. 10 second intervals (PSI sampling interval; service containers; PSI measurement). [44]

Auto-Scaling technology in cloud computing: Cloud scalability dynamically modifies resources in response to shifting demand, while auto-scaling performs this resource addition or removal automatically according to real-time usage. The page also contrasts this with manual scaling, which splits workloads among several resources. [47]

The supported scope includes Kubernetes orchestration for containerized applications and services, with scaling behavior evaluated through application metrics, replica counts, failed requests, response time, and cluster configuration. 2 worker nodes (cluster size; one HPA comparison cluster; HPA using Prometheus Custom Metrics). 4 worker nodes (cluster size; the comparison HPA cluster; HPA using Prometheus Custom Metrics). [50]

Auto-Scaling technology in cloud computing: In this study, elasticity is operationalized through on-demand scale-out and scale-in operations that change the set of servers running a distributed graph computation. [54]

In the cited cloud auto-scaling system, horizontal scaling is applied to large-scale graph processing with heterogeneous cloud resources; the system automatically adjusts the number and types of virtual machines according to computation requirements for convergent graph applications. [61]

Auto-Scaling technology in cloud computing: Auto-scaling is an automatic mechanism for adjusting cloud resources in response to demand, application conditions, or workload variation. It includes automatically adjusting the number of resources and providing an automatic solution for resource allocation. [62]

Predictive, or proactive, techniques determine future resource requirements and provide resources in advance. [62]

Auto-Scaling technology in cloud computing: Cloud auto-scaling is a resource auto-scaling approach that automatically adjusts cloud resources in response to system and workload conditions; in this study, it scales CPU-core resources by changing the number and frequency of cores. [63]

Kubernetes Horizontal Pod Autoscaler is a concrete autoscaling strategy that creates additional software instances when workload increases and scales down when workload decreases. [65]

Auto-Scaling technology in cloud computing: The study presents proactive auto-scaling as a machine-learning application: classifier and regressor MLP models predict UPF requirements, and the predicted scaling decisions are used as input to evaluate SFC placement. The Q-regressor/C-regressor (1hr) models achieved 96.2% accuracy in one comparison, while the Q-classifier/C-classifier (1hr) models achieved 98.43% accuracy or an R 2-score of 0.984 in another reported comparison. 6912 samples (training samples; model training data; MLP models). 2304 samples (validation samples; model validation data; MLP models). 2304 samples (testing samples; model testing data; MLP models). 0.194 (MAE; Q-regressor/C-regressor (1hr)). 0.0696 (MSE; Q-regressor/C-regressor (1hr)). 0.194 (RMSE; Q-regressor/C-regressor (1hr)). 98.43% accuracy (R 2-score/accuracy; Q-classifier/C-classifier (1hr)). 96.2% accuracy (accuracy; test dataset; Q-regressor/C-regressor (1hr) models). 1hr hour (scaling-decision interval). [68]

Reactive methods are policies that respond to observed conditions or real-time workloads; the source contrasts threshold-based reactive policies with AI-based proactive policies. [48]

HPA is a reactive scaler that makes scaling decisions based on static threshold values. [72]

Workload forecasting is part of a complete elastic system, where forecasting algorithms inform elastic provisioning and can reduce under-provisioning and over-provisioning costs. [51]

A cited primary research source relevant to reinforcement learning in cloud computing is “An end-to-end automatic cloud database tuning system using deep reinforcement learning,” by Ji Zhang and coauthors, published in 2019 in the Proceedings of the 2019 International Conference on Management of Data. [74]

Horizontal scaling can keep the existing pool of computing resources online while adding more resources, and the page states that when an app is scaled horizontally, it has the benefit of elasticity. [75]

Auto-Scaling technology in cloud computing: The page covers workloads hosted in cloud environments and auto-scaling across IaaS, managed Kubernetes, serverless CaaS, and serverless FaaS. Examples include AWS EC2, Azure Virtual Machine Scale Sets, GCP managed instance groups, EKS, AKS, GKE, ECS with AWS Fargate, Azure Container Apps, AWS Lambda, and some Azure Functions plans. The relevant resources include infrastructure capacity, Kubernetes pods or nodes, container workloads, and function capacity. [32]

energy efficiency: The study proposes TT-Autoscaling, which operates inside containers by tuning runtime thread counts and at the cloud-infrastructure level by transferring released resources to other containers. Compared with default container execution, it reports 55.8% performance improvements, 53.6% energy reductions, and 79.5% EDP improvements, and it outperforms strategies using vertical autoscalers proposed by orchestrator tools. 55.8% % (performance improvements; container-based parallel applications; comparison with default execution of containers). [66]

Auto-Scaling technology in cloud computing: The source covers distributed graph processing engines, large graphs, clusters of servers, graph computation, and on-demand scale-out/in operations, implemented in the LFGraph distributed graph processing system. [77]

Auto-Scaling technology in cloud computing: The report’s current-mainstream cutoff is 2026-10-17, while this study was published in 2026 and added to IEEE Xplore on 29 July 2026. 29 July 2026 (Date added to IEEE Xplore; IEEE Xplore metadata). 2026-10-17 (Current-mainstream cutoff; planning cutoff supplied in task). [80]

Auto-Scaling technology in cloud computing: The page lists workload-prediction-related studies including "Efficient autoscaling in the cloud using predictive models for workload forecasting" by Nilabja Roy, Abhishek Dubey, and Aniruddha Gokhale, published in the Proceedings of the 2011 IEEE International Conference on Cloud Computing (CLOUD), pages 500–507; it also lists "A cost-aware auto-scaling approach using the workload prediction in service clouds" by Jingqi Yang and coauthors, published in Information Systems Frontiers 16, 1 (2014), 7–18. 2011 (publication year). 500–507 pages (page range). 16, 1 (2014) (volume, issue, publication year). [49]

Auto-Scaling technology in cloud computing: The supplied planning cutoff is 2026-10-17; this source itself was published on 2022-12-01. 2026-10-17 (current-mainstream evidence cutoff). 2022-12-01 (source publication date). [84]

| Entity | Method name | Method category | Trigger or input signal | Core working principle | Advantages | Limitations | Method evidence scope |
| --- | --- | --- | --- | --- | --- | --- | --- |
| threshold-based autoscaling | Threshold-based autoscaling[34] | Reactive[104] | CPU, memory, network, latency, request rate, queue length; predefined thresholds[96] | Feedback loop compares current metrics with preset thresholds and triggers scale-out/in when crossed[57] | Simple, widely deployed; effective for stable demand or loose SLAs; low training/runtime overhead[107] | Delayed response to bursts; difficult threshold tuning; over-/under-provisioning and thrashing[105][83] | Established and widely used; evidence spans cloud platforms and studies through 2024[90][91][92] |
| machine-learning-based autoscaling | Machine-learning-based autoscaling [97] | Reactive or Proactive, depending on the control loop [79] | Historical workload/resource time series, container-performance data, and Kubernetes/application/custom-monitoring metrics [86][113][97] | Learn workload/resource patterns; forecast multidimensional demand; map predictions to CPU, memory, and network needs; combine forecasts with real-time monitoring to actuate scaling [97] | Proactive adaptation; improved resource utilization and QoS/SLA compliance; lower latency, cost, and energy use  | Data/training burden; accuracy degradation during sudden spikes and long horizons; black-box decisions; limited cross-environment and multi-cloud generalization [97][113] | Active evidence: 2026 survey of 60 primary studies (2015–2025) plus the 2024 study Enhancing Machine Learning-Based Autoscaling for Cloud Resource Orchestration; mainstream status by 2026-10-17 not established [60] |
| feedback-control-based autoscaling | Feedback-control-based autoscaling[112] | Reactive; Hybrid/Proactive variant also reported[110][103] | Response time, throughput, CPU utilization, memory, request rate[109][83] | Measure output; compare with reference; compute control input; adjust resource allocation or VM count[109] | Stable control; rapid settling; SLA support; balanced resource allocation; cost efficiency[109][106] | Slow response; oscillation or instability; poor performance under sudden changes; noisy or delayed metrics; computational overhead[109][111] | 2016 A discrete-time feedback controller for containerized cloud applications; 2025 Deep Learning and Feedback Control Based Container Auto-Scaling for Cloud Native Micro-Services; mainstream status by 2026-10-17 unestablished[100][101] |

Workload prediction manifests as forecasting computational requirements and demand patterns so that resources can be allocated or scaled before anticipated demand occurs. [56]

Auto-Scaling technology in cloud computing: autoscaling policies dynamically provision resources for customers; datacenter operators simplify application and resource management. [117] With 10-fold cross validation, TAS achieved around 99% correlation in both the private cluster and EC2; its average absolute error was 500 micro-seconds for EC2 and around 60 micro-seconds for the private cluster. [53]

Auto-Scaling technology in cloud computing is scoped to cloud computing across the computing continuum from data centers to edge to IoT sensors and devices, with cloud auto-scaling adapting allocated resources to workload requirements. [118] In 2022, a published example connects it to the challenge-and-solution purpose through “An autoscaling platform supporting graph data modelling big data analytics.” [85]

Auto-Scaling covers distributed graph processing engines, large graphs, clusters of servers, graph computation, and on-demand scale-out/in operations, implemented in the LFGraph distributed graph processing system. [77]

In cloud computing, the source covers distributed graph processing engines, large graphs, clusters of servers, graph computation, and on-demand scale-out/in operations, implemented in the LFGraph distributed graph processing system. [77] The published CCGrid study on cost-effective execution for distributed graph processing on configurable VMs was published on 2017-05-01. [35]

Cloud auto-scaling is presented as automatic adjustment and allocation of cloud resources in response to workload or system demand, with the goal of meeting Quality of Service requirements and avoiding over-utilization and underutilization. [71]

Cloud computing/telecom: Big Data Analytics; LambdaTel—proposed solution for batch and streaming data processing; lack of standardized architecture; response: structured/security-focused approach; recommend: Python, Dockerized implementation, local Telco app, cross-selling/up-selling. [119]

Cloud computing: The page links auto-scaling with elasticity through the cited work titled “A review of auto-scaling techniques for elastic applications in cloud environments.” [43]

Cloud computing lists 2022, 2023 publications: an autoscaling platform supporting graph data modelling and big data analytics, and a self-adjustable big data management platform exploiting the Hadoop ecosystem. [85] Its provisioning uses analytical application models to predict average response time or throughput, automate provisioning decisions, minimize costs, and correct runtime SLA deviations. [116]

HPA: metric-driven horizontal scaling adjusts pod replicas from observed metrics; reactive timing can cause resource inefficiency/performance degradation, under-provisioning during rapid demand increases, and over-provisioning when demand decreases [98]. A Jul 2025 published study is “Towards resource-efficient reactive and proactive auto-scaling for microservice architectures” [81].

**Working definition and boundary**

**Elasticity and the two-category taxonomy**

Cloud computing supplies elasticity—the ability to rapidly expand or reduce leased resources as load varies—whereas Auto-Scaling technology is the mechanism that changes those resources from autonomic or demand input; thus auto-scaling operationalizes and enables elasticity [58][64].

Reactive Methods and Proactive Methods should remain the two top-level categories, while hybrid reactive-proactive autoscaling is a cross-cutting combination rather than a third category: its reactive part handles current workload and its proactive part forecasts future needs; in HAS, the reactive decision replaces the proactive one when observed CPU utilization exceeds the predefined 0.9 ∗ bound [78][87][108]. The hybrid evidence is tested but does not establish mainstream status as of 2026-10-17, so the roster should tag it across the two categories rather than present an independent mainstream family [108].

Horizontal scaling adds or removes instances, whereas vertical scaling resizes the resources of an existing instance; both are resource-action dimensions, while Reactive and Proactive describe decision policy and timing [90][88]. Horizontal scaling can keep the current resource pool online, while vertical replacement may take the machine offline during an upgrade, so the action dimension should be reported separately from the strategy family [75].

Kubernetes Horizontal Pod Autoscaler (HPA) is a concrete implementation example for horizontal autoscaling: it periodically uses observed CPU, memory, custom, or external metrics to adjust pod replicas, and static thresholds make this example reactive [89][93][72]. It should therefore be listed as an implementation example under the horizontal/Reactive combination, not as a separate algorithm-family row [89].

Kubernetes Vertical Pod Autoscaler (VPA) is a concrete implementation example for vertical pod scaling: a recommender uses monitored usage to adjust CPU and memory requests and limits for existing pods [95][94]. VPA is not itself a Reactive or Proactive algorithm-family row, and its possible pod restarts introduce disruption risk, so it should be classified by its vertical action while its decision logic is analyzed separately [82][94].

Auto-Scaling technology in cloud computing is the report’s central object because it automatically provisions, de-provisions, or adjusts resources in response to demand, providing the common subject for the method taxonomy and application analysis [59][70]. It connects those purposes to resource, cost, and energy challenges, dynamic telecom/NFV services, graph scaling, and workload prediction [69][67][55][73].

rejected: citation_outside_operands; allowed_numbers=["","71 articles","2021-05-01","2019-08-14","13 November 2021","2019","2022"]; allowed_cites=[1,5,7,11,18,21,24,30,33,36,44,46,49,51,53,54,65,67,71,74,75,83,88,89,90,95,97,98,100,107,109,110,111,120,125,133,134,143,145,146,147,148,149,154,158,161,176,184,188,191,229,239,327,328,374,433,435,436,440,512,518,519,522,523,557]; allowed_entities=["Auto-Scaling technology in cloud computing","cloud computing","energy efficiency","horizontal scaling","Auto-Scaling"]

Auto-Scaling technology should be evaluated for each method through three linked elements: its principle, meaning automatic adjustment from observed or predicted demand; its advantage, such as elasticity, performance, or cost alignment; and its limitation, including scaling overhead, trigger sensitivity, over- or under-provisioning, and SLA or cost risk [45][52][76][48][67][115]. This supports the report’s purpose of a substantive method-by-method principle–advantage–limitation treatment rather than a name-only roster [114].

Cloud computing is the deployment context rather than an autoscaling method: it provides on-demand shared resources, elastic provisioning, and pay-as-you-go use, which make automatic resource adjustment useful [38][76]. Its rapid data growth, workload changes, and resource-management complexity motivate both the Reactive/Proactive taxonomy and the report’s challenge-and-solution analysis [69][102].

rejected: citation_outside_operands; allowed_numbers=["2017-05-01","","1,000 EC2 machines for one hour costs the same as using one machine for 1,000 hours machines and hours; 5% t","over 300 scientific projects","$3 trillion dollars","30–50% less energy per workload","2017","3000 online microservices","2022","41.98% percent","13 November 2021","2019","71 articles"]; allowed_cites=[1,5,11,13,17,18,19,20,21,22,24,30,41,44,46,47,53,54,71,74,75,80,85,86,88,95,97,103,107,108,109,110,113,125,133,134,145,146,147,148,149,188,192,197,201,205,213,230,250,253,254,255,258,259,262,263,265,266,268,269,270,306,307,313,349,382,407,415,416,418,420,436,437,439,464,465,469,484,500,519]; allowed_entities=["cloud computing","Auto-Scaling technology in cloud computing","energy efficiency","horizontal scaling","Auto-Scaling"]

Cloud auto-scaling—automatic or policy-driven adjustment of resources for a service as demand requires—includes horizontal scaling by adding or removing instances and vertical scaling by adding or removing resources from an existing instance [79].  
A systematic review selected 71 articles between 2008 and January 2017 as primary studies, providing a basis for Auto-Scaling research in cloud computing [43].

Auto-scaling is elastic adjustment of processing capacity for data stream processing operators, with MEAD using vertical resource allocation driven by workload-state information [42]. Cloud auto-scaling is automatic resizing or allocation of computational resources in response to system demand, implemented through monitoring and control loops that adjust elastic services as workload changes [57].

2020 survey: recurring research treatment; no documented deployment/official support for current-mainstream label [99]. Autoscaling matches performance requirements/demand: add resources as workload grows, remove them as demand slackens to minimize costs; scope—application/service/infrastructure monitoring/scaling—cloud-hosted environments [46].

**Additional documented evidence**

statistical or time-series forecasting autoscaling: Forecasting-based autoscaling belongs to Proactive because proactive strategies forecast future demand using predictive models. [144]

The page distinguishes Reactive methods by responding to real-time workload fluctuations and Proactive methods by forecasting future demand using predictive models. Hybrid methods are evidenced as a combination of reactive and proactive approaches rather than a separately established third top-level category. [144]

statistical or time-series forecasting autoscaling: Evidence on the page includes a chapter published in 2025 that discusses proactive autoscaling using predictive models and lists multiple forecasting studies from 2020 through 2023. The page does not establish a full current-mainstream criterion or deployment evidence through 2026-10-17. 08 December 2025. [144]

Workload-forecasting or time-series auto-scaling belongs to the Proactive category because it uses predictive models to anticipate demand and make scaling decisions before demand occurs. [145]

statistical or time-series forecasting autoscaling: The page describes predictive approaches as a response to the limitations of reactive autoscaling and states that a predictive autoscaling manager has a workload predictor that forecasts future job arrival time/rate. This supports classifying forecasting-based autoscaling as Proactive by decision timing. [146]

CloudInsight proposes a cloud workload-prediction framework that combines multiple workload predictors in a dynamically created ensemble. Predictor weights are determined in real time from their accuracy for the current workload using multi-class regression, and the ensemble is periodically recreated to handle dynamic workload fluctuations. [146]

Workload-forecasting auto-scaling uses historical workload data and recent workload similarity to predict future workload levels, then performs resource operations such as scaling in advance. FELT integrates historical and recent similarity into Transformer position encoding and attention masking, and predicts the workload levels of all containers at the next timestamp. next timestamp t (prediction horizon; all containers; FELT; Transformer with workload similarity perception). [147]

statistical or time-series forecasting autoscaling: Forecasting-based autoscaling consumes telemetry streams such as CPU utilisation and request rate, applies resampling, aggregation, feature extraction, and model inference, and feeds predictions to autoscaling controllers or dashboards. The pipeline returns point forecasts and confidence intervals, allowing forecasts to support proactive scaling and placement decisions. Classical models include ARIMA, SARIMA, exponential smoothing, and Prophet; deep models include LSTM, GRU, TCN, and Transformer architectures. [148]

The selected study is “Wasserstein Adversarial Transformer for Cloud Workload Prediction.” It presents WGAN-gp Transformer, a time-series forecasting model inspired by the Transformer network and improved Wasserstein-GANs; it uses a Transformer network as a generator and a multi-layer perceptron as a critic. Real-world workload-trace evaluations report 5× faster inference time with up to 5.1% higher prediction accuracy against the state-of-the-art. Applied to auto-scaling mechanisms on Google cloud platforms, the WGAN-gp Transformer-based mechanism significantly reduces VM over-provisioning and under-provisioning rates compared with the LSTM-based mechanism. 5× faster inference time (inference speed; real-world workload traces; extensive evaluations). 5.1% higher prediction accuracy (prediction accuracy improvement; real-world workload traces; comparison against the state-of-the-art). [149]

statistical or time-series forecasting autoscaling: Forecasting-based autoscaling is limited to CPU utilization as the scaling metric; Cloud Load Balancing and Cloud Monitoring metrics are unsupported. It requires at least 3 days of CPU-based autoscaling history, uses weekly and daily patterns, and does not predict monthly, annual, one-time, or sub-10-minute load patterns. Unexpected changes can still require real-time reactive handling, and predictive scaling may increase costs by starting VMs earlier and running them longer. 3 days days (required history; MIG CPU-based autoscaling; historical-data requirement). 10 minutes minutes (minimum predictable pattern duration; load patterns; supported-pattern boundary). [30]

statistical or time-series forecasting autoscaling: Workload-forecasting auto-scaling uses time-series forecasting to anticipate demand patterns and proactively allocate resources; the forecasts provide an RL agent with future context for scaling decisions. [130]

statistical or time-series forecasting autoscaling: The page describes predictive autoscaling as proactive: it uses machine learning algorithms and historical data to predict future demand and modify resources before anticipated spikes. [138]

statistical or time-series forecasting autoscaling: The source reports that the attention-enhanced forecasting model achieved the lowest MAPE among nine baselines with statistical significance at the 5% level or better on reconstructed Google- and Alibaba-like traces, and showed consistent gains on Alibaba Cluster Trace v2018 and Bitbrains VM workloads. The source bounds this conclusion to data-constrained cloud auto-scaling and does not establish universal superiority across all production traces or cloud environments. 5% level or better statistical significance level (significance threshold; nine-baseline comparison; controlled evaluation). 15 minutes minutes (forecast horizon; described proactive autoscaling system; workload forecasting). [142]

statistical or time-series forecasting autoscaling: Limitations and failure modes include dependence on historical data, larger forecasting errors at the beginning of online forecasting when historical data is lacking, difficulty adapting offline models to evolving features, cold-start constraints, and the practical difficulty of evaluating forecasting models in live online services because of system complexity and latency risk. at least 24 hours hours (historical data requirement; AWS ECS predictive auto-scaling; predictive auto-scaling). two weeks being ideal weeks (preferred historical data; AWS ECS predictive auto-scaling; predictive auto-scaling). 3, 7, 7 days days (historical data requirements; Google Cloud, Azura, and Alibaba Cloud respectively; predictive auto-scaling). [150]

statistical or time-series forecasting autoscaling: The source distinguishes proactive auto-scaling from reactive behavior by describing proactive scaling as using time-series forecasts to prepare resources in advance for peak load and reduce resources during low load. The control loop therefore uses predicted future demand rather than only a current observed threshold. [150]

statistical or time-series forecasting autoscaling: Statistical or time-series forecasting auto-scaling uses historical input sequences and forecasting models such as LR and ARIMA to predict near-future CPU usage or workload growth, then applies scaling actions before an anticipated peak. 5 min min (input sequence length; synthetic workload cluster; LR and ARIMA). 10 and 20 min min (input sequence lengths; synthetic workload cluster; ARIMA). [135]

The supplied passage does not report a specific limitation of machine-learning-based autoscaling; it only identifies published ML scaling work for Kubernetes edge clusters. [37]

| Entity | Method name | Method category | Trigger or input signal | Core working principle | Advantages | Limitations | Method evidence scope | Evidence quality |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| machine-learning-based autoscaling | Machine-learning-based autoscaling[97] | Reactive or Proactive; placement depends on control loop[79] | Reported signals: workload/resource patterns; CPU, memory, network, QoS, requests; predicted trends[139] | Forecast future multidimensional demand from workload data; map it to CPU, memory, and network needs; apply controller scaling actions[97][113] | Adaptive prediction; proactive scaling; fewer SLO violations; higher resource utilization; lower latency, cost, and energy use | Limited cross-workload generalization; black-box decisions; HPA/VPA/CA/KEDA conflicts; data/training burden; spike/long-horizon accuracy loss; AWS-specific validation[113][97] | Substantial active literature: 60 primary studies (2015–2025); current-mainstream status not conclusively established as of 2026-10-17 | Strong published evidence: 60-study survey; Zhang & Li (2025) AWS predictive-autoscaling study; IEEE TNSM (2021) Kubernetes-edge scaling study[97][37] |

Proactive methods contrast reactive autoscaling (changing behavior when the execution context changes) with proactive autoscaling (anticipating changes using historical knowledge and observed trends); the latter is typically also reactive, while the former may not be proactive when changes or uncertainties cannot be predicted. [125]

Machine-learning-based autoscaling uses workload forecasts and multidimensional resource signals to combine prediction with reactive scaling; versus threshold-based approaches, it achieved a 33.7% increase in CPU utilization and a 32.7% reduction in operational costs with stable application performance, but accuracy fell to 82.7% during sudden load spikes [97].

Machine-learning-based autoscaling: contextual/non-autoscaling energy evidence—optimization/forecasting/predictive maintenance/decision-making; data-quality/scalability/distributed/deployment challenges [152]; limits: sudden load spikes, complex/changing loads, longer horizons, beyond AWS retail/e-commerce; substantial data collection/training infrastructure [97].

In the page's operational scope, auto-scaling adjusts cloud resources in response to observed or predicted system conditions; conventional scaling is reactive when metrics breach thresholds, while predictive auto-scaling triggers actions from forecasts of target metrics. [135]

**Forecasting and statistical time-series methods**

Proactive Methods advance cloud auto-scaling research by using predictions to adjust resources before or as workload changes occur, improving resource utilization and reducing response times [143]. An ARIMA-based predictor achieved 91% accuracy on seasonal workloads, illustrating the value of anticipatory provisioning .

The requested Reactive/Proactive classification places Proactive Methods in the forecasting branch: Reactive methods respond to real-time workload fluctuations, whereas Proactive Methods forecast future demand and act before those changes [144][115]. The broader taxonomy also recognizes hybrid autoscalers alongside the reactive and proactive types [78].

Proactive Methods forecast future resource requirements and scaling needs; a multivariate forecaster uses several variables for a more holistic scaling decision than the common univariate form, but its added input/output complexity significantly increases training time [78]. They require large training datasets and delicate hyper-parameter tuning; when initial data are absent or tuning fails, accuracy can be unreliable and SLA compliance can be jeopardized [78].

Machine-learning-based autoscaling contributes a predictive, data-driven method by learning from historical and contextual workload data, forecasting multidimensional demand, mapping it to CPU, memory, and network requirements, and combining predictions with real-time monitoring to select scaling actions [97]. This supports proactive resource allocation and cost and service-performance optimization, but models may perform poorly when transferred across workload types or environments, creating a transferability risk [97][113].

rejected (reason: no_entity; allowed numbers: none; allowed citations: [106][144][146][147][113][153][154]; allowed entities: Statistical or time-series forecasting autoscaling; machine-learning-based autoscaling): Statistical or time-series forecasting autoscaling makes cloud auto-scaling proactive by analyzing historical workload series, predicting future demand, and converting forecasts into resource requirements for advance allocation before performance degrades . It improves responsiveness, reduces latency, and stabilizes scaling under fluctuating workloads [113], but classical ARIMA and Holt–Winters models are most suitable for stable trends or seasonality; their linearity and stationarity assumptions limit them for bursty, multivariate cloud-native demand .

Dynamic workloads challenge prediction; the 2022-06-28 study, “Wasserstein Adversarial Transformer for Cloud Workload Prediction,” uses WGAN-gp Transformer, reporting 5× faster inference time and up to 5.1% higher prediction accuracy on real-world workload traces; on Google cloud platforms, it significantly reduces VM over-/under-provisioning versus LSTM [149].

Machine-learning-based auto-scaling: workload data; training/inference/model-management overhead; performance varies by workload; no algorithm consistently optimal; long training cuts accuracy in rapid request-rate changes; degradation can require retraining [151]. Cited: serverless autoscaling; predictive elasticity control; no operational definition of cloud auto-scaling [135].

Machine learning-based auto-scaling should be discussed under the first main heading, 'Auto-Scaling Technology Classification', specifically under the 'Proactive Methods' subheading [140].

Reinforcement-learning-based autoscaling has a source published in 2019: “An end-to-end automatic cloud database tuning system using deep reinforcement learning” [74]. For cloud-computing auto-scaling, the source’s automatic resource management for cloud-native and serverless applications adjusts pods, replicas, and allocated resources in response to workload demand and measured utilization [155].

Reinforcement-learning autoscaling is a machine-learning subtype, proactive for future workload/rewards; RLPAS uses SARSA, state/action sets, function approximation/parallel learning, horizontal/vertical scaling but poor initial performance, long convergence; acceptable only up to 16 VMs per application, 4 state and 3 action variables [79]. MIRAS 2019 and A-SARSA 2020 leave taxonomy unresolved [141].

## Main Challenges and Solutions

**The shared problem is constrained resource management.** Academia and industry both seek to avoid underprovisioning and overprovisioning, but their immediate difficulties differ. Researchers must construct tractable models, define comparable objectives, and demonstrate that a proposed decision policy handles relevant workload variation. Practitioners must also integrate monitoring, orchestration, application configuration, and safe resource removal into a continuously operating service. [2][4]

**Each challenge changes the decision itself.** Energy management requires actions that affect physical consumption. Telecom scaling must preserve service availability despite initialization delays. Big-data and graph systems must manage data and placement as capacity changes. Workload prediction must turn uncertain estimates into appropriately timed resource decisions. The following studies provide specific examples of these solution patterns.

| Challenge | Problem manifestation | Published example | Proposed response | Decision criterion |
|---|---|---|---|---|
| Energy efficiency | Idle capacity consumes power | Alzahrani et al., EBAS, 2016 | Predict demand; adjust cores and frequency | Energy with acceptable performance |
| Telecom dynamics | Bursts and VNF initialization delays | Yi et al., 2024 | Predict traffic; learn continuously; switch states | Acceptance, cost, readiness |
| Big-data processing | Variable work and VM performance | Li et al., MarVeLScaler, 2019 | Initial sizing plus runtime correction | Expense and job performance |
| Graph-processing cost | Placement and communication affect runtime | Heidari and Buyya, 2019 | Heterogeneous sizing and repartitioning | Execution cost and performance |
| Workload prediction | Forecast errors distort provisioning | Hang et al., 2024 | Quantile forecasts and robust optimization | Efficiency versus service protection |

### Energy Efficiency

**Problem manifestation: idle resources consume energy.** A cloud application provisioned for peak demand can leave substantial capacity underused during quieter periods. Those resources can continue consuming power even when they perform little useful work. However, reducing active capacity too aggressively can increase waiting, require repeated activation, or compromise performance commitments. Energy-aware autoscaling must therefore account for both the consumption avoided and the service consequences of the reduction. [17]

**Power reduction is not automatically energy reduction.** Power is the rate of energy consumption, commonly measured in watts; energy accumulates over execution time. Lowering processor frequency can reduce instantaneous power but lengthen execution. Similarly, putting a resource to sleep saves idle energy only if that saving outweighs switching costs and any additional work caused by the transition. The energy-efficiency literature consequently treats shutdown, consolidation, and frequency control as workload-sensitive decisions. [17]

**Academic and industrial constraints differ here.** Researchers need power models that capture the relevant processor, memory, storage, network, and transition behavior. Operators must determine which of these controls they actually possess. A public-cloud application owner may remove a VM without controlling whether the provider switches off its physical host, whereas an infrastructure operator can coordinate workload placement with physical power management. The distinction matters because lower instance use and lower physical energy are related but different objectives. [17]

**Published study: Energy-Based Auto Scaling.** Alzahrani and colleagues presented Energy-Based Auto Scaling, or EBAS, in the joint 2016 IEEE HPCC/SmartCity/DSS proceedings, DOI **10.1109/HPCC-SmartCity-DSS.2016.0123**. EBAS proactively adjusts CPU-core count and frequency, combining CPU-usage prediction, workload consolidation, and dynamic voltage and frequency scaling, or DVFS. Its experiments report **14% average energy savings compared with the Linux governor**. [18]

**Proposed solution: resize processing capacity itself.** EBAS addresses more than the number of running service replicas. Its demand prediction informs how many CPU cores should be active and how fast they should run. Consolidation concentrates work on the required processing capacity, while frequency adjustment reduces excessive per-core performance when the workload does not need it. This connects workload anticipation directly to physical processor controls. [18]

**Prediction helps manage the performance trade-off.** A purely reactive power policy can wait until utilization increases before restoring capacity. A predictive policy can prepare additional cores or higher processing frequency beforehand. The intended benefit is to reduce unnecessary capacity during quieter intervals without allowing the next rise in work to encounter an avoidable processing shortage. The practical result depends on whether demand can be forecast sufficiently early and whether reduced frequency still satisfies application performance requirements.

**Consolidation and frequency scaling are complementary.** Frequency control changes the capability of active processors; consolidation changes how many resources must remain active. One does not automatically replace the other. A deployment with long quiet periods may benefit strongly from reducing active-resource count, while a workload that changes within a continuously busy host may present more opportunity for fine-grained capacity adjustment. EBAS’s combined design is important because it addresses both dimensions.

**A second study exposes the trade-off.** Cañete and colleagues’ *A proactive energy-aware auto-scaling solution for edge-based infrastructures*, associated with UCC 2022 and recorded as a 2023 proceedings publication, combines energy-aware task placement with node activation decisions. Its EdgeCloudSim experiments use Shanghai Telecom workload data and heterogeneous edge devices. The model includes computation, communication, idle, sleep, and switching energy rather than treating every active node as equivalent. [12]

**More aggressive sleeping saves more energy.** That framework offers two operating modes. One can select currently working nodes for subsequent sleep after their ongoing execution finishes; the more resource-preserving mode keeps currently executing nodes active. The aggressive configuration achieved a best-case 92.5% energy reduction against a non-autoscaling Fastest-fit configuration. The more conservative mode achieved zero or nearly zero failed requests in most tested cases, while consuming about 26% more energy on average than the aggressive mode. [12]

**The optimizer also consumes decision time.** In separate scalability experiments, one aggressive-mode configuration with 30 nodes required up to about 175 seconds to solve, whereas the resource-preserving mode substantially reduced the search space and solved the tested cases much faster. Since the workload experiments used a one-minute scaling interval, such a long decision can exceed the interval it is meant to manage. This shows why optimizer execution time belongs inside the energy-performance trade-off rather than outside it. [12]

**The practical implication is control-aware optimization.** EBAS is relevant where core-level and frequency controls are accessible; node-level consolidation is relevant where resources can actually enter lower-power states. If those controls are absent, reducing cloud charges remains worthwhile, but it is a different demonstrated outcome. Energy savings are strongest when the chosen action changes physical consumption for long enough to outweigh transition and performance costs.

**Additional documented evidence**

energy efficiency: The source's relevant scope is enterprise big-data operations, data centers, computational overhead, data replication, and cloud infrastructure use. It does not specify particular auto-scaling workloads, resource layers, energy measures, service objectives, population denominators, or geography. [171]

In this study, energy efficiency as an autoscaling challenge means minimizing global energy consumption while allocating computing resources to meet user-service quality-of-service requirements in edge infrastructures. Its boundary includes the base (idle) energy consumption of edge nodes, dynamic energy consumption from application execution, and the energy consumed by node scaling. [172]

energy efficiency: The energy-efficiency problem manifests as minimizing IT-infrastructure resource use while maintaining the agreed service level. In the autoscaling context, cloud costs and data-center maintenance costs are increasing, so systems must allocate and reallocate resources efficiently while preserving QoS. Insufficient resources can cause denial of service; excessive reservation creates unprofitable resource use. [84]

The source connects energy efficiency to energy-efficiency research generally: it is titled “Systematic literature review and bibliometric analysis of energy efficiency,” was published on 2024-05-27, and identifies “Energy Efficiency and Management” among its topics. It does not establish a direct relationship to cloud auto-scaling research. [173]

The page treats energy efficiency in computing as a topic and cites a survey on energy-efficient resource-allocation techniques for cloud computing systems, as well as studies on energy-efficient resource management and energy-consumption–delay trade-offs in cloud and cloud-fog computing. 2014. [170]

energy efficiency: The reported application scope is cloud-based microservices applications, including CPU-bound applications, with the objective of using an optimal amount of resources while maintaining or improving performance. The study describes a reduction in energy consumption and competitive cost compared with a nonelastic scenario. [65]

The source defines energy efficiency as useful computational work per unit of energy, and describes the challenge as maximizing computational output while minimizing energy consumption. In data centers, energy efficiency is affected by power, cooling, infrastructure, workload, and utilization constraints. [175]

energy efficiency: The source reports electrical power consumed over an entire build, measurements of power drawn by individual subsystems, an energy balance, and a Total Energy Indicator derived using Eco-Indicators. [176]

energy efficiency: The study authors are Aldossary, M and Djemame, K. [178]

Energy efficiency in cloud-based microservices has a performance-and-energy gap; Elergy, a lightweight proactive elasticity model, periodically reorganizes resources to use an optimal amount while maintaining or improving CPU-bound application performance, reducing energy consumption and achieving competitive cost versus a nonelastic scenario. [65] In simulated applications under the same workload, energy consumption decreased by a minimum of 47% versus RR using 50 virtual machines and approximately 55.41% with ACS in a 150-VM model; ACS achieved 11% higher energy gain than other algorithms, while DVFS and PSO differed by less than 3%. [166]

A study directly addresses energy efficiency via host energy consumption and energy violations influenced by microservice autoscaling policies. [174] For big-data jobs, Tetris’s runtime elastic VM adjustment changed CPUs at times for fixed-cluster imbalance and accommodated 31.3% more jobs on a real private cloud platform using Facebook trace and Wikipedia dataset, with no energy-consumption or energy-specific metric. [177]

Energy efficiency is a multidimensional cloud-data-center objective: CO2 emissions, energy consumption, execution time, cost; weighted scoring compares VM configurations and algorithms, classifies energy levels to reduce energy use, preserve processing time, and improve cost and environmental outcomes [166]. The study's VM scheduling used cloudlet workloads in one cloud datacenter [166].

**Energy Efficiency**

Energy efficiency requires reducing cloud-system energy consumption while preserving QoS; Saxena et al.’s neural-network-driven autoscaler directly addresses this through energy-efficient VM allocation while maintaining SLA compliance [243,572]. Under the stated SLA condition, the learned policy links resource scaling to the purpose of improving energy efficiency without sacrificing service quality.

### Dynamic Nature of Telecom Services

**Problem manifestation: demand and readiness change together.** Telecom workloads combine recurring busy and quiet periods with sudden bursts and heterogeneous service requirements. In network function virtualization, or NFV, functions traditionally tied to dedicated hardware run as virtual network functions, or VNFs. Elasticity requires these software functions to become available quickly enough to serve changing traffic, but creating an instance introduces delay before it can process requests. [19]

**Service chains make local metrics insufficient.** A service function chain, or SFC, connects functions such as a firewall and gateway into a required processing sequence. Adding capacity to one function may not resolve congestion elsewhere in the chain. Telecom scaling therefore needs to consider service availability and the required functions together, rather than assuming that average CPU utilization describes the whole service’s ability to accept traffic. [20]

**Edge deployment adds placement constraints.** Resources close to users can be heterogeneous and limited, while requests may require low latency or capabilities present on only some devices. A task might need a particular peripheral or a graphics processing unit, or GPU. Moving it to a remote node with spare CPU can introduce communication delay or fail to satisfy its capability requirements. These constraints make telecom-edge scaling more than a replica-count problem. [12]

**Research must connect several decisions.** The academic problem is to coordinate traffic prediction, resource selection, and VNF lifecycle management under changing conditions. The deployment problem is to fit those decisions into orchestration systems while preserving service continuity. Even an accurate traffic forecast offers limited protection if its lead time is shorter than the function’s readiness delay or if the needed resources cannot be placed where the service requires them.

**Published study: traffic prediction and VNF deployment.** Bo Yi and colleagues published *Traffic Prediction-Based VNF Auto-Scaling and Deployment Mechanism for Flexible and Elastic Service Provision* in *IEEE Transactions on Services Computing*, volume 17, issue 5, pages 2959–2973, in 2024. The paper addresses heterogeneous and bursty VNF traffic through a predictor, a continuously learning closed loop, and dynamic switching among VNF states. [20]

**Proposed solution: combine prediction with lifecycle control.** The traffic predictor uses a gated recurrent unit, or GRU, a recurrent neural-network architecture for sequential data. Its role is to estimate changing traffic before resource shortages occur. The closed loop then allows the prediction model to learn and evolve as conditions change, instead of treating its initial training as permanently sufficient. [20]

**State switching addresses repeated initialization.** The study introduces different VNF states and changes them dynamically according to current requirements. The mechanism avoids treating every demand reduction as a reason to destroy a function and every increase as a reason to initialize a new one. This targets lifecycle work directly: repeated initialization and destruction can add cost and slow the response even when the traffic forecast itself is useful. [20]

**The reported results cover distinct outcomes.** Yi and colleagues report the following experimental comparisons with the state-of-the-art methods used in their evaluation. Prediction quality, accepted service demand, and operating cost measure different parts of the proposed mechanism. [20]

| Metric | Reported result | Operational meaning |
|---|---|---|
| Traffic-prediction accuracy | Over 98% | Quality of anticipated demand |
| Service-acceptance improvement | More than 18% | More service demand accommodated |
| Overall-cost reduction | More than 20% | Lower evaluated provisioning cost |

**The mechanism explains the combined benefit.** Prediction can identify upcoming demand, but lifecycle control determines how quickly and cheaply the system can respond. Continuous learning addresses evolving traffic, while state switching reduces avoidable setup and teardown. The solution is therefore stronger than adding a predictor to an otherwise unchanged destroy-and-recreate workflow: it changes both demand analysis and resource execution.

**Earlier work supports multiple prediction horizons.** Luong and colleagues’ 2018 IEEE 5G World Forum paper, *Predictive Autoscaling Orchestration for Cloud-native Telecom Microservices*, combines real-time prediction of peaks or bursts with longer-term forecasting of periodic or seasonal demand. The approach was integrated with Kubernetes in a containerized testbed for stateless telecom services. Its emphasis is on forecasting around instance-creation delay, whereas Yi and colleagues additionally emphasize continuous learning and VNF-state transitions. [19]

**The practical implication is lifecycle-aware evaluation.** Telecom operators should assess accepted services, readiness time, response latency, overall cost, and repeated initialization—not just utilization or prediction accuracy. A policy can predict traffic well yet still fail operationally because the correct function is not ready at the required location. Conversely, reusable VNF capacity can soften forecast errors by reducing the work required to restore service.

**The judgment changes with service constraints.** Predictive lifecycle management is particularly valuable when startup costs and service-availability delays are substantial. Its benefit weakens when traffic shifts outside learned behavior, VNF states offer little reuse, or placement constraints prevent timely activation. Telecom elasticity depends on coordinating prediction with function readiness and service-chain requirements, not on choosing a forecasting model in isolation.

### Big Data Processing

**Problem manifestation: resource demand changes during execution.** Big-data jobs vary in input volume, required parallelism, and sensitivity to CPU, memory, storage, and communication. A fixed cluster sized for peak work wastes resources on smaller jobs. An undersized cluster can miss completion targets, while a cluster that expands only after a short intensive phase begins may receive useful capacity too late. [21]

**VM performance is not a fixed constant.** A public-cloud job can experience changing processing capacity during its execution. If an initial sizing model assumes a stable VM performance level, it can underestimate the resources needed to meet a deadline. This makes runtime correction important even when the workload’s initial data volume and target completion time are known. [22]

**State makes contraction a separate problem.** In Hadoop Distributed File System, or HDFS, worker nodes can hold data needed by the cluster. Removing a node therefore requires more than observing low CPU utilization: data may need to be transferred before the node is decommissioned. The resulting delay depends on the amount of data involved. Unsafe removal can jeopardize data availability, while safe removal can be too slow for the intended scaling interval. [21]

**Published study: MarVeLScaler for MapReduce.** Li and colleagues’ MarVeLScaler study was first published online in *IEEE Transactions on Cloud Computing* on 1 October 2019, DOI **10.1109/TCC.2019.2944916**. Evaluated with Hadoop in Alibaba Cloud, it reports **98.4% initial-cluster-size prediction accuracy** and **30.8% expense savings**, with performance similar to the state-of-the-art methods used for comparison. [22]

**Proposed solution: separate sizing from correction.** MarVeLScaler has two principal components. A Scale Estimator predicts an initial cluster size from the workload and deadline, using a multi-view deep-learning approach. A runtime Scale Controller then changes cluster scale according to execution status. The combined design addresses both the initial provisioning decision and deviations that emerge while the job runs. [22]

**Initial prediction reduces avoidable underprovisioning.** Starting with a suitable resource allocation can prevent a job from immediately falling behind and then waiting for expansion. The deadline supplies an application-level objective, rather than using a generic utilization threshold as a substitute for success. The estimator’s output is therefore meaningful because it connects expected work to an explicit completion requirement.

**Runtime control handles performance variation.** An initial estimate cannot fully anticipate changing VM behavior during a job. MarVeLScaler’s controller uses real-time execution information to identify when additional capacity is needed. Its advantage over initial sizing alone is adaptability; its advantage over purely reactive resizing is that the job does not have to begin from an arbitrary allocation and discover every capacity requirement through delayed corrections. [22]

**This is a hybrid application pattern.** The initial estimator is proactive because it allocates resources before the processing requirement unfolds. The runtime controller corrects observed execution conditions. This illustrates why the two-category taxonomy should describe component behavior rather than force an entire complex system into one exclusive label. The combination is especially useful when job inputs are known but execution performance remains variable.

**CEAS illustrates a simpler operational alternative.** The 2019 Applied Sciences paper *An Auto-Scaling Framework for Analyzing Big Data in the Cloud Environment* presents Cost-Effective Auto-Scaling, or CEAS, for Hadoop on Amazon EMR. It uses CloudWatch monitoring and cluster resizing to add resources as demand increases and remove idle resources as it declines. Its signals include available cluster memory and the ratio of pending execution containers. [21]

**The CEAS case makes resizing concrete.** Its evaluation processes a 20 GB dataset and includes an elastic cluster ranging from 3 to 15 workers, compared with fixed-capacity configurations over one-hour and three-hour periods. This demonstrates a deployable threshold-and-orchestration approach to variable workloads. It also exposes the practical requirement for data-safe HDFS decommissioning, which remains necessary regardless of whether the decision to remove capacity comes from rules or learning. [21]

**Counterevidence shows that elasticity can disappoint.** *Experimentally Evaluating the Resource Efficiency of Big Data Autoscaling* reports a 2025 evaluation of 18 Spark batch jobs across 13 configurations: three Google Dataproc Serverless configurations and ten additional Google Cloud configurations. The study found no significant resource-efficiency gain from the tested demand-based autoscaling over static allocations. It identifies inflexible node sizes and fixed memory-to-CPU ratios as important causes. [23]

**Its resource-use comparison favors static choices.** For the three Dataproc Serverless configurations, the study records which configuration used the fewest executor-seconds for each of the 18 jobs. Executor-seconds accumulate the number of allocated executors over execution time. The observed counts are as follows. [23]

| Configuration | Allocation policy | Jobs with lowest executor-seconds |
|---|---|---:|
| S1 | Dynamic allocation | 2 of 18 |
| S2 | Static: 8 executors | 9 of 18 |
| S3 | Static: 16 executors | 7 of 18 |

**Delayed capacity explains part of the difficulty.** For some tested jobs, maximum executor allocation appeared only around 180–200 seconds into runtime, which the authors interpreted as the delay before initial demand for more executors materialized. If the relevant processing phase is already advanced by then, the additional executors offer less useful work than their allocation suggests. This is the big-data version of the readiness problem: resource availability must align with the job phase that needs it. [23]

**Resource shape can dominate resource count.** Adding another node also adds its bundled memory and CPU proportions. A memory-heavy job can therefore accumulate excess CPU, while a different job may need the opposite balance. The 2025 evaluation found that selecting node type per job had a larger effect on resource efficiency than continuously adjusting node count. This suggests that a count-only autoscaler can be limited by the resource shapes it is allowed to choose. [23]

**Vertical elasticity offers a complementary solution.** Choi, Cho, and Kim’s 2021 *Employing Vertical Elasticity for Efficient Big Data Processing in Container-Based Cloud Environments* independently adjusts CPU and memory allocations for running Docker containers. Its controller monitors resource use through cAdvisor and applies separate policies to the two resources. Experiments use Hadoop and Spark workloads from the HiBench benchmark suite. [24]

**Shared-host gains come with startup costs.** In the study’s concurrent-container tests, the total Hadoop makespan fell from 10,621.2 seconds under fair static allocation to 5,301 seconds under adaptive allocation: a calculated reduction of approximately 50.1%, using \((10,621.2-5,301)/10,621.2\). Yet the adaptive scheme incurred an average 18.7% execution-time overhead in the single-container comparison against an allocation using all available host resources. Reclaiming idle capacity from neighboring jobs can therefore help shared operation while gradual expansion can hurt an isolated job. [24]

**The practical judgment is multidimensional elasticity.** Big-data autoscaling should distinguish initial sizing, runtime performance correction, resource shape, and safe data movement. MarVeLScaler demonstrates the value of initial prediction plus runtime control; CEAS demonstrates straightforward cloud integration; the Spark evaluation shows when node-count adjustment adds little. Elasticity is most useful when its action granularity and readiness delay match the job’s actual phases and bottlenecks.

**Additional documented evidence**

big data processing: The big-data manifestation is that different graph algorithms and systems expose different, non-trivial resource-demand patterns during execution, so a single observable such as active vertices is insufficient for scaling decisions. [181]

big data processing: The study describes graph-processing systems as using static deployment on a fixed set of machines, despite graph applications having iterative, highly irregular workloads. This mismatch can cause resource waste, high operational costs, system-wide crashes under under-provisioning, and difficult resource-management and scheduling decisions. Graph workloads are also sensitive to data migration when resources are leased or released, and scaling policies interact non-trivially with graph workloads. [181]

big data processing: In this study, the autoscaling challenge concerns elastic graph-processing jobs and analytics platforms whose resource demand varies across irregular, iterative workloads. The operational response is to allow infrastructure to grow and shrink at runtime instead of running on a fixed, statically defined set of machines. [181]

Big data processing concerns extremely large datasets whose volume, velocity, and variety exceed the capabilities of traditional databases. Its scope includes batch, stream, and massively parallel processing, as well as cloud data warehouses and efficient single-node analytics; the source names applications in finance, retail, healthcare, technology, scientific research, customer recommendations, predictive analytics, and real-time monitoring. [182]

big data processing: The challenge covers cloud-based, data-intensive processing systems and platforms, including Hadoop, Dryad, Pregel, Storm, and Spark. Its affected population includes tenants, applications, jobs, tasks, and distributed data-processing clusters; the source describes cloud and data-center settings rather than a narrower geography. [179]

big data processing: Big-data autoscaling challenges arise because data is gathered at unprecedented scale, has complex structures, requires frequent and complex access, and runs in distributed environments with unpredictable failures. Cloud tenants use fixed-size VMs and change VM counts as demand changes, which can be too coarse for dynamic data-processing workloads. [179]

big data processing: The page situates big-data processing in cloud environments where users concurrently run large-scale, data-intensive applications, creating a resource-management and elasticity challenge for autoscaling: demand fluctuates, resources may be underutilized, and users pay according to resource usage. [179]

The publication date is 01 September 2016. [165]

Big data processing: The DOI is 10.1007/s10723-016-9371-1. [165]

big data processing: Graph-processing autoscaling—demand≠active-vertex counts: system metrics vary at fixed vertices; vertices vary without comparable wallclock/memory; algorithm/system creates variability requiring fine-grained policies [181]; proposed BatchBench workload-aware benchmark: six-class workload taxonomy, parameterized generator, five-axis harness, standardized policy/agent interface [180].

Big data processing's study was published on 2019-06-17. [183] It relates to cloud auto-scaling through elastic resource management for data-intensive jobs; Graphless combines serverless computing with graph processing via push/pull architectures, an orchestrator, and a memory-as-a-service component, evaluating fine-grained elasticity, cost effectiveness and performance in real-world experiments. [184]

The big-data-processing study's publication venue is Journal of Grid Computing, Volume 14, Issue 3. [165]

**Big-data scope and manifestation**

### Cost-Effective Graph Processing

**Problem manifestation: graph placement affects execution.** Graph analytics operates on connected vertices and edges, often through repeated updates. Partitioning decides which machine owns each part of the graph, and connections crossing those partitions can create network communication. Adding VMs changes processing capacity, but it can also change communication, data distribution, and synchronization costs. Graph autoscaling therefore cannot be reduced to spreading independent requests over more identical workers. [25]

**The cheapest machine is not always cheapest execution.** A lower-priced VM can become more expensive overall if it extends runtime sufficiently. Likewise, fewer VMs can save capacity charges while increasing communication or creating an overloaded partition. The relevant objective is the cost of completing the graph computation at the required performance level, not merely minimizing the current instance count.

**Fixed-cluster assumptions obscure cloud costs.** Heidari and Buyya identify elasticity, monetary charges, resource heterogeneity, and changing network conditions as gaps in many graph-processing designs. Their criticism concerns frameworks built around a largely fixed available cluster rather than explicit pay-as-you-go resource decisions. In a cloud setting, choosing resource types and deciding when to release them become part of the algorithmic resource-management problem. [26]

**Published study: heterogeneous graph autoscaling.** Safiollah Heidari and Rajkumar Buyya’s *A Cost-Efficient Auto-Scaling Algorithm for Large-Scale Graph Processing in Cloud Environments with Heterogeneous Resources* was published online in 2019 and appeared in *IEEE Transactions on Software Engineering*, volume 47, issue 8, pages 1729–1741, in 2021. It targets convergent graph applications and reports better performance with **more than 50% lower dollar cost than Giraph**. [25]

**Proposed solution: couple sizing with repartitioning.** The study automatically adjusts both the number and types of VMs according to the graph application’s computation requirements. Smart profiling informs resource selection, while dynamic repartitioning distributes graph partitions across the selected resources. These components operate together: choosing a better VM mix is useful only if the graph’s work can be placed effectively on that mix. [25]

**Profiling makes heterogeneity operationally useful.** Different VM types provide different combinations of processing capacity, memory, and price. Treating them as interchangeable workers can misallocate work or overlook a more economical combination. Profiling supports a computation-aware decision about which resource mixture is suitable, rather than assuming that the smallest or largest type must be best.

**Repartitioning makes resource changes usable.** A graph cannot always take advantage of a new VM simply because it exists. Work and graph state must be distributed so that the changed resource set contributes usefully. Dynamic repartitioning addresses this mismatch, while also creating an overhead that the scaling decision must justify. The mechanism therefore connects the decision to change resources with the work required to make that change beneficial.

**Convergence changes the provisioning question.** A convergent computation proceeds toward a termination condition rather than generating the same amount of independent work indefinitely. Resource requirements can change over its execution. A computation-aware autoscaler can adjust the remaining resource allocation to those changing requirements instead of retaining a configuration selected only from the original graph’s size. The cited study’s focus on convergent applications is central to that design. [25]

**Simple cost accounting clarifies the trade-off.** For compute charges alone, cost can be expressed as the sum of each instance’s price rate multiplied by its billed duration:

\[
C_{\mathrm{compute}}=\sum_i p_i t_i.
\]

With \(p_i\) in dollars per hour and \(t_i\) in hours, the result is dollars. Resource selection changes both terms: a more capable configuration may cost more per hour but complete sooner. Repartitioning and communication matter because they can extend duration and may introduce additional charges beyond this simplified compute accounting.

**Related research adds service-level provisioning.** Heidari and Buyya’s 2019 *Future Generation Computer Systems* study proposes Graph Processing-as-a-Service, or GPaaS. It accepts multiple graph requests, monitors quality of service—QoS—against SLAs, selects resource combinations, scales resources according to workload and agreements, and dynamically repartitions graphs. This extends the problem from one graph execution to a service handling multiple users’ requirements. [26]

**Its results combine time and cost.** The GPaaS study reports execution-time reductions of up to 10%–15% relative to Giraph, and monetary-cost reductions of more than 40% relative to Giraph or PowerGraph. Its evaluated objectives are execution time and execution cost. This complements the heterogeneous autoscaling study by showing how graph-specific resource decisions can be tied to user-facing service requirements. [26]

**The practical judgment is placement-aware costing.** Graph autoscaling should evaluate resource price together with remaining computation, partition balance, communication, and redistribution overhead. The cited approach is attractive when the benefit of changing the resource mix exceeds the cost of moving graph work. Its advantage weakens when repartitioning dominates the remaining execution or when the application does not exhibit the convergent behavior the policy is designed to exploit.

### Workload Prediction

**Problem manifestation: forecast errors become resource errors.** Underprediction can leave too little capacity ready when demand arrives, creating queues, missed deadlines, or service violations. Overprediction can keep unnecessary resources active. Because the consequences differ, a predictor with a low average numerical error is not necessarily the predictor that produces the best autoscaling decisions. Hang and colleagues identify forecast-driven underprovisioning as the motivation for uncertainty-aware scaling. [27]

**High-dimensional demand complicates estimation.** Cloud services differ in their CPU, memory, storage, and network requirements, and their behavior changes over time. Some resource demands are interdependent, so forecasting each separately can miss important relationships. Saxena and colleagues’ 2023 analysis identifies variability and dimensionality across heterogeneous services as central workload-prediction difficulties. [28]

**Timing creates another source of error.** A forecast must describe demand when a scaling action can take effect, not simply the next value in a telemetry series. Monitoring and model execution also consume time. The 2024 IEEE Access service-chain study describes large monitoring-data volumes and VNF readiness delays of several minutes, illustrating why a technically accurate short-horizon forecast may still be poorly matched to an operational scaling decision. [8]

**Published study: robust cloud-database autoscaling.** Haitian Hang and colleagues published *Robust Auto-Scaling with Probabilistic Workload Forecasting for Cloud Databases* at the 2024 IEEE International Conference on Data Engineering, or ICDE, pages 4016–4029. The study combines probabilistic quantile forecasts with robust optimization and allows the degree of conservatism to vary across the decision horizon. Its reported outcome is robust scaling with reasonable resource efficiency. [27]

**Proposed solution: forecast a distribution.** A point forecast supplies one anticipated demand value. A probabilistic forecast instead describes a range of possible future outcomes, from which different quantiles can be selected. A quantile identifies a demand level associated with a chosen position in the predictive distribution. This gives the controller information about the risk surrounding the central prediction rather than requiring an arbitrary fixed buffer around it. [27]

**Quantile choice changes resource conservatism.** Selecting a higher demand quantile generally prepares for a larger possible workload than selecting a central estimate. That can reduce the risk of underprovisioning but requires more resources. A less conservative choice can improve efficiency when shortage consequences are tolerable or forecast uncertainty is low. The important change is making this trade-off explicit and adjustable rather than hiding it inside one forecast number.

**Robust optimization turns uncertainty into actions.** Hang and colleagues formulate autoscaling as a robust optimization problem using the forecast information. Resource choices are evaluated against selected uncertainty levels, allowing protection against forecast error to participate directly in the decision. The system is therefore not merely producing uncertainty estimates for a dashboard; it uses them to determine the capacity policy. [27]

**Conservatism can vary across the horizon.** The study permits different forecast quantiles at different future decision points. This is useful because the consequences of an error depend on when it occurs and whether there is still time for a corrective action. A deployment need not use the same safety position for every point in its plan. Instead, the decision can balance resource efficiency and protection over the sequence of upcoming requirements. [27]

**Capacity translation still needs service knowledge.** A demand quantile is not itself a number of database instances or processor cores. The autoscaler still needs a relationship between workload, resource configuration, and acceptable service performance. It also needs the readiness delay of the chosen action. Uncertainty-aware forecasting improves the information supplied to that calculation; it does not remove application-specific capacity constraints.

**Other research distinguishes uncertainty sources.** A 2024 Cluster Computing study evaluates hybrid Bayesian neural networks and probabilistic LSTM models on 12 workload traces from Google Cloud and Alibaba. It distinguishes epistemic uncertainty—uncertainty associated with the model or limited knowledge—from aleatoric uncertainty, the variability inherent in the observed process. Its hybrid Bayesian models address both, while the evaluated LSTM distributional model captures aleatoric uncertainty. [13]

**Joint forecasts improve realism at a cost.** The same study examines processing-unit and memory demand together and reports that uncertainty modeling improves service-level metrics. Bivariate forecasting can represent resource dependence more directly than isolated predictions, but it also requires more data and computation. The resulting design choice is not simply between “statistical” and “deep” models: it concerns which resource relationships and uncertainty sources materially affect the scaling objective. [13]

**Model comparison must reach the controller.** Saxena and colleagues implement five categories of machine-learning predictors on a common platform using three benchmark cloud workload traces. That shared experimental basis helps expose trade-offs among prediction approaches. For autoscaling, the comparison must additionally follow forecasts through resource decisions to service outcomes, since the cost of an error depends on its direction, timing, and operational consequences. [28]

**The practical judgment is risk-aware prediction.** Point forecasts are attractive when uncertainty is modest and resource efficiency dominates. Quantile-based robust control is more valuable when shortages carry substantial service consequences and uncertainty estimates remain calibrated to actual behavior. If workload changes invalidate those estimates, greater mathematical conservatism alone does not restore dependable protection. Predictive autoscaling should optimize the consequences of forecasting errors, not merely the average distance between predicted and observed demand.

**Reported results retain their measurement basis.** Percentages above belong to the named workloads, baselines, and experimental settings; they do not establish a cross-study ranking. Prediction “accuracy” follows each study’s definition, and relative improvements are not percentage-point changes. VM leasing time and executor-seconds measure resource use, monetary cost measures charges, and energy measures electricity consumed. Simulations and testbeds are identified where discussed; the makespan reduction is explicitly calculated from the published endpoints.

**The overall conclusion is application-aware control.** Reactive and proactive methods are complementary tools, not competing guarantees of efficiency. The strongest solutions combine an appropriate trigger with realistic readiness time, safe state handling, suitable resource shapes, and explicit treatment of service risk. Hybrid control is often a useful architecture, but its value comes from solving those concrete problems—not from combining algorithms for its own sake.

**Additional documented evidence**

big data processing: The big-data challenge manifests as growing demand for large-scale data processing and data-analysis applications, while existing Hadoop-based processing has limitations for large-scale structured data, graph data, and streaming data. The source links this to exponential data growth and availability and to domain-specific workload requirements. [165]

The source describes the solution direction as a “new wave of mostly domain-specific, optimized big data processing platforms,” developed to tackle the limitations of Hadoop in structured, graph, and streaming data scenarios. [165]

For workload prediction, the bottleneck is limited prediction precision and robustness; the scaling signal is predicted workload; the primary objectives are QoS assurance and resource-cost optimization; and the solution type combines adaptive prediction, a performance model, and reactive queuing-based correction. [164]

Energy efficiency is identified as a topic in the source, and the review connects reinforcement-learning autoscaling with green computing and energy-efficient solutions. [160]

The source is a published 2025 review of reinforcement-learning-based predictive autoscaling. It states that reinforcement learning learns resource-allocation policies through environmental interaction and identifies predictive auto-scaling, deep-learning integration, meta-reinforcement learning, green computing, multi-objective reinforcement learning, hybrid approaches, and continuous learning as relevant areas or directions. 2025-04-11. [160]

Auto-Scaling technology in cloud computing: The paper presents cloud auto-scaling as automatically and dynamically resizing application infrastructure in response to workload demand and performance requirements. Its scope includes automated resource allocation for cloud applications and infrastructure, using actions such as adding or removing VMs or changing VM resources. [156]

Auto-Scaling technology in cloud computing automatically increases or decreases allocated compute, memory, or networking resources as traffic spikes and use patterns demand, using policies that can provide capacity or launch additional resources. [45]

Auto-Scaling technology in cloud computing: Horizontal scaling adds more machines to a system and distributes the load, while vertical scaling upgrades one machine's CPU, RAM, and storage. Horizontal scaling is therefore a resource-action dimension relevant to cloud auto-scaling, not by itself a Reactive or Proactive decision-policy category. [168]

Auto-Scaling technology in cloud computing: The study analyzes auto-scaling-related resource adaptation as part of operational challenges in dynamic network services: static VNF planning and chaining must be evaluated under dynamic traffic, with performance assessed through blocking behavior. [158]

Auto-Scaling technology in cloud computing: The study concerns distributed stream-processing systems with highly variable workloads. Its autoscaler dynamically adapts assigned resources to input workload to balance performance and resource cost. The study proposes augmenting existing autoscaling controllers with windowing and weighting methods; it reports that this mitigated over 90% of undesirable extreme parallelism shifts and significantly reduced scaling-behaviour volatility. over 90% percent (undesirable extreme parallelism shifts mitigated; extreme parallelism shifts observed in the study; windowing and weighting methods augmenting existing autoscaling controllers). [159]

Auto-Scaling technology in cloud computing: Energy efficiency manifests as wasted energy from inefficient hardware use in containerized parallel applications; the study addresses this by tuning runtime threads and reallocating released cloud resources. [66]

energy efficiency: The study proposes TT-Autoscaling, which operates inside containers by tuning runtime thread counts and at the cloud-infrastructure level by transferring released resources to other containers. Compared with default container execution, it reports 55.8% performance improvements, 53.6% energy reductions, and 79.5% EDP improvements, and it outperforms strategies using vertical autoscalers proposed by orchestrator tools. 55.8% % (performance improvements; container-based parallel applications; comparison with default execution of containers). [66]

Auto-Scaling technology in cloud computing: In the study's telecom-cloud setting, cloud computing supplies elasticity, and autoscaling operationalizes that flexibility by adjusting the number of virtual network functions in response to device demand. [73]

Auto-Scaling technology in cloud computing: The study proposes a multi-view deep learning model that captures real-time performance variance and automatically scales out the cloud cluster whenever necessary. Its prototype, MarVeLScaler, contains a Scale Estimator and a Scale Controller. [163]

cloud computing: The paper presents cloud auto-scaling as automatically and dynamically resizing application infrastructure in response to workload demand and performance requirements. Its scope includes automated resource allocation for cloud applications and infrastructure, using actions such as adding or removing VMs or changing VM resources. [156]

cloud computing: The page describes auto-scaling as “also known as elasticity” and links it to the on-demand allocation of computing resources. [161]

Auto-Scaling: The study was published in GLOBECOM 2020 - 2020 IEEE Global Communications Conference. [162]

| Entity | Challenge area | Specific manifestation | Published study title | Study publication date | Study venue | Proposed solution | Study evidence |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Energy efficiency | Energy efficiency[167] | Balancing energy consumption, execution time, operational cost and CO2 emissions across VM configurations in a single datacenter[166] | A Tier Labeling Proposal for Energy Efficiency in Green Cloud[166] | 15 March 2024[166] | no evidence found | Energy-efficiency scoring and AI/neural-network classification of VM energy performance; VM consolidation and shutdown of unused machines[166] | Simulation, same workload: minimum 47% energy reduction; ACS at 150 VMs achieved 55.41% lower energy, 28.70% lower direct-allocation cost and approximately 84% lower response time than 50 VMs[166] |

**Challenge framework and scope**

Workload prediction is bottlenecked by limited prediction precision and robustness; its scaling signal is predicted workload, its objectives are QoS assurance and resource-cost optimization, and its solution combines adaptive prediction, a performance model, and reactive queuing correction [164]. By contrast, big-data processing reflects exponential data growth and demand for large-scale analysis, with Hadoop limitations for structured, graph, and streaming data motivating domain-specific optimized platforms; energy efficiency is framed as a relevant objective and future solution direction [165][160].

Auto-Scaling technology in cloud computing is the common intervention linking the required challenge areas to solutions: it converts workload, SLA, and application information into horizontal or vertical resource changes, aiming to preserve service objectives while limiting cost, energy use, and over- or under-provisioning [115][48][169]. Published cases therefore provide comparable solution evidence, from predictive telecom forecasting, CEAS big-data scaling, and graph repartitioning to windowing and weighting that mitigated over 90% of undesirable extreme parallelism shifts [73][69][55][159].

Auto-Scaling technology in cloud computing supplies the selection frame for published examples: prioritize studies that instantiate a concrete scaling mechanism and connect it to a measurable challenge, such as telecom forecasting, CEAS big-data scaling, dynamic graph repartitioning, or workload prediction [67][69][55][73]. A systematic mapping selected 71 articles published between 2008 and January 2017, supporting study-specific examples with explicit mechanisms and outcomes rather than generic topic references [43].

Cloud computing is the deployment and economic context for the challenge-and-solution purpose: on-demand elastic resources, pay-as-you-go pricing, and heterogeneous VM choices enable flexible scaling but make workload variation, resource provisioning, cost, and SLA management central problems [40][76][69][115]. Consequently, cloud auto-scaling studies are appropriate solution cases because they test capacity adaptation against service and efficiency objectives in real cloud environments [157][102].

**Additional documented evidence**

In this source, workload prediction is forecasting future load from a managed instance group's historical load so that scaling can occur before demand arrives. The scope is cloud applications running in managed instance groups, using VM instances and CPU utilization as the supported scaling metric. The source gives no specific geography or broader affected population. [30]

workload prediction: The workload-prediction problem manifests when load changes faster than newly added instances can initialize. For applications that take a few minutes or more to initialize, reacting to real-time increases may be too slow, causing user delays while new instances are initializing. Predictive autoscaling addresses this by forecasting future load from MIG history and scaling out in advance. [30]

The source frames workload prediction as forecasting future workload so that resources can be provisioned ahead of time in proactive autoscaling; it gives news feed and social network applications as contexts where uncertain arrivals are problematic. [191]

workload prediction: Reactive autoscaling responds only after resource saturation occurs, which can cause performance degradation and inefficient resource utilization. PredictScale instead anticipates workload fluctuations and provisions resources ahead of demand; this reduces scaling delay, improves resource utilization, and mitigates latency. [80]

Workload prediction is treated as a named auto-scaling challenge and as a proactive mechanism: the study presents PredictScale, a Transformer-based proactive autoscaling framework that forecasts workload fluctuations and provisions resources ahead of demand. It evaluates the approach with real Bitbrains workload traces against reactive HPA and LSTM, BiLSTM, and CNN-LSTM predictors, reporting higher forecasting accuracy, more balanced resource provisioning, improved pod utilization, reduced operational cost, and lower latency under bursty workloads. [80]

Workload prediction as an autoscaling challenge concerns predicting future workload from past workload history and, potentially, real-time external information. Its boundary is application-specific rather than general-purpose: examples include news applications affected by physical-world events and outdoor applications affected by weather conditions. The supported population and geography are application-dependent and are not specified more broadly here. [185]

Workload prediction belongs to the Proactive Scaling treatment because the source states that prediction accuracy determines an auto-scaler’s capability to scale applications proactively. Prediction algorithms use workload history or other information to forecast future demand, and the resulting predictions are applied to resource provisioning over a prediction horizon. [185]

Workload prediction: real-world workloads include bursts, batch jobs, anomalies, seasonal patterns, and service-specific differences; CPU forecasts miss demand; anomalies limit accuracy, requiring reactive SLO protection. [186] A published study “Dynamic workload patterns prediction for proactive auto-scaling of web applications” uses PWP and NNLS; three real web applications yielded significantly more accurate predictions than existing approaches. [189]

Workload prediction reports forecasting accuracy, pod utilization, operational cost, latency, and resource provisioning balance using real workload traces. [80] Dynamic workload intensity and characteristics are difficult to predict; a published 15 December 2018 study “Dynamic workload patterns prediction for proactive auto-scaling of web applications” used PWP and NNLS on logs of three real web applications, reporting more accurate workload-pattern and resource-demand predictions than prior work. [189]

**Evidence, limitations and fit**

rejected: no_entity; allowed entities: workload prediction, Workload prediction; allowed numbers: 2012, "", 2011, 28 November 2023; allowed citations: [161], [80], [185], [187], [188], [164], [189], [109], [190], [151], [191], [192]. Workload prediction directly models workload rather than merely presenting a proactive controller: using historical web-application logs, it partitions URI space by response time and document size, computes probabilistic workload patterns, predicts the next pattern, and uses that prediction for future resource-demand estimation and proactive scaling [189].

## References

[1] <https://doi.org/10.1186/s13677-017-0100-5> Autoscaling taxonomy and hybrid control; Threshold-based mechanisms; Rule-based autoscaling; Hybrid timescale separation
[2] <https://arxiv.org/html/1609.09224v6> Cloud autoscaling survey; Autoscaling objectives; MAPE and autoscaling; Autoscaling problem formulation
[3] <https://doi.org/10.1007/s10586-018-2807-6> Control-theoretic taxonomy; Feedback-control principle; Stability and settling behavior; Control-theoretic elasticity challenges
[4] <https://learn.microsoft.com/en-us/azure/architecture/best-practices/auto-scaling> Azure autoscaling guidance; Horizontal and vertical scaling; Application and infrastructure scaling; Azure scaling mechanisms; Azure threshold example; KEDA-ba…
[5] <https://docs.aws.amazon.com/autoscaling/ec2/userguide/ec2-auto-scaling-predictive-scaling.html> AWS predictive scaling; EC2 predictive scaling; AWS predictive-scaling mechanism
[6] <https://doi.org/10.1007/s10586-026-05944-x> Startup-aware predictive control; Reactive-policy behavior; Predictive-method examples; Model-driven predictive scaling; Receding-horizon resource planning; Lo…
[7] <https://dl.acm.org/doi/full/10.1145/3603532> Hysteresis and threshold control; Optimal queue-threshold study; Queue occupancy and SLA costs; Threshold-optimization results; Queue-model assumptions; High-s…
[8] <https://doi.org/10.1109/access.2024.3375772> Metric interpretation in cloud-native systems; Schedule-based limitations; Deep-learning-based proactive scaling; Monitoring and readiness constraints
[9] <https://doi.org/10.1109/tpds.2016.2603510> Streaming resource-management study
[10] <https://www.net.in.tum.de/fileadmin/TUM/NET/NET-2022-07-1/NET-2022-07-1_11.pdf> MLScale mechanism; Post-scaling metric prediction; MLScale advantages; MLScale limitations and spike behavior; RLPAS state and action design; RL convergence co…
[11] <https://spectrum.library.concordia.ca/985627/1/Alipour_PhD_F2019.pdf> Multi-metric predictive scaling; Alipour’s predictive architecture; Deployment and inference considerations
[12] <https://eprints.whiterose.ac.uk/id/eprint/193716/1/CloudAM2022.pdf> Context-aware prediction framework; Energy-aware edge scaling; Energy and request-acceptance results; Optimization-time analysis; Heterogeneous edge constraints
[13] <https://link.springer.com/article/10.1007/s10586-024-04933-2> Workload-modeling trade-offs; Uncertainty-aware workload forecasting; Multi-resource forecasting results
[14] <https://arxiv.org/html/2001.09957v3> RL autoscaling survey; RL scaling and scheduling analysis
[15] <https://doi.org/10.1007/s11036-018-0996-0> RLPAS publication
[16] <https://doi.org/10.30574/wjarr.2025.26.2.1988> Microservices autoscaling analysis
[17] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9424070/> Energy-efficiency challenges; Software-level energy management; Virtualization and consolidation mechanisms
[18] <https://doi.org/10.1109/hpcc-smartcity-dss.2016.0123> EBAS study; EBAS mechanism
[19] <https://doi.org/10.1109/5gwf.2018.8516950> Telecom orchestration challenge; Cloud-native telecom testbed
[20] <https://doi.org/10.1109/tsc.2024.3440050> VNF service provisioning; Yi et al.’s study; GRU and closed-loop mechanism; Dynamic VNF-state switching; Experimental findings
[21] <https://doi.org/10.3390/app9071417> Elastic Hadoop challenge; Hadoop decommissioning considerations; CEAS framework; CEAS evaluation and scale-down behavior
[22] <https://doi.org/10.1109/tcc.2019.2944916> MapReduce performance variance; MarVeLScaler study; Estimator and controller design; Runtime performance adaptation
[23] <https://ar5iv.labs.arxiv.org/html/2501.14456> Spark autoscaling evaluation; Executor-seconds comparison; Executor-allocation timelines; Resource-mix analysis
[24] <https://doi.org/10.3390/app11136200> Container vertical-elasticity study; Concurrent and single-container results
[25] <https://doi.org/10.1109/tse.2019.2934849> Graph-specific cloud-scaling problem; Heidari–Buyya graph study; Profiling and repartitioning mechanism; Convergent-application scope
[26] <https://clouds.cis.unimelb.edu.au/papers/QoS-ResouceProvisioningAlgorithms-Graphs-FGCS.pdf> Cloud graph-provisioning requirements; GPaaS architecture; GPaaS evaluation
[27] <https://doi.org/10.1109/icde60146.2024.00308> Forecast-error challenge; Hang et al.’s ICDE study; Probabilistic forecasting mechanism; Robust predictive autoscaling; Horizon-dependent robustness
[28] <https://doi.org/10.1109/tpds.2023.3240567> Workload-prediction analysis; Common-platform predictor comparison
[29] <https://doi.org/10.1109/cloud.2016.0138>
[30] <https://docs.cloud.google.com/compute/docs/autoscaler/predictive-autoscaling>
[31] <https://www.itconvergence.com/blog/navigating-the-peaks-and-valleys-advantages-of-auto-scaling-in-cloud-computing-for-agile-demand-management/>
[32] <https://www.datadoghq.com/knowledge-center/auto-scaling/>
[33] <https://dspace.networks.imdea.org/bitstream/handle/20.500.12761/882/Chapter_Application_Optimisation_Workload_Prediction_2020_EN.pdf?isAllowed=y&sequence=1>
[34] <https://rshariffdeen.com/paper/CLOUD16.pdf>
[35] <https://doi.org/10.1109/ccgrid.2017.85>
[36] <https://docs.cloud.google.com/architecture/framework/sustainability/optimize-resource-usage>
[37] <https://doi.org/10.1109/tnsm.2025.3532121>
[38] <https://doi.org/10.1007/s13174-010-0007-6>
[39] <https://doi.org/10.1007/s12599-009-0071-2>
[40] <https://doi.org/10.1145/1721654.1721672>
[41] <https://sre.google/workbook/data-processing/>
[42] <https://doi.org/10.1109/ccgrid51090.2021.00041>
[43] <https://onlinelibrary.wiley.com/doi/10.1002/cpe.5186>
[44] <https://doi.org/10.1109/access.2023.3260069>
[45] <https://www.techtarget.com/it-infrastructure/definition/autoscaling>
[46] <https://medium.com/@dmosyan/autoscaling-best-practices-83139972c98e>
[47] <https://www.kamatera.com/blog/cloud-scaling/>
[48] <https://www.sciencedirect.com/science/article/abs/pii/S157401372500067X>
[49] <https://arxiv.org/html/1609.09224>
[50] <https://www.mdpi.com/1424-8220/20/16/4621>
[51] <https://doi.org/10.1109/tcc.2016.2586064>
[52] <https://doi.org/10.1109/ucc63386.2024.00076>
[53] <https://dl.acm.org/doi/pdf/10.1145/2371536.2371559>
[54] <https://dprg.cs.uiuc.edu/data/files/2016/elasticity_ic2e.pdf>
[55] <https://ar5iv.labs.arxiv.org/html/2101.07026>
[56] <https://www.linkedin.com/pulse/predictive-workload-distribution-ai-forecasting-spike-andre-gr83e>
[57] <https://ar5iv.labs.arxiv.org/html/2111.02133v1>
[58] <https://ultraviolet.ding.unisannio.it/villano/papers/ccpi2019_prepeer.pdf>
[59] <https://dl.acm.org/doi/10.5555/2735522.2735532>
[60] <https://link.springer.com/article/10.1007/s10723-024-09783-1>
[61] <http://www.buyya.com/papers/Graph-AutoScaleTSE.pdf>
[62] <https://www.mdpi.com/1424-8220/22/3/1221>
[63] <https://doi.org/10.1109/hpcc-smartcity-dss.2016.0123>
[64] <http://users.encs.concordia.ca/~abdelw/papers/CASCON14-Autoscaling.pdf>
[65] <https://lutpub.lut.fi/handle/10024/166180>
[66] <https://doi.org/10.1109/tpds.2024.3357353>
[67] <https://doi.org/10.1109/glocom.2016.7841759>
[68] <https://mainlab.cs.ccu.edu.tw/presentation/pdf/(2020)%20Machine%20learning-driven%20service%20function%20chain%20placement%20and%20scaling.pdf>
[69] <https://doi.org/10.3390/app9071417>
[70] <https://doi.org/10.1142/s0218843017500046>
[71] <https://www.scribd.com/document/968586996/Auto-scaling-Containerized-Cloud-Applications>
[72] <https://dl.acm.org/doi/abs/10.1007/978-981-96-0808-9_2>
[73] <https://doi.org/10.1109/5gwf.2018.8516950>
[74] <https://arxiv.org/html/2106.11445v1>
[75] <https://www.missioncloud.com/blog/horizontal-vs-vertical-scaling-which-is-right-for-your-app>
[76] <https://clouds.cis.unimelb.edu.au/papers/Graph-AutoScaleTSE.pdf>
[77] <https://doi.org/10.1109/ic2e.2016.31>
[78] <https://arxiv.org/html/2510.10166v1>
[79] <https://www.net.in.tum.de/fileadmin/TUM/NET/NET-2022-07-1/NET-2022-07-1_11.pdf>
[80] <https://doi.org/10.1109/ccgridw69005.2026.00037>
[81] <https://research.monash.edu/en/publications/towards-resource-efficient-reactive-and-proactive-auto-scaling-fo/>
[82] <https://kubernetes.io/docs/concepts/workloads/autoscaling/vertical-pod-autoscale/>
[83] <https://www3.cs.stonybrook.edu/~anshul/courses/cse591_s16/autoscaling_survey.pdf>
[84] <https://doi.org/10.20535/1560-8956.41.2022.271344>
[85] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10558940/>
[86] <https://doi.org/10.22215/etd/2021-14489>
[87] <https://www.vldb.org/pvldb/vol17/p4090-lu.pdf>
[88] <https://doi.org/10.3390/encyclopedia5010037>
[89] <http://www.ce.uniroma2.it/publications/tcc2022.pdf>
[90] <https://inria.hal.science/hal-01529654/document>
[91] <https://doi.org/10.21203/rs.3.rs-2897886/v1>
[92] <https://doi.org/10.1145/3659994.3660310>
[93] <https://docs.cloud.google.com/kubernetes-engine/docs/concepts/horizontalpodautoscaler>
[94] <https://medium.com/@shashank.tavildar/proactive-kubernetes-scaling-how-ml-optimizes-hpa-for-cost-savings-6528b81736af>
[95] <https://www.microsoft.com/en-us/research/wp-content/uploads/2024/02/p28-pavlenko.pdf>
[96] <https://rjwave.org/jaafr/papers/JAAFR26A5073.pdf>
[97] <https://dl.acm.org/doi/10.1145/3772326.3774726>
[98] <https://www.sciencedirect.com/science/article/abs/pii/S0164121226000944>
[99] <https://rl-book.com/applications/2020_reinforcement_learningbased_autoscaling_of_workflows_in_the_cloud_a_survey/>
[100] <https://dl.acm.org/doi/10.1145/2950290.2950328>
[101] <https://doi.org/10.1109/tsc.2025.3596887>
[102] <https://www.sciencedirect.com/science/article/abs/pii/S1569190X22001241>
[103] <https://arxiv.org/html/2507.17128>
[104] <https://ink.library.smu.edu.sg/cgi/viewcontent.cgi?article=9964&context=sis_research>
[105] <https://doi.org/10.63282/3050-922x.ijeret-v2i2p110>
[106] <https://doi.org/10.1109/access.2026.3677437>
[107] <https://doi.org/10.62311/nesx/rp-m4-dec-2021>
[108] <https://dl.acm.org/doi/10.1145/3793811.3793826>
[109] <https://doi.org/10.1007/s10586-018-2807-6>
[110] <https://doi.org/10.31548/machinery/4.2025.21>
[111] <https://www.infoq.com/articles/auto-scaling-feedback/>
[112] <https://pure-oai.bham.ac.uk/ws/files/58263478/Chen_et_al_2018_A_survey_and_taxonomy_of_self_aware_ACM_Computing_Surveys.pdf>
[113] <https://www.preprints.org/manuscript/202607.0944>
[114] <https://doi.org/10.1155/2022/3725657>
[115] <https://www.sciencedirect.com/science/article/abs/pii/S0167739X20330879>
[116] <https://dl.acm.org/doi/10.4108/icst.Valuetools.2014.258191>
[117] <http://arxiv.org/abs/1711.08993v1>
[118] <https://www.sigmetrics.org/opentoc/icpe26companiontoc.html>
[119] <https://link.springer.com/article/10.1186/s40537-024-00914-9>
[120] <https://sites.bu.edu/casp/files/2022/05/Wang22NonExpert.pdf>
[121] <https://www.slices-ri.eu/wp-content/uploads/On_the_Automated_Scaling_of_User_Plane_Function_for_5G_An_Experimental_Evaluation.pdf>
[122] <https://iris.univpm.it/bitstream/11566/291301/2/Machine%20Learning-Driven%20Service%20Function%20Chain%20Placement%20and%20Scaling%20in%20MEC-enabled%205G%20Networks.pdf>
[123] <https://doi.org/10.1109/cloud72782.2026.00019>
[124] <https://dl.acm.org/doi/abs/10.1145/2460756.2460758?download=true>
[125] <https://research.vu.nl/ws/portalfiles/portal/365761384/MAPE-K_Based_Guidelines_for_Designing_Reactive_and_Proactive_Self-adaptive_Systems.pdf>
[126] <https://arxiv.org/html/2403.08798v1>
[127] <https://www.sciencedirect.com/science/article/abs/pii/S2214785320394657>
[128] <https://www.acceldata.io/blog/how-agentic-ai-enables-proactive-fixes-instead-of-reactive-responses-in-data-management>
[129] <https://www.usenix.org/system/files/atc23-qiu-haoran.pdf>
[130] <https://www.linkedin.com/posts/haris-berkovac_predictive-auto-scaling-for-aiaas-workloads-activity-7381926113524236288-rPlu>
[131] <https://www.emergentmind.com/topics/proactive-auto-scaling-algorithm>
[132] <https://doi.org/10.3850/978-981-18-5183-4_s28-02-493-cd>
[133] <https://mbrenndoerfer.com/writing/auto-scaling-horizontal-vertical-policies-llm-production>
[134] <https://dl.acm.org/doi/full/10.1145/3603532>
[135] <https://doi.org/10.26599/bdma.2023.9020014>
[136] <https://re.public.polimi.it/bitstream/11311/1261499/2/11311-1261499_Quattrocchi.pdf>
[137] <https://doi.org/10.1145/3626788>
[138] <https://www.geeksforgeeks.org/system-design/what-is-auto-scaling/>
[139] <https://link.springer.com/article/10.1007/s43621-024-00583-x>
[140] <https://arxiv.org/html/2112.10127v1>
[141] <https://doi.org/10.1109/icws53863.2021.00074>
[142] <https://doi.org/10.21203/rs.3.rs-9478960/v1>
[143] <https://arxiv.org/html/2507.17128v1>
[144] <https://doi.org/10.1007/978-3-032-12972-7_8>
[145] <https://doi.org/10.1007/978-3-032-12972-7_10>
[146] <https://par.nsf.gov/servlets/purl/10064358>
[147] <https://www.sciopen.com/article/10.26599/TST.2025.9010102>
[148] <https://doi.org/10.62311/nesx/rp-dec-d2-2024>
[149] <https://ojs.aaai.org/index.php/AAAI/article/view/21509>
[150] <https://arxiv.org/html/2508.12773>
[151] <https://www.nature.com/articles/s41598-026-40777-z>
[152] <https://link.springer.com/article/10.1186/s42162-025-00524-6>
[153] <https://www.iieta.org/download/file/fid/168740>
[154] <https://dl.acm.org/doi/10.1145/3437984.3458831>
[155] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11207725/>
[156] <https://www.usenix.org/system/files/conference/icac14/icac14-paper-gandhi.pdf>
[157] <https://www.mdpi.com/2076-3417/14/2/646>
[158] <https://doi.org/10.1109/access.2024.3435350>
[159] <https://doi.org/10.1145/3583678.3596886>
[160] <https://doi.org/10.1109/ccict65753.2025.00123>
[161] <https://dl.acm.org/doi/10.1007/978-981-97-0989-2_1>
[162] <https://doi.org/10.1109/globecom42002.2020.9322147>
[163] <https://doi.org/10.1109/tcc.2019.2944916>
[164] <https://dl.acm.org/doi/abs/10.1145/3589334.3645330>
[165] <https://dl.acm.org/doi/10.1007/s10723-016-9371-1>
[166] <https://sustainability.hapres.com/htmls/JSR_1564_Detail.html>
[167] <https://sustainability.hapres.com/UpLoad/PdfFile/JSR_1564.pdf>
[168] <https://www.akamai.com/glossary/what-is-horizontal-scaling-vs-vertical-scaling>
[169] <https://www.oracle.com/sa/a/ocom/docs/industries/communications/comm-5g-core-scaling-bb.pdf>
[170] <https://doi.org/10.1016/j.comnet.2026.112454>
[171] <https://www.atscale.com/blog/big-data-challenges-problems-solutions/>
[172] <https://eprints.whiterose.ac.uk/id/eprint/193716/1/CloudAM2022.pdf>
[173] <https://doi.org/10.1016/j.rser.2024.114583>
[174] <https://dl.acm.org/doi/10.1007/s10723-024-09789-9>
[175] <https://www.nvidia.com/en-us/glossary/energy-efficiency/>
[176] <https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.1176.pdf>
[177] <https://doi.org/10.1109/iwqos.2016.7590395>
[178] <https://eprints.whiterose.ac.uk/id/eprint/133235/>
[179] <https://www.comp.nus.edu.sg/~hebs/pub/shangresource16.pdf>
[180] <https://arxiv.org/html/2605.12272v1>
[181] <https://doi.org/10.1109/cluster.2018.00056>
[182] <https://motherduck.com/learn/big-data/>
[183] <https://doi.org/10.1109/access.2019.2923270>
[184] <https://atlarge-research.com/pdfs/graphless-ispdc2019.pdf>
[185] <https://clouds.cis.unimelb.edu.au/papers/AutoScaleWebAppClouds-ACMCS.pdf>
[186] <https://research.spec.org/icpe_proceedings/2022/proceedings/p105.pdf>
[187] <https://doi.org/10.48550/arxiv.1608.04030>
[188] <https://anshul-jindal.me/publication/reactive_autoscaling/reactive_autoscaling.pdf>
[189] <https://www.sciencedirect.com/science/article/abs/pii/S1084804518303102>
[190] <https://www.vldb.org/pvldb/vol16/p3808-yang.pdf>
[191] <https://www.scitepress.org/Papers/2021/104077/104077.pdf>
[192] <https://ar5iv.labs.arxiv.org/html/2009.12922>
