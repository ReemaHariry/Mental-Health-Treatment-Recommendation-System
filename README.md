# 🧠 Mental Health Treatment Recommendation System

This project is a data-driven recommendation system that analyzes mental health diagnosis and treatment data to suggest appropriate medications and therapy types based on patients' symptoms. It uses **association rule mining (Apriori algorithm)** to uncover meaningful patterns between symptoms and treatments.

## 📁 Dataset

The dataset contains patient-level data, including:
- Symptom severity scores (e.g., mood, stress, sleep quality)
- Treatment progress and adherence
- Medication and therapy types
- Treatment duration and demographic information

> 📌 File used: `mental_health_diagnosis_treatment_.csv`

---

## 🔍 Exploratory Data Analysis (EDA)

Performed comprehensive EDA to understand the structure and behavior of the dataset:

- **Data cleaning**: Checked for null values, duplicates, and data types.
- **Descriptive statistics**: Summary statistics for all numerical variables.
- **Visualizations**:
  - Bar plots and pie charts for categorical features (e.g., gender, therapy type)
  - Histograms and box plots for numerical features (e.g., mood score, symptom severity)

**Insights Discovered**:
- Average treatment duration: **12 weeks**
- High treatment progress even with symptom severity >7
- Average treatment adherence around **75%**, suggesting challenges in following plans

---

## 🛠 Feature Engineering

Created a new `Symptoms` column combining several key features:
- **Symptom Severity (1–10)**
- **Mood Score (1–10)**
- **Sleep Quality (1–10)**
- **Stress Level (1–10)**

This feature groups patients into meaningful symptom categories like:
- `Severe Symptoms`
- `Depressed`
- `Poor Sleep`
- `High Stress`

These were later used in association rule mining.

---

## 📊 Association Rule Mining (Apriori Algorithm)

Applied **Market Basket Analysis** to find frequent combinations of:
- Symptoms (antecedents)
- Medications and therapy types (consequents)

### Tools Used:
- `mlxtend.frequent_patterns.apriori`
- `TransactionEncoder`
- `association_rules`

### Process:
1. Transformed symptom and medication data into transactional format.
2. Extracted frequent itemsets with a minimum support threshold.
3. Generated strong association rules with:
   - **Confidence ≥ 0.65**
   - **Lift values between 0.97 and 1.11**

---

## 💡 Recommendation System

A custom function was built to **recommend treatments** based on user input:

### 🔄 How it works:
- Takes a list of symptoms from the user
- Matches them with high-confidence rules in the association results
- Returns a list of recommended medications or therapy types

### 🧪 Sample Input:
```python
Enter your symptoms (comma-separated): High Stress, Depressed
