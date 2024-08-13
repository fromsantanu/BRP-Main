Chapter: Hypothesis Testing
Overview
Hypothesis testing is a statistical method used to make decisions about a population based on sample data. In R, several functions are available to perform various types of hypothesis tests, including t-tests, ANOVA, Chi-square tests, proportion tests, and non-parametric tests. This chapter will guide you through these tests with code examples.

1. t-Tests
t.test()
The t.test() function is used to perform t-tests, which compare the means of two groups to determine if they are statistically different from each other.

One-Sample t-Test
A one-sample t-test compares the mean of a single sample to a known value (usually the population mean).

r
Copy code
# Example data: Sample of weights
set.seed(123)
sample_data <- rnorm(30, mean = 65, sd = 10)

# Performing a one-sample t-test
t_test_result <- t.test(sample_data, mu = 70)
print(t_test_result)
Two-Sample t-Test
A two-sample t-test compares the means of two independent samples.

r
Copy code
# Example data: Weights of two different groups
group1 <- rnorm(30, mean = 65, sd = 10)
group2 <- rnorm(30, mean = 70, sd = 10)

# Performing a two-sample t-test
t_test_result <- t.test(group1, group2)
print(t_test_result)
Paired t-Test
A paired t-test compares means from the same group at different times (e.g., before and after treatment).

r
Copy code
# Example data: Before and after weights
before <- rnorm(30, mean = 65, sd = 10)
after <- before + rnorm(30, mean = 2, sd = 5)

# Performing a paired t-test
t_test_result <- t.test(before, after, paired = TRUE)
print(t_test_result)
2. ANOVA (Analysis of Variance)
aov()
ANOVA is used to compare the means of three or more groups. The aov() function in R fits a linear model and performs an ANOVA.

r
Copy code
# Example data: Three different groups
group1 <- rnorm(30, mean = 65, sd = 10)
group2 <- rnorm(30, mean = 70, sd = 10)
group3 <- rnorm(30, mean = 75, sd = 10)

# Combining the data
data <- data.frame(
  weight = c(group1, group2, group3),
  group = factor(rep(c("Group1", "Group2", "Group3"), each = 30))
)

# Performing ANOVA
anova_result <- aov(weight ~ group, data = data)
summary(anova_result)
anova()
The anova() function is used to compare nested models or to perform an ANOVA on a fitted model.

r
Copy code
# Example: ANOVA on a fitted linear model
model <- lm(weight ~ group, data = data)
anova_result <- anova(model)
print(anova_result)
3. Chi-Square Tests
chisq.test()
The chisq.test() function is used for Chi-square tests, which assess whether observed frequencies differ from expected frequencies.

Chi-Square Test for Independence
This test checks if two categorical variables are independent.

r
Copy code
# Example data: Contingency table
observed <- matrix(c(20, 15, 10, 5), nrow = 2)

# Performing Chi-square test
chi_square_result <- chisq.test(observed)
print(chi_square_result)
Chi-Square Goodness-of-Fit Test
This test checks if an observed distribution matches an expected distribution.

r
Copy code
# Example data: Observed frequencies
observed <- c(50, 30, 20)

# Expected probabilities
expected <- c(0.5, 0.3, 0.2)

# Performing Chi-square goodness-of-fit test
chi_square_result <- chisq.test(observed, p = expected)
print(chi_square_result)
4. Proportion Tests
prop.test()
The prop.test() function tests the equality of proportions in one or more groups.

One-Proportion Test
This test compares the proportion in a sample to a known proportion.

r
Copy code
# Example data: Number of successes and total observations
successes <- 45
n <- 100

# Performing one-proportion test
prop_test_result <- prop.test(successes, n, p = 0.5)
print(prop_test_result)
Two-Proportion Test
This test compares the proportions between two independent groups.

r
Copy code
# Example data: Successes and total observations for two groups
successes <- c(45, 30)
n <- c(100, 80)

# Performing two-proportion test
prop_test_result <- prop.test(successes, n)
print(prop_test_result)
5. Non-Parametric Tests
wilcox.test()
The wilcox.test() function performs the Wilcoxon rank-sum test (for two independent samples) or the Wilcoxon signed-rank test (for paired samples).

Wilcoxon Rank-Sum Test
This test compares the distributions of two independent samples.

r
Copy code
# Example data: Two independent groups
group1 <- rnorm(30, mean = 65, sd = 10)
group2 <- rnorm(30, mean = 70, sd = 10)

# Performing Wilcoxon rank-sum test
wilcox_test_result <- wilcox.test(group1, group2)
print(wilcox_test_result)
Wilcoxon Signed-Rank Test
This test compares the distributions of paired samples.

r
Copy code
# Example data: Paired samples
before <- rnorm(30, mean = 65, sd = 10)
after <- before + rnorm(30, mean = 2, sd = 5)

# Performing Wilcoxon signed-rank test
wilcox_test_result <- wilcox.test(before, after, paired = TRUE)
print(wilcox_test_result)
kruskal.test()
The kruskal.test() function performs the Kruskal-Wallis test, a non-parametric alternative to ANOVA, which compares the distributions of three or more groups.

r
Copy code
# Example data: Three different groups
group1 <- rnorm(30, mean = 65, sd = 10)
group2 <- rnorm(30, mean = 70, sd = 10)
group3 <- rnorm(30, mean = 75, sd = 10)

# Combining the data
data <- data.frame(
  weight = c(group1, group2, group3),
  group = factor(rep(c("Group1", "Group2", "Group3"), each = 30))
)

# Performing Kruskal-Wallis test
kruskal_test_result <- kruskal.test(weight ~ group, data = data)
print(kruskal_test_result)
shapiro.test()
The shapiro.test() function tests whether a sample comes from a normal distribution.

r
Copy code
# Example data: Normally distributed data
normal_data <- rnorm(50, mean = 0, sd = 1)

# Performing Shapiro-Wilk test for normality
shapiro_test_result <- shapiro.test(normal_data)
print(shapiro_test_result)
This chapter provides an introduction to various hypothesis testing techniques in R. These tests are fundamental tools for data analysis, allowing you to make inferences about populations based on sample data. Each section includes practical code examples to help you understand how to apply these tests to your own data.


