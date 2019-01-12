# hello-world-devops
Trivial app to explore workflow &amp; CI pipelining in different CI frameworks

[![Build Status](https://dev.azure.com/monch1962/monch1962/_apis/build/status/monch1962.hello-world-devops)](https://dev.azure.com/monch1962/monch1962/_build/latest?definitionId=1)

![Build Status](https://sonarcloud.io/api/project_badges/quality_gate?project=monch1962_hello-world-devops)
![Build Status](https://sonarcloud.io/api/project_badges/measure?project=monch1962_hello-world-devops&metric=coverage)
![Build Status](https://sonarcloud.io/api/project_badges/measure?project=monch1962_hello-world-devops&metric=bugs)
![Build Status](https://sonarcloud.io/api/project_badges/measure?project=monch1962_hello-world-devops&metric=code_smells)
![Build Status](https://sonarcloud.io/api/project_badges/measure?project=monch1962_hello-world-devops&metric=duplicated_lines_density)
![Build Status](https://sonarcloud.io/api/project_badges/measure?project=monch1962_hello-world-devops&metric=ncloc)
![Build Status](https://sonarcloud.io/api/project_badges/measure?project=monch1962_hello-world-devops&metric=sqale_rating)
![Build Status](https://sonarcloud.io/api/project_badges/measure?project=monch1962_hello-world-devops&metric=alert_status)
![Build Status](https://sonarcloud.io/api/project_badges/measure?project=monch1962_hello-world-devops&metric=reliability_rating)
![Build Status](https://sonarcloud.io/api/project_badges/measure?project=monch1962_hello-world-devops&metric=security_rating)
![Build Status](https://sonarcloud.io/api/project_badges/measure?project=monch1962_hello-world-devops&metric=sqale_index)
![Build Status](https://sonarcloud.io/api/project_badges/measure?project=monch1962_hello-world-devops&metric=vulnerabilities)

## Intention
This is a trivial NodeJS app, with a few unit tests, a few integration tests, a few PACTs and a few performance tests. It's also linked to https://sonarcloud.io for code quality checks. Intended use case is to discover and document how to build/test/deploy this app within different CI frameworks

## Manual app startup & test execution

### Starting the app
To start the app running in a CI-ready state

`$ NODE_ENV=test npm install && node helloworld.js`

#### Running unit tests

`$ npm run unittests`

#### Running UI tests

`$ npm run uitests`

#### Running integration tests

`$ npm run integrationtests`

#### Running API tests

Get a copy of wilee (https://github.com/monch1962/wilee) and build it locally using `$ make local`

Execute tests using

`$ APP=http://localhost:8080 TESTCASES=test/api/*.wilee.json ./wilee`

and analyse results

#### Running performance tests

`$ npm install -g artillery`

`$ artillery run test/performance/performance.yml`


#### Running sonarcloud tests

It's complicated... Refer to https://sonarcloud.io/ for detailed instructions on how to set it up (this complexity is the reason why CI is so nice to have, so I can get it to do the hack work for me!)

## Automated CI pipeline execution
The app is hooked into its own Azure DevOps pipeline, and will run through all build/test steps automatically whenever a pull request is made to this repo. Note the build status 'badge' earlier in this README file - it indicates whether the build/test steps passed last time the pipeline was executed.

Pipeline build & test config for this test is held in the file `azure-pipelines.yml`
