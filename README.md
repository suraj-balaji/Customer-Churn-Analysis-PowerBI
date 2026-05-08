# Customer Churn Analysis (Power BI)

## Project Overview

This project analyzes customer churn behavior for a telecom service provider using Power BI. The objective of the analysis is to identify the major factors contributing to customer churn and provide actionable business recommendations to improve customer retention.

The dashboard focuses on customer demographics, contract behavior, payment methods, service usage patterns, international usage, customer support interactions, and pricing-related churn drivers.

The project was developed using a complete end-to-end data analytics workflow including:
- Data cleaning
- Data transformation
- Data modeling
- DAX calculations
- Business analysis
- Interactive dashboard development
- Business insights and recommendations

---

## Business Problem

Customer churn is one of the biggest challenges faced by telecom companies. Losing customers directly impacts revenue, acquisition costs, and long-term business growth.

Databel Telecom wanted to understand:
- Why customers are leaving
- Which customer segments are at highest risk
- What business factors influence churn behavior
- Which retention strategies could reduce customer loss

The company especially wanted to investigate:
- Contract-related churn
- Competitor influence
- Customer service issues
- Pricing dissatisfaction
- International usage behavior
- Unlimited plan usage mismatch
- Demographic risk patterns

---

## Project Objectives

The main objectives of this analysis were:

- Analyze customer churn behavior across multiple dimensions
- Identify high-risk customer segments
- Discover the major churn drivers
- Compare churn across contract types and payment methods
- Analyze customer service interaction impact
- Investigate unlimited plan and usage behavior
- Study demographic-based churn trends
- Provide business-focused retention recommendations
- Build an interactive Power BI dashboard for decision-making

---

## Dataset Information

Dataset Name: Databel Telecom Customer Churn Dataset

Dataset Type:
Telecom customer behavior and churn analysis dataset

Key Dataset Features:
- Customer demographics
- Contract type
- Payment method
- Account length
- Monthly charges
- International usage
- Unlimited data plan usage
- Customer service calls
- Churn category
- Churn reasons

Total Customers Analyzed:
~6.7K customers

---

## Tools & Technologies Used

- Power BI Desktop
- Power Query
- DAX (Data Analysis Expressions)
- Data Modeling
- Microsoft Excel / CSV Dataset
- Data Visualization Techniques
- Business Intelligence & Analytics

---

# Dashboard Pages

## 1. Executive Overview Dashboard

Purpose:
Provides a high-level overview of customer churn performance and major churn indicators.

Key Metrics:
- Total Customers
- Total Churn Customers
- Churn Rate %
- Average Account Length
- Average Monthly Charges

Main Insights:
- Competitor-related issues are the biggest churn drivers
- Monthly contract customers show higher churn behavior
- Certain states demonstrate significantly higher churn risk
- Short-tenure customers are more likely to churn

Visuals Included:
- KPI Cards
- Churn Reason Analysis
- Churn Category Analysis
- Contract Distribution
- State-wise Churn Map
- Key Business Insights

---

## 2. Customer Age & Demographic Analysis

Purpose:
Analyzes customer churn behavior across different age groups and demographic segments.

Key Findings:
- Senior customers show the highest churn rate
- Customers above 65 years demonstrate elevated churn risk
- Younger customers have lower churn despite larger customer share
- Customer grouping reveals varying pricing sensitivity

Visuals Included:
- Age Group Churn Analysis
- Customer Segment Churn Comparison
- Monthly Charge vs Churn Trend
- Demographic Distribution Analysis

---

## 3. Contract & Payment Behavior Analysis

Purpose:
Investigates how contract type, payment methods, and customer tenure impact churn behavior.

Key Findings:
- Month-to-month contracts have the highest churn rate
- Yearly contracts significantly improve customer retention
- Paper check customers exhibit the highest payment-related churn risk
- Longer account tenure reduces churn probability

Visuals Included:
- Contract Type Churn Trend
- Payment Method Risk Analysis
- Tenure vs Churn Relationship
- Contract & Payment Matrix

---

## 4. Usage & Extra Charges Analysis

Purpose:
Examines customer usage patterns, unlimited plan behavior, and billing-related churn drivers.

Key Findings:
- Customers with unlimited plans but low data usage show high churn behavior
- Low usage customers may perceive pricing mismatch
- Extra data charge groups reveal varying churn behavior
- Billing optimization opportunities exist for low-consumption users

Visuals Included:
- Unlimited Plan Analysis
- Data Usage Segmentation
- Extra Charge Analysis
- Usage-based Customer Segmentation

---

## 5. International Usage & Service Call Analysis

Purpose:
Studies the relationship between international usage behavior, customer support interactions, and churn patterns.

Key Findings:
- Customers making frequent service calls show significantly higher churn rates
- Internationally active customers without international plans exhibit elevated churn risk
- Customer support experience strongly influences retention
- High service-call states demonstrate higher churn concentration

Visuals Included:
- Service Call Trend Analysis
- International Usage Risk Matrix
- State-wise Churn Distribution
- Customer Support Interaction Analysis

---

## 6. Customer Churn Insights & Recommendations

Purpose:
Summarizes the major business findings and provides strategic retention recommendations.

Key Business Insights:
- Competitor pressure is the primary churn driver
- Monthly contracts contribute heavily to churn
- Senior customers are a high-risk demographic
- Low-usage unlimited plan customers indicate pricing mismatch
- Customer support quality impacts retention

Business Recommendations:
- Promote yearly contract adoption
- Improve customer support quality
- Launch loyalty retention campaigns
- Optimize pricing for low-usage customers
- Improve retention strategies for high-risk segments

Visuals Included:
- Executive KPI Summary
- Strategic Risk Indicators
- Key Findings Panels
- Business Recommendation Matrix
- Executive Conclusion Section

---

# Key DAX Measures & Calculated Columns

## Core KPI Measures

### Total Customers

```DAX
No. of Customers =
COUNT('Databel - Data'[Customer ID])
```
Purpose:
Calculates the total number of customer records.
```
No. of Churn Customers =
SUM('Databel - Data'[churned])
```
Purpose:
Counts distinct customers for accurate customer analysis.
```
No. of Churn Customers =
SUM('Databel - Data'[churned])
```
Purpose:
Calculates total churned customers.
```
Churn Rate % =
DIVIDE(
    [No. of Churn Customers],
    [No. of Customers]
)
```
Purpose:
Measures the percentage of customers who churned.
```
Avg Monthly Charges =
AVERAGE('Databel - Data'[Monthly Charges])
```
Purpose:
Calculates the average monthly billing amount.

```
Avg Account Length =
AVERAGE('Databel - Data'[Account Length (in months)])
```
Purpose:
Measures average customer tenure.

```
churned =
IF(
    'Databel - Data'[Churn Label] = "Yes",
    1,
    0
)
```
Purpose:
Creates a binary churn indicator for KPI calculations

```
Grouped Consumption =
IF(
    'Databel - Data'[Avg Monthly GB Download] < 5,
    "Less than 5 GB",
    IF(
        'Databel - Data'[Avg Monthly GB Download] < 10,
        "Between 5 to 10 GB",
        "10 or More GB"
    )
)
```
Purpose:
Segments customers based on data usage behavior.
```
Demographics =
IF(
    'Databel - Data'[Under 30] = "Yes",
    "Under 30",
    IF(
        'Databel - Data'[Senior] = "Yes",
        "Senior",
        "Other"
    )
)
```
Purpose:
Creates demographic segmentation for churn analysis
```
Contract Category =
SWITCH(
    'Databel - Data'[Contract Type],
    "One year", "Yearly",
    "Two year", "Yearly",
    "Monthly"
)
```
Purpose:
Simplifies contract segmentation into yearly vs monthly behavior groups.
```
Avg Extra International Charges =
SUM('Databel - Data'[Extra International Charges])
/
[No. of Customers]

```
Purpose:
Measures average additional international service charges per customer.

```
Avg Extra Data Charges =
SUM('Databel - Data'[Extra Data Charges])
/
[No. of Customers]
```
Purpose:
Measures average additional data charges across customers.

```
Avg Customer Service Calls =
SUM('Databel - Data'[Customer Service Calls])
/
[No. of Customers]
```
Purpose:
Measures average customer support interaction frequency.


# Data Preparation & Project Architecture

## Data Preparation Process

The dataset was cleaned and transformed using Power Query in Power BI.

The preparation workflow included:
- Data type corrections
- Null value inspection
- Column standardization
- Business-oriented calculated columns
- Segmentation preparation
- Churn flag creation
- Customer grouping logic
- Usage behavior categorization

---

## Data Cleaning Activities

The following data preparation steps were performed:

### Data Type Validation
- Verified numeric, text, and categorical fields
- Corrected formatting inconsistencies
- Standardized data structures

### Data Transformation
- Created churn indicator columns
- Generated customer demographic segments
- Grouped account usage categories
- Simplified contract categories
- Created age-based customer groupings

### Business Logic Implementation
- Segmented customers by usage behavior
- Identified high-risk churn groups
- Prepared data for behavioral analysis
- Structured metrics for executive reporting

---

## Power Query Transformations

Major Power Query operations included:
- Column renaming
- Data filtering
- Conditional column creation
- Text standardization
- Data categorization
- Numeric grouping logic
- Data quality validation

---

## Data Model Design

The project primarily used a structured analytical data model optimized for churn analysis and dashboard performance.

The model design focused on:
- Efficient filtering
- Simplified relationships
- KPI calculation performance
- Interactive reporting capability
- Segmentation-based analytics

---

## Analytical Workflow

The project followed an end-to-end analytics workflow:

1. Business Problem Understanding
2. Data Cleaning & Transformation
3. Customer Segmentation
4. KPI Development
5. Exploratory Analysis
6. Dashboard Design
7. Insight Generation
8. Business Recommendations
9. Executive Storytelling

---

## Dashboard Design Approach

The report was designed using a business storytelling approach:

- Executive overview first
- Customer segmentation analysis
- Contract & payment behavior analysis
- Usage & billing analysis
- Customer support analysis
- Final business recommendations

The dashboard design prioritized:
- readability
- business usability
- insight clarity
- executive reporting
- interactive exploration

---

## Performance Optimization

Basic optimization practices were implemented including:
- Removal of unnecessary visuals
- Simplified filtering logic
- KPI-based reporting
- Reduced visual clutter
- Optimized page structure
- Efficient DAX calculations


---

# Key Business Insights & Recommendations

## Key Business Insights

### 1. Competitor Pressure is the Largest Churn Driver

The analysis revealed that competitor-related reasons represent the highest source of customer churn. Customers frequently leave due to better competitor offers, pricing advantages, and perceived service improvements.

Business Impact:
- High competitive pressure directly affects customer retention
- Existing pricing and loyalty strategies may be insufficient
- Customers are highly price-sensitive

Recommendation:
- Develop targeted retention campaigns
- Improve loyalty reward programs
- Monitor competitor pricing strategies more aggressively

---

### 2. Month-to-Month Contracts Create High Churn Risk

Customers using monthly contracts demonstrate significantly higher churn rates compared to yearly contract customers.

Business Impact:
- Short-term contracts reduce customer retention stability
- Monthly customers are less committed to the service

Recommendation:
- Encourage yearly contract adoption through discounts and incentives
- Launch renewal campaigns for short-tenure customers
- Create retention-focused upgrade offers

---

### 3. Senior Customers Show Elevated Churn Behavior

Senior customer groups exhibit the highest churn rates among demographic segments.

Business Impact:
- Customer support experience may not fully meet senior customer expectations
- Service complexity or pricing concerns may disproportionately impact senior customers

Recommendation:
- Improve customer support accessibility for senior users
- Simplify communication and billing transparency
- Create senior-focused loyalty programs

---

### 4. Unlimited Plan Customers with Low Usage Show Pricing Mismatch

Customers subscribed to unlimited plans but using very low amounts of data display elevated churn behavior.

Business Impact:
- Customers may perceive poor pricing value
- Plan mismatch reduces customer satisfaction

Recommendation:
- Introduce lower-cost plans for low-usage customers
- Improve personalized plan recommendations
- Provide usage-based plan optimization alerts

---

### 5. Customer Service Calls are Strong Churn Indicators

Customers making frequent customer service calls demonstrate substantially higher churn rates.

Business Impact:
- High support interaction frequency indicates unresolved customer dissatisfaction
- Service quality directly impacts retention

Recommendation:
- Improve first-call resolution rates
- Monitor repeated service-call customers as high-risk segments
- Implement proactive retention outreach after repeated complaints

---

### 6. Geographic Regions Demonstrate Uneven Churn Risk

Certain states show significantly higher churn concentration compared to others.

Business Impact:
- Regional operational or competitive differences may influence customer retention
- High-risk regions require targeted intervention

Recommendation:
- Investigate regional pricing and service quality differences
- Strengthen retention strategies in high-risk states
- Monitor regional churn performance continuously

---

# Executive Summary

The analysis indicates that customer churn is primarily driven by:
- competitive market pressure,
- short-term contract behavior,
- pricing-plan mismatch,
- and customer support dissatisfaction.

The highest-risk customer groups include:
- monthly contract customers,
- senior customers,
- low-usage unlimited-plan users,
- and customers with repeated support interactions.

A combination of:
- retention campaigns,
- pricing optimization,
- customer support improvements,
- and long-term contract incentives

could significantly reduce churn risk and improve customer retention performance.

---

# Dashboard Screenshots

## Executive Overview

<img width="492" height="289" alt="overview_page" src="https://github.com/user-attachments/assets/c4c7cb2f-4874-4679-a568-ac4239c1b1e6" />


---

## Customer Age & Demographic Analysis

<img width="595" height="335" alt="age_demographic_analysis" src="https://github.com/user-attachments/assets/5c7f30e4-aca1-452b-a0bc-f56e14fa31bf" />


---

## Contract & Payment Behavior Analysis

<img width="596" height="334" alt="contract_payment_analysis" src="https://github.com/user-attachments/assets/c5d29983-0903-40e4-b5bc-c96d29ce3501" />


---

## Usage & Extra Charges Analysis

<img width="595" height="332" alt="usage_extra_charges_analysis" src="https://github.com/user-attachments/assets/85f6a123-3359-4cd9-b631-cd4af0412ae6" />


---

## Customer Support & International Usage Analysis

<img width="594" height="332" alt="service_international_analysis" src="https://github.com/user-attachments/assets/d00a5fa5-4fdb-4245-b380-2987d5e7b18a" />


---

## Customer Churn Insights & Recommendations

<img width="594" height="331" alt="insights_recommendations" src="https://github.com/user-attachments/assets/ae8382f0-4750-48ae-b60f-7d64a98fd59d" />



---

# Project Folder Structure

```text
Customer-Churn-Analysis-PowerBI
│
├── README.md
│
├── PBIX File
│   └── Customer_Churn_Analysis.pbix
│
├── Dataset
│   ├── Databel_Customer_Churn.csv
│   └── Dataset_Source.txt
│
├── Images
│   ├── overview_page.png
│   ├── age_demographic_analysis.png
│   ├── contract_payment_analysis.png
│   ├── usage_extra_charges_analysis.png
│   ├── service_international_analysis.png
│   ├── insights_recommendations.png
│   
│
├── Documentation
│   ├── Business_Problem.md
│   ├── Data_Cleaning_and_Preparation.md
│   ├── Business_Insights.md
│   ├── Recommendations.md
│   ├── Performance_Optimization.md
│   └── Project_Architecture.md
│
├── DAX Measures
│   └── DAX_Measures.md
│
└── Presentation
    └── Customer_Churn_Analysis_Presentation.pdf
```
Future Improvements

Possible future enhancements for this project include: </br>
Customer lifetime value analysis </br>
Cohort retention analysis </br>

---

Business Impact

This project demonstrates how business intelligence and customer analytics can help telecom companies:

identify high-risk customer segments,
improve retention strategies,
optimize pricing models,
monitor customer dissatisfaction indicators,
and support data-driven decision-making.

The dashboard was designed to support:

executive reporting,
operational analysis,
retention strategy planning,
and customer behavior investigation.

---

Author

Suraj Bhagaye </br>
besuraj28@gmail.com


Skills Demonstrated:

Power BI </br>
Power Query </br>
DAX </br>
Data Visualization </br>
Business Analytics </br>
Customer Segmentation </br>
Dashboard Design </br>
Business Storytelling </br>
Data Cleaning & Transformation </br>
Analytical Problem Solving </br>
