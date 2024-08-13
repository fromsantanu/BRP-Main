# Chapter: Scales and Coordinate Systems

In `ggplot2`, scales and coordinate systems are crucial for controlling how data is mapped to visual properties and how plots are displayed. In this chapter, we'll explore how to customize scales using functions like `scale_color_manual()` and `scale_fill_manual()`, and how to manipulate the coordinate system using `coord_cartesian()`, `coord_flip()`, and `coord_polar()`.

## Customizing Scales

Scales in `ggplot2` allow you to control the mapping between data values and visual properties such as color, size, and fill. You can use functions like `scale_color_manual()` and `scale_fill_manual()` to define custom mappings.

### Example: Customizing Colors with `scale_color_manual()`

Let's create a scatter plot and customize the colors of the points based on a categorical variable.

```r
# Scatter Plot with Custom Colors
ggplot(data = mtcars, aes(x = wt, y = mpg, color = factor(cyl))) +
  geom_point(size = 3) +
  scale_color_manual(
    values = c("4" = "blue", "6" = "green", "8" = "red"),
    labels = c("4 Cylinders", "6 Cylinders", "8 Cylinders")
  ) +
  labs(
    title = "Scatter Plot with Custom Colors",
    x = "Weight (1000 lbs)",
    y = "Miles per Gallon",
    color = "Number of Cylinders"
  ) +
  theme_minimal()
```

### Explanation:
- `scale_color_manual()`: Manually sets the colors for the different levels of the `cyl` variable.
- `values`: Specifies the colors to use for each level.
- `labels`: Customizes the labels in the legend.
- The plot displays points with custom colors based on the number of cylinders.

### Example: Customizing Fill Colors with `scale_fill_manual()`

You can also customize the fill colors of bars or areas using `scale_fill_manual()`.

```r
# Bar Plot with Custom Fill Colors
ggplot(data = mtcars, aes(x = factor(cyl), fill = factor(cyl))) +
  geom_bar() +
  scale_fill_manual(
    values = c("4" = "lightblue", "6" = "lightgreen", "8" = "lightcoral"),
    labels = c("4 Cylinders", "6 Cylinders", "8 Cylinders")
  ) +
  labs(
    title = "Bar Plot with Custom Fill Colors",
    x = "Number of Cylinders",
    y = "Count",
    fill = "Cylinder Type"
  ) +
  theme_minimal()
```

### Explanation:
- `scale_fill_manual()`: Manually sets the fill colors for the bars.
- `values`: Specifies the colors to use for each level.
- The plot shows bars with custom fill colors based on the number of cylinders.

## Coordinate Systems

Coordinate systems in `ggplot2` control how the data is plotted on the axes. The default is the Cartesian coordinate system, but you can also use other systems like flipped coordinates and polar coordinates.

### Example: Cartesian Coordinate System with `coord_cartesian()`

The `coord_cartesian()` function allows you to zoom in on a specific area of the plot without altering the data.

```r
# Scatter Plot with Zoomed In View Using coord_cartesian()
ggplot(data = mtcars, aes(x = wt, y = mpg)) +
  geom_point(color = "purple", size = 3) +
  labs(
    title = "Scatter Plot with Zoomed In View",
    x = "Weight (1000 lbs)",
    y = "Miles per Gallon"
  ) +
  coord_cartesian(xlim = c(3, 5), ylim = c(15, 30)) +
  theme_minimal()
```

### Explanation:
- `coord_cartesian(xlim = c(3, 5), ylim = c(15, 30))`: Zooms in on the plot to focus on the weight range of 3 to 5 and the MPG range of 15 to 30.
- The plot shows a zoomed-in view of the data within the specified limits.

### Example: Flipped Coordinates with `coord_flip()`

The `coord_flip()` function swaps the x and y axes, which is useful for creating horizontal bar plots.

```r
# Bar Plot with Flipped Coordinates
ggplot(data = mtcars, aes(x = factor(cyl), fill = factor(cyl))) +
  geom_bar() +
  labs(
    title = "Horizontal Bar Plot with Flipped Coordinates",
    x = "Number of Cylinders",
    y = "Count",
    fill = "Cylinder Type"
  ) +
  coord_flip() +
  theme_minimal()
```

### Explanation:
- `coord_flip()`: Flips the x and y axes, turning the vertical bar plot into a horizontal one.
- The plot displays the bars horizontally, which can be easier to read when category names are long.

### Example: Polar Coordinates with `coord_polar()`

The `coord_polar()` function transforms the plot into a polar coordinate system, often used for pie charts and circular bar plots.

```r
# Pie Chart Using Polar Coordinates
ggplot(data = mtcars, aes(x = factor(1), fill = factor(cyl))) +
  geom_bar(width = 1) +
  coord_polar(theta = "y") +
  labs(
    title = "Pie Chart of Cylinder Distribution",
    fill = "Cylinder Type"
  ) +
  scale_fill_manual(
    values = c("4" = "lightblue", "6" = "lightgreen", "8" = "lightcoral")
  ) +
  theme_void()  # Removes background and axis for a cleaner look
```

### Explanation:
- `coord_polar(theta = "y")`: Converts the bar plot into a pie chart by mapping the y-axis to the angle in polar coordinates.
- `theme_void()`: Removes all background, grid, and axis elements for a clean pie chart.
- The plot shows a pie chart representing the distribution of cylinder types in the dataset.

---

This chapter covers the basics of customizing scales and using different coordinate systems in `ggplot2`. By using scale functions like `scale_color_manual()` and `scale_fill_manual()`, you can control how data is mapped to visual properties. Additionally, coordinate systems like `coord_cartesian()`, `coord_flip()`, and `coord_polar()` allow you to transform and present your data in various ways, providing flexibility in how you visualize your data.
