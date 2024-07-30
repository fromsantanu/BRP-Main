# Chapter 1 - Data Types in R

In R, data types are fundamental elements used to store and manipulate different kinds of data. Here are some of the most commonly used data types in R, along with examples for each:

### Numeric
Used for real numbers (both integer and double).

```R
# Example
x <- 42         # Integer
y <- 3.14       # Double
```
### Integer
Specifically used for integer values.

```R
# Example
z <- as.integer(7)
```
### Character
Used for text or string data.

```R
# Example
name <- "Alice"
```
### Logical
Used for Boolean values (TRUE or FALSE).

```R
# Example
flag <- TRUE
```
### Factor
Used for categorical data with a fixed number of unique values (levels).

```R
# Example
gender <- factor(c("male", "female", "female", "male"))
```
### Date
Used for date values.

```R
# Example
today <- as.Date("2024-07-26")
```
POSIXct / POSIXlt
Used for date and time values.

```R
# Example
now <- as.POSIXct("2024-07-26 14:30:00")
```
### Complex
Used for complex numbers.

```R
# Example
complex_num <- 4 + 3i
```
#### Here are some additional examples to show how these data types are used in practice:
```R
# Numeric
num <- 10.5

# Integer
int <- as.integer(10)

# Character
str <- "Hello, world!"

# Logical
bool <- TRUE

# Factor
colors <- factor(c("red", "green", "blue", "red"))

# Date
birth_date <- as.Date("1990-05-17")

# POSIXct / POSIXlt (Date-Time)
appointment <- as.POSIXct("2024-07-26 09:30:00")

# Complex
comp <- 3 + 2i
```
### Collection Type Data
In addition to these basic types, R also includes data structures that can hold multiple elements of these types, such as vectors, lists, matrices, data frames, and arrays. Here are some examples of these data structures:

```R
# Vector
vec <- c(1, 2, 3, 4, 5)

# List
lst <- list(name = "Alice", age = 25, is_student = TRUE)

# Matrix
mat <- matrix(1:9, nrow = 3, ncol = 3)

# Data Frame
df <- data.frame(
  id = 1:3,
  name = c("Alice", "Bob", "Charlie"),
  score = c(85, 90, 88)
)

# Array
arr <- array(1:8, dim = c(2, 2, 2))
```
#### Understanding these data types and structures is essential for effective data manipulation and analysis in R.

