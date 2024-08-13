Chapter: Descriptive Statistics
Overview
Descriptive statistics are essential for summarizing and understanding your data. They provide simple summaries about the sample and the measures. In this chapter, we will cover various functions in R that allow you to compute summary statistics, frequency tables, the five-number summary, and quantiles/percentiles.

1. Summary Statistics
summary()
The summary() function provides a comprehensive overview of a dataset. It returns the minimum, 1st quartile, median, mean, 3rd quartile, and maximum for each numeric column.

r
Copy code
# Example dataset: Randomly generated numbers
set.seed(123)
data <- rnorm(100, mean = 50, sd = 10)

# Using summary() to get a summary of the data
summary(data)
mean()
The mean() function calculates the average of a numeric vector.

r
Copy code
# Calculating the mean
mean_value <- mean(data)
cat("Mean:", mean_value, "\n")
median()
The median() function returns the middle value of a numeric vector when sorted.

r
Copy code
# Calculating the median
median_value <- median(data)
cat("Median:", median_value, "\n")
sd()
The sd() function computes the standard deviation, which measures the amount of variation or dispersion in a set of values.

r
Copy code
# Calculating the standard deviation
sd_value <- sd(data)
cat("Standard Deviation:", sd_value, "\n")
var()
The var() function returns the variance of a numeric vector, which is the square of the standard deviation.

r
Copy code
# Calculating the variance
variance_value <- var(data)
cat("Variance:", variance_value, "\n")
2. Frequency Tables
table()
The table() function creates a frequency table, which shows the number of occurrences of each unique value in a vector.

r
Copy code
# Example dataset: Categorical data
categories <- sample(c("A", "B", "C"), 100, replace = TRUE)

# Creating a frequency table
frequency_table <- table(categories)
print(frequency_table)
prop.table()
The prop.table() function converts a frequency table into a table of proportions, giving the relative frequency of each category.

r
Copy code
# Creating a table of proportions
proportion_table <- prop.table(frequency_table)
print(proportion_table)
3. Five-Number Summary
fivenum()
The fivenum() function returns the five-number summary, which includes the minimum, lower-hinge (1st quartile), median, upper-hinge (3rd quartile), and maximum.

r
Copy code
# Five-number summary of the data
five_number_summary <- fivenum(data)
print(five_number_summary)
4. Quantiles and Percentiles
quantile()
The quantile() function calculates quantiles of a numeric vector. By default, it returns the 0th, 25th, 50th, 75th, and 100th percentiles (which correspond to the minimum, 1st quartile, median, 3rd quartile, and maximum).

r
Copy code
# Quantiles of the data
quantiles <- quantile(data)
print(quantiles)
You can also specify custom quantiles, for example, the 10th and 90th percentiles.

r
Copy code
# 10th and 90th percentiles
custom_quantiles <- quantile(data, probs = c(0.1, 0.9))
print(custom_quantiles)
This chapter covers the basics of descriptive statistics in R. By using these functions, you can quickly get a sense of the distribution, central tendency, and variability of your data, as well as the frequency of different categories. Each function serves a specific purpose and is crucial for preliminary data analysis.


