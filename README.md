# DIREWOLF Literature Corpus

Curated literature corpus for **DIREWOLF surrogate modeling**: transient coupled neutronics–thermal field prediction on irregular finite-element meshes, with emphasis on `power_density`, `Tfuel`, and `Tmod` over controlled 0–100 s transients.

The repository separates **bibliographic truth for Zotero** from **DIREWOLF-specific technical metadata for analysis/RAG**. The initial corpus contains 59 ranked papers from the Deep Research review (29 Tier 1 and 30 Tier 2).

## Repository layout

```text
zotero/
  direwolf_zotero_import.csl.json   # preferred Zotero import
  direwolf_zotero_import.ris        # alternative Zotero import
  direwolf_zotero_import.bib        # BibTeX fallback
metadata/
  direwolf_clean_bibliography.csv   # canonical normalized bibliography
  direwolf_technical_metadata.csv   # DIREWOLF architecture/physics/RAG table
  direwolf_acquisition_queue.csv    # OA/PDF/code acquisition tracking
docs/
  VALIDATION_REPORT.md              # QA status, unresolved metadata, limitations
source/
  direwolf_literature_review.md     # original Deep Research review
  original_acquisition_manifest.csv # original 59-row acquisition manifest
```

## Stable identifiers

Every ranked paper has a stable ID `DW-LIT-0001` through `DW-LIT-0059`. **Do not use Zotero item keys as the primary identifier.** Zotero keys are created only after import and can change across libraries/copies. The stable DIREWOLF ID should be retained in the Zotero `Extra`/note field and used to join Zotero exports back to the technical metadata table.

## Import into Zotero

1. Create a Zotero collection such as `DIREWOLF Literature`.
2. In Zotero, choose **File → Import**.
3. Import `zotero/direwolf_zotero_import.csl.json` (preferred) or the RIS file.
4. Put imported items into the DIREWOLF collection.
5. Use Zotero's duplicate-items view to merge any records that resolve to the same canonical publication.
6. Verify or correct unresolved metadata against publisher/Crossref records before treating those records as authoritative.
7. Attach only legitimate publisher, arXiv, OSTI, or institutional-repository PDFs.

## Corpus status

After the October 10, 2026 source-by-source resolution pass, **44 of 59 records have a verified publication/proceedings DOI**. Twelve peer-reviewed records have authoritative venue entries with no publication DOI, and three records are preprint-only. arXiv/DataCite DOIs are stored separately as `preprint_doi` rather than being substituted for publication DOIs. See [`docs/VALIDATION_REPORT.md`](docs/VALIDATION_REPORT.md) and [`docs/METADATA_RESOLUTION_2026-10-10.md`](docs/METADATA_RESOLUTION_2026-10-10.md) for the audit trail.

The original unresolved ScienceDirect seed `S0306454926007425` is **not** represented as a fabricated bibliography item.

## Technical metadata and RAG

`metadata/direwolf_technical_metadata.csv` is deliberately separate from the Zotero import because Zotero is not a good schema for fields such as FE representation, quadrature/mass-matrix treatment, temporal rollout, controls, multiphysics coupling, conservation, UQ, evaluation, and DIREWOLF-specific limitations.

Recommended RAG document metadata after PDF acquisition:

```text
record_id
zotero_item_key
doi
attachment_key
pdf_sha256
page_number
section_title
chunk_id
tier
rag_tags
source_url
```

The preferred state progression for each paper is:

`candidate → metadata-verified → pdf-acquired → fulltext-reviewed → indexed`

Relevance and verification status should remain separate: a paper can be highly relevant and still have unresolved bibliographic fields.

## Acquisition policy

No copyrighted PDFs are stored in this repository. The acquisition queue records publisher/OA/code links identified by the research and leaves direct-PDF fields blank unless independently verified.

## Source provenance

Initial source: DIREWOLF Surrogate-Modeling Literature Review, research cutoff October 7, 2026. The source review and original acquisition manifest are preserved under `source/` so later changes to normalized metadata are auditable.
