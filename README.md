# LITA_CAPSTONE_PROJECT
Here, I documented my final project while learning Data Analysis with the Incubator Hub.

## Project Title: Customer Data Analysis

### Table_of_content

[Project Overview](#project-overview) 

[Data Source](data-source)

[Tools Used](tools-used)

[Data Cleaning and Preparation](data-cleaning-and-preparation)

[Project Structure](project-structure)

[Exploratory Data Analysis](exploratory-data-analysis)

[Data Analysis](data-analysis)

[Data Visualization](data-visualization)

[Recommendations](recommendations)

## Project Overview
---
This Data Analysis project aims to generate insights into the customer performance regarding subscription for a certain service in the basic, standard, and premium subscription types and from 2022 to 2024. By analyzing the variuos parameters presented in the document file, I have gathered some insights to help the company involved to have a general overview of how well their service performed among their customers. I have also used the information obtained to tell compelling stories around the data presented. 


### Data Source
---
The data was obtained from the Learning Managagement System (LMS) Canvas platform set up by the organizers, the Incubator Hub. LITA Capstone Dataset; CustomerData.  

### Tools Used
---
For this project, I made use of three different softwares; Microsoft Excel [Download Here](https://www.microsoft.com), Microsoft SQL, and Microsoft PowerBI; all of which can be obtained from the Microsoft Store.
- Microsoft Excel was used for data cleaning, analysis, and visualization
- SQL-Structured Query Language for querying of data 
- Power BI for analysis and visualization.
- GitHub for portfolio building

### Data Cleaning and Preparation
---
After the file was obtained, I performed the following actions;
- Data loading and inspection
- Removal of duplicates
- Data formatting

### Exploratory Data AnalysiS
---
Exploratory data analysis invlolved exploring the data to answer some questions about the data such as; 
- The product, region, and months with the highest sales
- The product, region, and months with the highest revenue
- Average sales per product

### Data Analysis
---
1. Microsoft Excel
In Microsoft Excel, a revenue column was created, which was calculated as Unit Price*Quantity, while Total Sales was obtained as Total Sales = Total Quantity Sold = Unit sold.
After which Pivot table was used to summarise the data, and excel funtions used to calculate average sales per product and total revenue by region.
2. SQL
   Queries were generated in SQL to carry out some calculations and analysis.
```SQL
--FOR CUSTOMER DATA---
---the total number of customers from each region---
SELECT Region, COUNT (CustomerID)
AS Total_No_of_Customers
FROM [dbo].[LITA Capstone_Customer Data]
GROUP BY Region

select * from [dbo].[LITA Capstone_Customer Data]

---most popular subscription type by the number of customers---
SELECT SubscriptionType, COUNT (CustomerID)
AS No_of_Customers
FROM [dbo].[LITA Capstone_Customer Data]
GROUP BY SubscriptionType

---customers who canceled their subscription within 6 months--
SELECT CustomerName, Canceled, SubscriptionEnd
FROM[dbo].[LITA Capstone_Customer Data]
WHERE Canceled = 1 AND 
MONTH (SubscriptionEnd) <=6

---average subscription duration for all customers---
SELECT COUNT(CustomerID) AS All_Customers, AVG (DATEDIFF(DAY, SubscriptionStart, SubscriptionEnd))
AS Average_Subscription_Duration 
FROM [dbo].[LITA Capstone_Customer Data]
WHERE SubscriptionEnd IS NOT NULL

---customers with subscriptions longer than 12 months--
SELECT CustomerName, SubscriptionType,SubscriptionStart, SubscriptionEnd
FROM [dbo].[LITA Capstone_Customer Data]
WHERE DATEDIFF (MONTH, SubscriptionStart, SubscriptionEnd) >12

---total revenue by subscription type--
SELECT SubscriptionType, SUM(Revenue) AS Total_Reveue
FROM [dbo].[LITA Capstone_Customer Data]
GROUP BY SubscriptionType

---top 3 regions by subscription cancellations--
SELECT TOP 3 Region, Canceled
FROM [dbo].[LITA Capstone_Customer Data]

SELECT Region, COUNT(canceled)
FROM [dbo].[LITA Capstone_Customer Data]
ORDER BY SUM (Canceled) DESC

SELECT Region, COUNT (Canceled)
FROM [dbo].[LITA Capstone_Customer Data]
WHERE Canceled = 1
ORDER BY Region DESC

----total number of active and canceled subscriptions--
SELECT* FROM [dbo].[LITA Capstone_Customer Data]

SELECT SUM (CASE WHEN CANCELED = 0 THEN 1 ELSE 0 END) AS ActiveSubscriptions, 
SUM (CASE WHEN CANCELED = 1 THEN 1 ELSE 0 END) AS CanceledSubscriptions
FROM [dbo].[LITA Capstone_Customer Data]
GROUP BY Canceled``` 


4. Power BI
I created visuals, measures and new columns

### Data Visualization
- Microsoft Excel




