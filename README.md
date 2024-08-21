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
Checking the contents of the data
head(Bank)
```
##      Attrition_Flag Customer_Age Gender Dependent_count Education_Level
## 1 Existing Customer           45      M               3     High School
## 2 Existing Customer           49      F               5        Graduate
## 3 Existing Customer           51      M               3        Graduate
## 4 Existing Customer           40      F               4     High School
## 5 Existing Customer           40      M               3      Uneducated
## 6 Existing Customer           44      M               2        Graduate
##   Marital_Status Income_Category Card_Category Credit_Limit Total_Revolving_Bal
## 1        Married     $60K - $80K          Blue        12691                 777
## 2         Single  Less than $40K          Blue         8256                 864
## 3        Married    $80K - $120K          Blue         3418                   0
## 4        Unknown  Less than $40K          Blue         3313                2517
## 5        Married     $60K - $80K          Blue         4716                   0
## 6        Married     $40K - $60K          Blue         4010                1247
##   Total_Trans_Amt
## 1            1144
## 2            1291
## 3            1887
## 4            1171
## 5             816
## 6            1088


