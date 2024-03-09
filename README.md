# INTRODUCTION
Successfully converting leads into sales is critical for long-term business growth and success in the highly competitive paper industry. 
This project focuses on the in-depth analysis of leads and sales data for Blunder Pifflin Paper Company as part of their continuous commitment to performance optimization. 
This project includes a thorough analysis of several factors, such as number leads generated, sales cycle lengths, performance in specific regions, product-specific insights, salesperson performance. 
My aim is to uncover valuable insights that will inform strategic decision-making and drive impactful outcomes.
The company's lead and sales data will be thoroughly examined in the documentation that follows, with a focus on identifying trends, defining key performance indicators. With the help of this analysis, I hope to offer practical suggestions that will improve lead conversion effectiveness, increase sales, and advance Blunder Pifflin Paper Company general success.

## ABOUT BLUNDER PIFFLIN PAPER COMPANY

Blunder Pifflin Paper Company was founded in the small town of Pifflinville, USA by the Pifflin siblings: Bob, Jane, and Tom. They were always a bit clumsy and accident-prone, but they were also incredibly ambitious and hardworking. When they were young, they would often help their father, who owned a small stationery store. As they grew older, they became determined to turn their family's business into a successful enterprise.

Despite their best efforts, things didn't always go as planned. Bob was known for spilling coffee on important documents, Jane was prone to tripping over her own feet and knocking over displays, and Tom had a habit of accidentally setting things on fire (he was a bit of a pyromaniac). Despite these mishaps, the Pifflin siblings refused to give up. They worked tirelessly to improve their products and services, and slowly but surely, their business began to grow.

Eventually, the Pifflin siblings renamed their company Blunder Pifflin Paper Company, in honor of all the silly mistakes they had made along the way. They continued to expand their business, eventually opening branches across the country. Despite its bumbling origins, Blunder Pifflin Paper Company became known for its high-quality products and excellent customer service. The Pifflin siblings were proud of what they had built, and they continued to make people laugh with their clumsy antics even as their company became a household name.

### ABOUT MR. GUPTA, SALES STRATEGIST AT BLUNDER PIFFLIN PAPER COMPANY
Mr. Gupta grew up in a small village in India. From a young age, he was fascinated by the art of sales and persuasion. He would often go door to door selling small trinkets and knick-knacks to his neighbors, and he quickly became known as the "sales wizard" of his village. As he grew older, Mr. Gupta became determined to turn his passion into a career. He worked hard to save up enough money to attend business school, upon graduation, he landed a job at Blunder Pifflin Paper Company as a sales strategist.

Mr. Gupta believes that analyzing the sales performance data of the organization should be the starting point for his guiding the direction of the sales strategy. 
Mr. Gupta then has discussions with all the important stakeholders such as regional sales heads, product managers and sales agents. These interactions generate the following observations and queries in the mind of Mr. Gupta:

1.	The organization has four sales departments for four regions. He wants to know which region contributes how much to the total sales.

2.	There are three main product categories at Blunder Pifflin. Once a lead is generated, the sales agents do not focus on any particular category as of now. Mr. Gupta thinks that whichever product has higher average order value should be pitched first. So, he wants to find out category wise average order value.

3.	The marketing team at Blunder Pifflin undertakes several marketing activities and creates monthly campaigns to generate leads. Mr. Gupta wants to find out the trend of monthly leads generated to be able to fine tune the marketing strategy for generating leads.

4.	There are 10 sales agents who are assigned the leads generated. These agents then get in touch with the respective persons and pitch them the products. All of them are also given half yearly sales targets. Mr. Gupta wants to classify these sales agents based on their performance and identify salesperson specific actions to increase the conversion rate of the leads.

# OBJECTIVES
This project aims to assist Mr. Gupta in obtaining insights by analysing the company's provided leads and sales data. The key business questions include:

1. What is the sales contribution of each region to the overall total?
   
2. Which product boasts the highest Average Order Value (AOV)?
   
3. How does the monthly leads generation trend evolve over time?
   
4. How well are sales agents performing in comparison to their assigned sales targets?


# THE DATA 

Mr. Gupta provided last 6 months sales data of leads, sales, and targets present in an Excel workbook.

The leads data consist of 9 columns and 796 rows. Below are the column and descriptions. 

```S.No.``` – serial number of the lead generated 

```Customer Name``` – Name of Clients

```Sector``` – The Sector of company they work in 

```City``` – The city they belong. 

```State``` – The state they belong. 

```Postal Code```- the postal code of their location 

```Region``` – The Region they belong.  

```Salesperson assigned``` – The Salesperson assigned to the clients.

```Lead Date``` – The date the lead was generated. 

![leads](https://github.com/dannieRope/Leads-Sales-Data-Analysis-Insights-Recommendations/assets/132214828/f1ad63a4-ec23-4317-a19a-3abbfa6f6cef)


The Sales data consist of 6 columns and 320 rows. Below are the columns and descriptions. 

```S.No.``` – Serial number of leads converted. 

```Customer Name``` – The name of the client who bought the product.

```Salesperson Assigned``` – The salesperson who closed the sales. 

```Category``` – The category the product belongs. 

```Order Date``` – The date the order was placed. 

```Sales``` – The amount of money spent on the transaction. 

![Salesdata](https://github.com/dannieRope/Leads-Sales-Data-Analysis-Insights-Recommendations/assets/132214828/d3d445ba-9366-4cae-9150-73069e659758)


The Target data consist of 2 columns and 10 rows. 
It has 10 rows representing the total number of sales agents also a target column which is the target value of all the sales agents for the 6-month sales period. 

![Targetdata](https://github.com/dannieRope/Leads-Sales-Data-Analysis-Insights-Recommendations/assets/132214828/ccdd2bb6-52d6-410f-9796-06dffc575e58)


# DATA CLEANING AND PREPARATION 
I carefully examined the data to check for null values, duplicates, spelling errors, and inaccurate data types and issues were found, suggesting that the data has already been cleaned.
To simplify the analysis, I organized the data into tables and established named ranges, enhancing the readability of formulas.
However, to effectively address the business issue, it became apparent that the leads data lacks certain columns in the sales data, including category, order date, and sales. To address this gap, I plan to utilize functions like VLOOKUP, XLOOKUP, and INDEX-MATCH. These functions will help join in the necessary information from the sales data into the leads data, ensuring a comprehensive dataset for a thorough analysis.
The formulas provided below are utilized to retrieve information from the sales table based on the customer name in the leads table. Additionally, two columns, "Conversion" and "Conversion Day," have been added to aid in the analysis.

1. **Category Formula:**
   - This formula uses the VLOOKUP function to find the category of the customer in the SalesData table. If an error occurs (indicating a non-match), it returns "Not Converted."

   ```excel
   Category = IFERROR(VLOOKUP([@[Customer Name]],SalesData[[#All],[Customer Name]:[Sales]],3,FALSE),"Not Converted")
   ```

2. **OrderDate Formula:**
   - XLOOKUP is employed here to fetch the order date from the SalesData table based on the customer name. If an error occurs, it returns "Not Converted."

   ```excel
   OrderDate = IFERROR(XLOOKUP([@[Customer Name]],SalesData[Customer Name],SalesData[Order date],,0),"Not Converted")
   ```

3. **Sales Formula:**
   - INDEX-MATCH is used to retrieve the sales data based on the customer’s name and the column header "Sales" in the SalesData table. If an error occurs, it returns "Not Converted."

   ```excel
   Sales = IFERROR(INDEX(SalesData,MATCH([@[Customer Name]],SalesData[Customer Name],0),MATCH(Data[[#Headers],[Sales]],SalesHeaders,0)),"Not Converted")
   ```

4. **Conversion Formula:**
   - This formula checks if the Category is "Not Converted" and assigns "No"; otherwise, it assigns "Yes."

   ```excel
   Conversion = IF([@Category] = "Not Converted","No","Yes")
   ```

5. **Conversion Day Formula:**
   - This formula calculates the number of days between OrderDate and Lead date. If an error occurs, it returns "Not Converted."

   ```excel
   Conversion Day = IFERROR([@OrderDate]-[@[Lead date]],"Not Converted")
   ```

Below is the image of the Data after cleaning and preparation, ready for analysis. 

![Data](https://github.com/dannieRope/Leads-Sales-Data-Analysis-Insights-Recommendations/assets/132214828/8b0a3c6e-9ffa-4b94-93bb-b7e3518dac4d)

# EXPLORATORY DATA ANALYSIS  

To answer the business questions, I created pivot tables to summarize and aggregate datasets. Pivot tables help consolidate data, calculate totals, averages, counts, and other summary statistics.

### QUESTION ONE 
**•	What is the sales contribution of each region to the overall total?**

![Sales by region](https://github.com/dannieRope/Leads-Sales-Data-Analysis-Insights-Recommendations/assets/132214828/bd5f6ddb-2f98-451a-8284-d3f4e06e27e1)


**INSIGHTS** 

1.	Western Region generated the highest number of sales $84,627.26 which is about 32% of the total the Eastern Region contributed around 30%, while the Central Region had the lowest sales at $47,561.88, constituting about 18% of the total.

   
### QUESTION TWO

**•	Which product boasts the highest Average Order Value (AOV)?**

![category by AOV](https://github.com/dannieRope/Leads-Sales-Data-Analysis-Insights-Recommendations/assets/132214828/1ad15308-c9cf-4d9a-b541-7d9934111f6a)


**INSIGHTS**

1.	Copy Paper and Letterhead emerge as the highest AOV, standing at $878.31 and $830.17 respectively. Envelopes exhibited the lowest AOV.
   
### QUESTION THREE

**•	How does the monthly leads generation trend evolve over time?**

![monthly leads](https://github.com/dannieRope/Leads-Sales-Data-Analysis-Insights-Recommendations/assets/132214828/34bb8bff-9305-4109-957f-8719c1dff8b7)


**INSIGHTS**

1.	Leads slightly decreased from January (134) to February (120) and then gradually increased through March, April, peaking in May (157), followed by a decline in June to 136.
   
### QUESTION FOUR

**•	How well are sales agents performing in comparison to their assigned sales targets?**

![Sales and Target](https://github.com/dannieRope/Leads-Sales-Data-Analysis-Insights-Recommendations/assets/132214828/c8d781bf-b75f-4e0a-bab9-49dce30530b3)


![scatter plot](https://github.com/dannieRope/Leads-Sales-Data-Analysis-Insights-Recommendations/assets/132214828/c4688978-1bab-4134-9aef-96c6348b70ea)



**INSIGHTS**

1.	Michael and Toby showcased the highest sales figures at $34,970.1 and $33,746.4, respectively, while Angela recorded the lowest sales of $18,800.8.
2.	All sales agents met their sales targets except for Pam and Jim.
3.	With a 40% conversion rate deemed satisfactory, all agents, excluding Angela, Toby, and Ryan, exhibited commendable conversion rates.








