Chapter: Linear Models
Overview
Linear models are a fundamental tool in statistical analysis, used to describe the relationship between a dependent variable and one or more independent variables. In this chapter, we will cover simple linear regression, multiple linear regression, and how to summarize and diagnose your models in R.

1. Simple Linear Regression
lm()
Simple linear regression models the relationship between a dependent variable and a single independent variable using a straight line. The lm() function in R is used to fit a linear model.

Example: Predicting Weight Based on Height
r
Copy code
# Example data: Height and weight of individuals
set.seed(123)
height <- rnorm(50, mean = 170, sd = 10)
weight <- 0.5 * height + rnorm(50, mean = 0, sd = 5)

# Fitting a simple linear regression model
model_simple <- lm(weight ~ height)

# Viewing the model summary
summary(model_simple)
Interpreting the Summary
The summary() function provides detailed information about the model, including:

Coefficients: Estimates of the intercept and slope.
Residuals: Differences between observed and predicted values.
R-squared: The proportion of variance in the dependent variable explained by the model.
p-value: The significance of the coefficients.
Plotting the Regression Line
r
Copy code
# Plotting the data and the regression line
plot(height, weight, main = "Simple Linear Regression",
     xlab = "Height", ylab = "Weight", pch = 16)
abline(model_simple, col = "blue", lwd = 2)
2. Multiple Linear Regression
lm()
Multiple linear regression models the relationship between a dependent variable and multiple independent variables. The lm() function is also used for this purpose.

Example: Predicting Weight Based on Height and Age
r
Copy code
# Example data: Height, age, and weight of individuals
set.seed(123)
age <- rnorm(50, mean = 30, sd = 5)
weight <- 0.3 * height + 0.2 * age + rnorm(50, mean = 0, sd = 5)

# Fitting a multiple linear regression model
model_multiple <- lm(weight ~ height + age)

# Viewing the model summary
summary(model_multiple)
Interpreting the Multiple Regression Summary
The summary() of a multiple regression model includes:

Coefficients: Estimates for each independent variable.
Adjusted R-squared: A version of R-squared adjusted for the number of predictors.
F-statistic: A measure of the overall significance of the model.
3. Model Summary and Diagnostics
summary()
The summary() function provides a detailed overview of the model, including the coefficients, residuals, and overall fit.

r
Copy code
# Viewing the summary of the multiple linear regression model
summary(model_multiple)
Diagnostic Plots
R provides diagnostic plots to assess the validity of the linear model assumptions. The plot() function can be used to generate these plots.

r
Copy code
# Generating diagnostic plots for the multiple linear regression model
par(mfrow = c(2, 2))  # Arrange plots in a 2x2 grid
plot(model_multiple)
Key Diagnostic Plots:
Residuals vs Fitted: Checks for non-linearity. Ideally, the points should be randomly scattered.
Normal Q-Q: Assesses normality of residuals. Points should fall on a straight line.
Scale-Location: Checks for homoscedasticity (equal variance of residuals). Points should be spread equally.
Residuals vs Leverage: Identifies influential points that could affect the model.
Interpreting Diagnostic Plots
Residuals vs Fitted: A random scatter of points indicates a good fit.
Normal Q-Q: Points that closely follow the diagonal line indicate normally distributed residuals.
Scale-Location: A horizontal line with equal scatter indicates constant variance.
Residuals vs Leverage: Points outside the Cook's distance lines may be influential and worth investigating.
This chapter provides an introduction to building and diagnosing linear models in R. The lm() function is versatile and powerful for fitting both simple and multiple linear regression models. The model diagnostics are crucial for ensuring the assumptions of linear regression are met, leading to more reliable and interpretable results.
