# Alternative Metals for Advanced Semiconductor Interconnects

**Ru leads the scaled-line case.** Copper remains the manufacturing benchmark, but nanoscale electron scattering and the growing fraction of space occupied by barriers and liners increasingly weaken its advantage. Public research through early 2024 gives ruthenium the strongest combination of small-line performance and direct-metal-etch integration evidence; cobalt offers particularly strong electromigration results and established local-interconnect use; molybdenum offers compelling linerless filling; and nickel aluminide offers promising, microstructure-dependent thin-film conductivity. Ordered compounds, graphene hybrids, and topological conductors broaden the options, but selection must compare completed interconnect structures—not bulk resistivity alone. These conclusions follow the demonstrated transport and integration results discussed below, including the 2018 elemental-metal assessment [1] and 2022 two-level Ru demonstration [2].

**The report answers three questions.** Part 1 identifies the principal material families, representative compositions, and their research status. Part 2 explains how electrical scaling, reliability, manufacturing compatibility, and sustainability determine whether a candidate is useful. Part 3 consolidates those judgments into the requested five-material comparison, with Cu as the benchmark.

## Part 1 — Overview of Candidate Materials

### Cu scaling bottlenecks and the candidate landscape

**Cu faces two distinct penalties.** Its intrinsic conductor resistivity rises as surfaces and grain boundaries increasingly interrupt electron transport, while relatively resistive barriers and liners occupy a larger fraction of the available wiring cross-section. Moon and colleagues’ 2023 *Advanced Science* review reports approximately ten times bulk Cu resistivity for a cited 10 nm-wide line and describes barrier/liner stacks several nanometers thick as a major scaling obstacle. The same review estimates that interconnect resistance affects approximately 50% of total RC delay in its 5 nm-node discussion. These are technology- and structure-specific examples, but together they explain why a metal with higher bulk resistivity can become attractive in a narrower wire. [3]

**The target is usually local wiring.** Back-end-of-line, or BEOL, interconnects comprise horizontal metal lines connected vertically by vias. The tightest local layers are closest to the transistors; upper layers generally have more relaxed dimensions and different power-delivery or long-distance signaling requirements. Middle-of-line, or MOL, structures connect devices to this wiring system. Consequently, a material can be valuable for a contact, via, or lowest metal layer without being suitable for replacing Cu throughout the chip. [4]

**Pitch and linewidth are different.** Metal pitch is the center-to-center spacing of adjacent lines, whereas linewidth is the width of the conductor or patterned feature. A technology-node name is not a literal wiring dimension. For example, imec’s 2021 roadmap described 28 nm local-interconnect pitch at the 5 nm technology node, while retaining Cu dual damascene as the workhorse process. Separately, a 2022 MOL study identified contact-trench critical dimensions below 15 nm as a regime where barrier/liner scaling strongly affects performance and yield. [5][6]

**Four families organize the field.** The requested categories describe either chemical composition or a distinctive transport mechanism. They therefore overlap: LaAlGe is chemically ternary and also a topological-semimetal candidate, while CoPt is a binary compound studied in a topologically motivated interconnect program. The useful distinction is what each approach changes: the conductor’s scattering behavior, its atomic stability, its interfaces, or the integration scheme.

| Category | Representative materials | Main attraction | Research position through early 2024 |
|---|---|---|---|
| Elemental Metals | Ru, Mo, Co, W, Ir, Rh | Favorable confined transport and established deposition knowledge | Most developed alternative-conductor class |
| Binary Intermetallic Compounds | NiAl, CuAl₂, AlCu, RuV₃ | Chemical order and strong bonding | Screening, thin films, and selected integration studies |
| Ternary Compounds | MAX phases, LaAlGe, TaIrTe₄, Ru–Mo–C | Broader combinations of transport and interface functions | Computational, concept-level, and specialized integration evidence |
| Other Emerging Materials | Graphene hybrids, NbAs, TaP, CoSi | Interface engineering or unconventional surface transport | Hybrid demonstrations and exploratory conductor concepts |

**Material replacement is not the only response.** Cu extension through thinner barriers, improved liners, selective caps, and revised integration schemes remains an active alternative to changing the entire conductor. This matters because a replacement must outperform an improved Cu stack, not an artificially frozen baseline. Imec’s compound roadmap explicitly anticipates alternative materials first in critical local layers, while expecting Cu to remain attractive in upper layers. [7]

**Takeaway: replacement is layer-specific.** The relevant question is which material–process combination improves a particular line, via, or contact while preserving reliability and manufacturability.

### Elemental Metals

**Elemental metals provide the closest comparison.** A pure metal avoids the additional stoichiometry and chemical-order requirements of an intermetallic compound. Researchers screen these materials for low confined-line resistance, a favorable resistivity–mean-free-path product, strong atomic bonding, and compatibility with deposition, patterning, and surrounding dielectrics. Gall’s 2018 study compared thickness-dependent resistivity in epitaxial Cu, W, Ta, Mo, Ru, Co, Ag, Nb, and Ni with first-principles predictions, illustrating the breadth of the elemental search. [8]

| Element | Why it is investigated | Representative evidence or role |
|---|---|---|
| Ruthenium, Ru | Favorable size scaling; barrierless potential; direct etching | Narrow lines and multilevel semi-damascene |
| Molybdenum, Mo | Barrier/liner reduction and conformal filling | Linerless atomic-layer-deposited MOL fill |
| Cobalt, Co | Short mean free path and strong reliability results | Commercial local wiring and experimental nanoscale wires |
| Tungsten, W | Refractory conductor and low-diffusivity integration options | Contact benchmark and power-rail studies |
| Iridium, Ir | Favorable calculated confined transport | Narrow-wire measurements and screening |
| Rhodium, Rh | Favorable transport and cohesive-property screening | Thin-film and elemental comparisons |
| Tantalum, Ta | Refractory-metal and barrier comparison | Thickness-dependent epitaxial transport |
| Niobium, Nb | Attractive initial electronic-structure predictions | Experimental size-effect counterexample |
| Nickel, Ni | Cohesive-property and transport interest | Epitaxial-film screening |
| Silver, Ag | Very low bulk resistivity | Bulk-conductivity and thin-film comparator |

**Ru combines several useful advantages.** Its appeal is not simply that it is conductive: it can retain useful conductivity at small dimensions, potentially eliminate a conventional diffusion barrier, and support direct reactive ion etching, or RIE. Adelmann and colleagues’ 2018 assessment identified Ru as the best combination of material properties and process maturity within its elemental screening program, using experimental Ru, Ir, and Co lines down to approximately 30 nm² cross-sectional area. Their calibrated line models emphasized barrierless integration as the principal source of Ru’s advantage. [1]

**Ru also has integrated evidence.** In Murdoch and colleagues’ 2022 two-metal-level semi-damascene study, etched Ru lines had resistivity of 13–15 μΩ·cm, compared with 14–15 μΩ·cm for the annealed physical-vapor-deposited film before etching. Ru outperformed the Cu comparison below 268 nm² conducting area, corresponding to line critical dimensions below 12 nm in that flow. The importance of this result is that favorable film properties survived patterning and multilevel integration. [2]

**Mo has a filling-led case.** A 2022 IITC study demonstrated atomic layer deposition, or ALD, of Mo without a separate liner or barrier in high-aspect-ratio trenches down to 10 nm critical dimension. It reported good adhesion to SiO₂, SiN, and SiCO, and resistance to drift into SiO₂ and SiCO under the study’s tests. This makes Mo especially relevant to MOL contacts and local structures where conformal filling and the fraction of usable conductor are decisive. [6]

**Mo’s surface quality remains consequential.** A 2023 first-principles quantum-transport comparison found Mo to have the largest surface-roughness-induced resistivity among Cu, Co, Ru, and Mo at equal modeled thickness. Thus, an attractive intrinsic material screen does not guarantee low resistance in a rough deposited film. Mo’s integration advantage is strongest when its filling and barrier-removal benefits survive the actual surface morphology and post-processing. [9]

**Co has progressed beyond screening.** The 2023 review describes Intel’s introduction of Co into the lowest two wiring layers of a 10 nm-node technology and explains the combination of electromigration resistance and contact-resistance benefits behind that transition. This is an important distinction from candidates supported primarily by calculations or blanket films: Co has demonstrated a practical role even though it does not universally minimize resistivity. [3]

**Very small Co wires are feasible.** Dutta and colleagues fabricated subtractively patterned Co wires with electrical cross-sections as small as 34 nm². Their wafer-level tests found strong resistance to thermoelectric stress and high fusing-current capability. Their modeling also separated two regimes: grain-boundary scattering dominated around 100 nm², while the surface-scattering contribution increased sharply below 50 nm². [10]

**Other elements remain useful comparators.** W offers established contact-metallization knowledge and low-diffusivity integration possibilities, while Ir and Rh help establish how favorable electronic structure can improve size scaling. However, short mean free path alone is insufficient: the calculated resistivity–mean-free-path product for W can be less favorable than Cu’s, and grain structure strongly affects its confined resistance. These alternatives must therefore be compared on the combined transport metric and actual conductor geometry. [3]

**Nb illustrates a screening reversal.** The 2023 review reports an experimentally inferred effective mean free path approximately ten times its simulated value in a cited Nb comparison. That discrepancy weakens the favorable size-effect prediction obtained from the initial intrinsic screen. The broader lesson is that an electronic-structure shortlist is a starting point; measured thickness scaling and microstructure can change the judgment substantially. [3]

**Takeaway: elemental candidates lead for different reasons.** Ru is strongest for directly etched local lines, Co for demonstrated integration and reliability, and Mo for linerless filling; their relative positions change with geometry, dielectric, and process route.

### Binary Intermetallic Compounds

**Chemical order distinguishes this category.** Ordered intermetallic compounds have a regular arrangement of different atomic species, unlike random substitutional alloys. Random compositional disorder strongly scatters carriers and can raise resistivity; long-range chemical order can reduce that penalty. Adelmann and colleagues’ 2023 review therefore emphasizes ordered binary compounds, especially aluminides, rather than treating arbitrary alloying as a route to better conductivity. [11]

**Several binaries have specific relevance.** NiAl and CuAl₂ were explicitly investigated as advanced-node alternatives in Koike and colleagues’ 2021 IITC report. Imec also reported AlNi and AlCu thin films on 300 mm substrates and identified RuV₃ within its alternative-conductor program. AlNi and NiAl denote the same equiatomic nickel–aluminum composition here, not two separate candidates. [12][7][5]

| Material | Distinctive attraction | Evidence through early 2024 |
|---|---|---|
| Nickel aluminide, NiAl | Ordered B2 structure; favorable thin-film scaling | PVD, epitaxial films, and CMP backthinning |
| Copper aluminide, CuAl₂ | Conductivity and self-limiting interface chemistry | Qualitative barrier/liner-free EM and TDDB promise |
| AlCu | Ordered aluminide transport | Thin-film studies on 300 mm substrates |
| RuV₃ | Ordered Ru-based conductor concept | Alternative-conductor screening and roadmap inclusion |
| Cu₂Mg | Low resistivity and favorable size-effect behavior | Transport studies reveal stoichiometry and oxidation trade-offs |

**NiAl is the core aluminide example.** Stoichiometric nickel aluminide forms an ordered B2 phase, with distinct Ni and Al sublattices. Its appeal combines useful conductivity at small thickness, strong chemical bonding, and the possibility of favorable interface reactions. The measured resistivity, however, depends strongly on crystallinity, oxidation, deposition conditions, and substrate—not merely on the nominal Ni:Al ratio. [13]

**NiAl results show that dependence directly.** Soulié and colleagues reported the following film measurements in 2022 and 2023. Physical vapor deposition, or PVD, deposits material from a physical source; epitaxial growth produces a film crystallographically aligned with its substrate. Chemical mechanical polishing, or CMP, combines chemical surface reactions with mechanical removal; in the epitaxial examples below it was used to thin an initially thicker film. [13][14]

| Study and film route | Thickness | Resistivity | Stated processing context |
|---|---:|---:|---|
| 2022 PVD | 7 nm | 30 μΩ·cm | 420 °C deposition; in-situ Si cap |
| 2022 PVD | 22 nm | 18 μΩ·cm | Same deposition/capping conditions |
| 2022 epitaxial NiAl | 22 nm | 14.3 μΩ·cm | Ge(100) substrate |
| 2023 PVD | 10 nm | 17 μΩ·cm | 420 °C deposition |
| 2023 epitaxial NiAl plus CMP | 7.7 nm | 11.5 μΩ·cm | Ge(100); backthinned film |
| 2023 epitaxial NiAl plus CMP | 17.2 nm | 10.6 μΩ·cm | Ge(100); backthinned film |

**Crystallinity produces a measurable improvement.** At 22 nm thickness, the reported reduction from 18 to 14.3 μΩ·cm corresponds to a calculated 20.6% improvement: `(18 − 14.3)/18 × 100`. The source attributes the lower epitaxial-film value to better crystallinity. This matched-thickness comparison is more informative about microstructure than comparing unrelated thicknesses from different deposition routes. [13]

**Backthinning preserves a useful microstructure.** The 2023 study found that thinning NiAl films initially thicker than 50 nm by CMP or ion-beam etching could retain large grains at small final thickness. Its epitaxial Ge(100)/CMP films had lower resistivity than the PVD Ru comparator used in that paper. The result is a credible materials advance, with its practical value determined by whether a suitable microstructure can be maintained on production-relevant dielectric stacks and after line patterning. [14]

**CuAl₂ offers a different balance.** Koike and colleagues identify CuAl₂ as a promising liner-free and barrier-free material combining low resistivity with good electromigration and time-dependent dielectric breakdown behavior. The 2023 review additionally describes good gap filling and a resistivity advantage over a TaN/Cu/TaN comparison below 8 nm in the cited work. Its relevance therefore extends beyond a favorable blanket-film number to the potential removal of auxiliary layers. [12][3]

**Self-forming interfaces can help.** Al-containing compounds can form a thin Al-oxide-containing interface with SiO₂, providing adhesion and diffusion control without depositing a conventional metallic barrier stack. The attractive case is a reaction that becomes self-limiting. Excessive reaction would instead consume conductor, disturb stoichiometry, and add resistance, so the useful property is controlled interface formation rather than unrestricted oxidation. [3]

**Cu₂Mg provides a counterexample.** The 2023 review lists room-temperature resistivity of 4.5–7.1 μΩ·cm for Cu₂Mg and describes favorable size-effect behavior. Yet sputtered trench filling can lose Mg stoichiometry, while annealing can produce a thick MgO layer associated with severe dielectric leakage. This example shows why a promising ordered compound can lose its advantage through deposition kinetics and interface chemistry. [3]

**Takeaway: binaries expand the design space.** NiAl is a credible electrical candidate and CuAl₂ a compelling interface-engineering candidate, but chemical order must survive deposition, thinning, oxidation, and patterning to deliver a useful interconnect.

### Ternary Compounds

**Ternary candidates include several research directions.** Three-element chemistry can combine metallic conduction with strong bonding, diffusion resistance, or topological electronic states. Representative named examples include LaAlGe, TaIrTe₄, Co₃Sn₂S₂, and Co₂MnGa as conductor concepts, together with Ru–Mo–C and Co–W–P in specialized interconnect-stack roles. These examples should be distinguished from the separate, substantial MAX-phase screening program. [15][3]

| Named ternary | Material direction | Interconnect relevance | Evidence type |
|---|---|---|---|
| LaAlGe | Type-II Weyl semimetal | Emerging conductor candidate | Crystal physics and interconnect-oriented discussion |
| TaIrTe₄ | Weyl semimetal | Proposed topological line/via conductor | Patent-listed material concept |
| Co₃Sn₂S₂ | Magnetic Weyl semimetal | Proposed surface-transport conductor | Patent-listed material concept |
| Co₂MnGa | Nodal-line semimetal | Proposed topological conductor | Patent-listed material concept |
| Ru–Mo–C, “RuMoC II” | Conductive amorphous barrier | Seedless Cu plating and diffusion blocking | Damascene barrier demonstration |
| Co–W–P, CoWP | Metallic cap | Suppression of Cu interface diffusion | Cu reliability and capping studies |

**The named roles are not interchangeable.** LaAlGe appears in the 2023 topological-interconnect discussion as a type-II Weyl example, while the 2023 IBM patent explicitly lists TaIrTe₄, Co₃Sn₂S₂, and Co₂MnGa among potential topological interconnect materials. Ru–Mo–C and CoWP have a different significance: they demonstrate how ternary chemistry can improve an interconnect stack while leaving Cu as the principal line conductor. [16][15][17]

**MAX phases are the central ceramic–metal opportunity.** Their general composition is \(M_{n+1}AX_n\), where M is an early transition metal, A is an element from periodic-table groups 13 or 14, X is carbon or nitrogen, and the commonly discussed layer sequences have \(n=1,2,\) or \(3\). These layered carbides and nitrides combine metallic electrical behavior with ceramic-like thermal and chemical stability. They are investigated because that combination could improve both resistance scaling and atomic stability. [3]

**Computational screening gives a substantial shortlist.** The 2023 review summarizes first-principles screening of approximately 170 MAX compounds. Of those examined, 69 stable cases outperformed Cu on both the resistivity–mean-free-path product and cohesive-energy proxies, and 24 outperformed Ru. These counts describe intrinsic computational screening outcomes, not fabricated wiring yields or a ranking of integrated ternary lines. [3]

**Layering introduces an orientation requirement.** MAX phases can have strongly anisotropic conductivity: transport depends on crystallographic direction. A film that performs well in the plane of its layers may behave differently through a via or across misoriented grains. The 2023 review accordingly emphasizes suitable textured growth, precursor development, and synthesis within the BEOL thermal budget. The important engineering question is whether the favorable direction can be maintained along the actual current path. [3]

**Ru–Mo–C demonstrates a concrete stack benefit.** Zou and colleagues fabricated a 4 nm RuMoC II barrier supporting seedless electroplating of a Cu plug in a damascene structure. The barrier blocked Cu and oxygen diffusion after annealing up to 500 °C, while the resulting structure showed lower leakage current and via resistance than its traditional Ta-barrier comparison. This is strong evidence for a ternary barrier function, rather than a claim that RuMoC II replaces the entire Cu wire. [18]

**Composition labels need careful interpretation.** The same study’s best-performing RuMoC II condition used a Ru:MoC sputtering-rate ratio of 100:50 and produced an amorphous film with low residual oxygen. That ratio describes deposition conditions; it is not an atomic formula establishing a 1:1:1 stoichiometric compound. For multicomponent materials, process ratios, measured composition, and crystal phase are distinct descriptors. [18]

**Takeaway: ternaries offer multifunctionality.** Their strongest early-2024 case spans intrinsic MAX-phase screening, topological conductor concepts, and demonstrated barrier or cap functions; advancement as full line conductors depends on retaining the desired phase, orientation, and interfaces in patterned structures.

### Other Emerging Materials: Graphene and hybrid conductors

**Graphene is most compelling as a hybrid.** It can act as a conductor, cap, oxidation barrier, diffusion barrier, or interface modifier. Imec reports intrinsic mobility up to 200,000 cm²·V⁻¹·s⁻¹ and current-carrying capacity up to \(10^8\) A·cm⁻², but also emphasizes insufficient intrinsic carrier concentration for an efficient local wire. High mobility alone does not ensure high conductivity because the number of available carriers matters equally. [5]

**Multilayers trade resistance against geometry.** Modeling discussed by imec indicates that several graphene layers are needed to cross over Cu in local-interconnect applications. Additional layers improve conduction but also change the total thickness and capacitive environment. Doping and metal-induced charge transfer offer other routes to increase carrier concentration, motivating hybrid metal/graphene structures rather than relying solely on intrinsic graphene. [5]

| Hybrid structure | Reported electrical result | Intended benefit | Main integration issue |
|---|---|---|---|
| Graphene-capped Cu | About 6% lower line resistance | Reduced top-interface scattering | Weak-interface electromigration |
| Graphene-capped Ru | Average 15% lower sheet resistance | Interface modification and added conduction | Transfer and mechanism control |
| Ru-capped, plasma-treated graphene | About 18% higher conductivity | Metal-induced doping and hybrid transport | Plasma defects and metal coverage |

**Cu capping reveals an interface trade-off.** Nogami’s 2023 account describes single-layer graphene growth on Cu below 400 °C, with a resistance reduction limited to approximately 6% because only the upper interface benefits. The graphene/Cu interface nevertheless exhibited poor electromigration reliability, consistent with weak van der Waals bonding. The interface that reduces electronic disturbance can therefore be insufficiently robust against atomic motion. [19]

**Ru hybrids show a different interaction.** In imec’s experiments, multilayer graphene grown by chemical vapor deposition, or CVD, was transferred onto a typically 5 nm PVD Ru film. Encapsulation lowered sheet resistance by an average of 15% and shifted graphene’s Fermi level downward by approximately 0.5 eV, corresponding to a hole concentration of \(1.9\times10^{13}\) cm⁻². Those observations support metal-induced p-doping at the interface. [5]

**Two mechanisms can explain the improvement.** Graphene might reduce scattering in Ru, or the doped graphene and Ru might conduct in parallel. The reported sheet-resistance reduction does not by itself separate those contributions. This distinction matters because a favorable parallel conducting sheet may behave differently after patterning into narrow lines, contacting through vias, or introducing transfer defects. [5]

**Deposition order also changes performance.** Depositing Ru onto graphene is not equivalent to transferring graphene onto Ru. Imec found that hydrogen-plasma cleaning followed by Ru deposition could improve hybrid-device conductivity by approximately 18%, but single-layer graphene also suffered plasma-induced defects. Grain boundaries and contamination affect metal nucleation, making uniform metal coverage another integration variable. [5]

**Growth temperature remains a major constraint.** High-quality direct graphene growth typically requires 900–1000 °C in the cited work, well above ordinary BEOL processing conditions. Lower-temperature growth trades thermal compatibility against defectivity and quality. Transfer of high-quality graphene has been demonstrated on 300 mm wafers, but introduces extra operations and sensitivity to underlying topography, contamination, and uniformity. [5]

**Other two-dimensional materials serve supporting roles.** Hexagonal boron nitride, MoS₂, and TaS₂ are investigated principally as ultrathin diffusion barriers or interface layers in this context. They should not all be described as metallic replacements for the Cu core. Their potential benefit is retaining more Cu cross-section, while their out-of-plane resistance and conformality determine whether that benefit survives in vias. [3]

**Takeaway: interfaces are graphene’s strongest opportunity.** Graphene-based approaches are best assessed as complete hybrid stacks, with resistance reduction balanced against contact resistance, adhesion, growth or transfer complexity, and electromigration.

### Other Emerging Materials: Topological Metals

**Topological conductors change the scaling mechanism.** Conventional metal surfaces usually add scattering as dimensions shrink. Topological metals and semimetals can instead support conducting surface states whose relative contribution grows with confinement. Weyl semimetals have characteristic band crossings and surface states called Fermi arcs; related multifold-fermion materials such as CoSi provide another route to unusual transport scaling. The engineering attraction is useful surface conduction, not an assumption of universally dissipation-free wiring. [16][20]

| Candidate | Representative evidence | Proposed role | Decisive integration factor |
|---|---|---|---|
| NbAs | Low-resistivity nanobelts; circuit modeling | Local or global conductor | Persistence of transport after scaling and patterning |
| TaP | Experimentally realized type-I Weyl material | Exploratory topological conductor | Thin-film synthesis and interfaces |
| CoSi | Nanowire observations and quantum-transport calculations | Surface-conduction-based scaled wiring | Defect density and thickness |
| CoPt | Measured thin-film resistivity crossover | Hybrid poly-Si local routing | Phase formation and thermal budget |

**NbAs and CoSi show unusual trends.** Lien and colleagues summarize measurements in which approximately 100 nm-thick NbAs nanobelts reached about 1 μΩ·cm—at least an order of magnitude below bulk—and CoSi nanowires reached resistivity no greater than one-fifth of the bulk value as diameter decreased. These observations motivate the category because they contrast with ordinary Cu size scaling. Their practical value depends on preserving the effect in substantially smaller, silicon-compatible interconnect structures. [20]

**Defect tolerance is conditional.** The same study’s DFT-informed CoSi calculations span approximately two to fifty unit cells and identify a critical thickness of six unit cells. Above that thickness, low defect density can favor decreasing resistivity with decreasing thickness, while high defect density can restore conventional increasing-resistivity behavior. Thus, topology changes the transport possibilities but does not eliminate the importance of defects, surfaces, and material quality. [20]

**CoPt provides a measured thin-film example.** The 2023 study *Exploring Topological Semi-Metals for Interconnects* reports CoPt resistivity of \(22.2\pm2.9\) μΩ·cm at thicknesses no greater than 10 nm, versus approximately 36 μΩ·cm for its Cu comparison. Films were sputtered onto SiO₂/Si and annealed in nitrogen at 700 °C to obtain the desired tetragonal phase. This is a film result under a particular processing route, rather than a general replacement claim. [16]

**Microstructure is a competing explanation.** In the same work, 40 nm reference films showed grain growth from approximately 10 nm before annealing to 100 nm–1 μm afterward. Improved phase and grain structure can themselves reduce resistivity. Accordingly, the observed CoPt crossover is useful evidence of conductor performance, but it does not isolate a uniquely topological contribution to that performance. [16]

**Circuit gains depend on architecture.** Using CoPt-coated poly-Si for local routing, the study projected up to a threefold delay improvement relative to pure-poly routing and a 15.6% area reduction in a D-flip-flop design. The area-saving flip-flop incurred timing penalties relative to its conventional metal-routed comparison, illustrating a genuine density–performance trade-off. Those gains arise from the hybrid routing arrangement as well as the conductor properties. [16]

**NbAs projections address a different regime.** The study used an NbAs resistivity input of 0.55 μΩ·cm in global-interconnect circuit models and obtained propagation-delay reductions up to 35.88%. Its architecture simulations projected instructions-per-cycle improvements up to 23.8% after changing cache latencies. These are modeled consequences of the selected resistivity, geometry, and latency assumptions, distinct from measured wafer-scale circuit performance. [16]

**Fabrication concepts are becoming concrete.** IBM’s patent granted in September 2023 describes blanket topological-semimetal deposition, subtractive line patterning, removal of oxidized regions, protective layers, dielectric gap filling, and planarization. This provides a recognizable integration concept for materials such as NbAs and CoSi. The patent’s role is to define possible structures and process sequences; the transport and reliability judgments still rest on the relevant experimental or modeling evidence. [15]

**Takeaway: topology is a longer-horizon option.** The conclusion would strengthen substantially when unusual transport scaling persists through low-temperature synthesis, realistic defects, contacts, vias, and multilevel integration.

**Additional documented evidence**

Copper (Cu): The page identifies void formation and inadequate fill as scaling bottlenecks for conventional Cu interconnects at the 10 nm generation and beyond: conventional Cu seed and Cu plating fill often produce line-top and sidewall voids, while void-free Cu interconnects are required. 10 nm nm (interconnect generation; Cu interconnects). [35]

Copper (Cu): Electromigration failure-time reduction during scaling depends on conductor length: long lengths are primarily affected by critical geometry and Cu microstructure, while short lengths additionally depend on interconnect mechanical properties. [36]

Copper (Cu): As Cu BEOL dimensions are aggressively scaled down, resistivity increases exponentially, producing the size effect. This raises RC delay, IR drop, and power consumption at M0 and M1, degrading BEOL performance. The increase also derives from diffusion barriers and adhesion liners, not only the metal itself. [37]

Copper (Cu): At nanoscale dimensions, resistivity rises because rough surfaces and grain boundaries increasingly scatter electrons. Grain-boundary scattering is reported as the primary cause of the scaling effect, followed by surface-roughness scattering. Plasma excimer scattering is also included among the major mechanisms, while acoustic-phonon and electron–electron scattering are treated as bulk-like and linewidth-independent. [37]

Copper (Cu): The source identifies Cu challenges at scaled dimensions: a diffusion barrier is required to prevent copper diffusion into the surrounding dielectric; the barrier has much higher resistivity than copper and can consume approximately 20% of wire width; electron scattering at conductor surfaces and grain boundaries increases resistance when cross-sectional dimensions approach the electron mean free path; local-interconnect delay increases sharply beyond the 45 nm node; and current-carrying capability is constrained by Joule heating and electromigration. ~20% (wire width consumed; copper diffusion barrier film; wire width). ~40 nm at room temperature nm (electron mean free path; electrons in copper interconnects). sub-90 nm technology nodes nm (technology-node range; copper interconnects). beyond the 45 nm node nm (technology-node threshold; local interconnect delay). [38]

Copper (Cu): Reliability screening should include electromigration lifetime, Joule heating, current density, metal temperature, dielectric integrity, and thermal-electrical coupling. The source specifically links current-carrying capacity to Joule heating and electromigration and states that electrothermal coupling affects metal temperature and therefore electromigration lifetime. [38]

Copper (Cu): Copper remains the incumbent whose resistance scaling is being managed, while smaller dimensions create a critical line-resistance roadblock and motivate replacement candidates. [40]

Copper (Cu): Thermal screening for Cu and alternatives should consider Joule heating, maximum breakdown temperature, melting point, heat transport, current density, and microstructure-dependent failure. The source contrasts WTe2's high breakdown current density with Cu's “several MA cm−2” and states that polycrystalline Cu can fail mainly through grain-boundary migration rather than self-heating despite its high melting point. ≈1001 °C °C (maximum temperature; WTe2 under vacuum; thermal extraction). ≈664 °C °C (maximum temperature; WTe2 under air; thermal extraction). [41]

Copper (Cu): The source reports a Cu resistivity of 1.6 μΩ·cm for a 10 mm-long, 0.025 μm-wide interconnect with an 8:1 aspect ratio; this is a nanoscale interconnect comparison rather than an unconstrained bulk reference value. 1.6 μΩ·cm μΩ·cm (resistivity; Cu interconnect). 10 mm mm (length; interconnect). 0.025 μm μm (width; interconnect). [43]

Copper (Cu): Copper is the incumbent conductor occupying the largest material fraction in damascene trenches, making it the benchmark against which alternative interconnect materials are evaluated. [45]

Copper (Cu): The source identifies electromigration as a material-property concern for Cu and as a reliability basis for evaluating alternative conductors; it does not report a comparative electromigration test or indicator for Cu, Ru, Mo, Co, or NiAl in this slice. [45]

Copper (Cu): The ideal replacement metal should have low electrical resistance in scaled dimensions, good thermal conductivity, oxidation resistance, and a high melting point; melting point is linked to electromigration from metal diffusion. [48]

Copper (Cu): Localized self-heating creates a temperature concentration and thermal-cycling stress that leads to BEOL interconnect failures, BEOL stress and electromigration, and bottom-layer Cu/ELK cracking; the source states that further scaling requires new materials for metal lines, barrier layers and ELK. [49]

Copper (Cu): The epitaxial Ru(0001) and Co(0001) measurements were designed to quantify electron surface scattering while minimizing roughness and grain-boundary contributions: both metals formed epitaxial single-crystal layers, and the measured layers had negligible resistance contributions from roughness and grain boundary scattering. <; 0.4 nm nm (root-mean-square roughness; Ru(0001) epitaxial layers; Sputter deposition and transport measurements). <; 0.9 nm nm (root-mean-square roughness; Co(0001) epitaxial layers; Sputter deposition and transport measurements). [50]

Copper (Cu): Using the Fuchs-Sondheimer and Mayadas-Shatzkes models, the study predicted 10 nm half-pitch line resistances of 1.0, 2.2, and 2.1 kΩ/μm for Ru, Co, and Cu, respectively. 1.0 kΩ/μm kΩ/μm (predicted line resistance; Ru interconnect line; line length in μm; Fuchs-Sondheimer and Mayadas-Shatzkes models; grain boundary reflection coefficient R = 0.4; thinner barrier/adhesion layers accounted for). 2.2 kΩ/μm kΩ/μm (predicted line resistance; Co interconnect line; line length in μm; Fuchs-Sondheimer and Mayadas-Shatzkes models; grain boundary reflection coefficient R = 0.4; thinner barrier/adhesion layers accounted for). 2.1 kΩ/μm kΩ/μm (predicted line resistance; Cu interconnect line; line length in μm; Fuchs-Sondheimer and Mayadas-Shatzkes models; grain boundary reflection coefficient R = 0.4; thinner barrier/adhesion layers accounted for). [50]

Copper (Cu): The source provides representative elemental-metal evidence relevant to the survey: Molybdenum is proposed for highly scaled BEOL interconnects and MOL vertical contacts; its size-effect behavior is studied experimentally and computationally; cohesive energy, barrierless integration, electromigration resistance, melting point, grain size, and ρoλ are discussed as evaluation dimensions. The source also identifies Rh, Ir, and Ru as elemental nanoscale conductor candidates, while noting cost, earth abundance, and process-maturity challenges. 5.99 × 10− 16 Ωm2 Ωm2 (predicted ρoλ for Mo; Mo; predicted). 2896 K K (melting point; Mo). 3695 K K (melting point; W). 1358 K K (melting point; Cu). 46% (smaller ρoλ product than Mo; Rh; Mo ρoλ product; comparison). 38% (smaller ρoλ product than Mo; Ir; Mo ρoλ product; comparison). 15% (smaller ρoλ product than Mo; Ru; Mo ρoλ product; comparison). [52]

The page states that shrinking interconnect dimensions increase resistance because of reduced cross-sectional area, causing RC delay and power dissipation; surface and grain-boundary scattering further increase resistance. It also states that the TaN/Ta barrier-liner stack needs to be at least 3–4 nm thick, that copper occupies only about 30% of a 10 nm-wide interconnect cross-section, and that Cu interconnect resistivity can account for up to 35% of total signal delays and 50% of power dissipation in computer chips. 3–4 nm nm (minimum barrier-liner thickness; TaN/Ta stack). about 30% % (copper share of total interconnect cross-sectional area; 10 nm wide interconnect; total interconnect cross-sectional area). up to 35% % (share of total signal delays; computer chips; total signal delays). 50% % (share of power dissipation; computer chips; power dissipation). [53]

Copper (Cu): For copper, the page provides reliability and sustainability evidence from semiconductor packaging and manufacturing rather than scaled local on-chip interconnects: copper wire reliability involves CuAl microcracking, CuAl corrosion, Kirkendall voiding, interdiffusion, moisture testing, solderability, and solder-joint reliability; copper-related sustainability considerations include recycling, carbon emissions, energy consumption, chemical waste, and supply-chain costs. 0.70 eV (apparent activation energy; Prime Cu ball bond; Arrhenius model). 0.75 eV (apparent activation energy; Prime Cu ball bond; Arrhenius model). 8.62×10−5 eV/Kelvin (Boltzmann constant). [55]

Copper (Cu): For copper, the source rates supply risks as Medium, long-term market balances as High, geographical concentration of mining and refining as Low, and barriers to diversification as High. around 48% share (expected top 3 share in 2030; 2030; copper mining; global mined supply; expected top 3 share). around 23% share (expected top 1 share in 2030; 2030; copper mining; global mined supply; expected top 1 share). around 60% share (expected top 3 share in 2030; 2030; copper refining; global refined supply; expected top 3 share). [56]

Copper (Cu): Cu's documented challenge is that interconnect-resistance limits become more severe with longer wires and increased circuit complexity at advanced nodes. [57]

Copper (Cu): The source treats size-effect parameters as relevant interconnect variables and cites the influence of phonon, geometry, impurity, and grain size on copper-line resistivity, but it does not report a numerical electron mean free path λ. [58]

Copper (Cu): The source defines its interconnect scope as physical electrical interconnects from die to board and from package to package, excluding optical and wireless interconnects. It identifies die-die, on-package die-die, die-to-package, within-package, off-package, package-to-board, package-on-package, and PCB interconnects as distinct categories; within-package interconnects are not covered in this chapter. [60]

Cobalt (Co): The source presents cobalt as a candidate for BEOL metal interconnects, including cobalt seed-layer, fill-layer, plug, and line structures, with publication dated 2014-07-03. 2014-07-03 (publication date; WO2014105477A1). [62]

Copper (Cu): Conventional TaN/Ta barriers and liners consume interconnect cross-sectional area and are more resistive than Cu, reducing the effective conducting volume. At 20 nm width, a 3–4 nm TaN/Ta stack can occupy at least 35% of the cross-sectional area, so further scaling motivates much thinner or atomically thin alternatives. A credible replacement must also control diffusion, provide adhesion and wettability, preserve dielectric integrity, and withstand BEOL processing. 20 nm nm (interconnect width). 3-4 nm nm (TaN/Ta stack thickness). at least 35% % (interconnect cross-sectional area occupied by a 3-nm TaN/Ta layer; entire interconnect cross-sectional area). [63]

Copper (Cu): This source reports Ru-based alloys as investigated for copper diffusion barriers, not as direct replacement metallization. It identifies RuTa, RuW, RuMo and RuZr among investigated alloys, and reports excellent barrier performance for Ru60Ta40, Ru45W55 and Mo47Ru53; however, the source was published after the requested cutoff. 2024-06-04. [64]

The reference slice identifies copper interconnect scaling challenges and literature on materials for interconnects beyond Cu, supporting Cu's role as the incumbent benchmark motivating alternatives. 30 nm nm (pitch; interconnects). [64]

Copper (Cu): NiAl is studied as a potential post-Cu interconnect and can form an aluminum-rich oxide layer that may act as a self-forming barrier at the NiAl/SiO2 interface. 400 ºC ºC (annealing temperature associated with self-forming barrier behavior; NiAl/SiO2 interconnect sample; transmission electron microscopy; secondary ion mass spectrometry; voltage ramp dielectric breakdown test). [66]

Copper (Cu): Electromigration is driven by momentum transfer from moving electrons to metal atoms. Barrier layers constrain atomic movement, producing depletion regions that can lead to void nucleation and growth. The operating current density had exceeded 1 MA/cm2 and was approaching 10 MA/cm2; EM lifetime was predicted to decrease by half for each new technology generation. 1 MA/cm2 MA/cm2 (operating current density; interconnects). 10 MA/cm2 MA/cm2 (approaching operating current density; interconnects). [67]

Copper (Cu): Cu’s documented core advantage is its established role as the incumbent benchmark; however, under continuous scaling its resistance and electromigration-related current-carrying capability become limiting. [67]

The survey boundary should cover on-chip BEOL wiring, including local (Mx), intermediate (My), and (semi-)global (Mz) interconnect wires and vertically connected metal-filled vias. Package technologies and cooling solutions should be treated as boundary conditions affecting BEOL thermal behavior rather than as conductor applications. [68]

Titanium Disilicide (TiSi2) is documented as a material for source/drain contacts, trench contacts, gate electrodes, conductive interconnect fills, and vias. The source describes direct contact with epitaxial source/drain structures, conformal and hermetic sealing of non-flat topography, and use in integrated-circuit structures. This supports TiSi2 as a validated semiconductor contact and conductor-related material, but the source does not establish its current research status specifically for advanced BEOL interconnect adoption. [46]

The source states that continued scaling of IC feature sizes creates significant challenges for existing copper barrier materials and processes and for existing barrier/liner solutions used in emerging nanoscale interconnect structures. [54]

By the 2016 publication, cobalt had been demonstrated for MOL contacts and local interconnects, with successful integration below a Cu BEOL dual-damascene V0/M1 module. The study compared metal-line resistances and highlighted challenges for each option. 2016-05-01. ≤ 10 nm nm (node dimension; MOL interconnect and contact resistances). V0/M1 (BEOL module; Cu BEOL dual-damascene integration). [70]

Tungsten was the established metallization baseline in the reported study: CVD W-based metallization had been used for all nodes since the inception of damascene, but scaling was challenged by the traditional barrier and ALD nucleation-layer limitations. 2016-05-01. ≤ 10 nm nm (node dimension; MOL interconnect and contact resistances). [70]

Elemental Metals: As Cu BEOL dimensions are aggressively scaled down, resistivity increases exponentially, producing the size effect. This raises RC delay, IR drop, and power consumption at M0 and M1, degrading BEOL performance. The increase also derives from diffusion barriers and adhesion liners, not only the metal itself. [37]

The source evaluates the elemental metals Cu, Ru, Co, and W as interconnect materials; Co, Ru, and W are described as promising alternatives to conventional Cu. [37]

Elemental Metals: As linewidth decreases, the Cu proportion in the interconnect volume falls rapidly because liner and barrier thickness become increasingly important. Cu's resistance advantage is significantly weakened below about 20 nm, and anti-electromigration properties become a major concern. 3 nm nm (liner thickness for Cu; Cu interconnects). below about 20 nm nm (linewidth; nanoscale interconnects). [37]

The source treats elemental metals as candidate conductors for advanced MEOL, BEOL, and buried-power-rail interconnect applications. Their principal advantage is that Ru, Co, and W can achieve resistance comparable to Cu at deca-nanometer dimensions when liner and barrier volume is included; their limitations include linewidth-dependent scattering, grain-size sensitivity, liner requirements, electromigration, and contamination trade-offs. below 20 nm nm (linewidth threshold; Cu versus Ru, Co, and W interconnect resistance; numerical resistance simulation including liners and barriers). [37]

The page supports elemental metals as candidate conductors for advanced on-chip interconnects: it explicitly discusses Ru, Co, and Cu metallizations and potential replacement materials for copper, with benefits including lower predicted size-effect scaling, thinner barrier/adhesion layers, and greater electromigration resistance. [51]

Elemental Metals: The source's reference list documents pre-cutoff research on narrow interconnect lines, including Daniel Gall's invited perspective, “The search for the most conductive metal for narrow interconnect lines,” and related studies published through 2019. This supports the existence of a developed property-focused literature, but the supplied slice does not establish patterning or wafer-level integration maturity. [71]

Elemental Metals: Representative elemental-metal candidates identified by the source include Rh, Pt, Ir, Ru, Nb, Ni, Ta, Os, Al, Fe, and Mo; the source states that their calculated ρo×λ products are smaller than Cu’s, indicating potential for higher conductivity than Cu in the limit of narrow wires. Rh 3.2 10 -16 Ω-m 2 (ρo×λ; Rh; calculated). Cu 6.7 10 -16 Ω-m 2 (ρo×λ; Cu; calculated). [71]

Elemental Metals: Molybdenum was investigated as a potential metal for advanced microelectronic interconnects. The source reports PVD Mo thin films from 3 to 50 nm and identifies environmental reactivity, oxidation, nitridation, contamination sensitivity, and the need for carefully controlled metallization as key challenges. It also reports that Mo can potentially replace W and Cu in future interconnect nodes because its short carrier mean free path reduces thickness-dependent resistivity, especially when barrier and liner layers are unnecessary. 3 and 50 nm nm (film thickness; PVD Mo thin films; PVD thin-film investigation). 11 nm nm (carrier mean free path; Mo). 40 nm nm (carrier mean free path; Cu). [65]

Elemental Metals: Representative elemental candidates named in the source include Ru, Mo, Co, Ni, Cr, Pd, Ti, V, Rh, Pt, Zr, Hf, Tc, Nb, Ta, Re, and Os. The source validates their inclusion by comparing cohesive energy and bulk intrinsic resistivity, with larger cohesive energy than Cu interpreted as indicating fewer intrinsic electromigration issues. 4 eV eV (cohesive energy; Cu; first-principles simulations). [72]

Binary intermetallic compounds are defined here as compounds considered in alternative metallization schemes beyond Cu, with transport behavior requiring analysis beyond the treatment used for elemental metals. Their opportunities include potential interconnect metallization and, for NiAl, relatively low bulk resistivity and high melting point; the principal limitation identified is additional transport complexity. [73]

Binary intermetallic compounds are presented as an alternative-metallization category extending beyond elemental metals. The source describes a material-selection process and notes that transport in these metals is more complex than in elemental metals. [73]

Binary Intermetallic Compounds: The source identifies AlNi, Al3Sc, AlCu, Al2Cu, and NiAl as representative binary intermetallic or binary-compound candidates investigated for alternative interconnect metallization. [73]

Binary Intermetallic Compounds: Representative binary candidates include AlNi, Al3Sc, AlCu, Al2Cu, and NiAl. Their inclusion is supported by descriptions of thin-film investigation as potential Cu alternatives for interconnect metallization; NiAl is additionally described as having relatively low bulk resistivity and high melting point. [73]

Binary Intermetallic Compounds: The page identifies cobalt-based binary compounds as candidate advanced-interconnect materials and reports that a high-throughput screening method identified several compounds with potentially superior electronic transport and reliability at reduced thickness. However, this source is dated 14 March 2026 and is outside the provisional 2024-03-31 cutoff. [75]

Binary Intermetallic Compounds: Representative binary intermetallic candidates are NiAl, Al3Sc, and CuAlx. Their inclusion is supported by ab initio screening, low-resistivity and reliability criteria, and thin-film experimental results; the source states that especially binary aluminides can show promise for alternative metallization with excellent line resistance and reliability. over 1000 (compounds assessed; binary intermetallic compounds; ab initio screening). [74]

Ternary Compounds: The ternary-compound category qualifies as part of the evolution beyond elemental alternative metals, with research targeting improved reliability and resistivity at small dimensions. The source specifically reports AlCu and Al2Cu as investigated potential alternatives for Cu interconnect metallization. [42]

Ternary Compounds: The source reports thin-film and computational evidence for Cu-Al intermetallics, but identifies unresolved challenges: stoichiometry control, phase separation, surface oxidation, interfacial reactions, and ultrathin-film resistivity increases. Because the source was published on 2024-05-03, these findings are not cutoff-eligible for a 2024-03-31 survey. [77]

Ternary Compounds: The page states that research on alternative metallization had expanded from elemental metals to binary and ternary intermetallics, but it names only Ti4SiC3 as a ternary-related material in the reference list; it does not provide several ternary candidates or candidate-specific inclusion evidence. [74]

The page supports treating ternary compounds as an emerging alternative-metallization category, but it does not define their specific chemistry, conductive mechanism, integration benefits, or unresolved risks. The paper's detailed selection discussion is for binary intermetallics, including ordered compounds with low bulk resistivity. [74]

Ternary Compounds: The references identify Ti3SiC2, Ti3AlC2, Ti3SnC2, Ti2AlC, Ti2SnC, Ti2GeC, Ti3GeC2, Ti4GeC3, Ti2InC, Ta3AlC2, Ta4AlC3, and V2AlC as specific ternary-compound examples. The cited work concerns synthesis, thin films, transport, thermopower, stability, and other material properties; it does not by itself establish direct on-chip interconnect use. [78]

Ternary Compounds: The source reports that MAX phases combine metallic properties including good electrical and thermal conductivity, machinability, low hardness, thermal shock resistance and damage tolerance with ceramic properties including high elastic moduli, high temperature strength, and oxidation and corrosion resistance. [78]

The source places ternary compounds within the broad candidate-material space evaluated for advanced interconnects using atomistic material modeling, alongside simple metals, binary compounds, nanowires, and intercalated graphene. The stated scope includes bulk, surface, grain-boundary, and contact effects and practical implementation. [79]

Ternary Compounds: The source is an institutional-repository record for a 2024 presentation, with an accepted version listed; the record states “No license” and says it was deposited on 2024-05-28. Its publication-year metadata is within 2024, but the deposit date is after the provisional 2024-03-31 cutoff. [80]

Ternary compounds contribute to the survey by providing a category for evaluating proposed interconnect materials through material properties, structural or device functionality, and fabrication-process compatibility. [81]

Ternary Compounds: The page shows that ternary-compound research includes MAX phases and metallic MAX ceramics for advanced interconnect applications, with cited work on chemical diversity, research and development, ab initio screening, and resistivity scaling of Ti4SiC3 layers. It does not establish cutoff-bounded maturity or identify a complete set of uncertain candidates. (2019) (MAX phases; review). (2011) (MAX phases; review). 5 (metallic MAX ceramics; ab initio screening). 130 (Ti4SiC3(0001) layers; resistivity-scaling study). [81]

The page identifies Ternary Compounds through the presentation title “Binary and ternary intermetallics for advanced interconnect metallization,” indicating that ternary intermetallics are treated as a material class relevant to advanced interconnect metallization. The source is a 2024 oral presentation, but its recorded conference date and availability date are after the provisional 2024-03-31 cutoff. 2024-04-22. 2024-05-28T08:19:56Z. [82]

Ternary Compounds: Specific ternary/intermetallic candidates discussed are CuAl2, Cu3Al, CuAl3, CuAl, and Cu2Al3. CuAl2, Cu3Al, and CuAl3 show lower ρ₀×λ tensor diagonal components than Cu, whereas CuAl and Cu2Al3 are less promising for some transport directions. [77]

Ternary Compounds: The source cites pre-2024 research on resistivity scaling in epitaxial MAX-phase Ti4SiC3(0001) layers, which is a named ternary MAX-phase material relevant to the candidate landscape; the supplied page does not provide the study's results or establish its integration maturity. [79]

Ternary Compounds: Binary intermetallic compounds help explain why ordered compounds such as NiAl and RuAl are considered promising: they can combine strong atomic bonding with low size-effect metrics, suppress alloy-disorder scattering, and improve electromigration resistance. [83]

Other Emerging Materials can include topological conductors and emerging compounds such as MoN, TiS, and ZrB2, which are considered for next-generation interconnects because of surface-transport, bonding, and diffusion-resistance characteristics. The source does not provide a graphene-specific account. [84]

Other Emerging Materials: The page treats Ru, Co, and W as emerging alternative interconnect materials investigated alongside Cu for scaled M0 and M1 lines. Their relevance is driven by Cu’s scaling-induced resistivity increase and by the possibility of reducing barrier and liner burdens. The study evaluates them using a Boltzmann-transport-equation-based Monte Carlo simulator and considers grain-boundary, surface-roughness, plasma-excimer, acoustic-phonon, and electron-to-electron scattering. [37]

Other Emerging Materials are represented here by graphene and carbon nanotubes (CNTs), which are investigated as futuristic interconnect candidates because of their distinctive properties and potential advantages over traditional materials. [85]

Other Emerging Materials: The source refers to “Several emerging materials in the supply chain” as an emerging-material class, but does not name specific materials. [49]

Other Emerging Materials: The source describes a staged research pathway in which shortlisted metals are tested in thin films and then fabricated as scaled interconnect wires; it reports that remaining integration challenges are still discussed after these demonstrations. [86]

Other Emerging Materials: The source identifies interconnect scalability as a near-term challenge because interconnect resistance has entered an exponential increase regime due to non-ideal scaling of the Cu barrier and increased surface and grain-boundary scattering; it calls for new barrier materials and high-aspect-ratio Cu alternatives. It further states that new interconnect materials must meet conductivity and reliability requirements, while patterning, etching, filling, planarization, metrology, and integration complexity remain key challenges. [87]

Other Emerging Materials: Carbon nanotubes (CNTs) are a representative emerging material for advanced integrated-circuit research. The source reports aligned semiconducting CNT arrays, CNT field-effect transistors, CNT integrated circuits, and monolithic three-dimensional CNT technology as research examples. 100-200 tubes/µm tubes/µm (CNT density; dense parallel CNTs required by a CNT FET). sub-100 nm nm (interlayer-via scaling target; monolithic three-dimensional CNT electronics). lower than 400℃ ℃ (process temperature; CNT FETs). [88]

For this survey, Other Emerging Materials can be framed within BEOL-compatible materials and devices for advanced on-chip interconnects. BEOL compatibility is defined by chemical compatibility and thermal compatibility with FEOL layers, including a deposition temperature below 400. < 400 (deposition temperature; BEOL compatible materials). [89]

Other Emerging Materials: Ruthenium is identified as one of the other BEOL materials under R&D, specifically for the liner. The page therefore supports listing Ruthenium as a representative alternative-interconnect material, but it does not provide Ruthenium-specific advantages, challenges, RIE/CMP maturity, or supply-risk/GWP values. [90]

Other Emerging Materials: The page identifies Topological semimetals (TSMs) and topological metals (TMs) as an emerging materials class for replacing copper, and describes Weyl, multifold, triple point, and nodal line systems as included classes. However, the source is dated September 19, 2025, so it is outside the provisional evidence cutoff of 2024-03-31 and cannot establish the requested through-2024 representative roster. [84]

Other Emerging Materials: Representative emerging materials named by the page are graphene and carbon nanotubes (CNTs). The page also points to graphene nanoribbons, dual-layered graphene heterostructure interconnects, Cu–graphene hybrid interconnects, and in-situ grown graphene-enabled copper interconnects through its cited literature. [85]

Other Emerging Materials: Copper is expected to remain the preferred interconnect metal at least until 2029, while non-Cu solutions such as Co and Ru are expected for local interconnect M0. Cobalt is also described for MOL, M1, and Mx levels, particularly vias, because of its better integration window for filling narrow trenches and its electromigration performance, despite higher bulk resistivity than Cu. at least until 2029 (projected preferred-solution period for Cu; interconnect metal). [87]

Graphene is presented as a proposed material for atomically smooth 2D-2D contacts, but its tunable work function can cause threshold roll-off and other nonideal transistor behavior. The source does not provide graphene patterning, reliability, or on-chip interconnect-integration evidence. [92]

Graphene: The source demonstrates that researchers evaluate two-dimensional contact materials using current saturation, channel length, contact resistance, and temperature dependence. It reports current saturation up to 60 μA/μm at channel lengths down to 90 nm, and states that the intrinsic van der Waals gap could be exploited to further decrease contact resistance. 90 nm nm (channel length; WSe2 FETs contacted with thin metallic WTe2). 2× higher (current saturation relative to previous work; WSe2 FETs contacted with thin metallic WTe2; previous work). [92]

By the cutoff, graphene had been experimentally investigated as an on-chip interconnect material, including stacked multilayer graphene, electrical transport, contacts, current-carrying capability, breakdown, and local doping. The source characterizes stacked multilayer graphene as a promising platform for future high-performance on-chip interconnect applications, while identifying contact resistance, scaling, graphene breakdown, and copper-contact damage as important limitations. ~ 0.5×10 -7 Ω-m Ω-m (resistivity; 5 layer s-MLG; reported study measurement). over 1.1×10 9 A/cm 2 A/cm 2 (threshold current density at hard breakdown; s-MLG wire sample, n = 5; calculated from wire width and flake thickness). [95]

By 2024-03-31, graphene had demonstrated a BEOL-relevant role as a low-temperature-grown capping material for Cu interconnects: it improved Cu resistance by 5% and increased electromigration lifetime by 78 times, while nanostructure engineering with more graphene edge contact increased lifetime by 116 times. The source describes this as a demonstrated reliability-enhancement approach rather than a standalone replacement conductor. 2023-03-14 (publication date). 400 °C °C (graphene growth temperature; graphene grown for the BEOL-compatible process). 5% % (improvement in Cu resistance; graphene-capped Cu interconnect compared to Cu-only interconnect; Cu-only interconnect). 78 times (increase in electromigration lifetime; graphene-capped Cu interconnect compared to Cu-only interconnect; Cu-only interconnect). 116 times (increase in electromigration lifetime; graphene nanostructure with more edge contact to Cu compared to Cu-only interconnect; Cu-only interconnect). [96]

The source states that a graphene edge–Cu bond inhibits migration of Cu vacancies, thereby improving electromigration lifetime. Increasing graphene edge contact with Cu further enhanced the electromigration lifetime. 78 times times (electromigration-lifetime increase; graphene-capped Cu interconnect compared to Cu-only interconnect; Cu-only interconnect; first-principles calculation and interconnect demonstration). 116 times times (electromigration-lifetime increase; graphene nanostructure with more edge contact with Cu compared to Cu-only interconnect; Cu-only interconnect; nanostructure manipulation and interconnect demonstration). [96]

The review evaluates stability, signal integrity, and power integrity for pristine and intercalation-doped multilayer graphene nanoribbon interconnects, and its cited evidence includes electro-thermal analysis, self-heating, current-carrying capacity, and thermally limited current-carrying ability. [97]

The source presents graphene as an emerging interconnect material with modeled cache-level benefits, but its effectiveness is conditional on graphene-layer availability, wire geometry, and the choice between graphene, graphene-capped Cu, and heterogeneous designs. ~25 layers of graphene layers (graphene layers; heterogeneous interconnect design scheme using thick graphene for inter-subarray interconnects; cache-level modeling). 20 graphene layers (graphene layers; graphene-capped Cu preferred below this threshold; cache-level modeling). 30 graphene layers (graphene layers; heterogeneous interconnects preferred between 20 and 30 layers; cache-level modeling). 40% EDP reduction (EDP reduction; thick graphene compared to the traditional Cu counterpart; cache-level modeling). [98]

The source supports a geometry-dependent resistance mechanism: increasing aspect ratio can reduce resistance through a larger cross-sectional area, while increasing width can eventually raise delay and energy because area overhead increases total interconnect length. It also identifies large mean free path as a factor that lowers resistance in graphene wires. [98]

Graphene: The source-stated screening dimensions include current density, current-carrying capacity, electromigration, reliability, via dimensions, processing conditions, catalyst compatibility, inter-diffusion, synthesis temperature, selectivity, scalability to very small vias, CNT density and uniformity, CNT and contact resistance, and ohmic behavior. [99]

The page identifies electron mobility and conductance modeling as relevant to graphene interconnect analysis, but it does not report a numerical electron mean free path λ, its unit, or the material and temperature conditions under which λ is reported. [61]

Graphene contributes to the survey by providing an emerging interconnect candidate whose advantages, fabrication progress, integration approaches, and manufacturing limitations illustrate how candidate materials should be evaluated. [100]

Graphene's substantive role is as an emerging conductor candidate that addresses nanoscale copper resistance and reliability problems, while also exposing manufacturing maturity as a key evaluation criterion for advanced interconnect adoption. [100]

Graphene helps explain current research status by showing a candidate with experimentally and computationally verified advantages, multiple interconnect-integration demonstrations in the cited literature, and a persistent manufacturing-readiness gap. [100]

Atomic-layer etching of two-dimensional materials requires layer-by-layer removal without damage to the underlying material; for graphene, the etch rate varies by location and increases in the order of planes, edges, and defects. [101]

Topological Metals: The source lists NbAs as a specific emerging compound, with Materials Project ID 2059. [84]

The source presents topological metals as promising interconnect candidates based on calculated surface transmission, but states that experimental validation is essential and that practical integration requires BEOL compatibility, orientation control, electromigration reliability, diffusion barriers, and related process considerations. [84]



Ruthenium (Ru) [154]

Cobalt (Co) [154]

Copper (Cu) [154]

Topological Metals (2023): emerging alternative-interconnect class; no specific material/electrical metric, integration demonstration, RIE/CMP/GWP/HHI evidence; evidence: explicitly qualified [114]; criteria: surface transmission/bulk conductance/surface-state dominance/crystallographic orientation/reliability/integration [84].

Ternary Compounds provide interconnect evaluation via material properties, structural/device function and fabrication-process compatibility. [81] Their framework uses bulk ρ×λ for size effects and cohesive energy proxies reliability; candidates with Cu-comparable/higher cohesion and lower ρ×λ proceed to experiments. [76]

Binary intermetallic compounds help explain why ordered compounds such as NiAl and RuAl are considered promising: they can combine strong atomic bonding with low size-effect metrics, suppress alloy-disorder scattering, and improve electromigration resistance. [83]

Copper (Cu) benchmarks scaled transition-metal germanides and CoAl alloys, with resistivity, electromigration and barrier-scaling limitations at aggressive dimensions. [47] Cache modeling compares Cu with graphene-capped Cu/Ru and heterogeneous options; thick graphene gives up to 41% EDP and 42.6% EDAP reductions and remains conditional, not manufacturing-ready. [98]

Copper (Cu): On 2023-10-26, the page recorded the published patent “Packaging of three-dimensional integrated circuit by encapsulation with copper posts and double sided redistribution layer,” a package-level copper example rather than direct Cu local-interconnect RIE/CMP integration evidence; no RIE or CMP result was stated. [156]

Cobalt (Co): 2021-06-03, Co3Sn2S2 thin films were a Weyl semimetal with an emergent 2D surface-conduction channel, without established on-chip interconnect use [104]; Co ALD bonding testbed preliminarily assessed ultra-dense I/O feasibility, thermal benefits vs microbumps/hybrid bonds, and SEM/XPS analysis [121].

Cobalt (Co): Cu uses electrochemical damascene deposition/CMP, filling high-aspect-ratio trenches without voids and seams; PVD is unsuitable for high-aspect-ratio vias, while CVD often needs toxic precursors/high temperatures. [109] At small dimensions, Co's shorter electron mean free path than Cu's reduces surface scattering; below <10 nm, Co line resistivity crosses over with Cu. [102]

Other Emerging Materials contribute representative materials and evaluation evidence by linking graphene, h-BN, and MoS2 to Cu diffusion, dielectric reliability, conductivity, adhesion, interface, and process-compatibility questions [91].

Molybdenum (Mo) offers 5-10 nm EMFP (Ru/Mo/intermetallics), weaker resistivity scaling, higher cohesive energy, direct-etching and barrier-free/ultrathin-liner potential; deposition, etching, stoichiometric control and co-optimization remain necessary. Nanoscale RIE/ALE evidence exists, but CMP and supply-risk/GWP data are not supplied. [83][111]

Elemental Metals: Cu, Ru, Co, and W were evaluated through bulk-to-nanoscale resistivity simulations over a fitted linewidth range of 48 nm to 10 nm, with experimental comparisons; Ru was identified as the most promising metal to replace Cu for further scaling, while Co followed Ru in scaling performance. [37]

Copper (Cu): 2018 scaled damascene test found barrierless Ru and Co had lower resistance than Cu below 250nm2 trench cross-sectional area; barrierless Ru had higher electromigration lifetimes than Cu and Co. [39] Ru(0001) and Co(0001) epitaxial single-crystal layers had negligible resistance contributions from roughness/grain-boundary scattering, allowing electron-surface-scattering measurement. [50]

Copper (Cu): Conventional Cu interconnects face increasing resistivity as dimensions shrink, limiting power efficiency and causing interconnect delay to exceed gate delay; in 10-nm-wide Cu lines, electron scattering at surfaces and grain boundaries makes resistivity approximately an order of magnitude larger than bulk Cu. [44]

Graphene is a rapid-survey emerging-conductor case exposing nanoscale transport advantages and integration limits—wafer-level synthesis, edge control, doping, and low-resistance contacts. [95] Single-crystalline WTe2 nanobelts showed ≈100 MA cm−2 breakdown current density (high-field electrical/self-heating; 12 December 2018), but direct CMOS integration was difficult. [41]

Graphene was extensively studied as a carbon-based potential solution for sustaining high current density and reducing interconnect resistance [99]; first-principles estimates involving graphene ribbons and metal–graphene interfaces were contact-physics evidence, not a complete cutoff-bounded status assessment of graphene as an on-chip interconnect conductor [135].

Nickel (Ni)'s 2018-10-16 ALD Ni3Sn2 showed intermetallic XRD reflections and high purity; interconnect integration/readiness unestablished. [110] It was an evaluated interconnect metal with 2021 HHI 2,110 [0-10000] and relative embedded GWP 2.31 versus Cu. [123] By 2024, it had Low supply risk, High geopolitical risk, and high mining/refining concentration—not on-chip evidence. [56]

Molybdenum (2015-09-01): mining→production material/energy flows; no comparable interconnect GWP. [155] MoP (molybdenum phosphide) is a topological semimetal with high carrier density and low resistivity; its nanowires showed better dimensional scaling of resistivity than Cu with a TaN liner and Ru; MoTe2 is another topological semimetal candidate (2024 Nov 23; post-cutoff). 

Ruthenium (Ru) showed 10-9Ωcm-2 contact resistivity on p-SiGe and n-Si source/drain contacts on 9 October 2020, for MOL plugs; in 2018, barrierless Ru had lower resistance than Cu below 250nm2 in damascene trenches and higher EM lifetimes than Cu/Co, a credible alternative through early 2024. [118] [39]

By 2018, Nickel Aluminide (NiAl) was experimentally investigated as a potential liner-/barrier-free Cu replacement: strong adhesion, no SiO2 interdiffusion, favorable resistivity size effect below 7 nm linewidths [127]. RIE/CMP, supply risk/GWP: not reported; post-cutoff 2024 first-principles work indicated short electron mean free path and small ρ₀×λ, not cutoff-eligible [145].

Ruthenium (Ru): Ru electrodeposition has insufficient development because slow ED kinetics and competitive hydrogen evolution complicate morphology control [108]. By the pre-2024 cutoff, Ru had published evidence as a platform for direct Cu electroplating and BEOL integration beyond 32-nm technology nodes [157].

Carbon Nanotubes contribute as an emerging conductor candidate, but their contribution remains qualified: metallic enrichment, contact resistance, and manufacturing compatibility are unresolved or immature areas requiring further research. [120]

Cobalt: Existing Co-liner CMP formulations had no Cu-to-Co selectivity, a material-specific compatibility/selectivity issue in Co integration. [153] In 2018, Co(0001) films 5 to 300 nm gave λ = 19.5 ± 1.0 nm; a 10 nm half-pitch polycrystalline Co line was predicted at 2.2 kΩ/μm, showing nanoscale transport/scaling, not wafer-level integration/production readiness. [50]

Nickel Aluminide: RuAl is a heat-resistant-alloy research candidate, not a direct alternative on-chip interconnect candidate; it is a demonstration alloy for first-principles heat-resistant-alloy methods and high-temperature physical properties. [144] A 2021 IEEE IITC publication identified stoichiometric NiAl thin films as a potential alternative to Cu in interconnect metallization schemes. [42]

**Scope, cutoff, and category rules**


**At-a-glance category map**

**Copper benchmark and the scaling problem**

**Elemental Metals**

**Ruthenium and cobalt status**

rejected; reason=number_unsupported; allowed numbers: <1 pA | 2023 | 2016 | "" | 5 A/mm; 70% | 5 A/mm | 30%–50% | 03 October 2023 | 40-layer | 2059; allowed citations: [36][40][45][49][50][51][53][54][57][58][60][61][67][68][73][74][78][79][81][83][84][85][86][93][94][96][97][99][100][101][103][136][137][138][139][140][141][142][143]; allowed entities: Cadmium Arsenide (Cd3As2), Copper (Cu), Elemental Metals, Ternary Compounds, Other Emerging Materials, Binary Intermetallic Compounds, Graphene, Topological Metals, Copper, Molybdenum (Mo), Cobalt (Co), Molybdenum. Within Other Emerging Materials/Topological Metals, Cadmium Arsenide (Cd3As2) is an uncertain Dirac-semimetal case: epitaxial Cd3As2 has been integrated with a buffer into semiconductor structures, and thin-film/nanowire transport retains high mobility; suppressed backscattering is attributed to anti-aligned spins for nonmagnetic scattering [139][141]. This makes it useful for transport and heterostructure screening, but the evidence concerns semiconductor heterostructures and device physics rather than a demonstrated BEOL interconnect, so process compatibility and reliability remain unresolved [139][143].

Use the mandated headings Elemental Metals, Binary Intermetallic Compounds, Ternary Compounds, and Other Emerging Materials: elemental conductors remain in the first class, ordered two-element conductors such as aluminides in the second, MAX phases in the third, and graphene/2D and topological-semimetal concepts in the last [51][74][78]. Label candidates as demonstrated, discovered or research-stage, uncertain, or unsupported rather than implying equal maturity; new conductor and joining processes were known but not integrated into HVM, and topological-semimetal evidence after the cutoff should remain provisional [49].

Within the Elemental Metals classification, Cu, Ru, and Co are direct candidate conductors, and pre-cutoff work combines calculated size-effect rankings, epitaxial-film resistivity measurements, and modeled narrow-wire comparisons reaching < 10 nm [51][71]. The evaluation uses ρ₀×λ as a size-effect figure of merit—Rh is a representative predicted case at ρoλ = 3.23 × 10-16 Ωm2 with λ = 6.88 nm—but measured/model differences mean the category supports candidate prioritization rather than a blanket readiness claim [146][71].

Within Binary Intermetallic Compounds, ordered compounds extend alternative metallization beyond Cu; representative AlNi, Al3Sc, AlCu, Al2Cu, and NiAl are studied for scaled and semi-damascene conductors, with thin-film transport used to test the category [73][107][74]. Screening links low bulk resistivity and low ρ₀×λ to small-dimensional line resistance and high cohesive energy to reliability, while ordering, phase stability, composition fluctuations, and thin-film defects remain limitations [74][106].

Within Ternary Compounds, research extends alternative metallization beyond elemental and binary materials; metallic MAX phases and Ti4SiC3(0001) are representative, and the category is evaluated through material properties, structural or device function, and fabrication compatibility [78][79][81]. It remains exploratory: resistivity can include phonon, surface, and grain-boundary scattering plus atomic disorder, point defects, and local composition fluctuations, while the available evidence does not define a complete chemistry or roster [112][74].

Under Other Emerging Materials, graphene and CNTs represent futuristic conductor concepts, while h-BN and MoS2 represent 2D diffusion-barrier and dielectric-reliability concepts [85][91]. Status spans computational screening, thin-film testing, and scaled-wire fabrication, but new conductor and joining processes were not integrated into HVM; the category therefore supports comparison of current density, electromigration and reliability, via dimensions, process compatibility, and diffusion or dielectric functions without implying production maturity [86][49][99][91].

Under Other Emerging Materials, Graphene is a research-stage conductor with modeled and fabricated multilayer or nanoribbon structures and CMOS-oriented patterning; reported current-carrying capacity is over 1.1×10^9 A/cm^2 and mobility reaches 20,000 cm^2 V^-1 s^-1 [95][97][100]. Evaluation spans current density, contact resistance, electromigration, thermal/signal/power integrity, and damage-aware RIE; Graphene’s tunable work function can cause threshold roll-off, while breakdown, contact damage, and current-induced heating remain risks, so it is not yet practically deployed [99][92][95][101].

Under the Other Emerging Materials/topological-semimetal classification, Topological Metals are screened through surface transmission or conduction, bulk conductance, crystallographic orientation, surface energy, and disorder; CoSi and MoP are representative named candidates [84]. Their status is provisional rather than manufacturing-demonstrated: calculations are promising but direct advanced-interconnect demonstration and scalable experimental validation are not established, and some TSM evidence is dated after the early-2024 cutoff [84][105][53].

Copper (Cu) is the incumbent benchmark for candidate trade-offs: it has lower resistance than aluminum, lower susceptibility to electromigration failure, and established use, although continued scaling creates resistance and reliability bottlenecks [147][67][54]. The benchmark therefore tests whether an alternative can improve scaled line resistance, barrier or liner burden, or reliability without losing manufacturability; Cu’s required diffusion-barrier burden is itself part of the comparison [45][54].

Within the Elemental Metals classification, Ruthenium (Ru) contributes a leading scaled-interconnect and process case: reported advantages include higher line aspect ratios with capacitance control, no metal-CMP step, and use of the conductive footprint without a metal liner [117]. The process evidence addresses semi-damascene requirements on 300mm wafers and a 10 nm context, while line or contact resistance, adhesion, and reliability remain the relevant integration checks [118][35][115].

Within Elemental Metals, Molybdenum (Mo) contributes a scaled-interconnect candidate whose screening links conductivity and electromigration to barrierless integration; published work includes barrierless PVD Mo and process studies [113][116]. Its etch evidence is mechanistic: metallic Mo is oxidized to Mo6+ and amorphous MoO3 while Ce4+ from CAN is reduced to Ce3+, so wet-etch control is part of the material assessment at sub-10 nm and ≈10 nm scales [119].

Within Elemental Metals, Cobalt (Co) is included as an alternative conductor alongside Cu and Ru; the selection rationale is tied to lower size-effect scaling, thinner barrier or adhesion layers, and electromigration resistance [51]. The available Co-specific evidence supports transport and reliability screening through conductivity and electromigration, but does not establish a complete quantitative or process-maturity profile, so Co should be reported as a qualified candidate rather than universally mature [116].

Within Binary Intermetallic Compounds, Nickel Aluminide (NiAl) is a representative low-resistivity aluminide candidate investigated for advanced interconnects, with pre-cutoff studies addressing resistivity scaling and interdiffusion reliability [125][59]. It is therefore useful as a compound-specific transport and reliability screen, but the available evidence supports candidate status rather than full process maturity or a production-ready claim [125].

Within Elemental Metals, Tungsten (W) is an established MOL/contact comparator: it has long use in NAND, DRAM, and logic/foundry MOL and is associated with strong planarization and filling, making its process evidence useful for comparison [122][149]. It is not an unqualified solution: enhanced-PVD barrierless W has limited gap-fill performance, conventional W/Mo comparison uses a TiN liner, and W is a designated conflict mineral requiring supply-chain scrutiny [150][124][148].

Within Elemental Metals, Nickel (Ni) contributes mainly as a broad screening candidate: it is one of five metals reported favorable on at least six of nine indicators [123]. The available thermodynamic reference concerns Fe–Co–Ni CALPHAD properties rather than direct interconnect performance, so Ni remains a qualified roster candidate pending nanoscale transport, reliability, and process evidence [151].

Within Binary Intermetallic Compounds, Cobalt Aluminide (CoAl) contributes only an evidence-qualified electrical-screening example: it appears in a resistivity study with NiAl, NiGa, and CoGa, but direct CoAl interconnect performance is not established [126]. Its strategic-material context makes supply security relevant, yet no CoAl-specific process maturity, reliability, GWP, or quantified supply-risk result is established in the available evidence [152].

Within Binary Intermetallic Compounds, Iron Aluminide (FeAl) contributes as a background materials case rather than a demonstrated interconnect: the evidence concerns Fe3Al/FeAl high-temperature structural intermetallics, with processing, oxidation/corrosion, and mechanical-property issues [69][128][129]. It can inform stability and manufacturability screening, but its on-chip roster status remains unsupported or uncertain because direct interconnect use is not provided [69].

Within Ternary Compounds/MAX phases, Titanium Silicon Carbide (Ti3SiC2) supplies a conductive-material and contact case: formation in Ti/Al contacts at 950°C lowered Schottky-barrier height and specific contact resistance, while the literature covers thin-film deposition, electrical properties, and thermal stability [130][78]. Its relevance to advanced interconnects remains indirect rather than demonstrated in patterned BEOL wiring, and the 950°C formation condition is a major thermal-budget concern [130].

Within Ternary Compounds, Strontium Molybdate (SrMoO3) is an uncertain conductive-oxide candidate: reported films show room-temperature resistivity of ≈5.1 μÄ cm, but high-quality growth is difficult and one deposition study found both elements oxidized with no metallic peaks [131][132]. The limiting mechanism is the need for a highly reductive atmosphere because unstable Mo4+ tends to oxidize to a thermodynamically stable higher oxide; its demonstrated roles are electrodes and related devices rather than direct interconnects, so it mainly informs film-quality, resistivity, and process screening [133][134].

## Part 2 — Key Evaluation Criteria

### Electrical Performance and Size Effects

**Scaled line resistance is the primary metric.** A useful conductor must reduce resistance in the available footprint, not merely possess an attractive bulk resistivity. Nogami and colleagues identify lowest scaled line resistance as the principal selection criterion, accompanied by via resistance, reliability, production yield, and cost. Capacitance and operating temperature complete the electrical comparison because an apparently better wire can create a worse overall RC or thermal result. [21]

**Geometry converts resistivity into resistance.** For a uniform line, the engineering relation is:

\[
R_{\mathrm{line}}=\rho_{\mathrm{eff}}\frac{L}{A_{\mathrm{conducting}}}.
\]

**The two terms must stay separate.** Here, \(\rho_{\mathrm{eff}}\) is the conductor’s resistivity under its actual size, microstructure, and interface conditions; \(A_{\mathrm{conducting}}\) is its usable cross-section. A barrier can reduce area even if it does not change the intrinsic resistivity of the remaining Cu, while its interface can independently increase electron scattering. Confusing these contributions obscures why alternative metals sometimes win. [3]

**Nanoscale surfaces interrupt electron motion.** In a sufficiently large, clean metal near room temperature, phonon scattering largely sets the bulk mean free path. As line width or thickness approaches that distance, electrons encounter external surfaces and material interfaces more frequently. Roughness, surface chemistry, and coupling to adjacent materials can randomize the momentum component carrying current, increasing resistivity. Josell, Brongersma, and Tőkei describe this mechanism in their foundational 2009 review. [22]

**Grain boundaries add internal scattering.** A polycrystalline conductor comprises grains with different orientations separated by boundaries that disturb atomic periodicity. Smaller grains usually mean more boundary encounters along the transport path. Consequently, a film with low surface roughness can still have high resistivity if its grain boundaries strongly reflect carriers, while a large-grain film can perform substantially better at the same thickness. [3]

**Two models organize these effects.** The Fuchs–Sondheimer model describes surface scattering using a specularity parameter \(p\): fully specular reflection preserves current-carrying momentum, whereas diffuse scattering contributes to resistance. The Mayadas–Shatzkes model describes grain-boundary scattering using grain size and a boundary-reflection parameter. These models explain why identical chemical compositions can exhibit different thickness-dependent resistivities after different deposition or annealing processes. [3]

**The key product is \(ρ₀λ\).** In this report, \(\rho_0\) denotes bulk resistivity at the temperature of interest, and \(\lambda\) denotes the corresponding bulk electron mean free path. The screening quantity is:

\[
F_{\mathrm{size}}=\rho_0\lambda.
\]

**The product measures absolute size sensitivity.** For comparable geometry and boundary-scattering parameters, first-order surface and grain-boundary corrections scale with this product divided by the relevant thickness or grain dimension. Its units are Ω·m²; dividing by a length gives resistivity units, Ω·m. A lower product therefore indicates a smaller absolute resistivity penalty from confinement, although the bulk-resistivity starting point still matters. [7]

**Cu supplies a practical numerical benchmark.** Using imec’s room-temperature anchors, \(1.7\) μΩ·cm and \(39\) nm, gives the following calculated product:

\[
\rho_0\lambda\approx(1.7\times10^{-8}\ \Omega\!\cdot\mathrm{m})(39\times10^{-9}\ \mathrm{m})=6.63\times10^{-16}\ \Omega\!\cdot\mathrm{m}^2.
\]

**Equivalent units aid cross-paper comparison.** Rounded, this is approximately \(6.6\times10^{-16}\) Ω·m², or \(6.6\times10^{-12}\) Ω·cm². The 2009 review gives the same approximate Cu benchmark using \(1.67\) μΩ·cm and an approximately 39 nm mean free path. Unit conversion is essential because a product reported in Ω·cm² differs numerically by a factor of \(10^4\) from one in Ω·m². [22]

**The alternatives illustrate the screening logic.** The following table separates calculated transport products reproduced in the 2023 review from mean-free-path inputs used in a 2022 Monte Carlo study. The hcp-metal products are direction-dependent, while the mean-free-path column identifies that second study’s model inputs. [3][23]

| Metal | Calculated \(ρ₀λ\), \(10^{-16}\) Ω·m² | Mean-free-path input, nm | Screening implication |
|---|---:|---:|---|
| Ru | 3.81 | 6.59 | Favorable intrinsic size sensitivity |
| Co | 4.82 | 7.77 | Lower product than Cu |
| Cu | 6.70 | 39.9 | Low bulk resistivity; stronger size sensitivity |
| W | 8.20 | 11.2 | Shorter path alone does not ensure advantage |

**Short mean free path is insufficient.** W’s shorter mean free path does not make its product automatically better than Cu’s. Conversely, Ru can tolerate a higher bulk resistivity because its size-dependent increase is smaller and its conductor can occupy more of the footprint. The comparison must therefore retain both the resistivity intercept and the confinement penalty, rather than optimizing either in isolation.

**Microstructure can override the intrinsic ranking.** The 2022 Boltzmann-transport Monte Carlo study found grain-boundary scattering to be the dominant nanoscale contribution within its calibrated structures, followed by surface roughness. Its predicted resistance also depended strongly on the assumed barrier/liner thickness. Meanwhile, the 2023 quantum-transport study found particularly strong roughness sensitivity in Mo, showing that the dominant practical penalty depends on the material state being modeled. [23][9]

**Barrier area creates a separate crossover.** Consider the sourced example of a 20 nm-wide trench with aspect ratio two and a 3 nm barrier/liner stack. In a rectangular geometric estimate with coverage on both sidewalls and the bottom, the trench height is \(2\times20=40\) nm and the remaining Cu area is:

\[
A_{\mathrm{Cu}}=(20-2\times3)(40-3)=518\ \mathrm{nm}^2.
\]

**The area-only penalty is substantial.** The original area is \(20\times40=800\) nm², so the estimated area loss is `(800 − 518)/800 = 35.3%`. Treating the auxiliary stack as negligibly conducting, the resistance multiplier from area loss alone is `800/518 = 1.54`. This calculation explains the review’s “more than 30%” area statement; it should not be equated with the separate, more-than-threefold total line-resistance example reported in the review. [3]

**Area recovery permits higher conductor resistivity.** For identical outer dimensions and length, an ideal full-area alternative would beat this Cu core whenever its effective resistivity were less than approximately 1.54 times the Cu core’s effective resistivity. That is a conditional estimate from the calculated area ratio, holding other effects fixed. It demonstrates why barrierless integration can matter as much as the intrinsic transport product.

**Ru provides a measured crossover example.** In the two-level semi-damascene study, Ru’s advantage below 268 nm² conducting area and 12 nm line critical dimension reflects the realized metal and integration flow. It is not a universal transition width applicable to every Cu barrier stack or Ru deposition process. The engineering conclusion is that the replacement threshold must be expressed in conducting area, geometry, and process conditions. [2]

**Resistance-per-length estimates connect to design.** Combining the study’s post-etch Ru resistivity range of 13–15 μΩ·cm with its representative 250 nm² electrical area gives an estimated 520–600 Ω/μm: `10⁴ × (13–15)/250`. The factor \(10^4\) converts μΩ·cm and nm² into Ω/μm. This is a calculation using reported anchors, not an additional measured line-resistance distribution. [2]

**Vias and capacitance complete the comparison.** A material that lowers line resistance may still add resistance at the via bottom, a metal–metal junction, or an oxide-contaminated contact. Increasing line height improves conducting area but can increase coupling capacitance and complicate gap filling. These interactions explain why lowest line resistivity does not necessarily produce the lowest circuit delay. [21]

**Takeaway: use \(ρ₀λ\) to shortlist.** Final electrical judgment belongs to measured line and via resistance at matched footprint, microstructure, interfaces, and operating temperature; below approximately 10 nm, classical-model trends require especially careful comparison with experiments. [3]

### Reliability

**Barrierless integration preserves useful conductor volume.** A diffusion barrier suppresses metal migration into adjacent materials, while a liner commonly promotes adhesion, wetting, or nucleation. A cap protects the top interface and can also limit diffusion. Removing a separately deposited layer recovers conducting space and can simplify interfaces, but the remaining conductor–dielectric system must assume that layer’s protective function. [7]

**Barrierless and linerless are different claims.** A material may not need a conventional diffusion barrier yet still require an adhesion-promoting layer. For example, the 2022 Ru semi-damascene demonstration deposited its first PVD Ru layer on TiN described as an adhesion layer. That structure supports the value of removing a conventional Cu-style barrier stack, while also showing why “barrierless” should not automatically be read as “no auxiliary interface material anywhere.” [2]

**Reliability has several distinct mechanisms.** Electromigration and stress-induced voiding primarily threaten metal continuity; time-dependent dielectric breakdown threatens insulation. Adhesion, phase stability, and intermixing can influence both. A candidate that excels in one test can therefore fail through another mechanism under a different stress condition. [17]

| Reliability dimension | Failure mechanism | Meaningful assessment | Useful intrinsic clue |
|---|---|---|---|
| Electromigration, EM | Current-driven atomic redistribution | Resistance evolution and failure-time distributions | Cohesive strength and diffusion barriers |
| Stress-induced voiding, SIV | Stress-gradient-driven mass transport | Thermal storage and via-chain resistance | Mechanical and diffusion properties |
| Time-dependent dielectric breakdown, TDDB | Progressive conductive-path formation | Leakage and breakdown-time distributions | Metal–dielectric chemical stability |
| Interface and phase integrity | Delamination, reaction, or intermixing | Thermal, structural, and adhesion testing | Phase stability and interface bonding |

**Electromigration depends on flux imbalance.** Momentum transfer from current-carrying electrons can drive atomic movement. Damage develops where the entering and leaving atomic fluxes differ, creating depletion and voids in one region and accumulation or extrusion elsewhere. A small void can be electrically fatal in a narrow line or via, so scaling increases sensitivity even before considering changes in diffusion kinetics. [3]

**Current density links geometry to lifetime.** At a fixed delivered current, reducing conductor area increases current density, while higher resistance increases Joule heating. The relevant temperature is the local wire temperature, including self-heating, rather than simply the chamber or package temperature. Comparisons at equal current density and comparisons at equal delivered current answer different design questions, particularly when barrier removal changes the available cross-section. [4]

**Co has particularly strong comparative evidence.** Griggio and colleagues’ 2018 study of a 10 nm-node Co BEOL scheme reported electromigration time to failure at least four orders of magnitude above its Cu-alloy comparison. Intrinsic Co/low-k TDDB also met expectations and surpassed the tested Cu/low-k system, while stress-induced-voiding tests supported favorable intrinsic Co behavior. These findings support Co’s reliability-led case within that metallization scheme. [24]

**Barrierless Co also exposes interface weaknesses.** A separate 2018 study observed EM voids in some Cu-filled reference vias with a TaNCo barrier/liner, but not in the tested Co vias. Long thermal storage produced more failures in the barrierless Co structures, associated with weak Co/dielectric interfaces and Co/Cu intermixing. The two observations are compatible: improved current-stress behavior does not guarantee thermal-storage stability. [25]

**The dielectric changes the barrier requirement.** The same work describes barrierless Co deposition on dense low-k, while identifying a barrier requirement against diffusion into SiO₂ and porous low-k. Thus, “Co is barrierless” is not a dielectric-independent material property. Removing the barrier is beneficial only when the intended interface suppresses diffusion and preserves adhesion over the relevant temperature and electric-field conditions. [25]

**Ru has combined electrical and reliability results.** In the 2022 two-level semi-damascene study, structures with a 10 nm injector and 180 nm² via contact area endured 300 hours at 10 MA/cm² without resistance change. Separate storage at 200 °C for 120 hours produced no resistance change or yield drop, and via-to-line breakdown at 100 °C exceeded 9 MV/cm. These tests jointly address current stress, thermal diffusion, and electrical isolation in the demonstrated structure. [2]

**Dielectric breakdown is not simply metal failure.** Metal atoms or ions entering a dielectric can create traps, increase leakage, and help form conductive paths between neighboring lines. Porous low-k materials also have their own vulnerability to defects, weak interfaces, moisture, and plasma damage. A stable alternative metal can remove one breakdown driver, but it cannot compensate automatically for an already damaged dielectric. [4]

**Instantaneous strength and lifetime differ.** A high breakdown field demonstrates electrical robustness under that test, whereas TDDB measures the evolution of damage over time under sustained stress. Lifetime extrapolation requires a field-acceleration model and an appropriate failure distribution. The Ru breakdown result is therefore valuable evidence alongside, rather than a substitute for, time-dependent reliability characterization. [4]

**Cohesive energy supplies an intrinsic screen.** Cohesive energy measures how strongly atoms are bound in the solid relative to isolated atoms. Imec uses approximately 4 eV per atom for Cu in its screening discussion and favors alternatives with comparable or higher cohesive energy together with lower \(\rho_0\lambda\). Stronger bonding can make atom detachment, void formation, and self-diffusion less favorable. [7]

**Melting point provides a related clue.** Co’s melting point of approximately 1495 °C, compared with about 1085 °C for Cu, has been used as a heuristic indication of potentially stronger electromigration resistance. However, melting point and cohesive energy are screening proxies, not measured lifetime parameters. They are most useful for identifying candidates likely to have robust atomic bonding before testing their actual interfaces and diffusion paths. [25]

**Interfaces can bypass strong bulk bonding.** Atoms at surfaces, grain boundaries, and poorly bonded interfaces are not in the same environment as atoms inside an ideal crystal. A high-cohesive-energy conductor can therefore fail through a relatively easy interface-diffusion path. This is why adhesion, grain structure, cap chemistry, and metal–metal junctions remain decisive after a candidate passes intrinsic screening. [3]

**Activation energy is a different quantity.** In a 2019 study, low-frequency-noise measurements gave approximately 1 eV EM activation energies for Ru- and Co-based interconnects, interpreted as likely interface-related diffusion. For Ru accelerated tests, assigning different local temperatures because of Joule heating could shift the inferred activation energy toward approximately 2 eV. These values describe an active transport mechanism under a model, not the conductor’s cohesive energy. [26]

**Longer testing strengthens mechanism identification.** A 2022 package-level Co study ran EM measurements for more than eleven months and estimated an activation energy near 1.4 eV. Failure analysis associated void growth with grain boundaries and barrier/metal interfaces. This reinforces the practical importance of identifying the weakest diffusion path rather than assigning reliability from elemental bonding strength alone. [27]

**Stress migration requires independent attention.** Thermal-expansion mismatch, deposition stress, and constrained grain growth can create stress gradients that drive atomic redistribution without current. A material can consequently survive an EM test yet fail during storage or thermal processing. The barrierless Co example makes this distinction concrete and explains why thermal storage and adhesion belong beside current-stress testing. [17]

**Takeaway: barrier removal is conditional.** Prefer barrierless or linerless integration when the complete interface system supports it; cohesive energy narrows the candidate set, while EM, storage, adhesion, and TDDB establish whether the recovered conductor volume is dependable.

### Process Maturity

**Maturity belongs to an integration route.** A blanket film, a filled contact, a polished film, and a multilevel interconnect demonstrate different capabilities. The relevant question is whether a candidate can complete the selected manufacturing sequence while retaining conductivity, interfaces, dimensional control, and acceptable defectivity. A material’s favorable RIE behavior cannot substitute for void-free filling if the chosen scheme still requires filled vias. [21]

**Damascene and semi-damascene redistribute difficulty.** Damascene patterns the dielectric and fills the resulting cavities; semi-damascene combines filled vias with subtractively patterned metal lines. Single damascene separates via and line metallization, whereas dual damascene fills them together. The following comparison summarizes their distinct requirements. [4][2]

| Scheme | Principal pattern transfer | Metal filling | Planarization | Main integration pressure |
|---|---|---|---|---|
| Single damascene | Dielectric via and trench separately | Separate metal-fill operations | CMP after relevant fills | More operations and interfaces |
| Dual damascene | Dielectric via and trench | Combined via/trench fill | Metal and barrier CMP | Narrow-feature fill and auxiliary-layer continuity |
| Semi-damascene | Direct metal-line etch; patterned vias | Via filling remains | Metal CMP avoidable; dielectric CMP may remain | Etch profiles, gap fill, and via alignment |

**Cu demonstrates a complete established flow.** After dielectric patterning, Cu integration deposits a barrier/liner and a seed layer, fills the feature by electrochemical plating, anneals as required, and removes field overburden by CMP. The process is repeated to build successive wiring levels. Its maturity encompasses deposition, additive chemistry, planarization, cleaning, and reliability control—not simply the availability of Cu deposition. [17]

**Filling must avoid seams and voids.** Physical deposition can preferentially coat the feature entrance and suffer shadowing in high-aspect-ratio structures. Conformal deposition improves coverage, but opposing sidewall films can meet and leave a seam. Bottom-up or superconformal growth avoids premature closure by increasing deposition at the feature bottom relative to the top. These distinctions directly affect resistance, reliability, and yield. [3]

**Cu super-filling uses controlled chemistry.** Electrochemical Cu deposition employs suppressors, accelerators, and levelers to manage local growth rates. A continuous seed layer is essential to distribute plating current and initiate deposition throughout the feature. As dimensions shrink, seed continuity and barrier coverage become increasingly difficult, even though the overall process is industrially mature. [17]

**Alternative deposition must preserve material quality.** ALD and CVD can provide access to narrow structures, but their useful output depends on nucleation, film continuity, impurity incorporation, growth rate, and thermal conditions. In compounds, the process must also retain the desired composition and phase. A conformal film is valuable only if the resulting conductor remains electrically and chemically suitable after the complete sequence. [3][7]

**Mo provides a specific filling milestone.** The 2022 ALD Mo work demonstrated liner/barrier-free high-aspect-ratio trench filling to 10 nm critical dimension. Its adhesion and drift results address important integration functions that would otherwise require separate layers. That evidence supports a strong filling-unit-process judgment, while line patterning and planarization are evaluated as separate operations. [6]

**CMP must remove material selectively.** Chemical mechanical polishing must clear overburden across the wafer while controlling line recess, dielectric loss, scratches, particles, and residual contamination. In Cu damascene, the usual stages are bulk Cu removal, barrier clearing, and final overpolishing to clear field regions. Selectivity becomes especially important when metal, barrier, and dielectric are exposed simultaneously. [17]

**Topography becomes electrical variability.** Dishing lowers the metal surface within a feature; erosion removes material across a patterned region. Both alter the final conductor dimensions, and therefore resistance. Porous low-k dielectrics also limit the acceptable mechanical loading and can suffer cracking or delamination, making slurry chemistry, polishing pressure, and interface strength interdependent. [17]

**Ru and Co present different CMP challenges.** Ru’s hardness and low chemical reactivity complicate conventional polishing, while aggressive oxidation conditions can generate hazardous Ru oxide species. In Co/Cu structures, galvanic coupling can dissolve Co during CMP and post-CMP cleaning. Consequently, successful polishing requires control of electrochemistry as well as removal rate and mechanical action. [3][19]

**NiAl backthinning is a meaningful unit process.** The 2023 NiAl work demonstrates that CMP can reduce film thickness while retaining a favorable grain structure. This establishes compatibility with a useful material-removal operation. Its transfer to patterned interconnects is judged by additional requirements such as field clearing, pattern-density response, surface composition, dielectric selectivity, and post-CMP contact quality. [14]

**RIE requires a controlled removal pathway.** Reactive ion etching combines plasma chemistry with directional ion bombardment. For a line-patterning process, the desired outcome is an anisotropic profile with controlled critical dimension, sufficient hard-mask selectivity, low residue, and limited damage to neighboring materials. Etch rate alone is therefore an incomplete measure of suitability. [19]

**Cu’s etch chemistry explains damascene.** Cu chlorides and fluorides such as CuCl₂ and CuF have insufficient volatility for straightforward low-temperature RIE. This makes conventional subtractive Cu patterning difficult and motivates patterning the dielectric instead. An alternative material that supports controllable direct etching can therefore enable a different architecture, even if its blanket-film resistivity is higher. [4]

**Ru has the strongest direct-etch evidence.** Its semi-damascene route deposits metal, patterns a hard mask, transfers the pattern into Ru, cleans the gaps, and introduces dielectric or air gaps between the lines. This avoids the need to fill every narrow line trench with metal. The advantage is especially important for high-aspect-ratio lines, whose height can be increased without the same trench-fill restriction. [2]

**Pilot-line results quantify that progress.** Murdoch and colleagues’ 2020 work reported more than 80% reproducibility for 30 nm-pitch Ru line structures fabricated in a 300 mm cleanroom. Pokhrel and colleagues’ 2022 study then demonstrated 9–10 nm critical dimensions and aspect ratios of three to six at targeted pitches of 18–26 nm using extreme-ultraviolet lithography, self-aligned double patterning, and direct Ru etching. [28][29]

**The tightest pitch still changes yield.** For 10 μm-long Ru lines at aspect ratio three, more than 90% of devices met the resistance target below 700 Ω/μm at 20–26 nm pitch, compared with approximately 50% at 18 nm pitch. More than 90% met the reported leakage target of \(10^{-11}\) A/μm. These distributions are more informative about process readiness than a best-performing isolated line. [29]

**Multilevel integration adds alignment demands.** The 2022 two-level Ru flow used a 30 nm PVD film, a 420 °C anneal, a SiN hard mask, selective Ru RIE, and ALD SiO₂ gap fill. It demonstrated functional fully self-aligned vias with programmed placement errors up to 5 nm. The significance is that line formation, dielectric filling, via placement, and electrical continuity were exercised together. [2]

**Avoiding metal CMP is not CMP-free integration.** The same Ru flow planarized the deposited dielectric by CMP. Semi-damascene removes a particular source of metal-height variation and polishing difficulty, but still requires a planar surface for subsequent lithography and interconnection. It also exchanges metal trench-filling difficulty for dielectric gap filling, post-etch cleaning, and mechanical control of exposed lines. [2]

**Mo and NiAl occupy different stages.** As an evidence-based maturity estimate, Mo spans unit-process to early-module development: linerless ALD filling is demonstrated, and direct-metal-etch development appears in the 2022 literature on Ru and Mo at 32 nm pitch and below. NiAl spans materials-film to planarization-unit-process development, anchored by PVD, epitaxial transport, and CMP backthinning. These ranges describe demonstrated building blocks rather than numerical technology-readiness scores. [6][30][14]

**Qualification depends on retained properties.** For those maturity judgments to advance, directional patterning must preserve line conductivity and composition, while patterned CMP—or a credible no-metal-CMP route—must deliver controllable dimensions and clean contacts. Reproducible gap filling, multilevel alignment, and reliability across the intended wafer-scale process then determine manufacturing suitability. These conditions distinguish a successful material operation from a completed interconnect module.

**Thermal budget can reverse material choices.** The cited reviews place ordinary BEOL processing around or below 400 °C, while research demonstrations include NiAl deposition and Ru annealing at 420 °C, and CoPt phase formation at 700 °C. These temperatures have different implications: a modest excursion requires stack-specific assessment, whereas a much higher-temperature phase-forming step poses a more substantial integration conflict. Thermal exposure must be evaluated by temperature, duration, and processing sequence. [3][16]

**Takeaway: select the scheme with the metal.** Damascene rewards fillability and CMP control; semi-damascene rewards directional metal etching and subsequent dielectric integration, and neither route removes the need for reliable vias and clean interfaces.

### Sustainability

**Sustainability can change the technical shortlist.** Environmental burden, supply concentration, toxicity, cost, and by-product dependence matter alongside electrical performance. A January 2024 preprint assessed alternative local-interconnect metals across seven sustainability aspects and nine indicators. Ti, Al, Ni, Co, and Mo performed relatively favorably on at least six indicators, while several platinum-group metals, including Ru, performed more poorly. This supports adding sustainability early without treating it as a substitute for technical qualification. [31]

**GWP measures greenhouse-gas impact.** Global Warming Potential, or GWP, expresses climate impact in carbon-dioxide-equivalent terms over a stated time horizon. A material-production comparison typically uses kg CO₂-equivalent per kg of metal, with an explicit life-cycle boundary. Nuss and Eckelman’s 2014 assessment used one kilogram of metal at the factory gate, covered 63 metals, and modeled global production using 2008 data. [32]

**Per-kilogram and annual impacts differ.** That assessment places platinum-group metals, including Ru, among the highest environmental burdens per kilogram. Cu, together with Fe and Al, has high total annual impacts because of production volume. Thus, “Cu has high annual impact” and “Ru has high impact per kilogram” describe different denominators and do not establish a direct per-wire ranking. [32]

**Refining and allocation affect results.** The same study finds purification and refining dominant for most metals and treats 42 of its 63 elements as by-products or co-products of multi-output processes. Shared impacts were allocated using economic information, so allocation assumptions influence the burden assigned to individual metals. Semiconductor-grade purification, precursor synthesis, deposition efficiency, etching, polishing, and yield then add further process-specific effects. [32]

**The useful functional unit is a working interconnect.** For engineering selection, the relevant comparison is a completed line or via meeting the same resistance, pitch, and lifetime requirement. A high-impact-per-kilogram material might use less volume or avoid other operations; conversely, a low-impact feedstock might require costly deposition or annealing. This is a decision principle, not a numerical life-cycle result, and it follows the 2024 assessment’s emphasis on case-specific functional units. [31]

**HHI quantifies supply concentration.** The Herfindahl–Hirschman Index is the sum of squared market shares. Using percentage shares \(s_i\), its form is:

\[
HHI=\sum_i s_i^2.
\]

**The market boundary determines its meaning.** Country shares of mined ore, company shares of refined metal, and qualified suppliers of semiconductor-grade targets or precursors are different populations. A high HHI indicates concentration within the chosen population, but does not alone capture political risk, substitutability, stockpiles, recycling, or the time needed to qualify another supplier. The BCG/SIA 2021 study’s identification of more than 50 semiconductor value-chain points dominated by one region illustrates why concentration is operationally relevant. [33]

**Cobalt permits a transparent concentration bound.** Goswami’s 2023 *MIT Science Policy Review* article reports approximately 70% of mined Co from the Democratic Republic of the Congo. Treating that approximate share as 70% for calculation gives a limiting country-level HHI range of approximately 4,900–5,800 points: `70² + 0` if the remaining share is very widely dispersed, to `70² + 30²` if it belongs to one other country. This is a calculated mined-supply proxy, distinct from semiconductor-grade supplier concentration. [34]

**By-product dependence adds another exposure.** Most Co is recovered as a Cu or Ni by-product, so its supply response is linked to other mining markets. This can coexist with a favorable result on several environmental or broader sustainability indicators. Similarly, NiAl’s constituent metals can score favorably without fixing the compound’s final footprint: Ni/Al procurement, target or precursor production, deposition losses, and annealing determine the relevant compound-level judgment. [34][31]

**Takeaway: keep the indicators separate.** Ru’s technical advantages face a significant per-kilogram environmental trade-off; Co’s favorable reliability faces concentrated mined supply; and Mo’s favorable broad screening remains dependent on the actual refinery, precursor, and fabrication route.

### Applying the criteria together

**Selection requires four linked judgments.** The criteria are complementary: electrical screening identifies a possible performance advantage, reliability determines whether it is durable, manufacturing determines whether it is reproducible, and sustainability determines whether its wider burdens are acceptable. The purpose is not to assign a universal winning metal, but to identify a defensible material–scheme choice for the target interconnect level.

| Evaluation dimension | Decisive question | Evidence that carries most weight | Resulting judgment |
|---|---|---|---|
| Electrical performance | Does the finished structure reduce resistance or RC? | Matched line/via measurements; \(ρ₀λ\); geometry | Dimension-specific electrical advantage |
| Reliability | Can auxiliary layers be reduced safely? | EM, storage, adhesion, diffusion, TDDB | Qualified interface and lifetime behavior |
| Process maturity | Can the selected scheme be reproduced? | Fill, etch, CMP, gap fill, multilevel distributions | Manufacturing-route suitability |
| Sustainability | Is the complete option acceptable? | Common-boundary GWP and defined supply concentration | Environmental and procurement trade-off |

**Trade-offs can favor selective adoption.** A Cu upper-level line, a Co contact or local segment, and a directly etched Ru lowest-level line can each be rational within the same technology. This is consistent with the integration literature’s conclusion that no single metallization approach satisfies all BEOL levels simultaneously. [4]

**Additional documented evidence**

Through early 2024, Ruthenium had demonstrated a credible alternative-metal interconnect role: Ru was benchmarked against Cu in a damascene vehicle at scaled dimensions, and barrierless Ru showed lower resistance than Cu below a trench cross-sectional area of 250nm2 and higher electromigration lifetimes than Cu and Co. 250nm2 nm2 (trench cross-sectional area; 2018; Ru and Cu damascene interconnects; benchmarking and calibrated-model predictions). [39]

The source identifies electromigration performance and lifetime as reliability dimensions for comparing interconnect metals; barrierless Ru systems showed higher lifetimes than Cu and Co. [39]

The source uses line resistance, via resistance, trench cross-sectional area, resistivity, inelastic mean free path, and electromigration performance or lifetime to screen alternative interconnect metals. [39]

The source-supported screening dimensions include interconnect electrical resistivity, current density, Joule heating, thermal conductivity, thermal resistance, line width, via density and configuration, dielectric properties, package cooling, and reliability effects such as electromigration and stress migration. [68]

Thermal screening should consider BEOL temperature rise, metal-line self-heating, current density, electrical resistivity, dielectric thermal conductivity, melting or thermal limits, and thermal resistance. Scaling increases resistivity and current-density requirements, while poor low-k dielectric conductivity adds to heating. [68]

Thermal stability screening should connect temperature rise and Joule heating to electromigration, stress migration, process-node scaling, dielectric conductivity, via configuration, package cooling, and thermal resistance. The source reports that elemental-metal thermal conductivity significantly drops below 10 nm line width and that the metal choice has minimal impact on thermal dissipation in the evaluated 14-layer BEOL stack. <10nm line width (line width; evaluated elemental metals; BTE modeling). 14-layer BEOL stack (number of layers; advanced technology node BEOL stack; multi-step modeling framework). [68]

The source's screening dimensions include bulk resistivity, carrier mean free path, cohesive energy, dielectric adhesion, thermodynamic stability, BEOL-compatible annealing temperature, toxicity, rarity, cost, resistivity scaling in thin films and patterned lines, stoichiometry, surface oxidation, and etchability. [76]

The page identifies cobalt-based binary compounds as candidate advanced-interconnect materials and reports that a high-throughput screening method identified several compounds with potentially superior electronic transport and reliability at reduced thickness. However, this source is dated 14 March 2026 and is outside the provisional 2024-03-31 cutoff. [75]

The source states that nanoscale confinement makes current density more sensitive to scattering induced by impurities, grain boundaries, and surface roughness, increasing resistivity. It also notes that diffusion barriers and adhesion layers can occupy 2 to 3 nm of interconnect width, reducing the section available for current transport. 2 to 3 nm nm (thickness or width occupied by diffusion barriers and adhesion layers; Cu interconnect). [72]

The source presents Cu as the most performant candidate among the metals considered in its bulk-intrinsic screening, while noting that Cu interconnects require TaN and Ta barriers and exhibit increasing sensitivity to scattering and electromigration in confined dimensions. [72]

Resistivity scaling matters because copper exhibits significant size effects, while tantalum-based diffusion barriers impose thickness-scaling limitations; the λρo figure of merit matters because it identifies metals that may retain better resistivity scaling than Cu at nanometer dimensions. Supply-chain metrics matter because earth-to-manufacturing factors influence pricing and may reveal opportunities for future cost reductions. [168]

The source is a free ECS Meeting Abstracts article published in 2021. It reports a literature search, thin-film resistivity analysis, and supply-chain examination; the supplied page identifies the authors, DOI, publication venue, and copyright year, but does not state a primary-versus-secondary classification or an explicit comparability assessment. 272 Total downloads downloads (article downloads; this article). [168]

The source provides resistivity as a function of temperature and derives specific resistivity from resistivity at initial geometry combined with thermal expansion. The pulse-heating compilation uses homogeneous measurement conditions across the investigated pure metals, making it a starting point for comparative analyses, but the measurements primarily cover temperatures around melting rather than a standardized room-temperature bulk reference. [166]

The source was published on 2011-01-01, which is before the provisional 2024-03-31 early-2024 evidence endpoint. 2011-01-01 (publication date; source). [166]

Sustainability screening can include raw material price, supply risk, normalized vulnerability to supply restriction, embodied energy, water usage, rock-to-metal ratio, human health damage, human rights pressure, and labor rights pressure. These dimensions address economic, environmental, and societal impacts in addition to technical performance. [164]

Relevant supplementary dimensions include supply risk, vulnerability to supply restriction, embodied energy, water usage, rock-to-metal ratio, human-health damage, human-rights pressure, labor-rights pressure, and raw material price. [164]

At interconnect widths approaching 10nm, Cu's resistivity increases dramatically and its reliability degrades, motivating the search for alternatives to Cu metallization. 10nm nm (interconnect-line width; most critical interconnect lines in state-of-the-art logic and memory chips). [169]

Ruthenium (Ru): For narrow interconnect lines, grain-boundary reflection contributes to resistivity scaling, while liner thickness changes the available conducting cross-sectional area. [170]


**Screening frame**

Electromigration in Cu, Ru and Mo is driven by electron–atom momentum transfer and current-induced atom flux; current density, temperature/Joule heating, geometry, waveform, interfaces, diffusion paths and grain structure control drift, voiding and lifetime. Interface diffusion is a major Cu path and scaling increases grain-boundary transport; barrierless Ru/Mo at sub-10 nm therefore require MTTF, activation-energy and TCR tests, with Ru/Co activation energies near ≈1 eV sensitive to Joule-heated void temperature [158][67][163][171][177].

Barrier/liner removal is attractive because Cu occupies 25% of total interconnection [160], but recovered conductor volume must not sacrifice dielectric containment. Scaling raises fields; porous low-k, CMP/interface defects and conductor diffusion cause leakage and TDDB through traps or shorts, Co ions degrade porous low-k under stress, whereas Ru–Zn blocks Cu-ion diffusion and protects Cu from oxidation [161][63][162][113][178].

Cohesive energy is an intrinsic bonding proxy for electromigration and diffusion-barrier need, so it can pre-screen Co and other candidates; interface adhesion also matters when interfacial diffusion dominates [174][179]. It cannot predict lifetime alone: transport has multiple pathways and depends on current density, temperature and spacing, while cohesive-energy values depend on computational conditions; use it for ranking, then validate reliability experimentally [175][180][181][174].

Apply an Evidence-Gated Candidate Rubric to Elemental Metals, Binary Intermetallic Compounds, Ternary Compounds and Other Emerging Materials [72], and to Copper (Cu), Ruthenium (Ru), Molybdenum (Mo), Cobalt (Co) and Nickel Aluminide (NiAl) [173]. For each, require reduced-dimension conductivity/electronic, cohesive-energy/EM-TDDB, process-integration and supply/environmental evidence [72][173][164]; classify candidates as representative when documented, promising when every dimension is supported, uncertain when phase/lifetime/process evidence is incomplete, and excluded when a dimension fails, so conductivity cannot outweigh integration or sustainability risk [72][173].

Nickel’s clean-energy transition assessment reports low supply risks but high geopolitical risks, with high geographical concentration in both mining and refining [56]. Resistance and capacitance are screening metrics: RC scaling evaluates advanced metallization; their changes affect narrow-pitch interconnect performance [159].

BEOL interconnect resistance affects circuit power, performance and area; limits grow more severe with longer wires and greater circuit complexity [57]. Globally, a cradle-to-gate life-cycle assessment assessed 63 metals in their major use forms for reference year 2008 [165].

Post-cutoff sustainability dimensions for 3D RDL include environmental impacts, mineral-resource depletion, recycling/waste, and reparability/chip reuse [183]. Post-cutoff evidence reports cryogenic ICP-RIE at -120 ℃ reduced low-k plasma damage and improved breakdown/TDDB [182]. Ti2AlC is a ternary MAX phase in Cu/Ti2AlC composites, not an on-chip interconnect [176].

Sustainability screening found climate change was the focus of 64% of the LCAs in literature assessing mining impacts [167]. Cu interconnect had 1.6 μΩ·cm resistivity (10 mm-long, 0.025 μm-wide, 8:1 aspect ratio) in a nanoscale comparison, not an unconstrained bulk reference [43]. TaAs nanobelt structures had ~ 35 μΩ cm resistivity at ~ 200 nm width in a nanoscale interconnect structure [160].

Feature-filling behavior, deposit microstructure, thermal annealing, and reliability constraints guide screening [116]. On 23 May 2023, NiAl’s 7.7nm-thick binary-alloy film on a 300mm Si wafer had resistivity as low as 11.5µWcm, 23% lower than Cu; the lowest value came from an epi binary alloy deposited at 50nm, then thinned, with 45.7nm grain size [169].

Binary intermetallics are candidate conductors: ordered stoichiometric structures can sharply reduce resistivity; bonding aids reliability/adhesion, but composition, oxides, filling, integration limit them [108]. CMP: metal/barrier removal-rate selectivity and Cu/Co–Al/Co corrosion control [172].

## Part 3 — Comparison Table of Core Candidate Materials

**Cu is the benchmark below.** The table compares the five requested materials by their best-supported advantages, principal integration challenges, demonstrated processing functions, and sustainability implications through early 2024. Process maturity describes the relevant route: industrial Cu damascene, demonstrated Ru semi-damascene, established Co local-metallization experience, and the more development-stage Mo and NiAl cases.

| Metal | Core Advantages | Main Challenges | Process Maturity (RIE/CMP) | Sustainability Brief (Supply Risk/GWP) |
|---|---|---|---|---|
| Copper (Cu) | ≈1.7 μΩ·cm bulk; established fill and planarization | Size scattering; barrier/liner area; diffusion and EM | Dielectric RIE and CMP industrial; direct Cu RIE difficult | Supply: abundant feedstock; GWP: large annual-volume impact |
| Ruthenium (Ru) | Barrierless potential; demonstrated crossover below 12 nm | Higher bulk resistivity; fill, polishing, and gap-fill demands | Direct RIE demonstrated on 300 mm; semi-damascene avoids metal CMP | Supply: rare-PGM exposure; GWP: high per kilogram |
| Molybdenum (Mo) | Linerless ALD fill to 10 nm CD; dielectric adhesion | Roughness sensitivity; scheme-specific process control | RIE development; CMP integration gate; estimated unit-process–early-module range | Supply/GWP: favorable overall screening; refinery and precursor route decisive |
| Cobalt (Co) | Strong comparative EM results; established local-interconnect use | Dielectric-dependent barrier need; interfaces; galvanic corrosion | Fill and subtractive wires demonstrated; RIE route-specific; CMP corrosion-sensitive | Supply: estimated mined-country HHI 4,900–5,800; GWP: production-route dependent |
| Nickel Aluminide (NiAl) | Ordered B2; 11.5 μΩ·cm at 7.7 nm in epitaxial/CMP films | Stoichiometry, oxidation, crystallinity, and substrate transfer | CMP backthinning demonstrated; RIE qualification gate; estimated film–unit-process range | Supply: Ni/Al chains; GWP: synthesis/anneal dependent; favorable constituent screening |

**The table rests on distinct evidence.** Cu’s benchmark and mature processing follow the transport-screening reference [7] and Cu integration review [4]. Ru’s crossover and multilevel etching follow the two-level demonstration [2]. Mo’s filling and roughness judgments follow the ALD study [6] and quantum-transport comparison [9]. Co’s reliability and interface judgments follow the Co-fill reliability study [24] and barrierless-via comparison [25], while NiAl’s film and CMP entries follow the 2023 thin-film study [14]. Environmental and supply entries use the metal LCA [32], January 2024 sustainability assessment [31], and Co supply analysis [34].

**The practical preference is conditional.** For directly etched, aggressively scaled local lines, Ru has the most persuasive combined electrical and integration case among these five. For reliability-led local structures, Co is a demonstrated option, subject to dielectric and interface control. Mo is especially attractive where linerless filling is the bottleneck, while NiAl offers a credible route beyond elemental metals when its favorable ordered microstructure can be transferred into the intended stack.

**Evidence boundaries govern interpretation.** This survey uses public results through early 2024; measured films, patterned lines, model inputs, simulations, and patent concepts are identified separately. Resistivity values retain their thickness, substrate, and processing context; \(ρ₀λ\) values retain their calculation basis; the area, resistance-per-length, maturity-range, and cobalt-HHI results are explicitly calculated or assessed estimates. GWP statements distinguish per-kilogram from annual-production impacts, and mined-country concentration is not substituted for qualified semiconductor-material supply.

**The central conclusion is integration-led.** The strongest alternative is the one that converts favorable confined transport and atomic stability into lower-resistance, reliable, reproducible wiring at the target footprint. Through early 2024, that makes Ru the leading scaled-line development option, while preserving important roles for Cu, Co, Mo, and ordered compounds rather than supporting a single universal replacement.

**Additional documented evidence**

Copper (Cu): The source identifies resistivity, interconnect delay, current-carrying capability, Joule heating, electromigration, temperature, and leakage power as core dimensions for evaluating nanoscale interconnects. [38]

Interconnect delay depends on wiring level and length: long unbuffered-line delay is quadratic in length, optimally buffered-line delay is linear in length, and low-dielectric-constant materials can reduce capacitance and delay. [38]

Copper (Cu): Copper serves as the incumbent reference material: the study compares Ru and Co with Cu line performance and reports Cu bulk resistivity, mean free path, liner thickness, predicted resistivity, and resistance under the same modeled geometry. ρo = 1.7 µΩcm µΩcm (bulk resistivity; Cu; reported bulk values used in calculation). λ = 39 nm nm (mean free path; Cu; previous reports). [51]

Nickel Aluminide (NiAl): The source is dated 2019-07-11 and compares calculated RuAl parameters with those of the NiAl heat-resistant alloy; this provides a source-date basis and an example of a calculation-based comparison, but not a common advanced-interconnect comparison convention for the five table rows. NiAl (NiAl heat-resistant alloy; comparison of calculated RuAl parameters with NiAl). [144]

A fair comparison can use data collected under homogeneous conditions because the compilation used the same measurement technique and laboratory for every element. The source identifies this homogeneity as a basis for comparative analyses. [166]

Nickel Aluminide (NiAl): The source states that Cu resistivity increases dramatically and reliability degrades as critical interconnect widths approach 10nm, motivating alternatives. For binary-alloy thin films, resistivity is dominated by grain-boundary scattering at small grain sizes, while disorder contributes more for thicker films. The source also identifies the product of bulk resistivity and carrier mean free path, “r0 x l,” as a main figure of merit, but gives no NiAl-specific numerical r0 x l value. 10nm nm (critical interconnect-line width; state-of-the-art logic and memory chips). r0 x l (bulk resistivity–carrier mean-free-path product; candidate interconnect materials; ab-initio-based methodology). [192]


Copper (Cu): The source identifies the benchmark material as copper, written as Cu in the context of Cu interconnect CMP. [193]

Copper (Cu): Cu's core advantage is excellent wafer-level planarization ability, which enables device structures such as shallow trench isolation and multi-level interconnects. [193]

Copper (Cu): Cu has low resistivity, lower cost than silver and gold, and high electromigration resistance with substantially higher current-density tolerance than Al. Cu damascene also enables flat multilayer interconnects, including 10 layers or more. less than two-thirds of Al (resistivity; Cu relative to Al). almost one order of magnitude (higher current density tolerance; Cu relative to Al). 10 layers or more layers (multilayer interconnect count; Cu interconnects). [195]

Copper (Cu): Cu was difficult to etch by RIE, which hindered its practical use; Cu damascene also required specialized deep-trench filling, sidewall film formation, and plating-process development. [195]


| `Metal` | `Core Advantages` | `Main Challenges` | `Process Maturity (RIE/CMP)` | `Sustainability Brief (Supply Risk/GWP)` |
| --- | --- | --- | --- | --- |
| Copper (Cu)[196]; Copper (Cu)[202]; Copper (Cu)[109] | Low resistivity; lower cost than Ag/Au; high thermal conductivity; high electromigration/current-density tolerance; established flat multilayer damascene/CMP; Low resistivity/high conductivity; better electromigration durability…[195][147] | At 10 nm, resistivity ~10× bulk from surface/grain-boundary scattering; resistive barriers/liners consume area; Cu-diffusion reliability and RIE challenges; Under-15-nm resistivity/scattering and delay…[111][63] | RIE: difficult and experimentally demonstrated only; damascene avoids Cu RIE; CMP: established in mass-production damascene; CMP: documented in incumbent Cu damascene; RIE: dielectric-trench etch, not Cu etch; RIE: experimental…[195][189] | HHI 1,097 on 0–10,000 scale; relative embedded GWP 1.00 vs Cu; 2.51E-02 kg CO2eq/cm³; generic data likely underestimate semiconductor-grade impacts; HHI 1,097 on 0–10,000 scale; relative embedded GWP 1.00 vs Cu; generic…[123][200] |
| Ruthenium (Ru)[194]; Ruthenium (Ru)[201]; Ruthenium (Ru)[187] | Barrierless integration; low scaled resistivity; strong electromigration/TDDB reliability; no metal CMP in semi-damascene; Barrierless/liner-free integration; short EMFP (~5.7 nm); strong EM/TDDB reliability; continuous films to…[197][199] | Concentrated reserves/by-product dependence; RuO4 toxicity and oxidation; selective deposition/morphology control; long ALD/CVD-like process times; PGE supply-risk index 7.6/10 (Ru-group proxy); electrodeposition, morphology…[198][199] | RIE: no direct result in cited evaluation; CMP: no direct result in cited evaluation; CVD/ALD, etch-back and semi-damascene evidence; RIE: near-vertical patterning capability; CMP: Ru/Cu removal selectivity 0.1–2.7 demonstrated…[72][108] | IHH 0.96 (global reserve concentration); primary-production GWP 33.9 kg CO2e/g, cradle-to-gate; HHI 8,718 (global, 2021); relative embedded GWP 1,040× Cu; HHI 8,718 (global, 2021); relative embedded GWP 1,040× Cu (proxy…[198][191] |
| Molybdenum (Mo)[194]; Molybdenum (Mo)[201] | Short EMFP (~11 nm), weaker resistivity scaling, high melting point (2896 K), and barrierless/subtractive integration potential; Short EMFP (11–15 nm), high melting point (2896 K), barrier/liner-free 10 nm-CD fill potential, and…[83][52] | Grain/process-dependent resistivity, oxidation/contamination, specialized selective etch/cleaning and CMP integration, and Cu-byproduct supply dependence; Grain/process-dependent resistivity, oxidation/contamination, specialized…[52][149] | RIE/ALE: lab-level Cl2 plasma etch, including non-optimized 32 nm-pitch semi-damascene work; CMP: no eligible maturity evidence[185][111] | HHI 2,266 (2021); relative embedded GWP 2.32× Cu; proxy values, not semiconductor-interconnect-specific; HHI 2,266 (2021); relative embedded GWP 2.32× Cu; relative volumetric proxy; HHI 2,266; relative embedded GWP 2.32× Cu…[123] |

Ruthenium (Ru) resistance evidence retains setup, current, temperature, subtraction and uncertainty . Evidence is limited, condition-specific, not table-wide: Ru(0001) films model Co crossover at approximately 20 nm; epitaxial Co-on-Ru deposition shows BEOL feasibility [204]. Global-reserve concentration, by-product dependence and difficult recycling challenge Ru (IHH = 0.96; September 2020) [198].

Copper (Cu): CMP was put into practical use in the late 1980’s, advancing Cu interconnect mass production with damascene; damascene requires no Cu RIE and removes excess metal by CMP. [195] It is the benchmark interconnect material used to evaluate novel wire, via, barrier/liner, and alternative material options at advanced nodes. [57]

Molybdenum (Mo) ALE used chlorine and argon plasma; pulsed ALE at 40° C, 10% duty cycle achieved about 5-6 Å per cycle versus 2-3 Å per cycle for continuous ALE; CMP evidence is absent. [111] Its 2021 primary-production supply HHI was 2,266 HHI points on a 0–10000 scale; relative embedded GWP was 2.32 relative to Cu for production of equal metal volume. [123]

Nickel Aluminide (NiAl): 2019-07-11 calculated RuAl parameters vs NiAl heat-resistant alloy, not common advanced-interconnect basis [144]; 2024-05-01: it is studied as potential post-Cu interconnect with 400 ºC anneal; its aluminum-rich oxide may act as a self-forming barrier at NiAl/SiO2. [66]

Molybdenum (Mo), 2024-04-15: electrical test structures on six wafers measured ALD film thicknesses of 1.5, 1.8, 2.5, 3.8, 4.8, and 8.9 nm; chlorine/argon pulsed RIE/ALE at 40° C and 10% duty cycle reached 75% synergy; CMP, wafer-level interconnect integration, production-readiness, GWP, and HHI evidence was not reported [188][111].

Ruthenium's challenges are very high supply risk, PGM by-product dependence, concentrated reserves (IHH = 0.96 for global reserves), difficult recycling and possible future production decline; partial substitution can entail lower efficiency or higher costs. [198] HHI measures country-share concentration from 0 to 10 000; high values signal disruption and price-volatility risk. [190]

For Copper (Cu), smaller interconnect dimensions make line resistance a critical scaling roadblock, motivating consideration of Cu replacements such as Co. [40] At the page’s 2019 publication, a 12 nm half-pitch was used to model replacing Cu with advanced metallization. [159]

Cobalt (Co), scaled-interconnect alternative, has limited, condition-specific evidence: Co(0001) resistivity measured; epitaxial electrochemical Co/Ru deposition feasible for BEOL; air degraded Co-film specularity; 6–9 July 2021 AR vias found Ru resistance ~2x higher than Co on 1.1nm TiN and no Co/Ru failure in 1000 thermal-shock cycles (−50–125 °C; 250 hours). [204][186]

**Comparison basis**

Cu is the benchmark: high line resistance and poor electromigration reliability motivate liner/barrier-free alternatives [184]. Mo and Co have only a partial screen case—relatively favourable on at least six of nine sustainability indicators—while NiAl is a proposed intermetallic with incomplete thermal, filling, process and sustainability evidence; Ru’s corresponding evidence is not reported, so no balanced ranking is established [267,77,194,370,404,604].

Cu, Ru, Mo, Co and NiAl are survey-derived comparison rows under Metal; Core Advantages; Main Challenges; Process Maturity (RIE/CMP); and Sustainability Brief (Supply Risk/GWP). Screening covers resistivity, delay, current-carrying capability, Joule heating, electromigration, temperature and leakage power [38]; Cu’s HHI is 1,097 and relative embedded GWP 1.00 [123], while common reliability conditions and GWP/HHI definitions remain not established [4,267].

Compare scaled local CMOS lines/vias while separating bulk from patterned features, barriers/liners, contacts and package wiring: Cu bulk resistivity is 1.68 μOhm.cm; 1.56 μOhm.cm and the cited regime is sub-10 nm [121,109]. The mandatory Cu, Ru, Mo, Co and NiAl roster and requested column meanings are retained, but common temperature, feature size, film/crystal condition, method, integration level, date and sustainability boundary are not established, so no numerical equivalence is claimed [245,366,701,226,400,569].

rejected: citation_outside_operands. Allowed entities: Copper (Cu), Ruthenium (Ru), Molybdenum (Mo), Cobalt (Co), and Nickel Aluminide (NiAl). Allowed values include sub-10 nm, ~20%, late 1980’s, 1.00, 2.51E-02 kg CO2eq/cm³, IHH = 0.96, Mo95.95, and 300-mm; allowed citations include [4,206,267,280,287,416,537,558,568,571,573,575,576].

rejected: citation_outside_operands. Allowed entities: Copper (Cu), Ruthenium (Ru), Molybdenum (Mo), Cobalt (Co), and Nickel Aluminide (NiAl). Allowed values include sub-10 nm, ~20%, late 1980’s, 1.00, 2.51E-02 kg CO2eq/cm³, IHH = 0.96, Mo95.95, and 300-mm; allowed citations include [4,206,267,280,287,416,537,558,568,571,573,575,576].

The ternary-compound category qualifies as part of the evolution beyond elemental alternative metals, with research targeting improved reliability and resistivity at small dimensions; AlCu and Al2Cu thin films have been investigated as potential alternatives for Cu in interconnect metallization schemes [42]. Feature size shrinks by 30% every 2-3 years, while wires do not improve and may get worse [203].

## References

[1] <https://doi.org/10.1109/iitc.2018.8456484> Ru, Ir, and Co narrow-line assessment
[2] <https://imec-publications.be/server/api/core/bitstreams/274523b3-0320-4c52-ba68-e48b971547c9/content> Two-level Ru results; Ru–Cu crossover; Ru resistivity and electrical area; Ru integration stack; Ru reliability measurements; Semi-damascene flow; Ru semi-dama…
[3] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10427378/> Cu scaling review; Co integration context; Elemental and W scaling analysis; Predicted versus experimental scaling; CuAl₂ scaling and filling; Aluminide interf…
[4] <https://www.mdpi.com/2079-9292/11/18/2914> BEOL hierarchy and integration; EM and thermal considerations; TDDB mechanisms and integration damage; Dielectric lifetime assessment; Damascene definitions; C…
[5] <https://www.imec-int.com/en/articles/promise-hybrid-graphenemetal-structures-advanced-interconnects> 2021 BEOL roadmap; RuV₃ candidate context; Graphene interconnect assessment; Multilayer and doping considerations; Graphene/Ru measurements; Hybrid transport i…
[6] <https://doi.org/10.1109/iitc52079.2022.9881322> MOL scaling study; Linerless ALD Mo; Mo filling demonstration; Mo filling
[7] <https://www.imec-int.com/en/articles/can-binary-or-ternary-compounds-beat-cu-future-interconnect-applications> Compound-material roadmap; Aluminide-film program; Electronic-structure screening rationale; Barrier and liner functions; Cohesive-energy screening; Stoichiome…
[8] <https://doi.org/10.1109/iitc.2018.8456810> Elemental-metal transport screening
[9] <https://doi.org/10.1103/physrevb.107.195422> Surface-roughness comparison; Quantum roughness study
[10] <https://doi.org/10.1109/led.2018.2821923> Scaled Co-wire study
[11] <https://doi.org/10.1109/iitc/mam57687.2023.10154839> Ordered-intermetallic transport
[12] <https://doi.org/10.1109/iitc51362.2021.9537364> NiAl and CuAl₂ candidates; CuAl₂ reliability assessment
[13] <https://doi.org/10.1109/iitc52079.2022.9881310> NiAl thin-film investigation; 2022 NiAl results; Matched-thickness NiAl comparison
[14] <https://doi.org/10.1109/iitc/mam57687.2023.10154878> 2023 NiAl results; NiAl backthinning study; NiAl CMP backthinning; NiAl film processing
[15] <https://patents.google.com/patent/US11749602B2/en> Topological conductor families; Named patent candidates; Topological-semimetal integration concept
[16] <https://www.mdpi.com/2079-9268/13/1/16> LaAlGe and Weyl-material context; Topological-interconnect background; CoPt film measurements; CoPt phase and grain characterization; Hybrid local-routing eval…
[17] <https://openresearchlibrary.org/ext/api/media/84a84494-31e6-4e82-95a1-9b623b44c6ee/assets/external_content.pdf> CoWP cap mechanisms; Interconnect reliability categories; Stress-induced voiding mechanisms; Cu manufacturing sequence; Cu seed and super-filling; Cu CMP stage…
[18] <https://doi.org/10.1007/s10854-018-9091-3> Ru–Mo–C damascene study; RuMoC II processing conditions
[19] <https://www.jstage.jst.go.jp/article/jsaprev/2023/0/2023_230210/_pdf> Graphene-capped Cu results; Co/Cu galvanic corrosion; Subtractive patterning context
[20] <https://export.arxiv.org/pdf/2209.06135v1.pdf> CoSi transport analysis; NbAs and CoSi scaling evidence; Defect-dependent CoSi transport
[21] <https://doi.org/10.1109/vlsitechnologyandcir46769.2022.9830488> Material–scheme selection criteria; Line, via, and integration criteria; Integration selection criteria
[22] <https://elton.freeshell.org/Mse311/Literature/AnnuRevMaterRes39-Josell-Tokei2009_interconnect-resistivity-review.pdf> Size-dependent resistivity review; Cu product and mean free path
[23] <https://doi.org/10.3390/nano12101760> Monte Carlo inputs; Grain-boundary and geometry study
[24] <https://doi.org/10.1109/irps.2018.8353641> Co EM, TDDB, and voiding study
[25] <https://doi.org/10.1109/iitc.2018.8430396> Barrierless Co via study; Dielectric-dependent Co integration; Melting-point reliability rationale
[26] <https://doi.org/10.1109/ted.2019.2949196> Activation energy and Joule heating
[27] <https://doi.org/10.1109/irps48227.2022.9764427> Package-level Co electromigration
[28] <https://doi.org/10.1109/iitc47697.2020.9515597> 2020 Ru semi-damascene
[29] <https://doi.org/10.1109/iitc52079.2022.9881278> 2022 high-aspect-ratio Ru lines; Ru resistance and leakage distributions
[30] <https://doi.org/10.1116/6.0001791> Ru/Mo patterning study
[31] <https://doi.org/10.48550/arxiv.2401.02864> January 2024 sustainability assessment; Case-specific sustainability comparison; Constituent sustainability screening
[32] <https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0101298> Metal life-cycle assessment; Mass and annual-production comparisons; Refining and co-product allocation
[33] <https://www.semiconductors.org/study-identifies-benefits-and-vulnerabilities-of-global-semiconductor-supply-chain-recommends-government-actions-to-strengthen-it/> Semiconductor concentration risks
[34] <https://doi.org/10.38105/spr.tnepby7ntp> Cobalt supply anchor; Co by-product dependence
[35] <https://doi.org/10.1149/2162-8777/ad78fd>
[36] <https://doi.org/10.1109/irps.2013.6531999>
[37] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9145433/>
[38] <https://web.ece.ucsb.edu/Faculty/Banerjee/pubs/JOM_102004_Interconnects.pdf>
[39] <https://doi.org/10.1109/iitc.2018.8430407>
[40] <https://doi.org/10.1109/iitc.2018.8430411>
[41] <https://doi.org/10.1002/advs.201801370>
[42] <https://doi.org/10.1109/iitc51362.2021.9537441>
[43] <https://www.mdpi.com/2079-9268/13/1/16>
[44] <https://pubs.aip.org/aip/jap/article/127/5/050901/595089/The-search-for-the-most-conductive-metal-for>
[45] <https://doi.org/10.1149/ma2021-01301007mtgabs>
[46] <https://patents.google.com/patent/US12046654B2>
[47] <https://doi.org/10.1109/iitc.2014.6831863>
[48] <https://iopscience.iop.org/article/10.1149/MA2022-0215809mtgabs>
[49] <https://www.semi.org/sites/semi.org/files/2024-02/MRHIEP-Final-report-for-publication.pdf>
[50] <https://doi.org/10.1109/nanotech.2018.8653560>
[51] <https://par.nsf.gov/servlets/purl/10089436>
[52] <https://doi.org/10.3390/nano13060957>
[53] <https://doi.org/10.1016/j.isci.2024.111460>
[54] <https://doi.org/10.1080/00986445.2011.576450>
[55] <https://www.sciencedirect.com/science/article/pii/S2772671123001407>
[56] <https://iea.blob.core.windows.net/assets/ee01701d-1d5c-4ba8-9df6-abeeac9de99a/GlobalCriticalMineralsOutlook2024.pdf>
[57] <https://doi.org/10.1109/ted.2023.3261828>
[58] <https://doi.org/10.1109/ted.2013.2286176>
[59] <https://doi.org/10.1063/1.5133671>
[60] <https://eps.ieee.org/wp-content/uploads/2026/05/HIR_22_2026_0.9-1.pdf>
[61] <https://doi.org/10.1016/j.mee.2016.01.002>
[62] <https://patents.google.com/patent/WO2014105477A1/en>
[63] <https://doi.org/10.1063/5.0013737>
[64] <https://doi.org/10.1063/5.0211802>
[65] <https://doi.org/10.1016/j.mtla.2022.101511>
[66] <https://doi.org/10.1016/j.jmrt.2024.05.152>
[67] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9230697/>
[68] <https://www.imec-int.com/en/articles/mitigating-thermal-bottleneck-advanced-interconnects>
[69] <https://www.mpie.de/4687921/fe-al-sustainable-alloys-for-demanding-applications>
[70] <https://doi.org/10.1109/iitc-amc.2016.7507698>
[71] <https://par.nsf.gov/servlets/purl/10146877>
[72] <https://doi.org/10.1149/2.0181501jss>
[73] <https://www.semanticscholar.org/paper/Intermetallic-Compounds-as-Alternatives-to-Copper-Adelmann-Soulie/32b7bffa413de058e923258ec444793d01287a2f>
[74] <https://doi.org/10.1109/iitc/mam57687.2023.10154839>
[75] <https://www.scilit.com/publications/0db1ea4f0ade8aaa9e84a50b2f0e9752>
[76] <https://www.imec-int.com/en/articles/can-binary-or-ternary-compounds-beat-cu-future-interconnect-applications>
[77] <https://doi.org/10.48550/arxiv.2405.02046>
[78] <https://doi.org/10.1179/1743280410y.0000000001>
[79] <https://doi.org/10.1109/sispad62626.2024.10733304>
[80] <https://imec-publications.be/entities/publication/97240dd0-ba16-49a4-8511-4a2202f4d7bf>
[81] <https://www.science.org/doi/10.1126/science.adk6189>
[82] <https://imec-publications.be/entities/publication/97240dd0-ba16-49a4-8511-4a2202f4d7bf/full>
[83] <https://doi.org/10.1039/d6tc00317f>
[84] <https://doi.org/10.1002/advs.202520535>
[85] <https://doi.org/10.1007/978-981-99-6649-3_62>
[86] <https://iopscience.iop.org/article/10.1149/MA2020-01221293mtgabs>
[87] <https://irds.ieee.org/images/files/pdf/2024/2024IRDS_MM.pdf>
[88] <https://doi.org/10.1093/nsr/nwad261>
[89] <https://tnano.org/2022/03/special-session-on-beol-compatible-materials-and-devices/>
[90] <https://semiengineering.com/new-beolmol-breakthroughs/>
[91] <https://doi.org/10.1038/s41699-017-0044-0>
[92] <https://ieeexplore.ieee.org/document/7676206/>
[93] <https://www.nature.com/articles/s41467-023-41815-4>
[94] <https://doi.org/10.3390/cryst13040578>
[95] <https://doi.org/10.54014/r143-nq0v>
[96] <https://doi.org/10.1021/acsanm.2c05165>
[97] <https://www.aimspress.com/article/doi/10.3934/matersci.2021016>
[98] <https://doi.org/10.1109/ted.2022.3225512>
[99] <https://doi.org/10.1109/inec.2016.7589426>
[100] <https://doi.org/10.1587/transele.2021fup0008>
[101] <https://doi.org/10.1116/6.0003579>
[102] <https://pubs.acs.org/nalefd/article/24/6/2102/148200/Graphene-All-Around-Cobalt-Interconnect-with-a>
[103] <https://www.nature.com/articles/s42005-021-00627-y>
[104] <https://doi.org/10.1038/s42005-021-00627-y>
[105] <https://arxiv.org/html/2507.10736v1>
[106] <https://doi.org/10.1063/1.4973273>
[107] <https://www.imec-int.com/en/press/imec-introduces-intermetallics-and-airgaps-advanced-interconnect-metallization-schemes>
[108] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10427378/>
[109] <https://advanced.onlinelibrary.wiley.com/doi/full/10.1002/advs.202207321>
[110] <https://doi.org/10.1002/admi.201801291>
[111] <https://patents.google.com/patent/US11935758B2>
[112] <https://doi.org/10.1109/iitc61274.2024.10732594>
[113] <https://doi.org/10.3390/electronics11182914>
[114] <https://www.jstage.jst.go.jp/article/jsaprev/2023/0/2023_230210/_pdf>
[115] <https://doi.org/10.1109/irps45951.2020.9129087>
[116] <https://google.iopscience.iop.org/article/10.1149/2.043312jes/pdf>
[117] <https://www.imec-int.com/en/articles/imec-demonstrates-semi-damascene-interconnects-fully-self-aligned-vias-18nm-metal-pitch>
[118] <https://www.imec-int.com/en/press/imec-presents-alternative-metals-advanced-interconnect-and-contact-schemes-path-2nm>
[119] <https://doi.org/10.1002/smll.202406713>
[120] <https://doi.org/10.3390/nano13202791>
[121] <https://doi.org/10.1109/ectc51909.2023.00069>
[122] <https://newsroom.lamresearch.com/moly-replacing-tungsten-semiconductors>
[123] <https://doi.org/10.48550/arxiv.2401.02864>
[124] <https://doi.org/10.7567/ssdm.2024.c-1-03>
[125] <https://doi.org/10.1063/5.0026837>
[126] <https://doi.org/10.1109/jmems.2011.2148156>
[127] <https://doi.org/10.1063/1.5049620>
[128] <https://www.annualreviews.org/content/journals/10.1146/annurev-matsci-070218-125911>
[129] <https://doi.org/10.5006/c1999-99266>
[130] <https://journals.indexcopernicus.com/api/file/viewByFileId/659747>
[131] <https://par.nsf.gov/servlets/purl/10402805>
[132] <https://doi.org/10.3390/ma16062175>
[133] <https://www.sciencedirect.com/science/article/abs/pii/S002202481730088X>
[134] <https://doi.org/10.1016/j.commatsci.2023.112348>
[135] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10609618/>
[136] <https://doi.org/10.1117/1.apn.1.2.024001>
[137] <https://escholarship.org/content/qt8hb2f1w5/qt8hb2f1w5.pdf>
[138] <https://pubs.aip.org/aip/apl/article/123/22/223101/2923481/Interface-atomic-structures-in-a-cadmium-arsenide>
[139] <https://docs.nlr.gov/docs/fy22osti/81743.pdf>
[140] <https://journals.aps.org/prx/pdf/10.1103/PhysRevX.14.041037>
[141] <https://doi.org/10.1103/physrevb.109.195139>
[142] <https://arxiv.org/abs/2303.16883>
[143] <https://www.osti.gov/servlets/purl/2222447>
[144] <https://doi.org/10.18799/24056529/2019/2/233>
[145] <https://doi.org/10.1063/5.0198235>
[146] <https://par.nsf.gov/servlets/purl/10231066>
[147] <https://nepp.nasa.gov/docuploads/D01C3750-EC11-4D94-B086E4FAD49123CF/CuInterconnect_Evalreport.pdf>
[148] <https://www.kth.se/social/upload/51277776f276544ee241cd44/sustainable2013.pdf>
[149] <https://nccavs-usergroups.avs.org/wp-content/uploads/2023/01/ICPT22-Session-E2-White.pdf>
[150] <https://doi.org/10.1109/iitc61274.2024.10732806>
[151] <https://doi.org/10.1007/s11669-024-01166-z>
[152] <https://www.sciencedirect.com/science/article/pii/S092134492030389X>
[153] <https://doi.org/10.1149/2.042312jes>
[154] <https://gyan.iitg.ac.in/items/d6cb2a36-6329-4a1c-b427-2d74c9a94833/full>
[155] <https://doi.org/10.2172/1224976>
[156] <https://patents.google.com/patent/US20190131273A1/en>
[157] <https://doi.org/10.1109/led.2010.2091490>
[158] <https://iopscience.iop.org/article/10.1149/2.0171501jss>
[159] <https://doi.org/10.1109/ted.2019.2902031>
[160] <https://link.springer.com/article/10.1007/s40820-025-01898-8>
[161] <https://doi.org/10.3390/coatings13101818>
[162] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5449018/>
[163] <https://www.intechopen.com/chapters/58180>
[164] <https://www.nature.com/articles/s41597-025-04568-x>
[165] <https://doi.org/10.1371/journal.pone.0101298>
[166] <https://doi.org/10.1051/epjconf/20111501018>
[167] <https://www.pbl.nl/system/files/document/2024-02/PBL-2024-Environmental-impacts-of-extraction-and-processing-of-raw-materials-for-the-energy-transition-5364.pdf>
[168] <https://iopscience.iop.org/article/10.1149/MA2021-0212627mtgabs>
[169] <https://www.imec-int.com/en/press/imec-first-demonstrate-conductor-films-300mm-wafers-lower-resistivity-cu-and-ru>
[170] <https://doi.org/10.1109/iedm13553.2020.9372060>
[171] <https://doi.org/10.1021/acsaelm.3c00070>
[172] <https://doi.org/10.4028/www.scientific.net/kem.882.171>
[173] <https://par.nsf.gov/servlets/purl/10349174>
[174] <https://research.vu.nl/files/1740228/B4.pdf>
[175] <https://doi.org/10.1109/iirw.2012.6468915>
[176] <https://pmc.ncbi.nlm.nih.gov/articles/PMC13382948/>
[177] <https://doi.org/10.1109/ted.2019.2949196>
[178] <https://doi.org/10.1063/5.0108688>
[179] <https://doi.org/10.1109/tdmr.2005.846308>
[180] <https://doi.org/10.1063/1.353807>
[181] <https://link.springer.com/article/10.1557/PROC-516-129>
[182] <https://avsconferences.org/AVS2024/Sessions/Schedule/82415>
[183] <https://doi.org/10.23919/egg62010.2024.10631207>
[184] <https://doi.org/10.1109/iitc/mam57687.2023.10154850>
[185] <https://doi.org/10.1149/ma2022-01281246mtgabs>
[186] <https://www.semiconductorpackagingnews.com/uploads/1/Press_briefing_imec_2021_IITC_1.pdf>
[187] <https://growthmarketreports.com/report/ruthenium-interconnect-metallization-stack-market>
[188] <https://doi.org/10.1109/icmts59902.2024.10520676>
[189] <https://doi.org/10.1149/ma2018-01/22/1397>
[190] <https://doi.org/10.1103/prxenergy.4.023003>
[191] <https://ipa-news.de/assets/pdfs/2023-06-12-lca-factsheet-on-iridium-ruthenium.pdf>
[192] <https://www.semiconductor-digest.com/imec-first-to-demonstrate-conductor-films-on-300mm-wafers-with-lower-resistivity-than-cu-and-ru/>
[193] <https://doi.org/10.1109/tsm.2013.2278855>
[194] <https://www.energy.gov/sites/prod/files/2020/07/f76/The%20Periodic%20Table%20of%20Elements.pdf>
[195] <https://www.shmj.or.jp/english/pdf/process/exhibi426E.pdf>
[196] <https://www.aut.ac.nz/__data/assets/pdf_file/0005/297869/periodic-table-v2.pdf>
[197] <https://google.iopscience.iop.org/article/10.1149/MA2023-02171177mtgabs>
[198] <https://www.mineralinfo.fr/sites/default/files/documents/2021-03/fichecriticiteruthenium-publique201015_0.pdf>
[199] <https://docslib.org/doc/5645499/development-of-metal-free-wet-etching-chemical-for-ruthenium-interconnect>
[200] <https://nora.nerc.ac.uk/id/eprint/513472/1/Risk_List_2015_FINAL.pdf>
[201] <https://opossum.cz/tools/sigmatables/Sigma_PMV_Metals.pdf>
[202] <https://digicollections.net/phint/pdf/b/5.3.Names,-symbols,-and-relative-atomic-masses-of-certain-e_.pdf>
[203] <https://pages.hmc.edu/harris/class/e158/04/lect21.pdf>
[204] <https://pubs.aip.org/avs/jva/article/38/3/033406/1065741/Epitaxial-metals-for-interconnects-beyond-Cu>
