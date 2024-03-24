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
- **Launch Plan**
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
<img width="1227" alt="Screenshot 2024-03-22 at 17 06 29" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/5730a130-0ad5-4da5-805d-0337d4ba5dbc">
<img width="623" alt="Screenshot 2024-03-22 at 17 07 00" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/5428a1c9-0403-49c9-b21f-404055ee5ab9">

- **Monitor Plan**
  - Novelty Effect
  - Peeking can be a problem
    - 如果连续看result10天，至少一次出现False Positive的概率是 $1 - (1-0.05)^(10) = 40%$
    - 这个概率很高，不能马上上线，不要因为一天positive就认为positive，要看到一个非常stable trend，每一天都是positive-->才决定是不是上线
  - Need to monitor for concerning changes
    - 假设new feature launch，但是发现第二天time spent下降10%，**需要立马pause**，尽管这个可能是个假的signal
    - 分析：measure有问题 还是 实验真的造成negative impact
 
## Metric Evaluation 
- If metrics **move positively**
  - Is the result expected??? If see, launch
  - Need further investigation if results look too good to be true
    - 原本预计improve 2%，但是result是5%
    - Check Experiment Randomization Setup
    - Check Metrics Calculation ...
- If metrics **move negatively** --> **面试常见考点**
  - Expected? If not, deep dive to find causes(Bug? Data Logging issue??)
    - Content Loading Time: 即使move negatively，也是好事
    - Time Spent: 我们希望move positively，但是move negatively， Need to find causes
  - Consider Trade-Off(eg. **comment** increase 1% > **like** decrease 1%)
    - comment + like 都是topline metrics
    - 工作中常见的Trade-Off
    - Comment花的effort 要比 Like花的effort 多 --> 所以Comment是相对重要的Metrics --> Comment 也提供了内容的产出 --> 进一步刺激Engagement(Like, Comment, Repost) --> 我们愿意去Trade-Off --> **Overall Net Gain is Positive**
   
- If metrics are **neutral**
  - Is the experiment under-powered
    - Not Enough Sample Size
    - Other Reasons (Seasonality-->导致app traffic变少-->达不到预计sample size) 
  - Is the result positive on a specific segment
    - Subsegment vs. Overall
    - **Subsegment vs. Subsegment**
      - different regions (North America, Asia)
      - different platform (IOS, Android)
  
<img width="882" alt="Screenshot 2024-03-23 at 13 07 11" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/144fcf31-dabf-48ff-8a9a-1a85ba0d4ac5">

## Multiple Testing
- 如果连续看result10天，至少一次出现False Positive的概率是 $1 - (1-0.05)^(10) = 40%$
- Correction：
  - 降低False Positve可能性
  - **Bonferroni Correction（简单粗暴）**
    - Set Alpha_i =  alpha / m for each experiment
    - Ex. alpha = 0.05, 10 experiments --> alpha_new = 0.05 / 10 = 0.005
    - **Drawbacks**: 矫枉过正，hard to detect stat sig difference and hard to reject null hypothesis
  - **False discovery rate adjustments**
    <img width="703" alt="Screenshot 2024-03-23 at 13 21 39" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/b36ac9a2-5d26-4f7b-b130-751173e343e4">


## Common Problem
- **1. Network Effect**
  - Facebook
  - Linkedin
  - Wechat
  - **Ex. Red Pocket**
    - Goal: increase engagement
    - Test(enable red pocket) vs. Control (not visible red pocket)
    - 假设2人in Test Group， 2人in Control Group
    - Send a red pocket to a person in the control group, the person can't see it and gets confused!!!
    - Test users didn't get a response from the receiver, which decreased the engagement in the test group due to the network effect.
    - **Solution:**
      - **Country Level / Region Level / Isolated Region Test**
        - 两个相似地区，其中一个为control，另外一个为test，两者互不联系
        - Australia vs. New Zealand
        - LA vs New York
      - **Network Clustering**
        - user 和 user's friends assigned to the same cluster
        - Decrease intervention
       
  - **Tinder, Bumble, CMB**
    - 无法做 Network Clustering，User‘s Goal is not to engage with friends. Otherwise, the goal is to know more strangers
    - 无法做Country/Region Level Test.
   
  - **Ex. Video Call**
    - Goal: increase average video call time
    - Test(Improve video call button) vs. Control (nothing change)
    - 假设 my friend in the Test Group， I am in the Control Group
    - my friend is more likely to call others due to the new feature, including the video call with me, which increased the average video call time also in the control group
    - if the Test average video call time **increases by 10%**, the overall average video call time **increases by more than 10%**(Test User average video call time increases and also user average video call time increases --> **we underestimate average video call time**)
    - **Solution:**
      - **Country Level / Region Level / Isolated Region Test**
        - 两个相似地区，其中一个为control，另外一个为test，两者互不联系
        - LA (Test) vs SF (Control)
      - **Network Clustering**
        - user 和 user's friends assigned to the same cluster
        - Decrease intervention
 <img width="774" alt="Screenshot 2024-03-23 at 14 56 31" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/41ee1a19-c28a-4ed0-bda0-3ce927144029">


- **2. Marketplace**
  - Uber
  - Airbnb
  - Doordash
  - **Multi-Sides**：
    - Drivers
    - Customers
    - Restaurants
    - Delivery Persons ...
   
  - Ex. **Uber Eats**
    - Treatment: Simplify Order Process
    - Control: Nothing Change
    - Metrics: Total Order Time = Receive Food - Start Order (Topline)
    - Test and Control Groups share the same driver pool and restaurant pool
    - 哪怕没有直接影响，但是有间接影响 （都拿Uber Eats点餐 --> 同家restuarant + 同家 Driver --> restuarnt 先做Test Users + driver 先送 Test Users -> 对Test User提升based on 牺牲Control Users）
   
  - **Ex. Uber (Overestimate)**
    - Treatment: better-matching algo
    - Control: Nothing Change
    - Place: Shanghai
    - **if the Test average waiting Time **decreases by 10%**, the overall average waiting time **decreases by less than 10%**(对Test User提升based on 牺牲Control User)
   
  - **Solution:**
    - **Region Level / Isolated Region Test**
      - 两个相似地区，其中一个为control，另外一个为test，两者互不联系
        - **Assumption**:
          - User Behaviors are comparable
          - Driver Behaviors are comparable
          - Driver:Customer Ratios are comparable)
          - Public Transportation is comparable （公共交通便利地区 ———> 打车可能少）
          - Weather is comparable (下雨天打车多)
          - ...
      - LA vs SF
    - **Switching Hours**
      - 7 - 8 for Control (everyone)
      - 8 - 9 for Test (everyone)
      - 9 - 10 for Control (everyone)
      - ...
      - **Cautions:**
        - 不能是user visible feature change（界面改变）
          
  <img width="1016" alt="Screenshot 2024-03-23 at 15 44 35" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/4be7e476-2112-4d11-ac4e-1f7a9b34cf3f">

  - **3. Simpson‘s Paradox**
    - Reasons:
      - The setup of your experiment is incorrect
        - Randomization is not enough
        - Exposure Imbalance in Test and Control Groups
      - The Change affects new users and experienced users (or other user segmentation) differently 
   
<img width="724" alt="Screenshot 2024-03-23 at 16 25 31" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/ebf5e96f-e1e1-4b49-bd32-9ab394f51f3d">

## Interview Questions
<img width="1064" alt="Screenshot 2024-03-23 at 16 55 18" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/3b5f1540-e14c-4362-9009-eabbe18a594e">

#### 1. There are two experiments, and we want to test 3 versions of algo A, B, C. Two options, **The first experiment** A vs B and use the winner to test C again. **The second experiment** is to compare A, B, and C together. **Which one do you propose and why?**

**Solution:**
- **Clarification Questions**: A(Red), B(Blue), C(Current Version)
- **Sample Size**
  - We need to make sure that we have enough power to detect the statistically significance difference
  - The sample size is not enough --> Option 1
  - The sample size is enough --> Option 2
- **Time**
  - if we have enough time to launch this feature, A vs.B 14 days + winner vs.C 14 days = 28 days
  - if we don't have enough time to launch this feature, A vs.B vs. C 14 days
    - Control the external effects, since all three arms are tested in the same time frame
    - Or, We save time
- **User Experience**
  - Option 1 --> 可能存在一个User经历三个版本的情况（Randomization做不好） --> user experience inconsistent --> 对feature体验不好，产生aversion
 
- **Conclusion**: We can't easily make a conclusion about which one is better and each has a tradeoff.
  


#### 2.Pinterest Product Analyst Experiment
<img width="986" alt="Screenshot 2024-03-23 at 17 18 20" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/ccf88798-a3c1-4164-a913-33143418de90">

- **Why do we need to do this AB Testing?????** -> First question to clarify
  - Goal: 提升search的experience + 更多的下载图片 
- **what metrics would you like to measure?**
  - 


      
