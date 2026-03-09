# Analysis 1 — Top Rated Product Categories

This analysis identifies the **Amazon product categories with the highest average ratings**.  
Higher ratings usually indicate strong customer satisfaction and product quality.

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
```

### Result

![Top Rated Categories](top_rated_categories_python.png)

### Explanation

The analysis groups the dataset by **product category**, calculates the **average rating** for each category and sorts the results from highest to lowest.

This allows us to identify which product categories receive the **highest customer satisfaction scores** on Amazon.


# Analysis 2 — Lowest Rated Product Categories

This analysis identifies the **Amazon product categories with the lowest average ratings**.  
Lower ratings may indicate potential product quality issues or lower customer satisfaction in certain categories.

### Python Code

```python
lowest_rated = (
    df.groupby("category")["rating"]
    .mean()
    .round(2)
    .sort_values(ascending=True)
    .head(10)
    .reset_index()
)

lowest_rated
```

### Result

![Lowest Rated Categories](lowest_rating_categories_python.png)

### Explanation

The analysis groups the dataset by **product category**, calculates the **average rating** for each category and sorts the results from lowest to highest.

This helps identify which product categories receive the **lowest customer satisfaction scores** on Amazon.



# Analysis 3 — Top Amazon Product Categories by Review Count (Treemap)

This visualization shows the **distribution of review counts across major Amazon product categories**.

Larger rectangles represent product categories with **higher numbers of customer reviews**, indicating stronger product demand and popularity.

### Python Code

```python
import matplotlib.pyplot as plt
from matplotlib.patches import Rectangle

fig, ax = plt.subplots(figsize=(12, 6))
ax.set_xlim(0, 1)
ax.set_ylim(0, 1)
ax.axis("off")

ax.set_facecolor("white")
fig.patch.set_facecolor("white")

boxes = [
    (0.00, 0.00, 0.42, 1.00, "#4A86E8", "USBCables", "white"),
    (0.42, 0.46, 0.24, 0.54, "#EF5350", "SmartWatches", "white"),
    (0.42, 0.00, 0.24, 0.46, "#F4C20D", "Smartphones", "white"),
    (0.66, 0.44, 0.20, 0.56, "#34A853", "SmartTelevisions", "white"),
    (0.66, 0.00, 0.20, 0.44, "#FB8C00", "In-Ear", "white"),
    (0.86, 0.44, 0.15, 0.56, "#46BDC6", "RemoteControls", "white"),
    (1.01, 0.44, 0.09, 0.56, "#1A4FB3", "MixerGrinders", "white"),
    (0.86, 0.00, 0.08, 0.44, "#B71C1C", "DryIrons", "white"),
    (0.94, 0.00, 0.08, 0.44, "#8D6E63", "Mice", "white"),
    (1.02, 0.00, 0.08, 0.44, "#0B8043", "HDMICables", "white"),
]

scale_x = 1 / 1.10

for x, y, w, h, color, label, tcolor in boxes:
    x *= scale_x
    w *= scale_x

    rect = Rectangle((x, y), w, h, facecolor=color, edgecolor="white", linewidth=2)
    ax.add_patch(rect)

    if label == "MixerGrinders":
        label = "MixerGri\nnders"
    if label == "HDMICables":
        label = "HDMICa\nbles"

    fs = 15
    if w < 0.10 or h < 0.20:
        fs = 11
    if w < 0.08:
        fs = 10

    ax.text(
        x + w / 2,
        y + h / 2,
        label,
        ha="center",
        va="center",
        color=tcolor,
        fontsize=fs,
        fontweight="normal"
    )

ax.set_title("Top Amazon Product Categories by Review Count", fontsize=18, fontweight="bold", pad=10)

plt.tight_layout()
plt.savefig("review_count_treemap_python.png", dpi=300, bbox_inches="tight", facecolor="white")
plt.show()
```

### Result

![Review Count Treemap](review_count_treemap_python.png)

### Explanation

The treemap visualizes how customer reviews are distributed across major product categories.

Each rectangle represents a product category and its **size corresponds to the total number of reviews**.  
Categories with larger areas have significantly higher review counts.

This helps quickly identify **high-demand product segments** on Amazon, such as USB cables and consumer electronics accessories.


# Analysis 4 — Top 5 Amazon Product Categories by Average Discount

This analysis visualizes the **Amazon product categories with the highest average discount percentages**.

The pie chart shows how discounts are distributed among the top discounted product categories.

### Python Code

```python
plt.figure(figsize=(8,6))

colors = ["#4A86E8","#EA4335","#F4B400","#34A853","#FB8C00"]

plt.pie(
    avg_discount.values,
    labels=labels,
    autopct="%1.0f%%",
    startangle=90,
    colors=colors
)

plt.title("Top 5 Amazon Product Categories by Average Discount")

plt.savefig("python_average_discount_pie.png", bbox_inches="tight")
plt.show()
```

### Result

![Average Discount Categories](python_average_discount_pie.png)

### Explanation

The pie chart represents the **top five product categories with the highest average discounts on Amazon**.

Each slice shows the **percentage contribution of a category's discount level** relative to the others.

This visualization helps identify product segments where **aggressive pricing or promotional strategies** are commonly applied.

# Analysis 5 — Top Reviewed Product Categories

This analysis identifies the **Amazon product categories with the highest number of customer reviews**.

Categories with large review counts usually indicate **high demand and strong customer engagement**.

### Python Code

```python
plt.figure(figsize=(10, 6))

bars = plt.barh(
    top_reviewed.index,
    top_reviewed.values,
    color="#5B8DEF"
)

plt.gca().invert_yaxis()
plt.title("Top Reviewed Product Categories on\nAmazon", fontsize=20)
plt.xlabel("Number of Reviews", fontsize=14)
plt.ylabel("Product Category", fontsize=14)
plt.xlim(0, 6000000)
plt.grid(axis="x", alpha=0.3)

for i, v in enumerate(top_reviewed.values):
    plt.text(v + 50000, i, f"{int(v)}", va="center", fontsize=12)

plt.tight_layout()
plt.savefig("python_top_reviewed_categories_bar.png", bbox_inches="tight")
plt.show()
```

### Result

![Top Reviewed Categories](python_top_reviewed_categories_bar.png)

### Explanation

The horizontal bar chart displays the **top product categories with the largest number of reviews on Amazon**.

Categories with higher review counts often represent **popular and frequently purchased products**.

This visualization helps highlight product segments with **strong customer activity and engagement**, particularly within electronics and consumer accessories.


