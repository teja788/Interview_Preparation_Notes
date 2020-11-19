## Decision Trees Notes:
*	It is a tree like logic structure for making decisions.
*	Top of tree - root node or root, internal nodes have arrows pointing towards them or away from them. Leaf nodes are at end they have inputs to them but no output.
*	Leaf node (terminal node) is considered pure if it has only one category. Otherwise it’s considered impure.
*	We will use raw data to construct a decision tree. Impurity is measured using “Gini”
*	Gini of a node = 1 – (prob of yes)^2 – (prob of no)^2
*	Decision tree algo steps:
    * Take a predictor divide data using it to two leaf nodes. Calculate the GINI impurity of both nodes. Take weighted average of gini impurities of both nodes.
    * Repeat this step for all the predictors select which has the lowest gini impurity as root node.
    * At each internal node we will again repeat the same process for rest of predictors and select the predictor which has lowest gini value to divide.
    * At a node if after dividing we did not get lower impurity than above node for all remaining predictors we will make it a leaf node.
    * Repeat this process until we cannot divide any further based on the given parameters or impurity score. Decision tree is completed.
    * If we have a continuous predictor we sort the data take average of every two points and use it to divide the data. At every divide we will calculate the gini impurity and take the lowest one as cutoff for the predictor to compare with other predictors.
    * If we have multiple categories we will take all the combinations while calculating the gini impurities.
* For regression trees (DV is continuous) we use Sum of squared residuals (SSR) instead of Gini for finding the best division.
*	For Categorical DV largest category in leaf nodes is considered as its prediction. For continuous DV average of DV in the leaf node is considered as prediction.
*	Cost complexity pruning (Weakest link pruning), Tree Score = SSR + alpha * No. of leaf nodes. We will use tree score to prune the regression tree.
*	Imp Parameters and their meaning in sklearn Decision tree model
    * Max_depth: max depth of tree (Not that important)
    * Min_samples_split: min samples required to split a internal node(default = 2)
    * Min_samples_leaf: minimum no. of sample that should be in leaf node. (important for avoiding overfitting, generally 20 is used)
    * Min_impurity_decrease: Node is split if at least this much decrease in impurity there.
    * Ccp_alpha: cost complexity parameter
*	Main parameters are min_samples_leaf, ccp_alpha




## Random Forest Notes:
* Bootstraped data: We randomly select N samples from dataset with replacement. The sample size will be same as dataset size. So same rows maybe repeated in sample.
*	RF model steps:
    *	Select a bootstrapped data
    *	Using the bootstrapped create a decision tree but using random set of predictors(columns) to split each node.
    *	Repeat above two steps and create many trees.
    *	Pass a test data row through all trees and count the leaf node category the entry belonged to. Prediction for row is category with highest votes.
*	Bootstraping the data and using the aggregate to make decision is called Bagging. 
*	Out of Bag data (OOB) : data that is remaining from the dataset after bootstrapping. This can used as test data to evaluate the model.
*	Proportion of OOB sample that are incorrectly classified is called OOB error.
*	OOB error can be used to decide the no. of columns to considered randomly when splitting the data.
*	Parameters in RF model and their meaning:
    *	N_estimators: no. of trees
    *	Max_depth: max depth of tree (Not that important)
    *	Min_samples_split: min samples required to split an internal node (default = 2)
    *	Min_samples_leaf: minimum no. of sample that should be in leaf node. (important for avoiding overfitting, generally 20 is used)
    *	Min_impurity_decrease: Node is split if atleast this much decrease in impurity there.
    *	Ccp_alpha: cost complexity parameter
    *	Max_features: No. of features to be considered when making split. Generally, sqrt of # of features are considered.
    *	Oob_score: whether to return oob score or not.
•	Main parameters are min_samples_leaf, ccp_alpha, oob_score, max_features
•	Entropy can be used instead of Gini. Entropy = -sigma(p*(1-p)). Information gain is difference between entropy of parent and weighted average of children
