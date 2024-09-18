# Strategic Marketing Using Calibrated Probabilistic Classifiers for Insurance Firms

## Project Overview

This project focuses on optimizing the marketing strategy for an insurance firm that is looking to sell vehicle insurance to its existing life insurance policyholders. The goal is to maximize return on investment (ROI) by identifying customers most likely to buy vehicle insurance. Using **calibrated probabilistic classifiers**, the project aims to strategically target customer segments with personalized marketing efforts to ensure efficient use of marketing resources.

### Key Results:

- The logistic regression model with LASSO regularization achieved an approximate **30-40% improvement** in performance over the marketing analysts, as measured by **Brier Score**.
- Even though **Random Forest** slightly outperformed logistic regression in terms of accuracy, it was found to be significantly **more uncalibrated**. Random Forest, while producing good results in classification tasks, tends to predict class probabilities based on the proportion of trees that vote for a class. This leads to poorly calibrated probability estimates, which are less reliable for making decisions in marketing resource allocation. 

## Core Concepts

### 1. **Calibration of Classifiers**

In the context of this project, the probability outputs of classifiers need to be well-calibrated, meaning that the predicted probabilities should closely match the actual likelihood of the event (i.e., purchasing vehicle insurance). Calibration ensures that the model's predictions are not only accurate in terms of classification but also reliable for decision-making based on probability estimates.

**Why Calibration Matters:**
- Probabilities from classifiers like logistic regression are directly used for budget allocation. Miscalibrated probabilities can lead to overconfident predictions, which in turn may waste resources on customers unlikely to convert.
- Calibration was assessed using **calibration curves** to visually check whether the predicted probabilities align with actual observed outcomes.

### 2. **Avoiding ROC AUC as a Metric**

While **ROC AUC** is a widely used metric in binary classification problems, it is not appropriate for this specific project due to its limitations in dealing with imbalanced data and its insensitivity to the actual predicted probability values.

### 3. **Not Using Resampling Techniques**

Resampling techniques such as **SMOTE** or **undersampling/oversampling** are often used to handle imbalanced datasets. However, these techniques can lead to **classifier miscalibration** and introduce bias into probabilistic predictions, which is why they were avoided in this project.

## Data Overview

The dataset used for this project comes from Kaggle and represents an imbalanced insurance dataset where the target variable is whether a policyholder would be interested in purchasing vehicle insurance. The dataset consists of over **380,000 observations** and contains both categorical and numerical features.

### Key Features:
- **Categorical**: Sex, Driving License, Region Code, Vehicle Age, Vehicle Damage, etc.
- **Numerical**: Age, Annual Premium, Vintage.

The response variable is highly imbalanced, with less than 20% of the customers interested in buying vehicle insurance.

## Methodology

### 1. **Logistic Regression with LASSO Regularization**

The model of choice for this project is **logistic regression**, primarily due to its ability to produce well-calibrated probability estimates. **LASSO regularization** was applied to manage redundant categories and to avoid overfitting due to the large number of categorical variables.

### 2. **Evaluation with Proper Scoring Rules**

**Brier Score** was used as the primary evaluation metric. The Brier Score measures the mean squared difference between predicted probabilities and actual outcomes, making it a proper scoring rule for evaluating probabilistic forecasts. Calibration curves were plotted to assess the quality of probability calibration.

- Logistic regression with LASSO provided a **30-40% improvement** in Brier Score compared to the baseline model.
  
### 3. **Random Forest: Feature Importance vs Calibration**

While **Random Forest** demonstrated slightly better predictive performance in terms of accuracy, it was found to be significantly less calibrated than logistic regression. Random Forest calculates probability scores based on the proportion of trees that predict a sale, which leads to **uncalibrated probability estimates**. Despite its higher accuracy in classification tasks, the poorly calibrated probabilities make Random Forest less suitable for tasks requiring reliable probability estimates, such as marketing budget allocation.

## How to Run the Project

### 1. Clone the repository:
   ```bash
   git clone https://github.com/daniyalshahzad/insurance-marketing.git
   cd insurance-marketing

## How to Run the Project

### 1. Clone the repository:
   ```bash
   git clone https://github.com/daniyalshahzad/insurance-marketing.git
   cd insurance-marketing
   ```

### 2. Install the necessary R libraries"
Before running the code, ensure that you have the following R packages installed. You can install them by running the following commands in R:
```
install.packages("caret")
install.packages("glmnet")
install.packages("randomForest")
install.packages("verification")
install.packages("rms")
install.packages("zoo")
install.packages("gbm")
install.packages("pROC")
install.packages("dplyr")
install.packages("DescTools")
```

### 3. Navigate to the Rcode folder and run the scripts:
Project.rmd: Contains the main analysis for the project.
Project - Random Forests.rmd: Focuses on Random Forests especially its calibration
You can open these .rmd files in RStudio and run them interactively, or render them as HTML or PDF by using the following commands:

```
rmarkdown::render("Project.rmd")
rmarkdown::render("Project - Random Forests.rmd")
```

#### 4. View the PDF and PowerPoint files in the docs/ folder for a full detailed report and presentation.

