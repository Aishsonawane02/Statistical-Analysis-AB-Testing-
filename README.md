# Statistical-Analysis-AB-Testing-
Statistical Analysis &amp; A/B Testing using Python (Pandas, SciPy, Statsmodels).
This project performs a full end-to-end A/B testing analysis on a real-world e-commerce/web platform dataset containing nearly 294,478 user records. The goal was to statistically determine whether a newly designed landing page performs better than the existing page in terms of user conversion rates.

The project follows a structured 4-phase analytical pipeline:

Phase 1: Data Cleaning
Raw A/B test data often contains errors. The dataset had two major quality issues:

Mismatched records: 3,893 rows where control group users accidentally saw the new page or treatment users saw the old page — these were identified and removed

Duplicate user IDs: 3,894 duplicate entries that could skew results — removed keeping only the first occurrence

Final clean dataset: 290,584 valid observations ready for analysis


Phase 2: Group Statistics
After cleaning, conversion rates were computed for both groups:

Group	Conversion Rate
Control (old page)	12.04%
Treatment (new page)	11.88%
Uplift	-1.31%
The new page performed slightly worse, but the key question was: Is this difference statistically significant or just random noise?

Phase 3: Hypothesis Testing
Four rigorous statistical tests were applied:

H₀ (Null Hypothesis): The new page does NOT improve conversion rate
H₁ (Alternative): The new page improves conversion rate

Test	Result	p-value	Conclusion
Chi-Square Test	χ² = 1.7036	0.1918	Not Significant
Z-Test for Proportions	z = 1.3109	0.1899	Not Significant
95% Confidence Interval	Control: [11.87–12.21%], Treatment: [11.71–12.05%]	Overlapping	Not Significant
Cohen's d (Effect Size)	d = -0.004864	—	Negligible Effect
All p-values > 0.05 → Fail to reject H₀ across all four tests.

Phase 4: Daily Trend Analysis
Timestamps were parsed and daily conversion rates were grouped by date and group to observe whether conversion trends changed over time for both control and treatment users.

Tools & Libraries
Tool	Purpose
Python	Core programming
Pandas	Data cleaning & grouping
NumPy	Numerical operations
SciPy	Chi-Square test
Statsmodels	Z-test for proportions

Business Recommendations
Based on the statistical results:

Do NOT launch the new page — it performs slightly worse (-1.31%) with no statistical evidence the difference is real

Cost saved — with 145k users tested and no gain, deploying the new page would risk losing 1.31% of conversions with zero upside

Redesign required — the new page needs fundamental improvements, not cosmetic ones

Run longer test —  Cohen's d = 0.005 means even with infinite data, the effect is practically meaningless

Segment the test — check if the new page works better for specific user groups (device type, geography, new vs returning users) before fully discarding it


Future Improvements
Segment-level A/B testing (new vs returning users, device type, geography)

Power analysis for sample size planning

Bootstrap confidence intervals

Interactive Power BI / Tableau dashboard

Author
Aishwarya Sonawane
