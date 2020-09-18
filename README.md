# WooliesX weatherforecast app
## Pre requisites

Need to have below tools and cloud access to deploy the application
  - Azure Devops Access for CI/CD release pipeline
  - Docker Hub Access for image
  - Azure Cloud Subsciption for running APP service 
  - GitHub for source version control

## High Level Architecture

  <img width="460" height="300" src="/doc/images/AzureDeployTechChallenge.png">


## Steps to provision and deploy the solution

- Access [Github Repo](https://github.com/sathish86/wooliesxweatherforecast)
    - Make changes on develop or feature/** branch which will trigger the Azure devops pipeline DEV-WOOLIESX-WEATHERFORCAST to deploy infrastructure and application to Azure cloud in Dev environment.

    - Once changes are satisfactory then create PR from develop and rebase-merge to Master branch which will trigger the Azure devops pipeline PROD-WOOLIESX-WEATHERFORCAST to deploy infrastructure and application to Azure cloud in UAT and PROD environment.
  
- [Access Azure Devops Pipeline](https://dev.azure.com/WooliesX86/techchallenge/_build) which has both development and production deployment pipeline 

- [Docker Hub](https://hub.docker.com/r/dfranciswoolies/ciarecruitment-bestapiever) Image used for running application

- Azure Cloud Subsciption App Service
    - [Development environment App Service ](https://wooliesx-techchallenge-dev.azurewebsites.net/weatherforecast) to check weather forecast result from Developmetn Azure APP service

    - [UAT environment App Service ](https://wooliesx-techchallenge-uat.azurewebsites.net/weatherforecast) to check weather forecast result from UAT Azure APP service

    - [PROD environment App Service ](https://wooliesx-techchallenge-prod.azurewebsites.net/weatherforecast) to check weather forecast result from Production Azure APP service