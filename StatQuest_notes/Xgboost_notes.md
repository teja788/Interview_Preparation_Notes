## Xgboost regression notes:
*	Xgboost stands for extreme gradient boosting. It is designed to be used with large, complicated datasets.
*	Make a unique prediction. It is 0.5 regardless we are doing regression or classification.
*	Each Xgboost regression tree creation steps:
    * A unique tree called xgboost tree is fit on residuals. Xgboost tree starts with a leaf containing all the residuals. Similarity or Quality score is calculated
    *	Similarity Score = (Sum of residuals squared)/(No. of residuals + lambda)
    *	After dividing the data to two nodes. Similarity score for each node is calculated. Gain = Left Similarity + Right similarity – root similarity
    *	Gain for various predictors is calculated and one with highest gain is considered for division.
    *	This division is repeated and tree is made. Then gamma value is used to prune the true. 
    *	We start at the lowest branch and if gain is less than gamma we will remove the branch. If a branch is removed we will compare gamma with gain for above branch and then prune it. If at any point gain is greater than gamma we will stop pruning.
    *	Lambda in similarity score is regularization parameter. It is used to decrease the sensitivity of prediction to individual observation. When lambda>0 it is easier to prune the trees as values of gain are smaller.
    *	Setting gamma to zero doesn’t turn off pruning as gain can be negative.
    *	Output value = (sum of residual)/(no. of residuals + lambda) 
*	New prediction = Initial_leaf_vaue + eta * out_put_value of xgboost tree. Eta is nothing but learning rate.
*	Using the new predictions, new residuals can be found and new xgboost tree is built on the residuals. This process is repeated until residual are small or we reach given no. of trees.

## Xgboost Classification:
*	We will start with leaf which makes a unique prediction of 0.5 probability for all data.
*	We will calculate the residuals for all data
*	Each Xgboost classification tree creation steps:
    *	We start with leaf containing all residuals
    *	Similarity score = (sum of residuals squared)/(sigma(prev_prob*(1-prev_prob)) + lambda)
    *	We calculate the similarity score for all node divisions based on predictors and calculate the gain value for each node division.
    *	We consider the predictor with best gain for division
    *	Minimum No. of residuals in each leaf is determined by something called cover. Cover is denominator – alpha of similarity score.
    *	If cover value is lower than the default or selected cover value. Further division of nodes stops.
    *	Cover is also called min_child_weight
    *	Gamma, alpha are used to prune the tree as in classification.
    *	Output_value = (sum of residuals)/ (sigma(prev_prob*(1-prev_prob)) + lambda)
*	New predictions = log(odds) of initial leaf + eta * output_value
*	New predictions will be log odds values we can convert them to probabilities and calculate new residuals.
*	Based on new residuals another xgboost tree is made. This process carries on until we made certain no. of trees or residuals doesn’t decrease by significant amount

## Xgboost algorthim notes:
*	Above given procedures are specific cases which we get when we take loss function of regression as ½ * (actual – predicted )^2 and classification as -sigma(y * log(p) + (1-y) * log(1-p))	                              
*	We minimize the above loss function while building trees. O_value is output value. Lambda is regularization term similar to ridge regression.
*	Xgboost uses a approximate greedy algorithm. Greedy algorthim means it makes decisions without looking ahead to see if this is the absolute best choice in long term. So it builds tree relatively quickly.
*	When dividing a continuous variable instead of checking threshold between every point data is divided into quantiles and quantiles are checked to get the best threshold for division. This speeds up the algorithm a lot. We use about 33 quantiles in general.
*	Xgboost uses sketch algorithms to speed up the threshold detection. Data is divided into small parts they can be processed in parallel and quantile sketch algorithm combines results gets an approximate histogram and calculates approximate quantiles from it.
*	Approximate quantiles can be used as thresholds. This speeds up the algorithm a lot.
*	Second derivate of loss function is called Hessian. It is also cover.
*	We use weighted quantiles in xgboost. Each weighted quantile will have same sum of weights. Weights are obtained from cover or hessian.
*	Xgboost only uses weighted quantiles, parallel learning and approximate greedy algorthim only when dataset is huge.
*	Sparsity aware split finding: when a predictor has missing values: this is a inbuilt way of dealing with missing values. We separate the missing data and place it left node, right node and calculate gain for all thresholds and take the best one.
*	Cache aware access: xgboost uses cache memory which is very fast compared to regular memory to calculate gradients and hessians. 
*	Blocks for out of core computation:  xgboost compresses data when it is very big. So that reading from hard drive is fast. It also uses sharding to read from multiple hard drives.
*	Xgboost can also build by looking at random subset of data and random features of data while deciding to split the data to speed up the computation.



## sklearn xgboost parameters:
*	Sklearn has a wrapper around xgboost 
*	n_estimators: no. of trees or boostings. Shrinks the weightage after each step (0-1)
*	max_depth: max tree depth for each learner, generally 3-6 taken, bigger tree will be more complex may overfit and use more memory (0- infinity)
*	learning_rate: also called eta. Default is 0.3
*	objective: Loss function
*	n_jobs: no. of parallel threads
*	gamma: minimum loss reduction required to further divide leaf node
*	min_child_weight: minimum sum of instance weight(hessian) needed in a child. Larger min_child_weight leads to a more conservative algorthim.
*	max_delta_step: maximum delta for each tree’s weight estimation. It caps the weight of step. It is helpful in imbalanced data. Usually not needed.
*	subsample, colsample_bylevel, colsample_bytree, colsample_bynode : subsample ratio, columns sample ratio for tree, level, split
*	reg_alpha, reg_lambda: L1 reg(lasso), L2 reg(ridge)
*	scale_pos_weights: balancing of positive, negative weights. Used for imbalanced data.
*	base_score: initial leaf score
*	n_estimators, max_depth, learning_rate, gamma, L1, L2 maybe important parameters
*  GridsearchCV and RadomSearchCV of sklearn are good ways for parameter tuning.
*  scale_pos_weight is a important metric to tweek in case of imbalanced data.
*  subsample and cosample_by_tree can be given smaller values to speedup parameter search.

## other convinent parameters in fit function
* early_stopping_rounds: will specify no. of trees to make without improvement before stopping.
* eval_metric - evaluation metric to be displayed
* eval_test - we can give the dev set for evaluation here
* verbose - should be set to true to display the metrics
