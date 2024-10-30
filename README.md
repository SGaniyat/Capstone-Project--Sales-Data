# Capstone-Project--Sales-Data

### Project Overview
---
The project is to  analyze the sales performance of a retail store. Exploring sales data to uncover key insights such as top-selling products, regional performance, and monthly sales trends. The goal is to produce an interactive Power BI dashboard that highlights these findings.

### Data Analysis tools Used
- Microsoft Excel
- SQL
- Power BI

## Using Microsoft Excel as a Data Analysis tool
Steps
<h3>1. Data cleaning </h3><br/>
    <ol type="A"> 
     <li>The Data was cleaned by delecting all duplicate of records. This was accheived by selecting the sheet and click Data-Data Tool- Remove Duplicate. 40,079 duplicate value was found and removed. Ehile 9921 Unique values remains. </li>
     <li> Create Revenue column by Multiplying Quantity by Unit price</li>
    </ol>

  
<h3>2. Data Analysis by Pivot table for data Summary</h3>  
     <ol type="A"> 
   <li>Select all data by Ctrl+ A and click on  Insert on the Ribbon</li>
  <li> Select PivotTable and TableRange. fill approprately. </li>
   <li>Create your data summary accordingly to the specification end result </li>
     </ol>
     
### Using SQL as a Data Analysis tool.
---Steps
 1) Cleaning data in excel and file file in CVS.
 2) Create Database on Management Studio
    Create table Capstoneproject
3) Import your file by Right click on your Database created and select task and click Import Flat file. follow the prompt accordingly to import your file.
4) Write query to view your table content by
   select*from [dbo].[LITA_Capstone Salesdata] and click on Execute.

   The Anaysis done on the file and query are lsted below;

.............. 1) The total sales for each product category.
```SQL
Select Product ,SUM(Revenue) as Totalsales from[dbo].[LITA_Capstone Salesdata]
Group by Product
```

.............. 2) Find the number of sales transactions in each region.
```SQL
Select Region,Count(OrderID) as  NO_SalesTransactions from [dbo].[LITA_Capstone Salesdata]
Group by Region
```

............. 3) find the highest-selling product by total sales value.
```SQL
Select product, sum(revenue)from [dbo].[LITA_Capstone Salesdata]
Group by product
Order by 2 desc
```
..............4)calculate total revenue per product.
```SQL
select product, sum(Revenue) as RevenuebyProduct from [dbo].[LITA_Capstone Salesdata]
Group by Product
```

................5) calculate monthly sales totals for the current year.
```SQL
SELECT orderdate, SUM(REVENUE) as Monthly_Sales from [dbo].[LITA_Capstone Salesdata]
where orderdate between '2024-01-01' and '2024-12-31'
Group by Orderdate 
Order by orderdate
```


.................6)find the top 5 customers by total purchase amount.
```SQL
select Top 5 Customer_id, Sum(Revenue) as Top_5_Customer_Sales from [dbo].[LITA_Capstone Salesdata]
Group by Customer_id
Order by 2 desc
```
...................7)calculate the percentage of total sales contributed by each region.
```SQL
With region as ( Select region,Sum(Revenue) as Percentage_Sales_Region from [dbo].[LITA_Capstone Salesdata]
group by region)
Select  region,(Percentage_Sales_Region * 100.0 / (Select sum(Revenue)from [dbo].[LITA_Capstone Salesdata])) 
as Salespercentage from Region
Order by 2 desc
```
 ....................8)identify products with no sales in the last quarter.
```SQL
Select Region, (product) from [dbo].[LITA_Capstone Salesdata]
where Quantity < 0
and month >= 9
```
