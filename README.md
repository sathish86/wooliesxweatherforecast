# WooliesX weatherforecast app
## Pre requisites

Need to have below tools and cloud access to deploy the application
  - Azure Devops Access for CI/CD release pipeline
  - Docker Hub Access for image
  - Azure Cloud Subsciption for running APP service 
  - GitHub for source version control

## High Level Architecture

  <img width="460" height="300" src="/doc/images/tech_challenge_arch.png">

## Solution Design

To achieve deployment of weather forecast solution deployment, we used below design, cloud and tools.

  - GitHub for source version control and followed below git workflow
    - Make changes on develop or feature/** branch which will trigger the Azure devops pipeline DEV-WOOLIESX-WEATHERFORCAST to deploy infrastructure and application to Azure cloud in Dev environment.

    - Once changes are satisfactory then create PR from develop and rebase-merge to Master branch which will trigger the Azure devops pipeline PROD-WOOLIESX-WEATHERFORCAST to deploy infrastructure and application to Azure cloud in UAT and PROD environment.

  - Used pipeline as a code
    - Pipeline as code file `azure-pipelines_dev.yaml` used to release application in DEVELOPMENT environment
    - Pipeline as code file `azure-pipelines_prod.yaml` used to release application in UAT and PRODUCTION environment stage by stage

  - Used infrastructure as a code using Azure ARM template
    - IAAC file `azuredeploy.json` contains the resource deployment of Azure APP service which pull the image from docker hub and run the application as a container.

  - APIKeySecret security
    - To keep the secret variable we used Azure Devops tool Library variable group. In the pipeline file it passes the value as parameter to ARM template, when it deploys the resource it sets the environment variable in APP service and eventually used by container. 
    - `NOTE:` I would prefer to keep the secret in Azure Key Vault and refer it in ARM template.

  - Azure Devops used for CI/CD release pipeline
    - Pipeline has service connection configuration to github, docker hub and Azure cloud to orchestrate deployment process.

  - Used Azure Cloud Subsciption to run weather forecast applicatoin using Azure APP services

## Weather ForeCast Endpoints
- [Development environment App Service ](https://wooliesx-techchallenge-dev.azurewebsites.net/weatherforecast) to check weather forecast result from Developmetn Azure APP service

- [UAT environment App Service ](https://wooliesx-techchallenge-uat.azurewebsites.net/weatherforecast) to check weather forecast result from UAT Azure APP service

- [PROD environment App Service ](https://wooliesx-techchallenge-prod.azurewebsites.net/weatherforecast) to check weather forecast result from Production Azure APP service

## Links to access release piplines and other tools 
- [Access Azure Devops Pipeline](https://dev.azure.com/WooliesX86/techchallenge/_build) which has both development and production deployment pipeline 

- [Docker Hub](https://hub.docker.com/r/dfranciswoolies/ciarecruitment-bestapiever) Image used for running application

- Access [Github Repo](https://github.com/sathish86/wooliesxweatherforecast)
  

    