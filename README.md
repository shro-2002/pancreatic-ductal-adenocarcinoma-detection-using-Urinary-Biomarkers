# Pancreatic Ductal Adenocarcinoma Detection Project

## Introduction

This Python project focuses on the detection of Pancreatic Ductal Adenocarcinoma (PDAC) using urinary biomarkers. The dataset used for this project is sourced from an open-access paper published on December 10, 2020, titled "Urinary biomarkers for pancreatic cancer." The dataset is available under the CC-BY license, and attribution to the original authors, Silvana Debernardi and colleagues, is required.

### Background

Pancreatic cancer is a highly lethal form of cancer, with a five-year survival rate of less than 10%. Early detection significantly improves survival chances. Unfortunately, pancreatic cancer often remains asymptomatic until it reaches an advanced stage. Developing an accurate diagnostic test is crucial for identifying individuals with pancreatic cancer early on.

### The Paper

In the study published in PLOS Medicine, the researchers aimed to create a precise diagnostic test for PDAC. They collected urinary biomarkers from three groups of patients:

1. Healthy controls
2. Patients with non-cancerous pancreatic conditions (e.g., chronic pancreatitis)
3. Patients with Pancreatic Ductal Adenocarcinoma (PDAC)

The dataset includes key features, such as creatinine, LYVE1, REG1B, and TFF1. Age and sex, also included in the dataset, might influence pancreatic cancer incidence. The paper emphasizes the importance of predicting disease presence before formal diagnosis, making it a valuable resource for early detection efforts.

### Dataset

The primary dataset, named "Debernardi et al 2020 data.csv," contains raw data, while the accompanying file "Debernardi et al 2020 documentation.csv" provides detailed documentation of each column, including original column names from the paper.

**Key Biomarkers:**
- **Creatinine:** Indicator of kidney function.
- **LYVE1:** Lymphatic vessel endothelial hyaluronan receptor 1, potentially related to tumor metastasis.
- **REG1B:** Protein associated with pancreas regeneration.
- **TFF1:** Trefoil factor 1, potentially linked to urinary tract regeneration and repair.

Other biomarkers are included but not measured in all patients, serving as additional reference points.

### Prediction Task

The primary goal of this project is to predict the diagnosis, specifically distinguishing between three categories: pancreatic cancer (3), non-cancerous pancreatic condition (2), and healthy (1). The dataset contains information on pancreatic cancer stages and diagnoses for non-cancerous patients, but these won't be available for predictive modeling. The emphasis is on predicting disease presence before formal diagnosis, aligning with the goal of early detection.

## Getting Started

### Prerequisites

Ensure you have Python installed. Additionally, install the required libraries listed in the "requirements.txt" file using:

```bash
pip install -r requirements.txt
```

### Clone Repository
```bash
https://github.com/shro-2002/pancreatic-ductal-adenocarcinoma-detection-using-Urinary-Biomarkers.git
```
### Acknowledgments
This project relies on the dataset provided by Silvana Debernardi and colleagues. Please acknowledge their work when using this dataset.
