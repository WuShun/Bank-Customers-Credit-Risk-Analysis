# Bank-Customers-Credit-Risk-Analysis

## Project Description:
* Programming for Analytics courses project(DNSC 6211), GWU
* Time: Oct. 2017
* Instructor: Prof. Shivraj Kanungo
* Dataset: [creditdata.csv](Bank-Customers-Credit-Risk-Analysis/creditdata.csv)
* Object: Predict the credit rating for potential borrowers
* Scripts: [Bank Customers Credit Risk Analysis.Rmd](
      
        Bank-Customers-Credit-Risk-Analysis/Bank Customers Credit Risk Analysis.Rmd
      )
      
* Output: [Bank Customers Credit Risk Analysis.html](Bank-Customers-Credit-Risk-Analysis/Bank_Customers_Credit_Risk_Analysis.html)

## Instructions
Assume I have been hired as a consultant to a bank to help them predict the credit rating for potential borrowers. Here is the description of the dataset

* Varaible Description:

| **Variable** | **Description** | **Type** |
| --- | --- | --- |
| rating | credit rating | Factor |
| experience | Job experience (in years) | integer |
| homeown | home ownership | Factor |
| loandurn | Loan duration | integer |
| age | Age of borrower | integer |
| mstat | Marital status | Factor |
| rcds | Existence of records | Factor |
| jtype | Job type | Factor |
| explvl | Quantum of expenses | integer |
| inc | Level of income | integer |
| assts | Quantum of assets | integer |
| debt | Quantum of debt | integer |
| loanamount | Loan amount requested | integer |
| purchprice | Purchase price of item | integer |

* Size: 289KB
* Observations: 4446

## Data Preprocess 
(i) Imported the data file

(ii) Viewed variables and type

(iii) Transfered factor type varaible to numeric type

(iv) Converted original values 2 and 1 for rating to 1 and 0

(v) Make ensure that the data are clean:
* Checked if there are null
* Checked if there are blank space

(vi) Use the first half of this dataset to be the training set and the second half of this dataset
to be the test set. 

## Data Exploration
(i) Made descriptive statistical exploration for each variable using TABLE and SUMMARY function

(ii) Used ggplot2 package to plot discrete ~ discrete variables by bar and plot continuous ~ discrete variables by geom_point

(iii) There is nothing to inform me about a good predictor from these descriptives

## Data Analysis
(i) Logistic Regression

* Made a predictive model using logistic regression.
* According to summary of the model, all variables, except loandurn (loan duration) and age are significant
* Applied the function PREDICT to the model along with test dataset.
* How good our model is? Used IFELSE function so that if the predicted probability bigger than 0.5, the value will be replaced with 1, or else be replaced with 0.
* Calculated misclassificationerror which means the probability of wrong prediction
* Accuracy equals to 1 minus misclassificationerror, which is 0.792622582096266

(ii) Decision Tree
* Made a predictive model using a decision tree
* This tree has splited 8 times. Each split is on one certain variable which has the biggest influcence on classification. For each branch, the "good" or "bad" is decided by the majority of this node; the fraction stands for the number of this kind majority; the percentage stands for the ratio of the number of this node to the overall number of this dataset.
* The probability of all good rating customer is 1595/2223 = 71.75%. The biggest probability of good credit rating customers among all nodes is 911/1021 = 89.23% for those who don't have existed records and job experience more than 1.5 years and level of income higher than 102.

## Model Comparison
(i) Used ROC curve and AUC method to compare two model

(ii)
* Y-axis = Sensitivity
* Sensitivity = the proportion of true positives; The concept of true positive means the model we use predicts correctly customer "good" given that the customer is actually "good"
* X-axis = 1 - Specificity
* 1 - Specificity = the proportion of false positive
* The specificity is the probability of true negative. The concept of true negative means the model we use predicts correctly customer "bad" given that the customer is actually "bad".
* The concept auc in the ROC means the "area under curve", indicating whether the model is better than random 50/50 model. Because the random 50/50 model has a auc 0.5. The greater auc is, the better model fits. So as long as auc > 0.5, the model is better than random 50/50 model.

(iii) The AUC of logistic regression model is 0.8309551, and AUC of decision tree is 0.7518058

(iv) Compared with the decision tree model, the logistics regression model for this dataset is more credible by ROC curve(AUC).
