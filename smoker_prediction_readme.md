# Reproducible research project

 This project is reproduced research of previously made by Viktoria and Maxim for Advanced Econometrics lesson. The original research "Smoker Status Prediction" was done in R. The research investigates the prediction of smoking status using a variety of biometric and health-related variables

## Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Installation](#installation)
- [Project Structure](#project-structure)
- [Usage](#usage)
- [Methodology](#methodology)
- [Results](#results)
- [Feature Engineering](#feature-engineering)
- [Model Performance](#model-performance)

## Overview

 This study examines the prediction of smoking status using a variety of biometric and health-related variables. Using logistic regression models, the study aims to identify
 significant predictors of smoking status and quantify their impact through odds ratios and marginal effects. The analysis focuses on key variables, including waist circumference,
 serum creatinine level, and hemoglobin level. The results of the study revealed significant associations between these variables and smoking status, providing insight into potential biomarkers for
 smoking.

## Dataset

The dataset consists of **38,984 patient records** with **23 features** (22 bio-signals + smoking status).

**Source**: [Kaggle - Smoker Status Prediction Dataset](https://www.kaggle.com/datasets/gauravduttakiit/smoker-status-prediction)

### Features Description

| **Name**            | **Description**                                                                                                                                          |
|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Age                 | Age of patient, grouped by 5-year increments                                                                                                            |
| Height              | Height of patient, grouped by 5-cm increments                                                                                                           |
| Weight              | Weight of patient, grouped by 5-kg increments                                                                                                           |
| Waist               | Waist circumference in cm                                                                                                                              |
| Eyesight (left)     | Visual acuity in left eye from 0.1 to 2.0 (higher is better), where 1.0 is equivalent to 20/20, blindness is 9.9                                         |
| Eyesight (right)    | Visual acuity in right eye from 0.1 to 2.0 (higher is better), where 1.0 is equivalent to 20/20, blindness is 9.9                                        |
| Hearing (left)      | Hearing in left ear where 1=normal, 2=abnormal                                                                                                          |
| Hearing (right)     | Hearing in right ear where 1=normal, 2=abnormal                                                                                                         |
| Systolic            | Blood pressure, amount of pressure experienced by the arteries when the heart is contracting                                                           |
| Relaxation          | Blood pressure (diastolic), amount of pressure experienced by the arteries when the heart is relaxing                                                  |
| Fasting Blood Sugar | Blood sugar level (concentration per 100ml of blood) before eating                                                                                     |
| Cholesterol         | Sum of ester-type and non-ester-type cholesterol                                                                                                        |
| Triglyceride        | Amount of simple and neutral lipids in blood                                                                                                           |
| HDL                 | High Density Lipoprotein, "good" cholesterol, absorbs cholesterol in the blood and carries it back to the liver                                        |
| LDL                 | Low Density Lipoprotein, "bad" cholesterol, makes up most of body's cholesterol. High levels of this raise risk for heart disease and stroke.          |
| Hemoglobin          | Protein contained in red blood cells that delivers oxygen to the tissues                                                                               |
| Urine Protein       | Amount of protein mixed in urine                                                                                                                       |
| Serum Creatinine    | Creatinine level, Creatinine is a waste product in your blood that comes from your muscles. Healthy kidneys filter creatinine out of your blood.       |
| AST                 | Aspartate transaminase, an enzyme that helps the body break down amino acids. An increase in AST levels may mean liver damage, liver disease, or muscle damage. |
| ALT                 | Alanine transaminase, an enzyme found in the liver that helps convert proteins into energy for liver cells. When the liver is damaged, ALT increases.  |
| GTP                 | Gamma-glutamyltransferase (GGT), an enzyme in the blood. Higher-than-usual levels may mean liver or bile duct damage.                                   |
| Dental Caries       | Cavities, 0=absent, 1=present                                                                                                                           |
| Smoking             | 0=non-smoker, 1=smoker                                                                                                                                  |

## Installation

### Prerequisites
- Python 3.10+
- pip package manager

### Setup Instructions

1. **Clone the repository**
```bash
git clone <repository-url>
```

2. **Run 2nd cell of main.ipynb file**

3. **Activate virtual environment**
```bash
# Windows
venv\Scripts\activate

# macOS/Linux
source venv/bin/activate
```

4. **Install Jupyter kernel**
```bash
pip install ipykernel
```

5. **Install dependencies**
```bash
pip install -r requirements.txt
```

### Required Packages
- jupyter 1.1.1
- notebook 7.4.3
- pandas 2.2.3
- seaborn 0.13.2
- scipy 1.15.3
- scikit-learn 1.6.1

## Project Structure

```
smoker-prediction/
├── main.ipynb              # Main notebook
├── requirements.txt        # Python packages listed
├── Data/
│   └── dataset.csv        # Raw dataset
├── README.md              # Project documentation
└── venv/                  # Virtual environment
```

## Usage

1. **Open Jupyter Notebook**

2. **Run the analysis**
   - Execute cells one by one
   - The notebook is divided into sections:
     - Environment setup
     - Data loading and exploration
     - EDA
     - Feature engineering
     - Machine learning modeling

## Methodology

### 1. Exploratory Data Analysis
- Distribution analysis by smoking status
- Correlation matrix visualization
- Feature relationship exploration
- Statistical summaries for smokers vs non-smokers

### 2. Feature Engineering
- **Anthropometric features**: BMI, waist-to-height ratio, obesity flags
- **Cardiovascular features**: Pulse pressure, hypertension indicators, BP categories
- **Lipid profile features**: Cholesterol ratios, atherogenic indices
- **Liver function features**: Enzyme ratios, elevation flags
- **Metabolic features**: Diabetes risk, metabolic syndrome scores
- **PCA components**: Dimensionality reduction on lipid and liver profiles

### 3. Machine Learning Pipeline
- **Data preprocessing**: Feature scaling, categorical encoding
- **Feature selection**
- **Model training**: Multiple algorithms comparison
- **Hyperparameter optimization**: Grid search for best models
- **Ensemble methods**: Voting classifier with top performers

## Results

### Model Performance (Test Set)

| Model | AUC Score | Accuracy | F1 Score |
|-------|-----------|----------|----------|
| **Optimized Random Forest** | **0.8808** | **0.8003** | **0.7256** |
| Ensemble Model | 0.8628 | 0.7852 | 0.7081 |
| Gradient Boosting | 0.8381 | 0.7576 | 0.6715 |
| SVM | 0.8218 | 0.7486 | 0.6530 |

### Top Predictive Features
| Rank | Feature | Importance Score | Description |
|------|---------|------------------|-------------|
| 1 | **Hemoglobin** | 0.1228 | Oxygen-carrying protein in red blood cells |
| 2 | **GTP** | 0.1165 | Gamma-glutamyltransferase (liver enzyme) |
| 3 | **Height** | 0.1051 | Patient height measurement |
| 4 | **Triglyceride** | 0.0830 | Blood lipid levels |
| 5 | **HDL** | 0.0652 | High-density lipoprotein ("good" cholesterol) |

## Feature Engineering

The project creates **38 new features** from the original 23, including:

- **Health risk scores**: Cardiovascular, metabolic syndrome, overall health
- **Medical ratios**: Cholesterol ratios, liver enzyme ratios
- **Categorical indicators**: BMI categories, blood pressure stages
- **Composite scores**: Multiple risk factor combinations
- **PCA components**: Reduced dimensionality representations

## Model Performance

### Cross-Validation Results
- **5-fold stratified cross-validation**
- **Robust evaluation** across different data splits
- **Hyperparameter optimization** using grid search
- **Feature importance analysis** for interpretability

### Visualization Outputs
- ROC curves comparison
- Precision-recall curves
- Feature importance rankings
- Model performance metrics
- Distribution analysis by smoking status


## Contribution of developers
| StudentID | Name | GitHub | Responses  |
|------|---------|------------------|-------------|
| 463532 | Bogdan Jasiński | [BogdanJas](https://github.com/BogdanJas) | Reproducibility, Data loading, modeling  |
| 465710 | Viktoria Kurtsinovskaia | [kurctory](https://github.com/kurctory) | EDA |
| 465708 | Maxim Lichko | [maxim-lichko](https://github.com/maxim-lichko) | Modeling |

---

**Disclaimer**: This project is for educational and research purposes only. The models should not be used for actual medical diagnosis without proper clinical validation and regulatory approval.