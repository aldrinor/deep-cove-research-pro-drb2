# Big Loop and Atomization: Components, Advantages, and Construction Methods

**Big Loop means coordinated execution**: an LLM operates within a larger system that retrieves information, invokes tools or specialized models, checks results, updates state, and decides what to do next. **Atomization means exposing reusable units**: capabilities or reasoning processes are divided into components with explicit responsibilities, inputs, outputs, and checks. These are operational definitions for this review; the supporting literature uses more specific concepts, including compound AI systems, cognitive architectures, tool learning, and atomic reasoning. Zaharia and colleagues’ February 2024 BAIR technical essay provides a particularly clear distinction between an individual model and a system of interacting components. [1]

**The comparative conclusion is conditional**: such systems can outperform a single LLM, perform operations beyond text generation, and give users more control. They become computationally efficient when specialization, selective execution, reuse, or parallelism outweigh coordination overhead—not simply because they contain more components. The construction methods divide naturally into Tool Components—existing, manually engineered, or automatically generated tools—and Model Components, built through task-specific training and architectural changes.

**The review follows three questions**: what the concepts mean and which components they contain; how those components produce advantages across Capability Enhancement, Functionality Expansion, Computational Efficiency, and User-Centric Design; and how Tool Components and Model Components are constructed. The scope is public work released no later than **31 December 2025**, without geographic restriction.

| Aspect | Single-LLM baseline | System mechanism | Implementation example | Supporting evidence | Main trade-off |
|---|---|---|---|---|---|
| Capability Enhancement | GPT-4 answering alone | Generation, execution, feedback | AutoGen, 2023 report | MATH: 69.48% versus 55.18%, 5,000 problems [2] | Additional execution and inference |
| Functionality Expansion | Generated answers or suggested actions | Structured calls to external services | ToolLLM, ICLR 2024 | 16,464 APIs across 49 categories [3] | Access does not ensure successful use |
| Computational Efficiency | One execution strategy for every request | Difficulty routing and escalation | SAS/MAS routing, May 2025 preprint | 50% of always-MAS cost on GSM8K+AIME [4] | Routing and verification errors |
| User-Centric Design | Chat transcript as the main interface | Persistent preferences and editable subtasks | ExploreLLM, 2023 preprint | Eight-person comparison with ChatGPT [5] | Structure can add cognitive burden |

## 1. Definitions of Big Loop, Atomization, and Atomic-Component Categories

### Big Loop: the system boundary and feedback cycle

**The unit is the application**. Here, a Big Loop is a goal-directed execution system in which one or more LLM invocations interact with other components through an explicit control and feedback process. Its defining feature is not the number of models, but the ability to incorporate intermediate observations into subsequent decisions. CoALA, introduced in a September 2023 public preprint, supplies a close conceptual foundation: modular memory, internal and external actions, and a repeated decision-making process involving planning and execution. [6]

**Its boundary includes coordination infrastructure**. Inside the application’s logical boundary are the model-invocation roles, registered tool interfaces, retrieval and memory mechanisms, validators, execution state, and orchestration rules. The user, third-party services, source repositories, and physical environment remain external entities with which the system interacts. An API wrapper can therefore be an internal component even when the service it calls runs elsewhere; deployment location and architectural responsibility are different questions.

**Feedback closes the operational loop**. A typical execution begins with a user goal, selects a subtask or action, invokes a component, receives an observation, and updates the task state. A validator or controller then accepts the result, requests clarification, retries, changes the plan, or stops. ReAct, first released on 6 October 2022 and published at ICLR 2023, exemplifies this pattern by interleaving reasoning traces, actions, and observations from external sources or environments. [7]

**One model can support the loop**. The same LLM can perform planning, tool selection, interpretation, and revision through different calls. Conversely, several separately prompted agents can share one underlying model checkpoint. A Big Loop, in this operational sense, therefore includes both single-agent tool-using systems and multi-agent systems; it should not be equated with multi-agent collaboration alone.

**Workflows differ from autonomous agents**. Anthropic’s December 2024 technical guidance distinguishes workflows, whose execution paths are predefined in code, from agents, whose LLMs dynamically direct their processes and tool use. Both can contain multiple components, but their control policies differ. A fixed retrieval–generation–validation pipeline offers predictable sequencing; a dynamic agent can decide that a failed search warrants a different query or a new tool. [8]

**Compound systems are the broader category**. A compound system need not contain a feedback cycle: a one-way retrieval-and-generation pipeline already combines interacting components. “Big Loop” is used here for the feedback-oriented portion of that design space. This distinction prevents every multi-stage application from being described as an adaptive agent.

### Atomization: what is decomposed and what counts as atomic

**Atomization decomposes operational responsibility**. It can divide an end-to-end task into reasoning operations, learned prediction tasks, callable utilities, memory accesses, or validation steps. An atomic component is a unit the surrounding system treats as a separately invocable responsibility. “Atomic” is relative to the chosen abstraction: a calculator may contain complex software internally while remaining one component from the controller’s perspective.

**An atom needs an explicit contract**. For engineering purposes, a useful component contract specifies its accepted input, output, relevant state or side effects, and success or failure signal. This makes the unit individually testable and potentially replaceable. The June 2024 public study *Large Language Models as Software Components* similarly defines an LLM component through the software that constructs its prompt, invokes the model, and processes its output—not through a requirement for separate model weights. [9]

**Multiple modules are not enough**. Dividing an application into files, services, or role names does not necessarily produce meaningful atomization. A “researcher” and “reviewer” that consume the same unrestricted transcript and issue indistinguishable judgments may duplicate work without separating responsibilities. By contrast, separating tool selection from parameter generation creates a specific intermediate decision that can be inspected and corrected, as demonstrated by TOOLVERIFIER in Findings of EMNLP, November 2024. [10]

**Granularity determines the trade-off**. Fine-grained units provide more opportunities for routing, checking, reuse, and intervention, but create additional transitions and interfaces. Coarser units reduce coordination overhead while exposing fewer internal decisions. The January 2025 public blueprint for Reasoning Language Models explicitly describes this tension: token-level or small-step reasoning permits detailed search, whereas larger reasoning steps can reduce computational overhead and improve interpretability. [11]

**Atomization and orchestration are complementary**. Atomization determines what can be invoked independently; the Big Loop determines when, why, and in what order those units are invoked. A library of excellent tools without suitable routing remains difficult to use, while a sophisticated controller cannot compensate for consistently incorrect components. A dated primary definition explicitly linking the two labels would determine a narrower historical interpretation; the relationship adopted here is a functional synthesis of the documented architectures.

### Atomic-component categories and their interfaces

**Six functional categories recur** across the relevant architectures. They form a working map, not a claim that every paper uses the same taxonomy. CoALA organizes agents around memory, actions, and decision-making; the 2025 journal survey *LLM-Based Agents for Tool Learning* instead identifies executor, perceiver, validator, controller, and retriever components. The June 2025 public CAIS survey describes retrieval, multimodality, agents, and orchestration as architectural axes. [6][12][13]

| Category | Role | Input → output interface | Distinguishing characteristic | Named examples |
|---|---|---|---|---|
| Reasoning and decision | Produce deductions, plans, or candidate actions | Problem state → step, hypothesis, plan, action | Structured inference and alternative exploration | ReAct; Atomic Reasoner; AoT |
| Retrieval and memory | Supply relevant information and retain state | Query/state → evidence, memories, updates | Separates stored information from immediate context | CoALA memory; Sentence-BERT retrieval; MemGPT |
| Tools and actions | Execute operations outside text generation | Structured arguments → result, observation, state change | External grounding and possible side effects | Toolformer APIs; AutoGen executor; ROS2 actions |
| Perception and multimodality | Interpret non-text observations | Image/audio/video → representation or structured observation | Modality specialization and grounding | SAM; CLIP; GraspNet; speech recognition |
| Verification, reward, and feedback | Evaluate candidates or trajectories | Candidate/step/state → score, acceptance, correction | Explicit quality or constraint signal | PRM800K; ToolEval; symbolic verifiers |
| Orchestration, planning, and control | Allocate and sequence execution | Goal/history/feedback → assignments, routing, retries, termination | Manages dependencies and resource budgets | AutoGen; routers; orchestrator–worker systems |

**Reasoning components transform task state**. Their outputs can be a proposed inference, a hypothesis to investigate, a plan, or a candidate action. Atomic Reasoner’s March 2025 public preprint distinguishes premise discovery, premise retrieval, and premise summarization from hypothesis generation and hypothesis verification. It represents these actions as nodes in an Atomic Tree, enabling extension, backtracking, branching, and termination. [14]

**Memory is broader than retrieval**. Retrieval selects information for a current need; memory additionally specifies what is retained, how it is organized, and when it is updated. CoALA distinguishes working memory from episodic, semantic, and procedural long-term memory. A December 2025 public agent survey illustrates related implementations through MemGPT’s main/external-context separation and Generative Agents’ retrieval based on recency, importance, and relevance. [6][15]

**Tool components expose executable operations**. Their outputs may be ordinary return values, errors, files, database changes, or physical actions. Consequently, a tool contract must distinguish read-only observations from state-changing operations. ReAct’s Wikipedia interface primarily supplies information; AutoGen’s code executor can modify a runtime environment; a robot action can alter the physical world. [7][2]

**Perception supplies grounded observations**. A vision component might turn pixels into object masks, labels, spatial relations, or grasp poses, while a speech component turns audio into commands. The December 2025 robot-LAM preprint combines SAM segmentation, CLIP classification, GraspNet grasp estimation, and speech recognition through separate ROS2 nodes. These components contribute different kinds of information, so their outputs should not be treated as interchangeable textual descriptions. [16]

**Verification supplies a different signal**. A generator proposes an answer; a verifier evaluates it against evidence, examples, rules, or learned preferences. The implementation can be a trained reward model, a prompted LLM judge, a compiler, a symbolic solver, or a human checkpoint. These share an evaluation role, but differ substantially in what their judgments establish.

**Control governs the whole execution**. An orchestrator can decompose a goal, retrieve candidate tools, assign workers, merge outputs, and manage retries or stopping conditions. Reasoning and control may share an LLM implementation, but their responsibilities differ: deriving a possible next step is not the same as deciding whether that step is permitted, affordable, or ready to execute. AutoGen’s message interfaces and configurable reply functions make this distinction concrete. [2]

**Interfaces connect the categories**. A useful representation is a directed execution graph whose nodes are model invocations or tools and whose edges carry messages, results, or dependencies. The December 2025 public preprint *Towards a Science of Scaling Agent Systems* formalizes agents and external tools in this way. The topology can be independent, centralized, decentralized, or hybrid; changing topology changes communication and verification behavior without necessarily changing the underlying models. [17]

**Implementation families cross functional categories**. “Tool Components” and “Model Components” describe how a capability is realized, while the six categories describe what it does. A retrieval component can combine an embedding model, a vector index, and deterministic filtering. A vision model can be exposed through a callable tool interface. The distinction is therefore operational rather than mutually exclusive: learned computation and software execution often coexist inside the same functional component.

**Additional documented evidence**

| Entity | Atomic component category inventory | Category purpose and role | Characteristics of each category | Category implementation examples | Category evidence and inclusion status |
| --- | --- | --- | --- | --- | --- |
| Tool Components | no evidence found | no evidence found | no evidence found | API-Bank, MetaTools, the Berkeley Function Calling…[85] | no evidence found |
| Model Components | no evidence found | no evidence found | no evidence found | GPT-3.5 and Gemini Pro 1.0 are concrete model examples…[101] | no evidence found |
| Agent Components | no evidence found | no evidence found | no evidence found | “Communicative agents for software development” is a…[110] | no evidence found |
| Data/Memory Components | no evidence found | no evidence found | no evidence found | Memory Sharing (MS) is a concrete public study and…[90] | no evidence found |
| Model Collaboration | no evidence found | no evidence found | Training-free; complementary off-the-shelf models[125] | no evidence found | no evidence found |
| Multi-Agent Systems | no evidence found | no evidence found | Specialists; higher cost; may overthink simple tasks[139] | “Communicative agents for software development” is a…[110] | Confirmed system pattern; atomic status unresolved[74] |

| Entity | atomic-component category name | component role | characteristics of each category | component examples | category boundary status |
| --- | --- | --- | --- | --- | --- |
| Tool Components | no evidence found | no evidence found | no evidence found | ToolOps; calculators; code interpreters [153][172] | no evidence found |
| Model Components | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Agent Components | no evidence found | no evidence found | Most indexed agents depend on GPT, Claude, or Gemini…[58] | MAP; Claude Code; Plantbot; ALTER3 [135][145][180] | no evidence found |
| Data/Memory Components (candidate) | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |

Cosson, Plougoulen, Morin and Maisonneuve’s public EAGE paper (November 2020) defines Big Loop™ for subsurface operations as a software-agnostic, customizable workflow orchestrator running reservoir-modeling software and scripts [46]. New information triggers iterative model refinement; updates propagate across domains, preserving consistency and alignment [46]. This supplies a domain-specific iterative-workflow example, but not an Atomization definition, LLM taxonomy, single-LLM comparison, or LLM-construction evidence [46].

**Evidence-status limitation**


| Entity or required answer | Status in this part |
|---|---|
| **Big Loop** | No admissible definition, system boundary, scheduling account, interaction description, or review-role finding is available; unresolved here. |
| **Atomization** | No admissible definition, relationship to Big Loop, or terminology-boundary finding is available; unresolved here. |
| **Atomic Components** | No admissible component definition, category roster, inclusion rule, role, interaction, scheduling, limitation, or example is available; the roster remains open. |
| **Tool Components** | No admissible interface, invocation, execution, construction, validation, or example evidence is available; unresolved here. |
| **Agent or orchestration components** | No admissible evidence establishes whether these are components or coordinating roles; status remains uncertain. |
| **Data/Memory Components** | No admissible evidence establishes a separate category or support-layer status; unresolved. |
| **Model Collaboration** | No admissible evidence distinguishes a component category from an interaction relation; unresolved. |
| **Multi-Agent Systems** | No admissible evidence distinguishes a component from a whole-system pattern; unresolved. |
| **Examples and cross-cutting relations** | No admissible examples or corroborating evidence can be carried from this part. |


Terminology is unsettled. Kinnear’s 10 January 2025 Zenodo record presents **Big Loop** as cosmological, not an AI/LLM system, and reports no literature citations [47]. A public article dated the same day describes a universe whose Big Bang is both beginning and end, extending the loop to repeated human actions and a moral challenge [48]. Neither source establishes an AI definition, Big Loop–Atomization relation, or atomic-component roster/characteristics; these remain open, not canonical.

A 2013 study uses “atomization” for fluid spray/injection breakup: inertia+surface tension+viscosity→ligaments/droplets. NS, level-set, fast-marching, density-ratio and immersed-boundary tools cover air/jet/sheet/dual-orifice cases; DNS exceeds clusters; LES: flexible resolution. No AI/Big Loop meaning; exact date absent [49]

Atomization: sparse, separable atoms [50].

Atomization (AI): TSAEs decompose LLM representations into sparse/separable atoms, assessed by R² and q* [50]; 2024 “atomization” means jet breakup, not AI [51].

Atomization: metal powder; no AI [52][53].

Atomic Components are integral dependent parts of a composite; atomic composition joins multiple components n-to-1, with strict forms complete and disjoint, and modules reusable [54]. A component is identified relationally; compositions join into molecular hierarchies through top/free/joined/open/closed constituents, supporting separation of concerns and analysis [54]. This general composition taxonomy is not an AI-specific Big Loop roster or proof that models, tools, or agents qualify; a car example shows overlap [54].

Atomic components are reusable dependent parts of composites; atop/join relations build hierarchies; overlap can duplicate parts; taxonomy is not AI-specific [54].

CFPB (non-AI): atoms→molecules→organisms = increasing complexity; utility classes lie outside. Components are HTML/SCSS/JS, with JS/SCSS omitted if interaction or styling is absent, but no Big-Loop scheduling is specified. Supports decomposition, not an AI taxonomy; last edited 2026-10-16, so ineligible as a pre-2026 example [55]. AriGraph/Ariadne: an agent explores, updates semantic+episodic memory graphs, and uses planning/decision-making in interactive text games. Indexed under agent-based/multi-agent systems, it is one agent—not a confirmed atomic component or whole Big Loop; it shows state/autonomy/coordination, but inclusion remains unresolved [56].

Cutoff: source [57] is a 2026 preprint and ineligible; no eligible evidence here confirms these candidates. Agent Components—reported traits: task decomposition, delegation, runtime spawning, tool access, shared memory and natural-language coordination; category status: uncertain [57]. Data/Memory Components—governed/shared memory is runtime support, not a confirmed category: unresolved [57]. Multi-Agent Systems—open, changing, authority-delegating coordination; only mediated interfaces are covered, so this is system-level rather than automatically atomic: uncertain [57].

Agents uncertain; autonomy 1–5; Claude [58]

Open roster [60]. **Tool Components (supported):** external components; N-ACT/MCP enumerate/invoke tools and pass runtime context; LLM name/inputs → executor validates, calls, and returns results [59][60]. Examples: healthcare scheduling/refills and weather-by-city geocoding; procedures sequence calls; N-ACT says the executor SHOULD retry 5xx errors, while the designer controls escalation [59]. **Model Components:** supported components exposing functionality, outputs, and parameters [60]. **Agent Components:** uncertain; LLM plus executor/orchestrator, with design-time selection and runtime disclosure, but no standard atomic-category status [59][60]. **Multi-Agent Systems:** system-level; task sub-agents use separate procedures/tools and transfer sessions by tool call, reducing context and reportedly hallucinations [59]. **Model Collaboration:** a relation, not a category; orchestration coordinates models, topology, scheduling, and memory [60]. **AutoGen:** a conversational multi-agent graph with code/search/API support; the survey also lists AgentBench and an agent survey [60].

[61] (2026) is ineligible; category status unresolved. Agents are autonomous/semi-autonomous physical/digital executors under user limits, but planning/state/control/interfaces/coordination, strengths/failures, and pre-2026 examples are unreported [62]. G-Memory (2025): Multi-Agent Systems example, not an atomic component [63].

Evidence caveat: this source covers MAS/AgentWare, not Big Loop, and gives no public-availability date; all statuses below are provisional and not cutoff-verified [64].

- **Tool Components (uncertain):** External APIs/services used by agents; hosted Web, Wikipedia and Reddit tools exemplify the role, but Big-Loop inclusion remains unresolved [64].
- **Agent Components (uncertain):** Objectives/roles, perception/action, memory/tools, protocols/environment interfaces; sequential or hierarchical flow, stateful/stateless messages and manual/automated handoffs. Example: Extractor→Summarizer→Teacher→Prompt Creator, with a ROUGE-L threshold and iteration cap controlling revision [64].
- **Data/Memory Components (uncertain):** Private/shared/MAS storage for agent state and interactions; short/long-term memory, variables, vector databases and data sources; separate Big-Loop status is unresolved [64].
- **Model Collaboration (relation):** Providers/models can be selected or switched at runtime; evidence supports orchestration, not an atomic category [64].
- **Multi-Agent Systems (system-level):** A whole arrangement of agents, tools, memory and an application domain; coordination, communication and environment interfaces distinguish it from one component. AutoGen uses sequential execution, stateless messages and automated handoff; developers set order/loops or agents, turn and stop criteria, while team mode can automate messages [64].

MAS:agent/tools/memory;AutoGen:handoff[64]

Atomic components: one-task units pass pipeline outputs (classifier, NER), not necessarily models [66]. Agent Components/MAS: autonomous agents + Reo organization; system-level MAS, not atomic; incident mgmt; uncontrolled info alters behavior [65].

Agent Components—uncertain: Teriyaki’s GPT‑3/PDDL planner; SPEM checks/resets, neither atomic. Model Components—candidate: Teriyaki 9k/1k pairs (95.5% solved; 13.5% shorter; 61.4% wait cut) and 2024 BERT/GPT‑3.5/4/Gemini/LLaMA3.1 [67][68].

WM3C: extra language-controlled blocks (minimal/one-input/independent); identify→dynamics/causal→test; Meta-World 1,818/99, 5M/250K steps [69]. Agent Components uncertain; examples=Cognitive arch./Archer/System-1.x(23–25); MAP Tool Components=Actor-propose/Monitor-gate/Predictor-predict; Model Components=specialist LLMs; Orchestrator=plan; Model Collaboration=recurrent; Data/Memory=task/env text, not separate [70]

Tool Components (supported) expose external services (Toolformer, AutoGen) [72]. Agent Components (uncertain): MEM1 retrieves/adapts via compact state [71]. Data/Memory Components (uncertain): MEM1 consolidates prior/new information internally [71].

Agent Components uncertain; Koala/MAS [73]

Agent Components uncertain; workflow/API decomposition; memory=cap. [74]. Tools supported: ACE/Enrich-3 APIs [76]; CollabToolBuilder propose→code→critique→docs [75].

Capacity conflict: 42 chars insufficient.

Agent category uncertain; ARM example [77]

Atomic components: nodes (1 embodiment, 0+ physics models; flow/interface edges). Agent Components: uncertain, not canonical; 2025-11-06 nine-role MAS uses checkpointed orchestration vs Generator–Reflector 2AS; exploration/termination improve, but coverage ≤20% and physics/code fail. Data/Memory: 2024 survey only; unresolved [78].

Atomic components: agents coordinate decomposition, coding, ranking, execution [78].

AgentScope: Agent Components uncertain; agents→subtasks/interrupts; MsgHub/Pipelines exchange/sequence/remove agents; Planner→decompose/spawn workers/assign tools/persist state. message; Tool/Model Components: JSON-schema tools/unified async API; Memory: short/long ctx; parallel I/O cuts latency; usage:tokens/latency. Refs ToolLLM/Toolformer/ReAct/LATM/EasyTool/ToolACE; RAG/MoE/LoRA [79]

Tools:RAG/API;models:swap embed/gen;agents:hint/guess;plan/code;data/memory:store;multi-agent:async queues/loops;collab:co-design[80]. LoopTool:2025↔2026;excluded[81]

MC? Gemma/Axbench/edit/DPO/SAE/heads [82]

Agents/memory uncertain; Mars/SkillLib[83]

Tool Components yes [84]; agent/mem? [83]

Tool Components: supported NLT/Toolformer; atomic status unresolved; selects→parses→executes→responds [85]. Agents uncertain: ReAct/water ABMs [85][86]. Data/memory uncertain: Zep/A‑MEM/MemoryOS [87][88][89]

Agent Components: candidate; 3/domain specialized agents share memory; Data/Memory Components: uncertain; MS stores/scores/retrieves/shares QA pairs; Model Collaboration: uncertain relation; shared memory unnamed; Agent refs bibliographic [90][91]

OSC: multi-agent candidate; tools/RAG aid LLMs; mem/collab unclear [92][93][94]

Multi-Agent Systems≠atomic; Agent comps=unc; Model comps=unc; Model collab?[95][96]

Tool Components: CRAFT tools [97]; Model Components partial [98]; 2026 out [99][100]

AI techniques ≠ Big Loop categories [102].

Tools/APIs;model;agent/memory?;no-MAS[103]

The 2026 survey is post-cutoff and excluded [104]. Eligible 2025 evidence is indirect: data, models, programs and infrastructure are named, not a Big Loop taxonomy [105][106]. **Model Components** are self-contained models plus rules/submodels; prompts, agents and retrieval stay external [106]. **Tool Components** map provisionally to engineered programs (retrieval/apps) [106]. **Agents** and **Data/Memory** remain uncertain: non-learned agent parts are programs; data spans training/RLHF, symbolic, retrieval and Internet sources [105][106]. **Multi-agent systems**—uncertain [106]

Agents/multi-agent/memory: uncertain [108]; Agentic DataOps [107]; dynamic graph [108]

Agent?=adapt; Tool=API/lib[109]; MAS=sys; Mem=short/long; Collab=vote/role/deb[110]

No eligible pre-2026 evidence is available

VISION’24: tool/model; agent open [111]

Coscientist uses tools, LLMs, agent [112].

AtomR: Search, Relate, Filter—atomic [113]

AtomR defines Search, Relate, Filter [113]

AtomR: Search=disambig; Relate=1-hop; Filter=attr.; other cand.?; pub25-8-3 [113]

Atomic ops are Search/Relate/Filter [113]

Tool Components: supported—ACE OpenAPI→Python, top‑k/Enrich‑3 [114]; Model Components: supported—HEPTAPOD (17-Dec-2025), FeynRules→UFO→MadGraph→Pythia→FastJet [115]; Agent/orchestration: supported candidate—schema tools/LLM/sandbox; multi-agent: uncertain—Agenticsciml [115].

Tools+ LLMs+ Agent?/Mem?/Collab?/MAS?[116]

Tools: RE-GAINS/EnChAnT [117]; agents uncertain: PromptPilot [118], facilitator [119].

Data/Memory Components: MoMA uses external memories; category status uncertain [120]

Agent Components (uncertain): perception/reasoning/memory/action/tools/planning; local rationality ≠ coordination/stability; LLMTraveler/AGENTS-LLM [121]. Model Collaboration (relation, not category): TrafficGPT/MAPPO/dual-agent LLM coordination [121]. Multi-Agent Systems (system-level): MARL/CCMA/AgentSUMO; coordination/stability limits [121]. Tool Components: LA-Light/Open-TI; Model Components: TPLLM/GPT4TFP/Strada-LLM/GPTTC/HighwayLLM/LightGPT [121]

Agent Components (uncertain): autonomous planners/tool users; Open-TI/LLMTraveler show flexible, costly, safety/latency-limited execution. Model Collaboration: LLM↔physical feedback, not category; Multi-Agent Systems: system-level, not atomic [121]

Agents: reciprocal feedback [122].

AutoGen: Agent Components: async/event-driven units; unresolved [126]. Multi-Agent Systems: orchestration, not component [126]. LMC: model collaboration, not category [125]. 2026 evidence excluded [124].

Agents: post-cutoff; excluded [127][128]

Agent components/model collaboration/MAS/AutoGen: unresolved; [129] post-cutoff.

Multi-Agent Systems: system paradigm, not atomic; collab/learn; auto 4-tier memory promotes/consolidates/distills; monolithic limits; micro-benchmarked storage [130].

Post-cutoff source; exclude claims [131].

Agent? worker [133]; mem unresolved [132]

Agent Components:role/task;Multi-Agent Systems:system/uncertain;trace[115,116,117]

Agent roles differ; systems compose.[134]

Agents/MAS?uncertain;gain/filter[134][135]

Agents: BDI/svc/msg/ATC; uncertain [136]

Agents: uncertain; MAS=system-level [137].

Agent Components: planning modules [138]

Capacity conflict: facts exceed 41 chars.

Agent Components remain uncertain: an agent has model, objective, environment, input/output; it can learn, plan, reason, decide, specialize, coordinate via cooperation/competition/coopetition [140]. Structures: peer-to-peer/centralized/distributed/hierarchical; strategies: rule/role/model-based. Multi-Agent Systems are systems; orchestration is a candidate role. AutoGen shows subtask decomposition; DAGs schedule parallel/serial tasks and merge outputs. Benefits: scale, fault tolerance; risks: communication/coordination costs, infinite loops, cascading hallucinations [140].

Uncertain agents decompose tasks, assign roles; AutoGen coordinates [140]. MASs are whole-system: static/dynamic, central/decentralized; costly/failure-prone [140].

Agent components:roles/IO; MAS=whole[141]

Model Components (software): Leaf/Frame composition, provided/frame interfaces, and mutable roles [142]. Agent Components plan/act, use tools, revise by feedback, may orchestrate; Multi-Agent Systems are whole-system patterns; failures cascade [143].

Toolshed's five fields—name, description, schema, questions and topics—map retrieved metadata to Python functions; it adds no atomic category. Recall@1/5/10 uses 50/25/25 name/key/value weights [144].

Model Components — text/logit/weight; retrieval/routing/LoRA/MoE/reward; roster open. Model Collaboration — API/text/logit/weight exchange; relation≠category [146].

Model Components remain unresolved under the cutoff: a cited 2026 paper [147] has no established pre-2026 availability; inputs/outputs, API/text/logit/weight interfaces, specialization, routing, feedback, efficiency and handoffs cannot be claimed.

Model Components: task-specific CNN [148]

Model Components=experts+router; token/word/sentence→top-k outputs; shared/load-balanced/specialized; OLMoE: 7B total/1B active,8/layer,top-2; taxonomy open [149].

Capacity conflict: obligations exceed 41.

Agents/MAS uncertain; no eligible evidence

Agents: memory; MAS system-level [151]

Agent?;ToolOps loop;DIMAS sys[153][152].

Agent stateful; MAS sys; AutoGen coord[154]

AutoGen/MAS coordinate; agents plan [155]

Agent/MAS cards are post-cutoff (2026); ineligible, so no claim is retained [156].

Agents: system-level; AutoGen(2023) [157]

SoSAA agent?: beliefs/acts; MAS≠atom[158]

Agent Components:context;MAS=system[158].

Agent Components may be autonomous, goal-directed, stateful, delegating or reactive; SoSAA agents rewire sensors via interfaces [123][158][159]. MAS is a coordinating layer, not an atomic component [158].

Agents: local autonomy/coordination [160]

MAS=whole[160]; Agent=autonomous[161].

Agents plan/act; memory/MAS open; AutoGen: +15% gain/134-task ALFWorld [162][163].

AutoGen: coord.; category uncertain.[164]

Agent Components: stateful I/O subcomponents; autonomous; coordinate by links [165]

Agent=plan/ctl; MAS=compose [165][166]

Agent Components: autonomous units [167].

Agents are sandboxed and monitored [168]

Agent Components (BDI; uncertain) watch hosts, inject events; endpoints coordinate. MAS is system-level, not atomic; reuse costs traceability/performance [169].

Agent Components: coordinate events.[169]

Agents: autonomous/stateful; memory: support; multi-agent systems coordinate [170]

Agents: autonomous; memory support-layer; MAS system-level; atomic status TBD [170]

Agents and multi-agents: uncertain [171].

Agents open; AutoGen coord[173][174].

Agent/MAS: orch↔subs;collab AutoGen [175]

Capacity conflict: 41 chars < obligations.

Agent Components are framework-specific, supported but uncertain: a separable core-agent links an LLM to tools and has planning, memory, profile, action, and security modules; active managers are stateful, passive executors stateless [178]. ToolLLM retrieves APIs, relays them to an LLM, executes calls, and returns results [178]. Multi-Agent Systems are higher-level: core-agents may coexist and need sync or a gateway. Data/Memory Components unresolved; ChatDB has LLM controller and DB memory [178].

Agent components;MAS=whole;AutoGen[179]

Agents/AutoGen/NaviAgent:coord[181][182]

Agent status unresolved; coordinate [183]

Agent uncertain; peers interact[184][185]

Agents loop;AutoGen/tool/MAS?[186][187]

AutoGen coordination; redundancy [188]

Agent coordinates; planning unknown [189]

Agents: memory→reason→grounding;unc.[190]

Tool Components: models/retrievers/tools; Murakkab/ReAct DAG [192]. Agents: uncertain—goal decomposition/tool action; orchestrators schedule/process/memory [225,229]. OSC collaborator models/messages; ToM/joint planning/robustness weak [223,224,225]. Data/Memory open; memory layer [192]; Mixer scopes/demo/repairs automation [191].

Agent Components route hierarchically[193]

Agent components: plan→tools→feedback; autonomous, composition-risky [195]. TOOLMAKER Dockerized tools/self-correction: 80%/15 tasks, >100 tests [194]. Multi-agent systems: system-level, unresolved [196].


Model collab.=rel.; MAS=system [239,247].

Capacity conflict: 41 chars; facts exceed

AI-Researcher (NeurIPS 2025; public date unspecified) is indirect evidence: it defines neither “Big Loop” nor “Atomization.” It treats an atomic component as a fundamental, indivisible research element, decomposing objectives into units linking mathematics to code. [199]

Tool Components are Coding, File and Planning. Coding: gen_code_tree_structure/read_file/create_directory/list_files/run_python/write_file/create_file/execute_command; File: terminal_page_down/up/to/open_local_file/page_up/down_markdown/find_next/find_on_page_ctrl_f/question_answer_on_whole_page/visual_question_answering; Planning: plan_dataset/training/testing. Model components, pipelines and evaluation modules are decoupled at defined entry points, supporting reproducibility and extensibility. [199]

The source’s paradigms—not confirmed atomic categories—are Tool Integration (LangChain/HuggingGPT/OpenAgents), Multi-Agent Collaboration (MetaGPT/AutoGen/AgentScope/CAMEL), and Self-Directed Execution (Manus/OpenManus/OWL/AutoAgent). Cited years span 2023–25, but exact availability dates are absent; agent and multi-agent inclusion therefore remains uncertain. [199]

Construction covers dataset/model/training/testing plans (data pipeline; formula/details/references; loss/optimization/config/logging; metrics/data/code); unit/integration tests and success criteria are required. Resource/Paper/Code Analysts, Plan/Idea/Code, Advisor/Judge, Code Review and Experiment Analysis agents exchange knowledge and refine recursively; prototypes use 1–2 epochs or small subsets before scaling or being marked “unfeasible.” [199]

Atomization: no direct definition found; SoAy decomposes API sequences→code (34.58–75.99% gains; public artifacts) . Agent status unresolved: HuggingGPT plans/routes models [206]; autonomy, async voting, supervisor-led subagents [149,257,413].

Big Loop (2024): end-to-end optimization; Atomized AI: reusable/schedulable decomposition (general/adapt/interface) [202]. “Atomization”: exact independent definition absent; snippets: tools expand LLMs . AutoGen (2023): agent/human/tool dialogue (math/coding/QA); iterative code evaluation [205][204]. MAS unresolved at cutoff; machine-tool components excluded [207].

Taken separately, the permitted workflow and representation studies do not establish a direct Big Loop–Atomization relationship: Big Loop is documented as a system-level label for an automated interdisciplinary workflow [46], whereas Atom Theory defines atoms as internal LLM representation units under the atomic inner product [50]. The separate fluid-breakup and metal-powder meanings of atomization [51][52] reinforce the scope limitation, so they cannot bridge the two AI scopes.

Under the API-, text-, logit- and weight-level information-exchange classification, Model Collaboration is an interaction and coordination relation among model units, not an independently established atomic-component category [125]. The units exchange information and control at those levels; routing, debate, collaborative decoding and model-parameter interaction are concrete mechanisms [146].

From an input or high-level goal, Big Loop schedules its Atomic Components by decomposing work into subgoals, assigning roles, routing messages and actions, and invoking Tool Components and Model Components through Agent Components; MAP-like modules monitor validity, predict states, provide feedback, and terminate at goal completion [135][138][140]. A Big Loop-like tool-learning cycle plans, selects a tool, executes the task and generates a response [177]; asynchronous execution, shared memory and message passing connect modules [180], while LLM-engine adapters represent Model Components [176].

Big Loop frames an example-rich review as an end-to-end orchestration case: the public workflow uses an orchestrator, iteratively refines models as information arrives, and propagates updates across domains [46]. The accuracy limitation is terminological—another public use calls Big Loop a cosmological hypothesis rather than an AI/LLM system [48]—so the review should label the workflow scope instead of treating the name as a universal definition.

Atomization organizes the review as a decomposition lens, but its scope must be explicit: formal Atom Theory defines representation-level atoms under the atomic inner product, with representability, sparsity and separability [50], while the systems framing treats atomic capabilities as reusable units with clear interfaces and boundaries [200]. Tool learning, external-tool use and parallel invocation can illustrate the systems lens , whereas fluid and metallurgy uses are neighboring meanings rather than AI categories [49][52].

Atomic Components define the unit of analysis as an integral, dependent part of a composite whole; components are the parts from which compositions are constructed and joined [54]. This boundary directs the review toward modular component/composition relations rather than treating a composite system as an indivisible unit [54].

Agent Components clarify the category boundary as separable, role-specialized decision units: they plan, maintain working memory, act, verify or critique, receive state or goal context, and return actions or feedback, with autonomy bounded by coordination [137][150][167][188]. In orchestration, a controller or high-level planner dispatches specialists and aggregates outputs; the orchestrator–worker case shows delegated rather than fully independent control, preserving traceability while separating agents from the coordinating system [179][193][133].

Data/Memory Components should be retained in the review as a candidate support layer, not asserted as a canonical category: external memory repositories supply retrievable context for agent decisions, and MoMA implements retrieval-plus-generation [162][120]. Evidence is mixed and the boundary remains unresolved—some memory artifacts do not satisfy a feedback-loop criterion [122]—so confirming the category would broaden the roster, while rejecting it as a category should still preserve memory and retrieval mechanisms as agent support [120][162].

Model Collaboration belongs in the interaction layer, not the atomic-component roster: the Large Model Collaboration framework combines distinct off-the-shelf models in a training-free, complementary arrangement [125]. The taxonomy should therefore describe routing, cascading, cooperation or competition and API-, text-, logit- and weight-level exchange as relations among Model Components, using edge–cloud dependency routing as a concrete case [146][197].

Multi-Agent Systems are a supported system-level coordination pattern, not automatically one atomic component: they decompose complex tasks among specialized agents and tools, while constituent agent and tool units remain the relevant boundaries [139][137]. This distinction lets the review analyze hierarchical or decentralized coordination patterns and their system-level behavior without conflating orchestration with a constituent component [198][169].

AutoGen provides a concrete Agent-Component coordination case: an orchestrator selects the next expert, specialists use tools and write results to shared memory [187]. Its code-generation example evaluates generated code and invokes iterative LLM refinement [204], showing how delegation and feedback form a loop rather than a single model call [187][204].

Permitted Holistic-AI evidence supports a complementary architectural relationship: Big Loop supplies end-to-end optimization and coordination, while Atomization decomposes capabilities into reusable atomic units with clear interfaces and boundaries [200][202]. In that framing, Atomization supplies the units and the workflow orchestrator connects and iteratively refines them [46][200]; the limitation is that Atom Theory also uses atoms for internal LLM representations [50], so this systems relation is not a universal definition.

In Big Loop, Tool Components, Model Components and Agent or Orchestration Components operate as distinct but composable Atomic Components: planning decomposes a request and allocates work; models reason or select, tools are retrieved or generated and executed, and memory or environment state returns to agents for replanning and feedback [201][170][203]. Coordination may be hierarchical, peer-to-peer, hub-based or channel-based, with event propagation and explicit protocols mediating delegation; this closes the end-to-end loop but makes coordination and security controls material design concerns [140][169][203].

Big Loop’s useful role in this direction is as a system-level workflow label: a public subsurface study uses a workflow orchestrator over modeling software and scripts, iteratively refines models as data arrives, and propagates updates across domains [46]. Because another public use defines Big Loop as a cosmological hypothesis [48], the review should present the workflow as a bounded example and not claim that the name alone establishes an AI-system definition.

### Terminology ambiguities that matter technically

**An atom can denote different objects**. The literature applies atomic language to reasoning actions, reasoning states, hidden representations, mathematical abilities, and editable outputs. Likewise, a loop can exist inside a neural network or outside it in application control. These distinctions change what is being constructed and what evidence would support an improvement.

| Study and public period | Object being decomposed | Meaning of the unit | Relation to this review |
|---|---|---|---|
| Atomic Reasoner, March 2025 preprint | Reasoning process | Premise and hypothesis actions | Operational reasoning components [14] |
| Atom of Thoughts, 2025 preprint | Reasoning trajectory | Self-contained problem states | State-transition design [18] |
| *Towards Atoms of LLMs*, September 2025 preprint | Internal representations | Sparse, separable representational units | Interpretability, not service decomposition [19] |
| Componentization, September 2025 preprint | Model response | Linked, editable semantic units | Output and interaction architecture [20] |
| Atomic-thinking study, NeurIPS 2025 | Mathematical competence | Field-specific and logical abilities | Training/evaluation decomposition [21] |
| LoopLM, October 2025 preprint | Internal computation | Repeated shared-weight transformations | Model architecture, not external orchestration [22] |

**Reasoning states differ from actions**. Atom of Thoughts, or AoT, constructs a temporary directed acyclic graph of dependencies, then contracts it into a self-contained next problem intended to preserve the answer. This is different from Atomic Reasoner’s selection of an operation such as premise discovery or hypothesis verification. AoT emphasizes state sufficiency; Atomic Reasoner emphasizes explicit action selection. [18]

**Representational atoms are not tools**. *Towards Atoms of Large Language Models* defines atoms using representability, sparsity, and separability of internal representations. Its concern is identifying stable representational units, not building a calculator, retriever, or planner interface. Similarly, the NeurIPS 2025 atomic-thinking study separates mathematical fields—algebra, geometry, analysis, and topology—from logical abilities such as conceptual understanding, forward reasoning, and counterexample-driven backward reasoning. [19][21]

**The conceptual judgment is straightforward**: atomization exposes meaningful units and contracts, while the Big Loop composes those units through state, control, and feedback; neither term should erase the differences between application architecture, reasoning methods, and neural-network internals.

## 2. Advantages of Big Loop Systems Compared with a Single LLM

### Establishing a fair single-LLM baseline

**The primary baseline is one call**. Conceptually, the comparison is a general-purpose LLM receiving a prompt and producing an answer without external execution, persistent application memory, or a controller that revises its actions. Such a model can still perform substantial reasoning within its generated response. The relevant distinction is access to additional operations and feedback, not an assumption that a single LLM merely retrieves memorized sentences.

**Single-agent is a stronger baseline**. A single agent may already use tools, memory, and repeated model calls. The May 2025 preprint *Single-agent or Multi-agent Systems? Why Not Both?* defines a single-agent system, or SAS, as an execution graph with one LLM node, and a multi-agent system, or MAS, as one with multiple LLM nodes. Its results therefore address the incremental value of multi-agent organization, not the entire difference between a bare model and a compound system. [4]

**Different comparisons answer different questions**. Adding a calculator tests external computation; adding a verifier tests selection or correction; adding workers tests division of labor. A system that changes all three at once can demonstrate an end-to-end improvement, but that result does not identify which intervention produced how much of the gain. The analysis below consequently retains each study’s stated baseline.

### Capability Enhancement: stronger reasoning through complementary resources

**Capability gains can be substantial**. Tool use, execution feedback, and task isolation have all produced improvements, but on different tasks and against different baselines. The following results establish the scale and variety of the documented evidence without treating them as one pooled effect.

| Study | Task or workload | Stated baseline | Augmented-system result | Comparison |
|---|---|---|---|---|
| Toolformer, 2023 paper | LAMA SQuAD subset | Best reported baseline | Higher accuracy | +11.7 percentage points [23] |
| Toolformer, 2023 paper | LAMA Google-RE | Best reported baseline | Higher accuracy | +5.2 percentage points [23] |
| Toolformer, 2023 paper | LAMA T-REx | Best reported baseline | Higher accuracy | +18.6 percentage points [23] |
| AutoGen, 2023 report | Full MATH test set, 5,000 problems | GPT-4: 55.18% accuracy | 69.48% accuracy | +14.30 points, calculated [2] |
| ReAct, ICLR 2023 | ALFWorld | Imitation/RL methods | Higher success rate | +34 percentage points [7] |
| ReAct, ICLR 2023 | WebShop | Imitation/RL methods | Higher success rate | +10 percentage points [7] |
| Omar et al., August 2025 preprint | Clinical batch: 5 tasks | Single agent: 73.1% accuracy | Multi-agent: 90.6% | +17.5 points, calculated [24] |
| Omar et al., August 2025 preprint | Clinical batch: 80 tasks | Single agent: 16.6% accuracy | Multi-agent: 65.3% | +48.7 points, calculated [24] |

**External resources remove specific bottlenecks**. Toolformer uses a 6.7-billion-parameter GPT-J-based model trained to select and invoke APIs, including question answering, search, calculation, calendar, and translation services. Its LAMA results show that external information can improve factual completion even when the language model is much smaller than comparison models such as OPT-66B and GPT-3-175B. The mechanism is access to an appropriate resource, not a general replacement for model capacity. [23]

**Execution changes the reasoning problem**. AutoGen’s mathematical system allows a model to generate code, receive its execution result, and revise its response. On the full MATH test set, the calculated accuracy difference is 69.48 − 55.18 = 14.30 percentage points. This demonstrates the value of a complete generation–execution–feedback system using GPT-4; the intervention includes executable computation and orchestration, not merely additional agent names. [2]

**Decomposition can narrow each decision**. An end-to-end prompt may simultaneously demand premise extraction, planning, arithmetic, formatting, and checking. Separating those responsibilities lets each invocation focus on a more constrained objective. Atomic Reasoner operationalizes this by choosing an atomic reasoning action before executing it, with routing that can extend a chain or backtrack to explore another branch. [14]

**Narrower decisions still need good guidance**. Atomic Reasoner argues that specialized actions concentrate the output distribution within smaller reasoning subspaces. That is a useful mechanism hypothesis, but a smaller action space does not itself ensure that the selected action or resulting inference is correct. Its experiments make the boundary visible: linguistic logic benefits more consistently than mathematics, where specialized external feedback can be decisive.

| GPT-4o-mini reasoning strategy | MATH score | BBH average score |
|---|---:|---:|
| Chain-of-thought | 76.8 | 65.0 |
| Best-of-N | 81.5 | 67.7 |
| Atomic Reasoner | 79.1 | 78.8 |

**The task determines the winner**. In Atomic Reasoner’s March 2025 preprint, best-of-N leads on the reported GPT-4o-mini MATH comparison, while Atomic Reasoner leads on BBH. For GLM-4-FlashX, Atomic Reasoner and chain-of-thought both score 52.9 on MATH. These results support targeted reasoning decomposition, while arguing against a universal claim that finer-grained reasoning always improves every task. [14]

**State isolation protects independent tasks**. Omar and colleagues’ 24 August 2025 clinical-workload preprint assigns heterogeneous retrieval, extraction, and dosing tasks to dedicated workers. Between batches of 5 and 80 tasks, pooled multi-agent accuracy falls by a calculated 25.3 percentage points, compared with 56.5 points for the single-agent configuration. The authors attribute this pattern to reduced context interference through task isolation, across four evaluated model checkpoints. [24]

**Verification enables correction rather than repetition**. A useful feedback loop supplies information that changes the next attempt: a failing test identifies an incorrect behavior, a compiler reports an error, or a symbolic engine rejects an invalid deduction. Repeating a question without new evidence may instead reproduce the same misconception. AlphaGeometry illustrates complementary specialization: an LLM suggests geometric constructions, while a symbolic engine derives and checks consequences, according to the 2024 BAIR account. [1]

**Memory supports longer reasoning horizons**. A stateless call must receive all relevant information in its prompt. A memory-enabled system can retrieve earlier decisions, retain task progress, and preserve facts across separate execution phases. This does not eliminate information loss: the benefit depends on retaining the facts that later decisions actually require. CoALA’s distinction between working and long-term memory is useful precisely because storage and active reasoning context serve different purposes. [6]

**Stronger models can reduce collaboration gains**. The May 2025 SAS/MAS study reports that the MAS-over-SAS accuracy improvements narrowed when moving from original ChatGPT results to Gemini-2.0-Flash: 10.7% to 3.0% on MetaGPT-HumanEval, 16.0% to 1.2% on SelfCol-MBPP, and 9% to 0.8% on MathDebate-GSM8K, using the paper’s reported improvement figures. It also finds that multi-agent execution can underperform on simple tasks through overthinking, while difficult AIME tasks remain a stronger fit. [4]

**The capability judgment favors complementarity**: Big Loop systems are most persuasive when they add missing knowledge, executable computation, useful isolation, or independently informative checks; adding repeated reasoning without those resources has a much less reliable payoff.

### Functionality Expansion: from answering to operating

**New operations are a distinct benefit**. Capability enhancement means doing an existing task better; functionality expansion means making a new class of operation possible. An LLM can describe how to update a database, but a connected system can actually issue an authorized update and inspect the resulting state. That functional difference exists even before an accuracy improvement is established.

| Implementation and public period | Interface | Modality | State or side effects | Checking mechanism |
|---|---|---|---|---|
| ReAct, 2022/ICLR 2023 | Query → Wikipedia observation | Text | Primarily read-only | Evidence-guided reasoning [7] |
| RAG, described in June 2025 CAIS v1 | Query → retrieved passages | Text/documents | Index and retrieval state | Source grounding [13] |
| ToolLLM, 2023/ICLR 2024 | Structured call → REST response | Text/JSON | Service-dependent | ToolEval and execution [3] |
| AutoGen, 2023 report | Code/function → execution result | Text/code | Runtime and artifact changes | Execution feedback; safeguards [2] |
| m&m’s, March 2024 preprint | Typed plan → tool results | Multimodal | Generated artifacts | Typed composition; real execution [25] |
| AlphaGeometry, 2024 account | Construction → derived facts | Geometric/symbolic | Proof state | Symbolic engine [1] |
| Robot LAM, December 2025 preprint | Goal → bounded robot actions | Vision/audio/action | Physical motion | Plans, constraints, human review [16] |

**Retrieval separates knowledge from weights**. A retrieval-augmented generation system can index an external corpus, retrieve relevant passages, and condition the answer on them. Updating the corpus can change the system’s accessible information without retraining the generator. This also enables access-controlled applications in which evidence selection depends on a user’s permissions, a motivation emphasized in the February 2024 compound-systems essay. [1]

**API access broadens the action space**. ToolLLM’s ICLR 2024 paper describes ToolBench’s 16,464 REST APIs across 49 RapidAPI categories. The associated 2023 public version reports 3,451 retained tools, 126,486 instruction–solution instances, and 469,585 real API calls. These counts describe the scale of tool exposure and training data; successful use additionally requires selecting the right endpoint, supplying valid arguments, and interpreting its response. [3][26]

**Code execution produces inspectable artifacts**. AutoGen can combine agents that write code, execute it, interpret results, and solicit human feedback. This extends a language interface into mathematical computation, optimization, file generation, and interaction with application-specific dependencies. Its OptiGuide example coordinates code generation, a safeguard check, execution, and interpretation of a supply-chain optimization result. [2]

**Specialized models add modalities**. The March 2024 m&m’s benchmark integrates 33 executable tools: 13 multimodal machine-learning models, 11 image-processing modules, and 9 public APIs. It constructs typed tool graphs and executes plans against real inputs. The example shows why a tool inventory is more useful when interfaces are composable: an image-processing output must have the form expected by the next operation. [25]

**World state creates hidden dependencies**. ToolSandbox, published in Findings of NAACL in April–May 2025, defines stateful tools as operations that inspect, depend on, or manipulate world state. Its messaging example requires cellular service to be enabled, while enabling that service may first require disabling low-battery mode. The necessary sequence is therefore “disable low-battery mode → enable cellular service → send the message,” with observations determining whether each prerequisite is satisfied. [27]

**Observation is more valuable than intention**. A model-generated plan stating that a message was sent is not evidence that sending succeeded. A closed loop can inspect the actual tool response, identify a connection error, repair the prerequisite state, and retry. ToolSandbox’s 34 tools and 1,032 scenarios make these distinctions explicit through mutable state, conversational clarification, and intermediate milestones. [27]

**Robotics extends the same pattern physically**. The December 2025 robot-LAM prototype places perception, high-level reasoning, medium-level orchestration, and low-level motion control in separate modules. The LLM does not directly emit unrestricted motor-control code; it produces a bounded action sequence or a formal planning problem that downstream components process. This is genuine functionality expansion, because the output changes the physical environment rather than merely describing a possible action. [16]

**Action access changes the risk profile**. A failed retrieval can degrade an answer, whereas an incorrect refund, deletion, or robot movement can change external state. The architectural implication is to separate proposal from authorization and execution. Read-only evidence gathering can generally be treated differently from irreversible actions, and successful completion should be checked against the resulting state rather than the fluency of the final explanation.

**The functionality judgment is operational**: external components turn an LLM into an interface to knowledge, software, specialized models, and physical devices, but every added operation also introduces interface, permission, state-management, and reliability obligations.

### Computational Efficiency: selective effort versus coordination overhead

**Efficiency is not an intrinsic property**. A compound system can save resources by avoiding unnecessary large-model work, or spend substantially more by duplicating context and generating coordination messages. The central question is which execution strategy delivers the required quality under the relevant resource constraint.

| Design or study | Comparison basis | Resource measure | Reported result |
|---|---|---|---|
| SAS/MAS study, May 2025 preprint | MAS versus SAS, seven datasets | Input and output tokens | 4–220× prefill; 2–12× decode [4] |
| Anthropic Research, 2025 engineering report | Agents/MAS versus chat | Tokens | About 4× / 15× chat use report [28] |
| SAS/MAS request routing, May 2025 | Hybrid versus always-MAS | Reported serving cost | 50% of MAS cost on GSM8K+AIME [4] |
| FrugalGPT, described by BAIR in 2024 | Cascade versus LLM services | Monetary cost at matched quality | Up to 90% lower cost [1] |
| Clinical orchestration, August 2025 preprint | Task-isolated MAS versus single agent | Tokens | Up to 65-fold lower usage [24] |
| Anthropic parallel research, 2025 report | Parallel versus sequential execution | Research time | Up to 90% reduction [28] |
| AsyncThink, 30 October 2025 preprint | Asynchronous versus parallel thinking | Inference latency | 28% lower latency [29] |
| LoopLM, October 2025 preprint | Looped versus larger standard models | Parameter efficiency | Approximately 2–3× [22] |

**Coordination can dominate token consumption**. In the SAS/MAS study, multiple agents repeatedly process upstream messages and generate debates, reflections, or summaries. Across seven datasets, the prefill-token ratio reaches 4–220 times SAS usage. Even the study’s favorable assumption of perfect context reuse leaves MAS requiring 2–12 times as many decode tokens. [4]

**Selective routing avoids universal escalation**. The same study uses an LLM rater to estimate request difficulty, assigning easier requests to SAS and harder requests to MAS. With Gemini-2.0-Flash as rater on GSM8K+AIME, the authors report “2% better accuracy” at 50% of always-MAS cost. This result supports adaptive execution; its reference point is an expensive always-multi-agent policy, not a claim that the hybrid necessarily costs half as much as one bare LLM call. [4]

**Cascades require useful verification**. Another strategy first tries a cheaper system and escalates only when its answer fails a check. The economic logic can be expressed without assuming particular prices. If the first attempt costs \(c_s\), verification costs \(c_v\), escalation costs \(c_m\), and a fraction \(p\) of requests escalate, the expected cost is:

\[
C_{\mathrm{cascade}}=c_s+c_v+p\,c_m.
\]

**The saving has a threshold**. Relative to always paying \(c_m\), this simplified cascade is cheaper when \(p<1-(c_s+c_v)/c_m\), assuming common costs cancel. This is an analytical condition, not a measured result. It also exposes the quality problem: a verifier that wrongly accepts bad answers can produce apparent savings by silently reducing reliability.

**Reuse avoids solving identical classes repeatedly**. Answer caching reuses a previous response; functional caching reuses an operation that solves many different instances. LATM’s ICLR 2024 framework generates reusable Python tools with a stronger model and lets a cheaper model translate later requests into function calls. The reusable object is an algorithm or utility function, so its value can persist even when the natural-language wording changes. [30]

**Parallelism saves waiting, not necessarily work**. Anthropic’s 2025 engineering report describes 3–5 subagents operating in parallel, with subagents also using three or more tools concurrently, and reports research-time reductions of up to 90% for complex queries. The same report says multi-agent systems typically use about 15 times as many tokens as chats. Reduced wall-clock time and reduced total computation are therefore separate outcomes. [28]

**Dependencies determine parallelization value**. Independent source investigations can proceed concurrently, whereas tightly coupled tasks require repeated synchronization and shared context. For independent tasks with durations \(T_i\), a simple analytical approximation changes serial time from \(\sum_i T_i\) to \(\max_i T_i+T_{\mathrm{coord}}\). Shared-state conflicts, limited concurrency, and slow workers increase the coordination term and can erase the benefit.

**Asynchrony can reduce synchronization stalls**. AsyncThink’s public preprint, submitted on 30 October 2025, uses an organizer that delegates subqueries, merges intermediate knowledge, and coordinates concurrently executable reasoning structures. It reports 28% lower inference latency than parallel thinking while improving mathematical-reasoning accuracy. The comparison establishes an improvement among organized reasoning strategies, rather than a direct speed advantage over one ordinary model call. [29]

**Task isolation explains apparently opposing results**. The clinical-workload study reports up to 65-fold lower token use for its orchestrated configuration, while debate-style MAS evaluations report substantial increases. The difference is architectural: splitting an accumulating heterogeneous workload into clean task contexts can avoid repeated context processing; adding communicating agents to a task already handled compactly can create redundancy. “Multi-agent” alone is too broad a description to predict cost. [24][4]

**Internal efficiency is another design axis**. LoopLM reuses weight-tied Transformer blocks and learns when to exit recurrent computation. Its reported parameter-efficiency improvement concerns model size for broadly comparable benchmark performance, not an equivalent reduction in inference operations or application cost. A smaller parameter footprint can help deployment while repeated internal passes still consume computation. [22]

**The efficiency judgment favors adaptive systems**: use selective routing for mixed difficulty, reusable tools for recurring task classes, and parallelism for independent work; prefer a compact single-model execution when coordination adds more work than it removes.

### User-Centric Design: controllability, personalization, and safe delegation

**User benefit extends beyond answer accuracy**. A useful system should help users express preferences, inspect progress, correct assumptions, control consequential actions, and complete tasks with reasonable effort. Atomization makes intermediate decisions addressable; orchestration determines when those decisions become visible or require approval.

**Persistent preferences reduce repeated prompting**. ExploreLLM’s 2023 public prototype combines a structured task tree with shared personal preferences, selectable options, and summarization. For travel planning, it separates questions such as dates, accommodation, flights, and documents instead of placing the entire exploration in one transcript. Its prototype limits the tree to depth two, illustrating a deliberate balance between structure and interface complexity. [5]

**The user evidence favors steerability**. In a counterbalanced, within-subject study conducted on 6–10 November 2023, eight participants compared ExploreLLM with ChatGPT on travel planning. Participants found the structured breakdown useful for organizing their thoughts and steering personalization; all but one described the chat-only responses as verbose and generic. The mechanism is visible task organization and persistent preference entry, not evidence of a newly trained personalized language model. [5]

**Workflow integration can save user time**. AutoGen’s OptiGuide comparison involved an expert Python/Gurobi user answering ten supply-chain questions. Both systems answered eight correctly, but ChatGPT plus Code Interpreter required an average 4 minutes 35 seconds per question, compared with approximately 1.5 minutes for OptiGuide. The calculated ratio is 275/90 ≈ 3.1, consistent with the report’s approximately threefold time advantage. [2]

**The saving comes from orchestration**. OptiGuide handles code writing, safety screening, execution with relevant dependencies, and result interpretation inside one workflow. In the comparison, the user otherwise had to move code and results between interfaces. Separately, the report measures roughly 3–5-fold fewer user prompts across 2,000 questions in five applications, and reduces its core workflow implementation from more than 430 lines to 100 lines. These are interaction and engineering outcomes, distinct from model accuracy. [2]

**Human involvement becomes configurable**. AutoGen’s UserProxyAgent supports different frequencies and conditions for requesting input, including allowing users to skip a response. Its mathematical examples show how human hints can enter an otherwise automated solving process. This turns human assistance into an explicit escalation path instead of requiring a person to monitor every intermediate message. [2]

**Editable components support local correction**. The September 2025 Componentization preprint decomposes responses into linked semantic units that users can edit, exclude, or regenerate independently. Its MAOD workflow parses, segments, classifies, links, validates, and exports those units. This is particularly useful when a user wants to revise one section of a report or one part of a plan while retaining the rest. [20]

**More control can create more burden**. Componentization’s four-participant prototype study found value in selective rewriting and removal, but also Edit/Regenerate confusion, four-column cognitive load, formatting loss, and failures on a complex code-conversion task. Belosevic’s November 2025 HCI/NLP survey similarly warns that confidence displays and multi-step plan inspection can transfer verification responsibility to users who lack the necessary expertise. [20][31]

**Confirmation gates protect user authority**. The June 2024 LLM-component taxonomy describes AutoDroid repeatedly observing updated Android GUI state and requesting confirmation before irrevocable operations such as permanent deletion or calling a contact. The important design choice is not simply exposing the plan: authorization is required at the point where the system would change external state in a consequential way. [9]

**Physical interaction makes timing explicit**. The December 2025 robot-LAM prototype exposes a human-readable plan and accepts corrections such as “Swap the action order” before execution. Its speech evaluation reports mean recognition accuracy of 0.9791 across 30 task-related commands and three participants, while its emergency-stop voice path has a reported average latency of 1.41 ± 0.14 seconds. These measurements describe particular interface components; plan correctness, speech recognition, and physical safety remain different properties. [16]

**Personalization requires governed memory**. Storing preferences can improve continuity, but retained information must remain distinguishable from temporary instructions and changing circumstances. The engineering implication is to make preferences inspectable, editable, and scoped to the relevant user and task. A stale remembered preference should not silently overrule a user’s current explicit request.

**The user-centric judgment favors selective visibility**: show users meaningful plans, preferences, results, and consequential choices, while keeping routine coordination out of their way; more agents or more interface panels are not user benefits by themselves.

### How the four advantages depend on one another

**Shared interfaces create multiple benefits**. A well-defined tool contract can simultaneously improve task success, enable a new operation, reduce repeated interpretation, and support a clear approval interface. Similarly, an explicit intermediate state can make reasoning easier to verify, cheaper to resume, and simpler for a user to correct. The four advantage categories are different consequences of the same component boundaries.

**The bottleneck moves to coordination**. Once components are individually competent, selecting the right resource and passing the right information become central. Megagon’s 2024 enterprise compound-AI account reports a 46% average downstream accuracy drop associated with retriever-design choices in CMDBench experiments. The result illustrates how a weak information-selection stage can dominate the performance of an otherwise capable system. [32]

**Additional computation can explain apparent intelligence**. Anthropic’s 2025 research-system report attributes much of its browsing-evaluation variation to token use, tool calls, and model choice. Its internal multi-agent system, led by Claude Opus 4 with Claude Sonnet 4 subagents, reportedly outperformed single-agent Claude Opus 4 by 90.2% on its internal research evaluation. This supports the value of parallel context and broader exploration, while leaving agent organization and increased execution budget intertwined. [28]

**The system-level judgment is selective composition**: the strongest Big Loop designs allocate the right component and amount of effort to each bottleneck, while preserving a simpler execution path for tasks that do not benefit from additional coordination.

## 3. Construction Methods for Tool Components and Model Components

### Tool Components: comparing the three construction routes

**The routes differ in authorship**. Direct reuse preserves an existing utility’s underlying implementation; manual construction engineers the tool interface or task-specific behavior; LLM-based construction generates descriptions, wrappers, programs, or reusable implementations. A practical system can combine all three. For example, an LLM-generated program may call manually wrapped services whose underlying implementations were built by humans.

| Route | Starting material and output | Construction workflow | Strength and trade-off | Named examples |
|---|---|---|---|---|
| Direct reuse | Existing API/library → registered callable | Expose schema, invoke, normalize response | Reuses mature behavior; inherits dependencies | ReAct; ToolBench; m&m’s |
| Manual construction | Requirements/documentation → engineered tool or workflow | Implement rules, schemas, gates, tests | Precise control; developer effort | AutoGen; production rules; ToolSandbox |
| LLM-based construction | Examples/docs/code → generated tool artifacts | Generate, execute, test, repair, register | Scalable synthesis; validation burden | LATM; AutoTools; ToolFactory; TOOLMAKER |

**The reusable artifact matters**. A generated tool description, an API-call training example, and a new executable function are different deliverables. Wölflein and colleagues’ ACL paper, published in July 2025, explicitly distinguishes tool creation from tool learning: creation produces tools, while learning improves the use of human-crafted tools. This distinction is essential when evaluating claims of automatic construction. [33]

### Tool Components: directly using existing human tools

**Reuse begins with an existing capability**. Suitable starting points include search engines, calculators, databases, software libraries, code interpreters, REST services, and robot interfaces. The construction task is to expose the capability in a form the controller can call reliably. The LLM does not need to implement the search engine or numerical routine.

**Documentation becomes a machine-facing contract**. ToolLLM’s 2023 public version records API names, descriptions, HTTP methods, required and optional parameters, request bodies, executable call snippets, and example responses. These fields give the model enough information to distinguish tools and produce valid calls. They also give the surrounding program a basis for validation and execution. [26]

**A direct-use workflow is concrete**:

1. Select an existing operation whose semantics fit the task.
2. Expose its name, purpose, arguments, types, and response format.
3. Connect the interface to the actual executable service or library.
4. Validate arguments and distinguish successful results from errors.
5. Return observations to the controller and check the relevant task outcome.

**ReAct demonstrates minimal integration**. Its Wikipedia API is supplied externally; the innovation lies in the reasoning–action–observation protocol around that interface. The same general pattern supports a calculator or database query: the model proposes the call, an external executor performs it, and the result becomes evidence for the next step. [7]

**Multimodal reuse crosses model boundaries**. In m&m’s, the 13 machine-learning models, 11 image-processing modules, and 9 APIs are all presented as executable tools. From the orchestration perspective, the important properties are their accepted inputs, returned artifacts, and compatibility with other operations. This is why a Model Component can simultaneously appear as a Tool Component at an application interface. [25]

**Robotics shows mature infrastructure reuse**. The December 2025 robot-LAM system builds on ROS2 services and actions, MoveIt2 motion planning, and pretrained perception components. Its high-level agent delegates kinematic and collision-avoidance work to established lower-level software. Reusing those capabilities avoids asking a general-purpose language model to reproduce low-level control algorithms in generated text. [16]

**Reuse transfers existing dependencies**. API changes, authentication failures, service outages, response variability, and execution side effects remain part of the system. Direct integration is therefore strongest when the existing utility already solves the hard operational problem and its interface can be constrained clearly. “Direct” means preserving the underlying capability, not eliminating interface engineering.

### Tool Components: manual construction and interface engineering

**Manual construction adds deliberate semantics**. Developers can create a new utility, write a wrapper around an existing one, or encode a workflow with explicit preconditions and control rules. This route differs from simple reuse because the developer determines additional behavior: argument normalization, permitted operations, sequencing, failure handling, and approval requirements.

**Tool design shapes model behavior**. Anthropic’s December 2024 guidance treats tool descriptions and schemas as an agent–computer interface. It recommends clear boundaries, examples, edge cases, input requirements, and repeated testing. Its SWE-bench example changed file tools to require absolute paths after relative-path mistakes appeared when the agent changed directories. The lesson is that reducing interface ambiguity can be more effective than repeatedly telling the model to be careful. [8]

**Rules express domain constraints directly**. CoALA describes production systems in which each rule specifies a precondition and an action. A matching precondition permits the corresponding operation. Such rules can encode stable domain requirements explicitly, but require substantial manual knowledge engineering and work best where the relevant conditions can be represented reliably. [6]

**Manual orchestration separates responsibilities**. In AutoGen, a developer defines agent roles, registers reply functions, configures execution, and specifies termination or human-input conditions. OptiGuide’s Commander, Writer, and Safeguard embody different duties: coordination, code production and interpretation, and safety screening. The resulting tool-using behavior is partly model-generated, but the workflow’s responsibilities and checks are human-engineered. [2]

**Fixed roles suit stable processes**. MetaGPT and ChatDev use specialized software-development roles such as coder and reviewer, as described in the May 2025 MASLab public preprint. This can make handoffs predictable when the task resembles a known development process. It can also constrain generalization when an unfamiliar task does not fit the predefined roles or execution order. [34]

**Tests should express outcomes and prohibitions**. ToolSandbox provides a useful manual evaluation example: two domain experts constructed 1,032 scenarios with milestones and minefields. Milestones represent required progress with temporal dependencies, while a minefield identifies a prohibited event that makes a trajectory score zero. This tests whether tools were used appropriately, rather than whether the generated calls merely matched a valid schema. [27]

**Manual construction is strongest for invariants**. Stable safety requirements, permission checks, unit conventions, and known business rules should not depend solely on a model remembering natural-language instructions. The developer can place these conditions in executable gates while leaving interpretation and flexible planning to the LLM. The price is maintenance effort as tools and domains evolve.

### Tool Components: LLM-based automatic construction

**Automatic construction spans several artifacts**. An LLM can generate tool-use examples, callable wrappers, multi-step programs, descriptions, tests, or new algorithms. These outputs require different validation. A well-written description does not establish that its advertised function exists, and code that compiles does not establish that it implements the intended behavior.

| System and public period | Generated artifact | Main construction signal | Execution or validation | Reuse pattern |
|---|---|---|---|---|
| Toolformer, 2023 | API-call annotations and tool-use policy | Few human demonstrations | Execute calls; prediction-loss filtering | Learned API invocation [23] |
| LATM, ICLR 2024 | Python utility function and usage examples | Task demonstrations | Execution and validation samples | Functional cache [30] |
| AutoTools, 2024 preprint | Callable wrappers and composed Python | Raw tool documentation | Compilation and integration tests | Verified function library [35] |
| ToolFactory, January 2025 preprint | AI-compatible API tools | Unstructured REST documentation | Error diagnosis; verified-tool knowledge | Registered API interfaces [36] |
| TOOLMAKER, ACL July 2025 | Repository-derived Python tool | Task, paper, code repository | Environment setup; execution; repair | Specialized computational tool [33] |

**A general automatic workflow is iterative**. The model interprets examples, documentation, or source code; proposes an artifact; executes it in a controlled environment; compares behavior with tests or expected outputs; and revises failed candidates. Accepted artifacts enter a registry or library with invocation examples. This is construction through feedback, not simply requesting code once.

**Toolformer automates learning to use tools**. Starting with a handful of human-written demonstrations, it samples candidate API calls in a language-modeling corpus, executes them, and filters calls according to whether their results improve prediction of subsequent tokens. Fine-tuning on the augmented corpus teaches when to call an API, which API to choose, and what arguments to supply. The underlying calculator, search service, and other APIs remain existing utilities. [23]

**Its composition scope is bounded**. Toolformer’s reported inference setup allows at most one API call per input. Its results therefore support learned invocation, while richer multi-step tool construction requires additional control and composition mechanisms. This distinction matters because automatic annotation can improve a model’s tool-use policy without producing a new executable capability. [23]

**LATM constructs reusable executable functions**. Cai and colleagues’ ICLR 2024 framework separates a powerful tool maker from a potentially cheaper tool user. The tool maker receives three demonstrations, generates a Python function, and uses three validation samples; tool proposing and verification each permit up to three retries. The accepted function is packaged with examples showing how natural-language requests map to function arguments. [30]

**The validation details are important**. During proposing, execution errors can trigger another function-generation attempt. During the paper’s verification stage, corrections target function calls in unit tests rather than the function body itself. Consequently, passing the small validation set is a useful filter, not proof of correctness across all future inputs. The paper identifies over-specialization to demonstrations as a failure mode for weaker tool makers.

**LATM’s results show the mechanism clearly**. With GPT-4 creating tools and GPT-3.5 Turbo using them, the study evaluates six tasks with 240 test instances each, following three training and three validation instances. The first four baseline tasks use chain-of-thought demonstrations; the final two use direct few-shot prompting without chain-of-thought. [30]

| Task | GPT-3.5 Turbo baseline accuracy | GPT-3.5 Turbo with LATM | Calculated gain |
|---|---:|---:|---:|
| Logical Deduction, five objects | 66.4% | 79.7% | 13.3 percentage points |
| Tracking Shuffled Objects, five objects | 61.6% | 99.6% | 38.0 percentage points |
| Dyck Language | 20.4% | 92.2% | 71.8 percentage points |
| Word Sorting | 59.2% | 98.3% | 39.1 percentage points |
| Chinese Remainder Theorem | 0.0% | 100.0% | 100.0 percentage points |
| Scheduling Meeting | 18.9% | 100.0% | 81.1 percentage points |

**The tool converts reasoning into execution**. For logical deduction, the generated function searches permutations and checks constraints; for shuffled objects, it simulates swaps; for meeting scheduling, it computes interval intersections. The language model still has to translate the request correctly, but the repeated algorithmic work moves into executable code. This explains why a weaker tool user can perform strongly without acquiring the entire algorithm through additional model training.

**Amortization determines the economic payoff**. LATM characterizes serving cost as \(O(nc+C)\), compared with \(O(nC)\) when a stronger model handles every request, where \(C\) and \(c\) represent stronger- and weaker-model call costs. More generally, if construction costs \(C_{\mathrm{build}}\), each reused execution costs \(c_{\mathrm{use}}\), and direct large-model execution costs \(c_{\mathrm{large}}\), reuse is cheaper when:

\[
n>\frac{C_{\mathrm{build}}}{c_{\mathrm{large}}-c_{\mathrm{use}}},\qquad c_{\mathrm{large}}>c_{\mathrm{use}}.
\]

**The denominator carries the assumption**. Here, \(c_{\mathrm{use}}\) must include dispatch, argument generation, execution, and routine checking, while construction includes testing and repair. This analytical threshold explains why automatic tool making fits repeated task families better than one-off questions. LATM’s historical statement that a GPT-4 call cost over 15 times a GPT-3.5 Turbo call belongs to its original pricing period, not a general contemporary price relationship. [30]

**AutoTools addresses documented tool ecosystems**. Its 2024 public preprint separates Tool Encapsulation from Tool Programming. Encapsulation turns documentation into callable functions, checks syntax through compilation, and checks runtime behavior and input–output dependencies through generated integration tests. Programming then generates Python that chains accepted functions, parses intermediate results, and reuses variables. [35]

**Multi-step testing exposes different failures**. AutoTools-Eval contains 224 tasks spanning 107 tools, with each task requiring at least five tool calls. This setting tests dependencies that a single-call benchmark can miss. Incorrect argument names, incompatible intermediate outputs, and runtime failures remain central construction problems even when generated code is syntactically valid. [35]

**ToolFactory targets documentation conversion**. Submitted on 28 January 2025, its public preprint converts unstructured REST documentation into AI-compatible tools, diagnoses generation errors, and uses a knowledge base of verified tools to help interpret missing information. Its API Extraction Benchmark contains 167 documents and 744 endpoints. Those figures describe benchmark coverage, rather than a claim that every endpoint was converted correctly. [36]

**TOOLMAKER builds from scientific repositories**. The ACL July 2025 system receives a task description, a scientific paper, a GitHub repository, and example-valued arguments. It installs dependencies, creates a Docker environment, explores the repository, emits a Python function, and uses execution–diagnosis–repair cycles. On TM-BENCH, it correctly implements 80% of 15 tasks—12 tasks by calculation—with more than 100 unit tests. [33]

**Description generation is a separate case**. TOOLVERIFIER’s November 2024 paper begins with eight manually annotated seed tools, uses an LLM to expand a library to 173 tool descriptions, and creates 555 selection samples, including 75 hard examples. This is valuable automatic training-data construction, but the descriptions are used for selection learning and need not contain executable implementations. [10]

**The tool-construction judgment favors layered automation**: reuse established implementations when possible, manually encode stable constraints, and automate wrappers or new functions where execution tests can supply informative feedback; generated artifacts should earn registration through behavior, not persuasive descriptions.

### Model Components: task paradigms and construction objectives

**Task and architecture answer different questions**. A task paradigm specifies what a component predicts and how it receives supervision. Architecture specifies how that prediction is computed and how the component connects to other components. An embedding model and a reward model may share a Transformer backbone while exposing entirely different interfaces.

| Model paradigm | Input → output | Training or adaptation | Inference role | Example |
|---|---|---|---|---|
| Policy or generation model | State/prompt → text, step, action | Supervised traces; preference/RL adaptation | Propose a next operation | ToolLLaMA; RLM policy |
| Embedding model | Sequence → fixed-length vector | Prompting; contrastive or supervised tuning | Retrieve or match information | Sentence-BERT; Instructor; LLM2Vec |
| Outcome reward model | Prompt and response → quality score | Preferences or outcome labels | Rank complete candidates | RLHF reward models |
| Process reward model | Problem and reasoning prefix → step score | Step labels; automated process supervision | Detect errors and guide search | PRM800K-based models |
| Value model | State/action → expected-quality estimate | Search or outcome-derived targets | Allocate exploration | RLM MCTS value model |
| Perception model | Sensory input → labels, geometry, representation | Reuse or adapt pretrained models | Ground reasoning in observations | SAM; CLIP; GraspNet |

**Construction can start from existing models**. A component need not be trained from scratch. It may use a pretrained checkpoint with a new prompt, a task-specific output head, parameter-efficient adaptation, supervised fine-tuning, or reinforcement learning. The relevant question is whether its training and interface support the role it will play in the system. The 2025 RLM blueprint explicitly separates reasoning schemes, operators, associated models, and pipelines for this reason. [11]

### Model Components: embedding models

**Embedding models make similarity computable**. They map a sequence into a fixed-length vector that supports retrieval, clustering, matching, or recommendation. The public survey *LLMs are Also Effective Embedding Models*, first released in December 2024, describes extracting sequence representations through special-token selection, mean pooling, or attention-based aggregation of token hidden states. [37]

**Pooling defines the output interface**. In compact notation, an embedding is \(e(x)=\operatorname{Pool}(h_1,\ldots,h_m)\), where the \(h_i\) are token representations. An EOS representation is inexpensive to extract, mean pooling combines tokens uniformly, and attention pooling learns or applies nonuniform aggregation. The choice matters because a generative model’s token states were not necessarily trained to produce useful sequence-level distances.

**Retrieval requires compatible query and document spaces**. A standard dense-retrieval pipeline chunks documents, embeds and indexes them, embeds the query, retrieves the highest-scoring candidates, and supplies selected evidence to a generator. Cosine similarity is commonly used:

\[
s(q,d)=\frac{e(q)^{\top}e(d)}{\|e(q)\|\,\|e(d)\|}.
\]

**The model is only one stage**. Chunking, index behavior, access filtering, candidate count, and reranking affect which evidence reaches the generator. The June 2025 CAIS public version distinguishes sparse, dense, graph, hybrid, and LLM-as-retriever approaches. Dense embeddings support semantic matching, while sparse methods preserve explicit term matching; hybrid systems combine those strengths. [13]

**Tuning-free construction uses prompted extraction**. Methods such as PromptEOL adapt the input format to encourage useful sequence representations without updating model parameters. This reduces training requirements and offers a quick component-construction route. Its suitability depends on whether the resulting similarity geometry matches the downstream task. [37]

**Contrastive training shapes that geometry**. Positive query–document or instruction–tool pairs are pulled closer, while negative pairs are separated. ToolLLM uses a Sentence-BERT retriever based on BERT-BASE with contrastive learning to rank API documentation for an instruction. Its reported aggregate NDCG@1 and NDCG@5 scores are 78.0 and 84.9, compared with BM25’s 18.5 and 17.0 and text-embedding-ada-002’s 49.6 and 45.4 in that evaluation. [26]

| Tool-document retriever | NDCG@1 | NDCG@5 |
|---|---:|---:|
| BM25 | 18.5 | 17.0 |
| text-embedding-ada-002 | 49.6 | 45.4 |
| ToolLLM contrastive retriever | 78.0 | 84.9 |

**Ranking quality is an intermediate property**. NDCG measures the quality of the retrieved ordering, not whether the complete agent solves the user’s task. A retriever can select relevant documentation while the controller still supplies incorrect parameters. This is why component evaluation should connect retrieval relevance to downstream execution outcomes.

**Instruction tuning supports multiple embedding tasks**. Instructor uses instructions spanning 330 tasks to train a multitask contrastive model, according to the December 2024 embedding survey. The instruction tells the encoder what kind of relationship should matter—for example, relevance for retrieval rather than generic semantic resemblance. This makes the embedding interface conditional on task intent. [37]

**Reasoning can precede vector construction**. The public 2025 Large Reasoning Embedding Models study proposes reasoning-then-embedding for difficult e-commerce queries. It generates a reasoning augmentation, combines it with the original query, and embeds the result. Its example “Drinks That Are More Invigorating Than Tea” illustrates the intended mechanism: identify the comparative intent rather than retrieving items merely because they mention tea. [38]

**The LREM recipe combines objectives**. The study constructs approximately 75.06 million Query–CoT–Item triples, first trains with supervised fine-tuning plus InfoNCE, and then applies GRPO while retaining the contrastive objective. To control online sequential-generation overhead, it uses compact keyword-style reasoning limited to 16 tokens and samples eight reasoning candidates per query during the GRPO stage. This is a concrete example of co-designing a component’s supervision and serving behavior. [38]

**Embedding construction should target relevance**. The preferred component is not automatically the largest encoder. It is the model whose task-conditioned representations, training pairs, and retrieval interface select evidence or tools useful to the downstream workflow. Extra reasoning is justified when intent interpretation is the bottleneck and its retrieval benefit warrants the added inference.

### Model Components: reward models, process models, and value models

**Reward components make evaluation learnable**. An outcome reward model scores a completed response; a process reward model evaluates intermediate reasoning steps; a value model estimates the promise of a state or action. Wu’s peer-reviewed November 2025 Findings of EMNLP survey organizes reward learning across training, inference, and post-inference, emphasizing that feedback can update a policy or refine its outputs. [39]

**Preference pairs support explicit reward training**. A common dataset contains a prompt and a chosen/rejected response pair. A model is trained to assign the preferred response a higher score. A standard pairwise logistic objective can be written as:

\[
\mathcal{L}_{\mathrm{pref}}=-\log \sigma\!\left(r_{\theta}(x,y^{+})-r_{\theta}(x,y^{-})\right).
\]

**The labels define the target**. Here, \(x\) is the prompt, \(y^{+}\) the preferred response, \(y^{-}\) the rejected response, and \(r_{\theta}\) the learned score. Human preference may reflect helpfulness, style, safety, or correctness, depending on the annotation instructions. Lin and colleagues’ AAAI 2025 work analyzes preference-pair filtering using reward differences, illustrating that data selection can materially affect reward-model calibration and alignment. [40]

**RLHF and DPO use preferences differently**. A conventional RLHF pipeline trains an explicit reward model and then optimizes a policy against its scores. Direct Preference Optimization instead updates the policy directly from preference pairs without requiring a separately deployed reward model. Both belong in a review of reward-based construction, but DPO should not be described as automatically constructing a standalone reward-network component. [41]

**Process supervision changes annotation granularity**. Lightman and colleagues’ 2023 public paper *Let’s Verify Step by Step* constructs PRM800K using human judgments on generated mathematical solution steps. The dataset contains 800,000 step-level labels across 75,000 solutions to 12,000 problems, with positive, negative, and neutral step labels. This creates direct supervision for local reasoning evaluation rather than only final-answer scoring. [42]

**Local feedback can identify the first mistake**. A final incorrect answer says that some part of the solution failed; a process label can identify where the trajectory first becomes unsound. The study reports 78% success on a representative MATH test subset for its process-supervised approach and a 2.6-fold improvement in process-supervision data efficiency through active learning. The data-efficiency result concerns annotation use, not a 2.6-fold inference-speed improvement. [42]

**Automatic feedback offers several alternatives**. RLAIF uses AI-generated feedback; self-rewarding systems generate judgments within an iterative learning procedure; LLM-as-a-judge systems produce prompted evaluations; and formal rules or tools provide task-specific signals. A correct numerical answer, passing test suite, or accepted symbolic proof can supply an objective check in its respective domain. These signals can train a reward model, train a policy directly, or guide inference without parameter updates. [41]

**Search can generate process data**. The October 2025 public analytical reward-model survey describes OmegaPRM using an MCTS tree and binary search to locate the first error, while Tree-PLV constructs reasoning trees for preference collection. These approaches reduce reliance on exhaustive human step annotation. Their targets nevertheless depend on the quality of final-answer checks, sampled continuations, and the definition of a reasoning step. [43]

**GRPO is an optimization method**. It uses relative rewards within a group of sampled outputs to update a policy. It does not, by itself, specify a trained reward model: the reward may come from a neural evaluator, a correctness rule, a formatting check, or a combination. Separating the reward source from the policy optimizer prevents a taxonomy from confusing a learning algorithm with an evaluative component. [41]

**Inference use differs from training use**. A reward model can rank complete candidates, score branches during search, guide decoding, or decide which response warrants revision. These uses allocate inference computation without necessarily changing the generator’s weights. A model that is adequate for choosing between final answers may still be unsuitable for pruning intermediate steps, because the two decisions require different judgments.

**Heuristic scores remain separate objects**. The SAS/MAS study’s critical-agent analysis combines self-reported confidence on a 1–10 scale with a binary final-quality signal. That is a hand-designed credit-assignment procedure, not equivalent to training a reward network. Likewise, ToolEval’s documented role is a prompted ChatGPT evaluator producing pass and win comparisons; its interface should not be mistaken for a dedicated reward-model training recipe. [4][3]

**Reward quality must be evaluated independently**. A generator can exploit a reward model’s weaknesses, and a preference dataset may contain genuine disagreement rather than a single indisputable target. RewardBench, published in Findings of NAACL in April–May 2025, discusses 60–70% accuracy ceilings associated with annotator disagreement in particular Helpful and Harmless and summarization validation datasets. That is a property of those evaluation settings, not a universal ceiling for reward modeling. [44]

**The reward-construction judgment is task-specific**: choose outcome, process, or value supervision according to the decision the component must support, and distinguish learned preferences from formal correctness, prompted judgments, and heuristic confidence.

### Model Components: architectural innovations

**Architectural innovation operates at two levels**. Inside a model, it can change attention, pooling, output heads, parameter sharing, or computation depth. Around models, it can change the composition of policies, evaluators, selectors, and executors. Both affect construction, but a new orchestration graph is not automatically a new neural-network backbone.

| Architectural change | Mechanism | Constructed capability | Named design | Main trade-off |
|---|---|---|---|---|
| Bidirectional attention | Tokens use both preceding and following context | Sequence representations | LLM2Vec; Gecko | Compatibility with generative pretraining |
| Learned pooling | Aggregate token states through attention | Fixed-length embeddings | NV-Embed | Additional representation machinery |
| Scalar or generative critics | Score directly or generate evaluation text | Reward and verification | Explicit RMs; GenPRM | Speed versus expressive evaluation |
| Shared-weight recurrence | Reapply blocks with adaptive exit | Variable-depth latent computation | LoopLM/Ouro | Smaller weights, repeated computation |
| Policy–value–operator composition | Separate proposal, search, and evaluation | Structured reasoning | RLM blueprint | Search and verifier overhead |
| Selection–verification separation | Check tool choice before downstream use | More reliable tool invocation | TOOLVERIFIER | Additional evaluation stages |

**Embedding architecture changes information access**. The December 2024 embedding survey describes adding bidirectional attention in LLM2Vec and Gecko, combining embedding and generation in GritLM, parameter-efficient adaptation through LoRA, and latent-attention pooling in NV-Embed. The common goal is to make sequence representations more useful than a direct extraction from an unchanged causal generator. The survey also reports that bidirectional embedding fine-tuning can conflict with generative pretraining, so a stronger retriever need not remain an equally good generator. [37]

**Reward heads define different deployment costs**. Explicit discriminative reward models commonly replace the token-prediction head with a scalar linear head. Generative critics instead produce natural-language evaluation before a score, allowing richer criteria and sometimes tool-assisted checking. The October 2025 reward-model survey describes GenPRM’s code-verification integration and notes that generative critics are more expensive to deploy and harder to train than discriminative models. [43]

**Criteria can become part of evaluation**. CARMO, published in Findings of ACL in July 2025, generates criteria tailored to the query—such as logical consistency, clarity, and depth—before scoring responses. The paper also describes distillation into smaller models. This separates deciding what quality means for a request from assigning the resulting score, creating another reusable evaluative interface. [45]

**LoopLM shares parameters across depth**. Its recurrent computation repeatedly applies a shared Transformer block or stack, rather than adding new independent weights at every depth:

\[
H^{(t+1)}=B_{\theta}\!\left(H^{(t)}\right),\qquad y=\operatorname{LMHead}\!\left(H^{(t_{\mathrm{exit}})}\right).
\]

**Adaptive exit allocates internal effort**. The October 2025 public LoopLM paper trains depth allocation through an entropy-regularized objective and a subsequent gate-focused training stage. Easy inputs can exit after fewer recurrent passes, while difficult inputs receive more computation. Its Ouro models, trained on a reported 7.7 trillion tokens, have 1.4 billion and 2.6 billion parameters and are reported as broadly comparable to standard models of approximately 4 billion and 8 billion parameters. [22]

**Parameter sharing does not remove computation**. Every additional recurrence still performs neural operations, and the paper finds that benchmark performance can deteriorate beyond the recurrent depth used in training. Early exit therefore matters both for cost and for avoiding unhelpful additional processing. This is an internal architectural option for a Model Component, independently of whether that component participates in an external Big Loop.

**Reasoning architectures separate search responsibilities**. The January 2025 RLM blueprint constructs systems from a reasoning scheme, operators, associated models, and pipelines. A policy proposes steps; a value model assesses promising state–action choices; search operators expand, select, or backtrack through chains, trees, or graphs. Its example value model adds three linear layers and a shifted, rescaled sigmoid to produce scores in the range \([-1,1]\). [11]

**Training and inference can share structure**. The blueprint distinguishes an inference pipeline serving users, a training pipeline updating policy and value models, and a data-generation pipeline that produces further training examples. Successful or informative search trajectories can therefore support later model adaptation. The external execution loop and the model-update loop remain separate processes; persistent memory alone does not imply online weight training. [11]

**Tool verification localizes avoidable errors**. TOOLVERIFIER separates tool selection from parameter generation and adds contrastive questions between competing candidates. Its November 2024 Findings of EMNLP paper reports a 22% average improvement over few-shot baselines on four ToolBench tasks involving 17 unseen tools, with self-verification contributing an author-reported 8% improvement. The architectural point is the explicit intermediate choice, which can be challenged before downstream execution propagates the error. [10]

**Neuro-symbolic architecture combines different guarantees**. The December 2025 robot-LAM prototype compares restricted direct tool calling with a PDDL route. In the latter, static robot actions and capabilities are hard-coded, the LLM constructs the task-specific symbolic problem, and Fast Downward solves it. In the former, the model selects a structured sequence from finite predefined APIs. [16]

| Robot planning method | Reported success rate | Mean time per step | LLM requests per step |
|---|---:|---:|---:|
| Restricted LLM-direct tools | 100.0% | 7.20 ± 0.25 seconds | 2.0 |
| Neuro-symbolic PDDL | 91.0% | 6.83 ± 0.27 seconds | 2.0 |

**Formal structure trades flexibility for strictness**. Across 13 tasks and 65 total trials, the direct route is more successful in the reported evaluation, while PDDL is slightly faster per step. The symbolic planner checks validity within the encoded domain, but imperfect problem translation can prevent planning. Its logical guarantees do not by themselves establish that perception is correct or that every real-world safety condition has been modeled. [16]

**Output structure is a separate innovation**. Componentization’s parse–segment–classify–link–validate–export workflow creates typed, linked response units for user manipulation. It does not require interpreting those units as neurons, independent models, or executable tools. Its contribution is making model output a structured interface that other software and users can operate on. [20]

### Choosing and composing the components

**Construction should follow the bottleneck**. The evidence supports choosing a component because it supplies a needed operation, representation, or quality signal—not because a larger component inventory is desirable. The following selector summarizes the practical choices.

| Construction choice | Best-fitting need | Main artifact | Acceptance check | Principal cost driver |
|---|---|---|---|---|
| Direct tool reuse | Existing capability already fits | Registered callable interface | Valid calls and observed outcomes | Integration and service use |
| Manual tool construction | Stable rules or consequential actions | Utility, schema, gates, workflow | Preconditions and prohibited outcomes | Expert engineering |
| LLM-generated tools | Repeated or novel computational tasks | Tested wrapper or function | Execution and held-out behavior | Construction, repair, maintenance |
| Embedding component | Evidence or tool selection | Encoder and retrieval index | Relevance and downstream success | Encoding, indexing, retrieval |
| Reward/value component | Candidate selection or search guidance | Evaluator and scoring interface | Calibration and task-aligned judgments | Labels and evaluation calls |
| Architectural adaptation | Parameter, latency, or interface bottleneck | Modified backbone or composition | Quality–resource comparison | Training and serving complexity |

**Composition determines practical value**. A strong embedding model helps only if the controller uses its retrieved evidence effectively. A reward model helps only if its scores distinguish useful alternatives. A generated tool helps only if the system selects it, translates inputs correctly, and checks its result. These dependencies make end-to-end behavior the final criterion, while component-level tests explain where failures originate.

**Evidence and measurement basis**. The definitions and six-category map are analytical syntheses, not a standardized Big Loop specification. Evidence is restricted to public material through 31 December 2025, including the architectural content of the June 2025 CAIS version; later additions are outside scope. Conference papers, preprints, prototype studies, and corporate engineering reports retain their stated status. Benchmark percentages, percentage-point differences, ranking scores, tokens, latency, cost, and parameter efficiency measure different quantities. Calculated differences and thresholds above are explicitly identified; results are not pooled into a universal uplift. User evidence includes small prototype samples, while corporate figures describe internal evaluations and production experience.

**The final construction judgment is selective modularity**: build explicit, testable components where they add complementary information, computation, evaluation, or user control, and give the surrounding loop the responsibility to invoke them economically, inspect their effects, and stop when further execution no longer improves the outcome.

**Additional documented evidence**

| Entity | Tool-construction method category | Tool validation, interface and integrat… | Generic tool-construction examples | Tool construction requirements and cont… | Tool and model evaluation methods | Construction-method tradeoffs | tool-construction method | tool-construction mechanism | tool-construction example | tool-construction requirements | tool-construction evaluation | construction tradeoff |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Human Tools | no evidence found | no evidence found | no evidence found | no evidence found | The direct-use method for Human Tools consists of… | no evidence found | no evidence found | no evidence found | React, Stride, ToolChain*, SoAy | no evidence found | The example directly uses bash, Python, a full…[234] | no evidence found |
| LLM-Based Automatic Tool Construction | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | Propose, verify, wrap Python function; function API[239] | Scheduling, routing, Sudoku, web parsing[239] | Unit tests; retry errors and fail after threshold[238] | no evidence found | One-time maker cost; cheaper reuse with small LLM[239] |

| Entity | Model-construction perspective | Task-paradigm construction mechanism | Embedding-model construction and role | Reward-model construction and role | Architectural-innovation taxonomy | Architectural-innovation construction m… | Architectural-innovation examples | Model-component evaluation and integrat… | Construction-method tradeoffs | model-construction perspective | task-paradigm mechanism | embedding-model role | reward-model role | architectural innovation | architectural mechanism | model-construction example | model-component evaluation | construction tradeoff |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Embedding Models | no evidence found | no evidence found | The page cites MTEB: Massive Text Embedding Benchmark…[272] | 70%[261] | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | The page cites MTEB: Massive Text Embedding Benchmark…[272] | The page cites MTEB: Massive Text Embedding Benchmark…[272] | Text embedding models compress long text sequences…[259] | no evidence found | Remove causal mask; latent-attention pooling…[222] | GTE, LLM2Vec, NV-Embed, Qwen3 Embedding[267] | no evidence found | no evidence found |
| Reward Models | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Architectural Innovations | no evidence found | Joint embeddings, cross-attention, latent scenes[104] | Cross-modal grounding via joint embeddings[104] | no evidence found | no evidence found | Learned gating selects recurrent exit depth[226] | Unlocking emergent modularity in standard pre-trained…[284] | no evidence found | Search cost and diversity collapse[283][285] | Architecture via singular, composite, graph loops[213] | Joint embeddings, cross-attention, latent scenes[104] | Cross-modal grounding via joint embeddings[104] | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |

Tool Components: index name/description/schema, opt. 1–10 Qs/topics, metadata; rewrite/decomp./expand queries, retrieve/rerank top-k, map meta→Python, attach agent, hash updates. Toolshed/Advanced RAG-Tool Fusion: OpenAI/Anthropic function-calling, no tool-call fine-tuning; recall@1/5/10, score 50/25/25 name/key/value. Gains vary: BM25 46/56/47%, overall ~46%, DPR 41%, Re-Invoke 5/9%. Five fields ≠ category; no Model-Component lifecycle or permissions/sandbox/security/test/deployment checks reported [144].

Tool Components: 5-part docs; q-decomp→retrieve/rerank; map Python; update [144].

Tool Components: name/desc/schema/Q/topics→DB→rewrite/split→top-k/rerank→Py; Human Tools: OpenAI/Anthropic fn-call; manual/new-tool-gen absent; get_net_present_value; r@1/5/10, n/k/v=50/25/25 [144].

Tool Components: NPV/schema/RAG/Q+C[144]

Model LEGO (NeurIPS 2024) is a CNN-demonstrated architectural Model Component example: MDA selects a task, locates feature maps/parameters with hard thresholds α,β∈(0,1], and structure-prunes filters, kernels and biases. It combines task-aware components from isomorphic models using empty-kernel padding and parameter scaling, producing a unified model ready for inference without retraining [148]. A component is an independently usable, subtask-specific parameter set exposed through layer-wise decision routes; lifecycle: selection→location→linkage→extraction→assembly→accuracy testing [148]. Results were generally comparable or better, supporting explainability/debugging, compression and distillation, but many or unrelated components caused interference and higher FLOPs/parameters than FPGM/HRank in the reported comparison. Embedding/reward paradigms, Big-Loop routing, deployment, monitoring and revision are unreported [148].

Model Components (MDA) extract task-aware CNN parameters, link decision routes, and assemble isomorphic models via alignment padding and parameter scaling; inference needs no retraining, but irrelevant components can reduce accuracy [148].

Model components: MDA assembles CNN[148]

MDA: task parts assembled, 2024 [148]

CNN model LEGO: align+scale; ±acc [148].

Lifecycle: requirements→selection/gen→training/eval→deployment/monitor→revision [215]. Model Components are tested workflow modules; ModelGPT/GPT-NAS show construction; scheduling unspecified [215].

Model Components select/generate ML models/programs; lifecycle train→test→deploy→monitor→revise. Model zoos retrieve; ModelGPT/GL-Agent/GPT-NAS generate/search; stochasticity needs tests [215].

Model Components = modular elements: requirements → selection/generation → implementation/training → validation → deployment/integration → monitoring/revision [215]. Retrieval matches tasks to model cards (structure/params/FLOPs/speed/metrics; top-5 embedding shortlist). Generation is flexible/stochastic: Contextual Modular Generation unit-tests modules; ModelGPT’s Requirement Generator/Customizer uses LoRA hypernets [215]. Execution-based HPO is reliable/costly; prediction-based HPO faster/error-prone; AgentHPO splits Creator/Executor [215]. GPT-NAS/Guided Evolution combine LLM proposals/mutations, evolutionary search and training feedback; validate outputs. Examples: Attention, LoRA, LongRoPE, NAS, TabPFN (small-tabular classification “in a second”) [215]. Logs/tracing, tests+synthetic data, ensembles, human oversight mitigate halluc./bias/opacity; explanations mislead [215].

Model comps: select→test→feedback [215]

Model Components are modular units [215]

Model Components: retrieve/generate[215]


| Entity or route | Status in permitted evidence |
|---|---|
| **Tool Components** | Definition, Big Loop role, category boundary, interfaces, construction routes, controls, validation, examples, and trade-offs: unresolved. |
| **Human Tools** | Direct-reuse workflow, exposed interface, permissions, examples, validation, evaluation, and integration role: unresolved. |
| **Manual Tool Construction** | Human specification, implementation, testing, documentation, deployment, maintenance, examples, controls, evaluation, and trade-offs: unresolved. |
| **LLM-based Automatic Tool Construction** | Generation, refinement, packaging, validation, reuse, named tool-maker cases, interface requirements, performance or cost evidence, and trade-offs: unresolved. |


No eligible evidence can be reported here: the supplied cards trace to a globally prohibited source and cannot be cited, paraphrased, or used. Tool Components—definition, API interface, role, characteristics, validation, and scheduling—remain unresolved. Human Tools (direct reuse and examples), Manual Tool Construction (workflow and examples), LLM-based Automatic Tool Construction (generation, validation, LATM examples, and trade-offs), and the architectural-innovation example are likewise unsupported in this part.

Evidence gap: Human Tools, manual construction, LLM-based automatic construction, LATM, and examples remain unresolved: supplied cards fall under the global source exclusion; interfaces, validation, dates, and trade-offs are unavailable.

**Evidence status:** No eligible claim can be made here: the material supplied in this part for LLMs as Tool Makers, Toolformer, Embedding Models, and Reward Models comes from an excluded source. Their dates, mechanisms, interfaces, objectives, validation, examples, and Big Loop roles therefore remain unresolved; permitted primary-source evidence is required before citation or synthesis.

Model Components: ASR→LLM/PLM=transcribe→reason→classify/encode. Transformer/Conformer=self-attn/global-local; wav2vec2/Whisper=selfsup/weak; LoRA;GPT‑4o unifies ASR–LLM. HIL LLM73.7%/ASR21.1%;ext12/19;scale1/19;cascade/privacy/repro [221].

Source status: [221] was published in 2026; cutoff eligibility is unresolved, so its construction, architecture, evaluation, and deployment claims are not used.

Architectural innovations: Transformer/Conformer; Whisper+LLM+PLM adds clinical intelligence but may cascade; GPT‑4o unifies stages; eval. mixed [221].

Model Components—modules; API/text/logit/weight route/cascade/combine; Reward Models align; Architectural innovations: LoRA/FFN/MoE train-separately+combine; token/task routing; feedback/verify/debate; cost/latency/forgetting risk [146]

Model Components: retrieval/reward/routing, adapters/LoRA; separate→joint training; API/text/logit/weight routing; eval/tax incomplete; cost/latency risks[146]

Model Components: API/text/logit/weight collaboration; FFN/adapters/LoRA sep→joint; rewards aid alignment; routing↓cost/latency,cascading↑; evidence-gap. [146]

Model components: specialized modules; route/retrieve; LoRA/MoE; I/O; eval/risk [146]


Source [147] is post-cutoff; excluded.


40-char cap; [147] post-cutoff—excluded

Model Components: [147] post-cutoff.

Post-cutoff evidence excluded [147].

Capacity conflict: [147] date unresolved

MoE routes tokens to experts [149].

MoE: router selects sparse experts [149]

MoE model components route experts [149]

MoE sparse routing; metrics/safety [149]

OLMoE: 1B active/7B total; top-2 [149]

Model Components: top-2;8E;7B/1B [149]

Human Tools: Inspect's Linux-sandbox exposes shell/bash/Python, desktop, and stateful bash_session/web_browser/text_editor; approval gates calls/actions [234].

Manual construction (e012): collect→clean/dedupe/std→review↔feedback→maintain; annotators follow requirements [212]. Examples (datasets): Dolly/OASST/OL-CC/Aya/InstWild/LCCC/Zhihu; tool I/O/deployment unknown [212]. Quality/control↑; time/bias/inconsistency. Model gen faster/cheaper but hallucination/post-processing risk. Eval: pipelines or costly humans; accuracy/F1/BLEU/ROUGE; years only [212].

Manual construction: collect/filter/deduplicate/standardize/review/maintain data; it offers precision, quality and control but costs labor and risks bias. Databricks-dolly-15K, Aya, C4 and RefinedWeb are datasets, not tools; interface/deployment evidence is absent. Validation uses code/model pipelines or human review (accuracy, F1, BLEU/ROUGE); human review is costly; LLM generation saves time but needs cleanup [212].

Manual Tool Construction: human-led requirements→creation→filtering/deduplication→standardization→review/maintenance [212]. Firefly:23 tasks/templates; LIMA:1,330 instructions; 38 hybrids (Feb 2024) [212]. Higher quality/control, but costly/subjective; dataset evidence, not tools [212].

Manual: benchmark evidence; no tool[235]

Manual construction=benchmark-only [235]

Manual Tool Construction—no eligible pre-2026 workflow or example is established: the sole source was published 21 May 2026, after the cutoff, so its workflow, QA, embedding/RAG, hallucination, trade-off and evaluation claims are excluded, including 48.58% less time, 46.44% lower cost, +1.96% F1, and 255-case accuracy 0.818 vs GPT-4/RAG 0.790/0.807 [228].

Manual Tool Construction: no eligible pre-2026 Tool-Component example is established; the source card is dated 21 May 2026 and excluded by the cutoff [228]. Its inadmissible context covers expert schema/rule design, entity–relation refinement, consistency/LLM validation, RAG and MoE; it reports 2,058 documents, 4,783 nodes, 9,486 relations, 400 checks and 27 errors, not a tool workflow [228].

RAG failure, manual Tool Construction, embedding integration, model-component examples, and validation/trade-off claims: unresolved. Source [228] is dated 21 May 2026 and excluded by the 2025-12-31 cutoff; no eligible pre-2026 evidence appears in this part.

Manual Tool Construction: all claims excluded; [228] post-cutoff (21 May 2026).

Manual construction: physical only [236]

Manual construction (robotics), QC [236]

Manual iSMART: H/R; 840 logs, ±1mm [237]

Manual/HRI: glue/nail; robot marks [237]

Manual construction: HRI, not LLM [237].

Manual construction: HRI; <1mm [237]

LATM makes reusable Python Tool Components: a powerful LLM proposes, retries, unit-tests and wraps callable code; a lightweight LLM uses it; a dispatcher caches it [238]. LATM used 3 demos/3 validation samples; a failure threshold aborted tool-making [238]. Tasks: Logical Deduction (permutation search), Shuffled Objects, Dyck, Word Sorting, Chinese Remainder, Schedule Meeting, Search Simulation, Stack Sort, Euclidean, and interval intersections [238]. LATM contrasts with Toolformer’s learned tool use [238]. GPT-4 made tools and GPT-3.5 Turbo used them, matching GPT-4 more cheaply: O(nc+C) vs O(nC); GPT-4 calls cost >15× GPT-3.5 calls [238]. Only 2/60 corrected errors; validation challenging; safety/control under-addressed; performance task-dependent [238].

LATM: GPT-4→Python tools; GPT-3.5→use/cache; propose/verify/wrap; meeting; [238]

LLMs as Tool Makers: GPT‑4 generates Python tools, retries/tests/wraps them for a light model; caching reuses them for deduction, shuffled objects, Dyck, sorting, CRT and scheduling [238]. LATM matched GPT‑4 at lower cost; 2/60 corrections; real-world validation/safety remains open [238]. Toolformer: tool use [238].

LATM: LLM makes tools from 3 demos, runs 3 tests, wraps them; a cheaper model reuses them for meeting scheduling [238]

LATM exemplifies automatic tool construction: a powerful LLM generates a reusable Python function from demonstrations, proposes, unit-tests, and wraps it; a lightweight (or same) LLM invokes it. A dispatcher sends cache misses to the maker and reuses cached tools for analogous requests. GPT-4-made tools let GPT-3.5 Turbo match GPT-4 at lower inference cost on six tasks, including Scheduling Meeting [238]. LATM is early-stage; safety/validation remain open; Toolformer is only cited for learned tool use [238].

LATM: auto Python tools/cache [238]

LATM has GPT-4 generate Python tools, unit-test and wrap them, then reuse them via a lighter model; it reports GPT-4-level performance at lower cost, while validation and safety remain open [239].

LLMs as Tool Makers (LATM) [239]: propose→verify→wrap Python tools; light LLM reuses them. GPT‑4→GPT‑3.5≈GPT‑4, cost↓; 6 tasks (3/3/240); safety/validation open

LATM: GPT‑4→3.5 matched GPT‑4 performance at lower cost; Python tools from demos: test/wrap/reuse; safety unresolved [239].

LATM: Python tool, tests, wrapper [239]

LATM:G4→3.5;Py/test/wrap/cache≈perf[239]

LATM make/test/wrap; Toolformer? [240]

LATM: LLMs make, test, reuse tools [240]

LATM(2023):make→test→wrap→reuse[240]

LATM: makes, tests, wraps tools [240]

LATM auto-builds/tests/reuses tools [240].

LATM creates reusable Python tools [240]

LATM: reusable tools, tests, cache [240]

LLMs as Tool Makers: tested tools [240]

Toolformer(2023): few-shot/fine-tuning cited; details absent [241]. TOOLVERIFIER: select→parameterize→verify; primary EMNLP24 ToolBench: 4 tasks/17 tools, 89.52% [241].

Toolformer'23;ToolBench:4T/17 tools[241]

ToolBench: 17 tools; 4 REST tasks [241]

LLMs as Tool Makers (LATM), published 26 May 2023 (public date unreported): LLMs create reusable Python tools; the same or a different LLM uses them. GPT-4 maker/GPT-3.5 user matched GPT-4/GPT-4 on Big-Bench at lower inference cost [242].

LATM: GPT-4 makes reusable Python tools; GPT-3.5 uses them, matching GPT-4 with lower Big-Bench cost [242]. Toolformer unspecified. DaSLaM: 13B LoRA r16/alpha32/.05,last3layers; retrieval future [243].

Tool-Genesis: contracts→MCP schema/code→generate–execute–repair/sandbox tests; 86 servers/508 tools/2,150 tasks/9,441 tests. LATM’24: 6 tools/1 domain; schema✓, reuse/held-out/neg/GT✗; LATM/Toolformer’23 leads; ToolBench absent [244].

LATM 6t/1d sch✓ reuse/tests✗ mech?; TB only; Tool-Genesis MCP g/e/r [244]

LATM23?;Tool-Genesis:sig→exec→UT/U[244]

LATM builds/tests/fixes tools [218]

TOOLMAKER:80%(12/15);LLM→Docker→test[218]

LATM builds tools iteratively.[218]

LATM plans, codes, tests, repairs [218]

Toolformer: no method; exact args→obs→reuse [193]. RAG: GoogleLens→Wikipedia→LLM; HAMMR dispatches specialists; +16.3% vs naive LLM+tools, +5.0% vs PaLI-X [193]

HAMMR VQA avg: 24.0%→40.3%; dispatch→specialists; GoogleLens→Wikipedia→LLM [193]

TOOLMAKER: code/test/repair 12/15 [219]

TOOLMAKER builds and repairs tools [219]

LATM: plan, code, test, repair [219]

LATM makes tools 80%/15;oversight [219]

LATM23:GPT4→tool/GPT3.5→use;cost↓[245]

LATM: cached Python tools via APIs [246]

Toolformer 2023: learned tool-use; mechanism absent.[217] LATM 2024: tools as action space; APIs→executable programs.[217] AgentMD: PubMed→2,164 calculators; quality-check accuracy>85%, unit-tests>90%; selects/applies; risk accuracy 87.7% vs GPT-4 40.9% on 698 ED notes.[217] ToolBench: RapidAPI real APIs (16k/16,464); single/multi calls; RestBench multi-step paths.[217] Specialized tools improve reliability; agent communication and rare-task planning limit systems.[217] ToolChain/A* prunes paths; Tool-Planner clusters embeddings; MLLM-Tool aligns audio/image; LLaVA-Plus composes skills.[217]

Date unknown: LATM=ICLR-2024 listing only—no mechanism, Big Loop/Atomization definition, or requested taxonomy; Toolformer=2023 learned tool use [217]. Tools=virtual/real, uni/multimodal; metrics=completion, quality, selection, robustness/error. No-training=framework optimization or docs+few-shot retrieval. ToolLLM=domain→category→API; DFS/GPT-4 pruning. ToolChain*=A* task-cost: +3.1%/+3.5% (planning/reasoning), 7.35×/2.31× less time [217]. TPE=context/preferences→plan→execute; docs=functions/params/examples, but medical/robotic use may fail [217]. AgentMD curates/uses 2,164 calculators; >85% QC, >90% unit-pass; risk 87.7% vs 40.9%/698 ED notes [217]. IEEE fault-KG=zero-shot→RDF→iterative extraction; experiments claimed; cutoff unresolved (26–28 Dec 2025 conference; Xplore 25 Mar 2026); traditional route cumbersome/resource-heavy/error-prone [247].

Architectural Innovations differ from task paradigms: scaling may plateau, motivating new training/architectures; examples include multi-head latent attention in some DeepSeek models and reasoning models trained with inference-time scaling/RL/GRPO. They trade latency, cost, and quality; imperfect benchmarks require consistent evaluation [248]. Reward Models such as PRMs score explanations in RLVR via a second LLM, rerank top-N answers or guide search, but add RL overhead. RLVR uses deterministic correctness labels (mainly math/code), unlike SFT/RLHF written responses or preference labels [248].

RMs/PRMs score explanations; rerank/guide; cost. RAG/MoE/LoRA: eval hard [248]

Architecture spans neurons–models; MoE routes experts; PET/LoRA updates [249].

MoE routes experts; LoRA plugs in [249].

MoE top-k routing reduces FLOPs but adds overhead; LoRA/PET freezes the base and spans >100 NLP tasks; bricks support routing/retrieval/update/growth [249].

LoRA updates few parameters; routing may cut compute but adds overhead [249].

Model Components: pretrain→domain FT→human adapt; Transformer=attn+pos enc; MoE=gate specialists/few; LoRA=low-rank weights; RAG=DB retrieval at inference. T5/BART enc–dec (BART denoise), Falcon dec, T5-X scales; Mamba sel-SSM, faster/linear≤3B-param≈2×T [302; open 16-May-2025].

MoE∶g;LoRA∶LR;RAG∶D[227];Arch:T/D/G[214]

ENVISIONS builds a task-paradigm Model Component: execute symbolic candidates, use binary feedback/self-rewards, filter and train—without extra reward-model or human labels [208]. Tested on web/math/logic in Chrome/Python/Pyke [208].

ENVISIONS: self-train + env feedback[208]

ENVISIONS env-train;LLaMA3.1-8B GSM8K83.32/MATH42.13/GSM-H69.14;3 domains [208]

WM3C model architecture: causal modules/sparsity; 1,818 tasks, 5M steps in Meta-World [69].

WM3C: 1,818/99 tasks; 5M/250K steps.[69]

WM3C: causal WM; R²>0.9; 1818/99 [69]

Model:task≠arch;world/causal;gen/dyn[69]

Reward Models—SWiRL: Gemini 1.5 Pro scores steps for RL; gains +21.5/+12.3/+14.8/+11.1/+15.3% (GSM8K/HotPotQA/CofCA/MuSiQue/BeerQA); process>outcome; SFT↓ [250]. Embedding Models—Gecko’24: LLM-distilled embeddings; dates/eval missing [250]

Embedding: Gecko; Reward: SWiRL [250]

MEM1 PPO-RL QA/WS 1.27×m↓ 1.78×t↓ [71]

Architecture: BTS; stitch layers.[251]

BTS (arXiv, 2025-01-31): best avg; learned token-level hub–spoke gates combine frozen 2.7B-param seed+experts; 15Btok/7ksteps, 264M/11B train/total; eval MMLU/MBPP/HumanEval/Flores/GSM8K/MATH [251].

BTS: frozen experts+stitch layers [251]

BTS: 2.7B seed; best average [251]

MoE routes experts; SSMs aid context[72].

RAG retrieves external knowledge, augments prompts, and generates; FLARE repeats retrieval below confidence threshold. Toolformer learns tool/API choice. SSMs (Mamba, Hyena, Striped Hyena) target efficient long contexts; Monarch Mixer uses subquadratic GPU matrices; MoE gates experts (GLaM: 2/64 active); LoRA freezes weights and learns low-rank adapters [72].

Architectural Innovations: Transformer/self-attn; RETRO retrieval/2T-token/−25% params; GLaM MoE/⅓ energy/½ FLOPs [72].

Transformers; fine-tuning; pruning [252].

The supported result is narrow: **LLMs as Tool Makers (LATM)** is evidenced here only as a named public tool-construction case. The cited record identifies *Large Language Models as Tool Makers* (Tianle Cai et al.) as a **2023 arXiv preprint**; it supplies no exact first-public day or separate formal-publication date. The page gives only that citation, not LATM’s generated artifact, construction workflow, validation, deployment, comparison result, or evaluation [229].

Accordingly, LATM’s supported role here is illustrative rather than taxonomic: the source links suitable external tools with improved LLM problem-solving, but does not establish LATM-specific definitions, component categories, or construction advantages. Direct reuse of human tools, manual construction, embedding models, reward models, and architectural innovations therefore remain unresolved for LATM in this evidence slice rather than facts to infer from the citation [229].

Related evidence concerns an LLM-agent forecasting system, not LATM. Its agents autonomously identify missed news, refine their logic, and assess event impacts; properly selected supplementary information improves forecasting, whereas excessive news increases token load and irrelevant news adds noise or incorrect causal information that can degrade results [229]. This is a task-specific model/agent mechanism, not direct evidence that the system constructs Tool or Model Components, nor a direct single-LLM efficiency result [229].

The limitations are explicit: maximum token length can truncate large time-series inputs or multiple sequences and impair long-horizon accuracy; the approach augments rather than replaces traditional classification or interpolation and is less suitable where human activity has little influence or precise meteorological modeling is required [229]. For traffic forecasting over all roads in California, news gains were modest because regional or global news lacked local road detail; MSE exaggerated traffic-spike errors, while MAE indicated good average accuracy [229].

2024 evidence separates task roles from architecture: LLMs supply RL rewards, heuristics, planning, policies, subgoals, state or API-like modules; ablation tests integration, but module testing remains underexplored [253]. LATM (ICLR 2024) creates Python-function tools; Toolformer learns API choice, timing and arguments, while ToolBench/ToolLLM generates calls over 16,464 APIs [253]. RAG supplies examples; MoE uses specialized experts, but GPT-4 use is speculative [253]. Trade-offs include probabilistic outputs, context latency, deployment cost and judge bias; quantization, acceleration and rule/LLM routing help [253]. Indirect human-on-the-loop evidence covers preferences, explanations, visual change and human/machine allocation; search and categorization may be biased [253].

LATM (ICLR’24): different LLMs make/use Py funcs; varying complexity cuts tool cost; LLMs are API-like, probabilistic modules needing integration: context↑quality/latency/cost. Quant./distill./HW, rule/scale routing cut cost; test robustness—judge self-bias, LLM-EVAL/PandaLM [253].

Embedding Models map text to vectors for downstream retrieval/classification; Word2Vec/fastText/BERT/GloVe/ELMo exemplify conventional/distributional/contextual/domain-specific forms; large parameters, lengthy training, storage and interpretability constrain deployment [254]

Embedding models: task-fit vec/apps[254]

Embeddings: text→vectors; retrieval[254]

Embedding: text→vectors; tasks [254]

Embedding Models use vectors [254].

Embedding: contrastive retrieval [230]

Embedding Models: Conan-embedding-v2 embeds text; four-stage pretrain/SFT/weak+supervised embedding supports retrieval/ranking/classification/clustering/STS. 1.503B params, 3,584-D, 5.14 min/910B GPU; numeric/language bias; weaker STS [230].

Conan-embedding-v2: 1.4B param (2025); scratch-trained embedder; MTEB/MKQA [230]

Embeddings:vecs→RAG/search/IR;MLM→contrastive→FT(InfoNCE/cosine,hn/pfx);Nomic open/repro,137M,2048→8192,RoPE/SwiGLU/Flash;SwiGLU~25%;1wk/8H100;MTEB/LoCo[255]

Embedding models: contrastive/RAG [255].

NV-Embed: embedding component [222]

NV-Embed: embedding model for RAG [222].

NV-Embed 72.31 MTEB/56 tasks 2024 [222]

NV-Embed MTEB=72.31/56 tasks (2024)[222]

NV-Embed-v2: MTEB 72.31 (2024) [222]

Reward Models: Best-of-N selector [256]

Reward models score preference pairs for RLHF/Best-of-N; RM-BENCH style bias 46.6% vs random 50%; DPO+ref beat classifiers; ICLR 2025; public date unknown [256].

Reward models score/select outputs [256]

AI-Researcher: data→model→train→test; modular code; Claude 93.8% complete, 2.65/5 correct; tool→multi-agent→self-directed; embedding/reward unspecified [199].

Embeddings; LoRA→fewer models [257]; index dimensions match; method absent [231].

RewardModels:partial;LoRAr16α32;PPO[209]

KaLM-V2'25 embed: bi-attn/mean-pool; MTEB 35/56 CN/EN tasks; RAG/MoE/LoRA [232]

Embedding—KaLM (2025): bidir+mean pool; staged training, hard negatives, model soup; <1B params, MTEB 67.81, vs 3/14/18/26× larger. Mixing lowers overhead; A800 retrieval 1450/1448s, STS 68/70s. Refs: SBERT/SimCSE/BGE-M3; Arch: RAG/MoE/LoRA; mechanisms/integration absent [232]

Embedding:mix↓;1450/1448s;68/70s[232]

NV-Embed: embedding/RAG; 2-stage [223].

NV-Embed is a reusable embedder [223].

Embedding Models enable retrieval [223].

NV-Embed;WANDA/SparseGPT;RAG;4:8[223]

Gemini Embedding: task-specialized [258]

Gemini Embedding: 3,072-d vectors [258]

Gemini Embedding: NCE/MRL,3,072d’25[258]

Llama3.2-1B GEM MTEB 4.38→25.6 ’25 [259]

Embedding models: 32,000 rows;2025[259]

F2LLM (embedding model): 6M tuples [260]

F2LLM: 6M tuples; 41 MTEB tasks [260].

Emb:F2LLM6Mt;MTEB41;4B7/1.7B1/0.6B2[260]

Embedding models: InfoNCE component[261]

Embeddings:InfoNCE/4.3M/70:30/6ckpt[261]

Reward models;BT/reg;98% agreement[262]

Reward Models score responses [262]

LASER: reward models; LoRA tuning [233].

Reward models score outputs; LASER selects one; LoRA tunes efficiently [233]

LASER:RM/t;3×seq,2×ens;E/X;RM+LoRA[233]

Reward models use embeddings; LoRA [224]

Capacity conflict: 40 chars insufficient

Embedding:APILlama API→JSON 20t/572t[210]

APILlama soft: 20←572; JSON, cosine [210]

LoopTool (2026) is not eligible [81].

LoopTool: 2026 source; excluded [81].

GTM/CARG tool simulation; 89.4% Avg [84]

Embedding Models retrieve examples [211].

Embedding Models retrieve examples [211].

Embed models: contrastive retrieval[225]

Embeddings: MTEB 56d/7t (Oct 2024) [225]

Embedding:contrastive;MoE/projector[225]

Embedding models—CL/dense/IR/MTEB [225].

Embeddings: DEBATER cuts compute [225]

Embedding models: retrieval+LoRA [263]

Embedding Models: jina-embeddings-v4 (3.8B params; Nov 2025) is text-image with single/multi-vectors and 3×60M LoRA adapters for retrieval/code/techQA [263]. Competitive; long-doc retrieval except voyage-3. JVDR nDCG@5 73.98/80.55; ViDoRe 84.11/90.17 (single/multi) [263]. Single vectors are faster; multi costlier/more accurate. Limits: weaker languages/domains; untrained joint text-image, image-image retrieval and semantic similarity [263].

Embedding Models and RAG: no eligible evidence—source [264] is a 2026 study, beyond the 2025-12-31 cutoff.

Embedding Models: [264] excluded (2026).

T‑VEC emb.(2025): triplet/T‑Embed;tel. retrieval,75% data open,1.5k pairs[265]

T-VEC: 2025 embedding; retrieval [265].

BMEmbed adapts embeddings for RAG [266].

Embedding Models: BM25/listwise RAG retrieval; LoRA rank 16, 1,000 steps [266].

Embedding models:InfoNCE;BMEmbed BM25-listwise RAG/IR;LoRA rank 16/1k steps[266]

Embedding models:BM25→RAG/listwise[266]

SB/SC/T5/NV;RAG:BM25→BEmb;LoRA16/1k[266]

Embedding models support retrieval [267]

Embeddings: data→InfoNCE→retrieval [267]

MoE: general MRL/quantization+dense/sparse+contrastive/PE context. RAG: 2020 retrieval+generation. LoRA: Jina-v3, 8,192 tok/32d. Emb.: MLM/NTP→InfoNCE; hard negatives; E5 93L; Qwen 150M-pair; retrieval; 0.6–8B/1,024–4,096d; cost↑ [267].

Embedding models: 93 languages [267]

Embedding models: contrastive loss [267]

Embedding models:contrastive 2025[268]

MoTE: task-routed embeddings, 2025 [268]

Embedding Models: 2026; excluded [269]

Embedding models: 2026; ineligible [269]

Embeddings, 2025: CLSD ranks pairs [270]

RAG retrieves;MoE routes;LoRA adapts[271]

Reward Models: 5 named; rank→RM→PPO[271].

Embedding models: retrieval [272].

Embeddings: contrastive; retrieval [272]

Embedding models use contrastive training for retrieval; task-sensitive [272]

Embeddings: contrast→retrieve/rank [272]

Embeddings: retrieval; LoRA; DPR [272]

Embeddings: retrieval, contrastive [272]

Emb:8m/2d;Chroma;MRR(.90/.99);Rec[273]

Embedding models: Hungarian QA retrieval; 8 models/Chroma; MRR .90/.99; 2025 [273]

Embeddings: retrieval; unresolved [168]

CoE uses e5-mistral→kNN→experts;98% test;MT-Bench≈large at↓active params [274]

CoE:1exp/input;E5+kNN:98%test;LoRA—[274]

CoE/e5 router: 98% (2024) [274]

Emb.models:150m-pair;InfoNCE→IR/RAG[275]

Embeddings: retrieval; contrastive [275]

Embedding Models: vector retrieval [275]

Embedding: contrastive; LoRA: PEFT [275]

Embeddings: prompt/tune/specialize [275]

Embedding Models: retrieval loop [275]

CoE routes prompts via embeddings [276].

E5 router: 98% test accuracy [276]

Embedding models retrieve; nDCG@10 [277]

Embedding Models vectorize chunks/queries; RAG feeds top-10 passages to LLMs. Cohere retrieves; E5 278/560M:0.01–0.02 nDCG@10; MoE NA; size nondecisive [277].

RAG retrieves top-10 passages [277].

Embeddings: GTE-base, 109M params [277]

Embedding models: ineligible 2026 [216].

Embedding models: BGE retrieves; rerank/call; Docker verifies/integrates [278].

Embedding→BGE retrieval; Docker val [278]

Embedding:retrieval;RAG:4 modules[279]

WTS:retrieve→prune→answer→KG↑;BERT[279]

Embedding models route RAG via vectors/similarity; NV-Embed-v2, Llama2Vec [220].

Embedding models route LLMs [220].

Embedding models vectorize text; RAG retrieves chunks to ground output [280].

Embed/vector;RAG ground;agents+tool[280]

ROUTERRETRIEVER: routed embeddings [281]

ROUTERRETRIEVER: LoRA 0.5%/expert [281].

LoRA:.5%,~1M/ex,2×;BT-MiX/route(24)[281]

Granite Embedding—retrieval model [282].

Embeddings: retrieval, contrastive [282]

Embedding models:CL→retr.;MTEB8×56[282]

Granite: retrieval/contrastive [282]

## References

[1] <https://bair.berkeley.edu/blog/2024/02/18/compound-ai-systems/> Compound AI systems; Neural–symbolic geometry; account; Dynamic knowledge and access control
[2] <https://arxiv.org/html/2308.08155v2> study; AutoGen; AutoGen control flow; report; AutoGen mathematical evaluation; AutoGen and OptiGuide; OptiGuide user comparison; OptiGuide workflow results; Hu…
[3] <https://proceedings.iclr.cc/paper_files/paper/2024/file/28e50ee5b72e90b50e7196fde8ea260e-Paper-Conference.pdf> paper; ToolLLM conference paper; ToolEval
[4] <https://arxiv.org/html/2505.18286v1> study; SAS/MAS comparison; Model-dependent collaboration gains; Coordination cost; Difficulty-based routing; SAS/MAS token accounting; Confidence-guided credit
[5] <https://arxiv.org/html/2312.00763> study; ExploreLLM design; ExploreLLM user study
[6] <https://ar5iv.labs.arxiv.org/html/2309.02427v1> Cognitive architectures for language agents; CoALA; CoALA memory; Production-rule construction
[7] <https://arxiv.org/abs/2210.03629> ReAct; paper; ReAct API integration
[8] <https://www.anthropic.com/research/building-effective-agents> Workflows and agents; Manual tool-interface design
[9] <https://arxiv.org/html/2406.10300v1> LLMs as software components; AutoDroid interaction architecture
[10] <https://aclanthology.org/2024.findings-emnlp.289.pdf> Tool selection and verification; ToolSelect data construction; TOOLVERIFIER
[11] <https://arxiv.org/html/2501.11223v1> Reasoning Language Models blueprint; RLM component construction; RLM policy and value architecture; RLM pipelines
[12] <https://doi.org/10.1007/s41019-025-00296-9> Tool-learning taxonomy
[13] <https://arxiv.org/html/2506.04565v1> CAIS, public v1; survey; Retrieval construction
[14] <https://arxiv.org/html/2503.15944v1> Atomic Reasoner; paper; Atomic Reasoner mechanism; Atomic Reasoner experiments
[15] <https://www.preprints.org/manuscript/202512.2119> Memory implementations
[16] <https://arxiv.org/html/2512.11620v1> Modular robot perception; study; Robot-LAM architecture; Robot interaction results; Robot component integration; Robot planning architectures; Robot planning c…
[17] <https://arxiv.org/html/2512.08296> Agent–tool execution graphs
[18] <https://arxiv.org/html/2502.12018v4> paper; Atom of Thoughts
[19] <https://arxiv.org/html/2509.20784v2> paper; Representational atoms
[20] <https://arxiv.org/html/2509.08203> paper; Componentized outputs; Componentization study; Componentization architecture
[21] <https://proceedings.neurips.cc/paper_files/paper/2025/file/f2afcc872cb6a3e25f968ebfe6f497a9-Paper-Conference.pdf> paper; Mathematical atomic abilities
[22] <https://arxiv.org/html/2510.25741v1> paper; LoopLM; LoopLM construction and results
[23] <https://arxiv.org/html/2302.04761v1> paper; Toolformer; Toolformer training recipe; Toolformer inference setup
[24] <https://doi.org/10.1101/2025.08.22.25334049> study; Clinical workload study; Clinical task isolation
[25] <https://arxiv.org/html/2403.11085v1> benchmark; m&m’s executable tools; m&m’s construction
[26] <https://arxiv.org/html/2307.16789v2> Dataset details; ToolBench API representation; ToolLLM retriever
[27] <https://aclanthology.org/2025.naacl-findings.65.pdf> ToolSandbox state dependencies; Stateful conversational evaluation; ToolSandbox evaluation construction
[28] <https://www.anthropic.com/engineering/multi-agent-research-system> report; Parallel research execution; Research-system analysis
[29] <https://arxiv.org/abs/2510.26658v1> paper; AsyncThink
[30] <https://proceedings.iclr.cc/paper_files/paper/2024/file/ed91353f700d113e5d848c7e04a858b0-Paper-Conference.pdf> LATM functional caching; paper; LATM construction recipe; LATM experimental setup; LATM cost model
[31] <https://aclanthology.org/2025.hcinlp-1.3.pdf> User-control trade-offs
[32] <https://megagon.ai/compound-ai-systms/> Enterprise component dependencies
[33] <https://aclanthology.org/2025.acl-long.1266> Tool creation versus tool learning; paper; TOOLMAKER
[34] <https://arxiv.org/html/2505.16988v1> Fixed multi-agent workflows
[35] <https://arxiv.org/html/2405.16533v2> paper; AutoTools; AutoTools evaluation
[36] <https://doi.org/10.48550/arxiv.2501.16945> paper; ToolFactory
[37] <https://arxiv.org/html/2412.12591v2> Embedding-model survey; Tuning-free embedding methods; Instruction-conditioned embeddings; Embedding architectural adaptations
[38] <https://arxiv.org/html/2510.14321v2> LREM; LREM training
[39] <https://aclanthology.org/2025.findings-emnlp.970/> Learning from rewards
[40] <https://ojs.aaai.org/index.php/AAAI/article/download/34960/37115> Preference-data construction
[41] <https://aclanthology.org/2025.findings-emnlp.970.pdf> Human-feedback learning strategies; Automated reward sources; Reward-learning taxonomy
[42] <https://cdn.openai.com/improving-mathematical-reasoning-with-process-supervision/Lets_Verify_Step_by_Step.pdf> PRM800K; Process-supervision results
[43] <https://arxiv.org/html/2510.01925v2> Automated process supervision; Reward-model architectures
[44] <https://aclanthology.org/2025.findings-naacl.96.pdf> RewardBench
[45] <https://aclanthology.org/2025.findings-acl.114/> Context-aware reward modeling
[46] <https://www.earthdoc.org/content/papers/10.3997/2214-4609.202032024>
[47] <https://zenodo.org/records/14626000>
[48] <https://medium.com/@kylerkinnear/the-big-loop-hypothesis-a-journey-through-science-philosophy-and-harmony-9bb2378693fb>
[49] <https://ctflab.mae.cornell.edu/papers/Desjardins%20et%20al..%202013.%20Direct%20numerical%20and%20large-eddy%20simulation%20of%20primary%20atomization%20in%20complex%20geometries.pdf>
[50] <https://arxiv.org/html/2509.20784v2>
[51] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11470924/>
[52] <https://patents.google.com/patent/US10273567B2/sv>
[53] <https://utw10945.utweb.utexas.edu/sites/default/files/2025/96%20Review%20on%20Atomization%20of%20Metals.pdf>
[54] <https://doi.org/10.17863/cam.66459>
[55] <https://cfpb.github.io/design-system/development/atomic-components>
[56] <https://doi.org/10.24963/ijcai.2025/2>
[57] <https://doi.org/10.21203/rs.3.rs-10533072/v1>
[58] <https://aiagentindex.mit.edu/>
[59] <https://datatracker.ietf.org/doc/html/draft-rosenberg-aiproto-nact-00>
[60] <https://arxiv.org/html/2506.04565v2>
[61] <https://dl.acm.org/doi/pdf/10.1145/3843778.3856135>
[62] <https://coursiv.io/blog/ai-for-construction>
[63] <https://doi.org/10.52202/085713-0439>
[64] <https://mosaico-project.eu/wp-content/uploads/2026/09/With-disclaimer-D2.1-A-taxonomy-of-AI-agents-for-SEl.pdf>
[65] <http://www.sce.carleton.ca/faculty/esfandiari/agents/papers/dastani-aamas05.pdf>
[66] <https://explosion.ai/blog/atomic-nlp>
[67] <https://www.frontiersin.org/journals/neurorobotics/articles/10.3389/fnbot.2024.1342786/full>
[68] <https://www.sciopen.com/article/10.26599/JIC.2024.9180039>
[69] <https://arxiv.org/html/2505.08361>
[70] <http://www.npg.nature.com/articles/s41467-025-63804-5.pdf>
[71] <https://arxiv.org/pdf/2506.15841v2.pdf>
[72] <https://arxiv.org/html/2402.06196v2>
[73] <https://doi.org/10.1145/3708359.3712089>
[74] <https://dl.acm.org/doi/pdf/10.1145/3706599.3706693>
[75] <https://github.com/doxav/CollabToolBuilder>
[76] <https://arxiv.org/html/2509.11626>
[77] <https://arxiv.org/pdf/2510.05746v1.pdf>
[78] <https://doi.org/10.1115/1.4070328>
[79] <https://arxiv.org/html/2508.16279>
[80] <https://arxiv.org/pdf/2504.03771>
[81] <https://doi.org/10.18653/v1/2026.acl-long.968>
[82] <https://doi.org/10.18653/v1/2025.acl-long.1139>
[83] <https://doi.org/10.48550/arxiv.2410.08126>
[84] <https://arxiv.org/html/2512.04535v2>
[85] <https://arxiv.org/html/2510.14453>
[86] <https://doi.org/10.4211/hs.4294e9cedfca49838c2b191bc6f62260>
[87] <https://arxiv.org/pdf/2501.13956>
[88] <https://arxiv.org/pdf/2502.12110v11.pdf>
[89] <https://arxiv.org/html/2506.06326>
[90] <https://arxiv.org/html/2404.09982v1>
[91] <https://trepo.tuni.fi/handle/10024/226965>
[92] <https://arxiv.org/html/2509.04876>
[93] <https://www.mdpi.com/2075-5309/15/23/4296>
[94] <https://browse.arxiv.org/html/2401.05384v1>
[95] <https://arxiv.org/html/2510.22780v2>
[96] <https://arxiv.org/pdf/2511.20920>
[97] <https://doi.org/10.48550/arxiv.2309.17428>
[98] <https://www.cloudflare.com/learning/ai/what-is-large-language-model/>
[99] <https://pub.towardsai.net/from-brains-to-agents-my-journey-building-llm-systems-that-act-d559d47c3509>
[100] <https://doi.org/10.35490/ec3.2026.244>
[101] <https://www.scitepress.org/Papers/2025/133756/133756.pdf>
[102] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8830986/>
[103] <https://aclanthology.org/2023.emnlp-demo.51.pdf>
[104] <https://link.springer.com/article/10.1007/s44163-026-02342-5>
[105] <https://doi.org/10.1609/aaaiss.v7i1.36891>
[106] <https://ojs.aaai.org/index.php/AAAI-SS/article/download/36891/39029>
[107] <https://arxiv.org/html/2512.07926v1>
[108] <https://arxiv.org/pdf/2407.14788>
[109] <https://zenodo.org/records/19919086/files/Taxonomy_v2.csv?download=1>
[110] <https://arxiv.org/pdf/2311.13148>
[111] <https://doi.org/10.48550/arxiv.2412.18161>
[112] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10733136/>
[113] <https://doi.org/10.1145/3711896.3736849>
[114] <https://arxiv.org/html/2509.11626v1>
[115] <https://inspirehep.net/files/a10cd4201906eb0c19d2a2632e82584d>
[116] <https://arxiv.org/pdf/2510.04173>
[117] <https://arxiv.org/html/2401.15724v3>
[118] <https://soominkim.github.io/project/IJHCI2025_PromptPilot.pdf>
[119] <https://doi.org/10.48550/arxiv.2512.03568>
[120] <https://aclanthology.org/2023.emnlp-main.111.pdf>
[121] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12939955/>
[122] <https://doi.org/10.1016/j.cogsys.2013.04.002>
[123] <https://arxiv.org/abs/1410.0176>
[124] <https://doi.org/10.5220/0014473600004052>
[125] <https://arxiv.org/html/2309.12780v3>
[126] <https://www.microsoft.com/en-us/research/articles/autogen-v0-4-reimagining-the-foundation-of-agentic-ai-for-scale-extensibility-and-robustness/>
[127] <https://doi.org/10.5220/0014442700004052>
[128] <https://www.mintlify.com/library/best-technical-search-apis-for-ai-agents>
[129] <https://www.preprints.org/frontend/manuscript/a66798aba0a71bf9ce0a3eb35edcef4f/download_pub>
[130] <https://doi.org/10.1109/fllm67465.2025.11391226>
[131] <https://doi.org/10.1007/978-981-92-1468-6_10>
[132] <https://doi.org/10.48550/arxiv.2508.15294>
[133] <https://doi.org/10.1101/2025.08.22.25334049>
[134] <https://doi.org/10.48550/arxiv.2410.22584>
[135] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12485071/>
[136] <https://www.eecis.udel.edu/~decker/courses/886f04/pubs/KinnyGeorgeffATAL96.pdf>
[137] <https://arxiv.org/pdf/2505.18286v1.pdf>
[138] <https://doi.org/10.1038/s41467-025-63804-5>
[139] <https://arxiv.org/html/2505.18286>
[140] <https://arxiv.org/pdf/2501.06322>
[141] <https://doi.org/10.48550/arxiv.2510.12120>
[142] <https://doi.org/10.1016/j.jss.2007.02.047>
[143] <https://www.industry.gov.au/publications/risks-and-controls-multi-agent-systems>
[144] <https://www.scitepress.org/Papers/2025/133030/133030.pdf>
[145] <https://arxiv.org/html/2602.17753v1>
[146] <https://arxiv.org/html/2502.04506>
[147] <https://doi.org/10.18653/v1/2026.acl-long.775>
[148] <https://proceedings.neurips.cc/paper_files/paper/2024/file/e6c185ba1ac2880d6f53aae3cfa80469-Paper-Conference.pdf>
[149] <https://aclanthology.org/2025.findings-emnlp.43.pdf>
[150] <https://futureagi.com/blog/llm-agent-architectures-core-components/>
[151] <https://www.scitepress.org/Papers/2023/122391/122391.pdf>
[152] <https://doi.org/10.3390/electronics13224416>
[153] <https://research.ibm.com/blog/toolops-altk-agents-tools>
[154] <https://link.springer.com/article/10.1007/s10462-025-11471-9>
[155] <https://link.springer.com/article/10.1007/s10462-025-11422-4>
[156] <https://www.nature.com/articles/s42256-026-01268-y>
[157] <https://www.sciencedirect.com/org/science/article/pii/S1526149226001906>
[158] <https://doi.org/10.1145/1529282.1529432>
[159] <https://www.cse.sc.edu/~huhns/chapters/BergentiHuhnsAOSE.pdf>
[160] <https://lirias.kuleuven.be/server/api/core/bitstreams/5b9d7caa-daa5-426b-b252-38b44d739d79/content>
[161] <https://doi.org/10.26562/ijirae.2025.v1206.02>
[162] <https://doi.org/10.3389/fpsyg.2025.1591618>
[163] <https://arxiv.org/html/2308.08155v2>
[164] <https://arxiv.org/abs/2408.15247>
[165] <https://doi.org/10.1016/s0169-023x(01)00058-1>
[166] <https://arxiv.org/pdf/2310.00194>
[167] <https://www.lancaster.ac.uk/staff/chopraak/pdfs/programming-MAS-2009.pdf>
[168] <https://arize.com/resources/ai-model-lifecycle-management/>
[169] <https://ar5iv.labs.arxiv.org/html/1006.1450>
[170] <https://arxiv.org/html/2506.12508v5>
[171] <https://www.federalregister.gov/documents/2025/01/15/2025-00636/framework-for-artificial-intelligence-diffusion>
[172] <https://apxml.com/courses/intro-llm-agents/chapter-4-equipping-agents-with-tools/survey-of-available-tool-categories>
[173] <https://arxiv.org/html/2404.11584>
[174] <https://zhu.codes/papers/llmtools.pdf>
[175] <https://www.vldb.org/2025/Workshops/VLDB-Workshops-2025/LLM+Graph/LLMGraph-8.pdf>
[176] <https://github.com/hydang99/opentools>
[177] <https://doi.org/10.1007/s44336-025-00024-x>
[178] <https://arxiv.org/pdf/2409.11393>
[179] <https://arxiv.org/html/2509.11067v1>
[180] <https://ar5iv.labs.arxiv.org/html/2508.19042>
[181] <https://arxiv.org/pdf/2512.09458>
[182] <https://doi.org/10.48550/arxiv.2506.19500>
[183] <https://arxiv.org/html/2512.04388v3>
[184] <https://dl.acm.org/doi/10.1145/3758871.3758946>
[185] <https://arxiv.org/pdf/2506.19500>
[186] <https://doi.org/10.1145/3704268.3748670>
[187] <https://arxiv.org/pdf/2508.12981v1.pdf>
[188] <https://doi.org/10.48550/arxiv.2408.13406>
[189] <https://doi.org/10.48550/arxiv.2512.16310>
[190] <https://aclanthology.org/2025.findings-naacl.448.pdf>
[191] <http://www.cs.cmu.edu/~tomasic/doc/2009/ZimmermanEtAlCHI2009.pdf>
[192] <https://doi.org/10.1145/3713082.3730377>
[193] <https://doi.org/10.48550/arxiv.2404.05465>
[194] <https://doi.org/10.18653/v1/2025.acl-long.1266>
[195] <https://www.cs.cmu.edu/~ckaestne/pdf/icsenier16.pdf>
[196] <https://mastra.ai/articles/ai-agent-evaluation>
[197] <https://arxiv.org/html/2512.22137v3>
[198] <https://odr.chalmers.se/items/2a008985-ebbd-4cd1-926a-947499da2a66>
[199] <https://proceedings.neurips.cc/paper_files/paper/2025/file/0d904d300a105809a2114d727851e759-Paper-Conference.pdf>
[200] <https://www.itu.int/epublications/publication/itu-t-fstr-hai-2025-10-holistic-ai-a-survey-about-a-technical-framework-for-artificial-intelligence-ai-services-and-ai-capabilities>
[201] <https://arxiv.org/html/2503.10071v1>
[202] <http://www.ytzr.com/third_1.asp?id=704>
[203] <https://doi.org/10.48550/arxiv.2409.14457>
[204] <https://chenc10.github.io/assets/pdf/2024_iwqos_pstcs.pdf>
[205] <https://arxiv.org/abs/2308.08155>
[206] <https://proceedings.neurips.cc/paper_files/paper/2023/file/77c33e6a367922d003ff102ffb92b658-Paper-Conference.pdf>
[207] <https://doi.org/10.3403/30309017>
[208] <https://aclanthology.org/2025.acl-long.635.pdf>
[209] <https://arxiv.org/pdf/2502.01600v3.pdf>
[210] <https://arxiv.org/html/2501.16945>
[211] <https://openaccess.thecvf.com/content/CVPR2025/papers/Lin_ChatHuman_Chatting_about_3D_Humans_with_Tools_CVPR_2025_paper.pdf>
[212] <https://link.springer.com/article/10.1007/s10462-025-11403-7>
[213] <https://arxiv.org/html/2512.10350v5>
[214] <https://cypris.ai/insights/ai-accelerated-materials-discovery-in-2025-how-generative-models-graph-neural-networks-and-autonomous-labs-are-transforming-r-d>
[215] <https://arxiv.org/html/2411.10478v1>
[216] <https://link.springer.com/article/10.1007/s44163-026-01373-2>
[217] <https://www.researchgate.net/publication/393065457_LLM-Based_Agents_for_Tool_Learning_A_Survey_LLM-Based_Agents_for_Tool_Learning_A_SurveyW_Xu_et_al>
[218] <https://aclanthology.org/anthology-files/anthology-files/pdf/acl/2025.acl-long.1266.pdf>
[219] <https://aclanthology.org/2025.acl-long.1266.pdf>
[220] <https://ar5iv.labs.arxiv.org/html/2502.00409>
[221] <https://pmc.ncbi.nlm.nih.gov/articles/PMC13205700/>
[222] <https://proceedings.iclr.cc/paper_files/paper/2025/file/c4bf73386022473a652a18941e9ea6f8-Paper-Conference.pdf>
[223] <https://arxiv.org/pdf/2405.17428>
[224] <https://doi.org/10.48550/arxiv.2502.04357>
[225] <https://arxiv.org/pdf/2412.09165v4.pdf>
[226] <https://arxiv.org/html/2510.25741v1>
[227] <https://link.springer.com/article/10.1007/s10462-025-11241-7>
[228] <https://link.springer.com/article/10.1007/s40684-026-00890-w>
[229] <https://proceedings.neurips.cc/paper_files/paper/2024/file/6aef8bffb372096ee73d98da30119f89-Paper-Conference.pdf>
[230] <https://aclanthology.org/2025.emnlp-main.758.pdf>
[231] <https://opendl.ifip-tc6.org/db/conf/cnsm/cnsm2025/1571190267.pdf>
[232] <https://www.arxiv.org/pdf/2506.20923v1>
[233] <https://papers.nips.cc/paper_files/paper/2025/file/a996037f92d46d9f5d1094d16b5f4549-Paper-Conference.pdf>
[234] <https://github.com/UKGovernmentBEIS/inspect_ai/tree/main/examples/intervention>
[235] <https://pure.mpg.de/rest/items/item_3726568_1/component/file_3726569/content>
[236] <https://doi.org/10.1007/s41693-022-00072-5>
[237] <https://doi.org/10.1002/rob.22154>
[238] <https://arxiv.org/html/2305.17126v2>
[239] <https://proceedings.iclr.cc/paper_files/paper/2024/file/ed91353f700d113e5d848c7e04a858b0-Paper-Conference.pdf>
[240] <https://doi.org/10.48550/arxiv.2305.17126>
[241] <https://aclanthology.org/2024.findings-emnlp.289.pdf>
[242] <https://huggingface.co/papers/2305.17126>
[243] <https://arxiv.org/pdf/2310.18338v2.pdf>
[244] <https://koala.science/storage/pdfs/640e44ec-91da-4d38-9b9a-4a3a20ad15d0.pdf>
[245] <https://arxiv.org/abs/2305.17126>
[246] <https://proceedings.iclr.cc/paper_files/paper/2024/hash/ed91353f700d113e5d848c7e04a858b0-Abstract-Conference.html>
[247] <https://doi.org/10.1109/iceace67491.2025.11439251>
[248] <https://magazine.sebastianraschka.com/p/state-of-llms-2025>
[249] <https://arxiv.org/html/2409.02877v1>
[250] <https://scalingintelligence.stanford.edu/pubs/sdgrl.pdf>
[251] <https://doi.org/10.48550/arxiv.2502.00075>
[252] <https://uit.stanford.edu/service/techtraining/ai-demystified/llm>
[253] <https://arxiv.org/pdf/2512.04680>
[254] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9944441/>
[255] <https://arxiv.org/html/2402.01613v2>
[256] <https://proceedings.iclr.cc/paper_files/paper/2025/file/6da1eec80095dc5937f7716db15aca4b-Paper-Conference.pdf>
[257] <https://www.youtube.com/watch?v=WumStBfoArc>
[258] <https://arxiv.org/pdf/2503.07891v1.pdf>
[259] <https://arxiv.org/pdf/2506.04344v1.pdf>
[260] <https://arxiv.org/html/2510.02294>
[261] <https://arxiv.org/html/2511.07025>
[262] <https://aclanthology.org/2025.emnlp-main.8.pdf>
[263] <https://aclanthology.org/2025.mrl-main.36.pdf>
[264] <https://doi.org/10.48009/3_iis_2026_130>
[265] <https://aclanthology.org/2025.emnlp-industry.168/>
[266] <https://aclanthology.org/2025.findings-acl.357.pdf>
[267] <https://doi.org/10.1145/3831684>
[268] <https://doi.org/10.18653/v1/2025.findings-acl.1168>
[269] <https://doi.org/10.1109/mipr70517.2026.00054>
[270] <https://doi.org/10.18653/v1/2025.findings-emnlp.115>
[271] <https://dl.acm.org/doi/10.1145/3744746>
[272] <https://arxiv.org/html/2412.12591v1>
[273] <https://doi.org/10.36244/icj.2025.4.1>
[274] <https://doi.org/10.48550/arxiv.2412.01868>
[275] <https://arxiv.org/html/2412.12591v2>
[276] <https://arxiv.org/pdf/2412.01868v1.pdf>
[277] <https://www.mdpi.com/2504-2289/9/5/141>
[278] <https://github.com/lujiaxuan0520/Test-Time-Tool-Evol>
[279] <https://dlnext.acm.org/doi/10.1145/3690624.3709187>
[280] <https://doi.org/10.5753/sbc.17956.8.2>
[281] <https://doi.org/10.1609/aaai.v39i11.33306>
[282] <https://arxiv.org/pdf/2502.20204v1.pdf>
[283] <https://arxiv.org/pdf/2510.00379v1.pdf>
[284] <https://arxiv.org/abs/2310.10908>
[285] <https://arxiv.org/html/2311.16822>
