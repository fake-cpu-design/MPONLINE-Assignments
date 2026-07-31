# Adult Census Income Classification

## Project Overview
This project predicts whether an individual makes over $50K a year based on demographic and employment data from the 1994 US Census. It uses the Adult Census Income dataset from the UCI Machine Learning Repository, hosted on Kaggle.

## Dataset
* **Source:** [Kaggle - Adult Census Income](https://www.kaggle.com/datasets/uciml/adult-census-income)
* **Target Variable:** `income` (<=50K or >50K)
* **Features:** Age, Workclass, Fnlwgt, Education, Education-num, Marital-status, Occupation, Relationship, Race, Sex, Capital-gain, Capital-loss, Hours-per-week, Native-country.

## Environment
This project is designed to be executed in **Google Colab**. 

## Prerequisites
You must have a Kaggle account and an API token (`kaggle.json`) to download the dataset directly into the notebook.

## Workflow
1. **Data Acquisition:** Configures the Kaggle API and downloads the dataset directly to the Colab environment.
2. **Data Loading:** Imports necessary Python libraries (Pandas, Scikit-learn) and loads the CSV data.
3. **Preprocessing:** 
   * Handles missing values represented by `?`.
   * Removes duplicate rows and missing data.
   * Encodes categorical string variables into numerical formats using `LabelEncoder`.
   * Splits data into training and testing sets (80/20 split).
   * Scales feature values using `StandardScaler` for uniformity.
4. **Modeling:** Trains a `RandomForestClassifier` on the processed training data.
5. **Evaluation:** Outputs the overall accuracy score and a detailed classification report (Precision, Recall, F1-Score).