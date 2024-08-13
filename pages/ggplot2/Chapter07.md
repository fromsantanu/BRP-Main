# Chapter: Themes and Theme Elements

`ggplot2` provides a variety of themes to customize the overall appearance of your plots. Themes control non-data elements such as background color, grid lines, text styles, and axis lines. In this chapter, we'll explore some default themes, how to customize themes with `theme()`, and how to modify specific theme elements like background grid lines and text.

## Default Themes

`ggplot2` comes with several built-in themes that you can apply to your plots. These themes provide a quick way to change the overall look of your plot.

### Example: Default Theme (`theme_gray()`)

The default theme in `ggplot2` is `theme_gray()`, which provides a gray background with white grid lines.

```r
# Default Theme: theme_gray()
ggplot(data = mtcars, aes(x = wt, y = mpg)) +
  geom_point() +
  labs(title = "Scatter Plot with Default Theme (theme_gray())", 
       x = "Weight (1000 lbs)", 
       y = "Miles per Gallon") +
  theme_gray()
```

### Explanation:
- `theme_gray()`: The default theme with a gray background and white grid lines.
- The plot displays the default appearance that you get when creating a `ggplot2` plot.

### Example: Minimal Theme (`theme_minimal()`)

The `theme_minimal()` provides a clean, minimalistic design with a white background and no grid lines.

```r
# Minimal Theme: theme_minimal()
ggplot(data = mtcars, aes(x = wt, y = mpg)) +
  geom_point() +
  labs(title = "Scatter Plot with Minimal Theme (theme_minimal())", 
       x = "Weight (1000 lbs)", 
       y = "Miles per Gallon") +
  theme_minimal()
```

### Explanation:
- `theme_minimal()`: A theme with a white background and minimal visual elements, providing a clean look.
- The plot shows a simple design without any distracting elements.

### Example: Classic Theme (`theme_classic()`)

The `theme_classic()` gives your plot a classic look with a white background and black axes lines.

```r
# Classic Theme: theme_classic()
ggplot(data = mtcars, aes(x = wt, y = mpg)) +
  geom_point() +
  labs(title = "Scatter Plot with Classic Theme (theme_classic())", 
       x = "Weight (1000 lbs)", 
       y = "Miles per Gallon") +
  theme_classic()
```

### Explanation:
- `theme_classic()`: A theme that mimics classic plots with black axes lines and a white background.
- The plot appears similar to traditional plots often used in publications.

### Example: Light Theme (`theme_light()`)

The `theme_light()` is similar to `theme_gray()` but with a lighter background and grid lines.

```r
# Light Theme: theme_light()
ggplot(data = mtcars, aes(x = wt, y = mpg)) +
  geom_point() +
  labs(title = "Scatter Plot with Light Theme (theme_light())", 
       x = "Weight (1000 lbs)", 
       y = "Miles per Gallon") +
  theme_light()
```

### Explanation:
- `theme_light()`: A theme with a light gray background and light grid lines, providing a softer look.
- The plot is easy on the eyes while retaining the grid lines for reference.

## Customizing Themes with `theme()`

The `theme()` function allows you to customize specific elements of the plot's theme, such as text size, font, background color, and more. This function gives you granular control over the appearance of your plot.

### Example: Customizing Text Elements

You can use `theme()` to modify the appearance of text elements such as the title, axis titles, and axis text.

```r
# Customizing Text Elements
ggplot(data = mtcars, aes(x = wt, y = mpg)) +
  geom_point() +
  labs(title = "Customized Scatter Plot", 
       x = "Weight (1000 lbs)", 
       y = "Miles per Gallon") +
  theme_minimal() +
  theme(
    plot.title = element_text(size = 20, face = "bold", color = "blue"),
    axis.title.x = element_text(size = 15, face = "italic", color = "darkred"),
    axis.title.y = element_text(size = 15, face = "italic", color = "darkred"),
    axis.text = element_text(size = 12, color = "black")
  )
```

### Explanation:
- `plot.title = element_text(...)`: Customizes the title with a larger size, bold font, and blue color.
- `axis.title.x`, `axis.title.y = element_text(...)`: Customizes the x and y axis titles with italic font and dark red color.
- `axis.text = element_text(...)`: Customizes the axis tick labels with a specific size and color.
- The plot displays these customizations, making the text elements more prominent and visually distinct.

### Example: Removing Background Grid Lines

You can remove or modify the background grid lines using the `panel.grid.major` and `panel.grid.minor` theme elements.

```r
# Removing Background Grid Lines
ggplot(data = mtcars, aes(x = wt, y = mpg)) +
  geom_point() +
  labs(title = "Scatter Plot without Grid Lines", 
       x = "Weight (1000 lbs)", 
       y = "Miles per Gallon") +
  theme_minimal() +
  theme(
    panel.grid.major = element_blank(),  # Removes major grid lines
    panel.grid.minor = element_blank()   # Removes minor grid lines
  )
```

### Explanation:
- `panel.grid.major = element_blank()`: Removes the major grid lines.
- `panel.grid.minor = element_blank()`: Removes the minor grid lines.
- The plot now appears without any grid lines, giving it a cleaner look.

### Example: Modifying Background Color

You can also change the background color of the plot using `panel.background`.

```r
# Modifying Background Color
ggplot(data = mtcars, aes(x = wt, y = mpg)) +
  geom_point() +
  labs(title = "Scatter Plot with Custom Background Color", 
       x = "Weight (1000 lbs)", 
       y = "Miles per Gallon") +
  theme_minimal() +
  theme(
    panel.background = element_rect(fill = "lightblue", color = "black")
  )
```

### Explanation:
- `panel.background = element_rect(...)`: Changes the background color of the plotting area to light blue and adds a black border around it.
- The plot displays a light blue background with a black border, making the points stand out against the new background.

## Combining Theme Elements

You can combine multiple theme customizations to create a fully customized plot that meets your specific design needs.

### Example: Fully Customized Plot

```r
# Fully Customized Plot
ggplot(data = mtcars, aes(x = wt, y = mpg)) +
  geom_point(color = "darkorange", size = 3) +
  labs(title = "Fully Customized Scatter Plot", 
       x = "Weight (1000 lbs)", 
       y = "Miles per Gallon") +
  theme_minimal() +
  theme(
    plot.title = element_text(size = 18, face = "bold", hjust = 0.5),
    axis.title.x = element_text(size = 14, color = "darkgreen"),
    axis.title.y = element_text(size = 14, color = "darkgreen"),
    axis.text = element_text(size = 12, color = "darkgray"),
    panel.grid.major = element_line(color = "gray80", size = 0.5),
    panel.background = element_rect(fill = "white"),
    plot.background = element_rect(fill = "lightgray"),
    panel.border = element_rect(color = "black", fill = NA, size = 1)
  )
```

### Explanation:
- `plot.title = element_text(hjust = 0.5)`: Centers the plot title.
- `panel.grid.major = element_line(...)`: Modifies the major grid lines to be lighter.
- `panel.border = element_rect(...)`: Adds a black border around the plot.
- `plot.background = element_rect(...)`: Sets the background color outside the plotting area to light gray.
- The plot combines these customizations to create a distinctive, fully customized appearance.

---

This chapter covers the basics of using themes and customizing theme elements in `ggplot2`. By applying default themes and fine-tuning individual theme elements with the `theme()` function, you can create plots that are not only informative but also visually appealing and tailored to your specific needs.
