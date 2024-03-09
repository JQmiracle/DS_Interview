# Hypothesis Testing & Statistical Significance
<img width="689" alt="Screenshot 2024-03-04 at 11 05 43" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/0a50e0e0-a123-4213-9e5d-55fee1efb66f">

## Hypothesis Testing
- Hypothesis testing refers to the formal procedures used by statisticians to reject or not reject statistical hypothesis 
- **小概率事件设为Null Hypothesis**

<img width="1029" alt="Screenshot 2024-03-04 at 11 15 08" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/56025577-8921-4b55-bd02-48a59fced035">


## Type I and Type II Error
- Type I Error: 把 H0 --> 判断成 Ha (H0 is true)
- Type II Error: 把 Ha --> 判断成 H0 (Ha is true)

<img width="856" alt="Screenshot 2024-03-04 at 11 22 44" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/37283c42-3725-4986-a1dc-95508988bc4a">

## Alpha and P value

- **$\alpha$** = **Significance Level** = **False Positive Rate**
  - The probability of rejecting the null hypothesis when the null hypothesis is true
  - The probability of committing a Type I Error
- **P value** = Assuming H0 is correct, **the probability of obtaining test results** at least as extreme as the results actually observed (how extreme the data is)
- P value 实际上观测到 **given null hypothesis is true**； Alpha 人为设定。
- if P value <= alpha, reject null hypothesis
- if P value > alpha, fail to reject null hypothesis
- **人为设置 Alpha value (Significance Level) 越大，越容易 Reject Null Hypothesis == The Probability of committing a Type I Error Increases**.

  

<img width="874" alt="Screenshot 2024-03-04 at 11 31 16" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/f5721fdd-c291-4090-8dfb-c96e7d3021fd">

<img width="932" alt="Screenshot 2024-03-04 at 11 51 37" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/ab07248f-3b64-4fd3-86d2-e4ae2353f161">

<img width="952" alt="Screenshot 2024-03-04 at 12 00 57" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/2f8046f5-f44b-4a02-b005-ef0b20973b63">

- Interview Questions

<img width="928" alt="Screenshot 2024-03-04 at 12 43 33" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/e607a2e8-22e2-4ec4-a164-ed1e5ad295ea">

### What is P Value
- Given H0 = True
- Probability >= Observed Value
- 我们观测到的Observed Value = 10, 实际上 $X>=10$ 的Probability 就是 P Value
  




## Power

* Power: the probability of rejecting the null hypothesis when it is false

* **$\beta$ = Type II error rate** = Probability of failing to reject the null hypothesis when HA is true

* Power = 1 - $\beta$ (Ex. Power = 0.8 ; $\beta$ = 0.2)

* **Factors Affecting Power**:
  - Size of the effect --> increase the effect --> increase the power
  - Standard deviation of the metrics --> decrease the std --> increase the power
  - Sample Size --> increase N --> decrease the std --> increase the power
  - Significance level (alpha) --> increase $\alpha$ --> decrease $\beta$ --> increase the power
 

<img width="695" alt="Screenshot 2024-03-04 at 13 09 43" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/30036e19-c3a4-4e47-bd3d-0fd78586b2a6">


## Confusion Matrix

  <img width="695" alt="Screenshot 2024-03-09 at 11 00 41" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/00534070-2274-4623-bf42-1bac5c6513d1">
<img width="636" alt="Screenshot 2024-03-09 at 11 52 06" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/20ed2fa9-9151-4ba9-8750-7b453738d988">

  

  * Recall = TP / (TP + FN) 越大， Type II Error 越小
  * Precision = TP / (TP + FP) 越大， Type I Error 越小


## Z test

* The $Z$ test for $H_0: \mu=\mu_0$ versus $H_1: \mu<\mu_0$, $H_2: \mu \neq \mu_0$, $H_3: \mu>\mu_0$
* Test statistic: $TS=\frac{\bar{X}-\mu_0}{\sigma/\sqrt{n}}$
* Reject the null hypothesis when: $TS \leq Z_\alpha = -Z_{1-\alpha}$,  $|TS| \geq Z_{1-\alpha/2}$,  $TS \geq Z_{1-\alpha}$

### Interview Questions

<img width="739" alt="Screenshot 2024-03-09 at 11 10 02" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/4f434048-bfd8-4b90-92b3-a5fef343953e">

<img width="729" alt="Screenshot 2024-03-09 at 11 08 37" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/a2dd349a-a332-4b93-b001-250ef2ca5133">


<img width="681" alt="Screenshot 2024-03-09 at 11 24 56" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/47c341d2-ef13-4242-8161-a3ae322d32a5">

<img width="674" alt="Screenshot 2024-03-09 at 11 25 35" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/ee724c48-efee-42a6-9544-b2037f94880b">

<img width="722" alt="Screenshot 2024-03-09 at 11 26 34" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/4268c7ef-8c91-491e-b552-3edbbadb1523">


## T test

* Test statistic: $TS=\frac{\bar{X}-\mu_0}{S/\sqrt{n}}$
* S: 样本的std。但是，Z test的$\sigma$是代表总体的std，可以用估算（当n>=30）

<img width="686" alt="Screenshot 2024-03-09 at 11 32 05" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/aeb09cbd-94e4-499a-ad72-a00ef852496d">


### Interview Questions

<img width="629" alt="Screenshot 2024-03-09 at 11 46 12" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/b6055c78-63d8-43df-8908-d59b5bc7a655">

