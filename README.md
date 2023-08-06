# Predict Customer Personality to Boost Marketing Campaign by Using Machine Learning. 

## Project Background
  This is a mini-project of Rakamin Academy Data Science Bootcamp. My role is a Data Scientist in a company as part of the core Data Science team. My responsibility is to process historical marketing campaign data to improve performance and target the right customers, thus encouraging them to transact on the company's platform. In this mini project, I will learn how to process data, clean it, build machine learning models, and draw conclusions and business insights that can be recommended for the ongoing marketing campaigns.

Dataset: Sales Data Provided by Rakamin Academy. <br>
Tools:
- Python
- Jupyter Notebook

This project is divided into 4 stages:
1. Data Preparation
2. Data
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





