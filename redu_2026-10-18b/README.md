# ReDU metadata table, 2026-10-18b: full Nextflow run from a fresh clone

`redu_merged_metadata_2026-10-18b.zip` (21.7 MB) unzips to `merged_metadata.tsv` (1.39 GB, tab-separated,
1,293,729 rows, 73 columns, one row per USI).
sha256 of `merged_metadata.tsv`: `20de8fc462ff5173fbc7a6f23bda911897ffaa0397432d38ecb254eb61fb310a`;
sha256 of the zip: `b864d87c77ebad45c66351bf2e2f5f6b3d16531106c27ed3e5ab900c2f8eb762`.

| Source | Rows |
|---|---|
| MetaboLights | 593,951 |
| Metabolomics Workbench | 454,548 |
| GNPS / MassIVE (incl. MASST) | 232,456 |
| NORMAN | 12,774 |

## How it was made

- Code: PublicDataset_ReDU_Metadata_Workflow `79f81a9` (branch `fix/silent-data-loss`; ReDU-MS2-GNPS2 `338dc3c`).
  Not yet on main/master: the released version is the 2026-10-17 table (`../redu_2026-10-17/`).
- A complete Nextflow run: `git clone`, `git submodule update --init`, then
  `nextflow run ./nf_workflow.nf -c nextflow.config`, plus a site-only config with the cluster's executor settings.
  All 23 steps completed; inputs fetched on 2026-10-18. No rows carried over from an earlier table.

## Changes since 2026-10-18 (`../redu_2026-10-18/`)

- A bare 'Genus sp.' text with the ID of a species or strain of that genus now takes the ID in every source:
  GNPS 'Eggerthella sp' + 502558 -> `502558|Eggerthella sp. YY7918` (12 rows, MSV000086821, MSV000086884).
  No other value changed.
- 520 new rows from studies published upstream since the 2026-10-18 run (e.g. MTBLS16036 210, ST005236 120,
  ST004435 66). No rows are gone.

See `../redu_2026-10-18/README.md` for the earlier changes (several organisms per sample as `ID|Name||ID|Name`,
NCBI taxa named 'Genus sp. X' kept, more culture collections, typos of old NCBI names). The rule checks find no
violations.
