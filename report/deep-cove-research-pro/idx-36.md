# Global Quantum Technology Standardization: Status at 31 December 2022

**Quantum standardization was active but uneven.** By **31 December 2022**, ETSI and ITU-T had substantial published portfolios for quantum key distribution (QKD), including application interfaces, network architecture, deployment, management and security. ISO/IEC and IEEE were developing a broader foundation for quantum computing—terminology, architecture, simulation, algorithms and benchmarking—alongside quantum-security work. The Internet Research Task Force’s Quantum Internet Research Group (IRTF/QIRG) was developing research guidance, not Internet standards. QKD was the most mature shared application area; general-purpose quantum networking remained substantially more experimental. [1][2]

| Organization | Responsible bodies | Main technology areas | Position by end-2022 | Practical judgment |
|---|---|---|---|---|
| ETSI | QKD Industry Specification Group; CYBER quantum-safe working group | QKD, interfaces, network control, quantum-safe cryptography | Published specifications and reports; continuing security and interoperability drafts | Strong source for deployable QKD interfaces and cryptographic migration guidance |
| ITU-T | Study Groups 13 and 17; adjacent SG11 and SG15; FG-QIT4N | QKD networks, telecommunications architecture, security, quantum random-number generation | Published Recommendations, Supplements and focus-group reports; additional network drafts | Strongest telecommunications-oriented QKD network framework |
| ISO/IEC | JTC 1/WG 14; JTC 1/SC 27/WG 2 and WG 3 | Computing terminology, platforms, simulation, QKD evaluation, quantum-resistant cryptography | Committee drafts, approved work items, preliminary work and security studies | Foundational computing and security-assurance work was developing |
| IEEE | Project working groups and sponsoring standards committees | Computing definitions, algorithms, architecture, simulation, benchmarking, communication and post-quantum security | Eight active projects reported in October 2022; separate P3120.1 authorization in December | Broad engineering agenda, principally at project-development stage |
| IRTF/QIRG | Quantum Internet Research Group | Quantum-network architecture, applications, distributed computing and sensing | Approved charter and two principal Informational Internet-Draft workstreams | Research foundation for a future Quantum Internet, not an adopted protocol suite |

**The comparison follows document maturity.** The sections below identify each organization’s responsible bodies, explain their technical focus, and list document numbers, titles, types and historical status. The final comparison separates QKD from broader quantum networking, quantum computing and post-quantum cryptography, then explains where the organizations complemented or overlapped one another. The institutional map is supported by the contemporary ITU-T assessment, the November 2022 ISO/IEC working-group overview and IEEE’s October 2022 project presentation. [1][3][4]

## Scope and interpretation

**This is a global historical snapshot.** The report concerns internationally oriented quantum-technology standardization through **2022-12-31**, rather than national standards programmes or developments after that date. ETSI is European-based but develops globally applicable information and communications technology specifications; ITU-T, ISO/IEC and IEEE also draw on international participation. Contemporary cross-organization discussions explicitly connected these bodies with IRTF and other standards communities. [5][6]

**Three related technologies require separation.** QKD uses quantum communication to establish shared secret keys. Post-quantum cryptography (PQC) uses cryptographic algorithms intended to resist quantum-computer attacks, generally without requiring a quantum communications channel. A broader Quantum Internet would support the exchange of quantum states and distributed entanglement for applications extending beyond key distribution. These distinctions explain why a quantum-safe migration report, a QKD application interface and a quantum-network architecture draft address different engineering problems. [7][8][2]

| Technology | Principal function | Representative end-2022 work | Important distinction |
|---|---|---|---|
| QKD | Establish shared secret keys using quantum signals and classical processing | ETSI QKD interfaces; ITU-T Y.3800-series | Key distribution is not a complete encryption or network-security system |
| Post-quantum cryptography | Protect cryptographic functions against quantum-computer attacks | ETSI QSC; ISO/IEC SC 27/WG 2; IEEE P1943 and P3172 | Quantum-resistant algorithms need not use quantum hardware |
| General quantum networking | Distribute quantum states or entanglement for networked applications | QIRG architecture and application drafts; FG-QIT4N network reports | Goes beyond QKD and requires different services and resource management |

**Document type and status are separate.** An issued technical report is a completed publication, but it is not necessarily a normative interoperability specification. Conversely, a document whose proposed title begins “Standard for…” may still be an authorized development project. ETSI’s Group Specifications and Technical Specifications, ITU-T Recommendations, ISO/IEC work-item stages, IEEE project authorizations and IRTF Internet-Drafts therefore retain their native labels throughout this report. [9][10]

**Publication does not establish universal maturity.** ITU-T’s November 2021 assessment identified QKD and quantum random-number generation as exceptions to the generally early readiness of quantum information technologies. Nevertheless, its QKD-specific report still identified interoperability, implementation security and certification as important challenges. The appropriate conclusion is relative: QKD had a more developed standardization portfolio than general quantum networking, not that every QKD protocol, product or deployment was standardized or certified. [1][8]

## ETSI

### Responsible bodies

**Two distinct bodies led ETSI’s work.** The **Industry Specification Group on Quantum Key Distribution—ETSI ISG QKD**—was responsible for specifications describing quantum cryptography for information and communications technology networks. Its terms of reference focused on specifying QKD systems and their operating environment, with cooperation both inside and outside ETSI. The responsible designation is the ISG itself; its founding terms of reference did not establish a fixed subordinate working-group structure. [11]

**Quantum-safe cryptography had a separate home.** The **Technical Committee Cyber Security, Working Group for Quantum-Safe Cryptography—ETSI TC CYBER WG QSC**—assessed quantum-safe cryptographic primitives, protocols and deployment requirements. This working group succeeded the earlier **ISG QSC**, which produced several foundational Group Reports. Keeping the historical producer and the end-2022 responsible body separate avoids attributing older ISG publications to a committee structure that subsequently changed. [9][5]

### Main areas of focus

**ISG QKD addressed implementation and integration.** Its portfolio covered use cases, terminology, components and internal interfaces, optical characterization, security proofs, module security, deployment parameters and application access to keys. Network-level work extended this foundation to software-defined networking, orchestration, network architecture and interoperable key-management systems. The progression was from describing a QKD device to making that device usable within a multi-component operational network. [8]

**QSC addressed the quantum-computing threat.** Its work included key exchange, signatures, public-key encryption, key encapsulation mechanisms, identity-based encryption, virtual private networks and cryptographic migration. A key encapsulation mechanism, or KEM, is a cryptographic mechanism used to establish a shared secret suitable for subsequent symmetric-key protection. ETSI’s QSC work was therefore primarily about securing existing information systems against quantum attacks, rather than standardizing quantum processors. [12]

### Published documents

**The QKD foundation was already substantial.** The following tables identify the published editions relevant to the cutoff. For readability, the shared title prefix **“Quantum Key Distribution (QKD);”** applies to the QKD titles below. The versions and publication months are recorded in the 2022 BSI/UKNC proposal, with individual ETSI records supplying additional historical confirmation. [13]

| Identifier and edition | Document title after common prefix | Type | Status by cutoff |
|---|---|---|---|
| ETSI GS QKD 002 V1.1.1 | Use Cases | Group Specification | Published, 2010-06 |
| ETSI GR QKD 003 V2.1.1 | Components and Internal Interfaces | Group Report | Published, 2018-03 |
| ETSI GS QKD 004 V2.1.1 | Application Interface | Group Specification | Published, 2020-08 |
| ETSI GS QKD 005 V1.1.1 | Security Proofs | Group Specification | Published, 2010-12 |
| ETSI GR QKD 007 V1.1.1 | Vocabulary | Group Report | Published, 2018-12 |
| ETSI GS QKD 008 V1.1.1 | QKD Module Security Specification | Group Specification | Published, 2010-12 |

**Deployment and control became explicit targets.** ETSI’s record dates publication of GS QKD 012 to **28 February 2019** and describes its scope as point-to-point deployment, including device characteristics, communication channels, performance, footprint and link requirements. GS QKD 004 V2.1.1 was published on **25 August 2020**, updating the application interface for evolving network architectures. [14][15]

| Identifier and edition | Document title after common prefix | Type | Status by cutoff |
|---|---|---|---|
| ETSI GS QKD 011 V1.1.1 | Component characterization: characterizing optical components for QKD systems | Group Specification | Published, 2016-05 |
| ETSI GS QKD 012 V1.1.1 | Device and Communication Channel Parameters for QKD Deployment | Group Specification | Published, 2019-02 |
| ETSI GS QKD 014 V1.1.1 | Protocol and data format of REST-based key delivery API | Group Specification | Published, 2019-02 |
| ETSI GS QKD 015 V2.1.1 | Control Interface for Software Defined Networks | Group Specification | Published, 2022-04 |
| ETSI GS QKD 018 V1.1.1 | Orchestration Interface for Software Defined Networks | Group Specification | Published, 2022-04 |

**QKD 018 belongs among published specifications.** The official ETSI document is **GS QKD 018 V1.1.1, April 2022**, produced by ISG QKD. Although the 2022 proposal also repeats it in a draft list, the dated issued specification determines its classification here; it is counted once, as a published Group Specification. Its scope includes QKD-network resource, configuration and performance management, service provisioning, notifications and multi-domain management. [16]

**QSC combined reports with a specification.** The following publications addressed cryptographic assessment and deployment. Their distinctions matter: the Technical Reports describe and analyze approaches, while **TS 103 744** is a Technical Specification for hybrid key exchanges. All editions shown are V1.1.1. [12][7]

| Identifier | Document name | Type | Publication |
|---|---|---|---|
| ETSI GR QSC 001 | Quantum-Safe Cryptography (QSC); Quantum-safe algorithmic framework | Group Report | 2016-07 |
| ETSI TR 103 570 | CYBER; Quantum-Safe Key Exchanges | Technical Report | 2017-10-05 |
| ETSI TR 103 616 | CYBER; Quantum-Safe Signatures | Technical Report | 2021-09-20 |
| ETSI TR 103 617 | CYBER; Quantum-Safe Virtual Private Networks | Technical Report | 2018-09-24 |
| ETSI TR 103 618 | CYBER; Quantum-Safe Identity-Based Encryption | Technical Report | 2019-12-12 |
| ETSI TR 103 619 | CYBER; Migration strategies and recommendations to Quantum Safe schemes | Technical Report | 2020-07-21 |
| ETSI TS 103 744 | CYBER; Quantum-safe Hybrid Key Exchanges | Technical Specification | 2020-12-23 |
| ETSI TR 103 692 | CYBER; State management for stateful authentication mechanisms | Technical Report | 2021-11-08 |
| ETSI TR 103 823 | CYBER; Quantum-Safe Public-Key Encryption and Key Encapsulation | Technical Report | 2021-09-20 |

**Earlier reports supplied supporting context.** The December 2020 OPENQKD review also records the following issued ETSI publications. These extend the catalogue beyond individual algorithms to deployment scenarios, threat assessment, symmetric-key sizing and implementation security. [9]

| Identifier and edition | Document name | Type | Publication |
|---|---|---|---|
| ETSI GR QSC 003 V1.1.1 | Quantum Safe Cryptography; Case Studies and Deployment Scenarios | Group Report | 2017-02 |
| ETSI GR QSC 004 V1.1.1 | Quantum-Safe Cryptography; Quantum-Safe threat assessment | Group Report | 2017-03 |
| ETSI GR QSC 006 V1.1.1 | Quantum-Safe Cryptography (QSC); Limits to Quantum Computing applied to symmetric key sizes | Group Report | 2017-02 |
| ETSI White Paper No. 27 | Implementation Security of Quantum Cryptography: Introduction, challenges, solutions | White Paper | 2018 |

### Documents under development

**Security and interoperability work continued.** The pre-cutoff development portfolio included transmitter characterization, Trojan-horse protection, Common Criteria protection profiles, network architecture, authentication and interoperable key management. The table preserves explicit work-item references where they identify the development stream more precisely than a projected publication number. [8][13]

| Identifier or work item | Document name after QKD prefix | Type | Pre-cutoff development status |
|---|---|---|---|
| GS QKD 005, revision V2.1.1 | Security Proofs | Specification revision | Drafting in 2020; revision recorded in 2021 |
| GR QKD 007, revision | Vocabulary | Report revision | Revision in progress in 2021 |
| DGS/QKD-0010_ISTrojan | Implementation security: protection against Trojan horse attacks in one-way QKD systems | Draft Group Specification | Development recorded in 2021 |
| GS QKD 013 V1.1.2 | Characterisation of Optical Output of QKD transmitter modules | Draft Group Specification | Draft in 2022 inventory |
| DGS/QKD-016-PP, V0.6.2 | Common Criteria Protection Profile Pair of Prepare and Measure Quantum Key Distribution Modules | Working-draft Group Specification | Dated 2021-12 |
| QKD 017; DGR/QKD-017NwkArch | Network architectures | Group Report project; GS label in 2022 inventory | Under development |
| QKD 019; DGR/QKD-019_AUTH | Design of QKD interfaces with Authentication | Group Report project; GS label in 2022 inventory | Under development |
| DGS/QKD-020_InteropKMS | Protocol and data format of REST-based Interoperable Key Management System API | Draft Group Specification | Under development in 2021 |

**The dated QKD 016 draft is specific.** The December 2021 working document carries reference **DGS/QKD-016-PP** and version **V0.6.2**, with the prepare-and-measure module-pair title shown above. The shorter “QKD Common Criteria Protection Profile for QKD” title and V1.1.1 designation in the 2022 inventory describe the projected deliverable, not a reason to treat the working draft as a published specification. [17]

**QKD 020 was already a work item.** Its inclusion rests on the dated 2021 ITU-T inventory, which explicitly lists **DGS/QKD-020_InteropKMS** as under development. Likewise, QKD 010 has pre-cutoff open-area drafts, including a V0.4.1 file dated June 2021. These are stronger historical anchors than an undated description of a project as “current.” [8][18]

### What ETSI’s portfolio implies

**Application access and orchestration differ.** GS QKD 004 addresses how a security application obtains keys from a QKD system. GS QKD 014 specifies a representational state transfer, or REST-based, key-delivery application programming interface (API). Both concern the application’s access to key material, rather than specifying the complete optical operation of a QKD link. This distinction permits useful application integration without first requiring every vendor’s quantum transmitter and receiver to be interchangeable. [15][9]

**Control and orchestration address another boundary.** GS QKD 015 concerns software-defined networking (SDN) control interfaces. GS QKD 018 moves upward to the relationship between a QKD-network SDN controller and an orchestrator. Its vendor-independent YANG information model supports collection of topology and inventory, requests for candidate service paths, path selection and service deployment. The specification does not standardize the orchestrator’s interfaces to classical optical-transport controllers. [16]

**Security remained an implementation problem.** Optical component measurements, module security requirements and protection profiles connect mathematical security arguments to imperfect physical devices. A sound QKD protocol model does not by itself establish that a commercial implementation controls side channels or handles calibration safely. That explains why component characterization and evaluation-related drafts remained central even as operational interfaces were published. [9]

**Migration guidance addressed existing infrastructure.** TR 103 617 considered virtual private network protocols including Internet Protocol Security and Internet Key Exchange, Transport Layer Security, Media Access Control Security and Secure Shell. It emphasized the confidentiality risk of collecting encrypted traffic for later decryption and recommended combining classical and quantum-safe key-establishment techniques. TR 103 619 then organized planned migration into inventory compilation, preparation of a migration plan and migration execution. [5][19]

**Algorithm surveys were not blanket endorsements.** GR QSC 001 surveyed lattice-based, multivariate, code-based, hash-based and isogeny-based approaches. The 2021 signature and encryption/KEM reports described candidates from the third round of the United States National Institute of Standards and Technology process, using consistent notation to facilitate comparison. ETSI explicitly distinguished those descriptions from the detailed candidate specifications themselves. [7][20]

**ETSI’s end-2022 takeaway is operational.** It offered concrete QKD integration specifications and substantial quantum-safe deployment guidance, while broader certification, authentication and interoperability work continued at development stage.

**Additional documented evidence**

**Role and category**

At the inclusive **2022-12-31** snapshot, ETSI’s clearest quantum-standardization result was **ETSI GS QKD 016, “Quantum Key Distribution (QKD); Protection Profile (PP)”**, approved **2022-11-30** and still under ETSI Specialist Taskforce evaluation, scheduled to end **2023-06-30** [275]. ETSI (European Telecommunications Standards Institute) was an EU-recognized European/regional standards organization with international reach; pre-cutoff evidence describes globally applicable ICT standards and **more than 800 organizations in more than 60 countries** [114][56]. It was therefore a core European SDO with global participation, not a global intergovernmental body; its QKD work was documented among international SDO initiatives [52]. No company had a certified QKD system in 2022 [275].

**Responsible units and remit**

- **ETSI ISG-QKD**, an Industry Specification Group established in **2008**, connected science, industry and commerce to develop Group Specifications and specify a QKD system and its environment [207]. Its workflow covered use cases, requirements, reference architecture, components, protocols, interfaces, vocabulary, security proofs and certification [53].
- **ETSI TC CYBER WG QSC**, formerly ISG QSC, assessed and recommended quantum-safe primitives, protocols and implementation considerations for real deployments; its promotion to a Technical Committee working group enabled normative ETSI deliverables [207]. This was adjacent post-quantum security, distinct from ISG-QKD’s direct quantum-technology remit [53].
- Related **2022** security work by **TC TCCE**, with **SC TSA** experts, produced algorithms and specifications intended to protect TETRA networks against quantum-computer threats for **at least 20 years** [272]. The supplied record gives no identifier or publication stage, so it is not a separate confirmed quantum-document row.

**Focus, coordination and output maturity**

ETSI’s normalized focus was **communication/QKD, security/cryptography, testing/evaluation, networking/architecture, interoperability and terminology**. QKD work covered optical components and modules, characterization, implementation and protocol security, authentication, key-delivery and KMS interfaces, architectures, and SDN control/orchestration [114][270][275]. QSC covered quantum-safe/PQC migration, performance, protocols, benchmarking and application architecture [53]. Quantum computing appears as a threat and ICT-impact theme, not as a separately evidenced ETSI standards unit [114]. ETSI also joined the **2021 Joint Symposium on Standards for Quantum Technologies**, organized by ITU with IEC and IEEE’s UK & Ireland Photonics Chapter to discuss cooperation and harmonized standards [205]. Output types included informative Group Reports and Technical Reports and normative Technical and Group Specifications [68]. Reported totals vary by denominator—**14** QKD Group Specifications/Reports through December 2020, **nine** QKD specifications by 2019, and, in a 2020 account, two new QKD Group Specifications, two Group Reports and four QSC technical reports—so no 2022 total is claimed [52][54][56].

**Key records by 2022-12-31**

The inventory is selected, not exhaustive; later TBA dates are not backdated.

ETSI QKD ISG: GS QKD 015 V2.1.1 (2022-04), published; TC CYBER WG-QSC: QSC [273][276]

ETSI/QKD ISG: GS QKD 015/018 done/unpublished; GS QKD 005/013 stable drafts [130][233][235][253]

ETSI had QKD deliverables by 2022-12-31 [168][169], but the evidence is non-exhaustive [274]. ITU-T’s JCA-QKDN was approved 2022-12-16 and circulated to ETSI, IEEE, ISO/IEC JTC 1, IRTF and CEN/CENELEC FG QT [166]; IEC 61788-22-3:2022 was IEC, not ETSI [252].

By end-2022, ETSI fed European ICT standards into worldwide recommendations through the ITU and ISO/IEC JTC1 [65][66]; ISG-QKD covered QKD communication and TC CYBER WG QSC assessed quantum-safe cryptography [51][276], with QKD control/orchestration specifications and a GS QKD 013 V0.1.2 transmitter-characterisation draft [273][253][233].

Under the common taxonomy, ETSI’s local terms map to communication/QKD, security/cryptography (quantum-safe) and QKD networking/interoperability (SDN) [51][271][253]. Published cutoff outputs included GS QKD 015 V2.1.1 (2022-04), “Quantum Key Distribution (QKD); Control Interface for Software Defined Networks”; GS QKD 018 V1.1.1 (2022-04), “Quantum Key Distribution (QKD); Orchestration Interface for Software Defined Networks”; and TR 103 616 V1.1.1 (2021-09), “Quantum-Safe Signatures” [273][253][271].

rejected; reason=citation_outside_operands; allowed_entities=['ETSI']; allowed_numbers=['','V1.1.1 (2022-04)','EU Regulation 1025/2012','2008','30 March 2015','02/17','2017-03-08','0.1 - 10 THz','2021','9 specifications','ETSI GS QKD 015 v1.1.1','DGS/QKD-016','© ETSI 2022','2022-11-28','2022-12-31','more than 800 member companies and organizations','6 October 2021','over 100 strategic partnership agreements','October 10, 2025','948 members','2020-03-31','over 100 agreements','ETSI GS QKD 015 V2.1.1 (2022-04)','8 November 2022','V2.1.1','2022-12-16','GS QKD 013']; allowed_citations=[1-8,22,38,86,93,105,107,115,118-122,129,156,170,231,233,234,236,238,278,284,285,287,289-303,307,356,358,364,366,369,370,377,397,398,403-406,410-415,417-421]

## ITU-T

### Responsible bodies

**Study Groups 13 and 17 led.** Within the International Telecommunication Union’s Telecommunication Standardization Sector, **ITU-T SG13** led QKD-network architecture and operation work, while **ITU-T SG17** led security-related work. SG13’s **Working Party 3, Question 16/13**, was a principal home for trustworthy and quantum-enhanced networking and services; **Question 6/13** addressed quality-of-service aspects. SG17 established **Question 15/17**, covering security for and by emerging technologies, including quantum-based security. [6][8]

| Body | Quantum-related responsibility | Representative output |
|---|---|---|
| SG13, especially WP3/Q16 and Q6 | QKD-network requirements, architecture, management, interworking and quality of service | Y.3800-series; Supplements and reports |
| SG17, including Q15/17 | QKD-network security and quantum-related security mechanisms | X.1702, X.1710, X.1712, X.1714 |
| SG11, including Q2/11 | Signalling and QKD-network protocol frameworks | Q.QKDN_profr development item |
| SG15 | Optical transport and integration of quantum with classical communications | Transport-related studies and coordination |
| FG-QIT4N, WG1 and WG2 | Pre-standardization network aspects of quantum information and QKD networks | D1-series and D2-series technical reports |
| TSAG/JCA-QKDN coordination initiative | Cross-group and cross-organization QKD-network coordination | December 2022 liaison statement |

**The focus group supplied preparatory work.** The **Focus Group on Quantum Information Technology for Networks—FG-QIT4N**—was established in September 2019. It provided a collaborative pre-standardization platform, with WG1 addressing broader network aspects and WG2 addressing QKD networks. It concluded and adopted its deliverables as technical reports on **24 November 2021**; the reports’ forewords explicitly distinguish focus-group deliverables from ITU-T Recommendations. [1]

### Main areas of focus

**The principal focus was QKD networking.** ITU-T decomposed the subject into network concepts, functional requirements, architecture, key management, control and management, SDN control, quality of service, secure-storage integration, deployment roles and interworking. Security work addressed the network as a whole and the mechanisms by which keys are managed, combined and supplied. Quantum random-number generation was another identifiable topic, represented by X.1702. [8]

**Broader quantum networks remained exploratory.** FG-QIT4N considered quantum information technologies that enable networks, gain capabilities through networking, or improve network functions. Its scope included distributed entanglement, network-enhanced sensing, synchronization and randomness generation. That broader remit should not be confused with a completed normative architecture for a universal Quantum Internet. [1]

### Published Recommendations and Supplements

**The Y.3800-series established the foundation.** By the cutoff, the portfolio covered both foundational network functions and additional operational topics. **Y.3800** was approved on **25 October 2019** and provided an overview intended to support QKD-network design, deployment, operation and maintenance. The 2022 inventory also records Corrigendum 1 for Y.3800 and Y.3802. [21][13]

| Identifier | Document name | Type | Status by cutoff |
|---|---|---|---|
| ITU-T Y.3800; Corrigendum 1 | Overview on networks supporting quantum key distribution | Recommendation and corrigendum | Published; base approved 2019-10-25 |
| ITU-T Y.3801 | Functional requirements for quantum key distribution networks | Recommendation | Published |
| ITU-T Y.3802; Corrigendum 1 | Quantum key distribution networks – Functional architecture | Recommendation and corrigendum | Published |
| ITU-T Y.3803 | Quantum key distribution networks – Key management | Recommendation | Published |
| ITU-T Y.3804 | Quantum key distribution networks – Control and management | Recommendation | Published |

**Operational coverage expanded during the period.** The following documents addressed SDN, quality of service, storage integration, deployment roles, interworking and machine-learning-assisted assurance. Y.3809 was approved on **13 February 2022**; Y.3810 and Y.3812 were approved on **29 September 2022**. [22][23][24]

| Identifier | Document name | Type | Status by cutoff |
|---|---|---|---|
| ITU-T Y.3805 | Quantum key distribution networks – Software-defined networking control | Recommendation | Published |
| ITU-T Y.3806 | Quantum key distribution networks – Requirements for quality of service assurance | Recommendation | Published |
| ITU-T Y.3807 | Quantum key distribution networks – Quality of service parameters | Recommendation | Published |
| ITU-T Y.3808 | Framework for integration of quantum key distribution network and secure storage network | Recommendation | Published |
| ITU-T Y.3809 | A role-based model in quantum key distribution networks | Recommendation | Approved 2022-02-13 |
| ITU-T Y.3810 | Quantum key distribution network interworking – framework | Recommendation | Approved 2022-09-29 |
| ITU-T Y.3812 | Quantum key distribution networks – Requirements for machine learning based quality of service assurance | Recommendation | Approved 2022-09-29 |

**Security publications formed a complementary portfolio.** SG17’s documents addressed quantum random-number generator architecture, a QKD-network security framework, key-management security, and the combination and confidential supply of keys. The Supplement on machine learning belongs to the Y-series network portfolio and is informative rather than a Recommendation. [6][8][21]

| Identifier | Document name | Type | Status by cutoff |
|---|---|---|---|
| ITU-T X.1702 | Quantum noise random number generator architecture | Recommendation | Published |
| ITU-T X.1710 | Security framework for quantum key distribution networks | Recommendation | Published |
| ITU-T X.1712; Corrigendum 1 | Security requirements and measures for quantum key distribution networks – key management | Recommendation and corrigendum | Published in 2022 inventory |
| ITU-T X.1714 | Key combination and confidential key supply for quantum key distribution networks | Recommendation | Published |
| ITU-T XSTR-SEC-QKD | Security considerations for quantum key distribution network | Technical Report | Published, 2020-03 |
| ITU-T Y Supplement 70 | ITU-T Y.3800-series – Quantum key distribution networks – Applications of machine learning | Supplement | Issued, 2021 edition |

### Focus-group technical reports

**FG-QIT4N completed a broader report set.** Its final programme lists **nine report entries under eight deliverable identifiers**, because D2.3 has two layer-specific parts. All were adopted on **24 November 2021**. The D1 reports concern broader network aspects of quantum information technologies; the D2 reports concentrate on QKD networks. [1]

| Identifier | Document name | Type | Status |
|---|---|---|---|
| FG QIT4N D1.1 | Quantum information technology for networks terminology: Network aspects of quantum information technologies | Technical Report | Adopted 2021-11-24 |
| FG QIT4N D1.2 | Quantum information technology for networks use cases: Network aspects of quantum information technologies | Technical Report | Adopted 2021-11-24 |
| FG QIT4N D1.4 | Standardization outlook and technology maturity: Network aspects of quantum information technologies | Technical Report | Adopted 2021-11-24 |
| FG QIT4N D2.1 | Quantum information technology for networks terminology: Quantum key distribution network | Technical Report | Adopted 2021-11-24 |
| FG QIT4N D2.2 | Quantum information technology for networks use cases: Quantum key distribution network | Technical Report | Adopted 2021-11-24 |
| FG QIT4N D2.3, quantum-layer part | Quantum key distribution network protocols: Quantum layer | Technical Report | Adopted 2021-11-24 |
| FG QIT4N D2.3, other-layers part | Quantum key distribution network protocols: Key management layer, QKDN control layer and QKDN management layer | Technical Report | Adopted 2021-11-24 |
| FG QIT4N D2.4 | Quantum key distribution network transport technologies | Technical Report | Adopted 2021-11-24 |
| FG QIT4N D2.5 | Standardization outlook and technology maturity: Quantum key distribution network | Technical Report | Adopted 2021-11-24 |

**D2.2 connected standards to use cases.** It presented **21 QKD-network use cases in six classes**, covering cryptographic combinations, integration with Internet protocols, network topologies, user-device categories, network forms and vertical sectors. Its collection considered use cases that had reached at least a demonstrable proof-of-concept stage. Consequently, it was a structured account of demonstrated application possibilities, not evidence that all 21 represented mature commercial services. [25]

**D2.3 separated protocols from network frameworks.** The quantum-layer report reviewed QKD protocol types, workflows, security, parameters and commercialization. Importantly, its November 2021 assessment stated that the reviewed QKD protocols were not standardized. That finding can coexist with published Y-series Recommendations: network architecture and management can be specified while the detailed quantum-layer protocol and implementation remain heterogeneous. [26]

### Documents under development

**Interworking advanced from draft to Recommendation.** **Y.QKDN-iwfr** became **Y.3810** during 2022: a July temporary document presented the draft for consent, followed by approval on **29 September 2022**. Its year-end classification is therefore “approved Recommendation,” not “still a draft.” The Recommendation addresses interworking reference models, gateway functions, interworking functions, configurations and key-relay schemes. [27][23]

**Other network topics remained development work.** The 2022 inventory identifies the following workstreams; the November 2022 temporary-document records provide particularly clear anchors for the roadmap and quantum-enabled future-network report. [13][28][29]

| Identifier | Document name | Intended type | Pre-cutoff status |
|---|---|---|---|
| Y.QKDN-iwrq | Quantum key distribution networks – interworking requirements | Recommendation | Draft in 2022 inventory |
| Y.QKDN-ml-fra | Quantum key distribution networks – functional requirements and architecture to enable machine learning | Recommendation | Draft in 2022 inventory |
| Y.QKDN-rsfr | Quantum key distribution networks – resilience framework | Recommendation | Draft in 2022 inventory |
| Y.supp.QKDN-roadmap; TD 151-WP3 | Standardization roadmap on Quantum Key Distribution Networks | Supplement | Draft dated 2022-11-24 |
| Y.TR-QEFN / TR.QEFN; TD 148-WP3 | ITU-T’s Views for Quantum-Enabled Future Networks | Technical Report | Draft dated 2022-11-24 |

**Signalling and security had parallel workstreams.** The following entries were explicitly recorded as development work in FG-QIT4N D2.5. They demonstrate that responsibility extended beyond SG13’s architectural Recommendations to signalling, authentication, trusted nodes, management security and hybrid security approaches. [8]

| Identifier | Document name | Responsible body | Development record |
|---|---|---|---|
| Q.QKDN_profr | Quantum key distribution networks – Protocol framework | SG11/Q2 | Recommendation project, 2021 |
| X.sec_QKDN_AA | Authentication and authorization in QKDN using quantum safe cryptography | SG17 | Recommendation project, 2021 |
| X.sec_QKDN_CM | Security requirements and measures for quantum key distribution networks – control and management | SG17 | Recommendation project, 2021 |
| X.sec_QKDN_intrq | Security requirements for integration of QKDN and secure network infrastructures | SG17 | Recommendation project, 2021 |
| X.sec_QKDN_tn | Security requirements for quantum key distribution networks – trusted node | SG17 | Recommendation project, 2021 |
| TR.hybsec-qkdn | Overview of hybrid security approaches applicable to QKD | SG17 | Technical Report project, 2021 |

**Coordination also became an explicit activity.** On **15 December 2022**, the Telecommunication Standardization Advisory Group, or TSAG, issued **Temporary Document 167**, a liaison statement on the new **Joint Coordination Activity on Quantum Key Distribution Network—JCA-QKDN**. Recipients included ISO/IEC JTC 1, ETSI, IEEE and IETF/IRTF, as well as ITU-T groups and other organizations. This was a coordination milestone, not a new QKD technical standard. [30]

### What ITU-T’s portfolio implies

**ITU-T treated QKD as telecommunications infrastructure.** Its sequence of Recommendations separates what a network must do from its architecture, key management and operational controls. Y.3809 adds deployment roles, while Y.3810 addresses relationships between QKD networks. This is a different emphasis from a single device-security requirement or an algorithm definition: it is about organizing services and responsibilities across a network. [21][22][23]

**Interoperability has two materially different levels.** D2.5 distinguished key-management-level interoperability from QKD-link-level interoperability. The former can connect networks containing different vendors’ QKD links through agreed key-management interfaces. The latter requires compatibility across the quantum channel and associated protocol processing between the devices themselves, demanding substantially more detailed agreement. Published network interfaces therefore represented meaningful progress without implying universal optical-device interchangeability. [8]

**A concrete deployment illustrates that distinction.** D2.5 described Madrid’s MadQCI infrastructure in November 2021 as containing **22 QKD devices from three vendors**, combining discrete-variable and continuous-variable systems. Its integration of heterogeneous equipment with production telecommunications facilities illustrates the operational need for common management and service interfaces. Such network integration is a different achievement from allowing an arbitrary transmitter from one vendor to communicate directly with every other vendor’s receiver. [8]

**Machine learning concerned network operations.** Y.3812 specified high-level and functional requirements for machine-learning-based quality-of-service assurance. It required collection and preprocessing of quality-of-service data, a history repository and model construction, while recommending functions including training, anomaly prediction, policy decisions and reporting. Its scope was expressly quality-of-service assurance—not every possible application of machine learning to QKD, and not quantum machine-learning algorithms. [24]

**Operational examples were not performance guarantees.** Y.3812’s informative appendix discussed predicting quantum-channel noise, secret-key rate and quantum bit error rate when QKD shares dense wavelength-division-multiplexed optical infrastructure. The purpose was to support channel selection and fault handling. This demonstrates the growing specificity of operational requirements, but the appendix did not establish a universally validated prediction model or a guaranteed improvement for every network. [24]

**ITU-T’s end-2022 takeaway is architectural.** It had a substantial normative QKD-network framework, complemented by security Recommendations and a broad informative report set; this was not yet a complete standardized Quantum Internet.

## ISO/IEC

### Responsible bodies

**WG 14 led the computing programme.** **ISO/IEC Joint Technical Committee 1, Working Group 14—JTC 1/WG 14**—was established in **June 2020** for quantum computing. In **November 2022**, its title widened to **Quantum Information Technology**. Its responsibilities included identifying standardization gaps and opportunities, developing deliverables and maintaining relationships with related ISO, IEC and external committees. [3][31]

**SC 27 divided security responsibilities.** Within **ISO/IEC JTC 1/SC 27, Information security, cybersecurity and privacy protection**, **WG 2—Cryptography and Security Mechanisms** addressed cryptographic mechanisms and quantum-resistant cryptography. **WG 3—Security Evaluation, Testing and Specification** addressed QKD security requirements and evaluation methods, drawing on the Common Criteria security-evaluation framework. These were distinct technical responsibilities, not subdivisions of WG 14. [32][9]

### Main areas of focus

**Computing work emphasized common foundations.** WG 14’s portfolio covered terminology and introductory material, quantum machine-learning datasets, quantum-resource simulation platforms and quantum-simulation taxonomy. These topics help establish shared descriptions, benchmark inputs and service abstractions without prescribing a single physical qubit implementation or universal computing architecture. [3][31]

**Security work followed two different mechanisms.** QKD evaluation concerns whether physical and conventional components meet specified security requirements. Quantum-resistant cryptography concerns mathematical mechanisms and their security against classical and quantum attacks. SC 27’s division between WG 3 and WG 2 reflects that difference: a laboratory evaluation method for a QKD module is not a substitute for cryptographic algorithm assessment, or vice versa. [8][31]

### Documents under development

**The computing catalogue was developmental.** A **Committee Draft (CD)** is a committee-stage document, an **Approved Work Item (AWI)** identifies an approved development project, and a **Preliminary Work Item (PWI)** identifies preparatory work. A proposed **Technical Report (TR)** is an informative deliverable project; the TR designation alone does not establish that the report has been published. The following entries retain those distinctions.

| Identifier | Document name | Type or stage | Pre-cutoff status |
|---|---|---|---|
| ISO/IEC CD 4879 | Information technology – Quantum computing – Terminology and vocabulary | Committee Draft | CD ballot passed in April 2022; drafting continued |
| ISO/IEC AWI TR 18157 | Information technology – Introduction to quantum computing | Approved Technical Report work item | Project approved 2022-06-14 |
| ISO/IEC PWI 18660 | Information technology – Quantum machine learning datasets | Preliminary Work Item | Listed in November 2022 programme |
| ISO/IEC PWI 18670 | Information technology – General requirements for quantum resource simulation platform | Preliminary Work Item | Listed in November 2022 programme |
| ISO/IEC PWI 20153 | Quantum Simulation – Taxonomy of quantum simulator architectures and quantum simulation programming | Preliminary Work Item | Start recorded as 2022-11-23 |

**4879 remained a committee-stage document.** The committee account describes an April 2022 CD ballot that passed with numerous comments still being addressed, with publication then targeted for June 2023. Accordingly, **CD 4879** is the appropriate historical designation here, rather than importing the **Draft International Standard (DIS)** label appearing in a subsequent project overview. [33][3]

**TR 18157 had a dated approval.** Its ISO lifecycle records project approval and registration on **14 June 2022**. The November 2022 WG 14 overview places it within that group’s programme, and the 2022 committee report describes drafting of an introduction covering quantum computing, related technologies, applications and standardization. That contemporary WG 14 attribution governs this snapshot rather than later catalogue committee assignments. [34][35]

**The preliminary items had distinct identifiers.** The November 2022 WG 14 overview assigns **18660** to quantum machine-learning datasets and **18670** to the quantum-resource simulation platform. This resolves the duplicated “18670” reference appearing in the national committee’s narrative report. A retrospective project list, recording July 2022 starts, describes 18670 under the related title **“Information technology – Reference framework for quantum computing service platforms.”** The historical topic is the platform and resource-management workstream, not two separately published standards. [3][35][31]

**Simulation taxonomy entered the programme late.** PWI 20153 has a recorded start of **23 November 2022** and covers the taxonomy of quantum-simulator architectures and programming, including analog and digital quantum simulators. Its classification as a preliminary item captures the substantive decision to organize the field without treating the taxonomy as a completed International Standard. [31]

**QKD security had a two-part project.** The contemporary OPENQKD review and FG-QIT4N report identify **ISO/IEC 23837-1 and 23837-2** as the requirements and evaluation/testing projects. The 2022 BSI/UKNC proposal prints the first identifier as **23737-1**; that is retained below as the proposal’s conflicting reference, not a separate technical workstream. [9][8]

| Identifier | Document name | Responsible body | Pre-cutoff status |
|---|---|---|---|
| ISO/IEC 23837-1; printed as 23737-1 in the 2022 proposal | Security requirements, test and evaluation methods for quantum key distribution – Part 1: Requirements | JTC 1/SC 27/WG 3 | Draft International Standard project |
| ISO/IEC 23837-2 | Security requirements, test and evaluation methods for quantum key distribution – Part 2: Evaluation and testing methods | JTC 1/SC 27/WG 3 | Draft International Standard project |
| ISO/IEC PWI 19541 | Inclusion of key encapsulation mechanisms for Post-Quantum Cryptography in ISO/IEC standards | JTC 1/SC 27/WG 2 | Preliminary work; October 2022 contribution discussion |

**Quantum-resistant cryptography also had preparatory documentation.** SC 27/WG 2’s **Standing Document 8—SD8** organized a survey of quantum-resistant cryptography into six parts. A standing document prepares committee experts and supports subsequent standardization; its constituent surveys are not equivalent to six approved cryptographic standards. [31]

| Identifier | Part name | Document class | Role |
|---|---|---|---|
| SC 27/WG 2 SD8, Part 1 | General | Standing-document part | Preparatory survey |
| SC 27/WG 2 SD8, Part 2 | Hash-based Signatures | Standing-document part | Preparatory survey |
| SC 27/WG 2 SD8, Part 3 | Lattice-based Mechanisms | Standing-document part | Preparatory survey |
| SC 27/WG 2 SD8, Part 4 | Coding-based Mechanism | Standing-document part | Preparatory survey |
| SC 27/WG 2 SD8, Part 5 | Multivariate Mechanisms | Standing-document part | Preparatory survey |
| SC 27/WG 2 SD8, Part 6 | Supersingular Elliptic Curve Isogeny Cryptography | Standing-document part | Preparatory survey |

**The KEM discussion was not selection approval.** The account of the **3–6 October 2022** meeting records contribution questions concerning possible inclusion of FrodoKEM, Classic McEliece and Kyber in ISO/IEC standards. Those questions demonstrate active consideration under the PWI 19541 workstream. They should not be read as an approved algorithm list or an assurance statement about every mechanism surveyed in SD8. [31]

### What ISO/IEC’s portfolio implies

**Terminology served a practical integration function.** ISO/IEC 4879 sought a common vocabulary across basic concepts, hardware, software and applications. That is consequential when different computing platforms use similar terms for different capabilities or when purchasers need to distinguish physical resources from application-level performance. Nevertheless, terminology agreement does not establish that two quantum computers are interchangeable or have equivalent computational performance. [31]

**Datasets addressed a different comparison problem.** PWI 18660 proposed requirements for dataset characteristics, acquisition, labelling, consistency, performance and naming, with the objective of supporting quantum machine-learning benchmarks. Comparable inputs are necessary for meaningful algorithm comparisons, but a dataset specification alone does not demonstrate quantum advantage. Its value lies in reducing ambiguity around the comparison, rather than predetermining the result. [31]

**QKD evaluation linked requirements to tests.** The 23837 work applied the **ISO/IEC 15408 Common Criteria** approach to QKD. Part 1 concerned security requirements, while Part 2 concerned evaluation activities for protocol implementation, quantum optical components and conventional network components, together with supplementary assurance activities. This complements ETSI’s protection-profile work: requirements and evaluation methods describe how security should be assessed, while a protection profile specifies a particular class of product to be assessed. [8][9]

**Physical tests made the distinction concrete.** The QKD evaluation activities discussed in FG-QIT4N D2.5 included checking optical pulse intensity and state encoding, transmitter isolation, receiver back-flash, bright-light blinding resistance and calibration procedures. These are not issues resolved merely by agreeing a network architecture or key-delivery API. They show why security evaluation needed its own specialist committee and document series. [8]

**ISO/IEC’s end-2022 takeaway is foundational.** Its identifiable quantum portfolio concentrated on computing vocabulary and supporting frameworks, alongside specialist QKD evaluation and quantum-resistant cryptography work, with the listed core projects still in development stages.

**Additional documented evidence**

**Institutional role and responsible units**

**Result at 2022-12-31:** ISO/IEC was a core international standards body whose quantum work was principally organized through **ISO/IEC JTC 1**. JTC 1 is the joint ISO–IEC committee for international information-technology standardization, with national-body and expert participation; the cutoff evidence shows a distributed portfolio covering quantum computing and QKD security/evaluation rather than a standalone ISO-only committee [287][244][261].

The principal unit was **ISO/IEC JTC 1/WG 14**. Established in **June 2020** as the Quantum Computing working group, it was renamed **Quantum Information Technology** at the **November 2022** JTC 1 plenary, with a broader remit. Its responsibilities were to identify standardization gaps, maintain an inventory of standards and projects, develop deliverables, and maintain relationships with related committees and organizations [285][244]. WG 14 also reported liaison activity with IEEE P7130, JTC 1/SC 38, ITU-T FG-QIT4N and SG 13, and participation in IEC SMB/SWG 10 work on a quantum-information-technology white paper [244]. The 2021 ITU Joint Symposium on Standards for Quantum Technologies likewise brought together ITU, ISO, IEC, IEEE and other bodies to discuss cooperation and harmonized standards [205]. A later retrospective records predecessor SG 2, AG 4 and an advisory group maintaining WG 14 updates; these were support structures, not separate organization rows [212].

The security track was **ISO/IEC JTC 1/SC 27, Information security, cybersecurity and privacy protection**. Its documented quantum-related work involved WG 2/WG 3 on quantum-safe cryptography and **WG 3—Security evaluation, testing and specification** on QKD security requirements and evaluation [261]. Earlier evidence associates **JTC 1/SC 7/SG 1** with investigating quantum-computing standards [279]. A 2022 briefing associates **SC 25** with QKD certification and test protocols, but does not establish a distinct formal quantum remit; it is therefore a qualified related lead rather than a confirmed additional cutoff unit [277].

**Focus and documents at the cutoff**

ISO/IEC's normalized focus was **quantum computing and simulation; terminology and vocabulary; architectures and service platforms; datasets and benchmarking; communication/QKD; and security, certification, testing and evaluation** [244][212][278]. Quantum-safe or post-quantum cryptography is kept as an adjacent security track because the source explicitly links it to SC 27; it is not equated with QKD [261].


| Record | Exact title and status by 2022-12-31 |
|---|---|
| **ISO/IEC CD 4879** | *Quantum computing — Terminology and vocabulary*; Committee Draft listed in the November 2022 technical work [244]. |
| **ISO/IEC AWI TR 18157** | *Information technology — Introduction to quantum computing*; AWI technical report [244]. |
| **ISO/IEC PWI 18670** | *Information technology — General requirements for quantum resource simulation platform*; PWI [244]. |
| **ISO/IEC PWI 18660** | *Information technology — Quantum machine learning datasets*; PWI [244]. |
| **ISO/IEC PWI 20153** | *Quantum Simulation — Taxonomy of quantum simulator architectures and quantum simulation programming*; PWI started 2022-11-23 [212]. |
| **ISO/IEC 23837-1/-2** | *Security requirements, test and evaluation methods for quantum key distribution*—Part 1, *Requirements*, and Part 2, *Test and evaluation methods*; under development. Six drafts (3 WD, 2 CD, 1 DIS) had been commented, with publication planned for the first half of 2023 [54][261]. |

A later record gives development starts of **2020-06-26** for 4879, **2021-05-17** for TR 18157, **2022-07-06** for 18660 and 18670, and **2022-11-23** for 20153 [212]. It uses DIS/TR labels and a different title for 18670; the contemporaneous November 2022 labels therefore control. No published status is established for the WG 14 records in that dated list, and 23837 remained under development. One undated account calls 23837 “recently finalized,” but the dated 2022 evidence is stronger for the requested snapshot [275][261].

Separate IEC activity is not silently counted as JTC 1 output: the IEC White Paper (2021) and SEG 14 (formed in 2022) are distinct records [220], while ISO/IEC JTC 3 was announced only in January 2024 and is outside this snapshot [286].

ISO/IEC JTC 1/WG 14: quantum computing; CD 4879/TR18157/PWI 18670 were active in 2022 [140].

A 2020 JTC 1 plan names a WG on Quantum Computing [289]. SC 27’s ISO/IEC DTR 25544, “Effect of specific transmission media on the security evaluation of quantum key distribution,” was under development at stage 50.00; date unknown [58]. ISO/IEC 23837-1:2023 is post-cutoff [281].

ISO/IEC JTC 1/SC 27/WG3: ISO/IEC 23837, QKD security/testing draft (CD2), 2022-05-12 [282].

For the organization-by-organization comparison, ISO/IEC is the global standards-body row: ISO is international, nongovernmental and nonprofit, while JTC 1 is the joint ISO/IEC information-technology committee, global rather than regional or national; at the 2022 cutoff, WG 14 (Quantum Information Technology) followed earlier advisory work, was established in 2020, and coordinated quantum-computing work and links with other bodies, while JTC 1/SC 27/WG 3 handled QKD security evaluation, testing, and specification. Under the common taxonomy, this covered computing (terminology/vocabulary), communication/QKD, security/cryptography, and testing/evaluation; developing work included CD 4879 “Quantum computing — Terminology and vocabulary,” TR18157 “Information technology — Introduction to quantum computing,” PWI 18670 “Information technology — General requirements for quantum resource simulation platform,” and ISO/IEC 23837 “Security requirements, test and evaluation methods for quantum key distribution”; N50 “Quantum computing — Terminology and vocabulary” was a meeting report, while ISO/IEC 23837-1:2023 (published later) and IEC/ISO JTC 3 (announced in January 2024) fall outside the cutoff. [283][263][288][280][244][140][261][259][256][281][284][286]

## IEEE

### Responsible bodies

**IEEE used project-specific standards structures.** The **IEEE Standards Association—IEEE SA**—organized quantum work through sponsoring standards committees and project working groups. The broader **IEEE Quantum** initiative supported the community, but the responsible development bodies were the individual committees and groups associated with projects such as P7130, P7131, P3155 and P1943. [1][4]

**Several working groups are specifically identifiable.** **P7130** belonged to the **Quantum Computing Nomenclature Working Group—QCN-WG**, within the IEEE Computer Society’s C/SABSC structure. **P7131** was supported by the **Quantum Computing Benchmarking Working Group—QCB-WG**. **P3155** belonged to the **Programmable Quantum Simulator Working Group, NTC/SC/QuSIM/WG**, under the Nanotechnology Council’s Standards Committee, with Computer Society co-sponsorship recorded in its project form. [36][37][38]

**Communication and security used Communications Society structures.** **P1913** was associated with **COM/NetSoft-SC**, the Virtualized and Software Defined Networks, and Services Standards Committee. **P1943** was assigned to that committee’s **QuNET/WG—Post-Quantum Network Security** working group. The computing-architecture projects P3120 and P3120.1 were associated with **C/MSC**, while the P3155 authorization identifies **C/S2ESC** as the standards committee associated with P2995. [39][10][38]

### Main areas of focus

**IEEE’s coverage was comparatively broad.** Its October 2022 inventory covered terminology, software-defined quantum communication, post-quantum network security, migration, quantum algorithms, computing architecture, programmable simulation and performance benchmarking. The presentation reported **eight active quantum-technology standards projects** at that point. This was a count of active projects, not eight final published standards. [4]

**Authorization was an important status boundary.** A **Project Authorization Request—PAR** authorizes the development of a proposed IEEE document. An approved PAR, an active working group and a completed standard are different milestones. The **P** prefix and the proposed title should therefore be read together with the authorization or drafting status, especially for projects called “Standard,” “Trial-Use Standard” or “Recommended Practice.”

### Documents under development

**Computing projects covered complementary layers.** The following six identifiers encompass algorithms, architecture, simulator programming, terminology and benchmarking. P3120.1 is kept separate from P3120 because the December 2022 Standards Board record authorizes it under a different project number and title. [4][10]

| Identifier | Document name | Responsible body | Status by cutoff |
|---|---|---|---|
| IEEE P2995 | Trial-Use Standard for a Quantum Algorithm Design and Development | Computer Society, C/S2ESC | Active project in October 2022 |
| IEEE P3120 | Standard for Quantum Computing Architecture | Computer Society, C/MSC | Active project in October 2022 |
| IEEE P3120.1 | Standard for Quantum Simulator Architecture | Computer Society, C/MSC | New PAR approved 2022-12-03 |
| IEEE P3155 | Standard for Programmable Quantum Simulator | NTC/SC/QuSIM/WG | Active PAR approved 2022-02-23 |
| IEEE P7130 | Standard for Quantum Technologies Definitions | Computer Society, QCN-WG; C/SABSC | Active PAR approved 2021-09-23 |
| IEEE P7131 | Standard for Quantum Computing Performance Metrics & Performance Benchmarking | QCB-WG; Computer Society sponsorship | Active working-group development in 2022 |

**Terminology had visible title variants.** The October 2022 presentation used both **“Standard for Quantum Computing Definitions”** and **“Standard for Quantum Technologies Definitions”** for P7130. The latter also appears in P3155’s related-project list. The P7130 project record describes the work as a definitions guide promoting clarity and consistency; these descriptions identify the same nomenclature effort, rather than additional completed publications. [4][36]

**Communication and migration formed another track.** These three projects addressed the configuration of quantum communication devices and the protection of existing networks against quantum-computing threats. Their development responsibilities and goals differ from those of the computing and simulation projects. [4]

| Identifier | Document name | Responsible body | Status by cutoff |
|---|---|---|---|
| IEEE P1913 | YANG Model for Software-Defined Quantum Communication | Communications Society, COM/NetSoft-SC | Modified PAR approved 2022-12-03 |
| IEEE P1943 | Standard for Post-Quantum Network Security | COM/NetSoft-SC/QuNET/WG | New PAR approved 2022-06-16 |
| IEEE P3172 | Recommended Practice for Post-Quantum Cryptography Migration | IEEE SA P3172 project | Active project in October 2022 |

**P1913’s latest 2022 title was narrower.** Earlier inventories called the project **“Software-Defined Quantum Communication.”** The **3 December 2022** modified-PAR approval listed **“YANG Model for Software-Defined Quantum Communication.”** The historical progression supports a communication-management project with a more specific model-oriented title at the cutoff, not a final published communications standard. [10]

**P1943 progressed from submission to authorization.** Its March 2022 draft PAR was marked “Submitted,” while the **16 June 2022** Standards Board record approved the new PAR. The IEEE project page likewise records Active PAR status and that approval date. These are successive stages in the project’s development, rather than competing year-end classifications. [40][41][39]

**P3155 had concrete development milestones.** Its PAR was approved on **23 February 2022**, followed by a working-group kickoff on **17 June 2022**. The authorization form projected initial standards-committee ballot submission for January 2024 and submission to the Review Committee for January 2025. Those were project targets recorded in 2022, not completed outcomes at the historical cutoff. [38][42]

**P7131 was actively assembling benchmarks.** Its May 2022 working-group minutes assigned preparation and circulation of a benchmark template and assembly of an initial benchmark list. This is direct evidence of substantive benchmarking development, while preserving the difference between the working group’s activity and an approved benchmark standard. [43]

### What IEEE’s portfolio implies

**Simulation programming and architecture were distinct.** P3155 explicitly covered programming methods for analog, digital and hybrid quantum simulators and excluded proposals for simulator architecture. P3120 addressed quantum-computing architecture, while the separately authorized P3120.1 addressed quantum-simulator architecture. The scopes therefore support complementary workstreams; they do not justify merging the three project identifiers. [38][10]

**Benchmarking was not merely qubit counting.** P7131 addressed hardware and software performance metrics, while P2995 concerned quantum algorithm design and development. P3155’s project justification explicitly distinguished simulation-related advantage from the quantum-speedup emphasis attributed to the related algorithm and benchmarking projects. These distinctions show that IEEE’s agenda recognized multiple performance questions; project descriptions themselves were not experimental demonstrations of advantage. [38]

**Post-quantum networking emphasized retrofit engineering.** P1943 proposed a multilayer approach for adapting existing network-security protocols. Its scope included hybrid key exchange and authentication, and mechanisms for handling larger post-quantum public keys. It explicitly excluded defining a new PQC algorithm. The project therefore complemented algorithm-selection efforts by addressing how selected mechanisms could fit into actual network protocols. [39]

**Migration and protocol adaptation were complementary.** P3172’s recommended-practice project concerned post-quantum migration, whereas P1943 addressed network-security protocol mechanisms. ETSI’s existing migration and VPN reports offered an informative foundation in an overlapping area. The substantive issue was not simply which organization had the most projects, but whether guidance about inventory, migration and protocol changes could be made mutually consistent. [4][19]

**IEEE’s end-2022 takeaway is breadth under development.** Its portfolio extended well beyond QKD into computing and software engineering, but the decisive records for the listed projects were authorizations, working-group activity and drafting milestones—not interchangeable evidence of final standards publication.

## IRTF and the Quantum Internet Research Group

### Responsible body

**QIRG was the principal quantum-network body.** The relevant research group was the **Quantum Internet Research Group—QIRG**, within the **Internet Research Task Force—IRTF**. Its history records activation on **18 February 2019** and adoption of the name “Quantum Internet Research Group” on **24 March 2020**. Its approved charter, **charter-irtf-qirg-02**, was last updated on **16 May 2020**. [44][45]

**IRTF was not a standards-development organization.** QIRG’s March 2022 meeting explicitly reminded participants of that institutional distinction. The parallel **Internet Engineering Task Force—IETF** addresses engineering and standards-making, whereas IRTF focuses on longer-term research questions. Sharing document infrastructure does not make a QIRG Internet-Draft an IETF standard or give it standards-track standing. [46][47]

**Cryptographic research also had an adjacent forum.** IRTF’s **Crypto Forum Research Group—CFRG** reviewed cryptographic mechanisms for network security more generally. The December 2020 OPENQKD account distinguished that broader role from QIRG’s quantum-network architecture work and described CFRG as aware of, rather than focused on, QKD. QIRG is therefore the closest responsible body for the quantum-network documents catalogued here. [9]

### Main areas of focus

**The remit extended beyond secure communication.** QIRG’s charter named quantum-secure communication, distributed quantum computing and quantum-enhanced physical sensor systems as capabilities of a Quantum Internet. It identified QKD and quantum Byzantine agreement as cryptographic applications, while its engineering agenda covered routing, resource allocation, connection establishment, interoperability, security and APIs. [45]

**The central question was network design.** QIRG sought to turn laboratory capabilities into network services with usable architectural abstractions. Its charter recognized that quantum networks require classical connectivity for control and management, making conventional network-engineering experience relevant without assuming that quantum networks can simply copy packet-network designs. It also assigned the group a coordination role with other organizations working on quantum-network standardization. [45]

### Documents and status

**Two principal drafts defined the portfolio.** One workstream addressed architectural principles; the other categorized applications and scenarios. Both had **Informational** intended status. The following table treats them at their actual pre-cutoff revision and processing stages. [2][47]

| Identifier | Document name | Type | Status by cutoff |
|---|---|---|---|
| charter-irtf-qirg-02 | Quantum Internet Research Group | Research-group charter | Approved; updated 2020-05-16 |
| draft-irtf-qirg-principles-11 | Architectural Principles for a Quantum Internet | Informational Internet-Draft | Dated 2022-08-28; AUTH48 on 2022-12-22 |
| draft-irtf-qirg-quantum-internet-use-cases-14 | Quantum Internet Application Scenarios | Informational Internet-Draft | Dated 2022-12-11 |

**The architecture draft was in editorial processing.** Its history records submission to the RFC Editor on **5 October 2022** and transition to **AUTH48** on **22 December 2022**. For the two named document workstreams, the cutoff tally is therefore **two Internet-Drafts and zero published RFCs**. This is a tally of those two workstreams, not an organization-wide RFC census; inclusion of any RFC in a historical catalogue is determined by its RFC-series publication date, not entry into editorial processing. [48]

**The application draft remained work in progress.** Revision 14 was dated **11 December 2022** and recorded an expiry of **14 June 2023**. It was also described in the document record as **“Application Scenarios for the Quantum Internet.”** The alternate wording identifies the same draft, whose status statement explicitly says that it was submitted to the IRTF stream, was not endorsed by the IETF and had no formal standing in the IETF standards process. [47]

### What QIRG’s portfolio implies

**Entanglement changes the service abstraction.** The architecture draft treated distributed entanglement as a fundamental network resource. An entangled pair is not a packet carrying an ordinary header and payload: the quantum states and their associated classical control information must be correlated across devices. This helps explain why the document concentrated on node roles, control and data planes, resource lifetimes and service semantics rather than presenting a ready-to-deploy replacement for Internet Protocol. [2]

**Routing must account for physical quality.** QIRG’s charter identified fidelity thresholds and short quantum-memory coherence times as routing constraints. Fidelity describes how closely a produced state matches the desired quantum state; coherence time limits how long a stored quantum resource remains useful. A path that appears acceptable by conventional distance or bandwidth measures may fail an application’s requirements if states degrade while waiting for other operations. [45]

**The hardware examples were tightly qualified.** The August 2022 principles draft described successful entanglement-generation rates of the order of **10 Hz** between nitrogen-vacancy-centre nodes that could also store and process the resulting qubits. It discussed quantum-network hardware memory lifetimes on the order of seconds, while noting different capabilities and trade-offs on other platforms. These were illustrations of research-hardware constraints, not standardized performance benchmarks for all quantum networks. [2]

**Connection establishment was also a research problem.** QIRG’s charter asked what a request for entangled states should mean as it propagates through a network. It separately considered resource allocation, because finite memories and resource lifetimes cannot be reduced to path selection alone. The architecture draft consequently discussed stateful coordination of entanglement generation, swapping and delivery, rather than assuming that conventional store-and-forward behavior would suffice. [45][2]

**Heterogeneous hardware complicated interoperability.** The charter named ion traps, atomic ensembles and nitrogen-vacancy centres as examples of different physical platforms. The principles draft explained that technologies can trade entanglement-generation rate against storage and processing capabilities. An architecture intended to survive future hardware improvements therefore needed flexible abstractions, rather than treating one experimental platform’s constraints as permanent universal rules. [45][2]

**Application scope crossed three domains.** The December 2022 application draft categorized uses into quantum cryptography, quantum sensing or metrology, and quantum computing. Examples included QKD, network clock synchronization, high-sensitivity sensing, privacy-preserving remote quantum computation and distributed quantum computing. It expressly excluded computing applications purely local to one node, keeping the report focused on capabilities for which networking matters. [47]

**Remote access is not necessarily quantum networking.** Under the principles draft’s definition, a quantum network comprises nodes able to exchange qubits and distribute entangled states. A quantum computer reached only through a classical connection is not, on that basis alone, a member of such a quantum network. This is an important distinction when comparing quantum-computing cloud-service work with QIRG’s distributed quantum-computing agenda. [2]

**QKD supplied a mature reference application.** The December 2022 draft described QKD as the most mature quantum-information feature and pointed to ETSI documents for use cases and user-device interfaces. At the same time, it emphasized device imperfections and physical side-channel attacks. Its architecture counterpart described applications beyond QKD as being in their infancy, with management still dependent on low-level, custom and hardware-specific interfaces. [49][2]

**QIRG’s end-2022 takeaway is pre-standardization research.** Its contribution was to explain the architecture and application requirements that later engineering specifications would need to address, not to supply an adopted Internet protocol suite.

## Cross-organization comparison at the end of 2022

### Technology domains and institutional roles

**The organizations overlapped without being interchangeable.** ETSI’s QKD interfaces, ITU-T’s telecommunications architecture, ISO/IEC’s security evaluation, IEEE’s engineering projects and QIRG’s research abstractions addressed different parts of the same emerging ecosystem. The following matrix maps demonstrated work rather than implying that every organization had an equally mature programme in every domain. [1][4]

| Organization | Quantum communication | Quantum-safe security | Quantum networking | Quantum computing | Other relevant work |
|---|---|---|---|---|---|
| ETSI | QKD components and application interfaces | QSC algorithms, hybrids, VPNs and migration | QKD control, orchestration and architecture | Cryptographic-impact assessments | Optical characterization and implementation security |
| ITU-T | QKD-network requirements and services | SG17 security framework and key mechanisms | Architecture, management, interworking and QoS | Network-related applications in focus-group studies | QRNG architecture; networked sensing context |
| ISO/IEC | QKD security requirements and tests | WG2 quantum-resistant mechanisms and KEM work | Computing-service and resource-platform work | Terminology, introduction, datasets and simulation taxonomy | Common Criteria-based evaluation |
| IEEE | P1913 communication-control modelling | P1943 network security; P3172 migration | Software-defined communication project | Definitions, algorithms, architecture and benchmarking | Programmable simulation and simulator architecture |
| IRTF/QIRG | Quantum communication and QKD applications | Quantum cryptography research | Entanglement-network architecture and services | Distributed and privacy-preserving computation | Networked sensing, metrology and synchronization |

**The output classes reveal different maturity.** ETSI and ITU-T supplied the clearest published applied-QKD anchors. ISO/IEC and IEEE had identifiable computing and security programmes whose listed core milestones were predominantly developmental. QIRG’s architecture and application work belonged to an Informational research stream. These distinctions are more informative than a ranking based on raw document totals.

| Organization | Concrete publication or milestone anchors | Development anchors | End-2022 judgment |
|---|---|---|---|
| ETSI | Published QKD interfaces; GS QKD 018; TS 103 744; QSC reports | QKD protection profile, authentication, architecture and interoperable KMS | Applied QKD integration and migration guidance were established strengths |
| ITU-T | Y.3800-series, X-series security, Y Supplement 70, FG-QIT4N reports | Interworking requirements, resilience, roadmap and future-network studies | Telecommunications-oriented QKD framework was comparatively developed |
| ISO/IEC | CD 4879 ballot; TR 18157 project approval; specialist committee work | Computing PWIs, QKD evaluation projects and KEM preparation | Common foundations and assurance methods were still being developed |
| IEEE | Eight active projects in October; dated PAR approvals; December P3120.1 authorization | Computing, simulation, communication and migration projects | Broad engineering scope, principally project-stage evidence |
| IRTF/QIRG | Approved charter; architecture draft in AUTH48 | Two principal Informational draft workstreams | Architectural research, not standards-track protocol adoption |

### Why QKD was the most developed shared domain

**QKD exposed specifiable operational boundaries.** A QKD system can supply classical key material to an application, and its network can expose functions for key management, topology reporting, control and orchestration. These boundaries provided useful targets for ETSI interfaces and ITU-T network Recommendations even while the quantum devices and detailed protocols differed. The strongest maturity conclusion therefore concerns interfaces and operational frameworks, rather than a universal standardized quantum physical layer. [15][8]

**The security chain crossed organizations.** ETSI characterized components and developed implementation-oriented security material; ISO/IEC SC 27/WG 3 addressed security requirements and evaluation methods; ITU-T SG17 addressed network security and key-related mechanisms. These activities were complementary because a secure component, a secure module and a secure operational network are different assessment targets. None of those layers alone establishes the security of the complete application. [9]

**Trusted relaying illustrates the remaining boundary.** ITU-T D2.5 explained that a trusted-relay QKD network depends on point-to-point QKD security together with classical security for key relaying, application interfaces, and management or monitoring communications. Keys stored as classical information at intermediate nodes are not protected merely by invoking the quantum security of the adjacent links. This is why network security, trusted-node requirements and evaluation remained consequential workstreams despite published link and interface documents. [8]

**Relative maturity did not imply universal adoption.** D2.5 identified commercial QKD products and operational trials, but also discussed distance and key-rate constraints, integration costs, stability and the difficulty of achieving end-to-end security. Its assessment described adoption as concentrated in limited applications and emphasized the importance of evaluation and certification. QKD’s lead in documentary standardization should therefore not be mistaken for proof that it was the preferred security solution for every network. [8]

**QKD and PQC addressed different trade-offs.** The same report contrasted QKD’s specialist physical infrastructure and implementation challenges with PQC’s compatibility, portability and potential use of existing public-key infrastructure. ETSI’s hybrid-exchange specification and ITU-T’s key-combination work showed that the standards agenda also included combining mechanisms rather than choosing one universally. Such combinations still require careful protocol design; combining two security mechanisms is not itself a proof of correct integration. [8][9]

**The practical judgment is layered maturity.** By end-2022, QKD had the most concrete multi-organization combination of deployment, interface, network and security documents, while important protocol-interoperability and assurance questions remained distinct.

### Why computing standards emphasized foundations

**ISO/IEC and IEEE pursued different entry points.** ISO/IEC WG 14 emphasized terminology, introductory material and preliminary frameworks for datasets, platforms and simulation. IEEE’s programme spread across architecture, algorithm development, simulator programming and benchmarking. The contrast was not simply national-body standardization versus industry engineering: both were trying to create reusable foundations while avoiding dependence on one rapidly changing implementation approach. [3][4]

**Terminology was a substantive overlap.** ISO/IEC 4879 and IEEE P7130 both addressed quantum-computing language. ITU-T D1.4 explicitly identified these as parallel terminology efforts drawing on a limited pool of experts. Compatible terminology could support wider engineering alignment; inconsistent definitions could instead make procurement, benchmarking and technical communication harder across otherwise complementary standards. [1]

**Benchmarks could help without freezing architectures.** The October 2022 cross-organization briefing argued that quantum computing remained in its infancy and that direct standardization risked constraining innovation. It nevertheless identified useful work on performance benchmarks for supporting equipment and infrastructure. This supports the direction visible in the ISO/IEC and IEEE portfolios: agree how to describe, characterize and compare emerging capabilities before prescribing a complete product design. [50]

**Similar labels could hide different subjects.** ITU-T Y.3812 concerned machine learning used to operate a QKD network; ISO/IEC PWI 18660 concerned datasets for quantum machine-learning algorithms. Likewise, classical access to a quantum-computing service is different from QIRG’s exchange of quantum states between computing nodes. Domain labels such as “machine learning,” “cloud” or “networking” therefore need their technical object specified before portfolios can be compared meaningfully. [24][31][2]

**Computing maturity was consequently enabling rather than comprehensive.** The listed projects established vocabulary, comparison methods and engineering frameworks; a project authorization or terminology ballot was not evidence of interoperable, standardized quantum-computing products.

### Sensing, measurement and broader networking

**Measurement mattered beyond dedicated sensing standards.** ETSI’s optical characterization and ISO/IEC’s QKD evaluation work depended on reproducible measurements. ITU-T’s broader network reports and QIRG’s application scenarios included sensing, metrology and synchronization. These are genuine contributions to the quantum-technology landscape, but they address different things: measuring a QKD component is not the same as standardizing a networked quantum sensor application. [9][47]

**Supporting infrastructure was another important boundary.** The October 2022 briefing highlighted low-loss optical interconnect, photonic interfaces and supporting equipment as useful targets for quantum-related standardization. Such work can improve the supply chain for communication, computing and sensing without specifying the quantum application itself. It also explains why a five-organization catalogue should not be interpreted as a complete account of metrology or supporting photonics standards. [50]

**General networking faced deeper architectural change.** QIRG’s concerns about entanglement, fidelity, memory lifetimes and classical coordination extended beyond the classical-key interfaces of deployed QKD systems. Its architecture draft warned that existing metropolitan QKD networks were not necessarily an easy transition path to more sophisticated repeater-based applications. Accordingly, mature QKD-network documents and early Quantum Internet research could coexist without contradiction. [2]

**The domain judgment remains specific.** Communication standardization was strongest around QKD; computing and general quantum networking were principally building foundations; sensing appeared mainly through network applications, measurement methods and supporting infrastructure within this catalogue.

### Coordination and implications

**Coordination was real but not sovereign.** ITU-T’s 2021 assessment warned that no overarching authority controlled the initiation of international quantum standards. That did not mean the organizations worked in isolation: WG 14 recorded liaison relationships, IEEE reported liaison with ISO WG 14, QIRG’s charter assigned an external coordination role, and joint symposia brought standards communities together. These mechanisms supported alignment without replacing the organizations’ separate approval processes. [1][3][4]

**December 2022 strengthened the coordination signal.** TSAG’s JCA-QKDN liaison connected the principal organizations in this report around QKD-network coordination. Its significance was the recognition that architecture, interfaces, signalling, security and evaluation needed to fit together. The liaison itself did not establish a single organization with authority over all quantum technologies or convert research drafts into normative standards. [30]

**The strongest conclusion concerns coherent coverage.** For a QKD deployment, ETSI interfaces, ITU-T network functions and ISO/IEC evaluation methods served different needs. For quantum-computing research and engineering, ISO/IEC terminology and IEEE metrics, architecture and simulation projects were more directly relevant. For distributed entanglement networks, QIRG supplied the architectural questions and application requirements. The assessment would change with comparable pre-cutoff completed specifications and implementation evidence in other domains—not simply with a larger count of announced projects.

**Historical status is interpreted consistently.** The catalogue records key documents and their last identified pre-cutoff milestones, distinguishing approval, publication, drafting and preparatory work; later records are used only for explicitly dated earlier events. It is not a uniform global census. Counts refer to source-reported projects or explicitly bounded document sets, titles and identifier variants are retained where consequential, and no end-2022 aggregate total or performance estimate is extrapolated.

**The overall judgment is clear.** At the end of 2022, global quantum standardization was best understood as a developing, multi-organization system: comparatively concrete for QKD interfaces and telecommunications networks, increasingly organized for quantum-safe security, and still predominantly foundational for quantum computing and the broader Quantum Internet. Its practical value depended on compatible definitions, interfaces and assurance methods across organizations—not on treating every report, draft and project authorization as a finished standard.

**Additional documented evidence**

| Entity | organization name | roster inclusion status | organization type | organization category | organizational reach or geography | scope reason | relation to global quantum technology s… | organization role or status summary | specific working group or committee res… | responsible-unit remit | main areas of focus | published key standards | published key technical reports | draft or developing documents | evidence status | published or publicly issued documents | organization status summary | number or identifier of key document | name of key document | document type | document type at cutoff | document status at cutoff | document development stage | publication, approval, or development d… | document topic | key-document rationale | source reference for claim or document | allowed source citation | count of qualifying documents by status (records) | document-count denominator definition | cross-organization relationship | cross-organization role comparison | coordination mechanism | coverage difference or apparent gap | alternative explanation for difference |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| ETSI | The source uses the organization label “ETSI” in its…[160] | Explicitly included[65] | Not-for-profit association[236] | European Standards Organization[209] | Worldwide; 65 countries, 5 continents[129] | no evidence found | ETSI was one of several SDOs actively involved in…[54] | ETSI was one of several SDOs actively involved in…[54] | ETSI's quantum-related formal unit is ETSI ISG-QKD…[254] | ETSI's quantum-related formal unit is ETSI ISG-QKD…[254] | ETSI's stated quantum-related focus areas were…[205] | The source identifies three primary ETSI quantum-safe…[209] | The source identifies three primary ETSI quantum-safe…[209] | GS QKD 010/013/016/018 drafts[122][233][234] | Mixed; GS QKD 018 status conflict[253] | The source identifies three primary ETSI quantum-safe…[209] | Active QKD/QSC work; published and draft outputs[52][234] | The source identifies three primary ETSI quantum-safe…[209] | The source identifies three primary ETSI quantum-safe…[209] | The source identifies three primary ETSI quantum-safe…[209] | The source identifies three primary ETSI quantum-safe…[209] | The page presents the THz activity in a White Paper…[249] | The page presents the THz activity in a White Paper…[249] | 06/2010[207] | The source identifies three primary ETSI quantum-safe…[209] | The source identifies three primary ETSI quantum-safe…[209] | ETSI QKD document list[207] | ETSI source[207] | nearly 4 000 standards, specifications and other…[103] | Single page slice; not full catalogue[169] | Complementary, distinct QKD security approaches[51] | ETSI: specific CC profile; ISO/IEC: generic requirements[51] | ETSI renewed a Memorandum of Understanding with the…[245] | Gaps: certification, components, networks, satellites[52] | Scope/terminology differences; work-programme view[51][67] |
| ITU-T | The page uses the organization label ITU-T.[161] | explicitly included [165] | international standards body [74] | international standards-sector body [158] | worldwide [214] | Worldwide telecom standardization mandate [214] | ITU-T was one of several SDOs actively involved in…[54] | ITU-T was one of several SDOs actively involved in…[54] | ITU-T Study Group 17, specifically Q15/17, formerly…[239] | ITU-T Study Group 17, specifically Q15/17, formerly…[239] | The ITU-T study-group activity included QKD networks…[114] | The presentation states that Study Group 13 had 5…[239] | QIT4N D1.2, D1.4, D2.2, D2.3, D2.4 [256][81] | The presentation states that Study Group 13 had 5…[239] | The page’s publication metadata states: “Updated…[228] | Y.3800: Overview on networks supporting QKD [82] | Active QKDN standardization; FG-QIT4N concluded [82][114] | The presentation states that Study Group 13 had 5…[239] | The presentation states that Study Group 13 had 5…[239] | The presentation states that Study Group 13 had 5…[239] | The presentation states that Study Group 13 had 5…[239] | The presentation states that Study Group 13 had 5…[239] | The presentation states that Study Group 13 had 5…[239] | 2019 [82] | The document's stated focus is a framework for…[161] | QKD-network standard [82] | ITU-T Y.3800 work-item record [258] | Official ITU-T source [258] | 255 Recommendations (2022)[257] | QKDN subset; no complete ITU-T denominator [162] | Network-focused complement to device work [214] | QKDN coordinator with ETSI/ISO/IEEE [166] | JCA-QKDN and liaison statements [248] | Coverage concentrated on networks/security [51] | Multiple specialized groups and network remit [51] |
| ISO/IEC | The source names “ISO/IEC JTC1” but does not provide…[66] | ISO/IEC JTC 1 is presented as an international…[247] | The source characterizes ISO and IEC as “the two major…[101] | The source characterizes ISO and IEC as “the two major…[101] | The source characterizes ISO and IEC as “the two major…[101] | ISO/IEC JTC 1 is presented as an international…[247] | ISO/IEC was one of several SDOs actively involved in…[54] | ISO/IEC was one of several SDOs actively involved in…[54] | The page identifies the responsible ISO/IEC structure…[58] | no evidence found | ISO/IEC JTC1/SC27 is associated with QKD…[54] | None; 4879 and 23837 under development [140][261] | None; TR18157 under development [140] | ISO/IEC JTC 1/AG 4 produced meeting report N50 in…[256] | ISO/IEC JTC 1/AG 4 produced meeting report N50 in…[256] | 23837-1/-2—QKD requirements; CD 4879—terminology [259][140] | The source provides primary procedural evidence that…[243] | ISO/IEC CD 4879 [140] | ISO/IEC JTC 1/AG 4 produced meeting report N50 in…[256] | ISO/IEC JTC 1/AG 4 produced meeting report N50 in…[256] | ISO/IEC JTC 1/AG 4 produced meeting report N50 in…[256] | ISO/IEC JTC 1/AG 4 produced meeting report N50 in…[256] | ISO/IEC JTC 1/AG 4 produced meeting report N50 in…[256] | April 2022 [139] | ISO/IEC JTC 1/AG 4 produced meeting report N50 in…[256] | ISO/IEC JTC 1/AG 4 produced meeting report N50 in…[256] | ISO/IEC JTC 1/AG 4 produced meeting report N50 in…[256] | ISO/IEC JTC 1/AG 4 produced meeting report N50 in…[256] | 3,300+ published; ~600 in development, JTC 1 overall [263] | no evidence found | Complements ETSI; generic QKD security/evaluation [53] | ISO/IEC generic; ETSI specific QKD profile [53] | WG14 liaison relationships with IEEE and ITU-T [244] | Coverage distributed across existing units [51] | Apparent gaps may reflect incomplete evidence [100] |
| IEEE | The page uses the official organization label “IEEE…[112] | included [142] | professional organization [51] | global professional organization [142] | IEEE reports “Join over 486,000 innovators and shape…[119] | Core roster member; worldwide scope [142] | Quantum-standards contributor [144] | Quantum standards projects active/developing [113][265] | The page navigation includes “IEEE Standards,” but it…[93] | The page navigation includes “IEEE Standards,” but it…[93] | IEEE SA QuantumComm (P1913) focused on Software-Defined…[52] | IEEE 2065-2020[147] | IEEE 2065-2020[147] | P1913; P1943; P2995; P3120; P3185; P7130 [53][265][264] | The source is a 2021 IEEE SA Standards Style Manual…[260] | no evidence found | Quantum projects active/developing [113][265] | P1943 [230] | Standard for Post-Quantum Network Security [230] | standard project [230] | new IEEE standard [265] | The page lists IEEE P1913, Software-Defined Quantum…[52] | The page lists IEEE P1913, Software-Defined Quantum…[52] | 14 Mar 2022 [265] | post-quantum network security [230] | no evidence found | no evidence found | no evidence found | No quantum count; 1,500+ active/650+ developing [250][110] | No qualifying denominator stated [110] | No direct comparison established [246] | No direct role comparison [246] | ETSI renewed a Memorandum of Understanding with the…[245] | No comparative gap established [246] | Source scope may explain apparent gap [77] |
| IRTF | The official organization name displayed by the page…[115] | IRTF belongs in the research-task-force or…[117] | IRTF belongs in the research-task-force or…[117] | IRTF belongs in the research-task-force or…[117] | IRTF belongs in the research-task-force or…[117] | IRTF belongs in the research-task-force or…[117] | The page's only official IRTF label is "IRTF" in a…[265] | The page's only official IRTF label is "IRTF" in a…[265] | QIRG holds 2-3 meetings per year, online or in person…[231] | QIRG holds 2-3 meetings per year, online or in person…[231] | IRTF is associated in the source with planned standards…[53] | None; research outputs only  | No published report shown [217] | no evidence found | The page states that T2TRG was chartered on…[232] | draft-irtf-qirg-principles-11 Architectural Principles [266] | The page states that T2TRG was chartered on…[232] | draft-irtf-qirg-principles-11 [266] | Architectural Principles for a Quantum Internet [266] | Internet-Draft [266] | Work in Progress, Internet-Draft [266] | Developing; Informational [217] | AUTH48; not final [217] | 5 September 2022[107] | Quantum-network architecture [266] | Key architecture guidance [267] | QIRG draft record [266] | Permitted QIRG source [266] | no evidence found | no evidence found | The page supports only general IRTF research areas…[240] | Research/pre-standardization complement [152] | The page's only official IRTF label is "IRTF" in a…[265] | Application scenarios, not protocols [216] | Research-group remit, not standards [106] |
| CEN-CENELEC | The page identifies the institutional grouping as…[204] | Included, regional contextual comparator[53] | The page identifies the institutional grouping as…[204] | The page identifies the institutional grouping as…[204] | The page identifies the institutional grouping as…[204] | European QT roadmap and coordination activity[51] | The page identifies the institutional grouping as…[204] | Based on the roadmap, CEN/CENELEC decided in October…[213] | Technical questions are the competence of CEN or…[251] | Technical questions are the competence of CEN or…[251] | The page names CEN-CENELEC materials on “Towards…[255] | The page mentions a standards programme and Technical…[268] | The page mentions a standards programme and Technical…[268] | The page mentions a standards programme and Technical…[268] | The page mentions a standards programme and Technical…[268] | The page mentions a standards programme and Technical…[268] | Based on the roadmap, CEN/CENELEC decided in October…[213] | The page mentions a standards programme and Technical…[268] | The page mentions a standards programme and Technical…[268] | The page mentions a standards programme and Technical…[268] | The page mentions a standards programme and Technical…[268] | The page mentions a standards programme and Technical…[268] | The page mentions a standards programme and Technical…[268] | January 2022[125] | The page mentions a standards programme and Technical…[268] | The page mentions a standards programme and Technical…[268] | The page mentions a standards programme and Technical…[268] | The page mentions a standards programme and Technical…[268] | 20 % percent[173] | 20 % percent[173] | Regional complement to global SDOs[51] | Roadmap/liaison, not standards development[51] | The CEN-CENELEC Focus Group cooperated with the Focus…[125] | Regional mapping, not global inventory[51] | Regional remit and varying domain maturity[51] |
| IEC | ISO/IEC JTC 1 is presented as an international…[247] | contextually included; quantum status uncertain[51] | ISO/IEC JTC 1 is presented as an international…[247] | ISO/IEC JTC 1 is presented as an international…[247] | ISO/IEC JTC 1 is presented as an international…[247] | electrical/electronic standardization[252] | exploratory, roadmap-oriented role[97] | White paper and SEG 14; no standards deliverables[97] | The overview lists “IEC SMB/SWG 10” and describes its…[242] | The overview lists “IEC SMB/SWG 10” and describes its…[242] | The page links IEC/ISO JTC 3, described as “Quantum…[262] | IEC 61788-22-3:2022[252] | Quantum information technology white paper[97] | SEG 14 standardization roadmap[97] | mixed; IEC-specific quantum scope unresolved[97] | IEC WHITE PAPER QIT:2021—Quantum information technology[193] | no evidence found | IEC 61788-22-3:2022[252] | Superconducting strip photon detector—Dark count rate[252] | International Standard[252] | International Standard[252] | Published[252] | 6060 - Document made available - Publishing[252] | 30-Sep-2022[252] | superconducting photon detectors[252] | photon-detector measurement standard[252] | IEC publication record[252] | IEC publication record[252] | IEC 61788-22[51] | IEC 61788-22[51] | Complementary with ISO; IEC electrical scope[100] | IEC complements ISO in electrotechnical work[100] | Frankfurt Agreement with CENELEC[75] | Roadmap stage; no mature quantum portfolio[51] | Exploratory or preparatory maturity[51] |
| NIST | National Institute of Standards and Technology[178] | Contextual inclusion; not core international SDO[241] | National measurement and research institute[194] | National institute, not international SDO[184] | National, with international engagement[198] | National role; not formal international SDO[183] | National contributor to global PQC standardization[186] | National research, measurement, and guidance role[269] | The page names NIST authors and describes a NIST…[196] | The page names NIST authors and describes a NIST…[196] | The page connects NIST to quantum-resistant, or…[210] | No qualifying standard identified by cutoff[51] | NISTIR 8413-upd1 (PQC third-round status)[199] | Falcon, a digital signature algorithm, and HQC, a key…[185] | Supported; report supersession noted[269] | NISTIR 8413-upd1 - PQC third-round status report[199] | National PQC standardization; not an international SDO[269] | Falcon, a digital signature algorithm, and HQC, a key…[185] | Status Report on the Third Round of NIST PQC[199] | Falcon, a digital signature algorithm, and HQC, a key…[185] | Interagency/Internal Report[199] | NIST published the conference publication…[241] | NIST published the conference publication…[241] | September 29, 2022; November 29, 2022 update[199] | Falcon, a digital signature algorithm, and HQC, a key…[185] | PQC standardization-round status report[196] | NIST publication record[199] | Official NIST record[199] | 1 published record (source slice)[241] | Source slice; non-exhaustive[241] | NIST participated in ITU-T, ISO and ETSI work on…[53] | National measurement role complements formal SDOs[198] | NIST participated in ITU-T, ISO and ETSI work on…[53] | Few individually identified standards documents[198] | Mixed mandate/source format may explain gap[198] |

**Comparison basis and document rule**

At the inclusive **2022-12-31** snapshot, normalize focus areas as **communication/QKD, computing, networking/quantum Internet, measurement/sensing, security/cryptography, terminology, testing/evaluation, architecture, interoperability,** and **other/enabling technologies**, while retaining local wording. The underlying crosswalk also uses protocols, applications, hardware, and vocabulary. PQC/QSC is adjacent security work, not itself a physical quantum technology; QKD is direct quantum work. [51]

Treat as key any official quantum-specific standard, report, publicly issued draft, or active work item materially representing cutoff activity; the set is selected, not exhaustive. Pair every identifier with its exact title, type, topic, relevant date, and distinct status: published/approved, report, draft/active, exploratory, or unresolved/unknown. [51]

Evidence is security-heavy: PQC and QKD dominate, while computing and sensing standardization is limited; protocols recur across the available work. The source suggests immaturity as one explanation and, as an unverified assumption, vertical integration reducing demand for external interfaces. This is context, not a maturity ranking. [51]

**Common comparison labels and document states**

Use overlapping labels: communication/QKD; computing/simulation; networking/quantum internet; measurement/sensing/metrology; security/cryptography (PQC remains distinct from QKD); terminology; testing/evaluation; interoperability; architecture; and enabling components. A QKD record may carry several labels because it can address protocols, hardware, security, testing, and interfaces. The roadmap overview reports concentration in PQC, QKD, and quantum communication/security, with fewer standards for computing and sensing; this describes coverage, not maturity. [53]

Only official, quantum-specific records materially relevant to an organization’s remit qualify. Keep issuer, identifier, exact title, type, topic, date, and status at 2022-12-31 together. Published or approved standards, technical reports, drafts or active work items, roadmaps/pre-normative outputs, and research or exploratory outputs remain separate; a projected standard or identified gap is not an issued standard. The set is representative, not exhaustive, and unresolved records remain visible rather than becoming zero. Although the roadmap was composed through end-2022, its Release 1 is dated March 2023, so it is not a 2022 publication. [53]

**Evidence-stage examples**

The records support a layered comparison, not a maturity score. Pre-cutoff ETSI evidence covers QKD interoperability, security certification and control/management [56]. Its technical-group labels also distinguish interfaces, optical characterisation, quantum communications and networks [55]. ITU-T FG-QIT4N covers QKD-network telecom aspects, terminology, use cases, protocols and transport; SG13 and SG17 cover architecture and security [59]. ISO/IEC JTC 1/SC 27’s example is ISO/IEC DTR 25544, “Effect of specific transmission media on the security evaluation of quantum key distribution,” listed under development at stage 50.00, with no date supplied [58]. Non-quantum-linked SC27 entries on fully homomorphic encryption, cybersecurity and privacy remain adjacent, not qualifying records [58].

Status is separate from topic. ITU-T distinguishes QIT4N technical reports—not Recommendations—from SG17’s published and developing records [54]. ETSI’s 2020 account reports, since 2017, two QKD Group Specifications and two Group Reports, plus four QSC technical reports within three years, but no individual identifiers or titles [56]. GS QKD 005 is separately shown as a stable draft on 2022-11-29, with title unresolved [235]. IEEE P3155, “Standard for Programmable Quantum Simulator,” was a February 2022 New PAR, hence developing rather than published [57]. Keep identifier, exact title, type, topic, date and status as separate fields; unknown stays unknown.

QIRG’s quantum-Internet work is research/pre-standardization, not formal SDO issuance [54]. NISTIR 8105, 8240 and 8309 cover adjacent post-quantum cryptography, not QKD/network standards [54]. Joint JTC 1 records are not IEC-only [61]. ISO/IEC 23837-2:2023 is post-cutoff and cannot establish the 2022-12-31 snapshot [60].

Use normalized labels while retaining source terms. Communication/QKD/networking covers ETSI QKD authentication, interfaces, protection profiles, attack protection, transmitter characterization, SDN control, architectures and vocabulary; ITU-T QKD-network security, management and architecture; and QIRG quantum-Internet use cases, entanglement, teleportation and transport [67][68][69][70]. Computing covers JTC 1/WG 14 “Quantum Computing,” IEEE metrics and benchmarking, and QIRG distributed computing, which the minutes describe as work in progress distinct from the quantum Internet [62][68][69]. Security covers ETSI quantum-safe primitives—hybrid exchange, signatures, migration and stateful hashes—JTC 1/SC 27 QKD security and test-evaluation, and QIRG’s post-quantum transition; post-quantum cryptography should remain separate from QKD. Terminology, certification/testing, measurement, interoperability, procurement, benchmarks, software/algorithms and physical standards are cross-cutting labels [67][68].

Each document record keeps one paired identifier and exact title, plus type, topic, responsible unit, date and status. Approved or published deliverables, reports, drafts or active work items, exploratory/research outputs, and unresolved records remain distinct; normative and informative outputs are not interchangeable [66][68][69]. Y.3812 illustrates lifecycle handling: [35-PLEN] was a 2022-07-14 draft “for consent” [63], then an approved, in-force Recommendation on 2022-09-29, posted on 2022-12-26 [64]. It is one evolving record, not two. QIRG’s version-10 *Application Scenarios for the Quantum Internet* still needed revision before last call on 2022-03-22; it is therefore research/pre-standardization, not an approved standard [69].

Use issuer-specific status evidence: ETSI’s History clause separates public approval-stage availability from publication and its deliverable types include GS, TS, TR, GR, EG, ES and SR [66]. “Plan,” “expect” and “ongoing” do not prove publication by 2022-12-31 [67]; SG13’s 2022 pages do not supply quantum document identifiers or stages [70]. A JTC 1 catalogue with 2026 entries cannot backdate the cutoff [62], and IEEE 1451.4-2004 or 802.16 records lack an explicit quantum link [71].

**Evidence-status examples**

Pair each identifier with exact title, type, date and cutoff status; general standards machinery is not a quantum document. ITU-T’s FG-QIT4N was a Focus Group (2019-09–2021-11), submitted nine deliverables to TSAG, and produced reports on QIT networks, QKDN/beyond, terminology, use cases, protocols and transport. Its page gives no item-level identifiers, titles, dates or Recommendation status. [76] In Study Period 2022, SG13/Q6/13 listed QKDN drafts Y.3811 and Y.3812; another record lists draft TR.QEFN, “ITU-T’s Views for Quantum-Enabled Future Networks.” Treat these as developing work, not approved Recommendations. [238][237]

ETSI records show the identity rule: GS QKD 004 V2.1.1, “Quantum Key Distribution (QKD); Application Interface” (2010), and GS QKD 014 V1.1.1, “Quantum Key Distribution (QKD); Protocol and data format of REST-based key delivery API” (2019), are reported published; later v1.3.1 cannot be backdated. [73] TC QT lists communications, networking, sensing, QRNG and security; its “no standards to show” display is not a 2022 catalogue. [78] IEEE’s process distinguishes authorization, development, balloting, approval, maintenance and adoption, but no quantum record; IEEE 7000-2021 is ethical-AI, not quantum. IEC evidence supplies no separate quantum inventory. [72][79][75] “Not identified” is not zero.

The evidence reinforces two comparison rules. Focus labels are not maturity scores. In ITU-T FG-QIT4N, WG1 covers network terminology, use cases, standardization outlook and technology maturity; WG2 covers QKDN terminology/use cases, quantum-layer and higher-layer protocols, key management, control/management layers, transport and QKDN outlook [81]. These map to communication/QKD, networking, terminology, architecture, security, interoperability and evaluation/maturity; the same evidence describes a QIN linking QKD nodes, quantum computers and quantum sensors [81].

Status is record-specific. The source lists three WG1 and six WG2 deliverables but gives no publication dates, complete types or definitive 2022-12-31 status for every item; they cannot be treated as nine published standards [81]. An official ITU-T page identifies **[415-GEN]**, *“LS/i on work progress on Quantum Key Distribution Network (QKDN) in FG-QIT4N (as of March 2020),”* as a Temporary Document dated 2020-03-05 and linked to Q6/13 and Q16/13 [83]. Preserve identifier, exact title, type, date and stage; missing fields remain unresolved, not zero. A later source names earlier Y.3800 (2019) and Y.3805 (2021) Recommendations, but cannot alone establish their full cutoff status [82].

Quantum relevance is a gate. ETSI QSC covers quantum-safe cryptographic primitives, Group Specifications and deployment guidance, while excluding QKD-ISG work; “no specific deliverables planned” is developing remit, not a published record [87]. IEEE P1363.2, ISO/IEC JTC 1/WG 15’s ISO/IEC 2382 vocabulary, SC 27 security records and SC 31 AIDC records have identifiers or statuses, but the cited spans do not establish a quantum mandate [80][84][85][86]. Exclude them from the quantum denominator or label them adjacent. ETSI’s regional status and the Vienna/Frankfurt parallel-adoption mechanisms are separate comparison fields, not proof of quantum scope [88][89].

**Status and identity fields**

Use a status-separated inventory rather than a count of quantum mentions. The policy effective 2022-12-16 distinguishes ITU-T/ITU-R “Recommendations” from ISO/IEC “Deliverables”; both are “Document types,” including deliverables under development. ITU-T Study Groups develop Recommendations; labels such as SG13 “Future networks” and SG17 “Security” map to network and security categories but do not by themselves prove a quantum remit. [90][95]

An ITU-T Focus Group report, *Information and communication technologies for climate change adaptation in cities* (03/2015), shows the boundary: focus-group outputs may be reports or specifications for parent-group consideration, but are not Recommendations. [91] Each record should therefore retain its issuer, responsible unit, identifier, exact title, type, topic, date, and status at 2022-12-31.

Joint attribution is likewise part of identity. ISO/IEC/IEEE 42010:2022(E), *Software, systems and enterprise — Architecture description*, is a 2022-11 International Standard prepared by JTC 1/SC 7 with an IEEE committee; its non-quantum subject makes it an attribution example, not a qualifying quantum record. [92] A 2026 secondary page lists ETSI GS QKD 014 V1.1.1 (2019), GR QKD 012 V1.1.1 (2019), and GS QKD 015 V2.1.1 (2022), but cannot alone establish their cutoff status. [94]

IRTF illustrates research status. QIRG’s 2019 record lists Version 00 Internet-Drafts: *The Link Layer service in a Quantum Internet* (draft-dahlberg-ll-quantum); *Architectural Principles for a Quantum Internet* (draft-irtf-qirg-principles); *Connection Setup in a Quantum Network* (draft-van-meter-qirg-quantum-connection-setup); and *Advertising Entanglement Capabilities in Quantum Networks* (draft-kaws-qirg-advent). These are drafts, not approved standards; RFC 5743 (2009-12) is an Informational RFC defining the IRTF document stream. [96][98] IEC’s white paper (2021-10-26) and SEG 14 launch (2022-10-31) show roadmap work: working groups and a draft report were planned, but SEG groups cannot develop IEC standards or deliverables. [97] Thus focus labels—communication/QKD, computing, networking, testing, architecture, and security—remain distinct from maturity; unsupported dates or statuses remain unresolved, not zero.

Use 2022-12-31 as the common cutoff and one row per parent organization; nest responsible units and label reach separately. RFC 5742 distinguishes IRTF’s research stream from the IETF Standards Process and describes Research Group/IRSG review [99]. IRTF evidence is thus research or pre-standardization evidence, not automatically a formal standard.

Normalize focus fields as communication/QKD, computing, measurement/sensing, networking/quantum internet, security/cryptography, terminology, testing/evaluation, interoperability, architecture and other. Retain local wording; do not merge QKD, quantum networking or adjacent post-quantum cryptography. The RFC names neither QIRG nor a quantum focus; RFC 5742/BCP 92 (December 2009) is procedural, not quantum-specific [99].

Include only official quantum-specific records materially representative of the cutoff, not an exhaustive universe. Pair organization, responsible unit, identifier, exact title, type, topic, date and status. Separate published/approved, report, draft/active work item, exploratory output, RFC/Internet-Draft and unresolved/not found. ISO/IEC evidence distinguishes IS, TS, TR, guides and PAS and proposal-to-publication stages, including DIS/FDIS and fast-track entry. Its 2012 JTC 1 figures—498 published standards and a work-programme figure of 573—are general, not quantum-specific or a 2022 inventory [100].

IEEE “New PARs,” including P7130 and P7131, are developing proposals at their 2017/2018 approval-page dates, not approved standards; separate “New Standards” headings make that distinction explicit [104][105]. ETSI also distinguishes public availability during approval from publication and uses milestone history; its later procedural source cannot backdate a 2022 quantum status [102]. Keep “not found by cutoff,” “no qualifying item,” “not applicable” and “unresolved” visible; do not turn incomplete catalogues into zero counts or maturity rankings.

**Status-sensitive comparison of focus and outputs**

The evidence supports a two-axis comparison: subject focus and document stage. QIRG’s `draft-irtf-qirg-quantum-internet-use-cases-13`, *Application Scenarios for the Quantum Internet*, was updated 2022-06-10 and listed with an expiration date of 2022-12-12. It covers networking or the quantum Internet, communication/QKD, distributed computing, sensing/metrology, security and requirements, but is research/pre-standardization material rather than a formal IETF standard. [106][107] IRTF’s publication rules likewise describe its stream as Informational or Experimental research output, not Internet Standards Track specifications. [111]

Normalize focus labels to communication/QKD, computing, measurement/sensing, networking/quantum Internet, and security/cryptography while retaining terms such as “quantum cryptography,” “secure communication setup,” and “quantum sensing/metrology.” The evidence also names teleportation, entanglement generation and distribution, repeaters/routers, quantum memories, QKD, sensing, and network management. [106][107] QIRG’s six network stages—trusted repeater, prepare-and-measure, entanglement-distribution, quantum-memory, fault-tolerant few-qubit, and quantum-computing networks—describe technology progression, not six standards. [106][107]

Keep output stage separate: published or approved standard; technical report; draft or work in progress; active work item or PAR; and unresolved. For illustration, `draft-irtf-qirg-principles-10`, *Architectural Principles for a Quantum Internet*, 2022-02-14, and `draft-dahlberg-ll-quantum-03`, *The Link Layer service in a Quantum Internet*, 2019-10-10, are WIP Internet-Drafts. [107] ETSI GS QKD 014 V1.1.1 is recorded as a Standard for a QKD-network protocol/data format, while GR QKD 002 V1.1.1, *Use Cases*, 2010, and GR QKD 003 V2.1.1, *Components and Internal Interfaces*, 2018, are technical-report records. [108][107] IEEE P1943, *Standard for Post-Quantum Network Security*, has a PAR Approval date of 2022-06-16; its post-quantum network-security scope is adjacent to, not synonymous with, QKD. [113]

Each record should preserve its identifier, exact title, type, topic, date, status, and source qualification. IEEE observations labeling P1913 as a New PAR and P1913.1 as an active project should remain separate until their relationship and cutoff status are resolved; no date should be inferred. [109][110]

Document fields also need status separation. The evidence distinguishes ITU-T Recommendations (normative international standards) from FG-QIT4N technical reports or specifications, which are informative and not Recommendations; QIRG Internet-Drafts are intended informational RFCs, not standards specifications. [114][116] Each record should pair its identifier with the exact title, then separately record type, topic, date, development stage—published or approved, report, draft, active work item, exploratory, or unresolved—and status at 2022-12-31. The IEEE entries—P1913 “SW Defined Quantum Communications” (2016), P7130 “Quantum Technologies Definitions” (2020), and P7131 “Quantum Computing Performance Metrics & Performance Benchmarking” (2020)—show why identity fields cannot substitute for status. [118]

Retain identifier, exact title, type, date and status. ITU-T Q16/13 covers QKD networks, quantum-enabled future networks, satellite QKDN, use cases, architecture, key management, control/management and SDN control; its milestones are 2023–2025, so not 2022 publications. [120] ETSI’s 2022-10-31 release reports completed TS 100 392-7 and TS 100 396-6 TETRA security specifications, but no titles or publication/approval status. [121]

The roadmap was released in March 2023; use only its underlying end-2022 evidence, not the release itself.[122] Activity concentrated in post-quantum cryptography, QKD and quantum communication; quantum computing and sensing were less standardized, while only QKD/quantum communication covered protocols, applications, hardware and vocabulary.[122] Use labels: communication/QKD, computing, networking/Internet, measurement/sensing, security/cryptography (post-quantum separate), terminology, testing, interoperability and architecture; retain issuer wording.[122]

Taken together, the evidence supports a normalized taxonomy, not a single “quantum” label: communication/QKD; computing/simulation; networking/quantum Internet; measurement/sensing/metrology; security/cryptography; testing/characterization; interoperability/interfaces; architecture; terminology; and enabling technologies/components. The CEN-CENELEC roadmap spans these areas and use cases, but treats superconducting-circuit packaging, parametric amplifiers, quantum dots, photon sources/detectors, QRNGs and memories as pre-normative or projected work—not approved standards [122]. ETSI’s QKD evidence connects communication with security, optical characterization, vocabulary, SDN/network architecture and interoperable key-management interfaces [127]. A 2021 standards symposium likewise grouped communication, computation and measurement [123]. Preserve local wording and keep post-quantum cryptography distinct from QKD; labels describe coverage, not maturity.

Examples show the identity rule: ETSI GS QKD 012 V1.1.1, “Quantum Key Distribution (QKD); Device and Communication Channel Parameters for QKD Deployment,” is a Group Specification published 2019-02 [126]; IEEE P3155, “Standard for Programmable Quantum Simulator,” was an active project with PAR approval 2022-02-23 [124]. NIST names activities but supplies no identifiers, exact titles or individual dates, so those fields are unknown—not zero [122]. Overall totals such as ETSI’s >53,000 standards are not a quantum denominator [128].

**Status-sensitive comparison conventions**

Normalize as communication/QKD, computing, sensing, networking/quantum Internet, security/cryptography, terminology, testing/evaluation, interoperability and architecture; retain local wording. ETSI covers QKD, quantum computing, quantum-safe cryptography (adjacent security), architecture/frameworks, vocabulary, optical characterization and security/schema/assurance; informative reports, White Papers and Guides differ from normative Technical Specifications and Group Specifications. [134] ITU-T covers QKDN resilience, quantum-enhanced/trustworthy networking and quantum-based security; FG QIT4N adds memories, repeaters, end-nodes, distributed entanglement, networked sensing, timing/synchronization, randomness and improved security. These are coverage labels, not maturity scores. [131][134][135][136]

Every row pairs issuer/unit, identifier, exact title, type, topic, date and cutoff status. Examples: ETSI GS QKD 015 V2.1.1 (2022-04) had “Current Stage 12—Completion” on 2022-04-07 but “Status Not Published”; ITU-T Y.3809 (02/22) was an in-force Recommendation (updated 2022-07-12); ITU-T 84-WP3 (Draft Recommendation Y.QKDN-iwrq) was a 2022-09-20 Temporary Document for Q16/13, restricted to TIES users. [130][133][132] Completion, publication and developing temporary status are separate.

**Evidence-qualified status categories**

- **ITU-T—networking.** SG13’s WP3/13 is “Network Evolution, Trust and Quantum Enhanced Networking”; Q16/13 is “Future Networks: Trustworthy and Quantum Enhanced Networking and Services.” The source covers 2017–2020 and calls Q16/13 a question under study, not a Recommendation/report; 2022-12-31 status is unresolved [137].
- **ISO/IEC JTC 1—computing, terminology and adjacent security.** Evidence dates a post-quantum-cryptography study to 2015, a quantum-computing standardization evaluation to 2018, and a Quantum Computing Working Group to 2020; it later names a Quantum Information Technology Working Group but gives no successor date or cutoff status. Normalize its focus as security/PQC (adjacent), computing, QIT, terminology/vocabulary and simulation [138][141].
- **IEEE—multiple tracks.** IEEE-SA is the standards platform; 2022 governance separates PARs, draft/final Work Products and publication, requiring Board approval before publication [143][146]. QCN-WG’s P7130, “IEEE Draft Standard for Quantum Technologies Definitions,” was an Active PAR approved 2021-09-23 [144]. QCB-WG P7131 was assembling benchmarks in May 2022, with no publication shown [145]. QCIT-ETC lists liaison records 1913 “Software-Defined Quantum Communication,” 7131 “Standard for Quantum Computing Performance Metrics & Performance Benchmarking,” and 7130 “Standard for Quantum Computing Definitions”; stages and dates are absent, while its focus includes communications/networking, metrology/sensing, architecture, simulation and algorithms [148]. Photonics 2065-2020 and 2067-2021 are adjacent, not automatically quantum-specific [147].
- **IRTF/QIRG—research/pre-standardization.** QIRG is a full research group covering quantum cryptography, cloud computation, enhanced sensing, networking/Internet architecture, protocols, management, security and APIs. A 2020 account names “Applications and Use Cases for the Quantum Internet” and “Architectural Principles for a Quantum Internet” as Internet-Drafts near last call, intended for research or possible RFCs rather than formal standards; it does not establish 2022 status. RFC 9340 (2023-03), RFC 9583 (2024-06) and 2026 drafts are outside the cutoff [149][150].

**Applying the common taxonomy to heterogeneous records**

The comparison should yield a normalized, status-separated evidence set, not a raw document count. Apply communication/QKD, computing, measurement/sensing, networking/quantum Internet, security/cryptography, terminology, testing/evaluation, interoperability, architecture, interfaces, and other labels in parallel, retaining source wording. The QIRG charter maps quantum-secure communication and QKD to communication/security; distributed quantum computing to computing; quantum-enhanced sensors to sensing; routing, resource allocation, connection establishment, and network coding to networking; node roles and interoperability to architecture/interoperability; API design to interfaces; and applications and multi-party states to other applications [152]. Keep QKD distinct from adjacent post-quantum cryptography unless explicitly linked.

Topic does not establish maturity. QIRG was an approved, active research group, but described an architectural framework and capability roadmap as prospective work items, not completed standards [152]. IRTF may publish informational or experimental RFC material without being a standards-development organization [151]; an IETF-106 record lists QIRG items as Version 00 Internet-Drafts [154]. ANRW ’22, held on 2022-07-26, was an academic workshop, not an RFC or standards-track deliverable [155]. Type and status cells must therefore separate standards or Recommendations, reports, drafts, work items, research outputs, and workshops.

Each qualifying record should pair issuer and responsible unit with identifier, exact title, type, topic, version or date, status at 2022-12-31, and evidence qualification. The ITU-T catalogue exposes this schema through “Rec.”, “Type of text”, “SG”, “Status”, “Date of approval”, and “Title” [156]. Its quantum example is **ITU-T TSAG Temporary Document 579, “Quantum Work Consolidation”**: attributed to SG13/SG17 chairmen, dated and posted 2019-09-10, and marked “Public Document”; the page labels it a Temporary Document rather than a Recommendation [159]. A charter revision, **charter-irtf-qirg-02** (2020-05-13), is organizational evidence, not automatically a technical deliverable [153]. ISO stage labels—PWI, NP/NWIP, AWI, WD, CD, DIS, FDIS, PRF, and IS—must likewise remain distinct from publication [157].

Separate topic from status. ETSI’s April 2022 list includes ordinary TS/TR records without established quantum relevance, but also lists GS QKD 015 V2.1.1, “Quantum Key Distribution (QKD); Control Interface for Software Defined Networks,” and GS QKD 018 V1.1.1, “Quantum Key Distribution (QKD); Orchestration Interface for Software Defined Networks.” Both appear on 2022-04-04–10 under “on approval procedure or published,” so their exact stage remains unresolved [160].

ITU-T Y.3812, “Quantum key distribution networks – Requirements for machine learning based quality of service assurance,” is an SG13 Recommendation approved 2022-09-29; its cited earlier X/Y records are not standalone publication proof [164]. Public Document 1192, “Final report of the Focus Group on Quantum Information Technology for Networks,” is dated 2021-11-16; postings on 2021-12-14 and 2022-01-13 (addendum) are not necessarily approval dates. TSAG-LS11, approved 2022-12-16, is a JCA-QKDN liaison statement, not a standard or technical report [163][166]. Each record therefore retains its identifier, title, unit, type, topic, stage, and date.

By March 2022, ITU-T reported one first QKDN Recommendation, eight more approved, 12 ongoing, and one Supplement, but no complete denominator [162]. Separate QKD/networking, architecture, key-management, security, interworking, and terminology labels; QKD and post-quantum cryptography are complementary, not identical [165]. “Quantum computing” means use of quantum phenomena for computational purposes (ISO/TS 80004), but that source’s date and status are not established [167].

At 2022-12-31, the evidence supports a functional comparison, not a maturity ranking by raw counts. ETSI’s published Group Specifications cover QKD application delivery (GS QKD 004 V2.1.1, 2020-08), SDN control (GS QKD 015 V2.1.1, 2022-04), and orchestration (GS QKD 018 V1.1.1, 2022-04); these examples establish networking, interoperability and security work, not computing or sensing coverage. [168][169][170] ITU-T’s QKDN work spans communication, security, QoS, interworking, signalling and quantum-random-number generation; SG13 had 15 Recommendations and three Supplements by the cutoff. FG-QIT4N was exploratory, expired in December 2021 after nine reports, and JCA-QKDN began late in 2022.  ISO/IEC JTC 1 covered quantum-computing terminology (ISO/IEC 4879, with completion projected for 2022) and QKD testing/evaluation (ISO/IEC 23837-1/-2, Committee Drafts); IEEE projects covered communication, architecture, terminology, benchmarking, post-quantum security and computing. 

Keep each identifier with its exact title, type, topic, date and status. Draft and approved Recommendations, published deliverables, reports, work items, exploratory outputs and research RFCs are different stages. [171] RFC 9340, *Architectural Principles for a Quantum Internet*, and *Application Scenarios for the Quantum Internet* are QIRG research or technical outputs, not formal standards.  The cited CEN-CENELEC roadmap/JTC 22 and IEC SEG 14 activity is from 2023 and cannot establish a 2022 record. IEC’s 475 Standards published in 2022 is a general total, not a quantum count; the shown NIST/PQC reference leaves a qualifying NIST record unresolved. [172]

Code CEN-CENELEC as a European/regional framework, not a global SDO. Its European Standards are voluntary, consensus-based outputs using formal processes, open consultation and periodic review; national delegation yields one standard across member countries [173]. Guide 30’s around 19 000 European Standards (about 20% EU-harmonized; 2015) is general background, not a quantum denominator. The cited general material supplies no qualifying pre-cutoff quantum identifier, title or status, so the cells are “not established,” not zero [173]. Vienna/Dresden cooperation with ISO/IEC shows linkage, not a quantum deliverable [177].

Keep process and subject fields separate. CEN-CENELEC JTCs use an NWI process with stages of first working draft (20.60), enquiry (30.99) and formal vote (45.99). Both Technical Boards must approve an NWI before CCMC registration; a resulting deliverable bears the dual CEN-CENELEC logo [179]. These fields show issuer and stage, not a quantum work item. JTC 21, established in 2021, is an AI-standardization committee, not a quantum unit [174]. JTC 22 and CEN/CLC/TR 18202:2025 are post-cutoff: established in 2023 and published 2025-09-03, respectively; exclude both [175].

NIST is a national comparator. Historical material describes a U.S. measurement-and-standards institute with an information-technology standards remit; its organization-informed 1989 directory cannot establish quantum status at 2022-12-31 or prove absence [178]. A later summary links a 2016 process to post-quantum cryptography, supporting security/cryptography (adjacent PQC), not automatic QKD, computing or international-SDO classification [176]. Retain each record’s exact identifier, title, type, topic, date and cutoff status. Later evidence cannot backdate documents; missing evidence is “not found,” “not established,” or “unresolved,” never zero.

Separate document stage from topic. A CEN-CENELEC page posted 2023-03-22 calls a Standardization Roadmap and a Quantum Technologies Use Cases report “published,” but its post-cutoff date cannot establish either item’s publication date or status at 2022-12-31 [180]. Treat the labels as a post-cutoff evidence note, not as proof of 2022 status. A 2024 CEN-CENELEC guide lists generic EN, TS, TR, and CWA types and says a CWA is not a European Standard; because it supplies no quantum identifier, exact title, date, or cutoff status, it cannot populate a 2022 record [182]. The FGQT-to-JTC 22 progression signals exploratory-to-committee development, but the cited page leaves the JTC kick-off year unspecified [189].

NIST shows why selection is not publication: four algorithms were announced for standardization in 2022, while final standards for the first three were published in 2024 and a FALCON-based standard was planned later [183][186]. Record the 2022 state as selected or developing, not published.

Thus every key-document row keeps its identifier, exact title, type, topic, date, cutoff status, and source separately; unsupported fields remain unresolved. The key set is representative, not exhaustive: NIST’s publications database says it is incomplete and continually updated [188]. Geographic categories also remain distinct: CEN-CENELEC is European/regional, with 43 national organizations from 34 countries [181], whereas NIST is a U.S. national institute [187]. Neither institutional reach nor a visible record count is a maturity measure.

Normalize focus labels but retain source terms. FGQT maps to communication, computing/simulation, and metrology/sensing/imaging, plus cross-layer interfaces and interoperability; a 2021 record adds a QKD-security roadmap [190][192]. IEC’s QIT paper covers computing, research/technology, market readiness, and standardization readiness in a nascent field [193]. NIST covers quantum information/sensing, IT standards/testing/cybersecurity, and communications test protocols; its QIS agenda also addresses infrastructure and international cooperation [194][195].

Document identity and stage stay separate. CEN’s Q02–Q05 records are distinct; Q04, “Standardization Roadmap on Quantum Technologies,” has no supported 2022 publication/status, and a page marked 2023-01-01 cannot backdate it. Earlier evidence calls it a living roadmap planned for spring 2022, with a QKD roadmap under preparation; Q05 lacks a supplied date/status [190][191][192]. IEC’s “IEC WHITE PAPER QIT:2021—Quantum information technology” is dated 2021-10-20, edition 0.0, yet labelled “International Standard” despite being described as a white paper [193]. NIST IR 8413, “Status Report on the Third Round of the NIST Post-Quantum Cryptography Standardization Process,” is a July 2022 report updated 2022-09-26; 15 candidates were assessed and four advanced to round four [196]. Retain identifier, title, type, topic, date, and status; mark unknowns and classify PQC separately as adjacent security/cryptography.

Document rows must preserve identifier, exact title, type, topic, date and status. NISTIR 8413-upd1, *Status Report on the Third Round of the NIST Post-Quantum Cryptography Standardization Process*, was published 2022-09-29 and updated 2022-11-29; it records CRYSTALS-Kyber, CRYSTALS-Dilithium, Falcon and SPHINCS+ selected for standardization, while BIKE, Classic McEliece, HQC and SIKE remained under fourth-round evaluation. Selection, evaluation and development are separate statuses. [199] The 2017 book chapter, 2018 journal article and 2022 metrology paper are research outputs, not identified standards or work items, so label them separately. [197][201][202] The supplied sources do not establish an exhaustive NIST catalogue: report an unresolved document universe, not zero; a page created 2023-03-12 cannot establish the 2022 snapshot. [198][200][203]

Keep each document as one identity record: official identifier and exact title, then type, topic, publication/approval/draft/development date, and status at 2022-12-31. “Key” means a selected, official, quantum-specific standard or Recommendation, technical report, publicly issued draft, or active work item materially representing cutoff activity; the set is not exhaustive. Exploratory roadmaps and research outputs remain visible only with their actual type. Thus formal specifications or Recommendations, reports, active projects, under-revision records, roadmaps, and QIRG technical documents cannot be collapsed; RFC 9340 is not automatically a formal standard [206][208]. A document issued in 2023, such as the ISO/IEC 23837 parts, is outside this snapshot [207].

Map local terms without merging unlike work: ETSI—QKD security, components, interfaces and architecture/interoperability; ITU-T—QKDN security, architecture and key management/control; ISO/IEC 23837—QKD security requirements/testing; IEEE P1913—software-defined quantum communication. IRTF/QIRG is quantum-Internet research, not formal standardization; CEN-CENELEC FGQT is regional coordination, not standards issuance. NIST’s record is an algorithm-selection process with no dated identifier or 2022 status. [52][210]

Each record keeps its issuer, identifier, title, type, topic, date and 2022-12-31 status. Published/approved standards, reports, drafts/work items, exploratory outputs and research remain separate: an IEEE Network paper is research, not a standard [211]; QIRG Internet-Drafts are informational work in progress, not IETF standards [211]; and ISO/IEC DIS, TR and PWI denote distinct record types or stages [212]. Later sources may corroborate, not backdate; compare coverage and stage, not maturity or volume.

**Comparison labels and document records**

Use focus labels as analytical categories, not maturity scores: communication/QKD, computing, measurement or sensing, networking or quantum Internet, security or cryptography, terminology, testing or evaluation, interoperability, architecture, and other. Retain the issuer’s wording alongside the normalized label. For example, ITU-T Y.3810 covers communication/QKD, networking, architecture, and interoperability because it specifies QKDN interworking, reference and functional models, configurations, gateway functions, and interworking functions [214]. Post-quantum cryptography remains a separate adjacent category unless the source explicitly connects it to quantum technology, QKD, or quantum networking.

The cutoff test is substantive, not merely bibliographic. **Recommendation ITU-T Y.3810, “Quantum key distribution network interworking – Framework,” edition 1.0**, was assigned to Study Group 13 and approved on **2022-09-29**; its unique identifier is **11.1002/1000/15063**, so it belongs in the snapshot [214]. By contrast, **ITU-T Y.3813, “Quantum key distribution network interworking – Functional requirements,”** was approved on **2023-01-13** and is excluded from the 2022 inventory [215]. A source that confirms one qualifying record does not prove that no other record existed; document counts therefore require the same inclusion rule and must not be treated as maturity rankings.

**Applying the common comparison basis**

QIRG illustrates the distinction. Its 2022 use-cases draft classifies applications as quantum cryptography/QKD, quantum sensing, and quantum computing, while calling the list initial and non-exhaustive; it also discusses networking, entanglement, repeaters, management, routing, signaling, and separate classical and quantum channels. [216][218] *Application Scenarios for the Quantum Internet*, `draft-irtf-qirg-quantum-internet-use-cases-14`, was published on 2022-12-11 as an Informational Internet-Draft—working material, not an approved standard. [216] *Architectural Principles for a Quantum Internet*, `draft-irtf-qirg-principles-11`, reached RFC Editor “AUTH48” on 2022-12-22; completion recorded on 2023-02-21 is outside the snapshot, so it remains a developing draft at cutoff. [217]

Evidence supports a strict identity-and-stage rule. ETSI GS QKD 015 V2.1.1 (2022-04), “Quantum Key Distribution (QKD); Control Interface for Software Defined Networks,” is a Group Specification for SDN-QKD management, but its catalogue says “Not Published” while recording stage 12—Completion and completion on 2022-04-07 [219]. Mark it completed-stage with qualified publication status. Other ETSI records distinguish a 2010 publication (GS QKD 002) from TR 103 618, published 2019-12-12 and not a Harmonised Standard [221][222]. These are representative records, not an exhaustive catalogue.

ISO/IEC separates unit activity from deliverable stage: its Quantum Computing Working Group became the Quantum Information Technology Working Group in 2022; evidence reports 2 approved projects and 3 preliminary work items [220]. PWI 18670, “Information technology — General requirements for quantum resource simulation platform,” was a JTC 1 project at stage 00.00 (“Proposal for new project received”), effective 2022-07-06 [225]. The proposal covers computing, simulation, QKD/communications, quantum Internet, testing and post-quantum-cryptography integration; it identifies WG 14 and SC 27/WG 3, while a new JTC remains proposed [226].

Use one taxonomy: QKD/control = communication and networking; computing/simulation/vocabulary = computing, testing and terminology; post-quantum cryptography remains distinct from physical QKD [219][220][226]. ITU-T separates normative Recommendations from non-normative reports and Focus Group Technical Specifications, which may feed later Supplements or Recommendations [229]. CEN-CENELEC is regional context, not global scope [227]. Do not backdate: ETSI GS QKD 021 was created 2023-02-02; IEC JTC 3 evidence is from April 2024, and IEC 80000-6:2022 is not identified as quantum-specific [224][223].

**Evidence-sensitive comparison**

**Additional documented evidence**

At **2022-12-31**, public quantum standardization concentrated on **QKD/PQC, network security and protocols**; computing and sensing had fewer standards. The gap may reflect early maturity, fragmented mandates or non-public work, not inactivity. [51][207]

**ETSI**: ISG-QKD covered QKD requirements, architectures, interfaces, security and certification; TC CYBER WG QSC addressed adjacent classical quantum-safe cryptography. **ITU-T**: SG13/17/11 covered QKDN architecture, key management, security and signalling; FG-QIT4N supplied exploratory pre-standardization. SG13 reported **15 Recommendations and 3 Supplements by 2022-12-31**—not a common-denominator count. [51][207]

**ISO/IEC JTC 1**: WG14/QIT coordinated quantum-computing work; SC27/WG3 handled QKD evaluation, with ISO/IEC 23837-1/-2 in draft. **IEEE**: projects included P1913, P2995, P3120, P3155, P7130 and P7131; individual 2022 stages are unresolved. [51][206][207]

**IRTF/QIRG**: research/pre-standardization—not formal standards—on quantum-internet architecture, QKD and trusted repeaters; RFC 9340 is dated **March 2023**, outside scope. **CEN-CENELEC FGQT** was regional exploratory/liaison work; JTC 22 QT was agreed **October 2022**, but Roadmap Release 1 appeared **March 2023**. **IEC SEG 14** began needs/roadmap work **October 2022**; IEC 61788-22-3 was a committee draft. **NIST** was a national measurement/PQC comparator: in **2022**, it selected **1** encryption/key-establishment and **3** signature algorithms; FIPS 203–205 were published in **2024**. [51][302]

Coordination included the **23 March 2021** ITU symposium with IEC and IEEE’s UK & Ireland Photonics Chapter, attended by ISO, IEC, NIST, ETSI and CEN-CENELEC; **JCA-QKDN** began in **late 2022** to engage study groups and fora. [205] Except for the source-specific ITU-T count, comparable totals remain unresolved under a common denominator of qualifying public quantum-specific records; raw totals do not measure maturity.

CEN-CENELEC FGQT: regional exploratory; metrology/testing; 2022 count unresolved [52][208]

2022-12-31: ETSI—QKD pub./draft; ITU-T—QKDN Recs.; ISO/IEC—drafts; IEEE—projects; IRTF—research; CEN-CENELEC—roadmap; NIST—PQC/metrology [53][292]

At 2022-12-31, ITU-T approved Y.3810 (QKDN interworking; 2022-09-29), while Y.3812 remained a draft “for consent” (2022-07-14) [293][63]. QIRG drafts were Work-in-Progress, not formal standards [211]; FG-QIT4N linked ITU-T to ETSI, IEEE, ISO/IEC and IRTF [59].

ITU-T:Y.3810 interworking;Y.3812 ML-QoS,approved 2022-09-29 [64][214];QIRG:2022 drafts,not standards [216][217];ETSI:QKD/QSC;2022 count unresolved [67];IEEE:no quantum record [72]

By 2022-12-31: ETSI QKD/QSC outputs [221][222]; ITU-T Y.3800/Y.3805/Y.3811, 9 FG-QIT4N outputs [76][82][301]; ISO/IEC PWI 18670 [225]; IEC white paper/SEG [220]; CEN FGQT/JTC22 [290].

By Nov 2022, ITU-T SG13 reported 13 QKDN Recommendations plus one supplement; QIRG outputs were drafts, while IEC SEG14 was exploratory work [294][96][97].

IRTF/QIRG: quantum-Internet research, not formal standards [291].








QKD maturity remains uneven [54].


By the cutoff, ITU-T FG-QIT4N had liaison statements with ETSI ISG QKD and IRTF QIRG, approved on 2020-03-31 [299]; Q16/13 identified cooperation with SG11/SG17, ETSI ISG-QKD, ISO/IEC JTC1/SC27 and IETF/IRTF, while QIRG served as a coordination point for quantum-network standards bodies [294][297]. ISO/IEC JTC 3 coordinated with committees and WG14 received statements from IEEE P7130, ITU-T FG-QIT4N and SG13 [284][244]; IEEE reported liaison with ISO WG14 and a forthcoming CEN/CENELEC liaison [295], CEN-CENELEC sent its FGQT roadmap to ITU-T FG QIT4N, ISO/IEC JTC1/WG14 and ETSI ISG-QKD for comments [300], and its Vienna/Frankfurt Agreements supported harmonization and parallel adoption [89]; ETSI's joint work with CEN/CENELEC and OCG addressed duplication or conflict as far as possible [298], while ISO/IEC QKD work linked to ITU-T SG17 through document circulation and expert review [259]; NIST contributed ecosystem support through QEDC and the National Quantum Initiative [296].

## References

[1] <https://www.itu.int/en/ITU-T/focusgroups/qit4n/Documents/D1.4.pdf> ITU-T’s standardization assessment; ITU-T institutional comparison; ITU-T readiness assessment; FG-QIT4N’s institutional and output record; FG-QIT4N D1.4 scope…
[2] <https://datatracker.ietf.org/doc/draft-irtf-qirg-principles/11/> QIRG’s August 2022 architecture draft; QIRG’s architectural definitions; Architecture draft, revision 11; QIRG’s architecture model; Architecture draft’s physi…
[3] <https://jtc1info.org/sd-2-history/jtc1-working-groups/wg-14/> ISO/IEC WG 14 overview; November 2022 WG 14 overview; WG 14’s technical-work list; November 2022 committee listing; WG 14’s identifier mapping; WG 14’s 2022 wo…
[4] <https://standict.eu/sites/default/files/IEEE-SA-&-standict.eu_2022-10-13.pdf> IEEE’s 2022 project inventory; IEEE’s October 2022 project account; IEEE’s eight-project inventory; October 2022 inventory; IEEE’s 2022 title variants; IEEE’s…
[5] <https://www.etsi.org/newsroom/press-releases/1382-2018-10-press-etsi-tc-cyber-releases-report-on-quantum-safe-virtual-private-networks/> ETSI’s international remit; ETSI’s identification of the QSC working group; ETSI’s VPN report explanation
[6] <https://www.itu.int/hub/2021/03/standards-bodies-to-coordinate-contributions-to-quantum-information-technology/> ITU’s March 2021 coordination overview; ITU’s description of the lead groups; ITU’s security-document overview
[7] <https://www.etsi.org/deliver/etsi_gr/QSC/001_099/001/01.01.01_60/gr_QSC001v010101p.pdf> ETSI’s algorithmic framework; GR QSC 001; GR QSC 001 assessment scope
[8] <https://www.itu.int/dms_pub/itu-t/opb/fg/T-FG-QIT4N-2021-D2.5-PDF-E.pdf> ITU-T’s QKD technology assessment; ITU-T QKD maturity and gaps; ITU-T’s detailed ETSI inventory; ITU-T’s 2021 ETSI work-item inventory; 2021 work-item listing;…
[9] <https://openqkd.eu/wp-content/uploads/2021/03/OPENQKD_CurrentStandardisationLandscapeAndExistingGapsInTheAreaOfQuantumKeyDistribution.pdf> OPENQKD’s document taxonomy; OPENQKD’s organizational account; OPENQKD’s ETSI publication tables; OPENQKD’s interface analysis; OPENQKD’s implementation-securi…
[10] <https://standards.ieee.org/about/sasb/sba/dec2022/> IEEE’s December 2022 authorization record; December 2022 committee allocations; December 2022 Standards Board record; December 2022 modified PAR; P3120.1 autho…
[11] <https://portal.etsi.org/TB-SiteMap/QKD/QKD-ToR> ETSI ISG QKD terms of reference
[12] <https://portal.etsi.org/webapp/WorkProgram/Frame_WorkItemList.asp?SearchPage=TRUE&includeNonActiveTB=FALSE&qCURRENT_STATE_CODE=&qETSI_NUMBER=&qETSI_STANDARD_TYPE=&qINCLUDE_SUB_TB=True&qSCOPE=&qSTA=&qSTOP_FLG=N&qTB_ID=856%3BCYBER+QSC> ETSI’s historical QSC work programme; ETSI QSC publication records
[13] <https://share.ansi.org/Shared%20Documents/News%20and%20Publications/Links%20Within%20Stories/Draft%20ISO%20TSP%20for%20a%20new%20ISO-IEC%20JTC%20on%20Quantum%20Technologies.pdf> 2022 document inventory; 2022 draft inventory; 2022 Recommendation inventory; 2022 development inventory
[14] <https://portal.etsi.org/webapp/WorkProgram/Report_WorkItem.asp?WKI_ID=43812> GS QKD 012 historical record
[15] <https://portal.etsi.org/webapp/workprogram/Report_WorkItem.asp?WKI_ID=54395> GS QKD 004 historical record; GS QKD 004 scope; ETSI application-interface scope
[16] <https://www.etsi.org/deliver/etsi_gs/QKD/001_099/018/01.01.01_60/gs_qkd018v010101p.pdf> Official GS QKD 018; GS QKD 018 architecture and scope
[17] <https://docbox.etsi.org/ISG/QKD/Open/GS-QKD-016-PP-DRAFT_ETSI_v0-6-2.pdf> Dated QKD 016 working draft
[18] <https://docbox.etsi.org/ISG/QKD/Open/?sortby=name> ETSI’s open drafting directory
[19] <https://www.etsi.org/deliver/etsi_tr/103600_103699/103619/01.01.01_60/tr_103619v010101p.pdf> TR 103 619 migration framework; ETSI migration framework
[20] <https://www.etsi.org/newsroom/news/1981-2021-10-etsi-releases-two-technical-reports-to-support-us-nist-standards-for-post-quantum-cryptography/> ETSI’s 2021 report announcement
[21] <https://www.itu.int/itu-t/recommendations/rec.aspx?rec=13990> Official Y.3800 record; Y-series Supplement record; Y.3800’s deployment purpose
[22] <https://www.itu.int/ITU-T/recommendations/rec.aspx?id=14866&lang=en> Y.3809 approval and scope; Y.3809’s role model
[23] <https://www.itu.int/ITU-T/workprog/wp_item.aspx?isn=18145> Y.3810 approval record; September 2022 approval; Y.3810’s interworking functions
[24] <https://www.ietf.org/lib/dt/documents/LIAISON/liaison-2023-01-24-itu-t-sg-13-opsawg-ls-on-work-progress-on-quantum-key-distribution-qkd-network-in-sg13-as-of-november-2022-attachment-15.pdf> Y.3812 dated Recommendation; Y.3812 requirements and scope; Y.3812’s informative use cases; Y.3812 scope
[25] <https://www.itu.int/dms_pub/itu-t/opb/fg/T-FG-QIT4N-2021-D2.2-PDF-E.pdf> FG-QIT4N D2.2
[26] <https://www.itu.int/en/ITU-T/focusgroups/qit4n/Documents/D2.3%20part%201.pdf> FG-QIT4N D2.3, quantum layer
[27] <https://www4.itu.int/md/meetingdoc.asp?lang=fr&parent=T22-SG13-220704-TD-PLEN-0037> July 2022 consent record
[28] <https://www.itu.int/md/T22-SG13-221125-TD-WP3-0151> Roadmap draft record
[29] <https://www.itu.int/md/T22-SG13-221125-TD-WP3-0148/en> Future-network report draft
[30] <https://www.itu.int/md/T22-TSAG-221212-TD-GEN-0167/_page.print> TSAG’s December 2022 liaison; December 2022 JCA-QKDN liaison
[31] <https://www.iec.ch/system/files/2023-04/quantumslidesv2_0.pdf> Historical establishment and renaming timeline; Project descriptions and historical start dates; SC 27’s quantum-related programme; Historical project descript…
[32] <https://committee.iso.org/files/live/sites/jtc1sc27/files/resources/sc27-sd11-sc-27-structure-members-and-work-programme-data.pdf> SC 27’s July 2022 structure
[33] <https://itscj.ipsj.or.jp/committee-activities/report/J1wg14-2021.html> Committee account of the 4879 ballot
[34] <https://www.iso.org/standard/85203.html> ISO’s dated lifecycle milestones
[35] <https://itscj.ipsj.or.jp/committee-activities/report/J1wg14-2022.html> 2022 committee report; National committee account
[36] <https://standards.ieee.org/ieee/7130/10680/> P7130 project record; P7130’s purpose and authorization
[37] <https://sagroups.ieee.org/7131/> QCB-WG description
[38] <https://sagroups.ieee.org/3155/wp-content/uploads/sites/521/2022/05/P3155-1.pdf> P3155 project authorization; Related-project committee records; P3155 authorization and targets; P3155 scope and related-project comparison; P3155’s comparison…
[39] <https://standards.ieee.org/ieee/1943/10957/> P1943 committee and working group; P1943 project record; P1943’s technical scope
[40] <https://www.ieee802.org/1/files/public/docs2022/new-attia-p1943-draft-PAR-post-quantum-security-0522-v02.pdf> March 2022 submitted PAR
[41] <https://standards.ieee.org/about/sasb/sba/jun2022/> June 2022 approval
[42] <https://sagroups.ieee.org/3155/wp-content/uploads/sites/521/2022/06/P3155-WG-Kickoff-Mtg-Draft-Agenda-06172022.pdf> June 2022 kickoff agenda
[43] <https://sagroups.ieee.org/7131/qcb-wg-qgl-10may22/> QCB-WG’s May 2022 minutes
[44] <https://datatracker.ietf.org/group/qirg/history/> QIRG’s group history
[45] <https://datatracker.ietf.org/doc/charter-irtf-qirg/> Approved QIRG charter; QIRG’s chartered scope; QIRG’s engineering and coordination mandate; QIRG’s routing and resource-allocation problems; QIRG connection se…
[46] <https://datatracker.ietf.org/meeting/113/materials/minutes-113-qirg-00> March 2022 QIRG minutes
[47] <https://datatracker.ietf.org/doc/draft-irtf-qirg-quantum-internet-use-cases/14/> Status statement in the December 2022 draft; Application draft, revision 14; December 2022 draft metadata and text; QIRG application taxonomy; QIRG’s sensing a…
[48] <https://datatracker.ietf.org/doc/draft-irtf-qirg-principles/history/> Architecture draft’s dated history
[49] <https://datatracker.ietf.org/doc/html/draft-irtf-qirg-quantum-internet-use-cases-14> QIRG’s QKD application discussion
[50] <https://standict.eu/sites/default/files/20221013_StandICT_QuantumBriefing_Pitwon_v02.pdf> October 2022 assessment of computing readiness; 2022 briefing on quantum interconnect and infrastructure
[51] <https://www.cencenelec.eu/media/CEN-CENELEC/AreasOfWork/CEN-CENELEC_Topics/Quantum%20technologies/Documentation%20and%20Materials/fgqt_q06_standardizationroadmapquantumtechnologies_release1-1.pdf>
[52] <https://openqkd.eu/wp-content/uploads/2021/03/OPENQKD_CurrentStandardisationLandscapeAndExistingGapsInTheAreaOfQuantumKeyDistribution.pdf>
[53] <https://www.cencenelec.eu/media/CEN-CENELEC/AreasOfWork/CEN-CENELEC_Topics/Quantum%20technologies/Documentation%20and%20Materials/fgqt_q04_standardizationroadmapquantumtechnologies_release1.pdf>
[54] <https://www.itu.int/en/ITU-T/focusgroups/qit4n/Documents/D2.5.pdf>
[55] <https://www.etsi.org/technologies/next-generation-technologies/>
[56] <https://www.idquantique.com/etsi-makes-progress-on-quantum-safe-security-standards/>
[57] <https://standards.ieee.org/about/sasb/sba/feb2022/>
[58] <https://www.iso.org/committee/45306/x/catalogue/p/1/u/1/w/0/d/0>
[59] <https://www.itu.int/en/ITU-T/focusgroups/qit4n/Pages/ToR.aspx>
[60] <https://cdn.standards.iteh.ai/samples/77309/5eb82ba4c4ba43b6b9824a61b06244f4/ISO-IEC-23837-2.pdf>
[61] <https://www.iso.org/sites/ConsumersStandards/1_standards.html>
[62] <https://standards.iteh.ai/catalog/tc/iso/a56c764a-aab5-4e72-aa3f-69240bd82445/iso-iec-jtc-1?srsltid=AU7gw4W7IChPXLrVVKHqihxevd3_qkXVQmos7z46iBSc1uBgBSBeoQiD>
[63] <https://www4.itu.int/md/meetingdoc.asp?lang=fr&parent=T22-SG13-220704-TD-PLEN-0035>
[64] <https://www.itu.int/rec/recommendation.asp?lang=en&parent=T-REC-Y.3812-202209-I>
[65] <https://www.etsi.org/about/history/>
[66] <https://portal.etsi.org/directives/49_directives_jun_2024.pdf>
[67] <https://www.etsi.org/images/files/WorkProgramme/etsi-work-programme-2020-2021.pdf>
[68] <https://www.itu.int/en/ITU-T/focusgroups/qit4n/Documents/Briefing-D1.4.pdf>
[69] <https://datatracker.ietf.org/doc/minutes-113-qirg/>
[70] <https://www.itu.int/en/ITU-T/studygroups/2022-2024/13/Pages/default.aspx>
[71] <https://standards.ieee.org/faqs/regauth/>
[72] <https://standards.ieee.org/about/policies/opman/sect5/>
[73] <https://kpetrucena.lv/posts/etsi-014-v1-problems/>
[74] <https://www.itu.int/en/ITU-T/about/pages/default.aspx>
[75] <https://www.iec.ch/system/files/2020-03/Frankfurt-Agreement-Webinar-QandA.pdf>
[76] <https://www.itu.int/en/ITU-T/focusgroups/Pages/concluded.aspx>
[77] <https://ieeeusa.org/assets/public-policy/positions/research/QuantumTechnology0625.pdf>
[78] <https://www.etsi.org/technical-groups/qt/>
[79] <https://www.linkedin.com/posts/ieee-sa-ieee-standards-association_ieee7000-standards-ethicaldesign-activity-7417581456639549441-mm4n>
[80] <http://arxiv.org/abs/1802.04900v2>
[81] <https://www.itu.int/en/ITU-T/Workshops-and-Seminars/2023/0724/Documents/Zhangchao.pdf>
[82] <https://www.itu.int/rec/dologin_pub.asp?id=T-REC-Y.Sup98-202511-I%21%21PDF-E&lang=e&type=items>
[83] <https://www.itu.int/md/meetingdoc.asp?lang=en&parent=T17-SG13-200313-TD&question=6%2F13&source=FG+QIT4N>
[84] <https://jtc1info.org/sd-2-history/jtc1-working-groups/wg-15/>
[85] <https://standards.iteh.ai/catalog/tc/iso/c5e007a0-3912-4c77-8e35-c84cf7b61de5/iso-iec-jtc-1-sc-31-wg-2?srsltid=AU7gw4VCsz9zXjiuHpne0qpfe4EjFJWe3kyXXivqq5DoXsqs7YTiikup>
[86] <https://csrc.nist.gov/nissc/1999/proceeding/papers/o24.pdf>
[87] <https://portal.etsi.org/Portals/0/TBpages/QSC/Docs/QSC%20ISG_ToR%20.pdf>
[88] <https://standict.eu/synergies/etsi>
[89] <https://www.standardspluselearning.eu/b-1-1-standardization-organizations>
[90] <https://www.iso.org/files/live/sites/isoorg/files/developing_standards/resources/docs/20221216_Guidelines_for_Implementation_of_the_Common_Patent_Policy.pdf>
[91] <https://unfccc.int/sites/default/files/resource/ITU_ICTs-for-climate-change-adaptation.pdf>
[92] <https://assets.vde-verlag.de/iec-normen/preview-pdf/info_isoiecieee42010%7Bed2.0%7Den.pdf>
[93] <https://2026.ieeeicip.org/general-and-author-policies/>
[94] <https://quantumsecuritydefence.com/insights/qkd-explained/>
[95] <https://www.itu.int/en/ITU-T/studygroups/2022-2024/Pages/default.aspx>
[96] <https://datatracker.ietf.org/meeting/104/session/qirg>
[97] <https://gisc.or.kr/materials/2023/data/file/speaker_gisc/3731313045_gkOPfSTn_3c3546577193b0aa2e76361f8b35d7c735dc73ce.pdf>
[98] <https://datatracker.ietf.org/stream/irtf/>
[99] <https://datatracker.ietf.org/doc/rfc5742/>
[100] <https://www.nist.gov/system/files/nistir_8007-reviewofusparticip_isoiec-2014_0.pdf>
[101] <https://www.govinfo.gov/content/pkg/GOVPUB-C13-1758b67213d23ed7afde26884cfb4953/pdf/GOVPUB-C13-1758b67213d23ed7afde26884cfb4953.pdf>
[102] <https://portal.etsi.org/directives/53_ETSI_directives_sep_2026.pdf>
[103] <https://www.etsi.org/wp-content/uploads/etsi-annual-report_2024.pdf>
[104] <https://standards.ieee.org/about/sasb/sba/feb2018/>
[105] <https://standards.ieee.org/about/sasb/sba/jun2017/>
[106] <https://datatracker.ietf.org/doc/draft-irtf-qirg-quantum-internet-use-cases/13/>
[107] <https://datatracker.ietf.org/doc/draft-irtf-qirg-quantum-internet-use-cases/09/>
[108] <https://standict.eu/standards-repository/etsi-gs-qkd-014-v111>
[109] <https://standards.ieee.org/about/sasb/sba/mar2016/>
[110] <https://sdn.ieee.org/standardization.html>
[111] <https://www.rfc-editor.org/rfc/rfc5743.html>
[112] <https://standards.ieee.org/beyond-standards/quantum-computing-trends-shaping-the-future-and-why-standards-matter/>
[113] <https://standards.ieee.org/ieee/1943/10957/>
[114] <https://www.itu.int/dms_pub/itu-t/opb/fg/T-FG-QIT4N-2021-D1.4-PDF-E.pdf>
[115] <https://www.irtf.org/groups.html>
[116] <https://standict.eu/discussion-groups/quantum-computing/297/quantum-internet-research-group-ietf>
[117] <https://csperkins.org/standards/2020-11-20-IEEE-LATINCOM/latincom2020-perkins.pdf>
[118] <https://openqkd.eu/wp-content/uploads/2021/10/2021-09-28_1005_VicenteMartin_UPM_Overview-of-the-current-standardisation-landscape-on-QT.pdf>
[119] <https://www.ieee.org/>
[120] <https://www.itu.int/ITU-T/workprog/wp_search.aspx?isn_status=-1%2C2%2C5&q=16&sg=13&sp=17>
[121] <https://www.etsi.org/newsroom/press-releases/2140-2022-11-etsi-secures-critical-infrastructures-against-cyber-quantum-attacks-with-new-tetra-algorithms/>
[122] <https://iris.inrim.it/bitstream/11696/80319/1/fgqt_q04_standardizationroadmapquantumtechnologies_release1.pdf>
[123] <https://www.itu.int/en/ITU-T/Workshops-and-Seminars/2021/0323/Pages/default.aspx>
[124] <https://sagroups.ieee.org/3155/wp-content/uploads/sites/521/2022/05/P3155-1.pdf>
[125] <https://www.cencenelec.eu/media/CEN-CENELEC/News/Publications/2022/cen-cenelec_work_programme2022.pdf>
[126] <https://www.etsi.org/deliver/etsi_gs/QKD/001_099/012/01.01.01_60/gs_qkd012v010101p.pdf>
[127] <https://openqkd.eu/wp-content/uploads/2021/10/2021-09-28_1020_MartinWard_TEUR_ETSI-ISG-QKD.pdf>
[128] <https://www.etsi.org/images/files/MediaLibrary/ETSI-Corporate-brochure.pdf>
[129] <https://www.etsi.org/images/files/Brochures/Regulations_governing_use.pdf>
[130] <https://standards.iteh.ai/catalog/standards/etsi/0e4ae9f1-c2de-4a26-a4cf-c8dfc627d25c/etsi-gs-qkd-015-v2-1-1-2022-04>
[131] <https://www.itu.int/md/T22-SG13-220704/sum/en>
[132] <https://www.itu.int/md/T22-SG13-221125-TD-WP3-0084/_page.print>
[133] <http://www.itu.int/rec/recommendation.asp?lang=en&parent=T-REC-Y.3809>
[134] <https://www.itu.int/en/ITU-T/focusgroups/qit4n/Documents/D1.4.pdf>
[135] <https://www.itu.int/net4/ITU-T/lists/sgstructure.aspx?Group=17&Period=17>
[136] <https://www.itu.int/net4/ITU-T/lists/sgstructure.aspx?Group=13&Period=17>
[137] <https://www.itu.int/net4/ITU-T/lists/sgstructure.aspx?Group=13&Period=16>
[138] <https://styleguide.iec.ch/?docs=iec%2Ftypographic%2Ftc-references>
[139] <https://itscj.ipsj.or.jp/committee-activities/report/J1wg14-2021.html>
[140] <https://itscj.ipsj.or.jp/committee-activities/report/J1wg14-2022.html>
[141] <https://jtc1info.org/quantum-information-technology-workshop/>
[142] <https://www.ieee.org/about/corporate/governance/constitution.html>
[143] <https://www.itu.int/en/ITU-T/gsc/22/Documents/GSC-22-S01-007.pdf>
[144] <https://standards.ieee.org/ieee/7130/10680/>
[145] <https://sagroups.ieee.org/7131/qcb-wg-qgl-10may22/>
[146] <https://standards.ieee.org/wp-content/uploads/2022/02/sb-bylaws.pdf>
[147] <https://ieeephotonics.org/education/ieee-photonics-standards/>
[148] <http://site.ieee.org/comsoc-qcit/files/2022/11/Meeting-QCIT-ETC-ICC-2022-V2.pdf>
[149] <https://www.ietf.org/blog/quantum-internet/>
[150] <https://datatracker.ietf.org/group/qirg/documents/>
[151] <https://www.irtf.org/policies/irtf-note-well-2021-05.pdf>
[152] <https://datatracker.ietf.org/doc/charter-irtf-qirg/02/>
[153] <https://datatracker.ietf.org/doc/charter-irtf-qirg/history/>
[154] <https://datatracker.ietf.org/meeting/106/session/qirg>
[155] <https://www.irtf.org/anrw/2022/>
[156] <https://www.itu.int/ITU-T/recommendations/iso.aspx?ser=-1&status=F&type=T&pg_size=100>
[157] <https://en.wikipedia.org/wiki/International_Organization_for_Standardization>
[158] <https://www4.itu.int/dms_pub/itu-t/opb/res/T-RES-T.7-2022-PDF-E.pdf>
[159] <https://www.itu.int/md/T17-TSAG-190923-TD-GEN-0579/en>
[160] <https://portal.etsi.org/Portal_Pub/APNProcPub.asp?ACTION_TYPE_NB=PU&FROM_DD=4&FROM_MM=Apr&FROM_YYYY=2022&REAL_FROM_DD=4&REAL_FROM_MM=Apr&REAL_FROM_YYYY=2022&REAL_TO_DD=10&REAL_TO_MM=Apr&REAL_TO_YYYY=2022>
[161] <https://www.itu.int/md/T17-SG13-190628-TD-WP3-0264>
[162] <http://itu.int/en/ITU-T/wtsa20/presentations/Documents/ITU-T%20SG13%20Chairman%20WTSA20%20Presentation.pdf>
[163] <https://www.itu.int/md/T17-TSAG-220110-TD-GEN-1192/en>
[164] <https://www.itu.int/rec/dologin_pub.asp?id=T-REC-Y.3812-202209-I%21%21PDF-E&lang=e&type=items>
[165] <https://www.ietf.org/lib/dt/documents/LIAISON/liaison-2022-07-26-itu-t-sg-13-opsawg-ls-on-work-progress-on-quantum-key-distribution-qkd-network-in-sg13-as-of-july-2022-attachment-5.pdf>
[166] <https://www.itu.int/net/itu-t/ls/ols.aspx?after=2022-01-10&before=2022-12-21&from=8276>
[167] <https://www.itu.int/en/ITU-T/focusgroups/ai4ee/Documents/T-FG-AI4EE-2022-D.WG1.01-PDF.pdf>
[168] <https://www.etsi.org/deliver/etsi_gs/QKD/001_099/015/02.01.01_60/gs_QKD015v020101p.pdf>
[169] <https://cdn.standards.iteh.ai/samples/59581/0564c65893ad4f50b265b85c350642a8/ETSI-GS-QKD-018-V1-1-1-2022-04-.pdf>
[170] <https://www.etsi.org/deliver/etsi_gs/QKD/001_099/004/02.01.01_60/gs_qkd004v020101p.pdf>
[171] <https://www4.itu.int/dms_pub/itu-t/opb/res/T-RES-T.1-2022-PDF-E.pdf>
[172] <https://www.iecex.com/dmsdocument/4491/>
[173] <https://www.cencenelec.eu/media/Guides/CEN-CLC/cenclcguide30.pdf>
[174] <https://jtc21.eu/>
[175] <https://www.cencenelec.eu/news-events/news/2025/eninthespotlight/2025-10-23-tr-18202-2025/>
[176] <https://www.cisa.gov/resources-tools/resources/product-categories-technologies-use-post-quantum-cryptography-standards>
[177] <https://www.cencenelec.eu/media/Guides/CEN-CLC/cenclcguide12.pdf>
[178] <https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication767.pdf>
[179] <https://boss.cen.eu/reference-material/guidancedoc/pages/jointcenclctcs/>
[180] <https://www.cencenelec.eu/news-events/news/2023/brief-news/2023-03-22-standardization-for-quantum-technologies/>
[181] <https://www.cost.eu/uploads/2021/12/CEN-CENELEC-COST-Academy-training-2021-12-02-1.pdf>
[182] <https://www.cencenelec.eu/media/Guides/CEN-CLC/cenclcguide29.pdf>
[183] <https://www.nist.gov/news-events/news/2024/08/nist-releases-first-3-finalized-post-quantum-encryption-standards>
[184] <https://www.nist.gov/>
[185] <https://csrc.nist.gov/projects/post-quantum-cryptography>
[186] <https://blog.cloudflare.com/nists-first-post-quantum-standards/>
[187] <https://www.nist.gov/about-nist>
[188] <https://www.nist.gov/publications>
[189] <https://standict.eu/quantum-technologies-report>
[190] <https://standict.eu/discussion-groups/quantum-computing/297/first-live-meeting-cencenelec-fgqt-berlin-3-5-nov-2021>
[191] <https://cencenelec.eu/media/CEN-CENELEC/AreasOfWork/CEN-CENELEC_Topics/Quantum>
[192] <https://www.cencenelec.eu/media/CEN-CENELEC/AreasOfWork/CEN-CENELEC_Topics/Quantum%20technologies/Documentation%20and%20Materials/fgqt_q03_towardsstandardizationforquantumtechnologies.pdf>
[193] <https://webstore.iec.ch/en/publication/71610>
[194] <https://www.commerce.gov/opog/directives/DOO_30-2B>
[195] <https://www.nist.gov/system/files/documents/2018/10/15/1._walter_copan_nist_update_and_agenda_review_v2.pdf>
[196] <https://csrc.nist.gov/Pubs/ir/8413/upd1/Final>
[197] <https://www.nist.gov/publications/expanding-role-national-metrology-institutes-quantum-era>
[198] <https://www.nist.gov/speech-testimony/quantum-economic-development-consortium-qed-c>
[199] <https://www.nist.gov/publications/status-report-third-round-nist-post-quantum-cryptography-standardization-process-0>
[200] <https://www.nist.gov/pml/quantum-measurement>
[201] <https://nist.gov/publications/future-quantum-based-measurements-and-si>
[202] <https://www.nist.gov/publications/optimal-and-secure-measurement-protocols-quantum-sensor-networks>
[203] <https://www.nist.gov/pml/owm/about-owm/owm-responsibilities-and-authorities>
[204] <https://www.cencenelec.eu/?par=>
[205] <https://www.itu.int/hub/2021/03/standards-bodies-to-coordinate-contributions-to-quantum-information-technology/>
[206] <https://standards.ieee.org/initiatives/quantum-standards-activities/>
[207] <https://portail-qualite.public.lu/content/dam/qualite/publications/normalisation/2023/report-technical-standardization-quantum-technologies-november-2023.pdf>
[208] <https://interoperable-europe.ec.europa.eu/collection/rolling-plan-ict-standardisation/quantum-technologies-rp-2026>
[209] <https://quantumsecuritydefence.com/insights/etsi-quantum-safe-cryptography-standards-europe/>
[210] <https://www.nsa.gov/Cybersecurity/Quantum-Key-Distribution-QKD-and-Quantum-Cryptography-QC/>
[211] <https://datatracker.ietf.org/doc/draft-irtf-qirg-quantum-internet-use-cases/16/>
[212] <https://www.iec.ch/system/files/2023-04/quantumslidesv2_0.pdf>
[213] <http://joint-research-centre.ec.europa.eu/document/download/dddc3c31-969c-44a3-ab61-27d8aff34097_en>
[214] <https://www.itu.int/rec/dologin_pub.asp?id=T-REC-Y.3810-202209-S%21%21PDF-E&lang=e&type=items>
[215] <https://www.itu.int/rec/dologin_pub.asp?id=T-REC-Y.3813-202301-S%21%21PDF-E&lang=e&type=items>
[216] <https://www.ietf.org/archive/id/draft-irtf-qirg-quantum-internet-use-cases-14.html>
[217] <https://datatracker.ietf.org/doc/draft-irtf-qirg-principles/history/>
[218] <https://datatracker.ietf.org/doc/html/draft-irtf-qirg-principles-11>
[219] <https://standards.iteh.ai/catalog/standards/etsi/0e4ae9f1-c2de-4a26-a4cf-c8dfc627d25c/etsi-gs-qkd-015-v2-1-1-2022-04?srsltid=AU7gw4WN5NlloYclOmaR96WY-qN2pWAKnZNbkYBq9uT8vClutYAchHUI>
[220] <https://iec.ch/academy/webinars/quantum-information-technology-standardization-isoiec-jtc-1-workshop>
[221] <https://portal.etsi.org/webapp/WorkProgram/Report_WorkItem.asp?WKI_ID=29096>
[222] <https://portal.etsi.org/webapp/WorkProgram/Report_WorkItem.asp?WKI_ID=54441>
[223] <https://www.bipm.org/documents/20126/218156972/CCU-24-05_a++IEC+Report+to+the+CCU/5a6b8cfa-f2b7-9326-1a32-d9f6f77c3240>
[224] <https://portal.etsi.org/webapp/WorkProgram/Report_WorkItem.asp?WKI_ID=67987>
[225] <https://isrsm.gov.mk/en/project/show/iso:proj:85340>
[226] <https://share.ansi.org/Shared%20Documents/News%20and%20Publications/Links%20Within%20Stories/Draft%20ISO%20TSP%20for%20a%20new%20ISO-IEC%20JTC%20on%20Quantum%20Technologies.pdf>
[227] <https://www.cencenelec.eu/european-standardization/>
[228] <https://www.itu.int/ITU-T/studygroups/com17/sg17-q3.html>
[229] <https://www.itu.int/en/ITU-T/publications/pages/default.aspx>
[230] <https://sagroups.ieee.org/7131/qgl/>
[231] <https://datatracker.ietf.org/group/qirg/about/>
[232] <https://www.irtf.org/t2trg.html>
[233] <https://portal.etsi.org/webapp/WorkProgram/Report_WorkItem.asp?WKI_ID=50943>
[234] <https://portal.etsi.org/webapp/WorkProgram/Report_WorkItem.asp?WKI_ID=58004>
[235] <https://portal.etsi.org/webapp/WorkProgram/Report_WorkItem.asp?WKI_ID=58005>
[236] <https://www.etsi.org/newsroom/news/947-2015-03-news-etsi-launches-quantum-safe-cryptography-specification-group/>
[237] <https://www.itu.int/md/T22-SG13-221125-TD-WP3-0087/en>
[238] <https://www.itu.int/md/meetingdoc.asp?lang=en&parent=T22-SG13-220704-TD-WP1&question=Q6%2F13>
[239] <https://openqkd.eu/wp-content/uploads/2021/10/2021-09-28_1030_HelmutGriesser_QKD-related-work-at-ITU-T.pdf>
[240] <https://www.ietf.org/about/groups/>
[241] <https://www.nist.gov/publications/measurement-challenges-scaling-superconductor-based-quantum-computers>
[242] <https://www.itu.int/en/ITU-T/webinars/20210428/Documents/Bernard%20Lee.pdf?csf=1&e=tQTbja>
[243] <https://jtc1info.org/wp-content/uploads/2022/11/Consolidated-JTC-1-Supplement-2022.pdf>
[244] <https://jtc1info.org/sd-2-history/jtc1-working-groups/wg-14/>
[245] <https://www.etsi.org/images/files/AnnualReports/etsi-annual-report-2024.pdf>
[246] <https://standards.ieee.org/industry-connections/activities/standardization-roadmap-on-quantum-applications/>
[247] <https://jtc1info.org/>
[248] <https://www.itu.int/md/T22-TSAG-221212-TD-GEN-0167/_page.print>
[249] <https://www.etsi.org/images/files/ETSIWhitePapers/ETSI-WP-63-Standards_in_support_of_Europes_Digital_Infrastructure_Needs_.pdf>
[250] <https://standards.ieee.org/wp-content/uploads/2022/01/govt-engagement-global-development.pdf>
[251] <https://www.cencenelec.eu/bottom-navigation-pages/faqs/>
[252] <https://standards.iteh.ai/catalog/standards/clc/d3dfba4a-800c-41fa-8a48-01b9341742f8/en-iec-61788-22-3-2022?srsltid=AU7gw4V4EH7Tm7GcepKjv-Fzl5qSteZVvVL0N-quQa2UpoirZH-wjMQP>
[253] <https://standards.iteh.ai/catalog/standards/etsi/29b26231-0ebd-4f06-ae8d-3b073e803375/etsi-gs-qkd-018-v1-1-1-2022-04>
[254] <https://researchonline.ljmu.ac.uk/15809/1/ITU-K%20conference-2021.pdf>
[255] <https://journals.riverpublishers.com/index.php/QI/article/view/31891>
[256] <https://www.itu.int/en/ITU-T/focusgroups/qit4n/Documents/D1.1.pdf>
[257] <https://www.itu.int/epublications/publication/four-year-report-on-the-implementation-of-the-strategic-plan-and-the-activities-of-the-union>
[258] <https://www.itu.int/ITU-T/workprog/wp_item.aspx?isn=14750>
[259] <https://www.itu.int/en/ITU-T/Workshops-and-Seminars/2019060507/Documents/Presentation_Hongsong%20Shi_QKD_in_ISO-V5.pdf>
[260] <https://development.standards.ieee.org/myproject/Public/mytools/draft/styleman.pdf>
[261] <https://www.itu.int/en/ITU-T/Workshops-and-Seminars/2022/1108/Documents/ISO%20IEC%20JTC%201%20SC27%20-%20Hongsong%20Shi.pdf>
[262] <https://www.iso.org/organization/70.html>
[263] <https://jtc1info.org/wp-content/uploads/2021/12/JTC-1-Strategic-Business-Plan-November-2021_Final.pdf>
[264] <https://standards.ieee.org/about/sasb/sba/sep2022/>
[265] <https://www.ieee802.org/1/files/public/docs2022/new-attia-p1943-draft-PAR-post-quantum-security-0522-v02.pdf>
[266] <https://www.ietf.org/archive/id/draft-irtf-qirg-principles-11.html>
[267] <https://datatracker.ietf.org/doc/draft-irtf-qirg-principles/11/>
[268] <https://www.cencenelec.eu/about-cenelec/structure-and-governance>
[269] <https://nvlpubs.nist.gov/nistpubs/ir/2022/NIST.IR.8413.pdf>
[270] <https://www.etsi.org/technical-groups/qkd/>
[271] <https://www.etsi.org/newsroom/news/1981-2021-10-etsi-releases-two-technical-reports-to-support-us-nist-standards-for-post-quantum-cryptography/>
[272] <https://www.etsi.org/images/files/AnnualReports/etsi-annual-report-2023.pdf>
[273] <https://www.etsi.org/deliver/etsi_gs/QKD/001_099/015/02.01.01_60/gs_qkd015v020101p.pdf>
[274] <https://www.itu.int/en/ITU-T/Workshops-and-Seminars/2022/1108/Documents/ID%20Quantique%20-%20Thomas%20L%C3%A4nger%2C%20Florian%20Fr%C3%B6wis.pdf>
[275] <https://standict.eu/discussion-groups/quantum-computing/297/qkd-security-certification-current-state-and-outlook>
[276] <https://portal.etsi.org/TB-SiteMap/CYBER/CYBER-QSC-ToR>
[277] <https://standict.eu/sites/default/files/20221013_StandICT_QuantumBriefing_Pitwon_v02.pdf>
[278] <https://iebrain.com/wp-content/uploads/Whitepaper-Quantum_Standards.pdf>
[279] <https://joint-research-centre.ec.europa.eu/system/files/2019-03/standards4quantum-workshop-agenda-psis.pdf>
[280] <https://doi.org/10.47120/npl.tqe19>
[281] <https://www.iso.org/es/contents/data/standard/07/70/77097.html>
[282] <http://www.itu.int/en/ITU-T/focusgroups/qit4n/Documents/Briefing%20session%20on%20FG-QIT4N%20deliverables%20to%20SG17.pdf>
[283] <https://www.iso.org/files/live/sites/isoorg/files/archive/pdf/en/statutes.pdf>
[284] <https://www.iso.org/cms/%20render/live/en/sites/isoorg/contents/data/committee/10/13/10138914.html>
[285] <https://www.ntt-review.jp/archive/ntttechnical.php?contents=ntr202310gls_s.html>
[286] <https://www.itic.org/dotAsset/7f95ae51-96f4-484c-ba20-cf6841de18f8.pdf>
[287] <https://ansi.org/iso/ansi-activities/iso-iec-jtc-1-information-technology>
[288] <https://openqkd.eu/wp-content/uploads/2021/10/2021-09-28_1040_MariusLoffler_DIN_Standardization-at-CEN-CLC.pdf>
[289] <https://www.iso.org/files/live/sites/isoorg/files/developing_standards/who_develops_standards/docs/JTC%201%20Strategic%20Business%20Plan%20November%202020.pdf>
[290] <https://journals.riverpublishers.com/index.php/QI/article/download/31891/23175?inline=1>
[291] <https://www.irtf.org/>
[292] <https://interoperable-europe.ec.europa.eu/collection/rolling-plan-ict-standardisation/quantum-technologies-rp2025>
[293] <https://www.itu.int/ITU-T/workprog/wp_search.aspx?isn_task=18145>
[294] <https://datatracker.ietf.org/liaison/1810/>
[295] <https://www.standict.eu/sites/default/files/IEEE-SA-&-standict.eu_2022-10-13.pdf>
[296] <https://www.nist.gov/quantum-information-science>
[297] <https://datatracker.ietf.org/doc/charter-irtf-qirg/00-02/>
[298] <https://portal.etsi.org/directives/45_directives_jun_2022.pdf>
[299] <https://www.itu.int/net/itu-t/ls/ols.aspx?after=2019-05-03&before=2020-03-31&from=-1&to=3927>
[300] <https://standict.eu/discussion-groups/quantum-computing/297/first-two-publications-cencenlec-fgqt-online>
[301] <https://www.itu.int/rec/dologin_pub.asp?id=T-REC-Y.3811-202209-I%21%21PDF-E&lang=e&type=items>
[302] <https://datatracker.ietf.org/doc/html/rfc9340>
