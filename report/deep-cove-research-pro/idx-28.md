# Energy Recovery in Urban Water Supply Networks: Conventional Micro-hydroturbines versus PATs

**The main finding:** Pump as Turbine systems, or PATs—commercial pumps operated in reverse to generate power—usually offer lower equipment costs, easier procurement, and more readily accessible spare parts. Purpose-built conventional micro-hydroturbines generally offer higher cited peak efficiencies and more integrated hydraulic regulation. Small-turbine best-efficiency references are approximately **85–94%**, compared with commonly reported PAT best-efficiency values of approximately **65–75%**, although individual machines fall outside both generalizations. [1][2]

**The practical choice:** PATs are especially attractive where a standard machine closely matches a persistent excess-pressure resource. Regulated conventional turbines become more attractive when changing demand, pressure-control requirements, or the value of additional annual generation justifies their higher initial cost. In either case, the installation must preserve drinking-water service before optimizing electricity production.

| Requested part | Decisive finding | Practical judgment |
|---|---|---|
| 1. Detailed technology comparison | Conventional BEP references: 85–94%; common PAT references: 65–75% | Compare annual energy and pressure compliance, not peak efficiency alone |
| 2. Advantages and disadvantages | A 2018 comparison cites about €1,800/kW for miniaturized turbines versus up to €350/kW for PAT installation | PAT hardware economics are favorable; complete retrofit costs determine the outcome |
| 3. Turbine parameters and applicability | Impulse machines generally favor free discharge; reaction machines can retain downstream pressure | Screen by hydraulic arrangement before comparing efficiency |
| 4. Installation challenges | Civil works, variable demand, controls, transients, water quality, and grid connection can dominate | Treat the equipment as part of a water-service installation |

The installation figures above are historical literature anchors, not a matched quotation for the same site. [3]

**How the report proceeds:** Part 1 develops the performance, cost, control, longevity, and availability comparisons. Part 2 consolidates their advantages and disadvantages. Part 3 provides the requested turbine catalog and explains its numerical screening estimates. Part 4 connects the principal installation barriers to practical utility decisions. The evidence window extends through early 2024, including the February 2024 water-network study and the March–April 2024 British Hydropower Association guide.

## Part 1 — Detailed Comparison of Conventional Micro-hydroturbines and PATs

### What is being compared in a water network?

**The distinction concerns hydraulic design:** A conventional micro-hydroturbine is purpose-built to extract hydraulic energy. Its runner, casing, and, where provided, guide vanes, nozzles, or adjustable blades are designed for turbine operation. A PAT instead uses an existing pump design: reverse water flow drives the impeller and a suitably configured generator. The centrifugal PATs most frequently discussed here are reaction machines, although axial-flow pumps also have documented turbine applications. [4][5]

**The resource is excess head:** Both technologies can recover energy otherwise dissipated at a pressure-reducing valve, or PRV, a reservoir inlet, or another unavoidable pressure break. The recoverable head is the difference between upstream hydraulic head and the head needed to deliver acceptable downstream service, after other installation losses. It is not the entire upstream pressure. A February 2024 Funchal study explicitly retained existing PRVs downstream of PATs to preserve pressure management. [6]

**Power depends on simultaneous conditions:** For water, the hydraulic power passing through a turbine is approximately:

$$P_h=9.81QH\quad\text{(kW, with }Q\text{ in m³/s and }H\text{ in m).}$$

Here, \(H\) is the head actually extracted across the machine, not the source elevation alone. Electrical output is the hydraulic power multiplied by turbine, generator, and power-electronics efficiencies, less auxiliary consumption. The experimental Servigliano study uses this hydraulic-to-shaft energy balance to characterize a PAT. [7]

**Recovery should follow pressure optimization:** In a gravity-fed system, a pressure break may be unavoidable because of topography. In a pumped system, excess pressure may instead be partly avoidable through improved pump scheduling or speed control. Installing a turbine to recover unnecessarily generated pumping head is less efficient than avoiding that pumping input. The relevant comparison therefore includes direct pumping optimization as well as energy recovery. [3]

### Best-efficiency-point performance

**Purpose-built machines have higher references:** ESHA’s guide gives typical best-efficiency-point, or BEP, values of 85% for Turgo, 89–90% for Pelton, 91–93% for regulated Kaplan, and 94% for Francis turbines. BEP means the operating condition at which a particular machine achieves its highest efficiency; it does not necessarily coincide with maximum discharge or nameplate power. [1]

| Conventional turbine family | Cited best efficiency | Relevant interpretation |
|---|---:|---|
| Pelton | 89–90% | Small-turbine reference; nozzle configuration matters |
| Turgo | 85% | ESHA reference; other tests report higher values |
| Single-regulated Kaplan | 91% | One adjustable hydraulic control set |
| Double-regulated Kaplan | 93% | Adjustable guide vanes and runner blades |
| Francis | 94% | Peak reference, not guaranteed micro-scale performance |

**Micro-scale results can be lower:** Purpose-built equipment does not automatically deliver the upper values in that table. A 2018 drinking-water study summarized experimental axial microturbines reaching approximately 68% hydraulic efficiency at 4–9 m head and another reaching 64% at 3.4 m. Its own counter-rotating prototype targeted more than 85% hydraulic efficiency, which is a design objective rather than the measured performance of those earlier machines. [8]

**PAT performance depends strongly on selection:** A 2022 water-network paper summarizes maximum PAT BEP efficiencies around 65–75%, while the 2018 *Fluids* discussion cites approximately 60–70%. These are useful central references, but individual pump geometry, size, operating speed, and measurement boundary materially affect the result. [2][3]

| PAT evidence | Reported efficiency | Measurement or analysis basis |
|---|---:|---|
| Common literature reference | 65–75% at BEP | Pump-dependent literature synthesis |
| Movitec VF-90-1 | 75% hydraulic; 69% overall | Laboratory characterization |
| Granville PAT A and PAT B | 31% and 32% at BEP | Acceptance tests of small multistage units |
| Mixed-flow PAT experiment | 80.84% maximum | Reported experimental peak |
| Municipal variable-speed case | 62–64% | Network simulation, not field measurement |

The Movitec values come from Kramer, Terheiden, and Wieprecht’s 2018 study; the other machine-specific results illustrate the breadth of PAT performance rather than a single transferable efficiency distribution. [9][2][10][11]

**Efficiency boundaries change the comparison:** Hydraulic-to-shaft efficiency measures useful shaft power divided by hydraulic power. Overall, or water-to-wire, efficiency additionally includes generator and conversion losses. For the tested Movitec PAT, the turbine BEP occurred at 31.4 L/s and 37.1 m head, with reported hydraulic and overall efficiencies of 75% and 69%, respectively. [9]

**A worked example clarifies scale:** Those Movitec operating conditions imply approximately 11.43 kW of hydraulic input, calculated as \(9.81\times0.0314\times37.1\). Applying the reported efficiencies gives approximately 8.57 kW at the shaft and 7.89 kW electrical output. These are calculations from that machine’s reported BEP, not additional test measurements.

**Reverse operation changes the BEP:** The same Movitec pump had a pump-mode BEP of 21.9 L/s and 23.4 m, appreciably below its turbine-mode BEP. Thus, selecting a pump whose ordinary pumping curve appears to match a water-network duty can still produce a poor turbine match. Pump-to-turbine conversion methods are selection aids, not substitutes for the relevant reverse-mode characteristic. [9]

**The resulting efficiency judgment:** Regulated conventional turbines generally offer the stronger peak-efficiency proposition. That judgment changes when the conventional alternative is a modest-efficiency low-head microturbine, or when a well-matched PAT demonstrates strong performance over the actual operating range. The correct comparison is between candidate machines and complete generating packages, not the highest published percentage for each technology.

### Partial-load efficiency and changing urban demand

**Regulation broadens the useful operating range:** Conventional turbines can adjust water admission or blade geometry as flow changes. Pelton turbines use nozzle control and, in multi-jet arrangements, selective jet admission; Kaplan turbines can adjust guide vanes and runner blades. These mechanisms help maintain favorable flow angles and reduce the efficiency penalty of departing from one nominal condition. [1]

| Conventional configuration | Cited low-flow operating reference | Consequence for variable demand |
|---|---:|---|
| Multi-jet Pelton | Around 10% of design flow | Strong low-flow accommodation in suitable arrangements |
| Pelton, general ESHA reference | Around 20% of rated discharge | Broad satisfactory operating range |
| Double-regulated Kaplan | Around 20% | Broad range through coordinated adjustment |
| Single-regulated Kaplan | Around 33% | Less flexible than double regulation |
| Francis | Around 50% acceptable; instability possible below 40% | Less attractive for prolonged deep partial load |
| Crossflow | Broad range; limited efficiency decline with falling flow | Favorable where discharge varies substantially |

These percentages describe operating thresholds or qualitative acceptable-efficiency regions, not identical efficiency percentages at each threshold. [1][4][12]

**PATs have a narrower natural match:** A standard PAT generally has neither adjustable guide vanes nor adjustable runner blades. At fixed rotational speed, changing network demand moves its operating point away from BEP, often reducing efficiency sharply. Delgado’s 2018 experimental thesis identifies this decline, together with the difficulty of obtaining reverse-mode characteristic curves, as a central implementation problem. [13]

**A numerical curve shows the effect:** Alberizzi and colleagues’ Laives analysis provides a modeled PAT curve with a BEP efficiency of 69%. At 8.86 m³/h—approximately 62% of its stated BEP flow of 14.35 m³/h—the modeled efficiency was 38%. The accompanying head also changed, so these values describe movement along a machine characteristic rather than a controlled comparison at constant head. [14]

| Modeled flow, m³/h | Flow relative to stated BEP | Head, m | Hydraulic-to-shaft efficiency |
|---:|---:|---:|---:|
| 8.86 | 62% | 12.50 | 38% |
| 11.80 | 82% | 17.52 | 59% |
| 14.35 | 100% | 22.80 | 69% |
| 17.71 | 123% | 28.91 | 66% |
| 20.66 | 144% | 35.26 | 64% |

The relative-flow percentages are calculated from the tabulated discharges. They show that this modeled machine’s efficiency penalty was markedly steeper below BEP than moderately above it.

**Some partial-load points produce no electricity:** In the Granville energy-booster tests, the smaller PAT ceased producing positive power below 1.8 L/s. The installation used two small Caprari multistage pumps and alternative single-unit, parallel-unit, and bypass states to accommodate a measured flow range of 0–12 L/s. Its optimized recovery was approximately 9.68 kWh/day from 61.1 kWh/day available, or a calculated 15.8%, reported as about 16%. [2]

**Operating hours can mislead:** Granville’s bypass-only state occupied approximately 27% of operating time, yet flow below the 1.8 L/s production threshold represented only approximately 5% of available energy. Consequently, eliminating every non-generating hour would not necessarily justify a more expensive installation. The economically important question is how much energy is lost, not simply how often the turbine is stopped. [2]

**Variable speed can recover flexibility:** Changing speed shifts a PAT’s characteristic curves and can improve its match to changing flow and available head. In the 2023 municipal-network simulation by e Souza, Mesquita, and Blanco, variable-speed operation maintained efficiencies of approximately 62–64% while satisfying the pressure and throughput required from the original control valves. Constant-speed operation behaved appropriately only near BEP in that case. [11]

**BEP tracking is not the sole objective:** The Laives comparison demonstrates why maximizing instantaneous machine efficiency can fail to maximize recovered energy. Keeping the PAT near BEP while bypassing higher flows produced only a small energy improvement. A strategy accepting modest off-design losses while processing more water increased modeled recovery substantially. [14]

| Laives strategy | Downstream pressure | Reported recovery, kWh/year | Change from baseline | Reported annual electricity value |
|---|---:|---:|---:|---:|
| Fixed-speed flow control | 4 bar | 4,637 | Baseline | €979 |
| Flow control plus BEP speed tracking | 4 bar | 4,706 | +1.5% | €994 |
| Advanced speed and flow control | 4 bar | 5,699 | +22.9% | €1,204 |
| Speed control with lower pressure setting | 3.5 bar | 6,307 | +36.0% | €1,332 |

The source’s electricity-value calculation uses €0.22/kWh and 96% converter efficiency; for example, \(4,637\times0.96\times€0.22\approx€979\). The fourth strategy changes the water-service pressure setting as well as the operating strategy, so it is a different hydraulic case.

**Annual energy is the decision metric:** The relevant calculation sums output over the demand record, using simultaneous flow, available head, machine efficiency, bypass operation, and downtime. A machine with a lower BEP efficiency can outperform a higher-efficiency alternative if it captures substantially more of the usable hydraulic resource. Conversely, a cheap PAT selected around a brief demand peak can spend most of the year poorly matched.

**The partial-load takeaway:** Favor a regulated conventional turbine when wide variability contains substantial recoverable energy; favor a PAT when the measured duty remains near a suitable operating region or when justified external control produces a competitive annual result.

### Procurement, installation, and maintenance costs

**PATs have a genuine hardware advantage:** Their cost advantage follows principally from mass production, standard sizes, and established pump-component supply chains. Postacchini and colleagues describe lower prime cost and easier, cheaper maintenance than conventional turbine applications. Marini and colleagues similarly identify short delivery times, easy installation, and lower maintenance costs. [7][15]

**Procurement needs a package boundary:** Buying a pump is different from buying a generating installation. The latter also requires a generator or suitably configured motor-generator, coupling, frame, protection, switchgear, instrumentation, and possibly a frequency converter. Canyon Hydro’s pump-turbine package description explicitly includes such equipment, illustrating why bare-machine prices and complete package prices should remain separate. [16]

| Cost element | Conventional micro-hydroturbine | PAT | Basis |
|---|---|---|---|
| Equipment procurement | US$1,000–2,000/kW screening proxy | US$1,000–2,000/kW standardized-package anchor | EPRI 2011 package estimate |
| Equipment installation | US$500–1,000/kW estimate | US$500–1,000/kW shared installation proxy | 50% of the package range |
| Complete project capital | US$2,000–8,000/kW broad screen | US$2,000–8,000/kW broad screen | EPRI reconnaissance estimate |
| Historical installation comparison | About €1,800/kW | Up to about €350/kW | Literature figures cited in 2018 |
| Annual system O&M | 1–4% of installed capital, planning proxy | 1–4% as a shared system-level sensitivity | IRENA small-hydro benchmark |

The EPRI estimate covers turbine, generator, and controls below 100 kW; its detailed assumptions refer to Cornell-type inline equipment and induction generation. It is therefore especially relevant to standardized pump-based packages, while its use for bespoke conventional turbines is a screening proxy. The installation estimate is \(0.5\times US\$1,000–2,000=US\$500–1,000/kW\). [4]

**The historical euro comparison is directional:** The approximately €1,800/kW conventional and €350/kW PAT installation figures support the literature’s low-cost PAT argument. They should not be combined with the separate EPRI dollar estimates to create a single cost breakdown: they come from different references, years, and installation scopes. [3]

**Recurring costs require careful denominators:** IRENA’s 2012 small-hydro table gives annual O&M of 1–4% of installed capital, with broader discussion acknowledging 1–6% or higher for some small projects. Applying its 1–4% table range to installed costs of US$1,300–8,000/kW gives a calculated screening envelope of US$13–320/kW/year in the report’s real 2010-dollar basis. This is a whole-project proxy, not a turbine-specific maintenance quotation. [17]

**PAT economic models use different allowances:** Pugliese and Giugni’s 2022 framework assumes maintenance equal to 5% of PAT-plus-generator cost each year. By contrast, Marini and colleagues’ 2023 HYPER analysis assumes annual costs equal to 15% of total investment, including machinery maintenance or major repairs, labor, and salaries. A smaller percentage of a narrow equipment subtotal can represent a very different allowance from a larger percentage of total installed cost. [18][15]

**Controls can outweigh the pump:** The 2022 selection framework sets electrical and technical equipment, including frequency-modulator procurement and installation, at 300% of PAT-plus-generator cost. Under that model, those two categories alone total four times the PAT-generator subtotal: \(C_{\text{core}}+3C_{\text{core}}=4C_{\text{core}}\). This illustrates why a low pump price does not imply an equally low complete-project price. [18]

**Maintenance advantages are component-specific:** Standard PAT seals, bearings, and replacement pumps can be easier to procure than bespoke turbine parts. However, a PAT installation can still include specialized controls, actuated valves, power electronics, and buried-chamber equipment. Conventional turbines likewise vary: a direct-drive machine with simple regulation has a different maintenance burden from a double-regulated turbine with additional actuators and transmission equipment.

### Whole-life economics and payback

**Reported paybacks vary substantially:** Pre-2024 studies include favorable PAT paybacks below one year, approximately 2.1 years, and 27 months. These are different sites or models, not successive measurements of a common technology benchmark. A utility-reported HydroXS installation provides a useful complete-package counterexample with an expected eight-year payback; it should be treated as commercial in-pipe recovery evidence rather than assigned automatically to either hydraulic category. [3][19][11][20]

| Application or evidence | Reported energy or operation | Payback | Evidence basis |
|---|---|---:|---|
| PAT literature comparison cited in 2018 | Low-cost installation context | Less than 1 year | Secondary literature figure |
| Brazilian actual-network analysis | 4,331 kWh/year for the selected machine | 2.1 years | Model applied to an actual network |
| Municipal network serving 2,500 houses | 270,192 kWh/year across the modeled system | 27 months | Network and financial simulation |
| Skagit Public Utility District HydroXS | 16–18 kW, approximately 20 hours/day | 8 years | Utility-reported expectation |

**The conventional premium needs incremental value:** A conventional turbine is economically preferable when its additional annual energy and other operational benefits outweigh its additional capital, maintenance, and renewal costs. The deciding inputs are the head-flow time series, installed scope, electricity value, pressure-control performance, financing, maintenance, and the chosen evaluation horizon. This condition also determines whether either generating option improves on retaining the PRV.

**Simple payback is only a first test:** For a project with positive annual net benefit, simple payback is initial investment divided by annual electricity value and attributable savings, less recurring costs. It ignores discounting and can obscure replacement expenditure. Net present value, or NPV, discounts future cash flows; it is more informative when comparing a low-cost, replacement-oriented PAT strategy with a higher-cost, longer-lived conventional installation.

**More generation need not mean better economics:** HYPER’s high-head, smooth-demand commercial-pump scenario found that combined hydraulic and electrical regulation generated slightly more energy than hydraulic regulation alone, but produced a lower NPV. The model used a ten-year operating term, a 5% discount rate, electricity sales at €0.159/kWh, and the annual-cost allowance described above. [15]

| PAT regulation layout | Selected pump | Modeled energy, kWh/day | Modeled NPV |
|---|---|---:|---:|
| Hydraulic regulation | Xylem e-NSC 80-250/450 | 565.42 | €186,429 |
| Electrical regulation | Xylem e-NSC 80-250/370 | 490.73 | €155,114 |
| Combined regulation | Xylem e-NSC 80-250/550 | 576.86 | €167,927 |

**The additional control must earn its cost:** In that scenario, combined regulation increased energy by approximately 2.0% over hydraulic regulation, calculated as \(576.86/565.42-1\), while NPV was approximately 9.9% lower. The relevant mechanism is the added investment and operating burden relative to a modest energy increment. It is not evidence that variable speed is inherently uneconomic.

**A cost-energy proxy explains PAT appeal:** The DuoTurbo paper cites an irrigation comparison in which PAT electromechanical equipment cost was 74% lower than site-specific turbines while electricity production was 19% lower. On an indexed basis, PAT equipment cost was 26 against 100 for the conventional alternative, and energy was 81 against 100. Thus, equipment capital per unit of annual output was approximately \(0.26/0.81=0.321\), or 68% lower. [21]

**Balance-of-plant costs dilute that advantage:** As an explicitly conditional calculation using that irrigation relationship, let conventional equipment cost be \(C\), PAT equipment cost \(0.26C\), and identical non-equipment cost \(B\). With PAT energy equal to 81% of conventional energy, PAT retains a lower capital cost per annual energy unit only while \(B<2.89C\), obtained from \((0.26C+B)/0.81<C+B\). Urban installations can depart from both the assumed cost ratio and the assumption of identical civil and control costs, but the calculation shows why inexpensive machinery matters less when the retrofit dominates expenditure.

**The economic takeaway:** PATs usually deserve the first low-cost screening assessment; a conventional turbine should win when its demonstrable annual performance and service advantages repay the complete project premium.

### Pressure regulation capability

**Pressure loss is not pressure regulation:** Any turbine extracts head, but a pressure regulator must keep downstream service within its required range as upstream head and customer demand change. A fixed-speed machine’s head-discharge characteristic does not automatically provide that function. The Funchal methodology identifies the operating point through the intersection of the installation and PAT characteristic curves. [6]

**Conventional machines can regulate internally:** Francis guide vanes regulate inlet flow and incidence, while Kaplan guide vanes and adjustable blades offer additional flexibility. The Wyoming handbook specifically identifies Francis turbines as suitable for inline operation while maintaining downstream pipeline pressure. Pelton nozzle control regulates flow effectively, but its usual atmospheric discharge makes it less suitable for a pressurized distribution main that must retain downstream pressure. [4]

**PAT regulation is mainly external:** Four common operating arrangements distinguish how the installation deals with changing demand. Their performance follows from the complete circuit, not merely from the pump. [6]

| PAT operating mode | Main control equipment | Pressure-management mechanism | Main trade-off |
|---|---|---|---|
| No regulation, NR | Fixed machine and electrical loading | Natural machine-system intersection | Lowest complexity; narrow hydraulic match |
| Hydraulic regulation, HR | Series PRV and regulated bypass | Dissipates residual head or diverts excess flow | Broad service coverage; some energy bypassed |
| Electrical regulation, ER | Variable-speed generator and converter | Shifts the PAT characteristic | Better matching within speed and power limits |
| Combined regulation, HER | Valves, bypass, and variable speed | Coordinates hydraulic and electrical adjustment | Greater flexibility; higher system complexity |

**Hydraulic regulation prioritizes feasible service:** If available excess head exceeds what the PAT extracts, a series PRV dissipates the balance. If routing all demand through the PAT would create too much head loss, the bypass carries part of the flow. Consequently, water service can continue beyond the efficient operating envelope of the generator, although not all available hydraulic energy becomes electricity. [22]

**Electrical regulation has physical boundaries:** Variable speed can move a PAT toward a favorable operating point, but cannot create upstream head, remove generator current limits, or guarantee feasible operation at every demand. In HYPER, electrical-only layouts had less flexibility than hydraulic or combined regulation under the investigated demand patterns. A 2021 comparison across four cases likewise found hydraulic regulation the best energy-installation-cost trade-off. [15][23]

**Successful cases need counterexamples:** The variable-speed municipal study demonstrated valve-like pressure management in its modeled network. In a separate Brazilian actual-network analysis, however, one constant-speed candidate produced negative outlet pressure affecting a district-metered area. Together, these results show that pressure regulation is an outcome of machine selection and control, not an inherent guarantee of PAT operation. [11][19]

**Retaining a PRV can be rational:** The Funchal design placed PATs upstream of existing PRVs, expressly prioritizing adequate supply and leakage control. Retaining this independent pressure-control function can be more valuable than removing every dissipative component. A bypass is still needed where maintenance, obstruction, or high demand would otherwise interrupt delivery. [6]

**The pressure-control takeaway:** Conventional regulated reaction turbines offer more integrated hydraulic adjustment; PATs can deliver comparable network functions when the external regulation and backup arrangement are properly matched to the site.

### Design and operational complexity

**PAT simplicity applies to the core:** A standard pump avoids designing a turbine runner from first principles and provides established manufacturing tolerances and spare parts. However, its reverse-mode BEP, off-design curves, generator compatibility, allowable speed, cavitation behavior, and network control still require engineering. Pérez-Sánchez and colleagues’ 2020 study used an experimental database of 181 PATs to address this selection problem. [24]

**Conventional complexity buys hydraulic adaptability:** Purpose-built equipment can incorporate controls suited to a specified duty. That may reduce dependence on external throttling but adds actuators, mechanisms, and commissioning requirements. Fixed-blade or fixed-nozzle conventional machines are simpler, so “conventional” should not be treated as synonymous with “fully regulated.”

**A prototype illustrates the full system:** DuoTurbo’s purpose-built counter-rotating design uses two runners per stage, independent speed control, permanent-magnet rim generators, converters, and a controller. Its drinking-water layout includes two parallel branches and two PRVs. The prototype reached 59% peak hydroelectric efficiency and 6.5 kW maximum electrical power, demonstrating that sophisticated adaptability can coexist with a system efficiency well below generic turbine-only peak references. [21]

**Operational complexity follows variability:** Stable-flow installations may run with modest intervention, whereas changing demand requires coordination of speed, valves, bypass states, and pressure set-points. Carravetta and colleagues’ proposed urban PAT plant combined two regulating valves, two pressure meters, and automation. More elaborate arrangements add flow measurement, electrical metering, remote communications, and programmable control. [25]

**Automation reduces staffing, not responsibility:** Remote operation can make small installations viable without permanent operators, but staff must still manage alarms, calibration, isolation, maintenance, and safe restart. The engineering burden therefore shifts from continuous attendance toward reliable instrumentation, clear operating logic, and maintainable equipment.

### Expected service life

**Use different horizons for different assets:** A defensible conventional-hydro planning basis is at least 30 years for electromechanical equipment, with refurbishment, and 50 years or more for an appropriately engineered small-hydro system. IRENA identifies normal electromechanical design lives of 30 years or more; the BHA guide describes systems engineerable for 50 years or more. These are sector engineering benchmarks, not a promise that every bearing, seal, actuator, or converter lasts that long. [17][26]

**PAT budgets can use explicit scenarios:** For comparative appraisal, use a ten-year PAT base horizon, matching the 2022 and 2023 economic studies, and a labeled **10–30-year sensitivity range**. Its lower anchor is the studies’ ten-year operating assumption; its upper anchor is IRENA’s generic 30-year electromechanical design-life benchmark, transferred as a maintained-equipment scenario rather than a PAT failure forecast. [18][15]

**Operating experience supports durability assessment:** The Baiona 6 kW axial PAT installation had been operating with SCADA monitoring since July 2019 when its July 2023 paper appeared—approximately four years of installation experience. The conventional DuoTurbo pilot was monitored for one complete year without significant efficiency or vibration drift. These are useful operating records with different devices and durations, not competing whole-life expectancy measurements. [5][21]

**Duty and maintenance determine longevity:** The deciding conditions are water abrasiveness and chemistry, materials, bearing and seal design, cavitation margin, reverse-mode mechanical suitability, frequency of starts and stops, transients, and maintenance quality. The Wyoming handbook warns that repeated PAT switching can stress the turbine, generator, and piping; ESHA separately distinguishes bearing fatigue and lubrication-related failures. [4][1]

**The longevity judgment is conditional:** Conventional hydro has the stronger long-life engineering precedent. PATs have a strong replaceability advantage, but the ten-year economic assumption should not be interpreted as an intrinsic ten-year mechanical limit, nor should a generic hydro design life be treated as demonstrated PAT longevity.

### Market availability

**Standard pumps provide broader procurement choices:** PAT literature consistently identifies many standard pump sizes, numerous manufacturers, short delivery times, and readily accessible spare parts. The remaining selection task is finding a commercial machine whose turbine-mode performance fits the duty. Availability of a suitable pump and availability of a characterized generating package are therefore distinct advantages. [24][15]

| Supplier or product example | Relevant equipment | Evidence of availability | Procurement implication |
|---|---|---|---|
| Canyon Hydro | Pelton, Crossflow, Francis; pump-turbine packages | Components and complete custom systems | Established supply, with site engineering |
| Voith Hydro | Francis, Kaplan, Pelton, bulb/pit families | Established conventional product portfolio | Strong family maturity; scale must fit the project |
| Cornell Pump | Standardized pump-based turbine equipment | Handbook identifies tested turbine-mode products | Potential route to characterized PAT procurement |
| KSB models | Commercial pumps considered as PAT candidates | 145-model database in a 2022 study | Broad screening choice, subject to reverse-mode matching |
| Xylem e-NSC | Commercial pump series | 316 models screened in HYPER | Catalog breadth supports optimization |
| Caprari E4XED models | Small multistage submersible PAT candidates | Named Granville acceptance-tested units | Standard availability does not assure high efficiency |

The supplier descriptions and catalog examples support availability at different scales; they are not market-share rankings. [27][28][4][29][15][2]

**Conventional supply remains well established:** The issue is not whether conventional turbine manufacturers exist, but whether a suitably sized, affordable, pressure-compatible machine is practical for a small urban site. Baiona’s operators explicitly identified high small-turbine cost and limited availability for their hydraulic connection as reasons for selecting a PAT. [5]

**Part 1 takeaway:** PATs generally lead on standardized procurement and equipment economics, while appropriately regulated conventional turbines generally lead on hydraulic adaptability and cited peak efficiency; complete annual performance, pressure compliance, and life-cycle cost decide the installation.

## Part 2 — Summary of Advantages and Disadvantages

### Comparison of Conventional Micro-hydroturbines and PATs

**Performance and control trade-offs:**

| Dimension | Conventional advantages | Conventional disadvantages | PAT advantages | PAT disadvantages |
|---|---|---|---|---|
| BEP efficiency | Established references of 85–94% | Micro-scale axial examples can be 64–68% | Common BEP references of 65–75%; some higher peaks | Small tested units can be near 31–32% |
| Partial-load efficiency | Regulated Pelton and Kaplan offer broad operating ranges | Francis and fixed-blade designs have narrower efficient regions | Speed control or multiple units improve matching | Fixed-speed efficiency can decline sharply below BEP |
| Pressure regulation | Guide vanes, nozzles, and blades provide hydraulic adjustment | Atmospheric impulse discharge complicates pressurized-main use | HR, ER, and HER can achieve required pressure behavior | Standard pumps lack integral flow-regulation mechanisms |
| Design complexity | Purpose-built hydraulic performance and control | Custom sizing and mechanisms increase engineering | Standard pump core simplifies machinery procurement | Reverse-mode prediction and external circuit design remain important |
| Operational complexity | Integrated regulation can reduce external throttling | Actuators, governors, and protection need maintenance | Stable-flow installations can be straightforward | Variable demand adds speed, valve, and bypass coordination |
| Urban-network compatibility | Inline reaction designs can retain downstream pressure | Installation space and transient protection remain demanding | Fits many existing pressure-reduction opportunities | Backup regulation and service bypass often remain necessary |

The performance entries follow the ESHA guide and the experimental and network studies developed in Part 1. [1][2][6]

**Cost, life, and supply trade-offs:**

| Dimension | Conventional advantages | Conventional disadvantages | PAT advantages | PAT disadvantages |
|---|---|---|---|---|
| Procurement | Established complete-package suppliers | Bespoke equipment can carry a premium | Mass-produced pumps and standard components | Generating package costs exceed the bare pump price |
| Installation | Existing pipes can reduce new infrastructure | Historical miniaturized-turbine anchor: about €1,800/kW | Historical PAT anchor: up to about €350/kW | Controls, chambers, and connection can dominate |
| Annual O&M | Generic planning proxy: 1–4% of installed cost | Specialized mechanisms or parts can add expense | Standard spare parts and replacement machines | Models use differing allowances: 5% of core or 15% of investment |
| Whole-life economics | Additional annual energy can repay higher capital | Premium is difficult to justify at small, intermittent sites | Favorable site/model paybacks include below 1–2.25 years | Low procurement cost does not guarantee positive NPV |
| Expected service life | Generic core benchmark ≥30 years; engineered system ≥50 years | Component renewals remain part of long-life operation | Replacement-oriented strategy uses standard equipment | Use explicit 10–30-year appraisal sensitivity, not an assumed failure age |
| Market availability | Mature turbine families and suppliers | Small pressure-compatible units may be custom | Many standard sizes and broad pump supply chains | Turbine-mode characterization still governs suitability |

The dollar procurement benchmark for both columns is the shared US$1,000–2,000/kW equipment-package screen discussed in Part 1; the euro figures describe the separate historical installation comparison. [4][3][17][26]

**Part 2 takeaway:** The strongest PAT advantages concern standard hardware and supply chains; the strongest conventional-turbine advantages concern purpose-built hydraulic performance, provided that the selected configuration actually includes the regulation the site needs.

## Part 3 — Turbine Technical Parameters and Applicability

### Technical Parameters and Applicability of Various Turbine Types

**The strongest application distinction comes first:** Reaction machines are generally the more direct candidates for closed, pressurized mains requiring downstream residual pressure. Conventional impulse machines are often better suited to discharge into a reservoir or another pressure break. Specialized inline configurations can modify this distinction, but retaining pressure must be demonstrated for the actual arrangement. [4]

**The catalog uses explicit screening values:** “E” denotes an estimate, transferred family proxy, or conditional power-equivalent calculation. BEP references populate the efficiency column where they are the strongest quantitative anchor. A “power screen” gives the discharge corresponding to a hypothetical 5–100 kW shaft-power band, using the stated head and efficiency bounds; it measures power equivalence, not the manufacturing limits of every turbine in the family.

**Impulse turbine families:**

| Name | Type | Applicable Head Range, m | Applicable Flow Rate Range, m³/s | Design Point Efficiency Range, % | Pressure regulation capability |
|---|---|---:|---:|---|---|
| Pelton | Impulse | 50–1,500 E, high-head screen | 0.00038–0.229 E, power screen | 89–90 BEP reference | Nozzles regulate admission; usually atmospheric discharge |
| Turgo | Impulse | 15–300 | 0.0019–0.80 E, power screen | 85–90 contextual references | Jet admission regulates flow; ordinary arrangement favors free discharge |
| Crossflow / Banki–Michell | Impulse | About 1.8–198 | About 0.005–4.96 | 75–80 E, micro-hydro proxy | Segmented admission accommodates flow changes; inline version needs pressure-compatible design |

**Pelton’s head screen is estimated:** Its lower screening anchor uses the BHA high-head category above 50 m, combined with the handbook’s high-head Pelton preference. Its upper anchor is Voith’s reported large custom Pelton application up to 1,500 m. This deliberately combines a site-classification threshold with a family product limit rather than treating either as a universal micro-Pelton boundary. [26][4][28]

**Turgo has several documented operating contexts:** Mashkour’s 2019 thesis gives 15–300 m net head, approximately 87% operational efficiency, and up to 90% in factory or laboratory tests. ESHA’s separate best-efficiency reference is 85%. A 2023 review also summarizes experimental low-head Turgo results of 87% at 1 m and 91% at 3.5 m, showing that specialized designs can operate beyond the usual medium-head screening band. [30][1][12]

**Crossflow values span different sizes:** The handbook gives 6–650 ft head and 1.5–175 ft³/s discharge, converting to approximately 1.8–198 m and 0.042–4.96 m³/s. The catalog’s lower discharge anchor comes from smaller reported units operating at 5–50 L/s and 5–20 m head. Its 75–80% efficiency entry is explicitly a micro-hydro screening proxy from the BHA guide, while the type-specific evidence supports broad partial-flow performance and lower peak efficiency than Kaplan or Francis. [4][12][26]

**Conventional reaction turbine families:**

| Name | Type | Applicable Head Range, m | Applicable Flow Rate Range, m³/s | Design Point Efficiency Range, % | Pressure regulation capability |
|---|---|---:|---:|---|---|
| Francis | Reaction | Generally 15–750 | 0.00072–0.731 E, power screen | 93–94 peak reference | Adjustable wicket gates; documented inline pressure maintenance |
| Kaplan, double-regulated | Reaction | 3.05–19.81 handbook band | 2.83–29.73 handbook band | About 93 BEP reference | Adjustable guide vanes and blades provide broad regulation |
| Semi-Kaplan | Reaction | 3.05–19.81 E, Kaplan proxy | 0.20–1.495 documented case interval | About 91, single-regulated proxy | One adjustable control set; narrower range than full Kaplan |
| Fixed-blade propeller | Reaction | 3.4–9 E, axial proxy | 0.083–4.68 E, power screen | 64–68 E, axial-test proxy | Fixed geometry; external valves or speed control govern adaptation |
| Bulb/pit/S axial arrangement | Reaction | 3.05–30 E, family screen | 2.83–29.73 E, Kaplan proxy | 91–93 E, regulated-Kaplan proxy | Capability depends on guide-vane and blade configuration |

**Francis covers a broad family:** IIT Roorkee’s selection guidance gives generally 15–750 m head and approximately 40–105% of rated discharge, with instability possible below 40%. Its 93–94% peak-efficiency discussion concerns modern designs within the stated 25 MW capacity range, so the catalog uses it as a family reference. The estimated discharge range translates the micro-power band into hydraulic flow rather than importing large-unit discharge limits. [31]

**Kaplan’s quoted band is a handbook example:** Converting 10–65 ft and 100–1,050 ft³/s gives 3.05–19.81 m and 2.83–29.73 m³/s. Voith describes a broader primary application up to 50 m and technical product data up to 90 m, confirming that the handbook band is not the family’s absolute limit. For urban micro-sites with much smaller discharge, a scaled axial microturbine is usually a more relevant comparison than a full-sized low-head Kaplan installation. [4][28]

**Semi-Kaplan trades flexibility for simplicity:** The term covers a Kaplan variant with only adjustable guide vanes or only adjustable runner blades. The approximately 91% efficiency anchor follows ESHA’s single-regulated Kaplan reference, while the head band transfers the handbook Kaplan envelope. A documented Rebolluelo irrigation installation had 0.20 m³/s minimum startup flow and 1.495 m³/s nominal flow; this is a concrete startup-to-rated interval for one machine, not an urban-network class boundary. [4][1][32]

**Axial arrangement is not regulation level:** A bulb, pit, or S arrangement describes the placement and water passage of an axial turbine-generator installation. Its runner may have different adjustment capabilities. The bulb/pit row combines Voith’s application up to 30 m with the lower handbook Kaplan head anchor; its flow and efficiency values are declared Kaplan-family proxies. Voith reports advantages in full-load efficiency and flow capacity for suitable bulb/pit projects, but those benefits must be evaluated at the relevant scale. [28]

**In-pipe and geometry-specific entries:**

| Name | Type | Applicable Head Range, m | Applicable Flow Rate Range, m³/s | Design Point Efficiency Range, % | Pressure regulation capability |
|---|---|---|---|---|---|
| Pump as Turbine, PAT | Reaction | 1.5–77, observed site-average excess head | 0.002–0.453, observed site-average flow | 65–75 common BEP; machine cases about 31–81 | External hydraulic, speed, or combined regulation |
| Tubular axial microturbine | Reaction | 3.4–9 tested examples; 15 per runner prototype design | 0.0087 per-runner prototype point | 64–68 tested examples; above 85 design target | Adjustable geometry or independent speed, depending on design |
| Spherical, under spherical-hub axial interpretation | Reaction, conditional | 3.05–19.81 E, Kaplan proxy | 2.83–29.73 E, Kaplan proxy | 91–93 E, regulated-Kaplan proxy | Kaplan-type regulation only under this interpretation |

**PAT’s row describes urban opportunities:** The head and discharge values come from 38 PRV sites in Dublin and Seville: average excess head ranged from 1.5 to 77 m and average flow from 2 to 453 L/s. The extremes belong to different sites and do not form a rectangular machine operating envelope. Standard pumps span a much wider overall range, but these observations are directly relevant to urban pressure-recovery screening. [29]

**Tubular microturbines need machine-level distinctions:** The 2018 prototype had two independently controlled counter-rotating runners and an 8.7 L/s design flow. Its design head was 15 m per runner and its hydraulic-efficiency target exceeded 85%. The 64–68% efficiency band and 3.4–9 m head band describe earlier low-head experiments summarized in the same paper, not measurements of that prototype at its design point. [8]

**“Spherical” requires a hydraulic interpretation:** The conditional row applies when the term means a pressure-drop axial reaction runner with spherical hub or periphery, such as the minimum-gap geometry described by Voith for Kaplan/bulb machines. Its numerical values are explicitly transferred Kaplan proxies, not a separate spherical-product specification. If “Spherical” instead means a velocity-driven in-pipe rotor, flow velocity and allowable pressure loss would determine a different comparison. Brekke’s spherical inlet valves are control equipment and should not be assigned turbine conversion efficiencies. [28][33]

**Additional documented evidence**

| Entity | Name | Technical-table roster status | Type (Impulse or Reaction) | Applicable Head Range (m) | Applicable Flow Rate Range (m³/s) | Design Point Efficiency Range (%) | Technical pressure regulation capability |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Pump as Turbine (PAT) | The canonical name supported by this source is “Pumps…[139] | PAT is explicitly represented as a pump-turbine…[200] | PATs are reaction machines under the declared…[180] | 4–135 m (BEP head)[49] | 0.03–0.5 m³/s | 50%[50] | A documented PAT installation approach couples…[148] |
| Pelton turbine | The canonical name supported by the catalog is Pelton.[244] | no evidence found | Pelton is classified as an impulse turbine.[134] | 50–1,300 m net[46] | 0.386 m 3 /s[224] | 85%[193] | The page does not describe Pelton pressure-regulation…[186] |
| Turgo turbine | The canonical name supported for the row is “Turgo…[276] | Turgo should be included as a conventional action…[297] | Turgo is classified as an impulse turbine.[134] | 15–300 m net [258] | below 0.1 m3/s[273] | 93.7%[268] | no evidence found |
| Crossflow turbine | The canonical row name supported by the source is…[282] | A cited reference is titled “Development of an inline…[211] | The source distinguishes traditional Cross-Flow…[284] | 200 m[216] | 0.01–150 m³/s; typical <5 m³/s[234][288] | 75% to 80%[90] | The source reports an experimentally optimized…[165] |
| Francis turbine | The canonical name supported by the page is “Francis”.[235] | Kaplan turbines are represented in the U.S. hydropower…[58] | Francis is classified as a reaction turbine.[134] | 2–500 m hydraulic head[226] | 0.05–60 m³/s[226] | over 90% efficiency[216] | The supplied Francis-turbine references do not state…[96] |
| Kaplan turbine | The canonical name supported by this source is…[298] | no evidence found | Kaplan is a reaction turbine, specifically an inward…[253] | <10 m[228] | 0.5–1000 m³/s[60] | 85.90%[214] | no evidence found |
| Semi-Kaplan turbine | The canonical name supported by this source is…[298] | no evidence found | Kaplan is a reaction turbine, specifically an inward…[253] | <10 m[228] | 0.2–60.0 m3/s[229] | 85.90%[214] | Runner-blade regulation; intake/draft gate needed[299] |
| Spherical turbine | The source names the machine “Spherical”.[303] | no evidence found | no evidence found | 0.5–10 m[234] | 1–5.6 m³/s[234] | 22 %[211] | no evidence found |
| Propeller turbine | The source names the technology “five blades tubular…[167] | no evidence found | Propeller is classified as a reaction turbine: the…[228] | <10 m (low-head classification) [227] | 0.3–150 m³/s (Kaplan row) [234] | 85%[297] | no evidence found |
| Bulb/tubular low-head turbine family | no evidence found | no evidence found | Bulb and Tube turbines are listed as types of…[233] | Effective head: bulb 6–18 m; S-shaped tubular 3–18 m [57] | 2–60 m³/s (Kaplan bulb) [294] | 90% and 91%[305] | Runner pitch/wicket gates; auto shut-off if ungated [276] |
| Archimedes screw turbine | The canonical name supported by the source is…[306] | The source names Archimedes Screw Turbines and cites a…[75] | The Archimedes Screw is described separately as a…[238] | 0.1–10 m[309] | 0.01–10 m³/s[309] | 69%[185] | The source names Archimedes Screw Turbines and cites a…[75] |
| Vortex turbine | The canonical name supported by the source is…[63] | no evidence found | The source treats the vortex turbine as an impulse…[169] | 0.5–4 m [296] | 0.5–5 m³/s [296] | 58.13%[307] | Automated sluice gate; autonomous/remote control [102] |
| Deriaz or diagonal turbine | The canonical name supported by the page is “Deriaz…[263] | Provisional/uncertain candidate[297] | The Deriaz turbine is classified as a reaction turbine.[308] | 20–200 m; especially 20–100 m[263] | 1 to 5,5 m 3/s m³/s[115] | around 90%[250] | no evidence found |

rejected: citation_outside_operands — Propeller should be a contextual low-head reaction row: it is an adapted tubular machine for urban-network pressure recovery, with 85% reported BEP and a 2.3 m, 90 L/s example [297][227][228]. Its limited operating range and reported 54% and 70% values show why it should not be treated as a universal efficiency comparator; inline installation is documented, but the evidence is insufficient to treat Propeller as a mature standalone comparator [297][304].

Retain separate rows for Pump as Turbine (PAT), Pelton turbine, Turgo turbine, Crossflow turbine, and Francis turbine and every requested column, carrying source-qualified evidence—PAT’s two-valve regulation arrangement [54], Pelton’s net-head definition [65], Turgo’s medium-head and higher-flow characterization [70], Crossflow’s 2,5 to 80 m and 50 to 1600 l/s range [90], and Francis’s 20 m – 100 m range [116]—rather than dropping or silently filling cells. Mark missing, conditional, or non-comparable cells explicitly: the Spherical turbine efficiency cell is “no evidence found” [112], and gross and net head must remain distinct because friction, fittings, and entrance losses alter net head [65].

Apply an Evidence-status framework in the table and prose: label evidence as measured, modeled, manufacturer, field, normalized, qualitative, or non-comparable, and carry the source’s units, conditions, denominator, and method into each claim. PAT’s 40% to 80% range [69], Pelton’s 57% to 85% and 82% [77], and Turgo’s over 85% [273] therefore remain source-qualified—not a common ranking—unless their evidence status and basis are explicitly aligned.

**Technical Parameters and Applicability of Various Turbine Types**

Head definitions must remain visible. Net head is gross head minus penstock and other hydraulic losses; those losses vary with flow, pipe diameter, elbows, bends, valves, reducers, and turbine arrangement [68]. For Pelton applications, the effective pressure head is the head available at the turbine inlet after such losses [65]. Flow values may represent design, rated, minimum, maximum, or observed flow and should not be merged without qualification [68]. Efficiency values likewise retain their pump, turbine, system, or water-to-wire boundary: a general guide reports 50–70% typical overall electrical-generation efficiency and 70–85% for high-head, high-speed impulse systems, but these are system-level contextual values rather than universal row values [68]. In the conversions below, \(1\ \mathrm{L/s}=0.001\ \mathrm{m^3/s}\) and \(1\ \mathrm{ft}=0.3048\ \mathrm{m}\); converted values remain derived equivalents of the cited source values.

| Name | Roster status | Type (Impulse or Reaction) | Applicable head range (m) | Applicable flow-rate range (m³/s) | Design-point efficiency range (%) | Pressure-regulation capability |
|---|---|---|---|---|---|---|
| **Pump as Turbine (PAT)** [69] | **Include.** Standard centrifugal pumps operated in reverse; the useful range depends on pump geometry, selected speed, and generator arrangement [69]. | **Reaction, conditional on the centrifugal-pump configuration.** The cited design source identifies a reverse centrifugal pump but does not separately label the impulse/reaction class [69]. | The source figure shows a visible PAT head range of **2–10 m**; listed manufacturer examples have turbine heads of **8.6–39.2 m**. These are not one consolidated universal range [69]. | The source figure shows **2–60 L/s = 0.002–0.060 m³/s**; manufacturer examples span **4.9–93.8 L/s = 0.0049–0.0938 m³/s**. These are source-dependent ranges and examples [69]. | **40–80% typical pump efficiency**, with PAT efficiency described as approximately similar to pump efficiency; this is not a normalized PAT turbine design-point range [69]. | PATs can reduce water head while generating electricity. In a high-rise urban pipeline case, PAT selection and control avoided excessive head reduction at higher flows; the available evidence does not specify one universal bypass, speed, or electrical-control layout [310]. |
| **Pelton turbine** [65][68] | **Include, with qualified numerical fields.** It is an explicit turbine type and an impulse machine, but the available test values are machine- and condition-specific [65][68]. | **Impulse** [65][68]. | The source’s generic categories are **32–98 ft = 9.8–29.9 m** (“medium”) and **>98 ft = >29.9 m** (“high”); these are categories rather than a universal net-head interval. A separate 2020 study investigated modified operation at very low head, so that study should not redefine conventional Pelton applicability [68][65]. | No general applicable interval is established. A stainless-steel-runner test reports **0.001246, 0.001655, and 0.001721 m³/s**, but these are observed test discharges, not a family-wide range [65]. | A general table reports **80–90% typical efficiency**, without explicitly identifying a design-point or denominator; a separate stainless-steel-runner test reports **64%, 56%, and 49%** at the three listed discharges, in a system-efficiency column, not as a design range [68][65]. | The nozzle, flow-regulating arrangement, runner and buckets, and breaking jet provide turbine-level flow control. The cited material does not establish urban-network pressure-control logic, bypass control, or electrical regulation [65]. |
| **Cross Flow Turbine (SKAT T-12, T-13 and T-14)** [61] | **Include, qualified to the cited SKAT designs.** The source gives an application-limits table and describes Crossflow as suitable for micro power plants [61]. | **Not stated in the cited source group; retain as conditional/unsupported rather than infer a universal impulse/reaction label.** | **4–50 m net head**, measured at the turbine shaft [61]. | **100–820 L/s = 0.100–0.820 m³/s**, measured as source-reported discharge [61]. | Design-formula turbine efficiencies are **65% for T-12, 76% for T-13, and 80% for T-14**; the sample calculation gives optimum values of **65%, 70%, and 74%**, respectively. These are distinct design-data and sample-calculation contexts [61]. | Part-flow operation can be regulated by a simple valve or segment, hydraulic flap, or shaped semicircular segment. The source does not establish a complete downstream urban-network pressure-control strategy [66]. |
| **Francis turbine** [68] | **Qualified inclusion.** It is an explicit type and a documented reaction runner, but the strongest pre-cutoff application example is gravity-flow irrigation rather than an urban supply network [68]; a small Francis is also identified as a possible PAT-range alternative [69]. | **Reaction** [68]. | The source’s generic category is **32–98 ft = 9.8–29.9 m** (“medium”), not a universal range. A separate irrigation example used a Francis runner with **162 ft ≈49.4 m** of head, but that is a site example, not a family applicability limit [68]. | No general Francis range in m³/s is supplied. The irrigation example reports **888 gal/min**, but its gallon convention and nonurban context prevent treating it as a comparable technical-table range [68]. | A generic source table reports **80–90% typical efficiency**, but does not identify it as a design-point value or state the denominator for the Francis row [68]. | No pressure-regulation description is supplied for the documented Francis irrigation example [68]. A later page reports modeled pressure recovery and efficiency values, but it is marked published/updated **2025-12-31**; its modeled **92% hydraulic efficiency, 83.5% overall efficiency, 0.46 m distributor loss, and 1.26 m draft-tube loss** are therefore excluded from this pre-2024 table [62]. |
| **Gravitational Water Vortex Turbine** [63][64] | **Provisional/qualified inclusion.** The evidence supports retaining a vortex micro-hydro candidate, but does not establish its prevalence in urban supply recovery or a settled taxonomy [64]. | **Not established.** The source explicitly does not state whether the candidate is impulse or reaction [64]. | A source reports **0.7–2 m** and separately states that the hydraulic-head requirement can be as low as **1 m**; another product document reports operating examples of **1.7–1.8 m**. Gross, net, static, dynamic, and recoverable-head boundaries are not distinguished [63][64]. | No general interval is established. Reported operating examples are **0.9 m³/s** and **1.8 m³/s**; a separate example states **0.1 m³** but does not identify it as a flow rate, so it is not used as a range [64]. | No source-qualified design-point range is available. The evidence reports **80% turbine efficiency**, study-indicated values of **30–40%**, and commercial claims as high as **80%**, with differing denominators and evidence status [63][64]. | The documented mechanism uses a tangential inlet, circular basin, and free vortex; the source states that energy extraction is driven by the vortex’s dynamic force rather than a conventional pressure differential. Urban-network pressure control or external bypass/speed controls are not established [63][64]. |

**Pump as Turbine: pump-dependent applicability**

The PAT best-efficiency point occurs at a particular flow. Turbine-mode head and flow at BEP differ from the rated pump output, although the source describes PAT efficiency as approximately similar to pump efficiency; its typical pump-efficiency range is **40–80%** [69]. A particular PAT also has a narrower efficient flow range than a purpose-designed turbine because it lacks an equivalent variable guide vane or spear valve. It can still produce power below its maximum-efficiency flow, but with reduced output. Intermittent operation, storage-assisted operation, or parallel PAT units can address low-flow or high-flow conditions, although the extra installation cost may outweigh the equipment saving [69]. With direct drive, turbine and generator speed must coincide; the source warns about electrical or mechanical overload and recommends limiting an induction generator to approximately **80% of its rated motor power** [69].

**Pelton and Crossflow contextual contrasts**

Pelton recovers energy by directing a tangential jet onto buckets, rotating the runner and converting hydraulic energy first to mechanical energy and then to electricity [65]. Its useful contrast with PATs is strongest at **high head and low flow**, where the source states that Pelton is likely to be more efficient than a pump and no more expensive [69]. The Pelton source also explains that gross head is reduced by friction, bends, fittings, and entrance losses before the effective head reaches the turbine [65]. This is why the generic high/medium categories in the table must not be read as net-head guarantees.

The 2020 Pelton study is useful mainly for evidence qualification. It discusses a high-head conventional design but investigates very-low-head operation; its test material refers to different runner and vane materials, including a stainless-steel test table. The reported efficiencies of **64%, 56%, and 49%** correspond to discharges of **0.001246, 0.001655, and 0.001721 m³/s**, respectively, and are therefore not a general Pelton design range [65]. No urban pressure-control strategy is established beyond nozzle and flow-regulation components [65].

Crossflow evidence is more directly useful for variable-flow comparison. The source describes Crossflow as suitable for micro power plants across a wide range of actual site heads and flows, with comparatively low cost, short delivery time, easy installation, and local fabrication, maintenance, and repair in Indonesia [61]. It also reports available Indonesian design data and model testing [61]. These advantages are geographically conditional and should not be generalized to every procurement market.

The Crossflow power train described in the guide comprises the turbine, a speed-increasing coupling, a DC generator, transmission, and a DC–DC step-down controller for battery charging or later conversion to AC [66]. Its nonurban example is a custom Banki-Crossflow system developed and prototyped in **1991** at the Walsh River in Far North Queensland, integrated with Baldor DC generators and AERL Hydromax controllers [66]. That example demonstrates system integration, not urban potable-water deployment.

**Francis evidence and cutoff qualification**

**Vortex turbine: retained but unresolved**

**Source-qualified rows and evidence limits**

The cutoff is 31 March 2024. A numerical range below is retained only when its source defines the machine, operating condition, and measurement boundary. The 2023 ultra-low-head review covers heads of 0.5–3 m, 38 turbine types, and information obtained from 25 manufacturers, but it states that operating ranges are available only “in most cases”; therefore, its 0.5–3 m interval is not a universal range for every row [75]. PAT values are likewise machine-specific, and PAT internal efficiency must be distinguished from whole-network conversion efficiency [54].

| Name | Roster status | Type | Applicable head range (m) | Applicable flow-rate range (m³/s) | Design-point efficiency (%) | Pressure-regulation capability and qualification |
|---|---|---|---|---|---|---|
| **Pump as Turbine (PAT)** | Included; qualified as a machine-specific family | **Reaction**; the source explicitly describes PATs as reaction turbines [70] | **12.1–67.7 m**, an envelope across four investigated PATs, not a universal PAT-family range [54] | **0.0104–0.1293 m³/s**, converted from 10.4–129.3 L/s across four investigated machines; not a category-wide range [54] | **63.1–78.3% maximum PAT-mode efficiency** across four machines; the source does not establish this as a universal design-point range and distinguishes PAT efficiency from overall WDN conversion efficiency [54] | External regulation is required: a series valve dissipates excess head, a bypass valve reduces PAT flow, and variable-speed operation can match head and flow but requires an inverter and more complex controls [54]. |
| **Pelton turbine** | Included | **Impulse** [70] | No numeric range in the supplied pre-cutoff spans; the source provides only a higher-head/lower-flow contrast with Turgo [70] | No numeric range; Turgo is reported to handle substantially higher flow than Pelton [70] | No numeric design-point range; the source describes high efficiency over broad site conditions, while manufacturer evidence describes bucket geometry intended to maximize shaft-energy transfer [70][74] | A needle nozzle can adjust changing flow without shutdown in a 14 kW dual-jet Costa Rican system; this is flow control, not quantified downstream urban-network pressure regulation [74]. |
| **Turgo turbine** | Included | **Impulse** [70] | Viable for medium-head schemes and efficient at lower heads than Pelton; no numeric metre range is supplied [70] | Higher flow capacity than Pelton, but no numeric m³/s range is supplied [70] | Documented installations reportedly operated at **20–30%**, contrasted with a cited **50–60%** range; neither is established as a design-point value. Off-the-shelf specifications are often water-to-wire, leaving turbine efficiency ill-defined [70] | No pressure-regulation mechanism is reported in the supplied evidence; retain the pressure-control cell as unsupported rather than infer nozzle or bypass performance [70]. |
| **Crossflow (Banki-Crossflow) turbine** | Included; quantitative cells unresolved | Impulse/reaction classification is not established in the supplied sources; the cited classification review does not map Crossflow specifically [71][75] | Unsupported; the review’s 0.5–3 m interval is its overall ultra-low-head scope, not a Crossflow-specific range [75] | Unsupported; no Crossflow-specific m³/s range appears in the supplied spans [74][75] | Unsupported; no design-point efficiency range appears [71][74][75] | Unsupported as a network pressure-control value. Manufacturer evidence says selection requires measured head and flow plus pipeline and electrical requirements [74]. |
| **Francis turbine** | Included; quantitative cells unresolved | Not specified in the supplied spans | Unsupported [74] | Unsupported [74] | Unsupported [74] | Unsupported; the available manufacturer span only identifies Francis as a turbine type and discusses manufacturing procedures [74]. |
| **Kaplan turbine** | Included; pre-2024 technical lead, but row values unresolved | Not specified in the supplied spans | No Kaplan-specific range; the 0.5–3 m interval is the review scope, not a Kaplan value [75] | Unsupported [75] | Unsupported [75] | Unsupported in the supplied spans. The review cites a 2019 study of an ultra-low-head Kaplan system but does not provide its parameters [75]. |
| **LucidPipe™ lift-based vertical-axis spherical turbine** | Included; qualified and system-specific | Impulse/reaction classification is not stated by the source [72] | **1–4 m extracted head per turbine**, equivalent to 1–6 psi; this is a head-extraction specification, not a complete applicability range [72] | No complete m³/s range. The source reports typical pipeline velocities of **1.7–2.1 m/s** and rated flows of **14, 50, and 100 MGD** for different configurations [72] | No numerical design-point efficiency is supplied; the source states that the system was lab-tested and designed to maximize efficiency [72] | Automatic and remote controls can stop or slow the turbine and manage water velocity. Low extraction permits inline installation and series placement without a bypass; the pressure-control evidence is system-specific [72]. |
| **Propeller turbine** | Provisional/discovered; taxonomy unresolved | Not established in the supplied spans | Unsupported [54] | Unsupported [54] | Unsupported [54] | Unsupported. The pre-2024 lead is a 2014 numerical and experimental study of a “Propeller Pump as Turbine,” but the supplied passage provides no parameters or pressure-control result [54]. |
| **Archimedes Screw Turbine** | Provisional/discovered; retained as a candidate, with no admissible complete row | The supplied pre-cutoff evidence does not classify it as impulse or reaction or resolve whether it should be treated as a separate hydropower family [75] | No Archimedes-specific range is supported. The 0.5–3 m interval belongs to the review’s overall ultra-low-head scope, not specifically to this turbine [75] | Unsupported in the admissible spans [75] | Unsupported in the admissible spans [75] | Unsupported; no urban-network pressure-regulation mechanism is documented in the supplied pre-cutoff evidence [75]. |
|Semi-Kaplan turbine|Qualified;sewage-MHP case:13.4 kWp/86.8 MWh/y (2013);2022 small-hydro,not urban potable [554,526]|Impulse/reaction NR [295]|H:2–30 m (2013);1–10 m proto. (2022) [556,526]|Q:0.1–25 m³/s (2013);0.144 model/11.79 proj. (2022) [556,526]|η:85–90% turbine (2013);90.2% conversion at .35 m³/s,4.7 m net;82.1% model;87.7–89% CFD;86.92% proj. (2022) [554,526]|Reg.:adj./regulated runner;no guide vane;var. speed+level/head ctrl+PEC;network pressure unreported;cheap/simple vs Kaplan;cavitation/life risk [295]

The Pelton–Turgo evidence is principally from rural pico-hydropower rather than urban water networks; the source defines pico-hydropower as facilities below 5 kW, so its operating comparisons require transfer caution [70]. Within that context, Pelton is the higher-head/lower-flow comparator, whereas Turgo is a medium-head, higher-flow alternative. Turgo turbine-generator sets were available off the shelf in North America, although the cited specifications were water-to-wire values; the source also notes that projects in developing countries may assemble individual components and that Turgo and Pelton casting and machining are comparable [70]. Canyon Hydro reports systems from 4 kW to 25 MW and micro-hydro systems up to about 100 kW, but its supplied page does not give Pelton-specific head, flow, or efficiency ranges [74].

**Head, flow and classification conventions**

Gross head is the upstream-to-downstream vertical distance; net head is gross head less hydraulic losses. Thus, the ranges below are net-head or site-specific values, not universal gross-head limits [76]. Published ranges are approximate and design-dependent [78]. A 2019 Francis–Kaplan study further warns that speed equations developed for outputs above 1 MW have low accuracy below 1 MW, although its database contained hundreds of full-scale mini-turbines [79]. The drinking-water evidence is explicit for Pelton and for low-head reaction machines; river, generic small-hydropower, and channel examples are labeled rather than treated as urban-network data.

Crossflow terminology also covers distinct Darrieus-type and variable-pitch studies, so their parameters should not be transferred automatically to Banki/Michell Crossflow machines [80]. Likewise, the cited Propeller evidence from marine propulsion does not establish an urban-water technical row [80]. The Archimedes screw is fish-friendly in migratory-fish river installations and can avoid fine screening and automatic screen cleaning, but that environmental advantage is not an urban-network efficiency or pressure-regulation value [78].

**Range definitions and evidence limits**

Technical-table ranges are applicability evidence, not universal machine limits. The March 2024 guide defines gross head as the maximum vertical fall and net head as the head remaining after transfer losses; flow \(Q\) is volume per second, and shaft power follows \(P=\eta\rho gQH\) [84]. It reports generic, non-family-specific efficiencies of 80% to above 90% hydraulically for the best turbines, 75–80% for smaller systems below 50 kW, and 65–80% water-to-wire after gearbox and generator losses [84]. Its approximate ranges depend on precise design, head, flow, generator speed and reduced-flow duty; the guide’s 10–30% rated-flow lower operating figure and 40–60% capacity factor are mini-hydro/run-of-river context, not urban-network defaults [84].

**Named reaction and impulse families**

**Kaplan turbine.** Kaplan is a reaction, axial-flow propeller variant with adjustable guide vanes and runner blades; these controls broaden efficient operation across changing flows, although their mechanisms can be costly [84]. A 1960 comparison favored Kaplan below 38 m because of its higher speed and cheaper generator, while use became extremely difficult beyond 60 m [83]. Displayed model efficiencies were 87.1–88.2%, and 90–91% was described as normal for Kaplan models at specific speeds of 400–800 \(N_s\); these are turbine-model values, not system efficiencies or a universal design range [83]. The supplied evidence does not establish a complete applicable flow range or a downstream network-pressure curve: adjustable vanes and blades demonstrate flow/efficiency control, not autonomous pressure regulation.

**Crossflow (Banki) turbine.** Crossflow is an impulse turbine with a drum-like rotor. It is described as less costly but slightly less efficient than a spiral-case Francis, while efficiency falls more rapidly below half rated flow; the guide says it is uncommon on sites below 100 kW [84]. No numerical Crossflow head, flow, design-efficiency or network-pressure value is established here. A 2021 reference to “Crossflow Wind Turbines” concerns wind turbines, not water turbines, and cannot fill those cells [85].

**Provisional low-head candidates**

**Archimedes screw turbine/generator.** The reverse Archimedes Screw is classified as a gravity turbine in the low-head category below 10 m; the guide reports power-conversion efficiency above 80%, slow running, and the need for a multistage gearbox to drive a standard generator [84]. A 2021 review reports approximately 75% river-to-wire efficiency, relatively low installation and maintenance costs compared with same-scale hydropower, and simple, cost-efficient manufacture [86]. These values have different boundaries and must not be combined. The row is therefore a qualified gravity category rather than impulse or reaction; the supplied evidence gives no m³/s range or network-pressure mechanism. Inlet throttling or variable-speed operation can reduce screw flow, but variable speed is costlier and is normally associated with projects above 30 kW [84]. Few experiments and insufficient validation of current performance models remain limitations [86].

**Vortex turbine.** Vortex is an emerging low-head micro-hydro candidate requiring relatively little expertise and space; performance depends on flow, vortex height and a fully developed air core, with better performance near the middle of the speed/load range [82]. Prototype tests at 8.8 m³/h reported peak-efficiency results of 17–24%, 13–21%, 20–30%, and a maximum of 28.29% for model D with a 0.072 m outlet [81]. These are prototype-specific observations, not a design-point range; the candidate’s head, flow, classification and pressure-regulation cells remain unresolved. A 2023 review page confirms the technology but supplies no urban-water parameters [85].


**Evidence-qualified rows represented in this source group**

| Entity and row status | Type | Applicable head | Applicable flow | Design-point efficiency | Pressure regulation |
|---|---|---|---|---|---|
| **PAT — include; machine-specific values** | Classification is not explicitly stated in the supplied evidence; the tested machine is a centrifugal radial pump operated as a turbine [95]. | No general range; one tested BEP was **4.43 m water column**; a simulation at 810 rpm and 2.90 L/s produced section-specific heads of **1.09–4.67 m** [95]. | No general range; tested BEP **0.00360 m³/s**; the simulation used **0.00290 m³/s** [95]. | **62%** at the stated BEP [95]; separate experiments report **65% maximum** [93] and **79% maximum** for a flow-controlled unit [94]. These are not a harmonized PAT range. | Requires external inlet-flow and electrical/generator control; fixed geometry and absent inlet-flow control cause poor off-design performance [93][94]. |
| **Pelton — include; documented municipal example** | **Impulse** [89][97]. | No family range; a rough guideline is at least **10 ft = 3.05 m**; the Alamogordo installation used **460 ft × 0.3048 = 140.2 m** [89][97]. | No family range; Alamogordo averaged **1,000 US gal/min × 6.309×10⁻⁵ = 0.0631 m³/s**, and operated at **1,400 gal/min ≈ 0.0883 m³/s** at its reported output [89]. | No design-point range; the Alamogordo value was **77% measured overall-system efficiency**, not turbine efficiency [89]. | A nozzle converts pressure to a jet; adjustable nozzles or needle valves regulate flow, but the supplied sources do not establish a network-pressure-control rating [89][97]. |
| **Crossflow/Banki — include; manufacturer and review evidence** | **Impulse** in the explicit Michell–Banki classification; one reviewed passage uses “reaction values,” so the terminology is retained as a qualification [91]. | Product-page range **2.5–80 m**; a broader review describes suitability below **200 m**, which is not directly equivalent [90][91]. | Product-page range **50–1,600 L/s = 0.05–1.60 m³/s** [90]. | Manufacturer claim: minimum **75–80%**; reviewed studies span **58–86%**, with a **75.5% mean** and one CFD design point of **86%** [90][91]. | One- or two-compartment admission, guide vanes and inlet valves regulate flow; a study maintained flow at **20% of maximum**, but no dedicated urban-network pressure-regulation result is supplied [90][91]. |
| **Francis — include; qualified row** | **Reaction** [97]. | Unsupported in the supplied cards. | Unsupported in the supplied cards. | Unsupported as a Francis-family range; do not transfer values from the separate centrifugal-turbine study [96]. | No network-pressure-control value; a draft tube recovers pressure head after the runner, which is an energy-recovery mechanism rather than a downstream pressure-control rating [97]. |
| **Kaplan — named candidate; evidence incomplete** | Unsupported in the supplied page slice. | Unsupported. | Unsupported. | Unsupported. | Unsupported; the available source page identifies only a six-page document titled *Kaplan Turbines: design trends in the last decade* [99]. |
| **Spherical turbine — qualified contextual row** | A 2021 proposal calls it a **reactive lift-type** turbine, while another 2021 CFD source gives no classification; retain the conflict [87][88]. | Unsupported; the cited applications are large gravity-fed pipes rather than a standardized urban-network range [88]. | Unsupported. | No percentage range; the claim of **2–3 times the efficiency of solar and wind systems** is not a turbine design-point percentage [100]. | Two turbines may be installed in series in horizontal or oblique arrangements; horizontal placement was recommended where unwanted excess pressure exists, and oblique placement where gravity-created pressure is not wanted [87][88]. |

**Supporting applicability and comparison evidence**

**PATs.** The supplied review describes PATs as low-cost, easy to install, fast to procure and widely available, while warning that pump manufacturers generally do not publish reverse-mode characteristic curves; correlations are therefore needed for selection [93]. For low-specific-speed end-suction units below 10 kW, the turbine-mode BEP may require greater head and flow than the pump rating. Modified induction-motor coupling, capacitors and electrical controls can regulate output voltage and frequency [93]. A tested unit using a commercial pump impeller and customized inlet-flow control reached 79% maximum efficiency and a wider operating range than traditional PATs, but the study concerns rural micro-hydropower and energy-recovery installations rather than a universal urban-network result [94]. The 65% value appearing in cards associated with Pelton and Francis is explicitly a centrifugal-pump-as-turbine result and must not be assigned to either of those turbine families [93].

**Pelton.** The 1986 Alamogordo report documents a Pelton wheel in a 12-inch municipal supply pipeline: a 9.75-inch wheel drove a 100-kW, three-phase induction generator connected to the utility, with more than 75 kW produced at 1,400 gal/min and 160 psi. The system entered service in December 1985 and used two automatically adjustable needle valves [89]. This is strong evidence of urban water-supply applicability, but not a general efficiency or flow envelope. Impulse turbines are described as simple and relatively inexpensive, with variable flow accommodated by changing nozzle size or using adjustable nozzles [97].

**Crossflow.** The product description reports a robust machine with only two or three moving parts—the runner and one or two flow-control valves—plus low maintenance cost, compact civil works and quick installation from 2.5 m head [90]. The review reports more than 55% peak efficiency under heads below 5% and discharges below 30% of reference values, more than 80% in one 35–90 L/s example, and configuration-dependent nozzle results of 80–82%, 88%, 89% and 90% [91]. Results are sensitive to nozzle geometry, guide-vane angle, shaft diameter and air-layer effects; CFD and experimental results commonly differ by 2–10%, and sometimes by 15%. Poor operation beyond the maximum-efficiency flow can also introduce cavitation [91].

**Spherical and transfer limits.** The Spherical proposal used two turbines in series: at a 30° slope, the second oblique turbine produced more energy, whereas the first horizontal turbine produced more because it consumed pressure and increased downstream velocity [87]. The evidence is CFD-based and application-specific. Another source describes gravity-fed water and sewage lines, industrial or agricultural facilities, and claims installation in one day with generation in less than one week; it supplies no quantified procurement, O&M, service-life or market data [88]. A 27 March 2021 small-scale project used liquid flow and a DC generator but reported no aligned head, flow or efficiency range [101].

Open-channel evidence should not be silently generalized to pressurized supply networks: a Nile-channel study identifies shallow water, rocks, sediments, eddies and obstacles as installation constraints, while bottom-mounted relocation is costly; floating support is described as cheaper, easier to maintain and more flexible [92]. Conversely, a proposed Wainuiomata supply-pipeline project considered **40 MLD ÷ 86,400 = 0.463 m³/s**, approximately **100 m head**, 308 kW and 1,800 MWh/year; its reported $1.84 million capital estimate, $165,000 annual savings/revenue and payback of slightly over 11 years were project-specific, with consent and stakeholder requirements still pending [98].

Pelton 2013: impulse; rural/domestic; fall/flow; head/flow/η/pressure-reg. unreported [104][106].  
Crossflow/Banki: conditional impulse/reaction (20–60%/80–100% openings); low-cost but lower peak η; tested 3–10 m, η=79% at 5 m BEP, 2014; flow/pressure unreported [106].  
Francis: reaction; 12 m model head, 2022; off-BEP η falls; head/flow/η unreported; guide vanes reduce pulsation; adjustment issue [103].  
Archimedes screw: type unresolved; Belgium project: 10 m head, 5 m³/s each, 3–5 m³/s, 2018; η/pressure unreported [105].

- **Pelton turbine:** Impulse; urban head/flow NR. Efficiency \(>92\%\) applies to low-specific-speed prototypes, not a family range. Injectors/deflectors, governor and inlet valve control flow. [107]
- **Francis turbine:** Reaction; head 20–30–700+ m; flow NR (example: 36 m³/s at 400 m net head). Efficiency is 96% for large prototypes; another 96% is an assumed hydraulic value. Guide vanes are identified; urban pressure-control data are NR. [107]
- **Kaplan turbine:** Axial reaction with adjustable runner/guide vanes. Product variants: 1.5–35 m and 1.2–200 m³/s; guidance is <40 m, occasionally ~75 m net, extreme 75–80 m, and Bulb <15 m. KB1290 K3: 3.25 m net, 1.65–8.5 m³/s, assumed mean efficiency \(η=88\%\), not measured. Double regulation supports variable-head and part-load operation. [107][108][109]
- **Semi-Kaplan/propeller:** Axial reaction variants; Semi-Kaplan adjusts runner blades with fixed guide vanes, while propeller blades are fixed or limited-adjustable. Other requested cells are NR. [108]
- **Archimedes screw:** Separate equal-pressure/gravity family: <1–10 m head, ≤18 m³/s, efficiency up to 92%; variable speed regulates flow and avoids cavitation. [108]
- **Spherical:** Requested cells are NR. **Deriaz/diagonal:** only a high-specific-speed, low-head reversible-pump option is identified; requested ranges are NR. [107]

Pelton runners may exceed 50 years conditionally; erection and Francis casing/seal pressure testing are substantial. A 2016 Kaplan estimate was 20m Kč (5m technology + 15m construction), with ~884,000 kWh/year and payback more than twice the screw option; it is site-specific. [107][108] The evidence trail lists Kaplan design references from 1987 and Francis design references from 1987 and 1976, without aligned urban ranges. [110]

Kaplan [included]—reaction; H 1–30 m (axial), 1.5–35 m (Mavel); Q 1.2–200 m³/s; η unsupported; wicket+runner single/double regulation, low-head/high-flow [111][114][116].

Crossflow/Banki PRS [included]—impulse [114] (type unstated [113]); 2019 H 100 m net, Q .105 m³/s; flap+inverter; η mean 53/61% (d1/2) vs hydraulic 61/55%, ηtot≈80%; Q 70–100 L/s, p .2–.6 MPa; cost>dissipation, benefit>cost; stop: no overpressure [113].

Francis [included]—reaction; H 20–100 m; ηh design 52–87%, mean 62–72%; .700 large-turbine test, not small-hydro; variable-Q PRV replacement; GPV-3 > PAT at similar Q, no matched BEP [114][116].

Pelton [inc.]—impulse; atmospheric outflow not controllable for PRV replacement [114]. Spherical [cond.]—cross-axis Lucid; +15/+12.5% power-coefficient gains, η unsupported [112]. Deriaz/diagonal [cond.]—reaction; Q 5.4–6.0 m³/s, net H 50–57.5 m; η expected .8 (not %/range); adjustable distributor/blades; low-flow cavitation/noise, stainless runner; grids backwashed [115][116].

Caveat: EPS uses demand/time steps [122]; align model/prototype, gross/net H, mode and η boundary [117]. Pelton—impulse; drinking-water example [119]; Bieudron-2011: Hgross 1,734–1,883 m, Hnet 1,633–1,869 m, Q 25 m³/s/unit; nozzle/valve transients [123]. Turgo—2023 South Georgia: 13 kW, H 61 m, Q 42 L/s; variable hydrology/pipe loss [120]. Crossflow—impulse/action; urban 2014 ±15 kW; hydropower H>15–<100 m, urban H/Q/η absent; PRV hunting/manual control [118][124]. Francis—reaction; options <50 and 50–300 m, high-fall 80–200 m+; poor partial-load, surge/cavitation; Q/η absent [117][121]. Kaplan—adjustable reaction; <20 kW, H<5 m, η>85%; Palermo WWTP-2023: H 3.75 m, Q .806 m³/s, ηhyd 86.4%, ηglobal 76.6% [117][124]. Archimedes screw—qualified low-head drinking-water candidate; type/H/Q/η unsupported; external relief regulation [119]. Deriaz/diagonal—uncertain, non-urban; 2019 6–21 kW model ηhyd ~90–91.4%, peak 91%; pump η .79 at Q .12–.28 m³/s; double regulation [117].

- **Pump as Turbine (PAT)—included; reaction, similar to Francis/Kaplan [129].** H/Q: unsupported; inlet hydraulic power is 1–1,000 kW (losses excluded) or 5–750 kW conservatively, with radial/mixed/axial regions open. A 2021 3-kW study reports PAT efficiency 60% versus Francis 80%; off-design loss is 3–10% from absent hydraulic control. PRVs dissipate pressure; low-potential PAT cogeneration may be uneconomic [129].

- **Pelton—qualified impulse row [125].** Turbach/Gstaad: six-nozzle vertical unit; gross head ~230 m; 2.5 MW; expected 7.3 GWh/year; spherical valve, inlet pipe and hydromechanical governor; flow/design efficiency unsupported; planned summer 2024–26. Values are project-specific, not ranges; pressure regulation is unassessed. Contextual Pelton/Crossflow peak efficiency is ~80%, with denominator/duty absent [129].

- **Francis—qualified row; type not stated in project evidence [125].** Glarey/Bex, February 2024: two horizontal units; head 30.5 m, flow 5.3 m³/s; expansion flows 5.25/1.8 m³/s; 2.3 MW and ~7.5 GWh/year. These are non-urban project points, not ranges; design efficiency and pressure regulation are absent, although valves/control equipment are listed. Francis is described as a traditional potential-to-shaft turbine; a 2014 review gives only a 2009 partial-discharge lead [128][129].

- **Kaplan—included reaction row; GUGLER supplies units to 40 MW/unit [139,143].** Contexts: head <40 m, 40–60 m, and low-head selection typically <100 m (~50 m). Project head/flow maxima: 51.26/106.4, 46.8/178.7, 22/251; field flow was 100–840 m³/s; model head was 3 m—none is a generic urban range. Design efficiency is unsupported. Servomotor blade/guide-vane adjustment reduces very-low-load pulsation; tip-clearance vortices may cavitate. A 2005 CAM study (~150 regimes) found ~16% more power, but measurements below 350 m³/s were uncertain [126][127].

- **Crossflow—provisional.** The 2014 review provides only rural/remote low-head leads; type, head, flow, efficiency and pressure regulation are unsupported [128]. A 28 November 2024 page is post-cutoff and excluded [130].

Francis evidence concerns treated wastewater rather than pressurized potable supply: the October 2023 study reports 24.82 kW maximum output and 150.29 MWh/year modeled from 2018 discharge [67], while supplier material records a 57 kW Toruń recovery unit [131]. Pelton is supported here only in a wastewater context; Propeller is supported in pipe-inline micro-hydro studies, so their other cells remain unsupported in this fragment [212].

**PAT row—** *Pump as Turbine (PAT; Pumps-as-Turbines)* is included [49][52]; **type:** reaction [52], though [49][51] leave classification unstated. **Head:** no universal range: tested 7.0–27.5 m; 59 pump-mode BEPs 4–135 m; turbine examples 15.0–70.4 m [49][50]. **Flow:** tested 0.002–0.0046 m³/s (2.0–4.6 L/s); 59 pump-mode BEPs 0.005–0.222 m³/s; turbine examples 0.021–0.228 m³/s; Antalya 130–300 m³/h and 0.7–7.0 kWh at ~100 kPa [49][50][138]. **Efficiency:** 50% turbine-mechanical BEP at 2.5 L/s/30 m; another PAT 75% turbine/69% whole-unit at 31.4 L/s/37.1 m/3000 rpm; examples 0.67–0.84 unitless; ~80% estimated, 65.5% assumed—no common percentage range [49][50][51][59][140]. **Regulation:** bypass/PRV, valves, VFD or combinations; hydraulic control stays near BEP but dissipates head, electric may run off-BEP; SSP uses two PATs/three valves (20% vs 35% capability; one-third cost), and bypass protects pressure [50][52][56][145].

At ±40% off-BEP no efficiency value/trend was reported; partial-load decline was steeper without guide vanes [49][51]. Plant η=0.074–0.453 is not BEP; some cases exceeded 40%, others converted ~one-tenth of available energy [45]. PATs are off-the-shelf/mass-produced, lower-cost and inexpensive to maintain, but price data are discordant/outdated (343 pumps; 286 generators) [51][52][139]. Propeller is only cited PAT literature; no parameters are established [51].

**PAT (Pump as Turbine)**—included row: a centrifugal pump operated in reverse [149][150]. Type: **impulse/reaction unresolved** in the supplied evidence [149]. Reported pressure/head proxy: **5–100 m**, and flow: **0.00001–0.4 m³/s**; both are modeled cost-domain values, not universal limits [153]. Observed BEP values were **6.0–30.2 m** and **0.0041–0.0093 m³/s** [148]. Design-point turbine efficiency was **68–80%** in simulated WDN scenarios [155], versus tested total BEP efficiency of **44±1.9–63±0.7%** [148]; no numerical partial-load curve is reported [148][155]. Pressure control uses bypass/control valves, PRVs as needed, inverter/variable-speed and real-time control; residual head may be dissipated [149][154][156]. PATs recover excess WDN pressure and are lower-cost/standardized, but each unit has a narrower flow range and is selection/control-sensitive [150][154].

PAT (Pump as Turbine): row; type unresolved; reported operating head 1–152 m and flow 0.003–0.110 m³/s; η 0.6–87.2% (2023-11-28); PRV+bypass+3-way valve [159].

PAT (Pump as Turbine/reverse centrifugal pump): included; reaction-type by the fixed-guide-Francis analogy, but conditional because one source leaves the type unresolved [48][162][176]. Tests—not universal ranges—gave H=4.8–33.9 m and Q=0.005–0.009 m³/s [168]; a broader H=0.6–20 m, Q=0.006–2 m³/s applies to energy converters generally, not PATs alone [174]. BEPs included (H=9 m, Q=0.029 m³/s) and (15 m, 0.015 m³/s) [175], and H=37.1 m, Q=0.0314 m³/s with turbine η=75% and overall η=69% at 3,000 rpm [162]. Other tests reported η≈43% at 650 rpm and >60% at 1,250 rpm; at Q≤6 L/s, η was 37% versus 25% [168]. Pressure control uses speed/curve selection plus PRV, bypass or throttling; fine head-drop control is limited [48][174][203]. Sörenberg installation cost €27,100 (2018) [162].

Pelton turbine: impulse; stated minimum H=10 m and Q=0.5 L/s; laboratory Q=0.11–0.15 L/s (optimum 0.1583 L/s), ηmax=29.16%, not a general range [161]. Guides aid variable-flow/partial-load operation; back-pressure operation requires an air cushion [48].

Spherical turbine: lift-based in-pipe generator; impulse/reaction type and design η are unsupported. Modeled site H=8–17.9 m and Q=72–323 m³/h; PRV-replacement modeling produced 1.94% lean-flow and 9.70% peak-flow insertion loss in 250-mm pipe [167].

Turgo: impulse, H=20–80 m; Francis: guide-regulated; Kaplan: contextual only; Propeller: axial reaction, low-head/experimental (BEP H=3.5 m, Q=16 m³/h, η≈64%; one study leaves type unstated); bulb/tubular unresolved; Deriaz mixed-flow, type unresolved; Crossflow-specific data are absent from the PAT-only evidence [48][167][168][218].

PAT: Pump as Turbine; reaction; elsewhere unclassified [178,153]; case heads 6–15/73.6–75 m [132]; rated flows 0.0109–0.0298 m³/s [141]; ηmax 66.3% [219]; PRV/bypass [133]

Site/test values are not universal urban limits: **PAT**—reversed centrifugal pump; reaction turbomachine in one source, classification unresolved in others [158][151]. BEP: ΔH 13.8 m, Q 0.022 m³/s, η 70%; laboratory H 4.8–33.9 m and Q 0.005–0.009 m³/s [158][151]. Other studies report BEP maxima of 65–75%, variable-speed η 62–64%, and about 30% system efficiency [73][143]. Pressure requires valves/bypass or variable-speed control [158][143]. **Pelton turbine**—impulse; reported head 15–1,800 m and high-head/low-flow use, with no general flow range; a non-urban design used Q 3.14 m³/s and 95.4% hydraulic efficiency [198][47]. A spear nozzle, braking jet and deflector provide control [47]. **Turgo turbine**—impulse, medium-head/wide-flow; one BEP example was H 10 m and Q 0.044 m³/s, with efficiency unstated [215]. **Francis**—reaction, H 20–500 m/high-head-high-flow; **Kaplan**—reaction, low-head/high-flow, steerable [195]. **Propeller**—axial-flow reaction [215]. **Archimedes Screw**—separate family; Q 0.1–10 m³/s per screw, qualitatively high efficiency down to about 30% of maximum flow, sluice-gate regulation, and reverse pumping to a generator [194]. Crossflow pressure regulation remains unsupported [151].

PAT—reaction; 1–80 m head, 1–100 L/s flow (machine-dependent, 2018) [180]; efficiency range unsupported (80% modeled, 2024) [181]; PRV replacement needs minimum pressure [192]. Crossflow/Banki–Michell—impulse; few m–hundreds m head, few–hundred L/s flow; 85.6–86% CFD (2013) [166]. Francis—reaction; 27.5 m/12.4 m³/s case, ~83% hydraulic (2020) [171]. Propeller—reaction; <10 m; 25–55 L/s, 1–5 m, 50–60% (2023) [227]. Pelton—impulse; 0.386 m³/s pressure case; 85% minimum, up to 95% (2022) [224].

PAT—type unstated; H 2–1000 m and Q 0.001–10 m³/s (configuration span), peak η 65.04–76% (not general) [204]; PRV replacement needs network adjustment [189]. Pelton—impulse, H 10–50 m, low Q; η/pressure unavailable [228]. Turgo—impulse, H 10–50 m; Q/η/pressure unavailable [228]. Francis—reaction, H <10/10–50 m; Q unavailable [228]. Kaplan—reaction, H <10 m [228]. Propeller—reaction, H 1–5 m, Q 25–55 L/s, η 50–60% [228]. Spherical helical—H 4 m, Q 209 L/s; building case [228].

PAT: included, reaction; 2.5–80m, 0.8–6m³/s [229]; η61% BEP; lit:40–80% [173]; PRV/bypass/VFD [173]. Pelton: impulse; 3–100m [230]. Crossflow: impulse [229]. Capacity conflict

**Evidence-qualified roster entries**

- **PAT (reaction):** head 13–75 m [233]; supplier flows 0.03–6, 0.007–0.4 and <0.42 m³/s [234] (catalog examples: 6.5–11.5 and 45–95 CFS [157]). A related spillway site reported 100 ft³/s and ~11 ft head; the PAT used about half the flow [178]. BEP efficiency is about 0.6–0.7 [144]; a 2023 municipal simulation reported 0.62–0.64 [135]. PATs serve WDN/aqueduct recovery, but pressure control requires speed control with PRV, bypass or hydraulic regulation [178][225][135][157][209].

- **Pelton (impulse):** a 1-kW design/test used 10 m head and 0.02 m³/s; supplier data list 0.008–0.01 m³/s [232][234]. It is the high-head/low-flow contrast, although the cited application is rural rather than urban WDN; flow deflection/bypass and gradual spear-valve adjustment protect against transients [232][142].

- **Turgo (impulse):** it operates across varied head and flow and is reported most efficient at 1.5–3.5 m in low-head micro-scale work; the cited source gives no urban-WDN role [233][225].

- **Crossflow/Banki-Michell (impulse):** supplier flows are 0.01–1.0, 0.04–13 and 1.5–150 m³/s [234]. A 2019 prototype tested 0.0059–0.03 m³/s at 26.5 m net head and 76.3% BEP efficiency; other designs report 0.010–0.045 m³/s, 85% BEP, and 86.8% with regulation (>84.3%) [209][178]. A mobile flap provides passive constant-head or active-discharge control; compact diffusers and inline flanges reduce pipe modifications, and the PRS is reported to outperform PAT on energy and installation cost [178][209].

- **Francis, Kaplan and Propeller:** all are reaction machines; bulb and tube turbines are Propeller subtypes [233]. Supplier flows are 0.03–60 m³/s for Francis and 0.2–150 m³/s for Kaplan, with Propeller included in that Kaplan row [234]. Francis guide vanes alter characteristics, while bypass/deflection protects against transients [53][142]. A 5BTP axial/tubular Propeller was tested at 1.4–13.5 L/s; its BEP was 0.34 m, 4.4 L/s, 750 rpm and 64% hydraulic-to-mechanical efficiency in inline drinking-water service [137].

- **Other candidates:** Spherical inline turbines are listed at 0.5–10 m and 1–5.6 m³/s, installed in the primary conduit without a bypass and typically producing 1–100 kW [234]. Archimedes screws are a separate, unclassified low-head/high-flow family: heads <10, 4–20 and 1–10 m; flows <10, <10 and 0.2–10 m³/s; no design efficiency is supplied, but capital cost is reported 22% below equivalent Kaplan [233][234]. A vortex candidate has a listed flow of 0.05–20 m³/s [234].

PAT (row)—BEP η 0.6–0.7; alternatives >70%, 73% median/150, up to 85%; BEP H/Q/N absent; off-design η/reliability↓, maintenance↑ [146][163][179][182][152]. PRV replacement uses hydraulic series-parallel or inverter control; no guide vanes→external control, narrower than Francis; 10–20× cheaper, 5–500 kW, ~6-y payback vs 8–10 y [136][163][201][202]. Pelton—impulse; high-head/low-Q (460 ft net/1,500 gpm); bypass/nozzle/deflector PRV service [136][190]. Turgo—impulse; other cells unknown [136]. Francis/Kaplan—reaction; single-/double-regulated; Francis simulated H error ≤2% [136]. Deriaz—mixed-flow/double-regulated, also reaction; ranges unknown [136]. Crossflow—pressurized PRV candidate; type/ranges unknown [146][202]. Propeller—inline, variable-Q/low-H; type unclassified; frequency converter plus bypass/valves [187][188]. Spherical—no permitted pre-cutoff values; unresolved.

H=head; Q=flow; η=eff.; NR=not reported here. PAT: city pressure/flow recovery+battery; PRV parallel/substitute, but low-demand pressure fails; speed/parallel/bypass/valves [205][206][207]. Pelton—WDN pressure recovery; impulse; H 20–hundreds m, Q .005–1 m³/s, η≤95% (micro 90%); spear-jet/controller [236][239][197]. Turgo—atmospheric recovery; impulse; Q>same-size Pelton; H/η NR; fixed/spear jet [237][239][206]. Crossflow—impulse; pressurized PRS ηhyd>75%, passive/active pressure/Q; ordinary outflow atmospheric; H/Q NR [177][236]. Francis—reaction; in-line downstream pressure; guide vanes; narrow design η; H/Q/η NR [177][236][206][208]. Kaplan—reaction; H 1.5–6 m; Q .09–.41 vs .09–.53 m³/s intended; η 76.4% at 2.25 m; guide+blades [236][208]. Propeller—reaction, low-H/high-Q; tubular η poor at variable Q. Bulb/tubular—propeller subtypes, in-pipe; adjustable guides/blades+draft tube; ranges NR [236][177][205]. Archimedes screw—gravitational; falling water turns screw; ranges/pressure NR [238].

Pelton—impulse; high-head/low-flow; needle/deflector control; 97% max (not design) [240]. Gerlos (2023): 617 m, 16 m³/s, site-specific [243]. Francis—reaction, medium head/flow; Kaplan—reaction, low–medium head/high flow [217]; others N/A. Propeller—reaction, low-head/pressure-driven [241]; others N/A. Turgo—name only; other fields unreported [242].

Pelton 30 m/0.03 m³/s; global gen. 42–50% tested, 51% design; needle-jet control [247]. Turgo flow+power [246]; Francis reaction,50–750 m [246][245]; Crossflow listed [244]

Pelton turbine—impulse; qualified; urban role unshown. H 10–130 m; test <1–~6 m, 2017; 865-m example, 2011. Q 0.0005–0.007 m³/s; test 0–0.222; peak 0.053678. η 77% (1 m,¼ valve)/24.278% (3 m, brake peak); valves/bypass/nozzle/spear regulate. [248][249][251] Turgo—impulse; H 1–3.5 m/35 m; 200-ft test; η 90% theoretical/63% predicted; Q unknown (2015). [164][223] Francis/Kaplan—reaction; Francis 33–44.5-m net; Kaplan >3 m; ranges unknown. [223][251][170] Crossflow—impulse; urban role unshown. [223][251] Archimedes screw—gravity (reaction/separate); H<6 m; Q≤8 m³/s (4-m); η75–85%; gearbox. Deriaz—class unresolved; diagonal pump-turbine; η≈90% at 30–120% design flow; difficult pivots. [250]

**Pelton:** impulse; H 50–1,300 m net; Q high/very-low; η 80–89% at 0.2–1.2 load; nozzle/needle+deflector [46][255].  
**Turgo:** impulse; H 40–300 m effective; Q 0.01–0.07 m³/s (2021 case); η≤87% operating; nozzles/deflector [57][253][256].  
**Crossflow:** impulse; H 3–200 m net; Q≤0.8 m³/s example; η≈10% below Pelton; regulation— [46][255].  
**Francis:** reaction; H 10–350 m net; Q 0.8–25 m³/s normalized; η≈93% full→≈70% at ⅓Q; guide vanes [46][220][254][255].  
**Kaplan:** reaction; H 2–40 m net; Q 2.5–45 m³/s; η>90%; variable pitch [46][220][253].  
**Propeller (provisional):** fixed-blade reaction; H 2–40 m shared; Q/η/regulation— [46][220][252].  
**Bulb/tubular (qualified):** reaction; bulb H 6–18 m, S-tube H 3–18 m; Q 3–70 m³/s; η/regulation— [57][220].

Pelton—included impulse; H >300/≥400 m; other cells — [259][260].  
Turgo—listed impulse; other cells — [264].  
Crossflow/Michell–Banki—impulse; H 4–220 m; Q 0.03–18 m³/s; η up to 84/87%* (low/high); draft-tube air-valve/guide-vane control; drinking-water use; low-civil/easy-install, long-life/low-maintenance claims [265].  
Francis—reaction; H 40–600 or 20–700 m; hydraulic η >80%/up to 95%*; Q/control —; mixed forces [222][259][260].  
Kaplan—reaction; H 6–60, <60 or 10–70 m; η 85.90%* at full wicket/pure water; dual guide/runner regulation; silt/cavitation/fatigue/transient concerns [259][260][266].  
Semi-Kaplan—included, qualified reaction; low–medium H/medium–high Q; numeric cells — [264].  
Propeller—reaction; H 3 m and Q 0.94 m³/s† only; rest — [261][262].  
Bulb/tubular—type unresolved; guide ring regulates flow; ranges — [261].  
Archimedes screw—separate gravitational family; remaining cells — [264].

Pelton: impulse (2016) [267]. Turgo: impulse; H 15–500 m (2020); η 93.7% measured/94.2% modeled (2020); Q unknown; urban role unestablished; Pelton-like regulation [267][268].

**Additional roster evidence**

- **Turgo turbine:** Impulse; the source table gives 50–250 m and <10 m³/s. Opposite-direction outflow is advantageous, but casing rebound can interfere with jets and the runner, worsening performance and ventilation losses; efficiency and pressure-control values are not reported in this evidence [172][271].

- **Crossflow:** Impulse, with an inline vertical application reported for urban water-supply pipes [270]. **Francis:** Reaction; 40–600 m, *specific* flow 0.2–1,000 m³/s, and cited efficiency of 90–95%, falling sharply below 75% of design flow. **Kaplan:** Reaction; <50 m and 0.5–1,000 m³/s; variable blade angle assists extraction, but pipeline integration is problematic. **Propeller:** Reaction [270][271]. One Francis AVT-runner case increased weighted efficiency by 3.7% and capacity by 10%; this is not a general range [172].

- **Archimedes screw turbine:** A separate quasi-static-pressure/volumetric family, not an impulse or reaction turbine. Reported applicability is <10 m head, <10 m³/s flow, and 60–80% efficiency; conventional AST evidence gives 1–6 m and 0.1–6 m³/s, so ranges are source-dependent. Water-to-wire efficiency is typically 60–80%; plant peaks were around 75% and a real facility exceeded 80%, with different boundaries [271][272]. Urban-flow tests are reported, but not specifically potable-supply tests. Generator use dates from the 1990s; several hundred installations were mainly in Europe, with two North-American grid-connected units reported in 2020. Lack of standards, engineer-dependent design, gearbox losses, and high-head/flow structural and bearing limits remain qualifications; installation may require permits, cranes, stable foundations, and flood-protected electrical equipment [271].

Pelton—impulse; high-head/lower-flow [213]. Turgo—impulse; 13–28 m tested head, >85% turbine efficiency; nozzle/spear flow control and jet deflection [273]. Crossflow—impulse; urban inline prototype: 1.2–2.2 m/s, 69.1 W and 2.62 m head loss, <5 m in tests [231]. Francis/Kaplan—reaction, pressurized; efficiency drops below 50% of design flow [191].

Pelton: impulse, high-head [274]; Turgo: impulse, rated 30–205 m and 0.089–8.30 m³/s [257]; Crossflow: impulse, <200 m and <10 m³/s [269], 70–85% efficiency [275].

Turgo—impulse;100–300m;0.1–10m³/s;87%[277];PRV/deflectors[278].Semi-Kaplan—reaction;3–16m;Q=30.075m³/s;88.92%rated[276].Bulb/tubular—reaction?;flow/η?[276].Capacity conflict.

Turgo I H15–350m Q— η40–85% mixed pressure— [280][221]; Crossflow I/R H1–20m Q5–500L/s η64–96.233% mixed guide-vane [281][199][165]; Francis R H30–700m Q.20–50m³/s η/p— [279]

Pre-2024: Pelton/Turgo: impulse; Pelton 60–>1000 m (200m; 23/35 L/s min/design); rest unknown [216][285]. Francis: reaction; 20–700m; >90% large only; wicket-gate/governor; rest unknown [216][285]. Kaplan: 2–40m; WWTP; economic best; rest unknown [216][283]. Crossflow/Banki: impulse (hydrokinetic R=.73); <200m; 0.45m³/s; η72%; flat to 1/6; simple/regulable; urban inline/WWTP [282][216][287][55][283]. Archimedes screw: 1–10m; 0–1.4m³/s; rest unknown [216][285]. Spherical: ½–1kW in-pipe city concept; rest unknown [286]

Pelton impulse, >30 m, ~90%; Crossflow impulse/reaction, 1–30 m, 0.195–0.3 m³/s; Francis/Kaplan reaction low-head; Archimedes screw low/ultralow-head bulky/noisy [183][184][289]

Crossflow: impulse, 1.75–200 m (usually <40 m) [291]; inline urban-main case: max 42.4%, ~1,500 W [210]. WWTP Kaplan: reaction, 86.7% BEP at 3.75 m and Q=0.996 m³/s [290].

Francis turbine—include as a named contextual row, not a core comparator. A pressurized Huelva (Spain) distribution case reported 280 MWh/year, approximate investment €20,000/year, and two-year recovery [293]. Reaction turbine [147]. Head: typically several tens–several hundreds m in hydropower; efficiency: >90%, boundary unspecified [292]. Flow range unsupported: 0.21 m³/s is a Francis-99 test case [147]. Guide vanes/external controls regulate flow and power; PRV bypass handles surges (non-urban evidence) [147][196].

PAT—include adapted reverse-pump; neither impulse/reaction; PRV replacement, speed variation/parallel PRV regulate pressure; η40–70% [297]. Econ: <2y payback at 5–500kW, machine cost−50%, life25y [297]. Pelton/Turgo/Crossflow—inc. impulse/action; η≈90% (Pelton, head ratio .2–.8), ≈80% (Crossflow, .2–1) [297]. Francis/Kaplan—reaction; controls unspecified. Propeller—adapted reaction/tubular for pressure reduction; η≈85% (.9–1) [297]. Semi-Kaplan—reaction; intake/draft gate needed [299]. Deriaz—provisional reaction [297].

Kaplan: reaction; 1–20 m; 0.4–50 m³/s; 72.5% rated; double regulation [300][301][302]; Propeller: fixed low-head 3–45 m; flow/eff. unk. [160]; Bulb/tubular: conditional [160]

### How the estimated flow ranges are calculated

**Power equivalence fills the comparison transparently:** The hypothetical 5–100 kW shaft-power band mirrors IRENA’s micro-hydro capacity band while excluding generator losses from this hydraulic calculation. For turbine efficiency \(\eta\), its corresponding discharge is:

$$Q=\frac{P_{\mathrm{shaft}}}{9.81H\eta}.$$

Using the highest head and efficiency gives the lower discharge bound; using the lowest head and efficiency gives the upper bound. IRENA’s size categories provide the power anchor, while the turbine table provides the head and efficiency inputs. [17]

| Estimated entry | Lower-bound calculation, m³/s | Upper-bound calculation, m³/s |
|---|---|---|
| Pelton | \(5/(9.81×1,500×0.90)=0.00038\) | \(100/(9.81×50×0.89)=0.229\) |
| Turgo | \(5/(9.81×300×0.90)=0.0019\) | \(100/(9.81×15×0.85)=0.80\) |
| Francis | \(5/(9.81×750×0.94)=0.00072\) | \(100/(9.81×15×0.93)=0.731\) |
| Fixed-blade axial proxy | \(5/(9.81×9×0.68)=0.083\) | \(100/(9.81×3.4×0.64)=4.68\) |

**These ranges answer a conditional question:** They show the discharge associated with a specified micro-power scale under sourced head and efficiency anchors. They do not establish whether a vendor builds an economical runner at every endpoint, whether that runner satisfies cavitation constraints, or whether all head-flow combinations inside the projected bounds are compatible. Their practical use is to distinguish power scale from a genuinely characterized product envelope.

**Conversions preserve the original quantities:** The catalog uses \(1\text{ ft}=0.3048\text{ m}\), \(1\text{ ft³/s}=0.0283168\text{ m³/s}\), and \(1\text{ L/s}=0.001\text{ m³/s}\). Thus, Crossflow’s 6–650 ft becomes approximately 1.8–198 m; Kaplan’s 100–1,050 ft³/s becomes approximately 2.83–29.73 m³/s. These are unit conversions rather than new performance measurements.

### Selecting a turbine for the hydraulic arrangement

**High-head reservoir delivery favors impulse options:** Where water can discharge into a reservoir without retaining pipeline pressure, Pelton and Turgo become attractive. Pelton generally favors higher head and lower flow; Turgo can accommodate relatively higher flows at lower heads. Their nozzle and jet arrangements offer useful variable-flow operation, especially where multiple jets are economically justified. [4]

**Crossflow favors broad flow accommodation:** Segmented admission allows part of the runner to remain effectively loaded as discharge declines. Its comparatively simple, self-cleaning arrangement can be attractive where peak efficiency is less valuable than broad useful operation and straightforward maintenance. For drinking-water mains, the casing, outlet pressure, and hygienic arrangement still determine whether a particular inline design is appropriate. [12][7]

**Pressurized districts favor reaction candidates:** Francis, appropriately designed axial machines, and PATs can extract head while retaining pressure downstream. A Francis turbine is attractive where its efficient discharge range overlaps the annual duty. A PAT is attractive where a standard pump offers a close match and the external pressure-control circuit remains affordable.

**Low head makes discharge especially important:** From the power equation, halving available head doubles the flow needed for the same power at unchanged efficiency. Larger flow passages, pipe modifications, and chambers can therefore offset the attraction of a low-head resource. At small urban discharges, a compact axial microturbine may be more relevant than the larger Kaplan-family examples; at larger flows, adjustable axial designs can justify their additional mechanisms.

**Stable flow can justify simpler machines:** A semi-Kaplan or fixed-blade propeller may provide an economical compromise when the operating region is narrow. Wider variability strengthens the case for double regulation, variable speed, multiple units, or a PAT bypass arrangement. The Rebolluelo case shows the risk of accepting low-flow fixed-speed operation without sufficient cavitation and performance margin: blade erosion led to repairs and a variable-speed retrofit. [32]

**Part 3 takeaway:** Use the catalog to identify plausible hydraulic families and power scales, then select the actual machine against downstream pressure requirements and its annual operating envelope.

## Part 4 — Main Economic and Technical Challenges in Urban Water Supply Networks

### Small energy outputs must support substantial retrofit costs

**Technical potential exceeds economic potential:** EPRI’s 2013 municipal-water report estimated U.S. excess-pressure recovery potential on the order of hundreds of megawatts, while reporting one large utility’s view that the economic potential was small. The apparent conflict is understandable: a geographically dispersed technical resource can consist of many individually marginal sites. [34]

**Civil works do not scale with power:** Excavation, road reinstatement, chamber enlargement, access, drainage, isolation, and electrical protection remain necessary even where generation is only a few kilowatts. The Granville study identifies small street manholes and protection of electrical equipment in unfavorable environments as central economic constraints. Its energy-booster concept sought to reduce this civil-work burden rather than maximize machine efficiency alone. [2]

**Valves are material capital items:** Samora and colleagues’ Lausanne inline concept allowed up to four turbine units within a buried chamber around an existing pipe. Its cost analysis found that the required number of isolation valves could materially affect investment in addition to the electromechanical equipment. Adding units can improve hydraulic matching and maintenance flexibility, but also adds interfaces and isolation requirements. [35]

**Fixed control costs penalize small sites:** The EPRI-based handbook example gives US$10,000–15,000 for SCADA input. As a hypothetical scale comparison, allocating that amount to a 10 kW installation adds US$1,000–1,500/kW; at 100 kW it adds US$100–150/kW. This arithmetic illustrates a fixed-cost effect, not a prediction of a particular utility’s controls quotation. [4]

**A worked revenue scenario shows the constraint:** Annualizing Granville’s optimized 9.68 kWh/day gives an estimated 3,533 kWh/year, assuming its representative operating pattern persists. Applying electricity values used in three pre-2024 studies gives the following gross-revenue scenarios. A ten-year horizon and 5% discount rate produce an annuity factor of 7.722, calculated as \([1-(1.05)^{-10}]/0.05\). [2][15]

| Electricity-value scenario | Assumed annual recovery | Estimated gross revenue/year | Ten-year gross revenue present value |
|---|---:|---:|---:|
| €0.10/kWh, 2022 framework | 3,533 kWh | €353 | €2,728 |
| €0.159/kWh, 2023 HYPER model | 3,533 kWh | €562 | €4,338 |
| €0.22/kWh, 2019 Laives valuation | 3,533 kWh | €777 | €6,002 |

The tariff inputs come from the cited models; the table is a conditional calculation, not a new network simulation. [18][15][14]

**Gross revenue is a capital ceiling:** Those present values precede maintenance, replacements, administration, and other costs. They explain why a small site can possess substantial excess pressure yet support only a tightly contained retrofit budget. Existing chambers, nearby electrical loads, and shared instrumentation can change the outcome more than a few percentage points of peak turbine efficiency.

**The complete alternative matters:** Retaining a PRV can remain economically sensible even where recovery is technically feasible. PAT recovery adds a low-cost generating opportunity but usually retains some pressure-control infrastructure. A purpose-built regulated turbine adds potentially higher energy capture and integrated adjustment at a larger initial investment.

| Alternative | Main financial attraction | Principal added cost | Appropriate decision basis |
|---|---|---|---|
| Retain or improve PRV control | Low incremental investment | Valve maintenance and instrumentation | Pressure service and leakage-management value |
| PAT with PRV/bypass support | Standard equipment and spare parts | Integration, generation controls, and connection | Positive net value over realistic annual operation |
| Purpose-built regulated turbine | Higher capture and hydraulic adaptability | Custom machinery and regulation hardware | Incremental benefits repay the project premium |

### Variable demand complicates sizing and energy forecasts

**Average conditions can conceal mismatches:** Customer demand changes both flow and network pressure. During low-demand periods, pressure may be high while turbine flow is small; during peak demand, greater pipeline losses can reduce the head safely available for extraction. Consequently, multiplying an average flow by an independently calculated average head can misrepresent the resource. [36]

**Oversizing reduces useful utilization:** A machine selected for a short high-flow peak may operate inefficiently for much of the year. Selecting a smaller machine can improve utilization but bypass more water during peaks. Multiple units can improve matching, as illustrated by Trondheim’s proposed two parallel PATs, one operated discontinuously, but increase equipment, valve, and control requirements. [37]

**Seasonal assumptions alter economic results:** The February 2024 Funchal model assumed winter flow at 70% of summer flow and spring/autumn flow at 85%. These ratios were model inputs, while its 80% turbine efficiency was also a specified simulation setting. Such results are useful for scenario analysis, but an investment decision depends on whether the assumed seasonal operating pattern and machine performance fit the utility’s installation. [6]

**Low head and peaked demand interact:** HYPER’s low-head, peaked-demand scenario produced no positive NPV among the 316 catalog pumps assessed under its assumptions. This is stronger evidence than a general statement that PATs are cheap: even a broad commercial catalog did not overcome that particular combination of resource, variability, and modeled costs. [15]

**Leakage reduction can reduce generation:** Successful pressure management lowers leakage, which can reduce the water volume passing through a turbine. That may lower electricity production while improving the utility’s overall position through water savings and avoided treatment and pumping. Generation should therefore be evaluated alongside leakage management rather than used as a reason to preserve unnecessary flow. [36]

### Pressure, transients, and continuity impose non-negotiable constraints

**Critical-node pressure governs allowable extraction:** The lowest-pressure customer location, high-rise buildings, and fire-flow requirements constrain how much head can be removed. A satisfactory turbine outlet pressure does not by itself prove satisfactory pressure everywhere in the district. WaterWorld’s pressure-management discussion emphasizes maintaining service at maximum demand and minimum fire-hose pressure while reducing excess pressure during low demand. [38]

**Shutdown can be more severe than operation:** Electrical load rejection allows a turbine-generator to accelerate; abruptly stopping water flow can create water hammer. Reaction machines, including PATs, need a coordinated shutdown and bypass strategy that considers both overspeed and pressure transients. The Wyoming handbook explicitly calls for surge assessment and controlled closure. [4]

**Impulse protection works differently:** A Pelton jet deflector can remove torque from the runner without immediately stopping pipeline flow, permitting slower nozzle closure. Canyon’s marketed protection arrangement uses this principle. The advantage applies to that hydraulic arrangement; it does not eliminate the separate issue of atmospheric discharge in a pressurized water-supply system. [39]

**Water service needs independent operating states:** The installation should preserve supply during low flow, high demand, turbine isolation, and electrical failure. These requirements explain why parallel branches and retained PRVs recur in practical layouts, including DuoTurbo and Funchal. [21][6]

| Operating state | Required water-service behavior | Generation response | Relevant protection |
|---|---|---|---|
| Normal recoverable duty | Maintain downstream pressure and demand | Generate within the permitted envelope | Coordinated pressure and power control |
| Very low flow | Maintain low-demand pressure | Reduce speed, switch units, or stop | Regulated bypass or PRV |
| Peak or emergency demand | Preserve required delivery capacity | Limit extraction or bypass generation | Adequately sized service path |
| Turbine fault or maintenance | Continue water supply | Isolate the affected machine | Isolation valves and independent bypass |
| Grid loss or control failure | Avoid unsafe pressure excursions | Disconnect and enter safe hydraulic state | Load-rejection, overspeed, and fail-safe logic |

**Retained regulation improves blackout behavior:** A 2020 laboratory prototype used hydraulically operated PRVs for pressure control and an inverter for generation control. Its authors identified low valve operating-power requirements and greater reliability during electrical blackout as advantages. This supports separating the essential water-pressure function from the energy-optimization function where practical. [40]

### Cavitation, wear, and drinking-water compatibility affect maintenance

**Cavitation is a local-pressure problem:** Adequate average pipeline pressure does not guarantee adequate pressure everywhere inside a runner or outlet passage. Off-design operation can create local low-pressure regions, vapor formation, pressure pulsations, noise, and damage. Delgado’s PAT experiments identified a cavitating precessing vortex rope in the draft tube using pressure measurements and high-speed visualization. [13]

**The problem affects conventional turbines too:** Rebolluelo’s semi-Kaplan experienced severe blade erosion, noise, vibration, reduced output, and repair requirements during unfavorable operation. Variable-speed conversion was introduced to improve adaptation. The comparison is therefore between safe operating envelopes, not between a supposedly cavitation-free conventional machine and a vulnerable PAT. [32]

**Particles create continuing performance losses:** DOE’s microhydropower handbook explains that gravel and larger debris can cause immediate damage, while suspended silt and sand wear internal surfaces and progressively reduce efficiency. Urban drinking-water systems generally differ from untreated river intakes, so protective measures should match the actual water and maintenance conditions rather than automatically copying an open-water installation. [41]

**Potable-water compatibility extends beyond cleanliness:** Wetted materials, coatings, seals, lubricants, and maintenance procedures must preserve drinking-water quality under the applicable jurisdiction’s requirements. Voith’s oil-free hub discussion illustrates the broader engineering issue: avoiding accidental lubricant release can require specific bearing materials and mechanisms. A readily available industrial pump still needs assessment for the intended water-service duty. [28]

**Maintenance access affects economic performance:** Equipment that is inexpensive to buy but difficult to isolate, lift, drain, inspect, or reconnect can have high intervention costs. Conversely, a standardized removable PAT module can be attractive if the utility can replace it without interrupting supply. The appropriate maintenance budget includes the chamber, access, valves, and controls, not only the rotating machine.

### Control, electrical integration, and institutional capacity add costs

**Measurements must support the control objective:** Flow, upstream and downstream pressure, electrical power, and operating state are the basic variables linking water service to generation. SCADA provides centralized supervision of distributed assets, but local control remains important for immediate hydraulic responses. Sensor placement and calibration therefore affect both performance assessment and safe operation. [42]

**Faster control is not always better value:** Creaco, Galuppini, and Campisano compared small- and large-time-step real-time controllers in an unsteady network model. Their hydropower outputs were similar; the faster controller held critical-node pressure closer to its set-point, while the slower controller had a control-cost advantage. Controller selection should therefore reflect required pressure accuracy and dynamics rather than maximum update frequency alone. [43]

**Grid proximity strongly affects feasibility:** EPRI identifies distance to a suitable grid connection as a material barrier. Local self-consumption can avoid some export complications, but generation still needs suitable protection, metering, and electrical equipment. A small output can struggle to justify a long cable route, new transformer, or extensive connection process. [34]

**Grid-connected generation is not automatic backup:** The handbook explains that induction generators normally depend on the grid and must shut down when it fails. Islanded operation requires appropriate excitation, voltage and frequency regulation, protection, and load management. An installation designed to offset purchased electricity should not be credited with emergency-power capability unless it has the required electrical architecture. [4]

**Financing depends on monetizable benefits:** Electricity used locally may have a different value from exported energy. Grants, financing costs, connection charges, and eligibility rules can change project economics without changing hydraulic performance. At Skagit, the reported 16–18 kW system offset approximately US$1,000 per month and carried an expected eight-year payback, illustrating the importance of actual avoided electricity expenditure. [20]

**Governance can be a larger barrier:** ESMAP’s municipal water-energy primer identifies governance, knowledge gaps, and financing hurdles as major obstacles to energy-efficiency investment. Small recovery projects also require coordination among water operations, electrical engineering, finance, procurement, and the grid operator. Standardized equipment helps, but does not remove these organizational interfaces. [44]

**Permitting should match the actual retrofit:** Relevant obligations can include drinking-water approval, construction and access permissions, pressure-system safety, electrical interconnection, and environmental permissions where applicable. Existing-pipe recovery differs from building a river diversion, so the applicable pathway should reflect the installation rather than assume every conventional hydropower permit applies unchanged. The BHA guide identifies land access, permissions, resource assessment, and a nearby load or grid connection as core development prerequisites. [26]

**The best candidates combine favorable conditions:** Persistent excess head, useful flow across much of the year, an existing accessible chamber, nearby electrical demand, and a straightforward pressure-control arrangement strengthen both PAT and conventional-turbine economics. Extensive civil work, uncertain service pressure, repeated marginal operation, or difficult electrical connection weaken the case. The preferred response may be a different machine, a simpler control arrangement, or improved PRV and pumping management without generation.

**How to read the evidence:** Efficiencies distinguish hydraulic-to-shaft performance, water-to-wire performance, BEP references, measured tests, and model settings. Head-flow entries distinguish handbook bands, observed site averages, prototype points, and explicitly marked screening proxies; projected bounds do not imply every combination is feasible. Cost figures retain their source-year currencies and scopes, including IRENA’s real 2010-dollar basis, without inflation or exchange-rate adjustment. Estimated flow envelopes, annualized revenue scenarios, and the PAT 10–30-year appraisal range are calculations or transferred planning assumptions, not measured product guarantees.

**Closing judgment:** PATs are often the most economical starting point for urban pressure-energy recovery, but the winning installation is the one that preserves reliable water service and delivers the greatest justified life-cycle benefit—not necessarily the cheapest machine or the highest quoted efficiency.

**Additional documented evidence**

Installation feasibility is a **network-service problem**: the device must recover pressure energy without compromising downstream pressure or water supply. The deciding conditions are time-varying flow and head, installation location, control mode, civil/electrical scope and energy yield—not nominal turbine price alone [56][153].

**Economic barriers**

PATs can reduce equipment cost, but total installation cost remains highly site-specific. A model of nine water-network schemes rated **9–120 kW** estimated total PAT installation cost at **€72,518 on average**, ranging from **€4,035 to €201,662**; it assumed the PAT and generator represented 26% of total cost, with average shares of 24% for controls, 21% for civil/hydraulic works and 19% for other project costs [153]. The same evidence identifies limited low-power cost data and few civil-works case studies. A separate Ballinabranna case reported PAT equipment averages of **€5,919, €6,268 and €5,323** at three sites, with maxima of **€10,984, €11,633 and €9,879**; these are equipment figures, not complete installed costs [319]. Another model assumed electrical and technical equipment, including frequency-modulator procurement and installation, at 300% of PAT-plus-generator cost and annual maintenance at 5%; these are modeling assumptions, not universal rates [321].

Location can dominate economics. One dynamic-network study found capital payback of **1–3 years** at the best sites but **14–15 years** at a poorly selected site, making the investment economically infeasible [318]. Conversely, a full-scale Antalya PAT installation computed a project-specific payback of **53 days (1.8 months)** from implementation cost and environmental-benefit revenue [323]. Thus, tariffs, avoided leakage or water costs, flow duration, financing assumptions and civil scope can explain apparently conflicting payback results.

**Technical barriers**

**Technology-specific evidence and limits**

- **Conventional micro-hydroturbines:** the cited pre-cutoff evidence describes traditional small-hydro units as having higher initial-capital, maintenance and spare-parts burdens; one synthesis reports initial capital can reach about 25% of installation cost [328]. No universal urban-network cost or payback should be inferred.
- **Pelton turbines:** drinking-water systems with low discharge and **60–600 m head** are identified as suitable; a bypass is required when the turbine is unavailable or flow exceeds its capacity [77]. Pelton equipment is installed outside the pipe, with water routed back after pressure reduction, increasing routing and civil-interface requirements [197].
- **Francis turbines:** a Logan, Utah installation had to fit an existing PRV vault; higher flow accelerated PRV degradation, requiring a compact turbine-generator, hydraulic power unit, valves and controls [201].
- **Propeller turbines:** a water-supply prototype is a low-head, high-flow axial machine installable in a bypass or main pipe, but long-term field operation remains poorly established; laboratory overall efficiency reached **60.7% at 10.4 L/s** [325]. A separate selection source groups propeller with Kaplan below **40 m net head** [76].
- **Turgo turbines** are confirmed as impulse machines, but the cited pre-cutoff excerpt supplies no quantified urban installation challenge [285]. **Bulb/tubular turbines** are described as in-pipe machines with an axis parallel to flow; a separate challenge assessment remains unresolved [197].

**Entity-specific installation evidence**

**Conventional micro-hydroturbines.** Low-head/high-flow sites require more civil and machine capital; existing structures or dual-purpose projects can reduce cost and payback. Recurring MHP O&M (repairs and insurance) is **1.5–5% of capital cost** [216]—generic MHP evidence, not an urban average.

**Pelton.** Pelton is an impulse machine applicable at **60 m to >1,000 m** head. A rural Nepal case (200 m; 23 l/s minimum, 35 l/s design) suffered a badly welded penstock burst, delaying electricity; repairs depended on external technical and financial support [216]. Alamogordo’s municipal pipeline (1985) used 460 ft head, 1,000 gal/min average flow, needle-valve control and a 100-kW generator; it delivered over 75 kW at 1,400 gal/min and 160 psi, with **77% measured overall-system efficiency** [89]. At another 100-kW, 23-m-net-head site, predicted electromechanical cost was **€1.42/W**, with a **£50,000** water-to-wire quote; no suitable local supplier was found, and the source warns that the estimate was not South-Africa-site based [312]. A UAE case required bypass integration and pressure/discharge flexibility; modeled payback was **1 to <6 years**, depending on scenario [193].

**Turgo.** A municipal-supply study listed **89–100 kW**, **55–62 m**, and **€90,000–€115,000** options; environmental, hydraulic, economic, technical and location constraints were recognized, but pipe replacement was excluded. Assumptions were 30 years, 5.45% annual maintenance and 10-year debt at 8% [335]. A rural 890-kW, two-jet project required integrated drinking-water/hydropower planning [326].

**PAT and other types.** A municipal Worthington PAT suited constant flow; wide variation motivated another turbine [183]. TRANSCO modeling gave **AED417,592** capital, **AED959,236** 10-year NPV, **328.11 kWh/year** recovery and a **6-year payback**, while real multi-location implementation remained needed [303]. Crossflow is simple, inexpensive and well regulated, with a flat curve to 1/6 flow/load [216]; directory evidence gives **1–30 m**, **1–250 kW**, guide/split-vane control and a **$40,000, 50-kW/6-m** package [183]. Debris/FOD, sediment, corrosion, transients and fatigue can cause efficiency loss, repairs and downtime; modeled Kaplan efficiency was **85.90%** in pure water, with maximum silt and combined losses of **2.47 percentage points** and **4.31%**, respectively [214]. Propeller evidence is limited to a **0–3 m, 7–13 l/s** tubular test, with best power at 20° and 13 l/s—not a general range or efficiency [343]. No supplied pre-cutoff card establishes installation challenges for bulb/tubular, vortex or Deriaz/diagonal candidates; retain them as unresolved.

**Turgo:** South Georgia (2023): 7.5-in, 13-kW; skid mounting shortened installation, but controls and commissioning remained [120]. Existing-pipe losses occurred at 61 m and 42 L/s [120]. Rural Huro (not urban supply): 110 kW; 8.42 million SBD (January 2010; environmental/social costs excluded); 50–150 L/s, with bypass/spill above 150 L/s [353]. Complex runners, lower-than-Pelton efficiency, imported spares and specialist skills restrict deployment [267][164].

**Crossflow:** An urban-main model reached 42.4% maximum efficiency and approximately 1,500 W, with acceptable head reduction but incomplete validation [333]. Banki/PRS designs can replace PRVs and regulate head/flow; recirculation and internal shocks reduce efficiency, while coupled hydraulic/electrical control increased computed return time by about 30% [178]. Small-scale evidence identifies nozzle, runner, guide-vane, turbulence, stress and fabrication issues [165][317].

**Francis:** Daily flow variation can prevent conventional installation through net-head changes [339]. A Pretoria 15-kW variable-speed model used 8 months of data; PRV-parallel operation produced negligible reservoir oscillation, but bypass valves were estimated at 20–30% of investment and 30% of total case-study cost [339][188]. Huelva reported 280 MWh/year, approximately €20,000/year investment and 2-year recovery, all site-specific [293]. Generic evidence reports loss-of-load runaway below 1 second and surge [121]; municipal in-line projects can add transient protection, SCADA, electrical integration, certification and monitoring burdens [352].

**Kaplan/provisional types:** Generic Kaplan evidence identifies site-specific variable-pitch control; fewer than 1 in 10 units was field-tested, and a 2006 single-head test cost $25,000 [337]. No eligible pre-cutoff urban-network challenge is established for Archimedes, propeller, bulb/tubular, vortex or Deriaz/diagonal candidates; these remain evidence gaps.

- **Conventional micro-hydroturbines:** mounting, safety, corrosion, spares and maintenance raise lifecycle risk; reported paybacks below 10 years in some UK cases and 8–10 years for an aquarium installation are non-urban. [228]
- **PATs:** low-cost, available pumps have reported capital payback of ≤2 years at 1–500 kW, but absent turbine-mode curves, poor part-load/head-flow response and low-demand pressure failure can require bypasses or controls; tariffs and model uncertainty affect finance. [205]
- **Kaplan, Francis and Turgo:** Kaplan covers 1–20 m and 20–100% design flow in a compact/modular form; Francis is reaction-type for low-head/heavy-flow service. Turgo’s deflector can stop discharge with the nozzle open, but buried pipework and sand/material choices burden maintenance. [302][313][57]
- **Semi-Kaplan:** a 250 kW unit was operating in 2012; no-guide-vane simplicity is offset by submerged-generator/civil costs, converter/grid controls and cavitation or erosion. General small-hydropower O&M is 2.2–3%/year and electromechanical life is ≥30 years. [264][340][295][341]
- **Spherical and propeller:** spherical installation is claimed to take one day, with generation in under one week, but ≥14 million gal/day for a 24-inch unit confines viability to transmission pipes; 1–6 psi (1–4 m) extraction and remote control avoid a bypass. Propeller units suit low-head/high-flow sites, but cavitation, testing/interconnection and U.S. FERC permitting (≥6 months; tens of thousands of dollars) remain barriers. [342][72][331][304]
- **Bulb/tubular and Archimedes screw:** bulb/tubular units face sub-1 m runner constraints, poor access/cooling and submerged-seal pollution risk. Screws add leakage, speed/filling, weather/O&M, size, bypass, placement and transport/manufacturing burdens; up to 80% is hydraulic small-hydro efficiency, not total recovery. [57][160][330][344][316][327][336][345][346]

**Technology-specific challenges and evidence limits**

- **Archimedes screw:** At small scale, site, geotechnical, civil/electrical and approval costs are nearly fixed; the source reports the same burden for **7.2 and 150 kW** plants. Large screws need cranes, stable foundations and accessible channels; minimum reasonable flow is not analytically defined and depends on bearings, generators and electrical equipment [324]. No general design standard, a lab-to-field scale-up gap and the gearbox required by low speed add design and efficiency risk [271][347]. Evidence is mainly river or wastewater-based, not urban potable networks [271][347].
- **Vortex turbine (provisional):** Pre-cutoff evidence is mainly low-head river, irrigation, rural or off-grid. A Nepal pilot reported **$2,725/kW in 2016**; civil works were **30% of total cost**, and slow rotation required gearbox/belt and electronic-load control [349]. A Bali installation reported debris blockage and irreparable flood drivetrain damage [348]; a prototype reported **28.29% efficiency at 8.8 m³/h**, showing geometry and flow sensitivity [81]. Urban-network cost and reliability remain unverified.
- **Deriaz/diagonal turbine (provisional):** No urban-network challenge evidence is shown. Pumped-storage evidence reports severe cavitation, **1.5 mm** blade-wall clearance, difficult small-machine manufacture and complex double regulation/high maintenance [311]. NAUSSAC II reported **5.6 million French francs** extra hydraulic cost and a return in **under 5 years** for the full set [338]—historical, non-urban and not directly transferable.

PAT (2018): 485 MWh/y, B/C 8.2, 2-y payback; €350/kW vs €1,800/kW mini-turbine installation (basis unknown) [329][144]. Fixed/no inlet control + missing curves → poor off-design prediction; low pressure → cavitation risk; PRV/bypass/inverter control trades pressure for losses [94][95][144]. Funchal low-flow links favor valves; off-BEP → vibration/wear [96]. Francis/Kaplan equations weak <1 MW [79]. Crossflow claim: compact/low-maintenance, flood-safe; bulb guide-vane clogging [90][314]. Spherical 1-day/<1-week (CFD/product); screws ~75% river-to-wire, non-urban; vortex 0.7–2m, not pressure-based [88][86][350].

Conventional micro-hydroturbines carry recurring and site-specific economic risk: operation and maintenance, including repairs and insurance, can be 1.5–5% of total capital cost [216], while uncertain demand, long-term growth, pipe-friction coefficients and future costs affect revenue, NPV and payback [351]; site access also limits transportable equipment and quotations require layout, head and flow information [183]. Technically, variable demand changes residual head and energy, so extended-period modelling over 24 time-steps is needed [122]; low-flow links may produce so little energy that a valve is more viable [96], while cavitation and intake vortices require protective design because stable vortices can cause energy loss, reduced discharge, vibration and equipment damage [46][315].

PAT-specific economic uncertainty remains: estimated total installation cost averaged 72,518 € and ranged from 4,035 € to 201,662 €, while evidence is limited for very low powers, civil works and non-centrifugal PATs [153]. Variable demand complicates pump selection, manufacturers usually omit reverse-mode curves and real-network installations remain rare [322]; PAT efficiency at the BEP is 0.6–0.7 and the BEP differs by machine [144][55], so fixed-flow operation needs a parallel PRV/bypass for excess flow [157], while extending operation to 20 and 30 years raises payback by 11% and 22% through maintenance [321].

Pelton turbines impose substantial hydraulic, mechanical and civil-design demands: cavitation, overload behaviour and runner stresses must be addressed [123], the casing must resist vibration and fluid–structure loads [172], and a badly welded penstock joint has caused a test-run burst, demonstrating a quality and safety risk [216]. In urban sites, noise may require mitigation and permitting, sediment-laden water can erode buckets, and varying jet or flow conditions may require customized buckets or multi-jet nozzles [332]; counterpressure operation also requires aeration control to protect drinking-water quality [172].

Turgo turbines carry a fabrication and controls burden: their complex runner is harder to fabricate [267], while installation can include hydraulic control, an actuated inlet valve and electrohydraulic equipment [120], followed by coordinated installation and commissioning [278]. Flood-capable intakes must handle bed load and floating debris [353], and nozzle angle and silt affect erosion and performance [215]; site-specific intake and erosion-control design is therefore necessary [121].

Crossflow turbines are relatively simple and locally maintainable [334], but their recovery installation can cost more than a simple dissipation device [113], making site flow, head variation and expected output central to economic feasibility [118]. The turbine must be installed above the tailrace and outside flood reach [90], while frequency control, sudden load rejection and slow PRV response can cause hunting and transients; the pipeline must therefore be structurally sound [118], and inlet and nozzle geometry adds design work [165].

Francis turbines impose space, manufacturing and network-integration demands: an existing PRV vault must accommodate a compact system [201], precise geometry and installation space are required [320], and feasibility must be judged against network efficiency and service quality [339]. Large daily flow variation can prevent installation of traditional Francis units [339]; guide-vane changes alter flow, generator torque, pressure pulsations and efficiency and may require feedback control [103], while transient runaway can occur in less than one second [121], demanding robust protection and control.

## References

[1] <https://www.canyonhydro.com/images/Part_2_ESHA_Guide_on_how_to_develop_a_small_hydropower_plant.pdf> ESHA small-hydropower guide; ESHA efficiency guidance; ESHA operating-range guidance; ESHA guide; ESHA maintenance guidance; ESHA turbine references; ESHA sing…
[2] <https://www.mdpi.com/2073-4441/14/10/1526> Granville PAT study; Granville acceptance tests; Granville energy-booster results; Granville operating-state analysis; Caprari Granville tests; Granville tests…
[3] <https://doi.org/10.3390/fluids3020041> Fluids comparison, 2018; PAT recovery versus variable-speed pumping; Fluids comparison; Fluids cost discussion; Historical installation anchors
[4] <https://wyomingrenewables.org/renewable-technologies/hydroelectric/wyoming-small-hydropower-handbook/evaluating-resources/electromechanical-equipment2/> Wyoming small-hydropower handbook; Wyoming turbine descriptions; EPRI estimates reproduced in the Wyoming handbook; Wyoming pressure-maintenance discussion; Wy…
[5] <https://doi.org/10.6036/10874> Baiona drinking-water installation; Baiona operational study; Baiona selection rationale
[6] <https://www.mdpi.com/2073-4441/16/3/504> Funchal study, 2024; Funchal operating-point methodology; Funchal PAT operating modes; Funchal series arrangement; PAT control modes; Funchal seasonal and turb…
[7] <https://www.mdpi.com/2073-4441/12/4/958> Servigliano laboratory and network study; Experimental PAT study, 2020; Inline Banki–Michell context
[8] <https://doi.org/10.3390/app8091426> Axial microturbine experiments and prototype; Tubular microturbine study
[9] <https://unsworks.unsw.edu.au/server/api/core/bitstreams/7f5114ad-e76d-4e64-9262-de6dfb3a3019/content> Movitec laboratory study; Movitec pump-to-turbine comparison
[10] <https://doi.org/10.3390/en14092690> Mixed-flow PAT experiment
[11] <https://link.springer.com/article/10.1007/s11269-022-03421-9> Variable-speed municipal simulation; Municipal variable-speed study; Variable-speed municipal case
[12] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10336523/> Crossflow review; Low-head Turgo examples; Small crossflow examples; Crossflow operating behavior
[13] <https://doi.org/10.5075/epfl-thesis-9036> Delgado experimental thesis; Delgado cavitation investigation
[14] <https://www.mdpi.com/1996-1073/12/24/4738> Laives PAT operating curves; Laives control comparison; €0.22/kWh Laives valuation
[15] <https://www.mdpi.com/2073-4441/15/15/2807> HYPER study, 2023; HYPER economic assumptions; HYPER commercial-pump comparison; HYPER layout analysis; HYPER evaluation horizon; HYPER market discussion, 2023…
[16] <https://www.canyonhydro.com/products/pump-as-turbine.html> Canyon pump-turbine package
[17] <https://www.irena.org/-/media/Files/IRENA/Agency/Publication/2012/RE_Technologies_Cost_Analysis-HYDROPOWER.pdf> IRENA hydropower cost analysis; IRENA equipment-life discussion; IRENA O&M and equipment life; IRENA hydropower classification
[18] <https://doi.org/10.3390/w14111785> PAT selection framework, 2022; Pugliese and Giugni cost model; PAT framework assumptions; €0.10/kWh framework assumption
[19] <https://doi.org/10.5327/z2176-94781551> Brazilian network analysis; Brazilian pressure counterexample
[20] <https://www.enr.com/articles/56240-mini-hydroturbines-in-water-pipes-gain-traction-for-clean-energy> Skagit utility account
[21] <https://www.mdpi.com/2071-1050/13/19/10717> DuoTurbo discussion of the irrigation comparison; DuoTurbo prototype and pilot; DuoTurbo monitoring; DuoTurbo continuity arrangement
[22] <https://doi.org/10.3390/w5031211> PAT system-effectiveness analysis
[23] <https://ascelibrary.org/doi/10.1061/%28ASCE%29WR.1943-5452.0001480> Four-case layout comparison
[24] <https://doi.org/10.3390/w12020468> PAT selection and curve-prediction study; PAT market comparison, 2020
[25] <https://ascelibrary.org/doi/10.1061/%28ASCE%29WR.1943-5452.0000384> Urban PAT automation arrangement
[26] <https://british-hydro.org/wp-content/uploads/2023/09/BHA-Micro-Hydro-Guide-2024-3.pdf> BHA guide, 2024; BHA system-life benchmark; BHA head classification; BHA micro-hydro efficiency benchmark; BHA development guidance
[27] <https://www.canyonhydro.com/micro/> Canyon micro-hydro products
[28] <https://www.voith.com/corp-en/products-services/hydropower-components/turbines.html> Voith turbine portfolio; Voith Pelton application; Voith Kaplan applications; Voith bulb/pit comparison; Voith spherical minimum-gap geometry; Voith oil-free a…
[29] <https://www.mdpi.com/2673-4931/21/1/80> KSB screening study; Thirty-eight-site PAT study
[30] <https://amslaurea.unibo.it/id/eprint/17855/1/Thesis-Mashkour.pdf> Mashkour thesis
[31] <https://iitr.ac.in/Departments/Hydro%20and%20Renewable%20Energy%20Department/static/Modern_hydroelectric_engg/vol_1/Chapter-3_Hydraulic_Turbine_Classification_and_Selection.pdf> IIT Roorkee turbine selection chapter
[32] <https://www.mdpi.com/2076-3417/13/24/13096> Rebolluelo case, 2023; Rebolluelo operating comparison; Rebolluelo cavitation and retrofit
[33] <https://www.ntnu.no/documents/381182060/1267681377/HYDRAULIC%2BTURBINES_Hermod%2BBrekke%2B-%2B2015.pdf> Brekke hydraulic equipment classification
[34] <https://www.sciencetheearth.com/uploads/2/4/6/5/24658156/electricity_use_and_management_in_the_municipal_water_supply_and_wastewater_industries.pdf> EPRI municipal-water energy report; EPRI excess-pressure recovery discussion
[35] <https://doi.org/10.1061/(asce)wr.1943-5452.0000700> Lausanne inline arrangement
[36] <https://doi.org/10.3390/w12092447> Demand-dependent network analysis; Energy recovery and leakage optimization
[37] <https://doi.org/10.1061/(asce)wr.1943-5452.0001201> Trondheim PAT arrangement
[38] <https://www.waterworld.com/water-utility-management/article/16201079/dynamic-pressure-control-enhances-urban-water-management> Urban dynamic-pressure management
[39] <https://www.canyonhydro.com/micro/microoptions.html> Pelton protection example
[40] <https://ascelibrary.org/doi/10.1061/%28ASCE%29WR.1943-5452.0001234> Laboratory pressure-regulating prototype
[41] <http://www1.eere.energy.gov/water/pdfs/doewater-10107-vol.1-pt1.pdf> DOE microhydropower handbook
[42] <https://doi.org/10.3390/modelling1020009> Smart-water monitoring review
[43] <https://doi.org/10.1080/1573062x.2021.1992455> Real-time control comparison
[44] <https://www.esmap.org/sites/default/files/esmap-files/FINAL_EECI-WWU_TR001-12_Resized.pdf> ESMAP municipal-water energy primer
[45] <https://doi.org/10.1007/s11269-014-0836-3>
[46] <https://doi.org/10.13189/aep.2014.020102>
[47] <https://doi.org/10.11648/j.ijrse.20200903.12>
[48] <https://doi.org/10.26190/unsworks/27069>
[49] <https://iris.univpm.it/retrieve/dd745ea9-3127-4698-81e7-6c8a613ad195/A%20methodology%20to%20forecast%20the%20main%20non-dimensional%20performance%20parameters%20of%20pumps-as-turbines%20%28PaTs%29%20operating%20at%20Best%20Efficiency%20Point%20%28BEP%29.pdf>
[50] <https://www.iris.unina.it/retrieve/e268a732-e639-4c8f-e053-1705fe0a812c/_published_1-s2.0-S0960148118302842-main.pdf>
[51] <https://doi.org/10.1016/j.renene.2018.01.053>
[52] <https://doi.org/10.3390/proceedings2110678>
[53] <https://www.mdpi.com/2071-1050/13/19/10717>
[54] <https://doi.org/10.3390/en10101666>
[55] <https://doi.org/10.3390/w12040958>
[56] <https://doi.org/10.3390/environsciproc2020002001>
[57] <https://openjicareport.jica.go.jp/pdf/11734134_04.pdf>
[58] <https://www.energy.gov/sites/default/files/2023-09/U.S.%20Hydropower%20Market%20Report%202023%20edition_20230928.pdf>
[59] <https://doi.org/10.6036/10874>
[60] <https://doi.org/10.3390/su12187352>
[61] <https://openjicareport.jica.go.jp/pdf/11737046_10.pdf>
[62] <https://doi.org/10.70530/kuset.v19i3.684>
[63] <https://www.scribd.com/document/642461428/The-gravitational-vortex-water-turbine-p>
[64] <http://5.imimg.com/data5/GH/HL/VQ/SELLER-7846758/vortex-micro-hydro-turbine.pdf>
[65] <https://doi.org/10.37624/ijert/13.7.2020.1508-1515>
[66] <https://herehydro.weebly.com/uploads/9/3/9/1/93913/crossflow_design.pdf>
[67] <https://researchportal.ulisboa.pt/en/publications/assessment-of-a-francis-micro-hydro-turbine-performance-installed/>
[68] <https://www.ncat.org/publication/micro-hydro-power-a-beginners-guide-to-design-and-installation/>
[69] <https://openjicareport.jica.go.jp/pdf/11737046_11.pdf>
[70] <https://www.sciencedirect.com/science/article/abs/pii/S096014811200479X>
[71] <https://doi.org/10.4236/sgre.2012.33033>
[72] <https://doi.org/10.5703/1288284316353>
[73] <https://www.iris.unina.it/retrieve/599b0c8f-52d4-4fbb-980c-fb088ef28015/water-14-01526-v2.pdf>
[74] <https://www.canyonhydro.com/micro/>
[75] <https://doi.org/10.1016/j.heliyon.2023.e17753>
[76] <http://www.ijlret.com/Papers/Vol-2-issue-5/6-B2016245.pdf>
[77] <http://infoscience.epfl.ch/record/150150>
[78] <https://british-hydro.org/wp-content/uploads/2023/09/BHA-Mini-Hydro-Guide-2024.pdf>
[79] <https://ascelibrary.com/doi/10.1061/%28ASCE%29HY.1943-7900.0001643>
[80] <https://doi.org/10.47176/jafm.17.1.1978>
[81] <https://eprints.ums.edu.my/id/eprint/38349/>
[82] <https://pure.kfupm.edu.sa/en/publications/parametric-study-of-single-stage-gravitational-water-vortex-turbi/>
[83] <https://www.shf-lhb.org/articles/lhb/pdf/1960/06/lhb1960042.pdf>
[84] <https://british-hydro.org/wp-content/uploads/2023/09/BHA-Micro-Hydro-Guide-2024-2.pdf>
[85] <https://doi.org/10.1063/5.0116535>
[86] <https://onlinelibrary.wiley.com/doi/full/10.1002/er.6893>
[87] <https://doi.org/10.1109/irec51415.2021.9427795>
[88] <https://doi.org/10.1063/5.0066853>
[89] <https://www.osti.gov/biblio/5426619>
[90] <https://jlahydro.be/power-solutions/hydraulic-turbines/cross-flow/?lang=en>
[91] <https://onlinelibrary.wiley.com/doi/10.1155/2021/5570848>
[92] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10497636/>
[93] <https://www.academia.edu/72418104/Study_of_Centrifugal_Pump_Operating_as_Turbine_in_Small_Hydropower_Plants>
[94] <https://ideas.repec.org/a/eee/renene/v78y2015icp1-6.html>
[95] <https://www.mdpi.com/2311-5521/2/4/51>
[96] <https://doi.org/10.3390/en15041528>
[97] <https://www.altestore.com/pages/micro-hydro-power-systems-overview?srsltid=AU7gw4VWYXsgVk0sG9zeYNwGzgp_xUozKh1Ak-RA2p4b5J80B_dxcMRy>
[98] <https://www.gw.govt.nz/assets/Documents/2009/07/2008_728_1_Report.pdf>
[99] <https://www.scribd.com/doc/283216194/Kaplan-Turbines>
[100] <https://www.academia.edu/27616082/Theoretical_Study_and_Performance_Test_of_Lucid_Spherical_Turbine>
[101] <https://repo.ijiert.org/index.php/ijiert/article/view/1941>
[102] <https://www.turbulent.be/technology>
[103] <https://www.mdpi.com/1996-1073/15/18/6542>
[104] <https://extension.umd.edu/resource/energy-101-hydropower>
[105] <https://www.iahr.org/library/infor?pid=19044>
[106] <https://www.ijee.ieefoundation.org/vol5/issue2/IJEE_02_v5n2.pdf>
[107] <https://www.ntnu.no/documents/381182060/1267681377/HYDRAULIC+TURBINES_Hermod+Brekke+-+2015.pdf>
[108] <http://hdl.handle.net/10467/66538>
[109] <https://jhd.co.jp/en/products/kaplan/>
[110] <http://hdl.handle.net/1807/109549>
[111] <https://mavel.cz/wp-content/uploads/2018/11/Gatefold_Kaplan_FINAL_electronic.pdf>
[112] <https://jsfm.shahroodut.ac.ir/article_2427.html?lang=en>
[113] <https://doi.org/10.3390/w11061194>
[114] <https://doi.org/10.3390/w15030554>
[115] <https://www.shf-lhb.org/articles/lhb/pdf/1999/03/lhb1999032.pdf>
[116] <https://www.osti.gov/etdeweb/servlets/purl/22132010>
[117] <https://morabito-a.github.io/info/files/2019-Deriaz.pdf>
[118] <http://hdl.handle.net/2263/45094>
[119] <https://www.hevs.ch/media/document/1/andolfatto_iahr2015.pdf>
[120] <https://www.waterpowermagazine.com/analysis/new-hydro-for-south-georgia-10914652/>
[121] <http://www.gilkes.com/media/1811/turgo-paper_a4_hr.pdf>
[122] <https://doi.org/10.3390/w12092447>
[123] <https://www.powervision-eng.ch/Profile/Publications/pdf/HPD_2011_Bieudron.pdf>
[124] <https://doi.org/10.3390/w15050973>
[125] <https://www.gugler.com/news/successes-in-switzerland/>
[126] <https://www.cgti.org.br/publicacoes/wp-content/uploads/2016/03/PROJETO-DE-TURBINAS-KAPLAN-%E2%80%93-NOVO-CONCEITO-DE-PROJETO-BASEADO-EM-EXEMPLOS-BRASILEIROS.pdf>
[127] <https://www.mas.bg.ac.rs/_media/istrazivanje/fme/vol33/3/6._aleksandar_gajic.pdf>
[128] <https://doi.org/10.1016/j.rser.2014.11.045>
[129] <https://pdfs.semanticscholar.org/973c/456837e278a024792ed0f77ecf3e63e9849f.pdf>
[130] <https://doi.org/10.56904/imejour.v2i2.206>
[131] <https://greenevo.gov.pl/en/technologies/francis-water-turbines/>
[132] <https://doi.org/10.3390/w15152807>
[133] <https://www.mdpi.com/2073-4441/5/3/1211>
[134] <https://ira.lib.polyu.edu.hk/bitstream/10397/102947/1/Yang_Micro_Hydro_Power.pdf>
[135] <https://ideas.repec.org/a/spr/waterr/v37y2023i3d10.1007_s11269-022-03421-9.html>
[136] <https://www.mdpi.com/2073-4441/15/3/554>
[137] <https://arodes.hes-so.ch/record/9747/files/Hasmatuchi_2016_energy_production_tubular_propeller_turbine.pdf>
[138] <https://doi.org/10.1061/(asce)wr.1943-5452.0000795>
[139] <https://ascelibrary.org/doi/10.1061/%28ASCE%29WR.1943-5452.0001063>
[140] <https://doi.org/10.1080/14786451.2023.2244606>
[141] <https://doi.org/10.1016/j.renene.2019.04.067>
[142] <https://wrap.warwick.ac.uk/id/eprint/36099/1/WRAP_THESIS_Alatorre-Frenk_1994.pdf>
[143] <https://doi.org/10.1007/s11269-022-03421-9>
[144] <https://www.mdpi.com/2311-5521/3/2/41>
[145] <https://doi.org/10.2166/ws.2017.154>
[146] <https://doi.org/10.3390/fluids3020041>
[147] <https://www.sdewes.org/jsdewes/pid9.0410>
[148] <https://mdpi-res.com/d_attachment/energies/energies-12-02103/article_deploy/energies-12-02103.pdf?version=1559372806>
[149] <https://www.sciencedirect.com/science/article/abs/pii/S0960148116305754>
[150] <https://www.wseas.us/e-library/conferences/2013/Chania/POW/POW-46.pdf>
[151] <https://www.mdpi.com/2073-4441/12/4/958>
[152] <https://www.iris.unina.it/retrieve/e268a732-02bc-4c8f-e053-1705fe0a812c/2018_Fine%20tuning%20a%20PAT%20hydropower%20plant%20in%20a%20water%20supply%20network%20to%20improve%20system%20effectiveness.pdf>
[153] <https://doi.org/10.3390/w11061297>
[154] <https://doi.org/10.3390/w12020330>
[155] <https://www.mdpi.com/2504-3900/2/23/1486>
[156] <https://doi.org/10.1080/1573062x.2021.1992455>
[157] <https://soarhydro.com/downloads/CANYON_PAT-SystemPackages_WEB-EN.pdf>
[158] <https://doi.org/10.2166/hydro.2020.140>
[159] <https://doi.org/10.3390/w15234123>
[160] <https://scholarsmine.mst.edu/cgi/viewcontent.cgi?article=1335&context=umr-mec>
[161] <https://www.matec-conferences.org/articles/matecconf/pdf/2018/63/matecconf_imiec2018_07019.pdf>
[162] <https://unsworks.unsw.edu.au/server/api/core/bitstreams/7f5114ad-e76d-4e64-9262-de6dfb3a3019/content>
[163] <https://www.sciencedirect.com/science/article/abs/pii/S2213138821000503>
[164] <https://doi.org/10.1016/j.renene.2015.06.049>
[165] <https://www.cell.com/heliyon/fulltext/S2405-8440(20)31367-0>
[166] <https://doi.org/10.3390/en6052362>
[167] <https://repository.elizadeuniversity.edu.ng/bitstreams/43268687-d61b-4cb6-9880-e50c63f36e16/download>
[168] <https://mdpi-res.com/d_attachment/water/water-12-00958/article_deploy/water-12-00958-v2.pdf?version=1585573543>
[169] <https://doi.org/10.3126/jie.v10i1.10895>
[170] <https://doi.org/10.7763/jocet.2016.v4.263>
[171] <https://hydrovio.gr/images/pdf/HYDRO-2020_PAPER.pdf>
[172] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8665341/>
[173] <https://resolver.obvsg.at/urn:nbn:at:at-ubi:1-70884>
[174] <https://doi.org/10.2166/hydro.2013.200>
[175] <https://www.mdpi.com/1996-1073/9/11/877>
[176] <https://doi.org/10.1680/jwama.20.00063>
[177] <https://doi.org/10.3390/w9050309>
[178] <https://www.researchgate.net/publication/305872670_Banki-Michell_micro-turbines_for_energy_production_in_water_distribution_networks_Proceedings_of_the_4th_IAHR_Europe_Congress_Liege_Belgium_27-29_July_2016>
[179] <https://www.iris.unina.it/retrieve/e268a730-3291-4c8f-e053-1705fe0a812c/_published_fluids-03-00041.pdf>
[180] <https://doi.org/10.3390/w10040529>
[181] <https://doi.org/10.3390/w16030504>
[182] <https://doi.org/10.1016/j.jenvman.2023.119229>
[183] <https://library.uniteddiversity.coop/Energy/Hydro/Directory_of_Manufacturers_of_Small_Hydro_Power.pdf>
[184] <https://doi.org/10.3390/en15145173>
[185] <https://www.osti.gov/servlets/purl/2583823>
[186] <https://www.canyonhydro.com/products/products.html>
[187] <https://infoscience.epfl.ch/bitstreams/bc6b5365-c12c-4e0c-8d6b-cc38625578eb/download>
[188] <https://infoscience.epfl.ch/server/api/core/bitstreams/bc6b5365-c12c-4e0c-8d6b-cc38625578eb/content>
[189] <https://doi.org/10.3390/w8080344>
[190] <https://www.osti.gov/servlets/purl/1305089>
[191] <https://www.waterpowermagazine.com/analysis/energy-recovery-from-public-water-systems/>
[192] <https://pdfs.semanticscholar.org/1ec8/0b14298c9e8b45952140708a3b03e165ffa4.pdf>
[193] <https://doi.org/10.3390/su15010651>
[194] <https://greenbugenergy.com/how-we-do-it/archimedes-screw-generators>
[195] <https://fenix.tecnico.ulisboa.pt/downloadFile/563345090415319/Thesis%20Final%20-%20Rita%20Ferreira.pdf>
[196] <https://tugraz.elsevierpure.com/en/publications/pressure-regulation-valves-for-energy-dissipation-and-power-contr-2/>
[197] <https://www.prescouter.com/2017/07/hydropower-water-distribution-networks/>
[198] <https://en.wikipedia.org/wiki/Pelton_wheel>
[199] <https://en.wikipedia.org/wiki/Cross-flow_turbine>
[200] <https://www.osti.gov/etdeweb/biblio/6511461>
[201] <https://www.canyonhydro.com/products/Canyon_References_Energy-Recovery.pdf>
[202] <https://www.academia.edu/104691137/Feasibility_Analysis_of_Energy_Recovery_Using_PATs_in_Water_Distribution_Networks>
[203] <https://repositorio.uti.edu.ec/items/0ea5756e-aada-4871-bd04-939f60274102/full>
[204] <https://doi.org/10.1016/j.heliyon.2024.e26084>
[205] <https://amslaurea.unibo.it/id/eprint/17855/1/Thesis-Mashkour.pdf>
[206] <https://www.energy.ca.gov/sites/default/files/2021-05/CEC-500-2020-030.pdf>
[207] <https://webgate.ec.europa.eu/life/publicWebsite/project/LIFE17-ENV-ES-000252/boosting-the-sustainability-of-the-urban-water-cycle-energy-harvest-in-water-industry-using-micro-hydropower-technology>
[208] <http://hdl.handle.net/11250/234640>
[209] <https://doi.org/10.1016/j.renene.2019.10.076>
[210] <https://doi.org/10.1016/j.apenergy.2018.06.079>
[211] <https://doi.org/10.1016/j.rineng.2025.106360>
[212] <https://www.researchgate.net/publication/363488250_A_review_of_micro_hydro_systems_in_urban_areas_Opportunities_and_challenges>
[213] <https://www.energy.gov/sites/prod/files/2018/02/f49/Hydropower-Vision-021518.pdf?_sp=ed0ef580-f2cb-4118-a5c5-1db9053d5b7d>
[214] <https://www.mdpi.com/1996-1944/16/9/3303>
[215] <https://www.academia.edu/69731811/Development_of_the_Turgo_Impulse_turbine_Past_and_present>
[216] <https://repository.unescap.org/server/api/core/bitstreams/412c7ac2-d24d-4215-96fd-16dbd774b143/content>
[217] <https://www.marketsandmarkets.com/Market-Reports/hydro-turbine-market-3405034.html>
[218] <https://irep.ntu.ac.uk/id/eprint/41109/1/10290112.pdf>
[219] <https://www.mdpi.com/2071-1050/13/19/10755>
[220] <https://downloads.unido.org/ot/48/12/4812700/10001-15000_14146.pdf>
[221] <https://eprints.lancs.ac.uk/id/eprint/82918/1/2016benzonphd.pdf>
[222] <https://blog.gridpro.com/understanding-the-flow-through-francis-turbines/>
[223] <https://doi.org/10.1016/j.rser.2015.07.007>
[224] <https://www.mdpi.com/2071-1050/15/1/651>
[225] <https://www.sciencedirect.com/science/article/abs/pii/S0360544221009026>
[226] <https://www.mdpi.com/1996-1073/16/20/7214>
[227] <https://europepmc.org/articles/pmc10250803?pdf=render>
[228] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10250803/>
[229] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10336523/>
[230] <https://www.wrc.org.za/wp-content/uploads/mdocs/2219.pdf>
[231] <https://doi.org/10.1016/j.renene.2018.04.070>
[232] <https://ijsea.com/archive/volume8/issue7/IJSEA08071005.pdf>
[233] <https://aast.edu/pheed/staffadminview/pdf_retreive.php?stafftype=staffpdf&url=25785_48_1_1-s2.0-S1364032114009769-main+Paper+1.pdf>
[234] <https://repository.up.ac.za/bitstreams/419852b1-444a-4f08-af12-8d8f19e9acea/download>
[235] <https://www.marketresearchfuture.com/reports/small-hydropower-market-11336>
[236] <https://www.energy.gov/cmei/water/types-hydropower-turbines>
[237] <https://www.hydropowermaintenance.com/turbine-types/>
[238] <https://microhydrony.org/2017/05/17/types-turbines/>
[239] <https://renewablesfirst.co.uk/renewable-energy-technologies/hydropower/hydropower-learning-centre/pelton-and-turgo-turbines/>
[240] <https://www.academia.edu/9768999/DESIGN_OF_HIGH_EFFICIENCY_PELTON_TURBINE_FOR_MICRO_HYDROPOWER_PLANT>
[241] <https://www.conceptsnrec.com/blog/reaction-versus-impulse-type-turbomachinery>
[242] <https://www.youtube.com/watch?v=k0BLOKEZ3KU&vl=en>
[243] <https://www.powermag.com/hydropower-horizons-pioneering-a-pelton-turbine-breakthrough/>
[244] <https://www.minenergia.cl/archivos_bajar/Catalogo_21agosto.pdf>
[245] <https://www.statkraft.com/energy-insights/articles/renewable-new-turbine-technology-will-make-hydropower-more-flexible/>
[246] <https://hydro.org/powerhouse/article/the-advantages-of-energy-recovery-using-hydropower/>
[247] <http://www.scielo.org.co/pdf/inco/v15n1/v15n1a17.pdf>
[248] <https://doi.org/10.22214/ijraset.2017.11041>
[249] <https://www.hydronome.fr/index.php/en/pelton-turbines/>
[250] <https://irispublishers.com/ctcse/fulltext/the-revival-of-old-hydraulic-turbines-for-innovative-hydropower-generation-water-wheels.ID.000625.php>
[251] <https://www.canyonhydro.com/news_sp/Dewitt_IWP_Jun2011.pdf>
[252] <https://savree.com/en/encyclopedia/hydro-turbine-comparison-model>
[253] <https://waterturbines.wikidot.com/main:types-of-water-turbines>
[254] <https://www.micro-hydro-power.com/how-much-does-a-3-kw-hydro-turbine-cost-the-complete-buying-guide/>
[255] <https://doi.org/10.1016/j.envsoft.2018.08.018>
[256] <https://pdfs.semanticscholar.org/0fa5/8e4c8e40fe7791598789e3589619cf9590b5.pdf>
[257] <https://www.micro-hydro-power.com/Turgo-Inclined-Jet-Turbine.htm>
[258] <https://en.wikipedia.org/wiki/Turgo_turbine>
[259] <https://formacion-industrial.com/en/2020/12/31/francis-turbine-how-it-works-parts-head-range/>
[260] <https://www.diva-portal.org/smash/get/diva2:572692/fulltext01>
[261] <https://www.heliciel.com/en/helice/turbines%20hydraulique/turbine%20hydraulique%201%20%20helice%20bulbe%20kaplan.htm>
[262] <https://www.scribd.com/document/412037137/352146IJSETR1300-322>
[263] <https://www.scribd.com/document/922075344/Derrick-Turbine>
[264] <https://www.cnr.gob.cl/wp-content/uploads/2019/12/Informe-Estudio-Mercado-Microhidro-v11.0-12.05.2016.pdf>
[265] <https://www.cink-hydro-energy.com/crossflow-turbines>
[266] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10179411/>
[267] <https://doi.org/10.1016/j.apenergy.2015.12.091>
[268] <https://link.springer.com/article/10.1016/j.jksues.2020.04.011>
[269] <https://doi.org/10.1016/j.oceaneng.2022.111582>
[270] <https://doi.org/10.1049/iet-rpg.2019.1283>
[271] <https://www.mdpi.com/2071-1050/12/18/7352>
[272] <https://doi.org/10.3390/ijerph17249236>
[273] <https://eprints.lancs.ac.uk/id/eprint/78463/1/APEN_7411_edit_report.pdf>
[274] <https://www.canyonhydro.com/guide/HydroGuide4.html>
[275] <https://www.mdpi.com/1996-1073/11/2/267>
[276] <https://iitr.ac.in/Departments/Hydro%20and%20Renewable%20Energy%20Department/static/Modern_hydroelectric_engg/vol_1/Chapter-3_Hydraulic_Turbine_Classification_and_Selection.pdf>
[277] <https://www.jstage.jst.go.jp/article/ijfms/15/1/15_130/_pdf/-char/en>
[278] <https://waterprojectsonline.com/mini-case-studies/gilkes-glencorse/>
[279] <https://www.micro-hydro-power.com/Francis-Turbine-Large-Hydro-Power.htm>
[280] <https://www.sunecohydro.com/turgo-turbine/>
[281] <https://www.facebook.com/civiltechtime/posts/stream-powered-cross-flow-turbine-systema-cross-flow-turbine-banki-turbine-is-a-/1423568069901871/>
[282] <https://www.omicsonline.org/open-access-pdfs/crossflow-turbine-design-specifications-for-hhaynu-microhydropower-plantmbulu-tanzania.pdf>
[283] <https://fenix.tecnico.ulisboa.pt/departamentos/decivil/dissertacao/1128253548921473>
[284] <https://ideas.repec.org/a/eee/renene/v252y2025ics0960148125012224.html>
[285] <https://info.ornl.gov/sites/publications/Files/Pub177421.pdf>
[286] <https://repo.ijiert.org/index.php/ijiert/article/view/1941/1823>
[287] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10926066/>
[288] <https://www.cmff.hu/cmff18/proceedings/former/CMFF03/pdfs/1214.pdf>
[289] <https://bibliotekanauki.pl/articles/1931595.pdf>
[290] <https://doi.org/10.3390/w14101649>
[291] <https://energyeducation.ca/encyclopedia/Crossflow_turbine>
[292] <https://www.energyencyclopedia.com/en/renewable-energy/water-energy/francis-turbine>
[293] <https://doi.org/10.2166/aqua.2019.161>
[294] <https://www.water21.org.uk/wp-content/uploads/2012/02/Kaplan-Turbines-en.pdf>
[295] <https://pdfs.semanticscholar.org/50a7/388975d84ae24e2c123238e653482c66c85f.pdf>
[296] <https://iris.polito.it/bitstream/11583/2960355/1/1-s2.0-S2213138821009383-main_compressed.pdf>
[297] <https://doi.org/10.3390/w9020097>
[298] <https://www.youtube.com/watch?v=XK6RF8CZ9-I>
[299] <https://hydro-tinck.com/kaplan-turbines/>
[300] <https://sunnytek.se/sunnytek-web-site-in-englis/hydro-power-systems-and/kaplan-turbine-50kw--2.pdf>
[301] <https://doi.org/10.2991/aer.k.211106.012>
[302] <https://www.cink-hydro-energy.com/kaplan-turbines>
[303] <https://khazna.ku.ac.ae/ws/portalfiles/portal/27981773/file>
[304] <https://doi.org/10.5293/kfma.2018.21.3.044>
[305] <http://journal.esperg.com/index.php/TIJEE/article/download/3350/1512>
[306] <https://www.spaansbabcock.com/wp-content/uploads/2017/03/SB15009_Screw_Turbine_EN_LR.pdf>
[307] <https://link.springer.com/article/10.1007/s10098-023-02641-w?code=f23f7055-cb9a-4f63-8f45-8b31d40b34e5&error=cookies_not_supported>
[308] <https://fr.scribd.com/document/229759182/Deriaz-Turbine>
[309] <https://doi.org/10.3390/pr9122128>
[310] <https://ideas.repec.org/a/eee/energy/v137y2017icp431-440.html>
[311] <https://doi.org/10.1016/j.est.2019.100788>
[312] <https://www.crses.sun.ac.za/files/research/completed-research/other/bh_teuteberg.pdf>
[313] <https://www.mass.gov/doc/hydropower-its-use-at-public-water-systems-in-massachusetts/download>
[314] <https://doi.org/10.1088/1742-6596/1276/1/012024>
[315] <https://www.usbr.gov/tsc/techreferences/hydraulics_lab/pubs/HL/HL-2016-09.pdf>
[316] <https://doi.org/10.3390/w11081659>
[317] <https://asrjetsjournal.org/American_Scientific_Journal/article/download/2436/996/7419>
[318] <https://iwaponline.com/jh/article/17/3/347/3663/Pump-as-turbine-implementation-in-a-dynamic>
[319] <https://www.mdpi.com/2073-4441/11/6/1297>
[320] <https://eureka.patsnap.com/report-comparison-of-recovery-performance-between-francis-turbine-draft-tube-and-elbow-draft-tube>
[321] <https://www.iris.unina.it/retrieve/95d29759-1939-4f1f-9625-97486ab79ae3/water-14-01785-v2.pdf>
[322] <https://pdfs.semanticscholar.org/8f50/668842920596b234a80dc67aca6f332e980f.pdf>
[323] <https://doi.org/10.2166/ws.2017.087>
[324] <https://atrium.lib.uoguelph.ca/server/api/core/bitstreams/de06270b-8b09-49d3-8808-9357c4876cf6/content>
[325] <https://ep.liu.se/ecp/057/vol6/002/ecp57vol6_002.pdf>
[326] <https://www.unalaska.gov/sites/default/files/fileattachments/Mayor%20and%20City%20Council/page/8061/12_pyramid_micro_turbine_project.pdf>
[327] <https://energiazero.org/cartelle/idroelettrico/archimede/Archimedean%20Screw%20Turbine%20book.pdf>
[328] <https://doi.org/10.3390/w14050710>
[329] <https://doi.org/10.1080/1573062x.2018.1459747>
[330] <https://www.sciencedirect.com/science/article/abs/pii/S0360544218310922>
[331] <https://www.waterandenergyconsulting.com/recapture.pdf>
[332] <https://eureka.patsnap.com/report-comparison-between-francis-turbine-and-pelton-wheel-for-suitability-at-medium-head-sites>
[333] <https://ira.lib.polyu.edu.hk/handle/10397/102911?mode=full>
[334] <https://en.wikipedia.org/wiki/Crossflow_turbine>
[335] <https://www.ewra.net/wuj/pdf/WUJ_2014_07_03.pdf>
[336] <https://www.mdpi.com/2071-1050/14/23/15948>
[337] <https://www.powermag.com/optimizing-kaplan-turbine-efficiency-with-minimal-cost-effort-and-time/>
[338] <https://cordis.europa.eu/project/id/HY.-00360-89/de>
[339] <http://tamanini.it/wp/wp-content/uploads/2017/03/Techno_Economic-feasibility-analysis-for-energy-production-by-variable-speed-Francis-turbines-in-water-distribution-networks.pdf>
[340] <https://kiss.kstudy.com/Detail/Ar>
[341] <https://www.irena.org/-/media/Files/IRENA/Agency/Publication/2012/RE_Technologies_Cost_Analysis-HYDROPOWER.pdf>
[342] <https://pubs.aip.org/aip/acp/article/2386/1/040042/2821458/Performance-analysis-of-in-pipe-spherical-water>
[343] <https://doi.org/10.1063/5.0002920>
[344] <https://doi.org/10.1109/inmic.2013.6731326>
[345] <https://www.energy.gov/cmei/water/articles/21st-century-archimedes-screw-new-materials-and-manufacturing-techniques-enable>
[346] <https://www.firgelliauto.com/blogs/mechanisms/archimedian-screw-water-lift?srsltid=AU7gw4UN1jHWgu01fZzq6L7rG8KN7xi-LnL4WR83SZP2TP1Y2TQs2p1Q>
[347] <https://tethys-engineering.pnnl.gov/technology/archimedes-screw>
[348] <https://doi.org/10.5772/intechopen.100492>
[349] <https://doi.org/10.1109/icrera.2016.7884485>
[350] <https://www.scribd.com/document/396179947/The-Gravitational-Vortex-Water-Turbine-Puts-Small-Hydro-on-the-Map-EE-Publishers>
[351] <https://nrc-publications.canada.ca/eng/view/accepted/?id=d6084d10-3ce2-4483-a1ff-1473ff8955d2>
[352] <https://www.wateronline.com/doc/in-line-turbines-harness-energy-for-water-utilities-0001>
[353] <https://www.theprif.org/sites/theprif.org/files/documents/huro_mini_hydropower_scheme_feasibility_study_june_2010.pdf>
