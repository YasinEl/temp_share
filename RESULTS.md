# FoodSubstances MASST — Results Summary

## What was done

1. **Input**: PubChem "FoodSubstances" list — 2,681 substances (CID, name, SMILES).
2. **Desalting + neutralization**: each SMILES was reduced to its largest organic
   fragment (RDKit `LargestFragmentChooser`, stripping metal ions / counterions) and
   then charge-neutralized. 310 entries were multi-component salts that got desalted;
   1 entry was unparseable. → **2,680 molecules** (2,676 unique after name grouping).
3. **StructureMASST + DomainMASST** on every molecule, against the public MASST
   records database, with parameters **cosine ≥ 0.8, ≥ 5 matching peaks, annotation
   rank = 1**.

> All match tables use the corrected InChIKey deduplication (one row per real
> sample match). An earlier version of the batch script inflated match counts up to
> ~200× by emitting one row per library name-synonym; that bug is fixed here.

## Headline numbers

| Metric | Value |
|---|---|
| Molecules processed | 2,676 |
| Molecules with ≥1 hit | **356 (13.3%)** |
| Molecules with DomainMASST trees | 356 |
| Total unique-sample matches (Σ samples) | 1,845,360 |

### Hit-count distribution (unique samples per molecule)

| Samples matched | # molecules |
|---|---|
| 1–9 | 51 |
| 10–99 | 57 |
| 100–999 | 90 |
| 1,000–9,999 | 104 |
| ≥ 10,000 | 54 |

## Top hits (by unique samples)

| Molecule | Unique samples |
|---|---|
| Palmitic acid* | 53,246 |
| L-Tryptophan | 52,299 |
| Pantothenate (vitamin B5)* | 36,331 |
| Stearic acid* | 35,992 |
| Oleic acid* | 25,072 |

\* Listed once here, but appears under **many salt names** in the input
(e.g. sodium / potassium / calcium / magnesium / aluminum palmitate, and 9+ stearate
forms). After desalting they all resolve to the same free acid and therefore return
**identical** match counts — the clearest confirmation that desalting worked as
intended. Without desalting these multi-component salt SMILES would have returned zero.

## Interpretation

- Only ~13% of food substances have detectable spectral matches in public untargeted
  metabolomics data — expected, since many food additives are polymers, inorganic
  salts, or otherwise poorly ionizable / rarely measured by LC-MS/MS.
- The highest-prevalence hits are ubiquitous endogenous/dietary metabolites — free
  fatty acids (palmitic, stearic, oleic), amino acids (tryptophan), and vitamins
  (pantothenate) — matching tens of thousands of public samples, consistent with them
  being near-universal in biological and food matrices.
- Per molecule, the DomainMASST trees (microbe / plant / tissue / food / microbiome /
  combined) and Sankey plots show *where* each compound was observed
  (organism, body part, dataset), and `raw_redu.tsv` gives the full per-match ReDU
  metadata.

## Files

- `foodsub_results_share.tar.gz.part00..06` — split archive (reassemble per README).
- Inside: per-molecule folders with DomainMASST HTML trees, Sankey plots,
  `raw_redu.tsv` (hits + ReDU metadata), library match tables, plus
  `batch_output_foodsubstances_combined_summary.tsv` and the desalted input CSV.
