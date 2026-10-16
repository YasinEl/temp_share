# ReDU metadata table, 2026-10-16: full Nextflow run from a fresh clone

`redu_merged_metadata_2026-10-16.zip` (21.7 MB) unzips to `merged_metadata.tsv` (1.39 GB, tab-separated,
1,295,887 rows, 73 columns, one row per USI).
sha256 of `merged_metadata.tsv`: `41c790497d75d0a815bb9ce6ef1c4aa8d345ff704ecd726e4ed05d4131a49c48`;
sha256 of the zip: `9c8aea88ba35b6321b02a5cd496a8a03e7d946c5a7922ae2300a1e245c51167c`.

| Source | Rows |
|---|---|
| MetaboLights | 594,211 |
| Metabolomics Workbench | 457,500 |
| GNPS / MassIVE (incl. MASST) | 231,402 |
| NORMAN | 12,774 |

## How it was made

- Code: PublicDataset_ReDU_Metadata_Workflow `0ecf13a` (branch `fix/silent-data-loss`; ReDU-MS2-GNPS2 `80694da`).
- **A complete Nextflow run**, done the way the workflow is meant to be run: `git clone`,
  `git submodule update --init`, then `nextflow run ./nf_workflow.nf -c nextflow.config`, plus a small
  site-only config with the cluster's executor settings, which isn't part of the repository. Nextflow built
  the conda environment itself.
- Reference data, dataset cache, NORMAN, GNPS sheets, MetaboLights and Workbench metadata were fetched
  on 2026-10-16. The three file listings (MetaboLights, Workbench, MassIVE sheets) date from the first
  attempt of the run on 2026-10-15.
- No rows are carried over from an earlier table (the run starts with an empty "old" table).
  Production keeps older rows, e.g. the 22,497 rows of ST001636, which the Workbench has put back under embargo.

## Changes since 2026-10-15b (`../redu_2026-10-15b/`)

| Change | Rows | Datasets |
|---|---|---|
| Workbench studies whose data files are named per sample now match each file to its own sample | +1,437 rows (27 batch-level rows replaced) | 12 (e.g. ST004540, ST003444, ST004485) |
| New or updated upstream data | +585 rows | Workbench ST005207, ST005310, ST005129, ST005309, ST005269, ST004048, ST004310; MetaboLights MTBLS15696, MTBLS15104, MTBLS13847 |
| LifeStage only on human rows | 7,276 values cleared | 39 |
| SampleGroupFreeText: a label is study-level only if every real sample has it; only text labels count | 403 rows | 12 |
| **Regression:** MetaboLights' API now returns submission date 0 for 6 studies, so YearOfAnalysis is empty | 10,226 rows | MTBLS2273, MTBLS17, MTBLS13066, MTBLS127, MTBLS15110, MTBLS210 |

All other shared values are the same as in the offline build of the same code. The rule checks (diet, groups, food,
sex, personal care, allowed terms) find no violations.

## Known problems (fixes in progress)

- MetaboLights: in about 365 assay sheets the Sample Name column was sorted on its own, so files carry another
  sample's metadata (e.g. MTBLS718 participant files labelled pooled QC).
- MetaboLights: the NCBITaxon ID overrides the organism name even when they contradict (MTBLS12310 chicken →
  human, MTBLS3342 human → dog/fox/bear).
- Pooled QCs and reference materials carry no organism or body part. They will keep them, and named reference
  materials (e.g. NIST SRM 1950) will be labelled.
- GNPS: file names with leading spaces, identical copies in two folders and twin acquisitions (Aq/Org, MS1/MSMS)
  are not matched; the file-name "pool" rule turns pooled environmental samples into QCs.
- Workbench: the name of the zip archive a file came from is dropped, so polarity/chromatography stay empty when a
  study's analyses use files of the same name (e.g. ST004470 HILIC vs RP).
- Plant rows carry some animal UBERON terms (e.g. "olivary body" for olive oil).
- 156 GNPS rows (MSV000099793, MSV000099794) contain line breaks inside cells; read with a CSV parser.
