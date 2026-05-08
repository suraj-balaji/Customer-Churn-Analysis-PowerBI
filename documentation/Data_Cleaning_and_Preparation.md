# Data Cleaning & Preparation

## Overview

The dataset preparation process was performed using Power Query in Power BI. The objective of the preparation stage was to clean, standardize, transform, and structure the dataset for business analysis and dashboard reporting.

The data preparation workflow focused on:
- improving data quality,
- creating business-oriented segmentation,
- preparing churn metrics,
- and optimizing the dataset for analytical reporting.

---

## Data Preparation Workflow

The following analytical workflow was followed during the preparation stage:

1. Data Import
2. Data Type Validation
3. Data Cleaning
4. Data Transformation
5. Customer Segmentation
6. KPI Preparation
7. Dashboard Data Structuring

---

## Data Import

The Databel Telecom Customer Churn dataset was imported into Power BI from a CSV/Excel data source.

The dataset contained customer-level information including:
- customer demographics,
- contract details,
- payment methods,
- monthly charges,
- account length,
- international usage,
- service interactions,
- and churn behavior.

---

## Data Type Validation

Data types were validated and corrected to ensure accurate analysis.

Examples included:
- numeric field validation,
- text formatting validation,
- percentage calculations,
- and categorical field verification.

Key validated fields:
- Monthly Charges
- Account Length
- Customer Service Calls
- Extra Data Charges
- Extra International Charges
- Churn Label

---

## Data Cleaning Activities

Several cleaning operations were performed during the preparation stage.

### Column Standardization
- Renamed columns for readability
- Standardized text formatting
- Improved business-friendly naming conventions

### Null & Data Quality Inspection
- Reviewed missing values
- Inspected inconsistent records
- Validated category consistency

### Data Structuring
- Organized fields into analytical categories
- Prepared fields for dashboard filtering
- Structured dimensions for business analysis

---

## Business-Oriented Transformations

Several calculated columns and segmentation fields were created to support business analysis.

### Churn Indicator Column

A binary churn flag was created to simplify KPI calculations and churn analysis.
