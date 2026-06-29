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
Currently: Chose XGBoost as next model 

Last updated: **2026-06-28**

## Terms
- **Electronic Health Records (EHRs)**: Patient records that contain vital signs and lab results including blood pressure, heart rate, respiratory rate, and body temperature

- **Logistic Regression**: A model that estimates the probability of a binary outcome by fitting a straight-line relationship between features and the log-odds of the target. Best at problems where features relate to the outcome in an additive way and where interprtable coefficients matter. It does not capture non-linear relationships and needs feature scaling to fit properly. Why use it: fast, simple, gives a real baseline for other models.

- **Boosted Trees**: A family of models that build decision trees one at a time(sequential), where each new tree corrects the mistakes of the trees before it. Best at capturing non-linear patterns without manual engineering. It is more prone to overfitting if left untuned and more hyperparameters to manage. Why use it: boosting combines many weak trees int a much stronger model

- **XGBoost**: A gradient boosted tree, optimized for speed and performance. It excels at tabular and structured data. However, it requires tuning to reach its best performance and can train slower than LightGBM on very large datasets.

- **Random Forest**: A model that builds many decision trees independently(parallel), each on a random subset of data and features, then averages their predictions. Best at stable performance with minimal tuning, robust to overfitting since it averages many independent trees. It tends to be slightly less accurate than boosting on tabular benchmarks since it doesn't deliberately target leftover errors. Why use it: more forgiving without careful tuning, useful as a reliability check alongside a boosted model.

## Decisions and why
### 2026-06-28 - First Baseline Model
Considered: SVM, XGBoost, Random Forest, Neural Network 

Picked: **Logistic Regression**

Why: fast to train, simple enough to trust the result without tuning, interpretable coefficients to sanity check feature relationships, and matches binary classification structure of problem

### 2026-06-28 - Next Model
Considered: LightGBM and Random Forest

Picked: **XGBoost**

Why: Low AUC on logistic regression indicates non-linear relationships in data so moving on to boosted trees for next model. XGBoost has strong performance on tabular data, built-in regularization, and feature importance. XGBoost over random forest as sequential trees push harder on extracting whatever signal is actually in the data. XGBoost and LightBGM is similar and went with XGBoost because it's more established and wanted to learn with it more.

## Open questions / things to revisit
- What model to choose?
    - Model choice depends on what we are predicting (binary here) and how much data we have. It depends what tradeoffs we want as well like prioritizing speed or accuracy.
- When to use logistic regression or decision based trees?
    - Logistic Regression is better in fast and linear relationships to identify patterns. It uses less data and relies on fewer data points to fit reliably
    - Tree-based models work with non-linear relationships, mixed types, and has better predictive performance than interpretability.

## Quick links
- Dataset: Kaggle Vitals & Variables - https://www.kaggle.com/competitions/kaggle-community-olympiad-vitals-variables-predicting-patient-outcomes/overview
- Papers: 
- Links: 
    - ML Algo Cheat Sheet: https://learn.microsoft.com/en-us/azure/machine-learning/algorithm-cheat-sheet?view=azureml-api-1 