# Online Retail Data Visualization & Interactive Dashboard

An end-to-end data visualization project exploring online retail transaction data using Python. The project focuses on data cleaning, exploratory data analysis, feature engineering, visual storytelling, and the development of an interactive dashboard for exploring sales performance and customer behaviour.

The analysis examines product revenue, purchasing patterns, customer activity, country-level performance, and time-based sales trends to turn raw transactional data into meaningful business insights.

## Project Overview

The project uses an Online Retail transaction dataset containing information such as invoice numbers, product descriptions, quantities, invoice dates, unit prices, customer IDs, and countries.

The workflow covers:

- Data loading and inspection
- Missing value analysis
- Duplicate removal
- Transaction cleaning
- Feature engineering
- Exploratory data analysis
- Sales and customer visualisation
- Interactive filtering
- Multi-chart dashboard development

The final dashboard allows users to dynamically explore the retail data by country, minimum revenue, and date range.

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Plotly
- ipywidgets
- Jupyter Notebook

## Data Preparation

Several data quality checks and cleaning operations were performed before beginning the analysis.

### Missing Values

The dataset was inspected for missing values, particularly in fields such as `Description` and `CustomerID`.

Rows with missing product descriptions were removed because a valid product description is required for product-level analysis.

### Duplicate Transactions

Duplicate records were identified and removed to prevent transactions from being counted more than once.

A total of **5,268 duplicate rows** were identified during the cleaning process.

### Invalid and Cancelled Transactions

Additional filtering was performed to remove records that could distort the sales analysis:

- Cancelled invoices beginning with `C`
- Negative quantities representing returns
- Zero or negative unit prices

After these cleaning operations, the dataset contained **524,878 valid sales transaction records** for analysis.

### Date Conversion

`InvoiceDate` was converted to a datetime format to support time-based analysis such as monthly trends, hourly purchasing behaviour, weekday analysis, and dashboard date filtering.

## Feature Engineering

Two important variables were created to support the analysis.

### TotalPrice

Revenue for each transaction line was calculated as:

`TotalPrice = Quantity × UnitPrice`

This variable was used throughout the project to analyse product, country, daily, and monthly revenue.

### DayOfWeek

The weekday was extracted from `InvoiceDate` to investigate purchasing behaviour throughout the week.

An additional `Hour` feature was later extracted to analyse transaction and revenue patterns throughout the day.

## Exploratory Data Analysis

The cleaned dataset was explored using descriptive statistics and multiple visualisation techniques.

### Top 10 Products by Revenue

A horizontal bar chart was used to identify the products generating the highest total revenue.

The analysis showed that revenue was concentrated among a relatively small number of products. `DOTCOM POSTAGE` generated the highest revenue, while several decorative and novelty products also appeared among the strongest performers.

### Revenue by Day of Week

Revenue was compared across different days of the week.

The analysis showed stronger purchasing activity during weekdays, particularly around **Tuesday and Thursday**, while Sunday generated considerably lower revenue.

This provides useful information for operational planning, promotions, and sales scheduling.

### Monthly Revenue Trend

A line chart was created to examine changes in total revenue over time.

This visualisation helps identify:

- Revenue growth and decline
- High-performing months
- Low-performing periods
- Seasonal sales patterns

These insights can support inventory and promotional planning.

### Revenue by Day and Hour

A heatmap was created to analyse revenue across both weekday and hour of day.

The results showed stronger activity during weekday working hours, particularly from Tuesday through Thursday, while purchasing activity declined considerably during later hours and weekends.

### Customer Purchase Frequency

Customer purchase frequency was analysed using a histogram.

The distribution indicates that many customers make relatively few purchases, while a smaller group of customers accounts for a much higher level of repeat activity.

This highlights the potential importance of customer retention and repeat-purchase strategies.

### Common Purchase Quantities

The most frequently occurring purchase quantities were analysed to understand typical order sizes.

The analysis showed that smaller quantities such as 1, 2, 6, and 12 units occurred frequently, suggesting that the dataset primarily represents retail-style purchases while still containing some larger orders.

## Interactive Dashboard

An interactive dashboard was developed using **ipywidgets** and **Matplotlib**.

Users can dynamically filter the dataset using three controls:

- **Country** – explore transactions for a selected country
- **Minimum Revenue** – remove transactions below a selected revenue threshold
- **Date Range** – analyse transactions within a chosen period

A custom `filter_data()` function applies the selected filters before updating the dashboard.

## Dashboard Visualizations

The interactive dashboard contains six visualisations arranged in a 2 × 3 layout:

1. **Revenue Over Time**  
   Displays changes in revenue across the selected period.

2. **Top 10 Products by Revenue**  
   Identifies the strongest revenue-generating products.

3. **Top Countries by Revenue**  
   Compares revenue performance across countries.

4. **Correlation Heatmap**  
   Examines relationships between `Quantity`, `UnitPrice`, and `TotalPrice`.

5. **Transactions by Hour of Day**  
   Shows when transaction activity is highest throughout the day.

6. **Top 10 Most Active Customers**  
   Identifies customers with the highest transaction activity.

All six visualisations update automatically when the dashboard filters are changed.

## Key Insights

The analysis highlights several useful patterns within the retail data:

- Revenue is concentrated among a number of high-performing products.
- Weekday sales activity is considerably stronger than weekend activity.
- Tuesday and Thursday show particularly strong revenue performance.
- Customer activity is strongest during typical daytime business hours.
- Most customers make relatively few purchases, while a smaller group demonstrates significantly higher repeat activity.
- Small purchase quantities occur frequently throughout the dataset.
- Time-based analysis reveals patterns that can support inventory, staffing, and promotional decisions.

## Project Structure

```text
OEWS-Data-Visualization/
│
├── OEWS_Data_Visualization.ipynb
└── README.md
