# Smoking

## Table of Contents

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Recommendations](#recommendations)

### Project Overview
---

This project seeks to explores the health implications of smoking and various health parameters across different demographics. By analysing this data, we hope to establish trends, make key decisions based on the available data and gain in-depth understanding of the data.
![countplot](https://github.com/Farouk-Muda/Smoking/assets/166823237/ca46ef7b-bb47-49d8-81e2-502b14f30ffa)


### Data Source

The primary dataset used for this analysis is "smoking_health_data.csv" file, obtained from kaggle which gives detailed description of each column and its relevance to the study.

### Dataset Overview
Shape: The dataset contains **3900 rows** and **7 columns**.
- age: Age of participants.
- sex: Gender (male/female).
- current_smoker: Whether the participant currently smokes (yes/no).
- heart_rate: Heart rate of participants.
- blood_pressure: Blood pressure in mmHg.
- cigs_per_day: Number of cigarettes smoked per day.
- chol: Cholesterol level.

### Tool
Python - pandas, matplotlib & seaborn

### Data Cleaning/Preparation

In the initial data preparation phase, we performed the following tasks:
1. Data loading - The dataset was loaded and reviewed to understand its structure and identify potential issues.
2. Handling missing values - A check for missing values revealed null entries in the Cigs Per Day (14 missing) and Cholesterol (7 missing) columns. To address this:
All missing values were replaced with zeros using df.fillna(0).
This decision ensured a consistent dataset for analysis while avoiding errors in computations caused by missing data.
3. Data cleaning and formatting
- It was observed that values needed to be split into separate systolic and diastolic components for meaningful analysis.
- Column names were renamed to improve readability.
- Ensuring all categorical columns (Gender and Smoking Status) had consistent values.

### Exploratory Data Analysis

This focuses on drawing useful insights from the data and making the findings appealing for targeted public health interventions to reduce smoking rates and mitigate its adverse health effects
-  The dataset is grouped by the Gender column. Within each gender, the Smoking Status values are analyzed.
This creates groups for "female" and "male," where the number of occurrences of each smoking status (e.g., smoker, non-smoker) is counted.
``` df.groupby('Gender')['Smoking Status'].value_counts().reset_index(name='Total') ```

-  I split the blood pressure values (e.g., "137/88") into two parts at the "/" using  ``` str.split('/') ```.  This adds two new columns, Systolic and Diastolic, to the dataset. The categorize_BP function uses standard clinical guidelines to assign each individual to a blood pressure category based on their systolic and diastolic values.
Categories include:
1. Normal: Systolic < 120 and Diastolic < 80
2. Elevated: Systolic between 120–129 and Diastolic < 80
3. Hypertension Stage 1: Systolic 130–139 or Diastolic 80–89
4. Hypertension Stage 2: Systolic ≥ 140 or Diastolic ≥ 90
5. Hypertensive Crisis: Systolic > 180 or Diastolic > 120
Applies the function row-wise using ``` .apply``` and adds a new column, BP Category, to indicate the result.

-  Classify cholesterol values into three meaningful categories:
1. desirable: Cholesterol ≤ 200 mg/dL
2. at risk: Cholesterol between 201–240 mg/dL
3. very high: Cholesterol > 240 mg/dL
The ``` pd.cut```  function splits the numeric Cholesterol column into the specified bins and assigns the corresponding labels.
A new column, Cholesterol Level, is added to the dataset, indicating the cholesterol risk category for each individual. ``` pd.cut(df.Cholesterol, bins=[0, 200, 240, float('inf')], labels=['desirable', 'at risk', 'very high'])``` 


### Results/Findings

The analysis results are summarized as follows:
1. **More males** are smokers compared to females.
2. - Smokers are predominant in **younger age groups (31-50 years)**, whereas non-smokers are more common in older groups (51-70 years).
   - Smoking frequency (cigarettes per day) decreases with age.
3. - Smokers show a higher prevalence of **elevated blood pressure categories (Hypertension Stages 1 and 2)**.
   - Smoking significantly correlates with higher blood pressure. 
4. - Smokers are more likely to have **very high cholesterol levels** compared to non-smokers.
   - Non-smokers show higher "desirable" cholesterol levels.
5. - Male smokers are more likely to be **heavy or very heavy smokers** compared to females.
   - Light smoking is more common among females.
6.  **Middle-aged adults (41-50 years)** show the **highest cigarette consumption**, followed by younger groups.
7. **Heart rate** is mostly in the **"Normal"** category for all age groups, but a slight increase in "Low" heart rate is noted with age.
8. A **positive trend** exists between the number of cigarettes smoked and elevated systolic and diastolic blood pressures.

### Recommendations

Following the analysis of the data to establish the relationship between smoking and other health variables, we can make the these recommendations to public health officials, healthcare providers, policymakers, and community organizations.
1. - Develop gender-specific smoking cessation campaigns focusing on males to address their higher smoking rates.
   - Reinforce educational efforts among females to maintain lower smoking rates and emphasize the health benefits of non-smoking

2. - Introduce smoking prevention initiatives for individuals under 40 to curb early adoption of smoking.
   - Tailor cessation programs for the 41-50 age group to reduce smoking prevalence and mitigate long-term health impacts.
   - Highlight success stories of reduced smoking rates in older adults to encourage cessation among younger groups.

3. - Encourage regular blood pressure check-ups for smokers to identify and treat hypertension early.
   - Advocate for workplace health programs offering free screenings and cessation support.

4. - Offer dietary interventions and cholesterol education programs to smokers.
   - Promote public awareness about the compounded risks of smoking and high cholesterol leading to cardiovascular diseases.

5. - Advocate for increased taxes on tobacco products to deter high levels of smoking.
   - Focus interventions on heavy smokers, emphasizing the benefits of reducing cigarette consumption.

6. - Encourage smokers and non-smokers alike to engage in regular exercise to maintain normal heart rates.
   - Offer age-group-specific health screenings to detect early signs of abnormal heart rates.

7. - Provide clear information on how smoking directly elevates blood pressure.
   - Set measurable reduction goals for heavy smokers to improve their blood pressure levels.

8. Use multimedia campaigns to educate the public on the relationship between smoking and cholesterol.


### Limitations

I had to fill up all null values with zeros, as opposed to removing them because it would have greatly affected the precise details of my analysis


