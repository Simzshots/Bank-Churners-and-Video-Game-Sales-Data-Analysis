# Crime-Analysis-In-Derbyshire

## INTRODUCTION
In the realm of banking, keeping customers satisfied and preventing them from leaving is crucial. This report dives into a dataset focused on customers who have stopped using the credit card services of a bank. The goal is to not only predict potential churn but also understand the factors that contribute to it, using a mix of predictive modelling and statistical methods.
Also, comprehending sales trends and industry influencers is crucial for publishers and developers alike in the ever-changing video game market. An in-depth analysis of a video game sales dataset is also conducted in this research, including a wide range of factors including sales in North America, Europe, and worldwide markets as well as platform, genre, publisher, and more.

## BANK CHURNERS DATASET OVERVIEW:
The dataset contains a bunch of information about customers, including their age, gender, marital status, credit limit, and more. I am digging into this data to figure out why customers decide to stop using their credit card services. This report is structured to guide you through my journey. I start by looking at the big picture through data exploration. Then, I’ll build a tool to predict potential churn. Simultaneously, I’ll use simple statistical tests to uncover more insights about why customers might be leaving.
I aim to provide the bank’s management with clear and practical information, helping them make informed decisions to improve customer satisfaction and retention.
The dataset is a bank dataset which contains information about customers of a bank, including their age, gender, marital status, credit limit, and more as well as their attrition status. The data set has 9 variables, and 10,127 observations so parametric tests would be used to investigate the dataset without normality checks because the sample size is large (n>30). I am digging into this data to determine why customers stop using their credit card services.

Importing the Bank Churners dataset (Dataset 1)

Note: The dataset was cleaned by removing not needed columns using Excel.

library(readr)
Bank <- read.csv("BankChurners.csv")
Checking the contents of the data
head(Bank)
