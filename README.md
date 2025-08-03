Name: UWINEZA Assoumpta

Student ID: 26243

on03/08/2025

Course: Introduction to Big Data


📘 Project Overview
This research investigates the relationship between income levels, health indicators, and population size across different countries. Using global datasets, we analyze how economic factors influence health outcomes and how population size moderates these relationships. The goal is to identify trends and disparities to inform policy decisions.

❓ Research Question
What is the relationship between Income, Health, and Population size across different countries?

Key Objectives:
Examine how GDP per capita (income) correlates with health metrics (e.g., life expectancy, disease prevalence).

Assess whether population size amplifies or mitigates health-income disparities.

Visualize global trends to identify regions needing targeted interventions.


📂 Dataset & Tools Used
Dataset Sources:
World Bank Open Data (GDP, Population)

WHO Global Health Observatory (Life Expectancy, Disease Rates)

Our World in Data (Supplementary Health Metrics)

Tools:
Data Cleaning & Analysis: Python (Pandas, NumPy)

Visualization: Power BI (Interactive Dashboards)

Statistical Analysis: Python (SciPy, StatsModels)

🔍 Key Findings
1. Global Distributions
Income:

Mean: $17,322 ± $19,311

Range: $599 (Central African Republic) to $132,877 (Qatar)

Health (Life Expectancy):

Mean: 71.67 ± 7.75 years

Range: 45.5 to 84.1 years

Population:

Highly skewed (mean: 39M, max: 1.38B in China)
codes 
 from google.colab import files
uploaded = files.upload()  # Upload your uncleaned CSV

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

%matplotlib inline
sns.set(style="whitegrid")

# Automatically get the uploaded file name
filename = list(uploaded.keys())[0]
print("Loaded file:", filename)

# Load dataset
df = pd.read_csv(filename)
print("✅ Dataset loaded successfully!")

OUTPUT
<img width="1475" height="631" alt="datasetlodaded" src="https://github.com/user-attachments/assets/213dd489-46ac-49e2-887f-c908bdd49054" />
 CODE 2
 print("Shape:", df.shape)
print("\nData types:\n", df.dtypes)

print("\nMissing values:\n", df.isnull().sum())

print("\nUnique values per column:\n", df.nunique())

OUTPUT
<img width="1520" height="626" alt="output" src="https://github.com/user-attachments/assets/3cffcebf-3a8e-4802-b115-00347f226509" />

CODE 3
# Remove duplicates
df = df.drop_duplicates()

# Standardize column names
df.columns = df.columns.str.strip().str.lower()

# Check for invalid or extreme values
print("\nIncome summary:\n", df['income'].describe())
print("\nHealth summary:\n", df['health'].describe())
print("\nPopulation summary:\n", df['population'].describe())

# Remove unrealistic values
df_cleaned = df[
    (df['income'] > 0) &
    (df['health'] > 0) & (df['health'] <= 100) &
    (df['population'] > 0)
]

# Reset index
df_cleaned.reset_index(drop=True, inplace=True)

print("\nCleaned dataset shape:", df_cleaned.shape)
df_cleaned.head()
 OUTPUT
 <img width="1585" height="523" alt="code_distribution" src="https://github.com/user-attachments/assets/781e6b95-6998-4432-a79a-4c107fba1132" />
 
  CODE
  
# Distribution of regions
plt.figure(figsize=(10,6))
sns.countplot(data=df_cleaned, x='region', order=df_cleaned['region'].value_counts().index)
plt.title("Number of Countries by Region")
plt.xticks(rotation=45)
plt.show()

# Income vs Health scatter plot
plt.figure(figsize=(8,6))
sns.scatterplot(data=df_cleaned, x='income', y='health', hue='region')
plt.title("Income vs Health by Region")
plt.show()

# Histogram for Income
plt.figure(figsize=(8,5))
sns.histplot(df_cleaned['income'], bins=20, kde=True)
plt.title("Income Distribution")
plt.show()

# Histogram for Health
plt.figure(figsize=(8,5))
sns.histplot(df_cleaned['health'], bins=20, kde=True)
plt.title("Health (Life Expectancy) Distribution")
plt.show()

OUTPUT
<img width="1482" height="655" alt="outputdis" src="https://github.com/user-attachments/assets/8977267b-e417-411f-b9dc-bd07f4895b00" />
<img width="1512" height="615" alt="regios" src="https://github.com/user-attachments/assets/fa55cc22-a844-4f4b-a2ee-844dcbfad1a0" />
<img width="1573" height="708" alt="Screenshot " src="https://github.com/user-attachments/assets/066fb758-d7b5-4f07-8fb6-02f8454c7fd0" />

POWERBI
<img width="957" height="606" alt="Screenshot 2025-08-03 163755" src="https://github.com/user-attachments/assets/8a76f435-5d19-40a6-8a69-a375bc865963"/>

GOOGLE COLAB LINK:https://colab.research.google.com/drive/1FFoZiqpcv_V_T4PCurmquCxaa1e2LPpD#scrollTo=szEtjW-VB6y9







2. Regional Patterns
https://regios.png

Highest Life Expectancy: Europe/Central Asia (μ=78.2)

Lowest Life Expectancy: Sub-Saharan Africa (μ=61.3)

Income-Health Correlation: Strongest in Americas (r=0.81)

3. Population Effects
https://outputt.png

Large populations show wider health disparities at similar income levels

Small, high-income nations cluster at top-right of health-income spectrum    


📊 Visual Analytics
Power BI Dashboard Highlights
https://Screenshot%25202025-08-03%2520163755.png

Key Visualizations:

Geospatial Heatmap: Health-income ratios by country

Bubble Chart: Income vs Health (size=population)

Regional Comparisons:

America leads in absolute health spending

🎯 Policy Implications
Targeted Interventions: Prioritize health infrastructure in mid-income, high-population nations

Equity Focus: Address Sub-Saharan Africa's dual burden of low income and health outcomes

Sustainable Development: Balance population growth with health investment in emerging economies

🙋 Contact
For dataset access or collaboration:
📧 Email: [assoumptauwinez@gmail.com]
🔗 LinkedIn: [assoumptauwineza]
Contact:+250785389150

Thank you for visiting my project! 😊





