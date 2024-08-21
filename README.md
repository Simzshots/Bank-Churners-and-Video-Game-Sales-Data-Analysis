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



