# Metrics
A framework to define the most critical metrics to track a product’s success.

## About
The metrics question tests your ability to define the most critical metrics to **track a product’s success** and **find where to dig deeper if it is not doing well**.

## Evaluation
The interviewer wants to see your process of identifying the most critical metrics. They want to know **how you derive them** and **your reasoning behind why they are important**. The interviewer will be looking for these signals:

- **Analytical**: Are you structured and logical in your approach
- **Product goal**: Do you identify what the goal of the product is?
- **Metrics**: Do you specify the **most important things to measure and explain your reasoning**?
- **Communication**: Do you communicate clearly and succinctly?

## Metrics Framework
The framework below provides a logical and structured way to derive and defend your metrics. You start by identifying your product’s most important goal. This goal represents a target on the horizon that gives direction to all product-related activities. Your objective in defining metrics is to enable the product team to measure if they are achieving the goal and if the product has healthy user activity.

To do that, you will define **two sets of metrics**. One set measures **how well the product is achieving the product goal**. And the other set, **health metrics**, measures the health of funnel activity around **user acquisition, engagement, and retention**. Health metrics help **pinpoint which parts of the product are not working well.**

The following steps summarise this framework in a nutshell:

- Explain your approach
- Define the product goal
- Define goal metrics (North Star, Counter Metrics, Guard rail metrics)
- Define health metrics (Users, behaviours, and Health Metrics)

Detailed descriptions of each of these steps follow.

### 1. Explain Your Approach
Describe to the interviewer your approach to defining metrics. 

For example
- My approach to defining metrics is to define two sets of metrics.
- One set of metrics, which I call goal metrics, measures success towards achieving the product goal.
- And another set of metrics, which I call health metrics, measures the success in acquiring, engaging and retaining users.
- I will start this process by defining the product goal first.

### 2. Define the Product Goal
Infer what user problem the product solves, and reframe it into a product goal. 

For example
- if the product were Zillow, 
- then “Zillow is a real estate marketplace where agents advertise properties to sell or lease them. Buyers/renters want to find places to buy or rent. 
- The problem it solves is connecting these two parties to fulfil those needs. 
- Thus, the **product goal** is to **help agents and buyers/renters find each other to transact on the properties**.”

### 3.Define Goal Metrics
Define metrics related to the product goal: a North Star metric, counter-metrics, and guard rail metrics. 
- A North Star metric measures the success of the product goal.
- Counter metrics measure anything that goes against the product goal.
- And Guardrail metrics provide thresholds, usually **business metrics, that, if overrun, should cause alarm**.

  - **North Star Metric**
    - Propose three candidate metrics and discuss which one is the metric that best measures the product goal.
    - Discussing and prioritising one metric will allow the interviewer to get the signals they want about how you derive and prioritise metrics.
    - For the Zillow example
      - a metric that best measures the product goal could be the **number of sold/rented properties**
      - because it signals that **both the agent and buyer/renter accomplished their objectives**.
      - The agent sold/leased the property, and the buyer/renter found a place to live.

  - **Counter Metrics**
    - Use counter metrics to check that your North Star metric is not being gamed.
    - A single metric is not enough to conclude your product is doing well. For example, on Twitter, hashtags help people find relevant posts about topics they are interested in.
    - A North Star metric that measures this goal for a hashtag could be “the number of Twitter posts viewed by users after a hashtag search or click.”
    - However, users will eventually stop using hashtags if the posts’ content has nothing to do with the hashtag.

For example, this could happen if post creators want to clickbait users. So just using the number of posts viewed is not a sufficient measure of success. You must also define a metric that signals a counteraction to the product goal. One counter metric could be the percentage of posts that have nothing to do with the hashtag. Thus you can do a sanity check with this counter metric.

Other funnel metrics could also serve as counter-metrics.

Guard Rail Metrics
Guard rail metrics are usually business metrics with thresholds that should not be surpassed because your business will be in danger. Examples are revenue, Average Revenue Per Unit (ARPU), costs, etc.

Define Health Metrics
To define these metrics:

Think about the different things users do with your product, from the moment they sign up or fill out a form (acquisition) to the times they use the product’s features (engagement) to the “Aha!” moment when the product solves their problem (conversion).
Think about how you can detect if a user returns for more (retention).
Pick the most meaningful behaviours you want to track and the metrics that measure those behaviours and/or artefacts created by those behaviours. Always explain why these behaviours or artefacts are the most important to measure.

Using Zillow as an example, we will define health metrics for Zillow using the steps above.

Users
Identify the different user roles and their goal in using the product. In the case of Zillow, there are two types of users, the property agent and the buyer/renter. The agent’s goal is to sell or rent properties. The buyer/renter’s goal is to find a property of their liking to buy or rent.

Behaviours
For each user type, describe their journey from signup (acquisition) to the moment they solve their problem or “Aha!” moment (conversion). In other words, what behaviours do the users exhibit in this journey?

Then think about the most important behaviours to measure because they directly signal user growth, engagement, and retention. Always explain why these behaviours are important to measure.

Define metrics that measure those behaviours or artefacts created by those behaviours.

Health Metrics Example
For example, let’s do this for Zillow’s buyer/renter role. Their journey is as follows: they signup, search properties, or browse properties by categories; they like and save listings; they book an appointment or message an agent.

Some questions you may ask to see if the user base is growing, they are engaging and returning are:

How many people are signing up (acquisition stage)? We want to know this because it establishes the top-of-funnel user base. It will help us track growth and conversion rates through the funnel.
How many people are searching or browsing (engagement stage)? This number tells us if people are taking the first step in using the product.
Are people saving favourites (engagement stage)?. This behaviour is the first signal of genuine interest in properties which is a pre-signal to conversion—a crucial moment.
Are people booking visits (“Aha!” moment for buyer/renter)? This behaviour signals the “Aha!” moment for buyers/renters. And it signifies we have accomplished the user goal.
Are people returning to look for more properties (retention)? This behaviour signals whether the user values our product enough to come back.
Finally, define the metrics that answer each question we posed:

#number of signups per week/month
#number of searches per week/month
#number of views per week/month
#bookings per week/month
%people that return week over week, month over month
Pick the time interval that makes sense depending on how frequently users use the product.
