# Immi_Sales & Workforce Performance Dashboard - Power BI
## Project Overview
This project focuses on analyzing sales performance, employee productivity, and year-over-year growth using a structured Power BI data model.
The objective was to build an interactive dashboard that helps management:
* Track overall sales performance
* Identify top-performing employees and branches
* Analyze product performance
* Compare Year-over-Year (YoY) sales growth
This project demonstrates my ability to combine data modeling, DAX calculations, and business analysis to generate actionable insights.

### Data Source
The dataset was self-prepared in Excel for learning purpose only and structured into multiple related tables.

#### EmployeesImmi
Contains employee-level data:
* Emp_ID
* Emp_Name
* Position
* Department
* PhoneNumber
* EmailID
* JoiningDate
* Salary
* Branch

#### SalesImmi
Transactional sales dataset:
* Emp_ID
* Sale
* Cust_ID
* Product
* Country
* Gender
* Age
* Date

#### LeadsImmi
Customer lead tracking:
* Cust_ID
* Cust_Name
* Phone_No
* Lead_type
* Lead_status

#### DimDate
Calendar table created to enable time intelligence analysis.

### Data Model
The model follows a star schema structure:
* EmployeesImmi (1) → (n) SalesImmi
* LeadsImmi (1) → (n) SalesImmi
* DimDate (1) → (n) SalesImmi

This structure enables:
* Efficient filtering
* Time intelligence calculations
* Cross-table aggregations

### Key KPIs & DAX Measures
#### Total Sales
```
Sale Total = SUM(SalesImmi[Sale])
```
#### Average Sales Per Sales Employee
```
AvgSalePerEmployee =
DIVIDE(
    [Sale Total],
    CALCULATE(
        COUNT(EmployeesImmi[EmailID]),
        FILTER(EmployeesImmi,
            EmployeesImmi[Department] = "Sales")
    )
)
```
#### Year-over-Year Sales
```
YoY Sales =
CALCULATE(
    [Sale Total],
    SAMEPERIODLASTYEAR(DimDate[Date])
)
```

### Sales Ranking & Top Performers
* RANKX used for employee sales ranking
* Top3Flag created to dynamically identify top 3 performers
* Branch-wise top performer identified using ALLEXCEPT
* TOPN used to identify highest-selling product

This demonstrates strong understanding of: Context transition, Ranking logic, Time intelligence functions

### Dashboard Highlights
#### Overview
* Total Sales KPI
* Avg sale per employee
* Top product
* Top performer
* YoY comparison
* Sales trend
<img src="1. Overview.png" width="800">

#### Employee Performance 
* Sales ranking
* Top 3 performers
* Branch wise sale
* Position wise sale
<img src="2. Employee Performance.png" width="800">

#### Product Insights
* Top-selling product
* Country-level distribution
<img src="3. Product Performance.png" width="800">

#### Key Business Insights
* Identified top-performing branches and employees using ranking logic
* Determined product contributing highest revenue
* Measured YoY growth trends using time intelligence
* Evaluated sales department efficiency through average sales metric

#### Tools & Technologies Used
* Power BI Desktop
* Power Query
* DAX
* Excel (Data preparation)
* Data Modeling (Star Schema Design)

#### Skills Demonstrated
* Data modeling & relationship management
* DAX measure creation
* Ranking & performance analytics
* Time intelligence (YoY calculations)
* Business KPI development
* Dashboard design & storytelling

#### Future Enhancements
* Add drill-through pages for employee-level deep dives
* Introduce forecast modeling
* Add Row-Level Security (RLS)

### Why This Project Matters
This dashboard reflects my ability to:
* Translate business problems into analytical models
* Build structured data relationships
* Develop meaningful KPIs
* Deliver actionable insights for management
It combines technical Power BI expertise with business-oriented thinking, aligning with real-world organizational reporting needs.
