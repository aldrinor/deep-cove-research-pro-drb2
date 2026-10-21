# Low-Code Development Platforms: A Business Evaluation Through Early 2025

**No universal platform winner:** OutSystems and Mendix are strong candidates for broad enterprise application portfolios; Microsoft Power Apps fits Microsoft-centered workflows; UI Bakery and Retool favor developer-led internal tools; Huawei AppCube emphasizes reusable industry applications; and AppMaster differentiates through generated application code. The clearest adoption results include Mercedes-Benz Financial Services Portugal reducing complaints-handling work from three to one full-time equivalent, and MDEC delivering a grant application in seven days against a 100-day plan. Those results support low-code’s practical value, but integration, customization, security, performance, skills, and lifetime cost determine whether faster development produces a durable business benefit. [1][2]

| Business question | Key result | Decision implication |
|---|---|---|
| Which platform fits? | Seven products span enterprise suites, Microsoft workflows, internal tools, industry assets, and generated-code development | Select by application and operating model, not a universal ranking |
| What impacts are demonstrated? | New Oriental: one builder, two weeks; Mercedes-Benz: 3→1 FTE; MDEC: 100 planned→7 actual days; MassHousing: estimated 18 months→12 weeks | Separate delivery speed, operating capacity, and cash savings |
| What makes production use difficult? | Customization, compatibility, security, usability, performance, and lifecycle control | Evaluate the production system, not just the visual builder |

**How the report resolves this:** Part 1 compares the seven requested platforms and explains the choices their differences imply. Part 2 develops the four organizational cases, including calculations that distinguish staffing, effort, elapsed time, and financial value. Part 3 identifies the technical and operational conditions for serious commercial and industrial deployment. The reference period is early 2025, interpreted here as the first quarter of 2025.

## Part 1: Detailed Comparison of Major Low-Code Platforms

**Start with application fit:** The central distinction is what each platform helps your organization deliver: a complete enterprise application, a Microsoft-connected business process, an interface over existing operational data, an industry-specific application, or generated software that can run on your infrastructure. The following comparison uses the requested fields; the discussion afterward explains their practical consequences.

| Platform | Core Features | Target Domain(s) | Advantages | Limitations |
|---|---|---|---|---|
| OutSystems | Visual full-stack web/mobile development; AI assistance; 400+ system/database connections; C# extensions; lifecycle tooling. [3] | Enterprise applications, customer portals, operational systems, legacy modernization, customized ERP/CRM functions | Broad integration and governance; professional-developer productivity; cloud, on-premises, and hybrid options | High cost and learning requirements; complex customization needs specialists; reported deployment friction. [4] |
| Mendix | Visual data models and microflows; web/native mobile/PWA development; AI assistance; Java/JavaScript extensions; testing and governance. [5] | Cross-department business systems, manufacturing, logistics, portals, internal applications | Business–IT collaboration; reusable components; multichannel delivery; flexible hosting | Technical learning curve; bespoke interfaces require expertise; complex workloads need architecture and performance assessment. [6] |
| Microsoft Power Apps | Canvas/model-driven apps; data platform and connectors; templates; workflow integration; AI-assisted capabilities. [7] | Microsoft-centered finance, HR, sales, operations, frontline work, departmental workflows | Strong Microsoft integration; accessible business participation; rapid process digitization; professional extension options | Large-data and bespoke-logic constraints; premium licensing; editor-dependent collaboration; governance requirements. [8] |
| UI Bakery | Responsive component builder; SQL/NoSQL/API connectors; SQL, JavaScript, and Python logic; access roles and audit logs. [9] | Internal operational tools, dashboards, administration, data-management interfaces | Fast interface development over existing data; custom components; cloud or self-hosting | Reported loading, user/row, and publishing restrictions; advanced work needs coding; self-hosting adds configuration. [10][11] |
| Huawei AppCube | Model-driven pages/data; visual service/process/event orchestration; scripts, triggers, APIs, connectors, reusable industry assets. [12] | Office/HR/project applications; campuses, cities, energy, education, transportation; dashboards | Industry-template reuse; multidevice delivery; configurable permissions; integration and custom-widget options | Tenant-specific execution quotas; Chrome-oriented development; private-hosting support requires edition-specific agreement. [13] |
| AppMaster | Generates backend, web, and native-mobile code; visual models/processes; APIs; Go/Docker backend deployment. [14] | Operations, support, sales, IT systems; business-logic-heavy web/mobile applications | Generated software and deployment flexibility; native-mobile frameworks; source access on qualifying plans | Export rights depend on subscription; unusual integrations/compliance need engineering; customer-facing solutions may need additional tools. [15] |
| Retool | Developer-first component builder; database/API connections; JavaScript; workflows; release management; self-hosting and enterprise controls. [16] | Admin panels, support tools, operational dashboards, database interfaces, B2B/client portals | Rapid data-intensive internal tools; code extensibility; reusable connections; enterprise identity and deployment controls | JavaScript/SQL skills; debugging and editor-performance concerns; advanced-control costs; closed-source platform dependence; narrower mobile capability. [4] |

### What low-code changes—and what it leaves intact

**Less hand-coding, broader participation:** Low-code uses visual models, reusable components, connectors, and configuration to reduce the amount of software written manually. Microsoft’s explanation explicitly includes both professional developers and “citizen developers”—business employees who contribute applications without being full-time software specialists. It also emphasizes that these builders still need to understand the application’s purpose, workflows, and integrations. [17]

**Business processes are the natural center:** Mikko Saarinen’s April 2024 Tampere University thesis, drawing on Pinho and colleagues’ literature review, identifies business-process and database-management applications as common low-code outputs, followed by interfaces, web applications, and mobile applications. This is an important commercial distinction: much of low-code’s value lies in handling requests, records, approvals, cases, and operational exceptions more effectively—not in replacing every category of software engineering. [8]

**No-code is a narrower promise:** No-code aims to let users configure applications without writing code; low-code retains extension points for developers. The distinction is useful, but product labels overlap. AppMaster, for example, markets a no-code building experience while generating conventional application source code, whereas Retool is explicitly developer-oriented despite fitting the broader visual-development category. The decisive procurement question is therefore what you can customize, operate, and export—not which marketing label appears on the homepage. [17][14][16]

**Acceleration shifts the bottleneck:** Reusing an authentication component, a table, a connector, or a deployment pipeline removes repetitive construction work. It does not settle ambiguous business rules, determine the right data model, or prove that an application behaves safely under failure. Saarinen’s research identifies precisely this operational effect: when professional low-code development becomes faster, requirements engineering and testing need more resources to keep up. [8]

**The alternative is not always scratch-building:** Conventional development can also reuse frameworks, libraries, and existing services. A fair business comparison therefore places low-code against your realistic delivery alternative, including existing assets and team experience. Low-code is most attractive when it removes substantial repeated work while preserving the controls and customization the application actually needs; its advantage narrows when workarounds dominate. [8]

### OutSystems and Mendix: broad enterprise delivery

**OutSystems favors professional development:** OutSystems is best understood as a way to make technical teams deliver complete business applications faster. Its visual environment covers interfaces, data models, business logic, APIs, workflows, and deployment, with extensions through frontend technologies and C# backend code. Net Solutions describes more than 400 system and database connections and positions the platform for enterprise web/mobile applications, portals, and core-system development. [3]

**Breadth supports application portfolios:** The practical advantage is not simply assembling screens quickly. A company modernizing several connected processes can reuse integration services, identity patterns, business components, and lifecycle tooling across applications. That makes OutSystems a credible shortlist candidate when the organization needs customer portals, internal operations, mobile experiences, and legacy extensions within a coordinated delivery approach. Its integration guidance explicitly distinguishes prebuilt API connections, data-transformation tools, and custom adapters for more difficult legacy systems. [18]

**Enterprise capability carries an entry cost:** Net Solutions identifies cost and learning requirements as major barriers, describes OutSystems as technical rather than citizen-developer-first, and notes a two-week developer course. Its guide gives an indicative paid starting price of US$1,513-plus per month after a free offering supporting one application and up to 100 end users. These figures illustrate the commercial step from experimentation to enterprise use; they are not a complete production budget. [3]

**Complexity still demands specialists:** Appsmith’s platform assessment reports deployment delays, the absence of hot reload for immediate change checking, and a need for substantial expertise in complicated customization. Those are reported experiences, not a universal deployment benchmark. Their business significance is nevertheless clear: faster routine development does not make architecture, dependency management, plugin selection, or difficult debugging disappear. [4]

**Mendix emphasizes collaborative modeling:** Mendix combines visual data modeling, reusable interface components, and microflows—graphical sequences expressing application logic—with Java and JavaScript extension mechanisms. Pretius’s August 2024 overview describes native mobile, responsive web, progressive web applications, and complex internal systems. It also explains that Mendix 10 brought the former Studio and Studio Pro approaches into a unified development environment for different skill levels. [5]

**Collaboration is commercially consequential:** Mendix’s visual approach can let business specialists review behavior while developers handle data relationships, integrations, and exceptions. The resulting advantage is earlier correction of misunderstood requirements, rather than simply fewer lines of code. Its support for reusable components, testing integrations, governance, and deployment across public, private, hybrid, and on-premises environments makes it relevant to organizations building a continuing application portfolio. [5]

**Industrial ecosystem fit can matter:** Capgemini’s September 2023 industrial IT/OT report identifies Mendix’s compatibility with the Siemens environment, including Teamcenter, Opcenter, and Mindsphere, alongside connections to other enterprise platforms. For a manufacturer already operating within that ecosystem, this can be more important than a general claim about ease of use. The relevant benefit is reduced friction connecting engineering, manufacturing, and business information—not an assumption that every industrial application becomes a simple configuration exercise. [19]

**Visual development has a learning curve:** Third-party assessments report that Mendix interface customization and advanced widgets require technical knowledge. Okoone also argues that large, intricate applications may be less efficient to implement or optimize than with conventional coding. These concerns justify workload-specific assessment, but do not establish a single application-size ceiling: difficulty depends on the data model, custom logic, integration architecture, and team expertise. [4][6]

**Choose between them by context:** OutSystems is especially compelling where professional teams want an integrated full-stack delivery environment and expect substantial custom enterprise development. Mendix is especially compelling where visual collaboration, multichannel applications, and relevant industrial ecosystem connections are important. Both require experienced engineering for demanding systems; neither should be selected on an assumption that business users can independently build and operate any application.

**The decision boundary is practical:** Prefer the platform whose extension model, connectors, deployment edition, and available skills fit your hardest representative workflow. That judgment changes if the apparent integration advantage requires extensive custom adapters, the required hosting model is commercially impractical, or the application’s performance depends on controls the platform does not expose.

### Microsoft Power Apps: strongest within a Microsoft-centered estate

**Microsoft integration is the main advantage:** Power Apps is a particularly natural candidate when employees already work with Microsoft 365, SharePoint, Dynamics 365, and Azure. Its canvas applications allow visually arranged interfaces, while model-driven applications organize experiences around data and business processes. Forrester’s July 2024 study describes Power Apps as a suite of applications, services, connectors, and a data platform supporting custom business applications and connections to online and on-premises data. [7]

**Related products expand the solution:** Power Automate provides workflow automation around applications; Power Pages addresses website and portal scenarios; analytics and AI capabilities sit within the broader Power Platform ecosystem. These relationships make the ecosystem attractive, but they also mean the proposed solution may involve several products, entitlements, and operating responsibilities. A buyer should distinguish the Power Apps application itself from everything required to deliver the complete process. [20][21]

**Departmental workflows are a strong fit:** Typical candidates include employee requests, inventory records, frontline data collection, approvals, and interfaces that bring information from existing systems into one working process. Appsmith’s overview identifies finance, sales, marketing, HR, operations, and frontline work as target domains. The attraction is greatest when the application can exploit existing organizational identities, familiar data sources, and established Microsoft skills. [4]

**Accessibility does not remove programming:** Saarinen’s 2024 interviews describe Power Apps as approachable for simple data-input and processing applications, but identify complicated business logic and processing chains as harder work. Reported extension routes include Power Automate, Azure Functions, and C#/.NET plugins. The practical lesson is to budget for a blend of business makers and technical support when the process extends beyond straightforward forms and lists. [8]

**Licensing follows the architecture:** Saarinen’s thesis gives an approximately US$20-per-user premium-license reference and explains how premium connectors or more granular data-control needs can change the required license. This creates a recognizable commercial pattern: a simple application can begin cheaply, then become a different proposition when it needs a particular database, connector, or control. The correct comparison is the cost of the intended production architecture, not the cost of the first prototype. [8]

**Data and collaboration need scrutiny:** Appsmith reports difficulties with large data volumes, restricted customization, and simultaneous development. Saarinen’s earlier interviews also describe collaboration restrictions, while noting progress in Power Apps editing capabilities. The defensible conclusion is editor- and application-specific: demonstrate the actual multi-developer workflow, version handling, deployment process, and data access pattern your team will use, rather than treating collaboration as either universally present or universally absent. [4][8]

**Governance can strengthen the case:** Power Apps does not have to mean uncontrolled departmental development. Forrester’s interviewees described controlled environments, training, mandatory architecture/privacy review for sensitive applications, and reduced reliance on unsanctioned tools. For a Microsoft-centered enterprise, that can turn dispersed spreadsheet and ad hoc application development into a more visible organizational capability. [7]

**The resulting fit judgment:** Power Apps is a strong first candidate for Microsoft-connected business processes and supervised citizen development. Broader enterprise suites or conventional services become more attractive when the application depends on unusually complex logic, extensive bespoke interface behavior, difficult data operations, or licensing economics that no longer favor the Microsoft approach.

### UI Bakery and Retool: internal tools over existing data

**Both begin close to operational work:** UI Bakery and Retool are particularly relevant when the business already has databases, APIs, and software services, but staff lack an effective interface for using them together. Their component-and-connector model avoids rebuilding common tables, forms, charts, filters, and action panels. This is a different buying problem from choosing a platform to replace an entire enterprise application estate. [9][16]

**UI Bakery reduces frontend effort:** UI Bakery positions itself for solution architects and data engineers building secure internal applications without learning a full interface framework. Its product description lists SQL, NoSQL, REST API, and third-party-service connectors, along with SQL, Python, and JavaScript for advanced transformations and validation. Its component library and responsive editor support dashboards, administration interfaces, and operational workflows. [9]

**Data proximity is useful:** A technical operations team can connect an existing database, display selected records, add validation, and provide controlled actions without undertaking a complete frontend project. The important gain is that the team can devote more attention to the business action and underlying data. It should still decide which rules belong in the interface, which belong in backend services, and which must be enforced at the data source.

**Hosting choice changes responsibilities:** UI Bakery supports cloud and on-premises deployment. Its self-hosting documentation identifies additional setup for email, Google Sheets, Salesforce, and blob storage used for image uploads. Consequently, self-hosting offers infrastructure control but adds integration and operational work; the “one-click deployment” proposition for application changes should not be mistaken for an entirely configuration-free private installation. [11]

**Its data model needs understanding:** UI Bakery states that, for external databases and services, it acts as a proxy, does not store returned source data, and does not expose sensitive credentials to the browser. Its internal database follows a different storage arrangement. This distinction matters to data-flow and security reviews, because the answer depends on how the application is built and which storage option it uses. [22]

**Distribution and scale affect suitability:** A January 2025 comparison reports concerns about pricing, occasional slow loading, user and data-row restrictions, and publication to major app stores. These are useful acceptance questions for the relevant plan and version. They also reinforce UI Bakery’s principal fit: internal web applications and data interfaces, rather than assuming it is interchangeable with a full native-mobile or highly specialized consumer-product development environment. [10]

**Retool explicitly serves technical builders:** Retool combines prebuilt interfaces with JavaScript, SQL, database connections, API resources, and workflow automation. Bold Tech’s guide calls it developer-first and highlights internal tools, client portals, administration dashboards, and complex data-driven workflows. The platform is therefore attractive when an engineering team wants to stop rebuilding routine operational interfaces while retaining code-based control of business behavior. [16]

**Existing resources become reusable assets:** Retool’s resource model lets developers configure connections and authentication for reuse across applications. A customer-support dashboard can, for example, bring together customer records, product activity, and internal service actions. That makes the platform valuable for organizations with established backend systems whose main bottleneck is delivering usable operational software around them. [16]

**Enterprise controls are substantial but tiered:** Retool offers release management, Git-based source control, self-hosting, permissions, audit logs, separate environments, and custom single sign-on. The guide also explains that requirements for granular permissions or advanced identity controls can move a customer into higher-priced plans. Procurement should therefore price the required control set, not simply a low entry-level seat price. [16]

**Performance depends on application structure:** Retool’s Q1 2025 stable-release announcement reports an average 27% load-time improvement from multipage architecture, which evaluates the current page’s code and components rather than the entire application. The mechanism is instructive even without treating the percentage as a cross-platform benchmark: component scope, query execution, and page organization affect the performance of visually built applications. [23]

**The main trade-off is technical dependence:** Retool’s flexibility assumes comfort with JavaScript and SQL, and reported problems include difficult debugging, slow refreshes, editor lag, and limited customization of some components. Bold Tech also describes the mobile builder as less capable than the web builder and warns that a self-hosted customer still depends on Retool to repair defects in the closed-source platform. [4][16]

**Choose the operating model, not appearances:** UI Bakery merits attention when its interface builder, supported scripting, data connections, and deployment package fit the team’s requirements. Retool merits attention when developers want code-oriented control and a broad operational application environment. For either, a polished demonstration should be followed by a realistic assessment of permissions, query behavior, debugging, deployment, and ongoing cost.

### Huawei AppCube: reusable industry applications with explicit runtime boundaries

**Industry assets distinguish the offering:** Huawei AppCube, the product family described in Huawei’s Astro Zero materials, combines data modeling, page generation, graphical service/process/event orchestration, scripts, configurable triggers, and third-party integration. Its scenarios include office and HR applications, project management, and industry applications for campuses, cities, energy, education, and transportation. [12]

**Reuse can shorten repeated deployments:** Huawei describes reusable business-logic units, custom advanced-page widgets, and an industry-asset library containing more than 100 applications, business objects, and widgets. The commercial attraction is strongest where several projects share similar processes and data structures. A reusable industry application can preserve domain knowledge across deployments instead of repeatedly reconstructing the same behavior. [24]

**Multidevice support broadens reach:** Huawei lists PC, mobile, WeChat applet, H5, and WeLink compatibility, alongside responsive pages and configurable permissions. This can suit organizations needing business applications across several familiar channels. It should nevertheless be evaluated against the exact user journey and distribution method: multidevice access, a mobile-responsive website, and a native application with specialized device behavior are different requirements. [24]

**Runtime quotas are architectural facts:** An AppCube usage guide lists the following execution boundaries. They illustrate why a suitable low-code workflow must respect the tenant’s execution model, especially for lengthy processing, scheduled automation, and database operations. [13]

| Execution context | Guide-listed limit | Practical consequence |
|---|---|---|
| Scheduled-task script | 10-minute timeout | Long work needs decomposition or external execution |
| Scheduled-task volume | 10,000 tasks per day | Scheduling design must respect the daily allowance |
| Paid-tenant REST script call | 3-minute timeout | A synchronous request is unsuitable for longer work |
| Free-tenant scripts | 1 parallel script; 60-second runtime | Trial behavior differs from a larger paid workload |
| OSQL database statement | 60-second timeout | Queries require suitable design and execution time |

**Deployment claims require a precise edition:** Huawei community material describes hybrid-deployment capabilities, while the separate usage guide states that private deployment is unsupported and specifies Chrome for development, sandbox, and runtime environments. These descriptions could concern different product arrangements or versions. For a buyer requiring private hosting, the conservative decision is to make the exact supported edition, region, infrastructure, and operating responsibilities a contractual suitability condition. [25][13]

**Efficiency claims are not performance rankings:** Huawei’s English material claims development acceleration of up to tenfold, while its Chinese material describes a more-than-tenfold efficiency improvement. These are vendor positioning statements rather than a common measurement against the other six products. The stronger selection argument is the fit of reusable industry assets, integration mechanisms, supported channels, and execution boundaries to your intended applications. [24][12]

**The resulting fit judgment:** AppCube is a credible candidate where Huawei-related services, industry templates, reusable business assets, and supported delivery channels align with the organization. That judgment changes when mandatory private hosting, browser requirements, lengthy synchronous processing, or application-specific customization conflict with the selected tenant and edition.

### AppMaster: generated software and deployment control

**Code generation is the differentiator:** AppMaster visually models data, business processes, APIs, backend services, web interfaces, and native-mobile applications, then generates and compiles application code. Its 2023 description identifies Vue 3 for web applications, Kotlin and Jetpack Compose for Android, SwiftUI for iOS, and Go with Docker deployment for backends. [14]

**The target is complete business software:** AppMaster’s stated focus includes internal systems for operations, support, sales, and IT. Its own description distinguishes these from small websites, landing pages, or simple mobile applications without substantial business logic. It also says customer-facing solutions may require additional tools. This helps prevent a common selection mistake: choosing a broad application generator when a simpler website or form service would better match the task. [15]

**Generated code changes the exit discussion:** Application source access can give an organization more options to inspect, host, or continue developing the generated software. However, AppMaster’s 2023 subscription description makes export rights plan-dependent: its Startup plan excluded binary and source export, its Business plan allowed binary export and on-premises hosting, and its Enterprise arrangement included source-code access. Those are distinct levels of control. [14]

**Portability is not automatic maintenance:** Even when source is delivered, the business must be able to build, deploy, secure, and maintain it. A source export is therefore more valuable when the organization has the engineering skills and documentation to operate the resulting application. It also remains important to distinguish continuing the exported application conventionally from preserving the original visual-development experience on another platform.

**Generic risks need product-specific treatment:** AppMaster’s limitations glossary discusses customization, specialized integrations, compliance, scalability, and vendor dependence across low-code platforms. The same article argues that AppMaster’s editable source and full-stack deployment address several of those concerns. Accordingly, those general warnings should become evaluation questions, not be presented as proof that AppMaster itself lacks source access or cannot scale. [26]

**The resulting fit judgment:** AppMaster deserves attention when visual development must produce business-logic-heavy backend, web, and native-mobile software, especially where generated-code access or private deployment is important. The decision turns on the required subscription rights, the quality and maintainability of the generated application, and how unusual requirements interact with the model-driven regeneration process.

### Making the commercial decision

**Shortlist around your hardest requirement:** A feature inventory is useful, but the hardest non-negotiable requirement should shape the shortlist. That may be a particular legacy integration, a highly tailored interface, private hosting, a native-mobile workflow, or production access controls. Capgemini’s industrial guidance similarly emphasizes hosting, connectors, legacy-system compatibility, reusable components, user experience, licensing, mobility, stability, performance, and scalability. [19]

**Existing capability is an economic asset:** An organization with Microsoft identity, data, and administration skills may gain more from Power Apps than a neutral feature checklist suggests. A manufacturer with relevant Siemens systems may find Mendix integration particularly useful. An engineering team with established APIs and SQL databases may obtain faster value from UI Bakery or Retool than from adopting a broader full-stack suite.

**Compare complete operating costs:** License fees, implementation, training, integrations, hosting, support, application maintenance, and eventual migration all belong in the comparison. Saarinen’s research highlights how premium features, per-user charges, storage, developer seats, and support arrangements complicate total-cost estimation. A platform can reduce build effort and still become expensive as users, application counts, or control requirements grow. [8]

**Keep a hybrid option open:** Some applications fit a low-code platform completely; others fit best as low-code interfaces calling conventional backend services. Capgemini also cautions against assuming that low-code should recreate large packaged enterprise systems or replace dedicated advanced analytics platforms. The business objective is to reduce delivery friction while retaining appropriate systems of record and specialized services. [19]

**Part 1 takeaway:** Choose the platform whose application model, integrations, skills, controls, hosting, and lifetime economics fit the business—not the platform with the strongest generic speed claim.

**Additional documented evidence**

| Entity | Core Features | Target Domain(s) | Advantages | Limitations | Core Features | Target Domain(s) | Advantages | Limitations | Core Features | Target Domain(s) | Advantages | Limitations |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| OutSystems | OutSystems provided full-stack visual development for…[198] | OutSystems targeted enterprise-grade application…[202] | no evidence found | High cost; steep learning curve; technical audience[44] | OutSystems provided full-stack visual development for…[198] | OutSystems targeted enterprise-grade application…[202] | no evidence found | High cost; steep learning curve; technical audience[44] | OutSystems provided full-stack visual development for…[198] | OutSystems targeted enterprise-grade application…[202] | no evidence found | High cost; steep learning curve; technical audience[44] |
| Mendix | The study states that Mendix stood out in terms of…[178] | Manufacturing; finance; public sector; retail[211] | 55 apps; 94% on time/on budget; $10m cost avoidance[182] | Citizen-dev complexity; customization/scaling risk[93][226] | The source states that Mendix emphasizes model-driven…[203] | Manufacturing; finance; public sector; retail[211] | 55 apps; 94% on time/on budget; $10m cost avoidance[182] | Citizen-dev complexity; customization/scaling risk[93][226] | The source states that Mendix emphasizes model-driven…[203] | Manufacturing; finance; public sector; retail[211] | 55 apps; 94% on time/on budget; $10m cost avoidance[182] | Citizen-dev complexity; customization/scaling risk[93][226] |
| Microsoft Power Apps | Canvas/model-driven apps, Copilot, Power Fx, ALM [215] | The page says Power Apps is specifically designed for…[152] | The page reports vendor-positioned Power Apps…[152] | The page reports vendor-positioned Power Apps…[152] | Canvas/model-driven apps, Copilot, Power Fx, ALM [215] | Finance, operations, frontline, field service [46] | The page reports vendor-positioned Power Apps…[152] | The page reports vendor-positioned Power Apps…[152] | Canvas/model-driven apps, Copilot, Power Fx, ALM [215] | Finance, operations, frontline, field service [46] | The page reports vendor-positioned Power Apps…[152] | The page reports vendor-positioned Power Apps…[152] |
| UI Bakery | Drag/drop UI, workflows, APIs, Git, AI, self-hosting [151] | Internal tools, portals, dashboards, admin panels [188][134] | Fast iteration; backend connectivity [91] | Integration/docs gaps; performance issues [91] | Drag/drop UI, workflows, APIs, Git, AI, self-hosting [151] | Internal tools, portals, dashboards, admin panels [188][134] | Fast iteration; backend connectivity [91] | Integration/docs gaps; performance issues [91] | Drag/drop UI, workflows, APIs, Git, AI, self-hosting [151] | Internal tools, portals, dashboards, admin panels [188][134] | Fast iteration; backend connectivity [91] | Integration/docs gaps; performance issues [91] |
| Huawei AppCube | Visual low/no-code; data/process orchestration [190] | Industry; parks, cities, energy, education, transport [224] | Fast packaging; cloud integration; collaboration [225] | Runtime-only; 5000 TPS large instance; HTTPS-only APIs [190] | Visual low/no-code; data/process orchestration [190] | Industry; parks, cities, energy, education, transport [224] | Fast packaging; cloud integration; collaboration [225] | Runtime-only; 5000 TPS large instance; HTTPS-only APIs [190] | Visual low/no-code; data/process orchestration [190] | Industry; parks, cities, energy, education, transport [224] | Fast packaging; cloud integration; collaboration [225] | Runtime-only; 5000 TPS large instance; HTTPS-only APIs [190] |
| AppMaster | This page provides product capabilities, examples…[148] | This page provides product capabilities, examples…[148] | This page provides product capabilities, examples…[148] | This page provides product capabilities, examples…[148] | This page provides product capabilities, examples…[148] | This page provides product capabilities, examples…[148] | This page provides product capabilities, examples…[148] | This page provides product capabilities, examples…[148] | This page provides product capabilities, examples…[148] | This page provides product capabilities, examples…[148] | This page provides product capabilities, examples…[148] | This page provides product capabilities, examples…[148] |
| Retool | Retool offers 350+ templates designed for internal…[118] | The page discusses Retool as an Appsmith alternative…[127] | The page discusses Retool as an Appsmith alternative…[127] | The page discusses Retool as an Appsmith alternative…[127] | Retool offers 350+ templates designed for internal…[118] | Internal tools; data, ops, finance, manufacturing[112] | 2-day build; integrations; internal-tool fit[158][155] | Technical skills; cost, latency, portability[116][62] | Retool offers 350+ templates designed for internal…[118] | Internal tools; data, ops, finance, manufacturing[112] | 2-day build; integrations; internal-tool fit[158][155] | Technical skills; cost, latency, portability[116][62] |

Across the rows, OutSystems presents enterprise full-stack and AI development for regulated industries [40][39], Mendix visual model-driven development for industrial and public-sector teams [111][211], Power Apps ecosystem-connected business applications [46][80], UI Bakery developer-focused internal tools [137][134], Huawei AppCube industry/cloud scenarios [224][225], AppMaster generated backend/web/mobile solutions [85][147] and Retool code-friendly internal tools [116][118]. The advantages are speed, reuse, integration or generated artifacts, while limitations center on customization, governance, compatibility, developer dependence and workload validation [102][199][91][146][154].

**Scope, boundary, and evidence status**

**OutSystems: comparison entry**

| Platform | Core Features | Target Domain(s) | Advantages | Limitations |
|---|---|---|---|---|
| **OutSystems** | Visual IDE and business-logic modeling; drag-and-drop components, templates, reusable modules, visual workflows, automatic code generation, full-stack front end/back end/database development, REST and SOAP APIs, web services, connectors, custom code, AI, cloud, DevOps, CI/CD, testing, deployment, monitoring, lifecycle management, web and mobile applications, native-device access, and offline synchronization. [36][40][42][43] | Enterprise and mission-critical applications; internal tools, customer portals, complex enterprise systems, mobile and web applications, web services, kiosks, IoT, legacy modernization, ERP, and cross-channel applications. Cited industry examples include banking and financial services, insurance, government, manufacturing, healthcare, energy and utilities, retail, education, telecommunications, and logistics. Some detailed use-case lists are generic low-code examples rather than OutSystems-specific evidence. [36][40][42][43] | Broad full-stack scope; integration with enterprise data and systems; reusable code and UI; cross-platform delivery; lifecycle, testing, deployment, security, and governance features; claimed speed, scalability, and support for regulated or mission-critical work. Most benefit statements in the supplied material are vendor or secondary claims, not independent comparative measurements. [40][42][43] | Complex legacy or proprietary-system integrations may still require custom development; advanced business logic requires coding expertise; large projects may need performance optimization; proprietary components and version-control practices can create portability and deployment risks; weak governance can create technical debt. Cost, skills, procurement, and implementation burden are reported by a post-cutoff comparison and therefore cannot establish the March 2025 position. [35][40][41][43] |

**Target domain and business fit**

**Customization and user-friendliness**

**Compatibility and integration**

OutSystems is reported to provide more than **400 connectors** and to integrate with REST and SOAP services, SAP, Salesforce CRM, databases, on-premises systems, cloud databases, and other enterprise resources. The connector count is source-stated, but the supplied span does not provide a cutoff date or independent verification. [40] The same source makes the material qualification explicit: older or proprietary legacy systems can remain difficult to integrate and may require custom development, which can lengthen modernization schedules and increase cost. [40]

This is a mechanism rather than a contradiction. Connectors simplify standard interfaces; they do not eliminate undocumented protocols, proprietary data models, unusual authentication, data-quality problems, or bidirectional legacy behavior. The stated mitigation is to analyze the legacy estate before implementation, use available connectors, and consider a hybrid approach in which OutSystems coexists with older systems. [40] The broader low-code evidence likewise warns that old systems and third-party tools may require additional work or unique programming. [36]

**Security, performance, and lifecycle**

The supplied OutSystems material lists authentication, authorization, role-based access control, encryption in transit and at rest, audit logging, data-residency considerations, third-party risk management, automated testing, security checks, and compliance-related controls. It names GDPR, HIPAA, CCPA, ISO/IEC 27001, SOC 2, OWASP, SOX, and PCI DSS as relevant standards or requirements in particular contexts. It also mentions AppShield and Sentry as additional protections against security risks, regulatory fines, and data leaks. These statements are vendor or secondary descriptions of controls; they do not by themselves demonstrate that a particular implementation satisfies a regulation. [40][42]

The later comparison reports additional commercial constraints: minimum commitments and cost may exclude many mid-market teams; certified OutSystems developers may be difficult to find; Application Object pricing may increase with application complexity; and procurement and implementation cycles may be heavy. [35] These are explicitly post-cutoff observations from **5 August 2026**, so they are not evidence of the March 2025 price or skills market. They nevertheless identify the commercial questions a buyer should validate: licensing unit, minimum spend, partner dependence, internal skills, migration costs, and total cost at the expected application portfolio size.

**Additional platform evidence exposed in this source group**

**Microsoft Power Apps.** Power Apps is described as providing point-and-click design, templates, data linkage, web applications compatible with iOS, Android, and Windows, and **200 connectors** for disparate data and systems. [36] Another secondary description lists **200+ connectors** to Microsoft 365, Dynamics 365, Azure, SQL Server, and third-party services; AI Builder capabilities for form processing, object detection, and text classification; and Power Automate workflows triggered by events. [41] Its evidenced focus is custom business applications, enterprise-application modernization, manual-process automation, internal apps, portals, mobile apps, dashboards, and workflow use. [36][41]

**Retool.** Retool is positioned as an internal-tool and developer-experience platform. The supplied secondary description says it builds custom mobile web applications, external applications, database interfaces, and server-side workflows; offers **46+ native integrations**, REST and GraphQL support, and access to **50+ databases and SaaS platforms**; and permits JavaScript customization. It names Descript, FINN, Greenly, Neo4j, and Snowflake as users and says the platform is used from startups to Fortune 500 companies. These are secondary source claims, not independently verified adoption measurements. [41]

**Candidate platforms and the open roster boundary**

**Appian** remains a discovered candidate outside the required seven rows. A page dated **22 October 2024**—inside the provisional cutoff—describes Appian as providing AI automation for important business processes at large organizations and says that customers build AI-powered processes intended to accelerate work, reduce cost, and manage risk. It reports more than **25 years** of process-automation experience and makes vendor claims about power, reliability, and scale. [37] Other secondary material places Appian in BPM, case management, complex process optimization, ERP, CRM, and RPA, and names USDA, Ryder, and the FDA as clients; those statements are not independent outcome verification. [41] Appian also appears beside OutSystems, Mendix, and Power Apps in one secondary comparison, supporting candidate relevance but not changing the requested roster. [42]

A later page describes Appian’s native deployment tools, Jenkins and other DevOps integrations, drag-and-drop construction, native AI services, AI/ML connections through Google Cloud, AWS, and Microsoft Azure, and code-free integration with enterprise data and web services. Because that page was updated **23 February 2026**, it cannot establish Appian’s early-2025 state. [36] The available Appian cards supply no named match to the four requested impact cases, no manpower, time, or cost figures, and no challenge-specific result; those cells remain not established rather than estimated. [38]

**Comparison boundary and evidence status**

For this comparison, a low-code development platform is an application-development environment using visual, declarative, model-driven, or generated components to reduce hand coding while still supporting application construction, integration, deployment, or lifecycle management. Low-code permits code customization or manual integration; no-code relies entirely on graphical builders and prebuilt components. Workflow connectors and RPA-only products may support automation but are not application builders by themselves.[44][55][57] SAP’s extension guidance similarly places low-code tools in application development and process-automation scenarios, while Oracle’s material distinguishes low-code/pro-code customization from no-code process extensions.[58][59]

Evidence labels also matter. A 2018 Huawei Senegal HRM study illustrates primary organizational evidence: approximately **400 questionnaires** were distributed and **318** were retained for analysis using statistical methods including factor analysis, regression, ANOVA, and structural-equation modeling.[45] A February 2025 HUD OIG audit illustrates a different boundary: it separated Authority-supplied documentation from auditors’ inspections and conclusions; inspectors examined **36 units and 29 buildings** in **16 of 38 developments** during April, June, and August 2023, while the Authority’s February 2025 documentation reported mitigation of **102 of 113 unit deficiencies** and **98 of 105 building deficiencies**.[54] These examples define provenance categories; they are not low-code platform evidence.

**Boundary example: New Oriental is not a platform row**

The New Oriental evidence concerns **New Oriental Education & Technology Group**, developed from Beijing New Oriental School, and identifies **Hologres** as the real-time data store, **Flink** for streaming computation, and **MaxCompute** for offline processing.[49] The third-party article, published **3 February 2024** and attributed to New Oriental Internet Technology Center engineer Chen Yulin, reports a group-wide real-time warehouse after **half a year** of construction, but supplies no independent corroboration.[49]

**OutSystems**

**Core Features.** A secondary product description dated **29 January 2025** reports that OutSystems combines visual tools and AI-based automation for web and mobile applications with one IDE covering development, testing, production, and DevOps automation. It includes templates, modules, visual data modeling, APIs, web services, workflows, business rules, vulnerability identification, dependency analysis, and automated deployment; the source reports **more than 400 system and database connections**.[44] Deployment is described across OutSystems Cloud, public cloud, and on-premises environments using Kubernetes, Linux containers, and modern cloud services.[44]

**Target Domain(s).** OutSystems targets professional developers and enterprise application teams rather than exclusively citizen developers. The documented scope includes cloud, on-premises, and hybrid enterprise applications; customer experience, operational efficiency, workplace innovation, legacy modernization, ERP, CRM, logistics, internal and external portals, customer applications, and supply-chain operations.[44] The same January 2025 source reports **more than 435,000 community members in 87 countries**, a reach indicator rather than an independently verified adoption count.[44]

**Limitations.** The January 2025 description characterizes OutSystems as technical rather than citizen-developer oriented and identifies a steep learning curve, including a stated two-week developer training course.[44] Its free tier covers **one application for up to 100 end users**; the source reports paid pricing starting at **$1,513+ per month** after that threshold, although pricing should be rechecked before procurement.[44] A separate secondary comparison says that basic CRUD applications fit the platform’s guardrails, while custom business logic, third-party integrations, meaningful performance tuning, version control, CI/CD, and enterprise-grade content governance require developer expertise or workarounds.[51] Thus, OutSystems illustrates a central field trade-off: low-code can accelerate professional development, but it does not remove integration, performance, deployment, or governance complexity.[51]

**Mendix**

**Limitations and conditions.** The direct Mendix cards establish capabilities more strongly than product-specific defects. Cross-platform research identifies conditions that can constrain Mendix or any LCDP in serious use: complex algorithms and highly tailored functionality may exceed visual abstractions; compatibility requires API support, standard formats, external-system integration, and migration planning; security requires authentication, authorization, role management, multifactor authentication, encryption, logging, and audit trails; and data validation can be overlooked during external integration.[55] Large-scale changes or unsupported integrations may require conventional code or a separate solution, affecting maintainability and system-level optimization.[55] These are **general LCDP risks, not measured Mendix-specific failure rates**, and should be presented with that qualification.

A later MULTIMOORA study reported a Mendix score of **22.2696 points** and a **0.2696** index, but the study was published **24 August 2025** and used a different platform set and later evidence; those values are not an early-2025 ranking.[56] The Mendix evidence shown here also supplies no quantified manpower, time, or cost result for one of the four named cases; the August 2024 partnership is the dated organizational item, and its outcome status is source-reported but unquantified.[53] Mendix illustrates why platform selection should compare several criteria—functionality, user experience, development approach, scalability, collaboration, deployment, and governance—rather than rely on a single “best platform” label.[56]

**Microsoft Power Apps**

**Core Features and target domain.** Microsoft Power Apps combines canvas-style visual construction, Power Fx formulas, Dataverse, Microsoft and third-party connectors, and Power Automate workflows. Its strongest documented target is the Microsoft-centric organization using Microsoft 365, Dynamics 365, Azure, SharePoint, Teams, Excel, or Dataverse; intended builders include business analysts, power users, and developers.[51] A vendor-reported update from **October 2024** described improved data connectivity, a more intuitive interface, and AI features allowing machine-learning models to be used inside applications.[53]

**Advantages and business fit.** Power Apps is attractive when the organization already operates inside the Microsoft ecosystem: the existing identity, data, collaboration, and workflow stack can reduce integration friction.[51] The supplied Gartner Peer Insights page reports **4.4 stars from 469 reviews** and **89% willing to recommend**, but the card provides no observation date and identifies these as individual user opinions rather than statements of fact.[50] The numbers are therefore user-review context, not independently verified performance or ROI.

**Limitations.** Deep Microsoft ecosystem dependence is a conditional strength and a limitation: it is advantageous for a Microsoft-first organization but can add complexity outside that environment.[57] Reviewers also report a steeper learning curve than expected, difficult or limited interface customization, output formats that may not meet advanced business needs, and user experiences that become difficult to maintain in complex applications.[50] The 2025 LCNC inhibitor study additionally identifies lock-in, integration, scalability, testing, and customization as general risks, but its post-31-March evidence cannot be used as a Power Apps-specific early-2025 finding.[60] The cards shown here do not document Power Apps manpower, time, or cost results for the four named cases.

**Retool**

Retool is positioned primarily for developer-friendly internal tools: dashboards, administration panels, and data tools. The supplied descriptions report database and API connectivity, prebuilt tables, forms, charts, buttons, and modals, with JavaScript available for complex logic and custom workflows.[51][57] Its target domain is therefore internal operational software rather than an unrestricted replacement for every customer-facing or core enterprise application. The main advantage is rapid construction of integration-heavy internal tools without removing code-based extensibility; the corresponding limitation is dependence on developer skills and a narrower internal-tool fit.[51]

**AppMaster and the open roster boundary**

AppMaster is a required row, but the supplied Gartner Peer Insights material establishes market identity more clearly than product capability. It places AppMaster.io in the Enterprise Low-Code Application Platforms market and reports **4.2 stars from 3 reviews**; the same page reports **100% willing to recommend**, with **67% five-star** and **33% four-star** reviews.[50] These are page-reported user opinions with a very small denominator and no dated as-of point; Gartner expressly cautions that such opinions are not statements of fact.[50] The supplied cards do not establish a dated-by-cutoff core-feature inventory, target-domain profile, named-case outcome, or independently verified limitation for AppMaster. Those cells should therefore remain explicitly evidence-limited until stronger dated sources are applied.

**Scope and evidence boundary**

Evidence status is separated: the 2024 interoperability study used observations, interviews, archival material and triangulation as primary academic evidence [65]; controlled benchmark research is primary but not low-code evidence [67]; DoD guidance is official [71]; and GAO corroborated interview evidence with documents where available, while noting gaps [74]. A later comparison reports 280+ OutSystems connectors, 700+ Power Apps connectors, approximately $36,000/year and $1,000/month entry prices, and a roughly five-user Retool free tier; published after the cutoff, these figures do not establish the early-2025 state [62]. A 2026 retrospective’s dating of an OutSystems free developer version to 2014 is historical only [61].

- **OutSystems:** **Core features—**full-stack visual/pro-code development, DevOps and lifecycle tooling, performance/debugging tools, APIs, and legacy/cloud integration; **Target domains—**large enterprise, complex transactional or mission-critical systems and heavy workloads; **Advantages—**technical control, scale and integration; **Limitations—**higher stated pricing and a more technical learning curve [69].

- **Mendix:** **Core features—**visual/model-driven development, Git and DevOps lifecycle support, cloud/on-premises deployment, mobile and multi-experience delivery, APIs and connectors; **Target domains—**enterprise and cross-functional teams from business users to expert developers, including business, mission-critical, mobile, PWA, AR/VR and wearable applications; **Advantages—**collaboration, templates/reuse and cloud flexibility; its 90% development-time and 70%-learned-within-one-month figures are vendor-reported; **Limitations—**specialized extensions may require professionals, while proprietary-model migration, pricing/hidden-cost and learning-curve risks are reported [66][73][62]. A later university prototype used Mendix for course scheduling; its scaling and security barriers were general low-code findings, not Mendix-specific [61].

- **Microsoft Power Apps:** **Core features—**rapid app building, Dataverse, connectors, Microsoft 365/Teams/Power Automate integration, role-based access, auditing, monitoring, web/mobile delivery and custom logic; **Target domains—**workflow, departmental, internal and approval applications for citizen and business users; a retrospective case also describes extending Teams for medical education; **Advantages—**approachability, lower entry cost, automation and Microsoft-ecosystem fit; **Limitations—**not primarily intended for highly complex transactional systems, with constraints on highly custom UI and formula maintainability; general findings on limited functionality, scaling and security are not Power Apps-specific [69][61][62].

- **Retool:** A post-cutoff secondary comparison places it in internal tools, dashboards, admin panels and business apps, with JavaScript/SQL extensions, workflows, Git synchronization, role-based permissions, SSO/audit logging and staging/production controls. Reported limitations are tiered cost, latency as tools grow, weak fit for heavy backend or batch pipelines, external-system dependence and portability difficulty; these remain later secondary evidence rather than cutoff-confirmed findings [62].

- **Roster boundary:** Appian remains outside the required seven rows; secondary evidence positions it for larger enterprises with considerable budgets but reports rigid components that limit customization [63]. ServiceNow is only identified as a native integration target, not as App Engine evidence [62]. A 2026 study mentions two multinationals using ServiceNow but does not identify App Engine or provide relevant metrics, so its early-2025 roster membership remains unresolved [64].

**Definition and provenance**

A low-code development platform enables rapid business-application delivery with minimal hand-coding and upfront setup, using visual/model-driven components, prebuilt widgets, integrations, workflows, and generated code. It differs from no-code mainly through *minimal* rather than absent hand-coding; the source does not separately define RPA-only, workflow-only, or general developer tools [77]. The 23 February 2025 article is a case study, so generic platform benefits and customer-reported results must remain distinct [77].


**Core features:** Mendix is reported as providing prebuilt and pretested components, templates, APIs, enterprise connectors, cloud-AI access, visual model-driven development, and generated code deployable on premises or in the cloud [77].  
**Target domains:** A disguised Fortune 500 financial-services company used Mendix for business applications, Shadow-IT consolidation, relational-data front ends, and process optimization [77].  
**Advantages and business fit:** Visual collaboration allowed business analysts to prototype interfaces, reduce requirements misunderstandings, support mobile applications, and reduce some interface-development and QA effort [77]. It illustrates a hybrid citizen-developer/professional-IT model: effective for defined applications when IT retains governance and support.  
**Limitations:** The first major project took longer than expected; complex cross-organizational work still required traditional development. Ongoing training, CIT support, formal governance, application-sprawl control, database-connection management, and data-protection controls remained necessary [77].  
**Reported result:** In the InsuranceCo case, a 2018 hackathon had **200 participants**, and a quote process fell from **approximately two weeks to around five minutes**; no manpower-reduction or cost-savings amount, baseline, or observation period was reported [77]. These are customer-reported, single-case findings without independent corroboration. A later page updated **17 September 2026** claims **30–50%** faster delivery and describes security, lifecycle, and migration trade-offs, but it is outside the cutoff and is not admissible as early-2025 evidence [78].


**Core features and target:** A July 27, 2021 account describes canvas, model-driven, and portal apps; connectors to **over 200 data sources**; Dataverse, Power Automate, and Teams integration [80]. It targets developer-oriented teams building customer-experience, line-of-business, automation, onboarding, sales, portal, and field-work applications across browsers, phones, and tablets [80]. Microsoft’s own video labels Power Apps “low-code” and claims it accelerates organizational innovation; this is vendor evidence [79].  
**Advantages and limits:** Rapid prototyping, mobile/offline use, and workflow integration are strengths, but premium connectors require premium licensing; the Oracle connector cannot access triggers or stored procedures. Guidance identifies **500 controls**, **30 data connections**, and **200 concurrent gateway connections** as practical constraints, with gateway updating and monitoring required [80]. A juvenile-justice example limits privileged data on the device and synchronizes on a secure network [80].

**Roster boundary**

**Appian** remains outside the fixed seven-row table, but October 2024 roster evidence places it in Gartner’s Leaders Quadrant alongside Mendix, Microsoft, OutSystems, ServiceNow, and Pegasystems [77]. A company release published **12 May 2025**, outside the cutoff, reports Q1 results for **31 March 2025**—including **$99.8 million** cloud subscriptions revenue, **$166.4 million** total revenue, **112%** retention, and **$45.0 million** operating cash flow—but these are corporate figures, not customer application impacts, and are excluded from the early-2025 evidence base [81].

Appian (candidate outside seven): its SEC Form 10-K (19 February 2025) identifies a cloud/on-premises process platform, more than 1,000 customers, and 2024 revenue of $617.022 million (cloud subscriptions: $368.030 million); it supplies no named case, impact metric, or five-challenge evidence. Cloud contracts run 1–3 years and are prepaid/non-cancellable; AWS commitment: $220 million over five years, $44 million annually, with $41.2 million spent in 2024. Gartner is opinion, not fact; its August 2025 leader evidence is post-cutoff. [88][82]

ServiceNow App Engine (candidate outside seven): August 2024 partner evidence covers no-, low- and pro-code custom apps for procurement, finance, HR, fraud and IT, with workflows, portals/catalogs, IntegrationHub, scripting, reporting, DTAP and security. Estimates: procurement 70–100 days (email to auditable approvals); SAP data 60–80 days (Excel to API/BAPI); catalog 200–250 days; AI quality assurance 150–200 days for more than 1,000 engineers; university 150–200 days; vessel 50–75 days; security 20–30 days; relocation 600–800 days (hundreds annually, with reported time and quality gains). 2021 examples include Academy Mortgage (three developers; typical application four weeks/two sprints), Pomerleau mobile logistics, and ICE (more than 20 apps, fewer than 10 people, “50%” effort reduction without a baseline). These are partner, vendor, or customer reports, not independent corroboration; claims include 150+ integrations and legacy/on-premises/cloud, mobile and AI support. [84][87][176]

**Platform evidence and roster boundary**

The comparison uses “low-code” for visual, declarative, model-driven, or generated components supporting application construction, integration, deployment, or lifecycle management; no-code, workflow/BPM-only, and SaaS-attached products are adjacent categories. Greater abstraction improves ease of use but can constrain customization [99][102]. The provisional cutoff is **31 March 2025**; the UI Bakery, Jotform, and ServiceNow pages dated in 2026 are gap evidence only, not proof of the early-2025 state [89][90][92].

- **OutSystems:** Core capabilities include full-stack visual development, web and mobile applications, reusable components, APIs and connectors, data and security tooling, version control, and one-click publishing; an earlier experiment also demonstrated model-driven forms, SQL/blob storage, drag-and-drop fields, file upload/download, threshold triggers, and SMTP integration [95][102]. It targets professional developers and business users in enterprise domains including finance, healthcare, manufacturing, government, education, utilities, retail, and process automation [95][102]. Claimed strengths are speed, governance, customization, scalability, and integration; the experiment found its drag-and-drop design and one-click deployment the strongest low-code experience tested [102]. Limits include a failed time trigger, dependence on predefined SQL and an existing SMTP server, no native Python (external APIs are required), non-open-source status, and greater technical knowledge for complex conditions; vendor lock-in and operating cost were identified but not tested [95][102]. A secondary comparison also calls simple customization tools rudimentary and difficult for citizen developers [93]. The FAQ’s “more than 1,000 companies” figure is vendor-reported on **20 March 2026**, so it is not an early-2025 adoption count [95].

- **Mendix:** Mendix is positioned as a general-purpose enterprise platform combining data sources and systems, with native mobile, version control, governance, CI/CD, cloud-native deployment, and AWS/Snowflake partnerships [99]. It targets business technologists and professional developers building enterprise applications, SAP-integrated solutions, and medium- to high-complexity projects [99][101]. A Mendix-commissioned Coleman Parkes survey of **2,000** respondents in enterprises with at least **1,500 employees** (June–July 2024) reported that **80%** saw improved productivity, **79%** lower operating costs, **73%** better time to market, and **48%** faster application building; **85%** called for more training. These are vendor-commissioned survey findings, not independent Mendix performance measurements [100]. Reported trade-offs include complexity for citizen developers, retirement and merger of the citizen IDE in **2023**, third-party CRM dependence that may add cost and data silos, four editions with add-on charges, and general governance, security, skills, and maintainability concerns that are not all Mendix-specific [93][100][101].

- **Microsoft Power Apps:** Power Apps combines Microsoft 365, Dynamics, Azure, Dataverse, and the Flows engine for forms, screens, workflows, triggers, and smaller applications [101][102]. Its principal target is citizen development and smaller professional development inside the Microsoft ecosystem [101]. That ecosystem integration is an advantage where existing Microsoft services are already deployed. Documented trade-offs include coding requirements for validation and UI workflows, fragmented product documentation, unclear integration errors, separate Dataverse and Flows components, difficult trigger integration, and a list-threshold email condition that failed in the experiment; complex solutions may require Power Automate and two or three user interfaces for different devices [101][102]. A secondary page reports a starting price of **$20 per user per month** and accumulated subproduct costs, but supplies no comparable pricing basis [93].

- **UI Bakery:** Later pages describe internal-tool and business-application construction, AI generation averaging **2 minutes**, **45+** database/API integrations, CRUD and admin panels, workflows, code access, versioning, Git, and backend actions [89][90]. Target users include technical teams, operations, finance, marketing, manufacturing, construction, logistics, and enterprise-admin-panel teams. Vendor/page claims include **75%** development-time reduction for Ultra Clean Holdings (10 developers, three production apps), **2 months** saved by Colas (two developers plus one QA, 20-page apps), and applications serving **600+ employees** [89]. Claimed strengths include React export, self-hosting and air-gapped Docker deployment, SOC 2 Type 2, RBAC, audit logs, MFA, and custom React components. Reported constraints include an existing-backend requirement, an advanced-customization learning curve, **1,000–5,000** monthly server-action executions on lower tiers, a **50-viewer** Team-plan cap, shared non-Enterprise execution, paid-plan-only Git, and Enterprise-only custom SSO [89][90]. Because these pages post-date the cutoff, all UI Bakery cells remain **not verified for 31 March 2025**.

**Scope candidates:** Appian remains outside the fixed seven-row table but is a relevant candidate: sources place it in BPM, dynamic case management, and process automation, and an experiment selected it because it offered process automation and a free tier [93][99][102]. Salesforce Platform remains uncertain because it is primarily a CRM platform with low-code capabilities, industry-cloud integration, professional and citizen developers, and more than **7,000** marketplace resources [93]. ServiceNow App Engine remains outside the required roster: ServiceNow is described as a SaaS-attached low-code ecosystem with governance and more than **600 connectors**, but opaque pricing; the later GRC source is not App Engine-specific and is post-cutoff [92][93][99]. The broader market boundary remains open and should be expanded only with dated, direct capability and business-fit evidence.

Low-code = visual/declarative app building with data/API integration; no-code is higher-abstraction, while RPA/workflow tools and IDEs are adjacent [103][104][105]. OutSystems (2024): rapid enterprise develop/deploy/scale [106]. Mendix (2024): visual business-app logic [104]. Power Apps (Jan 2024): Sales 230, Customer Service 157, IT/Management Tools 139 AppSource add-ons [104]. UI Bakery (Spring 2025): High Performer, 50 reviews, score 52 [103].

OutSystems: ODC plateaued at 350–400 requests/s; C# extensions solved gaps; Green Cargo (2024) had no specific manpower/time/cost figures [107][108].

**Evidence boundary and roster extensions**

Low-code here means visual, declarative or model-driven application construction that reduces hand coding but permits code for production, integration and lifecycle; no-code removes hand coding, while RPA-only, workflow-only and general developer tools are adjacent unless they also build and deploy applications [117]. Appian’s bundled workflow, RPA and AI therefore does not make it RPA-only [109]. Retool remains a required row despite a 5 February 2025 guide calling it a JavaScript/SQL developer tool [116]. General integration claims—40–60% timeline cuts and up to 70% TCO savings—are attributed claims, not comparable platform results [115]. Appian’s July 2025 and ServiceNow’s 2026 evidence is post-cutoff [110][113].

**Mendix:** Mendix Studio Pro supplies a visual model-driven IDE, themes, drag-and-drop reusable components, workflows, process modelling, logic and integrations for citizen and professional developers [111]. Reported strengths include ready-made automation and **more than 500 add-ons**, with European, Latin American and APAC reach; limitations include no out-of-the-box CRM automation and reported prices of **€52,50/month** for a basic single app versus **€2,100/month** for larger multi-application enterprises, described as inflexible [111]. December 2024 NIST-mapped research found HSM support but differences in flexibility, integration and customizability; it is a restricted research finding, not a vendor claim [120].

**Appian (candidate, not a required row):** An authorized partner relays 2024 Gartner claims that Appian was a Magic Quadrant “Leader” and **#1** for complex internal applications; its described capabilities span process orchestration, automation, data fabric, process intelligence, low-code modelling, RPA and AI across public-sector, financial-services, insurance and life-sciences use cases [109]. Benefits such as greater profits, agility, compliance and fewer errors remain partner/vendor claims. A later announcement reports a **99% willingness-to-recommend score from 52 reviews dated 31 January 2025**, but its 30 July 2025 publication is outside the cutoff and supplies no requested case or savings [110].

**Salesforce Platform (uncertain candidate):** It combines low-code and traditional tools for scalable cloud applications, especially sales, marketing and service, serving midsize-to-large enterprises and broad industries; its reported marketplace exceeds **7,000 resources** [111]. It remains outside the fixed seven.

**Retool:** Early-2025 evidence covers UI components, JavaScript/SQL, database/API connectors, workflows, mobile, embeds/portals, Git/versioning, permissions, audit logs, SSO/self-hosting, Postgres, storage, forms, RPC and email; its target is technical teams building internal tools, dashboards, portals and embedded functions [116]. Its strengths are rapid, data-connected internal tooling; trade-offs include the JavaScript/SQL learning curve, limited advanced mobile/forms, per-run workflow pricing, database stickiness, closed-source bug dependence, higher enterprise cost and extra effort for pixel-perfect customer UX [116]. March 2025 vendor releases made multipage apps default and claimed **27% faster average loads** and **30–40% faster** performance than single-page apps, with governance/testing controls; these are vendor-reported, not independent benchmarks [117][154][157]. The cited material reports no Retool-specific manpower, time or cost case metrics [117].

Mendix 2024: visual apps; insurance/municipal; UI/integration/citizen dev; 20 workdays, 24mo; 2–4× reported; over-customizing/lock-in/scale/security [121]

Power Apps: visual low-code, unlike no-code/RPA/workflows [122][124]; canvas/model-driven; Power Fx/Dataverse; 1,000+ connectors; web/mobile/desk; AI/Copilot; PCF/APIs; telemetry/ALM [122]. Targets citizen/pro devs; internal/field; legacy/multi-src [122][126]. Microsoft-reported: 45% cost↓/140% ROI; MS-commissioned 2020: 74% app-cost↓ [122][126]. Limits: REST-only; virtual tables slower/no sec/features; reuse/debug; vol/offline; gov/training [122][124][126].

By 31 Mar 2025, low-code means visual app construction + integration/deployment; no-code/workflow-only tools remain distinct [131][129]. **OutSystems (2020):** visual mobile/desktop apps, data integration, scalable deployment; diverse NoSQL strains abstractions; SQL/embedded scripts proposed [131]. **UI Bakery (2024):** responsive apps/UI, integrations, Angular export for internal tools [138]; customer story: 5k+/400+ clinics, 3–4-month builds, savings unquantified [136]. **Candidates outside seven:** Appian: LCP leader [132]; ServiceNow App Engine: platform-bound, 70% low-code/30% no-code, 11 templates [129].

**AppMaster, UI Bakery and Retool**

**AppMaster.** AppMaster remains a required row, but its FAQ dated **21 September 2021** calls it a **no-code**, rather than low-code, platform using visual tools for backend, web and native iOS/Android applications. [149] Undated documentation lists visual relational data modelling, drag-and-drop business logic, REST/API endpoints and middleware, generated API documentation, screens and templates, third-party modules, source-code and binary export, deployment to AppMaster Cloud, user servers or repositories, local/offline hosting, active-active HA, Docker Swarm/Kubernetes, Health Monitor and PostgreSQL-compatible databases. [146][147][150] Its stated target is business software—process monitoring, support, sales, internal tools, customer portals, admin panels and process automation—for small businesses through large enterprises, including law, trading, public-sector, advertising, medical and IT organizations. [149][150]

**UI Bakery.** In the Rhenus Group customer account (case date not stated), about **30 developers** used UI Bakery and **600+ employees** used its applications; Rhenus is described as a logistics group with **€8.2B turnover, 41,000 employees and 1,330 sites in 70+ countries**. [139] The applications replaced Excel-heavy workflows and included list maintenance, company-wide feedback, arc42 documentation and an Information Security Fit-Gap tool. The documented profile is enterprise licensing, a user-friendly and intuitive workflow, rapid prototyping for small but critical internal tools, standardized input, database storage and group-level access control. The customer reports faster delivery, time and resource savings, less front-end work on small projects, faster cycles through knowledge sharing and fewer central-team bottlenecks, but no percentage, hours, currency or baseline. This is customer-reported, vendor-published evidence: it supports internal-tool fit but not independent quantified ROI or a product-specific limitation. [139]

**Retool.** In the same undated Rhenus account, Retool initially supported internal tools for **600+ users**; shifting licensing strategies and limited intuitiveness prompted reevaluation, and the account establishes no Retool advantage. Scalability, ease of use and cost-effectiveness were the relevant decision conditions. [139] A detailed Retool source is dated **2026**, after the **31 March 2025** cutoff; its later claims about CRUD primitives, SSO/RBAC/audit, workflows, mobile, REST/GraphQL, custom components, branding, complex-app performance and hybrid escape hatches are therefore excluded rather than backdated. [153] Rhenus is not one of the four requested impact organizations, and these cards establish no match for UI Bakery or Retool; AppMaster likewise has no named case. [139][147]

OutSystems/Mendix: enterprise LCAPs [160]; Retool: 100+ components/APIs [155]; AppMaster: visual models→Go/Vue3 [156]; Appian/ServiceNow: candidates [160].

Appian stays outside seven: 2020 customer reports—20% IT-spend saving, 45% productivity gain, <5-month ROI; its eight-week guarantee was vendor-reported, with baselines absent. Salesforce Platform is a dated leader; ServiceNow App Engine is a candidate offering workflow customization/IntegrationHub, but premium connectors and limited deployment. Cited rosters span 13–18 vendors; expansion remains open. [162][163][165][166][167][168]

LCAP = complete-app build/deploy, visual/model-driven tools; exclude workflow-only/MES [177][170]. Seven rows; Appian, Salesforce and ServiceNow remain candidates [171][175]. OutSystems: enterprise/client apps, AI/security/CI-CD; partner/paid-extension/lock-in risks [177][171]. Mendix: model-driven, cloud/on-prem/mobile; partner/customisation/connector risks [174][171]. Power Apps: Dataverse/Automate/Azure/BI, hundreds connectors; premium connectors paid [174][171]. UI Bakery: Gartner LCAP; 4.9/5, 96% recommend (25 reviews); post-cutoff features [169][172]. Retool: post-cutoff internal-tool evidence [172].

Criteria: capability, compatibility, governance and deployment [178]. OutSystems (25 Aug 2025, post-cutoff): process/deployment strength, index 0.3697; Mendix score/index 22.2696/0.2696 [178]. Appian appears in that different platform set, not this roster [178]. Power Apps (vendor): web UI, AI/code, 1,500+ connectors and business use [46]; Jan-2025 case: data-fetching/customization/governance risks, no quantified manpower/time/cost result [179]. SharePoint wizard: 2,000-step workaround [181]. AppMaster vendor docs: model-driven code/Docker/API/on-premise; limited UI customization; 35–45-second rebuilds [148].

Power Apps: HR 3–6 weeks/10 FTEs→1 hour/2 FTEs; energy repair: ≈$1m saved (⅓ employee time); customer-reported, unnamed, no period/no corroboration [48].

Mendix/Jabil: MES/SAP apps; 55 apps/<2y; 80–100 hours saved/project; 94% on-time/on-budget; ~$10m cost avoidance (customer); no FTE/no corroboration [182]

Evidence: vendor pages=reported; research [183][68]; assessments [184]. Mendix—C create/deploy/manage+model/version/cloud; D bank/logistics/manuf/gov-health/retail; A governed speed/integration/deploy (200+ apps; 80% process-time reduction); L no baselines, cutoff unresolved [70][72][76]. Power Apps—postcutoff 9-Jun-25: C plans/process/data/code; D IT/LOB/model-driven/portals/reports; A Entra/CA/DLP+1,500 connectors; L early-25 unverified [186]. UI Bakery—C/D developer-centric internal tools/portals/dashboards+AI Mar-24; A faster-work claim; L initial usability/no independent proof [188]. Appian—outside seven; postcutoff workflow/AI/data claims; State Street onboarding→org-wide automation; no manpower/time/cost figures [185][187][83].

**Huawei AppCube**

Huawei’s AppCube 1.8.0 introduction (revision **30 March 2022**; page published **26 July 2023**) calls it a low-code Application PaaS for industry customers, partners and developers. Core features are visual construction, data modelling, drag-and-drop pages, service/process/event orchestration, reusable assets, integration and container access, packaging/deployment/upgrades, collaboration and sandbox validation; documented domains are smart parks, smart cities and business-visualisation screens. [189]

**Remaining roster boundaries**

OutSystems (27 Mar 2025): visual apps, workflows, APIs; Forge >3,000 extensions [94]. AppCube (2022): low-code PaaS for industry/enterprise apps [190].

OutSystems: vendor-reported 506% ROI/3y, <6-month payback, up to 66% efficiency [191]; Mendix: vendor-claimed unified SDLC, multi-cloud, governance [98].

Retool: supplied evidence is post-cutoff (Wavect, 29 Sep 2026; survey, 7 Oct 2025, 1,128 builders), so 31-Mar-2025 cells are unverified [192][119]. It documents DB/REST/GraphQL, branch/PR control and internal apps; identity/governance, testing, monitoring, self-hosting/portability, omitted export resources and backend-dependent functions remain trade-offs [192].

Power Apps (Jul 2024): visual apps/connectors/data platform, reusable/code-extensible components and Power Automate for professional/citizen developers [123][125]. Composite (30k employees/$10bn): $46.1m benefits, $15.1m costs, $31m NPV, 206% ROI and <6-month payback over 3 years—not universal [123]. Setup: 20×10×30%×$12k=$720k; training 12h; integration gaps require custom APIs/connectors [123][125].

OutSystems: industrial-grade ecosystem; CHAMELEON (2023) measured 92ms on ~200k-widget models, not runtime; the source supplies no case-impact figures [130]. UI Bakery targets internal admin/dashboard/CRUD/approval/operations apps; supports APIs/queries, custom code, automation, RBAC/MFA/audit and Git [134]. Vendor examples: 400+ clinics/5,000+ users and 100+ apps, but no impact metrics; self-hosting shifts infrastructure, monitoring, backups and rollback to customers (2 vCPUs/4 GiB/20 GiB minimum) [134].

UI Bakery: RBAC/TLS/logs, cloud/on-prem; DB/public caution; vendor claim [194]. Huawei AppCube: page/data/logic/BPM; B2B/dashboard/mobile/light; Java/Python algorithms; results unreported [140][180]. Microsoft Power Apps: Dataverse/700+ connectors; governance/lic. risks; 140% ROI, $8.32M NPV/3y [195][145].

Mendix OIDC/API,multi-IdP,PKCE;B2C/B2E/PWA;custom-flow/restart/no-mobile;late [164]. Power Apps planned [197];New Oriental >50% workload expected [173]

OutSystems (2024): visual apps/Forge/CI/CD [96]; 60% of IT orgs saw legacy/API delays (2018) [97]. AppMaster (2023): generated apps, cloud/on-prem [201]

- **Scope:** Low-code = visual/declarative business-app platforms minimizing hand coding; the 2016 landscape listed 42 suppliers, so seven rows are fixed, not exhaustive [161].
- **OutSystems:** Web/mobile; REST/SFTP/DB/legacy integration; .NET/Java/JS/CSS extensions; enterprise target. Strong integration, but a poor connector made Excel manual [202]. A January 2025 prototype (15 participants) reported 1.5/2.3/2-second login/reservation/dashboard times and no manpower or cost figures. Mercedes-Benz Portugal reported 3→1 FTE (66%), six weeks, SLA 44→75%, and half resolution time [203][206].
- **Mendix:** Model-driven web/PWA/mobile, templates, cloud/on-premises deployment, testing, REST/DB/Marketplace integration; suited to complex apps, but steep learning and custom-Java SFTP work are trade-offs [202][205].
- **Power Apps:** Canvas/Model-driven, Power Fx, Dataverse/Microsoft connectors and the Power Platform suite; business/citizen users. Microsoft fit is strong, while non-Microsoft/cross-platform integration, large-data performance, customization and ALM/governance constrain fit [202][205].
- **UI Bakery:** Builder with drag/drop, workflows, 80+ components, DB/API, Git, AI, PostgreSQL, cloud and self-hosting [151].
- **Retool:** Internal dashboards/admin tools with DB/API, JavaScript, workflows, Git, embedded DB and self-hosting; debugging, slow refresh, SQL dependence and price constrain use [204][151].
- **Candidates:** Appian was a 2016 Forrester leader among 14 vendors, with process/mobile/cloud strengths but navigation and declarative-rule weaknesses [161]. Salesforce Platform and ServiceNow/App Engine remain outside seven; ServiceNow evidence concerns its older Platform, not App Engine, and notes scripting burden [161].

OutSystems: customer-facing apps; Forge needs developers; proprietary runtime/deployment dependence; MDEC reports modernization, portals, faster delivery [52][207]. Mercedes-Benz Portugal: 66% FTE/70% SLA, resolution halved; period unstated, vendor case, reuse/redesign confound [208]. Mendix: model-driven/multi-cloud, connectors, BPMN; DLM needs governance, testing, security, training [209]. AppMaster: web/mobile, code export, APIs/backend, offline [86]. Retool: JS/SQL internal tools; accelerator [52]. Generic LCDP risks—governance/customization/integration/scale/security/cost—not product-specific [200].

**Comparative evidence: Mendix and adjacent platforms**

Mendix documentation reports customer-experience, portal, mobile, IoT, microservice, workflow, legacy-modernization, and enterprise-integration use. Vendor-reported examples include Rotterdam’s 100+ applications for 100,000+ users at 8–12 weeks each; PostNL processing over 1 million parcels daily, clearing a two-year backlog in six months, with a 99.95% uptime guarantee; Kaneka rebuilding 55 processes and 13 systems with 80–100% time savings over 18 months; PVH saving 1–3 FTE per application; BDC delivering an MVP in four weeks and reducing processing to 20–30 minutes; Collin delivering in five months and placing €235,354,500 in loans; and a $700,000 increase in single-day ticket sales. These are vendor-reported, with publication dates not supplied. [211]

**MassHousing’s** Mendix 40B affordable-housing application centralized approvals and project data, replaced eight legacy systems, and was delivered in 12 weeks rather than the stated 18 months using .NET by a two-person team; manpower and cost savings, measurement period, and independent corroboration were not reported. [210]

Mendix’s documented trade-offs include SAP customization and the need to preserve a “clean core.” A post-cutoff August 2025 study of 11 late-2021 interviews is historical—not an early-2025 snapshot—but reports missing ERP endpoints, required ERP expertise, technical debt, governance/security demands, update-related maintenance, opaque licensing, and speed gains that depend on reusable components and roughly 6–7 applications. [211][199] A July 3, 2025 review likewise cannot establish cutoff conditions, but reports learning-curve, scale-performance, bespoke-UI, lock-in, talent, and pricing concerns. [212]

Mendix (25 Mar 2025): AI/modeling, REST/OpenAPI, tests, extensibility; targets enterprise/industrial; vendor-stated speed; Java/offline caveats.[159]

Mendix—2026 claim: 10× faster, 90% work; web/mobile, cloud/on-prem, IoT; risks: customization, lock-in, cost, performance [75][213]. 2024 case: reviews −80%, prioritization −70%, assignment time −80%, monthly closures +600% [214]. Power Apps—canvas/model-driven, Dataverse/connectors, AI/ALM [217][218]. Retool—internal admin/ops; server-side credentials, SSO/SCIM, self-hosting (2026) [114]. Appian/ServiceNow App Engine: outside seven [216][128].

Power Apps: canvas/model-driven, Dataverse, workflows, Copilot/code; business/US gov [219][220]; benefits [219]; licensing/capacity risks [141][196][221].

Power Apps—governance/security/ops, Admin Center 26-Feb-25 [142][143]; limits at 100–6000 users 17-Feb-25 [144]. Retool—code/API, 100+ UI components [152].

Power Apps: 2020–24 API/gateway migrations; WS-Trust lacked MFA [47]. UI Bakery: data/API builder, auth, multi-page apps [91][133]; gaps [91]

**UI Bakery**

UI Bakery’s G2 Spring 2025 usability score was **8.34** (data through **25 February 2025**; at least 10 reviews and five responses per question; proprietary algorithm, not a performance benchmark) [223]. State/local-government internal apps cover customer service, onboarding, configuration and incident response; an anonymous vendor case reports **32 developers/16 apps**, **75%** less front-end time, faster deployment, improved responsiveness and lower infrastructure/resource use [193]. Other vendor claims report Action Behavior Centers at **5k+ users/400+ clinics/$0** extra scaling cost, Ultra Clean at **over 75% time saved** (**10 developers/3 apps**), and a logistics deployment with **30 developers/600+ employees** [222]. A **9 October 2020** page reports one client was **3× faster**, but gives no baseline or raw time, manpower or cost measure, and quotes a customer saying Retool lacked flexibility/features [135]. Evidence is vendor/customer-reported; the stated limitation was traditional tools’ setup and maintenance burden and per-application runtime configuration [193].

## Part 2: Real-World Impacts of Low-Code Adoption

**The strongest results measure different things:** Mercedes-Benz demonstrates an operating-workload change; MDEC demonstrates delivery against a planned schedule; MassHousing compares actual development with an estimated conventional rewrite; and New Oriental reports a small-team delivery with expected reductions. A full-time equivalent, or FTE, is an amount of work equivalent to one full-time role, not necessarily an employee leaving the organization.

**Cost proxies preserve useful information:** In the table, **D** means the organization’s fully loaded cost of one developer-week, and **H** means its annual fully loaded cost of one complaints-handler FTE. Each organization has its own local rate. These conditional labor-capacity valuations retain a meaningful cost measure without importing another country’s salary assumptions.

| Organization and location | Application Scenario | Manpower Reduction | Time Savings | Cost Savings |
|---|---|---|---|---|
| New Oriental — Beijing | Tencent Cloud WeDa Reading Space booking/payment mini-program. [27] | Source expects >50% lower manpower/workload; one technical builder | Two-week delivery; >50% duration reduction expected | Conditional gross labor proxy: >2D per build, using full-assignment and workload assumptions |
| Mercedes-Benz — Lisbon label; Portugal operation | OutSystems complaints portal integrated with existing customer systems. [1] | 3→1 FTE: two FTEs released; 66.7% calculated reduction | Third-party complaint resolution halved; SLA compliance 44%→75%; delivery reported as 4–6 weeks | Conditional gross annual capacity value: 2H, if the workload difference persists |
| MDEC — Malaysia | OutSystems legacy consolidation, public portals, grant approval. [2] | Conditional grant-app effort proxy: 93% lower at unchanged staffing; development crew totals 15 | Grant app: 100 planned→7 actual days; 93 days earlier; ≥2× average delivery speed | Shared platform cost replaces payment for each new application; reported cost-structure improvement. [28] |
| MassHousing — Boston label; Massachusetts program | Mendix Chapter 40B application consolidating eight systems and 800+ fields. [29] | Two delivery developers; conditional same-team effort reduction of 84.6% | Estimated 18 months≈78 weeks→12 weeks: 66 weeks earlier; reports changed from days to one-click execution | Conditional same-two-person-team gross labor proxy: approximately 132D per build |

**Cash savings have specific conditions:** Converting these results into company-level cash savings depends on local labor rates, paid work or supplier invoices actually avoided, and the full incremental costs of licensing, implementation, integration, migration, security, hosting, and continuing operation over the same period. Releasing employee capacity can improve productivity without reducing payroll. MDEC’s reported shared-cost arrangement is a customer-specific commercial result, not a general statement that enterprise low-code has only one payment.

### New Oriental in Beijing: a tightly bounded transactional application

**One builder delivered in two weeks:** A December 2022 report states that one technical employee in New Oriental Education & Technology Group’s IT department completed the Reading Space reservation mini-program in two weeks using Tencent Cloud WeDa. The report specifically associates the rapid build with packaged payment and security components. It describes expected reductions exceeding 50% in manpower, development workload, and development duration. [27]

**The Beijing operating context is concrete:** Duozhi’s December 24, 2022 report identifies the Reading Space’s Beijing headquarters store and describes advance reservations for dates, sessions, and seats, followed by payment through the WeChat mini-program. Customers could reserve up to seven days ahead, and approximately 30 seats were selectable. These details establish a commercially useful but relatively bounded transactional scope. [30]

**Packaged services explain the acceleration:** Booking requires a customer interface, available-session information, seat selection, and a payment interaction. Reusing platform components can reduce the repeated construction and connection work associated with those functions. The case supports this component-reuse mechanism; it does not require an assumption that an entire education business, payment network, or physical venue operation was rebuilt in two weeks.

**Expected reductions need consistent arithmetic:** If the two-week delivery represents a duration reduction greater than 50%, the implied conventional-duration threshold is more than four weeks: two weeks divided by 0.5 equals four weeks. That is a conditional interpretation of the source’s expectation, not a measured previous project duration. Likewise, “one builder” describes the delivery team rather than an observed reduction in Reading Space employees.

**The labor-cost proxy is explicit:** Under a full-assignment scenario, one builder for two weeks represents two developer-weeks. If the expected workload reduction exceeds 50%, the comparable baseline effort would exceed four developer-weeks, giving more than two developer-weeks of gross capacity released: baseline effort above four minus two actual nominal developer-weeks. Valued at the organization’s rate D, that produces the table’s conditional proxy of more than 2D before incremental platform and operating costs.

**Do not multiply overlapping percentages:** The report’s manpower, workload, and duration statements describe related aspects of development. Treating each as an independent saving and multiplying them together would overstate the result. The more useful business interpretation is that a narrow, component-friendly application reached service quickly with one technical builder.

**The transferable lesson is scope fit:** New Oriental’s example is persuasive for reservation and transaction workflows that closely match existing components and channels. Its relevance weakens for a proposed application with substantially different integration, concurrency, regulatory, or customization needs. The business lesson is rapid delivery of an appropriately bounded service, not a general workforce-reduction ratio.

### Mercedes-Benz Financial Services: measurable complaints-operation improvement

**Two FTEs of work were released:** The OutSystems customer case reports that complaints handling at Mercedes-Benz Financial Services Portugal fell from three FTEs to one FTE, with occasional help from other colleagues. The exact arithmetic is a two-FTE reduction and 66.7% of the previous dedicated workload: `(3 − 1) ÷ 3 × 100`. The case rounds this to a 66% FTE saving. [1]

**Service quality improved alongside capacity:** The share of complaints resolved within service-level-agreement deadlines rose from 44% to 75%. That is an increase of 31 percentage points, or approximately 70% relative to the original rate: `(75 − 44) ÷ 44 × 100`. Average resolution time was halved for complaints involving third parties, such as suppliers, lawyers, or dealers; that population matters when interpreting the result. [1]

**Centralization removed handling friction:** Before the change, staff relied on manual emails, a shared inbox, a tracker spreadsheet, and an incident-management system. The purpose-built portal centralized communications, tracked process stages, provided category-specific deadlines and alerts, and made management information visible. It also enabled consultation with managers and external participants through the portal rather than repeatedly compiling and forwarding information. [1]

**Reuse explains part of delivery speed:** Mercedes-Benz already had an OutSystems customer portal and middleware connecting it to the customer and contract management system. Its delivery partner, ForTrevo, reused those integrations and brought an established understanding of the business. The observed speed therefore reflects a combination of platform capabilities, reusable technical assets, defined requirements, and partner familiarity—not simply a visual editor acting in isolation. [1]

**Six weeks is the detailed schedule:** The case’s opening summary says four weeks, while the detailed account says six weeks including development, user acceptance testing, and deployment. The six-week description is the more specific planning reference; the table preserves the reported four-to-six-week span. The account describes one junior developer building the solution, with a technical lead assisting in the final stages, which is separate from the operating-team FTE result. [1]

**Capacity value is not automatic payroll reduction:** If the two-FTE workload difference persists for a year, its gross capacity value is twice the annual fully loaded complaints-handler cost, or 2H. The source’s discussion of easier training and more flexible rostering is consistent with redeploying that capacity. Business value can also arise from more timely handling and lower exposure to missed deadlines, but assigning a currency amount to those effects would require additional company-specific assumptions.

**The transferable lesson is process redesign:** This is the strongest of the four cases for a direct before-and-after operating-workload comparison. It is especially relevant to businesses managing regulated cases through inboxes and spreadsheets while already possessing reusable customer-system integrations. Its applicability changes if the proposed process has different volumes, complexity, third-party dependencies, or service obligations.

### MDEC in Malaysia: portfolio consolidation and in-house capability

**The grant application beat its plan:** MDEC’s Grant Approval Committee application was scheduled for 100 days and delivered in seven. That is 93 days earlier, or a 93% reduction against the planned duration: `(100 − 7) ÷ 100 × 100`. OutSystems and Digital News Asia both report the seven-day result. [2][31]

**Portfolio performance uses a different basis:** The customer case says development was at least twice as fast on average, with some instances described as up to ten times faster. The literal planned-duration ratio for the grant application is approximately 14.3: `100 ÷ 7`. These should remain distinct statements: the named project supplies a planned-versus-actual schedule result, while the broader figures summarize the organization’s reported delivery experience. [2]

**The underlying problem was fragmentation:** MDEC had roughly 50 cloud-hosted applications, largely built and maintained by outside vendors, with some more than ten years old. Mixed technologies, maintenance demands, resource constraints, governance gaps, and hiring difficulties made new delivery harder. The low-code adoption therefore addressed an application landscape and capability problem, not simply slow screen construction. [2]

**Consolidation produced identifiable changes:** Malaysia Digital was delivered in four months and consolidated six of eleven applications. Saya Digital’s first application migrated in about one month, with twelve of eighteen applications replaced. Those fractions correspond to approximately 54.5% and 66.7% of the respective targeted portfolios; the denominator is each targeted set, not every application in MDEC’s estate. [2]

**Shared registration reduced repeated work:** Digital News Asia describes a centralized database and registration experience that removed the need for users to enter information repeatedly across programs. Consolidation also reduced the number of separately maintained applications. These mechanisms explain why the adoption could improve both user experience and development productivity: fewer duplicate interfaces and data submissions coexist with fewer fragmented application responsibilities. [31]

**Internal staffing supports a capability interpretation:** The customer case reports fifteen OutSystems developers organized into four teams, supported by training, certifications, and architecture guidance. That is evidence of an internal delivery capability. For the grant application alone, unchanged staffing and scope would make the seven-versus-100-day comparison a 93% reduction in staff effort, but that conditional proxy should not be applied to all fifteen developers or interpreted as an agency headcount cut. [2]

**The cost result concerns procurement structure:** Enterprise IT News reports a one-time cost rather than payment for every newly developed application, which MDEC associated with substantial cost reduction. This is a meaningful qualitative result: repeated purchasing of separate applications was replaced by a shared development arrangement. Its commercial importance grows where the agency can reuse skills and components across several applications, while still funding the internal team and platform operations. [28]

**The transferable lesson is organizational:** MDEC shows how low-code can accompany insourcing, application consolidation, training, and shared data. A business seeking the same benefit should compare the whole portfolio operating model, not assume that a seven-day project proves every future application will be delivered in a week. The judgment changes when proposed applications share few assets or require extensive specialist work outside the platform.

### MassHousing: a complex process delivered through iterative development

**Twelve weeks replaced an estimated rewrite:** A two-person team built MassHousing’s Chapter 40B application with Mendix in twelve weeks. The comparison was an estimated eighteen-month conventional implementation, described by the CIO as roughly one year of coding followed by half a year of quality assurance and testing. The case concerns Massachusetts’s affordable-housing permitting program and its data-intensive oversight requirements. [32]

**The construction-period arithmetic is substantial:** Using 52 weeks per year and twelve months per year, eighteen months equals approximately 78 weeks: `18 × 52 ÷ 12`. Compared with twelve weeks, that yields a 66-week reduction and an estimated 84.6% shorter construction period: `(78 − 12) ÷ 78 × 100`. The result depends on an estimated conventional alternative rather than two completed versions of the same project.

**The broader project clock differs:** Before selecting the development approach, MassHousing spent a year studying the process and produced a 1,200-page requirements document. If that same completed analysis year is included on both paths, the phase comparison becomes approximately 130 weeks versus 64 weeks—`52 + 78` versus `52 + 12`—or about 50.8% shorter. This does not diminish the build result; it shows why the start and finish points of a time-saving claim matter. [32]

**The application addressed genuine complexity:** The consolidated process involved eight legacy systems and more than 800 data elements. Fragmented packaged software, custom .NET applications, and spreadsheets made it difficult to retrieve information, handle requests, and produce compliance reports. The new application centralized the process rather than merely adding another screen over an unchanged collection of disconnected records. [29]

**Early user feedback changed delivery:** A three-day proof of concept produced one-quarter of the required functionality and persuaded the CIO to proceed. The delivery team combined a systems analyst with limited coding experience and a Mendix developer, while users reviewed working software during development. This pairing illustrates supported business participation: domain knowledge and platform expertise worked together, rather than the organization dispensing with engineering. [32]

**Reporting improvement came from integrated data:** Quarterly reports previously took days because staff had to query multiple systems. The new application made reports executable with a mouse click. “One click” describes a simplified reporting interaction, not zero computation time; the commercially important change is removing manual cross-system preparation and making compliance information easier to produce. [32]

**The staffing-cost scenario is transparent:** Holding the delivery team at two full-time developers in both alternatives gives 156 developer-weeks for the estimated conventional path and 24 for Mendix: `2 × 78` versus `2 × 12`. The difference is 132 developer-weeks, or approximately 132D in gross labor-capacity value. This is an explicitly hypothetical same-team comparison using the published duration and team anchors, not a claim about MassHousing’s actual conventional staffing plan.

**The transferable lesson is selective use:** MassHousing’s CIO described Mendix as an “express lane” alongside the organization’s conventional development approach. That is the most useful judgment for other businesses: low-code can deliver substantial, data-heavy process applications, particularly when consolidation and early user feedback matter, without becoming the mandatory tool for every project. [32]

### What the four cases collectively establish

**Repeated work is the common target:** New Oriental reused transaction components; Mercedes-Benz reused middleware and automated case handling; MDEC consolidated applications and registration; MassHousing centralized fragmented data and reporting. The common mechanism is reducing repeated construction or repeated operating work. The cases support that mechanism more directly than they support a single generic percentage for low-code productivity.

**Delivery speed and operating speed differ:** A two-week application build concerns software production. Halving complaint-resolution time concerns a business service after deployment. Replacing days of reporting preparation concerns recurring administrative work. These outcomes may reinforce one another, but they should enter a business case as separate benefits with separate populations and periods.

**Team size is not workforce reduction:** One New Oriental builder, fifteen MDEC developers, and two MassHousing developers describe delivery arrangements. Mercedes-Benz’s three-to-one complaints FTE comparison instead describes an operating-workload change. An organization can build more applications with the same staff, bring previously outsourced work in-house, or redeploy operations employees; all can be valuable without producing the same employment outcome.

**Reuse conditions transferability:** Mercedes-Benz had a functioning portal, middleware, and an experienced delivery partner. MassHousing had already completed extensive requirements analysis. MDEC received training and architecture support. Those supporting assets are part of the explanation and should be included when judging whether a proposed business application resembles the case.

**A financial model adds another perspective:** Forrester’s Microsoft-commissioned July 2024 study modeled a composite global organization with 30,000 employees and US$10 billion annual revenue. It estimated three-year risk-adjusted present-value benefits of approximately US$46.07 million against US$15.07 million in costs, producing about US$31.00 million net present value and a reported 206% return on investment. This is a modeled composite, not a result from the four organizations above or a competitive ranking. [7]

**Its assumptions explain the result:** The model includes a 50% reduction in professional app-development time and a 50% productivity-recapture assumption, recognizing that not every saved hour becomes productive value. Its approximately US$15.07 million cost total includes US$11.28 million licensing, US$1.87 million implementation/training, and US$1.92 million ongoing management. Benefits involve Power Apps working with Power Automate, while the cost model includes costs attributable to Power Apps—an important boundary for a complete solution-level financial comparison. [7]

**The cases support a qualified business judgment:** Low-code can compress delivery and reduce operational friction, particularly where applications use familiar patterns, reusable integrations, and consolidated data. They do not justify an organization-by-organization ROI league table, because the results measure different activities against different counterfactuals.

**Part 2 takeaway:** Treat low-code’s demonstrated gains as application-specific evidence, then distinguish faster delivery, released work capacity, service improvement, and realized financial savings.

## Part 3: Technical and Operational Challenges in Industrial and Commercial Use

**Production success requires more than assembly:** The most consequential challenges are customization, compatibility, security, user-friendliness, and performance, reinforced by testing, lifecycle management, hosting, vendor dependence, and cost control. Capgemini’s industrial guidance stresses technically led governance, while Arivoli’s May 2024 enterprise discussion emphasizes security, scalability, and maintainability as low-code enters normal delivery pipelines. [19][33]

### 1. Customization: exceptions can consume the productivity gain

**Prebuilt behavior has boundaries:** Components and templates accelerate familiar tasks, but an unusual user interaction, complex business rule, or specialized algorithm may fall outside the platform’s standard model. Okoone and AppMaster’s limitations discussion both identify reduced fine-grained control as a recurring concern. The operational risk is discovering this boundary after the application’s data, interface, and workflow have become deeply dependent on the platform. [6][26]

**Extension points alter the answer:** A customization problem does not automatically require abandoning low-code. OutSystems provides C# extensions, Mendix supports Java and JavaScript components, and the internal-tool products expose scripting and API-based integration. Their significance is that difficult behavior can sometimes be isolated in a supported component or external service rather than forced into an unsuitable visual model. [3][5]

**The maintenance consequence matters:** Every custom component introduces code, dependencies, tests, documentation, and upgrade considerations. A heavily extended application may still be an excellent solution, but its maintenance model becomes closer to a hybrid software project than a simple maker-built tool. The relevant question is whether the platform removes enough routine work to justify the remaining custom engineering.

**Set a business-oriented acceptance rule:** Identify the behaviors that distinguish your process from a standard template and determine whether they fit supported extension mechanisms. Low-code remains attractive where those exceptions are contained and maintainable. If most of the application consists of workarounds, a conventional service or frontend may offer a clearer long-term design.

### 2. System compatibility: connectors are only the beginning

**Connection does not guarantee interoperability:** A connector can establish access to a database or service without solving inconsistent identifiers, incompatible data definitions, authorization, transaction boundaries, or failure recovery. OutSystems describes three integration paths: prebuilt API/web-service connections, extract–transform–load tools for data consistency, and custom adapters for difficult or API-less systems. Those paths have different engineering and operating costs. [18]

**Legacy systems require special treatment:** Industrial and commercial estates often contain systems with restricted interfaces, specialized databases, or custom processes. AppMaster’s limitations discussion notes that such integrations can require substantial workarounds or specialist developers. Capgemini similarly advises involving IT because older systems may lack suitable connectors and need conventional code before they can participate in a low-code application. [26][19]

**Data correctness is the production test:** Consider a hypothetical inventory workflow that updates a warehouse record and then sends an instruction to an ERP system. If the second operation fails, a working screen and successful database connection do not establish that the business transaction remains correct. The design needs an explicit approach to partial failure, retries, duplicate requests, reconciliation, and user feedback.

**Centralization can help or compound problems:** MDEC and MassHousing show the value of shared information and fewer fragmented processes. Conversely, Forrester’s interviewees described prior environments where bespoke bridging solutions produced scalability problems and fragmented user experiences. The implication is not to avoid integration, but to give it an architectural owner and make its behavior observable. [31][7]

**Compatibility should be judged end to end:** A representative test should cover realistic data, authentication, writes as well as reads, error handling, and the actual legacy-system behavior. A platform moves up the shortlist when it supports that complete process cleanly; it moves down when “supported integration” means an accumulation of brittle, separately maintained bridges.

### 3. Security and compliance: built-in controls need application-level decisions

**Security remains a shared responsibility:** A platform may supply authentication, encryption, permissions, logs, and security updates while an application still exposes too much data or authorizes the wrong action. Microsoft cautions that low-code security concerns grow when comprehensive governance is absent. AppMaster’s general discussion similarly identifies overlooked access controls, encryption, data-leak protection, and specialized regulatory requirements. [17][26]

**Application permissions must follow business authority:** A user’s ability to open an application is different from permission to view every record, change a financial amount, or approve a transaction. Role-based access control—permissions assigned by role—helps organize access, while single sign-on connects applications to enterprise identity. Neither removes the need to define which data and actions each role should receive.

**Public access changes the threat model:** UI Bakery’s security documentation provides a concrete example: it supports custom roles and warns that anonymous access to a public application’s data source creates security considerations. A tool intended for a small trusted team can become materially riskier when made public or connected to sensitive operational data. The security review must follow the deployed audience and data flow, not the developer’s original intention. [22]

**Managed environments can reduce shadow IT:** Shadow IT means software adopted or built outside normal organizational oversight. A governed low-code program can bring such work into approved environments rather than merely creating more unsupervised applications. Forrester’s Power Apps interviews describe training, controlled environment access, and mandatory architecture and privacy review for sensitive applications as ways to obtain that benefit. [7]

**Regulated evidence must survive operation:** Industrial quality processes, financial services, and personal-data applications may need durable records of who did what, why an approval occurred, and which version of a rule was active. A dashboard showing the current state is not automatically equivalent to a suitable audit trail. Saarinen’s interviews even describe situations where standard platform logging needed customization to meet regulatory requirements. [8]

**The security judgment is conditional:** Favor platforms that can enforce the organization’s identity, authorization, data protection, audit, and deployment policies in the required edition. Centralize the sensitive controls and keep professional review proportionate to business risk. If mandatory controls depend on unsupported custom behavior or an unsuitable hosting arrangement, development speed should not override that mismatch.

### 4. User-friendliness: building a screen is not operating a service

**Ease varies by task and user:** A drag-and-drop interface can make a simple form approachable while data modeling, error handling, and complex workflows remain technical. Microsoft acknowledges that coding skills—or access to someone who has them—may be necessary. Retool’s developer-oriented model goes further, assuming familiarity with JavaScript and SQL for much of its useful behavior. [17][16]

**Business expertise and engineering complement each other:** Domain specialists know the exceptions, approval rules, terminology, and real working conditions. Developers understand data structures, system boundaries, security, and maintainability. MassHousing’s combination of a systems analyst and a Mendix developer illustrates how a mixed team can exploit both types of knowledge rather than expecting one person to possess everything. [32]

**Builder usability differs from user usability:** A platform that lets a maker construct a screen quickly may still produce an awkward workflow for an operator. Commercial applications need clear validation, useful error messages, accessibility, efficient navigation, and appropriate behavior on the devices actually used. Capgemini’s industrial examples emphasize mobile work instructions and interfaces suited to shop-floor conditions, where desktop design assumptions can be inappropriate. [19]

**Visual logic is not complete documentation:** A flow diagram can reveal structure, but may not explain why a rule exists, what an external service guarantees, or how to recover from a failed process. Saarinen’s interviews found limited support for treating the visual development interface itself as sufficient documentation. Maintenance and knowledge transfer still benefit from explicit descriptions of purpose, dependencies, data, and operating procedures. [8]

**The operational response is supported autonomy:** Give business makers approved components, training, and a route to technical help, while assigning continuing ownership to deployed applications. The balance should change with complexity: a local convenience tool can have lighter controls than a payment process, regulatory workflow, or production-critical operational application.

### 5. Performance and scalability: workloads expose abstraction costs

**Scale has several separate dimensions:** Interface load time, database-query time, transaction throughput, concurrent users, batch duration, and recovery from overload are different performance characteristics. An application can be quick for one user yet slow under concurrent writes or a large reporting workload. General vendor statements about cloud-native scalability therefore need to be translated into the business’s actual service requirements. [6]

**Architecture can remove avoidable work:** Retool’s multipage change illustrates a straightforward mechanism: evaluate only the code and components needed for the active page. Similar reasoning applies to querying only required data, avoiding repeated calls, and placing expensive processing in an appropriate backend. The right inference is that application design matters—not that a visual platform is inherently fast or inherently slow. [23]

**Quotas differ from poor optimization:** AppCube’s execution boundaries are examples of hard platform conditions: a correctly functioning script can still exceed the tenant’s permitted runtime or scheduling allowance. Such limits influence whether work should run synchronously, be split into smaller units, or move to an external service. Adding more application screens does not address a mismatch between processing duration and the execution model. [13]

**Cloud hosting does not erase bottlenecks:** Scaling application infrastructure may leave a constrained database, serialized external API, or inefficient query unchanged. AppMaster’s general limitations discussion notes that restricted access to underlying code can also narrow performance-tuning options. Conversely, the presence of generated source or custom-code access gives additional options but still requires engineers to identify and correct the actual bottleneck. [26]

**Industrial control needs a cautious boundary:** Low-code has a well-supported role in work instructions, maintenance workflows, approvals, operational interfaces, and dashboards. For time-critical machine control or safety-related functions, a prudent architecture keeps those functions in appropriately validated control systems unless the complete low-code-based design satisfies the required assurance and timing obligations. Capgemini similarly warns that mission-critical or enterprise-wide use calls for extensive IT and systems-integration involvement. [19]

**Judge performance with the intended workload:** Use realistic data volumes, query shapes, concurrency, external-service latency, and failure scenarios, with explicit response-time and throughput criteria. The conclusion changes when those results demonstrate the required service levels within an acceptable operating cost; a small demonstration alone does not establish production scalability.

### 6. Testing and lifecycle management: faster building increases downstream demand

**A working prototype is not completion:** Low-code can make functionality visible early, but commercial readiness still includes regression testing, authorization checks, integration testing, deployment control, and operating support. Saarinen’s central finding is that accelerated development increases demands on requirements engineering and testing. This is a staffing and workflow issue as much as a tool issue. [8]

**One-click publishing needs release discipline:** The ability to publish quickly is useful only when changes are controlled. Development, testing, and production environments should have distinct purposes and appropriate access, while releases need version identification and a recovery approach. Continuous integration and continuous delivery—CI/CD—automate checks and promotion, but their usefulness depends on the actual testing and version-control facilities available in the selected product and edition. [8]

**Platform changes can affect many applications:** Shared components, connectors, libraries, and runtime upgrades create dependencies across a low-code portfolio. Centralized reuse can reduce duplication, yet a change to a widely used asset can also require broad regression testing. The operational requirement is to know which applications depend on which assets and to have accountable owners for both.

**Maintenance is a continuing function:** Forrester’s Power Apps model explicitly includes ongoing monitoring, security and compliance work, access management, updates, user support, and troubleshooting. Its modeled ongoing-management cost is a useful counterweight to suggestions that low-code removes application maintenance altogether. Platform services can reduce or shift work; the business application still needs stewardship. [7]

**Retain engineering roles proportionately:** OutSystems itself argues that low-code projects continue to need product management, business analysis, developers, and testers, even when the same team can deliver more. The appropriate operating model adjusts those roles to the application’s risk and delivery rate, instead of assuming that visual construction makes them redundant. [34]

### 7. Hosting, portability, and vendor dependence: control has several layers

**Self-hosting and source access differ:** Self-hosting can give control over infrastructure location, network access, backups, and upgrade timing without granting the ability to repair the platform’s code. Retool is the clearest example in these materials: Bold Tech explains that even self-hosted customers depend on Retool to fix critical defects in the closed-source platform. [16]

**Application source is another layer:** AppMaster’s qualifying export arrangements can provide generated application code, which changes the options for continued hosting and maintenance. That should not be confused with obtaining the development platform itself or automatically preserving visual editing on a different system. Procurement needs to distinguish application artifacts, platform software, database contents, and the development experience. [14]

**Data portability does not preserve behavior:** Moving records is different from moving workflows, forms, authorization logic, integrations, and tests. Saarinen’s interviews describe how vendor-specific application definitions can limit migration even when some data or design knowledge survives. The economic consequence is that switching platforms may involve rebuilding behavior rather than simply importing an exported file. [8]

**Hosting choice reallocates operating work:** Cloud service can reduce infrastructure administration; private hosting can improve control over network placement and upgrade schedules. It also makes the customer responsible for more of the surrounding operation. UI Bakery’s additional self-hosting configuration requirements illustrate the practical trade-off: control is useful, but it brings work that must be assigned and funded. [11]

**Accept dependence deliberately:** Vendor reliance is not automatically disqualifying; organizations routinely depend on commercial software. The important question is whether support commitments, export rights, update practices, recovery options, and commercial terms match the application’s criticality. That judgment changes when a platform controls a business-critical capability without an acceptable remediation or continuity arrangement.

### 8. Governance and economics: portfolios can outgrow informal management

**Low-code can create application sprawl:** When development becomes easier, more applications can appear across more departments. Without visibility, organizations may accumulate duplicate workflows, inconsistent data definitions, forgotten owners, and overlapping subscriptions. Capgemini warns that easy creation and deployment complicate standards, security adherence, and cost control unless technical governance regulates expansion. [19]

**Governance should enable useful work:** Requiring a heavyweight approval process for every small improvement can reproduce the backlog problem low-code is meant to address. A more useful division gives low-risk applications approved environments and reusable building blocks, while directing sensitive, complex, or strategically important systems through stronger architecture and security review. Forrester’s interviewees describe centers of excellence providing standards, training, templates, collaboration, and troubleshooting support. [7]

**Licensing can change application behavior:** Per-user charges, developer seats, premium connectors, workflow executions, storage, and enterprise-control tiers can affect both cost and design. A team may optimize a workflow differently when every run has a charge, or discover that required permissions move the application to a higher plan. These are architecture inputs, not merely procurement details to consider after development. [8][16]

**Measure a small set of outcomes:** Useful commercial measures include delivery time, recurring task effort, service quality, application adoption, operating reliability, and complete cost. The four cases show why these should remain distinct. An organization that tracks only application counts or speed may reward rapid production of tools that are rarely used, costly to operate, or difficult to maintain.

**A minimum production control set:** Serious deployments should have the following visible arrangements, proportionate to their business risk:

- **Named ownership and support:** A business owner, technical maintainer, support route, and application inventory.
- **Controlled identity and data access:** Appropriate authentication, permissions, sensitive-data handling, and audit records.
- **Separated development and production:** Versioned releases, testing, approved promotion, and recovery procedures.
- **Realistic workload acceptance:** Defined service expectations, representative load tests, and checks against runtime quotas.
- **Observable business operations:** Logs, failure alerts, integration monitoring, backups, and practical recovery responsibilities.
- **Understood costs and exit rights:** A complete operating budget, necessary commercial entitlements, and documented export and continuity terms.

**Evidence and measurement bases:** Product descriptions and prices are edition-specific rather than live procurement quotations. Organizational outcomes are customer/vendor reports, not controlled comparative benchmarks; expected reductions, planned schedules, and estimated alternatives retain those labels. Calculated percentages use the stated endpoints, calendar conversions use 52 weeks per year and twelve months per year, and the D/H cost entries are conditional labor-capacity proxies rather than audited company cash returns.

**Part 3 takeaway:** Low-code is ready for serious business use when the organization can govern, integrate, test, secure, operate, and economically sustain the resulting applications; faster construction is the starting advantage, not the final acceptance criterion.

**Additional documented evidence**

**Boundary and evidence status**

Serious use means consequential production, mission-critical, regulated, scaled, or materially governed work where integration, security, reliability, compliance, maintenance, or bespoke fit affects deployment. A production-oriented Retool cost model operationalizes this with roles, audit trails, controlled releases, rollback, monitoring, backups, and recovery. A Forrester Power Apps composite models 30,000 employees, $10 billion in annual revenue, 200 professional developers, and 1,800 citizen developers in July 2024; it is not a measured customer result [192][123]. The cutoff is 31 March 2025. The June–December 2025 studies and product updates are excluded; the August 2025 ERP paper is historical late-2021 context only [60][232][231][119][186][199]. Generic findings are not proof of identical platform-specific defects.


**Main challenge mechanisms**

- **Customization.** Complex or highly tailored functions, custom algorithms, and fine control can exceed visual abstractions; deeper changes may require conventional code and reduce maintainability [55]. A Mendix study published on 8 August 2024 found that one project lasted 24 months; adapting Figma-derived UI below the intended abstraction increased effort, while complex logic was moved to Java rather than implemented through many microflows. The study warns that over-customizing can erase time and resource gains [121]. Jabil’s 2024 customer-reported Mendix case records 55 applications in less than two years, 80–100 hours saved at the start of every project, 94% delivered on time and on budget, and estimated $10 million cost avoidance; it lacked independent corroboration. Its workaround allowed sites to customize screens while IT blocked selected areas, supported by reusable templates and central governance [182].

- **Compatibility.** APIs, standard protocols and data formats, backward compatibility, and extensible interfaces are prerequisites; unsupported systems and platform migration create risk [55]. Power Apps interviewees said missing integrations required bespoke bridges, producing scalability and fragmented-user-experience problems. A Mendix insurance case found integration with the existing system landscape relatively easy, but still treated broad integration support as a selection requirement [123][121].

- **Security and compliance.** Serious applications require authentication, authorization, roles or MFA, validation, encryption, logging, and audit trails; simplified drag-and-drop development can omit validation at external-system boundaries [55]. Power Apps documents DLP, identity, monitoring, auditability, access controls, and privacy/security review, but uncontrolled shadow IT can leak data and complicate support [46][123]. DoD evidence shows that point-in-time authorization is insufficient: continuous monitoring, active defense, secure software supply chains, and cross-functional coordination are needed; cautious authorization and unclear reciprocity can delay capability or tool reuse for months [238].

- **Usability and lifecycle.** Low-code still requires application-development knowledge. A Mendix-commissioned survey conducted in June–July 2024 reports that 85% needed more training, 73% recognized upskilling needs, 71% blamed change management for transformation failure, 80% of nontechnical C-suite respondents were concerned about risk or compliance, and 41% saw technical-knowledge gaps [100][229]. Citizen-developer onboarding can exceed IT training; Power Apps uses Centers of Excellence, templates, and troubleshooting, while UI Bakery reports that its initial team-only tool needed refinement in early 2021 for broader users. This is vendor-reported evidence, not proof of a wider UI Bakery failure [121][123][188]. Documentation, testing, versioning, ownership, regression, and recovery remain required; Power Apps specifically calls for ALM with versioning, testing, and controlled releases [46][55][238].

- **Performance.** Large datasets or high traffic can produce variable response times; complex queries across many databases add latency, and platform design and resource costs can limit scale [55]. Microsoft supplies no workload, latency, throughput, or failure-rate measurements for its enterprise-scale claim [46]. Retool production planning still requires monitoring, backups, recovery, timeout/retry, and concurrency tests; four hours per month is plausible only for a quiet, low-support application [192].

- **Portability and cost.** Mendix evidence flags vendor lock-in, limited generated-code portability, added integration, licensing, operations, governance, and skills costs, and maintenance trouble outside prescribed usage paths; its reported 2–4× acceleration is a service-provider estimate, not a benchmark [121]. Power Apps premium connectors, Dataverse, and enterprise-scale scenarios may require standalone licenses; Forrester’s modeled $1.9 million three-year risk-adjusted present value, including a 10% risk adjustment, is not a customer bill [46][123]. Retool may require Enterprise for SAML/OIDC or Git Source Control; self-hosting shifts maintenance to the customer, and exports may omit resources while backend functions remain Retool-dependent [192].

**Platform-specific extension evidence**

- **OutSystems:** NoSQL models/scripts strain low-code abstractions; SQL plus embedded scripts is a proposed workaround [131].
- **Mendix:** Custom coding and extensions support bespoke work but require specialists; no failure is documented [73].
- **Microsoft Power Apps:** Deprecated APIs need PCF controls; legacy connectors need migration; non-primary lookups face a 2,000-step delegation workaround [47][181].
- **UI Bakery:** Angular components, data integration and downloadable code are documented; no serious-use failure is reported [138].
- **Huawei AppCube:** A review reports cumbersome calls, incomplete templates, slow startup, compile-to-publish and costly private deployment [225]; documentation adds ZIP bridges, dependencies, locks and irreversible deletion [235].
- **AppMaster:** Secondary reviews conflict—reduced complex-app flexibility versus easy use and exportable source; vendor support covers training and lifecycle services [239][247].
- **Retool:** Documentation supports npm components, theming, rollback and permissions; AI-provider/HITL constraints, grid limits, custom libraries, testing-selector and self-hosting concerns are also documented [248][237].

Compatibility is change-sensitive: Power Apps migrations, Retool’s 11 March 2025 Slack API break and REST workaround, and OutSystems/AppCube interface setup can interrupt integrations [47][157][131][235]. Power Apps lists ALM and audit controls; AppCube documents OAuth, AK/SK and no-auth options; Retool gates resources by administrator and Edit permissions—controls, not proof of security [143][235][248]. A Power Apps composite assumes 50 professional developers initially, 150 more in year 1, 600 citizen developers initially, 600 more in years 1–2, and four managers in years 1–3 [48]. Interviewees report approval delays, bespoke-integration fragmentation and shadow-IT leak or maintenance risk [48]. Retool’s 30–40% multipage gain is vendor-reported; self-hosted releases are quarterly, four versions behind cloud, tested four weeks and supported six months [157]. UI Bakery and AppMaster exports can reduce portability risk [138][239]. Select only after testing extensions, integrations, security, lifecycle and production workload.

Customization findings are conditional: OutSystems—missing advanced functions halted work until C# extensions [108]; Mendix—bespoke UI/algorithms need external code, but cited evidence is post-cutoff [240][241]; Power Apps—PCF/API/connectors fill gaps; reuse/debugging is limited [122]; UI Bakery—custom components call local actions only [233]; AppCube—complex algorithms use Java/Python microservices [140]; AppMaster—export/API/Go and claims of 22,000 lines/s and millions req/min are 2022 vendor evidence, not a documented limitation [228]; Retool—code skills enable advanced changes, but pixel-perfect UI is costly [116][118]. Risks: REST mediation, scale testing, customer-run operations [122][134].

OutSystems: custom code/modules extend it, but complex logic needs coding; legacy integration and enterprise releases can bottleneck [40][42][44]. Mendix: custom SSO microflows exist, but OIDC API security omits `aud` validation and SCIM may require identifier migration [164]. Power Apps: connectors/Dataverse aid integration and governance, but complex schemas may need repackaging; licensing constrains context [141][145]. AppMaster: regeneration can overwrite edits; adapters/interfaces mitigate this, while animated UIs may not fit [234][156]. Retool’s 2024 workflow evidence records a durability–latency trade-off requiring external storage and sandboxing [236]. UI Bakery-specific serious-use evidence is not established.

Serious = production/regulated/scaled/mission-critical [77]. Customization: OutSystems/Mendix need coding [230]; Power Apps needs developers/connectors [125]; AppCube extension, no limit documented [246]; AppMaster current UI limited [148]; UI Bakery needs code for granular customization [89]; Retool requires SQL [204]. AppCube HTTPS/5000TPS [189].

Power Apps restores delay users [196]; Mendix extensions need pros [205].

Generic LCDP evidence flags integration, scale, security and cost risks [200]. OutSystems needs .NET/Java and custom connectors [203]; Mendix uses Java/JS/modules but complex models strain scale [242][226]; Power Apps needs PCF/connectors or extra tools [152][174]; UI Bakery uses JS/React [137]; AppMaster source export is Enterprise-only [227]; Retool custom code still needs developer expertise [155].

Serious use means consequential production, mission-critical, regulated, scaled or materially governed deployment; customization is specialist/self-host dependent (OutSystems, Mendix, Power Apps, UI Bakery), integration gaps create scale and fragmented-UX risk (Power Apps) or clash with NoSQL models (OutSystems), continuous security needs monitoring, active defense and a secure supply chain, weak governance risks leaks and maintenance, user-friendliness suffers when technical skill or collaboration is required, and Retool trades workflow durability against latency. Lifecycle decisions should separate capability from burden: OutSystems needs costly expertise and lifecycle controls; Mendix over-customizing raises effort; Power Apps needs versioning, testing, controlled releases, governance and licensing management; UI Bakery self-hosting shifts security and operational control to the customer; survey evidence includes an 80% risk/compliance concern and is heterogeneous, not a cross-platform benchmark [244][121][123][243][131][238][48][188][148][236][43][204][46][205][229].

OutSystems needs specialist developers for custom logic, integrations, performance tuning and governance; paid extensions and partners are workarounds, so nontechnical tailoring is constrained, while Mendix remains specialist-dependent and deep component adaptation or REST mapping increases effort. Power Apps can use Azure Functions and custom connectors, but limited reuse/debugging, complex production-app fit and bespoke integrations shift risk to specialists and governance; UI Bakery permits custom code, yet self-hosting shifts infrastructure, identity, updates, monitoring, backups and incidents to the customer [51][171][111][244][121][242][122][126][123][245][134].

Huawei AppCube permits page, logic, process and script changes in template apps, but serious-use cost, maintenance, security and performance consequences are not established; AppMaster may need vendor-created tools for non-standard work; Retool extends with JavaScript and SQL but heavy pipelines need external systems and portability is difficult. Across the seven, these mechanisms range from specialist code (OutSystems, Mendix, Power Apps) to customer-operated UI Bakery, template-based Huawei AppCube, vendor-dependent AppMaster and JavaScript/SQL Retool, affecting delivery, security, maintenance and portability; assign extension and lifecycle owners [140][149][62][43][244][122][134].

## References

[1] <https://www.outsystems.com/case-studies/mercedes-benz-complaints-management-portal> Mercedes-Benz case; Customer case; Complaints-management results; SLA and resolution results; Process redesign; Reuse and delivery account; Delivery account
[2] <https://www.outsystems.com/case-studies/government-agency-delivers-innovation> MDEC case; Customer case; MDEC customer case; Development-speed account; Legacy-system context; Portal consolidation results; Team and support account
[3] <https://www.netsolutions.com/hub/low-code-no-code/outsystems/> Platform guide; OutSystems platform guide; Cost and learning discussion; OutSystems extensibility
[4] <https://www.appsmith.com/blog/low-code-platforms> Platform assessment; OutSystems assessment; Mendix user assessments; Power Apps use cases; Retool assessment
[5] <https://pretius.com/blog/mendix-platform> Mendix overview; Mendix platform overview; Mendix capabilities; Mendix extensibility
[6] <https://www.okoone.com/spark/technology-innovation/inherent-limitations-where-low-code-platforms-fall-short/> Limitations discussion; Complexity discussion; Customization discussion; Performance discussion
[7] <https://tei.forrester.com/go/microsoft/powerappstei/docs/TheTEIOfMicrosoftPowerApps.pdf> 2024 Power Apps study; Forrester’s 2024 study; Governance findings; Forrester’s financial model; Model assumptions and costs; Enterprise integration findings;…
[8] <https://trepo.tuni.fi/bitstream/10024/157011/2/SaarinenMikko.pdf> 2024 practitioner research; Saarinen’s 2024 thesis; 2024 development findings; Software economics discussion; 2024 practitioner interviews; Power Apps cost fin…
[9] <https://uibakery.io/low-code-platform> Product description; UI Bakery description; UI Bakery capabilities
[10] <https://www.subframe.com/tips/ui-bakery-vs-retool-65dd2> Comparison; January 2025 comparison
[11] <https://docs.uibakery.io/on-premise/ui-bakery-on-premise> Hosting documentation; Self-hosting documentation; UI Bakery hosting requirements
[12] <https://www.huaweicloud.com/intl/zh-cn/product/appcube.html> Huawei description; Huawei product description; Chinese product description
[13] <https://www.informat.cn/qa/14625> AppCube guide; Execution-limit guide; Usage-guide boundaries; AppCube execution guide
[14] <https://appmaster.io/blog/compare-drag-and-drop-app-builders> 2023 product comparison; AppMaster architecture; AppMaster’s 2023 architecture description; Export and subscription conditions; AppMaster export arrangements
[15] <https://appmaster.io/> Product scope; AppMaster’s stated scope
[16] <https://blog.boldtech.dev/what-is-retool/> Retool guide; Retool positioning; Retool’s target users and architecture; Retool integration examples; Retool controls and pricing structure; Platform boundari…
[17] <https://www.microsoft.com/en-us/power-platform/products/power-apps/topics/low-code-no-code/low-code-no-code-development-platforms> Microsoft explanation; Microsoft comparison; Microsoft’s security boundary; Microsoft’s skills discussion
[18] <https://www.outsystems.com/blog/posts/low-code-capabilities> Integration capabilities; Legacy integration approaches
[19] <https://www.capgemini.com/wp-content/uploads/2023/08/High-time-for-low-code-in-industrial-IT-OT_PoV_-Sep-23.pdf> Industrial platform guidance; Industrial selection criteria; Industrial application boundaries; Industrial governance guidance; Industrial integration guidance…
[20] <https://www.microsoft.com/en-us/power-platform> Power Platform overview
[21] <https://www.techtarget.com/enterprise-software/tip/10-Microsoft-Power-Apps-benefits> Application and workflow examples
[22] <https://docs.uibakery.io/reference/security> Security documentation; UI Bakery access controls
[23] <https://retool.com/blog/q1-2025-release> Q1 2025 release; Retool’s architecture explanation
[24] <https://www.huaweicloud.com/intl/en-us/product/appcube.html> Industry assets and extensibility; Device and application support; English product description
[25] <https://bbs.huaweicloud.com/blogs/374546> Huawei community description
[26] <https://appmaster.io/glossary/low-code-limitations> AppMaster limitations discussion; Low-code limitations; Integration limitations; Compliance considerations; Optimization and scalability discussion
[27] <http://www.eduydt.com/chengchangjiating/2022/1228/20943.html> 2022 development report; December 2022 development report
[28] <https://enterpriseit.news/mdec-leverages-outsystems-to-increase-operational-efficiency/> Cost account; MDEC cost account
[29] <https://www.casestudies.com/company/mendix/case-study/masshousing-shrinks-18-month-development-project-to-12-weeks> Case account; Consolidation account
[30] <http://www.duozhi.com/industry/insight/2022122414746.shtml> Beijing service description
[31] <https://www.digitalnewsasia.com/business/mdec-leverages-outsystems-platform-consolidate-its-numerous-applications-raise-operational> Digital News Asia account; Centralization mechanism; MDEC’s shared registration
[32] <https://www.mendix.com/customer-stories/masshousing/> MassHousing customer account; Requirements and implementation account; Proof of concept and team; Reporting result; CIO’s selection approach; MassHousing deliv…
[33] <https://doi.org/10.21275/sr24520082915> Enterprise challenges
[34] <https://www.outsystems.com/blog/posts/low-code-vs-traditional-development> Professional oversight discussion
[35] <https://www.appfarm.io/blog/best-low-code-platforms-enterprise>
[36] <https://www.testingxperts.com/blog/low-code-platforms>
[37] <https://appian.com/blog/acp/low-code/low-code-vs-no-code>
[38] <https://www.outsystems.com/low-code>
[39] <https://www.outsystems.com/>
[40] <https://www.ranosys.com/blog/insights/everything-you-need-to-know-about-low-code-outsystems-platform/>
[41] <https://www.appsmith.com/blog/outsystems-competitors>
[42] <https://www.arkasoftwares.com/blog/guide-on-everything-you-need-to-know-about-outsystems-low-code-platform/>
[43] <https://www.outsystems.com/blog/posts/how-to-choose-low-code>
[44] <https://www.netsolutions.com/hub/low-code-no-code/outsystems/>
[45] <https://doi.org/10.18775/jibrm.1849-8558.2015.33.3001>
[46] <https://www.microsoft.com/en-us/power-platform>
[47] <https://learn.microsoft.com/en-us/power-platform/important-changes-coming>
[48] <https://tei.forrester.com/go/microsoft/powerappstei/>
[49] <https://www.mo4tech.com/new-oriental-based-on-hologres-real-time-offline-integration-warehouse-construction-practice.html>
[50] <https://www.gartner.com/reviews/market/enterprise-low-code-application-platform/compare/product/appmaster-io-vs-power-apps>
[51] <https://www.anything.com/blog/outsystems-alternatives>
[52] <https://manchtech.com/en/Comparison-Blogs-Section/7-outsystems-alternatives-specialized-platforms-for-enterprise-application-development/>
[53] <https://www.precedenceresearch.com/low-code-development-platform-market>
[54] <https://www.hudoig.gov/sites/default/files/2025-02/2025ch1001_508_0.pdf>
[55] <https://www.computer.org/csdl/api/v1/periodical/mags/co/2025/03/10896927/24uGETds2Vq/download-article/pdf>
[56] <https://www.mdpi.com/2673-4591/104/1/15>
[57] <https://designrevision.com/blog/low-code-no-code-complete-platform-comparison>
[58] <https://d.dam.sap.com/a/juG2xVj/99719_White_paper_96262_1.pdf?inline=true&rc=10>
[59] <https://doi.org/10.56975/ijrar.v12i3.326879>
[60] <https://rfos.fon.bg.ac.rs/bitstream/123456789/3178/1/ActaEconomica43-4.pdf>
[61] <https://7universum.com/en/tech/archive/item/22525>
[62] <https://www.eleken.co/blog-posts/low-code-application-platforms>
[63] <https://lansa.com/blog/low-code/best-low-code-development-platforms/>
[64] <https://www.semanticscholar.org/paper/CHALLENGES-OF-LOW-CODE-NO-CODE-PLATFORMS-IN-A-AND-Rakovi%C4%87-Milutinovi%C4%87/838a62912b2063bb4d58e3f0c9def017346efb81>
[65] <https://doi.org/10.1177/02683962241295785>
[66] <https://www.mendix.com/mendix-vs-outsystems/>
[67] <https://arxiv.org/html/2410.03480v3>
[68] <https://arxiv.org/html/2504.13141v3>
[69] <https://nareshit.com/blogs/power-apps-vs-outsystems-vs-mendix-low-code-comparison>
[70] <https://www.mendix.com/videos/break-free-from-development-bottlenecks-with-mendix-low-code/>
[71] <https://dodcio.defense.gov/Portals/0/Documents/Library/DoDRefDesignCloudGithub.pdf>
[72] <https://www.mendix.com/>
[73] <https://www.mendix.com/low-code-guide/>
[74] <https://www.gao.gov/assets/gao-25-107114.pdf>
[75] <https://www.igmguru.com/blog/what-is-mendix>
[76] <https://docs.mendix.com/>
[77] <https://doi.org/10.33423/jabe.v27i1.7524>
[78] <https://devsdata.com/what-is-mendix-and-why-to-choose-it/>
[79] <https://www.facebook.com/MicrosoftCanada/videos/create-with-low-code-on-microsoft-power-apps/1218607727111513/>
[80] <https://www.abelsolutions.com/power-of-power-apps-low-code-solution-high-productivity/>
[81] <https://appian.com/about/explore/press-releases/2025/appian-announces-first-quarter-2025-financial-results>
[82] <https://investors.appian.com/node/13661/pdf>
[83] <https://www.rfp.wiki/enterprise-software-enterprise-application-software-eas-enterprise-service-management-esm/android-enterprise/appian>
[84] <https://plat4mation.com/wp-content/uploads/2024/08/P4M-Use-Cases-for-ServiceNow-App-Engine.pdf>
[85] <https://appmaster.io/>
[86] <https://appmaster.io/comparison>
[87] <https://www.nowfedforum.com/wp-content/uploads/2022/03/app-engine-race-great-apps.pdf>
[88] <https://www.sec.gov/Archives/edgar/data/1441683/000144168325000017/appn-20241231.htm>
[89] <https://www.minimum-code.com/tools-directory/ui-bakery>
[90] <https://www.jotform.com/blog/base44-vs-ui-bakery/>
[91] <https://www.softwareadvice.com/low-code-development/ui-bakery-profile/>
[92] <https://www.mordorintelligence.com/industry-reports/enterprise-governance-risk-and-compliance-market>
[93] <https://www.creatio.com/glossary/mendix-alternatives>
[94] <https://success.outsystems.com/documentation/11/integration_with_external_systems/>
[95] <https://www.outsystems.com/company/faqs>
[96] <https://www.outsystems.com/blog/posts/outsystems-dev-questions-answered>
[97] <https://eu-assets.contentstack.com/v3/assets/blt7dacf616844cf077/blt6d80e10367d5552f/679b8840940b90cd1ec18626/OutSystems-Legacy-Modernization-eBook.pdf>
[98] <https://www.mendix.com/evaluation-guide/mendix-difference/>
[99] <https://www.mendix.com/low-code-guide/platform-comparison/>
[100] <https://www.mendix.com/wp-content/uploads/lowcode-barometer-2024-final.pdf>
[101] <https://www.mendix.com/blog/how-to-decide-between-mendix-and-microsoft-power-apps-for-software-delivery/>
[102] <https://ceur-ws.org/Vol-3113/paper12.pdf>
[103] <https://www.salesforce.com/en-us/wp-content/uploads/sites/4/documents/platform/Low-Code.pdf>
[104] <https://link.springer.com/article/10.1365/s40702-024-01109-9>
[105] <https://www.mandsconsulting.com/blog/low-code-no-code-platform-comparison-2025>
[106] <https://www.everestgrp.com/report/egr-2024-32-r-6694/>
[107] <https://scholar.tecnico.ulisboa.pt/api/records/S1rf808ILMXAHfGmGJEacg3tpp1KAD5Nqhqo/file/743d47b1989354a78b19a9bceb716a1a1881a569a4ba7b7bb44bcdec805f35a7.pdf>
[108] <http://urn.kb.se/resolve?urn=urn%3Anbn%3Ase%3Aoru%3Adiva-115764>
[109] <https://www.iam-app.co/low-code>
[110] <https://www.prnewswire.com/news-releases/appian-recognized-as-a-leader-in-the-2025-gartner-magic-quadrant-for-enterprise-low-code-application-platforms-302517610.html>
[111] <https://www.creatio.com/glossary/appian-alternatives>
[112] <https://retool.com/>
[113] <https://www.maximizemarketresearch.com/market-report/enterprise-architecture-tools-market/319328/>
[114] <https://helix.tray.ai/blog/retool-alternatives/>
[115] <https://www.mordorintelligence.com/industry-reports/enterprise-application-integration-market>
[116] <https://blog.boldtech.dev/what-is-retool/>
[117] <https://retool.com/blog/what-is-low-code>
[118] <https://www.adalo.com/posts/what-is-retool/>
[119] <https://retool.com/blog/2025-builder-report>
[120] <https://scholarworks.lib.csusb.edu/etd/2075>
[121] <https://doi.org/10.1365/s40702-024-01095-y>
[122] <https://learn.microsoft.com/en-us/power-platform/guidance/adoption/application-modernization>
[123] <https://tei.forrester.com/go/microsoft/powerappstei/docs/TheTEIOfMicrosoftPowerApps.pdf>
[124] <https://www.microsoft.com/en-us/power-platform/products/power-apps/topics/low-code-no-code/low-code-vs-traditional-development>
[125] <https://learn.microsoft.com/en-us/power-apps/guidance/fusion-dev-ebook/01-what-is-fusion-dev-approach>
[126] <https://dxc.com/content/dam/dxc/projects/dxc-com/au/practices/microsoft-practice/pdfs/DXC-Technology-The-Silent-Revolution-Microsoft-Power-Platform-POV.pdf>
[127] <https://www.gumloop.com/blog/appsmith-alternatives>
[128] <https://www.youtube.com/watch?v=dG3f53KKnBo>
[129] <https://www.techzine.eu/blogs/applications/56875/servicenow-fully-enters-low-code-market-with-app-engine-studio/>
[130] <http://arxiv.org/abs/2305.03361v1>
[131] <http://arxiv.org/abs/2004.13495v1>
[132] <https://ceur-ws.org/Vol-3921/phd-paper5.pdf>
[133] <https://docs.uibakery.io/build-with-ai/features>
[134] <https://uibakery.io/self-hosted>
[135] <https://uibakery.io/blog/ui-bakery-co-founders-interview-on-nocodeportal>
[136] <https://uibakery.io/clients/how-action-behavior-centers-scaled-therapy-operations-for-5-000-users-across-400-clinics---without-scaling-their-development-costs>
[137] <https://docs.uibakery.io/llms-full.txt>
[138] <https://www.starterstory.com/ui-bakery-breakdown>
[139] <https://uibakery.io/clients/avoiding-the-excel-swamp-in-the-company-wide-internal-tools-with-ui-bakery>
[140] <https://bbs.huaweicloud.com/blogs/307164>
[141] <https://www.microsoft.com/content/dam/microsoft/final/en-us/microsoft-brand/documents/Power-Platform-Licensing-Guide-November-2024-PUB.pdf>
[142] <https://www.microsoft.com/en-us/power-platform/blog/2025/02/26/mastering-the-microsoft-power-platform-with-managed-governance-security-and-operations/>
[143] <https://learn.microsoft.com/en-us/power-platform/release-plan/2024wave2/power-platform-governance-administration/>
[144] <https://www.appfarm.io/blog/scaling-beyond-microsoft-power-platform>
[145] <https://dws.dataworld.com.hk/file.php?_file=template%2F721%2Fphoto%2F648029c00357e.pdf>
[146] <https://appmaster.io/docs/getting-started/what-is-appmaster-io>
[147] <https://appmaster.io/docs>
[148] <https://appmaster.io/university/tutorials/getting-started/appmaster-basics>
[149] <https://appmaster.io/blog/no-code-faq-answering-frequently-asked-questions-from-appmasterio-users>
[150] <https://appmaster.io/glossary/low-code-constraints>
[151] <https://uibakery.io/microsoft-power-apps-alternatives>
[152] <https://retool.com/competitor/powerapps>
[153] <https://retool.com/blog/react-or-retool>
[154] <https://retool.com/blog/q1-2025-release>
[155] <https://research.contrary.com/company/retool>
[156] <https://appmaster.io/blog/keep-exported-source-code-in-sync-governance>
[157] <https://docs.retool.com/changelog/page/28>
[158] <https://www.dashworks.ai/blog/building-a-prompt-engineering-playground-in-2-days-with-retool>
[159] <https://www.mendix.com/blog/mendix-release-10-21-ai-ai-ai-boosting-developer-productivity/>
[160] <https://www.gartner.com/en/documents/3991199>
[161] <https://smallake.kr/wp-content/uploads/2020/01/idSisdoc_12055179v2-86-Forrester-ES117623.pdf>
[162] <https://appian.com/about/explore/press-releases/2020/appian-named-the-clear-leader-in-nucleus-research-s-2020-value-m>
[163] <https://www.zoho.com/sites/zweb/images/zoho_general_pages/magic-quadrant-for-enterprise-low-code-shareable-until-end-of-year-only.pdf>
[164] <https://docs.mendix.com/appstore/modules/oidc/>
[165] <https://opendva.usercontent.opencode.de/simplex-studie-ap2/assets/files/Forrester-Wave-Low-Code-Development-Platforms-Q42017-40dabcbb81aae80f71429420c9306157.pdf>
[166] <https://lasvitprod.blob.core.windows.net/assets/2022/09/19/The-Forrester-Wave_-Low-Code-Development-Platforms-For-Professional-Developers-Q2-2021_uid_632864b699df4.pdf>
[167] <https://www.salesforce.com/news/stories/salesforce-recognized-gartner-magic-quadrant-for-enterprise-low-code-application-platforms/?bc=HA>
[168] <https://www.salesforce.com/news/stories/forrester-names-salesforce-a-leader-among-low-code-app-development-platforms/>
[169] <https://www.gartner.com/reviews/market/enterprise-low-code-application-platform/compare/product/build-vs-ui-bakery>
[170] <https://top-logic.com/wp-content/uploads/PAC-Analyst-Vendor-Landscape_Low-Code-No-Code-2025.pdf>
[171] <https://nxgenlowcode.biz/files/nextgen_platform_comparison_2025.en.pdf>
[172] <https://blog.tooljet.com/low-code-platforms/>
[173] <https://cloud.tencent.com/developer/article/2198285>
[174] <https://www.zoho.com/sites/zweb/images/creator/lcap-technology-value-matrix-2020.pdf>
[175] <https://newsroom.servicenow.com/press-releases/details/2024/ServiceNow-Named-a-Leader-in-the-2024-Gartner-Magic-Quadrant-for-Enterprise-Low-Code-Application-Platforms-for-Fifth-Consecutive-Year-10-22-2024-traffic/default.aspx>
[176] <https://newsroom.servicenow.com/press-releases/details/2021/ServiceNow-Named-a-Leader-in-Low-Code-Development-Platforms-for-Professional-Developers-by-Independent-Research-Firm-05-12-2021-12-00-AM/default.aspx>
[177] <https://solutionsreview.com/business-process-management/key-takeaways-2021-gartner-magic-quadrant-for-enterprise-low-code-application-platforms/>
[178] <https://doi.org/10.3390/engproc2025104015>
[179] <https://doi.org/10.70623/jnaj9314>
[180] <https://www.informat.cn/qa/14642>
[181] <https://doi.org/10.1007/978-1-4842-8823-8_16>
[182] <https://www.mendix.com/customer-stories/jabil-aligns-it-and-operations-to-transform-manufacturing-processes-at-scale/>
[183] <https://www.usenix.org/system/files/osdi24-chow.pdf>
[184] <https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53Ar5.pdf>
[185] <https://appian.com/blog/2025/appian-25-3-release-highlights>
[186] <https://www.microsoft.com/en-us/power-platform/blog/2025/06/09/whats-new-in-power-apps-may-2025-feature-update/>
[187] <https://appian.com/learn/events/event-videos/state-street-case-study--connecting-people--process--and-data-fo>
[188] <https://uibakery.io/about-us>
[189] <https://support.huawei.com/enterprise/zh/doc/EDOC1100239294>
[190] <https://support.huawei.com/enterprise/zh/doc/EDOC1100267340>
[191] <https://www.outsystems.com/fr-fr/news/tei-low-code-roi>
[192] <https://wavect.io/blog/retool-vs-custom-internal-tools-three-year-cost/>
[193] <https://uibakery.io/clients/transforming-government-software-development-with-ui-bakery>
[194] <https://docs.uibakery.io/reference/security>
[195] <https://www.gartner.com/en/documents/5463895>
[196] <https://dynamicsusergroup.com/wp-content/uploads/2024/11/Recommended-Practices-for-Power-Apps-and-Dataverse%E2%80%94How-to-Grow-with-Own-2.pdf>
[197] <https://learn.microsoft.com/en-us/power-platform/release-plan/2025wave1/power-apps/planned-features>
[198] <https://www.rapidevelopers.com/review/outsystems>
[199] <https://lswi.de/assets/downloads/publikationen/109/Abendroth_Bender_2025_Bridging_the_Gap_Low-Code_Platforms_and_the_Future_of_ERP.pdf>
[200] <https://doi.org/10.1109/access.2023.3258539>
[201] <https://appmaster.io/blog/small-business-success-with-apps-creator-software>
[202] <https://trepo.tuni.fi/handle/10024/161705>
[203] <http://theseus.fi/handle/10024/908093>
[204] <https://www.appsmith.com/blog/low-code-platforms>
[205] <https://www.clevr.com/blog/mendix-vs-powerapps-which-low-code-platform-wins>
[206] <https://www.casestudies.com/company/outsystems/case-study/mercedes-benz-financial-services-portugal-digitally-transforms-complaints-management>
[207] <https://www.outsystems.com/case-studies/government-agency-delivers-innovation>
[208] <https://www.outsystems.com/case-studies/mercedes-benz-complaints-management-portal>
[209] <https://www.mendix.com/customer-stories/dlm-finance-powers-agile-financial-services-with-cloud-native-low-code-platform/>
[210] <https://www.mendix.com/customer-stories/masshousing/>
[211] <https://www.mendix.com/low-code-guide/low-code-use-cases/>
[212] <https://www.superblocks.com/blog/mendix-reviews>
[213] <https://www.mendix.com/strategies/enterprise-application-development/lifecycle/>
[214] <https://media.armis.com/pdfs/cs-mendix-en.pdf>
[215] <https://www.epcgroup.net/microsoft-power-apps-model-driven-canvas-enterprise-2026?srsltid=AU7gw4VjgdOtUZ2Xn9Wq0bU6b2pndQBrzJuVF10gjBZk5OGtgy8s-5Wy>
[216] <https://www.youtube.com/watch?v=3BxN09ccB7o>
[217] <https://learn.microsoft.com/en-us/power-apps/>
[218] <https://dynamicssolution.com/power-apps-updates-unlocking-low-code-development/>
[219] <https://learn.microsoft.com/en-us/power-apps/powerapps-overview>
[220] <https://learn.microsoft.com/en-us/power-platform/developer/get-started>
[221] <https://www.gartner.com/reviews/market/enterprise-low-code-application-platform/vendor/microsoft/product/power-apps>
[222] <https://uibakery.io/solutions>
[223] <https://www.salesforce.com/en-us/wp-content/uploads/sites/4/documents/platform/Application-Development.pdf>
[224] <https://marketplace.huaweicloud.com/contents/3b8e1e0e-6217-4698-bb46-213fae5a0532>
[225] <http://www.dimajia.com/report/7/>
[226] <https://www.mendix.com/customer-stories/exp-realty-moves-to-microservices-archictecture/>
[227] <https://appmaster.io/pricing>
[228] <https://www.pr.com/press-release/860857>
[229] <https://www.mendix.com/blog/low-code-market/>
[230] <https://doi.org/10.1145/3652620.3688337>
[231] <https://retool.com/resources/videos/retool-presents-enterprise-ai-that-delivers>
[232] <https://doi.org/10.63356/ace.2025.013>
[233] <https://docs.uibakery.io/concepts/custom-components-2.0>
[234] <https://appmaster.io/docs/getting-started-en/faq>
[235] <https://support.huawei.com/enterprise/zh/doc/EDOC1100295974/cb58198>
[236] <https://temporal.io/resources/on-demand/orchestrating-complex-customer-defined-dags-with-temporal>
[237] <https://retool.com/resources/videos/retool-developer-day-q2-2024-release>
[238] <https://dodcio.defense.gov/Portals/0/Documents/Library/DevSecOpsStateOf.pdf>
[239] <https://www.trustpilot.com/review/appmaster.io?page=3>
[240] <https://edana.ch/en/2026/03/12/building-an-app-with-mendix-create-run-deploy-and-understand-the-real-enterprise-implications/>
[241] <https://bonjoy.com/articles/mendix-vs-traditional-development/>
[242] <https://www.theseus.fi/server/api/core/bitstreams/1350be49-533e-46d7-87d5-368156b755f7/content>
[243] <https://www.uibakery.io/clients/how-qualifirst-cut-300-000-in-annual-development-costs-and-took-control-of-their-internal-tooling>
[244] <https://www.appfarm.io/blog/outsystems-alternatives-enterprise>
[245] <https://blog.tooljet.com/best-low-code-application-platforms/>
[246] <https://bbs.huaweicloud.com/blogs/271157>
[247] <https://appmaster.io/services>
[248] <https://docs.retool.com/build/apps/concepts/intro>
