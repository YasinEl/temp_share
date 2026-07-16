# temp_share

## FoodSubstances — StructureMASST + DomainMASST results

The results are attached to the GitHub **Release**
[`foodsubstances-masst-v1`](https://github.com/YasinEl/temp_share/releases/tag/foodsubstances-masst-v1)
as `foodsub_results_share.tar.gz` (~574 MB).

Desalted + neutralized PubChem "FoodSubstances" list (2,676 unique molecules after
metal/counterion removal via RDKit `LargestFragmentChooser` + charge neutralization),
queried against public MASST records (cosine ≥ 0.8, ≥ 5 matching peaks, annotation
rank 1). 356 molecules had hits; 334 produced DomainMASST trees. All match tables
reflect the InChIKey-deduplication fix (one row per real match).

The archive contains, per molecule with hits: DomainMASST HTML trees
(microbe/plant/tissue/food/microbiome/combined), Sankey plots, `raw_redu.tsv`
(hit table joined with ReDU sample metadata), library match tables, and a combined
per-molecule summary. See `README_foodsub_share.md` inside the archive for details.
