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
    <ol type="i"> 
     <li>The Data was cleaned by delecting all duplicate of records. This was accheived by selecting the sheet and click Data-Data Tool- Remove Duplicate. 40,079 duplicate value was found and removed. Ehile 9921 Unique values remains. </li>
     <li> Create Revenue column by Multiplying Quantity by Unit price</li>
    </ol>

  
<h3>2. Data Analysis by Pivot table for data Summary</h3>  
     <ol type="i"> 
   <li>Select all data by Ctrl+ A and click on  Insert on the Ribbon</li>
  <li> Select PivotTable and TableRange. fill approprately. </li>
   <li>Create your data summary accordingly to the specification end result </li>
     </ol>

![image](https://github.com/user-attachments/assets/c3a02ba2-285b-402e-bbb6-97e2cffd98ac)

     
### Using SQL as a Data Analysis tool.
Steps
<ol type="i">
<li> Cleaning data in excel and save file in CSV.</li>
<li> Create Database on Management Studio </li>
    <strong>Create Capstoneproject table</strong>
<li> Import your file by Right click on your Database created and select task and click Import Flat file. follow the prompt accordingly to import your file.</li>
</ol>

```SQL
 select*from [dbo].[LITA_Capstone Salesdata] and click on Execute.
 ```
![Sales table](https://github.com/SGaniyat/Capstone-Project--Sales-Data/blob/6620cfd2d9aea15e16c98e2bd8f4203ad13312bc/Sales%20Table.png)
   The Anaysis done on the file and query are listed below;

1. The total sales for each product category.

```SQL
SELECT PRODUCT,SUM(Quantity) as Totalsales from[dbo].[LITA_Capstone Salesdata]
Group by Product
```
![Sales by Product Category](https://github.com/SGaniyat/Capstone-Project--Sales-Data/blob/5c7b25848672645c7253099e6e725577fe6890b7/Sales%20by%20Product.png)

2. Find the number of sales transactions in each region.
```SQL
Select Region,Count(OrderID) as  NO_SalesTransactions from [dbo].[LITA_Capstone Salesdata]
Group by Region
```
![Revenue by Region](https://github.com/SGaniyat/Capstone-Project--Sales-Data/blob/6620cfd2d9aea15e16c98e2bd8f4203ad13312bc/Sales%20traction%20by%20Region.png)

3. find the highest-selling product by total sales value.
```SQL
Select product, sum(revenue)from [dbo].[LITA_Capstone Salesdata]
Group by product
Order by 2 desc
```
![Highest selling product by revenue](https://github.com/SGaniyat/Capstone-Project--Sales-Data/blob/6620cfd2d9aea15e16c98e2bd8f4203ad13312bc/Highest%20Revenue.png)

4. calculate total revenue per product.
```SQL
select product, sum(Revenue) as RevenuebyProduct from [dbo].[LITA_Capstone Salesdata]
Group by Product
```
![Total Revenue by product](https://github.com/SGaniyat/Capstone-Project--Sales-Data/blob/6620cfd2d9aea15e16c98e2bd8f4203ad13312bc/Revenue%20by%20Product%20(2).png)

5. calculate monthly sales totals for the current year.
```SQL
SELECT orderdate, SUM(REVENUE) as Monthly_Sales from [dbo].[LITA_Capstone Salesdata]
where orderdate between '2024-01-01' and '2024-12-31'
Group by Orderdate 
Order by orderdate
```
![Monthly sales for Current year](https://github.com/SGaniyat/Capstone-Project--Sales-Data/blob/6620cfd2d9aea15e16c98e2bd8f4203ad13312bc/Monthly%20sales%20for%20current%20year.png)

6. find the top 5 customers by total purchase amount.
```SQL
select Top 5 Customer_id, Sum(Revenue) as Top_5_Customer_Sales from [dbo].[LITA_Capstone Salesdata]
Group by Customer_id
Order by 2 desc
```
![Top 5 Customer](https://github.com/SGaniyat/Capstone-Project--Sales-Data/blob/6620cfd2d9aea15e16c98e2bd8f4203ad13312bc/5%20top%20Customers.png)

7. calculate the percentage of total sales contributed by each region.
```SQL
With region as ( Select region,Sum(Revenue) as Percentage_Sales_Region from [dbo].[LITA_Capstone Salesdata]
group by region)
Select  region,(Percentage_Sales_Region * 100.0 / (Select sum(Revenue)from [dbo].[LITA_Capstone Salesdata])) 
as Salespercentage from Region
Order by 2 desc
```
![Percentage sales by region](https://github.com/SGaniyat/Capstone-Project--Sales-Data/blob/6620cfd2d9aea15e16c98e2bd8f4203ad13312bc/percentage%20of%20sales%20by%20region.png)

8. identify products with no sales in the last quarter.
```SQL
Select Region, (product) from [dbo].[LITA_Capstone Salesdata]
where Quantity < 0
and month >= 9
```
![Product with No sales in last quarter](https://github.com/SGaniyat/Capstone-Project--Sales-Data/blob/6620cfd2d9aea15e16c98e2bd8f4203ad13312bc/Product%20with%20no%20Sales.png)
