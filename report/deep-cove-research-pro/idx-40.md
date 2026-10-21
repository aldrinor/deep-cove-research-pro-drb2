# Secure Wi-Fi Sensing Before March 2025: Attacks, Defenses, and Deployment Trade-offs

**Two distinct security problems dominate:** passive attackers turn ordinary Wi-Fi transmissions into unauthorized observations of people, while active attackers manipulate signals or sensing inputs to produce incorrect results or degrade service. Payload encryption alone does not eliminate the first problem, and successful packet delivery does not rule out the second. Both conclusions were supported by public work before the operational cutoff of **28 February 2025**. [1][2]

**Defense selection follows the objective:** signal obfuscation, spatial scheduling, and physical-channel encryption address unauthorized sensing; interference analysis, spatial validation, robust features, and adversarial training address corrupted legitimate sensing. Gesture recognition, activity recognition, and localization require different combinations because they expose different features and tolerate different failure modes.

| Requested question | Representative methods | Decisive evidence | Practical verdict |
|---|---|---|---|
| Attack technology overview | Passive inference; active perturbation, spoofing, interference | Physical information leaks below payload encryption | Separate privacy, integrity, and availability |
| Defense technology overview | Active RF protection; passive processing and training | Protection acts at different sensing stages | Match the defense to attacker control |
| Gesture recognition | WiADv; PhyCloak; MIMOCrypt | Direct gesture attack and privacy-defense demonstrations | Distinguish gesture privacy from gesture integrity |
| Activity recognition | ActListener; IS-WARS; CAT | ActListener reports over 90% recognition accuracy | Protect both observations and classification |
| Localization estimation | FooLoc; AP spoofing; SFKNN | FooLoc: 99.5% online untargeted success; SFKNN: 2–5 m error reduction | Evaluate privacy, false location, and rejection separately |
| Communication preservation | BeamDancer; pilot perturbation | BeamDancer retains over 96% of baseline LoS packet-delivery ratio | Good communication is not a sensing-security guarantee |
| Temporal coverage | Public research and prototypes | Public by 2025-02-28 | Exclude later disclosures |

The scenario results above are developed below using ActListener [3], FooLoc [4], SFKNN [5], and BeamDancer [6].

**The report proceeds through comparisons:** first, the two requested catalogs identify each technique, its action, objective, application scenario, and corresponding countermeasures. The subsequent analysis explains how the principal attacks work, where defenses interrupt them, and which choices best fit gesture recognition, activity recognition, localization, and related applications.

## Scope and classification

### What counts as Wi-Fi sensing security

**The protected information extends beyond packets:** Wi-Fi sensing extracts physical information from radio propagation or communication behavior. Channel state information, or CSI, describes the amplitude attenuation and phase shift between transmitting and receiving antennas across frequency subcarriers. Received signal strength, commonly RSS or RSSI, is a coarser power measurement. Packet timing and size provide another, distinct observation channel. [7][8]

**Three outputs organize the scenarios:** detection answers whether something occurred or is present; recognition assigns a class, such as a gesture or activity; estimation produces a quantity, such as position, speed, or breathing rate. Ma, Zhou, and Wang’s 2019 survey uses this distinction. It matters here because detecting movement, recognizing an activity, and estimating coordinates are different security achievements. [7]

**Privacy and integrity require different judgments:** an attacker accurately locating an unaware person creates a privacy failure; an attacker making an authorized localization system report the wrong position creates an integrity failure. Lost measurements, unusable classifications, or rejected localization requests can also reduce availability. These consequences correspond to the exploratory, manipulation, and disruption threats distinguished in the 2021 wireless-sensing security perspective. [9]

### Active and passive actions

**Attack classification follows attacker intervention:** a passive attack observes legitimate ongoing transmissions using attacker-controlled receivers. An active attack transmits probing or interfering signals, modifies transmitted signals, or alters the inputs presented to a sensing model. The RF distinction follows the threat models in PhyCloak and Lo Cigno and colleagues; model-input modification is explicitly identified as a digital intervention rather than automatically treated as an over-the-air capability. [10][1]

**Defense classification follows protective action:** this report calls a defense *active* when it deliberately changes sensing-relevant transmissions, traffic, transmitter selection, beamforming, or the propagation environment at runtime. A *passive* defense leaves the sensing waveform unchanged and instead uses receiver-side analysis, filtering, server-side validation, model training, data protection, or static physical confinement. This is an operational convention, not a claim that every paper uses identical terminology.

**Two boundary cases deserve attention:** an active defense can target a passive attacker, as with an AP injecting cover signals. Conversely, a passive server-side filter can counter an active spoofing attack. A programmable reflecting surface is classified here by its controlled channel modification, not by whether its radio elements generate or amplify RF energy.

### Reading the catalogs

**Scenario labels preserve task specificity:** G means gesture recognition, A means activity recognition, and L means localization estimation. D indicates a directly studied task; C indicates an application context discussed for the mechanism; S indicates a supporting pipeline operation; O means outside the reported task. Thus, “A:C; presence” does not turn binary presence detection into demonstrated multiclass activity recognition.

**Defense correspondence has two levels:** “matched” identifies a defense described or evaluated for the corresponding attack setting. “Candidate” identifies a mechanism-based connection across studies, rather than a measured head-to-head result. Publication years appear beside the methods; more precise eligibility dates are addressed near the end.

## Part 1 — Attack Technology Overview

### Passive observation and privacy extraction

| Attack Method Name | Attack Type | Attack Objective | Sensing Scenarios Applied | Possible Defense Strategies |
|---|---|---|---|---|
| Adversarial WiFi Sensing / Et Tu Alexa?[11] — 2018/2020 | Passive — external RSS/CSI sniffing | Infer interior anchors, room presence, and movement | G:O; A:C; L:D; homes/offices | Matched: geo-fencing, rate limiting, AP signal obfuscation |
| ActListener [3] — 2022; [12] — 2024 | Passive — signal acquisition | Recover activity semantics and behavioral identity | G:O; A:D; L:S; activity/identity inference | Candidates: spatial scheduling, CSI obfuscation, MIMOCrypt |
| Multi-receiver CSI localization eavesdropping [13] — 2021 | Passive — multiple CSI receivers | Improve unauthorized position inference | G:C; A:C; L:D; device-free indoor positioning | Matched: randomized transmitter pre-distortion; candidates: AntiSense, BeamDancer |
| Encrypted Wi-Fi packet-metadata analytics [8] — 2024 | Passive — timing/size analysis | Fingerprint IoT devices and infer private status | G:O; A:C; L:O; sleep/activity status | Matched: traffic spoofing and packet-size obfuscation |

**Passive attacks exploit different observables:** the first three methods use propagation-dependent information, whereas metadata analytics uses communication patterns. Their objectives overlap—learning private behavior—but their countermeasures are not interchangeable. Changing CSI does not inherently conceal packet timing, and padding packets does not inherently conceal human-induced channel variation.

### Active probing, interference, and physical perturbation

| Attack Method Name | Attack Type | Attack Objective | Sensing Scenarios Applied | Possible Defense Strategies |
|---|---|---|---|---|
| CSI-MURDER active packet probing [14] — 2020 | Active — attacker-generated probes | Localize an unaware, device-free person | G:O; A:O; L:D; indoor positions | Matched: reactive preamble disturbance; candidate: AntiSense |
| IS-WARS [15] — 2021/2022 | Active — cross-technology interference | Corrupt CSI and induce false activity labels | G:O; A:D; L:O; indoor HAR | SCF-based CTI detection; robust features and interference monitoring |
| Physical-world behavior-recognition attack [16] — 2023 | Active — selective jamming | Create targeted or untargeted behavior errors | G:C; A:D; L:O; behavior/authentication | Candidates: CSI-loss monitoring and perturbation-aware training |
| WiADv [17] — 2022 | Active — full-duplex multipath manipulation | Force an attacker-selected gesture label | G:D; A:O; L:O; Widar3.0 | Candidates: physical-consistency checks and adversarially robust recognition |
| WiIntruder [18] — 2024 | Active — over-the-air perturbation | Degrade or redirect multiple sensing models | G:D; A:D; L:D; respiration/authentication | Candidates: robust training, RF anomaly detection, shielding |
| Unnoticeable communication-packet pilot perturbation [2] — 2024 | Active — transmitter-side pilot modification | Change activity/identity labels while preserving communication | G:O; A:D; L:O; HAR/authentication | Candidates: pilot/channel validation, SecureSense, CAT |

**Active surveillance differs from active deception:** CSI-MURDER probing seeks a more accurate unauthorized observation. IS-WARS and the perturbation methods instead corrupt the observations used by a legitimate sensing system. The distinction determines whether protection should conceal the environment, validate measurements, or make the inference model resilient.

### Active model-input adversarial examples

| Attack Method Name | Attack Type | Attack Objective | Sensing Scenarios Applied | Possible Defense Strategies |
|---|---|---|---|---|
| Fast Gradient Sign Method, FGSM [19] — Wi-Fi evaluation 2023 | Active — digital input perturbation | Induce classification errors with gradient-directed changes | G:O; A:D; L:O; HAR/apnea | Matched: adversarial training; CAT for HAR |
| Projected Gradient Descent, PGD [19] — Wi-Fi evaluation 2023 | Active — iterative input perturbation | Find damaging bounded CSI perturbations | G:O; A:D; L:O; HAR/apnea | Matched: adversarial training; CAT for HAR |
| Momentum Iterative Method, MIM [19] — Wi-Fi evaluation 2023 | Active — momentum-based input perturbation | Reduce CSI apnea-classifier accuracy | G:O; A:O; L:O; apnea/vital signs | Matched: MIM adversarial training |

FGSM and PGD also appear in the direct Wi-Fi activity-recognition evaluation of CAT [20].

**Digital access is a substantive capability:** these rows describe modification of model inputs. They establish algorithmic vulnerability but do not, by themselves, establish that the same perturbation can be transmitted through an uncontrolled wireless channel. Physical attacks must additionally accommodate propagation, synchronization, antenna structure, and the receiver’s channel-estimation process.

### Active localization falsification and deceptive WLAN sensing

| Attack Method Name | Attack Type | Attack Objective | Sensing Scenarios Applied | Possible Defense Strategies |
|---|---|---|---|---|
| FooLoc [4] — 2023 | Active — malicious-client training-signal manipulation | Produce targeted or untargeted false positions | G:O; A:O; L:D; CSI fingerprinting | Candidates: signal validation and robust localization processing |
| Phy-Adv [17] — 2024 | Active — physical adversarial interference | Mislead deep fingerprint-localization models | G:O; A:O; L:D; indoor fingerprinting | Matched: Robust Mean-Based Normalization |
| AP spoofing against UJIIndoorLoc [5] — 2024 | Active — fake beacons/RSS fingerprints | Pull estimates toward another location | G:O; A:O; L:D; indoor positioning | Matched: SFKNN spatial validation |
| Deceptive OFDM jamming [21] — 2024 | Active — physical-layer target deception | Generate phantom targets, shift ranges, hide targets | G:C; A:C; L:D; range–Doppler tracking | JCAS-specific electronic-counter-countermeasure design |

**Attack overview takeaway:** passive privacy extraction, active surveillance, digital adversarial examples, and physical sensing deception are separate capabilities; their names should not substitute for an explicit account of what the attacker controls.

**Additional documented evidence**

| Entity | Attack Method Name | Attack Type | Attack Objective | Sensing Scenarios Applied | Possible Defense Strategies |
| --- | --- | --- | --- | --- | --- |
| Passive CSI/packet eavesdropping | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Passive Wi-Fi sensing privacy inference | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Passive localization/person-tracking inference | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Passive physiological/typing inference | Wireless Training-Free Keystroke Inference Attack [61] | no evidence found | no evidence found | no evidence found | no evidence found |
| Wi-Fi sensing jamming/interference | Wi-Fi sensing jamming/interference is an active…[78] | Wi-Fi sensing jamming/interference is an active…[78] | Wi-Fi sensing jamming/interference is an active…[78] | The source supports the canonical attack family “CSI…[44] | The source supports the canonical attack family “CSI…[44] |
| Wi-Fi sensing signal injection/spoofing | The source uses the terminology “spoof their…[109] | The source describes signal spoofing and adversarial…[89] | The source describes signal spoofing and adversarial…[89] | no evidence found | The source describes signal spoofing and adversarial…[89] |
| Wi-Fi sensing replay attack | Replay attack; the page specifically describes a…[110] | Active attack, because the attacker records and later…[110] | The stated objective is to authenticate to the AP by…[110] | No Wi-Fi sensing application scenario such as gesture…[97] | The page documents CSI analysis for detection of…[110] |
| Unnoticeable communication-packet perturbation adversarial attack | The source describes an adversarial perturbation…[89] | The source describes an adversarial perturbation…[89] | The source describes an adversarial perturbation…[89] | The source describes an adversarial perturbation…[89] | The source describes an adversarial perturbation…[89] |
| Wi-Fi sensing model-evasion adversarial examples | The source documents model-evasion adversarial…[89] | The source characterizes model-evasion adversarial…[93] | The source characterizes model-evasion adversarial…[93] | The source characterizes model-evasion adversarial…[93] | For Wi-Fi sensing model-evasion adversarial examples…[51] |
| Wi-Fi sensing training-data or model poisoning | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Localization spoofing or manipulation | The source uses the name “spoofing of Access Points”…[71] | Under the report’s convention, this is an active…[114] | The attack objective is to make WPS output a fake…[113] | Supported target scenarios include WiFi positioning…[113] | Evidence-supported defenses include…[103] |
| Unauthorized or covert Wi-Fi sensing | Unauthorized computer access [96] | Unauthorized-access threat [96] | Access restricted data/resources [96] | Supported target scenarios include passive tracking…[39] | The documented defense is Secur-Fi: generate fraud…[39] |
| Device/AP impersonation for unauthorized sensing | Access point impersonation attack; also described as…[102] | Device or AP impersonation should be classified as an…[103] | Pretend to be an organization AP [77] | Device or AP impersonation targets WLAN localization…[102] | The page does not document a defense strategy for AP…[77] |
| Physical or environmental manipulation and occlusion | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Activity/gesture spoofing or impersonation | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Unnoticeable communication-packet perturbation adversarial attack | The source describes an adversarial perturbation…[89] | The source describes an adversarial perturbation…[89] | The source describes an adversarial perturbation…[89] | The source describes an adversarial perturbation…[89] | The source describes an adversarial perturbation…[89] |
| Passive eavesdropping and CSI or signal-pattern inference | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Unauthorized or covert Wi-Fi sensing by a rogue receiver or transmitter | The source describes the method as unauthorized or…[45] | The source supports a passive attack classification…[45] | The attack objective is to spy on and infer private…[45] | Supported target scenarios include passive tracking…[39] | The documented defense is Secur-Fi: generate fraud…[39] |
| RF signal injection or CSI spoofing | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Replay of Wi-Fi packets or CSI | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Jamming or interference denial of Wi-Fi sensing | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Training-data poisoning of sensing models | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Localization spoofing via false anchors, APs, or measurements | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Device or AP impersonation for unauthorized sensing | Access point impersonation attack; also described as…[102] | Device or AP impersonation should be classified as an…[103] | The attack pursues location spoofing: it reports…[102] | Device or AP impersonation targets WLAN localization…[102] | The page does not document a defense strategy for AP…[77] |
| Physical or environmental manipulation and occlusion to evade or mislead sensing | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Passive CSI/packet eavesdropping | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Passive physiological/typing inference | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Unnoticeable communication-packet perturbation adversarial attack | The source describes an adversarial perturbation…[89] | The source describes an adversarial perturbation…[89] | The source describes an adversarial perturbation…[89] | The source describes an adversarial perturbation…[89] | The source describes an adversarial perturbation…[89] |
| Localization spoofing or manipulation | The source uses the name “spoofing of Access Points”…[71] | Under the report’s convention, this is an active…[114] | The attack objective is to make WPS output a fake…[113] | Supported target scenarios include WiFi positioning…[113] | Evidence-supported defenses include…[103] |
| Passive activity/gesture inference | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| RF jamming or interference denial-of-service | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Sensing-signal/CSI injection or spoofing | The source uses the terminology “spoof their…[109] | The source describes signal spoofing and adversarial…[89] | The source describes signal spoofing and adversarial…[89] | The source describes signal spoofing and adversarial…[89] | The source describes signal spoofing and adversarial…[89] |
| Replay of recorded sensing packets or CSI | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Training-data or model poisoning | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Wi-Fi sensing jamming/interference | Wi-Fi sensing jamming/interference is an active…[78] | Wi-Fi sensing jamming/interference is an active…[78] | Wi-Fi sensing jamming/interference is an active…[78] | The source supports the canonical attack family “CSI…[44] | The source supports the canonical attack family “CSI…[44] |
| Wi-Fi sensing signal injection/spoofing | The source uses the terminology “spoof their…[109] | The source describes signal spoofing and adversarial…[89] | The source describes signal spoofing and adversarial…[89] | no evidence found | The source describes signal spoofing and adversarial…[89] |
| Wi-Fi sensing replay attack | Replay attack; the page specifically describes a…[110] | Active attack, because the attacker records and later…[110] | The stated objective is to authenticate to the AP by…[110] | No Wi-Fi sensing application scenario such as gesture…[97] | The page documents CSI analysis for detection of…[110] |
| Unnoticeable communication-packet perturbation adversarial attack | The source describes an adversarial perturbation…[89] | The source describes an adversarial perturbation…[89] | The source describes an adversarial perturbation…[89] | The source describes an adversarial perturbation…[89] | The source describes an adversarial perturbation…[89] |
| Wi-Fi sensing model-evasion adversarial examples | The source documents model-evasion adversarial…[89] | The source characterizes model-evasion adversarial…[93] | The source characterizes model-evasion adversarial…[93] | The source characterizes model-evasion adversarial…[93] | For Wi-Fi sensing model-evasion adversarial examples…[51] |
| Passive CSI eavesdropping/interception | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Wi-Fi sensing training-data poisoning | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |

**Availability attack: jamming/interference**

| Attack Method Name | Attack Type | Attack Objective | Sensing Scenarios Applied | Possible Defense Strategies |
|---|---|---|---|---|
| **Interleaving jamming** (Wi-Fi sensing jamming/interference; reactive subcarrier jamming) [50] | **Active** availability/DoS attack: transmits interference. | Degrade or block the underlying Wi-Fi transmissions and receiver processing on which sensing may depend; the cited experiment is communication-only [50]. | **Not reported for a sensing task**: no gesture recognition, activity recognition, localization estimation, presence, or physiological-sensing evaluation is given [50]. | Cryptographically randomize interleaving with a shared transmitter–receiver secret; alternatively make it frame-dependent and permute it across time and frequency subcarriers [50]. Generic WIDS/WIPS monitoring and prevention provide only contextual protection, not sensing-validated protection [49]. |
| **Wireless Training-Free Keystroke Inference Attack** (keystroke eavesdropping) [61] | **Passive** eavesdropping and inference [61] | Infer typed letters and other sensitive typing activity non-invasively from wireless-signal changes [61] | **Typing/keystroke inference demonstrated**; gesture recognition, activity recognition, and localization estimation are not reported for this attack [61] | **Reactive jamming during the typing period**, directly proposed as a countermeasure [61] |
| **Location Spoofing** (also “location spoofing attacks”) [62] | **Active** impersonation and interference attack: remote access points are impersonated and nearby signals are jammed [62] | Falsify the computed position so that a device appears to be somewhere other than its actual location [62] | **WiFi/WLAN positioning and self-localization**, specifically Apple iPhone/iPod positioning through Skyhook’s WiFi Positioning System (WPS) [62] | Restrict public WLAN-based localization systems, including Skyhook WPS, in security- and safety-critical applications; the source does not document a technical prevention or detection countermeasure [62] |
| **Wi‑Fi sensing jamming/interference** [64] | **Active availability attack**; constant/deceptive/random/reactive [64] | Denies transmission/channel access; may force rogue‑AP connection; sensing aim unresolved [64] | Not established: generic WLAN, not gesture/activity/localization [64] | Strength/PDR/PSR checks, frame rejection, channel switching, extra monitors; WLAN-only [64] |
| **AP spoofing** (“spoofing of Access Points”; localization spoofing/manipulation) [71] | **Active**—fake AP beacons reuse radio-map MAC addresses at other locations [71] | Corrupt RSS fingerprints and position estimates; misdirect users to unintended or prohibited locations and expose privacy [71] | Wi-Fi fingerprint indoor localization/positioning and smartphone location-based services; evaluated on multi-building UJIIndoorLoc; hospitals, airports and campuses are discussed contexts [71] | Cooperative/pre-installed measurements; landmark RSS correlation; CSI source authentication; Wasserstein detection; Shared/Unshared AP and Spatial Filter/SFKNN filtering [71] |
| **Wi-Fi sensing jamming/interference** (radio interference; denial of service) | **Active**, physical/MAC-layer availability attack | Deny transmission or reception; the sensing-availability consequence is qualified rather than directly demonstrated | **Not established** for gesture recognition, activity recognition, or localization estimation; the evidence concerns wireless-sensor/802.11 communication | Channel surfing/frequency hopping, spatial retreat, power control, and error-correcting codes; PDR, signal-strength, carrier-sensing-time, and multimodal detection are transferable but not sensing-specific [78] |
| **Device/AP impersonation for unauthorized sensing** (*AP Impersonation*; *Rogue AP*) | **Active, provisional**; the source establishes a rogue-AP class, not the sensing taxonomy | Pretend to be an organization’s access point | **Not reported**: no unauthorized-sensing demonstration or named sensing task | No pre-cutoff sensing defense is documented; a containment discussion dated 2026 is outside the report scope [77] |
| **Wi-Fi sensing signal injection/spoofing** | **Active**: injects or broadcasts a perturbation that changes the received signal. | Cause classifier misclassification, sabotage a protocol, or allow a transmitter to conceal itself from signal-intelligence observation; the Wi-Fi-sensing-specific objective remains **not established**. | **Not established for Wi-Fi sensing** in the supplied evidence. The source evaluates over-the-air RF waveform/modulation classification and generic recognition modules, not gesture recognition, activity recognition, or localization estimation. | **Adapted/analogous:** RF/device fingerprinting, physical-layer waveform authentication, adversarial training, and detection of anomalous patterned noise. Direct Wi-Fi-sensing effectiveness is not reported [89]. |
| **Wi-Fi sensing model-evasion adversarial examples** | **Active**: an independently transmitted perturbation changes the input seen by a neural classifier. | Induce systematic model error or evade recognition. | **Not established for Wi-Fi sensing**; demonstrated against a naïvely trained RESNET modulation classifier and other neural-network recognition modules using RF waveforms. | Adversarial data augmentation and robust/adversarial training are supported as mitigations; the source also states that a combination of techniques can substantially mitigate the UAA. No Wi-Fi-sensing evaluation is reported [89]. |
| **Unnoticeable communication-packet perturbation adversarial attack** | **Active**: a weak, difficult-to-detect interfering signal perturbs an over-the-air waveform. | Degrade or redirect naïve AI classification while avoiding simple energy-based detection. | **Not established for Wi-Fi sensing** in this source; the reported experiment uses RF waveform classification with clean and adversarial transmissions from a second SDR. | Adversarial training and data augmentation are directly supported in the source; anomaly or spectral detection is a qualified, adapted possibility rather than a demonstrated Wi-Fi-sensing defense [89]. |
| **RF signal injection or CSI spoofing** | **Active**: signal spoofing or adversarial perturbation transmitted by a man-in-the-middle or an independent transmitter. | Alter the apparent signal, sabotage processing, obfuscate the transmitter, or cause classification errors; a CSI-specific effect is **not established**. | **Not established** for Wi-Fi sensing or CSI. The documented scenarios are non-cooperative communications, radar-function preservation, SIGINT obfuscation, and RF modulation classification. | RF/device fingerprinting and source authentication, waveform authentication, adversarial training, and coordinated anti-jamming/anti-spoofing controls are possible adapted defenses; none is directly evaluated here for Wi-Fi sensing [89]. |
| **Wi-Fi sensing jamming/interference** | **Active, provisionally**: jamming changes signal availability and therefore fits the report’s active-attack rule. | Deny availability or degrade sensing measurements, but the supplied source does not demonstrate a sensing-specific denial-of-service effect. | **Not established** for gesture recognition, activity recognition, localization estimation, or another Wi-Fi-sensing task. A later source only identifies jamming as a common IoT-network attack [90]. | The later source lists encryption, strong authentication, network segmentation, firmware updates, and monitoring for aberrant behavior as general IoT protections. Their direct effectiveness against Wi-Fi-sensing jamming is **not established** [90]. |
| **Wi-Fi sensing jamming/interference** (RF jamming; denial of service) | **Active**, provisionally; the attacker transmits interference or overloads the wireless medium | Disrupt availability. Generic evidence describes spectrum pollution with noise and system overload, but does not demonstrate degradation of a sensing output specifically [91][92][95] | **Not established** in the supplied sensing-specific evidence; the cited examples concern WLAN, IoT, or industrial communications rather than gesture recognition, activity recognition, or localization estimation [91][92] | Transferable, not sensing-evaluated: a controller-based Colonel Blotto method, probabilistic hierarchical-game mitigation, deep-reinforcement-learning mitigation, firewalls/rate limiting, and wired-network isolation or segmentation [91][92][95] |
| **Replay of Wi-Fi packets or CSI / Wi-Fi sensing replay attack** (generic mechanism name: “Replay Attack (Copy-Paste Attack)”) | **Active** temporal/integrity attack; the attacker captures and retransmits a legitimate message [95] | Cause an unauthorized repeated action, alter an aggregate result, or reuse a stale sensing observation; direct CSI or sensing-output impact is **not established** [91][95] | **Not established** for gesture recognition, activity recognition, localization estimation, or another Wi-Fi-sensing task in the supplied evidence [91][95] | Fresh challenges/nonces, time tokens, timestamps, session tokens, secure packet variations, message-authentication codes, DTLS epoch and sequence numbers, and replay windows; these are generic or transferable controls rather than direct CSI-replay evaluations [91][95] |
| **Wi-Fi-sensing model-evasion adversarial examples** | **Active** operational-phase evasion; white-box or black-box depending on attacker knowledge [93] | Induce incorrect model predictions with carefully crafted, subtly perturbed inputs [93][94] | **Not established**: the supplied demonstrations concern generic AI or an NLP/fake-news classifier, not gesture recognition, activity recognition, localization estimation, or another Wi-Fi-sensing task [93][94] | Adversarial training; robustness evaluation with ART, RobustBench, or CleverHans; input-access controls; adversarial-input detection; and β-smoothing. These remain generic defenses for this candidate [93] |
| **RF signal injection or CSI spoofing**, also rostered as **Wi‑Fi sensing signal injection/spoofing**; the source-supported broader term is “wireless spoofing” [107] | **Active** when implemented through identity forgery and packet transmission. The narrower CSI/RF-waveform-injection claim remains **unresolved** [107] | Compromise transmitter identity, masquerade as another device, enable traffic injection, and potentially impair performance, access control, or availability; detection aims to locate and remove the adversary [107] | **Related method demonstrated:** real-time indoor localization/localization estimation in an office-building deployment using 802.11 Wi‑Fi and 802.15.4; no gesture- or activity-recognition evidence [107] | Cryptographic authentication; RSS-based statistical/K-means spoofing detection, attacker localization, and network removal. These are documented for related wireless spoofing, not validated specifically against CSI injection; authentication also requires infrastructure, computation, key management, and protection against node compromise [107] |

**Mechanism and status.** *Interleaving Jamming in Wi-Fi Networks* was publicly published on **2016-07-15** [50], making the enabling method pre-cutoff; its sensing-specific application remains **unresolved**, not demonstrated. Deterministic IEEE 802.11a/g/n OFDM interleaving lets a reactive HackRF One jammer target data subcarriers \(i,i+3,\ldots\), creating post-deinterleaving error bursts beyond convolutional correction. It detects the short preamble and emits interference in **less than 30 µs**; interleaving jamming can target any sub-OFDM symbol [50].

**Limits and evidence.** The communications testbed reported more than **95% packet destruction** with less than **0.1%** of transmitter power and complete blocking below **1%** [50]. With two jammed subcarriers, packet-error rate reached **95% at 35 dB SJR**; with seven, it reached **100% at 30 dB SJR** [50]. These are packet metrics, not sensing metrics. Effectiveness depends on detection, pattern, power, response time, and hardware; narrow-band interference may leave enough subcarriers for depth-6 coding to correct errors, while longer bursts waste energy. Parallel traffic, distortion, fading, multipath, false detections from low noise or repeated samples, and multiple links limit generalization; the open test used nodes within **2 m** [50]. CISA’s **2017** guide identifies generic DoS and RF interference, but not sensing-specific prerequisites [49].

The permitted study names “Beacon Replay Attack” for receiver-initiated WSN MACs: captured identity beacons are retransmitted, enabling sinkhole/blackhole/selective-forwarding/Sybil/wormhole/Sleepwalker attacks; active. RAP-D detects post-transmission cheaply; RAP-P authenticates pre-transmission and blocks data (two extra messages/larger challenge). RAP is formally verified; an energy/security trade-off is reported. No Wi-Fi-sensing scenario; background only. [52]

For Wi-Fi sensing jamming/interference, the candidate remains unresolved: a 12 June 2025 study (post-cutoff) reports CSI/RSSI sensing, not jamming, and supplies only related sensing-attack/defense context [53]. Related attack: active/passive motion/presence privacy inference via outside-room CSI/RSSI; jamming type/objective/metric/success rate unestablished. Setup: two three-antenna TP-Link N750 routers, 5 GHz, 4.5 m; 0.2 s, B=1/10, K=1/504; one person for approximately 15 s. Gain randomization blunts some features; all-feature use may need frequency dependence; CSI variance/SD persists. Limits: environment/temperature, phase noise, false positives, second-room failure, B=10 delay. Independent context: IRShield (2021) and radio-window defense (2020); no eligibility proof. [53]

**Wi-Fi sensing jamming/interference (RF-based DoS; WLAN interference)** is an availability-oriented candidate for the secure Wi-Fi sensing attack-and-defense survey, but the evidence is adjacent WLAN security evidence. **Type:** active availability/DoS candidate; WIPS response is active, while the sensing-specific subtype remains unresolved. **Objective:** disrupt or degrade authorized 802.11 access; a sensing-output objective is not established. **Scenarios:** not established—the source covers controlled 802.11 WLAN devices, not gesture recognition, activity recognition, or localization estimation. **Possible defenses:** adjacent/adapted only—WIDS detects and logs RF DoS, monitors spectrum, RSSI and baseline anomalies, and locates interferers; WIPS actively restricts unauthorized devices [54].

Mechanistically, dedicated WIDS sensors and a controller monitor 802.11 channels in the 2.4 and 4.9/5.0 GHz bands, compare a WLAN baseline, and locate emitters, with an optional **5 m radius** capability; WIPS provides **24/7** active restriction [54]. The Annex also identifies deauthentication/disassociation flooding and possible DDoS, but notes inadvertent signal collection and the secondary-network cost of overlay deployment. Its **February 2021** date establishes related pre-cutoff WLAN evidence, not the attack’s earliest public date; no sensing metric, dataset, denominator, direct sensing defense, or sensing-specific first-public date is reported, so the candidate remains unresolved [54].

Jamming is active DoS: SDR noise/packets disrupt Wi-Fi [55]. 2023 Wi-Fi-IoT evidence has no sensing scenario; status unresolved; detection is communication-level [55].

Jamming: active RF DoS; scenario unreported; signal/location checks proposed; metrics confounded by congestion/mobility; 2005-05-25, MICA2 packets; sensing unresolved [56].

Reactive/bit jamming actively causes packet/bit DoS; 2010 evidence is sensor-network-only, so Wi‑Fi scenario/status unresolved. RSS/error-code detection is unvalidated [57].

Jamming/interference—active DoS (constant/deceptive/random/reactive); RSS/PDR+hop/ECC defend. WSN-only; Wi‑Fi unresolved; 2006-05-01/Aug 2010; 3 bits=90%, >21 coded [57][58]

**Localization spoofing or manipulation**

Localization spoofing or manipulation is represented by **Wi‑Fi geolocation spoofing**, with related terms **target spoofing** and **preamble/fake-path injection** [59]. It is **active**: the adversary transmits spoofing or jamming signals and injects artificial targets. The mechanism exploits frame detection, synchronization, channel estimation, CSI feedback, or fabricated channel-transfer functions to alter the receiver’s target or channel map. Eve may need sensing parameters, knowledge of RDM processing, timing/CFO and link-distance estimates, and multiple antennas or beamforming for selective control [59].

The objective is to create false readings, shift or replace real target peaks, suppress the legitimate surveillance signal, and corrupt sensing or positioning integrity and location information [59]. Applied scenarios are **indoor localization, Wi‑Fi geolocation, WLAN positioning, and location estimation**. The direct experiment demonstrates WLAN/RDM target detection rather than a localization-estimation task; the localization mapping comes from cited related works [59].

Possible defenses include secure OFDM precoding, angle-of-arrival physical-layer authentication, machine/deep-learning jammer detection, location-spoofing-device identification, and receiver-side ridge detection with response. Related location-privacy methods use delay-angle or fake-path information spoofing [59]. These are qualified rather than universal defenses: no single method covers every jammer, and overly strict detection can miss real targets [59].

Thus, Localization spoofing or manipulation is an attack-table row linked to the defense part through spoofing identification and location-privacy protection [59]. Its exact family-level earliest public date is **unresolved**: related publications listed by the source are from **2009, 2015, 2017, and 2024**, all before the cutoff, but the source does not identify the first disclosure of this canonical family [59].

**Evidence additions: typing inference and localization spoofing**

The **Wireless Training-Free Keystroke Inference Attack** operates without malware installation or a training phase. A key press produces a subtle environmental change; the attacker extracts channel state information (CSI) from the wireless signal and maps each typed letter to its environmental change by exploiting correlations and known dictionary-word structures [61]. The abstract reports experimental validation on software-defined-radio platforms, and the source was published on **8 February 2022**, establishing demonstrated pre-cutoff evidence [61]. Its relevance to secure Wi-Fi sensing is direct: the attack exposes private typing activity, while the same work proposes reactive jamming as a defense [61]. For scenario-specific completeness, the supported result is typing inference—not a generic claim covering gesture recognition, activity recognition, or localization.

**Location Spoofing** is a distinct active attack on the sensing output rather than a passive privacy-inference attack. In the documented pipeline, a device detects neighboring access points, sends their information to Skyhook servers, receives access-point locations, and computes its position. The attacker impersonates access points from a known remote location and eliminates nearby access-point signals through jamming; forged MAC addresses make the impersonation possible, producing a false location [62]. The attack therefore supplies the localization-integrity row in the attack overview and also motivates the source’s warning that public WLAN positioning should be restricted in security- and safety-critical applications [62]. The cited public report is dated **16 April 2008** and is pre-cutoff, although it does not establish that date as the earliest public disclosure [62]. The page provides no quantitative metric or denominator for the attack, so no numerical success comparison is established here [62].

Wi‑Fi sensing jamming/interference: active availability attack; scenario, defense, and first-public date unresolved. It injects noise/packets; USRP/all channels required [63].

Mechanism: cognitive-radio/multi-channel or distributed low-power jamming cuts links; unencrypted management/control frames permit deauthentication [64]. Limits: antenna/battery faults, distance, multipath, walls and power confound detection; one parameter is insufficient [64]. Date/status: generic jamming public by 2004–2012; sensing-specific date unresolved [64]. Non-sensing tests: deceptive PSR/PDR 0/0; TPR 74.6% (1 monitor), 94.2%/FPR .2% (2), 99.9%/0% (3) [64].

Wi-Fi sensing jamming/interference=A DoS; mass-access/fake-PU→avail.; Wi-Fi scen not est. (CR, 2023-03-23); Pd/Pfa, 5k×50×100 RE, 3 nodes; auth/enc/anom; generic CMS [66][65]

RF jamming/interference: active WLAN-availability DoS; sensing task/parameters, metrics and first date unknown. WIDS logs RF DoS; WIPS blocks connections; 2021-02-02 [67].

**Qualified generic defenses.** [68] supports encryption for confidentiality; hashing, message digests and integrity checks for tampering; signatures/certificates for authentication; access control for limiting collection; and IDS/IPS, logging, anomaly detection and data-loss prevention for suspicious use. These are adapted possibilities—not sensing-specific evaluations—for passive CSI eavesdropping, injection/replay and unauthorized sensing. Defense-in-depth/Zero Trust add layered controls, segmentation, least privilege and per-request authentication; frequency hopping is only a generic channel/key-change idea. Security processing may increase latency [68]. For **Wi-Fi sensing jamming/interference**, [68] establishes no sensing-specific mechanism, prerequisite, scenario, metric, dataset, denominator, baseline, first-public date or demonstrated status. It offers only generic risk analysis: qualitative scores commonly use 1–5 or 1–10 scales, and quantitative estimates may be uncertain [68].

Jamming/interference: active physical DoS; RF disrupts WLAN; scenario not reported; perimeter defense. Proximity/benign RF confound detection; status/date unresolved [69].

RF jamming/interference: active DoS; Q-learning selects channels from SINR/freq/BW. Generic pre-cutoff 2013/2017 evidence; sensing-specific status unresolved [70]

**Mechanism/status.** RSS fingerprints are sent to a localization server; fake beacons inject random or copied fingerprints. A 2024 UJIIndoorLoc simulation used two scenarios with **1–10 spoofed APs**; SFKNN reduced mean localization error by **2–5 m** [71]. The publication record establishes pre-cutoff evidence, but not an exact first-public day. It is a demonstrated simulation; limits include infrastructure cost, limited consumer CSI, sampling delay, and weaker small-area robustness [71]. Detection and filtering therefore inform the defense crosswalk [71].

**Passive CSI/packet eavesdropping (wireless-sensing eavesdropping).** This is a **passive** attack: the adversary listens to existing Wi-Fi traffic, obtains CSI from sniffed frames, and performs sensing without transmitting. Its objective is privacy loss through inference of location, speed, activity, gestures, vital signs, gait or identity, occupancy, and related behavior; unauthorized CSI capture can directly track activity [42][41]. The scenario-specific attack cell therefore includes indoor location/speed estimation, activity or gesture inference, vital-sign sensing, person tracking/identification, and occupancy monitoring. A source-described possible defense is continuously changing AP beamforming, while jamming and geofencing are identified as impractical because they impair communications or do not scale [42]. The threat model assumes sufficient traffic for usable CSI and fixed legitimate and eavesdropping devices; the attack may nevertheless be mounted outside the premises, through walls, or from a drone. The supplied pre-cutoff passage does not establish an earliest public date or quantitative attack metric, so those cells remain **not established in the supplied evidence** [42].

A December 2025 source [40] later describes the same passive-inference family as recovering location, activity, motion, keystrokes, and speech. Because it is post-cutoff, it cannot establish eligibility for this survey. Its later summary nevertheless records jamming by channel occupation or virtual-signal injection, physical-layer encryption requiring transmitter/receiver changes, costly full-duplex active obfuscation, and passive obfuscation using large arrays or metasurfaces that may prevent legitimate sensing. Its proposed backscatter-tag system dynamically changes reflection states and reports a reduction of more than 60% in motion-detection rate; these are screening context only, not pre-March-2025 evidence [40].

**Wi-Fi sensing jamming/interference.** The candidate name is supported only indirectly; the evidence describes an **active availability/denial-of-service** attack that jams or interferes with a channel to disrupt information freshness and timeliness. No concrete Wi-Fi-sensing task—gesture recognition, activity recognition, or localization estimation—is reported; the experiment concerns a CPS sensor transmitting status or environmental information. Management Frame Protection is suggested against Wi-Fi deauthentication, but it is not directly evaluated against sensing-specific jamming [72]. The described mechanism uses an interferer transmitting against the channel, with strategy controlled by transmit power; the experimental attacker uses a Wi-Fi interface in monitoring mode and launches the attack 15 seconds after the experiment begins. Deauthentication sends a bogus frame and may require the victim’s MAC address [72]. In that CPS experiment, each run lasted 30 seconds with 60 request–response cycles and 10 repetitions; median AoI was approximately 300 ms without attack versus 6,000–7,000 ms under attack, while median energy was approximately 60 J versus 100 J. These are deauthentication/CPS results, not Wi-Fi-sensing performance metrics [72]. Thus, sensing-specific evidence status and earliest public availability remain **unresolved/not established**, although the candidate is relevant to the survey as an availability threat [72].

**Wi-Fi sensing signal injection/spoofing (forged management frames).** This is an **active integrity/availability** attack: an attacker transmits forged, unauthenticated Wi-Fi management frames to spoof the source and potentially enable disruption, rogue-AP, or man-in-the-middle effects. The directly documented defense is CSITE, which authenticates management frames at the physical layer using CSI and detects spoofing [73]. The source reports evaluation “in various scenarios,” but does not identify a named sensing application such as gesture recognition, activity recognition, or localization estimation; the sensing-specific scenario cell is therefore **not established** [73]. The attacker can use an injection-enabled wireless NIC. CSITE exploits rapid spatial decorrelation, transmit-power independence, and the richer dimensions of 802.11n CSI; it is implemented on off-the-shelf hardware and operates without collaboration or an advance fingerprint. The reported result is approximately **8× improvement** over an RSS-based method for falsely accepted attacking frames. The earliest public evidence supplied is the 14–19 April 2013 IEEE INFOCOM conference presentation, with IEEE Xplore addition on 25 July 2013 [73]. The evidence demonstrates pre-cutoff Wi-Fi spoofing and its countermeasure, but its application to a named Wi-Fi-sensing task remains unresolved [73].

Wi-Fi sensing jamming: active OFDM/CSI injection causing DoS/spoofing in auth/local./activity/object sensing; detection/hopping/noise possible. Unresolved (2024 vs ©2025).[44]

Jamming/interference: active DoS; stronger wide-/narrow-band signals disrupt channels; sensing scenario and pre‑2025 status unverified; monitoring may detect. [74]

Wi‑Fi geolocation spoofing: active fake-path injection falsifies indoor/public-WLAN location; defenses: device ID, AoA auth., OFDM precoding; RDM+known params [75].

Jamming operates by bypassing MAC protocols or transmitting on a selected channel; continual transmission blocks legitimate MAC operations and causes collisions and backoff, while a reactive jammer transmits after detecting channel activity. Its effect depends on jammer-to-node distance, relative transmission powers, and the MAC protocol [78]. Detection is confounded by congestion, device or battery failure, and mobility. The supporting communication study used PSR/PDR measures—not a sensing task—with MICA2 nodes 30 in apart, 5.28/6.46 kb/s traffic, and a congestion comparison of 19.38 kb/s offered traffic against 12.364 kb/s capacity at 100% duty cycle and approximately 78% PDR [78].

The jamming mechanism is publicly documented by **Spring 2006**, while a related source was publicly posted on **2012-08-02**; neither establishes the earliest public date or direct demonstration of Wi-Fi-sensing jamming, so the sensing-specific status remains unresolved [76][78]. The same 2012 page discusses CSI authentication for Wi-Fi management-frame spoofing and reports about an eightfold improvement over RSS-based false acceptance, but that is related wireless security rather than direct sensing-jamming evidence [76]. For **Localization spoofing or manipulation**, the available page supports only the year **2024** through a cited WLAN-sensing paper; the exact first-public month and day remain unavailable [75].

RIS selective jamming (active): eavesdrop/configure RIS, disrupt target Wi‑Fi reception; device-level, no named sensing task; countermeasures unspecified; 24–28 Feb 2025 [79]

RF-jam/DoS[A]: NIC-inj; jam paired+tunnel; sense? [80]. CSI-spoof: auth flags forged MF [80]. trad=block; subcar-IF≠block; 2025-05-12>cutoff; pre?/sim+real; m,d,b,s∅ [47]

Localization spoofing: active false-location injection for indoor localization; needs params. AoA auth/anti-jamming; 2009 related evidence, exact date/metric unresolved [81].

Jamming: DoS; HCS/WCS hop; sensing unresolved; 2015-02-01 [82]. MITM jam+tunnel; flow-loss monitor [83]. Localization spoofing: active false loc; generic defenses [84].

**Model-evasion adversarial examples** are active inference perturbations of test inputs (versus training poisoning or query-privacy attacks); taxonomy: white/gray/black-box, targeted/untargeted, and integrity/availability/privacy [51]. Proposed (not Wi-Fi-evaluated) defenses include adversarial/certified training, regularization, denoising, detection/ensembles/anomaly rejection, smoothing, and DP/HE/SMPC/FL; training shifts boundaries and detection rejects inputs [51]. Limits are retraining/compute, clean-data loss, black-box latency, adaptive bypass, and weak real-world transfer. General metrics include robustness, ASR, and ε/(ε,δ); no Wi-Fi scenario, dataset, or pre-cutoff date is established [51].

**Jamming/interference** is active DoS: RF energy or management-frame interference disrupts communications. An 802.11 study reported one packet causing complete DoS at some stations for >1 min (2009-10-01) [60]. NIST identifies same/conflicting-channel interference: check APs within five channels, then change channel. Possible defenses include rate limiting, redundancy, scrubbing, anomaly monitoring, and channel change [85][86]. No sensing task or sensing-specific defense is established; status remains unresolved [60][86].

Jamming/interference: active DoS; same-band RF disrupts availability; sensing/date/status unresolved (2009–18 VANET/WSN). Defenses: IDS/channel shutdown/filtering [87][88].

**Signal injection, spoofing, model-evasion, and jamming candidates**

Adversarial training is also supported as a robustness measure. Training with adversarially corrupted data hardened the classifier against environmental perturbations. A domain-adversarial protocol used a secondary domain-classifier head and a gradient-reversal layer: device-identity loss was minimized while domain-classifier loss was maximized. In that RF-fingerprinting experiment, a model trained on **2 or 3 days** of data maintained **70% classification accuracy** on data captured on subsequent days; these values apply to an RF-fingerprinting classifier, not to Wi-Fi sensing [89]. The same source recommends combining AI-based waveform checks with established jamming and spoofing countermeasures [89].

**Evidence-qualified attack candidates**

For **replay**, generic evidence dates to **2002**, but that date applies to replay in communications, not to a Wi-Fi-sensing or CSI replay technique [91]. The basic mechanism is capture, interception, delay, and retransmission of a legitimate message; the generic educational example calls this a “Replay Attack (Copy-Paste Attack)” and recommends timestamps and session tokens [95]. CHAP illustrates a fresh random nonce, a shared secret, response hashing, server-side comparison, and a different challenge for each authentication attempt [91]. In the SRTP example, a 16-bit sequence number plus a 32-bit rollover counter forms a 48-bit packet index; a 64-entry replay window gives \(1-64/2^{16}\approx99.9\%\) discard likelihood for a random sequence number [91]. These mechanisms are not direct evidence for Wi-Fi-packet or CSI replay, so that candidate remains **uncertain/unresolved**.

Loc spoofing—active; ToA delay/SNR loss corrupts location; IoT single-/multi-AP NN defense (3 Dec 2023), not Wi‑Fi; CSI spoofing unresolved [100].

CSI-based localization: passive/active unauthorized sensing; infers location/presence; localization/gestures; defense: CSI obfuscation; public 2022; day unresolved [104]

Unauthorized/covert Wi‑Fi sensing—Secur‑Fi: A Secure Wireless Sensing System Based on Commercial Wi‑Fi Devices (CSI localization)—is passive for rogue-receiver eavesdropping; active with attacker-controlled transmission/injection [39][105][106]. Objective: infer private behavior, position/activity and tracking without consent [39][106]. Scenarios: passive tracking, behavior/breath recognition, localization/position, activity/gesture recognition, empty-room detection; home/medical [39][106]. Defenses: Secur‑Fi fraud signals block sensing/recover authorized sensing; CSI pre-distortion/reflection obfuscation; reactive jamming unproven [39][105]. Mechanism/limits: through-wall strong frames; CSI/ML fingerprints fixed geometry, requiring attacker training (8 positions); users unaware [106]. Commercial-device results: 130%/72%/86% accuracy reduction for tracking/behavior/breath; denominator/population absent; 130% verbatim [39][105][106]. Dates/status: Secur‑Fi 17–20 May 2023 (Xplore 29 Aug 2023); AntiSense: Standard-Compliant CSI Obfuscation Against Unauthorized Wi‑Fi Sensing (Cominelli, Gringoli & Lo Cigno), preprint submitted 19 Nov 2021, access date unstated; taxonomy not standardized [39][105][106].

The documented mechanism is broader wireless spoofing: an attacker monitors communications for layer-2 MAC addresses, forges one, and transmits as another device. Landmarks measure RSS, forward vectors to a server, and use signal-space K-means clustering; spoofing creates distinct clusters around the genuine and spoofing nodes. The source does **not** establish CSI injection or RF-waveform injection specifically [107].

The detector becomes weaker when the genuine and spoofing nodes are fewer than **10–15 feet** apart because their RSS values become similar and detection can fall below **90%**; localization is also difficult when the system lacks either node’s position, and packet-level localization performed worse than signal-space centroid clustering [107]. Evaluation used **286 802.11 locations** with **200 simulated packets per location** and **100 802.15.4 locations** with **300 packet-level RSS samples per location**. Reported source-specific results include 802.11 at **T=5.5 dB**: detection **0.9937**, false-positive rate **0.0819**; and 802.15.4 at **T=8.2 dB**: detection **0.9806**, false-positive rate **0.0957**. Other conditions report detection above **90%** at about **20 feet**, **100%** at **45–50 feet**, over **95%** overall, false positives below **5%**, and median distance error of **10 feet**; these figures concern RSS spoofing detection and are not directly transferable to CSI injection [107].

**RF signal injection/CSI spoofing:** Source names “WiFi external signal attack,” “external signal attack,” and “location spoofing attack.” It uses collected SSIDs and 51-byte forged beacons with altered source address/BSSID/timestamp; four synchronized ESP8266s, GPS jamming at 1,575.42 MHz, stronger signals and >5× spoof APs create false inputs. Targets Wi-Fi localization/positioning, navigation and location apps. [108] Evaluation: static designed distance 6.91 m and error 3.23 m; dynamic 3.35±1.16 m versus 0±15.23 m normal (95% CI), standard errors 9.26±8.53 versus 8.74±6.44; over 90% of errors were below 15 m. [108]

**Wi-Fi sensing signal/CSI injection:** A real-world smartphone test produced false city results (New York, Paris, London, and Berlin), but no named CSI or human-sensing test; sensing-specific status, first-public date, dataset denominator, and independent provenance remain unresolved. [108]

AP impersonation/replacement—active; forged beacons+jamming→false WLAN location/DoS; Skyhook iPhone/iPod/Loki, WLAN/hybrid-GSM; defenses: beacon/mutual auth, ns challenge, AP fingerprints, consistency checks, DB controls, IP geolocation; date 2012-01-01 (related security works 2003–08; first disclosure uncertain) [102].  
Location spoofing/manipulation—active; insertion/replay/jamming/DB edits→wrong/unavailable location; WLAN positioning, not explicit Wi-Fi sensing; possible defenses as above, not sensing-evaluated [102].  
Replay of beacons—active; transmit/jam gear; iPhone spoofing persisted within 1 km of GSM accuracy; no sensing metric/study; enabling date 2012-01-01 [102].

AP impersonation: active forged-beacon; spoofs/denies WLAN localization; 2009; sensing-security analogue [103]. Localization spoofing/manipulation: active forged/replayed/relayed/jammed signals/DB changes; in no-AP/WLAN-only/WLAN-GSM localization; defenses: fingerprints/authentication/challenge-response, history/database/consistency checks [103].

**Location spoofing/database manipulation**—active; false/denied WLAN positions via forged/replayed beacons, jamming, spoofing/DB poisoning; AP-absent, WLAN-only, hybrid WLAN/GSM, PC plug-in; MobiSys’09, 22–25 Jun 2009; defenses: history/fingerprints/authentication, DB consistency/rescans, GSM cross-check [103]. **Wi-Fi sensing replay**—active; status unresolved: only 2009 public-WLAN localization replay; forged beacons/jamming; hybrid fallback, 1-km displacement; no sensing metric/dataset/denom./baseline [103].

CSI replay: no sens. metric/dataset/pop./base; WLAN/GSM spoof: loc. 1km (2009), sensing unresolved [103]. AP impersonation active: fake beacon/jam; BSSID/ESSID chk [111][112]

Sensing jamming=active RF/SDR; denies sensing; ∼10–30m+sync [38]. Limits: lab/confounders; detection untested [38]. Date/status: sensing unresolved; general May 2005 [116].

Wi‑Fi sensing jamming: active DoS disrupting frequency [117]; RF fingerprinting identifies jammers; 01 October 2013 enabling method [101]. Attack date unresolved; benign cause [115].

Passive CSI/packet eavesdropping is represented by passive CSI-based keystroke eavesdropping, and passive Wi‑Fi sensing privacy inference is relevant because that CSI exposes sensitive typing activity; passive physiological/typing inference is directly demonstrated, while passive localization/person-tracking inference is relevant through the documented security risk to Wi‑Fi positioning, although the localization evidence here establishes spoofing rather than a passive-inference mechanism [61] [71] [81]. Wi‑Fi sensing jamming/interference supplies the availability/integrity counterpart by actively altering CSI to cause sensing errors, denial of service, or identity spoofing; the defense implication is PDR/signal-strength checking and channel switching, but congestion, device failure, or a moving sender can mimic jamming, and a demonstrated reactive implementation responds in less than 30µs [44] [78] [64] [55] [50].

RF signal injection or CSI spoofing directly relates to secure Wi‑Fi sensing as an active integrity threat: the attacker monitors communications to obtain layer-2 MAC addresses and forges a transmitter identity, while CSI-phase manipulation affects localization [107] [46]. Cryptographic authentication and RSS-based K-means detection/localization of the adversary provide corresponding defenses, linking the attack to both sensing integrity and defense design [107] [46].

RF signal injection or CSI spoofing makes a substantive survey row: Wireless spoofing monitors layer-2 traffic and forges a MAC identity to masquerade as another transmitter, with identity compromise as the objective [107]. It targets localization estimation—angle of arrival, distance estimation, and spatial localization—and can be paired with cryptographic authentication, RSS-based K-means spoofing detection/localization, and phase perturbation [46] [107].

Device or AP impersonation is relevant as a related identity, integrity, and localization threat: an active rogue AP pretends to be an organization AP and can convince a device that it is at a false position, although the cited source does not establish a Wi‑Fi-sensing-specific application [77] [102] [103]. WIDS can validate beacon BSSID and ESSID, while client-side integrity checks can use location history to detect implausible displacement [112] [111].

Device or AP impersonation supplies a substantive row with AP Impersonation and forged AP beacons as the method, an active rogue-AP attack type, and location spoofing as the objective; the concrete sensing scenario is not established in the cited material [77] [102] [103]. WIDS beacon BSSID/ESSID validation and location-history checks for implausible displacement provide candidate defenses [112] [111].

rejected: no_entity. Unauthorized or covert Wi-Fi sensing directly serves the secure Wi-Fi sensing attack-and-defense purpose as a privacy threat: a passive rogue receiver eavesdrops on legitimate signals, whereas an active adversary controls a transmitter as well, to infer private location and activity [45] [39] [104]. It therefore merits a row covering indoor localization, passive tracking, behavior/activity recognition, and breath detection; AP-side CSI pre-distortion is limited to passive attacks, while active on-air obfuscation can address both attack classes and Secur-Fi generates fraud signals and recovers the signal [48] [39] [104] [43]. Allowed numbers: ['', '2024', 'Spring 2006', '3 December 2023', '2002', '2012-01-01', 'MobiSys’09, June 22–25, 2009', 'April 16, 2008', '10-15 feet', '2025', 'May 2005', '2012-08-02', '2009']; allowed citations: [30, 106, 136, 146, 162, 206, 217, 218, 224, 226, 227, 229, 233, 240, 241, 242, 243, 280, 281, 282, 286, 287, 293, 295, 325, 326, 338, 339, 343, 345, 347, 348, 349, 377]; allowed entities: Unauthorized or covert Wi-Fi sensing by a rogue receiver or transmitter; Passive physiological/typing inference; Wi-Fi sensing jamming/interference; Wi-Fi sensing signal injection/spoofing; Wi-Fi sensing replay attack; Unnoticeable communication-packet perturbation adversarial attack; Wi-Fi sensing model-evasion adversarial examples; Localization spoofing or manipulation; Unauthorized or covert Wi-Fi sensing; RF signal injection or CSI spoofing; Replay of Wi-Fi packets or CSI; Device or AP impersonation for unauthorized sensing.

rejected: no_entity. Replay of Wi-Fi packets or CSI is relevant to the secure-sensing purpose as an integrity and freshness attack: previously recorded signals or valid messages can be retransmitted so that a receiver accepts stale authentication material again [91] [99] [110]. Fresh random nonces, secure packet variations or TLS message authentication, and replay detection are the corresponding defenses, so sensing packets or CSI used for a decision should be bound to freshness [97] [91] [98]. Allowed numbers: ['', 'late 2017', '2016', '2002', '2024', 'Spring 2006', '3 December 2023', '2012-01-01', 'MobiSys’09, June 22–25, 2009', 'April 16, 2008', '10-15 feet', '2025', 'May 2005', '2012-08-02', '2009']; allowed citations: [30, 146, 217, 218, 224, 226, 227, 229, 233, 240, 241, 242, 243, 280, 281, 282, 286, 287, 290, 291, 293, 295, 325, 326, 348, 349, 354, 377]; allowed entities: Replay of Wi-Fi packets or CSI; Passive physiological/typing inference; Wi-Fi sensing jamming/interference; Wi-Fi sensing signal injection/spoofing; Wi-Fi sensing replay attack; Unnoticeable communication-packet perturbation adversarial attack; Wi-Fi sensing model-evasion adversarial examples; Localization spoofing or manipulation; Unauthorized or covert Wi-Fi sensing; RF signal injection or CSI spoofing; Device or AP impersonation for unauthorized sensing.

rejected: no_entity. Replay of Wi-Fi packets or CSI is a substantive row: the attacker captures a legitimate message or signal and sends it again to make the receiver accept a previously valid message, with replay detection and protection as the defense [110] [99] [91]. The cited material is protocol-level and does not establish a concrete sensing application, so the direct sensing scenario remains unresolved even though freshness controls are relevant to sensing integrity [91] [98]. Allowed numbers: ['', 'late 2017', '2016', '2002', '2016 calendar year', '2024', 'Spring 2006', '3 December 2023', '2012-01-01', 'MobiSys’09, June 22–25, 2009', 'April 16, 2008', '10-15 feet', '2025', 'May 2005', '2012-08-02', '2009']; allowed citations: [30, 146, 217, 218, 224, 226, 227, 229, 233, 240, 241, 242, 243, 280, 281, 282, 286, 287, 290, 291, 293, 295, 325, 326, 348, 349, 354, 377]; allowed entities: Replay of Wi-Fi packets or CSI; Passive physiological/typing inference; Wi-Fi sensing jamming/interference; Wi-Fi sensing signal injection/spoofing; Wi-Fi sensing replay attack; Unnoticeable communication-packet perturbation adversarial attack; Wi-Fi sensing model-evasion adversarial examples; Localization spoofing or manipulation; Unauthorized or covert Wi-Fi sensing; RF signal injection or CSI spoofing; Device or AP impersonation for unauthorized sensing.

## Part 2 — Defense Technology Overview

### Active transmitter and traffic defenses

| Defense Method Name | Defense Type | Defense Objective | Sensing Scenarios Applied | Targeted Attack Types |
|---|---|---|---|---|
| AP-based customized cover-signal obfuscation [22] — 2020 | Active — signal-side prevention | Make motion-induced measurements ambiguous | G:O; A:O; L:C; presence/movement | Passive external RSS/CSI reconnaissance |
| Randomized CSI/preamble pre-distortion [23] — 2020/2021 | Active — transmitter obfuscation | Hide location fingerprints while retaining communication | G:O; A:O; L:D; device-free positioning | Passive CSI localization, including multiple receivers |
| BeamDancer [6] — 2024 | Active — randomized beamforming | Disrupt fingerprinting with limited communication loss | G:C; A:O; L:D; speed estimation | Passive CSI localization and micro-Doppler inference |
| Scheduled spatial sensing [24] — 2023 | Active — transmitter scheduling | Separate authorized from unauthorized sensing | G:C; A:D; L:D; localized activities | Passive CSI eavesdropping |
| MIMOCrypt [25] — 2024 | Active — physical-channel encryption | Preserve authorized multi-user sensing and communication | G:D; A:C; L:O; gesture privacy | Passive unauthorized signal/CSI inference |
| Wi-Fi signal rate limiting [11] — 2018 | Active — transmission control | Reduce observations supporting external monitoring | G:O; A:O; L:D; room monitoring | Passive ambient-signal reconnaissance |
| Wi-Fi traffic spoofing [8] — 2024 | Active — traffic-pattern modification | Obscure IoT device fingerprints | G:O; A:C; L:O; device/status inference | Passive Wi-Fi metadata analytics |
| Data-efficient packet-size obfuscation [8] — 2024 | Active — traffic shaping | Conceal size patterns with restrained overhead | G:O; A:C; L:O; IoT status inference | Passive packet-size traffic analysis |

### Active relay and propagation-environment defenses

| Defense Method Name | Defense Type | Defense Objective | Sensing Scenarios Applied | Targeted Attack Types |
|---|---|---|---|---|
| PhyCloak [10] — 2016 | Active — full-duplex relay obfuscation | Distort physical information while preserving data | G:D; A:D; L:C; SISO sensing | Passive eavesdropping and active SISO probing |
| Reactive preamble-synchronous disturbance [14] — 2020 | Active — reactive RF intervention | Obfuscate attacker-generated probing frames | G:O; A:O; L:D; device-free positioning | Active CSI localization probing |
| AntiSense [26] — 2022 | Active — artificial reflections | Blur location-dependent CSI without disabling communication | G:O; A:O; L:D; position classification | Passive and active device-free localization |
| IRShield [17] — 2022 | Active — controlled surface reconfiguration | Confuse motion-related channel observations | G:O; A:O; L:O; human-motion detection | Adversarial physical-layer motion sensing |

### Passive physical, receiver, and localization-processing defenses

| Defense Method Name | Defense Type | Defense Objective | Sensing Scenarios Applied | Targeted Attack Types |
|---|---|---|---|---|
| Static RF shielding / geo-fencing [27] — pre-cutoff synthesis 2022 | Passive — physical confinement | Restrict signals reaching unauthorized receivers | G:C; A:C; L:C; through-wall inference | Passive wireless-sensing eavesdropping |
| SCF/cyclostationarity CTI detection [15] — discussed 2021/2022 | Passive — receiver detection/recovery | Identify narrowband interference and recover subcarriers | G:O; A:D; L:O; CSI HAR | Active cross-technology interference |
| PhaseAnti [28] — 2020 | Passive — robust feature extraction | Maintain recognition under co-channel interference | G:C; A:D; L:O; indoor HAR | Interference-induced sensing degradation |
| SFKNN [5] — 2024 | Passive — server-side spatial validation | Reject inconsistent fingerprints and reduce error | G:O; A:O; L:D; UJIIndoorLoc positioning | Active AP spoofing and RSS injection |
| Robust Mean-Based Normalization, RMBN [17] — 2024 | Passive — robust localization preprocessing | Improve resistance to physical adversarial examples | G:O; A:O; L:D; fingerprint localization | Phy-Adv physical interference |

### Passive model and sensing-data defenses

| Defense Method Name | Defense Type | Defense Objective | Sensing Scenarios Applied | Targeted Attack Types |
|---|---|---|---|---|
| MIM adversarial training [19] — 2023 | Passive — model resilience | Improve accuracy under adversarial CSI inputs | G:O; A:O; L:O; apnea detection | FGSM, PGD, and MIM input perturbations |
| SecureSense [29] — online 2022 | Passive — prediction-consistency learning | Stabilize clean and attacked predictions | G:O; A:D; L:O; activity/person identification | Gaussian and white-box adversarial inputs |
| Cross-adversarial training, CAT [20] — 2024 | Passive — cross-attack training | Improve HAR robustness across perturbation levels | G:C; A:D; L:O; Wi-Fi HAR | FGSM and PGD adversarial examples |
| Privacy-enhanced federated Wi-Fi sensing [30] — online 2024 | Passive — training-data protection | Limit raw-data sharing and protect distributed updates | G:O; A:O; L:O; IoT health monitoring | Exposure of sensing data during collaborative learning |

**Defense families protect different stages:** preventive RF methods alter what an outsider can observe; detective methods identify suspicious signals or spatial inconsistencies; mitigative processing suppresses interference; resilience methods keep models useful under perturbation. Federated learning protects the handling of collected sensing data, which is a different objective from concealing the radio channel itself.

**Defense overview takeaway:** the active/passive label describes how protection operates, while the targeted-attack column identifies what it protects against; neither label alone establishes coverage of another sensing scenario.

**Additional documented evidence**

| Entity | Defense Method Name | Defense Type | Defense Objective | Sensing Scenarios Applied | Targeted Attack Types |
| --- | --- | --- | --- | --- | --- |
| Wi-Fi link-layer encryption and sensing-data confidentiality | Wi-Fi link-layer encryption [141] | Passive preventive confidentiality [141] | Confidentiality and integrity [141] | The source supports Wi-Fi link-layer encryption and…[141] | TKIP side channels; traffic interception [141] |
| Sensing authorization, access control, and consent enforcement | The page names the concept "Sensing Authorization"…[137] | The page does not establish an active or passive…[137] | The stated objective is to distinguish permission…[137] | The page supports only a conceptual Sensing…[137] | The page supports only a conceptual Sensing…[137] |
| Packet/CSI authentication and integrity verification | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| RF/device fingerprinting and source authentication | no evidence found | no evidence found | no evidence found | Real-time classification of 8 LoRa transmitters [123] | no evidence found |
| Freshness and challenge-response anti-replay controls | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Adversarial training and robust sensing models | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Input filtering, denoising, feature sanitization, and obfuscation | CSI preprocessing/sanitization/obfuscation [136][133][135] | Active/passive signal/feature transformation [133] | Improve CSI quality; limit unauthorized sensing [133] | Pose; gesture/activity; localization [136][133][143] | CSI sensing/localization attacks (passive/active) [127][143] |
| Anomaly detection, outlier rejection, and consistency checking | no evidence found | no evidence found | Detect anomalies and policy violations [128] | Wireless Intrusion Detection Systems (WIDS) are…[128] | Rogue APs, spoofing, impersonation, deauth floods [128] |
| Differential privacy, noise injection, and private feature release | no evidence found | Differential privacy is described as a mitigation…[139] | no evidence found | Differential privacy is described as a mitigation…[139] | no evidence found |
| Anti-jamming channel/frequency hopping and diversity | Channel hopping scheme; rapid channel hopping.[144] | no evidence found | The stated objective is to increase 802.11 resilience…[144] | no evidence found | The defense targets Node Frequency Jamming.[117] |
| CSI/waveform randomization and sensing obfuscation | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Multi-AP or multimodal redundancy and cross-checking | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Poisoning-resistant data curation and secure training | The source names the evaluated defense as RECESS; it…[124] | no evidence found | Resist model poisoning; preserve training accuracy [124] | no evidence found | no evidence found |
| Federated learning and secure aggregation for sensing models | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Query auditing, rate limiting, and model hardening | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Physical shielding, directional placement, and environment access control | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Physical-layer security, artificial noise, and beamforming | Physical-layer security, artificial noise, and…[126] | Active signal design; Wi-Fi defense unclear [126] | Reduce eavesdropping; preserve link reliability/delay [126] | No Wi-Fi sensing scenarios documented [126] | Passive eavesdropping; poisoning; Wi-Fi unproven [126] [89] |
| Physical-layer security, artificial noise, and beamforming | Physical-layer security, artificial noise, beamforming[126] | Active signal design; not Wi-Fi-sensing-specific[126] | Reduce eavesdropping; preserve reliability/delay[126] | None documented; generic wireless transmission only[126] | Passive eavesdropping (generic wiretap)[126] |
| Encryption and authenticated link protection for sensing data | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Mutual authentication and RF fingerprinting | The source describes passive machine-learning device…[125] | The source describes passive machine-learning device…[125] | The source describes passive machine-learning device…[125] | The page supports AP-impostor or fake-access-point…[122] | The source describes passive machine-learning device…[125] |
| Integrity, freshness, and challenge-response anti-replay controls | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Adversarial training and robust sensing-model training | Robust model training [119] | The source supports classifying robust sensing-model…[119] | Mitigate adversarial output disruption; ensure…[119] | Action recognition [119] | Adversarial attacks; output manipulation [119] |
| Anomaly, outlier, and adversarial-input detection | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| CSI or feature sanitization and privacy-preserving abstraction | The source names the method “CSI Sanitization…[133] | Passive [133] | Remove CSI artifacts; preserve motion features [133] | Activity, gesture, action, fall, people counting [133] | No named attack family [129] |
| Differential privacy, noise injection, and output randomization | Differential privacy [140] | Passive [138] | Privacy protection with utility preservation [131] | The source documents traffic-density estimation on…[131] | Privacy attacks; membership inference [138] |
| Jamming detection with channel or frequency hopping | Channel hopping [132] | Active defense [134] | The source states that the system uses cryptographic…[130] | The source-supported scenarios are military…[130] | Jamming/DoS attacks [132] |
| Multi-AP or multi-view consistency and cross-sensor verification | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Poisoning-resistant learning and secure aggregation | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Anti-jamming channel/frequency hopping and diversity | Channel hopping scheme; rapid channel hopping.[144] | no evidence found | The stated objective is to increase 802.11 resilience…[144] | no evidence found | The defense targets Node Frequency Jamming.[117] |
| Poisoning-resistant data curation and secure training | The source names the evaluated defense as RECESS; it…[124] | no evidence found | no evidence found | no evidence found | Poisoning: label/feature/property/Byzantine/backdoor [139] |
| Wi-Fi link-layer encryption and traffic confidentiality | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Sensing authentication, authorization and access control | no evidence found | The page does not establish an active or passive…[137] | no evidence found | The page supports only a conceptual Sensing…[137] | The page supports only a conceptual Sensing…[137] |
| Packet/CSI integrity authentication and provenance | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Differential privacy or calibrated output noise | no evidence found | no evidence found | no evidence found | The documented sensing scenario is traffic density…[131] | Stealthy false-data injection [131] |
| CSI/feature obfuscation and privacy-preserving sanitization | The defense is named “AntiSense: Standard-Compliant…[104] | The source positions CSI/feature obfuscation and…[135] | The source positions CSI/feature obfuscation and…[135] | The source reports indoor localization experiments as…[142] | The source positions CSI/feature obfuscation and…[135] |
| Adversarial training and robust model training | no evidence found | no evidence found | Robust model training is presented as an approach to…[119] | no evidence found | no evidence found |
| Robust preprocessing, outlier detection and consistency checking | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Federated learning and secure aggregation | The source names the relevant method “Federated…[147] | no evidence found | Preserve patient privacy in collaborative training[147] | Brain-tumor, Alzheimer’s, Parkinson’s detection[147] | no evidence found |
| Query auditing, rate limiting and model hardening | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Physical shielding, directional placement and environment access control | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| RF/device fingerprinting and source authentication | no evidence found | no evidence found | Device authentication; detect spoofed transmitters [123] | The page supports AP-impostor or fake-access-point…[122] | Evil twin/fake AP; spoofed transmitters [122][123] |
| Adversarial training and robust sensing models | no evidence found | no evidence found | no evidence found | Domain adversarial training hardens the RFF…[89] | no evidence found |
| CSI/waveform randomization and sensing obfuscation | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Encryption and access control for sensing data | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Input filtering, denoising, and feature sanitization | no evidence found | no evidence found | no evidence found | Human-body/object sensing in live surveillance videos[118] | Playback and tampering attacks (video forgery)[118] |
| Anomaly detection and outlier rejection | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Anti-jamming and channel/frequency hopping | no evidence found | no evidence found | The stated objective is to increase 802.11 resilience…[144] | no evidence found | no evidence found |
| Differential privacy and privacy-preserving feature release | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |

**Confidentiality and device/source authentication**


| Defense Method Name | Defense Type | Defense Objective | Sensing Scenarios Applied | Targeted Attack Types |
|---|---|---|---|---|
| **Wi-Fi link-layer encryption and sensing-data confidentiality**; corresponding traffic-protection label: **Wi-Fi link-layer encryption and traffic confidentiality** (“Wi-Fi encryption”) | **Passive/preventive**: protects traffic through encryption rather than attack-time intervention [120] | Confidentiality and authorized access; prevent unauthorized disclosure of Wi-Fi traffic [120] | **Not reported in the source**: no evaluated mapping to gesture recognition, activity recognition, localization estimation, or another named sensing task [120] | Unauthorized disclosure, passive interception/eavesdropping, clear-text exposure, and—under the stated WPA2-Enterprise condition—man-in-the-middle interception; weak encryption also permits connection, capture, and decryption of frames [120] |
| **RF/device fingerprinting and source authentication** (including device identification) | **Defense classification not established by this source**. The demonstrated capability is passive channel monitoring; the associated traffic-spoofing and packet-size-obfuscation measures are proposed defenses [121] | Provisional source/device authentication and privacy-leakage reduction; the same evidence also documents fingerprinting as an attack capability [121] | IoT-device identification, including identification of sleep monitors and inference of whether a user is awake or asleep; no source-supported evaluation of gesture recognition, activity recognition, localization estimation, presence, or authentication [121] | Passive Wi-Fi eavesdropping and device-fingerprinting inference; defensive coverage is proposed rather than validated as a Wi-Fi-sensing countermeasure [121] |
| Physical-layer security, artificial noise, and beamforming (PLS; artificial-noise-aided signaling) [126] | Active signal design in the demonstrated generic wireless setting; classification as a Wi-Fi-sensing defense is not established [126] | Reduce passive eavesdropping while preserving legitimate-link reliability and low delay under quality-of-service constraints [126] | None documented for Wi-Fi sensing; the evaluated Alice–Bob–Eve transmission scenario is not gesture recognition, activity recognition, or localization estimation [126] | Passive eavesdropping in a generic wireless wiretap channel; coverage of Wi-Fi-sensing attacks is not established [126] |
| **CSI/feature obfuscation and privacy-preserving sanitization** (CSI obfuscation, CSI randomization, randomizing filter; CSI-MURDER) | **Hybrid:** passive when an external device passively randomizes the environment; active when a transmitter or protected device reacts to detected packets and emits artificial signal features. | Preserve privacy by making environmental CSI unusable while keeping frames decodable; prevent unauthorized localization and activity detection. | Demonstrated localization of humans, objects, and robots; precise position and rough room-sector/work-position estimation; activity detection; one testbed experiment used 10 target positions. | Passive CSI eavesdropping, localization or tracking inference; active localization attacks in which the attacker controls transmitter and receiver; activity inference by malicious eavesdroppers [127]. |
| **Input filtering, denoising, feature sanitization, and obfuscation** (directly demonstrated component: physical-layer CSI obfuscation) | **Hybrid:** passive obfuscation targets an eavesdropper, whereas active obfuscation detects packets and transmits artificial tones or spurious CSI. | Reduce privacy leakage from sensing features and defeat passive or active environment-sensing attacks while retaining communication utility. | Device-free CSI localization of people, objects, and robots, including precise positions, room sectors, work positions, and activity detection; demonstrated in Brescia and the w.iLab.2 testbed. | Passive localization/tracking and activity inference, plus active localization attacks and unauthorized CSI use [127]. |
| Anti-jamming channel/frequency hopping and diversity (aliases: channel hopping, frequency hopping, sensing anti-jamming) | **Active** availability defense: it changes the operating channel, radio configuration, or power rather than merely observing the channel. This is a report-level classification based on the documented channel-management mechanism [86]. | Avoid interference-induced denial of service and preserve radio-link or WLAN availability. Direct preservation of a Wi-Fi-sensing output is **not established** in the cited source [86]. | **Not established** for gesture recognition, activity recognition, localization estimation, presence, typing, physiological sensing, or authentication. The source reports only generic IEEE 802.11 interference and coverage conditions [86]. | RF jamming, radio interference, and availability-denial attacks. The mapping is direct for generic WLAN availability but only **partial/adapted** for Wi-Fi-sensing disruption because no sensing evaluation is reported [86]. |
| Anti-jamming and channel/frequency hopping (aliases: channel hopping, frequency agility) | **Active** channel-adaptation and availability defense; the source supports channel hopping and radio-channel management but does not label this as a sensing-specific defense [86]. | Reduce the likelihood that interference makes the wireless service unavailable. A sensing-specific robustness or accuracy objective is **not reported** [86]. | **Not established** in the cited evidence; no demonstrated sensing task or protected sensing population is specified [86]. | Jamming, radio-frequency interference, and WLAN denial of service; sensing-specific mitigation remains **unresolved** [86]. |
|Channel hopping|Active|Av.|Wi-Fi NR; WSN PDR+>50%/−20%E/15ms/100n;08/14?|Proactive; reactive/persistent bypass[145][146]|

For the two confidentiality entries, the mechanism is encryption of Wi-Fi frames and traffic so captured transmissions are not readable as clear text. The source reports that WEP used vulnerable RC4; WPA2 moved to AES; WPA2-Personal uses a pre-shared key for authentication and encryption, but a known key can decrypt captured traffic; WPA2-Enterprise provides strong AES encryption and can protect against man-in-the-middle attacks under correct implementation. WPA3-Personal replaces PSK with SAE-based key exchange, so the connection password cannot decrypt captured frames [120]. These qualifications matter: encryption protects confidentiality, but weak configuration, compromised credentials, and implementation errors reduce coverage [120].

The source lists WEP (**1999**), WPA (**2003**), WPA2 (**2004**), and WPA3 (**2018**) as standard dates, but does **not** establish the earliest public availability of encryption specifically as a Wi-Fi-sensing defense; that date therefore remains unresolved in the evidence record [120]. The confidentiality entries belong in the defense part of the survey as preventive controls against observation and traffic disclosure, while their scenario-specific protection remains unestablished [120].

RF/device fingerprinting is relevant to secure Wi-Fi sensing because passive monitoring can expose device identity and private-state information without joining the victim network. The source reports a **May 2024** release and **2024** completion date for the enabling dissertation, making the cited evidence pre-cutoff, but it does not prove that May 2024 was the technique’s first public disclosure [121]. Its demonstrated status is passive IoT-device fingerprinting; traffic spoofing and packet-size obfuscation are described as introduced or proposed defenses. The source is Mnassar Alyami’s University of Central Florida dissertation, *Internet-of-Things Privacy in WiFi Networks: Side-Channel Leakage and Mitigations*, released in May 2024 [121].

## Passive attacks and privacy-preserving defenses

### Room reconnaissance: accurate inference without network compromise

**Room-level reconnaissance was already practical:** the 2018 Adversarial WiFi Sensing study evaluated a passive outside-the-building attack in 11 real-world settings, including offices and residential apartments. A commodity smartphone first estimated the locations of interior Wi-Fi anchors from spatial RSS measurements, then used ambient-signal changes to monitor occupants. The attack assumed rough floorplans and an adversary able to move outside the target area. [11]

**Anchor localization enables interpretation:** observing a changing signal is more useful when the attacker knows which interior device produced it and approximately where that device sits. The study combined RSS model fitting, 1,000 Monte Carlo samples per measurement round, clustering, and consistency checks across four rounds. It reported **92.6% average room-level anchor-localization accuracy** after that consistency check. This is localization of the reference devices, not a claim of centimeter-level human positioning. [11]

**Multiple anchors strengthen presence inference:** reported presence recall was 87.8% with one anchor, 98.5% with two, and 99.8% with three, with 99.95% precision. Recall measures the fraction of actual presence events detected; precision measures the fraction of positive detections that are correct. The figures therefore describe a particular presence-detection operating point, rather than interchangeable percentages of general sensing accuracy. [11]

**The temporal and spatial scales matter:** the monitoring method used five-second windows advanced by 2.5 seconds. A typical anchor trigger range was approximately 3 m, and two or three anchors covered a standard 10 ft × 15 ft room in the reported setting. These parameters explain why dense smart-device deployments help room monitoring, but they do not turn the result into fine-grained gesture recognition. The reported output also stopped short of identifying individual occupants or counting them. [11]

**AP obfuscation directly attacks the measurement:** the later Et Tu Alexa? demonstration proposed having the access point inject customized cover signals for associated devices. Its reported human-detection rate fell to 47%, while the false-positive rate rose to 50%. The change required modification of the AP rather than every household device. [22]

**The two rates must travel together:** a 47% detection rate is not, by itself, evidence that privacy is protected. The accompanying 50% false-positive rate shows why the attacker’s positive observations became ambiguous: measurements suggested human motion frequently even when that interpretation was wrong. The relevant effect is degradation of useful discrimination, not simply a reduction in one headline percentage.

**Traffic reduction has a narrower advantage:** rate limiting reduces the number of observations available from legitimate traffic, while geo-fencing restricts where useful signals propagate. Neither requires an attacker to reveal itself before protection begins. Their practical value depends on whether communication and authorized sensing can tolerate the resulting coverage or sampling constraints; the 2018 study considered both alongside signal obfuscation. [11]

### Activity semantics: why the attacker need not occupy the legitimate receiver’s position

**ActListener addresses spatial mismatch:** its 2022 attack did more than feed arbitrary eavesdropped CSI into an existing activity classifier. It detected activity-induced signal segments, estimated relative device and victim geometry, modeled propagation, converted observations toward signals expected at legitimate devices, and calibrated noise using a generative model. This pipeline explains how an eavesdropper can recover semantics despite observing a different wireless path. [3]

**The measured recovery was substantial:** the 2022 experiments reported 88.4% average α-similarity in recovered signals and over 90% activity-recognition accuracy. Signal similarity and semantic accuracy answer different questions: the former evaluates reconstruction under the paper’s similarity measure, while the latter evaluates the usefulness of that reconstruction for recognizing activities. Their combination supports a practical privacy concern rather than merely showing that wireless samples are correlated. [3]

**Behavioral identity extends the consequence:** the 2024 extension added user-identification models to its substitute-model set and calibrated individual behavioral patterns. It reported over 80% accuracy for activity-semantics retrieval and impersonation using converted signals. That result connects activity observation to identity-related exploitation, particularly where sensing-derived behavior participates in authentication. [12]

**The acquisition label remains precise:** ActListener’s signal collection is passive because the adversary eavesdrops on ambient transmissions. Synthesizing converted signals for an impersonation objective is a further capability, however, and the passive label should not be extended automatically to every possible deployment of those signals. The catalog therefore classifies the demonstrated acquisition mechanism and identifies the extension’s objective separately.

**Model access control has a boundary:** restricting access to an authorized activity classifier does not remove the observations available to an external receiver. Scheduled spatial sensing explicitly considers an attacker using an environment-independent model, and ActListener constructs a substitute-model pipeline. Consequently, privacy protection must address signal acquisition or interpretability as well as access to the legitimate model. [24][3]

### Localization fingerprints: changing what the attacker learns

**Receiver diversity strengthens the attacker:** Cominelli, Gringoli, and Lo Cigno’s 2021 multi-point work examined how multiple attacker-controlled receivers improve the precision and robustness of device-free CSI localization. The method used convolutional-neural-network fingerprinting: labeled observations associate characteristic channel responses with positions. Multiple observation points add complementary evidence rather than requiring the victim to carry a transmitter. [13]

**Transmitter randomization breaks fingerprint stability:** the corresponding defense introduces a time-varying distortion before the signal propagates. An unauthorized receiver then observes a mixture of environmental structure and defender-controlled variation, weakening the position-to-fingerprint relationship. The 2021 multi-receiver study reports that properly randomized pre-distortion can prevent localization even with multiple attacker-controlled receivers. [13]

**The physical mechanism is compact:** Lo Cigno and colleagues express the received spectrum as the transmitted spectrum multiplied by the channel response. Their obfuscation adds a frequency- and time-dependent multiplier, \(O(f,t)\), which the receiver encounters as part of an effective channel. [1]

\[
S_R(f,t)=S_T(f,t)\,O(f,t)\,H(f,t).
\]

**Communication and sensing use that channel differently:** a communication receiver estimates the effective distortion so it can recover transmitted symbols. A sensing algorithm interprets the distortion as evidence about the environment. A carefully designed multiplier can therefore make environmental inference unreliable while still permitting equalization and data reception. That separation is the technical basis of communication-preserving privacy defenses, rather than a contradiction between privacy and successful reception.

**Not every random filter works:** the empirical 2021 pre-distortion study found randomly placed peaks effective against its localization framework, while tested random notches and phase jumps had negligible effects. Its selected filters used 5–10 peaks, widths of 2–6 frequency samples, and 80 MHz transmissions with 256 subcarriers. These results show that useful obfuscation depends on the sensing features being attacked, not simply the presence of added randomness. [23]

**A shared example illustrates the trade-off:** the 2022 IEEE Network analysis reported an eight-position localization classifier with 95% average accuracy on clean observations. Transmitter-side obfuscation and an external-reflection scenario reduced average accuracy to 20% and 17%, respectively. Uniform guessing among eight positions is 12.5%, calculated as \(1/8\); that comparison provides an interpretable reference without treating the two protected scenarios as identical deployments. [1]

| Reported configuration | Attacker setting | Average position accuracy | Communication observation |
|---|---|---:|---|
| Clean observations | Eight-position fingerprinting | 95% | Reference link |
| Transmitter-side obfuscation | Passive receiver | 20% | Highest tested rates affected |
| External-reflection obfuscation | Active/passive setting | 17% | Little impact in the example |

**Low average accuracy needs interpretation:** the external-reflection example strongly favored one output position, including 100% accuracy when the true position happened to match that favored class. This illustrates why a confused classifier can retain isolated high class-specific results while becoming broadly uninformative. It also explains why a privacy evaluation should examine the confusion pattern rather than rely entirely on average accuracy. [1]

**Transmitter control defines the protection boundary:** the same analysis explicitly states that transmitter-side obfuscation addresses passive attacks because an attacker controlling its own transmitter can omit the obfuscation. This is decisive for active probing and malicious-client localization attacks. A defense installed only in the legitimate AP does not govern every signal an adversary can introduce into the environment. [1]

### Relays, reflections, and native beamforming

**PhyCloak protects physical information selectively:** its 2016 full-duplex forwarder manipulates three orthogonal signal dimensions associated with SISO sensing: amplitude gain, delay, and Doppler shift. The prototype obfuscated illegitimate sensing, supported legitimate sensing, improved overall throughput, and demonstrated feasible gesture spoofing against an illegitimate sensor of the same type. [10]

**Its advantage is not ordinary jamming:** indiscriminate jamming damages both data transmission and physical sensing. PhyCloak instead aims to distort the environmental information superimposed on the signal while preserving logical data. It is therefore a privacy-preserving alternative to broad interference, not evidence of a general anti-jamming shield. [10]

**The SISO assumption is consequential:** multiple antennas expose relative spatial information used for angle-of-arrival or time-difference-of-arrival estimation. PhyCloak discusses antenna rotation or framework extensions for that additional degree of freedom. Its SISO results should therefore inform a deployment decision differently from a defense evaluated against multi-antenna localization.

**AntiSense moves protection into the environment:** an external reflector or relay adds artificial, time-varying signal reflections that blur location-dependent fingerprints. Because the altered environment affects signals from both legitimate and attacker-controlled transmitters, the approach addresses passive and active device-free localization. Its considered fingerprinting model used a single transmitter–receiver pair and excluded coordinated multi-receiver and angle-of-arrival localization. [26]

**Reaction time constrains selective protection:** AntiSense explains that reflection delay must be well below a symbol duration, leaving insufficient time to inspect MAC addresses before reflection. The obfuscator therefore cannot simply recognize an illegitimate frame and modify only that frame. It must introduce channel variation that is hard to reverse while remaining compatible with legitimate communication. [26]

**IRShield provides another environmental route:** the pre-cutoff role-based synthesis describes its controlled reflecting-surface configurations as confusing the channel seen by an eavesdropper. It summarizes a reduction of Wi-Fi human-motion-detection attack success to below 5%. This is a motion-detection result, so the catalog does not convert it into a gesture-recognition or coordinate-localization guarantee. [17]

**BeamDancer emphasizes deployability:** instead of adding a full-duplex relay or environmental radio component, it continuously randomizes beamforming vectors using native commodity Wi-Fi capabilities. Its evaluation covered supervised localization, unsupervised localization clustering, and model-based micro-Doppler speed estimation in line-of-sight and non-line-of-sight conditions. [6]

**Its utility result is baseline-relative:** BeamDancer retained, on average, more than 96% of the original packet-delivery ratio in line-of-sight scenarios, with slight degradation in most non-line-of-sight cases. This means the protected-to-original delivery-ratio relationship exceeded 0.96 on average; it does not assert an absolute packet-delivery ratio above 96% under every channel condition. [6]

### Preserving sensing for authorized users

**Spatial scheduling creates an information advantage:** Hernandez and Bulut’s 2023 method selects among spatially distributed transmitter antennas according to a schedule shared with legitimate receivers. The authorized receiver can preserve transmitter identity in its CSI representation; an eavesdropper lacking the schedule mixes observations from different propagation paths. The defense changes interpretability rather than preventing packet reception. [24]

**The experiment used a concrete home setting:** five ESP32 transmitters were spaced 70 cm apart in a 2.8 m × 3.2 m room, with a receiver in an adjacent room. Each transmitter contributed 20 Hz during collection, yielding 100 Hz aggregate CSI. Five labeled activities—Door, Sit, Stand, Closet, and Empty—were repeated three times for training and three for evaluation; scheduling was emulated from those observations. [24]

**The paired utility comparison is informative:** across three selected scheduling configurations, authorized-receiver accuracy ranged from 86.12% to 88.19%, while eavesdropper accuracy ranged from 40.60% to 40.94%, averaged over 25 repetitions per configuration. Because the activity classes were tied to positions, this supports localized activity sensing, rather than a separate meter-scale positioning result. [24]

**Residual inference remains practically relevant:** uniform guessing across five classes is 20%, calculated as \(1/5\). An eavesdropper near 40% accuracy therefore retains information even though the authorized receiver performs substantially better. The useful conclusion is selective degradation with preserved legitimate utility, rather than complete removal of all activity leakage.

**Repeated schedules can reverse the benefit:** an advanced attacker achieved 86.20% average accuracy under periodic schedules versus 56.58% under non-periodic schedules, each evaluated across 50 schedules. The calculated difference is 29.62 percentage points. This is a concrete counterexample to the assumption that adding multiple transmitters automatically improves privacy: learnable repetition can expose structure that the defense intended to conceal. [24]

**MIMOCrypt makes authorization explicit:** the 2024 framework uses multiple-input multiple-output, or MIMO, transmission to physically encrypt Wi-Fi channels, treating sensed human activities as physical plaintexts. Legitimate users receive decryption keys through a secure conveyance mechanism. Its SDR prototype emphasizes privacy-sensitive gesture recognition and realistic multi-user sensing. [25]

**The optimization has three objectives:** MIMOCrypt balances eavesdropping risk, sensing accuracy, and communication quality. This differs from a defense that simply makes sensing difficult for everyone. Its suitability depends on legitimate-user key distribution and the ability to maintain an authorized sensing path, making it especially relevant when privacy and continued sensing are simultaneous requirements. [25]

### Packet metadata requires a separate defense path

**Encrypted payloads leave behavioral patterns:** Alyami’s May 2024 dissertation shows how passive Wi-Fi monitoring can fingerprint IoT devices without joining the network. Packet inter-arrival times and sizes can reveal device categories and private status, illustrated by distinguishing a sleep monitor and inferring whether its user is awake or asleep. [8]

**The causal chain differs from CSI:** the attacker first identifies a characteristic traffic pattern, associates it with a device or state, and then interprets changes in that pattern. Human movement need not be the physical cause of a channel fluctuation. Consequently, radio-channel obfuscation and traffic-pattern obfuscation protect different links in the inference chain.

**Traffic defenses modify those observables:** the dissertation proposes traffic spoofing within the Wi-Fi channel and data-efficient packet-size obfuscation. Its design motivation is to avoid the large data overhead and deliberate transmission delays associated with some traffic countermeasures. The relevant engineering comparison is therefore privacy gain against traffic volume, delay, and application responsiveness. [8]

**Privacy defense takeaway:** protect the observable that carries the private information, and preserve an explicit advantage for authorized sensing when continued sensing is part of the requirement.

## Active attacks and sensing-integrity defenses

### Interference can damage sensing before communication fails

**IS-WARS targets channel estimation:** it injects cross-technology interference from coexisting protocol signals, with ZigBee, Bluetooth, and LTE-Unlicensed discussed as sources. The studied Wi-Fi human-activity-recognition setting focuses on 2.4 GHz. Contaminated radio observations distort CSI estimation, which then changes the features supplied to the activity classifier and produces false recognition. [15]

**Low power contributes to stealth:** the paper discusses ZigBee transmission at as little as 1 mW and a 10–100 m transmission range as feasibility anchors. These figures explain why a small interferer may affect a nearby sensing deployment while avoiding obvious channel disruption; they should not be read as a universal successful-attack radius. The attack is deliberately constrained to preserve ordinary Wi-Fi decoding sufficiently to remain inconspicuous. [15]

**Safety consequences follow classification semantics:** a fall-monitoring system may continue receiving packets yet classify a fall as an ordinary activity. In that situation, network availability and sensing correctness diverge. IS-WARS explicitly uses elder-care and surveillance contexts to illustrate the consequence of false recognition, rather than treating all interference as a simple throughput problem. [31]

**Selective CSI loss provides another route:** the 2023 physical-world behavior-recognition attack uses controlled jamming to create physically online adversarial samples. Across four real-world Wi-Fi behavior-recognition systems, it reported 80% untargeted and 60% targeted attack success, with generalization to user authentication. The underlying interference can mimic plausible CSI losses, linking measurement availability to eventual classification integrity. [16]

**Generic denoising does not establish security:** IS-WARS discusses smoothing, low-pass filtering, principal component analysis, interpolation, Kalman filtering, and wavelet transforms. Such processing can remove ordinary noise, but a malicious perturbation distributed within the sensing-relevant signal structure may survive. The important distinction is between cleaning incidental interference and resisting interference selected specifically to change the sensing output. [15]

**SCF detection has a frequency boundary:** the spectral correlation function, or SCF, exploits cyclostationary structure—statistical patterns that repeat over time—to identify cross-technology interference. The IS-WARS discussion describes detection and affected-subcarrier recovery when interference occupies a small frequency range. Carefully distributing interference across many subcarriers weakens that advantage, so the mechanism is most persuasive against concentrated CTI rather than an adaptive universal attacker. [15]

**PhaseAnti supplies complementary resilience:** its 2020 method extracts nonlinear phase-error variation after removing irrelevant CSI phase effects, then filters, calibrates, segments, and selects subcarriers. It reported 95% average activity-recognition accuracy, up to 16% recognition-accuracy improvement under co-channel interference, and recognition nine times faster than the compared state-of-the-art solution. These are CCI-resilience results, not a direct head-to-head defeat of malicious IS-WARS interference. [28]

**The resulting defense choice is layered:** receiver monitoring can identify interference or suspicious loss patterns, robust features can reduce sensitivity to particular disturbances, and model training can address remaining input perturbations. This combination is a deployment judgment, not a claimed measured composite system. Its value depends on whether the deployed receiver exposes the raw measurements needed to distinguish environmental motion from adversarial contamination.

### Physical adversarial attacks require more than a modified data array

**WiADv targets gesture-specific propagation:** a pre-cutoff synthesis describes full-duplex devices that simulate gesture-induced dynamic multipath, with phase and feature changes designed to induce a targeted label. It identifies black-box Constant Attack and Greedy Attack strategies and reports attack success above 70% on Widar3.0. The direct application is gesture recognition, rather than a demonstrated universal attack across every sensing task. [17]

**Non-differentiable preprocessing shapes the attack:** Wi-Fi sensing often transforms raw CSI before classification. If an attacker cannot differentiate through that processing chain, ordinary gradient access to the final classifier is insufficient for straightforward optimization. WiADv’s black-box strategies address this practical obstacle, illustrating why the preprocessing pipeline belongs inside the threat model rather than being treated as a neutral input adapter.

**WiIntruder broadens the application range:** its April 2024 preprint reports a one-antenna over-the-air attack designed around universality, robustness, and stealth. It seeks cross-model transfer, accounts for device desynchronization and wireless-channel distortion, and switches among perturbation surrogates generated using a generative adversarial network. The activity-recognition evaluation includes a gesture-recognition model, alongside respiratory monitoring, authentication, and indoor localization. [18]

**Its results concern reported degradation:** the paper gives accuracy degradation of 79.6% for activity recognition, 65.2% for respiratory-state monitoring, 68.3% for user authentication, and 78.4% for indoor localization, with low detection probability. These values describe the paper’s degradation metric, rather than final attacked accuracies. They establish breadth across application categories but do not provide a common success-rate ranking against FooLoc or ActListener. [18]

**Changing perturbations counters pattern-based detection:** WiIntruder notes that a static universal perturbation can be vulnerable to existing defenses. Generating and switching multiple surrogates diversifies the attack pattern while retaining the underlying adversarial objective. The implication is that a detector trained to recognize one fixed artifact may perform differently against a family of physically related perturbations. [18]

**Pilot manipulation attacks the estimator directly:** Li and colleagues’ 2024 MobiCom work changes pilot or long-training symbols within communication packets. The receiver estimates its channel using an expected training sequence; a controlled change in the transmitted sequence can therefore appear as a change in the estimated channel. The attack optimizes this pilot-to-CSI relationship rather than assuming arbitrary direct control of the receiver’s CSI array. [2]

**The reported trial had substantial scope:** the evaluation involved 35 volunteers across three universities over three months, using activity recognition and user identification. Application-specific attack success was 90.47% for activity recognition and 83.83% for user authentication. The paper separately summarizes untargeted success above 85% and targeted success at 85%; those are distinct aggregations and should remain separate. [2]

**Physical transfer has identifiable conditions:** neighboring Wi-Fi interference, furniture changes, and hardware imperfections can degrade the pilot attack. The authors use channel augmentation and synthesized hardware noise to improve robustness on commercial devices. This makes environmental variation a factor in attack effectiveness, but not a dependable defense by itself: the attacker can optimize against that variation. [2]

**The integrity implication is specific:** a valid packet and a plausible-looking channel estimate need not represent an untampered physical observation. Candidate protections therefore include checking consistency across training fields, antennas, time, or trusted observations, together with perturbation-aware learning. Such validation must respect real channel variability; otherwise it risks rejecting legitimate motion or mobility.

### Model-input attacks and robust learning

**The apnea experiment permits a direct comparison:** Ambalkar and colleagues’ INFOCOM 2023 poster evaluated FGSM, PGD, and MIM against a convolutional-neural-network classifier using Wi-Fi CSI for apnea detection. Clean accuracy was 0.85. At perturbation level 0.8, PGD reduced accuracy to 0.29 and MIM to 0.25; FGSM produced an approximately 0.45 decrease. [19]

| Attack | Perturbation setting | Clean accuracy | Attacked accuracy |
|---|---:|---:|---:|
| FGSM | 0.8 | 0.85 | ≈0.40, estimate |
| PGD | ε = 0.8 | 0.85 | 0.29 |
| MIM | ε = 0.8 | 0.85 | 0.25 |

**The FGSM value is a calculation:** estimated attacked accuracy is \(0.85-0.45\approx0.40\), using the reported baseline and approximate decrease. The perturbation parameter belongs to the study’s input representation; it is not 0.8 W, 0.8 dB, or a directly transferable RF power budget. This distinction is essential when comparing digital adversarial examples with physical transmission attacks.

**Momentum and iteration change the search:** FGSM applies a gradient-directed perturbation in one principal step. PGD iteratively searches within a permitted perturbation region, while MIM incorporates momentum across updates. The poster also discusses PGD transferability as a concern, motivating MIM; successful white-box optimization and reliable transfer to another model are different properties. [19]

**Adversarial training recovers only part:** adding adversarial examples during training increased reported MIM-attacked accuracy from 0.25 to 0.51. That is a calculated gain of 26 percentage points, while remaining 34 percentage points below the 0.85 clean baseline. The result supports meaningful mitigation, but it also shows why “adversarially trained” should not be interpreted as equivalent to clean-operation reliability. [19]

**SecureSense emphasizes prediction consistency:** its learning framework aims to keep predictions consistent between clean and adversarially perturbed inputs, reducing attack-induced distribution shift. The study evaluates wireless human-activity recognition and person identification against black-box Gaussian inputs and modern white-box attacks. Its contribution is a model-side robustness mechanism, distinct from a method that prevents an external receiver from collecting CSI. [29]

**CAT compares training strategies explicitly:** cross-adversarial training attacks source-domain data across batches, filters perturbation thresholds, and uses cross-zero sampling across positive and negative perturbation intervals. In its 2024 Wi-Fi HAR experiments, CAT exceeded its standard-adversarial-training comparator by average reported accuracy differences of 10.37% under FGSM and 16.33% under PGD. [20]

**Training quality matters as much as presence:** the CAT paper reports that its standard adversarial training comparator decreased performance relative to the original model under the tested attacks. This is an important counterexample to treating every augmentation procedure as beneficial. The distribution of perturbation magnitudes, attack construction, and coverage of the input space can influence whether training improves or harms useful recognition. [20]

**Deployment costs differ by stage:** adversarial training adds work during model development and retraining; inference-time filtering or anomaly detection adds work during operation. These costs should be evaluated against the sensing system’s latency and energy constraints. A health-monitoring receiver and an interactive gesture interface may prefer different allocations even when they use related CSI classifiers.

### Localization integrity: FooLoc, physical interference, and AP spoofing

**FooLoc attacks an authorized estimate:** a malicious client manipulates transmitted training signals so the AP’s localization model receives falsified uplink CSI. Targeted attacks seek an attacker-chosen position; untargeted attacks seek a sufficiently incorrect position. The paper connects these capabilities to geofencing bypass and evasion of Sybil-attacker detection. [4]

**Its construction respects antenna constraints:** FooLoc uses obtainable downlink CSI as a substitute for unknown uplink CSI at the client’s location, then optimizes multiplicative weights applied to training symbols. The subcarrier weights repeat across the AP’s receiving antennas. Applying corresponding weights to the payload allows message demodulation to remain intact while the localization model interprets the manipulated CSI. [4]

**Targeted control is the harder result:** offline experiments with commercial APs reported 73.0% targeted and 93.4% untargeted success. Online WARP v3 experiments reported mean success of 71.6% targeted and 99.5% untargeted, with perturbation-to-signal ratios around −18 dB. The larger untargeted success rate reflects the broader set of incorrect outcomes that satisfy that objective. [4]

| FooLoc evaluation | Targeted success | Untargeted success | Perturbation-to-signal ratio |
|---|---:|---:|---:|
| Offline, commercial AP observations | 73.0% | 93.4% | About −18 dB |
| Online, WARP v3 | 71.6% | 99.5% | About −18 dB |

**Privacy obfuscation is not automatically protection:** transmitter pre-distortion and BeamDancer seek to prevent an unauthorized receiver from learning location. FooLoc instead makes a legitimate receiver learn a false location from a malicious client’s transmission. The control point and security objective have changed. Those privacy defenses therefore supply relevant physical insights, but they should not be presented as established countermeasures against FooLoc.

**Robust processing has a closer target:** the pre-cutoff role-based synthesis describes Phy-Adv as a physically realizable interference attack against deep Wi-Fi fingerprinting models, with physical attenuation modeling and differentiable simulation. It reports that Robust Mean-Based Normalization improves model robustness. This supports a localization-specific preprocessing defense path, while retaining the distinction between Phy-Adv’s evaluated pairing and a candidate application to FooLoc. [17]

**AP spoofing corrupts a different input:** RSS fingerprint localization can be misled by fake AP identities and associated power values rather than altered CSI training symbols. The November 2024 UJIIndoorLoc study considered 1–10 spoofed APs per request. One scenario inserted random RSS values from −70 dBm to −30 dBm; another copied values from a fingerprint in a different building. [5]

**SFKNN checks spatial plausibility:** it estimates AP coverage areas from the radio map and identifies requests whose observed APs lack a plausible common coverage region. Only fingerprints passing that spatial filter proceed to k-nearest-neighbor localization. The defense uses environmental consistency at the server rather than requiring an additional RF emitter. [5]

**Error reduction carries a service cost:** SFKNN reduced mean localization error by 2–5 m in the reported spoofing comparison, especially as the number of spoofed APs increased. In the random-RSS scenario, however, it declined more than 90% of requests when at least three APs were spoofed. Nearby-building spoofing could escape detection because the fabricated AP combination remained spatially plausible. [5]

**The decision depends on failure tolerance:** for access control, rejecting an inconsistent location request may be preferable to accepting an attacker-chosen location. For continuous navigation, extensive rejection can itself be a serious service failure. SFKNN’s strongest practical lesson is therefore to evaluate localization error together with request acceptance, rather than celebrating accuracy among retained requests in isolation.

### Deceptive jamming targets the physical interpretation of echoes

**WLAN sensing also supports radar-like outputs:** a sensing transmitter and receiver can use standardized Wi-Fi waveforms to estimate range and motion. In bistatic sensing, those devices occupy different positions; the receiver interprets propagation paths and their evolution. The 2024 deceptive-jamming work examines how an attacker can inject OFDM signals that generate artificial range–Doppler maps or phantom targets. [21]

**Standardization can simplify deception:** known waveform structures and constrained sensing parameters reduce the attacker’s uncertainty about the signal that the receiver expects. OFDM also allows digitally constructed signal changes to appear as structured target information. This is not merely raising the noise floor: the attacker attempts to supply a convincing alternative physical interpretation. [32]

**The reported effects include displaced targets:** in one simulated case, the true range–Doppler map shifted by approximately 30 m; another case concealed the true target while leaving artificial target structure. The numerical setup included 80 MHz bandwidth and 23 dBm sensing-transmitter power. Separate indoor walking-human validation used two USRP X310s and 30 dBm jammer power. The approximately 30 m value is a simulated range displacement, not an experimentally measured attack distance. [21]

**Arrival timing and path strength decide impact:** the distortion depends on relative time of arrival and line-of-sight strength. The paper reports that effects reverse when the sensing transmitter’s line-of-sight component becomes stronger than the jammer’s. Geometry and synchronization are therefore part of the security condition, not incidental laboratory details. [21]

**The defense direction is JCAS-specific:** the study calls for electronic-counter-countermeasures within joint communication and sensing, or JCAS, design and standardization. Its recommendation should be treated as a design direction rather than a completed named defense with a measured universal success rate. Activity-model adversarial training and RSS radio-map filtering protect different representations and do not automatically validate range–Doppler targets. [21]

**Integrity defense takeaway:** validate the physical measurement process and the downstream inference separately; neither robust classification nor normal communication alone certifies that a sensed event or location is genuine.

## Scenario-specific decisions and practical trade-offs

### Shared-axis choices for the main applications

**The best starting point is scenario-specific:** the following comparison identifies the main security decision for each application, rather than ranking incompatible attack-success and recognition metrics.

| Scenario | Principal demonstrated threats | Closest defense families | Decisive trade-off | Selection condition |
|---|---|---|---|---|
| Gesture recognition | WiADv; WiIntruder gesture case | PhyCloak; MIMOCrypt; robust recognition | Privacy versus authorized interaction | SISO scope, MIMO support, key access |
| Activity recognition | ActListener; IS-WARS; pilot perturbation | Scheduling; SCF; PhaseAnti; SecureSense; CAT | Semantic privacy versus reliable classification | Observer access and interference structure |
| Device-free localization privacy | Passive CSI receivers; active probing | Pre-distortion; AntiSense; BeamDancer | Privacy versus communication/deployment cost | Who controls the transmitter |
| Localization integrity | FooLoc; Phy-Adv; AP spoofing | Signal validation; RMBN; SFKNN | False position versus rejected service | CSI versus RSS positioning pipeline |
| Vital-sign monitoring | WiIntruder; apnea input attacks | Adversarial training; signal validation | Robust monitoring versus missed events | Digital access versus RF perturbation |
| IoT status inference | Packet-metadata analytics | Traffic spoofing; size obfuscation | Privacy versus traffic overhead/delay | Whether leakage is metadata-driven |

### Gesture recognition: distinguish secrecy from trustworthy commands

**Gesture privacy has direct protection examples:** PhyCloak demonstrates manipulation of illegitimate gesture observations in a SISO setting, while MIMOCrypt explicitly evaluates privacy-sensitive gesture recognition with an SDR prototype. These are relevant when an outsider should not infer a gesture but an authorized user should retain sensing capability. [10][25]

**Gesture integrity is a different requirement:** WiADv’s objective is to force a recognizer toward a selected gesture label. In a control interface, a false label could represent an unwanted command even though gesture privacy is irrelevant to that event. A suitable integrity evaluation therefore measures false commands or targeted misclassification under physical perturbation, rather than only measuring how difficult it is for an outsider to recognize private gestures. [18]

**Domain robustness should not be confused:** Wi-AM, published in February 2024, uses adversarial domain learning and meta-learning for cross-domain gesture recognition. It reports 82.13% average unseen-domain accuracy with one sample and 86.76% with three samples on Widar3.0. Those results concern adaptation across users, environments, positions, and orientations; the word “adversarial” in its training design does not make those percentages a malicious-attack defense result. [33]

**The practical gesture judgment is conditional:** choose a selective privacy mechanism when unauthorized interpretation is the main risk, and physically grounded robustness checks when false commands are the main risk. Where both matter, the two mechanisms must coexist without erasing the authorized gesture features. A SISO relay demonstration should be reassessed when the deployment instead relies on multi-antenna spatial features.

### Activity recognition: combine privacy with safety-aware resilience

**Activity systems face attacks from both directions:** ActListener uses activity features successfully to invade privacy, while IS-WARS and pilot perturbation exploit those features to produce incorrect legitimate outputs. Reducing all activity information would help against surveillance but would also undermine fall detection or health monitoring. The required security property is selective access plus trustworthy inference, rather than uniformly poor recognition.

**Scheduling offers a useful selective example:** its authorized and unauthorized accuracy comparison directly addresses continued legitimate sensing. By contrast, a model-side defense such as CAT seeks to improve the legitimate classifier’s robustness but does not remove the ambient signal available to an eavesdropper. These approaches are complementary because they operate before and after different parts of the observation pipeline. [24][20]

**Safety changes the acceptance criterion:** overall classification accuracy can obscure rare but important errors, such as a fall classified as ordinary movement. For safety-sensitive deployments, the analyst’s decision should include event-specific missed detections, false alarms, and the behavior when signal quality becomes suspicious. This follows from the semantic consequence identified by IS-WARS, rather than from assuming that a single aggregate accuracy describes clinical or security reliability. [31]

**The activity judgment favors layered protection:** preserve authorized observation, monitor interference and sample loss, and use training matched to credible perturbations. PhaseAnti is attractive where co-channel interference is the demonstrated problem; CAT or SecureSense addresses model-input robustness. The conclusion changes when the attacker can alter the transmitter or waveform in ways outside the model’s training distribution.

### Localization: separate three different meanings of location

**The target may be a device:** external anchor localization estimates where interior Wi-Fi equipment sits, and client-positioning systems estimate the transmitter’s location. Other methods localize a person who carries no device. Radar-like WLAN sensing estimates propagation-derived target range and motion. These tasks share a word—localization—but expose different observables and attacker control points. [7]

**Privacy and integrity can demand opposites:** a resident may want an unauthorized CSI classifier to be inaccurate, while a navigation service wants its authorized estimator to remain accurate under spoofing. Randomization that successfully conceals location is not automatically appropriate inside a trusted location-estimation chain. This is why BeamDancer and SFKNN belong in the same survey but should not be treated as substitutes.

**The clearest operational fork is control:** legitimate-transmitter control favors pre-distortion or beamforming randomization against passive observers. Attacker-controlled probing motivates environment-side protection such as AntiSense or reactive disturbance. AP-identity spoofing in an RSS positioning service instead calls for validation against a radio map, while malicious-client CSI manipulation calls for physical and model consistency checks. [1][5]

**The localization judgment includes availability:** SFKNN’s 2–5 m error reduction and substantial request rejection describe a security–service trade-off, whereas BeamDancer’s packet-delivery retention describes communication utility. Neither measure alone expresses authorized positioning quality. A defensible decision therefore names which output must remain useful and whether rejecting an estimate is acceptable.

### Deployment assumptions can outweigh headline performance

**Different control points favor different methods:** the comparison below translates the mechanisms into deployment choices. These are engineering judgments from the stated designs, not measured results for a newly combined system.

| Available deployment control | Suitable starting methods | Protected step | Main operational burden |
|---|---|---|---|
| Legitimate AP/transmitter firmware | Cover signals; pre-distortion; BeamDancer | Outgoing observations | Waveform and communication compatibility |
| Spatial transmitter infrastructure | Scheduled spatial sensing | Transmitter identity/CSI organization | Placement, scheduling, authorized synchronization |
| Environmental hardware | PhyCloak; AntiSense; IRShield | Propagation channel | Hardware, placement, timing |
| Sensing receiver/model | SCF; PhaseAnti; SecureSense; CAT | Measurements and inference | Processing, training, adaptation |
| Localization server/radio map | SFKNN | Fingerprint acceptance | Map quality and rejection policy |
| Distributed learning platform | Federated sensing with secret sharing | Training-data handling | Update protection and coordination |

**Extra hardware buys a different boundary:** an environmental defense can affect attacker-generated signals that bypass a legitimate AP’s settings. Its cost is deployment and timing complexity. Native beamforming avoids a separate obfuscator but depends on control of the transmitting device. BeamDancer explicitly motivates its design through this contrast with secondary transceivers and environmental components. [6]

**Detection adds its own failure modes:** filtering and validation can reject legitimate observations as well as attacks. Static thresholds can also become inappropriate after furniture moves, devices relocate, or interference changes. The practical implication is to treat rejection, processing delay, and recovery behavior as part of sensing utility, not merely as ancillary implementation statistics.

**Layering requires compatibility, not accumulation:** combining every available defense is not inherently beneficial. A privacy obfuscator may intentionally change features that an integrity detector regards as suspicious, and a robust classifier may learn to undo patterns intended to frustrate eavesdroppers. A combined deployment needs an explicit authorized interpretation path and a consistent account of which changes are expected.

### Sensing-data privacy and adjacent machine-learning threats

**Federated learning protects collected data:** Lian and colleagues’ system trains locally for IoT health monitoring, then combines secret sharing, model sparsification, and adaptive-residual top-k updates. The stated purpose is to improve privacy and communication efficiency while maintaining sensing accuracy. Its first online publication was October 2024, with a February 2025 journal issue. [30]

**That protection begins after acquisition:** keeping raw measurements local reduces exposure through centralized data collection, but it does not alter the radio field available to an outside listener. Conversely, a physical obfuscator does not automatically secure stored CSI, model updates, or authorized users’ access. These are separate stages of the same system and merit separate controls.

**Membership inference asks another question:** the pre-cutoff wireless-classifier membership-inference work determines whether a signal belonged to a training dataset, using surrogate classification and inference models. Its demonstrated context is RF fingerprinting and physical-layer authentication. That privacy question differs from ActListener reconstructing current activity semantics or an external receiver estimating a person’s position. [34]

**Poisoning concerns the training pipeline:** the 2024 wireless federated-learning survey distinguishes data poisoning from model poisoning and identifies collection, training, and aggregation attack phases. A backdoor seeks targeted behavior on malicious inputs while retaining normal behavior on benign inputs. These are relevant model-governance risks, but generic wireless-learning results are not presented here as additional demonstrated Wi-Fi gesture, activity, or localization attacks. [35]

**Scenario decision takeaway:** choose protection by the information being exposed, the measurement being falsified, and the component under defender control; application names alone are too coarse.

## Public availability through 28 February 2025

**Public disclosure determines temporal eligibility:** conference papers, journal publications, public preprints, and technical reports qualify when they were public by the cutoff. “Publicly available” here describes disclosure of the technology, not a claim that every implementation was a consumer product or a downloadable software package.

| Work or group | Public record used | Date | Eligibility significance |
|---|---|---|---|
| PhyCloak | NSDI ’16 paper | 16–18 March 2016 | Early signal-obfuscation prototype |
| Adversarial WiFi Sensing / Et Tu Alexa? | Preprint; NDSS work | 2018; 2020 | Passive reconnaissance and AP defense |
| CSI-MURDER | Technical report | 14 August 2020 | Passive/active localization protection |
| CSI pre-distortion | Public manuscript | 20 March 2021 | Transmitter-side localization privacy |
| ActListener | ICDCS; journal extension | July 2022; 28 May 2024 | Activity and identity-related inference |
| WiIntruder | First arXiv submission | 24 April 2024 | Pre-cutoff physical perturbation attack |
| CAT | Conference; Xplore record | 8–10 May; 10 July 2024 | Pre-cutoff adversarial-training defense |
| MIMOCrypt | Conference; Xplore record | 19–23 May; 5 September 2024 | Pre-cutoff MIMO sensing privacy |

The dated records are available in the PhyCloak paper [10], CSI-MURDER report [14], pre-distortion manuscript [23], ActListener extension [12], WiIntruder submission record [36], CAT record [20], and MIMOCrypt record [25].

**The remaining principal entries also precede cutoff:** PhaseAnti dates to 2020; IS-WARS was published online on 8 September 2021, with its later issue version in 2022; SecureSense was published online on 6 December 2022; the apnea adversarial-example poster and FooLoc date to 2023. Scheduled spatial sensing appeared at PerCom in March 2023. [28][31][29][19][4][24]

**Late-2024 entries remain eligible:** the pilot-perturbation work and BeamDancer are identified as 2024 technologies; AP spoofing and SFKNN were published on 27 November 2024. The traffic-analysis dissertation was released in May 2024. WiADv and IRShield are 2022 works, while Phy-Adv and RMBN are described as 2024 work in the December 2024 role-based synthesis. [2][6][5][8][17]

**The February boundary includes online-first work:** Lian and colleagues’ federated system was published online on 8 October 2024 and appeared in the 1 February 2025 journal issue. It therefore meets either date basis. Standards discussion is likewise confined to pre-cutoff material: NIST’s 2023 account describes the first IEEE 802.11bf draft and its below-7-GHz sensing procedures, rather than relying on later standardization outcomes. [30][37]

**Reading the reported numbers:** the evidence combines prototypes, controlled experiments, dataset evaluations, and simulations, with different populations and threat models. Attack success, recognition accuracy, accuracy degradation, recall, false positives, meter-scale error, request rejection, and baseline-relative packet delivery measure different outcomes and do not support one universal ranking. CAT and PhaseAnti gains retain their authors’ percentage wording; the FGSM attacked accuracy is the explicitly labeled estimate from 0.85 minus approximately 0.45. Pilot perturbation and BeamDancer retain year-level 2024 dating. Scenario codes and candidate mappings identify the scope of demonstrated results without assuming automatic transfer between applications.

## Overall judgment

**Secure sensing requires two boundaries:** control who can interpret the physical signal, and control whether authorized inference can trust its measurements. Before March 2025, public research had already demonstrated practical attacks against both boundaries and several useful, scenario-specific defenses.

**The strongest practical conclusion is layered:** use signal-side protection for unauthorized inference, measurement and spatial validation for physical deception, and robust learning for classifier sensitivity. Preserve authorized sensing explicitly, and judge protection alongside communication quality, sensing utility, and service rejection—not by a security percentage in isolation.

## References

[1] <https://re.public.polimi.it/retrieve/f3be4760-1e33-4c6c-9c14-b151534f110a/2022_ieee_network.pdf> Physical-layer privacy analysis; CSI attack classification; CSI obfuscation formulation; Eight-position experiments; Class-specific localization behavior; Tran…
[2] <https://eceweb1.rutgers.edu/~daisylab/papers/Practical%20Adversarial%20Attack%20on%20WiFi%20Sensing%20Through%20Unnoticeable%20Communication%20Packet%20Perturbation.pdf> Communication-preserving perturbation attack; Pilot-perturbation construction; Pilot-attack evaluation; Environment and hardware sensitivity; Pilot perturbation
[3] <https://doi.org/10.1109/icdcs54860.2022.00080> ActListener mechanism; ActListener experimental results; ActListener signal conversion
[4] <https://arxiv.org/html/2301.03760v1> FooLoc threat and objectives; FooLoc physical construction; FooLoc experimental results; FooLoc
[5] <https://doi.org/10.3390/s24237624> AP-spoofing evaluation; SFKNN mechanism; SFKNN results and rejection behavior; SFKNN spatial validation; SFKNN publication
[6] <https://re.public.polimi.it/retrieve/f26694e7-d2c5-4b55-bf72-b4756d5a46f8/Cominelli2024_BeamDancer_TWC_AAM.pdf> BeamDancer evaluation; BeamDancer communication preservation; Deployment-cost comparison; BeamDancer
[7] <https://gzhou.pages.wm.edu/wp-content/blogs.dir/5736/files/sites/13/2017/12/WiFiSenseSurvey_CSUR19.pdf> CSI sensing foundations; Detection, recognition, and estimation; Localization distinctions
[8] <https://stars.library.ucf.edu/etd2023/101/> Wi-Fi metadata privacy; IoT Wi-Fi traffic inference; Traffic spoofing and size obfuscation; Dissertation release
[9] <https://doi.org/10.1109/ojcoms.2021.3054066> Wireless-sensing threat objectives
[10] <https://www.usenix.org/system/files/conference/nsdi16/nsdi16-paper-qiao.pdf> PhyCloak threat model; PhyCloak prototype; Jamming versus obfuscation; PhyCloak gesture protection
[11] <https://arxiv.org/html/1810.10109v1> Passive reconnaissance experiments; Anchor-localization method and result; Presence-detection performance; Monitoring configuration and scope; Three reconnaiss…
[12] <https://dl.acm.org/doi/full/10.1109/TNET.2024.3403839> extension; ActListener extension
[13] <https://doi.org/10.1109/medcomnet52149.2021.9501240> Multi-receiver localization; Multi-receiver obfuscation result
[14] <https://ans.unibs.it/assets/documents/ORCA_CSI-MURDER_Report_v1.1_compressed.pdf>
[15] <https://www.cs.fsu.edu/~xzhang/files/IS-WARS_Intelligent_and_Stealthy_Adversarial_Attack_to_Wi-Fi-Based_Human_Activity_Recognition_Systems.pdf> IS-WARS mechanism; IS-WARS feasibility analysis; Denoising comparison; Cyclostationarity protection boundary
[16] <https://doi.org/10.1109/tdsc.2023.3261328> Physical-world behavior attack
[17] <https://arxiv.org/html/2412.03064v1> IRShield mechanism and reported outcome; WiADv technical summary; Phy-Adv and RMBN; Pre-cutoff synthesis
[18] <https://arxiv.org/html/2404.15587v1> WiIntruder design; WiIntruder application results; WiIntruder surrogate switching; WiADv targeted objective
[19] <https://www.eng.auburn.edu/~szm0001/papers/infocom23_poster.pdf> Wi-Fi apnea adversarial examples; Attack comparison; MIM adversarial training; Apnea attacks
[20] <https://doi.org/10.1109/cscwd61410.2024.10580434> CAT mechanism and comparison; CAT training comparison; CAT robustness
[21] <https://arxiv.org/html/2401.01101> Deceptive WLAN sensing; Simulation and experimental validation; Deceptive-jamming conditions; JCAS defense recommendation
[22] <https://sandlab.cs.uchicago.edu/adversarialwifi/> AP-based defense
[23] <https://ans.unibs.it/assets/documents/COMNET-CSI_CR.pdf> Pre-distortion comparison and parameters
[24] <https://ebulutvcu.github.io/Percom2023_AntiEve.pdf> Independent eavesdropper model; Scheduled spatial sensing mechanism; Spatial-scheduling experimental setup; Authorized and unauthorized results; Periodic and n…
[25] <https://doi.org/10.1109/sp54263.2024.00025> MIMOCrypt design; MIMOCrypt objectives; MIMOCrypt gesture application
[26] <https://re.public.polimi.it/bitstream/11311/1264858/6/Cominelli2022_AntiSense_ComCom_AAM.pdf> AntiSense design and threat model; Reflection timing requirements
[27] <https://export.arxiv.org/pdf/2211.12087v1.pdf>
[28] <https://happyisac.github.io/PersonHomePage/paper/INFOCOM_2020_HuangJinyang.pdf> PhaseAnti mechanism and results; PhaseAnti
[29] <https://doi.org/10.1109/tmc.2022.3226742> SecureSense
[30] <https://doi.org/10.1109/jiot.2024.3476149> Privacy-enhanced federated sensing; Federated-system dates
[31] <https://doi.org/10.1109/tdsc.2021.3110480> IS-WARS application consequences; Activity-sensing safety concern; IS-WARS
[32] <https://doi.org/10.1109/radarconf2458775.2024.10549000> Standardized-waveform attack surface
[33] <https://doi.org/10.3390/s24051354> Wi-AM cross-domain recognition
[34] <https://arxiv.org/html/2006.14576> Wireless membership inference
[35] <https://doi.org/10.1109/comst.2024.3361451> Wireless federated-learning backdoors
[36] <https://arxiv.org/abs/2404.15587>
[37] <https://www.nist.gov/publications/ieee-80211bf-enabling-widespread-adoption-wi-fi-sensing> NIST draft description
[38] <https://www.preprints.org/manuscript/202601.0598>
[39] <https://ieeexplore.ieee.org/document/10229055?arnumber=10229055>
[40] <https://dl.acm.org/doi/10.1145/3770653>
[41] <https://waveyhq.dev/posts/ieee-80211bf-privacy-gap/>
[42] <https://re.public.polimi.it/retrieve/f26694e7-d2c5-4b55-bf72-b4756d5a46f8/Cominelli2024_BeamDancer_TWC_AAM.pdf>
[43] <https://ieeexplore.ieee.org/document/10229055>
[44] <https://par.nsf.gov/servlets/purl/10683665>
[45] <https://yangzhice.com/docforweb/WiShield/WiShield_ACSAC.pdf>
[46] <https://cse.buffalo.edu/tech-reports/2026-37.pdf>
[47] <https://doi.org/10.1109/dyspan64764.2025.11115902>
[48] <https://ebulutvcu.github.io/Percom2023_AntiEve.pdf>
[49] <https://www.cisa.gov/sites/default/files/publications/A_Guide_to_Securing_Networks_for_Wi-Fi.pdf?utm_source=chatgpt.com>
[50] <https://doi.org/10.1145/2939918.2939935>
[51] <https://link.springer.com/article/10.1007/s10462-025-11147-4>
[52] <https://www2.compute.dtu.dk/~xefa/files/conf/2013_nordsec_rap.pdf>
[53] <https://arxiv.org/pdf/2506.10718>
[54] <https://www.nsa.gov/portals/75/documents/resources/everyone/csfc/capability-packages/WIDS-WIPS%20Annex%20v1_0.pdf?ver=u0qF4d82XbjNg8-dNuwUuA%3D%3D>
[55] <https://doi.org/10.1109/access.2023.3293404>
[56] <https://doi.org/10.1145/1062689.1062697>
[57] <https://dl.acm.org/doi/pdf/10.1145/1824766.1824772>
[58] <https://doi.org/10.1109/mnet.2006.1637931>
[59] <https://arxiv.org/html/2501.06798>
[60] <https://doi.org/10.1109/lcn.2009.5355149>
[61] <https://dl.acm.org/doi/abs/10.1109/TNET.2022.3147721?download=true>
[62] <https://www.sciencedaily.com/releases/2008/04/080414145659.htm>
[63] <https://doi.org/10.1145/3636534.3690669>
[64] <https://doi.org/10.1002/wcm.2527>
[65] <https://security.cms.gov/policy-guidance/access-control-ac>
[66] <https://doi.org/10.1109/mcom.001.2200465>
[67] <https://www.nsa.gov/Portals/75/documents/resources/everyone/csfc/capability-packages/(U)%20WIDS-WIPS%20Annex%20v1.0.pdf?ver=nzUa0wOiqp_nMn87c4w6hg%3D%3D>
[68] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7122347/>
[69] <https://nvlpubs.nist.gov/nistpubs/legacy/sp/nistspecialpublication800-94.pdf>
[70] <https://www.mdpi.com/1424-8220/21/15/5122>
[71] <https://www.mdpi.com/1424-8220/24/23/7624>
[72] <https://doi.org/10.52545/3-10>
[73] <https://doi.org/10.1109/infcom.2013.6567061>
[74] <https://7signal.com/blog/wif-fi-jamming-what-you-need-to-know>
[75] <https://dipot.ulb.ac.be/dspace/bitstream/2013/386864/3/OFDM_based_JCAS_under_Attack.pdf>
[76] <https://doi.org/10.48550/arxiv.1208.0412>
[77] <https://community.cisco.com/t5/cisco-catalyst-center/ap-impersonation-on-dna-center-wireless-assurance/td-p/4829761>
[78] <https://scholarcommons.sc.edu/cgi/viewcontent.cgi?article=1018&context=csce_facpub>
[79] <https://www.ndss-symposium.org/wp-content/uploads/2025-440-paper.pdf>
[80] <http://staff.ustc.edu.cn/~xiangyangli/paper/Conf/attack-info13.pdf>
[81] <https://arxiv.org/html/2501.06798v1>
[82] <https://doi.org/10.1109/icsns.2015.7292430>
[83] <https://arxiv.org/html/1208.0412v2>
[84] <https://www.vectra.ai/topics/spoofing-attack>
[85] <https://www.encryptionconsulting.com/active-and-passive-attacks/>
[86] <https://csrc.nist.rip/library/NIST%20SP%20800-048r1.pdf>
[87] <https://www.redalyc.org/journal/643/64358093016/html/>
[88] <https://seon.io/resources/dictionary/jamming-attacks/>
[89] <https://publications.sto.nato.int/publications/STO%20Meeting%20Proceedings/STO-MP-IST-210/MP-IST-210-1B.01.pdf>
[90] <https://link.springer.com/article/10.1007/s11276-025-03942-2>
[91] <https://www.sciencedirect.com/topics/computer-science/replay-protection>
[92] <https://www.cyber.gc.ca/en/guidance/wi-fi-security-itsp80002>
[93] <https://arxiv.org/html/2506.23296v1>
[94] <https://ceur-ws.org/Vol-3731/paper08.pdf>
[95] <https://pravin-hub-rgb.github.io/BCA/resources/sem6/ns_cl/unit1/index.html>
[96] <https://www.afcea.org/signal-media/cyber-edge/identifying-shared-vulnerabilities-and-mitigation-strategies-cloud-wireless>
[97] <https://security.stackexchange.com/questions/248357/why-cant-we-perform-a-replay-attack-on-wifi-networks>
[98] <https://www.ijert.org/research/a-provenance-mechanism-to-identify-malicious-and-packet-drop-attacks-in-wireless-sensor-networks-IJERTCONV4IS11026.pdf>
[99] <https://www.eecs.umich.edu/courses/eecs589/papers/tinysec.pdf>
[100] <https://www.mdpi.com/1424-8220/23/23/9606>
[101] <https://ietresearch.onlinelibrary.wiley.com/doi/abs/10.1049/el.2013.2759>
[102] <https://doi.org/10.3929/ethz-a-006821886>
[103] <https://www.cs.ox.ac.uk/files/6493/rasmussen08wlan.pdf>
[104] <https://re.public.polimi.it/bitstream/11311/1264858/6/Cominelli2022_AntiSense_ComCom_AAM.pdf>
[105] <https://iris.unibs.it/retrieve/ddc633e4-675e-4e2e-e053-3705fe0a4c80/main.pdf>
[106] <https://lorenzoghiro.com/papers/ghiro2023wifi.pdf>
[107] <https://eceweb1.rutgers.edu/~daisylab/papers/Detecting%20and%20Localizing%20Wireless%20Spoofing%20Attacks.pdf>
[108] <https://cs.ou.edu/~shangqing/res/21SecureComm/21hll-securecomm.pdf>
[109] <https://arxiv.org/pdf/2006.03695.pdf>
[110] <https://research.engr.oregonstate.edu/hamdaoui/sites/research.engr.oregonstate.edu.hamdaoui/files/ieee_802_11gn_csi_datasets_v1.pdf>
[111] <http://www.poepper.net/papers/tippenhauer08attacks.pdf>
[112] <https://docs.fortinet.com/document/fortiap/8.0.1/fortiwifi-and-fortiap-configuration-guide/961129/wireless-intrusion-detection-system>
[113] <https://doi.org/10.1155/2021/8817569>
[114] <https://doi.org/10.1145/1555816.1555820>
[115] <https://www.ituonline.com/blogs/common-wi-fi-attacks/>
[116] <https://link.springer.com/article/10.1186/1687-1499-2013-208>
[117] <https://www.diva-portal.org/smash/get/diva2:1719628/FULLTEXT02>
[118] <https://dl.acm.org/doi/10.1109/TWC.2021.3129188>
[119] <https://arxiv.org/html/2503.08008v1>
[120] <https://www.ekahau.com/blog/essential-practices-for-secure-wi-fi-networks/>
[121] <https://stars.library.ucf.edu/etd2023/101/>
[122] <https://dl.acm.org/doi/pdf/10.1145/2590296.2590333>
[123] <https://scholarcommons.scu.edu/cgi/viewcontent.cgi?article=1121&context=elec_senior>
[124] <https://doi.org/10.48550/arxiv.2310.05431>
[125] <https://ieeexplore.ieee.org/ielx7/6287639/8948470/09082628.pdf>
[126] <https://arxiv.org/html/1805.08017v1>
[127] <https://ans.unibs.it/assets/documents/ORCA_CSI-MURDER_Report_v1.1_compressed.pdf>
[128] <https://bastille.net/wids-first-line-defense-wireless-attacks/>
[129] <https://tns.thss.tsinghua.edu.cn/wst/docs/sanitization/>
[130] <https://beechat.network/2025/07/29/hopsync-a-stateless-frequency-hopping-revolution-in-military-mesh-communications/>
[131] <https://www.ndss-symposium.org/wp-content/uploads/2020/02/23047.pdf>
[132] <https://hal.science/hal-03950904/document>
[133] <https://arxiv.org/html/2512.22143v1>
[134] <https://www.cdebyte.com/news/1144>
[135] <https://doi.org/10.1016/j.comnet.2025.111208>
[136] <https://doi.org/10.36227/techrxiv.170775475.59127516/v1>
[137] <https://sensingauthorization.com/>
[138] <https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-226.ipd.pdf>
[139] <https://www.sciopen.com/article/10.32604/cmc.2025.073519>
[140] <https://arxiv.org/html/2510.10316v1>
[141] <https://doi.org/10.17760/d20486909>
[142] <https://doi.org/10.1016/j.cose.2025.104594>
[143] <https://re.public.polimi.it/retrieve/c48cc0b2-59d6-4bb6-8c6d-4b30c44e73bf/Cominelli2022_AntiSense_ComCom_AAM.pdf>
[144] <https://www.cs.yale.edu/homes/ramki/sigcomm07.pdf>
[145] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12845974/>
[146] <https://doi.org/10.1007/978-3-319-11379-1_18>
[147] <https://www.dot.gov.in/static/uploads/2026/05/f7816fc9d380529182b62925ef38b96b.pdf>
