<h1> Customer-Segmentation-using-R </h1>

<p> Customer segmentation project </p>

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

<h2>K-means Algorithm<h2>

<p>While using the k-means clustering algorithm, the first step is to indicate the number of clusters (k) that we wish to produce in the final output. The algorithm starts by selecting k objects from dataset randomly that will serve as the initial centers for our clusters. These selected objects are the cluster means, also known as centroids. Then, the remaining objects have an assignment of the closest centroid. This centroid is defined by the Euclidean Distance present between the object and the cluster mean. We refer to this step as “cluster assignment”.</p>

<p>Process:
1. Randomly select 3 points/centroids for clustering
2. Calculate distance of each datapoint from the centroids. The datapoint
	belongs to the centroid closest to it.
3. Calculate SSE. The goal is to reduce the SSE (sum of squared errors)
4. Update centroids by estimating the mean of each cluster
5. Iterate from step 2 unless the value converges for centroids (centroids no
	longer move much)
</p>