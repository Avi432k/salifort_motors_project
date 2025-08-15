# Google Advanced Data Analytics Capstone – Salifort Motors

## Overview  
The goal of this project is to **analyze HR data for Salifort Motors** in order to **predict employee turnover** and provide **data-driven recommendations** to improve retention.

---

## Business Scenario
Salifort Motors is a fictional automobile manufacturer based in France.  
The HR department is concerned about increasing employee turnover, which can lead to:
- Higher recruitment and training costs
- Loss of experienced talent
- Decreased overall productivity

They have collected employee performance, satisfaction, and HR history data. My task was to analyze the dataset and create predictive models to:
1. Identify which employees are at risk of leaving.
2. Understand which factors most strongly influence turnover.
3. Recommend actionable strategies to improve retention.

---

## Objectives
**Main objectives:**
- Build predictive models to determine whether an employee will leave.
- Identify key factors that influence turnover.
- Provide actionable HR recommendations.

**Business value:**
- Reduce recruitment costs.
- Increase employee satisfaction.
- Maintain higher productivity through retention.

---

## Dataset Description
**Source:** The data was sourced from Kaggle, which can be accessed [here](https://www.kaggle.com/datasets/mfaisalqureshi/hr-analytics-and-job-prediction?select=HR_comma_sep.csv).  
**Target variable:** `left` – whether the employee left the company (1) or stayed (0).

| Column Name            | Description |
|------------------------|-------------|
| satisfaction_level     | Employee's job satisfaction (0–1 scale) |
| last_evaluation        | Employee's last performance evaluation score (0–1) |
| number_project         | Number of projects employee is involved in |
| average_monthly_hours  | Average hours worked per month |
| time_spend_company     | Years spent at the company |
| Work_accident          | Whether the employee had a work accident (1 = Yes, 0 = No) |
| promotion_last_5years  | Whether the employee was promoted in the last 5 years |
| Department             | Department the employee works in |
| salary                 | Salary category (low, medium, high) |
| left                   | Target variable (1 = Left, 0 = Stayed) |

---

## Methodology – PACE Framework
The project followed the **PACE (Plan, Analyze, Construct, Execute)** framework:

1. **Plan**  
   - Define the problem: Predict employee turnover and identify drivers.
   - Decide on approach: Exploratory data analysis (EDA) + Machine Learning models.

2. **Analyze**  
   - Data cleaning and preparation.
   - Visualizing relationships between variables and turnover.
   - Encoding categorical variables.

3. **Construct**  
   - Built two models: Random Forest and XGBoost.
   - Tuned hyperparameters for better accuracy and recall.

4. **Execute**  
   - Evaluated models using Accuracy, Precision, Recall, and F1-score.
   - Generated feature importance plots.
   - Presented findings and recommendations.

---

## 🔍 Exploratory Data Analysis (EDA)

Key findings from the EDA:

- **Average Monthly Hours & Turnover Patterns**  
  - Turnover rates were higher among employees working **125–160 hours/month** and **250+ hours/month**.  
  - Employees averaging **>170 hours/month** were more likely to leave voluntarily compared to those working less.  
  - This group (>170 hours) generally had **high final performance evaluations**, whereas those working less than 170 hours tended to have **lower evaluations**.  
  - Subsequent analyses focused on this high-hour, high-performance group.

- **Tenure**  
  - Most employees who likely left voluntarily had spent **4, 5, or 6 years** at the company.

- **Number of Projects**  
  - **2–3 projects** appeared to be the optimal range for employee contribution.  
  - After 3 projects, turnover increased sharply — with most who left having 6 projects, and **100% turnover** among employees with 7 projects.

- **Hours vs. Projects**  
  - For employees who stayed, **average monthly hours remained constant** regardless of project count — contrary to expectations.  
  - Among those who left, average monthly hours **increased with project count**, suggesting that departing employees may have been compensating for underperformance among colleagues who stayed.

- **Promotions in the Last 5 Years**  
  - **98.3%** of employees had not been promoted in the last 5 years.  
  - For employees averaging **170 hours/month**, turnover was much lower for those promoted (**1.5%**) than those not promoted (**13.9%**).  
  - Among non-promoted employees, those who left averaged **more hours/month** than those who stayed — indicating possible dissatisfaction due to lack of reward for extra effort.

- **Salary Levels**  
  - Among employees averaging **>170 hours/month**, salaries were distributed as: **47.5% low**, **44.0% medium**, **8.5% high**.  
  - Turnover rates were lowest among high-salary employees (**3.4%**) compared to low (**16.7%**) and medium (**12.5%**) salaries.  
  - Similar to promotion trends, those who left generally worked **more hours/month** than those who stayed, suggesting they may have felt **undercompensated for their workload**.


---

## Modeling & Results

### Random Forest
- Precision: **98%**
- Recall: **89%**
- Accuracy: **98%**
- F1: **0.93**

### XGBoost
- Precision: **98%**
- Recall: **86%**
- Accuracy: **98%**
- F1: **0.92**

**Best Model:** Random Forest (best recall score).

---

## Feature Importance
Top predictors of turnover:
1. **Satisfaction level** – lower satisfaction increases risk.
2. **Time spent at company** – higher years correlate with higher turnover after certain point.
3. **Number of projects** – overload can lead to burnout.
4. **Last evaluation** – very high or very low scores link to turnover.
5. **Average monthly hours** – overworking drives dissatisfaction.


---

## Recommendations
Based on the findings:
- **Limit excessive workload**: Keep project count per employee under 5 when possible.
- **Promote work-life balance**: Avoid consistent overwork (> 250 hours/month).
- **Improve recognition**: Ensure fair promotion and recognition policies.
- **Conduct regular satisfaction surveys**: Identify dissatisfaction early.
- **Provide targeted retention programs** for high-risk employees.

---

## Project Structure
salifort_motors_project/
├── data/
│   ├── anaconda_projects/db/project_filebrowser.db
│   ├── cleaned_sm_data.csv
│   ├── HR_comma_sep.csv
│   └── sm_data_170plus.csv
├── images/
│   └── sm_variables.png
├── notebooks/
│   ├── anaconda_projects/db/project_filebrowser.db
│   ├── smp_data_cleaning.ipynb
│   ├── smp_eda.ipynb
│   └── smp_model.ipynb
└── smp_data_cleaning.ipynb

