# temp_share

## FoodSubstances — StructureMASST + DomainMASST results

Desalted + neutralized PubChem "FoodSubstances" list (2,676 unique molecules after
metal/counterion removal via RDKit `LargestFragmentChooser` + charge neutralization),
queried against public MASST records (cosine ≥ 0.8, ≥ 5 matching peaks, annotation
rank 1). 356 molecules had hits; 334 produced DomainMASST trees. All match tables
reflect the InChIKey-deduplication fix (one row per real match).

The results archive (~574 MB) is split into 7 parts because GitHub caps single files
at 100 MB. Reassemble it, verify, and extract:

```bash
cat foodsub_results_share.tar.gz.part* > foodsub_results_share.tar.gz
sha256sum -c foodsub_results_share.tar.gz.sha256   # should print: OK
tar xzf foodsub_results_share.tar.gz
```

### Archive contents

Per molecule with hits (`batch_output_foodsubstances_part{1,2}/NNNN_<Name>_<hash>/`):

- `raw_redu.tsv` — hit table: one row per spectral match, joined with full ReDU
  sample metadata (dataset, organism/NCBI lineage, body part, method, …)
- `rawdata_sankey.html` — Sankey plot (Dataset → BodyPart → NCBIDivision → NCBITaxonomy)
- `domainMASST/domain_masst_<Name>_{microbe,plant,tissue,food,microbiome,combined}.html`
  — interactive DomainMASST trees
- `domainMASST/domain_masst_<Name>_matches.tsv` — matches fed to the trees
- `library_all_spectra.tsv`, `library_overview.tsv`, `library_<inchikey>.tsv`,
  `input.txt` — library matches + query provenance

Top level: `batch_output_foodsubstances_combined_summary.tsv` (per-molecule summary),
`FoodSubstances_desalted.csv` (desalted input), `README_foodsub_share.md`.

Molecules with no hits have no folder. DomainMASST intermediates
(`*.json`, `*_counts_*.tsv`, `domainMasst_input_*.tsv`, logs) were dropped — their
data is bundled inside the HTML trees. `raw_masst.tsv` was empty by design and is omitted.
