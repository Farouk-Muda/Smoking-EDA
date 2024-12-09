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
- 1. The dataset is grouped by the Gender column. Within each gender, the Smoking Status values are analyzed.
This creates groups for "female" and "male," where the number of occurrences of each smoking status (e.g., smoker, non-smoker) is counted.
``` df.groupby('Gender')['Smoking Status'].value_counts().reset_index(name='Total') ```
-2. 


### Results/Findings

The analysis results are summarized as follows:
1. Males were predominately smokers than females.
2. The aged, 50+ yrs age recorded less smoking activities comparatively to their younger counterpart.
3. It can be seen that smoking causes increased in blood pressure but there are many other contributing factors as visible in non-smokers blood pressure values. 
4. Cholesterol level of smokers are high, although non-smokers are at risk due to other factors.


### Recommendations

Following the analysis of the data to establish the relationship between smoking and other health variables, we can make the these recommendations to public health officials, healthcare providers, policymakers, and community organizations.
1. Promote smoking cessation programs that are tailored to different age groups and genders, specifically males and those aged 50+.
2. Creating awareness campaigns highlighting the health risks associated with smoking, focusing on the impact on heart rate, blood pressure, and cholesterol levels.


### Limitations

I had to fill up all null values with zeros, as opposed to removing them because it would have greatly affected the precise details of my analysis


