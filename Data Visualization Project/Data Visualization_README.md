
# Power BI Project

Power BI is an interactive data visualization software by Microsoft with a primary focus on business intelligence.
Business Intelligence is a broad term which combines business analytics, data mining, data visualization, data tools and infrastructure, and best practices to help organizations make more data-driven decisions.


## The Project Itself: SaGo's Coffee House

SaGo Coffee House or just Sago is a intercity coffee house based in New York & having various Coffee Houses across the city under different store name

## The Data Itself

### Lookup Data or Dimension Tables

    1.Calendar
    2.Customer Lookup
    3.Employee Lookup
    4.Product Lookup
    5.Store Lookup
    6.4-5-4 Calendar

### Data Table or Fact Table

    1.Sales by Store
    2.Food Inventory



 - [Data and Lookup Files](https://drive.google.com/drive/folders/15NH9m4X0W-3cSlvA-Tw-8Sxu4vFoDadg?usp=sharing)
 - 
 - [Power BI Project File](https://drive.google.com/file/d/1NRVhatJC_H0_sO1U3_bIAPiQGz-ptwKT/view?usp=sharing)
 - 
 - [Project Images PDF](https://drive.google.com/file/d/1lAeXLOM3n0EbS1GB2d7--bKgpLfYHEMV/view?usp=sharing)


Step1: Download all the above tables(.csv) files & store in one folder

Step2: Open the project .pbix file or create a new .pbix file.

Step3: Once .pbix project file is opened, go to 

Home Ribbon --> Transform Data --> Data Source Setting -->Change Source. Update the file path for individual .csv files


**Data Model is ready to serve us Amazing Insights.**







## The Actual Insights - Just the Most Important Insights & Unique Power BI Functions are used below.

### Page 1: All about Customer Sales(Revenue) and Orders. Inbuild functions used: **CALCULATE & FILTER**, **SUMX**, **ALL**, **COALESCE**, **DISTINCTCOUNT**

    **Summary**:
    1.All brief over view of Revenue-Cost = Profit

    2.Measures based on Transaction Date, Customer Sales,
    Total Orders & Sold(Order Volume), Order by Females etc. 

    3.A Donut Chart: Quantity Sold to Female Customer over the Year

![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/Data%20Visualization%20Project/Screenshots/1.PNG)


### Page 2: All about Products and Store Wise Sales. Inbuild functions used: **REMOVEFILTERS**,**KEEPFILTERS**



    **Summary**:
    1.Filtered by Store_ID, Profit and Revenue Product Wise

    2.Revenue based on Store 3 based on Category Whole Beans/Teas Sales

    3.Product Group split by Store ID and getting individual Sales for all 3 Stores along 
    with each store Revenue Contribution
    
![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/Data%20Visualization%20Project/Screenshots/2.PNG)
### Page 3: Monthly Targets & Top Products.



    **Summary**:
    1.Using Gauge Chart and Card to get insights regarding Monthly Order Target,Revenue,
    Top Item Sold,Top Profitable Item 

    2.Matrix value to show Product based on Revenue, Previous Month Revenue, Profit etc



![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/Data%20Visualization%20Project/Screenshots/3.PNG)

### Page 4: Product Count & Quantity Sold. Inbuild functions used: **COUNTROWS**,**SELECTEDVALUE**



    **Summary**:
    1.Counting Product & getting Quantity Sold based on Retail Price

    2.A Stacked Bar Chart based on Product Category and Product based on Customer Sales


![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/Data%20Visualization%20Project/Screenshots/4.PNG)

### Page 5: DrillDown by Product and Dynamic Charts.


    **Summary**:
    1.Using KPI Charts to know Highest Revenue/Orders Trend by Previous Month Revenue/Orders

    2.CARDS showing Top Revenue/Orders/Baked/Sold by Top Customer 

    3.Area Chart to show to trend

![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/Data%20Visualization%20Project/Screenshots/5.PNG)

### Page 6: Top Sales & Customers. Inbuild functions used: **ALLEXCEPT**



    **Summary**:
    1.Customer Sales based on Product Group + Product
    
    2.Top 10 Customers based on Product Group Selected and % of Store Level Sales

    3.Donut Chart on Gender and High/Low Value Customers


![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/Data%20Visualization%20Project/Screenshots/6.PNG)


### Page 7: Top Customers by.



    **Summary**:
    1.Finding Top Customer based on Revenue, Profit, Orders, Sold

    2.Using Decomposition Tree to get further detailed Insights


![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/Data%20Visualization%20Project/Screenshots/7.PNG)

### Page 8: Quantity Baked Vs. Sold. Inbuild functions used: **ALLSELECTED**



    **Summary**:
    1.Quantity Baked Vs Sold based on Customer Sales along with % of Total Baked & Sold
    2.Line & Clustered Column Chart to reveal Total Baked and Sold based on Month & Year along with % Total Baked and Sold


![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/Data%20Visualization%20Project/Screenshots/8.PNG)

### Page 9: Revenue Lost & Recurring Customers. Inbuild functions used: **SUMMARIZE**, **INTERSECT**



    **Summary**:
    1.Using Summarize to create a table wherein quantity baked != quantity sold & generate revenue loss
    2.Pie Chart tells us that quantity unsold is far more than quantity baked
    3.Using Intersect to find Recurring Customers in the year 2018 for Week 45 who return to Purchase in the Week 46 aswell &
        finding Profit & Revenue generated by them
    4.Donut Chart for Recurring Customers tells more on Profit & Revenue generated by them

![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/Data%20Visualization%20Project/Screenshots/9.PNG)
![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/Data%20Visualization%20Project/Screenshots/9.1.PNG)
![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/Data%20Visualization%20Project/Screenshots/9.2.PNG)

### Page 10: Sales by Employees. Inbuild functions used: **USERELATIONSHIP**, **CROSSFILTER**, **VALUES**



    **Summary**:
    1.We want to find quantity Baked even before it is Sold, we use USERELATIONSHIP to temporarily change the connection to explore some uncharted territory
    2.Using Crossfilter to change "1 --> Many" Unidirectional to "1 <--> Many" Bidirectional

![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/Data%20Visualization%20Project/Screenshots/10.PNG)

### Page 11: Average Order Values.



    **Summary**:
    1.Using TreeMap to DrillDown from product group --> product category --> product type --> product
    2.Using Crossfilter to access customer id both ways and further Average Order Values


![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/Data%20Visualization%20Project/Screenshots/11.PNG)


### Page 12: TREATAS Goals. Inbuild functions used: **TREATAS**,**DATATABLE** ,**UNION**



    **Summary**:
    1.Creating 2 tables using Datatables to create a Goal values for various Products for the Month of March & April 2019
        & using UNION to Append above 2 tables
    2.Using TreatAS to find common values of year & month between above Union table above and our calendar table
    3.Lastly, finding Product % to Goal value using Pie Chart


![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/Data%20Visualization%20Project/Screenshots/12.2.PNG)
![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/Data%20Visualization%20Project/Screenshots/12.1.PNG)

### Page 13: CONCATENATEX Universe. Inbuild functions used: **CONCATENATEX**,**HASONEVALUE**



    **Summary**:
    1.Dynamic Card which changes values based on Filters used
    2.% of Total Sales using ALL, ALLEXCEPT
    3.Dynamic Card which tells which Employee contributed how much Sales

![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/Data%20Visualization%20Project/Screenshots/13.PNG)

### Page 14 & 15: Moving Averages based on Revenue & Profit. Inbuild functions used: **AVERAGEX**



    **Summary**:
    1.Finding Avg Sales & Profit using AVERAGEX.
    2.Calculating Moving Averages based on Customer Sales and Profit 
        using Line & Clustered Column Chart & Area Chart respectively.
    
![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/Data%20Visualization%20Project/Screenshots/14.1.PNG)
![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/Data%20Visualization%20Project/Screenshots/15.1.PNG)

### Page 16: Rank of Customers & Product. Inbuild functions used: **RANKX**,**MROUND**



    **Summary**:
    1.Knowing Product category rank based on Customer Sales
    2.Top 5 Products based on Profit using Rankx

![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/Data%20Visualization%20Project/Screenshots/16.PNG)

### Page 17: Customer Sales Last Quarter. Inbuild functions used: **PARALLELPERIOD**,**PREVIOUSQUARTER**,**SAMEPERIODLASTYEAR**,**DATEADD**



    **Summary**:
    1.Pie Chart denoting Sales based on Weekdays Vs. Weekends
    2.Using Various Time Function to get Revenue based on different Parameters

![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/Data%20Visualization%20Project/Screenshots/17.PNG)

### Page 18: % Change Month over Month & Year over Year. 


    **Summary**:
    1.Matrix View to see % change based on Month to Month & Year to Year using above mentioned Time Functions
    2.Using Stacked Area Chart to get a better Revenue glance based on different % change

![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/Data%20Visualization%20Project/Screenshots/18.PNG)

### Page 19 & 20: % Change Week over Week, Quarter, Monthly, Yearly Sales 


    **Summary**:
    1.Matrix view to draw insights based on Week, Quarter, Month and Year

![](https://github.com/saks0106/Data_Analyst_Projects/blob/master/Data%20Visualization%20Project/Screenshots/1920.PNG)




## Feedback

If you have any feedback, please reach out to us at sakshemgotekar@gmail.com

