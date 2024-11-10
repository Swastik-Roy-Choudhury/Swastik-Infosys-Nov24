# **AUTHOR NAME**- SWASTIK ROY CHOUDHURY

### **Email Id** - swastikroychoudhury014@gmail.com

### **GitHub Repository** - https://github.com/Swastik-Roy-Choudhury/Swastik-Infosys-Nov24


# **Title**
**FutureCart**: *AI-Driven Demand Prediction for Smarter Retail.*

# **Project Statement:**
In the realm of E-commerce, demand forecasting plays a pivotal role in ensuring business success. This project aims to develop a demand forecasting model in an E-commerce business that predicts future product demand leveraging time series analysis and multivariate regression based on historical sales data, along with Google Analytics KPIs such as Google clicks and Facebook impressions, which are valuable indicators of customer interest.

# **Outcomes**

**>Improved Inventory Management:** More accurate demand forecasts lead to better inventory decisions, potentially reducing stock-outs and excess inventory.

**>Enhanced Marketing Efficiency:** Identify periods of high demand for targeted marketing campaigns, optimizing resource allocation.

**>Data-Driven Decision Making:** Reliable forecasts provide a basis for business decisions, such as pricing adjustments or product promotions.

**>Accurate Demand Predictions:** Implement a forecasting model that achieves high accuracy in predicting future demands, thereby improving customer service levels.

**>Scalable Solution:** Develop a solution that can scale to handle large datasets and varying demand patterns across multiple products.

# **Milestone 1: Week 1**
# Module 1: Data Collection
• Understanding the problem statement 

• Gathering sales data from relevant sources (database, store records) 

• Collecting Google Analytics and Facebook Impressions data


# **Milestone 1: Week 2**
# Module 2: Exploratory Data Analysis (EDA) and Data Preprocessing

• Ensuring my sales data is in a time series format (e.g., daily, weekly, monthly) with timestamps.

• Cleaning and formating data, handling missing values and outliers. Address them using appropriate techniques (imputation, elimination).

• Ploting the distribution plots on independent variables.

• Visualizations to understand trends, seasonality, and correlations.

• Statistical summaries.

# **Insights**

I started by importing the necessary libraries: `google.colab.drive` and `pandas`. I then mounted my Google Drive to access my dataset.

Next, I loaded the Excel file, "Master_ProductA_dataset.xlsx," into a pandas DataFrame. To get a sense of the data quality, I checked for missing values using `data.isnull().sum()`. This gave me a clear picture of the columns with missing data.

To identify potential outliers, I implemented two methods:

**1. Z-Score Method:**
   - I defined a function `detect_outliers_zscore` that takes a DataFrame and an optional threshold as input.
   - For each numerical column, I calculated the mean and standard deviation.
   - Then, I computed the Z-score for each data point.
   - Outliers were identified as data points with Z-scores exceeding the specified threshold.

**2. IQR Method:**
   - I defined a function `detect_outliers` that takes a DataFrame and a column name as input.
   - I calculated the first quartile (Q1) and third quartile (Q3) of the specified column.
   - The interquartile range (IQR) was computed.
   - Outliers were identified as data points lying below Q1 - 1.5*IQR or above Q3 + 1.5*IQR.

After identifying the outliers, I decided to replace them with the median value of the respective columns. I defined a function `replace_outliers` to achieve this. For each numerical column, I calculated the mean and standard deviation. Data points exceeding a certain threshold were considered outliers and replaced with the median.

Finally, I saved the cleaned dataset to a new Excel file, "cleaned_file.xlsx," for further analysis.


**Feature Engineering**

I started by loading the cleaned dataset into a pandas DataFrame. To gain a better understanding of the data, I printed the first few rows.

**Feature Creation**

I then embarked on the feature engineering process to extract more insights from the data:

1. **Datetime Conversion and Extraction:**
   - I converted the 'Day Index' column to a datetime format.
   - I extracted the day of the week from the 'Day Index' and created a new column 'Day of Week'.

2. **Interaction Feature:**
   - I calculated 'Clicks per Impression' by dividing 'Clicks' by 'Impressions' and added it as a new column.

3. **Polynomial Feature:**
   - I created a new column 'Quantity Squared' by squaring the values in the 'Quantity' column.

I printed the first few rows of the modified DataFrame to visualize the newly created features. Finally, I saved the enhanced dataset to a new Excel file, "enhanced_file.xlsx".

**Loading the Enhanced Dataset**

I loaded the enhanced dataset that I had previously created into a pandas DataFrame. To get a quick overview, I printed the first few rows.

## Data Exploration and Visualization

**Initial Exploration**

1. **Loaded Data:** I started by loading the enhanced dataset, "enhanced_file.xlsx," into a pandas DataFrame for further analysis.
2. **Previewed Data:** I printed the first few rows to get a glimpse of the data structure.
3. **Summary Statistics:** I generated basic descriptive statistics for each column to understand data distribution and ranges.
4. **Missing Values:** I checked for missing values to ensure data completeness.
5. **Data Distribution Visualization:**
   - I created histograms for numerical columns to visualize value distribution and identify potential patterns or outliers.
   - I used boxplots to detect outliers in the numerical columns for further analysis or cleaning.
6. **Relationships and Correlations:** I generated a pairplot to explore relationships and potential correlations between numerical columns.

**Creating Specific Visualizations**

1. **Time Series Plot:** I converted the 'Day Index' column to datetime format for accurate time-based visualizations.
   - I then created a line plot to visualize how 'Quantity' changed over time.

2. **Scatter Plot:** I created a scatter plot to examine the relationship between 'Clicks' and 'Impressions'.

3. **Bar Plot - Day of Week:** I investigated average 'Quantity' by day of the week:
   - I grouped data by 'Day of Week' and calculated the average 'Quantity'.
   - I created a bar plot with a specific order for days of the week (Monday to Sunday) to  visualize trends.

4. **Histogram:** Finally, I generated a histogram to observe the distribution of 'Quantity' values. I added a kernel density estimation (KDE) for a smoother distribution curve.

   

