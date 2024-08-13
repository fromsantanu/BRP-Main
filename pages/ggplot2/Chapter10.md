# Chapter: Combining Multiple Geoms

In `ggplot2`, you can combine multiple geoms (geometric objects) in a single plot to create more complex and informative visualizations. By layering different geoms, you can display multiple aspects of the data within the same plot. This chapter will cover how to layer multiple geoms and create complex plots with multiple layers.

## Layering Multiple Geoms in a Single Plot

Layering geoms in `ggplot2` is straightforward: you simply add multiple `geom_` functions to your plot. Each geom can represent a different aspect of the data.

### Example: Scatter Plot with a Smoothing Line

Let's start by combining a scatter plot with a smoothing line (a linear regression line) to show the relationship between two variables, along with the trend.

```r
# Scatter Plot with a Smoothing Line
ggplot(data = mtcars, aes(x = wt, y = mpg)) +
  geom_point(color = "blue", size = 3) +              # First layer: Scatter plot
  geom_smooth(method = "lm", se = FALSE, color = "red") +  # Second layer: Linear regression line
  labs(
    title = "Scatter Plot with Smoothing Line",
    x = "Weight (1000 lbs)",
    y = "Miles per Gallon"
  ) +
  theme_minimal()
```

### Explanation:
- `geom_point()`: Adds a scatter plot layer.
- `geom_smooth(method = "lm", se = FALSE)`: Adds a smoothing line using linear regression.
- The plot shows the individual data points along with a red line indicating the linear trend.

### Example: Bar Plot with a Line Plot

You can also combine different types of geoms, such as a bar plot with a line plot, to compare categorical and continuous data simultaneously.

```r
# Bar Plot with a Line Plot
df <- data.frame(
  category = c("A", "B", "C", "D"),
  value1 = c(10, 20, 15, 25),
  value2 = c(8, 18, 13, 22)
)

ggplot(data = df, aes(x = category)) +
  geom_bar(aes(y = value1), stat = "identity", fill = "skyblue") +  # First layer: Bar plot
  geom_line(aes(y = value2, group = 1), color = "darkblue", size = 1) +  # Second layer: Line plot
  geom_point(aes(y = value2), color = "darkblue", size = 3) +  # Third layer: Points on the line
  labs(
    title = "Bar Plot with Line Plot",
    x = "Category",
    y = "Values"
  ) +
  theme_minimal()
```

### Explanation:
- `geom_bar()`: Adds a bar plot layer.
- `geom_line()`: Adds a line plot layer to show the trend across categories.
- `geom_point()`: Adds points on the line for emphasis.
- The plot displays bars for `value1` and a line with points for `value2`, allowing comparison across the categories.

## Creating Complex Plots with Multiple Layers

By layering multiple geoms, you can create complex plots that convey more detailed information. This can be particularly useful for combining different types of data or emphasizing specific aspects of the data.

### Example: Histogram with Density Plot and Rug Plot

Let's create a plot that combines a histogram, a density plot, and a rug plot to show the distribution of a continuous variable.

```r
# Histogram with Density and Rug Plot
ggplot(data = mtcars, aes(x = mpg)) +
  geom_histogram(aes(y = ..density..), binwidth = 2, fill = "lightblue", color = "black", alpha = 0.6) +  # First layer: Histogram
  geom_density(color = "red", size = 1) +  # Second layer: Density plot
  geom_rug(color = "darkblue") +  # Third layer: Rug plot
  labs(
    title = "Histogram with Density and Rug Plot",
    x = "Miles per Gallon",
    y = "Density"
  ) +
  theme_minimal()
```

### Explanation:
- `geom_histogram(aes(y = ..density..))`: Adds a histogram with density on the y-axis.
- `geom_density()`: Adds a density plot over the histogram.
- `geom_rug()`: Adds a rug plot at the bottom, showing individual data points.
- The plot provides a comprehensive view of the distribution of `mpg`, combining the histogram's bins, the density curve's smoothness, and the rug plot's detailed data points.

### Example: Combining Scatter Plot, Line Plot, and Text Annotations

You can create a plot that combines a scatter plot, a line plot, and text annotations to highlight specific data points.

```r
# Scatter Plot with Line Plot and Text Annotations
ggplot(data = mtcars, aes(x = wt, y = mpg)) +
  geom_point(color = "darkorange", size = 3) +  # First layer: Scatter plot
  geom_line(color = "blue", size = 1) +  # Second layer: Line plot
  geom_text(aes(label = rownames(mtcars)), vjust = -0.5, color = "black") +  # Third layer: Text annotations
  labs(
    title = "Scatter Plot with Line and Text Annotations",
    x = "Weight (1000 lbs)",
    y = "Miles per Gallon"
  ) +
  theme_minimal()
```

### Explanation:
- `geom_point()`: Adds a scatter plot layer.
- `geom_line()`: Adds a line connecting the points.
- `geom_text()`: Adds text annotations for each point.
- The plot shows both the data points and the trend line, with each point labeled by its car model name for easy identification.

### Example: Box Plot with Jittered Points

Combining a box plot with jittered points helps visualize the distribution of individual data points along with the summary statistics provided by the box plot.

```r
# Box Plot with Jittered Points
ggplot(data = mtcars, aes(x = factor(cyl), y = mpg)) +
  geom_boxplot(fill = "lightgreen", color = "darkgreen") +  # First layer: Box plot
  geom_jitter(width = 0.2, color = "darkblue", size = 2) +  # Second layer: Jittered points
  labs(
    title = "Box Plot with Jittered Points",
    x = "Number of Cylinders",
    y = "Miles per Gallon"
  ) +
  theme_minimal()
```

### Explanation:
- `geom_boxplot()`: Adds a box plot layer to show summary statistics (median, quartiles, etc.).
- `geom_jitter()`: Adds jittered points to show individual data points, avoiding overlap.
- The plot allows you to see both the overall distribution and individual data points, providing a complete picture of the data.

---

This chapter covers how to combine multiple geoms in `ggplot2` to create more complex and informative plots. By layering geoms such as scatter plots, lines, histograms, density plots, and text annotations, you can create visualizations that convey multiple dimensions of your data and highlight specific insights.
