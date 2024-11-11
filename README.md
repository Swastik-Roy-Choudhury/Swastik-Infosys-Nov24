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


### 1. Data Loading and Setup
I started by loading the dataset from an Excel file and converting the 'Day Index' column to a datetime format, setting it as the index. This setup was important for performing time-series analysis.

### 2. Exploratory Data Analysis (EDA)

**2.1 Descriptive Statistics**
I reviewed descriptive statistics for key columns ('Quantity', 'Impressions', 'Clicks') to understand central tendencies and variability. This step provided an initial sense of the data’s distribution, revealing potential outliers or anomalies.

**2.2 Distribution Analysis**
I visualized the distributions for 'Quantity', 'Impressions', and 'Clicks' using histograms with KDE plots. Through this, I was able to:
   - Identify skewness or outliers.
   - Observe peaks that indicated common value ranges and demand periods.
   - Note valleys that could reflect rare events or demand gaps.

**2.3 Time Series Analysis**
I plotted daily trends for 'Quantity', 'Impressions', and 'Clicks' to observe temporal patterns. This analysis:
   - Highlighted periods of high and low activity.
   - Allowed me to spot seasonality and regular patterns.
   - Revealed peaks corresponding to high-demand days and troughs to low-demand days.

**2.4 Weekly and Monthly Rolling Averages**
I calculated weekly and monthly rolling averages to smooth out daily fluctuations and capture broader trends. The resulting plot helped in identifying:
   - Consistent short-term trends through weekly averages.
   - Long-term demand trends via monthly averages, reducing the impact of daily noise.

**2.5 Correlation Analysis**
Using pairwise scatter plots and a correlation heatmap, I examined relationships between 'Quantity', 'Impressions', and 'Clicks'. This analysis:
   - Visually identified positive or negative correlations.
   - Suggested interdependencies and segments in user behavior.
   - Quantified the strength of relationships, helping inform feature selection for predictive modeling.

**2.6 Conversion Rate Analysis**
I calculated and plotted the 'Conversion Rate' over time to evaluate the effectiveness of impressions converting into clicks. This analysis:
   - Showed peaks that highlighted successful campaigns or relevant content.
   - Revealed valleys, indicating potential misalignment with user interest.
   - Provided a basis to monitor conversion trends over time for optimization.

### 3. Data Preprocessing

**3.1 Missing Value Check**
I examined the dataset for missing values to determine if any data imputation or cleanup was needed, ensuring data quality.

**3.2 Date Feature Expansion**
To enhance temporal analysis, I extracted various date-related features, including 'Day of Week', 'Week', 'Month', 'Quarter', and 'Year'. These additional time dimensions helped in seasonal and weekly demand pattern recognition.

**3.3 Feature Scaling**
I normalized the 'Quantity', 'Impressions', and 'Clicks' columns using MinMaxScaler to ensure they were on a comparable scale, preparing the data for modeling.

### 4. Feature Engineering

**4.1 Rolling Metrics**
I calculated weekly and monthly rolling sums for 'Quantity' and average values for 'Impressions' and 'Clicks'. These metrics captured recent trends over different time windows, which could highlight periods of sustained or fluctuating demand.

**4.2 Lag Features**
To introduce temporal dependencies, I created lagged features for 'Quantity', 'Impressions', and 'Clicks'. This enabled me to analyze the impact of past values on present demand, setting the foundation for predictive modeling.

After completing these steps, I reviewed the data to ensure that all new features were integrated correctly, enhancing the dataset's richness and readiness for further analysis or modeling.

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

# **Insights**

I started by loading the cleaned dataset into a pandas DataFrame. To gain a better understanding of the data, I printed the first few rows.

**Feature Creation**

I then embarked on the feature engineering process to extract more insights from the data:

In this code, I was enhancing my dataset by generating new features to gain deeper insights into user behavior and trends. Here’s a detailed breakdown of each step and why I implemented it:

 **Loading and Initial Exploration**:
   - I started by loading the dataset from an Excel file into a DataFrame and printed the first few rows. This was crucial for examining the dataset’s initial structure and identifying any required data transformations or additional features that could improve analysis.

 **Date Conversion**:
   - I converted the 'Day Index' column to datetime format, as I wanted to extract date-related features. This step was essential for enabling any time-based analysis, such as understanding patterns across days of the week or differentiating between weekdays and weekends.

 **Time-Based Features**:
   - I created two features: `Day of Week` and `Is Weekend`. The `Day of Week` helped me capture daily trends, while `Is Weekend` flagged whether a given date was a Saturday or Sunday. This information was helpful for observing any differences in user behavior on weekends versus weekdays, which could impact campaign strategies.

 **Interaction Feature (Clicks per Impression)**:
   - I calculated `Clicks per Impression` to get a ratio of engagement. This feature gave insight into the effectiveness of impressions in generating clicks, helping me evaluate the engagement level more precisely. It served as an essential metric for understanding user interest and gauging performance.

 **Lag Features for Temporal Relationships**:
   - I added lagged columns (`Prev Day Clicks`, `Prev Day Impressions`, `Prev Day Conversion Rate`) to incorporate information from the previous day. This allowed me to analyze how past behaviors impacted the current day's performance. For example, if clicks spiked one day, I could see if there was any subsequent effect on the following day, which helped in time-series analysis.

 **Cumulative Metrics**:
   - I calculated cumulative metrics for `Quantity`, `Impressions`, and `Clicks`, which added a running total of these values. Cumulative metrics were insightful for understanding overall performance growth over time and helped me track the progress of various metrics continuously.

 **Exponential Moving Averages (EMA)**:
   - I applied a 7-day Exponential Moving Average (EMA) to `Clicks`, `Impressions`, and `Quantity` to smooth out fluctuations in the data, especially for high-frequency variations. Using EMA allowed me to observe long-term trends more effectively by reducing noise, helping me focus on significant patterns without being distracted by daily variations.

 **High-Engagement Flag**:
   - I created a `High Engagement` flag based on the 75th percentile thresholds for `Clicks` and `Impressions`. This flag identified days with unusually high engagement. With this feature, I could quickly spot peak activity days, which might correlate with successful campaigns or other significant events.

 **Output and Storage**:
   - After adding these new features, I printed the enhanced data and saved it to a new Excel file for further analysis or visualization. Saving the file ensured that I had a record of the enriched dataset for future use or sharing.

 These additions allowed for better analysis of trends, seasonality, engagement, and cumulative growth, providing a more comprehensive understanding of the dataset’s underlying dynamics.

 ## Data Exploration and Visualization
I was conducting a detailed exploratory analysis to visualize and interpret the key patterns within the dataset, focusing on user engagement metrics. Here are the insights and reasoning from each plot and analysis:

###  Line Plot of Quantity, Impressions, and Clicks Over Time
I was plotting 'Quantity,' 'Impressions,' and 'Clicks' over time to observe their daily trends.
   - **Insight**: Peaks in 'Impressions' pointed to high engagement periods, often corresponding to marketing campaigns, while 'Quantity' peaks aligned with 'Impressions,' suggesting a positive relationship.
   - **Reason for Peaks and Valleys**: High points represented strong demand or engagement, and valleys indicated off-peak periods or lower interest.
   - **Purpose of Plot**: This time-series analysis was crucial for observing general trends, campaign impact, and seasonality in customer behavior.

###  Boxplot of Quantity by Day of the Week
I examined the distribution of 'Quantity' across weekdays to identify day-specific patterns.
   - **Insight**: Certain days showed higher median values, suggesting peak activity aligned with user behavior patterns.
   - **Reason for Peaks and Valleys**: Peaks on specific days might correlate with scheduled campaigns or weekly habits.
   - **Purpose of Plot**: This analysis helped pinpoint the best days for user engagement and could inform scheduling strategies.

###  Histogram of Clicks per Impression
I analyzed the distribution of 'Clicks per Impression' to understand engagement quality.
   - **Insight**: The histogram showed the most common engagement rates, with the distribution shape indicating typical user interaction patterns.
   - **Reason for Peaks and Valleys**: Peaks in certain bins represented common engagement levels, while valleys indicated extremes.
   - **Purpose of Plot**: This plot revealed engagement quality and helped guide strategies for optimizing impression effectiveness.

###  Correlation Heatmap Between Numerical Features
I created a heatmap to visualize the correlations among 'Quantity,' 'Impressions,' and 'Clicks.'
   - **Insight**: Strong correlations between features highlighted synergistic relationships, informing feature selection for modeling.
   - **Reason for Peaks and Valleys**: High values represented strong dependencies, while low values indicated weaker relationships.
   - **Purpose of Plot**: This correlation matrix was essential for understanding interdependencies among features, useful in predictive modeling.

###  Cumulative Plot of Quantity, Impressions, and Clicks Over Time
I plotted cumulative totals of 'Quantity,' 'Impressions,' and 'Clicks' to examine overall growth trends.
   - **Insight**: A steady rise indicated continuous growth in user interactions, while peaks showed high-activity periods.
   - **Reason for Peaks and Valleys**: Peaks signaled accelerated growth phases, while plateaus suggested stabilization or seasonal drops.
   - **Purpose of Plot**: This cumulative view offered a big-picture perspective on overall engagement trends and growth over time.

###  Pairplot of Quantity, Impressions, and Clicks
I used a pairplot to explore relationships among 'Quantity,' 'Impressions,' and 'Clicks.'
   - **Insight**: Linear patterns suggested correlations or causations, while visible outliers indicated unusual data points.
   - **Reason for Peaks and Valleys**: Clustering in scatter plots indicated strong relationships, while dispersed points suggested weaker links.
   - **Purpose of Plot**: This plot was useful for identifying feature interrelationships and patterns that might inform further modeling.

This analysis provided a comprehensive understanding of user behavior patterns, feature relationships, and data quality, preparing the data for informed decision-making and future predictive modeling.
   

