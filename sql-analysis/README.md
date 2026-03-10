# SQL Data Analysis

This section contains SQL queries used to analyze the Amazon product dataset.

The analysis focuses on product ratings, customer reviews and discount patterns across different product categories.

The goal of this analysis is to extract insights about:

- customer satisfaction
- product popularity
- pricing strategies

SQL queries were used to explore relationships between product categories, ratings, review counts and discount percentages.

## Tools Used

- SQL
- Aggregation functions (AVG, SUM)
- GROUP BY
- ORDER BY

## Queries Performed
The following analytical SQL queries were used to explore the dataset:


The following analyses were performed:

• Top rated product categories based on average rating

• Lowest rated product categories based on average rating

• Product categories with the highest average discount

• Product categories with the highest number of reviews

• Most reviewed product categories

## Example SQL Query

```sql
SELECT category, AVG(rating) AS avg_rating
FROM amazon_products
GROUP BY category
ORDER BY avg_rating DESC
LIMIT 10;
```

## Results

### Highest Rated Product Categories
![Highest Rated Categories](highest_rated_categories_sql.png)

**Explanation**
This query calculates the average rating for each product category using the AVG() function.
The results are sorted in descending order to identify the categories with the highest customer satisfaction.
Categories with higher ratings typically indicate better product quality and stronger customer feedback.


### Lowest Rated Product Categories
![Lowest Rated Categories](lowest_rated_categories_sql.png)

**Explanation**
This query identifies the Amazon product categories with the lowest average ratings.
The dataset is grouped by product category and the average rating is calculated using the AVG() function.
The results are sorted in ascending order to highlight the categories with the lowest customer satisfaction.
These categories may indicate potential product quality issues or negative customer experiences.


### Categories with Highest Average Discount
![Average Discount](top_categories_average_discount_sql.png)

**Explanation**
This analysis calculates the average discount percentage for each product category.
The query groups products by category and uses the AVG(discount_percentage) function to compute the average discount level.
The results are sorted from highest to lowest to identify categories where aggressive pricing or promotional strategies are most common.


### Categories with Highest Review Count
![Review Count](top_categories_review_count_sql.png)

**Explanation**
This query determines which product categories have the highest total number of customer reviews.
The query uses the SUM(rating_count) function to calculate the total reviews for each category.
Categories with higher review counts usually represent high-demand products with strong customer engagement.


### Top Reviewed Categories
![Top Reviewed Categories](top_reviewed_categories_sql.png)

**Explanation**
This analysis highlights the most reviewed product categories on Amazon.
By summing the number of reviews for each category and sorting the results in descending order, we can identify product segments with the highest customer activity.
Categories with large review volumes typically indicate popular and frequently purchased products.



# Business Insights

Based on the analysis of the Amazon product dataset, several business insights can be identified:

• Product categories with extremely high review counts often represent **high-demand consumer electronics and accessories**, such as USB cables and audio devices.

• Categories with the highest average ratings typically indicate **strong customer satisfaction and product quality**, which may reflect well-established or trusted product segments.

• Some categories show **significantly lower average ratings**, which may indicate product quality issues, poor user experience or unmet customer expectations.

• Categories with very high average discount percentages may represent **highly competitive markets**, where sellers use aggressive pricing strategies to attract customers.

• High review volumes combined with strong ratings may indicate **successful product segments** that generate both high demand and positive customer feedback.

These insights demonstrate how data analysis can help identify **customer behavior patterns, product demand and pricing strategies** within large e-commerce platforms such as Amazon.
