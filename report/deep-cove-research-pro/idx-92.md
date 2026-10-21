# Integrated Urban Water Management Models: A Horizontal Comparison Before April 2018

**The models serve different decisions.** Across the 13 requested Integrated Urban Water Management Models (IUWMMs), the pre-April-2018 literature does not identify one tool that combines detailed network hydraulics, whole-cycle resource planning, life-cycle accounting and social-policy simulation equally well. MIKE URBAN and Sobek Urban are strongest for hydraulic questions; Hydro Planner and WMOST address resource and management portfolios; CWB and WaterMet2 extend water balances into sustainability accounting; and DAnCE4Water explicitly connects urban development, infrastructure and societal change. These distinctions are more useful than an overall feature-count ranking. [1]

**The historical boundary is explicit.** This comparison covers information documented through **31 March 2018**, including research models and prototypes alongside released software. The capability tables distinguish directly documented functions (**Y**), partial or linked functions (**P**), explicitly excluded functions in a documented version (**N**) and functions undocumented in the cited evidence (**U**).

| Requested element | Coverage | Principal finding |
|---|---|---|
| Model basic information | 13 models; five requested fields | Development milestones are distinguishable from exact first-development dates |
| Drinking Water Management | Nine functions | Separate resource allocation, distribution hydraulics and local reuse analysis |
| Stormwater Management | Nine functions | WBM emphasizes source controls; MIKE URBAN emphasizes drainage hydraulics |
| Cost and Energy | Seven functions | CWB, WaterMet2 and WMOST provide different kinds of economic assessment |
| Social and Policy Factors | Four functions | DAnCE4Water models system evolution; several others assess externally specified scenarios |
| Complete capability comparison | 13 × 29 = 377 intersections | Every intersection receives an explicit capability mark |

**The report follows the decisions.** Table 1 first compares development history, developers, advantages and scales. Table 2 then examines the four requested capability categories, explaining where superficially similar marks represent different mathematical detail, system boundaries or decision functions.

## Table 1. Model Basic Information Table

**The dates describe development milestones.** In the “First Developed Year” column, **≤** means that the model demonstrably existed by the stated year. This preserves a useful chronological value without treating a publication, manual or software release automatically as the first year of coding. CWB’s development interval is explicitly identified as an estimate.

**The spatial boundary matters immediately.** An urban water-management model may represent individual appliances, properties, neighborhoods, entire cities or their supplying catchments. Those are different analytical boundaries: a model that calculates imported-water demand at household taps does not necessarily simulate the reservoirs, abstraction rules or distribution pressures supplying those taps.

### Models 1–5: hydraulics, balances and source controls

| Model Name | First Developed Year | Main Developer | Core Advantages | Typical Spatiotemporal Scales |
|---|---|---|---|---|
| Sobek Urban | ≤2017; documented integrated Urban suite | Rijkswaterstaat/WL Delft Hydraulics lineage; Deltares stewardship | Coupled 1-D/2-D hydraulics; runoff, quality and control modules | Spatial: urban drainage–river systems; temporal: sub-daily event scale, estimated from hydrodynamic scope |
| Aquacycle | ≤2000; user-manual milestone | V. G. Mitchell, R. G. Mein and T. A. McMahon; CRC for Catchment Hydrology/Monash | Daily whole-cycle water balance; decentralized recycling assessment | Spatial: unit block–cluster–urban catchment; temporal: daily, over continuous multi-year records |
| Hydro Planner | ≤2005; design and implementation paper | CSIRO Water for a Healthy Country; later collaboration with eWater CRC | Links selectable component models; integrates resources, demands and reuse | Spatial: subcatchment–city–region; temporal: daily hydrology, monthly supply and annual demand components |
| WaterCress | ≤2002; manual and symposium paper | Richard Clark and David Cresswell, Clark & Associates | Node-based catchment–supply modeling; stormwater harvesting and aquifer-storage reliability | Spatial: site/urban system–river basin; temporal: daily; Parafield application spans 1959–2060 |
| Water Balance Model (WBM) | ≤2002; existing tool described in upgrade plan | CH2M HILL | Continuous runoff-volume assessment; source-control and land-use scenario comparison | Spatial: site/neighborhood–subcatchment/watershed planning; temporal: continuous, rainfall input at any increment |

**Sources for these entries.** Sobek’s integrated modules and Deltares documentation are described in the 2017 review [1]; its originating developer attribution appears in the SOBEK developer brochure [2]. Aquacycle’s 2000 manual and 2001 model paper are identified in the same review, while its spatial hierarchy and reuse options are described in Last’s 2010 thesis [3]. Hydro Planner’s institutions and mixed time resolutions are documented by Maheepala et al. in 2005 [4]. WaterCress’s 2002 origins are cited in Last’s thesis and the 2017 review; its developer, daily operation and Parafield application are recorded in Goyder Institute metadata from 2015 [5]. WBM’s developer and operating principles are directly described in the 3 June 2002 work plan [6].

### Models 6–9: local integration and network analysis

| Model Name | First Developed Year | Main Developer | Core Advantages | Typical Spatiotemporal Scales |
|---|---|---|---|---|
| Urban Cycle | ≤2005; named model paper | Hardy, Kuczera and Coombes research team, University of Newcastle | Detailed allotment water balances; stochastic rainfall and demand representation | Spatial: allotment–urban catchment; temporal: six-minute step in the documented implementation |
| Urban Volume and Quality (UVQ) | ≤2000; development-and-implementation report | T. Farley, C. Zoppou, S. R. Gray and G. Mitchell, CSIRO | Combined water/contaminant balances; treatment and on-site option assessment | Spatial: property–cluster–estate/catchment; temporal: daily-scale estimate from Aquacycle lineage |
| MIKE URBAN | ≤2004; named conference application | DHI | Water-distribution and drainage hydraulics; GIS-based network integration | Spatial: urban supply/sewer networks and 2-D surfaces; temporal: sub-daily event scale, estimated from hydrodynamic scope |
| Urban Water Optioneering Tool (UWOT) | ≤2008; model-description paper | C. K. Makropoulos and colleagues, including D. Butler | Hierarchical technology optioneering; water-efficiency, cost and energy indicators | Spatial: appliance/property–neighborhood hierarchy; temporal: six-minute–daily comparison bracket, estimated from peer-model anchors |

**Sources for these entries.** The 2005 UrbanCycle paper by Hardy, Kuczera and Coombes and the 2004 MIKE URBAN conference paper are identified in the 2017 review’s bibliography [1]. Urban Cycle’s six-minute implementation, UWOT’s scoping role, and their relative strengths are described in Last’s 2010 model comparison [3]. UVQ’s 2000 development report and author team are identified in the CSIRO Urban Water Program documentation [7]. DHI’s 2012 release documentation [8] establishes specific pre-cutoff hydraulic functionality.

### Models 10–13: sustainability, transitions and optimization

| Model Name | First Developed Year | Main Developer | Core Advantages | Typical Spatiotemporal Scales |
|---|---|---|---|---|
| City Water Balance (CWB) | 2006–2010, estimated development interval | Ewan M. Last, University of Birmingham, SWITCH project | Natural-system and decentralized-option representation; whole-life cost and life-cycle energy | Spatial: unit block–minicluster–subcatchment–city; temporal: daily, annual–decadal analysis, including 2055 scenarios |
| DAnCE4Water | ≤2011; named model conference papers | Monash University–University of Innsbruck collaboration, with Melbourne Water | Links urban evolution and infrastructure; represents socio-technical interactions | Spatial: household/urban-form detail within city–regional planning; temporal: annual urban development with linked hydraulic analyses |
| WMOST | ≤2013; version 1 documentation and release | U.S. EPA ORD and Region 1, with contracted research teams | Least-cost management portfolios; integrates supply, stormwater and watershed objectives | Spatial: local jurisdiction/small watershed, spatially lumped; temporal: daily or monthly |
| WaterMet2 | ≤2014; new-model introduction | K. Behzadian, Z. Kapelan and TRUST research collaborators | Integrated water-system metabolism; cost, energy, leakage and GHG assessment | Spatial: indoor–local–subcatchment–city; temporal: daily over user-defined years; Oslo demonstration: 30 years |

**Sources for these entries.** CWB’s estimated interval uses SWITCH’s February 2006 start and the completed September 2010 thesis as its endpoints; an implemented precursor was presented in 2007. Its daily resolution is expressly stated in the 2010 conference paper reproduced in Last’s thesis [3]. DAnCE4Water’s 2011 papers are listed in the 2017 review [1], while its institutional collaboration and development objectives appear in the 2014 CRC fact sheet [9]. WMOST’s originating institutions and daily/monthly structure are documented in the 2013 EPA manual [10]. WaterMet2’s developer team, four spatial scales and daily resolution are described by Behzadian et al. in 2014 [11].

### What development history changes in the comparison

**Several chronological anchors precede later descriptions.** WaterCress was documented in 2002, rather than first appearing with its 2015 Parafield metadata. Urban Cycle had a named 2005 publication before Graddon’s later UrbanNet work. Likewise, DAnCE4Water’s named 2011 conference papers precede the July 2013–June 2016 CRC project that expanded its scope. These distinctions prevent later applications or redevelopment projects from being mistaken for model origins. [1]

**Successors should remain separate entities.** UVQ extends Aquacycle by adding contaminant balances, but that does not make every UVQ feature an Aquacycle feature. Similarly, UrbanNet embeds WathNet5 within the Urban Cycle framework to address network configurations beyond Urban Cycle’s directed-acyclic-graph structure. UrbanNet’s optimization belongs to a named extension, not automatically to the original Urban Cycle core. [1][12]

**Release history also changes functionality.** WMOST version 1, documented in 2013, considered water quantity rather than water quality. Version 2 retained a water-quantity focus, while version 3’s pre-cutoff documentation added water-quality management, pollutant-loading targets and expanded combined-sewer-overflow assessment. Therefore, a water-quality judgment based only on WMOST version 1 would misrepresent the capability documented by early 2018. [10][13]

**Access status is heterogeneous.** WaterCress’s 2015 metadata explicitly identifies free software requiring no licence, and WMOST’s 2013 documentation identifies a public-domain tool. Hydro Planner’s 2013 report identifies a prototype. DAnCE4Water’s 2014 fact sheet describes conditional rolling release, while a December 2017 study still describes the broad platform as under development and not fully operational. Consequently, “mainstream models” is a better common description for this corpus than “13 equivalent commercial products.” [5][10][14][15]

### How spatial and temporal scales affect model choice

**Event hydraulics and strategic balances differ.** Sobek Urban and MIKE URBAN resolve flow through infrastructure and, in coupled configurations, across the urban surface. Aquacycle and WaterMet2 instead use daily balances to examine quantities, storage, demand and longer-term performance. A daily balance can represent annual water savings and prolonged supply deficits without resolving the short-lived peak that determines whether a particular sewer surcharges. [1][11]

**Urban Cycle occupies an intermediate position.** Its documented six-minute implementation can represent peak-flow behavior while retaining an integrated allotment-based water-cycle perspective. Last’s comparison nevertheless notes that this short step is less convenient for city-scale scoping. The practical trade-off is between retaining short-duration demand/runoff dynamics and keeping large, long-horizon scenario exercises manageable. [3]

**Hydro Planner explicitly mixes resolutions.** In the 2005 implementation, the end-use model generated annual consumption, REALM generally operated monthly, and receiving-water quality calculations used daily values. Hydro Planner translated between these representations through aggregation and disaggregation. This is a substantive integration mechanism: matching annual totals does not by itself establish that the resulting daily demand or release sequence reproduces actual operating behavior. [4]

**Spatial detail has several meanings.** CWB describes a city through unit blocks, miniclusters and subcatchments, whereas MIKE URBAN describes individual network elements and their hydraulic connections. WaterMet2 recognizes four spatial levels, but its Oslo demonstration used one subcatchment and one local area. Thus, a model’s possible hierarchy should be distinguished from the actual disaggregation used in a case study. [3][16]

**The basic-information takeaway is simple.** Select the system boundary and process resolution before comparing the number of advertised functions.

**Additional documented evidence**

| Entity | Model Name | First Developed Year | Main Developer | Core Advantages (summarize 1-2 key feat… | Typical Spatiotemporal Scales (spatial… | Supply-Demand Analysis | Water Resource Availability Analysis | Distribution System Simulation | Regional Water Allocation | Leakage Analysis | Abstraction from Hydrosystems | Customized Modeling for Different Users… | Alternative Water Infrastructure Options | Treatment Scheme Simulation | Best Management Practices (BMPs) Assess… | Drainage System Design | Stormwater Treatment/Reuse | Storage Facility Size Optimization | Runoff Management | Impact of Green Infrastructure (GI) on… | Average Runoff Assessment | Rainfall Inflow and Infiltration Mitiga… | Measures Planning Considering Overland… | Life Cycle Cost Accounting | Cost-Benefit Analysis | Capital and Operating Costs | Operating and Maintenance Costs | Energy Production and Consumption Estim… | Life Cycle Energy Use Analysis | Energy and Greenhouse Gas Emission Asso… | End-User Behavior Change Simulation | Technological Change Impact Simulation | Population and Urbanization Impact Simu… | Policy Impact Assessment | Supply-Demand Analysis | Water Resource Availability Analysis | Distribution System Simulation | Regional Water Allocation | Leakage Analysis | Abstraction from Hydrosystems | Customized Modeling for Different Users… | Alternative Water Infrastructure Options | Treatment Scheme Simulation | Best Management Practices (BMPs) Assess… | Drainage System Design | Stormwater Treatment/Reuse | Storage Facility Size Optimization | Runoff Management | Impact of Green Infrastructure (GI) on… | Average Runoff Assessment | Rainfall Inflow and Infiltration Mitiga… | Measures Planning Considering Overland… | Life Cycle Cost Accounting | Cost-Benefit Analysis | Capital and Operating Costs | Operating and Maintenance Costs | Energy Production and Consumption Estim… | Life Cycle Energy Use Analysis | Energy and Greenhouse Gas Emission Asso… | End-User Behavior Change Simulation | Technological Change Impact Simulation | Population and Urbanization Impact Simu… | Policy Impact Assessment |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Sobek Urban | The source uses the model name “Sobek-Urban”; the…[86] | 2017 calendar year[86] | A 2009 reference identifies SOBEK in the title “Flood…[86] | Hydraulic modeling; real-time control [86] | Catchment to neighborhood groups; seconds and minutes [86] | Sobek Urban is identified as a model whose main use… | The source identifies the model as “Sobek-Urban,” an…[86] | The source identifies the model as “Sobek-Urban,” an…[86] | The source identifies the model as “Sobek-Urban,” an…[86] | The manual states that SOBEK modules can be selected…[49] | The source identifies the model as “Sobek-Urban,” an…[86] | The source identifies the model as “Sobek-Urban,” an…[86] | Sobek Urban is identified as one of the models whose… | no evidence found | Sobek Urban is identified as a model whose main use… | no evidence found | no evidence found | no evidence found | no evidence found | The source identifies the model as “Sobek-Urban,” an…[86] | no evidence found | The manual states that SOBEK modules can be selected…[49] | The source identifies the model as “Sobek-Urban,” an…[86] | Sobek Urban is identified as a model whose main use… | The source identifies the model as “Sobek-Urban,” an…[86] | The manual states that SOBEK modules can be selected…[49] | The source identifies the model as “Sobek-Urban,” an…[86] | The source identifies the model as “Sobek-Urban,” an…[86] | The source identifies the model as “Sobek-Urban,” an…[86] | The source identifies the model as “Sobek-Urban,” an…[86] | Sobek Urban is identified as a model whose main use… | The source identifies the model as “Sobek-Urban,” an…[86] | The source identifies the model as “Sobek-Urban,” an…[86] | The source identifies the model as “Sobek-Urban,” an…[86] | The manual states that SOBEK-Urban supports simple or…[49] | The manual states that SOBEK-Urban supports simple or…[49] | The manual states that SOBEK-Urban supports simple or…[49] | The manual states that SOBEK-Urban supports simple or…[49] | The manual states that SOBEK-Urban supports simple or…[49] | The manual states that SOBEK-Urban supports simple or…[49] | The manual states that SOBEK-Urban supports simple or…[49] | The manual states that SOBEK-Urban supports simple or…[49] | no evidence found | The manual states that SOBEK-Urban supports simple or…[49] | no evidence found | no evidence found | no evidence found | no evidence found | The manual states that SOBEK-Urban supports simple or…[49] | no evidence found | The manual states that SOBEK-Urban supports simple or…[49] | The manual states that SOBEK-Urban supports simple or…[49] | The manual states that SOBEK-Urban supports simple or…[49] | The manual states that SOBEK-Urban supports simple or…[49] | The manual states that SOBEK-Urban supports simple or…[49] | The manual states that SOBEK-Urban supports simple or…[49] | The manual states that SOBEK-Urban supports simple or…[49] | The manual states that SOBEK-Urban supports simple or…[49] | The manual states that SOBEK-Urban supports simple or…[49] | The manual states that SOBEK-Urban supports simple or…[49] | The manual states that SOBEK-Urban supports simple or…[49] | The manual states that SOBEK-Urban supports simple or…[49] | The manual states that SOBEK-Urban supports simple or…[49] |
| Aquacycle | Aquacycle is identified in a 2005 user guide as… | 2000[26][86] | no evidence found | On-site wastewater treatment units reduce imported…[100] | no evidence found | A 2010 article reports “Applicability of Aquacycle… | A 2010 article reports “Applicability of Aquacycle… | no evidence found | no evidence found | no evidence found | no evidence found | Aquacycle mandates division of the study area into… | A 2010 article reports “Applicability of Aquacycle… | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | In the Greater Athens application, Aquacycle was…[76] | Aquacycle is identified as an earlier… | In the Greater Athens application, Aquacycle was…[76] | Aquacycle is identified as an earlier… | Aquacycle is identified as an earlier… | A 2010 article reports “Applicability of Aquacycle… | Aquacycle is identified as an earlier… | Aquacycle is identified as an earlier… | Aquacycle is identified as an earlier… | no evidence found | no evidence found | Aquacycle is identified as an earlier… | On-site wastewater treatment units reduce imported…[100] | Hydro Planner is capable of developing regional water… | no evidence found | no evidence found | no evidence found | no evidence found | For household occupancy less than or equal to 7 when…[26] | no evidence found | On-site wastewater treatment units reduce imported…[100] | no evidence found | no evidence found | On-site wastewater treatment units reduce imported…[100] | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | For household occupancy less than or equal to 7 when…[26] | For household occupancy less than or equal to 7 when…[26] | For household occupancy less than or equal to 7 when…[26] | For household occupancy less than or equal to 7 when…[26] | For household occupancy less than or equal to 7 when…[26] | no evidence found | For household occupancy less than or equal to 7 when…[26] | For household occupancy less than or equal to 7 when…[26] | For household occupancy less than or equal to 7 when…[26] | no evidence found | no evidence found | For household occupancy less than or equal to 7 when…[26] |
| Hydro Planner | Hydro Planner is documented in 2005 as a linked…[86] | 2001 | no evidence found | no evidence found | no evidence found | no evidence found | Hydro Planner is capable of developing regional water… | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | The review distinguishes Hydro Planner from the other…[98] | no evidence found | The review distinguishes Hydro Planner from the other…[98] | no evidence found | The review distinguishes Hydro Planner from the other…[98] | no evidence found | The review distinguishes Hydro Planner from the other…[98] | The review distinguishes Hydro Planner from the other…[98] | The review distinguishes Hydro Planner from the other…[98] | The review distinguishes Hydro Planner from the other…[98] | The review distinguishes Hydro Planner from the other…[98] | The review distinguishes Hydro Planner from the other…[98] | no evidence found | The review distinguishes Hydro Planner from the other…[98] | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | Hydro Planner is capable of developing regional water… | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | A 2012 record concerns “Representing wastewater…[80] | A 2012 record concerns “Representing wastewater…[80] | no evidence found | The review distinguishes Hydro Planner from the other…[98] | no evidence found | The review distinguishes Hydro Planner from the other…[98] | no evidence found | The review distinguishes Hydro Planner from the other…[98] | no evidence found | The review distinguishes Hydro Planner from the other…[98] | The review distinguishes Hydro Planner from the other…[98] | The review distinguishes Hydro Planner from the other…[98] | The review distinguishes Hydro Planner from the other…[98] | The review distinguishes Hydro Planner from the other…[98] | The review distinguishes Hydro Planner from the other…[98] | no evidence found | The review distinguishes Hydro Planner from the other…[98] | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| WaterCress | WaterCress is identified as an emerging integrated…[103] | 2002 | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | WaterCress considers the wastewater treatment plant… | WaterCress evaluates a range of conventional and… | WaterCress evaluates a range of conventional and… | WaterCress evaluates a range of conventional and… | WaterCress evaluates a range of conventional and… | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | WaterCress includes 18 icons representing…[37] | WaterCress includes 18 icons representing…[37] | WaterCress includes 18 icons representing…[37] | WaterCress includes 18 icons representing…[37] | WaterCress includes 18 icons representing…[37] |
| Water Balance Model (WBM) | The page describes WBM as “a scalable gridded global…[55] | 2004 | no evidence found | The page describes “the first fully open-source” WBM…[55] | The page describes WBM as “a scalable gridded global…[55] | In WBMplus irrigation, each grid cell is partitioned…[24] | In WBMplus irrigation, each grid cell is partitioned…[24] | WBMplus Regional was developed specifically for…[24] | WBMplus Regional was developed specifically for…[24] | The Water Balance Model powered by QUALHYMO is…[65] | In WBMplus irrigation, each grid cell is partitioned…[24] | no evidence found | no evidence found | WBM requires continuous rainfall data at any time…[28] | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | The source states that QUALHYMO can simulate water…[65] | WBM models all three components of an integrated…[28] | The Water Balance Model powered by QUALHYMO is…[65] | The Water Balance Model powered by QUALHYMO is…[65] | The source states that QUALHYMO can simulate water…[65] | The source states that QUALHYMO can simulate water…[65] | The source states that QUALHYMO can simulate water…[65] | Users can select climate data from British Columbia…[71] | The Water Balance Model powered by QUALHYMO is…[65] | The Water Balance Model powered by QUALHYMO is…[65] | WBM models all three components of an integrated…[28] | In WBMplus irrigation, each grid cell is partitioned…[24] | In WBMplus irrigation, each grid cell is partitioned…[24] | WBM uses a grid-cell representation: each grid cell…[39] | The Water Balance Model powered by QUALHYMO is…[65] | The Water Balance Model powered by QUALHYMO is…[65] | In WBMplus irrigation, each grid cell is partitioned…[24] | no evidence found | The page describes “the first fully open-source” WBM…[55] | The WBM model family branched into models for…[24] | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | The source states that QUALHYMO can simulate water…[65] | The source states that QUALHYMO can simulate water…[65] | The source states that QUALHYMO can simulate water…[65] | The source states that QUALHYMO can simulate water…[65] | The source states that QUALHYMO can simulate water…[65] | The source states that QUALHYMO can simulate water…[65] | The source states that QUALHYMO can simulate water…[65] | The WBM model family branched into models for…[24] | The page identifies WBM descendants and related…[24] | The page identifies WBM descendants and related…[24] | The page identifies WBM descendants and related…[24] |
| Urban Cycle | The source names Urban Cycle as an integrated urban… | 2005  | no evidence found | UrbanCycle is identified in a 2005 reference titled…[86] | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | UrbanCycle allows users to create precipitation and…[84] | UrbanCycle allows users to create precipitation and…[84] | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | UrbanCycle can model stormwater peak flows with…[98] | no evidence found | UrbanCycle can model stormwater peak flows with…[98] | UrbanCycle can model stormwater peak flows with…[98] | UrbanCycle can model stormwater peak flows with…[98] | UrbanCycle can model stormwater peak flows with…[98] | UrbanCycle can model stormwater peak flows with…[98] | UrbanCycle can model stormwater peak flows with…[98] | UrbanCycle can model stormwater peak flows with…[98] | UrbanCycle can model stormwater peak flows with…[98] | UrbanCycle can model stormwater peak flows with…[98] | UrbanCycle can model stormwater peak flows with…[98] | UrbanCycle can model stormwater peak flows with…[98] | UrbanCycle can model stormwater peak flows with…[98] | UrbanCycle can model stormwater peak flows with…[98] | no evidence found | no evidence found | no evidence found | no evidence found | Urban Cycle was first developed in 2005 by Hardy et… | Urban Cycle was first developed in 2005 by Hardy et… | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | Urban Cycle was first developed in 2005 by Hardy et… | no evidence found | Urban Cycle was first developed in 2005 by Hardy et… | Urban Cycle was first developed in 2005 by Hardy et… | Urban Cycle was first developed in 2005 by Hardy et… | Urban Cycle was first developed in 2005 by Hardy et… | Urban Cycle was first developed in 2005 by Hardy et… | Urban Cycle was first developed in 2005 by Hardy et… | Urban Cycle was first developed in 2005 by Hardy et… | Urban Cycle was first developed in 2005 by Hardy et… | Urban Cycle was first developed in 2005 by Hardy et… | Urban Cycle was first developed in 2005 by Hardy et… | Urban Cycle was first developed in 2005 by Hardy et… | Urban Cycle was first developed in 2005 by Hardy et… | Urban Cycle was first developed in 2005 by Hardy et… |
| Urban Volume and Quality (UVQ) | The source identifies UVQ through the cited work…[101] | 2005[82] | The source identifies UVQ through the cited work…[101] | The source identifies UVQ through the cited work…[101] | The page cites sources for UVQ and separately lists…[84] | The page cites sources for UVQ and separately lists…[84] | The page cites sources for UVQ and separately lists…[84] | UVQ calibration changed wastewater-generation…[91] | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | UVQ performs water-balance and contaminant-balance…[91] | UVQ performs water-balance and contaminant-balance…[91] | UVQ calibration changed wastewater-generation…[91] | UVQ calibration changed wastewater-generation…[91] | UVQ calibration changed wastewater-generation…[91] | UVQ calibration changed wastewater-generation…[91] | UVQ calibration changed wastewater-generation…[91] | UVQ was used to simulate six source-management…[91] | no evidence found | no evidence found | UVQ has pre-cutoff references describing simulation… | no evidence found | no evidence found | The page states that models such as UVQ were able to… | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | For the Port Vila application, UVQ enabled daily…[38] | For the Port Vila application, UVQ enabled daily…[38] | For the Port Vila application, UVQ enabled daily…[38] | For the Port Vila application, UVQ enabled daily…[38] | For the Port Vila application, UVQ enabled daily…[38] | For the Port Vila application, UVQ enabled daily…[38] | For the Port Vila application, UVQ enabled daily…[38] | The page states that models such as UVQ were able to… | no evidence found | no evidence found | UVQ has pre-cutoff references describing simulation… |
| MIKE URBAN | no evidence found | 2007  | Danish Hydrological Institute (DHI)  | no evidence found | Neighborhood to region; sub-hourly  | no evidence found | no evidence found | no evidence found | MIKE URBAN 2012 included catchment delineation from…[57] | no evidence found | MIKE URBAN 2012 included catchment delineation from…[57] | The source documents water-demand calculation at…[70] | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | The MIKE by DHI suite is described as supporting true…[57] | no evidence found | no evidence found | no evidence found | The page identifies MIKE URBAN as the predecessor of…[61] | The source documents water-demand calculation at…[70] | no evidence found | no evidence found | no evidence found | The page identifies MIKE URBAN as the predecessor of…[61] | The page identifies MIKE URBAN as the predecessor of…[61] | The MIKE by DHI suite is described as supporting true…[57] | The MIKE by DHI suite is described as supporting true…[57] | no evidence found | The source documents water-demand calculation at…[70] | no evidence found | no evidence found | no evidence found | MIKE URBAN independently (in parallel) simulates…[84] | no evidence found | MIKE URBAN independently (in parallel) simulates…[84] | MIKE URBAN independently (in parallel) simulates…[84] | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | MIKE URBAN independently (in parallel) simulates…[84] | no evidence found | no evidence found | no evidence found | MIKE URBAN covers wastewater leakage analysis and… | MIKE URBAN covers wastewater leakage analysis and… | no evidence found | no evidence found | no evidence found | MIKE URBAN covers wastewater leakage analysis and… | MIKE URBAN covers wastewater leakage analysis and… | MIKE URBAN independently (in parallel) simulates…[84] | MIKE URBAN independently (in parallel) simulates…[84] | no evidence found | MIKE URBAN covers wastewater leakage analysis and… |
| Urban Water Optioneering Tool (UWOT) | no evidence found | 2008 | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | UWOT covers transmission and distribution of water in… | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | 1/1/1980 to 31/12/1999 (1980,1999)[34] | no evidence found | UWOT is a documented decision support tool for…[77] | UWOT can operate in assessment and optimisation modes.…[27] | UWOT can operate in assessment and optimisation modes.…[27] | UWOT can operate in assessment and optimisation modes.…[27] | UWOT can operate in assessment and optimisation modes.…[27] | no evidence found | UWOT can operate in assessment and optimisation modes.…[27] | UWOT can operate in assessment and optimisation modes.…[27] | no evidence found | no evidence found | no evidence found | UWOT can operate in assessment and optimisation modes.…[27] | no evidence found | no evidence found | UWOT covers transmission and distribution of water in… | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | UWOT supports user-configured assessment of…[27] | no evidence found | UWOT is a documented decision support tool for…[77] | UWOT supports user-configured assessment of…[27] | UWOT supports user-configured assessment of…[27] | UWOT supports user-configured assessment of…[27] | UWOT supports user-configured assessment of…[27] | no evidence found | UWOT supports user-configured assessment of…[27] | UWOT supports user-configured assessment of…[27] | no evidence found | no evidence found | no evidence found | UWOT supports user-configured assessment of…[27] |
| City Water Balance (CWB) | The model is named City Water Balance model (CWB).[88] | 2010 | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | City Water Balance was developed to demonstrate…[45] | no evidence found | no evidence found | no evidence found | no evidence found | City Water Balance was developed to demonstrate…[45] | City Water Balance was developed to demonstrate…[45] | no evidence found | no evidence found | City Water Balance was developed to demonstrate…[45] | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | CWB explores green roofs, rainwater harvesting… | no evidence found | no evidence found | no evidence found | no evidence found | CWB explores green roofs, rainwater harvesting… | City Water Balance (CWB) was first developed in 2010… | no evidence found | no evidence found | The source explicitly connects CWB's water-management…[88] |
| DAnCE4Water | no evidence found | 2011  | no evidence found | no evidence found | no evidence found | Dance4Water is based on the Virtual Infrastructure…[84] | Dance4Water is based on the Virtual Infrastructure…[84] | DAnCE4Water is documented as a strategic planning…[50] | Dance4Water is based on the Virtual Infrastructure…[84] | Dance4Water is based on the Virtual Infrastructure…[84] | Dance4Water is based on the Virtual Infrastructure…[84] | no evidence found | no evidence found | The source discusses “water infrastructure” and its…[41] | no evidence found | By 2014, UrbanBEATS, the successor model associated…[69] | no evidence found | no evidence found | no evidence found | By 2014, UrbanBEATS, the successor model associated…[69] | DAnCE4Water is documented as a strategic planning…[50] | no evidence found | By 2014, UrbanBEATS, the successor model associated…[69] | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | DAnCE4Water is documented as a strategic planning…[50] | no evidence found | no evidence found | no evidence found | The source reports that an increase in rainfall…[29] | The source reports that an increase in rainfall…[29] | The source reports that an increase in rainfall…[29] | The source reports that an increase in rainfall…[29] | The source reports that an increase in rainfall…[29] | The source reports that an increase in rainfall…[29] | no evidence found | no evidence found | The source reports that an increase in rainfall…[29] | no evidence found | The source reports that an increase in rainfall…[29] | no evidence found | The source reports that an increase in rainfall…[29] | no evidence found | The source reports that an increase in rainfall…[29] | The source reports that an increase in rainfall…[29] | The source reports that an increase in rainfall…[29] | The source reports that an increase in rainfall…[29] | The source reports that an increase in rainfall…[29] | The source reports that an increase in rainfall…[29] | The source reports that an increase in rainfall…[29] | The source reports that an increase in rainfall…[29] | The source reports that an increase in rainfall…[29] | The source reports that an increase in rainfall…[29] | The source reports that an increase in rainfall…[29] | The source reports that an increase in rainfall…[29] | no evidence found | no evidence found | no evidence found |
| WMOST | The model is identified as WMOST, expanded as the…[43] | 2013[78] | no evidence found | no evidence found | WMOST is spatially lumped and operates with a daily or…[30] | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | The guide states that WMOST is a public-domain…[78] | no evidence found | WMOST considers operational and maintenance cost and… | no evidence found | no evidence found | The guide states that WMOST is a public-domain…[78] | The guide states that WMOST is a public-domain…[78] | The guide states that WMOST is a public-domain…[78] | no evidence found | The guide states that WMOST is a public-domain…[78] | The guide states that WMOST is a public-domain…[78] | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | WMOST calculates an optimal solution from user inputs…[44] | no evidence found | WMOST considers operational and maintenance cost and… | no evidence found | no evidence found | The source explicitly identifies several WMOST…[72] | WMOST is implemented using Excel as the interface…[68] | WMOST is implemented using Excel as the interface…[68] | no evidence found | The source explicitly identifies several WMOST…[72] | The source explicitly identifies several WMOST…[72] | no evidence found |
| WaterMet2 | no evidence found | 2014 | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | WaterMet2 requires manual trial-and-error…[73] | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | WaterMet2's risk assessment is partly external: the…[73] | no evidence found | no evidence found | no evidence found |

Across the rows, Sobek Urban and MIKE URBAN have the clearest hydraulic and drainage emphasis [86], whereas Aquacycle, Hydro Planner, WaterCress, and Water Balance Model (WBM) emphasize integrated balance, supply–demand, quantity/quality, reuse, or stormwater source-control functions [97][28]. Urban Cycle, Urban Volume and Quality (UVQ), Urban Water Optioneering Tool (UWOT), City Water Balance (CWB), DAnCE4Water, WMOST, and WaterMet2 extend the matrix toward continuous integrated modelling, contaminant/quality analysis, option and socio-technical scenario appraisal, optimization, and metabolism/energy assessment [31][42][32][93].

**Model basic-information rows**

| Model name | First developed year | Main developer | Core advantages (1–2 features) | Typical spatiotemporal scales |
|---|---|---|---|---|
| **Aquacycle** | **2000** as the initial development milestone in the documented Aquacycle–UVQ lineage; modifications are recorded for 2002 and 2006 [62]. | **Grace (G.) Mitchell**; eCRC is identified as distributor, while technical documentation associates the software with V. Grace Mitchell and CSIRO [54][58]. | Urban-water and rainwater-tank mass-balance simulation, including water-consumption prediction from multiple sources, stormwater, irrigation, indoor use and storage processes [54]. | **Spatial:** unit block, cluster and catchment. **Temporal:** daily, monthly and yearly; the documented Queensland study used unit-block/annual outputs and daily climate records from 1970–2009 [54]. |
| **WaterCress** | **Not established** in the supplied pre-cutoff manual; the manual describes the model and its operation but does not give a first-development year [25]. | **Not established** in the supplied manual; the expanded model name is Water Community Resource Evaluation and Simulation System [25]. | PC-based continuous time-series total-water-cycle modelling through node-and-link layouts; supports alternative layouts, multiple water sources and multiple objectives involving supply, flood mitigation and environmental enhancement [25]. | **Spatial:** rural or urban catchments, from an on-site dwelling or group of dwellings to regional and mixed-scale systems. **Temporal:** continuous equal steps of 1 day, 2 hours, 1 hour or 30 minutes; daily is the documented default [25]. |
| **Water Balance Model (WBM)** | **Not established.** The available record documents a 2002 upgrade programme and a planned Step 3 completion date of 1 February 2003, not the original development year [28]. | **CH2M HILL**; Lanarc appears as a participant in the later upgrade programme rather than the originating developer [28]. | Volume-based stormwater decision support that connects land-use planning with stormwater management; evaluates retention, detention, conveyance and source-control alternatives such as bioretention, infiltration, rainwater capture, green roofs and detention [28]. | **Spatial:** development or redevelopment sites, individual subcatchments and neighbourhoods, through watersheds or multi-land-use catchments. **Temporal:** continuous simulation with rainfall data supplied at any time increment; no single fixed native timestep is established in the available evidence [28]. |
| **Urban Volume and Quality (UVQ)** | **2000 as the earliest lineage milestone**, followed by UVQ-related modifications documented in 2002 and 2006; the first year of the separately branded UVQ implementation is not unambiguously distinguished [62]. | **V. G. Mitchell and C. Diaper, CSIRO Urban Water**; UVQ is also associated with CSIRO’s AISUWRS work [81][94]. | Daily total-urban-water-cycle and contaminant-balance modelling; tracks waterborne contaminants and evaluates conventional and non-conventional supply, stormwater and wastewater options [62][94]. | **Spatial:** lumped conceptual representations of urban allotments, neighbourhoods and study areas. **Temporal:** daily simulation [81][94]. |
| **MIKE URBAN** | **Not established** in eligible evidence. A 2008 version and 2011 service-pack records are documented, but these are release milestones rather than a first-development date [51][52]. | **Not established** in the supplied pre-cutoff evidence; the record identifies MIKE Urban as a package and MIKE Urban CS as covering stormwater and wastewater collection systems, but does not identify its originator [83]. | Network-focused modelling for urban pipes, manholes and stormwater/wastewater collection systems; supports large-network/GIS handling and reliability analysis of pressure, flow and water-quality thresholds [51][52][83]. | **Spatial:** urban collection and distribution networks. **Temporal:** not specified in the available admissible evidence [51][83]. |
| **WMOST** | **2013**, the earliest documented WMOST 1.0 release milestone; this should not be read as proof that no earlier prototype existed [47][60]. | **United States Environmental Protection Agency (EPA)** [60]. | Excel-based decision support that optimizes cost-effective water-quantity and water-quality management alternatives; later documentation supports least-cost analysis, cost-benefit exploration and trade-off/Pareto analysis [60][78]. | **Spatial:** local or small watershed, represented in a spatially lumped form. **Temporal:** daily or monthly [78]. |
| **WaterMet2** | **2014**, the earliest documented TRUST project report and paper in the supplied evidence; the evidence does not establish a prior prototype year [59][106]. | **TRUST project team**, documented by K. Behzadian, Z. Kapelan, V. Govindarajan, H. Brattebø, S. Sægrov, E. Rozos and C. Makropoulos; no single originating developer is singled out [59][62]. | Integrated conceptual mass-balance modelling of supply, wastewater, stormwater and resource recovery, with water, material, energy, greenhouse-gas, cost and sustainability-performance accounting [89][102]. | **Spatial:** indoor-area, local-area, subcatchment-area and city-area levels—four spatial scales. **Temporal:** daily; the Oslo demonstration used a 30-year horizon beginning in 2011 [62][102]. |
| WaterCress | Not established; the supplied manual names the model but gives no development year [46] | Not established; SelectWater is documented as the host/distribution source, not as the confirmed originator [46][67] | Household water-and-power self-sufficiency assessment; linked-node simulation of storage, demand, drainage, reuse/quality, reliability and costs [46] | House-level linked nodes; a separate comparison record describes multiple-catchment screening; daily, monthly, hourly and annual inputs or outputs are documented [46][94] |
| Water Balance Model (WBM) | **2003** for the original British Columbia Water Balance Model decision-support tool; this is a documented development milestone for that urban lineage [65] | Water Balance Model Inter-Governmental Partnership; Jim Dumont is identified as its Engineering Applications Authority, but the principal originating developer is not isolated [65] | Runoff-based decision support connecting site source-control evaluation with stream-health assessment; continuous long-record simulation and scenario comparison through QUALHYMO [65] | Site-to-stream and watershed representation using long-term time series; the eligible urban source does not state a single native timestep [65] |
| MIKE URBAN | **≥2004**: a 2004 publication is the earliest supplied pre-cutoff evidence, but it does not prove the first development year [84] | DHI [66] | Two-level LID analysis—catchment screening and detailed network-based hydraulic assessment—with treatment modelling through ECO Lab [66] | Catchment-to-drainage-network scale; the supplied eligible evidence does not establish a typical temporal resolution or horizon [66][84] |
| Urban Water Optioneering Tool (UWOT) | **2008**, recorded as the initial release rather than definitively the first development year [64] | Not disclosed in the accessible product record; associated pre-cutoff publications name Makropoulos, Butler and collaborators, but do not establish one principal developer [64] | Integrated urban-water-cycle simulation that compares and ranks combinations of water-saving, recycling, treatment and drainage technologies using user-based criteria [64] | Appliance to house, neighbourhood and city scales; daily or hourly timesteps; scenarios spanning years to decades [64] |
| City Water Balance (CWB) | Not resolved; the first supplied publication evidence is **1 December 2010** [53] | SWITCH European Framework VI/City Water integrated knowledge-base project; Rae Mackay and Ewan Last are documented authors, not necessarily sole originators [53] | Rapid city-scale scoping of alternative water-management strategies; indicators cover demand, quality, energy consumption and simplified life-cycle cost [53] | City scale, with Birmingham as the initial application; the supplied evidence does not state a model-wide temporal resolution or horizon [53] |
| WMOST | **2013**, the release year of Version 1; the prototype-development date is not separately stated [78] | U.S. EPA Office of Research and Development, with Abt Associates contributing to Version 2 development [32][85] | User-friendly least-cost linear-programming optimization; integrated screening of water supply, wastewater, stormwater, LID/GI and land-conservation options with cost-benefit and trade-off analysis [32] | Local or small watershed, spatially lumped; the Version 3 guide describes one basin and one reach, with daily or monthly modelling and at least hourly SUSTAIN inputs for some stormwater calculations [32][78][75] |
| **Aquacycle** | **2001** is the earliest documented development/publication milestone; the original study states that the model was developed to represent urban water flows [35][96]. | **V. Grace Mitchell/CSIRO** is the principal documented software author; R. G. Mein and T. A. McMahon co-authored the original study, so sole originator attribution remains uncertain [35][58]. | Represents the urban water supply, stormwater and wastewater systems as one water balance; evaluates decentralised reuse and alternative water-management scenarios [96][95]. | Unit-block, cluster and catchment scales, with a **daily timestep**; applications include Canberra, Greater Athens, Alexandria and other urban catchments [95][96][97]. |
| **Hydro Planner** | **2005** is the earliest documented development evidence; Hydro Planner Version 1 is subsequently identified as a **2007** regional-scale milestone [99][56]. | Developed through **CSIRO’s Water for a Healthy Country National Research Flagship**, with S. Maheepala and collaborating researchers; the prototype was linked to the eWater CRC E2 framework [99][56]. | Integrates water supply, wastewater, stormwater and natural-water systems for quantity-and-quality assessment; permits flexible coupling of component models and management options [99][56]. | Regional, metropolitan and local-government applications using user-defined basins, catchments and subcatchments; spatially lumped node-link representation with a **daily timestep**, while linked components may use monthly or annual data [56][90]. |
| **WaterCress** | **1995**, according to the WaterSelect description of the model’s inception; the independent 2005 evaluation does not verify this date [92][36]. | **Not definitively resolved.** Cresswell is associated with the platform, while Clark, Pezzaniti and Cresswell are cited for a 2002 model description; David Trebilcock authored the 2005 evaluation but is not identified as the developer [97][36]. | A PC-based platform for designing and testing systems using multiple, including unconventional, water sources; layouts can be modified relatively quickly and the platform can incorporate generic or project-specific hydrological models [92][36]. | The urban-water description reports **lot-to-regional** operation with a **daily water-balance timestep**; the evaluated groundwater-slice component operates transiently at daily or hourly steps [98][36]. |
| **Water Balance Model (WBM)** | **Unknown in the eligible evidence shown.** The apparent 2001 record identifies “the water balance model (Aquacycle),” which should not be transferred to the separately listed WBM entity [35]. | **Unknown.** No admissible evidence shown here establishes a developer for the roster’s Water Balance Model (WBM); the available record concerns Aquacycle [35]. | **Not documented for this WBM entity.** Aquacycle’s integrated supply–stormwater–wastewater features are not evidence for WBM [35]. | **Not documented for this WBM entity.** The daily timestep and urban-catchment scales in the cited record belong to Aquacycle [35]. |
| **Urban Cycle** | **2005** is the earliest documented named-model publication; the model was still under development in the 2006 review [87][98]. | M. J. Hardy, G. Kuczera and P. J. Coombes are the documented developers/authors; the model is associated with the University of Newcastle, Australia [87][84]. | Integrates the whole urban water cycle through hierarchical networks across scales; represents stormwater peak flows and allows assessment of options such as local treatment and rainwater harvesting [87][98]. | From **single lot to cluster** and higher hierarchical urban scales; continuous simulation with **subdaily/sub-hourly** resolution. The reviewed version had no water-quality or groundwater representation [98][87]. |
| **Urban Volume and Quality (UVQ)** | **2005**, supported by the UVQ publication and user-manual record [79][97]. | V. G. Mitchell and C. Diaper, associated with **CSIRO, Australia**, are the documented developers [82][84]. | Extends the Aquacycle-type balance with contaminant-flux and water-quality modelling; assesses water and contaminant impacts of urban-development scenarios [82][95][97]. | Nested urban spatial scales, reported in the source as **Pr, Ne, GNe and Cit.**, with a **daily** time scale [82][84]. The 2011 Glenroy application covered a 425-ha subcatchment, which is a case-study extent rather than necessarily the model’s native limit [91]. |
| **Urban Water Optioneering Tool (UWOT)** | **Unknown.** Pre-cutoff evidence identifies UWOT through work cited from 2008 onward but does not establish the first development year [95][105]. | **Not established in the evidence shown.** Makropoulos and colleagues are associated with the cited UWOT work, but the supplied spans do not prove a sole originating developer [95][105]. | Examines interactions among urban water-cycle components; evaluates sustainability through indicators covering water, runoff, wastewater, energy, cost, reliability and social acceptability [95][105]. | **Not documented in the eligible evidence shown** for a definitive native spatial extent and timestep; its documented role is urban development and decentralised water-cycle option assessment [95][105]. |
| **City Water Balance (CWB)** | **Not definitively established.** **2010** is the earliest documented CWB scoping-model publication in the supplied evidence, rather than an explicitly stated first-development year . | Developed within the EU-funded **SWITCH City Water knowledge-base/decision-support system**, associated with the University of Birmingham and Rae Mackay and Ewan Last . | Rapidly scopes alternative city water-management strategies while integrating natural systems, water quality, energy consumption and simplified whole-life cost . | City scale using neighbourhoods, unit blocks and subcatchments; the model is documented with a **daily timestep over decadal periods**. A separate thesis implementation reports a monthly timestep, so the temporal value is version or implementation dependent [45]. |

**Aquacycle and the UVQ lineage**

Aquacycle has a direct pre-cutoff relationship to urban-water-model research. A 2010 study used it for urban water-cycle analysis in the Goonja drainage basin, with 2006 rainfall and discharge data for calibration and 2007 data for verification; the study reports a verification correlation of \(r=0.97\) for observed data and \(r=0.84\) after calibration in the reported comparison [33]. A 2009 rainwater-tank study selected Aquacycle as the most relevant programme from a short list, assigning it a weighted suitability score of **4.52** and a score of **5** for several criteria, including research fit, data requirements, model classification, spatial and temporal output resolution and modeller expertise [54]. These applications establish strong relevance to the IUWMM literature review, although the evidence is weighted toward rainwater tanks, runoff and water-saving efficiency rather than every urban-water sector.

**WaterCress**

WaterCress is described as a continuous time-series, total-water-cycle model for natural and constructed systems. It reports flows and storages over the modelling period and compares performance with desired outcomes or alternative system layouts [25]. Nodes can represent catchments, towns, dams, treatment plants, aquifers, in-house demands, irrigation areas and pumps, while links route drainage or transfer water from supply-capable to demand-capable nodes [25]. The manual also describes an 18-node-type menu and node databases that can add, lose, modify or divert water quantities and qualities [74].

**Water Balance Model (WBM)**

The WBM represented here is the **CH2M HILL Water Balance Model**, a volume-based stormwater decision-support tool developed for the Greater Vancouver region of British Columbia [28]. The source describes it as serving educational, watershed-planning and site-design needs and as helping local governments integrate land-use planning with stormwater management [28]. This identity is retained rather than substituting a different generic or global “water balance model.”

**WMOST**

The documented Taunton case study covered the **220 km²** Wading–Threemile River Watershed in the Upper Taunton basin and used a **2002–2006** calibration period [60]. The reported screening calibration statistics were NSE **0.34**, \(R^2\) **0.50**, relative percent error **50.1%** and median bias **0.45 m³/s** [60]. In that case, infiltration basins were identified as the most cost-effective structural BMP among **nine** modelled BMPs, but the finding was preliminary and case-specific [60]. WMOST was also documented as a single-objective optimizer at that stage; a multi-objective version minimizing cost and pollutant load simultaneously was still described as under development [60]. These qualifications distinguish documented historical capability from a claim of unrestricted multi-objective optimization.

**MIKE URBAN**

The admissible pre-cutoff evidence places MIKE URBAN in the network-modelling portion of the urban-water model landscape. A December 2015 record identifies “MIKE Urban” as a distinct package and states that MIKE Urban CS models stormwater and wastewater collection systems [83]. A 2008-version record documents ArcGIS 9.2 and file-based geodatabase support, improved handling of large networks and external AutoCAD Civil 3D and Google Earth plug-ins [52]. A 2011 feature record documents reliability analysis for pressure, flow and water-quality results, including frequencies or durations of user-defined threshold exceedances [51].

**WaterMet2**

WaterMet2 links water supply, stormwater and wastewater subsystems and represents raw-water resources, treatment works, service reservoirs, supply conduits, trunk mains, distribution mains, sewer systems, wastewater-treatment works and receiving waters [106]. Its mass-balance framework quantifies water, material, chemical, energy and greenhouse-gas fluxes and supports costs, environmental impacts and sustainability indicators [89][102]. The model can also represent centralised and decentralised reuse, including rainwater harvesting and greywater recycling [102].

**Basic-information coverage**

**Basic-information rows supported by this evidence group**

**Aquacycle**

Aquacycle is directly relevant to an integrated urban-water literature review because it is documented as an Australian urban water-balance model with water-management options, rather than as a single-purpose drainage model. The retained application evidence identifies Mitchell et al. (2001), a Woden Valley, Canberra application, and options for modifying the urban water balance [82]. A separate pre-cutoff history records a beta release in **2000**, review in **2004**, and Version 1 release in **2005**; Version 1.0.0 was released and licensed on **8 March 2005** and replaced the beta [26]. Accordingly, 2000 is used as the earliest documented milestone, while 2005 is retained as the first full-version release.

**Water Balance Model (WBM)**

**Urban Volume and Quality (UVQ)**

The model’s contaminant treatment requires qualification. The contaminant-balance component is described as a prototype that was not fully functional [58]; another pre-cutoff description reports conservative contaminant calculations without conversion or degradation in existing infrastructure and without representing temporal water-quality variation [91]. UVQ outputs include water balances, contaminant loads, runoff, wastewater, groundwater, recharge and flooding indicators, and the model can link to pipe-leakage and groundwater-flow models [81]. Those linked analyses should therefore be understood as coupled or externally linked support rather than automatically as native functionality.

**MIKE URBAN**

The documented Gold Coast application demonstrates a catchment-scale use rather than a universal model limit: Birdlife Park covered **8.5 ha**, Alextown **1.8 ha**, and Gumbeel **1.2 ha**, all urban residential catchments in Southeast Queensland [40]. The retained sources do not specify one universal timestep. A pre-cutoff MIKE Urban instruction page, last modified **18 May 2016**, documents ASCII time-series import for water level, discharge, rainfall depth and rainfall intensity; the instructions apply through MIKE Urban 2007 Service Pack 1, while a later Service Pack 2 dialog was not yet documented on that page [48]. Imported series can be saved as dfs0 files and linked as model boundary conditions [48].

The application evidence also demonstrates why scale and parameter-transfer claims need qualification. A Southeast Queensland study developed a field-investigation methodology and an empirical conversion equation for MIKE URBAN build-up parameters where monitoring data were unavailable [40]. It found that regional inputs differed substantially from defaults and that the **Reduction Factor** was most sensitive for peak flow and total runoff volume, whereas **Build-up Rate** was most sensitive for TSS load [40]. Thus, MIKE URBAN’s relevance extends beyond hydraulic simulation to water-quality parameterization and urban-planning support, but results remain dependent on regional characteristics and version-specific modules. A February 2018 description additionally presents MIKE URBAN as commercial software commonly used to run SWMM, with added urban water-supply planning and management functions [104]. A 2021 page that cites a 2012 DHI manual is post-cutoff and is used only as an excluded source lead, not as independent historical evidence [63].

**WMOST**

## Table 2. Model Application Capability Comparison Table

**The matrix retains the requested orientation.** All 13 models appear as columns, in the requested order. The 29 functional rows are divided into four category panels, giving 117 Drinking Water Management intersections, 117 Stormwater Management intersections, 91 Cost and Energy intersections, and 52 Social and Policy intersections.

**The marks describe documented functionality.** A positive mark means the function exists at the model’s stated level of representation; it is not a claim that every model implements it with equal detail. In particular, routed water volumes, hydraulic pressures, treatment-removal assumptions and treatment-process kinetics are different representations.

| Mark | Meaning |
|---|---|
| Y | Function directly described or demonstrated within the named model |
| P | Partial, simplified, scenario-input or narrower implementation |
| P-L | Partial support through an explicitly named linked model or extension |
| N | Function explicitly excluded from the documented core/version |
| U | Undocumented in the cited pre-cutoff feature evidence; not a finding of absence |

**Compound rows need consistent interpretation.** “Stormwater Treatment/Reuse” includes either treatment or reuse, so a documented harvesting-and-supply application can receive Y without a detailed treatment-kinetics module. “Energy Production and Consumption Estimation,” by contrast, receives P where only consumption is clearly quantified. For customization, P identifies configurable components or user classes, not an assumption that separate farmer, designer and planner interfaces exist.

**The scope remains urban but connected.** Integrated Urban Water Management coordinates water supply, wastewater and stormwater. Broader river-basin allocation belongs to Integrated Water Resources Management, within which urban management operates. This distinction particularly affects the regional-allocation and hydrosystem-abstraction rows. [17]

### Drinking Water Management: nine requested applications

| Functional application | Sobek Urban [1] | Aquacycle [3] | Hydro Planner [4] | WaterCress [5] | WBM [6] |
| --- | --- | --- | --- | --- | --- |
| Supply-Demand Analysis | U | Y | Y | Y | U |
| Water Resource Availability Analysis | U | U | Y | Y | U |
| Distribution System Simulation | U | U | U | U | U |
| Regional Water Allocation | U | U | Y | U | U |
| Leakage Analysis | U | P | U | U | U |
| Abstraction from Hydrosystems | U | U | P | Y | U |
| Customized Modeling for Different Users (farmers/designers/planners) | U | P | P | U | P |
| Alternative Water Infrastructure Options | U | Y | Y | Y | U |
| Treatment Scheme Simulation | U | P | Y | U | U |

| Functional application | Urban Cycle [12] | UVQ [7] | MIKE URBAN [8] | UWOT [3] |
| --- | --- | --- | --- | --- |
| Supply-Demand Analysis | Y | Y | P | Y |
| Water Resource Availability Analysis | P | N | U | U |
| Distribution System Simulation | P | U | Y | U |
| Regional Water Allocation | P-L | P-L | U | U |
| Leakage Analysis | U | U | U | U |
| Abstraction from Hydrosystems | U | U | U | U |
| Customized Modeling for Different Users (farmers/designers/planners) | P | P | U | P |
| Alternative Water Infrastructure Options | Y | Y | U | Y |
| Treatment Scheme Simulation | U | Y | U | P |

| Functional application | CWB [3] | DAnCE4Water [15] | WMOST [10] | WaterMet2 [16] |
| --- | --- | --- | --- | --- |
| Supply-Demand Analysis | Y | P | Y | Y |
| Water Resource Availability Analysis | P | U | Y | Y |
| Distribution System Simulation | U | P-L | P | Y |
| Regional Water Allocation | U | U | P | P |
| Leakage Analysis | Y | U | Y | Y |
| Abstraction from Hydrosystems | Y | U | Y | P |
| Customized Modeling for Different Users (farmers/designers/planners) | P | P | P | P |
| Alternative Water Infrastructure Options | Y | Y | Y | Y |
| Treatment Scheme Simulation | Y | U | P | Y |

**Additional model-specific support matters.** Hydro Planner’s treatment, recycling and multiple-source marks also use its 2013 tested-feature report [14]. Aquacycle’s integrated demand/runoff and reuse functions are demonstrated in the Greater Athens application [18]. The WMOST marks combine its 2013 infrastructure and demand-management specification with the pre-cutoff v3 guide [13].

### Supply–demand analysis is not resource adequacy

**Hydro Planner, WMOST and WaterMet2 connect supply constraints to demand.** Hydro Planner explicitly quantifies the spatial and temporal distribution of existing and potential sources, then links supply-side and demand-side analysis. WMOST identifies the least-cost practices that meet human demand alongside streamflow or other watershed objectives. WaterMet2 calculates demand remaining after local recovery and propagates it through resources, treatment works, reservoirs and distribution routes. [4][10][11]

**Their decision mechanisms are different.** Hydro Planner is an integration environment whose results depend on selected component models and operating rules. WMOST is an optimizer: management choices and capacities are decision variables subject to goals and physical constraints. WaterMet2 is principally a simulation model whose intervention strategies can subsequently be compared using sustainability indicators and multi-criteria decision analysis. Calling all three “integrated” should not obscure the difference between connecting models, optimizing a portfolio and simulating a specified portfolio.

**Aquacycle and UVQ answer a different first question.** They calculate urban water requirements and the effects of local recycling, harvesting and changes in consumption. Aquacycle’s daily balance includes mains water, stormwater runoff and wastewater emissions; UVQ adds contaminant flows and treatment assumptions. This is valuable for estimating how much centralized supply a development would require, but it is not equivalent to estimating whether a finite external reservoir system can provide that amount. [3]

**UVQ provides the clearest boundary example.** CSIRO’s documented estate-level formulation assumes an infinite tap-water source and calculates the amounts of water of different qualities required by the estate. Accordingly, UVQ receives Y for demand calculation but N for finite-resource availability in that formulation. That combination is deliberate: demand can be calculated correctly even when source scarcity is outside the model boundary. [7]

**WaterCress evaluates a finite local resource.** Its Parafield implementation simulates rainfall–runoff, capture, aquifer storage and customer supply, including minimum storage, aquifer injection and storage-depreciation scenarios. Its Y for resource availability therefore concerns the harvesting-and-aquifer system represented in that application, rather than a universal regional water-rights model. [5]

**CWB combines internal and external boundaries.** It represents groundwater and surface-water systems within the city more explicitly than several earlier scoping tools, including borehole abstraction. Its mains supply nevertheless enters from outside the system boundary, with aggregate leakage, energy, cost and quality parameters. The resulting P for overall resource availability recognizes a useful local natural-resource representation without treating externally imported mains water as a fully modeled supplying basin. [3]

### Distribution simulation must be read by resolution

**MIKE URBAN provides hydraulic network analysis.** DHI’s 2012 Advisor documentation explicitly describes checking hydraulic-simulation results, identifying supply/distribution deficiencies, and improving design and operation. This is the clearest model-specific support here for distribution-network diagnostics. Its relevant outputs concern hydraulic behavior, not merely the amount of imported water required by a neighborhood. [8]

**WaterMet2 provides simplified distribution routing.** Its supply system contains resources, water treatment works, service reservoirs and subcatchments, connected by supply conduits, trunk mains and distribution-network mains. The model allocates delivered subcatchment demand among local areas. Its Y therefore denotes an explicit distribution-system representation at strategic volume/capacity level; it should not be read as evidence of pipe-by-pipe pressure or transient calculations comparable to detailed distribution hydraulics. [11]

**Urban Cycle’s connectivity has structural restrictions.** The original model’s directed acyclic graph simplifies flow connections but restricts investigation of systems with multiple storages and multiple supply paths. Embedding WathNet5 produces UrbanNet, which supports more flexible recycling, harvesting and objective-based supply decisions. This distinction explains the P for original connectivity and P-L for allocation through the extension. Graddon demonstrated the extension using hypothetical configurations, rather than presenting those demonstrations as operating municipal systems. [12]

**DAnCE4Water’s distribution support is linked.** The December 2017 description identifies biophysical modules including EPANET and SWMM, rather than presenting a single native hydraulic engine as the entire platform. Its P-L consequently recognizes a documented modeling connection. WMOST’s P is narrower still: it represents distribution-related capacities and nonpotable delivery options, but not a spatially explicit pressure network. [15][10]

### Regional allocation and abstraction require different evidence

**Hydro Planner explicitly addresses regional allocation.** Its water-supply module links REALM, which represents sources, demand centers and transfer links and uses network linear programming to allocate water under specified rules at each time step. This is stronger evidence for the regional-allocation row than a general statement that a model includes water supply. [4]

**UVQ delegates allocation to TAWS.** In the CSIRO workflow, UVQ furnishes estate demands and output supplies; TAWS then models allocation across the region formed by those estates. The allocation mark is therefore P-L. Assigning native allocation to UVQ would incorrectly transfer the role of the linked model into the UVQ column. [7]

**WMOST optimizes a smaller management domain.** Its local/small-watershed system can vary surface- and groundwater pumping, interbasin imports and infrastructure capacities while meeting demand and streamflow constraints. This supports abstraction analysis and partial allocation capability, but the model’s lumped structure is not equivalent to a multi-reach regional rights-allocation network. WaterMet2’s allocation likewise concerns delivery among urban subareas rather than full basin-level allocation institutions. [10]

**Abstraction is not merely naming a source.** WMOST explicitly specifies surface- and groundwater pumping capacities and withdrawal time series. CWB explicitly models borehole abstraction, and WaterCress models aquifer storage and recovery. Hydro Planner and WaterMet2 include hydrosystem sources and their supply roles, but receive P where the cited descriptions establish a simplified source/supply operation rather than a detailed abstraction process. This distinction matters for questions about river depletion, well constraints or pumping impacts.

**Additional documented evidence**

- Aquacycle: beta 2000, v1 2005; Grace Mitchell [26]. Daily supply/stormwater/wastewater modelling spans block–catchment scales and reuse; water quality is not simulated [35][153][161][110].
- Hydro Planner: CSIRO/E2 (2005), seven linked city/regional modules and scenarios [99]; developmental, daily/monthly, groundwater absent, developer unresolved [98][122].
- WaterCress: Water Community Resource Evaluation and Simulation System; Clark/Cresswell, inception 1995 [25][124][92]. Node-based supply/storage/treatment/recycling, 2013 subdaily study, two quality classes and calibration limits [25][116][36].
- UVQ: CSIRO report (August 2000) documents an Aquacycle extension adding contaminant balance; evidence remains partial, with limited options and no porous roads or pavements [58][45].
- MIKE URBAN: only shown classification is post-cutoff (2026), hence unresolved . UWOT: only a 2008 appliance-library fragment is shown; provenance and capabilities remain unresolved [45]. Urban Cycle: 2005 Australian IUWM model covering supply, wastewater and stormwater; 6-minute, flow-only and limited options [45][98].
- CWB: daily city-scale clusters/unit blocks and alternatives; small/subdaily accuracy, multiple aquifers and central-system energy/cost are limited [45].
- WBM: WBM/WTM (1996), USGS (1999/2016), CH2M urban (2002) and UNH variants are distinct; do not merge [120][158][28][119]. Later open-source evidence is excluded [157].

- Water Balance Model (WBM): 1997 v1; Greenland Engineering et al.; daily budgets/controls, runoff, infiltration, storage and scenarios; developer/validation/cells ? [162][160].
- Urban Cycle: 2005 whole-cycle, continuous sub-daily hierarchy; Urban Developer (2011) is based on it, not standalone evidence [87][166].
- Urban Volume and Quality (UVQ): CSIRO/Mitchell–Diaper daily model, expanded from Aquacycle; three nested scales; cells incomplete [94][91][163].
- MIKE URBAN: DHI; pre-cutoff supply/drainage and hydrologic/hydraulic/water-quality evidence; cells incomplete [159][40].
- Urban Water Optioneering Tool (UWOT): 2008 WaND mass balance, technology library, metrics and GA selection; external 2011 land-use coupling [77][34].
- City Water Balance (CWB): 2010 SWITCH scoping tool; options/Birmingham case; developer/alias/cost ? [131][156].
- DAnCE4Water: Pre-cutoff spatial integration of urban development, infrastructure and socio-institutional change; Melbourne validation; originator/cells ? [41][164].
- WMOST: EPA v1 (2013)/v2 (2016); public-domain, lumped local-watershed optimizer, daily/monthly; quality/cells ? by version [30][32].
- WaterMet2: 2014 paper; four spatial scales, daily resolution, supply/demand/wastewater/recovery and five Oslo strategies; developer/cells ? [165].

For the separate basic-information and capability tables, pre-cutoff evidence identifies Aquacycle as developed by Grace Mitchell and as a continuous, integrated water-balance model linking supply, stormwater and wastewater, with unit-block, cluster and catchment spatial scales and daily, monthly and yearly temporal scales; the 2001 publication and 2010 application dates document use rather than a verified first-development year. [26][153][95][54][167][33] Capability marks should remain quantity-focused: Aquacycle supports reuse, rainwater-tank and scenario analysis, but does not simulate water quality [110], lacks short-term variability [100], can overestimate irrigation demand when unmet demand compounds to the trigger threshold, and can overestimate usage or hydrologic yield under its daily inflow–supply–spillage order [54]; unexplained results are linked to soil and irrigation parameters [45]. Unsupported treatment, fine-time, cost/energy and social-policy claims should therefore not be inferred in the horizontal comparison.

### Leakage, treatment and user customization

**Leakage accounting appears at several levels.** Aquacycle includes water lost through system leaks in its imported-water balance, supporting P for aggregate accounting. CWB explicitly includes time-dependent mains leakage and uses supply/leakage data in calibration. WMOST makes potable-distribution leak repair an investment option with costs and a maximum repairable fraction. WaterMet2 compares rehabilitation interventions and their effects on leakage and supply reliability. [1][3][10]

**WaterMet2 illustrates the integration benefit.** Its Oslo demonstration assumed initial leakage equal to 22% of total demand. One intervention increased annual pipeline rehabilitation from 1% to 2% of network length. The paper reports a 17% reduction in leakage amount relative to business as usual and a reported 2% increase in reliability, while also reporting increased wastewater generation and combined sewer overflows because more water reached users. This is a modeled cross-system effect, not evidence that rehabilitation universally increases sewer overflow. [16]

**Treatment marks do not imply process kinetics.** UVQ requires users to specify contaminant concentrations, loads and treatment performance, and assumes no degradation or conversion of the tracked contaminants. It can therefore compare treatment schemes through prescribed removal behavior without resolving all physical, chemical or biological transformations. CWB similarly assesses local treatment/recycling technologies through a scoping representation, while WMOST screens treatment capacities and their costs rather than replacing a treatment-plant process simulator. [1][3]

**Customization usually means configuration, not separate professions.** Hydro Planner allows component-model selection according to data and scale. UVQ allows changes to property characteristics and on-site practices. UWOT’s component library allows application conditions, operation and design to be modified. WMOST allows users to define water-user categories, available practices and management goals. Those are useful adaptations, but they support P rather than a blanket claim of specialized farmer, designer and planner versions. [4][1][10]

**The drinking-water judgment follows the question.** Use MIKE URBAN for hydraulic network diagnosis, Hydro Planner for linked regional allocation, WMOST for constrained management portfolios, and WaterMet2 for strategic cross-system consequences; use Aquacycle, UVQ, Urban Cycle, UWOT or CWB when the main question concerns local demand and servicing alternatives.

### Stormwater Management: nine requested applications

| Functional application | Sobek Urban [1] | Aquacycle [18] | Hydro Planner [14] | WaterCress [5] | WBM [6] |
| --- | --- | --- | --- | --- | --- |
| Best Management Practices (BMPs) Assessment | U | P | P | P | Y |
| Drainage System Design | P | U | P | U | P |
| Stormwater Treatment/Reuse | U | Y | Y | Y | Y |
| Storage Facility Size Optimization | U | P | P | P | P |
| Runoff Management | Y | Y | Y | Y | Y |
| Impact of Green Infrastructure (GI) on Water Balance | U | U | U | U | Y |
| Average Runoff Assessment | U | P | P | P | P |
| Rainfall Inflow and Infiltration Mitigation | U | P | U | U | P |
| Measures Planning Considering Overland Flow | P | U | U | U | U |

| Functional application | Urban Cycle [12] | UVQ [7] | MIKE URBAN [19] | UWOT [1] |
| --- | --- | --- | --- | --- |
| Best Management Practices (BMPs) Assessment | P | P | Y | P |
| Drainage System Design | U | U | Y | U |
| Stormwater Treatment/Reuse | Y | Y | P | P |
| Storage Facility Size Optimization | U | P | P | U |
| Runoff Management | Y | Y | Y | Y |
| Impact of Green Infrastructure (GI) on Water Balance | U | U | Y | U |
| Average Runoff Assessment | P | P | P | U |
| Rainfall Inflow and Infiltration Mitigation | U | P | P | U |
| Measures Planning Considering Overland Flow | U | U | P | U |

| Functional application | CWB [3] | DAnCE4Water [15] | WMOST [13] | WaterMet2 [16] |
| --- | --- | --- | --- | --- |
| Best Management Practices (BMPs) Assessment | Y | P-L | Y | P |
| Drainage System Design | P | P-L | P | P |
| Stormwater Treatment/Reuse | Y | P-L | Y | Y |
| Storage Facility Size Optimization | P | U | Y | P |
| Runoff Management | Y | P-L | Y | P |
| Impact of Green Infrastructure (GI) on Water Balance | Y | U | Y | U |
| Average Runoff Assessment | P | U | P | U |
| Rainfall Inflow and Infiltration Mitigation | P | U | Y | U |
| Measures Planning Considering Overland Flow | P | P-L | P | U |

**The abbreviations describe overlapping practices.** BMP means *Best Management Practice*; GI means *Green Infrastructure*. The related terms LID (*Low-Impact Development*), WSUD (*Water-Sensitive Urban Design*) and SUDS (*Sustainable Urban Drainage Systems*) appear in the sources. The comparison concerns the modeled function—such as retention, infiltration or reuse—rather than assuming that differently named practice families are identical.

**The main stormwater contrast is three-way.** WBM evaluates source-control hydrology, MIKE URBAN evaluates detailed drainage behavior with screening-level LID representation, and WMOST selects management portfolios against watershed objectives. Each can contribute to stormwater planning, but they do not answer the same design question.

### BMP assessment and green-infrastructure water balances

**WBM directly targets source-control performance.** Its 2002 documentation names bioretention, infiltration facilities, rainwater capture/reuse, green roofs and detention. It continuously represents runoff, infiltration and evapotranspiration, and compares scenarios using land use, soil, groundwater and control-design parameters. That is direct support for assessing both BMP performance and GI effects on the water balance. [6]

**WBM emphasizes volumes rather than pipes.** Its purpose is to assess how development and source controls alter hydrological pathways, including how much rainfall is retained, evaporated, infiltrated or discharged. This gives it a particularly useful role where the management objective is restoring predevelopment-like runoff volumes. Its output hydrograph can feed a hydraulic-routing model, but that linkage should not be mistaken for an internal sewer-network solver.

**The 2002 upgrade context is consequential.** The document describes an existing spreadsheet model and proposed enhancements, including a more practical platform and improved multi-land-use and multi-year handling. Its site-to-watershed ambitions therefore should be read together with its actual implementation context, rather than treating every proposed enhancement as a completed release. The documented source-control hydrology remains the strongest basis for its Y marks. [6]

**MIKE URBAN connects controls to network response.** DHI’s January 2016 feature description explicitly adds WSUD/LID functionality to stormwater-runoff simulation while retaining detailed drainage-network hydraulics. The represented control processes include infiltration, filtering, storage, evaporation and detention close to the runoff source. This permits green-solution screening alongside assessment of downstream drainage behavior. [19]

**The distinction concerns decision detail.** WBM is useful for asking how source-control configurations change runoff volumes and pathways. MIKE URBAN is useful when the same intervention must also be assessed against pipe capacity, surcharge or surface-flooding consequences. The hydraulic detail does not automatically make every LID process more detailed: DHI expressly describes the LID representation as screening level.

**CWB adds sustainability to source-control comparison.** Its modeled options include green roofs, porous paving/asphalt, swales, filter strips, soakaways, retention ponds and detention basins. Their represented inflows include precipitation and runoff, while outflows include evaporation, infiltration, throughflow and overflow. Its GI-water-balance Y therefore rests on named devices and pathways, not merely on a general sustainability objective. [3]

**WMOST links GI to watershed objectives.** Its hydrological mechanism connects infiltration-based practices to aquifer recharge and stream baseflow, then to water-supply and minimum/maximum streamflow requirements. This is a stronger integration mechanism than assessing only the immediate reduction of runoff leaving a development. The desirability of infiltration depends on where that recharge goes and whether it contributes to the environmental or supply objective being optimized. [10]

**Partial BMP marks have narrower meanings.** Aquacycle, UVQ, Urban Cycle, WaterCress, Hydro Planner and WaterMet2 can investigate harvesting, storage, reuse or associated runoff changes, but the cited applications do not establish the same explicit GI-device breadth as WBM or CWB. Their P marks recognize relevant management interventions without turning every water-reuse scenario into a detailed BMP-performance model.

### Drainage design and overland-flow planning

**MIKE URBAN has the clearest drainage-design role.** Its runoff/pipeflow engine and coupled sewer–surface representation support assessment of drainage capacity and hydraulic deficiencies. The 2012 release introduced MIKE 1D for runoff and pipeflow, while the 2017 review identifies MIKE URBAN’s primary applications in flood control and drainage/sewer evaluation. [8][1]

**Sobek Urban also resolves hydraulic interactions.** Its integrated package includes one-dimensional urban/rural/river flow, two-dimensional overland flow, rainfall–runoff, water quality and real-time control. This supports hydraulic assessment of urban drainage and flooding. Its P marks in the exact design and overland-planning rows distinguish that physical capability from a separately specified automated design or measures-selection procedure. [1]

**CWB represents simpler surface redistribution.** Its effective-area concept routes runoff from directly connected impermeable areas to the drainage system, while runoff from non-effective areas reaches neighboring pervious space or SUDS. This supports partial assessment of measures involving surface flow and land-surface connectivity. It is not the same as resolving water depth and velocity across a two-dimensional inundation grid. [3]

**DAnCE4Water demonstrates linked adaptation planning.** A 2017 Melbourne study coupled its agent-based urban-development model with MIKE FLOOD’s 1-D/2-D hydrodynamics. The framework evaluated **nine urban-development/climate scenarios and 32 combinations of flood-adaptation measures**, including infrastructure changes, decentralized management and urban-planning policies. This is direct evidence of a linked overland-flow planning application, hence P-L rather than a native hydraulic Y. [20]

**That case changes the planning interpretation.** Adaptation performance depended on the climate and urban-development scenario and on other measures implemented alongside it. Urban-planning policies performed efficiently in the case, whereas guideline-oriented property buyback and pipe enlargement were comparatively costly. The result supports scenario-dependent planning, not a universal ranking of those measures across cities.

**Product boundaries remain important.** The Melbourne application explicitly names MIKE FLOOD as the hydrodynamic partner. It should not be used to assign every demonstrated function automatically to standalone MIKE URBAN. The linked DAnCE4Water framework and the requested MIKE URBAN product remain separate entries even though DHI modeling components can participate in related workflows.

### Treatment, harvesting and storage optimization

**Reuse requires a destination for captured water.** WaterCress’s Parafield application connects captured stormwater through aquifer storage and recovery to customer demand. Hydro Planner’s tested prototype includes treated stormwater among supply sources and large-scale harvesting. Aquacycle evaluates stormwater and wastewater reuse schemes, while CWB and WaterMet2 explicitly allocate alternative water to end uses. These are stronger reuse demonstrations than representing a detention volume without subsequent use. [5][14][18]

**WaterMet2 supplies a concrete example.** Its Oslo rainwater-harvesting/greywater-recycling strategy assumed adoption by 50% of households, with represented capacities of 0.48 million m³ for rainwater harvesting and 39,000 m³ for greywater recycling. These are capacities of the aggregated systems represented in the model, not individual household tank sizes. The alternative water supplied toilet flushing, irrigation and industrial uses. [11]

**Storage representation is not storage optimization.** A model can simulate a specified tank, test several capacities or calculate storage performance without searching for an optimal size. WaterCress’s detention/storage scenarios, WaterMet2’s assigned capacities and UVQ’s editable estate-storage properties justify partial sizing support. They do not establish a native optimal-design algorithm for the exact storage-size row. [5][7]

**WMOST makes capacity a decision variable.** Its 2013 specification allows maximum surface-water storage to be increased, with associated capital and maintenance costs, within a least-cost optimization. That directly supports Y for storage-size optimization at the model’s aggregate reservoir/surface-storage level. Its stormwater hydrology documentation additionally addresses BMP selection and sizing, including linkage with SUSTAIN. [10][21]

**CWB’s sizing remains qualified.** The thesis reports calculated recycling-store capacities, but also identifies development of a more sophisticated tank-size optimization module as a future improvement. A P therefore reflects useful sizing analysis without implying a mature general-purpose optimum-search procedure. [3]

### Average runoff and inflow/infiltration mitigation

**Average runoff often requires aggregation.** Several models generate continuous runoff quantities or time series from which a mean annual runoff can be calculated. For a record of \(T\) years with total runoff volume \(V\), the annual mean is \(V/T\), in m³/year when \(V\) is in m³. The P marks distinguish this straightforward derived assessment from an explicitly documented native “average runoff” reporting function.

**Averages do not replace event statistics.** Two scenarios can have similar annual runoff volumes yet different peak discharges, overflow frequencies or dry-weather intervals. WBM’s volume-based assessment, MIKE URBAN’s hydraulic response and WMOST’s streamflow constraints consequently supply complementary information. The appropriate comparison depends on whether the objective is annual runoff reduction, conveyance adequacy or receiving-water flow protection.

**Desired infiltration and sewer infiltration differ.** GI may deliberately infiltrate runoff into soil, whereas infiltration/inflow mitigation often means reducing unwanted groundwater or rainfall-derived water entering sewers. Demonstrating the first process does not automatically demonstrate the second. This is why WBM’s infiltration facilities and MIKE URBAN’s LID functions do not, by themselves, establish comprehensive sewer-leakage repair analysis.

**WMOST explicitly represents sewer repair.** Its manual identifies repair of infiltration into the wastewater collection system as a management practice, with repair costs and effects on treatment demand and groundwater retention. Its Danvers–Middleton case discusses reducing infiltration/inflow alongside supply, treatment and recharge decisions. The Y is therefore supported by an explicit intervention rather than inferred from general stormwater infiltration. [10]

**MIKE URBAN supports a related intervention.** The pre-cutoff stormwater review describes dynamic soakaway modeling in a Greater Copenhagen catchment, assessing extensive infiltration and effects on sewer overflows. That supports P for reducing rainfall-derived sewer loading. It does not alone establish a complete representation of groundwater ingress through defective sewer assets. [22]

**The stormwater judgment depends on the endpoint.** Choose WBM for source-control water balances, MIKE URBAN or Sobek Urban for hydraulic response, WMOST for least-cost watershed portfolios, and linked DAnCE4Water workflows when urban evolution changes the locations and exposure of future flooding.

### Cost and Energy: seven requested applications

| Functional application | Sobek Urban [1] | Aquacycle [3] | Hydro Planner [3] | WaterCress [3] | WBM [6] |
| --- | --- | --- | --- | --- | --- |
| Life Cycle Cost Accounting | U | N | N | U | U |
| Cost-Benefit Analysis | U | N | N | P | U |
| Capital and Operating Costs | U | N | N | U | U |
| Operating and Maintenance Costs | U | N | N | U | U |
| Energy Production and Consumption Estimation | U | N | N | N | U |
| Life Cycle Energy Use Analysis | U | N | N | N | U |
| Energy and Greenhouse Gas Emission Association Analysis | U | N | N | U | U |

| Functional application | Urban Cycle [3] | UVQ [3] | MIKE URBAN [1] | UWOT [3] |
| --- | --- | --- | --- | --- |
| Life Cycle Cost Accounting | N | N | U | P |
| Cost-Benefit Analysis | N | N | U | U |
| Capital and Operating Costs | N | N | U | Y |
| Operating and Maintenance Costs | N | N | U | P |
| Energy Production and Consumption Estimation | N | N | U | P |
| Life Cycle Energy Use Analysis | N | N | U | U |
| Energy and Greenhouse Gas Emission Association Analysis | N | N | U | U |

| Functional application | CWB [3] | DAnCE4Water [9] | WMOST [10] | WaterMet2 [16] |
| --- | --- | --- | --- | --- |
| Life Cycle Cost Accounting | Y | U | Y | Y |
| Cost-Benefit Analysis | P | P | Y | P |
| Capital and Operating Costs | Y | U | Y | Y |
| Operating and Maintenance Costs | Y | U | Y | Y |
| Energy Production and Consumption Estimation | Y | U | U | P |
| Life Cycle Energy Use Analysis | Y | U | U | P |
| Energy and Greenhouse Gas Emission Association Analysis | N | U | U | Y |

**The explicit exclusions are version-specific.** Last’s 2010 comparison states that Aquacycle/UVQ do not consider energy or cost, that Hydro Planner does not assess energy and cost, and that Urban Cycle models water flow only. Those statements support N for the documented cores; they are not blanket claims about every possible later coupling. The same thesis identifies average cost as a WaterCress indicator but explicitly excludes energy use. [3]

**The principal economic alternatives differ.** CWB emphasizes simplified whole-life cost and energy inventories; WaterMet2 combines discounted costs with system metabolism and emissions; WMOST minimizes annualized management costs subject to water-management goals. UWOT provides component-level cost and energy information useful for optioneering, but that is not automatically a complete life-cycle inventory.

### Life-cycle cost, operating cost and cost-benefit analysis

**CWB has an explicit technology library.** Last developed stand-alone simplified life-cycle energy and cost spreadsheets for decentralized management options, serving as a technology library for CWB. The accounting includes construction and operation, with maintenance within the operational phase. Conventional centralized supply/treatment is represented more simply through average costs and energy per cubic metre. [3]

**This supports more than a headline indicator.** CWB’s whole-life-cost Y is reinforced by documented construction, operation and maintenance categories, rather than inferred solely from the phrase “sustainability assessment.” The capital/operating and O&M rows therefore also receive Y. However, comparing whole-life costs per unit of service is still distinct from monetizing every environmental and social benefit, which explains its P for cost-benefit analysis.

**WaterMet2 explicitly discounts intervention costs.** Its Oslo assessment discounts capital investments and fixed/variable operation-and-maintenance costs to a 2011 base year at a 3% discount rate. Fixed costs include items such as salaries; variable costs include electricity associated with water processed or used. Its Y marks for life-cycle/planning-horizon cost, capital/operating cost and O&M therefore rest on named accounting categories and a specified financial basis. [11]

**Its decision comparison is multi-criteria.** The final Oslo paper compares five strategies using capital cost, O&M cost, supply reliability, leakage, greenhouse-gas emissions, combined-sewer-overflow volume and social acceptance. These are combined through Compromise Programming under four stakeholder-weight perspectives. This is not identical to a single monetary net-benefit calculation, hence P for the requested cost-benefit row. [16]

**WMOST includes financial life-cycle structure.** Its 2013 manual requests capital cost, O&M cost, remaining life of existing infrastructure, life of new infrastructure, a planning horizon and an interest rate. Initial costs are annualized, and replacement costs can arise where infrastructure reaches the end of its remaining life within the planning period. This is direct support for simplified financial life-cycle accounting, although it is not an environmental life-cycle assessment. [10]

**WMOST’s cost-benefit function is explicit.** The manual describes repeated optimization over different management-goal levels to construct a Pareto frontier or trade-off curve. Such a curve identifies how much additional cost is associated with a higher environmental target. It can be highly informative even when ecological benefits are expressed in streamflow units rather than converted into money. [10]

**The published case shows a threshold.** In the illustrative Danvers–Middleton application, annual management cost was approximately $13.4 million at the base streamflow criterion and remained $13.4 million at 125% of that criterion. At 150%, 175% and 200%, reported annual costs rose to approximately $15.2 million, $18.5 million and $22.7 million, respectively. Those are model-case costs, not transferable municipal budgets or general prices for ecological improvement. [10]

**The mechanism explains the nonlinearity.** Initial improvements can exploit slack or relatively inexpensive actions such as demand reduction and repair. More stringent flow requirements introduce additional treatment, recharge and stormwater measures. The case also demonstrates why an optimizer needs realistic feasibility bounds: unconstrained capacity choices can appear economically attractive while being impractical for the actual land or aquifer system.

**WaterCress and UWOT occupy narrower positions.** WaterCress’s average-cost indicator supports partial economic comparison of supply alternatives. UWOT’s component information includes capital cost, operating cost and energy use, supporting its capital/operating Y and partial operating-energy marks. Neither statement alone establishes the same life-cycle boundary, replacement treatment or environmental monetization documented for the more extensive accounting tools. [3]

### Energy inventories and greenhouse-gas accounting

**CWB explicitly calculates life-cycle energy.** Its simplified inventory includes embodied energy in materials, transport/construction energy, and operation/maintenance energy. Decommissioning is treated as small relative to other phases. The 2010 conference paper reproduced in the thesis expressly identifies energy consumption and production among the model’s intended assessment dimensions, supporting Y for that combined row. [3]

**A technology example demonstrates the mechanism.** In Last’s brown-roof example, a 100 m² roof, a 50-year lifetime and assumed attenuation of 100 m³/year produce modeled life-cycle energy of 1.4 kWh per m³ and whole-life cost of £1.1 per m³. The important capability is the conversion of material and operating requirements into service-normalized indicators; the particular values remain tied to the example’s technology and accounting assumptions. [3]

**Energy inventory is not impact assessment.** The thesis explicitly distinguishes its simplified energy inventory from environmental impact assessment, which could be added subsequently. It also identifies carbon-costing and impact categories such as global warming potential as extensions. Thus, its life-cycle-energy Y should not automatically become a native greenhouse-gas-impact Y. The GHG row records N for the documented energy-inventory-only implementation. [3]

**WaterMet2 connects energy and emissions directly.** It quantifies electricity, direct and indirect embodied energy, materials, chemicals and greenhouse-gas emissions in urban-water-system elements. In the Oslo assumptions, rainwater harvesting used 0.54 kWh/m³ and greywater recycling 1.84 kWh/m³. These were case-study parameters drawn from supporting studies, not universal performance figures for all technologies carrying those labels. [11]

**Its life-cycle-energy mark remains partial.** Embodied and operating energy over a strategic horizon provide substantial sustainability information. They do not, without an explicitly matched phase boundary, establish that every strategy receives a complete cradle-to-grave inventory including all replacements, retirement and end-of-life processes. The P distinguishes that broader metabolism accounting from CWB’s expressly framed simplified life-cycle-energy calculation.

**The Oslo emissions result shows burden shifting.** WaterMet2’s rainwater/greywater strategy produced the lowest reported system annual-average emissions, 142 kg CO₂-equivalent per capita per year, while household emissions increased by as much as 8.54 kg CO₂-equivalent per capita per year. Reduced centralized potable demand and wastewater generation outweighed added local-system burdens in that scenario. A household-only or utility-only boundary could therefore suggest a different conclusion. [16]

**Demand management can change the comparison.** CWB’s Birmingham application found water-efficient appliances particularly favorable when household water heating was included. Its demonstration reported annual mains-demand savings of 4,200 ML and wastewater reductions of 3,900 ML, with household water-heating energy savings of 61,000 MWh/year under its appliance-replacement assumptions. These are historical scenario outputs, not measured citywide savings. [3]

**The causal pathway is explicit.** Less water used by relevant appliances can reduce mains supply, wastewater handling and hot-water requirements simultaneously. By contrast, a recycling technology may reduce centralized water demand while adding local pumping and treatment energy. Whether demand efficiency or local supply performs better consequently depends on the technology, the hot-water share and the centralized service displaced—not simply on the volume of mains water saved.

### Native functions versus external assessment

**An external LCA does not change a model column.** A 2016 Cape Cod study used OpenLCA and ISO 14040 principles to compare five water-and-waste-service configurations. Its results illustrate how recovery and reuse can affect life-cycle energy and greenhouse gases, but they do not establish that Aquacycle, MIKE URBAN or any other requested model natively performs those calculations. [23]

**Linked workflows need named attribution.** The CSIRO UVQ–TAWS environment includes infrastructure and life-cycle-cost functions associated with the broader tool chain. The table nevertheless retains the explicit water/contaminant scope of UVQ’s documented core for its native economic marks. A study using that chain should identify UVQ as the water/contaminant engine and name the linked economic or infrastructure component separately. [7]

**The cost-and-energy judgment is conditional on purpose.** Choose CWB for integrated scoping with explicit simplified life-cycle energy/cost, WaterMet2 for metabolism and emissions trade-offs, and WMOST for least-cost portfolios and target–cost curves; change that choice when detailed environmental life-cycle impacts or treatment-process energetics become the decisive requirement.

### Social and Policy Factors: four requested applications

| Functional application | Sobek Urban [1] | Aquacycle [3] | Hydro Planner [4] | WaterCress [5] | WBM [6] |
| --- | --- | --- | --- | --- | --- |
| End-User Behavior Change Simulation | U | P | P | U | U |
| Technological Change Impact Simulation | U | P | P | U | U |
| Population and Urbanization Impact Simulation | U | P | P | P | P |
| Policy Impact Assessment | U | U | U | U | P |

| Functional application | Urban Cycle [1] | UVQ [7] | MIKE URBAN [1] | UWOT [3] |
| --- | --- | --- | --- | --- |
| End-User Behavior Change Simulation | U | P | U | P |
| Technological Change Impact Simulation | P | P | U | P |
| Population and Urbanization Impact Simulation | U | P | U | U |
| Policy Impact Assessment | U | U | U | U |

| Functional application | CWB [3] | DAnCE4Water [15] | WMOST [10] | WaterMet2 [16] |
| --- | --- | --- | --- | --- |
| End-User Behavior Change Simulation | P | Y | P | P |
| Technological Change Impact Simulation | P | P | P | P |
| Population and Urbanization Impact Simulation | P | Y | P | P |
| Policy Impact Assessment | P | P-L | Y | P |

**Three mechanisms should remain distinct.** A model may accept changed behavior as an input, calculate an aggregate response to an intervention, or simulate interacting adoption and urban-development dynamics. All can contribute to policy analysis, but they answer different questions. The original policy-impact request does not require every model to contain an endogenous political or behavioral system.

### End-user behavior and technological change

**DAnCE4Water explicitly targets socio-technical dynamics.** Its pre-cutoff descriptions connect societal needs, servicing-option uptake, urban form and infrastructure placement. The 2017 account describes interplay between urban development and societal dynamics influenced by willingness to pay, moving beyond a physical water balance with an externally imposed demand series. This is the clearest documented social-system mechanism in the corpus. [15]

**Its Y is an architectural judgment.** It identifies a directly described social/urban-development mechanism, not a finding that the platform was a fully operational commercial product or that its household adoption predictions had universal empirical validity. The model’s research-platform status and its intended explanatory function are separate attributes.

**Hydro Planner evaluates behavior scenarios.** Its 2005 Benalla case was designed to assess changing end-water-use behavior alongside climate and population effects. Its linked end-use model represents appliances, uptake rates and demographics, and can assess options targeting particular uses. This supports meaningful behavior and technology-impact assessment, while P distinguishes supplied uptake/behavior assumptions from a model that independently predicts how those behaviors emerge. [4]

**UVQ and UWOT support configurable consumption.** The CSIRO scenario environment permits occupant water-use estimates, appliance attributes, rainwater tanks and on-site treatment/reuse to be specified. UWOT’s optioneering hierarchy similarly supports comparison of water-efficient technologies and altered component operation. Their P marks recognize consequences of changed household practices or technologies, rather than claiming an autonomous social-adoption model. [7][3]

**WaterMet2 uses intervention assumptions.** In its Oslo scenario, a new water meter was assumed to reduce the associated per-capita demand by a constant 10%. The model then propagated that reduction into supply, wastewater and sustainability outputs. It did not derive the 10% behavioral response from an adoption or learning model, which explains the P for behavior-change simulation. [11]

**WMOST calculates an aggregate price response.** Its manual requests user-type price elasticities and allows demand reduction through changes in service prices. It also represents direct demand reductions associated with rebates, building-code changes, educational outreach or efficient appliances. This is more than merely labeling a scenario “conservation,” but it remains an aggregate economic/management representation rather than a simulation of individual household decision processes. [10]

**Technological scenarios are not technological forecasts.** Aquacycle, Urban Cycle, UVQ, UWOT, CWB and WaterMet2 can compare particular infrastructure or appliance configurations. That demonstrates their ability to estimate consequences if technologies are installed. It does not mean they forecast innovation, market diffusion or future technology performance independently of user assumptions. The P convention makes that distinction visible without dismissing the usefulness of scenario analysis.

### Population and urbanization impacts

**DAnCE4Water changes urban form dynamically.** Its urban-development module represents development and redevelopment under population and demographic change, with resulting consequences for infrastructure placement and performance. The model therefore addresses not only how much demand grows but also where urban change occurs and how that spatial pattern interacts with water systems. [9]

**Spatial growth can alter the preferred measure.** The Melbourne linked flood study found that random differences in the location and timing of urban development could materially affect flood risk and sometimes outweigh the benefits of less effective adaptation measures. This provides a concrete reason to distinguish a spatial urban-evolution model from a uniform percentage increase applied to all water-demand nodes. [20]

**Other models propagate specified development.** CWB varies future land use, population and climate; Hydro Planner incorporates demographic/end-use information and population scenarios; WaterCress’s Parafield application tests increased impervious area; and WBM uses land-use and site-design inputs including population density. These are useful urbanization-impact analyses, but their P marks distinguish externally specified change from endogenous urban-development generation. [3][5][6]

**WaterMet2 shows why temporal detail matters.** Its Oslo business-as-usual simulation, under fast population growth over 2011–2040, reported 94% supply reliability under the paper’s metric. Yet less than 75% of monthly demand was delivered in the final years. The whole-horizon reliability result and the late-horizon monthly deficit describe different summaries of the same deteriorating system; the former should not conceal the latter. [16]

**WMOST evaluates projected planning conditions.** Its inputs can represent future build-out areas and projected demand, and its manual encourages testing multiple climatic conditions. In the documented screening formulation, this establishes consequences of a selected future state rather than a detailed annual implementation or urban-growth trajectory. That distinction is important when comparing it with a dynamic model such as DAnCE4Water. [10]

### Policy assessment without overstating social simulation

**WMOST has explicit policy instruments.** Pricing changes, appliance rebates, land conservation, management constraints and streamflow standards can be assessed within a common optimization. A policy changes costs, demand or feasible actions, and the model calculates consequences for the selected portfolio and watershed outcomes. This supports Y for policy-impact assessment at screening level even though its behavioral representation remains aggregate. [10]

**CWB evaluates policy-informed demand futures.** Its Birmingham scenarios include metering and water-efficiency policy assumptions, land-use change and appliance-efficiency strategies. It can calculate the resulting water, energy and cost consequences. Its P recognizes that these policy responses are specified through scenarios rather than necessarily calculated from a policy-response equation within the core water-balance model. [3]

**WBM offers a narrower policy application.** Its 2002 work plan explicitly lists volume-based watershed trading, integration of land-use planning with stormwater management, and public education among applications. These support partial policy-planning relevance. They do not establish a general institutional or economic simulation of how trading participants, regulators or developers would respond. [6]

**DAnCE4Water evaluates policy through linked outcomes.** The 2017 adaptation framework explicitly tested urban-planning policies and calculated flood-risk implications through linked hydrodynamics. Its P-L records a completed policy-assessment application while retaining the division of labor between urban development and flood simulation. This is stronger evidence than the 2014 project’s prospective description alone. [20]

**Stakeholder weights are not behavior equations.** WaterMet2’s environmentalist, water-company, public and equal-weight perspectives change how alternative strategies are evaluated. They do not by themselves simulate how stakeholder preferences evolve, how institutions negotiate or how households adopt technologies. The distinction explains why WaterMet2 can offer substantive decision support while retaining P across the social-policy rows. [16]

**The social-policy judgment follows the mechanism.** Use DAnCE4Water when changing urban form and social uptake are central to the explanation, WMOST when explicit economic instruments and management constraints drive the decision, and scenario-based balance tools when the task is to quantify consequences of specified demographic, behavioral or technological futures.

**Additional documented evidence**

**Capability status—UWOT, WBM and WMOST**

**UWOT.** The Urban Water Optioneering Tool (UWOT) is a decision-support tool that compares water-saving, recycling, treatment and drainage technologies at different scales. It models individual water uses and technologies, aggregates their effects at development scale, and ranks technology combinations against user-based criteria. Its documented users are primarily water planners, developers and consultants working at early/conceptual and master-planning stages, including baseline and future scenarios [109]. Thus, its strongest entries concern alternative options; treatment, drainage design and user-oriented customization are only partial matches. The record does not establish potable distribution simulation, hydrosystem abstraction, green-infrastructure effects, cost analysis, or behavioral and policy simulation [109].

**WBM.** Water Balance Model (WBM) was first developed at the University of New Hampshire by Charles J. Vorosmarty in the **1990s (calendar decade)**; it is a **global-scale gridded model** applied from **local watersheds to the global river system** [24]. It simulates vertical ground–atmosphere exchange and horizontal runoff and stream transport, including river discharge, temperature, dissolved nitrogen, irrigation, reservoir effects, snowmelt, impervious-surface runoff and physically based evapotranspiration [24]. WBMplus adds a **daily time step**, Muskingum–Cunge routing and FrAMES grid-based distributed implementation; irrigation demand can be met from small reservoirs, groundwater-related runoff, river discharge or, when these are insufficient, a virtual fossil-groundwater pool [24]. WBMplus Regional is intended for **watershed-scale** analysis and adds urban land, withdrawals, reservoir routing, impervious surfaces, lawns, wetland storage and detention [24]. The documented family includes WBM/WTM, WBMplus, WBMplus Regional, PWBM, the Water Temperature Model, the Nitrogen Removal Model and Contemporary WBM/WBM_TrANS [24]. These variant-specific capabilities explain the partial marks; the source page gives no explicit publication or as-of date, so unsupported rows remain unresolved rather than being treated as absent.

**WMOST.** WMOST is the **Watershed Management Optimization Support Tool**. The documented releases are **v1 (December 2013), v2.0 (March 2016) and v3.0 (February 2018)** [111]. It is a spatially lumped screening tool for **local or small watersheds**, with **daily or monthly** time steps and nonlinear-programming optimization. It represents direct and indirect environmental effects, costs, water flows and water quality, and supports stormwater, green infrastructure, combined-sewer-overflow, stream-restoration, water-supply, wastewater, low-impact-development and land-conservation options [111]. Version 3 adds water-quality management, riparian and agricultural options, stormwater BMPs, baseline/stormwater hydrology modules, CSO and flood modules, ScenCompare and a GI Benefits Module [111]. Accordingly, alternative infrastructure and runoff management are documented; GI effects and cost-benefit support are partial. The cited record does not establish exact statuses for supply-demand, BMP assessment, average runoff, lifecycle costs, energy, or social-policy rows [111].

MIKE URBAN (DHI) is documented in a 2009 report as an urban rainfall–runoff/drainage model, not a potable-water model. Senai Town, Malaysia (2008) used Time-Area hydrology (also Kinematic Wave, Linear Reservoir, Unit Hydrograph and MOUSE RDI), pipe/canal links, free-surface/pressurized Saint-Venant flow, backwater effects, GIS/DEM, AutoAssign and calibration. Scale: 33 ha; 24 (25 with a virtual) subcatchments; one-minute water-level records. [112]

MIKE URBAN—DWM: Supply-Demand, Resource Availability, Distribution, Regional Allocation, Leakage, Abstraction, User Customization, Alternative Infrastructure and Treatment: all ?. SWM: BMP ?, drainage design △, treatment/reuse ?, storage ?, runoff ✓, GI balance ?, average runoff △ (runoff calculated; mean rate absent), rainfall I/I ?, overland planning △; Cost/Energy: all seven ?; Social/Policy: behaviour ?, technology ?, population/urbanization △, policy △. ?=insufficient evidence; △=partial/coupled. A sediment tool was unused; litter was omitted; evaporation was compensated in calibration; DHI manuals (2007/08) are cited. [112]

**Water Balance Model (WBM): evidence-qualified capability status**

All marks below are historical statuses as of **2018-03-31**. `?` means insufficient model-specific evidence, not documented non-support. The admissible 2009 European Commission/JRC report by Gunter Wriedt and Fayçal Bouraoui describes a **generic water-balance model**, but does not establish that this model is the roster entity **Water Balance Model (WBM)**. Its findings therefore remain contextual evidence rather than positive WBM capability marks [114].

**Evidence slice: DAnCE4Water and WaterMet2**

WaterMet2 is identified in a report published **1 February 2012** by Behzadian, Kapelan, Rozos and Makropoulos. The report identifies WaterMet2 as a work-in-progress, simulation-type, mass-balance model based on the earlier UWOT software developed by UNEXE/NTUA. It represents five integrated subsystems—water supply, water demand, wastewater, cyclic water recovery and resource recovery—and was intended for strategic planning and testing in Oslo. Its spatial representation runs from individual properties through land blocks and regions to a city/system; its default temporal resolution is **daily**, over a user-specified **N-year** horizon, with at least one year envisaged for seasonal variation. [73]

WMOST (2015): LP✓ supply/resource/abstraction, BMP/GI/runoff, alternatives, CBA, capex/O&M; basin/reach, daily/monthly; no quality [75]. CWB: △ city demand/energy/life-cycle cost [53]. MIKE URBAN: ? pre-cutoff

**Source-group evidence additions**

**Aquacycle.** Aquacycle is an integrated urban-water-balance model, described as quasi-distributed with a daily timestep and unit-block, cluster and catchment scales; it estimates demand, stormwater and wastewater and couples rainfall–runoff with supply–wastewater processes [76]. Its first-developed year and originating developer remain unresolved; the 2010 study’s Korea University authors are not identified as developers [33]. In Greater Athens, scenarios included a 2 m³ rainwater tank and 5 m³ treated-wastewater storage; on-site wastewater treatment and reuse reduced imported demand by 41% and wastewater production by 54%. Results depend on awareness and incentives, while short-term seasonal variation and long-term population, expansion and climate scenarios are limited [76]. A Seoul application reports conflicting verification values, \(r=0.97\) and \(r=0.84\), for 2007/verification reporting; both are retained, with observed data identified as important for calibration [33].


**MIKE URBAN.** DHI’s tool integrates modelling engines with an open GUI and supports steady/extended-period analysis, water quality, water hammer, real-time control, GIS/SCADA links, leakage reduction, pressure-zone optimisation and energy-cost optimisation [70]. It calculates node demand by pipe-length and two-coefficient methods, supports tank and pump-station design scenarios, and documents a 30-year Brisbane demand forecast. GIS/CAD/ODBC exchange, scenario management, 3-D viewing and overland-flow-related representation are also documented; first-developed year, typical scales and several row-specific statuses remain unresolved [70].

WMOST IUWM[148];WaterCress △supply-demand/runoff 2011[140];MIKE URBAN △1D/2D[57];UWOT total-cycle 2011[127];WBM? forest≠roster[139]

WBM—2002/03 conflict; site LID/source-control, external routing; no native routing/snowmelt/quality [71][65]. Hydro Planner—2005–17: integrated quantity/quality, supply–demand, portfolios, recycling; developer/scale ? [80]. UVQ—2005 total-cycle balance; MUSIC-coupled options/tanks/demand/contaminants; Pheasant Creek 1960–2005; treatment ? [79][146]. WaterMet2—2015 supply/stormwater/wastewater/reuse; 4 scales; water/energy/GHG; developer/timestep ? [136]. WaterCress—original unsupported/incompatible with WaterCress-e; 2025 excluded; capability ? [134].

WaterMet2: △ Water Resource Availability Analysis [62]—native supply models surface water, groundwater, desalination, inflow, storage, demand and shortage; ✓ Regional Water Allocation [62] uses source/route coefficients at local/subcatchment levels (Oslo 90%/10% split), not necessarily regionally. Oslo: 30-year horizon from 2011, daily step; alternatives include new resources/treatment and rain/grey-water recycling, but pressure and sub-day KPIs are not supported [62].

Hydro Planner (HydroPlanner): by early 2010, the SEQ prototype coupled hydrological, demand and supply simulations in a lumped node/subcatchment network, producing daily city/catchment/regional results [138]. It covered supply, demand, wastewater, stormwater, groundwater and manufactured water, including harvesting, reuse, desalination, dams and transfers [138]. Stage 1 implemented wastewater generation/treatment/discharge/direct recycling and stormwater; indirect recycling, harvesting, desalination, leakage/overflows and demand management were proposed, so no unconditional ✓ [138].

MIKE URBAN—DHI: 1-D/2-D supply/drainage/wastewater; Hydro Planner: E2/7 modules; UVQ—CSIRO: Aquacycle+contaminants/treatment; UrbanCycle: hourly/daily; UWOT: 10 min–monthly; CWB: 2010; DAnCE4Water: 2011–12; WaterMet2: 4 subsystems; WaterCress-e: energy/costing; Sobek: RR/2D/quality/RTC; WBM/WTM: Amazon only [115][120][122][150][83][84].

- Sobek Urban: 1-D/2-D, rainfall–runoff, water quality and real-time control; flood/drainage; leakage, rainfall I/I and capital/operating costs: ?; Aquacycle: WHB/SDDW/EISW/WWT/BMP/RT/RR/RGW/EGG cases; full status ?; Hydro Planner: E2 modules cover catchment, supply, consumption, rainwater, wastewater, receiving waters and integration; supply-demand documented [86].
- WaterCress: WHB/SDDW/BMP/RR/RGW cases; Urban Cycle: WHB/SDDW/BMP/RR/EGG cases; UVQ: water/contaminant-balance development scenarios; WHB/C/SDDW/EIGW/RC/WWT/BMP/H/RT/RR/RGW cases [86].
- MIKE URBAN: hydrologic/hydraulic balance; pre-cutoff flood/drainage/BMP cases; 2018 Jakarta evidence excluded [86][144]. City Water Balance: 2010 IUWM scoping model; capability cells ?. DAnCE4Water: evolving-city/infrastructure; BMP/RT/storage/energy/GHG/social factors [86].
- UWOT: supply/distribution, groundwater/surface abstraction, treatment, RWH/GWR/SUDS, sewer mining/runoff; energy parameters; named social/policy impacts and CBA/capital-opex method ?; training date ? [132].
- WaterMet2: supply/demand/wastewater/treatment subsystems; energy/GHG/chemical balance; WHB/C/SDDW/EISW/WWT/BMP/RR/RGW/EGG cases [86]. WBM: supplied detail is 2022 and excluded; no status here [39].

WaterCress: ✓ runoff/average-runoff (Parafield Drain; 30-min/daily/1-h; 20-month calibration) [116]. Urban Cycle: Urban Developer lineage only; standalone cells ? [141]. UWOT: household/city scales, scenarios, cost/energy library [126]. DAnCE4Water: 2017 integrated spatial planning; cells ? [142].

WMOST: demand/BMP/reuse/cost; basin, day/mo [130]; CWB: demand/options/GI/LC cost/energy; city blocks [131]; UrbanCycle: whole-cycle, subdaily allotment-catchment [87]; WaterMet2: water/energy/GHG, RWH/GWR [152]; WaterCress: late-80s, Richard+David, alloc. [145]; UWOT: RWH/SUDS/runoff [147]

WaterMet2: ✓ supply/treatment/energy-GHG; 2015[154]

Within the fixed roster, Sobek Urban is an IUWCM developed by Daltares (Netherlands) and is drainage/hydraulic-oriented; only a few documented applications cover the complete urban water cycle [86]. Its 1DFLOW/2-D overland-flow, rainfall-runoff, water-quality and real-time-control package spans catchment to group-of-neighborhood scales; a tutorial uses a 1-minute step and the manual demonstrates 25 000 sewer pipes/manholes, supporting fine-resolution drainage/runoff design while leaving non-hydraulic functions unestablished [86][49].

Aquacycle, developed by Grace Mitchell, is a mass-balance urban-water model: its beta was released in 2000 and Version 1 in 2005, and it links supply, stormwater and wastewater while evaluating collection, storage, treatment and distribution at unit-block, cluster and catchment scales on a daily step [26][96][153]. It does not simulate water quality, lacks short-term variability and was tested only in Woden Valley, so it suits daily supply-demand/reuse screening, not event-scale or contaminant analysis [110][100][96].

Hydro Planner is a regional, integrated total-water-cycle prototype using user-defined basins, catchments and subcatchments at a daily step; it documents supply-demand, stormwater harvesting, wastewater recycling/treatment and water-quality/quantity scenarios over a 50-year future scenario [56][90]. Its breadth suits long-horizon regional option planning, but full functionality was not incorporated and more decentralised/centralised options and multiple supply paths were future work, so demonstrated and planned functions must be separated [138][56].

WaterCress (Water-Community Resource Evaluation and Simulation System), attributed to Richard and David and originating in the late 1980s, is a node-link water-balance planning framework for rural/urban catchments; priorities/weights, real-time transfer control, farm-dam choices and what-if variations make it more allocation- and user-design-oriented than a drainage-only simulator [145][92][25]. It supports 30-min sub-daily and daily resolution and allocation planning for subdivisions/small communities and the State Government, but calibration needs flow-gauge and aquifer-storage depreciation data, so it is best for design/scenario screening with explicit data risk [116][92][145][124].

WBM is a global-to-watershed water-balance family attributed originally to Vorosmarty et al. and documented from the 1990s; WBMplus Regional incorporates urban land, irrigation, reservoirs and withdrawals/returns, with daily-average fluxes and monthly water-balance/runoff calculations [119][24][135]. It offers broader hydrologic extent but less direct urban-network/decision detail than city-scale tools; the evidence supports runoff and water-availability analysis, making WBM a watershed-context rather than complete urban-management platform [24][71][135].

Urban Cycle is a whole-of-water-cycle hierarchical network framework documented by Hardy, Kuczera and Coombes in 2005; it models supply, consumption, reuse, wastewater and stormwater from allotment through cluster, estate and small-suburb scales and supports scenario comparison by planners, managers and designers [87][121][141]. It is stronger for demand/wastewater, harvesting/recycling and allocation scenarios than a balance-only model, with minute-scale runoff modelling, but cannot analyse upstream transfers, bidirectional or complex distribution networks [121].

UVQ's technical description dates to August 2000; it is a conceptual daily mass-balance water-and-contaminant model with house, cluster and city scales, producing stormwater/wastewater flows and loads and comparing six source-management scenarios and treatment options [58][117][38][118][91]. Because contaminants are treated as conservative, reactive transformation is not represented; UVQ therefore suits daily/monthly/annual quality-and-reuse screening, not detailed reactive prediction [118][91].

MIKE URBAN, developed by DHI, is a detailed network/hydraulic framework supporting water-distribution and sewer modelling, steady-state/extended-period analysis, water quality, water hammer, real-time control and coupled 1-D/2-D overland-flow simulation [40][70][84]. It is stronger than balance/scoping models for distribution, drainage and flood hydraulics, but its detailed network orientation and reported $18,000 - $25,000 USD price create access/implementation risks, favoring network design over low-data screening [123][137].

UWOT is a component-based flexible urban-water decision-support framework developed by C. Makropoulos and E. Rozos and documented by 2008 for planners/developers at the conceptual stage; it aggregates households and switches among local/central recycling, rainwater harvesting, greywater treatment and other combinations [125][108][109][27]. It is stronger than hydraulic-network simulators for option selection and water/wastewater/energy/land-use and health-risk trade-offs, while daily household-demand representation limits it as a detailed distribution-hydraulics model [27][143].

CWB is the SWITCH project's conceptual daily city-scale water-energy-quality balance/scoping model, documented around 2010 for rapid option comparison; it represents neighbourhoods/subcatchments over annual-to-decadal periods and works with sparse or detailed mapping/monitoring [31]. It is broader than runoff-only models through natural systems, pollution, whole-life energy/cost, green roofs, rainwater harvesting and wastewater recycling, but its lowest meaningful resolution limits detailed hydraulic/GI claims, so it is best for rapid city-scale screening [107].

DAnCE4Water is a spatially explicit socio-technical framework developed through PREPARED by Ana Deletic and Rebekah Brown; its Scenario Input, Societal Transitions, Urban Development, Bio-Physical and Conductor modules link urban growth, infrastructure and social change to water security, flooding, stream health and extreme heat [42][113][128]. Compared with hydraulics-only tools, it offers stronger strategic multi-benefit/technology-transition analysis, but validation is for a Melbourne urban catchment without specified temporal resolution, so it suits strategic planning rather than fine-time-step hydraulics [133][151].

WMOST is EPA's Excel-based, spatially lumped linear-programming optimization framework with daily/monthly steps; it explicitly handles management goals, BMP/SUSTAIN runs, design sizes, capital/O&M costs and cost-benefit analysis [130][75][68][72]. SUSTAIN requires at least hourly time series for more accurate sub-daily stormwater modelling, so WMOST suits integrated economic/BMP option selection rather than detailed network hydraulics [68].

WaterMet2 is a mass-balance source-to-tap/urban-metabolism framework integrating supply, demand, wastewater, cyclic/recovery and resource-recovery processes from property to city at daily resolution; it quantifies water, energy, materials, chemicals and greenhouse-gas performance [73][149][129][106][155]. It is stronger than network-hydraulic models for intervention, cost/O&M, reliability and emissions comparisons over a 30-year horizon, but simplified distribution and strategic leakage approximation without pressure-head variation make it a sustainability-planning, not hydraulic-design, tool [149][89][106].

Sobek Urban's profile covers integrated 1-D wastewater/stormwater flow, rainfall-runoff, storage/street flow, drainage-capacity and detention-basin design, sewer-overflow analysis and water-quality/real-time control; the tutorial uses a 1-minute step and the manual demonstrates 25 000 sewer pipes/manholes [49]. Evidence does not establish supply-demand, resource/allocation, leakage, abstraction, user-customisation, alternative-infrastructure or treatment-scheme functions, nor the cost/energy or social/policy rows; with few applications spanning the complete cycle, mark Sobek Urban as detailed drainage/runoff rather than a complete profile [86][49].

Aquacycle's profile covers supply-demand/water-balance simulation, alternative stormwater/wastewater collection-storage-treatment/distribution and quantity-based runoff/reuse analysis at unit-block, cluster and catchment scales on a daily step [96][153]. It lacks water-quality simulation and short-term variability; evidence does not establish detailed allocation, leakage/abstraction, BMP/GI or overland-flow functions, cost/energy or social/policy functions, so it is a daily quantity/reuse screening model rather than complete coverage [110][100][96].

Hydro Planner's profile covers regional/daily supply-demand and water-availability modelling, stormwater harvesting, wastewater generation/treatment/recycling, alternative sources and water-quality/quantity scenarios over a 50-year future scenario; user-defined subcatchments and a treatment plant returning treated water are documented [56][90]. Full functionality was not incorporated and treatment evidence is application-specific; the material does not establish complete BMP/GI, cost/energy or social/technology/population/policy coverage, so Hydro Planner is a regional scenario prototype rather than a complete matrix [138][90].

## Choosing among the models for a literature review

**The strongest comparison is task-specific.** A horizontal review should not rank these models by simply counting Y marks. A single hydraulic capability may be decisive for drainage design, while a life-cycle-energy capability may dominate a strategic sustainability study. Conversely, a model with many broad accounting functions may be inappropriate where the research question depends on local pressure, surcharge depth or short-duration peak flow.

| Research decision | Most relevant starting models | Decisive distinction |
|---|---|---|
| Distribution or drainage hydraulics | MIKE URBAN; Sobek Urban for drainage/surface interactions | Physical network and surface-flow resolution |
| Supply adequacy and resource portfolios | Hydro Planner; WMOST; WaterMet2 | Linked allocation versus optimization versus simulation |
| Property/neighborhood servicing alternatives | Aquacycle; Urban Cycle; UVQ; UWOT; CWB | Demand detail, quality, topology and sustainability indicators |
| Source-control runoff performance | WBM; CWB; MIKE URBAN | Hydrological volumes versus sustainability versus network effects |
| Harvesting and aquifer-storage reliability | WaterCress; Hydro Planner; WMOST | Local recovery simulation versus integrated portfolio selection |
| Cost, energy and emissions trade-offs | CWB; WaterMet2; WMOST | Life-cycle inventory, metabolism accounting or least-cost optimization |
| Urban evolution and policy-linked flood risk | DAnCE4Water with named hydraulic partners | Spatial development and socio-technical coupling |

**Integration can expose competing benefits.** WaterMet2’s leakage-rehabilitation example improves water delivery while increasing modeled wastewater loading. WMOST’s infiltration practices can reduce runoff while supporting recharge and low flows. CWB’s appliance scenarios show that avoiding hot-water demand may outperform adding a new local supply technology on energy grounds. These are different manifestations of the same principle: an intervention should be evaluated across the systems it changes, not only the subsystem that motivates it. [16][10][3]

**Greater breadth does not guarantee greater accuracy.** A daily integrated balance can reveal an important supply–energy trade-off while remaining unsuitable for designing a particular pipe. A detailed hydraulic model can calculate that pipe’s response while leaving household adoption, life-cycle cost or external resource scarcity outside its immediate boundary. Model selection changes when the dominant decision changes from strategic screening to engineering design, or from assumed implementation to explanation of adoption.

**Evidence and measurement bases require one distinction.** Dates follow underlying pre-cutoff works rather than archive-hosting dates; ≤ values are existence bounds, and CWB’s 2006–2010 interval is an estimate from project and thesis anchors. UVQ’s daily scale is inferred from its Aquacycle-derived structure; UWOT’s six-minute–daily bracket is a comparison estimate using documented Urban Cycle/Aquacycle resolutions, not a claimed software setting; hydraulic temporal estimates identify event scale rather than fixed defaults. Y/P/N/U refer to the cited implementations, not every possible release or coupling. Monetary, energy, emissions and reliability results retain their original case, units, accounting boundaries and periods.

**The overall conclusion is complementary specialization.** For a literature review ending in March 2018, the most defensible result is that detailed hydraulics, integrated water balances, portfolio optimization, sustainability accounting and socio-technical evolution are distributed across different tools. The two tables make those distinctions visible while preserving the complete requested model and application coverage.

## References

[1] <https://www.mdpi.com/2073-4441/9/4/285> 2017 urban-water-cycle review; Pre-cutoff model references; UVQ description; Hydraulic-model descriptions; Aquacycle leakage balance; UVQ treatment assumptions…
[2] <https://www.svasek.nl/wp-content/uploads/2017/04/sobek.pdf>
[3] <http://etheses.bham.ac.uk/1757/1/Last11PhD.pdf> Urban Cycle comparison; CWB spatial representation; Aquacycle and UVQ comparison; CWB model concepts; CWB leakage representation; CWB technology representation…
[4] <https://www.mssanz.org.au/modsim05/papers/maheepala.pdf> Hydro Planner integration; Hydro Planner availability analysis; Hydro Planner–REALM integration; Hydro Planner configuration; Hydro Planner end-use and scenari…
[5] <https://www.waterconnect.sa.gov.au/Content/Publications/DEW/MARSUO_WaterCress.pdf> WaterCress access; WaterCress Parafield specification; WaterCress supply chain; WaterCress scenarios; WaterCress impervious-area scenario
[6] <https://waterbucket.ca/rm/files/2016/12/Water-Balance-Model-Upgrade-June2002.pdf> WBM source-control specification; WBM implementation and upgrade plan; WBM land-use inputs; WBM policy-facing applications
[7] <https://www.academia.edu/21436291/CSIRO_LAND_and_WATER_Final_Report_on_Application_and_Refinement_of_Assessment_Tools_for_the_CSIRO_Urban_Water_Program_Feasibility_Study> CSIRO UVQ boundary; UVQ–TAWS division of functions; UVQ scenario storage; CSIRO assessment-tool structure; UVQ household scenario configuration
[8] <https://wiki.mikepoweredbydhi.com/mikeurban/setup/installation_2012_neuin2012> DHI’s distribution-analysis tools; DHI’s runoff/pipeflow engine
[9] <https://watersensitivecities.org.au/wp-content/uploads/2016/05/FS_A4-3_Socio-technicalModellingUrbanWaterManagement.pdf> DAnCE4Water development mechanism
[10] <https://www.epa.gov/sites/default/files/2013-12/documents/wmostv1_userguide_92513.pdf.pdf> WMOST v1 manual; WMOST access; WMOST management objectives; WMOST distribution-capacity options; WMOST pumping and transfer decisions; WMOST leak repair; WMOST…
[11] <https://doi.org/10.5194/dwesd-7-1-2014> WaterMet2 formulation; WaterMet2 source-to-demand representation; WaterMet2 network structure; WaterMet2 intervention assumptions; WaterMet2 financial accounti…
[12] <http://hdl.handle.net/1959.13/1059162> UrbanNet thesis; Urban Cycle and UrbanNet
[13] <https://www.epa.gov/sites/default/files/2018-02/documents/wmostv3_userguide_epa600r17_255final508.pdf> WMOST v3 guide
[14] <https://climateresilientwater.org/wp-content/uploads/2026/05/Technical-Report-108-HydroPlanner-A-Prototype-Modelling-Tool-to-Aid-Development-of-Integrated-Urban-Water-Management-Strategies-April-2013.pdf> Hydro Planner prototype; Hydro Planner tested features
[15] <https://doi.org/10.3390/w9120983> DAnCE4Water’s 2017 status; DAnCE4Water module links; DAnCE4Water’s 2017 formulation
[16] <https://dwes.copernicus.org/articles/7/63/2014/dwes-7-63-2014.pdf> WaterMet2 Oslo configuration; Oslo rehabilitation results; WaterMet2 decision analysis; WaterMet2 component emissions; WaterMet2 long-horizon results; WaterMet…
[17] <https://sswm.info/sites/default/files/reference_attachments/MAHEEPALA%202010%20Towards%20the%20Adoption%20of%20Integrated%20Urban%20Water%20Management%20for%20Planning.pdf> Maheepala’s IUWM–IWRM distinction
[18] <https://doi.org/10.30955/gnj.000532> Aquacycle reuse application
[19] <https://www.dhigroup.com/upload/mpbd/rel2016/new-features/jan-2016-extended-support-for-green-infrastructure-in-mike-urban.html> DHI’s 2016 LID release
[20] <https://watersensitivecities.org.au/content/assessment-of-urban-pluvial-flood-risk-and-efficiency-of-adaptation-options-through-simulations-a-new-generation-of-urban-planning-tools/> 2017 Melbourne adaptation framework; Melbourne urban-development effects; DAnCE4Water-linked policy assessment
[21] <https://www.epa.gov/sites/default/files/2016-03/documents/wmostv2_theoreticaldoc_final9d.pdf> WMOST BMP selection and sizing
[22] <https://doi.org/10.1007/s11270-014-2055-1> Copenhagen soakaway application
[23] <https://doi.org/10.3390/w8040154> Cape Cod life-cycle assessment
[24] <https://wsag.unh.edu/wbm.html>
[25] <https://www.waterselect.com.au/download/watercressmanual.pdf>
[26] <https://toolkit.ewater.org.au/Tools/Aquacycle/history>
[27] <https://www.researchgate.net/profile/Christos-Makropoulos/publication/222957924_Decision_support_for_sustainable_option_selection_in_integrated_urban_water_management/links/5cbf113aa6fdcc1d49a92d55/Decision-support-for-sustainable-option-selection-in-integrated-urban-water-management.pdf>
[28] <https://waterbucket.ca/rm/files/2016/12/Water-Balance-Model-Upgrade-June2002.pdf>
[29] <https://eprints.qut.edu.au/231462/>
[30] <https://cfpub.epa.gov/si/si_public_record_report.cfm?Lab=NHEERL&dirEntryId=262280>
[31] <https://research.monash.edu/en/publications/switch-city-water-balance-a-scoping-model-for-integrated-urban-wa/>
[32] <https://www.epa.gov/sites/default/files/2016-03/documents/wmostv2_theoreticaldoc_final9d.pdf>
[33] <https://doi.org/10.5004/dwt.2010.1899>
[34] <https://www.itia.ntua.gr/en/getfile/1152/1/documents/CCWI2011_311.pdf>
[35] <https://hero.epa.gov/reference/6582331/>
[36] <https://www.waterconnect.sa.gov.au/Content/Publications/DEW/ki_LkMerreti_20050928.pdf>
[37] <https://mssanz.org.au/modsim2013/L15/hidayat.pdf>
[38] <https://pmc.ncbi.nlm.nih.gov/articles/PMC4235893/>
[39] <https://gmd.copernicus.org/articles/15/7287/2022/gmd-15-7287-2022-supplement.pdf>
[40] <https://www.dhigroup.com/upload/publications/mouse/Liu_2010.pdf>
[41] <https://digitalcollections.anu.edu.au/entities/publication/5923c877-48ab-4f2d-a9cd-6a55a758b896/full>
[42] <https://watersensitivecities.org.au/content/social-modelling-water-systems/>
[43] <https://www.casqa.org/model/wmost>
[44] <https://nepis.epa.gov/Exe/ZyPURL.cgi?Dockey=P101B0JK.txt>
[45] <http://etheses.bham.ac.uk/1757/1/Last11PhD.pdf>
[46] <https://www.waterselect.com.au/articles/selfsustainablehouse.pdf>
[47] <https://www.epa.gov/hydrowq/wmost-10-download-page>
[48] <https://wiki.mikepoweredbydhi.com/mikeurban/anleitungen/import_zeitserien_ascii>
[49] <https://content.oss.deltares.nl/sobek2/SOBEK_User_Manual.pdf>
[50] <https://eprints.qut.edu.au/231465/>
[51] <https://wiki.mikepoweredbydhi.com/mikeurban/setup/installation_2011_neuin2011>
[52] <https://wiki.mikepoweredbydhi.com/mikeurban/setup/installation_2008_neuin2008>
[53] <https://research.birmingham.ac.uk/en/publications/switch-city-water-balance-a-scoping-model-for-integrated-urban-wa/>
[54] <http://eprints.usq.edu.au/8510/1/Taylor_B.A._2009.pdf>
[55] <https://www.semanticscholar.org/paper/Water-balance-model-(WBM)-v.1.0.0%3A-a-scalable-model-Grogan-Zuidema/79ebc6b15786cb20a1a11c8f7d206d9d4b976e4c/figure/19>
[56] <https://www.researchgate.net/profile/Stephanie-Ashbolt/publication/215470407_Hydroplanner_towards_a_regional_integrated_urban_water_modelling_tool/links/5609d35208ae576ce63f965e/Hydroplanner-towards-a-regional-integrated-urban-water-modelling-tool.pdf>
[57] <http://dhiuk-demos.blogspot.com/search/label/MIKE%20URBAN>
[58] <https://csiropedia.csiro.au/wp-content/uploads/2014/07/cr-t4-47.pdf>
[59] <https://doi.org/10.5194/dwes-7-63-2014>
[60] <https://scholarsarchive.byu.edu/iemssconference/2018/Stream-C/129>
[61] <https://www.dhigroup.com/upload/campaigns/mike-urban-plus/MIKE-URBAN-Plus-decommission-note.pdf>
[62] <https://doi.org/10.13140/rg.2.1.3417.2965>
[63] <https://doi.org/10.37871/jbres1222>
[64] <https://mp.watereurope.eu/d/Product/25>
[65] <https://waterbucket.ca/cfa/files/2013/08/Beyond-Guidebook_WBM-powered-by-QUALHYMO_Jim-Dumont_Nov-2007.pdf>
[66] <https://www.evanet.dk/wp-content/uploads/2017/05/4_Modellering-af-LAR-anl%C3%A6g.pdf>
[67] <https://doi.org/10.25675/3.020745>
[68] <https://19january2021snapshot.epa.gov/sites/static/files/2018-02/documents/2018_wmostv3_theoreticaldoc_epa600r17_220final508.pdf>
[69] <https://urbanbeatsmodel.com/history/>
[70] <https://www.yumpu.com/en/document/view/44982865/pdf-download>
[71] <https://doi.org/10.2166/wqrj.2004.046>
[72] <https://nepis.epa.gov/Exe/ZyPURL.cgi?Dockey=P100HU1X.txt>
[73] <http://hdl.handle.net/10871/17302>
[74] <https://manualzz.com/doc/6717775/watercress-software-user-manual>
[75] <https://19january2021snapshot.epa.gov/sites/static/files/2016-03/documents/wmostv2_userguide_508final.pdf>
[76] <https://doi.org/10.30955/gnj.000532>
[77] <https://dl.acm.org/doi/10.1016/j.envsoft.2008.04.010>
[78] <https://www.epa.gov/sites/default/files/2018-02/documents/wmostv3_userguide_epa600r17_255final508.pdf>
[79] <https://doi.org/10.1016/j.envsoft.2013.12.018>
[80] <https://scholar.google.com.pk/citations?hl=th&user=kmcSpk4AAAAJ>
[81] <https://ru.dgb.unam.mx/server/api/core/bitstreams/7d319d67-7378-4524-a03d-364efa05ccc2/content>
[82] <https://centaur.reading.ac.uk/52792/1/URBAN%20WATER%20BALANCE%20AND%20HYDROLOGY%20MODELS.pdf>
[83] <https://assets.publishing.service.gov.uk/media/57a08969ed915d3cfd00022c/61183_ADB-MoU-Research-outputs_Vol8-SOBEK-Training-Report-Final.pdf>
[84] <https://doi.org/10.3390/w9040285>
[85] <https://www.epa.gov/sites/production/files/2018-02/documents/watershed_management_optimization_support_tool_final.pdf>
[86] <https://www.mdpi.com/2073-4441/9/4/285>
[87] <https://www.scribd.com/document/668360348/wst-2005-0276>
[88] <https://ihedelftrepository.contentdm.oclc.org/digital/api/collection/masters2/id/73845/download>
[89] <https://doi.org/10.5194/dwesd-7-1-2014>
[90] <https://water360.com.au/wp-content/uploads/2026/06/Technical-Report-108-Total-Water-HydroPlanner-Prototype-Feb-2013.pdf>
[91] <https://doi.org/10.36334/modsim.2011.i9.marleni>
[92] <https://www.waterselect.com.au/watercress/watercress.html>
[93] <https://www.sciencedirect.com/science/article/abs/pii/S0921344915000798>
[94] <https://paperzz.com/doc/8434017/uvq--a-tool-for-assessing-the-water-and-contaminant-balance>
[95] <https://doi.org/10.2166/wrd.2013.013>
[96] <https://www.sciencedirect.com/science/article/abs/pii/S1364815201000299>
[97] <https://www.academia.edu/13821770/Integrated_Urban_Water_Modelling_Past_Present_and_Future>
[98] <http://hdl.handle.net/2042/25394>
[99] <https://www.mssanz.org.au/modsim05/papers/maheepala.pdf>
[100] <https://www.academia.edu/66318635/Integrated_urban_water_modelling_using_Aquacycle_model>
[101] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7028841/>
[102] <https://repository.uwl.ac.uk/id/eprint/1824/1/RCR%20Paper-24-04-15.pdf>
[103] <https://climateresilientwater.org/wp-content/uploads/2026/05/Technical-Report-108-HydroPlanner-A-Prototype-Modelling-Tool-to-Aid-Development-of-Integrated-Urban-Water-Management-Strategies-April-2013.pdf>
[104] <https://pubmed.ncbi.nlm.nih.gov/29546883>
[105] <https://www.itia.ntua.gr/el/getfile/1121/1/documents/UWOT_EGU_2.pdf>
[106] <https://repository.uwl.ac.uk/id/eprint/2830/1/Behzadian%20et%20al%202014-DWES.pdf>
[107] <https://www.iahr.org/library/infor?pid=10981>
[108] <https://mp.uwmh.eu/d/Product/25>
[109] <https://b-watersmart.eu/the-urban-water-optioneering-tool/>
[110] <https://www.academia.edu/2903506/Modelling_the_urban_water_cycle>
[111] <https://www.epa.gov/hydrowq/wmost>
[112] <https://va-tekniksodra.se/wp-content/uploads/2019/02/ReuterwallThoren_2009.pdf>
[113] <https://idoc.pub/documents/dance4water-concept-for-integrated-modelling-of-the-water-cycle-for-the-city-development-wolfgang-rauch-university-of-innsbruck-ylyxe2z5pqnm>
[114] <https://publications.jrc.ec.europa.eu/repository/bitstream/JRC53258/eur_23966_en_wriedt.pdf>
[115] <https://www.waterselect.com.au/company.html>
[116] <https://doi.org/10.36334/modsim.2013.l15.hidayat>
[117] <https://www.wateronline.com/doc/part-3-urban-volume-and-quality-a-water-and-c-0002>
[118] <https://www.academia.edu/21436291/CSIRO_LAND_and_WATER_Final_Report_on_Application_and_Refinement_of_Assessment_Tools_for_the_CSIRO_Urban_Water_Program_Feasibility_Study>
[119] <https://scholars.unh.edu/dissertation/14>
[120] <https://scholars.unh.edu/ersc/107/>
[121] <https://hal.science/hal-03296707v1/file/21501-023GRA.pdf>
[122] <https://vuir.vu.edu.au/42848>
[123] <https://nepis.epa.gov/Exe/ZyPURL.cgi?Dockey=P100XAXO.TXT>
[124] <https://www.waterconnect.sa.gov.au/Content/Publications/DEW/MARSUO_WaterCress.pdf>
[125] <https://www.itia.ntua.gr/en/getfile/1597/1/documents/Abstract_SWITCH.pdf>
[126] <http://bgd.org.uk/wp-content/uploads/2015/11/BGDachieving_UWOT_C_Makropoulos1.pdf>
[127] <https://meetingorganizer.copernicus.org/EGU2011/EGU2011-6981.pdf>
[128] <https://hikom.grf.bg.ac.rs/stari-sajt/web_stranice/KatZaHidr/NaucniProjekti/2011-2014/37010/Dokumenta/2016-01-21-e-ADeletic-PlaningCitiesOfFuture.pdf>
[129] <https://repository.uwl.ac.uk/id/eprint/3321/>
[130] <https://19january2021snapshot.epa.gov/sites/static/files/2018-02/documents/wmost_v3_fact_sheet-final-16feb18.pdf>
[131] <https://www.enviweb.cz/85454>
[132] <https://uwmh.eu/images/files/uwot_hands_on_training_partII.pdf>
[133] <https://research.monash.edu/en/publications/modelling-transitions-in-urban-water-systems/>
[134] <https://www.waterselect.com.au/download.html>
[135] <https://www.gm-wics.sr.unh.edu/tech_report00_01/AppendB.htm>
[136] <https://agris.fao.org/search/en/providers/122535/records/65de23170f3e94b9e5caf9e0>
[137] <https://manuals.mikepoweredbydhi.help/2020/Release_Notes/MIKE%20URBAN%20Release%20Notes.pdf>
[138] <https://climateresilientwater.org/wp-content/uploads/2026/05/Technical-Report-37-Water-Accounting-Data-for-Integrated-Urban-Management-Modelling-Water-Accounting-Report-2-December-2010.pdf>
[139] <https://emf-creaf.github.io/medfatebook/basicwaterbalance.html>
[140] <https://mssanz.org.au/modsim2011/I12/savadamuthu.pdf>
[141] <https://doi.org/10.36334/modsim.2011.c4.snowdon>
[142] <https://eprints.qut.edu.au/208500/>
[143] <https://mp.uwmh.eu/media/product_files/3_UWOT_Handson_Training.pdf>
[144] <https://doi.org/10.1088/1755-1315/195/1/012018>
[145] <https://www.waterselect.com.au/mainblog/waterblog.html>
[146] <https://www.yumpu.com/en/document/view/8916335/sustainability-of-alternative-sewerage-and-water-servicing-options-/23>
[147] <https://www.itia.ntua.gr/en/docinfo/988/>
[148] <https://repository.library.noaa.gov/view/noaa/49467/noaa_49467_DS1.pdf>
[149] <https://dwes.copernicus.org/articles/7/63/2014/dwes-7-63-2014.pdf>
[150] <https://wiki.mikepoweredbydhi.com/mikeurban/setup/installation_2014_neuin2014>
[151] <https://www.scribd.com/document/379983427/DAnCE4Water-Concept-for-Integrated-Modelling-of-the-Water-Cycle-for-the-City-Development-Wolfgang-Rauch-University-of-Innsbruck>
[152] <https://ihedelftrepository.contentdm.oclc.org/digital/api/collection/masters2/id/98176/download>
[153] <https://www.mssanz.org.au/modsim05/papers/cleugh_1.pdf>
[154] <http://hdl.handle.net/10871/17361>
[155] <https://files01.core.ac.uk/download/pdf/43098288.pdf>
[156] <https://ihedelftrepository.contentdm.oclc.org/digital/api/collection/masters2/id/62508/download>
[157] <https://gmd.copernicus.org/preprints/gmd-2022-59/gmd-2022-59-manuscript-version3.pdf>
[158] <https://apps.usgs.gov/nccv/nccv2_documentation_v1.pdf>
[159] <https://doi.org/10.1007/1-4020-4685-5_6>
[160] <https://waterbalance.ca/technical_manual/>
[161] <https://cosmos.gnest.org/publication/532>
[162] <https://doi.org/10.14796/jwmm.r195-06>
[163] <https://vuir.vu.edu.au/35170/>
[164] <https://research.monash.edu/en/publications/dance4waters-bpm-a-planning-algorithm-for-decentralised-water-man/>
[165] <https://doi.org/10.1016/j.proeng.2014.02.014>
[166] <https://www.mssanz.org.au/modsim2011/C4/snowdon.pdf>
[167] <https://toolkit.ewater.org.au/Tools/Aquacycle/publications>
