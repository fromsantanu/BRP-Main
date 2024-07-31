# Chapter 10 - Dealing with Objects in R
## Introduction
In R, everything is an object. Understanding how to create, manipulate, and inspect objects is crucial for effective programming. This chapter covers the basics of dealing with objects in R, including creating objects, checking their type and structure, modifying objects, and examples of various types of operations.

## Creating Objects
You can create objects in R using the assignment operator <- or =.

```r
# Create a numeric object
num <- 42

# Create a character object
char <- "Hello, R!"

# Create a vector object
vec <- c(1, 2, 3, 4, 5)

# Create a matrix object
mat <- matrix(1:9, nrow = 3)

# Create a data frame object
df <- data.frame(Name = c("John", "Jane"), Age = c(30, 25))

# Create a list object
lst <- list(name = "John", age = 30, scores = c(85, 90, 88))

# Print the objects
print(num)
print(char)
print(vec)
print(mat)
print(df)
print(lst)
```

## Checking Object Type and Structure
You can check the type and structure of an object using functions like class(), typeof(), str(), and summary().

```r
# Check the class of an object
print(class(vec))

# Check the type of an object
print(typeof(vec))

# Check the structure of an object
str(df)

# Get a summary of an object
summary(df)
```

## Modifying Objects
You can modify objects in R by assigning new values to them.

### Modifying Vectors
```r
# Modify the second element of a vector
vec[2] <- 10
print(vec)
```

### Modifying Matrices
```r
# Modify the element in the second row and third column of a matrix
mat[2, 3] <- 20
print(mat)
```
### Modifying Data Frames
```r
# Modify the 'Age' column of a data frame
df$Age[2] <- 26
print(df)

# Add a new column to the data frame
df$Gender <- c("Male", "Female")
print(df)
```
### Modifying Lists
```r
# Modify an element in a list
lst$age <- 31
print(lst)

# Add a new element to the list
lst$gender <- "Male"
print(lst)
```

## Object Operations
### Object Coercion
You can convert objects from one type to another using functions like as.numeric(), as.character(), as.factor(), etc.

```r
# Convert a numeric vector to a character vector
char_vec <- as.character(vec)
print(char_vec)

# Convert a character vector to a numeric vector
num_vec <- as.numeric(char_vec)
print(num_vec)
```

### Object Comparison
You can compare objects using relational operators (==, !=, <, >, <=, >=).

```r
# Compare two numeric objects
result <- num == 42
print(result)

# Compare two character objects
result <- char == "Hello, R!"
print(result)
```

### Object Subsetting
You can extract subsets of objects using indexing and logical conditions.

```r
# Subset a vector
subset_vec <- vec[vec > 3]
print(subset_vec)

# Subset a data frame
subset_df <- df[df$Age > 25, ]
print(subset_df)
```

### Object Aggregation
You can aggregate data using functions like sum(), mean(), sd(), min(), max(), etc.

```r
# Sum of vector elements
sum_vec <- sum(vec)
print(sum_vec)

# Mean of vector elements
mean_vec <- mean(vec)
print(mean_vec)

# Standard deviation of vector elements
sd_vec <- sd(vec)
print(sd_vec)
```

## Summary
Dealing with objects in R is fundamental to programming in the language. This chapter covered creating objects, checking their type and structure, modifying objects, and performing various operations such as coercion, comparison, subsetting, and aggregation. Understanding these concepts will help you effectively manage and manipulate data in your R programming projects.
