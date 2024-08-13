# Chapter: Customizing Aesthetics

Customizing aesthetics in `ggplot2` allows you to control the visual properties of your plots, making them more informative and visually appealing. In this chapter, we'll explore how to map aesthetics such as color, size, and shape to variables in your data, and how to set these properties manually.

## Mapping Aesthetics: Color, Size, Shape, etc.

Mapping aesthetics means linking visual properties like color, size, and shape to variables in your dataset. This allows the plot to visually represent additional dimensions of data.

### Example: Mapping Color

Let's start by mapping the color of the points in a scatter plot to a categorical variable, such as the number of cylinders in the `mtcars` dataset.

```r
# Scatter Plot with Color Mapped to Number of Cylinders
ggplot(data = mtcars, aes(x = wt, y = mpg, color = factor(cyl))) +
  geom_point(size = 3) +
  labs(title = "Scatter Plot of MPG vs Weight", 
       x = "Weight (1000 lbs)", 
       y = "Miles per Gallon") +
  theme_minimal()
```

### Explanation:
- `color = factor(cyl)`: Maps the `cyl` variable (number of cylinders) to the color of the points.
- The plot shows points colored according to the number of cylinders in the cars, adding another layer of information to the scatter plot.

### Example: Mapping Size

You can also map the size of the points to a continuous variable, such as horsepower (`hp`).

```r
# Scatter Plot with Size Mapped to Horsepower
ggplot(data = mtcars, aes(x = wt, y = mpg, size = hp)) +
  geom_point(color = "blue") +
  labs(title = "Scatter Plot of MPG vs Weight with Size Mapped to Horsepower", 
       x = "Weight (1000 lbs)", 
       y = "Miles per Gallon") +
  theme_minimal()
```

### Explanation:
- `size = hp`: Maps the `hp` variable (horsepower) to the size of the points.
- The plot shows points of varying sizes based on the horsepower, giving a sense of how horsepower relates to both weight and fuel efficiency.

### Example: Mapping Shape

Shape can also be mapped to a categorical variable, such as the transmission type (`am`).

```r
# Scatter Plot with Shape Mapped to Transmission Type
ggplot(data = mtcars, aes(x = wt, y = mpg, shape = factor(am))) +
  geom_point(color = "darkgreen", size = 3) +
  labs(title = "Scatter Plot of MPG vs Weight with Shape Mapped to Transmission", 
       x = "Weight (1000 lbs)", 
       y = "Miles per Gallon") +
  theme_minimal()
```

### Explanation:
- `shape = factor(am)`: Maps the `am` variable (transmission type: 0 = automatic, 1 = manual) to the shape of the points.
- The plot shows different shapes for cars with automatic and manual transmissions, providing additional categorical information.

## Setting Aesthetics Manually

In addition to mapping aesthetics to variables, you can manually set the aesthetics to specific values. This is useful when you want to customize the appearance of your plot without linking it to data.

### Example: Setting Color Manually

You can set all points to be a specific color by specifying the color argument directly in `geom_point()`.

```r
# Scatter Plot with Manually Set Color
ggplot(data = mtcars, aes(x = wt, y = mpg)) +
  geom_point(color = "red", size = 3) +
  labs(title = "Scatter Plot of MPG vs Weight with Red Points", 
       x = "Weight (1000 lbs)", 
       y = "Miles per Gallon") +
  theme_minimal()
```

### Explanation:
- `color = "red"`: Sets the color of all points to red.
- The plot shows all points in the same color, focusing purely on the relationship between weight and miles per gallon.

### Example: Setting Size Manually

Similarly, you can set the size of all points to a fixed value.

```r
# Scatter Plot with Manually Set Size
ggplot(data = mtcars, aes(x = wt, y = mpg)) +
  geom_point(color = "blue", size = 5) +
  labs(title = "Scatter Plot of MPG vs Weight with Large Blue Points", 
       x = "Weight (1000 lbs)", 
       y = "Miles per Gallon") +
  theme_minimal()
```

### Explanation:
- `size = 5`: Sets the size of all points to 5.
- The plot displays large blue points, drawing attention to the data points themselves.

### Example: Setting Shape Manually

You can also set the shape of the points to a specific symbol.

```r
# Scatter Plot with Manually Set Shape
ggplot(data = mtcars, aes(x = wt, y = mpg)) +
  geom_point(color = "purple", size = 4, shape = 17) +
  labs(title = "Scatter Plot of MPG vs Weight with Triangles", 
       x = "Weight (1000 lbs)", 
       y = "Miles per Gallon") +
  theme_minimal()
```

### Explanation:
- `shape = 17`: Sets the shape of all points to triangles (shape code 17).
- The plot displays all points as purple triangles, providing a distinct visual style.

## Combining Mapped and Manual Aesthetics

You can combine mapped and manually set aesthetics in the same plot. For example, you might map color to a variable while manually setting the size.

### Example: Combining Aesthetics

```r
# Scatter Plot with Mapped Color and Manually Set Size
ggplot(data = mtcars, aes(x = wt, y = mpg, color = factor(gear))) +
  geom_point(size = 4, shape = 16) +
  labs(title = "Scatter Plot of MPG vs Weight with Mapped Color and Fixed Size", 
       x = "Weight (1000 lbs)", 
       y = "Miles per Gallon") +
  theme_minimal()
```

### Explanation:
- `color = factor(gear)`: Maps the `gear` variable (number of gears) to the color of the points.
- `size = 4`, `shape = 16`: Sets the size and shape of all points manually.
- The plot displays points of a fixed size and shape, with colors representing the number of gears.

---

This chapter covers the basics of customizing aesthetics in `ggplot2`. By mapping aesthetics to variables, you can create plots that convey multiple dimensions of information. Additionally, manually setting aesthetics allows for fine-tuned control over the appearance of your visualizations.
