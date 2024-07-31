# Chapter 09 - Defining Functions in R
## Introduction
Functions in R allow you to encapsulate a block of code that performs a specific task, making your code more modular, reusable, and easier to understand. This chapter will cover the basics of defining functions, including different types of arguments, returning values, and examples of various operations.

## Defining a Simple Function
You can define a simple function in R using the function() keyword.

```r
# Define a function to add two numbers
add_numbers <- function(a, b) {
  sum <- a + b
  return(sum)
}

# Call the function
result <- add_numbers(5, 3)
print(result)
```

### Output:

```r
[1] 8
```

## Function Arguments
### Default Arguments
You can define default values for arguments in a function.

```r
# Define a function with default arguments
greet <- function(name = "Guest") {
  message <- paste("Hello,", name)
  return(message)
}

# Call the function with and without an argument
print(greet("John"))
print(greet())
```

#### Output:

```r
[1] "Hello, John"
[1] "Hello, Guest"
```

### Named Arguments
You can call a function using named arguments, allowing you to pass arguments in any order.

```r
# Define a function to calculate the area of a rectangle
calculate_area <- function(length, width) {
  area <- length * width
  return(area)
}

# Call the function using named arguments
result <- calculate_area(width = 4, length = 5)
print(result)
```

#### Output:

```r
[1] 20
```

### Variable-Length Arguments
You can use the ... (ellipsis) to define a function that accepts a variable number of arguments.

```r
# Define a function to calculate the sum of multiple numbers
sum_numbers <- function(...) {
  numbers <- c(...)
  total <- sum(numbers)
  return(total)
}

# Call the function with a variable number of arguments
result <- sum_numbers(1, 2, 3, 4, 5)
print(result)
```

#### Output:

```r
[1] 15
```

## Returning Values
A function in R can return a value using the return() function. If return() is not explicitly used, the last evaluated expression is returned.

```r
# Define a function to multiply two numbers
multiply_numbers <- function(a, b) {
  product <- a * b
  return(product)
}

# Define a function to divide two numbers without using return()
divide_numbers <- function(a, b) {
  a / b
}

# Call the functions
result1 <- multiply_numbers(6, 4)
print(result1)

result2 <- divide_numbers(10, 2)
print(result2)
```

### Output:

```r
[1] 24
[1] 5
```

## Examples of Various Operations
### Recursive Function
You can define recursive functions in R to solve problems like calculating the factorial of a number.

```r
# Define a recursive function to calculate the factorial of a number
factorial <- function(n) {
  if (n <= 1) {
    return(1)
  } else {
    return(n * factorial(n - 1))
  }
}

# Call the function
result <- factorial(5)
print(result)
```

#### Output:

```r
[1] 120
```

### Anonymous Functions
You can define anonymous (or lambda) functions in R using the function() keyword without assigning them to a variable.

```r
# Use an anonymous function to double the elements of a vector
vec <- c(1, 2, 3, 4, 5)
doubled_vec <- sapply(vec, function(x) x * 2)
print(doubled_vec)
```

#### Output:

```r
[1]  2  4  6  8 10
```

## Higher-Order Functions
Functions in R can take other functions as arguments or return functions as results.

```r
# Define a function that returns another function
make_power_function <- function(power) {
  function(x) {
    x ^ power
  }
}

# Create a square function
square <- make_power_function(2)

# Call the square function
result <- square(4)
print(result)
```

### Output:

```r
[1] 16
```

## Summary
Defining functions in R is crucial for writing modular, reusable, and maintainable code. This chapter covered the basics of defining functions, including different types of arguments (default, named, and variable-length), returning values, and examples of various operations such as recursive functions, anonymous functions, and higher-order functions. Understanding these concepts will help you write more efficient and organized R programs.
