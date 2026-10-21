# Digital Twins for Health: Applications and Major Research Centers as of Early 2024

**Specialized twins already deliver value.** By early 2024, digital-twin methods supported concrete healthcare decisions, particularly coronary-flow assessment, medical-device engineering, patient-specific procedure planning, and laboratory bioprocess control. However, the field comprised several different technologies: individualized predictive models, operational simulations, digital shadows, and actively coupled twins—not a single, fully developed “virtual patient.” HeartFlow illustrates established clinical use, while BioDT demonstrates experimental sensor-to-model-to-control integration. [1][2]

**The institutional landscape is distributed.** Important programs include Europe’s EDITH/Virtual Physiological Human Institute ecosystem, the global Living Heart collaboration, Cleveland Clinic–MetroHealth’s population-health research, China’s Jiangnan University biomanufacturing work, and the UK–Indonesia healthcare-resilience partnership. The comparison below uses **31 March 2024** as the operational cutoff; entries marked † are supplementary technical or institutional profiles, kept separate from the dated early-2024 deployment record.

| Application direction | Representative cases and organizations | Main data or technology | Decisive evidence | Practical judgment |
|---|---|---|---|---|
| Hospital Management and Care Coordination | Decision Lab/AnyLogic; Saint-Louis AP-HP/Dassault | Patient-flow simulation; scanned facilities; airflow models | Two hospitals and 75 locations in the NHS model | Useful operational experimentation; distinguish simulations from live twins |
| Medical Device Design | Medtronic; FEops; HeartFlow; Living Heart | Finite-element analysis; CT-derived physiology | HeartFlow: 83.5% sensitivity and 85.8% specificity, per vessel | Strong engineering applications; specialized clinical deployment |
| Biomarker and Drug Discovery | Li et al.; Genzeva/LumaGene/RYLTI; Schmidt et al. | Single-cell networks; multiomics; computational pathology | Allergic-rhinitis framework: 16 patients and 14 controls | Primarily target, biomarker, and stratification research |
| Biomanufacturing | Jiangnan University/T&J Bioengineering; Körber/Intravacc† | Process sensors; kinetic models; adaptive feeding | BioDT: 14.8% higher cell density in an illustrative feeding experiment | A concrete route to closed-loop process optimization |
| Surgical Planning | Twente/MST; Medics3D iKidney; Atlas Meditech | CT/MRI models; simulated fluoroscopy; AR | SI-joint series: 10 patients, 30 implants | Clinically useful planning; often a precursor to an active twin |
| In-silico Clinical Trials | Unlearn; Schmidt et al.; Medidata/Dassault | Generative models; matched controls; mechanistic physiology | Unlearn released three disease-specific generators in February 2024 | Complement trial design and analysis; assess endpoint credibility |
| Personalized Medicine | HeartFlow; cardiac CMR/ECG pipeline; Turing PAH project† | Individual anatomy, physiology, monitoring, and model fitting | January cardiac demonstration reproduced ECGs at correlations of 0.93 and 0.89 | Narrow, decision-specific personalization is the clearest pathway |
| Wellness | Arivale analysis; Miami MILBox†; Mount Sinai DigiTwin† | Multiomics; wearables; home and environmental sensors | Arivale analysis: 1,131 six-month and 639 one-year records | Predictive research is ahead of demonstrated preventive benefit |
| Major Research Centers | EDITH; Living Heart; Cleveland–MetroHealth; Jiangnan; London–UGM | Shared infrastructure, organ models, process twins, and health-system models | EDITH: 19 partners; Cleveland registry: over 250,000 patients | Compare research roles and objectives, not an unsupported league table |

The numerical anchors come from the respective [3][4][5][2][6][7][8], and Arivale analysis [9].

**The report answers two questions.** Part One explains the eight requested application directions through named cases: what is represented, which organizations and technologies are involved, how information updates the model, and what decision follows. Part Two compares research centers and consortia using the four requested columns, then explains which organizations are most relevant to different research interests.

## Part One: Key Application Areas

### What qualifies as a digital twin for health?

**Individualization is the central requirement.** Viceconti and colleagues’ January 2024 position paper defines a Digital Twin in Healthcare as an individual- or patient-specific predictive model informed by personal patient data at least once during its lifecycle. Under that definition, continuous sensor streaming is useful in some applications but is not mandatory in every application. HeartFlow, for example, personalizes a physiological model from a particular patient’s medical images and uses it to support a particular clinical decision. [1]

**Feedback identifies the fuller implementation.** A stricter cyber-physical definition requires continuous or periodic information exchange between the real system and its virtual counterpart. New measurements update the model; the model forecasts outcomes or evaluates interventions; clinicians, operators, or automated controls act on those outputs. Subsequent observations then reveal whether the predicted response occurred. [10]

These established distinctions help interpret the applications consistently:

| Representation | Relationship with the real system | Main capability | Healthcare example |
|---|---|---|---|
| Individualized computational model | Personalized from patient or process data | Predict a defined quantity or intervention response | HeartFlow coronary-flow assessment |
| Static anatomical model | Reconstructs anatomy at imaging time | Visualize, measure, and plan spatial relationships | CT-derived surgical planning |
| Digital shadow | Receives information from the physical system | Track state and forecast operations | Workflow or bioprocess monitoring |
| Actively coupled digital twin | Updates its model and supports feedback action | Adapt decisions or execute control | BioDT automated glucose feeding |
| Population-health twin | Represents communities or groups | Explore public-health scenarios | Cleveland Digital Twin Neighborhoods |

The model–shadow–twin distinction is explicitly developed in the biomanufacturing literature [11]. Population-health twins remain relevant to healthcare, although they fall outside Viceconti and colleagues’ narrower individual-patient definition.

**A dashboard is not a twin.** An electronic health record stores observations; a dashboard displays them; a three-dimensional reconstruction represents anatomy. A digital-twin application adds a model of the represented system and uses that model to estimate an otherwise difficult-to-observe state, forecast change, or compare possible actions. Combining more data sources does not, by itself, establish that predictive or intervention-testing capability.

**The decision determines necessary complexity.** A model for selecting a coronary diagnostic pathway needs credible coronary physiology, not a complete molecular representation of the patient. A bioreactor twin may need frequent updates because cells consume nutrients continuously, whereas a preoperative model can be valuable when personalized once from imaging. The relevant comparison is therefore whether the model is sufficiently accurate, timely, and individualized for its intended decision—not whether it contains the largest possible collection of data. [1]

### 1. Hospital Management and Care Coordination

**Operational decisions are the clearest application.** Hospital-level twins and their precursors let administrators test capacity, staffing, scheduling, layout, and patient-flow changes before disrupting actual care. The examples differ substantially: Decision Lab models an entire hospital network, Cranfield and Simul8 examine recorded workflows, and Saint-Louis Hospital uses a facility-specific airflow model for infection-risk awareness.

| Specific application case | Companies and organizations | Projects or key technologies | How the representation supports decisions | Status or reported scale |
|---|---|---|---|---|
| Gloucestershire hospital operations | Decision Lab; AnyLogic; NHS trust | Discrete-event and agent-based simulation | Test demand, queues, beds, wards, and emergency pathways | Two hospitals; 75 locations; twin foundation |
| Bedfordshire workflow optimization† | Cranfield University; Simul8; Bedfordshire Hospitals | DASHclinic; AI-assisted historical-data analysis | Examine rotas, appointment order, cancellations, and equipment | Four-month digital-shadow pilot |
| Dialysis-unit infection-risk visualization | Dassault Systèmes; Saint-Louis Hospital AP-HP | 3DEXPERIENCE; SIMULIA; 3D scanning; AR | Compare airflow under alternative layouts and ventilation | February 2024; unit serving 50 people weekly |
| Multisource care coordination† | Open Health Network; University of Miami; AWS | PatientSphere 2.0; cloud data lake; EHR integration | Connect patient information, research models, and care-team communication | MILBox research infrastructure |

The cases are described by AnyLogic [3], Cranfield University [12], Dassault Systèmes [13], and the University of Miami [14].

**Decision Lab models interacting services.** Its AnyLogic model covered Cheltenham General Hospital and Gloucestershire Royal Hospital, encompassing 75 units and buildings. Discrete-event simulation represented processes within and between facilities, while agent-based modeling represented patient behavior across elective and non-elective pathways. The case was presented at the AnyLogic Conference in 2022. [3]

**The benefit is system-wide experimentation.** A hospital can use this representation to examine winter-demand peaks, the addition of a ward, bed utilization, queues, and emergency-department performance. These variables interact: opening capacity in one location may simply move a bottleneck elsewhere. Representing connected pathways makes the model more useful than considering each department’s utilization independently.

**The model precedes a live twin.** AnyLogic’s account explicitly describes the simulation as the foundation for a future digital twin. Its demonstrated function is scenario testing against a representation of the hospital system. Connecting that model to continually refreshed admissions, discharge, staffing, and equipment information would change its role from planning support toward operational forecasting. [3]

**Bedfordshire starts with recorded workflow.** Cranfield University, Simul8, and Bedfordshire Hospitals NHS Foundation Trust used historical information from DASHclinic, a queue-management application used by the hospitals since 2022. The four-month pilot, funded through Innovate UK’s Accelerated Knowledge Transfer Scheme, used AI to assist interpretation of treatment-pathway and movement data. Its output was described as a digital shadow. [12]

**Scheduling is the immediate decision.** The model examines doctors’ and nurses’ rotas, appointment order, scheduling and cancellations, and equipment availability. Unlike the broader AnyLogic network model, this approach begins with observed workflow records and asks how the existing service could be rearranged. Its proposed next step is a simulation-powered twin using real-time data to anticipate future workflow problems.

**Saint-Louis models the physical environment.** On 27 February 2024, Dassault Systèmes described a virtual twin of the dialysis unit at Saint-Louis Hospital AP-HP in Paris, where 50 people received dialysis each week. Blueprints and an on-site three-dimensional scan established the unit’s geometry; SIMULIA modeled how viral particles could circulate through that space. [13]

**Airflow simulation informs practical choices.** The scenarios varied ventilation, equipment and patient locations, masks, breathing, and airflow rates. Augmented reality—digital information overlaid on the real environment—allowed physicians and nurses to view the modeled circulation in the actual unit. The reported application was a learning and risk-awareness experience for staff caring for immunocompromised patients, rather than a measured infection-reduction intervention.

**PatientSphere supplies the coordination layer.** Open Health Network’s PatientSphere 2.0 integrates information from multiple sources and supports communication between patients and broad care teams. In the Miami MILBox architecture, it supports smartphone access, cloud acquisition, analysis, and construction of the individual research algorithm, while TheMIL and AWS develop remote monitoring and an EHR-connected healthcare data lake. The university describes PatientSphere as HIPAA-compliant. [14]

**Integration and simulation solve different problems.** PatientSphere addresses fragmented information and communication; AnyLogic and Simul8 address operational consequences; the Saint-Louis model addresses physical exposure pathways. These capabilities can complement one another, but a shared patient-data platform should not be treated as proof that a predictive twin has already improved coordination.

**The practical takeaway is operational specificity.** Hospital twins are most actionable when linked to a defined decision—such as bed allocation, appointment sequencing, or ventilation—and judged against the corresponding operational or patient outcome.

**Additional documented evidence**

**Scope and documented cases**

Within the report’s eight-direction taxonomy, **Hospital Management and Care Coordination** covers system- and process-level twins of hospitals, departments, patient pathways, staffing, equipment, resources, and workflows. At the early-2024 cutoff, the evidence base was still emerging: a rapid review covered **17 health-care-system digital-twin studies published from January 2002 to January 2022**, identifying four functions—safety management, information management, health management and well-being promotion, and operational control; **9 of the 17 studies** concerned operational control [101]. The defining value is the loop from operational data to a virtual model, simulation or prediction, and a management action—not merely displaying an EHR or running an unconnected queueing model.

| Named case | Company, project or institution | Digital-twin use and reported or intended result |
|---|---|---|
| **Capacity Command Center** | **GE Healthcare** and Johns Hopkins Hospital, Baltimore | Digital twins of patient pathways combine simulation and analytics to predict patient activity and plan hospital capacity according to demand; the source reports intended improvements in service, safety, patient experience, and activity volume [123]. |
| **HospiT’Win** | Karakra et al.; 2019 predictive-simulation project and 2020 real-time-monitoring/resilience framework | Discrete-event simulation and real-time data track patient pathways, forecast near-future delays or schedule changes, and provide decision support. The review reports intended reductions in waiting times, delays, and length of stay, with improved organizational resilience [101]. |
| **Health@Hand, BioSecure, DHPES and emergency-unit/trauma twins** | Nonnemann et al.; Mylrea et al.; Rodríguez-Aguilar et al.; Augusto et al.; Croatti et al. | Health@Hand twins ICU-station processes for remote monitoring and early fault intervention. BioSecure twins supply-chain processes for productivity and cybersecurity using Cyber-Informed Engineering. DHPES models hospital services, supplies, equipment, and human and financial resources during contingencies. Augusto’s emergency-unit model simulates alternative scenarios; its hospital-information-system inputs were supplemented by staff interviews because some process data were unreliable, and the validated model reduced waiting time and length of stay in tested scenarios. Croatti et al. used two twins to support severe-trauma management [101]. |

**Technologies and mechanism**

**Boundary, adjacent projects and research relevance**

Several named care-coordination systems are useful comparators but are not established as digital twins in the supplied evidence. These include the 2018 neurological-hospital queuing study, which models two multi-hospital configurations without a real-world updating link [124]; AHRQ projects using smart glasses and telemedicine (**R21 HS028104**, Zhan Zhang), **TELE-TOC** for post-hospital COPD care (**R01 HS027804**, Press, Abraham and Arora), a mobile PHR using EHR/FHIR for families of children with special needs (**R21 HS028699**, David Y. Ming), **myPOSH** (**R01 HS029454**, Bitton and Brindle), and **Peer PLUS** (**R21/R33 HS028880**, Tammy Toscos) [126]. The Ottawa Hospital learning-health-system redesign, DeepCare, the AI-Pathway Companion Prostate Cancer VA10B, and a Head and Neck Oncology e-pathway are similarly described as learning-health, AI, or EHR systems rather than explicit twins [125]. A retrospective account reports **12 integrated processes**, a reduction from **92 to 47 days (48%)** in median referral-to-treatment time, **71.88% (23/32)** simulated pediatric-oncology pathways handled successfully, and a **3.7-minute (27%)** reduction in initial oncology-consultation EHR time; these are outcomes of pathway or AI systems, not proven digital-twin outcomes [127].

- Cambridge University Hospitals’ Digital Hospitals (Addenbrooke’s Histopathology pilot) links records, processes, equipment/occupancy; its “Twin of Twins” combines discrete-event simulation, BIM and IoT monitoring to update models and simulate disruptions; pilot [131].
- Nova Scotia Health Authority C3/GE HealthCare CCSP covered 41 facilities; STAR/Meditech data and Tiles supported flow, capacity and discharge. Sep 2022–Jul 2023: EDD compliance ~91%, acute discharge accuracy 62.5% (+36%), nearly 5 staff-hours/day saved; decision support, not explicitly a twin [130]. Providence Vancouver C3 used six GE modules, updating every 30 seconds, 24/7; first modules were planned [132].
- Microsoft’s Hospital Operations reference architecture (not deployment) ingests EHR/ADT/RCM; Digital Twin Builder models beds/staffing/flow, ML predicts surges and Activator alerts [77]. Siemens simulated a customer radiology department [137]; TGH names a patient-flow twin with GE/Palantir, but gives no early-2024 date [139].
- Huma, Viz.ai and EY Care Coordination are named AI/monitoring platforms, not source-verified twins [128][129]. EDITH’s February 2024 minutes describe a VHT roadmap and federated data/model infrastructure, but not major-center status [140]; general evidence adds EHR/IoT/AI mechanisms without a named early-2024 deployment [133].

In this Hospital Management and Care Coordination subsection, AHRQ documents smart-glasses/telemedicine (R21 HS028104), TELE-TOC (R01 HS027804), and a FHIR mobile app (R21 HS028699); lung-cancer redesign and RESORT add named application cases [126][127]. The FHIR app had high feasibility/early adoption but limited sustained use under technical challenges and mixed experiences; not every case is an established digital twin [126][127].

rejected; reason: citation_outside_operands; allowed numbers: R21 HS028104, R01 HS027804, R21 HS028699, "", 66%, 2021, 96.85%; 60% reduction, 2024, 17 studies; allowed citations: [123][52][77][126][127][128][130][132][133][99][100][134][135][136][101][138][140]; allowed entity: Hospital Management and Care Coordination.

rejected; reason: number_unsupported; allowed numbers: R21 HS028104, R01 HS027804, R21 HS028699, "", 66%, 96.85%; 60% reduction, 2024, 17 studies, R21/R33 HS028880, R01 HS029454; allowed citations: [77][126][127][128][129][130][131][132][134][135][136][101][138][140]; allowed entity: Hospital Management and Care Coordination.

### 2. Medical Device Design

**Engineering and clinical evidence must be separated.** Device-design models investigate mechanical behavior, manufacturing variability, durability, and interaction with anatomy. Patient-specific clinical models instead help select or deploy a device, or estimate a physiological quantity. Medtronic and the Dunkley clip study illustrate engineering verification; FEops illustrates implantation planning; HeartFlow provides the strongest clinical-deployment example in this catalog.

| Specific application case | Companies and organizations | Projects or key technologies | Digital-twin function | Evidence status |
|---|---|---|---|---|
| Thoracic-aortic stent-graft design | Medtronic; Dassault Systèmes | Abaqus; Isight; probabilistic design workflows | Test manufacturing and anatomical variability | Bench-comparison engineering case |
| Medical-device clip tolerances† | Dunkley and colleagues; Haughton Design source | SolidWorks FEA; physical calibration; Monte Carlo analysis | Identify geometry most important to performance | Simplified engineering model |
| Patient-specific aortic-valve implantation | FEops; Ghent University; Erasmus Medical Center | HEARTguide/TAVIguide; CT; Abaqus | Predict implant–anatomy interaction and conduction risk | Retrospective 112-patient collaboration |
| Coronary physiological assessment | HeartFlow Inc. | FFRCT; coronary CT; AI; fluid dynamics | Estimate functional effects of coronary narrowing | FDA-reviewed device; NHS clinical use |
| Diseased-heart/device interaction | SIMULIA/Dassault Systèmes; Living Heart Project | Multiphysics heart model; annuloplasty-ring simulation | Evaluate a proposed device in diseased tissue | Conceptual validation |

Sources include the Medtronic engineering case [15], Dunkley clip study [16], FEops case [17], FDA HeartFlow review [4], and Living Heart benchmark [18].

**Medtronic propagates real design variability.** In a 2013 case, Medtronic’s Endovascular Therapies R&D group used finite-element analysis, which divides a structure into computational elements to calculate mechanical response. Abaqus simulated stent-graft behavior, while Isight automated design-of-experiments and probabilistic workflows. The model varied both manufactured-device characteristics and the anatomy receiving the device. [15]

**The tolerance ranges were explicit.** Stent height and wire diameter varied by ±10%, crown radius/pin diameter by ±25%, outer diameter by −1% to +2%, vessel diameter by ±2.5%, and material plateaus by ±10%. Rather than relying on one nominal configuration, the workflow examined how realistic combinations of variations could affect mechanical performance.

**Bench testing anchored the simulation.** Calculations were compared with radial-force tests and acoustic-fluid fatigue testing. Experimental work over three to six months represented a ten-year load requirement of approximately 400 million cycles. The team reported an order-of-magnitude reduction in the stent design cycle; that is a design-efficiency result, not a patient-outcome estimate. [15]

**The clip model prioritizes verification effort.** Dunkley and colleagues calibrated SolidWorks finite-element predictions against physical force–displacement measurements, varied five geometric parameters, and performed a 5,000-sample Monte Carlo tolerance analysis. The statistical calculation assumed normally distributed dimensional variation and a process-capability index, Cp, of 2. [16]

**Thickness dominated the clip’s sensitivity.** The study found thickness particularly influential because of its cubic effect on bending stiffness and its small nominal dimension. Length also influenced stiffness, while width and deflection had more moderate effects. This gives designers a concrete decision: prioritize control and verification of the dimensions that most strongly influence performance, rather than treating every tolerance as equally consequential. The study’s simplified two-dimensional geometry did not represent localized features or dynamic relatching contact.

**FEops personalizes implant deployment.** Belgium-based FEops, a Ghent University spinoff, uses an individual’s preoperative CT images to construct anatomically correct finite-element models of the aortic root. HEARTguide/TAVIguide then simulates how a transcatheter aortic valve will interact with that anatomy; the 2022 case illustrates virtual implantation of Medtronic Evolut R. TAVIguide was described as CE-marked for European clinical applications at that time. [17]

**The clinical question is device–patient interaction.** A retrospective collaboration involving 112 patients and Erasmus Medical Center in Rotterdam examined prediction of conduction abnormalities after transcatheter aortic-valve implantation, or TAVI. The model’s value lies in estimating effects that depend on the combination of implant behavior, deployment, and individual anatomy—not simply displaying a three-dimensional heart. The case reported that runtimes had fallen from days to hours, supporting scheduled preprocedural analysis rather than implying instantaneous intraoperative control. [17]

**HeartFlow has clinical deployment evidence.** HeartFlow FFRCT reconstructs a patient’s coronary arteries from coronary CT angiography, or CCTA, and applies computational fluid dynamics to estimate pressure and blood flow. Fractional flow reserve describes the functional significance of a narrowing; FFRCT estimates it computationally rather than obtaining it through an invasive pressure measurement. The FDA’s 2013 De Novo review classified version 1.4 as a Class II coronary physiological simulation software device. [4]

**The diagnostic denominator is important.** HeartFlowNXT enrolled 276 people, with 254 adults in the intent-to-diagnose population and direct invasive-FFR comparisons in 484 vessels. In the FDA review’s primary-endpoint section, per-vessel sensitivity was 83.5% and specificity was 85.8%; their lower one-sided 95% confidence bounds were 75.3% and 81.5%, respectively. These are diagnostic-performance findings for the studied software version and population, not general accuracy percentages for every cardiac digital twin. [4]

**The model enters an actual pathway.** HFMA’s 2024 NHS case study describes AI algorithms, computational fluid dynamics, and trained analysts creating and checking the model. In the reported pathway, CCTA narrowing of 40%–90% could trigger HeartFlow analysis, and approximately 35% of CCTAs proceeded to that modeling step. Results returned to the clinical team and were incorporated into the imaging and patient-record workflow. [19]

**Deployment extended beyond a research cohort.** In February 2024, HeartFlow was live in nearly 100 UK NHS hospitals, with another 12 implementing it. A separate MedTech Funding Mandate evaluation cited approximately 6,000 patients receiving the analysis annually. These implementation figures describe a different denominator from the larger pathway-outcomes study. [19]

**Outcome associations deserve a careful reading.** HFMA summarized the 2023 FISH&CHIPS analysis of over 90,000 pathway patients across 25 NHS sites. Comparing periods before and after implementation, the analysis reported 14% lower relative cardiovascular mortality and 8% lower relative all-cause mortality at two years, alongside reductions of 14% in non-invasive cardiac testing and 5% in invasive angiography. The report identifies the findings as univariate before-and-after associations, so they should not be interpreted as isolated causal effects of the model. [19]

**Living Heart tests a different question.** A 2015 benchmark modified left-ventricular tissue properties using post-myocardial-infarction patient data, then evaluated a novel annuloplasty ring with a sub-valvular component. The simulated ejection fraction fell from 55% in the normal-heart model to 45% in the infarcted model, and implantation predicted improved valve-leaflet coaptation—better leaflet closure. The source describes this as conceptual validation. [18]

**The practical takeaway is endpoint matching.** Device-design twins should be judged by validated mechanical and design decisions, while claims about clinical benefit require evidence tied to the intended patients, procedures, and outcomes.

### 3. Biomarker and Drug Discovery

**The strongest role is hypothesis prioritization.** Digital-twin approaches can organize complex molecular information, identify candidate regulators, stratify patients, and test drug-development assumptions. By early 2024, the concrete examples supported those research functions more strongly than claims that a comprehensive twin could reliably discover and validate a new drug.

| Specific application case | Companies, projects, or researchers | Key technologies | Digital-twin use | Reported result or status |
|---|---|---|---|---|
| Seasonal allergic-rhinitis target prioritization | Li and colleagues; Swedish/Austrian research cohorts | Time-series single-cell RNA sequencing; multicellular networks | Rank disease regulators and drug targets | 16 patients; 14 matched controls |
| Endometriosis molecular discovery | Genzeva; LumaGene; RYLTI; Brigham and Women’s; QIAGEN | Exome sequencing; phenotype ranking; biomimetic twin ecosystem | Connect phenotype, variant, and protein information | Eight pathogenic mutations; four VUSs; 29 March 2024 |
| NSCLC predictive-biomarker analysis | Schmidt and colleagues; CP1108/MYSTIC; AstraZeneca pathology collaboration | PD-L1 scoring; whole-slide imaging; patient matching | Evaluate biomarker stratification with virtual controls | 121 matched twins; treatment benefit underestimated |
| Drug Development Digital Twin schema | An and Cockrell | Mechanistic modeling; virtual patient populations | Explore novel, hypothetical, or repurposed drugs | Aspirational development roadmap |
| Metabolic drug-development support | Unlearn | Disease-specific generative models | Forecast clinical outcomes for trial participants | Three generators released February 2024 |

The cases are documented in the single-cell framework [5], endometriosis announcement [20], NSCLC abstract [21], drug-development schema [22], and Unlearn release [7].

**Single-cell models capture changing biological networks.** The 2022 Genome Medicine framework analyzed allergen-stimulated peripheral blood mononuclear cells—immune cells isolated from blood—from 16 people with seasonal allergic rhinitis and 14 matched healthy controls. Samples came from Linköping, Sweden, and Vienna, Austria. Time-series single-cell RNA sequencing measured gene activity across cell types and time points, providing a dynamic experimental basis for the models. [5]

**The target was a network, not one gene.** The analysis identified thousands of differentially expressed genes and multiple upstream regulators distributed across cell types. Multicellular network models ranked regulators according to predicted downstream effects. The useful output was therefore a prioritized set of disease-gene and drug-target hypotheses, rather than a single universal regulator assumed to control the whole response.

**Experimental timing supplies the update mechanism.** Here, “dynamic” refers to biological responses measured over an experimental time course, not continuous bedside monitoring. Repeated molecular observations change the inferred network state and the importance assigned to potential intervention points. This illustrates how a twin-like framework can support discovery even when its physical counterpart is a sampled biological system rather than an instrumented patient.

**Endometriosis provides a cutoff-edge example.** On 29 March 2024, Genzeva, LumaGene, RYLTI, Brigham and Women’s Hospital, and QIAGEN Digital Insights announced a multiomics study using clinical exome sequencing, phenotype-driven variant analysis, and RYLTI’s biomimetic AI platform. The announcement reported eight pathogenic mutations and four variants of unknown clinical significance, or VUSs. [20]

**Four linked representations organize the analysis.** The ecosystem comprised patient-profile, phenotype, gene-variant, and protein-variant twin classes. Phenotype-ranking algorithms and knowledge engineering connected these representations to identify relationships that conventional isolated analyses might overlook. This is a knowledge-based discovery architecture, rather than evidence of a continuously synchronized physiological patient replica. [23]

**MUC20 was a candidate biomarker.** The announcement reported a MUC20 VUS across all reported endometriosis samples and proposed it as a potential diagnostic biomarker. Other reported VUSs involved USP17L1, FAM66B, and DEFB109B on the short arm of chromosome 8; the report also described shared enhancer regulation of DEFB109B and FAM66B. A VUS remains a variant whose clinical significance is uncertain, so the result supports molecular prioritization rather than an established diagnostic test. [20]

**The NSCLC result tests predictive credibility.** Schmidt and colleagues’ November 2023 proof of concept used baseline tissue from the CP1108 Phase I/II trial and the MYSTIC Phase III trial in non-small-cell lung cancer. Quantitative Continuous Scoring measured PD-L1 expression in whole-slide pathology images. Patients in the earlier trial were matched to similar MYSTIC control-arm patients using Euclidean distance and Delaunay triangulation after reducing the dimensions of the patient-feature data. [21]

**The selected feature was precisely defined.** The analysis generated 121 matched digital twins and selected the 20th-percentile PD-L1 tumor-cell-expression feature for stratification. This means a feature of the distribution of expression intensity within a patient’s slide—not simply “20% of patients” or “20% PD-L1-positive cells.” The virtual analysis underestimated durvalumab’s observed overall-survival benefit, and its selected feature did not show a significant treatment benefit in the virtual cohort.

**This counterexample changes the interpretation.** A model can successfully assemble plausible virtual controls yet still misestimate treatment benefit. Similarity in measured baseline features does not guarantee equivalence in every factor influencing survival or treatment response. Consequently, this application is best read as technical feasibility for biomarker-development workflows, with treatment-effect prediction remaining the decisive test.

**Novel drugs require mechanistic assumptions.** An and Cockrell’s 2022 Drug Development Digital Twin schema explicitly targets novel or hypothetical drugs and existing drugs used in new populations or applications. Because such interventions lack established response histories in their proposed use, the framework requires a mechanistic representation of the presumed drug action. Its proposed virtual populations would then support in-silico testing. The authors presented this as an aspirational roadmap. [22]

**Trial forecasting is a distinct contribution.** Unlearn’s February 2024 hypertension, dyslipidemia, and type-2-diabetes generators support drug development by forecasting participant outcomes under specified standard-care contexts. They are not examples of molecular target discovery or proof that a new compound works. Their principal relevance is improving the design and analysis of subsequent human trials.

**The practical takeaway is disciplined hypothesis testing.** Discovery twins are valuable for prioritizing biomarkers, targets, and patient groups, but stronger therapeutic claims depend on replicated biology and accurate prediction of actual treatment outcomes.

### 4. Biomanufacturing

**BioDT provides a concrete adaptive-control example.** Jiangnan University and T&J Bioengineering connected a cell-culture process to a model that updated from measurements and supported automated nutrient feeding. This is a clearer demonstration of active coupling than a standalone process simulation, while other programs emphasize the data infrastructure, scale-up, and validation needed for industrial use.

| Specific application case | Companies and institutions | Key technologies | Digital-twin function | Status or result |
|---|---|---|---|---|
| BioDT CHO-cell culture | Jiangnan University; T&J Bioengineering | Optical sensing; kinetic models; C++/Python; connected HMI | Update process parameters and guide feeding | 2023 proof of concept; 14.8% cell-density gain |
| HIV-Gag virus-like-particle production | Helgers, Hengelbrock, Strube, and collaborators | HEK293 process models; dynamic metabolism | Connect production, purification, and control development | Published 2022 research series |
| Vaccine-process development† | Intravacc; Körber | PAS-X Savvy; process analytics; mechanistic models | Centralize process data and support soft sensors | Platform implementation profile |
| Pharmaceutical bioprocess optimization† | Wageningen University & Research | DBTL; experimental design; ML; metabolic models | Predict performance and optimize process design | Research-program profile |
| Process development and transfer† | Körber; TetraScience | Contextualized cloud data; analytics; PAS-X Savvy | Enable process prediction, verification, and transfer | Company-reported customer proof of concept |
| Stem/stromal-cell manufacturing† | KU Leuven | Stirred bioreactors; sensors; ML/mechanistic models | Adapt expansion and differentiation to variable cells | Proposed hMSC twin framework |

The dated research is described in BioDT [2], including its discussion of the 2022 HIV-Gag studies. Additional architectures appear in the Intravacc profile [24], Wageningen program [25], Körber–TetraScience account [26], and KU Leuven proposal [27].

**BioDT links a specified physical process.** Published on 13 April 2023, the study involved Jiangnan University in Wuxi and T&J Bioengineering in Shanghai, China. Its physical system was a three-dimensionally printed rocking platform adapted to T25 cell-culture flasks, with automated rocking settings, in-place optical cell-density measurement, and Wi-Fi communication. A web-based human–machine interface, or HMI, connected the device, model, operator, and stored data. [2]

**The model estimates biological process state.** BioDT used kinetic models for cell growth, glucose consumption, lactic-acid production, and oxygen uptake or transfer. The computational core was written in C++ and exposed as a reusable Python library. Chinese hamster ovary cells—CHO cells, widely used in biomanufacturing—provided the experimental system.

**Measurements and calculations had different frequencies.** Optical cell-density measurements occurred every 15 minutes, while glucose and lactic-acid measurements were sampled every 12 hours. Model parameters were recalculated when measurements synchronized with the twin. This matters because a model-generated estimate between laboratory samples is a “soft sensor”: a calculated process variable, not a direct new chemical measurement. [2]

**The comparison isolated adaptive modeling.** A 72-hour experiment, with a media change at 36 hours, compared a static digital model, a measurement-synchronized digital shadow, and a parameter-updating digital twin. The twin better captured glucose and lactate variation because it could adjust the kinetics rather than merely reset its current state. For tracking frequently measured process variables, however, its advantage over the digital shadow became less apparent at high sampling frequencies. [2]

**Feedback produced a physical action.** The HMI could alert an operator when predicted glucose or lactate reached preset thresholds, illustrated with 4 g/L glucose and 1 g/L lactic acid. Adding a dosing pump enabled automated glucose feeding based on predicted concentration. In the illustrative fed-batch experiment, cell density improved by 14.8% compared with batch culture. [2]

**The endpoint was cell density.** That result supports the feasibility of model-guided feeding, but it is not a measured increase in pharmaceutical product yield, product potency, or clinical benefit. The paper also described the feeding experiment as illustrative rather than comprehensive. The relevant next industrial question is whether the same control logic maintains product-specific quality and performance when the process or scale changes.

**The HIV-Gag work broadens the process scope.** BioDT’s authors identify a 2022 research series on virus-like-particle production in HEK293 cells, including production and purification modeling and a dynamic-metabolic-model approach toward autonomous control. This is a second named biomanufacturing application with a specific biological product and cell platform. Its relevance is the progression from isolated process models toward connected manufacturing operations. [2]

**Intravacc emphasizes an integrated data foundation.** The institute’s PAS-X Savvy implementation brings together upstream and downstream process information, bioreactor records, spreadsheets, analytical measurements, spectra, and microscopic images. Körber describes real-time analytics, multivariate statistics, mechanistic modeling, Python/R analysis, and model-based soft sensors for cell-culture monitoring. [24]

**The platform enables, rather than guarantees, twinning.** Consolidating measurements makes it possible to align continuous reactor data with intermittent quality assays and fit models to a particular process. A completed process twin additionally needs a credible model, an update procedure, and a defined operational use. The meaningful contribution is therefore more than data storage, but less than assuming that every connected process has already become self-optimizing.

**Körber connects models with manufacturing validation.** Its technical description combines development data and live process information with time- and space-dependent differential equations and Bayesian statistical models. Intended uses include predicting critical quality attributes, establishing operating ranges, informing process performance qualification, and setting alerts during continued process verification. These are model-supported justification and monitoring functions, not automatic permission to reduce validation work. [28]

**Wageningen connects modeling with experimentation.** Wageningen University & Research describes twins combining historical and real-time information to predict future bioprocess performance, including pharmaceutical applications. Its technologies include Design–Build–Test–Learn cycles, design of experiments, machine learning, robotics, microfluidics, semantic technologies, and flux-balance analysis for metabolic modeling. The broader microbial program includes Pseudomonas putida and other industrial organisms. [25]

**The commercial proof of concept measures data work.** Körber and TetraScience reported a customer project with a top-25 global biopharmaceutical company in which automatic data collection increased productivity by 50% and elimination of manual transcription reduced errors by 75%. They also reported six to twelve months faster process development and technology transfer. Their associated $250–$550 million potential-revenue figure was a company projection, not observed additional sales. [26]

**These gains have several possible mechanisms.** Faster collection, consistent metadata, reduced transcription, and reusable analyses can improve development work before any autonomous twin controls a reactor. Consequently, the commercial result should not be attributed wholly to digital-twin prediction. It demonstrates the business importance of data preparation and context alongside the model itself.

**KU Leuven targets variable therapeutic cells.** Its proposed framework concerns human mesenchymal stem/stromal cells, or hMSCs, in stirred suspension bioreactors. Integrated sensors, machine learning, mechanistic models, and analytics would model expansion and differentiation and support a self-adaptive process. Unlike an application focused only on maximizing cell number, this program explicitly addresses donor variability and cell-state control for cell and gene therapy. [27]

**A process proxy can mislead.** In adjacent research, WattBE Innovations’ Ranger refractive-index process analytics supported metabolic modeling and pH control for HEK293T cells producing lentiviral vectors in 5 L bioreactors. Across 22 experiments—18 development and four validation runs—control strategies increased metabolic activity 1.8-fold without increasing vector production. This was a process-analytics/control study, not an end-to-end twin demonstration, but it shows why biological activity cannot stand in for product yield. [29]

**Industrial adoption depends on operating infrastructure.** A targeted 2021 Danish survey of 33 biotech sub-organizations found 24 with digitalization plans, ten with well-defined business cases, and only two with complete advanced-process-analytics coverage. Its application question grouped digital twins, three-dimensional models, and simulation models together, so its adoption figures describe broad modeling practice rather than fully coupled twins alone. [11]

**The practical takeaway is product-focused control.** Biomanufacturing twins are most compelling when adaptive models improve an actionable process variable and that improvement translates into reproducible product quality, yield, or manufacturing reliability.

### 5. Surgical Planning

**Patient-specific planning is already tangible.** The strongest examples reconstruct an individual’s anatomy, compare approaches or implant positions, and help transfer the plan into the operating room. Their usefulness does not automatically make them continuously updated surgical twins: geometric visualization, live image registration, and physiological prediction are different capabilities.

| Specific application case | Companies and institutions | Key technologies | Use in planning or surgery | Reported evidence |
|---|---|---|---|---|
| Sacroiliac-joint fusion | University of Twente; Medisch Spectrum Twente; Materialise; SI-Bone | CT segmentation; virtual implants; simulated fluoroscopy | Plan implant position and reproduce it intraoperatively | Ten patients; 30 implants |
| Robotic partial nephrectomy | Turin clinical teams; Medics3D | HA3D models; CNNs; ResNet.50; iKidney | Align kidney/tumor models with live endoscopic images | Thirteen-patient series |
| Vestibular-schwannoma planning | Olexa and colleagues; Hoth Intelligence; Microsoft | MRI reconstruction; markerless AR; HoloLens 2 | Visualize anatomy and plan incision/craniotomy | March 2024 single case |
| Angiofibroma excision | Zahid and colleagues; Autodesk software | CT/DICOM; 3D Slicer; Meshmixer; PLA/TPU printing | Inspect tumor–skull relationships before and during surgery | Single-patient biomodel case |
| Brain-surgery rehearsal† | Atlas Meditech; NVIDIA | MONAI Label; Pathfinder; Omniverse; PhysX | Personalize anatomy and rehearse access pathways | Development platform |
| Thoracic-aortic-aneurysm planning | Biancolini and colleagues, Italy | Reduced-order models; radial-basis morphing; CFD | Explore how aneurysm geometry changes blood flow | 2020 proof of concept |

Sources are the Twente study [6], iKidney series [30], Hoth/HoloLens case [31], angiofibroma case [32], Atlas technical account [33], and cardiovascular review [10].

**Twente connects virtual implants with fluoroscopy.** The workflow, implemented as standard care at Medisch Spectrum Twente in Enschede in November 2021, used preoperative CT to segment the pelvis and sacroiliac joint. Materialise Mimics 23.0 and 3-Matic 15.0 supported reconstruction and virtual implant placement. Simulated fluoroscopic views then reproduced the lateral, inlet, and outlet images used during implantation of the SI-Bone iFuse system. [6]

**The clinical series measured plan reproduction.** The October 2023 report evaluated the first ten patients, all female, treated by one experienced surgeon. Thirty implants were placed. Mean total implant-apex positional deviation was 4.9 ± 1.26 mm, and mean angular deviation was 4.0 ± 1.44°, with no malpositioning complications. Those measurements quantify correspondence between the planned and achieved implant positions. [6]

**Live images retained clinical priority.** The surgeon compared simulated and actual fluoroscopy side by side and could depart from the plan when necessary. Actual intraoperative images took precedence. This is an important safety mechanism: the preoperative model supports understanding and targeting, while the current physical anatomy determines the final action.

**Zero events do not establish prevention.** The same paper cited nerve-related complications in three of 172 patients in one comparator study and revision for nerve-root impingement in 2.1% of interventions in a review. These are different populations and denominators, not a controlled comparison with the ten-case virtual-planning series. The substantive finding is feasible plan transfer with measured placement accuracy, rather than a demonstrated reduction in rare complications.

**iKidney adds live spatial registration.** Medics3D bioengineers constructed HA3D models from multiphase CT, including the kidney, tumor, arteries, veins, and collecting system. A convolutional neural network—a machine-learning method for recognizing image patterns—processed live endoscopic images. The iKidney software then overlaid the model in the robotic console, supporting navigation during robot-assisted partial nephrectomy. [30]

**Its evidence is a small clinical series.** Piana and colleagues’ 3 March 2024 publication included 13 patients enrolled between January 2022 and April 2023. Table 3 reports median co-registration time of 11 seconds, with an interquartile range of 6–13 seconds. One complete registration failure required ultrasound guidance; no complications above Clavien–Dindo grade 2 were recorded. The report’s text and table give a reported range of one to two patients with temporary dynamic registration failure. [30]

**Registration updates are not complete physiology.** The system updates where the model is placed relative to the camera view. That is a meaningful advance beyond an unchanging preoperative display, but it does not establish that the model continuously measures internal tissue deformation, perfusion, or functional response. Breathing, manipulation, camera changes, and instruments can all alter the correspondence between the virtual anatomy and operative scene.

**The comparison exposes a practical trade-off.** The paper contrasts iKidney with the earlier ICG-guided IGNITE approach, which reported seven-second mean registration. iKidney avoided injecting the fluorescent substance and its associated vascular-enhancement effects, but still needed initial human assistance and ongoing engineering collaboration. Faster registration alone is therefore not a sufficient comparison; reproducibility, assistance requirements, and robustness also matter. [30]

**Hoth’s case emphasizes anatomical understanding.** Olexa and colleagues used Hoth Intelligence software on Microsoft HoloLens 2 to align MRI-derived models of a vestibular schwannoma, ventricles, vessels, and brain with a patient’s head. The March 2024 report concerned a 47-year-old woman with a 3.3 cm lesion and used the display for layered inspection and planning of a retrosigmoid craniotomy. [31]

**The reported outcome remains case-specific.** A small tumor segment over the facial nerve was left during resection; postoperative facial numbness resolved, and the patient was otherwise neurologically stable. The authors positioned the system as an adjunct to conventional neuronavigation. The case demonstrates feasibility of spatially registered planning, not comparative superiority of an active twin.

**The printed angiofibroma model is a precursor.** Zahid and colleagues reconstructed CT/DICOM data using 3D Slicer and Autodesk Meshmixer for a 19-year-old man with recurrent juvenile nasopharyngeal angiofibroma. Dual-extrusion printing produced a rigid PLA skull and flexible TPU95A tumor. The model supported preoperative and intraoperative visualization during endoscopic endonasal excision. [32]

**Material realism serves a spatial purpose.** The contrasting rigid and flexible materials made the tumor’s relationship with the skull easier to inspect and discuss. That is useful patient-specific preparation, but the printed object does not update or predict a changing patient state. It belongs in the surgical-planning pathway as a related anatomical-model technology, not as evidence of bidirectional digital twinning.

**Atlas aims at interactive rehearsal.** Atlas Meditech’s Pathfinder uses MONAI Label to segment normal structures and tumors in MRI and CT scans, then morphs a brain model to an individual’s anatomy and lesion. Omniverse supplies the virtual environment, while PhysX supports simulated physical interactions. Surgeons can evaluate access paths and rehearse patient and equipment positioning. [33]

**Predictive rehearsal raises the validation burden.** A display that accurately locates a tumor is different from a simulation that accurately predicts brain-tissue movement under an instrument. Atlas’s proposed tissue-shift, haptic, intraoperative-AI, and instrument-training functions extend toward that harder problem. Their clinical meaning depends on how well the simulated physical behavior matches the operative situation.

**Biancolini addresses computational speed.** The Italian team’s thoracic-aortic-aneurysm planning work combined computational fluid dynamics, radial-basis-function mesh morphing, and reduced-order modeling. A reduced-order model approximates expensive calculations so users can interactively explore changes—in this case, aneurysm bulge shape and its hemodynamic consequences. The 2022 review classifies it as a proof of concept and digital-twin precursor. [10]

**The practical takeaway is to distinguish capabilities.** Surgical planning has credible patient-specific applications, while stronger surgical-twin claims depend on validated intraoperative updating and evidence that model-guided actions improve clinically meaningful outcomes.

**Additional documented evidence**

**Part One: Surgical Planning**

**Supported result.** By the early-2024 snapshot, Surgical Planning’s clearest DT4H role was patient-specific modeling for approach selection, rehearsal, implant fit, risk prediction, and navigation. The evidence is narrower than the surrounding VR/AR literature: a static 3-D image is not counted as a twin unless it is linked to the patient, procedure, or operating-room data. A surgical twin can represent the patient, instruments, staff, and environment for simulation, prediction, or feedback [82].

**Direct cases, actors and technologies**

- **Twin-s (2023), prototype.** Twin-s is explicitly described as “a digital twin for skull base surgery,” making it a named Surgical Planning project; the supplied evidence does not establish clinical deployment or a patient outcome [82].

- **Surgery digitalization proof of concept, ex-vivo spinal surgery.** The project digitized pedicle-screw drilling on a human specimen for planning, navigation, training, and quality control. Five RGB-D cameras captured the surgeon, a high-end camera reconstructed anatomy, an infrared stereo camera tracked instruments, and a laser scanner reconstructed and registered the operating room. FARO supplied the scanner, Microsoft the Azure Kinect cameras, Atracsys the FusionTrack 500 tracker, Arthrex the AR-600 drill, DePuy Synthes the drill sleeve, Sony the photogrammetry camera, and the Blender Foundation Blender software. It was a single-surgeon, manually curated proof of concept rather than patient deployment [82].

- **Nvidia surgical-preparation project.** The source names Nvidia’s participation but gives no formal project name. CT data were processed through organ segmentation, mesh refinement, and texturing to create photorealistic anatomical digital human twins. The intended uses were surgeon preparation, safe-pathway identification, reduced operating time and fatigue, and improved patient safety [159].

- **Microsoft–Johnson & Johnson digital surgical platform (2022; rollout work).** The proposed platform used Azure Digital Twins, advanced simulation, and modeling to represent patient anatomy for surgical planning and practice. The source describes work toward rollout, not a completed deployment [146].

**Evidence boundary and mechanism**

A review published **25 April 2024**, based on searches through **10 May 2023**, provides later-published adjacent VR evidence rather than proof that every case was a linked digital twin. It covers biventricular repair, non-small-cell-lung-cancer chest-wall resection, lung segmentectomy, middle-cerebral-artery aneurysm clipping, pediatric LVAD implantation, liver-tumor resection, and foreign-body removal; named tools include IMHOTEP, CorFix, 3D Slicer, and Surgical Theater [69]. Cited studies reported plan changes of **60% (9/15 cases)** and **52% (50 patients)**, but the review described the evidence as heterogeneous, often anecdotal, and still experimental [69]. A later review published **16 July 2024** adds skull-base examples involving a 69-year-old clinoid-meningioma patient, 30 anterior-skull-base meningioma patients, 17 pediatric AR procedures, and 134 retrospective endonasal cases; it identifies Surgical Theater and Brainlab as platform providers [151].

The mechanism is multimodal imaging—CT, MRI, ultrasound, echocardiography, or DSA—followed by segmentation, mesh or volume rendering, and a patient-specific model. VR/AR/MxR, optical tracking, tissue-deformation or cutting simulation, haptic feedback, and intraoperative data then support a surgical decision or model update [52][69][151]. AR/MxR can overlay the model in real time, but brain shift can make preoperative anatomy stale: reported AR target-registration error ranged from **0.90 to 8.55 mm**, depending on technique and application, requiring continuous imaging and recalibration [151]. The spine prototype reported **6.72 mm** one-sided chamfer distance and **1.39 pixels** mean reprojection error; these are ex-vivo registration metrics, not clinical outcomes, and the prototype did not capture a complete real surgery [82].

Surgical Planning uses patient-specific anatomy for preoperative visualization, rehearsal, simulation or guidance; some are models, not twins. Apple Inc./Hoth Intelligence’s Vision Pro used CT/DICOM/autosegmentation for a 44-year-old woman’s VP-shunt plan (2024-02-14), but was mixed reality [147]. Ceevra’s Reveal CT/MRI models and smartphone VR supported robotic partial nephrectomy in 92 patients (2017–18); control ORs for >200-mL blood loss and >2-day stay were 1.98 and 2.86 [155]. La Paz’s four-patient TMJ pilot used CT/CBCT, Timeus/CD Ortosan, Zimmer/Biomet and CAD-CAM; MIO 24.6→36.4 mm and pain 8→3, though long-term validation was needed [148]. ImmersiveTouch/Materialise orbital VR (2 patients; CBCT→implants→3-D guides) [158]; Cella/MD Anderson models [156]; Cincinnati Children’s heart twins [70]; ARCollab AR hearts [78]; and Fraunhofer MEVIS liver VR (2 cases; potential only) [152] add cases. Medis supplied QAngio for post-cutoff CoronaryXR/CTA-CABG; simXAR CT/MRI-AR craniopagus (2026) is retrospective, and no card establishes a major DT4H center [85,404].

HoloSNS used patient-specific brain models/HoloLens 2 for EEG/DBS placement in a depression trial [149]. HipInsight (Surgical Planning Associates) guided 3,000 hip replacements by 13 Feb 2024 [144].

Surgical Planning: HeartFlow, SurgiNet Twin, NeuroTwin, Twin-S, VR3S; CT/MRI, CFD, VR, AI enable rehearsal/prediction [153]. Later companies: Dassault Systèmes, inHEART, AVATAR MEDICAL; no major center named [55].

Surgical Planning: M3DICS CT→3D partial-nephrectomy; 30 patients (2020): PADUA downgraded in 8/30 (26.4%), risk in 4/30 (13.4%) [141]; SurgeonsLab’s 2024 aneurysm twin [142]; Twin-S/rAC-GAN .

At the requested cutoff, Surgical Planning is a distinct subsection making digital-twin applications concrete: Apple Vision Pro and Hoth Intelligence used a patient-specific model for neurosurgical planning; Twin-s, IMHOTEP and CorFix add named project/software cases [147] [82] [145]. Imaging-linked models support AI simulation and interactive, stepwise VR planning [157] [152].

Within the named digital-surgery framework, Surgical Planning uses a brain-tumor digital twin with AI agents to simulate the whole procedure and test entry points, angles and depths, aiming to reduce damage to healthy tissue [150] [157].

Surgical Planning’s cases and studies serve the purpose of understanding specific digital-twin-for-health applications by linking patient anatomy to concrete decisions [147] [154].

A coherent Surgical Planning account links cases, actors, projects and technologies: Apple/Hoth’s mixed-reality case, Twin-s, IMHOTEP, CorFix and Surgical Theater cover modeling, rehearsal and guidance [147] [82] [145] [151]. Within the digital-surgery framework, imaging creates patient-specific models; VR/AI rehearses and updates plans, with cardiac twins changing initial strategies, while learning curves and safety/efficacy evaluation constrain adoption [150] [143] [152] [49].

### 6. In-silico Clinical Trials

**Virtual cohorts complement human trials.** In-silico trials use individualized computational models to evaluate medicines, devices, or interventions. The important distinction is between forecasting outcomes under existing care, matching historical controls, and mechanistically simulating an intervention; these approaches answer different questions and carry different risks.

| Specific application case | Companies or research groups | Key technologies | Trial-related function | Evidence status |
|---|---|---|---|---|
| TwinRCTs | Unlearn | Neural Boltzmann Machines; participant-level forecasts | Predict control outcomes before randomization | Productized trial-design approach |
| Virtual Phase III NSCLC analysis | Schmidt and colleagues; CP1108/MYSTIC | Computational pathology; matched historical controls | Explore biomarker-stratified treatment comparisons | 121 matched twins; proof of concept |
| Virtual twin patient populations | Medidata; Dassault Systèmes | Generative-AI simulants; pathophysiology models | Construct synthetic control or treatment populations | February 2024 demonstration |
| Individual cardiac drug simulation | January 2024 cardiac research team | CMR/ECG; Bayesian inference; electrophysiology | Simulate dofetilide effects across plausible model parameters | Single-subject technical demonstration |
| Echocardiogram-derived hemodynamic twins | Kuang’s research team | Physics-informed self-supervised learning | Infer models for disease detection and virtual trials | February 2024 preprint |

These approaches are described in Unlearn’s release [7], the NSCLC study [21], Medidata’s case study [34], the cardiac pipeline [8], and Kuang’s preprint [35].

**Unlearn forecasts each participant’s control outcome.** In the TwinRCT design, a digital twin is created for every participant before randomization and predicts that person’s outcome under placebo or the relevant control context, regardless of actual assignment. The company presents those forecasts as supporting highly powered trials with smaller control groups. Its Neural Boltzmann Machines combine neural-network prediction with probabilistic modeling of patient histories and outcomes, including incomplete or noisy records. [7]

**The February releases were disease-specific.** On 15 February 2024, Unlearn announced three generators with defined patient and treatment contexts:

| Digital-twin generator | Standard-care context | Intended forecasting scope |
|---|---|---|
| Acute hypertension | Diuretics, beta-blockers, or other medications | Trials lasting no more than three months |
| Dyslipidemia | Hyperlipidemia participants taking statins | Clinical outcomes within the treated population |
| Type 2 diabetes | Participants with heart disease | Blood sugar, cholesterol, laboratory, and safety measures |

The segment definitions come from the February 2024 announcement [7].

**The forecast is not observed treatment response.** Predicting what would happen under control care does not directly reveal how the same individual would respond to a novel treatment. Randomized observations remain important for estimating treatment benefit and checking whether the prediction behaves as intended. The strength of this application is a more informative trial design, not a general claim that simulated participants can replace all real controls.

**Regulatory qualification has a defined scope.** Unlearn states that methods using its participants’ twins were qualified by the European Medicines Agency and aligned with FDA guidance. That is the company’s characterization of its methodology; it should not be expanded into approval of every disease generator, trial, or medicine using a twin. [7]

**Historical matching has a different vulnerability.** The NSCLC proof of concept carried observed survival information from matched historical control patients into its virtual comparison. Its 121 twins therefore were not 121 newly observed randomized participants, and the model underestimated durvalumab’s benefit. The result illustrates why similarity between datasets must be tested against treatment-relevant endpoints, rather than judged solely from plausible baseline matches. [21]

**Medidata combines empirical and physiological models.** Its February 2024 case study describes combining generative-AI simulants with Dassault Systèmes’ 3DEXPERIENCE human-pathophysiology models to create virtual twin patient populations. Proposed uses include synthetic control and treatment arms for drug and device assessment. The case presents these approaches as complements to conventional trials, with smaller enrollment and shorter timelines framed as potential benefits. [34]

**The cardiac example simulates drug mechanisms.** The preprint submitted on 18 January 2024 personalized ventricular anatomy and electrical function from cardiac magnetic resonance imaging, or CMR, and a standard 12-lead electrocardiogram, or ECG. Bayesian inference generated plausible patient-specific parameter sets, which were used in fast reaction-Eikonal models and more detailed monodomain electrophysiology simulations. [8]

**Its numerical result is technical fidelity.** In a healthy female subject, inferred reaction-Eikonal models reproduced the ECG with Pearson correlation 0.93; translated monodomain simulations achieved 0.89. Applying dofetilide to the model population produced dose-dependent prolongation of QT and T-peak-to-T-end intervals consistent with large-population drug-response patterns. These correlations describe ECG reproduction—not 93% or 89% clinical accuracy. [8]

**Parameter populations are not patient populations.** The cardiac study carried uncertainty through several plausible models for one subject. That is useful for testing whether a predicted drug response depends strongly on uncertain parameters, but it does not establish performance across a demographically or clinically diverse trial population. This distinction is essential when moving from personalized simulation to virtual-cohort claims.

**Kuang infers physiology from non-invasive video.** The February 2024 preprint applies physics-informed self-supervised learning to echocardiogram videos to identify cardiac-hemodynamic twins. Its stated applications include unsupervised disease detection and in-silico trials. The contribution is an inference method: extracting a physiologically constrained model from observations rather than requiring every internal state to be directly measured. [35]

**Credibility must match the regulatory question.** Medidata’s case study points to the FDA’s 16 November 2023 final guidance on assessing computational-modeling credibility in medical-device submissions. The broader January 2024 position paper likewise emphasizes a precisely defined context of use. A model credible for design exploration is not automatically credible for establishing efficacy or replacing a regulatory endpoint. [34]

**The practical takeaway is complementary evidence.** In-silico trials can improve design, stratification, uncertainty analysis, and selected evidence generation, provided their forecasts are calibrated against the actual endpoint and intended population.

**Additional documented evidence**

**In-silico Clinical Trials**

**Supported result.** By early 2024, an In-silico Clinical Trial (ISCT) assigned an intervention, possibly with a control, to computational models of human cells, tissues, organs or systems and evaluated health outcomes; a single-patient intervention simulation was classified as a digital-twin study rather than an ISCT [174]. Unlinked synthetic patients are not automatically patient digital twins; a later classification found 5/15 (33%) research-oriented models generated synthetic patients, generally without linking them to individual patients [172].


- **InSilc, INSIST, SILICOFCM and STriTuVaD** were pre-cutoff European projects, retrospectively corroborated as addressing, respectively, drug-eluting bioresorbable-stent design; acute-ischaemic-stroke virtual patients built from clinical, imaging and histopathology data from 4,500 patients; familial-cardiomyopathy drug workflows; and tuberculosis-vaccine models with virtual-patient libraries and an adaptive Bayesian trial [171].
- **InSilicoONCO** used PK/PD models to predict testosterone suppression in virtual prostate-cancer patients; **InSilicoCARDIO** predicted forces and strains in self-expanding valves and tested prototypes. **In Silico World** coordinated 11 ISCT solutions around validation, regulation, scalability and education [171].
- **Optimal Personalised Treatment Computation through In Silico Clinical Trials on Patient Digital Twins** used retrospective University Hospital Zurich records to define a 21-arm assisted-reproduction ISCT. VPH/PK-PD models, Modelica/JModelica 2.1, Python search and Cineca’s Marconi high-performance computer tested treatment alternatives; computed regimens used 40.82% of reference drug quantity, saving 59.18%, but were not proved globally lightest because of the time budget [175][176].
- Other named studies covered personalised high-tibial osteotomy, intracranial flow diverters, and cementless femoral-stem robustness, where 16 bone models were varied into 2,000 finite-element models; additional examples include UISS COVID-19-vaccine trials, an open-source artificial pancreas, pro-arrhythmic-cardiotoxicity prediction, Archimedes/UVA–Padova diabetes simulation and the Drug Development Digital Twin for drug discovery, testing and repurposing [96][92][174][161][168].

**Mechanism, actors and purpose.** Clinical records, imaging, genomics, histopathology and trial or real-world data feed patient, device, virtual-cohort, clinician and clinical-outcome models. Mechanistic and ordinary-differential-equation models, PK/PD, finite-element and agent-based models, CRBMs and other generative AI, reinforcement learning, and physics-, data-, rule- or empirically based submodels simulate interventions; outputs can support safety and efficacy prediction, synthetic controls, adaptive or hybrid trials, and regulatory decisions [79][161]. CINECA supplied the Marconi infrastructure, while Sapienza University, Italy’s Ministry of University and Research, and the EC FP7 PAEON project supported the assisted-reproduction case [176]. GNQ Insilico’s 6 November 2023 memorandum with an unnamed Fortune-100 company described electronic-record, genomic, epigenetic and MRI twins, a knowledge graph and pharmacokinetic simulation; its 4 March 2024 announcement is retrospective [179]. These named research actors, together with cardiac ISCT work concentrated mostly in the United States and United Kingdom, show how ISCT connects DT4H research to trial-level counterfactual evidence, without establishing a ranked list of “major” institutions [174].

**Evidence boundary and limits.** A 2 February 2024 digital-health-technology study searched ClinicalTrials.gov records with 2000–2022 start dates downloaded on 2 April 2023: Bellerophon/Actigraph and Sage Therapeutics/Kinesia ONE were sensor examples, not digital twins; pharma/medtech-sponsored trials used Holter monitors in 19.9% and glucose monitors in 15.2%, while other sponsors used activity or movement monitors in 16.4% and mobile apps in 12.1% [165]. A cardiac review of 36 publications from 2012–2022 found some validation in 75%, no sensitivity analysis in 81%, no prior-data reuse in 78%, no easy data/model access in 97%, and ANSYS FLUENT in 19% [174]. Industrial support appeared in 42% of reviewed ISCTs, including AstraZeneca, Biotronik, CSL Behring, Actelion Pharmaceuticals and Abbott, but roles were not case-specific; Zimmer Biomet and Servier appear only as affiliations [174][92][167]. Later market claims about a Seoul case involving over 100 twins and 15 regimens, Novadiscovery–AstraZeneca/Jinko, FDA virtual-patient frameworks, Simcyp and Open Virtual Patient remain unverified or post-cutoff [170].

By early 2024, VICTRE used synthetic phantoms for breast imaging; an aspirational drug-development twin targeted drug/repurposing evaluation, while Unlearn.AI’s generative twins modeled Alzheimer’s/MS [97][169][115].

ISCTs model patient physiology, disease/treatment response and intervention delivery in virtual populations for product/regulatory evaluation—not static models [61][166]; they cover DT4H trial design, safety/effectiveness and regulatory evidence [164].

Living Heart: global cardiovascular collaboration led by Dassault Systèmes with FDA, clinical and industry partners; its digital heart supports regulatory, treatment and personalized-care uses; 3DEXPERIENCE plus Medidata simulants create synthetic-control/treatment arms, while TCS co-developed an athlete’s heart [164]. Optimal Personalised Treatment Computation (2020) used patient twins; VPH models were intended to predict device/drug performance in virtual populations [118][163]. ENRICHMENT (Dassault Systèmes–FDA, 2019) is retrospective “trial-before-the-trial” device evidence, reported complete after the cutoff; Living Heart’s major-center eligibility is unestablished [178][164].

EHR/RWD, biomarkers, imaging, genetics, lifestyle and sensors initialize twins; mechanistic, PK–PD/QSP and AI/ML models, simulation and feedback estimate efficacy, safety, responders and endpoints [173][103]. A proposed sepsis simulator used EHR/sensors, DAGs, Neo4j and cloud computation to return next states for training and bedside decisions, not a completed trial . Ansys, Avicenna, Medtronic and Premier roles are unverified; Certara’s Simcyp/Phoenix are market platforms, not a named case [166][177]. Later ClinicalGAN/SynTwin show trial monitoring and outcome prediction; a later UK Biobank “more than 30 petabytes” figure lacks a denominator/date [134][160][162]. Validation, representativeness and uncertainty remain conditions [61][166].

In-silico Clinical Trials should be presented as a specific digital-twin health application, not a generic definition: “Reducing Clinical Trial Size through Virtual Patients” ties virtual-patient modeling to a concrete trial purpose [166]. The full report should keep the early-2024 scope traceable through planning, extraction, writing and review, covering the eight directions’ cases, companies, projects and technologies and placing global centers in the separate table.

### 7. Personalized Medicine

**Personalization works best around a defined decision.** The clearest applications estimate an individual physiological quantity, evaluate a treatment strategy, or monitor an interpretable disease mechanism. HeartFlow and the January cardiac pipeline provide dated examples; PAH monitoring, OPTOMICS, Neurotwin, and distributed health-twin frameworks illustrate additional research architectures.

| Specific application case | Companies, institutions, or projects | Inputs and key technologies | Individualized decision | Status |
|---|---|---|---|---|
| Coronary disease assessment | HeartFlow Inc. | Patient CCTA; AI; fluid dynamics | Assess physiological significance of narrowing | Clinical use |
| Cardiac drug-response modeling | January 2024 cardiac pipeline | CMR; ECG; Bayesian fitting; electrophysiology | Explore individual electrical response to dofetilide | Single-subject demonstration |
| PAH remote monitoring† | Alan Turing Institute; NHS context | Implanted monitors; imaging; cardiovascular models | Track physiology and simulate treatment strategies | Research objectives |
| Type-2-diabetes characterization† | OPTOMICS; complementary DIGIPREDICT community | Molecular phenotyping; optoacoustics; AI | Improve prognosis and patient stratification | Development/validation project |
| Individualized neuromodulation† | Neurotwin | Neuroimaging; electromagnetic and physiological models | Predict brain response to electrical stimulation | Research and planned testing |
| Personalized self-/joint management† | EPI; COMMIT2DATA | Distributed analysis; BRANE orchestration | Support personal interventions across data sites | 2024 infrastructure proof of concept |
| Insulin-strategy optimization† | Personalized-diabetes research framework | Glucose histories; RNNs; Soft Actor–Critic learning | Test individual glucose-control strategies | Simulation-oriented demonstration |

Sources are the January position paper [1], cardiac pipeline [8], Turing PAH project [36], OPTOMICS/Neurotwin profiles [37], EPI publication [38], and diabetes framework [39].

**HeartFlow personalizes a clinical measurement.** Its contribution is not merely predicting a population risk score from patient characteristics. It builds a particular patient’s coronary geometry and simulates physiology within that geometry, producing information used in that patient’s diagnostic and treatment pathway. It therefore illustrates why an episodically personalized model can be clinically useful without continuously streaming new measurements.

**The cardiac pipeline personalizes intervention response.** The January 2024 CMR/ECG study goes beyond reconstructing anatomy by fitting electrical behavior and then changing drug-sensitive model properties. The personalized model becomes an experimental environment for asking how an intervention could alter that individual’s cardiac electrical activity. Its single-subject demonstration supports feasibility, while treatment selection would demand validation in the relevant disease setting. [8]

**The PAH project adds longitudinal physiology.** The Alan Turing Institute’s project concerns pulmonary arterial hypertension, or PAH, and proposes updating cardiovascular models with implanted-monitor and imaging data. Patient-specific parameters include cardiac contractility, blood volume, and vessel compliance—the capacity of blood vessels to expand in response to pressure. Planned uses include forecasting wellbeing, evaluating drug response, and testing treatment strategies. [36]

**Model selection is part of personalization.** The project includes sensitivity analysis with model emulators to determine which models and parameters can be supported by the available data. This matters because several parameter combinations may explain similar measurements. A fitted parameter should therefore be treated as an estimate constrained by the observations, not automatically as a directly measured biological fact.

**OPTOMICS joins molecular and physical phenotyping.** The project combines molecular profiles, portable non-invasive optoacoustic measurements, and AI to develop a type-2-diabetes twin. Its intended applications span target identification, prevention and prognosis, and stratification of people at risk of diabetes complications. Its emphasis is heterogeneous disease development, rather than a single uniform trajectory for every patient. [37]

**Neurotwin models a treatment’s physical interaction.** Personalized hybrid brain models combine electromagnetic physics, physiology, and neuroimaging to predict responses to electrical stimulation. The project targets individualized neuromodulation for conditions including Alzheimer’s disease and epilepsy, with randomized double-blinded testing described as a planned activity. Here, the intervention’s physical mechanism is central to the model, contrasting with a purely statistical forecast from past outcomes. [37]

**EPI addresses fragmented personal data.** The Enabling Personalized Interventions project within COMMIT2DATA develops personalized digital-health-twin applications for self-management and joint management with care providers. Its framework combines distributed analysis infrastructure with BRANE to orchestrate applications across multiple sites. The 2024 publication describes a proof of concept applied to one use case. [38]

**Distributed infrastructure is an enabling capability.** Personal information often resides with different healthcare organizations and cannot simply be consolidated without legal, privacy, or operational consequences. Coordinating analysis across those sites helps make personalized modeling feasible. It does not, on its own, establish that the resulting model improves treatment or that distributed computation resolves every governance requirement.

**The diabetes comparator explores adaptive treatment policies.** A separate date-qualified 2024 framework combines a patient’s simulated twin with Soft Actor–Critic reinforcement learning, which learns actions through simulated experience, and recurrent neural networks for glucose forecasting. It targets a glucose range of 70–180 mg/dL and reports average prediction root-mean-square error of 19.83 mg/dL. Its illustrative time series covers ten days for one adult patient at three-minute intervals. [39]

**Prediction error is not treatment benefit.** The glucose forecast and the simulated insulin strategy measure different capabilities. A model can predict glucose reasonably well yet still make unsafe treatment decisions under unusual meals, illness, or physiology. The clinically relevant transition is from model performance to prospective evidence that acting on the policy improves control without unacceptable hypoglycemia or other harm.

**Prevention connects with wellness research.** Miami’s MILBox and Mount Sinai’s DigiTwin profiles, developed in the next subsection, extend personalization toward sleep, activity, environmental exposure, and health trajectories. Their role in this report is preventive phenotyping and research infrastructure, rather than demonstrated treatment optimization.

**The practical takeaway is decision-centered personalization.** A useful patient twin need not model everything, but it must show that its individualized predictions improve the particular monitoring or treatment decision for which it is used.

### 8. Wellness

**Measured prediction is ahead of preventive claims.** The January 2024 Arivale-based analysis provides a substantial longitudinal dataset and explicit modeling comparisons. MILBox provides a named home-sensing architecture, while Mount Sinai’s DigiTwin profile describes a more extensive healthspan cohort. These programs address related goals through very different observation periods and data burdens.

| Specific application case | Companies and institutions | Inputs and technologies | Proposed or demonstrated twin function | Scale and status |
|---|---|---|---|---|
| Arivale metabolic-trajectory modeling | Zhang and colleagues; Arivale dataset; Phenome Health support | Clinical data; proteins; metabolites; ML; SPOKE graph | Predict biomarker changes and interpret biological relationships | 1,131 six-month and 639 one-year records |
| MILBox personalized wellness† | University of Miami TheMIL; AWS; Open Health Network | Blood pressure; actigraphy; weight; air quality; phone/cloud | Build individual profiles and study sleep–health relationships | First-phase target: 1,500; seven-day capture |
| Mount Sinai DigiTwin† | BMEII; Icahn School of Medicine; Oura; SiPhox | MRI; genetics; multiomics; wearables; home sensors; eHive | Build longitudinal health profiles for future AI models | Target: 1,000; 24-month participant protocol |

The evidence comes from the 26 January 2024 Arivale analysis [9], Miami’s MILBox account [40], and Mount Sinai’s study profile [41].

**Arivale supplies longitudinal observations.** Zhang and colleagues analyzed data originating from approximately 5,000 deeply phenotyped wellness-program participants. After filtering, 1,131 participants contributed six-month observations and 639 contributed one-year results. The study analyzed 1,042 features: 262 proteins + 710 metabolites + 70 clinical-laboratory or demographic variables. [9]

**The models predicted changes, not diagnoses alone.** Targets included glycated hemoglobin, or HbA1c, glucose, insulin, insulin resistance, and estimated glomerular filtration rate, or eGFR, an indicator of kidney filtration. Models predicted changes from baseline at approximately six months and one year. Classification tasks identified increases of at least 5% in the selected measures, or a decrease of at least 5% for eGFR.

**The comparison tested additional data value.** Using ten-fold cross-validation, the study found that full clinical, proteomic, and metabolomic feature sets each performed better than demographics-only features for predicting changes in HbA1c, glucose, and eGFR. Proteomic and metabolomic sets also outperformed clinical feature sets for six-month eGFR and glucose prediction. By contrast, insulin and insulin-resistance prediction performed approximately similarly across feature sets. [9]

**More measurements were not uniformly better.** That counterexample matters for wellness programs, where adding costly molecular assays can appear inherently desirable. The study supports extra information for particular targets, not a blanket claim that the largest panel improves every forecast. All predictor sets included the baseline value of the outcome; the combined modeling set therefore contained 1,043 inputs, distinguishing it from the 1,042-feature measurement catalog.

**The knowledge graph adds interpretation.** The SPOKE biomedical knowledge graph connected predictive features with known disease relationships and potential intervention pathways. Examples included links involving NLRP3 in diabetes and TNF-related biology in kidney disease. These connections help explain and prioritize hypotheses; they do not convert a predictive association into proof that changing the connected molecule will improve health. [9]

**The implemented system remains a component framework.** The study concentrated on machine learning and knowledge graphs, with direct integration of mechanistic models identified as the next step in its architecture. Its participants were predominantly generally healthy, and observations were relatively sparse. Thus, the demonstrated result concerns short-term biomarker prediction in a wellness dataset, rather than a validated continuous model of established type-2-diabetes progression.

**MILBox captures everyday context.** The University of Miami’s Media and Innovation Lab, TheMIL, works with AWS and Open Health Network to combine home and body-worn measurements. The initial kit includes an ambulatory blood-pressure monitor, an actigraph for sleep–wake activity, a smart scale, an air-quality device, and a mobile phone transmitting data to the cloud. [40]

**The initial scientific question concerns sleep.** The project studies relationships between poor sleep, including sleep apnea, and conditions such as heart disease and dementia. Measurements over seven consecutive days are combined into a person-specific “biological health algorithm.” The first-phase target is 1,500 participants, emphasizing traditionally underserved communities and communities of color in Florida and the New York tri-state area. [14]

**Its architecture separates collection from intervention.** AWS supports cloud analytics and remote-monitoring infrastructure, while Open Health Network supports acquisition, analysis, the smartphone application, and the research algorithm. The project describes virtual evaluation of treatment or wellness options as an eventual capability. Seven-day profiles can characterize observed activity, sleep, and exposure patterns, but the longer-term disease relationships remain a separate modeling and clinical question.

**Mount Sinai describes deeper longitudinal profiling.** Its supplementary institutional profile combines whole-body MRI, clinical and physical-function tests, genetics, multiomics, lifestyle questionnaires, wearables, and environmental-exposure measurements. The stated goal is a 1,000-person cohort assembled over a three-to-five-year horizon, with each participant following a 24-month protocol involving baseline, one-year, and two-year visits. Those are different timelines: cohort assembly versus individual follow-up. [41]

**Named devices support the data pipeline.** The protocol includes an Oura activity ring, air-quality monitoring, at-home blood-sugar monitoring, and SiPhox EasyDraw capillary blood collection for laboratory multiomics. Mount Sinai’s eHive application supports consent, questionnaires, reminders, researcher communication, and connection of home-device information with a secure study database. [41]

**The study is explicitly observational.** Mount Sinai states that the collected information is for research, that the study does not provide diagnosis or individualized treatment recommendations, and that it does not evaluate the safety or effectiveness of an AI tool. Its objective is to create the longitudinal resource from which future health and aging models can be developed—not to present an already validated preventive service.

**The three approaches answer different questions.** Arivale asks whether measured features improve prediction over a simpler baseline. MILBox asks how an individual’s home environment and sleep-related behavior relate to health. Mount Sinai’s profile asks whether sufficiently broad and repeated observations can support future models of health trajectories. Their success should therefore be judged against those specific purposes rather than a common marketing claim of “whole-person optimization.”

**Preventive benefit requires an action pathway.** For researchers and innovation teams, the consequential step is showing that model-generated feedback changes decisions or behavior and produces meaningful health benefit. Access also matters: a model built from participants able to complete extensive testing may behave differently in populations with different resources or disease burdens. The January 2024 Annual Review identifies socioeconomic barriers and dataset representativeness as central issues for health-twin deployment. [42]

**The practical takeaway is prevention research, not assumed prevention.** Wellness twins offer promising individual profiling and forecasting, while demonstrated gains in adherence, disease risk, or healthspan depend on evidence that acting on their outputs helps people.

**Additional documented evidence**

**Wellness: cases and evidence**

Wellness covers prevention, healthy lifestyle and population well-being. For early 2024, count a case only when data link to an updateable model and prediction, simulation or feedback; trackers, PHRs and generic AI remain adjacent. Human-body work names wearables/on-body sensors, IoT and multimodal AI; wellness apps are distinct from medical software and were excluded from one digital-therapeutics review [192][190][185]. WHO adds population/community monitoring; market material names cloud/AI/health-IT but no named case [182][191].


- **WDT-RPMS (proposed):** The Wellness Digital Twin using Remote Patient Monitoring System combines RPMS, EMR and other datasets; sensors, Bluetooth/mobile apps, cloud and AI update it, generating predictive alerts and prescriptions for pose, breathing, blood pressure, glucose, medication and mental-health risks. Deployment is unestablished [94].
- **SmartFit (experimental; 11 athletes):** Wearable/IoT activity, sleep, food and mood data are imputed and classified; human twins predict fitness and counterfactuals suggest behavior changes. Missing/noisy data and the method’s non-health-specific scope limit generalization [120].
- **Prudential Pulse:** A 15-minute, over-50-question survey generates the source’s 3-D organ “digital twin”; Prudential used Babylon Health’s chatbot for symptom checking and consultation recommendations. An update loop is not shown [80].
- **US20220301715A1 (patent application, 2022-09-22):** Ai-Genetika Inc., doing business as Biotwin, proposed digital-twin biomarker profiles for sports performance, wellness and health; no deployment or outcome is reported [81].
- **Diabetes HDT prototype (retrospective, 2024-10-22):** GameBus, SugarVita and Trivia use bidirectional patient-twin data; health-literacy, daily-activity and player-type models update content and quiz difficulty, while E-DES simulates glucose from diet, activity, medication and stress. DiaGame, STRAP and HealthyW8 are associated projects; this is a post-cutoff proof of concept [183].

The cited cards name no company role for WDT-RPMS or SmartFit.


**My Wellness Portal** (AHRQ; University of Oklahoma, James Mold and Zsolt Nagykaldi) used a PHR and Preventive Services Reminder System for profiles, a three-year plan, reminders and recommendations. It had a 30-patient pilot and an RCT of 422 adults plus parents of 116 children at eight OKPRN practices; preventive-service delivery improved and visits fell, but the source does not label it a twin [84]. **Wellness Check Initiative** (Kindred–University of New Brunswick/PITCH–VeroSource) launched in November 2019 and was planned through fall 2021; over 185 caregivers and over 110 clients in May 2021 used a smartphone app to flag changing physical/mental health and inform medication or mobility actions. Twin status is unresolved [189].

A June-2024 retrospective describes **VivaScore** (Alula, Ally Health and Hannover Re): a 12-week, 30-employee pilot, with calendar years for November–January unspecified, used 30-second rPPG checks, wearables, blood tests and in-person checks to recalculate a 0–100 score and refer high-risk users; it is not explicitly a twin [71]. A 2017-07-17 study of 108 people used personal, dense, dynamic data clouds but reports no twin loop [184]. TechCrunch’s adjacent examples on January 18, 2024—NuraLogix MagicMirror, Vivoo, Zoe, 23andMe and Apple Watch—used facial, urine/glucose/stool, genetic or ECG inputs; several claims were investigational, non-diagnostic or unvalidated [187].

- **MILBox (University of Miami, 2022):** 1,500-participant target in Florida and the New York tri-state area; home/wearable sensors planned seven days of sleep, weight, air-quality and stress data. A biological-health algorithm would serve as a twin for AI testing of wellness/treatment options. AWS supplied cloud ML and EHR-data-lake support; Open Health Network’s PatientSphere 2.0 handled acquisition/analysis, with remote monitoring, blockchain and big-data processing [102].
- **Twin Health (30 January 2024):** its Whole Body Digital Twin combined sensors, routine blood tests and mobile self-input; AI/foundation models generated nutrition, activity and sleep insights for patients and physicians, targeting obesity, diabetes and hypertension [72]. Retrospective reports name Human Digital Twin for Fitness Management (Fitbit/MyFitnessPal→athlete recommendations), SmartFit (IoT/wearables→behavior alerts), a smart-clothing twin (sensors→audio/temperature feedback), and a mental-wellbeing twin (watch/phone/social data→anxiety detection) [63][193].
- Two-subject DTSM used Pixel-watch HRV, sleep/activity data, synthetic data and ML for stress prediction; another reported 1,800 type-2-diabetes patients received food suggestions from diet, glucose, metabolic and lifestyle data over one year, with HbA1c/medication improvement [64][159]. Employer apps, Kia Aroha’s 2019 Hauora day and Wellstar–Spatial/Catalyst’s 2022 audio pilot show support, not confirmed updating twins; NTT Research’s wellness expansion was planned [195][121][122].
- For the research purpose, Wellness makes the DT4H loop—data→model→recommendation→feedback—concrete, but privacy, validation and human oversight remain necessary [63][72]. No cited source establishes a major center; All of Us is a U.S. data program, not a documented twin [186]. The 20-February-2024 IEEE item is metadata-only; 2025 MCP/A2A evidence is retrospective [181][194].

Wellness is a distinct subsection: Twin Health’s Whole Body Digital Twin turns sensor, blood-test and app data into nutrition, activity and sleep insights via AI/foundation models [72]. SmartFit is a named computational framework using wearable data and human twins for ML predictions/prescriptions despite missing/noisy inputs; WDT-RPMS combines remote monitoring with EMR/other data for population insight, while population twins use updating data to simulate and feed back for planning [120][94][180].

Wellness links DT4H to a patient-facing use: Twin Health turns personal data into nutrition, activity and sleep insights [72], while real-world data benchmarks effectiveness, safety and equity [188]. Keep it as the final named direction; carry the complete request—cases/projects, actors, technologies, mechanisms, sources and the center table’s name/region/focus/objectives—through planning, extraction, writing and review for early 2024 [72].

Wellness cases include Twin Health’s Whole Body Digital Twin, which turns sensor, blood-test and app data into wellness insights [72], and MILBox: AWS cloud ML plus an EHR-linked data lake combine home/on-body sensor data into an individual twin for intended virtual wellness/treatment testing; its first phase was seeking 1,500 participants [102]. Real-time inputs can expand the model and patients and physicians can review insights, but privacy, validation, data checks and human judgment remain necessary [102][72].

### What adds value across the eight directions?

**The common feature is safer experimentation.** Hospitals test operational changes, engineers test device configurations, surgeons test spatial plans, and drug developers test cohort or treatment assumptions. The benefit is not simply digitizing a real-world object; it is making a consequential comparison that would otherwise be difficult, costly, slow, or risky.

**The feedback requirement varies with the task.** Adaptive feeding benefits from repeated process measurements because cells and nutrients change during a run. Surgical geometry may remain useful from one preoperative scan, while a trial-control forecast can be deliberately fixed before randomization. Connectivity should therefore be assessed alongside intended use rather than treated as the sole measure of clinical maturity.

**Prediction and action require separate evaluation.** HeartFlow’s diagnostic performance, BioDT’s process-control result, iKidney’s registration time, and Arivale’s biomarker forecasts measure different things. None is a universal score of “digital-twin accuracy.” The most important practical question is whether the measured capability is strong enough to support the action that follows.

**Hybrid approaches address complementary weaknesses.** Mechanistic models encode physiological or engineering relationships; data-driven models find useful patterns and can accelerate expensive simulations. Combining them can improve practical modeling, but it also requires checking how measurement error, uncertain parameters, and model assumptions propagate into the final recommendation. The January 2024 position paper therefore emphasizes validation data, interoperability, computational efficiency, and a clear context of use alongside model development. [1]

**Additional documented evidence**

**Taxonomy and common evidence test**

Part One keeps exactly the eight user-supplied directions: Hospital Management and Care Coordination; Medical Device Design; Biomarker and Drug Discovery; Biomanufacturing; Surgical Planning; In-silico Clinical Trials; Personalized Medicine; and Wellness. These are application categories, not an exhaustive universe. DT4H here means a health patient, organ, device, process, or care system linked to a virtual representation by live data and used for updating, monitoring, prediction, simulation, optimisation, or decisions [51][52]. A static model, dashboard, isolated prediction, or ordinary simulation is not automatically a twin: each case must identify its subject, inputs, model/update loop, action, evidence stage, and limitation. Companies, projects, and technologies remain distinct typed items.

**Evidence anchors for the taxonomy**

- **Hospital Management and Care Coordination.** Hospital digital twins use treatment counts, patient numbers, waiting times, sensors, and IoT; simulation can optimize internal processes and resources [52]. A named facility example is the digital-twin-aided facility-management case at Shanghai Tongji Hospital [50], but the available evidence does not establish its company, maturity stage, or outcome.
- **Medical Device Design.** The King’s College London record for *CDT DT4H: Optimising implanted cardioverter defibrillator devices through patient-specific device configuration, implant strategies and therapy delivery* classifies it as “Digital Twins for Healthcare” and “Project: Research,” with effective dates 1 October 2023–31 March 2027 [53]. Martin Bishop and John Whitaker are listed as investigators; no commercial company role is established.
- **Biomarker and Drug Discovery.** BMIS-DT is a model/intended application: wearables capture biomarkers continuously, the model simulates daily fluctuations, and threshold exceedance triggers proposed interventions for early deterioration, telemonitoring, and patient-specific treatment [52]. TechWear uses wearables or smart patches, IoT, cloud systems, AnyLogic, and synthetic or real-time data; molecular modules and virtual experiments support genes, pathways, drug targets, and biomarkers [52]. Atomic AI, Turbine, and XtalPi are named in related drug-discovery references, but a complete case role is not documented for each [52].
- **Personalized Medicine.** Examples include Duke blood-flow simulations, Johns Hopkins ablation-response models, the NHS–Imperial report of **over 3,800 digital heart twins** for patients with pulmonary arterial hypertension (date not stated), personalized heart twins for scar-dependent ventricular tachycardia, and Dassault Systèmes’ MediTwin lung/brain simulations [51]. FEops HEARTguide supports patient-specific heart-twin planning and device sizing; Sim&Cure’s aneurysm twins support implant selection, while Philips’ HeartNavigator supports cardiac imaging and analysis [52]. A retrospective review published 3 June 2024, covering literature through 24 December 2023, reports diabetes insulin management, a 319-patient one-year nutrition trial, 100 virtual radiotherapy patients (about 6 additional median progression days or 16.7% less radiation), 3,000 virtual cancer-pain patients (16% lower average pain and 23 additional pain-free hours), and risk models for multiple sclerosis and post-hepatectomy liver failure; aggregate outcome counts were 80% (24/30), 70% (7/10), and 100% (5/5) across management, therapy-effect, and risk-prediction categories [54]. These are distinct study stages, not proof of routine deployment.

DT4H is an updateable, data-linked patient/organ/device/care-process representation for monitoring, forecasting, simulation and decisions—not a static model or AI alone [56]. Retrospective Ottawa evidence (2024-08-08) adds EHR, wearable and patient data; Cardio Twin and COVIDMe were proofs of concept [57].

Surgical Planning is human-in-the-loop anatomy/path simulation [55]. By early 2024, cited cases included HeartFlow, SurgiNet Twin, NeuroTwin, tumor-growth/Twin-S, microwave ablation, VR robotics, vertebroplasty, liver puncture and QoS telesurgery . CT/MRI/DICOM, CTA-CFD, fMRI/DTI, segmentation/biomechanics, differentiable models, sensors and VR update anatomy and compare paths; surgeons decide . Dassault Systèmes/inHEART are developers; AVATAR MEDICAL supplied VR-planning software but had no study role [55]. Retrospective 2025 evidence leaves clinical benefit unestablished [55].

Personalized Medicine includes Molecular Twin (pancreatic multi-omics), CardioVision (aortic stenosis) and E-T2D HDT [56]. IoMT sensors/app plus LB-MPC were simulated with 15 elderly patients in 2023: time-in-range rose from 3–75% to 86–97%, and insulin use fell 14–29%; no implemented intervention was reported [56]. Affiliations included TVS Motor/TVS-Sensing, Jothydev’s, Madras Diabetes, SharkNinja and Pavia; roles were unspecified [56]. Retrospective 2024-05-13 laboratory proposals cover reference intervals, tumor response and test interpretation .

DT4H links entities to data-updated virtual models for monitoring, simulation, prediction and decisions; static/teleconsultation-only systems fail [58][59]. Hospital twins forecast beds, staffing and flow [58]; retrospective surgical evidence updates CT/MRI anatomy with intraoperative sensing for rehearsal . Personalized Medicine uses clinical/genomic/imaging/wearable data for tailored care; 2019–23 examples include Cardio Twin, ICD, fentanyl and prostate-cancer twins [58]. Philips launched Heart Digital Twin; Siemens Healthineers developed Digital Patient Twin; cutoff status is unverified . Biomarker/drug work is AI/ML-level, no outcome named [59]; retrospective Wellness evidence uses wearable data and feedback .

In-silico trials: digital twins simulate drugs/devices/interventions; VHT links data to models for validation, but is proposed, not deployed [61]. Personalized Medicine (retrospective): ReplayBG simulates diabetes therapies; Twin Health’s IoT twin recommends diet/lifestyle; a 2023 glioma twin used MRI/Bayesian calibration for RT [48–52].

DTs are real-time, data-linked, updateable models for simulation/prediction, not static models [62][63]. Patient twins aid diagnosis, treatment and monitoring; TWIN (2023), CRT, cancer avatars and stroke forecasting are named examples [63]. Virtual cohorts refine trials; wellness twins use wearables/cloud, including Fitness Management (2020) [63].

Later: DTs update models, not static ones [66]; In-silico clinical trials use twins for efficacy/safety/design [65]; Personalized Medicine updates patient models [66][67]; Wellness DTSM predicts stress via wearables [64].

**Discovery and biomanufacturing**

Organ-level twins support drug discovery and precision medicine; graphical biomarker models encode organ interactions for interpretable bedside use. Physics-based models, AI/ML and DAGs are named technologies; GNN link prediction for synthetic lethality and drug–target interaction remains proposed, not a completed case or project.  “A Flexible Digital Twin Framework for ATMP Production—Towards an efficient CAR T Cell Manufacturing” (2024; date incomplete), affiliated with Fraunhofer IPA and Universität Stuttgart, digitalizes, monitors and manages CAR-T/ATMP production through process/task/skill/microservice layers, modular updates and manual/automated operations; supplied evidence names no separate project or company role. [68]

**Surgical planning**

Cincinnati Children’s Heart Institute used VR heart twins for complex cardiac planning (15 November 2023); Morales and Moore led it, a Turner Farm Foundation gift of $2.7 million expanded it, and novel approaches reportedly occurred there first; no commercial company is named, although worldwide clinician collaboration was described. [70] Cardiac-CT mixed-reality twins for 50 patients with complex heart defects (September 2020–December 2022) changed strategy in 68% of cases after standard planning; AI still required manual correction (report: 18 September 2024). [49] A VR review (25 April 2024) lists biventricular repair, lung resection/segmentectomy, aneurysm clipping, liver tumours and IMHOTEP/CorFix/3D Slicer/Surgical Theater/MedicalVR/Specto/Enduvo/SurgeryVision/BananaVisionVR/3D Systems; direct roles and DT4H linkage are unverified, and evidence remains experimental/anecdotal. [69]

**In-silico trials and personalized medicine**

**Wellness and timing**

Twin Health’s Whole Body Digital Twin (30 January 2024) uses sensors, blood tests/mobile inputs and AI/foundation models for nutrition, activity and sleep insights targeting obesity, diabetes and hypertension; it partners with employers and health plans, with privacy, validation and human oversight required. [72] A later, not explicitly twin-labelled VivaScore pilot used Alula, Ally Health and Hannover Re (12 weeks; 30 employees); rPPG, wearable and clinical data updated a 0–100 score and reports for intended risk screening. [71] Evidence leaves 31 March versus 30 April 2024 unresolved: 14 March precedes 31 March, while 25 and 30 April expose the boundary; post-cutoff sources are retrospective. [73][69][74]

Declare an early-2024 cutoff; later evidence is retrospective [76]. Eight directions: Hospital Management and Care Coordination, Medical Device Design, Biomarker and Drug Discovery, Biomanufacturing, Surgical Planning, In-silico Clinical Trials, Personalized Medicine, and Wellness. Case rule: named subject/task + linked data + updateable model + prediction/simulation + action; static models and generic AI are adjacent.

Medical Device Design cases: ankle implant, tricuspid replacement, failed-hip redesign, heart valves, drug-eluting-stent release, and syringe verification; models, finite-element analysis, VR and V&V connect data to design [86][105][106]. Medtronic used twins for FDA questions (two years and >€10m saved) [86]. Living Heart’s 3-D models support device testing and FDA evidence [107]. AstraZeneca’s CP1108/MYSTIC twins generated vPhIII for PD-L1 biomarker discovery; validation remained necessary [88].

Biomarker/Drug Discovery: digital twins model molecules→patients for targets/biomarkers, design, dosing and trials [108][110][111]. Insilico dev. Rentosertib (PandaOmics→TNIK; Chemistry42→inhibitor), Phase IIa: 71 IPF patients/12 wk at 60 mg QD, FVC +98.4 vs −20.3 mL placebo; Fosun co-dev; Sanofi target; Exelixis/Menarini license [108].

Retrospective evidence: Biomarker/Drug Discovery uses disease, cell, organ and patient twins for target/lead discovery, optimisation, preclinical tests and trials; named examples include MedGAN, NP-VAE, TransDTI and liver twin [113]. DeepLife/Turbine use multi-omic cell twins [115].

Biomarker and Drug Discovery: virtual liver (2020) [118]

Biomanufacturing: BioDT/CHO twin uses sensor-updated kinetic models and HMI to predict metabolites and feed glucose; cell density +14.8% vs batch [91]. Cases: GSK vaccine, Pow.Bio; Bio-SoS/DoE calibration [75][85][98].

Biomanufacturing twin: 24.6% glycan MPC d14 (2026) [87].

2024: Biomanufacturing: CAR-T twin monitors production [109]; Surgical Planning: Twin-s: skull-base twin [82].

Wellness: Biotwin’s US20220301715A1 (2022 application) proposes biomarker profiles→wellness actions; no deployment/outcome [81]. My Wellness Portal (AHRQ), Wellstar/Spatial, and Hauora: twin status unverified [84][122][121].

rejected: number_unsupported. Hospital Management and Care Coordination advances the Digital Twin for Health application purpose because operational, clinical, and patient-movement data update a hospital twin for simulation, prediction, and capacity decisions; 9 out of 17studies [77][100][101] illustrate this mechanism. The case also supplies an institutional-map example, while patient-data safety, legal compliance, cybersecurity, and interoperability remain risks .

Medical Device Design supports the application purpose through a traceable biomedical-device twin linking CAD, analytical modelling, FEM and empirical testing in an MBSE environment; the validated case reduced model error from approximately 30% to within experimental repeatability and reported a 70% increase in interface performance [96]. The Living Heart project and Toobler provide named project/company anchors; however, modular, interoperable frameworks, standardized data and empirical validation are material conditions limiting unsupported virtual-only use [104][95][103][96].

Biomarker and Drug Discovery supports the application purpose by combining multilayer modules of mRNAs, genes and proteins with wearable biomarker streams to simulate fluctuations, disease mechanisms and treatment response; AstraZeneca’s computational-pathology case makes predictive-biomarker discovery concrete [52][88][112][113]. A reported model reached 0.88 ROC AUC [108], while causal AI is needed in drug development because pattern recognition alone does not establish causation [114], providing a specific research-industry anchor and validity caution.

Biomanufacturing broadens the application purpose from care to production: BioDT links a CHO-cell-culture/miniature-bioreactor system to a cloud HMI, uses sensors to update the twin and simulates conditions for control; GSK’s glycan-adaptive case monitored G0F, G1F and G2F in two 5 L bioreactor runs [91][75][87][89]. These named process examples anchor the technology/institutional map, but PAT data quality, calibration and interoperable models are conditions for reliable decisions [89][90].

Surgical Planning supports the application purpose by converting patient-specific imaging into models explored in VR/AR to rehearse and guide procedures; HeartFlow, SurgiNet Twin, NeuroTwin, Twin-S and ARCollab provide concrete cases [78]. Dassault Systèmes and inHEART, with DICOM, segmentation, immersive reality and differentiable simulation, anchor the actor/technology map, while fidelity monitoring remains important for reliable planning [55][119].

In-silico Clinical Trials directly support the application purpose by coupling patient/device models, virtual cohorts and study protocols to simulate inclusion criteria, dose, safety, failures and outcomes; a multi-arm assisted-reproduction study used retrospective patient twins, and the Avicenna Consortium’s roadmap anchors the institutional map [97][117][93][92]. One application used 2986 digital patients [106], but good simulation practices and credibility assessment are needed before results guide clinical or regulatory decisions [92][79].

Personalized Medicine supports the application purpose by integrating clinical, physiological, molecular, lifestyle and genetic data into a continuously updated, patient-calibrated twin that simulates disease progression and treatments; cases include elderly type 2 diabetes, an oncology tumour twin and assisted reproduction [54][83][93][99][116]. The diabetes case involved 15 patients, and Kalasalingam Academy of Research and Education anchors the actor map, while continuous data capture and patient-specific calibration condition individualized recommendations [56][60].

Wellness extends the application map to prevention and healthy-lifestyle support rather than diagnosis or treatment: WDT-RPMS combines remote-monitoring, EHR and human data, while wearables build twins for monitoring and personalized advice; SmartFit and My Wellness Portal at the University of Oklahoma Health Sciences Center are named cases/projects [94][80][63][120][84]. MILBox involved 1,500 participants over seven consecutive days through an AWS/EHR cloud platform, but limited data may require synthetic data and wellness should not be conflated with medical treatment [102][64][80].

## Part Two: Major Research Centers

**The comparison is program-based and non-ranked.** The tables identify centers, consortia, and institutional teams with explicit health-related digital-twin programs and concrete objectives. They distinguish organizations building shared infrastructure from those developing disease-specific models, population-health systems, bioprocess twins, or training capacity.

### Shared ecosystems and modeling collaborations

| Research Center Name | Region/Community | Research Focus | Main Objectives |
|---|---|---|---|
| EDITH, coordinated by the Virtual Physiological Human Institute [43] | Europe; EU and associated countries; 19 partners | Interoperable organ and Virtual Human Twin resources | Build roadmap, federated repository, and simulation-platform architecture |
| Digital Twin Consortium Healthcare and Life Sciences Working Group†[44] | International industry, research, healthcare, and life-science community | Devices, pharmaceuticals, hospitals, patient journeys, and connected monitoring | Develop use cases, interoperability, privacy-aware sharing, and operational guidance |
| SIMULIA/Dassault Systèmes Living Heart Project [18] | Global academic, clinical, regulatory, and industry collaboration | Dynamic cardiovascular multiphysics and heart–device interaction | Deliver validated models for product development, treatment, and regulatory use |
| DIGIPREDICT and EPFL-CIS community†[37] | European cluster, including Switzerland, with wider international links | Physiological twins; biosensors; AI; organ-on-chip technologies | Develop and validate predictive twins; share methods; advance privacy and sensor standards |

**EDITH coordinates an ecosystem, not one model.** Announced in 2022, EDITH—Ecosystem for Digital Twins in Healthcare—received €5 million from the European Commission and brought together 19 partners. Its participating countries included Belgium, Italy, Greece, Poland, the Netherlands, Germany, France, Spain, Switzerland, and the United Kingdom. The Virtual Physiological Human Institute, or VPHi, coordinates its scientific and technical work. [45]

**Its objectives address shared bottlenecks.** EDITH maps actors, resources, initiatives, and barriers; develops a clinical-deployment roadmap; proposes a federated cloud repository of data, models, algorithms, and good practices; and develops the architecture of a simulation platform. Five prototype domains were selected: cancer, cardiovascular disease, intensive care, osteoporosis, and brain applications. [43]

**The Virtual Human Twin is infrastructure.** The associated January 2024 position paper explicitly distinguishes this vision from a gigantic model that predicts every aspect of a person. It is a distributed collaboration and simulation environment intended to make specialized models easier to develop, validate, reuse, and combine. That distinction makes EDITH especially relevant to researchers working on model interoperability, validation resources, and multiscale integration. [1]

**The Digital Twin Consortium targets adoption.** Its healthcare and life-sciences group covers pharmaceutical R&D and product lifecycles, medical devices, hospital operations, patient journeys, and preventive care. Concrete objectives include identifying simulation scenarios, connecting medical and real-world information, and developing interoperability and data-sharing approaches with appropriate privacy governance. Reduced waiting, improved equipment utilization, and fewer bed shortages are target outcomes, not universal achieved results. [44]

**Living Heart supplies a shared organ platform.** Launched in 2014, the collaboration brings together cardiovascular researchers, clinicians, biomedical engineers, regulators, and industry. Its purpose is consistent, validated cardiovascular models supporting safer devices and treatments. The FDA’s participation reflects a collaborative regulatory-science role; it should not be interpreted as blanket approval of every model or use. [18][34]

**DIGIPREDICT connects complementary technology communities.** Its cluster spans inflammatory, metabolic, degenerative, and malignant disease applications, combining sensing, edge-to-cloud AI, physiological models, organs-on-chips, and nanomedicine. EPFL’s Center for Intelligent Systems is identified as central to the community. OPTOMICS and Neurotwin are complementary projects, rather than interchangeable names for the same consortium. [37]

### Clinical, bioprocess, and health-system research teams

| Research Center Name | Region/Community | Research Focus | Main Objectives |
|---|---|---|---|
| Cleveland Clinic–MetroHealth Digital Twin Neighborhoods, NIH-funded [46] | Cleveland, Ohio, United States; regional communities | EHR-based neighborhood models integrating biological, social, and geographic factors | Test place-based interventions and reduce health disparities |
| Alan Turing Institute cardiovascular-twin project for PAH†[36] | United Kingdom; NHS and PAH patient community | Physics-based cardiovascular models updated from monitors and imaging | Assess feasibility and affordability; forecast response; compare treatments |
| Jiangnan University BioDT team with T&J Bioengineering [2] | Wuxi and Shanghai, China; academic–industry bioprocess collaboration | Adaptive cell-culture models, sensors, and process control | Develop reusable open-source twins and model-guided feeding |
| London Digital Twin Research Centre–Universitas Gadjah Mada [47] | UK–Indonesia; associated Indian and Indonesian partners | AI-centered health-system and pandemic-resilience modeling | Build joint curriculum, exchanges, workshops, and policy-facing training |
| Enabling Personalized Interventions, COMMIT2DATA†[38] | Distributed multi-site healthcare-data community | Personalized digital-health twins and distributed analysis | Orchestrate multi-site applications with BRANE and test use cases |
| University of Miami TheMIL—MILBox†[14] | United States; Florida and New York tri-state communities | Sleep, environment, and individual health profiles | Recruit diverse participants and build sensor-based research twins |
| Mount Sinai BMEII/Icahn DigiTwin Study†[41] | New York City, United States; healthspan research cohort | Whole-body imaging, multiomics, wearables, and health trajectories | Assemble 1,000-person cohort and 24-month profiles for future models |

**Cleveland models the neighborhood as well as disease.** The NIH awarded a $3.14 million grant in February 2023 to work led by Jarrod Dalton at Cleveland Clinic and Adam Perzynski at MetroHealth. The project uses de-identified information from a combined research registry of more than 250,000 patients to build virtual neighborhoods incorporating biological, social, and geographic factors. [46]

**Its objective is place-based intervention analysis.** Proposed scenarios include regional mental-health initiatives, new services affecting community heart-disease burden, and frequent or economically driven residential relocation. The work was motivated partly by prior analysis showing major cardiovascular events in disadvantaged neighborhoods at more than twice the rates predicted by traditional risk tools. This is a population-health twin, not an individual bedside physiological twin.

**The Turing project targets translational feasibility.** Its PAH program combines longitudinal physiology with explicit questions about scalability and affordability in NHS care. Technical work includes sensitivity analysis, model emulators, and comparison of cardiovascular models against PAH pathology. Its distinguishing objective is not simply a detailed heart representation, but a usable monitoring and planning approach supported by available clinical data. [36]

**Jiangnan contributes experimentally connected process research.** The BioDT team’s combination of hardware, open-source modeling, parameter updates, and automated feeding makes it relevant to researchers interested in reproducible bioprocess architectures. T&J Bioengineering’s involvement provides a concrete academic–industry connection. Its laboratory scope should be preserved when considering industrial scale-up. [2]

**London–UGM builds healthcare-system capability.** The British Council–funded 2022–2024 partnership joins Middlesex University London’s Digital Twin Research Centre with Universitas Gadjah Mada’s Faculty of Medicine, Public Health, and Nursing. Associated partners include TCS Research India, PT Sisfomedika, the Kulon Progo Health Office, and Indonesian primary-care sites. [47]

**Its outputs are educational and institutional.** Objectives include a joint UK–Indonesia graduate curriculum, faculty exchange, a public-health workshop, a massive open online course targeting approximately 50 people, and two to four dissemination activities. These objectives are important for adoption capacity and resilience research, while differing from an organ-model center’s technical-validation endpoints. [47]

**EPI focuses on execution across institutions.** Its distributed framework and BRANE orchestration address the difficulty of analyzing health information held in multiple organizational systems. The proof of concept establishes an implementation route for personalized self- and joint-management applications. The concrete research question is how to execute such applications under data-sharing, privacy, legal, and infrastructure constraints. [38]

**Miami and Mount Sinai emphasize cohorts.** Miami’s distinctive feature is seven-day home and body sensing with an explicit underserved-community recruitment emphasis. Mount Sinai’s supplementary profile emphasizes deeper imaging, molecular, and repeated health measurements over 24 months. Both are relevant to prevention research, but cohort construction and future model development should be distinguished from demonstrated clinical decision support. [14][41]

### Specialized institutions within larger programs

| Research Center Name | Region/Community | Research Focus | Main Objectives |
|---|---|---|---|
| Barcelona Supercomputing Center–Centro Nacional de Supercomputación†[48] | Barcelona, Spain; European HPC and personalized-medicine networks | Virtual organs, cellular systems, and high-performance workflows | Develop EDITH use cases and efficient simulation infrastructure |
| INRIA’s EDITH research contribution†[48] | France; computational medicine and European research community | Liver/heart twins, image-based personalization, surgery, and hemodynamics | Contribute modeling expertise, standards, and technical roadmapping |
| University of Liège’s EDITH prototype†[48] | Liège, Belgium; intensive-care and in-silico-medicine community | Glycemic-control twins for intensive care | Prototype virtual trials and personalized glycemic treatment |
| Wageningen University & Research—Bioprocess Engineering†[25] | Wageningen, Netherlands; microbial and pharmaceutical biomanufacturing | Hybrid process models, experimental learning, and metabolism | Design and optimize bio-based processes, including pharmaceuticals |

**These institutions supply distinct building blocks.** Barcelona Supercomputing Center contributes high-performance computing, efficient workflows, and two EDITH use cases. INRIA contributes liver and heart modeling, patient-specific surgery, image-based personalization, and models spanning cells to hemodynamics. The University of Liège provides an early prototype concerning virtual trials and personalized glycemic control in intensive care. [48]

**Wageningen specializes in production systems.** Its digital-twin program combines historical and real-time process information with experimental design, machine learning, and metabolic modeling. For healthcare researchers, its pharmaceutical-biomanufacturing work is the relevant connection; the institution’s broader bio-based-production activities should not all be classified as health digital twins. [25]

**Collaboration choice should follow the problem.** EDITH and the Digital Twin Consortium are natural points of contact for shared infrastructure and interoperability questions. Living Heart, INRIA, and disease-specific clinical teams are more closely aligned with organ modeling and intervention analysis. Jiangnan and Wageningen address production processes, Cleveland–MetroHealth addresses place-based health, and London–UGM addresses workforce and health-system capability. These are complementary roles, not interchangeable measures of research leadership.

**The next gains favor focused translation.** The evidence supports a judgment that specialized organ and process models, connected to useful data and existing workflows, are better positioned for incremental practical gains than an all-purpose virtual human presented as a finished clinical product. Shared repositories, independent validation resources, faster model execution, and privacy-aware collaboration matter because they help such focused applications become reusable and credible. That judgment would change with convincing prospective evidence that broader integrated twins improve decisions across multiple conditions and populations. [1]

**The evidence has distinct measurement bases.** The dated baseline ends on 31 March 2024; † marks supplementary profiles rather than established Q1 deployments, including Mount Sinai’s page carrying IRB Study 25-00148. Numerical results retain their original denominators: patients, vessels, implants, cultures, or analytic records. Recruitment goals and planned objectives are not completed enrollment or outcomes; company-reported results and revenue projections remain identified as such. Variant counts are not diagnostic-prevalence estimates, ECG correlation is not clinical accuracy, and process improvements are not patient benefits. Static models, shadows, and coupled twins retain the distinctions established above.

**The overall judgment is selective confidence.** Digital twins for health were already useful by early 2024 when they answered a narrow, testable question. The most informative examples and research partners are therefore those that connect a specified real system to a credible model, a concrete decision, and an outcome appropriate to that decision.

**Additional documented evidence**

| Entity | Research Center Name | Region/Community | Research Focus | Main Objectives | Research Center Name | Region/Community | Research Focus | Main Objectives |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| European Virtual Human Twins Initiative | The official name shown by the page is “European…[242] | The initiative is described as operating across Europe.[243] | no evidence found | no evidence found | The page gives the initiative's name as “European…[215] | The initiative is described as operating across Europe.[243] | no evidence found | no evidence found |
| Digital Twin Consortium | The exact official name shown is “Digital Twin…[221] | no evidence found | The Digital Twin Consortium states that it works on…[233] | no evidence found | The official name shown on the page is Digital Twin…[245] | no evidence found | The Digital Twin Consortium states that it works on…[233] | no evidence found |
| The Living Heart Project | Dassault Systèmes’ Living Heart Project[216] | no evidence found | no evidence found | No objectives are attributed to The Living Heart…[106] | no evidence found | no evidence found | no evidence found | no evidence found |
| Virtual Physiological Human Institute | The exact name appearing in the source is "Virtual…[236] | The source describes the VPH as a “big, world-wide…[163] | no evidence found | The retained source slice does not state the Virtual…[118] | no evidence found | The source describes the VPH as a “big, world-wide…[163] | no evidence found | The retained source slice does not state the Virtual…[118] |
| All of Us Research Program | The article’s title gives the program name as “All of…[235] | no evidence found | no evidence found | no evidence found | The official name shown on the NIH page is “All of Us…[202] | no evidence found | no evidence found | no evidence found |
| EDITH (European Digital Twin in Healthcare) | The official name shown on the source page is EDITH.[246] | EDITH is identified in the source as “EDITH: European…[67] | EDITH is documented as a European coordinating action…[196] | no evidence found | no evidence found | France; academia, industry, hospitals, patients [240] | no evidence found | VHT roadmap; federated repository; simulation platform [232] |
| Insigneo Institute for in silico Medicine | The page's displayed official name is “Insigneo…[198] | no evidence found | no evidence found | no evidence found | The page's displayed official name is “Insigneo…[198] | no evidence found | no evidence found | no evidence found |
| Auckland Bioengineering Institute | The source names the institution as the Auckland…[226] | EDITH is identified in the source as “EDITH: European…[67] | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Precision Medicine Initiative Cohort Program | The program was formerly known as the PMI Cohort…[239] | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |

The rows span European VHT infrastructure, cross-sector standardisation, organ-specific simulation, whole-body computational medicine and large precision-medicine data resources: the European Virtual Human Twins Initiative is represented by multiscale health-digital-twin infrastructure and ecosystem development [208][213]; Digital Twin Consortium by Boston/global cross-sector coordination [228][231]; The Living Heart Project by a global, about-150-partner electro-mechanical heart simulator and cardiovascular translation [234][217][227][200]; Virtual Physiological Human Institute by international individualized VPH/in-silico modelling and clinical adoption [201][232][244]; and All of Us by U.S. precision-medicine data without a dedicated digital-twins-for-health focus [202][223]. EDITH adds Barcelona-based European roadmap, repository and simulation-platform work [219][232][218]; Insigneo adds Sheffield-based international VPH and paediatric digital-health/in-silico work [203][204][199]; Auckland Bioengineering Institute adds New Zealand-based personalised physiological twins and clinical translation [247][225][230]; and PMI-CP adds a U.S. longitudinal cohort of one million or more volunteers but no documented digital-twin focus [237][248].

**Candidate rows and screening status**

| Research Center Name | Region/Community | Research Focus | Main Objectives |
|---|---|---|---|
| **The Living Heart Project** — project-based candidate; qualifying-center status not established [200] | Principal geographic base is not stated in the permitted evidence. The documented community comprises cardiovascular researchers, medical-device developers, practicing cardiologists, treatment and device-development teams, clinical practitioners, and statisticians [200]. | Dassault Systèmes’ Living Heart initiative is described as creating digital heart models. Its SIMULIA Living Heart Human Model reportedly achieved a three-dimensional realistic whole-heart simulation in **2014**, with four-chamber electrical, structural, and fluid-flow physics; the project also used AI to generate virtual populations from virtual-twin data [200]. | Support treatment creation, device development, clinical-practice applications, statistical analysis, and virtual-population testing. The project is clearly health-digital-twin relevant, but the evidence does not establish it as a qualifying research center or consortium by the cutoff [200]. |
| **Virtual Physiological Human Institute for Integrative Biomedical Research (VPH Institute)** [201][229] | European and international. It is described as an international not-for-profit organization representing the VPH and in-silico-medicine community, including scientists, clinicians, healthcare professionals, policymakers, regulators, and industry [201][222]. | The VPH/in-silico-medicine field uses individualized physiology-based computer models, simulations, and data-driven models across prevention, diagnosis, prognosis, treatment, and biomedical-product design. VPH conference materials also identify digital twins, clinical decision-making, treatment development, and clinical trials as research themes [201][222]. | Realize, adopt, and use the Virtual Physiological Human in research and clinical practice; coordinate policy, funding, regulatory, clinical, and industrial stakeholders; support research continuity, project proposals, tool sharing, and translation from fundamental research to patient care [201][222][229]. It is the strongest organizational candidate in this group, although the supplied evidence does not itself issue a final “major DT4H center” determination. |
| **All of Us Research Program** — data-program candidate; excluded from the qualifying DT4H-center roster [202] | United States and its territories, serving participants, affiliated researchers, and health-care provider organizations. The protocol describes adults aged **18 years and older** living in the United States or its territories [202]. | A large NIH health-data program collecting surveys, electronic health records, physical measurements, biospecimens, and digital-health data from phones, apps, and wearable devices. A specific digital-twin-for-health research focus is not established in the permitted evidence [202]. | Build a large health database to study how biology, lifestyle, and environment affect health and disease and to support more personalized care. No named DT4H application case, company, DT4H project, or digital-twin updating, simulation, prediction, or feedback mechanism is documented [202]. |
| **Insigneo Institute for Healthcare Technology** — also reported in some sources as “Insigneo Institute for in silico Medicine”; provisional DT4H candidate [197][203][205] | University of Sheffield, Sheffield, United Kingdom; associated with Sheffield teaching hospitals and a wider academic, clinical, NHS, industry, and international research community [199][203][204]. | Computational modelling in medicine, healthcare data/AI, biomedical imaging, smart devices and sensors, in-silico medicine, and patient-specific predictive models. A 2023 paediatric programme explicitly included Digital Twins in real-life clinical-care settings [204][224]. | Improve health through interdisciplinary research, translation, clinical impact, NHS collaboration, industrial partnerships, and researcher training; develop digital platforms and digital-twin concepts for paediatric care. Substantive DT4H relevance is documented, but major-center status at the cutoff remains provisional [199][203][204]. |
| **Auckland Bioengineering Institute** — provisional physiological-twin candidate; major DT4H status not established [230] | University of Auckland, Auckland, New Zealand; serves biomedical-engineering, medtech, clinical, industrial, and international-collaboration communities. Its MedTech CoRE included partner nodes at the universities of Canterbury, AUT, Otago, and Victoria and at Callaghan Innovation [230]. | Applies mathematical and engineering sciences to biology, including physiome modelling, integrated-body modelling, cardiac physiome work, medical-device technology, and healthcare translation. The supplied evidence does not explicitly designate ABI itself as a digital-twin center [230]. | Bring physiome modelling into healthcare; develop the MedTech Innovation Quarter; boost New Zealand’s deep-tech sector through the Te Tītoki Mataora MedTech Research Translator; and strengthen the medical-device industry through the Consortium for Medical Device Technologies [230]. |
| **European VHT Initiative / “Virtual Human Twin ecosystem”** *(provisional initiative; exact formal name not established)* [122,133] | Europe; researchers, funded consortia, healthcare professionals, patients, and other VHT stakeholders [207] | Digital Twin in Healthcare and in-silico trials; distributed repository and simulation platform for quantitative human pathophysiology and patient-specific predictive models [207] | Facilitate development and validation, clinical decision support, personalized forecasting, resource reuse, and potentially reduced or replaced experimentation [207] |
| **Digital Twin Consortium** *(provisional general consortium; major DT4H status not established)* [129,295,296] | International industry, government, and academic community; a specific headquarters or health-specific community is not established in the cited evidence [231] | Cross-industry digital-twin vocabulary, architecture, security, interoperability, and adoption; Healthcare & Life Sciences is one working-group area, but a substantive health-research focus is not established [295,296] | Accelerate digital-twin innovation and market adoption; develop standards, roadmaps, research proposals, white papers, open-source projects, and best practices [129,296] |
| **The Living Heart Project / SIMULIA Living Heart** *(project, not confirmed center or consortium)* [211] | Dassault Systèmes–U.S. Food and Drug Administration cardiovascular and medical-device community; geographic base is not established [211] | A validated digital-twin model simulating human hearts and digitally examining organ–drug interactions, heart structure, and tissue mobility [211] | Support cardiovascular-device and pharmaceutical evaluation and future personalized treatment; the evidence does not establish major-center status [12,141] |
| **Virtual Physiological Human Institute** *(historically substantial; current major status unresolved)* [122,139,140] | Europe and an international VPH scientific and research community [122,140] | In-silico medicine; patient-specific computational models; modelling and simulation of human physiology and disease [122,140] | Coordinate academic, governmental, industrial, and societal stakeholders; share infrastructure through the VPH ToolKit; support integrative projects and clinical–industrial collaboration [210] |
| **All of Us Research Program** *(health-data program; not established as a major DT4H center)* [142,147] | United States; nationwide participant, researcher, and partner community, including more than 100 academic, provider, technology, and community partners in the 2018 backgrounder [214] | Precision-medicine and biomedical data infrastructure combining biosamples, physical measurements, EHRs, surveys, and wearable data; a specific digital-twin research focus is not documented [142,147] | Link, curate, and provide participant data through the Researcher Workbench; accelerate biomedical research, disease prevention and treatment, and health equity [142,143,147] |
| **An Ecosystem for Digital Twins in Healthcare (EDITH)** *(provisionally eligible consortium)* [213] | European 19-partner consortium led by VPHi, with non-European advisory participation including 12 Labours, SimVascular, and Stanford collaborators [213] | Distributed human-digital-twin infrastructure using model and data standards, SOPs, APIs, predictive models, and experimental and clinical data [213] | Operate a 24-month Coordination and Support Action, develop a shared facility for reuse and collaboration, and coordinate the European VHT roadmap [122,144] |
| **Auckland Bioengineering Institute (ABI)** *(biomedical-engineering candidate; major DT4H status not established)* [116,139] | Waipapa Taumata Rau, University of Auckland; the cited university-news source does not state a country or broader research community [206] | Mathematical lung models, applied computational physiology of the respiratory system, and modelling of normal and diseased human physiology [206] | Improve understanding of physiological processes and support diagnosis and treatment of injury or disease; explicit digital-twin-center status is not established [209] |
| **Precision Medicine Initiative Cohort Program** *(cohort/data program; not established as a major DT4H center)* [212] | United States voluntary national research-cohort and precision-medicine community [212] | Individual variability in genes, environment, and lifestyle; participant-data research for precision medicine, disease prevention, and treatment; no DT4H-specific focus is documented [212] | Build a cohort of 1 million or more volunteers, improve understanding of health and disease, enable open responsible data sharing, and support tailored prevention and treatment. The evidence identifies no DT4H case, company, project, technology, or twin mechanism [212] |
| European Virtual Human Twins (VHT) Initiative [241] | EU/VHT ecosystem [241] | Integrated human-body twins for health/care and personalised medicine [241] | Pool data/models/compute for research-to-clinical uptake; launched 21 Dec 2023; in-scope health initiative, major-center eligibility unresolved [220] |
| EDITH (European Digital Twin in Healthcare) Coordination and Support Action [238] | EU/VHT community [238] | Healthcare-twin roadmap: pathophysiology, federated infrastructure and credibility [238] | Pool resources, validate models and support uptake; atrial-fibrillation use case [73]; in-scope consortium candidate, major-center status unresolved [238] |

## References

[1] <https://orbi.uliege.be/bitstream/2268/313720/1/Position_Paper_From_the_Digital_Twins_in_Healthcare_to_the_Virtual_Human_Twin_A_Moon-Shot_Project_for_Digital_Health_Research.pdf> January 2024 position paper; January 2024 terminology and examples; Context-of-use discussion; Shared technical priorities; Virtual Human Twin blueprint; Janua…
[2] <https://doi.org/10.3390/pr11041213> BioDT study; BioDT experiment; BioDT framework; Sensing and parameter-updating methods; Model–shadow–twin comparison; Advanced-process-control experiment; BioD…
[3] <https://www.anylogic.com/resources/case-studies/hospital-digital-twin-to-improve-operations-and-enhance-patient-experience/> hospital case; Two-hospital case; Model-development status
[4] <https://www.accessdata.fda.gov/cdrh_docs/reviews/DEN130045.pdf> FDA HeartFlow review; FDA device description; HeartFlowNXT primary endpoints
[5] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9074288/> single-cell study; Li and colleagues’ study
[6] <https://www.mdpi.com/2673-7078/3/4/41> SI-joint study; Planning workflow; SI-joint results
[7] <https://www.unlearn.ai/blog/introducing-our-digital-twin-generators-for-hypertension-dyslipidemia-and-type-2-diabetes> Unlearn announcement; TwinRCT mechanism; Company regulatory statement
[8] <https://doi.org/10.48550/arxiv.2401.10029> cardiac preprint; Automated cardiac pipeline; Cardiac results; Personalized electrophysiology
[9] <https://www.frontiersin.org/journals/digital-health/articles/10.3389/fdgth.2024.1336050/full> Dataset and final analytic sample; Feature-set comparison; Knowledge-graph analysis
[10] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9418270/> 2022 cardiovascular digital-twin review; Aortic planning example
[11] <https://www.frontiersin.org/journals/chemical-engineering/articles/10.3389/fceng.2021.727152/full> Danish industry survey
[12] <https://www.cranfield.ac.uk/press/news-2024/cranfield-university-simul8-digital-shadow-and-digital-twin-trial> DASHclinic pilot
[13] <https://www.3ds.com/assets/invest/2024-02/dassault-systemes-virtual-twin-experience-saint-louis-hospital-ap-hp-pr-final-27-feb-2024.pdf> Dialysis-unit virtual twin
[14] <https://idsc.miami.edu/digital-twin/> Care-coordination architecture; MILBox population and collection plan; Miami program
[15] <https://www.medidata.com/wp-content/uploads/2024/02/simulia-medtronic-case-study.pdf> Medtronic design workflow; Bench comparison and reported efficiency
[16] <https://19ddfbc531122fe16eba-d0e8071b2c8ae292a1687ff17a4bdab8.ssl.cf1.rackcdn.com/PO_10_Haughton_Design_Limited_Dunkley.pdf> Clip modeling study
[17] <https://www.3ds.com/assets/invest/2022-05/lsh-innovating-to-improve-outcomes-in-heart-valve-replacement.pdf> FEops technology and status; 112-patient collaboration
[18] <https://www.3ds.com/fileadmin/Industries/life-sciences/pdf/NAFEMS-Benchmark-Technology-to-Save-Lives-LHP-07-01-15.PDF> Heart–device interaction example; Living Heart’s founding objectives
[19] <https://www.hfma.org.uk/system/files/2024-03/Delivering%20value%20digital%20case%20study%20-%20MedTech%20Heartflow%20v12.pdf> NHS pathway description; February 2024 implementation figures; NHS outcomes analysis
[20] <https://www.prnewswire.com/news-releases/first-study-using-biomimetic-ai-digital-twins-and-multiomics-in-genetics-research-302103336.html> 29 March announcement; Reported molecular findings
[21] <https://doi.org/10.1136/jitc-2023-sitc2023.0605> Computational-pathology study; Virtual Phase III results
[22] <https://www.frontiersin.org/journals/systems-biology/articles/10.3389/fsysb.2022.928387/full> Drug Development Digital Twin schema
[23] <https://www.drugdiscoverytrends.com/endometriosis-digital-twin-study-genetic-insights/> Architecture description
[24] <https://www.koerber.com/en/insights-and-events/intravacc-pas-x-savvy-digitalization> Intravacc implementation
[25] <https://www.wur.nl/en/chair-groups/bioprocess-engineering/research/biomanufacturing-and-digital-twins> Wageningen research program; Wageningen program scope
[26] <https://www.koerber.com/en/insights-and-events/bioprocessing-intelligence-to-accelerate-time-to-market> Company-reported results
[27] <https://research.kuleuven.be/portal/en/project/3M240130> hMSC manufacturing proposal
[28] <https://www.koerber.com/en/insights-and-events/bioprocess-digital-twin> Bioprocess-twin architecture
[29] <https://www.nature.com/articles/s41598-023-27998-2> Lentiviral-vector process study
[30] <https://www.mdpi.com/2072-6694/16/5/1047> CT-to-AR pipeline; Registration and clinical results; iKidney–IGNITE comparison
[31] <https://www.frontiersin.org/journals/surgery/articles/10.3389/fsurg.2024.1304039/full> Markerless-AR case
[32] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10927217/> Patient-specific biomodel
[33] <https://blogs.nvidia.com/blog/atlas-meditech-brain-surgery-ai-digital-twins/> Atlas rehearsal architecture
[34] <https://www.medidata.com/wp-content/uploads/2024/02/CaseStudy_InSilico-2.pdf> Virtual-population demonstration; Regulatory context; Global collaboration description
[35] <https://arxiv.org/abs/2403.00177> Echocardiographic-twin preprint
[36] <https://www.turing.ac.uk/research/research-projects/digital-twins-cardiovascular-system-remote-patients-monitoring> PAH monitoring architecture; Turing project objectives
[37] <https://www.digipredict.eu/community/> OPTOMICS objectives; Neurotwin objectives; DIGIPREDICT community structure
[38] <https://doi.org/10.4230/oasics.commit2data.2> EPI framework; EPI infrastructure objectives
[39] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11051158/> Personalized-diabetes demonstration
[40] <https://news.med.miami.edu/um-medical-researchers-accelerate-future-of-personalized-wellness-with-the-milbox/> MILBox sensor architecture
[41] <https://bmeiisinai.org/the_digitwin_study/> DigiTwin study design; Devices and eHive; Mount Sinai protocol
[42] <https://www.annualreviews.org/content/journals/10.1146/annurev-pharmtox-022123-022046> Health digital-twin translation challenges
[43] <https://www.edith-csa.eu/> EDITH objectives
[44] <https://www.digitaltwinconsortium.org/working-groups/healthcare/> Working-group focus
[45] <https://www.qmul.ac.uk/news/latest-news/2022/pr/new-group-to-advance-digital-twins-in-healthcare.html> EDITH’s formation and partners
[46] <https://newsroom.clevelandclinic.org/2023/02/21/nih-awards-researchers-3-14-million-grant-to-design-novel-model-aimed-at-reducing-healthcare-disparities> NIH-funded project announcement
[47] <https://dt.mdx.ac.uk/?page_id=1701> Partnership and duration; Specified project outputs
[48] <https://www.edith-csa.eu/partners/> EDITH institutional contributions
[49] <https://esc365.escardio.org/journal/80437>
[50] <https://vtechworks.lib.vt.edu/server/api/core/bitstreams/d261aeb8-489d-494f-a109-e08380588835/content>
[51] <https://www.embs.org/pulse/articles/one-patient-two-worlds-digital-twins-for-everyday-prevention-and-care/>
[52] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11705329/>
[53] <https://kclpure.kcl.ac.uk/portal/en/projects/cdt-dt4h-optimising-implanted-cardioverter-defibrillator-devices-/>
[54] <https://www.nature.com/articles/s41746-024-01146-0>
[55] <https://www.nature.com/articles/s41598-025-99608-2>
[56] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10056736/>
[57] <https://ruor.uottawa.ca/items/7665977e-7b33-4255-b571-068f3d00d623>
[58] <https://www.mdpi.com/2073-431X/13/9/228>
[59] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11344555/>
[60] <https://www.nature.com/articles/s41746-025-01447-y>
[61] <https://orbi.uliege.be/bitstream/2268/313720/1/Position_Paper_From_the_Digital_Twins_in_Healthcare_to_the_Virtual_Human_Twin_A_Moon-Shot_Project_for_Digital_Health_Research.pdf>
[62] <https://www.nature.com/articles/s41746-025-01738-4>
[63] <https://www.mdpi.com/2306-5354/11/6/606>
[64] <https://link.springer.com/article/10.1186/s40537-025-01280-w>
[65] <https://www.frontiersin.org/journals/digital-health/articles/10.3389/fdgth.2026.1827007/full>
[66] <https://www.nature.com/articles/s41746-025-01910-w>
[67] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11681439/>
[68] <https://doi.org/10.24406/publica-6186>
[69] <https://proceedings.spiedigitallibrary.org/journals/journal-of-medical-imaging/volume-11/issue-6/062603/Surgical-planning-in-virtual-reality-a-systematic-review/10.1117/1.JMI.11.6.062603.full>
[70] <https://scienceblog.cincinnatichildrens.org/cincinnati-childrens-gifted-2-7-million-for-virtual-reality-surgical-planning/>
[71] <https://life-and-health-uk.hannover-re.com/202406-changing-the-face-of-preventative-healthcare/?overlay=Health-metrics>
[72] <https://wellnesswise.co.uk/digital-twin-technology-has-the-potential-to-radically-disrupt-healthcare.html>
[73] <https://www.edith-csa.eu/2024/03/14/spot-on-a-use-case-cardiovascular/>
[74] <https://doi.org/10.22381/ajmr11120245>
[75] <https://www.kymanox.com/thought-leadership-series/blog/digital-twins-cdmo/>
[76] <https://www.ercot.com/files/docs/2024/04/30/ERCOT-Monthly-April-2024.pdf>
[77] <https://learn.microsoft.com/en-us/fabric/real-time-intelligence/architectures/hospital-operations>
[78] <https://www.cc.gatech.edu/news/georgia-tech-partners-childrens-hospital-new-heart-surgery-planning-tool>
[79] <https://www.frontiersin.org/journals/medicine/articles/10.3389/fmed.2024.1433372/pdf>
[80] <https://www.oecd.org/content/dam/oecd/en/publications/reports/2024/03/digital-tools-for-health-and-wellness-in-insurance_4af9a59e/d3764184-en.pdf>
[81] <https://patents.google.com/patent/US20190005200A1/en>
[82] <https://arxiv.org/html/2403.16736v2>
[83] <https://arxiv.org/pdf/2505.00670>
[84] <https://digital.ahrq.gov/sites/default/files/docs/page/SuccessStoryMold.pdf>
[85] <https://doi.org/10.1109/wsc63780.2024.10838898>
[86] <https://www.materialise.com/en/inspiration/articles/digital-twins-medical-device-design>
[87] <https://link.springer.com/article/10.1007/s00449-026-03369-9>
[88] <https://doi.org/10.1136/jitc-2023-sitc2023.0605>
[89] <https://pmc.ncbi.nlm.nih.gov/articles/PMC13424265/>
[90] <https://proceedings.aiche.org/conferences/aiche-annual-meeting/2024/proceeding/paper/372j-digital-integration-fermentation-and-centrifugation-processes-optimizing-pilot-plant>
[91] <https://doi.org/10.3390/pr11041213>
[92] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8110242/>
[93] <https://arxiv.org/html/2106.10684v1>
[94] <https://doi.org/10.18845/tm.v36i6.6750>
[95] <https://www.toobler.com/blog/digital-twin-medical-device>
[96] <https://incose.onlinelibrary.wiley.com/doi/10.1002/sys.70078>
[97] <https://journals.plos.org/ploscompbiol/article?id=10.1371%2Fjournal.pcbi.1012289>
[98] <https://www.synbiobeta.com/read/digital-twins-to-advance-biomanufacturing>
[99] <https://doi.org/10.18231/j.jchm.2024.011>
[100] <https://www.delveinsight.com/blog/digital-twin-technology-challenges-and-applications>
[101] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9428772/>
[102] <https://idsc.miami.edu/digital-twin/>
[103] <https://grants.nih.gov/funding/find-a-fit-for-your-research/highlighted-topics/129>
[104] <https://www.3ds.com/3dexperiencelab/portfolio/living-heart>
[105] <https://doi.org/10.1115/1.4002561>
[106] <https://mdic.org/wp-content/uploads/2024/04/CMS_Landscape_Report.pdf>
[107] <https://principia.es/en/living-heart-project-cardiovascular-science-through-realistic-simulation/>
[108] <https://insilico.com/casestudy>
[109] <https://doi.org/10.1016/j.procir.2024.08.022>
[110] <https://doi.org/10.3389/fddsv.2022.1019706>
[111] <https://www.annualreviews.org/content/journals/10.1146/annurev-pharmtox-022123-022046>
[112] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10608065/>
[113] <https://www.mdpi.com/2673-7426/4/2/79>
[114] <https://globalforum.diaglobal.org/issue/november-2024/virtual-patients-real-results-how-digital-twins-are-reshaping-drug-development/>
[115] <https://www.tandfonline.com/doi/full/10.1080/17460441.2023.2273839>
[116] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11368703/>
[117] <https://globalforum.diaglobal.org/issue/october-2024/in-silico-technologies-leading-the-future-of-drug-development-breakthroughs/>
[118] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11602770/>
[119] <https://doi.org/10.23919/annsim61499.2024.10732565>
[120] <https://air.unimi.it/bitstream/2434/711688/2/08981975.pdf>
[121] <https://doi.org/10.31235/osf.io/gkvqt>
[122] <https://www.wellstar.org/articles/redefining-healing-experiences-with-sound-at-south-by-southwest>
[123] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9410074/>
[124] <https://doi.org/10.1007/s10729-018-9453-7>
[125] <https://www.jmir.org/2024/1/e60258/>
[126] <https://digital.ahrq.gov/health-care-theme/care-coordination>
[127] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11650087/>
[128] <https://www3.weforum.org/docs/WEF_Transforming_Healthcare_2024.pdf>
[129] <https://www.ey.com/en_us/industries/health/care-coordination-infrastructure-to-support-health>
[130] <https://www.gehealthcare.com/content/dam/gehc/sitecore-migrated-assets/gehc/us/images/products/software/commandcenter/nsh-case-study-one-pager-extended-version-110923-v4-.pdf>
[131] <https://www.ifm.eng.cam.ac.uk/research/dial/current-research/digital-hospitals/>
[132] <https://www.canhealth.com/2023/07/05/providence-in-bc-deploys-enterprise-wide-care-coordination-centre/>
[133] <https://www.frontiersin.org/journals/digital-health/articles/10.3389/fdgth.2023.1253050/full>
[134] <https://www.frontiersin.org/journals/digital-health/articles/10.3389/fdgth.2025.1633539/full>
[135] <https://www.aidoc.com/learn/blog/ai-care-coordination-platform/>
[136] <https://carecoordinations.com/blog/top-7-care-coordination-technologies-revolutionizing-healthcare-in-2024>
[137] <https://www.einfochips.com/blog/digital-twin-top-use-cases-in-healthcare/>
[138] <https://aimultiple.com/digital-twin-applications>
[139] <https://www.tgh.org/about-tgh/care-coordination-center>
[140] <https://www.edith-csa.eu/wp-content/themes/edith/documents/EDITH-EM-Paris_Minutes.pdf>
[141] <https://www.scielo.br/j/ibju/a/QkVWtMwYTFc3nGbpkSjhsJz/abstract/?lang=en>
[142] <https://surgeonslab.com/precision-and-preparation-in-middle-cerebral-artery-aneurysm-surgery>
[143] <https://www.europeanurology.com/article/S0302-2838(23)03015-4/abstract>
[144] <https://www.prnewswire.com/news-releases/hipinsight-system-hits-3-000-total-hip-replacement-case-milestone-302060388.html>
[145] <https://doi.org/10.1117/1.jmi.11.6.062603>
[146] <https://www.custommarketinsights.com/report/healthcare-digital-twins-market/>
[147] <https://doi.org/10.7759/cureus.54205>
[148] <https://www.mdpi.com/1648-9144/60/2/339>
[149] <https://www.texaschildrens.org/content/research/dr-sameer-sheth-and-collaborators-develop-holographic-tool-facilitate-interactive>
[150] <https://doi.org/10.1136/bmjopen-2023-082875>
[151] <https://www.frontiersin.org/journals/surgery/articles/10.3389/fsurg.2024.1427844/full>
[152] <https://www.frontiersin.org/journals/surgery/articles/10.3389/fsurg.2022.821060/full>
[153] <https://www.cincinnatichildrens.org/professional/subspecialist-news/heart/increased-access-heart-care>
[154] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8658225/>
[155] <https://jamanetwork.com/journals/jamanetworkopen/fullarticle/2751395>
[156] <https://mdandersonhospiten.es/en/news/post/8396/md-anderson-madrid-hospiten-surgeons-will-use-3d-technology-to-plan-their-operations>
[157] <https://www.cell.com/patterns/fulltext/S2666-3899(24)00161-2>
[158] <https://doi.org/10.1097/scs.0000000000009794>
[159] <https://www.sermo.com/resources/digital-twins/>
[160] <https://doi.org/10.1038/s41746-025-01910-w>
[161] <https://ar5iv.labs.arxiv.org/html/2209.09023>
[162] <https://www.zs.com/insights/in-silico-trials-clinical-research>
[163] <https://royalsociety.org/blog/2017/12/the-virtual-physiological-human/>
[164] <https://www.medidata.com/wp-content/uploads/2024/02/CaseStudy_InSilico-2.pdf>
[165] <https://doi.org/10.1002/cpt.3192>
[166] <https://osma.net/wp-content/uploads/2024/07/6_Marc-Horner_OSMAFall2024-MarcHorner-Ansys_FINAL.pdf>
[167] <https://doi.org/10.1016/j.drudis.2023.103605>
[168] <https://doi.org/10.3389/fsysb.2022.928387>
[169] <https://www.frontiersin.org/journals/systems-biology/articles/10.3389/fsysb.2022.928387/full>
[170] <https://www.strategicmarketresearch.com/market-report/in-silico-clinical-trials-market>
[171] <https://doi.org/10.1109/jbhi.2024.3486538>
[172] <https://www.jmir.org/2024/1/e58504/>
[173] <https://www.jmir.org/2024/1/e50204/>
[174] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10286106/>
[175] <https://iris.uniroma1.it/handle/11573/1390455>
[176] <https://ar5iv.labs.arxiv.org/html/2106.10684>
[177] <https://www.datamintelligence.com/research-report/in-silico-clinical-trials-market>
[178] <https://blog.3ds.com/industries/life-sciences-healthcare/in-silico-clinical-trials-new-age-of-medical-innovation/>
[179] <https://gnqin.com/gnq-insilico-announces-collaboration-with-fortune-100-company-to-develop-next-generation-clinical-trial-platform/>
[180] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8401029/>
[181] <https://doi.org/10.1109/tce.2024.3367929>
[182] <https://www.who.int/docs/default-source/documents/gs4dhdaa2a9f352b0445bafbc79ca799dce4d.pdf>
[183] <https://doi.org/10.1007/978-981-97-5035-1_49>
[184] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5568837/>
[185] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11536218/>
[186] <https://www.nih.gov/allofus>
[187] <https://techcrunch.com/2024/01/18/six-rules-to-get-the-most-out-of-fitness-wellness-tracking/>
[188] <https://doi.org/10.2196/49208>
[189] <https://kindredhomecare.com/kindred-home-care-advances-digital-health-solution-for-senior-care-with-wellness-check-initiative/>
[190] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11420130/>
[191] <https://www.coherentmarketinsights.com/industry-reports/digital-human-twins-market>
[192] <https://doi.org/10.1038/s44287-024-00025-w>
[193] <https://www.intechopen.com/chapters/89360>
[194] <https://www.linkedin.com/pulse/wellness-digital-twin-bringing-our-2025-vision-life-through-grecu-p2xhc>
[195] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10916727/>
[196] <https://www.tetitokimataora.org.nz/post/european-funding-for-new-zealand-virtual-twins>
[197] <https://www.sheffield.ac.uk/insigneo>
[198] <https://www.sheffield.ac.uk/insigneo/research/our-research>
[199] <https://www.sheffield.ac.uk/insigneo/overview/about>
[200] <https://www.rdworldonline.com/how-the-living-heart-project-could-transform-fdas-approach-to-medical-device-testing/>
[201] <https://zenodo.org/communities/vph-institute/about>
[202] <https://www.nih.gov/allofus/about/protocol>
[203] <https://sheffield.ac.uk/insigneo/news/professor-jim-wild-appointed-executive-director-insigneo-institute>
[204] <https://www.sheffield.ac.uk/insigneo/news/phd-programme-digital-health>
[205] <https://sheffield.ac.uk/insigneo/research>
[206] <https://www.auckland.ac.nz/en/news/2023/08/17/new-director-appointed-at-abi.html>
[207] <https://doi.org/10.1109/jbhi.2023.3323688>
[208] <https://cordis.europa.eu/programme/id/HORIZON_HORIZON-HLTH-2027-03-TOOL-04>
[209] <https://www.vph-institute.org/news/the-vph-institute-board-of-directors-for-the-upcoming-year-2012-13-has-been-announced.html>
[210] <https://www.digitalhealthnews.eu/research/2014-european-institutededicated-to-the-virtual-physiological-human>
[211] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9330225/>
[212] <https://oig.hhs.gov/documents/audit/11266/A-18-24-06111.pdf>
[213] <https://www.rd-alliance.org/wp-content/uploads/2024/05/Health20Data20IG_The20usage20of20digital20twins20in20healthcare20for20personalised20care_RDA20VP19_20th20June202022.pdf>
[214] <https://www.nih.gov/news-events/all-us-research-program-backgrounder>
[215] <https://digital-strategy.ec.europa.eu/en/faqs/european-virtual-human-twins-initiative-qa>
[216] <https://research.tudelft.nl/en/publications/dassault-syst%C3%A8mes-living-heart-project/>
[217] <https://www.techcircle.in/2024/02/08/dassault-s-playbook-for-building-digital-twins-of-human-organs>
[218] <https://www.edith-csa.eu/>
[219] <https://www.bsc.es/research-and-development/projects/edith-ecosystem-digital-twins-healthcare>
[220] <https://digital-strategy.ec.europa.eu/en/library/european-virtual-human-twins-initiative>
[221] <https://www.digitaltwinconsortium.org/dtcmembersearch/>
[222] <https://vph-society.org/what-we-do/vph-conference/>
[223] <https://allofus.nih.gov/sites/default/files/AoU-Pioneering_Precision.pdf>
[224] <https://sheffield.ac.uk/insigneo/clinicians/overview>
[225] <https://www.mbie.govt.nz/science-and-technology/science-and-innovation/news-success-stories/success-stories/digital-twins-in-healthcare>
[226] <https://doi.org/10.1109/embc40787.2023.10341138>
[227] <https://pmc.ncbi.nlm.nih.gov/articles/PMC4175454/>
[228] <https://www.digitaltwinconsortium.org/press-room/01-31-24/>
[229] <https://www.vph-institute.org/history.html>
[230] <https://www.auckland.ac.nz/en/abi/about-the-institute/our-institute/milestones.html>
[231] <https://www.digitaltwinconsortium.org/press-room/10-27-21/>
[232] <https://www.edith-csa.eu/wp-content/uploads/2023/04/EDITH_D3.1_vision_roadmap_outline_final.pdf>
[233] <https://www.digitaltwinconsortium.org/membership/membership-levels/>
[234] <https://www.3ds.com/industries/life-sciences-healthcare/living-heart-project/project-members>
[235] <https://www.nature.com/articles/s41586-023-06957-x>
[236] <https://www.snsinsider.com/reports/in-silico-clinical-trials-market-6369>
[237] <https://allofus.nih.gov/sfsites/c/resource/pmi_working_group_report_20150917_2_pdf>
[238] <https://doi.org/10.5281/zenodo.8070380>
[239] <https://www.genomeweb.com/informatics/qa-all-us-data-center-ramps-lofty-goals-technical-challenges>
[240] <https://www.edith-csa.eu/2024/02/20/first-ecosystem-meeting-to-build-the-vht-beyond-the-fulfilment-of-ediths-mission-the-first-ecosystem-meeting-on-building-the-vht-a-productive-two-day-event-took-place-at-the-institut-polytechniq/>
[241] <https://www.vph-institute.org/news/european-virtual-human-twins-initiative-official-launch-in-barcelona.html>
[242] <https://digital-strategy.ec.europa.eu/en/events/european-virtual-human-twins-vht-initiative-accelerating-innovation-and-making-personalised>
[243] <https://www.youtube.com/watch?v=2wPz4ozVxxI>
[244] <https://dice.cyfronet.pl/edith/MB-KUKDM-March-2024-v01.pdf>
[245] <https://www.digitaltwinconsortium.org/industries/healthcare/>
[246] <https://www.rwth-aachen.de/cms/root/forschung/projekte/eu-projekte/eu-projekte-in-horizon-europe/~bicutr/edith/?lidx=1>
[247] <https://www.engineeringnz.org/news-insights/international-acclaim-for-bioengineering/>
[248] <https://grants.nih.gov/grants/guide/rfa-files/RFA-PM-16-001.html>
