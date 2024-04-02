# AB Testing From Scratch

## 1. A/B Testing 三大要素

- **Hypotheses**
  -  
- **GROUP A and GROUP B**
  - GROUP A：代表产品**现有的设计** 
  - GROUP B：代表hypothesis里想要**验证的新设计**
  - **实验对象并非全体用户**
    - 假设一周时间做AB Testing，很多用户没有机会登陆Airbnb，无论把他们分给A or B，都无法体验产品给出反馈
    - 及时一些用登陆Airbnb，使用的Website并非手机APP，这个时候feedback与手机APP用户体验毫无无关
    - Thus，以上两种用户都不是AB Testing实验对象
    - **Goal：尽量减少不相关的用户**
   
  - **实验分组**：
    - Group A 的用户锁定在组A
    - Group B 的用户锁定在组B
    - 实际工作中：会出现用户时而被分配到A，时而被分配到B，因此，在数据分析时，需要先Filter掉这些用户
    - **原则：Randomization**，任何符合条件的用户，都应该具有相同且独立的概率被分配到A or B
    - https://medium.com/@thisisflea/a-good-hash-is-hard-to-find-6edbbf6a78b0

   

- **Metrics**
  - Core / Success / Target Metrics (1 - 2 个)
    - 测量新功能是否呈现出预期的价值 
  - Tracking Metrics
    - 监测新设计如何改变用户行为
- Example：
  - 这个实验的Hypothsis 是什么？？
    - 假设把用户打开手机Airbnb APP，默认登录到Trips，可以提醒那些没有订房的用户，目前还没有任何旅行计划，以提高订房量
   
  - 这个实验对应的Group A and Group B的用户体验分别是什么？？
    - Group A：用户默认登录到Explore (确保这个用户每次默认登陆到Explore)
    - Group B：用户默认登录到Trips  (确保这个用户每次默认登陆到Trips)
   
  - 这个实验的Metrics 是什么？？
    - Core Metrics：订房量
    - Tracking Metrics：浏览量， 搜素房源的订房转化率
    - 两组之间订房量的difference
    - Example：
      - 如果看到订房量有减无增，且浏览量也下降  --> 用户登录到Trips，减少在Explore界面吸引用户直接浏览的房源的优势，看的少了，订的也少了，解释了新设计不可取的原因
      - 如果看到订房量有减无增，但是浏览量上升
        - 用户从Explore界面搜索房源得到房源列表的相关性 会比 用户从Trips界面，点击Start Exploring，再搜索，得到的房源列表的相关性要高 -> 因此被分到Trips的用户，虽然浏览的更多房源的搜索结果，但是还无法找到心仪的房源
        - Monitor两组的搜素房源的订房转化率，可以验证以上hypothesis是否正确
        
  - **Summary**： 通过A/B Testing -> 测量metric -> 来验证Hypothesis
 
