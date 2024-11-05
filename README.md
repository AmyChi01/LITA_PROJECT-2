# LITA_CAPSTONE_PROJECT
Here, I documented my final project while learning Data Analysis with the Incubator Hub.

## Project Title: Customer Data Analysis

### Table_of_content

[Project Overview](#project-overview) 

[Data Source](data-source)

[Tools Used](tools-used)

[Data Cleaning and Preparation](data-cleaning-and-preparation)

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

### Exploratory Data Analysis
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
GROUP BY Canceled
``` 


4. Power BI
I created visuals, measures and new columns

### Data Visualization
- Microsoft Excel
  
![Capstone Customer_1](https://github.com/user-attachments/assets/63cba3a2-1803-4d6f-b28e-3f12bfed3cad)


![Capstone Customer_2](https://github.com/user-attachments/assets/86d84cd8-6040-480f-af36-9b4dca9397dc)


![Capstone Customer_3](https://github.com/user-attachments/assets/8df52bc5-98d0-4eda-936d-45cae885d73f)


![Capstone Customer_4](https://github.com/user-attachments/assets/ea3336c3-7de4-4c5f-bd99-2fb1318bc1d6)


![Capstone Customer_11](https://github.com/user-attachments/assets/407585ec-45e1-4ce3-96cf-207857d9c81c)




-Power BI
![Capstone Customer_5](https://github.com/user-attachments/assets/157d109c-9795-49f8-a8f6-39f5071832e3)


![Capstone Customer_6](https://github.com/user-attachments/assets/1fb2e956-4be3-49fc-ba96-b5c3eaf351f2)


![Capstone Customer_7](https://github.com/user-attachments/assets/3e2f9536-7f75-4f97-86c3-bcd771c19a85)


![Capstone Customer_9](https://github.com/user-attachments/assets/b344c304-283b-485b-80a2-95830e432388)


![Capstone Customer_10](https://github.com/user-attachments/assets/3c516bfc-280e-4963-a0a0-72954284b615)



### Recommendations
From the analysis carried out on the customer data, the Eastern region recorded 8488 customers, the North, 8433, the South,	8446 and the West,	8420, indicating that the East had the highest number of customers. In addition, after confirming the canceled subscriptions in each region, it was found that the East had 0 canceled subscriptions, the North,	5067 canceled subscriptions, the South, 5064 canceled subscriptions, and the West, 5044 canceled subscriptions.  The East aslo had the highest revenue generated (16958763), while the North had the lowest revenue generated (16817972). In considering the active subscriptions, the East recorded	8488 Active subscriptions, the North,	3366, the 
South,	3382, and the West,	3376. This shows that the West still holds the highest number of active subscribers, while the North has the least. To boost the subscription levels in the North, the company may invest in more promotional activities, and incentives to boost patronage. 

Of the three subscription types, the Basic subscription type had the highest patronage, generating the highest revenue 33776735 while the Standard subscription type had the lowest, generating the lowest revenue of 16864376. The Basic subscription type also had the highest number of active subscriptions. Indicating that the Basic subscription is the most patronized. This may be as a result of its affordability. The second most patronized subscription type was the Premium subscription, while the Standard subscription was the least patronized. It is important that the company focuses also on the Premium and Standard subscription types, to foster more Subscriptions. The company may also focus on advertising their services to the upper class citizens, to boost the number of premium subscribers.   
















