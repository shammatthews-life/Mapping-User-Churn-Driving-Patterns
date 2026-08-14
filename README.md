# 🚗 Waze Project: Go Beyond the Numbers

> **Translate Data into Insights** — An Exploratory Data Analysis (EDA) and data visualization project for the Waze data science team.
> 
> 

---

## 📌 Project Overview

As part of the Waze data science team, this project focuses on conducting exploratory data analysis (EDA) on a provided dataset.

The goal is to continue the examination of the data that you began in the previous course, adding relevant visualizations that help communicate the story that the data tells.

---

## 🚀 The PACE Framework

Following Waze's structured problem-solving framework, this project is divided into four core stages:

1. **Plan:** Import necessary packages and load the dataset into a dataframe object called `df`.


2. **Analyze:** Inspect data structures, check for missing values (such as 700 missing rows in the `label` column), evaluate column relevance (like dropping `ID`), and handle outliers.


3. **Construct:** Build visualizations (including box plots and histograms) to evaluate the spread and distribution of key variables like `sessions` and `drives`.


4. **Execute:** Evaluate findings, determine outlier treatment strategies, and share results.



---

## 📊 Dataset Structure

The analysis is performed on `waze_dataset.csv`, where each row represents a user. Key aspects of the dataset include:

* **Data Loading:** Loaded into a dataframe called `df` using `pd.read_csv('waze_dataset.csv')`.


* **Missing Data:** 700 rows have the `label` missing, while other variables have no missing values.


* **Feature Selection:** `ID` can be dropped from the analysis since identifying a particular user is unnecessary. Essential columns include `label` (for tracking user churn) and other behavior-related variables.



---

## 🛠️ Tech Stack & Libraries

* **Programming Language:** Python 3.x


* **Data Manipulation & Calculation:** `pandas`, `numpy`

* **Data Visualization:** `matplotlib`, `seaborn`


---

## 📈 Key Analysis & Visualizations

### 1. Python EDA & Matplotlib/Seaborn Plots

* **Distribution Checks:** Utilized box plots and histograms to inspect the spread and distribution of continuous numeric variables like `sessions` (which is right-skewed with a median of 56.0) and `drives`.


* **Outlier Investigation:** Evaluated data range and outliers using `mean()`, `median()`, and box plots, applying guidelines to delete, reassign, or leave outliers based on modeling objectives.


* **Automation & Functions:** Developed custom helper functions (such as `histogrammer()`) to streamline repetitive plotting workflows for dataset features.



---

## ⚙️ Getting Started & Running the Code

1. **Load packages and read in the dataset:**
```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
import seaborn as sns

# Load the dataset into a dataframe
df = pd.read_csv('waze_dataset.csv')
```[cite: 2]

```
