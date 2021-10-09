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
