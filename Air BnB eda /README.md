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

```text
price < 1500
