# Molecular networking practical · MN Labs

You process the urine of 8 stroke patients (MassIVE MSV000081118) with the **Feature Finder** desktop app and then
explore the molecular network with ten teaching plugins, the **MN Labs**. Choose the labs you want to do: each link
below opens a start page with the downloads, a click-by-click guide and the questions.

1. **First time?** Follow [Getting started](getting-started.md): download, start the app, process the files, open a lab.
2. **Main task:** [What were these patients taking?](task-urine-drugs.md) The labs are the tools for it.
3. A good order to start: Lab 4 → 5 → 1 → 2 → 3 → 6, then whatever interests you.

Overview slide: [MN_Labs_overview.pptx](https://github.com/YasinEl/temp_share/releases/download/mn-teaching-materials-2026-10-29/MN_Labs_overview.pptx)

## The labs

| Lab | Theme | Time | What you learn | Data |
|---|---|---|---|---|
| **[1 · Spectral Similarity](lab01-spectral-similarity.md)** | Building the network | 45 min | How two MS/MS spectra become one score (cosine, modified cosine) and how the settings change it. | urine_POS |
| **[2 · Network Builder](lab02-network-builder.md)** | Building the network | 40 min | How threshold, matched peaks, top-K and the family-size cap turn scores into molecular families. | urine_POS |
| **[3 · Families × Patients](lab03-families-patients.md)** | Interpreting it | 50 min | Drug-derived vs body-made families, read with the patient metadata and the Δ masses on the edges. | urine_POS |
| **[4 · From Scans to Features](lab04-from-scans-to-features.md)** | Data → features | 45 min | Raw MS1 scans → XIC → peak area → table row; isotopes, RT alignment, which ions got an MS/MS. | urine_POS |
| **[5 · One Compound, Many Features](lab05-one-compound-many-features.md)** | Data → features | 40 min | Isotopes, adducts and in-source fragments of one molecule, and the network edges they create. | urine_POS |
| **[6 · Annotation Propagation](lab06-annotation-propagation.md)** | Interpreting it | 45 min | Carry library names through the network (known compound + Δ) and judge whether a proposal holds. | urine_POS |
| **[7 · Can I Trust This Feature?](lab07-can-i-trust-this-feature.md)** | Data → features | 45 min | Signal drift, CV of 17 repeated QC injections, blank filtering and PCA. | urine_POS + urine_QC_extra |
| **[8 · Positive vs Negative](lab08-positive-vs-negative.md)** | Study design | 45 min | What each polarity sees, the positive bias of libraries, impossible hits, sulfates. | urine_NEG |
| **[9 · ModiFinder](lab09-modifinder.md)** | Interpreting it | 50 min | The network says “modified version of X”; the shifted fragments show where the modification sits. | urine_POS |
| **[10 · Pool MS/MS vs every sample](lab10-pool-ms-ms-vs-every-sample.md)** | Study design | 60 min | What MS/MS only from a pooled QC costs: diluted vs crowded ions, and the MS1 price of MS/MS. | urine_POS |

## Downloads

No GitHub account needed; the files download when you click.

- [FeatureFinder-local-v365-windows-x86_64-MN-labs.zip](https://github.com/YasinEl/temp_share/releases/download/mn-teaching-materials-2026-10-29/FeatureFinder-local-v365-windows-x86_64-MN-labs.zip) · Feature Finder v365 with the ten MN Lab dashboards and the spectral library (Windows, 25 MB)
- [urine_POS.zip](https://github.com/YasinEl/temp_share/releases/download/urine-pos-test-data-2026-10-28/urine_POS.zip) · urine, positive mode: 11 mzML files + metadata.tsv (135 MB)
- [urine_QC_extra.zip](https://github.com/YasinEl/temp_share/releases/download/mn-teaching-materials-2026-10-29/urine_QC_extra.zip) · 27 more urine files: QC injections, blanks, MS1-only runs + metadata_QC_series.tsv (130 MB)
- [urine_NEG.zip](https://github.com/YasinEl/temp_share/releases/download/mn-teaching-materials-2026-10-29/urine_NEG.zip) · urine, negative mode: 11 mzML files + metadata.tsv (138 MB)
- [urine_POS_results.zip](https://github.com/YasinEl/temp_share/releases/download/mn-teaching-materials-2026-10-29/urine_POS_results.zip) · the app's results for urine_POS (aligned_features.csv + library_matches.tsv), + xic_positive.json (its LC peaks), to upload in panel 1
- [urine_POS_poolMSMS_results.zip](https://github.com/YasinEl/temp_share/releases/download/mn-teaching-materials-2026-10-29/urine_POS_poolMSMS_results.zip) · the app's results for the pool-only design (aligned_features.csv + library_matches.tsv), to load in section 5
- [urine_POS_pool_MSMS.zip](https://github.com/YasinEl/temp_share/releases/download/mn-teaching-materials-2026-10-29/urine_POS_pool_MSMS.zip) · optional: the raw files of the pool-only design (71 MB), only if you want to process it yourself
