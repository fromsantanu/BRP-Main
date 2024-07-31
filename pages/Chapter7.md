# Chapter 07 - Decision Structures in R
## Introduction
Decision structures in R allow you to control the flow of your program based on conditions. These structures include if statements, if-else statements, nested if-else statements, and switch statements. This chapter will cover the basics of decision structures and provide examples of various types of operations.

## If Statements
The if statement allows you to execute a block of code only if a specified condition is true.

```r
# Define a variable
x <- 10

# If statement
if (x > 5) {
  print("x is greater than 5")
}
```

### Output:

```r
[1] "x is greater than 5"
```

## If-Else Statements
The if-else statement allows you to execute one block of code if a condition is true and another block of code if the condition is false.

```r
# Define a variable
y <- 3

# If-else statement
if (y > 5) {
  print("y is greater than 5")
} else {
  print("y is not greater than 5")
}
```

### Output:

```r
[1] "y is not greater than 5"
```

## Nested If-Else Statements
You can nest if-else statements to create more complex decision structures.

```r
# Define a variable
z <- 7

# Nested if-else statement
if (z > 10) {
  print("z is greater than 10")
} else if (z > 5) {
  print("z is greater than 5 but not greater than 10")
} else {
  print("z is 5 or less")
}
```

### Output:

```r
[1] "z is greater than 5 but not greater than 10"
```

## Ifelse Function
The ifelse() function is a vectorized conditional function that operates on vectors and returns a value based on the condition.

```r
# Define a vector
vec <- c(4, 7, 10, 1, 3)

# Use ifelse() function
result <- ifelse(vec > 5, "Greater than 5", "5 or less")
print(result)
```

### Output:

```r
[1] "5 or less"     "Greater than 5" "Greater than 5" "5 or less"     "5 or less"
```
   
## Switch Statements
The switch() function allows you to select one of many code blocks to execute.

```r
# Define a variable
option <- 2

# Switch statement
result <- switch(option,
                 "First option",
                 "Second option",
                 "Third option",
                 "Invalid option")

print(result)
```

### Output:

```r
[1] "Second option"
```

## Combining Logical Conditions
You can combine multiple logical conditions using logical operators such as & (and), | (or), and ! (not).

### Using And Operator &
```r
# Define variables
a <- 8
b <- 12

# If statement with and operator
if (a > 5 & b > 10) {
  print("Both conditions are true")
}
```

#### Output:

```r
[1] "Both conditions are true"
```
### Using Or Operator |
```r
# Define variables
a <- 3
b <- 15

# If statement with or operator
if (a > 5 | b > 10) {
  print("At least one condition is true")
}
```

#### Output:

```r
[1] "At least one condition is true"
```

### Using Not Operator !

```r
# Define a variable
c <- FALSE

# If statement with not operator
if (!c) {
  print("c is false")
}
```

#### Output:

```r
[1] "c is false"
```

## Summary
Decision structures in R are essential for controlling the flow of your program based on conditions. This chapter covered the basics of if statements, if-else statements, nested if-else statements, the ifelse function, switch statements, and combining logical conditions using logical operators. Understanding these structures will help you write more flexible and dynamic R programs.
