# High-Mix, Low-Volume Manufacturing: Research Development, Core Technologies and Industry Applications, 2000–October 2022

**HMLV research increasingly emphasized adaptive control.** Across the three requested periods, research progressed from simulation, product-family organization and bottleneck-aware scheduling toward integrated optimization and production control, and then toward connected, data-driven decision support. Cellular Manufacturing, Flexible Manufacturing Systems (FMS) and Flow Management address different aspects of production variability; Constant Work-In-Process (CONWIP) and Paired-Cell Overlapping Loops of Cards with Authorization (POLCA) govern how work enters and moves through production. Heuristics, genetic algorithms, linear programming and reinforcement learning provide complementary scheduling approaches, rather than a universal hierarchy of performance.

**Two application groups lead this comparison.** Electronics/electrical-equipment manufacturing and semiconductor manufacturing are the leading application groups on the transparent literature-presence proxy developed below: approximately **40% and 20%**, respectively, of ten named, sector-specific application studies. These calculated proportions measure representation in that comparison, not manufacturing-market shares.

**The report connects development with decisions.** It first explains the three research stages, then compares layout and process technologies, examines CONWIP and POLCA, classifies scheduling algorithms, and analyzes the two application groups. Throughout, the central question is which source of variability each method addresses—and what operating conditions would change the recommendation.

## Where the main HMLV approaches fit

**The approaches solve different problems.** Work-in-process (WIP) means released but unfinished production. A layout determines where resources sit; equipment flexibility determines what they can process; flow management coordinates movement; and release control limits when additional work may enter. Treating these as interchangeable solutions obscures their practical value.

| Operating condition | Candidate approach | Main mechanism | Principal benefit | Main trade-off |
|---|---|---|---|---|
| Recurring families with similar processes | Cellular Manufacturing [1] | Group related work and resources | Shorter travel and simpler coordination | Weaker capacity pooling |
| Changing products within an automation-compatible envelope | FMS [2] | Integrate automated processing, handling and control | Routing and product flexibility | Capital and integration complexity |
| Shared machines and uneven family demand | Flow Management [3] | Coordinate adaptable family flow paths | Better use of shared constraints | Synchronization and buffer decisions |
| Need for a simple system-wide release limit | CONWIP [4] | Return an authorization after completion | Explicit total-WIP control | Limited local workload protection |
| High-variety work moving between cells | POLCA [5] | Authorize work through paired-cell loops | Local capacity-sensitive coordination | More parameters and card management |

**Combinations are often the practical answer.** A factory can organize repeatable operations into cells, retain expensive shared machines outside those cells, use flexible automation where technically appropriate, and coordinate the resulting network with release controls. The decision is therefore not simply “cells or automation or pull.” It concerns how physical organization, processing capability and workload authorization reinforce one another.

## What makes HMLV a distinct production problem?

**Low volume does not mean little activity.** HMLV manufacturing produces many product variants in relatively small quantities, often with different processing sequences, setup requirements and operation times. The 2020 *Processes* paper, *Real-Time Decision-Support System for High-Mix Low-Volume Production Scheduling in Industry 4.0*, identifies these changing product and process characteristics as a central scheduling difficulty. [6]

A 2022 Hungarian pneumatics-factory case illustrates the distinction between small orders and a small production system: 95% of orders contained fewer than 100 pieces, yet more than 1,300 production orders entered production each day. The plant worked with 800 suppliers, more than 32,000 material codes and more than 25,000 standard product codes. [7]

**Variety changes the capacity calculation.** Counting jobs or pieces can be misleading when their work content differs substantially. Two orders containing the same number of units may require different machines, different amounts of skilled labor and very different setup effort. Consequently, a schedule must account for the combination of quantity, routing, processing time, machine eligibility and labor availability, rather than treating every order as an equivalent load.

Chua, Cai and Low’s 2008 study describes this explicitly: jobs followed variable routes through multifunction machines, while skilled workers differed in grade and shift availability. Last-minute urgent orders added another source of disruption. The scheduling problem therefore involved both operations and manpower, not machine sequencing alone. [8]

**The performance objectives can conflict.** High utilization, short lead time and reliable delivery are all desirable, but a policy that maximizes one can weaken another. Large batches may reduce changeovers while delaying other orders. Releasing more work may keep a machine occupied while increasing queues elsewhere. Holding more material may protect customer service while tying up capital.

The 2022 delivery-performance study places these conflicts at the center of daily HMLV management and adds supplier unreliability as an external complication. Its proposed response combines manufacturing simulation with machine learning to support lot-sizing and scheduling decisions. [7]

**The metrics require separate interpretation.** Production lead time is the elapsed time between release and completion; makespan is the elapsed time required to complete a specified set of jobs; on-time delivery measures conformance to a stated delivery date; and utilization measures resource occupancy. A shorter algorithm runtime is a fifth, computational measure. Improvements in one should not automatically be translated into improvements in the others.

**Analyst judgment: manage workload, not variety alone.** Product variety becomes operationally difficult through its effects on setups, routing, work content, resource contention and uncertainty. The strongest HMLV methods make those effects manageable without removing the customization that gives the manufacturer its market position.

## Research hotspots across the three development stages

**The stages represent accumulating capabilities.** Early flow-control questions remained relevant after digital technologies emerged. Likewise, later optimization methods did not replace product-family formation or careful layout design. The development pattern is best understood as successive additions to the ability to represent, coordinate and adapt production.

| Research stage | Core topics | Representative keywords | Main development |
|---|---|---|---|
| 2000–2008 | Material release, family organization, layout and dynamic scheduling | Simulation; bottleneck; Group Technology; levelling; flow paths | Adapt flow principles to variable-routing production |
| 2009–2016 | Product-mix optimization and integrated production control | Genetic algorithms; particle swarm; CONWIP; POLCA; workload; maintenance | Coordinate decisions across resources and control layers |
| 2017–October 2022 | Connected decision support and disturbance response | Industry 4.0; real-time data; machine learning; digital models; reinforcement learning | Link changing shop conditions to adaptive decisions |

The early-stage themes are illustrated by Gilland’s release-control simulation, Birkmann and Deuse’s family-based levelling, and the 2008 flow-path and manpower-scheduling studies. [9][10][3]

The middle and recent themes are anchored by layered product-mix optimization, integrated lean control, comparative release-control studies, and the 2020–2022 decision-support literature. [11][12][6][7]

### 2000–2008: Representing variety and establishing controllable flow

**Early work made variability explicit.** The principal research questions concerned how to release material, identify constraints, form useful product families and schedule jobs through changing resource combinations. Simulation was important because static descriptions of capacity could not adequately represent queues, interactions and changing bottlenecks.

Gilland’s 2002 study modeled a manufacturing cell patterned after an Intel microprocessor assembly-and-test facility. It compared material-release procedures under single- and multiple-bottleneck conditions, seeking the greatest output rate for a given WIP level. New products, increasing variety and process changes were the sources of uncertainty motivating dynamic management. [9]

**Family repetition replaced individual-product repetition.** Birkmann and Deuse’s 2007 research examined production levelling, or *Heijunka*, in low-volume, high-mix job-lot production. Conventional levelling relies on recurring production and inventory that absorbs demand variation. HMLV complicates this because the number of variants is large and individual products repeat infrequently.

Their response was Group Technology: classify products with similar process requirements into families, allocate production slots to those families, and manufacture the subset actually required by current orders. This preserves some regularity in capacity demand without requiring every individual variant to be produced repeatedly. [10]

**The inventory implication was important.** A finished-goods supermarket for every customized product would multiply stock across a large variant population. Birkmann and Deuse therefore discussed the possibility of buffering standardized components instead, where product modularity allowed it. The mechanism was to locate repeatability at a common process or component level, rather than assume repeatability at the finished-product level.

This distinction remains useful: family-based levelling is not the same as producing unwanted customized products to stock. Its feasibility depends on genuine commonality in processes, components or setups. Where that commonality is weak, the benefits of levelling diminish. [10]

**Layout research challenged complete cellular conversion.** Khaewsukkho’s 2008 dissertation compared functional layouts, which group similar machines, with cellular layouts, which group resources around product families. Functional layouts offered flexibility and machine utilization but incurred long lead times, substantial WIP and complicated scheduling. Cells improved flow and quality control but introduced underutilization and reconfiguration risks.

The dissertation proposed Modular Layout and Hybrid Flowshop Layout alternatives. The former decomposed a complex material-flow network into modules; the latter sought a more flowline-like network while preserving useful job-shop characteristics. This was an early recognition that HMLV needs combinations of layout principles rather than automatic conversion to dedicated cells. [1]

**Flow paths extended the cellular idea.** Guan and colleagues’ 2008 framework proposed adaptable virtual production lines for product families. Unlike a permanently dedicated physical line, a flow path could be planned around shared resources and changing demand. Control policies based on the Theory of Constraints (TOC) and Drum-Buffer-Rope (DBR) were selected according to family variety and demand scale. [13]

Peng and colleagues complemented this operating concept with mathematical programming for flow-path design. Their objectives were to maximize throughput over a defined planning period and minimize the number of machines shared among product families. The research thus connected physical resource sharing with the coordination burden it creates. [3]

**Dynamic scheduling was already a practical concern.** Chua, Cai and Low reported that precision-engineering companies they visited in Singapore relied predominantly on Microsoft Excel for planning and scheduling. Reported problems included unrealistic delivery commitments, suboptimal machine and manpower use, and unacceptable order cycle time. Their proposed heuristics and optimization system targeted urgent orders and unplanned production events. [8]

The early research agenda was therefore not restricted to stable, offline optimization. It already recognized disturbances, multiple resources and the need for rapid response; later digital methods expanded the tools available to address those problems.

**Representative early keywords.** Simulation, material release, bottleneck management, constraint scheduling, Group Technology, product families, levelling, cellular manufacturing, modular layout, flow-path management, dynamic scheduling and manpower allocation capture the main documented lines of work.

**Stage judgment.** During 2000–2008, the central achievement was to make HMLV flow more structured without assuming that every product followed a repetitive mass-production route.

### 2009–2016: Integrating optimization, workload control and resource performance

**Product-mix optimization became more layered.** Neoh, Morad, Lim and Abdul Aziz’s study, published online in 2009 and in a 2010 journal issue, addressed the conversion-time and efficiency penalties caused by frequent changeovers. Its Layered-Encoding Cascade Optimization (LECO) approach used Genetic Algorithms (GA) and Particle Swarm Optimization (PSO) at different decision layers.

Using hypothetical and real manufacturing-plant datasets, the study reported that appropriate combinations could produce high-quality product-mix plans with low conversion time, high productivity and high equipment efficiency. The important development was not simply the adoption of another search algorithm: it was the decomposition and coordination of related decisions. [11]

**Integrated control linked several lean principles.** Slomp, Bokhorst and Germs’ 2009 implementation combined production levelling, CONWIP, First-In-First-Out (FIFO) flow and takt time in a low-volume, high-variety make-to-order job shop. The environment was constrained by both labor and machines, so its control system had to coordinate more than machine queues.

The case reported reduced flow times and an increase in on-time delivery from 55% to 80%. This result supports the value of a coherent control arrangement, rather than attributing all improvement to one card mechanism. [12]

**POLCA developed through implementation and refinement.** Krishnamurthy and Suri’s 2009 work described POLCA as a hybrid push-pull strategy for high-variety or custom-engineered products and discussed factory implementations in the United States and Canada. Its appeal was the ability to coordinate work without requiring repetitive replenishment of every product number. [14]

POLCA was not invented during this middle stage. Vandaele and colleagues had already published Load-Based POLCA in 2008, linking loop workloads and release authorizations to stochastic resource planning. The middle-period development was the growing emphasis on implementation, control-system fit and comparative evaluation. [5]

**Workload balancing became a coordination problem.** The study *Dynamic decentralised balancing of CONWIP production systems* formulated a nonlinear program for balancing work-in-queue across multiple workstations, product routes and bottlenecks. Part-specific primal-dual algorithms adjusted loading rates using authorization-card delays, without requiring access to complete global system information.

This extended the control question beyond a single fixed WIP cap. It examined how loading rates could respond to the distribution of waiting work and allocate resources reasonably across different routes. [15]

**Resource reliability joined scheduling efficiency.** The in-period literature reviewed in the 2022 delivery-performance paper includes 2015 research on equipment effectiveness in HMLV and a 2016 survey of cyber-physical manufacturing systems. These developments broadened the agenda from sequencing jobs toward understanding actual equipment capability and connecting physical production with information systems. [7]

Maintenance matters because a nominally good schedule can be invalidated by unreliable capacity. Automation and robotics similarly become useful only when their setup, programming, handling and integration requirements fit the product mix. The emerging concept was coordinated flexibility, not automation for its own sake.

**Comparative evidence tested method suitability.** Frazee and Standridge’s 2016 study compared CONWIP and POLCA in an industrial photonics system through discrete-event simulation. It assessed the controls at the same WIP level and considered deterministic and Poisson order arrivals. POLCA could provide lower average lead time in the studied conditions, while performance became equivalent at higher WIP. [16]

This illustrates an important shift in the research question: from asking whether a technique could be applied to HMLV to asking under which system conditions it should be preferred.

**Representative middle-period keywords.** Product-mix planning, genetic algorithms, particle swarm optimization, layered encoding, CONWIP, POLCA, workload balancing, FIFO, takt time, production control, equipment effectiveness, maintenance and cyber-physical integration characterize this stage.

**Stage judgment.** During 2009–2016, HMLV research increasingly connected optimization with the release, workload and resource conditions needed to make optimized plans executable.

### 2017–October 2022: Connecting data, models and adaptive decisions

**The newer emphasis was closed-loop support.** The 2020 *Processes* study placed HMLV scheduling in an Industry 4.0 environment involving sensors, the Internet of Things (IoT), Radio-Frequency Identification (RFID), cloud computing and Enterprise Resource Planning (ERP). Its proposed architecture used current resource information to support optimization, risk evaluation, simulation and production monitoring. [6]

The mechanism is straightforward: production generates information about material, machines and job progress; the decision system uses that information to revise a plan; execution then generates new information. The research contribution lies in connecting these activities reliably enough to support daily decisions.

**Software automation differed from physical robotics.** The same paper proposed Robotic Process Automation (RPA) to collect information and coordinate scheduling tasks. Here, “robotic” refers to software performing repeatable information-processing actions, not necessarily an industrial manipulator handling parts.

Its Multibroker–Genetic Algorithm (MB–GA) model first filtered alternatives using machine-workload and job-cost ratios, then applied genetic search. This is an example of combining decision architecture with an optimization method, rather than treating the algorithm as an isolated scheduling engine. [6]

**Digital manufacturing increased the integration challenge.** The 2022 delivery-performance study described Cyber-Physical Production Systems (CPPS) supported by Enterprise Information Systems (EIS), Manufacturing Execution Systems (MES) and advanced Production Planning and Control (PPC). It emphasized that large datasets do not automatically incorporate the engineering and managerial knowledge embedded in production models.

Its answer was to combine model-driven and data-driven analysis. Discrete-Event Simulation (DES), which represents changes such as operation starts, completions and queue movements, retained the process structure; machine learning helped condense historical demand into useful patterns. [7]

**The Hungarian case demonstrated this combination.** Within the larger factory, the study examined a mini-factory covering four cylinder families and more than 3,000 finished-product codes. Average order quantity was 13 pieces; 97% of orders contained fewer than 50 pieces; and 130 production orders were launched daily.

The researchers represented 235 historical working days as daily demand vectors, then used k-means clustering to identify representative patterns. A 25-cluster configuration provided a practical compromise between compactness and representative behavior for evaluating sequencing, lot-sizing and buffer changes. [7]

**Compression made detailed analysis more usable.** Representing 235 daily demand sets by 25 patterns gives a calculated compression factor of 235 ÷ 25 = 9.4. The study reported that the corresponding simulation effort fell from approximately nine hours to less than one hour.

This was not a claim that all daily demand could be reduced to a permanently fixed set of categories. Rather, it showed how learning could make detailed engineering models more practical for recurring planning decisions. The factory found that changing demand patterns warranted restarting the workflow approximately every three to six months. [7]

**Observed improvements involved a combined program.** The mini-factory’s average WIP fell from 3,000 to 1,000 pieces, a calculated reduction of approximately 66.7%: (3,000 − 1,000) ÷ 3,000. Reported production lead time moved from 2.5–3 days to 1.6–2 days.

These results accompanied changes in operating rules and buffers, while the wider improvement program also included replacing a machining center. The appropriate interpretation is that coordinated structural and operational changes improved performance—not that clustering alone caused every reported gain. [7]

**Reinforcement learning expanded adaptive scheduling research.** Wang, Pan and Wang’s December 2021 review identified 214 Scopus articles under the combined subjects “reinforcement learning” and “shop scheduling,” with rapid growth since 2015. This is evidence of the surrounding shop-scheduling research direction, including methods relevant to HMLV’s dynamic decisions. [17]

Reinforcement Learning (RL) learns decision policies through interactions and rewards, rather than solving every new scheduling situation entirely from scratch. Its attraction is responsiveness to job arrivals, machine failures and changing queues. The key practical question is whether the learned policy remains effective when the operating mix differs from its training experience.

**Lean and human work remained central.** Tomašević and colleagues’ systematic review examined 110 articles across 66 peer-reviewed journals explicitly discussing lean in HMLV. It found a strong practice orientation, relatively little theory development, and insufficient attention to advanced variability management and buffering. [18]

This finding matters because connected equipment does not remove the need to understand flow, work content or appropriate buffers. The recent research agenda expanded the available information and decision tools, while the underlying production-management problems persisted.

**Representative recent keywords.** Industry 4.0, CPPS, MES, real-time resource information, IoT, RFID, digital models, DES, machine learning, demand clustering, risk-aware scheduling, reinforcement learning, buffering and adaptive lot-sizing characterize the recent stage.

**Stage judgment.** During 2017–October 2022, the most consequential development was the integration of data, engineering models and operational decisions—not the replacement of established flow principles by a single intelligent algorithm.

### Why the hotspots shifted

**The operational pressures explain the transition.** Early methods sought useful structure within a highly variable production network. Optimization then addressed the growing interaction among mix, setups and resource allocation. Connected systems subsequently made it possible to observe changing conditions and adapt decisions more frequently.

This is an analyst interpretation of the development pattern, supported by the contrast between the 2008 dynamic-scheduling problem, the 2009/2010 layered product-mix optimizer and the 2022 model-and-data workflow. [8][11][7]

**The implication is cumulative capability building.** A factory with unreliable routing or processing-time data may obtain more value from improving visibility and workload representation than from deploying a more elaborate optimizer. Conversely, a well-instrumented factory with complex shared constraints can benefit from sophisticated models because it has the information needed to use them.

**Cross-stage takeaway.** HMLV development moved from making production understandable, through making decisions coordinated, toward making those decisions responsive to changing conditions.

## Layout and process optimization

**The three technologies operate at different levels.** Cellular Manufacturing simplifies the organization of work; FMS supplies adaptable processing and handling capability; Flow Management coordinates the movement and timing of work across the resulting network. Their benefits depend on how closely those levels match.

### Cellular Manufacturing: organize resources around meaningful families

**The basic principle is process commonality.** Cellular Manufacturing uses Group Technology (GT) to organize products or parts with similar production requirements into families and align resources around them. The useful similarity may concern routing, tooling, work content, material or assembly sequence—not merely product appearance.

The 2022 delivery-performance study describes GT as simplifying, standardizing and harmonizing HMLV processes. It also notes that common features of products, parts, processes, technologies and equipment can all inform family formation. [7]

**Cell design involves several linked decisions.** Family formation identifies what should flow together. Layout determines the arrangement of resources within a cell and the relationship between cells. Group scheduling determines the sequence of family work, while resource allocation determines whether machines and workers can support that sequence.

A cell therefore should not be evaluated solely by its floor plan. A compact arrangement can still perform poorly if its labor assignment, setup policy or shared-resource access is inconsistent with the mix it receives.

**HMLV application starts with actual routings.** Kadam’s 2022 architectural-lighting thesis grouped products by routing and used demand forecasts to select a valuable product family. It then examined build and material commonalities to reduce the analytical complexity of the chosen family.

In that case, commercial product descriptions concealed important manufacturing similarities. The selected family was reorganized into 31 work-content-distinct ordering categories, making it possible to design flow around manufacturing behavior rather than an overwhelming number of commercial permutations. [19]

**Dedicated flow should stop at shared resources.** Kadam combined processes that could be dedicated to the selected family and had compatible operating conditions into a continuous-flow cell. Shared processes remained outside that cell and were coordinated through controlled material flow.

This is a practical HMLV distinction. A machine serving several unrelated families may be more valuable as pooled capacity than as a dedicated asset inside one cell. Forcing it into a cell can improve the appearance of local flow while weakening the overall factory’s flexibility. [19]

**The core benefits concern coordination losses.** Compared with functional layouts, cellular arrangements can shorten material travel, reduce handling and queues, simplify scheduling and improve responsibility for quality. Khaewsukkho’s HMLV dissertation identifies shorter lead times, lower WIP and better quality control as important advantages. [1]

The mechanism is that fewer organizational handoffs and a more coherent route reduce the effort required to coordinate each order. This can be particularly valuable when a large number of small orders would otherwise pass through several independently managed departments.

**The principal trade-off is lost pooling.** A dedicated cell may leave a specialized machine idle while another part of the factory is overloaded. Changing demand can make the original family grouping obsolete, requiring costly reconfiguration. Breakdowns and absenteeism can also have disproportionate effects when a cell depends on a small set of resources. [1]

Modular and hybrid-flow layouts respond by preserving selected shared resources and alternative paths. Khaewsukkho’s work used a cut-tree algorithm for modular layouts and a ratio-cut partitioning heuristic for hybrid-flowshop layouts, alongside mathematical optimization and simulation. These are layout-design algorithms, distinct from shop-floor dispatching rules. [20]

**Selection judgment.** Cellular Manufacturing is most attractive when families have enough recurring process commonality to support coherent flow. Its recommendation weakens when family demand is unstable, equipment is expensive to duplicate, or substantial capacity pooling is essential.

**Cellular Manufacturing takeaway.** Create cells around demonstrable process commonality, while preserving shared capacity wherever dedication would create a larger system-level penalty.

### Flexible Manufacturing Systems: provide adaptable processing capability

**FMS combines processing with coordinated logistics.** Mulc, Ciglar, Staroveški and Klaić’s 2021 chapter defines an FMS as automated process workstations connected by automatic material handling and storage, coordinated through distributed control. The system can adjust product types and quantities as requirements change. [2]

The important distinction is integration. A collection of individually flexible machines is not necessarily a well-functioning FMS if handling, storage, tooling and control cannot support the same product mix.

**HMLV application requires a bounded flexibility envelope.** Product families should be examined for common technological stages, feasible tooling arrangements and compatible handling requirements. Mulc and colleagues use GT to establish a common technological base and standardize procedures, enabling faster preparation for new products.

This does not imply that the system can process every conceivable variant. The useful design objective is sufficient flexibility for the economically important range of products and routing changes. Unlimited flexibility would introduce complexity without a corresponding operating benefit. [2]

**Spatial design must include nonprocessing activities.** The chapter treats production, transport, material handling, storage and ancillary activities as explicit space requirements. It then considers material, energy and information flows, together with machine count, transport arrangements, storage and control.

For HMLV, these decisions are tightly coupled. A new routing option is useful only if the workpiece can reach the alternative station, the required tools and program are ready, and the control system recognizes the operation as eligible. Flexibility in one component can otherwise be neutralized by rigidity elsewhere. [2]

**The core problems are change and coordination.** FMS can address changing product types, quantities and feasible routes while reducing dependence on manual transfers and isolated machine decisions. Automated handling and distributed control can support repeated transitions among product families within the system’s design range.

The corresponding HMLV application method is to define that range, standardize family processes where possible, provide compatible workstation and handling capabilities, and coordinate their use through a common information structure. This is an engineering design application of the FMS principles, rather than a claim that automation alone resolves scheduling.

**Flexibility carries an investment penalty.** Mulc and colleagues report that increasing flexibility raises system complexity, investment cost and the time required to reach full productivity. They identify large capital requirements and slow recovery as constraints on wider application. [2]

The comparison with a dedicated line is therefore two-sided. A dedicated system may achieve greater productivity for a stable narrow mix, while an FMS can preserve usefulness when product types or quantities change. The correct economic comparison includes changeover, handling, integration and future mix—not only nominal machine cycle time.

**Reliability remains part of the design.** Automation can remove some manual variability while introducing dependence on control software, handling equipment and integrated availability. The 2022 HMLV case identifies machine interchangeability, maintenance quality, operator skills and programming capability as factors affecting manufacturing capability. [7]

An FMS recommendation consequently becomes stronger when the plant has compatible products, reliable equipment, maintainable controls and the necessary technical skills. It becomes weaker when utilization is too low to recover the investment or when product changes repeatedly exceed the system’s practical flexibility envelope.

**FMS takeaway.** Invest in integrated flexibility that matches the expected mix; do not confuse the broadest technical capability with the best production economics.

### Flow Management: coordinate movement through a variable network

**Flow Management does not require a fixed line.** Guan and colleagues’ 2008 framework explicitly addressed the difficulty of applying conventional, high-volume flow manufacturing to HMLV. It proposed dynamically formed virtual flow paths corresponding to product families, with different constraint-management policies for different variety and demand conditions. [13]

This permits a useful middle position between unrestricted job-shop movement and permanently dedicated flow lines. Products can share equipment while their movement is organized through planned family paths.

**Shared machines create the coordination problem.** Peng and colleagues’ mathematical-programming formulation maximized planning-period throughput while minimizing the number of machines shared among families. The trade-off is operationally meaningful: sharing preserves equipment flexibility, but it also couples otherwise separate production flows. [3]

A schedule for one family can delay another when both require the same resource. Consequently, optimizing each family independently may produce conflicting plans. Flow-path design makes those interactions explicit before daily dispatching begins.

**Constraint control provides a timing logic.** In TOC/DBR, the constraint sets the operating pace—the “drum”; a buffer protects it from disruption; and the “rope” coordinates release so upstream work does not expand without regard to downstream capacity. Guan’s framework made this logic path-specific and combined it with group scheduling.

The HMLV complication is that constraints may differ by family or shift as the product mix changes. Bottleneck identification and buffer sizing therefore remain active decisions, rather than permanent assumptions attached to a single machine. [13]

**Family levelling reduces avoidable variation.** Assigning family production slots can reduce erratic setup patterns while retaining order-specific production inside each slot. The purpose is not to erase demand variation but to prevent every individual order from independently resetting the entire production rhythm.

This method works best when families are meaningful in setup and process terms. Birkmann and Deuse also noted the practical difficulty of classifying large variant populations, so family definitions require plausibility checks rather than purely mechanical grouping. [10]

**Lot splitting changes the flow trade-off.** Dividing a customer order into smaller production lots allows downstream processing to begin before the entire order finishes upstream. The 2022 HMLV review identifies lot-splitting and lot-streaming methods as ways to improve makespan, WIP, mean flow time and total cost, subject to capacity and synchronization trade-offs. [7]

Its illustrative sequence shows the mechanism clearly. For orders A = 80, B = 120 and C = 40, a lot size of 40 can produce either the grouped sequence A40, A40, B40, B40, B40, C40 or the cyclic sequence A40, B40, C40, A40, B40, B40. The latter creates more opportunities for overlapping downstream work, but may introduce additional setups.

**Synchronization should target actual dependencies.** Parts that converge at assembly must arrive in a usable relationship, so synchronization points before merge operations can be valuable. Khan and Standridge’s 2019 discussion describes HMLV value-stream methods that place synchronization points before merge activities and split customer orders into suitable production orders. [21]

However, synchronization at every routing step can make the system unnecessarily rigid. The 2022 review reports deterioration when such universal synchronization is imposed. The practical objective is to protect real assembly and capacity dependencies without forcing unrelated work to move in lockstep. [7]

**Different items need different flow connections.** Kadam’s lighting design used FIFO lanes for customized components whose identity was established early, and supermarket pull for standardized mounting kits. This distinction follows from the economics of replenishment: common kits can be stocked and replaced, whereas unique components should follow their specific order sequence. [19]

Takt time and pitch also need adaptation. Takt is the available production time per unit of demand, while pitch is the interval used to communicate and monitor a production increment. Where work content varies greatly, a fixed piece count per interval may be less useful than a controlled amount of work.

**Dynamic pitch controls work rather than pieces.** Kadam proposed scheduling a fixed amount of work into each time interval while allowing the number of fixtures to vary. This accommodates high customization without continuously changing the production target merely because the day’s orders are more labor-intensive.

The mechanism is compatible with a stable capacity budget: the interval remains fixed, but its contents reflect the actual work required. It is therefore a process-control adaptation, not an assumption that every customized item should leave the cell at the same pace. [19]

**Flow Management takeaway.** Organize family paths, shared constraints, buffers and order splitting as one system; smooth flow does not require identical routes or identical work content.

**Additional documented evidence**

**Cellular Manufacturing**

**Principle.** Cellular Manufacturing groups products with similar operation sequences into families and places the required dissimilar machines, equipment, and tooling in cells. It combines job-shop flexibility with flow-shop efficiency, supports small-batch, unit-by-unit production, and—where routing permits—keeps a family within a cell without external departments through sequential, unidirectional, one-piece flow [39][45][51]. A 2000 method formalized three steps: part-family formation; machine assignment/cell formation, balancing bottleneck-machine benefits against inter-cell movement; and intra-cell layout refinement [50]. A second 2000 methodology added product and production-flow analysis, clustering, capacity planning, layout design, and simulation for either converting an existing structure or designing a new project [45].

**HMLV application and problems solved.** HMLV variety, uncertain demand, and many routings create a complex flow network; queue and transport are major lead-time wastes. One cited conventional-job-shop estimate is “up to 95%” of total production time waiting or travelling, not an HMLV-wide rate [39]. The application sequence is to identify product and routing commonality, form cells, allocate capacity, and simulate batch size, sequencing, handling priorities, bottlenecks, and setup [45]. It targets material handling and intercell movement, lead time, WIP, scheduling and production control, setup, throughput, capacity, and bottleneck utilization [39][45]. In the Vakharia dataset, normalized inter-module flow fell from 2,472 in the functional layout to 498 in the modular layout—a reported 79.8% reduction—after grouping high-traffic machines and buying two additional machines; CPLEX took 12,786 seconds [39]. In a 2022 sportswear case, three cells were formed from product-family sequences. Across 100 simulations of 300 hours plus a 10-hour warm-up, average flow time fell from 5,575.52 to 2,706.13 seconds (−51.46%), setup time fell 50.65%, and throughput rose from 133.38 to 1,603.93 units (+1,102.52%); idle time rose 285.1% and the bottleneck shifted to cutting and printing [51]. These are case results, not general guarantees.

**Limits and decision condition.** Cells are family-specific and need sufficient volume; changing mix, order quantities, demand, shared machines, exceptional parts, and bottlenecks make fully disjoint cells rare. Duplication is costly, so complete conversion from a functional HMLV job shop may be ill-advised [39][45]. A small HMLV facility may have hundreds to thousands of routings, each with at least ten operations and setups, making complete setup- and processing-time data expensive to collect [39]. Module size is consequential: an oversized module approaches a functional layout, whereas an undersized module increases inter-module flow and machine duplication; detailed modular-layout design is NP-complete and data-intensive [39]. Cell formation also faces space constraints and lacks clear procedure-selection guidance. Cited research covers alternative routes, lot splitting, unreliable machines, WIP, demand changes, and flexible reconfiguration, while sustainability and supply-chain integration remain under-studied [45][52]. The practical choice therefore depends on routing commonality, demand stability, capacity and duplication cost, and data availability.

**Evidence boundary.** In this source group, FMS is only reported as associated with Cellular Manufacturing; its own principle and HMLV application method are not established [51], and no like-for-like Flow Management comparison is supported [52]. The 2000 source mentions arbitrary clustering for machine-part grouping but names no model and assigns no required algorithm category, so it is context rather than a filled scheduling-table row [45]. A 2024 HMLV experiment is post-cutoff methodological context only: a three-machine cell reported a 109.51-hour critical path, 34.19% uptime, and a 0.06 scrap rate versus 0.07 at baseline; cellular processing was more effective for cost, standardization, and throughput than a single multipurpose-machine alternative, which increased lead time and cost . It is excluded from the 2000–October 2022 historical evidence.

**Cellular Manufacturing: principle and HMLV evidence**

Cellular Manufacturing (CM) groups part families with similar, recurrent work on dedicated clusters of dissimilar machines; the machine–part incidence matrix is the base, while sequence, volume and setup data improve formation [46][53]. It organizes people, tools, buffers and handling around a family to gain economies of scope [54].

Cellular Manufacturing part families→cells; HMLV cells cut handling/WIP/setup/LT [55]; limits PLC/demand/training/ctrl [55]. FMS reconfig [40]; Lean unclear [56];CM00[57];GA01[58].

Cellular Manufacturing (CM) groups similar parts/routings around dissimilar machines in cells, combining job-shop flexibility with product flow [59]. In HMLV, product-family/routing clustering, hybrid cells and flow-path design share machinery; mathematical programming, genetic algorithms and LP–particle-swarm hybrids optimize formation, layout and routes [34][60]. One facility clustered >5,000 parts/38 work centres into five cells, reporting >50% less travel; a three-machine HMLV cell reduced cost, standardized operations and increased throughput [42][35]. CM addresses movement, routing variability, WIP/lead time, throughput, cost and quality [59][28].

**Flexible Manufacturing Systems (FMS)**

FMS is a highly automated group-technology cell: numerically controlled workstations connect through automated handling and storage under distributed computer control; it processes varied part styles simultaneously and changes their mix and quantities with demand [48]. In HMLV, operations are grouped for part families in in-line, loop, ladder, open-field or robot-centred layouts, with software coordinating routing, scheduling, tools, transport and inspection [48][63]. Aerospace low-volume/high-variety components and medical-device small batches are documented contexts [63]. A simulation-based HMLV design separates design, planning, scheduling and control, reads shop-floor status and periodically reschedules after disturbances [41].

FMS addresses part-to-machine assignment, operation sequencing and material movement under capacity, tooling and due-date constraints; dynamic scheduling responds to breakdowns, rush orders and customer changes [63]. Reported benefits include higher utilization, lower WIP and lead time, and daily schedule adjustment for immediate orders [48]. Limits include combinatorial scheduling, capacity imbalance when cell specialization misses the product mix, high capital and skilled-labour requirements, software/tooling costs, and a flexibility–specialization trade-off; software development is estimated at **12–20% of total expense** [48][63]. The HMLV simulation assumed only a few disturbances and omitted queue-length, utilization and operation-completion monitoring; its recorded **5–7% performance-limit** figure has no defined metric and remains unclear [41]. An FMS treatment also describes Ant Colony Optimization for AGV routing and scheduling toward overall layout optimization [62].

An HMLV layout simulation tested five layouts, four factors—layout, batch size, machine capacity and move time—and batch sizes of **5–80**; with no capacity constraint, Cellular Manufacturing produced the lowest completion time and WIP, including **3.62 hours per part** and **2.11 parts of average WIP** at batch size 5 [44]. In a separate aerospace tube-assembly simulation over **60 days**, with **20 replications** and a **95% confidence interval**, family clustering, time-series forecasting, selective MTO-to-MTS conversion and partial pre-production reduced changeover from **148 to 75 hours** and time in system from **482 to 333 hours**, while throughput quantity rose from **370 to 532** [41]. PFAST combined a design-skeleton approach with a genetic algorithm for heuristic functional-layout design without guaranteeing optimality [44]. The same HMLV evidence reports that incomplete cells and random machine-level operations make POLCA difficult: 12 machines imply **66 pairs** or **six POLCA cards** if arranged as four cells, versus **16 cards** in a four-stage hybrid awareness design [44]. These remain case and simulation findings, not general causal estimates. A separate page lists six FMS layouts by adding a carousel layout to the five-layout list; the discrepancy is retained [47]. HMLV flexible-job-shop evidence published in **2023** is outside the historical cutoff and is not used as stage evidence [61].

**Flow Management: evidence boundary**

Material Flow Management is an economic method for analysing and reforming production and waste through material flows, using material-flow analysis, Sankey diagrams, industrial ecology and circular-economy concepts [64]. The available evidence does not establish an HMLV-specific application, stage, scheduling mechanism, algorithm, industry share or countermeasure; it reports general waste/resource-flow uses and a tension between MFM and sustainability [64]. Its status is therefore **partially supported/unclear for HMLV**, not a demonstrated HMLV performance technology. Cellular Manufacturing, FMS and Flow Management are complementary in scope, not interchangeable [44][48][64].

**Lean manufacturing: evidence status**

Limits are material: historical effectiveness was 200–20,000 parts/year, not small batches; FMS layout is NP-hard, and AI design sought short, bottleneck-free routes but used transport cost only [69]. Cost, correlated arrivals, machine count, pallets/AGVs, and robot/tool/material interactions constrain fit [68][69][70][71]. A 2022 FMS study cites 284 flexibility articles to 2017; its FMC ANOVA assigns 46% to machine-sequence flexibility. FIFO, one-transporter simulation (capacity: one product) found over 30% makespan gain and 40% shorter travel as flexibility increased—case-specific [70][71].

Post-cutoff 2023 FMS sources are context only; one review covers 1,096 records from 2001–2021 and quantitative, scheduling, cell-formation, and Industry 4.0 themes [65][66]. The 2022 SME review reports small/diverse batches and resource limits but no stage keywords or direct Cellular Manufacturing evidence [67]. Lean supports HMLV with flexibility [31]. Low-volume/low-variety models use mixed-integer/continuous-time shared-resource heuristics, not HMLV evidence [72].

FMS: computer-controlled CNC/AGVs under central control provide machine/routing flexibility [76][78]. HMLV use: programmable machines, scheduling, alternative routing and changeover for varied parts/small batches; problems include scheduling/loading, transport and WIP [33][73][76]. Models: 2006 hybrid GA for machine–AGV, MILP for transport–production (80/82 optimal), and 2020 Petri-net/DRL FMS [73][74]. Dynamic-rescheduling use filtered-beam and GA match-up [75]. Limits: transport, capital, skills/planning; HMLV evidence is context only [73][77].

Flexible Manufacturing Systems (FMS) use computer-controlled machines and automated material delivery; after their capital-intensive setup, little operator intervention is needed [43]. In HMLV-like use, FMS makes varied parts in small capacities with workstations, AGVs and automated storage/retrieval; job-shop FMS can change resources and capacity, while ICT traces products and resources in real time [80][81]. Flexible routing jointly assigns machines and operation order; an SDM case reported up to 80% lower queuing time when ordering was delayed until shop entry (observed, 2003) [79]. FMS therefore addresses HMLV routing, machine assignment, sequencing, throughput, downtime and material movement. Its trade-offs are capital intensity, predefined flexibility, uncertain arrivals, schedule “nervousness” under new jobs, downtime or variability, and static models that omit failures or transport disturbances [43][79][80]. Aerospace assembly further illustrates certification-specific labor, scarce work areas, precedence/nonparallel constraints and time lags [49].

Flow Management is a process-centred mechanism using iterative look-ahead planning, shared digital information and upstream mistake-proofing [82]. In engineer-to-order (ETO) material flow, it links design, schedule, production and transport through BIM/RFID, a common database and linked modules; short iterations monitor design-for-production and transport-freeze milestones [82]. It targets late design changes, incomplete information, coordination failures, wrong deliveries, delays and rework. A 1,000-run Monte Carlo example reported an 18% reduction in time to handle required changes, but the example was fictive; a separate BIM/RFID implementation reported about 32% higher time efficiency than traditional planning [82]. The construction-specific association with over 50% delays and cost overruns is not a general factory estimate [82]. Data sharing and defined ownership are prerequisites; FMS changes resource/routing capability, whereas Flow Management coordinates information/material movement [82].

Lean manufacturing is supported as a related concept, not a substitute for the three required technologies: it reduces waste/resources, whereas HMLV emphasizes customer-set batches, make-to-order customization and delivery speed; excessive standardization can hinder change [37]. In an HMLV case, parts sharing/standardization, DFM/DFA, guided monitoring, training and pictorial instructions reduced changeover, error and lead-time pressures, but standardization reduced autonomy and increased workload; among eight interviewees, 75% reported instruction/part problems, 50% no formal training, and 25% unstandardized similar parts [37].

**Flow Management**

**Lean manufacturing (discovered concept)**

Lean manufacturing is a supported HMLV process-optimization concept, but requires adaptation to high variety, small batches, stochastic demand, different sequences/routings, irregular cycles and frequent changeovers [29][36][38]. Its principle is continuous-improvement removal of non-value-added activity; its pillars are JIT and Jidoka, with JIT using Kanban, standard work/instructions, SMED and production flow [83]. Lean philosophy and total quality management are reported as necessary for efficient machine and labour use in real-time HMLV scheduling [32]; HMLV practice also emphasizes agility, flexible workflows, regular changeovers and skilled operators rather than mass-production repetition [30].

## Dynamic job release: CONWIP and POLCA

**Release is different from dispatching.** Release determines whether an order is allowed to enter a controlled production area. Dispatching determines which eligible job a resource processes next. A release method can limit congestion without identifying the best next job, while a dispatching algorithm can sequence work efficiently without preventing excessive release.

The difference matters because urgent-order handling, due-date performance and workload balance depend on both decisions. CONWIP and POLCA are therefore control architectures within which scheduling rules still operate.

### CONWIP: control the total amount of released work

**A returned authorization permits another release.** In the basic CONWIP configuration, a fixed number of job-anonymous cards limits work in the production line or controlled area. A job starts when an authorization is available; completion at the last station returns the card to the beginning, permitting another job to enter.

Thürer, Stevenson and Protzman’s 2016 review emphasizes that a CONWIP card authorizes “a job,” not a particular product. Product selection is therefore decided at the entry point rather than encoded in the card itself. [4]

**The limit is a ceiling, not a guarantee.** A system with ten authorizations need not contain ten active jobs at every instant: shortages, maintenance or insufficient demand can leave cards unused. “Constant” describes the control parameter, not perfectly constant observed inventory.

For HMLV, job anonymity is useful because it avoids maintaining a separate replenishment loop for every product number. However, the entry rule must still decide which waiting order deserves the next authorization.

**The main advantage is control simplicity.** CONWIP gives planners a visible total-WIP limit and a clear completion-to-release feedback mechanism. It can reduce uncontrolled queue growth while allowing the mix of released jobs to change.

This simplicity also makes experimentation easier. A planner can examine how alternative WIP limits affect throughput and lead time, instead of simultaneously configuring many product-specific loops. The Grand Rapids Chair case used aggregate simulation to investigate such a parameter. [21]

**HMLV makes equal job counts unequal loads.** A small quick order and a long complex order may each consume one authorization while imposing very different resource demands. A global cap consequently does not directly protect a particular milling station, assembly team or shared oven from overload.

The standard single-line configuration also has important structural assumptions. Thürer and colleagues describe its fit in terms of constant routings, similar processing times and a limited job set—conditions that differ from an unrestricted variable-routing HMLV job shop. [4]

**Adaptation can preserve the useful principle.** Product-family control, hybrid local inventory limits and workload-sensitive extensions can make system-wide WIP control more relevant to HMLV. Slomp and colleagues’ case combined CONWIP with levelling, FIFO and takt rather than applying the card limit in isolation. [12]

The decentralized balancing study offers a more analytical adaptation: loading rates respond to queue-related authorization delays across different routes. This shows that the limitations of basic CONWIP should motivate an appropriate configuration, rather than a blanket conclusion that total-WIP control has no place in HMLV. [15]

**Parameter selection requires dynamic analysis.** Khan and Standridge state that Value Stream Mapping (VSM), which depicts material and information flow, is insufficient by itself to establish the CONWIP limit. Their case aggregated more than 100 product types and examined parameter effects through simulation.

A limit that is too tight can starve the constraint; a loose limit can preserve throughput while allowing avoidable waiting. The useful operating point depends on routing, mix, processing variability and the location of congestion. [21]

**CONWIP judgment.** CONWIP is a strong initial candidate when a total-WIP ceiling addresses the main problem and routes can be organized into sufficiently coherent streams. Its recommendation weakens when local overload or wide workload differences dominate performance.

### POLCA: coordinate capacity between cell pairs

**POLCA authorizes capacity, not product replenishment.** POLCA uses paired-cell control loops to govern work between cells. A higher-level plan establishes when an order should be considered, while loop-card availability indicates whether the relevant downstream cell pair can accept more work.

Vandaele and colleagues identify the system as particularly suitable for highly variable demand, broad product variety and small-batch or one-of-a-kind production. Its logic is therefore directed at the capacity consequences of variety, rather than stocking a fixed quantity of every variant. [5]

**Overlapping loops provide local coordination.** Consider a route A → B → C. An A–B authorization governs work through that cell pair, while a B–C authorization governs the next pair. Cell B participates in both loops, creating the overlap through which successive capacity relationships are coordinated.

The practical distinction from CONWIP is the location of control. CONWIP primarily limits the total unfinished work in its controlled area; POLCA can restrict work in particular cell-to-cell relationships. Krishnamurthy and Suri describe this as a hybrid push-pull strategy designed to overcome conventional pull-system difficulties in high-variety custom production. [14]

**Local protection is the main advantage.** A factory can have an acceptable total WIP level while too much of that work concentrates around one constrained area. Pair-specific authorizations can discourage further loading of that area while allowing work on other routes to proceed.

This mechanism explains why POLCA may outperform a global cap when localized queues are a major source of delay. It also explains why its advantage may shrink when such queues do not arise.

**Workload-based cards address unequal job sizes.** Vandaele and colleagues’ Load-Based POLCA linked permitted loop workloads and release authorizations to Advanced Resources Planning (ARP), incorporating stochastic production behavior. The framework also supported lot-size fine-tuning and was discussed through an electronic implementation at Spicer Off-Highway Products Division. [5]

A workload-based limit is especially relevant when counting jobs poorly represents capacity demand. Its additional requirement is credible workload information: the release calculation becomes more informative, but also more dependent on processing-time and routing estimates.

**Original POLCA is decentralized.** Fernandes and colleagues explain that original POLCA has no central pre-shop release pool. Orders are forwarded to gateway manufacturing cells, where they wait in cell-specific release lists.

Their 2020 extension added loops between a centralized pre-shop pool and each gateway cell. A job first acquired a release card and then a POLCA card; the release card limited either the number of jobs or workload admitted to the gateway. [22]

**The additional control increases configuration effort.** Pair definitions, card quantities, workload units, authorization priorities and circulation discipline must work together. A centralized extension adds another decision layer and another set of parameters.

This is justified when the added control addresses a genuine operational problem. It is less attractive when a simpler global cap already provides acceptable flow and the local workload pattern is benign.

**POLCA judgment.** POLCA is the stronger candidate when cell-to-cell capacity protection is operationally important. Load-based or centralized versions become attractive when unequal job workloads or the need for a global release view materially affect performance.

### What the comparative evidence actually shows

**The results depend on the criterion.** The literature reports benefits for both control approaches, but the studies examine different production structures, configurations and performance measures.

| Study or configuration | Comparison basis | Reported result | Interpretation |
|---|---|---|---|
| Slomp et al., 2009 | Integrated levelling–CONWIP implementation | On-time delivery: 55% → 80% | Benefit of a combined control system |
| Frazee and Standridge, 2016 | POLCA versus CONWIP at equal WIP | POLCA could lower average lead time | Local queue control mattered |
| Khan and Standridge, 2019 | Aggregate CONWIP parameter analysis | Parameter 50 matched unlimited-WIP throughput | Unrestricted release was unnecessary |
| Centralized unit-based POLCA, 2020 | Extension versus original control | Throughput time improved 3.3%–5.4% | Pre-shop release added value |
| Load-based POLCA quantum, 2020 | Load-based versus unit-based accounting | Throughput time improved 3.5%–9.0% | Workload representation affected results |

Sources: Integrated lean control [12], equal-WIP comparison [16], aggregate CONWIP analysis [21], and centralized POLCA experiments [22].

**The photonics result supports a mechanism.** Frazee and Standridge’s primary 2016 report found that POLCA could reduce average lead time at a given WIP level, with equivalent performance at higher WIP. Its interpretation was that POLCA restricted inventory in specific areas, whereas CONWIP restricted only the system total.

That is more informative than declaring POLCA generally superior. The source of advantage was the spatial distribution of work, so the result is relevant when localized accumulation is the principal delay mechanism. [16]

**A later account reports a counterpoint.** Khan and Standridge’s 2019 discussion describes a nonaggregate comparison in which CONWIP achieved maximum throughput at a lower maximum WIP than POLCA. It attributes the absence of problematic local accumulation to batch operations and relatively low utilization in manual operations.

The direct equal-WIP lead-time result and the later throughput/WIP summary concern different reported criteria and should not be collapsed into a single universal ranking. They identify conditions under which the extra local protection may or may not provide value. [21]

**The Grand Rapids setting required calibration.** Khan and Standridge also reported a CONWIP configuration with parameter 58 associated with approximately 20% shorter lead time in their parameter analysis. This should be read together with the throughput result at parameter 50: a useful control parameter depends on the complete operating objective, not simply the smallest numerical cap.

Their aggregate model could generate randomized routes not corresponding to an actual product, potentially raising estimated waiting time. They therefore interpreted its lead-time results as an upper-bound approximation. [21]

**Central release improved tardiness as well.** Fernandes and colleagues simulated a six-cell general flow shop at 90% utilization, using 100 replications per scenario. Under the Modified Capacity Slack (MODCS) card-acquisition rule, centralized unit-based release improved total throughput time by 3.3%–5.4% and the percentage-tardy measure by 23.1%–53.3%.

Comparing load-based with unit-based quantum accounting produced throughput-time improvements of 3.5%–9.0% and percentage-tardy improvements of 20.4%–44.5%. These are separate comparisons, not additive gains. [22]

**The dispatching rule still mattered.** The same study compared First-Come-First-Served (FCFS), Earliest Authorization Date (EAD) and MODCS acquisition rules. MODCS performed substantially better on percentage tardy, while differences in total throughput time were less pronounced.

Thus, selecting POLCA does not finish the scheduling design. The priority rule governing access to its cards can materially affect due-date performance. [22]

**Release-control takeaway.** Prefer CONWIP for a sufficiently effective global ceiling and POLCA for valuable local capacity protection; determine the choice using the same demand pattern, workload definition and performance objective.

## Classification and selection of HMLV scheduling algorithms

**The categories describe different solution strategies.** Heuristics construct decisions using rules or problem-specific logic; genetic algorithms search populations of candidate solutions; linear and mixed-integer programming formulate explicit objectives and constraints; reinforcement learning learns a policy for repeated decisions.

Genetic algorithms belong to the broader metaheuristic family, so these categories are not mathematically exclusive. Wang, Pan and Wang’s review distinguishes exact methods, heuristics and metaheuristics, while its RL classification adds a learning-based perspective. [17]

### Algorithm classification table

**The table links models to objectives.** FCFS and Shortest Processing Time First (SPTF) are dispatching rules; LECO and MB–GA are hybrid optimization models. Mixed-Integer Linear Programming (MILP) extends Linear Programming (LP) with discrete assignment or sequencing decisions.

| Algorithm Category | Specific Algorithm Name/Model | Main Application Objective |
|---|---|---|
| Heuristic Algorithms | FCFS; SPTF [23] | Rapid job dispatching and online rescheduling |
| Heuristic Algorithms | Palmer heuristic within DES–GA [24] | Improve flow-shop sequence search |
| Genetic Algorithms | GA and LECO GA–PSO models [11] | Optimize product mix, conversion time and equipment use |
| Genetic Algorithms | Multibroker–Genetic Algorithm, MB–GA [6] | Minimize makespan using workload and cost filtering |
| Linear Programming | Improved PCB MILP Model 2 [25] | Minimize pressing-process makespan |
| Linear Programming | Maintenance and revenue-levelling assignment models [19] | Schedule maintenance and balance daily financial output |
| Reinforcement Learning | Multi-agent SARSA [17] | Learn decisions for dynamic multisite scheduling |
| Reinforcement Learning | Q-learning; Deep Q-Networks [17] | Learn state-dependent scheduling action values |
| Reinforcement Learning | REINFORCE; PPO; TRPO [17] | Learn scheduling policies directly |
| Reinforcement Learning | RL-B; RL-C online schedulers [23] | Respond to urgent jobs and resource disturbances |

### Heuristics: prioritize speed and interpretability

**Simple rules provide useful operating baselines.** FCFS prioritizes arrival order, while SPTF prioritizes shorter processing requirements. Their attractions are low decision effort and transparent logic. Their limitations arise when that single priority conflicts with due dates, setups, downstream constraints or the needs of long jobs.

The 2022 online job-shop comparison explicitly classified SPTF and FCFS as rule-based simulation methods and compared them with GA and RL approaches. This gives them an important role as understandable baselines, not merely simplistic alternatives to be discarded. [23]

**Problem-specific heuristics exploit structure.** A useful heuristic can encode the fact that certain families share setups, certain operations converge at assembly, or certain resources are scarce. The benefit is that the method spends little effort exploring obviously unsuitable decisions.

The July 2022 low-volume, high-mix flow-shop assembly record combined DES with GA and used a Palmer heuristic to improve the search. Its operating problem involved variable processing times, line imbalance and frequent changeovers. [24]

**Heuristic selection follows the dominant loss.** A short-processing-time rule may be sensible when queue clearance is the principal aim. A family-based rule may be better when changeovers dominate. A due-date or capacity-slack rule becomes more relevant when lateness is the main business concern.

The condition that would change the choice is not simply a larger job count. It is a change in which operational penalty matters most and whether the rule represents that penalty adequately.

### Genetic algorithms: search complex combinations

**GA searches beyond a single priority rule.** A genetic algorithm encodes candidate schedules or plans, evaluates their fitness, and uses selection, crossover and mutation to develop new candidates. This permits exploration of combinations involving assignments, sequences and product mix.

For HMLV, the value lies in handling interactions that are difficult to express through one dispatching rule. The LECO study used GA and PSO at different layers precisely because product-mix decisions had several connected components. [11]

**The encoding determines practical usefulness.** A candidate must represent an executable production plan: eligible machines, operation order, available resources and required demand must be respected. A sophisticated search with a poor representation can repeatedly generate infeasible or operationally irrelevant alternatives.

LECO’s contribution was therefore both algorithmic and architectural. Its layers structured the planning problem, while the optimizers searched within that structure. The resulting objective was improved conversion time, productivity and equipment use—not an abstract claim that GA is always superior.

**Hybrid filtering can reduce unsuitable choices.** The 2020 MB–GA proposal filtered alternatives using machine-workload and job-cost ratios before genetic optimization. Its architecture connected ERP information, risk analysis, simulation and monitoring, allowing optimization to consider current production conditions. [6]

A practical implication is that some performance gains may come from better inputs and better restriction of the search space, rather than the evolutionary search alone. This also makes system integration part of algorithm selection.

**Search time can conflict with response time.** In the 2022 job-shop experiment, involving about 100 generated orders and 152 operations, GA produced strong schedules but required a longer iterative computation. When ten urgent orders were introduced, online methods handled the events with little additional computation or makespan increase in that experiment. [23]

For a planner, this creates a useful division of labor: an iterative optimizer can support a planning window, while a faster rule or policy handles immediate disturbances. The recommendation changes when the available decision time becomes shorter than the search effort needed for a useful improvement.

**Suitability scores are not operating gains.** The MB–GA paper used the Analytic Hierarchy Process (AHP) to compare method suitability against requirements. Its 83.42% score measures weighted suitability in that assessment, not an 83.42% improvement in production performance.

This distinction matters because an architecture can be well matched to digital-manufacturing requirements without having demonstrated the same advantage on every scheduling instance. [6]

### Linear programming: express constraints explicitly

**MILP is valuable when feasibility is exact.** LP represents decisions through a linear objective and constraints; MILP adds integer or binary variables for decisions such as machine assignment, job precedence or order placement. This is well suited to production settings where compatibility and shared-resource restrictions must be represented precisely.

Laisupannawong, Intiyot and Jeenanunta’s 2021 PCB pressing study used an improved MILP formulation, Model 2, to minimize makespan under machine-cycle, material-compatibility and shared-oven constraints. [25]

**The distinction from heuristic search is assurance.** An exact formulation can establish optimality for the modeled problem when solved to completion. A fast feasible solution may also be useful before proof of optimality, but the result must be interpreted against its stopping condition and model assumptions.

The computational difficulty grows with the number of discrete combinations. Wang, Pan and Wang note the difficulty exact algorithms face on large-scale, computationally hard scheduling problems. The practical choice is therefore between the value of explicit constraint fidelity and the time available to solve the instance. [17]

**Planning objectives extend beyond makespan.** Kadam’s thesis formulated maintenance scheduling to minimize cost while respecting technician availability, overtime and maintenance requirements. It also formulated revenue-levelled production scheduling, subject to daily capacity and order-completion requirements.

Although described broadly as linear programming, the supplied formulations include binary and integer assignment variables and are more precisely understood as mixed-integer linear models. This illustrates the importance of classifying a method by its mathematical structure, not only the label in an abstract. [19]

**Model precision does not fix input error.** A mathematically optimal solution can still be operationally weak if its processing times, availability or eligibility data are wrong. The semiconductor example discussed below addresses this issue directly by predicting missing parameters and incorporating forecast uncertainty.

**Linear-programming judgment.** Use LP/MILP when explicit business and resource constraints are central and the instance can be solved within the relevant decision window; reconsider the formulation or combine methods when computation or parameter uncertainty dominates.

### Reinforcement learning: learn a repeatable decision policy

**RL targets sequential adaptation.** A scheduling agent observes a state, chooses an action and receives a reward reflecting the result. Over repeated interaction, it learns which actions tend to produce better outcomes.

Wang, Pan and Wang report that most reviewed RL scheduling methods were model-free, meaning they learned through interaction without requiring an explicit state-transition model. They divided these into value-based and policy-based approaches. [17]

**Value-based methods learn action desirability.** State–Action–Reward–State–Action (SARSA), Q-learning and Deep Q-Networks (DQN) estimate the value of taking particular actions in particular conditions. Policy-based methods, including REINFORCE, Proximal Policy Optimization (PPO) and Trust Region Policy Optimization (TRPO), learn the action policy more directly.

The review noted that policy-based methods were less widely used in scheduling at that time. The distinction is useful because the approaches organize learning differently; it is not a ranking of their suitability for every shop. [17]

**Comparisons should include conventional methods.** The review describes a dynamic multisite scheduling application using multi-agent SARSA, evaluated against GA and mixed-integer linear programming. This is a useful comparison structure: it asks whether learning offers an advantage over both search-based and exact-model approaches.

For HMLV, the attraction is rapid repeated decision-making when jobs arrive or resources change. The corresponding dependency is a training environment that represents the routes, job sizes and disturbances the policy will encounter.

**Training effort differs from operating speed.** In the 2022 RL-B/RL-C study, each model was trained for 300 episodes. RL-B converged near episode 270 and RL-C near episode 170, yielding approximately 37.0% fewer episodes for RL-C: (270 − 170) ÷ 270.

This measures learning convergence in that experiment. It is not a 37% reduction in factory lead time or an automatic equivalent reduction in total implementation effort. [23]

**Adaptability does not remove capacity loss.** The same study showed a scheduler responding to a milling-machine failure by routing later operations to other functioning machines. Waiting and load imbalance nevertheless worsened after the failure.

The implication is important: an adaptive policy can improve the response to a disturbance without restoring the capacity the disturbance removed. An RL recommendation weakens when its training scenarios omit important disruptions or when its reward function does not reflect real delivery and operating priorities. [23]

**Algorithm-selection takeaway.** Choose the method by constraint structure, information quality and decision time: interpretable rules for fast action, genetic search for complex combinations, MILP for explicit feasibility and optimization, and RL for repeated adaptive decisions.

**Additional documented evidence**

| Entity | Algorithm Category | Specific Algorithm Name/Model | Main Application Objective | Specific Algorithm Name/Model | Main Application Objective |
| --- | --- | --- | --- | --- | --- |
| Heuristic Algorithms | The source lists “Tabu Search -Part II” from 1990 and…[120] | The source lists “A new adaptive neural network and…[127] | The documented heuristic work pursues minimizing…[119] | The source lists “A new adaptive neural network and…[127] | The documented heuristic work pursues minimizing…[119] |
| Genetic Algorithms | no evidence found | Local search is rarely used in the reviewed…[188] | no evidence found | Local search is rarely used in the reviewed…[188] | no evidence found |
| Linear Programming | A multi-functional mathematical programming model is…[134] | A multi-functional mathematical programming model is…[134] | A multi-functional mathematical programming model is…[134] | A multi-functional mathematical programming model is…[134] | A multi-functional mathematical programming model is…[134] |
| Reinforcement Learning | no evidence found | Metaheuristic-based DRL models have been developed…[147] | no evidence found | Metaheuristic-based DRL models have been developed…[147] | no evidence found |

The rows move from Heuristic Algorithms’ priority, dispatching and metaheuristic methods [156][177], to Genetic Algorithms’ batching and sequencing applications [164], Linear Programming and MILP assignment and makespan formulations [49], and Reinforcement Learning value, policy-gradient and actor-critic families with HRL models for dynamic scheduling [181][113]. Each category is paired with named models and a scheduling objective, implementing the semantic columns Algorithm Category, Specific Algorithm Name/Model and Main Application Objective.

The literature supports this HMLV-relevant classification: | Algorithm Category | Specific Algorithm Name/Model | Main Application Objective | |---|---|---| | Heuristic Algorithms | FCFS/EDD/PRD/STWK, CSjobdir/MODCS, FIFO/SRPT/CR [160][156] | Reduce throughput/tardiness/WIP; balance load and meet due dates [160] | | Genetic Algorithms | GA/hybrid GA, RKGA/MO-HGA, NSGA-II/SMPSO [164][132] | Optimize batching/sequencing/flow-shop/rescheduling; minimize makespan, lead time and weighted tardiness [164][32][155][190] | | Linear Programming | MILP/extended integer LP; max-plus-linear MPC [144][109] | Minimize movement, setup/material cost, throughput, transitions and makespan; maximize productivity [144][135][122][49] | | Reinforcement Learning | Q-learning/SARSA/DQN, DDQN/DDDQN/HRL, CNN-A3C/PPO [113][156][181]; value-based RL: 70% of reviewed production-scheduling papers [182] | Adaptive release/scheduling; maximize urgent-order on-time delivery and minimize mean cycle time, earliness/tardiness and machine load [113][156] | Model-only listings remain unconfirmed HMLV applications rather than being overstated [52][85].

On a common goal scale, Heuristic Algorithms seek lower throughput time, tardiness and WIP plus better load balance and due-date satisfaction [160]; Genetic Algorithms minimize makespan, lead time and weighted tardiness [32][155][190]; Linear Programming minimizes cost, transitions, throughput time and makespan while maximizing productivity [144][135][122][49]; Reinforcement Learning seeks higher urgent-order on-time delivery and lower mean cycle time, earliness/tardiness and machine load through adaptive release [113][156][165]. Unspecified model objectives remain unreported rather than inferred [52][85].

**Classification rule and evidence boundary**

The visible period evidence is also uneven. The 2000–2008 record contains genetic-programming and hyper-heuristic examples dated 2001, 2002, 2003, and 2006–2008 [126]. No independent HMLV-specific algorithm finding for 2009–2016 is established here, although a 2015 Q-learning manufacturing-scheduling example is listed [165]. The 2017–October 2022 record includes 2020–2022 hybrid and reinforcement-learning studies, including semiconductor final-testing QHH in 2022 [165]. Accordingly, terms such as *heuristic*, *hyper-heuristic*, *dispatching rule*, *MILP*, *Q-learning*, *DQN*, and *RL-HH* are reported as method keywords, not as quantified HMLV hotspots.

**Current source-group classification**

| Algorithm Category | Specific Algorithm Name/Model | Main Application Objective |
|---|---|---|
| Heuristic Algorithms | Rules-of-thumb, dispatching rules, hyper-heuristics, SCRUPLES, and learning-improvement heuristics; HMLV-specific use is **unclear** in this source group [126][166]. | Quickly obtain good or feasible solutions when exact search is impractical; production scheduling, dispatching, runtime reduction, and robustness. A specific HMLV objective is **not established** [126]. |
| Genetic Algorithms | Hyper-heuristic genetic algorithm for trainer scheduling (2002); Genetic Programming and GP hyper-heuristics; SCRUPLES [126][165]. HMLV-specific use is **unclear**. | Evolve or select dispatching rules and heuristics; compete with First-Fit/Best-Fit or identify an effective schedule. A specific HMLV objective is **not reported** [126]. |
| Linear Programming | Linear programming means optimizing a linear objective under linear equations or inequalities; a 2021 MILP model combines constructive heuristics and meta-heuristics for two-stage assembly flow-shop scheduling with preventive maintenance [193][165]. | Find a best maximum, minimum, or target result under constraints. The named study’s exact objective and HMLV applicability are **not established in this card set** [165]. |
| Reinforcement Learning | Value-based RL (TRL/DRL), policy-based RL (PRL), TRL-HH, DRL-HH, PRL-HH, SARSA, Q-learning, QHH, DQN, DDQN, and DPPO; D3QN and later PPO applications are outside or beyond the cutoff [165]. | Learn actions from rewards for scheduling, resource allocation, and automated decisions. The 2022 semiconductor-final-testing QHH addresses maximum time span, but its HMLV status remains **unresolved** [165]. |
| Heuristic Algorithms | Quadra-directional decomposition heuristic (2007) for two-dimensional, non-equidistant machine-cell location; simulated annealing, tabu search, particle-swarm optimization, and ant-colony optimization for Cellular Manufacturing/Cell Formation; and general rules such as FCFS, SJF, priority, SRT, round robin, Min-Min, Max-Min, and multilevel queue. Predefined heuristics were also used for robotic just-in-time kitting. The cell-formation and general scheduling examples are not automatically HMLV-scheduling evidence. [134][169][104] | Cell location and formation, layout and material movement; general scheduling goals of waiting time, throughput, makespan, and fairness; and efficient delivery of custom kits. A normalized HMLV objective is not reported for most listed heuristics. [134][169][104] |
| Genetic Algorithms | A genetic algorithm for cellular-manufacturing design and layout (2007); a genetic algorithm for inter-cell layout and material-handling-system design (2007); and NSGA-II and SMPSO, used as metaheuristics to resolve a factory-level planning model in a smart cellular system. A general review also links Pan Quanke’s work with flow-shop scheduling, makespan, and genetic algorithms. [134][132][169] | Cellular layout, inter-cell material handling, and factory-level production planning; the general example targets flow-shop makespan. Exact normalized HMLV objectives are not stated for the two 2007 models or the 2022 factory-planning model. [134][132][169] |
| Linear Programming | Linear programming is explicitly listed among approaches for Cellular Manufacturing cell formation and the design of part families and machine cells. A 2006 multi-functional mathematical-programming model addresses manufacturing-cell formation; a mixed-integer linear-programming model addresses dynamic scheduling and rescheduling under internal and external events, with simulation representing stochastic aspects. The cited 2015 MILP example concerns fiducial-marker dictionaries, not HMLV scheduling, and the ADMM example is not explicitly linear programming. [53][134][192][104][169] | Cell formation and machine-cell design; dynamic production scheduling and rescheduling. The HMLV-specific objective remains partial or unclear, so generic mathematical models are not presented as confirmed HMLV algorithms. [53][134][192][104][169] |
| Reinforcement Learning | No supplied card establishes a reinforcement-learning model specifically used for HMLV scheduling. The general scheduling review identifies reinforcement learning as a research area and lists a deep actor–critic online-computing-offloading algorithm. [169] | General online computing offloading and scheduling. Waiting time, throughput, makespan, and fairness are general scheduling objectives, not objectives demonstrated for an HMLV reinforcement-learning model; the HMLV-specific model and objective cells are therefore **unsupported/unclear**. [169] |
| Heuristic Algorithms | Simulated Annealing; hybrid SA+mutation; Tabu Search; embedded heuristic [135][144] | Alternative-route cell layout minimizes movement, setup and machine costs. Robust one-machine scheduling minimizes total tardiness under energy limits; Tabu Search solved large cases within 1 minute [144][106]. |
| Genetic Algorithms | Hybrid GA for capacitated multi-route cells; inter-cell layout/material handling; concurrent cell design; 2010 pull-control GA [135][144][105] | HMLV context: high variety/low demand; cellular manufacturing reduces WIP, handling and setup, while objectives include layout and pull-control optimization; some scheduling objectives are unreported [135][144][105]. |
| Linear Programming | Linearized MILP (2013); extended linear IP; 2022 IQNM/optimization model [135][144][159] | Cell-layout costs include operating, movement, tool, breakdown, setup, construction/expansion and throughput time. The 2022 model minimizes transport cost under throughput/cycle-time constraints; reported errors were 2.11% for throughput and under 5% for sojourn time at SCV=1.5 [135][144][159]. |
| Reinforcement Learning | No specific RL model or policy established: **unsupported** [159] | Objective unreported; the cited IQNM/iterative optimizer is not RL [159]. |
| Genetic Algorithms | Population-based stochastic search: modified flexible-job-shop GA, MB–GA, active-learning/Nash-equilibrium/variable-neighborhood/object-coding/harmony-search hybrids [100][107][127] | HMLV makespan; also tardiness, flow time, workload, energy, cost [100][107] |
| Reinforcement Learning | DDPG + Actor–Critic (Sep 2022) | Mixed-model balancing/sequencing; minimize overload/idle-time; HMLV fit unclear [112] |
| Heuristic Algorithms | FCFS, EDD, PRD, STWK, CS/MODCS; EDA–DES; DP/local search; decision-matrix dispatch; multi-agent HH [160][95][71][98][99] | Release sequencing, load balance, throughput/WIP, tardiness/due dates, transport choice, and makespan [160][95][71]. |
| Genetic Algorithms | MB–GA; modified FJSP, energy-flow-shop, genetic-immune permutation, and cost-oriented hybrid GA [32] | HMLV scheduling/makespan; flexibility, energy, and cost; MB–GA AHP score: 83.42% [32]. |
| Linear Programming | Layered-Encoding Cascade for HMLV product mix; mathematical-programming cell formation/scheduling; exact LP subtype unclear [32][95] | Product mix, cells, and schedules; partial support [32][95]. |
| Reinforcement Learning | No named HMLV RL model; MAS/EDA learns sequencing, but is not explicitly classified as RL [98][99] | Unsupported; learning-based release targets mean weighted tardiness [98]. |
| Heuristic Algorithms | FIFO/SRPT/EDD/CR; SGS, shifting-bottleneck/column-generation, GRASP, SA [150][156][185] | tardiness/makespan/cycle/throughput [186] |
| Genetic Algorithms | GA+simulation/DP; NSGA-II [150][185] | lateness/tardiness/makespan/multi-objective |
| Linear Programming | MILP: time/rank/event; Petri-net LP [49][150] | assignment/precedence; makespan/throughput/lead time; dynamic limit |
| Reinforcement Learning | Q-learning/DQN/CNN-A3C [156] | adaptive release; urgent OTD/cycle time/productivity/flow [156] |
| Heuristic Algorithms | No named in-scope HMLV model established; later NP-hard-scheduling evidence gives only generic heuristic context [91]. | Efficient acceptable-time solution; HMLV objective unreported [91]. |
| Genetic Algorithms | LECO (GA/PSO) HMLV optimizer (24 September 2009); integrated GA–PSO; cellular-manufacturing GA (2001) [86][34][58]. | Lower conversion time; higher productivity, equipment efficiency and throughput; the 2001 objective is unreported [86][34][58]. |
| Linear Programming | HMLV flow-path mathematical programming (2008); mixed-integer LP/constraint-programming printing-shop model (2020), with details unreported [34][85]. | Optimize flow among cells; printing-shop objective unreported [34][85]. |
| Reinforcement Learning | No explicit HMLV RL model established; ANFIS makespan estimation and AI/ML FMS methods are not RL [145]. | Unsupported/not reported [145]. |
| Genetic Algorithms | Hybrid multi-objective GA for machine–AGV scheduling (2006); GA attribute selection (2005); GA–Monte Carlo routing-flexibility analysis (2015) [70]; improved GA for reconfigurable FJSP with limited auxiliary modules (2022) [190] | Multi-objective FMS scheduling, routing/attribute selection and total weighted tardiness; the 2022 GA adds encoding/decoding and iterated local search [70][190]. |
| Linear Programming | Max-plus-linear MPC for HVLV (2011) [109]; MILP_H (29 Dec 2021) [191]; LP/OPL–CPLEX maintenance and revenue-levelled schedules in HMLV LED lighting [97]; segmented-CONWIP MILP [163] | Event timing/control; makespan or weighted makespan/maximum lateness; maintenance, revenue leveling, cost, lead time, inventory and CONWIP-card throughput allocation [109][191][97][163]. |

**Heuristic, genetic, and mathematical-programming evidence**

Heuristics are “rules of thumb” used to generate good-quality solutions when exact methods are infeasible; they address large, constrained, noisy, or dynamic scheduling searches but do not guarantee optimality [126]. Examples include GSAT, HSAT, GWSAT, Walksat, Novelty, Novelty+, R-Novelty, and the First-Fit, Best-Fit, Worst-Fit, Almost-Worst-Fit, and Next-Fit rules [126]. Hyper-heuristics differ because they search, combine, adapt, or generate heuristics rather than directly searching the production-schedule solution space [126].

**Reinforcement-learning taxonomy and limits**

Reinforcement learning models an agent interacting with an environment through states, actions, transitions, and rewards. In RL-based hyper-heuristics, executing a low-level heuristic is the action, improvement in the solution is treated as feedback/state information, and the controller selects a suitable heuristic at successive optimization stages [165]. Value-based RL updates Q-values, commonly through Bellman iteration, and selects the highest-valued heuristic; policy-based RL directly parameterizes the probability of selecting an action and updates it toward higher expected reward [165].

The source separates value-based RL into traditional and deep variants and identifies TRL-HH, DRL-HH, and PRL-HH. Traditional controllers use value, transition-probability, bandit, or Q-table updates. Named examples include Q-learning-based hyper-heuristics, QHH-BS, Q-learning plus simulated annealing, and Q-learning selection of manufacturing-scheduling heuristics. Lin, Li and Song’s 2022 QHH addresses semiconductor final-testing scheduling with maximum time span; Heger and Voss’s 2021 study changes sequencing rules under stochastic job-shop influences; and Mosadegh, Fatemi Ghomi and Süer’s 2020 model combines Q-learning, simulated annealing, and hyper-heuristics for stochastic mixed-model assembly sequencing [165]. These are scheduling examples, but the cards do not establish that each is HMLV.

Deep RL uses neural networks to represent larger or higher-dimensional state information. DQN, DDQN, and D3QN are listed as deep value-based variants; however, the source notes that DRL does not remove high-dimensional action-space limitations. Policy-based methods can handle more complex action representations, but they may require more samples, incur high time overhead, suffer training instability, and be computationally expensive for real-time use [165]. The review therefore supports RL as an adaptive scheduling family while also requiring explicit qualification of scalability, training, and HMLV-transfer limitations.

A separate 2024 page describes a PPO–Transformer improvement heuristic for customized car-seat production, minimizing job tardiness and employee stress through pairwise job swaps; it reports better performance than tested heuristics but is outside the requested cutoff and does not explicitly identify the case as HMLV [166]. The same page lists 2017 PPO, 2018 RLlib, 2020 deep-RL routing/job-shop examples, and a 2022 routing heuristic; a February 2023 graph-neural-network/DRL model and the 1983 simulated-annealing paper are excluded from the historical roster by date [166].

Heuristic—cash-constrained multi-project heuristic; name/HMLV objective unreported [36]. Genetic—MB–GA schedules HMLV Industry 4.0, minimizing makespan; probabilistic mutation is costly [36]. Linear programming—MIP+simulation+GA (not pure LP): MIP minimizes supply-chain cost; simulation tests delayed orders [36]. Reinforcement learning—Q-learning/SARSA/DQN/actor–critic maximize cumulative reward; HMLV use/objective unestablished [103]

Post-cutoff: GA/GP (CDGP/GPRR/GPRT), heuristics (FIFO/STT/MTR), RL (DQN/DDQN/PPO/RLGP); HMLV Linear Programming: unsupported [167][168][96]

**Evidence-qualified algorithm classification**

**Interpretation and evidence limits**

The dated permitted evidence is uneven. The smart-cellular-production paper was published on 20 April 2022 and integrates factory planning, shop-floor bidding for unexpected events, cell-level decisions, scheduling, material handling, and real-time supply-chain data; its mathematical model is solved through NSGA-II and SMPSO and tested on a numerical example after parameter tuning. It concerns mass-customized production, but the supplied evidence does not independently establish the HMLV label or a normalized objective. [132] The public IEEE paper published on 29 August 2022 uses predefined heuristics for robotic kitting; variable part availability and logistics delays can make those rules inflexible, whereas its bilevel framework selects and arranges parts and schedules just-in-time delivery, evaluated with an 18-person study and shop-flow simulation. This is useful contextual evidence, not confirmed HMLV scheduling evidence. [104]

The general scheduling bibliometric review covers 12,644 Scopus documents from 1992–2021 rather than the HMLV corpus. Its title-only trend analysis used a minimum frequency of 50, found no qualifying keyword pairs before 2004, reported packet, fair, and real-time scheduling as prominent in 2004–2007, a frequency of 1,560 for “Scheduling Algorithm” in 2015, a keyword-count peak around 2017, and edge computing as the leading trend in 2020–2021. It also reports hybrids such as Ant-Bee and SBDE, and an ADMM distributed-scheduling example; none is verified here as HMLV scheduling. The single-Scopus dataset is itself a limitation. [169]

Additional evidence: scheduling generates detailed work-center orders within capacity [162]; pseudo-polynomial, exact B&B and logic-based Benders appear in a 2018 robust-scheduling roster [106]. A 2020 CONWIP simulation uses dispatching for workload balance while varying arrival, processing, card and loading factors [161]. Cellular references list dynamic reconfiguration (2009), Benders (2011), multi-objective (2014), fuzzy/stochastic (2015), and LP-hybrid (2016) models; full names/objectives remain unresolved in the supplied span [55].

Heuristic 3P-PCB-PH (HMLV?): makespan [171]; Genetic hGA(greedy+bisection): cycle/workload [170]; LP Model 2: makespan [128]; RL: 2024/out [154]

Reinforcement Learning (2009): policy-gradient DEC-MDP agents minimize stochastic job-shop Cmax; HMLV: partial evidence; local optimum only [174].

2022-12-09 [113]: FIFO/FILO/SSO=heuristics; GA=metaheuristic; HRL/Q-learning=RL. Cutoff-valid [114]: heuristic-guided Q-learning, FJSP optimization.

Heuristic Algorithms: EDD/MDD/SLK/S-RW/GRD, NEH/IG/SA and finite-capacity WIP planning target tardiness/on-time delivery [177][115]. Genetic Algorithms: HGA/GDA/GA target makespan; ASIC dispatching GA balances delivery, cycle time, WIP and tardiness [129][176]. Linear Programming: PI-printing MIP/MTMCP targets throughput [178]; Lagrange/network-flow/Frank-Wolfe not explicit LP/HMLV [175]. Reinforcement Learning: unsupported.

|Algorithm Category|Specific Algorithm Name/Model|Main Application Objective|
|---|---|---|
|Heuristic Algorithms|APOLLO Branch-and-Bound, timer-stopped (2018); B&B+GRASP/rolling horizon proposed hybrids [180].|Aerospace: minimize production time/maximize autoclave use under prepreg out-life/minimum-load limits; runtime and scrap rescheduling limit it [180].|
|Genetic Algorithms|NSGA-II, multiobjective GA (2002); cited aircraft use and HMLV objective unreported [118].|Multiobjective optimization; HMLV objective unsupported [118].|
|Linear Programming|Two LP methods plus iterative scenarios (Egypt, 2022-09-19); \(Z=\sum(P_j-C_j)x_j\) with resource/demand constraints [117].|Profit/resource utilization and production-rate/market-demand feasibility; not explicitly HMLV [117].|
| Reinforcement Learning | DQN/PPO; value-based (70% review); setup-aware RL | Adaptive: makespan/tardiness/setup waste; simulations [182][183] |
|Heuristic Algorithms|Greedy/VFLS/JSL|Violations; local search; HMLV cluster/layout/sched [121][87]|
|Genetic Algorithms|GA–ROC/PFA; robust-cell GA (2015)|Dynamic routes; feasible cells; partial/later [146]|
|Linear Programming|MILP (2002); MPS+/EMPS (2022)|Transitions/productivity; due-date/inventory; sequencing [122][121]|
|Reinforcement Learning|No permitted HMLV model|Required row; objective unsupported [146]|
| Reinforcement Learning | Specific HMLV RL model: not established; only generic ML evidence [194] | Objective: not established [194] |

Heuristics trade global optimality for speed and may trap locally [180]. The 2023-11-21 LP paper is post-cutoff and excluded [116]; wider material scaling can reduce LP accuracy [117].

**Heuristics:** HMLV base/max/oscillation ordering + local/cycle lot-splitting (10 rules); makespan <105% of best/mix [89]. k-means—not RL—compressed 235 orders into 5–100 clusters; lead-time/delivery and breakdown/shortage risks [89]. **Genetic Algorithms, Linear Programming, Reinforcement Learning:** no eligible in-window model for these categories here; 2023 cloud HHRL (GA/ACO/PSO/F-PSO; makespan/diversity) is out-of-scope [123].

Heuristic algorithms: HMLV math+resched [92]; LP: generic MILP/tank schedule [124]; RL: multi-agent FJSP, 02-Oct-22 [125]; GA: unsupported [184].

**Heuristic Algorithms:** Two-phase, flow-matrix and machine-assignment heuristics; GRASP, tabu, simulated annealing, ACO, ABC, scatter search, hyper-heuristics, iterated local search, MIP/QCP heuristics and branch-and-bound address cell formation/layout and flow-cell scheduling [52][139][130]. Objectives include makespan, flow time, total completion, and weighted earliness/tardiness; an HMLV-specific objective is not established. Routing/production-data support yields a quasi-optimal solution [139][130].

**Genetic Algorithms:** Documented models include adaptive, grouping, multi-objective, branch-and-bound-enhanced, hybrid, immune, two-layer, adjustable-grouping, virtual-cell, and integrated cell-formation/layout/scheduling GAs [52][139][130]. Objectives include material-handling cost, makespan and tardiness; HMLV status is partial [139].

**Linear Programming:** Mathematical cell-formation, linear-assignment, two-phase fuzzy-LP, and LP-embedded/linearized mixed-integer CMS models use non-negative variables, linear constraints and a linear objective; cited use is cell design, not explicit HMLV scheduling [52][130].

Heuristics: ROC/MODROC, SPT/LPT, MULTI FIT, tabu—makespan; GA:HVNS-NSGA-II—cost; LP:lot-streamlining FJSP—unreported; RL:none shown[140][141][142]

SA/TS/ACO—flow/tardiness; GA/MO-TS-GA—completion/intercell; LP—flow/setup [136]. RL—DRL-PPO (2022), objective unreported; HMLV unclear [143].

Taxonomy: assign the primary family and retain hybrid labels. Sources [98] (2022-12-11) and [61] (2023) are post-cutoff context. The [98] test has 6 workcenters, 21 machines, 20 types, stochastic arrivals/routings, priorities, setups, and due dates; its semiconductor lead has no model, objective, or validation details [98].

Heuristic Algorithms: SA/tabu/ACO/PSO/DE; fast near-optimal WIP/lead-time/tardiness/makespan schedules; no guarantee [157]. Genetic Algorithms: 2006 hybrid/2008 constructive/2020 improved GA; HMLV objective unclear in eligible slice [119][157]. Linear Programming: IP/MILP/DP; WIP/lead-time/tardiness objective candidates; NP-complete limits [157]. Reinforcement Learning: Q-learning/DQN/PPO/HRL; HMLV model/objective unclear; later source [151].

Heuristic alg.: STOCh, ~3% vs CPLEX [102]; Genetic alg.: LECO/MORMGA [102]; Linear prog.: MILP unclear [187]; Reinf. learning: unsupported [153].

Post-cutoff survey of pre-cutoff studies: hybrid categories overlap [164]. Heuristic Algorithms—ERT/FF/BF, GRLPT, VND, GRASP, SBH, adaptive/multi-rule dispatching, hybrid TS (2022): batching/sequence/bottlenecks; revenue/jobs; setup, release and expiry [164][138]. Genetic Algorithms—GA/MA, grouping GA, BRKGA/RKGA, HGA/MO-HGA, simulation-GA for POLCA: batching/sequence, makespan/completion/E-T, throughput/utilization, due dates, setup/energy [164][138]. Linear Programming—LP/MILP/MINLP, photolithography MILP (2010), rolling-horizon MILP: assignment, batches/resources, setups and dynamic arrivals; exact small cases and bounds for large cases [164]. Reinforcement Learning—SARSA (five actions), Q-learning, DRL, DQN/DQL; robust fab (2020)/packaging (2021): job-resource choice, setup, robust/scalable adaptive dispatching; nearly 70% above rules [164]. ASSIST (2001) documents low-volume space-system process planning/scheduling, but no named heuristic [179].

Genetic algorithms [131]: 2019 HMLV APS job-shop model uses mutation/selection/recombination (ABC, 2005) for makespan, tardiness/delays, deadlines, inventory and DIFOT; it reschedules disruptions but assumes deterministic inputs/time-limited convergence. Cell/FMS GAs: 2002, 2005–06; 2010 genetic search: objective unreported [133][68][94]. Linear programming: no HMLV model/objective shown; complex systems use simulation [94]. RL [158]: Q-learning/SARSA/DQN/PPO/TRPO target dynamic scheduling; general, not HMLV-specific. HMLV DES+ML targets scheduling/capacity/release/allocation, not RL .

Heuristics/GA: 2015 batch GA, 2020 HGA lot/load balance, makespan [137][149][155][189]; LP/MINLP-2020 lot/load [189]; 2022 RL-GNN stable JSS [74].

**Genetic and linear-programming models**

MILP_H minimizes makespan when jobs meet due dates, otherwise weighted makespan and maximum lateness; across 15 real/simulated problems (2021), average makespan fell 4.22% and average maximum lateness 22.62% [191]. A 12-week HMLV capacity tool reduced maximum tardiness from 28 to 5 days and tardy jobs from 60% to 11%, but required added capacity . SA–RVNS adds automated equipment/buffer configuration and reported 10–30% profit improvement; its category is unassigned [88]. These cards establish no RL model: the 2020 automotive and 2022 machining cases instead use DES/lean or simulation/statistics [84][93].

Linear Programming: 2021 MILP—6 products/4 lines; makespan and line count [110]. HMLV LP—preventive-maintenance uptime and revenue leveling [90]. 2022 AM MILP—HMLV link unclear; 2D/1D nesting, tardiness/makespan, simple cases optimal [111]. Reinforcement Learning: 2004 distributed RL—batch sequencing/sizing [148]; 2018 semiconductor-testing Cuckoo Search–RL–surrogate model; objective unreported [101]; HMLV objective unestablished [148][101].

For dynamic HMLV release, CONWIP is represented by greedy backlog sequencing: PRD, STWK, CSjobdir and modified capacity-slack rules are preferred to repeatedly re-solving an optimization when arrivals, routings and processing times are stochastic [160].

The classification table uses Algorithm Category, Specific Algorithm Name/Model and Main Application Objective; Heuristic Algorithms, Genetic Algorithms and Reinforcement Learning are family labels, while Linear Programming denotes a mathematical formulation, and combined B&B–GRASP and DDQN/DDDQN entries retain hybrid overlap [180][113]. It lists Heuristic Algorithms for backlog and dispatching [160], Genetic Algorithms for batching and sequencing [164], Linear Programming for cell-formation cost control and maintenance or revenue leveling [144][97], and Reinforcement Learning for dynamic release and scheduling [113][156].

Normalize the objective column as follows: Heuristic Algorithms support rapid scheduling, dispatching-rule discovery, runtime reduction and robustness [126]; Genetic Algorithms support batching, sequencing, flow-shop and rescheduling decisions [164]; Linear Programming supports movement/setup-cost and preventive-maintenance or revenue-level control [144][97]; and Reinforcement Learning supports real-time multi-objective scheduling under random arrivals [113]. These mappings connect HMLV needs to fast rule decisions, varied sequence applications, explicit capacity/cost trade-offs and adaptive release policies [160][156][164].

Linear Programming is used as an extended integer formulation covering routing, tool allocation, machine reliability and inter- or intra-cell movement and setup costs, while LP schedules address preventive maintenance and revenue leveling [144][97]. Reinforcement Learning improves actions through feedback [165], and HRL with DDQN/DDDQN handles random-arrival, multi-objective flexible-job-shop scheduling in real time [113].

Heuristic Algorithms address the HMLV hotspot of rapid dispatch and backlog sequencing when stochastic arrivals make re-optimization costly [156][160], whereas Genetic Algorithms provide models for batching, sequencing, flow shops and rescheduling [164]. Both therefore connect directly to HMLV scheduling decisions.

Linear Programming supplies an explicit constraint-based decision layer for cell-formation costs, maintenance, revenue leveling, transitions and productivity [130][144][97][122]. Reinforcement Learning supplies feedback-driven adaptation for dynamic flexible-job-shop and release scheduling with random arrivals, uncertain processing times and urgent orders [103][113][156].

Within the layout and process material, Heuristic Algorithms appear in HMLV layout design through PFAST with a Genetic Algorithm and in FMS planning through lot-sizing, cell grouping, tool loading and scheduling heuristics [44][140]. As a method, a heuristic is a rule of thumb for quickly obtaining a good solution; in high-variety production it is applied through CONWIP backlog and dispatching rules such as PRD, STWK and CSjobdir [126][177][160].

The table preserves the requested semantic fields, and its Heuristic Algorithms row pairs PRD, STWK, CSjobdir and MODCS with high-variety CONWIP backlog sequencing [160]. Heuristic Algorithms face breakdowns, long processes and new orders in dynamic scheduling [173], while stochastic semiconductor events make job-shop scheduling NP-hard [150]; countermeasures include RFHCP/RFFS matheuristics, the 3P-PCB-PH makespan approximation and QMOHH heuristic selection [108][171][152].

Genetic Algorithms contribute to layout and process planning through sequence-based factory planning and flow or hybrid-flow scheduling [132][164]. Their principle is population-level parallel search [36], and HMLV applications include dispatching-rule weighting at a high-mix, low-volume ASIC facility, photolithography capacity allocation and makespan minimization [176][189][129].

Genetic Algorithm scheduling maintains a population of candidate solutions and searches alternatives in parallel rather than from a single point [36]. The table therefore keeps the family label, named GA models and scheduling objectives separate; documented uses cover batching, sequencing and rescheduling, with makespan and facility-performance goals [164][129][176].

Linear Programming and MILP scheduling must assign operations to capable machines, preserve order and non-overlap, and minimize makespan [49]; cell-layout formulations add routing, capacity and material-handling costs [135]. Targeted models include extended integer programming for route, tool, reliability and movement costs [144] and LP schedules for preventive maintenance and revenue leveling [97].

Linear Programming selects nonnegative variables satisfying linear constraints and a linear objective [130]; in manufacturing it becomes integer or mixed-integer cell-formation and scheduling models [144][49]. Its HMLV-relevant applications include ERP-based preventive-maintenance and revenue-leveled schedules and cost-minimizing cell formation [97][144].

Linear Programming and MILP can find optimal solutions for deterministic job-shop instances [150], but model complexity and solution time grow with size, making MILP most suitable for small- and medium-size problems [172]. The LP row consequently names the formulation and records assignment, non-overlap and makespan objectives rather than treating LP as a dispatching rule [49].

Semiconductor scheduling must absorb uncertain processing times and urgent orders, while mixed-model assembly must coordinate worker balancing and sequence decisions to reduce overload and idle time [156][112]. Linear Programming and MILP countermeasures address route, movement, tool, reliability and setup costs [144] and preventive-maintenance or revenue-level schedules [97]; Reinforcement Learning adds CNN-A3C release control with adaptive rewards [156].

Reinforcement Learning treats scheduling as state–action–reward interaction and learns either Q-values or a direct policy [103][165].

Reinforcement Learning is applied to random-arrival flexible job shops and uncertain semiconductor release control [113][156]. In the latter, CONWIP parameters set maximum WIP and release proportion, while the agent observes a state, chooses combined release and scheduling actions and receives rewards at each decision point [156].

Reinforcement Learning offers adaptive real-time selection, preference-aware multi-objective compromise and suitability of policy methods for high-dimensional continuous actions [113][165]. Limitations include poor scalability of traditional RL, unresolved high-dimensional action spaces for DRL, policy-training overhead, sample demands, instability and computational cost [165]; the table names value-, policy-gradient and actor-critic models such as Q-learning, DQN, PPO, A2C, HRL and DDQN/DDDQN [181][113].

Documented industry examples pair semiconductor manufacturing, with uncertain times and urgent-order release, with mixed-model assembly, where balancing and sequencing must control overload and idle time [156][112]. Targeted models are CNN-A3C dynamic release control and a multi-agent deep-RL design using DDPG for balancing, Actor–Critic for sequencing and iterative information exchange [156][112].

Classification uses the dominant mechanism: heuristic rules/search [160][126], population evolution by Genetic Algorithms [131], linear-constraint formulation by Linear Programming [117], or state/action/reward policy learning by Reinforcement Learning [156][165]. Thus Heuristic Algorithms, Genetic Algorithms and Reinforcement Learning are families, Linear Programming is a formulation, and names are models/variants; HMLV-relevant uses cover stochastic release, batching/sequencing, constrained cell/resource decisions and dynamic scheduling, with GA–simulation/GA–SA and RL hyper-heuristics overlapping categories [160][164][144][113][155][165].

## Leading application industries and their literature prominence

**Electronics and semiconductors lead the defined proxy.** To quantify prominence without confusing research representation with production output, the comparison uses ten distinct, sector-specific application studies discussed in this report. Electronics/electrical-equipment manufacturing is treated as a broad application group covering PCB fabrication, electrical distribution/control equipment and architectural lighting; semiconductor production is coded separately.

| Rank on this proxy | Application group | Study count | Approximate proportion | Principal settings |
|---|---|---|---|---|
| 1 | Electronics/electrical-equipment manufacturing | 4 of 10 | 40% | PCB pressing; control equipment; custom lighting |
| 2 | Semiconductor manufacturing | 2 of 10 | 20% | Microprocessor assembly/test; semiconductor assembly/test |

**The calculation uses named literature inputs.** The four electronics/electrical-equipment studies are Slomp, Bokhorst and Germs’ 2009 control-system implementation, Rodriguez’s 2021 PSI Control Solutions project, Laisupannawong and colleagues’ 2021 PCB scheduling study, and Kadam’s 2022 architectural-lighting thesis. The electrical-equipment setting of Slomp’s case is also described in Kadam’s in-period literature discussion. [12][26][25][19]

The semiconductor studies are Gilland’s 2002 Intel-patterned cell analysis and Boydon, Wu and Wu’s 2021 assembly-and-testing scheduling framework. [9][27]

The denominator also includes four differently classified applications: Chua and colleagues’ precision-engineering study, Frazee and Standridge’s photonics study, Khan and Standridge’s furniture-cell study, and the 2022 Hungarian pneumatics study. Thus, the calculated estimates are 4 ÷ 10 × 100 = 40% and 2 ÷ 10 × 100 = 20 (est.), a difference of 20 percentage points. [8][16][21][7]

**The proxy measures application representation.** Its practical value is that every counted study has a named operating setting and a traceable scheduling or production-control contribution. It does not measure the number of factories using HMLV, their output, employment or revenue. A market-adoption ranking would depend on comparable plant-count, installed-base or production-output denominators across industries.

A separate document-based coding assigns semiconductor manufacturing an approximate 12% share of the reviewed HMLV document corpus.

The denominator is the reviewed HMLV document corpus; 12% is a document share, not a production-market share.

**Prominence has an operational explanation.** Both leading groups combine product differentiation with expensive shared resources and scheduling-sensitive delivery commitments. However, their most revealing research examples emphasize different problems: electronics highlights explicit process compatibility and coordination, while semiconductor assembly and testing highlights heterogeneous equipment and incomplete product-machine data.

**Industry-prominence takeaway.** The two groups are useful leading applications for development analysis, while the numerical ranking should be read on its stated, reproducible literature-presence basis.

**Additional documented evidence**

**Candidate screening and evidence boundary**

The candidate universe is defined by production process, not output-market share. 2022 NAICS groups establishments by similar production processes, covers 20 sectors and 1,012 U.S. industries, and defines manufacturing as transforming materials, substances or components into new products [207]. Reporting-unit definitions affect count comparability; ISIC may place multi-activity units in more than one class or use the activity contributing the most value added [207][209]. These classifications establish screening boundaries, not HMLV adoption.

| Candidate industry | Evidence and status from this source group |
|---|---|
| **Semiconductor manufacturing** | NAICS 334413/33441 and Census codes 3390, 3344 and 3346 identify the category [207][208]. A 2009 publication documents MT-HMLV facilities at the micro-/nano-/semiconductor-fabrication interface: borrowed high-volume metrics were ineffective, so it proposed a metrics approach combining MT-HMLV characteristics, HVSF metrics and R&D metrics [196]. A 2007 semiconductor-manufacturing special issue and a cited wafer-fab case establish research presence, but not a corpus count or rank [205][204]. The 13 October 2022 semiconductor-controls rule likewise establishes industrial relevance, not HMLV prominence [211]. **Candidate; proportion unresolved.** |
| **Electronics manufacturing** | NAICS 334, 3344 and 334418 cover computer/electronic products, electronic components and printed-circuit assembly [207]. A 2011 Thailand EMS case used cellular layout, Systematic Layout Planning and AHP; many customers and orders created varied products and routes, although the source describes the setting as high-volume/high-variety rather than explicitly HMLV [220]. **Candidate; proportion unresolved.** |
| **Aerospace and defense manufacturing** | NAICS 3364 includes aircraft, engines, aircraft parts and guided-missile/space-vehicle manufacturing [207]. Permitted evidence covers robotic machining of large aerospace parts, including a 2017 aerospace-robotics publication [219], and titanium-alloy use in aerospace and defense [215]. **Candidate; proportion unresolved.** |
| **Medical-device manufacturing** | Census code 3960/NAICS 3391 identifies medical equipment and supplies [208]. Medical devices also appear in an MES industry list and in the titanium-instrument application context [217][215]. **Candidate; proportion unresolved.** |
| **Industrial machinery / ETO** | NAICS 3332 includes industrial, semiconductor and other machinery; Census labels also include construction/mining, commercial/service and metalworking machinery [207][208]. ISIC 28 (“machinery and equipment nec”) has 6.52% global R&D intensity, but this is not an HMLV literature share [209]. **Candidate; ETO-specific rank unresolved.** |

An MES platform separately lists Semiconductor, Electronics, Medical Devices and Industrial Equipment as served industries, supporting candidate labels only [217]. A separate FMS market segmentation reports Automotive at **38.2%**, Aerospace at **24.7%**, Electronics at **19.3%**, Medical Devices at **11.8%**, and Other applications at **6.0%**; Medical Devices is reported as **2.4%** under a different end-user classification [201]. The source attributes aerospace demand to precision, complex geometry, traceability and relatively low volumes; electronics includes semiconductor assembly and circuit-board production; and medical devices involve traceability, documentation and sterilization. These are FMS market shares, outside the requested corpus, not HMLV-literature proportions.

The Texas profile provides further contextual—not global HMLV—evidence: its Computers, Electronics and Semiconductors cluster spans **29 industries** and recorded **$23 billion GDP contribution, $8 billion exports and 85,000 jobs in 2021**; its Aerospace, Aircraft and Defense cluster spans **six industries** and recorded **$16 billion, $10 billion and 51,000 jobs**, respectively; Production Technology and Heavy Machinery spans **34 industries** [210]. NIST reports U.S. semiconductor sales of **$208 billion in 2020**, more than a quarter-million workers and **12%** of global manufacturing capacity; later SIA material reports **338,000 workers**, **50.2%** of global sales, over **300** downstream sectors and a projected **67,000-worker shortfall by 2030** [214][213]. These measure industrial scale, not research prominence. NIST also records shortage, material, contamination and measurement problems, with standards, materials/testing, TSOM and a photomask standard reducing discrepancies tenfold as responses [214].

Post-cutoff evidence is excluded from ranking: a 2026 electronics HMLV-manual study used **200 manuals and 4,754 steps** and proposed adaptive digital instructions for product variation [195]; a 2025 flexibility bibliometric study contains **252** Scopus publications and describes Malaysia’s E&E sector as exposed to rapid cycles and external shocks [218]. Thus this source group establishes candidates and evidence boundaries, but no defensible HMLV document count, rank or proportion. A valid top-two calculation still requires a deduplicated in-window corpus, counted unit, multi-industry and unassigned-study rules, overlap treatment and rounding; the 2018 bibliometric source itself warns that it lacked full texts, had author keywords only from 2005, and covered academic sources only [205].

Aerospace is low-volume/high-variability: an EU study covered 17 suppliers, customization/regulation, 15 barriers and four digital/Industry-4.0 enablers; a 2020 aircraft study used hybrid simulation-optimization for ramp-up, workforce, buffers, lead times and backlog [221][118]. ETO/machinery evidence reports customer changes, on-site errors and seven barrier groups; DDS screening narrowed 582/398 database hits to 54 papers and separates context from implementation (A/B/C) [212][202]. Medical-device evidence lists compliance, supply, quality, cost, traceability and training challenges, with MES/inspection/tracking/certification responses [216]. Perfume is an added 15-Mar-2022 digital-twin/MILP case, not a rank; 2025 aerospace material is excluded [192][206].

Semiconductor manufacturing is HMLV-relevant: a 2012 low-volume, high-mix ASIC facility had several hundred product types/variants and process steps on dozens of equipment, with re-entrant flows, failures, setups and batching; weighted dispatching improved cycle time, WIP and on-time delivery about 5–8% versus extended FIFO [176]. A 2018 study addressed HMLV fabs with finite-capacity WIP planning and weighted-tardiness minimization under delivery and equipment constraints [115].

Electronics manufacturing has direct in-scope evidence: a 2014 HMLV PCBA case reported stochastic demand, varied products/test routes, long cycles and high fallout; a lean/pull pilot reduced cycle time 40% and defects 10–30% [29]. Aerospace/defense is represented by an October 2022 HMLV smart-manufacturing survey citation, and a 2000 low-volume aerospace study covered assembly balancing and scheduling [197][198]; scenario-based order allocation addressed uncertain aircraft configurations [223]. Medical-device evidence only shows small-batch, tight-tolerance FMS use [63]; its supplied direct scheduling study is from 1992, outside scope [199]. These cases establish relevance, not a comparable literature share or adoption rate; a top-two ranking is therefore unsupported by these records.

The available evidence supports no defensible ordering or gap in HMLV research prominence: Semiconductor manufacturing appears as an MT-HMLV context [196], Electronics manufacturing as an EMS case with varied orders and routes [220], Aerospace and defense manufacturing in a public-source record dated 2020-12-14 [118], and Medical-device manufacturing without a comparable HMLV-literature measure [201]; these context or case signals do not by themselves establish adoption. The industrial-context/empirical-nature classification (classes A, B and C) should separate implementation evidence from analytical or case-data evidence, while terminology and case-availability effects remain material because the review used only two databases and almost 50% of its papers came from two journals [202].

Within the HMLV manufacturing framework, Semiconductor manufacturing is a documented application: Intel’s Ireland Fab was transitioning from high-volume batch-process flow to HMLV, while product-mix variation, re-entrant routing and varied WIP make capacity planning and scheduling difficult [43][189]. The implication is to use semiconductor fabs as a hotspot-and-technology case: CONWIP reduced flow time while maintaining throughput in end-of-line assembly, while ML-based JIT1 optimization used secure-fab simulation for real-time throughput control [203][222].

Within the HMLV manufacturing framework, Electronics manufacturing is a direct application context: an assembly case combines a high-mix, low-volume portfolio with fluctuating demand and flexible customer requirements, while EMS orders from many customers create different products and routes [220]. The implication is to treat electronics as a test bed for layout and process hotspots: Cellular Manufacturing groups job families on machine cells to reduce movement and flow time, and Lean Manufacturing supplies a process-improvement route [139][200].

Under the HMLV manufacturing framework, Aerospace and defense manufacturing is a low-volume mixed-model assembly context; customized components, broad product variety, frequent task switching and diverse routing make scheduling difficult [198]. The implication is to treat aerospace as a case for Agile Production and uncertainty-aware scheduling: configurations finalized after ordering create uncertain workload, for which scenario-based scheduling is proposed [197][223].

## Electronics/electrical-equipment manufacturing: match control to process constraints

**Electronics contains several distinct scheduling problems.** PCB fabrication, board assembly and configurable electrical-product assembly are related manufacturing activities, but they are not the same process. The strongest examples here show why the scheduling model must be chosen at the process level rather than attached indiscriminately to an industry label.

### PCB pressing: compatibility and shared-resource scheduling

**The central problem is constrained batching.** Laisupannawong, Intiyot and Jeenanunta’s 2021 study examined short-term scheduling of the pressing process in multilayer Printed Circuit Board (PCB) manufacturing. It minimized makespan, meaning completion time for the scheduled job set, rather than directly optimizing all customer-delivery outcomes. [25]

The model used a 360-minute press-machine cycle over a three-day planning horizon. Within a cycle, all books—the material stacks prepared for pressing—had to share panel type, Stainless-Steel Template (SST) size and layout. An oven could perform only one press machine’s pressing phase at a time.

**Compatibility makes unrestricted pooling infeasible.** Jobs cannot simply be combined because the resulting batch is convenient for the schedule. They must satisfy the material and template restrictions. Likewise, otherwise available press machines cannot all use the same oven simultaneously.

This creates two coupled decisions: which compatible jobs belong together, and when their press and oven activities should occur. A rule that looks only at a press queue can therefore produce conflicts at the shared oven. [25]

**The targeted solution was improved MILP.** Model 2 represented assignment, sequencing and resource restrictions explicitly. The source reported an average relative improvement of **34.71% in computational time** compared with the previous MILP formulation, using literature and additionally generated test problems.

This is a solver-performance result. It means the improved formulation required less computation on the tested comparison; it should not be read as 34.71% shorter pressing cycles, higher throughput or faster customer delivery. [25]

**The physical cycle remains a constraint.** The 360-minute cycle equals six hours, but the shared-oven restriction applies specifically to the pressing phase, not automatically to every minute of the entire machine cycle. Preserving this distinction avoids overstating oven occupancy.

The model also assumed demand was feasible within the horizon and resources, and SST availability was unlimited. If template scarcity, infeasible demand or a different business objective becomes important, those conditions change the model required.

**PCB judgment.** MILP fits this application because feasibility depends on explicit compatibility and shared-resource rules; a release-control method alone would not enforce those requirements.

### Electrical assembly: connect flow, quality and delivery

**Assembly performance depends on more than sequencing.** Rodriguez’s June 2021 MIT project studied PSI Control Solutions, a mid-sized assembler of electrical distribution and control products. Its improvement work focused on component replenishment and production-process performance.

After a production cell applied waste elimination, mistake-proofing and pull methods, the share of sales delivered by the customer-desired date rose from 85.7% to 100% across subsequent three-month observation periods. First-pass yield rose from 87.9% to 93.1% across six-month periods. These are increases of 14.3 and 5.2 percentage points, respectively. [26]

**The mechanism includes effective capacity.** Rework consumes labor and time that a schedule may otherwise treat as available for new orders. Missing components can similarly interrupt a planned sequence. Improving replenishment and reducing errors therefore makes the schedule more executable, rather than merely changing the order in which jobs are listed.

This explains why the intervention combined quality and flow methods. A sequencing optimizer cannot compensate fully for recurring material shortages or work that must repeatedly return for correction.

**Integrated release addresses departmental imbalance.** Slomp and colleagues’ low-volume, high-variety case paired levelling and CONWIP with FIFO and takt. Its dual-resource setting required attention to both staffing and machine capacity, while the combined control system improved service performance.

The lesson for electrical-equipment assembly is that release, downstream flow and labor allocation must be compatible. A department filling its own capacity can create WIP that a downstream assembly team cannot absorb. [12]

**The targeted countermeasure is coordinated flow.** Family organization reduces setup and routing complexity; pull or release limits restrain excess work; FIFO preserves an intelligible sequence; and quality-at-source reduces capacity lost to rework. These methods address distinct causes of schedule failure and should be evaluated as an operating arrangement.

### Custom lighting: expose the business-objective trade-off

**Customization changes both work and information.** Kadam’s architectural-lighting case involved make-to-order and engineer-to-order products with many configuration possibilities. The thesis identified departmental separation, independently pushed schedules, WIP accumulation, variable work content, low yields and corrective-only maintenance as contributors to poor flow.

Its proposed future state combined a dedicated continuous-flow cell where feasible, shared upstream processes, capacity-based scheduling, dynamic pitch, finite FIFO lanes and supermarkets for common items. [19]

**Maintenance was modeled as scheduled capacity consumption.** The preventive-maintenance model allocated activities across machines, technicians, shifts and days, with regular-time, overtime and allowable-downtime constraints. This is a targeted response to breakdown-driven schedule disruption.

The mechanism is not that planned maintenance eliminates all failures. It makes some capacity loss foreseeable and coordinates it with labor availability and production requirements, instead of repeatedly allowing unplanned failures to determine the schedule.

**Financial levelling created a delivery penalty.** The thesis also modeled a management requirement for nearly equal revenue output on each production day. To meet it, orders were reorganized across a production week rather than handled only by arrival order.

The proposed flow design could support an approximately 2.4-week total order lead time under FCFS. Revenue levelling increased modeled average lead time to 3.3 weeks and worst-case lead time to four weeks, compared with the existing six-week customer lead-time offer. [19]

| Scheduling scenario | Evidence status | Total order lead time | Reduction from six weeks |
|---|---|---|---|
| Existing arrangement | Case baseline | 6 weeks | 0% reference |
| Proposed flow with FCFS | Future-state estimate | About 2.4 weeks | 60% |
| Proposed flow with revenue levelling | Modeled average | About 3.3 weeks | 45% |
| Proposed flow with revenue levelling | Modeled worst case | About 4 weeks | About 33.3% |

The calculated reductions use the six-week baseline: (6 − 2.4) ÷ 6 = 60%; (6 − 3.3) ÷ 6 = 45%; and (6 − 4) ÷ 6 ≈ 33.3%. These are conditional future-state comparisons, not measured post-implementation lead times. [19]

**The objective can matter more than the algorithm.** Revenue levelling produced a smoother financial output but required some orders to wait. The thesis noted that monitoring dynamic daily financial targets could offer earlier financial visibility without imposing the same equal-revenue sequencing requirement.

For decision-makers, this is a significant counterexample to the assumption that a more optimized schedule must improve customer responsiveness. Optimization produces what the objective requests; an unsuitable objective can systematically create delay.

**Electronics takeaway.** Use exact models for hard process compatibility, coordinated lean control for assembly flow, and explicit business-objective analysis where scheduling policies can trade customer lead time for financial or utilization targets.

## Semiconductor manufacturing: address missing data before optimizing assignments

**The distinguishing problem is heterogeneous capacity.** Boydon, Wu and Wu’s 2021 study examined HMLV semiconductor assembly and testing, where machines were acquired at different capacity-expansion stages. Machines could perform similar functions while differing in efficiency, quality and product eligibility.

The setting is described as *unrelated parallel machines*: processing characteristics depend on the product-machine pairing, rather than being captured adequately by one common machine speed. [27]

### Why high mix produces a sparse scheduling dataset

**Product-machine combinations grow quickly.** Broad product variety across heterogeneous machines produces many possible combinations. Some combinations have insufficient production history to estimate processing time accurately, especially when products change quickly or have short life cycles.

This is a scheduling barrier because an optimizer needs those parameters to evaluate assignments. A nominally sophisticated scheduling method may choose the wrong machine if the underlying duration estimate is poor. [27]

**Simple pooling loses important differences.** Treating machines as interchangeable can conceal efficiency or eligibility differences. Treating every product-machine combination independently, however, leaves sparse combinations with weak estimates.

The trade-off is between statistical pooling and operational specificity. HMLV requires enough sharing of information to estimate unfamiliar combinations, without erasing the differences that determine whether an assignment is sensible.

**New equipment can change the historical relationship.** A newer machine may offer greater efficiency or quality than an older model, so historical performance from one machine cannot automatically be transferred unchanged to another. The study identifies this staged equipment procurement as a defining feature of the operating environment.

The practical implication is that data management must preserve machine identity and relevant product characteristics. An overall average processing time is too coarse when the assignment decision depends on the pairing.

### Hierarchical prediction plus stochastic optimization

**The first countermeasure estimates missing parameters.** Boydon and colleagues developed a hierarchical prediction method for mixed-dataset analysis. Its role was to generate missing production parameters, including required processing times, for subsequent scheduling optimization. [27]

The method addresses the information structure before the combinatorial scheduling problem. This is an important contrast with approaches that assume a complete, accurate processing-time matrix and begin immediately with assignment or sequencing.

**The second countermeasure retains uncertainty.** Forecast models inevitably make errors, so the study used stochastic optimization to generate robust scheduling decisions. “Stochastic” means the formulation accounts for uncertain quantities rather than treating every prediction as an exact fact.

The framework was validated using an industry dataset from a leading semiconductor assembly-and-testing company. Its documented contribution is an industry-data-tested connection between prediction and uncertainty-aware scheduling. [27]

**The combination addresses two different failures.** Prediction helps fill an incomplete parameter set. Stochastic optimization then reduces reliance on the assumption that those estimated parameters will be exactly correct. Neither step substitutes for the other.

This matters operationally because a schedule optimized around uncertain point estimates can be brittle: small forecast errors may change which machine assignment is preferable. A robust decision can be valuable even if it gives up some apparent advantage under the single most optimistic forecast.

**Eligibility still requires explicit representation.** Predicting a duration does not establish that a product is technically qualified for a machine. The study’s introduction identifies machine-eligibility constraints arising from product specifications and machine functions.

The scheduling system must therefore distinguish “estimated to be fast” from “permitted and qualified to process.” Prediction informs the optimization; it does not replace engineering constraints. [27]

### How this differs from the electronics examples

**Semiconductor scheduling is partly an inference problem.** In the PCB pressing example, the main contribution was a better formulation of explicit compatibility and shared-resource constraints. In semiconductor assembly and testing, a central difficulty was constructing credible inputs for heterogeneous assignments.

The practical contrast is not “exact optimization versus machine learning.” The semiconductor framework combines prediction with optimization, while the PCB framework benefits from a process whose main restrictions can be represented directly. Different information conditions explain the different method choices.

**Bottleneck-aware release remains relevant.** Gilland’s earlier Intel-patterned cell study examined material-release rules under single and multiple bottlenecks. It provides a complementary control perspective: even with suitable processing estimates and assignments, the quantity and timing of released work affect output and WIP. [9]

Thus, prediction, stochastic scheduling and release control can operate at different levels of the same production system. Better parameter estimates improve assignment decisions; workload-aware release prevents those decisions from being overwhelmed by uncontrolled congestion.

**The recommendation changes with data maturity.** If product-machine histories become sufficiently rich and equipment more homogeneous, the incremental value of a hierarchical prediction layer may diminish. If uncertainty remains substantial, maintaining uncertainty-aware optimization remains useful even with more observations.

Conversely, when products or equipment change faster than the data can represent, relying heavily on historical averages becomes less attractive. Engineering eligibility, parameter updating and robustness then become more important.

**Semiconductor takeaway.** Treat HMLV scheduling as a combined data-estimation, uncertainty and resource-allocation problem; improving the optimizer alone does not resolve an incomplete product-machine information base.

**Additional documented evidence**

HMLV assembly/testing has diversified products, unrelated parallel machines and incomplete product–machine data; hierarchical prediction fills missing processing times and stochastic robust scheduling absorbs forecast error, validated on an industry dataset. [101] CNN-A3C handles urgent orders and uncertain times by tuning CONWIP maximum-WIP/release proportion and dispatching weights; its 2022 scenario 4 improved urgent-order ODR_u by 14.81% and mean cycle time by 52% versus rules. [156] Cluster/etch scheduling faces parallel wafers, failures, unstable chambers, limited chambers/robots, variable recipe/WAC/transfer times, nonlinear throughput and restricted data. KNN-JIT1 control changed JIT1 from 30 to 58 and throughput from 37.06 to 38.20 (process-time 195.00; WAC-time 50.00; idealized maximum 40.14; Pearson 0.989; RMSE 3.28). [222] A 2022 review of 181 RL/PPC articles places scheduling first; semiconductor RL targets delivery, makespan, utilization, lead time, violations and WIP. [181][182] AWS adds shared-hoist, minimum/maximum-window and zero-wait constraints, but that passage reports no semiconductor countermeasure. [186]

## Overall industry-analyst judgment

**The strongest development is coordinated flexibility.** Across 2000–October 2022, successful HMLV thinking increasingly joined physical organization, workload control, optimization and information quality. Cellular Manufacturing reduces coordination complexity; FMS provides adaptable capability; Flow Management connects shared resources; and CONWIP or POLCA regulates the work allowed to use them.

**Method choice should follow the failure mechanism.** Where stable families exist, cells and family levelling can simplify production. Where technical changeovers and routing alternatives justify investment, FMS can provide useful flexibility. Where queues dominate, release and buffer policies deserve priority. Where assignments depend on uncertain or missing data, prediction and robust scheduling become central.

**Digital sophistication does not replace operational fit.** The recent literature’s contribution is the ability to observe, model and adapt production more effectively. The 2022 industrial decision-support study explicitly retained production planners and their experience, while combining simulation and learning to improve the choices available to them. [7]

**Measurement basis matters throughout.** The stage hotspots are a qualitative synthesis of dated studies, not keyword-frequency rankings. The 40% and 20% industry proportions are calculated estimates from the ten named application studies, using the stated broad electrical/electronics grouping and separate semiconductor and photonics classifications. Field observations, simulation results, computational improvements and conditional future-state estimates measure different outcomes; the RL examples include general shop-scheduling research. Case conditions and model assumptions determine transferability, while a market-adoption ranking would depend on comparable industrial activity denominators.

**The final judgment is conditional but clear.** HMLV does not require a single replacement for mass-production methods. It requires selective standardization where repetition genuinely exists, protected flexibility where it does not, and scheduling controls that respond to the real distribution of workload, capability and uncertainty.

## References

[1] <http://rave.ohiolink.edu/etdc/view?acc_num=osu1211984904> HMLV layout alternatives; Functional versus cellular layouts; Cellular-layout risks in HMLV
[2] <https://doi.org/10.2507/daaam.scibook.2021.12> FMS definition and design; Group Technology within FMS; Integrated FMS spatial and logistics design; FMS economic trade-offs
[3] <https://doi.org/10.1109/ieem.2008.4738054> Peng et al., 2008; Mathematical flow-path design; Shared-machine flow-path optimization
[4] <https://eprints.lancs.ac.uk/id/eprint/79388/1/Thurer_Stevenson_Protzman_PPC.pdf> CONWIP operating mechanism; Standard CONWIP applicability conditions
[5] <https://pubsonline.informs.org/doi/10.1287/msom.1070.0174> Load-Based POLCA, 2008; POLCA suitability and definition; Load-Based POLCA framework and application
[6] <https://doi.org/10.3390/pr8080912> HMLV scheduling definition; Real-time HMLV scheduling, 2020; Industry 4.0 scheduling architecture; MB–GA and software automation; MB–GA decision architecture;…
[7] <https://doi.org/10.3390/app12115618> Hungarian HMLV factory case; Delivery-performance trade-offs; Model- and data-driven delivery support, 2022; HMLV equipment and cyber-physical research context…
[8] <https://doi.org/10.1109/etfa.2008.4638371> Dynamic operations and manpower scheduling; 2008 industrial scheduling problems; Early scheduling problem; Precision engineering
[9] <https://doi.org/10.1080/09537280110069784> Gilland, 2002; Bottleneck-aware release simulation; Gilland; Semiconductor-related release-control study
[10] <https://sfb876.tu-dortmund.de/en/PublicPublicationFiles/birkmann_deuse_2007a.pdf> Birkmann and Deuse, 2007; Family-based production levelling; Levelling and standardization boundary; Practical family-classification issues
[11] <https://doi.org/10.1109/tsmca.2009.2029557> Neoh et al., 2009/2010; LECO product-mix optimization; Layered optimization; Layered genetic and swarm optimization
[12] <https://doi.org/10.1080/09537280903086164> Slomp et al., 2009; Integrated lean production control; Integrated CONWIP application; Slomp et al.; Integrated control in a dual-resource environment
[13] <https://link.springer.com/article/10.1007/s11465-008-0083-5> Constraint-managed virtual flow paths; HMLV flow-management framework; Path-specific constraint management
[14] <https://doi.org/10.1080/09537280903034297> POLCA implementation research; POLCA push-pull logic
[15] <https://doi.org/10.1080/00207540902998323> Decentralized CONWIP balancing; Adaptive CONWIP loading rates
[16] <https://doi.org/10.3926/jiem.1248> CONWIP–POLCA comparison; Photonics comparison findings; Photonics
[17] <https://www.sciopen.com/local/article_pdf/10.23919/CSMS.2021.0027.pdf> Reinforcement-learning scheduling review; Scheduling algorithm taxonomy; Exact-method scaling; RL mechanisms and classification; Value- and policy-based RL
[18] <https://doi.org/10.1080/09537287.2020.1782094> Systematic HMLV lean review
[19] <https://spectrum.library.concordia.ca/id/eprint/990372/1/Kadam_MASc_W2022.pdf> Routing- and work-content-based family formation; Continuous-flow and shared-process design; FIFO versus supermarket application; Scheduling to capacity and dy…
[20] <https://etd.ohiolink.edu/acprod/odb_etd/ws/send_file/send?accession=osu1211984904&disposition=inline> Modular and hybrid layout methods
[21] <https://doi.org/10.5267/j.ijiec.2018.10.002> Merge-point synchronization; HMLV CONWIP parameter study; VSM and CONWIP parameter setting; CONWIP-favoring comparison account; Aggregate-model findings and in…
[22] <https://doi.org/10.1590/0103-6513.20190159> Centralized release extension; POLCA simulation results; POLCA card-acquisition rules
[23] <https://journals.sagepub.com/doi/10.1177/16878132221086120> Rule-based scheduling comparison; GA and online response comparison; RL training comparison; Machine-failure scheduling scenario
[24] <https://vbn.aau.dk/en/publications/line-scheduling-optimization-in-low-volume-high-mix-flow-shop-ass/> DES–GA with Palmer heuristic
[25] <https://www.mdpi.com/2227-7390/9/21/2653> PCB pressing MILP; PCB scheduling; PCB pressing problem; PCB compatibility and oven constraints; Model 2 computational result
[26] <https://dspace.mit.edu/handle/1721.1/139593> Rodriguez; PSI Control Solutions case
[27] <https://doi.org/10.1109/case49439.2021.9551555> Boydon, Wu and Wu; Semiconductor scheduling environment; Incomplete product-machine production data; Hierarchical processing-time prediction; Stochastic optimi…
[28] <https://buildamtech.com/high-mix-low-volume-manufacturing/>
[29] <https://doi.org/10.1108/ijlss-07-2013-0042>
[30] <https://www.3erp.com/blog/high-mix-low-volume-manufacturing/>
[31] <https://buildamtech.com/podcast/high-mix-low-volume-hmlv-is-the-future-of-manufacturing/>
[32] <https://doi.org/10.3390/pr8080912>
[33] <https://www.sigmadzn.com/solutions/high-mix-low-volume-hmlv-manufacturing>
[34] <https://link.springer.com/chapter/10.1007/978-3-031-18326-3_24>
[35] <https://discovery.researcher.life/topic/high-mix-low-volume/17726422?page=1&topic_name=High-mix%2C+Low-volume>
[36] <https://www.mdpi.com/2227-9717/8/8/912>
[37] <https://www.diva-portal.org/smash/get/diva2:1442082/FULLTEXT01.pdf>
[38] <https://www.diva-portal.org/smash/get/diva2:1029112/FULLTEXT02>
[39] <https://etd.ohiolink.edu/acprod/odb_etd/ws/send_file/send?accession=osu1211984904&disposition=inline>
[40] <https://www.olanabconsults.com/articles/managing-material-flow-in-high-mix-low-volume-hmlv-manufacturing>
[41] <https://etd.ohiolink.edu/acprod/odb_etd/ws/send_file/send?accession=akron1564787755980795&disposition=inline>
[42] <https://uh-ir.tdl.org/server/api/core/bitstreams/84dd73d1-a583-433d-b32a-52490f986056/content>
[43] <https://studylib.net/doc/10834747/>
[44] <https://rave.ohiolink.edu/etdc/view?acc_num=osu1211984904>
[45] <https://doi.org/10.26552/com.c.2000.1.39-44>
[46] <https://dlnext.acm.org/doi/10.1016/S0360-8352%2802%2900017-7>
[47] <https://www.chegg.com/homework-help/questions-and-answers/flexible-manufacturing-systems-fms-11-define-flexible-manufacturing-system-12-discuss-thre-q169455409>
[48] <https://roboticsbiz.com/flexible-manufacturing-system-fms-explained/>
[49] <https://doi.org/10.20868/upm.thesis.57901>
[50] <https://doi.org/10.1023/a:1007642413799>
[51] <https://doi.org/10.22201/icat.24486736e.2022.20.1.1335>
[52] <https://doi.org/10.1080/00207543.2022.2105763>
[53] <https://www.sciencedirect.com/science/article/abs/pii/S0925527307001065>
[54] <http://hdl.handle.net/1822/19121>
[55] <https://www.novapublishers.com/wp-content/uploads/2018/10/Cellular-Manufacturing-Systems-CH-1.pdf>
[56] <https://www.epa.gov/sustainability/environmental-professionals-guide-lean-and-six-sigma-chapter-2>
[57] <https://doi.org/10.1080/00207540050028124>
[58] <https://doi.org/10.1016/s0360-8352(00)00074-7>
[59] <https://www.encyclopedia.com/management/encyclopedias-almanacs-transcripts-and-maps/cellular-manufacturing>
[60] <https://ietresearch.onlinelibrary.wiley.com/doi/full/10.1049/cim2.12053>
[61] <https://www.sciencedirect.com/science/article/abs/pii/S2213846323000044>
[62] <https://www.taylorfrancis.com/chapters/edit/10.1201/9781003360001-1/introduction-flexible-manufacturing-system-industry-4-0-darshan-srivastav-arun-kumar-kushwaha-mohd-faizan-vipin-kumar-sharma>
[63] <https://technav.ieee.org/topic/flexible-manufacturing-systems/>
[64] <https://en.wikipedia.org/wiki/Material_flow_management>
[65] <https://mfr.edp-open.org/articles/mfreview/full_html/2023/01/mfreview230009/mfreview230009.html>
[66] <https://doi.org/10.1108/jm2-02-2022-0035>
[67] <https://doi.org/10.1016/j.procir.2022.05.180>
[68] <https://doi.org/10.1109/case48305.2020.9216985>
[69] <https://www.sciencedirect.com/science/article/abs/pii/S0925231209004056>
[70] <https://doi.org/10.35378/gujs.883367>
[71] <https://cpi2015.sciencesconf.org/77248/Evaluationflexibility_Modifications.pdf>
[72] <https://doi.org/10.32920/19874092.v1>
[73] <https://doi.org/10.5267/j.ijiec.2022.2.002>
[74] <https://doi.org/10.1109/smc53654.2022.9945585>
[75] <https://doi.org/10.1080/00207543.2021.1948134>
[76] <https://doi.org/10.1142/s0219686722500287>
[77] <https://sixsigmadsi.com/flexible-manufacturing-system-fms/>
[78] <https://doi.org/10.1007/978-1-4613-1187-4_10>
[79] <https://doi.org/10.1080/0020754021000032040>
[80] <https://www.mdpi.com/2227-9717/9/8/1391>
[81] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5338791/>
[82] <https://www.research-collection.ethz.ch/server/api/core/bitstreams/facfd0cc-b77f-45cb-9412-4a20ddf2d173/content>
[83] <https://link.springer.com/article/10.1007/s12351-022-00732-y>
[84] <http://www.ieomsociety.org/ieom2020/papers/604.pdf>
[85] <https://resolver.tno.nl/uuid:f605d9ab-9248-4c9c-b16d-9f1c85ee34eb>
[86] <https://doi.org/10.1109/tsmca.2009.2029557>
[87] <https://tdl-ir.tdl.org/items/d60fec3e-07d3-4615-9a06-436842284699/full>
[88] <https://research.tue.nl/en/publications/a-simulation-based-approach-to-design-an-automated-high-mix-low-v/>
[89] <https://www.mdpi.com/2076-3417/12/11/5618>
[90] <https://spectrum.library.concordia.ca/id/eprint/990372/>
[91] <https://www.jstage.jst.go.jp/article/jamdsm/17/1/17_2023jamdsm0008/_pdf/-char/en>
[92] <https://www.just-plan-it.com/smb-production-scheduling-blog/software-for-hmlv-production-scheduling-should-includes-these-functions>
[93] <https://www.jstage.jst.go.jp/article/jima/73/2E/73_136/_pdf>
[94] <https://www.wseas.us/e-library/conferences/2011/Barcelona/MEQAPS/MEQAPS-01.pdf>
[95] <https://growingscience.com/ijiec/Vol10/Vol10No2.html>
[96] <https://vbn.aau.dk/ws/portalfiles/portal/771000949/1-s2.0-S221282712401309X-main.pdf>
[97] <https://spectrum.library.concordia.ca/id/eprint/990372/1/Kadam_MASc_W2022.pdf>
[98] <https://doi.org/10.1109/wsc57314.2022.10015489>
[99] <https://informs-sim.org/wsc22papers/180.pdf>
[100] <https://pdfs.semanticscholar.org/cc88/8084138d7739546026445338528070aa807b.pdf>
[101] <https://doi.org/10.1109/case49439.2021.9551555>
[102] <https://www.academia.edu/26211462/Optimization_of_Product_Mix_Planning_in_High_Mix_Low_Volume_Industries_Using_Genetic_Algorithms>
[103] <https://en.wikipedia.org/wiki/Reinforcement_learning>
[104] <https://doi.org/10.1109/ro-man53752.2022.9900670>
[105] <https://doi.org/10.5267/j.ijiec.2014.8.003>
[106] <http://arxiv.org/abs/1802.03928v1>
[107] <https://www.sciencedirect.com/science/article/abs/pii/S036083522100098X>
[108] <https://doi.org/10.1016/j.cor.2022.105880>
[109] <https://doi.org/10.1109/etfa.2011.6059200>
[110] <https://doi.org/10.1088/1757-899x/1041/1/012046>
[111] <https://doi.org/10.1016/j.ifacol.2022.09.606>
[112] <https://digital-library.theiet.org/doi/full/10.1049/cim2.12061>
[113] <https://doi.org/10.3390/machines10121195>
[114] <https://arxiv.org/abs/2210.03674>
[115] <https://doi.org/10.1109/tsm.2018.2792312>
[116] <https://www.ijraset.com/research-paper/maximizing-manufacturing-efficiency-through-linear-programming>
[117] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9483369/>
[118] <https://doi.org/10.1109/wsc48552.2020.9383887>
[119] <https://doi.org/10.1145/3570773.3570812>
[120] <https://doi.org/10.1609/icaps.v32i1.19852>
[121] <https://link.springer.com/content/pdf/10.1007/s10696-021-09443-6.pdf?error=cookies_not_supported&code=d7ccfa1f-3c79-42a8-9a70-916bb9492299>
[122] <https://doi.org/10.1021/ie010009p>
[123] <https://www.techscience.com/iasc/v37n2/53243/html>
[124] <https://egon.cheme.cmu.edu/Papers/TankFarmTerrazasGrossmannWassick.pdf>
[125] <https://doi.org/10.1007/978-3-658-39179-9_3>
[126] <https://people.cs.nott.ac.uk/pszeo/docs/publications/ChapterGPasHH09.pdf>
[127] <https://doi.org/10.14743/apem2022.1.420>
[128] <https://www.mdpi.com/2227-7390/9/21/2653>
[129] <https://avesis.yildiz.edu.tr/yayin/3b174e72-8fd4-453b-81fe-08412a94dcf0/an-application-of-effective-genetic-algorithms-for-solving-hybrid-flow-shop-scheduling-problems/document.pdf>
[130] <https://www.ias.ac.in/article/fulltext/sadh/038/03/0421-0428>
[131] <http://hdl.handle.net/11250/2623337>
[132] <https://link.springer.com/article/10.1007/s00170-022-09188-y?code=0c1acbf9-0283-4b06-9b6f-d578e64d7ac1&error=cookies_not_supported>
[133] <https://doi.org/10.1080/00207540701581809>
[134] <https://doi.org/10.17093/aj.2015.3.2.5000140019>
[135] <https://pure.rug.nl/ws/portalfiles/portal/119058879/An_integrated_approach_for_the_cell_formation_and_layout_design_in_cellular.pdf>
[136] <http://www.journal-aprie.com/article_131034_79b88dd21974bdbc2ef2d713e77e7072.pdf>
[137] <https://www.ijamtes.org/gallery/287.%20sep%20ijmte%20-%201061.pdf>
[138] <https://mdpi-res.com/d_attachment/sustainability/sustainability-13-03452/article_deploy/sustainability-13-03452-v2.pdf?version=1616567011>
[139] <https://doi.org/10.24050/reia.v19i38.1543>
[140] <https://pure.tue.nl/ws/files/2351032/338434.pdf>
[141] <https://dept-mechanical-engineering.s3.ap-south-1.amazonaws.com/NBA2025/C6/6.1/6.1.6.1/CAYM3_(2021-22)/22.pdf>
[142] <https://sage.cnpereading.com/doi/10.1177/09544054211044660>
[143] <https://doi.org/10.3390/app13021125>
[144] <https://link.springer.com/article/10.1007/s40092-017-0239-1>
[145] <https://www.mdpi.com/2227-9717/11/4/1297>
[146] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12859057/>
[147] <https://arxiv.org/html/2310.03195>
[148] <https://doi.org/10.1023/b:apin.0000011143.95085.74>
[149] <https://link.springer.com/article/10.1007/s10696-012-9143-6>
[150] <https://itea4.org/project/workpackage/document/download/8969/AISSI_Deliverable_D11_Updated_SotA_v1_2024-06-18.pdf>
[151] <https://link.springer.com/article/10.1007/s10845-025-02585-6>
[152] <https://pmc.ncbi.nlm.nih.gov/articles/PMC13189325/>
[153] <https://ieeexplore.ieee.org/abstract/document/10847828>
[154] <https://www.sciencedirect.com/science/article/abs/pii/S0360835220300814>
[155] <https://journal.kalibra.or.id/index.php/reswara/article/download/424/384>
[156] <https://link.springer.com/article/10.1007/s40747-022-00844-0>
[157] <https://doi.org/10.2507/daaam.scibook.2021.01>
[158] <https://www.sciopen.com/local/article_pdf/10.23919/CSMS.2021.0027.pdf>
[159] <https://doi.org/10.1109/access.2022.3179711>
[160] <https://doi.org/10.1080/00207543.2017.1281462>
[161] <https://www.sciencedirect.com/science/article/abs/pii/S0360835220301716>
[162] <https://doi.org/10.24425/mper.2022.142384>
[163] <http://eprints.usm.my/46119/1/Joshua%20AL%20Jaya%20Prakash24.pdf>
[164] <https://doi.org/10.3390/su151713012>
[165] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11232579/>
[166] <https://arxiv.org/html/2409.11933v1>
[167] <https://arxiv.org/html/2504.07779v2>
[168] <https://web.cs.dal.ca/~mheywood/Thesis/UMukhammadnaim.pdf>
[169] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9157010/>
[170] <https://doi.org/10.1155/2022/9954518>
[171] <https://www.mdpi.com/2227-7390/9/6/653>
[172] <https://doi.org/10.3390/math9060653>
[173] <https://doi.org/10.1007/s11740-022-01152-9>
[174] <http://tgait.de/fileadmin/user_upload/documents/Gabel_Riedml_IJPR-11.pdf>
[175] <https://doi.org/10.1109/tra.2003.814512>
[176] <https://informs-sim.org/wsc12papers/includes/files/con358.pdf>
[177] <https://www.tandfonline.com/doi/full/10.1080/0305215X.2022.2124406>
[178] <https://doi.org/10.1109/tepm.2009.2019340>
[179] <https://doi.org/10.1115/detc2001/cie-21281>
[180] <https://www.tandfonline.com/doi/full/10.1080/00207543.2018.1554918>
[181] <https://www.tandfonline.com/doi/full/10.1080/00207543.2022.2104180>
[182] <https://repo.uni-hannover.de/bitstreams/918e0eda-634a-4f72-8b86-097898179bff/download>
[183] <https://ercim-news.ercim.eu/en122/special/reinforcement-learning-for-short-term-production-scheduling-with-sequence-dependent-setup-waste>
[184] <https://www.mdpi.com/1999-4893/17/8/343>
[185] <https://doi.org/10.1007/s10951-010-0222-9>
[186] <https://44jaiio.sadio.org.ar/sites/default/files/sii148-157.pdf>
[187] <https://lin.engin.umich.edu/wp-content/uploads/sites/551/2021/10/Mixed-Integer-Linear-Programming-in-Process-Scheduling.pdf>
[188] <https://link.springer.com/content/pdf/10.1007/s10696-012-9143-6.pdf>
[189] <https://www.sciencedirect.com/science/article/abs/pii/S0360835220303909>
[190] <https://experts.mcmaster.ca/scholarly-works/2169909>
[191] <https://ph02.tci-thaijo.org/index.php/ienj/article/view/242053>
[192] <https://link.springer.com/article/10.1007/s10845-022-01922-3>
[193] <https://doi.org/10.58837/chula.the.2021.1010>
[194] <https://www.youtube.com/watch?v=aaGESG8kolc>
[195] <https://sage.cnpereading.com/doi/10.1177/09544054251395468>
[196] <https://doi.org/10.1109/picmet.2009.5262198>
[197] <https://odr.chalmers.se/bitstreams/8d0a4da3-bd8d-4fb2-8977-b2a1d9a38ea1/download>
[198] <https://doi.org/10.1016/s0925-5273(00)00089-x>
[199] <https://doi.org/10.1109/robot.1992.220193>
[200] <https://repository.up.ac.za/bitstreams/4592e33a-f27f-47c5-be82-deb7c1cf516a/download>
[201] <https://dataintelo.com/report/global-flexible-manufacturing-system-market>
[202] <https://doi.org/10.1080/00207543.2022.2057256>
[203] <https://hal.science/hal-01988143/document>
[204] <https://doi.org/10.3233/atde220613>
[205] <https://doi.org/10.1080/00207543.2018.1551638>
[206] <https://uhy-us.com/media/u51fkmws/aerospace-analysis_2025_08-pages.pdf>
[207] <https://www.census.gov/naics/reference_files_tools/2022_NAICS_Manual.pdf>
[208] <https://www2.census.gov/programs-surveys/cps/methodology/IndustryCodes_Jan2025.pdf>
[209] <https://ncses.nsf.gov/pubs/nsb20226/assets/technical-appendix/nsb20226-technical-appendix.pdf>
[210] <https://gov.texas.gov/uploads/files/business/Sector_Profile_Advanced_Manufacturing.pdf>
[211] <https://www.federalregister.gov/documents/2022/10/13/2022-21658/implementation-of-additional-export-controls-certain-advanced-computing-and-semiconductor>
[212] <https://doi.org/10.1080/09537287.2021.1888159>
[213] <https://www.semiconductors.org/wp-content/uploads/2024/10/SIA_2024_State-of-Industry-Report.pdf>
[214] <https://www.nist.gov/semiconductors>
[215] <https://doi.org/10.1016/j.matpr.2020.10.217>
[216] <https://www.42-q.com/blog/news/how-mes-supports-medical-device-manufacturing/>
[217] <https://www.criticalmanufacturing.com/industries/medical-device-manufacturing/>
[218] <https://rsisinternational.org/journals/ijriss/articles/bibliometric-insights-into-manufacturing-flexibility-scholarly-output-hot-topics-and-research-gap/>
[219] <https://www.sciencedirect.com/science/article/pii/S1000936120305987>
[220] <https://www.iaeng.org/publication/IMECS2011/IMECS2011_pp1182-1187.pdf>
[221] <https://pure.manchester.ac.uk/ws/portalfiles/portal/210005140/Kazantsev_et_al_Investigating_Barriers_to_Demand_driven_SME_Collaboration_in_Low_volume_High_variability_Manufacturing_AAM.pdf>
[222] <https://www.mdpi.com/2076-3417/12/15/7519>
[223] <https://re.public.polimi.it/retrieve/e0c31c0f-67ef-4599-e053-1705fe0aef77/GA2018_ProregioPolimiKit_preprint.pdf>
