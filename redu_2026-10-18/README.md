# ReDU metadata table, 2026-10-18: full Nextflow run from a fresh clone

`redu_merged_metadata_2026-10-18.zip` (21.7 MB) unzips to `merged_metadata.tsv` (1.39 GB, tab-separated,
1,293,209 rows, 73 columns, one row per USI).
sha256 of `merged_metadata.tsv`: `7a6cb6b635cab6a6d3768e9e660b61efe4aebc4acb0c2fa11b777d986c31265f`;
sha256 of the zip: `da8092fa206ca2f1b9ea0a78a28d1c81b779928f8d778f904d070540fb2a045d`.

| Source | Rows |
|---|---|
| MetaboLights | 593,717 |
| Metabolomics Workbench | 454,262 |
| GNPS / MassIVE (incl. MASST) | 232,456 |
| NORMAN | 12,774 |

## How it was made

- Code: PublicDataset_ReDU_Metadata_Workflow `4c591cf` (branch `fix/silent-data-loss`; ReDU-MS2-GNPS2 `96109ae`).
  Not yet on main/master: the released version is the 2026-10-17 table (`../redu_2026-10-17/`).
- A complete Nextflow run: `git clone`, `git submodule update --init`, then
  `nextflow run ./nf_workflow.nf -c nextflow.config`, plus a site-only config with the cluster's executor settings.
  All 23 steps completed; all inputs were fetched on 2026-10-18. No rows are carried over from an earlier table.

## Changes since 2026-10-17

770 rows are new, 12 are gone (ST005273: the same 12 samples under new file names upstream), and 6,335 rows in
105 datasets have changed values.

| Change | Effect |
|---|---|
| Several organisms in one sample, written as the ReDU template asks: `ID|Name||ID|Name` (e.g. `9606|Homo sapiens||5833|Plasmodium falciparum`, `6613|Euprymna scolopes||312309|Aliivibrio fischeri ES114`). The lineage columns (NCBIRank ... NCBISpecies, OpenTreeOfLifeTaxonomyID) hold one value per organism in the same order, joined by `||`. Only samples that really contain several organisms (mixtures, co-cultures, host + parasite); a study-level list copied into every sample is not used | 1,953 rows in 34 datasets (GNPS 151, MetaboLights 1,794, Workbench 8); e.g. MTBLS15676's 224 meat mixtures (chicken, pig, cow) are back |
| NCBI taxa named 'Genus sp. X' are kept instead of reduced to the genus ('Synechocystis sp. PCC 6803', 'Sulfitobacter sp. CB 2047', 'Bacteroides sp. WH2', ...) | about 2,700 rows get their strain or species; bare 'Genus sp.', strains NCBI does not list and short lab labels ('sp. 1') stay at the genus |
| More culture collections in strain names (SAG, UTEX, CCMP, RCC, NCIB, PCC, ...); typos of old NCBI names (only when no other taxon is within two edits) | e.g. ST001688 strains, ST002790 +29 rows, ST003799 'Clostridium clostridioforme' |
| New studies upstream since 2026-10-17 | e.g. MTBLS15948 226 rows, MTBLS14939 62, MTBLS15852 20 |

Filtering by organism: with several organisms in one cell, use "contains" in tools that compare whole cells; the ReDU
web app's organism filters on branch `fix/silent-data-loss` match each organism of a `||` value.

The rule checks (allowed terms per organism, diet, groups, food, sex, personal care, blanks without organism, no
duplicate USIs, no empty or broken cells) find no violations. The multi-organism, strain and typo changes match the
offline replays of every source over the 2026-10-12 metadata download.
