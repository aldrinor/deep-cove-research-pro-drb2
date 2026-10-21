# Artificial Intelligence in PET Imaging: Technical Optimization and Clinical Applications Through Early 2024

**AI adds value throughout PET.** Artificial intelligence, especially deep learning, improves positron emission tomography (PET) at several distinct levels: locating detector interactions, refining timing and scatter handling, reconstructing and restoring images, compensating for motion, and converting images into clinical measurements and predictions. Representative results include interaction-depth resolution of **1.84 versus 3.04 mm**, clinically evaluated denoising at **25% of standard counts**, and personalized dose-map generation in **3.6 minutes versus 235.2 hours** for direct Monte Carlo simulation. These are application-specific achievements, not interchangeable measures of clinical benefit. [1][2][3]

**The strongest conclusion is task-specific.** AI can substantially improve PET image quality, automate tumor delineation and burden measurement, and accelerate physics-intensive calculations. Its strongest clinical role is generally assistance within a defined tracer, acquisition protocol, and clinical task: visually convincing restoration does not necessarily preserve lesions, and accurate contours do not by themselves demonstrate better treatment outcomes.

**Scope and roadmap are explicit.** This report covers global literature without geographic restriction, including detector-level PET, PET/CT, PET combined with magnetic resonance imaging (PET/MRI), dynamic PET, and whole-body imaging. The evidence boundary is early 2024, including the 28 March dosimetry report and the 1 April 2024 *Journal of Nuclear Medicine* issue. Part One follows four technical stages, distinguishing changes to measured events from changes to reconstructed images; Part Two examines six clinical applications, separating geometric agreement, diagnostic performance, quantitative reproducibility, and treatment-related predictions.

**The overview uses different endpoints.** A convolutional neural network (CNN) learns spatial or signal-pattern filters; a U-Net is an encoder–decoder CNN with connections that preserve information across resolutions. Full width at half maximum (FWHM) describes resolution; Dice similarity coefficient measures contour overlap from 0 to 1; and area under the receiver-operating-characteristic curve (AUC) measures binary discrimination across decision thresholds.

| Application | Objective or problem | Main AI techniques | Representative reported effect |
|---|---|---|---|
| Part One: acquisition enhancement | Improve event location, timing, and scatter handling | CNN, multilayer perceptron, U-Net, boosted trees | Prism-PET depth resolution: 1.84 versus 3.04 mm FWHM. [1] |
| Part One: reconstruction | Recover activity images from measured data | Direct encoder–decoder; physics-informed unrolling | Brain-simulation normalized error: 14.4% versus 20.7% for conventional reconstruction. [4] |
| Part One: post-processing | Restore noisy, already reconstructed images | Supervised U-Net/GAN; self-supervised denoising | At 25% counts, patient-level sensitivity 0.94 and specificity 0.98 against standard scans. [2] |
| Part One: motion correction | Reduce respiratory blur and dynamic-frame misalignment | Registration CNN, optical flow, recurrent networks | Respiratory simulation error: 24.3% versus 41.9% ungated. [5] |
| Part Two: segmentation | Delineate tumors and other regions | 3D U-Net, nnU-Net, clustering, graph cuts | Glioma PET Dice: 0.8231 after refinement. [6] |
| Part Two: lesion detection and classification | Find abnormalities and estimate malignancy | 3D CNN, HRNet, transfer learning, feature classifiers | Pathology-confirmed nodules: AUC 0.781; sensitivity 89.9%; specificity 54.5%. [7] |
| Part Two: quantitative analysis | Calculate metabolic tumor burden consistently | Organ-aware CNN pipelines; cascaded U-Nets | Automated lymphoma volume: intraclass agreement 0.98 with readers. [8] |
| Part Two: radiotherapy planning | Produce reproducible PET-based target contours | PET/CT nnU-Net and related segmentation networks | Head-and-neck external Dice 0.81 versus 0.80 internally. [9] |
| Part Two: dosimetry | Calculate individualized internal dose distributions | 3D U-Net, learned dose kernels, physics-guided GAN | Dose-rate map: 3.6 minutes versus 235.2 hours for Monte Carlo. [3] |
| Part Two: radiomics and radiogenomics | Predict molecular status, response, and prognosis | CNN features, feature selection, multimodal prediction | External mutation-prediction AUC 0.81 versus 0.50 for maximum uptake alone. [10] |

## Part One — Technical Optimization Across the PET Imaging Workflow

### 1. Image acquisition enhancement

**The objective is better measurement.** Acquisition-level AI aims to improve the information assigned to individual detected events: where a photon interacted, when it arrived, and whether its recorded trajectory is consistent with an unscattered coincidence. These interventions target localization error, parallax, timing uncertainty, count loss, and scatter contamination before those errors propagate into an image. Image-domain enhancement can address related appearances, but it operates at a different information level. [11][12]

**Raw events precede reconstructed images.** PET detectors record scintillation-light signals through devices such as silicon photomultipliers (SiPMs). Event processing estimates detector interaction positions, energies, and times; coincident detections define a line of response. Individual coincidences can be retained as list-mode records or grouped into sinograms—arrays of projection counts—which subsequently enter reconstruction.

**Event positioning corrects geometric ambiguity.** Classical light-centroid methods can misidentify interactions near detector edges and corners. They also provide limited information about depth of interaction (DOI): the distance into the scintillator at which a photon interacts. Uncertainty in this depth causes parallax error, particularly for oblique photons, so an apparently small detector-position error can degrade spatial resolution away from the scanner center. CNNs and multilayer perceptrons (MLPs) learn nonlinear mappings from detector readouts to crystal identity or three-dimensional interaction position. [13][14]

| Named approach | Input and learned output | Evaluation setting | Reported result |
|---|---|---|---|
| LaBella et al., 2020 CNN | Detector signals to crystal identity and position | Simulated single-ended detector | Edge/corner identification 99.0% versus 49.2%; spatial error 0.38 versus 0.76 mm |
| Sanaat and Zaidi, 2020 MLP | Fired SiPM pixels and energy to 3D position | Simulated monolithic-crystal scanner | Resolution 0.96 mm transversely and 1.02 mm axially; approximately 18% improvement |
| Prism-PET CNN | Per-event SiPM readout to DOI | Depth-encoding detector module | DOI resolution 1.84 versus 3.04 mm FWHM |

**The gains address different errors.** The first study mainly improved edge and corner localization relative to classical centroiding. The monolithic-detector MLP supplied depth information while retaining the simulated scanner’s absolute sensitivity. Prism-PET improved depth resolution relative to classical estimation; its 1.84 versus 3.04 mm result corresponds to a calculated 39.5% reduction in FWHM, using `(3.04 − 1.84) / 3.04`. These results should therefore be interpreted as improvements in different components of event localization, rather than a ranking of complete scanners. [13][14][1]

**Compact readouts can retain performance.** Prism-PET also tested a CNN receiving only the four highest signals per event. Average DOI resolution was 1.92 mm FWHM, approximately 4% worse than using all nonzero signals, including testing on a crystal excluded from training. The practical advantage is reduced per-event storage and processing, rather than simply adding a larger network to the detector chain. [1]

**Inter-crystal scatter can be recovered.** Smaller scintillation crystals improve intrinsic sampling but increase the frequency with which a photon deposits energy in multiple neighboring crystals. This inter-crystal scattering obscures the first interaction position. A 2023 study used a one-dimensional U-Net trained on GATE Monte Carlo events to predict that first position, combining local signal details with broader event-pattern information. [15]

**Recovery improves count utilization.** The U-Net achieved 78.1% first-interaction prediction accuracy. Relative to accepting coincidences comprising only two photoelectric photon interactions, recovered events increased sensitivity by 149%; reconstructed contrast-to-noise ratio for a 16 mm hot sphere rose from 6.973 to 10.795. Against an energy-centroid positioning method, the best reported spatial-resolution improvement was 33.46%. The mechanism is retention and better positioning of useful detector events, rather than removal of photons scattered inside the patient. [15]

**Measured timing improves actual TOF.** Time-of-Flight (TOF) PET uses the arrival-time difference between coincident photons to narrow the possible annihilation position along the line of response. Better coincidence timing reduces the spatial extent over which an event contributes uncertainty, thereby reducing noise propagation during reconstruction. Its image-quality benefit depends on timing resolution and the size of the imaged object. [16]

**Physics-guided learning refines calibration.** A 2023 residual-physics approach first applied analytical timing calibration, then used supervised gradient-tree boosting to learn higher-order timing corrections left behind by the analytical model. Known source positions supplied expected time differences, and Shapley-based feature attribution helped relate learned corrections to physical effects. For 19 mm-high detectors and a 450–550 keV energy window, coincidence timing resolution improved by more than 20%, reaching 185 picoseconds. This is a measured timing result; lower patient activity is a possible downstream use, not a quantified clinical outcome of that detector experiment. [17]

**Synthesized TOF is a different intervention.** Sanaat et al.’s Deep-TOF-PET used a cycle-consistent generative adversarial network, or CycleGAN, to translate non-TOF brain PET into TOF-like images or TOF-bin sinograms. A generative adversarial network (GAN) combines a generator, which produces an output, with a discriminator, which learns to distinguish generated outputs from reference data. Here, 140 clinical fluorine-18 fluorodeoxyglucose (^18F-FDG) brain scans were divided into 120 training and 20 test scans; projection-space implementation generated seven TOF bins with separately trained networks. [16]

| Output compared with non-TOF | Approximate SNR change | Approximate noise change | Approximate contrast change |
|---|---:|---:|---:|
| Measured reference TOF | +10% | −22% | +15% |
| Image-space predicted TOF | +7% | −16% | +13% |
| Sinogram-space predicted TOF | +3% | −7% | +4% |

**Image translation improved uptake agreement.** These are the study’s reported approximate changes in signal-to-noise ratio (SNR), background noise, and contrast. Average regional mean standardized uptake value—SUVmean—bias across 83 brain regions fell from 9.3% ± 2.21% for non-TOF images to 6.9% ± 0.08% for sinogram-space prediction and 6.2% ± 0.91% for image-space prediction. SUV is tracer uptake normalized using administered activity and patient-related normalization, commonly body weight. [16]

**Prediction does not recreate timestamps.** The important distinction is that an image-space network can learn the appearance and quantitative tendencies of TOF reconstruction without acquiring a new photon arrival-time measurement. The Deep-TOF-PET authors explicitly noted that their image metrics were not specific proof of recovered physical TOF information. Image-space translation performed better in that experiment, whereas synthesized sinograms retained the option of choosing a subsequent reconstruction algorithm and correction model. [16]

**Patient scatter creates wrong trajectories.** A photon scattered before reaching the detector can produce a coincidence whose inferred line does not pass through its true origin. The resulting background contamination changes contrast and quantitative uptake. A 2023 TOF brain-PET study addressed this directly in list mode: an MLP used event positions, energies, times, and related information to classify prompt coincidences as true or scattered. [18]

**Event classification reduced scatter contamination.** In the uniform-phantom GATE simulation, the scatter fraction among prompt events decreased from 30.0% to 10.6%, a calculated reduction of 19.4 percentage points. The corrected image profile resembled the true-event reconstruction. Importantly, this fraction describes the composition of retained prompt data; it is not, by itself, a classifier sensitivity or a guarantee that true-event losses are negligible. [18]

**Joint correction offers another route.** Deep convolutional networks have also been proposed to map noncorrected PET directly to jointly attenuation-and-scatter-corrected images, avoiding an explicit attenuation-map-generation stage followed by conventional scatter simulation. This is useful for dedicated brain PET configurations without integrated transmission information, but its operating domain is corrected-image estimation rather than raw detector localization. [19]

**Acquisition judgment favors upstream specificity.** Detector localization, measured timing calibration, and event classification improve identifiable measurement components; synthesized TOF and joint image correction should be judged by their resulting quantitative and clinical performance, not described as equivalent hardware upgrades.

**Additional documented evidence**

PET list-mode events retain detector IDs, TOF differences and timestamps; a typical 80-s FDG bed has >94% empty TOF bins [72]. This establishes the sparse timing/noise bottleneck; AI effects are not reported here.

Low counts and short/low-dose scans degrade PET SNR and may impair diagnosis [90]. In this source group, PET-AI evidence for event positioning, TOF/noise suppression and scatter correction is not reported.

Evidence has no acquisition-specific effect estimate; scanner, tracer, count/noise and reconstruction/correction conditions affect downstream measurements, requiring matched-protocol validation [88].

No shown dependency supports acquisition claims: event positioning, TOF/noise, and scatter effects are unreported here; the evidence concerns downstream tasks.

Low-count PET suffers count noise, randoms, scatter and electronics; AI uses event position/energy to classify scatter, estimates activity-based profiles, or approximates MC multi-scatter for faster correction [157,186].

Raw PET inputs are list-mode events, detector-normalisation/attenuation data and TOF viewgrams; corrections precede reconstruction [220,222]. The shown TOF benefit is conventional, not AI [78]; acquisition-AI effects: unreported.

At low counts, a CNN model reduced noise in 18F-FDG PET acquired at 66% of standard dose in a 2021 prospective Italian study (61 patients) [80]; paired standard-dose scans served as reference. No TOF/scatter result was reported.

Detector AI recovered 75% of triple-coincidence LORs; sensitivity rose 55% (360–660 keV). DNN/CNN positioning reached 0.68–0.75/up to 90%; Recovery-Net: 83% ID, 3.0-mm DOI error [83]. Mostly simulated; validate on real PET.

Pre-reconstruction U-Net predicted scatter from emission sinograms, AF and log-ACFs: brain NMAE 4.17% versus SSS; prostate error reached 14.11%. It took <30 s versus 3.5 min for five beds [73].

The cited TOF/list-mode result concerns LMPDNet reconstruction, not acquisition; AI event positioning, TOF/noise suppression and scatter-correction effects are not established [91].

In 2022, pix2pixHD converted ~30-s, >33-fold-shorter whole-body FDG PET/CT acquisitions into synthetic full-time images [84]. This is image enhancement after acquisition, not evidence of event-positioning, TOF or scatter correction [94].

AI/ML spans PET acquisition/correction; low resolution, noise, randoms and scatter are bottlenecks.[87] A 10-ps TOF challenge is noted.[87] Event-positioning/TOF effects are not reported.

ML estimates event position and arrival time from digitized waveforms [86]. A U-Net scatter predictor reached 4.17% brain NMAE and up to 14.11% prostate NMAE versus SSS, in <30 s versus 3.5 min for five-bed whole-body PET; TOF improves SNR and uptake precision [324,338].

At the acquisition/reconstruction boundary, CNNs generated μ-maps from NAC PET or refined MLAA maps for scatter estimation; μ-CNNMLAA was more accurate than μ-CNNAC [92]. Slide: non-TOF model <0.2 SUV (3%) bias versus <1 SUV (15%) for DL models [93].

Scatter is 20–50% of coincidences; ML correction is listed [79]. Deep learning estimates attenuation maps or corrected PET, with TOF availability affecting performance [77]; event-positioning results are unreported.

Acquisition evidence shown: DNN 3-D interaction-position estimation in a Monte Carlo Cherenkov detector study; CNN four-layer DOI encoding in small-animal PET. TOF/noise, scatter, effects and validation are not reported here [63]

This slice supplies post-reconstruction PET restoration evidence; raw-acquisition evidence on event positioning, TOF/noise and scatter is not reported here. [74][85]

Timing/event localization and TOF direction are AI targets: a 3-D CNN used view-grouped histo-images from Monte-Carlo brain-phantom PET at 300 ps; versus no direction, PSNR improved by 1.2 dB and SSIM by 0.02; computation was faster than iterative reconstruction (2022) [336,411].

These PET studies concern post-reconstruction low-count denoising/restoration, not detector event positioning, TOF/timing-noise estimation, or scatter correction; they therefore provide no acquisition-stage effect [68][96].

List-mode (preferably TOF) data can estimate motion; correction then acts on events, sinograms, the system matrix or images before, during or after reconstruction [293,331]. The motion evidence does not quantify event-positioning, TOF-noise or scatter gains.

PET list-mode gating may precede reconstruction, but the supplied methods address motion correction—not event positioning, TOF/noise handling, or scatter correction; acquisition effects are not reported [199,437].

No shown dependency establishes AI event positioning, TOF/noise suppression, or scatter correction; the 2026 dosimetry source treats scatter correction as a reproducibility parameter and is post-cutoff [98].

PET/CT evidence identifies low signal-to-noise and scanner/dose-dependent intensity variation; acquisition effects are not reported here [75].

These cards concern downstream PET/CT segmentation: AI-generated lesion masks support MTV/TMTV and planning [99]. They provide no evidence on acquisition-stage event positioning, TOF/noise, scatter correction, or quantitative gain.

Evidence is downstream PET/CT segmentation and MTV/TMTV quantification, not acquisition [298,451,117,118]. Event positioning, TOF/noise and scatter results are not reported here.

The shown evidence provides no direct AI result for PET event positioning, TOF/noise suppression, or scatter correction; these acquisition fields remain not reported here.

Studies provide protocol context, not a quantified AI-acquisition gain: low SNR, low resolution and partial-volume effects complicate small lesions; tracer, scanner and TOF protocols are study-specific [145,205].

No acquisition result is supported here; the supplied evidence is downstream (segmentation, TMTV, radiotherapy, radiomics). Event positioning, TOF/noise and scatter effects: not reported [212,213,393,457].

Available evidence is downstream: PET segmentation/ANNs produce ROIs and MTV; thresholds and manual review affect validity [248,462,463]. No raw-signal result is supported here.

These dependencies report downstream PET/CT segmentation, TMTV and GTV/radiotherapy, plus non-PET examples—not detector events, TOF/noise or scatter. They therefore provide no supported acquisition-stage effect estimate [60,133,255,323].

Acquisition claims need task-specific endpoints, external testing, protocol, reference standards and uncertainty; fidelity scores alone can mislead when scanner/site shifts alter inputs [448,456].

Dependency evidence links ML to PET acquisition and notes protocol/SUV variation changes PET features; AI event-positioning, TOF/noise and scatter results are not reported [82].

This source group supplies no qualifying pre-reconstruction evidence: its cards concern downstream lesion analysis, MTV/TMTV, or dosimetry. Event positioning, TOF/noise suppression, scatter correction, and acquisition effects remain unreported here.

Shown evidence links acquisition/reconstruction settings to FDG-PET texture variability [100]; it supplies no event-positioning, TOF/noise or scatter-correction result.

Acquisition affects PET reproducibility, bias and delineation through scanner, tracer/protocol, motion, resolution and SNR; protocols, validation and QA remain necessary. No AI-specific gain is reported in this evidence [137,481].

The shown evidence concerns radiotherapy contouring and radionuclide dosimetry, not detector-event positioning, TOF/noise handling, or scatter correction. No acquisition-stage effect is supported here.

AI can generate PET scatter sinograms from emission/attenuation or uncorrected PET data; throughput/speed benefits are unquantified [95]. Low-count Y-90 PET denoising targets noise; effects are unreported [76].

No supplied card here supports PET detector acquisition: the material addresses dosimetry or radiogenomics, not event positioning, TOF/noise suppression, or scatter correction [101][81][89][102].

The supplied review fragment places AI at the detector level for PET reconstruction and scatter/attenuation correction [103]. It reports no event-positioning or TOF/noise metrics; acquisition effects are not reported.

This slice adds no acquisition evidence; its records concern PET radiomics/radiogenomics, not event positioning, TOF/noise, or scatter correction. [34,36,39,468,512–514]

Downstream PET evidence shows that acquisition/reconstruction settings alter radiomic features and reproducibility [104]. No evidence here establishes AI event positioning, TOF/noise suppression, scatter correction, or acquisition benefit.

Downstream PET radiomics links acquisition, noise and reconstruction settings to feature robustness [105]; this source group reports no AI event-positioning, TOF or scatter-correction result.

PET-radiomics evidence qualifies acquisition claims: in a 2021 FDG-PET/CT study, 13% of 1,404 features were robust to motion, attenuation correction and delineation; noise and reconstruction settings also matter [421,528].

Acquisition noise affects PET features; results vary [97]

### 2. Image reconstruction

**The objective is quantitative image recovery.** AI reconstruction transforms measured projection data into an activity image while controlling noise and preserving clinically meaningful uptake. The central technical choice is between learning the reconstruction mapping directly and embedding learned components inside an explicit PET reconstruction model. Reader et al.’s review distinguishes these as direct data-driven and model-based, or physics-informed, approaches. [11]

**Conventional reconstruction supplies the reference problem.** PET reconstruction must explain observed coincidence counts through a system model that represents detection geometry and relevant corrections. Maximum-likelihood expectation-maximization (MLEM) and its ordered-subsets acceleration, OSEM, iteratively update activity estimates to fit those counts. Maximum-a-posteriori (MAP) methods additionally impose a prior or penalty to discourage implausibly noisy images. Deep learning can replace the whole mapping, learn the prior, or enhance an intermediate reconstruction. [4]

| Shared axis | Direct data-driven reconstruction | Model-driven reconstruction |
|---|---|---|
| Core idea | Learn measured-data-to-image mapping | Learn components within iterative reconstruction |
| Representative techniques | AUTOMAP, DeepPET, sinogram-to-image cGAN | Unrolled FBSEM, EM networks, ADMM/CNN methods |
| Physics representation | Largely learned through examples | Explicit forward model and data-fidelity updates |
| Training requirement | Representative measurements and image targets | Training data plus usable physical operators |
| Main strength | Flexible mapping and feed-forward inference | Measurements continue to constrain each reconstruction |
| Main computational burden | Learning a complex inverse mapping | Repeated projection operations and unrolled training |
| Main failure mechanism | Domain-specific learned mapping | Incorrect physics or excessive learned regularization |

**Direct networks learn the inverse mapping.** A direct network receives a sinogram and predicts the corresponding image, replacing conventional iterative inversion at inference. Dense layers can learn global changes between measurement and image coordinates, while convolutional layers learn structured features. The burden is substantial: the network must learn both the acquisition-dependent transformation and the statistical relationships between noisy inputs and desirable images. [4]

**Architecture changes the learning burden.** AUTOMAP used approximately 800 million trainable parameters, compared with approximately 60 million for the convolutional encoder–decoder DeepPET. The latter therefore represents a much more compact direct mapping. Parameter count is a model-size comparison, however, not an accuracy ranking: the decisive issue is whether the mapping retains quantitative fidelity on measurements that differ from its training distribution. [20]

**Adversarial reconstruction supplies a concrete example.** A 2022 conditional GAN, or cGAN, used a U-Net generator to reconstruct PET directly from sinograms and a whole-image discriminator to evaluate the generated image. Testing included simulated Zubal thorax and head phantoms, 12 rats, and nine human ^18F-FDG brain-PET patients. In the Zubal thorax phantom, full-image bias was less than one-tenth and variance less than 1% of the corresponding MLEM values. [21]

**The target determines the learned answer.** Those large reductions are phantom-image results, not a corresponding percentage improvement in patient diagnosis. The same study found difficulty with an extremely small region of interest and frame-dependent performance. A direct network trained against reconstructed reference images also learns characteristics of those references; it does not automatically produce an independent estimate of biological truth. [21][11]

**Model-driven networks retain measurement constraints.** Instead of replacing reconstruction, these methods unroll an iterative optimization algorithm into a sequence of trainable operations. A PET data-fidelity step continues to connect the image to measured emission data, while a CNN learns image regularization. Related designs use expectation-maximization, MAP optimization, block-coordinate descent, or the alternating direction method of multipliers (ADMM), which separates a difficult optimization problem into coupled subproblems. [4]

**FBSEM illustrates the mechanism clearly.** Forward–backward splitting expectation-maximization (FBSEM) divides each reconstruction update into regularization of the current image, an emission-data-based EM update, and weighted fusion of those results. Its unrolled recurrent implementation shares network parameters across reconstruction states and learns regularization strength. MRI can supply an additional input, but the PET counts remain part of the reconstruction process. [4]

| Method in the FBSEM comparison | Simulation NRMSE | In-vivo regional RSS error | Main operating principle |
|---|---:|---:|---|
| OSEM | 20.7% | 7.8% | Conventional likelihood reconstruction |
| MR-guided MAPEM | 17.7% | 5.9% | Reconstruction with anatomical regularization |
| Unrolled FBSEM | 14.4% | 3.9% | Emission updates plus learned regularization |
| Post-reconstruction U-Net | 13.4% | 5.7% | Learned enhancement of reconstructed images |

**The comparison separates error measures.** Normalized root-mean-square error (NRMSE) describes image error in the simulations; regional root-sum-of-squared (RSS) error summarizes uptake errors in the in-vivo brain analysis. The reported neural-network averages combine PET-only and PET/MR variants. Relative to OSEM, FBSEM’s simulation NRMSE reduction was a calculated 30.4%, from `(20.7 − 14.4) / 20.7`; this is an image-error reduction, not a clinical accuracy increase. [4]

**Physics did not guarantee universal superiority.** The post-reconstruction U-Net slightly outperformed FBSEM on average simulation NRMSE, and some simulated PET-specific lesions were better preserved by the U-Net. In vivo, the PET-only variants both achieved 4.7% regional RSS error, whereas adding MRI yielded 3.0% for FBSEM versus 6.8% for the U-Net. The evidence therefore supports a conditional advantage from physics integration, rather than an automatic victory for unrolling. [4]

**Reference physiology also matters.** The in-vivo study used 45 brain datasets, with 35 for training and ten for testing, and learned from two-minute data toward 30-minute reference images. The authors observed regional physiological differences between short and long acquisition windows. Consequently, a network could learn both noise suppression and a tendency toward later-window uptake, a distinction especially important in dynamic or rapidly changing tracer studies. [4]

**The practical choice follows the task.** Direct mapping is attractive when scanner conditions are stable, representative training pairs exist, and rapid inference is important. Model-driven reconstruction is attractive when explicit count consistency, correction modeling, or adaptation to changing count levels is central. Its advantage depends on a sufficiently accurate forward model and a learned prior that does not overwhelm the emission evidence.

**Reconstruction judgment favors justified complexity.** Retaining PET physics offers a principled constraint, but an optimized image-domain network can sometimes achieve comparable performance with a simpler deployment path; additional reconstruction complexity should earn its place through task-level quantitative gains.

### 3. Image post-processing and restoration

**The objective is image-domain improvement.** Post-processing starts with an already reconstructed PET image and aims to suppress noise, recover contrast, preserve uptake measurements, and support shorter acquisitions or lower administered activity. Unlike reconstruction methods that repeatedly use measured projection data, a standalone denoiser generally receives the image produced by the existing reconstruction chain. [20]

**Clinical quarter-count denoising is a strong example.** In a prospective multicenter external validation involving 50 adult cancer patients from three hospitals, SubtlePET enhanced whole-body ^18F-FDG PET reconstructed from 25% of standard counts. Enhanced scans were noninferior to standard scans in diagnostic image quality and overall diagnostic confidence. Patient-level lesion-assessment sensitivity was 0.94, specificity 0.98, and interscan agreement measured by Cohen’s kappa was 0.85. [2]

**Supervised learning uses paired targets.** SubtlePET’s 2.5-dimensional encoder–decoder U-Net uses neighboring slices to improve a central image slice, with training based on paired low- and high-count images. More generally, supervised CNNs learn from short/full-duration or low/standard-count pairs, often minimizing absolute or squared image differences. U-Net skip connections transfer spatial information from the contracting encoder to the expanding decoder, helping retain structures that simple smoothing would blur. [20][2]

**Counts are not total workflow time.** A 25%-count acquisition can correspond approximately to a fourfold shorter PET acquisition or reduced activity under suitable acquisition conditions. It does not imply fourfold greater department throughput, because patient preparation, uptake time, CT, positioning, and processing remain. Likewise, reducing PET activity is distinct from reducing the entire PET/CT examination’s radiation exposure.

| Learning approach | Training information | How restoration is learned | Practical advantage |
|---|---|---|---|
| Supervised U-Net | Paired low- and high-count images | Minimize output-to-reference error | Direct quantitative target |
| Supervised S-CycleGAN | Paired images plus adversarial constraints | Combine supervised, cycle, and identity losses | Balance appearance and uptake fidelity |
| Noise2Noise | Multiple noisy realizations | Predict one noisy realization from another | No clean reference required |
| Noise2Void | Single noisy images with masked pixels | Predict hidden pixels from surrounding information | No separate target acquisition |
| Deep image prior | One corrupted case and an untrained CNN | Optimize network parameters for that case | No population pretraining |
| Unpaired CycleGAN | Separate low- and high-quality image sets | Learn two-way domain translation | Can use unpaired cohorts |

**Hybrid losses can improve quantitative restoration.** Zhao et al.’s supervised S-CycleGAN used two generators and two discriminators, combining Wasserstein adversarial, cycle-consistency, identity, and supervised losses. Cycle consistency encourages a translated image to retain information needed to recover the input; identity loss discourages unnecessary changes to images already in the desired domain. The supervised component anchors the output to its corresponding full-dose reference. [22]

| Model at 10% brain-PET dose | Lesion SUVmean bias | Lesion SUVmax bias |
|---|---:|---:|
| S-CycleGAN | −6.4% ± 5.3% | −3.7% ± 16.2% |
| RED-CNN | −18.7% ± 11.8% | −24.9% ± 11.7% |
| 3D-cGAN | −20.0% ± 10.8% | −28.0% ± 16.5% |

**The benefit was reduced uptake bias.** Evaluation included ten clinical test datasets and 45 lesion-embedded simulations at 10% and 30% dose levels. S-CycleGAN inference took 74 milliseconds per image slice. The study favored 30% dose as a better balance between activity reduction and uptake preservation, illustrating that the strongest visual restoration need not justify the most aggressive count reduction. [22]

**Anatomical guidance can recover context.** A separate attention-weighted CNN combined simulated 6.25%-dose ^18F-FDG PET with five-slice MRI input in 23 children and young adults with lymphoma. Compared with the raw ultra-low-dose PET, mean peak signal-to-noise ratio increased from 51.6 to 55.6 dB, structural similarity index increased from 0.925 to 0.967, and NRMSE decreased from 0.257 to 0.158. Agreement with standard-dose interpretations, measured by weighted kappa, increased from 0.820 to 0.977. [23]

**Noise matching changes the optimum.** In a 195-patient ^18F-FDG study, separate 3D U-Nets trained at 20% and 60% count levels produced different trade-offs: the 20%-trained network suppressed more noise but blurred more, whereas the 60%-trained network preserved resolution better but left more noise. Blending their outputs allowed individualized control; at 20%-count input, a 90%/10% blend of those outputs optimized structural similarity. A single broadly trained model did not outperform appropriately noise-matched models. [24]

**Self-supervision replaces clean targets differently.** Canonical Noise2Noise trains from two noisy observations of the same underlying signal. If their noise is suitably independent and unbiased relative to that signal, the unpredictable component of the target cannot be consistently learned, while shared structure can. In PET, independent event partitions can generate the observations, provided count normalization and the reconstruction-induced noise structure are handled appropriately. [20]

**Wavelets provide a concrete implementation.** A 2021 PET Noise2Noise study split list-mode data into independent time-frame sinograms and combined a U-Net-based network with trainable forward and inverse wavelet transforms. The transforms separated low- and high-frequency components before reconstruction of the denoised output. In a clinical dataset of 14 ^18F-FDG brain scans—nine training and five test scans—the authors described ten-second denoised images as virtually equivalent to 300-second images filtered with a 6 mm Gaussian filter. The reference was therefore a deliberately smoothed image, not an unfiltered noise-free acquisition. [25]

**Blind spots remove another requirement.** Noise2Void masks selected pixels and predicts their values from surrounding image information. Because the network cannot directly copy the target pixel, it learns predictable spatial structure rather than pixel-specific noise. Its central assumption is that useful signal is spatially predictable while the relevant noise is sufficiently independent; reconstructed PET noise can violate that assumption through spatial correlation. [20]

**The choline study tested final images.** In 39 patients with pathology-confirmed diffuse glioma, a 2022 study compared Noise2Noise, Noise2Void, block-matching 3D filtering (BM3D), and non-local means on ^18F-fluoroethylcholine PET. Its Noise2Noise implementation added Gaussian noise to original PET images to create inputs, rather than using two separately measured independent PET realizations. That implementation detail matters when interpreting the comparison with canonical Noise2Noise. [26]

| Choline-PET denoiser | Mean CNR | CNR improvement over original images |
|---|---:|---:|
| Noise2Noise | 4.05 ± 3.45 | 13.60% ± 2.05% |
| Noise2Void | 3.89 ± 3.12 | 7.75% ± 2.07% |
| BM3D | 3.86 ± 3.06 | 1.62% ± 3.41% |
| Non-local means | 3.85 ± 3.06 | 1.37% ± 3.03% |

**Contrast improved more than uptake changed.** The study reported small changes in tumor SUVmean—0.85% for Noise2Noise and 0.58% for Noise2Void—and improved tumor-to-normal ratios. Its tumor contours were physician-assisted and retained during post-processing, so unchanged metabolic tumor volume in this experiment reflects a fixed-region analysis, rather than independent validation of automated volume recovery. [26]

**Deep image prior learns per case.** A deep image prior (DIP) uses the structure of an initially untrained CNN as an implicit regularizer. Random noise or an anatomical image can serve as input, and the network is optimized against the corrupted PET case. Useful image structure tends to be represented before the network fully fits noise, making the stopping point part of the restoration method. This removes population-level paired training but introduces case-specific optimization and, with anatomical guidance, registration dependence. [4]

**Unpaired translation learns population correspondence.** An unpaired CycleGAN can learn a low-quality-to-high-quality transformation from separate image collections. The benefit is access to training material without exact image pairs. The trade-off is that matching the target distribution does not uniquely determine which small focus belongs in a particular patient; cycle and identity constraints help preserve content but are not a substitute for lesion-level assessment.

**A convincing image can mislead.** A 2023 study applied a parameter-transferred Wasserstein GAN, PT-WGAN, to simulated 25%-activity ^64Cu-DOTATATE PET in 38 patients with neuroendocrine neoplasms. AI images correlated more closely with full-dose images than did the low-dose inputs, with R² of 0.94 versus 0.81; 32 of 33 clinically assessed AI studies received good or excellent image-quality scores. [27]

**Lesion counts changed the conclusion.** The full-dose reference contained 118 lesions. AI images yielded 115 detections, but only 78 were true positives: sensitivity was 66%—78/118—and false-discovery rate was 32%—37/115. Of those 37 false-positive foci, 23 were judged definite lesions by readers. This example demonstrates the difference between reproducing overall image intensities and preserving trustworthy individual abnormalities. [27]

**Restoration judgment requires task preservation.** Supervised, self-supervised, and unsupervised methods can all improve PET appearance and quantitative stability, but the clinically relevant acceptance criterion is preserved lesion information and uptake—not smoothness or similarity alone.

### 4. Motion artifact correction

**The objective is spatially consistent activity.** AI motion correction estimates movement and uses that estimate to align frames or compensate during reconstruction. For respiratory motion, a representative unsupervised registration study reduced simulation normalized root-mean-square error from 41.9% ± 2.0% ungated to 24.3% ± 1.7% with deep-learning compensation. Its mechanism was nonrigid alignment of respiratory gates followed by reconstruction using the gated measurements. [5]

**Breathing spreads activity across positions.** A lesion moving through the acquisition contributes counts at several locations, lowering its apparent peak uptake and broadening its apparent extent. Heartbeat motion similarly moves and deforms the myocardium. In dynamic cardiac PET, displacement between reconstructed time frames also changes which tissue lies within a measurement region, distorting time–activity curves and therefore myocardial blood-flow estimation. [5][28]

**Gating trades blur against counts.** Respiratory or cardiac gating divides events by motion state, making each state more nearly motion-frozen but reducing the counts in each image. Motion compensation attempts to recover both advantages: estimate transformations between states, then combine or reconstruct all accepted events in a common anatomical reference. Merely denoising a blurred image does not explicitly recover those temporal transformations.

| Named method | Motion information | Main AI operation | Reported effect |
|---|---|---|---|
| Stacked registration CNN | Respiratory-gated PET pairs | Predict nonrigid deformation with spatial transformers | Simulation error 24.3% versus 41.9% ungated |
| DL-ADMM | Respiratory gates and emission data | Jointly update activity and learned registration | Matched-noise error 26.5% versus 42.1% ungated |
| FlowNet-PET | Breathing-amplitude image pairs | Predict optical flow and align counts | Median residual below 2 mm slice thickness |
| Res-Voxel | Respiratory image pairs | Residual 3D U-Net deformation prediction | Clinical-data Dice 0.7510 |
| DeepMC | Dynamic ^82Rb cardiac sequence | Predict inter-frame translations with recurrent learning | Better motion and blood-flow accuracy than compared registration methods |

**Spatial transformers enable label-free registration.** The stacked registration framework combined CNN encoder–decoders with differentiable spatial transformer networks. The CNN predicts a deformation; the transformer warps the moving image; training minimizes dissimilarity from a fixed image while penalizing irregular deformation gradients. Because the loss can be calculated from the images, true deformation-field labels are unnecessary. Successive subunits refine motion from coarse displacement to finer detail. [5]

**Reconstruction reuses the gated measurements.** The estimated fields were incorporated into iterative PET reconstruction: the current reference image is transformed into each gate, projected against that gate’s measurements, and the corresponding corrections are transformed back. This differs from simply averaging separately reconstructed gates. In the study’s 11 test phantoms, conventional iterative-registration compensation produced 31.1% ± 1.4% error, intermediate between the learned method and ungated reconstruction. [5]

**Learned registration also reduced computation.** After training, registration required eight seconds per image pair, compared with approximately 15–20 minutes for the iterative method—roughly two orders of magnitude faster. Clinical examples showed sharper liver boundaries, higher lesion contrast than ungated imaging, and lower noise than an individual reference gate. [5]

**Joint estimation addresses noisy motion inputs.** DL-ADMM alternates gated-image reconstruction, learned motion estimation, and motion-compensated image fusion. The rationale is circular but useful: better images support better deformation estimates, and better deformation estimates support better images. In 22 XCAT digital phantoms, with 11 assigned to testing, matched-noise error was 26.5% ± 2.2%, compared with 33.2% ± 0.9% for iterative joint estimation and 42.1% ± 2.8% ungated. [29]

**The joint method exposes a speed trade-off.** A faster DL-ADMM configuration reduced runtime from approximately eight to 1.5 minutes per iteration while increasing error from 26.5% to 27.2%. The clinical implementation also used estimated deformations to generate phase-matched attenuation maps, addressing a separate source of bias when emission anatomy moves relative to the CT used for correction. [29]

**Optical flow offers count-preserving alignment.** FlowNet-PET used an unsupervised 3D CNN to predict displacement between breathing-amplitude frames. A photometric loss encouraged aligned images to agree, while an invertibility loss encouraged one-to-one correspondences. In six XCAT test phantoms with 25 mm lung lesions and diaphragm excursions of 9–21 mm, median flow residual was below the 2 mm slice thickness and 4 mm pixel width. [30]

**Its benefits depended on the reference.** Relative improvements against uncorrected images averaged 64% for tumor intersection-over-union, 89% for enclosed activity, and 75% for coefficient of variation. Similar results to conventional retrospective phase binning were obtained with one-sixth of the scan duration in the digital-phantom comparison. These percentages concern recovery toward no-motion references, not absolute clinical sensitivity gains. [31]

**Residual networks provide another implementation.** Res-Voxel used a residual 3D U-Net to predict deformation fields, with smaller convolution kernels intended to reduce computational demand. Its reported Dice indices were 0.9381 for geometric phantoms, 0.8175 for voxel phantoms, and 0.7510 for clinical data. The variation across these settings illustrates why synthetic geometric alignment is a different task from clinical registration. [32]

**Cardiac dynamics require temporal interpretation.** DeepMC used a bidirectional three-dimensional convolutional long short-term memory network—ConvLSTM—to combine local and longer-range temporal information in dynamic ^82Rb PET. It estimated three-dimensional frame translations and applied reverse shifts to align the original frames, improving consistent sampling of myocardial time–activity curves. [28]

**Its training count was not patient count.** DeepMC used one million simulated-motion samples derived from 65 patient scans for training, 600 samples from 20 scans for evaluation, and ten additional datasets with real patient motion. It outperformed the compared conventional registration methods and other CNNs for motion estimation and myocardial blood-flow accuracy, with faster inference after training. [28]

**Inter-frame correction differs from heartbeat correction.** DeepMC modeled rigid translation between dynamic frames; intra-frame cardiac and respiratory motion was averaged within frames. FlowNet-PET, trained on breathing-separated states, explicitly learned to ignore motion not correlated with respiration, including heart motion. Correcting the displacement of the heart between frames is therefore a demonstrated cardiac-PET application, but it is not equivalent to resolving deformation through each heartbeat. [28][30]

**Motion judgment depends on temporal scope.** AI can accelerate respiratory deformation estimation and improve dynamic cardiac alignment, but a method should be described according to the motion states it actually models: breathing phase, inter-frame translation, and beat-resolved deformation are distinct problems.

**Additional documented evidence**

| Entity | objective | problem or bottleneck | main AI techniques | technical mechanism | specific effects or advantages | limitations and uncertainty | study-effects time series |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Image Acquisition Enhancement | no evidence found | Scattered coincidences typically account for 30–50%…[57] | no evidence found | Scattered coincidences typically account for 30–50%…[57] | 30–50% of the detected coincidence events[57] | no evidence found | no evidence found |
| Image Reconstruction | The video description says it is a “Brief tutorial…[58] | no evidence found | PWLS requires fewer iterations and may be more tolerant…[56] | The video description says it is a “Brief tutorial…[58] | no evidence found | PWLS requires fewer iterations and may be more tolerant…[56] | no evidence found |
| Image Post-processing and Restoration | The cited literature includes PET image denoising…[68] | The cited literature includes PET image denoising…[68] | Examples of unsupervised or non-clean-reference…[64] | Examples of unsupervised or non-clean-reference…[64] | Using PET-MR data, FBSEM-Net can enhance PET image…[59] | Applications outside the head may pose challenges due…[67] | no evidence found |
| Motion Artifact Correction | no evidence found | no evidence found | A cited PET method uses advanced optical flow…[70] | A cited PET method uses advanced optical flow…[70] | no evidence found | no evidence found | no evidence found |

rejected: number_unsupported. The table shows no evidence for Image Acquisition Enhancement; Image Reconstruction maps noisy sinograms to tracer images with data-driven CNN/GAN and model-driven unrolling [59][61][62], whereas Image Post-processing and Restoration denoises after reconstruction and Motion Artifact Correction estimates motion fields to reduce blur [60][63][71][69]. The motion row reports a 2019 septal-Ki gain of 18% [66], while the table also flags unresolved clinical validation, small-cohort and motion-free-reference limitations [60][62][66].

**Workflow-stage coverage matrix**

Part One follows the PET data path rather than treating all neural-network operations as “reconstruction.” Measured coincidence events may remain in list mode, where they can be streamed and processed event by event, or be represented as sinograms; reconstruction maps those measurements to an image. Post-processing instead acts on an already reconstructed, degraded image. Motion estimation can interact with preprocessing, registration, gating, or reconstruction, so it is best treated as a cross-stage correction rather than as ordinary denoising [55][59][65].


| PET workflow application | Technical objective and problem solved | Main AI techniques and paradigms | AI mechanism and workflow location | Specific reported effects or advantages | Limitations, uncertainty and readiness |
|---|---|---|---|---|---|

## Part Two — Specific Tasks in Clinical PET Applications

### 1. Image segmentation

**The objective is usable tumor contours.** AI segmentation automatically or semi-automatically assigns image voxels to tumors or other regions of interest, reducing labor and reader variability while supporting measurement, response assessment, radiomics, and treatment planning. In an early ^18F-fluoroethyltyrosine (^18F-FET) glioma study, all 11 validation lesions were detected without false positives, and refined segmentation achieved Dice overlap of 0.8231. [6]

**Automatic networks predict voxel labels.** Fully convolutional networks such as 3D U-Net produce tumor-probability maps from PET, CT, or combined PET/CT inputs. Encoder features provide context, while decoder features recover spatial detail. nnU-Net additionally automates many preprocessing, architecture-configuration, and post-processing decisions; cascaded networks can first find disease at lower resolution and then refine it at higher resolution. [33][34]

**Semi-automatic methods retain targeted interaction.** A clinician can identify a lesion or initialize a three-dimensional region, after which clustering, a CNN, or a graph-based method delineates the boundary. This separates the difficult question “which uptake is disease?” from “where is its boundary?” Simple thresholds and morphology can assist these pipelines, although a fixed threshold alone is not a learned AI method.

| Named workflow | Automation and technique | Clinical material | Reported result |
|---|---|---|---|
| Blanc-Durand et al. | 3D U-Net, then morphology and thresholding | 37 FET glioma patients; 11 validation | Refined Dice 0.8231 |
| Zhong et al. | Separate PET/CT U-Nets plus graph cuts | 32 lung-cancer pairs; 12 test | PET Dice 0.757 to 0.760 with refinement |
| Lymphoma SAC Bayesian | Initialized ROI and Bayesian clustering | 65 patients; 920 lesions or clusters | Interobserver Dice 0.94 versus 0.84 manually |
| PET-only CNN/texture methods | Lesion-box initialization, then learned segmentation | Lung-cancer testing and independent retesting | Retest intraclass agreement 0.99 for CNN |
| TMTV-Net | Cascaded multiresolution 3D U-Nets | Multicenter lymphoma external set, 518 scans | External Dice 0.66 ± 0.18 |

**Detection and boundary refinement can cooperate.** The FET pipeline first used a U-Net to identify the glial-tumor region, then applied morphological dilation and uptake thresholding. Validation Dice increased from 0.7911 to 0.8231 after refinement. This design is clinically sensible because the maximum-uptake location is not necessarily the tumor, and a learned localization step can restrict subsequent intensity-based delineation to an appropriate region. [6]

**Multimodal consistency can refine boundaries.** Zhong et al. trained separate 3D U-Nets for PET and CT, then used their probability maps in graph-cut co-segmentation. Label-consistency constraints encouraged agreement while allowing modality-related differences. The experiment used tumor-centered crops; its removal of manually specified object seeds should therefore be distinguished from unrestricted whole-body tumor discovery. [33]

**The PET gain was modest.** On the 12 test cases, graph-cut refinement changed PET Dice from 0.757 ± 0.088 to 0.760 ± 0.088, while CT Dice changed from 0.856 ± 0.074 to 0.869 ± 0.049. The broader improvement over earlier methods came mainly from learned probability estimation. PET’s gradual uptake boundaries explain why anatomical co-segmentation can help without eliminating ambiguity. [33]

**Deep learning is not always best.** In the 65-patient lymphoma comparison, semi-automatic Bayesian clustering achieved interobserver Dice of 0.94 versus 0.84 for manual segmentation, with intraclass correlation coefficients—ICCs—of at least 0.92 for several uptake and volume measures. It performed favorably against the evaluated deep-learning segmenters. Bayesian clustering explicitly models intensity distributions and noise within an initialized region, which can be an advantage when the clinician has already resolved lesion identity. [35]

**Repeatability deserves separate assessment.** An independent lung-cancer test–retest analysis reported absolute mean volume differences of 13.9% for CNN segmentation and 13.0% for a random-forest texture approach, versus 28.1% for a 41%-of-SUVmax threshold. ICCs were 0.99 and 0.98 for the two learned methods. The reported percentage-difference comparisons did not remain statistically significant after multiple-comparison correction, so the strongest conclusion is favorable measured repeatability, rather than proven superiority on every endpoint. [36]

**Overlap can conceal consequential mistakes.** In the lymphoma comparison, three semi- or fully automatic deep-learning methods produced an incorrect lesion SUVmax in 20 of 65 patients, sometimes by including nonmalignant uptake with higher intensity than the true tumor. A contour can overlap much of the disease yet still yield an invalid measurement or include the wrong highest-uptake focus. [35]

**Segmentation judgment favors appropriate interaction.** Fully automatic networks are valuable for scalable contour generation, while well-designed semi-automatic methods can offer excellent reproducibility when lesion identity is ambiguous; clinical usefulness depends on correct tissue assignment as well as overlap.

### 2. Lesion detection and classification

**The objective has two components.** Detection asks where suspicious findings are located; classification asks what they represent, including benign versus malignant disease. A detector may be optimized to miss few abnormalities, whereas a malignancy classifier must also control false-positive decisions. These tasks use different reference labels and should not share an undifferentiated “accuracy” claim.

**Pathology-linked results show the trade-off.** A 2022 automated high-resolution representation-learning model, HRRL/HRNet, evaluated 112 pulmonary nodules, comprising 79 malignant and 33 benign pathology-confirmed lesions. Fivefold cross-validation produced AUC 0.781, sensitivity 89.9%, specificity 54.5%, and approximately 79.4% accuracy. The sensitivity is useful for identifying suspicious nodules, but the specificity means many benign lesions still received positive classifications. [7]

**Networks combine complementary information.** Whole-body 3D CNNs can triage scans; ResNet models classify image patches; HRNet preserves high-resolution representations for localization; and PET/CT multi-stream models combine metabolic intensity with anatomical morphology. Feature-based alternatives use texture, shape, location, uptake, and clinical information with random forests, extreme gradient boosting, deep neural networks, or logistic regression.

**Architecture improved automated nodule classification.** In the HRNet study, automated HRNet achieved sensitivity 0.899 and specificity 0.545, compared with 0.785 and 0.394 for automated ResNet. HRNet AUC was 0.781 with automatic localization versus 0.789 with manual localization, supporting the value of removing expert localization from that particular workflow. [7]

**Small radiomic models can add value.** A 48-patient solitary pulmonary nodule study included 31 malignant and 17 benign lesions, using pathology or follow-up as the reference. PET texture features were extracted after semi-automatic 40%-of-SUVmax delineation. The deep neural network achieved approximately 0.81 AUC and 88% sensitivity versus 83% for conventional evaluation; extreme gradient boosting achieved 86% specificity versus 79% conventionally. These were complementary changes in operating characteristics, not proof that one model dominated every measure. [37]

**Multistream fusion can improve discrimination.** Gao and Shao used ImageNet-pretrained MobileNet models for benign–malignant ground-glass nodule classification, with 142 nodules for development and 42 for external validation. Their development comparisons isolate the contribution of different information streams. [38]

| Development model | Information used | Development AUC |
|---|---|---:|
| PET stream | PET appearance | 0.741 |
| CT stream | CT morphology | 0.772 |
| Dual stream | PET and CT | 0.922 |
| Triple stream | PET, CT, and selected clinical/morphological variables | 0.950 |

**External results belonged to different models.** In the 42-nodule external set, the CT-only model had the highest sensitivity, 0.914, whereas the triple-stream model had the highest specificity, 0.714. Those figures should not be combined into the sensitivity–specificity pair of a single classifier. The CT model improved reclassification relative to a reader with three years’ experience but did not differ significantly from a reader with ten years’ experience. [38]

**Simpler fusion provides an important counterexample.** A 2023 logistic-regression model combined 12 clinical, CT, and PET variables in a 1,068-case early-lung-cancer dataset. Its 691 testing and validation cases yielded sensitivity 86.5%, specificity 68.1%, accuracy 82.1%, and overall AUC 0.89; a CT-only model had AUC 0.83. Experienced physicians nevertheless achieved 88.9% accuracy in the same testing/validation material, exceeding the model’s 82.1%. [39]

**Routine scans change the problem.** The CLARITI project used a 3D CNN to classify whole-body FDG PET scans for triage. Its performance differed substantially between an intentionally unambiguous dataset and heterogeneous real-life scans. [40]

| CLARITI evaluation setting | Sensitivity | Specificity | Negative predictive value |
|---|---:|---:|---:|
| Unambiguous set; 108 independent test scans | 84% | 98% | 85% |
| Real-life dataset; 4,963 scans | 61% | 79% | 40% |

**Negative triage needs particular caution.** The decline in negative predictive value means that reassuring model output was much less reliable in the real-life setting. Predictive values depend on disease prevalence as well as sensitivity and specificity, while routine cases also introduce equivocal uptake, varied anatomy, and technically imperfect images. A high result on clearly positive and clearly negative examples therefore does not establish safe exclusion of disease in routine work.

**Lesion size sets count requirements.** Guo et al. fine-tuned ResNet-50 using 20 patients with biopsy-proven primary lung cancer, including a four-patient test subset at nine simulated count levels. For lesion patches smaller than 10 mm, AUC of at least 0.96 required two million true counts; larger lesions achieved that criterion at 0.25 million counts. The study associated these levels with effective doses of 0.08 and 0.01 mSv, respectively. This was a count-dependent patch-classification experiment, not a general low-dose prescription for benign–malignant diagnosis. [41]

**Detection judgment favors second-reader use.** Through early 2024, the evidence supports AI for finding candidates, prioritizing scans, and ranking malignancy probability; autonomous reassurance or definitive benign–malignant adjudication demands stronger routine-data performance than high development AUC alone.

**Additional documented evidence**

**Objective and mechanism**

Lesion Detection and Classification uses AI to find, localize, segment and label PET foci—FDG-positive tissue, benign-to-metastatic bone grades, T/N/M stage or amyloid positivity—to reduce missed disease, staging error and reporting burden. CNN/3D-CNN models map PET/CT context to masks, boxes, locations or probabilities; expert labels, not always pathology, usually define the reference [108][123][162].

**PET evidence to 2024-03-31.** Patch-3D-DenseNet trained on 300 FDG-PET/CT cases gave 86% per-scan sensitivity, 3 false positives and a TP/FP ratio of 1.69; voxel analysis yielded 93% sensitivity, 88% PPV and Dice 86%. CNN FDG-uptake classification in lymphoma/lung cancer had AUC >0.95; DeepMedic nodal detection was comparable with experienced physicians. PSMA pelvic-node AI was likewise reported as physician-level, although no metric or denominator was supplied [108]. In 18F-NaF PET/CT (37 mCRPC subjects, 1,751 lesions; five-point benign-to-metastatic labels), random forests/SORT with 172 PET, CT and spatial features gave AUC .95 (95% CI .94–.95), sensitivity 88% (86–90), and specificity .89 (.87–.90), versus fixed-SUV AUCs .87/.86 (p<.001); physician agreement was κ=.53 and model AUC .91–.93 across four references [123].

Retina U-Net used PET+CT, segmentation supervision, box regression and anatomical T/N/M regions. In 364 histology-confirmed lung-cancer FDG-PET/CTs (216/74/74 train/validation/test), T/N/M sensitivity was 86.2%/54.2%/72.4% at 2.0 FP/c; 233/247 (94.3%) categories were correct, while external malignant-lesion sensitivity was 127/143 (88.8%) at 2.7 FP/c [162]. A breast-cancer CNN trained from 130 PERCIST- and physician-labeled FDG-PET/CT studies achieved sensitivity .96 (95% CI .90–1.00), specificity 1.00, Dice .94 and Jaccard .89 [117]. Fourfold reduced-count PET deep learning retained patient-level sensitivity .94 (.83–.99), specificity .98 (.95–.99), interscan κ=.85 and SUV CCC=.94 in multicenter/multivendor external testing [211].

For 18F-florbetaben, a 2D CNN plus fully connected network achieved 100% subject-level and 95% slice-level accuracy; among 54 equivocal scans, deep learning classified 37/54 as positive versus 40/54 by visual assessment or SUVR, agreeing with quantification in 45/54 (83%; κ=.59) [127]. In the 11 January 2024 lymphoma reader study, pre-segmentation reduced reporting time from 15.0 to 13.3 min (11.3%, p<.001), without changing report quality (p=.11), and increased confidence from 7/10 to 8/10; 80/88 false-positive/false-negative reports were unaffected, but trainees overlooked 3/15 (20%) false-negative segmentations [124].

**Limits.** Physiologic uptake, small or low-activity lesions, scanner/tracer/threshold and label variability, workflow bias, small or single-centre cohorts, domain shift and spurious features limit transfer. Denoising preserved 369/371 lesions (99.5%) but missed two small bone lesions and shifted SUVmax by −7.7±5.6% and SUVpeak by −2.8±5.3% [208]. PET AI should be demonstrably true, reproducible, useful and explainable [99]. Post-cutoff CT-only VGG16 and CT-to-PET FCN/GAN evidence is excluded; PML/Patlak dynamic PET is model-based, not AI [209][212][210].

AI is decision support: it proposes lesion locations/ROIs and labels; physicians adjudicate.

In 2017 F-18 NaF PET/CT, a tenfold-cross-validated random forest used bone-specific thresholds and 170 PET/CT texture/spatial features to label lesions as definite/likely metastasis, equivocal, or likely/definite benign. Among 37 patients (1,752 lesions; 598 additionally reviewed), AUC was 0.95 versus 0.86 (SUV>15 g/mL) and 0.87 (SUV>10 g/mL), with 88% sensitivity, 88% specificity, 83% PPV and 92% NPV (p<0.0001) [170]. It addresses benign uptake, false positives and review of hundreds of lesions.

PARS (2021) used fixed-threshold VOIs, PET/CT views, MIPs and atlas position, then a CNN classified FDG foci as suspicious/not suspicious; outputs were location, TMTV, TLG and Deauville score. Automatic/manual Dice and TMTV ICC were 0.65/0.68 (119 DLBCL research patients) and 0.48/0.61 (430 routine oncology patients); automated TMTV was prognostic for PFS/OS [182]. Under-segmentation and false negatives required manual checking [182].

In [64Cu]Cu-DOTATATE PET (2022), 7/41 (17%) needed no adjustment and 35/41 (85%) were acceptable after adjustment; correction took 5 versus 17 min (n=10, p<0.01), but one control produced 56 false-positive volumes totaling 68.6 mL [213]. In 2019 evidence, lesions <20 mm and scanner-dependent uptake in benign and malignant lesions required adapted standards [78]. Physician-label agreement was 63%; tracer/protocol transfer and external validation limit readiness [170][213][215].

PET lesion AI evidence supports AI as a reader aid, not autonomous diagnosis. In 2022 [18F]PSMA-1007 PET-CT, UNet3D achieved 82% lesion sensitivity (76–90%) versus 77% for readers and 1.8 false-positive lesions/patient (50-test/211-patient cohort) [126]. In breast-cancer FDG PET/CT, a CNN reported sensitivity 0.96 and specificity 1.00 for lesion/lymphadenopathy [217]. PSMA evidence was reader-referenced, not pathology-verified, single-centre, single-tracer and externally unvalidated [126]. A 2020 deep-CNN uptake-classification citation in lymphoma/lung cancer gives no benign/malignant labels or metrics [187][216]. A 99-study review flags annotation scarcity, overfitting and uncertainty [214].

### 3. Quantitative analysis

**The objective is reproducible tumor burden.** AI quantitative analysis converts accepted tumor regions into measurements such as metabolic tumor volume, total metabolic tumor volume, total lesion glycolysis, uptake statistics, and spatial dissemination. In a 100-patient diffuse large B-cell lymphoma study, automated metabolic tumor volume correlated approximately 0.981 with two readers and achieved ICC 0.98 against each. [8]

**MTV measures an identified metabolic region.** Metabolic tumor volume (MTV) is the volume of a segmented metabolically active lesion or region. Total metabolic tumor volume (TMTV) is the sum across all accepted tumor lesions. Total lesion glycolysis (TLG), used particularly with FDG, combines lesion volume and mean uptake. [42][35]

\(\mathrm{MTV}_k=\sum_{v\in L_k}\Delta V_v,\qquad \mathrm{TMTV}=\sum_{k=1}^{K}\mathrm{MTV}_k,\qquad \mathrm{TLG}_k=\mathrm{MTV}_k\,\mathrm{SUVmean}_k.\)

**The arithmetic is straightforward after classification.** Here, \(L_k\) is the set of voxels assigned to lesion \(k\), and \(\Delta V_v\) is voxel volume. MTV and TMTV are normally expressed in milliliters or cubic centimeters; TLG is volume multiplied by the chosen SUV measure. The difficult AI task is deciding which regions enter the calculation and where their boundaries lie, not summing voxel volumes.

| Named quantitative system | Evaluated population | Agreement with reference | Additional reported effect |
|---|---|---|---|
| PARS | 301 baseline DLBCL scans | TMTV Spearman correlation 0.76 | Prognostic hazard ratios 2.3 for progression and 2.8 for death |
| Kuker automated MTV | 100 newly diagnosed DLBCL patients | Pearson correlations 0.9814 and 0.9818; ICC 0.98 | No manual intervention in evaluated pipeline |
| TMTV-Net | 518 multicenter external lymphoma scans | TMTV correlation 0.89 | Absolute error 157.32 ± 378.12 mL |

**PARS first separates suspicious uptake.** The PET Assisted Reporting System (PARS) detects high-uptake regions and uses a CNN trained on an independent cohort to classify them as suspicious or nonsuspicious. The volumes of suspicious regions are summed into automated TMTV. In 301 patients from the REMARC phase III trial, uptake-region classification achieved 85% accuracy, 80% sensitivity, and 88% specificity. [42]

**The automated measurement preserved prognostic information.** PARS TMTV correlated with expert-derived TMTV at Spearman ρ = 0.76. For the study’s risk comparisons, progression-free-survival hazard ratios were 2.3 for automated versus 2.6 for reference TMTV, and overall-survival hazard ratios were 2.8 versus 3.7. This supports preservation of useful prognostic signal, not superiority over expert measurement. [42]

**Organ recognition removes physiological confounders.** Kuker et al.’s pipeline used a two-dimensional dilated residual U-Net to segment normally FDG-avid structures on CT, including brain, heart, kidneys, and bladder. These contours were transferred and adapted to PET; region-processing and volume rules, together with a 41%-of-SUVmax threshold, generated automated tumor measurements. AI therefore supplied anatomical exclusion information, while conventional image operations completed part of the measurement. [8]

**High agreement supports workload reduction.** Against reader one, Pearson correlation was 0.9814 and ICC 0.98; against reader two, the corresponding values were 0.9818 and 0.98. These results support automated processing of the evaluated cases without manual region construction. They do not imply that all anatomically unusual or physiologically avid structures will be classified correctly.

**External errors reveal the full distribution.** TMTV-Net used cascaded multiresolution 3D U-Nets, fivefold development, soft-voting ensembles, and a semi-supervised loss. Its 1,418 scans from four centers comprised 900 development/validation/testing scans and 518 external scans, covering several lymphoma subtypes. Internal Dice was 0.68 ± 0.12 and external Dice 0.66 ± 0.18. [34]

**Correlation does not express absolute error.** Despite external TMTV correlation of 0.89, average relative error was 0.43 ± 0.54, and average absolute error was 157.32 ± 378.12 mL. After exclusion of 53 outliers—approximately 10% of the external set—the corresponding errors were 0.30 ± 0.22 and 82.05 ± 99.78 mL. The all-case values are the appropriate headline; the outlier-excluded results show how much the error distribution depends on difficult cases. [34]

**Prognostic signal can coexist with missed lesions.** An independent PARS evaluation in 115 suspected or known lung-cancer patients found per-lesion sensitivity of 55.6% for lung tumors and 35.3% for lymph nodes. Nevertheless, automated lung-tumor TLG remained associated with overall survival, with hazard ratio 1.90 versus 1.99 for manual TLG. An aggregate burden measure can retain patient-level risk information while being insufficiently complete for staging. [43]

**Quantification judgment prioritizes valid lesion selection.** AI can remove substantial manual processing and produce reproducible burden metrics, but correlation, prognostic association, and complete lesion accounting answer different questions and should be reported separately.

**Additional documented evidence**

**Objective, definitions and pipeline**

AI-based **PET Quantitative Analysis** converts PET/PET/CT into lesion masks and tumor-burden metrics, addressing the labor, observer variation and missed lesions of manual whole-body delineation for prognosis and response assessment [182][229].

**MTV** is the volume of a segmented metabolically active lesion; **TMTV** sums all malignant FDG-lesion volumes. Retain each source’s mL/cm³, tracer, lesion-inclusion rule, threshold and reference contour. In PARS (FDG lymphoma; 26 February 2021), manual research contours used 41% of SUVmax, whereas its CNN used 42% of local SUVmax after selecting foci >2 mL in the research cohort or >1 mL in routine use [182]. SUV is normalized to injected activity and body weight; SUV ≥2.5 is a reported malignancy-indicative threshold, not an MTV/TMTV definition [224].

The workflow is PET/CT → threshold or ROI candidates → pathological-versus-physiological classification → lesion mask → per-lesion MTV → TMTV. Reported methods include supervised CNN/PARS, 3-D DeepMedic and fully convolutional networks, SVM/ANN/FCM, active contours, region growing, k-means and Bayesian two-class clustering; k-means uses nearest centroids, whereas Bayesian clustering estimates voxel-class probabilities [182][229][220]. A CNN/PERCIST pipeline can generate three-dimensional VOIs, but its supplied results do not report MTV/TMTV accuracy [161].

**Cutoff-compliant effects.** In 90 lymphoma patients with 1,223 lesions and a 20-patient second-reader subset (25 November 2020), DeepMedic was best for lesion segmentation; CNN, clustering and iterative-threshold methods matched inter-reader agreement for patient-level SUVtotal/MTV, unlike 40%/50% SUVmax and adaptive region growing [229]. On 14 April 2023, manual-versus-SAC-Bayesian MTV/TLG agreement was ICC ≥0.92, but TMTV was not reported [220]. PARS in 119 DLBCL patients produced automatic-versus-manual TMTV Dice 0.65 and ICC 0.68; PFS hazard ratios were 2.1 versus 3.3 and OS hazard ratios 2.4 versus 3.1 at 5-year follow-up. In 430 routine patients, Dice was 0.48 and ICC 0.61, requiring verification and correction [182].

Image-quality endpoints are not MTV/TMTV validation: a 50-patient 18F-FDG PET/CT denoising study from April–May 2019 versus Gaussian filtering improved reader scores (P<0.001; κ=0.78) but changed tumor SUV and reported no MTV/TMTV [224]. Non-AI NLM/deconvolution on ADNI PET improved COV 1.34-fold and CNR 1.23-fold without a gold standard [74]. CycleGAN partial-volume correction in 212 brain scans, four tracers and 83 regions (20 February 2023) achieved SUV R²>0.98 and RMSE<0.15 SUV versus MRI-guided PVC, not MTV/TMTV [218].

Limits are partial-volume/spill-in/out effects from 3.5–6-mm resolution, small-lesion and threshold bias, protocol/domain shift, and limited external or clinical validation [88][182][225]. Later evidence is outside the 31 March 2024 cutoff: September 2024 aTMTV reported *n*=367 and *r*=0.955 versus manual TMTV; October 2024 autoPET evaluated 150 test studies using mostly 3-D U-Nets; and a June 2025 DenseNet benchmark reported 80% level-1 compliance, Dice 99%/96%/95% and ICC 0.95 [231][219][221]. These and 2025 motion/MTV studies are excluded from cutoff-compliant evidence [227][228].

AI CNN/U-Net: PET MTV/TMTV; DSC 0.66±0.18 (n=518, 2024); thresholds vary [125][232].

AI CNNs automate MTV/TMTV; MTV uses 41% SUVmax; DLBCL:100 cases, 5 vs 20 min, 2022 [226]

Quantitative Analysis: DL TMTV r=.96 (n=367) vs manual; ≤10 mL sens=.67, PPV=.72 [233]

Quantitative Analysis: AI defines MTV as segmented-tumour volume; TMTV aggregates MTV across metastatic lesions/nodes, with ΔTMTV(%)=100×(TMTV1−TMTV0)/TMTV0 [99][153]. CNN/U-Net and transformer models map PET/CT to lesion masks and volumes (mL/cm³) [160]. The objective is faster, more consistent burden/prognostic assessment than manual contouring [160]. Post-cutoff FDG context used a study-specific SUV>4.0, excluded inflammatory uptake, and reports manual contouring at ~15 min/study [153]. High Dice did not ensure reproducible TMTV: external testing found poor reproducibility and outliers when ground-truth TMTV exceeded 100 ml; held-out, representative validation is essential [160][222]. [153] (22 Apr 2024) and [223]/[192] (2025/26) are outside the 31 Mar 2024 cutoff.

AI PET quantification: CNN/U-Net segmentation computes MTV; TMTV needs lesion aggregation, tracer, threshold, unit and contour, but no cutoff-compliant result is supplied [454,456]. NSCLC FDG-PET/CT (225; train/test 180/45): deeper U-Net MTV/TLG normalized errors 0.02/0.03 vs 0.11/0.09, despite Dice 0.90 vs 0.91 [230]. Florbetaben PET/CT (100): 3D-U-Net SUV/SUVr error <5% vs MLAA ≥20%; 50 bootstrap reconstructions quantified uncertainty [304,394]. Dice may diverge from task accuracy; technical accuracy is not clinical benefit [188].

Quantitative Analysis automates the segmentation-to-metric step to address slow manual delineation: MTV is an 18F-FDG PET biomarker of tumour glycolytic activity, while TMTV aggregates lesion MTVs. CNN/U-Net or end-to-end deep learning segments lesions and calculates volumes; preserve MTV (mL or cm3), TMTV (mL), standardized values (mL/kg; patient-weight denominator), threshold (SUV 4.0 or 41% SUVmax), and ΔTMTV=100×(TMTV1−TMTV0)/TMTV0 between baseline and interim PET [55,402,452,250,123,263].

It directly serves the PET-AI research purpose by converting PET/CT into tumour-burden, response and prognostic measures: AI detects/contours lesions, applies protocol thresholds and outputs MTV/TMTV, with expert or semi-automated reference comparison in FDG-PET/CT lymphoma evidence [55,452,461,473,474]. Keep objective, bottleneck, technique, endpoint, comparator, cohort and uncertainty separate; held-out evaluation should test bias, overfitting and interpretability [222].

In Quantitative Analysis, MTV is metabolic tumour volume in mL (or cm3), while TMTV is total volume in mL obtained by summing lesion MTVs; preserve the convention (for example, 41% of SUVmax or SUV≥4.0) and use ΔTMTV=100×(TMTV1−TMTV0)/TMTV0 for longitudinal response, with TMTV0 as denominator [250,475,263]. Because manual delineation is tedious and takes around 15 min per study, an end-to-end deep-learning aTMTV/CNN pipeline segments FDG-PET/CT lesions into masks and sums their volumes automatically, accelerating quantification and supporting clinical drug evaluation [263,452,398,475].

### 4. Radiotherapy planning

**The objective is consistent target definition.** AI helps radiotherapy planning most directly by producing editable PET-based tumor contours. Gross tumor volume (GTV) denotes the macroscopic tumor volume identified for planning; in head-and-neck cancer, this can include the primary tumor, GTVp, and involved nodal disease, GTVn. PET contributes metabolic information while CT contributes anatomical context. [44]

**The strongest result approaches expert variability.** A 2024 clinical evaluation used 1,220 ^18F-FDG PET/CT scans from 1,190 head-and-neck cancer patients. Training and validation involved 805 patients with 835 scans; independent test cohorts contained 196, 64, and 125 patients. On the 196-scan method-comparison set, nnU-Net achieved the highest mean Dice, 0.80, with a 95% confidence interval of 0.77–0.86. [9]

| Evaluated architecture | Main technical design | Role in GTV delineation |
|---|---|---|
| nnU-Net | Self-configuring U-Net pipeline | Adapt preprocessing and segmentation to the dataset |
| DeepMedic | Dual-resolution convolutional pathways | Combine local detail and wider context |
| InnerEye | Residual/dilated 3D U-Net | Preserve contextual information through convolution |
| Swin-UNETR | Shifted-window attention with convolutional decoder | Model longer-range spatial relationships |
| Tureckova | Attention-gated V-Net extension | Focus segmentation on relevant structures |

**Architectural novelty did not determine performance.** All five methods used two-channel PET/CT inputs and PET GTV references. nnU-Net’s mean Dice exceeded DeepMedic, InnerEye, and Swin-UNETR in that experiment; the difference from Tureckova was not statistically significant. This favors a well-configured convolutional baseline over assuming that a transformer must perform best. [9]

**Expert disagreement provides the meaningful benchmark.** In 64 independent internal scans, AI-to-expert Dice was 0.78 versus expert-to-expert Dice of 0.82. The mean difference was 0.04, with a 95% confidence interval from −0.01 to 0.09 and P = 0.12. The study therefore found no evidence of a difference in this comparison; that result is more informative than comparing AI with an assumed perfectly reproducible human contour. [9]

**External agreement was maintained in that evaluation.** The study’s internal-versus-external comparison reported Dice of 0.80 versus 0.81, respectively, with the external cohort containing 125 patients. Derived tumor-volume and uptake biomarkers also showed clinically interpretable agreement with expert measurements. These outcomes support contour initialization and automated biomarker extraction. [9]

**Institutional contouring style changes transferability.** Wang et al. evaluated a different workflow using Retina U-Net localization followed by regular U-Net segmentation, alongside end-to-end Retina U-Net alternatives. The baseline regular U-Net achieved averaged cross-validation Dice of 0.74, with average and 95th-percentile boundary distances of 2.6 and 8.5 mm. Direct external application produced substantially lower overlap. [44]

| External institution | Baseline regular U-Net Dice | Best facility-adapted model | Adapted Dice |
|---|---:|---|---:|
| MAASTRO | 0.60 | Regular U-Net | 0.70 |
| CRO | 0.63 | 2D Retina U-Net | 0.76 |
| BERLIN | 0.52 | 2D Retina U-Net | 0.67 |

**Adaptation partly learns local decisions.** These columns compare the baseline regular U-Net with the best adapted architecture at each institution, rather than identical-model gains in every row. Facility-specific transfer learning improved overlap, consistent with differences in acquisition, anatomy, and contouring conventions. The study also observed that high-SUV regions could lie outside a GTV, while low-SUV regions could contain involved nodes; target definition is therefore not simply uptake thresholding. [44]

**Contour precision is the supported proxy.** Dice and boundary distances measure agreement with reference contours, not delivered target coverage, dose conformity, normal-organ exposure, toxicity, or tumor control. In the clinical evaluation, nuclear-medicine PET GTVs were passed to radiation oncologists or radiologists to guide final GTV definition. That workflow preserves the distinction between metabolic delineation and the final treatment decision. [9]

**The practical advantage is structured assistance.** AI can supply a consistent first contour, identify disagreements for review, and extract volume-based biomarkers without repeated manual work. A clinically meaningful efficiency gain depends on how much editing is needed, not merely how quickly a network produces its initial mask.

**Radiotherapy judgment supports editable contours.** PET/CT deep learning can approach expert contour agreement in defined head-and-neck settings, while local contour conventions and clinical context remain essential to converting that contour into a treatment plan.

### 5. Dosimetry

**The objective is personalized internal dose.** AI dosimetry predicts voxel-level dose rates or absorbed doses from a patient’s activity distribution, anatomy, tissue properties, and radiopharmaceutical kinetics. The clearest computational example is Deep-dose: a 3D CNN generated a dose-rate map in 3.6 minutes, compared with 235.2 hours for the study’s direct Monte Carlo implementation. [3]

**Dose requires more than uptake intensity.** Internal absorbed dose depends on how much radioactive material is present, where it is located, how long it remains, and how emitted energy is deposited in surrounding tissues. PET supplies quantitative activity information; CT supplies patient anatomy and tissue-density information. Absorbed dose is measured in gray, Gy, equivalent to joules per kilogram; dose rate can be expressed in Gy per second.

**Calculation and prediction are distinct tasks.** A model can accelerate dose calculation from a measured activity distribution, or forecast later therapeutic dose from earlier diagnostic imaging. The first mainly approximates energy transport; the second must additionally infer time-dependent pharmacokinetics and differences between diagnostic and therapeutic radiopharmaceuticals.

| Dosimetry approach | Activity representation | Treatment of tissue/anatomy | Principal role |
|---|---|---|---|
| Organ-based MIRD/OLINDA | Organ-level activity | Reference-organ assumptions | Practical organ-dose estimation |
| Voxel S-value convolution | Voxel activity distribution | Usually predefined medium kernel | Efficient spatial dose calculation |
| Direct Monte Carlo | Patient-specific voxel source | Explicit particle transport through patient media | Physics-based dose reference |
| Deep-dose CNN | PET/CT patches | Learned activity–medium relationship | Fast voxel dose-rate prediction |
| Learned S-value kernels | Patient activity plus density information | Medium-specific learned kernels | Physics-structured voxel calculation |

**The MIRD framework clarifies the mechanism.** In Medical Internal Radiation Dose, or MIRD, calculations, time-integrated source activity is combined with S-values describing absorbed dose per unit time-integrated activity. A voxel S-value kernel expresses how activity in one voxel contributes dose to neighboring voxels. Integrating dose rate over time converts a sequence of dose-rate maps into absorbed dose. [3]

**Deep-dose learns local energy deposition.** Lee et al. trained a supervised patch-based 3D U-Net using PET and CT patches as inputs and direct Monte Carlo dose-rate maps as targets. Patches measured 48 × 48 × 24 voxels, chosen to include surrounding sources and media relevant to dose deposition. The dataset comprised ten subjects with dynamic ^68Ga-NOTA-RGD PET/CT at eight time points, evaluated through fivefold patient-level cross-validation. [3]

**Density information explains the advantage.** A homogeneous kernel can work reasonably in soft tissue but misrepresent dose in lung, bone, air cavities, and tissue interfaces. The CNN received CT information alongside PET activity, allowing it to learn how heterogeneous media change deposited energy. Whole-body voxel dose-rate error was 2.54% ± 2.09%, compared with 9.97% ± 1.79% for conventional voxel S-value convolution. [3]

| Method in Deep-dose evaluation | Average organ absorbed-dose error versus Monte Carlo |
|---|---:|
| Deep-dose CNN | 1.07% |
| Voxel S-value convolution | 9.43% |
| Organ-based OLINDA/EXM | 34.22% |

**Time integration preserved organ-dose agreement.** The study integrated predicted dose-rate maps over measured time points and extrapolated the tail after the final 62-minute acquisition. The CNN’s average organ absorbed-dose error was 1.07%, compared with 9.43% and 34.22% for the two alternatives. The improvement therefore concerned both local dose-rate maps and the subsequent organ-dose calculation. [3]

**Inference speed changes practical feasibility.** The reported 235.2-hour versus 3.6-minute runtimes correspond to a calculated ratio of 3,920:1, using `235.2 × 60 / 3.6`. This is the study’s implementation-level comparison, not a universal hardware-normalized advantage. Its practical significance is that a learned transport surrogate can make repeated patient-specific calculations much more accessible. [3]

**Learned kernels retain more physical structure.** Akhavanallaf et al. used a deep neural network to predict medium-specific S-value kernels instead of applying one homogeneous soft-tissue kernel everywhere. Those kernels were then used within voxel-level MIRD calculation with patient activity and density information. This places learning inside a physically interpretable calculation rather than asking a network to generate the entire dose map without such structure. [45]

| Kernel approach in the heterogeneous case | Mean absolute relative dose error versus Monte Carlo |
|---|---:|
| DNN-predicted medium-specific kernels | 2.6% ± 0.94% |
| Multiple voxel S-value approach | 3.0% ± 3.5% |
| Single soft-tissue kernel | 49% ± 68% |

**The comparison isolates medium mismatch.** These results came from a lung-adenocarcinoma case with a pulmonary tumor of approximately 120 g and evaluated regions including heart, bone, lung, and tumor. The large error of the single-kernel approach illustrates the penalty from a poor medium assumption; the close DNN and multiple-kernel results also show that much of the gain came from respecting heterogeneous physics. [45]

**The additional prediction step costs time.** Kernel inference required approximately 0.7 hours, followed by approximately 0.1 hours for convolution: a calculated total of 0.8 hours, or 48 minutes. The authors reported total time below 0.1% of direct Monte Carlo time. These timings describe a different workflow from Deep-dose and should not be used to rank the architectures independently of their calculation settings. [45]

**Pretherapy forecasting adds kinetic modeling.** Kassar et al.’s 28 March 2024 study combined a conditional GAN with a 3D U-Net generator and physiologically based pharmacokinetic (PBPK) regularization. It predicted post-therapy voxelwise dose from pretherapy ^68Ga-PSMA-11 PET for ^177Lu-PSMA-I&T therapy. PBPK information constrained the learned relationship between early imaging and subsequent radiopharmaceutical distribution. [46]

**Its reported benefit was physics-guided prediction.** The proof of concept used 120 virtual patients, with 100 for training and 20 held out for testing. In kidneys, spleen, liver, and salivary glands, the PBPK-adapted model improved dose prediction and dose–volume-histogram agreement relative to pure deep learning. This demonstrates the value of kinetic constraints when the desired output is future therapeutic dose, rather than dose associated with the activity already measured by PET. [46]

**Dosimetry judgment favors constrained acceleration.** AI can dramatically accelerate individualized dose calculations and make heterogeneous tissue modeling more practical; forecasting therapeutic dose is the more demanding problem because it must preserve both radiation-transport physics and patient-specific kinetics.

**Additional documented evidence**

**Objective and workflow**

Dosimetry links quantitative PET biodistribution to patient-specific internal absorbed dose. It estimates tumor and normal-tissue dose in **Gy**, anticipates biological effects, and individualizes activity instead of accepting fixed-activity under- or overdosing [200]. Calibrated activity, anatomy and serial uptake become activity or dose-rate curves; integration yields time-integrated activity coefficients (TIACs), after which MIRD dose factors, dose-point kernels or Monte Carlo produce organ, lesion or voxel dose (an organ-level coefficient may be reported in **mGy/MBq**) [498,496]. AI targets segmentation and registration, sparse-time kinetic/TIA prediction, Monte Carlo approximation and dose-map generation; fixed activity, maximum-tolerated absorbed dose (MTAD) and prescribed tumor-absorbed dose (PTAD) remain distinct prescription logics [200].

**AI prediction and calculation**

The dated examples below are **2023 studies summarized in a later review [89]**; the review itself is outside the 2024-03-31 cutoff. Reported AI PET-dosimetry results include:

- **Renal and tumor prediction:** Peterson et al. used pretherapy **68Ga-DOTATATE PET plus biomarkers** to predict first-cycle **177Lu-DOTATATE** renal dose; PET-only MAPE was **18.0%**, falling to **17.3%** with estimated glomerular filtration rate under leave-one-out validation. A related study used pretherapy **68Ga-DOTA-TATE** and biomarkers for **177Lu-PRRT** tumor-dose prediction [89].
- **PSMA and lesion prediction:** Yazdani et al. used **68Ga-PSMA PET/CT radiomics and clinical features** to predict **177Lu-PSMA-617** kidney and lesion dose in retrospective 20-patient cohorts: kidney RMSE **0.11 Gy/GBq**, R² **0.87**; lesion RMSE **1.04 Gy/GBq**, R² **0.77**, all under leave-one-out validation with no external test. A random forest trained on **25 patients/90 lesions** achieved R² **0.64** and MAE **0.73 Gy/GBq** under nested tenfold validation, also without an external cohort [89].
- **Sparse-time prediction:** Georgiou et al. trained a feed-forward neural network in **70 patients** to estimate permissible **¹³¹I** activity from 4-, 24- and 48-hour imaging/blood data; in **13** test patients versus five-time-point MIRD, the paired result was **p = 0.351**, 95% CI **−21.05 to 8.08 mCi**, but **1/13** predictions differed by more than 10%. An MLP using one oblique view produced organ differences of **−14.8% to +11.2%** versus GATE Monte Carlo in an external **23-patient** cohort; aggregate MAE/RMSE was not reported [89].
- **Dose maps and workflow acceleration:** A hybrid transformer produced **¹⁷⁷Lu-DOTATATE** voxel maps in **22 patients/50 sessions**, with patient-grouped fivefold validation and voxel relative absolute error **5.28 ± 1.32** versus Monte Carlo. Registration plus deep learning reduced TIA RMSE by about **27% for kidney** and **33% for tumor** versus Elastix in an external 14-patient test, but no dose-decision test followed. A deep-learning segmentation/dose workflow reduced total time from **54.3 to 47.0 min** in 23 patients (**p = 0.014**); its contour was staff-corrected. Deep-dose uses a CNN to map PET/CT to voxel dose instead of slow Monte Carlo, but no performance value is reported in the cited passage [342,336]. Other named approaches include random forests, radiodosiomics, transformers and Swin UNETR; their radionuclides, inputs and reference endpoints differ [89].

**Limits and evidence boundaries**

These results support technical prediction or acceleration, not proven outcome benefit or autonomous activity adaptation. Internal or leave-one-out validation does not establish generalization across tracers, scanners, reconstructions, organs or treatment settings; replacement requires uncertainty, out-of-domain, agreement and decision-threshold testing plus prospective comparison [89]. Conventional RPT uncertainty is **10–15% for major organs** and higher for small lesions because activity assay, volume, sampling, TIAC and dose-model errors propagate [200]. PET dose also depends on isotope, radioligand, biodistribution, excretion and patient factors, while clinical-trial calibration and pharmacokinetic coordination remain burdens [496,29]. FAPI PET/CT provides dosimetry context but no AI result [234]. Historical ¹³¹I SPECT/Monte Carlo work and later CT or EPID AI results are modality-specific, not PET internal-dosimetry evidence [337,13,16].

AI dosimetry targets patient-specific absorbed-dose maps. Published 25 January 2024, a hybrid transformer/UNETR learned the MC−MSV correction for [177Lu]Lu-DOTATATE: registered multi-time-point SPECT activity plus CT density produced voxel TACs, integrated to TIA; adding the correction to MSV produced MC-like maps [137]. In 22 patients/50 sessions, DL versus MC had voxel RAE 5.28±1.32 (MSV 5.54±1.40; SSV 7.80±3.02), lesion-dose error 1.15±2.50%, and 99.0±1.2% Gamma pass; single-bed generation was 3 s versus ~2 days [137]. This SPECT/CT result is not PET validation. PET dosimetry remains sensitive to registration, calibration, segmentation, TAC fitting and isotope effects; small rigid misregistration can alter dose by up to 90% [246].

Dosimetry: 3D U-Net CNN maps PET/CT to voxel dose-rate; 2019 error 2.54±2.09% vs Monte Carlo [139].

Dosimetry (2019): PET U-Net error 2.54%±2.09% vs VSV 9.97%±1.79%; 3.6 min vs 235.2 h, hardware differed [121]

rejected: citation_outside_operands; reason: citation_outside_operands; allowed numbers: 10 patients, 2008, 10%–15%, Lutetium-177-PSMA, "", 30% increase, 2024, June 2024; June 1, 2024, 50 sessions of 22 patients, ~1.2 h each, 23 March 2024; allowed citations: [235][236][237][238][239][240][121][241][135][242][243][137][138][139][140][144][76][152][81][87][245][89][247][95][248][98][191][193][197][199][249][200][250][251][252][201][253][101]; allowed entities: Dosimetry.

Dosimetry links quantitative three-dimensional imaging and activity to individualized treatment adaptation: modelled biodistribution or quantitative PET/SPECT feeds MIRD, voxel-S-value, dose-kernel or Monte Carlo calculation of patient-specific internal dose. AI addresses manual segmentation and Monte Carlo’s lengthy computation, but only approximates or accelerates it under trained and validated conditions; reported uncertainty is 10%–15% for major organs and higher for small lesions, arising from activity assay, volume/mass, time-dependent activity and time-integrated activity [244][238][236][89][200][137].

### 6. Radiomics and radiogenomics

**The objective is biological decision support.** PET radiomics converts images into quantitative features associated with diagnosis, treatment response, and prognosis. Radiogenomics links those imaging phenotypes to genetic or molecular information. A strong PET-specific example is Mu et al.’s deep-learning EGFR score: external-test AUC was 0.81 and accuracy 78.5%, compared with AUC 0.50 for SUVmax alone. [10]

**Three relationships must remain separate.** An imaging model may predict a molecular label, such as an epidermal growth factor receptor (EGFR) mutation, without receiving genetic information during inference. Alternatively, a prognostic model may jointly use imaging features and a patient’s measured mutation status. A third model may combine PET with clinical variables but no genetic data; that is multimodal prediction, not automatically radiogenomics.

| Modeling relationship | Inputs when used | Output | Representative example |
|---|---|---|---|
| Imaging-to-genotype inference | PET/CT appearance | Mutation probability | EGFR-DLS |
| Joint radiogenomic prediction | PET/CT features and measured EGFR status | Outcome-risk classification | Lung-cancer post-SBRT model |
| PET–clinical fusion | Whole-body PET and clinical variables | Survival prediction | ResNet3D–MLP model |

**Classical radiomics uses explicit features.** Common inputs include SUV statistics, MTV, shape, uptake histograms, spatial distribution, texture matrices, and wavelet-filtered features. A pipeline usually segments a tumor, standardizes image sampling and intensity handling, extracts many features, selects a smaller subset, and fits a classifier or survival model. Least absolute shrinkage and selection operator (LASSO) selection, support vector machines (SVMs), random forests, logistic models, and Cox proportional-hazards models are common choices. [47]

**Deep radiomics learns its representation.** CNNs can replace handcrafted feature extraction with image-derived representations learned for the prediction task. They can incorporate surrounding tissue without requiring an exact tumor boundary, although a tumor-containing region may still need to be selected. This changes the dependence from manually defined texture formulas toward training data, architecture, and the definition of the prediction target.

**EGFR-DLS fused metabolism and anatomy.** Mu et al.’s small residual CNN processed PET, CT, and their fused image as a three-channel input. Radiologists selected regions containing the tumor and surrounding tissue; slice-level outputs were averaged into a patient-level EGFR deep-learning score. Training and internal validation included 429 and 187 patients, with independent external evaluation and additional treatment-outcome cohorts. [10]

| EGFR-DLS evaluation cohort | EGFR-DLS AUC | EGFR-DLS accuracy | SUVmax-only AUC |
|---|---:|---:|---:|
| Training | 0.86 | 81.1% | 0.62 |
| Internal validation | 0.83 | 82.8% | 0.69 |
| External test | 0.81 | 78.5% | 0.50 |

**External discrimination exceeded simple uptake.** The score’s external AUC of 0.81 indicates useful but imperfect mutation discrimination. Adding histology and smoking information increased external AUC to 0.84 and accuracy to 80.0%, but the improvement over EGFR-DLS alone was not statistically significant. This is an important example of complementary information producing a numerical gain without establishing a decisive gain over the imaging model. [10]

**Reproducibility was measured explicitly.** Across regions selected by three radiologists for 73 validation cases, EGFR-DLS ICC was 0.91, with a 95% confidence interval of 0.87–0.94. The network’s 256 learned features also formed clusters associated with mutation status and clinical phenotype. These analyses support stability and biological association, while the model remained dependent on selecting a region that actually contained tumor and relevant surrounding tissue. [10]

**Molecular labels can supervise conventional learning.** Shiri et al. evaluated PET, low-dose CT, and contrast-enhanced diagnostic CT radiomics against polymerase-chain-reaction-defined EGFR and KRAS mutation status, using an independent validation set of 68 patients. For EGFR, multivariate PET radiomics reached AUC 0.82 versus 0.69 for SUVpeak. The best reported KRAS result came from CT rather than PET, an important modality distinction. [48]

| Prediction strategy | EGFR AUC | KRAS AUC | Relevant imaging basis |
|---|---:|---:|---|
| Conventional PET metric | 0.69 | 0.55 | SUVpeak for EGFR; MTV for KRAS |
| Best univariate radiomic feature | 0.75 | 0.71 | PET for EGFR; diagnostic CT for KRAS |
| Best multivariate machine learning | 0.82 | 0.83 | PET for EGFR; CT for KRAS |

**Deep learning is not mandatory.** A 2023 PET/CT radiomics preprint involving 34 histology-confirmed non-small-cell lung cancer (NSCLC) patients extracted 2,205 features and compared nine machine-learning methods with different feature-selection strategies. Its best reported neural-network AUC was close to those of ridge regression and random forest, providing another reason not to assume that model depth alone determines performance. [49]

| Best reported model | EGFR-prediction AUC |
|---|---:|
| Ridge regression | 0.826 |
| Random forest | 0.823 |
| Neural network | 0.821 |

**Clinical covariates can improve learned scores.** A 2022 study compared handcrafted PET/CT radiomics, a two-channel 3D CNN, and a hybrid model combining the deep-learning score with smoking information. It extracted 4,306 radiomic features and 2,048 deep features per patient before model construction. The hybrid’s validation accuracy was 0.82 versus 0.72 for the deep-learning model—a 10-percentage-point difference. [50]

| Model in the 2022 comparison | Principal representation | Validation AUC |
|---|---|---:|
| Radiomics model | Handcrafted PET/CT features | 0.68 |
| Deep-learning model | Learned 3D CNN representation | 0.79 |
| Hybrid model | Deep-learning score plus smoking | 0.85 |

**Joint radiogenomics uses measured genetics.** A 2023 *Life* study explicitly combined PET/CT radiomic features with clinical EGFR status to classify progression-free-survival risk after stereotactic body radiotherapy (SBRT). It included 123 lung-cancer patients, extracted 2,042 radiomic features, and retained five through LASSO. This was outcome prediction using genetic information, not prediction of EGFR mutation status itself. [51]

**Integration gains differ by context.** A 2019 radiogenomics review summarized a general lung-imaging survival example in which combining radiomics and genomics improved AUC from 0.78 for either alone to 0.84. That example illustrates the integration principle rather than supplying a PET-specific benchmark. The PET/CT SBRT study provides the directly relevant imaging-plus-genetic comparison. [47][51]

| Information used | General lung-imaging survival AUC | PET/CT SBRT risk AUC | SBRT sensitivity | SBRT specificity |
|---|---:|---:|---:|---:|
| Imaging features alone | 0.78 | 0.84 | 0.71 | 0.82 |
| Genetic information alone | 0.78 | 0.67 | 0.52 | 0.75 |
| Imaging plus genetic information | 0.84 | 0.86 | 0.71 | 0.83 |

**The PET-specific increment was small.** In the SBRT study, adding EGFR status increased AUC from 0.84 to 0.86, but that difference was not statistically significant. Sensitivity remained 0.71, while specificity increased from 0.82 to 0.83. The result supports complementary information, especially relative to the EGFR-only clinical model, without establishing that genetic integration invariably produces a large improvement over radiomics. [51]

**Prognosis requires time-to-event evaluation.** For survival modeling, the concordance index, or C-index, measures how well predicted risk orders comparable patients’ outcomes. It is distinct from a binary AUC and does not mean that an individual survival time is known precisely. Cox models and neural survival predictors can use PET features, clinical variables, and molecular information in different combinations.

**A combined nomogram improved survival ordering.** Yang et al.’s 2020 study included 109 patients with EGFR-mutant lung adenocarcinoma, split into 77 training and 32 validation cases. LASSO selected ten radiomic features from 1,672 candidates; the resulting score was combined with independent risk factors, including distant metastasis and MTV, in a Cox nomogram. [52]

| Prognostic model | Training C-index | Validation C-index |
|---|---:|---:|
| Radiomics alone | 0.819 | 0.737 |
| Clinical model | 0.694 | 0.729 |
| Combined radiomics nomogram | 0.840 | 0.803 |

**The combined model retained more information.** The validation C-index of 0.803 exceeded the clinical and radiomics-only values in that dataset. Mechanistically, imaging can describe disease burden and heterogeneity, while clinical and molecular variables describe other components of risk; fusion is useful when those inputs provide complementary rather than redundant information. [52]

**Treatment association can reverse direction.** EGFR-DLS was positively associated with benefit in 67 patients treated with EGFR tyrosine kinase inhibitors (TKIs): a score of at least 0.5 was associated with longer progression-free survival, with hazard ratio 0.24 versus lower scores. In 149 patients receiving immune checkpoint inhibitors (ICIs), lower scores were associated with longer median progression-free survival—12.00 versus 4.20 months—with a reported hazard ratio of 2.33 for the higher-risk comparison. [10]

**The reversal is biologically informative.** A score associated with EGFR-related phenotype may identify different treatment-response patterns, rather than merely labeling every high-score patient as having a better general prognosis. These observational associations support decision-support research and treatment stratification; they do not establish that selecting treatment from the AI score causes better survival or replaces tissue genotyping.

**PET–clinical fusion is broader than radiogenomics.** A 2023 study of 2,687 NSCLC patients combined whole-body FDG PET features from ResNet3D-34 with clinical data processed by an MLP. The three-dimensional representation preserved spatial context beyond a two-dimensional maximum-intensity projection. Because genetic variables were not part of the stated fusion, this is best described as multimodal prognostic AI. [53]

| Survival model | C-index | Mean absolute survival-time error |
|---|---:|---:|
| Clinical Cox model | 0.747 | 583 days |
| PET-only ResNet3D | 0.749 | 405 days |
| PET–clinical fusion | 0.756 | 399 days |

**Incremental benefit should remain proportional.** Fusion improved C-index by 0.007 over PET alone and reduced mean absolute error by six days in that comparison. Those are useful measured increments, but much smaller than the improvement over the clinical model’s survival-time error. The reader should therefore ask which comparator represents the actual clinical alternative, rather than interpreting “multimodal” as synonymous with a large gain. [53]

**Feature stability links both report parts.** Reconstruction, denoising, motion correction, and segmentation change the numerical features subsequently used by a radiomic model. In a ^90Y PET/CT robustness study, only 15 of 46 evaluated features passed a reproducibility screen using mean concordance correlation above 0.85 across repeated phantom acquisitions and reconstruction settings. Thus, improving an upstream image is not automatically neutral for a downstream predictor trained on another processing chain. [54]

**Radiogenomics judgment favors complementary evidence.** PET features can support mutation inference and prognosis, while measured genetic information can improve selected outcome models; the appropriate clinical role is additional biological evidence, not a substitute for molecular testing or a causal treatment recommendation.

**Evidence spans different measurement bases.** Reported effects depend on tracer, scanner, count level, reference image, contour convention, and validation design; detector and motion demonstrations often use simulations, while key dosimetry examples involve ten subjects, a single ^18F proof-of-concept case, or virtual patients, and runtime comparisons use different computing environments. [3][45] Radiogenomic evidence is commonly retrospective, and one 2022 report states 194 total cases despite subsets summing to 195. [50] Postsurgical GTV cases also reduced AI Dice to 0.46 and expert Dice to 0.58. [9] The decisive conditions for stronger claims about beat-resolved cardiac correction and radiotherapy benefit beyond contour overlap are, respectively, patient validation of within-heartbeat motion and independent plan-level target coverage, normal-tissue dose, or clinical outcomes. Arithmetic-derived changes are identified as calculations; the remaining numerical effects are reported study results.

**The practical conclusion is targeted integration.** By early 2024, AI’s clearest value in PET was improving defined measurements and automating bounded tasks while preserving an appropriate physical or clinical reference. The most useful systems connect those gains across the workflow: better event information, trustworthy images, correctly identified disease, reproducible measurements, and clinically reviewed decisions.

**Additional documented evidence**

| Entity | objective | problem or bottleneck | main AI techniques | technical mechanism | specific effects or advantages | limitations and uncertainty | study-effects time series |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Image Segmentation | no evidence found | no evidence found | A physics-guided modular deep-learning-based…[99] | A physics-guided modular deep-learning-based…[99] | no evidence found | no evidence found | no evidence found |
| Lesion Detection and Classification | AI in PET-CT supports lesion detection, segmentation…[174] | no evidence found | no evidence found | AI in PET-CT supports lesion detection, segmentation…[174] | no evidence found | no evidence found | no evidence found |
| Quantitative Analysis | no evidence found | no evidence found | no evidence found | no evidence found | The CNN took 1.5–2 minutes per scan for most patients…[192] | Manual verification and occasional correction required[182] | no evidence found |
| Radiotherapy Planning | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Dosimetry | Deep-dose uses a deep convolutional neural network…[166] | Deep-dose uses a deep convolutional neural network…[166] | The source also lists Monte Carlo, dose-point-kernel…[154] | The source also lists Monte Carlo, dose-point-kernel…[154] | Lesion-volume Gamma pass rates were 96.8 ± 6% for SSV…[137] | The source also lists Monte Carlo, dose-point-kernel…[154] | no evidence found |
| Radiomics and Radiogenomics | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found | no evidence found |
| Quantitative analysis | no evidence found | no evidence found | no evidence found | no evidence found | The CNN took 1.5–2 minutes per scan for most patients…[192] | no evidence found | no evidence found |

**Part Two coverage matrix**

| Clinical application | Objective and problem solved | Main bottleneck | Main AI techniques | Mechanism and workflow role | Reported effects or advantages | Limitations and evidence status |
|---|---|---|---|---|---|---|
| **Image Segmentation** | Delineate a lesion, tumor, organ or other ROI/VOI so it can be interpreted, measured and used for diagnosis or response assessment. PET-CT AI detects and segments abnormal metabolic regions and supports reproducible SUV measurement [171]. | Manual contours are laborious and observer-dependent; poor contrast and noise weaken threshold or edge methods. Respiratory motion can additionally degrade PET quality and tumor-contour precision [156]†[181]‡. | CNNs, encoder-decoder networks, U-Net/3D U-Net and Mask R-CNN; semi-automatic thresholding, edge or region methods and k-means clustering [156]†[157]. A cited PET study also describes physics-guided modular deep learning [173]. | The image is transformed into a pixel/voxel mask: an encoder extracts features, a decoder restores spatial resolution, and skip connections preserve detail. A 2014 prostate PET/MR boundary example used a 1.5-T scanner, TE **1.11 ms**, TR **20 ms** and flip angle **20**, then FCM, active contours and shape analysis to generate a three-class attenuation map; **15** pelvic images were compared with expert manual segmentation [106]. | AI is reported qualitatively to expedite interpretation, reduce workload and improve reproducibility [171]. Validation should compare prediction masks with expert ground truth: Dice \(=2|A∩B|/(|A|+|B|)\), range 0–1; IoU \(=|A∩B|/|A∪B|\); and boundary distances such as Hausdorff distance in pixels or millimetres when voxel size is known [107]. No PET-specific Dice, contour-time or volume-agreement value is reported in the current cards. | Generalizability depends on tracer, scanner, reconstruction, motion, annotation protocol and disease. Deep models need labelled data and may fail on domains unlike training data [156]†. The PET/MR attenuation-map method remained under development and required further comparison with CT-derived maps [106]. |
| **Lesion Detection and Classification** | Identify abnormal metabolic patterns, rank lesion candidates and assist physicians in deciding whether findings require further assessment. The supplied PET evidence directly supports detection and assessment, but not a pathology-validated benign-versus-malignant result [171]. | Small FDG-positive nodules, variable reconstructions and the volume of whole-body images can increase interpretation burden. | AI pattern recognition, candidate detection and lesion segmentation; the cited overview names lung-lesion detection, small FDG-positive nodule detection and bone-marrow assessment in multiple myeloma, but does not specify a single architecture [171]. | PET-CT input is mapped to abnormal-metabolism candidates and, where available, a lesion mask; the output supports rather than replaces radiologist review [171]. Named examples include Borrelli et al. (2021) for lung lesions, Schwyzer et al. (2020) for small FDG-positive lung nodules and Sachpekidis et al. (2023) for marrow involvement in myeloma [171]. | Automated detection and segmentation can expedite interpretation, focus the radiologist on nuanced analysis and improve reproducibility of lesion measurements [171]. Sensitivity, specificity, AUC, false-positive rate, reader-time change and benign/malignant accuracy are **not reported** in the cards. | The available evidence does not provide a consistent pathology or follow-up reference standard, patient/lesion denominator, or external-validation result. Therefore, detection benefit must not be presented as proof of autonomous benign/malignant classification. |
| **Quantitative Analysis** | Convert AI-derived lesion contours into reproducible PET measurements; segmentation supports SUV-based diagnosis and treatment-response assessment [171]. | Manual delineation, threshold selection and motion can change measured tumor burden. A motion-corrected reconstruction study in **2-[¹⁸F]FDG** and **[⁶⁸Ga]Ga-DOTA-NOC** PET-CT evaluated image quality and tumor quantification, but it does not establish an AI MTV/TMTV result [171]. | AI lesion detection and segmentation; FCM, active contours and shape analysis are relevant only as a PET/MR attenuation-map segmentation boundary example [106]. | The intended chain is PET image → lesion mask → SUV or volume metric. The current cards do not state the tracer-specific threshold, lesion-inclusion rule, aggregation method or unit needed to calculate **MTV** or **TMTV**. | The supported advantage is improved measurement reproducibility and lesion characterization through more consistent segmentation [171]. Numerical MTV/TMTV agreement, processing-time reduction, robustness, threshold comparison and longitudinal effect are **not reported** in this source-group part. | MTV/TMTV values cannot be compared without preserving tracer, threshold, lesion definition, volume unit and aggregation convention. The available tumor-quantification citation is technical context rather than direct evidence for automated MTV/TMTV calculation. |
| **Radiotherapy Planning** | Requested objective: use PET information to delineate GTV and support plan formulation. **Evidence status: not reported in the source-group cards available for this part.** | Not reported here. | Not reported here. | Not reported here. | GTV agreement, target coverage, organ-at-risk dose, plan quality and planning time are not reported here. | The dedicated radiotherapy-planning subsection must supply PET-specific evidence and preserve tracer, tumor site, reference contour and prescription context. |
| **Dosimetry** | Requested objective: predict or calculate patient-specific internal absorbed dose. **Evidence status: not reported in the source-group cards available for this part.** | Not reported here. | Not reported here. | Not reported here. | Dose error, dose agreement, uncertainty, acquisition burden and computation-time effects are not reported here. | The dedicated dosimetry subsection must specify radionuclide, activity-time data, organ or tumour target, dose unit and reference calculation. |
| **Radiomics and Radiogenomics** | Extract quantitative PET phenotype for diagnostic, prognostic or response prediction and, where available, relate it to molecular or genetic status. Radiomics addresses heterogeneity that is not reliably captured by visual interpretation [156]†. | High dimensionality, data scarcity, confounding, class imbalance, overfitting, scanner/protocol/reconstruction variation, feature instability, limited interpretability and weak external validation [156]†[181]‡. | Hand-crafted first-order intensity, shape and texture features; deep radiomics/CNNs; end-to-end deep learning; filter, wrapper, LASSO or PCA selection; supervised classification/regression and unsupervised clustering [156]†. PET-radiogenomic survey entries use SUV and manual segmentation, including breast cohorts of **36** and **18** and lung PET/CT cohorts of **138** and **355** [206]. | ROI/VOI → feature extraction → feature selection or regularization → diagnostic, prognostic or response model. The cards establish PET radiomic modelling and identify radiogenomic examples, but do not specify a genetic assay, fusion architecture or validated PET imaging-genetic relationship in this evidence slice. | Earlier examples identified in the cards include **⁶⁸Ga-DOTA-TOC PET/CT** feature sensitivity to segmentation/discretization and **2023 Tau-PET** classification of Alzheimer disease versus mild cognitive impairment [156]†. A later, outside-cutoff study (published **7 April 2025**) used **1,502 features per patient** in a four-centre NSCLC cohort of **323 patients**—**245 ADC** and **78 SCC**—with MRMR selection, RF/LDA/logistic-regression/SVM models and 5-fold cross-validation repeated five times [181]‡. | The 2025 study is outside the report cutoff. Its RF harmonization/oversampling validation AUROC was **0.712–0.737** versus **0.608** for the no-harmonization/no-oversampling baseline, with G-mean **0.573–0.626** versus **0.398**; all **29/29** combinations improved both measures, but differences were not statistically significant [181]‡. In cross-centre testing, ComBat gave AUROC **0.728 ± 0.037** versus **0.674 ± 0.066**, G-mean **0.644 ± 0.054** versus **0.461 ± 0.141**, sensitivity **0.620 ± 0.207** versus **0.414 ± 0.395**, and specificity **0.706 ± 0.168** versus **0.703 ± 0.255** [181]‡. |

**Evidence hierarchy and qualifications**

The general deep-learning taxonomy distinguishes supervised learning with labelled targets, unsupervised learning from unlabelled data, semi-supervised learning and reinforcement learning. Generative families include GANs, whose generator competes with a discriminator, and autoencoders, whose encoder compresses an input and decoder reconstructs it; hybrid models and transfer learning combine or fine-tune these representations [110]. These definitions identify possible techniques, not demonstrated PET clinical benefits.

**Clinical-task coverage matrix: segmentation through planning**

| Entity | Objective and bottleneck | AI techniques and mechanism | Effects, evidence context and limits |
|---|---|---|---|
| **Image Segmentation (e005)** | AI generates automatic or semi-automatic PET ROI, tumour and GTV masks and volume biomarkers; the objective is reproducible delineation despite low PET resolution, noise, heterogeneity, mismatched PET/CT boundaries and motion-related registration error [159]. | PET+CT-to-expert-GTV supervised deep learning included nnU-Net, DeepMedic, InnerEye, Swin-UNETR and Tureckova; other PET/CT methods used SVM, FCM, ANN, ATLAAS, 3-D U-Net/V-Net/W-Net and GANs, with weakly supervised, unsupervised and scarce-label variants [111][113][159]. | Online publication on **22 February 2024** (journal issue April; online evidence precedes the **2024-03-31** cutoff): Danish ¹⁸F-FDG PET/CT, **1,220 scans/1,190 patients, 2014–2019**; nnU-Net DSC **0.80** (95% CI, 0.77–0.86; n=196), AI-versus-expert DSC **0.78 versus 0.82** (n=64), and internal/external DSC **0.80/0.81** (n=125; difference 0.004, 95% CI −0.05–0.04) [111]. Postsurgical inflammation and lymph-node disagreement caused failures; AI DSC fell from **0.78 to 0.46** post-surgery, while mostly Siemens Biograph 64 data and limited interpretability constrain generalization [111]. The abstract and cohort description report training counts of **805 and 835**, respectively [111]. Generic U-Net material is not PET-specific evidence [158]. |
| **Lesion Detection and Classification (e006)** | AI examples address pulmonary-nodule detection, FDG-uptake-region detection/classification and whole-body bone-lesion detection with ⁶⁸Ga-Pentixafor PET/CT [159]. | Named approaches are CNN ensemble false-positive reduction, automatic uptake-region classification and deep-learning lesion detection [159]. | The supplied evidence cites studies from **2016–2018**, but reports no cohort, reference standard, sensitivity, specificity, AUC, false-positive denominator, reader-time effect, physician-facing display or benign/malignant label; benign-versus-malignant performance is therefore **not reported** in this source group [159]. |
| **Quantitative Analysis (e007)** | AI reduces the time and oversight burden of multi-lesion PET measurement [113]. MTV is ¹⁸F-FDG metabolic tumour volume reflecting glycolytic burden; a TMTV value, threshold, unit and lesion-aggregation rule are **not reported** here. | PET/PET-CT data are segmented into tumour or reference ROIs with SVM, ANN, FCM, CNN, deep CNN or CycleGAN, then converted to volume or SUV measurements [113]. A 3-D CNN predicted lymph-node SUV in **2019**; automated liver/blood-pool ROIs were comparable with manual radiologist ROIs in **80 lymphoma patients**; an RSF study used MTVwb among PET inputs in **935 baseline NSCLC scans**. A CycleGAN attenuation-correction example used **25 training and 55 evaluation images** and found no significant AC-versus-DL-AC intensity difference [113]. No numeric AI-versus-reference MTV/TMTV series is supplied. |
| **Radiotherapy Planning (e008)** | AI supplies a PET GTV contour to distinguish malignant from healthy uptake and guide the radiation oncologist’s or radiologist’s final target; the expected advantage is greater consistency and speed, not autonomous plan approval [111][113]. | Inputs include PET, CT, PET/CT and planning CT; methods include SVM, FCM, ANN, coupled 3-D U-Nets, deep CNNs and dense multimodality networks [113]. Reported GTV DSC values were **0.777** for 14 lung-cancer cases using SVM, **0.79±0.06/0.76±0.14/0.73±0.14** for FCM/ANN/SVM in 16 lung-cancer patients, and **0.72** for ATLAAS in 20 oropharyngeal cases after chemotherapy [113]. PET+CT DFCN outperformed single-modality models in 60 NSCLC-SBRT patients; a 22-patient, two-centre HNC CNN study found high expert-contour correlation, and a 250-scan HNC study used 140/35/75 training/validation/test scans [113]. The cutoff-compliant HNC study found AI-to-expert DSC **0.78** versus expert IOV **0.82** (n=64) [111]. Direct plan-dose, target-coverage, organ-at-risk, treatment-adaptation and measured planning-time endpoints were not reported [111][113]. |

**Outside-cutoff evidence, retained only as labelled context:** A **15 July 2025** synthetic PET brain-tumour FSM-ICL study used 1,000 training and 426 test images, reporting segmentation accuracy **92.57%**, precision **95.59%**, error **5.67%** and classification time **572.39 ms**, versus NRAN/DSSE-V-Net/DenseUNet+ accuracies of **62.16%/71.47%/83.93%**; it lacked denominators, uncertainty and external human validation [112]. A **23 August 2024** connected-U-Net study used teacher–student pseudo-PET generation from CT, MSE/consistency/focal/Dice losses and EMA; average Dice was **0.56** versus 0.51/0.50/0.43 for comparator models, while external NSCLC-Rad performance was Dice **0.38±0.32**, IoU **0.29±0.27** and HD95 **42.26±41.20** [114]. Distribution shift and single-tumour preprocessing limited interpretation [114].

- **Image Segmentation:** AI automates PET/CT ROI/GTV masks, separating pathologic/physiologic uptake and reducing manual variation [442,443]. U-Net/CNN, RFN, SVM/FCM/ANN and Dense-Net map PET+CT to contours [60,70]. Cutoff-compliant HNC data (online 22 February 2024): nnU-Net DSC .80 (95% CI .77–.86; *n*=196); AI–expert .78 versus expert IOV .82 (*n*=64; *p*=.12); external DSC .81 [119]. Postsurgical AI DSC fell .78→.46; domain shift limits generalization [70,442,443].

- **Lesion Detection and Classification:** AI detects/localizes subtle lesions; benign/malignant classification is not reported [116]. PAIRE used a 3-D CNN, QURIT a 3-D residual U-Net, with synthetic ground truth [116]. In 56 patients, 114 studies and 565 lesions, Algorithm A sensitivity/precision was 24.5%/9.1% (119/1,182/366 TP/FP/misses), versus B 66.2%/34% (374/724/191); B won 16/22 sites [116]. Synthetic rather than pathology-confirmed lesions, omitted true negatives, low-CNR false positives and approximately 6-mm resolution limit transfer [116].

- **Quantitative Analysis:** AI segments lesions then aggregates voxel volumes for MTV/TMTV, reducing multilesion labor and oversight [60,443]. Through 2024-03-31, no universal threshold/unit or numeric AI–reference result is supplied. RECOMIA’s 2026 example (3-D U-Net; 85% [100/117], 54.8 s; manual 321 versus AI 272 cm³) is outside cutoff [118].

- **Radiotherapy Planning:** PET+CT deep learning, including nnU-Net, supplies GTV contours to separate malignant/physiologic uptake near nodes and organs at risk and support planning [119]. In the 22 February 2024 study, GTV AI–expert DSC was .78 versus expert IOV .82; external DSC was .81 [119]. Plan quality, OAR dose, adaptation and planning time were not reported; CT-only iSeg (30 June 2025) is outside cutoff [115].

Image segmentation: automatic U-Net delineates tumors; Dice 0.80±0.03/232 PET patients [180].

Image Segmentation: AI masks address manual variability/physiologic uptake; CNN/nnU-Net/CRF plus threshold→VOI enables automatic/semi-automatic contours. Breast PET/CT (2022, n=130): sens/spec/Dice/Jaccard=.96/1.00/.94/.89 [161]; DLBCL PARS (2021): Dice/ICC=.65/.68 (research), .48/.61 (routine); manual review [182]. Lesion Detection and Classification: thresholded PET/CT, MIP and atlas inputs feed CNNs labeling foci suspicious/not suspicious for malignancy [182]. Quantitative Analysis: all FDG lesion volumes→TMTV (manual 41% SUVmax; PARS 42% local SUVmax); automatic TMTV predicted PFS/OS (HR 2.1/2.4, 5-y follow-up); correction needed [182].

**Image segmentation:** Automates lymphoma/physiologic-uptake ROIs for MTV/TMTV; manual contours are slow/variable [125]. A 2-D residual U-Net performs CT→PET transfer; TMTV-Net uses multiresolution 3-D U-Nets, soft voting and semi-supervision [184][125]. In 2022, organ Dice (brain/heart/kidney/bladder)=.9524/.9023/.9107/.8809 (50 CTs; expert consensus) [184]; on 8-Feb-2024, subtype DSC (DLBCL/PMBCL/DLBCL/Hodgkin)=.70/.62/.67/.63, overall=.66±.18 (n=518), internal=.68±.12; p<.001 versus nnU-Net/Swin [128][125]. Small lesions, domain shift and label variability persist; TTA DSC=.66±.16 [125].

**Quantitative analysis:** Automates MTV/TMTV burden despite manual time and threshold inconsistency [184][125]. CNN/3-D U-Net masks lesions; 2022 rules used a 41% SUVmax threshold, >1-cm³ retention and <2-cm³ exclusion [184]. In 100 DLBCL patients (2022), MTV r=.9814/.9818 and ICC=.98 versus readers; median time was 5 versus 20 min [184]. TMTV-Net external r=.89, ARE=.43±.54 and AE=157.32±378.12 mL (n=518) [125]. Jun-2024 aTMTV evidence (n=367, r=.96, Dice=.72) is outside cutoff [185]. Reader/site bias and failures near bladder/kidneys, distorted anatomy or motion remain [184].

Image segmentation: ATLAAS tree/DeepTarget CNN automate PET-GTV/CTV (10-pt DSC .82; ≤2 min) [132][163]; Radiotherapy planning: GTV/CTV DSC +8.7/+3.4% (148-pt CV); validation needed [163]

**Image Segmentation (2022-10-04 PET/CT):** In six ⁸⁹Zr-pembrolizumab patients (18 scans), AI masks addressed slow, variable manual organ contours for biodistribution and dosimetry. RECOMIA used two U-Net-like CNNs trained on 339 labelled CT scans; review and correction remained possible [138]. Time fell from approximately 4 h to ≤30 min/scan; Jaccard similarity was 0.05 (0–0.14) for pancreas and 0.78 (0.74–0.82) for lungs, while whole-body effective-dose difference was 0.52% (0.15–1.95%) [138]. Kidney, liver and spleen volumes differed significantly. Separate 2024-01-25 SPECT/CT evidence—not PET—reported OAR Dice for liver/kidney/spleen/bone/lung/bladder of 97/94/95/94/98/84%; tumors remained manually delineated [137].

**Dosimetry (PET; SPECT/CT qualified):** The objective is patient-specific dose for efficacy and safety; bottlenecks include sparse or noisy time points, heterogeneity, physiological variation, nonstandard protocols and labor [137]. PET workflow: CNN organ masks → biodistribution → area-under-curve residence time → OLINDA/EXM, yielding mSv/MBq [138]. SPECT/CT workflow: trapezoidal TAC fitting below 24 h and exponential fitting above 24 h → TIA; CT density plus MSV and UNETR predicts MC−MSV, which is added to MSV [137]. In the 2024-01-25 study of 22 patients with five-fold cross-validation, voxel RAE was 5.28±1.32 (DL) versus 5.54±1.4 (MSV) and 7.8±3.02 (SSV); Gamma pass rate was 99.0±1.2%, computation took 3 s versus approximately 2 days for MC, and lesion-dose error was 1.15±2.5% [137]. Retrospective, monocentric, internal—not external—validation, manual lesions, MSV dependence and the need for multicentre testing limit readiness [137]. 2025 radiomics evidence is outside cutoff [141].

Image segmentation: automatic PET/CT GTV Dice 0.788 (2023; n=359) [145], cutoff-compliant.

Readiness needs task-specific/external validation [178][179]. Outside cutoff: [147] 2025-05-17; [165] 2026-02-05; exclude.

Segmentation: hypermetabolic tumour/ROI masks; broader ViT/SAM evidence [149] and post-2024 MedNeXt 3-D CNN [189]; needs review [190]. Quantification: AI applies 41% SUVmax/SUV 2.5 thresholds to calculate TMTV [190]. Planning: supervised CNN-UNet sCT supported GTV thresholding; Dice ≥0.987 in 10 PET-MR pts vs CTAC [177]. Dosimetry/radiogenomics: no outcomes here.

PET radiomics, 290 studies to Oct 2020: 46% prognosis/response; 21% diagnosis/staging [175].

Segmentation: tumor masks vs manual ROIs; CNN/FCN, weak/semi/unsup; Dice .64–.86, not pooled [99]. Lesion detection/classification: benign/malignant; UNet3D CT+SUV+mask; 82% vs 77% sensitivity, 1.8 FP/patient (n=211); single-site [126]. Quantification: MTV=segmented volume; TMTV adds metastases/nodes; accuracy NR [99]. RT: GTV contours (U-Net/FCN/GAN); plan effects NR [99]. Dosimetry: post-cutoff [193]; PET/TIA→S-value via ML/CNN; R²=.64, MAE=.73 Gy/GBq.

Segmentation: PET noise/resolution make ROIs variable; PET+CT graph cuts +10% vs either; CNN/U-Net PET/CT Dice 0.87 [338,336].  
Detection/classification: lesion finding; benign/malignant accuracy not reported; outside-cutoff 2025, 565 lesions: sensitivity 24.5%/66.2%, precision 9.1%/34.0%; specificity unavailable [146].  
Quantification: outside-cutoff 2026, 3-D U-Net/¹⁸F-FDG PET/CT/SUV≥4; TMTV within 10% or 10 cm³ in 50/60 (83%); human correction needed [133].  
Radiotherapy: PET/CT U-Net GTV contours reduce manual variability; PET plan/OAR-dose effects not reported [166].  
Dosimetry: PET/CT TAC→cumulative activity→dose; Deep-dose CNN versus Monte Carlo agrees; registration may change dose 90% [336,338].  
Radiomics/radiogenomics: 2023 DLBCL, PET radiomics > IPI for outcome; metrics, cohort and imaging–genomic fusion absent [133].

Lesion detection/classification: AI cut PET/CT reporting 15.0→13.3 min (11.3%) in 2024 [108]

Lesion detection/classification: PET CNN(2022,n130) .96 sens/1.00 spec [117]; NaF SORT/RF(2018) AUC .95 [123]. Quant: SUV/PERCIST; MTV/TMTV unknown [87]. Dosimetry: low-dose PET→internal dose model; validation unknown [87]. Radiomics: texture+CNN dx/prog; genomics unknown [82]

Lesion detection/classification: random forest, 2017 AUC 0.95, sens/spec 88% [170]; Retina U-Net, 2023 external sensitivity 88.8% [162]; physician review required; 2023 SUV bias [176].

AI-CNN TMTV: ICC 0.99 vs reference; 178 vs 326 s (2023), with physician review [194].

Quantitative analysis—AI proposed to automate MTV/TMTV; manual contouring took ~15 min/study, while AI architecture and direct MTV accuracy were unreported (post-cutoff) [153]. Radiotherapy planning—PET/CT BTVs from 38–50% SUVmax/PERCIST-TLG; 20-patient (2010–11) conformity was 30.0–37.8%, requiring clinician GTV review [120].

Radiotherapy Planning: U-Net CNN automates PET/CT GTV; ASCC Dice 0.65–0.83, 5-fold CV [167].

Radiotherapy planning—PET/CT→GTV; CNN/ATP; 2D dose error ~2% PTV/<5% OAR (general), PET-AI NR [198][135]. Dosimetry—PET activity/time→dose; AI NR; calibration/time points [135]. Radiomics/radiogenomics—heterogeneity; genetic fusion/metrics NR (post-cutoff) [207][197].

Dosimetry: PET dose; DL predicts S-value kernels, then MIRD computes voxel dose [199]. 20 PSMA patients: RMSE (Gy/GBq) kidney 0.11 (R²=.87), lesion 1.04 (R²=.77); no external test [89].

Dosimetry—personal dose; MC costly; PET/CT→U-Net/Pix2pix [139][144];1.07% [139];PBPK [201].

Dosimetry: Y90 PET denoise[76]; SPECT/CT U-Net MAE K/BM/L/S/T=1.04/.81/.54/1.34/3.18%vsMC[168]

PET radiomics: stage-IV colorectal TMB AUC 0.719 (n=91, CV); molecular-label prediction [202]

PET radiomics/omics: ML/DL predicts metastasis/PFS/survival; 2016; validation gaps [122][203]

AI PET radiomics/genomics links genes/outcomes [204]; AUC .90/n=25 (2020), limited val. [100]

PET radiomics: 2022 FDG-PET survival multitask c-index 0.71 (95% CI 0.67–0.75), n=45 [164].

Image Segmentation uses AI/deep learning to fuse PET’s functional/metabolic signal with CT’s anatomic localization and produce automatic or semi-automatic tumor/ROI masks, targeting low PET resolution, noise, heterogeneous uptake, mismatched boundaries and motion-related registration error [159]. CNN/encoder–decoder methods such as U-Net and related convolutional networks reduce labor and observer variability while supplying quantitative outputs for diagnosis, planning, dosimetry and radiomics [151][172][191].

Cutoff-compliant Image Segmentation evidence should state the ROI, PET/CT inputs, expert or semi-automatic reference contours, model and training supervision, cohort, and internal/external validation; the operational date is Feb. 22, 2024 [119][113][163]. Report overlap and clinically task-based metrics, including MTV/TLG or biomarker agreement, because task-agnostic Dice scores can disagree with quantitative PET performance; scanner/protocol and observer-variability limitations should also be recorded [186][188][151].

Lesion Detection and Classification uses AI to locate abnormal metabolic foci and classify them for benign-versus-malignant clinical decisions, addressing reader subjectivity, detectability limits and inter-scanner variability [169][178]. A benign-versus-malignant framework is illustrated for F-18 sodium-fluoride bone lesions, while deep learning separates pulmonary lesions into benign, lung cancer, lymphoma or metastasis [170][183]; reported performance was above 0.95 AUC and reading time fell from 15.0 to 13.3 min (11.3%) [108][124].

rejected (reason: no_entity): For Lesion Detection and Classification, apply the RELAINCE framework: define the anatomic label and five diagnostic categories, tracer/acquisition, cohort, CNN/3D-CNN or random-forest method, localization/segmentation endpoint, reference standard, AUC/sensitivity, and internal/external validation [187][176][170]. Report the 83% and 92% performance values and the three retrospective versus two prospective studies separately, because scanner/reconstruction and validation uncertainty limit pooling [170][78][127].

Lesion Detection and Classification can localize suspicious regions and return lesion locations and segmentation masks; detectability is higher for larger, high-contrast candidates and lower for small, low-contrast candidates, providing the supported ordering of candidate difficulty [146][178]. A benign-versus-malignant classifier can label pulmonary findings as benign, lung cancer, lymphoma or metastasis for physician review, while benign uptake remains a false-positive risk; AI reading was 13.3 rather than 15.0 min (11.3% lower) [170][183][124].

Quantitative Analysis uses AI to automate lesion segmentation and compute SUV, MTV and TMTV, targeting the time, reader dependence and threshold nonstandardization that make tumor-burden measurements variable [184][185]. A deep-learning/CNN workflow reported, across 900 scans, TMTV correlation 0.89 with ARE 0.43 ± 0.54 and 157.32 ± 378.12 mL, plus 0.30 ± 0.22 and 82.05 ± 99.78 mL in a second reported analysis; reference checking remains important [194][125][160].

rejected (reason: citation_outside_operands): For Quantitative Analysis, define MTV/TMTV, PET/CT normalization and the threshold (SUV 4.0 or 41 % SUVmax), CNN/U-Net mask generation, reference contours, cohort denominator, and mask-to-metric calculation [129][194][188]. Report agreement/error, processing time, and external or test–retest validation: 900 scans yielded 0.89 correlation, while automated versus expert processing was 5 min versus 20 min; thresholding and software lack consensus [125][184][185].

Quantitative Analysis maps coregistered PET/CT into lesion masks with a 3-D, four-level U-Net/CNN [148]: localization finds hypermetabolic foci, physiological uptake is filtered, and voxel membership is refined into contours [190][178]. MTV is the segmented tumor volume and TMTV aggregates lesion volumes [99]; SUV thresholds such as 4.0 or 41% SUVmax then yield SUV and burden measures [129][160], with reported TMTV correlation 0.89 and ARE 0.43 ± 0.54 [125].

Radiotherapy Planning uses AI to turn PET, often fused with RTCT/CT, into GTV/CTV contours, targeting slow, observer-dependent target definition and the risks of undercoverage or unnecessary normal-tissue dose; PET supplies complementary physiologic tumor information [150][120]. Deep CNNs and coupled 3-D U-Nets, including a two-stream chained PET–RTCT fusion with spatial context, generate GTV/CTV targets, while uncertain deformable-registration and fusion validation remain risks [163][75][196][195].

rejected (reason: citation_outside_operands): For Radiotherapy Planning, using the Feb. 22, 2024 cutoff, define GTV inputs, PET/CT or PET-plus-radiotherapy-CT data, expert reference contours, model, validation split, contour concordance, time, and plan-level effects; ATLAAS is a supervised decision-tree selector, with 20 patients and 2 min reported [119][132]. Most studies are retrospective and often single-institution; dedicated radiotherapy-position PET/CT is preferred for highest accuracy, while automated contours still require expert input [151][130][134].

Radiotherapy Planning can use SVM, ANN, FCM, deep CNNs and coupled 3-D U-Nets on PET, CT or PET–RTCT, trained against expert/manual GTV/CTV contours; the two-stream model fuses PET with RTCT and uses spatial context for CTV [113][163]. The resulting GTV (GTVp+GTVn where applicable) enters the radiotherapy/SBRT plan, while indirect workflows register PET/CT CT to planning CT and may test 40%, 50%, 60% or 70% SUVmax thresholds; these are aids, not substitutes for review [75][130][131][195].

Dosimetry uses AI to estimate patient-specific absorbed dose to tumors and healthy organs, targeting fixed-dose protocols, laborious individualized calculations and the need to balance tumor efficacy with organ safety [155][191][200]. Deep-dose CNNs predict voxel dose from PET/CT and transformer/UNETR models generate heterogeneous maps; pre-treatment 68Ga-PSMA PET/CT radiomics and bloodwork can predict 177Lu-PSMA activity/dose, with one workflow reducing ~2 days to 3 s, but isotope retraining and uncertainty, out-of-domain or unvalidated activity-modification risks remain [121][137][140][152].

Cutoff-bounded dosimetry evidence should name the SSV/MSV/MC dose-model framework, unit (mSv/MBq), activity/time inputs, time-integrated-activity reference calculation, isotope, cohort, comparator and validation [137][138][200][152]. The reported record includes 22 patients and approximately 4 h per scan versus ≤30 min, but accuracy, uncertainty and out-of-domain testing must be retained before personalized-dose use [137][138][152].

Dosimetry combines calibrated activity, patient anatomy/segmented organs and serial time–activity curves; integrating those curves yields source-region time-integrated activity, and SSV/MSV/MC models plus CNN/transformer dose maps convert it to voxel or organ dose in mSv/MBq [136][200][137][138]. This framework enables patient-specific prediction and treatment adaptation—one deep workflow reports ~1 min [137]—but remains human-reviewed because no prospectively validated AI rule for changing administered activity is established and uncertainty/out-of-domain errors can compromise safety [152][89].

Radiomics and Radiogenomics uses AI, including deep learning, to convert PET/CT tumor ROIs into quantitative intensity, texture and heterogeneity features, then combine them with genomic or mutational signatures through machine-learning classifiers for non-invasive diagnosis, molecular classification, response and survival/risk prediction [142][143][103][205]. PET/CT models reported EGFR AUC 0.82 and KRAS AUC 0.83 [102]; acquisition/reconstruction variability, feature instability, overfitting and limited external validation limit generalization, so outputs support rather than replace clinicians [142][202][109].

To compile cutoff-compliant Radiomics and Radiogenomics evidence, record tracer and acquisition/reconstruction, ROI, standardized intensity/texture/shape features, feature selection/harmonization, genomic labels, clinical endpoint, cohort and independent external validation; established radiomics/radiogenomics sources describe this imaging–genomic integration [142][143][103][203]. Report discrimination, calibration, repeatability and external performance separately, because high dimensionality, overfitting, feature instability, small cohorts, class imbalance and multicenter variability can undermine reproducibility and generalization [142][105][103].

## References

[1] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11025679/> Prism-PET detector study; Study; Prism-PET; Reduced-input Prism-PET CNN
[2] <https://doi.org/10.1038/s41746-021-00497-2> Multicenter low-count PET validation; SubtlePET; SubtlePET external validation; SubtlePET architecture
[3] <https://www.nature.com/articles/s41598-019-46620-y> Deep-dose study; Deep-dose; Deep-dose dosimetry description; Deep-dose architecture and data; Voxel dose-rate comparison; Whole-body dosimetry results; Deep-do…
[4] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7610859/> FBSEM; Model-based PET reconstruction; Direct reconstruction explanation; Physics-informed reconstruction; FBSEM architecture; FBSEM quantitative comparison; D…
[5] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7446936/> Registration study; Respiratory registration study; Respiratory artifact mechanism; Unsupervised registration architecture; Motion-compensated reconstruction;…
[6] <https://doi.org/10.1371/journal.pone.0195798> Glioma study; Automatic FET segmentation; FET pipeline and results
[7] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8971840/> HRNet study; Automated HRNet nodule study; HRNet–ResNet comparison
[8] <https://doi.org/10.3390/cancers14215221> Automated MTV; Automated lymphoma quantification; Organ-aware MTV pipeline
[9] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10995525/> Clinical evaluation; Clinical PET GTV evaluation; Architecture comparison; Internal clinical comparison; External clinical evaluation; Clinical contour workflo…
[10] <https://www.nature.com/articles/s41467-020-19116-x> EGFR-DLS; EGFR-DLS study; EGFR-DLS methods; EGFR prediction comparisons; Feature and ROI analysis; EGFR-DLS treatment-outcome analysis
[11] <https://doi.org/10.1109/trpms.2020.3014786> PET reconstruction review; Reconstruction paradigms; Reference-target learning
[12] <https://epub.uni-regensburg.de/55586/1/a-2198-0358.pdf> PET workflow review
[13] <https://ieeexplore.ieee.org/document/9036979> CNN detector localization; LaBella et al., 2020
[14] <https://www.mdpi.com/2076-3417/10/14/4753> MLP depth estimation; Monolithic-detector MLP
[15] <https://beta.iopscience.iop.org/article/10.1088/1361-6560/ace1d1> Inter-crystal scatter recovery; Simulation results
[16] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9582376/> TOF mechanism; Deep-TOF-PET design; Deep-TOF-PET results; Image-versus-projection interpretation
[17] <https://ar5iv.labs.arxiv.org/html/2302.01681> Residual-physics timing study
[18] <https://doi.org/10.1109/nssmicrtsd49126.2023.10337926> List-mode scatter classification; Scatter-correction results
[19] <https://labs.utsouthwestern.edu/yang-lab/previous-research> Joint correction design
[20] <https://link.springer.com/article/10.1007/s12194-024-00780-3> AUTOMAP–DeepPET comparison; Denoising and reconstruction review; Supervised PET denoising; Noise2Noise PET review; Noise2Void mechanism
[21] <https://doi.org/10.3390/app12168118> Direct cGAN reconstruction; cGAN evaluation
[22] <https://doi.org/10.1371/journal.pone.0238455> S-CycleGAN mechanism; S-CycleGAN results
[23] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8266729/> PET/MRI restoration study
[24] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9321225/> Personalized denoising study
[25] <https://doi.org/10.3390/electronics10131529> Wavelet Noise2Noise
[26] <https://www.mdpi.com/2076-3417/12/10/5187> Choline-PET methods; Choline-PET outcomes
[27] <https://jnm.snmjournals.org/content/64/6/951> PT-WGAN image-quality results; PT-WGAN lesion analysis
[28] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8670362/> Dynamic cardiac motion mechanism; DeepMC architecture; DeepMC evaluation; DeepMC motion scope
[29] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9064915/> DL-ADMM framework and results; DL-ADMM implementation
[30] <https://arxiv.org/html/2205.14147v3> FlowNet-PET mechanism and residuals; FlowNet-PET cardiac behavior
[31] <https://doi.org/10.48550/arxiv.2205.14147> FlowNet-PET evaluation
[32] <https://doi.org/10.3837/tiis.2022.07.004> Res-Voxel study
[33] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6878113/> PET/CT segmentation framework; PET/CT co-segmentation study; Co-segmentation comparison
[34] <https://link.springer.com/article/10.1007/s00259-024-06616-x> TMTV-Net; TMTV-Net design and segmentation; TMTV-Net external quantification
[35] <https://doi.org/10.1007/s10278-023-00823-y> Lymphoma segmentation comparison; Quantitative segmentation errors; PET feature definitions
[36] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7788118/> Segmentation repeatability study
[37] <https://doi.org/10.4274/mirt.galenos.2021.43760> Solitary-nodule classification
[38] <https://jnm.snmjournals.org/content/63/supplement_2/3158> Ground-glass nodule study; External ground-glass nodule evaluation
[39] <https://doi.org/10.3389/fonc.2023.1192908> Clinical/PET/CT feature model
[40] <https://doi.org/10.3390/app13095281> CLARITI study
[41] <https://www.frontiersin.org/journals/public-health/articles/10.3389/fpubh.2022.1047714/full> Low-count lesion classification
[42] <https://jnm.snmjournals.org/content/62/1/30> PARS tumor-burden study; PARS workflow; PARS prognostic comparison
[43] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9540653/> Independent PARS lung-cancer evaluation
[44] <https://doi.org/10.1186/s13014-023-02388-0> Multicenter GTV study; Whole-scan localization and segmentation; Transfer-learning results
[45] <https://link.springer.com/article/10.1007/s00259-020-05013-4> Medium-specific kernel method; Kernel dosimetry comparison; Kernel pipeline runtime; Kernel dosimetry
[46] <https://doi.org/10.1109/trpms.2024.3381849> PBPK-guided dosimetry; Virtual-patient evaluation
[47] <https://doi.org/10.1007/s00261-019-02028-w> Radiomics and radiogenomics review; General integration example
[48] <https://link.springer.com/article/10.1007/s11307-020-01487-8> Multimodal EGFR/KRAS study
[49] <https://doi.org/10.48550/arxiv.2303.08569> Small-cohort PET/CT radiomics
[50] <https://doi.org/10.3389/fphar.2022.898529> PET/CT hybrid prediction study; Hybrid study
[51] <https://www.mdpi.com/2075-1729/13/4/884> PET/CT–EGFR outcome model; PET-specific SBRT comparison; Radiogenomic model comparison
[52] <https://www.frontiersin.org/journals/oncology/articles/10.3389/fonc.2020.567160/full> PET/CT prognostic nomogram; Nomogram discrimination
[53] <https://link.springer.com/article/10.1186/s12859-023-05160-z> Whole-body PET–clinical survival model; Multimodal comparison
[54] <https://doi.org/10.1186/s40658-020-00340-9> PET radiomic robustness study
[55] <https://doi.org/10.1109/tip.2008.2007756>
[56] <https://doi.org/10.1109/nssmic.1996.587908>
[57] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10562009>
[58] <https://www.youtube.com/watch?v=2YXoBqsk_ls>
[59] <https://doi.org/10.1007/s12194-024-00780-3>
[60] <https://link.springer.com/article/10.1007/s00259-022-05800-1>
[61] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10387227/>
[62] <https://doi.org/10.1007/s00259-022-06097-w>
[63] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10902118/>
[64] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8457531/>
[65] <https://doi.org/10.1186/2197-7364-1-s1-a57>
[66] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7007962/>
[67] <https://doi.org/10.1007/s10334-024-01199-y>
[68] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8218135/>
[69] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7105551/>
[70] <https://doi.org/10.1088/1361-6560/ac093b>
[71] <https://doi.org/10.1088/1361-6560/ab8688>
[72] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9361154/>
[73] <https://escholarship.org/content/qt5ss790gb/qt5ss790gb.pdf?t=s5jks5>
[74] <https://doi.org/10.1016/j.ejmp.2022.10.016>
[75] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10773015/>
[76] <https://www.imt.uni-luebeck.de/research/nuclear-imaging/ai-for-dose-reduction-and-denoising-in-pet>
[77] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8490278/>
[78] <https://doi.org/10.3990/1.9789036548700>
[79] <https://events.ncbj.gov.pl/event/314/contributions/1568/attachments/647/958/wmlq2024.pdf>
[80] <https://doi.org/10.1186/s40658-021-00374-7>
[81] <https://www.saxsons.com/research/paper/992/revolutionizing-internal-dosimetry-with-ai-pet-only-solutions-for-precision-medi/>
[82] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6702769/>
[83] <https://link.springer.com/article/10.1007/s13534-024-00427-7>
[84] <https://doi.org/10.1007/s00259-022-05901-x>
[85] <https://jnm.snmjournals.org/content/65/1/4>
[86] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10691821/>
[87] <https://doi.org/10.1186/s40644-020-00312-3>
[88] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5902038/>
[89] <https://www.frontiersin.org/journals/nuclear-medicine/articles/10.3389/fnume.2026.1935247/full>
[90] <https://arxiv.org/pdf/2302.13546>
[91] <https://doi.org/10.48550/arxiv.2302.10481>
[92] <https://doi.org/10.1007/s13139-024-00845-6>
[93] <https://belnuc.be/content/uploads/2024/06/AI_Belnuc-SVDB.pdf>
[94] <https://doi.org/10.1007/s00259-022-05746-4>
[95] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11440950/>
[96] <https://doi.org/10.1016/j.ejmp.2020.07.028>
[97] <https://doi.org/10.3390/tomography8020091>
[98] <https://link.springer.com/article/10.1007/s13139-026-00988-8>
[99] <https://doi.org/10.48550/arxiv.2107.13661>
[100] <https://doi.org/10.2478/raon-2020-0042>
[101] <https://www.mdpi.com/2075-4426/12/2/205>
[102] <https://doi.org/10.1007/s11307-020-01487-8>
[103] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9220825/>
[104] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7295928/>
[105] <https://doi.org/10.1016/j.phro.2021.10.007>
[106] <https://doi.org/10.1186/2197-7364-1-s1-a77>
[107] <https://www.serdarbalci.com/ClinicoPathJamoviModule/reference/segmentationmetrics.html>
[108] <https://www.frontiersin.org/journals/nuclear-medicine/articles/10.3389/fnume.2023.1327186/full>
[109] <https://link.springer.com/article/10.1186/s40644-024-00682-y>
[110] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8372231/>
[111] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10995525/>
[112] <https://www.nature.com/articles/s41598-025-09638-z>
[113] <https://atm.amegroups.org/article/view/69655/html>
[114] <https://www.frontiersin.org/journals/artificial-intelligence/articles/10.3389/frai.2024.1423535/full>
[115] <https://www.nature.com/articles/s41698-025-00970-1>
[116] <https://doi.org/10.22215/etd/2024-15866>
[117] <https://vivo.weill.cornell.edu/display/pubid36457510>
[118] <https://pmc.ncbi.nlm.nih.gov/articles/PMC13048871/>
[119] <https://jnm.snmjournals.org/content/65/4/623>
[120] <https://pmc.ncbi.nlm.nih.gov/articles/PMC3722117/>
[121] <https://www.nature.com/articles/s41598-019-46620-y>
[122] <https://zenodo.org/records/20270354>
[123] <https://iopscience.iop.org/article/10.1088/1361-6560/aaebd0>
[124] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11440880/>
[125] <https://link.springer.com/article/10.1007/s00259-024-06616-x?code=6a3211e7-4476-40af-afb3-048365908e45&error=cookies_not_supported>
[126] <https://link.springer.com/article/10.1007/s00259-022-05806-9>
[127] <https://scholarworks.korea.ac.kr/kumedicine/bitstream/2020.sw.kumedicine/49397/1/46_2019_EJNMMI_2019_equivocal_FBB_AI_published.pdf>
[128] <https://www.hug.ch/sites/interhug/files/structures/pinlab/documents/ejnmmi2024_segm.pdf>
[129] <https://medrun.ai/models/nm/fdg-pet>
[130] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6849663/>
[131] <https://www.nature.com/articles/s41598-018-25350-7>
[132] <https://doi.org/10.1016/j.radonc.2016.12.008>
[133] <https://doi.org/10.2967/jnumed.125.271605>
[134] <https://doi.org/10.1093/bjr/tqae077>
[135] <https://doi.org/10.1002/acm2.13785>
[136] <https://arxiv.org/pdf/2604.06280>
[137] <https://doi.org/10.1007/s00259-024-06618-9>
[138] <https://doi.org/10.1007/s11307-022-01775-5>
[139] <https://doi.org/10.1038/s41598-019-46620-y>
[140] <https://jnm.snmjournals.org/content/65/supplement_2/242200>
[141] <https://www.nature.com/articles/s41571-025-01067-1>
[142] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6278749/>
[143] <https://link.springer.com/article/10.1007/s00259-018-4139-4?code=559352fa-669a-4496-aacf-3ee147970b50&error=cookies_not_supported>
[144] <https://doi.org/10.1016/j.radphyschem.2024.111532>
[145] <https://doi.org/10.1007/978-3-031-27420-6_1>
[146] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12149679/>
[147] <https://biomedpharmajournal.org/vol19no1/external-validation-of-pet-radiomics-based-ml-model-for-non-invasive-lung-cancer-subtype-classification/>
[148] <https://research.chalmers.se/publication/552540/file/552540_Fulltext.pdf>
[149] <https://arxiv.org/html/2401.03495v1>
[150] <https://doi.org/10.1007/s00066-024-02262-2>
[151] <https://tcr.amegroups.org/article/view/118417/html>
[152] <https://doi.org/10.3389/fnume.2026.1935247>
[153] <https://jitc.bmj.com/content/12/4/e007628>
[154] <https://www.nature.com/articles/s41598-025-09212-7>
[155] <https://www.eurekalert.org/news-releases/1129744>
[156] <https://doi.org/10.3390/diagnostics14222473>
[157] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7814987/>
[158] <https://digitalcommons.mtu.edu/cgi/viewcontent.cgi?article=34342&context=michigantech-p>
[159] <https://www.bccrc.ca/dept/io-programs/qurit/news/state-art-petct-image-segmentation>
[160] <https://arxiv.org/html/2311.09614v4>
[161] <https://doi.org/10.3389/fonc.2022.1007874>
[162] <https://doi.org/10.1007/s00330-022-09332-y>
[163] <https://www.cs.jhu.edu/~lelu/publication/1-s2.0-S1361841520302735-main_DeepTarget.pdf>
[164] <https://doi.org/10.3390/cancers14051228>
[165] <https://www.nature.com/articles/s41746-026-02354-6>
[166] <https://doi.org/10.1186/s41824-020-00086-8>
[167] <https://medicaljournalssweden.se/actaoncologica/article/view/20326>
[168] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10043146/>
[169] <https://www.mdpi.com/2077-0383/15/6/2446>
[170] <https://www.auntminnie.com/clinical-news/molecular-imaging/nuclear-medicine/article/15618242/ai-algorithm-can-classify-bone-lesions-on-petct-images>
[171] <https://doi.org/10.3390/bioengineering11121213>
[172] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11450131/>
[173] <https://doi.org/10.1145/3768158>
[174] <https://www.mdpi.com/2306-5354/11/12/1213>
[175] <https://pmc.ncbi.nlm.nih.gov/articles/PMC7926413/>
[176] <https://link.springer.com/article/10.1186/s13550-023-00999-y>
[177] <https://link.springer.com/article/10.1186/s40658-024-00617-3>
[178] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8735853/>
[179] <https://arxiv.org/html/2303.00640v1>
[180] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8440243/>
[181] <https://link.springer.com/article/10.1186/s40658-025-00750-7>
[182] <https://doi.org/10.3389/fmed.2021.628179>
[183] <https://link.springer.com/article/10.1007/s00259-025-07215-0>
[184] <https://doi.org/10.3390/cancers14215221>
[185] <https://jnm.snmjournals.org/content/65/supplement_2/241325>
[186] <https://doi.org/10.1117/12.2647894>
[187] <https://doi.org/10.2967/jnumed.121.263239>
[188] <https://jnm.snmjournals.org/content/jnumed/early/2022/05/26/jnumed.121.263239.full.pdf>
[189] <https://www.mdpi.com/2072-6694/18/19/3196>
[190] <https://gaelo.fr/en/algorithms/pet-segmentation/fdg/>
[191] <https://www.hug.ch/sites/interhug/files/structures/pinlab/documents/petclin2026.pdf>
[192] <https://www.springermedizin.de/a-convolutional-neural-network-for-fully-automated-total-metabol/52206538>
[193] <https://doi.org/10.48550/arxiv.2510.12714>
[194] <https://www.springermedicine.com/lymphoma/artificial-intelligence/evaluation-of-a-convolution-neural-network-for-baseline-total-tu/23889942>
[195] <https://pureadmin.qub.ac.uk/ws/portalfiles/portal/16523251/pet.pdf>
[196] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10068574/>
[197] <https://www.frontiersin.org/journals/medicine/articles/10.3389/fmed.2026.1794722/full>
[198] <https://pmc.ncbi.nlm.nih.gov/articles/PMC6732844/>
[199] <https://doi.org/10.1016/j.ejmp.2021.03.008>
[200] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12079709/>
[201] <https://doi.org/10.1109/trpms.2024.3381849>
[202] <https://doi.org/10.1002/mco2.722>
[203] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5868194/>
[204] <https://www.ejradiology.com/article/S0720-048X(20)30638-0/fulltext>
[205] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10296704/>
[206] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5412389/>
[207] <https://www.mdpi.com/2076-3417/11/21/10170>
[208] <https://mdpi-res.com/d_attachment/diagnostics/diagnostics-13-01626/article_deploy/diagnostics-13-01626.pdf?version=1683198429>
[209] <https://esmed.org/deep-learning-for-multiclass-pulmonary-lesion-detection/>
[210] <https://doi.org/10.1109/isbi.2015.7164085>
[211] <https://pubmed.ncbi.nlm.nih.gov/34426629/>
[212] <https://doi.org/10.3389/fneur.2024.1383773>
[213] <https://doi.org/10.1186/s13550-022-00901-2>
[214] <https://www.sciencedirect.com/science/article/abs/pii/S0169260723005461>
[215] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9454473/>
[216] <https://doi.org/10.1007/s00259-022-06001-6>
[217] <https://www.frontiersin.org/journals/oncology/articles/10.3389/fonc.2022.1007874/full>
[218] <https://link.springer.com/article/10.1007/s00259-023-06152-0>
[219] <https://www.nature.com/articles/s42256-024-00912-9>
[220] <https://link.springer.com/content/pdf/10.1007/s10278-023-00823-y.pdf?error=cookies_not_supported&code=b19e63c5-1168-4e99-96cb-481b7b120c3f>
[221] <https://jnm.snmjournals.org/content/66/supplement_1/251795>
[222] <https://www.ai.mil/Portals/137/Documents/Resources%20Page/Test%20and%20Evaluation%20of%20Artificial%20Intelligence%20Models%20Framework.pdf>
[223] <https://link.springer.com/article/10.1186/s13550-026-01403-1>
[224] <https://ejnmmiphys.springeropen.com/counter/pdf/10.1186/s40658-021-00377-4.pdf>
[225] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9034765/>
[226] <https://pmc.ncbi.nlm.nih.gov/articles/PMC9653575/>
[227] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12838964/>
[228] <https://doi.org/10.1016/j.acra.2024.12.016>
[229] <https://google.iopscience.iop.org/article/10.1088/1361-6560/abb6bd>
[230] <https://pmc.ncbi.nlm.nih.gov/articles/PMC10659582/>
[231] <https://baselbiometrics.github.io/home/docs/talks/20240925/7_TaoXu_aTMTV%20Performance%20Assessment_final_noBackup.pdf>
[232] <https://doi.org/10.2967/jnumed.119.238923>
[233] <https://library.ehaweb.org/eha/2023/eha2023-congress/document?c_id=385693&cm_id=400349&type=document400349>
[234] <https://doi.org/10.1007/978-3-662-67192-4_7>
[235] <https://doi.org/10.1007/978-3-662-67192-4_27>
[236] <https://pmc.ncbi.nlm.nih.gov/articles/PMC13045712/>
[237] <https://www.dosisoft.com/2023/12/27/dosisoft-ai-based-research-explores-future-radiation-oncology-qa-procedures-medical-quantitative-imaging/>
[238] <https://www.banook.com/resources/blog/dosimetry-and-its-use-in-clinical-trials>
[239] <https://www.versantphysics.com/2021/10/27/radiation-dosimetry-for-animals/>
[240] <https://stacks.cdc.gov/view/cdc/121206/cdc_121206_DS1.pdf>
[241] <https://doi.org/10.1088/1361-6560/adf02c>
[242] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12051766/>
[243] <https://jnm.snmjournals.org/content/67/supplement_1/261832>
[244] <https://doi.org/10.1097/mnm.0b013e328330626f>
[245] <https://pmc.ncbi.nlm.nih.gov/articles/PMC2804106/>
[246] <https://pmc.ncbi.nlm.nih.gov/articles/PMC5695148/>
[247] <https://pmc.ncbi.nlm.nih.gov/articles/PMC11024845/>
[248] <https://pmc.ncbi.nlm.nih.gov/articles/PMC12446183/>
[249] <https://www.tracercro.com/radiation-dosimetry-study/>
[250] <https://pmc.ncbi.nlm.nih.gov/articles/PMC8324619/>
[251] <https://www.nature.com/articles/s41598-025-88498-z>
[252] <https://doi.org/10.2967/jnumed.121.263738>
[253] <https://www.intechopen.com/online-first/1241582>
