# Car Sales Power BI Project

### 🖼️ Dashboard Preview

### Overview Page 
![Overview Page](/Car%20Sales/Dashboard%20Screenshots/Car%20Sales%20Dashboard%20Screenshot.jpg)

### Details Page
![Details Page](/Car%20Sales/Dashboard%20Screenshots/Car%20Sales%20Dashboard%20Details%20Screenshot.jpg)

## 📌 Project Overview

This project is an end-to-end data analytics dashboard built using Power BI to analyze car sales performance.

The goal of this project is to transform raw sales data into interactive visual insights that help stakeholders understand trends, track KPIs, and make data-driven decisions.



This project follows a real-world business scenario where a car dealership wants to monitor sales performance across different dimensions such as time, region, vehicle type, and customer behavior.



## 🎯 Problem Statement

The company needs a dynamic dashboard to:

- Track sales performance over time

- Monitor key business KPIs

- Identify trends and growth opportunities

- Compare performance against previous periods

The dashboard provides insights into:

- Sales revenue

- Average car prices

- Number of cars sold

- Regional and company performance





## 📊 Key Features



### 1. KPI Metrics



The dashboard includes the following KPIs:

- YTD (Year-to-Date) Total Sales

- MTD (Month-to-Date) Total Sales

- YOY (Year-over-Year) Growth

- Average Price (YTD & MTD)

- Cars Sold (YTD & MTD)

- Difference between YTD and Previous Year (PTYD)



### 2. Visualizations



#### 📈 Sales Trends

Weekly trend of YTD sales

Helps identify seasonality and performance spikes



#### 🥧 Sales Distribution

Sales by Body Style

Sales by Color



#### 🌍 Regional Analysis

Map showing Cars Sold by Dealer Region



#### 🏢 Company Performance

Grid showing:

- Company Name

- YTD Sales

- Cars Sold

- Average Price

- % Contribution



#### 📋 Detailed Sales Table

Full transaction-level data including:

- Car Model

- Customer Name

- Dealer Name

- Region

- Sales Amount

- Date




### 🛠️ Tools & Technologies

- Power BI – Data visualization & dashboard creation

- Power Query – Data cleaning & transformation

- DAX (Data Analysis Expressions) – Calculated measures & KPIs

- VS Code – Project structure & version control

- GitHub – Project hosting

Power BI enables building interactive dashboards and real-time insights, which are essential for business decision-making .



### 🧹 Data Preparation

Steps performed:

- Data cleaning (handling missing values, formatting)

- Data transformation using Power Query

- Creating relationships between tables

- Creating calculated columns and measures using DAX



### 📐 Data Modelling

Fact Table:
- Sales Data

Dimension Tables:

- Customers

- Dealers

- Cars

- Dates

Relationships were created to enable efficient filtering and aggregation across visuals.



### 📌 Key Insights

- Some insights derived from the dashboard:

- Certain body styles contribute more to total revenue

- Sales show noticeable weekly fluctuations

- A few companies dominate total sales contribution

- Regional performance varies significantly





### DAX Measures



#### 📊 Sales Metrics
```  
Total Sales = 

SUM(car_data[Price ($)])

YTD Total Sales = 

TOTALYTD(

    [Total Sales],

    'Calendar Table'[Date]

)
```
```
MTD Total Sales = 

TOTALMTD(

    [Total Sales],

    'Calendar Table'[Date]

)
```
```
PTYD Total Sales = 

CALCULATE(

    [YTD Total Sales],

    SAMEPERIODLASTYEAR('Calendar Table'[Date])

)
```
```
Sales Difference = 

[YTD Total Sales] - [PTYD Total Sales]
```
```
YoY Sales Growth % = 

DIVIDE(

    [Sales Difference],

    [PTYD Total Sales],

    0

)
```
#### 🚗 Cars Sold Metrics
```
Cars Sold = 

COUNT(car_data[Car_ID])

YTD Cars Sold = 

TOTALYTD(

    [Cars Sold],

    'Calendar Table'[Date]

)
```
```
MTD Cars Sold = 

TOTALMTD(

    [Cars Sold],

    'Calendar Table'[Date]

)
```
```
PTYD Cars Sold = 

CALCULATE(

    [YTD Cars Sold],

    SAMEPERIODLASTYEAR('Calendar Table'[Date])

)
```
```
Cars Sold Difference = 

[YTD Cars Sold] - [PTYD Cars Sold]
```
```
YoY Cars Sold Growth % = 

DIVIDE(

    [Cars Sold Difference],

    [PTYD Cars Sold],

    0

)
```
#### 💰 Average Price Metrics
```
Average Price = 

AVERAGE(car_data[Price ($)])
```
```
YTD Avg Price = 

CALCULATE(

    [Average Price],

    DATESYTD('Calendar Table'[Date])

)
```
```
MTD Avg Price = 

CALCULATE(

    [Average Price],

    DATESMTD('Calendar Table'[Date])

)
```
```
PTYD Avg Price = 

CALCULATE(

    [YTD Avg Price],

    SAMEPERIODLASTYEAR('Calendar Table'[Date])

)
```
```
Avg Price Difference = 

[YTD Avg Price] - [PTYD Avg Price]
```
```
YoY Avg Price Growth % = 

DIVIDE(

    [Avg Price Difference],

    [PTYD Avg Price],

    0

)
```