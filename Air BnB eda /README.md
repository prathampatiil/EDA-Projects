#  Python EDA — Airbnb Listings in New York City

An Exploratory Data Analysis (EDA) project analyzing Airbnb listings across New York City neighbourhood groups. The analysis examines listing prices, room types, reviews, minimum-night requirements, availability, host listing counts, location, and other listing characteristics to identify important patterns and relationships within the dataset.

The project uses Python, Pandas, NumPy, Matplotlib, and Seaborn to perform data cleaning, statistical analysis, feature engineering, and visualization.

---

##  Table of Contents

- [🎯 Project Objective](#-project-objective)
- [📂 Dataset](#-dataset)
  - [Dataset Name](#dataset-name)
  - [Dataset Description](#dataset-description)
  - [Dataset Dimensions](#dataset-dimensions)
- [🛠️ Technologies & Tools](#️-technologies--tools)
- [🔄 EDA Workflow](#-eda-workflow)
- [💡 Key Insights](#-key-insights)
  - [Dataset-Level Insights](#dataset-level-insights)
  - [Pricing Insights](#pricing-insights)
  - [Neighbourhood Insights](#neighbourhood-insights)
  - [Room-Type Insights](#room-type-insights)
  - [Review Insights](#review-insights)
  - [Bed and Price Relationship](#bed-and-price-relationship)
  - [Feature Engineering Insight](#feature-engineering-insight)
- [📊 Important Visualizations](#-important-visualizations)
- [🧠 Analytical Findings](#-analytical-findings)
- [🎯 Final Conclusion](#-final-conclusion)
---

##  Project Objective

The objective of this project is to perform a systematic Exploratory Data Analysis of Airbnb listings in New York City.

The analysis focuses on understanding:

- How Airbnb listing prices are distributed.
- How prices vary across neighbourhood groups.
- How room type relates to listing price.
- Whether the number of reviews is associated with price.
- How minimum nights, reviews, reviews per month, and availability are distributed.
- Whether listing price has meaningful correlations with other numerical variables.
- How Airbnb listings are distributed geographically.
- Whether the dataset contains potential high-price observations and unusual values.

The goal is to transform raw Airbnb listing data into meaningful analytical findings that can support further statistical analysis, predictive modeling, and business intelligence applications.

---

##  Dataset

### Dataset Name
`datasets.csv`

### Dataset Description

The dataset contains Airbnb listing-level information for New York City.

The dataset includes information related to:

- Airbnb listings
- Hosts
- Neighbourhoods
- Geographic coordinates
- Room types
- Prices
- Minimum-night requirements
- Reviews
- Availability
- Host listing counts
- Ratings
- Bedrooms
- Beds
- Bathrooms
- Licensing information

### Dataset Dimensions

The original dataset contains:

- **20,770 rows**
- **22 columns**

After removing missing values:

- **20,736 rows**

After removing duplicate records:

- **20,724 rows**

For several price-based visualizations, the analysis uses a filtered dataframe containing listings where:


price < 1500

## Technologies & Tools

The following technologies and Python libraries were used in the analysis:

Python
Pandas
NumPy
Matplotlib
Seaborn
Jupyter Notebook

## 🔄 EDA Workflow

**01 → Data Loading**

**02 → Initial Data Inspection**

**03 → Dataset Structure Analysis**

**04 → Missing Value Analysis**

**05 → Duplicate Analysis**

**06 → Data Type Validation**

**07 → Data Cleaning**

**08 → Descriptive Statistics**

**09 → Univariate Analysis**

**10 → Bivariate Analysis**

**11 → Multivariate Analysis**

**12 → Correlation Analysis**

**13 → Price-Based Outlier Exploration**

**14 → Feature Engineering**

**15 → Key Findings**

**16 → Final Conclusions**

## Key Insights
### Dataset-Level Insights

The original dataset contains:

20,770 listings
22 columns

After missing-value and duplicate handling, the cleaned dataset contains:

20,724 listings
22 columns

The dataset contains five neighbourhood groups and four room types.

### Pricing Insights

Listing prices are strongly right-skewed.

The original:

Mean price = 187.71
Median price = 125
Maximum price = 100,000

The large difference between the mean and median indicates that higher-priced observations influence the average.

### Neighbourhood Insights

Within the price-filtered analysis dataframe, Manhattan has the highest mean listing price:

Manhattan: 204.15

The remaining neighbourhood groups are:

Brooklyn: 155.14
Queens: 121.68
Staten Island: 118.78
Bronx: 107.99

This indicates meaningful differences in average listing prices across neighbourhood groups.

### Room-Type Insights

The dataset contains:

Entire home/apt
Private room
Shared room
Hotel room

The grouped price visualization demonstrates differences in pricing across accommodation types and neighbourhood groups.

### Review Insights

The correlation between: number_of_reviews and reviews_per_month is approximately: 0.63

This is the strongest positive correlation in the displayed correlation matrix.

In comparison, the correlation between:

number_of_reviews

and:

price

is approximately:

-0.044

This indicates a very weak linear relationship between total reviews and price.

### Bed and Price Relationship

The correlation between:

beds

and:

price

is approximately:

0.42

This is the strongest positive correlation with price among the numerical variables analyzed.

This suggests that listings with more beds tend to have higher prices, although the relationship is not sufficiently strong to treat beds as the sole explanation for price variation.

### Feature Engineering Insight

The project creates:

price per bed

using:

price per bed = price / beds

This provides an additional metric for comparing listing prices while considering the number of beds.

The highest mean price per bed among the neighbourhood groups is observed in Manhattan.

## Important Visualizations
Price Distribution

The histogram shows the highly right-skewed distribution of Airbnb listing prices.

Price Boxplot

The boxplot highlights the central price distribution and potential high-price observations.

Price by Neighbourhood Group and Room Type

The grouped bar chart compares prices across neighbourhood groups and accommodation types.

Correlation Heatmap

The heatmap shows relationships among the numerical variables used in the analysis.

Pair Plot

The pair plot provides a multivariate view of numerical variable distributions and relationships.

Reviews vs Price

The scatter plot investigates the relationship between the number of reviews and listing price.

Geographical Distribution

The geographic scatter plot shows the spatial distribution of listings across neighbourhood groups.

### Analytical Findings

The EDA reveals several important characteristics of the Airbnb listings dataset.

### 1. Airbnb prices are highly skewed

Listing prices have a strong right-skewed distribution.

The median price is:

125

while the mean is:

187.71

The maximum price is:

100,000

This indicates that a relatively small number of expensive listings have a substantial effect on the mean.

### 2. Listing prices vary by neighbourhood

The price-filtered analysis shows differences in average listing prices across neighbourhood groups.

Manhattan has the highest mean price among the five neighbourhood groups, while the Bronx has the lowest mean price in the filtered analysis.

### 3. Room type is an important segmentation variable

The grouped price analysis demonstrates differences between room types within neighbourhood groups.

This suggests that room type should be considered when comparing listing prices.

### 4. Reviews and price have a weak linear relationship

The correlation between number of reviews and price is approximately:

-0.044

Therefore, the dataset does not show a strong linear relationship between these variables.

### 5. Reviews and reviews per month have a stronger relationship

The correlation between number of reviews and reviews per month is approximately:

0.63

This is considerably stronger than the relationship between reviews and price.

### 6. Beds have the strongest positive correlation with price

The correlation between beds and price is:

0.42

This is the strongest positive price correlation among the numerical variables included in the heatmap.

### 7. Geographic location provides useful context

The geographic visualization shows distinct spatial clustering across neighbourhood groups.

This supports the use of neighbourhood and location-related variables when investigating Airbnb pricing and listing characteristics.

### Final Conclusion

This Exploratory Data Analysis provides a structured examination of Airbnb listings across New York City.

The analysis shows that listing prices are highly right-skewed and contain substantial variation. The large difference between mean and median price demonstrates the influence of high-priced observations.

Neighbourhood group and room type both show meaningful differences in listing prices. In the price-filtered analysis, Manhattan has the highest mean listing price among the five neighbourhood groups.

The correlation analysis shows that beds has the strongest positive linear relationship with price, with a correlation of approximately 0.42.

In contrast, the number of reviews has a very weak linear relationship with price, with a correlation of approximately -0.044.

The strongest correlation in the displayed correlation matrix is between number_of_reviews and reviews_per_month, at approximately 0.63.
