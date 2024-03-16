# Product Sense

<img width="1315" alt="Screenshot 2024-03-14 at 16 01 34" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/95496b15-ce18-4ffa-8181-b9450c5a9a2d">


<img width="1254" alt="Screenshot 2024-03-14 at 16 16 13" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/9bc29ffe-0d99-4575-b144-de8673c7dddb">

## 1. MECE (Mutually Exclusive Collective Exhaustive
### 面试前准备
  - 使用公司产品
  - 答案围绕 Company Mission
### Common Mistakes Using MECE
  - **早期阶段：指出最重要的点**
  - Not Mutually Exclusive
  - Not Collectively Exhaustive
  - **No followup，No focus** (不要罗列太多点，容易挖坑)
  - Segment not parallel
    

<img width="1077" alt="Screenshot 2024-03-14 at 16 36 34" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/9b8e76c1-4531-4165-8ad8-e7e8c4542c91">

<img width="1161" alt="Screenshot 2024-03-14 at 17 04 40" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/9fc3eb88-d541-4f59-a8bb-0b545c0a0adf">

### Example：Zillow Company (Why real estate transaction volumn in greater LA area grow in 2020?)

- **Clarification**: Global -> US -> CA -> LA (Globally increase or only increase in LA area)
- **Macroecon vs Microecon** (和面试确认方向->Macroecon 不好控制->先focus在Microecon)
  - **Microecon**:
    - Demand: Buyer
    - Supply: Seller

## 2. ML Product Questions

<img width="956" alt="Screenshot 2024-03-15 at 21 10 28" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/1ccb3664-614b-45a7-996a-5891ea16293b">



<img width="516" alt="Screenshot 2024-03-15 at 21 08 28" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/8408d0b1-05fd-434c-83d7-bd308e3bad97">



<img width="572" alt="Screenshot 2024-03-16 at 00 29 21" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/f4d7dedd-092b-4430-bcc4-3dc6b9c44b1f">


## 3. Feature Questions


<img width="652" alt="Screenshot 2024-03-16 at 00 35 59" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/7cab2145-f114-4f6b-9b0a-86e36dc05eb8">


<img width="613" alt="Screenshot 2024-03-16 at 01 03 22" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/4821ea0d-8e78-4d02-8405-840daca98723">

## 4. Product Design Questions (Rarely Appear in the interview)


<img width="633" alt="Screenshot 2024-03-16 at 01 04 13" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/43e00c81-3879-4256-a7fb-0d21b6dbd0e6">


## 5. Brainstorm Questions （低频题）

<img width="657" alt="Screenshot 2024-03-16 at 11 10 14" src="https://github.com/JQmiracle/DS_Interview/assets/87022634/37187108-7311-4690-9622-af3ebdef1c1a">

### Can you estimate the daily revenue for Spotify?

- **Clarification**:
  - Daily Revenue 
    - Subscription Revenue
    - Ads Revenue
      - Ads between songs (更细化)
    - 问面试官，需要我们考虑那部分revenue
  - Market：
    - 地区性差异
    - 需要 Narrow Down to Specific Market（Ex.US Market）
    - Later, We can apply this framework to other regions
- **Calculation**:
  - DAU:
    - Internet Penetration: 90%
      - Song/Music Listener: 50%
        - Spotify User: 20%
          - Free User: 70%
  - Listening Music Habit Correlated to Age:
    - $\le 23 $
      - 40% population
      - 上下学 + 运动：2h
    - $23 - 45$
      - 30% population
      - 上下班 + 运动：2.5h
    - $\ge 45$
      - 30% population
      - 散步 + 遛狗：1h
    - Music Length：4min
    - After 3 songs, 15 sec Ads
      



