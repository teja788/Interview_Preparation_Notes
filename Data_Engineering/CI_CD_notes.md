## Introduction

* CI-CD - Continuos integration and Continuos deployment
* Continuos integration, Delivery and deployment collectively known as CI-CD
* It involves building, testing, deployment at every small iteration

## Various approches
* Continuos Integration 
  * All developers have a local copy of code and push there every incremental change to a common remote repository. It may be done every many days or many times in a day.
  * Every tinme a change is made to code in remote repo whole application or code is run and tested automatically to pass tests, guidelines and complainces.
  * This decreases chances of errors
* Continuos Delivery 
  * Along with above steps code is also deployed but only manually. This requires human intervention.
* Continuos deployment 
  * Same as above except deployment is done automatically. No human intervention required
  * Increases the speed of operation

### Pipelines
* Pipeline automatates the code build, test, deployment, staging production environment
* Steps in Pipeline:
  * Commit : New code writing and integaration
  * Build : code converted to executable form
  * Test
    * Two type of testing present. Aplha deployment and Beta deployment
    * Alpha deployment checks the integration between various builds
    * Beta deployment checks whether App is working
  * Deploy - Deploys to Production environment
* Above all can be automated using Gitlab or Jenkins

### Gitlab CI/CD
* Can automate whole CI-CD process without any outside application help
* Things needed for CI-CD in Gitlab
  * codebase on git
  * Sequentially defined scripts in YAML file
  * YAML file in root path with extension .gitlab-ci.yml
* YAML file has steps, whether to run them in parllel or in sequence and where to deploy the app. Specify whether to run them automatically or manually
* Steps in YAML file are similar to sequence of commands run in your terminal
* In summary YAMl file contains
  * Structre of pipeline
  * Steps to execute
  * What to do when certain conditions are satisfied
* Pipeline state and what is happening is shown by Gitlab



## References
* https://www.youtube.com/watch?v=HSV-Kky9N5E - Edureka

