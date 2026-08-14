# Wages-EDA
Waze Project  - Go Beyond the Numbers: Translate Data into Insights  Project: Exploratory Data Analysis  In this activity, you will examine data provided and prepare it for analysis.  The purpose of this project is to conduct exploratory data analysis (EDA) on a provided dataset.  The goal is to continue the examination of the data that you began in the previous Course, adding relevant visualizations that help communicate the story that the data tells.  This activity has 4 parts:  Part 1: Imports, links, and loading  Part 2: Data Exploration  Data cleaning  Part 3: Building visualizations  Part 4: Evaluating and sharing results  Visualize a Story in Python  PACE Stages  Throughout these project notebooks, you'll see references to the problem-solving framework PACE. The following notebook components are labeled with the respective PACE stage: Plan, Analyze, Construct, and Execute.  PACE: Plan  Consider the questions in your PACE Strategy Document to reflect on the Plan stage.  Task 1. Imports and Data Loading  For EDA of the data, import the data and packages that will be most helpful, such as pandas, numpy, and matplotlib.  Pythonimport pandas as pd
import matplotlib.pyplot as plt
import numpy as np
import seaborn as sns
```[cite: 2]

Read in the data and store it as a dataframe object called `df`[cite: 2].

```python
# Load the dataset into a dataframe
df = pd.read_csv('waze_dataset.csv')
```[cite: 2]

---

### **PACE: Analyze**[cite: 2]
Consider the questions in your PACE Strategy Document and those below where applicable to complete your code:[cite: 2]
1. Does the data need to be restructured or converted into usable formats?[cite: 2]
2. Are there any variables that have missing data?[cite: 2]

**Answers:**[cite: 2]
1. The data is already in a structured format[cite: 2]. Each row represents a user[cite: 2].
2. Yes, 700 rows have `label` missing[cite: 2]. Other variables have no missing values[cite: 2].

#### **Task 2. Data Exploration and Cleaning**[cite: 2]
Consider the following questions:[cite: 2]
1. Given the scenario, which data columns are most applicable?[cite: 2]
2. Which data columns can you eliminate, knowing they won’t solve your problem scenario?[cite: 2]
3. How would you check for missing data? And how would you handle missing data (if any)?[cite: 2]
4. How would you check for outliers? And how would handle outliers (if any)?[cite: 2]

**Answers:**[cite: 2]
1. Since we are interested in user churn, the `label` column is essential[cite: 2]. Besides `label`, variables that tie to user behaviors will be the most applicable[cite: 2]. All variables tie to user behavior except `ID`[cite: 2].
2. `ID` can be dropped from the analysis since we are not interested in identifying a particular user[cite: 2]. `ID` does not provide meaningful information about the churn (unless `ID` is assigned based on user sign-up time)[cite: 2].
3. To check for missing data, we can use `df.info()` and inspect the `Non-Null Count` column[cite: 2]. The difference between the number of non-nulls and the number of rows in the data is the number of missing values for the variable[cite: 2].
   If the missing data are missing completely at random (MCAR), meaning that the reason for missingness is independent of the data values themselves, we can proceed with a complete-case analysis by removing the rows with missing values[cite: 2]. Otherwise, we need to investigate the root cause of the missingness and make sure it won't interfere with the statistical inference and modeling[cite: 2].
4. See the previous exemplar responses for the outlier question[cite: 2].

#### **Data Overview and Summary Statistics**[cite: 2]
Use the following methods and attributes on the dataframe:[cite: 2]
* `head()`[cite: 2]
* `size`[cite: 2]
* `describe()`[cite: 2]
* `info()`[cite: 2]

It's always helpful to have this information at the beginning of a project, where you can always refer back to if needed[cite: 2].

```python
df.head(10)
```[cite: 2]

```python
df.size
```[cite: 2]

Generate summary statistics using the `describe()` method[cite: 2].

```python
df.describe()
```[cite: 2]

And summary information using the `info()` method[cite: 2].

```python
df.info()
```[cite: 2]

---

### **PACE: Construct**[cite: 2]
Consider the questions in your PACE Strategy Document to reflect on the Construct stage[cite: 2].

Consider the following questions as you prepare to deal with outliers:[cite: 2]
1. What are some ways to identify outliers?[cite: 2]
   * Use numpy functions to investigate the `mean()` and `median()` of the data and understand range of data values[cite: 2]
   * Use a boxplot to visualize the distribution of the data[cite: 2]
2. How do you make the decision to keep or exclude outliers from any future models?[cite: 2]
   * There are three main options for dealing with outliers: keeping them as they are, deleting them, or reassigning them[cite: 2]. Whether you keep outliers as they are, delete them, or reassign values is a decision that you make on a dataset-by-dataset basis, according to what your goals are for the model you are planning to construct[cite: 2]. To help you make the decision, you can start with these general guidelines:[cite: 2]
     * **Delete them:** If you are sure the outliers are mistakes, typos, or errors and the dataset will be used for modeling or machine learning, then you are more likely to decide to delete outliers[cite: 2]. Of the three choices, you’ll use this one the least[cite: 2].
     * **Reassign them:** If the dataset is small and/or the data will be used for modeling or machine learning, you are more likely to choose a path of deriving new values to replace the outlier values[cite: 2].
     * **Leave them:** For a dataset that you plan to do EDA/analysis on and nothing else, or for a dataset you are preparing for a model that is resistant to outliers, it is most likely that you are going to leave them in[cite: 2].

#### **Task 3a. Visualizations**[cite: 2]
Select data visualization types that will help you understand and explain the data[cite: 2]. Now that you know which data columns you’ll use, it is time to decide which data visualization makes the most sense for EDA of the Waze dataset[cite: 2].

**Question:** What type of data visualization(s) will be most helpful?[cite: 2]
* Line graph[cite: 2]
* Bar chart[cite: 2]
* Box plot[cite: 2]
* Histogram[cite: 2]
* Heat map[cite: 2]
* Scatter plot[cite: 2]
* A geographic map[cite: 2]

**Answer:**[cite: 2]
* Box plots will be helpful to determine outliers and where the bulk of the data points reside in terms of `drives`, `sessions` and all other continuous numeric variables[cite: 2]
* Histograms are essential to understand the distribution of variables[cite: 2]
* Scatter plots will be helpful to visualize relationships between variables[cite: 2]
* Bar charts are useful for communicating levels and quantities, especially for categorical information[cite: 2]

Begin by examining the spread and distribution of important variables using box plots and histograms[cite: 2].

#### **`sessions`**[cite: 2]
*The number of occurrences of a user opening the app during the month*[cite: 2]

```python
# Box plot
plt.figure(figsize=(5,1))
sns.boxplot(x=df['sessions'], fliersize=1)
plt.title('sessions box plot');
```[cite: 2]

```python
# Histogram
plt.figure(figsize=(5,3))
sns.histplot(x=df['sessions'])
median = df['sessions'].median()
plt.axvline(median, color='red', linestyle='--')
plt.text(75,1200, 'median=56.0', color='red')
plt.title('sessions box plot');
```[cite: 2]

The `sessions` variable is a right-skewed distribution with half of the observations having 56 or fewer sessions[cite: 2]. However, as indicated by the boxplot, some users have more than 700[cite: 2].

#### **`drives`**[cite: 2]
*An occurrence of driving at least 1 km during the month*[cite: 2]

```python
# Box plot
plt.figure(figsize=(5,1))
sns.boxplot(x=df['drives'], fliersize=1)
plt.title('drives box plot');
```[cite: 2]

As you perform EDA, you'll find that many tasks get repeated, such as plotting histograms of features[cite: 2]. Remember that whenever you find yourself copy/pasting code, it's worth considering whether a function would help make your work more efficient[cite: 2]. Sometimes it's not worth it[cite: 2]. Other times, defining a function will help a lot[cite: 2].

The following code block defines a function that helps plot histograms with a particular style/format using this particular dataset[cite: 2]. You don't have to do this, but in this case it's helpful[cite: 2].

```python
# Helper function to plot histograms based on the
# format of the `sessions` histogram
def histogrammer(column_str, median_text=True, **kwargs):    # **kwargs = any keyword arguments
                                                             # from the sns.histplot() function
    median=round(df[column_str].median(), 1)
    plt.figure(figsize=(5,3))
    ax = sns.histplot(x=df[column_str], **kwargs)            # Plot the histogram
    plt.axvline(median, color='red', linestyle='--')         # Plot the median line
    if median_text==True:                                    # Add median text unless set to False
        ax.text(0.25, 0.85, f'median={median}', color='red',
            ha='left', va='top', transform=ax.transAxes)
    else:
        print('Median:', median)
    plt.title(f'{column_str} histogram');
```[cite: 2]
