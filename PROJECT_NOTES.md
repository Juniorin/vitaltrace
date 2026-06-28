# VitalTrace

## What this is about
In healthcare, catching a disease after symptoms show up is often too late. By 
the time a lot of conditions become obvious, the chance to actually do something 
about them has already started slipping away. Machine learning gives doctors a 
way to flag risk earlier, by picking up on patterns in a patient's data that 
might not jump out to someone looking at a single chart at a single point in time.

This project uses structured Electronic Health Records (EHRs) and vital sign data 
to build a model that estimates how likely a patient is to face a serious health 
event, things like complications, deterioration, or readmission, before it 
actually happens instead of after.

The goal here isn't just getting a model that works. It's figuring out which 
signals in the data actually matter for prediction, and being honest about how 
much a model like this could really be trusted in an actual clinical setting.
## Status
Currently: Completed logistic regression model

Last updated: **2026-06-28**

## Terms I learned
- **Electronic Health Records (EHRs)**: Patient records that contain vital signs and lab results including blood pressure, heart rate, respiratory rate, and body temperature

## Decisions and why
### 2026-06-28 - First Baseline Model
Considered: SVM, XGBoost, Random Forest, Neural Network 

Picked: **Logistic Regression**

Why: fast to train, simple enough to trust the result without tuning, interpretable coefficients to sanity check feature relationships, and matches binary classification structure of problem

## Open questions / things to revisit
- What model to choose?
    - Model choice depends on what we are predicting (binary here) and how much data we have. It depends what tradeoffs we want as well like prioritizing speed or accuracy. 

## Quick links
- Dataset: Kaggle Vitals & Variables - https://www.kaggle.com/competitions/kaggle-community-olympiad-vitals-variables-predicting-patient-outcomes/overview
- Papers: 
- Links: 
    - ML Algo Cheat Sheet: https://learn.microsoft.com/en-us/azure/machine-learning/algorithm-cheat-sheet?view=azureml-api-1 