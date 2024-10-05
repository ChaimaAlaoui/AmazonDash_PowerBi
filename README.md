
# Amazon Customer Behavior Analysis
This project focuses on analyzing customer behavior on Amazon, using Power BI, DAX, and SQL to provide insights into customer interactions, shopping habits, and decision-making processes. The project aims to help optimize marketing strategies and improve customer experience on Amazon through data analysis and visualization.
## Table of Contents
- [Project Overview](#project-overview)
- [Objectives](#objectives)
- [Tools and Technologies](#tools-and-technologies)
- [Data Cleaning and Transformation](#data-cleaning-and-transformation)
- [Data Analysis and Visualization](#data-analysis-and-visualization)
- [DAX Codes](#dax-codes)
- [SQL Queries](#sql-queries-used)
- [Conclusion](#conclusion)

## Project Overview
This project aims to analyze customer behavior patterns on Amazon, focusing on customer interactions, browsing habits, purchase preferences, and product reviews. By leveraging Power BI, SQL, and DAX, we provide insights into key trends that can help optimize marketing strategies and enhance the customer experience on Amazon.
## Objectives
1. Analyze customer purchasing behavior by product categories and frequency.
2. Explore customer satisfaction and factors influencing shopping experiences.
3. Investigate the impact of personalized recommendations and reviews on purchasing decisions.
4. Identify key trends to optimize the customer experience and improve sales strategies.
## Tools and Technologies
- **Power BI**: For creating interactive dashboards and data visualizations.
- **DAX (Data Analysis Expressions)**: Used for measures and complex calculations in Power BI.
- **SQL**: For querying, cleaning, and validating data.
- **Microsoft Excel**: For initial data exploration and cleaning.
- **GitHub**: For version control and managing project files.
## Data Cleaning and Transformation
- **Data Import**: Imported dataset into Power BI from SQL.
- **Handling Missing Data**: Removed or imputed missing values.
- **Normalization**: Standardized data for consistency.
- **Filtering**: Focused on key variables related to customer behavior.
## Data Analysis and Visualization

### Power BI and DAX:
- Created measures to analyze **customer purchase frequency** and **satisfaction scores**.
- Analyzed **top product categories** and the **reasons for cart abandonment**.

### Key Visualizations:
1. **Customer Purchase Frequency Distribution**: Shows how often customers purchase products.
2. **Top 3 Product Categories Purchased**: Beauty and Personal Care, Clothing and Fashion, and Others.
3. **Reasons for Cart Abandonment**: Includes high shipping costs, better price found elsewhere, and change of mind.
4. **Customer Satisfaction by Age Group**: Highlights how satisfaction scores differ across various age brackets,etc..
## DAX Codes

- **Count of Reviews where 'Review_Left' is "Yes"**
   ```DAX
   Number_of_Reviews = 
   COUNTROWS(
    FILTER(
        'amazon_db customerbehavior', 
        'amazon_db customerbehavior'[Review_Left] = "Yes"
         )
    )



- **Average of Purchase Frequency**
   ```DAX
   Purchase_Frequency_Average = 
   AVERAGE('amazon_db customerbehavior'[Purchase_Frequency])

- **Rank Product Categories by Count of Customers**
  ```DAX
  Rank_Product_Categories = 
  RANKX(
    ALL('amazon_db customerbehavior'[Purchase_Categories]), 
    [Count_of_Customers], 
    , 
    DESC, 
    DENSE
  )

- **Count of Customers**
  ```DAX 
  Count_of_Customers = 
  COUNTROWS('amazon_db customerbehavior')

- **Average of Shopping Satisfaction**
  ```DAX
  Average_Satisfaction = 
  AVERAGE('amazon_db customerbehavior'[Shopping_Satisfaction])

- **Average of Rating Accuracy**
  ```DAX
  Average_Rating = 
  AVERAGE('amazon_db customerbehavior'[Rating_Accuracy])


## SQL Queries

- **Total Count of Customers and Reviews**:
  ```sql
  SELECT COUNT(DISTINCT customer_id) AS Total_Customers,
         COUNT(review_id) AS Total_Reviews
  FROM customer_behavior;


- **Top 3 Product Categories**:
  ```sql
  SELECT Purchase_Categories, COUNT(*) AS Count_of_Purchases 
  FROM customerbehavior 
  GROUP BY Purchase_Categories 
  ORDER BY Count_of_Purchases DESC 
  LIMIT 3;

- **Average Rating and Satisfaction:**
  ```sql
  SELECT AVG(customer_rating) AS Average_Rating,
  AVG(customer_satisfaction) AS Average_Satisfaction
  FROM customer_behavior;
- **Customer Purchase Frequency Distribution:**
  ```sql
  SELECT purchase_frequency, COUNT(*) AS Frequency_Count
  FROM customer_behavior
  GROUP BY purchase_frequency;

## Conclusion
This analysis highlights key insights into customer habits, satisfaction, and reasons for cart abandonment. These insights can be leveraged to improve marketing strategies, reduce cart abandonment, and enhance the overall customer experience. Addressing factors like high shipping costs and offering better deals could lead to higher conversion rates and customer satisfaction.




