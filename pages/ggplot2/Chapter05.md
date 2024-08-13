# Chapter: Faceting for Multi-Panel Plots

Faceting is a powerful feature in `ggplot2` that allows you to create multi-panel plots, where each panel shows a subset of the data. This technique is useful when you want to compare the same relationship across different categories or levels of a factor variable.

## Faceting with `facet_wrap()`

The `facet_wrap()` function arranges the panels in a wrap-around layout, meaning that the panels are displayed in a grid that wraps around as needed. It is particularly useful when you have a single faceting variable and want to compare across its levels.

### Example: Faceting with One Variable

Let's create a scatter plot of `mpg` versus `wt` from the `mtcars` dataset, faceted by the number of cylinders (`cyl`).

```r
# Scatter Plot Faceted by Number of Cylinders
ggplot(data = mtcars, aes(x = wt, y = mpg)) +
  geom_point() +
  facet_wrap(~ cyl) +
  labs(title = "Scatter Plot of MPG vs Weight Faceted by Number of Cylinders", 
       x = "Weight (1000 lbs)", 
       y = "Miles per Gallon") +
  theme_minimal()
```

### Explanation:
- `facet_wrap(~ cyl)`: Creates separate panels for each level of the `cyl` variable (number of cylinders).
- The plot shows separate scatter plots for cars with 4, 6, and 8 cylinders, making it easy to compare the relationship between weight and fuel efficiency across these groups.

### Customizing the Layout

You can control the number of rows and columns in the facet layout using the `nrow` and `ncol` arguments.

```r
# Faceting with Custom Layout
ggplot(data = mtcars, aes(x = wt, y = mpg)) +
  geom_point() +
  facet_wrap(~ cyl, nrow = 1) +
  labs(title = "Scatter Plot of MPG vs Weight Faceted by Number of Cylinders (One Row)", 
       x = "Weight (1000 lbs)", 
       y = "Miles per Gallon") +
  theme_minimal()
```

### Explanation:
- `nrow = 1`: Arranges all panels in a single row.
- The plot now displays the three panels in a horizontal layout.

## Faceting with `facet_grid()`

The `facet_grid()` function creates a grid of panels based on two faceting variables. This is useful when you want to explore interactions between two categorical variables.

### Example: Faceting by Two Variables

Let's create a scatter plot of `mpg` versus `wt`, faceted by both the number of cylinders (`cyl`) and the number of gears (`gear`).

```r
# Scatter Plot Faceted by Cylinders and Gears
ggplot(data = mtcars, aes(x = wt, y = mpg)) +
  geom_point() +
  facet_grid(gear ~ cyl) +
  labs(title = "Scatter Plot of MPG vs Weight Faceted by Cylinders and Gears", 
       x = "Weight (1000 lbs)", 
       y = "Miles per Gallon") +
  theme_minimal()
```

### Explanation:
- `facet_grid(gear ~ cyl)`: Creates a grid of panels with `gear` defining the rows and `cyl` defining the columns.
- The plot shows how the relationship between weight and miles per gallon varies across combinations of cylinder counts and gear counts.

### Example: Faceting by One Variable with `facet_grid()`

You can also use `facet_grid()` with just one variable by specifying only rows or columns.

```r
# Faceting by Gears Only
ggplot(data = mtcars, aes(x = wt, y = mpg)) +
  geom_point() +
  facet_grid(. ~ gear) +
  labs(title = "Scatter Plot of MPG vs Weight Faceted by Gears", 
       x = "Weight (1000 lbs)", 
       y = "Miles per Gallon") +
  theme_minimal()
```

### Explanation:
- `facet_grid(. ~ gear)`: Creates a grid of panels with the `gear` variable defining the columns. The dot (`.`) indicates that no faceting is done for rows.
- The plot shows how the relationship between weight and miles per gallon varies across different gear counts, with all panels in a single row.

### Example: Faceting by One Variable with Rows

Alternatively, you can create facets based on rows:

```r
# Faceting by Cylinders Only
ggplot(data = mtcars, aes(x = wt, y = mpg)) +
  geom_point() +
  facet_grid(cyl ~ .) +
  labs(title = "Scatter Plot of MPG vs Weight Faceted by Cylinders", 
       x = "Weight (1000 lbs)", 
       y = "Miles per Gallon") +
  theme_minimal()
```

### Explanation:
- `facet_grid(cyl ~ .)`: Creates a grid of panels with the `cyl` variable defining the rows.
- The plot shows how the relationship between weight and miles per gallon varies across different numbers of cylinders, with all panels in a single column.

## Combining Faceting with Aesthetic Mappings

You can combine faceting with aesthetic mappings to create even more informative plots. For example, you can map color to a variable while faceting by another.

### Example: Combining Faceting with Color Mapping

```r
# Scatter Plot with Faceting and Color Mapping
ggplot(data = mtcars, aes(x = wt, y = mpg, color = factor(am))) +
  geom_point() +
  facet_wrap(~ cyl) +
  labs(title = "Scatter Plot of MPG vs Weight Faceted by Cylinders and Colored by Transmission", 
       x = "Weight (1000 lbs)", 
       y = "Miles per Gallon") +
  theme_minimal()
```

### Explanation:
- `color = factor(am)`: Maps the transmission type (`am`) to the color of the points.
- `facet_wrap(~ cyl)`: Facets the plot by the number of cylinders.
- The plot shows separate panels for each cylinder group, with points colored by transmission type.

---

This chapter introduces the concept of faceting in `ggplot2` and demonstrates how to use `facet_wrap()` and `facet_grid()` to create multi-panel plots. By using faceting, you can efficiently compare different subsets of your data, making it easier to identify patterns and insights across categories.
