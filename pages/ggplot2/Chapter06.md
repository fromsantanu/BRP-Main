# Chapter: Handling Continuous and Categorical Data

In `ggplot2`, you can control the appearance and behavior of your plot's axes by using scale functions. These functions allow you to handle continuous and categorical (discrete) data in a flexible and customizable manner. In this chapter, we'll explore how to use `scale_x_continuous()`, `scale_y_continuous()` for continuous data, and `scale_x_discrete()`, `scale_y_discrete()` for categorical data.

## Continuous Data: `scale_x_continuous()` and `scale_y_continuous()`

Continuous scales are used when your data involves numeric variables that can take on an infinite number of values within a given range. These scales allow you to modify the axis breaks, limits, labels, and more.

### Example: Customizing X-Axis with `scale_x_continuous()`

Let's create a scatter plot of `mpg` versus `wt` and customize the x-axis to have specific breaks and labels.

```r
# Scatter Plot with Custom X-Axis
ggplot(data = mtcars, aes(x = wt, y = mpg)) +
  geom_point() +
  scale_x_continuous(name = "Weight (1000 lbs)", 
                     breaks = c(2, 3, 4, 5), 
                     labels = c("2K", "3K", "4K", "5K")) +
  labs(title = "Scatter Plot of MPG vs Weight with Custom X-Axis", 
       y = "Miles per Gallon") +
  theme_minimal()
```

### Explanation:
- `scale_x_continuous()`: Customizes the x-axis for continuous data.
- `name = "Weight (1000 lbs)"`: Sets a custom axis label.
- `breaks = c(2, 3, 4, 5)`: Specifies the positions of the axis ticks.
- `labels = c("2K", "3K", "4K", "5K")`: Customizes the labels displayed at the tick marks.
- The plot shows a scatter plot with the x-axis labeled in thousands of pounds.

### Example: Customizing Y-Axis with `scale_y_continuous()`

Similarly, you can customize the y-axis to change the range, breaks, and labels.

```r
# Scatter Plot with Custom Y-Axis
ggplot(data = mtcars, aes(x = wt, y = mpg)) +
  geom_point() +
  scale_y_continuous(name = "Miles per Gallon", 
                     limits = c(10, 35), 
                     breaks = seq(10, 35, by = 5)) +
  labs(title = "Scatter Plot of MPG vs Weight with Custom Y-Axis", 
       x = "Weight (1000 lbs)") +
  theme_minimal()
```

### Explanation:
- `scale_y_continuous()`: Customizes the y-axis for continuous data.
- `limits = c(10, 35)`: Sets the range of the y-axis from 10 to 35.
- `breaks = seq(10, 35, by = 5)`: Specifies the axis ticks at intervals of 5 units.
- The plot displays a scatter plot with the y-axis range and tick marks adjusted accordingly.

## Categorical Data: `scale_x_discrete()` and `scale_y_discrete()`

Categorical (discrete) scales are used when your data involves factors or categories that take on a limited number of distinct values. These scales allow you to modify the order, labels, and other properties of categorical axes.

### Example: Customizing X-Axis with `scale_x_discrete()`

Let's create a bar plot showing the count of cars by the number of cylinders, and customize the x-axis to reorder and rename the categories.

```r
# Bar Plot with Custom X-Axis
ggplot(data = mtcars, aes(x = factor(cyl))) +
  geom_bar(fill = "skyblue") +
  scale_x_discrete(name = "Number of Cylinders", 
                   labels = c("Four" = "4", "Six" = "6", "Eight" = "8")) +
  labs(title = "Bar Plot of Car Cylinders with Custom X-Axis", 
       y = "Count") +
  theme_minimal()
```

### Explanation:
- `scale_x_discrete()`: Customizes the x-axis for categorical data.
- `name = "Number of Cylinders"`: Sets a custom axis label.
- `labels = c("Four" = "4", "Six" = "6", "Eight" = "8")`: Reorders and renames the categories on the x-axis.
- The plot shows a bar plot with customized labels for the number of cylinders.

### Example: Customizing Y-Axis with `scale_y_discrete()`

Although less common, you can also customize the y-axis when dealing with categorical data in plots such as horizontal bar plots.

```r
# Horizontal Bar Plot with Custom Y-Axis
ggplot(data = mtcars, aes(x = factor(cyl))) +
  geom_bar(fill = "lightgreen") +
  coord_flip() +  # Flips the axes to make a horizontal bar plot
  scale_y_discrete(name = "Number of Cylinders", 
                   labels = c("Four" = "4", "Six" = "6", "Eight" = "8")) +
  labs(title = "Horizontal Bar Plot of Car Cylinders with Custom Y-Axis", 
       x = "Count") +
  theme_minimal()
```

### Explanation:
- `coord_flip()`: Flips the x and y axes to create a horizontal bar plot.
- `scale_y_discrete()`: Customizes the y-axis for categorical data (after the axes are flipped).
- The plot shows a horizontal bar plot with customized labels for the number of cylinders.

## Combining Continuous and Categorical Scales

In many cases, your plot will involve both continuous and categorical variables. You can combine `scale_x_continuous()` and `scale_y_discrete()` (or vice versa) to fully customize your plot's axes.

### Example: Combining Continuous X-Axis with Categorical Y-Axis

Let's create a scatter plot where the x-axis represents a continuous variable (`mpg`), and the y-axis represents a categorical variable (`cyl`).

```r
# Scatter Plot with Continuous X-Axis and Categorical Y-Axis
ggplot(data = mtcars, aes(x = mpg, y = factor(cyl))) +
  geom_point(color = "darkred", size = 3) +
  scale_x_continuous(name = "Miles per Gallon", 
                     breaks = seq(10, 35, by = 5)) +
  scale_y_discrete(name = "Number of Cylinders", 
                   labels = c("Four" = "4", "Six" = "6", "Eight" = "8")) +
  labs(title = "Scatter Plot with Continuous X-Axis and Categorical Y-Axis") +
  theme_minimal()
```

### Explanation:
- `scale_x_continuous()`: Customizes the continuous x-axis with specific breaks.
- `scale_y_discrete()`: Customizes the categorical y-axis with renamed categories.
- The plot shows a scatter plot that combines a continuous x-axis with a categorical y-axis, making it easy to compare miles per gallon across different cylinder categories.

---

This chapter covers the basics of handling continuous and categorical data in `ggplot2`. By using `scale_x_continuous()`, `scale_y_continuous()` for continuous variables, and `scale_x_discrete()`, `scale_y_discrete()` for categorical variables, you can fully control the appearance and behavior of your plot's axes, tailoring your visualizations to better convey the insights from your data.
