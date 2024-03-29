# Simple Application with User Signup and Signin features

This is a AWS Lambda application with 2 functions: user sign-up and user sign-in. Written in Python using Flask framework. 
- Uses AWS API Gateway as proxy integration to AWS Lambda.
- Uses AWS SecretsManager to store application credentails.
- Uses a PSQL Database to persist user information.

#### Project Structure
Designed to follow Clean Architecture principles and Domain Driven design concepts.

1. The entry point into this service is at **src/integration/user_controller.py**
2. Necessary Lambda functions for user login and register can be found in here.
3. Every Lambda functions entry point is pre-defined:
```
def lambda_handler(event, context):
   # add your code here. 
   # The name lambda_handler can be changed to what suits your requirement.
```
4. controller interacts with your service:  **src/application/user_service.py** . 
5. service interacts with your repository to talk to database: **src/domain/model/user_repository.py**
6. the actual implementation of database queries under persistence layer: **src/persistence/user_repository_impl.py**
7. at the end, response is delivered from the controller. Response should be in json format.
```
result = {

	'statusCode': <HTTP status code>,
	'body': json.dumps({'message': <your message>})
}
return result
```

### Unit and Integration Test
Designed following Test First Development approach:
- All Test located under test directory: **test/***

### Access to Database 
Uses Postgress as Relation Database tech. Follow the steps for access via CLI.
1. Install psql on your machine: `brew install libpq`
2. Connect to DB: `psql -h hostname -U <username> -d <password>`
3. When prompted for password, add the password.
4. Once you are connected, you can list tables(`/dt`)  and other PSQL commands.

### Deploying Lambda to AWS
 Follow the DeploymentNotes.md.

