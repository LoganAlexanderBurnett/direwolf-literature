# DIREWOLF Surrogate-Modeling Literature Review

Research cutoff: October 7, 2026 | Application: transient, coupled neutronics–thermal surrogate modeling on irregular finite-element meshes

This review prioritizes methods that can predict spatially distributed `power_density`, `Tfuel`, and `Tmod` over a 0–100 s transient under prescribed control-drum motion.

The evidence standard is important: a paper demonstrating field prediction on a Cartesian grid is not treated as having demonstrated compatibility with a native 3D finite-element mesh. Likewise, a physics-informed loss is not evidence of exact conservation, and a neural operator demonstrated on steady PDEs is not automatically a validated transient reactor surrogate.

## 1. Mandatory seed verification

| Seed                 | Verified identification                                                                                                                                                                           | Status                                                                              |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| 1. IEEE 8578372      | Wang et al. (2018), Deep Parametric Continuous Convolutional Neural Networks. CVPR. DOI: 10.1109/CVPR.2018.00274                                                                                  | Verified through an institutional publication record; IEEE's page was inaccessible  |
| 2. S0306454926007425 | Title, authors, DOI and publication status could not be independently established                                                                                                                 | Unresolved — do not ingest fabricated metadata                                      |
| 3. S1738573323002917 | Antonello, Buongiorno & Zio (2023), Physics informed neural networks for surrogate modeling of accidental scenarios in nuclear power plants. DOI: 10.1016/j.net.2023.06.027                       | Verified, open access                                                               |
| 4. S173857332400175X | Li, Zheng, Du & Xiao (2024), A new surrogate method for the neutron kinetics calculation of nuclear reactor core transients. DOI: 10.1016/j.net.2024.04.007                                       | Verified, open access                                                               |
| 5. Gong et al.       | Gong, Cheng, Chen & Li (2022), Data-Enabled Physics-Informed Machine Learning for Reduced-Order Modeling Digital Twin: Application to Nuclear Reactor Physics. DOI: 10.1080/00295639.2021.2014752 | Verified, published in Nuclear Science and Engineering 196(6), 668–693              |
| 6. Zeng et al.       | Zeng et al. (2025), Point cloud neural operator for parametric PDEs on complex and variable geometries. DOI: 10.1016/j.cma.2025.118022                                                            | Verified, Computer Methods in Applied Mechanics and Engineering 443, article 118022 |

The IEEE seed is a point-cloud convolution paper, not a nuclear-engineering paper. It is relevant as a geometric learning precursor. The 2024 Li paper is particularly relevant because it actually models time-dependent spatial reactor power distributions, including control-rod disturbances, although its demonstrated spatial resolution is much coarser than a large native FE field.

Sources: institutional IEEE metadata&#x20;

[image](https://www.google.com/s2/favicons?domain=https://experts.illinois.edu\&sz=32)

Illinois Experts

, nuclear publisher and indexing records&#x20;

[image](https://www.google.com/s2/favicons?domain=https://doi.org\&sz=32)

ScienceDirect

+2

, and PCNO publisher metadata&#x20;

[image](https://www.google.com/s2/favicons?domain=https://www.sciencedirect.com\&sz=32)

ScienceDirect

.



## 2. Ranked Tier 1 core library

The following ranking reflects expected usefulness for DIREWOLF, not citation count. A high score means the paper addresses an important part of the modeling problem; it does not mean its results have already been validated for heat-pipe microreactors.

Evidence notation: `T` = substantive technical sections inspected; `A` = publisher abstract and metadata examined; `B` = bibliographic reference independently identified but detailed methodology not reviewed. `NV` = not verified. `NR` = not reported in the material examined.

The DOI link is the canonical acquisition route where one was verified. OA links refer to publisher-open articles, author manuscripts, or legitimate preprints.

### Tier 1A — Highest-priority downloads

| Rank     | Paper and acquisition                                                                                                                                                                                                                                                                                                                                              | Technical contribution and applicability                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1 · 5/5  | Li, Xiaoqi; Zheng, Youqi; Du, Xianan; Xiao, Bowen (2024). A new surrogate method for the neutron kinetics calculation of nuclear reactor core transients. Nuclear Engineering and Technology, 56, 3571–3584. DOI / OA article. Code: NV.                                                                                                                           | CNN–RNN, reactor neutronics, coarse spatial zones, transient. Converts time-varying power into parameterized temporal functions, then learns their spatial dependence from reactivity disturbances. Tests 1D, 2D TWIGL and a simplified 3D core with 29 power zones and 18 rods. Direct precedent for drum-driven power transients, but not native high-resolution FE reconstruction or thermal coupling. Physics: engineered reactivity/time-function structure, not exact conservation. UQ: NR. Tags: `NUC,TRANS,FIELD,CTRL,SEQ`. Provenance: S4; T. |
| 2 · 5/5  | Zeng, Chenyu; Zhang, Yanshu; Zhou, Jiayi; Wang, Yuhan; Wang, Zilin; Liu, Yuhao; Wu, Lei; Huang, Daniel Zhengyu (2025). Point cloud neural operator for parametric PDEs on complex and variable geometries. CMAME, 443, 118022. DOI · OA manuscript · official code.                                                                                                | PCNO, general PDE/mechanics, irregular point clouds. Combines quadrature-weighted Fourier integral terms, pointwise maps and connectivity-based least-squares gradients. Tests adaptive meshes, varying geometries, vehicle pressure and parachute problems. Particularly relevant to FE volume weights and discretization sensitivity. Does not establish a controlled 100 s coupled-reactor rollout. Physics: operator structure, no guaranteed conservation. UQ: NR. Tags: `PC,FE,QUAD,FIELD,OPERATOR`. Provenance: S6; T.                          |
| 3 · 5/5  | Gong, Helin; Cheng, Sibo; Chen, Zhang; Li, Qing (2022). Data-Enabled Physics-Informed Machine Learning for Reduced-Order Modeling Digital Twin: Application to Nuclear Reactor Physics. Nuclear Science and Engineering, 196, 668–693. DOI · official code. OA manuscript: institutional version identified as HAL-03598305; direct file access not verified.      | POD + KNN/decision trees, reactor power/neutron flux fields. Learns input-dependent reduced coefficients and reconstructs HPR1000 core distributions under changes in burnup, rod position, power and coolant temperature. Strong nuclear precedent for interpretable reduced-coordinate field surrogates. Not demonstrated as an LSTM-driven long-horizon transient model. Physics: physics-based reduced basis, not necessarily constrained predictions. UQ: NR. Tags: `NUC,POD,FIELD,ROM`. Provenance: S5; A.                                       |
| 4 · 5/5  | Gong, Helin; Cheng, Sibo; Chen, Zhang; Li, Qing; Quilodrán-Casas, César; Xiao, Dunhui; Arcucci, Rossella (2022). An efficient digital twin based on machine learning SVD autoencoder and generalised latent assimilation for nuclear reactor physics. Annals of Nuclear Energy, 179, 109431. DOI · OA accepted manuscript. Code: NV.                               | SVD-autoencoder + latent assimilation, reactor power fields. Combines a compressed nonlinear representation, KNN/decision-tree forward prediction and an inverse latent assimilation formulation. Relevant to upgrading linear POD and incorporating observations without reconstructing every FE degree of freedom during inference. Long transient dynamics are not its demonstrated focus. UQ: NR. Tags: `NUC,LAT,POD,FIELD,ASSIM`. Provenance: related Gong group; A.                                                                              |
| 5 · 5/5  | Zhang, Tao; Jiao, Yongjun; Liu, Zhenhai; Li, Yuanming; Wang, Haoyu (2025). Learning to simulate quasi-steady-state fuel rod performance with hybrid Fourier neural operator. Progress in Nuclear Energy, 186, 105769. DOI. Legitimate OA: not located. Code: NV.                                                                                                   | FNO–LSTM, nuclear thermal/mechanical fields, structured 1.5D fuel-rod representation, power-history-driven sequences. Uses three LSTMs and an FNO–LSTM to predict spatially distributed fuel performance quantities. Reports a 1,700× acceleration over its 1.5D reference code. Strong evidence for temporal-history conditioning and multiple physical outputs; not evidence of full-core 3D FE capability. Physics: informed input/history generation. UQ: NR. Tags: `NUC,FNO,LSTM,TRANS,MULTI`. Provenance: recent-topic search; A.                |
| 6 · 5/5  | Yuan, Jiacheng; Zeng, Lei; Gui, Yewei; Shi, Youan; Xia, Bin; Wei, Dong (2026). A transient heat conduction prediction method for complex structures based on neural operators. International Communications in Heat and Mass Transfer, 175, 111125. DOI. OA/code: NV.                                                                                              | T²FO-Net / T²FGO-Net, transient temperature fields. Combines autoregressive FNO prediction with a graph-Fourier variant for unstructured 2D/3D meshes. Directly addresses irregular-mesh thermal rollout. The reported temperature errors are from four non-nuclear benchmarks; 100 s coupled-reactor stability and FE conservation are unverified. Tags: `THERM,TRANS,GNN,FNO,FE`. Provenance: 2026 topic search; A.                                                                                                                                  |
| 7 · 5/5  | Li, Zongyi; Kovachki, Nikola; Choy, Chris; Li, Boyi; Kossaifi, Jean; Otta, Shourya; Nabian, Mohammad Amin; Stadler, Maximilian; Hundt, Christian; Azizzadenesheli, Kamyar; Anandkumar, Anima (2023). Geometry-Informed Neural Operator for Large-Scale 3D PDEs. NeurIPS. Conference record · OA manuscript. DOI: NV. Code: NV.                                     | GINO, 3D CFD, irregular geometry to latent grid, static field operator. Uses graph-operator transforms between point clouds and regular latent grids, with FNO processing in between. Demonstrates large-scale surface-pressure prediction and discretization-transfer behavior. Strong architecture candidate for native FE data, but the published example is not coupled transient volume-field prediction. Tags: `GINO,GNN,FNO,3D,FE`. Provenance: topic search; A.                                                                                |
| 8 · 5/5  | Pfaff, Tobias; Fortunato, Meire; Sanchez-Gonzalez, Alvaro; Battaglia, Peter (2021). Learning Mesh-Based Simulation with Graph Networks. ICLR. Author publication, PDF and code links. DOI: NV.                                                                                                                                                                     | MeshGraphNets, mesh-based mechanics/fluids, autoregressive node-field dynamics. Mesh-edge message passing updates physical state and can accommodate unstructured connectivity and moving meshes. A natural FE-native alternative to POD-LSTM, but high-resolution 3D graph storage, long-range coupling and rollout drift need testing. Physics: learned dynamics rather than guaranteed conservation. UQ: NR. Tags: `GNN,FE,TRANS,FIELD,ROLLOUT`. Provenance: PCNO backward reference; A.                                                            |
| 9 · 5/5  | Sarkar, Subhankar; Chakraborty, Souvik (2025). Spatio-spectral graph neural operator for solving computational mechanics problems on irregular domain and unstructured grid. CMAME, 435, 117659. DOI · official code. OA manuscript: NV.                                                                                                                           | Sp²GNO, computational mechanics, unstructured graph fields. Combines local spatial graph processing with global spectral graph information to address long-range dependencies and oversquashing. Relevant to coupling localized thermal gradients with global neutronic response. Transient reactor demonstrations: NR. Physics/UQ: no exact conservation or calibrated predictive UQ established in examined material. Tags: `GNN,SPECTRAL,FE,FIELD`. Provenance: 2025 topic search; A.                                                               |
| 10 · 5/5 | Brandstetter, Johannes; Worrall, Daniel E.; Welling, Max (2022). Message Passing Neural PDE Solvers. ICLR. Conference PDF · OA manuscript · official code. DOI: NV.                                                                                                                                                                                                | Message-passing PDE solver, 1D/2D time-dependent fluid-like equations. Learns local numerical updates and introduces a stability-oriented training strategy motivated by zero-stability. Useful for controlled autoregressive rollout comparisons; its demonstrated dimensionality and physics do not establish large 3D coupled FE performance. UQ: NR. Tags: `GNN,TRANS,ROLLOUT,STABILITY`. Provenance: PCNO backward reference; A.                                                                                                                  |
| 11 · 5/5 | Wu, Haixu; Luo, Huakun; Wang, Haowen; Wang, Jianmin; Long, Mingsheng (2024). Transolver: A Fast Transformer Solver for PDEs on General Geometries. ICML, PMLR 235. Publisher / OA PDF · official code. DOI: NV.                                                                                                                                                    | Physics-attention transformer, point/mesh geometry, parametric PDE fields. Groups mesh points into learned physical-state slices, reducing attention cost and enabling nonlocal interactions. Candidate for long-range neutronic–thermal correlations without an all-pairs nodal attention matrix. Controlled transient rollout and conservation remain unverified. Tags: `ATTN,FE,FIELD,3D`. Provenance: 2024 topic search; A.                                                                                                                        |
| 12 · 5/5 | Luo, Huakun; Wu, Haixu; Zhou, Hang; Xing, Lanxiang; Di, Yichen; Wang, Jianmin; Long, Mingsheng (2025). Transolver++: An Accurate Neural Solver for PDEs on Million-Scale Geometries. ICML, PMLR 267. Publisher / OA PDF. DOI: NV. Code: publisher provides software link; exact repository not independently checked.                                              | Scalable geometry-aware transformer, million-point industrial meshes. Introduces optimized parallel processing and local adaptive state representations. Highly relevant to the memory barrier for full 3D FE fields, but published car/aircraft results are not evidence of 100 s nuclear transients. Tags: `ATTN,3D,SCALE,FE`. Provenance: 2025 topic search; A.                                                                                                                                                                                     |
| 13 · 5/5 | Li, Zongyi; Huang, Daniel Zhengyu; Liu, Burigede; Anandkumar, Anima (2023). Fourier Neural Operator with Learned Deformations for PDEs on General Geometries. JMLR, 24(388), 1–26. Publisher / OA · manuscript. DOI: NV.                                                                                                                                           | Geo-FNO, mechanics/CFD, geometry deformation to structured latent coordinates. Supports meshes, point clouds and design parameters by learning a geometry transformation before FFT-based operator layers. Attractive if DIREWOLF can use a stable geometric reference mapping; less attractive where topology or strongly nonuniform local features defeat that mapping. UQ: NR. Tags: `FNO,GEOM,FE,FIELD`. Provenance: PCNO backward reference; A.                                                                                                   |
| 14 · 5/5 | Li, Zongyi; Kovachki, Nikola; Azizzadenesheli, Kamyar; Liu, Burigede; Bhattacharya, Kaushik; Stuart, Andrew; Anandkumar, Anima (2021). Fourier Neural Operator for Parametric Partial Differential Equations. ICLR. Conference / OA. DOI: NV.                                                                                                                      | FNO, regular-grid PDE fields, static and time-dependent benchmarks. Fourier-space kernel parameterization learns functional solution maps efficiently, including Burgers, Darcy and Navier–Stokes examples. Essential operator baseline, but native irregular FE support is absent from the standard FFT formulation. Physics/UQ: unconstrained deterministic baseline. Tags: `FNO,OPERATOR,TRANS,GRID`. Provenance: PCNO backward reference; A.                                                                                                       |
| 15 · 5/5 | Lu, Lu; Jin, Pengzhan; Pang, Guofei; Zhang, Zhongqiang; Karniadakis, George Em (2021). Learning nonlinear operators via DeepONet based on the universal approximation theorem of operators. Nature Machine Intelligence, 3, 218–229. DOI. Legitimate OA manuscript: NV. Code: NV.                                                                                  | DeepONet, general PDE operators, coordinate-query outputs. Branch network encodes input-function observations; trunk network evaluates spatial coordinates. Potentially useful for predicting fields at arbitrary FE nodes and querying selected hot spots, with control trajectories represented as input functions. Universal approximation does not establish extrapolation to unseen drum histories. Tags: `DON,FIELD,CTRL,OPERATOR`. Provenance: PCNO backward reference; A.                                                                      |
| 16 · 5/5 | Wang, Sifan; Wang, Hanwen; Perdikaris, Paris (2021). Learning the solution operator of parametric partial differential equations with physics-informed DeepONets. Science Advances, 7, eabi8605. DOI / OA · official code.                                                                                                                                         | Physics-informed DeepONet, parametric PDEs, coordinate/time-query solution fields. Trains an operator using PDE residuals, including examples without paired solution data. Direct precedent for adding neutronic/thermal residual penalties to a trajectory-conditioned operator. The residuals are soft constraints; exact global conservation is not guaranteed. UQ: NR. Tags: `DON,PINN,PHYS,TRANS`. Provenance: topic and citation search; A.                                                                                                     |
| 17 · 5/5 | Li, Zongyi; Zheng, Hongkai; Kovachki, Nikola; Jin, David; Chen, Haoxuan; Liu, Burigede; Azizzadenesheli, Kamyar; Anandkumar, Anima. Physics-Informed Neural Operator for Learning Partial Differential Equations. Caltech accepted-manuscript record · arXiv. Accepted version deposited 2024; definitive journal venue/DOI not verified in this search. Code: NV. | PINO, regular-grid neural operator with PDE residual regularization. Combines coarse-resolution labeled fields with higher-resolution physics residuals. Relevant to exploiting expensive DIREWOLF simulations alongside cheaper residual evaluation, provided FE weak-form residuals are implemented correctly. Neither exact conservation nor nuclear OOD reliability is established. Tags: `FNO,PINN,PHYS,DATA`. Provenance: topic search; A.                                                                                                       |
| 18 · 5/5 | Hesthaven, Jan S.; Ubbiali, Stefano (2018). Non-intrusive reduced order modeling of nonlinear problems using neural networks. Journal of Computational Physics, 363, 55–78. DOI/publisher link: NV; identified in PCNO references. OA/code: NV.                                                                                                                    | Nonintrusive neural ROM, reduced coefficients. Establishes the central strategy of learning parameter-to-reduced-state maps without modifying the high-fidelity solver. A direct methodological baseline for DIREWOLF's FE-aware POD pipeline. Specific temporal architecture and UQ: NR. Tags: `POD,ROM,DATA`. Provenance: PCNO backward reference; B.                                                                                                                                                                                                |
| 19 · 5/5 | Peherstorfer, Benjamin; Willcox, Karen (2016). Data-driven operator inference for nonintrusive projection-based model reduction. CMAME, 306, 196–215. DOI/publisher/OA/code: NV; bibliographic metadata identified in PCNO references.                                                                                                                             | Operator inference, POD-coordinate dynamical systems. Infers reduced operators rather than an unrestricted recurrent black box. Particularly relevant to replacing or complementing the LSTM with interpretable, low-dimensional dynamics and known control inputs. Stability and accuracy depend on inferred dynamics and training coverage. Tags: `POD,OPINF,TRANS,CTRL`. Provenance: PCNO backward reference; B.                                                                                                                                    |
| 20 · 5/5 | Lee, Kookjin; Carlberg, Kevin T. (2020). Model reduction of dynamical systems on nonlinear manifolds using deep convolutional autoencoders. Journal of Computational Physics, 404, 108973. DOI/OA/code: NV; bibliographic metadata identified in PCNO references.                                                                                                  | Nonlinear-manifold ROM, convolutional autoencoder, dynamical fields. Provides an alternative when POD requires too many modes to represent localized nonlinear field variation. For DIREWOLF, the critical additional burden is constructing a decoder that respects FE geometry and physical weighting. UQ: NR. Tags: `LAT,AE,ROM,TRANS`. Provenance: PCNO backward reference; B.                                                                                                                                                                     |
| 21 · 5/5 | Qian, Elizabeth; Kramer, Boris; Peherstorfer, Benjamin; Willcox, Karen (2020). Lift & Learn: Physics-informed machine learning for large-scale nonlinear dynamical systems. Physica D, 406, 132401. DOI/OA/code: NV; bibliographic metadata identified in PCNO references.                                                                                         | Lift-and-learn operator inference, nonlinear dynamics. Uses variable lifting to expose useful reduced dynamics and physical structure. A candidate for coupling power and thermal state evolution through a reduced dynamical model instead of independently fitting each field's coefficients. Tags: `OPINF,ROM,PHYS,MULTI`. Provenance: PCNO backward reference; B.                                                                                                                                                                                  |
| 22 · 4/5 | Kobayashi, Kazuma; Alam, Syed Bahauddin (2024). Deep neural operator-driven real-time inference to enable digital twin solutions for nuclear energy systems. Scientific Reports, 14, 2101. DOI / OA. Code: NV.                                                                                                                                                     | DeepONet, nuclear neutron-transport fields, static source-to-flux operator. Uses PHITS-generated 2D neutron-flux distributions and spatial source inputs. Important direct nuclear evidence for function-to-field learning, but the published maze shielding example is not reactor kinetics or multiphysics transient prediction. UQ: NR. Tags: `NUC,DON,FIELD,STATIC`. Provenance: nuclear topic search; T.                                                                                                                                          |
| 23 · 4/5 | Ouyang, Weihang; Shin, Yeonjong; Liu, Si-Wei; Lu, Lu (2026). NOEM: efficient and scalable finite element method enabled by reusable neural operators. Nature Computational Science, 6, 417–429. DOI · OA manuscript · official code.                                                                                                                               | Neural-operator element method, hybrid FE/NO. Replaces expensive subdomain discretizations with learned operator elements assembled into a conventional FE variational framework. This is a different route from replacing the entire DIREWOLF solver and may better preserve FE compatibility. Not a demonstrated transient neutronics–thermal reactor surrogate. Tags: `FE,HYBRID,OPERATOR,PHYS`. Provenance: 2026 topic search; A.                                                                                                                  |
| 24 · 4/5 | Wen, Gege; Li, Zongyi; Azizzadenesheli, Kamyar; Anandkumar, Anima; Benson, Sally M. (2022). U-FNO—An enhanced Fourier neural operator-based deep-learning model for multiphase flow. Advances in Water Resources, 163, 104180. DOI · OA manuscript. Code: NV.                                                                                                      | U-FNO, structured-grid multiphase pressure/saturation fields. Combines Fourier operators with local U-shaped convolutional processing to improve sharp-front representation and data efficiency. Transferable to localized thermal gradients and heterogeneous material interfaces, but requires a grid mapping for native FE data. Tags: `FNO,MULTI,TRANS,DATA`. Provenance: PCNO backward reference; A.                                                                                                                                              |
| 25 · 4/5 | Ji, Jiahao; Wang, Yuanfeng; Wu, Chunbing; Li, Wei (2026). Physics-Regularized Heat-Source-Conditioned FNO-LA Surrogate for Coupled Neutronic–Thermal Field Prediction in a Steady-State Single-Rod Benchmark. Applied Sciences, 16, 8043. DOI / OA. Code: NV.                                                                                                      | Heat-source-conditioned FNO with linear attention, coupled source/temperature fields, fixed-grid steady-state single rod. Predicts heat source before conditioning the thermal decoder, and adds global heat-source and soft thermal penalties. A concrete alternative to three independent output heads. The authors explicitly limit its validation to a single-rod steady benchmark. UQ: bootstrap evaluation and initialization sensitivity, not calibrated predictive intervals. Tags: `NUC,FNO,MULTI,PHYS`. Provenance: 2026 topic search; A.    |
| 26 · 4/5 | Gao, Han; Sun, Luning; Wang, Jian-Xun (2021). PhyGeoNet: Physics-informed geometry-adaptive convolutional neural networks for solving parameterized steady-state PDEs on irregular domain. Journal of Computational Physics, 428, 110079. DOI/OA/code: NV; bibliographic metadata identified in PCNO references.                                                   | Geometry-adaptive PINN/CNN, irregular 2D domains, steady fields. Relevant as a comparison between mapped-grid physics losses and native-mesh operator methods. Does not solve the 100 s recurrent problem. Tags: `GEOM,PINN,FIELD,STATIC`. Provenance: PCNO backward reference; B.                                                                                                                                                                                                                                                                     |
| 27 · 4/5 | Zhu, Yinhao; Zabaras, Nicholas; Koutsourelakis, Phaedon-Stelios; Perdikaris, Paris (2019). Physics-constrained deep learning for high-dimensional surrogate modeling and uncertainty quantification without labeled data. Journal of Computational Physics, 394, 56–81. DOI/OA/code: NV; bibliographic metadata identified in PCNO references.                     | Physics-constrained probabilistic surrogate, high-dimensional PDE fields. Relevant to training with limited labels and estimating uncertain fields, rather than only deterministic reconstructions. The specific transfer to coupled reactor FE residuals requires independent validation. Tags: `PHYS,UQ,FIELD,DATA`. Provenance: PCNO backward reference; B.                                                                                                                                                                                         |
| 28 · 4/5 | Zhu, Yinhao; Zabaras, Nicholas (2018). Bayesian deep convolutional encoder–decoder networks for surrogate modeling and uncertainty quantification. Journal of Computational Physics, 366, 415–447. DOI/OA/code: NV; bibliographic metadata identified in PCNO references.                                                                                          | Bayesian encoder–decoder, field prediction and epistemic uncertainty. Supports an uncertainty-aware alternative to deterministic field decoding. Standard convolutional spatial representation is not inherently compatible with an irregular FE mesh. Tags: `AE,UQ,FIELD,GRID`. Provenance: PCNO backward reference; B.                                                                                                                                                                                                                               |
| 29 · 4/5 | Han, Xu; Gao, Han; Pfaff, Tobias; Wang, Jian-Xun; Liu, Li-Ping (2022). Predicting Physics in Mesh-reduced Space with Temporal Attention. ICLR. Author publication record. DOI/OA/code: direct links not independently resolved.                                                                                                                                    | Mesh-reduced dynamics with temporal attention. Relevant to combining spatial reduction with attention-based temporal evolution instead of retaining a pure LSTM. An especially useful bridge between POD-LSTM and full nodal graph dynamics. Detailed FE weighting and uncertainty treatment: NR. Tags: `LAT,ATTN,TRANS,FE`. Provenance: related MeshGraphNets research group; B.                                                                                                                                                                      |

The first six entries are particularly important because they directly connect reactor field prediction, controlled temporal behavior, irregular spatial representation and coupled thermal response. No one paper demonstrates all four simultaneously.

Evidence supporting the leading architectural distinctions: Li's reactor transient experiments&#x20;

[image](https://www.google.com/s2/favicons?domain=https://doi.org\&sz=32)

ScienceDirect

; PCNO's quadrature and gradient formulation&#x20;

[image](https://www.google.com/s2/favicons?domain=https://arxiv.org\&sz=32)

arxiv.org

+1

; Gong's two reactor ROM studies&#x20;

[image](https://www.google.com/s2/favicons?domain=https://www.tandfonline.com\&sz=32)

Get Access

+1

; the nuclear FNO–LSTM study&#x20;

[image](https://www.google.com/s2/favicons?domain=https://www.sciencedirect.com\&sz=32)

ScienceDirect

; and the 2026 irregular-mesh heat-conduction study&#x20;

[image](https://www.google.com/s2/favicons?domain=https://www.sciencedirect.com\&sz=32)

ScienceDirect

.



### What the PCNO paper actually establishes

PCNO deserves more attention than a generic point-cloud classification network. Its continuous operator layer is

\\[ f\_{\mathrm{out}}(x)=\sigma\left[ W\_\ell f(x)+b+ \sum_k\int\_\Omega e^{2\pi i k\cdot(x-y)/L}W_k f(y)\rho(y)\\,dy+ W_g\widetilde{\nabla}f(x) \right]. \\]

The formulation has three relevant properties.

First, its global integral is discretized using point-associated integration measures \\(d\Omega_i\\), rather than assuming every mesh node represents equal physical volume. Second, local gradients are computed through a least-squares reconstruction from neighboring point differences; the geometric pseudoinverse can be precomputed. Third, the authors investigate both uniform-volume integration and sampling-density-based integration, and explicitly note that density weighting tied to adaptive sampling requires a consistent adaptation strategy.

For DIREWOLF, the important distinction is that PCNO's quadrature weights are not automatically equivalent to the full consistent FE mass matrix. A nodal lumped-volume approximation may be adequate for some operators and losses, but that equivalence must be tested, especially across material interfaces and highly nonuniform elements.

The paper also reports greater memory use and training time than similarly sized FNOs, partly because of the differential message-passing operator. Its numerical demonstrations support irregular-mesh field learning, not a proven solution to controlled reactor rollout.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://arxiv.org\&sz=32)

arxiv.org

+3



## 3. Tier 2 extended library

These are additional method papers worth indexing. Tier 2 deliberately includes foundational numerical reduction, mesh-based learning, operator architectures, generalization, and UQ methods that can support a defensible DIREWOLF implementation.

For the entries discovered through PCNO's bibliography, the title, authors, year and venue are supported by that reference list, but publisher-level DOI verification was not completed for every entry. Those are explicitly marked `B`; they should not be treated as fully audited acquisition records.

| Rank / score | Paper, year, venue and acquisition                                                                                                                                                                                                                                                                                 | Method, representation and actual prediction target                                                                                           | DIREWOLF use, limitations and RAG tags                                                                                                                                       |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 30 · 4/5     | Antonello, Federico; Buongiorno, Jacopo; Zio, Enrico. Physics informed neural networks for surrogate modeling of accidental scenarios in nuclear power plants. 2023, Nuclear Engineering and Technology, 55, 3409–3416. DOI / OA.                                                                                  | PINN versus DNN; nuclear-battery loss-of-heat-sink scenario; time-dependent accident response. Spatial full-field capability not established. | Nuclear microreactor physics-loss precedent, not a replacement for 3D FE field prediction. Physics: soft residual constraints; UQ/code: NR/NV. `NUC,PINN,TRANS,PHYS`; S3, A. |
| 31 · 4/5     | Wang, Shenlong; Suo, Simon; Ma, Wei-Chiu; Pokrovsky, Andrei; Urtasun, Raquel. Deep Parametric Continuous Convolutional Neural Networks. 2018, CVPR. DOI. OA/code: NV.                                                                                                                                              | Parametric continuous convolutions on nonuniform spatial point representations; not a PDE surrogate or temporal solver.                       | Geometric learning precursor; useful for interpreting point-cloud convolution choices, not reactor dynamics. Physics/UQ: none demonstrated. `PC,GEOM`; S1, A.                |
| 32 · 4/5     | Benner, Peter; Gugercin, Serkan; Willcox, Karen. A Survey of Projection-Based Model Reduction Methods for Parametric Dynamical Systems. 2015, SIAM Review, 57, 483–531. DOI/publisher/OA: NV.                                                                                                                      | Projection-based ROM theory; reduced state spaces and parametric dynamics.                                                                    | Essential reference for reduced-system construction, stability and error decomposition. `ROM,POD,VV`; PCNO backward, B.                                                      |
| 33 · 4/5     | Chaturantabut, Saifon; Sorensen, Danny C. Nonlinear Model Reduction via Discrete Empirical Interpolation. 2010, SIAM Journal on Scientific Computing, 32, 2737–2764. DOI/OA: NV.                                                                                                                                   | DEIM; nonlinear term approximation in reduced coordinates.                                                                                    | Reduces the cost of evaluating nonlinear feedback terms in an intrusive or hybrid ROM. `ROM,DEIM,PHYS`; PCNO backward, B.                                                    |
| 34 · 4/5     | Carlberg, Kevin; Farhat, Charbel; Cortial, Julien; Amsallem, David. The GNAT Method for Nonlinear Model Reduction: Effective Implementation and Application to Computational Fluid Dynamics and Turbulent Flows. 2013, Journal of Computational Physics, 242, 623–647. DOI/OA: NV.                                 | Hyper-reduced nonlinear ROM; residual minimization and sampled residual evaluation.                                                           | Reference for physics-residual-preserving alternatives to purely learned POD dynamics. `ROM,GNAT,FE,VV`; PCNO backward, B.                                                   |
| 35 · 4/5     | Schmid, Peter J. Dynamic mode decomposition of numerical and experimental data. 2010, Journal of Fluid Mechanics, 656, 5–28. DOI/OA: NV.                                                                                                                                                                           | DMD; linear temporal evolution in learned modal coordinates.                                                                                  | Lightweight temporal baseline and modal stability diagnostic. `DMD,TRANS,ROM`; PCNO backward, B.                                                                             |
| 36 · 4/5     | Berkooz, Gal; Holmes, Philip; Lumley, John L. The Proper Orthogonal Decomposition in the Analysis of Turbulent Flows. 1993, Annual Review of Fluid Mechanics, 25, 539–575. DOI/OA: NV.                                                                                                                             | POD and modal energy representation.                                                                                                          | Foundation for POD truncation and physical-inner-product reasoning. `POD,ROM,VV`; PCNO backward, B.                                                                          |
| 37 · 4/5     | Willcox, Karen; Peraire, Jaime. Balanced Model Reduction via the Proper Orthogonal Decomposition. 2002, AIAA Journal, 40, 2323–2330. DOI/OA: NV.                                                                                                                                                                   | Balanced POD; input–output-oriented reduced modeling.                                                                                         | Motivates choosing modes for controlled response and QoI accuracy rather than snapshot energy alone. `POD,CTRL,QOI`; PCNO backward, B.                                       |
| 38 · 4/5     | Bhattacharya, Kaushik; Hosseini, Bamdad; Kovachki, Nikola B.; Stuart, Andrew M. Model Reduction and Neural Networks for Parametric PDEs. 2021, SMAI Journal of Computational Mathematics, 7, 121–157. DOI/OA: NV.                                                                                                  | Reduced representation plus neural approximation of parametric solution maps.                                                                 | Theoretical comparison point for POD-based and nonlinear approximation approaches. `ROM,OPERATOR,DATA`; PCNO backward, B.                                                    |
| 39 · 4/5     | Barnett, Joshua L.; Farhat, Charbel; Maday, Yvon. Neural-Network-Augmented Projection-Based Model Order Reduction for Mitigating the Kolmogorov Barrier to Reducibility of CFD Models. 2022 preprint. OA. Peer-reviewed version/DOI: NV.                                                                           | Neural augmentation of projection ROMs for difficult-to-reduce CFD fields.                                                                    | Candidate when a low-rank POD basis misses localized power or thermal features. `POD,LAT,ROM,FIELD`; PCNO backward, B.                                                       |
| 40 · 4/5     | Li, Zongyi; Kovachki, Nikola; Azizzadenesheli, Kamyar; Liu, Burigede; Bhattacharya, Kaushik; Stuart, Andrew; Anandkumar, Anima. Neural Operator: Graph Kernel Network for Partial Differential Equations. 2020 preprint. OA. Definitive publication/DOI: NV.                                                       | Graph-kernel integral operator for parametric PDE fields.                                                                                     | Mathematical precursor to GNO/GINO and quadrature-based spatial aggregation. `GNO,FE,OPERATOR`; PCNO backward, B.                                                            |
| 41 · 4/5     | Fortunato, Meire; Pfaff, Tobias; Wirnsberger, Peter; Pritzel, Alexander; Battaglia, Peter. Multiscale MeshGraphNets. 2022 preprint. Research-group publication index. DOI/OA direct file: NV.                                                                                                                      | Multiscale mesh-based message passing for simulation.                                                                                         | Addresses graph receptive-field and scalability limitations in large FE domains. `GNN,MULTISCALE,FE`; MeshGraphNets group, B.                                                |
| 42 · 4/5     | Kovachki, Nikola et al. Neural Operator: Learning Maps Between Function Spaces. 2023, Journal of Machine Learning Research. Full author list, DOI and direct publisher record not independently verified in this search.                                                                                           | Neural-operator theory and approximation framework.                                                                                           | Essential distinction between continuous operator approximation and discretized neural networks. `OPERATOR,THEORY,VV`; operator literature, B.                               |
| 43 · 4/5     | Goswami, Somdatta; Kontolati, Katiana; Shields, Michael D.; Karniadakis, George Em. Deep Transfer Operator Learning for Partial Differential Equations under Conditional Shift. 2022, Nature Machine Intelligence, 4, 1155–1164. DOI/OA: NV.                                                                       | Transfer operator learning under shifted PDE input conditions.                                                                                | Relevant to unseen control-history distributions; direct reactor OOD evidence not established. `DON,TRANSFER,OOD`; PCNO backward, B.                                         |
| 44 · 4/5     | Gao, Han; Kaltenbach, Sebastian; Koumoutsakos, Petros. Generative learning of the solution of parametric partial differential equations using guided diffusion models and virtual observations. 2025, CMAME, 435, 117654. DOI/OA: NV.                                                                              | Conditional generative PDE-field prediction using guided diffusion.                                                                           | Alternative for conditional field distributions and uncertainty; expensive sampling may limit real-time inference. `GEN,UQ,FIELD`; PCNO backward, B.                         |
| 45 · 4/5     | Liu, Xiaoyu; Lin, Hongtao; Liu, Xingli; Qian, Jianghong; Cai, Shengze; Fan, Hongguang; Gao, Qi. LAFlowNet: A dynamic graph method for the prediction of velocity and pressure fields in left atrium and left atrial appendage. 2024, Engineering Applications of Artificial Intelligence, 136, 108896. DOI/OA: NV. | Dynamic graph learning; distributed flow velocity and pressure.                                                                               | Transferable graph-field prediction ideas, though cardiac geometry/flow differs from reactor FE physics. `GNN,FIELD,TRANS`; PCNO backward, B.                                |
| 46 · 4/5     | Shen, Yiren; Needels, Jacob T.; Alonso, Juan J. VortexNet: A Graph Neural Network-Based Multi-Fidelity Surrogate Model for Field Predictions. 2025, AIAA SciTech, paper 0494. DOI/OA: NV.                                                                                                                          | Graph-based multifidelity field surrogate.                                                                                                    | Candidate for combining coarse and expensive high-fidelity simulations. `GNN,MF,FIELD,DATA`; PCNO backward, B.                                                               |
| 47 · 4/5     | Cao, Shuhao. Choose a Transformer: Fourier or Galerkin. 2021, NeurIPS, 24924–24940. DOI/OA: NV.                                                                                                                                                                                                                    | Fourier/Galerkin transformer formulations for PDE operator learning.                                                                          | Baseline for global attention versus spectral operator processing. `ATTN,OPERATOR,FIELD`; PCNO backward, B.                                                                  |
| 48 · 4/5     | Chen, Junfeng; Wu, Kailiang. Positional Knowledge Is All You Need: Position-Induced Transformer (PiT) for Operator Learning. 2024, ICML. DOI/OA: NV.                                                                                                                                                               | Position-informed transformer operator.                                                                                                       | Tests whether geometric positional encoding can substitute for expensive explicit graph construction. `ATTN,GEOM,OPERATOR`; PCNO backward, B.                                |
| 49 · 4/5     | Liu-Schiaffini, Miguel; Berner, Julius; Bonev, Boris; Kurth, Thorsten; Azizzadenesheli, Kamyar; Anandkumar, Anima. Neural Operators with Localized Integral and Differential Kernels. 2024 preprint. OA. Publication/DOI: NV.                                                                                      | Local integral and differential neural operators.                                                                                             | Particularly relevant to combining localized FE physics with nonlocal operator interactions. `OPERATOR,LOCAL,FE`; PCNO backward, B.                                          |
| 50 · 4/5     | Yin, Minglang; Charon, Nicolas; Brody, Ryan; Lu, Lu; Trayanova, Natalia; Maggioni, Mauro. DiMON: Learning Solution Operators of Partial Differential Equations on a Diffeomorphic Family of Domains. 2024 preprint. OA. Publication/DOI: NV.                                                                       | Geometry-family operator learning.                                                                                                            | Candidate if mesh variation is smooth and a consistent domain correspondence exists. `GEOM,DON,OPERATOR`; PCNO backward, B.                                                  |
| 51 · 4/5     | Xiao, Shanshan; Jin, Pengzhan; Tang, Yifa. Learning Solution Operators of PDEs Defined on Varying Domains via MIONet. 2024 preprint. OA. Publication/DOI: NV.                                                                                                                                                      | Multi-input operator learning on varying domains.                                                                                             | Relevant to jointly conditioning on geometry, material fields and prescribed controls. `DON,GEOM,MULTI`; PCNO backward, B.                                                   |
| 52 · 3/5     | Cao, Wenbo; Song, Jiahao; Zhang, Weiwei. Solving high-dimensional parametric engineering problems for inviscid flow around airfoils based on physics-informed neural networks. 2024, Journal of Computational Physics, 516, 113285. DOI/OA: NV.                                                                    | Physics-informed flow-field approximation on parametric geometry.                                                                             | Reference for residual-based field training and geometric generalization, not reactor transients. `PINN,FIELD,GEOM`; PCNO backward, B.                                       |
| 53 · 3/5     | Qi, Kai; Sun, Jian. Gabor-Filtered Fourier Neural Operator for Solving Partial Differential Equations. 2024, Computers & Fluids, 274, 106239. DOI/OA: NV.                                                                                                                                                          | Gabor-filtered spectral operator; PDE fields.                                                                                                 | Alternative spectral representation for multiscale spatial structure. `FNO,SPECTRAL,FIELD`; PCNO backward, B.                                                                |
| 54 · 3/5     | Tran, Alasdair; Mathews, Alexander; Xie, Lexing; Ong, Cheng Soon. Factorized Fourier Neural Operators. 2021 preprint. OA. Publication/DOI: NV.                                                                                                                                                                     | Factorized Fourier operator; structured-grid PDE fields.                                                                                      | Lower-cost FNO variant to benchmark if a regular latent grid is adopted. `FNO,SCALE,GRID`; PCNO backward, B.                                                                 |
| 55 · 3/5     | He, Juncai; Liu, Xinliang; Xu, Jinchao. MGNO: Efficient Parameterization of Linear Operators via Multigrid. 2023 preprint. OA. Publication/DOI: NV.                                                                                                                                                                | Multigrid-inspired operator parameterization.                                                                                                 | Hierarchical alternative for large spatial fields and nonlocal propagation. `OPERATOR,MULTISCALE`; PCNO backward, B.                                                         |
| 56 · 4/5     | Guo, Mengwu; Hesthaven, Jan S. Reduced order modeling for nonlinear structural analysis using Gaussian process regression. 2018, CMAME, 341, 807–826. DOI/OA: NV.                                                                                                                                                  | Gaussian-process reduced-coordinate surrogate.                                                                                                | Data-efficient baseline with predictive uncertainty for POD coefficient maps. `POD,GP,UQ,DATA`; PCNO backward, B.                                                            |
| 57 · 3/5     | Williams, Matthew O.; Kevrekidis, Ioannis G.; Rowley, Clarence W. A Data–Driven Approximation of the Koopman Operator: Extending Dynamic Mode Decomposition. 2015, Journal of Nonlinear Science, 25, 1307–1346. DOI/OA: NV.                                                                                        | Extended DMD/Koopman approximation of nonlinear dynamics.                                                                                     | Temporal reduced-state baseline, useful for stability and spectral diagnostics. `KOOP,ROM,TRANS`; PCNO backward, B.                                                          |
| 58 · 3/5     | Rowley, Clarence W.; Mezić, Igor; Bagheri, Shervin; Schlatter, Philipp; Henningson, Dan S. Spectral analysis of nonlinear flows. 2009, Journal of Fluid Mechanics, 641, 115–127. DOI/OA: NV.                                                                                                                       | Koopman/spectral flow analysis.                                                                                                               | Foundational reference for interpreting reduced dynamical modes and long-time behavior. `KOOP,DMD,TRANS`; PCNO backward, B.                                                  |
| 59 · 4/5     | Zhang, Yueyao; Zhang, Qian; Wan, Chenghui; Bai, Jiahe; He, Mingtao; Chen, Xiangdong. A Hybrid Physics-informed Surrogate Model Approach for Xenon-induced Power Oscillation in Nuclear Reactor. 2025, Atomic Energy Science and Technology. Publisher / DOI. OA: publisher page; code: NV.                         | Physics-informed hybrid surrogate for xenon-driven reactor power oscillation dynamics. Spatial output resolution not verified.                | Nuclear long-timescale feedback example, but not direct evidence for 0–100 s coupled 3D FE prediction. `NUC,TRANS,PHYS,CTRL`; nuclear topic search, A.                       |

For entries 32–58 without an explicit OA URL, no legitimate OA source was established in this search; this does not prove that none exists. For those same entries, unless specified, official code, predictive UQ, physics enforcement details, and full input/output tensor definitions remain unverified. The DOI field is intentionally left unresolved rather than filled using guesses.

The Tier 2 citation-chain source is PCNO's published reference list, particularly its ROM, neural-operator, geometry and graph-learning citations.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://arxiv.org\&sz=32)

arxiv.org

+1

&#x20;The Antonello paper is independently supported by its publisher record&#x20;

[image](https://www.google.com/s2/favicons?domain=https://www.sciencedirect.com\&sz=32)

ScienceDirect

, and the xenon paper by its journal record&#x20;

[image](https://www.google.com/s2/favicons?domain=https://yznkxjs.xml-journal.net\&sz=32)

yznkxjs.xml-journal.net

.



## 4. Tier 3 — Useful context, not core downloads

These are legitimate related works, but their demonstrated outputs or problem formulations are too far from DIREWOLF's main full-field transient objective to justify higher priority.

| Paper                                                                                                                                                                                                                   | Why lower priority                                                                                                                                                                                                                                                 |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Jin, Ik Jae; Bang, In Cheol (2026). Fuel surrogate temperature prediction for microreactor using heat pipe under transient conditions. Applied Thermal Engineering, 303, 132596. DOI                                    | Very close reactor technology and LSTM–Transformer temporal modeling, including unseen sequential transients and MC dropout. However, it estimates fuel temperature from accessible measurements rather than reconstructing the three distributed DIREWOLF fields. |
| Rivas, Andy; Delipei, Gregory Kyriakos; Hou, Jason (2024). Modeling a generic Pebble Bed High-Temperature Gas-Cooled Reactor to perform load-following using Simulink. Nuclear Engineering and Design, 428, 113506. DOI | Useful control/load-following context, but the surrogate is primarily system-level rather than high-dimensional spatial-field prediction.                                                                                                                          |
| Che et al. (2022). Machine learning-assisted surrogate construction for full-core fuel performance analysis. Annals of Nuclear Energy, 168, 108905. DOI                                                                 | Relevant to large-scale fuel-performance screening and data efficiency, but its emphasis on selected performance quantities is less directly transferable than full-field neural-operator work.                                                                    |
| Unresolved ScienceDirect record: `S0306454926007425`                                                                                                                                                                    | Keep as an unresolved seed identifier. No defensible bibliographic entry can be assigned.                                                                                                                                                                          |

The first two entries are supported by publisher abstracts describing their actual prediction targets.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://www.sciencedirect.com\&sz=32)

ScienceDirect

+1



## 5. Technical synthesis: ten DIREWOLF questions

### Q1. What does the nuclear literature actually establish?

The strongest direct nuclear precedent is Li et al. (2024) because it predicts time-dependent spatial reactor power under reactivity disturbances. Its simplified 3D test has only 29 active power zones, however, and its results do not establish accuracy on millions of FE degrees of freedom or simultaneous thermal fields.

Gong et al. (2022) demonstrate reconstructed reactor power/neutron-flux distributions using reduced bases, but their principal contribution is a parameter-to-field surrogate rather than an independently validated 100 s recurrent model.

Zhang et al. (2025) provides valuable evidence for combining temporal neural networks with operator layers to predict nuclear thermal/mechanical fields. Its reference physics and spatial dimensionality differ substantially from DIREWOLF.

The 2026 Ji study directly addresses heat-source-conditioned thermal prediction, but is steady-state and single-rod. Consequently, a validated native-FE, coupled, controlled 3D reactor transient neural operator remains an open research target in the literature examined.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://doi.org\&sz=32)

ScienceDirect

+3



### Q2. Should DIREWOLF retain POD?

Yes, as the principal benchmark and probably as one component of the strongest near-term architecture.

For FE snapshots \\(x_j\\), define the centered snapshot matrix \\(X\\) and the appropriate FE mass matrix \\(M\\). A mass-orthonormal POD basis can be constructed from

\\[ M^{1/2}X=U\Sigma V^\top,\qquad \Phi_r=M^{-1/2}U_r,\qquad \Phi_r^\top M\Phi_r=I. \\]

Reduced coefficients are

\\[ a_r(t)=\Phi_r^\top M\bigl(x(t)-\bar x\bigr). \\]

If reconstruction remains in the POD span, the squared FE error decomposes orthogonally:

\\[ \\|x-\hat x\\|\_M^2 = \underbrace{\\|x-P_rx\\|\_M^2}\_{\text{irreducible POD truncation error}} + \underbrace{\\|P_rx-\hat x\\|\_M^2}\_{\text{reduced-state prediction error}}. \\]

This gives a particularly useful diagnostic: no temporal architecture can remove the first term while using the same fixed linear POD basis.

Hesthaven–Ubbiali, Peherstorfer–Willcox, Lee–Carlberg and Qian et al. motivate the comparison among learned coefficient maps, operator inference, nonlinear manifolds and physically structured reduced dynamics. Their relative performance for DIREWOLF remains to be measured.

### Q3. Which methods genuinely support irregular FE meshes?

The strongest candidates are PCNO, MeshGraphNets, GINO, Sp²GNO and geometry-aware transformers. They support irregular spatial representations in different ways.

- PCNO uses point-associated integration measures and least-squares gradients.
- MeshGraphNets operates on mesh connectivity through message passing.
- GINO uses graph-based transforms between irregular geometry and a regular latent grid.
- Sp²GNO combines spatial and spectral graph operations.
- Transolver aggregates points into learned physics-state slices.

None of these automatically preserves a consistent FE \\(L^2\\) inner product. Even when an architecture can accept irregular nodes, the loss, material integration, boundary conditions and evaluation metrics must still use the correct FE geometry.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://arxiv.org\&sz=32)

arxiv.org

+4



### Q4. How should prescribed control-drum trajectories enter the model?

The input should represent the control history as a function, not merely the instantaneous drum position.

For a known prescribed trajectory, useful conditioning variables include drum angle \\(\theta_d(t)\\), angular velocity \\(\dot\theta_d(t)\\), the initial physical state, and—when known at prediction time—the planned future control trajectory.

Three formulations deserve comparison:

\\[ \hat a(t+\Delta t) =F\_\theta(a(t),\theta_d(t),\dot\theta_d(t)), \\]

\\[ \hat a(t\_{1:T}) =G\_\theta(a_0,\theta_d(t\_{0:T})), \\]

\\[ \hat u(x,t) =\mathcal G\_\theta[u_0,\theta_d(\cdot)]\(x,t). \\]

These correspond to a recurrent state model, a direct sequence model and a coordinate-query operator.

Li et al. (2024) establishes the relevance of sequential reactivity disturbances; DeepONet establishes a framework for function-conditioned coordinate queries. Applying the latter to drum histories is a research hypothesis, not a result established by those papers.

### Q5. Should the three fields be predicted jointly?

The most defensible comparison is between independent decoders, a shared latent model with separate field heads, and a physics-ordered conditional model.

Candidate shared-latent architecture. This is a proposed DIREWOLF experiment, not a published validated reactor model.

A shared representation may learn cross-field correlations. But different physical time scales and field regularities could make a single latent bottleneck harmful. The Ji et al. (2026) heat-source-conditioned architecture provides a useful causal design precedent, while Zhang et al. (2025) demonstrates multiple thermal/mechanical outputs driven by power histories. Neither settles whether joint modeling will outperform independent FE-aware POD bases for DIREWOLF.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://www.mdpi.com\&sz=32)

MDPI

+1



### Q6. What is known about long-horizon rollout stability?

The key distinction is one-step accuracy versus closed-loop accuracy.

A model can predict the next snapshot accurately when conditioned on true previous states and still drift badly when fed its own predictions. Brandstetter et al. explicitly address autoregressive stability in learned PDE solvers. Yuan et al. (2026) evaluates autoregressive temperature-field prediction, including unstructured-grid variants.

For DIREWOLF, evaluate the complete 0–100 s trajectory with no hidden use of reference future states. Compare:

- one-step teacher-forced predictions;
- fully autoregressive rollout;
- direct trajectory prediction;
- multi-step trained rollout;
- periodic correction only when actual online measurements would be available.

Direct trajectory prediction removes the particular mechanism of stepwise error accumulation, but it can still produce inaccurate or physically inconsistent trajectories. It is not automatically more stable or better at extrapolating beyond the training horizon.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://www.microsoft.com\&sz=32)

Microsoft Research

+1



### Q7. How should physics consistency be enforced?

Distinguish three levels of physics integration.

Soft regularization: penalize PDE residuals, boundary violations, power imbalance or thermal inconsistency. PINO and physics-informed DeepONet provide methodological precedents. A small training residual does not guarantee exact conservation.

Structure-preserving reduced dynamics: use physically motivated state variables, operators, positivity constraints or known coupling terms. Operator inference and Lift & Learn are relevant foundations.

Discrete conservation or constrained correction: enforce selected integral constraints algebraically or through a constrained projection. This is a proposed DIREWOLF extension, not a conservation property established for PCNO, FNO or MeshGraphNets.

For a nodal power-density vector \\(q(t)\\), define

\\[ P(t)=g^\top q(t),\qquad g_i=\int\_{\Omega\_{\mathrm{fuel}}}N_i(x)\\,dV. \\]

Here \\(N_i\\) are FE shape functions. The integration vector \\(g\\) is not generally the vector of unweighted nodal counts.

A useful loss is

\\[ \mathcal L_P= \frac{1}{T}\sum_t \left( \frac{\hat P(t)-P(t)}{P\_{\mathrm{scale}}} \right)^2. \\]

For thermal fields, an energy-balance residual must include heat capacity, heat deposition, heat transfer, boundary fluxes and any other terms actually represented by the high-fidelity physics. A simple penalty on \\(T\_{\mathrm{fuel}}-T\_{\mathrm{mod}}\\) would not constitute a physical energy balance.

### Q8. What uncertainty estimates are credible?

For a safety-relevant field surrogate, uncertainty should be assessed at three distinct levels:

1. Epistemic uncertainty: variation due to limited training data or uncertain model parameters, estimated with ensembles, Bayesian approximations or related methods.
2. Aleatoric or input uncertainty: propagated uncertainty in uncertain boundary conditions, material parameters, or controls, if these are modeled as random variables.
3. Model discrepancy: systematic differences between the surrogate, the high-fidelity solver and physical reality.

An ensemble's standard deviation is not automatically a calibrated predictive interval. MC dropout, as used in the 2026 heat-pipe microreactor temperature study, is a useful comparison method but does not by itself establish reliable OOD coverage.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://www.sciencedirect.com\&sz=32)

ScienceDirect



DIREWOLF should report empirical coverage and interval width for spatial fields, integrated power, peak temperatures and selected safety-relevant QoIs, separately for in-distribution and unseen control families.

### Q9. What is the best route to data efficiency?

Start with inexpensive improvements to the existing reduced representation before generating large new simulation campaigns.

The literature supports investigating operator inference, reduced-coordinate neural models, multifidelity field surrogates and physics-informed training. U-FNO provides an example of improved data utilization in a non-nuclear multiphase problem, while NOEM offers a fundamentally different strategy using reusable learned elements.

The research hypothesis is that DIREWOLF can achieve better accuracy per expensive high-fidelity transient by combining mass-weighted reduction, reduced dynamics and uncertainty-guided sampling than by training a large full-field neural operator from scratch.

This should be measured in high-fidelity simulation runs, training GPU-hours, peak memory, inference latency and accuracy—not only in neural-network parameter count.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://www.sciencedirect.com\&sz=32)

ScienceDirect

+1



### Q10. What constitutes credible V&V?

A credible evaluation must distinguish interpolation among sampled transients from generalization to new physical conditions.

At minimum, use held-out complete control trajectories, not randomly separated snapshots from the same trajectory. Report mesh-dependent errors using physical FE weights, time-dependent engineering QoIs, worst-case errors, long-horizon behavior, uncertainty coverage and sensitivity to mesh resolution.

Verification of surrogate code and numerical preprocessing is distinct from validation against the high-fidelity solver, and both are distinct from validation of the high-fidelity solver against physical evidence. Surrogate agreement with a simulation does not independently validate reactor physics.

## 6. Architecture comparison for DIREWOLF

The assessment below combines published evidence with explicitly identified research hypotheses. `M` denotes a consistent FE mass matrix, while `W` denotes lumped nodal or quadrature weights.

| Architecture                                     | Large irregular 3D FE meshes / weighting                                                                             | Control histories and three coupled fields                                                                   | 100 s rollout                                                                    | Data, compute, physics and UQ assessment                                                                                                                              |
| ------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Current FE-aware POD-LSTM                        | Native fixed FE basis; direct `M` support                                                                            | Excellent input/output dimensional reduction; controls enter recurrent model; separate or joint coefficients | Error accumulation possible                                                      | Lowest implementation risk; cheap inference; truncation floor. Add ensembles and QoI constraints. Direct DIREWOLF baseline.                                           |
| Improved POD sequence model / operator inference | Same FE compatibility and `M` as baseline                                                                            | Controls as forcing functions; multiple field coefficients or coupled reduced states                         | Direct-sequence, recurrent or inferred dynamics                                  | Relatively low training cost; interpretable dynamics possible; still limited by POD basis. Supported by Peherstorfer, Qian, Han.                                      |
| Nonlinear AE latent dynamics                     | Requires FE-aware encoder/decoder or mapping; `M` must be implemented in losses                                      | Supports nonlinear coupled latent states and control-conditioned evolution                                   | Latent drift remains possible                                                    | More training and decoder complexity; potentially reduces POD truncation limitations. Lee–Carlberg and Gong support investigation.                                    |
| PCNO                                             | Native irregular point clouds; explicit integration measures `W`; consistent `M` not inherent                        | Can condition on spatial inputs and control-history encodings; three-field transient coupling unproven       | No demonstrated DIREWOLF-like rollout                                            | Promising FE-native operator; substantial full-field memory and training requirements; no inherent conservation/UQ. Research hypothesis for coupled reactor dynamics. |
| GNO / MeshGraphNets                              | Native graph/mesh topology; `M` or `W` must be added explicitly                                                      | Control signals can be broadcast or spatially encoded; multi-field node states feasible                      | Published autoregressive PDE/mesh precedents                                     | Edge count, graph depth and long-range communication are concerns. Physics losses/ensembles require additions.                                                        |
| FNO / U-FNO                                      | Standard FFT requires structured latent grid; native `M` not supported automatically                                 | Control history can be represented as channels/functions; multi-output fields feasible                       | Demonstrated time-dependent PDE applications, not DIREWOLF OOD stability         | Fast spectral operations; interpolation/deformation error and fine-feature loss are concerns. Strong baseline after mapping.                                          |
| DeepONet / physics-informed DeepONet             | Arbitrary output query coordinates; input sensors/branch representation must be designed; `M` in training/evaluation | Natural functional control conditioning and multi-field coordinate queries                                   | Direct space-time queries avoid autoregressive feedback but not prediction error | Branch representation and query count affect cost; soft PDE residuals possible; reactor evidence is largely static-field.                                             |
| Hybrid POD/neural operator                       | POD preserves FE-aware reduced coordinates; operator can act on latent fields or residual corrections                | Controlled reduced dynamics plus joint spatial correction                                                    | Can compare direct and recurrent forms                                           | Attractive compromise in data and memory; coupling and conservation still need testing. Research hypothesis, supported indirectly by ROM and operator papers.         |

Practical ranking for implementation experiments: improve the existing POD dynamics first; test a hybrid reduced-state model next; benchmark PCNO or a mesh graph model against it on a representative FE subset; and include FNO/DeepONet as controlled alternatives rather than assuming either is intrinsically superior.

This ranking reflects the strength of available evidence and the engineering cost of each approach, not a published head-to-head result on DIREWOLF.

## 7. Concrete DIREWOLF research experiments

Each experiment below assumes the same high-fidelity reference simulations and a reproducible, trajectory-level data split unless otherwise stated.

| Study                                                   | Research hypothesis and experiment                                                                                                                                                                                                      | Baselines, evaluation and tradeoffs                                                                                                                                                                                                                     | Supporting papers / publication potential                                                                                                                 |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| E1. FE-weighted objectives                              | Compare unweighted nodal MSE, lumped-volume weighting and consistent-mass-matrix losses for POD-LSTM and an irregular-mesh model. Use the same FE snapshots, element geometry and physical-field scaling.                               | Report FE-relative \\(L^2\\), material-wise errors, peak temperatures, integrated power, and sensitivity to mesh refinement. Sparse `M` operations add cost but should be manageable compared with full-field neural training.                          | Zeng 2025; Hesthaven–Ubbiali 2018; Berkooz 1993. Novelty: quantify whether discretization-aware training materially improves reactor-field QoIs.          |
| E2. POD truncation versus temporal error                | Construct field-specific POD error curves and separate oracle reconstruction error from predicted-coefficient error. Compare LSTM, temporal attention and operator inference across identical reduced dimensions.                       | Test ranks such as 8, 16, 32, 64 and 128 where the available snapshot rank permits. Evaluate error at every time, near control events and at 100 s. Operator inference may be cheaper and more interpretable; attention may require more training data. | Gong 2022; Peherstorfer–Willcox 2016; Qian 2020; Han 2022. Novelty: establish the actual error bottleneck in DIREWOLF.                                    |
| E3. Direct trajectory versus autoregressive prediction  | Compare one-step POD-LSTM, multi-step-trained recurrent models, a direct reduced-trajectory decoder and a control-conditioned DeepONet. Use the entire known drum trajectory as an input only when it would be available in deployment. | Hold out complete control-history families. Measure 0–100 s FE error, time-to-peak error, drift, inference latency and memory. Direct models trade recurrent error accumulation for potentially larger sequence-model complexity.                       | Li 2024; Brandstetter 2022; Wang et al. 2021 physics-informed DeepONet. Novelty: controlled transient rollout benchmark.                                  |
| E4. Coupled versus separate field surrogates            | Compare three independent POD dynamics models, a shared latent model with separate decoders, and a power-conditioned thermal model that predicts `power_density` before `Tfuel` and `Tmod`.                                             | Preserve separate material domains and field normalization. Evaluate cross-field correlations, integrated power, temperature peaks and thermal lag after drum motion. Joint models may improve coupling but can also transfer errors between heads.     | Zhang 2025; Ji 2026; Gong 2022 SVD-AE. Novelty: identify whether explicit physical dependency improves coupled surrogate fidelity.                        |
| E5. Native-FE PCNO versus MeshGraphNets                 | Train PCNO and a mesh-graph surrogate on the same nodal fields and control inputs. Compare with POD-LSTM and, if feasible, GINO. Use element-derived quadrature weights, node coordinates, material identifiers and FE connectivity.    | Evaluate on held-out transients and, separately, alternative mesh resolutions. Report accuracy per GPU-hour, peak VRAM, inference time, edge count and sensitivity to nodal density. Full-field methods may be substantially more expensive.            | Zeng 2025; Pfaff 2021; Li et al. GINO 2023; Sarkar–Chakraborty 2025. Novelty: controlled native-FE reactor operator benchmark.                            |
| E6. Unseen drum trajectories and calibrated uncertainty | Train on selected drum trajectory families and test on held-out ramps, reversals, dwell sequences, rates and combinations. Fit ensembles for POD-LSTM and the strongest competing architecture.                                         | Evaluate field error, integrated power, peak temperature, ensemble spread, empirical interval coverage and selective prediction under OOD conditions. Ensemble inference increases computational cost roughly with ensemble size.                       | Goswami 2022; Zhu–Zabaras 2018; Gong 2022. Novelty: OOD reliability benchmark for prescribed-control reactor transients.                                  |
| E7. Multifidelity active learning                       | Combine coarse-mesh or simplified-physics simulations with selected expensive high-fidelity trajectories. Choose new trajectories using ensemble disagreement, predicted QoI error or physics residual indicators.                      | Compare random sampling against active acquisition at equal high-fidelity simulation budgets. Track field accuracy, peak-temperature error and integrated-power error per expensive run. Coarse-model bias must be monitored.                           | Shen et al. 2025 VortexNet; Wen et al. 2022 U-FNO; Ouyang et al. 2026 NOEM. Novelty: simulation-budget-aware surrogate development.                       |
| E8. Physics-constrained field reconstruction            | Add integral-power and thermal-energy consistency penalties to POD or operator predictions; compare with an optional constrained correction that exactly enforces selected linear integrals.                                            | Measure field error before and after correction, integrated power, thermal energy balance, negative-power violations and computational overhead. Enforcing one integral must not be mistaken for satisfying the full PDE.                               | Wang et al. 2021 physics-informed DeepONet; Li et al. PINO; Ji et al. 2026; Qian et al. 2020. Novelty: physically auditable full-field reactor surrogate. |
| E9. Discretization-transfer verification                | Train PCNO, GINO or a graph operator using one or several FE resolutions, then test on unseen refined/coarsened meshes representing the same physical conditions. Separate geometric interpolation error from model error.              | Use a common continuous FE reference, element quadrature and mesh-convergence studies. Report FE norms and material-wise conservation, not raw nodal MSE. Training on several meshes increases preprocessing and data costs.                            | Zeng 2025; Li et al. GINO 2023; Li et al. Geo-FNO 2023. Novelty: empirical test of discretization transfer on nuclear multiphysics fields.                |

### Recommended common evaluation metrics

Use these consistently across all nine experiments.

FE field accuracy

\\[ \epsilon_f(t)= \frac{\\|\hat u_f(t)-u_f(t)\\|\_{M_f}} {\\|u_f(t)\\|\_{M_f}+\varepsilon} \\]

Report per field and material region, not only a global average.

Integrated power error

\\[ \epsilon_P(t)= \frac{|\hat P(t)-P(t)|} {|P(t)|+P\_\epsilon} \\]

Use physical volume integration, including appropriate FE shape functions.

Thermal peak error

\\[ e\_{T,\max}(t)= |\max_x\hat T(x,t)-\max_xT(x,t)| \\]

Also compare the location and timing of peaks.

Long-horizon error

\\[ E_f=\frac{1}{T}\int_0^T\epsilon_f(t)\\,dt \\]

Include the final-time and worst-time errors, not just the mean.

For every model, additionally record the complete inference wall time, training cost, peak GPU memory, number of high-fidelity training trajectories, and worst-case error on held-out control families. A fast model that misses an important thermal peak should not be preferred solely because its average field error is small.

## 8. Machine-readable acquisition manifest

The following control copies a 59-entry CSV acquisition manifest covering both tiers. It includes ranking, verified DOI where available, acquisition URL, legitimate OA source where established, official code where verified, and RAG tags. Blank links indicate unresolved metadata rather than a claim that the resource does not exist.

This is a copyable CSV export, not a separately generated `.csv` or `.xlsx` attachment. The fuller methodological annotations remain in the bibliography above.

&#x20;Copy 59-entry CSV

Save the copied text as `direwolf_literature_acquisition.csv`.

## 9. Search accounting and remaining evidence gaps

The searches actually conducted included direct seed-identifier and DOI lookups; publisher, institutional repository and preprint searches; nuclear transient and multiphysics topic searches; recent 2024–2026 operator searches; and related-author/group discovery.

Backward citation chaining was performed selectively. PCNO's accessible reference list was examined and used to identify numerous ROM, operator, geometry and graph-learning papers. The Li et al. (2024) reactor transient article's accessible references were also examined.

Forward citation chaining was limited. A later neutron-diffusion FE article was identified citing Gong et al. (2022), and a 2025 nuclear conference manuscript independently referenced Gong and Antonello. These are confirmed citation relationships, but they do not constitute an exhaustive forward-citation graph.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://www.sciencedirect.com\&sz=32)

ScienceDirect

+1



The main limitations are:

- The unresolved `S0306454926007425` identifier has no verified bibliographic identity from the sources accessed.
- IEEE Xplore restricted direct retrieval of the first seed, although its metadata was established through an institutional record.
- Several Elsevier pages exposed abstracts or cached article text but blocked direct full-text retrieval.
- Many Tier 2 entries are bibliography-verified only; their definitive DOIs, OA copies, code and detailed methods require further verification.
- No exhaustive Scopus, Web of Science, Semantic Scholar or OpenAlex citation graph was retrieved.
- The strongest PCNO technical conclusions are supported by inspected manuscript sections, but full-text examination of all 59 entries was not completed.
- No independent reproduction of numerical results, code execution or comparison against DIREWOLF simulation data was performed.

The seed records can be cross-checked against the institutional CVPR record&#x20;

[image](https://www.google.com/s2/favicons?domain=https://experts.illinois.edu\&sz=32)

Illinois Experts

, nuclear publisher records&#x20;

[image](https://www.google.com/s2/favicons?domain=https://www.sciencedirect.com\&sz=32)

ScienceDirect

+2

&#x20;and the PCNO publisher record&#x20;

[image](https://www.google.com/s2/favicons?domain=https://www.sciencedirect.com\&sz=32)

ScienceDirect

.



## 10. Research conclusion

The resulting library contains 29 Tier 1 papers, 30 Tier 2 papers and three identified Tier 3 papers, plus one unresolved seed identifier. It is a substantive acquisition shortlist, but not all 59 Tier 1/2 records meet the same metadata-verification standard. The Tier 2 bibliographic gaps should be retained explicitly during RAG ingestion.

Three conclusions are supported strongly enough to guide DIREWOLF experiments.

First, the existing FE-aware POD-LSTM is a serious baseline, not an obsolete architecture. Its spatial compression, physical weighting and low inference cost are significant advantages. Its weaknesses—basis truncation, temporal drift and potentially weak cross-field coupling—are measurable and should be isolated before replacing it.

Second, PCNO and mesh/graph operators are the strongest candidates for removing the fixed linear-basis limitation while retaining irregular spatial representations. Their relevance is supported by actual computational mechanics demonstrations, but their ability to predict coupled 3D reactor transients over 100 seconds remains a research hypothesis.

Third, the most promising near-term contribution may be a physically constrained hybrid reduced model: retain FE-aware projection, improve control-conditioned latent dynamics, and introduce selective nonlinear or operator-based field corrections, with explicit power/thermal consistency and calibrated uncertainty.

The highest-value initial experiments are E1, E2, E3 and E4. They establish the actual error floor and coupling behavior of the existing pipeline. E5 and E9 then provide a defensible basis for deciding whether the additional cost of native-mesh neural operators is justified.

The publication opportunity is not simply applying a newer neural architecture to reactor data. It is demonstrating, under controlled and reproducible conditions, which architecture provides the best FE-consistent field accuracy, long-horizon reliability, multiphysics consistency and simulation-data efficiency for a heat-pipe-cooled microreactor.