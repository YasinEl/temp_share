# MN Lab 8 · Positive vs Negative

[← Lab 7](lab07-can-i-trust-this-feature.md) · [All labs](README.md) · [Lab 9 →](lab09-modifinder.md)

**About 45 min** · Study design

Electrospray can make positive or negative ions. Each polarity sees a different part of the metabolome. You will compare the same urines measured in both modes.

**What you will learn**

- which molecules ionise in positive and which in negative mode
- how little two polarities overlap
- the positive-mode bias of spectral libraries
- how to spot impossible library hits from the mass defect
- sulfates as a negative-mode speciality

## Downloads

- [FeatureFinder-local-v365-windows-x86_64-MN-labs.zip](https://github.com/YasinEl/temp_share/releases/download/mn-teaching-materials-2026-10-29/FeatureFinder-local-v365-windows-x86_64-MN-labs.zip) · Feature Finder v365 with the ten MN Labs, the GNPS libraries and all handouts (Windows, 27 MB)
- [urine_NEG.zip](https://github.com/YasinEl/temp_share/releases/download/mn-teaching-materials-2026-10-29/urine_NEG.zip) · urine, negative mode: 11 mzML files + metadata.tsv (138 MB)
- Worksheet to write your answers in: [MN_Lab_8_Positive_vs_Negative_questions.docx](https://github.com/YasinEl/temp_share/releases/download/mn-teaching-materials-2026-10-29/MN_Lab_8_Positive_vs_Negative_questions.docx)
- Printable handout (same content as this page): [MN_Lab_8_Positive_vs_Negative_handout.docx](https://github.com/YasinEl/temp_share/releases/download/mn-teaching-materials-2026-10-29/MN_Lab_8_Positive_vs_Negative_handout.docx)

## Step by step

Start the app and open the lab as in [Getting started](getting-started.md), but with the files named in step 1 below.

1. Process the 11 files of **urine_NEG** in the app (negative mode) with their **metadata.tsv** and **Engine v1 (classic)**, and open MN Lab 8 there.
2. Panel 1: upload the positive run's **aligned_features.csv** and **library_matches.tsv** (from your own positive run, or the copies in MN_teaching\handout\urine_POS_results).
3. Panel 2, **who sees what**: counts, the RT/mass map and the bars per minute (positive only / negative only / both). → **Worksheet [Q1](#q1), [Q2](#q2)**
4. Panel 3, library matches side by side: choose **named, and the molecule is seen in both polarities** and click a compound. Panel 4 shows its areas in both modes. → **[Q3](#q3)**
5. Choose **precursor m/z does not fit the library spectrum** and look at “citric acid” and “mannitol”. → **[Q4](#q4)**
6. Panel 5, the sulfate finder. → **[Q5](#q5)**

> **Watch out**
>
> - Never compare peak areas between polarities: compare samples within one polarity.
> - If a drug class is missing in positive mode (e.g. diuretics), look in negative mode.

## Questions

Write your answers in the worksheet [MN_Lab_8_Positive_vs_Negative_questions.docx](https://github.com/YasinEl/temp_share/releases/download/mn-teaching-materials-2026-10-29/MN_Lab_8_Positive_vs_Negative_questions.docx).

#### Q1

How many features does each polarity find, and how many molecules are seen in both? Is the overlap larger or smaller than you expected?

#### Q2

In the RT/m/z map, where do the “negative only” features sit? HILIC retains polar compounds longer: which kinds of molecules elute late and ionise only negatively?

#### Q3

Choose “named, and the molecule is seen in both polarities” and pick a compound. Do its positive and negative areas rise and fall together across the patients? What does that tell you about using either polarity for quantification?

#### Q4

Choose “precursor m/z does not fit the library spectrum”. Look at “citric acid” at m/z 190.88 and “mannitol” at 180.93. What m/z should [M−H]⁻ of citric acid have? Look at the decimals (the mass defect): can an organic molecule of this size have a mass defect of −0.1? What else could it be? What should the library search have checked?

#### Q5

How many negative-mode spectra show the sulfate fragments (HSO₄⁻ 96.960, SO₃⁻ 79.957)? How many of those molecules were seen at all in positive mode? Which drugs and body-made compounds are excreted as sulfates?

## Background

### Ionisation

In **positive** mode molecules take up a proton ([M+H]⁺): bases such as amines, many drugs. In **negative** mode they lose one ([M−H]⁻): acids such as carboxylic acids, sulfates, phenols, glucuronides. Many molecules ionise mainly in one mode. The [M+H]⁺ and [M−H]⁻ of one molecule differ by 2 × 1.00728 = 2.01455.

### Mass defect

The **mass defect** is the part of the mass after the decimal point relative to the nominal mass. Organic molecules (C, H, N, O) have small positive defects that grow with size (H = 1.0078). Heavy inorganic atoms (Na, K, Cl, metals) have negative defects. An ion at m/z 190.88 (defect −0.12) cannot be an organic acid: it is a salt cluster.

### Sulfates

Sulfate conjugates (drug metabolites, phenolic compounds from food, steroid sulfates, uraemic toxins such as indoxyl sulfate) give characteristic fragments in negative mode: **HSO₄⁻ (96.960)** and **SO₃⁻• (79.957)**.

## Molecules in this lab

For citric acid and mannitol compare the true [M−H]⁻ (given below each structure) with the library “hits” at m/z 190.88 and 180.93.

| Structure | Molecule |
|---|---|
| <img src="img/guanidinobutanoate.png" width="220" alt="4-Guanidinobutanoic acid"> | **4-Guanidinobutanoic acid**<br>C5H11N3O2 · [M+H]⁺ 146.0924<br>body-made; seen in both polarities<br>*in this run: 146.092 [M+H]⁺ / 144.078 [M−H]⁻ @ 13.4 min* |
| <img src="img/paracetamol_sulfate.png" width="220" alt="Paracetamol sulfate"> | **Paracetamol sulfate**<br>C8H9NO5S · [M+H]⁺ 232.0274<br>phase II metabolite (+79.957)<br>*in this run: 232.027 (POS) / 230.013 [M−H]⁻ (NEG)* |
| <img src="img/indoxyl_sulfate.png" width="220" alt="Indoxyl sulfate"> | **Indoxyl sulfate**<br>C8H7NO4S · [M−H]⁻ 212.0023<br>gut-microbial uraemic toxin; a typical sulfate<br>*in this run: 212.002 [M−H]⁻ @ 7.14 min (every patient)* |
| <img src="img/citric_acid.png" width="220" alt="Citric acid"> | **Citric acid**<br>C6H8O7 · [M−H]⁻ 191.0197<br>true [M−H]⁻ 191.020 — not the 190.88 “hit” |
| <img src="img/mannitol.png" width="220" alt="Mannitol"> | **Mannitol**<br>C6H14O6 · [M−H]⁻ 181.0718<br>true [M−H]⁻ 181.072 — not the 180.93 “hit” |

---

[← Lab 7](lab07-can-i-trust-this-feature.md) · [All labs](README.md) · [Lab 9 →](lab09-modifinder.md)
