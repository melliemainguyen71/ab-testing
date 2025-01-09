# Analysis of AB testing result - The impact of the variation on revenue

## Introduction
This A/B test evaluates the impact of a new feature on user revenue. This test is implemented by randomly assigning users into two groups: Control (users who use the orginal design) and Test (users who use the new feature). If the new feature has an impact on user revenue, there will be a significant difference in the average revenue between the two groups.

## A/B Testing summary
#### 1. Test design
The original design and the new feature are randomly assigned to a sample of 19561 users. The observations only include users who completed purchase. Based on the given data, we have:
- 10041 users using original design 
- 9547 users using the new feature 

#### 2. Exploratory Data Analysis (EDA)
This part examines descriptive statistics of the dataset and suggests pre-process to satisfy conditions of A/B testing. These conditions are
- identical independent distribution: satisfied by the nature of sampling approach
- sufficient sample size: satisfied by the nature of test design
- normal distribution: checked by histogram and box-plot
- homogeneity of variance: checked by comparing standard deviation

The EDA shows that revenue data is highly right-skewed which deviates from the normal distribution. This implies that the data needs transforming in further analysis.

Furthermore, Control group has a higher variance than that of the Test group. This difference is caused by the existence of outliers in Control group.

#### 3. Statistical Analysis
Based on the EDA, the revenue data is log-transformed to address the right skewness. Then, a linear regression model is applied to formally test the difference in revenue between the two groups. The regression analysis is based on the log-transformed revenue, thus, the model coefficient will be interpreted as percentage of change in revenue.

## Result summary
The A/B testing result shows that the average revenue of the Test group is 0.71% higher than that of the Control group and this difference is statistically significant. This result confirms that implementation of the new feature might bring about an increase in revenue, however, the magnitude is relatively small in practical terms. 

It is noticeable that the model's R-squared is close to 0. This implies that the group assignment does not explain the variance in revenue. However, our main objective is to confirm the difference in revenue between two groups which is captured by the model coefficient and its p-value. Therefore, low value of R-squared is not the main concern of this analysis and can be addressed by including more variables.

This A/B Test can be further enhanced by incorporating more covariates/ confounding variables. In reality, the difference in revenue might be the result of other factors such as demographic or purchasing behaviours.

The A/B Testing process is detailed as followed.
