# ReDU metadata table, 2026-10-15 (b): diet, groups, food, sex, personal care rules

`redu_merged_metadata_2026-10-15b.zip` (21.6 MB) unzips to `merged_metadata.tsv` (1.39 GB, tab-separated,
1,293,892 rows, 73 columns, one row per USI; same rows in the same order as `../redu_2026-10-15/`).
sha256 of `merged_metadata.tsv`: `2af27888971f100d3f5d05d1ffcbc3a1dd67ad7ac95f657cab596020667b0940`.

## How it was made

- Code: PublicDataset_ReDU_Metadata_Workflow `6f46b12` (branch `fix/silent-data-loss`; ReDU-MS2-GNPS2 `351add0`).
- **Not a new Nextflow run.** The inputs of the 2026-10-15 run of `8f6f658` were reprocessed offline with the new code:
  the MetaboLights and Workbench studies whose rows change were reconverted from the metadata mirrors, the GNPS
  and MASST steps were rerun, then merge, NCBI lineage and the two new final steps. The unchanged code reproduced
  the earlier table byte for byte.
- The rows are those of the earlier table; 82,625 rows have at least one changed value.

## What changed (cells filled: before → after)

| Column | Before | After | What |
|---|---|---|---|
| Diet | 12,760 | 17,384 | Diet factors from Workbench, MetaboLights, GNPS sheets and microbiomeMASST; foods eaten (e.g. apple, cranberry) only for animal subjects that are not food, blanks or QCs |
| FastingStatus | 42,311 | 43,273 | Fasting factors (e.g. MTBLS89, MTBLS13313) |
| InternalStandardsUsed | 90,089 | 99,941 | Internal-standard factors (e.g. MTBLS10622) |
| FoodOntologyTerm | 3,045 | 8,434 | Food samples named with a clear food-product term (cheese, wine, ...), 33 studies |
| BiologicalSex | 301,280 | 310,372 | From body parts only one sex has (e.g. MTBLS717 cervical mucus); mammals only |
| SampleGroupFreeText | 543,704 | 502,385 | Factors now held in a column, constant parts, single labels and labels on blanks/QCs removed |
| SampleType | | | 884 personalCareMASST rows: 'personal care product'; ProductCategory is the last path element |

## Known open points

- MSV000080918 and MSV000090974 show one SampleGroupFreeText label next to unlabelled real samples; their other
  groups are told apart by Diet.
- ST001714 and ST002011 keep the constant part 'Parasite Stage' so that treated and untreated samples differ.
- microbiomeMASST diets given to every file of a dataset are not used (often wrong for multi-arm studies), so
  MSV000088845 (all mice high-fat) has no Diet.
- MTBLS15689's intermittent-fasting arm has no Diet.
- 6,466 GNPS rows of non-human organisms carry a human LifeStage; MSV000086415 metadata is not downloadable.
