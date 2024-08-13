Chapter: Cluster Analysis
Overview
Cluster analysis is a technique used to group similar objects into clusters, where objects within the same cluster are more similar to each other than to those in other clusters. This chapter covers hierarchical clustering, k-means clustering, and cluster validation using the silhouette method in R.

1. Hierarchical Clustering
hclust()
Hierarchical clustering is a method of cluster analysis that seeks to build a hierarchy of clusters. The hclust() function in R performs hierarchical clustering on a set of dissimilarities.

Example: Performing Hierarchical Clustering
r
Copy code
# Example data: Simulated multivariate data
set.seed(123)
data <- matrix(rnorm(50 * 5), ncol = 5)
rownames(data) <- paste("Sample", 1:50, sep = "")

# Calculating the distance matrix
dist_matrix <- dist(data)

# Performing hierarchical clustering
hc_result <- hclust(dist_matrix, method = "complete")

# Plotting the dendrogram
plot(hc_result, main = "Hierarchical Clustering Dendrogram", xlab = "", sub = "", cex = 0.8)
Cutting the Dendrogram into Clusters
You can cut the dendrogram at a specific height to create a specified number of clusters.

r
Copy code
# Cutting the dendrogram into 3 clusters
clusters <- cutree(hc_result, k = 3)

# Viewing the cluster memberships
print(clusters)

# Adding rectangles around the clusters in the dendrogram
rect.hclust(hc_result, k = 3, border = "red")
Interpreting Hierarchical Clustering
Dendrogram: A tree-like diagram that shows the arrangement of the clusters produced by hierarchical clustering. The height at which branches merge indicates the dissimilarity between clusters.
Cutting the Dendrogram: Allows you to decide on the number of clusters by cutting the tree at a chosen height.
2. k-Means Clustering
kmeans()
k-means clustering partitions the data into k clusters, where each data point belongs to the cluster with the nearest mean. The kmeans() function in R performs k-means clustering.

Example: Performing k-Means Clustering
r
Copy code
# Example data: Simulated multivariate data
set.seed(123)
data <- matrix(rnorm(50 * 2), ncol = 2)

# Performing k-means clustering with 3 clusters
set.seed(123)
kmeans_result <- kmeans(data, centers = 3, nstart = 25)

# Viewing the k-means clustering results
print(kmeans_result)

# Plotting the clusters
plot(data, col = kmeans_result$cluster, pch = 19, main = "k-Means Clustering")
points(kmeans_result$centers, col = 1:3, pch = 8, cex = 2)
Interpreting k-Means Clustering
Cluster Centers: The mean location of the points in each cluster.
Within-cluster sum of squares: A measure of the compactness of the clusters. Lower values indicate tighter clusters.
Choosing the Number of Clusters
Choosing the optimal number of clusters (k) is often done using methods like the "Elbow method" or silhouette analysis.

r
Copy code
# Example: Using the "Elbow method" to determine the number of clusters
wss <- (nrow(data)-1)*sum(apply(data, 2, var))
for (i in 2:15) wss[i] <- sum(kmeans(data, centers = i, nstart = 25)$tot.withinss)
plot(1:15, wss, type = "b", pch = 19, frame = FALSE, xlab = "Number of Clusters K", ylab = "Total Within-Cluster Sum of Squares")
3. Cluster Validation
silhouette()
The silhouette method provides a measure of how similar an object is to its own cluster compared to other clusters. It can be used to assess the quality of clustering.

Example: Validating Clusters with Silhouette Analysis
r
Copy code
# Ensure the 'cluster' package is installed
if(!require(cluster)) install.packages("cluster")

library(cluster)

# Performing silhouette analysis for k-means clustering
silhouette_result <- silhouette(kmeans_result$cluster, dist(data))

# Plotting the silhouette plot
plot(silhouette_result, main = "Silhouette Plot for k-Means Clustering")
Interpreting the Silhouette Plot
Silhouette Width: Values range from -1 to 1. A value close to 1 indicates that the object is well matched to its own cluster and poorly matched to neighboring clusters. A value close to 0 indicates that the object lies between two clusters. A negative value indicates that the object might have been assigned to the wrong cluster.
Silhouette Plot: Visualizes the silhouette width of each point in the data, providing insights into the quality and structure of the clustering.
Summary
Hierarchical Clustering: Builds a hierarchy of clusters and is often visualized using a dendrogram. The hclust() function is used to perform hierarchical clustering.
k-Means Clustering: Partitions the data into k clusters with the nearest mean, performed using the kmeans() function.
Cluster Validation: The silhouette method (silhouette()) provides a measure of how well each data point fits within its assigned cluster.
This chapter provides an introduction to cluster analysis in R, covering hierarchical clustering, k-means clustering, and cluster validation using the silhouette method. These techniques are fundamental for exploring the structure of multivariate data and identifying natural groupings within the data.


