# LITA-CUSTOMER-PROJECT

**Summary**

This project outlines a comprehensive approach to analyzing customer data for a subscription service. Here’s a detailed plan for each phase of the project, from Excel analysis to SQL queries and Power BI visualization.


**Project Objectives**


Analyze customer data to identify patterns in subscription usage and preferences.

Assess how different demographics (e.g., age, region) affect subscription choices and behavior

Classify customers into meaningful segments based on subscription type, duration, and behavior.

Identify high-value segments for targeted marketing and retention strategies.

Determine which subscription types are most popular among customers.

Compute average subscription duration to understand customer loyalty.

Track renewal rates and identify factors that contribute to customer retention


**These objectives aim to enhance understanding of customer dynamics within the subscription service, ultimately leading to better strategies for customer acquisition, retention, and revenue growth.
**


**Data Source**


The datasets of this project was provided by ladies in tech africa as an assignment for analytic purpose.


**Dataset**

CustomerID: Unique identifier for each customer

SubscriptionType: Type of subscription (e.g., Basic, Premium, Standard)

SubscriptionStart: Date when the subscription started

SubscriptionEnd: Date when the subscription ended

Cancelled: Indicates if the subscription was cancelled (TRUE/FALSE)

Revenue: Total revenue generated from the subscription

Region: Geographic region of the customer




**Tools Used**

Excel

Purpose: Excel is great for initial data exploration and quick analysis. It allows for easy manipulation of data and visualization through pivot tables and charts.

SQL

Purpose: SQL is ideal for querying large datasets efficiently and performing complex analyses. It provides a robust framework for data manipulation and retrieval.

Power BI

Purpose: Power BI is designed for data visualization and business intelligence, allowing users to create interactive reports and dashboards. It makes it easier to communicate insights derived from data.

Github

Purpose: Github is iseal for portfolio building and public showcasing of the work done.


**Data Cleaning and Preparation**


Data cleaning is a crucial step in the data analysis process that ensures data is accurate, consistent, and complete.

Here are some steps you can take to clean data for analysis:

 Remove Duplicate

Action: Identified and removed 41,213 duplicate records from the dataset, resulting in 33,787 unique values remaining.

Add duration colum

Action: Subsciption end date - start date










![Screenshot (599)](https://github.com/user-attachments/assets/9f32606d-fecf-428d-b482-48a7d139ac17)


Before cleaning


![Screenshot (601)](https://github.com/user-attachments/assets/090ff717-cfcd-4f7c-ad7a-e2e18a1d15cf)



After cleaning




**Instructions**


1. Excel:

o Analyze customer data using pivot tables to find subscription patterns.

o Calculate the average subscription duration and identify the most popular 
subscription types.

o Create any other interesting reports.


2. SQL:
   

Write queries to extract key insights based on the following questions. 

o retrieve the total number of customers from each region.

o find the most popular subscription type by the number of customers.

o find customers who canceled their subscription within 6 months.

o calculate the average subscription duration for all customers.

o find customers with subscriptions longer than 12 months.

o calculate total revenue by subscription type.

o find the top 3 regions by subscription cancellations.

o find the total number of active and canceled subscriptions.

3. Power BI:

o Build a Power BI dashboard that visualizes key customer segments, 
cancellations, and subscription trends. Include slicers for interactive analysis


**Data Analysis**


Analyze customer data using pivot tables to find subscription patterns

1. Subscription type by revenue


![Screenshot (595)](https://github.com/user-attachments/assets/c75baaa3-82ba-4c0f-8223-bf0211c6ae9c)

Insight : Basic brings in more revenue for the business due to it affordability .

More marketing strategies should be adopted to maximize this subsciption type as customer"s preference.




2. Subscription date by revenue


![Screenshot (594)](https://github.com/user-attachments/assets/e1d7d063-1ecc-4208-978c-751bbafd669a)


Insight: more revenue was made in 2022 than 2023.

Promo and exciting offers can be made to attract customers who have stopped subscribing.




**Calculate the average subscription duration**

Average subsciption duration is 365 days

![Screenshot (602)](https://github.com/user-attachments/assets/0901b693-21f8-4910-b139-4b629f03c6b6)



**Identify the most popular subscription types**

The Basic subscription is the clear favorite among customers, with 16,921 customers subscribing.


![Screenshot (603)](https://github.com/user-attachments/assets/80da35cd-54fb-4a98-99cd-cdb21ed4b475)


![Screenshot (604)](https://github.com/user-attachments/assets/00305dd9-d64e-4acc-8b6f-bad0ac33d767)



**Create any other interesting reports.
**


 Region by revenue

![Screenshot (593)](https://github.com/user-attachments/assets/f4809c79-d052-4ad3-bd1b-e0f91f84738c)

Insight : The difference in revenue made from the regions isn"t outrageous.

All region should be given equal marketing and inventory assistance.





SQL

 **Total number of customers from each region.**



```sql
SELECT Region, 
COUNT(CustomerID) AS TotalCustomers
FROM [dbo].[LITA Capstone Dataset CustomerData]
GROUP BY Region
Order by TotalCustomers desc
```


![Screenshot (607)](https://github.com/user-attachments/assets/2fdcdf22-0288-43b6-9b73-06a21318a624)





**Most popular subscription type by the number of customers.**


```sql
SELECT Top 1 SubscriptionType, 
COUNT(CustomerID) AS CustomerCount
FROM [dbo].[LITA Capstone Dataset CustomerData]
GROUP BY SubscriptionType
ORDER BY CustomerCount DESC
```


Find customers who canceled their subscription within 6 months.

```sql
SELECT CustomerID, CustomerName, 
DATEDIFF(Month, SubscriptionStart, SubscriptionEnd) AS DurationInMonth
FROM [dbo].[LITA Capstone Dataset CustomerData]
WHERE Canceled = '1'
  AND DATEDIFF(Month, SubscriptionStart, SubscriptionEnd)
```


Insight: No customer cancelled their subscription during the period in view




**calculate the average subscription duration for all customers.**

```sql
SELECT AVG(DATEDIFF(DAY, SubscriptionStart, SubscriptionEnd)) 
AS AverageSubscriptionDuration
FROM [dbo].[LITA Capstone Dataset CustomerData]
```

Observation : the average subscription duration is 365 days.


**Find customers with subscriptions longer than 12 months**


```sql
SELECT CustomerID, CustomerName
FROM [dbo].[LITA Capstone Dataset CustomerData]
WHERE DATEDIFF(Month, SubscriptionStart, SubscriptionEnd) > 12
```

No customer had subscription that lasted more than 12 months.


**calculate total revenue by subscription type.
**

```sql
SELECT SubscriptionType, SUM(Revenue) AS TotalRevenue
FROM [dbo].[LITA Capstone Dataset CustomerData]
GROUP BY SubscriptionType
```


![Screenshot (608)](https://github.com/user-attachments/assets/8d295ecb-7474-4a3c-84ef-8d82742d8a96)




Find the top 3 regions by subscription cancellations.


```sql
SELECT Region, COUNT(*) AS CancellationCount
FROM [dbo].[LITA Capstone Dataset CustomerData]
WHERE Canceled = 1  
GROUP BY Region
ORDER BY CancellationCount DESC
OFFSET 0 ROWS FETCH NEXT 3 ROWS ONLY
```



**Find the total number of active and canceled subscriptions.**


```sql
SELECT 
    SUM(CASE WHEN Canceled = 0 THEN 1 ELSE 0 END) AS ActiveSubscriptions,
    SUM(CASE WHEN Canceled = 1 THEN 1 ELSE 0 END) AS CancelledSubscriptions
FROM [dbo].[LITA Capstone Dataset CustomerData]
```





















































1. Excel Analysis
Pivot Tables:

Create pivot tables to analyze:
Subscription types and their counts.
Customer distribution by region.
Cancellations over time.
Calculating Average Subscription Duration:

Use the formula:
Average Subscription Duration
=
Total Subscription Duration
Number of Customers
Average Subscription Duration= 
Number of Customers
Total Subscription Duration
​
 
Analyze subscription duration across different types.
Identifying Popular Subscription Types:

Use a pivot table to count the frequency of each subscription type.
Highlight the top three most popular subscription types.
Additional Reports:

Trend analysis of subscription sign-ups and cancellations over time.
Comparison of revenue generated by different subscription types.
2. SQL Queries
Once the dataset is loaded into SQL Server, you can run the following queries:

Total Number of Customers by Region:

sql
Copy code
SELECT Region, COUNT(CustomerID) AS TotalCustomers
FROM Customers
GROUP BY Region;
Most Popular Subscription Type:

sql
Copy code
SELECT SubscriptionType, COUNT(CustomerID) AS CustomerCount
FROM Customers
GROUP BY SubscriptionType
ORDER BY CustomerCount DESC
LIMIT 1;
Customers Who Canceled Within 6 Months:

sql
Copy code
SELECT *
FROM Customers
WHERE CancellationDate IS NOT NULL AND DATEDIFF(MONTH, SubscriptionStartDate, CancellationDate) <= 6;
Average Subscription Duration:

sql
Copy code
SELECT AVG(DATEDIFF(MONTH, SubscriptionStartDate, SubscriptionEndDate)) AS AverageDuration
FROM Customers;
Customers with Subscriptions Longer than 12 Months:

sql
Copy code
SELECT *
FROM Customers
WHERE DATEDIFF(MONTH, SubscriptionStartDate, SubscriptionEndDate) > 12;
Total Revenue by Subscription Type:

sql
Copy code
SELECT SubscriptionType, SUM(Revenue) AS TotalRevenue
FROM Customers
GROUP BY SubscriptionType;
Top 3 Regions by Subscription Cancellations:

sql
Copy code
SELECT Region, COUNT(CustomerID) AS Cancellations
FROM Customers
WHERE CancellationDate IS NOT NULL
GROUP BY Region
ORDER BY Cancellations DESC
LIMIT 3;
Total Number of Active and Canceled Subscriptions:

sql
Copy code
SELECT 
  COUNT(CASE WHEN CancellationDate IS NULL THEN 1 END) AS ActiveSubscriptions,
  COUNT(CASE WHEN CancellationDate IS NOT NULL THEN 1 END) AS CanceledSubscriptions
FROM Customers;
3. Power BI Dashboard
Dashboard Elements:

Visualize customer segments using bar charts for regions and subscription types.
Line charts to show trends in cancellations and renewals over time.
Slicers for interactive filtering by region, subscription type, and time period.
Key Visualizations:

Total active vs. canceled subscriptions.
Revenue breakdown by subscription type.
Number of customers by subscription type and region.
Interactive Features:

Implement slicers for:
Time periods (monthly, quarterly).
Subscription types.
Regions to allow users to drill down into specific data.
GitHub Repository
Create a repository to house:
Excel files with pivot tables and reports.
SQL scripts for queries.
Power BI project file (.pbix) for the dashboard.
Documentation on project methodology and findings.
Final Deliverables
An organized repository on GitHub with all analysis files.
A well-structured Power BI dashboard that provides insights into customer behavior, cancellations, and subscriptions.







