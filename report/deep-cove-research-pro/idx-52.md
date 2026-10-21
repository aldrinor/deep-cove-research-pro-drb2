# Generative AI in Education: Opportunities, Challenges, and Responsible Responses Through May 2023

**Supervised integration is the strongest approach.** Through May 2023, generative AI represented by ChatGPT offered substantial opportunities for individualized explanations, language support, formative feedback, and instructional preparation. Its educational value, however, depended on how it was used: fluent answers could contain errors, reproduce bias, expose personal information, or substitute for the thinking that an assignment was intended to develop. The strongest position was therefore neither unrestricted adoption nor a universal ban, but purposeful use with educator oversight, transparent assessment rules, privacy protection, and equitable access. This position accords with the human-centered recommendations of the U.S. Department of Education’s May 2023 report [1].

**Capability is not educational effectiveness.** GPT-3’s 175-billion-parameter scale and GPT-4’s stronger benchmark performance demonstrated important technical advances. They did not establish that conversational AI improved long-term learning, could independently assess students fairly, or should replace teachers. Educational decisions must distinguish what a model can produce from what a learner understands and what an institution can responsibly delegate.

**The report addresses four connected questions.** It first explains the technology and its development, then examines opportunities for learners and educators, analyzes the principal threats, and translates those findings into practical classroom and institutional responses. The following table summarizes the resulting recommendations; the four sections develop their evidence and reasoning.

| Educational use | Potential value | Evidence through May 2023 | Main risk | Minimum safeguard | Expand-or-stop condition |
|---|---|---|---|---|---|
| Tutoring and study support | Responsive explanations and practice | Demonstrations and short studies | Answer substitution | Teacher oversight and independent explanation | Expand when understanding improves |
| Language and accessibility support | Reduced communication barriers | Descriptive cases and model benchmarks | Distorted meaning or unequal quality | Learner choice and specialist review | Expand when access improves |
| Teacher planning and drafting | Faster preparation and more alternatives | Practical demonstrations and guidance | Inaccurate or unsuitable materials | Subject-expert review | Expand when net workload falls |
| Formative feedback | Timely guidance and feedback analysis | Exploratory task evaluations | Misleading feedback | Rubrics and human moderation | Expand when revisions improve |
| High-stakes educational decisions | Possible administrative efficiency | General model capability tests | Unfair or consequential errors | Accountable human decision-making | Exclude autonomous decisions |

## Technical Background and Development

### What generative AI, GPT, and ChatGPT mean

**Generative AI creates new content.** It produces text, images, code, or other media in response to an input, commonly called a *prompt*. Whereas many earlier educational AI applications primarily classified responses, predicted outcomes, or recommended resources, generative systems construct content using patterns learned during training. An April 2023 article in *IEEE Computer* identified essays, answers, summaries, code, images, and music as examples of such outputs. [2]

**GPT names a model family.** The abbreviation means *Generative Pre-trained Transformer*. A language model learns statistical relationships within language; a Transformer uses an attention mechanism to relate different parts of its input. GPT models generate a response progressively, predicting the next *token*—a word, word fragment, or other textual unit—from the preceding context. OpenAI describes GPT-4 as a Transformer-style model pretrained through this next-token prediction task. [3]

**Pretraining supplies broad linguistic capabilities.** During this stage, the model learns from large collections of examples rather than receiving a separately programmed rule for every possible question. This is often described as self-supervised learning because the text itself supplies the prediction target. The resulting model can generate language across many topics, but the training objective does not independently establish whether every generated statement is true.

**Post-training shapes conversational behavior.** ChatGPT’s initial release combined supervised conversational examples with reinforcement learning from human feedback, or RLHF. Human trainers demonstrated responses and ranked alternatives; those preferences helped shape subsequent model behavior. This process made dialogue and instruction-following more useful, but OpenAI’s launch description also acknowledged plausible-sounding incorrect answers and sensitivity to prompt wording. [4]

**ChatGPT is a conversational system.** It was publicly launched on 30 November 2022, initially using a dialogue-tuned model from the GPT-3.5 series. Its interface allowed users to ask follow-up questions, request revisions, challenge answers, and develop a response through conversation. GPT-4, released in March 2023, was a later underlying model made accessible through ChatGPT and an application programming interface, or API, which allows software to communicate with a model. ChatGPT and GPT-4 therefore refer to related but different things: a conversational product and a model that can power it. [4][5]

### Development from GPT-1 to GPT-4

**The progression involved more than scale.** Between 2018 and May 2023, the GPT family advanced through larger models, broader task performance, more accessible conversational interaction, and multimodal input. The essential milestones are summarized below. Historical parameter counts are reported in the contemporary [6], while the ChatGPT and GPT-4 entries follow OpenAI’s release descriptions.

| Date | Development | Parameters or model basis | Input and output | Principal transition |
|---|---|---|---|---|
| 2018 | GPT-1 | 117 million parameters | Text to text | Generative pretraining for downstream tasks |
| February 2019 | GPT-2 announcement | Largest model: 1.5 billion parameters | Text to text | More capable general text generation |
| 2020 | GPT-3 | 175 billion parameters | Text to text | Stronger few-shot task performance |
| 30 November 2022 | ChatGPT launch | Dialogue-tuned GPT-3.5 | Conversational text | Accessible interaction and follow-up dialogue |
| 14 March 2023 | GPT-4 launch | GPT-4 parameter count withheld by OpenAI. | Image/text to text | Stronger performance and multimodal capability |

**GPT-3’s size was a specification.** Its **175 billion parameters** were learned numerical values within the model, not a count of facts, documents, or educational competencies. Brown and colleagues described GPT-3 as approximately ten times larger than the previous non-sparse language models in their comparison. That scale supported broader performance, but parameter count alone was not a measure of instructional quality. [7]

**Few-shot learning widened practical use.** GPT-3 could perform many tasks from a textual description and a small number of examples without task-specific fine-tuning or changes to its parameters during the interaction. Reported strengths included translation, question answering, completing missing text, using unfamiliar words in sentences, and some three-digit arithmetic. This made a general language interface more plausible than building a separate model for every classroom task. [7]

**Scaling did not remove unevenness.** Contemporary comparisons reported strong GPT-3 results alongside weaknesses in word-in-context and reading-comprehension benchmarks. The significance of GPT-3 was therefore its flexibility across tasks, not uniformly dependable mastery. That distinction matters educationally: a model that handles one exercise convincingly may still fail on a closely related task requiring a different kind of reasoning. [8]

**ChatGPT changed access and interaction.** Its educational importance was not simply that language models had become larger. Natural-language dialogue lowered the barrier to requesting explanations, generating drafts, and revising material. A teacher or learner could interact without writing application code, while follow-up questions made assistance more responsive than a single static answer. These features explain why conversational tutoring and feedback became prominent proposed uses in UNESCO IESALC’s April 2023 guide [9].

### GPT-4’s capabilities and their educational meaning

**GPT-4’s parameter count remained withheld by OpenAI.** OpenAI’s March 2023 technical report withheld model size and further details concerning architecture, hardware, training compute, and dataset construction. Its published specification was therefore a disclosure status, not an estimated parameter total. Benchmark performance provides no defensible arithmetic for reconstructing that total. [3]

**GPT-4 improved several measurable capabilities.** OpenAI reported stronger performance on professional examinations, knowledge questions, coding tasks, and complex instructions. Human evaluators preferred GPT-4’s responses over GPT-3.5’s on 70.2% of 5,214 sampled prompts, judging whether responses matched user intent. That preference measure indicates improved usefulness in the sampled interactions; it measures neither factual accuracy alone nor student learning. [3]

**The bar result was substantial.** On OpenAI’s simulated Uniform Bar Examination, GPT-4 scored 298 out of 400, assigned an estimated percentile around the 90th, compared with GPT-3.5’s 213 out of 400 and approximately 10th percentile. “Around the top 10%” describes the reported position relative to a comparison distribution, not a score of 90% correct. The examination was simulated, using model prompts and exam-specific scoring procedures. [3]

A reanalysis using July administration data estimated GPT-4 below the 69th percentile overall and about the 48th percentile on essays; under conservative assumptions against first-time test takers, it estimated about the 62nd overall and 42nd essay percentiles.

| Evaluation reported in March 2023 | GPT-3.5 | GPT-4 | Task measured |
|---|---|---|---|
| Simulated Uniform Bar Examination | 213/400 | 298/400 | Legal examination responses |
| MMLU, five-shot evaluation | 70.0% | 86.4% | Multiple-choice knowledge across 57 subjects |
| HumanEval, zero-shot evaluation | 48.1% | 67.0% | Python programming problems |
| GRE analytical writing | 4/6 | 4/6 | Examination essay writing |
| AP English Language and Composition | 2/5 | 2/5 | Examination reading and writing |

**The counterexamples prevent overgeneralization.** GPT-4’s gains were broad but not uniform: its reported GRE writing score and AP English Language score matched GPT-3.5’s. A strong bar-exam result therefore supports a judgment about performance on that test, not a claim of general human-equivalent competence. Teaching also requires diagnosing misunderstandings, choosing instructional sequences, managing relationships, and responding to classroom circumstances—functions not measured by those examinations.

**Multimodality broadened the possible tasks.** GPT-4 could accept image and text inputs and produce text, including code. OpenAI demonstrated responses involving diagrams, photographed documents, and screenshots, creating possibilities for explaining visual material or making it more accessible. At release, however, image input remained a restricted research preview rather than a generally available classroom feature. [5]

**Multilingual results were promising but specific.** On machine-translated versions of MMLU, GPT-4 exceeded earlier models’ English-language performance in 24 of 26 tested languages, including Welsh, Latvian, and Swahili. This demonstrated multilingual knowledge-question performance under a particular translation and prompting procedure. It did not establish equally effective tutoring, culturally appropriate explanations, or reliable assessment in every language. [3]

**Factuality improved without becoming dependable.** OpenAI’s launch summary reported a 40% relative improvement over its latest GPT-3.5 on an internal adversarial factuality evaluation; the technical report described a 19-percentage-point advantage on its internal evaluation. These are model-evaluation results, not classroom accuracy rates. The technical advance should consequently be understood as broader and more useful assistance, with verification still necessary. [5][3]

**Technical judgment: capability enables educational experimentation.** The development through May 2023 justified carefully supervised applications, but did not justify treating generated explanations as authoritative or examination performance as proof of teaching effectiveness.

## Opportunities in Education

### What the early evidence actually demonstrates

**The clearest opportunities concern bounded tasks.** By May 2023, studies and institutional guidance showed that ChatGPT could generate instructional materials, support conversation, explain concepts, and assist with selected feedback and programming tasks. The strongest educational argument was not that it had already transformed attainment, but that it could make useful forms of assistance more responsive and easier to produce. UNESCO IESALC described roles including a personal tutor, Socratic opponent, study buddy, collaboration coach, and curriculum co-designer. [9]

**Early studies measured different outcomes.** Engagement, output correctness, and the classification of student comments answer different questions. Bringing them together reveals practical possibilities without incorrectly combining them into a single educational “effect.”

| Study and setting | Design or scale | Reported result | What the result measures |
|---|---|---|---|
| Digital-literacy study [10] | 130 undergraduates; two-week quasi-experiment | Context-dependent engagement effects | Short-term learning experiences |
| Team-learning feedback study [11] | Exploratory classification evaluation | Over 90% comment-labeling accuracy | A bounded feedback-analysis task |
| Rahman and Watanobe [12] | Eight programming problems; three outputs each | 23/24 basic checks; 18/24 online-judge checks | Generated-code performance |

**The programming comparison is instructive.** Eight problems multiplied by three generated solutions produced 24 code samples. The basic-compiler evaluation yielded 23/24, or approximately 95.8%, successful results, while the Aizu Online Judge accepted 18/24, or 75%, under its more demanding evaluation. The difference shows why educational usefulness depends on the standard applied: apparently successful output may still fail when execution constraints, formatting, or additional test cases matter. [12]

**Context influenced student engagement.** The 130-student study involved STEM and non-STEM undergraduates learning digital literacy with or without ChatGPT over two weeks. Survey results varied with the topics taught and students’ disciplinary backgrounds. Reflections identified benefits such as efficiency and filling knowledge gaps alongside generic responses, limited innovation, and concerns about self-discipline and thinking. The practical conclusion is to match integration to the task and learners, rather than assuming one approach will benefit every course. [10]

In a University of Bergen survey, 80 of 111 student users (72%) reported occasional or frequent improvement in task completion. This was a self-reported benefit, while the 130-student quasi-experiment found engagement effects that varied with topic and disciplinary background.

### Personalized tutoring and learning support

**Conversation can make explanations more responsive.** A learner can ask for a simpler explanation, a different example, a comparison, or a hint addressing a particular difficulty. Unlike a fixed worksheet, the same interface can respond to successive questions. UNESCO’s proposed tutor and study-buddy roles exploit precisely this capacity for dialogue and immediate response. [9]

**Personalization can change the route through material.** A student who understands a definition but struggles to apply it needs different assistance from one who misunderstands the definition itself. ChatGPT can generate alternative explanations and practice questions from descriptions of these needs. The benefit comes from adapting assistance to prior understanding, language, and learning goals—not from assuming that a conversational response constitutes a validated diagnosis of the learner’s knowledge.

**Hints preserve more learning work.** A proposed mathematics activity, for example, could require a student to attempt a problem before requesting one hint, explain why that hint is relevant, and then finish the solution independently. This uses generative AI to reduce an obstacle without removing the task’s central reasoning. Asking the model to produce the complete answer instead changes the relationship: successful completion may then reflect the model’s performance rather than the learner’s development.

**Additional support can complement scarce teacher time.** The World Bank identified adaptive assistance as particularly attractive where teachers were responsible for many students and had limited capacity for individualized attention. It also discussed Khan Academy’s proposed GPT-supported course guidance and commercial claims for personalized language lessons. The educational opportunity is supplementary support between human interactions, with supervision built into the arrangement. [13]

**Learner agency remains the deciding condition.** The most useful tutoring interaction leaves the student better able to explain, apply, or question the material afterward. Assistance should therefore be judged by what learners can subsequently do, including without the tool, rather than by the length or apparent sophistication of the conversation. This distinction separates personalized learning support from personalized answer delivery.

### Feedback, practice, and formative assessment

**Immediate feedback can shorten revision cycles.** ChatGPT can comment on a paragraph’s clarity, suggest weaknesses in an argument, explain a programming error, or generate another practice question. These functions fit *formative assessment*: feedback used during learning to guide improvement, rather than to make a final judgment or award a qualification. Cambridge education researchers identified the summarization of arguments and concepts as a promising support where teacher time was limited. [14]

**Useful feedback requires an actionable next step.** A comment such as “develop your argument” offers little direction; identifying an unsupported claim and asking what evidence would justify it is more educationally useful. Generative AI can produce such alternatives quickly, but educators must decide whether they are accurate, appropriate to the rubric, and suitable for the learner. Feedback becomes valuable through the resulting revision, not merely through its production.

**Feedback analysis offers a narrower opportunity.** The May 2023 team-based-learning study reported over 90% accuracy when ChatGPT labeled student comments using an existing positive-and-negative framework. That finding supports a possible role in organizing feedback for educator inspection. It does not make the system a validated judge of a student’s achievement, contribution, or emotional state. [11]

**Practice materials can become more varied.** Educators can generate additional questions, examples, or explanations around a defined concept, allowing students to practice beyond a single exercise set. A teacher could request questions addressing a recurring misconception and review their answer keys before distribution. The mechanism is economical variation: the model generates alternatives, while the teacher preserves curricular coherence and checks whether the questions actually assess the intended concept.

**Human feedback can become more selective.** If routine language suggestions or preliminary explanations are handled adequately, teachers may concentrate on deeper misconceptions, disciplinary judgment, and encouragement. This is an augmentation argument, not an argument for eliminating personal feedback. The recommendation changes if automated comments create confusion, require extensive correction, or discourage students from seeking human help.

### Language support, accessibility, and inclusion

**Language transformation can remove avoidable barriers.** ChatGPT can translate, simplify wording, explain unfamiliar terminology, and help learners express ideas more clearly. These functions may be particularly useful when subject understanding is stronger than proficiency in the language of instruction. The 2023 *CITE Journal* editorial identified writing and communication support for English-language learners and students with language or learning disabilities as promising applications. [15]

**A concrete case concerns academic writing.** Cambridge’s Vaughan Connolly described postgraduate students who used ChatGPT to rewrite paragraphs in an academic style when English was their second language. He argued that this reduced the burden of translation and allowed greater attention to content. The educational significance depends on the assessment objective: language assistance may remove an irrelevant barrier in a subject assessment, while extensive rewriting may displace the very skill being assessed in a language course. [14]

**Accessibility extends beyond language editing.** Contemporary education discussions proposed transcripts, subtitles, speech recognition, speech-to-text, and text-to-speech as ways to improve access. These should be understood as possible functions of an integrated educational system: the original text-based ChatGPT interface did not itself supply every audio or video capability. Combining language generation with appropriate speech and accessibility tools could support learners who encounter barriers in conventional text presentation. [16]

**Multimodal input suggested further possibilities.** GPT-4’s image-processing capability could support descriptions of diagrams, questions about photographed material, or explanations combining visual and written information. OpenAI’s initial collaboration with Be My Eyes illustrated an accessibility-oriented direction for development. Its restricted image-input release nevertheless distinguished a demonstrated technical possibility from a generally accessible school service. [5]

**Multilingual performance requires task-specific judgment.** GPT-4’s translated MMLU results contrasted with an April 2023 evaluation of ChatGPT across seven tasks and 37 languages, which reported weaker performance than previous models on various tasks and languages. These results concern different models, benchmarks, and prompting procedures; they are not contradictory estimates of one common outcome. Their joint implication is that multilingual access must be tested in the language and educational task actually required. [17]

**Inclusive design should preserve learner choice.** A conversational tool may help one student organize material while creating additional complexity for another. Xu and colleagues’ May 2023 discussion of personal learning environments identified possible support for learners with dyslexia or attention-deficit/hyperactivity disorder, while emphasizing training, security, and continued human interaction. Institutions should therefore treat AI as an optional support layer, developed with disabled and multilingual learners, rather than a replacement for established accommodations. [18]

### Teacher preparation and educational productivity

**Preparation is a strong near-term application.** ChatGPT can draft lesson outlines, learning objectives, discussion prompts, examples, quizzes, assignment instructions, and rubrics. Aga Khan University’s May 2023 guidance explicitly recommended several of these uses for faculty and teaching assistants, including using ChatGPT as a “peer” to critique learning outcomes and assessment design. The common feature is that outputs remain drafts under professional control. [19]

**Generating alternatives can improve design decisions.** A teacher could request several explanations of the same concept, compare their assumptions, and adapt the most suitable elements. Similarly, multiple draft discussion questions may help an educator select one that invites reasoning rather than recall. This benefit arises from having more options to evaluate; it should not be confused with the model independently knowing the class or selecting an effective pedagogy.

**Curriculum translation matters in constrained systems.** The World Bank highlighted the difficulty of converting dense curricula into engaging lessons in low- and middle-income countries. ChatGPT could assist with activity ideas, lesson preparation, and assessment questions. Its analysis also distinguished preparation from delivery: effective teaching still required pedagogical proficiency and an educator able to respond to students during the lesson. [13]

**First drafts can reduce routine writing.** Todd Finley’s March 2023 practitioner account described uses spanning planning, differentiated materials, correspondence, assessment, and writing feedback. His central practical recommendation was to regard generated compositions and curricula as first drafts and check their accuracy and usefulness. For teachers, the opportunity is strongest where drafting is time-consuming but review is manageable. [20]

**Net productivity depends on review costs.** The relevant relationship is straightforward: time saved equals drafting time avoided minus the time spent prompting, checking, correcting, and adapting outputs. A polished but inaccurate worksheet may create more work than it removes. Conversely, a suitable draft of routine instructions may allow a teacher to spend more time discussing misconceptions or supporting a struggling learner.

**Administrative assistance can improve responsiveness.** UNESCO IESALC identified possible uses in answering applicant questions, explaining administrative information, translating communications, and sending reminders. These functions are most defensible when grounded in approved institutional information and accompanied by a clear route to a person. An incorrect explanation of an examination deadline or course requirement can be consequential even if it appears administratively routine. [9]

### Research support and educational innovation

**Researchers can use assistance without delegating judgment.** Proposed applications included summarizing supplied material, improving expression, generating analysis code, and suggesting questions or alternative interpretations. The May 2023 *IEEE Computer* article also discussed experiment design and literature-related assistance. Such uses can lower barriers to preliminary work, provided researchers retain responsibility for sources, methods, interpretation, and the integrity of the final publication. [16]

**The strongest opportunity is expanded human capacity.** Generative AI is most educationally promising when it makes explanations, practice, accessible communication, and preparation more responsive while preserving meaningful work for learners and educators. Expansion is justified when those benefits translate into better understanding, participation, or net workload—not simply more generated text.

**Additional documented evidence**

**Conditional opportunity mechanisms**

By 31 May 2023, the defensible opportunity claim was conditional augmentation, not autonomous teaching: the literature review presents ChatGPT’s benefits as potential mechanisms and identifies itself as argumentative rather than a controlled outcome evaluation [93].

**Learners.** ChatGPT could support four learning interactions—content, others, self, and problem-solving—through personalized explanations, one-to-one tutoring and feedback, individually designed exercises or exam models, step-by-step solutions, and suggested materials. Multilingual responses and practice in writing, reading, mathematics, physics, and programming could support self-directed learning, reflection, metacognition, and the four Cs (collaboration, communication, critical thinking, and creativity), especially where high student–teacher ratios limit individual help. The proposed benefit depends on learner age or level, proficiency, needs, and proper human guidance [93].

**Access and inclusion.** ChatGPT could tailor resources, content, and pace for learners with disabilities or learning difficulties; text-to-speech and speech-to-text were proposed for disabled learners, including dyslexia and autism examples. These are proposed accessibility mechanisms, not measured causal outcomes [93].

**Educators and institutions.** ChatGPT could draft content, lesson plans, slides, teaching ideas, customized materials, questions, rubrics, grammar feedback, and multiple-choice scoring, potentially freeing time for instruction, professional learning, one-to-one feedback, and differentiated activities. Teachers remain responsible for source evaluation and judgment: the review says AI assessment was not yet consistent or truthful without guidance and calls for human–AI collaboration [93]. Institutions and education leaders could build a digital-friendly ecology through strategic planning, training, ethical-use rules, assessment redesign, and avoiding crude bans [93].

**Lineage and capability mechanism.** GPT-1 was introduced on 11 June 2018; GPT-2 followed in February 2019 as a direct scale-up, increasing parameters and data tenfold and reaching 1.5 billion parameters [45]. GPT-3 (2020) reached 175 billion parameters and a 2,048-token context window, with zero- and few-shot learning; its text-in/text-out API could complete almost any English-language task and generate code, prose, and a sample pedagogy essay [45]. In an initial test, 80 U.S. subjects correctly identified only 52% of approximately 200-word human-versus-GPT-3 articles [45]. This supports content, coding, and drafting as plausible opportunities, not learning gains. InstructGPT became OpenAI’s default API model on 27 January 2022; its fine-tuning on human-written instructions was reported to improve instruction following, reduce made-up facts, and produce somewhat less toxic content, making educational dialogue more usable but not authoritative [45].

Overall, the opportunity case is strongest for guided tutoring, drafting, feedback, and AI-literacy activities; the evidence here does not establish general learning or teaching effects. Later post-cutoff fragments are not counted as evidence for the May 2023 assessment.

ChatGPT and related large language models could give learners individualized questions, practice, explanations, assessments, contextual examples, dialogue, and immediate feedback for self-paced study; they can also assist collaborative writing, editing, summaries, outlines, and research prompts [94][95]. In language learning, they offer task-oriented practice, vocabulary feedback, and support for anxiety or low willingness to communicate; reviewed systems remained well behind human performance in helping students, so teacher and curricular guidance is necessary [94]. GPT-3 demonstrations generated reading-comprehension quizzes, code explanations, and curiosity prompts for knowledge testing, coding, and question-asking, but these are demonstrations or proposed mechanisms, not general causal learning gains [94].

For inclusion, large language models can combine speech-to-text/text-to-speech with adaptive writing, translation, and highlighting, with specialists adapting support to disability needs [94]. ChatGPT was described as handling German, French, Spanish, and English, but equal cross-language quality is unestablished; language and financial-access gaps could reverse equity benefits [94][95]. Educators could use Generative AI/GPT for lesson plans, syllabi, quizzes, rubrics, formative feedback, grading, reports, tailored activities, and professional-learning summaries, potentially reducing workload and freeing time for learners; professional judgment remains necessary [94][95][97]. Schools can build AI literacy by having learners generate hypotheses, question outputs, corroborate them with authoritative sources, and practise critical thinking [94]. Institutions could streamline communication, applicant screening, and data curation, subject to bias and fairness checks [95]. Benefits vary by education level, age, subject, task, language, disability, expertise, setting, and access; by May 2023, evidence remained early and limited [94][96].

ChatGPT’s opportunity is scalable natural-language dialogue: it could offer personalized, one-to-one explanations, exercises, diagnostic feedback, language practice, and writing/speaking suggestions. Grading and teacher “dynamic assessment” remain proposed—not measured—ChatGPT outcomes; direct education evidence was scarce [98].

Indirect, not ChatGPT-specific evidence: a 24-randomized-study meta-analysis (online 3 May 2023; issue record 2024) reported overall AI-chatbot learning ES=0.964 (95% CI .642–1.286); higher-education ES=1.079 [.710–1.448], versus primary .931 and secondary .214, which were statistically insignificant. Effects were larger below 10 weeks (ES=1.179) than at least 10 weeks (.492); heterogeneity was I²=94%, and trim-and-fill added 15 hypothetical studies for publication-bias adjustment [98]. Applications span mathematics, psychology, medicine, and language, but ChatGPT-specific STEM verification remains unestablished. Benefits require device access, feedback, language/digital literacy, self-regulation, and teacher guidance; novelty can fade and prolonged use can overload learners [98].

Generative AI/ChatGPT offered potential for instructional text/exercises, virtual assistants, student support, assessment and feedback; training, prior knowledge and human validation were needed amid accuracy, cheating, bias and fair-access concerns [100]. GPT models’ self-attention/feed-forward architecture supports text/code generation, but outputs are task-dependent and hard to interpret [100]. Students found ChatGPT exciting but questioned accuracy; dialogue/arithmetic aided problem-solving, yet mathematics was below an average graduate student’s level [100]. GPT-3 enabled rapid knowledge extraction but missed word counts and produced a minor code error; no GPT-4-specific educational result is supplied [100]. InstructGPT is lineage only; the June 18, 2023 tutoring study’s personalization/feedback/hallucination findings are excluded [99].

ChatGPT could support tutoring, feedback, translation/accessibility, coding, research, and lesson plans; dialogue may promote learning, but a physics study found contradictions and failed Socratic correction, so verification and human oversight remain essential [101] [102]. GPT-3’s 2020 scale was over 175 billion parameters, enabling content/language uses but not demonstrating educational gain [101]. These errors can support critical-media and process-assessment activities; multilingual access is conditional because outputs may be monocultural, while paid access and connectivity gaps can widen inequity [101] [103].

GenAI/ChatGPT may tutor, explain, code, translate and give feedback; learners must understand, verify and do lab work [75][104][106]. GPT-3: 175bn parameters, 3,000-word limit; GPT-4 physics retest: +2%, mixed vs GPT-3 [75]. iSTART (116 vs 118) improved self-explanation/transfer, not ChatGPT evidence [105]. Access may aid non-native/disabled learners, but paywalls/prompting widen divides; AI literacy/disclosure, educator/admin work and assessment need oversight [104][106].

By 31 May 2023, a U.S. Education Department report described ChatGPT-like tutoring as scalable support: systems could observe problem solving, give step-level feedback and adapt practice, while teachers retain instructional judgment [107]. Learners might gain customized, multilingual and disability-accessible materials; educators might save routine time; institutions could teach AI literacy and co-design tools [107]. These are possibilities, not measured ChatGPT outcomes: pilots must test accuracy, bias, privacy, efficacy and who benefits [107].

ChatGPT: potential, unmeasured tutoring/feedback, math/writing help, language practice, adaptive translation and disability support; teacher/specialist review required [46][108]. Generative AI can draft K–12 lessons/UDL activities, rubrics, assessments and role-play/debates; AI literacy requires source checks/disclosure; it remains a starting point [108][109]. GPT-3 enables text/content generation; GPT-4 can support medical curricula, cases, study plans, rubrics and feedback; monitor learning/dependence, privacy/equity, bias/misinformation and contested authorship [46][108]. Learners may gain access, but outsourcing and unequal language/technology access can reverse gains; institutions may gain administrative/tutoring support, with efficiency unproven [46][108].

At 31 May 2023, [65] (2025) and [110] (2024) are post-cutoff; their ChatGPT, GPT-4, GPT models and Generative-AI claims—tutoring, feedback, personalization, inclusion, research and AI literacy—are inadmissible; no pre-cutoff opportunity finding is established [65][110].

GenAI/ChatGPT/GPTs: tutoring, content, feedback, STEM; potential only; verify with humans [111][112].

ChatGPT: tutoring/source critique; code 95.83% basic, 75% AOJ (May 2023); GPT-3≈175B params (2020); potential—human review [113][114][115].

ChatGPT may tutor; verify outputs; preserve learner agency [116]

2024 review post-cutoff; ChatGPT findings excluded [117].

ChatGPT could support tutoring, feedback, content, translation and essay grading—but these were not proven learning gains; subject performance varied, so STEM outputs required verification [118]. The evidence concerned GPT-3.5, not GPT-3/GPT-4; schools should teach critical evaluation and update assessment/integrity policies [118].

ChatGPT: tutoring, AI literacy, feedback/content; 118 studies/53 uses; potential, not proven; verify/human oversight [119][120][121]

ChatGPT may support tutoring, teacher-unavailable clarification, discussion, brainstorming, writing, summaries and research; hallucinations, fabricated references and bias require verification [122][124]. Educators may use it for resource curation, coaching, routine feedback, lesson generation and administrative support, but complex grading and workload savings remain unproven [122]. A higher-education study found GPT-4’s rubric-aligned feedback matched human marking 100% in full-mark and non-attempt cases; learning was not measured, subjective judgments were weaker, and students must interpret feedback under human oversight [123]. AI literacy requires technical and ethical-critical skills; 85% of surveyed Asia-Europe teachers rated it important, but two-thirds reported AI in curricula [122].

May 2023: GPT-3 may tutor/content; risks: error, bias, cheating [125]

By May 2023, Generative AI/GPT offered tutoring, literacy, feedback and multilingual content; evidence was demonstrative [92][78]. ChatGPT revision in South Korea (2023 EFL; n=213 students, 7 teachers): 85% exposed used it for study; hallucinations needed verification [126]. GPT-3 feedback was supplementary; GPT-4 gains unmeasured [92].

GenAI/ChatGPT/GPT-3: potential tutoring, dialogue, feedback, translation, research, STEM, access [79][127][129]. InstructGPT: instruction-following dialogue; error/bias/prompt sensitivity [79]. Learners verify; teachers judge [127][155]. GPT-4: Dutch exam; adaptive feedback, 19/105 pass outcomes diverged [128].

By 31 May 2023, ChatGPT/LLMs offered potential tutoring, feedback, lesson drafting, personalized dialogue and AI literacy [130][131]; benefits required learner context, critical checking and teacher review, while personalization/effects remained uncertain (tertiary) [130]. GPT-3 dialogue was a precursor [131]; risks: cheating, reliance, bias, privacy and inequity [130][131].

By 31 May 2023, opportunity evidence was chiefly capability/application evidence, not causal learning gains. Reviews reported personalized/adaptive tutoring, language dialogue, course/practice materials, assessment support, translation, explanation, problem-solving and coding [90]. A physics-writing evaluation reported 71 ± 2% for generated essays versus a 71 ± 5% module average; advanced mathematics remained weak, and programming improved with decomposed tasks and execution checks [90]. ChatGPT launched 30 November 2022 and was built on GPT-3 (175 billion parameters) [132]; GPT-4’s count was undisclosed [56]. GPT-4’s 298/400 (about 90th percentile) simulated UBE result (MBE+MEE+MPT) shows benchmark capability, not teaching effectiveness [56]. Because GPT-4 still hallucinated and made reasoning errors, educators need human review or grounding; outputs are aids, not authoritative answers [56][90][132].

ChatGPT can offer dialogue and feedback, but bias/context limits require human oversight [133]. ChatGPT-3.5 prompts yielded richer formative questions, yet 42/90 were unusable; educators had to proofread, select and edit them [57]. UK academics perceived GAI planning support, not measured impact [134].

ChatGPT’s early-demo dialogue and premise correction could support tutoring; nonsense, bias, and harmful replies warranted educational review [58].

By May 2023, educational opportunity depended on active learning, feedback, teacher support, and learner agency; AI assistance could not replace these conditions [72][135][136].

Potential, not proven: ChatGPT offers adaptive tutoring, instant feedback, tailored materials, 24/7 access, accessibility and teacher relief [137], but needs trained human oversight, privacy and bias/integrity checks. A spring-2021 evaluation (117 students; 5,142 answers) found 0.75 accuracy and 1,118 false positives; verify outputs [59].

Learning gains vary by level [138]

GPT-4 (2023): 298/400 (top 10%) on a simulated UBE; verify outputs because hallucinations persist [60]

ChatGPT could support tutoring, practice and teacher work; evidence was preliminary by May 2023 [61].

ChatGPT may support learners through tutoring, problem solving, writing, coding, translation, accessibility and research ideation, but these are potential uses, not measured learning gains. Educators should retain human guidance, check sources, treat outputs as leads—not evidence, require attribution and align use with course goals [140][81].

Generative AI via ChatGPT (Nov 2022; GPT-3.5) offers dialogue, tutoring, coding and brainstorming; GPT-3 offers translation, summarization and content generation [141]. GPT-3 acted as pseudo-teacher; ChatGPT v3.5 gave students more detailed, high-agreement feedback than instructors and supported literacy [84]. Demonstrations, not learning gains: outputs vary, stale or wrong; verify sources/code and teach critical thinking [91][141]. GPT-1 (2018) is lineage only; GPT-4’s education was not directly evaluated [84].

ChatGPT: tutoring, personalized practice, lessons, feedback, quizzes, code and language support remain promising but require human review, fact-checking, equity [142][143].

ChatGPT’s opportunity is conditional dialogue: follow-ups can tailor explanations, scaffold reflection, and support learner challenge [144]. Evidence was early: a 24-study meta-analysis found mostly short-term, higher-education effects, possible novelty, and speculative conclusions [85]. AI could provide personalized guidance, support, and feedback; educators could use an AI lesson-planning assistant, and institutions could use analytics or grading, but opaque decisions and operating costs limit gains [85]. Learners and teachers must verify plausible but fallacious text [85]. Khan Academy’s March 2023 GPT-4 pilot framed Khanmigo as a tutor and teaching assistant—an aspiration, not a measured outcome [85].

ChatGPT: 103 Australian proposals; 57/103 (55%) process-focused feedback; assessment unreliable [145].

ChatGPT supported tutoring/feedback; 2023 EFL: 85% of exposed used it; Philippine learners needed prompting/verification [146][147].

ChatGPT may provide tutoring, feedback, and accessibility support; validate outputs [350, 351].


ChatGPT: tutoring potential [148].

Post-cutoff source; exclude [149].

GPT-2 MOOC: information 11.73% vs human 42.85%; community 79.28% vs 81.42% [44]. ChatGPT: physics hints, math errors; preliminary [150].

ChatGPT needs review [151]

Potential (not measured): ChatGPT/GenAI offers students tutoring, ideation, language/access, STEM/research, feedback; teachers draft lessons/quizzes [152][153]. Institutions may gain data/admin efficiency [153]. Verify outputs; redesign assessment around process and drafts [152]. Unequal access/connectivity, cost, skills may widen gaps [153].

By 31 May 2023, ChatGPT/GPT‑3.5 offered potential—not measured—support for language/translation, level-tailored materials, lesson planning, research, rubrics, quizzes and feedback; guiding questions preserved learner authorship [156]. GPT‑4 was reported better than GPT‑3.5 at target-level vocabulary and as reliable as local raters with careful prompts, but assessment validity was untested [156]. Benefits require context, access, expert review, approved tools, disclosure/consent, privacy controls and 100% human responsibility for feedback [154].

ChatGPT aids teaching/assessment but needs review [157]; writing practice may harm disadvantaged/foreign-language students; ~23 kg CO₂e/day (training excluded) [157].


By May 2023, ChatGPT offered lesson/writing support; benefits were potential, with outputs requiring verification and disclosure [82][139].

GPT-3 (175 billion parameters, 2020) generated connected text; benefits remained potential, not measured [159]. ChatGPT could support tutoring, writing, translation, accessibility and feedback, but needs verification, authorship, process assessment and AI literacy [158][160].

ChatGPT Plus: $20/month (2023-02-01); ChatGPT offered drafting, brainstorming, programming and learning; no measured education gains [83].

Practice-based GenAI/ChatGPT evidence supports student prompting/brainstorming/drafting, educator lesson design, research, collaboration and reflection, but not measured attainment; humans must verify/revise/discard outputs, retain authorship, and teach AI literacy amid role uncertainty [162]. The preprint, published 14 Aug 2023, is post-cutoff; its findings are excluded [161].

ChatGPT may aid L2 learners [163].

ChatGPT offered translation and multimodal uses; 77 algebra participants gained more from human hints, so benefits remain conditional [69].

Generative AI/ChatGPT: potential tutoring, feedback, translation and lesson planning; GPT-3 (2020): 175B parameters; GPT-4 education outcomes remained unshown [164]; educators/learners verify outputs [165].

Post-cutoff; excluded [166][167].

ChatGPT: schoolwork aid; detectors unreliable [76]; capacity issue

GenAI/ChatGPT may aid access, tutoring and AI literacy; verify outputs and retain human judgment [168]

By May 2023, GPT-3 (175 billion parameters) and ChatGPT in higher education could enable translation, summarisation, content generation, personalised assessment, grading, immediate feedback, tailored resources, problem-solving and remote learning/collaboration; inaccurate outputs, plagiarism and unfair advantage threatened assessment integrity, requiring human review [169].

2023: ChatGPT helped 51% [77]

No cutoff evidence; exclude [170].

ChatGPT: access, feedback [171].

May 2023—ChatGPT: dialogue/language/coding/research potential [172][80]; access+expertise+verification.

At the 31 May 2023 cutoff, no measured outcome is established for accessibility, tutoring, STEM, teacher productivity or institutional use; later reports and post-cutoff observations are excluded. These remain potential mechanisms, conditional on access, training, verification, accessible design and human support—not demonstrated effects.

ChatGPT may offer learners tutoring, feedback, language support and accessibility; schools gain efficiency; verify outputs [173][174][175].

ChatGPT may tutor, explain; verify outputs [177]. Disabled learners may gain flexible dialogue [176].

ChatGPT offered natural-language dialogue for language learning, but fluent outputs could be false, outdated or misleading; teach verification and ethical use [178]. A 2020 GPT-2 demonstration trained on 188 student papers for ~30 minutes, then produced revisable drafts; it could generate fake news, so assess process and authorship cautiously [179]. GPT-4 added visual explanation and handwritten-code generation; image access required a restricted API [86][87].

By 31 May 2023, Generative AI could amplify marginalised narratives through automated production; GPT-3 could support co-produced educational stories, but outputs required critical, bias-aware review—not proof of learning gains [181].

2021–23 education chatbots support mentoring, feedback/materials; access/training/pedagogy matter [182]

AI-based apps aided disabled postsecondary learners via transcription/translation; 2021 review: 4 empirical/46 screened, none rigorous [43]. Georgia State's Pounce reduced summer melt >20% (2019) [180]; synthetic-video trial (83 adults, 3 May 2023) found no difference in gains vs traditional (p=.80) [183].

GPT‑4’s March 2023 simulated U.S. bar exam: 298/400 (~90th percentile/top 10%); gain over GPT‑3.5: 80 percentile points on the UBE versus 40 on the LSAT, 36 on GRE verbal, and 0 on GRE Writing [68]. A reanalysis estimated 62nd percentile among first-time July takers and ~45th–48th among qualified attorneys; essay scoring lacked official-rubric, grader-training, and calibration conditions [68]. This is task-capability evidence, not legal competence, teaching effectiveness, or learning: the UBE is general/non-jurisdiction-specific and GPT‑4 effectively had training-corpus “open-book” access [68][71]. GPT‑4’s education applications brought hallucination, bias, privacy, cybersecurity, and overreliance risks; source transparency, uncertainty checks, human verification, and review are therefore required [73]. Post-cutoff records (17 Sep 2023; 26 Jun 2023; 3 Feb 2026) are excluded: they concern ChatGPT references, a GPT‑3 bias-probe course, and GenAI adaptive/access claims [74][185][184].

By 31 May 2023, GPT’s clearest educational opportunity was capability-based, not a proven learning gain: dialogue, drafting, feedback and personalization were demonstrations, not causal classroom outcomes. InstructGPT used supervised tuning, a reward model and PPO; outputs were preferred 85±3% versus 175B GPT-3 and 71±4% versus few-shot GPT-3, and it handled code questions and some other-language instructions. Closed-domain hallucination was 21% versus GPT-3’s 41%; bias did not significantly improve and simple mistakes remained [64].

GPT-4-launch was preferred on 70.2% of 5,214 ChatGPT/API prompts over GPT-3.5 and 61.1% over GPT-3.5 Turbo RLHF; safety tuning cut disallowed responses 82% versus GPT-3.5, and toxic generations were 0.73% versus 6.48% on RealToxicityPrompts [88]. Jailbreaks, hallucinations and convincing errors remained, requiring evaluation and monitoring [88]. Institutional services may be personalized and efficient, but benefits depend on equitable access, bias, provenance and copyright safeguards [41][55][187]. An image-training dataset with child-abuse links marks non-text AI as a safety boundary, not an educational benefit [55].

ChatGPT (Nov 2022): potential personalized learning/access, not measured gains . GPT‑3 (2020; 175B): few-shot summary/translation/code; K–12 plans err [189][190]. GPT‑1 (2018) began GPT; GPT‑2 (2019: 124M–774M released; 1.5B considered) produced fluent, biased, privacy-leaking text; non-Latin failures [190][188][52]. Human review/provenance/AI-literacy [42][189][190].

By 31 May 2023, the evidence here was capability evidence, not a measured educational outcome. GPT models generate human-like responses by extrapolating patterns in human-written data (“next-word prediction”), not formal deduction; this may support dialogue and reasoning practice, but can reproduce human errors [53]. In ETR61 (61 inference/judgment items; 30 March 2023), GPT-3 produced ETR-predicted outputs for 59% and GPT-4 for 75%; fallacious outputs were 18% and 34%, respectively [53]. A pre-cutoff evaluation found GPT-4 generally exceeded GPT-3.5, yet scored 17/30 versus 16/30 on HotpotQA and still struggled with inductive, mathematical, commonsense, and long-context reasoning [67]. Guided prompts are therefore a plausible aid—not proof of improved student learning—and outputs require human verification [67].

GPT-3 (2020) had 175B parameters and few-shot generation for Q&A, translation and drafting—potential educational content use, not measured learning [50]. GPT-4 (March 2023) added nuanced instructions, longer contexts, image inputs (research preview) and stronger benchmarks [62][54]. Its simulated UBE (MBE+MEE+MPT) was reported as 298/400 (~90th percentile; another account gives 297 and 75%); comparison groups alter estimates, so it signals capability, not educational effectiveness [48][63][70].

GenAI/GPT generate text/code/image/audio/video; GPT predicts tokens→fine-tunes [40][49][66]. GPT‑3=175B (2020); RLHF/InstructGPT improved instruction-following/truthfulness, but bias, hallucination and safety persisted [40][51][186]. GPT‑1 (June 2018): lineage; RACE +5.7% ≠ learning [47]. GPT‑4 (2023) orchestration was a demo≠education [89].

## Challenges and Threats in Education

### Fluent errors and misplaced authority

**Plausibility can conceal factual failure.** ChatGPT’s conversational confidence makes incorrect answers harder to recognize, particularly for users who are still learning the subject. OpenAI’s original release acknowledged both plausible-sounding falsehoods and changes in responses following small prompt alterations. In education, these are not merely software inconveniences: an incorrect explanation can establish a misconception that later learning builds upon. [4]

**Fabricated citations are especially damaging.** A reference that looks academically conventional can make an unsupported claim appear trustworthy. The University of Tartu’s April 2023 guidance specifically warned of fictional sources, calculation errors, logical mistakes, and culturally inappropriate responses. A student who accepts such a citation may mistake formal appearance for evidence and reproduce the error in assessed work or research. [21]

**Errors vary across domains and tasks.** Rahman and Watanobe’s review described mathematical evaluations in which ChatGPT understood questions but failed to provide correct solutions, alongside stronger results on some medical examination tasks. Their own programming experiment also showed how success depended on the evaluation standard. The practical risk is inappropriate transfer of trust: competence demonstrated in one area may be assumed in another without justification. [12]

**Training knowledge is not live verification.** OpenAI stated that the vast majority of GPT-4’s pretraining data ended in September 2021. User-provided context or connected systems can change what information an application can use, but a model’s fluent answer does not establish that it has consulted current authoritative evidence. Questions about new regulations, recent research, or institutional arrangements therefore require suitable external grounding. [5]

**Asking twice does not establish truth.** Regenerating a response, requesting confidence, or asking a model to check itself can produce a revision without providing independent evidence. Indeed, a model can repeat or elaborate an error. Educational verification must involve something outside the generated assertion: an actual source, a valid derivation, an executable test, or qualified human judgment.

**Improvement can increase misplaced trust.** GPT-4’s system card identified a consequential paradox: as models become more convincing and more often correct, users may become less attentive to the remaining errors. The danger is greatest when a learner lacks enough subject knowledge to recognize a subtle mistake. Better average performance therefore does not remove the need to preserve habits of checking and questioning. [3]

### Bias, cultural representation, and unequal quality

**Bias can affect both content and opportunity.** Generated examples may reproduce gender, racial, cultural, religious, or linguistic stereotypes. When AI is used to support grading, admissions, intervention, or disciplinary decisions, biased outputs may also influence the allocation of educational opportunities. The U.S. Department of Education emphasized that discrimination must be examined during deployment as well as during initial system design. [1]

**Representation shapes what appears normal.** Cambridge researchers discussed a reported example in which a request for ten famous philosophers returned ten white men. This is an illustrative output rather than a population-level audit, but it exposes a curricular mechanism: a seemingly neutral list can silently define whose ideas count as central. Repeated use of such defaults could narrow educational perspectives unless teachers actively examine omissions. [14]

**English-centered development creates additional risks.** OpenAI’s GPT-4 system card stated that most pretraining and alignment data were in English and that safety work was conducted primarily in English from a U.S.-centered perspective. It also acknowledged that many external testers had ties to English-speaking Western countries. Consequently, even a system that performs well on some multilingual benchmarks may handle local meanings, cultural expectations, or safety boundaries unevenly. [3]

**Standardization can amplify an unexamined bias.** If one flawed example appears in a single worksheet, the impact is limited. If an institution repeatedly distributes model-generated materials or uses the same automated rubric across many courses, the assumption can spread widely. The issue is therefore not only whether an individual answer is offensive, but whether routine adoption normalizes a narrow account of knowledge and achievement.

**Prompts alone are an incomplete remedy.** Asking for a more diverse answer may improve one response, but educators still need relevant subject knowledge, local sources, and affected learners’ perspectives. A defensible response combines output review with attention to institutional practices. Otherwise, apparent technical neutrality may obscure choices about curriculum, language, and whose experiences are recognized.

One analysis reported that 93% of GPT-3’s training data were in English and that its embedded values appeared to reflect an American sociocultural worldview, reinforcing the need to examine linguistic and cultural representation in educational materials.

### Privacy, cybersecurity, and child protection

**Personalization can invite excessive disclosure.** A student may provide details about health, disability, family circumstances, learning difficulties, or assessment results to obtain a tailored response. Teachers may upload student work or records for convenience. The educational benefit of context must therefore be weighed against whether that information should enter an external system at all.

**The chatbot is not its privacy policy.** Tlili and colleagues reported a revealing user-experience scenario: OpenAI’s FAQ described conversations being stored, reviewed, and used to improve the system, while ChatGPT itself denied storing conversation data. The appropriate institutional lesson is to rely on contracts, policies, and documented technical arrangements—not on generated statements about the service’s own operation. [22]

**The risks had concrete institutional examples.** Regulatory action, a service breach, and school ransomware incidents illustrated different failures involving personal information. They should be distinguished rather than treated as one common incident category.

| Case | Date or reporting period | Documented concern | Educational implication |
|---|---|---|---|
| Italy’s Garante order [23] | 31 March 2023 | Processing basis, transparency, accuracy, age checks | Review lawfulness and child safeguards |
| ChatGPT breach reported by Biola [24] | March incident; May notice | Sensitive/payment information; reported 1.2% of subscribers | Require contractual and breach protections |
| Minneapolis school ransomware case [25] | March 2023 incident | Sensitive records extending back to 1995 | Minimize retained educational data |

**Italy’s action concerned more than cybersecurity.** On 31 March 2023, the Garante imposed an immediate temporary limitation on OpenAI’s processing of Italian users’ data and opened an inquiry. Its concerns included transparency, the apparent absence of an adequate legal basis for large-scale personal-data processing, inaccurate personal information, and the absence of age verification. Educational institutions must therefore distinguish technical protection from lawful and appropriate use. [23]

**Informal adoption can precede institutional control.** Biola University’s 15 May notice reported 83,000 ChatGPT visits from its network during April and 26.7 gigabytes uploaded since January. These were network visits and data volume, not counts of unique users or sensitive records. Nevertheless, they showed how substantial use could develop while an institution lacked data-protection and breach agreements with the provider. [24]

**School breaches show why retention matters.** The Minneapolis ransomware incident was not presented as being caused by generative AI. Its relevance is the sensitivity and longevity of educational data: disciplinary, special-education, and maltreatment records can remain harmful long after their original collection. Adding conversational systems without clear deletion and retention rules could create another location in which sensitive information accumulates. [25]

**Cybersecurity includes misuse of generated content.** OpenAI’s system card identified assistance with some social-engineering tasks, including drafting realistic phishing messages, while also describing substantial technical weaknesses. In an educational setting, this creates a plausible additional route for impersonation, fraud, and credential theft. Generated code can introduce vulnerabilities as well as help identify them, making review essential before institutional deployment. [3]

**Children require more than general guardrails.** A system designed to refuse harmful requests can still produce inappropriate or misleading responses. The World Bank specifically warned about unsupervised tutoring that fabricates information or leads to disturbing conversations. Schools must preserve adult supervision, age-appropriate arrangements, and routes to qualified human support, especially when conversations concern wellbeing. [13]

### Academic integrity and assessment validity

**Unauthorized substitution threatens more than originality.** When students submit generated essays, code, or examination answers as their own, the problem is not simply textual resemblance to another source. The assessment may cease to demonstrate the student’s knowledge and skills. Maastricht’s February 2023 examiner guidance connected this directly to whether academic credit could legitimately be attributed to the student. [26]

**AI use is not inherently misconduct.** Brainstorming, translation, feedback, or code assistance can be authorized learning activities. The distinction depends on the assignment’s purpose and stated rules. Waterloo’s guidance prohibited presenting generated output as original work while allowing instructors to authorize appropriate uses. Clear authorization is therefore part of assessment validity, not merely an administrative detail. [27]

**Existing assignments were already vulnerable.** A May 2023 preprint compared ChatGPT with students across 32 university-level courses and found comparable or superior performance in many courses. An engineering benchmark involving ten subjects across seven Australian universities likewise reported passable responses to many assessments with little prompt modification. These studies show why an acceptable final answer alone can become weak evidence of independent student achievement. [28][6]

**Student surveys describe differing practices.** The *CITE Journal* editorial reported a poll of more than 4,000 Stanford students in which 5% acknowledged submitting ChatGPT material without editing. It also described a separate survey of more than 1,000 students aged over 18 in which nearly half reported using ChatGPT for an at-home test or quiz and 53% for a class essay. These figures concern their respective respondents and differently defined activities; they should not be combined into a sector-wide cheating rate. [15]

**Detection results depend on the denominator.** The May 2023 *Game of Tones* preprint inserted 22 GPT-4-generated submissions into assessment marked by 15 faculty members. Turnitin identified some AI content in 91% of those submissions, but marked only 54.8% of the total content as AI-generated. Faculty referred 54.5% of the experimental submissions to misconduct procedures. These are three different measures, not interchangeable descriptions of detector reliability. [29]

**A detector score does not establish authorship.** The 32-course study reported both human-written answers being incorrectly classified as AI-generated and edited AI text evading detection. The May *IEEE Computer* article similarly warned that minor alterations could defeat detectors and that their outputs should not constitute sole evidence. High-stakes accusations require corroborating evidence and a fair opportunity for the student to explain the work. [28][16]

**Assessment validity requires identifying the intended construct.** If an assignment aims to assess independent argumentation, unacknowledged AI- generated reasoning introduces an alternative explanation for the result. If it aims to assess competent AI-assisted analysis, using the tool may be appropriate, but students must still demonstrate evaluation and responsibility. The same software can therefore invalidate one assessment while forming a legitimate component of another.

**Automated grading creates a separate problem.** Generating a response to an assessment and judging a student’s response are different tasks. The World Bank warned about inaccurate grading and false-positive proctoring decisions. A model’s ability to produce an apparently strong answer does not establish that it can consistently apply a rubric, recognize unconventional valid reasoning, or make fair consequential decisions. [13]

### Overreliance, critical thinking, and creativity

**The crucial issue is displaced thinking.** Generative AI can weaken learning when it performs the mental work that students need to practice. Farrokhnia and colleagues’ 2023 analysis linked overdependence to reduced motivation for independent research, reasoning, creativity, and problem-solving. The mechanism is conditional: the risk arises from how assistance changes learning activity, not merely from the presence of a chatbot. [30]

**Answer substitution removes practice opportunities.** A student who immediately requests a complete solution may bypass interpreting the question, recalling relevant knowledge, choosing an approach, checking intermediate steps, and evaluating the result. Those activities are often the assignment’s educational purpose. Repeatedly outsourcing them can produce polished submissions while leaving independent capability underdeveloped.

**Fluency can distort self-evaluation.** Reading a coherent explanation can feel like understanding it. Yet recognizing an explanation is different from reconstructing or applying it. If students mistake that feeling for mastery, they may stop investigating too early, discover gaps only during an independent assessment, or become increasingly dependent on the system for reassurance.

**Novices face a particular verification burden.** The user most in need of help may also be least able to identify a confident error. A March 2023 survey of 110 first-year aerospace-engineering students in Spain reported confidence in ChatGPT responses at 3.4 on a five-point scale and general learning use at 3.61/5. These are perceptions rather than accuracy measurements, but they illustrate the importance of teaching evaluation alongside access. [31]

**Creativity can be expanded or narrowed.** Generating alternative approaches can help a learner move beyond an initial idea. Conversely, accepting the first plausible output can anchor the learner to generic formulations and discourage exploration. The two-week undergraduate study’s reflections included both efficiency and knowledge-gap benefits, and concerns about generic responses and lack of innovation. [10]

**Structured critique changes the mechanism.** A learner who must identify errors, compare sources, challenge assumptions, and justify a revised answer is practicing judgment rather than merely receiving text. UNESCO’s Socratic-opponent role and Tartu’s recommendations for evaluating chatbot responses offer concrete ways to create such activity. The same generative capacity that enables shortcuts can therefore supply material for critical examination. [9][21]

**Teacher dependence can reproduce the problem.** If educators accept generated plans or feedback without sufficient subject and pedagogical knowledge, the technology begins to determine instruction. Teachers College’s Paulo Blikstein warned against reliance before developing expertise in teaching, classroom management, and lesson design. Professional judgment becomes more important, not less, when persuasive drafts are easy to obtain. [32]

### Unequal access and unequal benefits

**A free interface does not ensure equity.** Effective use requires an appropriate device, reliable connectivity, sufficient language proficiency, digital skills, and time to learn the tool. Paid access can add differences in availability and capability. Existing digital inequalities therefore provide useful indicators of who could be excluded, even though they do not directly measure ChatGPT access.

**Historical access measures show substantial differences.** The following estimates calculate the complement of reported exclusion rates. They are regional device or broadband proxies, not estimates of global AI readiness.

| Population and period | Access barrier reported | Access complement, estimated | Measurement basis |
|---|---|---|---|
| UK households with children; 2020 survey | 9% lacked laptop, desktop, or tablet | 91% had such a device | Household device access |
| UK semi-skilled/unskilled-earner households; 2020 survey | 21% lacked such a device | 79% had such a device | Household device access |
| California Latino students; spring 2021 | 40% lacked reliable broadband | 60% had reliable broadband | Reported connectivity access |

**The calculations preserve their original scope.** The estimates are 100% − 9% = 91%, 100% − 21% = 79%, and 100% − 40% = 60%. The UK figures imply a calculated 12-percentage-point device-access gap between the two household groups. The UK source separately reported 4% smartphone-only access; that category should not be added to the no-computer figure as though it were a distinct population. [33][34]

**Service restrictions add another layer.** UNESCO IESALC’s April guide described ChatGPT as blocked or restricted in around 30 countries and reported ChatGPT Plus at US$20 per month. It also noted differences in response reliability between languages. Consequently, identical instructions to “use ChatGPT” could create materially different learning conditions across countries, institutions, and households. [9]

**Benefits also depend on institutional support.** A well-resourced institution can provide training, reviewed materials, approved accounts, and specialist assistance. A student using a public service alone may receive the tool without those protections. This creates a second divide beyond connectivity: unequal capacity to turn access into safe, educationally useful participation.

**Blanket restrictions can have unequal effects.** Blocking a school network may reduce immediate use on institutional devices while leaving privately connected students able to continue elsewhere. Teachers College’s Renzhe Yu described bans as a realistic short-term response but not a durable solution. Where restrictions are necessary, institutions should therefore consider their distributive consequences rather than assuming that all students are equally constrained. [32]

### Educator roles, accountability, and research integrity

**Tasks and professions must be distinguished.** Generating a quiz or drafting feedback is a component of teaching, not the whole profession. Teachers interpret learner needs, manage classroom interaction, exercise disciplinary judgment, safeguard welfare, and develop relationships. The World Bank’s distinction between lesson preparation and delivery is especially important when considering proposals to use AI in systems facing staffing pressures. [13]

**Augmentation changes rather than removes expertise.** Educators may spend less time producing routine text and more time selecting, checking, adapting, and explaining it. That shift can improve professional work if institutions provide time and support. It can also intensify work if teachers inherit responsibility for large volumes of unreliable material while losing discretion over how tools are used.

**Accountability cannot be assigned to fluency.** A generated recommendation does not explain who should answer for an unfair grade, a privacy violation, or inappropriate advice. The U.S. Department of Education therefore emphasized educator agency, inspectability, explanation, override, and human alternatives. Institutions remain responsible for deployment decisions even when the underlying model is supplied commercially. [1]

**Research assistance introduces related obligations.** Fabricated references, inaccurate summaries, unclear provenance, copyright concerns, and unacknowledged AI- generated text can damage scholarly integrity. The May *IEEE Computer* article argued that human authors remain responsible because AI tools cannot bear accountability for misconduct. Citing use of a tool does not turn its assertions into research evidence or remove the need to consult original sources. [16]

**Risk judgment: preserve the source of competence.** The central threats arise when persuasive output is mistaken for verified knowledge, student work, fair judgment, or professional responsibility. Responsible adoption must keep those distinctions visible.

**Additional documented evidence**

**Reliability and verification**

By 31 May 2023, evidence already showed that ChatGPT-like systems could produce confident, compounding errors [251][103]. On 22 May 2023, ChatGPT and GPT-4 produced incorrect answers plus erroneous justifications in three question-answering datasets (primality, U.S. senators, and graph connectivity). “Hallucination snowballing” means defending an initial error with further errors; separate re-evaluation recognized 67% of ChatGPT’s and 87% of GPT-4’s errors, but this conditional recovery did not establish reliability [251]. On 11 May 2023, a single introductory-physics case study found errors in 25 of 51 numerical homework problems, including omitted units and poor recovery after correction [103]. In education, explanations, calculations, and feedback therefore need independent conceptual, dimensional, and source checks; backtracking and step-by-step prompts may reduce, not eliminate, compounded errors [251]. These task-specific findings are not population-wide learning outcomes.

ChatGPT’s reliability threat was plausible error: it could give wrong answers, invented references, and biased or outdated content while sounding confident. Pattern prediction and instruction alignment imitate plausible language, not facts; prompt-sensitive limits in context, reasoning, and knowledge make outputs variable. Human review and primary-source checking were necessary [90] [159].

Students could outsource essays or exams, making hidden use unfair and obscuring learning. One ChatGPT essay scored 4% plagiarism in Grammarly Professional, but that score did not establish authorship or originality [159]. Under a cited U.S. rule, wholly machine-generated text lacked copyright absent human creativity; Nature required disclosure and rejected AI authorship—neither universal law [90]. Overreliance can replace writing-as-thinking and independent practice; process-rich or oral/reflective assessment is safer than detector-only enforcement. Automation may reduce routine work, but verification adds educator workload; evidence shows mechanisms, not prevalence or causal learning loss [159].

Bias/exclusion: biased training data/classifiers can flag African-American English as toxic, while toxicity-avoidance systems may suppress it; Western/English-centric mitigation can marginalize local languages [252][226]. GPT-3 may inherit gender/racial bias from unfiltered data; demographic reporting was sparse (9/118 studies) [111].

Reliability/integrity: ungrounded token prediction permits misinformation despite retrieval; controlled-decoding safeguards may be reversed for hateful or persona-manipulating outputs [252]. ChatGPT enables AI-written submissions/exam cheating, weakening authorship/validity; detectors can falsely accuse students [178][111]. Fluency may foster learner dependence; long-term effects remain unresolved [226].

Governance/equity/safety: GPT-3 APIs expose outputs, not training data; rapid deployment can outpace mitigation, so institutions need layered checks [252]. Commercial GPT-3 costs and connectivity divide access: January 2023 penetration was 64.6% globally, 97.3% in Northern Europe, and 23% in some African countries [111][178]. Harmful-content research supports safeguarding concern, not school-specific incidence [252].

By May 2023, Generative AI could produce unreliable, unfair recommendations when data quality, population fit or measurement was poor [42]. GPT-3 evidence included gender/representation bias; unconstrained LLMs could produce racist/extremist outputs or polarisation, while access/language effects remained gaps [131]. U.S./Canadian institutional sites recorded ChatGPT-use policy questions, not misuse prevalence or learning outcomes [233]; labor evidence was general [131].

ChatGPT’s uncited or fabricated output enables plagiarism and unauthorized assistance; University of Sydney: 8% of 2022 contract-cheating allegations, hundreds referred [253]. UK postgraduate module: 10–15% of fails involved suspected dishonesty [235]. Detection, privacy and copyright are unresolved [108][222]. Learners risk dependence and unequal access; educators risk errors and monocultural feedback [101]; English-LLM environmental costs burden the Global South [236].

ChatGPT—hallucinations/fabricated citations, bias, poor reasoning/common sense: verify ([114],[215]). Higher-ed misuse: plagiarism/unauthorised assistance; authorship/assessment challenged; weak detectors (66% tool/68% human, n=50; neither consistent) ([157],[169],[119]). Overreliance may erode critical-thinking/writing/problem-solving; code 95.83% compiler/75% AOJ/85.42% mean ([114]). Privacy/accountability/equity/environmental risks persist; 2023 operation ≈23 kg CO₂e/day, training excluded ([157]).

ChatGPT, 31 May 2023: misuse included whole essays, paraphrase/auto-cite and undisclosed assistance [158]; Jan-2023 survey (>1,000 university students) found >⅓ used it in assessment writing; 75% of them deemed it cheating [160]. Generated work obscures authorship; scoring suffers [158]; overreliance may displace writing/critical thinking [158][217], and GPT-3 may reproduce bias [245] (not causal).

ChatGPT enables cheating; 1 edit→detector:24% fake, threatening validity/authorship. Overreliance, misinfo/manipulation, privacy/bias/inequity may harm learners/schools; use process/oral assessment; verify [168].

By May 2023, ChatGPT risks error, bias, cheating, reliance and plagiarism; verify, disclose, redesign assessments. [113][208]

GPT-3-era text can be fluent yet wrong, with fabricated references; copied submissions obscure authorship and learning, while detectors miss paraphrase [200,353]. Uncritical use may outsource student writing and thinking, reducing practice and critical thought; this is plausible, not causal [94]. Educators must verify sources and retain judgment [219]; unequal digital skills may widen gaps; copyright and provenance remain unclear [80].

ChatGPT may make learners passive: fluent errors can weaken critical evaluation/practice; 2023 physics testing found polished contradictory errors [234][102]. This is plausible, not causal evidence: training bias, input/language, learner competence and support design moderate it [234]. A 2021 university EFL study (50/53 students) found reflective AI-writing improved writing, self-efficacy/self-regulation and reduced cognitive load [254]; earlier work found deliberate practice helpful, but permanent prompts could become redundant/overwhelming [255][105]. ChatGPT writing raises plagiarism, authorship/copyright and provenance risks; assignment harvesting is unproven [225]. Disclose/check; retain human oversight [225][46].

By 31 May 2023, ChatGPT posed plausible—not proven—risks: false, biased outputs, privacy risks, cheating, overreliance and reduced practice [152]. A May higher-education survey found teachers more concerned than students about errors/bias and overreliance [229]. OECD warned cognitive offloading may displace reasoning; preserve process evidence and verify outputs [152].

By May 2023, ChatGPT-like systems posed hallucination, bias, misinformation, cheating, privacy, and copyright/attribution risks [209]. GPT reasoning remained fallible: ETR61 fallacies (30 March 2023) were 18% (GPT-3), 33% (GPT-3.5), 34% (GPT-4); an ETR prompt blocked 14/17 GPT-3.5 cases versus 4/17 control (p=.0045) [53]. GPT-2’s education risk remains unresolved; generated text can obscure student thinking and sources [84].

ChatGPT (higher ed.)—students may use AI for essays/exams; AI text may evade plagiarism tools, undermining assessment (concern, not prevalence) [232]. Substitution for human creativity may reduce critical-thinking practice; causality is unmeasured [232]. ChatGPT privacy: services may collect pupil/location/IP/device data, share/retain it; verify no-training/protection with a DPO/IT [256]. April 2023 evidence adds absent consent, contextual-integrity/deletion, copyright and Turnitin’s indefinite storage [257]. ChatGPT: English works best; language/country access vary; connectivity, cost and US$20/month access divide users; age uncertainty risks inappropriate exposure for minors [232]. UK institutions face inaccurate/biased outputs, purpose creep, inferred/special-category data and time/expertise barriers [241]. GPT-4/GPT-1/non-text: unresolved.

Provider data raises provenance, consent, retention and ownership risks; paid access and biased training can exclude minority learners [230][248]. ChatGPT’s age rule is 13, with guardian permission below 18; age-inappropriate output, manipulation and prompt injection threaten child safety [230][40]. ChatGPT enables essay/test cheating and undermines evidence of learning; overreliance and automation bias can deskill users [40]. Opaque, fluent outputs can spread hallucinations, misinformation, phishing and malware; in 2023, reviewers detected only 63% of ChatGPT-generated fake abstracts [40][69]. Australian HE: 8 universities (20%) had policies referencing AI after 75 days; 14 (36%) after 100 [248]. ChatGPT is text-first; other tools add sound, images/video and need separate review [69].

ChatGPT’s threats include harmful, unreliable/biased information, plagiarism, privacy/security exposure, overreliance and reduced motivation; human interaction remains necessary [260]. In university courses, educators treated use as plagiarism and detectors were unreliable [76]. Unequal devices, broadband, skills and paid access can widen inequity [258][250][259].

By May 2023, evidence showed risks, not causal education outcomes: ChatGPT could hallucinate citations, enabling plagiarism and outsourced homework; detectors were inconsistent (89.2% average accuracy) [205,192,390]. Overuse may erode writing practice and critical evaluation; retain unaided work and human review [253,586]. Bias, unequal access and design gaps can marginalize learners [1,253,440]. Teacher work may shift to verification [261].

Educators face a workload trade-off: in January 2023, one teacher reported saving more than an hour with ChatGPT lesson paragraphs, but factual errors, post-2021 limits, bias, weak tailoring and required review mean automation transfers, rather than removes, professional judgment [221]. For learners, ChatGPT enables cheating and confident misinformation; use by both sides may weaken teacher–student trust [262]. GPT‑1 was not trained for factual output, could propagate stereotypes and generalize brittly; training took 1 month on 8 GPUs (0.96 petaflop-days), with carbon emissions unknown [263]. The cited education review was argumentative, not a controlled outcome study [93].

By 26 April 2023, a study of 50 original and 50 ChatGPT-generated medical abstracts found the GPT-2 detector reached AUROC 0.94 (86% sensitivity; 94% specificity), while reviewers misclassified 32% of generated and 14% of original abstracts [139]. In an educational grading task, ChatGPT’s accuracy on 5,142 self-explanations was 0.75, with 1,118 false positives, 170 false negatives and κ=41.2%, apparently using keywords rather than reasoning [59]. OpenAI warned detectors were unsuitable for high-stakes student judgments: false positives may burden English learners and formulaic writers, and small edits evade them [216]. Fabricated outputs and answers may foster overreliance and weaken critical thinking, a plausible but unmeasured learning risk [139][61].

Fluent output can be unreliable: GPT-2 cannot distinguish fact from fiction and reflects training bias; GPT-3 loses coherence, underperforms in underrepresented languages, and produces stereotypes [197][51]. GPT-3 could lower barriers to fraudulent essays and make synthetic authorship harder to detect [201]. A GPT-2 study found 1,193 plagiarized sequences (388 verbatim, 507 paraphrase, 298 idea); nearly 28% included location data and a person’s name, while extraction also recovered personal information [192][52]. GPT-4 scored 19 percentage points above the latest GPT-3.5 on an internal factuality test in April 2023, yet hallucination, harmful content, and persuasive disinformation remained possible [48]. InstructGPT was not fully aligned or safe; its approximately 40 feedback contractors were nonrepresentative [51]. GPT-3’s 175B-parameter training used several thousand petaflop/s-days [201]. Image-training data containing child-abuse links illustrates a possible non-text safety risk, not proof of model influence [55].

Evidence remains immature: a 2019–2022 K–12 review found 28 studies among 8,175 records, while an EdTech review found small samples, heterogeneous effects, and no causal evidence for some outcomes; these are mechanisms rather than measured learning effects [246][243]. Educational institutions in a Swedish school-cloud study faced security, privacy, and GDPR barriers [264]; GPT-2 documentation warned that automated detection had not reached >99% accuracy and advised human judgment [188].

GPT models: GPT‑4 is unreliable—hallucinations, reasoning errors, bias, over-reliance, privacy/cybersecurity and harmful advice persist; high-stakes use needs review [195]. ChatGPT launched text-only, without web/image/code/memory access, knowledge ending in 2021; prompt-sensitive errors threaten online-exam integrity [198][79][207]. GPT‑3’s next-token objective yields fabricated, biased/toxic text and instruction failures; InstructGPT reduces hallucination/toxicity but retains mistakes/bias [64]. Learners face outdated or biased output, unauthorized help, unequal access and integrity harms—not learning outcomes [240]. GPT‑1’s opacity leaves provenance/explainability and copyright attribution unsettled [272][41]. GPT‑2 retains corpus bias and weak text; fake reviews can enable scholarly fraud [200]. RLHF/InstructGPT reflects English-speaking labelers; adversarial prompts expose residual behavior, so humans remain accountable [271][267].

Documented GPT-3 risks included misinformation, spam/phishing, fraudulent essays, social engineering, toxic language and plagiarism [193]. Biased training data can produce discriminatory outputs and marginalize minority knowledge; overreliance on easy answers can reduce independent investigation and critical thinking [143]. GPT-2’s repetition, world-model failures and poor technical performance show that fluency is not reliability [268]. In March 2023, GPT-4’s UBE evaluation reported 75% (versus a 68% average), the 90th percentile and 297 points; it was a zero-shot benchmark, not an administered exam or learning measure [63]. Institutions face student-data misuse and breach risks [265]; generated content may reproduce copyrighted material without clear attribution or settled liability [199].

By May 2023: Institutions: privacy/consent, surveillance, bias, cyber and third-party/cloud-data risks; audits, breach plans and pilots [247][266][244]. Learners: errors/fabrications, ChatGPT overreliance, privacy/agency, integrity, unequal access and disability/language exclusion; risks are potential [206][212][242][43]. GPT‑2: fluent but unreliable/bias-prone text [270][269][238]; InstructGPT: RLHF improved following but still fabricated facts and reflected one group [204]. Non-text modalities existed by 2023; govern safety separately [273][191].

Multimodal AI risks deepfakes, misinformation, harmful content [211]; ChatGPT hallucinations make overreliance risky [202][98].

Institutions: access[239].

ChatGPT can produce plausible but wrong explanations, fabricated citations, calculation and logic errors, and feedback that hallucinates a learner’s answer [90][224][99]. Its training makes it mimic plausible human responses at the expense of correctness, while prompt sensitivity and hallucination snowballing make extended educational dialogue unreliable; calculation errors occurred in 25 of the 51 numerical problems, so educational outputs require verification [90][103][224][251].

ChatGPT-generated essays can be submitted as students’ own work or used to cheat in exams; assessors may not distinguish them from student submissions, allowing apparent learning outcomes without acquired knowledge, while non-plagiarized prompted text bypasses similarity checks [113][178][213]. This undermines assessment validity, authorship attribution, learning measurement and academic-integrity enforcement, so Educational institutions and educators should use contextual tasks, checkpoints/process records, oral or digital-free performance, and explicit authorship disclosure rather than detection alone [218][219][213].

Generative AI and ChatGPT can offload summarizing, expanding, improving and connecting ideas [231]; students may generate code that meets specifications without understanding it, replacing independent writing, research, critical-thinking, problem-solving and metacognitive practice with acceptance or editing [220][214][237][161]. Studies should distinguish passive substitution from ethical, teacher-guided assistance and account for conceptual understanding: ethical use can save time without harming outcomes, and RECIPE uses summarizing, dialogue and revision [223][146][103].

Using the digital-divide framework—devices and connectivity, affordability, skills and digital literacy—Generative AI can widen inequality: students without reliable internet or resources may be unable to use chatbots, while affluent or educated students may have greater access and familiarity [227][250][153]. ChatGPT’s $20/month premium tier [224] gives paid users more privileged, faster and less-limited access than free users [101]; assuming home access or banning tools can privilege already connected students, so institutions should provide suitable tools and skills support to learners and educators [101][249].

ChatGPT can reduce Educators’ routine workload in lesson planning, content creation, reporting and administration, with reports of saved time and less out-of-hours work [228][221]. The evidence distinguishes these task-level savings from new review and training work but gives no net-hours comparison: institutions must adopt new assessment and feedback practices and check generated grading, while automation may replace tasks, threaten job security and erode teaching’s creative and relational autonomy; required skills therefore expand to algorithmic awareness and knowledge of limits, bias and misinformation [213][261][228][221].

Through May 2023, Generative AI’s principal educational risk was plausible but false, fabricated, outdated or misleading content, including invented references; opaque training data add privacy, copyright and bias risks [210][55]. A 102-student evaluation found misleading ChatGPT answers rated similarly to an expert solution [194], implying supervised, source-checked use rather than treating generated material as evidence or autonomous feedback; backtracking and step-by-step prompts may reduce, not eliminate, compounded errors [251].

Through May 2023, GPT models posed an educational risk of unreliable output—hallucinations, reasoning errors, bias, disinformation and over-reliance—alongside privacy and cybersecurity, plagiarism and substantial resource demands [196][205][192][203]. Applying a GPT Educational-Risk Taxonomy of reliability, social/integrity and resource-capacity risks implies that institutions should use model documentation, interpret benchmark and intervention metrics, monitor applications and collect feedback before educational deployment [272][196].

## Response Strategies and Recommendations

### Establish a shared baseline before expansion

**Combine institutional safeguards with course-level judgment.** Institutions should set non-negotiable requirements for privacy, accessibility, due process, and accountability, while allowing educators to determine task-specific permissions. This responds directly to the evidence: low-stakes drafting and dialogue can be useful, but consequences vary sharply with the intended learning outcome, learner age, data involved, and assessment stakes. UNESCO IESALC and the University of Wyoming both supported coordinated, context-sensitive responses. [9][35]

**Use an explicit implementation sequence.** The following sequence is a recommendation derived from the opportunities and risks already discussed, not a claim that one institution had validated a universal model.

| Step | Action | Primary owner | Gate before proceeding |
|---|---|---|---|
| 1 | Define the task, learning goal, stakes, and data | Educator and program leader | A clear educational purpose |
| 2 | Publish permission and disclosure rules | Course coordinator | Students understand the boundaries |
| 3 | Approve tools and data controls | Privacy and IT teams | Lawful, secure processing arrangements |
| 4 | Collect process and understanding evidence | Assessment team | Intended outcomes remain assessable |
| 5 | Provide access and accommodations | Institution and support services | A fair alternative for every learner |
| 6 | Review learning, workload, fairness, and incidents | Accountable governance group | Benefits justify continued use |

**Temporary restraint remains legitimate.** A particular use should pause when appropriate data protection, supervision, accessibility, or assessment validity cannot be secured. That is different from treating every use of generative AI as equally unacceptable. Conversely, permission for brainstorming should not be interpreted as permission for autonomous grading or unrestricted uploading of student information.

### Publish clear classroom and assessment policies

**Rules should describe activities, not slogans.** “AI is allowed” and “AI is banned” are insufficient when one course contains brainstorming, drafting, feedback, programming, and independent examinations. Educators should state what is permitted, prohibited, dependent on prior permission, and subject to disclosure for each major task. Wyoming’s February report supplied alternative syllabus approaches precisely because a single policy was unsuitable across all courses and modalities. [35]

**Contemporary policies illustrate practical alternatives.** Institutions had already begun distinguishing support for learning from misrepresentation of assessed work.

| Institution and guidance | Approach to use | Transparency requirement | Assessment response |
|---|---|---|---|
| Wyoming, February 2023 [35] | Course-sensitive templates | Varies with adopted template | Instructor adaptation |
| Tartu, 28 April 2023 [21] | Purposeful use; lecturer discretion | Describe and reference assistance | Process tasks and controlled examinations |
| Waterloo, 2023 memo [27] | Explicit instructor authorization | Do not claim generated work as original | Prefer pedagogical responses where feasible |
| Maastricht FASoS, 7 February 2023 [26] | Specify scope and context | Mark generated text | Verify student learning and identity |
| National College of Ireland, May draft [36] | Assignment brief defines exceptions | Identify and cite quoted AI text | Student authorship remains the default |

**A usable rule names the boundary.** For example, a proposed course policy could permit brainstorming and language feedback, prohibit submitting generated reasoning as independent work, and require a short account of the tool, date, purpose, and extent of assistance. Another assignment could explicitly require AI-generated material for critique. The policy must make clear which capability the student—not the model—must demonstrate.

**Disclosure should reveal consequential assistance.** A brief statement can identify whether AI generated ideas, rewrote language, suggested code, or produced material incorporated into the submission. Tartu recommended describing questions, outputs, and modifications, with relevant material included in an appendix where appropriate. Disclosure should remain proportionate: it should explain the contribution without creating unnecessary collections of private conversations. [21]

**Apply transparency to educators as well.** If teachers use AI to draft feedback or instructional material, students should understand the role of the tool and the human review applied. Trust is weakened when institutions require detailed student disclosure while obscuring consequential automation on the teaching side. Teachers College’s discussion of the educational “social contract” supports making these expectations mutual. [32]

### Design pedagogy that retains meaningful thinking

**Start from the learning objective.** Before introducing ChatGPT, an educator should identify the work students need to practice: recalling knowledge, constructing an argument, interpreting evidence, writing in another language, or testing code. AI assistance is appropriate when it supports that work rather than silently replacing it. UNESCO recommended connecting use directly to course learning outcomes. [9]

**Require an initial student contribution.** One practical routine is to ask students to attempt the task, record their reasoning, and identify where they need help before consulting a model. This makes the assistance purposeful and gives both learner and teacher evidence of the starting point. It is particularly useful where immediate answer generation would otherwise remove the problem-framing stage.

**Ask for critique rather than acceptance.** Students can compare an AI explanation with a textbook, locate an unsupported inference, identify omitted perspectives, or test a generated program against difficult cases. Tartu explicitly recommended evaluating chatbot responses and analyzing the dialogue process. Such activities convert unreliable output into material for exercising disciplinary judgment. [21]

**Retain independent reconstruction and transfer.** After using AI, students should explain the revised answer in their own words or solve a related task without assistance. This addresses the difference between recognizing a fluent explanation and being able to use the concept. The purpose is not to prove that every action occurred without technology, but to preserve evidence that assistance has contributed to learning.

**Keep human collaboration central.** A model can supply a debate position or alternative explanation, but students still need to negotiate meanings with peers and teachers. Group discussion, peer feedback, practical work, and culturally relevant activities also expose assumptions that a private chatbot interaction may leave unchallenged. Xu and colleagues emphasized active, collaborative learning and a balance between technological and human interaction. [18]

### Verify and ground educational outputs

**Grounding addresses a specific failure mechanism.** Providing an approved passage, curriculum statement, or verified dataset can make a generated response more relevant and constrain unsupported elaboration. OpenAI recommended additional context and human review according to the stakes of the application. Grounding should supplement—not replace—checking against the original material. [5]

**Use prompts with explicit instructional constraints.** A teacher might ask: “Using this approved passage, draft questions assessing these learning objectives; provide an answer key and identify where the passage supports each answer.” This is a proposed preparation practice, not a guarantee of correctness. Its value is that the teacher can inspect alignment and support more efficiently than in an entirely open-ended response.

**Check the claim using appropriate evidence.** References should be opened and checked for both existence and relevance. Calculations should be independently worked through; code should be executed and tested; summaries should be compared with the source. Bias review should examine examples, assumptions, and omissions, rather than only checking for explicitly offensive language. These actions follow directly from the errors documented in Tartu’s guidance. [21]

**Match review to consequences and expertise.** A draft discussion prompt and a recommendation affecting a student’s progression require different controls. Where a qualified reviewer cannot adequately inspect the output, the task should not be delegated. Human review must mean an actual capacity to challenge and revise, not a nominal approval step after an automated recommendation has effectively determined the outcome.

### Teach AI literacy through disciplinary practice

**AI literacy includes evaluation and responsibility.** Students need a basic understanding of how generation works, why fluent output can be false, how training data can shape responses, and what the system does not establish about its own reasoning. They also need practical skills in prompting, verification, privacy protection, disclosure, and appropriate citation. The May 2023 *IEEE Computer* article explicitly recommended these competencies. [16]

**Teach these skills through actual subjects.** In history, students might examine omitted perspectives and unsupported claims. In programming, they could explain a generated function and design tests that expose failure. In language education, they could compare a rewrite with their intended meaning and identify changes in tone or cultural appropriateness. The disciplinary task supplies the standard against which the output is judged.

**Include privacy in ordinary classroom decisions.** Students should learn why entering a real classmate’s information, a medical detail, or an identifiable assessment record creates a different risk from asking about a public concept. Educators should use non-sensitive examples and explain the approved arrangements before requiring participation. This directly responds to the disclosure risks identified by Tlili and colleagues [22].

**Avoid reducing literacy to prompt technique.** Skillful prompting can improve relevance, but it cannot by itself establish truth, fairness, or lawful processing. A learner who obtains polished output but cannot assess it is not adequately prepared. The stronger objective is informed collaboration: knowing when to use the system, what to check, and when to seek human expertise.

### Redesign assessment using complementary evidence

**Assess both assisted and independent capability.** Educational programs can legitimately teach effective AI use while also requiring students to demonstrate foundational knowledge without it. These are different outcomes and should be assessed explicitly. Maastricht’s guidance recommended ensuring that intended learning outcomes remained visible in the student’s work, including through criticism of AI answers or comparison with specified sources. [37]

**Combine formats according to their strengths.** No format simultaneously maximizes authenticity, authorship assurance, scalability, accessibility, and low cost. A defensible assessment design therefore uses complementary evidence rather than treating one format or technology as universally sufficient.

| Approach | Evidence of learning | Operational requirement | Recommended role |
|---|---|---|---|
| Final take-home product | Sustained writing or problem-solving | Clear assistance rules | Retain with corroborating evidence |
| Drafts and portfolios | Development and revision decisions | Manageable checkpoints and criteria | Show learning processes |
| Oral follow-up | Explanation and responsive reasoning | Staff time and accommodations | Clarify understanding and authorship |
| Presentation or practical task | Application and communication | Suitable setting and fair criteria | Demonstrate performance |
| Proctored examination | Identified independent performance | Access and examination arrangements | Assess selected foundational outcomes |
| AI-inclusive critique | Evaluation of generated material | Shared access and explicit outcomes | Assess responsible assisted work |
| AI-text detector | Statistical text classification | Corroboration and due process | Never standalone proof |

**Process evidence should explain decisions.** Multiple drafts, source notes, peer feedback, and reflections can reveal how an argument or solution developed. However, collecting more files is not automatically informative: students could also generate drafts and reflections. Teachers should focus on meaningful changes, reasons for revision, and questions that connect the process to the final work. Farrokhnia and colleagues recommended portfolios, reflection, self-assessment, and authentic problems. [30]

**Oral assessment adds responsive evidence.** A student can be asked to explain an unexpected result, justify a source choice, or adapt a method to a changed condition. This provides information that a polished written product alone may not reveal. Oral examinations nevertheless require staff time and accommodations, and may be unsuitable as the sole format for high-enrollment courses or some students. [38]

**Authentic tasks remain valuable but not invulnerable.** Local cases, original observations, fieldwork, and recent developments can make assignments more relevant and reduce reliance on generic responses. Tartu recommended several such approaches. Yet specificity alone does not establish independent work: students can provide contextual material to a model. Authenticity should therefore be combined with process evidence and opportunities to demonstrate understanding. [21]

**Program-level arrangements can distribute assurance.** Maastricht’s FASoS Board of Examiners required at least 30% of program assignments to have full student-identity assurance from academic year 2023–2024. Its FPN guidance instead advised a substantial proportion, preferably at least 30%, and described its suggestions as non-mandatory. These were prospective local arrangements issued before the report’s cutoff, not a universal quota or an empirically optimal percentage. [26][37]

**Protect students from detector-only accusations.** An indicator should not be interpreted as a probability that a particular student cheated. Institutions need procedures for reviewing relevant drafts, discussing the work, considering permitted assistance, and allowing an explanation or appeal. The false positives and evasion documented by May 2023 make that protection a condition of fair assessment, not an optional concession. [28]

**Separate grading assistance from grading authority.** AI might help organize comments or draft feedback against an approved rubric, but consequential marks should remain subject to qualified human moderation. Institutions should also examine whether a simpler, more transparent tool would accomplish a bounded task more reliably. Generative capability is not a sufficient reason to adopt generative grading.

### Build governance, privacy, and accountability into adoption

**Assign identifiable institutional responsibility.** A governance group should include educators, students, assessment specialists, IT and security staff, privacy expertise, librarians, and disability-support representatives; school systems should also involve appropriate child-safeguarding and family perspectives. Its purpose is to make accountable decisions about specific uses, not merely publish a general statement of enthusiasm or concern. This follows the participation and human-agency emphasis of the U.S. Department of Education’s report [1].

**Review data flows before procurement.** Institutions should identify what information enters the service, where it is processed, who can access it, whether it is used for model training, and how long it is retained. Agreements should address deletion, security, breach handling, subprocessors, and changes to the service. Personal-data minimization reduces exposure while preserving many public-information drafting and preparation uses.

**Apply relevant legal obligations carefully.** GDPR requirements matter where applicable, while U.S. institutions must address FERPA and other relevant protections. FERPA does not prescribe a particular set of security controls, but the Department of Education warns that breaches can violate student privacy and expose students to identity theft, fraud, and extortion. Consent alone should not be assumed to settle every institutional or child-data obligation. [39][23]

**Distinguish approved services from public accounts.** Biola’s May notice permitted appropriate non-sensitive uses while prohibiting sensitive uploads and describing a locally managed Azure OpenAI service being scoped. That proposal illustrates an institutional response to contractual and security concerns, not evidence that a protected deployment had already succeeded. Institution-managed access can improve control, but its actual terms and technical arrangements still require examination. [24]

**Preserve explanation, override, and human recourse.** A student affected by an AI-supported recommendation should know that AI was involved and have access to a responsible person. Educators need enough information, authority, and time to reject unsuitable recommendations. Where the system cannot be meaningfully inspected or its consequences challenged, high-stakes use is difficult to justify. [1]

**Do not replace safeguards with surveillance.** Institutions should collect only the process evidence needed for a legitimate educational purpose, protect it, and define retention periods. Monitoring adoption must not become indiscriminate collection of private student conversations or intrusive proctoring. The response to one threat—misrepresentation—should not unnecessarily create another through excessive data collection.

### Fund staff development, equitable access, and accommodations

**Training must include difficult examples.** Staff development should involve identifying fabricated references, correcting misleading explanations, testing code, reviewing bias, and adapting unsuitable instructional materials. A workshop that demonstrates only impressive outputs does not prepare educators for responsible use. The World Bank explicitly called for teacher training and “algorithmic awareness,” including knowledge of misinformation and underrepresented languages and countries. [13]

**Provide disciplinary and pedagogical support.** Mathematics teachers, language instructors, research supervisors, and disability specialists face different verification and learning questions. Institutions should support peer mentoring, shared reviewed examples, and collaboration with libraries and teaching-development teams. UNESCO IESALC recommended continuing capacity-building and communities of practice rather than treating adaptation as a one-time technical briefing. [9]

**Protect time for the added work.** Review, assessment redesign, student guidance, and policy interpretation require resources. Institutions should not assume that faster generation immediately compensates for these responsibilities. Workload decisions should consider the complete workflow, including correction and dispute resolution, while preserving educator agency over instructional choices.

**Equal access requires concrete provision.** Loan devices, reliable connectivity, institution-supported access, training, multilingual resources, and accessible interfaces can reduce predictable barriers. Offline alternatives remain necessary where connectivity is weak; these may use teacher-reviewed exported material rather than implying that ChatGPT itself works offline. *The Conversation* specifically recommended loaner laptops, subsidized internet, community partnerships, and disability support. [33]

**Required use must not impose private costs.** If an assessment depends on a particular model or paid feature, the institution should provide equivalent access or a genuinely equivalent alternative. Tartu’s guidance also stated that students could not be required to use a tool that forced account creation with a personal email address. These principles connect privacy and equity: an educational opportunity should not depend on purchasing access or surrendering unnecessary personal information. [21]

**Co-design support with affected learners.** Disabled and multilingual students should help evaluate whether a proposed tool actually removes barriers. Institutions should preserve established accommodations and human support, while checking that alternatives assess the same intended learning. Accessibility is demonstrated through usable participation, not through a list of advertised features.

### Decide whether continued use earns expansion

**Measure outcomes that match the purpose.** Tutoring should be evaluated through understanding and transfer, feedback through the quality of subsequent revisions, and preparation support through usable materials and net workload. Engagement and satisfaction matter, but they do not substitute for learning. The two-week undergraduate study’s topic-dependent findings reinforce the need to judge each application in its educational context. [10]

**Examine differences between learner groups.** An average benefit can coexist with poorer service for a language group, inaccessible interaction for disabled students, or greater costs for low-income learners. Institutions should examine who participates, who benefits, and who carries the burden of checking or obtaining access. UNESCO’s proposed institutional audit explicitly included monitoring both effectiveness and equity. [9]

**Set practical continuation and stopping conditions.** Expand a use when it improves the intended educational activity, preserves independent capability, reduces net burdens, and meets privacy and fairness requirements. Restrict or suspend it after consequential inaccuracies, unlawful processing, discriminatory effects, inaccessible assessment, or persistent displacement of intended learning. These are decision conditions, not predictions that benefits or harms will occur at a particular rate.

**Retain the capacity to change course.** Models, commercial terms, access arrangements, and institutional practices can change. Policies should therefore name responsible owners and specify review points, while procurement should preserve access to necessary records and workable alternatives. A decision to adopt a tool should not become an irreversible decision to depend on it.

**The evidence basis remains specific.** This report concerns developments and material available through May 2023. Parameters measure model size; benchmark scores measure model outputs; ratings measure respondents’ perceptions; and the two-week study concerns short-term experiences. Much educational evidence was conceptual, exploratory, or narrowly task-based. The regional access complements are explicitly calculated estimates, while the recommendations are reasoned proposals rather than measured deployment outcomes.

**The educational test is human development.** Generative AI deserves a place in education when it helps learners understand more, participate more fully, and exercise better judgment, while helping educators teach responsibly. Its place should shrink when it substitutes persuasive output for those achievements. Through May 2023, the defensible direction was supervised augmentation: preserve teachers’ expertise and learners’ agency, verify consequential claims, assess meaningful understanding, and make access both safe and fair.

**Additional documented evidence**

**Capacity, oversight and learning design**

By 31 May 2023, the defensible response to **Generative AI** was conditional integration, not automatic adoption or blanket prohibition: define a narrow learning purpose; train educators and learners in operation, limitations, accuracy, bias, privacy and pedagogy; require corroboration and human oversight; and review results [94][165][311]. This is an evidence-informed recommendation, not a measured causal effect.

**Educators and ChatGPT.** Educators need demand-oriented, case-based professional development, open resources and peer communities covering prompting, failure recognition, multiple authoritative sources, subject-expert review and fact-checking [94]. The teacher remains the expert: ChatGPT outputs, feedback and materials should be checked, edited and refined, never accepted unsupervised or presented as human-authored [94][311]. A 2023 survey of 147 teachers found more positive reported views with more frequent use (Spearman \(r_s=.37, p<.05\)); this association does not demonstrate better learning [165].

**Curriculum, access and assessment.** Schools and universities should teach AI and source literacy, using ChatGPT to generate hypotheses, perspectives, questions or debate prompts, then corroborating claims with books, articles and authoritative sources; generated text is a starting point, not evidence or a substitute for cognitive work [94][302][311]. Institutions should state permitted uses, acknowledgment and accountability rules, and provide access alternatives, connectivity support and accommodations so learners without tools are not penalized [165][311]. Assessment should emphasize drafts, process evidence, authentic or complex tasks and oral defense or viva rather than detector-only enforcement [311]. The U.S. bar-exam benchmark should retain its test conditions and be treated as model-capability evidence—not proof of student learning—so educational decisions rely on direct learning evidence [276][311].

By 31 May 2023, Generative AI’s defensible educational response was guided, human-led use—not prohibition or uncritical adoption. Educators should teach AI literacy as “understand, access, prompt, corroborate, incorporate”: capabilities and bias, appropriate use, effective prompts, fact-checking, and ethical disclosure [163]. For second-language learners, unequal linguistic and financial capital means absent guidance can deepen inequality [163]. Teacher preparation should combine technical and human dimensions, continuing professional development, critical thinking, authorship, source evaluation, and learner agency [226].

Educators should use ChatGPT as an adjunct: check facts, citations, calculations, bias, and privacy because fluent outputs may contain fictional sources and errors; users remain accountable [339]. Lesson plans, questions, summaries, and tailored materials are aids, not measured learning gains: teachers should verify facts, age/ability fit, pedagogy, accessibility, and harmful or age-inappropriate output [315][226][289].

Institutional rules should state course permissions or prohibitions, require disclosure of prompts, outputs, model/version, and modifications, and use fair procedures; detection is difficult, so a 3 April 2023 report of an innocent-student flag does not justify detector-only misconduct decisions [339][289]. Require consent before personal-data entry; do not compel personal-email accounts or paid tools [339]. Pre-cutoff examples—Maastricht examiner guidance (7 February 2023), Sciences Po rules (9 February), EU Commission guidance (31 May), and Italy’s 31 March data-protection action—are identified, but the supplied records do not reproduce their provisions or outcomes [289].

Before adoption, institutions should test bias across diverse groups; address consent, age/ability, privacy, and intellectual property; audit deepfakes, false news, and hate speech; and retain human accountability [315]. Co-design pilots with teachers and learners, compare no-tech alternatives, use task-specific metrics, monitor life-cycle harms, and revise policy [315]. If non-text systems are included, scope them explicitly: by the cutoff GPT-4 accepted image and text prompts, while image systems could approach photographic realism and music systems could reproduce source structure [315].

Educators need pre-use training in bias, digital literacy, lateral reading, fact-checking, privacy and pedagogy; ChatGPT supplements, not replaces, teachers. [109][341] A 2023 qualitative study of 11 language teachers using it for two weeks found roles as interlocutor, content provider, teaching assistant and evaluator, while teachers orchestrated resources and AI ethics—not a causal outcome. [313]

Human users must verify outputs: ChatGPT may make up facts, misunderstand nuance, hallucinate, and produce misinformation, bias or discrimination. [341] Institutions should adopt clear protocols, fund professional development, address access costs, disability, multilingual and training gaps, and consult learners, families and communities. [109][341]

Learners should corroborate outputs, treat AI as a first step, learn digital citizenship, and retain drafts; detectors have mixed results. [109] Pilots should monitor learning, workload, equity, accuracy, integrity, privacy and harms, predefining duration, denominator and comparison group; the guide specifies none. [109]

**Evidence status.** No card in this group supplies cutoff-compliant substantive evidence. [316] is a 2025 study based on Spring 2024; [295] was published 13 June 2024;  is dated 15 February 2024; and [122] is labeled 2023-10/111223. Dates for [112] and [319] are not verified here, so they cannot establish May 2023 evidence.

- **Generative AI/ChatGPT:** AI literacy, responsible use, verification, bias/privacy, integrity, and oversight: **unresolved** [112][295][319].
- **Educators:** training, prompting, pedagogy, assessment, workload, and accountability: **unresolved** [112][295][122][319].
- **Institutions/education systems:** acceptable use, disclosure, procurement, privacy, equity, participation, pilots, monitoring, incidents, appeals, and prioritization: **unresolved** [112][295][122][316].
- **Learners:** agency, access, critical evaluation, and protection: **unresolved** [112][295][122][316].

Later or date-unverified recommendations must not be presented as available by 31 May 2023.

Educators should teach learners Generative-AI/ChatGPT literacy—prompting, regeneration, source checking, self-evaluation, peer feedback, academic honesty and critical reflection—before use [237]. Institutions should restrict ChatGPT to self-learning or supplementary materials, not direct completion of writing tasks/tests, and issue protocols and misuse/plagiarism training [237]. In a one-week undergraduate L2-writing practicum, iterative prompting suggested improved writing efficiency/quality; lecturer observation, screen monitoring, learning logs, collaborative revision, peer feedback and triangulation supplied checks [237]. Integrity, equity and detection-evasion concerns, plus limited authentic-setting evidence, require pilots tracking documented use, source checks and incidents rather than learning gains [237].

Generative AI: educators need training in prompting, verification, bias, privacy/IP and pedagogy, retaining accountability; curricula should teach critical source use, not prohibition [324]. Institutions should co-design, pilot and audit task accuracy, bias/access, privacy/safety, with incident response and policy review [324]. Learners need age limits, agency and practice; non-text tools need safety tests [230].

By 31 May 2023, Generative AI called for governed, teacher-led integration—not blanket prohibition or unrestricted adoption: educators needed training in tool selection, prompting, output evaluation, bias, privacy and pedagogy [174]. Institutions should teach learners to evaluate and discuss generated content, disclose or cite assistance, and preserve human accountability; assessment should emphasize evaluation and reflection rather than content creation [174]. Before deployment, institutions should set ethical-use rules, review privacy, transparency, fairness and accessibility, secure data collection and sharing, and monitor and correct errors or bias [174]. Education systems should ensure access across backgrounds, involve educators, learners and communities in policy design, and refine guardrails through monitoring. Adoption is justified only when educational value does not impose unacceptable integrity, privacy or equity costs [174].

Educators need AI-literacy training, bias checks and oversight; institutions should co-design rules with teachers and students on purpose, use, privacy and misuse, equitable access, procurement and monitoring; learners should verify outputs, disclose use and retain agency [175][300].

Educators, institutions, and learners should build AI literacy, disclose use, verify outputs, redesign assessment, protect data, ensure access, pilot tools with stakeholders, monitor harms, and provide appeals.[310][241]

By 11 May 2023, educators should redesign assessment around process and judgment: learners critique ChatGPT, use graphs, estimates or measurements, and complete tool-free essentials plus tool-allowed tasks where tools are necessary but insufficient; oral exams probe competence [103]. Preserve independent concepts, metacognition and source checking: fluent answers can be false [103].

Educators and institutions should teach AI literacy: source checks, bias/uncertainty, attribution, cognitive off-loading, and human responsibility [215][159]. Use ChatGPT outputs for critique, revision, and reflection—not evidence; verify sources and preserve authentic writing [158][159].

Redesign GPT-3-era assessment with process evidence—portfolios, drafts, screen records, in-class/oral work, and disclosed AI use—aligned to outcomes; verify AI questions in high-stakes work [142][299][158][160]. Test deployments on domain tasks, log errors and equity effects, and require qualified human review [142][299].

Institutions need clear use/integrity rules, training, fair access, and monitoring; revise policy from learning, workload, accuracy, equity, and privacy feedback [159][299]. Among 100 media articles (2020–February 2023), detection appeared in 51 and caught-student examples in 20—not prevalence [160]. Therefore, guided, disclosed use—not outsourcing or bans—protects learning; benchmarks or final products alone are not learning evidence [158][160].

Educators should redesign assessment with authentic tasks, drafts, process evidence, oral/project work, and AI disclosure [301][219]. ChatGPT requires source checks and human judgment; generated rubrics/questions need accuracy/bias review [301]. Detectors miss paraphrase and misflag: pair them with teacher feedback, reference checks and oral follow-up [292]. Institutions should train staff/students; set rules, protect privacy/consent, assess risk, document controls, and contract providers [217][342].

Institutions: ensure access/equity, AI literacy, human review, and policy updates [314][258].

By May 2023, educational institutions should fund devices/connectivity and accessible alternatives; teach digital literacy; train educators; involve students, families and teachers; regulate procurement/privacy; monitor learning, equity and safety—not uptake [330]. This is broad digital evidence, not GenAI outcomes.

By 31 May 2023, institutions should train educators/learners; verify outputs; protect data; redesign assessment; audit bias/accessibility; procure equitably; provide alternatives; enable appeals; monitor harms. [306][240][317]

Education systems pair human-centred, auditable policy with co-design, pilots, monitoring and revision [247]. Institutions provide broadband, offline access; educators teach ethical verification and protect learner agency and equity [247][344].

Institutions: access, safe data, bias review, training, governance, voice; educators guide/verify/redesign; learners literacy/agency/alternatives; pilot accuracy/equity/time [318][304][320]

Generally, institutions should provide device alternatives, accessible formats and human support, and co-design with disabled learners [321][176]; train users in critical use [322][325]. Pilot with diverse users, control groups, and learning, equity, privacy and workload measures [321]. Governance should secure/manage data, publish retention rules, audit, and include students, faculty and privacy officers [335].

For U.S. Title IV schools, the March 2023 guide sets out a June 9 compliance date: assign a security lead, assess risks, safeguard, monitor providers and revise controls [345]. Contracts should cover compliance, records, termination and liability; corrective-action plans record actions, dates and signatures [345].

Institutions should set default/course AI rules, involve stakeholders, and require acknowledgement for unauthorised work [331]; govern data end-to-end—minimise, classify, de-identify and monitor it [265], ensure secure, portable storage [264], and combine flagging/decoding when users lack training-data/compute access [252].

By May 2023, educational institutions should co-design rules; train, verify, protect data, assess vendors, audit and rehearse incidents [232][327][244][266].

Co-design with teachers/learners; retain human judgment; give learners voice, consent and challenge [107][116][242]. Assess access/disability, infrastructure, privacy/security, procurement; pilot learning, workload, bias/harm—what works, for whom, under conditions [107][243]. English n=71: devices 77%, connectivity 73%, cost 72%, staff 68%, budget 66%, safety/data 35%, procurement 13% [243]. Train educators in critical/digital literacy; verify feedback [308][121].

Co-design training with educators and learners [326]. Institutions pilot accuracy/workload/privacy/cyber/harm/integrity; exclude sensitive data [347]. Educators verify outputs; teach prompting, corroboration, disclosure and AI-free practice [104]. Provide access and appeals [334][348].

Generative AI—educators/learners: build source literacy, bias, privacy and rights awareness—not prohibition [332]. ChatGPT: supervised aid; verify outputs and redesign assessment [114][115]. GPT-2/4: document limits; pilot with stakeholders; institutions monitor, offer appeals and revise policy from evidence [111][332].

Educators should teach AI literacy: verify ChatGPT sources, disclose use, log prompts, and defend work; outputs may be wrong, biased or plagiarised, so review remains human [120][81]. GPT-3-era assessment should preserve process evidence and teacher judgement, not rely on detectors with false positives [120]. Before GPT-4-level deployment, institutions should run stakeholder pilots testing readiness, performance, replicability, transparency, privacy, equality and beneficence; GPT-2’s lesson is to document models, prompts, temperature and datasets, test broadly, and revise policy from evidence [120]. Learners need agency, privacy and fair access [274][307].

Educators should teach prompting, source checks, disclosure and authorship; institutions should use process assessment, human review and no autonomous grading [279][225]. ChatGPT personalizes dialogue and gives feedback but may diverge from instructors [144][145]. GPT-1’s 117M-parameter Common Crawl/BooksCorpus record guides documentation; pilots should log prompts, limits, privacy/equity risks, and revise if transfer fails [148][293]. Post-cutoff sources are excluded [74].

Fade AI prompts as competence grows: permanent prompts reduced learners’ strategies, effort and learning [255]. In a 2021 MOOC study (n=150), GPT‑2 matched human community support (79.28% vs 81.42%) but not informational support (11.73% vs 42.85%); learner outcomes were unmeasured [44]. Pilot human-reviewed formative assessment and adversarial tests: GPT‑2 could be steered without internal access [337][351]. Log provenance and audit bias for fairness, accountability, transparency and explainability; protect privacy [42]. Bar-exam validity ≠ educational competence [349].

Claims need source/date/locator; exclude post-cutoff evidence [353]. ChatGPT's 115 references: 47% fabricated, 46% inaccurate, 7% accurate—verify/disclose [287][291]. GPT‑3 assessment: disclose AI; assess process, not output [352]; GPT‑4: pilot before scale, but pilot is post-cutoff [333]. Institutions need roles, privacy and annual review [350]. GPT‑2 needs documented conditions; InstructGPT erred [269][186].

Generative AI: teach educators, institutions and learners limits, verification, bias, privacy and disclosure; protect agency [189][323]. GPT-family monitoring needs held-out human ratings for truthfulness, toxicity, bias and instruction-following: InstructGPT’s closed-domain hallucination rate was 21% versus GPT-3’s 41%, but bias did not significantly improve [64]. Add originality/privacy audits, red-team pilots and incident review; GPT-2’s memorized text and detector error make verification essential [192][52][354]. ChatGPT’s May 2023 beta browsing, Python, uploads and plugins were experimental; verify sources and external actions [286]. GPT-3 assessment needs attribution and verification; GPT-4 deployment needs bounded pilots and revision gates—not educational-effect claims [52][62][354]. Institutions should document model/version, data, intended uses, limits and evaluations; require ethical review and human accountability [263][189]. GPT-1/2 support testing; InstructGPT needs disclosure [263][52][189]. Non-text modalities remain a boundary pending verification.

GPT-family deployment needs layered evaluation—expert/adversarial, truthfulness/toxicity/bias checks, multilingual review, abuse monitoring and iteration; alignment is insufficient [88][205][204]. GPT-4 mitigation reached about 60% TruthfulQA accuracy versus 30% earlier—a factuality, not learning, proxy [88].

Education systems should pilot GPT-4 tools with approved data, domain tests, red-teaming, monitoring, appeals and incident response; staged caps support rollout [205][285]. Interpret UBE results by simulation, scoring, denominator and population: a May-2023 reanalysis estimated about the 48th overall and 15th essay percentile among passers—not learning evidence [68].

Non-text scope remains bounded: on 30 March 2023, HuggingGPT orchestrated external vision, speech, image, audio and video models; govern components for provenance and safety [89]. GPT-1 (2018) and GPT-2 (2019; 1.5 billion parameters) require versioned records of data and limits [355][200].

GPT-4/ChatGPT: 2023 simulated zero-shot UBE 297/213 points, respectively, not learning evidence; preserve prompts/scoring and human review [283]. Education systems: privacy/IP, plagiarism/exam-integrity rules; monitor [358]. Educators: train, disclose, verify; ChatGPT drafts/differentiates/translates/tutors but risks cheating/misinformation/lost practice [357][113]. Institutions: procure/pilot, secure data, log limits, track equity; learners: disclose; oral/process evidence [268][357][113]. GPT-1/GPT-2/InstructGPT: disclose limits, verify outputs, keep human accountability [40][179][271]; non-text needs safety governance [191].

Generative AI should be governed through clear, adaptable, people-centred policies that keep humans in the loop and teach its benefits, limitations, verification, privacy, bias, provenance, intellectual-property and ethical-use issues; opaque training data can expose sensitive information and legal risks and reproduce cultural bias, so provenance should be maintained as a fair, transparent, accountable and explainable investment [290][229][55][181][42]. Institutions should pair this literacy with equitable access and process-centred assessment—checkpoints, drafts, reflection and student-authored analysis—so AI augments rather than replaces teaching, learning and accountability [290][309].

GPT models should be evaluated through a Helpful-Honest-Harmless alignment framework with held-out human-preference ratings, task-specific benchmarks, truthfulness and hallucination checks, toxicity and bias tests, adversarial red-teaming and context-specific application monitoring; these measures are proxies, so inspect outputs and retain human experts rather than treating benchmark scores as safety proof [204][275][88][110][62]. Educational users should pre-test in small pilots, ground outputs with additional context or human review, collect user feedback, monitor misuse continuously and avoid high-stakes uses when safeguards cannot control residual failures [354][54][205].

Because ChatGPT can produce plausible but incorrect or nonsensical answers and fabricated references, educators should treat its contribution as provisional: require human review, fact-checking against reliable sources, proper attribution and disclosure, and accountability for errors, bias, plagiarism, copyright and privacy [340][302][240][225][117]. They should use rubric-aligned prompts, iterative comparison with human judgement and process-focused assessment rather than rely on automated detection, so ChatGPT supports learning without displacing critical judgement or valid authorship evidence [123][292][117].

GPT-3’s text generation and rewriting, including few-shot use without fine-tuning, made its prose difficult to distinguish from human writing; assessment should therefore evaluate process and credibility as well as product through disclosed prompts and revisions, source evaluation, learner critique of AI text and human review [279][278][201][104][158][200][352]. Learners should retain opportunities to write without AI and demonstrate process on authentic cases rather than treating generated text alone as evidence of learning [104][65].

Before deploying GPT-4 in education, institutions should run staged, authentic-context pilots with students and educators, define risk tolerances, and test hallucination, unsafe output, bias, prompt injection, overreliance and sensitive-data disclosure through pre-deployment and adversarial evaluation; GPT-4’s safety work used over 50 expert testers [272][120][211][338][62]. They should begin with limited users, require review gates, grounding and escalation, monitor model and application behaviour and misuse, and scale only when evidence supports it, avoiding high-stakes uses when safeguards are inadequate [285][338][88][196].

For GPT-4’s U.S. bar-exam benchmark, the reported approximately 297 points on the 400-point UBE scale and 90th-percentile result should be treated as conditioned capability evidence, not proof of professional competence: the UBE is a general, limited proxy rather than jurisdiction-specific practice, and performance varies with task structure, prompting, population and scoring method [282][70][284][194]. An assessment-literacy framework therefore preserves the benchmark’s construct and conditions, compares like with like, reports limitations and retains human oversight before transferring the result to educational or professional decisions [68][284][280].

For 2023 adoption, education systems should use transparent, ethical, human-centred, multi-stakeholder governance: define roles and responsibilities, involve teachers, learners, policymakers and providers, align adoption with curriculum and standards, and coordinate legislation, resourcing, capacity development and school-level implementation [247][242][329][328]. They should require risk-based pilots and authentic-context validation, monitor performance, generalisability, equity and privacy, measure digital skills and meaningful access rather than devices alone, and revise policy as threats, laws and evidence change [296][73][336][330][350].

Educators should receive differentiated, continuing professional learning, coaching, peer collaboration and practical resources on GenAI capabilities, limitations, ethics, bias and acceptable use; they should be consulted in pilots and keep tools human-controlled, proportionate to learners’ age and aligned with learning goals [328][315][247][303]. In class, educators should model disclosure and attribution, require source verification and fact-checking, use rubric-aligned prompts and iterative human review, and assess process and reasoning rather than treat AI output as the student’s authorship [328][117][123].

Educational institutions should make procurement a documented risk-and-accountability gate: vet vendors for quality, health and safety, legal and human-rights risks; designate security responsibility; and require disclosure of data location, processing, encryption, segregation, access, purpose and lifecycle safeguards [343][342][346][265]. They should remove cost barriers such as a $20-a-month subscription through licensing, infrastructure and broadband, UDL and co-design with disabled students, while reviewing data inventories, vendor safeguards and privacy, security and accessibility impacts before and during use [298][214][330][297][176][241].

Education providers should teach students and learners to work with AI rather than simply ban it, combining data and algorithm literacy with critical source evaluation, acknowledgement, ethics, academic-integrity knowledge, independent thinking and human agency [179][318][240][235][324]. They should provide equitable access, accessible formats and accommodations, protect learner data and autonomy, involve disabled learners, and pair independent exploration with teacher, peer and trusted-adult support because benefits vary by disability, content modality, subject and access to assistive technology, while young learners may accept harmful output without critical engagement [329][334][43][247][320][330][305].

Using a model-card documentation framework, GPT-1 should be recorded by version and architecture—including its twelve-layer, twelve masked self-attention-head design and 117 million parameters—along with training data and procedure, intended uses, limitations, provenance, evaluation conditions and capability boundaries [47][263][281][203][272]. The historical change to preserve is qualitative: GPT-1’s limited early disclosure should give way to more structured model cards, usage policies and capability-change records, while human validation remains necessary rather than inferring reliability from the early architecture [272][288][46][40].

Using a model-card and staged-release framework, GPT-2 documentation should identify the 1.5-billion-parameter version, configuration, input conditions, data provenance, intended and unintended uses, evaluation metrics, bias and truthfulness limits and synthetic-content status; human review and partnership-based release should precede broad educational use [294][312][52][356][277][270]. GPT-2 marks a qualitative increase in disclosure—from staged release toward model cards, metadata and updated documentation—but not a demonstrated increase in reliability: it could repeat, lose long-range coherence, produce fluent but unsupported text and reproduce bias, so realistic testing and human scrutiny of references and code remain necessary [277][356][188][200][269][100].

## References

[1] <https://www.ed.gov/sites/ed/files/documents/ai-report/ai-report.pdf> Federal analysis of algorithmic bias; Human-in-the-loop recommendations; Human-centered governance principles
[2] <https://doi.org/10.1109/mc.2023.3253292> Generative AI overview
[3] <https://cdn.openai.com/papers/gpt-4.pdf> GPT-4 technical report; GPT-4 technical disclosure; GPT-4 evaluation results; Simulated examination results; Multilingual benchmark results; Technical evaluati…
[4] <https://openai.com/index/chatgpt/> ChatGPT launch description; ChatGPT introduction; ChatGPT’s stated limitations
[5] <https://openai.com/index/gpt-4-research/> GPT-4 release; GPT-4 visual-input description; GPT-4 factuality summary; GPT-4 visual-input release; GPT-4 knowledge and reliability boundaries; GPT-4 deployme…
[6] <https://doi.org/10.1080/03043797.2023.2213169> engineering-education literature; Australian engineering benchmark
[7] <https://openai.com/index/language-models-are-few-shot-learners/> Brown et al., 2020; GPT-3 capabilities
[8] <https://developer.nvidia.com/blog/openai-presents-gpt-3-a-175-billion-parameters-language-model/> NVIDIA’s GPT-3 comparison
[9] <https://library.glion.edu/wp-content/uploads/2023/05/ChatGPT-and-Artificial-Intelligence-in-higher-education-Quick-Start-guide_EN_FINAL-1.pdf> UNESCO teaching-and-learning applications; UNESCO’s learning-support roles; UNESCO’s administrative applications; UNESCO’s dialogue applications; UNESCO’s acce…
[10] <https://arxiv.org/abs/2305.18616> May 2023 quasi-experimental study; Undergraduate reflections; Context-sensitive integration findings
[11] <https://arxiv.org/abs/2305.11882> Student-comment labeling study
[12] <https://www.mdpi.com/2076-3417/13/9/5783> Programming experiment; Education and programming review
[13] <https://blogs.worldbank.org/en/education/how-use-chatgpt-support-teachers-good-bad-and-ugly> World Bank analysis; World Bank’s teacher-support examples; World Bank’s supervision warning; World Bank’s grading and proctoring analysis; World Bank’s teache…
[14] <https://www.cam.ac.uk/stories/ChatGPT-and-education> Cambridge discussion of formative assessment; Cambridge’s postgraduate example; Cambridge discussion of bias
[15] <https://citejournal.org/volume-23/issue-1-23/editorial/editorial-chatgpt-challenges-opportunities-and-implications-for-teacher-education> Teacher-education editorial; Reported student-use surveys
[16] <https://doi.org/10.1109/mc.2023.3263576> IEEE accessibility discussion; Research applications and responsibilities; IEEE assessment guidance; Research and publication implications; AI-literacy recomme…
[17] <https://doi.org/10.48550/arXiv.2304.05613> Multilingual ChatGPT evaluation
[18] <https://files.eric.ed.gov/fulltext/ED654282.pdf> Xu et al., May 2023; Personal learning environment recommendations
[19] <https://www.aku.edu/qtl/SiteAssets/Pages/ai-guidelines/AI%20Guide-May_2023.pdf> Aga Khan University guidance
[20] <https://larrycuban.wordpress.com/2023/04/08/six-ways-teachers-can-use-chatgpt-to-save-time-todd-finley/> Finley’s classroom applications
[21] <https://ut.ee/sites/default/files/2023-05/university_of_tartu_guidelines_for_using_ai_chatbots_for_teaching_and_studies_28_april_2023_pdf.pdf> Tartu’s accuracy guidance; Tartu’s learning activities; Tartu’s disclosure guidance; Tartu’s teaching recommendations; Tartu’s verification requirements; Tartu…
[22] <https://doi.org/10.1186/s40561-023-00237-x> Tlili et al.’s privacy scenario
[23] <https://www.garanteprivacy.it/home/docweb/-/docweb-display/docweb/9870847> Garante’s order; Garante’s regulatory concerns
[24] <https://www.biola.edu/information-technology/information-security/chatgpt-at-biola> Biola’s security notice; Biola’s approved-use approach
[25] <https://www.nysed.gov/sites/default/files/programs/data-privacy-security/nysed-privacy-office-newsletter-april-2023.pdf> NYSED’s April 2023 newsletter
[26] <https://www.maastrichtuniversity.nl/file/22052-boe-fasos-chatgpt-guidelines-examiners-v-7-2-2023pdf> Maastricht FASoS guidance; FASoS requirement
[27] <https://uwaterloo.ca/associate-vice-president-academic/news/avpa-memo-chat-gpt-and-other-ai-tools-university-waterloo> Waterloo’s academic-integrity memo
[28] <https://arxiv.org/abs/2305.13934> University-course comparison; Classifier evaluation; Classifier findings
[29] <https://doi.org/10.48550/arxiv.2305.18081> Game of Tones
[30] <https://doi.org/10.1080/14703297.2023.2195846> Farrokhnia et al.’s analysis; Assessment redesign analysis
[31] <https://www.mdpi.com/2076-3417/13/10/6039> Sánchez-Ruiz et al.’s engineering study
[32] <https://www.tc.columbia.edu/articles/2023/january/navigating-the-risks-and-rewards-of-chatgpt/> Teachers College discussion; Teachers College’s policy analysis; Trust and transparency discussion
[33] <https://theconversation.com/if-ai-is-to-become-a-key-tool-in-education-access-has-to-be-equal-204156> UK access figures; Equal-access recommendations
[34] <https://dsu.edu/news/2023/03/will-ai-chatbots-raise-digital-equity-concerns.html> California broadband report
[35] <https://www.uwyo.edu/acadaffairs/_files/docs/final-report-aigw-february-2023.pdf> Wyoming working-group report; Wyoming’s syllabus recommendations
[36] <https://www.ncirl.ie/Portals/0/Library/NCI%20Academic%20Integrity%20Policy%20on%20Assessments%20and%20use%20of%20AI%20Generated%20Material%20such%20as%20ChatGPT.pdf?timestamp=1684768817233&ver=2023-05-22-161619-910>
[37] <https://www.maastrichtuniversity.nl/file/fpnedhubfaculty-guidelines-managing-artificial-intelligence-tools-education-and-assessment> Maastricht FPN guidance; FPN recommendation
[38] <https://researchonline.lse.ac.uk/id/eprint/118601/1/highereducation_2023_3_23_resist_ai_by_rethinking_assessment.pdf> Pirrone’s assessment discussion
[39] <https://studentprivacy.ed.gov/data-security-k-12-and-higher-education> Student-data security guidance
[40] <https://doi.org/10.48550/arxiv.2304.11215>
[41] <https://arxiv.org/pdf/2305.03720>
[42] <https://dl.acm.org/doi/10.1145/3503488>
[43] <https://doi.org/10.5206/eei.v31i1.14089>
[44] <https://doi.org/10.1007/s40593-020-00235-x>
[45] <https://en.wikipedia.org/wiki/GPT-3>
[46] <https://doi.org/10.2196/48291>
[47] <https://en.wikipedia.org/wiki/GPT-1>
[48] <https://www.techrxiv.org/doi/pdf/10.36227/techrxiv.22312330.v2>
[49] <https://aws.amazon.com/what-is/gpt/>
[50] <https://lambda.ai/blog/demystifying-gpt-3>
[51] <https://github.com/openai/following-instructions-human-feedback/blob/main/model-card.md>
[52] <https://ar5iv.labs.arxiv.org/html/2012.07805v1>
[53] <https://arxiv.org/pdf/2303.17276>
[54] <https://www.mofo.com/resources/insights/230315-gpt-4-release-deep-dive-briefing-improvements>
[55] <https://mitsloan.mit.edu/ideas-made-to-matter/bringing-transparency-to-data-used-to-train-artificial-intelligence>
[56] <https://static.poder360.com.br/2023/03/relatorio-testes-chat-gpt-4-open-ai-mar-2023.pdf>
[57] <https://www.emerald.com/aiie/article/1/1/24/1277151/Can-ChatGPT-design-formative-assessments-to>
[58] <https://venturebeat.com/business/openai-debuts-chatgpt-and-gpt-3-5-series-as-gpt-4-rumors-fly>
[59] <https://www.cs.cmu.edu/~hn1/papers/ECTEL2023_EvaluatingChatGPT.pdf>
[60] <https://ar5iv.labs.arxiv.org/html/2303.08774>
[61] <https://ar5iv.labs.arxiv.org/html/2304.06488v1>
[62] <https://openai.com/index/gpt-4-research/>
[63] <https://www.iit.edu/news/gpt-4-passes-bar-exam>
[64] <https://proceedings.neurips.cc/paper_files/paper/2022/file/b1efde53be364a73914f58805a001731-Paper-Conference.pdf>
[65] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12018347/>
[66] <https://www.centerconsulting.com/ai-library/milestones/2018-gpt-1>
[67] <https://arxiv.org/html/2305.12477>
[68] <https://law-ai.org/re-evaluating-gpt-4s-bar-exam-performance/>
[69] <https://arxiv.org/html/2304.02017v14>
[70] <https://doi.org/10.2139/ssrn.4441311>
[71] <https://faculti.net/studybank/explainers/gpt-performance-on-the-uniform-bar-exam-92971b0e82d3>
[72] <https://www.oecd.org/content/dam/oecd/en/publications/reports/2021/02/positive-high-achieving-students_6e6b7c03/3b9551db-en.pdf>
[73] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10795998/>
[74] <https://doi.org/10.48550/arxiv.2309.09401>
[75] <https://www.tandfonline.com/doi/full/10.1080/03043797.2023.2213169>
[76] <https://arxiv.org/abs/2305.13934>
[77] <https://verkkolehdet.jamk.fi/finnish-business-review/wp-content/blogs.dir/16/files/2023/08/FBR-2023-article-3.pdf>
[78] <https://doi.org/10.13140/rg.2.2.12715.82721>
[79] <https://openai.com/index/chatgpt/>
[80] <https://doi.org/10.1007/s12599-023-00795-x>
[81] <https://www.cedtech.net/download/chatgpt-in-education-strategies-for-responsible-implementation-13036.pdf>
[82] <https://www.aasa.org/docs/default-source/publications/journal-of-scholarship-and-practice/2023-spring-issue/rise-chatgpt-generativeai.pdf>
[83] <https://openai.com/index/chatgpt-plus/>
[84] <https://export.arxiv.org/pdf/2305.07605v3.pdf>
[85] <https://nepc.colorado.edu/sites/default/files/publications/PB%20Williamson_1.pdf>
[86] <https://doi.org/10.48550/arxiv.2305.04160>
[87] <https://export.arxiv.org/pdf/2304.11221v1.pdf>
[88] <https://cdn.openai.com/papers/gpt-4-system-card.pdf>
[89] <https://doi.org/10.48550/arxiv.2303.17580>
[90] <https://doi.org/10.48550/arxiv.2304.06488>
[91] <https://researchspace.auckland.ac.nz/server/api/core/bitstreams/23592098-f1a2-412d-ac9b-a85135f2fde4/content>
[92] <https://doi.org/10.48550/arxiv.2305.07605>
[93] <https://doi.org/10.22521/edupij.2023.124.1>
[94] <https://epub.ub.uni-muenchen.de/125071/1/ChatGPT_for_Good_v3.pdf>
[95] <https://doi.org/10.36227/techrxiv.22589497>
[96] <https://doi.org/10.1016/j.caeai.2023.100182>
[97] <https://www.waldenu.edu/programs/education/resource/five-pros-and-cons-of-ai-in-the-education-sector>
[98] <https://doi.org/10.1111/bjet.13334>
[99] <https://doi.org/10.48550/arxiv.2306.10645>
[100] <https://www.mdpi.com/1999-5903/15/6/192>
[101] <https://citejournal.org/volume-23/issue-1-23/editorial/editorial-chatgpt-challenges-opportunities-and-implications-for-teacher-education>
[102] <https://doi.org/10.1088/1361-6552/acc299>
[103] <https://doi.org/10.1103/physrevphyseducres.19.010132>
[104] <https://www.writecenter.org/uploads/1/2/5/6/125695261/educational_research_and_ai-generated_writing_tate_et_al_2023__2_.pdf>
[105] <https://link.springer.com/article/10.1007/s40593-018-0164-5?code=9ca30cd5-478c-44a0-91ea-01bc346dc474&error=cookies_not_supported>
[106] <https://www.tandfonline.com/doi/full/10.1080/10494820.2023.2253861>
[107] <https://www.ed.gov/sites/ed/files/documents/ai-report/ai-report.pdf>
[108] <https://doi.org/10.31235/osf.io/c5hf3>
[109] <https://www.oregon.gov/ode/educator-resources/teachingcontent/Documents/ODE_Generative_Artificial_Intelligence_%28AI%29_in_K-12_Classrooms_2023.pdf>
[110] <https://www.frontiersin.org/journals/education/articles/10.3389/feduc.2024.1379796/full>
[111] <https://doi.org/10.48550/arxiv.2303.13379>
[112] <https://www.mdpi.com/2071-1050/15/17/12983>
[113] <https://www.maastrichtuniversity.nl/file/chatgpt-guidelines-fse-13022023pdf>
[114] <https://www.mdpi.com/2076-3417/13/9/5783>
[115] <https://www.researchgate.net/publication/367541637_ChatGPT_for_Good_On_Opportunities_and_Challenges_of_Large_Language_Models_for_Education>
[116] <https://www2.ed.gov/documents/ai-report/ai-report.pdf>
[117] <https://www.frontiersin.org/journals/education/articles/10.3389/feduc.2024.1328769/full>
[118] <https://doi.org/10.3390/educsci13040410>
[119] <https://doi.org/10.1109/seeng59157.2023.00010>
[120] <https://doi.org/10.1111/bjet.13370>
[121] <https://doi.org/10.37074/jalt.2023.6.1.22>
[122] <https://asef.org/wp-content/uploads/2023/12/2023_10_ASEF_AI_and_Education_009_111223_FINAL_DOUBLE.pdf>
[123] <https://journals.calstate.edu/ijaipil/article/download/6962/5333>
[124] <https://hdsr.mitpress.mit.edu/pub/1cbv006q/release/1>
[125] <https://doi.org/10.2991/978-2-38476-138-8_23>
[126] <https://ar5iv.labs.arxiv.org/html/2305.11583>
[127] <https://doi.org/10.1631/fitee.2300166>
[128] <https://datainnovationhub.eu/wp-content/uploads/2023/10/SAIConference_PAPER_FORMAT_004.pdf>
[129] <https://doi.org/10.22541/au.167712329.97543109/v1>
[130] <https://doi.org/10.14742/ajet.8695>
[131] <https://doi.org/10.48550/arxiv.2303.05453>
[132] <https://doi.org/10.1038/s41746-023-00819-6>
[133] <https://socialspacejournal.eu/menu-script/index.php/ssj/article/download/176/81/428>
[134] <https://link.springer.com/article/10.1007/s42438-023-00440-6>
[135] <https://doi.org/10.17105/spr-2017-0035.v46-3>
[136] <https://www.sciencedirect.com/science/article/abs/pii/S0361476X20300643>
[137] <https://files.eric.ed.gov/fulltext/ED654282.pdf>
[138] <https://bera-journals.onlinelibrary.wiley.com/doi/10.1111/bjet.13116>
[139] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10133283/>
[140] <https://digitalcommons.uri.edu/cgi/viewcontent.cgi?article=1547&context=cba_facpubs>
[141] <https://doi.org/10.48550/arxiv.2302.10916>
[142] <https://link.springer.com/article/10.1186/s41239-023-00392-8>
[143] <https://doi.org/10.1016/j.lindif.2023.102274>
[144] <https://www.tandfonline.com/doi/full/10.1080/10494820.2023.2180191>
[145] <https://doi.org/10.35542/osf.io/hcgzj>
[146] <https://doi.org/10.1145/3573051.3596200>
[147] <https://doi.org/10.1002/tesj.755>
[148] <https://doi.org/10.33851/jmis.2023.10.1.79>
[149] <https://doi.org/10.4018/ijcallt.326135>
[150] <https://link.springer.com/article/10.1186/s40561-023-00273-7>
[151] <https://doi.org/10.29333/ejmste/13313>
[152] <https://one.oecd.org/document/EDU/EDPC(2023)11/en/pdf>
[153] <https://www.aph.gov.au/Parliamentary_Business/Committees/House/Former_Committees/Employment_Education_and_Training/AIineducation/Report/Chapter_4_-_Opportunities_as_educational_tool>
[154] <https://educational-innovation.sydney.edu.au/teaching@sydney/should-we-use-generative-artificial-intelligence-tools-for-marking-and-feedback/>
[155] <https://www.getcircles.org/en/blog/planning-with-ai-is-not-cheating>
[156] <https://files.eric.ed.gov/fulltext/EJ1397173.pdf>
[157] <https://doi.org/10.1038/s42256-023-00644-2>
[158] <https://doi.org/10.1002/tesj.716>
[159] <https://doi.org/10.37074/jalt.2023.6.1.9>
[160] <https://doi.org/10.37074/jalt.2023.6.1.17>
[161] <https://doi.org/10.21203/rs.3.rs-3208562/v1>
[162] <https://doi.org/10.14742/apubs.2023.514>
[163] <https://doi.org/10.1515/jccall-2023-0008>
[164] <https://arxiv.org/pdf/2302.13817>
[165] <https://doi.org/10.70725/815246mfssgp>
[166] <https://doi.org/10.3390/computers12080153>
[167] <https://doi.org/10.2196/51344>
[168] <https://link.springer.com/article/10.1186/s40561-023-00237-x>
[169] <https://www.tandfonline.com/doi/full/10.1080/14703297.2023.2190148>
[170] <https://doi.org/10.29408/veles.v7i3.21209>
[171] <https://pearl.plymouth.ac.uk/cgi/viewcontent.cgi?article=1310&context=bms-research>
[172] <https://doi.org/10.3390/fi15060192>
[173] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10670526/>
[174] <https://www.global-solutions-initiative.org/publication/reconsidering-education-policy-in-the-era-of-generative-ai/>
[175] <https://www.brookings.edu/articles/should-schools-ban-or-integrate-generative-ai-in-the-classroom/>
[176] <https://oro.open.ac.uk/79244/3/79244VOR.pdf>
[177] <https://onlinelibrary.wiley.com/doi/full/10.1002/brx2.30>
[178] <https://www.mdpi.com/2226-471X/8/3/191>
[179] <https://phys.org/news/2020-01-text-generating-artificial-intelligence-classroom.pdf>
[180] <https://files.eric.ed.gov/fulltext/EJ1224780.pdf>
[181] <https://doi.org/10.25112/bcij.v3i2.3540>
[182] <https://link.springer.com/article/10.1007/s10639-023-11846-x>
[183] <https://arxiv.org/abs/2304.03784>
[184] <https://www.centerforengagedlearning.org/generative-ai-and-non-majority-students-risks-and-benefits/>
[185] <https://doi.org/10.1609/aaai.v37i13.26879>
[186] <https://doi.org/10.48550/arxiv.2203.02155>
[187] <https://www.tandfonline.com/doi/full/10.1080/10382046.2023.2194036>
[188] <https://cdn.openai.com/GPT_2_August_Report.pdf>
[189] <https://link.springer.com/article/10.1007/s43681-022-00148-6>
[190] <https://ar5iv.labs.arxiv.org/html/2212.00857v1>
[191] <https://ar5iv.labs.arxiv.org/html/2303.04226>
[192] <https://arxiv.org/pdf/2203.07618v2.pdf>
[193] <https://en.wikipedia.org/wiki/GPT-3.5>
[194] <https://arxiv.org/html/2308.12488v2>
[195] <https://ar5iv.labs.arxiv.org/html/2303.08774v2>
[196] <https://arxiv.org/html/2303.08774>
[197] <https://github.com/openai/gpt-2/blob/master/model_card.md>
[198] <https://chatgpt.ca/blog/when-did-chatgpt-come-out>
[199] <https://doi.org/10.48550/arxiv.2303.15715>
[200] <https://doi.org/10.3233/faia200717>
[201] <https://proceedings.neurips.cc/paper_files/paper/2020/file/1457c0d6bfcb4967418bfb8ac142f64a-Paper.pdf>
[202] <https://arxiv.org/abs/2303.08774v4>
[203] <https://ttms.com/chat-gpt-evolution/>
[204] <https://arxiv.org/html/2203.02155v1>
[205] <https://cdn.openai.com/papers/gpt-4.pdf?hl=en-US>
[206] <https://www.everycrsreport.com/files/2023-05-23_R47569_69f42fc0dd78a52fa49ac47a921f99652501618b.pdf>
[207] <https://doi.org/10.48550/arxiv.2302.13795>
[208] <https://doi.org/10.30935/cedtech/13036>
[209] <https://en.wikipedia.org/wiki/ChatGPT>
[210] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10328063/>
[211] <https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf>
[212] <http://nbn-resolving.de/urn:nbn:de:bsz:100-opus-21463>
[213] <https://www.frontiersin.org/journals/education/articles/10.3389/feduc.2025.1610836/full>
[214] <https://teaching.cornell.edu/sites/default/files/2023-08/Cornell-GenerativeAIForEducation-Report_1.pdf>
[215] <https://doi.org/10.11575/prism/dspace/40894>
[216] <https://help.openai.com/en/articles/8313351-how-can-educators-respond-to-students-presenting-ai-generated-content>
[217] <https://files.eric.ed.gov/fulltext/EJ1394645.pdf>
[218] <https://doi.org/10.37965/jait.2023.0184>
[219] <https://fernuni.ch/fileadmin/user_upload/public/UniDistance/Actualites/NEWS_digitalskills/Ressources_pedagogiques/ChatGPT/ChatGPT_Guidelines.pdf>
[220] <https://teaching.cornell.edu/sites/default/files/2023-08/Cornell-GenerativeAIForEducation-Report_2.pdf>
[221] <https://www.edweek.org/technology/with-chatgpt-teachers-can-plan-lessons-write-emails-and-more-whats-the-catch/2023/01>
[222] <https://link.springer.com/article/10.1007/s40979-023-00130-7>
[223] <https://www.tandfonline.com/doi/full/10.1080/0144929X.2024.2394886>
[224] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10339472/>
[225] <https://doi.org/10.25172/slrf.76.1.5>
[226] <https://discovery.ucl.ac.uk/id/eprint/10179267>
[227] <https://www.frontiersin.org/journals/education/articles/10.3389/feduc.2025.1527851/full>
[228] <https://assets.publishing.service.gov.uk/media/65b8cd41b5cb6e000d8bb74e/DfE_GenAI_in_education_-_Educator_and_expert_views_report.pdf>
[229] <https://doi.org/10.48550/arxiv.2305.02878>
[230] <https://discovery.ucl.ac.uk/id/eprint/10176438/1/Miao%20and%20Holmes%20-%202023%20-%20Guidance%20for%20Generative%20AI%20in%20Education%20and%20Resear.pdf>
[231] <https://link.springer.com/article/10.1186/s40561-023-00279-1>
[232] <https://digital.library.unt.edu/ark:/67531/metadc2289578>
[233] <https://er.educause.edu/articles/2023/3/chatgpt-and-higher-education-initial-prevalence-and-areas-of-interest>
[234] <https://doi.org/10.3389/feduc.2023.1166682>
[235] <https://doi.org/10.1016/j.ijme.2023.100818>
[236] <https://doi.org/10.1080/17439884.2023.2167830>
[237] <https://doi.org/10.35542/osf.io/s4nfz>
[238] <https://doi.org/10.18653/v1/2022.eval4nlp-1.10>
[239] <https://doi.org/10.4995/eurocall2023.2023.16994>
[240] <https://www.teqsa.gov.au/sites/default/files/2023-04/aain-generative-ai-guidelines.pdf>
[241] <https://researchonline.lse.ac.uk/id/eprint/119737/1/A_Blueprint_for_Education_Data_FINAL_Online.pdf>
[242] <https://link.springer.com/article/10.1007/s40593-021-00239-1>
[243] <https://assets.publishing.service.gov.uk/government/uploads/system/uploads/attachment_data/file/1107808/Implementation_of_education_technology_in_schools__and_colleges.pdf>
[244] <https://doi.org/10.3390/su14063414>
[245] <https://doi.org/10.18552/joaw.v12i1.820>
[246] <https://doi.org/10.1016/j.caeai.2023.100145>
[247] <https://discovery.ucl.ac.uk/id/eprint/10130180/1/Miao%20and%20Holmes%20-%202021%20-%20AI%20and%20education%20guidance%20for%20policy-makers.pdf>
[248] <https://doi.org/10.59453/jmtn6001>
[249] <https://digitalpovertyalliance.org/events/without-intervention-ai-widen-digital-divide-students/>
[250] <https://theconversation.com/if-ai-is-to-become-a-key-tool-in-education-access-has-to-be-equal-204156>
[251] <https://www.emergentmind.com/papers/2305.13534>
[252] <https://doi.org/10.18653/v1/2023.eacl-main.241>
[253] <https://www.sydney.edu.au/study/student-life/student-news/2023/05/29/what-you-need-to-know-about-the-new-academic-integrity-policy.html>
[254] <https://doi.org/10.1080/10494820.2021.2012812>
[255] <https://www.jsums.edu/english/files/2014/03/nuckles.pdf>
[256] <https://www.gov.uk/guidance/data-protection-in-schools/generative-artificial-intelligence-ai-and-data-protection-in-schools>
[257] <https://iweb.langara.ca/edtech/blog/2023/04/28/ai-tools-privacy/>
[258] <https://www.govtech.com/education/higher-ed/will-ai-chatbots-raise-digital-equity-concerns-for-students>
[259] <https://bellwether.org/blog/make-ai-work-for-everyone/>
[260] <https://arxiv.org/html/2304.09103v1>
[261] <https://blogs.worldbank.org/en/education/how-use-chatgpt-support-teachers-good-bad-and-ugly>
[262] <https://www.tc.columbia.edu/articles/2023/january/navigating-the-risks-and-rewards-of-chatgpt/>
[263] <https://huggingface.co/openai-community/openai-gpt/blob/main/README.md>
[264] <http://urn.kb.se/resolve?urn=urn%3Anbn%3Ase%3Akau%3Adiva-96569>
[265] <https://studentprivacy.ed.gov/sites/default/files/resource_document/file/Data_Governance_and_Stewardship_0.pdf>
[266] <https://ovic.vic.gov.au/wp-content/uploads/2021/06/OVIC-examination-report-privacy-and-information-security-policies-of-Victorian-universities.pdf>
[267] <https://doi.org/10.48550/arxiv.2304.11082>
[268] <https://openai.com/index/better-language-models/>
[269] <https://cdn.openai.com/better-language-models/language-models.pdf>
[270] <https://github.com/openai/gpt-2/>
[271] <https://openai.com/index/instruction-following/>
[272] <https://ojs.aaai.org/index.php/AIES/article/download/31757/33924/35821>
[273] <https://doi.org/10.48550/arxiv.2301.04655>
[274] <https://discovery.ucl.ac.uk/id/eprint/10158374/1/Holmes%20and%20Tuomi%20-%202022%20-%20State%20of%20the%20art%20and%20practice%20in%20AI%20in%20education.pdf>
[275] <https://mbrenndoerfer.com/writing/instructgpt-rlhf-aligning-language-models-human-preferences>
[276] <https://arxiv.org/abs/2303.08774>
[277] <https://openai.com/index/gpt-2-6-month-follow-up/>
[278] <https://syncedreview.com/2020/05/29/openai-unveils-175-billion-parameter-gpt-3-language-model/>
[279] <https://doi.org/10.33140/jctcsr.02.02.02>
[280] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10894685/>
[281] <https://arxiv.org/html/2303.18223v11>
[282] <https://royalsocietypublishing.org/doi/10.1098/rsta.2023.0254>
[283] <https://www.courthousenews.com/wp-content/uploads/2023/03/chatgpt-bar-pass.pdf>
[284] <https://law-ai.org/wp-content/uploads/2023/05/s10506-024-09396-9-4-1.pdf>
[285] <https://help.openai.com/en/articles/6825453-chatgpt-release-notes?q=old+version>
[286] <https://help.openai.com/en/articles/6825453-chatgpt-release-notes>
[287] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10439949/>
[288] <https://www.gaussalgo.com/knowledge-base/a-brief-history-of-ai-and-the-rise-of-chatgpt>
[289] <https://repository.gchumanrights.org/bitstreams/a3318776-4cac-4385-a69c-9f7a4cd7f5f4/download>
[290] <https://advance.uky.edu/sites/default/files/2023-08/2023.08.11_ADVANCEfacultyguidelines.pdf>
[291] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9939079/>
[292] <https://doi.org/10.1145/3633287>
[293] <https://www.sciengine.com/doi/10.1109/JAS.2023.123618>
[294] <https://arxiv.org/pdf/2302.09419>
[295] <https://www.mdpi.com/2227-7102/14/6/643>
[296] <https://researchmgt.monash.edu/ws/portalfiles/portal/580360903/501470316_oa.pdf>
[297] <https://journals.calstate.edu/er/article/download/3866/3476/12085>
[298] <https://repository.jisc.ac.uk/9232/1/ai-in-tertiary-education-a-summary-of-the-current-state-of-play-september-2023.pdf>
[299] <https://doi.org/10.18260/1-2--4690>
[300] <https://www.teachai.org/toolkit-principles>
[301] <https://www.c21u.gatech.edu/sites/default/files/publication/2023/03/C21U%20ChatGPT%20White%20Paper_Final.pdf>
[302] <https://oer.informationskompetenz.ch/objects/LOR:91/datastreams/DS1>
[303] <https://www.mdpi.com/2227-7102/13/9/856>
[304] <https://www.frontiersin.org/journals/education/articles/10.3389/feduc.2023.1071759/full>
[305] <https://www.oph.fi/sites/default/files/documents/Guidance%20for%20generative%20AI%20in%20education%20and%20research.pdf>
[306] <https://link.springer.com/article/10.1007/s11423-023-10203-6>
[307] <https://doi.org/10.1186/s41239-023-00411-8>
[308] <https://link.springer.com/article/10.1007/s11528-022-00715-y>
[309] <https://www.mdpi.com/2078-2489/16/4/296>
[310] <https://www.maastrichtuniversity.nl/file/fhml-examiner-guidelines-chatgpt-20230309-defpdf>
[311] <https://www.aph.gov.au/DocumentStore.ashx?id=98d34f1a-1f3b-4ee1-a742-f57076f924c8&subId=745132>
[312] <https://huggingface.co/transformers/v3.0.2/model_doc/gpt2.html?highlight=use_cache>
[313] <https://eric.ed.gov/?id=EJ1402581>
[314] <https://www.qaa.ac.uk/docs/qaa/members/maintaining-quality-and-standards-in-the-chatgpt-era.pdf>
[315] <https://unesco.org.uk/site/assets/files/10375/guidance_for_generative_ai_in_education_and_research.pdf>
[316] <https://d-nb.info/1364545578/34>
[317] <https://education.nsw.gov.au/content/dam/main-education/about-us/strategies-and-reports/consultation-items/AI_Consultation_Paper.pdf>
[318] <https://discovery.ucl.ac.uk/id/eprint/10146850/1/381226eng.pdf>
[319] <https://www.cambridge.org/sites/default/files/media/documents/CPELE_Exploring%20the%20Impact%20of%20Generative%20AI%20on%20Language%20Education%20Insights%20from%20Teachers_FINAL.pdf>
[320] <https://doi.org/10.19053/2011835x.7545>
[321] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7644889/>
[322] <https://lib.dr.iastate.edu/cgi/viewcontent.cgi?article=1100&context=engl_pubs>
[323] <https://link.springer.com/article/10.1007/s10639-023-12174-w>
[324] <https://discovery.ucl.ac.uk/id/eprint/10176438>
[325] <https://doi.org/10.25364/401.2021.5.2>
[326] <https://documents1.worldbank.org/curated/en/268121613971613659/pdf/Foundational-Teaching-Skills-Guide.pdf>
[327] <https://doi.org/10.1080/17439884.2020.1786399>
[328] <https://www.doe.mass.edu/edtech/ai/ai-guidance.pdf>
[329] <https://www.oecd.org/content/dam/oecd/en/publications/reports/2023/08/digital-equity-and-inclusion-in-education_c56b91ad/7cb15030-en.pdf>
[330] <https://doi.org/10.1787/7cb15030-en>
[331] <https://doi.org/10.1007/s40979-023-00133-4>
[332] <https://www.unesco.org/mil4teachers/sites/default/files/medias/fichiers/2023/10/Modules_11_CI%20MIL_CURRICULUM.pdf>
[333] <https://doi.org/10.1109/fie61694.2024.10893330>
[334] <http://doras.dcu.ie/16296>
[335] <https://files.eric.ed.gov/fulltext/ED614998.pdf>
[336] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11622955/>
[337] <https://doi.org/10.52041/iase.icots11.t3c3>
[338] <https://pmc.ncbi.nlm.nih.gov/articles/PMC13212166/>
[339] <https://ut.ee/sites/default/files/2023-05/university_of_tartu_guidelines_for_using_ai_chatbots_for_teaching_and_studies_28_april_2023_pdf.pdf>
[340] <https://academicsenate.usc.edu/wp-content/uploads/sites/6/2023/02/CIS-Generative-AI-Guidelines-20230214.pdf>
[341] <https://ipad.education.uconn.edu/wp-content/uploads/sites/509/2023/05/UCONN-ChatGPT-Presentation.pdf>
[342] <https://oig.ed.gov/sites/default/files/document/2023-03/title_iv_dear_cpa_19-01.pdf>
[343] <https://defenddigitalme.org/wp-content/uploads/2023/04/Biometrics-in-schools-briefing-2-April-2023.pdf>
[344] <https://excelined.org/wp-content/uploads/2023/05/c3_DigitalPolicy_OnePager_ChatGPT-FAQs_2023.pdf>
[345] <https://oig.ed.gov/sites/default/files/document/2023-03/title_iv_audit_guide_march_2023.pdf>
[346] <https://st4s.edu.au/wp-content/uploads/2023/12/Safer-Technologies-4-Schools-Supplier-Guide-2023.1-v1.0.pdf>
[347] <https://dera.ioe.ac.uk/id/eprint/39800/1/Generative_artificial_intelligence_in_education_.pdf>
[348] <https://assets.schools.nsw.gov.au/content/dam/doe/sws/schools/y/yass-h/Documents/Procedures/School%20Procedures%20on%20Academic%20Malpractice%20Involving.pdf>
[349] <https://www.calbar.ca.gov/Portals/0/documents/admissions/Examinations/CBEStudy_Attachment_A.pdf>
[350] <https://www.ed.gov/media/document/2022-pl-planning-standard-signedpdf-45575.pdf>
[351] <https://doi.org/10.1145/3461702.3462578>
[352] <https://doi.org/10.56294/mr202329>
[353] <https://cdn.jsdelivr.net/npm/pi-research-workbench@0.2.0/skills/evidence-foundation/SKILL.md>
[354] <https://openai.com/index/language-model-safety-and-misuse/>
[355] <https://doi.org/10.54455/mcn2204>
[356] <https://openai.com/index/gpt-2-1-5b-release/>
[357] <https://acceleratelearning.stanford.edu/app/uploads/2023/02/AI-and-Education.pdf>
[358] <https://articles.unesco.org/sites/default/files/medias/fichiers/2023/05/ministerial-roundtable-generative-AI-in-education-agenda-en_0.pdf>
