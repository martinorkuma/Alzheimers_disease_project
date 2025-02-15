## Introduction

Alzheimer’s disease (AD) is a progressive neurodegenerative disorder that primarily affects memory and cognitive function. This analysis explores potential risk factors and patterns associated with Alzheimer's disease diagnosis using a dataset of 2,149 patients. The dataset includes demographic information, lifestyle habits, medical history, cognitive assessments, and behavioral symptoms.

**Objectives of the Analysis**
1. Data Preprocessing
- Convert numerical categorical variables (e.g., Gender, Ethnicity, Smoking) into readable labels.
- Identify missing values and handle inconsistencies.

2. Exploratory Data Analysis (EDA)
- Examine the distribution of key features such as age, MMSE scores, and diagnosis rates.
- Visualize correlations between cognitive function, lifestyle, and chronic diseases.

3. Risk Factor Assessment
- Compare groups based on AD diagnosis to identify statistically significant differences in risk factors.
- Analyze the impact of hypertension, diabetes, smoking, and lifestyle habits on cognitive decline.

4. Hypothesis Testing
- Perform t-tests and chi-square tests to determine which factors are significantly associated with AD.
- Perform ANOVA tests on key variables to examine differences across AD diagnosis groups. 

This analysis uncovers patterns and relationships in the dataset, providing insights into the potential predictors of Alzheimer’s disease and helping guide further research and intervention strategies. 


### Data Source
The data used in this project was collected and developed by [Rabie El Kharoua](https://www.kaggle.com/rabieelkharoua) as part of the [Alzheimer's Disease Dataset](https://www.kaggle.com/datasets/rabieelkharoua/alzheimers-disease-dataset/data) on Kaggle. It is synthetic and **for educational purposes only.** All data analyses and visualizations were performed using Python in JupyterLab Desktop. 

## Exploratory Data Analysis

See file: alzheimers_disease_project.ipynb for full exploratory data analysis. 

```Python
# I combined boxplots for Physical Activity and Diet Quality into one cell:

fig, axes = plt.subplots(1, 2, figsize=(14, 7))

# Physical Activity
sns.boxplot(data=df, x=df["Diagnosis"], y=df["PhysicalActivity"], 
            hue="Diagnosis", palette=["lightblue", "gold"], ax=axes[0])
axes[0].set_xlabel("Diagnosis (No Alzheimer’s Dx | Alzheimer’s Dx)")
axes[0].set_ylabel("Physical Activity Score")
axes[0].set_title("Physical Activity by Diagnosis")

# Diet Quality
sns.boxplot(data=df, x=df["Diagnosis"], y=df["DietQuality"], 
            hue="Diagnosis", palette=["lightblue", "gold"], ax=axes[1])
axes[1].set_xlabel("Diagnosis (No Alzheimer’s Dx | Alzheimer’s Dx)")
axes[1].set_ylabel("Diet Quality Score")
axes[1].set_title("Diet Quality by Diagnosis")

plt.tight_layout()
plt.show()
```

![Output1](https://github.com/user-attachments/assets/5d425cb7-787e-47e2-b7bc-c1234e748fd2)



## Key Insights
- MMSE scores are the strongest differentiator between individuals diagnosed with AD and those without AD diagnosis.
- Although several studies, Edwards III et al. (2019), have shown the association between lifestyle factors (BMI, diet, physical activity) and chronic diseases, this dataset does not show strong statistical associations.
- HDL cholesterol levels are significantly different across groups. Further investigation (e.g., Tukey's post-hoc test) can determine which groups differ.
- Age, BMI, and LDL cholesterol are not significantly associated with Alzheimer's diagnosis in this dataset.
- Further analysis (e.g., logistic regression) is needed to determine potential risk factors and predictors of AD.


## References

- Arevalo‐Rodriguez, I., Smailagic, N., i Figuls, M. R., Ciapponi, A., Sanchez‐Perez, E., Giannakou, A., ... & Cullum, S. (2015). [Mini‐Mental State Examination (MMSE) for the detection of Alzheimer's disease and other dementias in people with mild cognitive impairment (MCI).](https://www.cochranelibrary.com/cdsr/doi/10.1002/14651858.CD010783.pub2/full) Cochrane database of systematic reviews, (3).
- Edwards III, G. A., Gamez, N., Escobedo Jr, G., Calderon, O., & Moreno-Gonzalez, I. (2019). [Modifiable risk factors for Alzheimer’s disease.](https://www.frontiersin.org/journals/aging-neuroscience/articles/10.3389/fnagi.2019.00146/full) Frontiers in aging neuroscience, 11, 146. 
- [Rabie El Kharoua](https://www.kaggle.com/rabieelkharoua) (2024). [Alzheimer's Disease Dataset](https://www.kaggle.com/datasets/rabieelkharoua/alzheimers-disease-dataset/data). DOI: [10.34740/KAGGLE/DSV/8668279]. Kaggle.
- Yoelin, A. B., & Saunders, N. W. (2017). [Score Disparity Between the MMSE and the SLUMS.](https://journals.sagepub.com/doi/full/10.1177/1533317517705222) American Journal of Alzheimer's Disease & Other Dementias®, 32(5), 282-288.
