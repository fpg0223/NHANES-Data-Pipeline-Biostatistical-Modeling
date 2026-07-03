# NHANES Clinical Data Pipeline & Predictive Modeling

**Project Overview**  
This project evaluates the clinical, demographic, and lifestyle drivers of Metabolic Syndrome (MetS) using a nationally representative sample of U.S. adults from the 2017–2018 NHANES cycle. By engineering a unified relational dataset from raw National Health and Nutrition Examination Survey (NHANES) files, this analysis utilizes logistic regression frameworks to determine whether domain-specific physical activity (leisure vs. occupational) and age are statistically significant predictors of cardiometabolic risk.

**Core Technologies:** R, `tidyverse`, `haven`, `ggplot2`, `broom`, `car`  
**Statistical Techniques:** Relational Data Merging (ETL), Logistic Regression, Interaction Terms (Effect Modification), Multicollinearity Diagnostics (VIF), Odds Ratio Analysis

---

## 🏗️ Data Engineering & ETL Pipeline
The analytic dataset was constructed by extracting and joining 7 distinct raw NHANES `.xpt` files via unique respondent identifiers (`SEQN`). 

*   **Demographics:** `DEMO_J` (Age, Gender)
*   **Physical Activity:** `PAQ_J` (Leisure vs. Occupational Domains)
*   **Clinical Biomarkers:** `BPX_J` (Blood Pressure), `BMX_J` (Waist Circumference), `HDL_J` (Cholesterol), `GLU_J` (Fasting Glucose), `TRIGLY_J` (Triglycerides)

**Feature Engineering:** A binary Metabolic Syndrome target variable was engineered using strict clinical cutoffs. Patients were classified as having MetS if they met 3 or more of the following criteria: elevated waist circumference, elevated triglycerides, low HDL cholesterol, high blood pressure, or elevated fasting glucose.

---

## 🛠️ Statistical Methodology
A multivariable logistic regression model was built to evaluate the relationship between physical activity domains and MetS, controlling for age and gender. 

*   **Assumption Diagnostics:** Evaluated multicollinearity using Variance Inflation Factors (all VIFs < 2) and confirmed the linearity of the logit for continuous predictors.
*   **Effect Modification:** Introduced an interaction term (Physical Activity × Gender) to test for divergent group effects, ensuring robust main-effect interpretations.
*   **Confidence Intervals:** Calculated 95% CIs and Odds Ratios (OR) to quantify the magnitude of risk.

---

## 📈 Key Business & Clinical Insights
*   **Age is the Dominant Predictor:** Age demonstrated a massive, statistically significant impact on cardiometabolic health. For each additional year of age, the odds of developing Metabolic Syndrome increased by 3% (OR = 1.03, p < 0.001). 
*   **Activity Domain Does Not Drive Risk:** The analysis yielded a statistically negligible difference (OR = 0.88, p = 0.36) between leisure-time and occupational physical activity, proving that the domain of activity alone is not a sufficient predictor of MetS.
*   **Targeted Interventions:** Findings indicate that preventative healthcare strategies and clinical interventions should prioritize age-based screening over broad physical activity categorizations.

---

## 📂 Repository Contents
*   `NHANES_Data_Pipeline.Rmd`: The master R Markdown script containing the data merging, cleaning, visualization, and modeling pipelines.
*   `NHANES Data Pipeline & Biostatistical Modeling.pdf`: The fully compiled analytical report featuring data visualizations, assumption checks, and formatted regression tables.
*   *Note: Raw NHANES `.xpt` datasets are publicly accessible via the CDC website and are not hosted in this repository due to size constraints.*
