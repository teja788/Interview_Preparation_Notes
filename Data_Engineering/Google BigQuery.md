## Notes on Google BigQuery

### Introduction
* BIGQUERY is a cloud data warehouse. It is serverless, scalable and cloud based. Can process petabytes of data fast.
* Can use it through google cloud console, python api etc
* Normal SQL langauage can be used
  * There are some differences in datatypes and aliases
  * Public datasets and local data from computer can be used
* Datasets can be queried and even visualized

### Notes
* Datasets can be saved in repeated format different from normalized and denormalized
* Some columns values can be given as arrays
* structs are different tyoe of datatypes and can have multiple datatypes and can have arrays
* They can be accessed using "." like column.var
* Partitioning in BigQuery is the process of dividing a large table into smaller, more manageable sections based on a specific column or set of columns.
  * Partitioning can be based on different columns
  * Physically stores in different sections
* Clustering is also diving data but sorts and groups but physicallly won't store in seperate sections


### Reference
* https://www.youtube.com/playlist?list=PL-oeM7CaGtVjVHzeA_RB04s7gjyrq53ZI
