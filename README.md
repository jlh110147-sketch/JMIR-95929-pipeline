# JMIR-95929-pipelines (HF--XGBoost)
Source code for:

"A Risk-Aware Pseudotime Approach for Modeling Heart Failure Progression: A Geometric Analysis of Longitudinal Electronic Health Record Data"

## Data
This study uses MIMIC-IV.

Visit-level data are not included due to PhysioNet restrictions.


## Data Schema  : one row is one admission
    'subject_id',   # Unique patient identifier (Static across all longitudinal admissions)
    'hadm_id',      # Unique encounter/admission identifier for the index hospitalization
    'icd3_list',    # List of 3-digit ICD diagnosis codes recorded during the index admission(ex.["E11","N18","I25"...])
    'admittime',    # Timestamp of hospital admission for the index episode
    'deathtime',    # Timestamp of patient death (Null if the patient survived/censored)
    'los',          # Length of stay for the current hospitalization (Measured in days)
    'age',          # Patient age at the time of the index admission (Baseline chronological age)
    'gender'        # Patient biological sex at birth (Demographic baseline factor)


## Pipeline
1. Preprocessing
2. Node2Vec Embedding
3. XGBoost Training
4. Evaluation

## Requirements
Python 3.8.18

## Citation
Please cite our paper if you use this code.
