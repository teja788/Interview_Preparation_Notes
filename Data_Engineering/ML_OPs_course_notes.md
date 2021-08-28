# Course 1 - Introduction to Machine Learning in Production

## Introduction

* MLops deals with putting machine learnning models into production and tackling challenges that come with it.

### Challenges in Machine learning
* Input data distribution in production different from data used for modelling. This is called data drift.
* Beyond machine learning code which may be 5-10% there are many components for deploying a model to production

### ML project lifecycle
* Scoping
  * Define project
* Data
  * Define data and establish baseline
  * Label and organize data
* Modelling 
  * Select and train model
  * Perform error analysis
    * We may go back to data step to get more data or organize it differently based on performance
* Deployment
  * Deploy in production
  * Monitor & maintain system
    * New real time data can be sent back to data step and Model can also be retrained if needed
 
### Deployment

#### Key Challeanges
* Concept drift and data drift
 * changes in data can be sudden(due to some external change) or gradual.
 * data drift is when distribution of X(independent variables) itself changes.
 * Concept drift is when distribution of X remains same but relation between X and Y(Dependent var) changes.
 * 
 

