# Probability and Statistics



## Basic Probability

* The **probabiilty** of an event is a number indicating how likely that event will occur
* **Expectation** measures the **center** of that random variable's distribution
 **$$E[X] = \sum_{x \in X}xP(X)$$**
* **Variance** quantifies the **spread** of that random variable's distribution. The variance is the average value of the squared difference between the random variable and its expectation. (**Ex. Investor -- high  risk --> high return --> high variance**)
 **$$Var[X] = E[(X - E[X])^2]$$**

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

$$P(Pos \mid Sick) = 0.05$$

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


