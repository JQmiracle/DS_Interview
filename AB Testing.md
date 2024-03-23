# A/B Testing

<img width="736" alt="Screenshot 2024-03-22 at 10 50 10" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/b94eafbd-7fb2-42e8-959c-cb780ba6e405">


## Why A/B Testing

- **Correlation <> Causality !!!!**

- **A/B Testing 做多了的弊端**
  - 牺牲用户体验(Customer Experience Inconsistence)
  - Team Culture 不好(engineer对于指标提升功利，短时间改变feature，只根据AB test短期结果)

<img width="762" alt="Screenshot 2024-03-22 at 10 59 08" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/f0c02cbc-df14-4b8a-a1be-c804462f06cb">

## A/B Testing Work
- SWE, DS, DE work together
- **先想好hypothesis，再choose metrics**
- Decision
  - Launch (All Positive)
  - Pause (Fix Current Problems)
  - Roll Back --> Switch to the original version (All Negative)
  
<img width="738" alt="Screenshot 2024-03-22 at 11 12 40" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/b4eacd67-4436-468b-8919-8255f2aa5e98">

## A/B Testing Universe
- Search, Gmail, Calendar 三个组的AB testing互相不影响，**可以共用用户Universe**
- Gmail Org下面两个组： UI + Email Thread --> UI组的change 会影响 Email Thread组 -->如果UI组的用户同时也在Email Thread组 -->**那么不可以共用用户Unvierse**
<img width="750" alt="Screenshot 2024-03-22 at 11 43 31" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/d34be235-dc0e-4282-b831-32a1f0c48263">


## When A/B Testing doesn't NOT work
- **When being first** >>> being optimal (市场上第一个产品 -->抢占先机--> 没时间做optimize)
- **When the implementation cost is high** (Ex. Build a new platform version costing 100 ENGs 30 days to finish)
  - Alternative Way (Light-weighted) to gather qualitative user experience:
    - User Survey
    - 1 vs 1 in-depth interview
    - Focus Group
- **When the user base is tiny**
- **When the effect takes a long time to measure**
- **When the risk of taking action is low**
  - Content Loading: 0.01s --> 0.008s
  - 没必要做AB Testing：
    - 对用户体验只好不坏
    - 提升幅度不会很大
    - 对feature进行Subtle Change，risk小 
<img width="720" alt="Screenshot 2024-03-22 at 11 59 55" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/e2dab508-83b1-4fe5-b6c9-568284665222">

## A/B Testing Process
<img width="707" alt="Screenshot 2024-03-22 at 12 04 29" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/67045d48-a208-4037-ba44-1b48163e2817">

## Design of Experiment (DOE)
- **Unit Randomization**
  - **Experiment Unit(考虑New Feature最后影响哪部分群体)**
    - user_id
    - admin
    - business_id
  - **Experiment Split Point**
    - Log in -> Browse Products -> Click Products -> Add to Carts -> Check Out
    - **Split Point: 决定在哪个点分成 Test vs Control**
    - **Check-Out 分组 比 Login 分组更好一些**
  - **Control and Test Experience**
    - Ex. Old Button Design(Control) vs. New Button Design(New)
- **Experiment Metrics**
  - Topline Metric (**核心Metrics** + 和hypothesis直接挂钩 + 1-2 个 Golden Metrics)
  - Tracking Metrics （**非最重要Metrics** + 和hypothesis不直接挂钩 + 方便其他组Monitor）（如果下降的话，对我们的hypo也不会是不好的signal）
  - Counter Metrics （**Guardrail** 护城河 + 我们不希望negatively impact counter metrics + Ex. Revenue）
    - 即使新的feature可以increase Topline，如果Counter Metrics Decreases，那么我们也不发布新的feature
    - 绝对不能降低Counter Metrics（从公司层面出发） 
- **Testing Plan**
  - Launch Plan
  - Monitoring Plan
  - Metric Evaluation 

<img width="761" alt="Screenshot 2024-03-22 at 13 23 35" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/c3f57133-b194-4abc-aa4f-05414c5dd1a1">


### Randomization Details
<img width="624" alt="Screenshot 2024-03-22 at 13 50 07" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/e60e7d39-74f3-4957-8561-fc5892801634">

- **Split Method**:
  - Green(33%) vs. Blue(33%) vs. Red(33%)
  - **Long Term Experiment: Holdout Group(10% for 6 month)**
    - 10 个 新feature --> 先后做 10 次实验
    - 假设每个feature，都能提升 Metric A 5%，我们不能判定出10个features一起上线的情况， Metric A的变化情况
    - Holdout group 看不到 这10个新的feature --> 6个月后比较 Metric A 长期的变化
   
### Quiz
- 1. **Doordash wants to test the impact of an item search function in a grocery page**.
    - **User_id Unit Randomization**
    - 50% 用户 不能使用 item search function
    - 50% 用户 可以使用 item search function
    - **Topline Metrics**:
      - \# of searches / user
      - \# of empty searches / user (空搜率 -> 预估转化率)
      - \# of orders / user
      - \# of items / order
    - **Tracking Metrics:**
      - The average of time spent:
        - if 变长 --> 更enjoy这个feature -->想把所有东西都搜一遍
        - if 变短 --> 点菜更加高效
    - **Counter Metrics**:
      - total revenue
      - total price / order (因为顾客可以更精确的找到物品，而不是滑着滑着随意添加到购物车，可能导致total price/order 下降，即使总order提升)
      - user retention
- 2. **Doordash wants to test the impact of a change in a payment setup process on user retention rate**.
     - **User_id Unit Randomization**
     - 如果用order_id, 一个用户会有50%几率看到new feature，50%几率不会 --> 影响用户体验
- 3. **Facebook wants to test a change in a business posting tool**.
     - **Business_id Unit Randomization**
     - 业界可能出现的问题：
       - 某个公众号有A、B、C三个人管理
       - 如果B同时还管理其他公众号的话，且按照business_id分组的话，B的user experience is inconsistent
     - 解决办法：
       - 如果按照admin_id分组（A、B、C）， user角度的话，user experience consistent
       - 问题：假设A分到新feature， B、C老feature -->对公众号管理很麻烦（因为只有A能看到新功能）
        
<img width="651" alt="Screenshot 2024-03-22 at 16 49 14" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/82476008-284e-4215-bae9-c15efa10161d">

## Exposure Plan （How long should the experiment run?）
- Estimate sample size
- How many users you have per day in each group
- Seasonality (>=2 weeks)
  - 7, 14, 21...
  - 周中、周末不同表现
- **Novelty Effect:**
  - 新鲜感，前几天很热情 --> 前期出现feature 显著变化 --> **需要谨慎** --> 等待一段时间后再判断
- **Gradually Launch**
  - 1% -> 10% -> 50% (one group)
  - 2% -> 20% -> 100% (two groups)

