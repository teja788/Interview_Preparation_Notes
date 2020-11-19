## Notes - CrossValidation
* CrossValidation lets us compare different machine learning methods to give us a sense which will work best in practice.
* K fold cross-validation: Divide data into k blocks randomly, use k-1 blocks to train the model and 1 block to test the model. This is repeated with every block as test and evaluations metrics are averaged
 
## Notes  - Linear Regression
* Fit best line given data
* Sum of squared residuals – sum of square of difference between actual and predicted Y. Best fit line will have least SSR
* Y = ax+b is equation of line. We have to find optimal values of a,b to minimize the SSR. We do this by taking derivative of SSR and finding where it is zero
* Final line minimizes sum of squares and it gives least squares between it and real data.

## Notes – Logistic Regression
*	Odds – Chances something will happen . Odds are 6/4 means out of 10 one event will happen 6 times and other will happen 4 times. Odds are ratio of something happening to something not happening.
*	Probability is ratio of something happening to no all events.
*	Odds = (Prob of event happening)/(Prob of event not happening), odds = (p/(1-p))
*	Taking log of odds ratio makes odds for event and against event symmetrical.
*	We can calculate log of odds through counts or probabilities. When we calculate using probabilities we call it logit function. Log(p/(1-p)) is called logit function. It forms basis for logistic regression.
*	Odds ratio is different from odds
*	For events A and B Odds ratio = (odds of A given B happened/odds of A given B didn’t happen). We take log to make it symmetrical.
*	So Odds ratio is a indicator of relationship between A and B. If odds ratio is high it means B is a good predictor of A and smaller values means vice versa.
*	One of Fisher’s exact test, Chi square test, Wald test can be used to calculate significance of odds ratio. Wald’s test is used to calculate confidence intervals
*	Logistic regression fits a S shaped logistic function to data.
*	Maximum Likelihood is used to select best fit curve in logistic regression
*	Logistic regression are a type of Generalized linear models.
*	Probabilities on Y axis are transformed using logit function – log(p/(1-p)). After transforming probability of 0-1 is transformed to -ve infinity to +ve infinity.
*	line is fit through predictors and log of odds of Y
*	We cant use the sum of squared residuals for logistic regression as residuals for a best fit line will become infinity.
*	We project the original data on a candidate line. This gives each sample a candidate log odds value. 
*	We transform the log odds value to probability using exp(log(odds))/(1+exp(log(odds))).
*	We now calculate the likelihood of data which is product of likelihood (in this probabilities of each point) . (p1 * p2 * p3 *(1-p4)*(1-p5)…….
*	Log of likelihood is generally preferred – log(p1) + log(p2) + log(1-p3) +log(1-p4)……..
*	We rotate the line multiple times and calculate log likelihood again. We will select the line which has maximum likelihood. Expectation maximization algorithm or some other algorithm is used to get the best fit line.
*	McFadden Pseudo R square can be used to understand the fit of regression. We will use log likelihood instead of sum of squared residuals for calculating R square.
*	Iterative weighted squares can be used for calculating the line which gives maximum likelihood.

## Notes – Regularization
*	In normal regression sum of squared residuals is minimized whereas in ridge regression SSR + lambda * slope^2 is minimized.
*	Ridge regression tries to decrease the influence of each predictors on independent variable. If lambda increases slope or coefficient decreases.
*	In logistic ridge regression we use Maximum_Likelihood + lambda * slope^2 for finding best fit curve.
*	For a model with coefficient C1,C2…  SSR+ lambda * (C1^2+C2^2+….) is used.
*	When sample sizes are small ridge regression can help reduce variance. If parameters are larger number than data points. Ridge regression can be used to get a good model.
*	Lambda can be determined using k fold cross validation.
*	In lasso regression SSR + lambda * abs(slope) is used to fit data.
*	Main difference between ridge and lasso regression is lasso can make coefficients zero, whereas ridge makes coefficients closer to zero but not zero.
*	Lasso regression is useful when there are lot of useless variables in the model as it excludes variables. Ridge regression does well when model has lot of useful variables
*	L2 norm is ridge, L1 norm is lasso. Elastic net adds both L2 norm and L1norm to SSR.
*	Ridge regression - SSR + lambda1 *(C1^2 + C2^2…)
*	Lasso regression - SSR+lambda2 * (abs(C1)+abs(C2)+…..)  
*	SSR + lambda1 *(C1^2 + C2^2…)+lambda2 * (abs(C1)+abs(C2)+…..)  – elastic net
*	Elastic net regression is good when dealing with model having corelated parameters.
