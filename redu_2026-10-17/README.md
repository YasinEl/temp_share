# ReDU metadata table, 2026-10-17: full Nextflow run from a fresh clone

`redu_merged_metadata_2026-10-17.zip` (21.6 MB) unzips to `merged_metadata.tsv` (1.39 GB, tab-separated,
1,292,451 rows, 73 columns, one row per USI).
sha256 of `merged_metadata.tsv`: `122f21b714411dbd834c1ab022b87a656d78706ee4abce57cd9f42ff29816bb1`;
sha256 of the zip: `7c61b267aa4d9e1e81d3feca8e6dcb605ca1fff1f0892d1105d74465f4f29ea6`.

| Source | Rows |
|---|---|
| MetaboLights | 592,988 |
| Metabolomics Workbench | 454,233 |
| GNPS / MassIVE (incl. MASST) | 232,456 |
| NORMAN | 12,774 |

## How it was made

- Code: PublicDataset_ReDU_Metadata_Workflow `32497ff` (branch `fix/silent-data-loss`; ReDU-MS2-GNPS2 `526cb31`).
- A complete Nextflow run: `git clone`, `git submodule update --init`, then
  `nextflow run ./nf_workflow.nf -c nextflow.config`, plus a site-only config with the cluster's executor settings.
  Nextflow built the conda environment itself. All 23 steps completed; all inputs were fetched on 2026-10-17.
- No rows are carried over from an earlier table (the run starts with an empty "old" table).

## Changes since 2026-10-16 (`../redu_2026-10-16/`)

6,187 rows are gone, 2,751 are new, and 113,161 rows in 2,256 datasets have changed values.

| Change | Effect |
|---|---|
| Files must carry their own sample's metadata. MetaboLights assay sheets whose Sample Name column was sorted on its own are re-paired by file name or withheld; Workbench no longer gives a file to the longest sample name containing it (e.g. `32650.mzML` to liver sample `L32650`) | Removed: MTBLS718 1,259 and MTBLS13295 258 mispaired rows; 3,552 Workbench rows in 51 datasets that were paired by guessing (ST001181 1,191, ST001114 480, ...). Many more re-paired |
| Organism: the name wins over a contradicting or drag-filled taxon ID (microbes: the ID); a sample's own species wins over the study species (Workbench); misspelled names and strain numbers are resolved ('Arbidopsis thaliana', 'Zymomonas mobilis ... ATCC 31916') | rows with an organism 1,102,953 -> 1,141,873; MTBLS2522 and MTBLS14081 samples now have their real organism |
| Reference materials named precisely (`reference material_NIST SRM 1950`, `..._NIST SRM 3672`, ...; unknown number: `reference material_NIST`) | reference material rows 2,741 -> 5,494 (1,898 with an SRM/RM number, 1,160 NIST without) |
| Pooled QCs keep the organism and body part of what was pooled; Workbench `_QC_` / `_POOLED_` samples are pool_QC, not blank_QC | pool_QC 36,634 -> 49,627 rows (43,857 with organism, 32,872 with body part); blank_QC 17,155 -> 3,728 |
| Body part from the sample's own organ / tissue / matrix instead of a study-wide value; tissue abbreviations (BAT, WAT, eWAT ...); outdated translation labels fixed (muscle, gallbladder, umbilical cord blood) | rows with a body part 795,112 -> 830,359 |
| Standard injections recognised (molecular_standards, no organism) | molecular_standards 24,373 -> 25,419 |
| MetaboLights submission dates of 0 (1970) replaced by the real year | 10,177 rows of MTBLS2273, MTBLS17, MTBLS13066, MTBLS127, MTBLS210 get their year back |
| Also: plant body parts as Plant Ontology terms, exudate as SampleTypeSub1, surface water from the study text, GNPS negative-mode copies of described files, Workbench polarity / chromatography fixes | |
| Mixtures of several organisms in one sample (e.g. MTBLS15676 chicken; pig; cow) get no organism and are dropped by the minimum-metadata filter | 224 rows |

The rule checks (allowed terms, diet, groups, food, sex, personal care, blanks without organism, no duplicate USIs,
no empty or broken cells) find no violations. The same code gave the same changes in offline replays of
every source over the 2026-10-12 metadata download.
