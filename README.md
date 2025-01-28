# Sales_Dashboard
Automated Power BI dashboard for AtliQ Hardware, offering real-time sales insights to support data-driven decisions. Includes MySQL integration, DAX queries, and visualizations of sales trends, top customers, products, and market performance. Identifies focus areas to boost recovery.
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AtliQ Hardware Sales Insights Dashboard</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            margin: 20px;
        }
        h1, h2, h3 {
            color: #2c3e50;
        }
        pre {
            background-color: #f4f4f4;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            overflow-x: auto;
        }
        code {
            font-family: Consolas, monospace;
            color: #e74c3c;
        }
        ul {
            margin: 10px 0;
            padding-left: 20px;
        }
    </style>
</head>
<body>
    <h1>AtliQ Hardware Sales Insights Dashboard</h1>

    <h2>Problem Statement</h2>
    <p>AtliQ Hardware supplies computer hardware and peripherals to clients across India. The Sales Director is facing challenges in tracking sales effectively in a dynamically growing market. Insights provided by regional managers are often verbal, biased, or sugar-coated, leading to frustration and a lack of clarity about the real business performance. While managers share multiple Excel files, analyzing them manually is time-consuming and inefficient.</p>

    <h2>Project Planning</h2>
    <h3>Purpose</h3>
    <p>To unlock hidden sales insights, automate the process of gathering data, and support the sales team with decision-making using a centralized dashboard.</p>

    <h3>Stakeholders</h3>
    <ul>
        <li>Sales Director</li>
        <li>Marketing Team</li>
        <li>Customer Service Team</li>
        <li>Data and Analytics Team</li>
        <li>IT Team</li>
    </ul>

    <h3>End Result</h3>
    <p>An automated dashboard that provides quick, up-to-date sales insights to support data-driven decision-making.</p>

    <h3>Success Criteria</h3>
    <ul>
        <li>Dashboard uncovering sales order insights with the latest data available.</li>
        <li>Sales team enabled to take better decisions and achieve 10% cost savings of total spend.</li>
        <li>20% reduction in manual data gathering time for sales analysts, enabling them to focus on value-added activities.</li>
    </ul>

    <h2>Database Information</h2>
    <h3>Database Used</h3>
    <p>MySQL</p>

    <h3>Tables</h3>
    <ul>
        <li><strong>Customers</strong>: Contains <code>Customer_code</code> (Primary Key), <code>customer_name</code>, <code>customer_type</code>.</li>
        <li><strong>Transactions</strong>: Contains <code>Product_code</code>, <code>market_code</code>, <code>order_date</code>, <code>sales_qty</code>, <code>sales_amount</code>, <code>currency_type</code>.</li>
        <li><strong>Products</strong>: Contains <code>Product_code</code>, <code>product_type</code> (Own Brand or Outsourced).</li>
        <li><strong>Markets</strong>: Contains <code>Market_code</code>, <code>Market_name</code> (City Names), <code>zone</code>.</li>
        <li><strong>Date</strong>: Contains <code>order_date</code>, <code>year</code>, <code>month</code>, <code>month_number</code>.</li>
    </ul>

    <h3>Data Processing</h3>
    <ul>
        <li>Focused only on Indian markets by removing data from other countries.</li>
        <li>Converted all amounts from INR to USD for consistency.</li>
        <li>Removed zero and negative values from <code>sales_qty</code>.</li>
    </ul>

    <h2>Dashboard Details</h2>
    <h3>Tabs</h3>
    <ul>
        <li><strong>Overview Tab</strong>: Displays sales amount and quantity by year, top 10 customers, top 10 products, and top 10 cities by sales quantity.</li>
        <li><strong>Insights Tab</strong>: Shows revenue and sales correlation year-wise and month-wise, along with sales insights by market region and product type.</li>
        <li><strong>Analysis Tab</strong>: Focuses on the comparison between current year and previous year sales, primarily for the analytics team.</li>
    </ul>

    <h3>DAX Queries Used in Power BI</h3>
    <pre><code>sales_qty = SUM('sales transactions'[sales_qty])
Revenue = SUM('sales transactions'[Normalized_USD_Sales_amount])

Previous_year_sales = 
VAR SelectedYear = MAX('sales date'[Year]) 
VAR Previous__Year = SelectedYear - 1 
VAR PreviousYearSales =
    CALCULATE(
        SUM('sales transactions'[sales_qty]),
        'sales date'[Year] = Previous__Year
    )
RETURN
    IF (
        ISBLANK(PreviousYearSales), 
        "Not Applicable", 
        PreviousYearSales
    )

Previous_year_sales_amount = 
VAR SelectedYear = MAX('sales date'[Year]) 
VAR Previous__Year = SelectedYear - 1 
VAR PreviousYearSales =
    CALCULATE(
        SUM('sales transactions'[Normalized_USD_Sales_amount]),
        'sales date'[Year] = Previous__Year
    )
RETURN
    IF (
        ISBLANK(PreviousYearSales), 
        "Not Applicable", 
        PreviousYearSales
    )

YoY_Percentage_Change = 
VAR SelectedYearSales = [Revenue]
VAR PreviousYearSales = [Previous_year_sales_amount]
RETURN
    IF(
        NOT(ISBLANK(PreviousYearSales)), 
        DIVIDE(SelectedYearSales - PreviousYearSales, PreviousYearSales, 0), 
        BLANK()
    )

YoY_Percentage_Change_QTY = 
VAR SelectedYearSales = [sales_qty]
VAR PreviousYearSales = [Previous_year_sales]
RETURN
    IF(
        NOT(ISBLANK(PreviousYearSales)), 
        DIVIDE(SelectedYearSales - PreviousYearSales, PreviousYearSales, 0), 
        BLANK()
    )
</code></pre>

    <h2>Insights</h2>
    <ul>
        <li>In 2018, sales peaked at 4.8 million USD but declined steadily afterward.</li>
        <li>The major decline is attributed to <strong>Product 318</strong>, which dropped from 400k units sold in 2018 to 80k units in 2020, and the <strong>Ahmedabad market</strong>, which fell from 600k units in 2018 to 100k units in 2020.</li>
        <li>There was an 18% decrease in sales amount and a 25% decrease in sales quantity compared to 2019.</li>
        <li><strong>Nixon</strong>, the fifth-largest vendor, has gradually reduced purchases. This needs investigation.</li>
        <li>Sales in Mumbai dropped by 50%, warranting further analysis.</li>
        <li>Focus areas: Ahmedabad and Mumbai markets, Nixon vendor, and Product 318 to drive sales recovery.</li>
    </ul>
</body>
</html>
