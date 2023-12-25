# Fraud-detection

In this assignment we implemented a machine learning algorithm to detect fraudulent credit card transactions, forming a simplified version of one that could be employed in the real world. In this process, we used different techniques for dimensionality reduction (Clustering.java), developing our decision stump model that worked as our basis weak learner (WeakLearner.java), and we enhanced our accuracy using an AdaBoosting algorithm (BoostingAlgorithm.java). 

Consider a set of m points in 2D space, each representing coordinates of retail establishments, such as shops and restaurants, on a map. In the problem, we are given a data set with n labeled transaction summaries. A transaction summary is an array of m non-negative numbers, one per location, representing the amount of money spent there using a particular credit card. A label is either clean or fraud, indicating whether a fraudulent transaction was detected in the corresponding transaction summary. 

We developed a machine learning model that learns from this data set, in order to label new transaction summaries as either clean or Fraud.

For more details, refer to readme file and the Java files used in the implementation of the model present in the fraud folder. 

