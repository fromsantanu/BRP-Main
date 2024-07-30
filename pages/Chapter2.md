# Chapter 02 - Vectors
Vectors are one of the most fundamental data structures in R. They are used to store sequences of elements of the same type. Here’s an overview of vectors and some common operations performed on them.

## Basic Operations
### Creating Vectors
Vectors can be created using the c() function, which combines elements into a vector.

```R
# Numeric vector
num_vec <- c(1, 2, 3, 4, 5)

# Character vector
char_vec <- c("apple", "banana", "cherry")

# Logical vector
log_vec <- c(TRUE, FALSE, TRUE)
```
### Accessing Elements
You can access elements of a vector using square brackets [].

```R
# Access the second element
num_vec[2]  # Output: 2

# Access multiple elements
num_vec[c(1, 3, 5)]  # Output: 1 3 5
```
### Modifying Vectors
You can modify elements of a vector by assigning new values.

```R
# Change the third element
num_vec[3] <- 10

# Append elements to a vector
num_vec <- c(num_vec, 6, 7)
```

## Vector Operations
### Arithmetic Operations
Arithmetic operations on vectors are performed element-wise.

```R
# Addition
a <- c(1, 2, 3)
b <- c(4, 5, 6)
c <- a + b  # Output: 5 7 9

# Multiplication
d <- a * b  # Output: 4 10 18
```
### Mathematical Functions
R provides many built-in functions to operate on vectors.

```R
# Sum of elements
sum(num_vec)  # Output: sum of elements in num_vec

# Mean of elements
mean(num_vec)  # Output: mean of elements in num_vec

# Maximum and Minimum
max(num_vec)  # Output: maximum element in num_vec
min(num_vec)  # Output: minimum element in num_vec
```
### Logical Operations
Logical operations on vectors are also element-wise.

```R
# Comparison
e <- a > 2  # Output: FALSE FALSE TRUE

# Logical AND
f <- c(TRUE, FALSE, TRUE)
g <- c(FALSE, TRUE, TRUE)
h <- f & g  # Output: FALSE FALSE TRUE
```
### Subsetting Vectors
You can subset vectors using logical conditions.

```R
# Subset elements greater than 3
subset_vec <- num_vec[num_vec > 3]  # Output: elements of num_vec greater than 3
```
## Vector Functions

### length()
Get the number of elements in a vector.

```R
length(num_vec)  # Output: length of num_vec
```
### sort()
Sort the elements of a vector.

```R
sorted_vec <- sort(num_vec)  # Output: sorted elements of num_vec
```
### unique()
Get the unique elements of a vector.

```R
unique_vec <- unique(c(1, 1, 2, 3, 3, 4))  # Output: 1 2 3 4
```
### Combining Vectors
You can combine multiple vectors using the c() function.

```R
# Combine two vectors
combined_vec <- c(a, b)  # Output: combined elements of a and b
```
### Replicating Vectors
You can replicate elements of a vector using the rep() function.

```R
# Replicate elements of a vector
rep_vec <- rep(c(1, 2, 3), times = 2)  # Output: 1 2 3 1 2 3
rep_vec_each <- rep(c(1, 2, 3), each = 2)  # Output: 1 1 2 2 3 3
```
#### Understanding vectors and their operations is crucial for effective data manipulation and analysis in R, as they form the basis of more complex data structures like matrices and data frames.

