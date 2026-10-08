#  Python EDA — Airbnb Listings in New York City

An Exploratory Data Analysis (EDA) project analyzing Airbnb listings across New York City neighbourhood groups. The analysis examines listing prices, room types, reviews, minimum-night requirements, availability, host listing counts, location, and other listing characteristics to identify important patterns and relationships within the dataset.

The project uses Python, Pandas, NumPy, Matplotlib, and Seaborn to perform data cleaning, statistical analysis, feature engineering, and visualization.

---

##  Table of Contents

- [🎯 Project Objective](#-project-objective)
- [📂 Dataset](#-dataset)
- [🛠️ Technologies & Tools](#️-technologies--tools)
- [🔄 EDA Workflow](#-eda-workflow)
- [🔍 1. Data Loading & Initial Exploration](#-1-data-loading--initial-exploration)
- [🧹 2. Data Cleaning & Preprocessing](#-2-data-cleaning--preprocessing)
- [📊 3. Descriptive Statistics](#-3-descriptive-statistics)
- [📈 4. Univariate Analysis](#-4-univariate-analysis)
- [🔗 5. Bivariate Analysis](#-5-bivariate-analysis)
- [🧩 6. Multivariate Analysis](#-6-multivariate-analysis)
- [🔥 7. Correlation Analysis](#-7-correlation-analysis)
- [🚨 8. Outlier Analysis](#-8-outlier-analysis)
- [💡 9. Key Insights](#-9-key-insights)
- [📊 Important Visualizations](#-important-visualizations)
- [🧠 Analytical Findings](#-analytical-findings)
- [🎯 Final Conclusion](#-final-conclusion)
- [🚀 Future Scope](#-future-scope)
- [⚠️ Limitations](#️-limitations)
- [📁 Project Structure](#-project-structure)
- [⚙️ Installation & Setup](#️-installation--setup)
- [📦 Requirements](#-requirements)
- [▶️ How to Run](#️-how-to-run)
- [👨‍💻 Author](#-author)
- [⭐ Project Highlights](#-project-highlights)

---

#  Project Objective

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

#  Dataset

## Dataset Name

`datasets.csv`

## Dataset Description

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

🛠️ Technologies & Tools

The following technologies and Python libraries were used in the analysis:

Python
Pandas
NumPy
Matplotlib
Seaborn
Jupyter Notebook

The project does not use machine-learning models.

🔄 EDA Workflow

The analysis follows a structured Exploratory Data Analysis workflow:

Data Loading
Initial Data Inspection
Dataset Structure Analysis
Missing Value Analysis
Duplicate Analysis
Data Type Validation
Data Cleaning
Descriptive Statistics
Univariate Analysis
Bivariate Analysis
Multivariate Analysis
Correlation Analysis
Price-Based Outlier Exploration
Feature Engineering
Key Findings
Final Conclusions
🔍 1. Data Loading & Initial Exploration

The dataset is loaded using Pandas:

data = pd.read_csv('datasets.csv', encoding_errors='ignore')

The initial dataset contains:

20,770 rows
22 columns

The notebook performs initial exploration using:

data.head()
data.tail()
data.shape
data.info()
data.describe()

The initial analysis examines:

Dataset dimensions
First records
Last records
Column names
Data types
Numerical summaries
Missing values
Overall dataset structure
Neighbourhood Groups

The dataset contains five neighbourhood groups:

Manhattan
Brooklyn
Queens
Bronx
Staten Island
Room Types

The dataset contains four room types:

Entire home/apt
Private room
Shared room
Hotel room
🧹 2. Data Cleaning & Preprocessing
Missing Value Analysis

The original dataset contains missing values in 12 columns.

Column	Missing Values
neighbourhood	7
latitude	7
longitude	7
room_type	7
price	34
minimum_nights	7
number_of_reviews	7
last_review	7
reviews_per_month	7
calculated_host_listings_count	7
availability_365	7
number_of_reviews_ltm	7

The largest number of missing values occurs in the price column, with 34 missing records.

Missing records are removed using:

data.dropna(inplace=True)
Result

The dataset changes from:

20,770 rows

to:

20,736 rows

Therefore, 34 records were removed during missing-value handling.

Why It Matters

Removing incomplete observations allows the subsequent analysis to work with complete records for the selected variables.

However, dropping records can reduce the available sample size and may potentially affect the analysis if missingness is not random.

Duplicate Analysis

Duplicate records are checked using:

data.duplicated().sum()

The notebook identifies:

12 duplicate rows

These are removed using:

data.drop_duplicates(inplace=True)
Result

The dataset changes from:

20,736 rows

to:

20,724 rows

The final cleaned dataset therefore contains:

20,724 rows
22 columns
Data Type Handling

The notebook converts several identifier, text, and categorical columns to object.

These include:

id
name
host_id
host_name
neighbourhood_group
neighbourhood
room_type
last_review
license
rating
bedrooms
baths

Numerical variables include:

latitude
longitude
price
minimum_nights
number_of_reviews
reviews_per_month
calculated_host_listings_count
availability_365
number_of_reviews_ltm
beds

No explicit datetime conversion was performed for last_review.

📊 3. Descriptive Statistics

The notebook uses:

data.describe()

to calculate descriptive statistics for numerical variables.

Price Statistics
Statistic	Value
Mean	187.71
Median	125
Q1	80
Q3	199
Minimum	10
Maximum	100,000
Standard Deviation	1,023.25

The mean is substantially higher than the median.

This is consistent with a strongly right-skewed price distribution where a relatively small number of expensive listings increase the mean.

The maximum recorded price is:

100,000

which is substantially higher than the third quartile:

199
Minimum Nights
Statistic	Value
Mean	28.56
Median	30
Q1	30
Q3	30
Minimum	1
Maximum	1,250

The variable is highly concentrated around 30 nights, while some listings have considerably larger minimum-night requirements.

Number of Reviews
Statistic	Value
Mean	42.61
Median	14
Q1	4
Q3	49
Maximum	1,865

The mean is substantially higher than the median, indicating a right-skewed distribution.

Reviews per Month
Statistic	Value
Mean	1.26
Median	0.65
Q1	0.21
Q3	1.80
Maximum	75.49

The distribution is strongly right-skewed.

Availability

availability_365 ranges from:

0 to 365 days

with approximately:

Mean: 206 days
Median: 215 days
Q1: 87 days
Q3: 353 days
📈 4. Univariate Analysis
4.1 Price Distribution
Visualization

Purpose

The histogram is used to understand the distribution of Airbnb listing prices and identify skewness and extreme observations.

Observation

The distribution is strongly right-skewed.

Most listings are concentrated toward the lower price range, while the frequency decreases as price increases.

A long right tail is visible, indicating the presence of relatively high-priced listings.

Insight

Airbnb listing prices are not normally distributed.

The difference between the median price of 125 and the mean price of approximately 187.71 supports the observation that high-priced listings influence the average.

For the visualization, a price-filtered dataframe using:

price < 1500

is used.

4.2 Price Boxplot
Visualization

Purpose

The boxplot is used to examine price spread and identify potential high-price observations.

Observation

The boxplot shows a relatively concentrated central distribution with many observations extending beyond the upper whisker.

Even after applying the price < 1500 filtering used for the exploratory analysis, several high-price observations remain visible.

Insight

Listing prices have substantial variability and contain potential outliers.

The project uses a fixed price threshold for exploratory analysis rather than applying a formal statistical outlier-removal method.

🔗 5. Bivariate Analysis
5.1 Price by Neighbourhood Group and Room Type
Visualization

Purpose

This visualization compares Airbnb listing prices across neighbourhood groups while also considering room type.

Variables
X-axis: neighbourhood_group
Y-axis: price
Hue: room_type
Visualization Type

Grouped bar chart.

Observation

Listing prices vary across neighbourhood groups and room types.

Manhattan generally shows higher listing prices compared with several other neighbourhood groups.

Room type also contributes to differences in average listing prices.

Insight

Both geographic location and accommodation type are useful segmentation variables when analyzing Airbnb prices.

Comparing neighbourhoods without considering room type may hide important differences.

Caution

These observations represent associations within the dataset.

They do not establish that neighbourhood or room type causes a specific price.

5.2 Mean Price by Neighbourhood Group

Using the price-filtered dataframe where:

price < 1500

the mean prices are:

Neighbourhood Group	Mean Price
Manhattan	204.15
Brooklyn	155.14
Queens	121.68
Staten Island	118.78
Bronx	107.99
Insight

Manhattan has the highest mean listing price among the five neighbourhood groups in this analysis subset.

The Bronx has the lowest mean price among the five groups in this filtered analysis.

5.3 Price per Bed

The project creates a derived feature:

df['price per bed'] = df['price'] / df['beds']

This provides an additional normalized measure for comparing listings with different numbers of beds.

The mean price per bed by neighbourhood group is:

Neighbourhood Group	Mean Price per Bed
Manhattan	138.71
Brooklyn	99.79
Queens	76.34
Bronx	74.71
Staten Island	67.73
Insight

Manhattan has the highest mean price per bed among the neighbourhood groups in the price-filtered dataframe.

5.4 Number of Reviews vs Price
Visualization

Variables
X-axis: number_of_reviews
Y-axis: price
Hue: neighbourhood_group
Purpose

The scatter plot examines whether listings with more reviews tend to have higher or lower prices.

Observation

The scatter plot shows a broad spread of prices, particularly at lower review counts.

There is no strong visual pattern indicating that listings with more reviews consistently have higher prices.

Correlation

The correlation between:

number_of_reviews

and:

price

is approximately:

-0.044

This represents a very weak linear relationship.

Insight

The number of reviews does not show a strong linear relationship with listing price in the analyzed data.

Caution

A weak correlation does not prove that there is no relationship of any kind. It only indicates that the linear relationship between these two variables is weak.

Correlation also does not establish causation.

🧩 6. Multivariate Analysis
6.1 Pair Plot
Visualization

Purpose

The pair plot provides a simultaneous view of distributions and pairwise relationships between several numerical variables.

The analyzed variables include:

price
minimum_nights
number_of_reviews
reviews_per_month
availability_365

The plots are grouped by:

neighbourhood_group
Observation

Several variables display highly concentrated distributions with long tails.

Price is strongly right-skewed.

Minimum nights is concentrated around repeated lower values but extends toward much higher values.

The relationship between total number of reviews and reviews per month appears more clearly positive than several of the other variable relationships.

Insight

The pair plot demonstrates that the numerical variables have substantially different distributions and that some variables have stronger relationships than others.

It also shows considerable overlap between neighbourhood groups across the numerical feature space.

6.2 Geographical Distribution
Visualization

Purpose

The geographical scatter plot visualizes the spatial distribution of Airbnb listings using latitude and longitude.

Variables
X-axis: longitude
Y-axis: latitude
Color: neighbourhood_group
Observation

Listings form geographically distinct clusters corresponding to the neighbourhood groups represented in the dataset.

The listings are not uniformly distributed across geographic space.

Insight

Location provides important context for interpreting differences in Airbnb listing characteristics and prices across New York City.

🔥 7. Correlation Analysis

The notebook calculates a correlation matrix for the following numerical variables:

latitude
longitude
price
minimum_nights
number_of_reviews
reviews_per_month
calculated_host_listings_count
availability_365
beds
Correlation Heatmap

The heatmap provides a visual overview of linear relationships between the numerical variables.

Important Correlations
Number of Reviews ↔ Reviews per Month

Correlation:

0.63

This is the strongest positive relationship shown in the correlation matrix.

It indicates that listings with more total reviews tend to also have higher reviews-per-month values.

Price ↔ Beds

Correlation:

0.42

This is the strongest positive correlation with price among the numerical variables shown in the heatmap.

Listings with more beds tend to have higher prices.

However, the correlation is not strong enough to conclude that beds alone determine listing price.

Price ↔ Longitude

Correlation:

-0.19

This represents a weak-to-moderate negative linear relationship.

Price Correlations
Variable	Correlation with Price
beds	0.42
longitude	-0.19
availability_365	0.048
latitude	0.013
minimum_nights	-0.045
number_of_reviews	-0.044
calculated_host_listings_count	-0.016
reviews_per_month	-0.013
Interpretation

Among the numerical variables analyzed, beds has the strongest positive linear relationship with price.

Several other variables have correlations close to zero.

Important Note

Correlation measures association, not causation.

A correlation of 0.42 between beds and price does not mean that adding a bed will necessarily increase the price by a particular amount.

🚨 8. Outlier Analysis

The notebook investigates high-price observations using a fixed filtering condition:

df = data[data['price'] < 1500]

This creates a working dataframe for several price-related visualizations and analyses.

The cleaned dataset contains:

20,724 rows

The price-filtered dataframe contains:

20,636 rows

Therefore:

88 listings

are excluded from the price-filtered analysis because their price is greater than or equal to 1,500.

Important Distinction

The project does not perform formal statistical outlier removal using:

IQR
Z-score
Winsorization
Robust statistical methods

Instead, a fixed price threshold of:

price < 1500

is used for exploratory analysis.

Therefore, this should be described as price-based filtering for exploratory analysis, rather than formal outlier treatment.

The original dataset still contains a maximum price of:

100,000
💡 9. Key Insights
📌 Dataset-Level Insights

The original dataset contains:

20,770 listings
22 columns

After missing-value and duplicate handling, the cleaned dataset contains:

20,724 listings
22 columns

The dataset contains five neighbourhood groups and four room types.

📌 Pricing Insights

Listing prices are strongly right-skewed.

The original:

Mean price = 187.71
Median price = 125
Maximum price = 100,000

The large difference between the mean and median indicates that higher-priced observations influence the average.

📌 Neighbourhood Insights

Within the price-filtered analysis dataframe, Manhattan has the highest mean listing price:

Manhattan: 204.15

The remaining neighbourhood groups are:

Brooklyn: 155.14
Queens: 121.68
Staten Island: 118.78
Bronx: 107.99

This indicates meaningful differences in average listing prices across neighbourhood groups.

📌 Room-Type Insights

The dataset contains:

Entire home/apt
Private room
Shared room
Hotel room

The grouped price visualization demonstrates differences in pricing across accommodation types and neighbourhood groups.

📌 Review Insights

The correlation between:

number_of_reviews

and:

reviews_per_month

is approximately:

0.63

This is the strongest positive correlation in the displayed correlation matrix.

In comparison, the correlation between:

number_of_reviews

and:

price

is approximately:

-0.044

This indicates a very weak linear relationship between total reviews and price.

📌 Bed and Price Relationship

The correlation between:

beds

and:

price

is approximately:

0.42

This is the strongest positive correlation with price among the numerical variables analyzed.

This suggests that listings with more beds tend to have higher prices, although the relationship is not sufficiently strong to treat beds as the sole explanation for price variation.

📌 Feature Engineering Insight

The project creates:

price per bed

using:

price per bed = price / beds

This provides an additional metric for comparing listing prices while considering the number of beds.

The highest mean price per bed among the neighbourhood groups is observed in Manhattan.

📊 Important Visualizations
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

🧠 Analytical Findings

The EDA reveals several important characteristics of the Airbnb listings dataset.

1. Airbnb prices are highly skewed

Listing prices have a strong right-skewed distribution.

The median price is:

125

while the mean is:

187.71

The maximum price is:

100,000

This indicates that a relatively small number of expensive listings have a substantial effect on the mean.

2. Listing prices vary by neighbourhood

The price-filtered analysis shows differences in average listing prices across neighbourhood groups.

Manhattan has the highest mean price among the five neighbourhood groups, while the Bronx has the lowest mean price in the filtered analysis.

3. Room type is an important segmentation variable

The grouped price analysis demonstrates differences between room types within neighbourhood groups.

This suggests that room type should be considered when comparing listing prices.

4. Reviews and price have a weak linear relationship

The correlation between number of reviews and price is approximately:

-0.044

Therefore, the dataset does not show a strong linear relationship between these variables.

5. Reviews and reviews per month have a stronger relationship

The correlation between number of reviews and reviews per month is approximately:

0.63

This is considerably stronger than the relationship between reviews and price.

6. Beds have the strongest positive correlation with price

The correlation between beds and price is:

0.42

This is the strongest positive price correlation among the numerical variables included in the heatmap.

7. Geographic location provides useful context

The geographic visualization shows distinct spatial clustering across neighbourhood groups.

This supports the use of neighbourhood and location-related variables when investigating Airbnb pricing and listing characteristics.

🎯 Final Conclusion

This Exploratory Data Analysis provides a structured examination of Airbnb listings across New York City.

The analysis shows that listing prices are highly right-skewed and contain substantial variation. The large difference between mean and median price demonstrates the influence of high-priced observations.

Neighbourhood group and room type both show meaningful differences in listing prices. In the price-filtered analysis, Manhattan has the highest mean listing price among the five neighbourhood groups.

The correlation analysis shows that beds has the strongest positive linear relationship with price, with a correlation of approximately 0.42.

In contrast, the number of reviews has a very weak linear relationship with price, with a correlation of approximately -0.044.

The strongest correlation in the displayed correlation matrix is between number_of_reviews and reviews_per_month, at approximately 0.63.

The project also demonstrates the importance of examining skewness, missing values, duplicates, and high-value observations before performing deeper analysis.

These findings describe relationships observed in the dataset and should not be interpreted as causal conclusions.

🚀 Future Scope

The current project focuses on Exploratory Data Analysis. Several additional analyses could be performed in future work.

Feature Engineering

Potential future features include:

Price per bedroom
Price per bed
Listing availability categories
Host-level listing concentration
Review-based engagement metrics
Geographic distance features
Listing age or review recency features
Statistical Analysis

Future work could include:

Hypothesis testing between neighbourhood groups
Statistical comparison of room types
Confidence intervals
ANOVA or non-parametric tests
Analysis of statistical significance
Investigation of nonlinear relationships
Predictive Modeling

The cleaned dataset could be used for future machine-learning tasks such as:

Airbnb price prediction
High-price listing classification
Availability prediction
Review-volume prediction

Potential regression models could include:

Linear Regression
Decision Tree Regression
Random Forest Regression
Gradient Boosting

These models are not part of the current project and would represent future work.

Clustering

Unsupervised learning could be used to identify different types of Airbnb listings based on:

Price
Reviews
Availability
Minimum nights
Beds
Host listing count
Dashboard Development

The analysis could be extended into an interactive dashboard using tools such as:

Power BI
Tableau

Potential dashboard metrics could include:

Average price by neighbourhood
Average price by room type
Availability
Review activity
Listing distribution
Geographic distribution
Host activity
⚠️ Limitations
Missing Data

The original dataset contains missing values across multiple columns.

The project handles these records by removing incomplete rows rather than applying imputation.

Outliers

The price variable contains extreme observations, including a maximum value of 100,000.

The project uses a fixed price < 1500 filter for several exploratory analyses.

A formal statistical outlier-detection technique such as IQR or Z-score filtering was not implemented.

Skewed Distributions

Several variables show strong right-skewness, including:

Price
Number of reviews
Reviews per month
Minimum nights

Therefore, means should be interpreted alongside medians and other descriptive statistics.

Correlation Does Not Imply Causation

Correlation analysis identifies associations between variables.

It does not establish that one variable causes another.

For example, the 0.42 correlation between beds and price does not prove that adding beds directly causes an increase in price.
