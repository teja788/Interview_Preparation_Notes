## Scaling Continous Features

* If we have features whose units and ranges are different. Model may give more importance to one over other.  
* So we can scale them using various techniques to bring them to same range so that make model can give same importance.
* Scaling should be done where some kind of distance metric is used
* Types of scaling:
  * **Min - Max** (Normalization) - brings the values to range 0-1 
    * formuale: (x_value - x_min)/(x_max - x_min)
  * **Standard scaling** (Z - values) - calculates z values using mean and standard deviation.
    * formulae: (x_value - x_mean)/(x_standard_dev)
  * **MaxAbsScaler** - divides by maximum absoulte value. brings the range to -1 to +1 
  * **RobustScaler** - scales the column to InterQuartile range. 
    * formulae: (x_value - x_quartile_1)/(x_quartile_3 - x_quartile_1)

## Other Continous feature transformations

* **log transform**: It is used to convert the skwed distribution to normal or less skwed distribution
  * By taking log of values we can decrease the range of values and effect of outliers
* **Box-Cox** transform - it transforms the non - normal to normal distribution. It has parameter lambda which can be adjusted.
* power transform Scaler - provided by sklearn automatically selects the lambda value.
* 
