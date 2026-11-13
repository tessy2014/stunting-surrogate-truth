# Do Surrogate Models Recover the Truth?

Code for the paper **"Do Surrogate Models Recover the Truth? Evaluating Global Surrogate Explanations against WHO Growth Standard Rules in Child Stunting Classification"** (T. Badriyah, S. W. Arifhana, A. Zakiyah).

The notebook checks whether global surrogate decision trees, fitted to black-box classifiers (random forest, gradient boosting, MLP, XGBoost), recover the WHO length/height-for-age rule that defines the labels of a public stunting dataset.

## Contents

| File | Description |
|---|---|
| `Paper6_Surrogate_Truth_Recovery.ipynb` | Full analysis (Sections 1–11 → Tables T1–T8, Figures F1–F7) |
| `requirements.txt` | Python packages |

## 1. Install

```bash
pip install -r requirements.txt
```

Python 3.9 or newer is recommended.

## 2. Get the data (not included in this repository)

**Kaggle dataset.** Download *Stunting Toddler (Balita) Detection (121K rows)* from
https://www.kaggle.com/datasets/rendiputra/stunting-balita-detection-121k-rows
(a free Kaggle account is required), unzip it and save the CSV as:

```
data/data_balita.csv
```

**WHO growth standard tables.** The notebook downloads the four WHO length/height-for-age z-score tables automatically. If the download is blocked, get them manually from
https://www.who.int/toolkits/child-growth-standards/standards/length-height-for-age
(*Tables → z-scores*, Excel files for boys and girls, *Birth to 2 years* and *2 to 5 years*) and save them in a folder named `who/`.

Expected layout:

```
stunting-surrogate-truth/
├── Paper6_Surrogate_Truth_Recovery.ipynb
├── data/
│   └── data_balita.csv
└── who/
    ├── lhfa_boys_0-to-2-years_zscores.xlsx
    ├── lhfa_boys_2-to-5-years_zscores.xlsx
    ├── lhfa_girls_0-to-2-years_zscores.xlsx
    └── lhfa_girls_2-to-5-years_zscores.xlsx
```

## 3. Run

```bash
jupyter notebook Paper6_Surrogate_Truth_Recovery.ipynb
```

Then choose *Run All*. In the configuration cell, keep `SMOKE_TEST = False` and `QUICK = False` to reproduce the paper (the full run takes roughly 30–60 minutes on a laptop; the simulation in Section 9 is the slowest part).
`SMOKE_TEST = True` runs on synthetic data with approximate WHO values and is meant only for checking that the code works.

All tables and figures are written to `outputs_paper6/`.

## Data sources and licences

- Kaggle dataset: R. Putra, *Stunting Toddler (Balita) Detection (121K rows)*, Kaggle, 2023. Please follow the licence shown on the Kaggle page.
- WHO Multicentre Growth Reference Study Group, *WHO Child Growth Standards*, World Health Organization, Geneva, 2006.
- Classification cut-offs: Regulation of the Minister of Health of the Republic of Indonesia No. 2 of 2020 on Child Anthropometric Standards.

## Citation

If you use this code, please cite the paper (citation details will be added after publication).

## Contact

Tessy Badriyah — Department of Informatics and Computer Engineering, Politeknik Elektronika Negeri Surabaya, Indonesia — tessy@pens.ac.id
