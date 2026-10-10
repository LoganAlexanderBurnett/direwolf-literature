# Metadata resolution pass — 2026-10-10

This pass resolves the **43 records** that lacked a publication DOI in the initial DIREWOLF acquisition manifest. Each record was checked individually against an authoritative publisher, proceedings, journal, institutional, or preprint record. GitHub repositories were separately checked for selected official code links.

## Outcome

- Previously unresolved records checked: **43**
- Newly verified publication/proceedings DOIs: **28**
- Authoritative publication records with no publication DOI: **12**
- Preprint-only records with no separate publication DOI: **3**
- Remaining ambiguous records from this 43-record set: **0**
- Initial 16 verified DOI records were retained unchanged unless separately normalized.
- Total corpus records with publication/proceedings DOI after this pass: **44 / 59**
- Total corpus records without a publication DOI after this pass: **15 / 59**

**Important:** an arXiv/DataCite DOI is stored in `preprint_doi` and is not promoted into `verified_doi` when a peer-reviewed publication has no DOI or when the work remains a preprint.

## Record-by-record resolution

| Rank | ID | Resolution | Publication DOI | Preprint DOI | Verification source |
|---:|---|---|---|---|---|
| 7 | DW-LIT-0007 | verified_publication_doi | 10.52202/075280-1556 | — | https://doi.org/10.52202/075280-1556 |
| 8 | DW-LIT-0008 | authoritative_record_no_publication_doi | — | 10.48550/arXiv.2010.03409 | https://openreview.net/forum?id=roNqYL0_XP |
| 10 | DW-LIT-0010 | authoritative_record_no_publication_doi | — | 10.48550/arXiv.2202.03376 | https://openreview.net/forum?id=vSix3HPYKSU |
| 11 | DW-LIT-0011 | authoritative_record_no_publication_doi | — | 10.48550/arXiv.2402.02366 | https://proceedings.mlr.press/v235/wu24r.html |
| 12 | DW-LIT-0012 | authoritative_record_no_publication_doi | — | 10.48550/arXiv.2502.02414 | https://proceedings.mlr.press/v267/luo25o.html |
| 13 | DW-LIT-0013 | authoritative_record_no_publication_doi | — | 10.48550/arXiv.2207.05209 | https://jmlr.org/papers/v24/23-0064.html |
| 14 | DW-LIT-0014 | authoritative_record_no_publication_doi | — | 10.48550/arXiv.2010.08895 | https://openreview.net/forum?id=c8P9NQVtmnO |
| 17 | DW-LIT-0017 | verified_publication_doi | 10.1145/3648506 | 10.48550/arXiv.2111.03794 | https://doi.org/10.1145/3648506 |
| 18 | DW-LIT-0018 | verified_publication_doi | 10.1016/j.jcp.2018.02.037 | — | https://doi.org/10.1016/j.jcp.2018.02.037 |
| 19 | DW-LIT-0019 | verified_publication_doi | 10.1016/j.cma.2016.03.025 | — | https://doi.org/10.1016/j.cma.2016.03.025 |
| 20 | DW-LIT-0020 | verified_publication_doi | 10.1016/j.jcp.2019.108973 | — | https://doi.org/10.1016/j.jcp.2019.108973 |
| 21 | DW-LIT-0021 | verified_publication_doi | 10.1016/j.physd.2020.132401 | — | https://doi.org/10.1016/j.physd.2020.132401 |
| 26 | DW-LIT-0026 | verified_publication_doi | 10.1016/j.jcp.2020.110079 | — | https://doi.org/10.1016/j.jcp.2020.110079 |
| 27 | DW-LIT-0027 | verified_publication_doi | 10.1016/j.jcp.2019.05.024 | — | https://doi.org/10.1016/j.jcp.2019.05.024 |
| 28 | DW-LIT-0028 | verified_publication_doi | 10.1016/j.jcp.2018.04.018 | — | https://doi.org/10.1016/j.jcp.2018.04.018 |
| 29 | DW-LIT-0029 | authoritative_record_no_publication_doi | — | 10.48550/arXiv.2201.09113 | https://openreview.net/forum?id=XctLdNfCmP |
| 32 | DW-LIT-0032 | verified_publication_doi | 10.1137/130932715 | — | https://doi.org/10.1137/130932715 |
| 33 | DW-LIT-0033 | verified_publication_doi | 10.1137/090766498 | — | https://doi.org/10.1137/090766498 |
| 34 | DW-LIT-0034 | verified_publication_doi | 10.1016/j.jcp.2013.02.028 | — | https://doi.org/10.1016/j.jcp.2013.02.028 |
| 35 | DW-LIT-0035 | verified_publication_doi | 10.1017/S0022112010001217 | — | https://doi.org/10.1017/S0022112010001217 |
| 36 | DW-LIT-0036 | verified_publication_doi | 10.1146/annurev.fl.25.010193.002543 | — | https://doi.org/10.1146/annurev.fl.25.010193.002543 |
| 37 | DW-LIT-0037 | verified_publication_doi | 10.2514/2.1570 | — | https://doi.org/10.2514/2.1570 |
| 38 | DW-LIT-0038 | verified_publication_doi | 10.5802/smai-jcm.74 | — | https://doi.org/10.5802/smai-jcm.74 |
| 39 | DW-LIT-0039 | verified_publication_doi | 10.1016/j.jcp.2023.112420 | 10.48550/arXiv.2212.08939 | https://doi.org/10.1016/j.jcp.2023.112420 |
| 40 | DW-LIT-0040 | preprint_only_no_publication_doi | — | 10.48550/arXiv.2003.03485 | https://authors.library.caltech.edu/records/k3t18-we744 |
| 41 | DW-LIT-0041 | preprint_only_no_publication_doi | — | 10.48550/arXiv.2210.00612 | https://arxiv.org/abs/2210.00612 |
| 42 | DW-LIT-0042 | authoritative_record_no_publication_doi | — | — | https://jmlr.org/papers/v24/21-1524.html |
| 43 | DW-LIT-0043 | verified_publication_doi | 10.1038/s42256-022-00569-2 | — | https://doi.org/10.1038/s42256-022-00569-2 |
| 44 | DW-LIT-0044 | verified_publication_doi | 10.1016/j.cma.2024.117654 | — | https://doi.org/10.1016/j.cma.2024.117654 |
| 45 | DW-LIT-0045 | verified_publication_doi | 10.1016/j.engappai.2024.108896 | — | https://doi.org/10.1016/j.engappai.2024.108896 |
| 46 | DW-LIT-0046 | verified_publication_doi | 10.2514/6.2025-0494 | — | https://doi.org/10.2514/6.2025-0494 |
| 47 | DW-LIT-0047 | verified_proceedings_doi | 10.5555/3540261.3542170 | 10.48550/arXiv.2105.14995 | https://papers.nips.cc/paper/2021/hash/d0921d442ee91b896ad95059d13df618-Abstract.html |
| 48 | DW-LIT-0048 | authoritative_record_no_publication_doi | — | 10.48550/arXiv.2405.09285 | https://proceedings.mlr.press/v235/chen24au.html |
| 49 | DW-LIT-0049 | authoritative_record_no_publication_doi | — | 10.48550/arXiv.2402.16845 | https://proceedings.mlr.press/v235/liu-schiaffini24a.html |
| 50 | DW-LIT-0050 | verified_publication_doi | 10.1038/s43588-024-00732-2 | 10.48550/arXiv.2402.07250 | https://doi.org/10.1038/s43588-024-00732-2 |
| 51 | DW-LIT-0051 | preprint_only_no_publication_doi | — | 10.48550/arXiv.2402.15097 | https://arxiv.org/abs/2402.15097 |
| 52 | DW-LIT-0052 | verified_publication_doi | 10.1016/j.jcp.2024.113285 | — | https://doi.org/10.1016/j.jcp.2024.113285 |
| 53 | DW-LIT-0053 | verified_publication_doi | 10.1016/j.compfluid.2024.106239 | — | https://doi.org/10.1016/j.compfluid.2024.106239 |
| 54 | DW-LIT-0054 | authoritative_record_no_publication_doi | — | 10.48550/arXiv.2111.13802 | https://openreview.net/forum?id=tmIiMPl4IPa |
| 55 | DW-LIT-0055 | authoritative_record_no_publication_doi | — | 10.48550/arXiv.2310.19809 | https://openreview.net/forum?id=8OxL034uEr |
| 56 | DW-LIT-0056 | verified_publication_doi | 10.1016/j.cma.2018.07.017 | — | https://doi.org/10.1016/j.cma.2018.07.017 |
| 57 | DW-LIT-0057 | verified_publication_doi | 10.1007/s00332-015-9258-5 | — | https://doi.org/10.1007/s00332-015-9258-5 |
| 58 | DW-LIT-0058 | verified_publication_doi | 10.1017/S0022112009992059 | — | https://doi.org/10.1017/S0022112009992059 |

## Material bibliographic corrections

- **Rank 17 (PINO):** promoted from accepted-manuscript/preprint status to the definitive 2024 ACM/IMS Journal of Data Science article, DOI `10.1145/3648506`.
- **Rank 39:** the peer-reviewed Journal of Computational Physics version was identified; its canonical published title is slightly shorter than the preprint title.
- **Rank 42:** normalized to the full JMLR title, *Neural Operator: Learning Maps Between Function Spaces With Applications to PDEs*.
- **Rank 50 (DIMON):** matched to the peer-reviewed Nature Computational Science article published under the different title *A scalable framework for learning the geometry-dependent solution operators of partial differential equations*, DOI `10.1038/s43588-024-00732-2`.
- **Rank 51 (MIONet varying domains):** kept as a 2024 preprint. A later related SIAM paper has a different title and was not silently substituted.
- **Rank 54 (F-FNO):** verified as an ICLR 2023 peer-reviewed conference paper rather than an unresolved preprint.
- **Rank 55 (MgNO):** verified as an ICLR 2024 peer-reviewed conference paper.

## DOI policy

`verified_doi` is reserved for the DOI of the canonical publication/proceedings record. `preprint_doi` is separate. For ICLR, PMLR/ICML, and JMLR records whose authoritative entry has no DOI, `doi_status` records that fact rather than leaving the record ambiguously unresolved.

## Code repository checks

The following official/public repositories discovered during this pass were verified through the linked GitHub connection:

- MeshGraphNets: https://github.com/google-deepmind/deepmind-research/tree/master/meshgraphnets
- Transolver++: https://github.com/thuml/Transolver_plus
- PINO: https://github.com/neuraloperator/physics_informed
- PhyGeoNet: https://github.com/Jianxun-Wang/phygeonet
- Graph Kernel Neural Operator: https://github.com/neuraloperator/graph-pde
- Galerkin Transformer: https://github.com/scaomath/galerkin-transformer
- Gabor-Filtered FNO: https://github.com/Kai-Qi/Gabor-Filtered-Fourier-Neural-Operator
- Factorized FNO: https://github.com/alasdairtran/fourierflow
- MgNO: https://github.com/xlliu2017/MgNO

## Remaining separate issue

The original seed identifier `S0306454926007425` remains outside the ranked 59-record corpus and was not fabricated into a bibliography entry.
