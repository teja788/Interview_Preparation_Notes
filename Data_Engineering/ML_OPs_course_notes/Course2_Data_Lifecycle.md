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
