# MN Lab 5 · One Compound, Many Features

[← Lab 4](lab04-from-scans-to-features.md) · [All labs](README.md) · [Lab 6 →](lab06-annotation-propagation.md)

**About 40 min** · Data → features

One molecule produces several ions: isotopes, adducts, in-source fragments. You will see how the software groups them into one compound, what evidence it uses, and how these extra ions appear in the molecular network.

**What you will learn**

- the common ion types of one molecule in positive ESI
- co-elution and correlation across samples as evidence that ions belong together
- how to recognise in-source fragments
- why some network edges are not chemistry at all

## Downloads

- [FeatureFinder-local-v365-windows-x86_64-MN-labs.zip](https://github.com/YasinEl/temp_share/releases/download/mn-teaching-materials-2026-10-29/FeatureFinder-local-v365-windows-x86_64-MN-labs.zip) · Feature Finder v365 with the ten MN Lab dashboards and the spectral library (Windows, 25 MB)
- [urine_POS.zip](https://github.com/YasinEl/temp_share/releases/download/urine-pos-test-data-2026-10-28/urine_POS.zip) · urine, positive mode: 11 mzML files + metadata.tsv (135 MB)
- Worksheet to write your answers in: [MN_Lab_5_One_Compound_Many_Features_questions.docx](https://github.com/YasinEl/temp_share/releases/download/mn-teaching-materials-2026-10-29/MN_Lab_5_One_Compound_Many_Features_questions.docx)
- Printable handout (same content as this page): [MN_Lab_5_One_Compound_Many_Features_handout.docx](https://github.com/YasinEl/temp_share/releases/download/mn-teaching-materials-2026-10-29/MN_Lab_5_One_Compound_Many_Features_handout.docx)

## Step by step

**Before you start:** do [Getting started](getting-started.md) with the 11 files of urine_POS (Engine **v1 (classic)**, Quantification **Peak area**), then open **MN Lab 5 · One Compound, Many Features** from the **All plugins** tab.

1. Panel 1 counts the features and the compounds after grouping, and which kinds of extra ions were found. → **Worksheet [Q1](#q1)**
2. Panel 2: pick the **carnitine** example. Panel 3 lists its members with their Δ to the main ion and their type. → **[Q2](#q2)**
3. Panel 4 overlays the XICs of the members (evidence 1); panel 5 plots their areas across samples and gives the correlations (evidence 2). Look for a member that does not fit. → **[Q3](#q3)**
4. Pick a group with an in-source fragment and compare the fragment's m/z with the MS/MS of the main ion. → **[Q4](#q4)**
5. Panel 6 lists the network edges that connect two members of the same compound. → **[Q5](#q5)**

> **Watch out**
>
> - Grouping by co-elution can go wrong in crowded regions (many compounds at the same RT): always check the correlation.
> - Report one value per compound, not per feature, or you count the same molecule several times.

## Questions

Write your answers in the worksheet [MN_Lab_5_One_Compound_Many_Features_questions.docx](https://github.com/YasinEl/temp_share/releases/download/mn-teaching-materials-2026-10-29/MN_Lab_5_One_Compound_Many_Features_questions.docx).

#### Q1

How many features does the run have, and how many compounds after grouping? What fraction of the feature table is “extra” signals of the same molecules?

#### Q2

Open the carnitine example. Name each member: why is there a peak at +1.003, one at +21.98, and smaller ions below the main one?

#### Q3

Evidence 1 and 2: why must isotopes and adducts of one molecule have the same peak shape and the same ratio across samples? What would a *different* compound at the same RT look like?

#### Q4

In-source fragments look exactly like real metabolites in MS1. How can you tell? (Hint: compare the fragment’s m/z with the parent’s MS/MS.)

#### Q5

Panel 6: how many network edges connect two features of the same compound? Should you interpret a “Na instead of H” or “¹³C” edge as a metabolic reaction?

## Background

### One molecule, many ions

In positive electrospray a molecule M is seen mainly as **[M+H]⁺**, but also as **[M+Na]⁺** (+21.982 relative to [M+H]⁺), **[M+K]⁺** (+37.956), **[M+NH₄]⁺** (+17.027), dimers [2M+H]⁺, and its isotope peaks (+1.003, +2.007). Fragile molecules can also break in the ion source before the MS1 scan: **in-source fragments** look exactly like real molecules in MS1.

### Evidence that ions belong together

Ions of one molecule are formed at the same moment from the same molecules, so they **elute together** (same peak shape and apex) and **rise and fall together** across samples (high correlation). A different compound at the same RT has its own peak shape and its own pattern across samples.

| ion | Δ to [M+H]⁺ | carnitine example |
|---|---|---|
| [M+H]⁺ | 0 | 162.113 |
| M+1 isotope | +1.003 | 163.116 |
| [M+Na]⁺ | +21.982 | 184.095 |
| in-source fragment | −59.074 (trimethylamine) | 103.039 |

## Molecules in this lab

Carnitine loses trimethylamine (N(CH₃)₃, 59.074) easily: the in-source fragment at m/z 103.039.

| Structure | Molecule |
|---|---|
| <img src="img/carnitine.png" width="220" alt="L-Carnitine"> | **L-Carnitine**<br>C7H15NO3 · [M+H]⁺ 162.1125<br>body-made: carries fatty acids into mitochondria<br>*in this run: 162.113 @ 12.16 min (everyone)* |
| <img src="img/creatinine.png" width="220" alt="Creatinine"> | **Creatinine**<br>C4H7N3O · [M+H]⁺ 114.0662<br>body-made, from muscle creatine; cleared by the kidney<br>*in this run: 114.066 @ ~9.5 min (everyone)* |

---

[← Lab 4](lab04-from-scans-to-features.md) · [All labs](README.md) · [Lab 6 →](lab06-annotation-propagation.md)
