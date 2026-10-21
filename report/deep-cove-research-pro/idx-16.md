# Machine-Learning-Based Materials Inverse Design: Main Methods and Key Databases Through Early 2024

**Materials inverse design begins with targets.** It starts from a desired property or function and seeks materials, compositions, structures, or microstructures that could deliver it—the reverse of forward prediction, which starts from a specified material and predicts its properties. Machine-learning approaches can usefully be organized into three overlapping categories: **exploration-based methods**, which screen or navigate candidate spaces; **model-based methods**, which learn representations or mappings for proposing candidates; and **optimization-based methods**, which explicitly improve a design objective. This distinction follows the central separation between chemical-space exploration and candidate evaluation described in the scholarly literature. [1]

**The principal data resources serve different purposes.** Materials Project, OQMD, AFLOW, and JARVIS primarily supply calculated structures and properties; NOMAD supplies raw and normalized atomistic calculations; Materials Cloud emphasizes datasets, workflows, and provenance; and the Crystallography Open Database supplies crystal structures. These resources support different stages of discovery rather than functioning as interchangeable collections.

**Scope and reading guide.** This global overview covers developments available through early 2024, including the Materials Project inventory published on February 15, 2024. Part One explains how the three method categories work, which algorithms they include, their advantages and disadvantages, and how to choose among them. Part Two provides database descriptions and official URLs, then explains how data type and provenance affect inverse-design research.

## Part One: Main Methods

### The three strategies at a glance

**The categories describe complementary design roles.** A useful starting point is the distinction among high-throughput virtual screening, generative models, and global optimization used by Noh and colleagues. These correspond approximately to the requested exploration-based, model-based, and optimization-based categories. The labels below are a practical organizing scheme, not three mutually exclusive mathematical families: reinforcement learning can explore and optimize, while a learned surrogate can support all three strategies. [1][2]

| Category | Principle and search space | Representative algorithms | Main advantages | Main disadvantages | Appropriate uses |
|---|---|---|---|---|---|
| Exploration-based | Screen a library or traverse allowed states | HTVS, active learning, RL, MCTS | Broad triage; adaptive exploration | Coverage or action-space bias; evaluation cost | Database screening; sequential structural design |
| Model-based | Learn a distribution, representation, or inverse mapping | GANs, VAEs, diffusion models, inverse networks, surrogates | Novel proposals; compact search; rapid inference | Training-data dependence; invalid or inaccurate outputs | New compositions, crystals, porous materials, metamaterials |
| Optimization-based | Iteratively improve an explicit objective | Genetic algorithms, BO, PSO, annealing, gradient methods | Direct property targeting; flexible constraints | Expensive evaluations; local convergence; parameter sensitivity | Composition, structure, microstructure, and experiment optimization |

**Algorithm names alone are insufficient.** A random forest predicting formation energy is a forward model, not a complete inverse-design method. It becomes part of inverse design when a workflow uses its predictions to select, generate, or modify candidates toward a specified target. Similarly, a genetic algorithm is not inherently machine learning: an ML-based implementation usually couples the optimizer to a learned property predictor, interatomic potential, latent representation, or adaptive data-acquisition process. [1]

### What materials inverse design means

**Forward prediction answers a different question.** Given a crystal structure, composition, polymer representation, or microstructure, a forward model predicts an output such as formation energy, band gap, conductivity, or stiffness. Inverse design instead asks which material representation should be selected to obtain a required output. The 2022 review *Inverse Design of Materials by Machine Learning* describes this as moving from desired properties into chemical space rather than from chemical space into properties. [3]

**The design variables depend on scale.** At the atomic level, they can include elemental identities, stoichiometry, lattice parameters, and atomic coordinates. For polymers, they can include building blocks, sequence, architecture, and composition. For architected materials, they can include beam connectivity, node positions, or geometric patterns. Consequently, inverse design encompasses both discovering a new chemical compound and designing a new arrangement of existing constituents. [3][4]

**Inverse design is usually non-unique.** Several materials can share a similar band gap, elastic modulus, or optical response. Mathematically, the forward map can be many-to-one, so a single target does not identify a unique structure. This makes the inverse problem ill-posed: additional constraints or preferences are needed to distinguish useful solutions. The literature therefore uses restricted search spaces, probabilistic generators, dimensionality reduction, and constrained optimization rather than assuming that a property predictor can simply be reversed. [3]

**Non-uniqueness changes neural-network training.** Suppose two distinct structures produce essentially the same response. A conventional inverse network trained to recover one exact structure from that response receives conflicting examples; averaging their design parameters may produce a structure that is not a useful solution. A tandem architecture addresses this by connecting an inverse network to a pretrained forward network and training the inverse component to reproduce the requested response, rather than requiring it to recover one particular original design. [5]

**Feasibility is part of the objective.** A material with an excellent predicted functional property may still be unstable, difficult to synthesize, or incompatible with a manufacturing process. For crystals, reasonable atomic separations, plausible compositions, thermodynamic stability, and structural validity can therefore be constraints alongside the target property. For architected materials, connectedness and manufacturability can matter as much as predicted mechanical performance. Lu and colleagues explicitly argue that property optimization and stability or formability must be considered together. [6][4]

**Stability measures require careful interpretation.** Negative formation energy means that a compound is favorable relative to its constituent elemental reference states; it does not establish stability against every competing compound. Energy above the convex hull measures the energetic driving force for decomposition into competing phases represented in the calculation. A small hull energy is therefore a useful screening quantity, but it does not by itself describe synthesis pathways or establish experimental accessibility. [7][1]

**Candidate quality has several distinct meanings.** Novelty asks whether a proposal differs from a reference dataset; chemical validity asks whether it passes specified chemical rules; structural validity asks whether it describes a physically meaningful arrangement; and stability and functional performance require their own evaluations. These distinctions are essential when reading generative-model results. A large number of novel compositions, for example, is a different achievement from producing distinct relaxed crystals with the target property. [8]

**Validation connects algorithms to discovery.** Learned models provide inexpensive guidance, while density functional theory, molecular simulations, finite-element calculations, and experiments provide progressively more direct tests of the proposed design. Density functional theory, or DFT, is an electronic-structure method widely used to calculate crystal energies and properties. Which evaluator is appropriate depends on the material and target: crystal stability requires different evidence from nonlinear mechanical response or an optical spectrum. [1]

**The central design task is selection.** A successful inverse workflow does not merely produce plausible-looking outputs; it identifies feasible candidates that satisfy a defined purpose and subjects them to an appropriate physical test.

### Exploration-based methods

**Exploration-based methods navigate a specified space.** They begin with a candidate library or a set of allowed design states and actions, then evaluate alternatives and allocate attention to promising regions. The simplest form is high-throughput virtual screening; adaptive forms use feedback to decide what to evaluate next. The defining question is: “Where should the search look?” [1][9]

| Method | Candidate representation | Selection mechanism | Typical role |
|---|---|---|---|
| High-throughput virtual screening | Existing or enumerated library | Filters and property ranking | Broad candidate triage |
| Active learning | Labeled and unevaluated candidates | Informative next evaluations | Improve a model efficiently |
| Reinforcement learning | States and permitted design actions | Learned reward-seeking policy | Sequential candidate modification |
| Monte Carlo tree search | Branching partial or complete designs | Reward-guided tree expansion | Large combinatorial or structural searches |

**High-throughput screening provides broad triage.** High-throughput virtual screening, abbreviated HTVS, evaluates a large collection against predefined requirements. Its usual sequence is to define the screening scope, calculate or predict relevant properties, and assess selected candidates experimentally. The collection can contain experimentally reported structures, computed structures, or hypothetical candidates enumerated through operations such as elemental substitution. [1]

**Computational funnels control screening cost.** A screening workflow commonly applies inexpensive filters first, then reserves demanding calculations for the surviving candidates. Simple composition rules or rapid ML predictions can eliminate poor prospects before more expensive structural relaxation or property calculations. This ordering matters because evaluating every candidate at the highest fidelity would often consume the available budget before the most promising part of the library was examined. [1]

**Several predictors can accelerate the funnel.** Representative algorithms include support-vector regression, which learns a regression function from descriptors; kernel ridge regression, which captures nonlinear relationships through a kernel; decision-tree ensembles and random forests; and crystal graph convolutional neural networks, which learn from atomic neighborhoods in periodic structures. Reported screening targets include melting temperature, bulk and shear modulus, band gap, formation energy, and formation enthalpy. These algorithms are evaluators inside the exploration workflow rather than independent candidate generators. [1]

**Published screening examples demonstrate substantial narrowing.** Noh and colleagues summarize work by Sendek, Reed, and collaborators that identified 21 lithium solid-electrolyte candidates from 12,831 lithium-containing Materials Project entries. They also describe Singh and colleagues’ identification of 43 photocatalysts for carbon-dioxide conversion from 68,860 Materials Project materials through a combined theoretical and experimental screening framework. These examples show how a broad collection can be reduced to a manageable set of application-specific prospects. [1]

**Library discovery can mean new functionality.** A compound already represented in a database may become a discovery candidate because its suitability for a new application was previously unrecognized. Conversely, a library can be expanded with hypothetical substitutions before screening. The important distinction is between discovering a useful role within a collection and discovering a structure that lies outside the collection’s construction rules; HTVS can accomplish the former directly, while the latter requires an additional proposal mechanism. [1]

**Active learning makes exploration selective.** Instead of labeling the entire candidate space, active learning chooses evaluations expected to be especially informative for the model. This is useful when property labels require costly simulations or experiments. In an inverse-design workflow, the resulting information can improve the reliability of later candidate ranking, especially near poorly represented regions. Active learning is thus a way to spend an evaluation budget strategically, not a guarantee that every selected candidate will have high performance. [1]

**Exploration and exploitation pursue different benefits.** Exploitation selects candidates already predicted to perform well; exploration examines less understood regions that could contain better materials or correct misleading predictions. A strongly exploitative search can converge quickly within a familiar region but overlook a different structural family. Excessive exploration spreads the budget across many uncertain possibilities and may delay useful discoveries. Tree-search and uncertainty-aware approaches make this trade-off explicit. [9]

**Reinforcement learning learns sequential design choices.** In reinforcement learning, or RL, an agent observes a state, takes an action, receives a reward, and learns a policy for subsequent actions. In materials design, a state can describe a composition or structure; an action can alter a constituent, position, or geometric feature; and the reward can reflect a calculated property or a combination of performance and feasibility. A deep RL implementation uses neural networks to represent the policy or action values. [10]

**The environment supplies physical feedback.** The agent’s environment can be a simulation, experiment, or learned property evaluator. Reported applications include tough graphene oxide, continuum composite materials, and porous graphene for water desalination. These examples illustrate why RL is attractive for designs built through a sequence of dependent modifications: the algorithm can learn which actions are useful in a particular context rather than assigning every candidate an independent score. [10]

**Reward design determines learned behavior.** An agent rewarded only for the target property may repeatedly exploit a narrow family of high-scoring designs, while rewards incorporating stability or diversity can encourage different outcomes. The allowed actions also determine which materials can ever be reached. RL is therefore not inherently restricted to a fixed database, but it remains restricted by its state representation, action definitions, and evaluator. CASTING demonstrates this dependence through its explicitly defined atomic and lattice perturbations. [2]

**Monte Carlo tree search structures exploration.** Monte Carlo tree search, or MCTS, represents choices as branches in a tree and builds promising portions incrementally. A conventional iteration selects a branch, expands it, completes a trial design through a simulation or rollout, and propagates the resulting score back along the visited path. This avoids constructing the entire combinatorial tree and uses previous evaluations to guide subsequent sampling. MCTS can operate without a neural policy, although it can also be combined with learned models. [9]

**Atom-assignment studies illustrate query efficiency.** Dieb and colleagues’ 2019 review describes a copper–silver grain-boundary study in which MCTS reached the stable segregation configuration after examining 1% of the candidates for one boundary. For a larger boundary problem, the optimum was reached after exploring 0.34% of the search space. The same account reports that search order, search paths, and rollout choices affected efficiency—showing that representing and traversing the tree are consequential design decisions. [9]

**Continuous actions extend the approach.** Conventional materials MCTS implementations initially concentrated on discrete choices, such as assigning an atom to a lattice site. Banik and colleagues’ 2023 CASTING framework—Continuous Action Space Tree Search for Inverse Design—adapted MCTS through modified sampling and policies to continuous structural variables. Its moves include changing lattice parameters and atomic coordinates, as well as adding or removing composition-preserving units. [2]

**CASTING demonstrated high-dimensional structural searches.** Its silver scaling tests reached 774 variables, calculated as 256 atoms × 3 Cartesian coordinates + 6 lattice parameters. The authors reported a best-solution energy-difference range below 0.15 meV in their energy-per-atom comparison. These tests used an empirical interatomic potential and searches around known face-centered-cubic reference structures, establishing a specific scaling result rather than an accuracy claim for arbitrary DFT-driven discovery. [2]

**Search diversity can oppose fast convergence.** In CASTING’s carbon comparison, MCTS sampled more configurations close to low-energy solutions, while the genetic algorithm produced a more diverse set of polymorphs. Increasing the MCTS exploration constant broadened its search, whereas an excessively small constant confined attention to already favorable regions. Thus, “better exploration” depends on whether the research goal is one best structure or a diverse collection of useful metastable structures. [2]

**The main advantages are accessibility and throughput.** HTVS makes effective use of existing datasets, permits understandable screening criteria, and supports parallel evaluation. Adaptive exploration can reduce wasted queries, and RL or MCTS can navigate spaces too large for exhaustive enumeration. Compared with training a general crystal generator, these approaches can also exploit a relatively narrow, well-defined design representation. [1][9]

**The main disadvantages concern coverage and feedback.** Static HTVS cannot select a candidate absent from its library, and template-based enumeration inherits the templates’ structural restrictions. Adaptive approaches replace this boundary with dependence on allowed actions, search order, and exploration settings. All remain vulnerable to expensive evaluations or misleading property predictions; a fast selection algorithm offers limited practical benefit when each rollout requires a very long experiment or simulation. [3][9]

**Practical judgment favors well-defined search spaces.** Exploration-based methods are strong choices for curated-library screening and sequential structural searches; move toward a different proposal mechanism when the library or allowed actions exclude the materials the application requires.

### Model-based methods

**Model-based methods learn how designs are organized.** Their central contribution is a learned relationship between material representations, properties, and plausible candidates. A generative model learns a distribution from which new candidates can be sampled; an inverse network maps requested responses to design variables; and a surrogate approximates the forward property calculation. The inverse-design workflow emerges when these learned components are conditioned, sampled, inverted, or coupled to search. [1][5]

| Model family | Learned object or role | How targets guide design | Main advantage | Main difficulty |
|---|---|---|---|---|
| Direct inverse or tandem network | Response-to-design mapping | Requested response enters inverse network | Rapid design recommendation | Non-unique solutions; surrogate errors |
| Forward surrogate | Design-to-property mapping | External search or input optimization | Inexpensive candidate evaluation | Extrapolation and error exploitation |
| GAN | Distribution of plausible candidates | Conditions, penalties, or property predictor | Efficient novel sampling | Training instability; incomplete coverage |
| VAE or semi-supervised VAE | Probabilistic latent representation | Property-conditioned latent search | Compact, continuous design space | Invalid decoding; posterior collapse |
| Diffusion-based model | Iterative denoising process | Conditions or property-related training | Flexible structural generation | Physical validity and relaxation cost |
| RNN-based generator | Sequential material representation | Conditional generation or reward feedback | Natural sequence construction | Representation and sequence validity |

**Learned generation differs from enumeration.** Enumeration creates candidates from explicit rules, such as substituting elements into known prototypes. A generative model instead learns statistical regularities from examples and uses them to produce additional representations. This can fill gaps between known materials and propose structures beyond a fixed library, but the learned distribution still reflects what the training set contains and how the representation encodes it. [1]

**Property control makes generation purposeful.** An unconditional generator answers “What resembles the training data?” rather than necessarily “What meets this target?” Desired properties can enter as conditioning variables, additional training losses, property-prediction branches, or objectives for searching the learned latent space. Another route is to train on a property-selected subset and thereby bias sampling toward that subset. These mechanisms provide different degrees of control and should not be treated as equivalent. [6][8]

**Inverse networks provide fast recommendations.** Once trained, a direct inverse network can return design parameters from a desired response with little additional computation. Tandem networks improve handling of non-uniqueness by assessing whether the proposed design’s predicted response matches the target. Their practical strength is repeated design within a sufficiently well-covered domain; their weakness is that the forward network remains the judge, so errors in that network can become errors in the recommended design. [5]

**Surrogates accelerate rather than complete inversion.** Gaussian processes, random forests, deep neural networks, and graph neural networks can replace expensive property evaluations during design. For example, MEGNet graph-network models have been used to evaluate properties while an optimizer changes materials-design variables. The surrogate supplies the structure–property relationship; the optimizer or generator supplies the target-directed proposal process. Keeping these roles separate makes a method description much more informative than simply calling the entire workflow “neural-network inverse design.” [10]

**GANs learn through adversarial competition.** A generative adversarial network, or GAN, contains a generator that maps random latent inputs into candidate representations and a discriminator that distinguishes generated examples from training examples. Alternating training encourages the generator to reproduce statistical features of the real data. Conditional GANs and property-penalized variants add target information, while Wasserstein GANs alter the distribution-comparison objective to improve training behavior. [8]

**MatGAN demonstrated composition-space generation.** Dan and colleagues’ 2020 MatGAN learned inorganic compositional regularities from datasets including ICSD, Materials Project, and OQMD. In its ICSD-trained experiment, it reported 92.53% novelty when generating two million samples. A separately specified experiment using chemically filtered ICSD training data reported 84.5% of generated samples satisfying its charge-neutrality and electronegativity-balance criteria. These are study-specific sampling results, with different training conditions, rather than percentages that should be multiplied into one discovery yield. [8]

**Composition validity is not crystal prediction.** MatGAN’s outputs encode elemental compositions, not lattice vectors and atomic positions. A composition can possess multiple polymorphs with different properties, so a promising formula still needs structural prediction or an accompanying structure generator. The paper explicitly identifies this boundary and discusses combining its composition sampler with crystal-structure search methods. This is a useful example of a model that expands the proposal space without independently solving the whole materials-design problem. [8]

**Target-biased GAN sampling has several forms.** MatGAN also trained a generator on 30,186 Materials Project compounds with positive band gaps and evaluated generated compositions with a separate band-gap predictor. By contrast, ZeoGAN modified a generator’s loss to favor a desired methane adsorption-related property. The first approach biases sampling through the training population; the second adds an explicit property objective. In both, the property evaluator’s reliability affects whether statistical targeting translates into physical performance. [8][5]

**Porous-material generation shows structural reach.** Lu and colleagues summarize a GAN application that generated 121 novel crystalline porous materials from a training base of more than 30,000 known zeolites. Such systems are attractive for generative design because pore geometry and chemical structure influence adsorption and separation behavior. The result illustrates generation beyond the training list, while also showing that a successful representation can remain specialized to a particular material family. [6]

**VAEs create a probabilistic latent space.** A variational autoencoder, or VAE, uses an encoder to map a material representation into a lower-dimensional probability distribution and a decoder to reconstruct material representations from sampled latent vectors. Training balances reconstruction with regularization toward a chosen prior distribution. Unlike an ordinary compressed lookup table, the resulting continuous latent space can support interpolation, nearby sampling, and optimization. [1]

**Property prediction can organize that space.** A semi-supervised VAE adds a supervised branch that predicts a labeled property from the latent representation. The model is then encouraged to retain information relevant to both reconstruction and the target. A search can move toward latent regions associated with favorable formation energy, stiffness, or another response, after which the decoder produces explicit candidates. This is the mechanism that connects dimension reduction to inverse design rather than merely data visualization. [11]

**Architected materials provide a concrete example.** Zheng and colleagues’ 2023 truss study combined a VAE with a property predictor to convert discrete beam connectivity and continuous node geometry into a unified latent representation. The training collection contained 965,736 unique truss structures and finite-element-derived stiffness data. The study held relative density at 0.15, helping separate improvements in architecture from improvements obtained simply by adding material. [4]

**Reconstruction and generation measure different abilities.** In that study, adjacency-matrix reconstruction accuracy was 99.9%, and the property predictor achieved coefficients of determination of at least 0.982 across stiffness components on an independent test set. Yet random sampling of 1,000 latent points produced valid truss topologies in 82.3% of attempts. Accurate reconstruction of familiar examples therefore did not imply that every newly sampled point decoded into a meaningful structure. [4]

**Latent regularization creates a real trade-off.** Stronger regularization can make randomly sampled latent points easier to decode, but it can reduce fidelity when reconstructing individual structures. The truss study explicitly identified this balance and adjusted the regularization weight during training. For a researcher, the appropriate balance depends on purpose: faithful representation of known structures and reliable open-ended generation are related objectives, but they are not identical. [4]

**Diffusion models generate by progressive denoising.** Rather than producing a complete candidate in one decoding operation, a diffusion-based generator learns to transform noisy representations into structured samples through successive denoising steps. Lyngby and Thygesen’s 2022 materials study used a crystal diffusion variational autoencoder, or CDVAE, combining a variational representation with a diffusion decoder. Its networks included a periodic graph encoder, a predictor for structural quantities, and a noise-conditional decoder for atom types and coordinates. [12]

**CDVAE couples chemical and geometric information.** In the reported architecture, the encoder maps a crystal into latent space; another network predicts quantities including atom count, lattice vectors, and composition; and the decoder denoises atomic information into a periodic candidate. Its equivariant geometric treatment is designed so that changes such as rotating coordinates are handled consistently. For two-dimensional materials, the study introduced artificial periodicity in the non-periodic direction because the model had originally been designed for three-dimensional bulk crystals. [12]

**The two-dimensional study compared generation routes.** CDVAE was trained on 2,615 two-dimensional materials with energy above the convex hull below 0.3 eV per atom and produced 5,003 candidates for DFT relaxation. A lattice-decoration protocol, based on systematic elemental substitution, produced another 14,192 candidates. Across the two workflows, the study reported 11,630 predicted new two-dimensional materials, including 8,599 meeting the seed-material stability threshold and 2,004 within 50 meV per atom of the convex hull. The combined total should not be attributed to CDVAE alone. [12]

**Broader generation came with more failures.** CDVAE reached crystal classes beyond the seed structures, whereas lattice decoration remained tied to seed stoichiometries and structural templates. However, about 31% of CDVAE-generated structures failed DFT relaxation, compared with about 18% for lattice decoration. This provides a direct novelty–robustness comparison: a generator can explore more structural possibilities while producing a larger fraction of candidates that fail the subsequent physical calculation. The authors also noted that failed relaxations could affect the apparent stability comparison. [12]

**Sequence models suit sequential representations.** Recurrent neural networks, or RNNs, generate a sequence one element at a time using information from previous elements. They have been applied to molecular inverse design, including encoder–decoder approaches that connect structural features and material properties to recognizable molecular representations. Their usefulness depends on an appropriate sequence representation; molecular strings are more naturally available than reversible strings for arbitrary periodic crystals. [3][1]

**Crystal representations remain a central difficulty.** A useful generative representation should be decodable into a structure and should handle physically equivalent descriptions consistently. Translation, rotation, atom ordering, and alternative unit-cell choices can change a numerical representation without changing the underlying material. Early image-based approaches could encode detailed structures but required post-processing and lacked exact rotational invariance; coordinate- and graph-based methods address different parts of this problem. [6]

**Invariance and equivariance solve related problems.** An invariant property representation gives the same result under a transformation that should not affect the property. An equivariant geometric model transforms its output consistently when its input is transformed. These ideas help prevent a model from spending capacity relearning arbitrary coordinate conventions. They do not, however, automatically enforce chemically sensible bonding, appropriate cell geometry, or stability; those still depend on the model, training data, and constraints. [1][12]

**Data coverage controls generative coverage.** Lu and colleagues emphasized that inorganic datasets contained roughly hundreds of thousands of compounds but comparatively limited structural diversity, with particularly sparse examples for some target properties. A model trained on such data may underrepresent unfamiliar chemical families even when it generates many samples. MatGAN similarly found difficulty generating a subset with composition rules poorly captured by its learned representation. More sampling therefore does not necessarily compensate for missing or unlearned material classes. [6][8]

**Collapse can undermine property control.** Posterior collapse occurs when a latent-variable model fails to use its latent representation effectively, weakening the intended relationship between latent position and generated candidate. Mode collapse or restricted sampling can reduce the variety of outputs. In the EVAPD perovskite study, these concerns motivated adding an evolutionary search component and geometric screening rather than relying solely on a property-organized VAE. [11]

**Surrogate errors can become attractive designs.** An optimizer repeatedly querying a learned predictor may find inputs where the predictor is overly optimistic rather than where the actual material is exceptional. This risk grows when designs move outside the initial training domain. The inverse-design literature consequently distinguishes interpolation within well-covered data from extrapolation into a much larger design space, and discusses active updating and transfer learning as ways to improve prediction along the search path. [5]

**The main advantages are proposal power and reuse.** Generators can propose candidates beyond an existing library, while latent representations can make a difficult discrete or high-dimensional problem easier to navigate. Once trained, inverse networks and surrogates provide rapid repeated inference. These strengths are particularly valuable when many target queries share a material class and representation, allowing the initial investment in data and training to support multiple design tasks. [1][5]

**The main disadvantages are learned-model dependence.** Data scarcity, narrow structural coverage, unstable training, invalid decoding, and inaccurate extrapolation can all restrict useful output. Some GAN-based property-design workflows also depend on a separately pretrained simulator, adding another learned component whose errors matter. The strongest case for model-based design is therefore not simply that it produces novel samples, but that its representation, target control, and physical evaluations work together effectively. [6][3]

**Practical judgment favors supported open-ended generation.** Choose model-based methods when proposing new compositions or structures is central and the training representation covers the relevant physics; favor narrower screening or adaptive search when data and decoding reliability are the dominant constraints.

### Optimization-based methods

**Optimization-based methods pursue an explicit objective.** They represent a candidate through design variables, evaluate its performance, and update those variables to improve a target. The evaluator may be an experiment, a physics calculation, a learned surrogate, or a combination. The essential question is: “Which candidate should be proposed next to improve the objective?” [1]

**Objectives must express the actual requirement.** Maximizing a property is different from matching a specified value or response curve. A solar material might require a useful band-gap interval rather than the largest possible band gap; a structural material might require stiffness at fixed density rather than stiffness without a mass constraint. The chosen objective therefore determines what the optimizer considers successful, and constraints determine which apparent improvements remain acceptable. [3][4]

**A standard formulation makes choices visible.** For target matching, one illustrative mathematical form is a weighted mismatch minimized over feasible designs:

$$x^\star=\operatorname*{arg\,min}_{x\in\mathcal F}\sum_{j=1}^{m}w_j\left[\frac{\hat p_j(x)-p_j^\star}{s_j}\right]^2.$$

Here, \(x\) represents design variables, \(\mathcal F\) is the feasible set, \(\hat p_j(x)\) is a predicted property, \(p_j^\star\) is its target, and \(s_j\) is a reference scale with the same units as that property. The scales prevent quantities measured in different units from being combined arbitrarily; the weights express preferences. This is a general explanatory formulation, not a reproduction of a particular study’s objective.

**Multi-objective design exposes trade-offs.** Stability and functional performance need not improve together, and strength, toughness, density, cost, or processing time can conflict. A weighted objective selects one compromise, whereas Pareto optimization seeks designs for which improving one objective would worsen another. Evolutionary methods and multi-objective Bayesian optimization can both operate in this setting. The result is often a set of useful alternatives rather than one scientifically unique “best material.” [1][5]

| Algorithm family | Update principle | Particularly suitable setting | Main difficulty |
|---|---|---|---|
| Genetic algorithm | Selection, crossover, and mutation | Discrete or mixed structural searches | Population cost; parameter sensitivity |
| Bayesian optimization | Surrogate plus acquisition function | Expensive evaluations; limited data | Surrogate mismatch; dimensionality |
| Particle swarm optimization | Personal and collective best positions | Parameterized derivative-free searches | Premature concentration; tuning |
| Simulated annealing | Temperature-controlled acceptance | Rugged discrete or continuous landscapes | Cooling and move choices |
| Minima hopping | Escapes between locally relaxed minima | Energy-landscape and crystal searches | Repeated relaxation cost |
| Gradient-based methods | Derivatives guide variable updates | Differentiable continuous representations | Local optima; discrete feasibility |
| Random or quasi-random search | Broad sampling under allowed rules | Baselines and relatively accessible spaces | Many unproductive evaluations |

**Genetic algorithms evolve candidate populations.** A genetic algorithm, or GA, treats each candidate as an individual whose encoded variables act as a chromosome. Selection favors higher-fitness individuals; crossover combines information from parents; and mutation introduces changes. For crystal search, individuals can represent atomic configurations, lattice variables, or compositions. In an ML-assisted implementation, predicted energies or properties can replace many costly direct evaluations. [1]

**Representation determines useful genetic operations.** Arbitrarily exchanging sections of a numerical vector may violate stoichiometry, create overlapping atoms, or destroy a structural motif. Effective implementations therefore use chemically or geometrically meaningful operators, constrain offspring, or repair candidates before evaluation. Mutation must also preserve sufficient diversity without making most offspring unproductive. These are reasons why a successful GA configuration in one materials problem does not automatically transfer to another. [3][11]

**Evolutionary search can leave existing databases.** Unlike library ranking, a structural GA can create configurations that have never appeared in a database. Noh and colleagues describe applications involving new crystal phases, magnetic materials, superhard carbon phases, and alloy nanoparticles. Nevertheless, some evolutionary workflows fix composition in advance, leaving the broader composition-selection problem to a separate model or search. This makes “global optimization” global only relative to the variables and bounds actually supplied. [1]

**Property evaluation often dominates total cost.** The Noh review cites an estimate that evaluations account for approximately 99% of evolutionary or global-optimization cost in the discussed setting. For platinum–gold nanoparticles, an on-the-fly Gaussian-process model reduced the required DFT calculations to 300, with a reported cost reduction of about 50-fold from using ML. The practical lesson is that improving the evaluator can matter more than reducing the optimizer’s own computational overhead. [1]

**Bayesian optimization spends expensive queries selectively.** Bayesian optimization, or BO, maintains a probabilistic surrogate for an expensive objective and uses an acquisition function to choose the next evaluation. After obtaining the result, it updates the surrogate and repeats. This combination makes BO particularly attractive when only a small number of experiments or demanding simulations can be afforded. [13]

**Acquisition functions value information as well as performance.** A candidate may be selected because its predicted property is excellent, because uncertainty leaves room for improvement, or because it combines both. For a maximization problem, an upper-confidence-bound rule has the general form \(a(x)=\mu(x)+\kappa\sigma(x)\), where \(\mu\) is predicted performance, \(\sigma\) is predictive uncertainty, and \(\kappa\) controls exploration. Expected improvement is another common choice, evaluating the potential to exceed the best observed result. [5]

**Optimization uses the surrogate differently from prediction.** A model with good average prediction accuracy may still rank the best candidates poorly or assign misleading uncertainty near a phase transition. BO performance therefore depends on whether the surrogate and acquisition function are suitable for the search landscape, not simply on whether the regression method is popular. Adaptive-surrogate work specifically addresses high-dimensional, sparse, or non-smooth material-design spaces where standard Gaussian-process assumptions can be restrictive. [13]

| BO surrogate | Representation of the objective | Useful characteristic | Principal concern |
|---|---|---|---|
| Gaussian process | Covariance-based function distribution | Prediction with posterior uncertainty | Kernel assumptions can be restrictive |
| Bayesian regression splines | Products of spline basis functions | Flexible shape and feature selection | Suitability depends on data and landscape |
| Bayesian additive regression trees | Sum of small regression trees | Flexible patterns and feature selection | Model and acquisition must work together |

**Surrogate choice changes evaluation efficiency.** In the adaptive-surrogate study, the MAX-phase example contained 403 stable phases. Searches for maximum bulk modulus used initial sample sizes of 2, 5, 10, 15, and 20, with 100 replicates per setting and an 80-evaluation budget. Bayesian additive regression trees and Bayesian multivariate adaptive regression splines generally reduced evaluation counts and gave more stable performance than the compared Gaussian-process-based alternatives. This demonstrates that changing the model within BO can be as consequential as choosing BO itself. [13]

**Categorical variables require meaningful treatment.** Materials choices often mix continuous quantities, such as concentration or geometry, with qualitative choices, such as element, solvent, or constituent type. Latent-variable Gaussian-process BO maps qualitative factor levels into learned quantitative coordinates rather than assuming that arbitrary numeric labels have physical distances. This permits joint optimization of categorical and continuous choices. [14]

**A perovskite example shows task-specific gains.** In a hybrid organic–inorganic perovskite problem containing 240 stable combinations with precomputed DFT binding energies, the latent-variable expected-improvement method found the exact optimum in 28 of 30 replicates. The dummy-variable comparison found it in 22 of 30. The result supports the value of representing qualitative variables appropriately; it is not a head-to-head ranking of BO against every other inverse-design strategy. [14]

**BO becomes harder as representations grow.** Sparse observations in a large design space can leave the surrogate unable to distinguish promising regions reliably. Abrupt property transitions can conflict with a smooth covariance model, while noisy results complicate the distinction between a genuine improvement and measurement variation. Acquisition optimization also has its own computational cost. Consequently, BO is especially compelling when evaluations are expensive and the design variables form a manageable, informative representation. [13][9]

**Particle swarms share promising search locations.** Particle swarm optimization, or PSO, maintains candidate positions and updates their movement using each particle’s own best result and favorable positions discovered by the swarm. It does not require derivatives and has been combined with ML predictors and physical simulations. Reported polymer applications include cloud-point engineering and multiblock-polymer morphology design; a cloud-point study predicted 17 polymer structures intended to meet specified targets. [3]

**Annealing and hopping traverse rugged landscapes.** Simulated annealing permits some unfavorable moves, especially at higher algorithmic temperatures, helping a search cross barriers before becoming more selective. Minima hopping combines local relaxation with moves intended to escape the current energy basin. These approaches are useful when many local minima correspond to distinct structural possibilities, but their success depends on move definitions, schedules, and the cost of repeatedly relaxing candidates. [1]

**Gradient methods exploit differentiable structure.** Gradient descent changes continuous design variables in a direction that reduces an objective; Newton–Raphson and related Newton-type approaches use derivative information, including curvature when applied to minimization. Neural-network surrogates and continuous latent spaces make derivatives accessible through automatic differentiation. This can be efficient for geometry, optical-layer thicknesses, or latent vectors, provided the relevant mapping is differentiable. [5]

**Training gradients and design gradients differ.** During model training, optimization changes network weights to fit data. During inverse design through a trained forward model, the weights can be fixed while gradients change the input design variables. Peurifoy and colleagues’ nanoparticle example, discussed in the inverse-design methods review, used this approach to select layer-thickness combinations for desired light-scattering spectra. Calling ordinary network training “materials inverse design” misses this important distinction. [5]

**Differentiability does not remove physical constraints.** Atomic species, beam connectivity, and some property labels are discrete, so continuous updates may require relaxation, thresholding, or decoding. Those operations can change the candidate represented by the optimized vector. In the truss study, the authors used an additional decoding–encoding route to maintain meaningful designs and checked final properties with finite-element calculations. Gradient-based methods can also converge near their initial conditions rather than reaching the most useful region of a non-convex space. [4][10]

**Random search remains an important comparison.** Random or quasi-random sampling can be useful when evaluation is cheap, the representation is constrained by strong physical rules, or a baseline is needed to establish whether a sophisticated method earns its complexity. The Noh review describes successful random structure-search applications alongside more elaborate global optimizers. The relevant comparison is not sophistication of the algorithm’s name, but how many useful, distinct candidates it finds for the actual evaluation budget. [1]

**The main advantages are explicit direction and flexibility.** Optimization directly incorporates the desired response, can handle constraints and multiple objectives, and can create candidates beyond existing collections. Derivative-free methods accommodate black-box evaluators, gradients exploit smooth structure, and BO can economize expensive queries. These advantages explain why optimization is frequently combined with both database exploration and generative modeling. [1]

**The main disadvantages concern cost and convergence.** Population methods can require many evaluations and depend strongly on mutation, crossover, population, or movement parameters. BO can suffer from surrogate mismatch and difficult acquisition searches. Gradient methods require suitable derivatives and can settle in local optima. A 2023 preprint comparing inverse optimizers also found substantial differences in variability associated with algorithm settings, reinforcing the need to judge performance under the intended representation and budget. [10]

**Practical judgment follows evaluator and variable structure.** Prefer BO for expensive queries with informative low-dimensional representations, evolutionary or other derivative-free methods for discrete and mixed black-box searches, and gradients for differentiable continuous designs—changing that choice when the representation or evaluation budget changes.

### Choosing among the categories and combining them

**The strongest choice addresses the bottleneck.** A curated candidate library makes screening a natural starting point. A need to create new structural families makes a generator attractive. A clearly specified performance objective with expensive evaluations favors an optimizer that learns from or reuses previous results. The comparison table at the start summarizes these roles; the practical distinction is which part of the discovery problem each method makes easier. [1]

**Data-rich and data-poor problems differ.** A well-covered design domain can support a reusable inverse network or a fixed surrogate coupled to optimization. If the optimum lies far from the training set, sequential evaluation and model updating become more important. When labels are exceptionally expensive and only a small dataset exists, BO may be more appropriate than training a large generative network from scratch. Transfer learning can help when related low-fidelity or adjacent-domain data exist. [5]

**Hybrid workflows combine distinct contributions.** A generator can propose structures, a surrogate can predict their properties, an optimizer can improve them, and an active-learning rule can choose which ones deserve new physical evaluations. This is not merely a conceptual possibility: the literature contains concrete implementations in which different algorithm families solve different stages of the same design problem. Understanding the interfaces between those stages is often more useful than forcing the workflow into one exclusive category. [1]

**EVAPD illustrates a completed hybrid analysis.** Chenebuah, Nganbe, and Tchagang’s 2023 Evolutionary Variational Autoencoder for Perovskite Discovery combined a semi-supervised VAE, genetic algorithm, geometric similarity analysis, and DFT evaluation. Its Materials Project-derived training set contained 8,228 perovskite compounds, restricted to conventional cells with at most 40 atoms because examples above that size were inadequate. The VAE organized candidates around formation energy; evolutionary search ranked promising latent proposals; and geometric screening reduced problematic atomic arrangements. [11]

**The reported outputs require distinct labels.** EVAPD reported 137 DFT-relaxed perovskite candidates: 114 in one double-perovskite group and 23 in the more compositionally complex group. Its conclusion identified 59 + 23 = 82 as unique and novel relative to the databases compared by the authors; the broader output also included rediscoveries or polymorphic alternatives. Formation energy and hull energy in the reported candidate table were model predictions, while band gaps and magnetization were evaluated with DFT. This distinction preserves what each component actually established. [11]

**Its mechanism explains both benefit and boundary.** The learned latent space made proposal generation manageable, while the GA added explicit target-directed search. Similarity screening improved geometric plausibility but favored resemblance to selected standards. The combined approach therefore gained practical validity by narrowing open-ended generation—a deliberate exploration–feasibility trade-off rather than unrestricted discovery. Its reported photovoltaic and optoelectronic prospects remained computational candidates for subsequent experimental assessment. [11]

**Experimental feedback can close the loop.** Kusne and colleagues’ 2020 CAMEO system used Bayesian active learning in an autonomous synchrotron workflow to connect phase mapping with property optimization. Its cycles took seconds to minutes and led to a reported novel epitaxial nanocomposite phase-change-memory material. This example demonstrates a different form of progress from large-scale candidate generation: the decision algorithm operated directly with experimental feedback. [15]

**Performance metrics should match the purpose.** A search that repeatedly revisits one excellent material can have a high mean score over all evaluations, while another that samples diverse candidates can have a lower mean score but produce a more useful discovery portfolio. The 2023 optimization benchmark explicitly distinguished mean objectives, unique material counts, and repeated sampling. For method selection, best validated performance, distinct useful candidates, and expensive evaluation count answer different questions and should remain separate. [10]

**Part One’s judgment is complementary rather than competitive.** Exploration, learned modeling, and optimization are best understood as cooperating capabilities whose value depends on search-space coverage, representation quality, physical evaluation, and the researcher’s actual design objective.

## Part Two: Key Databases

### Database shortlist and official websites

**Seven resources provide a strong starting set.** The tables below distinguish four primarily computed-property resources from three resources centered on calculations, workflows, or crystal structures. Each can contribute to inverse design, but the contribution differs: training a formation-energy predictor, recovering a crystal structure, reproducing a calculation, and preserving a generated dataset require different information.

**Computed-property resources support prediction and screening.** Materials Project, OQMD, AFLOW, and JARVIS provide structured computational information that can support property-model training, candidate ranking, and target-driven searches. Their official portals are linked directly below. [16][17][18][19]

| Database | Data scope and type | Functional description | Typical inverse-design use | Official website URL |
|---|---|---|---|---|
| Materials Project | Primarily computed crystal and molecular properties; experimental information | Search materials, structures, and associated properties | ML training, HTVS, stability and property selection | https://materialsproject.org/[20] |
| Open Quantum Materials Database — OQMD | DFT thermodynamic and structural data | Explore known and hypothetical crystalline compounds | Formation-energy models and phase-stability screening | https://www.oqmd.org/[17] |
| AFLOW | High-throughput ab initio materials data | Search structures and properties by composition or identifiers | Alloy discovery, computational screening, property modeling | https://www.aflowlib.org/[18] |
| JARVIS | DFT, force-field, and ML datasets | Integrated NIST materials discovery and design infrastructure | Property prediction, rapid screening, model development | https://jarvis.nist.gov/[19] |

**Repositories preserve information beyond property tables.** NOMAD separates raw calculation files from normalized records; Materials Cloud emphasizes reusable datasets and computational provenance; and COD concentrates on crystallographic structures. Their functions are documented by the official NOMAD tutorial and the Materials Cloud and COD websites. [21][22][23]

| Resource | Data scope and type | Functional description | Typical inverse-design use | Official website URL |
|---|---|---|---|---|
| NOMAD Repository and Archive | Raw and normalized atomistic calculations | Search, publish, download, and analyze code-independent records | Reproducible training datasets and calculation mining | https://nomad-lab.eu/prod/rae/gui/search [24] |
| Materials Cloud | Raw and curated computational datasets; workflows and provenance | Archive and disseminate reproducible computational research | Dataset reuse, workflow inspection, discovery-data publication | https://www.materialscloud.org/[22] |
| Crystallography Open Database — COD | CIF crystal structures | Open structure search and retrieval | Structural inputs, reference structures, candidate comparison | https://www.crystallography.net/cod/[23] |

### Materials Project

**Materials Project is a broad starting point.** The DOE-backed Materials Project precomputes and disseminates material properties to accelerate discovery. Its scope includes inorganic crystals and small molecules, with searchable physical-property information derived principally from electronic-structure calculations and supplemented by experimental information. Its documentation highlights applications including batteries, solar energy, water splitting, optoelectronics, and catalysts. [16]

**Its early-2024 scale is explicitly dated.** On February 15, 2024, the U.S. Department of Energy reported more than 154,000 known and predicted materials, over 172,000 molecules, and millions of associated properties. The described information included bonding, oxidation states, chemical environments, and electronic and crystallographic descriptions. These figures provide a contemporaneous inventory for the requested cutoff. [25]

**Its main value is connecting structures and properties.** Researchers can use the resource as a candidate library for screening, as labeled data for property prediction, or as a source of structures for generator training. The earlier electrolyte and photocatalyst cases show library-based use, while EVAPD demonstrates reuse for generative-model training. This combination makes Materials Project particularly useful when a project must connect composition, explicit crystal geometry, and several calculated targets. [1][11]

**Molecular data broaden its design relevance.** Materials Project’s molecular documentation describes electrochemical, thermodynamic, electronic, and vibrational properties and points to its 2023 database publication. This extends the platform beyond bulk crystalline solids into molecular systems relevant to materials chemistry. A researcher should nevertheless select the collection matching the representation and target, rather than assuming that crystal and molecular entries can be pooled into one homogeneous model. [26]

### Open Quantum Materials Database

**OQMD emphasizes energetics and phase stability.** The Open Quantum Materials Database, created in Chris Wolverton’s group at Northwestern University, contains DFT-calculated thermodynamic and structural properties. It combines calculations starting from experimentally reported ICSD structures with hypothetical compounds produced by decorating common structural prototypes. That combination makes it useful both for learning known-material energetics and for identifying promising regions of composition space. [17][7]

**Its hypothetical entries support inverse exploration.** Prototype decoration systematically assigns elements to known structural arrangements. A predicted low-energy entry can indicate a composition where a favorable compound may exist, even if a more extensive structure search later finds a different ground-state geometry. OQMD’s authors explicitly distinguish identifying a promising composition region from proving that the tested prototype is its final stable structure. [7]

**Historical inventories show its established role.** The 2015 database paper reported 297,099 DFT calculations, including both known-structure-derived and hypothetical compounds. MatGAN’s 2020 account described an OQMD snapshot containing 606,115 compounds and used a filtered subset for generative training. The latter example demonstrates that a study’s actual training population can be substantially narrower than the database it cites. [7][8]

**Its accuracy study informs label interpretation.** The 2015 OQMD paper compared calculated formation energies with 1,670 experimental formation energies and reported a mean absolute error of 0.096 eV per atom using its selected reference-energy correction scheme. Separately, disagreement between experimental sources had a mean absolute difference of 0.082 eV per atom for 75 overlapping intermetallic compounds. These populations differ, but together they demonstrate why neither computed nor experimental labels should automatically be treated as exact. [7]

**Its strongest fit is thermodynamic design.** OQMD is especially useful for formation-energy prediction, competing-phase analysis, stability-oriented candidate screening, and supplying prior information to adaptive searches. For a target primarily concerned with another response, its energetic information remains valuable as a feasibility layer rather than necessarily supplying the complete training label. [14]

### AFLOW

**AFLOW provides automated computational materials data.** AFLOW stands for Automatic FLOW for Materials Discovery. Its official interface supports searches using an ICSD number, an AFLOWLIB unique identifier, or composition-style queries such as combinations of elements. This allows researchers to connect chemical selection with crystallographic identifiers and calculated materials information. [18]

**Its established emphasis includes complex alloys.** Draxl and Scheffler’s 2019 survey characterizes AFLOW as a major ab initio materials resource with a focus on complex alloys and associated ML property-prediction applications. This makes it a useful alternative when the design space is organized around alloy chemistry or systematically calculated structural families. Its contribution is not simply additional entries, but a computationally organized source suited to screening and model construction. [27]

**Published inverse-design work demonstrates model reuse.** The Noh review describes an evolutionary search that used an AFLOW-trained bulk-modulus predictor to identify 43 proposed superhard carbon phases. Here, the database supplied examples for learning the evaluator, while the evolutionary algorithm supplied new candidate structures. This is a clear example of a property database supporting discovery beyond the database’s own candidate list. [1]

### JARVIS

**JARVIS integrates several computational layers.** NIST’s JARVIS infrastructure combines DFT, classical force fields, machine learning, and supporting tools for materials discovery and design. The main distinctions are JARVIS-DFT for electronic-structure-derived properties, JARVIS-FF for force-field calculations, and JARVIS-ML for learned models and associated data. Its official portal provides access to this integrated ecosystem. [19][28]

**Its historical inventory is substantial and specific.** The 2020 JARVIS paper reported approximately 40,000 materials and approximately one million calculated properties in JARVIS-DFT. It also described approximately 500 materials and 110 force fields in JARVIS-FF, alongside approximately 25 property-prediction models in JARVIS-ML. The different units reflect distinct resources rather than a single count of unique materials. [28]

**Its ML collection includes reusable modeling information.** JARVIS-ML stores model parameters, descriptors, and input–target datasets. The platform’s Classical Force-field Inspired Descriptors, introduced in 2018, represent chemistry, structure, and charge-related information for property prediction. This makes JARVIS useful not only for obtaining labels but also for reproducing or extending an established modeling approach. [28]

**Its practical strength is integrated screening.** The 2020 paper describes a solar-material workflow that begins with inexpensive screening and proceeds to more demanding calculations, using quantities such as band gap, dielectric response, and spectroscopic limited maximum efficiency. It also discusses comparisons with experiment and higher-level electronic-structure methods. For inverse design, this illustrates how a resource can support several evaluator fidelities rather than only one uniform property table. [28]

### NOMAD Repository and Archive

**NOMAD separates files from normalized knowledge.** The Repository preserves raw atomistic input and output files; the Archive transforms computational results into a normalized, code-independent representation. The official 2020 tutorial describes browser access, an application programming interface, or API, and a Python package for automated searching, downloading, and local processing. The platform homepage is also available at https://nomad-lab.eu/[29]. [21]

**Normalization enables cross-code analysis.** Raw files from different simulation packages encode related information in different formats and conventions. NOMAD’s archive and metadata make it possible to search across methods, systems, properties, and uploads without manually interpreting every file first. The tutorial gives examples such as finding titanium oxides calculated with a specified code and containing density-of-states information. This is especially valuable when the research question depends on how a property was calculated. [21]

**Calculation counts are not unique-material counts.** Draxl and Scheffler’s 2019 account reported more than 50 million open-access total-energy calculations as of March 15, 2018, with roughly 40 supported computational codes. A 2022 NOMAD paper described more than 100 million total-energy calculations and input/output from more than 50 atomistic codes. Multiple calculations can concern the same material, different computational settings, or related configurations; this depth is useful for provenance and model development. [27][30]

**Its strongest fit is reproducible data mining.** NOMAD can support the assembly of method-aware training sets, examination of raw calculations behind a prediction, and publication of newly generated candidate data. EVAPD’s authors deposited their perovskite results there under DOI 10.17172/NOMAD/2023.05.31-1. That example connects the two parts of this report: a repository can be both an input to materials discovery and a destination for its reusable outputs. [11]

### Materials Cloud

**Materials Cloud is a research platform.** It combines raw and curated computational datasets with archival services, provenance graphs, modeling tools, analytics, and educational resources. Its official site organizes these functions into Discover, Explore, Archive, Work, and Learn. It is therefore best understood as a platform connecting datasets and workflows, rather than a single homogeneous table of materials properties. [22]

**Provenance explains how results were produced.** The 2020 Materials Cloud paper describes AiiDA as both a workflow manager and a recorder of computational events. Provenance can preserve relationships among inputs, codes, calculation settings, outputs, and subsequent calculations. For inverse design, this allows another researcher to inspect how a candidate was relaxed or evaluated rather than seeing only its final predicted property. [31]

**Archival services make discovery outputs reusable.** Materials Cloud Archive assigns persistent digital object identifiers, or DOIs, to deposited datasets and documents preservation for at least ten years after deposition. Its FAIR orientation means making data findable, accessible, interoperable, and reusable. The practical value is that the structures, labels, and workflow behind a published inverse-design result can remain connected and citable. [22][31]

**Interoperability connects otherwise separate resources.** The 2020 paper describes AiiDAlab importing structures from connected databases implementing OPTIMADE, the Open Databases Integration for Materials Design interface, including AFLOW, COD, and Materials Project. This supports a useful division of labor: retrieve structures from one source, run a reproducible evaluation workflow, and preserve the resulting data and provenance together. [31]

### Crystallography Open Database

**COD is primarily a structure collection.** The Crystallography Open Database is an open-access repository covering organic, inorganic, metal-organic compounds, and minerals, excluding biopolymers. Its principal materials-discovery contribution is providing crystallographic structures rather than a uniform suite of computed functional properties. The official website states that contributor data are in the public domain. [23]

**CIF files provide explicit structural inputs.** The crystallographic information file, or CIF, format records information such as unit-cell parameters, symmetry, composition, and atomic coordinates. These files can supply starting structures for calculations, reference structures for evaluating generated candidates, or examples for learning structural representations. A property-design project still needs suitable labels if its target is not directly represented in the structural record. [32]

**Historical collections distinguish deposited and predicted structures.** COD’s 2012 status report recorded more than 80,000 structures. It separately described PCOD, the Predicted Crystallography Open Database, as containing more than 100,000 predicted inorganic crystal structures generated with GRINSP. These were companion collections with different origins, not two measurements of the same inventory. [32]

**Deposition checks do not eliminate research-level curation.** The 2012 paper describes CIF syntax validation and duplicate screening, including checks involving matching formulas, publication information, cell constants within 0.5 Å, and cell angles within 1.2°. Flagged cases received manual review, and specified temperature and pressure were considered. These are useful repository safeguards, but a modeling study must still decide how to treat alternative measurements, polymorphs, and condition-dependent structures. [32]

### Choosing and combining data resources

**Choose data by the intended output.** Composition generation needs composition examples and relevant chemical information; crystal generation needs recoverable geometry; property-conditioned generation additionally needs labels linked to those representations. An energy-landscape model may require raw configurations and calculation metadata rather than only relaxed structures and final energies. This follows directly from the distinction between candidate generation, forward evaluation, and optimization: the database must support the particular role it is expected to perform. [1][30]

**Computed and experimental data answer different questions.** Computed datasets are attractive because automated workflows can provide many consistently generated labels, including for hypothetical candidates. Experimental records show what has actually been observed under particular conditions, but do not automatically provide every property needed for design. Their combination is powerful when the workflow preserves which values are simulated, measured, corrected, or inferred. The Materials Project’s early-2024 description explicitly includes both computational and experimental property information. [25]

**Cross-database merging requires compatible definitions.** The same formula can refer to different structures, and the same named property can depend on computational method, reference energies, or experimental conditions. OQMD’s comparison with Materials Project found that chemical-potential fitting choices explained much of the difference in reported formation-energy agreement with experiment. Pooling values without their calculation context can therefore introduce systematic differences that a model mistakes for materials behavior. [7]

**Observed structures and hypothetical structures need labels.** Both can be valuable for inverse design, but they play different roles when learning feasibility. A hypothetical material that has not been reported experimentally should not automatically receive a negative synthesizability label. The 2022 inverse-design review discusses positive-and-unlabeled learning for this reason: known examples provide positive evidence, while unobserved candidates are treated differently from demonstrated failures. [3]

**Dataset restrictions shape reachable discoveries.** EVAPD’s 40-atom cell restriction and MatGAN’s study-specific filtering show that citing a broad database does not mean training over its complete chemical or structural diversity. The effective design space is determined jointly by the selected records, descriptor, and model architecture. For a report, describing that intersection is more informative than presenting the database’s headline size as the model’s training coverage. [11][8]

**Specialized datasets can outperform broader starting points.** A general inorganic collection may contain many entries but relatively few examples of the target family or property. The two-dimensional generation study illustrates the alternative: use a focused seed set, generate within a representation suited to that domain, and preserve the resulting structures and properties in the Computational 2D Materials Database. Broad resources supply reach; specialized collections supply relevance and consistent domain-specific evaluation. [12]

**Provenance supports scientific interpretation, not just reproduction.** When an unexpected candidate performs well, the researcher needs to determine whether the improvement comes from chemistry, structure, computational settings, or an ML extrapolation. Raw-file repositories and workflow graphs make those alternatives easier to distinguish. This is why NOMAD and Materials Cloud complement computed-property databases even when they contain some overlapping calculations. [21][31]

**Evidence and measurement basis.** Method comparisons here synthesize problem-specific studies rather than a common-budget ranking, and the scientific examples precede the early-2024 cutoff. Database inventories are dated snapshots measured in different units—materials, structures, properties, models, or calculations—and are not additive. Novelty, validity, and stability retain each study’s definitions; computed candidates remain distinct from experimentally realized materials. Approximate inventories retain source rounding, and the approximately 99% evaluation-cost figure is a review-reported estimate.

**The overall judgment is practical.** Use the inverse-design method to solve the actual search bottleneck and the database to supply the actual representation, labels, and provenance required. The strongest materials-discovery result is not the largest generated list, but a set of physically credible candidates whose target performance survives the appropriate computational and experimental tests.

**Additional documented evidence**

| Entity | database name | functional description | official website URL |
| --- | --- | --- | --- |
| Materials Project | The table names the database “Materials Project (MP)”.[198] | Materials Project provides reference structures and…[34] | The brochure lists the ICSD Web portal at[71] |
| AFLOW | The table names the database “Aflow-Automatic-FLOW…[198] | AFLOW is presented as the “Automatic Flow Framework…[170] | The supplied official AFLOW-ML page is[52] |
| Open Quantum Materials Database | The source names the resource “Open Quantum Materials…[148] | The provider lists the OQMD sub-database endpoint as…[247] | The provider lists the OQMD sub-database endpoint as…[247] |
| NOMAD Repository | The page names the resource “NoMaD Repository (Novel…[199] | NOMAD is a free web service for sharing, organizing…[155] | The source lists the NOMAD Analytics Toolkit official…[140] |
| JARVIS-DFT | The source gives the expanded name as “the joint…[182] | JARVIS-DFT is listed as a dataset containing more than…[45] | The catalog record lists the JARVIS landing page as[209] |
| Crystallography Open Database | The source names the database “Crystallography Open…[137] | The downloadable file is “cod_apr_2023.sdf” and has a…[55] | The listed URL for COD is “[198] |
| Inorganic Crystal Structure Database | The page names the resource “FIZ/NIST Inorganic…[83] | The cited ICSD work concerns accessibility supporting…[97] | The brochure gives the ICSD Web portal URL as[102] |
| Materials Cloud | The official page names the resource “The Materials…[224] | The Materials Cloud@HPC Board was created in late 2020.[222] | This source identifies Materials Cloud as a web…[216] |
| Citrination | The FAIRsharing record was last reviewed on September…[87] | Citrine Informatics has undertaken to develop an open…[227] | The official Citrination site URL documented here is[84] |
| Materials Data Facility | The official organization identifies the resource as…[231] | The page lists publication-year counts including…[72] | The source gives the MDF website as[195] |

Across the table, Materials Project, AFLOW, OQMD, NOMAD Repository, JARVIS-DFT, and COD are paired with computed-ML data, DFT/ML screening, DFT structures and thermodynamics, FAIR inverse-design data, DFT properties, and open crystal structures, respectively, alongside their listed official sites [35][143][241][81][130][184][193][146][128][140][135][49][204][77][97][174][215]. The remaining rows add ICSD's searchable crystal data, Materials Cloud's open computational platform, Citrination's materials-data/ML platform marked decommissioned in 2022, and MDF's materials-data discovery/ML infrastructure with their corresponding sites [43][51][175][158][223][63][84][87][58].

**Evidence-based database roster**

Using **31 March 2024** as the operational endpoint, the strongest evidence distinguishes computational databases, structure collections, and broader data platforms rather than treating them as interchangeable. The list is representative, not a popularity ranking. Computational resources such as Materials Project, AFLOW, OQMD, NOMAD, and JARVIS support model training, screening, or candidate generation; COD and ICSD primarily supply structural data; Materials Cloud and the Materials Data Facility are platform or repository candidates. [110][135]

| Resource and status by 31 March 2024 | Function, data scope, and relevance to machine-learning inverse design | Official website URL |
|---|---|---|
| **Materials Project** — directly evidenced and used in pre-cutoff inverse-design work | Materials Project is an open-access database for inorganic-materials discovery that provides pre-computed properties for candidate catalysts. Its Catalysis Explorer supplies adsorption energies for catalysts under different configurations, with data sourced from the Open Catalyst Project OC20; a study published on **4 December 2023** used Materials Project and OC20 adsorption-energy data to train a deep-reinforcement-learning agent for multi-objective inverse catalyst design. [44] A separate pre-cutoff inverse-design study trained a CGCNN surrogate on Materials Project data and used Materials Project reference structures for Ag-fcc, diamond and graphite, graphane, and NdNiO₃. [34] A further benchmark formed materials libraries from Materials Project IDs, generated candidate elemental compositions, and used a MEGNet surrogate to evaluate candidates during inverse optimization. [36] Thus, Materials Project can supply training data, reference structures, candidate libraries, and screening properties. The benchmark also cautions that some potential materials lack existing property data or suitable interatomic potentials for direct MD or DFT evaluation; database lookup and surrogate screening do not remove the need for higher-fidelity validation. [36] | **https://materialsproject.org/** [34] |
| **AFLOW** — established computational database/framework | AFLOW is described as an automated framework that generates, stores, and disseminates materials data and applies it to thermodynamic formability modeling, including phase-diagram prediction and properties of disordered materials. Its standardized data have supported machine-learning training, property prediction, descriptor development, design-rule discovery, and identification of candidate functional materials. [79] A materials-ML review lists AFLOW as a computational materials-data resource and gives the AFLOWlib address. [110] This makes AFLOW relevant for training and screening, although the supplied evidence does not provide a numerical usage denominator or a single cutoff-date snapshot of its contents. | **https://aflowlib.org/** [110] |
| **Open Quantum Materials Database (OQMD)** — recognized computational database | OQMD is associated with high-throughput density-functional-theory materials design and discovery; its formation-energy data were also the subject of an accuracy assessment. [110] A 2022 account lists OQMD among computational materials databases created through high-throughput screening initiatives. [135] OQMD is therefore relevant for computational-property training, surrogate evaluation, and virtual screening. The cited spans establish its design-and-discovery role but do not establish the complete field inventory or a canonical official URL. | **Unresolved in the cited evidence**; do not substitute a mirror or aggregator. |
| **NOMAD Repository & Archive** — established repository and AI-enabled data platform | NOMAD is a FAIR storage infrastructure rather than a single homogeneous property table. The Repository stores input and output from **more than 50 atomistic codes**, and the cited article reports **more than 100 million total-energy calculations**, both as of the article’s stated present in the publication dated **5 December 2022**. The Archive converts, normalizes, and characterizes those data using NOMAD Metainfo, producing a code-independent representation suitable for AI analysis. [135] Its browser-based AI Toolkit supports archive querying through an API, feature construction, data mining, machine-learning training, visualization, exploratory analysis, predictive modeling, and reproducible notebooks; cited examples include archive querying, clustering, and tetradymite analysis. [135] NOMAD therefore supports data acquisition, preprocessing, training, and reproducible evaluation, while its repository/archive classification should be retained in the table. | **https://nomad-lab.eu/** [110] |
| **JARVIS-DFT / Joint Automated Repository for Various Integrated Simulations** — recognized data-driven materials-design repository | JARVIS is identified as a repository of integrated simulations for data-driven materials design. Its data are relevant to machine-learning inverse design because they can supply calculated structures and properties for model training, surrogate evaluation, and candidate screening. [110] The supplied evidence establishes the JARVIS name and function but does not itself establish a canonical URL. | **Unresolved in the cited evidence**. |
| **Crystallography Open Database (COD)** — open structural database; inclusion remains qualified | COD is described as an open-access collection of crystal structures and a platform for worldwide collaboration. [110] Its primary inverse-design contribution is structural: crystal structures can serve as representations, reference candidates, or inputs for structure-based models. COD should not be treated as a complete property-label database; target properties, calculated labels, or experimental metadata may need to be joined from other resources. The supplied evidence supports structural relevance but does not establish COD’s common-use level specifically in machine-learning inverse design by the cutoff. | **Unresolved in the cited evidence**. |
| **Inorganic Crystal Structure Database (ICSD)** — major structure resource; access qualification unresolved | ICSD is identified as an inorganic crystal-structure resource. A supporting pre-cutoff source describes it as containing hundreds of thousands of experimentally determined crystalline structures. [89] Its likely inverse-design role is to provide experimentally grounded structural data or chemical-relationship information, but the supplied evidence does **not** establish whether access is open, subscription-based, or subject to another qualification; it should not be presented as freely accessible without verification. One supplied evidence fragment reports a WGAN trained on inorganic materials from ICSD and gives **2 million generated samples**, **92.53% novelty**, and **84.5%** satisfying charge-neutrality and electronegativity conditions; because the fragment does not establish the publication date, these figures demonstrate a possible use case, not common-use evidence at the cutoff. [103] | **Unresolved in the cited evidence**; access conditions must be checked before use. |
| **Materials Cloud** — platform candidate, not a single database | The cited pre-cutoff source identifies Materials Cloud as a platform for open-access storage and access to materials-science data and cites a 2020 publication describing it as a platform for open computational science. [135] It can therefore support discovery, sharing, provenance, and retrieval of computational datasets, but its platform/ecosystem boundary should remain explicit rather than being presented as one uniform database. The supplied evidence does not establish a specific inverse-design dataset, common-use denominator, or a single database status as of 31 March 2024. | **Unresolved in the cited evidence**. |
| **Citrination** — retained candidate with unresolved cutoff-bounded status | The supplied cutoff-bounded evidence does not establish Citrination’s pre-31-March-2024 function, common-use or recognition in machine-learning inverse design, database classification, or canonical official URL. It should remain a named but unresolved candidate rather than being silently promoted to a verified database. | **Unresolved**. |
| **Materials Data Facility (MDF)** — repository/platform candidate with unresolved inverse-design adoption | MDF is identified as a platform for open-access storage and access to materials-science data. [135] Supporting pre-cutoff material describes a repository for data produced by simulations and experiments, with publication and discovery services, persistent identifiers, metadata, searchable records, custom schemas, REST APIs, and support for automation, analysis, and reuse. [68][167][233][234] These functions make MDF relevant for finding training data, preserving provenance, and accessing model-ready datasets, but the supplied evidence does not establish specific inverse-design usage or common-use status by 31 March 2024. It should remain labeled as a platform/repository candidate. | **Unresolved in the cited evidence**; an archived or third-party URL should not be substituted. |

**How the resources enter an inverse-design workflow**

**Materials Project provides the clearest end-to-end database example.** In the CASTING workflow, the user specifies an optimizer, target properties, an objective or scoring function, a crystal system and composition, a simulator or evaluator, and output or monitoring options. Target properties can be energetic, mechanical, electronic, or thermal; the search space can include lattice bounds, angles, chemical species, composition, and minimum allowed interatomic distances. Molecular-dynamics or ab-initio packages then evaluate candidates, and the workflow records objective status, sampled configurations, and termination information. [34] The crystal representation includes lattice parameters \((a,b,c,\alpha,\beta,\gamma)\), basis atoms, atomic positions, and chemical composition; candidate structures are modified through add-atom, remove-atom, lattice-mutation, or atom-mutation operations before scoring. [34]

The Materials Project-linked benchmark shows the complementary database role in discrete composition design. Design variables are transformed into candidate elemental compositions, a materials library is formed from Materials Project IDs, and selected entries are converted into graph structures for MEGNet evaluation. The pretrained surrogate enables rapid property screening, but the same source notes that missing property records or missing pseudo-potentials can prevent direct evaluation by MD or DFT. [36] The benchmark describes its comparison as involving **11** optimization methods, although the visible enumeration names Bayesian optimization, deep reinforcement learning, genetic algorithm, particle swarm optimization, hybrid Grey Wolf optimization, hybrid improved Whale optimization, ant-colony optimization, differential evolution, simulated annealing, Bees optimization, Arithmetic optimization, and Runge–Kutta optimization. That internal count discrepancy should not be normalized into a database count. [36]

**AFLOW, OQMD, JARVIS-DFT, and NOMAD serve different computational-data needs.** AFLOW emphasizes automated generation and standardized high-throughput data; OQMD emphasizes high-throughput DFT materials design, discovery, and formation-energy data; and JARVIS-DFT emphasizes integrated simulations for data-driven design. [79][110] NOMAD is especially useful when the researcher needs raw calculation inputs and outputs, normalized metadata, API access, and reproducible analysis rather than only a preselected property table. [135] These resources can support forward-property models that score inverse-design candidates, but their calculated values retain the assumptions and errors of the underlying computational methods.

**COD and ICSD primarily solve the structure-data problem.** Their crystal structures can initialize candidate representations, provide reference materials, or support composition- and structure-based learning. They do not, by themselves, guarantee target-property labels, consistent calculation protocols, uncertainty estimates, or synthesizability. ICSD additionally requires an explicit access check; COD’s open-structure role should not be conflated with universal coverage of experimentally realizable materials. [89][110]

**Materials Cloud and MDF solve access, sharing, and provenance problems more than they define one fixed property distribution.** Materials Cloud is described as a platform for open computational science, while MDF is described as supporting publication, discovery, metadata, persistent identifiers, and programmatic access to materials data. [135][68][167][233][234] These capabilities are valuable when assembling training or validation sets from multiple projects, but the researcher must still normalize representations, units, calculation settings, target definitions, and provenance before combining records.

**Cutoff and evidence qualifications**

Later evidence in the packet is not used to extend the historical roster. In particular, a source submitted on **5 November 2025** reports reinforcement-learning and diffusion-model results for MatInvent, while a source published on **23 June 2025** reports approximately **154,000 Materials Project crystals**, universal-model use of Materials Project, AFLOW, and OQMD, and a **257,487-structure** WBM dataset using an ICSD-derived chemical-similarity matrix. These observations are explicitly post-cutoff and therefore do not establish database names, functions, common use, or status as of 31 March 2024. [33][88]

**Conclusion and deciding condition.** For property-labelled computational screening, begin with Materials Project, AFLOW, OQMD, or JARVIS-DFT; for raw calculations, normalization, API access, and reproducible AI analysis, NOMAD is the more appropriate resource; for crystal-structure coverage, consider COD or ICSD subject to access and metadata checks; and for cross-project discovery and provenance, consider Materials Cloud or MDF. The deciding condition is whether the resource supplies the required representation, target labels, provenance, access rights, and validation pathway for the particular inverse-design task. No database alone establishes that a generated candidate is stable, novel, experimentally realizable, or synthesizable.

**Computational and data-platform entries**

| Resource | Function, data role, and evidence through 2024-03-31 | Official URL or status |
|---|---|---|
| **Materials Project** | An in-house computational resource providing searchable calculated structures and properties, with structure export in CIF, JSON, POSCAR, and VASP Input Set formats [138]. An inverse-optimization workflow used it as a materials library: a deep-reinforcement-learning agent selected compositions and MEGNet supplied predicted-property rewards [91]. Pre-cutoff studies also used Materials Project structures for generative training and atom-feature learning [106][93]. Its 2023 MPcules extension provided API, Python, and web access to molecular data and reported more than 170,000 DFT calculations; the same report gave 172,874 collected molecules, 248,302 associated molecules, and 568,004 tasks—figures for MPcules, not the whole Materials Project [139]. Important qualifications are PBE band-gap underestimation, significant possible error in layered-crystal interlayer distances, typical 1–3% overestimation for many crystals, and changing aggregated releases [138]. | Official documentation: `https://docs.materialsproject.org/frequently-asked-questions` [138] |
| **Open Quantum Materials Database (OQMD)** | OQMD is a high-throughput DFT resource focused on energetics, thermodynamics, and formation energies [140][122]. Pre-cutoff literature recognizes it, alongside Materials Project and AFLOW, as one of three larger high-throughput simulation databases for systematically exploring theoretical materials; related raw data were also published through NOMAD [142]. This establishes relevance and recognition, not a quantitative popularity ranking or a specific inverse-design algorithm. | Official URL unresolved in the cited cards [142]. |
| **NOMAD Repository** | The canonical resource is the NOMAD Repository, within the broader Novel Materials Discovery Laboratory; it is a repository and platform rather than one homogeneous database [140]. It stores raw code outputs, normalized code-independent data, metadata, search functions, and machine-learning tools. A 2019 account reported support for about 40 computational codes [140]; on 15 October 2023, the public service reported over 12 million materials-science simulations, around 50,000 experiment or synthesis entries, public availability since 2014, and data from over 500 authors [142]. Analytics notebooks covered crystal-structure and property prediction, error estimation, and classification; an 883-submission competition used crystal-graph n-grams with kernel ridge regression, descriptor-based LightGBM, and SOAP with a neural network [140]. Main qualifications are data sufficiency, difficult model reporting, and the accuracy and computational-cost limits of electronic-structure calculations [140]. | `https://nomad-lab.eu/` [142] |
| **JARVIS-DFT** | The Joint Automated Repository for Various Integrated Simulations supplied DFT data in a 2023 inverse-design study of superconductors. Approximately 1,000 superconducting materials trained a crystal-diffusion variational autoencoder; 3,000 structures were generated, 61 survived ALIGNN screening, and leading candidates received DFT validation [122]. This is direct pre-cutoff evidence of a training-to-generation-to-screening workflow. | Official URL unresolved in the cited cards. |
| **Citrination** | Citrination remains a platform candidate rather than a confirmed standalone database. Its official Python Citrination Client documentation records data upload, model, search, and data-view operations; prediction/design calls; model reports; relation graphs; and machine-learning data-view and formulation tools [141]. The documentation records version-specific additions including PIF metadata, relation graphs, an advanced ML data-view builder, class probabilities, and formulation views, while also documenting deprecated or removed APIs [141]. It does not establish a pre-cutoff common-use denominator, inverse-design taxonomy, or specific reinforcement-learning or genetic-algorithm implementation. | Official client documentation: `https://citrineinformatics.github.io/python-citrination-client/index.html` [141]; database landing-page status unresolved. |
| **Crystallography Open Database (COD)** | Retained as an open crystal-structure candidate, but its function, pre-cutoff common-use evidence, and inverse-design role remain unresolved in this cutoff-bounded part. | URL unresolved here. |
| **Inorganic Crystal Structure Database (ICSD)** | Retained as an inorganic crystal-structure candidate, but its pre-cutoff function, recognition, access qualification, and inverse-design role remain unresolved in this cutoff-bounded part. | URL unresolved here. |

The deciding condition is materials relevance plus pre-cutoff use or recognition, not an unsupported popularity ranking. Materials Project, OQMD, NOMAD, and JARVIS-DFT have direct eligible evidence of computational or machine-learning use; Citrination remains a data-informatics platform candidate, while COD and ICSD require eligible pre-2024 verification before their table cells can be completed. Separate algorithm benchmarks—such as Bayesian optimization reaching goals in about 10 experiments and over 1,000-fold acceleration against random sampling in its hardest virtual case [82], or a mixture-density network generating candidate-structure distributions from desired properties [50]—are method evidence, not database metrics.

**Conclusion.** In this evidence set, Materials Project has the broadest direct ML/design support; OQMD has direct generative-training evidence, while COD and ICSD mainly supply crystal structures. Verify unresolved URL and access fields before final inclusion.

- **Materials Project (MP):** Open computed-property data for inorganic materials, supporting ML training, screening, and validation—not a method category [308,381]. MP18 models degraded severely on new MP21 compounds through version shift; UMAP, model disagreement, query-by-committee, and adding 1% test data improved accuracy [144]. A 2023 release provides MP18/MP21 snapshots, `e_form`, `bandgap`, `bulk_modulus`, metadata, 273 Matminer features, and separate pymatgen/CIF structures [150].

- **AFLOW:** AFLOW/AFLOWLIB is a high-throughput *ab initio* repository; AFLUX searches it and AFLOW-ML predicts properties [374,375]. On 2018-11-20, it was reported to contain over 2 million compounds and about 100 standardized computed properties per compound; ML supported prediction, descriptor and design-rule discovery, and functional-candidate identification, with two permanent magnets synthesized [145].

- **OQMD (Open Quantum Materials Database):** High-throughput DFT data cover known and hypothetical structures; a 2022 account reports over 1 million compounds, ML projects, open data, and FAIR-querying aims [123]. OQMD data yielded a model 30× faster than undirected search and 55 predicted stable Heuslers [146]; a 2018 study predicted 186/254 known and 87/235 ML perovskites within 100 meV/atom of the convex hull, including six cubic at T=0 K [147]. In 2013, it reported over 200,000 structures (32,489 ICSD entries), 4,000→8,700 formation-energy cases, over 1.6 million ternary predictions, and eight stable compounds among nine tested; coverage remained limited by observed structures and prototypes [148]. Source-listed portal: `http://oqmd.org` [151].

- **NOMAD:** The NOMAD Repository/Laboratory is a data platform rather than one database: raw data from about 40 codes (13 May 2019) are normalized in the Archive; the Encyclopedia exposes properties and the Analytics Toolkit provides AI notebooks for structure/property prediction, error estimates, and classification. The Repository was public from early 2014 [151]. Source-listed URL: `https://nomad-coe.eu` [151].

- **ICSD (Inorganic Crystal Structure Database):** A crystallographic-structure resource for materials research and design; its exact access qualification, standalone scope, and direct ML-inverse-design use remain unresolved, although its experimental structures occur in OQMD [334,380].

Materials Project and AFLOW are recognized large high-throughput databases for theoretical-material exploration; computation screens hundreds of thousands of candidates against design targets, but synthesis remains human validation [383,309]. Materials Project supplies structures, formation energies, electronic, mechanical, phonon, synthesis and XAS properties for queries and ML training/validation; hull screening reduces DFT work, but interpolative ML struggles with outliers [153]. OQMD (Open Quantum Materials Database) is another high-throughput database; its raw data are on NOMAD and qmpy connects to it, but its official URL is not verified by the cited evidence [383,384].

NOMAD is a free public application for sharing, normalizing, searching and analyzing materials data, with metadata and ML tools; on 15 October 2023 it reported >12 million simulations, ~50,000 experiment/synthesis entries, public availability since 2014, and >500 authors [152]. JARVIS-DFT (Joint Automated Repository for Various Integrated Simulations) is a NIST data-driven-design resource: its 2020 description reports ≈40,000 materials, ≈1 million calculated properties, and https://jarvis.nist.gov [206]. No taxonomy-specific algorithm is established; a >80,000/millions report dated 7 May 2024 is post-cutoff [108].

ICSD (Inorganic Crystal Structure Database) reported >60,000 inorganic crystal structures in computerized formats on 19 February 2017; its structures underlie Materials Project datasets, while its natural-material bias toward stable, low-formation-energy entries and access model remain unresolved [83,384]. Evidence names Theoretical COD, not COD; COD remains unresolved [153]. Citrination is a commercial Physical Information File (PIF)/ML cloud platform; uncertainty-aware acquisition and experimental updates in closed-loop nanoparticle synthesis reached a target in 21 iterations and mapped feasibility in three Gaussian-process cycles [112].

**Resource records and qualification notes**

The entries below form a representative, evidence-based roster rather than a popularity ranking. Counts are source-dated observations, not a uniform 2024 snapshot.

| Entity | Function and relevance to ML inverse-design research | Official URL status in this evidence group |
|---|---|---|
| **Materials Project** (Materials Project database) | Community resource for theory-based data, analysis tools, software, and an API. A 2018 account reported more than 69,000 materials with structures and total energies, more than 57,000 with band structures, and more than 48,000 with transport properties. Its data support screening, model development, surrogate prediction, and design-oriented searches; the same account reported several hundred studies and more than 40,000 users in 2018. [86] Coverage remains incomplete: one study found 79 stable systems absent, while another described known-database coverage as only a tiny portion of chemical space. [86][40] | `https://www.materialsproject.org/` is source-stated as the project website. [86] Revision-specific updates should not be treated as a 2024-03-31 snapshot. [62] |
| **AFLOW / AFLOWLIB.ORG** | AFLOW is an automatic framework for high-throughput materials discovery; AFLOWLIB.ORG is a distributed repository of materials properties from high-throughput *ab initio* calculations, and AFLOW-ML supplies a REST API for machine-learning property prediction. These establish pre-cutoff recognition and direct relevance to computational and ML-assisted discovery. [113][157] | An official URL is not established by the cards in this source group. |
| **Open Quantum Materials Database (OQMD)** | Computational resource associated with materials design and discovery through high-throughput density-functional-theory calculations. A 2020 source describes the Materials Project and OQMD together as containing more than \(10^5\) DFT-calculated crystal structures and describes database screening for targeted applications. OQMD was recognized in a 2018 materials-design citation, but the evidence supplies neither a usage denominator nor a direct OQMD-specific inverse-design workflow. [132][113][40] | Official URL unresolved in this source group. |
| **NOMAD Repository / NOMAD Project** | Infrastructure for collecting and sharing materials data in searchable, accessible, and reusable form. It was presented as supporting materials-science and engineering tools and the combination of data mining, high-throughput screening, inference, and machine-learning methods. [132] | Official URL unresolved in this source group. |
| **Inorganic Crystal Structure Database (ICSD)** | Experimental crystallographic data extracted from scientific journals over more than 100 years; such data are used to screen candidates for targeted applications. A published workflow used an experimentally determined WTe₂ supercell from ICSD as a template, and Materials Project compounds commonly use bulk geometries reported in ICSD. The source calls ICSD popular but gives no common-use denominator; its access model is unresolved here. [132][99][86][40] | Official URL and access qualification unresolved in this source group. |
| **Citrine Informatics / Citrination** | Materials-data platform and service. The cited description lists open infrastructure, a large free-materials collection, the PIF data standard, an open-source *lolo* ML library, and API tools and tutorials. A source-reported case states that an isolated dataset was too small, additional Citrination data enabled a larger model, and real-world discovery took half the time; this is not a controlled benchmark. The cards do not establish a Citrination-specific taxonomy category or algorithm. [115][132] | The source lists `https://citrine.io/`, but does not establish it as Citrination’s canonical official URL. [132] |
| **Materials Data Facility (MDF)** | Materials Genome Initiative data service and data infrastructure. MDF can publish datasets regardless of size, support extensible domain-specific metadata schemas, expose data and metadata through REST APIs for automation and analysis, and allow users to search, interrogate, and reuse published data. Its qualification as a commonly used single database remains unresolved. [157][132] | Official URL unresolved in this source group. |

The deciding distinction is functional: Materials Project, AFLOW, and OQMD are computational materials-data resources; NOMAD and MDF are broader data infrastructures; ICSD is a crystallographic source with access qualifications; and Citrination is a data/informatics platform. These categories should remain explicit rather than being presented as interchangeable databases.

With **31 March 2024** as the operational endpoint, the evidence supports the following **representative, non-ranked** roster. “Database” includes a repository or platform only where its materials-data function is explicit; unresolved cells are retained rather than inferred.

These resources are **data-layer inputs rather than members of the three method categories**. Materials Project provides the clearest direct example here: its data supplied reference structures and trained a CGCNN surrogate used within a multi-objective CASTING inverse-design search; the search converged in approximately **6,000 evaluations**, while sampled carbon polymorphs included structures below **−7 eV/atom** and allowed metastable solutions. [37] AFLOW, OQMD, and NOMAD primarily support model-based prediction, screening, and optimization through structure–property data; COD and ICSD provide structural observations for candidate-space construction, training, or validation; Materials Cloud emphasizes provenance and reproducibility; and Citrination emphasizes data extraction and structuring. The cited database evidence does not establish resource-specific algorithm superiority or a separate advantage/disadvantage ranking. [41][134][158][159]

Recognition is not treated as a popularity ranking. The **2013** Materials Project paper reported more than **33,000 compounds**, over **15 million CPU-hours**, more than **4,000 registered users**, and several hundred daily page views at that time; these are historical observations, not 2024 counts. [48] AFLOW, OQMD, and NOMAD are identified as major materials repositories in the inverse-design literature, while COD and ICSD are recognized crystal-structure resources. [41][134] Materials Cloud’s **2020** description reports persistent identifiers, at least **10 years** of stated preservation, and size limits of **5 GB** for general records and **50 GB** for AiiDA databases. [158] Citrination’s **2015** presentation reported more than **1,000 institutions**, **3.1 million materials-data records**, **3,200 datasets**, and **150,000 documents**, but those figures do not establish its status at the 2024 cutoff. [159]

**Conclusion:** the strongest cutoff-compatible database candidates are Materials Project, AFLOW, OQMD, NOMAD, JARVIS, COD, and the qualified Materials Cloud platform. The deciding condition for retaining ICSD, Citrination, or Materials Data Facility as ordinary database rows is verification of their pre-cutoff identity, access model, function, common-use evidence, and official URL.

Materials Project: open, recognized database; >100,000 crystals and millions of properties (2021) [161]. AFLOW: ab-initio property repository; OPTIMADE/AiiDAlab source [96][163]. Open Quantum Materials Database (OQMD): 637,644 materials; thermodynamic/structural data (2020) [117]. NOMAD Repository/Laboratory: electronic-structure repository; AiiDAlab source [161][163]. Crystallography Open Database (COD): open crystal structures; AiiDAlab source; ML-use unknown [163]. Inorganic Crystal Structure Database (ICSD): >180,000 inorganic structures (1913 literature; CIF; 2021); 92 possible 2D compounds, 680 stable monolayers (2020); access unknown [162][117]. Materials Cloud: platform, not one database; data/tools/workflows/provenance; inclusion/URL unresolved [163][73]. Citrination: Physical Information File makes complex data searchable/machine-readable; import/storage/access; use/URL unresolved [162]. Materials Data Facility: publication/discovery infrastructure; heterogeneity impedes integration; qualification unresolved [162].

For the 31 March 2024 cutoff, the database set is representative, not a popularity ranking: the evidence shows recognition or use, not a common denominator.

- **Materials Project:** open inorganic-DFT database; a 2021 account reports tens–hundreds of thousands of calculations and queryable properties [126]. A 2023 inverse-design case trained CGCNN on its data and used Ag-fcc, diamond/graphite, graphane and NdNiO3 reference structures; URL: `https://materialsproject.org/` [38].
- **AFLOW/AFLOWLIB:** high-throughput repository of material properties [78][164]. **Open Quantum Materials Database (OQMD):** high-throughput DFT database of thermodynamic and structural properties for materials design and discovery; open endpoint: `www.oqmd.org` [78][136].
- **NOMAD Repository:** ab-initio electronic-structure data from DFT and beyond [78]. **JARVIS-DFT:** functional- and two-dimensional-layered-material data; an undated summary reports approximately 40,000 materials and 1 million calculated properties [78][118].
- **Crystallography Open Database (COD):** crystal structures for inorganic, organic, metal-organic compounds and minerals, supporting structure-based ML [78][118]. **Inorganic Crystal Structure Database (ICSD):** more than 100,000 inorganic materials’ compositions and site occupations, mostly synthesized; a strong ML starting set but insufficient alone for novel-material prediction, where hypothetical DFT structures help [126]. An undated listing says more than 159,000, so counts are snapshot-dependent [78].
- **Materials Cloud:** `https://www.materialscloud.org/` is a data/platform ecosystem—curated/raw data, structure databases, repositories, workflows and provenance—not one database [75]. **Citrination:** named “Citrine Informatics’ Citrination platform,” but its pre-cutoff function and canonical URL remain unresolved [167]. **Materials Data Facility (MDF):** provides materials-data publication/discovery and ML-ready collections; official page: `https://www.materialsdatafacility.org/` [166], but pre-cutoff common-use status is unestablished.

**Data-resource evidence and qualifications**

The roster is representative rather than a popularity ranking, and claims are bounded at 31 March 2024. **Materials Project** is a recognized materials-genome resource: its computed-property database was exposed through a REST API and Python library for open, application-level access [169]. A 2018-derived machine-learning compilation reports seven properties—bulk modulus, formation energy, energy above the convex hull, elastic anisotropy, band gap, magnetization, and shear modulus—in CSV datasets split 70:15:15 into training, validation, and test sets [168]. A pre-cutoff design study also used high-throughput data from materialsproject.org, including a 704-material piezoelectric dataset with 11 Pareto-front materials, illustrating training, screening, and adaptive optimization rather than a popularity measure [120].

**AFLOW**, documented in the cited sources as **AFLOWLIB** or **AFLOWLIB.org**, is a distributed repository of calculated structural, thermodynamic, electronic, crystallographic, and mechanical properties, together with simulation provenance and runtime data [169]. Its API supports searches and external workflows: users can retrieve stoichiometry, formation enthalpy, geometries, prototypes, and calculation files to construct convex hulls and phase diagrams or obtain band structures and density-of-states plots [169]. AFLOWLIB is therefore relevant to candidate screening and property prediction; its high-throughput data are cited alongside Materials Project and OQMD as materials-design resources [120]. The source does not resolve whether the table’s canonical name should be “AFLOW” or “AFLOWLIB,” nor does this evidence establish a quantitative usage ranking [169].

**Open Quantum Materials Database (OQMD)** is a high-throughput density-functional-theory resource for materials design, discovery, and prediction [92][120]. It is identified with Materials Project and AFLOWLIB in adaptive-design workflows that use computational data to guide subsequent experiments or calculations [92]. The available evidence does not establish a resource-specific limitation or canonical URL here. Later reviews report OQMD use for testing property-conditioned crystal generators, but those reviews cannot establish an early-2024 status [46][119].

**NOMAD**, also called the **NOMAD laboratory** or **Novel Materials Discovery**, is recognized as an initiative addressing the shortage of reliable, diverse, machine-readable materials data [90]. This supports its relevance to machine-learning discovery, but the cited evidence does not resolve the Repository’s exact data schema, coverage, official URL, common-use level, or resource-specific limitations. The same evidence cautions that computational assumptions can introduce errors and that failed experiments are often absent from training data [90].

**JARVIS-DFT** is a NIST-JARVIS data resource. The associated JARVIS-ML service provides model parameters, descriptors, and machine-learning input and target data; CFID and JARVIS-DFT data have supported classification and regression models for fast materials screening and energy-landscape mapping, including formation-energy, exfoliation-energy, band-gap, magnetic, dielectric, thermoelectric, and piezoelectric properties [53]. The official page available here is `https://www.nist.gov/programs-projects/jarvis-ml`, but it does not establish that page as the canonical JARVIS-DFT URL or state resource-specific limitations [53]. A later source expands JARVIS as “Joint Automated Repository for Various Integrated Simulations” and reports broader integrated capabilities, but that evidence is outside the cutoff [47].

For **Crystallography Open Database (COD)**, pre-cutoff evidence is strongest for its predicted component, **PCOD**: 331,163 hypothetical zeolites supplied neural-network training data, and generated structures were compared with IZA/PCOD records; seven of eight generated structures matched the test sets while one was unknown [104]. This demonstrates direct relevance to structure generation and validation, but does not by itself establish all-COD common use or the official URL. A later source describes COD as storing inorganic, organic, metal-organic, and mineral structures with unit-cell, volume, space-group, and CIF information; that later description is not used to extend the cutoff [119]. The same qualification applies to **ICSD**: a later source reports approximately 300,000 evaluated inorganic structures with experimental and theoretical entries, but its early-2024 access model, canonical URL, and ML-use frequency remain unresolved here [119].

**Materials Cloud** has direct pre-cutoff relevance as a data ecosystem. Its 25 January 2023 Archive record documents machine-learning and inverse-design discovery of polymer membranes: the training set contains 1,169 homopolymers with permeability, glass-transition temperature, and decomposition-temperature data, while the output set contains 784 optimized candidates generated with inverse-design and machine-learning techniques [57]. A prediction-engine service, regression model, and notebook support the workflow [57]. This establishes research relevance, but does not by itself determine whether the broader Materials Cloud is one database or a platform, nor does the Archive record verify its canonical website URL. A September 2025 article’s claims that Materials Project, AFLOW, OQMD, NOMAD, and Materials Cloud were prominent screening resources, and that JARVIS formed a unified multiscale platform, are outside scope [47].

Materials Project: ML data [170]; AFLOW (Automatic Flow): repository, >1.8M×~100 props (2018) [170]; Open Quantum Materials Database (OQMD): open DFT structures/energies, stability [171]; NOMAD: FAIR Repo/Archive, 3,000 oxides/883 teams (2019) [172]; Inorganic Crystal Structure Database (ICSD): structures/fingerprints; stability needs energy [171]

Materials Project: open DFT thermodynamic/structural data; ML/GNoME use (≈69,000 materials, 2018 snapshot; March 2021) [173][94]. OQMD: open DFT data; June 2021 GNoME snapshot; cubic-dominated [173][94]. AFLOW: first-principles database; JARVIS: data-driven design; Materials Cloud: platform/database status unresolved [173][176]. NOMAD: 2018 competition, 3,000 compounds (2,400 train/600 test), band-gap and formation-energy targets [127]. COD: open experimental/theoretical small–medium-cell structures; CIF/SQL at http://www.crystallography.net [174]. ICSD: licensed inorganic structures; ML/recommender training; 20,000-CIF/year Campus limit and API agreement [175][176].

**AFLOW.** A 2017 account describes AFLOW as a high-throughput repository with more than 1.7 million entries, DFT properties for experimentally observed and theoretically predicted structures, REST/AFLUX search, and AFLOW-ML structure-to-property prediction. [177][178] Official portal: https://aflow.org [177]

**Inorganic Crystal Structure Database (ICSD).** The official brochure gives the canonical name and URL, https://icsd.fiz-karlsruhe.de. [71] It reports more than 200,000 peer-reviewed, completely determined inorganic structures dating from 1913 and about 7,000 additions per year; theoretical structures support new-material development and structure/property prediction. Web, Desktop, and STN access options qualify its use. [71]

**Materials Cloud.** Its official page names Materials Cloud but does not establish a single database: it describes a CSCS-hosted platform, Ceph/S3 storage, an Azure-hosted Archive, and DOI-backed records. [179] Mark its database status unresolved.

**Materials Project and OQMD.** A pre-cutoff inverse-design reference identifies both as databases for calculated properties and gives their portals as materialsproject.org and oqmd.org. [133]

Materials Project—ML data for prediction/screening [98]; OQMD—DFT formation energies and phase stability for discovery [74]; JARVIS-DFT—calculated properties for ML design [181]; ICSD—structures for prediction/validation, https://icsd.nist.gov/ [165][95]; AFLOW—searchable entries/properties via AFLUX, https://aflow.org/ [184].

AFLOW-ML predicts electronic, thermal/thermomechanical, vibrational and superconducting properties from structures or compositions; **>26,674 materials (9 Sep 2021)** were used for training, and PLMF–XtalOpt genetic-algorithm searches found superhard carbon phases. [130] AFLOWlib supplied **5,244 compounds (16 Jun 2020)** for GB/RF/ANN/SVM predictions of Debye temperature and Grüneisen parameter. [185]

AFLOW-CCE (**27 Oct 2023**) reduced oxide/nitride DFT deviations from a few hundred to **~25 meV/atom** with structural inputs; this result is module-specific. [54] DFT may take days–months; AFLOW is open-source/Linux-native, but macOS/Windows need extra software. [130][81] Evidence establishes recognition, not popularity, and no explicit taxonomy assignment. [80][186]

AFLOW (Automatic FLOW) is a high-throughput ab-initio/DFT database/repository of searchable structures and calculated properties for ML training, screening, stability and candidate selection; GUI, AFLUX and REST APIs enable access. Its 2021 source reports >3.5M entries and >700M properties. Official URL: https://aflow.org/ [69][188][189][190]

| Resource | Supported answer |
|---|---|
| **OQMD** | **The Open Quantum Materials Database (OQMD)** is an open high-throughput DFT resource containing ICSD/prototype structures, formation energies, band gaps, magnetic and stability data; its API and downloads support ML ranking, structure prediction and GAN/CVAE generation [343,360,274,451]. It is recognized and widely used, but not quantitatively ranked [343,448]. Reported snapshots vary: ~300,000 DFT calculations (2015), 606,115 compounds (2020), >1 million data (2023), and ~700,000 API-accessible materials [449,331,448,451]. Official URL: https://oqmd.org [128]. |
| **ICSD** | **Inorganic Crystal Structure Database (ICSD)** supplies crystal structures for OQMD/ML: an ICSD-trained prototype ranker reported 85% correct ranking at Δ#=0.7; a GAN used 28,137 filtered compounds; and a VAE extracted 2,021 phases in a 148-dimensional space [360,331,274]. It supports generation and validation, but its access model and popularity denominator remain unresolved [303,274]. Source-listed URL: http://icsd.fiz-karlsruhe.de [105]. |
| **COD** | **Crystallography Open Database (COD)** is an open-access crystal-structure collection and worldwide-collaboration platform, relevant as structural input; no specific ML workflow, popularity denominator or URL is established in these cards [111]. |
| **Materials Project** | Its API supplied 7,189 CIFs covering binary alloys, perovskites and Heuslers for VAE, 3-D U-Net and CGCNN structure generation/property prediction [111]; its URL is unresolved in this part. |
| **NOMAD Repository** | A materials-data-sharing resource linked to artificial intelligence; detailed scope and URL are unresolved in this part [111]. |
| **JARVIS-DFT/JARVIS** | The Joint Automated Repository for Various Integrated Simulations is a library/database project for data-driven materials design; JARVIS-DFT-specific scope and URL are not established here [105]. |

OQMD=Open Quantum Materials Database: DFT thermo/structure; search/API; screen/ML; oqmd.org [156][180]. Citrination=DB create/share; MDF dispatch; URL/methods unresolved [195]. MDF=publish/enrich/search; 30TB (2019); materialsdatafacility.org [195]. COD=open structures; ICSD=inorganic, access unknown; NOMAD=FAIR/big-data, inventory unknown [196]

**JARVIS-DFT**

JARVIS-DFT is NIST’s DFT database in the Joint Automated Repository for Various Integrated Simulations (JARVIS), alongside JARVIS-FF, JARVIS-ML and JARVIS-Tools [76]. It supports screening, prediction and inverse design. A 2020 paper reported ~40,000 materials and ~1 million calculated properties; NIST’s 18 October 2023 update reported >80,000 materials and millions of properties—date-specific snapshots [204][85]. Coverage includes 3D bulk, 2D monolayers, 1D nanowires and 0D molecules; properties include formation energy, band gap, elastic/dielectric/piezoelectric/magnetic data, exfoliation energy, phonons, spin–orbit spillage, optical/solar, infrared, heterojunction and Wannier data. It uses OptB88vdW/TBmBJ, with subsets using higher-level methods and spin–orbit coupling [76][204]. The 2023 update noted experimental data, graph-neural-network design, benchmarking, and superconducting, 2D-magnetic, MOF, defect and interface classes, emphasizing openness and reproducibility [85].

CFID encodes crystal structures in **1,557 descriptors per material**; DFT targets use an approximately **90:10** train/test split with cross-validation and uncertainty analysis, supporting rapid classification/regression, screening and energy-landscape mapping [204]. JARVIS-ML documents neural networks, Gaussian processes, decision trees, graph-convolutional networks and LightGBM [203]. JARVIS-DFT feeds JARVIS-ML/FF, and ML accelerates those components [76]. It is a notable relevant resource, not a popularity ranking; sources do not assign it to the three taxonomy categories or establish category-specific advantages and disadvantages [76][85][203]. An older sheet said “under development” and recorded **873 VASP calculations (>25,000 sub-calculations)**; this is historical only [131].

JARVIS-DFT (Joint Automated Repository for Various Integrated Simulations): DFT repository of crystalline-material properties—≈40,000 materials and ≈1 million calculated properties (source published 2020) [206][207]. Pre-2024 work used it for inverse generation, screening and validation [60][208]. Official: https://jarvis.nist.gov/ [206].

JARVIS-DFT: ML/DFT/FF/exp discovery, 50+ pubs; 80,000+ materials, millions props; https://jarvis.nist.gov/jarvisdft [210]; COD: open crystal structures; search/download, ML use; >450,000 entries; http://www.crystallography.net [211][212][101]. ICSD: inorg structs; >187,000 entries (2017), licensed; https://icsd.fiz-karlsruhe.de (canonical?) [137]

**Crystallography Open Database (COD):** Open-access FAIR CIF crystal-structure collection; CC0-derived 3-D data support ML. Revision 265250 (19 Dec 2023): 473,500 CIFs, ~68% described [101]. URL: https://www.crystallography.net/cod [101]; no ranking denominator [101].

ICSD (“NIST Inorganic Crystal Structure Database”): >210k inorganic structures (from 1913), searchable/computable; subscription-only [51]. https://icsd.fiz-karlsruhe.de [102]. 2023.2=291,333 coord. [124]. ML:~15k ICSD materials trained an energy model [42]. Citrination:~5k metallic-glass + ~2k nonmetallic-glass records for classification [107].

ICSD—Inorganic Crystal Structure Database: curated inorganic structures/properties/API; >290k structures, 2×/yr (oldest 1913); GAN use; common-use unproven; customer-only; icsd.products.fiz-karlsruhe.de [220][39]. MC—Materials Cloud: platform, not DB; FAIR archive/workflows/ML data; recognized; pop. unresolved; www.materialscloud.org [63][56][221]

|Name|Function/status|Official URL|
|---|---|---|
|**Citrination/Open Citrination**|Materials/chemicals database/platform; ML prediction/design/inverse calibration; FCC-Cu and sequential-learning use [65][121][229]. Decommissioned **19 Sep 2022**: public datasets remained downloadable; private data and ML/analysis/visualization unavailable [87]. **18 Dec 2018** scholarly use (no ranking); Terms **17 Jul 2018** [229][65].|https://citrination.com/ (listed; canonical caveat) [65][66]|
|**Materials Data Facility (candidate)**|Repository candidate; labels “MDF Open”/“MDF”; **93** organization results and **29** ML-tagged; name/function/cutoff/URL unresolved. Page mixes **2020–24** with 2025–26 [230].|Unresolved [230]|

- **Materials Data Facility (MDF)** — **Name/URL:** Materials Data Facility (MDF), `https://www.materialsdatafacility.org/` [231]. **Function:** a materials-data repository/service for publication and discovery, metadata extraction, persistent identifiers, REST APIs, unified search, and simulation- and experiment-derived datasets [233][232]. A paper published **23 January 2024** reports **30 Foundry-ML datasets as of Q1 2023** and support for **multi-TB databases with potentially millions of files**, accessible through Foundry-ML, Python/web, Globus, and HTTPS [238]. A 2021 NIST report and a 2023 materials-data paper recognize MDF as a data-sharing or aggregation resource, but do not establish a common-use denominator or direct inverse-design study [236][237]. Undated pages additionally report **40 TB**, hundreds of indexed datasets, millions of metadata records, and **880+ published/60+ ML-ready datasets**; these figures are not a 31 March 2024 snapshot [232][231]. MDF is therefore best labeled a repository/data-platform candidate rather than a confirmed commonly used inverse-design database. The acronym must not be confused with DOE’s different **Manufacturing Demonstration Facility** at Oak Ridge [239].

- **Materials Project (MP)** — **Name/URL:** Materials Project (MP), `https://materialsproject.org` [241][244]. MP is a searchable database of solid-state materials and molecules with calculated and experimental properties; its high-throughput first-principles data, API/pymatgen access, composition/property search, stability analysis, and structure/substitution tools support model training, screening, target-property selection, and experiments [240][243][245][246]. As of **15 February 2024**, it reported **more than 154,000 materials, over 172,000 molecules, and millions of properties**; its reported **over 400,000 registered researchers** and **over 19,000 citations** indicate broad recognition, not a comparable inverse-design usage denominator [240]. Because calculations and correction schemes evolve, users should record versions, accuracy limits, and experimental validation requirements [241][242][246].

- **Citrination** — The source associates Citrination with **Citrine Informatics**, an enterprise software platform using generative AI and materials science for materials and chemicals development; it identifies `citrination.com` as the site [70]. Its status as a database, pre-cutoff common use, taxonomy or algorithm role, and comparative advantages and limitations remain unestablished in this evidence group.

Materials Project supports a machine-learning materials-discovery report by supplying computed structures and properties, training and reference data, and pre-computed catalyst adsorption energies for an Offline/Deep-RL inverse-catalyst workflow [34][44].

At the stated early cutoff, represent Materials Project as a core computational data source and a concrete inverse-design example: its open-access catalyst properties, materials library, and surrogate-model training data support reinforcement-learning and property-guided search [44][36][37]. Because the service distinguishes legacy and next-generation interfaces and data states, identify the accessed release and current site rather than treating it as a timeless snapshot [160].

Materials Project supplies in-house computed structures and properties—including crystal structures, DOS, charge densities, energies, elastic and transport data—through searchable web and API access; the cited description reported over 33 000 compounds [138][100][99][109]. These data support training and reference sets, candidate-library generation, surrogate evaluation, screening, and inverse optimization [36][37][44].

AFLOW supports the report through automated high-throughput DFT data, searchable and downloadable structures and properties, AFLUX/REST access, and AFLOW-ML predictions for machine-learning screening; one cited scope is > 26,674 materials [130][184][189][52].

Include AFLOW in the early-cutoff overview as integrated, FAIR computational-discovery infrastructure—especially its high-throughput repositories, APIs, and AFLOW-ML—rather than as a popularity-ranked database; one source reports > 3.5 million entries and > 700 million properties [192][187][130].

AFLOW provides queryable and downloadable stoichiometry, formation enthalpies, geometries, prototypes, and other DFT outputs, while AFLUX/REST and AFLOW-ML support programmatic retrieval and structure-to-property prediction [169][184][129][52]. This makes it useful for model training, fast screening, and inverse-design candidate generation, with a reported scope of > 26,674 materials [154][130].

OQMD supports a machine-learning materials-discovery report because its large first-principles and high-throughput DFT collection supplies structures, thermodynamic and other property data, compositions, and phase-diagram tools for screening and candidate narrowing; OQMD data are widely used to train and validate machine-learning models [128][193][180][125].

At the cutoff, represent OQMD as an open high-throughput DFT resource focused on energetics and thermodynamics, not as a fixed-size ranking: reported snapshots range from 285,780 compounds to >1.3 million, and the resource is CC-BY-4.0 [180][43][194][140]. This version-aware description preserves its role in systematic theoretical-materials exploration while avoiding an unjustified popularity claim [142][149].

OQMD provides DFT-calculated formation energies, band gaps, crystal structures, compositions, and phase diagrams, with searchable analyses and raw data made available through NOMAD; these data support machine-learning training and validation, property screening, and inverse search over more than one million compounds [193][180][152][136][125].

NOMAD supports the report through searchable, accessible, reusable FAIR materials-data infrastructure, browser-based AI analysis, tutorials, and reproducible workflows; cited use evidence includes 883 teams and a 3,000-compound challenge [132][135][172][127].

code=rejected; reason=citation_outside_operands; allowed numbers=[September 2021|883 teams|""|17 May 2004|about 40 codes|more than 40 computer codes|40 different codes|26 May 2016|17 000 calculations|GNU General Public License v3.0|3,000|2023|> 26,674 materials|June 2021|3,000 compounds|more than 450,000 entries|∼15 000 materials|> 100,000 inorganic materials|40 TB|30 TB|60+ ML-ready datasets|2023.2|1913|30 datasets|2018|331,163 hypothetical zeolites|approximately 69,000 materials|273 features|27 Oct 2023|784 homopolymers]; allowed citations=[3,4,6,8,25,31,37,45,59,60,62,67,69,78,80,81,82,87,91,96,98,102,108,109,124,134,136,139,142,152,174,178,216,234,261,263,272,304,308,309,313,314,316,317,318,319,321,322,324,336,340,341,343,345,348,349,357,359,363,364,367,368,369,371,373,376,378,381,382,383,386,388,389,398,407,408,412,413,432,436]; allowed entities=[NOMAD Repository|Materials Project|AFLOW|Open Quantum Materials Database|JARVIS-DFT|Crystallography Open Database|Inorganic Crystal Structure Database|Materials Cloud|Citrination|Materials Data Facility]

NOMAD supplies raw inputs and outputs plus normalized, structured quantities, units, and provenance through its Archive, REST API, and Jupyter workflows; data from more than 40 codes can be queried, feature-engineered, and reused for model training, validation, and screening [151][202][200][201].

JARVIS-DFT supports the report by providing downloadable atomistic and DFT structures and property data used for machine-learning screening, energy prediction, and data-driven materials design; its companion JARVIS-ML supplies descriptors, model parameters, and machine-learning input and target data [205][77][197][53].

Include JARVIS-DFT in the cutoff overview as an open DFT/ML data and benchmarking resource within JARVIS, with a documented 90:10 data split and dedicated machine-learning descriptors and models [204][76]. Qualify it as complementary training and screening data, not as evidence of a universal popularity rank [77][210].

JARVIS-DFT provides downloadable JSON and atomistic DFT data, structures, and conventional, electronic, mechanical, and specialized properties; JARVIS-ML adds descriptors and model-related inputs and targets, enabling training, validation, screening, and inverse design [205][197][204][53].

COD supports the report because its open, searchable crystal structures, atomic coordinates, and CIF data can seed property calculations, derived molecular descriptions, and machine-learning inputs; predicted zeolite structures provide a concrete materials-discovery example [158][216][101][104].

Retain COD in the cutoff overview as an open-access and FAIR crystallographic source for structure-based machine learning, while distinguishing it from computed-property repositories; its cited scope exceeds 450,000 entries [214][174][211].

COD provides searchable and downloadable CIFs, atomic coordinates, diffraction and structure-factor data, SQL/SMILES access, and derived powder patterns; CC0 licensing and composition search support descriptor generation, training, and known- or candidate-structure screening [101][212][213][64]. The cited inverse-design example includes 331,163 hypothetical zeolites [104].

ICSD supports the report as a curated, evaluated inorganic-crystal-structure resource for data mining, structure prediction, and optimization, but its access model is subscription/customer-based rather than open: use requires an ICSD customer relationship and full-database login or license [183][220][219]. Its Web/API and CrystalWorks routes supply searchable structures and related calculated-property links for machine-learning workflows [217][218][124].

Represent ICSD in the cutoff overview as a curated experimental inorganic-structure resource, with over 210,000 entries covering literature from 1913 and a documented 2023.2 release; link its calculated-property search to Materials Project but flag the license and access barrier [220][51][124][218][219].

ICSD provides fully determined inorganic structures with unit cells, space groups, atomic coordinates, descriptors, and bibliography for screening, data mining, and structure prediction; its Web/API supports search and retrieval [183][102][218]. The required qualification is an ICSD customer relationship and full user license, with Web, Desktop, Intranet, or API options rather than unrestricted open access [220][219].

Materials Cloud could support the report if platforms qualify under the inclusion rule: it is a web platform for the computational-project lifecycle, powered by AiiDA, with shared workflows, curated and raw data, archive, and discovery tools [63][73][216]. It should therefore be labeled as a qualified data-ecosystem candidate rather than automatically treated as a single database.

Through the cutoff, retain Materials Cloud only as a qualified platform and data-ecosystem candidate: sources describe it as open computational science rather than a narrowly defined database, with an AiiDA-backed lifecycle and over 100000 calculations [158][63][223]. It belongs in the overview for workflow and data-sharing relevance, but not as a standalone database without an explicit inclusion decision [73].

If included, Materials Cloud offers raw and curated computational data, structure databases, full workflows and provenance, and long-term archival and dissemination through AiiDA; these functions support reproducible model training, screening, and inverse-design studies [75][158][216][221]. A documented dataset contains 1,169 calculated homopolymer properties and 784 optimized candidates, illustrating the data role rather than a universal database scope [57].

Conditional on verifying its pre-cutoff function and status, Citrination could support the report through open materials data and infrastructure, extraction and streaming, predictive web models, API access, and design runs; a cited snapshot reports 17m+ free data items [115][225][67][59][114]. Because access required registration and the evidence is date-sensitive, it should not be presented as currently operational without that verification [87][66].

code=rejected; reason=citation_outside_operands; allowed numbers=[2016-05-01|""|2016|~5000; ~2000|2024|7/17/18|18 December 2018|3.1m materials data records|Feb 19, 2026|> 26,674 materials|June 2021|883 teams|3,000|3,000 compounds|more than 450,000 entries|∼15 000 materials|> 100,000 inorganic materials|40 TB|30 TB|60+ ML-ready datasets|2023.2|1913|30 datasets|2018|331,163 hypothetical zeolites|approximately 69,000 materials|273 features|2023|27 Oct 2023|784 homopolymers]; allowed citations=[3,4,6,8,25,31,37,45,69,78,87,88,89,98,101,102,103,108,109,134,139,142,146,152,160,174,178,216,261,263,272,279,308,309,312,313,314,316,318,319,322,324,336,340,341,343,345,348,349,357,359,363,364,367,368,369,371,373,376,378,381,388,389,391,398,399,406,407,408,413,432,436,439,440,441,445,453,462,475,488]; allowed entities=[Citrination|Materials Project|AFLOW|Open Quantum Materials Database|NOMAD Repository|JARVIS-DFT|Crystallography Open Database|Inorganic Crystal Structure Database|Materials Cloud|Materials Data Facility]

Citrination offers data extraction and streaming, PIF-structured data, Data Views, predictive models, t-SNE analysis, and design runs for candidate selection, plus adaptive and sequential learning [225][112][228][59][226]. Its 17m+ free data items and a deprecated ModelsClient method are material access and reproducibility limitations [114][141].

Materials Data Facility is sufficiently related to remain an in-scope candidate: it publishes, discovers, and connects high-quality materials datasets, offers structured ML-ready Foundry data, and reports 60+ ML-ready datasets and 40 TB [166][231][232]. Treat it as data-service infrastructure rather than a settled standalone database, because sources use MDF, MDF Open, and Manufacturing Demonstration Facility labels and early evidence describes a repository or project [230][116][68].

Include MDF in the cutoff overview as qualified materials-data publication and discovery infrastructure: its cloud services support sharing, discovery, and Foundry-ML access, with 60+ ML-ready datasets documented [233][231]. Its role is infrastructural rather than a popularity-ranked database, and the evidence should be dated because the project was publicly announced and developing [68][232].

MDF can support inverse-design research by publishing datasets, applying domain-specific metadata and controls, indexing and connecting independent sources, and exposing structured validated Foundry-ML datasets for machine learning; its documented scale includes 40 TB and 30 datasets in Q1 2023 [157][166][232][238]. This makes it useful for training, validation, and screening, while its service and aggregation model should be distinguished from a single curated property database [61][235].

Materials-inverse-design data resources are justified because computed or experimental structures and properties supply training and validation data, candidate libraries, surrogate-evaluation inputs, and screening targets; Materials Project supplies training and reference data, while AFLOW adds high-throughput data and machine-learning screening [34][36][44][130]. Materials Project and AFLOW therefore connect the data purpose to concrete materials-discovery workflows [37][191].

Use a representative, evidence-supported roster—Materials Project, AFLOW, OQMD, NOMAD Repository, JARVIS-DFT, and COD—rather than a definitive popularity ranking; their documented roles span computed properties, high-throughput search, FAIR multi-code data, DFT/ML data, and open crystal structures [34][130][128][132][204][174]. Compare only like-for-like dated fields and give each row its name, principal function, URL, and use or recognition evidence [143][184][128][49][77][212].

Keep the roster open to qualifying additions such as ICSD, Materials Cloud, Citrination, and MDF, but label subscription, platform, and status uncertainties explicitly; ICSD is licensed, Materials Cloud is a platform, and Citrination and MDF require status or identity verification [220][158][87][230][68]. Any exclusion should state the reason rather than imply a definitive field-wide ranking.

## References

[1] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8159218/> Inverse-design overview; Strategy classification; Exploration and evaluation roles; Synthesizability challenge; Evaluation and experimental feedback; High-thro…
[2] <https://www.nature.com/articles/s41524-023-01128-y> Continuous-action search; Actions and scoring in CASTING; CASTING framework; Silver scaling tests; Carbon search behavior
[3] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8911677/> Forward and inverse mappings; Materials applications; Ill-posed inverse problems; HTVS boundaries; RNN-based design; Simulator-dependent GAN example; Target-pr…
[4] <https://doi.org/10.1038/s41467-023-42068-x> Truss-design representation; Manufacturable truss design; Truss dataset and model; Reconstruction, prediction, and sampling results; VAE regularization trade-o…
[5] <https://engrxiv.org/preprint/download/2845/5279/4133> Inverse and tandem networks; Inverse and surrogate modeling; Inverse-network strengths and boundaries; ZeoGAN property targeting; Extrapolation and model updat…
[6] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9385454/> Property and feasibility requirements; Property-directed generation; Porous-material GAN example; Representation challenges; Inorganic-data scarcity; Generativ…
[7] <https://www.nature.com/articles/npjcompumats201510> Formation energy and phase stability; Database construction; Interpretation of prototype predictions; 2015 OQMD inventory; Formation-energy assessment; Cross-d…
[8] <https://www.nature.com/articles/s41524-020-00352-0> MatGAN evaluation criteria; Conditional sampling example; GAN operation; MatGAN results; MatGAN structural boundary; Band-gap-biased MatGAN; MatGAN coverage an…
[9] <https://link.springer.com/article/10.1557/mrc.2019.40> Feedback-guided search; Exploration–exploitation balance; MCTS algorithm; Grain-boundary search results; Tree-search strengths; MCTS evaluation bottleneck; Lar…
[10] <https://arxiv.org/html/2309.02646v2> RL mechanism in materials design; Materials RL applications; Surrogate-driven inverse optimization; Local-optimum concerns; Optimizer variability; Search-metri…
[11] <https://doi.org/10.3389/fmats.2023.1233961> Property-structured latent spaces; Latent-model failure modes; Evolutionary latent-space operations; EVAPD architecture and data; EVAPD candidate results; EVAP…
[12] <https://doi.org/10.1038/s41524-022-00923-3> CDVAE architecture; Periodic generation mechanism; Two-dimensional discovery results; Generation versus decoration; Equivariant CDVAE components; Two-dimension…
[13] <https://doi.org/10.1038/s41524-021-00662-x> Bayesian optimization mechanism; Adaptive surrogate motivation; MAX-phase benchmark; High-dimensional BO boundaries
[14] <https://doi.org/10.1038/s41598-020-60652-9> Mixed-variable Bayesian optimization; Perovskite mixed-variable results; OQMD-supported materials exploration
[15] <https://arxiv.org/abs/2006.06141> CAMEO autonomous discovery
[16] <https://docs.materialsproject.org/> Materials Project documentation; Official project description
[17] <https://www.oqmd.org/> OQMD; Official OQMD portal
[18] <https://www.aflowlib.org/> AFLOW; Official AFLOW search interface
[19] <https://jarvis.nist.gov/> NIST JARVIS; Official NIST JARVIS portal
[20] <https://materialsproject.org/>
[21] <https://www.fair-di.eu/events/big-data-ai-in-materials-science/exercise-1> NOMAD Repository and Archive; Official Repository and Archive tutorial; Metadata and search functions; NOMAD normalization
[22] <https://www.materialscloud.org/> Materials Cloud; Official Materials Cloud description; Archive and FAIR functions
[23] <https://www.crystallography.net/cod/> COD; Official COD scope
[24] <https://nomad-lab.eu/prod/rae/gui/search>
[25] <https://www.energy.gov/science/articles/search-engine-materials-data-how-materials-project-advances-research> DOE February 2024 account; DOE data description
[26] <https://docs.materialsproject.org/methodology/molecules-methodology/overview> Materials Project molecular methodology
[27] <https://nomad-laboratory.de/uploads/publications/th/Draxl_2019_J._Phys._Mater._2_036001.pdf> AFLOW scope in the database survey; Earlier NOMAD inventory
[28] <https://www.nature.com/articles/s41524-020-00440-1> 2020 infrastructure paper; JARVIS 2020 inventory; JARVIS-ML and descriptors; JARVIS materials-screening workflow
[29] <https://nomad-lab.eu/>
[30] <https://www.nature.com/articles/s41524-022-00935-z> 2022 NOMAD account; NOMAD data architecture
[31] <https://www.nature.com/articles/s41597-020-00637-5> AiiDA workflow and provenance; 2020 platform paper; Database interoperability; Materials Cloud provenance
[32] <https://pmc.ncbi.nlm.nih.gov/articles/PMC3253730/> COD data organization; COD and PCOD status report; COD validation and duplicates
[33] <http://arxiv.org/abs/2511.03112>
[34] <https://doi.org/10.1038/s41524-023-01128-y>
[35] <https://hdl.handle.net/21.11116/0000-0012-DCC7-4>
[36] <https://doi.org/10.1063/5.0177266>
[37] <https://www.nature.com/articles/s41524-023-01128-y>
[38] <https://doi.org/10.48550/arxiv.2212.12106>
[39] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8911677/>
[40] <https://doi.org/10.1021/acs.jpcc.1c02438>
[41] <https://arxiv.org/html/1811.06060>
[42] <https://pubs.rsc.org/en/content/articlehtml/2020/sc/d0sc00594k>
[43] <https://doi.org/10.1002/adma.202523620>
[44] <https://doi.org/10.48550/arxiv.2312.02308>
[45] <https://doi.org/10.1088/0256-307x/42/2/027403>
[46] <https://doi.org/10.3390/cryst15110925>
[47] <https://www.sciencedirect.com/science/article/abs/pii/S0927025625004069>
[48] <https://ceder.berkeley.edu/publications/2013_Jain_Materials_Project.pdf>
[49] <https://www.re3data.org/repository/r3d100011583>
[50] <https://par.nsf.gov/biblio/10686261-probabilistic-inverse-design-metasurfaces-using-mixture-density-neural-networks>
[51] <https://icsd.nist.gov/>
[52] <https://aflow.org/aflow-ml/>
[53] <https://www.nist.gov/programs-projects/jarvis-ml>
[54] <http://arxiv.org/abs/2310.18187v1>
[55] <https://zenodo.org/records/7860342>
[56] <https://www.marvel-nccr.ch/news/communication/MCA-500>
[57] <https://archive.materialscloud.org/record/2023.14>
[58] <https://par.nsf.gov/servlets/purl/10134745>
[59] <https://citrineinformatics.github.io/python-citrination-client/tutorial/models_examples.html>
[60] <https://www.nist.gov/publications/forward-and-inverse-design-high-tc-superconductors-dft-and-deep-learning>
[61] <https://nanohub.org/groups/nanomfg/File:/uploads/MDF_DLHub-Foster-UIUC.PDF>
[62] <https://doc.docs.materialsproject.org/database-updates/>
[63] <https://nccr-marvel.ch/news/communication/2018-02-materials-cloud-is-online>
[64] <https://www.crystallography.net/cod/mysqlcod.html>
[65] <https://citrination.com/tos>
[66] <https://www.re3data.org/repository/r3d100012077>
[67] <https://github.com/CitrineInformatics/learn-citrination>
[68] <https://voices.uchicago.edu/compinst/press-releases/materials-data-facility-launches-support-material-genome-initiative/>
[69] <https://aflow.org/documentation/>
[70] <https://citrine.io/media-post/citrination-redesign/>
[71] <https://icsd.products.fiz-karlsruhe.de/sites/default/files/ICSD/documents/brochures/ICSD-Inorganic-Crystal-Structure-Database.pdf>
[72] <https://acdc.alcf.anl.gov/mdf/>
[73] <https://www.nature.com/articles/s42004-024-01143-0>
[74] <https://doi.org/10.1038/npjcompumats.2015.10>
[75] <https://www.materialscloud.org/>
[76] <https://arxiv.org/pdf/2007.01831>
[77] <https://tsapps.nist.gov/publication/get_pdf.cfm?pub_id=930588>
[78] <https://scepscor.org/mgi-databases/>
[79] <https://arxiv.org/abs/1803.05035>
[80] <https://arxiv.org/abs/2207.09842>
[81] <https://materials.duke.edu/aflow.html>
[82] <https://doi.org/10.1016/j.isci.2021.102781>
[83] <https://www.nist.gov/srd/nist-standard-reference-database-84>
[84] <https://citrineinformatics.github.io/python-citrination-client/tutorial/initialization.html>
[85] <https://www.nist.gov/publications/recent-progress-jarvis-infrastructure-next-generation-data-driven-materials-design>
[86] <https://perssongroup.lbl.gov/papers/jain-2018-mp.pdf>
[87] <https://fairsharing.org/FAIRsharing.x6y19r>
[88] <https://doi.org/10.1038/s42256-025-01055-1>
[89] <https://doi.org/10.1039/d1mh00495f>
[90] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9585593/>
[91] <https://arxiv.org/html/2309.02646v2>
[92] <https://doi.org/10.1038/s41524-019-0153-8>
[93] <https://ar5iv.labs.arxiv.org/html/1807.05617>
[94] <https://www.nature.com/articles/s41586-023-06735-9>
[95] <https://www.law.berkeley.edu/wp-content/uploads/2024/02/Merchant-Scaling-deep-learning-for-materials-discovery.pdf>
[96] <https://journals.sagepub.com/doi/full/10.3233/SW-233340>
[97] <https://pubs.acs.org/pcrhej/article/4/8/1087/5232753/Materials-Databases-Foundations-of-Modern-Digital>
[98] <https://www.nature.com/articles/s41524-022-00750-6>
[99] <https://www.nature.com/articles/s41524-018-0129-0>
[100] <https://arxiv.org/html/2312.00111v1>
[101] <https://link.springer.com/article/10.1186/s13321-023-00780-2>
[102] <https://icsd.products.fiz-karlsruhe.de/sites/default/files/ICSD/documents/brochures/ICSD-Reliable-Crystal-Structure-Data.pdf>
[103] <https://doi.org/10.1002/mgea.30>
[104] <https://www.science.org/doi/10.1126/sciadv.aax9324>
[105] <https://www.frontiersin.org/journals/materials/articles/10.3389/fmats.2022.865270/full>
[106] <https://ar5iv.labs.arxiv.org/html/2112.03528>
[107] <https://doi.org/10.1038/s41524-023-00968-y>
[108] <https://doi.org/10.1038/s41524-024-01259-w>
[109] <https://doi.org/10.1063/1.4812323>
[110] <https://doi.org/10.1007/s11467-023-1325-z>
[111] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7592118/>
[112] <https://pubs.aip.org/aip/jcp/article/154/22/224201/313373/Utilization-of-machine-learning-to-accelerate>
[113] <https://doi.org/10.1557/mrs.2018.207>
[114] <https://chimad.northwestern.edu/docs/2016DATA_documents/BryceMeredigCitrine-MGISummit.pdf>
[115] <https://www.energy.gov/documents/analyzing-large-scale-data-solve-applied-problems-materials-rdb-meredigpdf>
[116] <https://www.energy.gov/documents/ai-applied-materials-discovery-and-designworkshop-summary-reportpdf>
[117] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9419423/>
[118] <https://github.com/WanyuGroup/AI-for-Crystal-Materials>
[119] <https://arxiv.org/html/2408.08044v4>
[120] <https://doi.org/10.1038/s41598-018-21936-3>
[121] <https://nanohub.org/resources/citrinetools>
[122] <https://doi.org/10.1021/acs.jpclett.3c01260>
[123] <https://doi.org/10.1088/2515-7639/ac7ba9>
[124] <https://cds.dl.ac.uk/cgi-bin/news/disp?icsd=>
[125] <https://iopscience.iop.org/article/10.1088/2515-7639/ac7ba9/pdf>
[126] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8600243/>
[127] <https://doi.org/10.1038/s41524-019-0239-3>
[128] <https://mat-dacs.dxmt.nims.go.jp/en/list/1358>
[129] <https://aflowlib.org/aflow-school/past_schools/20220221/04_aflow_school_ml.pdf>
[130] <https://aflow.org/aflow-school/past_schools/20210906/09_aflow_school_ml.pdf>
[131] <https://www.nist.gov/document/jarvis-mgipdf>
[132] <https://doi.org/10.1557/mrc.2020.2>
[133] <https://www.academia.edu/38895289/Inverse_design_in_search_of_materials_with_target_functionalities>
[134] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7716341/>
[135] <https://www.nature.com/articles/s41524-022-00935-z>
[136] <https://chimad.northwestern.edu/docs/DDD_WS_II/11_Wolverton_The_OQMD_Vinay_Logan.pdf>
[137] <https://datascience.codata.org/articles/10.5334/dsj-2017-038>
[138] <https://docs.materialsproject.org/frequently-asked-questions>
[139] <https://perssongroup.lbl.gov/papers/spottesmith_database_molecular_2023.pdf>
[140] <https://nomad-laboratory.de/uploads/publications/th/Draxl_2019_J._Phys._Mater._2_036001.pdf>
[141] <https://citrineinformatics.github.io/python-citrination-client/index.html>
[142] <https://pure.mpg.de/rest/items/item_3684784_3/component/file_3684785/content>
[143] <https://perssongroup.lbl.gov/papers/ye-2018-mp-ml.pdf>
[144] <https://arxiv.org/abs/2210.13597>
[145] <https://doi.org/10.48550/arxiv.1811.08464>
[146] <https://doi.org/10.1103/physrevmaterials.2.123801>
[147] <https://doi.org/10.1103/physrevmaterials.2.043802>
[148] <https://iric.imet.ac.ru/PDF/166.pdf>
[149] <https://arxiv.org/pdf/2312.11335>
[150] <https://zenodo.org/records/8200972>
[151] <https://iopscience.iop.org/article/10.1088/2515-7639/ab13bb>
[152] <https://joss.theoj.org/papers/10.21105/joss.05388.pdf>
[153] <https://ar5iv.labs.arxiv.org/html/1910.02336>
[154] <https://arxiv.org/html/1308.5715v1>
[155] <https://nomad-lab.eu/nomad-lab/nomad.html>
[156] <https://www.nist.gov/mgi/chimad-resources>
[157] <https://www.osti.gov/biblio/1393151>
[158] <https://www.nature.com/articles/s41597-020-00637-5>
[159] <https://www.slideshare.net/slideshow/citrinationmrs-fall-meeting-2015/55956972>
[160] <https://matsci.org/t/legacy-materials-project-website-temporarily-in-degraded-status/44750>
[161] <https://www.nature.com/articles/s43588-020-00016-5>
[162] <https://doi.org/10.1038/s41524-021-00557-x>
[163] <https://doi.org/10.1038/s41597-020-00637-5>
[164] <https://www.nature.com/articles/sdata201853>
[165] <https://www.nist.gov/programs-projects/crystallographic-databases>
[166] <https://www.materialsdatafacility.org/>
[167] <https://citrine.io/the-materials-data-facility-data-services-to-advance-materials-science-research/>
[168] <https://github.com/anhender/mse_ML_datasets>
[169] <https://doi.org/10.1016/j.commatsci.2014.05.014>
[170] <https://s4e.ai/media/publications/10.1557_mrs.2018.207.pdf>
[171] <https://www.nature.com/articles/npjcompumats201510>
[172] <https://nomad-laboratory.de/uploads/Research%20docs/report_on_the_nomad_laboratory2019.pdf>
[173] <https://doi.org/10.1016/j.actamat.2022.118353>
[174] <https://doi.org/10.1093/nar/gkr900>
[175] <https://www.fiz-karlsruhe.de/sites/default/files/ICSD/documents/brochures/scientific-manual-2021-en.pdf>
[176] <https://www.nature.com/articles/s41524-022-00899-0>
[177] <https://arxiv.org/html/1712.00422>
[178] <https://www.nature.com/articles/ncomms15679.pdf?error=cookies_not_supported&code=8b528d52-1731-4034-9111-3ae04a6e17d5>
[179] <https://www.materialscloud.org/infrastructure>
[180] <https://ce.northwestern.edu/magazine/fall-2014/materials-database.html>
[181] <https://jarvis-materials-design.github.io/dbdocs/jarvisdft/>
[182] <https://www.nature.com/articles/s41524-024-01259-w>
[183] <https://icsd.products.fiz-karlsruhe.de/en/about/about-icsd>
[184] <https://aflow.org/aflow-school/past_schools/20220921/03_aflow_school_database.pdf>
[185] <https://doi.org/10.1109/usbereit48449.2020.9117689>
[186] <https://arxiv.org/pdf/2207.09842>
[187] <https://entropy4energy.ai/media/publications/10.1016_j.commatsci.2022.111889.pdf>
[188] <https://www.aflow.org/>
[189] <https://aflow.org/aflow-school/past_schools/20220221/00_aflow_school_introduction.pdf>
[190] <https://aflow.org/aflow-school/past_schools/20210906/08_aflow_school_database_aflux.pdf>
[191] <https://aflow.org/aflow-school/past_schools/20210712/00_aflow_school_introduction.pdf>
[192] <https://aflow.org/aflow-school/past_schools/20210729/0_aflow_school_introduction.pdf>
[193] <https://ma.issp.u-tokyo.ac.jp/en/app/6334>
[194] <https://resources.psdi.ac.uk/data/optimade-oqmd-oqmd>
[195] <https://arxiv.org/pdf/1904.10423>
[196] <https://doi.org/10.1002/adts.201900131>
[197] <https://tsapps.nist.gov/publication/get_pdf.cfm?pub_id=959617>
[198] <https://www.nature.com/articles/s41524-021-00495-8/tables/1>
[199] <https://www.datacc.org/en/warehouses/nomad-repository-novel-materials-discovery/>
[200] <https://doi.org/10.1038/s41524-022-00935-z>
[201] <https://www.fairmat-nfdi.eu/fairmat/projects-fairmat/story-fairmat>
[202] <https://nomad-lab.eu/prod/rae/docs/metainfo.html>
[203] <https://jarvis-materials-design.github.io/dbdocs/jarvisml/>
[204] <https://doi.org/10.1038/s41524-020-00440-1>
[205] <https://www.ctcms.nist.gov/~knc6/documentation>
[206] <https://www.nist.gov/publications/joint-automated-repository-various-integrated-simulations-jarvis-data-driven-materials>
[207] <https://www.nist.gov/programs-projects/jarvis-dft>
[208] <https://jarvis-tools.readthedocs.io/en/master/publications.html>
[209] <http://catalog.data.gov/dataset/jarvis-joint-automated-repository-for-various-integrated-simulations>
[210] <https://jarvis.nist.gov/>
[211] <https://nanocrystallography.research.pdx.edu/databases/>
[212] <https://chateigner.ensicaen.fr/pdf/Grazulis_NAR40_D420.pdf>
[213] <https://qiserver.ugr.es/cod/new.html>
[214] <https://pmc.ncbi.nlm.nih.gov/articles/PMC3245043/>
[215] <https://www.crystallography.net/cod/index.php>
[216] <https://ar5iv.labs.arxiv.org/html/2107.09619>
[217] <https://libguides.mit.edu/icsd-mit>
[218] <https://icsd.fiz-karlsruhe.de/>
[219] <http://icsd.iqfr.csic.es/icsd/>
[220] <http://www.fiz-karlsruhe.de/en/produkte-und-dienstleistungen/inorganic-crystal-structure-database-icsd>
[221] <https://doi.org/10.5281/zenodo.19706846>
[222] <https://www.materialscloud.org/team/>
[223] <https://www.materialscloud.org/swissuniversities>
[224] <https://archive.materialscloud.org/about>
[225] <https://chimad.northwestern.edu/docs/DDD_WS_II/9_Meredig_Citrine-CHiMaD.pdf>
[226] <https://doi.org/10.2172/1630122>
[227] <https://citrine.io/perspective-interactive-material-property-databases-through-aggregation-of-literature-data/>
[228] <https://citrineinformatics.github.io/python-citrination-client/tutorial/view_examples.html>
[229] <https://link.springer.com/article/10.1007/s40192-018-0123-x>
[230] <https://acdc.alcf.anl.gov/mdf/?filter-match-any.dc.subjects.subject=experiment&filter-match-any.mdf.resource_type=dataset&page=1&q=%2A>
[231] <https://huggingface.co/foundry-ml>
[232] <https://labs.globus.org/projects/mdf.html>
[233] <https://www.anl.gov/argonne-scientific-publications/pub/131746>
[234] <https://www.materialsdatafacility.org/guides>
[235] <https://connect.materialsdatafacility.org/>
[236] <https://nvlpubs.nist.gov/nistpubs/ir/2021/NIST.IR.8364.pdf>
[237] <https://www.nature.com/articles/s41597-023-02107-0>
[238] <https://par.nsf.gov/servlets/purl/10617062>
[239] <https://www.energy.gov/cmei/ammto/manufacturing-demonstration-facility-mdf-oak-ridge-national-laboratory>
[240] <https://www.energy.gov/science/articles/search-engine-materials-data-how-materials-project-advances-research>
[241] <https://docs.materialsproject.org/changes>
[242] <https://legacy.materialsproject.org/>
[243] <https://legacy.materialsproject.org/open>
[244] <https://docs.materialsproject.org/>
[245] <https://www.mgi.gov/content/materials-project>
[246] <https://newscenter.lbl.gov/2020/05/08/materials-project-qa-persson/>
[247] <https://www.optimade.org/providers-dashboard/providers/oqmd.html>
