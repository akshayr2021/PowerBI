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
   `Check advanced editor in power query for reference`
> I have created measures in the below tables
7. Important Measures
   - Total Sales: Total Sales = SUMX(Sales, Sales[Order Quantity]*Sales[Unit Price]) 
   - Total Profit: Total Profit = [Total Sales] - [Total Cost]
   - Total Quantity: Total Quantity = SUM(Sales[Order Quantity])
   - Total Cost: Total Cost = SUMX(Sales, Sales[Order Quantity]*Sales[Total Unit Cost])
   - Profit Margin: Profit Margin = DIVIDE([Total Profit], [Total Sales], 0)
 8. 


