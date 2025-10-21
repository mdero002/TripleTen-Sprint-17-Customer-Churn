# TripleTen-Sprint-17-Final-Project-
This was the final project for the TripleTen Data Science Bootcamp. In this project, I was tasked with building a model that could accurately predict the churn rate for the company Interconnect. My goal was to create a binary classification model that could predict churn rate with an AUC-ROC score of 0.88 or higher. 

## Overview

This project focuses on developing a binary classification model to predict customer churn for Interconnect, a telecom operator. The goal is to identify customers likely to churn, enabling proactive measures to improve customer retention.

## Project Summary
This project involved comprehensive data preprocessing, exploratory data analysis, model training, and testing to predict customer churn. Multiple machine learning models were evaluated, with a final model selected based on its accuracy and efficiency.

## Table of Contents
1. [Project Task](#project-task)
2. [Pre-Processing](#pre-processing)
3. [Work Plan](#work-plan)
4. [Step 1: Data Processing, Cleaning, and Feature Engineering](#step-1-data-processing-cleaning-and-feature-engineering)
5. [Step 2: Exploratory Data Analysis (EDA)](#step-2-exploratory-data-analysis-eda)
6. [Step 3: Preparing the Data for the Models](#step-3-preparing-the-data-for-the-models)
7. [Step 4: Training the Models](#step-4-training-the-models)
8. [Step 5: Testing the Best Model](#step-5-testing-the-best-model)
9. [Step 6: Comprehensive Report](#step-6-comprehensive-report)
10. [Final Solutions Report](#final-solutions-report)

## Project Task

The primary task was to create a binary classification model to predict churn rate for Interconnect customers, achieving an AUC-ROC score of 0.88 or higher.

## Pre-Processing

Initial evaluation of four dataframes revealed:

*   Consistent `customer_id` across all dataframes.
*   No duplicate values.
*   No initial missing values, but discrepancies in row counts across dataframes necessitated handling during merging.
*   Data types were mostly appropriate, with adjustments needed later.
*   Monthly charges ranged from \$18.25 to \$118.75, with a left-skewed distribution.
*   Presence of categorical columns in all dataframes.

## Work Plan

A six-step work plan was devised:

1.  Data processing, cleaning, and feature engineering.
2.  Exploratory Data Analysis (EDA).
3.  Preparing the data for the models.
4.  Training the models.
5.  Testing the best model.
6.  Comprehensive report.

## Step 1: Data Processing, Cleaning, and Feature Engineering

*   Downloaded necessary libraries for EDA, model building, and evaluation.
*   Ensured no unmatched `customer_id` values before merging dataframes using an outer merge.
*   Addressed missing data post-merge by filling with the string "missing".
*   Standardized column names to snake\_case.
*   Converted date-based columns to datetime format and engineered `ended_service` and `contract_length` features.
*   Corrected the datatype of the `total_charges` column to float64.

## Step 2: Exploratory Data Analysis (EDA)

*   Verified categorical columns by identifying those with limited unique values (<=15).
*   Changed datatypes to category for appropriate columns.
*   Analyzed value counts for categorical columns using pie charts to check for imbalances.
*   Identified features influencing churn:
    *   Customers with 2-year contracts, automatic payments, and DSL lines were less likely to churn.
    *   Month-to-month contracts, electronic checks, and fiber optic services correlated with higher churn.
    *   Additional internet services, especially device protection, online security, and tech support, reduced churn.
    *   Churn was more likely for customers paying \$70-100 monthly and within the first 250 days of service.

## Step 3: Preparing the Data for the Models

*   Encoded categorical features using OneHotEncoder and the target variable using LabelEncoder.
*   Defined features and target variables, splitting the data into training and testing sets (80/20).
*   Opted for KFold cross-validation instead of a validation set.

## Step 4: Training the Models

*   Trained eight models: Dummy Classifier, Logistic Regression, Decision Tree Classifier, Random Forest Classifier, K-Nearest Neighbor, LGBMClassifier, XGBMClassifier, and CatBoostClassifier.
*   Implemented three training iterations: without addressing class imbalance, with downsampling, and with upsampling.
*   Upsampling was found to be the best method for handling class imbalance in most models.
*   The Random Forest model achieved the highest AUC-ROC score of 0.9704 in training, but the LGBMClassifier was chosen for testing due to its balance of speed and accuracy.

## Step 5: Testing the Best Model

*   The LGBMClassifier model was tested, yielding an AUC-ROC score of 0.9168.
*   Analysis included a ROC curve, confusion matrix, and classification report, revealing better prediction for the majority class.

## Step 6: Comprehensive Report

Concluded the project with a final overview, explaining findings and recommendations.

## Final Solutions Report

#### What steps of the plan were performed and what steps were skipped (explain why)?

All steps and action items were completed as intended, with some modifications:

*   The datatype of the `final_charges` column was corrected after initial oversight.
*   Logistical Regression was used instead of Linear Regression, which is better suited for binary classification.
*   Considered addressing skew in statistical data and potentially dropping less accurate models after initial training for efficiency.

#### What difficulties did you encounter and how did you manage to solve them?

Encountered issues with pip installing libraries on the TripleTen platform, requiring alternative methods for task completion. This involved further research to find alternative methods to complete the tasks I wanted to accomplish, which took more time. There is also an identified need to practice coding loops, defining functions, and visualizing outputs. Frustration was managed through breaks and persistence.

#### What were some of the key steps to solving the task?

*   Creating a detailed work plan.
*   Feature engineering to create the target variable.
*   Data preprocessing, including correcting data types and encoding categorical data.
*   Addressing class imbalance through upsampling.
*   Providing ROC Curve, Confusion Matrix, and Classification Report to showcase model insights.

#### What is your final model and what quality score does it have?

The final model is the LGBMClassifier, chosen for its high accuracy and speed. The test results showed an AUC-ROC score of 0.9168.
