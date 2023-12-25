Programming Assignment 7: Fraud Detection

/* *****************************************************************************
 *  Describe how you implemented the Clustering constructor
 **************************************************************************** */
First we initialize m and k.
The constructor has a local EdgeWeightedGraph G variable with m vertices (repre-
senting the locations) and  its edges represent the distances between the
locations. Then, we generate the MST by Kruskal agorithm through the kruskal
variable and store the MST edges separately in the array mstE. Then we sort
the mstE array by the edges weight and create a new graph clusterG with m vertices
by adding the m-k first edges of mstE in order to the clusterG. Finally,
we use CC datatype to get the clusters of clusterG and use it to initialize the
instance variable cluster.
/* *****************************************************************************
 *  Describe how you implemented the WeakLearner constructor
 **************************************************************************** */
Prior to the construct, we define a helper class Pair that implements
comparable for sorting the inputs and keeping the weights. It has a coord and
idx objects that indicate  the value of a point at any coordinate, and the
index of the point. Finally, we define the compareTo for comparing the coord
variables of two different pairs.
Now we go to the constructor.
First we initialize n as the input.length, and k as input[0].length because
it represents the dimension of the points. Then we do the following next lines
for each i = 0, ..., k-1 (reducing the problem to 1 dimension):
  - Create array of n pairs storing coord = input[j][i] and idx = j, j=0,...,n-1
  - sort array of pairs by coordinate
  - Then we do the following procedure for sign =0:
      - iterate over the elements of array. If we find one pair that corresponds
      to 1 (we can find this by labels[pair[j].idx]), then we sum weights[pair[j].idx]
      to a counter named val.
      - Then, if val > currBest, we set curBest = val, BestDim = i, BestVal =
      pairs[j].coord, and bestSgn=0.
      - do this for all j =0,...,n-1
  - Then repeat it again for sign =1 the analogous procedure

After iterating this procedure over all dimensions, we have the BestVal,
BestDim, BestSgn and curBest.



/* *****************************************************************************
 *  Consider the large_training.txt and large_test.txt datasets.
 *  Run the boosting algorithm with different values of k and T (iterations),
 *  and calculate the test data set accuracy and plot them below.
 *
 **************************************************************************** */

      k          T         test accuracy       time (seconds)
   --------------------------------------------------------------------------
      3         100             0.752            0.51
      3         1000            2.476            0.78
      5         100             0.841            0.67
      5         1000            0.822            3.83
      10        1000            0.955            7.22
      12        1000            0.963            8.63
      13        1000            0.964            9.24
      15        800             0.973            9.047
      16        800             0.976            8.571
      17        800             0.971            8.814
      45        450             0.978            9.488

/* *****************************************************************************
 *  Find the values of k and T that maximize the test data set accuracy,
 *  while running under 10 second. Write them down (as well as the accuracy)
 *  and explain:
 *   1. Your strategy to find the optimal k, T.
 *   2. Why a small value of T leads to low test accuracy.
 *   3. Why a k that is too small or too big leads to low test accuracy.
 **************************************************************************** */
k = 45, T = 500 give 0.978 accuracy.
1.
The strategy for finding k and T consisted of fixing T and setting a window
for k. Then we did binary search on k to find the largest k for which the algorithm
gives lower than 10s.
After varying the values of T (we used 100,200,...) and we compared the results
for each of our sampled Ts.

2.
A small value of T represents a low number of weak learners being used. Since
weak learners don't have high accuracy, averaging out the results from a small
number of weak learners may not give high accuracy.

3. A k that is too small clusters the data points into a smaller number of
clusters, hence increasing the variance in each cluster. Because of that, points
that are not similar might be in the same cluster, leading to a bad learner.
In contrast, a high value of k gives cluster that are more uniform.

/* *****************************************************************************
 *  Known bugs / limitations.
 **************************************************************************** */
none

/* *****************************************************************************
 *  Describe any serious problems you encountered.
 **************************************************************************** */
none

/* *****************************************************************************
 *  List any other comments here. Feel free to provide any feedback
 *  on how much you learned from doing the assignment, and whether
 *  you enjoyed doing it.
 **************************************************************************** */
we liked the assignment
