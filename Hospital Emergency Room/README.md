 # 🏥 Hospital Emergency Room Power BI Project



## 📌 Project Overview



This project is an end-to-end data analytics dashboard built using Power BI to analyze hospital emergency room (ER) operations.



The objective is to transform raw patient data into interactive visual insights that enable healthcare stakeholders to monitor performance, improve efficiency, and enhance patient care.



This project simulates a real-world hospital scenario where management needs visibility into patient flow, wait times, and service quality across multiple dimensions such as time, demographics, and department referrals.



## 🎯 Problem Statement

Hospitals require a dynamic dashboard to:

1) Monitor ER performance in real time

2) Track patient flow and wait times

3) Identify operational inefficiencies

4) Analyze patient demographics

5) Improve patient satisfaction

The dashboard provides insights into:

- Patient volume

- Wait time efficiency

- Satisfaction levels
- Admission trends

- Department workload

- Peak hours of operation



## 📊 Key Features



## 1. KPI Metrics

- Total Patients

- Average Wait Time

- Patient Satisfaction Score

- Total Referrals

- Admission Rate (%)

- Patients Seen Within 30 Minutes (%)

## 2. Visualizations

### 📈 Patient Trends

- Monthly & yearly patient analysis

- Identifies patterns and seasonality



### 🥧 Patient Demographics

- Age group distribution

- Gender breakdown

- Race distribution



### 🏥 Department Referral Analysis

- Patient distribution across departments

- Identifies high-demand specialties



### 📊 Admission Status

- Admitted vs Not Admitted

- Evaluates case severity



### ⏱ Wait Time Analysis

- Tracks ER efficiency

- % patients seen within target time



### 📅 Peak Time Heatmap

- Patient volume by Day & Hour

- Identifies busiest time periods



### 📋 Detailed Data Table

Includes:

- Patient ID

- Admission Date

- Age, Gender, Race

- Wait Time

- Satisfaction Score

- Department Referral



### 🖼️ Dashboard Preview

### Monthly View
![](/Hospital%20Emergency%20Room/Dashboard%20Screenshots/Monthly%20View.png)
### Consolidated View
![](/Hospital%20Emergency%20Room/Dashboard%20Screenshots/Consolidated%20View.png)
### Patient Details
![](/Hospital%20Emergency%20Room/Dashboard%20Screenshots/Patient%20Details.png)
### Key Takeaways
![](/Hospital%20Emergency%20Room/Dashboard%20Screenshots/Key%20Takeaways.png)

### 🛠️ Tools & Technologies

- Power BI – Dashboard development

- Power Query – Data transformation

- DAX – Calculations & KPIs

- VS Code – Project documentation

- GitHub – Version control



### 🧹 Data Preparation

Steps performed:

1) Data cleaning (missing values, formatting)

2) Data transformation using Power Query

3) Data anonymization (Patient ID, initials)

4) Created calculated columns (e.g., Admission Hour)

5) Built DAX measures for KPIs



### 📐 Data Modelling

Fact Table:

- Hospital ER Data

Dimension Tables:

- Date

- Patient Demographics

- Department

Relationships were created to enable filtering and cross-analysis across visuals.



### 📊 DAX Measures 



**⏱ Time-Based Column**
```
Admission Hour = 

HOUR('Hospital ER_Data'[Patient Admission Date])
```


**👥 Patient Metrics**
```
Total Patients = 

COUNT('Hospital ER_Data'[Patient ID])
```


**⏱ Wait Time Metrics (Best Practice: Numeric + Display)**
```
Avg Wait Time = 

AVERAGE('Hospital ER_Data'[Patient Waittime])
```
```
Avg Wait Time (Display) = 

FORMAT([Avg Wait Time], "0.0") & " Min"
```
```
Patients Within 30 Min = 

CALCULATE(

    [Total Patients],

    'Hospital ER_Data'[Patient Waittime] <= 30

)
```
```
% Within 30 Min = 

DIVIDE(

    [Patients Within 30 Min],

    [Total Patients],

    0

)
```


**⭐ Satisfaction Metrics**
```
Satisfaction Score = 

AVERAGE('Hospital ER_Data'[Patient Satisfaction Score])
```


**🏥 Admission Metrics**
```
Admitted Patients = 

CALCULATE(

    [Total Patients],

    'Hospital ER_Data'[Patient Admin Flag] = TRUE()

)
```
```
Admission Rate % = 

DIVIDE(

    [Admitted Patients],

    [Total Patients],

    0

)
```


**🏥 Referral Metrics**
```
Total Referrals = 

COUNT('Hospital ER_Data'[Department Referral])
```


## 📌 Key Insights

- Around 40% of patients are not seen within 30 minutes, indicating a performance gap

- Peak ER hours occur between 9 AM – 6 PM

- General Practice dominates referrals, suggesting ER overuse for non-emergency cases

- A significant number of patients are elderly, requiring more complex care

- Patient satisfaction remains high despite moderate wait times