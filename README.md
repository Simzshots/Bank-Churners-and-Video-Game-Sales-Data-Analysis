# Crime-Analysis-In-Derbyshire

## INTRODUCTION
In the realm of banking, keeping customers satisfied and preventing them from leaving is crucial. This report dives into a dataset focused on customers who have stopped using the credit card services of a bank. The goal is to not only predict potential churn but also understand the factors that contribute to it, using a mix of predictive modelling and statistical methods.
Also, comprehending sales trends and industry influencers is crucial for publishers and developers alike in the ever-changing video game market. An in-depth analysis of a video game sales dataset is also conducted in this research, including a wide range of factors including sales in North America, Europe, and worldwide markets as well as platform, genre, publisher, and more.

## BANK CHURNERS DATASET OVERVIEW:
The dataset contains a bunch of information about customers, including their age, gender, marital status, credit limit, and more. I am digging into this data to figure out why customers decide to stop using their credit card services. This report is structured to guide you through my journey. I start by looking at the big picture through data exploration. Then, I’ll build a tool to predict potential churn. Simultaneously, I’ll use simple statistical tests to uncover more insights about why customers might be leaving.
I aim to provide the bank’s management with clear and practical information, helping them make informed decisions to improve customer satisfaction and retention.
The dataset is a bank dataset which contains information about customers of a bank, including their age, gender, marital status, credit limit, and more as well as their attrition status. The data set has 9 variables, and 10,127 observations so parametric tests would be used to investigate the dataset without normality checks because the sample size is large (n>30). I am digging into this data to determine why customers stop using their credit card services.

_Importing the Bank Churners dataset (Dataset 1)_

Note: The dataset was cleaned by removing not needed columns using Excel.

```r
library(readr)
Bank <- read.csv("BankChurners.csv")
#Checking the contents of the data
head(Bank)
```

| Attrition_Flag     | Customer_Age | Gender | Dependent_count | Education_Level | Marital_Status | Income_Category | Card_Category | Credit_Limit | Total_Revolving_Bal | Total_Trans_Amt |
|--------------------|--------------|--------|-----------------|-----------------|----------------|-----------------|---------------|--------------|---------------------|-----------------|
| Existing Customer  | 45           | M      | 3               | High School     | Married        | $60K - $80K     | Blue          | 12691        | 777                 | 1144            |
| Existing Customer  | 49           | F      | 5               | Graduate        | Single         | Less than $40K  | Blue          | 8256         | 864                 | 1291            |
| Existing Customer  | 51           | M      | 3               | Graduate        | Married        | $80K - $120K    | Blue          | 3418         | 0                   | 1887            |
| Existing Customer  | 40           | F      | 4               | High School     | Unknown        | Less than $40K  | Blue          | 3313         | 2517                | 1171            |
| Existing Customer  | 40           | M      | 3               | Uneducated      | Married        | $60K - $80K     | Blue          | 4716         | 0                   | 816             |
| Existing Customer  | 44           | M      | 2               | Graduate        | Married        | $40K - $60K     | Blue          | 4010         | 1247                | 1088            |

## SUMMARY OF THE DATA SET

```r
summary(Bank)
```

| Attrition_Flag    | Customer_Age | Gender | Dependent_count | Education_Level | Marital_Status | Income_Category  | Card_Category | Credit_Limit | Total_Revolving_Bal | Total_Trans_Amt |
|-------------------|--------------|--------|-----------------|-----------------|----------------|------------------|---------------|--------------|---------------------|-----------------|
| Existing Customer | 45           | M      | 3               | High School     | Married        | $60K - $80K      | Blue          | 12691        | 777                 | 1144            |
| Existing Customer | 49           | F      | 5               | Graduate        | Single         | Less than $40K   | Blue          | 8256         | 864                 | 1291            |
| Existing Customer | 51           | M      | 3               | Graduate        | Married        | $80K - $120K     | Blue          | 3418         | 0                   | 1887            |
| Existing Customer | 40           | F      | 4               | High School     | Unknown        | Less than $40K   | Blue          | 3313         | 2517                | 1171            |
| Existing Customer | 40           | M      | 3               | Uneducated      | Married        | $60K - $80K      | Blue          | 4716         | 0                   | 816             |
| Existing Customer | 44           | M      | 2               | Graduate        | Married        | $40K - $60K      | Blue          | 4010         | 1247                | 1088            |

| Variable            | Length | Min   | 1st Qu. | Median | Mean  | 3rd Qu. | Max   | Class   | Mode           |
|---------------------|--------|-------|---------|--------|-------|---------|-------|---------|----------------|
| Attrition_Flag      | 10127  |       |         |        |       |         |       | character | character    |
| Customer_Age        | 10127  | 26.00 | 41.00   | 46.00  | 46.33 | 52.00   | 73.00 | character | character    |
| Gender              | 10127  |       |         |        |       |         |       | character | character    |
| Dependent_count     | 10127  | 0.000 | 1.000   | 2.000  | 2.346 | 3.000   | 5.000 | character | character    |
| Education_Level     | 10127  |       |         |        |       |         |       | character | character    |
| Marital_Status      | 10127  |       |         |        |       |         |       | character | character    |
| Income_Category     | 10127  |       |         |        |       |         |       | character | character    |
| Card_Category       | 10127  |       |         |        |       |         |       | character | character    |
| Credit_Limit        | 10127  | 1438  | 2555    | 4549   | 8632  | 11068   | 34516 | numeric  | numeric       |
| Total_Revolving_Bal | 10127  | 0     | 359     | 1276   | 1163  | 1784    | 2517  | numeric  | numeric       |
| Total_Trans_Amt     | 10127  | 510   | 2156    | 3899   | 4404  | 4741    | 18484 | numeric  | numeric       |

The data set has no missing values with 11 variables and 10,127 observations so parametric tests would be used to investigate the dataset without normality checks because the sample size is large (n>30) and a Shapiro Test will not work because the sample size is >3,000.

## ONE SAMPLE T-TEST
*PROBLEM STATEMENT*: The bank wants to know if the average age of their clientele is 45.
*EXPLORATORY DATA ANALYSIS*: Using a histogram to investigate the frequency of customer ages.


*Histogram*
```r
hist(Bank$Customer_Age,xlab = "Age", ylab ="Frequency", main = "Histogram of Customer Ages", col = "blue")
```
![Histogram](images/1.png)
_Inference_: From the histogram, the majority of the clients are around 40-50 years old.

*Density Plot and Boxplot*
```r
plot(density(Bank$Customer_Age), main = "Density of Age Spread", col="red")
```
![Density Plot](images/2.png)

```r
boxplot(Bank$Customer_Age, main = "Boxplot of Customers' Age", col = "red")
```
![Box Plot](images/3.png)

_AIM_: I aim to use a one sample t-test to see if the mean customer age is statistically different from 45 at the 95% confidence interval.
_ASSUMPTIONS_:
-  *Null Hypothesis (H0)*: The average customer age is equal to 45.
-  *Alternate Hypothesis (H1)*: The average customer age is not equal to 45.

```r
t.test(Bank$Customer_Age, mu=45)
```

*Output*
_data:  Bank$Customer_Age
t = 16.644, df = 10126, p-value < 2.2e-16
alternative hypothesis: true mean is not equal to 45
95 percent confidence interval:
  46.16980 46.48212
sample estimates:
  mean of x 
  46.32596_

_RESULTS_: After conducting the T-test, the t-statistic was 16.644 with a 95% confidence interval of 46.16980 to 46.48212 and the p-value was < 2.2e-16.
_Inference_: Since the t-statistic is not in the confidence interval and the p-value is less than the 0.05 significance level, I reject the null hypothesis and accept the alternate hypothesis that the average customer age is not equal to 45.

## WELCH TWO SAMPLE T-TEST
*PROBLEM STATEMENT*: In exploring the credit dynamics within the customer base, a pertinent question arises: Do the credit limits of male and female customers differ significantly?
*EXPLORATORY DATA ANALYSIS*: Using a t-test to check if the credit limit of customers with respect to their genders are equal. Shapiro test failed to work because the sample size is too large (>3,000). To visualize the distributions of the credit limit of each gender and compare, box plots would be used.

```r
boxplot(Credit_Limit ~ Gender, data = Bank, main = "Credit Limit by Gender", col = c("pink","skyblue"))
```
![Box Plot](images/4.png)

```r
bartlett.test(Bank$Credit_Limit ~ Bank$Gender) 
```

*Output*
_Bartlett test of homogeneity of variances
 data:  Bank$Credit_Limit by Bank$Gender
 Bartlett's K-squared = 2393.8, df = 1, p-value < 2.2e-16_

_Inference_: From the box plots, it is noticeable that the credit limit of the female gender has some outliers which could affect the mean and the medians of the credit limits by gender are not equal which could imply that the means are not equal and they have unequal variances. But a parametric t-test will be used to further investigate the claim gotten from the box plots. Because the sample is large, i.e n>30 there would be no need to test normality before the t-test. Also, the Bartlett test shows that they have unequal variances.

_AIM_: I will be carrying out a two-sample t-test to check if the credit limits across both genders are equal at the 95% confidence interval.
_ASSUMPTIONS_:
-  *Null Hypothesis (H0)*: The credit limits of each gender are equal.
-  *Alternate Hypothesis (H1)*: The credit limits of each gender are not equal.

```r
t.test(Bank$Credit_Limit ~ Bank$Gender, conf.level = 0.95)
```

*Output*
_Welch Two Sample t-test 
 data:  Bank$Credit_Limit by Bank$Gender
 t = -45.052, df = 6773.7, p-value < 2.2e-16
 alternative hypothesis: true difference in means between group F and group M is not equal to 0
 95 percent confidence interval:
  -7995.201 -7328.441
 sample estimates:
 mean in group F mean in group M 
        5023.854       12685.675_

_RESULTS_: After conducting the T-test, the t-statistic was -45.052 with a 95% confidence interval of -7995.201 to 7328.441 and the p-value was < 2.2e-16.
_Inference_: Since the t statistic does not fall inside the confidence interval and the p value is way less than 0.05, we reject the null hypothesis that says the credit limit of customers with respect to their genders are equal.

## ANOVA TEST
*PROBLEM STATEMENT*: In delving into the financial dynamics within the bank’s customer base, a critical inquiry emerges: Are the credit limits uniform across distinct card categories?
*EXPLORATORY DATA ANALYSIS*: Now, before using an ANOVA Test to check if the credit limit of the type of cards are equal, box plots would be used to visualize the distributions of the credit limits of the different card categories.
```r
boxplot(Credit_Limit ~ Card_Category , data = Bank, main = "Credit Limit by Card Type", col = c
        ("blue","gold","brown","lightgray"))
library("lattice")
```

![Box Plot](images/5.png)

```r
dotplot(Credit_Limit ~ Card_Category , data = Bank)
```

![Box Plot](images/6.png)

```r
bartlett.test(Credit_Limit ~ Card_Category , data = Bank)
```

*Output*
_Bartlett test of homogeneity of variances 
 data:  Credit_Limit by Card_Category
 Bartlett's K-squared = 68.069, df = 3, p-value = 1.106e-14_

_Inference_: From the box plots, the blue card type has a lot of outliers and the median is quite far from the other card types. The gold and platinum card types have similar medians and the silver card type has a median closer to theirs but far from the median of the blue card type. Overall, from the plots, the card types do not have equal medians which could indicate that their means may not be equal. Also, the Bartlett test shows that they have unequal variances.
_AIM_: I aim to use an ANOVA test to investigate if the credit limits across distinct card categories are equal using the 0.05 significance level.
_ASSUMPTIONS_:
-  _Null Hypothesis (H0)_: The credit limit of each card category is equal.
-  _Alternate Hypothesis (H1)_: The credit limit of each card category is not equal.

```r
oneway.test(Bank$Credit_Limit~Bank$Card_Category, var.equal = FALSE) #Using a Welch's ANOVA because their variances are not equal.
```

*Output*
_One-way analysis of means (not assuming equal variances) 
 data:  Bank$Credit_Limit and Bank$Card_Category
 F = 867.07, num df = 3.000, denom df = 79.821, p-value < 2.2e-16_

_RESULTS_: The F-statistic is 1232.1 and the p-value is < 2.2e-16.
_Inference_: Since the p value is very low (< the significance level 0.05), the null hypothesis that the credit limit of the different types of cards are equal will be rejected. Hence, accepting the alternative hypothesis that the different card categories have different credit limits.













