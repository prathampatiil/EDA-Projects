#  Sales & Profitability Analysis — Exploratory Data Analysis

An end-to-end **Exploratory Data Analysis (EDA)** project analyzing sales transactions to understand sales performance, profitability, customer behavior, product performance, regional patterns, discounts, and sales channels.

The project focuses on transforming raw transactional data into meaningful business insights using Python-based data analysis and visualization.

---

##  Business Problem

A retail business wants to understand its sales and profit performance across products, categories, regions, discounts, customers, and sales channels.

The analysis aims to identify:

- Which regions generate the highest sales and profit?
- Which product categories contribute most to revenue and profitability?
- Which products perform strongly?
- How do discounts relate to profitability?
- How do Online and Offline channels compare?
- How do quantity and unit price influence net sales?
- Are there unusual transactions or potential data-quality issues?
- Where are potential opportunities for improving sales and profitability?

---

##  Project Objectives

The main objectives of this project are:

1. Understand the structure and quality of the sales dataset.
2. Clean and prepare the data for analysis.
3. Analyze sales and profit distributions.
4. Analyze regional and category-level performance.
5. Compare Online and Offline sales channels.
6. Investigate relationships between sales, profit, quantity, price, and discounts.
7. Identify potential outliers using the IQR method.
8. Generate business-oriented insights.
9. Provide data-driven recommendations for further business analysis.

---

##  Dataset Overview

The dataset contains **1,000 sales transactions** and **13 original variables**.

### Dataset Dimensions

| Metric | Value |
|---|---:|
| Records | 1,000 |
| Original Columns | 13 |
| Period | 2025 |
| Regions | 5 |
| Cities | 16 |
| Categories | 5 |
| Products | 20 |
| Customers | 20 |
| Sales Channels | 2 |

---

##  Dataset Columns

| Column | Description |
|---|---|
| `order_id` | Unique order identifier |
| `order_date` | Date on which the order was placed |
| `customer_name` | Customer associated with the transaction |
| `city` | Customer/order city |
| `region` | Geographic sales region |
| `category` | Product category |
| `product_name` | Product purchased |
| `quantity` | Number of units purchased |
| `unit_price` | Product/transaction price |
| `discount_percent` | Discount applied to the transaction |
| `net_sales` | Net sales generated |
| `profit` | Profit generated from the transaction |
| `sales_channel` | Sales channel: Online or Offline |

Additional time-based features were created during preprocessing:

- `order_year`
- `order_month`
- `order_quarter`

---

## 🛠️ Tools & Technologies

The project was developed using:

- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Jupyter Notebook**
- **Git**
- **GitHub**

### Python Libraries

```text
pandas
numpy
matplotlib
jupyter
```

---

#  Analysis Workflow

The project follows an end-to-end data analysis workflow:

```text
Raw Dataset
     ↓
Data Understanding
     ↓
Data Type Handling
     ↓
Data Quality Assessment
     ↓
Data Cleaning
     ↓
Univariate Analysis
     ↓
Bivariate Analysis
     ↓
Multivariate Analysis
     ↓
Outlier Analysis
     ↓
Business KPI Analysis
     ↓
Key Business Insights
     ↓
Business Recommendations
```

---

#  1. Data Understanding

The dataset contains 1,000 unique sales transactions across multiple customers, cities, regions, product categories, products, and sales channels.

### Dataset Characteristics

- **1,000 transactions**
- **20 customers**
- **16 cities**
- **5 regions**
- **5 product categories**
- **20 products**
- **2 sales channels**
- Transactions from **2025**

### Initial Observations

- All 1,000 `Order_ID` values are unique.
- There are 344 unique order dates.
- North has the highest transaction frequency with 315 orders.
- Furniture is the most frequently occurring category with 228 transactions.
- Online is the dominant sales channel with 662 transactions.
- Study Table is the most frequently occurring product with 70 transactions.
- Quantity is concentrated around lower values, particularly 1–3 units.
- Net sales and profit show substantial variation.
- Some transactions generate negative profit.
- The dataset contains only 2025 records, so year-over-year growth cannot be evaluated.

---

#  2. Data Cleaning & Preparation

The following preprocessing steps were performed:

- Standardized column names.
- Removed leading and trailing whitespace from column names.
- Cleaned string-based categorical fields.
- Converted `order_date` into datetime format.
- Converted numerical columns into appropriate numeric data types.
- Created year, month, and quarter features.
- Checked uniqueness of order IDs.
- Investigated potential missing values.
- Investigated potential duplicate records.
- Examined numerical distributions.
- Identified potential outliers.

### Column Name Standardization

Column names were converted to lowercase and standardized using underscores.

Example:

```text
Order Date → order_date
Discount Percent → discount_percent
Net Sales → net_sales
Sales Channel → sales_channel
```

---

#  3. Data Type Handling

Appropriate data types were assigned to each variable.

| Column | Data Type |
|---|---|
| `order_id` | String |
| `order_date` | Datetime |
| `customer_name` | String |
| `city` | String |
| `region` | String |
| `category` | String |
| `product_name` | String |
| `quantity` | Integer |
| `unit_price` | Float |
| `discount_percent` | Float |
| `net_sales` | Float |
| `profit` | Float |
| `sales_channel` | String |
| `order_year` | Integer |
| `order_month` | Integer |
| `order_quarter` | String |

### Date Feature Engineering

The `order_date` column was converted to datetime format.

Additional features were created:

- `order_year` — transaction year
- `order_month` — transaction month
- `order_quarter` — transaction quarter

These features enable monthly and quarterly sales analysis.

---

# 📊 4. Data Exploration

## Categorical Variables

### Order ID

- 1,000 unique Order IDs are present across 1,000 records.
- Each transaction has a unique order identifier.
- No duplicate Order IDs were observed.

### Order Date

- 344 unique order dates are present.
- Multiple transactions can occur on the same date.
- All transactions belong to 2025.

### Customer

- There are 20 unique customers.
- Riya Kapoor is the most frequent customer with 68 transactions.

### City

- There are 16 unique cities.
- Jaipur has the highest transaction frequency with 73 orders.

### Region

- There are 5 regions.
- North has the highest transaction count with 315 orders.
- West follows with 253 orders.
- Central has the lowest transaction count with 110 orders.

### Category

- There are 5 product categories.
- Furniture is the most frequent category with 228 transactions.
- Grocery has the lowest transaction frequency with 160 transactions.

### Product

- There are 20 unique products.
- Study Table is the most frequently occurring product with 70 transactions.

### Sales Channel

- There are two sales channels: Online and Offline.
- Online accounts for 662 transactions.
- Offline accounts for 338 transactions.
- Online represents 66.2% of all transactions.

---

## Numerical Variables

### Quantity

- Quantity ranges from 1 to 10 units.
- Quantity 3 is the most common value with 229 transactions.
- Most transactions involve relatively small quantities.

### Unit Price

- There are 809 unique unit-price values.
- Unit prices show substantial variation.

### Discount Percentage

- There are 721 unique discount values.
- Discounts vary considerably across transactions.

### Net Sales

- All 1,000 transactions have unique net-sales values.
- Net sales show substantial transaction-level variation.

### Profit

- All 1,000 transactions have unique profit values.
- Profit ranges from negative values to high-profit transactions.
- The presence of negative profit indicates that some transactions resulted in losses.

---

#  5. Univariate Analysis

The following variables were analyzed individually to understand their distributions:

- Order frequency by month
- Order frequency by year
- Profit
- Net sales
- Discount percentage
- Unit price
- Quantity

## Key Insights

### Order Frequency by Month

Order volume varies across months, with relatively higher order frequency around July–August and lower order frequency around January–February.

The differences are moderate, suggesting relatively consistent order activity throughout the year.

### Order Frequency by Year

All transactions belong to 2025.

Therefore, year-over-year growth cannot be evaluated from the current dataset.

### Profit Distribution

Profit is strongly right-skewed.

Most transactions generate relatively lower profits, while a smaller number of transactions generate substantially higher profits.

### Net Sales Distribution

Net sales are strongly right-skewed, with most transactions concentrated at relatively lower sales values and a smaller number of high-value transactions.

### Discount Distribution

Discount percentages are concentrated mainly around moderate discount levels, with fewer transactions at very low or very high discount levels.

### Unit Price Distribution

Unit price shows substantial right-skewness.

Most transactions have relatively lower prices, while a smaller number have substantially higher prices.

### Quantity Distribution

Transaction quantities are concentrated at lower values, particularly around 1–5 units.

Higher quantities occur less frequently.

---

#  6. Bivariate Analysis

The following relationships were investigated:

- Profit vs Net Sales
- Profit vs Discount Percentage
- Net Sales vs Unit Price
- Net Sales vs Quantity

---

## Profit vs Net Sales

Profit generally increases as net sales increase, indicating a positive relationship between the two variables.

However, the spread becomes wider at higher sales values, suggesting that higher sales do not always result in the same level of profit.

### Business Interpretation

High-sales transactions should be investigated further to understand differences in profitability and margins.

---

## Profit vs Discount Percentage

Profit varies considerably across different discount levels.

The scatter plot alone does not establish a clear linear relationship between discount percentage and profit.

### Business Interpretation

Discount effectiveness should be evaluated using profit and profit margin across discount ranges rather than assuming that higher discounts directly increase or decrease profitability.

---

## Net Sales vs Unit Price

Net sales generally increase as unit price increases.

However, substantial variation exists at higher price levels.

### Business Interpretation

Unit price is an important contributor to transaction value, but quantity and discounting should also be considered.

---

## Net Sales vs Quantity

Net sales vary considerably across quantity levels.

Higher quantity does not necessarily result in proportionally higher sales because unit price and discounts also influence transaction value.

### Business Interpretation

Quantity should be evaluated together with unit price and discount percentage when analyzing transaction value.

---

#  7. Multivariate Analysis

Sales and profitability were analyzed across combinations of:

- Region
- Category
- Sales Channel

This allows the analysis to move beyond individual variables and examine how multiple business dimensions interact.

## Key Insights

### Region × Category × Channel

Sales and profitability vary depending on the combination of region, category, and sales channel.

Therefore, business performance should not be evaluated using only one dimension.

### Online Channel

Several high-value combinations in the analysis occur through the Online channel.

This indicates that Online transactions contribute significantly to high-value sales combinations.

### Home Appliances

Home Appliances shows strong sales and profitability in several region-channel combinations.

### Electronics

Electronics records some of the highest net-sales values in the analyzed combinations.

However, high sales do not automatically imply the highest profit.

### Furniture

Furniture contributes substantial sales and profit across multiple region-channel combinations.

---

#  8. Outlier Analysis

Potential outliers were identified using the **Interquartile Range (IQR)** method.

### IQR Formula

```text
IQR = Q3 − Q1

Lower Bound = Q1 − 1.5 × IQR

Upper Bound = Q3 + 1.5 × IQR
```

Observations outside the calculated boundaries were flagged as potential outliers.

## Outlier Results

| Variable | Potential Outliers | Percentage |
|---|---:|---:|
| Quantity | 55 | 5.5% |
| Unit Price | 110 | 11.0% |
| Discount Percentage | 3 | 0.3% |
| Net Sales | 102 | 10.2% |
| Profit | 78 | 7.8% |

## Outlier Interpretation

### Quantity

55 transactions were identified as potential outliers.

These may represent unusually large orders and should be investigated rather than automatically removed.

### Unit Price

110 transactions were identified as potential outliers.

These values may represent premium or high-priced products rather than incorrect data.

### Discount Percentage

Only 3 transactions were identified as potential outliers.

This indicates that discount values are generally concentrated within the expected range.

### Net Sales

102 transactions were identified as potential outliers.

These may represent genuine high-value transactions and can have a significant effect on total sales.

### Profit

78 transactions were identified as potential outliers.

These may represent unusually profitable transactions and should be investigated separately.

---

## Outlier Treatment

Potential outliers were **not automatically removed**.

An unusual observation is not necessarily an incorrect observation.

High sales, prices, quantities, or profits may represent legitimate business transactions.

Therefore, observations should only be removed when further investigation identifies them as:

- Data-entry errors
- Impossible values
- Invalid records
- Clearly incorrect measurements

---

#  9. Key Business Insights

## Sales Performance

- Net sales show substantial variation across transactions.
- A relatively small number of high-value transactions contribute significantly to total sales.
- Higher net sales generally correspond with higher absolute profit.

## Regional Performance

- North has the highest transaction volume with 315 orders.
- West follows with 253 orders.
- Transaction volume alone does not indicate which region generates the highest revenue or profit.

## Category Performance

- Furniture is the most frequently occurring category with 228 transactions.
- Clothing, Home Appliances, Electronics, and Grocery also contribute substantially to transaction volume.
- Category performance should be evaluated using both sales and profitability.

## Sales Channel

- Online accounts for 662 transactions or 66.2%.
- Offline accounts for 338 transactions or 33.8%.
- Online is the dominant channel based on transaction count.
- Channel profitability should be evaluated using total sales, total profit, and profit margin.

## Discounting

- Discount percentages show considerable variation.
- Only 3 discount observations were flagged as potential IQR outliers.
- Discount effectiveness should be evaluated using profit and margin rather than sales volume alone.

## Profitability

- Profit varies considerably across transactions.
- Some transactions result in negative profit.
- High-profit transactions should be examined to understand which products, categories, regions, and channels contribute to them.

---

#  10. Business Recommendations

Based on the exploratory findings, the following areas should be investigated further.

### 1. Analyze Regional Profitability

Compare:

- Total sales
- Total profit
- Average order value
- Profit margin

across regions.

### 2. Evaluate Category Profitability

Identify categories that generate:

- High sales
- High profit
- High sales but relatively low margins

### 3. Investigate High-Value Transactions

Analyze unusually high sales and profit observations to determine whether they represent:

- Premium products
- Bulk orders
- Specific regions
- Specific categories
- Specific sales channels

### 4. Evaluate Discount Effectiveness

Compare sales and profit margins across discount ranges to determine whether additional discounts generate sufficient business value.

### 5. Compare Sales Channels

Compare Online and Offline channels using:

- Transaction count
- Net sales
- Profit
- Average transaction value
- Profit margin

### 6. Analyze Product-Level Performance

Identify products with:

- High sales
- High profit
- Low profit despite high sales
- Unusually high discounts

---

#  11. Visualizations

The project contains visualizations covering:

### Distribution Analysis

- Profit distribution
- Net sales distribution
- Unit price distribution
- Quantity distribution
- Discount percentage distribution

### Time Analysis

- Monthly order frequency
- Yearly order frequency

### Relationship Analysis

- Profit vs Net Sales
- Profit vs Discount Percentage
- Net Sales vs Unit Price
- Net Sales vs Quantity

### Multivariate Analysis

- Region × Category × Sales Channel
- Net Sales and Profit by business dimensions

---

#  12. Project Structure

```text
sales-analysis/
│
├── data/
│   └── sales_dataset.csv
│
├── notebooks/
│   └── Sales_eda.ipynb
│
├── outputs/
│   └── figures/
│       ├── order_frequency_by_month.png
│       ├── order_frequency_by_year.png
│       ├── profit_distribution.png
│       ├── net_sales_distribution.png
│       ├── discount_percentage_distribution.png
│       ├── unit_price_distribution.png
│       ├── quantity_distribution.png
│       ├── profit_vs_net_sales.png
│       ├── profit_vs_discount_percentage.png
│       ├── net_sales_vs_unit_price.png
│       └── net_sales_vs_quantity.png
│
├── README.md
├── requirements.txt
└── .gitignore
```

---

#  13. How to Run the Project

## Clone the Repository

```bash
git clone <your-github-repository-url>
```

## Navigate to the Project

```bash
cd sales-analysis
```

## Install Dependencies

```bash
pip install -r requirements.txt
```

## Launch Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
notebooks/Sales_eda.ipynb
```

Run the notebook cells sequentially.

---

#  14. Requirements

Create a `requirements.txt` file containing:

```text
pandas
numpy
matplotlib
jupyter
```

---

#  15. Limitations

- The dataset contains only transactions from 2025.
- Year-over-year growth cannot be analyzed.
- The dataset contains a limited number of customers and products.
- High-value transactions may influence aggregate metrics.
- IQR-based outliers are potential outliers and are not necessarily data errors.
- Correlation or association between variables does not establish causation.
- Some business conclusions require additional KPI calculations before being considered definitive.

---

# 16. Future Improvements

The project can be extended with:

- Interactive Power BI dashboard
- Monthly and quarterly KPI tracking
- Customer segmentation
- RFM analysis
- Product profitability analysis
- Regional sales heatmaps
- Discount-to-margin analysis
- Customer Lifetime Value analysis
- Sales forecasting
- Sales-channel performance dashboard
- Automated reporting

---

# 17. Project Outcome

This project demonstrates an end-to-end approach to exploratory data analysis.

The workflow covers:

```text
Data Loading
     ↓
Data Understanding
     ↓
Data Cleaning
     ↓
Data Type Handling
     ↓
Data Exploration
     ↓
Statistical Analysis
     ↓
Data Visualization
     ↓
Relationship Analysis
     ↓
Multivariate Analysis
     ↓
Outlier Detection
     ↓
Business Insights
     ↓
Business Recommendations
```

The analysis provides a foundation for deeper investigation into sales performance, profitability, customer behavior, product performance, regional performance, and sales-channel effectiveness.


## Project Highlights

- 1,000 sales transactions analyzed
- 13 original variables
- 5 regions
- 5 product categories
- 20 products
- 20 customers
- 16 cities
- 2 sales channels
- Data cleaning and preprocessing
- Univariate analysis
- Bivariate analysis
- Multivariate analysis
- Outlier detection using IQR
- Business-oriented insights
- Data-driven recommendations
