# Task: what were these patients taking?

← [All labs](README.md) · first do [Getting started](getting-started.md)

Downloads: [urine_POS.zip](https://github.com/YasinEl/temp_share/releases/download/urine-pos-test-data-2026-10-28/urine_POS.zip), optional [urine_NEG.zip](https://github.com/YasinEl/temp_share/releases/download/mn-teaching-materials-2026-10-29/urine_NEG.zip), [the app with the labs](https://github.com/YasinEl/temp_share/releases/download/mn-teaching-materials-2026-10-29/FeatureFinder-local-v365-windows-x86_64-MN-labs.zip).

**Data:** urine of 8 stroke patients, a pooled urine QC and 2 blanks (MassIVE MSV000081118), positive mode.
**Files:** the 11 mzML files and `metadata.tsv` from `urine_POS.zip`. Optional: `urine_NEG.zip` (same patients, negative mode).

## Your question

Stroke patients take many medicines: blood-pressure drugs, blood thinners, statins, diabetes drugs,
painkillers, antidepressants. The body turns each drug into **analogues**: metabolites such as hydroxylated,
demethylated, hydrolysed or glucuronidated forms. In a molecular network, these analogues sit next to the drug.

1. **Which drugs can you find, and in which patients?**
2. **Which drug analogues (metabolites, related compounds) sit next to them in the network?** Propose what each
   one is from the mass difference Δ on the edge and from the MS/MS.
3. **Does what you find fit what is known about each person?** The metadata gives:
   - sex and age,
   - smoking status,
   - diabetes,
   - the number of blood-pressure drug classes they take,
   - kidney function (GFR).

   Where it does not fit, give possible explanations.
4. **Would a cheaper design have found the same drugs?** Many labs record MS/MS only in a pooled QC and measure
   each sample in MS1 only. The patients were also measured that way (`_fullscan` files).
   - Which of your drugs would have had no MS/MS spectrum?
   - For each one, is it missing because it is diluted in the pool, or because stronger ions took all the MS/MS slots?
   - Does recording MS/MS in every sample cost MS1 data: fewer MS1 points per peak, worse peak areas, lost signals?

## How to do it

1. Double-click **Start Feature Finder - This Computer**. Drag in the 11 mzML files and drop `metadata.tsv` on the
   **Sample metadata** box of the Data Selection tab. Set **Engine** to **v1 (classic)** and **Quantification** to **Peak area**, and click **Find Features**
   (other settings as they are). Wait for library search and molecular networking to finish.
2. Open any MN Lab under **Plugins → Yours** (or search for *teaching* in the plugin gallery). The labs read the
   metadata from the app; if a lab still shows **⚠ load sample metadata** at the top right, click it and choose
   `metadata.tsv`.
3. Work through the labs:

   | Lab | Use it to |
   |---|---|
   | **MN Lab 3 · Families × Patients** | Find families that occur in only one or a few patients: drugs are personal, body-made molecules are in everyone. Sort the heatmap by the metadata columns. |
   | **MN Lab 6 · Annotation Propagation** | Start from the library matches and list their unnamed neighbours with the Δ on each edge. |
   | **MN Lab 1 · Spectral Similarity** | Check a drug–analogue pair in the mirror plot, compare their LC peaks in every sample, and see the whole family with its library names. |
   | **MN Lab 5 · One Compound, Many Features** | Make sure an "analogue" is not just an adduct, isotope or in-source fragment of the drug. |
   | **MN Lab 8 · Positive vs Negative** (optional) | Look for acidic drugs (diuretics, aspirin) that only show up in negative mode. |
   | **MN Lab 10 · Pool MS/MS vs every sample** | Question 4: which drugs only a patient run fragmented (section 3), why the pool missed them (section 6: dilution or crowding), and what DDA costs the MS1 data (section 7, with the pool-only results from `urine_POS_poolMSMS_results.zip`). |

4. Not every drug has a library spectrum. For a suspect, search its [M+H]⁺ m/z in the feature table (5 ppm).
   Then check whether its MS/MS and its neighbours support the identity.

## What to hand in

One table row per finding:

| Patient | Compound | m/z, RT | Evidence | Analogues found (Δ, proposed change) | Fits the metadata? |
|---|---|---|---|---|---|

For **Evidence**, give a confidence level:
- **library** (MS/MS match, level 2),
- **network + Δ** (level 3),
- **exact mass only** (level 4).

Also say which library names you do *not* trust, and why. Check the precursor m/z error and the retention time.

Finish with a short paragraph for each patient: what you found, what fits the metadata, and what is missing or surprising.

For question 4, add a short table: each drug that only a patient run fragmented, the patients who have it, its
intensity in the pool as a share of the patient, and why the pool missed it (not in the pool / too weak / crowded out).
Then give two or three sentences on what MS/MS in every sample costs the MS1 data, with numbers.
