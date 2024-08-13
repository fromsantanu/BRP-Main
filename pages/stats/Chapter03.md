# Chapter: Probability Distributions

## Overview

Probability distributions describe how the values of a random variable are distributed. In R, the `stats` package provides functions to work with common probability distributions, including functions for density, cumulative distribution, quantile calculations, and random number generation. In this chapter, we will cover some of the most common distributions: Normal, Binomial, Poisson, and Exponential.

## 1. Common Distributions

### Normal Distribution

The Normal distribution, also known as the Gaussian distribution, is a continuous probability distribution defined by its mean (`mu`) and standard deviation (`sigma`).

### Binomial Distribution

The Binomial distribution describes the number of successes in a fixed number of independent Bernoulli trials, each with the same probability of success.

### Poisson Distribution

The Poisson distribution gives the probability of a given number of events happening in a fixed interval of time or space, assuming these events occur with a known constant mean rate and independently of the time since the last event.

### Exponential Distribution

The Exponential distribution describes the time between events in a Poisson process, where events occur continuously and independently at a constant average rate.

## 2. Density Functions

Density functions give the probability density function (PDF) for continuous distributions or the probability mass function (PMF) for discrete distributions.

### `dnorm()` - Normal Distribution

```r
# Probability density of a normal distribution
x <- seq(-3, 3, by = 0.1)
density_normal <- dnorm(x, mean = 0, sd = 1)

# Plotting the density function
plot(x, density_normal, type = "l", main = "Normal Distribution (mean=0, sd=1)",
     ylab = "Density", xlab = "x")
```

### `dbinom()` - Binomial Distribution

```r
# Probability mass of a binomial distribution
n <- 10  # number of trials
p <- 0.5  # probability of success
x <- 0:n
density_binom <- dbinom(x, size = n, prob = p)

# Plotting the probability mass function
plot(x, density_binom, type = "h", main = "Binomial Distribution (n=10, p=0.5)",
     ylab = "Probability", xlab = "Number of successes")
```

### `dpois()` - Poisson Distribution

```r
# Probability mass of a Poisson distribution
lambda <- 2  # rate
x <- 0:10
density_pois <- dpois(x, lambda = lambda)

# Plotting the probability mass function
plot(x, density_pois, type = "h", main = "Poisson Distribution (lambda=2)",
     ylab = "Probability", xlab = "Number of events")
```

### `dexp()` - Exponential Distribution

```r
# Probability density of an exponential distribution
x <- seq(0, 5, by = 0.1)
rate <- 1  # rate
density_exp <- dexp(x, rate = rate)

# Plotting the density function
plot(x, density_exp, type = "l", main = "Exponential Distribution (rate=1)",
     ylab = "Density", xlab = "x")
```

## 3. Cumulative Distribution Functions

Cumulative distribution functions (CDFs) give the probability that a random variable is less than or equal to a certain value.

### `pnorm()` - Normal Distribution

```r
# Cumulative probability of a normal distribution
pnorm_value <- pnorm(1.96, mean = 0, sd = 1)
cat("Cumulative probability P(X <= 1.96):", pnorm_value, "\n")
```

### `pbinom()` - Binomial Distribution

```r
# Cumulative probability of a binomial distribution
pbinom_value <- pbinom(6, size = 10, prob = 0.5)
cat("Cumulative probability P(X <= 6):", pbinom_value, "\n")
```

### `ppois()` - Poisson Distribution

```r
# Cumulative probability of a Poisson distribution
ppois_value <- ppois(3, lambda = 2)
cat("Cumulative probability P(X <= 3):", ppois_value, "\n")
```

### `pexp()` - Exponential Distribution

```r
# Cumulative probability of an exponential distribution
pexp_value <- pexp(2, rate = 1)
cat("Cumulative probability P(X <= 2):", pexp_value, "\n")
```

## 4. Quantile Functions

Quantile functions return the value below which a given percentage of observations fall.

### `qnorm()` - Normal Distribution

```r
# Quantile (inverse CDF) of a normal distribution
qnorm_value <- qnorm(0.975, mean = 0, sd = 1)
cat("Quantile corresponding to 97.5%:", qnorm_value, "\n")
```

### `qbinom()` - Binomial Distribution

```r
# Quantile (inverse CDF) of a binomial distribution
qbinom_value <- qbinom(0.8, size = 10, prob = 0.5)
cat("Quantile corresponding to 80%:", qbinom_value, "\n")
```

### `qpois()` - Poisson Distribution

```r
# Quantile (inverse CDF) of a Poisson distribution
qpois_value <- qpois(0.9, lambda = 2)
cat("Quantile corresponding to 90%:", qpois_value, "\n")
```

### `qexp()` - Exponential Distribution

```r
# Quantile (inverse CDF) of an exponential distribution
qexp_value <- qexp(0.5, rate = 1)
cat("Quantile corresponding to 50%:", qexp_value, "\n")
```

## 5. Random Number Generation

R provides functions to generate random numbers from these distributions, which is useful for simulations and modeling.

### `rnorm()` - Normal Distribution

```r
# Generating random numbers from a normal distribution
random_norm <- rnorm(100, mean = 0, sd = 1)

# Plotting the histogram of generated random numbers
hist(random_norm, breaks = 10, main = "Random Numbers from Normal Distribution",
     xlab = "Value", ylab = "Frequency")
```

### `rbinom()` - Binomial Distribution

```r
# Generating random numbers from a binomial distribution
random_binom <- rbinom(100, size = 10, prob = 0.5)

# Plotting the histogram of generated random numbers
hist(random_binom, breaks = 10, main = "Random Numbers from Binomial Distribution",
     xlab = "Number of successes", ylab = "Frequency")
```

### `rpois()` - Poisson Distribution

```r
# Generating random numbers from a Poisson distribution
random_pois <- rpois(100, lambda = 2)

# Plotting the histogram of generated random numbers
hist(random_pois, breaks = 10, main = "Random Numbers from Poisson Distribution",
     xlab = "Number of events", ylab = "Frequency")
```

### `rexp()` - Exponential Distribution

```r
# Generating random numbers from an exponential distribution
random_exp <- rexp(100, rate = 1)

# Plotting the histogram of generated random numbers
hist(random_exp, breaks = 10, main = "Random Numbers from Exponential Distribution",
     xlab = "Value", ylab = "Frequency")
```

---

This chapter provides a comprehensive introduction to working with probability distributions in R. Each section covers a different aspect of probability distributions, from calculating densities to generating random numbers. By mastering these functions, you'll be well-equipped to handle a variety of statistical modeling tasks in R.
