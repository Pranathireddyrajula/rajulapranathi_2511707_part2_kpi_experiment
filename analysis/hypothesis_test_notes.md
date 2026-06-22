# Hypothesis Test Notes

## Metric Being Tested

Paid Conversion Rate : the percentage of users who converted to a paid subscription within 30 days.

This metric was selected as the North Star Metric because the main objective of the experiment is to increase the number of paying customers.

## Reason for Choosing This Metric

Paid Conversion Rate was selected because it directly measures whether the new onboarding campaign helped users become paying customers.
Other metrics such as landing page visits, trial starts, onboarding completions, and engagement scores provide useful information about user behavior, but paid conversion is the final business outcome that the company wants to improve.
For a subscription-based business, an increase in paid conversions has a direct impact on revenue growth.

## Hypotheses

### Null Hypothesis (H₀)

There is no difference in Paid Conversion Rate between the Control group and the Treatment group.
H₀: Conversion Rate (Treatment) = Conversion Rate (Control)

### Alternative Hypothesis (H₁)

The Treatment group has a higher Paid Conversion Rate than the Control group.
H₁: Conversion Rate (Treatment) > Conversion Rate (Control)

## Test Type

A one-tailed test was used because the business objective is to determine whether the new onboarding campaign improves conversion performance.

The company is interested in testing for an increase in conversion rate rather than any difference in either direction.

## Significance Level

α = 0.05 (5%)**

This means the test accepts a 5% risk of concluding that the campaign improved conversions when the observed improvement occurred by chance.

## Test Method

A Two-Proportion Z-Test was used.

This test is appropriate because:

* The outcome is binary (converted or not converted)
* Two independent groups are being compared
* Both groups contain a large number of users
* The objective is to compare conversion rates between groups

### Test Inputs Summary
The experiment compared Paid Conversion Rate between the Control and Treatment groups.

Input            Control  Treatment 

Total Users (n) : 690      710       
Converted Users : 22       50        
Conversion Rate : 3.19%    7.04%     

## Decision Rule

* If p-value < 0.05, reject the Null Hypothesis.
* If p-value ≥ 0.05, fail to reject the Null Hypothesis.

A statistically significant result suggests that the observed improvement is unlikely to be caused by random variation alone.

## Test Ouputs

Output                    Value  

Control Conversion Rate   : 3.19%                   
Treatment Conversion Rate :7.04%                   
Absolute Lift             : +3.85 Percentage Points 
Z-Statistic               : 3.26                    
P-Value                   : 0.0005                  
Decision                  : Reject Null Hypothesis  

## Business Interpretation

A Two-Proportion Z-Test was conducted to compare the Paid Conversion Rate between the Control and Treatment groups.
The Control group achieved a conversion rate of 3.19%, while the Treatment group achieved a conversion rate of 7.04%.
The calculated p-value was 0.0005, which is lower than the significance level of 0.05.
Based on this result, the Null Hypothesis was rejected. The analysis provides strong evidence that the new onboarding campaign improved the Paid Conversion Rate compared to the existing onboarding experience.
The Treatment group more than doubled the conversion rate, indicating that the new onboarding process was effective at helping users become paying customers.
However, the experiment also showed an increase in refund rate and support ticket rate. These guardrail metrics should be reviewed before making a final rollout decision.


