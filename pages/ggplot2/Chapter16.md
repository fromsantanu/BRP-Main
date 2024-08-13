# Chapter: Case Studies and Examples

In this chapter, we'll explore real-world examples of data visualization using `ggplot2`. These case studies will demonstrate how to apply `ggplot2` to common data visualization tasks, such as exploring relationships between variables, visualizing distributions, and creating complex, multi-layered plots. Each example will address a specific problem and provide a solution using `ggplot2`.

## Case Study 1: Exploring the Relationship Between Variables

### Problem: How can we visualize the relationship between two continuous variables, while also highlighting a categorical variable?

### Dataset: `mtcars` (built-in R dataset)
- Variables:
  - `wt`: Weight of the car
  - `mpg`: Miles per gallon
  - `cyl`: Number of cylinders (categorical variable)

### Solution: Scatter Plot with Color-Coded Points by Category

```r
# Load necessary libraries
library(ggplot2)

# Create a scatter plot with color-coded points by number of cylinders
p <- ggplot(data = mtcars, aes(x = wt, y = mpg, color = factor(cyl))) +
  geom_point(size = 3) +
  geom_smooth(method = "lm", se = FALSE, linetype = "dashed", color = "black") +
  labs(
    title = "Scatter Plot of MPG vs Weight",
    subtitle = "Colored by Number of Cylinders",
    x = "Weight (1000 lbs)",
    y = "Miles per Gallon",
    color = "Cylinders"
  ) +
  theme_minimal()

# Display the plot
print(p)
```

### Explanation:
- **Task**: Visualize the relationship between car weight and fuel efficiency, with color-coded points based on the number of cylinders.
- **Solution**: A scatter plot with a linear regression line to show the trend. Points are color-coded by the number of cylinders, making it easy to compare different categories.
- **Takeaway**: This plot helps in understanding how weight and the number of cylinders affect fuel efficiency.

## Case Study 2: Visualizing the Distribution of a Continuous Variable

### Problem: How can we visualize the distribution of a continuous variable across different categories?

### Dataset: `iris` (built-in R dataset)
- Variables:
  - `Sepal.Length`: Length of the sepal (continuous variable)
  - `Species`: Species of the iris (categorical variable)

### Solution: Box Plot with Jittered Points

```r
# Load necessary libraries
library(ggplot2)

# Create a box plot with jittered points to visualize the distribution
p <- ggplot(data = iris, aes(x = Species, y = Sepal.Length, color = Species)) +
  geom_boxplot(outlier.shape = NA) +  # Hide outliers in the boxplot
  geom_jitter(width = 0.2, size = 2, alpha = 0.7) +  # Add jittered points
  labs(
    title = "Distribution of Sepal Length by Species",
    x = "Species",
    y = "Sepal Length (cm)"
  ) +
  theme_minimal()

# Display the plot
print(p)
```

### Explanation:
- **Task**: Compare the distribution of sepal length across different species.
- **Solution**: A box plot combined with jittered points to show both the summary statistics and individual data points. This approach helps in identifying the central tendency and variability within each species.
- **Takeaway**: The plot highlights differences in sepal length distributions across species and can reveal any potential outliers.

## Case Study 3: Visualizing Time Series Data

### Problem: How can we visualize trends over time and identify patterns in time series data?

### Dataset: `economics` (built-in R dataset)
- Variables:
  - `date`: Date of the observation
  - `unemploy`: Number of unemployed people (in thousands)

### Solution: Line Plot with Highlighted Sections

```r
# Load necessary libraries
library(ggplot2)

# Create a line plot to visualize unemployment over time
p <- ggplot(data = economics, aes(x = date, y = unemploy)) +
  geom_line(color = "blue", size = 1) +
  geom_rect(aes(xmin = as.Date("2008-01-01"), xmax = as.Date("2009-12-31"), ymin = -Inf, ymax = Inf), fill = "red", alpha = 0.2) +
  labs(
    title = "Unemployment Trends Over Time",
    subtitle = "Highlighted Period: 2008-2009 (Global Financial Crisis)",
    x = "Date",
    y = "Unemployed (in thousands)"
  ) +
  theme_minimal()

# Display the plot
print(p)
```

### Explanation:
- **Task**: Visualize unemployment trends over time and highlight significant periods (e.g., the 2008-2009 financial crisis).
- **Solution**: A line plot with a shaded rectangle to highlight the specific period. The use of `geom_rect()` helps to draw attention to the period of interest.
- **Takeaway**: This plot effectively communicates long-term trends while emphasizing critical periods that may warrant further analysis.

## Case Study 4: Comparing Multiple Categories

### Problem: How can we compare the frequency of different categories within multiple groups?

### Dataset: `diamonds` (part of `ggplot2`)
- Variables:
  - `cut`: Quality of the cut (categorical variable)
  - `clarity`: Clarity of the diamond (categorical variable)

### Solution: Stacked Bar Plot

```r
# Load necessary libraries
library(ggplot2)

# Create a stacked bar plot to compare cut quality across different clarity levels
p <- ggplot(data = diamonds, aes(x = clarity, fill = cut)) +
  geom_bar(position = "fill") +
  labs(
    title = "Proportion of Cut Quality by Diamond Clarity",
    x = "Clarity",
    y = "Proportion",
    fill = "Cut"
  ) +
  theme_minimal()

# Display the plot
print(p)
```

### Explanation:
- **Task**: Compare the distribution of cut quality across different clarity levels.
- **Solution**: A stacked bar plot with proportions, making it easier to compare the relative frequencies of each cut quality within each clarity category.
- **Takeaway**: The plot shows the distribution of cuts for each clarity level, helping to understand how cut quality varies across different clarity grades.

## Case Study 5: Visualizing Correlations with a Heatmap

### Problem: How can we visualize the correlation between multiple numeric variables?

### Dataset: `mtcars` (built-in R dataset)
- Variables: Various numeric variables (e.g., `mpg`, `hp`, `wt`, etc.)

### Solution: Correlation Heatmap

```r
# Load necessary libraries
library(ggplot2)
library(reshape2)

# Compute the correlation matrix
cor_data <- round(cor(mtcars), 2)

# Melt the correlation matrix into a format suitable for ggplot2
melted_cor_data <- melt(cor_data)

# Create a heatmap of the correlation matrix
p <- ggplot(data = melted_cor_data, aes(x = Var1, y = Var2, fill = value)) +
  geom_tile(color = "white") +
  scale_fill_gradient2(low = "blue", high = "red", mid = "white", midpoint = 0) +
  labs(
    title = "Correlation Heatmap of mtcars Variables",
    x = "Variable",
    y = "Variable",
    fill = "Correlation"
  ) +
  theme_minimal() +
  theme(axis.text.x = element_text(angle = 45, hjust = 1))

# Display the plot
print(p)
```

### Explanation:
- **Task**: Visualize the correlations between multiple numeric variables in the `mtcars` dataset.
- **Solution**: A heatmap created using `geom_tile()` with a color gradient to represent the strength and direction of correlations. The x-axis labels are rotated for better readability.
- **Takeaway**: The heatmap provides a clear visual representation of correlations, helping to identify strong positive or negative relationships between variables.

---

This chapter presents a series of real-world case studies that demonstrate how to solve common data visualization tasks using `ggplot2`. Each example is designed to address a specific problem and provide a practical solution, showcasing the versatility and power of `ggplot2` for data visualization. Whether you're exploring relationships between variables, visualizing distributions, or comparing categories, these case studies offer useful techniques that you can apply to your own data.
