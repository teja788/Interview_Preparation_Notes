### Data Life Cycle

Collect ---> Analyze ---> Clean ---> Organize ---> Transform ---> Insight

* Raw data is split into chunks distributed across clusters and data transformations are done on it

* Spark is a unified programming language ot can be used to process any kind of data and transform it. 

* It can also be used to store the processed data in any cloud or other storage systems.

* Spark can help run on multiple systems Baremetal(Physical), Cloud Managed Services, Cloud kubernetes services

* SparkMl and SparkGraphX can be used to further analyze data. Spark has support for multiple languages.

### Spark Architecture
Code ---> Spark Context (Driver Program) ---> Cluster Manager (Yarn or Mesos or Kubernetos or Standalone)  ---> Worker Nodes (Executors)

* Databricks has community edition where you can create a free account and use spark
