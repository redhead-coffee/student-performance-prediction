# Student Performance Prediction & Academic Risk Analysis

A Data Science and Machine Learning project for analyzing student academic performance, predicting final examination marks, identifying students at academic risk, and segmenting students based on their learning and performance patterns.

---

## Overview

Student academic performance can be influenced by multiple factors such as attendance, study habits, previous academic performance, assignment performance, internal assessments, and student support systems.

This project develops a complete Data Science and Machine Learning pipeline to analyze these factors and generate useful academic performance insights.

The system focuses on four major Machine Learning tasks:

- **Linear Regression** — Predict final examination marks
- **Logistic Regression** — Predict Pass/Fail probability
- **K-Nearest Neighbors (KNN)** — Identify students with similar academic profiles
- **K-Means Clustering** — Segment students into performance groups

The final system also provides an **academic risk level** and identifies the major factors associated with student performance.

---

## Dataset

### Synthetic Dataset

This project uses a **synthetically generated student-performance dataset**.

The dataset was created using:

- Python
- Faker
- NumPy
- Pandas

A synthetic dataset was selected because the available public datasets did not contain all the variables required by the project specification.

The generated dataset does **not represent real students** and does not contain real personal or academic records.

The synthetic data is designed to contain plausible relationships between academic and behavioral variables while also incorporating controlled noise and data-quality issues for demonstrating the preprocessing workflow.

---

## Dataset Features

| Feature | Description | Type |
|---|---|---|
| `StudentID` | Unique student identifier | ID |
| `Name` | Synthetic student name | Categorical |
| `Age` | Student age | Numerical |
| `Gender` | Student gender | Categorical |
| `AttendancePct` | Student attendance percentage | Numerical |
| `StudyHoursPerWeek` | Weekly study hours | Numerical |
| `PreviousGrade` | Previous academic grade | Numerical |
| `AssignmentMarks` | Assignment performance | Numerical |
| `InternalAssessmentMarks` | Internal assessment performance | Numerical |
| `OnlineClasses` | Participation in online classes | Categorical |
| `ExtracurricularActivities` | Number of extracurricular activities | Numerical |
| `ParentalSupport` | Level of parental support | Categorical |
| `FinalExamMarks` | Final examination marks | **Target** |

---

## 🔄 Project Workflow

```text
                    ┌──────────────────┐
                    │ Synthetic Dataset│
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │ Data Preprocessing│
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │ Feature Engineering│
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │ Exploratory Data │
                    │     Analysis     │
                    └────────┬─────────┘
                             │
              ┌──────────────┼──────────────┐
              │              │              │
              ▼              ▼              ▼
        Linear Regression  Logistic       KNN
                           Regression
              │              │              │
              ▼              ▼              ▼
        Final Marks       Pass/Fail    Similar Students
              │
              │
              ▼
        ┌──────────────┐
        │ K-Means      │
        │ Clustering   │
        └──────┬───────┘
               │
               ▼
       Performance Segments
               │
               ▼
        Academic Risk
               │
               ▼
        Final Predictions
```

---

## 🧹 Data Preprocessing

The preprocessing stage includes:

- Missing-value detection and treatment
- Duplicate-record detection and removal
- Invalid-value detection
- Outlier analysis
- Categorical-value normalization
- Categorical encoding
- Numerical feature scaling
- Feature selection
- Train/test splitting

Some controlled data-quality issues are intentionally introduced into the synthetic dataset so that the preprocessing workflow can be demonstrated.

---

## ⚙️ Feature Engineering

Additional features may be created from the original variables to improve the representation of student learning patterns.

Examples include:

- Attendance and study-hour interaction
- Academic preparation indicators
- Aggregated academic performance indicators
- Pass/Fail target
- Academic risk level
- Cluster-based performance segment

Feature engineering is performed using information available before the target prediction to avoid target leakage.

---

## Machine Learning Models

### 1. Linear Regression

Used to predict:

> **Final Examination Marks**

Evaluation metrics:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R² Score

---

### 2. Logistic Regression

Used to predict:

> **Pass / Fail**

The classification target is derived from the final examination marks using the defined passing threshold.

Evaluation metrics include:

- Accuracy
- Precision
- Recall
- F1-Score
- ROC-AUC
- Confusion Matrix

---

### 3. K-Nearest Neighbors

KNN is used to identify students with similar academic and learning profiles based on features such as:

- Attendance
- Study hours
- Previous grade
- Assignment performance
- Internal assessment
- Other relevant academic characteristics

---

### 4. K-Means Clustering

K-Means is used to segment students into performance groups such as:

- **High Performing**
- **Average**
- **At-Risk**

The cluster labels are assigned after examining the characteristics of each generated cluster rather than assuming that the numerical cluster IDs have inherent meaning.

---

## ⚠️ Academic Risk Analysis

The project provides three academic risk levels:

| Risk Level | General Interpretation |
|---|---|
| 🟢 Low | Student is performing satisfactorily and has a low predicted risk of failure |
| 🟡 Medium | Student may require additional academic attention |
| 🔴 High | Student shows indicators associated with potential academic difficulty |

Risk thresholds are defined as part of the project methodology and are intended for demonstration purposes rather than as universal educational standards.

---

## Expected Outputs

For an individual student, the system can provide:

```text
Predicted Final Examination Marks
Pass / Fail Prediction
Pass Probability
Academic Risk Level
Performance Segment
Important Performance Factors
Similar Student Profiles
```

Example:

```text
-----------------------------------------
     STUDENT PERFORMANCE ANALYSIS
-----------------------------------------

Predicted Final Marks : 74.6 / 100

Pass Probability      : 92.3%

Result                : PASS

Academic Risk         : LOW

Performance Segment   : HIGH PERFORMING

Major Factors:
1. Previous Grade
2. Internal Assessment
3. Attendance
4. Assignment Marks
5. Study Hours
```

*Example output shown for illustration only.*

---

## 📁 Project Structure

```text
student-performance-prediction/
│
├── README.md
├── LICENSE
├── requirements.txt
├── .gitignore
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   ├── 01_data_generation.ipynb
│   ├── 02_data_preprocessing.ipynb
│   ├── 03_exploratory_data_analysis.ipynb
│   ├── 04_linear_regression.ipynb
│   ├── 05_logistic_regression.ipynb
│   ├── 06_knn_analysis.ipynb
│   ├── 07_kmeans_clustering.ipynb
│   └── 08_model_comparison.ipynb
│
├── src/
│   ├── data_generation.py
│   ├── preprocessing.py
│   ├── feature_engineering.py
│   └── evaluation.py
│
├── models/
│   ├── linear_regression.pkl
│   ├── logistic_regression.pkl
│   ├── knn.pkl
│   └── kmeans.pkl
│
├── results/
│   ├── figures/
│   └── metrics/
│
├── app/
│   └── app.py
│
└── docs/
    └── methodology.md
```

---

## Technologies Used

### Programming

- Python

### Data Processing

- Pandas
- NumPy

### Data Generation

- Faker

### Visualization

- Matplotlib
- Seaborn

### Machine Learning

- Scikit-learn

### Development Environment

- Jupyter Notebook
- Kaggle Notebooks

### Optional Deployment

- Streamlit

---

## 📦 Installation

Clone the repository:

```bash
git clone https://github.com/<your-username>/student-performance-prediction.git
cd student-performance-prediction
```

Install the required dependencies:

```bash
pip install -r requirements.txt
```

---

## Usage

### 1. Generate the dataset

Run:

```text
notebooks/01_data_generation.ipynb
```

This generates the synthetic student-performance dataset.

### 2. Preprocess the dataset

Run:

```text
notebooks/02_data_preprocessing.ipynb
```

### 3. Perform exploratory analysis

Run:

```text
notebooks/03_exploratory_data_analysis.ipynb
```

### 4. Train the Machine Learning models

Run the model-specific notebooks:

```text
04_linear_regression.ipynb
05_logistic_regression.ipynb
06_knn_analysis.ipynb
07_kmeans_clustering.ipynb
```

### 5. Compare models

Run:

```text
08_model_comparison.ipynb
```

---

## Model Evaluation

The final project compares the models using appropriate evaluation metrics.

Regression:

```text
MAE
RMSE
R²
```

Classification:

```text
Accuracy
Precision
Recall
F1-Score
ROC-AUC
Confusion Matrix
```

Clustering:

```text
Silhouette Score
Cluster Profiles
```

Final model results will be added to the `results/metrics/` directory after model development.

---

## 🔐 Data Privacy

No real student records or personally identifiable academic information are used in this project.

All student names and academic records are synthetically generated.

---

## 📚 Project Type

**Academic Data Science & Machine Learning Project**

This project is intended for educational purposes, demonstrating a complete machine-learning workflow from dataset generation and preprocessing to prediction, clustering, evaluation, and interpretation.

---