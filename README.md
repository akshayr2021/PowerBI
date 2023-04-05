# Product Data Analysis
This project analyzes the launch strategies of a new product. The visuals created provide targeted customer segmentation & regions.

![report](https://user-images.githubusercontent.com/34497459/230132694-33290a39-6486-42d9-be48-ddfa65eaeea3.png)

## Dataset

The data contains information about products and its categories, employee details, regions, retail & sales etc.

> Custom table (DimTable & Important Measures) have been created to map existing data

1. **Dim Table** has date information within specified dates
   - To create this table, open the power query editor to create a blank query (DateQuery function) and later call this function while creating the Dim Table Check advanced editor in power query for DAX reference
2. **Imporant Measures**
   - ProductCategory TopPerformers = CALCULATE([Total Units Sold], FILTER(VALUES('Product'[EnglishProductName]),
IF(RANKX(ALL('Product'[EnglishProductName]),[Total Units Sold],,DESC)<=10,[Total Units Sold],BLANK())))
   - ProductSubCategory TopPerformeres = CALCULATE([Total Units Sold], FILTER(VALUES('Product Sub-Category'[Subcategory]),
IF(RANKX(ALL('Product Sub-Category'[Subcategory]), [Total Units Sold], , DESC)<=10,[Total Units Sold], BLANK())))
   - Total Retail Unit = SUM('RetailSales'[OrderQuantity])
   - Total Sales Unit = SUM('Sales Details'[OrderQuantity])
   - Total Units Sold = [Total Retail Unit] + [Total Sales Unit]

## Data Model/ Schema
> NOTE: When you load data into PowerBI it is possible that some relationships amongst the tables might be missing. Create new relations if needed.
> Check the model view tab in PowerBI to learn more

![model](https://user-images.githubusercontent.com/34497459/230136485-1036fffd-6fc3-49ab-8d6c-4a1b81acb136.png)

# Happy Learning!



