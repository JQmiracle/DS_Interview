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



### **2. Logistic Regression Concept**

- Logit Function: $\ln(\frac{p(x)}{1-p(x)}) = \beta_{0} + \beta_{1}X_{1} + ... + \beta_{N}X_{N}$
- Odds Ratio = $\frac{p}{1-p}$ = $\frac{p}{q}$
- Log Odds Ratio : $X_{1}$ increases by 1 unit, $\ln(\frac{p}{1-p})$ increases by $\beta_{1}$
- Compare two variables: $\frac{e^{\beta_{1}}}{e^{\beta_{2}}} = \{e^{\beta_{1} - \beta_{2}}}$
- 人为设置threshold, 因为output是probability。

<img width="1050" alt="Screenshot 2024-03-13 at 16 34 32" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/6ad2b645-7f88-448e-a176-a63857768245">

<img width="1228" alt="Screenshot 2024-03-13 at 16 35 08" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/a810d721-7790-4f32-841c-94987b6ce74f">


<img width="1001" alt="Screenshot 2024-03-13 at 16 46 19" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/b6cc5958-ad5a-438b-aa2e-a1604d7ace4a">


<img width="999" alt="Screenshot 2024-03-13 at 16 50 02" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/1d3b8faf-b19b-4b50-a5fb-d27652ddf08f">






## Predicting with trees

* Easy to interpret and Better performance in nonlinear settings

* Without pruning/cross-validation can lead to overfitting, Harder to estimate uncertainty, and Results may be variable

* **Basic algorithm**:
  * Start with all variables in one group
  * Find the variables/split that best separates the outcomes
  * Divide the data into two groups ("leaves") on that split ("node")
  * Within each split, find the best variable/split that separates the outcomes
  * Continue until the groups are too small or sufficiently "pure"

* **Minimize Entropy == Increase Information Gain**

* Measures of impurity: $\hat{p_{mk}}=\frac{1}{N_m}\sum_{x_i in Leaf m} 1(y_i=k)$

* Misclassification error: $1-\hat{p_{mk}};k(m)=most;common;k$

* **Gini index**: $1 - \sum_k \hat{p_{mk}}^2$ ( **The lower the Gini Index, the better the lower the likelihood of misclassification**.)

* Entropy =  $-\sum_k \hat{p_{mk}} log_2\hat{p_{mk}}$

* Information gain = Entropy(Parent) - Entropy(Children)


<img width="1307" alt="Screenshot 2024-03-13 at 17 08 52" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/96ab51b1-1b69-4da5-85f9-67ce49a1c62c">




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

* Goal is to minimize error (on training set): Iteratively select one $h$ at each step, Calculate weights based on errors, and Upweight missed classifications and select next $h$

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


### Interview Questions:
<img width="1190" alt="Screenshot 2024-03-13 at 17 24 36" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/f3ceae19-681d-48d8-bb34-653d18d36e0e">

- **Cost of False Positive is Higher**: 公司招聘一个不合格的人，最后公司需要大量人力物力去解雇

- **Cost of False Negative is Higher**: 预测一个人得了癌症，但是没被检测出来，最后没得到治疗，对病人生命危害很大

<img width="1048" alt="Screenshot 2024-03-13 at 17 48 42" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/9d8f4bb5-91e1-472b-ba09-a0814a465db9">

- **Metric 选择： False Positive vs. False Negative**
  - False Positive rate (Type 1 Error = Alpha): Not Fraud 预测成 Fraud --> 用户可能麻烦一些登陆 --> 影响一部分用户的用户体验
  - **False Negative rate (Type 2 Error = Beta)**: Fraud 预测成 Not Fraud --> 继续产生 new Fraud --> 更大损失
- **Drawbacks of using supervised machine learning model:**
  - **Imbalanced dataset** --> the classifier always predicts the one label (把Not Fraud 预测成 Fraud) --> need to upsampling or downsampling
  - **Training on the history dataset** --> One step behind the new data --> 很难通过historical data去detect new fraud
  - **Current Industry Method:** **Anomaly Detection** (和 ML 不同) --> 罗列feature --> 看看那些用户feature处于outlier之上
  - **New Idea:**
    - Step 1: Supervised ML --> First Fraud Detection
    - Step 2: Anomaly (Not Fraud from Supervised ML) --> Second Fraud Detection


<img width="1166" alt="Screenshot 2024-03-13 at 18 12 53" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/d3da740d-89f4-4d0c-bcab-79d23429ad9b">

 
- **Customer Satisfaction** is too general and hard to quantify. Assumption: Increase the customer safisfication rate --> increase retention rate --> decrease churned rate --> increase the lifetime value + potential revenue
- **Main Goal**: Customer 那些**Feature**是一个很强的signal代表他们满意或者不满意，改善Feature基于Feature Importance，改善客户体验，更少的Say No
- **Regression vs. Classification:**
  - Logit Regression:
    - Benefits: 不占公司算力 --> 很快出结果；正确率不重要，更重要的是理解Feature Importance
    - Drawbacks: 学习能力有限 --> 需要大量的Feature Engineering
  - **如果选择Logit Regression，你觉得需要哪些feature**
    - Behavior Data（**更重要**）：Purchase History、Call Time(Midnight-->情绪崩溃), Date（weekend vs. weekday), Call Duration
    - Demographic Data：国籍、性别、年龄、职业、locaiton、用了多久服务
    - **Analysis**：
      - Purchase History：if 某个具体的brand或者category出现问题 --> customer satisfication becomes lower -->判断出这类商品出问题
      - Call Duration：if call duration 越长  --> customer satisfaction becomes higher --> 越容易Say Yes -->判断出customer service team 需要更多培训，回答更多问题

    
