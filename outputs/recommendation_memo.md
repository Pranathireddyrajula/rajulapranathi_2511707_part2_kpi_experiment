# Recommendation Memo

### Executive Summary

An A/B experiment was conducted to compare the existing onboarding experience (Control group) with a new onboarding and activation campaign (Treatment group).
The main goal of the experiment was to increase the number of users who convert to a paid subscription. The Treatment group achieved a Paid Conversion Rate of 7.04%, compared to 3.19% for the Control group. Statistical testing confirmed that this improvement was significant and unlikely to have occurred by chance.
While the experiment produced strong improvements in conversion, onboarding completion, engagement, and conversion speed, some guardrail metrics showed concerns. In particular, Support Ticket Rate increased noticeably and Social traffic users performed worse than the Control group.

Based on the overall results, the recommendation is to launch the campaign only for selected segments while continuing to monitor risks.

## North Star Metric

### Paid Conversion Rate

Paid Conversion Rate was selected as the North Star Metric because it directly measures whether users become paying customers.

Group      Paid Conversion Rate 

Control    3.19%                
Treatment  7.04%                

The Treatment group more than doubled the conversion rate compared to the Control group.

## KPI Tree Summary

The KPI framework was built around Paid Conversion Rate.

These metrics helped evaluate whether the campaign created any negative side effects while improving conversion.

North Star → Paid Conversion Rate
Primary Driver 1 — Funnel Entry & Reach

* Landing Page Visit Rate 
* Traffic Source Quality 

Primary Driver 2 — Trial Activation

* Trial Start Rate
* Onboarding Completion Rate 

Primary Driver 3 — Conversion Efficiency

* Onboarding-to-Paid Rate 
* Average Days to Convert 

Primary Driver 4 — Engagement Quality 

* Average Engagement Score
* Engagement Consistency Across Segments

Guardrail Metrics (must not be ignored even if North Star improves)

* Refund Rate 
* Support Ticket Rate 
* Average Revenue per Converted User 

## Experiment Result Summary

Metric                     Control    Treatment 

 Landing Page Visit Rate     63.62%     72.39%    
 Trial Start Rate            25.07%     29.01%    
 Onboarding Completion Rate  15.65%     21.13%    
 Paid Conversion Rate        3.19%      7.04%     
 Avg Revenue Per User        51.97      54.25     
 Avg Engagement Score        57.03      62.94     
 Avg Days to Convert         8.86 days  6.40 days 

The Treatment group performed better than the Control group across most funnel metrics. Users completed onboarding more often, converted faster, and showed higher engagement.

## Hypothesis Test Interpretation

A One-Tailed Two-Proportion Z-Test was performed using Paid Conversion Rate as the primary metric.

 Test Output                Value                   

 Control Conversion Rate    3.19%                   
 Treatment Conversion Rate  7.04%                   
 Absolute Lift              +3.85 Percentage Points 
 Z-Statistic                3.26                    
 P-Value                    0.0005                  
 Significance Level          0.05                    
 Decision                   Reject Null Hypothesis  

Since the p-value is lower than 0.05, the Null Hypothesis was rejected.
This means there is enough evidence to conclude that the new onboarding campaign improved Paid Conversion Rate.

## Guardrail Analysis

The recommendation was not based only on conversion improvement. Several guardrail metrics were also reviewed.

Guardrail Metric            Control    Treatment     Observation                              

Refund Rate                 0.00%       0.42%        Small increase observed                   Support Ticket Rate         14.78%      24.79%      Increased noticeably                     Revenue per Converted User  1630.10     770.41       Lower average revenue per converted user 
Avg Engagement Score        57.03       62.94        Improved                                 
Avg Days to Convert         8.86 days   6.40 days    Improved            

**Support ticket rate** is the most serious concern. A 10 percentage point
increase that is consistent across every device type (Desktop +8.94pp, Mobile
+9.97pp, Tablet +10.52pp) indicates a systemic issue with the new onboarding
experience, not a random fluctuation. At full launch scale, this would
significantly increase support team workload with no proportional revenue
justification.

**Revenue per converted user** dropped by 52.7%. While total revenue per user
(including non-converters) increased slightly, the quality of conversions
declined. Treatment is converting more users at lower value — consistent with
the Free plan segment driving the largest lift (+6.23pp). This raises a
concern about conversion intent and long-term retention.

**Refund rate** introduced 3 new refund cases in Treatment versus zero in
Control. Small at current scale but directionally negative, particularly in
the Premium plan segment (0.89%).

The largest concern is the increase in Support Ticket Rate. This suggests that some users may need additional help after completing onboarding.
The decrease in Revenue per Converted User should also be monitored because converted users spent less on average in the Treatment group.

## Segment-Level Insights

### Region

The Treatment group performed better than the Control group in all regions.

* North showed the strongest improvement (+5.41 percentage points)
* West showed the smallest improvement (+1.70 percentage points)

### Device Type

The campaign performed well across all device types.

* Mobile users showed strong improvement
* Tablet users showed the highest conversion lift
* Desktop users also improved compared to Control

### Traffic Source

Results varied across traffic sources.

* Referral traffic showed the strongest improvement (+8.52 percentage points)
* Organic, Email, and Paid Search users improved
* Social traffic users performed worse than the Control group (-1.69 percentage points)

### Plan Type

* Free plan users showed the largest improvement (+6.23 percentage points)
* Premium users also improved
* Basic plan users showed very little change

## Final Recommendation

### Recommendation: Launch Only for Selected Segments

The experiment successfully achieved its main objective of improving Paid Conversion Rate.

However, the increase in Support Ticket Rate and the weaker performance of Social traffic users suggest that a full rollout may be premature.
The campaign should first be launched to the segments where it performed strongly, including:

* Referral Traffic Users
* Free Plan Users
* Mobile Users

Social traffic users should remain on the existing onboarding experience until further investigation is completed.
This approach allows the company to benefit from the improved conversion performance while reducing risk.

## Risks and Limitations

* Support Ticket Rate increased in the Treatment group.
* Revenue per Converted User decreased compared to the Control group.
* Social traffic users showed lower conversion performance.
* Additional monitoring is required before considering a full rollout.
* Converted user counts are small (Control = 22, Treatment = 50). Results are statistically significant but should be validated at larger scale before permanent full launch.
* Minor group size imbalance in Social traffic segment (73 Control vs 56 Treatment) may affect conclusions for that source.

## Next Steps

1. Launch the campaign for high-performing segments.
2. Review the reasons behind the increase in support tickets.
3. Investigate why Social traffic users responded negatively.
4. Continue monitoring refund and revenue metrics.
5. Conduct a follow-up experiment after improvements are made.
6. Reassess the rollout decision using the new results.

## Conclusion

The new onboarding campaign improved user conversion, engagement, and onboarding performance. Although some risks were identified, the overall results were positive. A targeted rollout to the best-performing segments is recommended while continuing to monitor guardrail metrics and user feedback.
