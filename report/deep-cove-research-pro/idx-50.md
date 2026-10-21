# Content Caching Strategies for MEC-Assisted Video Streaming Through 2021

**Two families dominate the literature.** Through 31 December 2021, mainstream approaches were conventional policies—especially LRU, LFU, FIFO, and their variants—and policies using predicted popularity, viewing behavior, social relationships, or mobility. Conventional policies offer inexpensive, transparent decisions; predictive and behavior-aware schemes often improve delivery performance in their evaluated settings, but require useful data, timely updates, and sufficient edge resources. Neither family has a universal winner: request patterns, video granularity, cache capacity, placement, and replacement costs change the result. [1]

| Requested category | Main selection and update mechanisms | Decisive evidence | Overall judgment |
|---|---|---|---|
| Traditional Caching Schemes | Recency, frequency, arrival order, fixed popularity, and representation-aware optimization | LRU supports constant-effort updates; LFU approaches the top-\(M\) popularity mass under stationary independent requests | Strong baselines when simplicity and predictable overhead matter |
| Caching Schemes based on User Behavior or Content Popularity Prediction | Forecast demand, rank content or segments, coordinate placement, and refresh learned decisions | LSTM-C reports 20%–32% higher hit rate; HRS reports 12.3% average improvement in their respective evaluations | Attractive when fresh, locally relevant signals justify learning and coordination |

The LRU/LFU properties come from Hasslinger et al.; the predictive results come from the separate LSTM-C and HRS studies. [2][3][4]

**The comparison follows cache decisions.** The first section explains what conventional policies admit, retain, and evict, including video-specific extensions. The second distinguishes concrete prediction models and behavioral signals, then explains when their additional information improves hit rate, latency, backhaul use, or quality of experience. The literature scope is geographically unrestricted; individual results retain their dataset and experimental setting.

## Traditional Caching Schemes

**Traditional does not mean ineffective.** These schemes make decisions from observed accesses, known popularity, cache contents, or a specified optimization objective without requiring a learned forecast of future viewing. LRU and LFU remained widely used in video systems by 2021; more elaborate conventional schemes added aging, cooperation, file-size awareness, or transcoding. [5]

**Video objects need careful identification.** A cached object can be a complete video, a temporal segment, a spatial tile of a 360° video, or a segment encoded at a particular bitrate. This distinction matters because a server can possess a video but lack the requested segment/bitrate pair. In collaborative adaptive streaming, lookup can proceed from the local edge to neighboring edges and finally to the origin. [6]

### Classic replacement policies: LRU, LFU, and FIFO

**The principal contrast is memory.** LRU remembers the latest access, LFU remembers request frequency, and FIFO remembers insertion order. Their different interpretations of past demand explain both their usefulness and their failure cases.

| Scheme | Decision signal | Content admitted | Eviction when full | Main attraction |
|---|---|---|---|---|
| LRU | Last access | Newly requested object | Least recently requested object | Cheap adaptation to recent accesses |
| LFU | Request count | Requested or high-frequency object | Lowest-frequency object | Retains repeatedly requested videos |
| FIFO | Insertion order | Newly requested object | Earliest inserted object | Minimal bookkeeping |

These mechanics are described in the 2019 edge-assisted video-caching study and the contemporary video-caching survey. [3][1]

- **LRU — Least Recently Used**
  - **Core principle and selection:** Cache recently requested video objects, using recent access as evidence of likely reuse. A newly requested uncached object is admitted under the standard reactive policy.
  - **Placement, eviction, and updates:** Maintain a recency-ordered list. Accessed objects move to its head; a full-cache miss removes the tail—the object with the oldest last-access time. Classic LRU is a local replacement rule, not a replica-placement algorithm. Hasslinger et al. describe an implementation with constant update effort per request. [2]
  - **Advantages for MEC video:** Simple implementation, modest metadata, and no training stage make LRU an appropriate baseline for resource-constrained MEC servers. It can respond promptly when a newly active group starts requesting different videos.
  - **Limitations and trade-offs:** Recency alone can protect an unpopular video merely because it was requested recently. A succession of one-time requests can displace reusable content, while recency says nothing directly about the requested bitrate, future cell location, or remaining viewing duration. The first weakness is explicitly identified by Goian et al.; the broader MEC consequences follow from the signal LRU uses. [1]

- **LFU — Least Frequently Used**
  - **Core principle and selection:** Treat request frequency as a popularity indicator and preferentially retain frequently requested videos. Pure LFU accumulates historical counts; bounded-window versions restrict which observations contribute.
  - **Placement, eviction, and updates:** Increment request statistics as accesses occur. When admitting an object into a full cache, replace the cached object with the smallest frequency count. The classic policy determines local retention; cooperation and replication require an additional placement mechanism. [1]
  - **Advantages for MEC video:** LFU is particularly well matched to stable demand concentrated on a recurring set of titles. For equal-sized objects under an independent-reference model, with request probabilities ordered \(p_1\geq\cdots\geq p_C\), its long-run hit rate approaches \(h^*(M)=\sum_{i=1}^{M}p_i\). The reasoning is straightforward: a cache holding \(M\) objects maximizes hit probability by selecting the \(M\) largest probability contributions. [2]
  - **Limitations and trade-offs:** Historical popularity can become an obstacle. A formerly popular video may retain a large count after demand disappears, causing **cache pollution**—storage occupied by content whose past success no longer predicts reuse. This is especially consequential when an edge serves a changing local population. [3]

- **FIFO — First In, First Out**
  - **Core principle and selection:** Admit requested content in insertion order, without using its popularity or a prediction model.
  - **Placement, eviction, and updates:** Keep a queue of stored objects. When capacity is exhausted, a newly admitted object replaces the earliest stored object. The queue defines replacement rather than the geographical distribution of copies. [7]
  - **Advantages for MEC video:** Its chief benefit is operational simplicity. An edge node needs insertion-order bookkeeping rather than a popularity database, per-object learning model, or continuous reordering by frequency.
  - **Limitations and trade-offs:** Age in storage is a weak approximation of usefulness: an old but heavily requested video can be removed before a newer one-time request. Consequently, FIFO cannot explicitly protect a stable working set or anticipate handoffs and changing viewing patterns. Zhang et al. group it with fixed-rule policies that adapt poorly across dynamic video-access scenarios. [3]

**LFU does not always beat LRU.** In Zhang et al.’s three-dataset evaluation, the strongest conventional or forecasting baseline changed with both dataset and cache size. LFU led for small caches on the aggregate iQiyi trace, whereas LRU became strongest among the baselines for larger caches in some iQiyi settings; LFUDA occupied intermediate regimes. Thus, even before introducing a new predictor, cache capacity can change the preferred conventional policy. [3]

**The practical implication is conditional.** Prefer frequency when the same titles remain important over the relevant retention period; prefer recency when recent reuse is more informative than accumulated history. That judgment changes when request bursts consist mostly of one-time accesses, when demand shifts faster than counters age, or when the content unit changes from whole videos to bitrate-specific segments.

### Aging, windowed, segmented, and hybrid policies

**These variants correct specific weaknesses.** Aging and windows reduce stale-frequency effects; segmentation protects repeatedly reused objects from first-time arrivals; hybrids combine conventional signals. They remain conventional because they transform observed accesses through a fixed rule rather than learning a future-demand model. [1]

| Scheme | Principal signal | Retention preference | Replacement or update | Main purpose |
|---|---|---|---|---|
| LFUDA | Frequency plus cache age | Popularity adjusted for aging | Age-aware frequency replacement | Reduce stale-count pollution |
| JW-LFU | Fixed-window frequency | Frequently requested window contents | Reevaluate bounded-window counts | Discard old demand history |
| SW-LFU | Moving-window frequency | Recent recurrent demand | Roll counts over \(W\) requests | Follow popularity drift |
| S3-LRU | Repeated hits across three levels | Promoted, repeatedly used objects | Insert low; promote on hits | Protect established reuse |
| FIFO-LFU | Frequency/order mixture | Stable and aging-sensitive content | LFU with \(p\), FIFO with \(1-p\) | Mix demand regimes |
| LRFU | Recency/frequency mixture | Combined access value | Update combined priority | Balance two local signals |
| WGDSF | Weighted size/frequency-related factors | Weighted object value | GDSF-derived replacement | Broaden conventional scoring |

The first six mechanisms are documented by Goian et al. and Zhang et al.; WGDSF appears as a video-segment comparison policy in the 2019 multi-MEC study. [1][3][8]

- **LFUDA — LFU with Dynamic Aging**
  - **Core principle and selection:** Preserve LFU’s preference for repeated demand while incorporating cache-age information so that old popularity does not dominate indefinitely.
  - **Placement, eviction, and updates:** Apply frequency-based replacement with a maintained cache-age count. Aging changes the relative protection of resident objects as replacement proceeds; it does not itself choose neighboring MEC nodes for replicas. [3]
  - **Advantages for MEC video:** It directly targets the pollution problem of cumulative LFU. In Zhang et al.’s experiments, LFUDA was the strongest baseline over intermediate cache-size ranges on the iQiyi and iQiyi Small Cell datasets.
  - **Limitations and trade-offs:** Aging improves the treatment of historical demand but does not supply advance knowledge of a new release or a moving user’s next serving cell. Assessment: it is a useful middle ground when LFU is too persistent and LRU too easily disturbed, provided its aging behavior matches the workload. [3]

- **JW-LFU — Jumping-Window LFU**
  - **Core principle and selection:** Estimate usefulness from request counts within a predefined observation window rather than the entire request history.
  - **Placement, eviction, and updates:** Replace a cached item having the lowest frequency within that window with an item having a higher window frequency. Its defining operation is bounded-window local replacement. [1]
  - **Advantages for MEC video:** Limiting history prevents a video’s distant popularity from permanently protecting it. The policy can therefore refresh the edge working set without introducing neural-network training or external user data.
  - **Limitations and trade-offs:** Assessment: fixed observation boundaries can make decisions sensitive to when a burst occurs. A long window preserves stability but delays adaptation; a short window follows recent activity but can overreact to sparse samples. It still relies on counts rather than viewing continuation, mobility, or social propagation.

- **SW-LFU — Sliding-Window LFU**
  - **Core principle and selection:** Retain videos with the strongest request frequency over a continuously moving recent history.
  - **Placement, eviction, and updates:** Maintain counts over the latest \(W\) requests, adding new observations and removing expired ones. When replacement is needed, evict the least-requested object within that moving window. Hasslinger et al. show that this can retain constant update effort per request. [2]
  - **Advantages for MEC video:** It follows changing popularity more quickly than unbounded LFU while remaining inexpensive. Unlike a jumping window, its statistics evolve with each advancing observation.
  - **Limitations and trade-offs:** The window \(W\) determines the effective memory of the cache. Assessment: small \(W\) is attractive under rapid drift but noisy at lightly loaded edges; large \(W\) improves statistical stability but approaches LFU’s inertia. The relevant horizon therefore depends on request intensity as well as elapsed time.

- **S3-LRU — Three-Segment Segmented LRU**
  - **Core principle and selection:** Divide the cache into three levels so that repeated accesses provide stronger evidence for retention than a single recent request.
  - **Placement, eviction, and updates:** A new object enters the head of level 1 and displaces the tail of level 1. A hit promotes an object to the head of the next level, with entries shifted through the segmented ordering. The highest-popularity end is the head of level 3. [1]
  - **Advantages for MEC video:** Staged promotion separates speculative new arrivals from established reusable content, addressing a central weakness of ordinary LRU.
  - **Limitations and trade-offs:** Assessment: segment allocation determines how much space is available for exploration versus protected reuse. Repeated historical accesses still need not identify the right future location or video representation. Its significance is also architectural: it can serve as the reactive update layer beneath a predictive initialization policy, as in Tanzil et al.’s design discussed below.

- **FIFO-LFU — Hybrid Arrival-Order and Frequency Caching**
  - **Core principle and selection:** Accommodate both aging-sensitive new videos and videos with stable popularity.
  - **Placement, eviction, and updates:** In the version summarized by Goian et al., request frequency governs decisions with probability \(p\), and request order with probability \(1-p\). FIFO handles recent, age-sensitive content; LFU protects persistently popular content. [1]
  - **Advantages for MEC video:** A mixed policy can avoid committing the entire cache to either cumulative popularity or arrival order, which is useful for catalogs containing both news-like clips and long-lived movies.
  - **Limitations and trade-offs:** The source explicitly identifies category-dependent tuning of \(p\). A mixture suitable for stable entertainment titles may retain aging-sensitive videos too long; a mixture favoring arrivals can displace valuable recurring content. Its benefit therefore depends on matching the mixture to the catalog.

- **LRFU — Least Recently/Frequently Used**
  - **Core principle and selection:** Combine recent access and repeated access into a common retention decision rather than treating either as sufficient.
  - **Placement, eviction, and updates:** The survey’s formulation assigns recency weight \(p\) and frequency weight \(1-p\); resident priorities evolve as new accesses change these signals. Lower combined-priority content gives way when admission requires space. [1]
  - **Advantages for MEC video:** It offers a controllable compromise between responsiveness and protection of a recurring working set.
  - **Limitations and trade-offs:** Assessment: choosing the balance is itself a workload assumption. Combining two cache-local signals does not automatically capture video abandonment, a new episode’s release pattern, or geographical movement. Its value changes when those omitted signals become more important than recency and frequency.

- **WGDSF — Weighted Greedy Dual Size Frequency**
  - **Core principle and selection:** Use a GDSF-derived weighted policy rather than only recency or frequency. The documented enhancements include weighted frequency-based time and weighted document type.
  - **Placement, eviction, and updates:** Its role in the MEC-video comparison is replacement of cached video segments using these weighted factors. The policy therefore represents score-based conventional replacement, distinct from a prediction model or a cooperative placement optimizer. [8]
  - **Advantages for MEC video:** The broader factors provide a way to discriminate between objects beyond raw access order. In the cited multi-MEC simulation, WGDSF and RBCC generally delivered higher throughput than the policies labeled LRU and LFU.
  - **Limitations and trade-offs:** Assessment: richer weights introduce policy choices and still require a suitable relationship between the score and actual delivery value. In particular, a weighted object score is not equivalent to jointly considering a client’s playback urgency and whether its channel can sustain a cached representation.

**Adaptation has a tuning cost.** These variants improve conventional policies by deciding how much history to forget or how much protection repeated access deserves. Their advantage over prediction is that the control mechanism remains understandable and comparatively lightweight; their disadvantage is that the chosen window, weight, or segmentation expresses an assumption about demand rather than learning all relevant behavior.

**Use variants before adding complexity.** Where the dominant problem is merely stale LFU counts, an aging or sliding-window policy is a direct remedy. Prediction becomes more compelling when the missing information is genuinely forward-looking—such as upcoming requests, expected viewing continuation, or the user’s next location—rather than simply an inappropriate history length.

### Static popularity and known-popularity placement

**Proactive placement need not predict.** A policy can preload content before requests arrive while assuming popularity is already known. Such a policy belongs here because optimization or prefetching alone does not make it a popularity-prediction scheme.

| Scheme | Input signal | Content selected | Placement/update rule | Main benefit |
|---|---|---|---|---|
| Static top-\(S\) | Known popularity ranking | Most popular \(S\) objects | Fixed or epoch-based set | Simple concentration on demand |
| Liang–Hu LFU placement | Popularity and quality hierarchy | Top-\(S_n\), highest-quality videos | LFU placement/replacement | Multiple qualities from one copy |
| RPCC | Known popularity | Randomly selected popular content | Random proactive caching | Low-complexity baseline |
| BB-ZOMKP | Known popularity and file size | Optimal feasible full-file set | One copy per cluster; epoch refresh | Size-aware use of cooperative storage |

These policies are documented in the video-caching survey, Liang and Hu’s MEC model, ECMSP’s comparison, and the 2021 cooperative-placement study. [9][10][11][12]

- **Static Top-\(S\) Most-Popular Caching**
  - **Core principle and selection:** Fill the edge cache with the \(S\) most popular videos or objects according to a supplied popularity ranking.
  - **Placement, eviction, and updates:** The selected set remains resident in a static deployment; in an epoch-based deployment, a refreshed ranking determines the next resident set and displaces objects that fall outside it.
  - **Advantages for MEC video:** It concentrates limited storage on repeated demand and reduces contention on the origin server. For equal-sized objects and stable known popularity, this is the natural hit-probability-maximizing selection rule. Video-popularity caching discussion [9] Top-\(M\) probability argument [2]
  - **Limitations and trade-offs:** A fixed ranking does not follow temporal drift or differing local audiences. Assessment: with unequal video sizes, selecting titles only by rank can also waste an opportunity to cache a more valuable combination of smaller files—one reason to use explicit capacity optimization.

- **Liang–Hu LFU with Highest-Quality Placement**
  - **Core principle and selection:** Use LFU so that each base station stores its \(S_n\) most popular video files, keeping each selected file at its highest quality.
  - **Placement, eviction, and updates:** Popularity determines file placement and replacement; cached high-quality videos can be transcoded to lower requested qualities. The default simulation used a 1,000-video library, 200 cached files at the macro base station and 100 at small base stations, with Zipf exponent 0.56. Reported hit rates were around 50% and 40%, respectively. [10]
  - **Advantages for MEC video:** Popularity protects reusable titles, while transcoding avoids storing every quality separately. The design therefore links caching to MEC’s computing capability.
  - **Limitations and trade-offs:** Limited transcoding capacity can become the bottleneck even when the desired title is cached. The joint mixed-integer optimization is generally NP-complete, and local information exchange adds overhead. These are properties of the wider MEC delivery design, not computational costs of LFU counting alone. [10]

- **RPCC — Random Proactive Content Caching**
  - **Core principle and selection:** Sort content by popularity and randomly cache highly popular objects.
  - **Placement, eviction, and updates:** Admission is proactive and randomized within the popularity-oriented selection process. It is a useful static-popularity comparator for assessing the value of more directed spatial placement. [11]
  - **Advantages for MEC video:** It provides a simple way to preload popular videos without solving a detailed mobility-aware placement problem.
  - **Limitations and trade-offs:** In the ECMSP simulation, RPCC had the lowest hit ratio among the four compared schemes and substantial delay. The authors attribute this to random caching that did not consistently focus on hot content or account for spatial aggregation. Assessment: randomization is inexpensive, but it is poorly matched to situations where *which base station* stores the video is as important as the title’s overall popularity. [11]

- **BB-ZOMKP — Bound-and-Bound Cooperative Full-File Placement**
  - **Core principle and selection:** Maximize cluster-wide cache-hit probability using known video popularity, file size, and heterogeneous node capacities. The selection is a 0/1 multiple-knapsack problem, solved by exact bound-and-bound search.
  - **Placement, eviction, and updates:** Store complete files, prohibit file partitioning, and allow only one copy of each file inside a MEC cluster. Placement is recomputed for each cache epoch; a request counts as a cluster hit if any cluster node stores the file and relays it to the serving node. [12]
  - **Advantages for MEC video:** It improves diversity and packing without requiring a new predictor. In one dispersed-popularity setting with mean SBS cache size 100 GB, the paper reports up to 20 percentage points, or 40% relative, improvement in cluster-hit probability over popularity-only greedy placement.
  - **Limitations and trade-offs:** The problem is NP-hard, popularity is fixed within an epoch, and centralized coordination is required. Reported desktop computation included approximately 0.2–11 seconds in one parameter sweep. A single copy improves diversity but can increase intra-cluster delivery compared with local replicas. [12]

**Placement can matter without better forecasts.** BB-ZOMKP illustrates a crucial distinction: a policy may improve hit probability because it packs heterogeneous files more effectively, not because it predicts demand more accurately. The paper also finds that greedy placement becomes competitive when popularity is strongly concentrated, making the exact optimizer’s additional processing less worthwhile. [12]

### Video-specific cooperation, bitrate selection, and transcoding

**A hit must be usable.** Adaptive bitrate streaming requires a suitable representation of the right segment before its playback deadline. MEC therefore adds a storage–computation choice: store several representations, store one high-quality representation and transcode, or influence bitrate selection to reuse existing copies. [13]

| Scheme | Main decision input | Cached or selected unit | Update/control mechanism | Primary objective |
|---|---|---|---|---|
| JCCP | Requests, cache and processing state | Multi-bitrate video objects | LRU plus online scheduling | Reduce backhaul and access delay |
| Highest-bitrate-only caching | Representation hierarchy | Highest-rate segment | Downward transcoding | Reduce duplicate representations |
| Cache-aware bitrate coordination | Existing chunk/bitrate copies | Cached-compatible request | Greedy bitrate scheduling | Balance QoE and traffic |
| DPACA | Delay, quality, storage | DASH/scalable-video placement | Dynamic programming | Joint delivery quality and delay |
| DACPSs | Network stochastic information | Cooperative bitrate placement | Proactive resource allocation | Maximize slice revenue |
| DACRS | Changed network statistics | Refreshed video placement | Delivery-aware refresh | Adapt placement during delivery |

The corresponding studies distinguish replacement, representation selection, and delivery optimization rather than treating them as identical operations. [13][14][15][16][17]

- **JCCP — Joint Collaborative Caching and Processing**
  - **Core principle and selection:** Tran et al.’s 2017 scheme jointly considers which videos and bitrate versions to store and how to serve arriving requests, using LRU as its cache replacement foundation.
  - **Placement, eviction, and updates:** Make placement and scheduling decisions on each new request. Serve from the home MEC, a neighboring MEC, or the origin; when feasible, produce a requested lower bitrate by transcoding a higher cached version at the home or neighboring server. LRU supplies reactive admission and eviction. [13]
  - **Advantages for MEC video:** It operates online without prior popularity or arrival information. Simulations report higher cache-hit ratio and lower backhaul traffic and initial access delay than traditional approaches.
  - **Limitations and trade-offs:** Storing multiple representations increases storage consumption, while simultaneous real-time transcoding can exhaust edge processing. The underlying joint optimization is NP-complete, explaining the motivation for an online scheduling solution rather than repeated exact offline optimization. [13]

- **Highest-Bitrate-Only Caching with MEC Transcoding**
  - **Core principle and selection:** Kumar, Vineeth, and Franklin cache only the highest available bitrate of each selected DASH segment.
  - **Placement, eviction, and updates:** Store that representation at the MEC and transcode downward for lower-rate requests. This is a representation-admission rule: it replaces the practice of inserting multiple encodings with one reusable high-rate source copy, while object aging remains a surrounding cache-management concern. [14]
  - **Advantages for MEC video:** One stored representation can satisfy several bitrate choices. The real-time testbed reports less backhaul traffic, shorter video load time, and higher cache-hit rate than traditional store-and-forward caching.
  - **Limitations and trade-offs:** The mechanism exchanges storage duplication for computation. Assessment: it is attractive when storage is scarce and transcoding headroom exists; its advantage weakens when many simultaneous sessions require conversion or when processing delay threatens playback deadlines.

- **Cache-Aware Bitrate Coordination**
  - **Core principle and selection:** Mehrabi, Siekkinen, and Ylä-Jääski coordinate bitrate requests so clients favor chunks already cached, potentially accepting a slightly lower bitrate.
  - **Placement, eviction, and updates:** A low-complexity greedy scheduler selects cache-compatible chunk/bitrate requests under joint QoE, fairness, and traffic objectives. Lookup considers local and neighboring caches before origin retrieval; cache replacement and request adaptation are cooperating but distinct controls. [15]
  - **Advantages for MEC video:** It can reduce misses without improving the popularity estimate at all: changing the requested representation makes an existing copy useful. Collaborative caching further reduces origin transfers.
  - **Limitations and trade-offs:** The optimization is NP-hard, and traffic reduction can require lower selected bitrate. The operator-adjustable backhaul/fronthaul traffic ratio changes the balance. The study finds replacement affects backhaul more noticeably than QoE, underscoring that improved cache statistics need not translate proportionally into viewing improvement. [6]

- **DPACA — Adaptive Quality/Delay-Oriented Caching**
  - **Core principle and selection:** Deng’s 2020 DASH-based MEC scheme uses average end-to-end delay, provided video quality, and per-server storage constraints to obtain an optimized caching strategy.
  - **Placement, eviction, and updates:** Dynamic programming operates within a multi-server, SDN-based cooperative architecture. Its cache-control output is an optimized placement; it is classified here because its defining inputs are delivery quality and resource constraints rather than a named popularity predictor. [16]
  - **Advantages for MEC video:** Simulations report improved cache-hit ratio, significantly reduced end-to-end delay, and greater flexibility and adaptability.
  - **Limitations and trade-offs:** Assessment: optimizing quality and delay is more directly relevant to streaming than a title-only popularity ranking, but the result depends on how those objectives are weighted and on the accuracy of network-state inputs. Storage limits still force choices between representations and titles.

- **DACPSs — Delivery-Aware Cache Placement Strategies**
  - **Core principle and selection:** Rezvani et al.’s 2019 strategies proactively select cooperative multi-bitrate placement from network stochastic information, jointly allocating physical and radio resources.
  - **Placement, eviction, and updates:** Placement is the first phase of a cooperative caching/transcoding framework for heterogeneous virtualized MEC networks. Delivery subsequently responds to actual requests and channel conditions; DACRS supplies the refresh mechanism described next. [17]
  - **Advantages for MEC video:** The design exploits several delivery opportunities rather than treating storage as independent of radio and transcoding resources. Its stated objective is maximizing total network-slice revenue.
  - **Limitations and trade-offs:** Both placement and delivery optimizations are non-convex and computationally demanding. A lower-complexity resource-allocation framework reduces delivery complexity. Assessment: proactive resource optimization is useful when network statistics are sufficiently representative, even without introducing a learned popularity model.

- **DACRS — Delivery-Aware Cache Refreshment Strategy**
  - **Core principle and selection:** Update the cache as the stochastic information used for initial placement changes.
  - **Placement, eviction, and updates:** Refresh cooperative video placement during the delivery phase, replacing the assumption that the initial placement remains appropriate throughout operation. [17]
  - **Advantages for MEC video:** It explicitly addresses the mismatch between initial statistics and evolving delivery conditions. The paper reports up to 30% performance improvement for the combined DACPSs/DACRS design over traditional approaches.
  - **Limitations and trade-offs:** That percentage is a combined framework-level result rather than an isolated hit-rate or QoE gain for DACRS. Assessment: frequent refresh can improve relevance but also consumes transfer and optimization resources, so its operational value depends on how much conditions change between refreshes.

**Conventional caching can be sophisticated.** JCCP, representation-aware caching, and cooperative optimization show why “traditional” should not be equated with “single-node and simplistic.” A conventional replacement rule can support an advanced MEC delivery system, and a prediction-free optimizer can outperform naive popularity placement by managing storage, representations, and retrieval paths more effectively.

**The section’s practical takeaway:** use LRU/LFU and their variants as meaningful baselines, then add size awareness, cooperation, or transcoding when the dominant bottleneck is placement or delivery rather than demand prediction.

**Additional documented evidence**

**Baseline setting and evidence boundary**

- **MEC’s caching role.** MEC places storage and network functions near mobile users; edge caching stores video at the network periphery so that requests can avoid part of the core or backhaul path, reducing traffic, service latency, congestion, and—in limited-backhaul settings—operator or inter-ISP cost [109]. A 2021 MEC-server study likewise frames caching and video adaptation as ways to increase edge-cache hits and reduce backhaul congestion and access delay [113].
- **Video object and request path.** In the reported DASH setting, a video is divided into chunks of approximately **2–10 seconds** and each chunk is encoded at multiple quality levels; clients request chunks and qualities, while an edge access point can use cache state, client-buffer state, available bitrates, and backhaul capacity when serving them [109]. The source uses a single WiFi access point rather than explicitly identifying the node as an MEC server, so it is adjacent edge-cache evidence rather than conclusive MEC evidence.
- **Direct pre-cutoff comparator evidence.** A paper publicly dated **2021-02-01** evaluates **LRU, LFU, and FIFO** in edge-cache-assisted **360° live video streaming**. The video is represented through multiple quality layers and tiles; the proposed scheme forecasts requests with LSTM, prefetches content, and permits users in overlapping small-base-station coverage to receive data from any suitable station [76]. The proposed scheme—not the three traditional baselines—is reported as superior in delivered video quality, cache-hit ratio, and backhaul-link usage [76].
- **Traditional-family result.** LRU, LFU, and FIFO therefore have direct pre-cutoff evidence as comparison policies in mobile edge-relevant video caching, but a named comparison in one study is not by itself proof of widespread adoption. The profiles below distinguish verified use, mechanism details, and unresolved mainstream status.

**Least Recently Used (LRU)**

- **Classification and MEC-video relation.** **LRU is a traditional, non-predictive, recency-based replacement policy.** In the 2020 EdgeDASH study, a WiFi access point admits all video contents and uses LRU to manage its limited cache; the cached object is indexed as video \(j\), chunk \(k\), and quality \(m\) [109]. In the 2021 360° live-streaming study, LRU is directly evaluated as an edge-cache video policy [76]. Neither description gives LRU a demand-prediction or learning model.
- **What LRU caches and admits.** In the EdgeDASH model, admission is broad—the access point “admits all the contents”—while LRU controls which video chunks and quality representations remain in the cache; the cache capacity is measured in **\(S\) bits** [109]. The 360° study confirms the broader video setting—quality layers, tiles, mobile users, and live delivery—but does not specify whether the LRU baseline acts on whole videos, tiles, layers, or individual segments [76]. That baseline-specific granularity is therefore **not reported**.
- **Replacement rule.** LRU maintains observed access order: a newly inserted or fetched object is placed at the most-recent position, a cache hit moves the object toward that position, and capacity pressure removes the least recently accessed object. Generic descriptions represent this as inserting at the head of a list, moving hits to the head, and deleting the tail when free memory falls below a threshold [77]. The generic Java description similarly removes the eldest entry when the access-ordered map exceeds capacity [164]. These sources explain the algorithm, but they are not pre-2022 MEC-video evaluations.
- **Source-specific variant and qualification.** A later CDN patent applies LRU to VOD and live-event **segments**, with high- and low-priority LRU lists: near-live segments are placed in the high-priority list, older segments can move to the low-priority list according to age, and space can be recovered from the low-priority tail [77]. Its prior-art date is **2023-04-06** and publication date is **2024-10-10**, so it cannot establish historical MEC-video evidence by 2021-12-31; it also describes CDN edge servers rather than explicitly identifying MEC nodes [77].
- **Decision signal.** LRU uses observed access recency or last-access time, not a popularity denominator, forecast, or prediction horizon [110]. A GitHub implementation discussion proposes storing last-access dates and tracking recency with a linked list or timestamp, again without a popularity model [121]. The **Zipf exponent 1.2** used to generate video requests in the EdgeDASH evaluation is a workload assumption, not an LRU input or prediction model [109].
  - LRU is simple to understand and implement and is useful when recently accessed objects are more likely to be requested again soon [110]. Its advantage is therefore conditional on temporal locality, not universal across video workloads.
  - In an edge-cache video system, retaining recently requested chunks can reduce repeated upstream retrieval; the broader MEC/edge benefit is lower traffic and latency, but the cited MEC evidence does not attribute a particular numerical gain to LRU itself [109].
  - The EdgeDASH evaluation intentionally assumes a **high-capacity cache** to minimize the measured effect of admission and replacement; consequently, its cache-hit, bitrate, stall, and latency results cannot be interpreted as an LRU-specific superiority result [109].
  - The 2021 360° paper reports that its LSTM-prefetching proposal outperforms LRU, LFU, and FIFO, but it does not report a separate LRU advantage or an LRU-specific cache-hit, quality, or backhaul value [76].
  - LRU tracks recency but overlooks access frequency; under limited capacity or dynamic request patterns, this can produce lower hit ratios than policies that retain repeatedly requested objects [165]. The cited source is a **2025** paper and is used only as later diagnostic evidence, not as evidence that this limitation was newly established after the cutoff.
  - Under a generic round-robin workload in which the requested set exceeds cache capacity, LRU objects can continually enter and leave without a hit, whereas LFU can retain repeatedly referenced objects [166]. This is a generic proxy result, not a MEC-video measurement.
  - For heterogeneous object sizes, a large recently accessed file can displace many smaller files and rapidly reduce the hit ratio; this limitation is described in a later MEC-cache replacement discussion [165].
  - Recency does not necessarily match the value of retaining a segment for live-event scrubbing. A later edge-streaming design warns that missing segments can impair rewind, pause, and fast-forward, require numerous origin re-downloads, saturate the upstream link, and reduce service to other clients [77]. This is a later CDN observation, not pre-cutoff evidence, but it identifies a material live-video failure mode.
  - Distributed LRU requires consistent access state across nodes. The CacheTower discussion describes local-only eviction as a limitation and says that distributed LRU would require broadcasting every access, including local accesses, through the cache system and distributed backends; maintaining current cache data is also described as “fiddly” [121].
  - A later Android image-cache report illustrates capacity-dependent operational problems: a **100 MB** LRU cache sometimes filled quickly and caused performance degradation, while in other cases images remained cached for months and wasted storage [111]. The report is dated **2026-03-14**, concerns images rather than video at MEC, and is not historical evidence for this review.
- **Evidence date and mainstream status.** The supplied evidence establishes qualifying LRU use in a pre-cutoff 2020 edge-video study and an explicit publication date of **2021-02-01** for direct 360° live-video comparison [109][76]. It does **not** establish an absolute first-public LRU date in MEC video streaming. LRU is therefore a **verified traditional-baseline candidate** and a strong roster member, while the exact prevalence of LRU across the entire pre-2022 literature remains unquantified in the supplied evidence. Later generic pages dated **2024-07-15** and **2024-10-10**, the 2024 patent, the 2025 MEC replacement paper, and the 2026 operational report cannot be backdated to prove mainstream status by 2021-12-31 [77][110][111][164][165].

**Least Frequently Used (LFU)**

- **Classification and MEC-video relation.** **LFU is a traditional, observed-frequency policy rather than a prediction-based policy.** The direct 360° live-video paper evaluates LFU as an edge-cache comparator on **2021-02-01** [76]. Generic descriptions define LFU by counting references or accesses and removing the item with the lowest count [164][166]. The direct video paper does not state a predictive model, popularity forecast, or learning component for LFU.
- **What LFU caches and admits.** The 2021 edge-video evidence identifies LFU as a comparison algorithm but does not report whether it caches complete 360° videos, tiles, quality layers, chunks, or representations, nor does it specify an LFU admission rule [76]. Generic implementations act on cache keys or items: a newly inserted item starts with frequency **1**, and later `get` or `put` operations increase its observed frequency [164][166]. Those generic items must not be mistaken for a demonstrated MEC-video object granularity.
- **Replacement rule.** When capacity is reached, LFU removes the cached item with the lowest observed reference frequency; if several items tie, the least recently used or oldest item is removed [164][166]. A later MEC-cache replacement paper describes the same general state as a per-file frequency table and eviction of the minimum-frequency file [165]. The supplied direct 2021 video paper does not confirm that this exact implementation was used in its LFU baseline, so its baseline-specific tie-break and update rules remain **not reported**.
- **Decision signal and model status.** LFU uses historical request or access counts. The generic source increments frequency on every `get` or `put` and supplies no popularity denominator, forecast window, prediction target, or learning model [166]. A frequency count is therefore an observed workload statistic, not forecast popularity.
  - LFU favors repeatedly requested objects and can retain them when a cache serves many requests under limited storage [166].
  - In the generic round-robin example where the request set exceeds capacity, LFU performs better than LRU because it retains frequently referenced resources while LRU continually replaces them [166]. This condition-specific comparison is not a MEC-video experiment.
  - A later source reports the strongest LFU behavior under an **Independent Reference Model (IRM)**—requests independently drawn from a fixed distribution—and in its heterogeneous-file-size simulations [165]. The source is dated **2025-03-03**, so this is later corroboration of a workload condition, not pre-cutoff evidence.
  - The 2021 360° study’s reported superiority belongs to its LSTM-prefetching proposal; no LFU-specific advantage, hit ratio, quality value, or backhaul value is reported [76].
  - Historical counts can become stale when popularity or requests change; the later MEC replacement discussion describes LFU as vulnerable to outdated statistics in dynamic environments and to an aging problem [165]. No frequency-aging method is reported for the direct 2021 LFU baseline [76].
  - Implementation cost depends on the data structure. A simple frequency-map implementation scans all counts in **\(O(n)\)** time to find the minimum, while a frequency-list implementation can require **\(O(n)\)** worst-case work to locate an accessed item [166]. A later implementation reports **\(O(\log n)\)** behavior for its own frequency table [165]; these are implementation-specific results, not a universal LFU complexity.
  - LFU can retain historically popular content after demand has shifted, so it is less suitable when video popularity changes quickly unless counts are aged or reset. The supplied direct video paper does not report such an aging mechanism, cache window, or forecast horizon [76][165].
  - Frequency ties require a secondary rule, commonly recency or insertion age; the tie-break can alter which video object survives even when frequency counts are equal [164][166].
- **Evidence date and mainstream status.** **2021-02-01** is the explicit qualifying public date for LFU’s direct use in edge-cache-assisted 360° live-video streaming [76]. The supplied record confirms pre-cutoff application as a comparison baseline, but the direct MEC-video evidence is a single named study and does not establish literature-wide mainstream status. LFU should therefore be retained as a **traditional baseline with verified pre-cutoff use but incompletely established prevalence**.

**First-In, First-Out (FIFO)**

**Additional traditional-policy leads**

- **Expanded names beyond the initial examples.** A later MEC-cache replacement paper names **Random, ARC, TinyLFU, Incremental LRU (iLRU), and W-iLRU** alongside LRU and LFU [165]. It describes ARC as using two self-tuning lists for recent and frequent access, TinyLFU as using a Counting Bloom Filter for historical frequency plus aging, and iLRU as initially caching only part of a requested file and increasing the cached portion with subsequent requests; W-iLRU is presented for bursty requests [165]. Because that source was published on **2025-03-03** and the supplied passages do not establish direct pre-2022 MEC-video use for these policies, these names are discovery leads rather than confirmed additions to the historical mainstream roster.
- **ARC-specific status.** The available ARC evidence says that ARC is more complex and may retain older frequently used files for longer, potentially reducing cache efficiency; it does not identify the exact object evicted when full [165]. The 2021 LRU/LFU/FIFO comparison paper does not identify ARC, so its **2021-02-01** publication date cannot be transferred to ARC [76]. No qualifying pre-2022 MEC-assisted video advantage for ARC is established in the supplied evidence.
- **Earlier citation lead.** The later paper cites a **2019** work on adaptive-bitrate video caching and processing in mobile-edge computing networks, and its own discussion identifies LRU as relevant to MEC cache replacement [165]. The supplied passage does not show that the cited 2019 work evaluated LRU, LFU, or ARC, so it is a discovery lead rather than proof of a first qualifying date or mainstream status.
- **Evidence qualification.** Generic LRU/LFU implementation pages dated **2024-07-15** and **2024-10-10**, a generic caching-proxy discussion, a software implementation discussion, the **2024-10-10** patent, the **2025-03-03** MEC replacement paper, and the **2026-03-14** Android-cache report can clarify mechanisms or failure modes, but none supplies qualifying pre-2022 MEC-assisted video evidence for a new traditional scheme [77][110][111][121][164][165][166].

- **LFU—traditional/observed-frequency.** Admit requested segments if space; evict the lowest global request count Γg; no prediction model is reported. It is simple and widely used but suffers cache pollution; LFU-DL’s lifespan remedy reached ARC/LRU-level VoD performance. A wireless-edge test on 2020-01-21 (10 clients, 100 files, 2–5-minute clips, 5-Mbps segments, 5–15% cache, 3 hours) found LFU-Index better than LFU/LRU; both neared Belady only with very large caches. A 2006 LRLFU proxy hybrid improved byte-hit ratio, delayed starts and CPU, but was not MEC; 2022 MEC evidence is post-cutoff. [167][117][46][163][51][168]

- **Least Recently Used (LRU)—traditional, retained mainstream baseline.** LRU is a non-predictive traditional policy and is repeatedly used as an edge-video baseline [56][57]. The earliest dated qualifying record visible here is August 2019, although the supplied evidence does not prove that it is globally the first [122]; another edge-video experiment was published on 2021-12-01 [57]. Depending on the study, the object is a file, video chunk, or tile. In the VoD simulation, 1,000 video files were divided into sequential chunks; a requested file is added to or moved to the queue head, and the least recently requested file at the tail is evicted when capacity is insufficient [122]. In the 360° setting, popular videos are divided into edge-cached tiles and recency determines eviction [57].  
  - **Admission and signal:** LRU uses observed request recency, not a prediction or learning model. An LRU filter can also act as an admission layer: an unseen chunk is treated as unpopular and sent to the origin while entering the filter; a repeated chunk is treated as popular and forwarded to the edge cache [118].  
  - **Advantages and limits:** Implementation is simple [56]. In a 2019 testbed with 10^7 chunks, 1.125-MB chunks, an edge capacity of 10^5 chunks, 1,400 clients, Zipf popularity, and a 40-ms origin delay, the optimally sized filter produced a 48% global hit ratio versus 44% without filtering, a reported 9% improvement; the paper also reports 36% lower chunk-download time and 37% lower cache CPU load [118]. These are workload-specific results. LRU can perform poorly for unequal file sizes and, in a separate single-try mobile-P2P model where uncached packets cannot be cached later, it is inapplicable [122][103]. The MEC-media record also reports poor hit-ratio and latency performance for basic LRU-like policies [56]. In a 2021 experiment using 48 users and two 360° videos while varying cache size, LFU achieved the greater average hit rate [57].

- **Least Frequently Used (LFU)—traditional, retained mainstream baseline.** LFU uses observed request frequency rather than forecast popularity or a prediction model, and frequency determines eviction; the supplied edge-video passage does not report its exact admission, tie-breaking, or counter-update rule [57]. In the 2021-12-01 360°-video experiment, LFU operated on edge-cached tiles and achieved a greater average cache hit rate than LRU across varying cache sizes, using 48 users’ head-movement data and two videos [57]. It is therefore a qualifying traditional baseline, but not universally superior. The related LFRU variant is distinct: it combines frequency and recency through a CRF value to resolve frequency ties and evicts the lowest-CRF content [56].

- **First-In, First-Out (FIFO)—traditional candidate, not confirmed mainstream for direct MEC video by 2021-12-31.** A 2019 video-edge testbed used Apache Traffic Server with FIFO as its cache-admission policy, while a 2019 mobile-P2P study evaluated FIFO but neither study explicitly established MEC deployment [118][103]. A later source dated 2022-04-21 describes the conventional oldest-first rule—new content enters the queue tail and the head is removed—but that source is discovery-only for the requested cutoff [58]. In the P2P study, FIFO performs poorly for packet IDs below \(L-A\), behaves like infinite caching for IDs at least \(L-A\), and requires \(A\geq0.7L\) to reach server load \(\leq0.05\); with five connections, random caching used 40% fewer packets for the same reported benefit [103]. Thus FIFO remains an uncertain traditional candidate rather than a confirmed mainstream MEC-video scheme.

- **LRU status and limits.** Pre-cutoff evidence includes 2020 edge comparisons and APNOMS-2021’s “traditional weighted LRU” MEC model, but not broad direct MEC-video mainstream status. [170][94] Direct MEC-video LRU appears only in a post-cutoff 2022 system: its Cache Manager evicts segments for local/neighbor MEC or 5GC service; the first qualifying pre-2022 date is unresolved. [66] Temporal locality helps; volatile popularity and long inter-reference times hurt. At 30 proxies with \(A=100\), LRU had a 0.0 hit ratio and about 0.6% bandwidth saving; a 4-4-4 test needed 1,600 blocks (22%) versus LFU’s 100 (1.4%), while CDN traces required up to 3.5× the cache to match AViC. [59][105][123][171]

- **LFU (traditional).** It uses observed access/request frequency, not prediction; its exact full-cache victim and state update are unreported. [123][59] It was repeatedly tested with LRU/Prefix in 2009 wireless multimedia streaming (not explicitly MEC) and compared as an edge baseline in 2020. [59][170] At 30 proxies and \(A=100\), it achieved about 30% bandwidth savings and a 0.30 hit ratio; skewed prefixes favor it, whereas uniform, non-sequential, or volatile popularity reduces benefit, and aging addresses cache pollution. [59][123] Direct MEC-video mainstream status and date remain unresolved.

- **FIFO (First-In, First-Out)—retain cautiously.** FIFO is a traditional reactive queue: new content enters in arrival order and, when full, the oldest item is removed independently of access frequency or recency [120]. Its advantage is implementation simplicity and minimal state; its limitation is that it ignores locality and frequency, and the supplied evidence reports no FIFO-specific MEC-video benefit [120][174]. A MEC-multimedia source dated **2021-12-01** identifies FIFO as conventional reactive caching, whereas dated 2021 coded-video and 2020 wireless-edge comparisons are adjacent rather than direct MEC-video evidence [148][174][149]. Thus FIFO is a canonical candidate, but its direct MEC-video mainstream status and earliest qualifying date remain less firmly established.

- **MRU (Most Recently Used)—unconfirmed.** The supplied edge-cache comparator describes MRU as a static policy that discards the most recently used contents and does not consider future popularity; its admission, placement, retention, and video-object unit are unreported [147]. No direct MEC-video application is shown: the dated **2014-12-19** LRU–MRU record concerns FPGA/disk I/O, not video streaming [146]. Generic material calls MRU simple and predictable but not always optimal for hit rate; another page labels LRU behavior—keeping the most-recent item and evicting the least-recent—as “MRU,” conflicting with the direct MRU definition, so neither establishes MEC-video status [150][147]. No qualifying MEC-video evidence date is established.

- **Random replacement—unconfirmed.** When full, random replacement selects an arbitrary cached item; it is simple and requires no access-frequency or recency tracking, while the supplied generic description does not identify a video-object granularity [120][172]. A mobile-video edge simulator using Wi-Fi APs and cellular base stations evaluated random replacement with LRU and LFU over **5–600 cache items** and found similar hit rates, especially at larger capacities [132]. Because MEC is not stated, mainstream MEC-video status and a qualifying date remain unconfirmed; one separate edge comparison reported random replacement as the weakest traditional baseline [175].

- **Adaptive Replacement Cache (ARC)—unconfirmed.** ARC is a pre-cutoff named self-tuning replacement cache dating to **2003**, but the supplied evidence does not demonstrate its use in MEC-assisted video streaming or provide a qualifying MEC-video date [145]. A post-cutoff generic evaluation describes separate recency/frequency queues with ghost-queue-based sizing and lower miss ratios than LRU in some traces, but also workload-dependent sizing failures; this is background only, not cutoff evidence [112].

- **Least Recently Used (LRU; traditional/reactive caching).**
  - **Working principle and object:** LRU admits the requested video after a miss, records request recency, and when capacity is full evicts the least recently requested object; in MEC video systems the object may be a whole video, DASH segment, or representation.[154][156][80] Its signal is observed time since the latest request, not an explicit demand-prediction model.[156]
  - **Status and date:** LRU is repeatedly treated as a classical, lightweight comparison baseline, including direct edge-video evaluations before the cutoff; qualifying MEC/edge-video uses are shown by 2016 and 2021, although the exact first qualifying public date is not established.[68][80][96] A January 2013 LRU publication record is earlier but concerns non-MEC cache analysis.[96]
  - **Advantages:** LRU reacts quickly when popularity changes and has low operational overhead; one five-city video-caching study found it among the fastest heuristic algorithms.[96][156] In a study-specific RAN experiment with a **200 GB** cache, LRU achieved a **0.58** hit ratio, required **42 Mb/s** mean backhaul bandwidth under high user dynamics, delivered initial delay of **5 s or less** for **0.77** of requests, and supported **275 concurrent videos** at blocking probability **0.01**.[154] These metrics are study-specific; hit ratio means edge-served requests divided by total user requests.[96]
  - **Limitations:** LRU ignores frequency and therefore may discard long-term popular videos for recently but briefly popular ones, particularly under uneven arrivals.[156] It may be ineffective in small, distributed RAN caches, and it does not match cached segment representations to channel state.[154][98] Treating segments or representations independently can also scatter a video's cached pieces and cause playback-quality fluctuation.[68] In the cited MEC simulation, a competing scheme's throughput was **60.7%** higher than LRU at **2.4 GB** total MEC cache space; this is not a universal ranking.[98]

- **Least Frequently Used (LFU; traditional/reactive frequency caching).**
  - **Working principle and object:** LFU uses observed request counts and retains or replaces the least-frequently requested item; standard LFU was explicitly run at an MEC cache on DASH segments/representations.[68][158] A local implementation also maintained a normalized request ratio rather than relying only on raw lifetime counts.[154] It is not prediction-based unless a named variant changes the rule: OPLFU, for example, predicts future popularity with linear, power-law, exponential, or Gaussian functions and maintains the cache using the estimated popularity.[96]
  - **Status, benefits, and date:** LFU is repeatedly identified with LRU as a classical MEC/video-caching baseline; direct MEC-DASH evidence is available by 2016, but the exact first qualifying date is unresolved.[68][96] In the reported LTE-A experiment (**66 sessions**, **1,928 s**, approximately **2,900 segment requests**, an **800 MB** cache), LFU produced **9.83 Mbps** average bitrate and **37.6%** 4K-segment requests, versus **4.76 Mbps** and **2.5%** without edge caching.[68] LFU is generally more favorable when popularity is stable.[156]
  - **Limitations and evidence conflict:** Frequency counts can retain stale objects after a short popularity burst and adapt poorly to changing access patterns; heuristic LRU/LFU methods are lightweight but can miss diverse, dynamic viewer interests.[96][158] In the LTE-A test, LFU caused over **50%** more switched quality levels than the QoE-driven policy and had **135** switches across the 720p threshold because it does not preserve segment continuity.[68] One MEC paper labels its comparison entry “LFU: Least Recently Used”; that is a source-label error/ambiguity, not evidence that LFU and LRU are the same policy.[98]

  - **FIFO:** FIFO replaces the oldest stored object; it appears in a 2011 video-caching benchmark and later ICN comparisons, but the evidence does not establish a direct MEC-assisted video-streaming deployment or mainstream status by **2021-12-31**.[152][151] A 2020 paper’s FIFO queues are only a data structure for retaining arrival times, not FIFO cache eviction.[156]
  - **MRU, random replacement, and ARC:** MRU is supported here only by a generic Smart City traffic-stream evaluation, which reports better behavior for smaller caches; qualifying MEC-video use, detailed object rules, advantages, limitations, and first date remain unestablished.[82] Random replacement evicts a randomly selected cached item and has minimal state requirements, but the cited **2014** evidence is from CCN rather than MEC video.[158] ARC combines recency and frequency in generic cache experiments; its cited evidence is website-oriented, reports no MEC-video object rule, and finds its advantage negligible as cache size grows.[153] A 2004 ARC bibliography entry and the supplied evidence do not establish a qualifying MEC-video date or mainstream status.[157][96]

- **Collaborative Video Cache Management Strategy in Mobile Edge Computing.** A later source identifies a **2021 WCNC** paper with this name, establishing pre-cutoff existence but not mainstream or canonical status by **2021-12-31**.[176] It belongs primarily to the cooperative/hybrid category: MEC servers serve mobile users locally and exchange content through backhaul links, while the supplied evidence does not report the named strategy’s exact placement, eviction rule, coordination signal, prediction model, or forecast horizon.[176] Related collaborative MEC work seeks lower access or delivery delay, higher hit rate, lower backhaul use, and lower initial delay under finite storage and inter-server capacity; mobility can trigger server switching and new-cache misses, requiring neighbor or cloud retrieval.[176]

- **LRU (traditional):** 2019 MEC live-DASH evidence shows reactive caching of recent chunks after misses, exploiting temporal locality [48]. It is a recurring baseline by 2021-12-31, but mainstream status is unestablished; its heuristic degrades with smaller caches, higher live latency, and changing popularity [48][115]. Eviction detail and first date are unresolved; variants were evaluated 2021-05-10 [100].
- **LFU (traditional):** A 2021 edge-video study applies LFU per cache and serves misses from another SBS before the remote server [115]. No standalone advantage, eviction detail, or first date is reported; LRU/LFU adapt poorly to changing popularity, while variants were complementary across two video platforms (2021-05-10) [100]. Mainstream status remains unproven [115][100].
- **Screening:** Requested-tile HAS/360° proxy caching is mobile but not direct MEC evidence [99]; **ARC** has no supported MEC-video classification or advantage [48]. Movielens and VR/TLRU records are post-cutoff (2022) [116][101].

- **MEC/video:** By 2021-12-31, MEC at BSs cached/processed multibitrate video for mobile users; cooperation reduced backhaul [54][52]. A 2017 setup used 3 servers, 1,000 videos and four variants [52].
- **LRU—traditional/reactive:** Miss→store the video/object; full→evict the least-recent by observed request time, not prediction [54][85]. Evidence: 2016-12-08/2019-01-01; repeated baseline use supports mainstream status. Mobility, sparse BS demand, bursts and thrashing limit performance [52][54][83][85].
- **LFU—traditional/reactive:** Evict the least-frequent by observed counts; no named model [54][178]. It suits multi-location/low-entropy demand, but local LFU may keep excess replicas and perform poorly; date and universal superiority remain unestablished [178][83].
- **FIFO/RR/cooperation:** FIFO is traditional, but 2009 evidence is P2P-VoD, not MEC; status is unconfirmed [177][84]. RR randomly evicts when needed, with no predictive signal; larger capacity makes it resemble LRU [178]. A WCNC 2021 cooperative proposal is pre-cutoff but not shown mainstream: related MEC/D2D placement chooses maximum utility and replaces least utility only if utility rises; delay/backhaul gains are reported, but its local rule, model and horizon are unknown [179].

- **MEC.** eNodeB/gNB edge caches serve DASH segments locally or cooperatively before the cloud, reducing delay and backhaul [87][181].
- **LRU—traditional/reactive.** Evidence includes a 2016 DASH mention, a 2019 MEC evaluation, and pre-cutoff LRU-RR [73][87][63][181]. Miss→insert; full→evict the least-recently-used segment/object by access history; no model [71][63]. It is a baseline, but costly updates and recency miss channel/QoE shifts [71][63]. Overall—not LRU alone—the system achieved 60% hit and 69% lower backhaul utilization [63].
- **LFU—traditional frequency.** Standard LFU and pre-cutoff LFU-RR count references/current popularity and evict the least-frequency content [73][181]. Stale bursts and new items can be misranked; segment replacement can scatter videos [71][73]. In 2016 (10 phones; 1,928 s; 66 sessions), LFU delivered 9.83 versus 4.76 Mbps without caching, 37.6% 4K requests, but over 50% more switching; at 3.0 GB, CTRA throughput was 37.54% higher than LFU-RR [73][181]. A 2019 source mislabels LFU as LRU [87].
- **FIFO/MRU/ARC.** FIFO evicts the oldest item using insertion order; it is simple but least specialized and lacks direct MEC-video evidence [88][71]. MRU appears only for generic blocks/prefetching, with up to 42% improvement; ARC is unnamed, so neither qualifies by 2021 [124].

- **LRU (Least Recently Used)—traditional/mainstream baseline.** LRU records observed recency only, not a prediction model; on overflow it admits new video/chunk content and evicts the least recently accessed or arrived object [74][104][106]. Direct MEC use is shown in sources dated **2018-01-01** (Octopus, without inter-edge cooperation) and **2021-10-18** (SBS neighbor fallback) [74][119]. Its benefits are simple, constant-time operation and adaptation to changing requests; unpopular requests can displace popular content, especially with small or growing caches [104][106]. Common, repeated-baseline use supports mainstream status, while CCA’s cold-start delay and remote-bandwidth gains are not LRU gains [119].

- **LFU (Least Frequently Used)—traditional/mainstream baseline.** LFU uses historical access counts rather than forecasts and evicts the least-frequent object; P-LFU, PP-LFU and OP-LFU are distinct predictive variants [90][104]. LFU was a direct MEC comparator published **2021-10-18** and a recurring/common video-cache baseline [75][119]. Its counts become stale under changing popularity: hit rate can fall after “a few tens of days”; the **5.325%** result reported in 2019 is collective for FIFO/LRU/LFU/RANDOM, not LFU alone [75][104]. LFUDA’s dynamic aging is distinct, and generic VoD gains of **20%** with perfect prediction and **10%** with curve fitting are not MEC-specific [90][106].

- **MEC edge role:** BS/SBS caches serve video files/360° tiles locally; misses use MBS/backhaul, reducing latency and traffic [61][67][69].
- **LFU (traditional, recurring by 2021; 2018 evidence, first date unknown):** observed counts—not forecasts—retain popular files/tiles and evict the least-frequent item [61][67][69]. **Benefit:** lower backhaul; **limit:** finite capacity/misses [67]. A 1,000-video/15-user run reports ~50% MBS and 40% SBS hit rates [61].
- **LRU (traditional):** observed recency evicts the least-recently requested video/tile; no forecast [69]. No specific gain is reported; cooperative MEC evidence finds no significant LRU–LFU difference [67]. FIFO is a comparator [69]; FIFO/MRU/ARC status by 2021 is unestablished [184][185].

- **Adaptive Replacement Cache (ARC)—traditional adaptive candidate.** ARC divides cache space between items referenced exactly once and at least twice, using recency/frequency state rather than an explicit forecast [125]. Its earliest cited public evidence is **March 2003** [125]; no direct MEC-video use, object-level eviction rule, MEC metric, or mainstream status is established. Its cited potential is self-tuning and low overhead, but no MEC-specific advantage or limitation is reported [125].

- **LFU (Least Frequently Used)—traditional observed-frequency policy.** Pre-2022 evidence evaluates LFU for mobile-video delivery at Wi‑Fi APs/BSs (2017) and as a mobile-edge comparator (2020) [135][134]. When full, it evicts the least-frequently requested item; generic ties use LRU, while admission and object granularity are unreported [135][187]. The 2017 two-week traces (1,055,881 APs; 69,210 BSs; default 20 items; 5–600-item sweep) favored LFU at lower location-request entropy and for multi-location users; LRU/LFU/RR converged at large capacity [135]. Stale counts, poor demand-shift adaptation and classic logarithmic update cost limit it [136]. First shown date: **2017-03-09** (edge, not explicitly MEC); recurring 2016–2021 baseline use supports traditional mainstream status, but direct MEC prevalence remains qualified [135][133][138].

- **Random replacement (RR)—traditional baseline.** In the **2017-03-09** mobile-video edge study, RR randomly selects and discards a candidate item when replacement is needed; video-object granularity, admission and predictive/popularity signals are unreported [135]. At large capacity its hit rate resembled LRU/LFU [135]. This conditional, single-study result does not establish global MEC-video mainstream status.

- **Adaptive Replacement Cache (ARC)—adaptive traditional candidate.** Video evidence begins **2014-09-01** in a five-policy local-access VoD comparison, not explicitly MEC; original public evidence is FAST 2003 [141][136]. Generic ARC uses recency/frequency LRU lists, adapts their split from workload and ghost history, and on a full miss evicts an LRU page from the selected list; video-object admission and victim detail are unreported [136][137][141]. It is self-tuning and scan-resistant; a 2004 implementation reported **0.75%** space overhead [137]. Limits include extra history—up to \(2c\) remembered pages—and possible slight loss to offline-optimal fixed tuning on stable workloads; LRU can be comparable when potential caching gain is high [136][141]. It is therefore pre-2022 video evidence, but not confirmed mainstream MEC-specific evidence.

- **Roster leads.** Additional pre-cutoff names are PPC (future popular chunks), CCP/MPV, LFRU, IPEC, PopCaching, hybrid/probabilistic, Bayesian dynamic-clustering, self-learning cooperative, proactive/RL precaching, Edgecache, and adaptive popularity/prediction caching [188][138]. Post-cutoff discovery-only labels include fuzzy logic, ICSAD, TS-MMCM (LSTM/Zipf/Thompson sampling), CCBG, FLBC, PBC, and DRL/FL/RNN/MLP/CNN/Q-learning/DQN/MARL approaches [127][128].

- **LRU/traditional:** Miss→front; full→least-recent tail; recency only, no prediction [189]. 2021 mobile-video baseline; ignores future popularity [175][178].
- **LFU/traditional:** Reference counts; MEC-MAP “use”=transmission to covered vehicles; full cache evicts least-transmitted chunks [91]. 2021 baseline [175]; stable-demand benefit versus stale/new-item bias and tracking overhead; 1993/1997 records are generic [79].
- **FIFO:** Traditional/reactive; oldest removed regardless of use [189]. No pre-2022 MEC-video evidence/date/signal; weak adaptation to dynamic edge requests [160][191].
- **Random replacement:** No history/prediction; random eviction for space [175]. 2021: equal-size movies, 10–50 Mb caches; worst traditional baseline; MEC-video status unconfirmed [175].
- **MRU/ARC:** MRU appears only inside FBR/ARC; standalone MEC-video rule/benefit/limit/date unestablished [142][143]. ARC: T1/T2; hits→T2; full lists LRU→B1/B2; adaptive, no QoS [143]. 2003 record generic; direct MEC-video status unconfirmed [190].

- LFU: traditional FIFO/LRU; MEC-video status unproven. CR-LFU vs LFU: +8.67% (churn)/+3.83% (mixed), cache<working set, 2021 storage-I/O [161][162].
- FIFO: traditional reactive; miss→admit, full→oldest out [162]. 2011 P2P VoD retained unpopular data [78]; 2021 CMEC updated MEC video FIFO while selecting popular content [50]. Mainstream unproven.
- MRU: newest-out, scan-friendly; no qualifying MEC-video date. ARC: adaptive traditional T1/T2 recency-frequency cache; 2003 record non-MEC; scan→churn causes continuous replacement [161].
- GCS (2021-03-29): greedy MBS/SBS place/update; hit/delay/backhaul gains; BS-capacity limit; eviction/mainstream unknown [198]. CVC (2021-12-14): hybrid federated-learning request prediction + collab decision/response; hit/delay/cost gains vs traditional; horizon/mainstream unknown [197]. CMEC: 7 nodes/30 users/~50 videos [50].

- **Least Recently Used (LRU)—traditional.** LRU admits requested video content reactively and, when full, replaces the least-recently used cached item; the source granularity may be a content item, video, chunk, or full video [202][199]. Its only core signal is observed recency/request history, not a reported prediction model [108]. LRU benefits workloads with high temporal locality and stable popularity, but can retain recently requested unpopular videos and performs poorly when a small edge population has volatile, non-stationary demand [200][108]. Study-specific results must not be pooled: one comparison reports a 75% LRU hit rate, another 76% under temporal correlation, while learned alternatives report 89% and 79%; MaCoCache reports 50% lower latency than LRU [196]. LRU is a canonical edge/video baseline, but the cited spans do not establish an exact first MEC-video date or literature-wide MEC-specific mainstream status [108][202].

- **Least Frequently Used (LFU)—traditional.** LFU keeps an observed reference count for each cached video/content object and evicts the least frequent object; ties are broken by LRU [199][200]. Ordinary LFU uses request frequency only. OP-LFU is a distinct predictive variant: it uses requests recorded hourly for **12 hours** and selects among linear, power-law, exponential, and Gaussian popularity models, so it belongs with predictive methods rather than ordinary LFU [192]. LFU suits stable, Zipf-like, heavily skewed demand, but suffers cache pollution when historically popular content becomes stale and its count remains high [200]. Reported, non-comparable baselines include 81% hit rate in one F-RAN study and 77% under temporal correlation [196]; a later post-cutoff comparison reports capacity-related plateaus and sharper decline as users increase [193]. Exact first MEC-video evidence is not established in the supplied spans, although pre-cutoff baseline treatment is documented [192][108].

- **First-In, First-Out (FIFO)—traditional candidate.** FIFO stores requested objects in arrival order and, when full, replaces the oldest; its signal is queue order, with no reported popularity or prediction model [192][196]. It appears as a conventional baseline, including a reported 75% hit rate in one F-RAN comparison, but no standalone advantage is established [196]. Direct scheme-specific MEC-video evidence, an exact first qualifying date, and literature-wide mainstream status remain unconfirmed.

- **Collaborative Video Cache Management Strategy in Mobile Edge Computing (GCS).** Two 2021 bibliographic records establish pre-cutoff existence—one WCNC paper and one *Ad Hoc Networks* work—but provide no mechanism, classification, evaluation, or evidence of canonical/mainstream status [139][140]. Accordingly, the cutoff record does not establish its placement, local replacement, coordination signal, advantages, or limitations. A later 2025 account describes a hybrid using predicted location (BiGRU next-step, \(t+1\)) and preferences for proactive placement, with simulated hit-rate and latency gains, but that evidence cannot upgrade GCS’s 2021 status [193].

- **MEC/video:** edge caches at base stations serve nearby users’ video segments, reducing backhaul and delay [60].
- **FIFO (traditional):** admission/placement unreported; a full cache evicts its first-stored file (queue order, not prediction). 2020-04-02; 60-day retention; at capacity 1000, hit ratio ≈0.5 and highest damage from most evictions [126].
- **ARC:** no qualifying pre-2022 MEC-video evidence; rule, benefits, limitations, mainstream status and first date remain unestablished [64][86].

- **MEC:** Base-station MEC servers cache/serve DASH/VoD chunks/bitrates near mobile users; local/neighbouring caches precede the CDN. [62][72]
- **LRU/LFU/FIFO:** LRU evicts least-recently requested; LFU the lowest-count and lags sudden surges; FIFO the oldest. FIFO's direct MEC-video status remains unestablished by 2021-12-31. [129][201][93]
- **ARC:** Balances LRU/LFU, but MEC-video use and mainstream status by 2021-12-31 remain unestablished; the cited acronym hit is unrelated. [201][45][203]

- **LRU:** traditional; recency→oldest-accessed chunk; simple under locality, weaker under long-tail/ingress (62% vs 73% at α=2; 2–3× disk); MEC date unknown; generic 1966. [70]
- **LFU:** traditional; request counts→least-frequent eviction; no predictor, ties/stale counts; first MEC comparison: 2021-12-05. [195][44]
- **FIFO:** traditional oldest-out queue; MEC queue; video/mainstream evidence unknown. [195][155]
- **ARC:** traditional; once/≥2 refs tune LRU/LFU; MEC-video/status unknown; generic 2004. [204][194]

- MEC edge caches serve video segments near mobile users, reducing backhaul/latency; 2021 ABR caching/transcoding [41] and mobility-aware prefetch/replacement [49] qualify. ARC has generic demand-paging evidence; its MEC status is unestablished [205].

Least Recently Used (LRU) is a traditional, non-predictive MEC video-cache policy: a requested or downloaded segment is inserted or moved to the head of an access-order list, and when capacity or free memory is insufficient, the least recently accessed tail segment is evicted [77][122][164][117][97]. Pre-cutoff evidence includes a 2019 video-cache application and a 2021-12-01 edge-video study [165][77][57]; LRU is simple and useful when recent data recurs [110], but MEC-media hit-ratio and latency performance can be poor and distributed state maintenance is costly [58][121].

Least Frequently Used (LFU) is a traditional, non-predictive frequency policy: it tracks observed reference counts, starts new keys at frequency 1, increments counts on access, and evicts the lowest-frequency object when capacity is reached, using recency to break ties [164][95][183]. In MEC/video work, including a comparison dated 01 February 2021, LFU is used for edge video-block pre-caching, MEC-server placement or replacement, and baseline evaluation [180][61][69][76]; it retains repeated demand but becomes stale when popularity changes and has weaknesses under dynamic viewing workloads [102][104][71].

First-In, First-Out (FIFO) caching has direct pre-cutoff evidence in edge-cache-assisted 360° live video: a study dated 01 February 2021 evaluates FIFO with LRU and LFU [76], while an edge HTTP cache uses FIFO rather than LRU [118]. FIFO is conventional rather than prediction-based and evicts the oldest first-added content without using recency or frequency [78][81], so its role is a comparison baseline.

Collaborative Video Cache Management Strategy in Mobile Edge Computing is evidenced in 2021 as a cooperative MEC video-delivery approach that coordinates cached content among MEC servers in heterogeneous macro- and small-base-station networks [176]. Its operation combines proactive collaborative edge caching with inter-server resource coordination [197][176], aiming to reduce delay and backhaul or cloud load and improve cache hit ratio [176], although the pre-cutoff account does not specify video-object granularity or a fixed placement and eviction rule .

Most Recently Used (MRU) caching evicts the item retrieved most recently; it can suit one-pass or long sequential scans by quickly removing poor-locality data that is unlikely to recur [186][89]. MRU is simple and predictable but does not always provide the best hit rate [150], and the available applications are generic or vehicular-edge rather than direct MEC-assisted video [147][150]; consequently, no qualifying mainstream MEC-video role is established by the cutoff.

Random replacement caching is a traditional, non-predictive baseline with 2014 mobile-video edge evidence and evaluation at Wi-Fi access points and cellular base stations [130][135]: when space is needed, it selects and discards a cached item randomly without a popularity, recency, or frequency signal [178][182]. Its low overhead is an advantage [186], but randomness and lack of popularity relevance slow hit-rate improvement and worsen average transmission, limiting it to a comparator rather than a popularity-aware MEC policy [182].

Adaptive Replacement Cache (ARC) is a rule-based adaptive traditional policy, not a predictor: it separates once-referenced objects in T1 from repeatedly referenced objects in T2, promotes hits toward the most-recent position, adjusts the partition with its target parameter, and uses B1/B2 history to determine which list supplies an eviction [143][161][159]. ARC has Internet video-on-demand replacement evidence before the cutoff [141] and adapts recency and frequency, but the direct application evidence is Internet VoD rather than MEC-assisted video, so ARC should be retained only as a qualified adaptive comparator [141].

Mobile Edge Computing (MEC) moves compute, storage, and caching from the central cloud to base-station and network-edge locations close to users; local MEC nodes cache popular videos or chunks and serve requests locally, while missing content is fetched from the core or cloud [54][47][55][65]. This placement reduces core or backhaul traffic and delivery latency and supports transcoding, context awareness, cooperative clusters, and proactive or adaptive streaming, making MEC the application setting for these caching policies [40][50][60][61].

MEC-assisted video streaming is a distributed application in which a remote video server or 5G core supplies segmented, multi-bitrate video to mobile or DASH clients through MEC nodes at small or macro base stations; cache-enabled clusters serve requested segments near users [66][45][43][47]. It is therefore the test context for cache placement and replacement, prefetching, transcoding, and cooperative or D2D delivery, with the aims of reducing delay and backhaul burden and improving streaming QoE [47][60][181].

Least Recently Used (LRU) qualifies for the requested mainstream traditional roster by the cutoff: direct video-cache evidence is dated 2019 and 01 February 2021 [165][76], and its segment mechanism evicts the least-recent tail when memory is constrained [77]. The evidence supports a baseline role and usefulness when recent data recurs [110], but distributed access and state maintenance remain material limitations [121], so universal effectiveness cannot be confirmed.

Least Frequently Used (LFU) qualifies as a traditional mainstream baseline by the cutoff: it appears in video-streaming cache management [163], is a classic frequency policy that evicts the least-frequency item [161][200], and has qualifying evidence dated 01 February 2021 [76]. Its lightweight historical counts can be inaccurate for diverse, highly dynamic viewing [96], so it should be treated as a workload-dependent baseline rather than a guarantee of universal effectiveness.

First-In, First-Out (FIFO) caching should be retained as a traditional baseline rather than excluded: pre-cutoff evidence evaluates it in edge-cache-assisted 360° live streaming on 01 February 2021 [76], and a CMEC cache-update study is dated 2021-09-07 [50]. Its first-added-first-evicted rule is conventional and non-predictive [78][81], which supports roster inclusion but not a claim that FIFO is broadly superior or the dominant policy.

Collaborative Video Cache Management Strategy in Mobile Edge Computing directly relates to MEC-assisted video streaming by coordinating cached video among MEC servers and macro- or small-base-station edge caches, with inter-node resource sharing supporting nearby delivery [176]. Its cooperative scope is intended to lower access and delivery delay, backhaul or cloud load, and improve cache hit ratio [176], but the pre-cutoff evidence does not specify video-object granularity or a complete fixed placement and eviction rule .

Collaborative Video Cache Management Strategy in Mobile Edge Computing has valid pre-cutoff evidence dated 29 March 2021 and 2021-12-14 [197], so it should be retained as a qualifying candidate, although broad mainstream status is not established by the available material [176][140]. Under the requested taxonomy it is cooperative or hybrid: inter-node caching is primary while user-location prediction and preference modelling drive proactive placement, placing it with cooperative or prediction-aware methods rather than fixed traditional LRU or LFU [179][193].

Most Recently Used (MRU) caching is a traditional candidate with a static rule: when the cache is full it discards the most recently used contents, which can help one-pass or scan workloads by quickly evicting poor-locality data [147][186][89]. It is simple and predictable [150] but workload-dependent, ignores dynamically changing popularity, and is not universally suitable [173][147]; because the available material is not a direct MEC-assisted video-streaming evaluation [161], retain MRU only as a qualified comparator.

Random replacement caching is a traditional candidate: when replacement is necessary it chooses among cached blocks with equal probability and uses no popularity or predictive demand signal [200][182]. It has conventional mobile-video edge-baseline evidence [135] and low implementation overhead [186], but its randomness and lack of relevance to popularity produce slower cache-hit improvement and poorer average transmission [182], so it should be retained as a comparator.

Adaptive Replacement Cache (ARC) is an adaptive traditional candidate: it maintains T1 for objects seen once and T2 for objects seen repeatedly, promotes hits, adjusts the recency-frequency partition, and uses B1/B2 history to select evictions [143][161][159]. ARC has Internet video-on-demand evidence dated 2014-09-01 [141] and is described as outperforming LRU through dynamic adaptation, but its more complex mechanism can retain older frequent files and lose performance under some workloads [185][165]; direct MEC-video evidence is not established [141].

Traditional Caching Schemes form a broader baseline family rather than an LRU/LFU-only category: LRU represents recency-based replacement and LFU frequency-based replacement [77][200], while FIFO, random replacement, and ARC have separate conventional or adaptive evidence [76][135][141]. Therefore, LRU and LFU should be profiled explicitly without treating them as the exhaustive traditional roster.

Least Recently Used (LRU) belongs on the requested mainstream roster: it is applied to streamed segments and edge caches and evicts the least-recent item [77], with evidence dated 2019 and 2021-12-01 [165][57]. The evidence supports a reactive baseline role, while distributed state maintenance remains a material limitation [121].

Least Frequently Used (LFU) belongs on the requested mainstream roster as an observed-frequency baseline: it appears in video-streaming cache management [163], evicts the least-frequency item [200], and has qualifying evidence dated 01 February 2021 [76]. Its historical counts can be inaccurate for diverse and dynamic viewing [96], so its relationship to the roster is that of a useful baseline rather than a universally reliable policy.

Traditional Caching Schemes function as canonical, non-predictive comparison baselines for Mobile Edge Computing (MEC)-assisted video streaming: Random replacement caching, Least Recently Used (LRU), First-In, First-Out (FIFO) caching, and Least Frequently Used (LFU) select content for retention or eviction from request-history statistics under the assumption that current popularity persists [108][192]; placing content at edge or intermediate nodes serves later requests nearer users and reduces bandwidth, server/backhaul load, and delay, while cooperative variants share cache state and coordinate nodes and non-cooperative variants decide independently [53], so these policies provide comparison context rather than a representation-aware solution—traditional schemes are agnostic to multiple video representations and the evidence does not independently establish MEC-specific mainstream status [42][108][107]. rejected: citation_outside_operands; reason: the proposed FIFO-by-the-cutoff qualification relies on supporting citations outside the permitted evidence, so its study dates, oldest-content rule, superiority, and broad mainstream status are not established here; allowed numbers: Oct. 2014 | 12 hours | July 2017 | 2003 | 2019 | 1,000 video files | "" | 01 February 2021 | 2019 year | 0.0 hit ratio | 1 Dec 2021 | 19 December 2014 | 6 September 2022 | 2023-04-06; 2024-10-10; 2021-12-31 | 2021 | 10 May 2021 | 2016 year | 2024-10-10; 2021-12-31 | Jan. 2013 month and year | MAR 14, 2026 | 2020 | Jun. 2018 | 2018 | 2-10 seconds | 1.2 | 2021-10-18 | 5.325% | 2009 | 2011 | (2021) | November 9, 2024 | up to 42% | Mar. 2003 | 2004 | 2004 year; 2003 year | 2014-09-01 | 1966 | Jul 15, 2024 | August 2019 | Oct 10, 2024 | 2021 year | 100 blocks | S bits; 1.2 | 2022 | 05 December 2021 | 0.56 | 2021-04-12 | 02 December 2014 | 2016-06-01 | 2020-04-02 | 2019-01-01 | 75% hit rate | 42% | 0.75 percent; allowed citations: [41], [42], [44], [45], [46], [48], [51], [53], [57], [59], [61], [63], [67], [68], [70], [73], [74], [75], [76], [77], [78], [79], [80], [84], [90], [92], [93], [94], [96], [98], [99], [100], [101], [103], [107], [108], [109], [110], [111], [114], [118], [119], [121], [122], [124], [125], [126], [131], [133], [135], [137], [139], [140], [141], [144], [145], [146], [147], [148], [149], [152], [154], [157], [161], [163], [164], [165], [166], [169], [170], [171], [176], [179], [181], [186], [188], [190], [192], [193], [196]; allowed entities: Traditional Caching Schemes; Least Recently Used (LRU); Mobile Edge Computing (MEC); Least Frequently Used (LFU); First-In, First-Out (FIFO) caching; Collaborative Video Cache Management Strategy in Mobile Edge Computing; Most Recently Used (MRU) caching; Random replacement caching; Adaptive Replacement Cache (ARC).

## Caching Schemes based on User Behavior or Content Popularity Prediction

**Additional information changes cache decisions.** These schemes estimate future requests or use behavioral evidence that simple access counters omit. Some forecast popularity explicitly; others learn replacement actions, exploit viewing retention, predict user movement, or optimize retention from a video’s lifecycle. Their shared advantage is a richer decision signal—not necessarily a particular neural-network architecture. [1]

**Prediction and control remain separate.** A model estimates demand; a caching policy translates that estimate into admission, placement, replication, or eviction. A stronger predictor can still produce poor streaming results if it preloads the wrong representation, stores content at the wrong node, or replaces useful content too aggressively.

### Request-history and popularity-evolution models

**The main alternatives model different structure.** Context-based learning associates request patterns with future popularity; LSTM models learn sequential dependencies; point processes model event timing and saturation; hit-density models connect expected reuse to occupied space.

| Scheme | Concrete model or signal | Cache selection | Replacement/update | Main reported strength |
|---|---|---|---|---|
| PopCaching | Request-context learning | Forecast-popular objects | Context-driven replacement | Learns recurring access patterns |
| OP-LFU | Selected popularity curve | Highest forecast popularity | Refit/select forecasting model | Explicit trend modeling |
| LSTM-C | Deep LSTM request sequence | High predicted retention priority | Evict lowest predicted priority | 20%–32% hit-rate improvement |
| DeepCache | LSTM encoder–decoder | Forecast-popular contents | Sequence-forecast-based caching | Learns popularity evolution |
| HRS | Hybrid point process | Top-\(S\) predicted request rates | Online rate and parameter updates | 12.3% average improvement |
| LHD | Conditional hit density | Expected hits per occupied space | Evict lowest contribution | Size-aware reuse prediction |

These mechanisms appear in the LSTM-C study, HRS study, and Goian et al.’s survey. [3][4][1]

- **PopCaching — Context-Based Popularity Learning**
  - **Core principle and selection:** Learn how recent request patterns relate to future content popularity, then retain objects with greater predicted future value.
  - **Placement, eviction, and updates:** The surveyed mechanism represents request history as a context vector and partitions its space into hypercubes carrying learned future-popularity values. Actual demand updates those values, and partitions can become finer. A miss triggers a cache decision using the requested object’s context and predicted popularity. [1]
  - **Advantages for MEC video:** It learns online without a separate initial batch-training phase and uses more information than a single cumulative count. With cache size 10 in Zhang et al.’s preliminary comparison, it was strongest on iQiyi Small Cell and MovieLens, whereas LFU led on aggregate iQiyi.
  - **Limitations and trade-offs:** Initial performance is weak while contexts lack experience. Features effective on one dataset may transfer poorly, and outdated request patterns can reduce performance. Across those three datasets, the strongest pre-LSTM-C baseline achieved 52.6%–75.5% of the future-informed OPT hit rate. [3]

- **OP-LFU — Optimal-Selection Predictive LFU**
  - **Core principle and selection:** Replace historical-frequency ranking with predicted future popularity. Candidate models describe different popularity trajectories rather than assuming one fixed evolution shape.
  - **Placement, eviction, and updates:** Use hourly accumulated request observations over 12 hours, fit linear, power-law, exponential, and Gaussian models, and select the model with lowest prediction error. Maintain cached content according to the resulting future-popularity estimate. [1]
  - **Advantages for MEC video:** The model family explicitly accommodates steady growth, sharp changes, slower changes, and S-shaped evolution. The decision is more interpretable than an undifferentiated black-box score.
  - **Limitations and trade-offs:** Evaluating several models for each content item and time period increases processing. HRS’s evaluation used only three of the four curve families because of computational complexity. Assessment: the approach is attractive when recognizable trends persist long enough to estimate, but weaker for sparse local histories or abrupt externally driven popularity changes. [4]

- **LSTM-C — Long- and Short-Term Sequence-Learning Replacement**
  - **Core principle and selection:** Feed request sequences to a deep Long Short-Term Memory network, which learns long- and short-term popularity structure and assigns caching priorities.
  - **Placement, eviction, and updates:** On an uncached request requiring replacement, rank resident objects by predicted caching priority and evict the lowest. Training uses an approximate priority target derived from historical sequences; an asynchronous trigger separates learning from inference and retrains after a specified number of misses. [3]
  - **Advantages for MEC video:** It avoids manual feature extraction and reports 20%–32% higher hit rate than baselines under limited-cache conditions. Measured average training and prediction times were 8.6 ms and 300 μs per iteration on the study’s CPU platform.
  - **Limitations and trade-offs:** It initially performed worse while learning; the authors recommend pretraining with at least 2,000 requests. Hyperparameters still matter, prediction costs exceed simple baselines, and expanding the content inventory can require model resizing. Calculated from the reported timings, one training iteration costs about \(8.6/0.3=28.7\) prediction iterations, motivating asynchronous training rather than continuous retraining. [3]

- **DeepCache — LSTM Encoder–Decoder Popularity Forecasting**
  - **Core principle and selection:** Use an LSTM encoder–decoder to map a historical popularity sequence to a forecast sequence and base content retention on anticipated popularity.
  - **Placement, eviction, and updates:** The model accepts an \(M\)-length input sequence with features representing content popularity and produces a \(K\)-length prediction sequence. These forecasts drive popularity-oriented caching rather than a fixed recency queue. [4]
  - **Advantages for MEC video:** Forecasting a sequence can represent an evolving popularity trend rather than merely predicting the next request. In HRS’s evaluation, DeepCache was the second-best method in most tested hit-rate settings.
  - **Limitations and trade-offs:** Neural forecasting requires sufficient observations and training resources. The HRS study particularly identifies extensive parameter tuning, sparse histories for cold videos, and weaker interpretability as difficulties for neural popularity models. Assessment: a model with good aggregate accuracy may still miss the particular few objects that matter most in a very small edge cache.

- **HRS — Hawkes, Reactive, and Self-Correcting Prediction**
  - **Core principle and selection:** Predict each video’s request rate with a hybrid point process. Hawkes self-excitation captures momentum from recent requests; a reactive component captures negative events; self-correction limits continued growth as a finite local audience becomes saturated.
  - **Placement, eviction, and updates:** Cache the top \(S\) predicted-rate videos from a catalog of \(C\), with \(S<C\). Update request-rate kernels frequently and model parameters less frequently; re-rank changed predictions and refresh the resident set. Parameters are learned by maximizing historical-event log-likelihood. [4]
  - **Advantages for MEC video:** The model is interpretable and uses fewer parameters than the neural comparators. On Tencent traces from five Guangdong cities—15,841,209 requests for 20,000 videos during November 2014—the paper reports 12.3% average hit-rate improvement and over 24% improvement under very limited capacity.
  - **Limitations and trade-offs:** Equal-sized videos or blocks simplify storage selection. In the evaluation, negative events were inferred after 12 hours without requests, making them a constructed behavioral signal. Kernel and parameter refresh rates still trade computation against responsiveness; the model is lightweight, not parameter-free. [4]

- **LHD — Least Hit Density**
  - **Core principle and selection:** Predict potential future hits per unit of consumed cache space using conditional probabilities.
  - **Placement, eviction, and updates:** Retention favors objects with higher expected hit density; eviction removes objects contributing least to expected cache-hit performance. This is predictive reuse scoring rather than simply counting past accesses. [4]
  - **Advantages for MEC video:** Its objective addresses storage efficiency directly, which is relevant when large video objects compete with smaller ones. In the HRS comparison, LHD and LRU had the lowest execution times.
  - **Limitations and trade-offs:** Assessment: hit density optimizes a different quantity from playback urgency or mobility-aware availability. A large segment with an immediate deadline may have high streaming value despite a lower expected hit count per byte; conversely, equal-sized-object experiments suppress part of the size trade-off that motivates density scoring.

**Freshness benefits are not monotonic.** HRS’s sensitivity results illustrate why “update more often” is not a complete recommendation.

| HRS kernel-update interval | Hit rate with 200 cached videos | Hit rate with 5,000 cached videos |
|---|---|---|
| 4 hours | 26.403% | 79.149% |
| 1 hour | 27.754% | 80.112% |
| 0.5 hour | 27.607% | 80.700% |

These are the study’s reported values for the same update-interval experiment. [4]

**The mechanism explains the choice.** Moving from four-hour to hourly updates captures newer demand and improves both displayed cases. Halving the interval again improves the larger cache but slightly reduces hit rate for the 200-video cache. The implication is to choose a useful refresh horizon, not the smallest possible interval; the conclusion changes with cache size, event noise, and computational budget.

### Regional, demographic, and cooperative popularity learning

**Local relevance competes with sample size.** A regional model can share observations and learn faster, but aggregation can dilute the tastes of a particular edge audience. These schemes differ in how they combine local evidence, group structure, and cooperative placement.

| Scheme | Prediction model or signal | Placement decision | Update mechanism | Main outcome |
|---|---|---|---|---|
| DCoL | Item-based filtering plus LSTM | Regional top-\(n\) at RSUs | Shared regional forecasts | 8.9% hit-efficiency gain |
| Demographic LSTM ensemble | Group LSTM plus online regression | Next edge-cache state | Online ensemble control | Up to 30% hit-rate gain |
| Tanzil et al. | Extreme learning machine | Predicted-popularity initialization | MILP initialization; S3-LRU updates | Fast-learning hybrid design |
| ANN cooperative placement | Artificial neural network | Latency-oriented cooperative set | Greedy placement optimization | Higher hits, lower latency |
| Spatiotemporal VB | Nonlinear Bayesian dynamics | Proactive cooperative caching | Sequential online inference | Tracks changing popularity |
| Deep-regression caching | Local and neighbor estimates | Next-slot proactive content | Per-slot prediction | Reduced delivery latency |
| CCA with EWMA | Smoothed shared requests | Replication/diversity balance | Periodic reoptimization | Explicit delay-cost trade-off |

The named mechanisms come from their respective studies and the 2019 video-popularity survey. [18][19][1][20][21][22][23]

- **DCoL — Distributed Collaborative Filtering and LSTM Prediction**
  - **Core principle and selection:** Combine item-based collaborative filtering at roadside units with LSTM prediction at a macro base station. RSUs share local popular-content information to construct a regional popularity database.
  - **Placement, eviction, and updates:** Use regional predicted popularity to update RSU caches proactively with the \(n\) most popular contents. The refreshed top-\(n\) selection determines which resident objects persist and which give way. [18]
  - **Advantages for MEC video:** MovieLens-based simulations report 8.9% improvement in cache-hit efficiency and 18% improvement in content-retrieval cost over a competitive centralized baseline. Combining filtering with temporal prediction addresses different aspects of demand.
  - **Limitations and trade-offs:** The paper explicitly notes that collaborative filtering can use stale data and miss short-term patterns. RSU storage is limited and the underlying caching problem is NP-hard. Assessment: regional cooperation helps when neighboring demand is informative; it can misdirect local placement when audiences differ substantially.

- **Demographic LSTM–Online-Ensemble Caching**
  - **Core principle and selection:** Nguyen et al. learn time-varying demand separately for demographic user groups using LSTM models with STL time-series preprocessing, then combine their outputs through a regression-based online ensemble.
  - **Placement, eviction, and updates:** Map current cache status, historical group demand, and group information to the next edge-cache state. The online ensemble adjusts how group predictions influence cache control. [19]
  - **Advantages for MEC video:** MovieLens experiments report up to 30% higher cache-hit ratio than conventional representative algorithms and performance within approximately 9% of an optimum supplied with perfect prior popularity.
  - **Limitations and trade-offs:** MEC storage, computing, energy, and communication bandwidth remain explicit resource constraints. Assessment: demographic grouping can improve signal quality when groups share persistent interests, but changing group composition or weak demographic–preference relationships can undermine the benefit. More detailed grouping also divides observations among more models.

- **Tanzil et al. — Extreme-Learning-Machine Popularity Caching**
  - **Core principle and selection:** Predict YouTube popularity with an extreme learning machine: a single-hidden-layer neural model with randomized hidden parameters and learned output weights.
  - **Placement, eviction, and updates:** Initialize cache placement during low network load using a mixed-integer linear program informed by predicted popularity and cellular-network characteristics. Subsequently update the cache using S3-LRU. The selected input features include subscriber count, previous-day views, thumbnail contrast, and overexposure. [1]
  - **Advantages for MEC video:** Learning only output weights reduces training work compared with training every neural connection. More importantly, the design demonstrates a practical division of responsibilities: prediction initializes placement, while a conventional policy handles online replacements.
  - **Limitations and trade-offs:** Assessment: the predictor depends on informative video metadata and on those feature relationships remaining relevant. S3-LRU can react to subsequent accesses, but it does not automatically correct every geographical or temporal error in the initial forecast.

- **Sun et al. — ANN-Based Cooperative Placement**
  - **Core principle and selection:** Learn popularity with an artificial neural network and use it as an input to cooperative placement minimizing average downloading latency.
  - **Placement, eviction, and updates:** Formulate content selection as a 0–1 integer program and approximate the placement with a greedy algorithm. The cache-control output is a proactive cooperative resident set rather than a recency-ordered queue. [20]
  - **Advantages for MEC video:** Numerical results report increased cache-hit rate and reduced content-delivery latency compared with popular caching strategies. The important mechanism is that prediction is coupled to a network objective, rather than followed by independent top-popularity filling at every node.
  - **Limitations and trade-offs:** Assessment: prediction error and greedy approximation affect different parts of the decision. This mobile-edge placement model is relevant to video objects, but download-latency improvement should not be treated as a direct measurement of playback freezing or bitrate stability.

- **Spatiotemporal Variational-Bayes Popularity Prediction**
  - **Core principle and selection:** Model temporal and spatial popularity correlations using a nonlinear probabilistic dynamical model with non-Gaussian distributions.
  - **Placement, eviction, and updates:** Estimate model parameters through Variational Bayes, including an online form for sequential request arrivals. Evolving popularity estimates guide proactive cooperative caching. [21]
  - **Advantages for MEC video:** The model explicitly represents correlations that independent per-cache frequency counters ignore. Real-data simulations report improved caching performance over conventional policies.
  - **Limitations and trade-offs:** The study emphasizes that proactive efficiency depends on accurate time-varying prediction. Assessment: spatial sharing is useful only when the learned relationship between cells persists; changes in local audiences or movement patterns can weaken it. Its main contribution is the prediction-and-tracking component, which must be matched to a storage- and delivery-aware video placement policy.

- **Masood, Nguyen, and Cho — Deep-Regression Next-Slot Caching**
  - **Core principle and selection:** Use deep regression to predict next-slot video popularity from local popularity estimates and information shared by neighboring edge devices.
  - **Placement, eviction, and updates:** Each time slot, a base station generates local estimates, exchanges them with neighbors, predicts the next slot, and proactively caches accordingly. The next-slot selection supplies the update target. [22]
  - **Advantages for MEC video:** The evaluation reports good performance and significant latency reduction. Neighbor information can provide evidence beyond the limited requests visible at one small edge.
  - **Limitations and trade-offs:** Assessment: per-slot exchange and inference must finish early enough for the predicted content to arrive before demand. A shorter slot improves responsiveness but leaves less time for communication and preload completion; a longer slot reduces update frequency but risks stale predictions.

- **CCA — Collaborative Caching with EWMA Popularity Updates**
  - **Core principle and selection:** Estimate popularity online through an exponentially weighted moving average, then balance local copies of popular videos against a broader cooperative catalog.
  - **Placement, eviction, and updates:** First fill SBS caches greedily in decreasing popularity order. Then replace duplicate copies with uncached videos when the popularity ratio satisfies \(\pi_{k_2}/\pi_{k_1}>d/[ND-(N-1)d]\), where \(d\) and \(D\) represent local-cooperative and remote retrieval delay costs. For unequal sizes, use popularity density \(\pi_k/s_k\) and rounding to complete videos. [23]
  - **Advantages for MEC video:** Popularity follows \(\pi_k^t=(1-\alpha)\pi_k^{t-1}+\alpha n_k^{t-1}/W\), using shared request windows, and placement is periodically reoptimized. Unit-size algorithm complexity is \(O(NK+K\log K)\), or \(O(N+K\log K)\) in the distributed implementation.
  - **Limitations and trade-offs:** Shared request lists and reoptimization add overhead; one common popularity vector limits spatial differentiation. In Netflix-based tests with six SBSs and 5–50 GB caches, the CCA/OPT delay ratio stayed within two for exact comparisons restricted to 20 videos. This is a tested comparison, not a universal factor-two claim for all video catalogs. [23]

**CCA makes replication economics explicit.** When cooperative retrieval is cheap relative to remote retrieval, replacing redundant copies can broaden the catalog served without origin access. When cooperative retrieval approaches remote cost, that diversity becomes less valuable and local copies deserve more protection. The implication is that cooperation should be evaluated using delivery costs, not merely the number of distinct cached videos.

**Group learning has a locality condition.** DCoL and demographic learning improve predictions by combining related observations; CCA shares popularity for coordinated placement. These approaches become less attractive when aggregation hides meaningful differences between adjacent cells, and more attractive when local histories are sparse but neighboring or group histories remain relevant.

### Viewing retention, request probability, and social behavior

**Video behavior adds within-title information.** A title can be popular while its later segments are rarely watched. User preferences, abandonment, social influence, and playback urgency therefore change which parts and representations deserve scarce edge space.

| Scheme | Behavioral signal or model | Selected content | Placement/update role | Main advantage |
|---|---|---|---|---|
| Hit-Ratio-Driven VoD | Popularity, preferences, representations | Storage-feasible video choices | Grouping-knapsack placement | Preference-aware hit optimization |
| PcP | Watching-pattern probabilities | High-probability chunks | Proactive admission | Avoid unnecessary preloads |
| CrP | Same chunk-probability model | Most useful resident chunks | Probability-aware replacement | Refresh low-value chunks |
| PCCP | Demand and cooperative resources | Distributed chunks and processing | Online scheduling | Coordinate storage and transcoding |
| RBCC | Retention and neighbor value | Likely-useful segments | Collaborative replacement | Reduce abandonment waste |
| CSQCA | Dynamic social graph plus ARMA | Social/QoE-aware video content | Cache ratio, lifetime, adaptation | Improve hits and viewing QoE |
| Markov dissemination | Predicted viewing probabilities | Socially likely requests | Probability-guided caching | Anticipate propagation |

The schemes draw on preference modeling, chunk-level probability, retention-aware streaming, and social prediction. [24][25][6][26]

- **Hit-Ratio-Driven MEC Caching for VoD**
  - **Core principle and selection:** Derive video-request probability from content popularity, user preference, and characteristics of video representations.
  - **Placement, eviction, and updates:** Select a storage-feasible combination through a grouping-knapsack formulation solved by dynamic programming. Its primary decision is which video/representation choices constitute the resident placement, rather than which item is oldest or least recently accessed. [24]
  - **Advantages for MEC video:** It connects user preferences and representation choices to the hit-ratio objective under storage constraints. Simulations report a substantial improvement in hit ratio.
  - **Limitations and trade-offs:** Assessment: optimizing expected hits depends on the request-probability model remaining representative. A choice that maximizes request hits need not minimize bytes transferred or prevent playback stalls, particularly when representations differ in size or delivery urgency.

- **PcP — Proactive Caching Policy**
  - **Core principle and selection:** Baccour et al. estimate chunk popularity from viewers’ watching patterns and proactively admit chunks with the highest request probability.
  - **Placement, eviction, and updates:** Neighboring MEC servers distribute different chunks of a video and collaborate in storing and transcoding them. PcP controls proactive selection; CrP and PCCP provide replacement and scheduling in the same design. [25]
  - **Advantages for MEC video:** Chunk-level probabilities avoid treating every part of a popular video as equally worthwhile. This can conserve storage and preload traffic when many viewers stop early.
  - **Limitations and trade-offs:** Assessment: the benefit depends on stable enough watching-pattern estimates and on successful coordination among the nodes holding different chunks. More precise chunk decisions also require more detailed state than whole-title popularity.

- **CrP — Cache Replacement Policy**
  - **Core principle and selection:** Use the same watching-pattern probability model to keep the chunks most likely to be requested.
  - **Placement, eviction, and updates:** Replace less useful resident chunks so the cache better matches the high-probability set; replacement operates within the cooperative chunk-storage and transcoding architecture. [25]
  - **Advantages for MEC video:** Unlike proactive admission alone, it addresses what happens after storage fills. Its decision criterion is expected chunk demand rather than mere recency.
  - **Limitations and trade-offs:** Assessment: a probability-only retention decision can become stale when viewing patterns change. Replacement also creates transfer work, so aggressively following every small probability change can offset savings from better content selection.

- **PCCP — Online Collaborative Caching and Processing**
  - **Core principle and selection:** Coordinate where chunks are stored and which MEC servers perform transcoding, alongside PcP admission and CrP replacement.
  - **Placement, eviction, and updates:** An online scheduler arranges collaborative caching and processing among neighboring servers storing different chunks, using the other two policies to maintain useful content. [25]
  - **Advantages for MEC video:** It uses distributed storage and compute together rather than placing every chunk of a video at one MEC. The combined model and policies report up to 50% performance improvement in some cases over conventional replacement approaches.
  - **Limitations and trade-offs:** The 50% figure is a combined-system performance claim, not a separate PcP, CrP, or PCCP hit-rate improvement. Assessment: distributed chunk ownership makes inter-MEC connectivity and processing availability part of the service path; cooperation helps only while those resources remain usable.

- **RBCC — Retention-Based Collaborative Caching**
  - **Core principle and selection:** Use clients’ retention toward different videos or video parts to distinguish content likely to be watched from content likely to be abandoned.
  - **Placement, eviction, and updates:** Incorporate retention and inter-edge collaboration into the replacement heuristic. Requested segment value includes the possibility of fetching from neighboring edges, so an object’s local value depends partly on cooperative availability. [6]
  - **Advantages for MEC video:** The study reports a significant cache-miss-rate reduction over LRU-based policies. Retention gives a concrete reason not to cache an entire requested video uniformly.
  - **Limitations and trade-offs:** Assessment: retention estimates may differ by user, content type, and session conditions. A population-level abandonment pattern can misrepresent a particular viewer who continues watching. Cooperation also shifts some delivery from backhaul to inter-edge links rather than eliminating all transfer work. [15]

- **CSQCA — Collaborative Social-Aware QoE-Driven Caching and Adaptation**
  - **Core principle and selection:** Represent social relationships with a dynamic bidirectional graph and predict their evolution using an Auto-Regressive Moving Average model.
  - **Placement, eviction, and updates:** A two-tier collaborative MEC architecture makes proactive cache-ratio and cache-lifetime decisions. Cached video is adapted or transcoded to requested resolutions using real-time channel and backhaul conditions; changes in predicted social relevance and cache lifetime guide residency updates. [26]
  - **Advantages for MEC video:** Real-dataset simulations report higher average cache-hit ratio and QoE than traditional algorithms. The design links anticipated social demand to actual delivery quality instead of optimizing popularity alone.
  - **Limitations and trade-offs:** The authors identify personality, mood, weather, and changing relationships as sources of social variability. Assessment: graph collection and updating introduce additional state and processing, and an accurate social forecast must still be translated into content suitable for the current channel.

- **Markov-Chain Social-Dissemination Prediction**
  - **Core principle and selection:** Predict the probability that users will view particular content as it disseminates through social relationships.
  - **Placement, eviction, and updates:** Use predicted viewing probability as a proactive caching priority, with the probability model determining which socially propagated content deserves retention. The CSQCA discussion identifies Markov-chain dissemination models as an alternative to interest-history filtering and dynamic-relationship prediction. [26]
  - **Advantages for MEC video:** Propagation can provide advance information before local request counts become large, making the signal relevant to proactive video admission.
  - **Limitations and trade-offs:** The cited variants assume dissemination probabilities as prior information and neglect time-varying relationships. This contrasts with CSQCA’s attempt to forecast changing social links. Assessment: such a model is most credible when its propagation probabilities remain representative over the caching horizon.

**Behavior can outperform title-level popularity.** Retention and chunk probability answer “how far will viewers watch?”, while social models answer “who may request next?” These are different sources of value. A retention-aware policy is particularly useful when later segments occupy substantial storage but see little demand; a social predictor becomes more useful when sharing creates observable lead time before requests arrive.

**QoE requires deadline awareness too.** The 2019 refined multi-MEC segment-update scheme makes this connection especially explicit:

- **Refined Multi-MEC Segment-Update Caching**
  - **Core principle and selection:** Combine segment popularity, segment importance, client transmission capability, and playback-buffer state. Partition the cache into \(\Delta_1\), containing the first 15% of popular videos’ segments; \(\Delta_2\), containing their remaining segments; and \(\Delta_3\), containing nonpopular-video segments.
  - **Placement, eviction, and updates:** Update \(\Delta_1\) on a longer period \(J\), and \(\Delta_2/\Delta_3\) on a shorter period \(\gamma\). Calculate deletion priority from request counts, segment rate, and transmission capability, smoothing it across periods. Delete high-priority candidates while excluding segments currently being transmitted; admit segments according to playback urgency and capacity-constrained utility.
  - **Advantages for MEC video:** It protects useful startup content while refreshing the rest more responsively. A local miss first seeks a neighboring MEC with high remaining transmission capacity; cache-partition sizes can exchange space. Simulations report improved throughput and segment hits with reduced backhaul and freezing. [8]
  - **Limitations and trade-offs:** It needs playback, request, channel, and inter-MEC capacity information and solves a constrained 0/1 optimization. When cooperation exceeds link capacity, the server falls back to cloud retrieval or waits. The first-15% partition is tied to the paper’s cited viewing-retention observation, rather than a universal property of all videos.

**A common configuration permits comparison.** With 378 clients and 2.4 GB total MEC cache, the study reports the following improvements for its proposed scheme:

| Compared baseline | Proposed throughput increase | Proposed backhaul reduction |
|---|---|---|
| LRU | 60.7% | 35.3% |
| LFU | 23.3% | 32.8% |
| WGDSF | 9.8% | 18.8% |
| RBCC | 5.9% | 14.2% |

These are comparisons within one multi-MEC simulation. With MEC caching disabled, the same study reports average playback frozen time of 4.2 seconds. [8]

**The gain has a video-specific mechanism.** The proposed scheme does not merely keep frequently requested segments: it selects representations that clients can receive and gives priority to clients with urgent playback needs. This explains why a richer policy can improve throughput and freezing even when a baseline already captures popularity reasonably well.

### Mobility-aware and 360° video caching

**Correct location is part of usefulness.** A video can be accurately predicted yet placed at a base station the user has already left. Mobility-aware schemes therefore decide where and how much to cache, while 360° schemes additionally face large content volumes and spatially selective viewing.

| Scheme | Concrete predictive signal | Placement decision | Update/control focus | Main result |
|---|---|---|---|---|
| LSTM 360° prefetching | Evolution of content requests | Cooperative SBS tile caching | Forecast-driven prefetch | Better quality, hits, backhaul use |
| ECMSP | Speed, dwell time, popularity | Appropriate portions along route | Pre-cache and capacity-aware update | Best of four tested schemes |
| MLCP | Predicted network traffic | Multi-location VANET prefetch | Traffic-driven admission | Proactive traffic awareness |
| CCMP | Predicted stay on path | Longest-stay base station | Mobility-based node choice | Path-aware placement |

The first comes from Maniotis and Thomos; the remaining three are compared in the ECMSP study. [27][11]

- **LSTM-Based Tile Prefetching for 360° Live Video**
  - **Core principle and selection:** Forecast evolving content requests with LSTM networks and use those forecasts to prefetch tile-based 360° video content.
  - **Placement, eviction, and updates:** Place anticipated content in edge caches; users within overlapping small-base-station coverage can obtain data from any available SBS. Forecast-driven prefetch changes the selected edge content as demand evolves. [27]
  - **Advantages for MEC video:** Compared with LFU, LRU, and FIFO, the evaluation reports better delivered video quality, cache-hit ratio, and backhaul-link use. Cooperative access increases the useful cache pool available to an overlapping user.
  - **Limitations and trade-offs:** 360° content creates substantial storage and bandwidth pressure. Assessment: request forecasting must remain timely enough for live-video deadlines; predicted demand that changes before a prefetched tile is consumed wastes precisely the resources prefetching is intended to save.

- **ECMSP — Edge Caching Based on User Speed and Content Popularity**
  - **Core principle and selection:** Given a known route, calculate dwell time from user speed, determine the video amount deliverable during each area visit, and prioritize competing videos by popularity.
  - **Placement, eviction, and updates:** Coordinate macro and small base stations in a cloud–edge–user hierarchy. Cache appropriate video portions along the route and extra content near handoff boundaries. Use pre-caching before capacity fills and cache updating afterward. [11]
  - **Advantages for MEC video:** In simulations tracking 300 mobile users, ECMSP had the lowest average delay and highest hit ratio among ECMSP, RPCC, MLCP, and CCMP. Increasing SBS capacity from 2 to 6 GB increased its hit ratio by a reported 21%.
  - **Limitations and trade-offs:** The known-path assumption is central. The simulation omits some real road effects, including obstruction and interference; obtaining movement information raises privacy and access concerns. The 21% is a capacity-change result within ECMSP, not its improvement over the three baselines. [11]

- **MLCP — Machine-Learning-Based Content Prefetching**
  - **Core principle and selection:** Detect or predict network traffic with machine learning and use multiple locations and factors to determine proactive content placement.
  - **Placement, eviction, and updates:** Pre-cache content in a vehicular ad hoc network according to the traffic model. Its defining control is traffic-driven multi-location prefetching, complementary to per-node replacement. [11]
  - **Advantages for MEC video:** It brings network-demand information into admission before requests arrive and is broader than a single-location frequency counter.
  - **Limitations and trade-offs:** ECMSP’s authors attribute its relatively poor pre-caching performance to ignoring traffic changes caused by user movement. This is an important counterexample: a learning-based traffic model is not automatically mobility-aware, even when deployed in a vehicular environment.

- **CCMP — Cooperative Caching Based on Mobility Prediction**
  - **Core principle and selection:** Predict where the user will stay longest along a path and select that base station as the cache node.
  - **Placement, eviction, and updates:** The primary admission decision is geographical: place the relevant content at the predicted longest-stay node. Mobility-based node selection supplements, rather than substitutes for, the node’s resident-content management. [11]
  - **Advantages for MEC video:** It recognizes that caching at an arbitrary nearby node can be ineffective for a moving user and directs storage toward an expected service opportunity.
  - **Limitations and trade-offs:** In the ECMSP comparison, its prediction model ignored differences in user speed, although speed changes actual dwell time. Assessment: path prediction alone is insufficient when the amount downloadable during a visit varies substantially across users or road conditions.

**Mobility changes the admission question.** For a stationary audience, it may be sufficient to ask whether a title will be requested. For a moving viewer, the useful question is whether the needed portion can be delivered at a particular node before departure. ECMSP’s advantage over MLCP and CCMP is therefore explained by a more complete service-opportunity model, not by a general superiority of one machine-learning architecture.

### Collaborative learning, reinforcement learning, and lifecycle-aware control

**These schemes learn or coordinate actions.** Some distribute request prediction across edges; others directly learn replacement decisions or introduce objectives beyond hit rate. They should be compared by what the controller optimizes and what information it exchanges.

| Scheme | Model or decision signal | Cache action | Update mechanism | Main outcome |
|---|---|---|---|---|
| PCR | Proactive demand prediction | Collaborative placement/replacement | Combined predictive framework | Beats named conventional baselines |
| CVC | Federated request prediction | CCD placement and CSR delivery | Collaborative prediction-driven control | Lower waiting and system costs |
| DQN-OVC | Cost-aware deep Q-learning | Video-cache changes | Continuous online decisions | Adapts to dynamic popularity |
| LECS | TCN popularity plus caching value | Cooperative value-maximizing placement | Dynamic-programming selection | 8.3%–10.1% hit-rate gain |
| Popularity distillation | DRL plus neighbor distributions | Learned content replication | Local learning and peer exchange | 3.0% hit-rate improvement |
| LiA-cache | K-Medoids lifecycle clusters | Cluster-dependent retention/eviction | Joint cost-aware control | Up to 90% less cache damage |
| Bl-CMEC/DQN-VCT | Demand, popularity, network, capability | Joint caching and transcoding | DRL with smart-contract execution | Improved simulated QoE |
| Cache-log ML deletion | Learned request/cache-log patterns | Delete predicted video | Real-time learned replacement | Testbed implementation |

These designs span predictive collaboration, federated learning, learned actions, and lifecycle optimization. [28][29][30][31][32][33][34][35]

- **PCR — Predictive–Collaborative–Replacement Caching**
  - **Core principle and selection:** Combine proactive demand prediction, collaboration among MEC servers, and a replacement algorithm to manage limited storage.
  - **Placement, eviction, and updates:** Prediction identifies content for proactive caching; MEC collaboration extends the framework beyond isolated caches; the replacement component manages resident content as storage is reused. Its defining contribution is the integration of these three control functions. [28]
  - **Advantages for MEC video:** Experiments using MovieLens20M report better replacement performance than LFU, LRU, MQ, FBR, and LFRU. The study also compares PCR with a contemporary LSTM-based caching method.
  - **Limitations and trade-offs:** Limited MEC storage is the motivating constraint. Assessment: coordinated prediction and replacement can exploit neighboring content, but their value depends on forecast freshness and the cost of obtaining a remotely held copy. The framework should therefore be compared with an equally cooperative conventional baseline, not only with isolated LRU or LFU.

- **CVC — Federated Collaborative Video Caching**
  - **Core principle and selection:** Predict video requests using federated learning, then coordinate proactive caching and delivery.
  - **Placement, eviction, and updates:** Collaborative Caching Decision, or CCD, controls cooperative cache selection; Collaborative Service Response, or CSR, coordinates responses to user requests. Cache changes follow the prediction-driven collaborative decision layer, while delivery coordination is handled separately. [29]
  - **Advantages for MEC video:** Video-service experiments report higher hit rate, shorter user waiting delay, and lower overall communication and caching cost than traditional algorithms. The prediction model is expressly designed to reduce communication cost.
  - **Limitations and trade-offs:** Assessment: federated learning changes the information-exchange mechanism but does not remove the need for model updates, participating nodes, or local computation. Its practical advantage depends on whether coordinated learning is cheaper and more relevant than collecting request information centrally or using simpler local policies.

- **DQN-OVC — Cost-Aware Deep-Q Online Video Caching**
  - **Core principle and selection:** Learn video-cache decisions from user and network information while accounting for replacement costs.
  - **Placement, eviction, and updates:** Decompose the Q-value as a product of a video-value function and an action function. A low-complexity cost-aware action function selects cache changes continuously as popularity evolves. The learned action controls video caching rather than following a fixed least-recent or least-frequent queue. [30]
  - **Advantages for MEC video:** Tencent-trace evaluation reports significant improvement over state-of-the-art baselines. The major conceptual benefit is treating replacement timing as consequential, rather than assuming that moving to a better popularity ranking is free.
  - **Limitations and trade-offs:** Replacing a stale video incurs downloading cost and can interrupt ongoing users of the displaced content. Large learning action spaces challenge limited edge compute; prediction accuracy can also be unstable. The authors’ Tencent trace had nearly 100 cache-intercepted requests per millisecond during peak hours, illustrating why update disruption matters. [5]

- **LECS — Learning-Based Cooperative Caching**
  - **Core principle and selection:** Predict popularity with a Temporal Convolutional Network and translate it into a Content Caching Value, or CCV, for each content/server pairing.
  - **Placement, eviction, and updates:** Use dynamic programming to maximize overall CCV across cooperating edge servers. The selected cooperative placement determines which content is retained as predictions and values change. [31]
  - **Advantages for MEC video:** Simulations report 8.3%–10.1% higher cache-hit rate and 9.1%–15.1% lower average content-delivery delay than state-of-the-art schemes. Server-dependent value provides a mechanism for avoiding identical independent decisions at every edge.
  - **Limitations and trade-offs:** The underlying cooperative caching problem is NP-hard. Assessment: a useful prediction must still justify the optimization and coordination effort; the advantage changes when cooperation is expensive or server-specific values fail to represent current delivery conditions.

- **DRL Content Replication with Popularity Distillation**
  - **Core principle and selection:** Let an edge learn from local requests through deep reinforcement learning and from other edges through exchanged “soft” popularity distributions.
  - **Placement, eviction, and updates:** Learn content-replication strategies using both information sources. A neighbor-maintenance mechanism iteratively chooses a small collaborating set, limiting the scope of peer exchange. [32]
  - **Advantages for MEC video:** Experiments driven by a real-world mobile-video dataset report a 3.0% hit-rate improvement over a non-distillation baseline, with transmission-data overhead described as small.
  - **Limitations and trade-offs:** The motivating problem is slow DRL learning under sparse requests at an individual edge. Assessment: borrowing knowledge helps when selected peers experience relevant demand; unrelated peer popularity can reduce local relevance. Neighbor selection therefore affects learning quality as well as signaling volume.

- **LiA-cache — Lifecycle-Aware Retention and Eviction**
  - **Core principle and selection:** Cluster videos by popularity lifecycle using K-Medoids, distinguishing long-lived, approximately one-month patterns from short-lived, approximately one-week patterns.
  - **Placement, eviction, and updates:** Jointly optimize cluster-dependent retention times and eviction policies for delivery cost and flash-cache damage. The lifecycle labels describe content behavior; they are not fixed instructions to retain every video for exactly a week or month. [33]
  - **Advantages for MEC video:** The paper reports up to 90% less cache damage while maintaining hit ratio close to popularity-only caching. A separate reported comparison describes a 30-fold damage-cost decrease and corresponding lifetime extension.
  - **Limitations and trade-offs:** Short retention increases misses, traffic, and latency; long retention increases flash damage. The lifecycle analysis used a mainland-China trace from November–December 2014 and filtered low-view and irregularly shaped videos. Assessment: lifecycle control is especially useful when flash wear affects operating cost, but its objective differs from maximizing delivery hits alone.

- **Bl-CMEC with DQN-VCT — Joint Caching and Transcoding**
  - **Core principle and selection:** Use a DQN-based Video Caching and Transcoding algorithm with user-demand predictions, video popularity, time-varying network conditions, and MEC-node capabilities.
  - **Placement, eviction, and updates:** Make joint intracluster caching and transcoding decisions, proactively storing high-popularity video at MEC nodes while leaving low-popularity content at CDN tips. Blockchain smart contracts execute and record service transactions and payments. [34]
  - **Advantages for MEC video:** Simulations report improved streaming QoE alongside security, integrity, privacy, and consistency benefits. The policy recognizes that a suitable storage decision can depend on available transcoding capability.
  - **Limitations and trade-offs:** The experiments treat deep-reinforcement-learning processing latency as negligible. Assessment: neither learning nor blockchain execution should consequently be treated as operationally free; the design becomes less attractive if their processing and communication costs consume the latency saved by edge delivery.

- **Akbar et al. — Cache-Log Machine-Learning Deletion**
  - **Core principle and selection:** Generate video-request patterns from a public dataset and train a machine-learning model on cache logs to identify a video for deletion.
  - **Placement, eviction, and updates:** Delete the predicted video from the edge to create space for incoming content. The concrete behavioral input is the request/cache-log history, and the learned output directly controls replacement. [35]
  - **Advantages for MEC video:** A real-time KOREN testbed demonstrates implementation of learned deletion rather than only an offline placement simulation. Evaluation uses MAE, MSE, and \(R^2\).
  - **Limitations and trade-offs:** Assessment: regression fit and caching utility are different evaluation axes. A model can predict its target accurately without selecting the eviction that best reduces future misses, backhaul bytes, or stalls. Its practical benefit therefore turns on the relationship between the learned target and the actual video-service objective.

**Learning actions addresses update costs.** DQN-OVC makes the strongest distinction from popularity-only selection: keeping an apparently stale video can be rational while it serves ongoing sessions. CVC and popularity distillation instead address how edges share learning information, while LiA-cache changes the objective by including storage wear. These are complementary developments, not interchangeable algorithms.

### Choosing between conventional and predictive caching

**Choose for the bottleneck.** The following decisions summarize the evidence without converting independent experiments into a universal leaderboard.

| Operating condition | Conventional starting point | Predictive or behavioral alternative | What decides the choice |
|---|---|---|---|
| Stable recurring title demand | LFU or static top-\(S\) | Popularity forecasting | Extra prediction value over stable counts |
| Fast popularity drift | LRU, LFUDA, SW-LFU | LSTM-C or HRS | Adaptation speed versus learning cost |
| Unequal files and heterogeneous caches | BB-ZOMKP | Prediction plus size-aware placement | Packing quality and popularity accuracy |
| Frequent early abandonment | Segment-level conventional caching | RBCC or PcP/CrP | Reliable continuation probabilities |
| Moving users with known routes | Local LRU/LFU baseline | ECMSP | Usable path, speed, and dwell information |
| Sparse requests at each edge | Simple local replacement | DCoL, CVC, popularity distillation | Relevance and cost of shared knowledge |
| Storage scarce, compute available | Highest-bitrate caching/transcoding | Learned joint caching/transcoding | Conversion capacity and deadlines |
| Replacement disruption or flash wear | Conservative refresh | DQN-OVC or LiA-cache | Service continuity and lifecycle cost |

**Hit rate is not the objective.** Request-hit ratio counts served requests, whereas backhaul savings depend on the sizes and retrieval paths of missed objects. Under an explicitly simplified equal-sized-request model, origin demand falls with \(1-h\), where \(h\) is hit ratio; real proactive systems must also account for preload and refresh transfers. A policy can therefore improve hit rate while gaining less in traffic because it replaces content frequently or caches many small, low-byte requests.

**Latency depends on the service path.** A local ready-to-send hit, a neighboring-cache hit, and a hit requiring transcoding have different response times. BB-ZOMKP’s cluster-hit objective, CCA’s delay-sensitive replica decisions, and JCCP’s processing-aware scheduling illustrate these alternatives. Their implication is that “found at the edge” should be followed by “where, in which representation, and at what delivery cost?” [12][23][13]

**QoE depends on usable delivery.** Startup delay, freezing, selected bitrate, and representation changes are not interchangeable. The refined multi-MEC scheme improves decisions by considering buffer urgency and transmission capability; cache-aware bitrate coordination may deliberately reduce bitrate to avoid an origin transfer. The appropriate judgment changes with the service objective: saving backhaul is less valuable if a resulting conversion delay or quality reduction damages the viewing experience. [8][15]

**Prediction must earn its overhead.** LSTM-C demonstrates that online inference can be fast enough for its tested setting, while HRS demonstrates the attraction of a lower-parameter interpretable model. Neither establishes that training, inference, request exchange, or reoptimization is negligible on every MEC platform. Predictions also age: Goian et al. explicitly warn that omitted features, unexpected events, and outdated parameters can make predictive caching less reliable than traditional caching. [3][4][1]

**Cooperation must preserve local relevance.** Sharing data or learned distributions is most useful when it increases effective sample size without erasing the preferences of the serving area. Mobility adds a further condition: the target audience must still be reachable when the content arrives. DCoL’s stale-filtering concern and ECMSP’s speed-aware placement show why a globally accurate forecast can still produce an ineffective local cache. [18][11]

**Evidence and historical boundary.** Reported percentages retain their original metrics and baselines; they are not automatically percentage-point changes. MovieLens ratings serve as request proxies, while video, segment, tile, representation, and cluster hits measure different objects; marked arithmetic is calculated from reported inputs. Framework-level descriptions remain at their documented control level. The 2019 multi-MEC paper reverses recency/frequency descriptions in its baseline text, so its figures retain the authors’ labels. Early-online 2021 publications are included. DCCCP, Zheng et al.’s federated-RL work, PPFUC-FL, and mobility-aware LSTM–DQN segment caching are outside the substantive catalog because their supplied public records give IEEE additions in February 2022 or January 2022; a demonstrable pre-cutoff public version would change that treatment. [36][37][38][39]

**The final decision is conditional.** Through 2021, conventional caching remained the defensible choice when demand was sufficiently stable, local observations were sparse, or processing and coordination budgets were tight. Prediction and behavioral modeling were most persuasive when they supplied fresh information that the baseline genuinely lacked—and when placement, representations, and update costs were controlled. The strongest practical rule is therefore to use the simplest policy that matches the workload, adding prediction or cooperation only when its demonstrated benefit survives the full MEC video-delivery cost.

## References

[1] <https://eprints.bbk.ac.uk/id/eprint/26766/6/26766.pdf> Video-caching survey; Survey comparison; Recognized recency limitation; LFU mechanics; Traditional-policy taxonomy; Variant descriptions; JW-LFU description; S…
[2] <https://dl.ifip.org/db/conf/wiopt/wiopt2018/1570431787.pdf> Conventional-policy analysis; LRU mechanics; Stationary-model result; Sliding-window analysis
[3] <https://ira.lib.polyu.edu.hk/bitstream/10397/81787/1/Zhang_Edge-Assisted_Video_Content.pdf> LSTM-C study; Policy definitions; LFU pollution discussion; Fixed-rule comparison; Cross-dataset and cache-size results; LFUDA description; LFUDA mechanism; Ba…
[4] <https://arxiv.org/pdf/2102.00646v1.pdf> HRS study; HRS and predictive baselines; Predictive-baseline implementation; DeepCache description in HRS; HRS formulation; Dataset, event construction, and ev…
[5] <https://mmlab-sigs.github.io/groups/zwang/publications/tmm-QLearning.pdf> Cost-aware edge-video caching study; Replacement-cost analysis
[6] <https://irep.ntu.ac.uk/id/eprint/37695/1/14859_Mehrabi.pdf> Collaborative edge-assisted DASH study; QoE–traffic findings; RBCC; RBCC mechanism
[7] <https://doi.org/10.1109/access.2019.2947067> FIFO definition
[8] <https://ar5iv.labs.arxiv.org/html/1911.10723v1> WGDSF comparison; WGDSF definition; Partitioning and update algorithm; Multi-MEC performance results; Playback-aware replacement
[9] <https://www.academia.edu/45376089/Applying_machine_learning_techniques_for_caching_in_next_generation_edge_networks_A_comprehensive_survey> Static popularity context
[10] <http://arxiv.org/pdf/1706.09536> Liang–Hu model; Placement and simulation results; Joint optimization constraints
[11] <https://doi.org/10.3390/electronics10182217> RPCC comparison; RPCC mechanism; Four-scheme results; Mobility comparison; Speed-aware placement; Evaluation and deployment conditions; MLCP description; CCMP…
[12] <https://doi.org/10.1109/access.2021.3095356> BB-ZOMKP study; Placement formulation; Performance and processing results; Popularity-skew trade-off; Cluster caching
[13] <https://opendl.ifip-tc6.org/db/conf/wons/wons2017/1570316181.pdf> Joint caching and processing study; JCCP; JCCP mechanism; Results and constraints; Processing-aware delivery
[14] <https://doi.org/10.1109/ants.2018.8710106> Highest-bitrate caching; Representation rule
[15] <https://arxiv.org/pdf/1805.09255v1.pdf> Cache-aware coordination; Cache-aware scheduling; Retention-aware streaming design; QoE–traffic coordination
[16] <https://doi.org/10.1007/s11042-020-08808-7> DPACA; DPACA design
[17] <https://doi.org/10.1109/access.2019.2927903> DACPSs/DACRS; Placement phase; Refresh mechanism
[18] <https://doi.org/10.1109/access.2021.3080512> DCoL; DCoL architecture; DCoL freshness discussion
[19] <https://uclab.re.kr/publications_openaccesspdf/vi_iotj_2021_open.pdf> Demographic ensemble; Hierarchical learning mechanism
[20] <https://doi.org/10.17559/tv-20190303092125> ANN placement; ANN placement method
[21] <https://doi.org/10.1109/tcomm.2020.3015478> Variational Bayes; Bayesian dynamics model
[22] <https://doi.org/10.1109/icoin50884.2021.9333920> Deep regression; Per-slot caching mechanism
[23] <https://arxiv.org/html/2109.00369> CCA; CCA placement rule; Complexity and evaluation; Delay-sensitive cooperation
[24] <https://doi.org/10.48550/arxiv.1909.03766> Hit-Ratio-Driven VoD; Request-probability placement
[25] <https://doi.org/10.1109/wcnc.2019.8885906> PcP/CrP/PCCP; PcP mechanism; CrP mechanism; PCCP scheduling
[26] <https://wmnlab.ee.ntu.edu.tw/lab/publication/Journal/[J]2021_Collaborative%20Social-Aware%20and%20QoE-Driven%20Video%20Caching%20and%20Adaptation%20in%20Edge%20Network.pdf> CSQCA and Markov comparisons; CSQCA mechanism; Markov-model comparison
[27] <https://doi.org/10.1109/tcsvt.2021.3055985> 360° live-video caching; Tile-based caching mechanism
[28] <https://doi.org/10.1109/access.2021.3058769> PCR; PCR framework
[29] <https://doi.org/10.1109/tnsm.2021.3135306> CVC; CVC architecture
[30] <https://doi.org/10.1109/tmm.2021.3125803> DQN-OVC; DQN-OVC mechanism
[31] <https://doi.org/10.1109/tpds.2021.3135257> LECS; LECS components
[32] <https://doi.org/10.1109/icme51207.2021.9428134> Distillation; Distillation mechanism
[33] <https://helda.helsinki.fi/server/api/core/bitstreams/c91fe38b-f498-4569-8b57-f9728fbce1bf/content> LiA-cache; LiA-cache mechanism
[34] <https://doi.org/10.1155/2021/7443260> Bl-CMEC; Joint control mechanism
[35] <https://doi.org/10.23919/apnoms52696.2021.9562623> Cache-log updater; Cache-log replacement mechanism
[36] <https://doi.org/10.1109/edge53862.2021.00024> DCCCP date
[37] <https://doi.org/10.1109/globecom46510.2021.9685242> Zheng et al. date
[38] <https://doi.org/10.1109/ic-nidc54101.2021.9660437> PPFUC-FL date
[39] <https://doi.org/10.1109/ic-nidc54101.2021.9660434> LSTM–DQN date
[40] <https://www.couchbase.com/resources/concepts/mobile-edge-computing/>
[41] <https://ieeexplore.ieee.org/document/9354743>
[42] <https://www.sciencedirect.com/science/article/abs/pii/S1084804520302113>
[43] <https://ieeexplore.ieee.org/ielx7/6287639/9312710/09476036.pdf>
[44] <https://dl.acm.org/doi/10.1016/j.knosys.2021.107523>
[45] <https://doi.org/10.1155/2020/6684293>
[46] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8347317/>
[47] <https://doi.org/10.1109/access.2021.3095356>
[48] <https://doi.org/10.1109/access.2019.2955749>
[49] <https://doi.org/10.1109/padsw.2018.8644948>
[50] <https://doi.org/10.1155/2021/7443260>
[51] <https://www.mdpi.com/2076-3417/12/9/4205>
[52] <https://opendl.ifip-tc6.org/db/conf/wons/wons2017/1570316181.pdf>
[53] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11860416/>
[54] <https://arxiv.org/pdf/1612.01436>
[55] <https://ieeexplore.ieee.org/iel8/6287639/6514899/11121143.pdf>
[56] <https://research-management.mq.edu.au/ws/portalfiles/portal/348517725/339697092.pdf>
[57] <https://doi.org/10.1109/uemcon53757.2021.9666668>
[58] <https://doi.org/10.3390/app12094205>
[59] <https://doi.org/10.11575/prism/2599>
[60] <https://digital-library.theiet.org/doi/pdf/10.1049/iet-com.2019.1198?download=true>
[61] <http://arxiv.org/pdf/1706.09536>
[62] <https://doi.org/10.1109/wcnc.2019.8885906>
[63] <https://www.robertoriggio.net/papers/cnsm2020.pdf>
[64] <https://resourcecenter.ieee.org/workshops/icme-2020/icme20vid013>
[65] <https://arxiv.org/html/1812.06501v1>
[66] <https://www.robertoriggio.net/papers/tnsm2022.pdf>
[67] <https://colouryen.github.io/pub/PiCom2018.pdf>
[68] <https://conferences2.sigcomm.org/acm-icn/2016/proceedings/p237-ge.pdf>
[69] <https://repository.essex.ac.uk/29700/1/FINAL%20VERSION.pdf>
[70] <https://dl.acm.org/doi/pdf/10.1109/TNET.2016.2621067>
[71] <https://doi.org/10.5121/ijcsit.2018.10208>
[72] <https://ieeexplore.ieee.org/document/8467314>
[73] <https://openresearch.surrey.ac.uk/view/pdfCoverPage?download=true&filePid=13140617350002346&instCode=44SUR_INST>
[74] <https://doi.org/10.1109/access.2018.2870855>
[75] <https://dl.ifip.org/db/conf/lanoms/lanoms2019/196373_1.pdf>
[76] <https://doi.org/10.1109/tcsvt.2021.3055985>
[77] <https://patents.google.com/patent/US20240340467A1/en>
[78] <https://doi.org/10.1109/aina.2011.103>
[79] <https://en.wikipedia.org/wiki/Least_frequently_used>
[80] <https://athena.itec.aau.at/wp-content/uploads/sites/12/2021/06/nossdav2021.pdf>
[81] <https://www.gmp-compliance.org/gmp-news/fifo-fefo-lifo-what-is-the-meaning>
[82] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9169600/>
[83] <http://mirage.cs.uoregon.edu/pub/pvc-2012.pdf>
[84] <https://doi.org/10.1109/cmc.2009.159>
[85] <https://doi.org/10.1109/access.2019.2936866>
[86] <https://doi.org/10.1109/access.2020.3047373>
[87] <https://doi.org/10.48550/arxiv.1911.10723>
[88] <https://rodrigo-bruno.github.io/mentoring/90763_pedro_luis_dissertacao.pdf>
[89] <https://dl.acm.org/doi/abs/10.1007/978-3-030-85928-2_36>
[90] <https://backoffice.biblio.ugent.be/download/3254441/3254472>
[91] <https://iris.polito.it/retrieve/handle/11583/2644916/e384c42e-57ea-d4b2-e053-9f05fe0a1d67/main.pdf>
[92] <https://dlnext.acm.org/doi/10.1145/2674005.2675003>
[93] <https://doi.org/10.1109/tbc.2021.3071010>
[94] <https://www.ieice.org/publications/proceedings/bin/pdf_link.php?fname=p250-akbar.pdf&iconf=APNOMS&year=2021&vol=67&number=PS2-13&lang=E>
[95] <https://stackoverflow.com/questions/21117636/how-to-implement-a-least-frequently-used-lfu-cache>
[96] <https://arxiv.org/pdf/2102.00646v1.pdf>
[97] <https://doi.org/10.17559/tv-20190303092125>
[98] <https://arxiv.org/html/1911.10723>
[99] <https://doi.org/10.1145/3507917>
[100] <https://dlnext.acm.org/doi/10.1109/INFOCOM42981.2021.9488910>
[101] <https://doi.org/10.3390/electronics11182824>
[102] <http://pdl.cmu.edu/PDL-FTP/associated/PID4735521.pdf>
[103] <https://doi.org/10.1109/access.2019.2950800>
[104] <https://www.vanderschaar-lab.com/papers/pop_infocom2016.pdf>
[105] <https://web.stanford.edu/~balaji/papers/04modelingcorrelations.pdf>
[106] <http://arxiv.org/pdf/1803.04675>
[107] <https://ieeexplore.ieee.org/iel8/6287639/6514899/10973056.pdf>
[108] <https://arxiv.org/html/2101.05885v1>
[109] <https://doi.org/10.1109/tnsm.2020.3037147>
[110] <https://miladezzat.medium.com/understanding-the-least-recently-used-lru-caching-algorithm-42346e021bfe>
[111] <https://www.infoq.com/news/2026/03/grab-tlru-image-cache/>
[112] <https://www.cs.cmu.edu/~rvinayak/papers/s3-fifo-sosp-2023-fifo-queues-are-all-you-need-for-cache-eviction.pdf>
[113] <https://doi.org/10.1109/tnsm.2021.3136439>
[114] <https://ris.utwente.nl/ws/files/264111322/EdgeDASH_Exploiting_Network_Assisted_Adaptive_Video_Streaming_for_Edge_Caching.pdf>
[115] <https://arxiv.org/html/2109.00369>
[116] <https://doi.org/10.2139/ssrn.4583764>
[117] <https://people.kth.se/~gyuri/Pub/Li_WDAK_Youtube_Caching2014.pdf>
[118] <https://dl.ifip.org/db/conf/im/im2019/188685.pdf>
[119] <https://doi.org/10.23919/wiopt52861.2021.9589569>
[120] <https://bytebytego.com/guides/top-8-cache-eviction-strategies/>
[121] <https://github.com/TurnerSoftware/CacheTower/issues/57>
[122] <https://dl.acm.org/doi/fullHtml/10.1145/3345022>
[123] <https://arxiv.org/pdf/1504.01957>
[124] <http://www.pdl.cmu.edu/PDL-FTP/TIP/SOSP15.ps>
[125] <https://ar5iv.labs.arxiv.org/html/2002.08805v2>
[126] <https://doi.org/10.1109/tmc.2020.2984364>
[127] <https://jtit.pl/jtit/article/download/1616/1358/5485>
[128] <https://doi.org/10.1155/2022/7212984>
[129] <https://doi.org/10.48550/arxiv.2101.05885>
[130] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7959663/>
[131] <https://doi.org/10.1109/access.2019.2947067>
[132] <https://ar5iv.labs.arxiv.org/html/1702.07627>
[133] <https://doi.org/10.1109/iscc.2016.7543869>
[134] <https://doi.org/10.1109/gtsd50082.2020.9303170>
[135] <http://personal.cityu.edu.hk/mchen88/papers/edge.caching.mobile.video.JSAC.17.pdf>
[136] <https://www.cs.cmu.edu/~natassa/courses/15-721/papers/arcfast.pdf>
[137] <https://theory.stanford.edu/~megiddo/pdf/IEEE_COMPUTER_0404.pdf>
[138] <https://pdfs.semanticscholar.org/5aee/de0bc3ee3f5e91814031c5f93231f36804db.pdf>
[139] <https://researchr.org/publication/wcnc-2021>
[140] <https://www.csauthors.net/zihao-sang/>
[141] <https://doi.org/10.1109/softcom.2014.7039112>
[142] <https://arxiv.org/pdf/1001.4135>
[143] <https://doi.org/10.1109/mascots59514.2023.10387601>
[144] <https://digitalcollection.zhaw.ch/entities/publication/29f75e8d-8d31-4d18-bee3-7edd4f5a3acb/full>
[145] <https://doi.org/10.1145/3106157>
[146] <https://www.semanticscholar.org/paper/LRU-MRU-with-Physical-Address-Cache-Replacement-on-Xue-Lei/6a6608c6a788f3ce205778a09f494c43d48feedc>
[147] <https://search.proquest.com/openview/eb878e11be4aae43e33fdea4038d2472/1?pq-origsite=gscholar&cbl=51922&diss=y>
[148] <https://arxiv.org/pdf/2112.00633>
[149] <https://doi.org/10.1109/tccn.2020.2968326>
[150] <https://www.linkedin.com/posts/ritik-soni-x007_mru-and-lru-understanding-cache-replacement-activity-7028582862035566592-ktuv>
[151] <https://doi.org/10.3390/s19030694>
[152] <http://medianetlab.ee.ucla.edu/papers/pop_infocom2016.pdf>
[153] <https://www.cs.utexas.edu/~inderjit/public_papers/caching_lcns2006.pdf>
[154] <https://mesdat.ucsd.edu/sites/default/files/2017-06/06708492.pdf>
[155] <https://ar5iv.labs.arxiv.org/html/1905.06650>
[156] <https://doi.org/10.1109/access.2020.2966495>
[157] <https://doi.org/10.1109/inm.2011.5990669>
[158] <https://doi.org/10.1109/lcn.2014.6925761>
[159] <https://en.wikipedia.org/wiki/Adaptive_Replacement_Cache>
[160] <https://www.sciopen.com/local/article_pdf/10.26599/TST.2023.9010051.pdf>
[161] <https://www.usenix.org/system/files/fast21-rodriguez.pdf>
[162] <https://uclab.re.kr/publications_openaccesspdf/vi_iotj_2021_open.pdf>
[163] <https://doi.org/10.1007/s00530-006-0042-0>
[164] <https://medium.com/@alxkm/introduction-to-lru-and-lfu-caching-concepts-implementations-and-practical-use-cases-ab90f2e168bd>
[165] <https://www.cse.cuhk.edu.hk/~cslui/PUBLICATION/Incremental_Least-Recently-Used_Algorithm_Good_Robust_and_Predictable_Performance.pdf>
[166] <https://www.enjoyalgorithms.com/blog/least-frequently-used-cache/>
[167] <https://doi.org/10.1109/wcncw48565.2020.9124865>
[168] <https://dl.acm.org/doi/10.1007/s10586-022-03624-0>
[169] <https://doi.org/10.1155/2011/237561>
[170] <https://sah.borca.ai/papers/212646302>
[171] <https://doi.org/10.1145/3359989.3365423>
[172] <https://repositum.tuwien.at/bitstream/20.500.12708/220197/1/Prilop%20Meiko%20-%202025%20-%20Caching%20Middleware%20for%20FaaS%20in%20Edge-Cloud%20Continuum%20based...pdf>
[173] <https://par.nsf.gov/servlets/purl/10532009>
[174] <https://www.mdpi.com/1424-8220/21/8/2867>
[175] <https://doi.org/10.1109/access.2021.3080512>
[176] <https://itiis.org/digital-library/manuscript/file/25992/TIIS%20Vol%2016,%20No%209-12.pdf>
[177] <https://www.sciopen.com/article/10.26599/TST.2023.9010051>
[178] <https://arxiv.org/html/1702.07627v1>
[179] <https://www.mdpi.com/2079-9292/12/9/1974>
[180] <https://doi.org/10.1109/tvt.2020.3029742>
[181] <https://ar5iv.labs.arxiv.org/html/2005.07384>
[182] <https://doi.org/10.1109/access.2020.2964711>
[183] <https://www.geeksforgeeks.org/dsa/least-frequently-used-lfu-cache-implementation/>
[184] <https://arxiv.org/pdf/2606.26119>
[185] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11893820/>
[186] <https://aerospike.com/blog/cache-replacement-policies/>
[187] <https://www.arunbaby.com/dsa/0060-lfu-cache/>
[188] <https://www.researchgate.net/publication/318693906_PPC_Popularity_Prediction_Caching_in_ICN>
[189] <https://helabenkhalfallah.com/2024/11/01/the-secret-life-of-caches-a-deep-dive-into-lru-and-lfu/>
[190] <https://www.mdpi.com/2076-3417/16/2/666>
[191] <https://arxiv.org/html/2402.02795>
[192] <https://eprints.bbk.ac.uk/id/eprint/26766/6/26766.pdf>
[193] <https://www.ceai.srait.ro/index.php/ceai/article/view/9367/1765>
[194] <https://wmnlab.ee.ntu.edu.tw/lab/publication/Journal/[J]2021_Collaborative%20Social-Aware%20and%20QoE-Driven%20Video%20Caching%20and%20Adaptation%20in%20Edge%20Network.pdf>
[195] <https://doi.org/10.1109/access.2021.3058769>
[196] <https://arxiv.org/html/2105.05564v3>
[197] <https://doi.org/10.1109/tnsm.2021.3135306>
[198] <https://doi.org/10.1109/wcnc49053.2021.9417255>
[199] <https://doi.org/10.15623/ijret.2016.0507082>
[200] <https://arxiv.org/pdf/1003.4062>
[201] <https://redis.io/glossary/lru-cache/>
[202] <https://www.mhchen.com/papers/edge.caching.mobile.video.JSAC.17.pdf>
[203] <https://unsdg.un.org/sites/default/files/ARC_An-Overview.pdf>
[204] <https://ar5iv.labs.arxiv.org/html/2002.08805>
[205] <https://www.usenix.org/conference/fast-03/arc-self-tuning-low-overhead-replacement-cache>
