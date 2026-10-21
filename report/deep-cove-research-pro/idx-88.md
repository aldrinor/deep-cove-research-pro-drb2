# Contact Engineering for Low-Resistance 2D FETs: Strategies and Evidence Through 2022

**Three complementary pathways address contact resistance:** top-contact engineering improves the electrode–basal-plane junction; edge-contact engineering creates a lateral injection interface at the material’s side plane; and contact-region/interface engineering modifies the semiconductor through doping or phase conversion, or introduces a controlled interlayer. Together, these strategies address the injection barrier, interface electronic states, tunneling resistance, and current crowding that limit two-dimensional material field-effect transistors, or 2D FETs.

**Several implementations reached the hundreds-of-ohms range:** representative results include **123 Ω·µm** for Bi/monolayer MoS₂, 190 Ω·µm for In/Au-alloy/monolayer MoS₂, and 200–300 Ω·µm for Au contacts incorporating n-butyllithium-converted metallic MoS₂. A plasma-distorted MoS₂ contact region reached 90 Ω·µm in a three-layer device; the corresponding monolayer entry was approximately 2,000 Ω·µm. These results make carrier polarity, layer number, thermal budget, and fabrication architecture central to selecting a strategy. [1][2][3]

| Technical pathway | Defining intervention | Representative results through 2022 | Engineering verdict |
|---|---|---|---|
| Top-contact engineering | Select the electrode and preserve its basal-plane interface | Bi/MoS₂: 123 Ω·µm; In/Au-alloy/MoS₂: 190 Ω·µm. [1][2] | Strong low-resistance n-type options; interface quality and thermal compatibility are decisive |
| Edge-contact engineering | Contact exposed side planes or grow a lateral conducting junction | Cr/Au/monolayer MoS₂: 2,500 Ω·µm; In/Au/six-layer MoS₂: 4,070 Ω·µm at \(V_G=60\) V. [3][4] | Particularly valuable for encapsulation, multilayer injection, and contact-length scaling |
| Contact-region/interface engineering | Change local carrier density, phase, or intervening material | Au/1T-MoS₂: 200–300 Ω·µm; AlOₓ-doped Au/MoS₂: 480 Ω·µm; distorted three-layer MoS₂: 90 Ω·µm. [5][6][3] | Can strongly improve injection without changing the external electrode; stability and process selectivity matter |

**The report resolves three questions:** what each pathway changes physically, which named implementations demonstrated useful device performance, and how their limitations affect engineering choices. The comparison tables provide the requested five fields; the accompanying analysis explains why superficially similar low-resistance results can arise from different mechanisms.

## Scope, classification, and contact physics

### Scope and the boundaries of the three pathways

**The scope is global and historical:** this report concerns contact-engineering strategies for reducing resistance in 2D-material FETs, with device developments published by 31 December 2022. MoS₂ receives the greatest attention because it supports the broadest comparison here; WSe₂, WS₂, MoTe₂, PdSe₂, and InSe provide important tests of material compatibility and carrier polarity.

**The three categories are operational:** they distinguish the principal engineering intervention, not three mutually exclusive physical structures. The literature also organizes contacts by electrode dimensionality, interfacial material, or whether fabrication is top-down or bottom-up. Choi and colleagues’ 2022 review explicitly discusses overlap between nominal top contacts and lateral contacts when the semiconductor underneath an electrode becomes conducting. [3]

**Pathway 1 changes the top junction:** the semiconductor’s basal plane is contacted using a selected metal, alloy, semimetal, or separately prepared conducting 2D electrode. Its inventory includes Sc, In/Au and Sn/Au alloys, Bi and Sb semimetals, transferred Ag/Pt electrodes, optimized metal evaporation, and conducting 2D electrodes such as degenerately doped WSe₂. The main purpose is to improve energy alignment and interfacial transmission without deliberately converting the channel’s contact region. [7][3]

**Pathway 2 changes the injection geometry:** an electrode reaches the exposed side plane, or a conducting material is grown laterally against the semiconductor. Its inventory includes plasma etching followed by metallization, in-situ edge cleaning, graphene-mediated hybrid contacts, and grown lateral junctions such as VS₂–MoS₂. A lateral VS₂–MoS₂ junction belongs here because its documented injection geometry is lateral, even though VS₂ is also a 2D metallic electrode material. [7]

**Pathway 3 changes the contact region:** the semiconductor beneath or adjacent to the electrode is doped, structurally converted, or separated from the metal by a controlled interfacial material. Its inventory includes n-butyllithium treatment, plasma- and laser-induced phase engineering, K and polyethyleneimine doping, AlOₓ-induced charge transfer, in-situ Fe doping, h-BN and TiO₂ tunneling layers, semiconductor interlayers, sacrificial Se protection, and controlled surface oxidation. A converted 1T/2H boundary is geometrically an edge junction, but its defining intervention is semiconductor phase conversion, so it is assigned to this third pathway. [8][9]

### The quantities and mechanisms that must remain distinct

**Contact resistance is width-normalized here:** \(R_c\), expressed in Ω·µm, denotes the resistance contribution of one contact multiplied by channel width. It differs from specific contact resistivity, commonly expressed in Ω·cm², and from the width-normalized drain current \(I_D/W\), expressed in µA/µm. Mobility, Schottky-barrier height, and on/off ratio describe other aspects of the device.

**Two contacts remain in series:** for symmetric source and drain contacts in a linear-resistance model, the channel and contact contributions obey the following relation, where \(R_{\mathrm{sh}}\) is channel sheet resistance, \(L\) is channel length, and \(W\) is width. This relation underlies transfer-length-method extraction. [3]

\[
R_{\mathrm{total}}W=R_{\mathrm{sh}}L+2R_c.
\]

**Four concepts describe different changes:** suppressing metal-induced gap states is not synonymous with depinning the Fermi level, forming an ohmic contact, or converting a semiconductor to a metallic phase.

| Concept | Physical meaning | Consequence for injection |
|---|---|---|
| MIGS suppression | Reduce metal-induced electronic states extending into the semiconductor’s bandgap | Can reduce interface-state-mediated pinning |
| Fermi-level depinning | Restore sensitivity of barrier height to electrode work function | Enables purposeful electron- or hole-barrier selection |
| Ohmic-contact formation | Obtain sufficiently nonrectifying, low-loss injection in the operating range | Can result from a small barrier or efficient tunneling through a narrow barrier |
| 2H–1T phase conversion | Change local atomic coordination and electronic structure | Creates a conducting contact region adjoining a semiconducting channel |

**MIGS and defects have different origins:** metal-induced gap states arise from electronic coupling across the junction, whereas disorder-induced gap states originate from defects, reactions, contamination, and processing damage. Both can participate in Fermi-level pinning: interface states accept charge and make the barrier less responsive to the selected metal. Liu, Stradins, and Wei’s 2016 calculations show how weakly interacting van der Waals interfaces can suppress MIGS and recover work-function-dependent barrier tuning. [10]

**Depinning restores control, not automatic improvement:** the pinning factor \(S\) measures the slope of electron Schottky-barrier height against metal work function. A value near zero indicates strong pinning; a value near one approaches ideal Schottky–Mott alignment. Whether depinning lowers resistance then depends on choosing a suitable electrode for the desired carrier. [9]

\[
S=\frac{d\Phi_{Bn}}{d\Phi_m}.
\]

**Barrier height is only one bottleneck:** electrons may cross a low barrier poorly if the electrode–channel coupling is weak, the tunneling separation is large, or conducting states couple inefficiently. Conversely, heavy contact-region doping can make a finite Schottky barrier sufficiently narrow for strong tunneling. A nearly linear output curve therefore supports a transport interpretation but does not, by itself, establish a zero barrier or a particular \(R_c\). [11]

**The central design problem is transmission:** top-interface cleaning reduces harmful states but may preserve a tunneling gap; edge bonding removes that gap but creates chemically sensitive edge states; doping increases tunneling without necessarily removing pinning. The best intervention is the one that removes the dominant bottleneck while preserving the transistor channel.

**Additional documented evidence**

Top/interface engineering lowers Schottky barriers and metal-induced gap states (MIGS)/Fermi-level pinning: a 1-nm TiO₂ interlayer in multilayer MoS₂ FET contacts raised the pinning factor from 0.02 to 0.24 and widened the controllable Schottky-barrier-height range from 37 to 344 meV [74]. The roster includes Sc, In/Au, Bi, Sb, vdW/laminated electrodes, buffer or tunneling layers, and SAM/work-function tuning [226,141,108,202,248]. Edge engineering creates bonded in-plane injection: plasma-treated graphene FETs reached 270 Ω·µm in 2014, a 77% reduction [76], while graphene edge contacts to monolayer MoS₂/WS₂ averaged 30 kΩ·µm in 2016 [72]; narrow edges can cause current crowding [63]. A phase-engineered 1T′-MoTe₂/2H-MoTe₂ FET array showed ohmic contact behavior and distinctly low Rc [75].

**Top-contact and metal–2D-interface engineering.** This pathway changes the interface while retaining a surface-contact geometry. Work-function and band alignment reduce the Schottky barrier; transfer or buffer layers avoid deposition damage and suppress Fermi-level pinning and MIGS; ultrathin tunnelling layers reduce the effective barrier but add tunnelling resistance. Solutions include selected 3D metals, transferred or laminated electrodes, graphene/metal contacts, h-BN, graphene or TiO₂ interlayers, chemical interface modification, and ultra-high-vacuum deposition [71]. Representative records include In contacts to layered InSe, which showed a 50-meV barrier and 410 µA/µm on-current at 2 K in 2018 [80]; graphene/Ag contacts on CVD-grown MoS₂, which in 2018 achieved 35 cm² V⁻¹ s⁻¹ mobility and a \(4\times10^8\) on/off ratio, although no absolute \(R_\mathrm{c}\) was reported [82]; and a monolayer-WS₂ tunnelling layer on MoTe₂, which yielded a 3-meV barrier and 1 MΩ·µm contact resistance at 300 K in 2021 [83].

**Edge or one-dimensional contact engineering.** Plasma or ion-beam exposure removes the basal material and exposes reactive edges for immediate metallization; end-bonded and vdW-gap-free contacts then inject carriers through the side of the 2D channel, reducing vdW-gap tunnelling and current crowding. In-situ Ar etching followed by metal deposition formed bonded MoS₂ edge interfaces, whereas ex-situ isotropic plasma could leave contaminated, reactive edges [78]. A monolayer-MoS₂ end-bond device reported 2.5 kΩ·µm contact resistance, with saturation-current densities of 730 µA/µm at 300 K and 960 µA/µm at 6 K (published 2021; issued 2022) [81]. The trade-off is demanding alignment, edge preservation, and in-situ or specialized equipment.

Top/interface solutions are metal selection, transferred electrodes, conductive 2D/graphene contacts, and h-BN, oxide or 2D-semiconductor interlayers. They lower Schottky barriers or suppress deposition damage, MIGS and Fermi-level pinning. In Ni/MoS₂, one–two-layer h-BN reduced SBH from **158 to 31 meV** and Rc from **5.1 to 1.8 kΩ·µm** at room temperature; per-contact status was unreported [84].

Edge/1D solutions use encapsulation plus plasma exposure, end-bonded contacts, or lateral epitaxy from 3D seeds or graphene, 1T′-MoTe₂ and VS₂. Dangling-bond overlap narrows the barrier and enables lateral injection, reducing interlayer resistance and crowding [84]. SF₆/O₂-defined Au–MoS₂ edges reached **432 cm² V⁻¹ s⁻¹** mobility and **Ion/Ioff >10⁸** at room temperature; Rc was not given [53]. MoS₂ can underperform graphene when transfer length limits injection [53].

**Evidence boundary.** Sc–multilayer MoS₂ (2013) has Rc/method unreported here; alloyed synthetic-monolayer MoS₂ reports <200 Ω·µm (2021), but not In/Au; Bi–MoS₂ is linked to 123 Ω·µm; the 2021 Sb record only names enhanced thermal stability [85]. CVD-grown, phase-engineered and intercalation-induced metallic-2D contacts remain solution families, not a separately justified fourth pathway [85]. Post-cutoff simulations (discovery-only) give 64 Ω·µm for Sc–hBN–MoS₂ at LC=40 nm and 50/40 Ω·µm for WS₂–YBi/LaBi at NSD=3×10¹³ cm⁻² [365,366].

By 2022, 3D top deposition caused defects, Fermi-level pinning and vdW barriers; PtTe₂–MoS₂ edge FETs achieved Rc 168±127 kΩ·µm (TLM) and 18 kΩ·µm minimum (Y-function), but scaling/reproducibility remained difficult [87].

Top/interface engineering is pathway 1 (metals, transfer, interlayers). Metallic-2D contacts are pathway 3’s material-state family—not a fourth: CVD 2D metals, patterned 2H→1T/1T′ conversion (n-BuLi, laser, Ar plasma), and Co/Cu intercalation. van der Waals interfaces suppress MIGS/FLP and Schottky barriers; in-plane contacts narrow tunnelling. Pre-2023 examples: VS2/MoS2, Rc 520 versus 8640 Ω·µm at Vg=50 V; WTe2/WSe2, ΦSB 70 versus 126 meV; NbTe2/WSe2, 2.68 µA/µm at VDS=1.5 V [88]. CVD risks high-temperature defects and poor repeatability; 1T can revert above 100 °C; intercalation is material-limited and interfaces undercharacterized [88].

Edge/1D engineering is pathway 2: covalent edge injection removes the vdW gap, MIGS/FLP and crowding [68]. Plasma/RIE, Ar+ cleaning and tilted Ti/Au are variants; Cl2-pit MoS2 reached ~1 kΩ·µm, while Ti-edge 1L-MoS2 gave RcW 27.8/11.7/8.3 kΩ·µm at VDS=1/2/3 V [373,375]. Pd/Mo-MoS2 edge contacts gave pinning 0.98 and mobility 330 cm²V⁻¹s⁻¹ at 300 K [58]. Oxidation, edge damage, anisotropy and specialist in-situ equipment limit scale-up [375,290].

Metal/2D interface and electrode-structure engineering is a top-contact subfamily, not a fourth pathway: metal choice, deposition, transfer and interlayers modify injection [54]. Metal-induced barriers, defects and reaction products create MIGS/FLP and access resistance; clean interfaces, band alignment, depinning and low-damage deposition reduce \(R_c\) [54][57]. Cu doping/contact decoration in WS₂ FETs cut \(R_c\) 1–3 orders (August 2020) and raised mobility 5–7×, but no absolute \(R_c\) was reported [94]. Indium/MoS₂ vdW contacts were ohmic (2021); 2022 defect-free vdW contacts extended the variant [95]. Bi/MoS₂ reached 123 Ω·µm (6 December 2022); Sb evidence was DFT-only [95]. Sc/WSe₂ diodes (2019) yielded 0.34 eV electron SBH, but Sc was reactive/anneal-sensitive; scale-up remains difficult [54][57].

Third pathway: 2012 NO2-doped monolayer WSe2 raised ON-current >1000× by narrowing Pd–WSe2 barriers, but desorbed in air [98]. 2019 transfer reduces pinning [52]; 2022 MoS2/Ni–Au FETs with 1–2 h-BN layers cut Rc 5.1→1.8 kΩ·µm, while thicker layers add tunnelling resistance [65]. Metallic-2D contacts (2020): area-dependent direct/FN tunnelling [96]

Metal/2D interface engineering is a top-contact branch: Ag deposition, transfer and AlOx insertion address pinning; transferred MoS₂/Ag yielded 0.45 Ω·cm and 12.8 meV in 2022 [100].

Top-contact and metal/interface engineering lowers Rc by tuning interface energy levels to reduce the Schottky barrier and, when localized at the contact, using doping to narrow it; clean interfaces reduce gap-state, MIGS and Fermi-level-pinning effects, while a van der Waals gap still adds a tunnelling barrier [97][71][77][86]. Energetic 3D deposition instead creates traps and gap states that raise the barrier and Rc; a reported interfacial defect density is ∼1.13 × 10 13 eV −1 cm −2, so defects, contamination and Rc-extraction assumptions must be separated from band-alignment, pinning, doping and tunnelling explanations [87][85].

Edge or one-dimensional contact engineering lowers Rc by exposing active edge states: the smaller metal–2D separation and stronger orbital hybridization and covalency give direct in-plane injection, narrower tunnelling barriers, Fermi-level depinning and more uniform injection without current crowding [84][67][73][89]. A reported comparison gives 7.5 kΩ μm for an edge contact versus 211 kΩ μm for a top contact; however, narrow edge areas can still produce current crowding, and two-step processing can introduce phase discontinuity, oxide impurities and vacancies [66][63].

The best-supported third pathway is contact-region electronic/material-state engineering. It is defined by a local change in the channel/contact region: phase engineering supplies a metallic 1T-MoS2 injection region, while contact doping narrows the Schottky barrier, lowering Rc by changing the carrier-injection state rather than only the external metal or contact geometry [71][53][84].

Metal/2D interface and electrode-structure engineering is a subfamily within contact engineering, not a separate top-level pathway. An inserted 2D or interfacial layer changes separation, band alignment and interface states to weaken Fermi-level pinning and lower the Schottky barrier; it is assigned to the top/interface pathway unless the dominant operation is edge formation or local phase/doping [71][64][61].

Metallic 2D-material contacts are a solution family under contact engineering, not a top-level pathway: the roster spans 2D top and edge contacts, CVD-grown metallic 2D contacts, phase-engineered metallic phases and intercalation-induced metallic states. Their primary assignment follows geometry or local state change, while their attraction is a van der Waals, Fermi-level-pinning-free interface with fewer lattice defects [84][88].

Contact-region chemical, electronic or resistance-state modification is best treated as a specialized solution family within the third pathway: chemical/contact doping changes carrier concentration and interface band bending to narrow the Schottky barrier and increase injection, while phase or electronic pretreatment modifies the local contact state [51][79][99][93]. The WSe2/NO2 example is within the 2D-channel scope, but NO2 gradually desorbs from WSe2 under ambient conditions, so permanence is limited and the supplied evidence does not support a universal Rc claim [98].

For the pre-cutoff scope, this overview precedes solution comparison and evidence audit and adopts exactly three mutually intelligible pathways: top-contact/metal-interface engineering for band alignment, interface states, doping and van der Waals tunnelling; edge/one-dimensional engineering for exposed-edge hybridization and covalent in-plane injection; and contact-region electronic/material-state engineering for local carrier-density or phase changes [64][71][84][89][59]. The ownership rule assigns specific-metal choices such as Sc, In/Au, Bi and Sb, UHV or transferred/laminated top contacts and interlayers to the first branch; exposed-edge etching to the second; and doping, 2H-to-1T phase engineering and intercalation to the third, while CVD metallic 2D contacts remain a cross-boundary solution family and incompletely evidenced candidates remain provisional [55][71][69][91][70][59][88].

The comparison table labels hBN/TMDC edge-contact preparation—etching to expose the edge, Ar+ cleaning and metal deposition—as the edge/one-dimensional category and records its ∼100 Ω⋅μm example, while keeping geometry, interface chemistry and process separate [84][90][92]. Metal/2D interface and electrode-structure engineering is a subfamily row covering van der Waals integration and inserted interfacial layers; a pre-cutoff monolayer WSe2 FET is explicitly in scope and a 4-bar FET reports less than ∼600 Ω·µm, while roughness, high cost/manual transfer and limited throughput constrain scaling [64][61][50][62][60][56].

Metal/2D interface and electrode-structure engineering remains a subfamily rather than a separate top-level route: its van der Waals and interlayer variants tune interface states and Fermi-level pinning, but transfer and integration demand low roughness and costly manual processing, limiting scale-up [64][51][60][56]. Metallic 2D-material contacts form one solution family comprising CVD-grown metallic contacts, including MoS2, ReS2 and graphene, phase-engineered metallic phases and intercalation-induced states; oxide barriers can be inhomogeneous and wafer-scale reliable growth remains challenging, so material, mechanism, stability and scalability claims stay solution-specific [88][96][84].

## Pathway 1: Top-contact engineering

### Specific metals, alloys, and semimetals

**Top contacts offer several distinct solutions:** Sc represents low-work-function selection; In-based contacts combine favorable injection with gentle interface formation; alloys add thermal robustness; and Bi/Sb exploit semimetal electronic structure. Their comparison shows why electrode identity and fabrication conditions must be considered together.

| Technical Pathway | Solution Name | Core Mechanism | Representative Results (Device and Performance) | Main Challenges or Limitations |
|---|---|---|---|---|
| Top Contact Engineering – Using Specific Metals | Sc contacts | Low work function lowers the electron Schottky barrier; residual Fermi-level pinning remains | Sc/10-nm MoS₂ with 15-nm Al₂O₃: effective mobility 700 cm²·V⁻¹·s⁻¹ at room temperature; barrier ≈30 meV, 2013. [11] | Work-function selection alone does not remove pinning |
| Top Contact Engineering – Using Low-Melting Alloys | In/Au alloy | Favorable electron injection and alloy-controlled interface formation; Au improves thermal robustness | Monolayer MoS₂: minimum \(R_c=190\) Ω·µm in a 720-transistor contact comparison, IEDM 2021. [2] | Alloy composition and thermal processing must be controlled |
| Top Contact Engineering – Using Low-Melting Alloys | Sn/Au alloy | Low-work-function component improves injection; alloying stabilizes the electrode | Monolayer MoS₂: minimum \(R_c=270\) Ω·µm; alloy approach tolerated approximately 450 °C processing, IEDM 2021. [2] | Thermal performance depends on the alloy, not bare Sn |
| Top Contact Engineering – Clean Deposited Interfaces | Annealed In/Au stack | Gentle In deposition and an atomically sharp interface limit chemical disorder; annealing forms an In–Au solid solution | MoS₂ with 10/100-nm In/Au: \(R_c=3,000\pm300\) Ω·µm, monolayer; \(800\pm200\) Ω·µm, few-layer; 200 °C anneal, 2019. [12] | Interface and alloy formation depend on deposition and annealing |
| Top Contact Engineering – Low-Thermal-Energy Deposition | Substrate-cooled In evaporation | Preserves a clean interface; field emission and conduction-band-edge hybridization support ohmic-like injection | In/MoS₂: cryogenic \(R_c\approx600\) Ω·µm, few-layer, and ≈1,000 Ω·µm, monolayer; transport examined over 2.4–300 K. [13] | Reproducible behavior required substrate-holder cooling near 100 K |
| Top Contact Engineering – Using Semimetal Electrodes | Bi contacts | Low density of states near the relevant Fermi energy suppresses MIGS; degenerate interface states enable ohmic injection | Bi/monolayer MoS₂: \(R_c=123\) Ω·µm at \(n=1.5\times10^{13}\) cm⁻²; zero extracted barrier; \(I_{\mathrm{on}}/W=1,135\) µA/µm, 2021. [1] | Defect sensitivity, poor hole injection, and limited thermal robustness |
| Top Contact Engineering – Using Semimetal Electrodes | Sb contacts | Semimetal electronic structure suppresses MIGS and supports near-zero-barrier injection | Sb/monolayer MoS₂: \(R_c=660\) Ω·µm; current >600 µA/µm at \(V_{DS}=1\) V and >1,000 µA/µm at 2 V, 2021. [14] | Thermal endurance improves over Bi, but annealing still reduces performance |

**Sc demonstrates both benefit and boundary:** Das and colleagues obtained a small electron barrier and high effective mobility using Sc contacts, a 10-nm MoS₂ flake, and an Al₂O₃ overlayer. The result belongs to the combined contact-and-device design; the 700 cm²·V⁻¹·s⁻¹ value should not be attributed to the metal independently of semiconductor thickness and dielectric environment. [15]

**The barrier responds only partially:** temperature-dependent experiments gave approximately 230, 150, 50, and 30 meV for Pt, Ni, Ti, and Sc contacts, respectively. This supports selecting a favorable metal, while the comparatively restricted barrier variation shows the continuing influence of pinning near the MoS₂ conduction band. [11]

| Contact metal on MoS₂ | Extracted Schottky-barrier height |
|---|---:|
| Pt | ≈230 meV |
| Ni | ≈150 meV |
| Ti | ≈50 meV |
| Sc | ≈30 meV |

**Orbital coupling adds another criterion:** Liu and colleagues’ 2013 WSe₂ experiments found that Al could form a high-resistance Schottky contact despite its low work function. Their calculations compared an approximately 0.16 eV tunneling barrier for Ag–WSe₂ with 0.6 eV for Al–WSe₂, emphasizing interface orbital overlap as well as energy alignment. Thus, selecting the lowest-work-function metal is not a general recipe for the lowest \(R_c\). [16]

**Indium addresses interface formation too:** its significance is not limited to work function. Wang and colleagues’ 2019 study used electron microscopy to identify an atomically sharp In/Au–MoS₂ interface without detectable chemical interaction after a 200 °C anneal. The In and Au layers formed a solid solution while preserving a van der Waals-type boundary to the semiconductor. [12]

**The In/Au implementations are distinct:** the 2019 capped stack, the cooled-In experiment, and the 2021 alloy study should be understood as separate contact recipes. Their differences encompass layer number, deposition energy, substrate temperature, alloy formation, and measurement temperature. The 190 Ω·µm alloy result consequently supports a specific implementation, rather than a resistance value intrinsic to every In/Au electrode.

**Alloying changes the thermal trade-off:** Kumar and colleagues combined a low-work-function, low-melting component with a stable noble metal and reported approximately 450 °C tolerance. Their statistical comparison covered 720 transistors across contact recipes, giving the alloy route useful evidence beyond a single exceptional device. The thermal conclusion concerns the engineered alloy system, not the melting point of its low-melting constituent. [2]

**Clean interfaces need useful coupling:** the cooled-In study also prevents an overly simple “remove every gap state” interpretation. Its transport and calculations associated ohmic-like behavior with field emission and conduction-band-edge hybridization. Harmful localized states that pin or trap carriers must be distinguished from hybridized conducting states that assist injection. [13]

### Bi versus Sb: electrical performance and thermal endurance

**Bi directly targets interface electronic states:** Shen and colleagues showed that its semimetallic electronic structure can sufficiently suppress MIGS for degenerate states to form in a monolayer semiconductor. For MoS₂, the reported interface reached a zero extracted Schottky-barrier height and 123 Ω·µm contact resistance. This is a more specific mechanism than simply substituting one conventional metal work function for another. [1]

**Crystal defects can defeat the benefit:** the Bi study’s defect analysis showed that sulfur-vacancy states can pin the Fermi level within the gap. Suppressing metal-induced states therefore does not eliminate the consequences of semiconductor defects. The practical implication is that electrode engineering and high-quality channel growth are complementary requirements, not interchangeable remedies. [1]

**Bi favors electron injection:** Bi-contacted WS₂ and WSe₂ devices were also reported as n-type, with on/off ratios above \(10^7\). Its favorable electron-contact behavior should therefore not be interpreted as a general solution for hole injection into the same materials. The 2022 Frontiers of Physics synthesis explicitly identifies Bi’s low work function as a limitation for lowering hole barriers. [1][7]

**Sb trades resistance for thermal margin:** Chou and colleagues measured approximately 660 Ω·µm for Sb/monolayer MoS₂ and high short-channel on-current. More importantly for integration, Sb-contacted devices remained operational after 400 °C annealing. Their reported performance retention was 80% after 300 °C and 64% after 400 °C treatment. [14]

**Melting point explains only part:** the same study compared bulk melting points of 630.6 °C for Sb, 271.5 °C for Bi, and 231.9 °C for Sn. Those values motivate the choice of Sb, but the device annealing experiment provides the stronger integration evidence: thin-film morphology, interfaces, and alloying can change before a bulk melting transition is reached. [14]

**The choice follows the process:** Bi is compelling for low-resistance n-type injection when semiconductor quality and subsequent processing preserve the interface. Sb becomes more attractive when a contact must survive processing near 400 °C. The Sb–Bi alloy concept discussed in the 2021 work was a modeling prospect, distinct from its measured Sb-device results. [14]

### Transferred electrodes, optimized deposition, and conducting 2D contacts

**Interface preservation extends metal choice:** transferred electrodes and carefully controlled evaporation can reduce deposition-induced disorder and make work function useful again. These routes are especially important for p-type contacts, where ordinary deposition can prevent a high-work-function electrode from delivering its intended band alignment.

| Technical Pathway | Solution Name | Core Mechanism | Representative Results (Device and Performance) | Main Challenges or Limitations |
|---|---|---|---|---|
| Top Contact Engineering – Clean Electrode Transfer | Transferred Ag electrodes | Clean lamination reduces chemical disorder and weakens Fermi-level pinning | Few-layer MoS₂/Ag: \(R_c\approx20,000\) Ω·µm; electron mobility ≈260 cm²·V⁻¹·s⁻¹ in the 2022 compilation. [3] | Transfer alignment, contamination control, and residual tunneling separation |
| Top Contact Engineering – Clean Electrode Transfer | Transferred Pt electrodes | Depinning permits high-work-function Pt to support hole injection | Few-layer MoS₂/Pt: \(R_c\approx67,000\) Ω·µm; hole mobility ≈175 cm²·V⁻¹·s⁻¹ in the 2022 compilation. [3] | Clean transfer does not guarantee minimum resistance; large-substrate assembly is difficult |
| Top Contact Engineering – Optimized High-Work-Function Deposition | Pd/MoS₂ and Pt/WSe₂ evaporation | Optimized deposition preserves near-ideal interfaces and enables Fermi-level depinning | Single-/few-layer MoS₂ and WSe₂ p-FETs: study-level \(R_c=3,300\) Ω·µm, mobility ≈190 cm²·V⁻¹·s⁻¹ at room temperature, 2022. [17] | Radiative heating, metal-specific reactions, and staged cooling |
| Top Contact Engineering – Ultra-High-Vacuum Deposition | UHV Au contacts | Cleaner deposition reduces contamination-related injection losses | Au/MoS₂: \(R_c\approx740\) Ω·µm for the UHV example tabulated in 2022. [3] | Vacuum cleanliness and deposition conditions become critical process variables |
| Top Contact Engineering – Conducting 2D Electrodes | Nb-doped WSe₂ electrodes | Degenerately doped 2D electrodes form low-resistance 2D/2D hole contacts | WSe₂ with Nb-doped WSe₂ contacts: \(R_c\approx300\) Ω·µm; mobility ≈220 cm²·V⁻¹·s⁻¹ in the 2022 compilation. [3] | Doped-electrode preparation, clean assembly, and spatial integration |

**Transfer provides strong depinning evidence:** the transferred-metal devices summarized in Frontiers of Physics had \(S\approx0.96\), compared with approximately 0.09 for evaporated-metal controls. This is a particularly clear distinction between restoring barrier tunability and merely observing increased current. The accompanying Ag and Pt mobility results demonstrate electron and hole operation in few-layer MoS₂. [7]

**Depinning and low resistance remain separate:** the transferred Ag/Pt examples achieved useful carrier control while retaining larger \(R_c\) than several other implementations. A clean interface can remove one bottleneck while leaving tunneling separation, band alignment, or transmission as another. Transfer is therefore particularly attractive when preserving a high-quality channel or selecting carrier polarity is important, rather than solely chasing the smallest contact-resistance number.

**Deposition rate has competing effects:** Wang and colleagues’ 2022 study showed severe Au/MoS₂ interface damage after a slow, 0.1 Å/s deposition that required more than eight minutes for 50 Å. Faster deposition at 2 Å/s, divided into stages with cooling, preserved an ultraclean interface. A slower flux may reduce some impact-related effects while increasing total radiative heating; “gentler deposition” must therefore describe the full thermal and kinetic exposure. [17]

**Metal–semiconductor chemistry remains specific:** optimized Pd contacts supported improved hole injection into MoS₂, whereas Pt was advantageous for WSe₂. The same study detected PdSe₂ formation at Pd–WSe₂ interfaces and poor p-type characteristics when Pt/WSe₂ deposition conditions were not optimized. A high work function is useful only when the actual interface preserves the intended electronic structure. [17]

**Conducting 2D electrodes offer compatibility:** Liu and colleagues’ calculations placed representative stacked 2D-metal/semiconductor separations at approximately 3–4 Å and found weak pinning because MIGS in the semiconductor were suppressed. Their analysis also identified high-work-function NbS₂ as a promising hole electrode. These theoretical results explain the attraction of layered electrodes, while their measured device performance must still be evaluated separately. [10]

**Top-contact takeaway:** electrode selection works best when combined with control of deposition damage, electronic coupling, and the complete thermal history; neither work function nor interface cleanliness alone determines \(R_c\).

**Additional documented evidence**

**Core principle.** Top contacts can reduce injection resistance by lowering the Schottky barrier, narrowing or eliminating the tunnel barrier, suppressing metal-induced or defect-induced gap states, reducing Fermi-level pinning, and improving orbital overlap or band alignment. Calculations show that strong metal–2D orbital overlap can metallize the semiconductor beneath the electrode and remove the local tunnel barrier, although the remaining Schottky barrier may still limit injection [35]. Metal work function alone is therefore insufficient; contact structure, interface bonding, charge transfer, and defect density also matter [32]. For Bi, the near-zero density of states near the Fermi level suppresses MIGS and can produce near-ohmic injection [39].

Representative device evidence is heterogeneous. In 2021, monolayer MoS₂ transistors with In/Au alloy contacts reportedly reached \(190\ \Omega\cdot\mu\mathrm{m}\) across a 720-transistor study, with approximately \(450^\circ\mathrm{C}\) temperature tolerance [37]. A 2016 ReSe₂ FET study reported up to three orders of magnitude contact-resistance improvement after UHV annealing and an average post-treatment contact value of \(750\ \Omega\cdot\mathrm{cm}\), but did not supply a width-normalized \(R_\mathrm{c}\) [38]. CVD-grown monolayer MoS₂ with inkjet-printed Ag top contacts was demonstrated in 2016; contact properties were evaluated by the Y-function method, but the retained evidence does not report a numerical \(R_\mathrm{c}\) [36]. A top-gated monolayer MoS₂ FET with gold source/drain leads reported \(I_\mathrm{ON}/I_\mathrm{OFF}=10^8\), room-temperature mobility above \(200\ \mathrm{cm^2\,V^{-1}\,s^{-1}}\), and a subthreshold swing of \(74\ \mathrm{mV\,dec^{-1}}\), but no contact-resistance value [34].

**Additional documented evidence**

**Specific-metal and semimetal top contacts**

- **Sb:** A pre-2023 primary lead is the 2021 IEDM study *Antimony Semimetal Contact with Enhanced Thermal Stability for High Performance 2D Electronics* [122]. The historical evidence supports Sb as the higher-temperature-resistant alternative to Bi and associates it with near-zero-barrier ohmic injection [149]. A later secondary summary reports Sb(01̄12)/MoS₂ band hybridization, degenerately doped MoS₂, a \(20\ \mathrm{nm}\) channel, and \(R_\mathrm{c}<100\ \Omega\cdot\mu\mathrm{m}\), but that summary is discovery-only for this cutoff and cannot substitute for the pre-2023 primary result [67]. Sb therefore has a stronger thermal-stability rationale than Bi, while its exact historical \(R_\mathrm{c}\) and extraction conditions remain to be verified from the primary study.

Related semimetal variants broaden the family: a later summary reports NbP topological-semimetal contacts on sub-\(2\ \mathrm{nm}\) WS₂ with \(5.8\ \mu\mathrm{A}/\mu\mathrm{m}\) hole current; this is a current-density result, not \(R_\mathrm{c}\), and is not evidence for the named Sc/In/Au/Bi/Sb rows [67]. Similarly, theoretical metallic-TMD contacts predict approximately \(1\ \mathrm{mA}/\mu\mathrm{m}\) for a scaled 1T′–2H MoTe₂ device, \(80\ \mathrm{mV/dec}\) subthreshold swing, and \(I_\mathrm{on}/I_\mathrm{off}\approx10^7\) for an Ohmic 1T–2H MoS₂ device; these are simulated alternative metrics, not selected-metal measurements [40].

Specific-metal contacts: overlap/charge transfer removes tunnel barriers; 2H→1T′/1T″ can remove Schottky barriers [35]. Sc–MoSe2/WSe2 DFT; In/Au n/r. 2021 Bi/MoS2=123 Ω·µm (Bi-unstable,271°C); Sb/MoS2=42 Ω·µm, discovery-only [101].

Bi is demonstrated: Bi/monolayer MoS₂, published 12 May 2021, achieved Rc = 123 Ω·µm and on-state current density = 1,135 µA/µm; Bi/WS₂ and Bi/WSe₂ FETs reached room-temperature I_ON/I_OFF >10⁷ [172]. Suppressed MIGS, spontaneous degenerate TMD states and zero Schottky-barrier height explain ohmic injection; sulfur-vacancy pinning makes low-defect TMD necessary [172]. Sb evidence is post-cutoff: 5 April 2023 theory predicts weak-metalization SMIGSs and lower tunneling-specific resistivity than Bi [117]; a 27 July 2023 dual-gate study attributes lower Rc to weak FLP and top-gate modulation of pseudo-junction resistance, with TCAD support, but gives no numeric Rc here [118]. Neither is final 2022 evidence. Later discovery-only evidence flags low-melting/diffusive metals as BEOL reliability/stability risks and transfer damage, polymer/metal contamination and adhesion problems [76,297].

Top contacts use the interface route: deposition damage/diffusion/bonding create DIGS, FLP and a Schottky barrier; Bi suppresses MIGS and Sb forms an ohmic near-zero-barrier contact [120][122]. The later review [119] (lead only) identifies Sc/MoS₂ and In/Au–MoS₂/WS₂/WSe₂; it reports lower In/Au damage but no Sc/In-Au Rc/method. Bi/1L-MoS₂: ≈123 Ω·µm (2022; conditions/method unreported) [43]; Sb/1L-MoS₂: 0.66 kΩ·µm and >600/>1000 µA/µm at VDS=1/2 V (2021) [122]. Se-buffer vdW: 10-nm Se, 50-nm metal, 150°C removal; Au/WSe₂: 1.25 kΩ·µm, 155 cm²V⁻¹s⁻¹, on/off 106 [43]. Transfer printing: ~100% yield [43]; Ni/MoS₂ nanocavities show morphology matters [121]. vdW processing is complex; Bi melts at 271.5°C, Sb survives 400°C annealing [119][122].

Top metals Sc/In/Bi/Sb: FLP→Ohmic [82–84]; 2022 Sb-group Rc<1kΩ[102]; Bi/MoS₂ 1.53kΩ·µm 4pt yr?; In/MoS₂ 480Ω·µm 4pt yr?[103]

Specific-metal top contacts are a top/interface solution: Sc, In/Au, Bi and Sb. No pre-2023 Sc/In-Au record is supported here; a 2021 Bi-semimetal lead lacks channel, stack, Rc and extraction details [104]. SWCNT/MoS2, published 7 Jan 2023 and discovery-only, used LTLM because 4PP/TLM are inapplicable for short contacts; it reported 10−6 Ω·cm² and 50 kΩ·µm Rc, rising below transfer length [104]. Clean vdW interfaces, suppressed MIGS/FLP and gate-tunable work function/SBH provide context [104]. Post-cutoff Sb/Au-contacted DG MoS2 showed ~0 meV SBH, weak FLP/suppressed MIGS and Sb-induced n+–n doping; VTG lowered the barrier [146]. 4PP measured 2Rc (not per-contact) = 63→40 kΩ·µm (VBG=0; VTG=0→12 V; ~30%); Ion≈8 µA/µm is separate from Rc and Ion/Ioff≈10^7 [146]. Air-gap/top-gate, EBL/dry transfer and longer Ljunc (higher Rjunc) are caveats; yield/scale unreported [146].

**Selected-metal/interface evidence**

- **Specific-metal top contacts (Sc, Ti, Ag, Pt, Ni, Au):** For MoS₂, charge transfer suppresses many-electron effects; bilayer interlayer coupling lowers SBH and improves electron injection [123]. No measured Rc/current-density or process limit is supplied [123].
- **Sc:** DFT+NEGF (2014-06-04) predicts Sc/MoSe₂ face/edge SBHs of ~0.25/>0.6 eV and ~0.003G₀ zero-bias face transmission [124]. These are calculated proxies, not Ω·µm Rc: no experimental Rc/current, extraction method, bias or temperature is given [124]. Sc is top/interface engineering; geometry and interface-localized states leave transport tunneling-dominated. The study reports ~0.5% lattice mismatch; strong binding need not ensure transparent injection, and oxidation, thermal, scale-up and reproducibility limits are unestablished [124].
- **In/Au:** The eligible record is In–WSe₂, not a demonstrated In/Au alloy: the 2013-03-25 back-gated n-type monolayer FET reports 210 µA/µm ON-current (alternative metric, not Rc) and d-orbital-assisted ohmic injection [125]; Rc extraction, geometry and limitations are unreported [125].
- **Bi/Sb:** A post-cutoff 2024 review attributes Bi–MoS₂ ohmic behavior to MIGS suppression and Sb–MoS₂ approach to the quantum limit to M–S hybridization; it gives no numerical Rc and cautions reactions, stability and integration [105]. Its 2024 Pd/alloy–WSe₂ result (~98 Ω·µm; 4.5 kΩ/sq; gate-independent) is ineligible [107]. The 2022 IEDM model covers MIGS/FLP, vdW-gap depinning and interface bonding; ~2 nm overlap is modeled optimal, but no selected-metal device is named [106].

2018 MoTe₂/MoOₓ/Pt/ITO FET: improved hole injection; μ≈5 cm²V⁻¹s⁻¹, ON/OFF≈10⁵, T=70%; Rc unreported [109]. Sc/In-Au/Bi/Sb unverified [108]; 2023 Al/Y discovery-only [126][147].

Sc-specific top contacts are intended to improve electron injection into n-type MoS₂ and reduce \(R_c\) through a low work function; however, Fermi-level pinning near the MoS₂ conduction-band edge can make different metals show similar resistance, so the supplied evidence reports no Sc-specific numerical \(R_c\), current density, or extraction method [110]. The source bibliography lists pre-2022 candidate studies but does not itself identify their selected-metal device metrics [110].

In/Au alloy contacts provide the strongest directly supported variant here: a 2021 IEDM study reported \(R_c=190\ \Omega\cdot\mu\text{m}\) for monolayer MoS₂, across a statistical study of 720 transistors [37]. The alloy combines a low-work-function, low-melting-point metal with a stable noble metal; the alloyed stacks tolerated approximately \(450^\circ\text{C}\), supporting back-end-process compatibility [37]. The same study reported \(270\ \Omega\cdot\mu\text{m}\) for Sn/Au contacts; the conference occurred on 11–16 December 2021 and the record was added to IEEE Xplore on 9 March 2022 [37]. The supplied record does not state the \(R_c\) extraction method, per-contact versus contact-pair definition, bias, temperature, geometry, or normalization, so the value is not fully comparable with records using different conventions [37].

A broader pre-2023 metal example is a 2017 Pd-contacted black-phosphorus FET: exposure to 5% H₂ in Ar formed Pd–H, increased the Pd work function, lowered the Schottky barrier, and changed the reported \(R_c\) from approximately \(7.10\) to \(1.05\ \Omega\cdot\text{mm}\), while doubling transconductance [112]. This is an analogous work-function-engineering result, not evidence for Sc, In/Au, Bi, or Sb; the source gives no extraction method, and its \(\Omega\cdot\text{mm}\) values should not be ranked directly against \(\Omega\cdot\mu\text{m}\) results [112]. A contextual 2D/2D comparator used highly p-doped WSe₂ contacts, a \(10.8\ \mu\text{m}\) channel and \(3.0\ \mu\text{m}\) width, \(>10^9\) room-temperature on/off ratio, and highly ohmic output, but reported no \(R_c\) [173].

A post-cutoff discovery source attributes \(123\ \Omega\cdot\mu\text{m}\) to a Bi/MoS₂ interface in 2018 and \(42\ \Omega\cdot\mu\text{m}\) to an Sb/MoS₂ interface in 2021, associating both with low-DOS suppression of MIGS and n-type ohmic injection [128]. Because that page is post-2022 and omits device architecture, extraction method, and conditions, these are discovery leads rather than final historical records. A 2022 DFT/NEGF/Landauer study modeled MIGS, vdW-gap depinning, interface scattering, and carrier transport, finding modeled hybrid contacts optimal at approximately 2 nm metal–2D overlap; it supplied no selected-metal measurement [111].

Top contacts: 3D-metal traps/MIGS pin EF and raise SBH; 2D metals may avoid pinning, but vdW tunnelling limits injection [86]. 2023 CVD-MoS2/Ni TLM/CER: Rc lower at 300K vs 80K and gate-dependent; Rce gate-independent [113]. Post-cutoff sims: WS2–YBi/LaBi Rc=50/40 Ω·µm at 3×10^13 cm−2; Sc/In-Au/Bi/Sb; transfer/interlayer evidence unresolved [86].

Sc is a top-contact metal/interface solution: mild WSe₂ pre-oxidation limits Sc–WSe₂ reactions and yields the lowest electron SBH; Sc–Se intermetallics, metallic W, oxygen-deficient ScₓOᵧ gap states, and residue cleaning confound attribution [163]. Pre-2023 Sc-FET examples used multilayer MoS₂ (2013), black phosphorus (2016), and WSe₂ (2019). The WSe₂ FET used 20-nm Sc/50-nm Pd/100-nm Au, UHV deposition, and air/RT testing; it reported SS 109 mV dec⁻¹, ION/IOFF ~10⁶, and modeled SBH 0.4–0.45 eV—not Rc; Rc extraction/current density were unreported [163]. Oxidation, annealing, diffusion, and consumption of ≥1 WSe₂ layer at RT and ≥3 after 400 °C limit integration; yield/scale data are unreported [163].

Ag/Au/Cr/Cu/In/Mo/Ni/Ti contacts on CVD monolayer MoS₂ correlate lower work function with lower \(R_c\) via Schottky/lateral barriers [165]. Bi/Au-capped Bi suppresses MIGS by gap-state saturation, removing the barrier; TLM gives per-contact \(R_c=123\pm63\ \Omega\cdot\mu\text{m}\) (RT; \(n_{2D}=1.5\times10^{13}\ \text{cm}^{-2}\)), versus DFT 130 \(\Omega\cdot\mu\text{m}\) [129]. Defects restore pinning; CMOS-compatible evaporation reported; oxidation/scale unknown [129]. In/Au lowers \(R_c\) versus Au, but composition/\(R_c\) are unreported; In clustering creates process/thermal concerns [165]. Multilayer MoS₂–Bi is ohmic at 4.2/2.3/0.4 K; \(R_c\) unreported [174]. Sb: 42 \(\Omega\cdot\mu\text{m}\) and 1.23 mA/µm, published 11 Jan 2023—discovery-only [166].

Later: Bi/MoS₂~78 Ω·µm,15 K[56]; Sc/MoS₂(2013) Rc NR[55]

MoS2/Au–Cr Rc 35.2→5.2 kΩ via O-defect removal, 2020 [175].

2H-MoS₂/1T-MoS₂–Au (2014): Rc≈200 Ω·µm; 110 µA/µm [151].

Sc/MoS₂:12;Bi/MoS₂:0.12kΩ·µm@23/NR[133];RIL:1.53kΩ·µm[134].

Specific-metal contacts: In/Bi/Sb–MoS₂ FETs >10 μA/μm ON-current; Bi dopes MoS₂ degenerately [135]. Sc: low-Rc comparative only—no standalone record; ~10⁻⁹ Torr UHV and oxidation risk [167]. Cu/WS₂ cuts Rc 1–3 orders (Schottky→Ohmic) [94]. Pt/hBN–WSe₂ transfer data are post-cutoff [93].

Sc/MoS₂: 30 meV Schottky barrier (2021); Rc unreported [71].

Sc/MoS₂ 2013: ~30 meV SB; 700 cm²/V·s mobility; Rc NR [136]

Fermi pinning limits selected-metal contacts: Sc–MoS₂ interface resistance was 0.65 kΩ·µm, but overall Rc ≈5 kΩ·µm from semiconductor resistance [115]. The 2013 multilayer-MoS₂ Sc study gives no Rc, method, or conditions [138].

Sc: no standalone Rc; Au/MoS₂=740 Ω·µm (TLM, 300 K) [139]

Ti/MoS₂:O₂/Ti Rc−20×[140];TiSₓ>22:MIGS↓[116];1T/2H-MoS₂[141]

≤2022: Sc/MoS₂:low-SB,pinning[52];In/Au/MoS₂:vdW 3000±300/800±200Ωµm[142];Bi:123Ωµm,MIGS→ohmic;Sb:659/146Ωµm[52]

Pre-2023 Sc/MoS₂: ~30 meV barrier; Rc 0.65 kΩ·mm [92].

SWCNT/MoS₂: 50 kΩ·µm (LTLM); MIGS↓; post-2022 [143].

2019 MoS₂: Sc pins; InₓAuᵧ vdW; Rc unreported [171]

Sc/MoS₂ is identified, but no Sc-specific \(R_c\) is retained; low-work-function Sc oxidizes and degrades \(R_c\), so UHV matters [127]. In/Au alloy, Bi, and Sb have no eligible device/\(R_c\) record here; later citations to 2013 Sc/MoS₂ and 2021 semimetal work are leads only [145]. A 2026 Step-Eva report of Bi/In/Au contacts is post-cutoff and leaves channel, method, alloy, and Sb assignments unresolved [144].

Chemical doping is not n-BuLi or memristive forming: 2012 monolayer WSe₂/Pd–Au exposed to 0.05% NO₂/N₂ for 10 min showed >1000× \(I_\text{on}\) and 250 cm²/V·s mobility but no \(R_c\); the effect reverses in air [98]. Inserted-layer evidence is contextual: 2017 MIS simulations and an h-BN-gap MoS₂/p-Ge TFET (SS 31 mV/dec; \(V_{DD}=0.1\) V), not qualifying \(R_c\) records [130][34].

Sc/MoS₂(2013):Rc unreported[169];Bi/MoS₂≈123Ω·µm(2021)[114]

In/Au/MoS₂: 800 Ω·µm TLM (2021); Sc Rc unreported [148].

**Specific metals.** Sc: a 2013 *Nano Letters* record identifies multilayer MoS₂/Sc, but the extract lacks \(R_\mathrm{c}\), method, conditions, mechanism and limitations [85]. Post-cutoff DFT/NEGF predicts Sc–hBN–MoS₂ **64 Ω·µm** at \(L_\mathrm{c}=40\) nm (SBH 0; TBT 0.53 nm); distance-dependent MIGS suppression and Fermi-level depinning trade against increased TBT, so this is not a historical device result [85]. In/Au: the only lead is a 2021 “sub-200 Ω·µm alloyed contacts” result for synthetic monolayer MoS₂; composition and extraction remain unresolved [85]. Bi/MoS₂: the 2021 lead is later summarized as **123 Ω·µm** with carrier concentration **1.5 × 10¹³ cm⁻²**; low Fermi-level DOS and orbital resonance suppress MIGS [51][85]. Modeling gives **~4.5 kΩ·µm** at minimum spacing versus the cited 123 Ω·µm, implicating spacing, adsorbates, alignment and TBT [85]. Sb/MoS₂ is reported at **42 Ω·µm** with **\(I_\mathrm{on}/I_\mathrm{off}>10^8\)**, attributed to low-DOS/MIGS suppression and band overlap/vdW coupling; primary conditions are absent, although a 2021 IEDM title claims enhanced thermal stability [51][85].

Novel metals face stability, applicability, cost and process limits [51]. Laser/Ar 2H→1T conversion via chalcogen vacancies can lower \(R_\mathrm{c}\), but defects, scale-up and metastability remain concerns [51]. CVD depends on precursors, substrate, temperature and gas flow; control, repeatability and quality remain difficult [152]. WSe₂₋ₓTeₓ at 250 °C is 2H for Te<14%, 1T′ for Te>79%, with a 14–79% miscibility gap; this is not contact-FET evidence, and Bi/In/Sb may incorporate into chalcogenides rather than act as surfactants [154]. n-BuLi is a strong base (1.6/2.5 M in hexanes), water-reactive, inert-atmosphere dependent and pyrophoric; its 2D-FET contact use is not established here [153]. \(R_\mathrm{ds(on)}=R_\mathrm{Cds}+R_\mathrm{Css}+R_\mathrm{series}\), and contact values may be misestimated [51].

**Sc metal contacts (top-contact selection).** A 2012 multilayer-MoS₂ back-gated FET used 30-nm Sc/20-nm Ni source/drains and a 5-µm channel. Sc gave ΦSB = 30 meV (Ti 50, Ni 150, Pt 230 meV), 4.8 µA/µm at VDS = 1 V, and, with 10-nm MoS₂ plus 15-nm Al₂O₃, 240 µA/µm at n≈2.8×10¹² cm⁻² [176]. No Sc Rc or extraction/per-contact definition was reported; these are proxies. Low ΦM = 3.5 eV improves injection, but S≈0.1 and measured 30 meV versus theoretical −0.7 eV show pinning; tunnelling can mimic ohmic behavior [88][176]. Mobility was 184 cm²/(V·s) at 10 nm but <20 at 3 nm; contact masking and interlayer resistance are caveats, while Sc-specific oxidation, thermal, scale-up and reproducibility limits are unestablished [88][176].

**Scandium contacts and evidence gaps**

A 2019 WSe₂-transistor study used Sc contacts deposited in UHV at room temperature without post-metallization processing; it reported a 109 mV dec⁻¹ subthreshold slope and \(I_\mathrm{ON}/I_\mathrm{OFF}=10^6\), but the supplied span gives no \(R_c\) or extraction method [177]. Mild in-situ WSe₂ oxidation minimized Sc–WSe₂ reactions and lowered electron SBH; Sc-selenide intermetallic formation was linked to a larger SBH [177]. A 2013 citation records multilayer MoS₂/Sc transistors but gives no \(R_c\) or mechanism details [162].

Sc is extremely reactive, requiring stringent processing and producing metastable performance. Reducing anneals degraded \(I_\mathrm{ON}/I_\mathrm{OFF}\) by ~\(10^3\), increased subthreshold slope tenfold and SBH by 0.4–0.5 eV, converted 100% of deposited Sc to intermetallic/oxide, and consumed ≥1 WSe₂ layer at room temperature and ≥3 after 400 °C, requiring sacrificial layers [177].

Later computational work is discovery-only: no Sc or In/Au device is reported; Sb is merely screened among Pt/Ru/Mo/Bi/Sb, with no completed Sb result. It flags pinning, SBH, vdW tunnelling, doping, geometry, bias and extraction as confounders, and gives no transferred or inserted-layer device [156]. General 2022 assembly risks are thermal/chemical instability, transfer residue, thermal-budget damage, poor spatial control and poor large-scale reproducibility [162]. A post-cutoff 2H-MoS₂/1T-LiₓMoS₂ edge-memory result reports 10/100 ns, not \(R_c\), and remains discovery-only [157].

Sc:ScP-like 0-eV barrier;Sc/WSe₂ FET(2019,UHV):SS109 mV/dec,on/off10⁶,Rc NR;reactive/loss [178][179]. In/Au–MoS₂:sharp interface,Rc/limits NR [180]. Bi/Sb:FLP/MIGS↓(later),Bi low-melt/Sb EBE [181];Bi–MoS₂:0.123 kΩ·µm(post22 table)[159];Sb–MoS₂:42 Ω·µm/TLM,Ion1.23 mA/µm(2023 src)[158]. Transfer MoS₂/Ag:0.45 Ω·cm,SB12.8 meV [100]. Interlayers:FLP depin,result NR [161].

**Inserted layers and transferred contacts**

Inserted tunneling/interfacial layers belong to top-contact metal/interface engineering. A vdW gap or ultrathin barrier attenuates wave-function penetration and MIGS, reduces FLP, and enables tunneling or dipole-controlled Schottky-barrier lowering; variants include graphene, metallic 2D layers, MgO/TiO₂/Ta₂O₅/ZnO, h-BN, 2D-semiconductor interlayers, and thiols [84]. In MoS₂, graphene/Ag lowered SBH from 300 to 190 meV (2019); 2-nm ZnO gave ~6 × 10⁻⁶ Ω·cm² specific contact resistivity (2020); and one–two-layer h-BN in Ni-contacted MoS₂ lowered SBH from 158 to 31 meV and width-normalized Rc from 5.1 to 1.8 kΩ·µm at room temperature (2016; per-contact versus contact-pair status not stated), with 330 µA/µm output current [84]. Thickness trades pinning suppression against tunneling probability; oxide growth may be inhomogeneous, and deposition conditions can instead produce less-conductive TiₓSᵧ. Mechanical metal transfer can remove residues and interface states, but no quantitative Rc is supplied in the record [84].

**n-Butyllithium and Sc**

Sc’s low work function is intended to lower the electron Schottky barrier and Rc in n-type MoS2; a pre-2023 multilayer-MoS2 Sc study dates to 2013, and Sc–MoS2 evidence reports an approximately 30 meV barrier [110][138][92]. The alternative to check is interface chemistry rather than work function alone: Sc–WSe2 intermetallic/oxide formation and Fermi-level pinning can dominate, with annealing increasing the electron barrier by 0.4–0.5 eV [54][163].

rejected: no_entity; allowed numbers: 190 Ω·µm; 110 meV; allowed citations: [37][148][85][156]; allowed entities: In/Au alloy contact; Top-contact and metal/interface engineering; Specific-metal top contacts, including Sc, In/Au alloy, Bi semimetal, and Sb.

Bi’s near-zero Fermi-level density of states suppresses MIGS and saturates gap states, enabling ohmic injection; Bi on monolayer MoS2 reached 123 Ω·µm [52][129]. The alternative to check is TMD quality: sulfur-vacancy states can pin EF in the gap, while structural defects, contamination and alignment can confound Rc [129][39][85].

rejected: no_entity; allowed numbers: 2021; allowed citations: [164][137][95][173][85][156]; allowed entities: Sb semimetal contact; Top-contact and metal/interface engineering; Specific-metal top contacts, including Sc, In/Au alloy, Bi semimetal, and Sb.

rejected: no_entity; allowed numbers: none; allowed citations: [69][160][161][85][156]; allowed entities: Transferred or laminated metal/semiconductor contact; Top-contact and metal/interface engineering; Specific-metal top contacts, including Sc, In/Au alloy, Bi semimetal, and Sb.

rejected: no_entity; allowed numbers: none; allowed citations: [84][83][85]; allowed entities: Inserted tunneling or interfacial layer; Top-contact and metal/interface engineering; Specific-metal top contacts, including Sc, In/Au alloy, Bi semimetal, and Sb.

rejected: number_unsupported; allowed numbers: 5.2 k 10^3 Ω kΩ; 70 k 10^3 Ω kΩ; allowed citations: [150][97][132][182][131]; allowed entities: n-Butyllithium contact treatment; Contact-region chemical, electronic, or resistance-state modification; Specific-metal top contacts, including Sc, In/Au alloy, Bi semimetal, and Sb.

Conductive-filament formation creates the low-resistance state and rupture restores the high-resistance state [155]. The reported Au/Ti/MoTe2/Au/Ti device is a 2D MoTe2 memristor, not a 2D-FET contact-engineering device; contact-region forming is not reported, so it does not satisfy the requested 2D-FET scope [155][145][183].

Specific-metal top contacts are the material-selection family: Sc targets low-barrier electron injection, In/Au combines low-work-function In with stable Au, Bi suppresses MIGS, and Sb uses weak metalization/MIGS suppression; representative values include 190 Ω·µm for In/Au and 123 Ω·µm for Bi [110][37][52][164]. The rows should retain channel/contact materials, metric and evidence status, flag Sc reaction chemistry and TMD-defect dependence [54][129], and place pathway scope before solution rows and the comparison table, followed by the evidence audit and references.

Sc is the specific-metal n-type MoS2 row: its low work function lowers electron SBH, with approximately 30 meV reported and a 2013 multilayer-MoS2 study [110][138][92]. The table should label barrier/device evidence and Rc uncertainty [127], and flag oxidation, reaction-driven intermetallic/oxide states and thermal reproducibility; annealing can raise the electron SBH by 0.4–0.5 eV [54][163].

The specific-metal top-contact family comprises Sc, In/Au alloy, Bi semimetal and Sb [104]; the explicit causal evidence here is that Sc’s low work function is intended to improve electron injection into n-type MoS2 and lower Rc [110]. Family-level results include 740 Ω∙μm [139], ~98 Ω·µm; 4.5 kΩ/sq [107], and 123 Ω μm [52], but the evidence does not assign each metric to a named variant or provide complete device rows; a listed process/thermal constraint is 271.5°C [119], so these entries support a lowering direction rather than a universal ranking.

Sc contacts are intended to use a low work function to improve electron injection into n-type MoS2 and lower Rc [110]. The pre-cutoff Sc entry is dated 2013 [138], but no Sc-specific Rc or complete extraction/device conditions are supplied [127]; the available performance entries are 4.8 μA/μm and 240 μA/μm [176], while controlling intermetallic concentration and an oxygen-deficient ScxOy interlayer is proposed to reduce the electron barrier, whose listed values are 0.4–0.5 eV and ΦB = 150 meV [54][167].

In/Au alloying combines work-function engineering with a clean, weakly pinned interface and supports near-ohmic injection [148][180]. A representative monolayer MoS2 result is 190 Ω·µm with a 110 meV In/MoS2 barrier [37][148]; standard evaporation can form indium clusters rather than a smooth film, and the evidence does not provide a complete alloy-specific quantitative process record [165].

Bi semimetal contacts lower Rc by combining near-zero Fermi-level DOS with MIGS suppression and gap-state saturation, enabling weak-pinning/ohmic injection; sulfur/chalcogen vacancies can instead pin the Fermi level [129][39]. A 2021 Bi/MoS2 entry reports 123 ± 63 Ω µm and 450 μA μm−1, with an additional 10−9 Ωcm2 contact-resistivity value [52][129][39][95], while the main limitation is dependence on TMD quality and vacancy control [129].

Sb contacts are linked to lower Rc by weak metalization: semimetal-induced gap states extend below the TMDC conduction-band minimum and close the Schottky mismatch, while weak pinning suppresses MIGS and permits top-gate control of the pseudo-junction Rjun in a dual-gated MoS2 FET [164][170][146]. The pre-cutoff evidence is dated 2021 [95] and includes a 10−9 Ωcm2 entry [95], but a 530 Ω·μm result is dated 2023-05-05 [168][146] and is outside the requested cutoff; Sb-specific limitations are not reported in the supplied evidence [157].

rejected: citation_outside_operands; allowed numbers: 2013; 2021; 2022; 740 Ω∙μm; allowed citations: [114][52][40][43][124][125]; allowed entity: Specific-metal top contacts, including Sc, In/Au alloy, Bi semimetal, and Sb.

## Pathway 2: Edge-contact engineering

### Plasma-defined edges and hybrid graphene contacts

**Edge contacts have architectural advantages:** direct lateral injection can avoid the basal-plane tunneling geometry and reach multiple layers without first entering only the uppermost layer. The following examples separate direct metal–semiconductor edges from hybrid devices whose metal leads contact graphene edges.

| Technical Pathway | Solution Name | Core Mechanism | Representative Results (Device and Performance) | Main Challenges or Limitations |
|---|---|---|---|---|
| Edge Contact Engineering – Plasma Etching | Plasma-exposed graphene with Cr/Pd/Au | Strong metal–edge coupling replaces basal-plane tunneling injection | h-BN-encapsulated monolayer graphene; Cr/Pd/Au 1/15/60 nm: \(R_c\approx150\) Ω·µm at room temperature, 2013. [3] | Edge termination, etch damage, and transfer complexity |
| Edge Contact Engineering – Etching and In-Situ Cleaning | Jain-style Ti/MoS₂ edge contacts | Ar⁺ sputtering removes oxide and adsorbates immediately before metallization | Ti/monolayer MoS₂: \(R_c\approx50,000–70,000\) Ω·µm; mobility ≈30 cm²·V⁻¹·s⁻¹, 2019 example. [3] | Requires precise etching and integrated sputtering/deposition equipment |
| Edge Contact Engineering – High-Vacuum Metallization | Slowly deposited Cr/Au on exposed MoS₂ edges | Cleaner edge formation and controlled deposition improve lateral transmission | CVD monolayer MoS₂/Cr/Au: \(R_c=2,500\) Ω·µm; saturation current 730 µA/µm, reported by 2022. [3] | Edge cleanliness and metal-bond formation remain process-sensitive |
| Edge Contact Engineering – Plasma Etching and In/Au Metallization | CF₄/O₂ etching with In/Au contacts | Side-plane injection reaches multiple MoS₂ layers; annealing improves the junction | Six-layer MoS₂, 15/40-nm In/Au: \(R_c=4,070\) Ω·µm at \(V_G=60\) V; room-temperature mobility 32 cm²·V⁻¹·s⁻¹, 2021. [4] | Plasma processing, encapsulation, and annealing; residual Schottky/tunneling behavior |
| Edge Contact Engineering – Hybrid Graphene Electrodes | h-BN/graphene/MoS₂/h-BN assembly | Edge-contacted graphene provides conducting leads while encapsulation preserves the MoS₂ interface | Graphene-contacted MoS₂: \(R_c\approx2,000\) Ω·µm; mobility 40–120 cm²·V⁻¹·s⁻¹ at room temperature and up to 34,000 at low temperature. [3] | Multilayer dry transfer, alignment, and graphene–semiconductor junction control |
| Edge Contact Engineering – Plasma-Defined Hybrid Leads | CHF₃/O₂ ICP etching and Cr/Pd/Au leads | Metal contacts exposed graphene edges; graphene couples to encapsulated MoS₂ | Multilayer MoS₂ with graphene and 1/20/50-nm Cr/Pd/Au leads: mobility 33–151 cm²·V⁻¹·s⁻¹ across 12 devices; sustained current ≈500 µA, 2015. [18] | ICP etching, electron-beam patterning, dry assembly, and residue control |

**Edge geometry improves orbital access:** a basal-plane contact to a transition-metal dichalcogenide approaches the outer chalcogen surface, whereas an edge can provide stronger coupling to the states carrying in-plane current. Kang and colleagues’ calculations compared top and edge geometries through orbital overlap, tunneling barriers, and Schottky barriers, finding significant potential advantages for edge injection. [19]

**The tunneling barrier can shrink:** an earlier calculation gave approximately 0.31 eV for an Au–MoS₂ side, or top, contact and 0.14 eV for an end, or edge, contact. These are calculated interfacial barriers, not measured contact resistances, but they show the physical reason that geometry can improve transmission even without changing the metal. [20]

**Multilayer access is a separate benefit:** Conde-Rubio and colleagues explain that top-contact current must reach deeper MoS₂ layers through interlayer transport, whereas edge contacts can inject directly into the side planes of multiple layers. This advantage becomes important when an otherwise clean top contact underuses the conducting thickness. It does not require assuming that every edge is barrier-free. [21]

**Plasma exposure creates a chemical problem:** freshly exposed edges contain reactive atoms and can acquire oxides or adsorbates before metal deposition. Jain and colleagues improved edge preparation through in-situ Ar⁺ sputtering at a tilted angle immediately before metallization. The intervention addresses a specific sequence—etching, contamination, cleaning, bonding—rather than merely increasing edge area. [3]

**The In/Au experiment isolates useful geometry:** Le Thi and colleagues encapsulated six-layer MoS₂ in h-BN, used CF₄/O₂ etching, deposited 15/40-nm In/Au, and annealed at 150 °C in Ar for two hours. The 4,070 Ω·µm result at \(V_G=60\) V was approximately ten times below the comparable indium top-contact device. Mobility increased from 32 cm²·V⁻¹·s⁻¹ at room temperature to 40.7 cm²·V⁻¹·s⁻¹ at 77 K. [4]

**That improvement preserves a residual barrier:** the same device retained Schottky-contact and direct-tunneling characteristics. Its result supports more efficient injection through the edge, not the broader assertion that exposed-edge geometry automatically creates an ideal ohmic interface. The distinction matters when translating a favorable mobility or output curve into an actual contact-resistance target.

**Graphene hybrids contain two junctions:** in the Lee implementation, CHF₃/O₂ inductively coupled plasma, or ICP, exposed graphene edges for the Cr/Pd/Au leads. Graphene then coupled to MoS₂ within the layered stack. The approximately 150 Ω·µm graphene edge-contact benchmark and the MoS₂ hybrid-device results therefore describe different contact systems; the graphene value should not be assigned to the MoS₂ junction. [18][3]

**Encapsulation preserves channel transport:** h-BN separates the channel from adsorbates and processing residues while permitting electrical access through the stack edge. This explains why hybrid structures can deliver particularly high low-temperature mobility. It also explains their assembly burden: the contact is one part of a carefully aligned multilayer heterostructure, rather than a single added metal film. [3]

### Edge chemistry, yield, and scaling

**Strong bonding is not universally depinning:** the ideal edge has higher transmission, but real edge terminations can introduce their own pinning states. Choi and colleagues describe both experimentally depinned MoS₂ edges and strong termination-dependent pinning. Strong orbital overlap and MIGS suppression should therefore not be used as interchangeable explanations for every edge-contact result. [3]

**WSe₂ provides an important counterexample:** ex-situ plasma processing can form an inhomogeneous WOₓ region at WSe₂ edges. Its interaction with the metal can favor p-type behavior largely independently of the metal work function. This differs from a deliberately deposited, thickness-controlled depinning layer: uncontrolled edge oxidation changes the junction chemistry and can add substantial resistance. [3]

**Electrode mechanics also affects yield:** in Conde-Rubio and colleagues’ 29-device comparison, a 20-nm Cr layer generated stress-related cracks, metal leakage, and short circuits in some devices. Switching to Ti/Au improved fabrication yield but reduced device performance. This is a concrete example of why an electrically attractive contact stack can lose its advantage when mechanically integrated. [21]

**Annealing can improve the junction:** the same work used 250 °C treatment for three hours in N₂ and discussed atomic rearrangement and improved metal–MoS₂ bonding as mechanisms for reduced resistance and hysteresis. Annealing is consequently part of the contact recipe, but its usefulness must be reconciled with the stability of the metal, semiconductor edge, and encapsulation. [21]

**Contact-length scaling favors the edge:** the 2022 edge-contact review describes MoS₂ devices whose current was approximately independent of contact length between 20 and 80 nm. Top contacts, by contrast, depend on sufficient overlap relative to the current-transfer length. The architectural advantage of an edge is therefore not necessarily the smallest initial laboratory \(R_c\), but reduced sensitivity to shrinking lateral contact dimensions. [3]

### Grown lateral junctions

**Bottom-up growth offers another edge route:** instead of exposing and metallizing a reactive semiconductor edge, a conducting material can be grown laterally against it. This can create a cleaner junction, although it transfers the integration challenge to selective synthesis, registration, and growth-temperature compatibility.

| Technical Pathway | Solution Name | Core Mechanism | Representative Results (Device and Performance) | Main Challenges or Limitations |
|---|---|---|---|---|
| Edge Contact Engineering – CVD Lateral Heterostructures | VS₂–MoS₂ junction | Structurally compatible metallic VS₂ forms a conducting lateral interface and limits direct metallization damage | Monolayer MoS₂ with lateral VS₂: four-probe \(R_c\approx520\) Ω·µm versus ≈8,640 Ω·µm for Ni–MoS₂. [7] | Selective two-step growth and wafer-scale junction uniformity |
| Edge Contact Engineering – Lateral Graphene Growth | CVD graphene–MoS₂ stitching | Grown lateral connection replaces a transferred junction with an atomically connected interface | Graphene-contacted MoS₂: \(R_c\approx30,000\) Ω·µm and Schottky barrier ≈15 meV in the 2022 synthesis. [3] | Patterned-edge epitaxy and interface continuity; low barrier alone leaves substantial resistance |
| Edge Contact Engineering – End-Bonded Growth | Pd-alloy-seeded WSe₂ | WO₃₋ₓ/Pd/WO₃₋ₓ seeds promote WSe₂ growth with a covalently bonded conducting boundary | Monolayer WSe₂/Pd-alloy: \(R_c\approx16,300\) Ω·µm; mobility ≈90 cm²·V⁻¹·s⁻¹. [3] | High-temperature seed transformation and controlled end-bond formation |

**VS₂ provides a strong same-study contrast:** the reported 8,640-to-520 Ω·µm comparison corresponds to approximately 16.6-fold lower resistance, calculated as \(8,640/520\). A separate 2020 synthesis reports a barrier reduction from 163 to 30 meV and at least fourfold mobility improvement relative to Ni/Au contacts. These observations support the combination of compatible lateral bonding and reduced injection-barrier losses. [7][8]

**A low barrier remains insufficient:** the grown graphene–MoS₂ example combines an approximately 15 meV barrier with approximately 30,000 Ω·µm resistance. Its practical message is that barrier height does not determine conductance independently of available conducting states, coupling, junction continuity, and the remainder of the contact structure. This is particularly relevant when comparing a fitted barrier against a directly extracted \(R_c\).

**Growth shifts the integration burden:** lateral synthesis can avoid post-growth edge contamination, but the junction must form at the correct location with consistent stoichiometry and connectivity. The 2022 Frontiers review identifies controllable wafer-scale metallic/semiconducting 2D heterostructure synthesis as a central challenge. A successful isolated boundary and a uniform contact array are different engineering accomplishments. [7]

**Edge-contact takeaway:** edge engineering is particularly valuable for encapsulated, multilayer, and aggressively scaled devices, provided that edge chemistry, bonding, and fabrication yield preserve its geometric advantage.

**Additional documented evidence**

**Core principle.** Edge contacts expose the reactive sidewall of the 2D semiconductor and allow direct contact to multiple layers. This can bypass interlayer tunneling resistance, reduce the van der Waals gap, provide a more direct lateral injection path, and reduce current crowding compared with a basal-plane top contact [31][42]. A 2013 graphene demonstration established a one-dimensional interface between the edge of a 2D material and a 3D metal electrode [41].

A 2020 edge-contacted MoS₂ back-gate FET used dry etching and \(10\ \mathrm{nm}\) Ti/\(100\ \mathrm{nm}\) Au electrodes fabricated by sputtering and lift-off. Using a parallel-layer model and TLM, the study reported approximately \(7.27\ \mathrm{k\Omega\cdot\mu m}\) per-layer contact resistance; derived \(R_\mathrm{con}\) values were \(0.632\), \(0.511\), \(0.350\), and \(0.225\ \mathrm{k\Omega\cdot\mu m}\) for 11-, 14-, 23-, and 31-layer MoS₂ devices, respectively, on 10 December 2020 [31]. These values are model-derived and layer-normalized, so they should not be ranked directly against conventional per-contact \(R_\mathrm{c}\). The same study ranked fabrication difficulty as edge-contacted \(>\) sandwich-contacted \(>\) top-contacted [31]. Simulations of 1T–2H MoS₂ likewise found side contact superior to top contact for conductance, with most current transferring at the edge [40].

**Additional documented evidence**

**Edge preparation and one-dimensional injection**

By 2022, edge-contact engineering had two separable functions: etching or otherwise exposing and cleaning an edge, and using a one-dimensional edge interface to improve carrier injection. The latter can reduce the effective barrier width and transfer length, increase orbital coupling to the semiconductor, and reduce the influence of surface-interface states; plasma etching is therefore a preparation step, not by itself a proof of a lower intrinsic \(R_\mathrm{c}\). [87]

**Plasma etching for edge-contact preparation**

**Plasma-defined top–edge hybrid contacts were demonstrated in few-layer MoS₂ in 2020.** Nanoscale pits were etched only in the contact regions before Ti/Au metallization, so the exposed MoS₂ edges operated in parallel with the remaining top-contact paths. The reported device used a 10 s, 100% Cl₂ plasma at 25 °C, 40 mTorr and 45 sccm, with 50 W plasma power, 20 W chuck-bias power, and a nominal 6 nm Au-island mask. Exposed edge sites added carrier-injection paths to the top contact. The devices produced on-currents of hundreds of µA/µm, on/off ratios ≥10⁶, and \(R_\mathrm{c}W<10\) kΩ·µm; the best set reached approximately 1 kΩ·µm (approximately 1,000 Ω·µm). [193]

The most auditable result was obtained from transfer-length-method (TLM) structures. For a six-layer MoS₂ flake, the extracted width-normalized contact resistance was \(R_\mathrm{c}W=1.5\pm0.5\) kΩ·µm, or \(1,500\pm500\) Ω·µm, with little dependence on overdrive voltage from 7–24 V. The extraction used \(R_\mathrm{tot}W=2R_\mathrm{c}W+R_\mathrm{sh}L\), extrapolating the linear fit to \(L=0\) over channel lengths of 200–700 nm; measurements were made at room temperature, \(V_\mathrm{D}=0.1\) V, and \(1.5\times10^{-5}\) Torr, without intentional annealing. These results were reported in 2020 and are within the historical cutoff. [193]

The main limitations are process sensitivity and reproducibility. Ar and O₂ trials produced apparent “negative” etching, attributed to oxidation or MoOₓ formation, while Ar also lacked adequate selectivity against the Au mask. Cl₂ plasma caused Au agglomeration, reduced mask coverage by approximately 10–40%, and changed island size, connectivity, aspect ratio and orientation. The resulting edge density must be high within approximately one transfer length and preferably oriented perpendicular to current flow; the relevant transfer length could be as small as 30 nm. Exposure of the etched edge to air can also cause unintended oxidation, making in-situ etching immediately before metallization attractive. Thus, gas chemistry, mask morphology, feature size, alignment, edge orientation, plasma damage, doping and oxidation all need to be controlled before assigning the resistance reduction solely to edge geometry. [193]

**Conventional 3D-metal one-dimensional edge contacts**

**Conventional 3D-metal one-dimensional edge contacts belong to the edge-contact pathway.** Their core principle is direct coupling between the metal and active electronic states at the atomically thin edge, rather than injection across the broad surface of a top contact. A lateral metal–2D semiconductor junction can remove atomic discontinuities at the interface, shorten the carrier-injection path to a few-atom-thick region and reduce the effective transfer length from the tens-to-hundreds-of-nanometres scale associated with many vertical contacts to a few nanometres. The eligible pre-2023 literature roster includes plasma-made contacts reported in 2016, one-dimensional edge contacts to monolayer semiconductors and in-situ MoS₂ edge contacts reported in 2019, and related edge-contact carrier-injection studies. [87]

**vdW-gap-free one-dimensional edge contacts**

**A pre-2023 quantitative demonstration was the PtTe₂–MoS₂ lateral junction published on 22 August 2022.** The device used monolayer MoS₂ as the channel and metallic 2D PtTe₂ as the edge contact. TLM gave \(R_\mathrm{c}=168\pm127\) kΩ·µm, or \(168,000\pm127,000\) Ω·µm, at \(n_\mathrm{2D}\approx9\times10^{12}\) cm⁻²; the corresponding Ti/MoS₂ comparison was approximately \(4,285\pm1,959\) kΩ·µm. A Y-function extraction gave a minimum of approximately 18 kΩ·µm (18,000 Ω·µm) and an average of approximately \(113\pm60\) kΩ·µm. TLM and Y-function values should remain separately labeled because the source notes sensitivity to transfer length, channel thickness and extraction method. [87]

The principal limitations are fabrication and scale-up. Typical 2D materials remain thermally and chemically unstable; lithographic edge formation may require encapsulation or in-situ etching, and many studies had not demonstrated high yield or high device density. For 2D–2D variants, CVD can provide poor spatial control, thermal budgets near 700–800 °C can degrade the active layer, and graphene-based transfer can introduce lattice mismatch and polymer residue. Even for PtTe₂, large-area, stoichiometric metallic films, tellurium incorporation, environmental stability and precursor-mass-flux control remain difficult; excessive flux can produce randomly distributed multilayer MoS₂ rather than selective edge nucleation. Reproducible pure-edge patterns, channel-to-channel statistics and scalable TLM-compatible integration therefore remain unresolved. [87]

A 2019 hBN-encapsulated monolayer-MoS₂ FET combined reactive-ion etching, in-situ Ar⁺ sputtering and annealing for edge contacts, achieving >50 µA/µm at \(V_{DS}=3\) V; \(R_c\), metal and extraction method were not reported [198]. Contacting nearly all layers enables in-plane transport and possible covalent bonding, improving injection [198]. A 2022 MoS₂ photodetector used O₂/SF₆ plasma (100 W, 25/75%, 50 mTorr, 20 s) with Ti/Au and reached 18 MHz, but is contextual non-FET evidence [197]. In 2022 graphene/hBN stacks, edge \(\rho_c\approx10\) versus ≈230 Ω·µm² for surface contact; this is contact resistivity, not \(R_c\) [185]. General 1999–2008 etching sources flag ion damage, residue, anisotropy, defects, chamber matching and repeatability [186][187][188].

Plasma edge prep: radicals/ions remove material for in-plane edge injection; RIE adds bombardment, downstream etching shields wafers [199]. 2022 graphene-via: fluorination+plasma → edge/fluorinated-graphene electrodes in complementary 2D FETs; Rc/extraction not reported [190]. Metal-edge covalent bonding reduces pinning [195]. Discovery-only later records: MoS2/Ni-Au, Rc 1.25±0.46 kΩ·µm, 436 µA/µm@1 V; HfSe2/Hf2C, Rc 475 Ω·µm, Ion 920 µA/µm [195][189]. Caveats: residue, radiation damage, roughness, reproducibility [199][200].

**Plasma edge preparation.** 1L-MoS₂/Ti-Au FETs using SF₆+Ar RIE (20+20 sccm, 50 W, 100 mTorr) gave width-normalized RCW = 64.2 ± 9.6 kΩ·µm at |VDS| = 1 V and 46 ± 10 kΩ·µm at 2 V; CHF₃+O₂+Ar gave 73.5 ± 23.4 kΩ·µm. Eq. 4 ID–VGS fits; two-probe, RT air; date not stated in excerpt [90]. RIE exposes edges; Ar sputtering removes MoOx/adsorbates; anisotropy creates crevices, incomplete contact and variability, while 300 °C annealing promotes Ti–MoS₂ bonding [90]. **3D edge.** Ti-Au/1L-MoS₂ gave RCW = 27.8, 11.7, 8.3 kΩ·µm at VDS = 1, 2, 3 V; tunneling/barrier narrowing aid injection, but voids, edge states and alignment limit reproducibility [90]. This is 1D, not explicitly vdW-gap-free; gap-free Rc is unreported.

Plasma etching exposes a 2D edge for metallization; edge overlap narrows the Schottky barrier and promotes lateral injection [84]. In 2019, h-BN-encapsulated MoS₂ with RIE, tilted in-situ Ar⁺ sputtering/annealing reached >50 μA/μm (μ~30 cm²V⁻¹s⁻¹; SS~116 mV/dec); metal/Rc were unreported [68]. Damage/roughness and demanding in-situ equipment limit scale-up [68][84]. Conventional metal–MoS₂ edges use covalent injection, avoid the vdW gap/current crowding, and worked to Lc=20 nm in 2019; metal and Rc were unspecified [68]. Gap-free variants include graphene-edge/h-BN/WSe₂ (tunable barrier) and 1T′/2H-MoS₂ (75 Ω·μm access resistance in 2016, not Rc) [68].

2019 plasma edge preparation used CF₄/600-eV Ar etching plus in-situ Ni deposition on CVD MoS₂; reactive edges formed bonded interfaces, and TLM Rc≈31/30.5 kΩ·µm at Lc=30/80 nm (n₂D≈1.2×10¹³ cm⁻²; VDS=0.54 V) [78]. Ex-situ residue and sub-20-nm yield limit it [78]. In 2019, Pd/Au 3D-edge MoS₂ FETs showed Fermi-level depinning and yielded 330/432 cm² V⁻¹ s⁻¹ hole mobility at 300 K; Rc was unreported and pure-edge fabrication is hard to scale [192][88]. In 2022, monolayer MoS₂/PtTe₂ vdW-gap-free edge FETs gave Rc≈168±127 kΩ·µm (TLM) and ≈18 kΩ·µm minimum (Y-function); comparisons are conditional [162].

Pre-cutoff SF₆/O₂ plasma etching of h-BN/MoS₂ exposes a clean edge for direct metal coupling; stronger edge hybridization and a narrower injection barrier link the one-dimensional contact to lower Rc [53][67][84][91]. Check the damage alternative: residue removal or passivation can mimic a geometry benefit, while Ar preferentially sputters sulfur into sulfur-deficient MoₓSᵧ and plasma can oxidize or destabilize the edge [202][67].

Pre-cutoff framework: conventional 3D-metal one-dimensional edge contact is an Edge Contact Engineering/lateral metal–2D junction solution. Versus a top contact, shorter bonding distance, higher covalency and orbital overlap, and a narrower barrier favor in-plane injection and lower Rc, but a reported edge device still had Rc≈6 MΩ·µm; interface and barrier quality must therefore be separated from geometry [192][84][73][90][194][196][91].

Pre-cutoff framework: vdW-gap-free one-dimensional edge contact belongs to Edge Contact Engineering. Direct edge exposure injects into every MoS₂ layer through short bonds, strong overlap, and no vdW gap or lower tunnel barrier, so Rc is lower than for surface contacts [184][84][191]; a reported result is 130 Ω·µm [201]. A sputtered MoRe/hBN-encapsulated MoS₂ implementation performed poorly, so edge chemistry and interface/process quality must be checked [196].

The solution-level comparison rows are plasma edge preparation (O₂/CF₄/SF₆ with in-situ ion-beam cleaning), conventional 3D-metal one-dimensional edge contact, and vdW-gap-free one-dimensional edge contact under Edge Contact Engineering [67][78][91]. Plasma exposes and cleans the edge; the one-dimensional geometries strengthen in-plane coupling and narrow the barrier to lower Rc, but sulfur damage/oxidation and edge/interface sensitivity remain risks; a 17 Oct 2019 result reports 53.5 µA/µm [73][84][202][91].

Plasma etching is the Edge Contact Engineering preparation solution: it exposes a clean MoS₂ edge before deposition and can remove resist, but sulfur sputtering/oxidation, anisotropic roughness, edge-state trapping, alignment, stringent in-situ equipment, and scale-up threaten yield and Rc [67][202][90][91][194].

Conventional 3D-metal one-dimensional edge contact is likewise an Edge Contact Engineering solution; the supplied result is Rc≈6 MΩ·µm, and stringent in-situ ion-sputter/metal-deposition requirements make interface quality decisive [88][196][194].

By the cutoff, plasma etching exposes a clean, sharp MoS₂ edge for one-dimensional injection; prompt metallization, edge-state passivation, and removal of adsorbates/oxide or the interface gap support lower R_c, whereas dangling bonds and edge states can trap carriers [289,378]. A 2016 MoS₂ plasma-etching implementation and a representative >50 μA/μm current show pre-cutoff use, but anisotropic or rough etching, oxidation, ion damage, and residue can make injection and R_c variable; the supplied result gives current rather than numerical R_c [271,376,375,447].

## Pathway 3: Contact-region and interface engineering

### Phase conversion and conducting contact regions

**Phase engineering changes the injection region:** rather than asking an external metal to inject directly into pristine semiconducting material, it creates a conducting region within the 2D material itself. The relevant junction then becomes metal/conducting region/semiconducting channel, with the internal boundary often acting as a seamless lateral contact.

| Technical Pathway | Solution Name | Core Mechanism | Representative Results (Device and Performance) | Main Challenges or Limitations |
|---|---|---|---|---|
| Contact-Region/Interface Engineering – Chemical Phase Conversion | Local n-butyllithium treatment | Electron donation induces 2H–1T conversion; metallic MoS₂ improves injection into the preserved 2H channel | Au/1T-MoS₂ contacts: \(R_c=200–300\) Ω·µm versus 1,000–10,000 Ω·µm for Au/2H-MoS₂, associated with Kappera’s 2014 work. [5] | Metastable converted phase and contact-region selectivity |
| Contact-Region/Interface Engineering – Local Plasma Conversion | Ar-plasma-treated MoS₂ | Defect-mediated local 2H–1T conversion creates conducting injection patches | Monolayer MoS₂ with locally converted contact regions: on-current approximately doubled in the reviewed example. [3] | Mixed-phase coverage and nanoscale conversion uniformity |
| Contact-Region/Interface Engineering – Semimetallic Bridge Formation | Soft-O₂-plasma-distorted MoS₂ | Distorted octahedral material creates a semimetallic bridge to the pristine channel | Semimetallic-MoS₂/2H-MoS₂ contacts: \(R_c\approx90\) Ω·µm for three layers; ≈2,000 Ω·µm for one layer, 2022. [3] | Layer-dependent performance and precise localization of plasma-induced distortion |
| Contact-Region/Interface Engineering – Microwave Phase Conversion | Forming-gas microwave plasma | Ion-driven structural rearrangement creates extended metallic 1T regions | Cr/Au-contacted MoS₂: ohmic behavior from 4–300 K; Hall density ≈\(2.3\times10^{15}\) cm⁻² in an ≈8-nm sample, 2018. [22] | Simultaneous thinning, hydrogen-dependent conversion, and mixed structural coverage |
| Contact-Region/Interface Engineering – Laser Phase Patterning | 1T′-MoTe₂ contact regions | Local conversion creates conducting 1T′ regions adjoining semiconducting 2H-MoTe₂ | 1T′/2H-MoTe₂ FET: barrier ≈10 meV and mobility up to ≈50 cm²·V⁻¹·s⁻¹ in the reviewed laser-patterned example. [3] | Laser positioning, phase-boundary control, and thermal reversibility |
| Contact-Region/Interface Engineering – Defect-Mediated Compound Conversion | Ar-plasma conversion of PdSe₂ to Pd₁₇Se₁₅ | Se-vacancy-driven conversion creates a metallic contact compound | Pd₁₇Se₁₅/PdSe₂: \(R_c\approx750\) Ω·µm; barrier ≈3.3 meV; mobility ≈100 cm²·V⁻¹·s⁻¹ at room temperature. [3] | Plasma dose, stoichiometry, and the location of the converted boundary |

**n-Butyllithium is a phase-engineering treatment:** it donates electrons to MoS₂ and promotes conversion from the semiconducting 2H structure to a conducting 1T-like contact region. In the ideal structural description, 2H has trigonal-prismatic coordination and 1T has octahedral coordination. The intervention is therefore more than ordinary surface doping: it changes the semiconductor’s local atomic and electronic structure. [8][22]

**The channel must remain semiconducting:** selective treatment leaves a 2H channel between converted contact regions. The external Au electrode couples to conducting MoS₂, and carriers subsequently enter the channel across the conducting/semiconducting boundary. Converting the whole channel would defeat the switching function that the contact engineering is intended to improve. [3]

**The resistance reduction is substantial:** the quoted Au/2H-MoS₂ and Au/1T-MoS₂ ranges correspond to approximately 3.3–50-fold resistance ratios, calculated from \(1,000/300\) and \(10,000/200\). Choi and colleagues’ account of the pioneering phase-contact device also reports approximately 200 Ω·µm, mobility around 50 cm²·V⁻¹·s⁻¹, and drive current around 100 µA/µm. [5][3]

**Metastability explains the reliability concern:** chemically intercalated MoS₂ can contain a mixture of 1T, distorted phases, and residual 2H material. Sharma and colleagues describe relaxation of intercalation-derived material toward other phases over time or above temperatures around 150 °C. Such changes can alter the conducting fraction and move the effective injection boundary during later processing. [22]

**Plasma treatments are not one mechanism:** Ar-induced local conversion, forming-gas microwave conversion, and soft-O₂-induced distortion employ different chemistries and structural pathways. The soft-O₂ example is best described as a semimetallic, distorted-octahedral bridge rather than automatically equating it with an ideal, uniformly converted 1T electrode. Its atomically sharp boundary is central to the reported injection improvement. [3]

**Layer number changes the result:** the 90 Ω·µm distorted-MoS₂ result belongs to the three-layer entry, while the monolayer entry is approximately 2,000 Ω·µm. The additional layers change the injection cross-section and electronic structure. This contrast is particularly important for engineers targeting monolayer channels: a successful contact treatment must be evaluated at the intended thickness. [3]

**Some phase treatments improve stability:** Sharma and colleagues used microwave plasma containing 10% H₂ and 90% Ar, with lithographic masking to define converted regions. They reported 1T areal coverage above 70%, metallic transport down to 4 K, and stability after 300 °C annealing for up to 15 minutes. Resistance changed little over approximately 90 days, including about 30 days under ambient conditions. [22]

**That stability has specific conditions:** lower microwave power produced etching without phase conversion, and treatment without H₂ produced highly resistive material without the expected Raman phase signatures. The authors proposed that ion momentum drives plane rearrangement while the reducing environment and heating help manage defects. These findings show why plasma composition, power, masking, and thickness loss are integral to the contact solution. [22]

**Material conversion also varies chemically:** laser-patterned MoTe₂ changes its structural phase, while Ar-treated PdSe₂ forms the different conducting compound Pd₁₇Se₁₅ through vacancy-mediated conversion. Both can improve contact injection, but neither should be described as the same 2H–1T process used for MoS₂. Their stability and boundary-control requirements follow their respective transformation chemistry. [3]

**Phase-engineering takeaway:** a locally conducting semiconductor region can strongly reduce injection loss, but its practical value depends on preserving both the conducting contact phase and the semiconducting channel throughout processing and operation.

**Additional documented evidence**

- **n-Butyllithium (n-BuLi)** is best classified as local phase engineering rather than generic contact doping: patterned 2H-MoS₂ was converted to metallic 1T-MoS₂ in a glovebox before metal deposition, reducing the 2014 hetero-phase FET contact resistance fivefold to **0.24 kΩ·µm (240 Ω·µm)** by TLM; the metal identity and full bias/geometry conditions were not reported [84]. A separate account gives **6–48 h at 60 °C** for converting 2H-MoS₂ nanosheets, but does not establish a complete FET result [203]. Glovebox processing, air-stable phase preservation, and spatial phase control are therefore material limitations; class-wide uniformity and yield remain unestablished [84].

- **Other phase-engineered contacts** include sequentially heteroepitaxial 1T′/2H-MoTe₂, laser-induced 1T′-MoTe₂, Ar-plasma-induced 1T-MoS₂, and annealing-induced 1T′ regions. A 2017 1T′-MoTe₂/2H-MoTe₂ device used growth temperatures of **710 °C** and **670 °C**, respectively, giving an estimated Schottky barrier of **~22 meV** and **Rc ~14 kΩ·µm**; the MoS₂ n-BuLi example is the stronger direct Rc demonstration [84]. The mechanism is a metallic injection region with reduced barrier and, in suitable homophase structures, an ohmic path. Precisely controlled conversion, thermal or plasma processing, and the need for air-stable metallic phases constrain integration [84]. A 2023 review additionally quotes **0.2 kΩ** for a 1T/2H-MoS₂ contact, but that later value is discovery-only rather than cutoff-qualified evidence [203].

### Contact doping and carrier-density engineering

**Doping primarily narrows the barrier:** increasing carrier concentration near a contact reduces the depleted region through which carriers must pass. This increases tunneling probability even when the Schottky-barrier height or Fermi-level pinning is not completely removed. Contact doping therefore targets a different physical variable from changing the electrode work function.

| Technical Pathway | Solution Name | Core Mechanism | Representative Results (Device and Performance) | Main Challenges or Limitations |
|---|---|---|---|---|
| Contact-Region/Interface Engineering – Selective Surface Doping | K-vapor treatment | Electron donation increases source/drain carrier density and thins the injection barrier | Au-contacted three-layer WSe₂: after 120 min doping, current increased ≈\(10^5\)-fold; mobility >110 cm²·V⁻¹·s⁻¹; on/off ratio >\(10^4\), 2013. [23] | Dopant diffusion, threshold shifts, and air-stability requirements |
| Contact-Region/Interface Engineering – Oxide-Induced Contact-Edge Doping | AlOₓ capping of Au/MoS₂ | Electron transfer raises carrier density near the contact edge and narrows the Schottky depletion region | Au/CVD monolayer MoS₂: TLM \(R_c\approx480\) Ω·µm; 690 µA/µm at \(V_{DS}=5\) V for \(L=380\) nm, 2021. [6] | Trap activation, pure-Au fabrication yield, and high-field self-heating |
| Contact-Region/Interface Engineering – In-Situ Semiconductor Doping | Fe-doped MoS₂ with Cr/Au | Controlled dopant incorporation enables ohmic injection while managing impurity scattering | Monolayer Fe-doped MoS₂: TLM \(R_c\approx678\) Ω·µm versus ≈117,000 Ω·µm pristine; aligned domains on 2-inch sapphire, 2022. [7][24] | Growth-stage dopant-site and concentration control |
| Contact-Region/Interface Engineering – Molecular Donor Doping | Polyethyleneimine contact modification | Molecular electron donation increases MoS₂ carrier concentration and improves contact injection | Polyethyleneimine-modified MoS₂ FETs: field-effect mobility increased from 20.4 to 32.7 cm²·V⁻¹·s⁻¹, associated with Du’s 2013 work. [25] | Chemical-doping stability under repeated use and environmental exposure |

**Selective K doping demonstrates barrier thinning:** Fang and colleagues treated the source/drain regions of a three-layer WSe₂ top-gated device with Au electrodes. Electron donation increased current dramatically and produced more ohmic low-\(V_{DS}\) output behavior. The approach illustrates how contact-region carrier density can improve injection without requiring the channel to be structurally converted. [23]

**Dopant placement protects transistor behavior:** the K study also observed diffusion-related threshold changes and identified the importance of air-stable dopants. If a nominal contact treatment spreads into the channel or gate stack, it changes switching voltage as well as injection. Spatial confinement is therefore an electrical requirement, not merely a patterning preference. [23]

**AlOₓ provides a particularly developed example:** McClellan and colleagues combined pure Au contacts with a thin oxidized Al seed and approximately 15 nm of atomic-layer-deposited AlOₓ. Atomic layer deposition, or ALD, was performed at 150 °C, followed by a 200 °C N₂ anneal for 40 minutes. The treatment produced high carrier density while recovering mobility and subthreshold behavior that initially degraded after oxide deposition. [6]

**Doping must be separated from trapping:** immediately after AlOₓ deposition, midgap states captured carriers and weakened gate control. After annealing, donor states could supply electrons to the MoS₂ conduction band without the same trapping penalty. A threshold shift or increased current alone consequently does not establish a successful doping process; the accompanying mobility, hysteresis, leakage, and on/off behavior matter. [6]

**Contact-edge doping is not an edge contact:** the AlOₓ layer touched the edge of a top-contact region rather than replacing that contact with a side-plane junction. Because current crowding concentrates injection near the end of the metal overlap, modifying carrier density there was sufficient to narrow the Schottky barrier and improve tunneling. The reported current-transfer-length estimate was approximately 50 nm. [6]

**The current result has explicit bias:** the 380-nm device delivered approximately 690 µA/µm at \(V_{DS}=5\) V, but approximately 300 µA/µm at 1 V. Its reported conduction-area-normalized current exceeded 110 MA/cm² because the conducting layer was only about 6.15 Å thick. The latter is a current-density normalization, not another resistance measurement. [6]

**Process maturity appears in secondary results:** the AlOₓ-doped devices retained high on/off ratio and showed only slight degradation after 60 days in air. At the same time, pure-Au contacts required careful lift-off because adding a conventional Ti or Cr adhesion layer would change the semiconductor interface. The reported Au lift-off yield was approximately 70%. [6]

**Heat becomes important after injection improves:** at the highest tested bias, the authors estimated a channel temperature rise of approximately 400 K. Their modeling associated the high-field current limit with heat removal across the MoS₂/SiO₂ interface and substrate. A low-\(R_c\) contact can therefore expose a different device bottleneck rather than allowing current to increase without bound. [6]

**Fe doping offers a growth-integrated route:** the reported 117,000-to-678 Ω·µm comparison corresponds to approximately 173-fold lower resistance, calculated as \(117,000/678\). Li and colleagues attributed favorable transport to dopant placement and suppressed impurity scattering, and demonstrated aligned Fe-doped monolayer domains on 2-inch sapphire. This connects contact performance to a synthesis route rather than a post-fabrication molecular exposure. [24][7]

**Growth area and selective doping differ:** incorporating dopants during growth can support large-area material production, but controlling the contact region independently of the active channel remains a separate integration consideration. This distinction determines whether a doping strategy primarily solves injection, threshold-voltage control, or both.

**Molecular donors offer processing simplicity:** polyethyleneimine provides a named example of electron-donating molecular treatment, with field-effect mobility increasing from 20.4 to 32.7 cm²·V⁻¹·s⁻¹. That improvement is consistent with reduced contact losses, but field-effect mobility also reflects channel and gate-interface behavior. It should be interpreted as device-performance evidence rather than converted into an \(R_c\) estimate. [25]

**Doping takeaway:** useful contact doping creates mobile carriers close to the injection bottleneck while maintaining gate control, spatial selectivity, and stable charge transfer.

### Ultrathin interlayers and protective buffers

**Interlayers introduce a deliberate compromise:** separating metal from semiconductor can suppress wavefunction-induced gap states and protect against deposition damage, but carriers must still cross the inserted material. The optimum minimizes the combined injection-barrier and tunneling penalties.

| Technical Pathway | Solution Name | Core Mechanism | Representative Results (Device and Performance) | Main Challenges or Limitations |
|---|---|---|---|---|
| Contact-Region/Interface Engineering – Atomic Tunneling Interlayer | One- to two-layer h-BN beneath Ni/Au | Suppresses MIGS penetration; interfacial dipoles reduce the effective Schottky barrier | Four- to five-layer MoS₂: TLM \(R_c=1,800\) Ω·µm at \(n=5.1\times10^{12}\) cm⁻², versus 5,100 Ω·µm without h-BN, 2016. [26] | Added tunneling resistance increases with h-BN thickness |
| Contact-Region/Interface Engineering – Atomic Tunneling Interlayer | Mono-/bilayer h-BN with Cr/WS₂ | Reduced injection barrier with thickness-dependent tunneling | Four-layer WS₂: approximately tenfold lower \(R_c\) than direct contacts; mobility ≈115 cm²·V⁻¹·s⁻¹ at 300 K, 2022. [27] | Performance depends jointly on metal work function and h-BN thickness |
| Contact-Region/Interface Engineering – Oxide Depinning Layer | Cu/TiO₂/MoS₂ contacts | Ultrathin oxide suppresses interface states and lowers the effective barrier while retaining tunneling | Multilayer MoS₂, Cu/Au 15/50 nm, TiO₂ 1.5 nm: TLM \(R_c=4,000\) Ω·µm and effective barrier 22 meV, 2022. [25] | Excess oxide thickness makes tunneling resistance dominant |
| Contact-Region/Interface Engineering – Semiconductor Interlayer | Ti/MoSe₂/MoS₂ contacts | Interposed 2D semiconductor changes the injection band alignment and contact pathway | MoS₂ with Ti/MoSe₂ contacts: \(R_c\approx1,900\) Ω·µm and barrier ≈30 meV in the 2022 compilation. [3] | Requires continuous interlayer coverage and controlled heterointerface alignment |
| Contact-Region/Interface Engineering – Sacrificial Protective Buffer | Se-assisted Au/WSe₂ contacts | Se protects WSe₂ during evaporation; removal leaves a reduced-disorder interface | Few-layer WSe₂/Au: representative hole mobility ≈135 cm²·V⁻¹·s⁻¹ and on/off ratio >\(10^6\); Se removed near 150 °C. [7] | Uniform protection and complete, nondamaging buffer removal |
| Contact-Region/Interface Engineering – Controlled Surface Oxidation | Oxidized-monolayer InSe with In/Au | Uniform surface oxide suppresses MIGS and disorder-induced states, enabling depinning | InSe, In/Au 15/40 nm: ≈1-nm oxide; barrier 65 meV; 103 µA/µm at 2 K, \(V_{DS}=1\) V, \(V_{GS}=80\) V, 2019. [9] | Oxidation thickness, process temperature, and clean contact definition |

**h-BN demonstrates the thickness trade-off:** Wang and colleagues measured 1,800 Ω·µm with one to two h-BN layers, compared with 5,100 Ω·µm for direct Ni/Au contact at the stated carrier density. This is a calculated reduction of approximately 65%, using \((5,100-1,800)/5,100\). Increasing h-BN to three to four layers raised \(R_c\) to 3,200 Ω·µm even though the Schottky barriers were similar. [26]

**The mechanism has two components:** reduced metal-wavefunction penetration suppresses MIGS, while interfacial dipoles help prevent the semiconductor Fermi level from being driven toward the interface charge-neutrality level. These changes improve band alignment, but they do not eliminate the physical tunneling barrier introduced by h-BN. [26]

**The device benefit extends beyond resistance:** optimized h-BN/Ni/Au contacts supported approximately 330 µA/µm output current and 73 cm²·V⁻¹·s⁻¹ mobility at room temperature. At 77 K, the reported values increased to approximately 572 µA/µm and 321.4 cm²·V⁻¹·s⁻¹. These results connect the measured contact improvement with useful transport, while preserving the measurement temperature for each value. [26]

**WS₂ confirms material-dependent behavior:** Phan and colleagues compared direct contacts with mono- and bilayer h-BN contacts in four-layer WS₂ over 77–300 K under vacuum. They found approximately tenfold resistance improvement and different behavior for Cr and In electrodes. The result reinforces that an interlayer and its metal must be designed as a pair. [27]

**TiO₂ supplies an especially clear control:** Cheng and colleagues varied interlayer thickness in Cu-contacted multilayer MoS₂. The 1.5-nm device combined the smallest measured \(R_c\) with a 22 meV effective barrier. At 2.5 nm, resistance increased sharply despite the intended interface-state suppression. [25]

| TiO₂ thickness | Contact resistance | Dominant interpretation |
|---|---:|---|
| 0 nm | 8,200 Ω·µm | Larger Schottky injection penalty |
| 1.5 nm | 4,000 Ω·µm | Favorable balance of barrier reduction and tunneling |
| 2.5 nm | 46,000 Ω·µm | Excessive tunneling resistance |

**Small thickness errors have large consequences:** the optimized TiO₂ layer reduced resistance by approximately 51%, calculated as \((8,200-4,000)/8,200\). Increasing thickness by only 1 nm above that optimum increased resistance 11.5-fold, calculated as \(46,000/4,000\). Uniformity and oxidation control are therefore central manufacturing variables, not secondary refinements. [25]

**Barrier reduction is not proportional conductance:** the effective barrier fell from 168 to 22 meV between the direct-contact and optimized TiO₂ devices, while resistance fell by about half. This is consistent with multiple contributions to the contact: lowering the semiconductor barrier helps, but the inserted oxide also carries a tunneling penalty. The fitted effective barrier represents the combined contact behavior rather than a complete microscopic description of the oxide. [25]

**Earlier TiO₂ work established the principle:** Park and colleagues’ 2014 IEDM study reported approximately 5,400 Ω·µm and a 0.1 eV effective barrier using an optimized depinning layer without intentional doping. The later thickness sweep adds a direct explanation of why interlayer optimization is nonmonotonic. [28]

**A semiconductor buffer need not act identically:** MoSe₂ between Ti and MoS₂ introduces an additional semiconductor band alignment rather than simply an insulating spacer. Its reported low-resistance contact supports band-structure engineering at the injection region. It should not automatically be assigned the same complete-depinning mechanism as a successful ultrathin oxide; the actual alignment and coupling of both semiconductor interfaces matter. [3]

**Se protection is a sacrificial process:** the Se layer protects WSe₂ while the metal is deposited and is subsequently removed near 150 °C. Its purpose is to prevent a damaged final junction, not to leave a permanent insulating film through which carriers must tunnel. This explains why a buffer-assisted process belongs within interface engineering even when the completed device is a metal/WSe₂ van der Waals contact. [7]

**Contact polarity reveals the interface change:** the Frontiers account contrasts n-type direct-Au WSe₂ devices with p-type van der Waals-contacted devices after interface protection. Calculations associated direct contact with additional midgap states and altered band bending. Because the electrode remains Au, the polarity difference provides evidence that the fabricated interface—not simply the tabulated metal work function—controls injection. [7]

**Controlled InSe oxidation gives quantitative depinning:** Chen and colleagues formed an approximately 1-nm oxidized monolayer by UV–ozone treatment at 80 °C for ten seconds. The pinning factor increased from \(0.05\pm0.02\) in controls to \(0.50\pm0.01\) with the oxide. The study combined structural evidence for a uniform barrier with electrical evidence that metal selection again influenced contact behavior. [9]

**Depinning can worsen an unsuitable electrode:** with In contacts, the controlled oxide enabled a 65 meV barrier and improved current. With Pd, depinning increased the electron barrier from approximately 0.28 to 0.57 eV. This is a direct experimental counterexample to treating “more depinning” as synonymous with “lower resistance” independent of electrode choice. [9]

**Oxidation still requires thickness control:** increasing UV–ozone processing temperature from 80 toward 90–100 °C produced thicker oxide and lower current. The successful devices also used resist-free shadow definition and clean deposition to preserve a uniform barrier. Their two-terminal mobility reached 940 cm²·V⁻¹·s⁻¹ at 300 K and 2,160 cm²·V⁻¹·s⁻¹ at 2 K. [9]

**Interlayer takeaway:** a useful buffer reduces harmful interaction more than it obstructs carrier transmission; thickness, band alignment, and final interface cleanliness determine that balance.

**Additional documented evidence**

**Solutions included.** The roster contains 2H-to-1T, 1T′, or 1Tᵈ phase conversion; Li or n-butyllithium treatment; laser, plasma, or thermal phase engineering; CVD-grown metallic transition-metal dichalcogenide contacts; intercalation-induced metallic states; local chemical/electrostatic contact doping; and memristive forming at contact regions. In 2014, phase-engineered metallic 1T-MoS₂ electrodes produced \(200\text{–}300\ \Omega\cdot\mu\mathrm{m}\) contact resistance at zero gate bias [30]. In 2015, CVD-grown monolayer WSe₂ FETs with metallic 1T-WSe₂ contact regions reached an on/off ratio of \(10^7\) and mobility up to \(66\ \mathrm{cm^2\,V^{-1}\,s^{-1}}\) [49]. A pre-2023 memristive-forming study reduced MoS₂-FET contact resistance by at least one order of magnitude and improved MoTe₂-FET on-state current density by approximately two orders of magnitude [33].

Use the dominant physical lever for classification. Top/interface engineering covers selected metals (Sc, In/Au, Bi, Sb), transferred/vdW electrodes, buffer or tunnelling layers, and interface treatments [37][43][47][48]. Conventional deposition can damage 2D material and create MIGS/FLP; transfer suppresses chemical disorder and depins the Fermi level, though the vdW gap adds a tunnelling barrier [45]. A 2022 MoS₂ MIS device illustrates the thickness trade-off: 1.5-nm TiO₂ produced \(R_c=4\ \text{kΩ·µm}\) by TLM, versus 8.2 kΩ·µm without it; 2.5 nm raised \(R_c\) to 46 kΩ·µm [47].

Edge/1D engineering is a separate geometry pathway: exposed-edge injection changes the current path and can reduce crowding. For mono-/bilayer MoS₂, carriers are predicted to enter mainly at the contact edge; ideal edge-only contacts avoid crowding, but experimental results were sub-par [44][46]. In-/ex-situ edge-metal deposition is a process variant, not a separate pathway [45].

**Additional documented evidence**

**Phase-engineered metallic contact, including n-butyllithium.** n-BuLi, laser irradiation or Ar plasma converts exposed 2H MoS₂ to metallic 1T while protected regions remain 2H, producing a patternable, atomically seamless contact; the cited phase study is from 2014 and the Ar-plasma study from 2017. For 1T-MoS₂-contacted 2H-MoS₂, the source reports “1.1 to 200 kΩ·µm” as a reduction and mobility from **19 to 46 cm²/(V·s)**; the ordering and unit pairing are internally inconsistent, so that Rc value is not safely comparable. A laser-induced 1T′-MoTe₂ contact reduced the reported barrier from **200 to 10 meV** and increased mobility from about **1 to 50 cm²/(V·s)**; these are proxies rather than Rc. The method requires a material with stable or metastable phases; induced T phase may revert to H over time or above **100 °C**, and the 2H–1T boundary barrier is not systematically characterized. For n-BuLi specifically, dose, air-safety, reproducibility and independent Rc extraction are not reported. [88]

**Broad metallic-2D contact.** This umbrella covers the CVD, phase and intercalation examples above rather than adding independent mechanisms. Its representative VS₂–MoS₂ result is therefore **520 Ω·µm at Vg = 50 V**; WTe₂, NbTe₂ and graphene provide named variants and barrier, current or mobility proxies. The remaining causal uncertainty is whether improvement arises from the metallic contact itself or coupled changes in mobility, barrier and device architecture. Apparent linear I–V is not sufficient proof of ohmic injection: an h-BN-encapsulated MoS₂ edge device still had calculated Rc of about **314 kΩ** and mobility of **1.2 cm²/(V·s)**. [88]

## Comparing pathways and selecting an implementation

### Shared engineering axes

**The pathways solve different problems:** top contacts offer relatively direct integration with planar processing; edges address injection geometry and lateral scaling; contact-region methods alter the barrier or conducting state locally. A sensible comparison therefore starts with the device constraint that motivates the contact change.

| Shared axis | Top-contact engineering | Edge-contact engineering | Contact-region/interface engineering |
|---|---|---|---|
| Injection geometry | Basal-plane overlap | Exposed side plane or grown lateral junction | Often retains the original geometry while modifying its injection region |
| Main physical lever | Electrode electronic structure and interface preservation | Orbital coupling and direct lateral access | Carrier density, local phase, or controlled separation |
| Multilayer compatibility | Deeper layers require interlayer access | Can contact multiple side planes directly | Depends on treatment penetration and modified-region structure |
| Integration strength | Conventional patterning and deposition are readily adapted | Compatible with encapsulated and compact-contact architectures | Can complement either top or edge structures |
| Principal process burden | Cleanliness, deposition energy, and electrode stability | Etching, edge cleaning, bonding, and alignment | Treatment selectivity, thickness control, and activation |
| Main reliability concern | Reaction, contamination, and thermal evolution | Oxidation and variable edge termination | Phase relaxation, dopant redistribution, or barrier nonuniformity |

**The strongest improvements include internal controls:** same-study comparisons help connect an intervention with a changed contact, especially when geometry, thickness, and extraction conditions are held close. They are particularly valuable for judging whether an added process step removes the intended bottleneck.

| Contact comparison | Reference \(R_c\) | Engineered \(R_c\) | Calculated resistance ratio |
|---|---:|---:|---:|
| Direct Ni/Au versus thin h-BN/Ni/Au on MoS₂ | 5,100 Ω·µm | 1,800 Ω·µm | 2.83×. [26] |
| Direct Cu versus 1.5-nm TiO₂/Cu on MoS₂ | 8,200 Ω·µm | 4,000 Ω·µm | 2.05×. [25] |
| Ni–MoS₂ versus lateral VS₂–MoS₂ | 8,640 Ω·µm | 520 Ω·µm | 16.6×. [7] |
| Pristine versus Fe-doped monolayer MoS₂ | 117,000 Ω·µm | 678 Ω·µm | ≈173×. [7] |
| Comparable In top contact versus In/Au MoS₂ edge contact | ≈40,700 Ω·µm, estimate | 4,070 Ω·µm | ≈10×. [4] |

**The final reference is a reconstruction:** the estimated In top-contact value is \(4,070\times10\approx40,700\) Ω·µm, using the measured edge-contact resistance and the paper’s approximately tenfold comparison. It represents that particular comparator, not an expected resistance for In top contacts generally.

**Large improvement factors depend on the baseline:** Fe doping’s approximately 173-fold ratio is compelling evidence of a major change within its reported comparison, but it is not a measure of superiority over a Bi or alloy contact starting from a much better baseline. Likewise, a modest fractional improvement can be valuable when the original contact already performs well. Both absolute \(R_c\) and the relevant reference device are needed.

**Carrier polarity changes the shortlist:** Bi, In-based contacts, and electron-donor treatments primarily support n-type injection in these examples. High-work-function clean contacts, conducting hole-contact layers, and protected WSe₂ interfaces serve a different objective. The approximately 300 Ω·µm Nb-doped-WSe₂ contact example also shows why the best n-type metal cannot define the p-type solution space. [3]

### Contact scaling and device-level consequences

**Short channels amplify contact losses:** channel resistance decreases with \(L\), while the two contact contributions remain. Using the AlOₓ study’s \(R_c=480\) Ω·µm and representative \(R_{\mathrm{sh}}=8,100\) Ω/□, equal channel and combined-contact resistance occurs at an estimated \(L=2R_c/R_{\mathrm{sh}}=960/8,100\) µm, or approximately 119 nm. Below this scale, further channel shortening increasingly exposes the contact bottleneck. [6]

**Contact length introduces another scale:** current transfers between an overlapping metal and semiconductor mainly within a characteristic distance near the contact edge. In the AlOₓ work, dividing 480 Ω·µm by an average channel sheet resistance of about 9,000 Ω/□ gives approximately 53 nm, used as an upper-bound transfer-length estimate. Contact overlaps approaching or falling below this distance require additional attention to current crowding. [6]

**Edge contacts address that geometric penalty:** their injection interface follows the channel edge rather than an extended overlap region. This explains their relative immunity to changing lateral contact length. It does not remove finite transmission resistance or the need for a clean, chemically suitable edge. [3]

**High current needs more than contacts:** once injection improves, channel sheet resistance, carrier velocity, dielectric electrostatics, and heat removal become increasingly important. The AlOₓ case is especially instructive because its high-current behavior was limited by self-heating despite a low measured \(R_c\). A contact strategy should consequently be judged by useful current at the intended supply voltage and temperature, as well as by its resistance minimum. [6]

### What the extraction method establishes

**TLM separates slope and intercept:** the transfer length method uses devices or contact separations with different channel lengths. At consistent carrier density or gate overdrive, the resistance–length slope estimates sheet resistance and the intercept estimates the two-contact contribution. McClellan and colleagues used channel lengths from 180 to 980 nm and emphasized spanning contact-dominated and channel-dominated devices. [6]

**Four-terminal measurements separate channel transport:** voltage probes reduce the influence of current-contact drops on channel-resistance measurements. They are particularly useful when establishing whether a converted contact region is actually metallic or when comparing different injection materials. The VS₂ comparison used four-probe measurements, while the microwave-MoS₂ study combined two- and four-probe transport with Hall measurements. [7][22]

**Y-function extraction needs a valid window:** it offers a simpler route when multiple-length or four-probe structures are difficult to fabricate. However, Hemanjaneyulu, Kumar, and Shrivastava’s 2022 study found that its applicability depends on Schottky behavior, drain bias, electric field, and contact resistance. Their analysis covered MoS₂, MoSe₂, WS₂, and WSe₂ and narrowed the operating conditions under which estimates approached TLM results. [29]

**Assumptions must retain their status:** the K-doping paper estimated carrier density by assuming that barrier thinning made tunneling probability approach unity and allowed post-doping contact resistance to be neglected. That is an extraction assumption, not an experimental demonstration of exactly zero contact resistance. Keeping that distinction preserves the useful conclusion—strongly improved injection—without assigning an artificial resistance value. [23]

## Engineering judgment at the end of 2022

**The preferred solution follows the objective:** the following decision table translates the completed comparisons into device-level choices. These are engineering judgments based on the demonstrated mechanisms and operating constraints.

| Device objective | Leading candidates | Decisive evidence | Condition that changes the choice |
|---|---|---|---|
| Low-resistance n-type monolayer injection | Bi; In/Au or Sn/Au alloys | 123, 190, and 270 Ω·µm anchors | Defects, thermal processing, or contact-length constraints dominate |
| Processing near 400 °C | Sb; thermally qualified alloys | Sb operational after 400 °C; alloy approach reported ≈450 °C tolerance | Full process sequence degrades the particular interface |
| Hole injection into WSe₂ or MoS₂ | Optimized Pt/WSe₂ or Pd/MoS₂; conducting 2D hole contacts | Depinning, p-type transport, and direct resistance examples | Metal-specific reactions or unfavorable band alignment remain |
| Encapsulated or multilayer devices | Clean metal edges; graphene hybrids | Direct side-plane access and preserved channel interfaces | Edge oxidation, assembly yield, or alignment dominates |
| Contact modification compatible with CVD MoS₂ | AlOₓ doping; controlled Fe incorporation | 480 and 678 Ω·µm examples | Trap generation, dopant placement, or threshold control becomes limiting |
| Interface-state suppression with an existing electrode | Thin h-BN, optimized TiO₂, controlled surface oxide | Thickness sweeps and measured depinning | Added tunneling resistance outweighs barrier improvement |

**Manufacturing favors complete contact recipes:** the transferable unit is the electrode, interface preparation, patterning sequence, activation or annealing step, and protective environment together. An apparently simple metal substitution may require demanding deposition control; an additional interlayer may be worthwhile if it stabilizes a reproducible interface. The alloy, AlOₓ, and optimized-evaporation studies are particularly informative because they connect contact physics with process details.

**Reliability changes the laboratory preference:** low initial resistance is most useful when retained after thermal processing, environmental exposure, repeated operation, and dimensional scaling. The decisive conditions for eventual manufacturing preference are resistance after the full process sequence, useful current at the intended voltage, contact-length dependence, device-to-device uniformity, and yield. Phase stabilization and clean edge formation matter because they determine whether the injection interface remains the one originally designed.

**Measurement basis governs the comparison:** the quoted results use different layer counts, carrier densities, temperatures, biases, geometries, and extraction methods. Mobility, barrier height, current, and on/off ratio remain labeled device metrics rather than conversions into \(R_c\). Review-tabulated values are identified as such; resistance ratios, the reconstructed In comparator, and scaling lengths are calculations from stated inputs, while the AlOₓ temperature rise is the original authors’ model estimate. The values support mechanism-based comparisons, not a universal numerical ranking.

**The overall conclusion is practical:** by the end of 2022, semimetal and alloy top contacts, locally conducting contact regions, and carefully engineered doping had demonstrated strong low-resistance performance. Edge contacts offered a distinct architectural advantage for multilayer access and scaling. The most promising implementation is the one that matches its injection mechanism to the required carrier polarity, geometry, and process budget while preserving the active channel.

## Appendix: Further Evidence

**Additional documented evidence**

The pre-2023 evidence supports exactly three primary pathways for reducing \(R_\mathrm{c}\) in 2D FETs: **(1) top-contact and metal/2D-interface engineering, (2) edge and one-dimensional contact engineering, and (3) contact-region material-state and electronic engineering** [32][31][30][33]. The distinction is physical rather than procedural: the first modifies the metal–basal-plane interface, the second changes the carrier-injection geometry, and the third modifies the semiconductor or contact region itself into a doped, metallic, phase-converted, or low-resistance state.

Each solution receives one primary assignment according to its dominant \(R_\mathrm{c}\)-changing mechanism. Thus, a transferred **top** electrode belongs to pathway 1, whereas a transferred electrode that injects through an exposed **edge** belongs to pathway 2. Metallic 2D materials are not a fourth pathway: a metallic counterpart or phase-converted contact belongs to pathway 3, while graphene used only as a van der Waals top electrode belongs to pathway 1. Contact length, extraction method, and wafer-scale integration are cross-cutting geometry or process variables rather than independent pathways.

**Additional documented evidence**

The strongest eligible result in this source group is **not a conventional transistor benchmark**: the 2020 study directly measured point contacts to free-standing CVD-grown two-dimensional materials using an in-situ TEM–STM setup at room temperature. It therefore establishes how interface structure, contact area, defects, and van der Waals (vdW) gaps affect contact transport, but it does not by itself establish a width-normalized \(R_\mathrm{c}\) for a fabricated 2D FET. The CVD-grown metallic-contact entry should consequently be retained as a **mechanism and process candidate**, with its measured quantities kept distinct from transistor \(R_\mathrm{c}\). [96]

For the supported configuration, a tungsten (W) STM tip contacted free-standing CVD-grown single-layer MoS₂, ReS₂, and graphene. In the metallic-2D case, the source links CVD-grown graphene’s intrinsic semimetal character and low atomic-defect density to a lower probability of chemical bonding, a vdW interface, and direct tunnelling. More generally, flat, smooth, parallel vdW interfaces provide relatively homogeneous conducting channels, whereas chemically bonded interfaces contain defect-related or segregated high-resistance regions. [96]

The transport regime depends strongly on contact area. For CVD-grown MoS₂ and ReS₂, contacts below approximately \(50\ \mathrm{nm^2}\) were fitted by direct tunnelling, while contacts above approximately \(95\ \mathrm{nm^2}\) displayed rectifying behaviour fitted by Fowler–Nordheim tunnelling. The reported transition areas were \(249\ \mathrm{nm^2}\) for MoS₂ and \(97.0\ \mathrm{nm^2}\) for ReS₂; these are setup-specific observations, not universal contact-area thresholds for integrated FETs. [96]

| Representative source record | 2D material or channel | Actual contact | Reported result and definition | Evidence status |
|---|---|---|---|---|
| CVD-grown MoS₂, published 2020-08-07 | Single-layer CVD MoS₂ | W STM tip; \(33.3\ \mathrm{nm^2}\) contact area | Source-reported contact resistivity \(\rho=3.81\times10^{7}\ \Omega\cdot\mu\mathrm{m}\), fitted with the direct-tunnelling model. The source defines \(R=dV/dI\) at \(V=0\) and uses \(\rho=RA/d\). [96] | Primary contact-transport result; not a width-normalized 2D-FET \(R_\mathrm{c}\) |
| CVD-grown MoS₂, published 2020-08-07 | Single-layer CVD MoS₂ | W STM tip; \(249\ \mathrm{nm^2}\) contact area | Source-reported contact resistivity \(\rho=2.47\times10^{8}\ \Omega\cdot\mu\mathrm{m}\), fitted with the Fowler–Nordheim model. [96] | Primary contact-transport result; not directly comparable with TLM-extracted \(R_\mathrm{c}\) |
| CVD-grown ReS₂, published 2020-08-07 | Single-layer CVD ReS₂ | W STM tip; \(45.4\ \mathrm{nm^2}\) contact area | Source-reported contact resistivity \(\rho=2.78\times10^{7}\ \Omega\cdot\mu\mathrm{m}\), fitted with direct tunnelling. [96] | Primary contact-transport result; contextual rather than a transistor result |
| CVD-grown ReS₂, published 2020-08-07 | Single-layer CVD ReS₂ | W STM tip; \(97.0\ \mathrm{nm^2}\) contact area | Source-reported contact resistivity \(\rho=7.68\times10^{7}\ \Omega\cdot\mu\mathrm{m}\), fitted with Fowler–Nordheim tunnelling. [96] | Primary contact-transport result; contextual rather than a transistor result |
| CVD-grown graphene, published 2020-08-07 | Single-layer CVD graphene | W STM tip; \(42.2\ \mathrm{nm^2}\) contact area | Source-reported contact resistivity \(\rho=5.54\times10^{2}\ \Omega\cdot\mu\mathrm{m}\), fitted with direct tunnelling. [96] | Primary metallic-2D contact result; not a 2D-FET \(R_\mathrm{c}\) |
| CVD-grown graphene, published 2020-08-07 | Single-layer CVD graphene | W STM tip; \(174\ \mathrm{nm^2}\) contact area | Source-reported contact resistivity \(\rho=4.90\times10^{3}\ \Omega\cdot\mu\mathrm{m}\), also fitted with direct tunnelling. [96] | Primary metallic-2D contact result; area and geometry must be retained |
| Exfoliated MoS₂ comparator, published 2020-08-07 | Exfoliated MoS₂ | W STM tip; contact area below \(50\ \mathrm{nm^2}\) | The source reports a contact-resistivity range of approximately \(2.67\times10^{5}\) to \(1.43\times10^{7}\ \Omega\cdot\mu\mathrm{m}\) for the exfoliated comparator. [96] | Comparator only; not CVD-grown and not a transistor \(R_\mathrm{c}\) |

The numerical values above must not be relabeled as width-normalized \(R_\mathrm{c}\). The source’s \(\rho=RA/d\) expression uses the measured contact area and a barrier-width term, whereas a transistor table normally requires a per-contact or contact-pair quantity normalized by contact width. The same study reports current–voltage and current-density–voltage behaviour, but the supplied record does not provide a numerical current density in \(\mu\mathrm{A}/\mu\mathrm{m}\) for a 2D FET. [96]

The main mechanism is therefore **interface-controlled tunnelling rather than CVD growth alone**. Direct tunnelling is favoured by a flat vdW gap; chemical bonding and defect states can produce band realignment, Fermi-level pinning, triangular barriers, and Fowler–Nordheim transport. The study also finds that contact area, layer thickness, geometry, strain, and atomic defects materially affect the result. In particular, higher in-plane strain reduced contact resistivity for graphene and MoS₂ but increased it for ReS₂, showing that an apparent material advantage can instead reflect strain or defect changes. [96]

**Additional documented evidence**

For **phase-engineered metallic contacts**, this source group provides no demonstrated 2H-to-1T or 1T′ contact conversion and no phase-engineered 2D-FET \(R_\mathrm{c}\). The closest evidence is a chemically bonded W–MoS₂ contact in which current-density–voltage behaviour was measured and chemical interactions modified the electronic structure. Defect-related scattering, Fermi-level pinning, and Fowler–Nordheim barriers are supported alternative explanations for an apparent contact change; phase uniformity, metastability, and phase-specific scalability are not established here. [96]

**Additional documented evidence**

The same post-cutoff source reports a simulated Bi–MoS₂ value of **\(4.5\ \mathrm{k}\Omega\cdot\mu\mathrm{m}\)** at the minimum-energy separation of \(3.2\ \text{Å}\); increasing the separation to approximately \(4.0\), \(4.5\), and \(5.3\ \text{Å}\) suppresses MIGS and the Schottky barrier but increases the tunnelling-barrier thickness, producing a competing trade-off. It predicts **\(64\ \Omega\cdot\mu\mathrm{m}\)** for Sc–hBN–MoS₂ at a \(40\ \mathrm{nm}\) contact length, with zero simulated Schottky-barrier height and a \(0.53\ \mathrm{nm}\) tunnelling barrier, and **\(7.5\ \mathrm{k}\Omega\cdot\mu\mathrm{m}\)** for Au–WSe₂ at a \(0.40\ \mathrm{nm}\) separation, with a \(70\ \mathrm{meV}\) simulated barrier. These values are simulation or post-cutoff context and must not be used as the historical CVD-contact result. [85]

**Additional documented evidence**

- **CVD-grown metallic 2D contacts** provide an integrated injection interface. In a 2019 WSe₂ FET, two-step CVD formed metallic 1T′-WTe₂ on 2H-WSe₂; the Schottky barrier decreased from **126 to 71 meV**, with improved on/off ratio and mobility, but no Rc was reported [84]. This is distinct from a CVD-grown channel with a conventional contact: CVD monolayer MoS₂ with Au-capped In (10-nm In/100-nm Au, 200 °C H₂/Ar anneal) reached **3.3 ± 0.3 kΩ·µm** at **5.0 × 10¹² cm⁻²** and mobility **167 ± 20 cm²·V⁻¹·s⁻¹** [84]. CVD scale-up still faces low-defect growth, wafer-temperature, reliability, contamination, and uniformity constraints; some reported voids and grain-boundary limitations concern CVD films generally, not uniquely metallic contacts [363, 391].

- **Broad metallic-2D contacts** encompass metallic 2D buffers, 2D top/edge contacts, and related vdW interfaces—not a fourth top-level pathway. Their benefit is metallic carrier injection with cleaner, flatter interfaces, reduced MIGS/Fermi-level pinning, and lower barrier; incomplete metalization, under-contact sheet resistance, contact length, and extraction conditions remain competing explanations [84]. Transferred-metal MoS₂ contacts showed pinning factors of **~0.96** versus **~0.09** for evaporated contacts, while graphene insertion reduced MoS₂/Ag barrier height from **300 to 190 meV** [84]. A post-cutoff review reports TLM values of **~430 kΩ·µm** for multilayer MoS₂/Pd and **~3.3 kΩ·µm** for multilayer WSe₂/Pt, but these are contextual only [203]. A 2025 MXene alloy proposal is likewise simulated and lacks direct experimental validation, so it is excluded from the historical roster [204].

- **CVD metallic-2D/process candidate:** High-temperature CVD films show voids, impurities, grain boundaries and misalignment; no pre-2023 2D-FET channel/contact/Rc record is supplied, so scale and yield remain unestablished. [97]
- **Phase candidate:** Patterned n-BuLi converts 2H→1T MoS₂ before deposition (6–48 h, 60 °C) and reportedly lowers Rc; 1T/2H MoS₂ is reported at 0.2 kΩ (not Ω·µm; 2023 secondary, discovery-only). Doping/intercalation and air instability confound attribution. [97]
- **Intercalation candidate:** Metallic-state/structural conversion is proposed, but host–guest choice and the in-situ mechanism remain unresolved; scalable, low-cost processing and air stability are problematic, with no qualifying 2D-FET Rc/current-density record. [97]
- **Broad metallic-2D family:** 2D top/edge, vdW and metallic-TMD covalent contacts form a family, not a standalone pathway. vdW/FLP suppression and hybridization aid injection; incomplete metalization, residues, strain and under-contact sheet resistance confound. Ambient TLM values are ≈430 kΩ·µm for MoS₂/Pd and ≈3.3 kΩ·µm for WSe₂/Pt, with date/definition missing. [97]
- **Local contact doping:** It may narrow Schottky barriers and remove FLP, but beyond n-BuLi no qualifying pre-2023 local 2D-FET result exists; status remains uncertain. [97]

**Phase contact (third pathway).** The 2020 review (1 July) lists phase, CVD and intercalation contacts [88]. Examples: 2H-MoS₂/1T-MoS₂ (Kappera, 2014), laser-induced 1T′-MoTe₂ (2015), and Ar-plasma 1T/2H-MoS₂ (2017) [30][88][205]. Metallic injection is the rationale; curves are shown, but Rc (Ω·µm), current density, method, bias/temperature, geometry and date are absent. Uniformity, metastability, damage, patterning, thermal budget, scale and electrostatic limits are unreported [88].

**Additional documented evidence**

By 26 December 2017, n-BuLi-treated MoS₂ with 1T/1T′ material beneath Ti/Au electrodes yielded extracted per-contact \(R_\mathrm{c}=5.2\ \text{k}\Omega\) at 275 K and 70 kΩ at 90 K [132]. It is assigned to the third pathway—contact-region chemical/phase engineering—although this result is not a dedicated conventional-2H-channel optimization.

Pre-2023 flakes were immersed in 1.6 M n-BuLi/hexane for more than 48 h and washed. Charge transfer incompletely converted 2H-MoS₂ to 1T/1T′; high electron density and linear I–V characteristics indicated metallic/ohmic behavior. The representative stack used 5-nm Ti/70-nm Au, with converted material beneath the contacts [209]. \(R_\mathrm{c}=0.5[R_{2T}-(l_{2T}/l_{4T})R_{4T}]\) was obtained from two- and four-terminal data, including ±100 nA four-probe measurements; it was below 20% of total resistance over 90–275 K. These kΩ values lack width normalization and are not directly comparable with Ω·µm data [132].

**Contact-region chemical and local-doping candidates**

**Local chemical contact doping (NO₂; demonstrated pre-2023).** Retain this as a contact-region modification solution, not a fourth top-level pathway: a monolayer WSe₂ p-FET published on 14 June 2012 used patterned NO₂ chemisorption on Pd/Pd–Au source/drain contacts [98]. Heavy p-doping narrows the Pd–WSe₂ Schottky-barrier width and increases hole tunnelling; NO₂ may also raise the Pd work function and lower the barrier height. Linear low-\(V_{\mathrm{DS}}\) curves were consistent with ohmic contacts [98]. The source reports no Rc value: after 0.05% NO₂ in N₂ for 10 min, room-temperature performance included >1000× higher ON current without changing \(I_{\mathrm{OFF}}\), effective hole mobility of approximately 250 cm²/(V·s), subthreshold swing of approximately 60 mV/dec, and \(I_{\mathrm{ON}}/I_{\mathrm{OFF}}>10^6\) [98]. These are alternative metrics, not Rc. The documented limitation is reversibility: NO₂ desorbs in ambient air, so doping and ON-state behavior revert; permanent doping was not established [98]. General doping literature also warns of threshold-voltage shifts, dose and uniformity problems, residues, metrology challenges, precursor instability, and scale-up issues; these caveats are not all 2D-FET-specific [99][167]. Later 2017–2022 doping leads identify doped WSe₂/2D FETs, but the retained spans do not establish local contact geometry or Rc; a 2024 oxygen-plasma/transfer-contact WSe₂ result (estimated individual Rc ≈3.6 kΩ·µm; >30,000× reduction) is post-cutoff discovery-only [208][93]. A 2025 secondary page also reports 0.7 kΩ·µm for HAuCl₄-doped monolayer WSe₂ at a doping level of 1.76×10¹³ cm⁻², but this remains a discovery lead rather than final historical evidence [206].

CVD-grown metallic two-dimensional-material contacts are linked to lower Rc because CVD-grown MoS2, ReS2 and graphene exhibit van der Waals/direct-tunneling transport that is more conductive than defect-mediated Fowler–Nordheim transport [96]. Contact area, defects and geometry must be controlled before attributing the effect to CVD itself; the reported TMDC contact-resistivity range is 2.67 × 10 5 to 2.47 × 10 8 Ω μm [96].

Intercalation-induced metallic contact states reduce interface resistance when intercalated Li lowers Schottky and tunnel barriers through its low potential energy and mild electron doping [207]. Co intercalation converts n-type SnS2 into metallic Co–SnS2 and improves current in contacted devices, but no direct Rc or controlled causal comparison is supplied; host–guest choice and the actual structural change must therefore be checked [88][161][97].

rejected: no_entity — Use the van der Waals-contact/FLP-free framework for broad two-dimensional metallic-material contacts: vdW bonding and metallic injection reduce defects and pinning, enable direct tunneling or reduced barriers, and edge geometries add stronger orbital overlap and narrower Schottky barriers [84][203]. Reported broad-contact values include ~430 kΩ·µm and ~3.3 kΩ·µm, but area, thickness, geometry, defects, and under-contact resistance must be controlled before attributing Rc to the metallic contact family alone [96][203].

n-Butyllithium contact treatment is primarily local phase engineering: its strong-base, nucleophile and reductant chemistry converts patterned MoS2 from semiconducting 2H to metallic 1T/1T′ before metal deposition [150][210][97]. A representative reduced-contact result is 200–300 Ω·μm , but doping/intercalation chemistry and geometry or under-contact effects must be separated from the phase contribution [182][209].

rejected: no_entity — Within the CVD-grown metallic two-dimensional-material contact framework, CVD growth is one fabrication route alongside phase engineering and intercalation, not an independent top-level pathway [88]. Pre-2023 evidence is transport on CVD-grown MoS2, ReS2, and graphene with W probes; it links vdW/direct tunneling to low-defect interfaces, but CVD-specific FET Rc attribution still requires controls for area, defects, and contact geometry [96][85].

Broad two-dimensional metallic-material contacts are the umbrella vdW/top/edge family: clean vdW interfaces suppress FLP and defects, while covalent or edge hybridization can remove the vdW gap, narrow the Schottky barrier and improve injection [84][88][203]. Representative values are ~430 kΩ·µm and ~3.3 kΩ·µm [203], but CVD growth, phase conversion, intercalation, geometry, area, defects and carrier density must be disentangled before claiming a family-wide Rc effect [96][97].

Use a practical three-pathway framework: top-contact/interface engineering tunes energy alignment and suppresses Schottky barriers, MIGS and FLP; edge-contact engineering uses stronger edge overlap and a narrower injection barrier; and contact-region/metallic-two-dimensional/phase engineering creates a metallic injection region through CVD growth, phase conversion or intercalation. Wafer-scale optimization is an integration and scalability umbrella rather than a separate Rc mechanism; broad metallic contacts remain the umbrella family, while local NO2 doping is retained as a qualifying contact-doping example and unsupported memristive forming is excluded [84][88][97][98]. By the cutoff, CVD-grown and broad metallic contacts have mechanism/performance evidence, intercalation has metallic-state/current evidence but no direct Rc, and the report should proceed from scope and framework to the comparison table, evidence audit and references, with each row assigned a pathway, mechanism, material/performance metric and limitation [88][96][98][97].

CVD-grown metallic two-dimensional-material contacts are a route for lowering Rc through van der Waals interfaces that avoid Fermi-level pinning and favor direct tunneling; larger contact areas instead favor Fowler–Nordheim tunneling [88][96]. In pre-2023 CVD-grown MoS2 transport, the reported value rose from 3.81 × 10 7 Ω μm at 33.3 nm 2 to 2.47 × 10 8 Ω μm at 249 nm 2, while voids, impurities, grain boundaries, atomic misalignments, high-temperature growth, and wafer-scale reliability limit scale-up and require controls before assigning the result specifically to CVD FET Rc [96][85][203].

**Additional documented evidence**

Eligible: Bi/Sb–WS2 (2022) Rc 0.63/0.73 kΩ·µm; Ion 250/243 µA/µm @1V [219]; phase-MoS2 Rc 200–300 Ω·µm (2014) [30]; In–InSe Ion 410 µA/µm, ΦB 50 meV (2018) [218]; transfer-MoS2 arrays 270 (2022), DCE-MoS2 Rc 0.5 kΩ·µm (2014), edge process 2022 [220][224][214]. TLM/YFM; gaps limit ranking [114][212]; later/non-2D/3D-IC context [211][216][221].

Valid comparison needs matched Rc/2Rc, extraction, width, bias, geometry and T; SBH, Rtotal and current are proxies [222][176]. Pre-2023: Sc/MoS2 30meV SBH, J=240µA/µm (no Rc) [176]; In/Au-MoS2 Rc=190Ω·µm [37]; Bi-MoS2 Rc=123Ω·µm (TLM) [39]; Ag-transfer/MoS2 Rc=60kΩ·µm (TLM) [226]. Interface states, doping and geometry confound [225]. n-BuLi nanosheets are non-FET; post-cutoff cards are leads only [97][77][227].

Rc rankings need matched definition, method, geometry, bias, temperature and date; otherwise invalid. Bi/MoS2: 123 Ω·µm (2021); Sb/MoS2: 0.66 kΩ·µm (2021) [39][217]. Co/hBN/MoS2 (2017): 3.0 kΩ·µm at 1.7 K and 5.3×10^12 cm−2 [228]. Pt/2L-hBN/WSe2 (2020) reports 5.34–72 meV barriers, not Rc [229]; Co–SnS2 (2018) reports sheet resistance, not Rc [230]. Residue/carrier-density confound [228].

Compare only matched Rc definitions/methods, bias, geometry and denominator; Y-function is condition-limited [223]. Plasma-cleaned MoS2 reached 1.5–2 µA/µm, but doping confounds attribution [202]. 2018 Co–SnS2 was ohmic (400 Ω□−1), not Ω·µm Rc [231]; MoS2 memristors are non-FET evidence [183].

MoS₂ 1T: 200–300 Ω·µm at zero gate (2014) [232]; n-BuLi/1T′-MoS₂ Rc 5.2 kΩ at 275 K (2017) [132]; intercalation proxy (2018) [233].

The only quantitative cross-pathway comparison is conditional: TLM-derived, width-normalized on-state Rc at comparable 8–10 nm thickness was 7.5 kΩ·μm for W:MoTe2 edge contact versus 211 kΩ·μm for Cr/Au top contact, so edge was lower [66]. Because this evidence is post-cutoff and lacks matched polarity, temperature, bias, and device date, it cannot support a pre-cutoff ranking; in multilayer MoS2, the proposed edge benefit—every-layer injection, shorter bonds, lower barriers, and stronger orbital overlap—is confounded by geometry, processing, adsorbates, defects, strain, and interface dipoles [184][215][213].

## References

[1] <https://www.nature.com/articles/s41586-021-03472-9> Bi contacts, 2021; Studies; Study; Bi mechanism and device results; Defect sensitivity of Bi contacts; Bi device polarity
[2] <https://doi.org/10.1109/iedm19574.2021.9720609> Alloy contacts, IEDM 2021; Alloys; Study; Statistical alloy-contact study
[3] <https://doi.org/10.1002/adma.202202408> Phase-engineered contact comparison, 2022; Edge comparison; Distorted interface; Contact geometries and their overlap; Comparative contact data; Contact-resist…
[4] <https://sndl.skku.edu/_files/ugd/a7895f_0247d3c4cc3941e7b084d84ef6565297.pdf> In/Au device; Study; Encapsulated In/Au edge-contact device
[5] <https://par.nsf.gov/servlets/purl/10156619> Phase contacts; Comparison; Au-contact comparison
[6] <https://poplab.stanford.edu/pdfs/McClellan-HighCurrentMoS2-nano21.pdf> AlOₓ doping; Study; AlOₓ fabrication and activation; Trapping-versus-doping analysis; Contact-edge injection mechanism; Bias-dependent current and normalizatio…
[7] <https://journal.hep.com.cn/fop/EN/10.1007/s11467-022-1190-1> Electrode and interface strategies; Lateral contact structures; Hole-contact implication; Transferred-electrode comparison; Comparison; Resistance comparison;…
[8] <https://www.researching.cn/articles/OJ2d35faf08d297d90> Phase and doping approaches; Barrier and mobility comparison; Chemical phase-conversion mechanism
[9] <https://doi.org/10.1038/s41699-019-0133-3> Tunneling-contact engineering; Experimental pinning-factor definition; Study; Oxidized-monolayer InSe study; In-versus-Pd depinning response; Processing and te…
[10] <https://doi.org/10.1126/sciadv.1600069> MIGS and van der Waals junctions; 2D-metal junction theory
[11] <https://www.purdue.edu/discoverypark/nanotechnology/membership/Appenzeller/research_2d_sbfet.html> Temperature-dependent MoS₂ contact analysis; Study; Experimental metal comparison
[12] <https://www.nature.com/articles/s41586-019-1052-3> Study; In/Au interface characterization
[13] <https://www.nature.com/articles/s41699-020-00191-z> Study; In/MoS₂ transport mechanism
[14] <https://doi.org/10.1109/iedm19574.2021.9720608> Study; Sb electrical and thermal results; Semimetal thermal comparison; Sb–Bi modeling context
[15] <https://docs.lib.purdue.edu/nanopub/1317/> Sc-contact device
[16] <https://djena.engineering.cornell.edu/papers-new/2013/liu2013role.pdf> Metal selection in monolayer WSe₂
[17] <https://doi.org/10.1038/s41586-022-05134-w> Study; Deposition-rate and heating experiment; Metal-specific reactions and controls
[18] <http://ciqm.harvard.edu/uploads/2/3/3/4/23349210/leegh2015.pdf> Study; Hybrid-device fabrication
[19] <https://doi.org/10.1103/physrevx.4.031005> Atomistic top-versus-edge study
[20] <https://djena.engineering.cornell.edu/papers/2012/iedm12_2d_contacts.pdf> Calculated Au–MoS₂ contact barriers
[21] <https://digital.csic.es/bitstream/10261/283465/1/Conde_ACSAMI_2022_editorial.pdf> Layer-resolved injection geometry; Cr/Au versus Ti/Au fabrication; Annealing and contact bonding
[22] <https://doi.org/10.1038/s41598-018-30867-y> Study; Structural phase descriptions; Intercalation-derived phase stability; Forming-gas conversion and stability; Process-window evidence; Phase-region transp…
[23] <https://bdt.semi.ac.cn/library/upload/2013/10/9111548595.pdf> Study; Selective potassium doping; K diffusion and threshold effects; K-doping extraction assumption
[24] <https://doi.org/10.1002/adma.202200885> Study; Fe-doping mechanism and synthesis
[25] <https://www.mdpi.com/1996-1073/15/17/6169> Reported example; Polyethyleneimine example; Study; TiO₂ thickness experiment; Measured thickness dependence; Barrier extraction and resistance interpretation
[26] <https://eezfan.home.ece.ust.hk/Papers/Paper114.pdf> Study; h-BN thickness experiment; h-BN interface mechanism; Temperature-dependent h-BN-contact device
[27] <https://doi.org/10.1002/smll.202105753> Study; WS₂ tunneling-contact comparison
[28] <https://doi.org/10.1109/iedm.2014.7046986> TiO₂ depinning demonstration, 2014
[29] <https://doi.org/10.1109/led.2022.3149410> Y-function extraction assessment
[30] <https://www.nature.com/articles/nmat4080>
[31] <https://www.mdpi.com/2079-9292/9/12/2110>
[32] <https://doi.org/10.1103/physrevx.4.031005>
[33] <https://pubs.acs.org/nalefd/article/22/17/7094/1489480/Lowering-Contact-Resistances-of-Two-Dimensional>
[34] <https://theses.hal.science/tel-01637267v1/file/CAO_2017_diffusion.pdf>
[35] <https://www.nature.com/articles/s41699-018-0059-1>
[36] <https://pubs.acs.org/doi/full/10.1021/acsnano.5b07942>
[37] <https://doi.org/10.1109/iedm19574.2021.9720609>
[38] <https://doi.org/10.1063/1.4947468>
[39] <https://par.nsf.gov/servlets/purl/10294455>
[40] <https://uwspace.uwaterloo.ca/items/2d4bc9c7-e21e-46e8-b891-b3486c2f46b7>
[41] <https://www.sciencedaily.com/releases/2013/10/131031142740.htm>
[42] <https://sentech.com/news/what-is-plasma-etching/>
[43] <https://www.nature.com/articles/s41928-022-00783-1>
[44] <https://pubs.rsc.org/en/content/articlelanding/2017/NR/C7NR02487H>
[45] <https://ieeexplore.ieee.org/abstract/document/9372028>
[46] <https://arxiv.org/pdf/2105.10792>
[47] <http://www.cityu.edu.hk/phy/appkchu/Publications/2022/22.90.pdf>
[48] <https://hanwang6.github.io/Lab_Website/iedm_2022.pdf>
[49] <https://doi.org/10.1021/acsnano.5b02399>
[50] <https://link.springer.com/article/10.1007/s40820-025-01898-8>
[51] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10873265/>
[52] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9609734/>
[53] <https://pubs.rsc.org/en/content/articlehtml/2020/nh/c9nh00743a>
[54] <https://iopscience.iop.org/article/10.1088/2053-1583/ab2c44/ampdf>
[55] <https://onlinelibrary.wiley.com/doi/10.1002/inf2.12491>
[56] <https://doi.org/10.1088/2053-1583/ad4044>
[57] <https://www.imec-int.com/en/articles/introducing-2d-material-based-devices-logic-scaling-roadmap>
[58] <https://phantomsfoundation.com/GRAPHENEFORUS/2019/Abstracts/grapheneforus2019_Yang_Zheng_29.pdf>
[59] <https://doi.org/10.1088/2053-1583/aba449>
[60] <https://iopscience.iop.org/article/10.1088/2053-1583/ae2b82>
[61] <https://www.mdpi.com/1996-1073/15/17/6169>
[62] <https://doi.org/10.1021/acs.nanolett.1c00180>
[63] <https://pubs.acs.org/doi/10.1021/acsnano.9b05965>
[64] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6194502/>
[65] <https://www.sciencedirect.com/topics/physics-and-astronomy/metal-interface>
[66] <https://doi.org/10.1002/smsc.202500320>
[67] <https://www.intechopen.com/chapters/1214953>
[68] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9529977/>
[69] <https://www.nature.com/articles/s41928-019-0245-y>
[70] <https://djena.engineering.cornell.edu/papers/2015/jeds15_mingda_thintfet.pdf>
[71] <https://www.ias.ac.in/public/Volumes/boms/044/00/0223.pdf>
[72] <https://doi.org/10.1021/acsnano.6b02879>
[73] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12061291/>
[74] <https://pubs.acs.org/ancac3/article/12/6/6292/746473/Schottky-Barrier-Height-Engineering-for-Electrical>
[75] <https://pubs.acs.org/doi/10.1021/acsanm.0c02302>
[76] <https://doi.org/10.1039/c4nr05725b>
[77] <https://pubs.rsc.org/en/content/articlehtml/2024/nh/d4nh00030g>
[78] <https://franklin.pratt.duke.edu/files/u9/Papers/Cheng-NanoLett-2019.pdf>
[79] <https://www.academia.edu/170639072/Geometry_dependent_Halogen_Contact_Doping_in_W_WSe_2_W_Field_Effect_Transistors_A_First_Principles_Quantum_Transport_Study>
[80] <https://arxiv.org/abs/1809.03181>
[81] <https://link.springer.com/article/10.1007/s12274-021-3504-y?code=b1bcdd77-8c7b-4d7e-9230-149e06c49d6c&error=cookies_not_supported>
[82] <https://onlinelibrary.wiley.com/doi/10.1002/adma.201804422>
[83] <https://onlinelibrary.wiley.com/doi/10.1002/advs.202100102>
[84] <https://www.cell.com/cell-reports-physical-science/fulltext/S2666-3864(20)30324-6>
[85] <https://doi.org/10.1021/acsanm.3c00166>
[86] <https://www.nature.com/articles/s41699-023-00402-3>
[87] <https://www.nature.com/articles/s41467-022-32582-9>
[88] <https://www.researching.cn/articles/OJ2d35faf08d297d90>
[89] <https://par.nsf.gov/servlets/purl/10396678>
[90] <https://www.research-collection.ethz.ch/bitstreams/6c6f0209-69ac-47cb-92e5-77b5d170ac3b/download>
[91] <https://arxiv.org/html/1902.05506v3>
[92] <https://par.nsf.gov/servlets/purl/10066926>
[93] <https://mdr.nims.go.jp/rails/active_storage/blobs/proxy/eyJfcmFpbHMiOnsiZGF0YSI6IjQyYWNjNjFlLWE5MDAtNDEyNC1iNGVkLTM5ZDFmYzc2YzQ3MyIsInB1ciI6ImJsb2JfaWQifX0=--aef624ea1675b8cab73a033383b12ddcaa35fdf5/chen-et-al-2024-locally-doped-transferred-contacts-for-wse2-transistors.pdf>
[94] <https://par.nsf.gov/biblio/10710130-impact-contact-deposition-process-interface-engineering-monolayer-wse2-fets>
[95] <https://arxiv.org/pdf/2212.03003>
[96] <https://doi.org/10.1038/s41467-020-17784-3>
[97] <https://eprints.gla.ac.uk/289413/1/289413.pdf>
[98] <http://nano.eecs.berkeley.edu/publications/NanoLett_2012_WSe2_MLFETs.pdf>
[99] <https://doi.org/10.1088/0957-4484/27/34/342002>
[100] <https://doi.org/10.1002/aelm.202200513?urlappend=%3Futm_source%3Dresearchgate.net%26utm_medium%3Darticle>
[101] <https://doi.org/10.1002/adfm.202402474>
[102] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11314317/>
[103] <https://fsrc.nycu.edu.tw/Conference/wp-content/uploads/2024/08/19theme3-%E7%B0%A1%E7%B4%8B%E6%BF%B1-%E8%94%A1%E6%98%95%E9%9C%96.pdf>
[104] <https://www.nature.com/articles/s41467-022-35760-x>
[105] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11315877/>
[106] <https://doi.org/10.1109/iedm45625.2022.10019374>
[107] <https://research.tsmc.com/english/research/logic/low-dimensional-material/publish-time-1.html>
[108] <https://openscholarship.wustl.edu/cgi/viewcontent.cgi?article=1895&context=eng_etds>
[109] <https://doi.org/10.1002/adfm.201801204>
[110] <https://engineering.purdue.edu/~yep/Papers/APL%20Materials_Contact_Du.pdf>
[111] <https://ieeexplore.ieee.org/abstract/document/10019374>
[112] <https://pubs.acs.org/doi/abs/10.1021/acsnano.7b02858>
[113] <https://poplab.stanford.edu/pdfs/BerGrady-ComponentsContactResistance-aem23.pdf>
[114] <https://poplab.stanford.edu/pdfs/DasMcClellan-2DFETs-nelec21.pdf>
[115] <https://docs.lib.purdue.edu/cgi/viewcontent.cgi?article=2879&context=open_access_dissertations>
[116] <https://doi.org/10.1039/d3na00387f>
[117] <https://google.iopscience.iop.org/article/10.1088/1361-6463/acc53f>
[118] <https://aaltodoc.aalto.fi/items/53120723-2c79-434d-a286-bfdba22c6198>
[119] <https://doi.org/10.1360/tb-2023-0051>
[120] <https://www.semanticscholar.org/paper/Uncovering-the-Different-Components-of-Contact-to-Ber-Grady/73a8c200be10d5affcc0c8d5122eb62dd1d285d8>
[121] <https://www.nist.gov/news-events/news/2022/06/road-tiny-transistors-how-flat-flat>
[122] <https://doi.org/10.1109/iedm19574.2021.9720608>
[123] <https://doi.org/10.1038/srep21786>
[124] <https://doi.org/10.1103/physrevb.89.245403>
[125] <https://pubs.acs.org/doi/10.1021/nl304777e>
[126] <https://doi.org/10.1002/aelm.202300277>
[127] <https://pubs.acs.org/doi/pdf/10.1021/acs.nanolett.6b01309>
[128] <https://arxiv.org/pdf/2412.18385>
[129] <https://ciqm.harvard.edu/uploads/2/3/3/4/23349210/shensu2021.pdf>
[130] <https://doi.org/10.7567/jjap.56.04cb02>
[131] <https://doi.org/10.1002/cjoc.202100876>
[132] <https://pure.tudelft.nl/ws/files/37937128/PhysRevB.96.235436.pdf>
[133] <https://doi.org/10.1038/s41467-023-36715-6>
[134] <https://doi.org/10.1109/led.2015.2501323>
[135] <https://api.repository.cam.ac.uk/server/api/core/bitstreams/1e3ef4ac-5159-4599-9c6a-e580b025bc00/content>
[136] <https://www.purdue.edu/discoverypark/nanotechnology/membership/Appenzeller/research_2d_sbfet.html>
[137] <https://hanwang6.github.io/Lab_Website/iedm_2021.pdf>
[138] <https://doi.org/10.1038/nmat4452>
[139] <https://arxiv.org/pdf/1605.03972>
[140] <https://pubs.acs.org/doi/10.1021/acsaelm.8b00059>
[141] <https://www.osti.gov/servlets/purl/1986277>
[142] <https://www.repository.cam.ac.uk/items/29198282-f390-4a70-8f70-cb142f85f14c>
[143] <https://doi.org/10.1038/s41467-022-35760-x>
[144] <https://www.eurekalert.org/news-releases/1141543>
[145] <https://link.springer.com/article/10.1007/s40820-023-01273-5>
[146] <https://doi.org/10.1002/advs.202301400>
[147] <https://doi.org/10.21203/rs.3.rs-2508636/v1>
[148] <https://www.repository.cam.ac.uk/bitstreams/cd973f37-770f-447d-937e-841633c9ed92/download>
[149] <https://www.nature.com/articles/s41699-022-00327-3>
[150] <http://www.nature.com/articles/s41586-019-0892-1/figures/5>
[151] <https://pubs.aip.org/aip/apm/article/2/9/092516/150649/Metallic-1T-phase-source-drain-electrodes-for>
[152] <https://www.sigs.tsinghua.edu.cn/en/2020/1223/c1303a23922/page.htm>
[153] <http://www.commonorganicchemistry.com/Common_Reagents/n-Butyl_Lithium/n-Butyl_Lithium.htm>
[154] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10324635/>
[155] <https://doi.org/10.15541/jim20210658>
[156] <https://preview-www.nature.com/articles/s41699-023-00402-3>
[157] <https://www.nature.com/articles/s41467-023-41363-x>
[158] <https://www.nature.com/articles/s41586-022-05431-4>
[159] <https://arxiv.org/pdf/2406.02008>
[160] <https://www.osti.gov/servlets/purl/2586665>
[161] <https://www.jos.ac.cn/article/doi/10.1088/1674-4926/41/7/071901>
[162] <https://doi.org/10.1038/s41467-022-32582-9>
[163] <https://doi.org/10.1088/2053-1583/ab2c44>
[164] <https://arxiv.org/html/2212.03003v1>
[165] <https://pubs.aip.org/aip/jap/article/132/22/224305/2838034/Comparison-of-contact-metals-evaporated-onto>
[166] <https://www.nature.com/articles/s41586-022-05431-4?code=c58c21ea-766b-4925-8952-e941e978d1d5&error=cookies_not_supported>
[167] <http://poplab.stanford.edu/pdfs/English-MoS2contactsUHV-nl16.pdf>
[168] <https://pmc.ncbi.nlm.nih.gov/articles/PMC13470917/>
[169] <https://pubs.acs.org/doi/10.1021/acsami.0c09541>
[170] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10375162/>
[171] <https://experts.umn.edu/en/publications/visualizing-the-metal-mo-s2-contacts-in-two-dimensional-field-eff/>
[172] <https://www.nature.com/articles/s41586-021-03472-9>
[173] <https://digitalcommons.wayne.edu/oa_dissertations/1523>
[174] <https://doi.org/10.48550/arxiv.2210.11897>
[175] <https://kummelgroup.ucsd.edu/pubs/papers_2020/Bang%20-%20MoS2%20Contract%20Engineering%20Advanced%20Functiional%20Mat%202019.pdf>
[176] <https://docs.lib.purdue.edu/cgi/viewcontent.cgi?article=2313&context=nanopub>
[177] <https://cora.ucc.ie/items/5edd4938-1a81-433d-9ba9-36bc7a8d9acf>
[178] <https://doi.org/10.1109/jeds.2019.2897167>
[179] <https://iris.cnr.it/handle/20.500.14243/411260>
[180] <https://doi.org/10.1017/s1431927618008279>
[181] <https://www.sciengine.com/sci-open/api/v1/open/file/pdf/99D62A32F6CE42569531C678974D550A>
[182] <https://www.sciopen.com/local/article_pdf/10.1007/s12274-023-5946-x.pdf>
[183] <https://www.nature.com/articles/s41467-022-30519-w>
[184] <https://pubs.acs.org/aamick/article/14/37/42328/373420/Edge-Contact-MoS2-Transistors-Fabricated-Using>
[185] <https://doi.org/10.1002/aelm.202101169>
[186] <https://doi.org/10.1143/jjap.47.1435>
[187] <https://doi.org/10.1002/bltj.2184>
[188] <https://hal.science/hal-00397110v1/file/lill2008.pdf>
[189] <https://pmc.ncbi.nlm.nih.gov/articles/PMC13106841/>
[190] <https://doi.org/10.1002/smll.202200882>
[191] <https://pubs.acs.org/nalefd/article/19/10/6914/511694/One-Dimensional-Edge-Contacts-to-a-Monolayer>
[192] <https://www.academia.edu/112480753/A_Fermi_Level_Pinning_Free_1D_Electrical_Contact_at_the_Intrinsic_2D_MoS2_Metal_Junction>
[193] <https://doi.org/10.1088/1361-6528/abbb4a>
[194] <https://www.cell.com/iscience/fulltext/S2589-0042(22)01432-8>
[195] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11739435/>
[196] <https://pubs.aip.org/aip/adv/article/11/4/045312/994340/One-dimensional-edge-contact-to-encapsulated-MoS2>
[197] <https://doi.org/10.26434/chemrxiv-2022-6lkj0>
[198] <https://doi.org/10.1021/acs.nanolett.9b02166>
[199] <https://wcnt.wisc.edu/wp-content/uploads/sites/882/2018/12/Etching.pdf>
[200] <https://doi.org/10.1117/1.3504697>
[201] <https://doi.org/10.1002/andp.201600410>
[202] <https://doi.org/10.1021/acsaelm.1c00379>
[203] <https://doi.org/10.1002/smll.202206550>
[204] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12644695/>
[205] <https://doi.org/10.1021/jacs.7b05765>
[206] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12561449/>
[207] <https://doi.org/10.1002/adfm.202003688>
[208] <https://doi.org/10.1021/acsaelm.4c01574>
[209] <https://ar5iv.labs.arxiv.org/html/1801.05157>
[210] <https://en.wikipedia.org/wiki/N-Butyllithium>
[211] <https://theses.hal.science/tel-04581358>
[212] <https://www.researchgate.net/publication/352810493_A_contact_resistance_extraction_method_of_2D-FET_technologies_without_test_structures>
[213] <https://par.nsf.gov/servlets/purl/10520950>
[214] <https://arxiv.org/abs/2206.03839>
[215] <https://djena.engineering.cornell.edu/papers/2012/iedm12_2d_contacts.pdf>
[216] <https://doi.org/10.1007/s12274-013-0330-x>
[217] <https://ieeexplore.ieee.org/document/9720608>
[218] <https://pubs.acs.org/aamick/article/10/39/33450/809946/High-Performance-InSe-Transistors-with-Ohmic>
[219] <https://doi.org/10.1109/vlsitechnologyandcir46769.2022.9830376>
[220] <https://www.cell.com/matter/fulltext/S2590-2385(22)00322-8>
[221] <https://doi.org/10.1109/ectc.2011.5898485>
[222] <https://arxiv.org/pdf/1406.4492>
[223] <https://doi.org/10.1109/led.2022.3149410>
[224] <https://doi.org/10.1109/vlsit.2014.6894432>
[225] <http://www.npg.nature.com/articles/s41467-022-29449-4.pdf>
[226] <https://www.cityu.edu.hk/phy/appkchu/Publications/2022/22.58.pdf>
[227] <https://par.nsf.gov/biblio/10434932-ab-initio-computational-screening-performance-assessment-van-der-waals-semimetallic-contacts-monolayer-wse2p-type-field-effect-transistors>
[228] <https://ciqm.harvard.edu/uploads/2/3/3/4/23349210/cui_shin2017.pdf>
[229] <https://web.phys.ntu.edu.tw/nanomagnetism/eng/pdf/122-ACS%20Appl.%20Mater.%20Interfaces%2012-18667-2020-Ultralow%20Schottky%20Barriers%20in%20Hexagonal%20Boron%20Nitride-Encapsulated%20Monolayer%20WSe2%20Tunnel%20Field-Effect%20Transistors.pdf>
[230] <https://vandegroeplab.com/wp-content/uploads/2020/07/gong-et-al.-2018-spatially-controlled-doping-of-two-dimensional-sns2through-intercalation-for-electronics.pdf>
[231] <https://web.stanford.edu/group/cui_group/papers/Yongji_Cui_NATNANO_2018.pdf>
[232] <https://hero.epa.gov/reference/4835469/>
[233] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6290021/>
