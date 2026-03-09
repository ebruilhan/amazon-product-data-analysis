# Python Data Analysis

This folder contains the **Python-based exploratory data analysis (EDA)** performed on the Amazon product dataset.

The analysis was conducted using **Python, Pandas and Matplotlib** to explore patterns in product ratings, review counts and discount percentages across Amazon product categories.

## Tools Used

- Python
- Pandas
- Matplotlib

## Dataset

The dataset includes:

- Product category
- Product rating
- Rating count (number of reviews)
- Discount percentage
- Product pricing information

These variables allow us to analyze product popularity, customer satisfaction and pricing behavior.

---

# Analysis 1 — Top Rated Product Categories

This analysis identifies categories with the **highest average ratings**, which usually indicates strong product quality and customer satisfaction.

### Python Code

```python
top_rated = (
    df.groupby("category")["rating"]
    .mean()
    .round(2)
    .sort_values(ascending=False)
    .head(10)
    .reset_index()
)

top_rated
