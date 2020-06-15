Clustering is an important task in machine learning and data mining.

Here, I will list the traditional and modern clustering methods. If you want to cluster something. This blog may help you.

For each clustering methods, there are three things to kind in mind:
- What is the clustering objective? Show the objective function?
- What is the input?
- What is the output?


# K-Means

- Description from scikit-learn document: The k-means algorithm divides a set of *N* samples *X* in to *K* disjoint clusters *C*, each described by the mean  <img src="https://render.githubusercontent.com/render/math?math=u_j"> of the samples in the cluster. The means are commonly called the ccluster "centriods"; note that they are not, in genereal, points from *X*, although they live in the same space.

- **The clustering objective**: 
minimize the **inertia** or **within-cluster sum-of-squares**: <img src="https://render.githubusercontent.com/render/math?math=\displaystyle\sum_{i=0}^n \displaystyle\min_{u_j \in C}(||x_i-u_j||^2)">

- Inputs: samples *X*, the number of clusters *k*
- Outputs: cluster of each sample

## Standard k-means
<img src="./figures/k-means.png" width='800'>

## k-means++


<img src="./figures/k-means++.png"
      width='800'>

## Mini-Batch K-Means

<img src="./figures/Mini_batch_kmeans.png"
      width='400'>


References:
- [Scikit-learn document-Clustering-K-Means](https://scikit-learn.org/stable/modules/clustering.html#k-means)
- MacQueen, J. (1967, June). [Some methods for classification and analysis of multivariate observations](http://citeseer.ist.psu.edu/viewdoc/download;jsessionid=07EDF90CB90A2BA3AEB24B6B52CA9DC9?doi=10.1.1.308.8619&rep=rep1&type=pdf). In Proceedings of the fifth Berkeley symposium on mathematical statistics and probability (Vol. 1, No. 14, pp. 281-297).
- Arthur, David, and Sergei Vassilvitskii. ["k-means++ the advantages of careful seeding."](https://dl.acm.org/doi/pdf/10.5555/1283383.1283494) Proceedings of the eighteenth annual ACM-SIAM symposium on Discrete algorithms. 2007.
- Sculley, David. ["Web-scale k-means clustering."](https://dl.acm.org/doi/pdf/10.1145/1772690.1772862) Proceedings of the 19th international conference on World wide web. 2010.

# Affinity propagation

- High level description: Affinity propagation measures the similarity between pairs of data points. Real-valued messages are exchanged between data points until a high-quality set of exemplars and corresponding clusters gradually emerges.

There are two kinds of message to transfer: "responsibility"  <img src="https://render.githubusercontent.com/render/math?math=r(i,k)"> and “availability” <img src="https://render.githubusercontent.com/render/math?math=a(i,k)">.

"responsibility"  <img src="https://render.githubusercontent.com/render/math?math=r(i,k)"> sent from data point i to candidate exemplar point k, reflects the accumulated evidence for how well-suited point k is to serve as the exemplar for point i, taking into account other potential exemplars for point i.

“availability” <img src="https://render.githubusercontent.com/render/math?math=a(i,k)"> sent from candidate exemplar point k to point i, reflects the accumulated evidence for how appropriate it would be for point i to choose point k as its exemplar, taking into account the support from other points that point k should be an exemplar.

The algorithm is described as follows:
- To begin with, the availibities are initialized to zero: a(i,k)=0
- <img src="https://render.githubusercontent.com/render/math?math=r(i,k) \gets  s(i,k) - max \{a(i, k') + s(i, k')\} for \forall k' \neq k"> 
- <img src="https://render.githubusercontent.com/render/math?math=a(i,k) \gets s(i,k)-min\{0, r(k, k)+\sum_{i'\, \text{s.t.}\, i' \notin \{i,k\}} \max\{0, r(i',k)\}\} "> 
- The “self-availability” a(k,k) is updated differently: <img src="https://render.githubusercontent.com/render/math?math=a(k,k) \gets  \displaystyle\sum_{i' \, \text{s.t.}\, i' \neq k} \max\{0, r(i',k)\}\}"> 

References:
- Frey, Brendan J., and Delbert Dueck. ["Clustering by passing messages between data points."](https://science.sciencemag.org/content/315/5814/972) science 315.5814 (2007): 972-976.


# Mean-shift

# Spectral clustering

# Ward hierarchical clustering

# Agglomerative clustering

# DBSCAN

# OPTICS

# Gaussian mixtures

# Brich
