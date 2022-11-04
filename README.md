
# hello-world-python-application

In this repository you will find a Hello World coded in Python that will be deployed to [AWS Lambda](https://aws.amazon.com/pt/lambda) using the [Serverless Framework](https://www.serverless.com).
[Github Actions](https://github.com/features/actions) has been configured as CI/CD.

## Gitflow

- `feature` > `develop` > `main`

In the `feature` branch we run CI workflow (Lint and Unit tests). In the `develop` branch we deploy to AWS Lambda using development configuration and in `main` we deploy to AWS Lambda using production configurations.

## Deploying in your AWS Account

In this project we are using the simplest form of communication with AWS: `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`.
This information **MUST BE** turned into secrets within your repository.

Here some basic steps to obtain this data:

- Create a new IAM Police based on this article: <https://serverlessfirst.com/create-iam-deployer-roles-serverless-app/>
- Create a new group of user inside AWS IAM and attach the IAM Policy created to it (<https://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups_create.html>)
- Create a new user only for Serverless framework deployment and add to the group created (<https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html#id_users_create_console>)
- Create an access key for this new user to get the `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`. (<https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html#Using_CreateAccessKey>)
- Transform this credentials in two repository secrets (<https://github.com/Azure/actions-workflow-samples/blob/master/assets/create-secrets-for-GitHub-workflows.md>).

## Run Serverless framework locally

- Install NodeJs and NPM: <https://docs.npmjs.com/downloading-and-installing-node-js-and-npm>
- Install NPM project dependencies:
  - npm install
- Install Serverless packages:
  - npm install -g serverless
  - npm install -g serverless-offline

After that, run this command to spin up a local environment:

- serverless offline --config serverless_dev.yml

### TODOS

- Create an API Gateway using Serverless Framework
- Create a DynamoDB table using Serverless Framework
- Change the Python code to read a text on DynamoDB table and return it on a AWS Lambda request
- Configure GET method on API Gateway that will call the AWS Lambda to respond it
- Fix the automatic PR creation
