# DIREWOLF literature corpus validation report

Generated from the Deep Research outputs supplied in the ChatGPT project conversation. Literature cutoff: **October 7, 2026**.

## Record accounting

- Ranked records ingested: **59** (29 Tier 1, 30 Tier 2)
- Records with a DOI explicitly verified in the supplied acquisition manifest: **16**
- Records with a legitimate OA URL recorded in the supplied manifest: **23**
- Records with an official code URL recorded in the supplied manifest: **7**
- Records without parsed author metadata from the review: **0**
- Records without parsed year metadata from the review: **0**
- Duplicate ranked records silently removed: **0**

## Verification policy

This repository does **not** convert missing metadata into guessed metadata. DOI fields are populated only when the source acquisition manifest labeled them verified. Author/year/venue fields are parsed from the human-readable ranked bibliography in the supplied literature review. Publisher, OA, and code URLs are carried forward from the manifest.

The original Deep Research review uses evidence levels `T`, `A`, and `B`:

- `T`: substantive technical sections inspected.
- `A`: publisher abstract/metadata examined.
- `B`: bibliographic reference identified, but detailed methodology not reviewed.

These levels are retained where they could be parsed from the review text.

## DOI status

**43 records do not have a DOI verified in the supplied manifest.** Some are conference papers or preprints and may legitimately lack a DOI; others need a later metadata-verification pass. Missing DOI is therefore recorded as unresolved, not as “no DOI exists.”

### DOI-unresolved ranked records

- DW-LIT-0007 (rank 7): Geometry-Informed Neural Operator for Large-Scale 3D PDEs
- DW-LIT-0008 (rank 8): Learning Mesh-Based Simulation with Graph Networks
- DW-LIT-0010 (rank 10): Message Passing Neural PDE Solvers
- DW-LIT-0011 (rank 11): Transolver: A Fast Transformer Solver for PDEs on General Geometries
- DW-LIT-0012 (rank 12): Transolver++: An Accurate Neural Solver for PDEs on Million-Scale Geometries
- DW-LIT-0013 (rank 13): Fourier Neural Operator with Learned Deformations for PDEs on General Geometries
- DW-LIT-0014 (rank 14): Fourier Neural Operator for Parametric Partial Differential Equations
- DW-LIT-0017 (rank 17): Physics-Informed Neural Operator for Learning Partial Differential Equations
- DW-LIT-0018 (rank 18): Non-intrusive reduced order modeling of nonlinear problems using neural networks
- DW-LIT-0019 (rank 19): Data-driven operator inference for nonintrusive projection-based model reduction
- DW-LIT-0020 (rank 20): Model reduction of dynamical systems on nonlinear manifolds using deep convolutional autoencoders
- DW-LIT-0021 (rank 21): Lift & Learn: Physics-informed machine learning for large-scale nonlinear dynamical systems
- DW-LIT-0026 (rank 26): PhyGeoNet: Physics-informed geometry-adaptive convolutional neural networks for solving parameterized steady-state PDEs on irregular domain
- DW-LIT-0027 (rank 27): Physics-constrained deep learning for high-dimensional surrogate modeling and uncertainty quantification without labeled data
- DW-LIT-0028 (rank 28): Bayesian deep convolutional encoder–decoder networks for surrogate modeling and uncertainty quantification
- DW-LIT-0029 (rank 29): Predicting Physics in Mesh-reduced Space with Temporal Attention
- DW-LIT-0032 (rank 32): A Survey of Projection-Based Model Reduction Methods for Parametric Dynamical Systems
- DW-LIT-0033 (rank 33): Nonlinear Model Reduction via Discrete Empirical Interpolation
- DW-LIT-0034 (rank 34): The GNAT Method for Nonlinear Model Reduction: Effective Implementation and Application to Computational Fluid Dynamics and Turbulent Flows
- DW-LIT-0035 (rank 35): Dynamic mode decomposition of numerical and experimental data
- DW-LIT-0036 (rank 36): The Proper Orthogonal Decomposition in the Analysis of Turbulent Flows
- DW-LIT-0037 (rank 37): Balanced Model Reduction via the Proper Orthogonal Decomposition
- DW-LIT-0038 (rank 38): Model Reduction and Neural Networks for Parametric PDEs
- DW-LIT-0039 (rank 39): Neural-Network-Augmented Projection-Based Model Order Reduction for Mitigating the Kolmogorov Barrier to Reducibility of CFD Models
- DW-LIT-0040 (rank 40): Neural Operator: Graph Kernel Network for Partial Differential Equations
- DW-LIT-0041 (rank 41): Multiscale MeshGraphNets
- DW-LIT-0042 (rank 42): Neural Operator: Learning Maps Between Function Spaces
- DW-LIT-0043 (rank 43): Deep Transfer Operator Learning for Partial Differential Equations under Conditional Shift
- DW-LIT-0044 (rank 44): Generative learning of the solution of parametric partial differential equations using guided diffusion models and virtual observations
- DW-LIT-0045 (rank 45): LAFlowNet: A dynamic graph method for the prediction of velocity and pressure fields in left atrium and left atrial appendage
- DW-LIT-0046 (rank 46): VortexNet: A Graph Neural Network-Based Multi-Fidelity Surrogate Model for Field Predictions
- DW-LIT-0047 (rank 47): Choose a Transformer: Fourier or Galerkin
- DW-LIT-0048 (rank 48): Positional Knowledge Is All You Need: Position-Induced Transformer (PiT) for Operator Learning
- DW-LIT-0049 (rank 49): Neural Operators with Localized Integral and Differential Kernels
- DW-LIT-0050 (rank 50): DiMON: Learning Solution Operators of Partial Differential Equations on a Diffeomorphic Family of Domains
- DW-LIT-0051 (rank 51): Learning Solution Operators of PDEs Defined on Varying Domains via MIONet
- DW-LIT-0052 (rank 52): Solving high-dimensional parametric engineering problems for inviscid flow around airfoils based on physics-informed neural networks
- DW-LIT-0053 (rank 53): Gabor-Filtered Fourier Neural Operator for Solving Partial Differential Equations
- DW-LIT-0054 (rank 54): Factorized Fourier Neural Operators
- DW-LIT-0055 (rank 55): MGNO: Efficient Parameterization of Linear Operators via Multigrid
- DW-LIT-0056 (rank 56): Reduced order modeling for nonlinear structural analysis using Gaussian process regression
- DW-LIT-0057 (rank 57): A Data–Driven Approximation of the Koopman Operator: Extending Dynamic Mode Decomposition
- DW-LIT-0058 (rank 58): Spectral analysis of nonlinear flows

## Unresolved seed outside the ranked 59-record corpus

The original research seed `S0306454926007425` remained unresolved: title, authors, DOI, and publication status could not be independently established in the supplied review. It is **not fabricated into the Zotero import**.

## Acquisition/PDF policy

No PDFs are committed to this repository. `legitimate_oa_url` stores the legal OA source identified by the research; it may be a landing page rather than a direct PDF. `direct_pdf_url` is intentionally blank in the acquisition queue unless a direct PDF has been independently verified.

## Known limitations

1. This build is a normalization of the supplied Deep Research results, not a fresh 59-paper publisher/Crossref re-audit.
2. Many Tier 2 papers were bibliography-verified only in the research review. Their DOI/OA/code fields need a later verification pass.
3. Parsed venue strings retain useful volume/page/article details and sometimes acquisition wording may require manual cleanup in Zotero.
4. The technical metadata table retains the original review prose because that is more defensible than over-normalizing claims that were not fully inspected.
5. No numerical results or code repositories were independently reproduced.

## Recommended next QA pass

Resolve remaining identifiers with publisher records/Crossref/OpenAlex; import the CSL JSON or RIS into Zotero; merge any duplicates Zotero detects; attach legitimate PDFs; then write the resulting Zotero item key back to `metadata/direwolf_technical_metadata.csv` using `record_id` as the stable join key.
