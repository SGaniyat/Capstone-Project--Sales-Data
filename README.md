
# Capstone Project: Sales Perormance Analysis Report

### Table of Content

<nav>
<ul>
<li><a href="#Section1">Overview</a></li>
<li><a href="#Section2">Using Microsoft Excel as a Data Analysis tool</a></li>
<li><a href="#Section3">Using SQL as a Data Analysis tool</a></li>
<li><a href="#Section4">Using Power BI as a Data Analysis tool</a></li>
<li><a href="#Section5">Result and Findings </a></li>

<h2 id="Section1">Overview</h2>
---
The project is to  analyze the sales performance of a retail store. Exploring sales data to uncover key insights such as top-selling products, regional performance, and monthly sales trends. The goal is to produce an interactive Power BI dashboard that highlights these findings.

### Data Analysis tools Used
- Microsoft Excel
- SQL
- Power BI



<h2 id="Section2">Using Microsoft Excel as a Data Analysis tool</h2>

Steps
<h3>1. Data cleaning </h3><br/>
    <ol type="i"> 
     <li>The Data was cleaned by delecting all duplicate of records. This was accheived by selecting the sheet and click Data-Data Tool- Remove Duplicate. 40,079 duplicate value was found and removed. Ehile 9921 Unique values remains. </li>
     <li> Create Revenue column by Multiplying Quantity by Unit price</li>
    </ol>

 <h3>2. Use Excel formulas to calculate metrics such as average sales per product and
total revenue by region.</h3><br/>

=AVERAGEIF(range,criteria[average_range])</h3><br/>
 =sUMIF((range,criteria[sum_range])</h3><br/>
 =Sum(Number 1,(Number......)

![image](https://github.com/user-attachments/assets/22b6b8f9-780d-49f5-90d9-19627fdd8eab)

![image](https://github.com/user-attachments/assets/f6d39e20-d7c7-4b15-b9c5-7e4b41dce9d9)


<h3>3. Data Analysis by Pivot table for data Summary</h3>  
     <ol type="i"> 
   <li>Select all data by Ctrl+ A and click on  Insert on the Ribbon</li>
  <li> Select PivotTable and TableRange. fill approprately. </li>
   <li>Create your data summary accordingly to the specification end result </li>
     </ol>

![image](https://github.com/user-attachments/assets/1c5c057f-b033-4b45-b9be-7a5c6492c535),

![image](https://github.com/user-attachments/assets/1e5e85ba-dde0-4132-a9e8-68e1cbfa0026)

![image](https://github.com/user-attachments/assets/b8df6d90-b52a-43bd-ba4b-6d3facf52097)

![image](https://github.com/user-attachments/assets/b816b4db-3783-45d1-bccb-fab9b525c070)

![image](https://github.com/user-attachments/assets/ba55fc34-a222-4bc4-ae66-64028b0a5aa9)

<h3>3.Create any other interesting report


  ![Sales Performance Dashboard](https://github.com/SGaniyat/Capstone-Project--Sales-Data/blob/f4912e82367c12f35d54bcb0370741e32cebbbbf/Sales%20Performance%20Dashboard%20Excel.png)




<h2 id="Section3">Using SQL as a Data Analysis tool</h2>
    
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
SELECT PRODUCT,SUM(Revenue) as Totalsales from[dbo].[LITA_Capstone Salesdata]
Group by Product
```
![Sales by Product Category](https://github.com/SGaniyat/Capstone-Project--Sales-Data/blob/6d2c9701bd267f084ff886de30df1a8845e39ccc/Revenue%20by%20Product%20(2).png)
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

<h2 id="Section4">Using Power BI as a Data Analysis tool</h2>
Steps
<ol type="i">

<li> From Canvas click on Get Data and import your data </li>
<li> Select data and click on Transform data.</li>
<li>Remove duplicate data by selecting your entire column and click 'delect duplicate rows.</li>
<li>Add Custom by clicking Add Custom and fill in the field accordingly to have your revenue coulumns.</li>
<li>Click on view to ensure your quality,distribution and profile are 100% accurate.</li>
<li>Close and apply.</li>
<li>Select Table view and add Mearsure for the Total revenue Value.</li>


</ol>


![Sales Performance Interactive Dashboard](https://github.com/user-attachments/assets/10892438-8c68-443b-ac0a-301eda4b0bd9)

<h2 id="Section5">Result and Finding </h2>

The analysis yielded the following quantitative insights;

Shoes is the highest revenue-generating product of N613,388 i.e 29.2% of the total revenue why Hat is the highest selling product of 15,929 Units followed by Shoes of 14,402 Pairs

The Product  varied slightly across regions: North: 2,481 transactions East: 2,483 transactions South: 2,480 transactions West: 2,477 transactions Observation: The number of transactions was fairly balanced, with the East region having a marginally higher count. This indicates consistent customer engagement across all regions.

The South region had the highest revenue contribution of 44.16% followed by East of 23.13% .
