# Pipeline [![CircleCI](https://circleci.com/gh/RoopanV/udagram/tree/main.svg?style=svg)](https://circleci.com/gh/RoopanV/udagram/tree/main)

CircleCI is used to create pipeline. It is listening on the main branch. Once any push made to main brach pipeline is triggered automatically. It is configured to build, lint, test, wait for approval and deploy the code.


## High level View of Pipeline
![Screenshot of pipeline overview](../screenshots/pipeline-architecture.png)

### AWS Config
All the required configuration for AWS are passed to the pipeline.
![Screenshot of env variable in pipeline](../screenshots/environment-variable-circleci.png)

### Stages Involved
1. Build Phase
1. Approval Phase
1. Deploy Phase

## Build Phase
1. Install the dependecies for both `udagram-api` and `udagram-frontend` applications.
1. Check for linting.
1. Builds both the application
1. Run unit test on `udagram-frontend`
1. Preserve the build files so it can be used in next stages.

![Screenshot of pipeline build phase](../screenshots/pipeline-build-stage.png)


## Approval Phase
Holds the pipeline until approved manually.
![Screenshot of pipeline approval](../screenshots/pipeline-approval-stage.png)

## Deploy Phase
Once approved deploy build files of `udagram-api` and `udagram-frontend` applications to `AWS Elastic Beanstack` and `AWS S3` respectively.  
![Screenshot of pipeline deploy](../screenshots/pipeline-deploy-stage.png)