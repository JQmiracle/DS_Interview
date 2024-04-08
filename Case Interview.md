# Metrics Framework - Part 1
<img width="752" alt="Screenshot 2024-03-18 at 19 46 07" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/20e5c714-9c89-4508-85f9-e3a4b9fa3938">

## 1. Case Interview
<img width="767" alt="Screenshot 2024-03-18 at 19 48 31" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/519fd9c0-804a-45df-b39f-e0ab7963339e">

## 2. Why Case Interview
<img width="719" alt="Screenshot 2024-03-18 at 20 07 42" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/db242fb8-1ed2-41f1-b904-f94530181b8b">

## 3. Common Frameworks

### Ex. Study why my profit margin reduces.

- **Profit = Revenue - Cost**
  - Revenue = R1 + R2 + R2
  - Cost = Fixed Cost + Variable Cost
- **Revenue 下降**
  - 研究哪个产品Revenue下降
    - 如果产品1 Revenue下降，研究产品Revenue的具体来源
    - Revenue = Price * Volume
      - **假设销量降了，去探寻是局部销量下降 or 全局销量下降** 
- **Cost 上升**

  <img width="862" alt="Screenshot 2024-03-18 at 20 16 01" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/c99bc39a-9cc1-426e-8b87-b71b6a51e929">

## 4. Common User Analysis Framework
### AARRR (New users become loyal users)
<img width="915" alt="Screenshot 2024-04-01 at 10 49 18" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/ab30e280-41ca-430a-b928-c07a14a7b66a">

- **Acquisition: Users find you**
  - **Marketing**:
    - **organic:传统方法**
    - **paid / advertising**
      - App store 打广告
      - 路边巨大二维码广告
      - 电视广告
  - **Acquisition Cost**
  - **Marketing Channel（考虑那个channel投入最大，而且不同channel触及的人群不一样，所以同样要考虑diversification）**:
    - **Optimize 投资回报率 + 人群 Diversification** (三方面考虑！！！)
      - Volume (考虑每个channel内部有多少potential customers)
      - Cost (100$/customer vs. 10$/customer)
      - Quality (Conversion Rate)
        - Ex. 公司早起阶段，更愿意牺牲Revenue，获得更多的增长和客户流量
        - Ex. 公司成熟阶段，成长瓶颈期，新用户的增长的重要性降低，更愿意寻找变现的途径    
    - Channel Examples:
      - 发传单
      - Twitter上发广告
      - Google Ads
 
- **Activation: Users' first experience with your product**
  - **用户下载软件且完成一些基本操作**
  - Ex.完善个人Profile； Netflix选择10部喜欢的电影；
  - Ex.Facebook activation point： if connect 10 friends within a week --> high prob of retention rate

- **Retention: Means and rates of users returned**
  - **最最重要！！！**
  - DAU, MAU 也重要！！！
  - $$Week-X-Retention (Weekly)  = \frac{num-of-users-retained-on-week-X}{num-of-users-who-started-using-product-on-week-0}$$
    - Week 0 100 -> 100%
    - Week 1 50 -> 50%
    - Week 2 20 -> 20%
    - **每个用户的week 0不一样，所以需要按照不同起始日分成cohort计算**
      - Datelist Feature
    - **Retention Curve (J - Curve)**
     <img width="459" alt="Screenshot 2024-04-01 at 11 07 21" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/5395cf70-43b8-431a-b74a-69249d56727b">

      - 健康的Retention Curve：从week 4 之后，变成平稳，会有20%的loyal customers，找到了PMF（Product Market Fit）
      - 不健康的Retention Curve：从week 4 之后，会一直下跌，直到0%。即使DAU有100万人，但是会一直流失客户，所以是个非常大的warning
        - 可以做出改变，然后对比新旧的retention curve
      - **Retention Metrics 的一些注意事项**：
        - Lagging Metrics：现实生活中，**可能需要花很长时间**(6-12months)才能观察到平稳期出现
          <img width="457" alt="Screenshot 2024-04-01 at 11 16 52" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/98319e78-34cf-4dbb-9612-2006961e58f5">
        - 解决办法：
          - 把注意力集中在前几周，最快下降最大可能出现在第一周（一般用户不喜欢的话，会在一周内离开APP）
          - 尽快看到前三周signal，及时改善产品，稳定retention rate

- **Referral: Users tell the others about you**
  - **Goal: 吸引更多用户**
  - Methods: Word-of-mouth, incentives,  
  - 面试比较少涉及
 
- **Revenue: The profits you gain**
  - Business Model
    - subscription fee
    - advertisement revenue
    - Or, Just care about the customer growth rate 
  - 判断现阶段是否盈利
    - Ex. 推送内容改变 -> Engagement 提升(广告Space 改成 和用户息息相关的内容) -> But, Ad Revenue 大幅下降（Guardrail Metric） -> **这个recommendation不能接受**
   
- **AARRR Example**（Model APP Customer Purchase Funnel）
  - Customer Lifetime Value
    - Average User spent / Month = 10$
    - Monthly Retention = 20% (Stabilized)
    - Monthly Churned Rate = 80% (Stabilized)
    - Average User Lifetime Period
      - If a firm has a 60% loyalty rate, then their loss or churn rate of customers is 40% (Note: These two rates always add to 100%.)
      - Customer lifetime value period can be calculated as 1 /40% = 2.5 months. 
    - **Customer Lifetime Value** = Average User spent / Month * Average User Lifetime Period  = 10 * (1 / 80%) = 12.5$
      <img width="1140" alt="Screenshot 2024-04-08 at 13 09 41" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/67287c2d-38e7-448c-847d-45597b49133b">


## 4. Key Metrics in Social Network (Social Media App(Care More): Linkedin, WeChat, Facebook...)
- **Growth（用户的覆盖面宽度）** 
  - DAU
    - **existing users + new users + resurrected users(复活用户) - churned users**
    - 如何定义：
      - 但凡一个用户在过去一周内active过至少一次
      - active的具体定义
        - 至少login一次
        - 至少take meaningful action 一次
        - 至少发过一张图片
        - ...    
    - 每年APP活跃度对比，如果活跃度提升，证明APP更加active -> 更多人愿意在APP打广告 -> Potential Ad Revenue Increases
  - WAU
  - MAU
- **Engagement（用户使用产品的深度）**
  - **Time Spent**
    - 用户APP使用时间越久，看广告的可能性越大，广告商更愿意投放广告
  - **重要：Lness**
    - L7：过去7天用户在APP上活跃天数
      - L7 = 3 ：On Average，过去7天用户在APP上活跃天数为3
    - L28 过去28天用户在APP上活跃天数
      - L28 = 10 ：On Average，过去28天用户在APP上活跃天数为10
  - **\# of session**
  - **\# of meaningful actions: posts/comments/likes/shares**
 
- **Retention**
  
