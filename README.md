# Yulu Bike Rental – Exploratory Data Analysis & Hypothesis Testing

## Project Overview

Yulu is a micro-mobility service provider offering shared electric bikes for convenient urban transportation.

This project analyses Yulu's bike rental data to understand the factors influencing rental demand. The objective is to identify patterns across seasons, weather conditions, and working days, and use statistical hypothesis testing to determine whether these factors significantly affect bike rental demand.

The analysis combines Exploratory Data Analysis (EDA) with statistical techniques to generate actionable insights that can help Yulu optimize bike availability, improve customer engagement, and support business growth.

## Business Objectives

- Understand the overall distribution and trends in bike rental demand.
- Identify seasonal and monthly patterns in bike rentals.
- Analyse the relationship between weather conditions and rental demand.
- Compare bike rentals on working and non-working days.
- Determine whether rental demand differs significantly across seasons.
- Examine the relationship between weather conditions and seasons.
- Apply statistical hypothesis testing to validate observations.
- Develop data-driven recommendations for improving business performance.

## Dataset Overview

The dataset contains **10,886 records and 12 original columns**, covering bike rental activity from January 2011 to December 2012.

| Feature | Description |
|---|---|
| datetime | Date and time of rental activity |
| season | Season (Spring, Summer, Fall, Winter) |
| holiday | Indicates whether the day is a holiday |
| workingday | Indicates whether the day is a working day |
| weather | Weather condition category |
| temp | Actual temperature |
| atemp | Feels-like temperature |
| humidity | Humidity level |
| windspeed | Wind speed |
| casual | Rentals by casual users |
| registered | Rentals by registered users |
| count | Total bike rentals |

**Data validation:**
- 10,886 records and 12 original features.
- No missing values identified.
- No duplicate records identified.
- Verified that total rentals (`count`) equal the sum of casual and registered rentals.
- Created additional date-related features such as year, month, day, and hour.

## Tools & Technologies

- **Python**
- **Pandas & NumPy** – Data manipulation and numerical analysis
- **Matplotlib & Seaborn** – Data visualization
- **SciPy** – Statistical hypothesis testing
- **Statsmodels** – Q-Q plot analysis
- **Jupyter Notebook** – Analysis and experimentation

## Project Workflow

### 1. Data Loading & Inspection

- Imported the required Python libraries.
- Loaded the bike-sharing dataset.
- Examined dataset dimensions, data types, and statistical summaries.
- Checked for missing and duplicate values.
- Verified the relationship between casual, registered, and total rentals.

### 2. Data Cleaning & Feature Engineering

- Converted categorical variables into appropriate categorical data types.
- Converted the datetime column into a datetime format.
- Extracted year, month, day, and hour from the datetime column.
- Replaced numerical category codes with meaningful labels for seasons, holidays, working days, and months.
- Performed descriptive statistical analysis.

### 3. Exploratory Data Analysis (EDA)

**Univariate Analysis**
- Examined the distribution of rental counts.
- Analysed season, holiday, working-day, and weather categories.
- Studied temperature, apparent temperature, humidity, and windspeed.
- Identified outliers and skewness in numerical variables.

**Bivariate Analysis**
- Compared rental demand across seasons.
- Analysed the impact of weather conditions on rentals.
- Compared demand on working and non-working days.
- Examined correlations between weather variables and rental counts.

**Monthly Analysis**
- Aggregated total rentals by month.
- Identified peak and off-peak rental periods.
- Examined seasonal variations in bike rental demand.

### 4. Correlation Analysis

Analysed relationships between numerical variables using a correlation matrix and heatmap.

Key observations:
- Temperature and apparent temperature have a strong positive correlation of approximately 0.98.
- Apparent temperature has a moderate positive correlation with casual rentals (approximately 0.46).
- Temperature has a moderate positive correlation with casual rentals (approximately 0.47).
- Humidity has a negative relationship with rental demand.
- Weather-related variables show different degrees of association with casual and registered rentals.

### 5. Statistical Hypothesis Testing

Performed statistical tests at a **95% confidence level**, using a significance level of 0.05.

The analysis covered three major business questions.

#### A. Does bike rental demand differ between working and non-working days?

**Hypotheses:**

- H₀: There is no significant difference in bike rental demand between working and non-working days.
- H₁: There is a significant difference in bike rental demand between working and non-working days.

**Statistical approach:**
- Shapiro-Wilk test to examine normality.
- Q-Q plot to visually inspect the distribution.
- Levene's test to examine equality of variances.
- Kruskal-Wallis test to compare the two independent groups.

**Result:** The p-value was greater than 0.05.

**Conclusion:** Failed to reject the null hypothesis. The analysis did not find a statistically significant difference in bike rental demand between working and non-working days.

#### B. Does bike rental demand differ across weather conditions?

**Hypotheses:**

- H₀: There is no significant difference in bike rental demand across different weather conditions.
- H₁: There is a significant difference in bike rental demand across different weather conditions.

**Statistical approach:**
- Examined the distribution of rental counts across weather categories.
- Used Levene's test to assess equality of variances.
- Applied One-Way ANOVA.
- Applied the Kruskal-Wallis test as an additional non-parametric comparison because the data did not satisfy the normality and equal-variance assumptions.

**ANOVA result:** p-value = 5.48 × 10⁻⁴².

**Conclusion:** Rejected the null hypothesis. There is a statistically significant difference in bike rental demand across weather conditions.

#### C. Does bike rental demand differ across seasons?

**Hypotheses:**

- H₀: There is no significant difference in bike rental demand across different seasons.
- H₁: There is a significant difference in bike rental demand across different seasons.

**Statistical approach:**
- Examined rental distributions across the four seasons.
- Used Levene's test to assess equality of variances.
- Applied One-Way ANOVA.
- Applied the Kruskal-Wallis test to compare the results.

**Results:**
- ANOVA p-value = 6.16 × 10⁻¹⁴⁹.
- Kruskal-Wallis p-value = 2.48 × 10⁻¹⁵¹.

**Conclusion:** Both tests indicate a statistically significant difference in bike rental demand across seasons.

#### D. Are weather conditions dependent on seasons?

**Hypotheses:**

- H₀: Season and weather conditions are independent.
- H₁: Season and weather conditions are dependent.

**Statistical approach:**
- Created a contingency table between season and weather.
- Applied the Chi-Square Test of Independence.

**Result:**

- Chi-square statistic = 49.16
- p-value = 1.55 × 10⁻⁷

**Conclusion:** Rejected the null hypothesis. There is a statistically significant association between seasons and weather conditions.

## Key Findings

### 1. Monthly Rental Trends

- June recorded the highest number of rentals, with **220,733 rentals**.
- July and August were also among the peak rental months.
- June, July, and August show higher rental activity.
- January, February, and March recorded comparatively lower rental activity.

### 2. Seasonal Demand

- Rental demand varies significantly across seasons.
- Summer months demonstrate higher rental activity.
- Seasonal variations should be considered when planning bike availability and operational capacity.

### 3. Weather Impact

- Bike rental demand differs significantly across weather conditions.
- Weather conditions are statistically associated with seasonal patterns.
- Weather-responsive operational planning could help improve bike utilization.

### 4. Working vs. Non-Working Days

- The analysis did not identify a statistically significant difference in rental demand between working and non-working days.
- This suggests that operational planning should not rely solely on the working-day classification.

### 5. Correlation Insights

- Temperature and apparent temperature are highly correlated.
- Casual rentals show a stronger positive correlation with temperature than registered rentals.
- Humidity has a negative association with rental activity.

## Strategic Business Recommendations

Based on the analysis, the following recommendations were identified:

1. **Optimize Bike Distribution During Peak Months:** Increase bike availability during June, July, and August to accommodate higher rental demand.

2. **Seasonal Marketing Strategies:** Introduce targeted campaigns during peak months to attract more customers and capitalize on increased demand.

3. **Off-Peak Promotions:** Offer discounts and promotional packages during January, February, and March to encourage rentals during slower periods.

4. **Weather-Responsive Operations:** Adjust bike deployment and promotional strategies based on weather conditions.

5. **Optimize Weekly Deployment:** Since no significant difference was identified between working and non-working days, consider demand patterns beyond the working-day classification when allocating bikes.

6. **Improve Customer Experience:** Invest in app features, bike maintenance, and customer support to encourage repeat usage.

7. **Diversify Revenue Streams:** Explore premium memberships, partnerships, sponsorships, and additional subscription benefits.

8. **Seasonal and Weather-Based Planning:** Combine seasonal trends and weather forecasts to improve bike availability and operational efficiency.

## Key Learnings

Through this project, I strengthened my understanding of:

- Exploratory Data Analysis and feature engineering.
- Univariate, bivariate, and correlation analysis.
- Data distribution, skewness, and outlier detection.
- Shapiro-Wilk normality testing.
- Levene's test for equality of variances.
- Independent group comparison using non-parametric methods.
- One-Way ANOVA and Kruskal-Wallis tests.
- Chi-Square Test of Independence.
- Formulating null and alternative hypotheses.
- Interpreting p-values and statistical significance.
- Translating statistical findings into actionable business recommendations.

## Repository Structure

```text
Yulu-Case-Study/
│
├── Yulu_Case_Study_2024.ipynb
├── bike_sharing.csv
└── README.md
```

*Note: Include the dataset in the repository only if its distribution is permitted.*

## Conclusion

This project demonstrates how Exploratory Data Analysis and statistical hypothesis testing can help understand the factors influencing bike rental demand.

The analysis identifies significant differences in rental demand across weather conditions and seasons, while no statistically significant difference was found between working and non-working days.

These findings provide a foundation for improving seasonal planning, optimizing bike distribution, and developing weather-responsive business strategies.

---

## Author

**Umar Reyaz**

Data Analyst | Data Science & AI/ML Enthusiast

- **LinkedIn:** https://www.linkedin.com/in/umar-reyaz-55a164272
- **GitHub:** https://github.com/umar16257-design
- **Email:** umar16257@gmail.com
