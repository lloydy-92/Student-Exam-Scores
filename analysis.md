# Which variable has the greasest correlation and causal link with a student's exam score?
### Goal: Plot control variables against outcome variable, as well peform statistical testing techniques to determine correlation and causal link significance between the control variables (hours studied, hours slept, class attendance percent, previous exam score).

## Scatter plots to visualise correlation
<img width="1990" height="396" alt="image" src="https://github.com/user-attachments/assets/930eeb9b-e657-4c6a-aff1-2805fbddd44e" /><br/>
Just by looking, it's clear to see that hours_studied is the only variable to have a significant correlation with exam_score, visually speaking. To confirm suspicions, multiple Pearson Correlation Analyses will be run on each control variable against exam_score to compute which one has the strongest and most significant correlation.

## Pearson Correlation statistical significance test

**Table 1: Pairwise Pearson correlations (control variable vs outcome (exam_score))**
| variable | pearson_r | abs_r | pearson_pvalue | Statistically significant? |
|----------|-----------|-------|----------------|----------------------------|
| hours_studied |	0.777604 | 0.777604 |	9.123710e-42 | True |
| previous_scores |	0.429550 | 0.429550 |	2.193865e-10 | True |
| attendance_percent | 0.223812 |	0.223812 | 1.443301e-03 |	True |
| sleep_hours |	0.188608 | 0.188608 |	7.480595e-03 | True |<br/>

It would appear that indeed actually all control variables are have a statistically significant positive correlation with exam_score, but hours_studied has by far the most significant link, as expected from our visual observations. hours_studied also has by far the strongest correlation, with an r value of about 0.78, compared to sleep_hours (the weakest correlation) with just r ~ 0.19. However, as the saying goes, **Correlation does not imply causation**. Which is why, a Simple Linear Regression model will also be fitted to the variables to test for causal evidence between the control variable and exam_score.<br/><br/>

## Simple Linear Regression model for causal inference

**Table 2: Simple OLS regression results (each control individually predicting outcome (exam_score))**
| variable | coef_unstd |	standardised_beta |	std_err |	t_value |	p_value |	r_squared |	Statistically significant? |
|----------|------------|-------------------|---------|---------|---------|-----------|----------------------------|
| hours_studied |	1.640097 | 0.777604 |	0.094245 | 17.402424 | 9.123710e-42 |	0.604668 | True |
| previous_scores |	0.186667 | 0.429550 |	0.027889 | 6.693258 |	2.193865e-10 | 0.184513 |	True |
| attendance_percent | 0.106911 |	0.223812 | 0.033086 |	3.231280 | 1.443301e-03 |	0.050092 | True |
| sleep_hours |	0.857536 | 0.188608 |	0.317317 | 2.702459 |	7.480595e-03 | 0.035573 |	True |<br/>

Looking at the above table reveals some interesting conclusions. For example, not only were all control variables significantly correlated to exam_score, but they are all significantly causally linked to it too. Each control variable shares the exact same p_value between the Simple Linear Regression model and the Pearson Correlation test, as well as the same correlation/causality strength coefficient (abs_r and standardised_beta respectively). This model also highlights the importance of normalising data as, without it, it would have been implied that sleep_hours has the second strongest causal link coefficient with exam_score (coef_unstd ~ 0.86), when in actuality it has the weakest, as shown by its standardised_beta and std_err value being the smallest (~ 0.19) and largest (~ 0.32) respectively. Whilst the majority of the evidence from the above table points to hours_studied have the strongest and most significant causal link with exam_score (with it having the highest standardised_beta, t_value, and r_squared value, as well as the smallest p_value), it has the second largest standard error std_err value of ~ 0.094, meaning that its coef_unstd (and so in turn its standardised_beta value too) was estimated with second least amount of precision out of all the control variables.

## Summary and Final Conclusion
Most strongly correlated variable (by |r|): hours_studied (r = 0.7776)<br/>
Most statistically significant simple regression predictor (by p-value): hours_studied (p = 9.124e-42)


As seen from the results, whilst all control variables have a positive and significant correlation and causal link with exam_score, hours_studied is by far the strongest predictor. It has highest abs_r or standardised_beta value, meaning it has the biggest effect on exam_score, the highest r_squared, meaning it accounts for the highest variance in exam_score (about 60%) out of all the control variables, and the lowest p_value, meaning it has the most significant and reliable relationship with exam_score.
In summary, hours_studied contributes more than all the other control variables combined. It is important to note however though that the other control variables, particulary previous_scores also has a strong and significant correlation/causal relationship with exam_score, however they are clearly just secondary influences compared to hours_studied.

