# ReDU table, local test run 22 (2026-11-12)

`ReDU_test_run22_2026-11-12.zip` holds the merged ReDU table as TSV (1,343,062 rows); the `.parquet` is the same table. This run replaces run 21.

Workflow `df81883`, ReDU `606b5cf`, ReDU_metadata `2278d93` (all held sheets pushed). Against run 21:

- **No row, dataset, USI or free-text part is lost.** 15 files more (MassIVE).
- **SampleCollectionDateandTime from MetaboLights date columns** named `harvest time` or `sampling day`, and dotted dates with a 2-digit year:
  - MTBLS1968 (`Factor Value[Harvest Time]`, `01.04.19`): 241/428 rows, 2019-03-30 to 2019-04-04;
  - MTBLS9008 (`Comment[Sampling Day]`): 170/216 rows.

  No other study changes (offline converter over all MetaboLights studies: 411 values gained, nothing else different).
- **MSV000084794: 90 → 105 files.** The 15 files only the 2021 uploads list (16GU, 23TM, 24TM, 28TM, HCO04/07/62/64/65/73, SM05/11/25/30/34) are now in its sheet:
  - the fields of their population's rows, and the free text `Population` / `Urbanization Score` / `Indus Score`;
  - age, sex and LifeStage are missing.

  Its ages now print as `58.0` instead of `58` (the column has missing values now), as for 203 other datasets; the values are the same.
- **MSV000084116, MSV000085891:** drag-filled instrument accessions fixed in the sheets. The table already had `Q Exactive|MS:1001911`, so it is unchanged.
- **Unchanged:**
  - SampleGroupFreeText: 756,027 rows in 5,335 datasets;
  - SampleType missing: 25,332;
  - junk patterns: 0.
  - `free_text_changes_run21_to_run22.tsv` is empty: no free text changed on files in both runs.

Local test as before:
- Run 14's inputs, with the changed steps replayed.
- Workbench and MetaboLights converted offline from the 2026-10-12 mirror. ST002706, ST004471 and ST004490 are missing here only.
- MB-POST from the unmerged branch.
