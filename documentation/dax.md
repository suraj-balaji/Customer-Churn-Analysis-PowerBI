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

```
Avg Customer Service Calls =
SUM('Databel - Data'[Customer Service Calls])
/
[No. of Customers]
```
