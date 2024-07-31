# Chapter 08 - Repetitive Constructs in R

## Introduction
Repetitive constructs in R allow you to execute a block of code multiple times. These constructs include for loops, while loops, repeat loops, and apply functions. This chapter will cover the basics of repetitive constructs and provide examples of various types of operations.

## For Loops
The for loop is used to iterate over a sequence of elements.

```r
# Define a vector
vec <- c(1, 2, 3, 4, 5)

# For loop
for (i in vec) {
  print(i)
}
```

### Output:

```r
[1] 1
[1] 2
[1] 3
[1] 4
[1] 5
```

## While Loops
The while loop is used to execute a block of code as long as a specified condition is true.

```r
# Initialize a variable
i <- 1

# While loop
while (i <= 5) {
  print(i)
  i <- i + 1
}
```

### Output:

```r
Copy code
[1] 1
[1] 2
[1] 3
[1] 4
[1] 5
```

## Repeat Loops
The repeat loop is used to execute a block of code indefinitely until a specified condition is met.

```r
# Initialize a variable
i <- 1

# Repeat loop
repeat {
  print(i)
  i <- i + 1
  if (i > 5) {
    break
  }
}
```

### Output:

```r
Copy code
[1] 1
[1] 2
[1] 3
[1] 4
[1] 5
```
## Apply Functions
The apply family of functions provides a way to apply a function to elements of an array, list, or data frame.

### apply() Function
The apply() function is used to apply a function to the rows or columns of a matrix or array.

```r
# Define a matrix
mat <- matrix(1:9, nrow = 3)

# Apply sum function to the rows
row_sums <- apply(mat, 1, sum)
print(row_sums)

# Apply sum function to the columns
col_sums <- apply(mat, 2, sum)
print(col_sums)
```

#### Output:

```r
[1]  6 15 24
[1] 12 15 18
```

### lapply() Function
The lapply() function is used to apply a function to each element of a list and return a list.

```r
# Define a list
my_list <- list(a = 1:5, b = 6:10, c = 11:15)

# Apply sum function to each element
list_sums <- lapply(my_list, sum)
print(list_sums)
```

#### Output:

```r
$a
[1] 15

$b
[1] 40

$c
[1] 65
```

### sapply() Function
The sapply() function is similar to lapply() but simplifies the result to a vector or matrix if possible.

```r
# Apply sum function to each element and simplify the result
list_sums <- sapply(my_list, sum)
print(list_sums)
```

#### Output:

```r
 a  b  c 
15 40 65
```

### tapply() Function
The tapply() function is used to apply a function over subsets of a vector.

```r
# Define a vector and a factor
vec <- c(1, 2, 3, 4, 5, 6)
fac <- factor(c("A", "A", "B", "B", "A", "B"))

# Apply sum function to subsets of the vector
subset_sums <- tapply(vec, fac, sum)
print(subset_sums)
```

#### Output:

```r
 A  B 
 8 13
```

### mapply() Function
The mapply() function is a multivariate version of sapply() and applies a function to multiple lists or vectors.

```r
# Define two vectors
vec1 <- 1:5
vec2 <- 6:10

# Apply sum function to each pair of elements
pair_sums <- mapply(sum, vec1, vec2)
print(pair_sums)
```

#### Output:

```r
[1]  7  9 11 13 15
```

## Summary
Repetitive constructs in R are essential for performing iterative operations. This chapter covered the basics of for loops, while loops, repeat loops, and apply functions (apply(), lapply(), sapply(), tapply(), and mapply()). Understanding these constructs will help you write more efficient and concise R programs.
