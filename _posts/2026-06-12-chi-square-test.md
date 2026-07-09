---
layout: post
title: Assessing Campaign Performance Using Chi-Square Test For Independence
image: "/posts/AB_testing.jpg"
tags: [AB Testing, Hypothesis Testing, Chi-Square, Python]
---

In this project, we'll be running an A/B test on grocery retailer campaign data to determine if the quality of promotion mail sent to customers significantly impacted who signed up for a promoted membership. 

We will do this through applying the Chi-Square Test For Independence to measure the significance of the difference in signups between 2 groups of customers.

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

The Chi-Square Test For Independence will be applied to compare the **signup rates** of two distinct groups from our *campaign_data* client database:
    * customers who received cheap **Mailer1** 
    * customers who received the higher quality **Mailer2**.

The Hypothesis Test elements are defined as:  
* **Null Hypothesis:** There is no relationship between mailer type and signup rate. They are independent variables and any difference in signup rates are due to chance.  
* **Alternate Hypothesis:** There is a true relationship between mailer type and signup rate. They are not independent.  
* **Acceptance Criteria:** 0.05 (5%)  

Through Pandas, we can aggregate the observed data of *mailer_type* and *signup_flag* into a 2x2 matrix. We'll then feed these observed frequencies to the `chi2_contingency` algorithm provided by the `scipy` library to calculate the expected values, p-values, Degrees of Freedom (dof), and the Chi-Square Statistic.

We'll then take this one step further and find our Critical Value to truly get a grasp on whether we should reject or fail to reject our null hypothesis.

*See more details on the Chi-Square Test, and other related concepts in the *Concept Overview* section*

**Note**: Another viable choice for an approach comparing *rates* would be *Z-Test For Proportions*, which would provide us with the same statistical result as the Chi-Square Test would. However, in this business case, it was determined to be more beneficial to use the Chi-Square Test for analysis.

The Chi-Square Test can be represented using a 2x2 data matrix, making the data easier to visualize and explain to stakeholders. Additionally, if the company ever had interest in expanding this campaign to more than two groups, we could easily adapt the Chi-Squared approach to include new group data, providing the business with a consistent way to measure variable significance. 

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

* **The Null Hypothesis**

    The "Null Hypothesis" is a statistical assumption stating that there is no statistically significant relationship, association, or difference between two outcomes or groups. We run a Hypothesis Test to either reject or support this Null Hypothesis.

* **The Alternate Hypothesis**

    The "Alternate Hypothesis" suggests that there is a significant and measurable relationship, effect, or difference between variables, directly contradicting the Null Hypothesis. When we reject the Null Hypothesis, we accept the Alternate Hypothesis, concluding that the observed relationship is highly unlikely to have occurred by chance alone.

* **The Acceptance Criteria**

    To statistically determine whether to reject the null hypothesis in favor of the alternate, an "Acceptance Criteria" must be specified. The acceptance criteria, also known the Significance Level, is a specified p-value threshold in which we are measuring our Null Hypothesis against. In other words, the set threshold draws a line between what we consider random chance and what we consider a statistically significant result.

    A *p-value*, or probability value, is a calculated value used to determine if the data is extreme enough to reject the null hypothesis. It is a common practice to set the acceptance criteria to 0.05 or 5%.

    * A *low p-value* (≤ 0.05) suggests your results are highly unlikely to have occurred by chance. There is strong evidence to reject the null hypothesis.

    * A *High p-value* (> 0.05) means your results could easily happen under random variation. We would fail to reject the null hypothesis, meaning there isn't enough evidence to prove a true association exists

<br>
#### Chi-Square Test For Independence

The **Chi-Square Test For Independence** is a hypothesis test used to determine whether a significant association exists between two categorical variables. It compares the *observed frequencies* from the actual data points collected from a sample against the *expected frequencies*, the data expected to be seen if the two variables were truly independent.

The *Null Hypothesis* described above is our baseline assumption. It assumes that there is no relationship or difference between the two variables. It asserts that the observed frequencies of data will match the expected frequencies, with any minor difference being the result of random chance.

The Chi-Square Contingency function provides a Chi-Square statistic that can be compared against a calculated *critical value*, in order to reject or fail to reject a null hypothesis.

	* Chi-Square Statistic < Critical Value: We retain the null hypothesis - the observed results could easily happen under random variation.  meaning there isn't enough evidence to prove a true association exists between variables
	* Chi-Square Statistic ≥ Critical Value: We reject the null hypothesis - the observed results are highly unlikely to have occurred by chance providing strong evidence that an association exists between variables

This function also provides a p-value, which can be compared to the chosen acceptance criteria (also known as the significance level, commonly set to 0.05). If the p-value is less than or equal to this acceptance criteria, the null hypothesis is rejected.

___

<br>
# Data Overview & Preparation  <a name="data-overview"></a>

Our table of interest in the grocery client database is the *campaign_data* table. 
This table contains each each unique customer_id, the type of mailer they received, if any, and whether or not the customer signed up for the Delivery Club membership.

To determine whether the fancier Mailer 2 led to a significant difference of people to sign up as opposed to the cheaper Mailer 1, we will first need to exclude the control group from the data by extracting the customers who got either mailer.

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


#### State Hypotheses & Acceptance Criteria For Test

To kick off our Hypothesis Test, we'll need to define our **Null Hypothesis**, our **Alternate Hypothesis**, and our **Acceptance Criteria**. (See more on these terms in the *Concept Overview* section above)

For our Acceptance Criteria, we'll be using the commonly used value of 0.05 (or 5%).

* null_hypothesis: There is no relationship between mailer type and signup rate. They are independent.
* alternate_hypothesis: There is a relationship between mailer type and signup rate. They are not independent.
* acceptance_criteria: 0.05

<br>
#### Calculate Observed Frequencies & Expected Frequencies

As detailed in the *Concept Overview* section above, our **observed frequencies** come directly from the rates per group in our collected data. To get these frequencies, we'll create our 2x2 matrix needed for the Chi-Square approach, using a method called **`crosstab()`**. 

Our observed values come directly from our campaign_data imported above. We are analyzing the impact that mailer_type had on member sign-up rates, so we'll want to pass these data points into the crosstab method.

We can visualize this data in the `DataFrame` below:
```python
observed_vals = pd.crosstab(campaign_data['mailer_type'],campaign_data['signup_flag'])

print(observed_vals)
>>> signup_flag    0    1
>>> mailer_type          
>>> Mailer1      252  123
>>> Mailer2      209  127
```

By running the `crosstab` method, we see:
* For customers who received Mailer 1,
    * 252 customers did not sign up for the promotion
    * 123 customers signed up for the promotion. 
* For customers who received Mailer 2,
    * 209 customers did not sign up for the promotion
    * 127 customers signed up for the promotion   

The Chi-Squared contingency function won't accept Pandas DataFrames, so we'll have to convert the observed values data into an array by using *.values* property for observed_values.

```python
observed_values = pd.crosstab(campaign_data['mailer_type'],campaign_data['signup_flag']).values
print(observed_values)
>>> array([[252, 123],
       [209, 127]])
```

Now that the observed_values are in an array, we can pass the observed_values into our `chi2_contingency` function that we imported with `scipy`.

Running the Chi-Squared function will provide us with the following:
* **Expected values**
* **P-values**
* **Degrees of Freedom (dof)**: used for finding the critical value later
* **Chi2 Statistic** 

We can additionally test the null hypothesis by finding the *critical value* along our Chi-Squared distribution based on our set acceptance criteria and our calculated dof, using the `chi2.ppf` percentage point function from the scipy library.

```python
# run the chi-square test
chi2_statistic, p_value, dof, expected_values = chi2_contingency(observed_values, correction = False)

print(chi2_statistic)
>> 1.94

print(p_value)
>> 0.16

# find the critical value for our test using chi2.ppf
critical_value = chi2.ppf(1 - acceptance_criteria, dof)

print(critical_value)
>> 3.84
```

*Note: The chi2_contingency function accepts a correction parameter. By setting correction = False, we are setting our degrees of freedom to 1, applying Yate's Correction. This is necessary to define as we are comparing 2 group totals against their result in a 2x2 matrix*

!!!
*Note:* When applying the Chi-Square Test above, we use the parameter correction = False which means we are applying what is known as the Yate’s Correction which is applied when your Degrees of Freedom is equal to one. This correction helps to prevent overestimation of statistical significance in this case.
!!!

With that code in place, we have all of the values necessary to analyze the results, assess the null hypothesis, and draw a conclusion.

___

<br>
# Analyzing The Results <a name="chi-square-results"></a>

Based upon the raw observed values from the campaign, we can see that the signup rate for customers receiving Mailer 2 was higher than for the customers receiving Mailer 1:

Mailer 1 (Low Cost): 32.8% signup rate
Mailer 2 (High Cost): 37.8% signup rate

The Chi-Square test gives us further insight into whether this difference in signup rate was truly due to the quality of the mailer, or just due to chance.

Our calculated p-value of 0.16 is greater than our set acceptance criteria of 0.05, meaning that **the difference in signup outcomes between the two mailing groups is not significant.** 

This conclusion is further supported by our Chi-Square statistic of 1.94 being lower than the calculated critical value of 3.84. In both cases, we **retain the null hypothesis** as there is not enough evidence that the signup rates for Mailer 1 and Mailer 2 were significantly different.

___

<br>
# Discussion <a name="discussion"></a>

!!!!
While Mailer 2 saw a higher sign-up rate than Mailer 1 (37.8% vs. 32.8%), the difference was not statistically significant at our 0.05 acceptance criteria threshold. The results of the hypothesis test suggest that the the more expensive mailer didn't truly impact whether a customer signed up or not.

At first glance, our client may have assumed that the quality of expensive Mailer 2 may have been a driving force in signup rate. Without our hypothesis test, the client may have considered sending strictly the fancy Mailers, for their next promotion, losing unneccessary funding. 

Though we've concluded there is no significant difference between signup rates, it is important to note that we've only analyzed a small sample of data from one campaign. The evidence supporting our null hypothesis rejection does not garuntee that the quality in mailer didn't make a difference, our experiment justifies us in advising our client that we should not jump to conclusions just yet on the impact of the mailers. 

Running more A/B tests like this over more data would give us more insight overtime. With more experiments supporting retaining the null hypothesis, we may recommend that for the next promotion, the grocery store only send the cheaper version of the mailers to customers to cut printing costs. 