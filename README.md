# Data Analytics Project

## Overview
This project demonstrates skills in data acquisition, cleaning, transformation, and visualization Using advanced DAX functions in Power BI.

## Project Scope
- **Data Sources**:Sales Data
- **Tools Used**: Excel, Power BI, DAX
- **Key Features**: 
  - Data cleaning and transformation
  - Interactive dashboards
  - Advanced DAX calculations
  - Performance optimization

## Project Structure
- `data/` - Raw and cleaned data files
- `excel/` - Excel workbooks for data processing
- `powerbi/` - Power BI project file
- `documentation/` - Detailed documentation

## Data Model
Fact Tables:
Sales: Contains sales transactions with OrderID,Customer_name,Product Name,product description,gross product price,tax per product,quantity pucrchased,gross revenue,total tax, net revenue. About 54 rows.
Dimension Tables:

Countries: Has country name,country id,exchange ID. 5 rows
Purchases: Has Purchase ID,Order ID,last visitied. 54 rows.
Key Measures:

Sales in USD = DDCOLUMNS(
Sales,
    "Country Name", RELATED(Countries[Country]),
    "Exchange Rate", RELATED('ExchangeTable'[ExchangeRate]),
    "Exchange Currency", RELATED('ExchangeTable'[ExchangeCurrency]),
    "Gross Revenue USD", [gross_revenue] * RELATED('ExchangeTable'[ExchangeRate]),
    "Net Revenue USD", [net_revenue] * RELATED('ExchangeTable'[ExchangeRate]),
    "Total Tax USD", [total_tax] * RELATED('ExchangeTable'[ExchangeRate])
)

Exhange Table = DATATABLE("Exchange ID",INTEGER,"ExchangeRate",DOUBLE,"ExchangeCurrency",STRING,{{1,1.00,"USD"},{2,0.75,"GBP"},{3,0.85,"EUR"},{4,3.67,"AED"},{5,1.30,"AUD"}})

Calender Table=ADDCOLUMNS(
CALENDAR(DATE(2020, 1, 1), DATE(2023, 12, 31)),
"Year", YEAR([Date]),
"Month Number", MONTH([Date]),
"Month", FORMAT([Date], "MMMM"),
"Quarter", QUARTER([Date]),
"Weekday", WEEKDAY([Date]),
"Day", DAY([Date])
)
Relationships:

Purchases → Sales (one-one with both direction cross filter)
Country → Sales (Many-One with both cross filter)
Sales in USD → Sales (Many-One with both cross filter)

## Key Dashboards
1. Sales Overview = To find out the sales performace by country and by product.
2. Profit Overview = To analyse the profit yoy & by product

## How to Use
1. Open the Power BI file: `Sales_project.pbix`
2. Navigate between dashboards using the menu
3. Use slicers and filters to explore data
4. Hover over visuals for detailed tooltips

## Key Metrics & KPIs
Total Sales - Sum of all revenue
Total Quantity - 152 units purchased
Median Sale - $222.50 baseline
Total Loyalty Points - By country breakdown
Loyalty Points by Country - USA leads
Median Sale by Country - USA: 45.07%
Quantity by Product - 40+ products tracked
Stock Level - 14K units
Median Sale Trend - Sep-Oct 2023 analysis
Net Revenue USD by Product- Modular Sofa set has highest revenue i.e 928.36
Toal net revenue- 13.89k


## Technologies & Skills Demonstrated
- ✅ Data extraction from multiple sources
- ✅ Data cleaning and validation
- ✅ ETL process design
- ✅ Dimensional data modeling
- ✅ DAX calculations (measures, calculated columns)
- ✅ Interactive dashboard design
- ✅ Performance optimization
  
## Files Description
| File | Purpose |
|------|---------|
|Sales.xlsx | for Sales Data |
|Purchases.xlsx | Purchase Data |
|Sales_project.pbix | Main Power BI dashboard |

## Author
[Sunil Raul]

