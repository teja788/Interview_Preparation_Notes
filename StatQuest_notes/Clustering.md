# DBSCAN

* DBSCAN stands for Density Based Spatial Clustering of Applications with Noise
* It is a density based clustering algorthim
* Advantages
    * You don't need to specify # of clusters like k-means
    * It can find arbitrarily shaped clusters or even a cluster surrounding another cluster
    * It creates seperate category for outliers and those won't effect the clusters

* There are two parameters in DBSSCAN 
    * epsilon : distance from a point to check what other points are present around
    * minPoints: Min no. of points within epsilon distance from a point to consider it a corepoint

* Algorthim steps:
  * All the points are divided into core-points, non-core points(border point), outliers
    * Core point : If a point has no. of points equal or greater than minPoints present in a epsilon distance circle drawn around it
    * Non Core point(border point): If a point has lesser than minPoints(but non-zero) around it in epsilon distance
    * Outliers: If a point has no points in the circle around it

  * Now we randomly select a Core point as a cluster and add all the other points in epsilon distance around it to same cluster 
  * We repeat the same to all the core points added
  * If a Non-Core point is in epsilon distance to a core point it is added to the cluster but process is not repeated with non-core point
  * After one cluster is done. we again pick one of remaining core points as a new cluster and repeat the process
  * We don't touch outliers

* minPoints generally should be greater than dimension + 1 and atleast greater than 3. Rule of thumb is to choose 2 * Dimensions
* epsilon can be choosen by k-distance graph. if we choose small distance clusters won't form. If we choose big everything becomes one cluster. 
* Disadvantages:
  * epsilon is tough to find without good understanding of distribution of distances
  * DBSCAN cannot make good clusters in Data where densities in different clusters are very different
  * If there is a tie for a non-core point it is choosen in first cluster which was selected

* HDBSCAN is another clustering algorthim made by some of same authors. It is better and we don't need to choose epsilon in it. Can be explored further in future.

* Ref - 
   * https://en.wikipedia.org/wiki/DBSCAN
   * https://www.youtube.com/watch?v=RDZUdRSDOok
