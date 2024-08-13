Chapter: Multivariate Analysis
Overview
Multivariate analysis involves the observation and analysis of more than one statistical outcome variable at a time. Techniques like Principal Component Analysis (PCA), Factor Analysis, and Multidimensional Scaling (MDS) are commonly used to reduce the dimensionality of the data, explore its structure, and visualize complex relationships between variables. In this chapter, we will cover PCA, Factor Analysis, and MDS in R.

1. Principal Component Analysis (PCA)
prcomp()
Principal Component Analysis (PCA) is a technique used to reduce the dimensionality of a dataset while preserving as much variability as possible. It transforms the original variables into a new set of uncorrelated variables called principal components.

Example: Performing PCA with prcomp()
r
Copy code
# Example data: Simulated multivariate data
set.seed(123)
data <- matrix(rnorm(100 * 5), ncol = 5)
colnames(data) <- paste("Variable", 1:5, sep = "")

# Performing PCA using prcomp
pca_result <- prcomp(data, scale. = TRUE)

# Viewing the summary of the PCA result
summary(pca_result)

# Viewing the loadings (principal components)
print(pca_result$rotation)

# Plotting the variance explained by each principal component
plot(pca_result, type = "l", main = "Scree Plot")
Interpreting PCA Results
Standard deviations: The square roots of the eigenvalues, representing the amount of variance explained by each principal component.
Loadings: The coefficients of the linear combinations of the original variables that define each principal component.
Scree Plot: A plot of the eigenvalues in descending order, used to determine the number of principal components to retain.
Biplot of PCA
r
Copy code
# Plotting a biplot of the first two principal components
biplot(pca_result, main = "PCA Biplot")
princomp()
princomp() is another function in R for PCA, which is primarily based on the covariance matrix. It is less commonly used than prcomp() but is still useful in certain contexts.

Example: Performing PCA with princomp()
r
Copy code
# Performing PCA using princomp
pca_result2 <- princomp(data, cor = TRUE)

# Viewing the summary of the PCA result
summary(pca_result2)

# Plotting a scree plot
plot(pca_result2, type = "lines", main = "Scree Plot using princomp()")
2. Factor Analysis
factanal()
Factor Analysis is a technique used to identify underlying relationships between observed variables. It models the observed variables as linear combinations of potential factors plus error terms.

Example: Performing Factor Analysis
r
Copy code
# Example data: Simulated multivariate data
set.seed(123)
data <- matrix(rnorm(100 * 4), ncol = 4)
colnames(data) <- paste("Variable", 1:4, sep = "")

# Performing Factor Analysis with two factors
factor_analysis_result <- factanal(data, factors = 2, rotation = "varimax")

# Viewing the results of Factor Analysis
print(factor_analysis_result)

# Viewing the loadings
print(factor_analysis_result$loadings)
Interpreting Factor Analysis Results
Loadings: The coefficients that relate each factor to the observed variables. High loadings indicate a strong relationship between a factor and a variable.
Uniqueness: The variance in each observed variable that is unique (not explained by the factors).
Rotations in Factor Analysis
Rotations (e.g., Varimax) are used to make the output more interpretable by achieving a simpler and more interpretable structure.

r
Copy code
# Performing Factor Analysis with different rotation
factor_analysis_result_oblimin <- factanal(data, factors = 2, rotation = "oblimin")

# Viewing the results of Factor Analysis with Oblimin rotation
print(factor_analysis_result_oblimin)
3. Multidimensional Scaling (MDS)
cmdscale()
Multidimensional Scaling (MDS) is a technique used to visualize the level of similarity or dissimilarity of individual cases in a dataset. It maps the data into a lower-dimensional space based on pairwise distances.

Example: Performing MDS
r
Copy code
# Example data: Simulated distance matrix
set.seed(123)
data <- matrix(rnorm(10 * 3), ncol = 3)
dist_matrix <- dist(data)

# Performing Classical MDS
mds_result <- cmdscale(dist_matrix, k = 2)  # k is the number of dimensions

# Plotting the MDS result
plot(mds_result, type = "n", main = "MDS Plot")
text(mds_result, labels = paste("Point", 1:10), cex = 0.8)
Interpreting MDS Results
MDS Plot: Points that are closer together in the plot represent observations that are more similar based on the distance matrix. The axes in MDS do not have a direct interpretation.
Summary
Principal Component Analysis (PCA): Used for dimensionality reduction while retaining the variance in the data.
Factor Analysis: Used to identify underlying factors that explain the correlations among observed variables.
Multidimensional Scaling (MDS): Used to visualize the similarity or dissimilarity between observations in a lower-dimensional space.
This chapter provides an introduction to multivariate analysis techniques in R, including PCA, Factor Analysis, and MDS. These techniques are essential for understanding and visualizing the structure of high-dimensional data.
