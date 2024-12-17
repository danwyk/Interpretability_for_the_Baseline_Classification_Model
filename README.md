# Data Interpretability for the Baseline Classification Model

> Credit to   
> Daniel Wang(danwyk@umich.edu)  
> Maria Han Veiga(mhanveig@umich.edu)

<br>
 
*The dataset used for this project comes from [PubMed](https://pubmed.ncbi.nlm.nih.gov/18379538/)*   

---

## Goal   
The main goal of this project is to explore the interpretability of the Brazilian Peritoneal Dialysis Multicenter Study (BRAZPD) dataset with a trained baseline classification model.   
This project aims to:   

- Predict patient mortality outcomes
- Understand and interpret the model's predictions using SHAP values
- Identify key features contributing to patient mortality and cause of death
- Evaluate the performance of the classification model using various metrics

---

## Methods

### Data Processing

1. **Data Cleaning**: 
    - Removed artifacts, outliers, and incorrect handling of records.
    - Set data contradicting the follow-up endpoints to NaN.

2. **Feature Engineering**: 
    - Relabeled features and handled time-dependent features.
    - Visualized data distributions to understand feature behavior over time.

### Predictive Models

1. **Baseline Classification Models**:
    - Developed binary classification models to predict patient mortality and cause of death.
    - Used XGBoost, a supervised learning algorithm.
    - Applied cross-validation with a stratified k-fold procedure (k=10).

2. **Performance Metrics**:
    - Evaluated models using accuracy, F1 score, recall, and precision.
    - Implemented SMOTE to address class imbalance.

### Interpretability

1. **SHAP Values**:
    - Used SHAP (Shapley Additive exPlanations) values to measure feature contributions.
    - Analyzed the importance of features in model predictions.
    - Identified potential biases and performed feature selection for improvement.

---

## Findings

1. **Key Features**:
    - "Age" and "Davies Score" were the most significant features contributing to patient mortality.   
    <img src="https://github.com/danwyk/Interpretability_for_the_Baseline_Classification_Model/blob/main/demo/death_event_3y.png" width="500">   
    
    - Experience and size of medical centers also impacted patient mortality rates.

2. **Model Performance**:
    - The baseline classification model achieved a mean accuracy of around 0.827 but had a mean F1 score of around 0.2.
    - Models for specific causes of death (CVD and non-treatment-related sepsis) showed mean accuracies of 0.6 and 0.62, and mean F1 scores of 0.34 and 0.33, respectively.

3. **Validation with Iris Dataset**:
    - The model demonstrated better performance with clean data, achieving over 90% accuracy and F1 scores with the Iris dataset.

4. **Insights from SHAP Values**:   
    - Identified that higher "Age" and "BMI" significantly influenced mortality caused by CVD.   
    <img src="https://github.com/danwyk/Interpretability_for_the_Baseline_Classification_Model/blob/main/demo/CVD.png" width="500">   
    
    
    - Found that lower "BMI" contributed more to mortality caused by non-treatment-related sepsis.   
    <img src="https://github.com/danwyk/Interpretability_for_the_Baseline_Classification_Model/blob/main/demo/Sepsis-non-related.png" width="500">   
    
    - "Gender" was a major factor for CVD-related mortality, with females being more prone to CVD issues.
