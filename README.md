# customer-segmentation
<h2>Introduction : </h2>

<p> <ul>
    <li>Customer segmentation is one of the most well-known Data Science projects. Customer segmentation is a well-known example of unsupervised learning. </li>
    <li>Clustering is used by businesses to identify customer groups and target their potential user base. 
To sell to each group effectively, they categorize consumers based on shared characteristics such as gender, age, hobbies, and purchasing patterns. </li>
    <li>K-means clustering may be used to visualize the gender and age distributions. Following that, their annual earnings and spending patterns are examined.</li>
</p></ul>

<h2>DATASET : </h2>
<p>customers.csv </p>

<h2>PACKAGES REQURIED : </h2><ul>
<li>plotrix </li>
<li>purr </li>
<li>cluster</li>
<li>gridExtra</li>
<li>grid</li>
<li>nbClust</li>
<li>factoextra</li>
<li>ggplot2</li>
<li>dplyr</li>
</ul>

K-means Algorithm
While using the k-means clustering algorithm, the first step is to indicate the number of clusters (k) that we wish to produce in the final output. The algorithm starts by selecting k objects from dataset randomly that will serve as the initial centers for our clusters. These selected objects are the cluster means, also known as centroids. Then, the remaining objects have an assignment of the closest centroid. This centroid is defined by the Euclidean Distance present between the object and the cluster mean. We refer to this step as “cluster assignment”.

When the assignment is complete, the algorithm proceeds to calculate new mean value of each cluster present in the data. After the recalculation of the centers, the observations are checked if they are closer to a different cluster. Using the updated cluster mean, the objects undergo reassignment. This goes on repeatedly through several iterations until the cluster assignments stop altering. The clusters that are present in the current iteration are the same as the ones obtained in the previous iteration. Summing up the K-means clustering –

We specify the number of clusters that we need to create.
The algorithm selects k objects at random from the dataset. This object is the initial cluster or mean.
The closest centroid obtains the assignment of a new observation. We base this assignment on the Euclidean Distance between object and the centroid.
k clusters in the data points update the centroid through calculation of the new mean values present in all the data points of the cluster. The kth cluster’s centroid has a length of p that contains means of all variables for observations in the k-th cluster. We denote the number of variables with p.
Iterative minimization of the total within the sum of squares. Then through the iterative minimization of the total sum of the square, the assignment stop wavering when we achieve maximum iteration. The default value is 10 that the R software uses for the maximum iterations.
we calculate the clustering algorithm for several values of k. This can be done by creating a variation within k from 1 to 10 clusters. We then calculate the total intra-cluster sum of square (iss). Then, we proceed to plot iss based on the number of k clusters.
This plot denotes the appropriate number of clusters required in our model. In the plot, the location of a bend or a knee is the indication of the optimum number of clusters. Let us implement this in R as follows –

Code: library(purrr) set.seed(123)
function to calculate total intra-cluster sum of square iss <- function(k) { kmeans(customer_data[,3:5],k,iter.max=100,nstart=100,algorithm="Lloyd" ) $tot.withinss }

k.values <- 1:10 iss_values <- map_dbl(k.values, iss)

plot(k.values, iss_values, type="b", pch = 19, frame = FALSE, xlab="Number of clusters K", ylab="Total intra-clusters sum of squares")

Visualizing the Clustering Results using the First Two Principle Components
A line chart or line plot or line graph or curve chart is a type of chart which displays information as a series of data points called 'markers' connected by straight line segments. It is a basic type of chart common in many fields. Used across many fields, this type of graph can be quite helpful in depicting the changes in values over time. We are going to use ggplot for depicting the line plot.

Code: set.seed(1) ggplot(customer_data, aes(x =Annual.Income..k.., y = Spending.Score..1.100.)) + geom_point(stat = "identity", aes(color = as.factor(k6$cluster))) + scale_color_discrete(name=" ", breaks=c("1", "2", "3", "4", "5","6"), labels=c("Cluster 1", "Cluster 2", "Cluster 3", "Cluster 4", "Cluster 5","Cluster 6")) + ggtitle("Segments of Mall Customers", subtitle = "Using K-means Clustering")