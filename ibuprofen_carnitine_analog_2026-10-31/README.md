# Ibuprofen–carnitine conjugates: StructureMASST with analogue search

31 GNPS library spectra (ibuprofen / hydroxy- and carboxy-ibuprofen carnitine esters) searched against
`metabolomicspanrepo_index_nightly` with modification (analogue) search, run 2026-10-31.

## Search settings

| | |
|---|---|
| mode | FASST (USI queries), `bin/run_script_batch.py --mode fasst --mod-search` |
| cosine ≥ | 0.70 |
| min matching peaks | 5 |
| precursor / fragment tolerance | 0.02 / 0.02 Da |
| analogue window | ±170 Da (addition and elimination) |
| metadata | ReDU dump of 2026-10-31 (457,767 files, 74 columns) |
| analogue requirement | **an analogue is reported only if the same raw file also carries an unmodified (parent) match of that same query spectrum** — the app's `--mod-condition "Raw file"` rule |

## What is in here

| file | contents |
|---|---|
| `combined_summary.tsv` | one row per query spectrum: raw matches, parent matches, parent files, analogues before/after the filter, files / datasets / taxa kept, top mass offsets |
| `delta_mass_summary.tsv` | every unit mass offset surviving the filter, with match counts, file counts, how many of the 31 spectra show it, and example files |
| `ibuprofen_carnitine_usis.csv` | the batch input (accession, compound, adduct, precursor m/z) |
| `ibuprofen_carnitine_analog_results.zip` | all 31 result folders: `raw_redu_parent_filtered.tsv` (filtered matches + ReDU metadata), `rawdata_sankey_parent_filtered.html` (sankey of the filtered matches), `rawdata_sankey.html` (unfiltered, for comparison), library spectrum tables, `input.txt`, plus `sankeys/` with every filtered sankey in one place and `batch_parameters.json` with the exact run parameters |

The unfiltered `raw_redu.tsv` tables (901 MB, 352,558 matches) are too large for GitHub and stayed on VSC at
`projects/Structure_MASST_App/batch_output_ibuprofen_carnitine_analog_newredu/`.

## Headline numbers

- 352,558 raw matches → **4,902 parent matches + 23,582 of 347,656 analogues kept** (93 % of analogue hits had no parent in the same file and were dropped)
- 733 raw files across 49 datasets carry a parent match; 17 of the 31 query spectra have any parent hit at all
- all parent-carrying files are *Homo sapiens*: urine (24,400 matches), blood serum (3,888), feces (152)
- three datasets dominate: MSV000096359, MSV000095726, MSV000097935
- 69 distinct unit mass offsets survive; the most frequent are −14, −48, −12, −38, −50, −60 Da
- the duplicate library entries of the same conjugate (e.g. CCMSLIB00017390871 / 00015258101 / 00015437818) return identical counts, as expected
