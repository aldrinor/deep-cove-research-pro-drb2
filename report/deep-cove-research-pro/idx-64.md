# T-Cell Exhaustion: Defining Features, Transcriptional States, and Experimental Models Before July 2023

**T-cell exhaustion is an antigen-driven differentiation state:** exhausted T cells (Tex), studied most extensively among antigen-specific CD8+ T cells in chronic infection and cancer, develop impaired proliferative and effector capacity together with sustained inhibitory-receptor expression and distinct transcriptional, epigenetic, and metabolic programs. Exhaustion is heterogeneous: T cell factor 1 (TCF-1)-positive progenitor Tex maintain the response, whereas terminally exhausted cells have less renewal capacity but can retain substantial cytotoxic activity. These distinctions are supported by primary mouse infection and tumor studies, including Khan et al. (2019) [1] and Miller et al. (2019) [2].

**The experimental trade-off is clear:** in-vitro generation offers speed, scale, and control over individual causes; direct isolation provides cells shaped by actual disease, tissue niches, and prolonged antigen exposure. Representative cultures develop exhaustion-associated features within **5–10 days**, compared with approximately **3–5 weeks** for established chronic-infection sampling in mice. In-vitro systems reproduce important parts of exhaustion, but their physiological fidelity depends on the particular molecular and functional features being studied. Zhao et al. (2020) [3] provide a five-day example; the publicly posted April 2023 P14-model preprint [4] demonstrates both useful similarities and consequential differences from directly isolated Tex.

| Requested question | Decisive finding | Research judgment |
|---|---|---|
| Definition | Persistent-antigen adaptation with coordinated dysfunction and regulatory reprogramming | More than transient activation |
| Transcription factors | TCF-1 supports progenitors; NFAT–TOX/NR4A circuitry supports exhaustion | Networks and developmental stage matter |
| Inhibitory receptors | Sustained, overlapping checkpoint expression accompanies functional restraint | A single receptor is insufficient |
| Effector functions | Cytokine breadth and renewal decline; killing can persist | Dysfunction is selective, not complete |
| Metabolic activity | Glycolytic and mitochondrial insufficiency interact with tissue stress | No single universal metabolic state |
| Three-state factor comparison | TCF-1 differs consistently; several other rankings depend on context | Use qualified qualitative profiles |
| Direct isolation | Mouse infection sampling: 21–35 days; tumor examples: 10–21 days | Best for disease-conditioned states |
| In-vitro generation | Representative endpoints: 5, 7, or 10 days; one model expands approximately ninefold | Best for controlled perturbation |
| Physiological simulation | Cultures reproduce selected features, not every tissue-dependent program | Complement direct isolation |

**The report follows the experimental questions:** it first defines exhaustion and its boundaries, then develops the four requested biological dimensions. The transcription-factor table separates robust state differences from context-dependent patterns; the methods comparison addresses all six requested aspects. The final analysis explains when in-vitro Tex generation is informative and why antigen history, accessory cells, tissue organization, metabolism, and population heterogeneity can change its interpretation. The literature scope is public work published or posted through **30 June 2023**, with preprints and conference abstracts identified explicitly.

## 1. Definition and boundaries of T-cell exhaustion

### What makes a T cell exhausted?

**Exhaustion combines history, function, and identity:** Tex arise after activation in settings where antigenic stimulation persists rather than resolving. Their characteristic profile includes reduced cytokine production, diminished capacity for sustained expansion, altered cytotoxic responses, and prolonged expression of multiple inhibitory receptors. Crucially, they also acquire regulatory programs that distinguish them from conventional effector T cells, abbreviated Teff, and memory T cells, abbreviated Tmem. Khan et al.’s primary mouse study established TOX as a central regulator of this distinct transcriptional and chromatin state. [1]

**A useful operational definition is multidimensional:** an antigen-specific population in chronic infection or cancer is most convincingly classified as Tex when persistent-antigen exposure accompanies functional impairment, coordinated inhibitory-receptor expression, and an exhaustion-consistent regulatory program. Functional impairment should be evaluated against a relevant comparator: an acutely generated effector population, a memory population, or a less differentiated exhausted subset. These comparisons answer different questions, so “less functional” should always identify the function and reference population. The 2020 Journal of Leukocyte Biology review [5] synthesizes these developmental and functional distinctions.

**Exhaustion is not simple cellular inactivity:** many Tex remain alive, encounter antigen, cycle, and perform selected effector functions. Their central deficit may be the inability to combine immediate activity with durable proliferation, survival, and recall. In Miller et al.’s mouse melanoma experiments, terminally exhausted tumor-infiltrating lymphocytes—TILs—were more cytotoxic than progenitor Tex, yet progenitors persisted better and produced superior long-term tumor control. [2]

### Distinguishing exhaustion from related states

**The developmental distinctions prevent misclassification:** transient activation, anergy, senescence, and exhaustion can all involve reduced responses or overlapping surface markers, but they are not interchangeable explanations.

| State | Typical developmental setting | Principal distinction |
|---|---|---|
| Transient activation | Recent antigen encounter | Checkpoints can rise without durable dysfunction |
| Conventional effector differentiation | Productive activation and expansion | Strong immediate effector activity |
| Anergy | Antigen recognition with inadequate costimulation | Hyporesponsiveness established during priming |
| Senescence | Extensive proliferative history | Stable growth arrest |
| Exhaustion | Persistent antigen after activation | Coordinated functional and regulatory adaptation |

The distinctions between exhaustion, anergy, and senescence are summarized in the 2017 review of exhaustion biology [6]; the effector-versus-exhausted comparison is supported by Khan et al.[1].

**PD-1 alone does not establish exhaustion:** programmed cell death protein 1, or PD-1, is induced during normal activation as well as maintained during chronic stimulation. In a primary mouse study comparing acute lymphocytic choriomeningitis virus, or LCMV, Armstrong infection with chronic Clone 13 infection, antigen-specific P14 CD8+ cells expressed similarly high PD-1 on days 2–3. By day 40, persistent PD-1 and impaired cytokine production distinguished the chronic response from the resolved acute response. [7]

**Terminal exhaustion is a separate concept:** “terminally exhausted” does not mean the same thing as terminal effector differentiation or replicative senescence. Buggert et al.’s primary human HIV study illustrates the distinction: HIV-specific cells with low T-bet and high EOMES showed poor polyfunctionality and multiple inhibitory receptors, yet predominantly occupied a transitional-memory phenotype rather than the study’s terminally differentiated effector compartment. [8]

### Why exhaustion contains several developmental states

**Progenitor Tex sustain the response:** TCF-1-positive progenitors self-renew and generate more differentiated exhausted descendants. They are often called precursor exhausted, progenitor exhausted, or stem-like exhausted cells. “Stem-like” describes their renewal and developmental capacity; it does not make them equivalent to healthy conventional memory cells. They already carry features of the exhaustion-associated program. [9]

**Terminal Tex specialize differently:** terminal populations generally lose TCF-1, accumulate additional inhibitory receptors, and show limited capacity for further expansion after restimulation. Between progenitors and terminal cells, effector-like intermediate populations can reacquire substantial cytotoxic activity. Beltra et al.’s primary study identified four Ly108/CD69-defined subsets and linked their transitions to changing TCF-1, T-bet, EOMES, and TOX programs. [10]

**The pathway can diverge early:** exhaustion is often described as progressive deterioration of established effector cells, but chronic-antigen programming need not wait until a fully developed effector response has passed. In acute-versus-chronic LCMV experiments, Utzschneider et al. found exhaustion hallmarks emerging within days in TCF-1-positive precursors while early effector cells retained polyfunctional features. Their descendants subsequently propagated the exhausted response. [11]

**Exhaustion also serves host protection:** persistent stimulation creates a conflict between pathogen or tumor control and damage caused by excessive immune activity. An exhaustion program can preserve antigen-specific cells and restrain immunopathology, even while limiting clearance. Thus, eliminating an exhaustion-associated regulator is not automatically equivalent to producing a more durable protective response. Nayar et al.’s chronic-LCMV study discusses this balance, while TOX-focused work connects exhaustion programming to persistence under sustained stimulation. [12][13]

### What the different evidence settings establish

**Mouse experiments supply causal leverage:** LCMV Armstrong, Clone 13, and Docile comparisons permit controlled analysis of antigen persistence, developmental time, and antigen-specific cells. Tumor models such as B16-OVA permit additional tests of tumor entry, residence, antigen recognition, and local suppression. Conditional gene deletion, overexpression, and adoptive transfer connect regulatory changes to cell fate rather than merely documenting their coexistence. [11][2]

**Human samples establish disease relevance:** chronic-HIV peripheral blood, hepatitis C virus-specific cells, melanoma tissue, renal-cell-carcinoma TILs, and clinical engineered T-cell products reveal related but nonidentical dysfunction programs. For example, Baitsch et al. found functional tumor-specific cells in circulation alongside exhaustion-profile cells in melanoma metastases. This directly demonstrates that anatomical location can separate different functional states within the same disease setting. [14]

**Cultures isolate particular mechanisms:** repeated antigen stimulation, repeated CD3/CD28 stimulation, engineered receptor signaling, and imposed metabolic stresses allow individual inputs to be manipulated. Their strongest contribution is determining what a defined stimulus or perturbation does under specified conditions. The resulting interpretation becomes physiological when the relevant relationship also holds in disease-conditioned cells or an appropriate in-vivo model.

**The definition’s practical consequence:** classify exhaustion from a coordinated developmental and functional profile, then specify the exhausted subset and disease setting before interpreting a marker or intervention.

## 2. Characteristics across four dimensions

### Transcription factors

**The principal change is regulatory rewiring:** exhaustion involves altered use of transcription factors, their binding partners, and accessible DNA regions—not simply uniform increases in a list of proteins. The seven requested factors span different functions: maintaining progenitors, supporting effector differentiation, translating persistent stimulation, and stabilizing exhaustion-associated identity. Their roles therefore need to be interpreted as an interacting network.

**NFAT translates persistent calcium signaling:** nuclear factor of activated T cells, or NFAT, becomes active downstream of T-cell receptor, or TCR, signaling through calcium and the phosphatase calcineurin. During productive activation, NFAT cooperates with activator protein 1, or AP-1, to promote effector-associated transcription. When NFAT activity becomes uncoupled from the appropriate AP-1 partnership, it can instead promote inhibitory receptors and exhaustion-associated regulators. [15]

**Partner state matters more than abundance:** Martinez et al. engineered an NFAT1 variant unable to interact normally with AP-1. In activated mouse CD8+ cells, it increased inhibitory-receptor expression, reduced TCR signaling, and impaired protection in bacterial-infection and tumor experiments. The study supports AP-1-independent NFAT activity as a mechanism of dysfunction; it does not establish that all terminal Tex uniformly contain NFAT homodimers. NFAT can bind particular DNA elements as a monomer or dimer, depending on the element and cellular context. [15]

**TOX stabilizes an exhaustion-associated identity:** thymocyte selection-associated high-mobility-group box protein, or TOX, is induced by calcineurin and NFAT2 during persistent stimulation. Khan et al. showed in mice that TOX subsequently participates in a feed-forward program that becomes sustained independently of ongoing calcineurin activity. TOX therefore links an initiating signaling history to a more durable transcriptional and epigenetic state. [1]

**TOX is not merely a dysfunction marker:** in Khan et al.’s experiments, removing TOX prevented normal Tex formation while largely sparing conventional effector and memory formation. This makes TOX mechanistically important, not simply correlated with checkpoint expression. However, the exhaustion program also supports survival under persistent stimulation, so preventing its establishment can create a different problem: excessive differentiation or attrition of antigen-specific cells. [1][13]

**TCF-1 preserves progenitor capacity:** TCF-1, encoded by TCF7 in humans and Tcf7 in mice, is high in the self-renewing progenitor compartment and low or absent in terminal Tex. Its network favors survival and precursor-associated programs while opposing aspects of terminal effector differentiation. In chronic-LCMV P14 experiments, Tcf7 deletion allowed an initial response but failed to establish a durable Tex pool; enforced TCF-1 increased precursor-like cells and restrained more differentiated phenotypes. [9]

**T-bet and EOMES allocate different functions:** T-bet, encoded by TBX21, and EOMES, or eomesodermin, are related T-box transcription factors. T-bet often accompanies effector-like differentiation and can restrain PD-1 expression, whereas EOMES is prominent in several highly exhausted populations. Yet EOMES also supports survival and memory-related biology, including early exhausted precursors. Their ratio is therefore informative only when developmental stage and population definition are specified. [8]

**TCR strength modifies that balance:** Nayar et al.’s primary mouse study connected TCR-signal strength and interferon regulatory factor 4, or IRF4, to the T-bet:EOMES balance. Reduced IRF4 shifted cells toward EOMES, reduced the T-bet-positive/EOMES-negative precursor population, and impaired control of chronic LCMV. This supports a causal regulatory relationship in that model, while also showing why T-bet and EOMES should not be treated as interchangeable “good” and “bad” factors. [12]

**BATF has partner-dependent effects:** basic leucine zipper ATF-like transcription factor, or BATF, participates in AP-1-related regulatory complexes. Older human-HIV work associated BATF induction with dysfunction, whereas primary chronic-LCMV studies established a requirement for BATF in generating cytotoxic effector-like descendants from progenitors. Chen et al. showed that BATF maintained permissive chromatin near Tbx21 and Klf2, enabling the transition toward CX3CR1-positive effectors. [16]

**BATF’s apparent contradiction is biologically informative:** the same factor can support different outcomes when its partners, accessible binding sites, and developmental timing differ. BATF activity associated with effector enhancers is not equivalent to a high BATF transcript in a dysfunctional human population. The 2022 review of exhaustion chromatin [17] synthesizes evidence that BATF–IRF4 interactions can favor either exhaustion-associated circuitry or effector-associated chromatin opening, depending on context.

**PRDM1 links differentiation with restraint:** PRDM1 encodes B lymphocyte-induced maturation protein 1, usually called BLIMP-1. Its expression generally increases as cells leave stem-like states and acquire differentiated effector or exhausted programs. In the exhausted lineage, greater PRDM1 expression or accessibility accompanies differentiated subsets, while TCF-1-associated networks oppose Prdm1. Under continuous stimulation and hypoxia, BLIMP-1 also represses mitochondrial adaptation through PGC-1α, connecting differentiation to metabolic dysfunction. [2][18]

**NR4A reinforces the chronic-stimulation program:** the nuclear receptor subfamily 4 group A family comprises NR4A1, NR4A2, and NR4A3. These factors respond to TCR activation, but persistent or preferential use of their regulatory networks contributes to exhaustion. Seo et al. placed NFAT upstream of TOX, TOX2, and NR4A, and identified positive feedback between TOX and NR4A. In mouse chimeric antigen receptor T cells—CAR-T cells—loss of TOX/TOX2 reduced inhibitory receptors and increased cytokine expression, supporting a causal role for this network. [19]

**Human expression supports network conservation:** in human melanoma TIL analyses, high TOX and TOX2 transcripts accompanied high PDCD1, HAVCR2, and LAG3, which encode PD-1, TIM-3, and LAG-3. The PD-1-high/TIM-3-high subset also showed increased NR4A transcripts. These are human expression associations; the direct genetic demonstrations in the same body of work were performed in mouse CAR-TIL systems. [19]

**The transcriptional interpretation is developmental:** TCF-1 maintains a renewable reservoir; T-bet and BATF can support effector-like output; NFAT, TOX, NR4A, and PRDM1 participate in establishing or maintaining chronic-stimulation adaptations. A change in one factor is meaningful chiefly through the cell state and regulatory interactions it changes.

### Inhibitory receptors

**Co-expression is the characteristic surface pattern:** Tex commonly maintain several inhibitory receptors together, rather than displaying a single exhaustion-specific surface molecule. Important examples include PD-1, cytotoxic T-lymphocyte-associated protein 4 (CTLA-4), lymphocyte activation gene 3 (LAG-3), T-cell immunoglobulin and mucin-domain-containing protein 3 (TIM-3), and T-cell immunoreceptor with immunoglobulin and inhibitory-motif domains (TIGIT). CD160 and CD244/2B4 are additional context-dependent regulators; CD39 is an associated ectoenzyme rather than a conventional signaling receptor. [20]

| Molecule | Typical exhaustion-associated change | Specific functional role |
|---|---|---|
| PD-1/CD279 | Sustained expression; often higher in differentiated Tex | Restrains activation and costimulatory signaling |
| CTLA-4/CD152 | Increased in several dysfunctional tissue populations | Competes with CD28 for CD80/CD86 |
| LAG-3/CD223 | Persistent co-expression with other checkpoints | Restrains activation, proliferation, and cytokine output |
| TIM-3/HAVCR2 | Often enriched in differentiated Tex | Context-dependent regulation of signaling and survival |
| TIGIT | Increased alongside other checkpoints | Opposes CD226-associated costimulation |
| CD39/ENTPD1 | Enriched in several terminal-like populations | Degrades extracellular inflammatory nucleotides |
| CD160 | Frequently co-expressed in chronic viral responses | Marks context-dependent inhibitory circuitry |
| CD244/2B4 | Increased in several chronic-infection populations | Activating or inhibitory according to adaptor context |

Receptor-specific mechanisms are synthesized in the 2017 checkpoint review [6]; CD39 enrichment is supported by Gupta et al.’s primary study [21].

**PD-1 directly raises activation thresholds:** engagement by PD-L1 or PD-L2 activates intracellular inhibitory and switch motifs that recruit phosphatases, prominently SHP-2 and, in the reviewed signaling literature, SHP-1. These events restrain pathways including phosphoinositide 3-kinase/AKT and RAS signaling. PD-1 consequently influences cytokine production, proliferation, and metabolic activation; its effect is not simply a surface-label association. [6]

**CTLA-4 limits access to costimulation:** CTLA-4 competes with CD28 for CD80 and CD86 and can remove these ligands from antigen-presenting cells through trans-endocytosis. Antigen-presenting cells, or APCs, supply peptide–major histocompatibility complex and accessory signals required for T-cell activation. Because CTLA-4 also acts through regulatory T cells and APC ligand availability, a systemic CTLA-4-blockade effect should not automatically be assigned to an intrinsic change in exhausted CD8+ cells. [6]

**TIGIT alters a competitive receptor system:** TIGIT shares ligands such as CD155 and CD112 with the activating receptor CD226 and can interfere with effective CD226 signaling. Its functional meaning therefore depends on both TIGIT and the competing costimulatory machinery. Increasing TIGIT expression in a culture does not by itself establish that the complete physiological TIGIT pathway is operating: ligand presentation and the CD226 state also matter. [6]

**LAG-3 and TIM-3 are not interchangeable:** LAG-3 restrains activation and proliferative responses and can cooperate functionally with PD-1-associated inhibition. TIM-3 lacks the canonical intracellular inhibitory motif used by PD-1 and has ligand- and cellular-context-dependent effects. TIM-3 expression often identifies more differentiated exhausted cells, but a TIM-3-positive population may still contain substantial cytotoxic activity. These distinctions explain why counting receptors is informative but does not describe a uniform mechanism. [6]

**CD39 connects phenotype with extracellular metabolism:** CD39 hydrolyzes extracellular nucleotides and contributes to a less inflammatory extracellular environment. In Gupta et al.’s human study, mean CD39 positivity was **51% of HCV-specific CD8+ cells** and **31% of HIV-specific CD8+ cells**, exceeding the comparator virus-specific and healthy populations examined. In chronic LCMV, the CD39-high population was enriched for terminal-exhaustion-associated phenotype and function. [21]

**CD160 and 2B4 require contextual interpretation:** Buggert et al. linked PD-1/CD160/2B4 co-expression to poor polyfunctionality in human HIV-specific cells. Yet 2B4 can provide activating or inhibitory signals depending on receptor abundance and intracellular adaptor availability, including SLAM-associated protein. Thus, an increased receptor can be associated with dysfunction without having an invariant inhibitory effect in every T-cell state. [8][6]

**Persistent antigen need not mean maximal signaling:** a primary 2020 chronic-LCMV study found very limited ongoing TCR signaling in established Tex despite abundant antigen. PD-L1 blockade or introduction of peptide-pulsed target cells increased signaling measured with an Nr4a1 reporter. This distinguishes the antigenic history that establishes exhaustion from the signaling intensity observed at a later inhibited steady state. [20]

**The receptor-level judgment is functional:** sustained multireceptor expression supports an exhaustion classification, but ligand engagement, competing costimulation, and demonstrated cellular responses determine what those receptors actually do.

### Effector functions

**Functional loss is selective and hierarchical:** interleukin-2 (IL-2) production and strong proliferative responses are commonly impaired early; tumor necrosis factor (TNF) and interferon-γ (IFN-γ) responses may decline with further dysfunction. Cytotoxic impairment can involve reduced perforin production, defective granule delivery, reduced inducible degranulation, or poorer target-cell lysis. The sequence varies among models and subsets, rather than defining a mandatory timetable. [22]

**Polyfunctionality captures more than one output:** a polyfunctional T cell can perform several activities together, such as producing IFN-γ and TNF while degranulating. Exhaustion often narrows this combination even when one response remains detectable. Consequently, a sample that still produces IFN-γ can nevertheless have substantial exhaustion-associated impairment.

**A direct subset comparison is instructive:** Miller et al.’s primary B16-OVA mouse-tumor study showed that progenitor and terminal Tex distribute functions differently. The percentages below refer to the indicated exhausted subset, not to all tumor lymphocytes; functional assays generally used TILs isolated from tumors around days 19–21. [2]

| Readout | Progenitor Tex | Terminal Tex | Measurement basis |
|---|---:|---:|---|
| IFN-γ-positive cells | 21% | 44% | Six-hour peptide stimulation |
| IFN-γ/TNF double-positive cells | 13% | 2% | Six-hour peptide stimulation |
| IL-2-positive cells | 18% | 0% | PMA/ionomycin stimulation |
| Granzyme-B-positive cells | 12% | 80% | Ex-vivo staining |
| Ki-67-positive cells | 39% | 58% | Ex-vivo cycling marker |
| BrdU-positive cells | 20% | 43% | Twelve-hour in-vivo labeling |
| Annexin-V-positive cells | 41% | 72% | Ex-vivo apoptosis-associated staining |
| Further division after restimulation | Greater | Lower | Division-tracking assay |

**Immediate activity and durability separate:** terminal Tex in this model produced more IFN-γ and granzyme B and killed tumor targets more effectively than progenitors. Progenitors instead retained broader cytokine potential, greater capacity for additional divisions, and better survival. The apparent paradox disappears once immediate cytotoxic specialization is separated from the capacity to sustain a response over time. [2]

**Cycling does not guarantee population expansion:** the higher Ki-67 and BrdU measurements in terminal cells demonstrate ongoing division, not robust renewal. Greater apoptosis can offset that division, while the remaining cells possess little reserve for subsequent stimulation. This distinction is especially important when interpreting an intervention that increases a proliferation marker without increasing viable cell recovery or durable recall.

**Granzyme abundance is not equivalent to killing:** granzyme B and perforin must be appropriately packaged, polarized, and delivered to a target. Likewise, surface CD107a reports granule exocytosis but does not independently establish successful target-cell death. Buggert et al.’s human HIV study found monofunctional degranulation among poorly polyfunctional EOMES-high cells, reinforcing the need to distinguish release of granules from effective cytotoxic content and lysis. [8]

**Repeated stimulation reproduces selective dysfunction:** in Zhao et al.’s five-day OT-I culture, repeat-peptide cells produced IFN-γ after restimulation in **27 ± 3%** of cells and TNF in **4.8 ± 0.4%**, compared with **44 ± 4%** TNF-positive cells after single-peptide stimulation. These are means with standard errors from the study. Repeat-stimulated cells also contained elevated granzyme B but showed reduced target-cell killing and failed to increase degranulation further upon restimulation. [3]

**Residual functions remain biologically important:** Tex can retain tissue patrol, some killing, and production of chemokines such as MIP-1α, MIP-1β, and RANTES. These activities help explain why an exhausted population can still contribute to pathogen containment or tumor control. Exhaustion describes altered effectiveness and developmental potential, not a requirement that every canonical immune function disappear. [22]

**The functional judgment requires several assays:** cytokine breadth, actual target-cell lysis, viable expansion, survival, and recall answer complementary questions; none should stand alone as a complete measure of exhaustion.

### Metabolic activity

**Metabolic insufficiency is an interacting driver:** exhaustion-associated metabolism includes reduced capacity to support activation, impaired mitochondrial fitness, and adaptation to environmental constraints. A 2022 metabolic review summarizes evidence that reduced glycolysis and mitochondrial respiration can arise early in chronic infection, before overt functional failure. This temporal relationship argues that metabolic changes can help drive exhaustion rather than merely follow it. [23]

| Pathway or state | Exhaustion-associated change | Functional consequence |
|---|---|---|
| Glucose uptake and glycolysis | Reduced use or limited induction | Restricts activation and cytokine support |
| Mitochondrial respiration | Impaired respiratory fitness in several models | Reduces energetic and adaptive capacity |
| Fatty-acid oxidation | Favored by PD-1 ligation in reductionist cultures | Changes fuel use without guaranteeing fitness |
| PGC-1α-dependent adaptation | Repressed in stressed tumor T cells | Limits mitochondrial renewal and function |
| Mitophagy and membrane potential | Reduced quality control; depolarized mitochondria accumulate | Promotes terminal-like dysfunction |
| Reactive oxygen species | Excess mitochondrial production | Reinforces stress and NFAT-associated circuitry |
| Endoplasmic-reticulum stress | Increased stress signaling | Links nutrient and protein stress to dysfunction |

The table integrates [24][25], and the 2022 metabolic review [23].

**PD-1 changes metabolic programming:** Patsoukis et al. used purified human CD4+ T cells stimulated with CD3/CD28 beads carrying PD-L1 or control proteins. PD-1 ligation suppressed glycolysis and amino-acid-associated metabolic activation while promoting lipolysis and fatty-acid oxidation. Increased carnitine palmitoyltransferase 1A, or CPT1A, and adipose triglyceride lipase, or ATGL, accompanied this shift. This is receptor-specific human in-vitro evidence, providing mechanistic context rather than a direct metabolic census of CD8+ Tex in tissues. [24]

**Different checkpoints produce different fuel responses:** CTLA-4 also inhibited glycolysis in that experimental system but did not augment fatty-acid oxidation. Moreover, inhibiting either PI3K/AKT or MEK/ERK alone did not fully reproduce PD-1’s metabolic effect; combined inhibition more closely reproduced the CPT1A and fatty-acid-oxidation response. These results show why a generic “checkpoint-high metabolic state” is too imprecise. [24]

**Mitochondrial quality matters independently of quantity:** Yu et al. found accumulation of depolarized mitochondria in tumor-infiltrating CD8+ cells associated with reduced mitophagy, the selective clearance of damaged mitochondria. These cells displayed functional, transcriptional, and epigenetic features of terminal exhaustion. Pharmacologically enforcing accumulation of depolarized mitochondria promoted terminal-exhaustion-associated epigenetic reprogramming, supporting a causal contribution of mitochondrial dysfunction in the studied systems. [25]

**PGC-1α links transcription with mitochondrial adaptation:** peroxisome proliferator-activated receptor-γ coactivator 1α, abbreviated PGC-1α, supports mitochondrial adaptation and fitness. Scharping et al. showed that continuous stimulation promoted BLIMP-1-mediated repression of PGC-1α-dependent reprogramming. When continuous stimulation occurred under hypoxia, this impaired adaptation contributed to mitochondrial stress and rapid exhaustion-consistent dysfunction. [18]

**Combined stress can change the outcome:** in Scharping et al.’s antigen-specific in-vitro experiments, continuous stimulation alone or hypoxia alone could still generate functional effectors, whereas their combination rapidly produced dysfunction consistent with exhaustion. The hypoxic antigen-specific assay used **1.5% oxygen**. Mitochondrial stress increased reactive oxygen species, or ROS, and NFAT activity, linking an environmental condition back to the transcriptional circuitry described above. [18]

**Metabolism can reinforce durable programming:** excessive mitochondrial ROS and disturbed calcium handling can influence NFAT-dependent transcription, while mitochondrial dysfunction can alter chromatin and DNA-methylation programs. These relationships create feedback: chronic stimulation and inhibitory signaling impair metabolic adaptation, and metabolic stress in turn helps stabilize dysfunctional regulatory states. Yu et al.’s mitochondrial perturbations and Scharping et al.’s hypoxia/ROS experiments support particular links in this feedback rather than a single universally sufficient pathway. [25][18]

**Fatty-acid use is not exhaustion-specific:** memory-like cells, progenitor Tex, and stressed cells may all use fatty-acid-associated pathways for different reasons. A transcriptomic enrichment for fatty-acid oxidation therefore does not independently demonstrate either exhaustion or healthy mitochondrial function. Jung et al.’s engineered PRDM1-knockout CAR-T cells, for example, combined fatty-acid-oxidation and tricarboxylic-acid-cycle signatures with early-memory features; the authors interpreted this as a shift toward an early-memory fate. [26]

**The metabolic judgment is stage-specific:** evaluate actual fuel use, respiration, mitochondrial quality, and tissue stress together; a pathway signature or receptor-induced fuel shift alone does not define the metabolic state of Tex.

**Additional documented evidence**

**Operational definition and scope**

T-cell exhaustion is a context-dependent state of T-cell dysfunction arising during many chronic infections and cancer. It combines poor effector function, sustained inhibitory-receptor expression, and a transcriptional state distinct from functional effector or memory T cells; one marker is therefore insufficient [38]. Prolonged antigen exposure and chronic inflammation can “downtune” T cells to limit tissue damage, indicating a specialized differentiation program [43]. Exhaustion impairs control of infection or tumors, making its molecular definition relevant to mechanism and therapeutic research [38].

The evidence is chiefly animal and CD8-focused: indexed contexts include animals, bacterial infection, and CD8-positive lymphocytes [38]. Chronic infection and cancer are core contexts, not a closed biological universe. In chronic infection and the tumor microenvironment, sustained inhibitory-receptor expression may reflect specialized differentiation [43]. A 2021 expression-atlas resource reported cancer in 19 of 45 represented human disease states and in more than 80% of highly represented diseases in its bulk atlas; these figures describe evidence availability, not Tex-specific biology [39].

**Transcription-factor dimension**

Transcription-factor binding to cognate DNA helps determine gene-regulatory-network connectivity and expression, while post-translational modification and co-regulator binding can alter factor activity or localization [41]. In-vitro binding assays can quantify interactions but may miss chromatin and cooperative context; in-vivo assays provide biological context but may not distinguish direct from indirect binding. Combined evidence is therefore preferable [41]. In a CD8 CAR-T tumor model, TOX and TOX2 were highly expressed in exhausted CAR TILs, and TOX cooperated with NR4A. The experiment used 5 × 10^5 B16-hCD19 tumor cells in C57BL/6 mice, transferred 1.5 × 10^6 CAR T cells 12 days later, isolated CAR TILs every 4 days, and analyzed them on day 24 alongside in-vitro CAR T cells [40]. This supports transcription-factor readouts, but within a specified murine tumor context.

**Inhibitory-receptor dimension**

Sustained inhibitory-receptor expression is a defining Tex feature; multiple receptors are reported as coregulated during chronic viral infection [38]. However, naïve, effector, and memory CD8 T-cell subsets inherently differ in receptor expression, and activation strongly upregulates receptors [43]. Receptor abundance should therefore be interpreted with differentiation, activation, antigen history, function, and tissue context. Checkpoint blockade and receptor biomarkers make this dimension therapeutically relevant, but receptor positivity alone does not establish exhaustion [43].

The cited records used here predate 1 July 2023; examples include publications dated 18 May 2011 and 19 November 2021 [2,7].

Effector function is multidimensional, not a single Tex marker. A 9-Nov-2020 primary-human assay separately measured proliferation, cytotoxicity/target-cell killing and cytokine production; shortly after stimulation, proliferation and cytotoxicity were inversely related in heterogeneous cells, but the basis was unresolved and only two CAR/TCRs were tested [44]. Outputs may depend on donors and culture conditions, despite general consistency across donors and IL-15/IL-21; phenotype should therefore be tracked with function, not used alone to diagnose Tex [44]. A 2010 citation compared IL-7+IL-15 with IL-2 in ex-vivo mammary-carcinoma T-cell expansion [52].

Inhibitory receptors and negative feedback are Tex-relevant: chronic antigen recognition drives heterogeneous exhaustion; TCR-signal strength shapes exhausted differentiation and therapy response; changing feedback can promote single-agent resistance. Receptor blockade can increase immune activation and tumour clearance [46]. Infection and cancer therefore require separate context labels.

Human lung-tumour data show why tissue matters: deficient migration factors and dense matrix restrict entry into tumour islets, while chemokine-rich loose stroma favors accumulation; T cells are often stromal and move parallel to the tumour–stroma boundary [53]. Purified T cells added to tumour slices behaved like resident TIL [53]. Glucose culture drives glycolysis/lactate; tumours impose carbohydrate/amino-acid competition and mitochondrial changes, while cytokines alter T-cell subtype and adhesion receptors. Killing alone is insufficient: persistence, circulation, homing and in-vivo amplification need testing [52]. Model qualification must match cell type, platform, throughput and endpoint [55].

General model evidence suggests simplified cultures may miss native organization and cell–matrix mechanics [56]; isolated systems aid mechanism but can be far from physiology [54]. CD8-specific and mixed CD4/CD8 work should not be generalized without qualification [52]. Human-tissue models may translate better but are scarce; exosome and model papers here provide context, not Tex mechanisms [45][47][48][49][50][51][58]. All evidence here is pre-1 July 2023, with explicit records spanning 2004–30 June 2023 [57][46]; later records were excluded.

Date screen: pre-July-2023 records are date-eligible [61][65][69][70][72][75][77][78][79][80][81][82][88]; records from 6 July 2023 onward are excluded [59][60][62][63][64][66][67][68][74][76][83][84][85][86][87][89][90][91]. [71] has only a 17 January 2023 update; [73] has no page publication date and reports only normal immune markers, not Tex endpoints.

Human HCV evidence links chronic infection and cancer to killer-T-cell dysfunction: prolonged stimulation leaves incomplete recovery, whereas shorter stimulation can yield functional memory; after cure, epigenetic scars and efficacy-linked changes persist despite partial molecular normalization [61]. This separates exhaustion from transient suppression and ordinary memory. The evidence is CD8-focused: CD8 cells kill infected or tumour cells and bind MHC-I, whereas CD4 helpers coordinate cytotoxic T cells, B cells and macrophages and bind MHC-II [61][71].

T-bet/Eomes are T-box factors for immune development and cytolysis; human flow cytometry measured them in CD4+, CD8+, γδ, iNKT, NK, B and dendritic cells, not defined Tex states [70]. NFAT1/2/4 support activation; NFATc1/c2 support effector differentiation, NFATc1 proliferation and Th2 cytokines, NFAT4 T-cell survival, and NFAT complexes tolerance [72]. ExTRI is general, not Tex-specific: it preserves direct TF–target, cell/tissue and evidence context, with annotations for about 100 TFs and about 900 broader TFs [82].

Exhaustion is dysfunction in chronic infection/cancer, with poor effector function, sustained inhibitory receptors, and a transcriptional state distinct from effector/memory cells [92]. Breast-tumor PD-1/CTLA-4/LAG-3/TIM-3 co-expression is tissue/subset-specific, especially among CD8⁺ cells [92].

**Tex states and contextual boundaries**

Tex are not diagnosed by PD‑1 alone: chronic-infection and cancer Tex commonly co-express PD‑1, CTLA‑4, TIM‑3, LAG‑3, TIGIT, CD244/2B4 and CD160; single receptors also mark activated effectors [93,94]. Progenitor Tex are typically PD‑1^hiTIM‑3^loTCF1^+, whereas terminal Tex are PD‑1^hiTIM‑3^hiTCF1^− and expand poorly [93]. Transcription-factor candidates include T-bet/EOMES, FOXO1/FOXP1, PRDM1, NFAT, BATF, IRF4, NR4A, TOX and VHL; persistent NFAT without AP‑1 induces NR4A/TOX and supports receptor induction and Tex survival. PD‑1 ligation recruits SHP2, suppresses TCR/CD28 and PI3K–AKT–mTOR signaling, and limits IL‑2 and proliferation; blockade can restore antiviral function and reduce viral load [94].

Function declines hierarchically: IL‑2 first, TNF and other cytokines later, while IFN‑γ, β‑chemokines and sometimes cytotoxicity persist [94]. Tex are hypofunctional, not inert: cytokines, granzymes, proliferation and partial pathogen or tumor control remain possible; terminal cells have limited recall expansion, whereas TCF1+ progenitors self-renew [93]. PD‑1-associated bioenergetic and mitochondrial dysfunction are reported; IL‑12 or mitochondrial targeting restored HBV-specific CD8+ antiviral function [94]. Core programmes span chronic infection and tumors in mice and humans; viral Tex have stronger type-I-interferon signaling, whereas TILs face metabolic, suppressive cytokine/chemokine and ionic constraints, and some are dysfunctional rather than exhausted [93]. Evidence is CD8-heavy, although CD4+ Tex are also reported [94]. Exhaustion follows productive activation plus persistent antigen, unlike anergy, senescence (KLRG1/CD57^hi), memory without antigen, or suppression/ignorance; it becomes distinct from acute effector differentiation after approximately 2 weeks [93,94].

T-cell exhaustion is chronic-antigen dysfunction distinct from effector/memory states: in chronic infection or cancer, sustained TCR signaling accompanies reduced proliferation/effector function, altered gene expression/metabolism and sustained inhibitory receptors; studying it informs immunotherapy [97][98][99]. In CD8+ Tex, TCF-1 maintains stemness and promotes Eomes/c-Myc/Bcl-2; BATF and NFATc1 promote PD-1/metabolic impairment, although BATF–IRF4 can counter exhaustion in tumor-infiltrating CAR T cells [95][98]. High PRDM1/BLIMP1 is associated with terminal differentiation, TCF7 repression and loss of stemness; NR4A3 rises after prolonged tumor-antigen exposure and drives NFAT-dependent dysfunction, while TOX/TOX2 cooperate with NR4A to impose exhaustion [98][99]. PRDM1-deficient CAR T cells lost function despite receptor downregulation [98].

Tex sustain/co-express graded PD-1, CTLA-4, TIM-3, LAG-3, TIGIT, 2B4/CD244 and VISTA; co-expression usually tracks severity [95][99]. PD-1–PD-L1 recruits SHP2 and reduces NF-κB/AP-1/NFAT activity; TIGIT competes with CD226 and LAG-3 disrupts LCK signaling [95]. Proliferation, killing and IL-2 decline before TNF/cytotoxicity; terminal Tex may lose IFN-γ/β-chemokines and degranulation [95][96]. Nutrient/oxygen-poor tumors add metabolic plasticity, energy shortage and mitochondrial dysregulation [95].

LCMV (mouse), HCV/HIV (human) and cancer are documented contexts [99]. Evidence is mainly CD8+; limited CD4+ data include Nr4a1 effects on anergy genes and IL-2/IFN-γ, limiting generalization [99]. Anergy, senescence, memory and transient activation are not directly compared in these sources [96].

The transcriptional axis of Tex is state- and time-dependent, not a one-marker diagnosis. In chronic LCMV infection in mice and HCV infection in humans, TOX supports TCF-1+ progenitor survival and is linked to inhibitory-receptor expression and exhaustion-specific epigenetic remodeling; TOX/TOX2 and NR4A-family factors participate with NFAT, while PRDM1 activated the TOX promoter in a human Jurkat reporter assay [100]. Chronic CMV, EBV and HIV infection upregulated TOX, whereas acute influenza infection upregulated TCF-1, illustrating context dependence [100].

A murine P14 CD8+ model sampled spleen cells in LCMV Cl13 infection and CT26 tumor challenge. TCF-1+ Tex precursors repressed the Teff-like developmental path: Tcf7 deletion reduced the durable Tex pool, whereas enforced TCF-1 repressed KLRG1+CD39+ and Tim-3+CD39+ Teff-like cells [101]. At day 8 of chronic infection, TCF-1+ precursors expressed more Eomes, slightly less T-bet, and the lowest T-bet:Eomes ratio; TCF-1 was upstream of Eomes but had minimal effect on T-bet at that time [101]. NFATC1 was implicated in exhaustion and predicted to be TCF-1-regulated in early precursors; BATF correlated positively with TCF-1 and was predicted downstream of TCF-1, so these latter relationships are not direct perturbational evidence [101].

TOX is informative but not exhaustion-specific: approximately 5–10% of CD8+ lymphocytes expressed TOX in the 2023 report, and TOX was also detected in activated, memory, functional and CD4/Tfh populations [100]. Thus receptor and functional context remains necessary: persistent-antigen CD8+ Tex showed increased inhibitory receptors, lower perforin, granzyme, IFN-γ and TNF-β, IL-2 downregulation and reduced proliferation [100]. After HCV cure, 77.1% of exhaustion-related epigenetic scars persisted and 18.2% decreased during long-term follow-up [100]. The murine functional assay used 5 h ex vivo GP33–41 stimulation and measured TNF, IFN-γ, granzyme B and CD107a [101].

Chronic antigen and poor CD4 help produce programmed Tex; cancer adds metabolite/cell signals [105,106]. Tex coexpresses PD-1, CTLA4, TIM-3, LAG-3, TIGIT, 2B4 and SLAMF6, but receptors alone do not diagnose exhaustion [102]. Function and recall decline; TCF1+ progenitors retain cytokines/proliferation, while metabolism and epigenetics change. NFAT–IRF4–BATF represses TCF1; TOX/NR4A reinforce CD8 Tex [103].

Exhaustion is a chronic-infection/cancer state induced by persistent antigen/TCR stimulation—not receptor positivity alone: versus effectors, cells are hyporesponsive/hypofunctional, express PD-1/TIM-3/LAG-3/CTLA-4/TIGIT, and acquire TOX/TCF-1/NFAT programmes; cytokine/granzyme output and pathogen/tumour control may remain [105]. In chronic LCMV, CD8 cells are deleted or persist with lost cytotoxicity/cytokines; PD-1 blockade restores function, and TCF1+Tim3− cells self-renew into TCF1−Tim3+ progeny [104]. T-bet^Hi/Eomes^Low cells are relatively functional, whereas T-bet^Low/Eomes^Hi cells are PD-1^Hi and dysfunctional [104]. NFAT without AP-1 induces NR4A/TOX; BATF/IRF4 contribute, but Tex states form a continuum [105]. HCV/HIV epigenetic features persist after cure [106]; viral Tex has stronger type-I-interferon signalling, CD4 help can rescue exhausted CD8 cells, and CD8-heavy evidence limits CD4 generalization [104].

Persistent antigen/inflammation after the effector phase drives hierarchical loss of IL-2, polyfunctionality, proliferation, then IFN-γ, TNF, chemokines and degranulation; inhibitory-receptor diversity rises [107]. Tex retain residual function [107]. In CD8+ models, progenitor Tex persist and generate more cytotoxic, shorter-lived terminal Tex [108]. CD4+ Tex share a core program but differ in receptors, transcription factors and cytokines [107].

Chronic infection causes dysfunction; IRs persist [109].

Tex is progressive hypofunction from persistent antigen in chronic infection or cancer: inhibitory receptors rise, cytokines/cytotoxicity fall, yet some pathogen or tumor control remains. [110][111] Persistent TCR–Ca2+ signaling leaves NFAT unpaired with AP-1, inducing TOX/NR4A; PD-1–SHP-2 restrains PI3K–Akt–mTOR, while TCF-1 supports progenitor Tex. Tex metabolism shows reduced glycolysis/GLUT1, mitochondrial fitness and oxidative phosphorylation, ER stress/mtROS, and sensitivity to hypoxia, low pH and nutrient scarcity. [110] CD8+ LCMV-Cl13 dysfunction appears by 2 weeks; CD4 help resolves infection in 2–3 months, but its absence sustains exhaustion. Teff and Tex may both be cytolytic; TCF-1+ populations can share transcripts yet differ in chromatin, so no single marker defines Tex. [111][112]

Tex: persistent antigen in infection/tumor causes hypofunction; inhibitory receptors rise, IL-2/cytotoxicity/cytokines/proliferation fall; TOX, TCF1, NFAT, NR4A, BATF drive [113].

Chronic infection shows a trajectory: virus-specific CD8+ T cells contain T-bet^hi cells that proliferate under persistent antigen and yield Eomes^hi terminal progeny; both support viral control [116]. In HCV/HIV and LCMV, CD39^high cells co-express PD-1, CD244/2B4 and LAG3 and make less IFN-γ/TNF-α; CD39^high cells are absent after acute LCMV and in functional memory, though activation can transiently raise CD39 [114]. TOX is low/transient in acute but persistently high with chronic antigen, promoting chromatin remodeling, inhibitory receptors, reduced cytokines and persistence; NFAT/calcineurin induces TOX and NR4A, while TCF1 marks progenitor-like cells. The program is also reported in tumor CD8+ cells/human cancers [115]. ATP was assayed in six HCV subjects (no result); CD39 alone confounds CD4+ Tregs, so CD8 findings need validation [114].

Under persistent antigen, CD8 Tex lose proliferation and IFN-γ/TNF-α/IL-2 while PD-1/LAG-3 rise; blockade can restore function [132,134]. TCF-1 marks progenitor persistence; NFAT/TOX/NR4A enforce exhaustion, while BATF–IRF4 regulate T-bet:EOMES [135,134].

Tex: Ag→dysfunction; PD-1/TIM-3; NFAT monomer→Tex [137,139].

Exhaustion follows persistent antigen/inflammation in chronic HIV, HBV, HCV, LCMV or cancer: antigen-specific cells lose function and adopt a distinct state [118]. It differs from transient activation/memory, anergy (excess TCR stimulation plus inhibitory signaling), and senescence (KLRG1/CD57-high, unlike PD-1-high Tex) [118]. Tex involves T-bet/EOMES, PRDM1, NFAT and BATF programs; sustained PD-1 with CTLA-4, TIM-3, 2B4, LAG-3/CD160; hierarchical IL-2 then TNF loss; and PD-1–AKT/mTOR suppression, glycolysis-to-FAO shift, mitochondrial depolarization, low biogenesis and ROS-linked dysfunction [140,144].

T-cell exhaustion/Tex is heterogeneous under persistent antigen in chronic infection/cancer: PD-1/CTLA-4/TIM-3/LAG-3/TIGIT rise; IFN-γ/TNF-α, cytotoxicity and TCF-1 fall; NFAT→TOX/NR4A rewires chromatin; mitochondrial/ROS dysfunction [119]

T-cell exhaustion is persistent-antigen–driven CD8+ hyporesponsiveness with PD-1/Tim-3/2B4/Lag-3 and declining function [150,152]. NFAT→NR4A/TOX reinforces the program; healthy-donor expansion remained functional, not Tex [152,153].

Tex: chronic infection/cancer CD8+ dysfunction; PD-1/LAG3/TIGIT, altered TFs/metabolism; NFAT2→TOX programs it [154,155].

Tex: chronic-antigen hypofunction; PD-1/receptors and TFs change [121]. Partial Tex: repeated 5–7 d, ≤30 d [122].

Persistent antigen in chronic infection/cancer yields hyporesponsive Tex, distinct from anergy; Tex lose effector function, gain inhibitory receptors; TCF1 marks progenitors [123].

Exhaustion requires phenotype plus function and state [124].

Persistent antigen/inflammation in chronic infection/cancer drives exhaustion: IL‑2, polyfunctionality and proliferation fall early, then IFN‑γ/TNF/chemokines and degranulation; PD‑1, LAG3, 2B4, CD160 and TIGIT rise [126]. TCF1⁺ Tex retain effectors [125].

T-cell exhaustion is persistent-antigen/TCR dysfunction: Tex lose proliferation/effector output and gain inhibitory receptors with transcriptional/metabolic change; PD-1 alone is insufficient [128][130]. Human CD8+/CD4+ cultures: 14 d CD3/CD28+IL-2 maintained LAG-3; PD-1 varied; cytokines fell; 3 d stimulation+11 d rest restored function [127]. Chronic infection/cancer are contexts; species/subsets differ [128][130]. Markers: PD-1/TIM-3/LAG-3, TOX/NR4A, altered glycolysis/OXPHOS [130][131]. Cancer exosomes are context, not Tex evidence [129].

RA TNF-exposed CD4+ T cells: calcium/NFAT↓, Ras/ERK spared [132]. PRDM1/BLIMP1 knockdown in human T cells: memory↑, effector↓; PD-1↑/TIM-3↓ at day 25 [133].

Tex: PD-1/LAG3 rise; cytokines fall; TOX programs Tex [134].

Exhaustion/Tex: chronic infection/cancer→IR↑; effector/metabolic dysfunction; TCF-1+→TOX+ terminal states [135][182–185].

CD8 Tex: chronic antigen causes dysfunction; PD-1 high.[136]

CD8: LCMV (days 8–30) and MC38/B16 tumors identify Slamf6+/CXCR5+ progenitors (proliferative/polyfunctional) and Tim-3+/PD-1hi Tex (cytotoxic, less proliferative) [137]. TOX/NR4A/TCF1/NFAT qualify [189,191,192]; CD4 was depleted [137].

Tex: chronic Ag→hyporesponsive, checkpoint-rich transcriptional state; PD‑1 alone ≠ exhaustion; CD8↓, CD4 intact [138].

Tex: antigen→dysfunction; IRs↑; TCF1+ self-renew [139]

T-cell exhaustion is persistent-antigen dysfunction: cells persist but lose cytokine production/proliferation, sustain PD-1, and acquire a transcriptional state distinct from effector/memory cells [140]. Mouse LCMV; human HIV/HBV/HCV and cancer show TCF1/TCF7+ precursor Tex; TOX/NR4A associate with Tex, BLIMP1 with terminal differentiation [140]. PD-1, LAG-3, TIGIT and TIM-3 co-occur; blockade can restore function, but terminal cells respond poorly [140].

Persistent antigen impairs Tex; CD4 help redirects fate[141]

Tex: dysfunction, markers, cause; PD-1 insufficient [142].

Chronic infection/cancer: persistent-antigen PD-1/LAG-3+ Tex; cytokine↓, cytolysis/expansion retained [202,203]

Persistent-antigen Tex are heterogeneous: TCF1+ progenitors self-renew into terminal cells; TOX/PD1/LAG3 mark dysfunction; phenotype/function can uncouple [143]. Cancer TILs lose cytokines/cytotoxicity; reactive/bystander differ [143].

Tex: persistent dysfunction; PD-1/LAG-3 coexpress [144].

Chronic infection: CD8⁺ Tex dysfunction; PD-1 high [145].

T-cell exhaustion: persistent Ag→dysfunction; receptors [146]

Tex: persistent antigen→dysfunction; PD-1/TIM-3↑ [214,216].

Persistent antigen in chronic infection and cancer drives CD8+ exhaustion: multiple inhibitory receptors rise, cytotoxicity and re-expansion fall, while a TOX-dependent epigenetic program supports persistence [147]. TCF-1+PD-1+ progenitor Tex self-renew and generate transitional/terminal progeny; TCF-1− cells can be migratory (CX3CR1+) or resident (CD101+), and bifurcation is also reported [148]. TOX overexpression increases PD-1 and lowers TNF/IFN-γ; deletion improves effector function but worsens immunopathology [222,223].

T-cell exhaustion follows chronic antigen exposure.[149]

Chronic HBV CD8+ Tex show dysfunction and PD-1 [150].

Tex TCF1+;PD-1/TOX/CD39↑;IFNγ/TNF↓;mito↓/ROS↑[151][152][153]

PD-1 blockade restores Tex function in chronic LCMV [154].

Tex: persistent antigen/TCR→dysfunction+receptors [245,246].

T-cell exhaustion: chronic antigen causes NFAT homomers, not NFAT:AP-1, induces PD-1/TIM-3/LAG-3 and lowers CD8 effector function; NFAT senses glucose, ROS and lactate [155].

Chronic infection: Tex lose cytokines/proliferation, gain inhibitory receptors, and show metabolic dysfunction [256,258]

Tex follows chronic antigen exposure with hypofunction.[156]

Tex: persistent antigen → dysfunction; PD-1↑, IL-2↓ [157].

Persistent antigen limits NFAT entry, lowering IFNγ [158].

Tex: persistent antigen, hypofunction, IRs/metabolism [159].

Tex: chronic antigen; dysfunction; NFAT/PD-1; noninert [160].

Persistent antigen recognition—not tumor residence—marks CD8⁺ Tex: PD-1/LAG-3/Tim-3 rise, cytokine production falls, and exhaustion-linked chromatin differs; acute Nr4a/receptor induction can be activation [162]. PD-1 blockade restored cytokines and killing [163]; Eμ-Tcl1 CLL showed impaired synapses and no profound metabolic-regulator difference [161].

Exhaustion—persistent antigen; PD-1↑, function↓.[164]

HCV: early OXPHOS dysregulation precedes exhaustion [165].

Chronic-HCV CD8 Tex: multi-IR+, CD127low, poor prolif. [166]

Chronic antigen drives Tex; iRs alone do not define it [167].

Exhaustion follows persistent antigen and dysfunction [168].

Tex combines chronic antigen, dysfunction, and PD-1 [169]

BATF sustains CD8 function[322,323]; PD-1 suppresses TCR[170].

Tex: persistent antigen, hypofunction, IRs, distinct state [171].

Capacity conflict: 60 chars cannot cover all assigned facts

Persistent antigen drives Tex dysfunction and PD-1 gain [172].

Persistent antigen drives progressive Tex dysfunction [173].

Inhibitory receptors are not Tex-specific [174].

Chronic antigen exposure sustains PD-1 through NFATc1 [175].

T-cell exhaustion: persistent antigen→dysfunction; PD-1/LAG-3/TIM-3; TCF1+→terminal Tex; NFAT→BATF/TOX/NR4A [344,345].

Exhaustion: chronic-infection/cancer CD8 hyporesponsiveness, poor function, inhibitory receptors, distinct transcriptional program; residual function [176][180]. NFAT–AP-1 imbalance induces Tex; NR4A loss restores function [177][178][179].

Exhaustion progresses; PD-1 alone is nonspecific.[181]

Exhaustion: antigen→hypofunction; PD-1↑, cytokines↓ [182]

HNSCC terminal Tex: higher TIM-3, CTLA-4, TIGIT [183].

Persistent antigen drives altered Tex differentiation [184].

Persistent antigen drives Tex: PD-1/TIM-3/CTLA-4/CD244 rise as IL-2/proliferation/cytotoxicity fall [363,364].

T-cell exhaustion = persistent Ag + effector loss + inhibitory receptors + distinct gene state≠effector/memory/anergy [185]. Chronic infection/tumor: TCF‑1 marks TPEX; NFAT/AP‑1 imbalance induces TOX/receptors; NR4A cooperates with TOX [186]. PRDM1/BLIMP1 changes PD‑1/TIM‑3; CD4/CD8 differ [187].

Chronic LCMV yields exhausted, not effector CD8+ cells [188].

Chronic-infection Tex show dysfunction, inhibitory receptors and a distinct TF state; CD4+ Tex have altered costimulation/cell cycle, with CD4/CD8 repertoires differing [189]. TCF-1 marks progenitor Tex but falls in terminal Tex; NFAT2 induces TOX, which programs Tex chromatin [373,374]. OT-I CD8+ cells: 5-day repeat culture, ~9-fold expansion, receptor co-expression and functional/TF/chromatin changes [190].

T-cell exhaustion=chronic-Ag dysfunction; effectors↓, PD1/PDL1/CTLA4/LAG3/TIM3/TIGIT↑, distinct TF/epigenetic state [376,379]. Tex hetero: TCF1+ progenitor/CX3CR1+ effector/terminal; BATF/IRF4,NFAT,TOX/NR4A shape infection/cancer [377,378].

CD8+ Tex: PD-1↑; Eomes↑/T-bet↓; TOX→chromatin [380,381].

Persistent TCR stimulation drives CD8+ Tex dysfunction [191].

CD8+ Tex: PD-1/Tim-3, reduced effectors [193]; TCF-1+ progenitor vs TCF-1− terminal; TOX/NR4A program exhaustion [194].

Chronic infection yields hierarchical Tex dysfunction [195].

CHB Tex: Tim-3↑; IFN-γ/TNF-α↓; blockade partly restores[196]

Tex: chronic antigen, PD-1, and lost function [394,395].

T-cell exhaustion is chronic-stimulation dysfunction [198].

Tex: PD-1/Tim-3 coexpression; cytokines fall [401,402].

HCV Tex: ongoing antigen, PD-1/2B4; poor proliferation [200]

Receptor positivity alone does not prove exhaustion [201].

Mouse models link T-cell exhaustion to dysfunction, polyfunctionality, and signaling/metabolic/transcriptional circuits. In clone-13 infection, TOX regulates cytokines, TFs, and inhibitory receptors and maintains antigen-specific CD8 pools; PD-1/LAG-3 perturbations alter persistence [202].

Tex follows chronic antigen in infection/cancer: ↓cytokines, cytotoxicity/proliferation; ↑PD-1/TIGIT; distinct transcriptional/epigenetic state [205]. TCF-1 marks progenitors; NFAT→TOX, NR4A, BATF, PRDM1 shape CD8 Tex [203][204][205].

Tex: persistent-antigen dysfunction [206]; scope cannot fit.

Tex (mostly CD8) follows chronic antigen in infection/cancer: cytokines, cytotoxicity and proliferation decline; inhibitory receptors persist, transcriptional/epigenetic programs diverge, but receptors alone may reflect activation/differentiation [209]. iRs: PD-1, CTLA-4, TIM-3, LAG-3, BTLA, 2B4, CD160, TIGIT/CD244; TIM-3–CEACAM-1 and ITIM/ITSM signaling show context dependence [207][208]. LCMV/HIV: receptors persist; TNF/IL-2 fall; IFN later [207][208]. TCF-1 marks self-renewing pTex; TOX/NR4A shape terminal states; pTex favors FAO/OXPHOS, terminal Tex is metabolically insufficient [208][209].

Persistent antigen and inflammation can drive CD8+ Tex in chronic LCMV, hepatitis B/C, HIV-1 and tumors. Tex arises from CD127+ memory precursors, not senescent KLRG-1+ effectors; memory potential is highly compromised by ~2 weeks and essentially ablated by day 30 of chronic infection [210]. Sustained/co-expressed PD-1, 2B4, CD160, KLRG1, LAG-3, TIGIT and Tim-3 accompany dysfunction; blockade restores only some functions [210]. Partnerless NFAT induces Pdcd1, Lag-3 and Tim-3; TCF-1 maintains progenitor capacity, while T-bet/Eomes, BATF, IRF4, PRDM1/Blimp-1 and TOX are context-dependent [210]. Function declines hierarchically (IL-2→TNF/cytotoxicity→IFN-γ), although degranulation, chemokines or survival may persist [210].

Tex:persistentAg→IL2/TNF/IFNγ↓,lysis↓;PD1/CTLA4/TIM3↑[211]

Chronic infection and cancer sustain T-cell exhaustion.[212]

CD8-heavy; CD4 helps CD8 Tex; TFs drive Tex [427,430].

Early CD8 cells remain plastic; later become fixed [213].

T-cell exhaustion: chronic antigen, PD-1, dysfunction [214]

Persistent antigen creates Tex: PD-1/LAG-3/Tim-3 rise; cytokine, lytic, proliferative and glycolytic outputs fall [216].

Capacity conflict: 60 chars cannot cover all evidence.

Tex: chronic infection/cancer; persistent TCR signaling causes low cytokines/cytolysis and high PD-1/TIM-3/LAG-3 [444,446]. NFAT induces TOX/NR4A; TCF1 marks stem-like CD8+ cells; BATF rises after Tox/NR4A loss [218]. CD8+ Tex: dysfunctional mitochondria, low OXPHOS and glycolytic dependence; PGC1α/IL-12 rescue function [444,448]. CD4 transfer unclear [219].

Chronic antigen raises PD-1 and exhausts CD8 T cells [220].

T-cell exhaustion is context-dependent; markers can dissociate [221].

NFAT/BATF may prime Tex; TOX/NR4A maintain it [455,456].

CD8 Tex: progenitors retain polyfunctionality and become terminal Tex [223]; rapamycin cells increase OXPHOS [222].

CD8 exhaustion: TOX/PD-1/TIM-3; CD4 scope limited [224].

LCMV clone-13: IL-2→TNFα→IFNγ loss marks dysfunction [225].

T-cell states vary by tissue, infection, and subset [226].

Persistent antigen sustains CD8+ Tex dysfunction [228].

LCMV/HCV/HBV/HIV: CD8⁺ Tex dysfunction—poor proliferation/killing/cytokine output; CD4 help rescues [230]. T-bet/Eomes→Pdcd1 [231]; BATF3→CD8⁺ memory [232]; mouse/human vary [229].

Chronic LCMV evidence is CD8-specific: PD-1+TCF1+ resource cells self-renew and become terminal Tex; stem-like cells show Tcf7/Id3 accessibility, whereas Tex show Prdm1/Id2 and ETS/RUNX motifs and differ from acute programs [233]. Human basal-cell-carcinoma data link CD8 exhaustion with CD4 Tfh development, but do not make CD4 and CD8 exhaustion interchangeable [233]. TFs regulate gene expression [42].

NFAT is an activity/localization state, not abundance alone: Ca²⁺/calcineurin drives nuclear entry and partners shape tolerance versus effector transcription [235]. In antigen-experienced CD8⁺ cells, export half-life is ~20 min; NFAT memory preserves Egr2, not Ifng, while tumor tolerance links to lower Ifng/Tnfa and higher Pdcd1 [235]. In CD4⁺ cells, NFATc1/c2 are high in memory, low in naïve, with distinct IL-2 dependence [234]. CCR5/NFAT effects are context-dependent [236].

NFAT controls T-cell transcription and differentiation [237].

BHLHE40 regulates a Tex differentiation checkpoint [238].

Tex:TCF1/TOX/Eomes/T-bet/Helios;NFAT/BATF/NR4A[510–515]

PD‑1/TIGIT link cancer Tex; CD4 sustains CD8 function; PRDM1 regulates receptors; motifs need validation [516,518,521].

NFAT→TOX/NR4A drives CD8⁺ Tex; TCF1 preserves stemness; BATF/IRF4 oppose exhaustion; NR4A3 reshapes CD8⁺ fate [217][120]

D8: TCF-1+ precursors had higher Eomes/lower T-bet; TCF-1 sustains progenitor fate [239]. Culture skewed terminal-like; BATF/PRDM1/NR4A varied, TOX/NFAT incomplete [240].

NFAT without AP-1 induces anergy/exhaustion upstream of TOX/NR4A; NR4A1 deletion lowers PD-1/TIM-3 and restores proliferation; PRDM1/Blimp-1 drives chronic-LCMV dysfunction; TOX maintains Tex [241]. PD-1high CD8+ TILs co-express checkpoints and lose function; tumor glucose dampens T-cell mTOR [241].

CD8/CD4 scope is context-specific: in 2003 human lung-tumour xenografts, local IL-12 increased IFN-γ⁺ CD8⁺ cells 2.3-fold (2.5–5.7%); CD4⁺ depletion reduced IFN-γ/tumour suppression, and CD4 help sustains CD8 responses in chronic viral infection [243]. A 2015 5%-versus-20% oxygen study used hES cells, not Tex; its cell-line-dependent result cannot establish T-cell metabolic mechanisms [242].

Cancer-associated Tex are context-specific: in a 2022 mouse-melanoma model, T cells progressed from progenitor-like to poorly functional terminal Tex, yet retained recoverable function; hypoxia impaired gene expression, while 4-1BB co-stimulation increased activity [248]. Tumor heterogeneity, stroma and gradients may be absent from simple cultures; mouse models may misrepresent human tumors [245][246][247]. These sources establish no universal Tex factor profile.

In Exhausted T cells, the clearest direct perturbational result concerns TCF-1: in chronic infection, genetic loss depletes the durable Tex pool, whereas enforced TCF-1 represses terminal/Teff-like cell formation and expands the Tex-precursor population, supporting roles in establishing and maintaining exhaustion [101]. NFAT, BATF, T-bet/EOMES, PRDM1, NR4A and TOX are supported mainly as exhaustion-associated or pathway-level regulators rather than matched gain- or loss-of-function findings; the direct reversal evidence here is checkpoint blockade, which restores function transiently and depends durably on progenitor cells [110,127,282].

Exhausted T cells lose effector capacity hierarchically: IL-2 production, high proliferative capacity and in-vitro cytotoxicity decline first, TNF-α follows, and IFN-γ and other late effector outputs decline later; cytokine production is reduced rather than necessarily absent [127,140,165]. The resulting loss of proliferation, cytotoxicity and recall weakens pathogen and tumor control, although residual function can restrain persistent infection; chronic LCMV responses also show poor recall and cytokine production [105,114,427].

In Exhausted T cells, PD-1-associated inhibition of AKT/mTOR, glycolysis, mitochondrial activity and PGC1α, together with restricted glucose use and mitochondrial depolarization or reduced biogenesis, increases ROS and links metabolic remodeling to impaired function [140,420]. Compared with an effector-oriented program, this state can favor survival and persistence under nutrient limitation while sacrificing effector output; long-term antigen exposure changes metabolic requirements, making the shift relevant to Tex differentiation and maintenance [441,105].

Chronic infection is the canonical setting in which T-cell exhaustion is defined: after the effector phase, persistent antigen and inflammation maintain TCR stimulation and drive hierarchical loss of function, inhibitory-receptor/TOX programs and heterogeneous progenitor-to-terminal states [165,130,205]. It also defines the evidence boundaries—antigen load and duration, CD4 help and the particular infection context modify the phenotype, and some persistent EBV/CMV-specific cells remain functionally competent—so chronic-infection findings should not be treated as context-free rules [353,482,426].

Cancer shapes Exhausted T cells through persistent tumor antigen plus a tumor microenvironment that supplies checkpoint ligands, suppressive signals and competition for nutrients; the result is a heterogeneous continuum from stem-like/progenitor tumor-reactive cells to terminal dysfunctional TILs with inhibitory-receptor co-expression and impaired cytokine, proliferation and killing [164,225,478,205]. The evidence is strongly context-bound: tumor type/subtype, tissue location, spatial distribution, species and immune composition alter phenotype and mechanism, and the literature is predominantly murine, so cancer findings require an explicit tumor context before generalization [178,200].

CD8 T cells provide core exhaustion evidence: chronic LCMV and human viral/tumor studies link persistent antigen to altered transcriptional programs, inhibitory-receptor co-expression and impaired effector function, while a stem-like population can persist, expand and sometimes be reinvigorated [454,475,169]. These conclusions are not automatically transferable to CD4 or all T cells, because CD8 receptor profiles and functions vary with activation, differentiation, species, tissue and anatomical context; CD8-focused chronic-infection evidence therefore needs subset-specific validation [474,405,531].

CD4 T cells qualify CD8-centered evidence in both helper function and intrinsic dysfunction: CD4 help maintains effector but not proliferation-competent progenitor cells, whereas in chronic toxoplasmosis CD4 dysfunction is more pronounced than CD8 dysfunction [215][244]. Thus CD8-derived exhaustion rules should not be generalized without subset and species controls: CD4 receptors are MHC-II-restricted rather than CD8 receptors being MHC-1-restricted, and mouse endothelial cells cannot activate CD4 cells whereas human endothelial cells can [71][249].

T-cell exhaustion is the report's central biological focus because it is a chronic-antigen differentiation state in which effector function progressively deteriorates while residual function, altered transcriptional programs and inhibitory receptors remain measurable [93,620,456]. Studying that state supports the purpose of a comprehensive report by connecting chronic infection and cancer to pathogen/tumor control and immunotherapy, and by motivating comparison of Tex subsets and mechanisms rather than treating all hyporesponsiveness as anergy [365,356,598].

Exhausted T cells are the direct measurable research object: persistent inhibitory-receptor expression, reduced cytokine/cytotoxic/proliferative output, altered chromatin/transcription and residual function operationalize the problem across experiments [93,109,465]. Their heterogeneity—including progenitor, intermediate and terminal developmental states—makes Tex useful for linking mechanism to persistence, checkpoint response and therapeutic reinvigoration, but requires state-aware rather than individual-marker interpretation [126,598,617].

Chronic infection is the research benchmark because persistent high antigen and inflammation produce progressive CD8 dysfunction, inhibitory-receptor co-expression and exhaustion-associated transcriptional programs, while CD4 help and co-inhibitory pathways modulate persistence and progression [209,454,482,206]. It therefore supplies the physiological reference for testing mechanisms and validating in-vitro Tex models, but virus-, host- and tissue-specific contexts limit direct generalization [193,206,188].

Cancer is a complementary research context in which persistent tumor antigen and the tumor microenvironment expose T cells to inhibitory ligands, stromal/ECM barriers, suppressive cytokines and metabolic stress; tumor-reactive cells can remain present while impaired proliferation and function permit tumor growth [178,33,477,443,157]. This makes cancer essential for testing tumor control and immunotherapy, but tumor heterogeneity, tissue architecture and host–stroma interactions mean findings and in-vitro readouts must be benchmarked to the specific tumor context [495,578].

Use the TCF1+ stem-like-progenitor versus more differentiated exhausted-state classification for the Transcription-factor dimension: TCF1/TCF7 supports precursor formation, whereas T-bet/EOMES show state-dependent balance and PRDM1, BATF, NFAT, IRF4, TOX and NR4A regulate exhaustion-associated programs [454,300,127]. This framework makes TF profiling useful for separating exhaustion from ordinary activation, but factor expression is context-dependent and no single master regulator is established, so causal perturbation is needed [188,160].

Use a co-inhibitory-receptor co-expression/severity framework for the Inhibitory-receptor dimension: increasing receptor amount and diversity, and co-expression, track greater dysfunction and exhaustion severity, so multireceptor panels operationalize the Tex state [126][197][107]. The framework also identifies blockade as a perturbation target, but receptor patterns vary with T-cell function, differentiation, infection severity and tumor aggressiveness and can accompany activation, requiring contextual rather than single-marker interpretation [139][192][199][207].

Use the ‘metabolically insufficient’ versus ‘metabolically inert’ framework for the Metabolic-activity dimension: Tex are metabolically insufficient under chronic activation, while metabolic circuits couple energy state to stemness, effector differentiation and epigenetic regulation [441,126]. This dimension explains how nutrient limitation, extracellular acidosis and inhibitory signaling can sustain dysfunction or alter Tex-state progression, but metabolic measurements require physiological and subset context rather than serving as a standalone exhaustion label [554,126].

CD8 T cells are the principal experimental population for researching exhaustion: mouse LCMV and tumor models plus human viral and tumor samples connect persistent antigen to altered differentiation, checkpoint expression, impaired function and state-specific persistence [454,126,198,475,209]. Generalization is limited because CD8 receptor profiles and functions vary with activation, differentiation, tissue, species and antigen context, and CD4 help can change the trajectory; conclusions should therefore be labeled as CD8-specific unless independently validated [474,21,482].

CD4 T cells are relevant as helper inputs and as a distinct exhaustion population: CD4 help supports maintenance of CD8 effector rather than proliferation-competent progenitor cells and is required for formation of a cytolytic CD8 subset, while exhausted CD4 cells have a distinct molecular profile [215][212][189]. CD4-specific NFAT evidence and MHC-II restriction, together with mouse–human differences in endothelial antigen presentation, mean CD8-derived receptor, transcription-factor and cytotoxicity rules require separate validation across subset, tissue and species [117][71][249][227].

T-cell exhaustion gives the comprehensive report its organizing problem: a progressive, heterogeneous chronic-antigen state combining impaired effector function with altered transcriptional, epigenetic, inhibitory-receptor and metabolic programs, yet not necessarily complete loss of function [620,598,510,448,202]. That definition supports the report's comparative and modeling aims because it requires multidimensional functional and molecular validation and has direct implications for chronic-infection control, tumor immunity and therapeutic reinvigoration; phenotype alone should not be equated with exhaustion [365,621,202].

## 3. Comparison of transcription-factor expression profiles

**The clearest shared-axis comparison follows:** the strongest recurring distinction is high TCF-1 in progenitor exhausted cells versus low or absent TCF-1 in terminal Tex. PRDM1 and NR4A-associated activity generally become more prominent with differentiated exhaustion, while T-bet:EOMES, BATF, NFAT, and the progenitor-to-terminal TOX ordering require more specific interpretation.

| Transcription factor or state | Effector T cells | Progenitor exhausted T cells | Terminally exhausted T cells |
|---|---|---|---|
| TCF-1/TCF7 | Unclear; differentiation-dependent | High | Low or absent |
| T-bet:EOMES ratio | Usually High; T-bet-dominant | Unclear; stage- and gate-dependent | Usually Low; EOMES-dominant |
| BATF | High/active effector circuitry | Active enhancers; abundance Unclear | Abundance Unclear; lower BATF-enhancer enrichment |
| NFAT | AP-1-coupled activation | Abundance/partner state Unclear | Persistent or AP-1-independent activity |
| PRDM1/BLIMP-1 | Increased with effector differentiation | Low relative to differentiated Tex | High or increased |
| NR4A family | Unclear; transient activation also induces | Unclear; trajectory-dependent | High family-regulon activity |
| TOX | Low/transient relative to chronic Tex | High or TOX-positive | High versus Teff; progenitor–terminal rank Unclear |

The TCF-1 and T-box entries draw principally on Chen et al.’s mouse fate study [9] and human HIV phenotyping [8]. BATF and NR4A activity distinctions are supported by chronic-LCMV regulatory analysis [27]. NFAT partner-state evidence comes from Martinez et al.[15]; PRDM1 and terminal-subset features are supported by Miller et al.[2].

### The robust transition: loss of progenitor capacity

**TCF-1 tracks a functional developmental difference:** the progenitor-to-terminal contrast is supported by expression, genetic perturbation, and transfer experiments. TCF-1-positive cells renew the response and produce differentiated descendants; TCF-1-negative terminal cells contribute immediate activity but sustain themselves less effectively. In Miller et al.’s mouse tumors, PD-1 blockade expanded transferred progenitor Tex **4.4-fold**, while transferred terminal Tex did not show the corresponding expansion. [2]

**The effector column needs developmental context:** an acutely activated CD8+ population can contain different proportions of differentiated effectors and cells retaining precursor potential. In addition, some BATF and T-bet evidence comes from CX3CR1-positive effector-like cells within a chronic infection, not exclusively from acute-infection effectors. These comparisons establish active effector-associated circuitry, but they do not make every effector population an identical reference state.

**PRDM1 contrasts with the progenitor program:** low PRDM1 relative to differentiated Tex is consistent with TCF-1-centered precursor networks. In Jung et al.’s 2023 primary CAR-T study, low PRDM1 identified potent TCF7-expressing CD8+ cells in clinical products, whereas higher PRDM1 accompanied TIM-3-expressing cells associated with poorer outcomes. That study analyzed **20,702 cells from five autologous PSMA CAR-T infusion products**, combining a small clinical association with engineered perturbation experiments. [26]

### Why the T-bet:EOMES ratio changes with context

**A familiar hierarchy is not universal:** older chronic-infection descriptions often distinguished proliferative T-bet-high/PD-1-intermediate cells from EOMES-high/PD-1-high differentiated cells. However, the progenitor category defined by TCF-1 is not identical to every earlier PD-1-intermediate or T-bet-high gate. The Annual Review synthesis by McLane, Abdel-Hakeem, and Wherry [28] discusses these overlapping but distinct subset definitions.

**Early precursors provide a concrete counterexample:** at day 8 of chronic LCMV Clone 13 infection, Chen et al. found that PD-1-positive/TCF-1-positive P14 cells had the highest EOMES and the lowest T-bet:EOMES ratio among the compared populations. KLRG1-positive/CD39-positive effector-like cells instead had the highest T-bet and strong immediate effector functions. Thus, a low ratio can occur in early progenitor Tex as well as in differentiated exhausted states. [9]

**Human HIV supports association, not equivalence:** in Buggert et al.’s cohort of **52 untreated people with chronic HIV**, HIV-specific responses were predominantly T-bet-dim/EOMES-high, whereas cytomegalovirus-specific responses occupied both T-box expression patterns. Among PD-1/CD160/2B4 triple-positive CD8+ cells, a median **91.7%** were T-bet-dim/EOMES-high. These measurements support an exhaustion-associated balance but do not assign the human cells to formally sorted TCF-1-defined progenitor and terminal Tex compartments. [8]

**The ratio’s practical meaning is relational:** it can distinguish effector-biased from exhaustion-associated programming within an appropriately defined comparison. Its interpretation changes when the sampling day, tissue, sorting markers, or underlying precursor population changes; it should not replace the broader cell-state profile.

### Why BATF, NFAT, NR4A, and TOX resist simple ranking

**BATF activity differs from BATF quantity:** chronic-LCMV enhancer analysis found BATF-associated motifs in regulatory regions shared by progenitors and CX3CR1-positive effectors, rather than the terminally exhausted compartment. That observation concerns accessible regulatory DNA and inferred activity. It is compatible with BATF expression in other exhausted populations and with its ability to participate in different complexes. [27]

**NFAT is fundamentally a state comparison:** AP-1-coupled versus AP-1-independent NFAT better captures the experimentally demonstrated distinction than a universal high/low protein label. Even this is not an exclusive division: in-vivo Tex chromatin can contain both NFAT-only and NFAT:AP-1 composite motifs. The relevant issue is how the regulatory balance changes, not whether AP-1-associated transcription disappears altogether. [15][4]

**NR4A activation is not exhaustion-exclusive:** these receptors respond during ordinary activation as well as contributing to exhausted-cell programs. High terminal-associated NR4A regulon activity—a coordinated expression pattern of inferred target genes—does not imply that an activated effector must have no NR4A. Persistence, network connections, and the functional consequences of perturbation provide the useful distinction. [19]

**TOX distinguishes lineage better than severity:** both progenitor and terminal Tex can express substantial TOX. The 2020 Immune Network review describes higher TOX in stem-like than terminal subsets, whereas the June 2023 hierarchical review describes a terminal TOX-high state. Both support high TOX relative to conventional effector or memory comparators; their differing within-Tex orderings underscore the importance of subset definitions and developmental context. [29][30]

**The table’s resulting judgment is specific:** TCF-1 provides the strongest progenitor-versus-terminal discriminator among the requested factors; the other entries become most useful when paired with developmental stage, function, and the type of molecular measurement.

**Additional documented evidence**

| Entity | TCF-1 | T-bet to EOMES ratio | BATF | NFAT | PRDM1 | NR4A | TOX | key effector functions or states | T-bet to EOMES ratio | effector-function roles in exhaustion | key metabolic molecules or states | PRDM1 | metabolic roles in exhaustion |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Effector T cells | no evidence found | no evidence found | no evidence found | NFATC1 lower; NFATC2 not different [257] | no evidence found | Unclear; no significant state difference [257] | Lower than exhausted lineage [261] | no evidence found | no evidence found | no evidence found | NFATC1 lower; NFATC2 not different [257] | no evidence found | Unclear; no significant state difference [257] |
| Progenitor exhausted T cells | no evidence found | no evidence found | BATF suppresses T-cell functions in HIV-specific CD8+… | NFAT is reported to promote exhaustion of activated…[257] | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | Tpex cells exhibited robust interactions with myeloid…[262] | NFAT is reported to promote exhaustion of activated…[257] | no evidence found | Tpex cells exhibited robust interactions with myeloid…[262] |
| Terminally exhausted T cells | no evidence found | Low (T-bet-low/EOMES-high)[260] | no evidence found | NFATC1 higher; homodimers; impaired NFAT:AP-1[257][155] | no evidence found | no evidence found | The supplied page names TOX as a transcription factor… | no evidence found | no evidence found | no evidence found | NFATC1 higher; homodimers; impaired NFAT:AP-1[257][155] | no evidence found | no evidence found |

Additional or intermediate Tex states should be discussed because the evidence operationally separates progenitor, intermediate, and terminal populations and supports analysis beyond a simple terminal-versus-effector contrast [264]. They should qualify interpretation around the fixed Effector–Progenitor exhausted–Terminally exhausted table, not displace its requested rows [264].

rejected: no_entity. Additional or intermediate Tex states should be retained around the fixed state table because the trajectory includes progenitor, intermediate, and terminal populations, including early effector-like and intermediate Tex [264][265]; allowed numbers: none used; allowed citations: [264][265]; allowed entities: Additional or intermediate Tex states, Effector T cells, Terminally exhausted T cells.

**Comparison basis and state definitions**

The three rows are operational comparators, not universally fixed developmental labels. “High” and “Low” below mean relatively higher or lower within the cited assay, tissue, species, disease model, and sampling point; “Unclear” means that the evidence shown here does not support a directly comparable state-level call. Most direct comparisons concern CD8+ T cells exposed to chronic viral antigen or tumors, so the profiles should not be generalized automatically to every T-cell subset or human disease context [205, 455].

**Effector T cells** are the functional comparator, most clearly represented during acute infection. In that setting, T-bet and Eomes promote effector molecules such as IFN-γ, and T-bet drives the effector and KLRG-1+ terminal-effector programs [210]. Effector cells are therefore a functional baseline rather than simply “all factors high” or “all inhibitory markers absent.” A small subset of early effector-phase CD8+ cells retains TCF-1 and can give rise to central-memory cells, so TCF-1 is not uniformly absent from every effector-phase population [143].

**Progenitor exhausted T cells** are a heterogeneous, self-renewing exhaustion-stage population. In one operational scheme, T Ex prog1 and T Ex prog2 are distinguished by Ly108/SLAMF6, CD69, and Ki67. T Ex prog1 has low T-bet and low Ki67, is quiescent, resides in splenic white pulp, and does not enter the bloodstream; T Ex prog2 expresses Ly108 but not CD69, has intermediate expression of the other markers and Ki67, proliferates, and circulates in blood and red pulp [250]. Other studies define progenitor Tex as PD-1^int^CD44^hi^Eomes^low^ or CXCR5+TCF-1+TIM-3− cells. These cells are less functionally exhausted, have greater proliferative or polyfunctional capacity, can respond to PD-1 blockade, and can generate a larger terminal-Tex pool [424, 442].

**Terminally exhausted T cells** represent a more differentiated, generally less reprogrammable state. They are characterized by loss of T-bet, gain of Eomes, the highest TOX activity, restored CD69, permanent cell-cycle exit, low Ki67, high PD-1, and residence in peripheral tissues, blood, or splenic red pulp [250]. They are less responsive to checkpoint blockade than progenitor Tex, and their distinctive epigenetic landscape can dampen effector function and the efficacy of PD-1 blockade [185, 442]. In chronic viral-infection comparisons, terminally differentiated cells are generally TCF1^low^ [143].

The three rows should not be interpreted as a mandatory single linear trajectory. A chronic-LCMV single-cell study identified early-effector exhausted (Tex eeff), progenitor (Tex prog), intermediate (Tex int), KLR-expressing (Tex KLR), and terminal (Tex term) populations. Tex int had an intermediate chromatin state and could represent a bifurcation point leading toward alternative terminal or KLR-associated phenotypes [264]. These additional states remain in the discussion rather than being added to the fixed three-row table.

**Qualitative transcription-factor comparison**

| T-cell state and context | TCF-1 | T-bet:EOMES relationship | BATF | NFAT | PRDM1 (BLIMP-1) | NR4A | TOX |
|---|---|---|---|---|---|---|---|
| **Effector T cells** — functional CD8+ effector state in acute infection or early activation | **Unclear** across the whole effector population; a small early effector subset retains TCF-1 and can seed central memory [143] | **T-bet-driven effector program; literal ratio Unclear**. T-bet and Eomes support effector molecules, but the shown evidence does not report a common T-bet:EOMES ratio [210] | **Unclear** abundance; BATF participates in antigen-driven activation and effector CD8+ differentiation, including a Sirt1-linked program [424, 442] | **Balanced NFAT:AP-1 activity**: NFAT–AP-1 heterodimers promote functional effector-gene transcription; this is an activity description, not an abundance call [210] | **Unclear** abundance; BLIMP-1 can repress PD-1 through a feed-forward circuit during acute viral infection, but that does not establish an effector-row expression level [210] | **Unclear**; the evidence shown concerns NR4A-associated dysfunction or exhaustion rather than a directly comparable effector profile [263] | **Transient/activation-linked**, not stably High: functional effectors generated by acute infection or in-vitro stimulation can transiently express TOX, which decreases after antigen–TCR stimulation stops [143] |
| **Progenitor exhausted T cells** — chronic antigen; primarily CD8+ chronic-infection or tumor contexts | **High/TCF-1+**: TCF-1 maintains progenitor capacity, supports self-renewal, and marks cells that can generate terminal Tex; TCF-1+ progenitors are also associated with CXCR5 and checkpoint responsiveness [185, 205, 455] | **Unclear as a literal ratio**: T Ex prog1 has low T-bet, whereas the broader PD-1^int^Eomes^low^ progenitor pool has been associated with elevated T-bet; the CXCR5+TCF-1+ population is not uniformly T-bet-high [185, 424] | **High/enriched motif activity in the early Tex–progenitor program**, rather than an absolute protein level; progenitor-associated BATF motifs decline when cells enter Tex int [264] | **Unclear abundance**; NFAT and BATF help prime TCF-1− precursor chromatin for the Tex program, but a directly comparable progenitor NFAT level is not supplied [264] | **Unclear**; BLIMP-1/PRDM1 is linked to PD-1 regulation and exhaustion, but no progenitor-specific PRDM1 profile is shown [210] | **Unclear**; NR4A cooperates with TOX/TOX2 in exhaustion, but the shown evidence does not establish a progenitor-specific NR4A level [263] | **High/present across Tex states**; TOX is described as a core exhaustion regulator, and Tox-locus accessibility rises during the Tex eeff-to-progenitor transition [185, 455] |
| **Terminally exhausted T cells** — chronic antigen; tissue-associated CD8+ terminal Tex | **Low/TCF-1^low^**, particularly in terminally differentiated cells located in peripheral tissues or splenic red pulp [143] | **Low T-bet:high EOMES direction**, not a calculated ratio: terminal Tex lose T-bet and gain Eomes [185, 424] | **Unclear** terminal abundance; progenitor-specific BATF motifs are lost during progression toward Tex int, but the shown evidence does not justify calling terminal BATF protein Low [264] | **High motif accessibility/activity**, not necessarily high abundance: Tex term chromatin is strongly enriched for NFAT motifs [264] | **Unclear** terminal abundance; the cited BLIMP-1 evidence establishes regulatory relevance but not a directly comparable terminal-Tex value [210] | **High/enriched terminal-program motif activity**, not a quantitative expression call: NR4A motifs are enriched in the Tex term trajectory and may guide terminal differentiation [442, 455] | **High/highest activity**: all Tex subsets express TOX in the cited scheme, while terminal Tex shows the highest activity; TOX also programs the durable exhaustion state [185, 442] |

The **T-bet:EOMES** column is deliberately not calculated from separate T-bet and Eomes calls: the available evidence sometimes describes low T-bet, Eomes^low^, or Eomes^high^ subsets, but those observations are not necessarily measurements of the same population, assay, or denominator. Accordingly, the table reports direction or “Unclear” rather than inventing a ratio [185, 424].

**Mechanistic qualifiers for interpreting the table**

TCF-1 is most informative as a state and trajectory marker. TCF1+ progenitor cells in chronic infection self-renew and give rise to TCF1^low^ terminal cells; TCF-1-positive cells are progressively lost as Ki67 increases, and the TCF-1–T-bet axis helps regulate progression from T Ex prog2 toward intermediate Tex [185, 205]. In human tumors, however, TCF1+ TILs can include bystander, non-tumor-reactive cytotoxic cells, whereas TCF1^low^ TILs can show PD-1, LAG-3, CD39, and TOX hallmarks. TCF-1 therefore supports—but cannot alone establish—progenitor Tex identity [143].

BATF and NFAT illustrate why transcription-factor **activity and regulatory context** matter more than abundance alone. BATF participates in initial antigen-driven activation, effector differentiation, and IL-21-associated chronic antiviral control; in some settings PD-1-associated BATF induction is linked to impaired T-cell function [210]. In the chronic-LCMV trajectory, BATF motifs are enriched early and in Tex progenitor-associated programs but decline at entry into Tex int [264]. NFAT with AP-1 promotes functional effector genes after acute activation, whereas high NFAT relative to AP-1 produces partnerless NFAT that can induce PD-1, LAG-3, TIM-3, and other Tex genes while repressing memory programs. Impaired NFAT nuclear translocation can instead produce “split exhaustion,” showing that NFAT localization and partners are essential qualifiers [210].

For **PRDM1**, the evidence shown is mechanistic rather than a complete three-state profile: BLIMP-1 can repress PD-1 during acute viral infection, and a cited study assigns BLIMP-1 a role in CD8+ exhaustion during chronic viral infection [210]. **NR4A** transcription factors cooperate with TOX and TOX2 to impose CD8+ exhaustion, limit CAR-T function in solid tumors, and associate with terminal-Tex regulatory motifs [442, 455]. **TOX** is likewise not a simple terminal marker: it is present across Tex states, rises in the exhaustion program, reaches highest activity in terminal Tex, and can remain elevated after antigen removal. In one cited recovery experiment, TOX remained high after 500 days and recovered cells retained epigenetic scars and failed to fully restore memory or effector function [250].

The open roster is biologically important. In the chronic-LCMV multi-omic study, 96,750 quality-controlled single-cell RNA profiles were obtained; differential open-chromatin regions included 3,567 for Tex eeff, 4,818 for Tex prog, 235 for Tex int, 1,223 for Tex KLR, and 1,594 for Tex term, with additional Tex eeff2 cells identified [264]. Tex eeff showed greater cycling and glycolytic activity, whereas Tex int expressed proliferation- and TCR-signaling-associated programs. Tex KLR and Tex term were epigenetically divergent, with 405 and 364 state-specific open regions, respectively, and only 4 shared regions in one comparison [264]. These findings justify discussing intermediate and alternative states while retaining the requested three-row table.

**Evidence-qualified state interpretation**

**TCF-1 (TCF7/Tcf7) is the clearest state discriminator in the supplied evidence:** Progenitor exhausted T cells are **High/expressed** for TCF-1, whereas the terminal-Tex comparator is **Low or absent**; the Effector T-cell TCF-1 cell remains **Unclear** in a matched three-row comparison because the other observations come from thymocytes, acute infection, HBV-specific cells, or CAR-T cells rather than the fixed state roster and assay [147][148][253][150][267]. In mouse and human melanoma, progenitor exhausted cells were defined as **Tcf7^+Pdcd1^+**, whereas the terminal-Tex comparator was **Tcf7^−Pdcd1^+** [147]. The progenitor population is stem-like, self-renewing, capable of differentiating into other exhausted populations, and more proliferative and recall-competent than terminal Tex [147][148].

In the same melanoma study, **CD39^−Tim-3^−Slamf6^+PD-1^+ CD8 TILs** showed the greatest enrichment for Tcf1^+ cells and represented approximately **3.5% of total endogenous or transferred OT1 TILs**; this conclusion came from transcriptomic analysis and flow cytometry of murine B16/B16.OVA tumors and human primary melanoma tumors [147]. However, CXCR5 did not consistently identify Tcf1^+ cells in those mouse and human melanoma datasets, so progenitor markers are context-dependent rather than universal [147]. In chronic LCMV infection, Tcf-1^+PD-1^+ cells are concentrated in secondary lymphoid organs and are nearly absent from peripheral blood; TGF-β restrains mTOR activity, supports long-term responsiveness, limits CX3CR1^+ effector differentiation, and promotes CD101^+ terminal exhaustion [148].

TCF-1 is a T-cell-specific transcription factor involved in Wnt signaling and αβ-T-cell differentiation [266]. The mouse Tcf7 gene page reports tissue-level expression of **829.6 RPKM in adult thymus** and **56.0 RPKM in adult spleen**, and describes **14 exons** with alternatively spliced transcripts; these are gene- and tissue-level observations, not expression values for the three requested T-cell states [266]. Similarly, in a separate mouse thymocyte/lymphoma system, Tcf1-deficient non-tumor ISP and DN3 thymocytes had Wnt-reporter MFI values of **385 and 104**, compared with **874 and 635** in controls; Tcf1-deficient lymphoma samples showed **1,425 and 1,225 MFI** in tumor-1 DP/ISP cells and **2,123, 2,374, and 1,203 MFI** in tumor-2 DP/ISP/DN3 cells [251]. These measurements indicate altered Wnt activity, not a Tex-state TCF-1 profile.

The progenitor-to-terminal relationship is therefore not necessarily a universal linear sequence. Tcf-1^+ cells can generate transitional CX3CR1^+ populations and CD101^+ terminal cells, but the cited review also notes evidence for a bifurcation model; the lineage relationship between TRM-Tcf-1^+ and non-TRM-Tcf-1^+ cells remains unresolved [148]. Tumor-draining lymph nodes can act as reservoirs of Tcf-1^+ CD8 T cells: cDC1-delivered tumor antigen and TGF-β promote Tcf-1^+ tissue-resident states, whereas type I interferon can inhibit their establishment; Tcf-1^+ cells can subsequently lose TRM identity and differentiate toward Tcf-1^− effector cells [148]. These intermediate and tissue-resident populations are relevant boundary cases but do not replace the fixed Effector, Progenitor exhausted, and Terminally exhausted rows.

**Context-qualified evidence for the remaining factor columns**

**T-bet:EOMES ratio.** In chronic HBV infection with low viral load, pol455-specific CD8 T cells had **higher Eomes with equally low T-bet** than core18-specific cells, producing an Eomes-skewed, dysregulated relationship that more closely resembled terminal exhaustion; the study did not report a literal numeric ratio [150]. The result is antigen-, disease-, and human-sample-specific rather than a universal assignment to the requested Terminally exhausted row. The same study found that TCF1 expression was equal between the compared HBV-specific populations and their memory-like subsets, so TCF1 alone did not explain their different expansion capacities; balanced TCF1/BCL2 expression was more informative [150].

**PRDM1/BLIMP-1.** In acute LCMV infection, PRDM1 was **higher in terminally differentiated KLRG1^hiIL-7R^lo short-lived effector cells than in KLRG1^loIL-7R^hi memory-precursor effector cells by approximately 2–4-fold**, measured by mRNA, protein, and a YFP reporter [253]. Conditional PRDM1 loss produced fewer terminal effector cells and more memory-precursor and central-memory phenotypes [253]. Its functional effects were not uniformly suppressive: PRDM1-deficient cells produced more IL-2 and showed greater polyfunctionality but lower per-cell IFN-γ and granzyme B; on day 5 after infection, granzyme B was detected in approximately **50–60%** of knockout effector cells versus **about 90%** of wild-type cells, while in-vivo cytotoxicity was only marginally affected [253]. Because SLEC and MPEC populations are acute-infection differentiation comparators rather than the fixed Tex rows, these findings should not be converted directly into Effector-, Progenitor-, or Terminal-Tex PRDM1 calls.

A separate CAR-T analysis found that **low PRDM1** marked potent TCF7/TCF1-expressing CD8 CAR-T cells, whereas elevated PRDM1 in HAVCR2/TIM-3-expressing cells was associated with poor outcome; PRDM1 knockout promoted TCF7-dependent stemness and proliferation [267]. This analysis used single-cell RNA sequencing of CAR-T cells from a first-in-human metastatic-prostate-cancer trial and therefore provides mechanistic context, not a complete three-state exhaustion profile [267].

**NFAT and NR4A.** The CAR-T evidence supports an **NFAT-driven activity state**, not an abundance call: under PRDM1 deficiency, NFAT was associated with a negative epigenetic feedback program of dysfunction that increased NR4A3 and other exhaustion-related transcription factors and impaired effector function in solid tumors [267]. Thus, NFAT abundance, partner usage, and dimerization remain **Unclear** for the three requested rows in this evidence set. NR4A3 was **compensatorily upregulated** in that context; dual PRDM1/NR4A3 loss shifted cells away from TIM-3^+CD8^+ and toward TCF1^+CD8^+ cells, countering exhaustion and improving antitumor responses [267]. This supports a context-specific NR4A3 mechanism but not a complete NR4A-family profile for Effector, Progenitor exhausted, and Terminally exhausted T cells.

**TOX.** TOX is mechanistically linked to exhaustion rather than resolved here by a complete three-row expression profile. Sustained antigenic stimulation induces a TOX-driven epigenetic program that supports CD8 T-cell persistence; failure to activate that program can allow persistent antigen to erode immunodominant clones through activation-induced cell death [147]. In the chronic LCMV work, TOX overexpression increased PD-1, reduced KLRG-1, TNF, and IFN-γ production, and promoted a dysfunctional phenotype, while Tcf-1 MFI remained similar; TOX deficiency or deletion was associated with functional memory or enhanced effector function but also greater immunopathology [252]. Human ex-vivo activated T cells transduced with TOX were co-cultured with SK-Mel-23 or 888-A2 tumor cells for **16 hours**, after which TNF and IFN-γ were measured [252]. The related evidence used intracellular flow cytometry, microarray, sequencing at days **8 or 20** after infection, and ATAC-seq [252]. These perturbational and assay-specific results establish TOX relevance, but the Effector, Progenitor exhausted, and Terminally exhausted TOX expression cells remain **Unclear** in the cited direct comparison [147][252].

**BATF.** The evidence shown in this source group does not provide a directly comparable BATF measurement for the fixed three-state roster; BATF cells should therefore remain **Unclear here**, rather than borrowing TCF-1, T-bet:EOMES, or TOX patterns [148][150]. The deciding condition for a High or Low table label is a matched state definition, assay modality, species or tissue context, and sampling basis; otherwise the appropriate entry is **Unclear**, even when a factor has a strong mechanistic association with exhaustion.

Effector T cells are the functional comparator: circulating tumor-specific CD8+ cells showed high granzyme B/perforin and efficient IFN-γ, whereas tumor-infiltrating cells were exhausted; BATF was not enhanced, and TCF-1, NFAT, PRDM1 and TOX were not directly measured [254]. Progenitor exhausted T cells are TCF1+ memory-like CD8+ cells with no effector signature but self-renewal and differentiated progeny; they are Eomes+ and T-bet-low, not a literal ratio [153]. Terminal-like chronic-LCMV cells are T-bet-low/Eomes-high and exhaustion-associated; TCF1 is reduced in terminally differentiated cells, although direct row mapping is limited [246,250].

TCF1+ cells sustain chronic responses and expand after PD-1 blockade [153]. TOX deletion reduces inhibitory receptors and Eomes while improving effector function; PRDM1/Blimp-1 regulates inhibitory receptors and increases in Tbx21 E/E CTLs [255]. Because marker scales can differ by orders of magnitude, all labels require assay and context qualifiers [151]. Additional CD8+ Tex evidence distinguishes two TCF1+ progenitor subsets, an effector-like subset and a terminal subset, so the fixed three-row table is not exhaustive [256].

**Progenitor-state evidence and table qualifiers**

Progenitor exhausted CD8+ T cells are a distinct, stem-like exhausted subset: they retain self-renewal capacity, have distinct transcriptional and epigenetic features, and can be reinvigorated by PD-1 inhibition. Progenitor and terminal subsets can cooperate to contain chronic viral infection, while TCF-1-expressing memory-like cells sustain responses during chronic infection [257]. In tumor trajectories, effector cells can become dysfunctional and exhausted under an immunosuppressive tumor microenvironment, whereas another branch develops into long-lived memory cells [257]. In the source-specific phenotypic gate, PD-1⁺TIM-3⁻ cells represent progenitor exhaustion, PD-1⁺TIM-3⁺ cells represent terminal exhaustion, and PD-1⁻TIM-3⁻ cells are the less-exhausted comparator [257].


- **TCF-1 — Unclear for abundance; progenitor-associated and functionally characteristic.** TCF7/TCF-1 is described as essential in progenitor exhausted CD8+ T cells and associated with their stem-cell-like phenotype. However, one tumor analysis found no significant TCF7 upregulation in exhausted versus effector cells; in some mouse tumors, TCF1 correlated positively with PD-1. Thus, regulatory importance should not be converted into an unconditional “High” expression label [257].
- **T-bet:EOMES ratio — Unclear.** The eligible passages do not report a literal ratio or a compatible, state-by-state progenitor measurement; no ratio should be calculated from separate factor measurements.
- **BATF — Unclear for the fixed state comparison.** BATF was recovered as an exhaustion-associated transcription factor and differed between PDCD1-high and PDCD1-low tumor-infiltrating subsets, but its direction specifically in progenitor, terminal, and effector rows was not reported [257].
- **NFAT — Unclear for progenitor-specific abundance or activity.** NFAT promotes exhaustion; NFATC1 was higher in exhausted than effector cells (*P* = 7.637 × 10⁻⁵), whereas NFATC2 was not (*P* = 0.8299), and NFATC1/NFAT2 can induce TOX. These observations do not establish one progenitor-wide NFAT call [257].
- **PRDM1 — Unclear.** PRDM1 was identified among transcription factors associated with intratumoral CD8+ T-cell exhaustion, but the eligible passage does not give a qualitative profile across the three fixed states [257].
- **NR4A — Unclear or late-associated.** NR4A1 increased at later exhaustion stages, but the increase across the whole trajectory was not significant (*P* = 0.1209), and another comparison found no significant exhausted-versus-effector difference. Its regulatory relationship with TOX also remained unresolved [257].
- **TOX — Intermediate relative to the source-defined subsets.** TOX increased with exhaustion severity, with the reported ordering **terminally exhausted > progenitor exhausted > PD-1⁻TIM-3⁻** cells. This supports a higher progenitor value than the less-exhausted comparator but a lower value than terminal exhaustion [257].


Factor calls are assay- and state-dependent. In repeated-peptide murine CD8+ CTL, progenitor-exhausted cells retained TCF-1, whereas terminally exhausted cells were TCF-1-low; Tcf7 promoter methylation accompanied downregulation and persisted after rest/reactivation [157]. The cultures contained TCF-1+TOX+ progenitor cells and TCF-1-low/TOX-high/GzmB-high terminal cells; TOX rose with repeat stimulation [157]. Effector T cells: TCF-1 is Unclear here.

No literal T-bet:EOMES ratio was reported: repeat stimulation increased T-bet (≈90% T-bet+PD-1+) and lowered EOMES, leaving three-state calls Unclear [157]. BATF and NR4A rose; PRDM1 rose 4.5-fold, but none has a complete three-state profile. PRDM1/Blimp-1 is linked to chronic-viral CD8 exhaustion [268,269], while BATF can either accompany exhaustion or, with IRF4, support effector function [258].

NFAT is an activity/complex readout: persistent antigen impaired its nuclear translocation and could reduce IFN-γ [158]. Sustained nuclear NFAT without FOS/JUN shifts toward exhaustion genes; NR4A/TOX are downstream, and depletion partly restores TIL effector activity [258].

Effector T cells here refer to bona fide effectors generated after acute infection or vaccination and serve as the functional comparator for Tex [259]. Progenitor exhausted T cells (TPEX) are typically PD-1⁺TCF-1⁺, self-renewing, and capable of producing terminally differentiated PD-1⁺TCF-1⁻GZMB⁺ progeny; terminal Tex are typically PD-1^hiTIM-3^hiTCF-1⁻ with limited expansion capacity [160]. In chronic LCMV, CD69⁺ TPEX are relatively quiescent, whereas CD69⁻ TPEX are transitional toward TCF-1⁻ effector-exhausted cells; terminal cells express the highest inhibitory-receptor levels [186]. This is a context-dependent trajectory rather than a universal two-state sequence, because stages differ between tumors and chronic infections [259][160].

- **TCF-1:** Effector T cells show higher TCF-1 than Tex in comparative profiling; **Progenitor exhausted T cells: High/preserved**; **Terminally exhausted T cells: Low or absent** [159][160][186]. TCF-1 supports progenitor self-renewal and persistence, while transition to TCF-1⁻ exhausted effectors is largely irreversible in the described CD8⁺ contexts [186].
- **T-bet:EOMES:** **Unclear for all three rows as a literal ratio**. The evidence describes differential T-bet/EOMES programming, not a directly measured, comparable ratio; no arithmetic should be inferred [159][160].
- **BATF:** **Unclear for state-specific abundance** in this evidence group. BATF is an NFAT-driven, TCR-responsive factor associated with inhibitory-receptor expression and Tex survival, and it regulates the progenitor-to-cytolytic-effector transition [160][186].
- **NFAT:** **Unclear for abundance; report activity/partner state instead.** Acute effector signaling involves NFAT with AP-1, whereas chronic signaling can sustain NFAT despite reduced AP-1, favoring inhibitory-receptor and TOX expression [160][186].
- **PRDM1:** **Unclear** for Effector and Progenitor cells; **present/associated, not quantitatively graded** in Terminal Tex, which coexpress PRDM1 with effector genes and multiple inhibitory receptors [160].
- **NR4A:** **Unclear for state-specific abundance**; NFAT induces NR4A, which can suppress cytokine production and cooperate with TOX to impose CD8⁺ Tex [186].
- **TOX:** **Low relative to Tex in Effector cells; High/abundant in progenitor and terminal Tex**, although exact matched levels remain context-dependent [159][259][186]. TOX is not simply monotonic: complete loss compromises PD-1⁺-cell persistence, whereas partial loss can restrict dysfunction and increase cytotoxicity [186].

**State definitions and qualified profiles**

The rows are context-defined rather than universal stages: Effector T cells are acute-infection/vaccination KLRG1^Hi cells with robust function; progenitor exhausted cells are early chronic-LCMV TCF-1^+Ly108^+PD-1^+ cells with self-renewal and checkpoint responsiveness; terminally exhausted cells are established Tex with low function, high inhibitory-receptor expression and high TOX [239][208][108].

| State | TCF-1 | T-bet:EOMES | BATF | NFAT | PRDM1 | NR4A | TOX |
|---|---|---|---|---|---|---|---|
| Effector T cells | Low/absent in KLRG1^+CD39^+ Teff-like cells at D8 of Cl13 infection [239] | Higher than the TCF-1^+ progenitor population: highest T-bet and lower EOMES; no literal ratio reported [239] | Unclear; an early-effector differentiation checkpoint rather than a state-level call [239] | Unclear; activity, not abundance, is the relevant readout [208] | Unclear; PRDM1 promotes terminal effector differentiation [239] | Unclear; no state-specific level [208] | Unclear; no direct Teff-specific value [239][208] |
| Progenitor exhausted T cells | High/positive: TCF-1^+ Tcf7-rich Tex-precursor population at D8 of Cl13 infection [239] | Low relative balance: highest EOMES, slightly lower T-bet, and the lowest reported ratio [239] | Tcf7-correlated and present in the early precursor cluster; a PD-1–BATF–TCF-1 feedback loop is proposed, but level is unclear [239] | Unclear abundance; NFATc2 activity is exhaustion-relevant [208] | Negatively correlated with Tcf7; exact expression level is unclear [239] | NR4A1 positively correlated with Tcf7; exact level is unclear [239] | Present and Tcf7-correlated; TOX-dependent epigenetic remodeling occurs during the first 1–2 weeks of chronic antigen exposure [239][208] |
| Terminally exhausted T cells | Low/negative (TCF1^−) in the cited developmental trajectory [208] | Unclear; no direct terminal-state ratio is reported [239][208] | Unclear; no terminal-specific value [239] | Unclear; activity, partner and complex state require direct measurement [208][108] | Unclear; PRDM1 is reported in an intermediate effector-like subset, not assigned a terminal level [208] | Unclear; NR4A promotes dysfunction, but terminal abundance is not established [208] | High in the terminal subset [208] |

These qualitative calls are assay- and context-qualified; they do not create a universal cross-study expression scale. TCF-1 has the strongest state-discriminating evidence: its loss prevented a durable Tex pool and shifted cells toward KLRG1^+CD39^+ or Tim-3^+ populations, whereas enforced expression increased Ly108^+CD39^− precursors [239]. Progenitor cells showed greater polyfunctionality, antigen-independent persistence and PD-1 responsiveness, whereas terminal cells were more cytotoxic but short-lived [108]. In a transfer assay, 50,000 cells of each type were followed for 30–40 days; roughly 100-fold more progenitor cells were recovered, and terminal cells yielded only Tim-3^+ progeny [108].

Mechanistically, T-bet represses PD-1 and has temporally distinct effects on Tim-3; BATF is PD-1-associated but its relationship to early effector BATF function remains unresolved. TCR/CD28 signaling activates NFAT, which supports IL-2 and IFN-γ transcription, while NFATc2 activity is implicated in CD8-Tex regulation. PRDM1 promotes terminal differentiation, NR4A promotes dysfunction and cooperates with TOX/TOX2, and TOX converts persistent TCR signaling into an exhaustion-specific transcriptional and epigenetic program [239][208][108]. The fixed three-row table should therefore retain intermediate states as explanatory biology rather than silently adding them as rows.

## 4. Comparison of research methods

**The two approaches answer different questions:** direct isolation asks what cells have become in an actual chronic infection, tumor, or human tissue; in-vitro induction asks what specified inputs are sufficient to produce selected exhaustion-associated changes. Both approaches support mechanistic work, but they offer different combinations of physiological history, cell supply, and experimental control.

| Requested aspect | Direct isolation from mouse models/human tissues | In-vitro induction/generation |
|---|---|---|
| Method of isolation/generation | Disease-conditioned tissue; dissociation, enrichment, and subset sorting | Repeated peptide/APC or CD3/CD28 stimulation; engineered stress systems |
| Time to isolate/generate Tex cells | LCMV: 21–35 days; tumor examples: 10–21 days; human collection clinically timed | Representative endpoints: 5, 7, or 10 days |
| Cell yields for future testing | Limited, subset-dependent; reported assay inputs of 400–50,000 cells | Scalable; approximately ninefold expansion in one five-day model |
| Access to samples | Requires disease-bearing animals or appropriate clinical material | Naïve mouse cells, healthy-donor cells, or engineered populations |
| Mechanistic studies | Native disease-conditioned states; transfer, genetics, and low-input profiling | Controlled antigen, cytokine, genetic, pharmacological, and metabolic tests |
| Assigning cause-effect | Isolation alone is associative; in-vivo perturbation can establish causality | Strong within-model attribution; physiological transfer depends on context |

Timing and direct-isolation examples are documented by Chen et al.[16] and Miller et al.[2]. Culture timing and expansion are supported by Zhao et al.[3], the April 2023 P14 preprint [4], and Bommakanti et al.’s 2022 conference abstract [31].

### Isolation and generation workflows

**Direct isolation preserves disease-conditioned identity:** investigators collect infected organs, tumors, blood, or clinical tissue, prepare cell suspensions, enrich lymphocytes, and sort relevant populations. Peptide–MHC tetramers identify cells recognizing a defined antigen; flow-cytometric sorting then separates subsets using markers such as PD-1, TIM-3, and SLAMF6. SLAMF6—signaling lymphocytic activation molecule family member 6—is also called Ly108 in the mouse literature. [2]

**Antigen specificity and subset identity differ:** a checkpoint gate may enrich tumor-reactive cells without identifying all tumor-reactive cells or excluding every bystander. Moreover, adding TIM-3 or CD39 can improve enrichment for some tumor-reactive populations while selecting cells with poor expansion potential. Martinez-Usatorre et al. therefore used the combination **PD-1-positive/TIM-3-negative/SLAMF6-positive/CD39-negative** to enrich TCF-1-positive precursor exhausted TILs. [13]

**In-vitro generation begins with defined inputs:** antigen-specific systems repeatedly expose cells to cognate peptide, sometimes presented by dendritic cells, while antibody systems repeatedly engage the TCR complex through CD3 and provide CD28 costimulation. Cytokines maintain survival or expansion, and additional conditions can impose hypoxia or alter metabolism. These choices are part of the model’s causal structure, not interchangeable technical details.

| Representative system | Starting cells and principal input | Endpoint | Demonstrated output | Main experimental use |
|---|---|---:|---|---|
| Zhao et al., 2020 | Mouse OT-I; daily OVA peptide with IL-7/IL-15 | 5 days | Approximately ninefold expansion; dysfunction and methylation changes | Rapid perturbation and compound testing |
| P14 model, April 2023 preprint | Mouse P14; peptide-pulsed dendritic cells, repeated peptide/IL-2 | 7 days | Multireceptor phenotype; partial Tex regulatory program | Molecular benchmarking and genetic screening |
| Bommakanti et al., 2022 abstract | Human donor T cells; repeated CD3/CD28 stimulation | 10 days | Flow, cytokine, RNA, chromatin, and CRISPR readouts | Human epigenetic-regulator screening |

Protocol-specific evidence comes from the OT-I primary study [3], the publicly posted P14 study [4], and the human screening abstract [31].

**Cytokine details materially change interpretation:** Zhao et al.’s principal protocol used daily **10 ng/mL OVA peptide** with **5 ng/mL each of IL-7 and IL-15**, not simply a generic peptide-plus-IL-2 culture. The authors used these survival-supporting cytokines to limit activation-induced death; additional experiments showed exhaustion-associated features could also occur with IL-2. A cell surviving and differentiating under IL-7/IL-15 may follow a different balance of proliferation and death from one maintained under repeated IL-2-supported stimulation. [3]

**Generation differs from short-term restimulation:** a six-hour peptide or CD3/CD28 assay measures a previously isolated population’s response capacity; it does not generate exhaustion de novo. The same distinction applies to rescue cultures. A 2023 AML study, for example, tested freshly isolated patient bone-marrow or blood cells over five days; **two of seven** patient samples responded to a BET inhibitor or its combination with anti-PD-1. That is evidence about modulation of an existing dysfunctional population, not a five-day generation yield. [32]

### Time, yield, and sample access

**Two clocks determine the time comparison:** disease induction and maturation precede direct mouse isolation, whereas tissue processing and sorting occur after the cells already exist. Chen et al. isolated chronic-LCMV subsets **3–5 weeks after infection**, pooling **2–3 mice per CUT&Tag replicate**; CUT&Tag maps protein-associated chromatin using a targeted enzymatic assay. Human tissue collection follows clinical access and sampling opportunities rather than a standardized exhaustion-generation interval. [16][14]

**Tumor endpoints are model-specific:** Miller et al. profiled B16-OVA cells from days 10 and 20, with several subset assays using tumors around days 19–22. Martinez-Usatorre et al. harvested B16-OVA tumors on day 21. Other CAR-TIL experiments followed cells through tumor days 16, 20, and 24. These examples show why a blanket “more than 30 days in vivo” statement should not be applied to every tumor-isolation experiment. [2][19]

**Usable yield depends on the target subset:** Miller et al. generated single-cell profiles for **9,194 gp33-tetramer-positive cells** from day-28 chronic LCMV and **11,212 PD-1-positive/CD44-positive/CD8+ TILs** across day-10 and day-20 tumors. These are profiled-cell counts, not per-animal recovery estimates. Their methods also used **400-cell pools for RNA sequencing** and **5,000–50,000 sorted cells per chromatin-accessibility replicate**, providing concrete examples of achieved downstream assay scale. [2]

**Rare progenitors create a practical bottleneck:** Martinez-Usatorre et al.’s most enriched precursor gate represented approximately **3.5% of the analyzed endogenous or OT-I TIL populations**. Their transfer experiments pooled tumors from **6–10 mice** and injected **300 sorted cells per recipient condition**. In human melanoma work, Baitsch et al. demonstrated reproducible expression profiling from **1,000 sorted antigen-specific cells**, illustrating the value of low-input assays when expansion would change the state of interest. [13][14]

**Culture expansion gives an absolute anchor:** Zhao et al. seeded **0.5 million purified CD8+ cells per initial culture** and reported approximately ninefold expansion by day 5. The calculated estimate is therefore **0.5 million × 9 ≈ 4.5 million live cells per seeded culture**, across the expanded culture rather than a permanently unsplit well. This supports substantially sized downstream experiments without treating the result as a universal yield for every Tex-induction protocol. [3]

**Chronic stimulation can also restrict yield:** in the P14 benchmark, chronically stimulated cells plateaued below **three population doublings**, whereas acutely stimulated cells reached approximately **four doublings**. Repeated CD3/CD28 stimulation produced lower expansion and cellular yield than the antigen-specific culture in that comparison. Thus, scalability means the culture can be reproduced and enlarged; it does not mean exhausted cells intrinsically expand without constraint. [4]

### Mechanistic studies and cause-effect assignment

**Direct isolation is not inherently noncausal:** sorting alone documents an association between state and phenotype. However, conditional deletion, controlled infection, altered tumor antigen, or adoptive transfer can establish causal relationships in an intact physiological setting. Miller et al., for example, transferred OVA-specific progenitor Tex into tumors with or without OVA and showed that acquisition of a terminal phenotype depended on cognate antigen encounter. [2]

**Culture improves isolation of causal inputs:** investigators can hold cell source and stimulation constant while changing one gene, cytokine, receptor signal, oxygen condition, or metabolic intervention. Martinez et al.’s engineered-NFAT experiments used this advantage to examine binding behavior that was difficult to study directly in scarce mouse Tex. The authors specifically reported insufficient directly isolated material for in-vivo NFAT chromatin-immunoprecipitation sequencing. [15]

**The methods-choice judgment follows the claim:** use cultures to isolate mechanisms and support screening, direct samples to characterize disease-conditioned states, and in-vivo perturbations when the proposed causal relationship depends on the physiological environment.

## 5. Advantages and limitations of generating Tex in vitro

### Advantages: speed, scale, and controlled mechanisms

**Rapid induction broadens experimental access:** five- to ten-day models allow exhaustion-associated changes to be examined with repeated time points and multiple perturbations. They also permit matched acute-versus-chronic stimulation controls derived from the same starting population. This makes it easier to distinguish effects of continued stimulation from differences already present between animals, tissues, or patients. [3]

**Scale enables experiments beyond phenotyping:** greater cell supply supports RNA sequencing, chromatin-accessibility assays, protein studies, metabolomics, and genetic screens. RNA sequencing measures transcript abundance; assay for transposase-accessible chromatin sequencing, or ATAC-seq, measures DNA accessibility rather than transcription-factor binding itself. The April 2023 preprint explicitly describes the value of scalable cultures for large-input and perturbational experiments. [4]

**Human screening is an important extension:** Bommakanti et al.’s November 2022 conference abstract described repeated CD3/CD28 stimulation over **10 days** and an arrayed CRISPR knockout screen targeting **829 human epigenome-associated genes**, using cells from **three donors** as biological replicates. This demonstrates a practical scale of controlled human experimentation. Its evidence category remains a conference abstract, distinct from a full primary report with comparably extensive physiological testing. [31]

**Reductionism can establish a precise mechanism:** an engineered healthy-donor human CD8+ system varied PD-1 while controlling antigen-presenting-cell ligands. At intermediate PD-1 expression, IL-2-producing cells decreased by **more than 90%**, compared with a **60% decrease** in IFN-γ-producing cells. The experiment demonstrates that PD-1 signaling can differentially suppress outputs; it does not require the engineered cells to represent the complete exhausted lineage. [33]

**Epigenetic interventions become experimentally tractable:** Zhao et al. found greater methylation around the Tcf7 promoter in repeat-stimulated cells and showed that a DNA-methyltransferase inhibitor preserved higher TCF-1 expression. Because treatment occurred during induction, the most direct conclusion concerns prevention or alteration of developing exhaustion-associated programming, not proof of complete reversal of a mature tissue-derived Tex state. [3]

### Benchmarking reveals partial rather than uniform equivalence

**The P14 comparison quantifies the mismatch:** the publicly posted April 2023 study compared naïve P14 cells exposed to acute or repeated antigen stimulation with Tex from chronic LCMV. It reproduced sustained multireceptor expression, reduced expansion, and altered cytokine production. Yet the strengths of these features did not all match their in-vivo counterparts. [4]

| Feature | Acute P14 culture | Chronic P14 culture | Direct chronic-LCMV Tex |
|---|---|---|---|
| Five-receptor co-expression | Less than 10% | More than 50% | Approximately 30% |
| Expansion behavior | Approximately four doublings | Fewer than three doublings | Physiological proliferation–survival balance |
| Progenitor-associated program | Memory/precursor features retained | Weak progenitor signature | Progenitor and differentiated subsets |
| TOX induction | Low relative to Tex | Modest | Stronger sustained Tex-associated expression |
| Pdcd1 −23.8-kb enhancer | Not accessible in this comparison | Accessible | Accessible |

The receptor comparison concerns the day-7 culture endpoint, while the expansion comparison concerns the early culture trajectory; the chromatin and transcriptional comparisons are from the same [4].

**More checkpoints do not mean greater fidelity:** chronic culture overrepresented the five-receptor-positive state relative to the in-vivo benchmark while showing weaker induction of several regulatory components. By day 7, it upregulated genes including Pdcd1, Havcr2, Entpd1, Lag3, Cd244, and Tigit, but did not robustly express Cd160, Batf, Ctla4, Tox, and Nfatc1. A highly checkpoint-positive culture can therefore exaggerate one feature of exhaustion while incompletely reproducing another. [4]

**A shared enhancer is meaningful but local:** accessibility of the exhaustion-associated Pdcd1 enhancer demonstrates that chronic stimulation reproduces an important regulatory feature beyond surface PD-1 expression. However, the broader comparison also found different motif enrichments: in-vivo-specific regions favored NFAT and NFAT:AP-1-related features, whereas culture-specific regions favored other regulatory families, including Fli1 and RUNX. Agreement at one locus does not establish equivalence of the entire chromatin program. [4]

**Different culture systems capture different components:** Zhao et al.’s OT-I model showed increased TOX protein, decreased TCF-1, transcriptomic overlap with chronic-LCMV exhaustion, and persistence of several features after three days without peptide. Dunsford et al.’s 2020 human protocol reported sustained checkpoints and TOX together with progressive functional impairment and partial response to PD-1 blockade. These results support useful exhaustion models, while emphasizing that the phenotype depends on stimulation, cytokines, species, and starting cells. [3][34]

**The appropriate judgment is feature-specific:** cultures can convincingly model selected mechanisms even when they do not reproduce every property of directly isolated Tex; model quality should be judged against the particular physiological claim.

### Persistent antigen involves more than repeated stimulation

**Antigen exposure has several biological dimensions:** peptide concentration, encounter frequency, TCR affinity, presenting-cell identity, and duration all influence the response. Daily peptide addition models one form of persistence, whereas CD3/CD28 antibodies bypass antigen processing and peptide–MHC recognition. These approaches are useful precisely because they simplify the stimulus, but their simplification changes what can be inferred about physiological antigen recognition.

**Antigen presentation and costimulation are coupled:** tissue APCs provide changing combinations of peptide–MHC, inhibitory ligands, and costimulatory signals. A culture with fixed CD28 engagement can impose a different balance from an infected or malignant tissue where inhibitory receptors constrain access to effective costimulation. Likewise, supplying a checkpoint-blocking antibody is informative only if the corresponding receptor–ligand interaction contributes to the baseline culture state. [6]

**The antigen requirement has direct support:** Miller et al.’s transfer experiments separated tumor residence from cognate antigen encounter. OVA-specific progenitor cells differentiated toward a terminal phenotype in OVA-expressing tumors but maintained a progenitor phenotype in tumors lacking that antigen. This establishes an antigen-dependent transition within an intact tumor environment, rather than attributing every change simply to nonspecific tumor suppression. [2]

**Time compression can preserve only selected history:** chronic-LCMV transfer studies summarized in a 2020 review place progressive loss of plasticity and epigenetic fixation across approximately **14–30 days**, while some exhaustion-associated programming begins much earlier. A five-day culture can reproduce a mechanism that operates during this trajectory without reproducing the full sequence of exposure, selection, and stabilization experienced in vivo. [22]

**The antigen-model implication is narrow:** repeated stimulation tests the effects of that specified stimulation history; conclusions about physiological antigen kinetics become stronger when the same relationship holds under controlled changes in antigen presentation in vivo.

### Tissue architecture, migration, and accessory cells shape Tex

**Tissue niches distribute developmental opportunities:** in chronic-LCMV literature, progenitor-like cells preferentially occupy lymphoid environments, whereas differentiated cells are found in both lymphoid and nonlymphoid tissues. The 2020 Immune Network review discusses progenitor interactions in APC-rich T-cell zones and more differentiated-cell encounters in infected regions. These spatial relationships affect which signals a cell receives, how often it encounters antigen, and whether it remains in a renewal-supporting niche. [29]

**Cell suspensions erase physical relationships:** directly isolated cells retain molecular consequences of their tissue history, but dissociation itself removes architecture, neighboring cells, and local gradients. Thus, direct isolation is stronger than de-novo culture for recovering disease-conditioned states, while intact-tissue imaging and in-vivo experiments remain necessary for claims about localization or ongoing interactions. Miller et al.’s combination of sorting, transfer, and human tissue imaging illustrates how these different observations complement one another. [2]

**Macrophages provide a concrete missing input:** Kersten et al. tracked tumor-specific OT-I cells after recruitment into mouse tumors. Cells resident for 14 days upregulated PD-1, CD38, TOX, and CD5 and showed impaired cytokine responses. Depleting tumor-associated macrophages through CSF1R blockade reduced several exhaustion-associated markers and increased IFN-γ and TNF, while changing tumor size only modestly. This supports a myeloid contribution without reducing tumor control to one cellular interaction. [35]

**Human observations support environmental relevance:** in the same study’s **20-patient renal-cell-carcinoma cohort**, TIL PD-1 and CD38 expression correlated with the degree of myeloid differentiation toward macrophages rather than monocytes. The relationship used a macrophage-to-monocyte differentiation measure, not simply absolute macrophage abundance. This is a human association, while the experimental depletion evidence came from mice. [35]

**Cytokines can alter the regulatory module:** chronic infection and tumors provide inflammatory and suppressive mediators that a purified culture includes only if deliberately supplied or produced by its component cells. Zhao et al. noted that their culture did not reproduce some tumor-associated co-inhibitory components, including PROCR and podoplanin, and discussed the relevance of IL-27-dependent environmental programming. This illustrates a genuine distinction between shared exhaustion features and disease-specific additions. [3]

**The tissue-model implication is consequential:** a purified culture is well suited to cell-intrinsic questions, but a result involving migration, niche maintenance, or myeloid regulation depends on interactions that cell-intrinsic stimulation alone does not reproduce.

### Oxygen, nutrients, and mitochondrial stress act jointly

**Environmental stresses interact rather than add independently:** the continuous-stimulation/hypoxia experiments show that a culture can produce functional effectors under either input alone and dysfunctional cells under their combination. The relevant mechanism is therefore an interaction between stimulation demand and the capacity to support mitochondrial adaptation, not simply a larger dose of generic stress. [18]

**Uniform media remove physiological competition:** replenished culture medium and uniform oxygen conditions simplify the varying resource availability encountered in tissue. Tumor cells, stromal cells, and immune cells coexist in environments with local oxygen and nutrient constraints. The June 2023 hierarchical review identifies hypoxia, low pH, insufficient nutrients, and stromal influences as interacting contributors to exhaustion-associated metabolism. These conditions change the interpretation of a metabolic intervention that appears beneficial under well-supported culture conditions. [30]

**Causal metabolic rescue supports the mechanism:** Scharping et al. found that PGC-1α overexpression diverted TILs away from terminal-exhaustion-associated gene sets, while cells entering less-hypoxic engineered B16-F10 tumors shifted toward effector/memory states. Yu et al. likewise reported improved mitochondrial fitness and enhanced anti-PD-1 responsiveness following nicotinamide riboside supplementation in their tumor-exhaustion models. These experiments connect metabolic state to function, but through particular interventions and environments. [18][25]

**The metabolic-model implication is conditional:** a culture suited to receptor-driven fuel switching may not predict an intervention’s effect on hypoxic tissue Tex; that judgment changes when the relevant resource constraints and mitochondrial defects are present in the experimental comparison.

### Heterogeneity and prior history change what a culture represents

**Bulk resemblance can conceal subset loss:** the chronic P14 culture enriched for terminal-like transcriptional features while weakly representing the progenitor program. That makes it useful for selected differentiated-cell mechanisms, but less representative of a complete response maintained by progenitors, intermediates, and terminal descendants. A treatment requiring a progenitor reservoir may behave differently in such a culture even when its direct target is expressed. [4]

**Three labels simplify a richer population:** Giles et al.’s longitudinal mouse single-cell RNA and chromatin analysis identified multiple TCF-1-positive stem/progenitor-like subsets and a Zeb2-dependent population expressing natural-killer-cell-associated genes. Beltra et al.’s four-subset analysis likewise resolved developmental and localization differences within the broader progenitor-to-terminal sequence. A culture with a uniform endpoint does not automatically reproduce this mixture or its developmental relationships. [36][10]

**Apparent recovery may reflect selective survival:** in a 2021 mouse antigen-withdrawal study, approximately **tenfold more donor cells** were recovered after four weeks from transferred TCF-1-positive progenitor Tex than from TCF-1-negative terminal Tex. The terminal-derived progeny retained higher TOX and EOMES, lower TCF-1, and more inhibitory-receptor co-expression. A changed population average after resting can therefore reflect survival of a different subset rather than reprogramming of each terminal cell. [37]

**Regulatory history can survive antigen removal:** the same study identified **666 open-chromatin regions** more accessible in recovering Tex than in conventional memory cells; **526**, or approximately **79%**, also showed greater accessibility in Tex than memory cells. These residual regions were interpreted as exhaustion-associated chromatin scars. Functional improvement after antigen withdrawal therefore need not imply restoration of a conventional memory identity. [37]

**Human viral suppression gives a related contrast:** Buggert et al. observed persistence of the HIV-specific T-bet-dim/EOMES-high pattern and associated features despite long-term suppressive antiretroviral therapy, including a group treated for more than ten years. This does not establish the same mechanism as a controlled mouse antigen-withdrawal experiment, but it argues against assuming that reducing circulating virus rapidly erases the prior T-cell state. [8]

**The history-model implication is decisive:** cells newly induced from naïve or healthy-donor inputs model acquisition under defined conditions, whereas cells isolated from chronic disease also embody previous selection, survival, treatment, and epigenetic history.

### Functional rescue is different from complete reversal

**Removing tissue inhibition can reveal latent capacity:** Baitsch et al. reported that melanoma-derived tumor-specific cells with poor cytokine production could regain IFN-γ responses after short-term culture. A primary 2020 chronic-LCMV study similarly found strong transcriptional inducibility after six-hour CD3/CD28 restimulation: **429 genes** changed similarly in acute- and chronic-derived cells, with only **35 genes** remaining differentially expressed between the stimulated populations under that study’s criteria. These observations show that ex-vivo conditions can mask the extent of inhibition operating in tissue. [14][20]

**Transient rescue does not erase identity:** an improvement in IFN-γ, receptor expression, or short-term proliferation can occur without restoring durable recall or the memory-associated chromatin landscape. Conversely, residual exhaustion-associated chromatin does not imply that no useful functional improvement is possible. These are separate outcomes and should be reported separately.

**Checkpoint treatment can change population composition:** in Miller et al.’s tumors, anti-PD-1 expanded progenitors and promoted their differentiation while producing relatively limited changes to the underlying transcriptional and epigenetic states. Importantly, the proportion of terminally differentiated cells could rise after effective treatment because progenitors generated more cytotoxic descendants. A lower “terminal Tex percentage” is therefore not a necessary signature of benefit. [2]

**The therapeutic inference should match the endpoint:** a culture assay can demonstrate receptor blockade, prevention of developing dysfunction, expansion of a subset, or recovery of a particular function. Claims of complete reversal require a broader change in durable state and behavior than any one of these endpoints establishes.

### Choosing the model for the biological decision

**The strongest use is question-specific:** the relevant distinction is not whether a system is globally “a Tex model,” but whether its demonstrated biology supports the proposed conclusion.

| Biological question | Most informative starting point | Reasoned decision |
|---|---|---|
| What state exists in a patient or tissue? | Direct isolation plus tissue context | Preserve disease-conditioned identity |
| Which input causes a defined cellular change? | Controlled in-vitro induction | Separate candidate causal variables |
| What maintains progenitor-to-descendant dynamics? | Direct subsets with transfer or in-vivo perturbation | Preserve developmental relationships |
| Which compounds or genes merit mechanistic testing? | Scalable, benchmarked culture | Enable parallel perturbation |
| Will an intervention work physiologically? | Disease-relevant in-vivo or direct-tissue evidence | Include environment and population effects |

**Physiological agreement would change the judgment:** a culture that reproduced the relevant direct-Tex subset composition, receptor distributions, regulatory circuitry, broad chromatin state, metabolic fitness, and durable response behavior would support stronger physiological inference for that setting. Adding tissue components or three-dimensional organization is not sufficient by itself; the deciding evidence is whether those additions reproduce the biological relationship being claimed.

**Evidence interpretation remains model-specific:** expression labels are qualitative cross-study summaries, and transcript abundance, protein staining, enhancer motifs, and inferred regulon activity measure different properties. Direct-isolation numbers above are identified assay inputs or profiled populations rather than standardized recoveries; the approximately 4.5-million-cell culture output is a calculated estimate from the sourced input and ninefold expansion. Receptor percentages can overlap, and functional percentages retain their stated assay denominators. Reviews provide synthesis, while the April 2023 P14 work and November 2022 human screen are treated according to their pre-cutoff preprint and conference-abstract status.

**The overall research judgment is complementary:** in-vitro Tex generation is particularly valuable for scalable, controlled tests of exhaustion-associated mechanisms. Direct isolation remains more informative about the states that actually develop in chronic infection and cancer. The most reliable conclusions distinguish the mechanism a culture reproduces from the physiological processes—especially niche organization, environmental stress, subset renewal, and prior history—that determine how that mechanism operates in vivo.

## References

[1] <https://www.nature.com/articles/s41586-019-1325-x> TOX programming of exhaustion; TOX induction and maintenance; TOX-dependent developmental commitment
[2] <https://senlab.mgh.harvard.edu/wp-content/uploads/2020/12/Miller-Sen-et-al-2019.pdf> Functional specialization of exhausted subsets; tumor-subset transfer experiments; Subset-specific PRDM1 regulation; Subset-specific functional measurements; C…
[3] <https://journals.plos.org/plospathogens/article?id=10.1371%2Fjournal.ppat.1008555> Five-day functional induction model; OT-I culture conditions and survival rationale; Seeded input and measured expansion; Five-day OT-I model; Tcf7 methylation…
[4] <https://www.biorxiv.org/content/10.1101/2023.04.17.537229v1.full-text> pre-July public P14 chromatin benchmark; P14 expansion benchmark; Scalable in-vitro Tex analysis; Pre-July public P14 comparison; P14 benchmark; Phenotypic–tra…
[5] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7317876/>
[6] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5225559/> PD-1 signaling synthesis; CTLA-4 competition and cell-extrinsic effects; TIGIT–CD226 regulation; Receptor-specific checkpoint biology; 2B4 signaling context; C…
[7] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8896520/> PD-1 during activation and memory formation
[8] <https://journals.plos.org/plospathogens/article?id=10.1371/journal.ppat.1004251> Human HIV-associated differentiation and exhaustion; T-box regulation in chronic infection and human HIV; Human receptor co-expression; Human cytotoxic markers…
[9] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6943829/> TCF-1-centered fate regulation; TCF-1 loss- and gain-of-function evidence; Day-8 protein-level comparison
[10] <https://www.cell.com/immunity/fulltext/S1074-7613(20)30172-2> Developmental relationships among four Tex subsets; four-subset developmental analysis
[11] <https://www.nature.com/articles/s41590-020-0760-z> Early precursor programming under high antigen; Mouse precursor-fate experiments
[12] <https://journals.plos.org/plosone/article?id=10.1371%2Fjournal.pone.0144826> IRF4 and chronic antiviral responses; IRF4 regulation of the T-box balance
[13] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2020.00340/full> TOX-dependent persistence; persistence under chronic stimulation; Precision isolation of precursor Tex; Rare precursor sorting
[14] <https://doi.org/10.1172/jci46102> Human melanoma blood–tissue comparison; clinical melanoma sampling; human low-input profiling; Human short-term functional recovery
[15] <https://pmc.ncbi.nlm.nih.gov/articles/PMC4346317/> NFAT perturbation experiments; Engineered partnerless-NFAT study; NFAT mechanism; Controlled NFAT mechanism and input constraints
[16] <https://www.nature.com/articles/s41590-021-00965-7> BATF-dependent progenitor-to-effector transition; Chronic-LCMV isolation timing
[17] <https://www.nature.com/articles/s41417-022-00495-w>
[18] <https://www.nature.com/articles/s41590-020-00834-9> hypoxic mitochondrial mechanism; Continuous stimulation under hypoxia; Antigen–hypoxia interaction; ROS-linked dysfunction; Combined antigenic and hypoxic stre…
[19] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6589758/> NFAT–TOX/NR4A feedback; Mouse perturbations and human melanoma associations; NR4A in exhaustion circuitry; CAR-TIL time course
[20] <https://www.nature.com/articles/s41467-020-18256-4> Checkpoint mechanisms in chronic infection; In-vivo suppression of TCR signaling; mouse restimulation-induced transcription
[21] <https://pdfs.semanticscholar.org/be8a/ec2243a0a03924118b1b18b3663aa7bc5fb0.pdf> Human and mouse CD39 evidence
[22] <https://www.mdpi.com/1422-0067/21/19/7357> Cross-model functional synthesis; Residual activities across exhaustion models; Antigen history and progressive fixation
[23] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9008220/> Metabolic regulation of exhaustion
[24] <https://www.nature.com/articles/ncomms7692> primary PD-1 metabolic experiments; PD-1-driven metabolic reprogramming; Comparative receptor and pathway perturbations
[25] <https://www.nature.com/articles/s41590-020-0793-3> primary mitochondrial-quality experiments; Mitochondrial fitness and terminal exhaustion; Mitochondrial epigenetic effects; mitochondrial supplementation
[26] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10257143/> PRDM1-deficient CAR-T metabolic signatures; Human CAR-T PRDM1 study
[27] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9258987/> BATF enhancer and transition evidence
[28] <https://www.annualreviews.org/content/journals/10.1146/annurev-immunol-041015-055318>
[29] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7049579/> Stem-like subset synthesis; Spatial organization of exhausted subsets
[30] <https://doi.org/10.3389/fimmu.2023.1198551> June 2023 hierarchical synthesis; Microenvironmental regulation of exhaustion
[31] <https://doi.org/10.1136/jitc-2022-sitc2022.1405> Human epigenetic-regulator screen
[32] <https://doi.org/10.1038/s41375-023-01808-0> AML ex-vivo rescue experiments
[33] <https://www.pnas.org/doi/10.1073/pnas.1305394110> Controlled human PD-1-dose experiments
[34] <https://doi.org/10.1007/978-1-0716-0171-6_6> human antibody-stimulation protocol
[35] <https://escholarship.org/content/qt2nh5c95p/qt2nh5c95p_noSplash_dbeaa1fea17156d677208dd62353533f.pdf> Tumor residence and macrophage perturbation; Human renal-cancer myeloid association
[36] <https://doi.org/10.1038/s41590-022-01338-4> Longitudinal Tex heterogeneity
[37] <https://vahedilab.com/wp-content/uploads/2021/07/s41590-021-00975-5.pdf> Subset survival after antigen withdrawal; Persistent chromatin scars
[38] <https://www.scilit.com/publications/763efc181cd37ac49be05a064ace2710>
[39] <https://doi.org/10.1093/nar/gkab1030>
[40] <https://doi.org/10.1073/pnas.1914896116>
[41] <https://pmc.ncbi.nlm.nih.gov/articles/PMC3080775/>
[42] <https://www.ibiology.org/genetics-and-gene-regulation/transcription-factors/>
[43] <https://iris.unil.ch/entities/publication/a1e69e69-e012-44ff-82d9-3109740d38bf>
[44] <https://journals.plos.org/plosone/article?id=10.1371%2Fjournal.pone.0241421>
[45] <https://doi.org/10.14573/altex.2007141>
[46] <https://research.birmingham.ac.uk/en/publications/t-cell-response-to-checkpoint-blockade-immunotherapies-from-funda>
[47] <https://journals.sagepub.com/doi/10.1369/0022155414564219>
[48] <https://doi.org/10.3892/ijmm.2017.3080>
[49] <https://journals.plos.org/plosone/article?id=10.1371%2Fjournal.pone.0170628>
[50] <https://pubmed.ncbi.nlm.nih.gov/25820723/>
[51] <https://doi.org/10.3402/jev.v4.27031>
[52] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9277485/>
[53] <https://pmc.ncbi.nlm.nih.gov/articles/PMC3489771/>
[54] <https://doi.org/10.1007/s00421-010-1480-0>
[55] <https://doi.org/10.1177/2472555220923332>
[56] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6749960/>
[57] <https://minuth.app.uni-regensburg.de/PDF/Proceedings/2004_Minuth_TissueEngineering.pdf>
[58] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5624548/>
[59] <https://news.vumc.org/2023/08/03/study-finds-hallmarks-of-t-cell-exhaustion-within-hours-of-tumor-exposure/>
[60] <https://ecancer.org/en/news/23478-study-finds-hallmarks-of-t-cell-exhaustion-within-hours-of-tumour-exposure>
[61] <https://www.sciencedaily.com/releases/2021/07/210728201431.htm>
[62] <https://arxiv.org/html/2602.18885v1>
[63] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10375689/>
[64] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10361069/>
[65] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10225178/>
[66] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10850623/>
[67] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10591664/>
[68] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10570208/>
[69] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7615097/>
[70] <https://jdc.jefferson.edu/mifp/84/>
[71] <https://my.clevelandclinic.org/health/body/24630-t-cells>
[72] <https://www.semanticscholar.org/paper/NFAT-proteins%3A-key-regulators-of-T-cell-development-Macian/6030714e5f20380aea322a4381c93fadd70dc661>
[73] <https://biocytogen.com/product/humanized-mouse-model-toxicology>
[74] <https://www.protocols.io/view/isolation-and-characterization-of-tissue-and-cell-de2f3gbn.pdf>
[75] <https://doi.org/10.1017/cbo9780511550089.046>
[76] <https://www.biorxiv.org/content/10.1101/2023.07.18.549489v2.full-text>
[77] <https://doi.org/10.1109/icarcv.2018.8581346>
[78] <https://doi.org/10.1109/jstqe.2008.2010233>
[79] <https://doi.org/10.1109/jssc.2003.822774>
[80] <https://doi.org/10.1109/icsecompanion.2007.73>
[81] <https://doi.org/10.1161/01.cir.64.6.1227>
[82] <https://upcommons.upc.edu/bitstreams/0d21df39-e0d5-4604-9de1-817a0935801c/download>
[83] <https://doi.org/10.1007/s11095-025-03979-0>
[84] <https://doi.org/10.1017/ehs.2024.33>
[85] <https://doi.org/10.21203/rs.3.rs-10594510/v1>
[86] <https://www.drugtargetreview.com/exploring-alternatives-to-animal-testing-in-drug-discovery/600640.article>
[87] <https://aspe.hhs.gov/sites/default/files/documents/2d5c0a194c180b52d1c760d3bb09f70a/Biosimilars%20Final%20Report_250825_v508.pdf>
[88] <https://repository.ubn.ru.nl/bitstream/handle/2066/290916/290916.pdf?sequence=1>
[89] <http://arxiv.org/abs/2505.11894v1>
[90] <http://arxiv.org/abs/2403.12117v2>
[91] <https://www.acquisition.gov/caac/2025-01>
[92] <https://doi.org/10.7717/peerj.9478/fig-2>
[93] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7286441/>
[94] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2018.02569/full>
[95] <https://www.mdpi.com/2079-7737/12/4/541>
[96] <https://www.news-medical.net/whitepaper/20220307/Understanding-and-analyzing-T-Cell-exhaustion.aspx>
[97] <https://www.cancer.gov/publications/dictionaries/cancer-terms/def/t-cell-exhaustion>
[98] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10257143/>
[99] <https://www.rndsystems.com/resources/blog/immunology-news-researchers-identify-nr4a-and-tox-transcription-factors-mediators-cd8-t-cell>
[100] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2023.990419/full>
[101] <https://sites.duke.edu/dukevirology/files/2020/03/TCF-1-Centered-Transcriptional-Network-Drives-an-Effector-versus-Exhausted-CD8-T-Cell-Fate-Decision.pdf>
[102] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8563372/>
[103] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2023.1149622/full>
[104] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9533227/>
[105] <https://api.unil.ch/iris/server/api/core/bitstreams/f2ad406e-1528-4779-974f-3f6e3f2b994d/content>
[106] <https://www.broadinstitute.org/publications/broad1036036>
[107] <https://www.caseyhein.com/wp-content/uploads/Molecular-and-cellular-insights-into-T-cell-exhaustion.pdf>
[108] <https://senlab.mgh.harvard.edu/wp-content/uploads/2020/12/Miller-Sen-et-al-2019.pdf>
[109] <https://www.nature.com/articles/s41590-022-01194-2>
[110] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2023.1198551/full>
[111] <https://www.cell.com/immunity/fulltext/S1074-7613(19)30488-1>
[112] <https://doi.org/10.1038/s41590-022-01338-4>
[113] <https://www.cancerbiomed.org/content/17/4/923>
[114] <https://pdfs.semanticscholar.org/be8a/ec2243a0a03924118b1b18b3663aa7bc5fb0.pdf>
[115] <https://acir.org/weekly-digests/2019/july/tox-is-so-exhausting>
[116] <https://doi.org/10.1126/science.1229620>
[117] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5739523/>
[118] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6237934/>
[119] <https://www.mdpi.com/2072-6694/12/8/2274>
[120] <https://www.pnas.org/doi/10.1073/pnas.2007224117>
[121] <https://www.nature.com/articles/s12276-021-00568-0>
[122] <https://doi.org/10.1002/eji.201141931>
[123] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8080584/>
[124] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2022.977394/full>
[125] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7866257/>
[126] <https://ichgcp.net/ru/clinical-trials-registry/publications/111418-molecular-and-cellular-insights-into-t-cell-exhaustion>
[127] <https://onlinelibrary.wiley.com/doi/10.1002/cyto.a.24496>
[128] <https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8460019/>
[129] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6880756/>
[130] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2023.1151632/full>
[131] <https://acir.org/journal-articles/memory-t-cell-exhaustion-and-tumor-immunity>
[132] <https://pmc.ncbi.nlm.nih.gov/articles/PMC3240133/>
[133] <https://bi.tbzmed.ac.ir/PDF/bi-12-337.pdf>
[134] <https://rcastoragev2.blob.core.windows.net/f06523d18f9ba6a20715fea1effb9f40/PMC6713202.pdf>
[135] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9297918/>
[136] <https://ncbi.nlm.nih.gov/pmc/articles/PMC7003858/>
[137] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6754306/>
[138] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6081269/>
[139] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2023.1166128/full>
[140] <https://academic.oup.com/intimm/article-pdf/34/11/547/46343939/dxac016.pdf>
[141] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10569258/>
[142] <https://journals.plos.org/plospathogens/article?id=10.1371%2Fjournal.ppat.1009892>
[143] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9792152/>
[144] <https://pmc.ncbi.nlm.nih.gov/articles/PMC2605166/>
[145] <https://www.cell.com/immunity/fulltext/S1074-7613(09)00319-7>
[146] <https://www.sciopen.com/article/10.20892/j.issn.2095-3941.2020.0338>
[147] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2020.00340/full>
[148] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2022.1074698/full>
[149] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8439596/>
[150] <https://gut.bmj.com/content/gutjnl/68/5/905.full.pdf>
[151] <https://gut.bmj.com/content/gutjnl/72/11/2123.full.pdf>
[152] <https://air.unipr.it/retrieve/e177fbc7-66f8-50b0-e053-d805fe0adaee/2017%20NM-99535_4_merged_1483541957.pdf>
[153] <https://www.cell.com/immunity/fulltext/S1074-7613(16)30294-1>
[154] <https://cmgm-new.stanford.edu/biochem/biochem230/papers2007/week6/PD1_LCMV.pdf>
[155] <https://ncbi.nlm.nih.gov/pmc/articles/PMC5840618/>
[156] <https://www.annualreviews.org/content/journals/10.1146/annurev-immunol-090222-110914>
[157] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7340326/>
[158] <https://www.tandfonline.com/doi/pdf/10.4161/onci.19856>
[159] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2019.03039/full>
[160] <https://doi.org/10.1038/s41577-019-0221-9>
[161] <https://insight.jci.org/articles/view/155534>
[162] <https://www.signalingsystems.ucla.edu/pubs/Mognol.pdf>
[163] <https://www.semanticscholar.org/paper/CD8-T-Cell-Exhaustion-During-Chronic-Viral-and-McLane-Abdel-Hakeem/0239372203803540e7400053a3e0a225630a8d9f>
[164] <https://immunenetwork.org/search.php?code=0078IN&id=10.4110%2Fin.2020.20.e2&vmode=PUBREADER&where=aview>
[165] <https://www.cell.com/immunity/fulltext/S1074-7613(17)30416-8>
[166] <https://journals.plos.org/plospathogens/article?id=10.1371%2Fjournal.ppat.1000947>
[167] <https://doi.org/10.3389/fimmu.2013.00455>
[168] <https://doi.org/10.4049/jimmunol.1000841>
[169] <https://pmc.ncbi.nlm.nih.gov/articles/PMC2947065/>
[170] <https://doi.org/10.1038/s41467-020-18256-4>
[171] <https://doi.org/10.3389/fimmu.2023.1198551>
[172] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2023.1117092/full>
[173] <https://ncbi.nlm.nih.gov/pmc/articles/PMC3946600/>
[174] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5225559/>
[175] <https://ncbi.nlm.nih.gov/pmc/articles/PMC4889009/>
[176] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7608527/>
[177] <https://www.frontiersin.org/journals/endocrinology/articles/10.3389/fendo.2020.624122/full>
[178] <https://acir.org/weekly-digests/2019/march/nr4a-transcription-factors-control-t-cell-dysfunction-programs>
[179] <https://www.biorxiv.org/content/10.1101/767566v1.full-text>
[180] <https://www.nature.com/articles/ni.2035>
[181] <https://pmc.ncbi.nlm.nih.gov/articles/PMC3946600/>
[182] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5557644/>
[183] <https://www.sciopen.com/article/10.1038/s41368-022-00160-w>
[184] <https://doi.org/10.1146/annurev-med-012017-043208>
[185] <https://doi.org/10.1038/nature14468>
[186] <https://doi.org/10.1093/intimm/dxac050>
[187] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9376159/>
[188] <https://doi.org/10.1126/science.aae0491>
[189] <https://pmc.ncbi.nlm.nih.gov/articles/PMC3990591/>
[190] <https://journals.plos.org/plospathogens/article?id=10.1371%2Fjournal.ppat.1008555>
[191] <https://doi.org/10.1038/s41590-020-0760-z>
[192] <https://www.bdbiosciences.com/content/dam/bdb/marketing-documents/BD-T-cell-Exhaustion-White-Paper.pdf>
[193] <https://doi.org/10.1038/s41556-022-00942-8>
[194] <https://vahedilab.com/wp-content/uploads/2021/07/s41590-021-00975-5.pdf>
[195] <https://ncbi.nlm.nih.gov/pmc/articles/PMC2605166/>
[196] <https://journals.plos.org/plosone/article?id=10.1371%2Fjournal.pone.0047648>
[197] <https://pmc.ncbi.nlm.nih.gov/articles/PMC4669840/>
[198] <https://www.science.org/doi/10.1126/sciimmunol.adg3868>
[199] <https://www.biorxiv.org/content/10.1101/846048v1.full-text>
[200] <https://pmc.ncbi.nlm.nih.gov/articles/PMC2883597/>
[201] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2013.00455/full>
[202] <https://www.med.upenn.edu/pici/t-cell-exhaustion-pre-clinical-model.html>
[203] <https://www.cell.com/immunity/fulltext/S1074-7613(19)30409-1>
[204] <https://doi.org/10.1126/sciimmunol.aay0555>
[205] <https://www.researchgate.net/publication/338419151_A_Human_In_Vitro_T_Cell_Exhaustion_Model_for_Assessing_Immuno-Oncology_Therapies>
[206] <https://www.cell.com/immunity/pdfExtended/S1074-7613(16)30281-3>
[207] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2015.00310/full>
[208] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10232978/>
[209] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2022.926714/full>
[210] <https://inplainenglishpod.org/wp-content/uploads/2022/10/cd8-t-cell-exhaustion-during-chronic-viral-infection-and-cancer.pdf>
[211] <https://doi.org/10.1172/jci46102>
[212] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9197228/>
[213] <https://doi.org/10.1128/jvi.00889-12>
[214] <https://www.pnas.org/doi/10.1073/pnas.1305394110>
[215] <https://www.sciencedirect.com/science/article/abs/pii/S1879625720301000>
[216] <https://pmc.ncbi.nlm.nih.gov/articles/PMC4837657/>
[217] <https://www.semanticscholar.org/paper/TOX-and-TOX2-transcription-factors-cooperate-with-T-Seo-Chen/5c8d184595f2212ba192b983a33de193fac9a8e8>
[218] <https://escholarship.org/content/qt31b0283w/qt31b0283w.pdf>
[219] <https://doi.org/10.1016/j.celrep.2016.06.078>
[220] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7808153/>
[221] <https://journals.plos.org/plosone/article?id=10.1371%2Fjournal.pone.0188882>
[222] <https://doi.org/10.1371/journal.pone.0020107>
[223] <https://www.broadinstitute.org/publications/broad500776>
[224] <https://link.springer.com/article/10.1186/s13073-020-00722-9>
[225] <https://pmc.ncbi.nlm.nih.gov/articles/PMC3382859/>
[226] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7175802/>
[227] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6913881/>
[228] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8330547/>
[229] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7121329/>
[230] <https://ncbi.nlm.nih.gov/pmc/articles/PMC3248546/>
[231] <https://doi.org/10.1016/j.celrep.2021.109120>
[232] <https://med.stanford.edu/content/dam/sm/shared/community/department-of-medicine/Immuno/JournalClub/2020-21/JC_012621.pdf>
[233] <https://greenleaf.stanford.edu/publications>
[234] <https://doi.org/10.1073/pnas.0610442104>
[235] <https://pmc.ncbi.nlm.nih.gov/articles/PMC3582823/>
[236] <https://doi.org/10.4049/jimmunol.182.1.171>
[237] <https://doi.org/10.1084/jem.20082731>
[238] <https://pubmed.ncbi.nlm.nih.gov/37131713/>
[239] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6943829/>
[240] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10153201/>
[241] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7027373/>
[242] <https://doi.org/10.1530/rep-14-0633>
[243] <https://doi.org/10.4049/jimmunol.170.1.400>
[244] <https://rupress.org/jem/article/213/9/1799/42121/Blimp-1-mediated-CD4-T-cell-exhaustion-causes-CD8>
[245] <https://doi.org/10.1242/dmm.031260>
[246] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8423639/>
[247] <https://doi.org/10.1007/s00262-021-02897-5>
[248] <https://www.upmcphysicianresources.com/news/080522-exhausted-t-cells>
[249] <https://ncbi.nlm.nih.gov/pmc/articles/PMC7121329/>
[250] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8718368/>
[251] <https://journals.plos.org/plosbiology/article?id=10.1371%2Fjournal.pbio.1001430>
[252] <https://mediatum.ub.tum.de/doc/1538141/document.pdf>
[253] <https://pmc.ncbi.nlm.nih.gov/articles/PMC2783637/>
[254] <https://pmc.ncbi.nlm.nih.gov/articles/PMC3104769/>
[255] <https://journals.plos.org/plospathogens/article?id=10.1371%2Fjournal.ppat.1008870>
[256] <https://www.mdpi.com/2072-6694/13/3/515>
[257] <https://doi.org/10.1101/641316>
[258] <https://doi.org/10.1038/s41590-021-00964-8>
[259] <https://doi.org/10.1126/scitranslmed.abo4997>
[260] <https://dash.harvard.edu/bitstreams/7312037d-a895-6bd4-e053-0100007fdf3b/download>
[261] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10618911/>
[262] <https://www.frontiersin.org/journals/immunology/articles/10.3389/fimmu.2025.1659077/full>
[263] <https://www.nature.com/articles/s42255-020-00280-9>
[264] <https://doi.org/10.1101/2021.12.16.472900>
[265] <https://www.ovid.com/journals/ejoi/fulltext/10.1002/eji.70205~t-cell-exhaustion-as-a-regulated-differentiation-programme>
[266] <https://www.ncbi.nlm.nih.gov/gene/21414>
[267] <https://www.urotoday.com/component/content/article/140641-blimp1-and-nr4a3-transcription-factors-reciprocally-regulate-antitumor-car-t-cell-stemness-and-exhaustion.html>
