Chapter: Generalized Linear Models
Overview
Generalized Linear Models (GLMs) are an extension of linear models that allow for response variables to have error distribution models other than a normal distribution. They are particularly useful when the data does not meet the assumptions of linear regression, such as when dealing with binary outcomes or count data. In this chapter, we will cover logistic regression, Poisson regression, and how to fit and diagnose these models in R.

1. Logistic Regression
glm()
Logistic regression is used when the dependent variable is binary (i.e., it has two possible outcomes, often coded as 0 and 1). The glm() function in R can be used to fit a logistic regression model by specifying the family as binomial.

Example: Predicting Probability of Success
r
Copy code
# Example data: Predictor and binary outcome
set.seed(123)
predictor <- rnorm(100)
outcome <- rbinom(100, 1, prob = 1 / (1 + exp(-predictor)))

# Fitting a logistic regression model
model_logistic <- glm(outcome ~ predictor, family = binomial)

# Viewing the model summary
summary(model_logistic)
Interpreting the Logistic Regression Summary
The summary() function provides:

Coefficients: Estimates for the intercept and predictor(s). These are in log-odds units.
Null deviance: A measure of how well the model with no predictors (only the intercept) fits the data.
Residual deviance: A measure of how well the model with predictors fits the data.
AIC: A measure of the model's quality, taking into account the number of parameters. Lower AIC values indicate a better model.
Predicting Probabilities
You can use the model to predict the probability of the outcome for new data.

r
Copy code
# Predicting probabilities for new data
new_data <- data.frame(predictor = c(-1, 0, 1))
predicted_probabilities <- predict(model_logistic, newdata = new_data, type = "response")
print(predicted_probabilities)
2. Poisson Regression
glm()
Poisson regression is used when the dependent variable represents count data (i.e., non-negative integers). The glm() function is used with the family specified as poisson.

Example: Predicting Count Data
r
Copy code
# Example data: Predictor and count outcome
set.seed(123)
predictor <- rnorm(100)
outcome <- rpois(100, lambda = exp(0.5 * predictor))

# Fitting a Poisson regression model
model_poisson <- glm(outcome ~ predictor, family = poisson)

# Viewing the model summary
summary(model_poisson)
Interpreting the Poisson Regression Summary
The summary() function for a Poisson regression model provides:

Coefficients: Estimates for the intercept and predictor(s). These are in the log scale of the rate parameter (lambda).
Null deviance and Residual deviance: Similar to logistic regression, these indicate the fit of the model.
AIC: Lower values indicate a better model fit.
Predicting Counts
You can use the model to predict the expected count for new data.

r
Copy code
# Predicting counts for new data
new_data <- data.frame(predictor = c(-1, 0, 1))
predicted_counts <- predict(model_poisson, newdata = new_data, type = "response")
print(predicted_counts)
3. Model Fitting and Diagnostics
summary()
The summary() function provides detailed information about the model fit, including coefficient estimates, standard errors, z-values, and p-values.

r
Copy code
# Viewing the summary of the logistic regression model
summary(model_logistic)

# Viewing the summary of the Poisson regression model
summary(model_poisson)
anova()
The anova() function can be used to compare nested models or to perform a chi-square test on the deviance to determine if the inclusion of additional predictors significantly improves the model.

Comparing Models with ANOVA
r
Copy code
# Example: Adding a second predictor to the logistic regression model
set.seed(123)
predictor2 <- rnorm(100)
model_logistic2 <- glm(outcome ~ predictor + predictor2, family = binomial)

# Comparing the models
anova(model_logistic, model_logistic2, test = "Chisq")

# Example: Comparing Poisson models
model_poisson2 <- glm(outcome ~ predictor + predictor2, family = poisson)
anova(model_poisson, model_poisson2, test = "Chisq")
Diagnostic Plots
Diagnostic plots help assess the assumptions of the model and identify potential outliers or influential points.

r
Copy code
# Generating diagnostic plots for the logistic regression model
par(mfrow = c(2, 2))
plot(model_logistic)

# Generating diagnostic plots for the Poisson regression model
par(mfrow = c(2, 2))
plot(model_poisson)
Interpretation of Diagnostic Plots
Residuals vs Fitted: Used to check the assumption of linearity in the log-odds or log scale. A random scatter suggests a good fit.
Normal Q-Q: Checks if the residuals are approximately normally distributed (important for larger samples).
Scale-Location: Used to check homoscedasticity. A horizontal line suggests constant variance.
Residuals vs Leverage: Identifies influential points that may disproportionately affect the model.
This chapter provides an introduction to Generalized Linear Models (GLMs) in R, including logistic regression and Poisson regression. The glm() function is versatile for fitting a variety of models, and understanding how to interpret and diagnose these models is crucial for accurate statistical analysis.


