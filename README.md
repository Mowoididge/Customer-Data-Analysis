# Customer_Data_Analysis

## Project Overview
This project involves analyzing customer data for a subscription service to identify
segments and trends. The goal is to understand customer behavior, track subscription types,
and identify key trends in cancellations and renewals. 

## [Project Overview](project-overview)

## [Data Sources](data-sources)

## [Tools Used](tools-used)

## [Data Cleaning and Preparation](data-cleaning-and preparation)

## [Exploratory Data Analysis](exploratory-data-analysis)

## [Data Analysis](data-analysis)

## [Data Visualization](datavisualization)

## [Insights and Key Findings](insights-key-findings) 

## [Conclusion and Recommendations](conclusion-and-recommendations)


## Data Sources
The primary source of data is https://canvas.instructure.com/files/273182802/download?download_frd=1 which supplied by the Incubator Hub Fascilitators
## Tools Used
- Excel: For data exploration and preparation
- SQL: For data cleaning and advanced querying.
- Power BI: For dynamic visualizations and dashboards.
## Data Cleaning and Preparation
In the initial phase of loading the data, I performed the following actions:
1.  Data Inspection
2.  Handling Missing variables in excel
3.  Data Loading and validation in excel and power BI
4.  Data cleaning and formating
## Exploratory Data Analysis
The initial EDA involved exploring the data to answer some key questions about the data such as;
- what is the overall subcription trends and cancellation?
- Which is the Highest subscription type and which is the lowest?
- Who are the top 5 customers?
- What is the total revenue?

## Data Analysis
```sql
SELECT * FROM[dbo].[CUSTOMER DATA]

	....TOTAL NUMBER OF CUSTOMERS IN EACH REGION
SELECT Region,
COUNT(CustomerID) AS Total_Number_Of_Customers
FROM [dbo].[CUSTOMER DATA]
GROUP BY Region
ORDER BY Total_Number_Of_Customers DESC

.......MOST POPULAR SUBSCRIPTION TYPE BY NUMBER OF CUSTOMER....
SELECT TOP 1
    SubscriptionType,
    COUNT(CustomerID) AS NUMBER_OF_CUSTOMERS
FROM [dbo].[CUSTOMER DATA]
    GROUP BY SubscriptionType
ORDER BY NUMBER_OF_CUSTOMERS DESC



.......CUSTOMERS WHO CANCELLED THEIR SUBSCRIPTION WITHIN 6MONTHS.....
SELECT  COUNT(CustomerID) As Customers_who_Cancelled
FROM [dbo].[CUSTOMER DATA]
WHERE 
    Canceled=1
    AND DATEDIFF(month, SubscriptionStart, SubscriptionEnd) <= 6


.......AVERAGE SUBCRIPTION DURATION FOR ALL CUSTOMERS......
 SELECT 
    AVG(DATEDIFF(day, SubscriptionStart, SubscriptionEnd)) AS average_duration_days
FROM [dbo].[CUSTOMER DATA]


..... CUSTOMER SUBCRIPTION LONGER THAN 12MONTHS....
SELECT CustomerID,SubscriptionStart,SubscriptionEnd
FROM [dbo].[CUSTOMER DATA]
WHERE 
  DATEDIFF(month, SubscriptionStart, SubscriptionEnd) > 12


  .......TOTAL REVENUE BY SUBSCRIPTION TYPE.....
  SELECT SubscriptionType,
    SUM(Revenue) AS Total_revenue
FROM [dbo].[CUSTOMER DATA]
GROUP BY SubscriptionType
ORDER BY Total_revenue DESC

........TOP 3 REGION BY SUBCRIPTION CANCELLATION.....
SELECT Top 3 Region,
    COUNT(*) AS Cancellation_count
FROM [dbo].[CUSTOMER DATA]
WHERE  canceled = 1
GROUP BY Region
ORDER BY Cancellation_count DESC

......TOTAL NUMBERS OF ACTIVE AND CANCELED SUBCRIPTION.....
SELECT 
    COUNT(CASE WHEN canceled = 1 THEN 1 END) AS active_subscriptions,
    COUNT(CASE WHEN canceled = 0 THEN 1 END) AS canceled_subscriptions
FROM [dbo].[CUSTOMER DATA]
```

```Dax
Total Revenue = Sum(CustomerData[Revenue])
```
## Data Visualization

![Customer Data Pivot Table](https://github.com/user-attachments/assets/3af35e2d-154f-4532-ac4a-d6ae45566068)


![Screenshot 2024-11-05 150838](https://github.com/user-attachments/assets/54bc6407-4c82-4622-99fa-b60d34abd176)

## Insights and Key Findings         
1.	The most Popular subscription type is  Basic with a total sales value by percentage, followed by Premium and then Standard by a percentage total sales value of 49.90%, 25.08% and 25.02% respectively
	  Insights: The company should  focus on the sales of Basic Subscription
2.	Regional Analysis: The South and west regions has the highest sales of subscription while the east and North followed closely behind
    Recommendation: Consider region-specific marketing to boost sales in the east and north
3.	From the Analysis, it is observed that there is 41,250 active subscriber and 33,750 cancellations and there were equal numbers of cancellations in the North, South and West
  	Recommendations: There should be improved Customer Services and sales discounts should be made available to customers in these regions.
## Conclusion and Recommendations
- Focus Marketing Campaign on Underperforming Regions
- Reward the top 5 Customers
- Focus on sales of the Basic Subscription



