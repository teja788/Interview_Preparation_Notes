## Introduction

* In prodcution ML, model is only 5% of the work
* Production machine learning = Machine learning development + Modern Software development
* Prduction Machine learning system
  * Scoping - Define Project
  * Data
    * define data and establish baseline
    * label and orgaznize
  * Modelling
    * select and train model
    * perform error analysis
  * Deployment
    * Deploy in production
    * Monitor and Maintain
* Challenges in production ML
  * Build integrated ML system
  * continuosly operate in production
  * handle continuosly changing data
  * optimize compute resource costs

## ML Pipelines
* there are infrastructre for automating, monitoring and maintaining model training and deployment
* Directed acycilc graphs are directed graphs with no cycles
* ML pipeline workflows are usually DAGS
* DAGS define sequence of tasks to be performed and their relationships and dependencies
* Pipeline orchestration frameworks are responsible for various components in an ML pipeline DAG dependencies. They help with pipeline automation
  * ex: Airflow, Argo, Celery, Luigi, Kuberflow
* Tensorflow extended is open source end to end platform for deploying production ML pipelines. It can handle huge data and is scalable

## Collecting data
* Data pipeline consists of data collection, ingestion, preparation
* Above steps has to be done as automated tasks and data collection has to be monitored as for most applications, data is not collected once but throughout the lifetime
* Broken data is common cause of problems in production ML
* key things to consider while collecting data
  * What kind and how much data needed
  * How od=ften new data comes in
  * is it labelled and how expensive to label it
  * How to translate user needs to data needs
* Dataset issues:
  * inconsistent formatting
  * compounding errors if the data comes from other models
  * monitor data sources for system issues and outages
* while collecting data we have to take care of security, privacy and fairness. We also should have labelling system which doesn't have bias
* people who label are called raters
* types of raters - Generalists, Subject matter experts (medical images), users (app user ratings etc)
* Two types of labelling - process feedback and human labelling
* Process feedback is automatically we get labels from user feedbak, ratings on app or some other process

### Validating data

* Data Issues
  * Drift and Skew
     * Data and concept drift
     * Schema skew
     * Distribution skew
* Drift: Changes in data over time 
* Skew: difference in two version like training and serving(predicting realtime or later)
* Data Drift : Data(x) changed due to some real world change
* Concept Drift: Labels(y) statistical properties changed
* Schema Skew: when training and serving doesnt have same schema
* Distribution schew is when data distribution changes (it may be covariate or concept shift)
* Dataset shift: when both distribution of both x,y change from training to serving
* covariance shift: when distribution of x changes but relation between x and y remains same
* concept shift: when relation between x and y change but distribution of x remains same across training and serving
* Skew detection workflow contains computing baseline stats, schema  of training and serving and comparing them
* we validate statistics, detect anamolies between them and alert
* TFDV (tensorflow data validation) is used to understand, monitor and validate data. can work on petabytes scale
* TFDV gives charts in browser and helps in detecting various skews
* It can dtect schema skew, feature skew and distribution skew
