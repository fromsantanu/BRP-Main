Chapter: Basic Plot Types
In this chapter, we'll explore some of the most common types of plots you can create using ggplot2. Each plot type is represented by a specific geometry function (geom_) that defines how the data should be visualized.

Scatter Plots: geom_point()
Scatter plots are used to display the relationship between two continuous variables. Each point represents an observation in the dataset.

Example: Scatter Plot
r
Copy code
# Load ggplot2 package
library(ggplot2)

# Scatter Plot of Weight vs. Miles per Gallon
ggplot(data = mtcars, aes(x = wt, y = mpg)) +
  geom_point(color = "blue", size = 3) +
  labs(title = "Scatter Plot of MPG vs Weight", 
       x = "Weight (1000 lbs)", 
       y = "Miles per Gallon") +
  theme_minimal()
Explanation:
geom_point(): Adds points to the plot.
The plot shows how the weight of the car (x-axis) is related to its miles per gallon (y-axis).
Line Plots: geom_line()
Line plots are used to display data points connected by straight lines, often used to show trends over time.

Example: Line Plot
r
Copy code
# Line Plot of Horsepower vs. Miles per Gallon
ggplot(data = mtcars, aes(x = hp, y = mpg)) +
  geom_line(color = "red") +
  labs(title = "Line Plot of MPG vs Horsepower", 
       x = "Horsepower", 
       y = "Miles per Gallon") +
  theme_minimal()
Explanation:
geom_line(): Connects the data points with lines.
The plot shows how horsepower (x-axis) is related to miles per gallon (y-axis).
Bar Plots: geom_bar() and geom_col()
Bar plots are used to represent categorical data with rectangular bars. The height of the bars indicates the count or value of the data.

Example: Bar Plot using geom_bar()
r
Copy code
# Bar Plot of Car Cylinders
ggplot(data = mtcars, aes(x = factor(cyl))) +
  geom_bar(fill = "purple") +
  labs(title = "Bar Plot of Car Cylinders", 
       x = "Number of Cylinders", 
       y = "Count") +
  theme_minimal()
Explanation:
geom_bar(): Automatically counts the number of occurrences of each category.
The plot shows the distribution of cars based on the number of cylinders.
Example: Bar Plot using geom_col()
r
Copy code
# Custom Bar Plot with geom_col()
df <- data.frame(
  category = c("A", "B", "C"),
  value = c(10, 20, 15)
)

ggplot(data = df, aes(x = category, y = value)) +
  geom_col(fill = "orange") +
  labs(title = "Bar Plot of Custom Values", 
       x = "Category", 
       y = "Value") +
  theme_minimal()
Explanation:
geom_col(): Plots the values provided in the dataset without counting.
The plot shows custom values for categories A, B, and C.
Histograms: geom_histogram()
Histograms are used to visualize the distribution of a continuous variable by dividing the data into bins and counting the number of observations in each bin.

Example: Histogram
r
Copy code
# Histogram of Miles per Gallon
ggplot(data = mtcars, aes(x = mpg)) +
  geom_histogram(binwidth = 2, fill = "green", color = "black") +
  labs(title = "Histogram of Miles per Gallon", 
       x = "Miles per Gallon", 
       y = "Count") +
  theme_minimal()
Explanation:
geom_histogram(): Creates a histogram with specified binwidth.
The plot shows the distribution of miles per gallon among the cars.
Box Plots: geom_boxplot()
Box plots are used to visualize the distribution, central tendency, and variability of a continuous variable. They also help identify outliers.

Example: Box Plot
r
Copy code
# Box Plot of MPG by Cylinder
ggplot(data = mtcars, aes(x = factor(cyl), y = mpg)) +
  geom_boxplot(fill = "yellow") +
  labs(title = "Box Plot of MPG by Cylinder", 
       x = "Number of Cylinders", 
       y = "Miles per Gallon") +
  theme_minimal()
Explanation:
geom_boxplot(): Creates a box plot that displays the median, quartiles, and outliers.
The plot compares the distribution of miles per gallon across different numbers of cylinders.
Violin Plots: geom_violin()
Violin plots combine aspects of box plots and density plots. They show the distribution of the data and its probability density.

Example: Violin Plot
r
Copy code
# Violin Plot of MPG by Cylinder
ggplot(data = mtcars, aes(x = factor(cyl), y = mpg)) +
  geom_violin(fill = "lightblue") +
  labs(title = "Violin Plot of MPG by Cylinder", 
       x = "Number of Cylinders", 
       y = "Miles per Gallon") +
  theme_minimal()
Explanation:
geom_violin(): Creates a violin plot that displays the density of the data at different values.
The plot compares the distribution and density of miles per gallon across different numbers of cylinders.
This chapter provides an overview of some basic plot types available in ggplot2. Each plot type serves a specific purpose, allowing you to visualize different aspects of your data. By mastering these basic plots, you'll be able to effectively explore and communicate your data insights.
