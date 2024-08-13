# Chapter: Survival Analysis

## Overview

Survival analysis is a branch of statistics that deals with the analysis of time-to-event data. It is commonly used in clinical trials, reliability engineering, and other fields where the time until an event (such as death, failure, or relapse) is of interest. In this chapter, we will cover the Kaplan-Meier estimator, Cox proportional hazards model, and the log-rank test in R.

## 1. Kaplan-Meier Estimator

### `survfit()`

The Kaplan-Meier estimator is a non-parametric statistic used to estimate the survival function from lifetime data. It provides an estimate of the probability of survival beyond a certain time point.

#### Example: Estimating Survival Curves

```r
# Ensure the 'survival' package is installed
if(!require(survival)) install.packages("survival")

library(survival)

# Example data: Time-to-event data and censoring information
time <- c(5, 8, 12, 16, 23, 27, 30, 34, 35, 42)
event <- c(1, 1, 0, 1, 1, 0, 1, 0, 1, 0)  # 1 = event occurred, 0 = censored

# Creating a Surv object
surv_object <- Surv(time, event)

# Fitting the Kaplan-Meier estimator
km_fit <- survfit(surv_object ~ 1)

# Viewing the summary of the Kaplan-Meier estimator
summary(km_fit)

# Plotting the Kaplan-Meier survival curve
plot(km_fit, xlab = "Time", ylab = "Survival Probability", main = "Kaplan-Meier Survival Curve",
     col = "blue", lwd = 2)
```

### Interpreting the Kaplan-Meier Curve

- **Survival Probability**: The y-axis represents the estimated probability of survival beyond each time point.
- **Steps in the Curve**: Each step down corresponds to an event (e.g., death, failure).
- **Censored Data**: Observations that are censored (i.e., the event did not occur during the study period) are represented by ticks on the curve.

## 2. Cox Proportional Hazards Model

### `coxph()`

The Cox proportional hazards model is a semi-parametric model used to assess the effect of several variables on survival time. It models the hazard rate as a function of the covariates.

#### Example: Fitting a Cox Proportional Hazards Model

```r
# Example data: Time-to-event data, event indicator, and covariates
age <- c(50, 55, 60, 65, 70, 75, 80, 85, 90, 95)
treatment <- factor(c("A", "A", "B", "B", "A", "A", "B", "B", "A", "B"))

# Fitting a Cox proportional hazards model
cox_model <- coxph(surv_object ~ age + treatment)

# Viewing the summary of the Cox model
summary(cox_model)
```

### Interpreting the Cox Model Summary

- **Coefficients**: These represent the log-hazard ratios associated with each covariate.
- **exp(coef)**: The hazard ratios, which indicate the effect of each covariate on the hazard (risk of event occurring).
- **p-value**: Tests the null hypothesis that the corresponding coefficient is zero (no effect).
- **Concordance**: A measure of the model's predictive accuracy.

### Plotting the Cox Model

You can visualize the effect of covariates on survival by plotting the survival curves for different levels of a covariate.

```r
# Plotting the survival curves for different treatments
plot(survfit(cox_model, newdata = data.frame(age = 70, treatment = "A")),
     col = "red", lwd = 2, main = "Survival Curves by Treatment", xlab = "Time", ylab = "Survival Probability")
lines(survfit(cox_model, newdata = data.frame(age = 70, treatment = "B")),
      col = "blue", lwd = 2)
legend("bottomleft", legend = c("Treatment A", "Treatment B"), col = c("red", "blue"), lwd = 2)
```

## 3. Log-Rank Test

### `survdiff()`

The log-rank test is a non-parametric test used to compare survival distributions between two or more groups. It is commonly used to test the null hypothesis that survival curves are identical across groups.

#### Example: Performing a Log-Rank Test

```r
# Performing the log-rank test to compare survival between treatment groups
log_rank_test <- survdiff(surv_object ~ treatment)

# Viewing the results of the log-rank test
print(log_rank_test)
```

### Interpreting the Log-Rank Test

- **Chi-squared statistic**: The test statistic used to determine whether there is a significant difference between the survival curves.
- **p-value**: The probability of observing a chi-squared statistic as extreme as, or more extreme than, the observed value under the null hypothesis. A small p-value (typically < 0.05) indicates that the survival distributions are significantly different between groups.

---

This chapter provides an introduction to survival analysis in R, covering the Kaplan-Meier estimator, Cox proportional hazards model, and the log-rank test. These methods are fundamental for analyzing time-to-event data and understanding the impact of covariates on survival.
