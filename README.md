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

Select Region,Count(OrderID) as  NO_SalesTransactions from [dbo].[LITA_Capstone Salesdata]
Group by Region

............. 3) find the highest-selling product by total sales value.

Select product, sum(revenue)from [dbo].[LITA_Capstone Salesdata]
Group by product
Order by 2 desc
