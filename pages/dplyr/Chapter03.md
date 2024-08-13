Advanced Data Manipulation 
As you become more comfortable with basic data manipulation using dplyr, you'll likely encounter situations where more advanced techniques are needed. This chapter covers advanced data manipulation methods, including using mutate() with custom functions, performing conditional mutating with if_else(), and handling multiple conditions with case_when().

Using mutate() with Custom Functions
The mutate() function in dplyr can be used not only to create new variables based on existing ones but also to apply custom functions for more complex operations.

Example:

Suppose you have a data frame with a column representing the scores of students, and you want to create a new column that standardizes these scores (i.e., subtracts the mean and divides by the standard deviation).

r
Copy code
# Load the dplyr package
library(dplyr)

# Create a sample data frame
df <- data.frame(
  name = c("Alice", "Bob", "Charlie", "David", "Eva"),
  score = c(85, 90, 88, 92, 95)
)

# Define a custom function for standardizing scores
standardize <- function(x) {
  (x - mean(x)) / sd(x)
}

# Use mutate() with the custom function to create a standardized_score column
df_standardized <- df %>% mutate(
  standardized_score = standardize(score)
)

# View the data frame with the new standardized_score column
print(df_standardized)
This code applies the custom standardize function to the score column and creates a new standardized_score column.

Conditional Mutating with if_else()
The if_else() function is a vectorized alternative to the base R ifelse() function, providing a more robust and type-safe way to perform conditional operations within mutate().

Example:

Suppose you want to assign a pass/fail status to each student based on their score, with a threshold of 90 points.

r
Copy code
# Use mutate() with if_else() to create a pass_fail column
df_pass_fail <- df %>% mutate(
  pass_fail = if_else(score >= 90, "Pass", "Fail")
)

# View the data frame with the new pass_fail column
print(df_pass_fail)
This code creates a pass_fail column that labels students as "Pass" if their score is 90 or higher and "Fail" otherwise.

Working with case_when()
The case_when() function allows you to evaluate multiple conditions and assign values based on which condition is met. It is especially useful when you have more than two conditions to check.

Example:

Suppose you want to assign letter grades (A, B, C) to students based on their scores, with the following criteria:

"A" for scores 90 and above
"B" for scores between 80 and 89
"C" for scores below 80
r
Copy code
# Use mutate() with case_when() to create a grade column
df_grades <- df %>% mutate(
  grade = case_when(
    score >= 90 ~ "A",
    score >= 80 & score < 90 ~ "B",
    TRUE ~ "C"
  )
)

# View the data frame with the new grade column
print(df_grades)
This code uses case_when() to create a grade column, assigning letter grades based on the specified conditions.

Combining Advanced Techniques
You can also combine these advanced techniques for more complex data manipulation tasks. For example, let's standardize the scores and then assign letter grades based on the standardized scores.

r
Copy code
# Combine custom function, if_else(), and case_when()
df_combined <- df %>% 
  mutate(standardized_score = standardize(score)) %>% 
  mutate(grade = case_when(
    standardized_score >= 1 ~ "A",
    standardized_score >= 0 & standardized_score < 1 ~ "B",
    TRUE ~ "C"
  ))

# View the data frame with the combined results
print(df_combined)
This code first standardizes the score column, then assigns letter grades based on the standardized scores using case_when().

This chapter illustrates how to perform advanced data manipulation in dplyr using mutate() with custom functions, conditional mutating with if_else(), and handling multiple conditions with case_when(). These techniques enable you to handle complex data transformation tasks efficiently within the dplyr framework.
