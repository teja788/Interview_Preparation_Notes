## Adaboost:
*	In adaboost we have just node and two leaves (stumps). We create forest of stumps. Stumps are weak learners
*	In adaboost some stumps get more say(weightage) in the final classification than others.
*	Order in which stumps are made is important. Errors of first stump influences second one and so on.
*	Sample weights are taken initially the same. Sample weights of incorrectly classified samples are used to calculate “Total error” and “amount of say”.
*	Total_Error = sum of incorrectly classified sample weights
*	Amount of say = ½ * log((1-Total_Error)/Total_Error)
*	Now weights are updated. For incorrectly classified samples: New_weight = old_weight * exp(amount_of_say). For incorrectly classified sample 
* New_weight = old_weight * exp(-amount_of_say)
*	New sample weights are normalized so that they add up to one.
*	We can use these modified sample weights to make the next stump.
*	When predicting amount of say of each category is added and prediction will be the highest amount of say.

## Gradient boost trees(regression):
*	Gradient boost starts by making single leaf. This leaf represents initial guess for the DV. For regression first guess is average value. Pseudo Residual(observed - predicted) of dataset are calculated based on leaf value.
*	Next a tree of fixed size(8 to 32) is made on the pseudo residuals. We set a learning rate. New_prediction = leaf + learning_rate * prediction_of_residual. We use this  
* New prediction to calculate new pseudo residuals.
*	This process is repeated until we make a given number of trees or there is no significant improvement anymore.
*	After the construction of trees to prediction = Initial_leaf_value + learning_rate * tree_1_residual_prediction+ lr * tree_1_residual_prediction+…………….
*	Residual get smaller with each tree.
*	Above algo is most used Gradient boost procedure with loss function as ½*(observed- predicted)^2 of Original gradient boosting algorthim.
*	General gradient boosting algo found statquest video.



## Gradient boost classification:
*	We start with initial leaf the prediction of initial leaf is log(odds). It’s equivalent to average for continuous data.
*	We convert log(odds) to probability which is exp(log(odds))/(1+exp(log(odds)))
*	We calculate the pseudo residual (observed value– predicted probability)
*	Now we build a fixed tree using pseudo residuals
*	Output value of leaf = sigma(residual predicted)/sigma(prev_prob*(1- prev_prob)
*	New prediction = orig_leaf_value + lr * output_value (this gives new log(odds)). We can calculate probability and new pseudo residuals.
*	We keep repeating above until we have made the specified trees or residual does not increase significantly.
*	Final Prediction =  Initial_leaf_value + lr * tree_1_output + lr * tree_2_output…..
*	Above gives log odds we have to convert it to probability to get final prediction.
*	Algo above is specific case of general gradient boost algo where loss function is  - sigma(y*log(p)+(1-y)*log(1-p))

*	Parameters of sklearn gradient boost:
    *	Learning rate:  rate at which each tree contribution shrinks
    *	n_estimators: No. of trees to be made
    *	subsample: Fraction of samples to be used for each individual learner. Default is zero.
    *	Min_samples_split:  minimum no. of samples required for splitting internal node.
    *	Min_samples_leaf: minimum no. of samples required to be in leaf node.
    *	Max_depth: max depth of individual estimators. It limits no. of nodes. It has to be tuned to get best model.
    *	Min_impurity_decrease: Minimum impurity decrease required for node to be split.
    *	Max_leaf_nodes: Maximum no. of leaf nodes
    *	n_iter_no_change: if set to a number, early stopping will be used to terminate training when validation score is not improving.
    *	validation_fraction: proportion of data set aside for early stoping
    *	ccp_alpha: cost complexity parameter
*	learning_rate, n_estimators, Min_samples_leaf, Max_leaf_nodes maybe important parameters.
