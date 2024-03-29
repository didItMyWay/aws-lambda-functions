# Deployment Notes

Uses Serverless framework for deployment and thus require a serverless.yaml conifguration.

## Deployment Steps
#### Install npm on your machine
`brew install npm`

#### Install serverless framework 
`npm -g install serverless`

#### Configure AWS CLI on your machine
https://docs.aws.amazon.com/cli/latest/userguide/getting-started-quickstart.html

#### Deploy Lambda Function
`serverless deploy`     

You can continue doing any changes to your code base and deploy again using `serverless deploy`. 
If any dependency is to be added, then follow below steps:
##### Install new dependency 
In your .venv install new dependency, suing pip/pip3:       
`pip3 install <<new library>>`
##### Update requirements.txt
Execute in your .venv:      
`pip freeze > requirements.txt`

##### Deploy Lambda again
`serverless deploy`

Head over to AWS console to see your Lambda function(s) deployed.

#### Destroy Lambda Function
Use Serverless to delete the Lambda function and all related resources.      
`serverless remove`


