# Chapter: Case Studies and Examples

## Overview

In this chapter, we'll explore real-world examples of statistical analysis using R's `stats` package. We'll walk through common statistical tasks such as hypothesis testing, regression analysis, ANOVA, and time series analysis, and provide solutions to these tasks using R.

## 1. Hypothesis Testing: t-test for Comparing Means

### Case Study: Comparing the Average Heights of Two Groups

Suppose you have two groups of individuals, and you want to test whether there is a significant difference in their average heights.

#### Data Setup

```r
# Example data: Heights of two groups
set.seed(123)
group1 <- rnorm(30, mean = 170, sd = 5)
group2 <- rnorm(30, mean = 175, sd = 5)

# Visualizing the data
boxplot(group1, group2, names = c("Group 1", "Group 2"),
        main = "Boxplot of Heights by Group", ylab = "Height (cm)")
```

#### Performing a t-test

```r
# Performing a two-sample t-test
t_test_result <- t.test(group1, group2)

# Viewing the results
print(t_test_result)
```

### Interpretation

- **p-value**: If the p-value is less than 0.05, you reject the null hypothesis and conclude that there is a significant difference in the average heights between the two groups.
- **Confidence Interval**: The 95% confidence interval provides a range within which the true difference in means is likely to lie.

## 2. Regression Analysis: Simple Linear Regression

### Case Study: Predicting House Prices Based on Size

Suppose you want to predict the price of a house based on its size (in square feet).

#### Data Setup

```r
# Example data: House sizes (in square feet) and prices (in $1000)
size <- c(1500, 1700, 2000, 2100, 2200, 2400, 2800, 3000, 3200, 3400)
price <- c(300, 320, 360, 400, 410, 450, 490, 520, 540, 600)

# Visualizing the data
plot(size, price, main = "House Size vs. Price",
     xlab = "Size (sq ft)", ylab = "Price ($1000)", pch = 19)
```

#### Performing Simple Linear Regression

```r
# Fitting a linear regression model
lm_model <- lm(price ~ size)

# Viewing the summary of the model
summary(lm_model)

# Adding the regression line to the plot
abline(lm_model, col = "blue", lwd = 2)
```

### Interpretation

- **Coefficients**: The intercept and slope tell you the baseline price of a house and how much the price increases for each additional square foot.
- **R-squared**: The proportion of variance in the price that is explained by the size of the house.
- **p-value**: Tests whether the slope of the regression line is significantly different from zero.

## 3. ANOVA: Comparing Multiple Group Means

### Case Study: Comparing Test Scores Across Three Teaching Methods

Suppose you want to test whether three different teaching methods result in different test scores.

#### Data Setup

```r
# Example data: Test scores for three different teaching methods
method1 <- c(85, 88, 90, 92, 87, 85, 91, 89)
method2 <- c(78, 85, 80, 79, 84, 82, 83, 81)
method3 <- c(92, 94, 95, 90, 93, 91, 96, 94)

# Combining the data
scores <- c(method1, method2, method3)
method <- factor(rep(c("Method 1", "Method 2", "Method 3"), each = 8))

# Visualizing the data
boxplot(scores ~ method, main = "Test Scores by Teaching Method",
        ylab = "Test Score")
```

#### Performing One-Way ANOVA

```r
# Performing one-way ANOVA
anova_result <- aov(scores ~ method)

# Viewing the summary of the ANOVA
summary(anova_result)
```

### Interpretation

- **p-value**: If the p-value is less than 0.05, you reject the null hypothesis and conclude that at least one teaching method results in significantly different test scores.
- **Post-Hoc Analysis**: If the ANOVA is significant, consider performing a post-hoc test (e.g., Tukey's HSD) to determine which methods differ.

## 4. Time Series Analysis: Analyzing and Forecasting Sales Data

### Case Study: Forecasting Monthly Sales

Suppose you have monthly sales data for a year and want to forecast the next three months.

#### Data Setup

```r
# Example data: Monthly sales data (in units)
sales <- c(200, 220, 210, 250, 260, 240, 300, 310, 280, 290, 320, 330)

# Creating a time series object
sales_ts <- ts(sales, start = c(2023, 1), frequency = 12)

# Plotting the time series
plot.ts(sales_ts, main = "Monthly Sales Data", ylab = "Sales (units)", xlab = "Month")
```

#### Fitting an ARIMA Model and Forecasting

```r
# Fitting an ARIMA model
library(forecast)
arima_model <- auto.arima(sales_ts)

# Forecasting the next 3 months
forecast_result <- forecast(arima_model, h = 3)

# Plotting the forecast
plot(forecast_result, main = "Sales Forecast")
```

### Interpretation

- **ARIMA Model**: The ARIMA model is chosen based on the best fit to the data.
- **Forecast**: The forecast provides estimates of future sales along with confidence intervals.

## 5. Proportion Testing: Comparing Two Proportions

### Case Study: Testing the Effectiveness of a Marketing Campaign

Suppose you want to compare the conversion rates of two different marketing campaigns.

#### Data Setup

```r
# Example data: Number of conversions and total users exposed to two campaigns
conversions1 <- 50
total1 <- 200

conversions2 <- 70
total2 <- 250

# Performing a two-proportion z-test
prop_test_result <- prop.test(c(conversions1, conversions2), c(total1, total2))

# Viewing the results
print(prop_test_result)
```

### Interpretation

- **p-value**: If the p-value is less than 0.05, you conclude that the conversion rates for the two campaigns are significantly different.
- **Confidence Interval**: Provides the range within which the true difference in proportions lies.

## Summary

This chapter provided a hands-on approach to solving real-world statistical problems using R's `stats` package. We covered:

- **Hypothesis Testing**: t-tests for comparing group means.
- **Regression Analysis**: Simple linear regression for predicting outcomes.
- **ANOVA**: Comparing means across multiple groups.
- **Time Series Analysis**: Analyzing and forecasting time-dependent data.
- **Proportion Testing**: Comparing proportions between two groups.

Each example included detailed R code, plots, and interpretations to help you apply these methods to your own data analysis tasks.
