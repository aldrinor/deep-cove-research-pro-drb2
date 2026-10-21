# Choosing an Open-Source Drone Autopilot: A Technical and Ecosystem Comparison Through 2024

**Start with ArduPilot or PX4.** For a drone project requiring autonomous missions, an onboard computer, custom software and substantial simulation, these are the strongest general-purpose candidates. ArduPilot is especially attractive for broad vehicle support and onboard Lua customization; PX4 stands out for robotics integration, modular development and established MATLAB/Simulink workflows. Paparazzi suits custom aircraft and research, Betaflight suits first-person-view (FPV) racing and freestyle, iNAV suits navigation-oriented RC aircraft, and LibrePilot is most compelling when its existing hardware or software already fits your project.

| Project | Best-fit profile | Decisive advantage | Main trade-off |
|---|---|---|---|
| ArduPilot | General-purpose autonomous vehicles | Broad vehicle coverage; onboard Lua; MAVLink interfaces | Many configuration choices; scripting depends on hardware |
| PX4 | Robotics and model-based development | Native ROS 2 bridge; modular architecture; extensive simulation | Integration requires compatible software versions |
| Paparazzi | Research, education and custom aircraft | Configurable modules, flight plans and complete ground system | Its own communications and development conventions |
| LibrePilot | Vehicle-control projects and existing installations | Integrated flight/ground architecture; OpenPilot heritage | Advanced integrations are more project-specific |
| Betaflight | FPV racing and freestyle | Pilot-oriented control, filtering, tuning and peripheral support | Rescue functions are not a general mission-autonomy stack |
| iNAV | Navigation-equipped multirotors and fixed-wing aircraft | Position/altitude hold, return-to-home and waypoint missions | MSP-oriented workflow rather than broad robotics integration |

**The comparison is requirement-dependent.** ArduPilot’s documented scope includes aircraft, rovers and underwater vehicles; PX4 combines multiple vehicle types with external robotics interfaces; and the specialist projects organize their software around different priorities. Those differences matter more than finding one universal winner. [1] · PX4 architecture [2] · Paparazzi project [3] · LibrePilot project [4] · Betaflight project [5] · [6]

**This report uses the end-of-2024 perspective.** Part One explains each project’s core features, operating environment, implementation language, scripting, communications and license. Part Two presents the requested ecosystem table, then explains the practical trade-offs behind the ratings and the conditions that would change the recommendation.

## Part One — Technical Summaries

### Essential terms and distinctions

**An RTOS manages time-sensitive work.** A real-time operating system helps schedule tasks such as reading sensors, estimating aircraft motion and updating motor commands predictably. ChibiOS, NuttX and FreeRTOS are examples. “Real-time” concerns meeting timing requirements; it does not simply mean that a processor is fast. Paparazzi’s architecture explicitly distinguishes an RTOS-based implementation from a legacy implementation running directly on the hardware. [7]

**Bare-metal firmware still schedules tasks.** Software without a traditional RTOS can use interrupts and its own scheduler to organize flight-control work. Therefore, “no traditional RTOS” does not mean “no real-time behavior.” Conversely, choosing a recognized RTOS does not by itself establish better flight performance: the drivers, scheduling design, workload and complete sensor-to-actuator delay also matter. [8] · [9]

**Core code and scripts differ.** The core language implements the flight controller itself, including control algorithms and hardware drivers. A supported scripting language may instead run inside the controller, on a separate onboard computer, on a ground computer or even on the radio transmitter. These are different capabilities, so each technical entry identifies where secondary code executes.

**A companion computer adds computing capacity.** This is a separate onboard computer, such as a Linux single-board computer, connected to the flight controller. It can process images, plan routes or manage payloads while the flight controller handles stabilization and other immediate flight responsibilities. ArduPilot and PX4 both document this separation explicitly. [10] · [11]

**Protocols define messages and behavior.** A communication protocol specifies how systems exchange information. MAVLink and MSP define messages; USB, serial wiring, Ethernet and radio links carry those messages. A ground control station, or GCS, is the application used to configure, monitor or command the vehicle. Sharing a connector or radio does not necessarily make two autopilots compatible with the same GCS. [12] · [13]

**ROS connects robotics software components.** ROS means Robot Operating System, but it is primarily a collection of robotics middleware, libraries and tools—not a replacement for the flight controller’s RTOS. ROS 2 is its newer generation. An autopilot’s ROS connection lets robotics programs exchange sensor information and commands with flight software, either through a translator such as MAVROS or through a more direct message bridge. [14] · [15]

**SITL and HITL test different things.** Software-in-the-loop, or SITL, runs an autopilot executable on a development computer while a model supplies the vehicle’s simulated motion and sensors. Hardware-in-the-loop, or HITL, keeps the flight-controller hardware in the loop while a simulator supplies the modeled environment. SITL is convenient for debugging and repeated testing; HITL adds the actual controller hardware, but does not automatically reproduce every aspect of real flight. [16] · [17]

### ArduPilot

**Core software features.** ArduPilot is a broad autonomous-vehicle software family rather than a multicopter-only controller. Its vehicle implementations include Copter, Plane, Rover, Sub and AntennaTracker, with shared libraries for sensor drivers, attitude and position estimation, and control. This makes it attractive when a project may expand beyond one aircraft type or requires substantial mission and peripheral functionality. [1] · [18]

**RTOS and execution model.** The mainstream embedded baseline is **ChibiOS on STM32-based flight controllers**. ArduPilot also has a Linux hardware-abstraction layer, and its ESP32 development port uses FreeRTOS. The operating environment is therefore target-specific: “ArduPilot uses ChibiOS” is a useful short answer for common embedded boards, but not a universal statement about every ArduPilot build. [18] · [19]

**Older NuttX references are historical.** ArduPilot previously used NuttX on relevant hardware, but its move to ChibiOS was already the subject of a developer presentation in 2018. This explains why older material can associate both ArduPilot and PX4 with NuttX even though their common embedded configurations differed by the end of 2024. The presentation documents the architectural transition, not a controlled performance ranking between the projects. [20]

**Core programming language.** ArduPilot’s main flight code is primarily **C++**. Python is common in its supporting tools, but that does not make Python the language implementing the onboard stabilization and navigation core. For substantial changes to flight behavior, estimators or hardware drivers, C++ is the relevant development skill. [1]

**Scripting and secondary development.** **Lua provides onboard scripting**, while Python supports ground-side tools and external control applications. Lua scripts can add behaviors without modifying the compiled flight core; they run in a sandbox and can access vehicle state and selected control interfaces. Python-based external applications communicate with the autopilot rather than execute as ordinary Python programs inside the microcontroller’s flight firmware. [21] · [1]

**Lua has an important timing boundary.** Scripts run at low priority and receive bounded execution opportunities so that a long-running script does not simply block the main flight code. However, the scripting documentation explicitly says callbacks do not have a guaranteed reliable schedule. Lua is therefore a good fit for supervisory behavior, payload actions and custom automation—not a substitute for implementing a tightly timed inner flight-control loop in the core firmware. [21]

**Hardware determines scripting availability.** The documented scripting setup calls for at least 2 MB of flash and 80 kB of memory, normally with script storage on an SD card. F4-based autopilots are explicitly excluded from the documented Lua capability. This distinction matters when buying a controller: a board capable of running ArduPilot flight firmware is not necessarily capable of running the additional scripts your project requires. [21]

**Communication protocols and roles.** **MAVLink is the principal ground-station and companion-computer interface**. It carries telemetry, commands, mission exchanges and other vehicle-management messages. **DroneCAN**, operating over a CAN bus, serves a different role: communication with distributed peripherals and components. The two are complementary rather than competing alternatives for the same connection. [22] · [18]

**Software license and exceptions.** ArduPilot’s flight software uses **GNU GPL version 3**, with its porting documentation referring to GPLv3-or-later requirements for firmware customization. This is the license of the ArduPilot code, not a claim that every bundled library, external tool or hardware design has an identical license. The project also explicitly allows separate proprietary higher-level software on a companion computer. [23] · [24]

**Practical selection judgment.** ArduPilot is a strong starting point when the vehicle must execute autonomous missions and interact with varied sensors, payloads or vehicle types. Its main trade-off is the breadth of configuration and the need to match optional capabilities to the selected controller. If your central requirement becomes a native ROS 2 development workflow or tightly integrated Simulink deployment, PX4 becomes the more direct comparison.

**Takeaway: choose ArduPilot for broad vehicle autonomy, especially when onboard Lua and MAVLink-based integration are useful.**

**Additional documented evidence**

**Technical profile**

**Supported result (public evidence through 2024-12-31):** ArduPilot’s core flight code is primarily **C++**, and its core project license is **GNU GPL version 3 or later** [52]. Its execution environment is target-dependent: embedded firmware uses documented **ChibiOS or NuttX** options, while Linux-based boards use **Linux rather than a traditional RTOS** (real-time operating system) [49][57]. Its clearest differentiator is breadth: the 2024 development documentation names multicopters, traditional helicopters, fixed-wing aircraft, rovers, submarines and antenna trackers, with many controller, sensor and frame options [52]. ArduPilot is therefore a strong conditional shortlist for varied vehicles, autonomous missions and integration-heavy research, but not a universal winner.

| ArduPilot field | Answer at the 2024-12-31 snapshot |
|---|---|
| **RTOS / execution model** | **Target-dependent:** ChibiOS and NuttX are documented embedded operating-system choices. Linux-based autopilots run on Linux, not a traditional RTOS. The Mission Planner workflow describes ChibiOS as newer and more efficient but with some missing features, and NuttX as older; this should not be reduced to one project-wide runtime [49][57]. |
| **Core programming language** | **C++:** ArduPilot’s main flight code is written in C++; supporting tools use several languages, commonly Python [52]. |
| **Scripting languages** | **Lua 5.3.6** is the documented onboard scripting language. Lua scripts run in a sandbox alongside the flight code, can execute MAVLink commands and communicate with DroneCAN peripherals, and are normally loaded from the vehicle’s scripts directory [62][150]. Mission Planner also supports **external Python 2.x up to Python 2.7 through IronPython**, but that is ground-station scripting rather than onboard flight-firmware scripting [49]. Lua availability is hardware-dependent: F4-based boards do not support it, and normal use requires suitable flash, memory and storage [62][150]. |
| **Primary communication protocols** | **MAVLink** is the principal ground-station, telemetry, command and peripheral protocol. **DroneCAN** provides reliable component communication over CAN. USB, telemetry radio, IP networking and UART are connection methods or interfaces rather than alternative primary flight protocols [52][57][130]. |
| **Core software license** | **GNU GPLv3-or-later** for the ArduPilot software identified in the development documentation [52]. A material component distinction is that vendored Lua, excluding its modifications, is identified as **MIT-licensed** [62]. A 2021 comparison summarizes the GPLv3 consequence for distributed modified firmware as source disclosure and same-license distribution; this should be treated as project-planning guidance, not legal advice [112]. |

**Decision-relevant strengths and limits**

ArduPilot’s hardware breadth is useful but creates board-selection work. Its documentation identifies support for redundant inertial measurement units (IMUs) and GPS receivers, UART connections for telemetry, GPS and companion computers, I2C/CAN expansion, and IMU heaters for harsh or highly variable temperatures [57]. Linux boards generally provide more processing power and memory for advanced control or navigation experimentation, but may lack DShot, bidirectional DShot, BLHeli passthrough, some GPIO features and easy ground-station uploading. Flash-limited F4 and other boards may also omit features; a custom build can exchange unused features for required ones [57]. Not every listed board has been directly tested or endorsed by the development team [128]. Thus, the correct question is not only “Is ArduPilot suitable?” but also “Which ArduPilot target preserves the features this vehicle needs?”

The extension and integration path is substantial. ArduPilot’s documentation lists companion-computer platforms and tools including Raspberry Pi, BlueOS, DroneKit, MAVSDK, pymavlink and Rpanion, as well as Robot Operating System (ROS) 1 and ROS 2, MATLAB/Simulink, Software-in-the-Loop (SITL) and Hardware-in-the-Loop (HITL) workflows [52]. A supplied `ardupilot_ros` record documents ROS 2 Humble, Gazebo Garden, Cartographer ROS and a simple ROS 2 viewing/control GUI, but also reports no published releases; this is a documented integration route whose maintenance and version compatibility should be checked rather than assumed [116].

Simulation evidence is particularly relevant for research and testing. ArduPilot’s development documentation lists SITL setup, vehicle-specific simulations, MATLAB/Simulink resources and HITL options involving X-Plane and FlightGear [52]. A dataset published on **15 January 2024** used ArduCopter SITL to generate **70 autonomous-flight records covering more than 7 hours**, with MAVLink control through Mission Planner/MAVProxy, MATLAB files for analysis, and an obstacle-avoidance site-surveillance example [127]. In one simulated GPS-failure test, `SIM_GPS_DISABLE 1` changed the GPS status flag from 6 to 1, after which ArduCopter entered a failsafe land mode and landed vertically at its current position [127]. These are useful research and fault-testing mechanisms, not proof of real-world safety: the dataset was SITL-only, and its authors caution that simulated, ArduPilot-specific results may not generalize to actual flights or other autopilots [127].

**Plain-language implication:** put ArduPilot near the top of the shortlist when the project may involve helicopters, boats, rovers, unusual or multiple airframes, broad hardware/peripheral support, autonomous waypoint or survey missions, onboard Lua extensions, companion computers, ROS or simulation-based development [49][52]. Its trade-off is depth: a comparison describes more vehicle-specific features, parameters and previously handled edge cases, but a codebase that is harder for a newcomer to modify safely and therefore more favorable to teams that configure rather than fork [124]. For a non-expert, ArduPilot is best understood as a flexible, feature-rich starting point; confirm the exact board, memory, scripting requirements, integration versions and GPL implications before making the final choice.

ArduPilot (2024-12-31): MAVLink carries GCS telemetry, missions, commands and companion links [113][151]. Core license: GPLv3 [51]. Companion/ROS 2 support, MATLAB/Simulink, and SITL are documented; HITL is conditional [137][158][163][162]. Fits research, autonomy, mapping and inspection conditionally [115][120].

ArduPilot: Runtime is target-dependent—ChibiOS/NuttX on supported boards; Linux variants aid algorithm development but omit some hardware features [132][160]. Core C/C++, Lua scripting, GPLv3 [143][142][118]. Telemetry: MAVLink2 (MAVLink1 legacy; High Latency satellite/low-bandwidth); MSP is sensor/telemetry-only [142][144]. Companion computers use MAVLink for control/vision [161]; ROS uses MAVROS, with ROS2 still improving [147]. MATLAB/Simulink JSON/SITL is documented; HITL is not established [166]. Conditional fit: autonomous/research or repeatable multicopter work; verify airframe, board, mission and safety constraints [142][146].

code:rejected;reason:number_unsupported;allowed_numbers:["","14855 port","ArduPilot 2.0","2018b","115200 baudrate","42.841448,24.770727,0.5,0","2022","0.12","2024"];allowed_citations:[109],[110],[111],[112],[113],[114],[115],[116],[117],[51],[52],[119],[62],[120],[121],[122],[123],[124],[125],[126],[127],[128],[129],[130],[131],[133],[134],[135],[136],[137],[138],[139],[140],[141],[142],,[87],[89],[145],[148],[149],[150],[151],[152],[153],[154],[155],[156],[157],[158],[159],[162],[163],[164],[165],[166],[167],[168],[169],[170],[171];allowed_entities:["ArduPilot"]

For a non-expert, the main trade-off is breadth versus simplicity: in the direct PX4 comparison, ArduPilot is described as having a larger community, broader platform support, and more documentation, but no numerical margin is reported [115]; its deeper feature and parameter base supports unusual vehicles and advanced missions while making safe modification and setup harder [124][134]. The integration trade-off is similarly conditional: MAVROS is more documented than PX4’s route but translates MAVLink to ROS, whereas PX4’s uXRCE-DDS is native [121]; ROS 2 support is still improving, APSync is deprecated, and flash limits can remove features on some boards [158][154][128].

The clearest uncertainty-reducing distinction is breadth: ArduPilot spans multicopters, helicopters, fixed-wing aircraft, rovers, boats, submarines, and other vehicle classes, while supporting many flight controllers, sensors, and frames [109][52]. An undecided user can therefore defer the mission and hardware choice, then select matching Copter, Plane, Rover, or Sub firmware and the required autopilot and peripheral hardware [111].

Plain-language recommendation: shortlist ArduPilot when you need broad vehicle coverage, autonomous missions, community help, companion-computer extensions, or simulation-based learning and testing; these are supported by its flexible firmware, MAVLink ecosystem, ROS resources, and SITL workflows [111][154][151][157][113]. Do not treat it as a universal winner: GPLv3 may require sharing core modifications, open-source systems have a steeper learning curve, ROS 2 support is still improving, APSync is deprecated, and SITL evidence may not generalize to real operations; check the project’s mission, vehicle, hardware, and licensing needs before choosing [122][125][158][154][127].

### PX4

**Core software features.** PX4 is a modular flight-control stack supporting multirotors, fixed-wing aircraft, vertical-takeoff-and-landing aircraft—usually abbreviated VTOL—and other unmanned vehicles. It separates estimation and control functions into modules connected by an internal messaging system. This structure is particularly useful when researchers or product developers want to replace one algorithm without reorganizing the entire stack. [2] · [25]

**RTOS and execution model.** **NuttX is PX4’s principal embedded RTOS** on conventional flight-controller boards. PX4 also runs in environments providing a POSIX-style operating-system interface, including Linux and macOS, with other platform-specific possibilities such as QuRT. Desktop execution is especially important for simulation; it should not be confused with running a desktop operating system on every flight controller. [2]

**Modularity depends on message exchange.** PX4 modules communicate through **uORB**, an internal publish/subscribe bus. A module publishes information such as an estimated position, and interested modules subscribe to it. The internal bus uses shared memory; it is not itself the same thing as an external ROS 2 network connection. PX4’s middleware provides the bridge between these internal software components and external systems. [2]

**Core programming language.** PX4’s core development is primarily **C++**, with C also present in lower-level and supporting code. Its contribution documentation uses the Google C++ style guide as its baseline. For a developer planning to replace an estimator, controller or firmware module, C++ is the principal implementation language to learn. [26]

**Scripting and secondary development.** **Python is an external application option through MAVSDK or ROS tooling**, while shell scripts are used for startup and module configuration. These should not be mistaken for an ArduPilot-style onboard Lua application environment. PX4’s main extension choices are compiled firmware modules or external programs using its robotics and vehicle APIs. [27] · [2]

**External control is a deliberate design path.** A companion computer can receive vehicle data and send higher-level commands while PX4 continues to run flight-control functions. PX4’s documentation identifies MAVSDK and ROS 2 as high-level communication approaches. This is useful when a project needs substantial computing power for perception or planning, but it also makes the behavior of the link and the external application part of the system design. [27]

**Communication protocols and roles.** **MAVLink** is the principal interface for ground stations such as QGroundControl and for many companion-computer applications. **DDS/ROS 2 communication through uXRCE-DDS** provides a robotics-oriented route to selected PX4 topics. **uORB** remains the internal message bus. For actuator and peripheral integration, the supported interface depends on the board and configuration; MathWorks’ 2024 PX4 tooling, for example, explicitly supports PWM and UAVCAN actuator output. [27] · PX4 v1.14 DDS bridge [15] · [28]

**ROS 2 integration advanced before 2025.** PX4 v1.14 replaced the previous MicroRTPS bridge with uXRCE-DDS and aligned the message definitions used for internal and ROS 2 topics. PX4 v1.15 then introduced an experimental C++ ROS 2 Interface Library for higher-level control and sensor access. The first is an architectural integration path; the second carried an explicit experimental qualification. [15] · [29]

**Software license and exceptions.** PX4 flight-stack and middleware code use the **BSD 3-Clause license**, a permissive license allowing incorporation into proprietary products subject to its conditions. Related materials differ: PX4’s license page lists Pixhawk hardware under CC BY-SA 3.0 and the user guide under CC BY 4.0. The permissive flight-software license therefore does not erase separate hardware, documentation or third-party obligations. [30] · [31]

**Practical selection judgment.** PX4 is especially attractive when the drone is part of a larger robotics system, when algorithms will be developed in modules, or when MATLAB/Simulink deployment is central. Its trade-off is version coordination across firmware, message definitions, ROS software and simulator tooling. If the project mainly needs existing vehicle functionality plus lightweight onboard customization, ArduPilot may offer a more direct route.

**Takeaway: choose PX4 when robotics interfaces, modular algorithm development and model-based tooling dominate the project.**

**Additional documented evidence**

**PX4 technical profile at the 2024-12-31 cutoff**

| Requested field | PX4 answer |
|---|---|
| **RTOS / execution model** | **PX4:** NuttX is the primary real-time operating system (RTOS) on flight-control boards. PX4 also has POSIX-based builds for environments such as Linux, macOS and QuRT; its software-in-the-loop (SITL) build can run on POSIX, while Linux on a companion computer is a separate computing layer rather than the flight-controller runtime. [54][173][91] |
| **Core programming language** | **PX4:** the flight-control core is primarily **C/C++**. An older code study describes 25 kloc of C/C++ application code and 25 kloc of C/C++ platform-support code; this is composition evidence, not a current code-size estimate. PX4’s C++ style guide and `.cpp` source files corroborate C++ in the core. [58][206] |
| **Scripting / secondary control** | **PX4:** no cutoff-verified onboard scripting language is established here. PX4 does document external control through MAVLink, MAVSDK and ROS 2, but a language used by a ground station or companion computer should not be mislabeled as an onboard scripting runtime. [173][172] |
| **Primary communication protocols** | **PX4:** **MAVLink** is the principal ground-station, telemetry and command protocol; QGroundControl communicates through a bidirectional telemetry link. Internally, PX4 modules use **uORB**, a publish–subscribe message bus. **DDS/ROS 2** mechanisms provide additional companion-computer and robotics integration. [173][54][178] |
| **Core software license** | **PX4:** the core source is licensed under the **BSD 3-Clause** license, allowing use, modification and redistribution. PX4’s contribution rules also require the BSD 3-Clause license. A separate PX4 v1.14.3 Zenodo release record was published on 24 May 2024, but its CC BY 4.0 license applies to that record—not to the core repository. [178][206][175] |

The language boundary matters: PX4’s repository also contains CMake, Python, MATLAB and shell tooling, but those auxiliary languages do not change the answer for the flight-control core. Similarly, the repository’s mention of MATLAB does not by itself establish MATLAB/Simulink blocks, a toolbox, or code-generation support. A direct MATLAB/Simulink integration path therefore remains **not established** by the cutoff-safe evidence used here; it should not be inferred from a repository language listing. [172][178]

**Why PX4 is different**

PX4’s clearest differentiator is its layered architecture. The **flight stack** contains estimation, guidance and control algorithms for fixed-wing, multirotor and vertical-takeoff-and-landing (VTOL) aircraft; the **middleware** supplies hardware drivers, external communications, the uORB message bus and simulation facilities. This separation makes it comparatively natural to replace an estimator or controller without redesigning unrelated modules. [54][172]

That architecture gives PX4 broad conditional scope: documented support includes multirotors, fixed-wing aircraft, VTOLs and rovers, with examples ranging from racing quads to industrial survey aircraft. Other frames—including helicopters, airships, boats and submarines—are described as having basic support but not necessarily inclusion in the regular flight-test programme. [173][178] The breadth is therefore useful, but “supported” should not be read as “equally mature for every vehicle.”

PX4 also has a documented companion-computer model. A companion computer is a separate onboard computer that provides higher-level command and control or computationally demanding functions such as computer vision and collision prevention. It commonly runs Linux and connects to the flight controller through serial, Ethernet or Wi‑Fi, using interfaces such as MAVLink, MAVSDK or ROS 2. [173] Dedicated Pixhawk flight controllers are not generally intended for general-purpose computing; PX4 documentation presents a separate companion computer or dedicated digital-signal processor as the usual solution. Native Raspberry Pi operation is described as less robust than those alternatives. [204]

ROS 2 therefore strengthens PX4 mainly when the project can accommodate a companion computer and the associated integration work. The benefit is access to robotics software and higher-level control; the limitation is that the project must manage an additional computer, link, software stack and version compatibility rather than treating ROS 2 as a script running directly inside the flight controller. [173][54]

**Simulation and application implications**

PX4 documents both **SITL**—running flight software against a computer-modeled vehicle—and **hardware-in-the-loop (HITL)** testing. Its architecture includes a desktop simulation layer, and the project summary describes comprehensive SITL, HITL and log-analysis tooling; it also provides a Docker-based, single-command SITL workflow. Exact simulator, board and workflow support remains target- and version-dependent. [54][174][91]

These features make PX4 a plausible choice for research, education, controller validation and development before flight. They also fit camera-equipped multirotors, fixed-wing mapping or survey aircraft, VTOL projects requiring both hovering and forward flight, and applications using companion-computer perception or autonomy. A Pixhawk 4 profile, for example, explicitly identifies academic and commercial developers and lists multicopters, airplanes, rovers and boats, but that evidence is target-specific rather than a guarantee for every PX4 board. [173][177][191]

**Decision implication:** shortlist PX4 when the project values broad vehicle and hardware coverage, a modular C/C++ flight stack, companion-computer or ROS 2 integration, and repeatable simulation/testing. Do not select it solely because it is broadly capable: verify the exact flight-controller board, airframe, mission, safety requirements, companion-computer cost and power budget, and the team’s ability to maintain the surrounding robotics software. PX4’s uncertainty-reducing distinction is its integration-oriented, modular architecture; its corresponding trade-off is greater system and hardware-selection complexity than a minimal flight-controller firmware. [173][204][178]

PX4 (2024-12-31): NuttX is the primary RTOS; Linux/macOS/QuRT are documented; core language C/C++ [192]. PX4: no onboard scripting language is established in the evidence; external MAVSDK control supports C++, Python, Java and Swift via companion computer/GCS [86]. PX4: MAVLink is principal for GCS/telemetry/peripherals; uORB is internal and ROS 2 uses FastRTPS [179][181]. PX4: core license BSD 3-Clause; documentation CC BY 4.0 [189]. PX4 suits research, autonomy and varied airframes; companion-computer, MATLAB/Simulink SIL/HIL and Gazebo/JMAVSim workflows [181][196][192] matter, but hardware/network/compute needs decide [176].

PX4 v1.15 documents MAVLink: ground stations use UDP port 14550, offboard APIs 14540, and simulators TCP port 4560; Gazebo instead uses its own API [203]. ROS 2 uses uXRCE-DDS and ROS 1 MAVROS [93][201]. PX4 supports companion-computer workflows and SITL/HITL with lockstep testing [203].

PX4 uses MAVLink for GCS and uXRCE-DDS for ROS 2/mission links [184][185]; code is BSD-3-Clause [94]. PX4's ROS 2 path is Linux-only and needs PX4-architecture know-how [200]. PX4's Simulink SIL/HIL support [209] fits waypoint, survey, payload and research work conditionally; check hardware/version [183][205].

PX4: NuttX/C/C++; MAVLink/uORB; BSD-3-Clause [194]. Python: external ROS 2 offboard control [199]. ROS 2/DDS-RTPS bridges uORB through matched agents [187]; offboard needs 2-Hz proof-of-life [186]. SITL/HITL are documented [194]; Simulink codegen is HIL-limited [180]. Best fit: ROS/autonomy work [186].

At the report cutoff, PX4 is conditionally suitable for broad-vehicle, companion-computer, ROS 2/DDS, and simulation work: flight control runs on NuttX, MAVLink is primary (UDP 14550 for ground stations, UDP 14540 for offboard APIs, TCP 4560 for the simulator), and a companion computer usually runs Linux [54][92][182][202][207][195]. PX4 therefore fits research/education, waypoint and survey missions, computer-vision/object-avoidance, and multi-vehicle testing; its companion-computer and SITL/HITL support are Strong, ROS integration is Moderate, and beginner configuration complexity plus missing `pwm_out_sim` in some firmware are material caveats [56][212][203][197][207][188][211].

PX4’s main trade-off is Strong companion-computer support versus Moderate ROS integration: MAVLink/uXRCE-DDS connects separate computers for intensive applications, but ROS 2 over XRCE-DDS requires PX4-convention knowledge, officially supports only Linux, and has an interface that is not stable across releases [197][207][200]. Thus PX4 is better aligned with high-performance, broad-airframe developer work than beginner simplicity, while its unauthenticated, unsigned and unencrypted default interfaces leave hardening to the integrator [188][195][193][198].

PX4’s clearest uncertainty-reducing distinction is its layered split: NuttX on the flight controller handles core flight and safety, while a usually Linux companion computer handles general or computationally intensive applications over MAVLink/uXRCE-DDS [92][197][204]. For a non-expert, this marks PX4 as developer/integration-oriented, with broad airframe coverage and documented computer-vision, new-hardware and custom-flight-mode paths, while advanced workloads normally sit on the companion [193][195][207][204].

Plainly, PX4 is a conditional choice when Strong companion-computer and Strong SITL/HITL support matter for research, computer vision, object avoidance or multi-vehicle testing; its high-performance flexibility is less beginner-friendly because configuration is complex and ROS 2 is officially Linux-only, requires PX4-specific understanding, and has an unstable cross-release interface [197][56][188][200][207]. Before committing, verify the board and workflow: HITL may require a Pixhawk Series controller and may lack `pwm_out_sim` in default firmware, while community simulator compatibility is not assured across current versions [190][210][208].

### Paparazzi

**Core software features.** Paparazzi is a complete unmanned-aircraft system encompassing airborne software, mission planning, monitoring and bidirectional communications. Its supported configurations extend beyond conventional fixed-wing aircraft to rotorcraft, hybrids, gliders and other experimental vehicles. Its long-standing research orientation is reflected in its configurable architecture and its use by universities as well as hobbyists and companies. [3] · [32]

**RTOS and execution model.** Paparazzi has **target-specific execution paths**. ChibiOS provides an RTOS kernel and hardware abstraction on relevant embedded targets. Older libopencm3-based configurations use a bare-metal implementation without threads. Linux supports desktop simulation and some aircraft platforms, including documented Parrot Bebop configurations. Naming ChibiOS alone would therefore omit a material part of the architecture. [7]

**Core programming language.** The airborne autopilot is primarily **C**. The wider system also uses languages including OCaml and Python for ground software, tools and interfaces. Paparazzi’s module-generation system produces C code for module calls and static scheduling, connecting the configuration system directly to the compiled flight implementation. [32]

**Configuration is part of development.** Aircraft configuration is distributed across XML descriptions for the airframe, flight plan, radio and telemetry. During compilation, the module system determines dependencies and task ordering. This provides substantial control over a custom vehicle, but it is a different experience from selecting a few options in a general-purpose configurator. [7]

**Scripting and secondary development.** **Python is the clearest scripting interface** for external monitoring, ground tools and control through PPRZLINK. C/C++ and OCaml interfaces are also relevant, although those are not all scripting languages in the usual sense. A custom onboard feature can instead be implemented as a compiled autopilot module. [33] · [34]

**Several extension layers are supported.** Paparazzi documents four approaches: extend the existing ground tools, use PPRZLINK independently, add a dedicated onboard computer or board, or add a module directly to the autopilot. These options can be combined. For example, a ground-side Python application can monitor position and battery data while a compiled onboard module handles a custom sensor. [33]

**Communication protocols and roles.** **PPRZLINK** is the principal aircraft/system messaging toolkit, including telemetry from aircraft to ground and datalink messages in the opposite direction. **Ivy** connects ground-side programs through a publish/subscribe software bus. A separate onboard computer can communicate directly with the autopilot through PPRZLINK, commonly using serial transport. [34] · [7]

**The ground system is distributed.** Paparazzi’s Link program handles aircraft communications, its Server maintains aircraft state, and the GCS provides the user-facing controls. These programs may run together on one laptop or be distributed across networked computers. That is useful for research involving customized displays or multiple cooperating tools, but it introduces Paparazzi-specific concepts that a newcomer must learn. [7]

**Software license and exceptions.** Paparazzi uses the **GNU GPL family, principally GPLv2-or-later for its main software**, with important component-level distinctions. PPRZLINK’s C and OCaml libraries use GPLv2-or-later, its generators use GPLv3-or-later, and its Python library uses LGPLv3-or-later. Ivy is separately described as LGPL software. These components should not be collapsed into one indiscriminate license label. [3] · PPRZLINK component licenses [34] · [7]

**Practical selection judgment.** Paparazzi is a strong candidate when the research includes the aircraft architecture, control system, mission representation or ground interface itself. Its main trade-off is that broad compatibility with MAVLink-centered or ROS-centered workflows is not its organizing principle. Existing Paparazzi expertise, a suitable aircraft configuration or a need for its complete configurable system can outweigh that integration cost.

**Takeaway: choose Paparazzi when custom UAS development is central and adopting its integrated toolchain is an advantage.**

### LibrePilot

**Core software features.** LibrePilot focuses on vehicle control, stabilization, autonomous vehicles and robotics. It includes flight software, ground software and related hardware resources, reflecting its roots in OpenPilot. Its appeal is an integrated control platform rather than a narrowly defined racing controller or a ROS-first robotics stack. [4]

**RTOS and execution model.** LibrePilot’s conventional embedded flight architecture is **FreeRTOS-based**, with platform-specific hardware support around the flight firmware. It should not be grouped with PX4’s NuttX implementation or ArduPilot’s common ChibiOS implementation merely because some boards look similar or serve similar aircraft. Hardware support and firmware architecture are separate selection questions. [4]

**Core programming language.** The embedded flight firmware is primarily **C**, while the ground-control application and associated desktop components use substantial **C++**. For this question, C is the most useful answer for the flight core; “C/C++” describes the broader flight-and-ground system. Changing a desktop configuration interface and changing an onboard stabilization algorithm therefore involve different parts of the codebase. [4]

**Scripting and secondary development.** LibrePilot’s optional **PicoC** facility provides interpreted C-like scripting on builds that include it. Python is relevant to external utilities and object-oriented data access rather than as a general Python interpreter inside the flight controller. PicoC support is a build-dependent extension capability, so it should not be assumed to appear on every resource-constrained controller. [4]

**PicoC differs from Lua.** Both can reduce the need to rebuild all flight firmware for a small behavior change, but PicoC uses a C-like programming model. ArduPilot’s Lua environment has a more explicitly documented application-scripting workflow, including sandboxing, scheduling and hardware requirements. For a non-expert whose principal development goal is onboard scripting, ArduPilot’s documented Lua route is the more straightforward comparison.

**Communication protocols and roles.** **UAVTalk** is the principal flight-controller/ground-system protocol, organized around **UAVObjects**: structured representations of settings and vehicle data. External integration therefore means understanding those objects and their message exchange, rather than assuming MAVLink mission and parameter services. Receiver, sensor and actuator connections remain board- and configuration-dependent interfaces alongside that ground link. [4]

**Object definitions shape integration.** An object-based model is useful when a ground application and flight firmware share structured data definitions. The trade-off is that a custom companion application must work with that schema and protocol. A MAVLink application written for ArduPilot or PX4 does not become a LibrePilot application simply by changing the serial-port name.

**Software license and exceptions.** LibrePilot source code uses **GNU GPLv3**, with the project’s license file directing readers to source headers for minor exceptions. Artwork uses CC BY-SA 3.0. Its inherited OpenPilot notices also distinguish documentation and hardware, including some hardware files under the noncommercial CC BY-NC-SA 3.0 license. The noncommercial condition applies to those particular hardware materials, not to GPL flight software as a whole. [35] · [36]

**Practical selection judgment.** LibrePilot is most attractive when an existing controller, codebase, vehicle or teaching setup already uses its architecture. Its strength is the opportunity to build on an integrated control system; its trade-off for a new robotics project is the greater likelihood of protocol-specific integration work. That is a project-fit judgment, not a claim that stabilization quality can be ranked from the software’s name or license.

**Takeaway: choose LibrePilot when its existing flight/ground architecture and hardware fit are assets you can reuse.**

### Betaflight

**Core software features.** Betaflight is principally a pilot-oriented flight-control system, especially associated with FPV racing and freestyle. Its software emphasizes responsive stabilization, gyro filtering, controller tuning, flight logging, on-screen displays and RC peripherals. The 4.5.0 release includes concrete racing and piloting features such as a GPS lap timer, control-mode improvements and extensive GPS Rescue changes. [5] · [37]

**RTOS and execution model.** Betaflight’s conventional microcontroller firmware uses **its own scheduler rather than a traditional RTOS such as ChibiOS or NuttX**. Time-critical gyro, filtering and control work receives particular scheduling treatment. This is a purpose-built embedded scheduling design, not evidence that the firmware lacks real-time requirements. [8]

**Core programming language.** The flight-controller firmware is primarily **C**. Betaflight’s tests can be written in C++ and linked against the C firmware, but that does not make C++ the principal flight-core language. Similarly, the implementation language of the desktop configurator is a separate matter. [38] · [39]

**Scripting and secondary development.** Betaflight’s ordinary firmware is **not a general-purpose onboard Lua or Python application runtime**. Lua is relevant to compatible transmitter-side configuration tools, while an external program—including a Python program—can communicate through MSP. These are secondary interfaces around the controller, not a promise that arbitrary scripts execute inside its flight loop. [40] · [5]

**Configuration is not general autonomy.** A transmitter script that adjusts settings and an external program that sends RC channel commands are both useful, but neither automatically provides mission planning, navigation-state management or high-level robot behavior. Betaflight 4.5.0’s release notes do establish MSP override work, providing a pre-2025 basis for external channel-level interaction. That is a narrower interface than a complete autonomous-vehicle API. [37]

**Communication protocols and roles.** **MSP—the MultiWii Serial Protocol—is the principal configuration and tool interface**. For other components, **DShot** communicates motor commands from the flight controller to electronic speed controllers, or ESCs. Receiver interfaces include protocols such as **CRSF** and **SBus**, while telemetry includes CRSF, FrSky/SmartPort, HoTT and MSP-related paths. These protocols serve distinct jobs rather than representing competing ground-station options. [40] · Betaflight peripheral protocols [5] · [41]

**GPS Rescue is a different capability.** Rescue functionality helps address a specific flight-recovery problem. It should not be treated as equivalent to the waypoint mission, payload coordination and companion-computer workflows central to general-purpose autonomous stacks. The relevant 2024 release documents rescue improvements, but the decision to choose Betaflight should still begin with its piloting-oriented purpose. [37]

**Software license and exceptions.** Betaflight firmware uses **GNU GPL version 3 or later**. Its core source headers state that license explicitly. Third-party code retains its own applicable notices; no project-wide exception is assumed here that would convert the GPL firmware into permissively licensed proprietary flight code. [38]

**Practical selection judgment.** Betaflight is the natural first candidate when the aircraft is mainly flown by a pilot and the project prioritizes racing, freestyle or precise RC handling. Its trade-off is architectural fit when the main task becomes a robot executing complex autonomous missions. If navigation modes and waypoint flying are central but the project remains an RC-oriented build, iNAV is the closer specialist alternative.

**Takeaway: choose Betaflight for the flying experience and control workflow of a piloted FPV aircraft.**

### iNAV

**Core software features.** iNAV is a navigation-oriented flight-control system offering position hold, altitude hold, return-to-home and waypoint missions. It supports multirotors and fixed-wing aircraft, with configurable mixing also extending to other vehicles. Its distinguishing role is to combine RC-oriented setup and piloting with substantial onboard navigation. [6]

**RTOS and execution model.** iNAV’s conventional embedded firmware runs **without a traditional RTOS**, using an in-firmware scheduler and interrupt-driven hardware support. It is therefore closer to the dedicated scheduling approach of the Cleanflight-derived flight-controller family than to PX4’s NuttX environment. The absence of a general RTOS does not remove the need to coordinate navigation, sensor processing and stabilization carefully. [6]

**Core programming language.** The core flight firmware is primarily **C**. The configurator, supporting utilities and programming frontends are separate software layers; their use of other languages does not change the implementation language of the flight-control core. [6] · [42]

**Scripting and secondary development.** The practical onboard customization baseline is the **INAV Programming Framework**, using logic conditions, global variables and configurable control functions through the configurator or command-line interface. It is not equivalent to embedding a general-purpose Python or Lua interpreter. **Lua can be used externally in compatible transmitter/telemetry arrangements**; that code runs on the radio rather than in iNAV’s stabilization firmware. [43] · [13]

**Logic programming has concrete limits.** The framework can combine conditions involving switches, altitude, distance, timers and other flight information, then use the result in mixes or selected overrides. It uses integer arithmetic, so fractional results require deliberate scaling: the documentation’s example shows that dividing 1 by 3 produces 0 after truncation. This is useful embedded customization, but it is not a substitute for a full numerical-computing environment. [43]

**Communication protocols and roles.** **MSP is iNAV’s native configuration, mission and monitoring protocol**. **LTM**, or Light Telemetry, provides a lightweight flight-data stream; other telemetry paths include SmartPort, FPort, CRSF and a MAVLink subset. For GPS component communication, the 7.1.0 release requires the UBLOX protocol rather than NMEA. [13] · [44]

**MAVLink does not imply full interchangeability.** The historical iNAV mission guide describes MAVLink as a limited monitoring interface, with MSP used for mission management. Therefore, selecting a ground station solely because it understands MAVLink is not a sufficient interoperability test. An iNAV-oriented tool such as mwp addresses a different set of configuration and mission expectations from a general ArduPilot or PX4 application. [13]

**Navigation features have hardware prerequisites.** INAV 7.1 made multirotor navigation without a compass possible, but still recommended a compass for better sustained position holding and reduced heading drift. Without one, the listed navigation modes depend on first acquiring a valid GPS-derived heading. “Compass optional” consequently does not mean “navigation is immediately ready under every takeoff condition.” [44]

**Fixed-wing capability is a distinguishing strength.** Version 7.1 added advanced fixed-wing automatic landing, including landing at a Safehome after return-to-home or at a designated LAND waypoint. The same release also warned that the INAV 7 series was the final official series for F411-based controllers. These are practical reasons to choose the firmware and the hardware together rather than independently. [44]

**Software license and exceptions.** iNAV firmware uses **GNU GPL version 3 or later**. This describes the firmware’s licensing baseline; supporting applications and third-party components retain their own notices. No blanket exception is assumed that changes the flight firmware into BSD-licensed software. [6]

**Practical selection judgment.** iNAV is a strong specialist choice for an RC aircraft that needs dependable navigation functions without adopting a broad robotics software architecture. Its trade-off is that companion-computer and external-tool integration should be designed around its actual MSP-oriented interfaces. If the main requirement becomes intensive ROS integration, computer vision or a custom autonomous software stack, ArduPilot and PX4 become stronger starting points.

**Takeaway: choose iNAV when navigation is central to an RC-style multirotor or fixed-wing project.**

### What the technical differences mean for development

**The extension layer often decides.** For a non-expert, the most important development question is usually not “Which core language is best?” but “How much of the core must I change?” A small custom payload behavior, a new flight-control algorithm and a computer-vision mission planner belong at different software layers.

| Development layer | Typical task | Suitable examples | Main responsibility |
|---|---|---|---|
| Inside flight firmware | New estimator, driver or control law | C/C++ modules in the autopilot | Timing, memory and flight-code correctness |
| Onboard extension logic | Payload action or conditional behavior | ArduPilot Lua; iNAV logic; optional LibrePilot PicoC | Respect the extension environment’s limits |
| External computer/application | Vision, planning or custom operator tools | MAVLink/MAVSDK, ROS, PPRZLINK or UAVTalk clients | Communications, command authority and failure behavior |

**Onboard scripts minimize some changes.** ArduPilot’s Lua interface is especially useful when the required behavior already fits its exposed APIs. iNAV’s logic framework can be sufficient for conditional switching or mixing, while Paparazzi’s generated configuration and compiled modules offer deeper structural control. The distinction is between using an existing extension surface and changing the flight system itself—not simply choosing a familiar language. [21] · iNAV programming [43] · [33]

**External computers move the integration boundary.** A companion application can perform work that is unsuitable for a small flight microcontroller, but it must communicate through the selected protocol and control interface. PX4’s ROS/MAVSDK paths, ArduPilot’s MAVLink path and Paparazzi’s PPRZLINK path make different assumptions about the external application. A protocol adapter may solve message translation while still leaving vehicle modes, units and command semantics to be handled correctly.

**RTOS choice is usually secondary.** Unless you are porting firmware, modifying low-level scheduling or adding unusually demanding onboard code, board support and application fit normally matter more than the RTOS brand. Choosing NuttX does not automatically provide an easier aircraft setup; choosing bare-metal firmware does not automatically provide lower end-to-end delay. The architecture must be evaluated as a complete system.

**Takeaway: select the least invasive supported extension path that can express your project’s actual behavior.**

**Additional documented evidence**

Profiles refer to core onboard flight-control software, not a GCS, configurator, SDK, simulator, or dependency. RTOS means a named real-time operating system; Linux, schedulers, and external APIs remain distinct. Scripting labels its execution context. Snapshot: evidence public by 31 December 2024; target, release, and component qualifications remain visible.

**ArduPilot**

- **RTOS/execution model:** Target-dependent: Rover releases document ChibiOS; Linux-based boards use Linux, and comparative evidence also lists NuttX. No single runtime covers every target [87][57][89].
- **Core language:** C++; the development guide distinguishes Python as a support-tool language [52].
- **Secondary scripting/control:** Onboard Lua 5.3.6 is sandboxed and normally loaded from the `scripts` folder (unavailable on F4 boards). Mission Planner separately supports external Python 2.x through 2.7 with IronPython; that is GCS, not firmware, scripting [62][49].
- **Protocols:** MAVLink carries GCS telemetry, missions, parameters, and commands; DroneCAN carries Controller Area Network (CAN) peripheral traffic [90][52].
- **License:** Core project: GPLv3 or later. Vendored Lua, excluding modifications, is MIT, a component exception [51][63][62].

**PX4**

- **RTOS/execution model:** NuttX is the primary RTOS on a flight-control board. PX4 also has POSIX/Linux/macOS contexts, including software-in-the-loop (SITL); companion-computer Linux is separate from flight firmware [54][91][92].
- **Core language:** C/C++ for application and platform-support code [58].
- **Secondary scripting/control:** No onboard scripting runtime is established here. MAVSDK documents C++ with Python, Java, and Swift wrappers for GCS or companion-computer scripting; Robot Operating System 2 (ROS 2) examples use C++ and Python for offboard control [86][85].
- **Protocols:** MAVLink covers GCS, telemetry, offboard control, and most simulation/API paths; uXRCE-DDS covers ROS 2/companion links, while uORB is the internal publish–subscribe bus. PX4 v1.16 documents default UDP 14550 for GCS, UDP 14540 for offboard APIs, and TCP 4560 for simulators; Gazebo can use its direct API [92][93][56].
- **License:** Core flight stack: BSD 3-Clause; documentation: CC BY 4.0 [94].

**Paparazzi**

- **RTOS/execution model:** Mixed: RT Paparazzi uses ChibiOS/RT; the v5.18/v6 plan described Linux for simulation and Parrot drones and ChibiOS for microcontrollers, while bare-metal/static-scheduler targets were being removed. A 24 May 2024 commit adds ChibiOS Pixhawk 6X files [73][74][75][76][77].
- **Core language:** C is the best-supported primary answer; repository detection reports C 59.5%, Python 8.8%, and OCaml 3.2%, but includes tools and documentation [79].
- **Secondary scripting/control:** Python 3 is documented for tools and libraries, including flight-plan and settings functions; the shown evidence does not establish an onboard scripting runtime [75].
- **Protocols:** PprzLink is the named project link; an airborne MAVLink module is also documented. IVY/GPSD follow-me and NatNet–Simulink are additional bridges, not necessarily primary protocols [64][99][75].
- **License:** Scope/version conflict: the repository reports GPL-2.0, while a v6.4.0 row reports GPL-3.0 for flight firmware, GFDL for documentation, and GPL-3.0 for the configurator. Verify the exact release and component [79].


**Runtime:** ChibiOS RTOS on supported targets; legacy `libopencm3` builds are bare-metal/no-thread; Linux is used for desktop simulation and some Bebop deployments, with static dispatch. [55][95] **Core:** C airborne code. **Secondary:** C custom navigation; PPRZLINK libraries use C, OCaml, Python and Rust, while Python/Ivy provides external messaging; no general onboard scripting runtime is established. [68][69][67][96] **Protocols:** PPRZLINK/PPRZ carries telemetry air-to-ground and datalink ground-to-air; Ivy links GCS agents; serial/UDP and MAVLink modules or bridges are also documented. [64][96][100][97] **License:** GPL-2.0/GPLv2-or-later core; PPRZLINK, documentation and hardware have GPL/LGPL/GNU-FDL/CC-BY-SA variants. [50][78][96][98][68]

**LibrePilot**

**Runtime:** FreeRTOS, typically on ARM, with the PiOS hardware-abstraction layer and delayed-callback scheduler; `simposix` runs the firmware on Linux. [53][101] **Core:** Embedded C and C++; the separate GCS uses C++/Qt5. **Secondary:** Arduino headers, documented for the 2017 “next” branch, can read telemetry and send UAVTalk commands; generated Python UAVObject/example scripts are external, and no official onboard scripting language is established. [53][83][59] **Protocols:** UAVTalk exchanges UAVObjects over USB, serial or radio telemetry; MSP/MAVLink telemetry and OPLink control/telemetry are also documented. [53][101] **License:** GPLv3-or-later core; documentation/artwork use CC-BY-SA, while some hardware uses CC-BY-NC-SA. [71][102]

**Betaflight**

**Runtime:** Cooperative multitasking rather than a traditional RTOS; the 4.3 scheduler protects gyro, filter and PID timing. [72] **Core:** C, with C++ used for tests. **Secondary:** Lua transmitter scripts on OpenTX/EdgeTX configure Betaflight through MSP; this is transmitter-side support, not an established onboard general-purpose runtime. [88][60][80][81] **Protocols:** MSP handles configuration, telemetry, commands and peripheral passthrough; CRSF, MAVLink and SmartPort provide telemetry, while DShot is the preferred flight-controller-to-ESC link and can return bidirectional telemetry. [104][105][70] **License:** GPLv3-or-later core; the Configurator is separately GPLv3. [61][106]

**iNAV**

**Runtime:** Priority-based cooperative scheduler, with no traditional RTOS; documented targets include STM32 F4/F7/H7 and AT32. [65] **Core:** C99/C11, with some C++ for unit tests. **Secondary:** The JavaScript-based INAV Programming Framework compiles into logic conditions through the Configurator or CLI; Lua runs on OpenTX/EdgeTX radios for telemetry. [65][107][66] **Protocols:** MSPv1/v2 covers configuration, telemetry, navigation, sensors, GPS, RC and commands; SmartPort, FPort, MAVLink, LTM and CRSF are telemetry protocols. The 2024-12-14 INAV 8.0.0 RC3 record documents MAVLink RC control plus telemetry and Mission Planner/QGroundControl monitoring. [108][65][103] **License:** GPLv3; a proposed MPL relicensing was not adopted, with a 2017 project conclusion that INAV would remain GPL. [82][84]

## Part Two — Ecosystem and Application Comparison

### Ecosystem and application comparison table

**Ratings describe integration readiness.** **Strong** means an established, explicit workflow with substantial tooling; **Moderate** means a useful route with narrower coverage, translation or compatibility work; **Limited** means a specialized or custom integration should be budgeted. An asterisk marks a conservative planning estimate based on the named interface, rather than a measured support score or proof that another integration is impossible.

**The row labels identify projects.** The five data columns below use the requested titles and order. Simulation ratings consider both software and hardware loops; consequently, a project can have excellent SITL while receiving a lower combined SITL/HITL rating.

|  | Companion Computer Support | ROS Integration Level | MATLAB/Simulink Support | SITL/HITL Simulation Support | Most Suitable Scenarios |
|---|---|---|---|---|---|
| ArduPilot | Strong — documented MAVLink data and command links | Moderate — established MAVROS translation workflow | Moderate — community coupling; 2024 log analysis | Moderate — extensive SITL; HITL is target-specific | Broad autonomy, mapping, payloads, aircraft, rovers and submarines |
| PX4 | Strong — MAVSDK and ROS 2 interfaces | Strong — firmware uXRCE-DDS bridge | Strong — deployment, peripheral and simulation tooling | Strong — SITL and documented HITL workflows | Research and Education, robotics, VTOL, model-based development |
| Paparazzi | Moderate — direct PPRZLINK/serial extension | Limited* — budget for PPRZLINK/Ivy bridging | Limited* — custom model/interface coupling | Strong — NPS explicitly supports SITL and HITL | Research and Education, custom UAS and experimental aircraft |
| LibrePilot | Limited* — custom UAVTalk integration | Limited* — budget for an object/protocol bridge | Limited* — custom data and model interfaces | Limited* — controller-specific simulator coupling | Vehicle-control development and existing LibrePilot systems |
| Betaflight | Moderate — MSP channel-level interaction | Limited* — custom MSP-to-ROS integration | Limited* — protocol-level custom coupling | Moderate — 4.5 Gazebo SITL; hardware loops specialized | FPV Racing, freestyle and pilot-oriented filming |
| iNAV | Limited* — MSP missions/telemetry; custom application | Limited* — custom MSP/telemetry bridge | Limited* — custom protocol or log workflow | Moderate — 7.1 SITL/RealFlight work; HITL specialized | Navigation-oriented fixed-wing, flying wings and multirotors |

**The strongest ratings have specific anchors.** ArduPilot documents companion-computer messaging and MAVROS; PX4’s releases document its native ROS 2 bridge, while MathWorks’ 2024 release notes establish firmware, hardware and actuator support. Paparazzi’s NPS documentation explicitly provides both simulation modes. Betaflight 4.5.0 and iNAV 7.1.0 supply release-level evidence of simulation development before the cutoff. [10] · ArduPilot MAVROS example [14] · PX4 v1.14 [15] · MathWorks 2024 release notes [28] · Paparazzi NPS [45] · Betaflight 4.5.0 [37] · [44]

**Specialists should not lose automatically.** A Limited ROS rating is irrelevant if the aircraft does not need ROS. Betaflight can be the best fit for a racing aircraft despite a much narrower robotics workflow than PX4; similarly, iNAV can be preferable for a navigation-equipped flying wing even when a general-purpose stack offers more external APIs. The appropriate comparison is the work needed to satisfy your requirements.

**Takeaway: use the table to eliminate mismatches, not to calculate an unconditional overall winner.**

**Additional documented evidence**

| Entity | Companion Computer Support | ROS Integration Level | MATLAB/Simulink Support | SITL/HITL Simulation Support | Most Suitable Scenarios |
| --- | --- | --- | --- | --- | --- |
| ArduPilot | APSync supports the RPi3, NVidia TX1, NVidia TX2 and…[154] | no evidence found | no evidence found | The page documents ArduPilot SITL connectivity…[164] | no evidence found |
| PX4 | no evidence found | PX4's README states that it has first-class DDS / ROS…[178] | no evidence found | PX4 documents comprehensive SITL simulation and…[174] | The source uses ArduPilot-only evidence and therefore…[127] |
| Paparazzi | no evidence found | no evidence found | Paparazzi documents a bridge between NatNet, Simulink…[311] | no evidence found | Delft University of Technology released its Lisa/S…[273] |
| LibrePilot | LibrePilot GCS is available for Windows, Mac, and Linux.[218] | no evidence found | no evidence found | no evidence found | LibrePilot was forked from OpenPilot.[214] |
| Betaflight | Betaflight 4.1 removed support for F3-based flight…[262] | Betaflight 4.1 removed support for F3-based flight…[262] | Betaflight 4.1 removed support for F3-based flight…[262] | Betaflight 4.1 removed support for F3-based flight…[262] | Betaflight 4.1 removed support for F3-based flight…[262] |
| iNAV | no evidence found | no evidence found | iNAV 3.0 supports an external BNO055 connected…[268] | The simulator OSD output identifies a new HITL format…[243] | The page contains a user report of having had…[317] |

For SITL/HITL, ArduPilot is Strong for native SITL and external/SIL workflows, with HIL-style limits; PX4 is Strong for documented SITL and HITL, although HITL is community- and target-conditioned; Paparazzi is Strong for self-contained SITL and HITL; LibrePilot is Limited because AeroSimRC/HITL was experimental and complete SITL is not established; Betaflight is Moderate because SITL is documented without a HITL workflow; and iNAV is Strong through native SITL and X-Plane HITL, with a sensor-processing caveat [163][202][211][231][340][283][237][301][345][279].

Betaflight companion support is Not established officially—an external MSP/MAVLink-over-UART report supports at most Limited—while ROS and MATLAB/Simulink are also Not established because no qualifying package or workflow is documented [325].

Across the rows, ArduPilot is Strong for companion computers, ROS, and SITL/HITL but Moderate for MATLAB/Simulink; PX4 is Strong in all four evaluated columns; Paparazzi is Moderate for companion, ROS, and MATLAB/Simulink and Strong for SITL/HITL; LibrePilot is Limited throughout; Betaflight has no established companion/ROS support, Limited MATLAB/Simulink, and Moderate SITL/HITL; and iNAV is Limited for companion and ROS, has no established MATLAB/Simulink support, and is Strong for SITL/HITL. The scenario column spans mixed-fleet survey/inspection, autonomy/survey, research/education, legacy/basic aircraft, FPV, and long-range/fixed-wing navigation [163][194][85][74][260][283][252][279][237][242][332][301][122][239].

**Comparison basis and evidence status**

Within the fixed six-project denominator, the clearest conditional distinctions are these: PX4 is strongest for a robotics-oriented integration and simulation workflow; ArduPilot is strongest for broad autonomous missions and vehicle coverage; Paparazzi is most distinctive for technically intensive research and customization; LibrePilot is easier to position as a simple or legacy-platform option; Betaflight is optimized for manual first-person-view (FPV) flying; and iNAV sits between FPV firmware and a full navigation autopilot. These are conditional fits, not a universal ranking: the suitable choice changes with the aircraft, mission, hardware, and desired autonomy level [214][188][280].

The ratings below compare documented capability and maturity within the six named projects, not popularity, repository size, or market share. The available comparisons describe capabilities, hardware, development activity, and intended use but do not provide a common formal support denominator [214][252]. Other sources compare only two projects, three projects, four firmware families, or an eight-project historical set, so none can replace the report’s fixed six-project denominator [280][141][290]. A 2024 platform comparison used its own normalized 0–10 measures for performance, flexibility, energy consumption, and complexity; those measures are not substituted for the Strong/Moderate/Limited rubric here [188].

**Strong** means broad, documented, usable, and reasonably mature support. **Moderate** means a meaningful but narrower, conditional, indirect, or less mature path. **Limited** means minimal, immature, or weakly evidenced support. **Not established** means that the eligible evidence does not justify a reliable rating; it does not mean that the capability is proven absent. Software-in-the-Loop (SITL) runs flight software against a simulated vehicle, whereas Hardware-in-the-Loop (HITL) runs firmware on real flight hardware while the vehicle and sensors are simulated.

The deciding condition after this table is not the label alone. Choose PX4 when ROS 2, companion computing, model-based development, and repeatable simulation are central; choose ArduPilot when broad vehicle or mission coverage is central; choose Betaflight when the aircraft is primarily manually flown for FPV performance; choose iNAV when GPS navigation is needed without the full complexity of a larger autonomy stack; and shortlist Paparazzi or LibrePilot only when their specific research, hardware, simplicity, or legacy-platform conditions match the project.

**ArduPilot: autonomy, vehicle breadth, and SITL evidence**

**ArduPilot’s strongest documented advantage is mission-oriented autonomy across varied vehicles.** A 2024 discussion describes support for multicopters, fixed-wing aircraft, ground vehicles, and underwater vehicles, together with route planning, obstacle avoidance, and interaction with other vehicles. The same source identifies high computing-resource demand as a limitation, so feature breadth does not remove the need to check the companion hardware and flight-controller resources [188]. Another comparison identifies ArduPilot support for planes, vertical-take-off-and-landing aircraft, rovers, multirotors, boats, submarines, and blimps, with MAVLink as the command protocol and DroneKit as a high-level control interface [280].

The supplied flight-mode evidence lists Auto, Guided, Loiter, Return-to-Launch (RTL), SmartRTL, Follow, and ZigZag. Several of those modes require valid positioning data before takeoff, so their presence should not be interpreted as unconditional autonomous capability [138]. This is the mechanism behind ArduPilot’s fit for waypoint missions and navigation-heavy applications: the firmware supplies dedicated mission and position-control modes, while the aircraft still needs appropriate positioning sensors, configuration, and a suitable airframe.

**ArduPilot’s SITL evidence is concrete but not equivalent to HITL evidence.** A dataset paper published on 2024-01-15 describes ArduCopter running in SITL with a simulated flight-dynamics model. The simulated servo and motor outputs feed back into the firmware control loop, while Mission Planner and MAVProxy issue MAVLink commands [127]. In one sensor-failure experiment, the test set `SIM_GPS_DISABLE 1`; the logged GPS status flag changed from 6 to 1, after which ArduCopter entered failsafe, activated land mode, and performed a vertical landing at its current position [127]. MAVLink telemetry logs, or “tlogs,” were transmitted from ArduPilot to Mission Planner, while dataflash logs were retained on the simulated controller [127].

That result is useful evidence for repeatable failure testing, not proof of real-flight behavior. The same study explicitly states that its dataset was generated exclusively in SITL and may not capture the complexity and variation of real-world flight [127]. Accordingly, ArduPilot’s combined SITL/HITL cell remains below Strong in this evidence set: SITL is established, but HITL is not.

ArduPilot’s ecosystem advantage is therefore **breadth and mission depth**, not necessarily the lightest or simplest implementation. It is a strong candidate for survey, mapping, autonomy, and research projects when the team can provide the required sensors, computing resources, and configuration effort. A manually flown FPV quad that needs only high-rate acro response would not automatically benefit from that breadth.

**PX4: integration, middleware, and simulation**

**PX4’s clearest differentiator is its robotics-oriented integration architecture.** The project record describes uORB as a publish/subscribe middleware compatible with the Data Distribution Service (DDS), together with first-class MAVLink and DDS/ROS 2 integration [194]. MAVLink provides command and telemetry exchange, while a separate comparison identifies MAVSDK as PX4’s primary high-level vehicle-control interface [280]. The repository record also describes broad support for flight-controller boards, sensors, telemetry radios, and actuators through the Pixhawk ecosystem [194].

The same record lists multicopters, fixed-wing aircraft, vertical-take-off-and-landing aircraft, and rovers among the supported vehicle classes, with additional experimental platforms receiving only basic support outside the regular flight-test program [194]. Developer documentation is aimed at people modifying the flight stack or middleware, hardware integrators adding boards and peripherals, and users adapting PX4 to unsupported airframes [193]. This explains why PX4 is attractive for a technically capable research or product team, while also explaining why a beginner may find configuration more demanding. A 2024 comparison likewise characterizes PX4 as suitable for high-performance systems and large volumes of sensor data, but complex for beginners [188].

**PX4’s simulation mechanism is unusually accessible in the cited project record.** The documented workflow runs PX4 SITL with one Docker command, maps UDP port 14550, and then connects QGroundControl for flight [194]. The same record describes comprehensive SITL, HITL, and log-analysis tools [194]. That combination gives PX4 a practical advantage for teams that want to test controllers, perception, or autonomy before risking hardware.

**PX4’s BSD license can affect ecosystem decisions.** The cited comparison states that PX4 uses the BSD license and interprets that as allowing code changes to remain outside the main branch, which can be attractive when a company wants to keep flight-control intellectual property private [280]. This is a license-related ecosystem trade-off, not a claim that proprietary companion-computer code must be contributed to any autopilot project.

Several evidence-status qualifications remain important. A live repository page displays 12.8k stars, 16.2k forks, 137 releases, 911 contributors, and a latest-release label of v1.17.0, but the supplied page slice gives no observation date [193]. Those interface statistics and the latest-release label are therefore not used as 2024 maturity measurements. Similarly, one literature page reports PX4 companion-computer, ROS 2, MATLAB/Simulink, and SITL/HITL capabilities, but its publication metadata is not sufficient to establish pre-2025 availability . Another literature record reports MATLAB/Simulink integration but likewise lacks a qualifying date . The dated or otherwise bounded project records support PX4’s middleware and simulation mechanisms; they do not justify silently importing later claims.

PX4 is consequently most attractive when the project values **ROS 2, companion computing, simulation, high-rate sensor processing, or model-based research**. The deciding limitation is team capacity: a beginner seeking the simplest path to a small manually flown quad may value a less expansive configuration environment.

**Paparazzi: technical research and in-loop customization**

**Paparazzi’s distinctive strength is technical openness for research-oriented development.** A historical source published on 10 September 2012 and describing the state of the projects in May 2012 presents Paparazzi as an autopilot for inexpensive autonomous aircraft of all types. It originally targeted fixed-wing aircraft and later supported quadrotors by modifying the control-mixing rule. The source reports nine autopilot hardware systems developed under the ENAC team and a graphical ground-control station with flight-path scripting [141].

That source reports GPS-based waypoint navigation, altitude hold, hardware-in-the-loop support, other multirotor airframes, camera stabilization, and a ground-control station, but not computer-vision support in its summarized comparison [141]. Because the evidence is historical, it establishes that these capabilities existed in that period; it does not by itself establish their maturity or hardware availability at the 2024 cutoff. A separate contemporary description characterizes Paparazzi as technically demanding, mainly used by universities, limited in hardware availability or openness, and Linux-dependent at the time described [214].

**Paparazzi’s communication path is explicit but specialized.** PPRZLINK is identified as the Paparazzi UAV communication library. It provides serial and UDP access, and uses the Ivy software bus for messages exchanged among ground agents [64]. Telemetry messages travel from aircraft to ground, datalink messages travel from ground to aircraft, and Ivy-based messages are intended for the ground side [64]. A PPRZROS bridge is available, but the cited page does not establish whether it is official, maintained, or compatible with ROS 2 [64]. That is why the ROS cell is Limited rather than Strong.

PPRZLINK itself is stated to be under GPL version 2, with a possible future change to LGPL to ease integration into third-party projects [64]. This is a component-specific license fact and should not be silently treated as the complete license answer for all Paparazzi software.

The architectural evidence explains the research trade-off. Paparazzi has its own ABI middleware, while ROS spans inter-processes and systems; middleware bridges make integration easier but can cost performance. Paparazzi also permits custom functions inside the attitude-controller loop, which can be valuable when a research function must run at control-loop timing rather than as a slower external process [274]. This low-level placement is a genuine differentiator for control-law and embedded-systems research, but it requires substantially more technical expertise than a configuration-only workflow.

Paparazzi is therefore a conditional fit for **university research, education, inexpensive autonomous aircraft, custom control laws, and GPS waypoint experiments**. It is less attractive when the project requires a large, beginner-oriented integration ecosystem, broadly documented ROS 2 support, or a modern plug-and-play hardware path.

**LibrePilot: approachable legacy hardware with substantial qualifications**

**LibrePilot’s main practical advantage is a relatively approachable configuration and stabilization environment for supported legacy hardware.** A 2024 comparison describes it as simple to use, suitable for users with basic knowledge, and appropriate for entry-level flight stabilization, while also describing its functionality as limited relative to more capable platforms [188]. A separate description presents it as a general autopilot for fixed-wing and rotor-wing aircraft, including inexpensive CC3D-based platforms, with an excellent GUI and solid firmware; it attributes the smaller feature set partly to a smaller developer community [214].

The historical LibrePilot/OpenPilot manual identifies itself as Release 0.1.4 dated 16 October 2016 and includes LibrePilot release 15.09 as its first release [260]. It describes the Ground Control Station (GCS) as a configuration, control, and monitoring application for Windows, macOS, and Linux. It documents serial telemetry, USB, I2C, GPS, receiver interfaces, OPLink, camera stabilization, and autonomous extensions [260]. These facts establish the documented software and hardware boundary, but the manual does not establish LibrePilot’s scripting languages, core language, license, ROS integration, MATLAB/Simulink integration, or a current 2024 maturity level [260].

**LibrePilot does have external-computing pathways, but they are narrower than a modern companion-computer framework.** The Revolution board’s unshared SPI port can connect to another embedded system such as an Overo Linux board. The manual describes an additional board supplying networking, storage, video analysis, autonomous behavior, and artificial intelligence while Revolution remains the real-time controller and sensor platform [260]. It does not identify that additional board as a formal companion computer or provide a named offboard-control API, so the appropriate rating is Moderate rather than Strong.

OPLink supplies another practical mechanism. It supports telemetry-only, telemetry-plus-vehicle-control, and vehicle-control-only modes. A ground OPLink can pass vehicle telemetry through Bluetooth to a computer or smartphone [260]. Direct Bluetooth connection to the flight controller is useful for nearby configuration but is normally lost during flight because of its short range; OPLink extends the link to the ground [260]. The described workflow requires successful binding, and CC, CC3D, and Atom vehicle-control configurations require the relevant PPM wiring. The manual also specifies a 38400-baud Bluetooth connection to match OPLink, while another historical release note records a 9600-bps PPM-only radio mode [260][283].

The radio design creates a material caveat: OPLink units are described as operating at 433 MHz, and simultaneous use of a 433-MHz UHF control transmitter can create a frequency conflict with possible loss of control [260]. This is a hardware and deployment constraint, not a general software-rating issue.

**LibrePilot’s application coverage varies strongly by board and release.** The manual describes multirotor, helicopter, and fixed-wing operation, GPS navigation, uploaded flight plans, autonomous path following, optional fixed-wing airspeed sensing, and camera stabilization [260]. CC3D and Atom do not support GPS functions such as Return to Base or Position Hold, whereas Revolution is described for multirotors, helicopters, and fixed-wing aircraft [260]. Release notes also document ground-vehicle configuration in the GCS, receiver interfaces including PWM, PPM, Spektrum satellite, and Futaba S.Bus, and direct MSP and MAVLink telemetry to compatible OSD devices [283].

The release history records auto-takeoff and landing in path plans, GPS-assisted VelocityRoam, RateTrainer for beginners and aerial photographers, GPSAssist braking into position hold, and camera stabilization [283]. However, it also records strong version and target dependence: GPS-navigation additions were aimed at Revolution, CC3D was excluded from one 15.05 feature release, and advanced Revo features such as altitude hold, guidance, Return to Home, and autolanding were described as still in development in an earlier release [283]. The first Revolution hardware batch was explicitly intended for developers and early testers rather than users seeking a completely final platform [283].

**Simulation and integration evidence is limited and historical.** The changelog documents an AeroSimRC plugin for HITL version 2 and calls it experimental. It also records HITL and SITL defects, including FlightGear position/velocity problems and sanity checks that broke HITL/SITL [283]. The manual’s general recommendation to use a flight simulator for learning is not, by itself, evidence of integrated SITL or HITL [260]. A MATLAB-import bug fix is recorded, but no MATLAB/Simulink toolbox, block library, code-generation path, or sustained support level is documented [283]. Likewise, UAVTalk and OPLink external interfaces do not establish a ROS or ROS 2 integration [283].

LibrePilot is therefore most defensible for **beginner learning, legacy CC3D/Revolution builds, basic stabilization, selected fixed-wing or rotor-wing projects, and historical research or robotics work**. The deciding condition is whether the exact board and release provide the required GPS, navigation, telemetry, and simulation features. A project needing current active development, deep autonomy, or modern ROS/MATLAB integration should treat LibrePilot’s dated evidence and target limitations as major disadvantages.

**Betaflight: high-performance FPV with resource and integration limits**

**Betaflight’s strongest documented fit is manual FPV performance.** The project record describes open-source flight-control firmware used for racing, freestyle, cinematic filming, long range, micros, and wings [242]. It documents DShot, Multishot, Oneshot, and Proshot motor protocols; Blackbox flight recording; receiver and failsafe connections; CRSF, FrSky, HoTT smart-port, and MSP telemetry; OSD; in-flight PID and rate tuning; configurable serial ports; and VTX support [242]. A secondary technical description characterizes the platform as performance-oriented, actively developed, broadly supported across F4, F7, and H7 boards, and especially suitable for racing and freestyle [289]. Because that secondary page is not used as the sole date anchor, the more specific cutoff evidence comes from Betaflight 4.5 and 4.5.1 release records [250][329].

Betaflight 4.5 documents improved GPS hardware handling, GPS Return to Home, magnetometer use, GPS mapping in Blackbox, failsafe changes, landing improvements, receiver binding, Soft Serial, custom builds, and hardware support [250]. It also documents an 8-channel Blackbox debug configuration and a default 5% initial dynamic-idle value, both specific to that release [250]. GPS-based lap timing is available as a custom build option, requiring GPS in the firmware build and a sufficiently good GPS signal [250].

**Betaflight’s navigation capability remains bounded.** GPS Rescue is described as an advanced safety feature that can autonomously fly the craft home after RC or video-link loss, but not as a full navigation stack [138]. The release notes state that GPS Rescue places a large CPU load on the flight controller and recommend a 4k PID loop, especially at 57600 baud, for reliability [250]. Thus, GPS Rescue supports long-range safety and selected navigation-oriented use, but it should not be equated with ArduPilot-style mission planning.

**Hardware resources directly constrain Betaflight’s ecosystem value.** A board-support account states that older F1 and many F3 boards, some early F4 variants, and a few early F7 boards lost support because of insufficient processing power, memory, flash, sensors, or abandoned manufacturer targets [252]. It quotes historical Betaflight 3.2/3.3 and 4.0 release decisions concerning F1 and F3 support, but the page does not provide a reliable publication date; those statements are therefore historical context rather than a standalone 2024 snapshot [252]. The mechanisms remain important: limited CPU prevents modern filtering and protocols, firmware can outgrow available flash, and unmaintained targets eventually lose support [252].

The same source recommends modern F7 boards as a general value option, H7 boards for high-performance or heavy digital-video-recorder use, and AIO F7 1S/2S boards for whoops and micros. It says unsupported hardware may be retained for slow cinematic cruising on a 3S rig, but recommends replacement for demanding freestyle, racing, long-range, cinematic, or heavy-GoPro use [252]. The cloud-build documentation likewise warns that enabling many options can exceed the flash capacity of 512-KB targets [323]. DShot and bidirectional DShot provide ESC telemetry such as RPM, voltage, current, temperature, and status [70].

**Betaflight’s external ecosystem is intentionally narrower.** Serial ports, MSP, telemetry, GPS, OSD, and peripheral links are not equivalent to a documented companion-computer or ROS workflow. The cited repository record does not directly establish either ROS or companion-computer support [242]. Betaflight 4.5 release notes do not establish MATLAB/Simulink support [250]. A 4.5.1 SITL firmware asset and a development-page `make SITL` path establish Software-in-the-Loop build support, but no equivalent HITL workflow is established [60][329]. A displayed core source file provides evidence of GPL-licensed C code and scheduler-based execution, but a single file cannot establish the complete project profile or any missing ecosystem support [227].

Betaflight is consequently the best conditional fit for **manual FPV racing, freestyle, acro, cinewhoops, micros, wings, and pilots prioritizing response and tuning**. It is a weaker choice when the project’s decisive requirement is ROS, companion-computer autonomy, MATLAB/Simulink model-based deployment, or full mission navigation.

**iNAV: navigation features without the full autonomy stack**

**iNAV’s clearest differentiator is navigation-oriented capability on hobby-class hardware.** The pre-cutoff evidence describes iNAV 4.0’s Soaring mode for fixed-wing glider and thermal-oriented operation: it changes Course Hold, Cruise, or Position Hold behavior, disables altitude control, and allows the aircraft to soar, although thermal following was not yet implemented in that release [333]. Other supplied comparisons characterize iNAV as suitable for GPS navigation, autonomous flight, long-range navigation, fixed-wing aircraft, flying wings, and navigation-focused models, with waypoint, Return-to-Home, altitude-hold, position-hold, automated-launch, and navigation-assisted functions [289]. The practical distinction is that iNAV adds navigation to a flight-controller ecosystem familiar to FPV builders, without requiring the full complexity of ArduPilot.

The ecosystem limitation is equally important: the cited iNAV records do not establish a named companion-computer API, ROS package, or MATLAB/Simulink workflow. Telemetry or navigation features should not be treated as proof of offboard-computing support. The table therefore preserves those cells as Not established rather than guessing from iNAV’s GPS capabilities.

**iNAV’s SITL/HITL evidence is stronger than its other integration evidence.** The INAV 8.0.0-RC4 release record documents built-in serial-receiver support in SITL, flight-controller proxy mode, updated SITL documentation, and an `inav-HITL-plugin` pathway [279]. It also records a specific limitation: accelerometer and magnetometer data are not processed when SITL is used with that HITL plugin [279]. This supports a Moderate combined rating: both simulation paths are represented, but the implementation is not equivalent to an unrestricted, mature validation environment.

**The license discussion creates a separate ecosystem trade-off.** A 2017 iNAV discussion concludes that the project would remain under GPL. It explains that GPL prevents static linking with non-GPL code and therefore prevents closed-source components from being included in iNAV as distributed as a whole; features requiring such components would need GPL-compatible implementations [84]. This is a source-distribution constraint, not evidence about companion computers, ROS, MATLAB, or simulation.

iNAV is therefore most suitable for **GPS-assisted long-range FPV, fixed-wing and flying-wing projects, waypoint navigation, position hold, Return to Home, and navigation-focused hobby aircraft**. It is less suitable than Betaflight for projects whose main objective is maximum acro performance, and less suitable than ArduPilot or PX4 for deep autonomy, complex companion-computer integration, or large research workflows. A page in the supplied evidence explicitly dated 2026 is outside the permitted period; its later iNAV and Betaflight recommendations are not used in this comparison [271].

**Cross-project qualifications and practical pros and cons**


- **PX4’s advantage is integration depth.** uORB, DDS/ROS 2, MAVLink, Pixhawk hardware, SITL, HITL, and log analysis form a coherent robotics-development path [194]. The cost is greater configuration complexity and the need to distinguish regularly tested frames from experimental ones [188][194].
- **ArduPilot’s advantage is breadth of missions and vehicles.** MAVLink/DroneKit control, dedicated autonomous modes, broad vehicle coverage, and SITL failure testing support survey, mapping, autonomy, and research [127][188][280]. The costs are computing demand, configuration effort, and the absence of equivalent HITL evidence in the cited experiment [127].
- **Paparazzi’s advantage is low-level research flexibility.** PPRZLINK, ABI, flight-path scripting, and the ability to place custom functions in the attitude-control loop can suit researchers who need to modify control behavior deeply [64][274]. The costs are technical complexity, dated or hardware-specific evidence, and uncertain ROS bridge maturity [214][64][141].
- **LibrePilot’s advantage is accessibility on supported legacy hardware.** Its GCS, stabilization workflows, OPLink telemetry, and beginner-oriented interface can reduce the initial learning barrier [188][260]. The costs are target-specific feature gaps, historical and experimental simulation support, no established MATLAB/Simulink or ROS path, and a smaller or less current development base [283].
- **Betaflight’s advantage is pilot feel and FPV tooling.** High-rate motor and sensor handling, tuning, OSD, Blackbox, receiver/telemetry support, and FPV-focused workflows make it appropriate for racing and freestyle [242][250]. The costs are limited evidence for companion-computer and ROS integration, no established MATLAB/Simulink support, incomplete HITL evidence, and hardware-resource constraints [242][250][252].
- **iNAV’s advantage is a middle ground between FPV hardware and navigation.** It adds GPS-assisted modes, fixed-wing support, and long-range navigation while remaining closer to the hobby flight-controller ecosystem [279][333]. The costs are less established integration support and a narrower autonomy ceiling than ArduPilot or PX4 [279][84].

Some evidence gaps are structural rather than project failures. A live repository’s stars, forks, releases, or contributor count has no value as a common maturity score without an observation date [193]. A literature survey whose publication population and date do not match the six-project comparison cannot be used to rate the six rows . A four-family feature matrix covering ArduPilot, PX4, Betaflight, and iNAV cannot establish Paparazzi or LibrePilot values or a six-project denominator [290]. Finally, a 2024 source reports documentation gaps and up to 25% variation in platform power-consumption measurements under particular operating modes, while separate experiments report a 20% reduction in navigational error and an estimated 15% energy-efficiency improvement from sensor fusion and trajectory prediction; those results are not attributed uniformly to the six autopilots and should not be converted into cross-project scores [188].

The table should therefore be read as a decision filter: first identify whether the project needs high-level autonomy, manual FPV performance, GPS navigation, low-level research customization, or an integrated robotics workflow; then verify the exact flight-controller target, release, simulator, companion hardware, and required external tools.

**Additional evidence for integration ratings**

- **PX4 — Strong companion-computer and ROS 2 support; combined SITL/HITL is not established here.** PX4 v1.16 documents GCS, companion-computer and other MAVLink links; Ethernet uses one IP network, GCS port 14550, or companion “Onboard” port 14540 with `MAV_2_MODE=2` [251]. uXRCE-DDS provides bidirectional PX4–companion exchange over serial, UDP, TCP or custom links, with C++ and Python offboard examples; matching messages, QoS and coordinate-frame conversion remain conditions [85]. Gazebo/Gazebo Classic SITL and automatic UDP-port-8888 startup are documented, but not a separate HITL procedure [85]. MATLAB/Simulink is not established in these cards; Pixhawk 4/NuttX is documented for academic and commercial, multi-vehicle use where servo interfaces fit [191].

- **Paparazzi — Target-specific simulation; companion, ROS and MATLAB/Simulink levels are not established.** RT Paparazzi uses ChibiOS/RT threads, priorities, memory control and a hardware-abstraction layer, with kernel overhead [73]. The April 2021 v5.18 record reports an OCaml/dependency build rewrite, static scheduling and planned `pprzlink` changes; v6 planned to remove lpc21 and bare-metal STM32, leaving Linux for simulation/Parrot and ChibiOS for microcontrollers [74][76]. A ChibiOS/Pixhawk 6X target is also recorded [77]. Python 3 is documented for tooling, not onboard scripting [75]. Gazebo/NPS provides 3-D camera-based closed-loop vision simulation, but is rotorcraft-only and has AHRS/INS, video, atmospheric-model and target-configuration limitations [255][256].

- **LibrePilot — Limited companion support; HITL exists, but combined SITL/HITL is not established.** LibrePilot2Go supplied USB/Bluetooth/OPLink field telemetry but was beta/alpha software and not a full GCS [291]; PC/smartphone OPLink supports configuration, calibration and control, with direct-Bluetooth range limits [259]. UAVTalk/UAVObjects carry remote telemetry metadata, and FlightGear can replace local GPS data in HITL [267]. A ROSBridge HITL-export commit is limited/legacy evidence [321]; MATLAB/Simulink is not established. FlightGear/UDP HITL is documented, while SITL is not [257][267]. Supported scenarios are field telemetry, stabilization/robotics and practical FPV setup; a personal Helix project links a high-level drone language to LibrePilot and a Google Earth simulation, not production suitability [253][266][292].

- **Betaflight — Moderate SITL artifact; companion, ROS, MATLAB/Simulink and HITL levels are not established here.** Lua on OpenTX/EdgeTX configures Betaflight through MSP from the transmitter rather than onboard [80][254]. Betaflight 4.1.0, published **2019-10-16**, supplied `betaflight_4.1.0_SITL.hex` at **946.3 KB**; F3 support was removed and no HITL workflow is shown [262]. Version 4.4.3 notes UART, GPS, MSP, JETIEXBUS and DSHOT-telemetry changes, but its publication date is not supplied [261]. The strongest scenario evidence here is FPV/radio configuration and software testing.

- **iNAV — Limited external-computer evidence; SITL mechanisms are documented, but combined and ROS/MATLAB ratings are not established.** INAV 8.0.0-RC1, published **2024-11-16**, documents single-UART MAVLink RC control plus telemetry and Mission Planner/QGroundControl monitoring, not a maintained companion workflow [265]. It records SITL airspeed through an HITL plugin, serial receivers and FC-proxy mode, but not a complete combined rating [265]. INAV 7.1.0, published **2024-04-01**, adds GPS-heading-dependent compass-free navigation, fixed-wing landing and native tailsitter support; a compass remains recommended and F411 boards stop at INAV 7 [263]. SmartPort, S.Port/F.Port and HoTT telemetry maintenance is also recorded [264]. Geozones are unavailable on STM32F722, and GPS-fix assistance is not precise pilot return [265].

- **ArduPilot — Target-specific ChibiOS and performance evidence.** The ChibiOS port merged on **2018-01-15** for Pixhawk, Pixhawk2, PixRacer and MindPX-v2; NuttX remained separate and ChibiOS required WAF [132]. High-rate tests exposed IOMCU **1.5 Mbit/s** and USB-MAVLink scheduling limits; one Solo test reported overruns falling from **30–50%** to **0.125%** with ChibiOS, but these single tests do not establish a general companion or scenario rating [132].

As of 2024-12-31: PX4—Strong companion/ROS: MAVSDK/MAVLink runs onboard or on Raspberry Pi; ROS 2 uses FastRTPS/MAVROS [268,364]. Strong SITL/HITL: Gazebo/JMAVSim recreate the vehicle; SITL omits hardware, HITL uses the real controller [192]. Paparazzi ROS 2—Moderate: community bridge sends waypoints/telemetry but needs Humble/Raspberry; its connection function failed [293].

Evidence to 2024-12-31: ArduPilot—ROS2/DDS, companion, Simulink, SITL [87]; PX4—MAVLink/ROS2, SITL/HITL [287][297]; Paparazzi—MAVLink 2 telemetry [298]; LibrePilot—FlightGear HITL, SITL uncertain [284][294]; Betaflight—MSP/GPS Rescue, hardware-limited [285][296]; iNAV—MSP/MAVLink external control, versioned SITL/HITL [295][299][300].

**Additional evidence**

- **ArduPilot**—companion **Moderate** (serial Raspberry Pi/MAVLink); ROS **Moderate** (MAVROS topics/services); SITL documented, HITL unestablished; autonomy/research [136][275].
- **PX4**—companion **Strong** (MAVSDK offboard, telemetry and mission APIs; C++, Swift and Python external SDK); MATLAB/Simulink **Moderate** (UAV Toolbox/HITL, with high-rate I/O limits); SITL/HITL **Strong** [288][270][276].
- **Paparazzi**—companion **Moderate** (external-pose, guided-setpoint and mission messages); simulation **Moderate** (Bixler/JSBSim); FPL missions compile to C via an OCaml generator; research/fixed-wing [281][79][272].
- **LibrePilot**—companion **Moderate** (Arduino serial telemetry/UAVTalk); ROS **Limited** (ROSBridge IMU/odometry; ROS 2 maturity unestablished); education/prototyping [83][282].
- **Betaflight**—C core; FPV racing/freestyle/manual quads; companion **Limited**, while ROS, MATLAB/Simulink and HITL remain unestablished [134][276][88].
- **iNAV**—SITL/HITL **Strong** (native SITL, RealFlight/X-Plane and MSP-over-TCP); GPS long-range/fixed-wing/waypoints; companion **Limited** [301][277][278].

**ArduPilot —** As of the cutoff-bounded comparison, **Strong** companion-computer support is documented: an onboard computer can use MAVLink to receive autopilot and GPS data, make flight decisions, trigger photographs, preprocess sensor data, and actuate peripherals; a 2020 change also added Guided-mode control of heading, speed, altitude, and their rates. [151][229] The ecosystem includes DroneKit, MAVSDK, Pymavlink, BlueOS, and Rpanion workflows, although APSync is deprecated. [52][154] **ROS integration is Moderate overall:** ROS 1 uses MAVROS, while ROS 2 has AP_DDS/micro-ROS packages and tests; Humble-only instructions, “support is improving” notices, and conflicting or undated native-ROS2 claims prevent an unqualified Strong rating. [147][148][158][335] The integration repository itself is GPL-3.0, which does not determine the core-firmware license. [116]

**ArduPilot’s remaining ecosystem cells —** **Moderate** MATLAB/Simulink support is documented through a modified TCP/UDP toolbox, MEX files, Simulink connection blocks, and rover/helicopter examples, but additional toolboxes and MATLAB 2020a may be required; external JSON/MAVLink physics is not equivalent to a full native integration. [137][164][162] **SITL is Strong; combined SITL/HITL is Moderate and conditional:** native SITL supports failure modes, multiple vehicles, real peripherals, and external simulators, while Simulation on Hardware reuses SITL but is not enabled by default, remains under improvement, and has limited precompiled-board coverage. [113][249][162][163] Suitable scenarios include research and education, development and testing, companion-assisted autonomy, inspection or agriculture, and varied air, ground, and water vehicles. Broad hardware, redundant sensors, and I/O are advantages; flash-limited boards, Linux-target feature losses, and board-specific support are disadvantages, partly mitigated by custom firmware. [109][215][226] A secondary description also reports GPLv3 and broad vehicle coverage, but its current-release label is not used as cutoff evidence. [118]

**PX4 —** **Strong** companion-computer support is documented through MAVLink and XRCE-DDS; **Strong ROS 2** support uses uXRCE-DDS to publish PX4 uORB messages directly as ROS 2 topics, while MAVROS provides a tested bridge. [306][304][307] These mechanisms suit offboard control, controller validation, simulation, and research involving fixed-wing, multirotor, VTOL, or indoor vehicles; the indoor/outdoor preference reported by one tutorial is contextual, not universal. [304] PX4 release v1.14.0 contained **324,666 C/C++ lines on 23 July 2024**; reported components included 79,689 driver lines, 14,979 `ekf2`, 10,120 MAVLink, and 9,824 commander lines. This is code-size context, not a maturity score. [286]

**Paparazzi —** A supplied project page, whose publication date is not shown, describes Paparazzi as a university-developed open-source system for **Research and Education** and fixed-wing drones; its displayed 1,718 stars is a popularity indicator, not ROS evidence. Treat those scenarios as provisional pending dated corroboration. [216] The landscape snapshot labels Paparazzi v6.4.0 “ChibiOS / Scheduler,” preserving target/runtime variation. 

**LibrePilot —** **Limited and conditional** scenario fit is supported for CC3D and documented UAV configurations with setup, sensor-integration, and GCS guidance; a 2024 document says development ceased in **2019**, so legacy or experimental use requires a maintenance check. [240] A landscape page places LibrePilot among EOL or stale suites without identifying which condition applies, and reports GPL-3.0-only for LibrePilot GCS—not the core flight firmware—so the core license remains **not established from this evidence**. 

**Betaflight and iNAV —** Betaflight is most clearly suited to high-performance fixed-pitch quadcopters, FPV racing, and acrobatics; collective-pitch rotorcraft are a limitation relative to Rotorflight. The landscape labels Betaflight v4.5.2 “Scheduler,” C, GPL-3.0 rather than a traditional RTOS. [240] For iNAV, the same snapshot labels v8.0.1 “Scheduler,” C, GPL-3.0; repository history records the CleanFlight-to-INAV change in pull request #8583, merged commit 94fc253 into milestone 6.0. [302] This history source establishes no reliable iNAV ecosystem rating; undated comments about laptop-only field configuration are anecdotal and not cutoff-verified. [133]

At the 2024-12-31 cutoff, **ArduPilot’s MATLAB/Simulink support is Moderate and qualified**: a 2020 record documents JSON SITL, MATLAB vehicle physics, Simulink rover/helicopter models, UDP visualization and SITL serial testing; a SIL connector requires MATLAB R2022a or earlier, while the 13-Nov-2012 APM2 blockset was early and target-specific. One 2020 account calls the workflow Strong, so the unresolved issue is breadth and maintenance, not absence of integration [166][131][167]. ArduPilot’s SITL component is Strong, but the combined SITL/HITL result is **Limited/Not established** because SITL paths are documented while no eligible source here demonstrates a technical HITL workflow [166][196][62].

ArduPilot conditionally fits autonomous Plane, Copter and Rover missions, FPV, camera survey/mapping, research and custom vehicle dynamics, agriculture, inspection and underwater work. Mission Planner adds mode changes, waypoint and grid-photography missions, and scripting, subject to telemetry, payload, board and mission requirements [49][120][111]. Broad board, bus and redundant-sensor support is an ecosystem strength; Linux targets add CPU and memory for advanced algorithms but may lose DShot, GPIO functions and easy upload [303]. MAVLink supports ground-station commands over radio or MAVProxy-routed internet [130]. GPLv3 flight code can coexist with closed companion-computer code, while high-level vision, avoidance, planning and decisions may require a mission board; this flexibility increases configuration effort [119][224][125].

**Paparazzi’s MATLAB/Simulink support is Limited.** A 29-June-2011 developer record says its simulator, firmware and MATLAB interfaces had to be written independently and requests a Simulink loop. Paparazzi hardware was considered powerful enough with Overo, but one account reported fewer hardware interfaces than ArduPilot. It therefore suits teams willing to build or adapt tools, rather than teams needing a ready-made workflow [169].

**PX4 is Strong for companion computers and ROS integration**: documented paths include serial/Ethernet links, TELEM2 with MAVLink for offboard control, ground-station/cloud routing, ROS 1/MAVROS, and ROS 2/uXRCE-DDS; ROS 2 external modes require a companion computer [197][309][173]. MATLAB/Simulink support is Strong but conditional: UAV Toolbox provides SIL/HIL, uORB and Pixhawk deployment; the 2024 setup record used R2024a, package 24.1.0, PX4 v1.14.0 and compatible WSL/Ubuntu [196][248]. SITL/HITL support is Strong through Pixhawk-host/jMAVSim and Pixhawk/QGroundControl/Simulink HIL, although one HIL example lacks real sensors and actuators [196]. PX4 suits research, education, survey, VTOL and complex-autonomy work; developer kits ease setup, but experimental frames, hardware cost, tuning and offboard-flight safety remain conditions [173][198][220].

Betaflight is the conditional **FPV-racing, freestyle and manual-performance** choice: extensive tuning and black-box logging are strengths, while autonomous missions are weak; payload or research use is conditional on GPS Rescue and sufficient position/status data [122][123]. iNAV favors **navigation, long-range and fixed-wing** missions with waypoints and Return-to-Home, but offers less complex-mission customization and less performance tuning than Betaflight [122]. For either project, first establish the use case, vehicle and team’s technical comfort [122].

PX4 (2024-12-31): Companion Computer Support—Strong (MAVLink/uXRCE-DDS; 2-Hz offboard) [93][186]; ROS Integration Level—Moderate/Strong (ROS 2/uORB; compatibility caveat) [93][207]; MATLAB/Simulink Support—Not established [230]; SITL/HITL Simulation Support—Strong (SITL computer, HITL board) [203]; Most Suitable Scenarios—conditional robotics/autonomy/research/simulation [203].

PX4: v1.14.3 (24 May 2024) [175]; ROS 2 **Moderate**—XRCE-DDS/uORB+MAVROS; Linux/Ubuntu 20.04 [200]; MATLAB/Simulink **Strong**—codegen/deploy/tuning, but blocks lack plant/HIL/MAVLink [336][180]; SITL/HITL **Strong**—computer/hardware, Gazebo lockstep; HITL version-sensitive [56][210]; fit: research/simulation, autonomy, mapping/payloads [56][337]; broad, hardware/version-dependent [213][210]. Paparazzi: companion **Moderate**—Copilot/PPRZLINK control, but board/mapping/trust-limited [96][313]; MATLAB **Limited**—NatNet bridge, depth unclear [308]; SITL/HITL **Moderate**—NPS/JSBSim/HITL, currency unclear [311][232]; best for scientific meteorology, multi-UAV, mapping/vision/survey; flexible; UDP/Bluetooth/MAVLink, but RTOS/GCS caveats [233][311].

**Paparazzi (2024-12-31):** Companion **Moderate**—Gumstix SBC control/payload integration; offboard maturity unclear [68]. ROS **Limited–Moderate**—ROS/FlightGear and Gazebo bridges, but no ROS2 or maintenance evidence [312][338]. MATLAB/Simulink **Limited–Moderate**—NatNet via UDP/Ivy, not native tooling [97][316]. SITL/HITL **Strong**—NPS/`sim` and real-controller HITL; setup/version caveats [339][231][340]. Scenarios: research/education, custom autonomous aircraft, survey/payloads; flexible but configuration-heavy [68][310].

**LibrePilot (2024-12-31):** Companion **Not established**—GCS and ROS/HITL links, no distinct companion workflow [53][235]. ROS **Limited**—ROS package/ROSBridge, without established official maintenance or ROS2 [245][234]. MATLAB/Simulink **Not established**—MATLAB outputs, no Simulink workflow [318]. SITL/HITL **Moderate**—Linux `simposix` and GCS/HITL bridge; dated completeness unresolved [53][258]. Scenarios: research/education, stabilization and robotics; UAVObjects/PathPlanner enable GPS autonomy, but calibration, tuning and CC3D limits decide fit [320][222].

LibrePilot: companion/ROS **Not established**—GCS, MSP/MAVLink do not establish either integration [217][319]; MATLAB/Simulink **Limited**—historical MATLAB import/Makefile target, no full Simulink/2024 snapshot [101][59]; SITL/HITL **Limited**—Linux-only SimPosix and FlightGear/X-Plane/UDP HITL, but broken hitl/sitl/crash [236][246][101]. Scenarios: model aircraft, multirotor/fixed-wing, robotics/R&D, camera work; developer Revo and conflicting watercraft reports qualify fit [217][101][322].

Betaflight: companion **Moderate**—CRSF telemetry and MSP_OVERRIDE/UART control, conditional on build/CLI, bandwidth and failsafe [105][325][330]; ROS **Limited**—experimental ROS 2 vehicle_gateway/joystick-SITL; bridge one commit/no releases [342][331][343]; MATLAB/Simulink **Limited**—MATLAB logs, modified Betalink only [238][327][328]; SITL/HITL **Limited**—Gazebo/UDP SITL, v4.5.0 (2024-04-28), HITL feature request [324][326][344]. Best fit: FPV racing/freestyle/cinematic multirotors, not dependable waypoint autonomy [223][247][72][305].

iNAV companion support: **Limited**; official Configurator/radio telemetry exist, but MSP/UART control is only a tested report [221][325].

iNAV’s core context is C with a cooperative scheduler and GPL-3; the evidence identifies a JavaScript-based Programming Framework/logic-condition workflow, while primary paths include MSP/MSP2, MAVLink, SmartPort, FPort, LTM and CRSF [65][243][107][334]. ArduPilot has at least ten GCS choices, with APM Planner 2 and AndroPilot caveats; PX4 supports local offline log analysis [126][219]. Paparazzi’s core is GPL-2-or-later and Etherlink GPL-3; Android “Paparazzi” pages are unrelated UI software [228][314][315][241]. LibrePilot’s CC3D evidence is anecdotal [341]. Betaflight’s app supports several aircraft and cross-platform Lua/BlackBox tools, but its master build is testing-only [244][225].

ArduPilot’s MAVLink/GCS and companion-computer paths support mission control and autonomy, while SITL exposes failure behavior; check vehicle, board/runtime, and simulated-versus-flight conditions because the initial ChibiOS targets were board-specific and the GPS-failsafe result was simulated [142][132][127]. PX4’s uORB/DDS and MAVLink explain its ROS/offboard ecosystem; Paparazzi’s ChibiOS kernel/HAL and branch architecture explain I/O and target differences; LibrePilot’s bound OPLink/Bluetooth path explains telemetry/control but depends on wiring and range; Betaflight’s FPV fit depends on CPU/flash and target maintenance; and iNAV’s Mavlink/SITL-HITL path depends on release, board, and sensor-plugin conditions [194][73][74][260][259][252][242][300][263][279].

Part One facts that must feed the ratings are execution model and protocol scope: ArduPilot’s ChibiOS target caveat and MAVLink/MSP, PX4’s NuttX and uORB/DDS/MAVLink, Paparazzi’s ChibiOS/scheduler and architecture branch, LibrePilot’s GCS/UAVTalk/OPLink, Betaflight’s scheduler/serial protocols and hardware-resource limits, and iNAV’s scheduler plus release/board constraints [132][191][194][74][260][283][252][250][263]. Keep provenance visible rather than treating these as universal: Paparazzi’s v6 branch changes targets, LibrePilot’s cited stable line is 16.09, Betaflight support is manufacturer/target-dependent, and iNAV’s cited evidence includes a release candidate and an F411 boundary; PX4’s BSD-versus-ArduPilot GPL distinction also changes commercial interpretation [74][269][252][277][263][280].

ArduPilot’s principal comparative advantage is breadth: many vehicle types, broad hardware choice, GCS/documentation, and ROS/SITL/Simulink paths support mixed fleets, mapping, autonomy, and research [122][171][134][147][168]. Its trade-offs are less emphasis on advanced autonomy and implementation conditions—ROS support is still being improved and the Simulink path is a software-in-the-loop integration—so it is a conditional broad-fleet choice rather than a universal winner [122][147][168].

### Companion computers and ROS integration

**ArduPilot and PX4 lead this comparison.** Both provide explicit paths for an onboard computer to exchange vehicle data and commands with the flight controller. ArduPilot’s documentation gives examples such as using GPS information to trigger a photograph or operate an auxiliary interface. PX4 documents serial and network connections together with higher-level MAVSDK and ROS 2 approaches. [10] · [11]

**Their advantage is more than connectivity.** Almost any embedded controller can potentially exchange bytes with another computer. The more consequential questions are whether the messages expose the required vehicle state, whether the commands have useful semantics, and whether existing software understands both. A documented vehicle API reduces the amount of custom protocol and state-management code that your project must own.

**PX4 provides a direct robotics route.** Its uXRCE-DDS integration connects selected internal topics to the DDS ecosystem used by ROS 2. This reduces the need to translate every useful data item into an unrelated application protocol. The v1.14 release explicitly describes shared message definitions, while v1.15’s experimental interface library aims to simplify higher-level control. [15] · [29]

**ArduPilot’s MAVROS route remains useful.** MAVROS translates MAVLink traffic into ROS topics and services. The documented example includes receiving autopilot information and changing vehicle mode, making it a real control integration rather than a telemetry-only display. The Moderate rating reflects this bridge-oriented workflow; it is not a claim that ArduPilot is unsuitable for robotics. [14]

**Direct integration also brings version coupling.** PX4’s v1.14 migration required a new agent, matching message definitions and adjustments to topic names and quality-of-service settings. “Quality of service” here means the message-delivery behavior expected by the communicating components. A native bridge can provide better structural integration while still requiring careful version alignment. [15]

**Paparazzi offers a different trade-off.** Its architecture explicitly supports an embedded companion computer, and its interface tutorial describes direct serial communication with a dedicated onboard board. That is meaningful support. However, a ROS application designed around PX4 topics or MAVLink messages would need an adaptation layer to speak Paparazzi’s PPRZLINK messages and interact with its operating model. [7] · [33]

**Channel injection is a narrower interface.** Betaflight’s MSP override work supports external interaction at the RC-channel level. That can be useful for experiments, but the external program may have to decide the roll, pitch, yaw and throttle commands that a higher-level autopilot interface would otherwise help manage. This is why the companion rating is Moderate while the ROS rating remains a custom-integration estimate. [37]

**Telemetry alone does not establish autonomy.** iNAV’s mission-oriented MSP interface can support substantial ground interaction, while LibrePilot’s UAVTalk objects can expose structured vehicle information. But receiving a position estimate is not the same capability as supplying a navigation target, managing a mission or handling loss of external control. The proposed custom-bridge work must preserve those distinctions rather than simply rename messages. [13] · [4]

**Your requirement changes the preferred route.** For a new ROS 2 research platform, PX4 is the first candidate. For a vehicle-centric application using MAVLink, onboard Lua and a companion for selected high-level tasks, ArduPilot is equally serious. Paparazzi becomes more attractive when its custom messages and ground architecture are already part of the research environment.

**Takeaway: choose the external control abstraction you need—not merely a controller with a spare serial port.**

### MATLAB and Simulink workflows

**PX4 has the stronger integrated workflow.** By 2024, MathWorks documented a support package covering PX4 firmware integration, hardware targets and generated-code workflows. R2024a added support for PX4 firmware v1.14 and code generation for Cube Orange Plus and Pixhawk 6c. R2024b added a PX4 Actuator Write block for PWM and UAVCAN outputs. These are concrete development capabilities, not just the ability to read a log file. [28]

**ArduPilot earns a different rating.** Its relevant 2024 baseline combines community MATLAB/Simulink coupling with official MATLAB log-analysis support. The ArduPilot community workflow uses a modified TCP/UDP/IP toolbox compiled as a MEX interface; MathWorks’ R2024a notes add import of ArduPilot Dataflash `.bin` logs and the `ardupilotreader` object. This justifies Moderate support without treating all integration tasks as equivalent. [46] · [28]

**There are several distinct support levels.** “Works with MATLAB” can mean analyzing recorded data, exchanging live messages, connecting a simulated aircraft model or generating deployable controller code. A project may need only the first of these, while a controls-research laboratory may require the last. The relevant support question must therefore be stated as a workflow.

| MATLAB/Simulink activity | What it provides | Strongest practical fit here |
|---|---|---|
| Analyze recorded flight data | Inspect behavior and diagnose a flight | PX4 and ArduPilot |
| Exchange data with a running autopilot | Monitor or command through an interface | PX4; ArduPilot community coupling |
| Connect an aircraft dynamics model | Test controller/model interaction | PX4; custom interfaces for other stacks |
| Generate and deploy controller code | Put model-derived algorithms into firmware | PX4’s established support-package workflow |

**Code deployment changes the development burden.** A supported code-generation path connects model design to a known toolchain and target configuration. A custom socket or protocol interface is more flexible in principle, but your team must define signal mapping, execution timing and the relationship between the model and the flight software. For a beginner, that distinction can be more important than whether the flight firmware itself is C or C++.

**A named study illustrates the mechanism.** The 2024 paper *Development of SITL & HITL System based on PX4-Matlab for VTOL Test* proposed a PX4–MATLAB/Simulink simulation approach and applied it to the LC-62 VTOL aircraft. Its motivation was not that Gazebo was generally unusable, but that unusual aircraft configurations can be difficult to model faithfully and that separate simulation and operational implementations can duplicate development effort. [47]

**Model fidelity remains a separate problem.** A well-integrated support package cannot supply accurate aerodynamics, actuator behavior or sensor behavior for every custom aircraft automatically. The same study specifically identifies differences between simulation and actual operation when component models lack fidelity. PX4’s tooling advantage reduces integration work; it does not remove the engineering work needed to construct an appropriate aircraft model. [47]

**Other projects remain custom-interface options.** Paparazzi’s PPRZLINK libraries, LibrePilot’s structured objects, and Betaflight/iNAV’s MSP interfaces provide possible boundaries for a MATLAB application. The Limited planning ratings mean that the project should own the adapter, data mapping and test arrangement. They do not mean that exchanging data with MATLAB is technically impossible.

**Folder names are not deployment workflows.** LibrePilot’s repository includes MATLAB-related resources, but that alone should not be treated as equivalent to a supported Simulink target, generated-code integration or a complete HITL workflow. The same principle applies to a Python or JavaScript tool found around any autopilot: the existence of code in a language does not define the scope of supported development. [4]

**Toolchain constraints can decide the choice.** If your project already owns MATLAB/Simulink licenses, uses compatible flight hardware and plans to develop control algorithms in models, PX4 is the clearest starting point. If MATLAB is needed mainly for analyzing flights or connecting a custom model, ArduPilot remains a practical alternative. The support-package version, firmware version and target board must be selected as one compatible combination.

**Takeaway: distinguish log analysis and custom coupling from a supported model-to-firmware deployment path; PX4 leads the latter through 2024.**

### SITL and HITL simulation support

**PX4 and Paparazzi explicitly cover both modes.** PX4 documents SITL and HITL environments, while Paparazzi’s NPS module binds embedded autopilot code to a flight-dynamics model and explicitly selects SITL or HITL. ArduPilot has particularly extensive SITL capabilities. Betaflight and iNAV also have pre-2025 software-simulation evidence, so describing either specialist as having “no simulation” would be incorrect. [17] · Paparazzi NPS modes [45] · ArduPilot SITL [16] · Betaflight 4.5.0 [37] · [44]

**SITL is usually the starting point.** It runs without a flight-controller board, supports ordinary development tools and makes repeated tests easier to arrange. ArduPilot’s SITL is a native executable built with an ordinary C++ compiler. It can use built-in vehicle physics or connect to external models, and its documentation identifies interactive debugging and analysis tools as major advantages. [16]

**ArduPilot’s software simulation is broad.** Its documented simulation scope includes aircraft, ground and underwater vehicles, gimbals, trackers and optional sensors. External physics can be supplied through JSBSim or a JSON interface, with examples including Gazebo and Webots; FlightGear can provide visualization. This is an excellent fit for checking mission behavior and custom software before flying. [16]

**The combined rating reflects hardware-loop requirements.** ArduPilot’s Moderate SITL/HITL rating should not be read as a Moderate rating for SITL alone. A Blue Robotics discussion concerning ArduSub described hardware-loop work as substantial and older HITL instructions as archived. That narrower, community discussion is a reason to treat a required hardware-loop configuration as a separate project decision—not proof that every conceivable ArduPilot hardware simulation is impossible. [48]

**PX4’s hardware loop has explicit structure.** In the documented arrangement, the simulator runs on a development computer and exchanges data with the flight controller through USB/UART, with MAVLink connections also reaching QGroundControl. The guide identifies multicopter and VTOL configurations. This gives a more concrete starting point when testing on the actual controller is mandatory. [17]

**HITL is not automatically more complete.** PX4 explains that HITL modes bypass some normal functionality in core modules, whereas SITL executes more of the normal system code apart from its simulated drivers. The guide also describes HITL as community-supported and version-sensitive. Its Strong rating reflects the explicit tooling and architecture, not a guarantee that arbitrary firmware, boards and simulator releases work together unchanged. [17]

**Paparazzi makes the mode choice explicit.** NPS supports JSBSim or CRRCSIM flight-dynamics models and provides `USE_HITL=0` for the default software loop and `USE_HITL=1` for a hardware loop. That clear configuration boundary is valuable for research that needs to move between host execution and controller-connected experiments. The suitability of the chosen vehicle model remains part of the experiment. [45]

**Betaflight has release-level SITL evidence.** Its 4.5.0 release specifically includes “Added SITL Gazebo,” alongside other software-simulation changes. This supports using Betaflight in firmware-development experiments without treating a pilot-training simulator as the only option. It does not turn the 2024 release into a general mission-autonomy platform merely because the firmware can be connected to simulated physics. [37]

**iNAV also has a software-loop baseline.** The 7.1.0 release includes SITL-related work and a RealFlight fix, providing a stronger pre-2025 anchor than relying solely on a later community-plugin description. The Moderate rating credits that software simulation while treating hardware-loop arrangements as specialized. Its navigation focus makes this useful for checking aircraft behavior and configuration, provided the simulated model is appropriate. [44]

**LibrePilot calls for a project-specific budget.** Its Limited planning rating means that controller/simulator coupling should be treated as part of the selected setup, rather than as an assumed broad research environment. An existing LibrePilot simulation installation can change that practical balance substantially. For a new project where portable, repeatable simulation is a mandatory deliverable, the explicitly documented ArduPilot, PX4 and Paparazzi routes provide clearer starting points.

**Pilot simulation tests a different system.** A simulator used to practice stick control may model an aircraft without executing the actual autopilot firmware. That can be excellent training, but it does not test your modified estimator, protocol client or mission logic. The relevant question is whether the component you intend to validate is actually inside the simulation loop.

**Simulation needs a specific purpose.** For mission logic and interface development, SITL may be enough. For controller-board interaction or resource-sensitive integration, hardware participation becomes more important. For a novel VTOL configuration, model fidelity may dominate both choices. The best simulator arrangement is the one that exercises the failure or behavior your project needs to understand.

**Takeaway: prefer ArduPilot for broad SITL, PX4 or Paparazzi for explicit dual-mode workflows, and specialist simulation where the specialist firmware is itself the test subject.**

### Communication and ground-tool compatibility

**Message coverage matters more than protocol names.** Two autopilots can both advertise MAVLink while implementing different commands, mission operations or parameter services. The historical iNAV guide provides a concrete counterexample: its MAVLink path supported monitoring, while MSP handled mission-related interaction. Counting both as identical “MAVLink support” would hide a decision-relevant difference. [13]

**ArduPilot exposes a broad vehicle interface.** Its MAVLink documentation covers commands, modes, parameters, missions, cameras, gimbals and other integration tasks, with vehicle-specific message lists explicitly referenced to November 2024. That breadth makes it useful when a ground application must do more than display location and battery information. [22]

**PX4 combines two external integration styles.** MAVLink supports conventional vehicle and ground-station interaction, while the ROS 2 bridge provides topic-oriented access to selected flight-system data and commands. A developer should choose the abstraction that matches the external application rather than assume one must always replace the other. The same vehicle can have a ground-station workflow and a robotics workflow serving different users. [27] · [15]

**Paparazzi and LibrePilot are coherent alternatives.** PPRZLINK and UAVTalk are not inherently inferior because they differ from MAVLink. Their value comes from how closely the aircraft, ground software and configuration data fit together. The trade-off appears when an external tool assumes MAVLink-specific messages or services and therefore requires an adapter.

**MSP supports real development interfaces.** Betaflight documents firmware identification, mode-range reading and writing, adjustment ranges and other tool-facing operations. Those interfaces are useful for custom configuration utilities and integration tests. They also demonstrate why an external client must respect the protocol’s actual structure instead of assuming every configuration object has a fixed size. [40]

**Radio behavior can influence responsiveness.** iNAV’s mission guide contrasts MSP’s request/response polling with LTM’s unsolicited, or “push,” telemetry. On a half-duplex link—one that alternates between transmitting and receiving—repeated direction changes can impose a cost. The guide describes using MSP for configuration and mission transfer, then LTM for flight monitoring, illustrating how complementary protocols can solve different parts of the workflow. [13]

**Component protocols answer another question.** DShot concerns commands to ESCs; DroneCAN concerns networked components; receiver protocols concern the pilot’s radio link. None is a substitute for a ground-station mission protocol. When selecting hardware, first identify the device’s role, then confirm the appropriate bus, electrical interface and firmware support.

**Takeaway: validate the exact operation your external system needs—mission upload, parameter access, setpoints or telemetry—not just a matching protocol acronym.**

### Application fit and each project’s trade-off

**General autonomy favors broad stacks.** ArduPilot and PX4 both cover multiple vehicle classes and provide substantial integration surfaces. ArduPilot’s advantage is particularly clear when the project combines existing autonomous vehicle functions, varied peripherals and onboard Lua. PX4’s advantage becomes more pronounced when the project’s center of gravity is modular robotics software, ROS 2 or model-based control development. [1] · [2]

**Research does not imply one winner.** Paparazzi can be especially suitable when the experiment involves custom flight plans, new airframes, distributed ground applications or close control over module scheduling. PX4 can be preferable when the experiment builds on a wider ROS-based robot system. ArduPilot can be preferable when the research needs an existing vehicle implementation and wants to concentrate on a payload or external algorithm rather than the flight core.

**Institutional expertise is a real asset.** A laboratory with Paparazzi configurations, experienced users and existing PPRZLINK tools may face less work extending that system than migrating to a nominally broader ecosystem. The same reasoning applies to a LibrePilot-based teaching or vehicle-control platform. Existing working code and aircraft knowledge can outweigh a generic feature comparison.

**FPV priorities favor Betaflight.** A racing or freestyle aircraft is primarily a human-controlled dynamic system: the pilot’s input, filtering, control response, motors and display workflow are central. Betaflight’s software and release changes directly address those activities. Adding a broad mission architecture does not automatically improve that project, and may introduce concepts that its user does not need. [5] · [37]

**Navigation-equipped RC flight favors iNAV.** A flying wing needing return-to-home, waypoint missions and automatic landing has a different requirement set from a racing quad. iNAV’s fixed-wing navigation and 7.1 automatic-landing features directly match that need. Its narrower external robotics integration is a trade-off only if the project also requires sophisticated external autonomy. [6] · [44]

**LibrePilot benefits from a concrete fit.** Its stated control-and-robotics scope is broad, but that alone is not a reason to select it over a documented PX4 robotics workflow or an ArduPilot mission workflow. Its strongest case is a compatible existing vehicle, controller, extension or development environment. The trade-off is accepting its object/protocol model when wider interoperability is a central requirement. [4]

**Vehicle physics still govern the application.** For surveying, a fixed-wing aircraft may offer longer and faster coverage, while a multirotor can hover and inspect a vertical structure slowly. PX4’s guide makes this distinction explicitly. Autopilot selection should follow the actual flight task, not compensate for choosing an unsuitable aircraft configuration. [27]

**A return function is not complete safety.** Navigation and rescue behavior depends on configuration and valid state information. iNAV’s compass-free navigation conditions provide a concrete example: a valid GPS-derived heading must be acquired before relevant modes become operational. The practical implication is to select sensors and operating procedures together with the advertised flight mode. [44]

**Takeaway: match the stack to the aircraft’s main job before comparing optional ecosystem features.**

### Licensing and hardware constraints

**BSD and GPL support different choices.** PX4’s permissive BSD 3-Clause license is attractive when proprietary firmware modifications or incorporation into a closed product are important. GPL-family projects are also compatible with commercial use, but redistribution of covered software brings corresponding obligations. “Commercial” and “closed source” are not interchangeable categories. [31] · [23]

| Code-license baseline | Projects | Main selection implication |
|---|---|---|
| BSD 3-Clause | PX4 | Permissive incorporation and proprietary modification |
| GPLv3 family | ArduPilot, LibrePilot, Betaflight, iNAV | Preserve applicable source and redistribution obligations |
| GPLv2 family with mixed components | Paparazzi | Track parent-code and library-specific conditions |

**GPL does not require every private change online.** The practical issue is compliance when distributing covered software, including the corresponding source and other applicable license requirements. That is different from a blanket obligation to publish every internal experiment or submit every change upstream. ArduPilot’s own guidance distinguishes customer source obligations from its request that useful improvements be contributed to the project. [23]

**A companion can separate product layers.** ArduPilot explicitly describes using closed-source software on a companion computer for higher-level functions. A company can therefore keep proprietary mission or perception software separate from GPL flight firmware, while complying with the obligations of any covered firmware it distributes. This can materially change a license-driven comparison between ArduPilot and PX4. [23]

**Hardware licenses must be considered separately.** LibrePilot’s inherited notices identify some hardware materials under a noncommercial license; PX4’s license page separately identifies Pixhawk hardware and documentation terms. Neither statement means that every controller sold for the corresponding firmware has one identical hardware license. Reusing an open hardware design and installing firmware on a purchased controller are different activities. [36] · [30]

**Board resources can override software preference.** ArduPilot’s Lua requirements can eliminate an otherwise compatible controller from a scripting-heavy project. iNAV’s INAV 7/F411 support boundary can make a low-cost existing board a poor basis for a project expecting later firmware migration. These are concrete constraints, not minor specification details. [21] · [44]

**Tool support is also board-specific.** MathWorks’ R2024a release names particular PX4 targets and firmware compatibility. A board’s ability to run PX4 does not automatically establish that every Simulink peripheral block or deployment workflow has the same support on that board. When model-based development is mandatory, the supported combination is the product you are effectively selecting. [28]

**Takeaway: select a firmware–board–toolchain combination whose licensing and resources match the project, rather than choosing those pieces independently.**

### Which should you select for a typical project?

**For an unspecified autonomous drone, shortlist two.** Begin with ArduPilot and PX4. Both provide a broad foundation, so the deciding factors should be the vehicle, the extension layer, the external software and the license—not a speculative overall score. Paparazzi, LibrePilot, Betaflight and iNAV become first choices when their particular architecture or application focus matches the project.

| Project requirement | First candidate | Alternative worth considering | Deciding condition |
|---|---|---|---|
| Autonomous mapping with custom payload actions | ArduPilot | PX4 | Lua/vehicle features versus robotics integration |
| ROS 2 perception and planning | PX4 | ArduPilot | Native topic bridge versus MAVLink/MAVROS workflow |
| Simulink-developed controller | PX4 | ArduPilot | Deployment tooling versus custom simulation coupling |
| Custom research aircraft and ground tools | Paparazzi | PX4 or ArduPilot | Existing lab expertise and required interfaces |
| FPV racing or freestyle | Betaflight | iNAV | Piloting performance workflow versus navigation needs |
| RC flying wing with missions and landing | iNAV | ArduPilot | Specialist navigation versus broader autonomy |
| Existing LibrePilot vehicle or codebase | LibrePilot | ArduPilot or PX4 | Value of reuse versus cost of new integrations |

**A mapping aircraft illustrates ArduPilot’s appeal.** Suppose the drone must follow a mission, trigger a camera at appropriate locations and operate a custom payload. ArduPilot’s MAVLink interface, broad vehicle functions and Lua extension layer align well with that combination. A companion computer becomes useful if image processing or more complex planning is added, rather than being required merely to express every small custom behavior. [10] · [21]

**A robotics aircraft illustrates PX4’s appeal.** Suppose the main research work involves ROS 2 perception, localization and trajectory generation. PX4’s native topic bridge provides a more direct architectural fit, with simulation and modular control development supporting the same workflow. ArduPilot remains an alternative when its vehicle functions or MAVLink-centered software are more valuable than direct ROS-topic integration. [15] · [14]

**A controls laboratory favors explicit tooling.** If a controller is being designed in Simulink and the result must be deployed to supported flight hardware, PX4’s 2024 support package is a decisive advantage. If the experiment instead concerns connecting an existing autopilot to a custom dynamics model, both PX4 and ArduPilot remain plausible. Paparazzi becomes especially interesting when the laboratory wants deeper control over generated configuration and flight-system modules. [28] · ArduPilot MATLAB interfaces [46] · [32]

**A racing quad needs fewer abstractions.** If a pilot will fly the aircraft and autonomous navigation is not the project’s central purpose, Betaflight is the first candidate. Its filtering, tuning, logging and peripheral workflow address that use directly. The recommendation changes toward iNAV when position hold, waypoint missions or fixed-wing navigation become defining requirements, rather than optional additions. [5] · [6]

**A navigation wing highlights iNAV’s niche.** A fixed-wing RC project needing return-to-home, missions and automatic landing has a clear specialist candidate in iNAV. ArduPilot becomes more attractive when the same project also needs extensive payload integration, a broader mission system or a substantial companion-computer application. The distinction is not whether both can fly a wing, but which software architecture best matches the rest of the project. [44] · [22]

**Existing expertise can change the answer.** A working Paparazzi or LibrePilot platform should not be discarded solely because PX4 and ArduPilot have broader general-purpose integration paths. Reusing an aircraft configuration, proven wiring, data tools and team knowledge can reduce the scope of the project. Migration is most compelling when a mandatory capability fits another stack’s established interface much better.

**The final conditions are concrete.** Vehicle type, mandatory navigation modes, companion-computer requirements, ROS generation, Simulink deployment needs, the required simulation loop, onboard customization and redistribution constraints decide the final choice. These are design inputs, not performance numbers to invent or replace with a universal ranking.

**These are integration judgments, not benchmarks.** The report’s time boundary is 31 December 2024; release-specific dates take precedence over timestamps on continuously updated pages. RTOS labels describe the relevant controller target, language labels describe flight firmware rather than whole-repository percentages, and scripting is separated by execution location. Asterisked ratings are conservative planning estimates based on the stated protocol/interface work; they are not measured capability scores or claims that other integrations are absent.

**The practical starting choice is straightforward.** Choose ArduPilot for a broad autonomous vehicle with practical onboard customization; choose PX4 when ROS 2, modular robotics development or Simulink deployment is the project’s defining requirement. Choose a specialist when its particular flying or development workflow is the reason for building the drone.

## References

[1] <https://ardupilot.org/dev/> ArduPilot development overview; ArduPilot language description; ArduPilot development tools; ArduPilot scope
[2] <https://docs.px4.io/main/en/concept/architecture> PX4 architecture; PX4 runtime environments; PX4 uORB architecture; PX4 module execution; PX4 development architecture
[3] <https://github.com/paparazzi/paparazzi> Paparazzi project overview; Paparazzi repository and license files
[4] <https://github.com/librepilot/LibrePilot> LibrePilot project description; LibrePilot flight-software repository; LibrePilot flight and ground source; LibrePilot source and extension modules; LibrePilot…
[5] <https://github.com/betaflight/betaflight> Betaflight project overview; Betaflight project interfaces; Betaflight features
[6] <https://github.com/iNavFlight/inav> iNAV project; iNAV feature overview; iNAV firmware repository; iNAV firmware source; iNAV repository and license; iNAV navigation features
[7] <https://paparazzi-uav.readthedocs.io/en/latest/developer_guide/system_overview.html> Paparazzi system architecture; Paparazzi low-level architecture; Paparazzi system configuration; Paparazzi ground architecture; Paparazzi ground-segment design…
[8] <https://github.com/betaflight/betaflight/blob/master/src/main/fc/tasks.c> Betaflight task organization
[9] <https://discuss.px4.io/t/px4-chibios-portd/5821> PX4 architectural discussion
[10] <https://ardupilot.ardupilot.org/dev/docs/companion-computers.html> ArduPilot companion computers; ArduPilot companion interface; ArduPilot companion applications; ArduPilot companion examples
[11] <https://docs.px4.io/main/en/companion_computer/pixhawk_companion> PX4 companion connections; PX4 companion setup
[12] <https://arxiv.org/pdf/1906.10641> MAVLink technical overview
[13] <https://www.rcgroups.com/forums/showatt.php?attachmentid=11240545&d=1538097119> iNAV mission and telemetry guide; Transmitter and telemetry arrangements; iNAV mission and protocol guide; iNAV ground-station and telemetry guide; iNAV missio…
[14] <https://en.ardupilot.org/dev/docs/ros-sitl.html> ArduPilot ROS example; ArduPilot ROS-with-SITL example; ArduPilot ROS bridge example
[15] <https://px4.io/px4-autopilot-release-v1-14-what-you-need-to-know/> PX4 v1.14 ROS 2 bridge; PX4 v1.14 release summary; PX4 v1.14 ROS 2 architecture; PX4 migration requirements; PX4 ROS 2 bridge; PX4 ROS 2 architecture
[16] <https://ardupilot.org/dev/docs/sitl-simulator-software-in-the-loop.html> ArduPilot SITL overview; ArduPilot SITL architecture and benefits; ArduPilot supported simulation arrangements
[17] <https://docs.px4.io/main/en/simulation/hitl> PX4 SITL/HITL distinction; PX4 simulation environments; PX4 HITL architecture and airframes; PX4 HITL versus SITL
[18] <https://github.com/ArduPilot/ardupilot_wiki/blob/master/dev/source/docs/learning-ardupilot-introduction.rst> ArduPilot code organization; ArduPilot hardware-abstraction layers; DroneCAN and external support code
[19] <https://discuss.ardupilot.org/t/why-not-freertos/106060> ESP32 FreeRTOS discussion
[20] <https://forum.chibios.org/viewtopic.php?t=4521> ArduPilot’s NuttX-to-ChibiOS transition
[21] <https://ardupilot.org/copter/docs/common-lua-scripts.html> ArduPilot Lua scripting; Lua scheduling behavior; Lua hardware requirements; ArduPilot scripting; ArduPilot Lua requirements
[22] <https://ardupilot.org/dev/docs/mavlink-commands.html> ArduPilot MAVLink interface; ArduPilot MAVLink services; ArduPilot interfaces
[23] <https://www.ardupilot.ardupilot.org/dev/docs/license-gplv3.html> ArduPilot GPL license; ArduPilot commercial-use guidance; ArduPilot license guidance; ArduPilot proprietary-companion example
[24] <https://ardupilot.org/dev/docs/porting.html> Firmware customization terms
[25] <https://github.com/px4/px4-autopilot> PX4 project overview
[26] <https://docs.px4.io/main/en/contribute/code> PX4 source-code conventions
[27] <https://docs.px4.io/main/en/getting_started/px4_basic_concepts> PX4 external development interfaces; PX4 companion-computer concepts; PX4 MAVLink and companion interfaces; PX4 communication concepts; PX4 vehicle-type guidan…
[28] <https://ww2.mathworks.cn/help/uav/release-notes.html> MathWorks R2024b actuator support; MathWorks R2024a and R2024b release notes; MathWorks R2024a ArduPilot log support; MathWorks R2024a PX4 support; MathWorks 2…
[29] <https://px4.io/px4-autopilot-release-v1-15-what-you-need-to-know/> PX4 v1.15 release summary; PX4 v1.15 interface library
[30] <https://docs.px4.io/main/en/contribute/licenses> PX4 component licenses; PX4 component licensing
[31] <https://px4.io/software/software-overview/> PX4 proprietary-use explanation; PX4 licensing explanation
[32] <https://comp4drones.github.io/Component_repository/enabling_technologies/WP3/ENAC_paparazzi/> Paparazzi architecture and applications; Paparazzi generated-code architecture; Paparazzi module architecture
[33] <https://paparazzi-uav.readthedocs.io/en/stable/tutorials/interfacing_with_paparazzi.html> Paparazzi interfacing tutorial; Paparazzi extension approaches; Paparazzi extension paths; Paparazzi direct interfaces
[34] <https://github.com/paparazzi/pprzlink> PPRZLINK libraries; PPRZLINK message classes
[35] <https://github.com/librepilot/LibrePilot/blob/next/LICENSE.txt> LibrePilot license
[36] <https://github.com/librepilot/LibrePilot/blob/next/legacy_openpilot_license.txt> Inherited hardware and documentation notices; LibrePilot inherited notices
[37] <https://github.com/betaflight/betaflight/releases/tag/4.5.0> Betaflight 4.5.0 release; Betaflight 4.5.0 MSP changes; Betaflight 4.5.0 release changes; Betaflight 4.5.0 MSP override changes; Betaflight 4.5.0 simulation ch…
[38] <https://github.com/betaflight/betaflight/blob/master/src/main/fc/core.c> Betaflight firmware source; Betaflight license header
[39] <https://betaflight.com/docs/development> Betaflight development and testing
[40] <https://betaflight.com/docs/development/API/MSP-Extensions> Betaflight MSP extensions; Betaflight MSP API
[41] <https://betaflight.com/docs/category/api> DShot’s component role
[42] <https://github.com/iNavFlight/inav-configurator?tab=readme-ov-file> iNAV Configurator
[43] <https://github.com/iNavFlight/inav/blob/master/docs/Programming%20Framework.md> iNAV Programming Framework; Programming Framework behavior
[44] <https://github.com/iNavFlight/inav/releases/tag/7.1.0> iNAV 7.1.0 component requirements; iNAV 7.1 navigation requirements; iNAV 7.1.0 release; iNAV 7.1.0; iNAV 7.1.0 SITL and RealFlight changes; iNAV 7.1 automatic…
[45] <http://docs.paparazziuav.org/v5.16/module__nps.html> Paparazzi NPS configuration
[46] <https://ardupilot.org/dev/docs/sitl-with-MATLAB.html> ArduPilot MATLAB community resources
[47] <https://doi.org/10.5626/jok.2024.51.6.528> 2024 PX4–MATLAB VTOL study; LC-62 study’s modeling discussion
[48] <https://discuss.bluerobotics.com/t/hitl-regime-for-ardusub-on-pixhawk-platform/7792> ArduSub HITL discussion
[49] <https://online.prowingsafrica.com/wp-content/uploads/2023/05/Mission-Planner-Overview.pdf>
[50] <https://github.com/paparazzi/paparazzi>
[51] <https://github.com/ArduPilot/ardupilot>
[52] <https://ardupilot.org/dev/>
[53] <https://librepilot.atlassian.net/wiki/spaces/LPDOC/pages/100523730/LibrePilot+System+Architecture>
[54] <https://docs.px4.io/main/en/concept/architecture>
[55] <https://github.com/paparazzi/paparazzi/blob/master/doc/sphinx/source/developer_guide/system_overview.rst>
[56] <https://docs.px4.io/v1.16/en/simulation/>
[57] <https://en.ardupilot.org/plane/docs/common-autopilots.html>
[58] <https://leepike.github.io/pubs/embedded-experience.pdf>
[59] <https://github.com/librepilot/LibrePilot/blob/next/Makefile>
[60] <https://betaflight.com/docs/development>
[61] <https://github.com/betaflight/betaflight/blob/cc3f135e/src/main/fc/core.c>
[62] <https://github.com/ardupilot/ardupilot/blob/master/libraries/AP_Scripting/README.md>
[63] <https://ardupilot.org/ardupilot/docs/common-downloads_firmware.html>
[64] <https://wiki.paparazziuav.org/wiki/Pprzlink>
[65] <https://github.com/iNavFlight/inav/blob/master/AGENT.md>
[66] <https://docs.corewing.com/en/plane/inav/settings/rc/lua-setup.html>
[67] <https://paparazzi-uav.readthedocs.io/en/stable/tutorials/interfacing_with_paparazzi.html>
[68] <https://wiki.paparazziuav.org/wiki/Overview>
[69] <https://wiki.paparazziuav.org/w/images/0/0a/Users_manual.pdf>
[70] <https://betaflight.com/docs/wiki/getting-started/hardware/esc-firmware>
[71] <https://github.com/librepilot/LibrePilot>
[72] <https://betaflight.com/docs/wiki/tuning/4-3-Tuning-Notes>
[73] <https://wiki.paparazziuav.org/wiki/RT_Paparazzi>
[74] <https://blog.paparazziuav.org/2021/04/13/paparazzi-v5-18-is-out-v6-0-is-starting/>
[75] <https://github.com/paparazzi/paparazzi/releases/tag/v5.18.0_stable>
[76] <https://lists.libreplanet.org/archive/html/paparazzi-devel/2021-04/msg00001.html>
[77] <https://lists.libreplanet.org/archive/html/paparazzi-commits/2024-05/msg00036.html>
[78] <https://docs.paparazziuav.org/latest/main__bare_8c_source.html>
[79] <https://github.com/tudelft/paparazzi>
[80] <https://github.com/betaflight/betaflight-tx-lua-scripts/>
[81] <https://github.com/betaflight/betaflight-tx-lua-scripts/releases/tag/1.6.0>
[82] <https://github.com/iNavFlight/inav/blob/master/LICENSE>
[83] <https://librepilot.atlassian.net/wiki/spaces/LPDOC/pages/93945858/Extend+a+Flightcontroller+with+an+Arduino>
[84] <https://github.com/iNavFlight/inav/issues/1303?timeline_page=1>
[85] <https://docs.px4.io/v1.16/en/ros2/user_guide>
[86] <https://discuss.px4.io/t/programming-drones/30125>
[87] <https://github.com/ArduPilot/ardupilot/blob/Rover-4.5/Rover/ReleaseNotes.txt>
[88] <https://github.com/betaflight/betaflight/blob/master/src/main/fc/rc.c>
[89] <https://doi.org/10.1016/j.micpro.2018.05.002>
[90] <https://github.com/ArduPilot/ardupilot/blob/2c814e9de2a1f384f1c913365caee4889877c82c/libraries/GCS_MAVLink/GCS_Common.cpp>
[91] <https://microsoft.github.io/AirSim/px4_build/>
[92] <https://docs.px4.io/v1.16/en/companion_computer/>
[93] <https://docs.px4.io/v1.14/en/ros/ros2_comm>
[94] <https://docs.px4.io/main/en/contribute/licenses>
[95] <https://github.com/paparazzi/paparazzi/releases>
[96] <https://github.com/paparazzi/pprzlink/>
[97] <https://github.com/paparazzi/paparazzi/commit/905c9802235ba721e6d3835fe0bff9cc0e44ec0d>
[98] <http://recherche.enac.fr/~brisset/PascalBrisset_InfoIndustrielle_Paparazzi.pdf>
[99] <https://docs.paparazziuav.org/latest/mavlink_8c_source.html>
[100] <https://docs.paparazziuav.org/latest/onboard_modules.html>
[101] <https://github.com/librepilot/LibrePilot/blob/next/WHATSNEW.txt>
[102] <https://github.com/librepilot/LibrePilot/blob/next/legacy_openpilot_license.txt>
[103] <https://github.com/iNavFlight/inav/releases/tag/8.0.0-RC3>
[104] <https://github.com/betaflight/betaflight/blob/master/src/main/msp/msp_protocol.h>
[105] <https://betaflight.com/docs/wiki/guides/current/Telemetry>
[106] <https://github.com/betaflight/betaflight-configurator/blob/master/LICENSE>
[107] <https://github.com/iNavFlight/inav/blob/master/docs/Programming%20Framework.md>
[108] <https://github.com/iNavFlight/inav/blob/master/src/main/msp/msp_protocol.h>
[109] <https://www.ardupilot.org/>
[110] <https://www.youtube.com/watch?v=s-xxiiP7oik>
[111] <https://ardupilot.org/ardupilot/>
[112] <https://droneanalyst.com/2021/05/30/rise-of-open-source-drones/'>
[113] <https://ardupilot.org/dev/docs/using-sitl-for-ardupilot-testing.html>
[114] <https://icaerus.eu/hover-view-open-source-alternatives-in-drone-technology/>
[115] <https://www.sphengineering.com/news/using-ardupilot-px4-with-ugcs-flight-planning-software>
[116] <https://github.com/ArduPilot/ardupilot_ros>
[117] <https://doi.org/10.1186/s44147-025-00645-5>
[118] <https://www.aeroratech.com/guides/best-autonomy-software-stacks-for-drones/>
[119] <https://www.ardupilot.ardupilot.org/dev/docs/license-gplv3.html>
[120] <https://desosa.nl/projects/ardupilot/2020/03/06/uplink-to-ardupilot>
[121] <https://fadi-labib.github.io/bennu/decisions/001-px4-over-ardupilot/>
[122] <https://droniax.com/a-comprehensive-guide-to-open-source-flight-control-software-for-drones>
[123] <https://libdrone.eu/reference/platform-selection/>
[124] <https://www.projects-house.com/articles/drone-development/px4-vs-ardupilot/>
[125] <https://ask.ifas.ufl.edu/publication/AE576/pdf>
[126] <https://www.ardupilot.ardupilot.org/copter/docs/common-choosing-a-ground-station.html>
[127] <https://doi.org/10.1016/j.dib.2024.110069>
[128] <https://ardupilot.ardupilot.org/sub/docs/common-autopilots.html>
[129] <https://www.linkedin.com/posts/kiril-vardapetyan_dronedevelopment-uav-ardupilot-activity-7377205286270312448-Jghu>
[130] <https://dojofordrones.com/ground-control-stations/>
[131] <https://www.mathworks.com/matlabcentral/fileexchange/114315-ardupilot-software-in-the-loop-sil-connector-for-simulink>
[132] <https://discuss.ardupilot.org/t/chibios-port-of-ardupilot/20491/22>
[133] <https://www.youtube.com/watch?v=JnYfSnLEIr4>
[134] <https://www.mepsking.shop/blog/betaflight-ardupilot-inav-fc-firmware.html?srsltid=AU7gw4V-D6XmTTb2fC6nVG3Rx3kFh7QzfQ5gi3DyEF4AxBvxDzLjF6SI>
[135] <https://www.mepsking.shop/blog/betaflight-ardupilot-inav-fc-firmware.html?srsltid=AU7gw4UeqtVn7GAagAdQ_RX8cztmFky5MymZPiNfa_BMcop8xNUS246A>
[136] <https://discuss.ardupilot.org/t/ssh-into-companion-computer-over-telemetry/114126>
[137] <https://ardupilot.org/dev/docs/sitl-with-MATLAB.html>
[138] <https://www.mepsking.shop/blog/betaflight-ardupilot-inav-fc-firmware.html?srsltid=AU7gw4WIopdfHSyqIUdGGKfZUcVkZdb_vGt065YshsrX6jq85El8TNbc>
[139] <https://discuss.ardupilot.org/t/mavros-2-humble-jammy-jellyfish-ubuntu-22-04-64bit-pi4b-setup-build-warnings-4-tests-fail/110213>
[140] <https://research.tudelft.nl/en/publications/ardupilot-based-adaptive-autopilot-architecture-and-software-in-t/>
[141] <https://najafabadnews.ir/wp-content/uploads/2015/03/166-Build-your-own-quadrotorIEEE-IROREF.ir_.pdf>
[142] <https://ardupilot.github.io/MethodicConfigurator/TUNING_GUIDE_ArduCopter.html>
[143] <http://cse.unl.edu/~jbradley/CI/controlleridentification.html>
[144] <https://ardupilot.org/copter/docs/common-msp-overview.html>
[145] <http://github.com/ardupilot/ardupilot>
[146] <https://ardupilot.org/rover/docs/common-autopilots.html>
[147] <https://ardupilot.org/dev/docs/ros1.html>
[148] <https://github.com/Ardupilot/ardupilot/blob/master/Tools/ros2/README.md>
[149] <https://www.youtube.com/watch?v=Ewh0fKGEJL4&xstg=CAMSBhUDzO3xHw%3D%3D>
[150] <https://www.ardupilot.ardupilot.org/dev/docs/common-lua-scripts.html>
[151] <https://ardupilot.org/dev/docs/companion-computers.html>
[152] <https://github.com/ArduPilot/ardupilot/issues/10141>
[153] <https://github.com/ArduPilot/ardupilot_wiki/blob/master/plane/source/docs/ArduPlane_MAVLink_Messages.rst>
[154] <https://ardupilot.ardupilot.org/dev/docs/apsync-intro.html>
[155] <https://cloud.ardupilot.org/scenarios/de-scenarios.html>
[156] <https://blueos.cloud/docs/stable/integrations/hardware/required/onboard-computer/>
[157] <https://ardupilot.org/dev/docs/ros2.html>
[158] <https://ardupilot.org/dev/docs/ros2-install.html>
[159] <https://dojofordrones.com/companion-computers/>
[160] <https://ardupilot.org/blimp/docs/common-autopilots.html>
[161] <https://ardupilot.org/plane/docs/common-companion-computers.html>
[162] <https://ardupilot.org/dev/docs/sim-on-hardware.html>
[163] <https://ardupilot.org/dev/docs/simulation-2.html>
[164] <https://ardupilot.org/dev/docs/MATLAB-Simulink-Simulation.html>
[165] <https://github.com/ArduPilot/ardupilot/pull/17072>
[166] <https://discuss.ardupilot.org/t/gsoc-2020-matlab-and-simulink-conclusion/61049>
[167] <https://www.mathworks.com/matlabcentral/fileexchange/39037-apm2-simulink-blockset>
[168] <https://www.mathworks.com/help/uav/ardupilot/ref/ardupilot-sitl-quadcopter-plant-simulink.html>
[169] <https://lists.libreplanet.org/archive/html/paparazzi-devel/2011-06/msg00176.html>
[170] <https://www.simnet.aero/post/autonomous-sitl-flight-simulation-tutorial>
[171] <https://ardupilot.org/copter/docs/common-use-cases-and-applications.html>
[172] <https://github.com/px4/px4-autopilot>
[173] <https://docs.px4.io/main/en/getting_started/px4_basic_concepts>
[174] <https://github.com/PX4/PX4-Autopilot/blob/main/README.md>
[175] <https://zenodo.org/records/11288850>
[176] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7472300/>
[177] <https://doi.org/10.35784/iapgos.6786>
[178] <https://github.com/PX4/PX4-Autopilot>
[179] <https://docs.px4.io/main/en/peripherals/mavlink_peripherals>
[180] <https://discuss.px4.io/uploads/default/original/2X/9/961a8d2ad0b44d7d2d2342cb30cd5cb8cef06df5.pdf>
[181] <https://px4.io/wp-content/uploads/2019/06/PX4-Roadmap-Q2-_-2019.pdf>
[182] <https://px4.io/wp-content/uploads/2019/06/Presentation-ROS2-powered-PX4.pdf>
[183] <https://px4.io/px4-autopilot-release-v1-15-what-you-need-to-know/>
[184] <https://www.eprosima.com/news/bridging-px4-and-ros-2-with-micro-xrce-dds>
[185] <https://www.taholab.com/24101>
[186] <https://docs.px4.io/v1.16/en/flight_modes/offboard>
[187] <https://docs.px4.io/v1.12/en/ros/ros2_comm>
[188] <https://doi.org/10.30525/978-9934-26-499-3-6>
[189] <https://px4.gitbook.io/px4-user-guide>
[190] <https://www.mathworks.com/help/uav/px4/ref/hitl-simulink-plant-example.html>
[191] <https://docs.px4.io/main/en/flight_controller/pixhawk4>
[192] <https://www.politesi.polimi.it/retrieve/7eba5e83-ad9c-4c0f-9322-355fda9096c1/TESI_HOSM_PX4_MONTEMURRO.pdf>
[193] <https://github.com/px4/firmware/tree/stable>
[194] <https://github.com/px4/Firmware/>
[195] <https://github.com/tudelft/Firmware>
[196] <https://www.mdpi.com/2673-4052/3/3/25>
[197] <https://docs.px4.io/main/en/companion_computer/>
[198] <https://docs.px4.io/main/en/>
[199] <https://docs.px4.io/main/en/ros2/user_guide>
[200] <https://docs.px4.io/v1.15/en/ros2/>
[201] <https://docs.px4.io/main/en/ros/mavros_installation>
[202] <https://docs.px4.io/v1.17/en/simulation/>
[203] <https://docs.px4.io/v1.15/en/simulation/>
[204] <https://docs.px4.io/main/en/getting_started/flight_controller_selection>
[205] <http://hdl.handle.net/10150/675395>
[206] <https://docs.px4.io/main/en/contribute/code>
[207] <https://docs.px4.io/v1.17/en/robotics/index>
[208] <https://docs.px4.io/v1.16/en/sim_gazebo_classic/index>
[209] <https://www.mathworks.com/videos/simulate-and-deploy-uav-applications-with-sil-and-hil-workflows-1653992847786.html>
[210] <https://docs.px4.io/main/en/simulation/hitl>
[211] <https://docs.px4.io/v1.17/en/simulation/hitl>
[212] <https://docs.px4.io/v1.16/en/flying/missions>
[213] <https://px4.io/>
[214] <https://blog.unmanned.tech/flight-controller-firmware/>
[215] <https://ardupilot.org/copter/docs/common-autopilots.html>
[216] <https://robotics.growbotics.ai/projects/software/ardupilot>
[217] <https://www.librepilot.org/>
[218] <http://opwiki.readthedocs.io/en/latest/user_manual/gcs_install_lp.html>
[219] <https://www.youtube.com/watch?v=jnVgsROwRos>
[220] <https://docs.px4.io/main/en/ros/offboard_control>
[221] <https://github.com/iNavFlight/inav>
[222] <http://www.droneteamproject.eu/images/gallery/meetings/fourth_meeting/tutorialW.pdf>
[223] <https://betaflight.com/docs/wiki/getting-started>
[224] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7915191/>
[225] <https://betaflight.com/download>
[226] <https://en.ardupilot.org/rover/docs/common-autopilots.html>
[227] <https://github.com/betaflight/betaflight/blob/884229e9/src/main/main.c>
[228] <https://docs.paparazziuav.org/latest/main__ap_8c_source.html>
[229] <https://github.com/ArduPilot/ardupilot/pull/13637>
[230] <https://docs.px4.io/v1.16/en/sim_gazebo_gz/>
[231] <https://docs.paparazziuav.org/v5.14/module__nps.html>
[232] <https://wiki.paparazziuav.org/wiki/Mission_computer>
[233] <https://www.imavs.org/papers/2014/paper26.pdf>
[234] <https://github.com/robot-perception-group/LibrePilot/commits/airship_control_noetic/>
[235] <https://github.com/robot-perception-group/LibrePilot/commits/2bd3c8f05d3f37297261dd996d6482e44392f09b/>
[236] <https://forum.librepilot.org/index.php?topic=1287.0>
[237] <https://betaflight.com/docs/wiki/release/older/Betaflight-3-2-Release-Notes>
[238] <https://github.com/pichim/bf_controller_tuning>
[239] <https://inavfixedwinggroup.com/guides/getting-started/inav-modes-guide/>
[240] <https://robomed.bg/wp-content/uploads/2025/01/2024-10-28-MR-2024-autopilots.pdf>
[241] <https://ryanharter.com/blog/2023/10/screenshot-tests-are-manual-tests/>
[242] <https://github.com/betaflight/betaflight>
[243] <https://github.com/iNavFlight/inav/blob/f1c5e748/src/main/fc/fc_msp.c>
[244] <https://github.com/betaflight/betaflight-configurator>
[245] <https://github.com/robot-perception-group/LibrePilot/commit/14b319903979127ef493f13bbf2494fa17df3f11>
[246] <https://github.com/librepilot/LibrePilot/blob/next/ground/gcs/src/plugins/hitl/simulator.cpp>
[247] <https://betaflight.com/docs/wiki/tuning/4-2-tuning-notes>
[248] <https://www.mathworks.com/matlabcentral/answers/2098126-how-to-locate-the-px4-files-which-in-wsl2-when-i-use-the-uav-toolbox-for-px4>
[249] <https://ardupilot.org/dev/docs/sitl-simulator-software-in-the-loop.html>
[250] <https://betaflight.com/docs/wiki/release/Betaflight-4-5-Release-Notes>
[251] <https://docs.px4.io/v1.16/en/advanced_config/ethernet_setup>
[252] <https://www.mepsking.shop/blog/what-boards-does-betaflight-not-support-anymore.html?srsltid=AU7gw4VGVAtJLXUdC5AlPpoWxNjJ8EDZDM3V8T_rP5Zjmce2yNUKo9Hf>
[253] <https://bitbucket.org/librepilot/librepilot/src>
[254] <https://github.com/betaflight/betaflight-tx-lua-scripts/blob/master/README.md>
[255] <https://github.com/paparazzi/paparazzi/pull/2069>
[256] <https://docs.paparazziuav.org/latest/module__fdm_gazebo.html>
[257] <https://github.com/librepilot/LibrePilot/blob/next/ground/gcs/src/plugins/hitl/fgsimulator.h>
[258] <https://github.com/librepilot/LibrePilot/blob/next/ground/gcs/src/plugins/hitl/simulator.h>
[259] <https://opwiki.readthedocs.io/en/latest/user_manual/oplink/bluetooth.html>
[260] <https://app.readthedocs.org/projects/opwiki/downloads/pdf/latest/>
[261] <https://github.com/betaflight/betaflight/releases/tag/4.4.3>
[262] <https://github.com/betaflight/betaflight/releases/tag/4.1.0>
[263] <https://github.com/iNavFlight/inav/releases/tag/7.1.0>
[264] <https://github.com/iNavFlight/inav/commits/master/src/main/telemetry/smartport.c>
[265] <https://github.com/iNavFlight/inav/releases/tag/8.0.0-RC1>
[266] <https://github.com/gonsp/Helix>
[267] <https://librepilot.atlassian.net/wiki/spaces/LPDOC/pages/8552484/UAVObjects>
[268] <https://github.com/iNavFlight/inav/releases/tag/3.0.0-final>
[269] <https://grokipedia.com/page/librepilot>
[270] <https://www.mathworks.com/matlabcentral/answers/1907645-simulink-px4-difference-between-r2022a-r2022b-same-simulink-model-does-not-work-in-r2022b>
[271] <https://www.unmannedtechshop.co.uk/blogs/knowledge-base/betaflight-vs-inav-vs-ardupilot-which-firmware?srsltid=AU7gw4UUXbC3OCoohb6Z3la8LXu9UKakCSOqMo_Y2HoKdGf6G8-KUdDf>
[272] <https://baptiste-pollien.fr/project/paparazzi-frama-c/>
[273] <https://en.wikipedia.org/wiki/Paparazzi_Project>
[274] <https://hal.science/hal-04628208>
[275] <https://ardupilot.ardupilot.org/dev/docs/ros-sitl.html>
[276] <https://arxiv.org/html/2311.02296v7>
[277] <https://github.com/inavflight/inav/releases>
[278] <https://oscarliang.com/setup-inav-fpv-drone/>
[279] <https://github.com/iNavFlight/inav/releases/tag/8.0.0-RC4>
[280] <https://dojofordrones.com/ardupilot-vs-px4/>
[281] <https://docs.paparazziuav.org/latest/paparazzi_messages.html>
[282] <https://github.com/robot-perception-group/LibrePilot/commit/a35771c57ddb3f9af2fc3659b54d00e22f611b22>
[283] <https://bitbucket.org/librepilot/librepilot/raw/8c101adcccabc57ecbfe5be9250344448bee7908/WHATSNEW.txt>
[284] <https://librepilot.atlassian.net/wiki/spaces/LPDOC/pages/8552484>
[285] <https://github.com/betaflight/betaflight/releases/tag/4.5.0-RC3>
[286] <https://discuss.px4.io/t/px4-contains-300000-lines-of-code/39842>
[287] <https://github.com/PX4/PX4-Autopilot/compare/v1.14.0...v1.15.0>
[288] <https://dronecode.org/interdrone/>
[289] <https://oscarliang.com/fc-firmware/>
[290] <https://docs.altnautica.com/mission-control/firmware-comparison>
[291] <https://librepilot.atlassian.net/wiki/spaces/LPDOC/pages/34668550/LibrePilot2Go+Android+App>
[292] <https://www.youtube.com/watch?v=LSxnxwlvp4k>
[293] <https://github.com/ucm-237/ros_paparazzi>
[294] <https://forum.librepilot.org/index.php?topic=1818.0>
[295] <https://github-wiki-see.page/m/iNavFlight/inav/wiki/INAV-Remote-Management,-Control-and-Telemetry>
[296] <https://betaflight.com/docs/wiki/guides/current/betaflight-4.5-cli-commands>
[297] <https://github.com/tudelft/event_orin_drone>
[298] <https://github.com/paparazzi/paparazzi/commit/0f206f185791deebb81571672f37b1ac68996d62>
[299] <https://github.com/iNavFlight/inav/pull/6738>
[300] <https://github.com/iNavFlight/inav/releases/tag/8.0.0-RC2>
[301] <https://deepwiki.com/iNavFlight/inav/6.5-sitl-and-simulation>
[302] <https://github.com/iNavFlight/inav/pull/8583>
[303] <https://github.com/ArduPilot/ardupilot_wiki/blob/master/common/source/docs/common-autopilots.rst>
[304] <https://ucl-delta.github.io/project_gazebo_aruco/simulation/intro_ros2_uav/>
[305] <https://noirfpv.com/betaflight-vs-pixhawk/>
[306] <https://docs.arkelectron.com/knowledge-base/knowledge-base/mavlink.md>
[307] <https://github.com/mavlink/mavros>
[308] <https://github.com/paparazzi/paparazzi/releases/tag/v5.16.0_stable>
[309] <https://docs.px4.io/main/en/companion_computer/pixhawk_companion>
[310] <https://paparazzi-uav.readthedocs.io/en/stable/developer%5Fguide/modules.html>
[311] <https://github.com/paparazzi/paparazzi/blob/master/CHANGELOG.md>
[312] <https://github.com/rafael1193/skyscannner_integration>
[313] <https://github.com/paparazzi/paparazzi/commit/ca68570d035f2e2ed1f80e944135e8f17170fab8>
[314] <https://github.com/paparazzi/etherlink>
[315] <https://www.repeato.app/repeato-vs-paparazzi/>
[316] <https://github.com/paparazzi/paparazzi/compare/2430b31f0f38...def68323ad79>
[317] <https://www.youtube.com/watch?v=LcUHlc_9ZQs>
[318] <https://github.com/librepilot/LibrePilot/blob/refs/changes/32/240132/1/Makefile>
[319] <https://github.com/UncleRus/OPWiki/blob/master/source/user%5Fmanual/gcs%5Finstall%5Flp.rst>
[320] <https://github.com/robot-perception-group/LibrePilot>
[321] <https://github.com/robot-perception-group/LibrePilot/commit/9de9db60b9e258742989a5bdc84abf4655bd504e>
[322] <https://forum.librepilot.org/index.php?topic=2461.0>
[323] <https://betaflight.com/docs/development/API/Cloud-Build-API>
[324] <https://github.com/betaflight/betaflight/releases/tag/4.5.0>
[325] <https://github.com/nilay994/trytime/issues/2>
[326] <https://github.com/betaflight/betaflight/pull/12346>
[327] <https://github.com/jacqu/betalink>
[328] <https://github.com/ianrmurphy/PIDtoolbox>
[329] <https://github.com/betaflight/betaflight/releases/tag/4.5.1>
[330] <https://github.com/betaflight/betaflight/issues/13374>
[331] <https://github.com/osrf/vehicle_gateway/blob/main/BETAFLIGHT_README.md>
[332] <https://thedevanaproject.com/2024/12/30/how-to-make-a-companion-computer-communicate-with-inav/>
[333] <https://inavfixedwinggroup.com/rc-news/whats-new-in-inav-4-0-the-ultimate-fixed-wing-guide/>
[334] <https://gitee.com/ayu6688/inav>
[335] <https://github.com/ArduPilot/ardupilot/issues/20830>
[336] <https://www.mathworks.com/hardware-support/px4-autopilots.html>
[337] <https://docs.px4.io/main/en/payloads/use_cases>
[338] <https://lists.libreplanet.org/archive/html/paparazzi-commits/2019-02/msg00054.html>
[339] <https://paparazzi-uav.readthedocs.io/en/stable/user_guide/simulation_main.html>
[340] <https://wiki.paparazziuav.org/wiki/HITL>
[341] <https://www.facebook.com/groups/411910415670782/posts/1747829035412240/>
[342] <https://www.linkedin.com/posts/ahcorde_ros2-vehiclegateway-cpp-activity-7074298679645380608-XCqp>
[343] <https://github.com/mariobo8/betaflight_ws>
[344] <https://github.com/betaflight/betaflight/issues/12212>
[345] <https://github.com/iNavFlight/inav/blob/maintenance-10.x/docs/SITL/SITL.md>
