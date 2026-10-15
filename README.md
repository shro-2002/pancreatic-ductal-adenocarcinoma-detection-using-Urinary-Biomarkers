# Pancreatic Ductal Adenocarcinoma Detection Project

## Introduction

This Python project focuses on the detection of Pancreatic Ductal Adenocarcinoma (PDAC) using urinary biomarkers. The data come from Debernardi et al. (2020), *PLOS Medicine* ([doi:10.1371/journal.pmed.1003489](https://doi.org/10.1371/journal.pmed.1003489)); please credit the original authors.

### Background

Pancreatic cancer is a highly lethal form of cancer, with a five-year survival rate of less than 10%. Early detection significantly improves survival chances. Unfortunately, pancreatic cancer often remains asymptomatic until it reaches an advanced stage. Developing an accurate diagnostic test is crucial for identifying individuals with pancreatic cancer early on.

### The Paper

In the study published in PLOS Medicine, the researchers aimed to create a precise diagnostic test for PDAC. They collected urinary biomarkers from three groups of patients:

1. Healthy controls
2. Patients with non-cancerous pancreatic conditions (e.g., chronic pancreatitis)
3. Patients with Pancreatic Ductal Adenocarcinoma (PDAC)

The dataset includes key features, such as creatinine, LYVE1, REG1B, and TFF1. Age and sex, also included in the dataset, might influence pancreatic cancer incidence. The paper emphasizes the importance of predicting disease presence before formal diagnosis, making it a valuable resource for early detection efforts.

### Dataset

The primary dataset, named "Debernardi et al 2020 data.csv" contains raw data, while the accompanying file "Debernardi et al 2020 documentation.csv" provides detailed documentation of each column, including original column names from the paper.

**Key Biomarkers:**
- **Creatinine:** Indicator of kidney function.
- **LYVE1:** Lymphatic vessel endothelial hyaluronan receptor 1, potentially related to tumor metastasis.
- **REG1B:** Protein associated with pancreas regeneration.
- **TFF1:** Trefoil factor 1, potentially linked to urinary tract regeneration and repair.

Other biomarkers are included but not measured in all patients, serving as additional reference points.

### Prediction Task

The dataset labels three groups: healthy (1), non-cancerous pancreatic condition (2) and pancreatic cancer (3). This project frames it as a **binary** task: PDAC (3) vs not PDAC (1 and 2). The `stage` and `benign_sample_diagnosis` columns are excluded because they encode the label.

## Results (leak-free, Oct 2026)

Repeated stratified 5-fold cross-validation (5 folds × 3 repeats), mean ± std. Imputation and scaling are fitted inside each training fold; class imbalance is handled with class weights. Source: [`notebook.ipynb`](notebook.ipynb), also saved as [`results.csv`](results.csv).

| Features | Model | ROC AUC | Recall (PDAC) | Specificity | Balanced accuracy |
| --- | --- | --- | --- | --- | --- |
| Urine panel | Logistic regression | 0.867 ± 0.033 | 0.762 ± 0.053 | 0.835 ± 0.045 | 0.798 ± 0.033 |
| Urine panel | Random forest | 0.884 ± 0.033 | 0.749 ± 0.038 | 0.838 ± 0.049 | 0.793 ± 0.029 |
| Urine panel | LightGBM | 0.870 ± 0.030 | 0.692 ± 0.069 | 0.842 ± 0.044 | 0.767 ± 0.046 |
| Urine + plasma CA19-9 | Logistic regression | 0.910 ± 0.030 | 0.806 ± 0.042 | 0.876 ± 0.036 | 0.841 ± 0.030 |
| Urine + plasma CA19-9 | Random forest | 0.945 ± 0.017 | 0.843 ± 0.059 | 0.906 ± 0.043 | 0.874 ± 0.029 |
| Urine + plasma CA19-9 | LightGBM | 0.939 ± 0.022 | 0.811 ± 0.078 | 0.904 ± 0.052 | 0.857 ± 0.043 |

Urine panel = age, sex, creatinine, LYVE1, REG1B, TFF1. CA19-9 is a blood marker missing for 240 of 590 patients; it is imputed within training folds.

## Correction

An earlier version of this repository reported recall of 0.97. That number came from a flawed protocol: the PDAC rows were duplicated **before** the train/test split, so 59 of 158 test rows were exact copies of training rows, and the imputer was fitted on all data. The notebook now reproduces that protocol in its last section so the size of the leak is visible. The leak-free recall above (0.69–0.84 depending on features and model) is the honest result.

## Limitations

- One public dataset from one study (590 patients); no external validation.
- Default decision threshold; no calibration or threshold tuning.
- A learning project, not a diagnostic tool.

## How to run

```bash
git clone https://github.com/shro-2002/pancreatic-ductal-adenocarcinoma-detection-using-Urinary-Biomarkers.git
cd pancreatic-ductal-adenocarcinoma-detection-using-Urinary-Biomarkers
pip install -r requirements.txt
jupyter nbconvert --to notebook --execute notebook.ipynb
```

## Acknowledgments

Data: Debernardi S. et al. (2020) "A combination of urinary biomarker panel and PancRISK score for earlier detection of pancreatic cancer: A case–control study", *PLOS Medicine* 17(12): e1003489. Please cite the original authors when using the data.
