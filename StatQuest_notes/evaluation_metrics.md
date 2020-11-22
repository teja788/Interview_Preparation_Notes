# Evaluation metrics

## Classification
* **True Positives** - 1's predicted correctly
* **True Negatives** - 0's predicted correctly
* **False Positives** - 0's predicted as 1
* **False Negatives** - 1's predicted as 0
* **Confusion matrix** - matrix between actual and predicted vales containing all above measures
* **Sensitivity** - percentage of 1's that are correctly identified,**Sensitivity = TP/(TP+FN)**
* **Specificity** - percentage of 0's that are correctly identified,**Specificity = TN/(TN+FP)**
* **Recall** - same as Sensitivity or **TP/(TP+FN)**
* **Precision** - among the predicted 1's how many are correctly predicted **TP/(TP+FP)** .It is used when cost of false positive is high, non spam mail classified as spam
* **F1-Sccore** - 2 * (Precision * Recall)/(precision + recall) - when we need a balanced model.
* **Accuracy** - percentage of tp's ans tn's on whole data **(TP+FN)/(TP+TN+FP+FN)**

* **ROC** - Reciever Operator Characterstic is a chart which provides way to summarize all confusion matrices. It helps deciding best threshold value.
    * **Sensitivity or TP rate (y- axis) and (1 - specificity) or FP rate** are calculated at various threshold values and plotted which gives ROC curve.
* **AUC** - Area under the curve is area under ROC curve. It is used to compare various models.
* FPR can be replaced by precision some times in ROC curve.

## Regression
* **RMSE** - Root Mean Square error - **srqt((x_actual - x_pred)^2)/N)** . Used in regression to compare error between models
* **MAE** - Mean Absolute error
* **MAPE** - Mean absolute percentage error
* **R-Squared** -
