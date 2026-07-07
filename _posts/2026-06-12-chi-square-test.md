---
layout: post
title: Assessing Campaign Performance Using Chi-Square Test For Independence
image: "/posts/AB_testing.jpg"
tags: [AB Testing, Hypothesis Testing, Chi-Square, Python]
---

In this project, we'll be running an A/B test on grocery retailer campaign data to determine if the quality of promotion mail sent to customers significantly impacted who signed up for a promoted membership. 

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
* The first group received a cheap, low quality mailer, Mailer 1.
* The second group received a colorful, high quality, high cost mailer, Mailer 2. 
* The third group was a control group. They did not receive any mailer.

The client knows that customers who were contacted, signed up for the Delivery Club at a far higher rate than the control group, but are now curious as to if there is a significant difference in customer signup rate between the cheap mailer and the expensive mailer. This will allow them to make more informed decisions in the future, such as whether it is worth it to spend the money on fancier mailers or not.

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
### A/B Testing

An A/B test takes two randomized groups, A and B, and provides them with different experiences. In the A/B test, we measure the response of each group to understand the impact each experience had on the response. These insights can help drive business decisions in the future.

For example, a company may post 2 different pictures advertising the same product on their website. With an A/B test, we could look to measure if the picture used in the ad significantly impacted the amount of users who clicked on the ad. If one ad yielded significantly more clicks, the business can use this data when thinking about what characteristics got the user to click and incorporate those features into future ads.

<br>
### Hypothesis Testing

A Hypothesis Test is a statistical method used to evaluate the likelihood of an assumption on a population, using sample data. It determines whether an observed pattern or correlation in the data is due to a true relationship or due to random chance.

There are multiple types of Hypothesis Tests as well as many scenarios we can run them on. 

When performing any Hypothesis Test, the following must always be defined:

<br>
**The Null Hypothesis**

The Null Hypothesis is a statistical assumption stating that there is no statistically significant relationship, association, or difference between two outcomes or groups. We run a Hypothesis Test to either reject or accept this Null Hypothesis.

<br>
**The Alternate Hypothesis**

The Alternate Hypothesis suggests that there is a measurable relationship, effect, or difference between variables, directly contradicting the Null Hypothesis. When rejecting the Null Hypothesis, we are accepting the Alternate Hypothesis.

!!! Confident result is not by chance? 

<br>
**The Acceptance Criteria**

The acceptance criteria is the specified p-value defined at the is also our p-value threshold. Or rejection criteria?? 

a p-value is

<br>
**Types Of Hypothesis Test**

There are many types of hypothesis tests. 

<br>
#### Chi-Square Test For Independence

The **Chi-Square Test For Independence** is a hypothesis test used to determine whether a significant association exists between two categorical variables. It compares the *observed frequencies* from the actual data points collected from a sample against the *expected frequencies*, the rates expected to be seen if the two variables were truly independent.

The *Null Hypothesis* described above is our baseline assumption. It assumes that there is no relationship or difference between the two variables. It asserts that the observed frequencies will match the expected frequencies, with any correlation or minor difference is the result of random chance.

The *Alternate Hypothesis* 

----


The *assumption* is the Null Hypothesis, which as discussed above is always the viewpoint that the two groups will be equal.  With the Chi-Square Test For Independence we look to calculate a statistic which, based on the specified Acceptance Criteria will mean we either reject or support this initial assumption.

**Note:** Another option when comparing "rates" is a test known as the *Z-Test For Proportions*.  While, we could absolutely use this test here, we have chosen the Chi-Square Test For Independence because:

* The resulting test statistic for both tests will be the same
* The Chi-Square Test can be represented using 2x2 tables of data - meaning it can be easier to explain to stakeholders
* The Chi-Square Test can extend out to more than 2 groups - meaning the business can have one consistent approach to measuring signficance

___

<br>
# Data Overview & Preparation  <a name="data-overview"></a>

Our table of interest in the grocery client database is the *campaign_data* table. 
This table contains each each unique customer_id, the type of mailer they received, if any, and whether or not the customer signed up for the Delivery Club membership.

To determine whether the fancier Mailer 2 lead to a significant difference of people to sign up as opposed to the cheaper Mailer 1, we will first need to exclude the control group from the data by extracting the customers who got either mailer.

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
Below is a 10 row sample of the imported **campaign_data** DataFrame:
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

In the **campaign_data** DataFrame we have the following columns:

* customer_id
* campaign name
* mailer_type (either Mailer1 or Mailer2)
* signup_flag (either 1 or 0)

___

<br>
# Applying Chi-Square Test For Independence <a name="chi-square-application"></a>



<br>
#### State Hypotheses & Acceptance Criteria For Test

To kick off our Hypothesis Test, we'll need to define our **Null Hypothesis**, our **Alternate Hypothesis**, and our **Acceptance Criteria**. (See more on these terms in the *Concept Overview* section above)

For our Acceptance Criteria, we'll be using the commonly used value of 0.05 (or 5%).

```python
# specify hypotheses & acceptance criteria for test
null_hypothesis = "There is no relationship between mailer type and signup rate.  They are independent"
alternate_hypothesis = "There is a relationship between mailer type and signup rate.  They are not independent"
acceptance_criteria = 0.05
```

<br>
#### Calculate Observed Frequencies & Expected Frequencies

As detailed in the *Concept Overview* section above, our **observed frequencies** come directly from the rates per group in our collected data. In this case, our observed frequencies come directly from our campaign_data imported above.

!!!! For our *expected frequencies*, we will be calculating infered population parameters

!!!! Explain it.. maybe insert picture. Categorical variables Mailer1 and Mailer2. (See more on these terms in the)

Now, we'll create our 2x2 matrix needed for the Chi-Square approach, using a method called **crosstab()**. 

Our observed values come directly from our campaign_data imported above. We are analyzing the impact Mailer type had on member sign up rates, so we'll want to pass these values into our method.

Need to pass in an array to Chi-Squares contingincy function, use .values property for observed_values


___

<br>
# Analyzing The Results <a name="chi-square-results"></a>



```python

# print the results (based upon p-value)


```
<br>
As we can see from the outputs of these print statements, we do indeed retain the null hypothesis.  We could not find enough evidence that the signup rates for Mailer 1 and Mailer 2 were different - and thus conclude that there was no significant difference.

___

<br>
# Discussion <a name="discussion"></a>

Because there is no significant difference between the signup rate of Mailer recipients, we could recommend that for the next promotion, the grocery store only send the cheap version of the mailers to customers. This can save the business money overall.

If we did however, determine that Mailer 2 led to significantly more customers signing up, then we may consider going forward with only sending out Mailer 2 to keep us ahead of the competition by appealing to newer folks.

ROI in campaign by saving money on mailers, if expanding to other stores in a chain or a wider audiance after the pilot 

