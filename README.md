# Part 2: KPI Framework, Experiment Analysis & Recommendation

## Business Context

A subscription-based digital product company tested a new onboarding and activation campaign to improve user conversion and early engagement.

Users were divided into two groups:

* **Control Group** – Existing onboarding experience
* **Treatment Group** – New onboarding and activation campaign

The purpose of the experiment was to determine whether the new onboarding experience should be launched based on its impact on user conversion and overall business performance.

## Dataset Description

**Dataset File:** `data/campaign_experiment_data.xlsx`

The dataset contains user-level experiment data collected during the onboarding campaign test.

### Dataset Overview

Item                         : Details               

Original Records             : 1,408                 
Final Records After Cleaning : 1,400                 
Number of Columns            : 16                    
Experiment Groups            : Control and Treatment 

### Key Columns

 Column                :  Description                           

 user_id               : Unique user identifier                
 experiment_group      : Control or Treatment                  
 signup_date           : User signup date                      
 region                : User region                           
 device_type           : Desktop, Mobile, or Tablet            
 traffic_source        : User acquisition source               
 plan_type             : Free, Basic, or Premium               
 visited_landing_page  : Whether user visited landing page     
 started_trial         : Whether user started a trial          
 completed_onboarding  : Whether user completed onboarding     
 converted_to_paid     : Whether user became a paying customer 
 revenue_30d           : Revenue generated within 30 days      
 support_tickets_30d   : Number of support tickets raised      
 refund_requested      : Whether a refund was requested        
 engagement_score      : User engagement score                 
 days_to_convert       : Days required to convert              

---

## Business Problem Statement

The company needs to determine whether the new onboarding campaign should replace the existing onboarding experience.

The decision impacts future users, product teams, marketing teams, customer support teams, and overall business performance.

The campaign should improve user conversion while avoiding negative effects such as increased refunds, lower revenue quality, or excessive support requests.

The final recommendation should be based on experiment results rather than assumptions.

## North Star Metric

### Selected Metric: Paid Conversion Rate

Paid Conversion Rate was selected as the North Star Metric because it directly measures whether users become paying customers.

For a subscription-based business, increasing the number of paying users is one of the most important indicators of growth.

### Why This Metric Was Selected

* Directly measures business success
* Closely connected to revenue generation
* Reflects the final outcome of the onboarding journey
* Easy to compare between experiment groups

### Supporting Metrics

The following metrics were treated as supporting metrics:

* Landing Page Visit Rate
* Trial Start Rate
* Onboarding Completion Rate
* Engagement Score
* Revenue Metrics

These metrics help explain user behaviour but are not the primary success measure.

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

`outputs/kpi_tree.png`

## Experiment Analysis Approach

The following steps were completed before analysis:

1. Reviewed the dataset for missing values.
2. Checked Control and Treatment group counts.
3. Identified duplicate user records.
4. Validated binary fields.
5. Reviewed revenue outliers.
6. Verified segment distribution across groups.
7. Prepared a cleaned dataset for analysis.
8. Calculated experiment metrics for both groups.
9. Performed segment-level analysis.
10. Conducted hypothesis testing using the North Star Metric.

### Data Preparation Summary

 Check                           : Result                       

 Duplicate User Records          : 8 duplicate records removed  
 Missing device_type values      : 18 replaced with "Unknown"   
 Missing traffic_source values   : 24 replaced with "Unknown"   
 Missing engagement_score values : 14 filled using group median 
 Revenue Outliers                : 4 identified and retained    
 Binary Value Issues             : None found                   
 Funnel Logic Issues             : None found                   

Detailed analysis is available in:

`analysis/experiment_analysis.xlsx`

## Experiment Summary

### Overall Results

 Metric                    |  Control  |  Treatment 

 User Count                |  690      |  710       
 Landing Page Visit Rate   |  63.62%   |  72.39%    
 Trial Start Rate          |  25.07%   |  29.01%    
 Onboarding Completion Rate|  15.65%   |  21.13%    
 Paid Conversion Rate      |  3.19%    |  7.04%     
 Avg Revenue Per User      |  51.97    |  54.25     
 Avg Engagement Score      |  57.03    |  62.94     
 Avg Days to Convert       |  8.86 Days | 6.40 Days 

The Treatment group performed better than the Control group across most key metrics and achieved a substantially higher Paid Conversion Rate.

## Hypothesis Test Summary

A One-Tailed Two-Proportion Z-Test was performed using Paid Conversion Rate.

### Test Inputs

 Group   |   Users | Converted Users |  Conversion Rate 

 Control  |  690   | 22              | 3.19%           
 Treatment|  710   |50               |7.04%           

### Test Results

 Item               | Value                            
 
 Test Type          | One-Tailed Two-Proportion Z-Test 
 Significance Level |0.05                             
 Z-Statistic        |  3.26                             
 P-Value            | 0.0005                           
 Decision           |Reject Null Hypothesis           

### Interpretation

The p-value was below the significance level of 0.05.

This indicates that the difference in Paid Conversion Rate between the Control and Treatment groups was statistically significant.

The analysis provides evidence that the new onboarding campaign improved conversion performance.

Detailed calculations are available in:
`analysis/hypothesis_test_notes.md`

## Guardrail Metrics Considered

The recommendation was not based only on conversion performance.

Several guardrail metrics were reviewed.

 Metric                     |  Control  |  Treatment | Observation                              
  
 Refund Rate                | 0.00%     | 0.42%       |Small increase observed                  
 Support Ticket Rate        |14.78%     | 24.79%     |Increased noticeably                     
 Revenue per Converted User | 1630.10   | 770.41     |Lower average revenue per converted user 
 Avg Engagement Score       | 57.03     | 62.94      |Improved                                 
 Avg Days to Convert        | 8.86 Days | 6.40 Days  |Improved                                 

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
The largest concern identified during the experiment was the increase in Support Ticket Rate.

## Final Recommendation

### Recommendation: Launch Only for Selected Segments

The Treatment group achieved a significantly higher Paid Conversion Rate than the Control group and showed improvements across most funnel metrics.

However, Support Ticket Rate increased noticeably and Social traffic users performed worse than the Control group.

Based on these findings, the campaign should first be launched to high-performing segments such as:

* Referral Traffic Users
* Free Plan Users
* Mobile Users

Social traffic users should remain on the existing onboarding experience until additional analysis is completed.
Further monitoring should be conducted before considering a full rollout.
Detailed recommendations are available in:

`outputs/recommendation_memo.md`

## Assumptions and Limitations

### Assumptions

* Users were assigned to either the Control or Treatment group before the experiment began.
* User activity was recorded correctly in the dataset.
* The experiment period was sufficient to capture conversion behaviour.

### Limitations

* Support Ticket Rate increased in the Treatment group.
* Revenue per Converted User was lower in the Treatment group.
* Social traffic users responded less positively to the new onboarding experience.
* Results should continue to be monitored after rollout.
* Converted user counts are small (Control = 22, Treatment = 50). While results are statistically significant, findings should be validated at larger scale.
* Minor group size imbalance in Social traffic (73 Control vs 56 Treatment) may affect segment-level conclusions for that source.

## Screenshots Included

summary_metrics.png        : Overall experiment results and metric comparison                       
hypothesis_test_output.png : Hypothesis test calculations and final decision                        
kpi_tree_preview.png       : KPI tree showing North Star metric, KPI drivers, and guardrail metrics


