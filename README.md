# Predict Customer Personality to Boost Marketing Campaign by Using Machine Learning. 

## Project Background
  This is a mini-project of Rakamin Academy Data Science Bootcamp. My role is a Data Scientist in a company as part of the core Data Science team. My responsibility is to process historical marketing campaign data to improve performance and target the right customers, thus encouraging them to transact on the company's platform. In this mini project, I will learn how to process data, clean it, build machine learning models, and draw conclusions and business insights that can be recommended for the ongoing marketing campaigns.

Dataset: Sales Data Provided by Rakamin Academy. <br>
Tools:
- Python
- Jupyter Notebook

This project is divided into 4 stages:
1. Data Preparation
2. Data Exploratory
3. Data
4. Data

## 1. Data Preparation
### Data Overview
Dataset is consisted of 2240 rows and 30 columns.

**Table 1. Data Pre-Processing Treatment** <br>
**No**  |     **Treatment**      |    **Findings**     |    **Actions**     |
:-----: |    ----------------    |    ------------     |--------------------|
1 | Handling Missing Values | 24 missing values in `Income` | Fill the missing values with median value |
2 | Convert Irrelevant Data Type | `Dt_Customer` datatype is object | `Dt_customer` datatype is changed to Datetime |
3 | Remove Outlier | `Year_Birth` & `Income` have few outliers | Remove outliers with IQR |
4 | Duplicated Values | - | - |

**Table 2. Feature Engineering** <br>
**No**  |     **New Feature**      |    **Method**     |   
:-----: |    ----------------    |    ------------     |
1 | `Age` | (2023 - `Year_Birth`) |
2 | `Age_Category` | `Age` ~ 21-40 : **Adult** , 41-60 : **Middle Aged** , 61-80 : **Old** |
3 | `Total_Children` | `Teenhome` + `Kidhome` |
4 | `Total_Purchases` | `NumDealsPurchases` + `NumWebPurchases` + `NumCatalogPurchases` + `NumStorePurchases` |
5 | `Total_Spend` | `MntCoke` + `MntFruits` + `MntMeatProducts` + `MntFishProducts` + `MntSweetProducts` + `MntGoldProds` |
6 | `Total_Accepted_Campaign` | `AcceptedCmp1` + `AcceptedCmp2` + `AcceptedCmp3` + `AcceptedCmp4` + `AcceptedCmp5` + `Response` |
7 | `Conversion_Rate` | `Total_Purchases` / `NumWebVisitsMonth` |



## Data Exploratory

### Correlation Analysis
<p align="center">
  <img src= "https://github.com/jedijm/Predict-Customer-Personality-to-Boost-Marketing-Campaign/blob/main/asset/heatmap_corr.png"> <br>
Fig 1. Correlation Analysis
</p>

It can be seen there are a few features with high correlation. Total Spend and Income as the highlight, reaching 0.8 positive correlation. Higher `Income` customers have higher `Total Spend`, vice versa for the lower `Income` customers.

### **Conversion Rate Analysis**
<p align="center">
  <img src= "https://github.com/jedijm/Predict-Customer-Personality-to-Boost-Marketing-Campaign/blob/main/asset/reg_plot.png"> <br>
Fig 2. Correlation Plot of Conversion Rate with Each Features
</p>

- It can be seen that there are positive correlation of `Conversion Rate` especially with Income and Total_Spend. The higher `Income` and `Total Spend` of customer, the Conversion Rate is higher also. `Income` and `Total Spend` show financial capacity of customer, higher financial capacity customers have higher `Conversion Rate`. This is an important insight for the marketing to adjust the strategy. They can upsell higher priced items for the high income customers and offer a special discount for the customers with lower income.
- Age does not show high correlation with conversion rate. Conversion Rate is distributed well in every ages, it shows that the age does not significantly effect the conversion rate of customer.

## Clustering Analysis

In order to cluster customers based on the behaviour, K-Means Clustering Analysis is done with the dataset we have processed.

### Determine Number of Clusters (K)
<p align="center">
  <img src= "https://github.com/jedijm/Predict-Customer-Personality-to-Boost-Marketing-Campaign/blob/main/asset/yellowbrick.png"> <br>
Fig 3. Distortion Score Elbow Analysis
</p>
 
### Model Evaluation (Silhouette Score Analysis)
<p align="center">
  <img src= "https://github.com/jedijm/Predict-Customer-Personality-to-Boost-Marketing-Campaign/blob/main/asset/Silhouette.png"> <br>
Fig 4. Silhouette Score Analysis
</p>

Based on the analysis above, the best number of clusters for the customer (K) is 4. Thus, the customer is clustered into 4 groups with each characteristic as below:

### Cluster Distribution and Characteristics
<p align="center">
  <img src= "https://github.com/jedijm/Predict-Customer-Personality-to-Boost-Marketing-Campaign/blob/main/asset/pairplot.png"> <br>
Fig 5. Cluster Distribution
</p>

<p align="center">
  <img src= "https://github.com/jedijm/Predict-Customer-Personality-to-Boost-Marketing-Campaign/blob/main/asset/Table.png"> <br>
Fig 6. Cluster Characteristics
</p>

# Insights

Characteristics of each cluster:
1. Cluster 0:
    - Highest in Recency, Conversion Rate & Total Purchases
    - Second highest in Income and Total Spend
3. Cluster 1:
    - Biggest cluster
    - Averagely has Children
    - Least in Income, Total Purchases, Total Accepted Campaign and Conversion Rate
4. Cluster 2:
    - Averagely the oldest amongst other cluster.
    - Averagely has Children
    - Second highest in Total Purchases, Total Accepted Campaign
5. Cluster 3:
    - Smallest cluster
    - Highest in Income, Total Spend, Total Accepted Campaign
    - Second Highest in Conversion Rate
    
It can be concluded as:

Cluster 0 -> High Active Transaction Customers <br>
Cluster 1 -> Low Transaction Customers <br>
Cluster 2 -> Moderate Customers <br>
Cluster 3 -> Potential High Transaction Customers <br>

# Recommendation

1. Cluster 0:
    - Upsell higher priced item.
    - Offer loyalty program to maintain transaction.
2. Cluster 1:
    - Do like & dislike product category survey because it is the biggest cluster.
    - Offer discounts periodically.
3. Cluster 2:
    - Give more campaign based on each customer product interest.
    - Give family transaction promo due to it averaged highest in age and have children.
4. Cluster 3:
    - Offer loyalty program for special discounts.
    - Upsell higher priced item.
    - Give more campaign based on each customer interests.
    
