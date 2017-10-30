# Introduction 
*Norfolk Cache* is a simple key-value storage application designed for Azure Mentoring program.

# Getting Started
The project structure:
- [NorfolkCache](NorfolkCache) - an ASP.NET MVC application that runs on .NET Framework version 4.6.1.
- [ApiTests](ApiTests) - a set of API tests that are built using chakram/mocha.
- [LoadTests](LoadTests) - a set of load tests and initial data. 

Branches:
- *development* - an unstable development branch.
- *master* - a stable production-ready branch.
- *release* - a stable release branch.

Workflow:
- Developers work on a feature using it's own feature branch. When the feature is completed a responsible developer merges the feature branch to *development* branch.
- All features that are deployed and verified on CI environment are merged to master branch using a special schedule.
- All features that are deployed to CI environment are merged to the release branch according to a release schedule.  

Fork this repository to create your own copy that you will use in this program. 

Running API tests
```sh
cd ApiTests
npm install
rem Set hosname
notepad test\tests.js
npm tests
```

# Build and Test
Open ASP.NET MVC solution file [NorfolkCache](NorfolkCache\NorfolkCache.sln) with Visual Studio 2015 or Visual Studion 2017.

# 1. Practical Task "Web Apps"
The goal of this task is to create a set of App Services for three different environments:
- *my-norfolk-cache-ci* - a unstable CI environment with the latest version of **development** branch.
- *my-norfolk-cache-uat* - a stable UAT environment with the latest version of **master** branch.
- *my-norfolk-cache* - a stable production environment with the latest version of **release** branch.

Please, use your own prefix name instead of *my* to avoid name conflicts.

## Solution 1
1. Create a new resource group *my-norfolk-cache*. (Learn more about (Azure Resource Manager)[https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-overview].)
2. Create a new *my-norfolk-cache-ci* web app in *my-norfolk-cache* resource group with new app service plan *my-norfolk-cache-ci-plan* (free pricing tier, any location).
3. Create a new *my-norfolk-cache-uat* web app in *my-norfolk-cache* resource group with new app service plan *my-norfolk-cache-uat-plan* (free pricing tier, any location).
4. Create a new *my-norfolk-cache* web app in *my-norfolk-cache* resource group with new app service plan *my-norfolk-cache-plan* (free pricing tier, any location).
5. Setup for deployment for *my-norfolk-cache-ci* web app:
	* Open "Deployment slots" tab and learn information on this page.
	* Open "Deployment options" tab and setup github deployment for development branch.
	* Learn about "Quotas" for this web app. (["Monitor Apps"](https://docs.microsoft.com/en-us/azure/app-service/web-sites-monitor).)
	* Open "Overview" tab and open a web app url - http://my-norfolk-cache-ci.azurewebsites.net.
	* Run API tests for this host.
	* Open "Diagnostics logs" and enable filesystem application logging (Information level), web server logging, and detailed error messages. ([Learn about troubleshooting a web app in Azure](https://docs.microsoft.com/en-us/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio).)
	* Open "Log stream" go to "Application logs" and run API tests.
	* Open "Log stream", go to "Web server logs" and run API tests. (["Enable diagnostics logging""](https://docs.microsoft.com/en-us/azure/app-service/web-sites-enable-diagnostic-log).)

Questions:

1. What is a resource group location?
2. What plan do you need to have deployment slots for your web app?