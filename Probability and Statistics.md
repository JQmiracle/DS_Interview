# Probability and Statistics



## Basic Probability

* The **probabiilty** of an event is a number indicating how likely that event will occur
* **Expectation** measures the **center** of that random variable's distribution
 **$$E[X] = \sum_{x \in X}xP(X)$$**
* **Variance** quantifies the **spread** of that random variable's distribution. The variance is the average value of the squared difference between the random variable and its expectation. (**Ex. Investor -- high  risk --> high return --> high variance**)
 **$$Var[X] = E[(X - E[X])^2]$$**
  $$Var(X) = E[(X - \mu)^2] = E[X^2] - E[X]^2$$

## Conditional Probability 
$$P(A \mid B) = \frac{P(A \cap B)}{P(B)}$$
* Two events A and B are not independent if: $P(A \cap B) = P(A\mid B)P(B)$
* Two events A and B are independent if: $P(A \cap B) = P(A)P(B)$

<img width="767" alt="Screenshot 2024-03-01 at 09 07 44" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/969d7978-3056-4883-bc3a-d0b55bbd34a8">

## Bayes' Theorem

* Bayes Rule - Formula 1: $$P (A \mid B) = \frac{P(B \mid A) P(A)}{P(B)} $$

* Deduction Steps：
  
  * $P(B \mid A) P(A) = P(A \mid B) P(B) = P(A \cap B)$

  * $P(B) = P(B \cap A) + P (B \cap  \neg A)$

* Bayes Rule - Formula 2: $$P (A \mid B) = \frac{P(B \mid A) P(A)}{P(B \mid A) P(A) + P(B \mid \neg A) P(\neg A)} $$

* Example: 

$$P(Sick) = 1 / 1000$$

$$P(Not Sick) =  1 - 1 / 1000 = 0.999$$

$$P(Pos \mid Sick) = 0.99$$

$$P(Pos \mid Not Sick) = 0.05$$

$$Thus, **P(Sick \mid Pos) = 0.0196**$$

* 估算法（带数字）：

<img width="687" alt="Screenshot 2024-03-01 at 09 45 18" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/369856c7-7f2a-40ec-9b5f-dfb560a5859a">

* Interview Question：
  * 确定A、B事件
  * 代入Bayes公式
 <img width="735" alt="Screenshot 2024-03-01 at 09 57 16" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/e83eb3a5-f558-4cf3-9db3-211e9e6656c0">

## Basic Stats Concepts

<img width="907" alt="Screenshot 2024-03-01 at 10 03 09" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/fe658058-c5f6-44e9-9976-88ea8f64f4d8">

### Expected Values

* Our sample expected values (the sample mean and variance) will estimate the population versions



* Linearity of expectation: $E[\sum_{i=1}X_i] = \sum_{i=1}E[X_i]$

### The Variance and Standard Deviation

* The **population variance**: $Var(X) = E[(X - \mu)^2] = E[X^2] - E[X]^2$

* The **sample variance** is also a random variable: $S^2 = \frac{\sum_{i=1}(X_i - \bar{X})^2}{n-1}$

* The **standard deviation $S$**: how variable the population is and it is a measure of the variability of a random variable.

**Assumption: Normal Distribution**

<img width="532" alt="Screenshot 2024-03-01 at 10 10 23" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/a5601837-94b1-4041-a667-ea006694c790">

<img width="889" alt="Screenshot 2024-03-01 at 10 13 59" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/c3c4ebe0-2490-47aa-a105-3c929aed159d">

### Sample Mean and Standard Error of Sample Mean

* The **average of random sample from a population** is itself a random variable: $E[\bar{X}] = \mu$ and $Var[\bar{X}] = \sigma^2 / n$

* The **standard error $S/\sqrt{n}$**: how variable averages of random samples of size $n$ from the population are

<img width="672" alt="Screenshot 2024-03-01 at 10 32 19" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/17a51d07-db8b-442d-a89f-17957c758f76">


## Relationship Between Variables

- **Causality**: Relationship between two events where one event is affected by the other.
- **Correlation:** Measure the relationship between two variables and ranges from -1 to 1, **the normalized version of covariance**.
- **Covariance:** A quantitative measure of the joint variability between two or more variables.
  $$Cov(X, Y) = \frac{1}{n}\sum_{i=1}^{n}(X_i - \bar{X})(Y_i - \bar{Y})$$
  $$Cor(X, Y) = \frac{Cov(X, Y)}{\sqrt{Var(X)Var(Y)}}$$
  $$Var(X)=Cov(X,X)$$

  
<img width="647" alt="Screenshot 2024-03-02 at 12 33 31" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/8ef04e8f-28fe-4f37-b50c-5d8081fdad39">

## Continuous Probability Distribution

- **Normal Distribution**: $f(x) = (2\pi\sigma^2)^{-1/2}e^{-(x-\mu)^2/2\sigma^2}$, $E[X] = \mu$, $Var(X) = \sigma^2$
- **The Central Limit Theorem (CLT)**: the distribution of **average of iid variables** (properly normalized) becomes that of a standard normal as the sample size increases (**n > 30**)
- **Law of Large Numbers：** The average of the results obtained from a large number of **independent and identical random** samples converges to the true value, if it exists

  ![image](https://github.com/JQmiracle/DS_Interview/assets/87022634/8cf488cf-bafe-426f-81c0-b2da8173ca5a)

  ![image](https://github.com/JQmiracle/DS_Interview/assets/87022634/462d8a7e-aeb1-4454-8326-612a6302e8e8)



## Discrete Probability Distribution

* **The Bernoulli distribution**: $P(X = x) = p^x(1-p)^{1-x}$, $E[X] = p$, $Var(X) = p(1-p)$

* **The Binomial Mass Function**: $P(X = x) = \binom{n}{x}p^x(1-p)^{n-x}$, $E[X] = np$, $Var(X) = np(1-p)$

<img width="712" alt="Screenshot 2024-03-02 at 12 53 25" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/79a3501e-2041-40da-9d0f-16c6aa75b626">

<img width="643" alt="Screenshot 2024-03-02 at 12 57 04" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/89b5d24d-e4b0-466e-96f6-9fe35286d1e7">


* **The Geometric Distribution**: 需要几次Bernoulli Trails才能成功一次的Probability Distribution， $E[X] = 1/p$, $Var(X) = q/p^2$
  
<img width="641" alt="Screenshot 2024-03-02 at 13 02 33" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/b4ffb2b4-81ec-4ff4-977c-52b57517e3d0">


<img width="537" alt="Screenshot 2024-03-02 at 13 09 14" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/031bd9de-46a0-4006-9f2b-5a8e6044bbb4">

  - Solution:
    - Normal Distribution: 68 - 95 - 99.7
    - Geometric Distribution
    - P(X = 拿到大于2的可能性)= 0.025
    - P(X = 拿到小于2的可能性)= 0.975
    - E[X] = 1 / p = 1 / 0.025 = 40

* **The Poisson distribution**:  $P(X = x; \lambda) = \frac{\lambda^xe^{-\lambda}}{x!}$, $E[X] = \lambda$, $Var(X) = \lambda$


<img width="648" alt="Screenshot 2024-03-02 at 13 21 18" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/7d3e5e1d-6ccf-4da6-b7e9-bb7522631bed">


<img width="719" alt="Screenshot 2024-03-02 at 13 31 58" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/c2dea28c-2b70-41be-a472-a8a5f34394ba">



## Interview Questions
<img width="909" alt="Screenshot 2024-03-04 at 11 01 35" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/2fe1ce13-6702-41c8-91b8-3f327ec2a0d9">

- Binomial Distribution:
    1. Each trail is Bernoulli
    2. Each trail is independent
    3. P(success) is 5% for each trail
- Normal Approximation for Binomial Distribution:
    1. n >= 30
    2. np >= 5
    3. nq = n(1-p) >= 5
 

