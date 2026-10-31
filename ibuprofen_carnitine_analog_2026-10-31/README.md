# Ibuprofen–carnitine conjugates: StructureMASST with analogue search

31 GNPS library spectra (ibuprofen / hydroxy- and carboxy-ibuprofen carnitine esters) searched against
`metabolomicspanrepo_index_nightly` with modification (analogue) search. Run 2026-10-31,
**minimum 4 matching ions** (this replaces an earlier 5-ion version at this same URL).

## Search settings

| | |
|---|---|
| mode | FASST (USI queries), `bin/run_script_batch.py --mode fasst --mod-search` |
| cosine ≥ | 0.70 |
| **minimum matching ions** | **4** |
| precursor / fragment tolerance | 0.02 / 0.02 Da |
| analogue window | ±170 Da (addition and elimination) |
| metadata | ReDU dump of 2026-10-31 (457,767 indexed files, 74 columns) |
| analogue requirement | **an analogue is reported only if the same raw file also carries an unmodified (parent) match of that same query spectrum** — the app's `--mod-condition "Raw file"` rule |

## What is in here

| file | contents |
|---|---|
| `combined_summary.tsv` | one row per query spectrum: raw matches, parent matches, parent files, analogues before/after the filter, files / datasets / taxa kept, top mass offsets |
| `delta_mass_summary.tsv` | every unit mass offset surviving the filter, with match counts, file counts, how many of the 31 spectra show it, and example files |
| `ibuprofen_carnitine_usis.csv` | the batch input (accession, compound, adduct, precursor m/z) |
| `ibuprofen_carnitine_analog_results.zip` | all 31 result folders: `raw_redu_parent_filtered.tsv` (filtered matches + ReDU metadata), `rawdata_sankey_parent_filtered.html` (sankey of the filtered matches), `rawdata_sankey.html` (unfiltered, for comparison), library spectrum tables, `input.txt`, plus `sankeys/` with every filtered sankey in one place and `batch_parameters.json` with the exact run parameters |

The unfiltered `raw_redu.tsv` tables (1,208,570 matches, 3.1 GB) are too large for GitHub and stayed on VSC at
`projects/Structure_MASST_App/batch_output_ibuprofen_carnitine_analog_4ions/`.

## Headline numbers

- 1,208,570 raw matches → **8,934 parent matches + 107,973 of 1,199,636 analogues kept** (91 % of analogue hits had no parent in the same file and were dropped)
- 894 raw files across 59 datasets carry a parent match; 19 of the 31 query spectra have any parent hit
- essentially all parent-carrying files are *Homo sapiens* (96 matches in *Mus musculus*): urine (102,903 matches), blood serum (12,208), feces (1,155), blood plasma (295)
- three datasets dominate: MSV000096359, MSV000095726, MSV000097935
- 128 distinct unit mass offsets survive; the most frequent are −14, −64, −48, −12, −40, −50, −60 Da
- duplicate library entries of the same conjugate (e.g. CCMSLIB00017390871 / 00015258101 / 00015437818) return identical counts, as expected

### Effect of dropping the ion threshold from 5 to 4

| | 5 ions | 4 ions |
|---|---|---|
| raw matches | 352,558 | 1,208,570 |
| parent matches kept | 4,902 | 8,934 |
| analogues kept | 23,582 | 107,973 |
| files with a parent match | 733 | 894 |
| datasets | 49 | 59 |
| query spectra with any parent hit | 17 | 19 |
| distinct unit mass offsets | 69 | 128 |

A 4-ion match on a small conjugate is weak evidence on its own, so the extra offsets in this version deserve
spectrum-level inspection before being treated as real modifications.
