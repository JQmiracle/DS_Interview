# Practical Machine Learning

Course Website: https://www.coursera.org/learn/practical-machine-learning

Slides: https://github.com/bcaffo/courses/tree/master/08_PracticalMachineLearning

<img width="746" alt="Screenshot 2024-03-10 at 09 32 55" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/419e63ff-616f-46aa-942f-034fa7c917e5">

<img width="761" alt="Screenshot 2024-03-10 at 09 57 31" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/0e2e65f2-8f8d-4441-9677-8b0a93deb797">


## What is prediction?

* question -> input data -> features -> algorithm -> parameters -> evaluation

## Relative importance of steps

* question > data > features > algorithms

## In sample and out of sample error

* In sample error < out of sample error due to overfitting: **capturing both signal + noise**

## Prediction study design

* Define your error rate -> Split data into training, testing, and validation 

* A large sample size: 60% training + 20% test + 60% validation

* A medium sample size: 60% training + 40% testing

* A small sample size: cross validation

## Types of errors

* Mean squared error (MSE): $\frac{1}{n}\sum_i(Prediction_i-Truth_i)^2$

* Root mean squared error (RMSE): $\sqrt{\frac{1}{n}\sum_i(Prediction_i-Truth_i)^2}$

* True positive: correctly identified

* False positive: incorrectly identified

* Sensitivity: TP/(TP+FN)

* Specificity: TN/(TN+FP)

* **Accuracy**: (TP+TN)/(TP+FP+FN+TN)

* **Precision**: TP/(TP+FP)

* **Recall**: TP/(TP+FN)

* **F score**: $2\frac{Precision \times Recall}{Precision + Recall}$

## ROC curves

* True positive rate vs. False positive rate

* AUC: 0.5 is random guessing and 1 is perfect classifier

## Cross validation
* Used for:
  * picking variables to include in a model
  * picking the type of prediction function to use
  * picking the parameters in the prediction function
  * comparing different predictors

* Use the training set and split it into taining/test sets: Random subsampling, K-fold, and Leave one out without replacement

## Preprocessing with principal components analysis (有问题)

* Combination with the "most information" possible: reduce number of predictors and noise (due to averaging)

* SVD: $X=UDV^T$ where $X$ is a matrix with each variable in a column and each observation in a row

* PCA: the principal components are equal to the right singular values if you first scale the variables

## What is supervised learning

<img width="737" alt="Screenshot 2024-03-10 at 10 09 18" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/37262f46-d4b4-448b-b647-e67a2ef25584">



## Predicting with regression

* Easy to implement and interpret

* Often poor performance in nonlinear settings

### **1. Linear Regression Concept**
<img width="663" alt="Screenshot 2024-03-10 at 10 15 55" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/b3b85946-b13f-4cc6-96eb-fb5d1f65e832">

  * $R^2$: How much % variance could be explained by your model ($R^2$ = $1 - \frac{SSR}{SST}$ = $\frac{SSE}{SST}$)
  * Adjusted $R^2$: 更多variables --> $R^2$变大，所以用Adjusted $R^2$ --> 更好比较不同model的performance
 
<img width="596" alt="Screenshot 2024-03-10 at 10 16 42" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/3398b77c-d2df-4c04-9a14-4cf43b8d5c6c">
<img width="784" alt="Screenshot 2024-03-10 at 10 21 23" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/c61b1c20-e406-462f-b03c-e981613c6884">
<img width="780" alt="Screenshot 2024-03-10 at 10 24 20" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/ea7f205b-936f-48f3-9ac0-05b3460b7da1">

  * **Assumption in Linear Regression**:
    * **Linear relationship** between the dependent variable and the regressors
    * **Minimal Multicollinearity** between explanatory variables (Matrix X has full column rank)
      * **Correlation Matrix** --> remove high collinearity terms
    * The errors or residuals of data are normally distributed and independent from each other.
      * (**normality + iid from random sample**) **iid: "independent and identically distributed"**
      * 业界normality很难实现，确保iid就行
    * **Homosedasticity:** The variance around the regression line is the same for all values of the predictor variable

<img width="830" alt="Screenshot 2024-03-10 at 10 40 57" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/2d41407f-927a-43b1-a549-900b292bd58f">

  * **Coefficient Interpretation**:
    * Given the investments are same for all other channels, with 1 investment in the Facebook Channel(independent variable), there is 0.18 unit increase in Sales(dependent variable). 
<img width="733" alt="Screenshot 2024-03-10 at 10 54 41" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/edda7e82-a2b3-407a-be59-dae733e12fb5">
<img width="760" alt="Screenshot 2024-03-10 at 10 54 55" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/992ad198-cdec-474b-b51d-f8a49be5990c">





## Predicting with trees

* Easy to interpret and Better performance in nonlinear settings

* Without pruning/cross-validation can lead to overfitting, Harder to estimate uncertainty, and Results may be variable

* Basic algorithm: Start with all variables in one group -> Find the variables/split that best separates the outcomes -> Divide the data into two groups ("leaves") on that split ("node") -> Within each split, find the best variable/split that separates the outcomes -> Continue until the groups are too small or sufficiently "pure"

* Measures of impurity: $\hat{p_{mk}}=\frac{1}{N_m}\sum_{x_i in Leaf m} 1(y_i=k)$

* Misclassification error: $1-\hat{p_{mk}};k(m)=most;common;k$

* Gini index: $1 - \sum_k \hat{p_{mk}}^2$

* Deviance/information gain: $-\sum_k \hat{p_{mk}} log_2\hat{p_{mk}}$

## Bagging

* Resample cases, recalculate predictions and Average or majority vote

* Similar bias, Reduced variance but More useful for non-linear functions

* An extension is random forests

## Random forests

* Bootstrap samples, At each split bootstrap variables and Grow multiple trees and vote

* Pros: Accuracy

* Cons: Speed, Interpretability, and Overfitting

## Boosting

* Start with a set of classifiers $h_1, ..., h_k$ and Create a classifier that combines classification functions: $f(x)=sgn(\sum_t \alpha_t h_t(x))$

* Goal is tto minimize error (on training set): Iteratively select one $h$ at each step, Calculate weights based on errors, and Upweight missed calssfications and select next $h$

* One large subclass is gradient boosting

## Model based prediction

* Our goal is to build parametric model for conditional distribution $P(Y=k|X=x)$: Apply Bayes theorem $P(Y=k|X=x) = \frac{f_k(x)\pi_k}{\sum_l f_l(x)\pi_l}$, Estimate the paramaters from the data, and Classifiy to the class with the highest value of $P(Y=k|X=x)$

* Prior probabilities $\pi_k$: set in advance

* A common choice for $f_k(x)$: a Gaussian distribution

* Discriminant function: $\delta_k(x) = x^T \Sigma^{-1} \mu_k - \frac{1}{2}\mu_k  \Sigma^{-1} \mu_k + log(\mu_k )$ and $\hat{Y}(x) = argmax_x \delta_k(x)$

* Naive Bayes: $P(Y=k|X_1, ... X_m) \propto \pi_k P(X_1, ... X_m|Y=k)$ and $P(X_1, ... X_m, Y=k) \approx \pi_k P(X_1|Y=k)P(X_2|Y=k)...P(X_m|Y=k)$

## Regularized regression

* Pros: Can help with bias/variance tradeoff and model selection

* Cons: May be computationally demanding on large data sets and Does not perform as well as random forests and boosting

* Ridge regression: $\sum_i(y_i - \beta_0 + \sum_j x_{ij}\beta_j)^2 + \lambda \sum_j \beta_j^2$

* Lasso regression: $\sum_i(y_i - \beta_0 + \sum_j x_{ij}\beta_j)^2 + \lambda \sum_j |\beta_j|$

## Combing predictors 

* Combine similar classifiers: Bagging, Boosting, and Random forests

* Combine different classifiers: Model stacking and Model ensembling

## Unsupervised prediction

* You don't know the labels for prediction:  clusters

## Forecasting

* Trend: Consistently increasing pattern over time

* Seasonal: When there is a pattern over a fixed period of time that recurs 

* Cyclic: When data rises and falls over non fixed periods
