# Chapter 05 - Data Frames in R
## Introduction
A data frame is a two-dimensional, table-like data structure in R that can store different types of variables (numeric, character, factor, etc.) in columns. Data frames are essential for data analysis and manipulation in R. This chapter will cover the basics of data frames, their creation, and various operations that can be performed on data frames.

## Creating a Data Frame
You can create a data frame in R using the data.frame() function. Here's a simple example:

```r
# Create a data frame
my_df <- data.frame(
  Name = c("John", "Jane", "Jim"),
  Age = c(28, 34, 42),
  Gender = c("Male", "Female", "Male"),
  Score = c(85.5, 90.0, 88.0)
)

# Print the data frame
print(my_df)
```

### Output:

```r
  Name Age Gender Score
1 John  28   Male  85.5
2 Jane  34 Female  90.0
3 Jim   42   Male  88.0
```

## Accessing Data Frame Elements
You can access elements of a data frame using the $ operator, square brackets [ , ], or the subset() function.

### Using $ Operator
```r
# Access the 'Age' column
age_column <- my_df$Age
print(age_column)
```

### Using Square Brackets [ , ]
```r
# Access the element in the second row and third column
element <- my_df[2, 3]
print(element)

# Access the entire first row
first_row <- my_df[1, ]
print(first_row)

# Access the entire 'Score' column
score_column <- my_df[, "Score"]
print(score_column)
```

### Using subset() Function
```r
# Subset the data frame to include only rows where Age > 30
subset_df <- subset(my_df, Age > 30)
print(subset_df)
```

## Modifying Data Frame Elements
You can modify elements of a data frame by assigning new values to them.

```r
# Modify the 'Score' of the first row
my_df$Score[1] <- 87.0

# Modify the 'Gender' of the second row
my_df[2, "Gender"] <- "Non-binary"

print(my_df)
```

## Adding Rows and Columns to a Data Frame
You can add rows and columns to a data frame using the rbind() and cbind() functions.

### Adding a New Row
```r
# Add a new row to the data frame
new_row <- data.frame(Name = "Jake", Age = 25, Gender = "Male", Score = 92.0)
my_df <- rbind(my_df, new_row)

print(my_df)
```

### Adding a New Column
```r
# Add a new column 'Passed'
my_df$Passed <- c(TRUE, TRUE, TRUE, TRUE)

print(my_df)
```

## Removing Rows and Columns from a Data Frame
You can remove rows and columns from a data frame using negative indices or the subset() function.

### Removing Rows
```r
# Remove the second row
my_df <- my_df[-2, ]

print(my_df)
```

### Removing Columns
```r
# Remove the 'Passed' column
my_df <- my_df[, -5]

print(my_df)
```

## Data Frame Operations
### Sorting a Data Frame
You can sort a data frame by one or more columns using the order() function.

```r
# Sort the data frame by 'Age' in ascending order
sorted_df <- my_df[order(my_df$Age), ]
print(sorted_df)

# Sort the data frame by 'Score' in descending order
sorted_df <- my_df[order(-my_df$Score), ]
print(sorted_df)
```

### Merging Data Frames
You can merge two data frames using the merge() function.

```r
# Create another data frame
another_df <- data.frame(
  Name = c("John", "Jane", "Jake"),
  Country = c("USA", "UK", "Canada")
)

# Merge the two data frames by 'Name'
merged_df <- merge(my_df, another_df, by = "Name")
print(merged_df)
```

### Summary Statistics
You can obtain summary statistics for a data frame using the summary() function.

```r
# Get summary statistics for the data frame
summary_stats <- summary(my_df)
print(summary_stats)
```

## Summary
Data frames in R are powerful and flexible data structures for storing and manipulating tabular data. This chapter covered the creation of data frames, accessing and modifying elements, adding and removing rows and columns, and performing various operations such as sorting, merging, and obtaining summary statistics. Understanding these operations will help you effectively manage and analyze data in your R programming projects.
