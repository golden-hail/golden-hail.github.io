---
layout: post
title: Assessing Campaign Performance Using Chi-Square Test For Independence
image: "/posts/ab-testing.jpg"
tags: [AB Testing, Hypothesis Testing, Chi-Square, Python]
---

!!!In this project, we'll be running an A/B test on grocery retailer campaign data to determine whether the quality of the promotion mailers sent to customers for a membership had an impact on whether the customer signed up or not.

We will do this through applying the Chi-Square Test For Independence to measure the significance of the difference in signups between 2 groups.

# Table of contents

- [00. Project Overview](#overview-main)
    - [Context](#overview-context)
    - [Actions](#overview-actions)
    - [Results & Discussion](#overview-results)
- [01. Concept Overview](#concept-overview)
- [02. Data Overview & Preparation](#data-overview)
- [03. Applying Chi-Square Test For Independence](#chi-square-application)
- [04. Analysing The Results](#chi-square-results)
- [05. Discussion](#discussion)

___

# Project Overview  <a name="overview-main"></a>

### Context <a name="overview-context"></a>

In late June, our client, a grocery retailer, ran a campaign to promote their new "Delivery Club" membership. Signing up for the club costs $100 and gives customers free grocery deliveries for one year, starting June 1st.

For the campaign promoting the club, customers were put randomly into three groups:  
The first group received a cheap, low quality mailer, Mailer 1.
The second group received a colorful, high quality, high cost mailer, Mailer 2. 
The third group was a control group. They did not receive any mailer.

The client knows that customers who were contacted, signed up for the Delivery Club at a far higher rate than the control group, but are now curious as to if there is a significant difference in customer signup rate between the cheap mailer and the expensive mailer.  This will allow them to make more informed decisions in the future, such as whether it is worth it to spend the money on fancier mailers or not.

<br>
<br>

### Actions <a name="overview-actions"></a>

!!!!

Note: The *Z-Test For Proportions* is another viable test to run for measuring rates. 

<br>
<br>

### Results & Discussion <a name="overview-results"></a>

!!!!

<br>
<br>

___

# Concept Overview  <a name="concept-overview"></a>

<br>
#### A/B Testing

An A/B test takes two randomized groups, A and B, and provides them with different experiences. Both groups get their own version of an experience. 

For example, a company may post 2 different pictures advertising the same product. With an A/B test, we could look to measure whether either ad picture significantly impacted the amount of user clicks.  

Measuring the response of each group provides us with information that can help drive future business decisions. 

<br>
#### Hypothesis Testing

A Hypothesis Test is 

<br>
**The Null Hypothesis**



<br>
**The Alternate Hypothesis**



<br>
**The Acceptance Criteria**



<br>
**Types Of Hypothesis Test**

There are many types of hypothesis tests. 

<br>
#### Chi-Square Test For Independence


___

<br>
# Data Overview & Preparation  <a name="data-overview"></a>


___

<br>
# Applying Chi-Square Test For Independence <a name="chi-square-application"></a>

<br>
#### State Hypotheses & Acceptance Criteria For Test



```

<br>
#### Calculate Observed Frequencies & Expected Frequencies



___

<br>
# Analysing The Results <a name="chi-square-results"></a>



```python

# print the results (based upon p-value)


```
<br>
As we can see from the outputs of these print statements, we do indeed retain the null hypothesis.  We could not find enough evidence that the signup rates for Mailer 1 and Mailer 2 were different - and thus conclude that there was no significant difference.

___

<br>
# Discussion <a name="discussion"></a>
```
Because there is no significant difference between the signup rate of Mailer recipients, we could recommend that for the next promotion, the grocery store only send the cheap version of the mailers to customers. This can save the business money overall.

If we did however, determine that Mailer 2 led to significantly more customers signing up, then we may consider going forward with only sending out Mailer 2 to keep us ahead of the competition by appealing to newer folks.

