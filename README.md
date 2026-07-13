# JMIR-95929-pipelines (HF--XGBoost)
Source code for:

"A Disease Trajectory Representation Framework with Risk-Aware Pseudotime Analysis for Longitudinal Electronic Health Records: Application to Heart Failure Risk Stratification"

## Data
This study utilizes the MIMIC-IV dataset. Due to **PhysioNet data credentialing and privacy restrictions**, individual admission-level clinical data cannot be publically hosted or redistributed within this repository.
*   **In this Repository (Sample Data)**: We set `n_splits=5` in the provided example script. Because this dummy dataset is small, a higher fold count would lead to empty splits or highly unstable stratification during cross-validation.
*   **In the Paper (Formal Evaluation)**: For the full dataset and the official results reported in the paper, **`n_splits=10` (10-fold cross-validation)** was used to provide a more rigorous evaluation.
*   **Note: The provided sample_data.csv is a minimal synthetic dataset designed solely to verify that the pipeline runs without execution errors. Because of the small sample size, the calculated performance metrics (e.g., ROC AUC) on this dummy data may be uninformative or heavily skewed.

## Data Schema  : 
    'subject_id',   # Unique patient identifier (Static across all longitudinal admissions)
    'hadm_id',      # Unique encounter/admission identifier for the index hospitalization
    'icd3_list',    # List of 3-digit ICD diagnosis codes recorded during the index admission(ex.["E11","N18","I25"...])
    'admittime',    # Timestamp of hospital admission for the index episode
    'deathtime',    # Timestamp of patient death (Null if the patient survived/censored)
    'los',          # Length of stay for the current hospitalization (Measured in days)
    'age',          # Patient age at the time of the index admission (Baseline chronological age)
    'gender'        # Patient biological sex at birth (Demographic baseline factor)
*   **Granularity**: Each row represents a single **admission-level** record (i.e., one row is one admission).
*   **Structure**: If a patient has multiple admissions over time, they will appear across multiple rows sharing the same patient identifier (`id1` / `subject_id`), ordered chronologically for longitudinal analysis.

## Pipeline
To ensure the reproducibility of our computational methodology, this repository contains the complete pipeline including
1. Preprocessing
2. Node2Vec Embedding
3. XGBoost Training
4. Evaluation


## Requirements
Python 3.8.18

## Citation
Please cite our paper if you use this code.
