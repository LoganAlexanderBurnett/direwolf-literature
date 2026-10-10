# DIREWOLF literature corpus validation report

Updated **October 10, 2026** after a source-by-source metadata resolution pass.

## Record accounting

- Ranked records: **59** (29 Tier 1, 30 Tier 2)
- Records with a verified publication/proceedings DOI: **44**
- Records whose authoritative publication record has no publication DOI: **12**
- Preprint-only records with no separate publication DOI: **3**
- Records still ambiguous within the ranked 59-record corpus: **0**
- Duplicate ranked records silently removed: **0**

The detailed 43-record resolution log is in [`METADATA_RESOLUTION_2026-10-10.md`](METADATA_RESOLUTION_2026-10-10.md).

## DOI policy

`verified_doi` stores the DOI of the canonical publication or proceedings record. An arXiv/DataCite DOI is stored separately as `preprint_doi`; it is not substituted into `verified_doi` merely to make the DOI column non-empty.

This matters because ICLR, PMLR/ICML, and some JMLR publications in this corpus have authoritative peer-reviewed records but no publication DOI. Three records (DW-LIT-0040, DW-LIT-0041, DW-LIT-0051) remain preprint-only and are explicitly labeled as such.

## Metadata corrections made

The pass identified definitive publication metadata for older ROM papers and several operator-learning papers. It also corrected publication state/title for notable cases:

- PINO (DW-LIT-0017) → definitive 2024 ACM/IMS Journal of Data Science article, DOI `10.1145/3648506`.
- Neural-network-augmented projection ROM (DW-LIT-0039) → definitive JCP article, DOI `10.1016/j.jcp.2023.112420`.
- Neural Operator theory paper (DW-LIT-0042) → full canonical JMLR title.
- DIMON (DW-LIT-0050) → definitive Nature Computational Science article under a changed title, DOI `10.1038/s43588-024-00732-2`.
- F-FNO (DW-LIT-0054) → verified ICLR 2023 publication.
- MgNO (DW-LIT-0055) → verified ICLR 2024 publication.

## Acquisition/PDF policy

No copyrighted PDFs are committed to this repository. `legitimate_oa_url` records legal OA sources where identified. A landing page is not represented as a direct PDF URL unless that exact direct PDF was independently verified.

## Evidence provenance

The initial ranked corpus came from the October 7, 2026 DIREWOLF Deep Research review. The October 10 metadata pass checked the previously unresolved 43 records individually against DOI resolvers, publisher/journal pages, official proceedings/OpenReview/PMLR/JMLR records, institutional repositories, or arXiv when the work is preprint-only.

Selected code repositories discovered during that pass were verified through the linked GitHub connection. See the detailed resolution log for record-by-record source URLs.

## Remaining separate seed issue

The original ScienceDirect identifier `S0306454926007425` remains unresolved and is outside the 59 ranked records. No bibliographic metadata has been fabricated for it.

## Next QA step

Import the regenerated CSL JSON or RIS into Zotero, merge any duplicates Zotero detects, acquire legitimate full text for Tier 1 records, and then write Zotero item keys back into the technical metadata table using `record_id` as the stable join key.
