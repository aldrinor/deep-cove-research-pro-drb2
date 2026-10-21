# AI-Supported Shared Decision-Making in Healthcare: Transparency, Explainability, Reasoning, and Patient Choice

**The concepts serve different purposes.** AI transparency concerns what people are told about an AI system, its development, performance, intended use, and limitations. AI explainability—usually called explainable AI, or XAI—helps people understand a model’s behavior or a particular output. AI reasoning concerns the computational or logical process leading to a conclusion; a convincing written rationale does not, by itself, demonstrate that the process was sound or faithfully described. The FDA, Health Canada, and MHRA explicitly place model logic and explainability within the broader concept of transparency. [1]

**AI-SDM supports a human partnership.** AI-supported shared decision-making means using AI to help patients and clinicians understand options, consider individualized evidence, articulate preferences, and deliberate together. Predictive AI can supply risk or outcome estimates; generative AI can support questions, explanations, and summaries. The intended result is an informed, jointly considered care plan—not an autonomous AI decision. [2]

| Concept | Focus | Goals | Primary audience | Core questions answered | Specific output examples |
|---|---|---|---|---|---|
| AI Transparency [1] | Whole system, lifecycle, and use context | Enable appropriate use, accountability, and oversight | Patients, care teams, developers, institutions, regulators | What is it for? How was it developed and tested? Where might it fail? | Intended-use documentation; data provenance; validation report; bias and failure warnings |
| AI Explainability — XAI [3] | Model behavior or a particular prediction | Support understanding, inspection, and challenge | Clinicians and technical users; patients receiving tailored explanations | Why this prediction? Which inputs mattered? What would change it? | SHAP contributions; LIME explanation; image heatmap; counterfactual; similar-case comparison |
| AI Reasoning — working definition [4] | Computational or logical path toward a conclusion | Draw conclusions; examine the inference process | Developers, researchers, clinicians, expert reviewers | What rules, computations, or intermediate steps led here? Are they sound? | Rule trace; decision-tree path; model-logic account; generated intermediate-step narrative |

**The report follows three questions.** First, what information does each terminology category actually provide? Second, how can different AI functions support a preference-sensitive healthcare conversation? Third, how does AI-SDM differ from traditional shared decision-making and XAI alone? The sections below develop those distinctions, explain an operational workflow, and assess concrete examples and their practical implications.

## 1. Understanding transparency, explainability, and reasoning

### AI transparency: understanding the system and its use

**Transparency extends beyond individual predictions.** The 2024 FDA–Health Canada–MHRA principles define transparency through communication of appropriate information about a machine-learning-enabled medical device, including intended use, development, performance, and, when available, logic. This includes information needed before adoption, during clinical use, and after updates or changes in performance. [1]

**Its central concern is appropriate reliance.** A clinician needs to know whether a tool was designed for screening, diagnosis, prognosis, or treatment support; which patients it addresses; and how its output should influence clinical judgment. A patient may instead need a clear account of why AI is involved, who reviews its contribution, and whom to approach with questions. Both are transparency needs, although they require different information and presentation.

**Documentation is only one mechanism.** Kiseleva, Kotzinos, and De Hert’s 2022 analysis treats transparency as an umbrella concept spanning AI development and use. It identifies explainability, communication, auditability, traceability, record-keeping, data governance, and documentation as complementary ways to achieve it. Publishing an explanation of one prediction therefore addresses only part of the broader responsibility. [5]

**A concrete output is a label.** The 2024 AMIA/Beth Israel Deaconess Medical Center working group proposed a Unique AI Identifier, or UAII: a transparency label resembling a medical-product or nutrition label. Its proposed fields include intended use, training-data provenance, potential biases, version information, validation, conflicts of interest, limitations, warnings, and recommended user training. This is a governance proposal, not a claim that every healthcare AI product already carries such a label. [6]

**Meaning matters alongside technical disclosure.** Transparency also requires clarity about what a prediction represents. A 2022 clinical explainability analysis cites a review finding 44 different definitions of acute kidney injury across algorithm-based prediction models. It notes that models invoking the same clinical standard could nevertheless operationalize it differently, including omission of urinary-output criteria. A comprehensible explanation of an ambiguously defined outcome would still leave clinicians uncertain about what condition the model was predicting. [7]

**More disclosure is not automatically useful.** A long technical document can contain accurate information yet fail to help someone at the point of care. The joint regulators’ principles emphasize the right audience, medium, timing, and level of detail. A concise warning during a high-risk workflow step may be more useful than another page in a technical manual; detailed validation information may be more useful during procurement or specialist review. [1]

**Transparency should therefore be actionable.** For a healthcare reader, the practical test is whether the disclosed information helps answer: “Is this system appropriate for this patient and this decision, and what should we do when its assumptions do not fit?” Transparency supports that assessment, but the disclosure itself is not proof that the system is accurate, equitable, or clinically beneficial.

### AI explainability: understanding model behavior or an output

**XAI addresses a narrower question.** Explainable AI provides information that helps users understand how a model behaves or why it produced a particular result. In healthcare, its usefulness depends on the task and the recipient: an oncologist checking a recurrence prediction, a developer investigating an error, and a patient considering treatment do not necessarily need the same explanation. [3]

**Explanations have different scopes.** A global explanation describes the model generally—for example, its overall dependence on particular variables. A local explanation concerns one prediction, such as which recorded characteristics contributed most to a particular patient’s estimated risk. Local explanations can be patient-specific without addressing that patient’s goals or preferred trade-offs. [3]

**Interpretability can be built in.** An intrinsically interpretable, or ante-hoc, model is structured so that people can directly inspect how it operates. Examples include suitably simple decision trees and rule-based systems. A post-hoc explanation is added after a model has been trained, often to help interpret a complex model whose internal operation is difficult to understand directly. [4]

**Feature contributions are common outputs.** SHAP—Shapley Additive Explanations—assigns contributions to input features relative to a defined reference. LIME—Local Interpretable Model-agnostic Explanations—uses a simpler local approximation to describe behavior around an input. In a clinical interface, either might support a display showing which recorded variables pushed a prediction upward or downward. [8]

**Image explanations highlight influential regions.** Saliency maps and related visualization methods mark image regions associated with a model’s output. In the UK Information Commissioner’s Office’s illustrative cancer-diagnosis workflow, supplementary salience and class-activation maps highlight abnormal regions on radiologic images. Radiologists then combine those outputs with other evidence, and the clinical team translates the findings for the patient. [9]

**Counterfactuals ask what would change.** A counterfactual explanation identifies changes to inputs that would alter a model’s prediction. A similar-case explanation instead presents relevant examples from previous patients or cases. These formats can make a prediction easier to discuss, especially when a list of feature weights would be difficult to interpret. [10]

**Prediction changes are not treatment effects.** If changing an input changes a prediction, that does not establish that a real-world intervention on that input will produce the corresponding clinical benefit. Statistical associations can reflect confounding, selection effects, or spurious relationships. A 2023 healthcare XAI analysis therefore stresses that clinicians still need clinical inference to distinguish model associations from causal reasons. [3]

**A plausible explanation may be approximate.** Post-hoc methods can simplify a model in ways that are useful for a specific purpose, but their faithfulness must be assessed. An explanation that sounds medically reasonable may describe only part of the model’s behavior—or may encourage a reader to fill in a causal story that the model never represented. Comprehensibility and fidelity are different properties. [11]

**Uncertainty deserves separate attention.** A prediction interval, confidence display, or other uncertainty information can help someone judge a recommendation without explaining why the model produced it. Conversely, an explanation can identify influential features without communicating how uncertain the prediction is. A well-designed clinical interface may need both, rather than treating either as a substitute for the other. [12]

**The audience determines explanatory adequacy.** The 2022 “Explanatory Pragmatism” framework argues that explainability is relative to an audience and a contextual purpose. A technical explanation sufficient for model debugging might be unsuitable for a treatment conversation. A short patient-facing explanation may appropriately omit technical detail while still explaining the information needed for that patient’s decision. [13]

### AI reasoning: the process rather than its presentation

**Reasoning concerns how conclusions arise.** Here, “AI reasoning” means the computational or logical process connecting available information to a conclusion. It can involve explicit rules, learned associations, probabilistic calculations, or attempts at multistep problem-solving. The term is useful descriptively, but it should not be read as a standardized healthcare governance category with boundaries equivalent to the regulators’ definition of transparency.

**Reasoning and explanation can intersect.** Combi and colleagues distinguish explanations of a system’s reasoning mechanism—the path it followed—from explanations describing relationships between data and results without exposing that path. This explains why a feature-attribution chart can be informative without revealing a complete reasoning process. It also explains why “why?” and “how?” overlap in ordinary discussion rather than dividing cleanly into separate technical boxes. [4]

**Different systems expose different traces.** A rule-based system may record which explicit rules fired. A decision tree may expose the branches used to reach a result. A complex learned model may instead require supplementary analysis to investigate its behavior. These are different forms of access to a decision basis, not interchangeable guarantees of understanding.

**Generated reasoning is still generated content.** A language model can produce sequential intermediate-step text, often called a chain-of-thought-style response. WHO’s 2024 guidance lists responses accompanied by such reasoning as a possible educational output, while also identifying errors, false information, and automation bias as risks. The existence of a structured narrative does not establish that every step is correct or that the narrative faithfully exposes the system’s underlying computation. [14]

**Clinical reasoning adds patient context.** Human clinical judgment involves interpreting history, examination, investigations, competing explanations, and information that may not be represented in the model. For treatment decisions, it also involves reasoning about what ought to be done for this particular person. That requires patient values and circumstances as well as scientific evidence. [11]

**The distinction avoids two extremes.** It would be misleading to equate fluent AI text with human clinical understanding. It would also be unhelpful to assume that every computational conclusion must be useless unless it resembles a clinician’s thought process. The practical questions concern performance, relevance, faithful representation, and the way the output is incorporated into care.

### Why clinical justification is a further question

**An explained prediction is not a justified choice.** A model might explain which inputs contributed to an estimated treatment benefit, yet still leave open whether that benefit is worth the burdens for the patient. Muralidharan, Savulescu, and Schaefer’s 2024 paper distinguishes algorithmic transparency from patient-directed justification: the latter concerns why a decision is appropriate in light of the patient’s values, priorities, and situation. [15]

**The cancer example makes this concrete.** In the ICO’s illustrative workflow, transparency includes information about data, responsibility, safety, and performance; XAI adds image-based information supporting interpretation; clinicians critically assess the result. None of those steps alone decides which treatment the patient should choose after diagnosis. That further decision requires discussion of reasonable options and their consequences for the patient’s life. [9]

**Shared deliberation supplies the missing relationship.** Shared decision-making, or SDM, is not another visualization method. It is a collaborative process in which clinical evidence and expertise meet the patient’s goals, values, preferences, and circumstances. AHRQ explicitly describes patients as leading decisions about their healthcare, supported by the care team’s evidence and experience. [16]

**The practical distinction is therefore functional.** Transparency supports assessment of the system, XAI supports inspection of its behavior, reasoning concerns inference, and SDM determines how evidence contributes to a person’s healthcare choice.

## 2. What AI-supported shared decision-making means

### Definition, objective, and intellectual foundations

**AI-SDM is SDM augmented by AI.** A useful working definition is: an AI-supported patient–clinician process that supplies understandable and individualized information, helps elicit preferences, organizes relevant evidence, and supports a jointly considered decision while preserving human judgment and patient autonomy. This definition combines established SDM principles with independently published work on AI-enabled decision aids, patient-centered clinical decision support, and interactive prototypes. [16][17]

**Its objective is value-aligned care.** The central aim is to connect the best relevant evidence and individualized estimates with what the patient wants to achieve and what the clinician considers medically reasonable. A recommendation that maximizes one modeled outcome is not necessarily the best choice for someone who values another outcome more highly. AI-SDM should make such differences discussable rather than conceal them inside a ranking.

**The human relationship remains central.** Patients contribute lived experience, priorities, practical constraints, and judgments about acceptable trade-offs. Clinicians contribute diagnostic interpretation, treatment knowledge, professional recommendations, and responsibility for clinical care. Family members and caregivers can participate where appropriate, but their involvement should support rather than erase the patient’s voice. [16]

**Several permitted sources inform the concept.** Roche Pharma AG’s patient-centered white paper describes AI-supported preparation for consultations, understandable medical information, structured summaries for doctors, and individualized consideration of research and personal preferences. Its development involved qualitative input and design thinking, including a Patient Council founded in 2023 with seven experienced patient representatives. Its contribution is a patient-informed design perspective. [18]

**Prototype research adds operational detail.** Hao, Liu, Riter, and Kalantari’s 2024 CHI paper, *Advancing Patient-Centered Shared Decision-Making with AI Systems for Older Adult Cancer Patients*, describes an i-SDM prototype. It presents treatment comparisons, risks and benefits, and progressively detailed information within a workflow involving clinician framing, patient learning and preference expression, and joint decision-making. [19]

**Related work uses similar terminology.** Another research contribution is titled *The i-SDM Framework: Developing AI-based Tools in Shared Decision-Making for Cancer Treatment with Clinical Professionals*. Its title and DOI identify a cancer-treatment and professional-design context. These related labels should be interpreted according to each contribution’s stated setting, rather than assumed to denote one universal clinical architecture. [20]

**Implementation research broadens the picture.** Giguère and colleagues’ 2024 preliminary environmental scan involved 22 participants across seven countries. Stakeholders identified personalized information and decision aids as potential implementation levers, alongside AI-supported assessment of real or simulated consultations for SDM training. This places some AI applications around the clinical conversation rather than inside the treatment recommendation itself. [21]

**The defining feature is deliberation.** An AI risk calculator used only by a clinician can be clinical decision support without being AI-SDM. A chatbot that explains a disease can provide education without supporting a shared decision. The AI-SDM designation becomes meaningful when the tool’s contribution enters an actual exchange about options, preferences, and an informed care plan.

### Functional components and what each contributes

**The components connect evidence with people.** The following component pattern synthesizes the documented functions of AI-supported decision aids and patient-centered clinical decision support with established SDM practice. It describes contributions to a decision, rather than prescribing a particular number of models or a fixed software implementation. [2][19]

| Component | Main inputs | Contribution or output | Human role |
|---|---|---|---|
| Patient and clinical context | History, condition, investigations, patient-reported information | Decision-relevant patient profile | Patient and clinician check accuracy and relevance |
| Predictive or analytical support | Clinical variables and an appropriate model | Risk, prognosis, classification, or outcome estimate | Clinician assesses applicability and interpretation |
| Generative or conversational support | Questions, evidence, clinical context | Explanations, summaries, clarifications, decision-aid content | Users review and correct generated material |
| Preference and value elicitation | Patient goals, concerns, acceptable trade-offs | Explicit, revisable preference summary | Patient confirms what matters |
| Clinical appraisal | AI outputs, evidence, expertise, contextual information | Reviewed options and professional recommendations | Clinician challenges, contextualizes, or overrides AI |
| Patient–clinician deliberation | Options, consequences, uncertainty, preferences | Informed preference or shared decision | Patient and clinician compare and discuss |
| Documentation and follow-up | Decision, reasons, outstanding questions | Agreed, deferred, or revisable care plan | Care team records and revisits the plan |

**These components need not be separate products.** A single application may collect patient information, generate a summary, and display a decision aid. Alternatively, an electronic health record may connect a predictive model with a separate patient portal and a clinician-facing interface. What matters is whether the information survives the handoffs accurately and reaches the people making the decision.

**Human contributions are not model modules.** Preference elicitation, clinical appraisal, and deliberation should not be understood merely as additional algorithmic tasks. AI can help organize them, but patients must be able to correct representations of their values, and clinicians must be able to disagree with the model. A completed preference field is useful only if it meaningfully informs the conversation.

**The output is more than information.** A personalized explanation or option table is an intermediate product. NICE’s SDM guideline identifies the final task as making a joint treatment or care decision or plan, agreeing when to review it, and recording what the person said mattered to them. AI-generated content becomes useful insofar as it supports that outcome. [22]

### Predictive AI: estimating risks and outcomes

**Predictive AI supplies patient-specific estimates.** AHRQ describes predictive AI as including machine learning, statistical modeling, and data-mining techniques used for predictive analytics. In an SDM setting, its contribution can be an estimate of disease risk, prognosis, complications, or other outcomes relevant to comparing care options. [2]

**A useful estimate needs clinical meaning.** Readers need to know the outcome being predicted, the relevant patient population, and the time horizon. “Risk of an event” is incomplete without those details. A model developed for one setting may also require careful assessment before its estimate is applied to another setting or patient group. [6]

**Individualization can improve the conversation.** Instead of discussing only an average result from a broad population, a decision aid can use the patient’s characteristics to make evidence more personally relevant. The 2024 *npj Digital Medicine* review defined AI-enabled decision aids as machine-learning-based tools that use individualized information, including preferences, medical history, and current clinical conditions, to generate tailored recommendations. [17]

**Prediction does not settle the decision.** A lower predicted complication risk may favor one option clinically, while recovery demands, treatment burden, or another outcome may matter more to the patient. The clinician and patient must also consider whether the model captures those consequences. A numerical advantage on the model’s chosen target should not silently become the definition of the “best” treatment.

**Recommendations contain additional value assumptions.** Predicting an outcome and recommending an action are different tasks. To rank actions, a system must in some way prioritize outcomes, burdens, or constraints. Those priorities may be explicit in a decision model or implicit in its design, but they should remain open to discussion when the choice is preference-sensitive. [11]

**What-if tools require careful interpretation.** Some explainable decision-aid proposals allow users to explore simulated treatment or lifestyle changes. This can help patients notice that alternatives exist and articulate priorities. Its clinical meaning depends on the underlying evidence: a model-based change in predicted risk should not automatically be presented as an established causal treatment effect. [23]

### Generative AI: supporting understanding and communication

**Generative AI creates communicative material.** Generative models produce new text, images, or other data. Large language models, or LLMs, are one important example: they can answer questions, summarize information, translate technical material into plain language, and support conversational interaction. These functions differ from estimating a clinically validated probability. [2]

**Preparation is an important use case.** Before a consultation, conversational support can help patients identify questions, understand unfamiliar terms, and describe their priorities. Roche’s white paper emphasizes understandable information and focused preparation so that the consultation can address the patient’s actual concerns. The AI’s contribution is to support participation, not to pre-empt the discussion. [18]

**Summaries can support both parties.** Patients may benefit from a concise account of the options and their own questions. Clinicians may benefit from a structured summary of symptoms, concerns, preferences, and unresolved issues. AHRQ’s PAIGE prototype illustrates this approach by asking clarifying questions and producing a patient-reviewed summary that can be sent to the clinician. [2]

**Language fluency is not numerical validation.** An LLM can explain a supplied risk estimate without being the model that generated it. It can also produce an authoritative-sounding answer that omits clinical context or contains incorrect information. AHRQ therefore emphasizes human review to catch confabulations—plausible but false or misleading generated content—and assess clinical relevance. [2]

**Predictive and generative functions can cooperate.** In a possible implementation, a validated predictive model could supply an estimate, an explanation method could identify relevant model behavior, and a generative interface could translate approved information into accessible language. That is a design option, not evidence that a single model performs every function equally well. The accuracy of the risk estimate, faithfulness of the explanation, and correctness of the generated wording remain distinct questions.

**Both model types are not mandatory.** AHRQ explicitly describes either predictive or generative AI as potentially contributing to patient-centered clinical decision support. An AI-SDM application may therefore emphasize outcome prediction, communication, or a combination. Its claim to support SDM rests on how it helps people make a decision together, not on including every fashionable model category.

### Other functions and suitable healthcare contexts

**Additional functions can contribute selectively.** Diagnostic classification, imaging analysis, triage, evidence synthesis, and patient-data summarization can supply information relevant to a shared decision. The AMA’s 2026 report describes clinical decision support moving beyond rule-based alerts toward real-time evidence synthesis and LLM assistance while preserving human judgment. These are possible supporting functions, not required modules of every AI-SDM application. [24]

**Preference-sensitive decisions are especially relevant.** These are decisions in which medically reasonable options involve trade-offs that different patients may value differently. Documented contexts include cancer treatment, knee osteoarthritis, severe aortic stenosis, multiple sclerosis treatment, stroke-related decisions, chronic-condition management, and breast reconstruction. The common feature is not a specialty but the importance of connecting outcomes with individual priorities. [25][17]

**Preferences must remain explicit and revisable.** AI can help extract statements from a patient’s narrative, but population-level patterns are not equivalent to that person’s informed preference. Yang and colleagues’ 2025 review of 67 studies found extensive work on measuring and predicting preferences, while relatively little focused on helping patients understand and reflect on their own preferences. This distinction is central to patient empowerment. [26]

**The central objective remains unchanged.** AI-SDM is valuable when its analytical and communication functions strengthen the connection between evidence, patient priorities, and clinical judgment—not when they replace that connection with an automated answer.

**Additional documented evidence**

AI-Supported Shared Decision-Making (AI-SDM) should be treated as a healthcare decision-support framework, not as a single model type. The allowed evidence cited here supports several AI functions and broader human-centred decision-support initiatives, but it does not establish a complete patient–clinician specification, exhaustive component roster, or clinical validation for the exact AI-SDM label requested. Accordingly, supported functions, broader analogies, and unresolved candidates are kept distinct.

**Objective and healthcare boundary**

The acronym **AI-SDM** is ambiguous. A Harvard report dated **May 4, 2023** describes the NSF AI Institute for *Societal* Decision Making as a planned **five-year, $20 million** initiative intended to improve decision-making in public health, disaster management, and other societal settings; a related institute page reports a **June 1, 2023** launch and NSF award **2229881**. These sources concern societal decision-making, not a defined patient–clinician shared-decision framework. [48] [53]

The broader initiative’s stated objective is to combine AI and social-science research to understand human decisions, improve AI-supported decisions, account for factors such as bias, risk, trust, equity, and ethics, and produce better and more trusted choices. [48] [53] Its healthcare-relevant work is primarily at the public-health and organizational level: collaboration with public-health departments, hospitals, health clinics, and emergency-management organizations; equitable allocation of health workers, vaccines, tests, treatment options, and emergency aid; and timely messaging about infectious-disease control or maternal health. [48]

Those examples clarify the decision-support logic but should not be mistaken for evidence of individual patient-level personalization. They involve public-health officials and emergency managers making resource or intervention decisions during health crises, rather than a documented consultation between one patient and one clinician. [48] A related description presents human–AI alignment as a dynamic process in which AI is aligned with human goals while people understand, audit, and collaborate with AI; it does not specify patient roles, clinician accountability, or delegated authority in a clinical encounter. [53]

For the healthcare request, a defensible working objective is therefore: **use appropriately governed AI outputs to improve the information, options, uncertainty communication, and deliberation available to patients and clinicians while retaining human decision responsibility**. This is a scope definition for interpreting the requested framework, not a claim that every element has been implemented or clinically validated.

**An ordered AI-SDM process**


1. **Define the decision context.** Identify the clinical or public-health problem, relevant population, available evidence, constraints, uncertainty, and affected people. The broader AI-SDM initiative specifically targets dynamic environments involving incomplete information, competing objectives, imperfect communication, and pressure. [48]

2. **Collect and qualify inputs.** Depending on the function, inputs may include clinical records, wearable-sensor data, medical images, vital signs, laboratory results, genomic data, clinical history, behavioural data, or public-health and demographic information. The input definition matters: predictive results depend on what population, outcome, and time horizon have been specified. [56] [55]

3. **Apply the appropriate AI function.** A predictive model may estimate risk or a future event; a generative system may be considered for communication or synthesis; other candidates may model human decisions, compare scenarios, retrieve evidence, recommend options, or support reasoning. The available evidence does not justify treating all of these labels as confirmed AI-SDM components. [48] [53] [56]

4. **Return a contextualized output.** Documented outputs include risk estimates, forecasts, classifications, alerts, counterfactual or causal analyses, resource-allocation tools, messages, maps, and reports. A disaster-response example combines mobility data, open-source AI models, Census demographics, and USGS seismic data to produce near-real-time, expert-validated tools for evacuation tracking, displacement mapping, and vulnerability analysis; the outputs include downloadable PDF reports and interactive maps. This is an analogue from disaster management, not a patient-facing AI-SDM artifact. [53]

5. **Enable human interpretation and deliberation.** Decision-makers review the output, consider its uncertainty and relevance, compare alternatives, and integrate it with human goals and expertise. The predictive-healthcare literature emphasizes clinician feedback and clinician-in-the-loop design; the broader AI-SDM material emphasizes that people should understand, audit, and collaborate with AI. [53] [56]

6. **Act, monitor, and evaluate.** The broader initiative describes field deployment alongside public-health experts, surveys, virtual exercises, pilot deployments, and technical exchanges. These activities indicate an evaluation and implementation pathway, but they do not establish a validated patient–clinician AI-SDM workflow. [48]

The exact patient-facing and clinician-facing output formats, handoffs, feedback loops, and authority transitions for the requested healthcare framework remain unspecified in the evidence cited here. The clearest supported boundary is that AI supplies decision support, while human users interpret the output and retain responsibility for action.

**Candidate functionality roster**

The AI-SDM functionality roster should remain open rather than being presented as an exhaustive list.

- **Predictive AI — supported healthcare functionality, but not independently confirmed here as a formal AI-SDM component.** It produces estimates, classifications, risk scores, forecasts, or alerts that may inform clinical or public-health decisions. [54] [56]
- **Generative AI — candidate functionality only in the evidence cited here.** The institute page describes generative AI as one part of a wider AI landscape and notes that chatbots are only a small part of AI; it contrasts generative AI with computer vision and physical AI. It does not provide a formal healthcare definition or establish generative AI as a component of the requested AI-SDM framework. [53]
- **Additional functionality candidates — unresolved membership.** Allowed sources describe computational models of human decision-making, group and hybrid human–AI decision-making, autonomous decision tools, counterfactual and causal simulation, communication tools, computer vision, and physical AI. These are documented areas of research or application, not a verified roster for a healthcare AI-SDM framework. [48] [53]
- **Evidence retrieval or recommendation — unresolved.** The cited sources describe scenario modelling, causal reasoning, communication, and decision-support tools, but they do not establish an evidence-retrieval or recommendation module as a component of the requested AI-SDM framework. That candidate should therefore remain explicitly unconfirmed.

**Predictive AI as a possible AI-SDM function**

**Predictive AI uses healthcare data to estimate future outcomes, risks, patterns, or resource needs; it is not itself a complete shared-decision process.** Predictive outputs can support early diagnosis, risk stratification, triage, proactive care, resource allocation, and treatment planning, but prediction alone does not provide explanation, reasoning, patient deliberation, or a final decision. [54] [56]

Healthcare examples include forecasts of patient admissions and hospital-resource needs; predictions supporting personalized treatment and dosing; sepsis-onset prediction in intensive-care settings; forecasts of cardiovascular events, cancer recurrence, diabetes, hypertension, disease severity, deterioration, hospital admission, and discharge time; and disease-outbreak forecasting for targeted public-health responses. [54] [56] The inputs and outputs depend on the clinical task: examples include electronic health records, wearable sensors, medical images, vital signs, laboratory results, genomic data, clinical history, and behavioural data producing risk estimates, classifications, alerts, or forecasts. [56]

A systematic review published **September 24, 2025** examined **22 studies** of predictive machine learning in healthcare covering work from **2021–2025**. It reports common use of tree-based ensembles such as Random Forest, XGBoost, and LightGBM, alongside deep-learning architectures such as convolutional and recurrent neural networks. The review also reports that predictive applications are concentrated in high-acuity, data-rich intensive-care settings, while oncology, chronic disease, and primary-care applications remain less explored. [56]

Predictive outputs are dependent on definitions and modelling choices. A general statistics example expresses an estimated quantity as **Q = a + b₁P + b₂S**, where the forecast depends on assessed population and surface area and the coefficients are estimated through survey procedures. The example is not healthcare AI, but it illustrates why the target population, variables, model specification, and estimation method must be made explicit rather than treating a forecast as an unquestionable fact. [55]

Within an AI-SDM workflow, predictive AI could therefore supply a risk estimate or forecast to a clinician, patient, or shared deliberation process, where it is interpreted alongside patient preferences, clinical evidence, and uncertainty. It should not replace either participant’s decision role. The healthcare review reports that prospective validation and real-time deployment were uncommon, clinician-in-the-loop frameworks were often missing, and outputs were sometimes poorly aligned with clinical priorities. [56]

The main limitations are data quality and representativeness, privacy, limited generalizability across institutions and populations, data latency, workflow integration, interpretability, and insufficient prospective validation. The review also notes that stringent inclusion criteria excluded some non-English research and studies from underrepresented regions, including Africa, Latin America, and Eastern Europe, which may affect generalizability. [56] The European Commission likewise emphasizes high-quality and diverse health data, safety, trustworthiness, workflow integration, clear user information, and human oversight for high-risk medical AI; the cited **August 1, 2024** AI Act date and associated requirements are EU-specific and should not be generalized automatically to every jurisdiction. [54]

Predictive AI remains distinct from transparency, XAI, and reasoning. Techniques such as SHAP and LIME can make feature contributions or model behaviour more interpretable, but they are additional interpretability methods rather than the prediction itself. The review notes that complex black-box models can be difficult for clinicians to understand and trust and that interpretability methods are often underused. [56]

**Generative AI, reasoning, and unresolved boundaries**

The available generative-AI evidence is insufficient to claim a defined AI-SDM role. It establishes only that generative AI is one functionality area among many and that chatbot-based AI is not synonymous with AI as a whole. Computer vision, physical AI, and other functions occupy different positions in the broader landscape. [53] A generative system may consequently be investigated as a communication or synthesis function, but any patient-facing summary, option explanation, or preference-sensitive dialogue should be labelled proposed or illustrative unless a source documents it.

AI reasoning is also a function rather than a synonym for transparency or XAI. The broader AI-SDM material describes **counterfactual and causal reasoning** that allows decision-makers to ask what might have happened under an alternative action, evaluate decisions not taken, and improve future decisions. [48] This supports an observable reasoning or justification role between model outputs and human deliberation. It does not establish access to a system’s private internal chain-of-thought.

The resulting conceptual boundary is: **predictive and generative AI describe model functions; reasoning describes inference, comparison, or justification; transparency concerns what relevant system information is disclosed; XAI concerns methods for making a model or output understandable; and AI-SDM describes the larger decision-support workflow.** A model can use more than one function and can also be made more transparent or explainable, but none of those properties alone constitutes a complete shared-decision process. [48] [56]

As supported by the evidence cited here, AI-SDM should therefore be presented as a developing, evidence-qualified healthcare application of human-centred decision support—not as an established clinical replacement for patient autonomy, clinician judgment, or shared deliberation.

**Predictive AI as a candidate function**

Predictive AI uses historical healthcare data, statistical algorithms, and machine learning to estimate future outcomes or risk. It is a model function—not an SDM framework or synonym for transparency, XAI, or reasoning [63][65]. Its outputs include risk assessments and forecasts for risk stratification, treatment planning, resource needs, and scheduling [58][63]. In a 2023 U.S. AHA survey of 2,425 acute-care hospitals using predictive models, reported uses included inpatient trajectories (92%), high-risk outpatients (79%), and scheduling (51%) [62].

EHR, imaging, wearable, claims, and trial data can form a single-patient view; poor integration or lineage impairs prediction [63]. Clinicians must check intended population, setting, performance, and bias; out-of-scope use can produce biased assessments, missed complications, or misallocated resources [57][58]. In that survey, 61% of hospitals evaluated accuracy but 44% evaluated bias [62]. Predictive models support—not replace—human judgment [57][58] and respond to prompts rather than initiate, plan, or adapt autonomously [67]. Evidence supports functionality, not an official or exhaustive AI-SDM roster; membership remains open [59][62].

**Generative AI as a candidate function**

Generative AI creates new text, images, medical imagery, synthetic data, or summaries from learned patterns; generation differs from forecasting and does not itself confer decision authority [57][63]. Healthcare uses include documentation, research hypotheses, image enhancement, human-readable forecasts, therapy personalization, cardiac-problem detection, and readmission flagging [60][63]. A chapter published 19 February 2025 describes API-connected EHR models exchanging data for predictive analytics, documentation, and scheduling, but not patient/clinician recipients or SDM stages [60].

A possible AI-SDM pathway pairs predictive forecasts or risk assessments with generative, human-readable outputs, but the evidence does not establish that handoff or confirm either as required [63][65]. Accuracy and failure-mode checks are essential because generative outputs may be incorrect or fabricated; human-in-the-loop review mitigates this risk [57]. A report published 15 August 2026 described a randomized study of over 9,600 patients in 16 Kenyan primary-care clinics: an EHR-integrated generative tool improved decision-making quality, while short-term outcomes did not significantly change [66]. Improved process is not proof of improved outcomes; generative AI remains possible, not confirmed, AI-SDM functionality [60][66].

Predictive AI is a possible model function, not AI-SDM itself: it learns from existing data to classify or forecast, yielding risk scores, predictions, or recommendations; healthcare examples include sepsis and readmission. [46][68][72] U.S. non-federal acute-care hospitals reported EHR-integrated predictive AI in 71% (n=2,080) in 2024 versus 66% (n=2,425) in 2023—adoption, not framework membership. [68] EHR/CDSS outputs reach clinicians; XAI may identify contributing vital signs, laboratory values, or history. [68][43] Context, bias, validation, and generalizability remain essential; among 2024 users (n=1,587), 82% evaluated accuracy, 74% bias, and 79% monitored post-implementation. [68][46]

Generative AI is a possible function: prompts yield summaries, recommendations, conversations, and text/images/video. Uses include administrative work, triage, education, self-management, chronic-disease prediction, and drug discovery; a September 2025 report says 85% of healthcare leaders adopted GenAI at scale, with no denominator specified. [69][70][71][74] Predictive outputs may feed generative prompts for personalization or scenario exploration, but not an AI-SDM demonstration. [73][74] Membership is unverified; hallucination, nondeterminism, bias, and accuracy/privacy/cost/latency risks require human review. [69][72][73]

Predictive AI maps task-specific inputs to forecasts, risks, flags or recommendations; in healthcare it supports—not replaces—decisions [76][77][79]. EHR-integrated use (survey): 71% of US hospitals (2024) vs 66% (2023) [75]. It is a possible AI-SDM function, not confirmed membership. Task mismatch, overfit, drift, bias and weak validation can mislead; an imaging dataset’s 80% chest-tube rate among pneumothorax cases enabled device false positives [76].

Generative AI creates novel content from prompts; fine-tuning enables multimodal tasks, but behavior varies [78][79]. Healthcare examples include synthetic imaging data and new molecules [78]. Kenya trial: EMR “AI Consult” provided diagnostic/treatment suggestions; >9,600 patients, 16 primary-care clinics, improved clinician decision quality [75]. Setting-specific; no proof of AI-SDM membership/generalizability. Both functions require validation, human review and oversight [75][77].

Predictive AI is a possible AI-SDM function: it forecasts patient outcomes/risks from data; probabilities, classifications and alerts inform, not decide, care amid uncertainty, bias and drift [81][82]. Generative AI is a possible function, creating text or images; chatbots can educate, but hallucinations and outdated or guideline-discordant advice require review [80][82].

Generative AI is a candidate function, distinct from transparency, XAI and reasoning, not a verified AI-SDM component. It creates new content, data or solutions from learned patterns: information generation tailors content and information synthesis produces grounded responses [83]. Retrieval-augmented generation appears in non-healthcare information-retrieval evidence, not AI-SDM validation [85]. Healthcare reviews report tailored treatment; synthetic data for training/validation/simulation and decision support; image analysis, risk prediction, education/documentation and personalized surgery. Clinical literature is scarce because GenAI is new; privacy, bias, transparency/accountability are risks, and it supports—not replaces—experts [83]. Predictive AI is only indirectly evidenced: risk prediction and synthetic data may improve accuracy, but its definition, evidence basis and AI-SDM membership are unestablished [83]. AI reasoning applies information and logic to form predictions, inferences and conclusions; this is not proof of private chain-of-thought or authority [51]. Non-healthcare studies show human-edited drafts/summaries, opaque iteration needing verification/accountability beyond disclosure, and context-sensitive XAI feedback/oversight with adaptive, metacognitive, bias-aware input/output support; they do not validate clinical AI-SDM [37][47][84].

Generative AI creates healthcare text and summaries; outputs need checking for errors and hallucinations [87]. Evidence: simulated/limited [88][90]; AI-SDM membership unverified [86].

Generative AI supports healthcare triage, communication, and personalization; AI-SDM membership is unverified, while accuracy, bias, privacy, and workflow-disruption risks need human review [91][92][93][94].

**Generative AI**

Generative AI generates text/images/video rather than merely analysing data; it is a model function, not transparency, XAI or AI reasoning [95][42]. Healthcare uses include patient-specific assessment, diagnostic/treatment suggestions, summaries/notes, communication/education and evidence discovery/screening/extraction/synthesis; use may be direct (provider/patient) or application-integrated [95][97][98][99].

For AI-SDM, it is an evidence-qualified candidate, not verified framework membership: sources do not establish workflow, output mapping, personalization or clinical validation [96][98]. The 14 October 2026 source is a non-peer-reviewed preprint; WHO calls clinical-decision-support LMM use experimental, requiring authorized trials, safeguards, oversight and clinical outcomes [97][99].

Risks include hallucinations/errors, bias/privacy, manipulation, automation bias, unpredictability, changing outputs and poorer provider–patient interaction [97]. A February 2024 review of 33 studies found serious errors in approximately one-third of 180 clinical cases; 65% of other queries were fully accurate/appropriate [95]. FHIR can disclose AI-altered data, not validate it [39]; generated rationales may misrepresent processes and chain-of-thought may not capture reasoning, while empathy remains difficult; human review is necessary [42][95][97].

Generative AI learns patterns from EHRs, images, labs, wearables and patient data to generate summaries, simulations, reports, treatment options and messages [61][100][101]. It may personalize support, but is a candidate function—not AI-SDM itself—and cannot replace clinical judgment [61][101]. Hallucinations, bias and privacy risks require independent review [61][101].

GenAI creates health content [219,365], synthesizes vetted evidence to guidance [102], and classifies/translates/summarizes with human review [103]; AI-SDM membership unverified [367-372].

Generative AI can summarize evidence and tailor information; hallucinations, bias and privacy risks require human review, so it is a candidate—not a validated AI-SDM component [40][104].

Generative AI creates content from diverse inputs and can personalize clinical insights; its AI-SDM membership remains unverified. Errors, bias, and privacy risks require human oversight [105].

Generative AI is a model function—not transparency, XAI, or reasoning—that generates text/images/audio, summaries, answers, and clinical outputs from diverse inputs [107][108]. Healthcare uses span diagnosis/triage, documentation, patient instructions, cited literature answers, personalized insights, and guideline-hybrid systems [41][107]. In a possible AI-SDM workflow it may ask questions, summarize patient information, and pass it to clinicians; it augments—not replaces—deliberation, with verification and authority retained [107][109]. It is a candidate, not an established AI-SDM component; hallucinations, omissions, bias, privacy, opacity, and overreliance need monitoring and oversight [107][109].

PC CDS is adjacent context, not an established AI-SDM component/row: it supports bidirectional communication and shared decisions; AI can collect/analyze data and inform clinical decisions [106][109]. Generative-AI chatbots outside EHR are being explored as one modality [109]. May 2024 AHRQ report: 7 advocates (5 patients, 2 caregivers); preliminary evidence, not an AI-SDM taxonomy [109].

Generative AI creates prompted content; it may summarize evidence or draft messages, but outputs can vary or hallucinate. It is not AI-SDM itself: human review remains necessary [110][111].

Generative AI creates content; healthcare uses include summaries/explanations, evidence retrieval. It is a candidate AI-SDM function, not autonomous; hallucinations need human review [112]

**Component boundaries**

- **Generative AI:** A healthcare model function—not AI-SDM or decision authority—summarizes or creates clinical data, generates likely diagnoses/treatment recommendations, and answers patient queries. Outputs are possible, not certain; clinicians interpret them, patients discuss risks/benefits, and professionals retain responsibility. It supports decisions, engagement, workflows, and research, but requires controls for bias, privacy, transparency, infrastructure, failure modes, validation, and monitoring. Its AI-SDM membership is unestablished; it is distinct from transparency, XAI, and reasoning. [113][114]

- **Additional candidates:** Multimodal/embodied, personalized, metacognitive, neural-network, reinforcement-learning, cognitive-architecture, and LLM/hybrid functions keep the roster open. Educational evidence is heuristic and overlapping, not healthcare evidence or proof of AI-SDM membership; XAI interpretability does not establish these candidates. [44]

- **Evidence retrieval/recommendation:** This function can search/rank literature, build knowledge bases, extract entities, and supply evidence to LLM/CDSS; RAG aims to ground responses. [115][116] Model, prompt, retrieval, or deployment changes can alter recommendations despite unchanged evidence, so AI-SDM membership remains unresolved. [38] A 2025 molecular-tumor-board study found PubMed citations 75% properly cited versus 17% hallucinated; responses were 25% clinician-matched versus 37.5% plausible alternatives. Clinicians oversaw query/review before patient presentation; the pipeline was not fully automatable. [117]

**Evidence-retrieval and recommendation candidates**

Evidence-retrieval or recommendation AI remains an open functionality candidate, not an established AI-SDM component. Clinical-AI tasks can be decomposed into information extraction, evidence retrieval, differential generation, verification, and recommendation, assigned to specialized tools or agents; agentic systems can coordinate retrieval, tool use, and sequential workflows. These are general clinical-AI capabilities—not proof of AI-SDM membership. [118]

Operationally, a candidate could map a patient-specific question and record data to clinical concepts, retrieve curated guidelines or literature, combine that evidence with patient data in a reasoning or generation module, and return a recommendation with source identifiers. Retrieval supplies source material; reasoning synthesizes it; transparency and auditing expose provenance; XAI is a separate explanatory function. A proposed design uses a knowledge layer, retrieval-and-reasoning engine, interface, citation generator, and audit log. [52] In broader clinical decision support, AI adds conversational retrieval, record synthesis, structured reasoning, and generated drafts to alerts, order sets, diagnostic support, and reference information. [119]

The candidate must satisfy the Five Rights: right information, person, format, channel, and time. Outputs should provide options or information rather than a single directive and should be traceable to pertinent guidelines or peer-reviewed literature. Examples include an alert, order set, ranked differential, reference text, or plain-language recommendation delivered through an EHR, app, browser extension, or API. [119] The proposed source-verified design would attach citations and permit later review, while showing a concise recommendation rather than raw model internals or complex probability scores. It remains conceptual, unimplemented, untested, and unvalidated; citation misattribution, missed context, outdated or biased knowledge, latency, usability, privacy, and security remain risks. [52] A February 2026 review of 12 multi-agent RAG studies published from 2020 through 2025 likewise found early-stage evidence, retrieval-quality dependence, computational overhead, and limited clinical or real-world validation; its retriever–reasoner–verifier–safety proposal is not direct AI-SDM evidence. [120]

**Predictive and generative functions**

Predictive AI is a model function—not transparency, XAI, reasoning, or an extra table row. Predictive models estimate classes and risks; classical clinical decision-support systems may output a numeric prediction or hard rule without rationale. The RAG evidence does not define or evaluate Predictive AI, so it cannot establish AI-SDM membership. Any healthcare use must specify the population, target and alternatives, pathway role, reference standard, threshold, and consequences of false-positive, false-negative, and indeterminate results; retrospective accuracy alone is insufficient. [118][120]

Generative AI is likewise a model capability, not an explanation property. Large language models can synthesize medical knowledge and support guideline interpretation, rare-disease diagnosis, patient education, record summaries, translation, and adaptation to different users. RAG pairs generation with retrieval from verified sources and may improve relevance or reduce unsupported outputs, but hallucination, outdated pre-training, poor traceability, citation instability, and limited validation remain concerns. Generated summaries may improve readability while still containing inaccuracies, omissions, or safety-relevant errors requiring clinician review. [118][120] A conceptual design also warns that strict citation integration requires engineering and that citation misattribution is a major risk. Generative AI’s AI-SDM membership therefore remains unverified and cannot substitute for transparency, XAI, or observable justification. [52]

**PC CDS as adjacent context**

Patient-centered clinical decision support (PC CDS) is contextual rather than a requested row or automatic AI-SDM component. AHRQ cases show it connecting patient data and preferences, education, risk information, recommendations, and clinician workflow to shared decision-making: MyPAIN transmitted patient-reported outcomes and education, PainManager supplied EHR-based recommendations, context, and alerts, and DDInteract used a patient-specific risk profile, visual calculator, education, and decision tree. [121]

In a screening example, EHR prompts identified eligibility and reminded clinicians to conduct SDM, followed by a patient-portal reminder. Screening was 22.8% (278/1,219) in phase 1 and 23.7% (298/1,255) in phase 2 after reminders were added; the different denominators prevent attributing the difference to reminders alone. Patients were also less likely to engage with an HbA1c recommendation when they did not believe their primary-care clinician had reviewed or approved it. [121]

PC CDS therefore illustrates the AI-SDM boundary: patient and clinician inputs must fit real workflows and lifeflows. Implementation can be limited by interoperability, regulation, cost, privacy, poor data quality, alert fatigue, missing data, and clinician burden. In one project, about 60% of guideline-adherence concepts were unused or inaccurate, slightly more than 65% of patients lacked patient-specific data, and half of use-case scenarios had data insufficient for accurate alerting. [121] These examples clarify an enabling context, not a fixed AI-SDM functionality roster.

PC CDS is contextual—not an established AI-SDM component or row—using patient data, preferences and social determinants to support shared decisions [123]. AI can analyse data, recommend care, and generate summaries/drafts for clinician review [50]. Workflows elicit goals and require oversight; data errors cause false/missed alerts [122][125]. AI for SDM is nascent [124].

PC CDS: evidence+patient data+delivery+patient-clinician SDM; not proven as AI-SDM [126][127][128]. GenAI: personalized support; review/testing, drift checks, transparency+consent [126].

**Adjacent PC CDS context**

PC CDS is adjacent healthcare-AI context, not automatically an AI-SDM component or comparison row. It links evidence-based guidelines, patient-generated/reported data, preferences, social factors, workflows, and shared decision making, delivering patient-specific guidance to patients, caregivers, and care teams in clinical or nonclinical settings. The AHRQ overview is dated March 2024. [129][130][131][132]

Human–AI teaming evidence is context, not an AI-SDM definition: AI analyzes, scores risk, triages, detects anomalies, and monitors; humans integrate context and values, question or override outputs, and retain accountability. Transparent interfaces, provenance, audit trails, escalation, and human review support augmentation rather than replacement. Retrieval needs human validation because sources may be outdated or hallucinated; rationales, confidence, and evidence links aid interrogation, while post-hoc explanations may mislead. AI reasoning can clarify goals, surface assumptions, track trade-offs, flag conflicts, and generate alternatives, but humans remain ethical authority. These are supporting properties or functions, not the decision framework itself. [45]

AI-SDM is ambiguous: a 4 May 2023 Carnegie Mellon announcement uses it for a societal/public-health institute, not a patient–clinician framework. It proposes human-centred tools attentive to bias, risk, trust and equity, but does not establish the requested framework or an exhaustive roster [133].

Evidence is early: 2022 scoping review (6 ML studies; to May 2021) called it “in its infancy” and did no quality appraisal [137]. Coverage: 3+3 primary/secondary-care interventions, 4 regions (diabetes/stroke/NICU/knee); preliminary scan: 22 stakeholders/7 countries—not validation [134][137]. Inputs: EHR/sensors, guidelines, demographics, outcomes/comorbidities, evidence/values. AI-SDM supports SDM: team/option/decision talk; AI gives predictions/recommendations, tailored info/outputs; human deliberation; clinician final discretion, patient may refuse AI [136]. Predictive AI: data-based outcome/risk candidate; generative workflow/fixed roster unestablished; evidence-based options do not establish retrieval/recommendation membership; 15-Sep-2023 seminar/video metadata only [137][135]. Risks: privacy, trust/transparency/explainability, bias/missingness, generalizability/reproducibility, cost/time/acceptance, complexity, values [134][137].

Predictive AI is task-specific: it maps patient data to predictions influencing decisions (sepsis, diagnosis, screening, triage); population shifts or updates can cause drift, false alarms, testing and cost [64][138]. Generative AI accepts multiple inputs and produces diverse content, including clinical support, chatbots and recommendations; multi-step errors, hallucination, bias, automation bias and privacy require human oversight [138]. Evidence does not establish an AI-SDM component; retain source snapshots and exact spans before attributing it [138][89].

Allowed evidence supports AI-SDM only as an evidence-qualified support layer for patient–clinician shared decision-making, not as a validated replacement for human judgment; the literature remains heterogeneous, with limited experimental effectiveness evidence [49]. The functionality roster remains open: candidates include decision aids, conversation support, recommender and rule-based systems, collaborative filtering/NLP, and recording, transcription, summarization, speech analysis, or outcome visualization; no canonical component list is established [49]. Recommenders retrieve, predict, and rank options but may neglect patient values; value-flexible designs, preference weights, and clinician dialogue may improve alignment, whereas inferred preferences from similar patients are conditional and not suitable for everyone [49].

**Component functions and safeguards**

**Inputs, outputs, and human deliberation**

## 3. How an AI-SDM process can work

### An ordered workflow from preparation to follow-up

**The sequence supports an iterative conversation.** The workflow below combines documented AI-support functions with established SDM practice. Its logical order helps explain responsibilities and information flow, but real consultations may move backward and forward as understanding or preferences change. Elwyn and colleagues’ revised three-talk model likewise treats SDM as collaborative and potentially recursive rather than rigidly linear. [27]

1. **Frame the decision and establish context.**  
   The patient and care team identify the healthcare problem and the decision being considered. Relevant inputs may include history, investigations, current symptoms, previous treatment, patient-reported information, and practical circumstances. The clinician establishes which options are medically reasonable and whether there is time and capacity for deliberation.

   The patient should also understand the AI’s role: what it is helping with, what information it uses, and who reviews its contribution. This is where system transparency becomes directly relevant to the clinical relationship. It prevents a patient from mistaking an automated interaction for a clinician’s assessment. [1]

2. **Generate decision-relevant support.**  
   Depending on the application, AI produces individualized predictions, clinical summaries, evidence summaries, option comparisons, or explanatory material. Predictive outputs should retain their outcome definition and time horizon; generated summaries should preserve the distinction between recorded facts, model estimates, and suggested questions.

   The purpose is to supply useful material for discussion, not to convert an early model output into an irrevocable recommendation. If an application includes intervention simulations, those should be interpreted according to the evidence supporting them. Different treatment options may have consequences that the model does not represent. [23]

3. **Elicit goals, values, and preferences.**  
   The patient is asked what they hope to achieve, what worries them, and which trade-offs they find acceptable. This can include desired activities, tolerance of side effects, recovery burden, treatment convenience, or preferred involvement in the decision. AI may structure the questions and summarize the responses.

   The patient should be able to revise or reject that summary. A statement such as “I want treatment X” may be a starting position, whereas “I want to regain enough mobility to garden” describes a goal that several options might address. Roche’s illustrative knee-replacement case uses precisely this distinction to show why eliciting goals matters. [18]

4. **Prepare the patient for deliberation.**  
   The patient receives understandable information about the reasonable alternatives, their potential benefits and harms, and the uncertainties relevant to the choice. Conversational AI may clarify terminology, organize questions, or provide an accessible summary. Visual or written decision aids can support the same purpose.

   Preparation should create opportunities to ask questions rather than pressure the patient toward the system’s preferred answer. NICE recommends personalizing information about risks and consequences and making clear how the evidence applies to the individual. It also supports quality decision aids and pictographs where useful. [22]

5. **Review and contextualize the outputs.**  
   The clinician checks the clinical information, evaluates whether the model is appropriate for this patient, and considers important factors outside its scope. The clinician may accept an estimate as useful, correct an input, seek further information, or reject a recommendation. A preference summary may also require clarification if the patient’s words have been simplified or misinterpreted.

   This review is a substantive task, not merely a confirmation button. AHRQ emphasizes that AI may omit context known to clinicians and may generate incorrect or misleading content. The clinician’s contribution is to integrate the tool’s output into a fuller clinical picture. [2]

6. **Deliberate together about the alternatives.**  
   The clinician and patient compare options in light of the evidence and what the patient values. They discuss disagreements, uncertainty, burdens, and the reasons behind a professional recommendation. The patient may clarify a preference, change their mind, ask for more time, or choose to involve a support person.

   This is the decisive SDM step. Elwyn and colleagues’ “team talk,” “option talk,” and “decision talk” describe supporting the patient, comparing alternatives, and arriving at a decision reflecting informed preferences. AI-generated material can assist these conversations, but displaying it does not itself establish that they occurred. [27]

7. **Agree, document, and revisit the plan.**  
   The output is an informed preference and an agreed care plan—or a decision to defer while obtaining information or allowing further reflection. The record should include the decision and what the patient said was important. The parties should agree when and how the plan will be reviewed.

   Where AI materially contributed, documentation can also capture the question asked, the AI response, clinician review, date and time, and relevant references. These fields distinguish the AI’s contribution from the human decision and support continuity when care passes between professionals. [22][6]

### Why information must flow in both directions

**AI support should permit correction.** In a one-way system, the patient receives a recommendation and is asked whether to accept it. In a more patient-centered interaction, the patient can correct symptoms, challenge a preference summary, and explain why an option is impractical. The clinician can likewise correct context or explain why a model’s assumptions do not apply.

**PAIGE illustrates a useful handoff.** AHRQ describes PAIGE as taking a patient’s question, asking one or more clarifying questions, and generating a summary that the patient reviews before it can be sent to the clinician. Its pilot evaluation highlighted the importance of retaining the patient’s own words and integrating electronic health record context. The mechanism is not simply faster text generation; it is a more informative exchange between patient and care team. [2]

**A summary can otherwise distort priorities.** Compressing a patient’s narrative may remove qualifications, uncertainty, or the distinction between a fear and a settled preference. Allowing review helps preserve meaning, especially when the summary will influence the clinician’s first impression. It also gives the patient an opportunity to develop their own understanding before the visit.

### Human responsibility and the decision’s boundaries

**Shared decisions preserve distinct responsibilities.** The patient’s authority over their own healthcare should not be confused with the clinician’s responsibility for clinical assessment and professional recommendations. “Human in the loop” should not mean that the clinician simply approves whatever the AI proposes; nor should it mean that AI grants the clinician authority to bypass patient preferences. AHRQ’s SDM definition preserves both patient leadership and care-team expertise. [16]

**The regulatory boundary is specific.** The FDA’s January 29, 2026 *Clinical Decision Support Software* guidance explains that one criterion for the specified Non-Device CDS exclusion is enabling a healthcare professional to independently review the basis for recommendations, so the professional is not intended to rely primarily on them. All four statutory criteria must be satisfied for that exclusion. This is a particular US regulatory classification, not a universal legal rule governing every AI-SDM application. [28]

**Some settings require different procedures.** NICE’s ordinary SDM guideline excludes unexpected emergencies requiring immediate life-saving care and situations in which an adult lacks decision-making capacity at the relevant time. These circumstances require appropriate emergency or substitute-decision processes rather than mechanically applying a routine consultation sequence. This does not mean that all urgent-care decisions exclude SDM; the available time and nature of the decision matter. [22]

**The workflow succeeds through human use.** AI-SDM occurs when reviewed information and explicit patient priorities actually shape deliberation and the resulting plan, not simply when a system generates a personalized recommendation.

## 4. Comparing AI-SDM, traditional SDM, and XAI alone

**The approaches perform different jobs.** Traditional SDM is already a personalized, evidence-informed human process. AI-SDM adds AI-supported analysis or communication to that process. XAI alone concerns understanding an AI model and can contribute to either clinical review or an SDM conversation without constituting the whole conversation. [16][23]

| Dimension | AI-Supported Shared Decision-Making — AI-SDM | Traditional Shared Decision-Making — SDM | AI Explainability — XAI alone |
|---|---|---|---|
| Purpose | Align evidence, individualized information, patient priorities, and clinical judgment | Develop informed preferences through evidence-and-values deliberation | Make model behavior or an output understandable and inspectable |
| Output format | Tailored comparisons, predictions or summaries, preference record, shared care plan | Conversation, decision aids, informed preference, agreed or deferred plan | Prediction plus explanation: attribution, heatmap, counterfactual, cases, or rationale |
| Workflow integration | Before-visit preparation; consultation review and deliberation; documentation and follow-up | Preparation and consultation, potentially across several visits | Alongside a model output, alert, recommendation, or report |
| Personalization level | Intended to tailor clinical information, communication, and preference support | High in principle through personal circumstances, goals, and dialogue | Can explain one patient’s prediction; value personalization is not inherent |
| Patient’s role | Express and revise priorities; check summaries; compare options; participate in decisions | Share goals and values; understand trade-offs; lead or share the choice | May receive an explanation; active decision participation is not built in |
| Clinician’s role | Review AI, contextualize evidence, discuss recommendations, preserve clinical responsibility | Explain evidence, recommend, clarify understanding, support deliberation | Interpret and challenge the explanation; accept, modify, or reject model advice |
| AI usage | Predictive, generative, conversational, or other appropriate assistive functions | AI is not required; conventional digital aids may be used | Interpretable model or an existing model plus an explanation method |
| Transparency | System disclosure plus understandable outputs and clear human responsibilities | Clear communication of evidence, options, consequences, and uncertainty | Model- or output-level insight; broader system disclosures remain separate |
| Limitations | AI errors, bias, privacy, access, overreliance, and workflow burden | Time, communication skills, literacy, numeracy, and organizational constraints | Approximation, non-causal interpretation, cognitive load, and misplaced confidence |

**The comparison follows established role descriptions.** AHRQ and Elwyn establish the traditional SDM roles and process; Hao and colleagues and AHRQ’s patient-centered AI work supply examples of augmented interaction; the healthcare XAI literature supplies the explanation functions. NICE provides the requirements for personalized communication, joint planning, and documentation. [27][19][22]

### Personalization: what AI changes and what it does not

**Traditional SDM is not generic care.** “Traditional” here means that AI is not required, not that the clinician ignores individual risks or patient preferences. A skilled clinician can tailor a discussion to the person’s circumstances, use a conventional risk calculator, and explore values in depth. NICE explicitly recommends personalizing risk, benefit, and consequence information as much as possible. [22]

**AI can extend personalization’s reach.** It may process more information, tailor preparatory content, ask follow-up questions, or organize patient-reported concerns between visits. This can make it easier to bring relevant context into a short consultation. Whether it actually improves the encounter depends on the relevance and accuracy of those contributions and whether the clinician and patient use them.

**Patient-specific does not mean preference-sensitive.** A local XAI explanation may describe exactly why a model predicted a particular patient’s risk. That is individualized model information. It does not necessarily explain whether the model’s preferred outcome is the patient’s preferred outcome, whether the patient accepts the treatment burden, or whether the recommendation fits their circumstances.

**Preference support must remain contestable.** A prediction that someone is likely to choose a treatment is not equivalent to asking what they now want after understanding the alternatives. Yang and colleagues’ review found that many AI preference applications emphasize prediction and decision support rather than patient self-reflection. For AI-SDM, inferred preferences should therefore be treated as prompts for discussion rather than replacements for an expressed choice. [26]

**The advantage is conditional, not automatic.** AI-SDM has a stronger personalization claim when it combines appropriate clinical estimates with patient-confirmed priorities and accessible communication. That claim weakens if it mainly reproduces population averages, assigns preferences from demographic similarity, or generates tailored language around a predetermined recommendation.

### The patient–clinician relationship: support without displacement

**AI changes preparation and mediation.** In traditional SDM, the clinician often performs most of the work of explaining evidence, eliciting concerns, and organizing the encounter. AI can redistribute some preparatory and information-processing tasks. A patient may arrive with clearer questions, while a clinician may arrive with a more structured picture of the patient’s priorities.

**Authority should not follow the interface.** A prominently displayed recommendation can become the default around which the conversation revolves. If the patient’s role is reduced to consenting to that default, the interaction may be technologically sophisticated but weak in shared decision-making. The same concern applies when a clinician uses the explanation mainly to persuade rather than to examine alternatives.

**XAI can support a genuine conversation.** Amann and colleagues explicitly propose explainable AI as a personalized conversation aid that could raise choice awareness and help elicit values. This is an important counterexample to portraying XAI and SDM as competing approaches. Once the explanation is incorporated into preference elicitation and joint deliberation, it becomes part of a broader decision process. [23]

**Clinician recommendations still have a place.** SDM does not require clinicians to remain neutral about every option or leave patients alone with difficult choices. Professional advice can be valuable, especially when uncertainty is distressing. The distinguishing feature is that the recommendation is discussed in relation to the patient’s understanding and priorities rather than treated as an unquestionable command. [11]

### Choosing the appropriate approach

**Choose SDM for preference-sensitive care.** When reasonable options involve meaningful trade-offs, a shared conversation is the foundation. It can be supported by paper materials, established digital aids, or ordinary clinical discussion. An AI component should earn its place through a relevant contribution rather than being treated as a prerequisite for modern care.

**Use AI-SDM for useful augmentation.** AI support is most compelling when it addresses a concrete difficulty: preparing patients, synthesizing complex information, estimating relevant outcomes, or preserving patient priorities across visits. The application should still leave space for disagreement, correction, and a decision to defer. Its value is the improvement in the supported human task, not the quantity of generated material.

**Use XAI for model inspection.** When the immediate question is why a model produced a result or whether its basis seems clinically appropriate, XAI is the relevant capability. It may help a clinician challenge a recommendation or communicate it to a patient. It should not be credited with preference elicitation or authority sharing unless those activities actually occur.

**The appropriate relationship is complementary.** Traditional SDM supplies the ethical and conversational foundation; AI can augment it; XAI can help inspect some of the AI’s contributions.

**Additional documented evidence**

| Entity | entity / approach name | purpose | output format | workflow integration | personalization level | patient's role | clinician's role | AI usage | transparency | limitations |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| AI Explainability (XAI) | no evidence found | no evidence found | no evidence found | XAI is integrated by presenting explanations…[190] | The source supports explanation customization to…[151] | no evidence found | no evidence found | In an XAI-alone approach, AI is used to render model…[182] | The page does not substantively describe how…[146] | The source's XAI entry does not state technical…[211] |
| Traditional Shared Decision-Making (SDM) | no evidence found | The source states that transparent reasoning can…[192] | no evidence found | no evidence found | Personalization in Traditional SDM is based on the…[252] | no evidence found | no evidence found | In the cited overview, explainability is relevant to…[206] | no evidence found | Time, literacy, workflow, and implementation barriers[236] |

Across the requested dimensions, AI-Supported Shared Decision-Making (AI-SDM) applies the PC CDS-SDM Framework: evidence, patient data, and recommendations move through team, option, and decision talk to contextualize benefits and risks around values, preferences, circumstances, and goals while preserving clinical expertise and autonomy [269][260]; Traditional Shared Decision-Making (SDM) follows situation, option, harms-and-benefits, and preference deliberation to a patient–clinician decision [268]. XAI alone explains model behavior or features but may leave clinicians without context or an actionable plan [195][197][196], so the contrast is supportive AI in shared deliberation, human deliberation as the baseline, and explanation as a technical layer, with early clinician-led evidence for AI-SDM [241], workflow barriers for Traditional SDM [253], and black-box, bias, and actionability limits for XAI [197][195].

Traditional SDM should remain the human clinical process within which the other concepts operate: patients and clinicians exchange evidence and preferences, deliberate, and decide together [233]. AI Transparency supplies system information, XAI supplies interpretability and communication, and AI Reasoning exposes the process behind a recommendation; together they should make outputs inspectable and challengeable while leaving synthesis and responsibility with clinicians [193][194][212][218].

AI Transparency should fill the comparison’s transparency column, not become a fourth approach: it makes system operation, data, training, documentation, and decision basis accessible to relevant users [147][149]. It supports consent, safety, accountability, and oversight across AI-SDM and XAI, while XAI is one way to provide explanations within that broader property [141][145].

Predictive AI belongs in the AI-usage, output, and personalization cells, not as an extra approach: it learns patterns to produce task-specific classifications, risk scores, or forecasts that can inform patient risk assessment and shared decisions [68][79][267]. Its usefulness depends on integrated patient data and clinical oversight; population shifts can reduce performance, and predictions may be inaccurate, biased, hard to interpret, or trigger false alarms and unnecessary tests [63][64][77][254].

Generative AI is another possible AI-SDM function, not a table row: it transforms records, images, or questions into summaries, explanations, drafts, and personalized communication for option discussion [80][251][248]. It can improve output and patient-facing personalization, but generated content is not reliable individualized risk assessment or autonomous advice; it remains a draft requiring error and provenance checks because fluent language can still be untrustworthy [249][87][40][254].

An evidence-retrieval or recommendation component can insert source retrieval before recommendation generation, bring guidelines or studies into the workflow, and link claims to evidence without expanding the row roster [52][119]. Its safe use depends on the Five Rights and on current, high-quality knowledge sources [119][120].

Place the comparison immediately after the AI-SDM introduction and use exactly these rows: AI-SDM, Traditional SDM, and XAI alone, with separate columns for purpose, output format, workflow integration, personalization, patient and clinician roles, AI usage, transparency, and limitations. The row logic is supported by the PC CDS-SDM Framework [269], Traditional SDM’s deliberation pathway [268], and XAI’s explanation-without-action boundary [195].

The comparison table should give each requested dimension its own cell and use the PC CDS-SDM Framework for AI-SDM, the patient–clinician SDM process for Traditional SDM, and explainability functionality for XAI alone [269][268][173].

XAI alone is explainability functionality, commonly an additional post-hoc layer around a predictive model; it explains outputs but does not by itself establish a complete SDM workflow, personalization framework, or actionable decision plan [152][173][195].

Use a common limitations lens: AI-SDM has early, clinician-led evidence and missing patient perspectives [241]; Traditional SDM faces time, continuity, communication, literacy, and implementation barriers [253][234]; and XAI risks misleading or unintelligible explanations, interpretability gaps, bias, and overreliance [206][143]. AI deployments must also check autonomy, privacy, fairness, equity, and trust [245][260].

Traditional SDM belongs in the comparison as a care process, not as another AI explanation method: its defining unit is patient–clinician exchange, preference deliberation, and joint decision-making [236][237].

The table supplies the requested cells for AI-SDM and Traditional SDM: AI-SDM integrates knowledge, patient data, and delivery into team, option, and decision talk [269], whereas Traditional SDM supplies patient–clinician deliberation and option clarification [268]; XAI’s explanation-only contrast is captured separately [195].

Traditional SDM’s comparison basis is its structured choice-to-decision process [268]; material limits include time, continuity, communication, patient readiness, organizational support, and implementation barriers [253][234].

After the AI-SDM introduction, the comparison uses the requested AI-SDM, Traditional SDM, and XAI-alone rows: AI-SDM is the PC CDS-SDM Framework integrating knowledge, data, and delivery across SDM talks [269], Traditional SDM is collaborative deliberation [268], and XAI alone is explanation functionality that may leave context and actionability unresolved [195].

XAI alone is the requested technical baseline: it provides model-based or post-hoc explanations for interpretation and audit, not a complete shared-decision process [152][195].

The table retains only the requested approaches as rows: AI-SDM integrates support into SDM [269], Traditional SDM supplies collaborative human deliberation [268], and XAI alone supplies explanations [195].

Traditional SDM is a care process rather than a simplified explanation method: patients and clinicians exchange information, explore options, express preferences, and decide together [235][268].

The AI-SDM row is completed by the PC CDS-SDM Framework: evidence, patient data, and recommendations support team, option, and decision talk, contextualizing benefits and risks to values, preferences, circumstances, and goals while preserving autonomy and clinical expertise [269][260]. Its evidence base remains limited and initially clinician-led, with patient perspectives reserved for later study [241].

Traditional SDM’s row is collaborative deliberation: meaningful dialogue and decision aids support a jointly considered, value-concordant choice across preparation, encounter, and follow-up [235][234][268].

The second comparison is a clear table with the requested rows and separate columns for purpose, output format, workflow integration, personalization, patient and clinician roles, AI usage, transparency, and limitations. It contrasts AI-SDM’s integrated decision support [269][260], Traditional SDM’s collaborative deliberation [268][235], and XAI alone’s explanation-without-action boundary [195].

Across the rows, XAI is a technical explanation layer that adds model, feature, visual, text, or rule explanations for review but may leave clinicians without context or an actionable plan [152][195][160]; AI-SDM embeds patient-centred decision support in SDM talks, uses recommendations and patient-specific information, and keeps patient values and clinician expertise central [269][260]. Traditional SDM is the human comparison: meaningful dialogue and decision aids support a jointly considered choice, while time, continuity, communication, literacy, evidence, and implementation barriers constrain it [235][268][253][234].

The table contrasts AI-Supported Shared Decision-Making (AI-SDM), Traditional Shared Decision-Making (SDM), and AI Explainability (XAI): AI-SDM enhances person-centred SDM while preserving autonomy and expertise [260], using patient-specific recommendations and values/preferences across team, option, and decision talk [269]; Traditional SDM uses dialogue and decision aids for a joint evidence- and preference-aligned choice, with values/preferences expressed in 64 instances [235][221]; XAI makes model workings understandable [210] through a post-hoc review layer [152], not shared deliberation [173]. AI-SDM and Traditional SDM retain patient–clinician roles; limitations are AI-SDM’s limited evidence from six professionals with patient perspectives deferred [241], SDM time/workflow barriers [221][234], and XAI misleading or non-actionable explanations [206][143][195].

The table uses exactly AI-Supported Shared Decision-Making (AI-SDM), Traditional Shared Decision-Making (SDM), and AI Explainability (XAI) as its rows: AI-SDM is the supportive deliberation framework [260][269], Traditional SDM the human joint-decision baseline [235], and XAI the explanation layer [152].

The table keeps purpose, output format, workflow integration, personalization level, patient's role, clinician's role, AI usage, transparency, and limitations as separate columns. It represents AI-SDM with personalized SDM-phase recommendations [269], Traditional SDM with dialogue and decision aids [235], and XAI with transparent post-hoc explanations [152][210]; limitations include limited AI-SDM evidence [241], SDM implementation barriers [234], and misleading XAI explanations [206][143].

**Traditional Shared Decision-Making (SDM): the human-care baseline**

Traditional SDM is a non-AI, patient-centred communication process for preference-sensitive healthcare decisions: clinicians and patients share the best available evidence, consider options and benefits or harms, discuss values and concerns, and reach informed preferences. The clinician contributes medical and treatment expertise; the patient contributes expertise about preferences, values and concerns. Traditional SDM is therefore the human-care baseline for comparing AI-SDM, not an AI system itself. [221][222]

**Purpose and process.** Traditional SDM supports patient-centred choices when clinically reasonable options have different trade-offs. In breast-cancer care, a patient may choose lumpectomy or mastectomy according to priorities such as preserving breast tissue or avoiding daily radiotherapy. The process involves exchanging clinical information, risks, uncertainties and options; eliciting questions and preferences; deliberating with clinicians and, if desired, family caregivers or the wider care team; and making or supporting a treatment choice. Outputs are shared understanding, conversation and a patient–clinician choice. Patient decision aids may add side-by-side option comparisons and risk or knowledge support, but they are tools within SDM, not SDM itself. [221][222]

**Personalization and roles.** Traditional SDM is highly personalized: clinical characteristics, physiology, genetics, risk tolerance, preferences, work, hobbies, family circumstances and life events may matter. Patients ask questions, express values, help share information and may choose among feasible options; participation can range from informed non-dissent after a clinician recommendation to patient-driven choice. Clinicians explain options, risks and uncertainty, interpret evidence, answer questions, may recommend, and coordinate with colleagues. In one observed breast-cancer workflow, patients explicitly communicated values or preferences in 64 coded instances and performed information-broker tasks in 74; clinicians shared risk information in 82 instances and used risk to discuss uncertainty in 81. [221]

**AI, transparency and limits.** Traditional SDM has no defining AI component or autonomous decision authority. EHRs, decision aids and other technologies may support it, but the observed process was not characterized as AI and technology did not replace human deliberation. Its transparency is communicative—diagnosis, evidence, options, risks, benefits and uncertainty explained through discussion, visuals, paper or shared screens—not disclosure of algorithmic internals. Limitations include time pressure, emotional burden, jargon, variable health literacy or numeracy, incomplete information, interdependent decisions, fragmented workflows, unclear roles, clinician time and knowledge constraints, and the need for training and organizational support. [221][222]

**Evidence boundary.** The main empirical evidence is a 2024 observational breast-cancer workflow study at one U.S. academic centre: 20 clinician observations, 79 hours and 118 encounters during February–August 2022; it is not a universal account of SDM. A 2024 commentary supports the healthcare definition but does not validate AI-SDM; a preview published on 23 April 2026 provides publication context only, not substantive SDM evidence. [220][222] “SDM” can also mean spatial division multiplexing in optical communications, so the healthcare meaning should be stated explicitly. [223]

Traditional SDM is a non-AI patient–clinician process: introduce choice, describe options, explore preferences, and jointly choose care using patient values, goals, context, and evidence; it is AI-SDM’s human baseline, not an AI model [227][231]. Its output is dialogue and a joint treatment choice; a rheumatology example is a web-based DMARD aid [229]. Patients learn and express preferences; clinicians provide expertise, explain options, make choice explicit, and decide with—not for—the patient [224][230]. Personalization is contextual, not one-size-fits-all [225][229]. SDM itself uses no AI; aids may support communication without replacing human responsibility [224][230]. Transparency is conversational—options, evidence, risks, benefits, and fit—not algorithmic internals [224][231]. Limits include time, literacy/language barriers, overload, miscommunication, uneven participation, and missed choice awareness; a 2022 hospital thesis observed these in 781 consultations, not universally [224][230]. XAI alone gives treatment-option explanations; current systems may be one-size-fits-all, and interactive tailoring remains proposed. It does not establish a full SDM workflow, patient authority, or independent AI decision authority [155]. A 2026 Netherlands–Flanders event listing is implementation context only; a retraction notice is not SDM evidence [228][226].

Traditional SDM: non-AI collaboration—evidence + patient values → informed joint care plan; high personalization; patient leads, clinician explains, tools support not replace judgment; transparency is conversational; limits: time, inequity, uncertainty [267,268,269]. XAI alone gives contextual explanations, not SDM, participation, or authority [158].

Traditional SDM: non-AI, patient–clinician preference-led deliberation to joint choice; aids supplement dialogue; options/risks disclosed; limits: time/literacy/uptake [236].

Traditional SDM is a non-AI patient-clinician process: evidence and options are exchanged, values and preferences guide deliberation, and the parties reach a choice [238].

Traditional SDM is non-AI: patient–clinician exchange—evidence/options, values, deliberation, choice; personalization, communicative transparency, limited adoption. [239]

Traditional SDM: non-AI transparent patient–clinician dialogue/aids elicits values, co-creates personalized plans, shares roles, excludes AI; time/equity/workflow limits [240].

**Traditional Shared Decision-Making (SDM)** is a non-AI patient–clinician process: evidence and options are shared, preferences are deliberated, and a choice is made together, especially when multiple reasonable healthcare options exist [242]. Outputs are dialogue, informed preferences, a decision, and optional text/diagram aids; workflow is choice→option→decision talk, sometimes across visits [242]. It is highly individualized: patients assess options and state preferences, while clinicians explain evidence, facilitate deliberation, and support autonomy [242]. AI is absent from the baseline; a **2024 i-SDM study of six US cancer-care clinicians** presents AI-SDM as a proposed assistant for tailored education and treatment-option discussion, with patient perspectives pending; human judgment remains decisive [241]. Transparency covers evidence, benefits, harms, uncertainty, and values—not algorithmic internals [242]. Limits include time, literacy/numeracy, cultural and routine-practice barriers; the **2012** model is simplified and non-prescriptive, while generic tools may introduce bias or inequity [241][242].

Traditional SDM is non-AI patient–clinician dialogue: evidence, options and preferences are exchanged; patients deliberate and choose/defer, while clinicians facilitate.[243]

Traditional Shared Decision-Making (SDM) is the human-care comparator for AI-SDM, not an AI model: patients and clinicians exchange information, deliberate about options and preferences, and reach, implement, review, or defer a choice. Models vary in detail, but a common sequence is choice talk, option talk, and decision talk. [246][247]

**Traditional SDM:** **purpose**—support high-quality, patient-oriented decisions when options involve value-sensitive trade-offs; **outputs**—decision aids, option comparisons, risk–benefit and uncertainty information, value-clarification materials, and a choice or deferred plan; **workflow**—choice, option, and decision talk, with aids linked to guidelines or electronic records at decision points; **personalization**—individualized through values, preferences, circumstances, and patient-reported information, although preference sensitivity varies; **patient**—central participant who expresses values, deliberates, and decides or reconsiders; **clinician**—diagnoses, presents and interprets options, checks understanding, and supports deliberation; **AI usage**—none in the baseline, although computerized tools may support it; **transparency**—accessible communication of evidence, benefits, harms, risks, and uncertainty, not algorithmic internals; **limitations**—health-literacy and communication barriers, information overload, cognitive or emotional burden, complex or urgent choices, uncertain evidence, inequitable access, burnout, paternalism or bias, and time, training, organizational, and implementation constraints. Decision aids alone do not ensure full SDM. [148][246][247]

AI context is separate: a 2024 neuro-oncology account describes patient input, LLM-tailored evidence, patient consideration, physician discussion and interpretation, clarification, collaboration, and follow-up; LLMs should support rather than supplant clinicians, and implementation varies by setting. [148] Another project uses automated prediction to facilitate patient-provider SDM and involves patients and providers as co-designers, while targeting personalized feedback and aggregated public-health information and minimizing threats to autonomy, privacy, security, integrity, solidarity, fairness, inclusiveness, transparency, and equity; this is not a definition of Traditional SDM. [245] The retained AI-Transparency extract identifies only a 2023 research-roadmap title and establishes none of its focus, goals, audience, core questions, or outputs. Here, AI Transparency is therefore a cross-cutting transparency dimension, not a fourth comparison row. [148]

Traditional SDM is non-AI: clinicians explain options, harms, benefits and alternatives; patients state preferences; both deliberate toward a mutual plan [252].

**Traditional SDM as the human-care baseline**

Traditional Shared Decision-Making (SDM) is a human, non-AI process in which patient and clinician combine evidence, clinical knowledge, values and preferences to reach the best healthcare decision for that patient [235]. It is not an AI model or an explainability method, but the care-process baseline for comparison [235][253].

Traditional SDM — **purpose:** patient-centred choice; **output:** meaningful dialogue, evidence-based resources or decision aids, and a jointly reached and evaluated decision; **workflow:** seek participation, compare options, assess values and preferences, reach a decision, and evaluate it [235]. **Personalization** is based on the individual’s preferences and circumstances; the **patient** contributes goals, values, questions and recommendations; the **clinician** supplies evidence and expertise, explains options and contextualizes deliberation. AI is not intrinsic, although non-AI decision aids, electronic records and information systems can support implementation [235][253]. **Transparency** concerns benefits, harms, risks, probabilities and scientific uncertainty rather than algorithmic internals. Limitations include translating probabilistic evidence, limited time and continuity, fragmented records, communication and training demands, variable decision-aid quality, patient readiness, power dynamics and organizational support [235][253].

The AHRQ implementation guide was last reviewed in **September 2020** and presents research-, literature- and expert-informed implementation guidance rather than an exhaustive current review [235]. A **2026** qualitative study interviewed **18 patients** with multiple long-term conditions in West Midlands GP practices during **January–February 2024**; its context-specific findings add concerns about time, continuity, health literacy, accessibility, depersonalization, data trust and cost pressures, while emphasizing clinician explanation, data provenance and retained clinical judgment [253].

**AI-SDM evidence relevant to the comparison**

Independent evidence documents AI interventions that facilitate SDM rather than one universally standardized implementation. A scoping review published **9 August 2022**, searching **six databases** through **May 2021**, included **six peer-reviewed publications**; all used machine learning and supplied clinical recommendations or predictions, and the authors described the evidence as being “in its infancy” [136]. A related review reports **1,445 records**, **894 screened documents** and **six eligible publications**, with limited attention to patient values, explainability and end-user design [244].

| AI-SDM dimension | Supported answer |
|---|---|
| **AI-SDM purpose** | Supports the decision point with clinical recommendations or predictions so patients and providers weigh options, risks, benefits and outcomes; it supports rather than replaces their decision [136]. |
| **AI-SDM output** | Tailored knowledge or choices, predictions, outcome reports, risk information, recommendations and textual explanations; decision aids and personalized information are also proposed outputs [136][134]. |
| **AI-SDM workflow** | Enters the decision point within team talk, option talk and decision talk; patient and clinician deliberate, with the clinician mediating the output [136]. |
| **AI-SDM personalization** | Can use current condition, metrics, demographics, patient-reported outcomes and comorbidities, but incorporating individual values into algorithm design remains difficult [136]. |
| **AI-SDM patient role** | The patient states goals and preferences, reviews options and may dispute or refuse AI input [136]. |
| **AI-SDM clinician role** | The clinician explains and contextualizes output, adapts it to the patient, monitors care and retains final discretion [136]. |
| **AI-SDM AI usage** | Predictive and recommendation-based machine learning supports, rather than replaces, collaborative SDM; all six reviewed studies used machine learning [136]. |
| **AI-SDM transparency** | Requires interpretable explanations and reporting of data, bias, missingness, AI use and outcomes; reporting and explainability were often poor [136]. |
| **AI-SDM limitations** | Evidence remains early; limitations include poor reporting, limited explainability, insufficient values and end-user involvement, uncertain generalizability and reproducibility, bias or missing data, and trust, responsibility and informed-consent risks [136][244]. |

A preliminary stakeholder report involving **22 participants from seven countries**—seven AI experts, 14 SDM experts including five practicing clinicians, and 10 observer-rated consultation datasets—identified personalized information, decision aids and assessment or training in real or simulated consultations as possible uses; it also reported privacy, reliability, transparency, human-interaction, cost, time, social-acceptance and data-quality barriers [134]. Separately, Carnegie Mellon’s NSF AI-SDM program uses the label for broader public-health and emergency-management research involving human-centric hybrid systems, recommendations, counterfactual reasoning and personalized interventions under uncertain, dynamic and resource-constrained conditions; that adjacent context does not establish clinical patient–clinician validation [257].

Traditional Shared Decision-Making (SDM) is the non-AI human-care baseline: patients, support networks and healthcare professionals exchange information, explain the problem, present options and evidence, discuss benefits, risks and costs, elicit values and preferences, deliberate, and make or explicitly defer a decision [260]. Its format is communication and deliberation—choice talk, option talk, decision talk, mutual agreement or deferral—not an algorithmic score [260]. Patients retain a central role; clinicians contribute expertise, recommendations, evidence interpretation, explanations and partnership [260]. Personalization is conversational and preference-based, while transparency concerns communicated evidence and options, not algorithmic internals [260]. SDM requires preparation and embedding in services; inadequate tools, mismatches with patient ability, integration barriers and decision-culture change remain limitations [260].

For the AI-Supported Shared Decision-Making (AI-SDM) row, allowed evidence supports an intended AI-supported process, not a clinically validated complete framework: AI decision support may enhance SDM and person-centred care while supporting—not replacing—clinical expertise and preserving autonomy and the human factor [260]. Inputs may combine medical or EHR data with personal insights, worries, preferences, lifestyle and risks; outputs may include diagnostic or prognostic categories, treatment options with explanations, evidence, visualizations, recommendations and next-step guidance [260]. Patients and clinicians can discuss these outputs through choice, option and decision talk; personalization is a potential adaptation to the individual, not an established outcome [260]. In mental-health evidence, 1,773 articles published in 2011–2022 yielded 12 eligible studies, and AI decision support remained pre-implementation in practice [260]. Risks include opaque logic, misread language or non-verbal cues, misdiagnosis, workflow burden, privacy threats, weakened relationships, unclear accountability and paternalism [260].

XAI alone focuses on making a model’s decision-making methodology or output understandable; it may provide explanations supporting clinician–patient communication [260]. The evidence does not establish patient participation, personalization or a complete SDM workflow for XAI alone; black-box opacity can reduce trust, autonomy and adoption [260]. Thus, SDM is the care process, AI-SDM the proposed support layer, and XAI an explanatory function—not interchangeable approaches.

Traditional SDM is the non-AI baseline: patients and clinicians share evidence/options, elicit values, and make a preference-sensitive choice with shared authority; its sequence is team talk → option talk → decision talk [49][137]. Time pressure, training gaps, and incomplete preference capture limit implementation [49].

AI-SDM adds assistive AI at the decision point: decision aids/chatbots, risk–benefit profiles, and recommendations (i-SDM/CoroPrevention/Mit-Plan 2.0) support dialogue [49][137]. Preference/value elicitation can personalize outputs, but ML misses nuance; patients can state values or refuse AI, while clinicians explain, check omissions, align values, and retain discretion [49][137]. Risks include misleading/biased outputs, opacity, over-reliance, privacy, role ambiguity, and co-design gaps; evidence is early—six studies in a 2022 review (search to May 2021), only two mentioned explainability and none described how [49][137].

XAI alone gives post-hoc explanations, not full SDM, personalization, or authority; clinicians communicate them [49]. Counterfactual/causal simulations may aid explanation yet not justify patient values or resolve communication, trust, fairness, or reliability problems [49][48]. NSF AI-SDM (launched June 1, 2023) is societal, not clinical validation [258][259].

Traditional SDM is the non-AI patient–clinician baseline: evidence/expertise meet patient preferences and circumstances [122]. Purpose: informed choice (consent/refusal), accountability, safety [207]. Patients state needs/goals; clinicians explain options/risks, review risk–benefits, document/follow up, and retain responsibility [122][262]. Workflow: prepare → elicit → deliberate → record; EHR may assist, but AI is not intrinsic; AI-for-SDM remains early [122][124]. Transparency is clinical, not algorithmic; constraints: time/training, knowledge/confidence, sociocultural barriers, data/workflow/engagement, context/trust [207][122][262].

XAI supplies explanations that make outputs understandable, not full transparency or SDM [207]. Outputs include SHAP/LIME, heatmaps, and counterfactual explanations [192][208]. Clinicians validate/explain; patients may receive information, but XAI alone grants neither shared participation nor authority [207][262]. Personalization is output-level. Limits: opacity, accuracy–explainability trade-offs, bias/data gaps, overdisclosure, resource burden, and accountability [192][261].

Traditional SDM joins evidence with patient values/preferences in shared decisions; XAI alone explains predictions, not choice or authority; clinicians interpret it. [209][168]

Predictive AI: tailored risk/treatment; generative AI: personalization/efficiency; neither row[263].

Traditional SDM: preference-led patient–clinician choice, no AI [125]. XAI-only: explains outputs, not SDM/personalization/authority [201]. GenAI: possible AI-SDM function [255]

Traditional SDM: human, value-based mutual choice [204]. XAI alone explains outputs, not SDM; clinician decides [214]. Predictive AI informs options; GenAI may personalize [264].

Traditional SDM: evidence/options/preferences and joint choice; non-AI [265][266]. XAI alone: explanations; no workflow/personalization/patient role; clinician oversight [265].

**XAI alone:** an explanation function—not a complete SDM workflow or decision authority [169][203]. Outputs include SHAP/LIME contributions, saliency maps, rules, counterfactuals, text and interactive graphics [153][169][203]. Clinicians interpret, verify and explain outputs; patients may query them for consent, but participation is not automatic [206][203]. Interactive feedback may personalize outputs [213]. Limits include misleading explanations, interpretability/confirmation/automation bias, overreliance, overload, privacy, bias and uncertain clinical effects [206][213].

XAI alone: explains AI outputs (heatmaps, saliency), not SDM; clinicians interpret, patient role and AI authority unestablished; limits: opacity, bias, overload, privacy [164][165]

XAI alone = explainability, not SDM, personalization or autonomy; it explains model logic/output [181]. Goal: clinician understanding, verification and appropriate reliance [177]. Outputs: explanations, rationales, uncertainty and counterfactuals [177][202]. Evidence is clinician-facing and simulated [177]. Patient role is unestablished; clinicians interpret, check and decide [178]. Transparency covers data, logic, evidence and limits; risks include bias, error, over-reliance, burden and post-hoc inaccuracy [178][177].

**XAI alone:** purpose—explain AI outputs for care tasks, not SDM [183]. Outputs—local/global explanations (features, SHAP/LIME, Grad-CAM, counterfactuals), predictions, confidence and recommendations [183][205][215]; a March 2026 review found XAI in 13/50 predictive-AI-CDS studies (SHAP in 12; SHAP+LIME in 1) [215]. Workflow—post-hoc in CDS/EHR; clinicians validate or override; patient deliberation is unestablished [183]. Personalization—unestablished; context tailoring [219]. Patient participation/authority is unestablished; clinicians retain judgment [183][205]. AI predicts, explains and recommends; XAI itself assigns no authority [205]. Transparency shows model behavior, features, input-output links or confidence—not safety or causality [184][205][215]. Limits include opacity, cognitive burden, anchoring/overreliance and bias; safety, generalizability and accountability remain uncertain [183][215]. Generative AI is not established as a healthcare component; one source reports only prose editing [219].

**XAI-only:** explanation, not SDM/personalization/authority [157][159]. Purpose: understand model/prediction, trust/error checking; outputs: intrinsic/post-hoc local/global attributions, rules, charts, saliency, counterfactuals, interfaces [160][161]. Workflow: model predicts; clinician interprets/acts [161]. Personalization: audience/context fit [160]. Patient receives explanation; clinician adds context/retains judgment [162]. Transparency: data, development, performance, logic, output; post-hoc may mislead [159][200]. Limits: opacity, bias, privacy, literacy/access, accuracy–interpretability, evaluation/monitoring [156][160][200]. Predictive AI: no AI-SDM membership shown; generative AI: image audits only [156][157].

XAI alone: explanations/heatmaps/attributions [163][167]; clinicians interpret, patients may receive/contest [166]; not SDM or autonomous. Outputs may mislead; validate [167][170].

| Approach | Purpose | Output format | Workflow integration | Personalization level | Patient's role | Clinician's role | AI usage | Transparency | Limitations |
|---|---|---|---|---|---|---|---|---|---|
| XAI alone | Explain how/why outputs arise; support validation, not SDM [172][179]. | SHAP/LIME attributions, saliency/Grad-CAM, integrated gradients, counterfactual or natural-language explanations; a 2023 review of 450 medical supervised-ML uses found SHAP/Grad-CAM leading [171][172][179]. | Layered onto model use, monitoring and audit; no inherent deliberation [172][176]. | Case/audience tailoring may occur; preference-based care personalization is not established [172][182]. | No inherent authority or participation; patient-friendly explanations may support autonomy/consent, depending on the system [180][182]. | Checks clinical fit, safety and applicability, communicates rationale, and retains accountability [179][180][182]. | Interprets inputs/predictions; may alert or rationalize; no independent authority [179][180]. | Shows contributing data/reasoning and audit trails; XAI is only one transparency measure [174][180]. | Explanations may be approximate, misleading or noncausal; a 2024 review found surrogate R²=0.68 for SVM and 0.57 for random forest; bias, attacks, drift and audience mismatch require validation and oversight [172][174][180][182]. |

AI Transparency is a dimension, not a row: XAI adds output visibility; broader transparency requires more than explanations [180]. AI Reasoning is a cross-cutting justification dimension, not a fourth row: in a 12-clinician qualitative study, visual artifacts enabled inspection, comparison and critique, while chat mainly supported lookup; this was walkthrough, not deployment, evidence [218]. A 2025 paper revised on 23 January 2026 proposes Rhetorical XAI—logos, ethos and pathos—beyond traditional individual/system explanations; it is not healthcare validation [185].

XAI alone—out: local/global explanations (attribution, counterfactual, confidence/X-ray views) [191][139]; workflow: clinician validates/decides; patient inspects/contests; no SDM authority [175][154]; personalization: context tailoring ≠ care [191]; AI: explanation only, no authority [175]; transparency: features, uncertainty and reasoning—not full transparency/private reasoning [175][154]; limits: incomplete EHR; automation bias; unreliable/burdensome explanations; weak validation; privacy/workflow constraints [175][151][188]. Predictive AI forecasts risks/outcomes; gaps/bias limit automation [254]. Generative AI makes summaries/docs/recommendations; hallucination/context/bias/privacy need review—assists, not decides [254][187]. Catalonia, 6 months: 89% satisfaction/21% adoption/85% adherence; not XAI-specific [254]. Functions, not rows; HRM-only/15-Jul-23 arXiv: contextual/preliminary [150][186].

Adjacent functions are not extra rows. Predictive AI remains a possible component function; this evidence establishes predictive-classification and bias/uncertainty context, not AI-SDM membership [189]. Generative AI can add natural-language/contextual responses and emerging decision support, but is an enabling layer—not a replacement for expertise; agentic variants can propagate errors or misstate dose/timing [144][138]. AI Transparency is a comparison property; AI Reasoning is communicable justification, with no direct health-AI validation here [149][216].

**XAI alone:** Explains model predictions for confidence, consent, challenge and compliance—not SDM; outputs include local/global attributions (LIME/SHAP), counterfactuals, trees and knowledge-limit disclosures [197][198][199]. It supports development/deployment/review and audience tailoring, but not patient personalization or shared workflow; clinicians remain accountable and AI has no independent authority. Explanations are partial/selective and face opacity, bias, privacy and performance trade-offs [198][199].

**AI-SDM:** Evidence supports a human-centric hybrid augmenting decisions with recommendations, counterfactual reasoning and personalised interventions for fair, trusted choices [256]; its public-health/disaster scope does not establish a complete healthcare SDM workflow, exhaustive models or detailed patient/clinician/transparency fields [256].

**Boundaries:** Traditional SDM is the patient–clinician process, not species-distribution modelling [232]. Predictive AI supplies risk scores/probabilities/classifications/forecasts for SDM; performance ≠ benefit, so uncertainty, bias, population shift and monitoring matter [68][81][267]. Generative AI supplies text, summaries, clinical proposals and education; hallucination/incompleteness require validation/review [40][80]. A Kenya trial (>9,600 patients; 16 clinics) improved decision quality, not short-term outcomes [66]. AI Reasoning supplies inference/justification, not authority; clinicians remain responsible [51][217][212]. Transparency is a property, not a row: disclosure/structural completeness ≠ truth/accountability [37][140][142].

Predictive AI forecasts/classifies; oncology models use EHR/imaging/lab/patient data to stratify risk; thresholds can trigger intervention; it augments clinicians, but subgroup/geography/time variation, bias and drift limit reliability [82]. Generative AI creates summaries, notes, explanations and tailored suggestions; candidate function, not confirmed AI-SDM component/row. Clinicians retain authority and verify outputs; hallucinations/errors, inconsistency, bias/privacy, opacity and over-reliance persist [112]. Generation differs from transparency/XAI/reasoning; retrieval/recommendation membership unresolved; retrieval changes alter recommendations [110][38]. GenAI education: critical engagement [84][250]

**Evidence retrieval/recommendation** is an unestablished AI-SDM candidate. A proposed, unimplemented system retrieves verified guidelines/studies, feeds reasoning, returns cited options—not directives—to clinicians for review, and logs sources, answers and an audit trail [52][119]. Agents may sequence extraction, retrieval, differential, verification and recommendation (HandRAG/MedRAG); function alone proves no clinical value [118][120]. Five Rights: right information/person/format/channel/workflow-time; source completeness, retrieval quality, privacy/bias/accountability, computation, limited validation and absent real-world impact constrain use [118][119][120].

Traditional Shared Decision-Making (SDM) resolves the human-care baseline by defining a non-AI partnership in which patients and clinicians exchange information, consider options and uncertainty, express preferences, and share responsibility for the healthcare decision [236][237].

Traditional SDM supports comparison with AI-SDM by supplying the process that AI is meant to assist: patients and clinicians exchange evidence, discuss options and preferences, deliberate through communication, and reach a jointly responsible decision [233][222].

Traditional SDM resolves baseline confusion by making the decision a human partnership: patient and clinician share information, consider options and uncertainty, elicit preferences, and reach a jointly responsible choice [236][237].

In healthcare, Traditional SDM is an iterative process that diagnoses the situation, signals when options exist, clarifies options and harms, deliberates about fit with patient preferences, and makes the decision with the patient [268].

Traditional SDM supplies the human-care context for AI-SDM: it moves from situation and option clarification through harms, benefits, and preference deliberation to a patient–clinician decision [268].

Traditional SDM is the human-care context for an AI-SDM introduction: patients and clinicians combine evidence, options, preferences, and clinical expertise in a jointly responsible decision [237][236].

AI-SDM’s core objective is to enhance SDM and person-centred care with AI as support rather than replacement, preserving clinical expertise, autonomy, and the human factor [260].

## 5. Concrete examples and what the evidence establishes

### Named applications and comparators

**Examples demonstrate different contributions.** The following cases distinguish illustrative designs, prototypes, clinical evaluations, and conventional decision aids. Keeping those categories separate helps explain what each example contributes without treating every tool as a validation of the same framework.

| Named example | Healthcare context | AI contribution | Evidence basis | Main decision-making lesson |
|---|---|---|---|---|
| Roche knee-replacement illustration [18] | Knee osteoarthritis | Proposed questioning and preference support | Patient-informed white paper | A desired activity may matter more than an initial treatment preference |
| Hao and colleagues’ i-SDM [19] | Older adult cancer care | Interactive treatment comparisons and AI-supported information | Interview and usability studies | Layered information can support patient–clinician discussion |
| Quartz [2] | Hypertension medication adherence | Text and chatbot-supported information collection | AHRQ prototype pilot | Between-visit information must reach the clinical workflow |
| PAIGE [2] | Patient portal communication | LLM clarification and patient-reviewed summaries | AHRQ prototype evaluation | Preserve patient wording and review before handoff |
| Custom breast-reconstruction GPT [29] | Initial immediate-reconstruction consultation | Generative preconsultation questions and answers | Single-center randomized trial, 20 women | Preparation can affect consultation experience and duration |
| AVITA [30] | Severe aortic stenosis | Conventional interactive decision aid, without an AI model | Prospective multisite pilot | Personalization and preference summaries do not require AI |
| Chest Pain Choice [31] | Low-risk possible acute coronary syndrome | Conventional quantitative risk tool and decision aid | Multicenter randomized trial, 898 adults | Personalized risk communication can support SDM without generative AI |

**The knee example identifies the mechanism.** Roche’s illustrative patient, Ms Müller, initially planned knee replacement but described mobility for gardening as her underlying goal when the doctor explored what mattered. The lesson is not that AI should choose an alternative treatment. It is that a tool can help surface a goal that the clinician and patient then use to reconsider options together. [18]

**The cancer prototype addresses presentation.** Hao and colleagues conducted an initial study with 12 interviews—seven older adults with chronic diseases and five clinicians—and a second study involving 25 usability interviews with older adult cancer survivors and cancer clinicians or providers. Five of the seven patients in the initial study volunteered that visual aids would help them process information. This supports the importance of understandable presentation and user involvement in design. [19]

**The communication pilots address handoffs.** Quartz and PAIGE illustrate how AI can collect information outside the consultation rather than directly select treatment. Their evaluations identified needs for better workflow integration, adequate response times, more personalized replies, preservation of patient language, and integration of clinical-record context. These findings locate the challenge in the whole interaction, not just the model’s ability to produce text. [2]

### The wider evidence base

**Early literature emphasized predictions and recommendations.** Abbasgholizadeh Rahimi and colleagues’ 2022 scoping review included six peer-reviewed publications after a search through May 2021. All six used machine learning and provided recommendations or predictions. None involved patients or healthcare providers in design and development; three involved providers in validation, and one involved both patients and providers in clinical validation. [32]

**That finding matters for design.** A system can perform a technically relevant task yet fail to fit the needs of the people expected to use it. If patient values are central to the intended decision, excluding patients from development creates a risk that the tool will optimize information delivery without supporting meaningful participation. The review’s concern was therefore not simply the number of studies, but what their development and evaluation actually included.

**Later reviews describe a broader field.** Hassan and colleagues’ 2024 review included 26 articles on AI-enabled decision aids, covering screening and prevention, prognosis, and treatment. Its definition required discussion or joint decision-making rather than tools used separately by patients or clinicians. Reported user experiences included understandable interfaces and a sense of ownership, alongside concerns about outdated information, bias, privacy, anxiety, and digital exclusion. [17]

**The 2026 review is in scope.** Giorgetti, Giorgetti, Pelotti, and Contissa’s *AI and shared decision-making: a systematic review* was first published online on March 11, 2026, according to its Crossmark history. Its literature window extended through June 2025, placing it within this report’s September 13, 2026 evidence horizon. [33]

**Its study mix remains revealing.** The review’s detailed results identify 78 included studies, with 30 conceptual-paper classifications, 20 observational reports, 18 reviews, six experimental studies, and six protocols. Two papers occupied more than one article-type category. These counts show substantial discussion and development activity, while distinguishing experimental evaluation from conceptual, observational, and planned work. [34]

**Growth does not establish clinical superiority.** The six-study 2022 review and the later 78-study review used different dates and inclusion criteria, so their totals should not be interpreted as a direct growth rate for clinically validated AI-SDM systems. The later review itself describes broader criteria. Neither a large literature count nor a persuasive conceptual model establishes that AI-SDM outperforms high-quality traditional SDM across specialties.

**The strongest judgment is application-specific.** The evidence supports examining particular tasks—such as preparation, information comprehension, preference elicitation, and consultation workflow—rather than assuming a universal effect from the AI-SDM label. A condition-specific trial can strengthen a claim about that tool and encounter while leaving broader claims dependent on other settings and outcomes.

### A randomized example: generative preparation for breast reconstruction

**A small trial provides concrete results.** A single-institution randomized trial published online on December 19, 2025 enrolled 20 women aged 18–80 seeking an initial consultation for immediate breast reconstruction. Ten used a custom GPT before the consultation and ten received the control condition; the reconstructive surgeon was blinded. The preconsultation interaction was limited to a maximum of 10 minutes. [29]

| Immediate consultation measure | Custom GPT group | Control group | Interpretation |
|---|---|---|---|
| SURE decisional-conflict screening score | 3.9 points | 3.1 points | Higher score indicated less conflict; reported P = 0.03 |
| Mean consultation duration | 21.7 minutes | 28.4 minutes | Shorter consultation; reported P = 0.02 |
| Shared-decision-making top-box responses | 10/10 patients, 100% | 8/10 patients, 80% | Favorable patient-reported responses in this sample |

**The tool supported an existing consultation.** It was developed with iterative surgeon feedback, reflected institutional standards and common complications, and aimed for approximately sixth- to eighth-grade reading level. Users spent an average of 6.79 minutes asking an average of 6.5 questions. The tool did not replace the patient–surgeon interaction. [29]

**The likely mechanism was preparation.** Recovery, reconstruction options, and complications were prominent question topics. Addressing these before the visit could allow the surgeon to spend less time establishing background understanding and more time addressing the patient’s particular concerns. The authors also note that feeling prepared may contribute to the observed benefit, rather than every improvement being uniquely attributable to language generation.

**Consultation savings need careful interpretation.** The observed difference was 6.7 minutes, calculated as 28.4 − 21.7 minutes. An estimated two-component patient interaction time for the GPT arm is 28.49 minutes, calculated as 6.79 minutes of tool use + 21.7 minutes of consultation. Comparing that with 28.4 minutes of control consultation counts tool-plus-consultation time on one side and consultation time alone on the other; it illustrates redistribution of time, not proof of reduced end-to-end patient time. [29]

**The outcome claims should stay specific.** This trial supports an early claim about previsit education and immediate consultation experience for one type of reconstructive decision. Those findings are different from demonstrating a better long-term surgical outcome, durable value alignment, or superiority over an equally well-designed non-generative preparation tool. The authors also identify the small sample and absence of formal GPT benchmarking as important features of the study.

### Conventional decision aids provide important counterexamples

**AI is not necessary for personalization.** AVITA—Aortic Valve Improved Treatment Approaches—is an interactive online decision aid for severe aortic stenosis. It presents options, elicits goals and preferred decision-making roles, and generates a patient-specific summary for clinicians without making a treatment recommendation. Its design demonstrates that structured preference support and individualized summaries can be achieved without an AI model. [30]

**Its workflow resembles proposed AI-SDM.** Patients complete AVITA before the encounter, and clinicians review the summary before or during the consultation. It was designed for 10–20 minutes of patient use and 2–5 minutes of clinician review. The relevant innovation is the timely transfer of patient priorities into the treatment conversation; AI is one possible way to support that transfer, not its defining prerequisite. [30]

**Preferences changed as understanding developed.** The prospective multisite pilot involved 30 patients and 14 clinicians across 28 encounters. Among the 25 patients who responded at all three assessment points, 15—60%—changed their treatment preference at least once. This is consistent with the idea that preferences can develop through information and deliberation rather than existing as fixed data waiting to be collected. [30]

**Satisfaction did not guarantee complete SDM.** All clinicians self-reported practicing SDM in all 28 encounters. However, none of the 22 patient-evaluated encounters met all the study’s SDM process criteria. Patients often reported omissions involving discussion of treatment disadvantages or explicit questions about which treatment they preferred, despite rating clinicians’ general communication highly. [30]

**This is a decisive counterexample.** A well-received, personalized tool can coexist with incomplete shared decision-making. The implication for AI-SDM is direct: usability, satisfaction, and confidence are important, but they should not stand in for evidence that patients understood alternatives and influenced the choice. Adding a conversational model would not automatically close those gaps.

**Conventional risk communication also has trial evidence.** Hess and colleagues’ 2016 Chest Pain Choice trial randomized 898 adults—451 to the decision aid and 447 to usual care—across six US emergency departments, with 361 emergency clinicians participating. The workflow combined a quantitative tool for personalized 45-day acute coronary syndrome risk with an encounter-based discussion of management options and patient preferences. [31]

**The trial changed knowledge and choices.** Patients receiving the decision aid answered an average of 4.2 knowledge questions correctly versus 3.6 in usual care. Patient-involvement scores were 18.3 versus 7.9, and admission for cardiac testing occurred in 37% versus 52%—an absolute difference of 15 percentage points. The study reported no intervention-related major adverse cardiac events for its 30-day safety outcome. [31]

**The setting clarifies emergency-care boundaries.** This was a decision for low-risk possible acute coronary syndrome where discussion of alternatives was feasible, not an unexpected emergency requiring immediate life-saving intervention. It therefore shows why “emergency department” is not synonymous with “no opportunity for SDM.” The nature of the decision and the time available are more informative than the department’s name.

**The evidence favors task-level judgments.** Concrete tools can improve parts of decision-making, but whether AI adds value must be judged against the same functions already achievable through good clinical communication and conventional decision aids.

## 6. Risks, safeguards, and the resulting judgment

### Reliable content and faithful explanations

**Generated errors can redirect the conversation.** A chatbot may give incorrect, outdated, or poorly contextualized information; it may also omit an option or describe a consequence misleadingly. In AI-SDM, such errors can affect which questions the patient asks and how they evaluate treatment before the clinician sees them. AHRQ’s recommendation for human review addresses this pathway, not merely the final wording of the answer. [2]

**Explanatory quality needs independent assessment.** The AMA’s 2026 report stresses that explainability should not substitute for safety and efficacy evidence, and that explanations should be evaluated rather than accepted solely on developer claims. An attractive interface or a coherent narrative is not enough. The relevant question is whether the explanation is faithful, understandable, and useful for its intended clinical purpose. [24]

**Source grounding supports accountable communication.** Patients and clinicians should be able to distinguish an established clinical statement, a model prediction, and generated explanatory wording. Keeping those origins visible makes errors easier to identify and questions easier to direct. It also helps prevent a generated statement from acquiring the authority of a clinician-reviewed recommendation merely through polished presentation.

### Bias, privacy, and access

**Personalization can reproduce population bias.** Training data may represent some demographic or clinical groups poorly. A system can then generate individualized-looking output whose reliability differs across patients. For preference models, the problem is especially sensitive: patterns drawn from online or population data may misrepresent people whose experiences or values are less digitally visible. [26]

**A preference profile can become paternalistic.** If an inferred preference is treated as a fact about what the patient ought to want, the system may narrow rather than expand their participation. Giorgetti and colleagues identify lack of attention to patient preferences as a central risk, including a “computer knows best” pattern. The appropriate response is to make the relevant priorities explicit and open to acceptance, rejection, or revision. [34]

**Privacy extends to conversational information.** Patient-facing AI may collect concerns, symptoms, priorities, and information about daily life as well as conventional clinical data. AHRQ’s patient and caregiver work highlights the importance of explaining who can access the data, how they are stored and shared, and what evidence informs the tool’s outputs. A friendly conversational style does not remove these governance responsibilities. [2]

**Access determines who receives the benefit.** Digital literacy, health literacy, language, disability, and access to suitable technology can affect participation. The 2024 decision-aid review identifies digital exclusion as a concern, while AHRQ’s pilot findings emphasize testing with people who have limited digital or health literacy. An AI-supported pathway should therefore preserve workable routes for people who cannot or do not wish to use its digital interface. [17][2]

### Workflow burden and appropriate reliance

**Explanations can increase confidence without discrimination.** In the CORONET user study, 23 healthcare professionals considered 10 artificial patient cases. Although 21 of 23 considered explanations of individual recommendations important, adding explanations did not significantly improve satisfaction, trust, or understanding. The study also illustrated overreliance when a model focused on COVID-19 severity failed to account for oncological emergencies. [12]

**Persuasiveness can amplify incorrect advice.** A preprint by Khanna, Wang, Wei, and Xue examined 3,855 diagnostic decisions by 257 clinical-year medical students. Explanations increased diagnostic accuracy by 4.3 percentage points when the AI advice was correct but decreased it by 4.6 percentage points when the advice was incorrect. This is not an AI-SDM patient-outcome study, but it directly illustrates why a persuasive rationale need not improve detection of bad advice. [35]

**More information can also consume attention.** A clinician may need time to inspect an explanation, verify a summary, resolve discrepancies, and translate the result for the patient. A 2025 ethical analysis of hypothetical time-sensitive surgical use argues that this extra work can undermine the purpose of decision support when explanations cannot be processed within the available time. The value of explanation therefore depends partly on workflow and urgency. [36]

**Integration determines whether support is usable.** The AMIA/BIDMC consensus recommends embedding AI-CDS into existing clinical information systems, records, and patient portals. A technically capable model that produces information in a disconnected application may create another handoff or documentation task. AHRQ’s Quartz and PAIGE evaluations similarly show that response time, complete information, and workflow fit are central to practical usefulness. [6]

**The objective is appropriate reliance.** Better healthcare AI should help users identify when an output is relevant, when it deserves challenge, and when human information changes the conclusion. Maximizing trust, satisfaction, or acceptance alone would reward some misleading systems. For AI-SDM, the more consequential outcomes are informed understanding, meaningful patient involvement, a plan reflecting the patient’s priorities, and safe clinical use.

### How to interpret the overall comparison

**Evidence should match the claimed benefit.** A usability study can support a claim about usability; a consultation trial can support a claim about that encounter; a predictive validation study can support a claim about the estimate tested. Broader claims about patient outcomes, equity, or superiority over traditional SDM depend on evidence addressing those outcomes and comparators. The AMA’s 2026 synthesis characterizes broad patient-outcome evidence for AI decision support as mixed. [24]

**The conclusion changes with demonstrated performance.** AI-SDM becomes more compelling when a specific implementation improves understanding or decision quality, preserves patient influence, fits the workflow, and performs appropriately across the patients it serves. It becomes less compelling when generated errors, biased estimates, burdensome interfaces, or excessive reliance undermine those same goals. The relevant comparison is with a well-supported human decision process, not with an artificially impersonal version of traditional care.

**How to read the evidence.** This report’s horizon is September 13, 2026. Terminology tables compare functions, not clinical efficacy rankings; the component pattern and workflow are cross-source syntheses. Framework-specific authorship and mandatory-module claims depend on an original specification explicitly establishing those features. Study counts use detailed results, including 78 studies in Giorgetti and colleagues’ review; article-type categories overlap. Scores, times, and proportions retain their study-specific meanings and denominators. The 6.7-minute consultation difference is calculated, and the 28.49-minute combined interaction time is an estimate from reported group means.

**The decisive test is partnership.** AI-SDM is best understood as shared decision-making strengthened by useful AI support—not as XAI renamed, a chatbot making treatment choices, or a claim that visible reasoning makes a model clinically trustworthy. Its success lies in helping patients and clinicians reach better-informed, personally meaningful decisions while keeping evidence, responsibility, and patient choice clear.

## References

[1] <https://www.gov.uk/government/publications/machine-learning-medical-devices-transparency-principles/transparency-for-machine-learning-enabled-medical-devices-guiding-principles> Joint transparency principles, 2024; Joint transparency principles; Audience-sensitive transparency guidance; Transparency and intended workflow
[2] <https://digital.ahrq.gov/ahrq-funded-projects/clinical-decision-support-innovation-collaborative-cdsic/viewpoints/exploring-how-artificial-intelligence-enhance-patient-centered-clinical-decision-support> AHRQ patient-centered AI viewpoint; AHRQ’s predictive–generative distinction; AHRQ’s account of generative AI; PAIGE’s patient-reviewed communication workflow;…
[3] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9931364/> Healthcare XAI analysis; Global and local explainability; Correlation and explanation fidelity
[4] <https://zitniklab.hms.harvard.edu/publications/papers/XAIPerspective22.pdf> Combi and colleagues’ medical XAI perspective, 2022; Reasoning mechanisms and data–result relationships
[5] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9189302/> Healthcare transparency as a multilayered system
[6] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11491642/> Labkoff and colleagues’ responsible AI-CDS recommendations; Use-case dependency and validation; AMIA/BIDMC documentation recommendations; Clinical integration…
[7] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9527344/> Semantic transparency in clinical decision support
[8] <https://www.mdpi.com/2227-9709/12/4/119> Examples and categories of clinical XAI
[9] <https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/artificial-intelligence/explaining-decisions-made-with-artificial-intelligence/annexe-1-example-of-building-and-presenting-an-explanation-of-a-cancer-diagnosis/> ICO cancer-diagnosis example; ICO’s layered explanation workflow
[10] <https://www.nature.com/articles/s44222-025-00363-w> Medical AI explanation techniques
[11] <https://doi.org/10.1017/s0963180123000294> Explanation versus validation in evidence-based medicine; Clinical responsibility and practical reasoning; Practical reasoning in evidence-based medicine; Shar…
[12] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7618637/> Recommendation, uncertainty, and explanation in clinical user studies; CORONET explanation study
[13] <https://link.springer.com/article/10.1007/s10676-022-09632-3> Audience- and purpose-relative explainability
[14] <https://iris.who.int/server/api/core/bitstreams/e9e62c65-6045-481e-bd04-20e206bc5039/content> WHO guidance on large multimodal models
[15] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10912120/> AI and the need for justification to the patient
[16] <https://www.ahrq.gov/sdm/about/index.html> AHRQ’s SDM definition; AHRQ SDM guidance; AHRQ’s account of collaborative healthcare decisions; AHRQ SDM definition
[17] <https://www.nature.com/articles/s41746-024-01326-y> AI-enabled decision-aid review, 2024; Hassan and colleagues’ decision-aid review; AI-enabled decision-aid review; Systematic review of users’ perspectives; Dec…
[18] <https://assets.roche.com/f/167129/x/28b5572017/whitepaper_ai_patient_eng.pdf> Roche patient-centered AI white paper; Roche white paper; Roche’s preference-sensitive knee example; Roche’s illustrative case
[19] <https://dl.acm.org/doi/full/10.1145/3613904.3642353> Hao and colleagues’ i-SDM prototype; Hao and colleagues; Hao’s i-SDM prototype; Hao and colleagues’ interview and usability findings
[20] <https://doi.org/10.1145/3678884.3681841> Cancer-treatment i-SDM framework record
[21] <https://doi.org/10.1136/bmjebm-2024-sdc.88> Giguère and colleagues’ environmental scan
[22] <https://www.nice.org.uk/guidance/ng197/resources/shared-decision-making-pdf-66142087186885/> NICE guideline NG197; NICE recommendations on personalized communication; NICE documentation guidance; NICE guideline scope; NICE NG197; Personalization in ord…
[23] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7706019/> Amann and colleagues’ personalized conversation-aid proposal; AI-supported personalized conversation aids; Amann and colleagues’ multidisciplinary XAI analysis…
[24] <https://www.ama-assn.org/system/files/a26-handbook-refcomm-e.pdf> AMA Council on Science and Public Health Report 7-A-26; AMA evidence and transparency report; AMA Report 7-A-26
[25] <https://doi.org/10.1186/s12911-025-02945-5> Clinical preference-model applications
[26] <https://www.nature.com/articles/s41746-025-02156-2> AI measurement and prediction of patient preferences; Patient preference measurement and prediction review; Yang and colleagues’ preference review
[27] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5683042/> Elwyn and colleagues, 2017; The revised three-talk model; Elwyn’s three-talk model
[28] <https://www.fda.gov/media/109618/download> FDA Clinical Decision Support Software guidance
[29] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12962575/> Breast-reconstruction consultation trial; Trial design and patient interaction; Reported timing inputs
[30] <https://journals.plos.org/plosone/article?id=10.1371%2Fjournal.pone.0302378> Coylewright and colleagues, 2024; AVITA intervention description; AVITA preference findings; Patient–clinician differences in SDM assessment
[31] <https://www.bmj.com/content/355/bmj.i6165> Hess and colleagues’ pragmatic randomized trial; Chest Pain Choice results
[32] <https://medinform.jmir.org/2022/8/e36199/> Application of Artificial Intelligence in Shared Decision Making: Scoping Review
[33] <https://crossmark.crossref.org/dialog/?doi=10.1007%2Fs00146-026-02955-5> Publication history
[34] <https://link.springer.com/article/10.1007/s00146-026-02955-5> Giorgetti and colleagues’ detailed results; AI, values, and digital paternalism
[35] <https://www.chapman.edu/research/institutes-and-centers/economic-science-institute/_files/ifree-papers-and-photos/ai-health-belief.pdf> When Medical AI Explanations Help and When They Harm
[36] <https://jme.bmj.com/content/early/2024/09/18/jme-2024-110046> XAI in time-sensitive care
[37] <https://doi.org/10.20944/preprints202604.0956.v1>
[38] <https://www.preprints.org/manuscript/202606.2079>
[39] <https://build.fhir.org/ig/HL7/aitransparency-ig/en/>
[40] <https://doi.org/10.1016/j.jbi.2024.104640>
[41] <https://www.avomd.com/education/ai-automation-in-healthcare-transforming-u-s-health-system-workflows-and-patient-care>
[42] <https://arxiv.org/html/2602.24176v1>
[43] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12427955/>
[44] <https://link.springer.com/article/10.1007/s10648-026-10202-y>
[45] <https://doi.org/10.1093/pnasnexus/pgag030>
[46] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7727333/>
[47] <https://doi.org/10.64136/asge3694>
[48] <https://seas.harvard.edu/news/harvard-researchers-part-nsf-ai-institute-societal-decision-making>
[49] <https://link.springer.com/article/10.1007/s00146-026-02955-5>
[50] <https://digital.ahrq.gov/sites/default/files/IAS%20Topic%20Highlight%20AI%20and%20PC%20CDS_508%20Compliant.pdf>
[51] <https://www.ibm.com/think/topics/ai-reasoning>
[52] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12913532/>
[53] <https://www.linkedin.com/company/ai-sdm>
[54] <https://health.ec.europa.eu/ehealth-digital-health-and-care/artificial-intelligence-healthcare_en>
[55] <https://doi.org/10.1137/1.9781611977653.ch65>
[56] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12525484/>
[57] <https://www.ama-assn.org/system/files/ai-tool-evaluation-guide.pdf>
[58] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8654471/>
[59] <https://www.annualreviews.org/content/journals/10.1146/annurev-biodatasci-122220-110053>
[60] <https://doi.org/10.1007/978-3-031-75771-6_19>
[61] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10960211/>
[62] <https://www.sph.umn.edu/news/new-study-analyzes-hospitals-use-of-ai-assisted-predictive-tools-for-accuracy-and-biases/>
[63] <https://www.confluent.io/blog/predictive-analytics-healthcare/>
[64] <https://www.michiganmedicine.org/health-lab/whats-impact-predictive-ai-health-care-setting>
[65] <https://www.xsolis.com/blog/types-of-ai-in-healthcare/>
[66] <https://www.clinicaltrialvanguard.com/article/intel-brief/ai-clinical-decision-support-is-outrunning-its-own-evidence-base-what-trial-operators-need-to-know-now/>
[67] <https://doi.org/10.20944/preprints202610.0849.v1>
[68] <https://healthit.gov/data/data-briefs/hospital-trends-use-evaluation-and-governance-predictive-ai-2023-2024/>
[69] <https://ep.jhu.edu/news/ai-in-healthcare-applications-and-impact/>
[70] <https://doi.org/10.1007/978-3-031-75771-6_23>
[71] <https://www.microsoft.com/en-us/ai/ai-101/generative-ai-vs-other-types-of-ai>
[72] <https://sloanreview.mit.edu/article/when-to-use-genai-versus-predictive-ai/>
[73] <https://iianalytics.com/community/blog/beyond-the-hype-when-generative-ai-isnt-always-the-answer>
[74] <https://docs.cloud.google.com/docs/ai-ml/generative-ai/generative-ai-or-traditional-ai>
[75] <https://www.clinicaltrialvanguard.com/article/article-deep-dive/ai-clinical-decision-support-is-everywhere-the-evidence-base-is-not/>
[76] <https://pmc.ncbi.nlm.nih.gov/articles/PMC13004926/>
[77] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11612599/>
[78] <https://www.ibm.com/think/topics/generative-ai-vs-predictive-ai-whats-the-difference>
[79] <https://arxiv.org/html/2506.17347v2>
[80] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10941464/>
[81] <https://doi.org/10.1145/3830235>
[82] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11170282/>
[83] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11739231/>
[84] <http://arxiv.org/abs/2504.16770v1>
[85] <http://arxiv.org/abs/2501.02842v1>
[86] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11459854/>
[87] <https://www.has-sante.fr/upload/docs/application/pdf/2026-01/initial_key_guiding_principles_for_the_use_of_generative_ai_in_healthcare.pdf>
[88] <https://www.ncbi.nlm.nih.gov/books/NBK615593/>
[89] <https://citeability.ai/insights/dependable-ai-systems-and-information-governance/what-an-ai-evidence-audit-trail-should-contain>
[90] <https://www.annualreviews.org/content/journals/10.1146/annurev-biodatasci-103123-094756>
[91] <https://pubmed.ncbi.nlm.nih.gov/40533396/>
[92] <https://doi.org/10.1016/j.caeai.2026.100654>
[93] <http://arxiv.org/abs/2603.16204v1>
[94] <http://arxiv.org/abs/2504.15647v2>
[95] <https://doi.org/10.23880/jqhe-16000361>
[96] <https://doi.org/10.1007/978-3-031-75771-6_21>
[97] <https://iris.who.int/server/api/core/bitstreams/e9e62c65-6045-481e-bd04-20e206bc5039/content>
[98] <https://doi.org/10.1007/978-3-031-75771-6_13>
[99] <https://doi.org/10.20944/preprints202610.1326.v1>
[100] <https://aimultiple.com/generative-ai-healthcare>
[101] <https://www.gao.gov/products/gao-24-107634>
[102] <https://about.ebsco.com/blogs/health-notes/ai-clinical-decision-support-what-responsible-evidence-based-solutions-should>
[103] <https://cdh.stanford.edu/sites/g/files/sbiybj29486/files/media/file/stanford_scdh_genaiwhitepaper_v16_compressed.pdf>
[104] <https://www.effectivesoft.com/blog/generative-ai-in-healthcare.html>
[105] <https://link.springer.com/article/10.1007/s11606-024-09102-0>
[106] <https://digital.ahrq.gov/ahrq-funded-projects/clinical-decision-support-innovation-collaborative-cdsic>
[107] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11861482/>
[108] <https://www.thelancet.com/journals/lanam/article/PIIS2667-193X%2825%2900291-1/fulltext>
[109] <https://digital.ahrq.gov/sites/default/files/OY1_FINAL%20TPC%20Patient%20Perspectives%20Generative%20AI.pdf>
[110] <https://www.mja.com.au/journal/2025/223/11/using-generative-artificial-intelligence-clinical-practice-narrative-review-and>
[111] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12479492/>
[112] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12683314/>
[113] <https://www.ncbi.nlm.nih.gov/books/NBK615592/>
[114] <https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.300-1.ipd.pdf>
[115] <https://dl.acm.org/doi/10.1145/3777577.3777598>
[116] <https://www.medrxiv.org/content/10.1101/2025.10.17.25338266v1.full.pdf>
[117] <https://doi.org/10.2196/64364>
[118] <https://www.mdpi.com/2306-5354/13/10/1175>
[119] <https://evidencemd.ai/best-clinical-decision-support-ai>
[120] <https://pdfs.semanticscholar.org/eeab/620e9d8c8d0c4215b2d39bcced9fc4d9440c.pdf>
[121] <https://digital.ahrq.gov/sites/default/files/Final%20IAS%20PC%20CDS%20Case%20Studies%20Report_2.pdf>
[122] <https://doi.org/10.1093/jamia/ocae138>
[123] <https://digital.ahrq.gov/sites/default/files/IAS_Key%20Factors%20and%20Considerations%20for%20Assessing%20the%20Value%20of%20PC%20CDS.pdf>
[124] <https://www.sciopen.com/article/10.12290/xhyxzz.2023-0209>
[125] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11258405/>
[126] <https://www.sciencedirect.com/org/science/article/pii/S1438887126002992>
[127] <https://www.norc.org/research/library/patient-centered-decision-support-moving-from-innovation-to-impact.html>
[128] <https://www.ncbi.nlm.nih.gov/books/NBK618247/>
[129] <https://www.ncbi.nlm.nih.gov/books/NBK617815/>
[130] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10436138/>
[131] <https://digital.ahrq.gov/sites/default/files/SRF_Taxonomy%20of%20PC%20CDS%20Override%20Recommendations_508_0.pdf>
[132] <https://digital.ahrq.gov/sites/default/files/CDSiC%20Factsheet_508.pdf>
[133] <https://www.eurekalert.org/news-releases/988275>
[134] <https://doi.org/10.1136/bmjebm-2024-sdc.88>
[135] <https://www.youtube.com/watch?v=rbULOSu6Usc>
[136] <https://medinform.jmir.org/2022/8/e36199>
[137] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9399841/>
[138] <https://sheffield.ac.uk/media/118146/download?attachment=>
[139] <https://censinet.com/perspectives/beyond-black-box-transparency-strategies-healthcare-ai>
[140] <https://lifesciences.mofo.com/topics/ai-transparency-in-healthcare-navigating-a-changing-regulatory-landscape>
[141] <https://ace-usa.org/blog/research/research-technology/ai-transparency-in-healthcare-what-patients-need-to-know/>
[142] <https://www.emj.life/downloads/publications/MWP04-AIEDSM-AI-Evidence-Data-Science-Methodology-v1.0.pdf>
[143] <https://ora.ox.ac.uk/objects/uuid:cfb52ef7-67c3-4b9e-9fea-4a8fcca3dd4f/files/rjd472z84g>
[144] <https://doi.org/10.3390/ai7080296>
[145] <https://zortify.com/xai/>
[146] <https://shorensteincenter.org/wp-content/uploads/2024/05/CleAR_KChmielinski_FINAL.pdf>
[147] <https://doi.org/10.1007/s43681-025-00661-4>
[148] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10951032/>
[149] <https://link.springer.com/article/10.1007/s13347-025-01009-w>
[150] <https://doi.org/10.4018/979-8-3373-1737-3.ch001>
[151] <https://pmc.ncbi.nlm.nih.gov/articles/PMC13097491/>
[152] <https://pmc.ncbi.nlm.nih.gov/articles/PMC13079713/>
[153] <https://www.mdpi.com/2227-9709/12/4/119>
[154] <https://dr.lib.iastate.edu/bitstreams/f7b0f5bf-56a6-484e-9c51-9d8adc2a8884/download>
[155] <https://scholars.cityu.edu.hk/en/publications/interactive-xai-for-shared-decision-making-in-healthcare-in-afric/>
[156] <https://www.nature.com/articles/s44222-025-00363-w>
[157] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9122967/>
[158] <https://link.springer.com/article/10.1007/s10676-022-09632-3>
[159] <https://doi.org/10.1016/j.jbi.2020.103655>
[160] <https://www.mdpi.com/2076-3417/13/19/10778>
[161] <https://link.springer.com/article/10.1186/s12911-021-01703-7>
[162] <https://www.mdpi.com/2673-2688/4/3/34>
[163] <https://zitniklab.hms.harvard.edu/publications/papers/XAIPerspective22.pdf>
[164] <https://link.springer.com/article/10.1007/s10676-022-09649-8>
[165] <https://www.isjtrend.com/article_243223_d6bec260c9a5f76d2225e6569695f629.pdf>
[166] <https://doi.org/10.1177/20552076221074488>
[167] <https://arxiv.org/pdf/2007.15911>
[168] <https://www.frontiersin.org/journals/medicine/articles/10.3389/fmed.2025.1545409/full>
[169] <https://doi.org/10.1007/s10677-023-10390-4>
[170] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11958387/>
[171] <https://doi.org/10.1016/j.artmed.2023.102616>
[172] <https://doi.org/10.1177/20552076241272657>
[173] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9607788/>
[174] <https://www.atscale.com/glossary/explainable-ai-xai/>
[175] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10689048/>
[176] <https://witness.ai/blog/ai-explainability/>
[177] <https://doi.org/10.66224/ist.202603.12.02>
[178] <https://scholarlycommons.law.emory.edu/cgi/viewcontent.cgi?article=1564&context=elj>
[179] <https://doi.org/10.1038/s41746-025-01764-2>
[180] <https://doi.org/10.1371/journal.pdig.0000016>
[181] <https://cispa.de/elsa/2024/ELSA%20%20D3.4%20Short%20Report.pdf>
[182] <https://link.springer.com/article/10.1007/s42452-025-08176-7>
[183] <https://journals.plos.org/digitalhealth/article?id=10.1371%2Fjournal.pdig.0001417>
[184] <https://openjdm.github.io/jdm_and_ai.html>
[185] <http://arxiv.org/abs/2505.09862v3>
[186] <http://arxiv.org/abs/2307.11765v1>
[187] <https://www.annualreviews.org/content/journals/10.1146/annurev-biodatasci-103123-095332>
[188] <https://doi.org/10.1016/j.surg.2023.03.019>
[189] <https://www.frontiersin.org/journals/artificial-intelligence/articles/10.3389/frai.2020.507973/full>
[190] <https://www.mdpi.com/2079-9292/13/14/2842>
[191] <https://ojs.aaai.org/index.php/AIES/article/download/31648/33815>
[192] <https://www.johnsnowlabs.com/building-trustworthy-health-ai-systems-through-transparency-measures/>
[193] <https://doi.org/10.4018/979-8-3373-8904-2.ch008>
[194] <https://doi.org/10.1093/jamia/ocac006>
[195] <https://doi.org/10.1002/dad2.70236>
[196] <https://doi.org/10.1007/s10676-024-09754-w>
[197] <https://dl.acm.org/doi/full/10.1145/3561048>
[198] <https://royalsocietypublishing.org/rsta/article/379/2207/20200363/111914/Artificial-intelligence-explainability-the>
[199] <https://doi.org/10.6028/nist.ir.8312>
[200] <https://doi.org/10.1038/s41746-023-00992-8>
[201] <https://doi.org/10.1145/3643834.3660697>
[202] <https://www.frontiersin.org/journals/radiology/articles/10.3389/fradi.2025.1627169/full>
[203] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11391805/>
[204] <https://doi.org/10.70594/brain/16.4/26>
[205] <https://doi.org/10.1038/s41746-021-00549-7>
[206] <https://doi.org/10.3390/bioengineering12040375>
[207] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9189302/>
[208] <https://www.mdpi.com/2673-7426/5/3/37>
[209] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7706019/>
[210] <https://virtualitics.com/the-4-key-principles-of-explainable-ai-applications/>
[211] <https://kontakt.io/blog/glossary-of-terms-defining-artificial-intelligence-in-healthcare/>
[212] <https://kclpure.kcl.ac.uk/portal/en/publications/6c47c260-3059-46ae-a63e-0962e4185382>
[213] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11392082/>
[214] <https://doi.org/10.34190/icair.5.1.4309>
[215] <https://journals.plos.org/digitalhealth/article?id=10.1371%2Fjournal.pdig.0001310>
[216] <https://link.springer.com/article/10.1007/s43681-025-00668-x>
[217] <https://www.akingump.com/en/insights/alerts/artificial-intelligence-in-clinical-decision-making-regulatory-roadmap-and-reimbursement-strategies>
[218] <https://arxiv.org/html/2601.22338v1>
[219] <https://www.frontiersin.org/journals/digital-health/articles/10.3389/fdgth.2025.1697825/full>
[220] <https://doi.org/10.1007/s12312-026-01572-z>
[221] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11192055/>
[222] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11404645/>
[223] <https://doi.org/10.1109/ecoc.2017.8346124>
[224] <https://yuexinghao.github.io/Yuexing-Hao/assets/files/papers/CHI%2024%27.pdf>
[225] <https://doi.org/10.1177/0272989x241286880>
[226] <https://doi.org/10.1155/2023/9803293>
[227] <https://doi.org/10.3388/jspaci.39.84>
[228] <https://doi.org/10.61686/zxixy51912>
[229] <https://doi.org/10.3990/1.9789036543897>
[230] <https://doi.org/10.33612/diss.232457161>
[231] <https://doi.org/10.1017/9781009181549.006>
[232] <https://doi.org/10.30707/etd2022.20230207065834798728.999983>
[233] <https://mghdecisionsciences.org/about-us-home/shared-decision-making/>
[234] <https://www.nice.org.uk/guidance/ng197/resources/shared-decision-making-pdf-66142087186885/>
[235] <https://www.ahrq.gov/health-literacy/professional-training/shared-decision/tool/resource-8.html>
[236] <https://www.ahajournals.org/doi/10.1161/CIR.0000000000001162>
[237] <https://pmc.ncbi.nlm.nih.gov/articles/PMC4788386/>
[238] <https://doi.org/10.12788/jfp.0536>
[239] <https://doi.org/10.1016/j.jacadv.2024.100981>
[240] <https://doi.org/10.1136/bmjebm-2023-112374>
[241] <https://doi.org/10.1145/3678884.3681841>
[242] <https://pmc.ncbi.nlm.nih.gov/articles/PMC3445676/>
[243] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12686322/>
[244] <https://www.sciencedirect.com/org/science/article/pii/S2291969422001971>
[245] <https://algosoc.org/research/effective-ai-based-shared-decision-making-in-healthcare>
[246] <https://www.jclinepi.com/cms/10.1016/j.jclinepi.2025.111708/attachment/5eacfc2a-db41-4148-8ae9-238b4382cec4/mmc6.pdf>
[247] <https://relationalagents.com/publication/2020/zessie-thesis/ZessieThesis.pdf>
[248] <https://arcadia.io/resources/ai-tools-in-healthcare/>
[249] <https://www.yalemedicine.org/news/generative-ai-artificial-intelligence-for-health-info>
[250] <https://www.youtube.com/watch?v=eLAq8yzvu8Q>
[251] <https://doi.org/10.3390/jcm14176169>
[252] <https://nam.edu/perspectives/shared-decision-making-strategies-for-best-care-patient-decision-aids/>
[253] <https://www.jmir.org/2026/1/e92518/PDF>
[254] <https://www.ncbi.nlm.nih.gov/books/NBK621838/>
[255] <https://doi.org/10.2196/75851>
[256] <https://www.cmu.edu/ai-sdm/index.html>
[257] <https://www.cmu.edu/ai-sdm/>
[258] <https://www.youtube.com/channel/UCkI4QzpHgVABudTIK44IILw>
[259] <https://www.cmu.edu/ai-sdm/research/index.html>
[260] <http://urn.kb.se/resolve?urn=urn%3Anbn%3Ase%3Ahh%3Adiva-55599>
[261] <https://www.nature.com/articles/s41746-026-02587-5>
[262] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10879008/>
[263] <https://doi.org/10.1515/med-2025-1232>
[264] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12413788/>
[265] <https://www.frontiersin.org/journals/public-health/articles/10.3389/fpubh.2025.1605212/full>
[266] <https://doi.org/10.1038/s41746-024-01326-y>
[267] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10414079/>
[268] <https://systematicreviewsjournal.biomedcentral.com/counter/pdf/10.1186/s13643-019-1034-4.pdf>
[269] <https://digital.ahrq.gov/sites/default/files/FINAL%20OO%20PC%20CDS%20SDM%20Report.pdf>
