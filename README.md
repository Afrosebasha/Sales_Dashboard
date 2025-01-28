# Sales_Dashboard
Automated Power BI dashboard for AtliQ Hardware, offering real-time sales insights to support data-driven decisions. Includes MySQL integration, DAX queries, and visualizations of sales trends, top customers, products, and market performance. Identifies focus areas to boost recovery.

## Problem Statement
AtliQ Hardware is a company that supplies computer hardware and peripherals to many clients across India. The Sales Director of the company is currently facing challenges due to the dynamically growing market. He struggles to track sales performance accurately and obtain actionable insights.

The primary issue is that the Sales Director relies on verbal communication with regional managers to gather updates. These conversations often lack clarity, as managers tend to paint overly optimistic pictures of the sales situation. Some managers may unintentionally sugarcoat facts, while others might misreport data.

When asked for numerical data, the regional managers share multiple Excel files, which are tedious and time-consuming for the Sales Director to analyze. Frustrated by declining sales and the lack of reliable insights, the Sales Director is looking for a solution that provides a simple, clear, and actionable view of the company’s sales performance. He envisions a dashboard that presents real-time data and enables data-driven decision-making to grow the business.

## Project Plan
### Purpose
To unlock sales insights that were previously hidden, provide decision support for the sales team, and automate processes to reduce manual time spent on data gathering.

### Stakeholders
- Sales Director  
- Marketing Team  
- Customer Service Team  
- Data and Analytics Team  
- IT Team  

### End Result
An automated dashboard providing quick and accurate sales insights to support data-driven decision-making.

## Success Criteria
- The dashboard uncovers sales order insights with the latest available data.
- The sales team can make better decisions, leading to a **10% cost savings** on total spend.
- Sales analysts save **20% of their time** previously spent on manual data gathering, allowing them to focus on value-added activities.

## Data Specifications
- **Database Used:** MySQL  
- **Coding Tool:** MySQL Workbench  

### Tables Used:
#### Customers
- `Customer_code` (Primary Key)
- `Customer_name`
- `Customer_type`

#### Transactions
- `Product_code`
- `Market_code`
- `Order_date`
- `Sales_qty`
- `Sales_Amount`
- `Currency_type`

#### Products
- `Product_code`
- `Product_type` (own brand or outsourced)

#### Markets
- `Market_code`
- `Market_name` (city names)
- `Zone`

#### Date
- `Order_date`
- `Year`
- `Month`
- `Month_number`

## Data Processing
- Filtered data to focus on the **Indian market** by removing entries from other countries.
- Converted all sales amounts to **USD** for consistency.
- Removed **zero and negative values** from `sales_qty` for accurate analysis.

## Dashboard Overview
The dashboard has three main tabs:

### Overview Tab
- Displays total sales amount by year, sales quantity by year, top 10 customers, top 10 products, and top 10 cities based on sales quantity.

### Insights Tab
- Shows the correlation between revenue and sales, both year-wise and month-wise.
- Breaks down sales amount and quantity by market region and product type.

### Analysis Tab
- Focused on technical metrics for the analytics team.
- Includes a year-over-year (YoY) comparison of current-year sales and previous-year sales.

## Key Insights
### Sales Trends
- Sales peaked in **2018** at approximately **4.8 million USD** but have shown a steady decline since.

### Top Product Decline
- **Product 318**, which sold **400,000 units** in **2018**, only sold **80,000 units** in **2020**, significantly contributing to the overall decline.

### Regional Issues
- **Ahmedabad**, the third-largest market in **2018** (**600,000 units sold**), dropped to just **100,000 units in 2020**.
- **Mumbai** experienced a **50% sales reduction** in the following year.

### Vendor Concerns
- **Nixon**, the fifth-largest vendor, has gradually reduced purchases. This issue requires investigation.

### YoY Decline
- **Sales amount decreased by 18% compared to 2019**.
- **Sales quantity dropped by 25% compared to 2019**.

## Recommendations
- Focus on **Ahmedabad** and **Mumbai** markets to recover lost sales.
- Promote **Product 318** to regain its previous performance.
- Investigate and address the declining purchases from **Nixon**.

By addressing these areas, the company can achieve a noticeable improvement in sales performance.
