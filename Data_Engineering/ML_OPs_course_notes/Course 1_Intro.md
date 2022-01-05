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
* Software engineering issues
  * Checklist of questions while building a prediction system
    * Realtime or batch
    * Cloud vs edge/browser
    * compute resources (CPU/GPU/memory)
    * Latency, throughput(queries per second)
    * Logging
    * Security and privacy
 * Deployment will have different practices from maintanence. First deployment is only half work done. 
 
#### Common deployment cases
* New product/capacbility
* Automate/assist manual task
 * Shadow mode, run along with Human
* Replace previous ML system

##### Key ideas in deployment
* Gradual ramp up with monitoring
* Rollback

##### Deployment patterns
* Shadow deployment - deploy along with human or previous algorthim
* Canary deployment - Rollup to a small fraction monitor and ramp up gradually
* Blue/Green deployment - you have old/blue software or model running and new/green model running simaltaneously and system can switch sending data to them easily between two systems. Partial switching can also happen.

##### Degrees of Automation
* Human Only ---> Shadow mode ----> AI assitance ----> Partial Automation ----> Full Automation
* There is human in loop in AI assistance and Partial automation. This is commonly done in industries and Manufacturing.
* Full Automation has no human. It is used in consumer internet applications like web searches, recommendations etc
* Deployments start with human only and proceed to one of next steps

#### Monitoring
* Monitoring dashboards can be used to monitor various metrics
  * these can be based on what can posiibly go wrong
  * Statistics/metric that detect the problem
* Examples of metrics
  * Software
    * Memory, compute, latency, throughput, server load
  * Input
    * Input dataset related metrics, Missing value %
  * Output
    * Output related metrics, null output, click through rate
* think of deployment as iterative system with Deployment/Monitoring --> Traffic --> Performance analysis
* Common practice while monitoring is it set threshold for Alarms and Adapt/Change metrics over time
* There are two types of retraing - Manual and Automatic - Manual is used in most cases as of now
* User data generally has slow dift
* Enterprise(B2B) data changes fast

### Modelling
* AI System = Code(Model\Algo) + Data
* Model development is a highly iterative process with data --> Model Training --> Error analysis ---Hyper parameter tuning etc

#### Challenges in model development
* Doing well on training data
* doing well on dev/test data
* doing well business metrics/ project goals
* Perfomance on disproprtainately important examples
* performane on key slices of data
* Rare cases - skewed data distribution, Accuracy in rare cases

##### Ways to establish baseline for our solution
* Human level performance(HLP) - good for unstructred data
* Literature search for state of art/ open source
* Quick and dirty implementation
* Performance of older system

##### Error analysis
* by making spreadsheet of error % in categories, overall, human level performance. We can make a informed decision how to reduce it.
* we can collect more data of specific category, improve data quality, labeling accuracy, use data augmentation
* It is better to check performance on various slices of data before taking model to production

##### Skewed datasets
* Precision and recall are better measure than accuracy for measuring model performance on highly skewed data
* F1 score can be used for comparing model . F1 score is harmonic mean of precision and recall F1 = 2/((1/P)+(1/R))

##### Data Iteration
* Data centric AI development is becoming more important than model centric development. Improving data quality, getting more data rather than improving model on fixed dataset.
* Data Augmentation: create relastic examples that algorthim does poorly on. but humans do well on
* like model iteration loop we can have data iteration loop also
* If model is large and mapping x->y is clear. Adding more data hurts accuracy
* There is a shift from using colabarative filtering to content based filtering in product recommendations over last few years
* For structred data adding hand desgined features still adds value
* having a good expirement tracking helps in decision making on hyperparametrs, model etc
* things to track in experimetns:
  * Algorthim/ Code version
  * Dataset used
  * Hyperparameters
  * Results & Metrics

##### Define data and establish baseline
* Data definition questions
 * What is x? what input features to include
 * What is y? how can we be sure targets were labelled correctly
 * If you have small dataset having clean labels is critical
 * emphasis should be on data process like how it is collected etc. if the dateset is big

