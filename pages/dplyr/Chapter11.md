Case Studies and Examples 
In this chapter, we will explore real-world examples of data manipulation using dplyr. These examples will demonstrate how to handle common data manipulation tasks that you might encounter in your day-to-day data analysis work. By walking through these case studies, you'll gain a deeper understanding of how to use dplyr effectively.

Case Study 1: Analyzing Sales Data
Scenario:
You work for a retail company and need to analyze sales data to understand trends and performance across different regions and product categories.

Data:
r
Copy code
# Load necessary packages
library(dplyr)

# Create a sample sales data frame
sales_data <- data.frame(
  region = c("North", "South", "East", "West", "North", "South", "East", "West"),
  product = c("A", "A", "A", "A", "B", "B", "B", "B"),
  sales = c(100, 150, 120, 130, 200, 180, 160, 170),
  date = as.Date(c("2023-01-01", "2023-01-01", "2023-01-02", "2023-01-02", "2023-01-03", "2023-01-03", "2023-01-04", "2023-01-04"))
)

# View the sales data
print(sales_data)
Task 1: Summarize Total Sales by Region and Product
You want to calculate the total sales for each region and product.

r
Copy code
# Summarize total sales by region and product
total_sales <- sales_data %>%
  group_by(region, product) %>%
  summarise(total_sales = sum(sales))

# View the summarized data
print(total_sales)
This code groups the data by region and product and calculates the total sales for each combination.

Task 2: Calculate the Percentage of Total Sales by Region
You want to understand what percentage of total sales each region contributes.

r
Copy code
# Calculate the total sales across all regions
total_sales_all <- sum(sales_data$sales)

# Calculate the percentage of total sales by region
sales_percentage <- sales_data %>%
  group_by(region) %>%
  summarise(total_sales = sum(sales)) %>%
  mutate(percentage = (total_sales / total_sales_all) * 100)

# View the percentage of total sales by region
print(sales_percentage)
This code calculates the total sales for each region and then computes the percentage of the overall sales that each region contributes.

Task 3: Identify Top-Performing Products by Region
You want to find the top-performing product in each region based on sales.

r
Copy code
# Identify the top-performing product by region
top_products <- sales_data %>%
  group_by(region, product) %>%
  summarise(total_sales = sum(sales)) %>%
  arrange(region, desc(total_sales)) %>%
  slice(1)

# View the top-performing products by region
print(top_products)
This code calculates total sales for each product within each region, orders them by sales, and selects the top product for each region.

Case Study 2: Customer Churn Analysis
Scenario:
You work for a telecommunications company and need to analyze customer data to understand churn rates and identify patterns among customers who left the service.

Data:
r
Copy code
# Create a sample customer data frame
customer_data <- data.frame(
  customer_id = 1:10,
  age = c(25, 40, 35, 23, 45, 50, 33, 36, 28, 55),
  tenure = c(12, 24, 36, 6, 48, 60, 18, 30, 9, 72),
  churn = c(TRUE, FALSE, TRUE, TRUE, FALSE, FALSE, TRUE, FALSE, TRUE, FALSE)
)

# View the customer data
print(customer_data)
Task 1: Calculate the Churn Rate
You need to calculate the overall churn rate among customers.

r
Copy code
# Calculate the churn rate
churn_rate <- customer_data %>%
  summarise(churn_rate = mean(churn) * 100)

# View the churn rate
print(churn_rate)
This code calculates the churn rate by taking the mean of the churn column (where TRUE represents churned customers).

Task 2: Analyze Churn by Age Group
You want to understand how churn rates vary by age group.

r
Copy code
# Define age groups
customer_data <- customer_data %>%
  mutate(age_group = case_when(
    age < 30 ~ "Under 30",
    age >= 30 & age < 40 ~ "30-39",
    age >= 40 & age < 50 ~ "40-49",
    age >= 50 ~ "50+"
  ))

# Calculate churn rate by age group
churn_by_age <- customer_data %>%
  group_by(age_group) %>%
  summarise(churn_rate = mean(churn) * 100)

# View churn rate by age group
print(churn_by_age)
This code creates age groups and then calculates the churn rate for each group.

Task 3: Identify High-Risk Customers
You want to identify customers who are at high risk of churning, defined as customers with a tenure of less than 12 months.

r
Copy code
# Identify high-risk customers
high_risk_customers <- customer_data %>%
  filter(tenure < 12)

# View high-risk customers
print(high_risk_customers)
This code filters the data to find customers with a tenure of less than 12 months, identifying them as high risk for churn.

Case Study 3: Financial Data Analysis
Scenario:
You work for a financial services company and need to analyze transactional data to identify trends and key metrics.

Data:
r
Copy code
# Create a sample transactions data frame
transactions_data <- data.frame(
  transaction_id = 1:10,
  customer_id = c(1, 2, 3, 1, 2, 3, 4, 5, 4, 5),
  amount = c(100, 200, 150, 120, 210, 130, 180, 220, 160, 250),
  transaction_date = as.Date(c("2023-01-01", "2023-01-02", "2023-01-03", "2023-01-04", "2023-01-05", "2023-01-06", "2023-01-07", "2023-01-08", "2023-01-09", "2023-01-10"))
)

# View the transactions data
print(transactions_data)
Task 1: Calculate Total Transaction Amount by Customer
You need to calculate the total transaction amount for each customer.

r
Copy code
# Calculate total transaction amount by customer
total_by_customer <- transactions_data %>%
  group_by(customer_id) %>%
  summarise(total_amount = sum(amount))

# View the total transaction amount by customer
print(total_by_customer)
This code groups the data by customer_id and calculates the total transaction amount for each customer.

Task 2: Identify Transactions Above a Certain Threshold
You want to find all transactions where the amount is above a specific threshold, such as $200.

r
Copy code
# Filter transactions above the threshold
high_value_transactions <- transactions_data %>%
  filter(amount > 200)

# View high-value transactions
print(high_value_transactions)
This code filters the data to include only transactions where the amount exceeds $200.

Task 3: Calculate Daily Transaction Volume
You need to calculate the number of transactions that occurred each day.

r
Copy code
# Calculate daily transaction volume
daily_volume <- transactions_data %>%
  group_by(transaction_date) %>%
  summarise(transaction_count = n())

# View daily transaction volume
print(daily_volume)
This code calculates the number of transactions that occurred on each date.

This chapter provides real-world examples of data manipulation using dplyr. These case studies demonstrate how to handle common tasks such as summarizing data, calculating percentages, filtering rows, and identifying patterns. By following these examples, you can apply similar techniques to your own data analysis projects, making your work more efficient and insightful.
