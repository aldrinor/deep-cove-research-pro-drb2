# Low-Voltage SRAM: Alternate Cell Designs, Eight Assist Schemes, and Performance Comparisons

**The central problem is competing margins.** Conventional 6T SRAM offers excellent density, but its shared read/write access path creates a conflict: access devices must be weak enough to avoid disturbing stored data during reading and strong enough to overwrite the latch during writing. Lower supply voltage magnifies device variation, weakens read current, and makes accumulated bitline leakage harder to distinguish from a selected cell’s signal. The mainstream remedies are therefore either to change the cell topology—using 7T through 12T structures—or to change wordline, bitline, supply, and ground voltages temporarily through assist circuits. [1]

**More transistors do not guarantee superiority.** An isolated read port can greatly improve read stability without improving write half-select behavior; feedback cutting can improve writability while increasing timing and routing complexity. Conversely, a carefully assisted 6T implementation can remain competitive: Kumar et al. reported a 28 nm FDSOI 6T SRAM operating at 0.5 V using wordline-underdrive read assist and negative-bitline write assist. A fabricated 7 nm FinFET 12T compiler reached a reported minimum operating voltage of 290 mV, illustrating the different operating range available when density is traded for stronger cell-level isolation. [2][3]

**The report answers three questions.** First, it explains what each requested transistor-count family changes relative to 6T and identifies its principal controls. Second, it compares exactly eight assist schemes by operation, mechanism, and overhead. Third, it presents a fully populated performance table, separating published results from explicitly conditional calculations and interpreting the strongest within-study comparisons.

**Selection starts with the failure mode.** The following map summarizes representative choices; the detailed discussion explains why different variants within one transistor count can behave differently.

| Candidate | Principal problem addressed | Read approach | Write approach | Main cost |
|---|---|---|---|---|
| 6T plus assist [2] | Read/write margin loss | Underdriven WL | Negative BL | Bias generation and timing |
| 7T [4] | Area-conscious low-voltage access | Compact single-ended port | Virtual-ground control | Reference and rail controls |
| 8T [5] | Read disturb | Isolated 2T read stack | Usually 6T-like | Extra read lines and sensing |
| 9T [6] | Read and half-select disturbance | Independent read port | Cross-point, data-aware access | Selection and assist circuitry |
| 10T [7] | Read/write contention | Buffered or pulse-decoupled | Feedback or supply control | Additional controls and devices |
| 11T [8] | Weak writing and leakage | Isolated or stacked path | Stronger access, weaker feedback | Bias, feedback, and timing circuits |
| 12T [9] | Deep-low-voltage robustness | Differential or isolated read | Column selection or feedback cutting | Cell area and peripheral complexity |

## 1. Alternate Cell Designs

### The 6T baseline and its low-voltage failure mechanisms

**The baseline shares its access devices.** A conventional 6T cell comprises two cross-coupled CMOS inverters—four storage transistors—and two access transistors. A row wordline, WL, connects the complementary storage nodes, Q and QB, to the column bitlines, BL and BLB. During reading, the bitlines are initially charged and the selected cell develops a voltage difference for a sense amplifier; during writing, external drivers force complementary bitline values that overwrite the latch. [10]

**Reading exposes the stored zero.** When a precharged bitline connects to the node storing zero, the access transistor and the cell’s pull-down transistor form a voltage divider. The internal zero rises temporarily. If it rises beyond the switching threshold of the opposite inverter, the cross-coupled latch can regenerate the disturbance into a bit flip. Stronger pull-down devices and weaker access devices reduce that risk. [11]

**Writing requires the opposite intervention.** To write zero onto a node initially storing one, the access transistor must discharge that node against the pull-up PMOS. Strong access devices and weak pull-ups therefore improve writability. The practical sizing hierarchy is not simply “make every transistor stronger”: it is to maintain sufficient pull-down-to-access strength for reading while maintaining sufficient access-to-pull-up strength for writing. Device mismatch can upset either relationship. [12]

**Voltage scaling magnifies current variation.** In subthreshold operation, transistor current depends exponentially on gate and threshold voltage. A threshold mismatch that is tolerable at a higher supply can consequently produce a large current imbalance near or below threshold. Kim, Liu, and Kim identify reduced read static noise margin, poor writability, smaller on/off-current ratio, and greater process, voltage, and temperature sensitivity as the principal obstacles to low-voltage SRAM. [13]

**Static margins describe different failures.** Static noise margin, SNM, measures the DC disturbance a cell tolerates without losing its intended state. Hold SNM concerns retention with access disabled; read SNM concerns retention under read bias; write margin concerns the ability to force a state change. A large hold margin does not automatically imply a large read margin, and neither establishes that a write will complete within a specified pulse width. [10]

**Array yield sharpens the requirement.** Kumar et al.’s single-well 28 nm UTBB FDSOI study targeted six-sigma qualification and found that the conventional cell’s SNM and write margin fell short below approximately 750 mV and 700 mV, respectively. Those values describe that implementation and qualification target; their significance is that an SRAM array can become voltage-limited by statistical margin before nominal logic stops functioning. [2]

**Read isolation leaves sensing problems.** Even when the storage node is electrically isolated, a read bitline still connects many unselected read ports. Their leakage can discharge a line that should remain high or alter the discharge rate of a line representing zero. Do et al. show that the difficulty depends on both the selected-cell current and the stored-data pattern throughout the column. [14]

**Current separation governs successful sensing.** Expressing the worst-case column condition with minimum and maximum unselected-cell leakage gives the following useful relationship, where \(n\) is the number of cells sharing the read bitline. [14]

\[
I_{\mathrm{cell},0}-I_{\mathrm{cell},1}>(n-1)\left(I_{\mathrm{leak,max}}-I_{\mathrm{leak,min}}\right).
\]

**The equation explains two remedies.** Increasing selected-cell current improves the left-hand side; reducing or equalizing data-dependent leakage reduces the right-hand side. Shorter local bitlines also help by reducing both the number of leakage contributors and bitline capacitance. Thus, read-port design, leakage compensation, bitline hierarchy, and sense-amplifier design address related but distinct limitations.

**Half-selection creates another operating state.** In a column-multiplexed array, asserting a row wordline can expose cells whose columns are not being written. Those cells may experience a read-like disturbance while a neighboring cell receives write data. Bit interleaving—which places adjacent physical bits in different logical words to improve error-correction effectiveness—makes this behavior particularly important. Read-disturb immunity alone does not establish write half-select immunity. [6]

**The baseline remains a serious candidate.** Kutila, Paasio, and Lehtonen’s 130 nm near-threshold comparison reported acceptable read reliability for their 6T design together with 31% smaller area and lower power than the compared 8T design. The appropriate judgment is therefore conditional: retain 6T when the target array meets its yield, timing, and half-select requirements economically; change the topology when a shared electrical path prevents those requirements from being met. [15]

### 7T cells: compact read access and selective feedback or ground control

**7T is an incremental architecture family.** Adding one transistor can interrupt a disturbing feedback path, provide a compact read function, or support a different access arrangement. Consequently, “7T” identifies a device count, not one universally defined schematic. A representative near-threshold implementation is Yeoh et al.’s 2013 design, combining a single-transistor read port with reference sensing, write-through virtual ground, and fine-grained power management. [4]

**The read port minimizes cell overhead.** Yeoh’s single-ended 1T read arrangement avoids the area of a conventional two-device isolated read stack. Its small read-bitline signal is resolved using a process-, voltage-, and temperature-tracking reference. The reference is essential to the architecture: the saved cell device does not eliminate the need to distinguish a weak selected-cell signal from leakage and circuit variation. [4]

**Virtual-ground timing improves dynamic stability.** The write-through virtual-ground scheme, WTVG, limits how long the relevant virtual ground disturbs neighboring cells during a write. The paper reports a 6.1-fold reduction in the write-disturbance period. This is a timing-based improvement: shortening exposure can preserve a cell that would be less robust under a continuously applied disturbance. [4]

**Power gating targets unaccessed circuitry.** Ultra-fine-grain power gating, UFPG, suppresses leakage associated with unaccessed portions of the memory. In the fabricated 16 kb, 65 nm test chip, the authors report 52% leakage suppression after initial power-up and a minimum energy of 2.01 pJ at 0.4 V. The leakage and operating-frequency characterization includes measurements at 27 °C. [4]

**The controls extend beyond WL.** The following inventory distinguishes data lines, selection signals, virtual rails, and sensing controls in this representative implementation. [4]

| Signal | Role |
|---|---|
| WL | Row access control |
| COL | Column selection |
| WBL/WBLB | Complementary write-data lines |
| RBL | Single-ended read-data line |
| RD_VGND | Read-path virtual-ground control |
| WR_VGND | Write-through virtual-ground control |
| VREF | Tracking read reference |
| SA Enable | Sense-amplifier activation |

**Feedback-interruption variants solve a different problem.** Namdev and Rawat describe Takeda et al.’s read-static-noise-margin-free 7T approach as adding a transistor that turns off during reading, preventing an internal disturbance from propagating through the normal regenerative path. Their signal description uses WL for writing and a separate R read control with BL_1 and BL_2. That design should not be treated as identical to Yeoh’s 1T-read-port implementation. [16]

**An extra device can save area.** Namdev and Rawat’s summary reports 23% smaller area than conventional 6T at the same speed for the cited read-SNM-free 7T design. This is an equal-performance comparison: removing a sizing constraint can allow sufficient device downsizing to outweigh the added transistor. It does not imply that every minimum-sized 7T layout is smaller than every minimum-sized 6T layout. [16]

**The trade is peripheral dependence.** A compact 7T cell is attractive when cell area, leakage, and moderate-voltage energy dominate. Its advantage weakens if reference generation, virtual-ground distribution, or worst-case single-ended sensing requires substantial additional circuitry. An 8T alternative becomes more attractive when direct storage-node isolation gives a larger reliability benefit than the seventh-transistor economy.

**7T takeaway:** A well-chosen seventh device can remove a specific constraint efficiently, but the reference, feedback, and virtual-ground implementation determines which constraint is actually removed.

### 8T cells: a conventional write core with an isolated read stack

**8T directly separates read disturbance.** The conventional read-decoupled 8T cell retains a 6T storage/write core and adds two NMOS devices in a dedicated read path. One device senses a storage-node voltage through its gate; the other selects the read. Read current therefore flows through the added stack rather than through the storage node. [5]

**Isolation relaxes the sizing conflict.** Because the read bitline is not conductively connected to the latch node, its precharged charge does not raise the stored zero in the same manner as a 6T read. Read SNM can consequently approach hold SNM, allowing storage and write-access devices to be optimized more independently. The read stack can then be sized according to current, leakage, and sensing requirements. [17]

**Read operation uses a separate control.** In a conventional dynamic implementation, RBL is charged before reading. Asserting the read wordline, RWL, permits a data-dependent discharge through the read stack. The write wordline remains inactive, keeping the write bitlines disconnected from Q and QB. Writing instead asserts WWL and drives WBL/WBLB while the read port remains disabled. [14]

| Signal | Role |
|---|---|
| WL or WWL | Enables the conventional write-access pair |
| RWL | Selects the isolated read stack |
| WBL/WBLB | Carries complementary write data |
| RBL | Carries single-ended read information |
| VSSRD or VGND | Optional read-return bias and column control |
| WL_RD | Local read-buffer enable in hierarchical variants |

**The names belong to particular implementations.** For example, Sharma et al.’s hierarchical 8T architecture activates an accessed column by connecting VSSRD to ground, then uses WL_RD to enable a local read buffer. At 0.55 V in 40 nm low-power CMOS, the reported nominal read delay changes from 22.9 ns to 5.35 ns; the paper separately reports a 6.5-fold improvement at the slow-device corner. [18]

**Channel engineering can strengthen access.** Kim, Liu, and Kim’s 130 nm implementation exploits the reverse short-channel effect, RSCE. It uses write-access channels three times the minimum length and read-path channels twice the minimum length. In that process and low-voltage regime, the threshold-voltage behavior makes longer channels useful for improving drive without the same bitline-junction-capacitance penalty as simply widening devices. [5]

**The area denominator matters.** The RSCE cell incurs a reported 20% area overhead relative to an all-minimum-sized 8T cell, not relative to 6T. The paper reports 66 mV, or 33%, write-margin improvement and 56.9% read-performance improvement at 0.2 V relative to its previous 8T comparison. These results demonstrate an additional optimization within the 8T family rather than a benefit attributable to transistor count alone. [5]

**Leakage compensation extends voltage scaling.** The same 64 kb SRAM uses marginal bitline-leakage compensation, MBLC, and reports minimum operation at 0.26 V with 512 cells per bitline. A replica bitline establishes compensation strength so that the accessed read line settles near the sense-amplifier trip point. Unlike the conventional dynamic example above, this scheme determines read levels through current balance and eliminates the normal read-bitline precharge requirement. [13]

**Read isolation does not fix writing.** The remaining write core is still 6T-like. Row half-selected cells can therefore experience pseudo-read disturbance during a write. Kim et al. explicitly note that stronger RSCE access devices reduce half-selected stability and discuss writeback as a remedy, while stating that writeback was not implemented in their test chip. [5]

**Single-ended sensing becomes the next bottleneck.** Do et al.’s fabricated 32 kb, 65 nm 8T array combines column-data randomization, bitline biasing, and a dynamic keeper. It operates at 0.2 V with a measured 2.5 µs read access time at room temperature. The detailed results place its minimum read energy of 1 pJ/access at 0.4 V, showing that the lowest functional voltage is not necessarily the minimum-energy operating voltage. [14]

**8T takeaway:** The isolated 2T read port is a strong remedy for read disturb, but successful low-voltage arrays still require attention to leakage-dependent sensing and write half-selection.

### 9T cells: independent ports, leakage equalization, and cross-point writing

**The ninth device broadens isolation options.** One established 9T structure combines a 6T storage/write subcircuit with three read-path transistors. In the description by Singh et al., stored data controls two read devices and a separate RD signal controls the third. WL continues to control the conventional write-access pair. [19]

**Different 9T variants address different constraints.** A three-device read path can improve isolation or leakage behavior; a different arrangement can provide local wordline qualification or cross-point writing. These functions should be distinguished because an isolated read path does not, by itself, guarantee half-select-free writing or data-independent read leakage.

| Representative 9T variant | Core improvement | Principal controls | Main trade-off |
|---|---|---|---|
| 6T core plus 3T read path [19] | Storage-node read isolation | WL, RD, bitlines | Read-stack loading |
| Cross-point two-port cell [6] | Read and write-disturb protection | Read WL, write WL, RBL, WBL | Selection and aligned assists |
| Leakage-equalized MTCMOS cell [20] | Improved sensing margin | Read/write controls, RBL, CAM control | CAM and mixed-threshold circuitry |
| Local-wordline variant [16] | Read protection and qualified access | WL, LWL, RWL, CBLB | Local selection logic |

**Cross-point access protects neighboring cells.** Lu et al.’s two-port 9T cell uses independent single-ended read and write bitlines together with a cross-point data-aware write structure. Joint row and column qualification prevents a cell selected in only one dimension from undergoing the same destructive write conditions as the fully selected cell. That property supports bit interleaving for improved soft-error handling with error-correcting codes. [6]

**Aligned assists strengthen the selected write.** Lu’s implementation aligns boosted write-wordline and negative write-bitline waveforms. Both are triggered by the same low-going global write bitline, reducing the possibility that one assist arrives too early or too late relative to the other. The mechanism combines increased access-device gate drive with a stronger low-going write input. [6]

**Measured results establish the operating range.** The 72 kb test chip in UMC 40 nm low-power CMOS functions from 1.5 V to 0.32 V without redundancy. At 25 °C, the reported maximum frequency is 260 MHz at 1.1 V and 450 kHz at 0.32 V. At 0.325 V, it operates at 600 kHz with 5.78 µW total power and 4.69 µW leakage power. [6]

**Leakage dominates that low-voltage point.** The leakage fraction is approximately 81.1%, calculated as \(4.69/5.78\). Subtracting the reported leakage from total power gives 1.09 µW of non-leakage power for that operating condition. The implication is practical: reducing switched bitline energy alone has limited leverage when most power is spent retaining the array between accesses.

**Leakage equalization addresses another failure.** Wang et al.’s 65 nm, 16 kb MTCMOS implementation uses a three-transistor read port to remove data dependence from read-bitline leakage. A miniature content-addressable-memory, CAM, assist conceals slow data development after a write transition involving high-threshold devices. Equalization improves read distinguishability, whereas CAM assistance improves the effective write-performance path. [20]

**Its voltage-dependent timing spans orders.** Wang et al. report operation from 1.2 V to 0.26 V, with read access ranging from 6 ns to 0.85 µs across that voltage range. Minimum energy is 2.07 pJ at 0.4 V. These results reinforce that supply voltage and peripheral techniques can have a much larger influence on access time than the difference between eight and nine devices. [20]

**Signal aliases require topology-specific interpretation.** RWL, RD, or RDL denotes read control in different papers; WL, WWL, or WDL denotes write access. RBL carries read information, while WBL or BL carries write data. In the local-wordline variant summarized by Namdev and Rawat, WL activates local selection, LWL is the local wordline, RWL controls read access, and CBLB controls the added protection transistor. [16]

**The extra read stack has costs.** More devices connected to bitlines can increase capacitance, and series devices can reduce selected read current. A 9T design is attractive when leakage equalization, independent ports, or half-select protection removes the actual array limitation; a simpler 8T cell may be preferable when its sensing margin is already adequate and cross-point writing is unnecessary.

**9T takeaway:** The strongest 9T solutions improve the entire access environment—selection, leakage, and write timing—not merely the nominal cell read margin.

### 10T cells: buffered reads, Schmitt triggers, and controlled feedback

**10T includes several distinct strategies.** Important examples are a 6T-like latch with a four-transistor read port, a Schmitt-trigger storage core, pulse-controlled dynamic read decoupling, and data-aware supply interruption. Their operating principles differ enough that one generic “10T sensing method” or delay value would conceal important design choices. [1][7]

| 10T approach | Main mechanism | Read arrangement | Key added controls |
|---|---|---|---|
| Decoupled 4T read port | Isolates read and reduces leakage | Dedicated RBL | RWL, WWL, WB |
| Schmitt-trigger ST2 | Raises disturbance-resistant trip point | Differential access | WL, WWL |
| PNN-10T | Pulse decoupling and data-aware writing | BL/BLB with pulsed isolation | CL/CR, PG, Write_EN |
| SEDF10T | Data-aware supply interruption | Separate single-ended buffer | WLA, WLB, VVSS |

**The decoupled cell preserves hold-mode stability.** Kim et al.’s 10T structure comprises the cross-coupled inverter pair, write-access devices, and a four-transistor read port. RWL conditionally discharges RBL without directly exposing the storage node to the bitline. WBL/WBLB and WWL control writing. [1]

**Writeback protects unselected columns.** During the writeback sequence, RWL and WWL are asserted together and the sensed contents of unselected columns are returned through the write drivers. WB is activated after a replica-bitline delay. The cell-level isolation is therefore complemented by peripheral sensing, feedback, and timing circuitry to preserve half-selected data. [1]

**Silicon demonstrates long-column operation.** The associated fabricated 480 kb SRAM in 130 nm CMOS operates at 100 kHz and 0.2 V at 27 °C with 1,000 cells per bitline. Reported leakage current is 10 µA, equivalent to 2 µW calculated from \(0.2\text{ V}\times10\text{ µA}\). A 1,000-cell quadrant remains readable at 0.17 V. These are combined cell-and-periphery results rather than an isolated benefit from four extra transistors. [1]

**Schmitt triggers change the latch itself.** A Schmitt-trigger inverter has a switching threshold influenced by feedback and transition direction. In an SRAM, that feedback can raise the voltage excursion needed to upset a stored state during reading. A reviewed 10T Schmitt-trigger design reports 1.56 times the conventional 6T read SNM with a 33% area penalty. Unlike an isolated read buffer, this mechanism strengthens the storage characteristic rather than simply removing the read-current connection. [17]

**PNN-10T uses timed internal isolation.** The 2021 PNN-10T cell uses two PMOS and four NMOS devices in its cross-coupled latch, plus four access devices. CL and CR control the additional latch switches. A pulse generator, PG, briefly changes CL/CR during a read, dynamically isolating the vulnerable storage path; during writing, external Data/Datab determines which path is weakened. [7]

**Read and write controls cooperate.** RWL controls the first access-device pair, and WWL controls the second. During writing, both are asserted. Write_EN selects write-data-aware behavior; when it is inactive, CL/CR maintain the hold state or follow the read-assist pulse. The source’s operating table is summarized below. [7]

| Operation | Write_EN | RWL/WWL | BL/BLB | CL/CR |
|---|---:|---|---|---|
| Hold | 0 | 0/0 | 1/1 | 1/1 |
| Read | 0 | 1/0 | 1/1, floating | Pulse |
| Write 0 | 1 | 1/1 | 0/1 | 1/0 |
| Write 1 | 1 | 1/1 | 1/0 | 0/1 |

**The pulse changes the vulnerable state.** At 0.3 V, the paper reports read SNM of 13.17 mV without the temporary switch turn-off and 45.81 mV with it. That approximately 3.48-fold increase, calculated as \(45.81/13.17\), establishes why pulse timing is consequential. The implementation must supply sufficient sensing time without leaving the latch in an unnecessarily vulnerable temporary configuration. [7]

**Data-aware writing attacks contention directly.** For a write, CL/CR cuts off the opposing pull-down path while the enabled side supplies an additional discharge route. The design therefore improves the ability to raise one storage node and lower the other without requiring an external boosted supply. The trade is additional internal control generation and routing rather than a charge pump. [7]

**Post-layout results provide macro-level anchors.** The TSMC 40 nm GP implementation uses a 32-by-32, 1 kb macro. At 0.3 V and 10 MHz, its post-layout simulation reports 4.15 µW read power, 3.82 µW write power, and approximately 0.39 pJ average energy/access. The bit-cell footprint is 3.28 µm², and retention power is 3.64 µW. [7]

**SEDF10T weakens the appropriate inverter.** Mansore and Gamad’s single-ended, read-disturb-free cell uses supply interruption for writability, a separate read buffer, a shared single bitline, and cross-point write selection. M1 and M4 interrupt the left or right inverter supply; M7/M8 provide write access; M9/M10 form the read buffer. [11]

**Its control vector is explicit.** The source uses WL, WLA, WLB, VVSS, and BL with the following states. WLA/WLB distinguish the data-dependent write action, while VVSS establishes the read/hold return condition. [11]

| Operation | WL | WLA | WLB | VVSS | BL |
|---|---:|---:|---:|---:|---:|
| Write 0 | 1 | 1 | 0 | 0 | 0 |
| Write 1 | 1 | 0 | 1 | 0 | 0 |
| Read | 1 | 0 | 0 | 0 | 1 |
| Hold | 0 | 0 | 0 | 1 | 1 |

**Stability improvement need not mean speed improvement.** At 0.4 V in the 65 nm simulations, SEDF10T provides approximately 2.8 times conventional 6T read SNM and occupies 1.34 times its area. Its write-zero/write-one delays are 20.98/20.08 ns, compared with 7.5/7.5 ns for conventional 6T in that comparison. Supply interruption improves successful low-voltage writing but does not make this particular cell the fastest writer. [11]

**10T takeaway:** Specify whether the extra devices isolate reading, reshape the latch, or interrupt feedback; those choices explain the result more reliably than the count “10T.”

### 11T cells: stronger write access, feedback cutting, and leakage control

**11T offers several robustness combinations.** Representative designs include boosted-negative-bitline, BNBL, cells; feedback-cutting FC11T cells; Schmitt-trigger ST11T cells; and data-aware read–write-assist cells. Their common motivation is to recover low-voltage operating margin while managing the leakage or half-select penalties left by simpler architectures. [8][21]

**BNBL strengthens access from both sides.** Bhatnagar et al.’s 45 nm simulated cell uses transmission-gate write access, a negative voltage on one write bitline, and a boosted voltage on the other. It also interrupts the supply to one inverter, weakening the latch feedback opposing the write. The design consequently combines stronger external forcing with less internal contention. [8]

**Replica timing controls assist application.** The BNBL implementation includes replica-bitline sensing to determine when the boosted bias should be applied. Its relevant controls therefore include write selection, complementary write-bitline biasing, inverter-supply interruption, and replica-derived assist timing. These functional controls should be distinguished from the literal WL/WWLA/WWLB labels used by FC11T. [8]

**Margin improvement has a timing price.** The BNBL paper reports approximately 5.37 times conventional 6T write margin, yet a write time 52% slower than 6T. It is faster than its LP10T and WRE8T comparators. This is an instructive distinction: eliminating write failure under adverse conditions and minimizing nominal write latency are related but different objectives. [8]

| 11T variant | Core mechanism | Named controls | Read organization |
|---|---|---|---|
| BNBL | Dual bitline bias and supply interruption | Write selection, bias enables, replica timing | Variant-specific |
| FC11T | Opens latch feedback during writing | WL, WWLA, WWLB | Single-ended |
| ST11T | Schmitt-trigger core and controlled virtual ground | WL, RWL, VGND | Isolated single-ended |
| E²VR11T | Data-aware tail devices and stacked read path | WL, RWL, PC | Single-ended |

**Feedback cutting reduces write opposition.** FC11T uses WL together with WWLA and WWLB to control the access and feedback-cutting sequence. During writing, opening the regenerative loop reduces the strength that the write input must overcome. The corresponding cost is that successful operation depends on the feedback-opening and restoration sequence, and the path may behave more like cascaded inverters than a simultaneously switching conventional latch. [21]

**ST11T combines isolation and hysteresis.** The Schmitt-trigger core improves resistance to a storage-node excursion, while the separate read path avoids direct bitline disturbance. RWL selects reading; VGND controls the read-return or virtual-ground condition; WL controls writing. The additional virtual-ground line and driver are part of the implementation overhead, even though they do not increase the nominal bit-cell transistor count. [21]

**Experimental 11T results show the distinction.** A 40 nm half-select-disturb-free 11T implementation reports read SNM 19.8 times the minimum-area 6T value at 0.5 V, but 0.96 times the minimum-area 8T value. Its leakage is 53.3% lower than 6T and 44.5% lower than 8T. Thus, the substantial gain over 6T does not mean that the 11T cell also surpasses read-decoupled 8T in every margin. [22]

**DARWA moves assistance inside the cell.** The 2023 E²VR11T design uses data-aware read–write assist, DARWA. Its read path contains three series NMOS devices, N7–N9: RWL controls N7/N8, while QB controls N9. The write path adds two tail devices, N3/N4, whose gates are driven by the complementary storage nodes. [23]

**Internal data controls feedback weakening.** When a tail device turns off during writing, it interrupts the opposing pull-down path and helps the latch transition without waiting for complete bitline discharge. During hold, stacking suppresses leakage. The read port is disabled during writing by holding RWL low; WL enables the differential write-access pair, and PC controls read-bitline precharge. [23]

**The evaluation is explicitly simulation-based.** E²VR11T was evaluated in a 45 nm generic CMOS process, with nominal results at 1 V and 27 °C and 5,000-sample Monte Carlo analysis. It reports 52.216 nW nominal leakage and a footprint 1.34 times conventional 6T. Its nominal-voltage results establish mechanisms and relative behavior in that setup, rather than a silicon-demonstrated subthreshold operating point. [23]

**11T takeaway:** Choose the variant according to whether write contention, half-selection, read robustness, or standby leakage is dominant; “11T” alone does not specify the solution.

### 12T cells: differential access, data-dependent supply cutoff, and compiler integration

**12T supports robust but different architectures.** Important examples include fully differential cells with column selection, data-dependent supply-cutoff cells with an 8T-like read port, feedback-cutting cells, and Schmitt-trigger variants. A fabricated 7 nm compiler also demonstrates that 12T is not confined to isolated academic bit-cell simulations. [9][24][3]

**Differential 12T improves read distinguishability.** Ataei, Stine, and Guthaus’s design uses decoupled differential read paths and a latch-type sense amplifier. Rather than resolving one read line against an absolute threshold or reference, the amplifier resolves the difference between BL and BR. Row WL and column SEL jointly control access, supporting half-select-free bit interleaving. [9]

**Series access motivates selective boosting.** During writing, WL and SEL are boosted by 50 mV at a 300 mV supply. The stronger gate drive improves current through the series access devices. The design avoids applying this boost indiscriminately during reading, where stronger access can reduce stability. The required dynamic header and boosted-control distribution are therefore genuine peripheral costs. [9]

**The macro reaches a low operating voltage.** The OpenRAM-designed 64 kb macro in IBM 32 nm SOI is reported to read and write without error at 300 mV and hold data at 250 mV. Reported operating frequencies are 50 MHz at 0.3 V and 2.2 GHz at 0.9 V. These are macro-design operating points, distinct from the fabricated 7 nm compiler discussed below. [25]

**Supply-cutoff 12T attacks write feedback.** Kim and Mazumder’s cell contains four inverter devices, two write-access devices, four PMOS supply switches, and two read devices. WBL/WBLB and WWL select which inverter supply is interrupted during a write. The opposing high node can then discharge without sustained pull-up contention, after which cross-coupled action completes the transition. [24]

**Its read port remains 8T-like.** RWL enables the path from RBL to VGND through the two read transistors. VGND is driven to ground during reading and returned toward VDD afterward to reduce unused-port leakage. This architecture therefore combines familiar read isolation with a more elaborate data-dependent write-supply network. [24]

**Write robustness improves beyond read isolation.** In the 40 nm study at 0.55 V, the reported 12T read SNM is approximately 198.28 mV, close to 8T’s 199.32 mV and well above 6T’s 80.08 mV under the stated FS-corner, 125 °C read evaluation. The more distinctive improvement is writing: the data-dependent supply cutoff removes contention that remains in the conventional 8T write core. [24]

**Feedback-cutting alternatives reduce control generation.** Sharma et al.’s 12T design uses bitline-controlled lower NMOS devices for data-dependent feedback cutting, together with isolated reading and cross-point selection. Because the write data itself controls the feedback-cutting devices, the design avoids a separate dedicated feedback-control generator used by some earlier approaches. Stacked write paths also reduce leakage. [26]

**Its operating signals differ explicitly.** Sharma’s control vector is WL/WWL/RWL/RGND, with the following states. These levels apply to that circuit, not to the differential WL/SEL design or Kim and Mazumder’s supply-cutoff cell. [26]

| Operation | WL | WWL | RWL | RGND |
|---|---:|---:|---:|---:|
| Write | 1 | 1 | 0 | 1 |
| Read | 0 | 1 | 1 | 0 |
| Hold | 0 | 0 | 0 | 1 |

**Reported benefits span multiple margins.** At 0.4 V, Sharma et al. report 2.14 times the 6T write trip point, 8.99 times write SNM, 2.6 times read SNM, and 1.06 times dynamic read noise margin. Standby power is 0.93 times and area is 1.49 times the conventional 6T values. The much smaller dynamic-margin gain than static write-margin gain illustrates why one robustness metric should not stand in for all others. [26]

**Not every 12T cell isolates reading.** The 7 nm PTM-MG comparison includes an ST12T whose read path still suffers disturbance, despite its Schmitt-trigger core and half-select protection. At 0.2 V, its read SNM is 44.1 mV, compared with 67.1 mV for conventional read-decoupled 8T. Extra devices may improve writing or selection without delivering the particular read-isolation benefit of another topology. [21]

**Compiler integration adds architectural obligations.** Sinangil et al.’s fabricated 7 nm FinFET one-port compiler uses a write-contention- and read-upset-free 12T cell and reports 290 mV minimum operation. It supports column multiplexing and bit-write masking through read-modify-write, together with built-in self-test, synchronous write-through, and power-management functions. The bit cell improves the electrical access problem, while the surrounding architecture provides practical memory semantics. [3]

**12T takeaway:** The strongest justification for 12T is a specific combination of low-voltage read, write, and selection robustness that outweighs its cell and peripheral costs—not the transistor count by itself.

**Additional documented evidence**

**6T reference and low-voltage failure modes**

The conventional 6T cell contains two cross-coupled CMOS inverters and two access transistors, giving **6 transistors per bit cell**. A single wordline (WL) controls access to complementary bitlines BL and BL̅: WL is low during hold and asserted for read or write. Conventional readout is differential, using the voltage difference between BL and BL̅; in a single-port cell, read and write are performed in separate operations.[41][121] A reduced supply voltage narrows the stability and sensing margins, while the cell must still balance read safety, write ability, retention, leakage, delay, and power. Large bitline capacitance also slows discharge and motivates sense amplification.[42][44][121]

The 6T cell therefore provides the comparison reference, but “7T,” “8T,” and higher labels identify transistor-count classes rather than unique canonical circuits. The added transistor may instead implement read isolation, feedback interruption, source-line control, supply gating, leakage reduction, or write assistance.

**7T cells: feedback control, low-swing writing, and leakage gating**

A 7T representative uses **7 transistors per bit cell**, but the evidence shows several materially different variants.

* **Feedback-controlled 7T CNTFET cell.** One reported 7T cell adds transistor 7 in the feedback path between the cross-coupled inverters. Separate **WRITE SELECT** and **READ SELECT** controls select the write and read access transistors. Transistor 7 is on during read and off during write; turning it off disconnects the feedback path, allowing the write-bitline value to overcome the cell more easily. During read, sizing the read devices accelerates read-bitline charging. The topology therefore improves read speed and reduces switching activity and dynamic power, at the cost of an extra device and additional control complexity.[117]

* **Sense-amplifying small-swing 7T cell.** A different 7T design adds an nMOS switch, called **Vss** in the source, between the driver nMOS sources and the source line. The switch suppresses driver current while WL is active, allowing a cell node to invert from a small bitline differential rather than a full-swing write. The bitline is precharged to \(V_{DD}-V_{TN}\), not \(V_{DD}\), and a write “0” pulls it toward \(V_{DD}-V_{TN}-\mathrm{DBL}\). The source-line control signal **SLC** is synchronized with WL: the Vss switch is turned off before WL rises during write, and SLC returns high after WL falls, when the cell restores the small-swing value to full swing internally.[42]

  In the cited 0.35-µm, 2-V, 100-MHz simulation, the small-swing scheme saved **75% of write-cycle power**. The source estimated **15% delay overhead** and **11% area overhead**, although the cited passage does not state a fully defined common denominator for those percentages. The Vss switch cannot be placed independently in every cell when that would push area overhead beyond **20%**; it is consequently shared among neighboring cells. Sharing introduces routing and half-select concerns: in one example, 64 cells were connected to a WL and 256 to an SLC line, leaving 192 cells temporarily unstable while 64 were written. A dc–dc converter and voltage-reference generator produced the reduced precharge level.[42]

  The same design trades read current, noise margin, delay, and area through the Vss sizing parameters. A smaller switch saves layout area but reduces read current and read margin; a larger switch improves read performance but increases area. Compared with driving-source-line and switched-virtual-ground techniques, the SLC implementation avoids negative source voltage and half-precharging. The cited comparison warns that negative source voltage can overstress the gate oxide, while a virtual-ground line parallel to a bitline has greater delay, power, and area overhead than an SLC line routed with the wordline.[42]

* **Read/write-separated virtual-ground 7T cell.** A 90-nm HSPICE design evaluated at **500 mV** separates the read and write access devices, isolates the storage node from the read path, uses a single-ended write, and applies a virtual ground to one inverter. The virtual ground weakens positive feedback during write, improving write ability; storage-node isolation improves read stability, and the stacked ground path reduces leakage. Relative to the cited conventional 6T cell, the source reports **80% higher read stability**, **54.9% higher write ability**, and **12.35% static-power improvement** at 500 mV. The virtual ground is shared across a row to reduce the added area and power burden. The supplied evidence names the virtual-ground node but does not specify a separate signal name, polarity, or timing waveform.[44]

* **Single-bitline and dual-threshold variants.** Another reported 7T design uses one bitline during writing and reports at least **49% write-power saving**, higher stability, and no performance degradation, with **12.25% additional silicon area** in HSPICE simulation.[43] A related 7T design is identified as a single-bitline cell for near-threshold operation in **14-nm FinFET technology**, published in 2016, with “enhanced performance and energy” as its stated objective; the supplied evidence does not disclose its detailed topology, control phases, or numeric metrics.[119] A separate record describes a **128-kb, 0.3-V, 90-MHz, 28-nm FD-SOI 7T sense-amplifierless SRAM** with **8.4 fJ/bit** energy and a single-bitline path.[39]

* **Ground-gated leakage-control 7T cell.** A further 7T design adds bottom transistor **NM5** between the pull-down devices and ground. WL drives NM5: WL low turns NM5 off in standby and interrupts the leakage path, while WL high turns it on for active read and write, making the active path function like a 6T cell. The source reports an insignificant write-access-time effect but a larger array, especially for large arrays; the resulting cell dimensions remain comparable to 6T after including the NM5 dimensions.[121]

These variants show why “7T improvement” cannot be reduced to one metric. The added device can improve read isolation, write ability, leakage, or write energy, but it can also add a control line, shared-rail routing, area, half-select exposure, or a read-current penalty.

**8T cells: decoupled read paths and variability tolerance**

An 8T cell uses **8 transistors per bit cell**. In the cited CNTFET topology, additional transistors isolate the internal inverter from accidental writing through the read path. **RBL** is precharged to the supply before read, and **RWL** is asserted to begin the read; the sensed RBL state depends on the stored internal node. The write cycle remains similar to the 6T write cycle. Thus, the principal 6T improvement is read-path isolation and reduced read disturb, while the overhead is an additional read path, RBL precharge, RWL routing, and associated control timing.[117]

Other 8T evidence describes breaking the inverter feedback loop and eliminating direct bitline effects to increase static noise margin and read stability. An 8T cell is also reported as capable of substantially improving variability tolerance and low-voltage operation without significant area penalty over 6T and without secondary or dynamically generated power supplies.[43][39] A source titled *Low voltage high speed 8T SRAM cell for ultra-low power applications* confirms the intended low-voltage and power objectives, but the supplied span does not establish its circuit topology, control signals, overhead, or performance values.[120]

**9T cells: write assistance and standby-leakage reduction**

A 9T representative contains **9 transistors per bit cell**, but the class includes distinct read- and write-oriented designs. One single-stacked 9T-ST design uses a **boosted bitline swing** together with **collapsed cell supply** during write. Its stated objective is to improve write speed and write-process efficiency; the supplied evidence does not specify the assist polarity, timing phase, or complete control-signal names.[39]

A different low-power 9T architecture targets both active and passive modes by adding a **sleep transistor in the ground path**. The resulting stack effect reduces static power during standby. The cited evidence identifies the sleep device but does not provide its control-signal name, asserted level, or exact wake-up timing.[43] The literature anchors listed for the 9T class also include a 256-kb near-threshold SRAM and a separately characterized nine-transistor SRAM, so the count alone does not identify one universal read path or sensing method.[40]

**10T cells: explicit read/write separation**

A 10T cell uses **10 transistors per bit cell**. In the cited topology, **WL** and **WWL** separate read and write behavior. During read, WL is enabled and WWL is disabled, decoupling the internal storage nodes from the bitlines and improving read static noise margin. During write, both WL and WWL are enabled so that bitline data can enter the cell. The added series access devices improve read and write noise margins but can make write ability more difficult, particularly at low supply voltage.[117]

A separate 0.13-µm HSPICE study describes 10T and 11T cells with separate read and write processes intended to obtain high static noise margin. The 10T cell was operated at **0.32 V**, used one read bitline, and was evaluated in a 128-column array with up to 512 cells per bitline; the same study labels an 11T structure operated at **0.27 V**. These values establish low-voltage operating context, not a universal 10T or 11T implementation.[44]

A 2025 study proposes a 10T SRAM using vertical nanowire tunnel FETs and compares it with 6T–9T cells. The reported 10T objective is lower leakage power and leakage current with acceptable read delay, write delay, and circuit complexity; the source reports **25–79% lower leakage power**, **6–60% higher read SNM**, and **5–47% higher write SNM** relative to the comparison cells. These are source-specific results for vertical nanowire tunnel FETs and should not be transferred to conventional CMOS 10T cells.[118]

**Source-specific performance evidence and limits**

An allowed 180-nm CMOS comparative study, published in 2016, used Cadence pre-layout and post-layout simulation. It reports the following paired **read/write delays**, power consumption, and static noise margins (SNM): 6T, **0.671/0.267 ns**, **1.69 µW**, and **0.4 V**; 7T, **0.456/0.752 ns**, **1.09 µW**, and **0.375 V**; 8T, **0.517/0.392 ns**, **1.82 µW**, and **0.65 V**; 9T, **0.388/0.181 ns**, **1.3 µW**, and **0.65 V**; and 10T, **0.167/0.242 ns**, **2.01 µW**, and **0.6 V**.[40] The study frames data stability and power consumption as central scaling issues, but its 180-nm supply, sizing, load, and timing definitions are not a common basis for the other reported studies.

A separate CNTFET simulation reports dynamic power of **10.054 nW** for 6T, **4.87 nW** for 7T, **12.458 nW** for 8T, **16.548 nW** for 9T, and **17.58 nW** for 10T. Its table gives read delays of **5.9, 3.6, 6.5, 7.6, and 8.0 ns**, respectively, with 8T, 9T, and 10T showing more than 50% higher RSNM than 6T; the same source gives 7T no significant RSNM improvement, approximately 10% WSNM improvement for 7T and 8T, and more than 30% WSNM improvement for 10T. The table lists RSNM/WM pairs of **202/340 µV** for 6T, **223/360 µV** for 7T, **397/379 µV** for 8T, **410/330 µV** for 9T, and **432/475 µV** for 10T.[117]

The source’s narrative separately states a **3.54-ps** 7T read delay and calls it 36% below 6T, whereas its table lists **3.6 ns** for 7T and **5.9 ns** for 6T; these conflicting source-reported timing values should remain qualified rather than silently reconciled. The numerical results above are therefore illustrative topology evidence, not normalized rankings across 6T–10T designs.

**6T reference and count-class boundary**

The conventional 6T cell contains **six transistors per bit cell**: two cross-coupled CMOS inverters and two NMOS access transistors controlled by WL, with BL and BLB carrying differential data [51][54]. Direct read access to the storage nodes can disturb the stored zero, whereas writing requires the latch to flip; reduced supply voltage and process variation therefore shrink read, write, and retention margins [49][51][58][59]. The labels 7T–12T denote transistor-count classes rather than unique circuits: published variants trade added isolation, sensing, supply control, or robustness against area, routing, leakage, and timing overhead [48][124].

**7T class: added read control and low-power read paths**

A 7T SRAM cell contains **seven transistors per cell**; published examples include a 65-nm bulk-CMOS subthreshold cell operating at **200 mV** and a 32-nm subthreshold cell operating down to **0.4 V** [58][52]. The main design direction is to separate or condition the read path so that the 6T latch is less exposed during read. One single-ended implementation uses BL for writing and a separate RBL for reading: WWL is enabled and RWL is disabled during write, while WWL = 0 disconnects the write path during read and RWL is asserted [51]. A related implementation calls the added read control RL or RW; RL is off during writing and on during reading [54]. During a read of zero, a transistor uses charge sharing to return charge to BL rather than discharging it entirely to ground, reducing read energy [51].

The 7T class is not uniform. A different single-bit-line 7T cell uses one BL for both read and write and reports reduced power, high read stability, and high static-noise margins [123]. A 14-nm FinFET near-threshold 7T variant resolves half-select disturbance without a write-back cycle and reports **13% better read access time, 42% better energy, 23% better standby power, and 3% smaller cell area** than its comparison basis [122]. These improvements address read disturb, half-select behavior, and low-voltage write/read energy, but the added read control and signal routing are topology-specific; 7T designs generally incur an area penalty, while triple-threshold 7T variants are evaluated against stability, write margin, leakage, access speed, and active power under process variation [59][124].

**8T class: a 2T read buffer around the 6T latch**

The standard 8T cell contains **eight transistors per cell**, conventionally a 6T storage core plus a 2T read buffer. The buffer isolates the read path from the storage nodes and write path, improving read stability while allowing the write path to remain close to the conventional 6T path [124]. In a 65-nm bulk-CMOS subthreshold comparison, the 8T cell operates at **200 mV** and exhibits the highest reported RSNM, HSNM, and WNM among the compared 6T, 7T, and 8T cells [58].

**9T class: read decoupling and write-assist variants**

The principal 6T improvements are stronger low-voltage read and write margins and reduced read-path loading. One reported 9T cell improves read SNM by **80%** and write SNM by **50%** relative to conventional 6T and reduces bit-line leakage, aiding current sensing [123]. A supply-feedback 9T cell internally weakens pull-up current during writing, enabling low-voltage writes without additional peripheral assist circuitry [123]. Accordingly, its material controls can include a data-aware write word line, a negative-bit-line control, adaptive read timing, or internal supply-feedback control; polarity and phase are variant-specific rather than universal. The additional devices and control logic increase area and implementation complexity, while Schmitt-trigger and differential-read variants change the sensing path and delay trade-off [48][124].

**10T class: leakage suppression, writeability, and read isolation**

A 10T cell contains **ten transistors per cell**. Published representatives include a 90-nm, 32-kb subthreshold array using bit interleaving and differential read, and a 45-nm LP10T comparison cell with differential read and write paths [125][48]. A subthreshold 10T result reports **2.95× larger RSNM and 1.93× higher write margin** than conventional 6T [52].

The LP10T control labels include WBL/RBL and WWL, RWL, and WWLA, with differential write/read operation [48]. These controls, together with WL/W_WL in cascaded-access variants, are introduced to coordinate write strength, read isolation, bit interleaving, and sensing. The trade-off is additional transistors, word-line phases, routing, and possible write limitation from series access devices.

**11T class: integrated data-aware read/write assist**

Under one 45-nm CMOS comparison at **1 V, 27 °C, and 1-µs transient time**, E²VR11T reports **52.216 nW leakage, 188.035 ps read delay, 336.972 ps write delay, and 1.34× normalized area**; MET11T reports **57.834 nW leakage, no read-delay value in the table, 722.505 ps write delay, and 1.68× area** [48]. The same source reports, under those conditions, S8T at 70.298 nW/93.655 ps/402.153 ps/1.24×, ST9T at 119.543 nW/295.513 ps/152.056 ps/1.32×, and LP10T at 88.357 nW/273.906 ps/560.399 ps/1.51× for leakage/read delay/write delay/normalized area, respectively [48]. These are source-specific simulations, not universal values for their transistor-count classes.

**12T class: simultaneous-operation and low-power variants**

**7T**

The dual-VT 7T cell has 7 transistors/cell in 180-nm CMOS (2013): an N1/P1/N2/P2 latch stores data; WBL/N3 writes; precharged RBL/N4–N5 reads; and RWL/WWL separately control read/write (R high, W at ground). Read isolation improves stability and removes latch sizing from the read-delay path [60]. Another 7T account separates the paths, drives WL high with N5 on, and keeps the zero node near ground [60]. A 45-nm comparison reports 7T data-retention voltage at 1.71× that of the proposed 10T over 20–100°C [62]. L-shaped 7T is identified as sub-0.3-V and area-efficient, with boosted-RBL, asymmetric-VTH read-port and offset-cell-VDD techniques, but its phases and metrics are unavailable; an MTCMOS 7T is only a cited lead [319, 104]. A non-intrinsic local-rail write assist uses write-enable and power-down signals to set ΔV1/ΔV2 below VDD; write-enable can switch transistors 28/30 to pull the rail toward VSS and increase write margin, with polarity implementation-dependent [127].

**8T**

An 8T dedicated read port isolates storage from bitlines, eliminating read disturb at the cost of area [60]. The asymmetric Schmitt-trigger 8T uses single-ended read, asymmetric inverters and a higher trip point; it retains 6T-like writing without write assist. WL controls read/write, WWL write only, and simulated RSNM is 86% higher than 6T and 19% higher than 10T-ST without VT variation [60]. A separate 8T sets RWL low to disconnect feedback during write, precharges WBL high and discharges it only for data 1; RWL and RD enable read, producing a 100–200-mV RBL drop [60]. Another named 64-kb 8T operates at 0.26 V [128]. A 16-nm comparison reports LP8T read latency 8% lower and standby power nearly an order of magnitude lower, but poorer hold stability from disabled tail transistors; WRE8T reduces active power by 55% [126].

**9T**

Published 9T variants include single-ended disturb-free, power-gated, SB9T, half-select-free/bit-line-sharing and one-sided Schmitt-trigger cells [126]. The decoupled representative is 9 transistors/cell: a 6T latch plus a 3T single-ended RBL port; WWL/WBL/WBLB write, RWL read, with HVT storage/write devices and an LVT read port [128]. Leakage equalization makes RBL(0) lower than RBL(1), giving positive sensing margin; RBL swing improves 4.6× at 0.2 V and the sensing window is 1.5 µs at 50 kHz [128]. A 65-nm, 16-kb test chip operates from 1.2 to 0.26 V, with read access from 6 ns to 0.85 µs; values are 79 ns at 0.4 V and 0.85 µs at 0.26 V [128]. It reports 52 mV SNM at 0.2 V—85.7% above 6T-HVT—and 145 ± 17 mV at 0.4 V; layout is 2.63 × 0.72 µm², with 1.4 µA leakage at 0.1 V and 126 aJ/b [128]. HVT improves leakage but slows writing. A CAM booster adds a 48-bit CAM, ring counter, encoder and mini-SRAM to the 16-kb array, creating about 3% array-area overhead; CAM energy is 59 fJ/search at 0.4 V and 1 MHz, while measured macro power is 146 µW at 0.6 V to 4.12 µW at 0.32 V. Write power and write time are not supplied [128].

**10T**

The proposed 10T is 10 transistors/cell; PPN10T and Proposed 10T are distinct 10T entries [62]. It uses differential read, single-ended write, read buffers and low read-bitline capacitance. Relative to 6T, it reports 8.69% higher read margin, 16.85% higher write margin, 1.78×/2.326× read/write-delay improvement, and at 0.9 V 34.65% lower standby power and 2.03× lower read power [62]. At 45 nm and 0.8 V, normalized area is 2.17× 6T, read power 1.76 µW, write power 185.43 nW, and read/write access times 49.33/46.31 ps [62]. WR=1 with CSR=RD=0 selects writing; WR off and CSR on protect half-selected cells. WPDP is lowest at 0.5–0.65 V, but Q-node activity raises write power above 0.7 V [62]. A differential ST2 10T reports 3% improved writability at 16 nm [126].

**11T**

ST11T is 11 transistors/cell in 16-nm CMOS: feedback-stabilized inverters and an isolated read path improve retention and read margins by a factor of 1.18 under PVT variation [126]. D2p11T is another 45-nm comparison label; the supplied evidence gives no signal phases or polarity for either representative [93, 317].

**12T**

The 12T class is 12 transistors/cell; named variants include stable bit-interleaved, half-select-free bit-line-sharing and boosted-word-line fast-write cells [126]. A 40-nm bit-interleaved subthreshold 12T uses data-aware write assist [62]. These mechanisms target retention, half-select disturbance, leakage, writability and bit-interleaving; exact signal names, polarity and phase are not supplied in the cited spans [93, 317].

7T: feedback is cut for writes; WL_L/WL_R and TRANS7 control access/feedback; 2016/180 nm: 0.456/0.752 ns delay, 1.09 μW power, 0.375 V SNM [130,126].

**7T/M7T.** Near-threshold 6T: low SNM/read margin, writability, half-select/PVT robustness; 7T bitline decoupling gives read SNM = hold SNM, but a higher write rail requires routing [130]. 0.4-V/2.01-pJ 7T: single-ended 1T read, WTVG, PVT-tracked differential sensing, ultra-fine-grain gating; RD_VGND=GND/read (precharged RBL; VDD otherwise), WR_VGND=GND/write (WBL/WBLB). VDD/VSS gating: leakage −96.3% initially/−52% post-power-up; area +2.4%/+2% [71]. Supplementary 65-nm 7T Asym7T/M7T: asymmetric-ground-gated sleep; stability +7.03× read/+2.32× idle versus 6T, write margin +9.02% versus 8T; assist signals unnamed [129]. Variants: tri-VT lowest write/highest read power; self-level leakage to 92%; 7T2 stability/power gains [72][73][74].

**8T–10T.** 8T: RWL/WWL, WBL/WBLB, precharged RBL; isolated read, 6T-like write; Ultra8T uses single-ended offset-canceling voltage-latch sensing [75]. 8T: 11.40 mm², 77.72/45.47 ps read/write, dynamic/leakage −38.33%/−25.31% versus reported 8T data; 9T: leakage equalization, 15.46 mm², 98.85/10 ps, HVT-slowed read, capacitance-raised write power, dual-VT leakage control [72][74]. 10T: decoupled read margin; measured 130-nm/0.2-V/480-kb design adds RSCE write-margin enhancement, leakage-suppressed bitlines, VGND-replica sensing and writeback; PPN-10T reports high read stability/FOM [130][72].

6T: access/pull-down voltage division causes read disturb; read/write sizing conflict worsens with variation [81][80].  
7T: SE-BL adds an access device, single BL and feedback TG; shared WL, write-control cuts feedback, precharge pulse. At 65 nm: 34% lower data-line power and 11% area penalty; SE-7T has separate read port [91][81].  
8T: RDWL/RDBL isolation or feedback-cut single BL; at 0.5 V/65 nm: 4.66× write ability, 2.33× read margin, 28% lower write power, 3.3× lower standby; CS/read-buffer FinFET: 70 mV, 0.331 pW leakage [81][90].  
9T: SB9T is single-ended/half-select-free; at 16 nm: 37% area overhead, 4.2× RSNM, 33% lower leakage, longer write. Data-aware write-WL, negative BL and adaptive timing give 71.2× ION/IOFF at 0.3 V/32 nm versus 8T [86][87][133].  
10T: read decoupling, floating node and un-precharged single-ended read improve stability, writability and power at 0.3 V/10 nm; 90-nm differential/P-P-N variants exist; 10T1C and ternary leads are not selected binary representatives [86][132][89].  
11T: four NMOS access+biased PMOS header, or separate read/stacked access/feedback cut; 1.61× FD8T area at 0.7 V/16 nm; 19.8× RSNM and 11.84× WM versus 6T at 0.5 V/40 nm [90][131][77].  
12T: 40-nm data-aware-write-assist and low-swing multi-VT representatives are cited; detailed control phases remain unavailable [132][133].

**7T (variants).** +1T read decoupling improves RSNM/stability but slows series/differential read; M7 feedback uses WRITE/READ SELECT (on read/off write) [97][101][134]. Other forms remove access T [92] or add Meq for WE data-clear [96]. Body-bias WBL/WWL/RWL (no new signal) restores sub-1-V write; overhead is 10% at Nmax=8 cells/contact [135]. Dynamic power (operation unspecified): 4.87 versus 10.054 nW; read-delay conflict: 3.6 ns in the table versus 3.54 ps in text [97].

**8T.** +2T decouples read/write; RWL→precharged RBL with single-ended sensing; RSNM >50% and WSNM ≈10% versus 6T, but read slows [93][97][101][134].

**10T/12T.** Representative 10T (+4T versus 6T) uses WL/WWL to isolate Q/QB (both write): WSNM >30%, but writability and parasitic power-delay trade off [97][100]. At 45 nm, leakage power/current fell 36%/64% and read stability rose 13% [96]; 12T examples include compact coupling [103] and SVL for lower standby/average power [104].

6T: read disturb and low-VDD write/hold/access failures [109][112]. At 180 nm/27°C simulation, dynamic power was 5.45 µW (7T) and 10.26 µW (8T) (8T highest; static similar) [136]. 7T: MN5 with W/WL/R phase control and one-bitline write improves SNM/RSNM/WSNM, but adds 11.1% area vs 6T (32 nm) and raises hold power [113]. 8T: two-NMOS read stack; WWL write, RWL/precharged RBL read, isolating storage; 30% area and RSNM=HSNM=0.41 V [110][137]. 9T: RWL/RBL read and super-cutoff sleep reduce leakage [105][137]. 10T: R/W buffers/data-independent leakage; 11T: CB (NMOS3 source→RDWL); 12T: VDD/GND devices improve stability [106].

8T: a decoupled read buffer prevents read disturb; RBL is precharged before RWL, and WWL drives WBL/WBLB; sensing is single-ended [50].


An 8T cell contains 8 transistors per bit cell. The single-ended ULV version breaks feedback between storage nodes to improve writeability and isolates the cell from the bit-lines during read; at 200 mV it reports 1.3× higher mean write static-noise margin than CU-6T, while CU-6T read time is 1.2× the 8T value, and at 500 mV CU-6T read power is 8× higher (UMC 90 nm simulation, May 2014) [139]. The read-SNM-free form adds a two-transistor M7/M8 read port: RWL controls reading and WWL controls writing, producing a nondestructive read but adding area and leakage [56]. One implementation uses WWL/WBL/WBLB for write and RWL/RBL for read, with a modified current-sense amplifier; it reports 753.25 ps read access and 1.002 ns write access at 1.95 V and 0.5 MHz [140]. A 40 nm variant adds floating VSSRD, low-swing precharge, and a WL_RD-activated local buffer; at 0.55 V it reports 5.35 ns versus 22.9 ns read delay and 40× lower worst-corner leakage current [55]. A 65 nm PD-SOI 32 kb cache demonstrated operation at 295 MHz and 0.41 V without secondary or dynamic supplies [141]. Thus 8T improves read isolation and variation tolerance, but adds devices, routing, buffering, and write-energy burden [55][56].

**9T and 10T**

The canonical 9T cell adds three transistors to bypass read current from the storage nodes, yielding nondestructive or SNM-free read stability; its reported cost is 38% extra area, complex layout, and poly jogs [56]. A separate subthreshold 9T uses dynamic feedback cutting and reports 80% read-SNM and 50% write-SNM improvement versus 6T [63]. The supplied 9T evidence does not identify additional signal names or polarities; only baseline WL and BL/BLB phases are documented [57][63].

The 10T cell uses a four-transistor read port while retaining a 6T-like storage and write path. Two additional read-port devices cut the RBL leakage path when RWL is low, making read behavior independent of storage-node data [56]. A P-P-N 10T is separately identified for low-leakage, resilient subthreshold operation, but its complete signal inventory is not reported [64].

**MPT8T**

MPT8T is a named 8T modified-PMOS pass-transistor-logic cell, evaluated at 45 nm in the subthreshold regime and at 0.4 V. It replaces the 6T access devices with MP3–MN3 and MP4–MN4 pairs; the added NMOS devices remain cut off during read/write while limiting voltage degradation and balancing leakage [63]. It reports 3.5× higher read SNM, 2.4× higher write SNM, and 7.735× lower standby power than 6T at 0.4 V; average write/read access times are reported as 2.61×/1.07× lower over 0.3–0.5 V [63]. WL is pulsed low for the PMOS access devices, BL/BLB carry data, and no additional data-control line is required. MPT8T remains a named 8T candidate; whether it is the selected representative is unresolved [63].

8T: A 2T read buffer decouples storage/read (RSNM = hold SNM) and permits write sizing, but half-select instability remains [94][142]. WL/BL/BLB write; RDWL/RDBL perform single-ended read (RDBL precharged); BVSS is the read-buffer virtual ground, while row MCHd is lowered in write and raised in read [142]. Dual-port 8T uses RWL and write-time VDD collapse; hold margin limits Vmin [85]. Write-assist area is <6% and second-sense-amplifier/selection area <10% [142]. In 180-nm FDSOI at 20 kHz and 80% yield, 8T had the lowest read Vmin (10% below peers); 6T/8T were iso-area, with silicon/model mismatch [94].

10T: Schmitt-trigger feedback weakens the pull-down during read, giving 1.56× 6T RSNM at a 33% area penalty [94]. A 90-nm, 32-kb subthreshold variant uses bit-interleaved differential read; stacked devices require boosted WL but reduce bitline leakage [142][85].

12T: The 2RW cell decouples ports: RWLA/B read, WWLA/B write, and VGND grounds selected read columns; hierarchical bitlines improve speed/power [83]. At 65 nm it reports ~6% cell-area overhead, 0.4-V common-row Vmin, and 73% simulated standby-RBL-leakage reduction at 0.4 V. Measured results are 6.0 µs read access at 0.3 V including I/O and level shifters, 7.6 µA leakage current at 0.4 V, and 101 µW/MHz combined power at 1.2 V with equal read/write probability; sensing uses PMOS-inverted RBLB, with no conventional category specified [83].

8T read isolation via RWL/RBL prevents 6T disturb [95][99]; 9T adds 3T, raising read/hold/write SNM [98]; 10T Schmitt: RSNM 1.56×, area +33% (2012) [95].

8T: 0.57V/45nm SOI (2010), AC-coupled sensing [143]; 9T: single-ended/stacked, WM+42.2%, area+32% (2016) [144]; 10T: 1.7×6T area, 0.45V/300MHz (2010) [114].

PNN-10T uses CL/CR pulse read-assist, data-aware SWL/SWR, and WWL/RWL; at 40 nm, 0.3 V, and 10 MHz it reports 4.15 µW read and 3.82 µW write power. Its layout is 3.28 µm², but no matched 6T denominator supports a percentage overhead [145]. 12T examples include 40-nm data-aware subthreshold and 7-nm/290-mV write-contention/read-upset-free cells [145].

7T adds a PMOS/power gate; PC equalizes the cell, then WL/VVCC writes, reducing energy–data correlation >1000× [148]. 8T decouples read/write; RWL/WWL boosting and VVSS-footer control support 350–700 mV, with 320 mV retention [147]. 90-nm 9T at 300 mV raises RSNM 219% and read I_on/I_off 113%, reaches VDDmin 350 mV, but adds 83% cell area [146]. 10T adds a 4T decoupled read port with virtual rails [149]; 12T targets variation-tolerant writeability [65].

7T: a WL-gated bottom NMOS cuts standby leakage at WL=0 and restores 6T-like read/write at WL=1; cost: slight delay/array area [156]. Decoupled-read/dual-Vth variants need write assist/add fabrication complexity [152]. 8T: an isolated 2T read port decouples read/write VDDmin; differential write/single-ended RBL improves stability, but RBL leakage, precharge power and bit-interleaving limits remain [151][152]; D2AW8T adds DA-CVSS, DA-WWL and NRWL [153]. 9T: read isolation doubles RSNM and cuts idle leakage 22.9% versus 6T at 65 nm; a 90-nm simulated cell reports DRV 84.5 mV and read/write delays of 98.85/10 ps [66][154]. CP9T trades half-select relief for area and write-limited VDDmin; subthreshold variants use boosted WWL, negative BL and adaptive timing [153][155]. 10T P-10T adds a 4T read port plus CWL/WWL, WBL/WBLB and VDDM1–3; dropped-VDD lowers power; 5.5-kb-array leakage is 41.8 µW at 0.5 V/6.25 MHz [151]. 11T ST11T uses decoupled Schmitt/VGND read; write-1 access is 7.5 ns at 0.4 V/22 nm and write-1/0 power is 3/15 µW at 0.9 V [152]. E2VR11T uses differential write/single-ended RBL sensing [150]. No 12T-specific topology/control evidence appears in this slice.

7T: +NMOS between cross-coupled inverters; Quiet-BL; DT−=standby, DT+=read (90nm,0.7V,8×8 sim); BL/BLB differential SA [157]. 8T: 65nm differential/bit-interleaved high-noise-margin cell; N5 cuts feedback and read/write lines control it [161][158]. 9T/WRE9T: separate R/W paths address 6T read-upset/write-fail; single-ended read; controls read-BL,WBL,boosted WWL,global WBL-low. PP-9T adds RWL-low bypass NMOS and shared WL [160][165][68]. 10T: WWL/RWL=1/0 write,0/1 read,0/0 hold; separate paths, differential BL/BLB+SA; +55% area,+16% read delay,−12% power versus 6T [162]. 11T: M8/M9 stack,M10 sleep,M11 pass reduce leakage; RWL,CBL/CBLB,WL,LWL controls. At 32nm/1V: P=.0835/.2385µW RB/NB, L=14.92/17.90nW@25°C, Dmax/min=6.089/2.617 and 3.035/1.457ps; no R/W split [159]. 12T: read-decoupled,data-dependent VDD-cutoff write assist; half-select-stable bit-interleaving; WL,BL/BLB,RD,WR controls; at 55nm, SNM=16.13×6T and leakage −15.7% [163][164].

- **7T.** Differential near-threshold 7T adds a controlled nMOS and row WLRB beside WL; WLRB=VSS isolates the read-disturbed path, and differential VLSA senses the cell [168].
- **8T.** Separate-read/write, different-VT low-voltage 8T/9T variants simulated at 130 nm and 0.7 V improve static power, RSNM and speed [173].
- **9T.** Discovered M9T is a 45-nm, 0.4-V subthreshold candidate using cross-coupled inverters, TG access pairs and a WL-controlled PMOS; WL is pulsed low, BL/BLB are differential, and no extra data-control line is needed. It targets voltage loss/leakage and reports 1.3× higher read-SNM and 1.77× higher write-SNM than 6T [167]. A single-ended 9T adds row WL/VVSS, column WWLA/WWLB/BL, a read buffer/full-swing SA, NBL write assist and AROTT replica/FSM timing; at 65 nm and 0.4 V it reports 151 versus 57 mV RSNM and 97% area overhead [171]. Its measured macro operated error-free to 0.35 V at 229 kHz and 4.05 µW, holding data at 0.275 V and 2.29 µW [171].
- **10T.** Differential 10T uses a WWL pass gate and VLSA to mitigate half-select disturbance but costs area/read energy; RLP10T uses three series read devices and a single bitline, trading short read for long write delay [168][174].
- **11T.** The 2019 cited 11T cell is half-select-disturb-free with built-in write/read assist; the supplied span gives no further topology or signal details [166].
- **12T.** Differential 12T uses WWL/VLSA for half-select protection but costs area/read energy; a 130-nm, 0.4-V Schmitt-trigger 12T reports 16% lower power and 45% higher SNM than 6T [168][170].

7T: 0.17V/90nm; isolated read, WL/RWL/Read-bit/VGND; +7% area, 7× margin [177]. 9T: equalized single-ended read; WR/RD, negative BL/adaptive WWL [175][176]. 10T PNN: CL/CR/WWL/RWL; pulse read/data-aware write [179]. 11T: WWL/RWL/RBL; −40% power, +7% write delay [177]. 12T: decoupled/VGND; BL/BLN/WL [176][178].

9T: RWL/RBLB read; WWL/BL/BLB write; ZWL=0; isolated read raises RSNM, single-BL write cuts power [102]. 10T: AWL PMOSs improve read/write margins [115].

10T LP10T: stacked tail/read bufs cut leakage, improve RSNM [108]; 11T HF11T: RWL read isolation, VGND write assist [180]; 12T: decoupled read, HS-free [181].

8T: Decoupled-read leakage removal, one read transistor, power gating and p-type stacking; VDDmin 710→430 mV vs 6T, RSNM/WSNM 0.203/0.270 V, read/write power 3.93/5.9 µW, leakage 16.07 nW, area 1.42× (8 Aug 2025) [183]. Control names and sensing type are unreported [183].

12T: Separate R/W access, storage decoupling, read footer/BLLC; read WL on/WWL off, BLL/BLR precharged to VDD; write WL+WWL on [61]. At 55 nm, 0.4 V, 25 °C: RSNM/writability +80%/+64%, area 2.58×, lower leakage, comparable access versus 6T [61]. SFD12T (16 nm/0.5 V) grounds 0 on read and cuts pull-down on write; stability/writability +2.11×/+1.09× and leakage improvement 18.55% versus FD8T [184].

Other 12Ts use data-dependent supply/isolation/stacking to reduce leakage and write power versus 6T [82]; feedback cutting gives WTP/WSNM +2.14/+8.99× and area 1.49× [84]. RHD-12T uses dummy-access PMOS control for SEMNU; a sleep-transistor 12T targets standby leakage [454,455]. MI-12T is supplementary: its ON/OFF pair suppresses leakage; at 45 nm and VDD 0.2–0.4 V, write/read SNM is +2.5×/+1.6× and write delay/hold power are 3.57×/1.476× lower than 6T; controls and absolute rows are unavailable [185].

SE‑7T (subthreshold Monte‑Carlo) versus 6T: read/write‑1/write‑0 delay improves ×2.71/2.71/8.42, read static-noise margin (RSNM) ×3.28, but hold power is 1.22× higher at 350 mV [190]. TG‑DTMOS‑8T (45‑nm GPDK) reduces those delays by 80/63.95/22.7%, raises write static-noise margin (WSNM) 360%, but raises read/write‑1/write‑0 power by 400/458.4/221.4% [190]. M8T means “most-significant 8T” (versus L8T) and is supplementary; decoupled 8T/10T cells prevent read disturb and provide full read-bitline swing, while a 10T variant performs binary line dot-products on source lines [189]. CNTFET 9T uses WWL for writing, RWL and complementary RWL for read isolation, and VGND to weaken pull-down contention; at 0.3 V, RSNM/WSNM improve ×2.115/14.024, layout area is +10.3%, and critical time is 162.37 versus 132.37 ps for 6T [186]. An 11T-specific mechanism remains unresolved; generic evidence says read isolation improves RSNM, whereas an unchanged write path leaves WSNM largely unchanged [186].

ST12T (45-nm simulation) uses a Schmitt-trigger latch; at 0.5–1 V, read-power reduction is 29.17/24.14/7.66/5.87/7.67/16.62% versus 6T/7T/TA8T/9T/PPN10T/D2p11T, with RSNM/WSNM +26.82/+8.87%; it is half-select-free and bit-interleaving capable [111]. SCM-12T (65 nm) uses two gating transistors per column and two-stage readout: read/write energy −91.8/45.6%, read delay −92.7%, and area −22.9% versus prior SCM [187]. A fabricated dual-port 12T is 16 Kb in 65-nm CMOS and reaches 0.4 V in common-row access using hierarchical bitlines and virtual ground; requested absolute metrics and signal phase are not reported [188]. A one-port 12T in 7-nm FinFET is write-contention/read-upset-free, reaches 290 mV minimum operating voltage, and includes read-modify-write, built-in self-test, synchronous write-through, and power-management controls [116]. MI-12T (2019; 45 nm; 0.2–0.4 V) uses an ON/OFF leakage pair; versus S6T, WSNM/RSNM improve ×2.5/1.6, write delay is 3.57× lower, and hold power is 1.476× lower, but representative status, controls, and absolute metrics remain unresolved [462,465]. RS12T/RSWA12T use WL/WWL, BL/BLB precharge, adaptive feedback, and high-write/low-read VGND; latched-current sensing and 1.9×-6T area are reported at 0.5 V, but this is not proven MI‑12T [192].

6T is two cross-coupled inverters plus two access transistors; shared read/write access causes low-VDD read-SNM/writeability conflict, disturb, leakage and variation [37][45][47]. Classes contain 7, 8, 9, 10, 11 and 12 transistors/cell [38][193][194]. 7T adds write-balancing/feedback-cut circuitry and an extra BL, controlled by CS/WL, cutting switching; 8T uses virtual ground and read isolation, with WLB=¬WL and single-ended sensing [195][38][193]. 9T adds three read-port devices for nondestructive read (38% area); 10T adds separate read port and cuts RBL leakage with RWL low [38]. 11T separates read/write at 0.27 V in 0.13-µm HSPICE; 12T adds WL/WWL/RWL/RGND, isolated read and cross-point feedback-cutting paths for write, leakage and half-select robustness at area/delay cost [193][194].

7T dual-Vt (65nm, 2008) isolates storage nodes on read; SNM up 87%, speed up 17%, leakage down 66%, write power down 35% vs 6T [70].

7T adds an NMOS; 8T adds leakage NMOSs; 9T adds a read path; 10T uses WWL/RWL; 11T uses wl/rwl/rbl; 12T uses differential read with WL/SEL [270,536].

6T shared path [197]; 7T feedback isolation,+13% area [198]; 8T read-decoupled [107]; 9T/10T 3T/4T read ports [196]; 11T decoupled [197];12T write-gated [197].

7T WL/RL/MWL feedback cut [201]; 8T read buffer [199]; 9T RD/WR isolation [169]; 10T RBL/virtual rails [203]; 11T M11/RWL/WL/VVDD [200]; 12T WL/SEL+DDFC [202].

10T: stacked-sleep, 65 nm/1.2 V/500 MHz, 7.71 mW overall [204]. 11T P11T: 18.26/5.32 µW R/W [206]. 12T EDP12T: SEU/SEMNU recovery, 50 mV BL sensing [205]

The 7T SRAM topology class is a mainstream low-voltage alternative: its added MN5/feedback or source switch and separate read/write paths isolate storage from read activity and permit small-swing writing; a small-swing implementation reports 75% write-cycle power saving [113][117][42][69]. The trade-off is variant-dependent area—10% in one report and 11% in another—and single-ended variants can have limited write margin or higher read power [135][91][67][74].

The 8T class adds a two-transistor read buffer/port and separate RWL/WWL controls, decoupling the storage nodes from the read bitline and producing a non-destructive, SNM-free read; this targets read disturb, variability and low-voltage operation reported at 0.41 V and 0.57 V [56][75][43][137][143]. One single-ended 8T implementation reports 4.66× write-ability improvement, 2.33× read-margin improvement and 28.0% write-power reduction, while the extra read path remains the main area/leakage cost [81][48].

The 9T class extends the 6T core with a dedicated three-transistor read subcircuit and separate read/write paths; variants use read decoupling, an array-Vss clamp or power-gated read path to protect storage and widen the low-voltage operating window, including a reported 230 mV case [56][85][46][67][68]. Reported controls include BL, WWL, RWL, ZWL, BLB and RBLB: RWL/RBLB are active for read, whereas WWL/BL/BLB are active for write; the benefit is improved read stability and lower standby leakage at the cost of extra transistors and higher leakage energy [102][88][74].

The 10T class adds complementary or single-ended read circuitry to the 6T latch, separating read and write paths so WL and WWL can be tuned independently; LP10T uses differential read/write with WBL/RBL lines, while other variants use dedicated inverter/transmission-gate read ports [46][117][48][76]. This addresses the 6T read/write conflict and near-threshold stability problem; one comparison reports 88.357 nW leakage and more than 30% improvement, with additional read circuitry as the principal overhead [48][97].

The 11T class combines a read-decoupled port with virtual-ground or power-cutoff and dedicated write/assist paths—seen in HF11T, HS11T, E²VR11T and Schmitt-trigger variants—to address low-voltage read/write stability, write ability, leakage and half-select disturb [180][79][48][182]. E²VR11T uses WL for write access, RWL for read, BL/BLB for write data and a single-ended RBL; an 11T comparison reports 52.2160 nW leakage, while another low-voltage result reports 2.17× [48][78].

The 12T class uses separate read/write access structures, stacked devices and sleep or leakage-control elements to decouple the true storage node and target write ability, read stability, half-select immunity and leakage; it is associated with ultra-low-power operation at 0.4 V and moderate performance [53][61][138][172][181][52]. Its phase controls are WL and WWL: read enables WL while disabling WWL and precharges BLL/BLR to VDD, whereas write enables both; the trade-off is 12T complexity and 1.25× area overhead relative to 6T [61][138].

M7T is a supplementary named variant rather than the selected 7T class representative: its asymmetrically ground-gated seven-transistor cell targets low-leakage, data-preserving SLEEP mode and high data stability in nanoscale and low-voltage use [129].

MPT8T is a supplementary 8T variant—a modified PMOS pass-transistor-logic cell—whose WL is pulsed low to turn on the PMOS access devices while BL/BLB carry differential data; it is reported at 0.4 V, directly linking it to the low-voltage survey [63].

M8T is a supplementary named 8T structure used in a weighted-computation array, with a separately labeled read path; that separation makes it relevant to read isolation, but the supplied evidence gives no further voltage, control-phase or performance figure [189].

M9T is a supplementary nine-transistor variant derived from a transmission-gate-based fully differential 8T cell [167]. The supplied evidence does not specify its distinct 6T improvement, low-voltage benefit or quantitative trade-off, so it remains a candidate variant rather than a fully characterized class representative [167].

MI-12T is a supplementary 2019 subthreshold 12T variant, so it is directly relevant to low-voltage SRAM; it changes WL, WWL, VGND, BL/BLB and precharge control, and reports comparative factors of 2.5x, 1.6x, 3.57x and 1.476x without mapping them to named metrics [192][191][190]. Its role is therefore a named low-voltage candidate, not a substitute for a fully specified 12T benchmark.

The evidence supports a source-backed Alternate Cell Designs survey: relative to 6T, 7T uses an added switch/feedback and separated read/write paths, 8T adds an isolated read port, 9T adds a three-transistor read port, and LP10T adds differential read/write circuitry to target read disturb, write ability, leakage and variability [42][56][128][48][43]. Reported trade-offs include an 11% 7T area penalty, a 13% 9T area increase and 8T operation at 0.41 V, so the implication is improved low-voltage robustness or power at the cost of added cell complexity and area [91][107][137].

Reported control evidence explicitly names separate read/write wordlines for 8T as RWL/WWL and for 9T as separate write/read wordlines; complete 7T, 10T and 11T polarity and phase descriptions are not supplied in the aggregate evidence, so they should not be inferred [75][128].

The Low-Voltage SRAM Failure Framework groups the comparison into read disturb/read stability, write ability, retention, process variation, leakage/dynamic power and sensing margin. 6T is the comparison reference; 8T reports RWL/WWL or RDWL/RDBL read-path controls with separate write controls, while the 7T and 8T evidence reaches 200mV and 0.41V respectively, reports a 1.71× 7T retention-voltage figure over 20°C–100°C, and identifies variability/low-voltage improvement for 8T; complete polarity and phase evidence for every 9T–11T control is not supplied [56][50][75][142][58][62][137][43].

## 2. Assist-Circuits

**Assist circuits change transistor competition temporarily.** Instead of permanently enlarging the cell, an assist changes the voltage applied to its access devices or storage latch during a vulnerable operation. The benefit depends on where the change is applied: a row wordline affects many cells, a column bitline affects selected and unselected rows, and a virtual supply rail affects every cell sharing that rail. [27]

**Eight schemes cover the requested inventory.** The table assigns each scheme its principal purpose; wordline overdrive can additionally improve read-current development in suitable architectures.

| Scheme | Primary operation | Electrical action | Main added circuitry | Principal trade-off |
|---|---|---|---|---|
| Negative bitline | Write | Drives low BL below ground | Coupling capacitor or negative generator | Energy and unselected-row stress |
| Suppressed bitline | Read stability | Reduces BL precharge level | Discharge/clamp or charge-sharing controls | Reduced read current |
| Wordline overdrive | Write | Raises WL above VDD | Boost generator and level shifting | Half-select and oxide stress |
| Wordline underdrive | Read stability | Lowers asserted WL | Controlled low-WL driver | Slower access |
| VDD boosting | Read | Raises cell supply | Supply generator and selection switches | Rail-switching energy |
| VDD lowering | Write | Collapses cell supply | Header, regulator, or charge sharing | Retention disturbance |
| GND boosting | Write | Raises cell ground | Virtual-ground driver or regulator | Headroom and shared-rail effects |
| GND lowering | Read | Drives cell ground negative | Negative generator and ground switches | Distribution energy |

### 1. Negative bitline: write assist

**Negative BL strengthens the access device.** Driving the low-going write bitline below ground increases the gate-to-source voltage of the selected access NMOS. It pulls the initially high storage node down more forcefully without first weakening the entire cell supply. The negative voltage can be produced using a flying capacitor, capacitive coupling, or a regulated negative source. [27]

**The main overhead is charge generation.** A coupling capacitor, switching devices, negative-voltage-tolerant write-driver path, and timed enable are required. Because bitlines have substantial capacitance, generating enough undershoot can consume appreciable energy. Park, Lee, and Jeong explicitly identify the large coupling capacitor and bitline load as the principal reason conventional NBL assistance is expensive when triggered for every write. [28]

**Published comparisons favor its write leverage.** Chandra, Pietrzyk, and Aitken found negative bitline and wordline boosting particularly effective in commercial low-power SRAM comparisons. At 0.7 V, they reduced critical write-wordline duration by approximately 2.5 times and its three-sigma spread by approximately 3.3 times. Negative BL had virtually no half-selected dynamic read-noise-margin penalty in their setup, whereas the other compared write assists degraded that margin by 10–15%. [29]

**Different half-select metrics explain different warnings.** A favorable half-selected read-noise margin does not eliminate every unselected-row risk. Zimmer et al. analyze write-stability exposure caused by the nonzero access-device gate-to-source voltage that a negative column bitline creates in unselected rows. Assist magnitude, duration, array organization, and the failure metric determine whether that exposure matters. [27]

**Selective activation reduces unnecessary energy.** Park et al.’s 7 nm ASAP post-layout study detects bitline status and triggers NBL only when a write initially fails. The reported write-energy improvement is approximately 19%, with roughly 10% reported area overhead for the combined proposed assist circuitry. This variant preserves the NBL mechanism while adding failure detection, capacitors, and control logic to avoid paying its full switching cost on easy writes. [28]

**Selection judgment:** NBL is a strong write-assist candidate when weak access current limits operation, provided its generator energy, undershoot stress, and unselected-row behavior fit the array.

### 2. Suppressed bitline: read-stability assist

**Suppressed BL reduces the disturbing charge.** Here, suppressed bitline means reduced or partial bitline precharge: the line begins below VDD rather than at the full supply. Connecting it to a stored zero produces less read disturbance. Literature implementations include regulated partial precharge and selective charge sharing between a charged bitline section and a discharged auxiliary section. [27][30]

**The main overhead is controlled conditioning.** Implementations require additional discharge or clamp devices, a reduced-precharge regulator, or switches and timing for charge sharing. A charge-sharing implementation can avoid a separate reference supply, but introduces a conditioning phase before WL assertion. Its final voltage depends principally on the capacitance ratio. [30]

**Stability improves at a current cost.** Lower bitline voltage reduces the access-path forcing that disturbs the latch, but can also reduce cell read current and alter sense-amplifier input common mode. Zimmer et al. discuss approximately 70%-of-VDD precharge, with a cited yield improvement from five to 5.7 sigma; their low-supply analysis finds only about 25 mV Vmin improvement and slightly worse readability. [27]

**Selection judgment:** Use suppressed precharge when read upset is more restrictive than signal-development time; it becomes less attractive when the cell already struggles to generate adequate sensing current.

### 3. Wordline overdrive: primarily write assist

**Boosted WL increases access strength.** Raising the asserted wordline above the cell supply increases access-device overdrive. During writing, this helps the access transistor overcome the pull-up or other opposing latch devices. It can also accelerate read-current development, but stronger access during a conventional 6T read can increase disturbance. [29]

**The main overhead is boosted driving.** The higher WL level may come from a separate supply, charge pump, or capacitive coupling. Level shifting, appropriate driver devices, pulse control, and often adaptive tuning are needed to deliver the boost reliably across process and supply variation. [29]

**Row sharing creates its main hazard.** The same boosted WL reaches half-selected cells in the row. Zimmer et al. show that improved readability and writability can accompany sharply reduced half-selected read stability, motivating delayed boost and adaptive control. Gate-voltage stress also constrains how large and how long the boost can be. [31]

**Selection judgment:** Wordline overdrive is compelling when selected-cell access strength is limiting and half-selected cells are isolated, restored, or otherwise protected; an ordinary column-multiplexed 6T row needs particularly careful qualification.

### 4. Wordline underdrive: read-stability assist

**Underdriven WL weakens the disturbing access.** Holding the asserted WL below VDD weakens the access transistor relative to the pull-down device. The stored-zero node rises less during reading, and row half-selected cells receive the same protection. Zimmer et al. identify WL underdrive as a particularly effective stability assist at very low voltage. [27]

**The main overhead is controlled bias.** The row driver must generate a repeatable underdriven high level, using biasing, clamping, or a regulated driver arrangement. Tracking circuitry and controlled timing may be added to prevent excessive underdrive at slow corners. The important cost is not necessarily many cell transistors, but a modified row-driving and bias-control network. [2]

**The speed penalty is intrinsic.** Weaker access reduces cell current, so the bitline takes longer to develop the required differential. If the same reduced WL level is used during writing to protect half-selected cells, writability also weakens. Park et al. consequently pair stability-oriented underdrive with selective assistance for slow reads or difficult writes. [28]

**A practical example combines complementary assists.** Kumar et al.’s 28 nm FDSOI implementation uses 90 mV WL underdrive and 114 mV negative-bitline undershoot. Reported read- and write-assist area overheads are 1.0% and 2.5%, respectively. The pair addresses the opposing margin effects directly rather than expecting one WL bias to improve both operations. [2]

**Selection judgment:** WLUD is attractive for density-oriented 6T arrays limited by read stability, especially when a separate write assist restores the access strength sacrificed during writing.

### 5. VDD boosting: read assist

**Higher cell VDD strengthens the latch.** Raising the cell supply strengthens the storage pull-down action through the cross-coupled inverter state and improves resistance to read disturbance. It can also increase read-current capability. Unlike WL boosting, however, cell-supply boosting does not directly strengthen the access transistor’s gate drive. [31]

**The main overhead is supply distribution.** A boosted supply source, selection switches or column multiplexing, and a separate or switched cell-supply network are required. Generator area is only part of the cost: a large supply rail must be charged, settled, and restored, and its resistance and capacitance influence both timing and energy. [28]

**The limiting transistor determines the benefit.** If the access device is already the principal read-current bottleneck, strengthening only the pull-down gives diminishing returns. If latch stability is limiting, strengthening the storage network can be preferable to boosting WL because it does not deliberately increase access-device disturbance. That distinction separates read stability from raw current-development speed.

**Selection judgment:** Cell-VDD boost is most persuasive when storage strength is limiting and the rail is locally segmented enough that switching its capacitance is affordable.

### 6. VDD lowering or collapse: write assist

**Lower cell VDD weakens pull-up contention.** Temporarily reducing or floating the cell supply makes it easier for the write-access path to discharge the initially high storage node. Implementations include a second lower supply selected through a multiplexer, an on-chip regulator, a switched header, or selected-column floating and charge sharing. [29]

**The main overhead is transient rail control.** Supply switches, collapse devices, restoration circuitry, and timing must support a controlled voltage excursion. The rail’s capacitance can make this energy-intensive. Excessive collapse also reduces the retention margin of unaccessed cells sharing the selected column supply. [27]

**Feedback control can limit over-assistance.** Huang and Chiou’s conditional-biasing write assist adjusts the bias only when a write fails and leaves native-success cases unchanged. Their silicon measurements report 29–34% lower write energy than conventional assists with similar area overhead and a 0.4 V minimum operating voltage. The extra circuitry senses write progress and controls the intervention rather than applying a full bias change unconditionally. [32]

**Charge sharing offers another implementation.** Cho et al.’s self-collapse and bitline-charge-sharing scheme combines cell-supply collapse with write-failure feedback. A measured 65 nm test chip operates down to 0.36 V and reports 12.6 µW/MHz write power. That normalized quantity corresponds to 12.6 pJ per clock cycle when one write is performed per cycle. [33]

**Selection judgment:** VDD collapse is useful when pull-up contention limits writing, provided collapse depth and restoration protect all cells sharing the rail; adaptive collapse is especially relevant when most writes succeed without assistance.

### 7. GND boosting: write assist

**Raised ground weakens the storage latch.** Raising the cell’s virtual ground reduces its effective rail-to-rail supply and weakens the cross-coupled inverters. This helps the write path move the internal nodes through their switching thresholds. It is the ground-side counterpart to lowering cell VDD, but its device-headroom effects are different. [27]

**The main overhead is a separate return.** The array needs a controllable virtual-ground network, selection switches, and a raised-ground source, level-shifting driver, or regulator. Cells sharing that return experience the bias excursion, so segmentation and half-select retention are central implementation issues. [29]

**More boost eventually loses leverage.** Zimmer et al.’s analysis finds benefit saturating around a boost of 30% of VDD. The NMOS pass gate can raise the low internal node only to approximately \(V_{\mathrm{DD}}-V_{\mathrm{TH}}\), limiting further improvement. A larger virtual-ground excursion can therefore consume more energy without providing proportional additional write margin. [27]

**Selection judgment:** Ground boosting is attractive when a local virtual-ground network already exists, but the useful bias range should be determined by access-device headroom and shared-cell retention rather than boost magnitude alone.

### 8. GND lowering: read assist

**Negative cell ground increases read drive.** Pulling cell ground below zero lowers the internal zero and increases effective gate-to-source voltage in both the pull-down and access devices. This can improve read-current development more directly than cell-VDD boost, which mainly strengthens the pull-down. [31]

**The main overhead is negative-ground distribution.** A negative-voltage generator, suitable footer switches, and a separately controlled ground network are required. Zimmer et al. identify the high capacitance of two horizontal ground lines per conventional 6T cell as a major energy burden. The voltage generator cannot be evaluated independently of the wires it drives. [31]

**Selective application can reduce the burden.** Park et al.’s selective cell-current boosting uses bitline-status detection to identify slow cells and applies negative CVSS only when needed. In its 7 nm ASAP post-layout evaluation, the required WL duration changes from 2.6 ns to 1.67 ns—approximately 36% improvement—while average read energy changes from 29.4 fJ to 27.7 fJ, approximately 5.8% lower. [28]

**Additional controls determine the final trade.** That implementation reuses failure detection and negative-voltage generation across read and write assistance, but adds transmission gates, read-select logic, and column-specific CVSS routing. The gain is strongest when rare slow cells set the timing requirement; if the detection and ground-network overhead dominates ordinary accesses, a simpler read port or shorter local bitline can be preferable.

**Assist-circuit takeaway:** Choose the voltage intervention that changes the limiting transistor-strength relationship, then include its generator, distribution, half-select, and timing costs in the comparison.

## 3. Performance Comparison Table

### Complete 6T–12T performance evidence

**The table is indexed by cell count.** It combines identifiable published examples and explicitly labelled conditional values, rather than presenting transistor count as a unique circuit specification. The source codes identify the topology and measurement basis of each entry. In particular, a macro-level power result and a bit-cell simulation remain different quantities even when both are expressed in µW.

**Reported and calculated values are distinguished.** `E` marks a calculated estimate or conditional bound. `F` denotes the common 7 nm predictive-model study; other codes identify separate literature examples. The read-power budget bounds are explained immediately below the source key.

| Parameter | 6T | 7T | 8T | 9T |
| --- | --- | --- | --- | --- |
| Area Overhead (%) | 0% | −23% T | 42.4% E:A | 83.3% E:A |
| Read Dynamic Power (µW) | 0–3.38 E:J | 0–2.18 E:J | 0–3.64 E:J | 0–2.60 E:J |
| Write Dynamic Power (µW) | 12.335 F | 0–2.18 E:J | 13.354 F | 0–2.60 E:J |
| Leakage Power (nW) | 0.730 F | 0–1,090 E:J | 0.812 F | 34.4 E:N |
| Read Access Time (ps) | 2,750 F | 456 J | 3,640 F | 388 J |
| Write Access Time (ps) | 300 F | 752 J | 300 F | 181 J |
| Sensing Method | Differential F | Single-ended Y | Single-ended F | Single-ended W |

| Parameter | 10T | 11T | 12T |
| --- | --- | --- | --- |
| Area Overhead (%) | 96.6% E:A | 34% D | 96% K |
| Read Dynamic Power (µW) | 0–4.02 E:J | 0–0.05433 E:D | 4.62 E:M |
| Write Dynamic Power (µW) | 19.794 F | 3.335 F | 6.248 F |
| Leakage Power (nW) | 0.565 F | 0.565 F | 0.151 F |
| Read Access Time (ps) | 5,630 F | 3,640 F | 4,210 F |
| Write Access Time (ps) | 380 F | 1,670 F | 740 F |
| Sensing Method | Differential ST2 F | Single-ended ST11T F | Single-ended ST12T F |

**The source key fixes the examples.** The following records identify which actual alternatives the table represents.

| Code | Source and representative circuit | Technology and operating basis | Evaluation |
|---|---|---|---|
| F | FinFET topology comparison [21] | 7 nm PTM-MG; 0.2 V; 25 °C | HSPICE preprint study |
| J | Joshi and Lobo [34] | 180 nm; individual 6T–10T cells | Pre/post-layout simulation |
| A, W | WRE cell comparison [35] | 90 nm; WRE8T, WRE9T, ST2 | HSPICE and layout study |
| D | E²VR11T/DARWA [23] | 45 nm; nominal 1 V, 27 °C | Cell/layout simulation |
| K | Kim and Mazumder 12T [24] | 40 nm supply-cutoff cell | Layout and circuit simulation |
| M | PCA12T comparison record [7] | 40 nm GP; 4 kb; 0.35 V; 11.5 MHz | Published macro comparison |
| N | PNN-stack 9T [12] | 45 nm; 0.8 V; FF leakage point | Circuit simulation |
| T, Y | 7T area summary [16], Yeoh 7T [4] | Equal-speed area; separate 65 nm read example | Literature summary; measured chip |

**The F entries use named variants.** The 10T column represents ST2, the 11T column ST11T, and the 12T column ST12T. F read delay is measured from wordline activation to 50 mV bitline discharge; write delay is measured until a storage node reaches the specified 10% or 90% supply threshold. The source’s dynamic-power discussion explicitly treats its dynamic row as write power, so it is used only in the write row here. [21]

**Area estimates retain their original denominators.** The A calculations use the reported 90 nm footprints: 6T 2.03 µm², WRE8T 2.89 µm², WRE9T 3.72 µm², and ST2 3.99 µm². Applying \(100(A/A_{\mathrm{6T}}-1)\) gives 42.4%, 83.3%, and 96.6%, respectively. D and K convert reported footprint factors of 1.34 and 1.96 into 34% and 96% overhead. T’s −23% instead describes the cited equal-speed 7T area reduction. [35][23][24]

**The J bounds are hypothetical budgets.** Joshi and Lobo report aggregate power of 1.69, 1.09, 1.82, 1.30, and 2.01 µW for 6T through 10T. For an explicitly hypothetical equal-duration read/write workload with constant leakage \(L\), the allocation below gives conservative nonnegative mode-power bounds. It does not assign the aggregate figure to both operations as though each were measured separately. [34]

\[
P_{\mathrm{avg}}=L+\frac{P_{\mathrm{R,dyn}}+P_{\mathrm{W,dyn}}}{2},\qquad 0\le P_{\mathrm{R,dyn}},P_{\mathrm{W,dyn}}\le2P_{\mathrm{avg}},\qquad 0\le L\le P_{\mathrm{avg}}.
\]

**The arithmetic supplies each budget cell.** Doubling those five aggregate powers gives the table’s 3.38, 2.18, 3.64, 2.60, and 4.02 µW upper bounds. For 7T, the corresponding leakage budget is \(1.09\text{ µW}\times1{,}000=1{,}090\text{ nW}\). Within this hypothetical workload, the two dynamic powers and leakage must jointly satisfy the equation; their individual upper bounds are not simultaneous operating values.

**Other estimates use explicit electrical anchors.** N leakage is \(0.8\text{ V}\times43\text{ nA}=34.4\text{ nW}\). D’s read-power interval uses its reported process-corner-average read-power budget of 54.33 nW, converted to 0.05433 µW, as an upper bound on the dynamic component. M’s conditional read-dynamic calculation is \(22.0-17.38=4.62\text{ µW}\), assuming the reported read-active power includes the matched retention baseline. [12][23][7]

### What the controlled comparisons actually establish

**The 7 nm study favors isolation.** At 0.2 V and 25 °C, conventional 8T read SNM is 67.1 mV versus 32.8 mV for 6T—approximately 2.05 times higher. Its hold SNM is also 67.1 mV, consistent with removal of the direct read-disturb path. Yet its read delay is 3,640 ps versus 2,750 ps, approximately 32.4% longer. Better stability therefore does not require faster nominal bitline discharge. [21]

**The strongest read margin is topology-specific.** ST11T reaches 79.2 mV read SNM, approximately 2.41 times the 6T value. ST12T reaches only 44.1 mV because its read access still disturbs the storage core. The larger device count helps other properties but does not substitute for electrical isolation. [21]

**Identical counts produce different trade-offs.** The same study’s two 10T and two 11T variants make this particularly clear.

| Variant | Read SNM (mV) | Write SNM (mV) | Leakage (nW) | Write delay (ps) |
|---|---:|---:|---:|---:|
| ST2 10T | 46.3 | 89.0 | 0.565 | 380 |
| PPN10T | 62.4 | 67.0 | 0.693 | 390 |
| FC11T | 67.1 | 84.5 | 0.236 | 2,380 |
| ST11T | 79.2 | 74.0 | 0.565 | 1,670 |

**The comparison separates three objectives.** PPN10T improves read margin over ST2 but has lower write SNM and higher leakage. FC11T leaks less than ST11T but writes more slowly and has lower read SNM. A designer optimizing standby energy, read robustness, or write latency would therefore make different choices even before considering layout and peripheral costs. [21]

**Lower reported power can reflect slower operation.** The F study reports 3.335 µW dynamic write power for ST11T versus 12.335 µW for 6T, approximately 73.0% lower. Its discussion also attributes some differences to the designs’ write frequencies. Consequently, that power reduction should not be interpreted automatically as an equal-throughput energy reduction. The 11T write delay is 1,670 ps versus 300 ps for 6T. [21]

**A separate study reverses timing rankings.** Joshi and Lobo’s 180 nm comparison reports the following values for its own implemented cells. These provide a direct within-study comparison for all counts from 6T through 10T, including the requested 7T and 9T entries. [34]

| Cell | Aggregate power (µW) | Read delay (ps) | Write delay (ps) | SNM (mV) |
|---|---:|---:|---:|---:|
| 6T | 1.69 | 671 | 267 | 400 |
| 7T | 1.09 | 456 | 752 | 375 |
| 8T | 1.82 | 517 | 392 | 650 |
| 9T | 1.30 | 388 | 181 | 650 |
| 10T | 2.01 | 167 | 242 | 600 |

**Its fastest choices differ by operation.** In this study, 10T has the shortest read delay, approximately 75.1% below 6T, while 9T has the shortest write delay, approximately 32.2% below 6T. The 7T cell has the lowest aggregate power but a write delay approximately 2.82 times the 6T value. Its SNM is also slightly below the 6T result, demonstrating that adding one device does not establish a universal margin improvement.

**Recent evidence preserves the same trade-off.** A 2026 IEEE 65 nm LTspice comparison, covering 30 supply points from 0.85 V to 1.5 V, reports 8T read SNM of 125 mV versus 100 mV for 6T and approximate read access of 240 ps versus 290 ps. It also reports lower 6T dynamic power by 14%. Its access criterion uses a 50%-VDD transition point, illustrating why delay definitions must accompany headline numbers. [36]

### Cell power, macro power, and energy are different comparisons

**Macro results include useful circuit costs.** Whole-memory power captures decoders, drivers, sensing, control, and inactive-cell leakage that an isolated bit-cell result can omit. The following examples retain their published active-power labels rather than silently equating them with dynamic-only power.

| Example | Circuit and operating point | Read active power (µW) | Write active power (µW) |
|---|---|---:|---:|
| Conventional 6T [35] | 256 kb, 90 nm, 0.725 V | 376.50 | 456.12 |
| WRE9T [35] | 256 kb, 90 nm, 0.350 V | 25.68 | 32.75 |
| PNN-10T [7] | 1 kb, 40 nm, 0.300 V, 10 MHz | 4.15 | 3.82 |

**The WRE9T comparison includes voltage leverage.** Relative to its 6T macro, read power falls approximately 93.2% and write power approximately 92.8%. However, the two macros operate at different minimum voltages, and read delay increases from 1.29 ns to 13.205 ns—approximately 10.2 times. The benefit combines a more robust topology, lower operating voltage, and different bitline organization; it is not a fixed-voltage transistor-count effect. [35]

**Power-delay products show the distinction.** Using those reported powers and delays, the calculated read power-delay product changes from approximately 0.486 pJ for 6T to 0.339 pJ for WRE9T: \(376.5\text{ µW}\times1.29\text{ ns}\) versus \(25.68\text{ µW}\times13.205\text{ ns}\). This approximately 30% reduction is much smaller than the read-power reduction. A power-delay product is an operation-level proxy, not automatically the complete energy of precharge, recovery, control, and subsequent idle time.

**Leakage changes the optimum frequency.** In Lu et al.’s measured 9T macro, leakage consumes approximately 81.1% of total power at the 0.325 V, 600 kHz point. In the PNN-10T post-layout macro, reported retention power is 3.64 µW compared with 4.15 µW read-active power. These examples explain why aggressive voltage scaling can cease to reduce energy/access once longer access time allows leakage energy to accumulate. [6][7]

**Area overhead also changes with scale.** The WRE9T study reports cell areas of 3.72 µm² versus 2.03 µm² for 6T, approximately 83.3% overhead. Its 256 kb macro areas are 1.18 mm² versus 0.86 mm², approximately 37.2% overhead. Longer columns allow read/write peripherals to be shared among more cells, so cell-area penalty and macro-area penalty need not match. [35]

**Peripheral occupancy can be substantial.** The PNN-10T study reports a 3.28 µm² bit cell and a 5,401.84 µm², 1,024-bit macro. Multiplying gives 3,358.72 µm² of nominal bit-cell area, approximately 62.2% of the reported macro footprint. This calculation illustrates why a small macro’s system cost cannot be estimated from the cell count alone. [7]

For this 1,024-bit macro, the total footprint is 5,401.84 µm²: 3,358.72 µm² for nominal bit cells and an estimated 2,043.12 µm² (37.8%) for peripheral, routing, and other non-cell area.

### Sensing configuration and reliability determine usable performance

**Single-ended is not inherently low energy.** A single read line saves wiring and can avoid switching a complementary line, but its decision threshold must remain separated from data-dependent leakage and noise. A full-swing single-ended read can also require more bitline movement than a differential small-signal read. References, keepers, leakage compensation, and hierarchical buffering determine the final energy and latency. [14]

**Differential sensing trades wires for discrimination.** The differential 12T design resolves BL–BR with a latch-type sense amplifier. The paired lines and read devices increase layout and loading, but a small differential can be resolved before either line makes a full logic swing. Its advantage depends on sense-amplifier offset, common-mode behavior, and the signal-development criterion, not simply on having two bitlines. [9]

**Peripheral design can outweigh cell changes.** Valaee’s 65 nm sensing study reports 216.5 ps schematic sensing delay and 3.65 µW column power for its preamplifier-assisted scheme, versus 484.8 ps and 4.64 µW for conventional sensing at 1 V, 500 MHz, and 60 fF bitline capacitance. Post-layout values for the proposed scheme become 410 ps and 4.887 µW. The added circuit improves the electrical sensing mechanism, while extracted parasitics materially change the final result. [30]

**Dynamic failure criteria alter Vmin.** Zimmer et al.’s 28 nm analysis gives a particularly important example: at 2 GHz, dynamic read-stability Vmin is approximately 450 mV, compared with 650 mV from a static test and 780 mV from a Gaussian fit to SNM. Their target relates to 90% yield for a 1 MB array with bit-error probability below \(10^{-9}\). Timing, population, and statistical method therefore belong beside any Vmin claim. [27]

**Finite samples establish finite evidence.** Kim and Mazumder report no dynamic-write failures for their proposed 12T cell in 50,000 Monte Carlo iterations under the specified 0.55 V write evaluation. Under an independent-trial binomial interpretation, zero failures would give an approximate 95% upper probability bound of \(3/50{,}000=6\times10^{-5}\), calculated using the rule-of-three approximation. It does not by itself establish a \(10^{-9}\) failure probability; rare-event extrapolation and demonstrated array operation answer different questions. [24]

**Evidence and measurement basis.** The literature discussed spans seminal work through 13 September 2026. Values retain their original cell, column, or macro basis; F is a 7 nm predictive-model simulation, J retains the authors’ 180 nm setup with unspecified supply, temperature, and operation mix, and D’s read-power bound is a process-corner average. E:J values are hypothetical balanced-workload budgets, E:M assumes subtraction of a constant retention baseline, and other E entries are stated unit or ratio calculations. Area denominators, sensing thresholds, activity rates, and simulation-versus-silicon status must remain attached to their examples.

### Selection judgment

**Density favors targeted assistance first.** For a density-driven array, 6T with carefully localized WLUD and write assistance is a strong starting point when it meets the required yield and timing. Read-decoupled 8T is a natural next choice when read disturb dominates. Cross-point 9T or appropriately selected 10T–12T structures become more persuasive when half-selection, feedback contention, long-column leakage, or very-low-voltage sensing remains limiting.

**The final choice is workload-dependent.** A standby-heavy memory benefits disproportionately from low leakage and inexpensive retention; a read-heavy memory emphasizes sensing energy and worst-case read time; a write-heavy memory emphasizes contention removal and assist-generator energy. Select the smallest cell-plus-periphery solution that meets those requirements at the intended voltage, temperature, array size, and reliability target—not the topology with the largest transistor count or the most favorable isolated number.

**Additional documented evidence**

| Entity | Parameter | 6T | 7T | 8T | 9T | 10T | 11T | 12T | Area Overhead (%) | Read Dynamic Power (µW) | Write Dynamic Power (µW) | Leakage Power (nW) | Read Access Time (ps) | Write Access Time (ps) | Sensing Method |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 6T conventional SRAM cell | The source supports representing the conventional…[94] | The baseline is a 6T static random-access memory…[305] | 51 pages[257] | 51 pages[257] | 130nm[320] | 51 pages[257] | 51 pages[257] | 51 pages[257] | 3%[294] | 376.5 µW [160] | 456.12 µW [160] | 70.440 nW [48] | 72 ps [62] | 138.4 ps [62] | The source supports representing the conventional…[94] |
| 7T SRAM topology class | The source cites “A 32-nm Subthreshold 7T SRAM bit…[150] | 65nm[318] | The paper distinguishes three SVL types: upper SVL…[321] | no evidence found | 90nm[157] | 45nm[284] | 90nm[157] | 90nm[157] | 11% [91] | 25.48 µW [121] | 7.5 µW [121] | 6.3 nW [121] | 9.18 ps [121] | 27.96 ps [121] | The TAK7T is described as a single-ended 7T cell.[291] |
| 8T SRAM topology class | no evidence found | Destructive, unstable read[314] | 31%[275] | The proposed circuit is designed in TSMC 65nm CMOS…[276] | 31%[275] | 36%[284] | 31%[275] | 31%[275] | 46%[239] | 18.4 µW[121] | 26.5 µW[121] | 5.98 nW[121] | 16.04 ps[121] | 37.93 ps[121] | The reported 8T asymmetric Schmitt Trigger bitcell…[199] |
| 9T SRAM topology class | The comparison table includes a 9T Mixed-VT cell at…[147] | no evidence found | 90nm[157] | 90nm[157] | The WARD representative is a novel 9-transistor SRAM… | 45nm[284] | 90nm[157] | 40 nm[145] | 83% [160] | 25.68 µW [160] | 32.75 µW [160] | 22.6 nW [280] | 65.57 ps [62] | 77.94 ps [62] | no evidence found |
| 10T SRAM topology class | The source names three 10T designs: QUCCE 10T, NS 10T…[319] | 10T[283] | 10T[283] | 10T[283] | 10T[283] | The source names three 10T designs: QUCCE 10T, NS 10T…[319] | 10T[283] | 10T[283] | 55% [162] | 4.15 µW [145] | 3.82 µW [145] | 84 nW [250] | 49.33 ps [62] | 46.31 ps [62] | no evidence found |
| 11T SRAM topology class | 300mV[310] | 11T[290] | 5000[206] | 5000[206] | 5000[206] | 10T[200] | The comparative table reports an 11T SRAM cell. | 7.5 ns[152] | 1.34× normalized area factor[48] | 3.595 µW[177] | 4.957 µW[177] | 23.95 nW | 140 ps[180] | 585 ps[180] | no evidence found |
| 12T SRAM topology class | The source names three 10T designs: QUCCE 10T, NS 10T…[319] | 01/12/2018[172] | The proposed differential 7T SRAM targets…[168] | The proposed 12T DP SRAM cell uses 2 decoupled read…[176] | 65-nm[179] | The source names three 10T designs: QUCCE 10T, NS 10T…[319] | 11T transistors[174] | For write improvement, the proposed 12T cell boosts…[300] | ~6%[83] | 2.736 µW[177] | 3.734 µW[177] | 7.69 nW[121] | 29.89 ps[304] | 1.28 ns[304] | no evidence found |

**Comparison basis and 6T baseline**

The comparison uses the conventional 6T CMOS bit cell as the denominator: six active transistors per bit cell, comprising two cross-coupled CMOS inverters and two access transistors [212][41]. The cross-coupled inverters provide bistable storage. A word line (WL) controls both access transistors; WL is low in hold mode and high during read or write, connecting the storage nodes to complementary bit lines BL and BLB [211][41]. Before a conventional differential read, the bit lines are precharged, the selected cell creates a voltage difference, and a sense amplifier resolves that difference [211][41]. Some implementations additionally expose a precharge control such as PRE, but PRE is a peripheral timing signal rather than an intrinsic sixth-transistor-cell control [213].

This baseline is the reference because low-voltage operation exposes its competing margins. Direct access to the storage nodes allows precharged bit lines to disturb the stored state during read, whereas successful write requires the bit-line driver to overpower the cross-coupled latch [211][213]. Increasing the pull-down/access strength ratio improves read stability but makes writing harder; supply scaling and process variation further reduce static noise margin and write ability [210][211]. The same scaling raises leakage and sensitivity to variation, while full-swing differential bit-line activity contributes dynamic power [213]. The 6T cell remains attractive for density and speed, but its shared read/write path motivates separate read ports, additional cell transistors, and read/write-assist circuits; the literature explicitly presents 8T and 10T cells as alternatives to the basic 6T mechanism [207]. Compared with a 4T cell, the 6T structure offers better speed, noise immunity, and standby-current behavior, but at greater cell size [212].

For the final matrix, `Parameter` is followed by `6T`, `7T`, `8T`, `9T`, `10T`, `11T`, and `12T`; transistor-count labels denote topology classes rather than unique universal circuits. The 6T area-overhead entry is therefore **0% by definition** when its own same-condition cell area is the denominator, not a cross-paper measured result. A source-specific comparison instead reports 6T area of **0.1285 mm²**, bit-line current of **31.02 µA**, total power of **2.09 mW**, and read/hold/write margins of **0.38/0.84/0.36 V**; these values do not constitute the requested read dynamic power, write dynamic power, leakage power, or access-time fields [213]. Likewise, a 180-nm Cadence study reports **54.63 × 10⁻⁹ W** power dissipation and **19.96 × 10⁻⁹ s** delay for a designed 6T cell, without separating read and write events or defining leakage and access endpoints [208].

One 180-nm comparative simulation does provide source-specific read/write delays: **6T 671/267 ps, 7T 456/752 ps, 8T 517/392 ps, 9T 388/181 ps, and 10T 167/242 ps**, respectively; its single power figures are **1.69, 1.09, 1.82, 1.30, and 2.01 µW**, not separate read and write dynamic-power measurements. The corresponding simulated SNMs are **0.400, 0.375, 0.650, 0.650, and 0.600 V** [40]. These results should remain source-qualified rather than being interpreted as universal transistor-count trends. A separate 40-nm, 0.4-V 10T comparison reports RSNM of **2.93×**, write margin of **1.99×**, and leakage-power reduction of **54.7%** relative to conventional 6T [209].

For the 7T column, evidence is variant-specific and conflicting rather than a single canonical value. A 0.35-µm small-swing 7T scheme reports **11% estimated area overhead** relative to an unstated 6T denominator, **15% estimated delay overhead**, and **75% write-cycle power saving**; it avoids half-precharging and negative voltage on the cell source line, while its shared VSS switch cannot practically be placed in every cell because the per-cell overhead would exceed 20% [42]. A different body-bias/shared-body-contact 7T implementation reports **10% area overhead** at \(N_{\max}=8\), with simulated access-time reductions of **36% for a “1” write** and **43% for read** at its stated 0.6-V, 256-word × 32-bit-array conditions [135]. These two 7T results use different variants, layout assumptions, and evaluation contexts and must not be pooled into one normalized area value.

6T: six transistors/cell [214]; low-V SNM, write, leakage [216]; area 0% (15nm,2013) [215]; read 12.28nW (2015) [216]; rest NR[217]

**Baseline and source-qualified entries**

For the comparison matrix, the conventional **6T SRAM cell** is a bistable latch formed by two cross-coupled CMOS inverters and two nMOS pass transistors, giving **6 transistors per bit cell**. Its normal controls are **WL** for both access transistors, complementary **BL/BLB** for data transfer, and **VDD/VSS** for the latch supplies. BL and BLB are precharged and equalized before a differential read; a sense amplifier detects their voltage difference. The cited implementation uses a latch-type sense amplifier enabled by **SAE**. [46][47]

At near- or subthreshold voltage, the 6T cell’s pass gate must be weaker than the inverter driver for read stability yet stronger than the inverter load for writing. This coupled sizing requirement exposes read disturb, write-ability loss, process-variation sensitivity, and slower access as voltage is reduced. During a read, current through a pass transistor and pull-down device can raise the opposite latch node toward its threshold and upset the stored state. [220][46] A low-voltage comparison also identifies pseudo-read and half-select errors, weak writing after added access stacking, bitline parasitic capacitance, and leakage as relevant limitations. [221]

For timing, one **6T** evaluation at **16 nm, 0.7 V, 128 cells** reports **4 ps read time** and **16 ps write time**; these are simulation results under that specific setup, not universal 6T constants. [218] A separate **45 nm, 450 mV, room-temperature** comparison reports **0.310 µs read delay**, equivalent to **310,000 ps** using \(0.310\times10^6\); its timing endpoint and evaluation basis differ, so it must remain a non-comparable alternative rather than be merged with the 4-ps result. [220] In this evidence set, 6T area overhead is **0% by definition** relative to the declared 6T denominator, while comparable 6T read/write dynamic-power and leakage values are **NR (not reported)**. [46][47]



A separate 22 nm FDSOI comparison identifies the standard 6T cell’s susceptibility to radiation-induced single-event upset; this is a reliability observation, not a substitute for the requested low-voltage power or timing metrics. [219]

**Source-conditioned comparison values**

The conventional 6T reference contains six transistors per cell: two cross-coupled inverters and two nMOS access devices. WL controls access to complementary BL/BLB; standby deasserts WL, read precharges and floats the bitlines for differential sensing, and write drives complementary bitline levels. Reduced VDD exposes device-ratio, \(I_\mathrm{on}/I_\mathrm{off}\), variability, leakage, read-disturb, writability, half-select, and sensing-delay limits [222][48][227]. A boosted wordline therefore belongs to the assist annotation, not to a new transistor-count class [49][225][226].

The [48] comparison uses 45-nm CMOS, 1 V, 27 °C, a 1-µs transient, and simulation. `NR` means not reported in the requested definition or unit. `†` converts source-reported read/write power from nW to µW; the source does not explicitly separate dynamic power.

| Parameter | 6T | 7T | 8T | 9T | 10T | 11T | 12T |
|---|---|---|---|---|---|---|---|
| Area Overhead (%) | 0% [48] | 10% body-bias variant, shared contact, \(N_\mathrm{max}=8\) [135] | 24% [48] | 32% [48] | 51% LP10T [48]; 297% low-leakage 10T [223] | 34% E²VR11T [48]; 68% MET11T [48] | NR; no comparable area value [224] |
| Read Dynamic Power (µW) | 0.070716† [48] | NR [135] | 0.071023† [48] | 0.120765† [48] | 0.089639† [48] | 0.053839† E²VR11T; 0.059224† MET11T [48] | NR; only total power is reported [224] |
| Write Dynamic Power (µW) | NR [48] | NR [135] | NR [48] | NR [48] | NR [48] | 0.029598† E²VR11T; 0.014506† MET11T [48] | NR [224] |
| Leakage Power (nW) | 70.440 [48] | NR [135] | 70.298 [48] | 119.543 [48] | 88.357 LP10T; 0.00000185 low-leakage 10T [48][223] | 52.216 E²VR11T; 57.834 MET11T [48] | NR [224] |
| Read Access Time (ps) | 236.095 ps [48] | NR; 43% relative reduction, no absolute ps value [135] | 93.655 [48] | 295.513 [48] | 273.906 [48] | 188.035 E²VR11T; NR for MET11T [48] | NR [224] |
| Write Access Time (ps) | 343.658 ps [48] | NR; 36% relative reduction, no absolute ps value [135] | 402.153 [48] | 152.056 [48] | 560.399 [48] | 336.972 E²VR11T; 722.505 MET11T [48] | NR [224] |
| Sensing Method | Differential sense amplifier; a 32-nm study used a large-signal HI-skew inverter pair [222][227] | NR [135] | NR [48] | NR [48] | Dedicated single-ended, non-destructive RL-to-RBL port; sense element unspecified [224] | Single-ended RBL with sense amplifier; dynamic differential write [48] | NR [224] |

For normalized areas, overhead is \(100(A_\mathrm{norm}-1)\): 1, 1.24, 1.32, 1.51, 1.68, and 1.34 yield 0%, 24%, 32%, 51%, 68%, and 34%, respectively [48]. The low-leakage 10T result is a different 0.18-µm prototype: 1.85 fW/bit at 0.35 V with a 0.5-V boosted supply, versus 3.6 fW without boosting, a reported 49% reduction [223]. A measured 0.13-µm 2-kb 6T array operated at 193 mV; first retention failure occurred at 134 mV and whole-array standby power was 26 nW [222]. Separate 32-nm 6T layout simulations reported read delays of 21/11/8/6/6 ps for Type 1b and write delays of 21/12/8.5/7.5/6.5 ps over 0.4–0.8 V, confirming that timing values are source- and voltage-specific [227].

6T: 6 transistors/cell—two cross-coupled CMOS inverters plus two access/pass devices. WL connects BL/BLB; precharge/SAE support differential sensing, and BL/BLB write [229][230][51][233]. At low VDD, read voltage-division upset, write/hold failure, sensing-margin loss, leakage, low read current, and PVT/mismatch limit operation [228][229][50][232]. Case: 65-nm/400-mV/4-Kbit post-layout Monte Carlo (2012) [228].

6T table: Area Overhead (%) NR; Read Dynamic Power (µW) NR; Write Dynamic Power (µW) NR; Leakage Power (nW) NR; Read Access Time (ps) NR; Write Access Time (ps) NR; Sensing Method: differential BL/BLB + sense amplifier [230][231]. A 1-V/500-MHz/60-fF sensing column reports 4.64 µW and 484.8 pS, not cell metrics [229]. In 90-nm PSPICE (July 2012), 8T read/write delay is 110/65 ps with 101 µW aggregate power; 9T is 120/10 ps with 151 µW; powers are unsplit [231].

6T (6 transistors/cell) has two cross-coupled inverters, two WL-controlled access devices and BL/BLB; differential sense-amplifier readout [235][236]. Low VDD makes shared pass-gate sizing a read-stability/writeability trade-off; variation shrinks margins [56][236]. Matrix: area overhead 0% (self-denominator); read/write dynamic power NR (0.104 µW is average power at 90 nm/1.8 V); read access NR (0–600 ps waveform proxy); write delay 9.47 ps at 90 nm/1.8 V [53][57]. Leakage is current, <50 fA/cell at 1.5 V/25 °C and <400 fA/cell at 85 °C, so nW power is NR [234]. A 32-nm 7T study (2017) reaches 0.4 V subthreshold; a 65-nm 7T–9T study (2014) covers area, leakage, speed and active power but has no normalized area/write-power values [52][59].

45-nm/0.8-V timing comparison (source variants retained) [62]:

|Access (ps)|6T|7T|8T|9T|10T|11T|12T|
|---|---:|---:|---:|---:|---:|---:|---:|
|Read|72|82.39|49.78 TA8T|65.57|49.33 proposed/52.5 PPN|51.88|NR|
|Write|138.4|123.9|96.22 TA8T|77.94|46.31 proposed/300.3 PPN|141.8|NR|
|Parameter|6T|7T|8T|9T|10T|11T|12T|
|-|-|-|-|-|-|-|-|
|Area Overhead (%)|0*|NR|NR|NR|NR|NR|96†|
|Read Dynamic Power (µW)|16.85|25.48|18.4|18.96|23.73|58.15|73.1|
|Write Dynamic Power (µW)|24.31|7.5|26.5|8.19|27.49|50.83|69.1|
|Leakage Power (nW)|5.6|6.3|5.98|6.13|5.99|2.26|7.69|
|Read Access Time (ps)|3.06|9.18|16.04|17.23|36.9|91.2|103.5|
|Write Access Time (ps)|33.53|27.96|37.93|36.7|41.83|61.06|118.3|
|Sensing Method|DF|SE|SE/DF|DF/NR|DF/SE|NR|NR|

NR = not reported here; variants are not universal count classes [62].

The 6T baseline has six transistors: two cross-coupled inverters and two NMOS access devices; wordline (WL) selects complementary bitlines (BL/BLB), and differential sensing reads their voltage difference [102,97]. At low VDD, the shared path perturbs the stored 0; pull-up/pass-gate/pull-down widths satisfy WPU<WPG<WPD, with variation aggravating stability [90,92,98].

The proposed 10T uses differential read, single-ended write, and RD/WR/CSR controls. At 45 nm/0.8 V it reports 49.33 ps read, 46.31 ps write, area 2.17×6T (=117% overhead), 1.76 µW read power, and 185.43 nW (=0.18543 µW) write power [62]. A measured 90-nm 8T is 46% larger and dissipates 2.68 µW total at 0.36 V/700 kHz—not read-dynamic power; its single-ended read uses a local inverter buffer [239]. A separate 65-nm 8T simulation gives 25%/12% write-time gains (write 0/1) at 600 mV and 21%/4% read-time degradation at 200/600 mV, with similar access time at ≥800 mV [238]. A separate 45-nm 6T evaluation reports 170.15 µW total power, not read-only [237].

6T: six transistors/cell—two cross-coupled inverters and two access devices—with WL and BL/BLB controls [242]. Low VDD causes read disturb, write failure, variation and sensing-margin loss [240]; without auxiliary circuits, one source reports a 0.6 V lower operating boundary [241]. A 180-nm Cadence post-layout simulation (2016) gives read/write delays (ns×1000→ps): 6T 671/267, 7T 456/752, 8T 517/392, 9T 388/181, 10T 167/242 [243]. Reported powers are 1.69/1.09/1.82/1.30/2.01 µW (6T→10T), not read/write-separated; area, leakage and sensing: NR [243].

6T: six transistors with differential sensing [245]; cited 7T: single-ended read/write [246]. At 32 nm, 6T read failed below 600 mV [247]. At 0.18 µm, low-VDD/high-temperature SS simulation, 6T/7T read delays were 454.36/353.90 and 458.97/379.45 ps (Read 0/1), respectively; endpoint was 50% WL-to-sense output [244]. At 65 nm/8 Kib, 7T vs 6T: +63.0% area, +70.6% read/+57.9% write power, −49.3% leakage, −42.7% read/−36.9% write delay [246]; relative, not absolute µW/nW/ps cells.

6T baseline: six transistors/cell—two cross-coupled inverters and two access nMOS; WL connects storage nodes to BL/BLB for differential sensing [252][253]. Low VDD exposes voltage-divider read upset, half-select disturb, variation-shrunken SNM, and conflicting read stability/write ability; leakage and sensing margin also limit operation [75][76][253]. A 45-nm, 256-Kb macro operated to 0.6 V from one supply with tracking write assist, a write booster, adaptive read assist, and self-timed dummy-cell sequencing (2008) [249]. The matrix assigns 6T 0% area overhead; a June-2015 comparison reports 12.35 mm² area, 72.82 ps read delay, and 8.976 ps write delay [74]. Absolute R/W power and nW leakage are NR [248][74]; relative evidence is 38% lower read power for an isolated design [254], and 6T leakage falls 63.1% (cell) or 61.7% (macro) at 0.65 V retention [251].

6T: differential sensing [255]; 8T: 2.83/3.96µW read/write, 350mV, 65nm, 25kHz [259]; 12T: ~6% area overhead, 0.4V [83]

6T: 6 transistors/cell; cross-coupled inverters+access; WL/BL/BLB; differential sense; low-VDD read/write-SNM risks [199,200].

6T: six transistors/cell—two cross-coupled inverters plus two access NMOS; WL drives complementary BL/BLB for read/write [97][99]. Low VDD exposes shared-path read disturb/low RSNM, read-stability/write-ability conflict, and variation-sensitive retention, leakage and delay [261][99][263][264]. Table: area overhead 0% (declared denominator); read/write dynamic power (µW), leakage (nW), read/write access (ps), and sensing method are NR/non-comparable—no standalone compatible values [262][98]. A 2026 32-nm CNTFET comparison instead reports 5.163-ps read, 7.668-ps write and 0.5349-nW power [100].

6T: 6 transistors/cell (2 CMOS inverters+2 access); WL/BL/BL′; low VDD cuts SNM/WM; this source’s metrics NR [254,267].

6T: 6 transistors/cell; WL/BL/BLB differential sensing [265]. 32 nm/1 V: area 0%; read 27.20 ps; read power 95.99 nW [113]

6T has six transistors—two cross-coupled inverters and two access devices; WL controls access, BL/BLB carry data, and readout is differential [37][298]. Low VDD lowers SNM, causing read disturb, write failure, variability, leakage and delay [267][303].

| Entity | Evidence/status |
|---|---|
| 6T | Area 0%; 0.69 µm² at 0.9 V (65 nm); leakage 0.4822 nW (482.2 pW; 65 nm, 0.4 V, 27°C); read/write µW and ps values NR [266][194]. |
| 7T | 45% lower array power than 6T in a 45-nm Cadence simulation; no absolute read/write value [268]. |
| CNTFET 6T–10T | Dynamic power is 10.054, 4.87, 12.458, 16.548 and 17.58 nW for 6T–10T respectively; operation is unspecified, so these are not read/write µW values [117]. |
| 11T | Area overhead is 22–28%; read speed improves 4×, but no ps value is reported; simulation uses 65 nm and 0.2–0.35 V [270]. |
| 12T | Area is 1.49× 6T (49% overhead); leakage is 0.4516 nW; read delay is 2.23× 6T, measured from RWL assertion to 100-mV BL discharge, with no absolute ps value [194]. |

Sensing is differential for 6T and 12T, single-ended for 8T and 9T, and differential or single-ended for 10T depending on the variant [37][298][293][194]. A 2024 comparison reports unspecified power of 100.2 µW for 6T and 8.02 µW for 10T; both remain non-comparable [302].

*0%=6T denominator; †12T: (1.96−1)×100=96% layout [304]. DF=differential, SE=single-ended, NR=not reported; slash=variant-specific [482,534,548].  
[312; June 2023] Power/delay rows: 1-KB, 0.6-V CMOS; 130/90/65 nm. Temp, workload, endpoints and sim/measurement status unreported; do not rank columns.

6T: 6/cell—2 cross-coupled inverters+2 access NMOS; WL controls BL/BLB [299]. Low VDD: read disturb/RSNM loss, writeability conflict [197]. Differential sense [301]. 2021, 0.2V/7nm/25°C: Pdyn 12.335µW, Pleak 0.730nW [197]; R/W split and delays NR.

2025 simulation (6T→10T): R=150/145/135/125/120 ps; W=210/190/175/165/160 ps; L=60/55/52/48/45 nW [297] (conditions incomplete). 6T=6 transistors, WL/PRE/SAEN controls and differential BL/BLB sensing [308][306]; 8T=single-ended, timing normalized [125]. Area: 7T=10% [135], 8T=8.5% (90-nm DVS) [274], 10T=+64% [308]. 9T leakage=22% or 33% lower (conflict) [277]. June 2016, 180-nm/1.8-V simulation lists 6T=1.21 µW and 12T=9.384 nW as unspecified power consumption, not read/write dynamic [307].

8T: 54.96/20.69 ps read/write (1 V, 300 K, sim) [279]; single-ended RBL/domino sensing [278]. 9T: +83% cell/+37% array area (90 nm, 300 mV) [146]. 10T: +33% area [199]; read/write 4.15/3.82 µW (40 nm, 0.3 V, 10 MHz, sim) [145].

6T: 2CI+2A, BL/BLB/WL, diff sense [281]. 7T SE: R/W1/W0 access ×2.71/×2.71/×8.42; ps NR [190]. 8T TG-DTMOS: R/W1/W0 delay −80/−63.95/−22.7%, power +400/+458.4/+221.4% (45nm) [190]. 9T: stacking+dual-VT cuts leakage [281]. 10T PNN: R/W 4.15/3.82µW 0.3V/10MHz, 40nm/1-kb [282]. 11T MET: R/W/L 59.224/14.506/57.834nW; W 722.505ps, R NR; 1V/27°C/1µs; area 1.68× (=68%) C6T [150].

6T: 2-inv+2-access; differential WL/BL/BLB sense [390,572]. 65nm/8-kbit simulation: 0.5V, 380kHz, R/W assist [312]. At 22nm, write-1/0=500/100ps@0.4V; 13/18µW@0.9V; other requested fields NR [152]. 8T-DP: read/write=19.5/19.6mW/MHz (40nm, 1.1V, 25°C); access=2.92ns; leakage=3742µW/Mbit, NC [313]. 10T P-10T: +8% area vs SE-10T; drivers <5% array; leakage=41.8µW@0.5V/6.25MHz; bitline power −70.9/53.6%, read delay +16/10%; absolute µW/ps NR [151]. 11T ST11T: SE Schmitt/VG; write-1=7500ps@0.4V; write-1/0=3/15µW@0.9V [152]. 7T/9T: NR here [391,392].

6T→9T (90 nm) R/W delay 72.82/8.97→98.85/10 ps; 9T single-ended, area 1.35×8T (no 6T %, leakage NR) [154]. 10-nm 6T HD/LV areas 0.0312/0.0367 µm²; PP-TVC/S-WL: 43% energy and 50/>100-mV VMIN reductions [315]. WRE9T@350mV:83% cell/37% block area,25.68/32.75µW R/W,13.205/12.88ns; 6T@725mV:376.5/456.12µW,1.29/1.76ns (read-SA excluded) [160]. R-power 6T→12T:16.85/25.48/18.4/18.96/23.73/58.15/73.1µW; 6T W=24.31µW, leakage=5.6nW [156]. 7T 8×8: R/W power NR; 8.4nW, R/W 21.1/16.5ns (90nm,0.7V), non-comparable [157]. 10T@45nm:36%↓ leakage/64%↓ current,13%↑ stability; absolute rows NR [284]. 11T:42nW leakage,0.2µW total (not R/W) @350mV/180nm; 32nm RB/NB:14.92/17.90nW@25°C (414.6/518.0@110°C), not R/W-specific [200][159].

6T six-transistor, differential BL/BLB [405,581]. 7T metrics NR; 11T area NR [161]. 9T RDFC relative @0.7 V; 1.86 µW untyped [402,405]. 8T single-ended, read-decoupled, leakage-limited swing [316]. 10T 1.81/1.07 read/write (unit unstated), leakage 0.96–1.22×6T [316]; +55% area vs 6T, relative delays [162]. 12T 1.8×/1.6× RSNM/WSNM@0.4 V; 2 nW untyped; rest NR [405,580].

6T differential SA [317]; 7T VLSA, 3.15/2.73 ns read/write [168]; 9T 97% area [171]; 12T 2.4 ns read [202].

12T: area +49% (1.49× 6T); leakage 0.4516 nW (451.6 pW; 2018, 65 nm, 0.4 V, 27 °C); differential sensing; other rows NR [172].

NR = not reported/not comparable; variants stay separate.  
7T: area ≈6T (24 nm) or +7% (90 nm); differential read; rest NR [594,429].  
8T: RD_VGND +4.8% area/+17% leakage; vertical-RWL read energy 5× lower at 0.5 V; metrics NR [287].  
9T: +37.8% area (65 nm); 4.05 µW minimum≠write, 0.05 µA≠leakage; read 6,000–850,000 ps (1.2→0.26 V, converted); equalized single-ended RBL; write/leakage NR [429,427,428].  
10T: stacked read port/boosted WL; leakage 2,000 nW (256-kb, 0.3 V, 27 °C); rest NR [176].  
11T: read/write 3.595/4.957 µW; static 2.038 µW≠nW leakage; times 19.392/15.861 lack units; single-ended RBL [177].  
12T: 45nm read/write 2.736/3.734 µW, static 1.893 µW; RHB-12T 5.89/5.87 nW (table/text), total dynamic 24.09 µW (table)/nW (text), read/write 114.77/16.45 ps; EDP12T read/write energy 1.82×/2.21× lower vs QUATRO12T (16-nm PTM); differential BL/BLN [429,430,597].

6T leak=29.5nW@0.21V[296];10T R/W=4.15/3.82µW@0.3V[179];11T R/W=18.26/5.32µW@0.5V/32nm[206];12T(WWL/D) leak=0.33nW@0.3V[288]

NR means not reported; values are variant- and condition-specific.

6T baseline: two cross-coupled inverters plus two access transistors. At 20-nm PTM FinFET (VDD=0.5 V; 10 fF), read time was 4.2–42 ps (modal 10.2 ps) and write time 38.6–368 ps (modal 75.1 ps); cell layout was 700 λ², while power and leakage were NR [311]. Differential VLSA/CLSA sensing is reported [309].

7T: the 7TP cell at 32 nm/0.8 V reports 6 µW read, 1.9 µW write, 256 pW (=0.256 nW) hold leakage, 0.553 µm² area, 5 ps read and 0.14 ns (=140 ps) write pulses, with single-ended latch sensing [292]. At 20 nm/0.5 V, modal read time is 24.1 ps and modal “0”/“1” write times are 18.9/26.3 ps; a 180-nm, 27°C simulation reports 5.45 µW dynamic power [311][136].

8T: a 22-nm 4×4 array reports 12 ps read, 10 ps write, 0.42 µW array power, and single-ended read/differential write [271]. A 7-nm measured current-mode macro reports 161 ps at 1.0 V/6.2 GHz and 10–12% power saving [272]. Another cell reports 3.93 µW read, 5.9 µW write, 16.07 nW leakage, and 1.42× area (42% overhead) [183]. Reduced precharge and raised virtual ground reduce bitline swing and power [273].

9T: the ST-9T comparison at 45 nm/0.5 V reports 22.6 nW leakage and 122 ns (=122,000 ps) read delay [280]; a measured 65-nm macro reports 79 ns at 0.4 V and 0.85 µs at 0.26 V [128]. Readout is single-ended Schmitt-trigger based [285]. Conflicting reports give 33% versus 3.3× leakage reduction [286].

10T: a 65-nm/1.2-V/500-MHz design reports 7.71 mW overall average power, not read/write dynamic power; those fields are NR [204]. DIBBSA establishes compatibility with fully differential 10T cells, not separate 10T metrics [283]. 11T at 45 nm/0.6 V reports 12.01 nW read, 18.67 nW write, 9.63 pW (=0.00963 nW) leakage, 140 ps read, 585 ps write, and 4.82 µm² area; its read path is single-bitline [180]. 12T is dual-port with decoupled read/write, saves 85.4% average read time, and has the largest RSNM, but no absolute requested metric is supplied [319].

6T:6 trans/cell (2 cross-coupled inverters+2 access); low-V PVT risk; body-bias tunes Vmin [321][289][295]; metrics NR [289].

The conventional 6T SRAM cell is the compact baseline, but access-transistor sizing and read-current Vdrop create a read-stability/writeability conflict; as VDD is reduced, poor margins, write failure, half-select disturbance, variability, and leakage become limiting, with one source placing unassisted operation no lower than 0.6 V [258][46][260][269][237][241]. It therefore supplies the reference against which decoupled cells and read/write assists are surveyed [256].

The comparison table places the 6T conventional SRAM cell beside the 7T, 8T, 9T, 10T, 11T, and 12T topology classes and keeps a sourced value or explicit “no evidence found” status for each requested metric, rather than inferring missing data [239][160][145][177].

The table retains units, scope, and evidence status and records conditions where available: 6T has 12.335 μW at 7 nm, 0.2 V, and 25 °C, 7T timing is reported at 20 nm and 0.5 V, and the measured 8T chip reports 2.68 μW at 90 nm, 0.36 V, and 700 kHz [197][311][239]. Missing workload, activity, load, stimulus, endpoint, source-date, or simulation/measurement fields are marked unreported rather than filled in.

Because the entries span different process nodes, VDDs, temperatures, frequencies, scopes, and simulation/measurement modes, their apparent higher/lower order is not a topology effect alone; the table therefore labels cross-source comparisons non-comparable and preserves source-specific values for 6T, 7T, 8T, and 9T [197][311][239][160].

Read/write dynamic power is kept as an operation-specific quantity: 6T reports 12.335 μW read and 456.12 μW write, 7T reports 25.48 μW read and 7.5 μW write, and 8T reports 18.4 μW read and 26.5 μW write [197][160][121]. The 9T evidence gives 4.05 uW at 350mV but does not label it read or write; separate 9T entries and any cross-source power ranking remain unsupported, while VDD, frequency, temperature, activity, and cell/array scope are retained only where reported [287].

Timing is source-defined: 6T lists 72 ps read and 138.4 ps write; 7T lists 9.2 ps, 57.1 ps, and 24.1 ps read plus 10.6 ps, 60.2 ps, 18.9 ps, 14.6 ps, 80.8 ps, and 26.3 ps write; 8T lists 16.04 ps read and 37.93 ps write [62][311][121]. In the supplied source-specific pair, 7T’s 3.15 ns is longer than 6T’s 1.29 ns by exactly 1.86 ns (2.44×); absent common start/end, threshold, load, sensing, and write-success conventions make this comparison non-universal [168][160].

The matrix preserves every requested metric position for the 6T conventional SRAM cell and the 7T–12T classes—area, read/write power, leakage, read/write access time, and sensing—using a value, a source-specific qualifier, or “no evidence found” rather than silently dropping a cell. It also keeps denominators separate: 9T is 83% above 6T at cell scope but 37% overhead at 256kb block scope, so those figures are not a single comparable rank [160].

The apparent rank is confounded: the 6T 12.335 μW entry is from 7 nm, 0.2 V, and 25 °C simulation, the 7T timing entries from 20 nm and 0.5 V simulation with Vth variation, and the 8T 2.68 μW entry from a 90 nm, 0.36 V, 700 kHz measured chip [197][311][239]. Thus process node, VDD, temperature, activity, load, stimulus, sensing circuitry, timing endpoints, and simulation-versus-measurement status can change the 6T–9T ordering; the table does not attribute higher/lower performance to transistor count alone.

The performance matrix uses the conventional 6T SRAM cell as the reference and places 7T–12T classes beside it; its supported 6T entries include 456.12 µW write power and 1.29 ns read time [160]. The implication is a traceable comparison baseline, not a claim that all columns share one operating condition.

Every requested 6T–12T position is populated by a sourced, unit-bearing value or an explicit “no evidence found” or “non-comparable” status; for example, the 9T 83% cell-area increase and 37% 256kb-block overhead remain separate entries [160]. This makes gaps visible while preventing a cell-level percentage from being read as a block-level percentage.

## References

[1] <http://people.ece.umn.edu/groups/VLSIresearch/papers/2008/ISCAS08_SRAM.pdf> Kim et al., subthreshold SRAM design; Decoupled 10T; 10T cell operation; Writeback architecture; Measured 10T implementation
[2] <https://doi.org/10.1109/vlsid.2016.62> Assisted 6T implementation; Six-sigma margin results; WLUD implementation context; Compensated WLUD and NBL
[3] <https://doi.org/10.1109/jssc.2019.2895236> 12T compiler demonstration; 7 nm compiler; Fabricated 12T compiler
[4] <https://pages.cs.wisc.edu/~yxy/pubs/iscas13_sram.pdf> Yeoh et al., 7T SRAM; Compact read and reference architecture; WTVG result; Measured 7T implementation; Named 7T signals
[5] <http://www.ee.umn.edu/groups/VLSIresearch/papers/2009/JSSC09_8TSRAM.pdf> Kim et al., 8T topology; RSCE implementation; RSCE comparisons; Write half-select behavior
[6] <https://doi.org/10.1109/tvlsi.2014.2318518> Half-select and bit-interleaving mechanisms; Cross-point 9T architecture; Aligned write-assist timing; Measured 9T results; Measured 9T power
[7] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8512319/> PNN-10T; PNN-10T schematic and controls; PNN-10T operating states; PNN read-decoupling comparison; PNN write mechanism; PNN macro results; PCA12T power inputs;…
[8] <https://www.jos.ac.cn/article/doi/10.1088/1674-4926/39/2/025001> BNBL 11T; BNBL mechanism; BNBL timing circuitry; BNBL comparisons
[9] <https://escholarship.org/content/qt99f6q9c9/qt99f6q9c9_noSplash_222640032c53d2930c471a00f6c095da.pdf> Differential 12T; Differential architecture and controls; WL/SEL write boost; Differential 12T sensing
[10] <https://www.intechopen.com/chapters/59211> Conventional 6T operation; Stability definitions
[11] <https://journals.tubitak.gov.tr/cgi/viewcontent.cgi?article=1849&context=elektrik> Read-disturb mechanism; SEDF10T structure; SEDF10T control table; SEDF10T stability and timing
[12] <https://doi.org/10.4236/cs.2012.32027> 6T strength-ratio conflict; 9T leakage input
[13] <https://doi.org/10.1109/jssc.2009.2020201> Device and circuit mechanisms; MBLC architecture and operating point
[14] <https://oar.a-star.edu.sg/storage/0/0jxvywzd3n/pub15-113-ics-017-pp.pdf> Data-dependent bitline leakage; Column-current comparison; Separate 8T ports and controls; Measured 8T sensing architecture; 8T sensing mechanisms
[15] <https://ieeexplore.ieee.org/document/6908567> 6T–8T counterexample
[16] <https://doi.org/10.5120/ijca2016912360> Alternative 7T operation; Equal-speed area comparison; Local-wordline control description
[17] <https://doi.org/10.3390/jlpea2020143> Read-SNM mechanism; Schmitt-trigger mechanism
[18] <https://past.date-conference.com/proceedings-archive/2012/PDFFILES/09.5_2.PDF> Hierarchical 8T implementation
[19] <https://doi.org/10.5121/vlsic.2012.3108> Representative 9T structure
[20] <https://doi.org/10.1109/tcsi.2014.2360760> MTCMOS 9T mechanisms; 9T timing and energy results
[21] <https://doi.org/10.21203/rs.3.rs-801530/v1> 11T variant comparison; FC11T comparison; ST11T controls and operation; ST12T counterexample; F topology, power, and timing definitions; Matched 6T–8T results;…
[22] <https://ieeexplore.ieee.org/document/8737872> Experimental 11T comparison
[23] <https://doi.org/10.3390/s23115095> DARWA circuit; DARWA read and write operation; DARWA evaluation conditions; 11T footprint; 11T power input
[24] <https://web.eecs.umich.edu/~mazum/PAPERS-MAZUM/12T%20SRAM.pdf> Supply-cutoff 12T; 12T device inventory and operation; RWL/RBL/VGND sequence; Matched read-margin comparison; 12T footprint; 12T Monte Carlo evaluation
[25] <https://doi.org/10.1109/iccd.2016.7753333> 32 nm SOI macro results
[26] <https://acris.aalto.fi/ws/portalfiles/portal/27962651/ELEC_Sharma_et_al_2018_International_Journal_of_Circuit_Theory_and_Applications.pdf> Data-dependent feedback cutting; 12T operating states; 12T relative results
[27] <https://people.eecs.berkeley.edu/~bora/Journals/2012/TCASI-12.pdf> Dynamic assist analysis; Negative-bitline mechanism; Dynamic NBL failure analysis; Partial-precharge analysis; Partial-precharge trade-off; WL-underdrive analy…
[28] <http://ndac.re.kr/data/file/sci/3754036775_Q4OtVgLT_94ce1d9881104ecddaf0ebdab18da7604ce02a00.pdf> NBL implementation overhead; Selective NBL results; WLUD performance trade-off; Column-based assist overhead; Selective negative-ground results
[29] <https://past.date-conference.com/proceedings-archive/2010/DATE10/PDFFILES/04.2_2.PDF> Commercial write-assist comparison; Wordline-boost mechanism; Boost generation options; VDD-collapse implementations; VSS-raising implementation
[30] <https://spectrum.library.concordia.ca/id/eprint/36175/1/Valaee_MASc_S2012.pdf> Selective-precharge circuitry; Selective-precharge mechanism; Sensing and post-layout comparison
[31] <https://people.eecs.berkeley.edu/~krste/papers/zimmer-ieeetcasII-2012.pdf> Half-select and timing effects; Cell-VDD boost analysis; Negative-ground readability mechanism; Ground-line energy overhead
[32] <https://doi.org/10.1109/tvlsi.2021.3084041> Conditional-biasing measurements
[33] <https://ieeexplore.ieee.org/document/9520659> Self-collapse and charge-sharing assist
[34] <https://link.springer.com/chapter/10.1007/978-981-10-1023-1_3> J aggregate-power inputs; 180 nm comparison
[35] <https://arxiv.org/html/1812.10011> 90 nm footprints; WRE9T macro comparison; Cell and macro area comparison
[36] <https://doi.org/10.1109/qpain69676.2026.11545855> 2026 6T–8T comparison
[37] <https://chipverify.com/digital-fundamentals/the-6t-sram-cell>
[38] <https://ajbasweb.com/old/ajbas/2014/August/41-50.pdf>
[39] <https://www.semanticscholar.org/paper/A-32-kb-0.35%E2%80%931.2-V%2C-50-MHz%E2%80%932.5-GHz-Bit-Interleaved-Grover-Visweswaran/6c5cae2847abc69b825aa9daf66fdc44bcbb3521/figure/0>
[40] <https://doi.org/10.1007/978-981-10-1023-1_3>
[41] <https://www.egr.msu.edu/classes/ece410/mason/files/Ch13.pdf>
[42] <https://www.design-reuse.com/article/58819-low-power-7t-sram-cell-scheme-saving-write-zero-power-/>
[43] <https://www.semanticscholar.org/paper/f0083e5031837b3bb366b5f789eac438d12bfd26>
[44] <https://www.academia.edu/13779655/DESIGN_OF_LOW_POWER_SRAM_CELL_WITH_IMPROVED_STABILITY>
[45] <https://ijcrt.org/papers/IJCRT2112227.pdf>
[46] <https://patents.google.com/patent/US7742326B2/en>
[47] <https://cmosedu.com/jbaker/courses/ee421L/f21/students/pinales/labproj/labproj.htm>
[48] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10255441/>
[49] <https://arxiv.org/html/2312.03559v1>
[50] <https://trea.com/information/ultra-low-power-sram-cell-circuit-with-a-supply-feedback-loop-for-near-and-sub-t/patentgrant/ac8e91cf-810d-41f8-b606-1b2f4bbf8094>
[51] <https://www.arcjournals.org/pdfs/ijirec/v3-i1/4.pdf>
[52] <https://www.semanticscholar.org/paper/A-32-nm-Subthreshold-7T-SRAM-Bit-Cell-With-Read-Gupta-Gupta/1a41179d4e645e46948063b83746594747df9d5a>
[53] <https://pages.hmc.edu/harris/class/e158/04/lect13.pdf>
[54] <https://aejournals.org/index.php/AEJ/article/download/3207/3223>
[55] <https://past.date-conference.com/proceedings-archive/2012/PDFFILES/09.5_2.PDF>
[56] <https://cdn.intechopen.com/pdfs/29218/InTech-Sram_cells_for_embedded_systems.pdf>
[57] <https://research.ijcaonline.org/iice2016/number1/iice201673.pdf>
[58] <https://doi.org/10.1109/isvdat.2016.8064899>
[59] <https://doi.org/10.1109/iscas.2014.6865602>
[60] <https://doi.org/10.9790/4200-0211520>
[61] <https://www.jstage.jst.go.jp/article/elex/15/20/15_15.20180758/_pdf>
[62] <https://digital-library.theiet.org/doi/full/10.1049/cds2.12006>
[63] <https://pdfs.semanticscholar.org/f6dc/66043ee0233b2bd1610f7562bcccc72e1190.pdf>
[64] <https://cse.buffalo.edu/~rsridhar/cse691/Present15/Narayan_Aiyer_ProjReport.pdf>
[65] <https://www.semanticscholar.org/paper/Design-of-12T-SRAM-cell-for-low-power-dissipation-Kumar-Ranjani/a52b7d75af9aeb377525b54abb8eb987a4b10e1c>
[66] <https://doi.org/10.1109/tvlsi.2007.915499>
[67] <https://doi.org/10.4236/cs.2011.24038>
[68] <https://doi.org/10.1109/tvlsi.2014.2318518>
[69] <https://dl.acm.org/doi/10.1145/1973009.1973034>
[70] <https://doi.org/10.1109/iscas.2008.4541702>
[71] <https://pages.cs.wisc.edu/~yxy/pubs/iscas13_sram.pdf>
[72] <https://www.semanticscholar.org/paper/Analyzing-the-Performance-of-6T-SRAM-Cell-and-64%C3%9764-Singh-Prakash/aa2fa790ebb95b10c5fc5e5b7cbd29a3da085ed6>
[73] <https://www.springerprofessional.de/en/comparative-analysis-of-different-sram-cells-based-on-transistor/52270130>
[74] <https://www.scribd.com/document/291639226/A-Comparative-Study-of-6T-8T-and-9T-SRAM-Cell>
[75] <https://arxiv.org/html/2306.08936v2>
[76] <https://doi.org/10.5120/ijca2015906751>
[77] <https://dl.acm.org/doi/10.1109/TVLSI.2019.2919104>
[78] <https://doi.org/10.1109/ecis65594.2025.11086956>
[79] <https://www.sciencedirect.com/science/article/abs/pii/S1879239125003765>
[80] <https://www.scribd.com/document/377765886/Scribd>
[81] <https://www.sciencedirect.com/science/article/abs/pii/S0026269213001031>
[82] <https://link.springer.com/chapter/10.1007/978-981-32-9767-8_52>
[83] <https://dl.acm.org/doi/10.1016/j.mejo.2017.01.003>
[84] <https://onlinelibrary.wiley.com/doi/10.1002/cta.2555>
[85] <https://doi.org/10.5121/vlsic.2012.3108>
[86] <https://www.sciencedirect.com/science/article/abs/pii/S0026269216300945>
[87] <https://onlinelibrary.wiley.com/doi/10.1002/cta.2951>
[88] <https://www.sciencedirect.com/science/article/abs/pii/S0026271421000925>
[89] <https://www.nature.com/articles/s41598-026-56270-6>
[90] <https://www.academia.edu/120476169/Comprehensive_Analysis_of_7T_SRAM_Cell_Architectures_with_18nm_FinFET_for_Low_Power_Bio_Medical_Applications>
[91] <https://ijcrt.org/papers/IJCRT1704451.pdf>
[92] <https://www.scribd.com/document/464309151/07100378-2>
[93] <https://www.scribd.com/document/871732956/Design-and-Implementation-of-Low-Power>
[94] <https://doi.org/10.3390/jlpea2020143>
[95] <https://www.mdpi.com/2079-9268/2/2/143>
[96] <https://ieeexplore.ieee.org/document/9396938>
[97] <https://pdfs.semanticscholar.org/015c/8e97987c677bc0bff2522be5e3e9b5ab708c.pdf>
[98] <https://www.scribd.com/document/910495458/Comparative-Analysis-of-6T-8T-and-10T-SRAM-Using-180nm-CMOS-Technology-for-IoT-Applications>
[99] <https://www.ijert.org/design-and-simulation-of-monolithic-3d-accelerated-8t-sram-using-planar-mosfets-for-low-power-and-high-reliability-ijertv15is042887>
[100] <https://pmc.ncbi.nlm.nih.gov/articles/PMC13062016/>
[101] <https://doi.org/10.1109/ccece47787.2020.9255734>
[102] <https://www.scribd.com/document/862228045/Performance-Analysis-of-Different-SRAM-Cells-and-Proposed-9T-SRAM-Cell>
[103] <https://m.researching.cn/articles/OJ71f0fe0153e563d5/figureandtable>
[104] <https://www.semanticscholar.org/paper/Design-and-analysis-of-SRAM-cells-for-power-using-Rukkumani-Saravanakumar/6ef8f67039aa43837f49f884682667e3621135ad>
[105] <http://www.ijmer.com/papers/vol%201%20issue%202/L012327331.pdf>
[106] <https://www.ijeat.org/wp-content/uploads/papers/v8i2s2/B10480182S219.pdf>
[107] <https://www.ijirset.com/upload/2016/nciet/13_PERFORMANCE.pdf>
[108] <https://www.academia.edu/79882378/Leakage_Characterization_of_10T_SRAM_Cell>
[109] <https://www.scribd.com/document/681481318/2>
[110] <https://beckassets.blob.core.windows.net/product/readingsample/10621157/9781461440383_excerpt_001.pdf>
[111] <https://dl.acm.org/doi/10.1007/s10470-020-01718-6>
[112] <https://doi.org/10.1109/access.2014.2323233>
[113] <https://journals.iium.edu.my/ejournal/index.php/iiumej/article/download/25/83/496>
[114] <https://doi.org/10.1109/tcsii.2010.2083130>
[115] <https://doi.org/10.1587/elex.13.20160382>
[116] <https://doi.org/10.1109/vlsic.2018.8502419>
[117] <https://doi.org/10.1155/2017/4575013>
[118] <https://doi.org/10.1134/s1063782625600299>
[119] <https://doi.org/10.1109/isicir.2014.7029512>
[120] <https://www.youtube.com/watch?v=6Waxt8GmGAo>
[121] <https://www.irjet.net/archives/V10/i6/IRJET-V10I628.pdf>
[122] <https://www.semanticscholar.org/paper/9d759abefacefcb98a2262741aa60aff0717e522>
[123] <https://www.semanticscholar.org/paper/Design-of-High-Speed-Single-Ended-6T-and-8T-SRAM-M./c9fbe3d6d7b89135a5690e03a931b6162d10263d/figure/5>
[124] <https://www.sciencedirect.com/science/article/abs/pii/S0167926015000024>
[125] <https://inria.hal.science/hal-01383730/document>
[126] <https://doi.org/10.1088/2631-8695/adfeb5>
[127] <https://patents.google.com/patent/US8310894B1/en>
[128] <https://doi.org/10.1109/tcsi.2014.2360760>
[129] <https://www.sciencedirect.com/science/article/abs/pii/S0167926015001583>
[130] <http://www.ee.umn.edu/groups/VLSIresearch/papers/2008/JSSC08_SRAM.pdf>
[131] <https://onlinelibrary.wiley.com/doi/10.1002/cta.3364>
[132] <https://doi.org/10.1007/s10470-018-1286-2>
[133] <https://www.academia.edu/69492161/Performance_Analysis_of_Conventional_SRAM_with_Higher_Order_SRAM_Topologies>
[134] <https://doi.org/10.1109/cicc.2008.4672109>
[135] <https://academicjournals.org/journal/IJPS/article-full-text-pdf/540433422647>
[136] <https://doi.org/10.1109/icccnt.2017.8204092>
[137] <https://doi.org/10.12785/ijcds/110182>
[138] <https://ijeer.forexjournal.co.in/papers-pdf/ijeer-130409.pdf>
[139] <https://scixplorer.org/abs/2014idet.conf...13K/abstract>
[140] <https://ir.uitm.edu.my/114754/1/114754.pdf>
[141] <https://doi.org/10.1109/jssc.2007.917509>
[142] <http://www.princeton.edu/~nverma/VermaLabSite/Publications/2009/SinangilVermaChandrakasan_JSSC2009.pdf>
[143] <https://dspace.mit.edu/handle/1721.1/62194?show=full>
[144] <https://doi.org/10.1109/isqed.2016.7479201>
[145] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8512319/>
[146] <https://www.academia.edu/21735035/A_64_Mb_SRAM_in_32_nm_High_k_Metal_Gate_SOI_Technology_With_0_7_V_Operation_Enabled_by_Stability_Write_Ability_and_Read_Ability_Enhancements>
[147] <https://pdfs.semanticscholar.org/8ced/c51d016f6ad867b070e1663072e963fdd9df.pdf>
[148] <https://xilirprojects.com/wp-content/uploads/2023/01/35.-A-7T-Security-Oriented-SRAM-Bitcell.pdf?srsltid=AU7gw4VI6fXZCVJ9jlhiEncESsBXBtdW8RR_RaDxq15MviYomWMZCPEx>
[149] <https://doi.org/10.64771/jsetms.2026.v03.i01.pp73-80>
[150] <https://mdpi-res.com/d_attachment/sensors/sensors-23-05095/article_deploy/sensors-23-05095.pdf?version=1685088580>
[151] <https://kresttechnology.com/krest-academic-projects/krest-mtech-projects/ECE/M-TECH%20VLSI%202019-20/BASE%20PAPERS/23.pdf>
[152] <https://corescholar.libraries.wright.edu/cgi/viewcontent.cgi?article=2984&context=etd_all>
[153] <http://ieeexplore.ieee.org/document/6576631>
[154] <https://www.academia.edu/10626112/A_comparative_study_of_6T_8T_and_9T_decanano_SRAM_cell>
[155] <https://doi.org/10.1109/tcsi.2018.2876785>
[156] <https://ns2.irjet.net/archives/V10/i6/IRJET-V10I628.pdf>
[157] <https://www.jetir.org/download1.php?file=JETIR2308411.pdf>
[158] <https://thinkindiaquarterly.org/index.php/think-india/article/download/15449/10584/>
[159] <https://ijettjournal.org/assets/year/2017/volume-45/number-10/IJETT-V45P299.pdf>
[160] <https://dl.acm.org/doi/10.1109/TVLSI.2014.2377518>
[161] <https://dl.acm.org/doi/abs/10.1007/s10470-022-02015-0>
[162] <https://www.ijcaonline.org/research/volume129/number2/ahmad-2015-ijca-906751.pdf>
[163] <https://www.jstage.jst.go.jp/article/elex/advpub/0/advpub_19.20220089/_article/-char/en>
[164] <https://doi.org/10.32628/ijsrset207348>
[165] <http://pdfs.semanticscholar.org/625a/0c1b601e284c49e27662d506b8123bccf75c.pdf>
[166] <https://ieeexplore.ieee.org/document/11135348/>
[167] <https://journal.beei.org/index.php/EEI/article/download/557/926>
[168] <https://doi.org/10.1109/access.2021.3075460>
[169] <https://ijsrset.com/paper/6466.pdf>
[170] <https://research.ijcaonline.org/volume115/number18/pxc3902615.pdf>
[171] <https://scispace.com/pdf/a-single-ended-disturb-free-9t-subthreshold-sram-with-cross-221sd28qry.pdf>
[172] <https://scispace.com/pdf/a-write-improved-low-power-12t-sram-cell-for-wearable-2n7vb11iny.pdf>
[173] <https://doi.org/10.1007/s00034-018-0858-9>
[174] <https://doi.org/10.1002/cta.3361>
[175] <https://doi.org/10.1109/socc.2014.6948972>
[176] <https://doi.org/10.32657/10356/65355>
[177] <https://www.ijesrt.com/Old_IJESRT/issues%20pdf%20file/Archive-2017/April-2017/55.pdf>
[178] <https://mdpi-res.com/d_attachment/micromachines/micromachines-14-01305/article_deploy/micromachines-14-01305.pdf?version=1687683329>
[179] <https://doi.org/10.3390/s21196591>
[180] <https://dl.acm.org/doi/full/10.1145/3653675>
[181] <https://doi.org/10.1587/elex.19.20220351>
[182] <https://ieeexplore.ieee.org/document/11386655>
[183] <https://iopscience.iop.org/article/10.1088/1402-4896/adf5fb/meta>
[184] <https://doi.org/10.1149/2162-8777/aca791>
[185] <https://www.research.ed.ac.uk/en/publications/leakage-immune-modified-cross-coupled-inverter-based-mi-12t-sram-/>
[186] <https://www.nature.com/articles/s41598-026-48572-6>
[187] <https://doi.org/10.1109/icicdt.2019.8790912>
[188] <https://doi.org/10.1109/isocc.2014.7087645>
[189] <https://www.researching.cn/ArticlePdf/m00098/2022/43/3/031401.pdf>
[190] <https://discovery.researcher.life/article/leakage-immune-modified-cross-coupled-inverter-based-mi-12t-sram-in-sub-threshold-regime/d7ed9c06c3e73a62980d83dfdda08e09>
[191] <https://doi.org/10.1109/iccece46942.2019.8941661>
[192] <https://www.mdpi.com/2079-9292/10/21/2724>
[193] <https://www.academia.edu/36811052/Design_of_Read_and_Write_Operations_for_6t_Sram_Cell>
[194] <https://acris.aalto.fi/ws/portalfiles/portal/27962651/ELEC_Sharma_et_al_2018_International_Journal_of_Circuit_Theory_and_Applications.pdf>
[195] <https://www.gyanvihar.org/wp-content/uploads/2019/03/SRAM-cell.pdf>
[196] <https://xilirprojects.com/wp-content/uploads/2023/01/17.-10T-SRAM-Using-Half-VDD-Precharge-and-Row-Wise-Dynamically-Powered-Read-Port-for-Low-Switching-Power-and-Ultralow-RBL-Leakage.pdf>
[197] <https://doi.org/10.21203/rs.3.rs-801530/v1>
[198] <http://hdl.handle.net/10012/6167>
[199] <https://mdpi-res.com/d_attachment/jlpea/jlpea-02-00143/article_deploy/jlpea-02-00143.pdf?version=1334735654>
[200] <https://www.jos.ac.cn/fileBDTXB/oldPDF/09111601.pdf>
[201] <https://nopr.niscpr.res.in/bitstream/123456789/61028/1/IJPAP%2060%2812%29%201016-1024.pdf>
[202] <https://escholarship.org/content/qt99f6q9c9/qt99f6q9c9.pdf>
[203] <https://ieeexplore.ieee.org/document/7801981/>
[204] <https://doi.org/10.1109/hnicem.2018.8666355>
[205] <https://doi.org/10.1109/access.2022.3161147>
[206] <https://doi.org/10.1088/1402-4896/ae32d0>
[207] <https://www.youtube.com/watch?v=RPQ0KsUgBAc>
[208] <https://www.academia.edu/27323585/Performance_Analysis_of_a_6T_SRAM_Cell_in_180nm_CMOS_Technology>
[209] <https://doi.org/10.1109/apccas.2018.8605599>
[210] <https://doi.org/10.1109/delta.2008.98>
[211] <https://doi.org/10.37394/23201.2020.19.2>
[212] <https://web.eecs.umich.edu/~prabal/teaching/eecs373-f11/readings/sram-technology.pdf>
[213] <https://opensiuc.lib.siu.edu/cgi/viewcontent.cgi?article=1067&context=ece_articles>
[214] <https://doi.org/10.1109/iconset.2011.6167980>
[215] <https://doi.org/10.1109/isqed.2013.6523634>
[216] <https://doi.org/10.1109/smacd.2015.7301691>
[217] <https://doi.org/10.1007/978-981-13-5950-7_47>
[218] <https://sbmicro.org.br/sforum-eventos/sforum2019/A%20Comparative%20Evaluation%20of%20SRAM%20topologies.pdf>
[219] <https://www.mdpi.com/2072-666X/14/4/845>
[220] <https://kuwaitjournals.org/jer/index.php/JER/article/view/10399/2293>
[221] <https://www.mdpi.com/2079-9292/10/6/685>
[222] <https://blaauw.engin.umich.edu/wp-content/uploads/sites/342/2017/11/369.pdf>
[223] <http://blaauw.engin.umich.edu/wp-content/uploads/sites/342/2017/11/438.pdf>
[224] <https://www.researchsquare.com/article/rs-7923985/latest.pdf>
[225] <http://arxiv.org/abs/2003.12558v1>
[226] <https://www.youtube.com/watch?v=1tQQqBmQ8Z8>
[227] <https://www.jestr.org/downloads/Volume9Issue5/fulltext23952016.pdf>
[228] <https://ieeexplore.ieee.org/document/6291950/>
[229] <https://spectrum.library.concordia.ca/id/eprint/36175/1/Valaee_MASc_S2012.pdf>
[230] <https://electronics.stackexchange.com/questions/144986/schematic-for-run-of-the-mill-sram>
[231] <https://ijltet.org/wp-content/uploads/2012/07/71.pdf>
[232] <https://www.design-reuse.com/article/61060-low-voltage-sram-the-missing-link/>
[233] <https://patents.google.com/patent/US10679694B2/en>
[234] <http://courses.ece.ucsb.edu/ECE125/125_W11Banerjee/Lectures/ibmsram.pdf>
[235] <https://doi.org/10.25103/jestr.095.23>
[236] <https://blaauw.engin.umich.edu/wp-content/uploads/sites/342/2018/02/Zhai-A-Variation-Tolerant-Sub-200mV-6-T-Subthreshold-SRAM.pdf>
[237] <https://doi.org/10.1109/iccc64910.2025.11077211>
[238] <https://doi.org/10.1007/978-3-319-25279-7_6>
[239] <https://ietresearch.onlinelibrary.wiley.com/doi/10.1049/iet-cds.2018.5150>
[240] <https://arxiv.org/html/1812.10011>
[241] <https://www.mdpi.com/1424-8220/21/19/6591>
[242] <https://github.com/Adivakersharma/10T_BLP_SRAM_Cell>
[243] <https://researcher.manipal.edu/en/publications/comparative-study-of-7t-8t-9t-and-10t-sram-with-conventional-6t-s/>
[244] <https://scholars.csus.edu/esploro/fulltext/graduate/A-comparative-analysis-of-performance-parameters/99257831264801671?repId=12232580370001671&mId=13233870710001671&institution=01CALS_USL>
[245] <https://www.mdpi.com/2079-9268/6/3/16>
[246] <https://doi.org/10.1109/isvlsi.2013.6654624>
[247] <https://ieeexplore.ieee.org/document/8675024>
[248] <https://www.ramxeed.com/tech-column/low-power-sram-design-considerations/>
[249] <https://doi.org/10.1109/esscirc.2008.4681902>
[250] <https://www.mdpi.com/2079-9268/7/3/24>
[251] <https://doi.org/10.1109/ojcas.2021.3104945>
[252] <https://www.kresttechnology.com/krest-academic-projects/krest-mtech-projects/ECE/M-TECH%20VLSI%202019-20/BASE%20PAPERS/22.pdf>
[253] <https://patents.google.com/patent/US6985380B2/en>
[254] <https://doi.org/10.5120/13240-0681>
[255] <https://doi.org/10.1109/icm.2012.6471396>
[256] <https://www.scribd.com/document/335651639/Low-Voltage-and-Low-Power-in-Sram-Read-and-Write-Assist-Techniques>
[257] <https://www.scribd.com/document/373429118/Report-SRAM-6T-Cell-Design-Analysis-Nisha-1306184446>
[258] <https://www.sciencedirect.com/science/article/abs/pii/S1434841120322044>
[259] <http://www.princeton.edu/~nverma/VermaLabSite/Publications/2007/nverma_isscc2007_paper.pdf>
[260] <https://doi.org/10.1109/isscc.2015.7063052>
[261] <http://arxiv.org/abs/1905.08624v1>
[262] <http://arxiv.org/abs/2006.13285v3>
[263] <https://www.ijera.com/papers/Vol2_issue3/AI23204208.pdf>
[264] <https://dl.acm.org/doi/epdf/10.1145/2483028.2483056>
[265] <https://ebrary.net/180412/engineering/sram_cell_operation>
[266] <https://doi.org/10.1109/vlsit.2003.1221088>
[267] <https://doi.org/10.1587/elex.5.750>
[268] <https://doi.org/10.1109/acct.2012.81>
[269] <https://patents.google.com/patent/US9236113B2/en>
[270] <https://doi.org/10.1109/socc.2008.4641491>
[271] <https://doi.org/10.1088/1361-6641/abf7d3>
[272] <https://www.scribd.com/document/951481447/24-1-a-6-2-GHz-Single-Ended-Current-Sense-Amplifier-CSA-Based-Compileable-8T-SRAM-in-7nm-FinFET-Technology>
[273] <https://doi.org/10.5194/ars-9-247-2011>
[274] <https://www28.cs.kobe-u.ac.jp/wp-content/uploads/2017/03/0706_morita_vlsi.pdf>
[275] <https://doi.org/10.1109/date.2012.6176649>
[276] <https://doi.org/10.1109/vlsi-soc.2014.7004186>
[277] <https://www.scirp.org/pdf/CS20110400006_90531935.pdf>
[278] <https://doi.org/10.1109/jssc.2016.2540799>
[279] <https://www.researching.cn/ArticlePdf/m00138/2025/23/2/100306.pdf>
[280] <https://pdfs.semanticscholar.org/a816/90b6a87d1857d62a8d7e231b28decdbb6223.pdf>
[281] <https://www.ijraset.com/research-paper/design-and-implementation-of-sram-using-verilog>
[282] <https://mdpi-res.com/d_attachment/sensors/sensors-21-06591/article_deploy/sensors-21-06591.pdf?version=1633163336>
[283] <https://www.eecg.utoronto.ca/~dr.patel/pdf/pubs/DIBBSA_Accepted_FINAL_VERSION.pdf>
[284] <https://doi.org/10.1109/ecs.2015.7124742>
[285] <https://doi.org/10.1109/tcsi.2020.2964903>
[286] <https://www.scirp.net/html/7903.html>
[287] <https://doi.org/10.32657/10356/86213>
[288] <https://digital-library.theiet.org/doi/pdf/10.1049/iet-cds.2019.0050?download=true>
[289] <https://oar.a-star.edu.sg/storage/0/0jxvywzd3n/pub15-113-ics-017-pp.pdf>
[290] <https://www.computer.org/csdl/journal/si/2019/10/08737872/1aW6nsT0652>
[291] <https://doi.org/10.36227/techrxiv.21326055.v1>
[292] <https://royalsocietypublishing.org/rspa/article/478/2259/20210745/82483/A-comprehensive-analysis-of-different-7T-SRAM>
[293] <https://www.academia.edu/30761659/Low_Voltage_and_Low_Power_in_SRAM_Read_and_Write_Assist_Techniques>
[294] <https://ietresearch.onlinelibrary.wiley.com/doi/10.1049/iet-cds.2013.0205>
[295] <https://nckur.lib.ncku.edu.tw/retrieve/231989/%E5%BC%B5%E5%90%8D%E4%BD%91ISQED-Poster_90cm-X-120cm_v2.pdf>
[296] <https://doi.org/10.14711/thesis-b1626269>
[297] <https://theaspd.com/index.php/ijes/article/download/5626/4081/11399>
[298] <https://sites.utexas.edu/CRL/wp-content/uploads/sites/4417/2018/11/6_ST2_TVLSI.pdf>
[299] <https://www.sciencedirect.com/science/article/abs/pii/S1434841126003900>
[300] <https://doi.org/10.1109/iccd.2016.7753333>
[301] <https://www.researchsquare.com/article/rs-6625510/v1.pdf?c=1750683746000>
[302] <https://doi.org/10.1109/emergin63207.2024.10961032>
[303] <https://gvpress.com/journals/IJHIT/vol9_no2/10.pdf>
[304] <https://web.eecs.umich.edu/~mazum/PAPERS-MAZUM/12T%20SRAM.pdf>
[305] <https://doi.org/10.13164/re.2017.0772>
[306] <https://escholarship.org/content/qt4hk101kx/qt4hk101kx.pdf>
[307] <http://www.ijste.org/articles/IJSTEV2I12205.pdf>
[308] <http://hdl.handle.net/11250/2371162>
[309] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10780789/>
[310] <https://www.scribd.com/document/905378909/New-SRAM-design-using-body-bias-technique-for-ultr>
[311] <https://onlinelibrary.wiley.com/doi/10.1002/ecj.12162>
[312] <https://doi.org/10.1109/icecs.2015.7440347>
[313] <https://www-vlsi.es.kit.ac.jp/thesis/doctor/pdf/yokoyama.pdf>
[314] <https://www.sciencedirect.com/science/article/abs/pii/S003811011830159X>
[315] <https://doi.org/10.1109/jssc.2018.2861873>
[316] <https://docs.lib.purdue.edu/cgi/viewcontent.cgi?article=1007&context=ecepubs>
[317] <https://doi.org/10.54105/ijvlsid.b1210.092222>
[318] <https://doi.org/10.1109/ftfc.2012.6231727>
[319] <https://doi.org/10.1109/edssc.2019.8754291>
[320] <https://ijaem.net/issue_dcp/Design%20of%206T%20SRAM%20Cell%20Using%20SKY130%20PDK.pdf>
[321] <https://www.ijsr.net/archive/v4i8/SUB157674.pdf>
