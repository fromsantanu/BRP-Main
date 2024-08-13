Joins and Relational Data 
In relational data, it is common to work with multiple tables that need to be combined or merged based on key variables. The dplyr package provides several functions for performing different types of joins, which are essential for combining data frames (or tibbles) based on a common key.

Introduction to Joins
A join is an operation that allows you to combine two data frames by matching rows based on a common key (one or more columns). There are several types of joins, each serving a different purpose depending on how you want to merge the data.

Inner Join: inner_join()
An inner join returns only the rows that have matching values in both data frames. If a key does not exist in both data frames, the corresponding row is dropped.

Example:

r
Copy code
# Load the dplyr package
library(dplyr)

# Create two sample data frames
df1 <- data.frame(
  id = c(1, 2, 3, 4),
  name = c("Alice", "Bob", "Charlie", "David")
)

df2 <- data.frame(
  id = c(2, 3, 4, 5),
  score = c(90, 88, 92, 85)
)

# Perform an inner join on the 'id' column
df_inner <- inner_join(df1, df2, by = "id")

# View the result of the inner join
print(df_inner)
This code combines df1 and df2 using an inner join, returning only the rows where id exists in both data frames.

Left Join: left_join()
A left join returns all rows from the left data frame and the matched rows from the right data frame. If there is no match, the result will contain NA for the right data frame's columns.

Example:

r
Copy code
# Perform a left join on the 'id' column
df_left <- left_join(df1, df2, by = "id")

# View the result of the left join
print(df_left)
This code combines df1 and df2 using a left join, retaining all rows from df1 and matching rows from df2.

Right Join: right_join()
A right join returns all rows from the right data frame and the matched rows from the left data frame. If there is no match, the result will contain NA for the left data frame's columns.

Example:

r
Copy code
# Perform a right join on the 'id' column
df_right <- right_join(df1, df2, by = "id")

# View the result of the right join
print(df_right)
This code combines df1 and df2 using a right join, retaining all rows from df2 and matching rows from df1.

Full Join: full_join()
A full join returns all rows from both data frames, with NA where there are no matching keys. This is useful when you want to retain all data, regardless of matches.

Example:

r
Copy code
# Perform a full join on the 'id' column
df_full <- full_join(df1, df2, by = "id")

# View the result of the full join
print(df_full)
This code combines df1 and df2 using a full join, returning all rows from both data frames.

Semi Join: semi_join()
A semi join returns all rows from the left data frame that have a match in the right data frame. However, it does not return any columns from the right data frame.

Example:

r
Copy code
# Perform a semi join on the 'id' column
df_semi <- semi_join(df1, df2, by = "id")

# View the result of the semi join
print(df_semi)
This code returns all rows from df1 where id exists in df2, but without any columns from df2.

Anti Join: anti_join()
An anti join returns all rows from the left data frame that do not have a match in the right data frame. It is useful for identifying non-overlapping data.

Example:

r
Copy code
# Perform an anti join on the 'id' column
df_anti <- anti_join(df1, df2, by = "id")

# View the result of the anti join
print(df_anti)
This code returns all rows from df1 where id does not exist in df2.

This chapter provides an overview of how to use various join functions in dplyr to combine and manipulate relational data in R. By understanding these different types of joins, you can effectively merge data frames based on key variables and perform complex data manipulations with ease.
