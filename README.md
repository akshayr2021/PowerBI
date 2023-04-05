# Acquisition Data Analysis
This project compromises of 3 reports visualizing sales & profit trends

## Dataset & Tables Information
1. Customer Data
   - Customer Index: Mapped with the Sales table
   - Customer Names
2. **Metric Selection** includes metric index and metrics name
3. Product Name
   - Product Index: Mapped with the Sales table
   - Product Name
4. Regions
    - Region Index: Mapped with Sales table
    - Other columns include territory, city and country
5. **Sales** table has information about the shipping dates, order details, units costs & revenues generated

**I have created seperate manual tables containing measures**
6. **Dim Table** has date information within specified dates
   - To create this table, open the power query editor to create a blank query (DateQuery function) and later call this function while creating the Dim Table
   `Check advanced editor in power query for DAX reference`
> I have created measures using DAX in the below tables
7. Important Measures
   - Total Sales: Total Sales = SUMX(Sales, Sales[Order Quantity]*Sales[Unit Price]) 
   - Total Profit: Total Profit = [Total Sales] - [Total Cost]
   - Total Quantity: Total Quantity = SUM(Sales[Order Quantity])
   - Total Cost: Total Cost = SUMX(Sales, Sales[Order Quantity]*Sales[Total Unit Cost])
   - Profit Margin: Profit Margin = DIVIDE([Total Profit], [Total Sales], 0)
 8. Top Scenarios
    - Top 10 Customers: Top 10 Customers = CALCULATE([Total Sales], FILTER(VALUES('Customer Data'[Customer Names]),
IF(RANKX(ALL('Customer Data'[Customer Names]),[Total Sales],,DESC)<=10,[Total Sales], BLANK())))
    - Top 10 Products: Top 10 Products = CALCULATE([Total Sales], FILTER(VALUES('Product Data'[Product Name]),
IF(RANKX(ALL('Product Data'[Product Name]),[Total Sales],,DESC)<=10,[Total Sales], BLANK())))
9. Time Intelligence Measures
   - Performance Last Year: Performance LY = CALCULATE([Total Profit], PREVIOUSYEAR('Dim Table'[Date]))
   - Profit Last Year: Profit Last Year = CALCULATE([Total Profit], SAMEPERIODLASTYEAR('Dim Table'[Date]))
   - Profit Moving Average: Profit Moving Average = AVERAGEX(
    FILTER(ALLSELECTED('Dim Table'),
    'Dim Table'[Date]<=MAX('Dim Table'[Date])),
    [Total Profit])
   - Sales 2 years ago: Sales 2 yrs ago = CALCULATE([Total Sales], PARALLELPERIOD('Dim Table'[Date], -2, YEAR))
   - Sales Last Year: Sales Last Year = CALCULATE([Total Sales], SAMEPERIODLASTYEAR('Dim Table'[Date]))
   - Sales Moving Average: Sales Moving Average = AVERAGEX(
    FILTER(ALLSELECTED('Dim Table'),
    'Dim Table'[Date]<=MAX('Dim Table'[Date])),
    [Total Sales])
    
 ## Data Model/ Schema
 



