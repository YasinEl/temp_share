# Calprotectin marker search: Everything-Bagel export

**Download:** [calprotectin_bagel_export.zip](https://github.com/YasinEl/temp_share/releases/download/calprotectin-bagel-2026-09-22/calprotectin_bagel_export.zip)
(165 MB, attached to the release
[calprotectin-bagel-2026-09-22](https://github.com/YasinEl/temp_share/releases/tag/calprotectin-bagel-2026-09-22);
SHA-256 `9cb3bc4e180b0a08aee1c65a534254cff9f5333508ab5349e4b7e16c55072efa`).

Untargeted LC-MS reprocessing, with the GNPS2 Everything-Bagel feature finder, of public IBD
metabolomics studies, to find features correlated with fecal calprotectin:

| ID | Cohort / matrix |
|---|---|
| ST002471 | PROTECT pediatric UC, stool |
| ST002470 | PROTECT pediatric UC, plasma (same subjects as ST002471) |
| ST001000 | PRISM / Netherlands IBD, stool |
| ST000923 | HMP2 / iHMP IBD, stool (longitudinal) |
| ST001689 | breast milk vs infant fecal calprotectin |
| MTBLS9877 | fecal water / plasma / urine, high vs low calprotectin (m/z-level check) |

The zip contains:

- feature tables per study × LC method;
- annotations: the submitters' named metabolites, GNPS library hits, pool MS/MS and the inclusion list;
- per-sample metadata with calprotectin and covariates;
- per-feature association results, the cross-study recurrence tables and the 357 recurrent markers;
- MS2-linking diagnostics;
- all scripts;
- a standalone HTML report.

`README.md` inside the zip describes every folder and column.

```bash
curl -LO https://github.com/YasinEl/temp_share/releases/download/calprotectin-bagel-2026-09-22/calprotectin_bagel_export.zip
sha256sum calprotectin_bagel_export.zip   # compare with the value above
unzip calprotectin_bagel_export.zip
```

Related: [Scalable_FeatureFinder_Rust PR #87](https://github.com/Wang-Bioinformatics-Lab/Scalable_FeatureFinder_Rust/pull/87)
(orphan MS2 rescue after gap filling, found during this analysis).

# ReDU metadata table, 2026-10-15 (b)

**Download:** [redu_2026-10-15b/redu_merged_metadata_2026-10-15b.zip](redu_2026-10-15b/redu_merged_metadata_2026-10-15b.zip)
(21.6 MB; unzips to a 1.39 GB TSV, 1,293,892 rows, one row per USI). Metadata of public MassIVE/GNPS,
MetaboLights, Metabolomics Workbench and NORMAN datasets, built with the
[PublicDataset_ReDU_Metadata_Workflow](https://github.com/Wang-Bioinformatics-Lab/PublicDataset_ReDU_Metadata_Workflow)
at commit `6f46b12` (branch `fix/silent-data-loss`). Details in `redu_2026-10-15b/README.md`.
