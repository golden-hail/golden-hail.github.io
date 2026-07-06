---
layout: post
title: Assessing Campaign Performance Using Chi-Square Test For Independence
image: "/posts/AB_testing.jpg"
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

When performing a hypothesis test, the following must be defined:

<br>
**The Null Hypothesis**

The null hypothesis is a statistical assumption stating that there is no real relationship, effect, or difference between variables in a population

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

Our table of interest in the grocery client database is the *campaign_data* table. 
This table contains each each unique customer_id, the type of mailer they received, if any, and whether or not the customer signed up for the Delivery Club membership.

To determine whether the fancier Mailer 2 lead to a significant difference of people to sign up as opposed to the cheaper Mailer 1, we will first need to exclude the control group from the data by extracting the customers who got either mailer.


<br>
```python

# import the required python libraries
import pandas as pd
from scipy.stats import chi2_contingency, chi2

# import campaign data
campaign_data = pd.read_excel(...)

# filter out the control group
campaign_data = campaign_data.loc[campaign_data["mailer_type"] != "Control"]

```
<br>
Below is a 10 row sample of the imported campaign_data DataFrame:
<br>
<br>

| **customer_id** | **campaign_name** | **mailer_type** | **signup_flag** |
|---|---|---|---|
| 74 | delivery_club | Mailer1 | 1 |
| 524 | delivery_club | Mailer1 | 1 |
| 607 | delivery_club | Mailer2 | 1 |
| 343 | delivery_club | Mailer1 | 0 |
| 322 | delivery_club | Mailer2 | 1 |
| 115 | delivery_club | Mailer2 | 0 |
| 1 | delivery_club | Mailer2 | 1 |
| 120 | delivery_club | Mailer1 | 1 |
| 52 | delivery_club | Mailer1 | 1 |
| 405 | delivery_club | Mailer1 | 0 |
| 435 | delivery_club | Mailer2 | 0 |

<br>

In the campaign_data DataFrame we have:

* customer_id
* campaign name
* mailer_type (either Mailer1 or Mailer2)
* signup_flag (either 1 or 0)

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

