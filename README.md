Deployment Instructions for Bottest AI Application
This document provides instructions for deploying the Bottest AI application in both production (PROD) and development (DEV) environments using AWS S3 and AWS CloudFormation.

Table of Contents
Syncing Files to S3
CloudFormation Stack Operations
Create Stack
Update Stack
Delete Stack
Environment Specific Instructions
Production (PROD)
Development (DEV)
Syncing Files to S3
Before deploying the CloudFormation stack, ensure the necessary files are synced to the appropriate S3 bucket.

Production
sh
Copy code
aws s3 sync . s3://bottest-ai-app-prod-us-east-1-122253718099/ --exclude ".git/*" --exclude "LICENSE" --exclude "README.md"
Development
sh
Copy code
aws s3 sync . s3://bottest-ai-app-dev-us-east-1-533267082328/ --exclude ".git/*" --exclude "LICENSE" --exclude "README.md"
CloudFormation Stack Operations
CloudFormation stacks can be created, updated, and deleted using the following commands.

Create Stack
Production
sh
Copy code
aws cloudformation create-stack --stack-name bottest-api-prod-app-us-east-1 --template-body file://code/cfn/stacks/prod/prod-main.yml --parameters ParameterKey=project,ParameterValue=bottest-ai ParameterKey=env,ParameterValue=prod ParameterKey=dBUsername,ParameterValue=postgres ParameterKey=dBPassword,ParameterValue=postgres123 ParameterKey=slackToken,ParameterValue=xyz-123 ParameterKey=openaiApiKey,ParameterValue=xyz-123 ParameterKey=jwksUrl,ParameterValue=xyz-123 ParameterKey=environment,ParameterValue=xyz-123 ParameterKey=clerkApiKey,ParameterValue=xyz-123 --capabilities CAPABILITY_NAMED_IAM
Development
sh
Copy code
aws cloudformation create-stack --stack-name bottest-api-dev-app-us-east-1 --template-body file://code/cfn/stacks/dev/dev-main.yml --parameters ParameterKey=project,ParameterValue=bottest-ai ParameterKey=env,ParameterValue=dev ParameterKey=dBUsername,ParameterValue=postgres ParameterKey=dBPassword,ParameterValue=postgres123 ParameterKey=slackToken,ParameterValue=xyz-123 ParameterKey=openaiApiKey,ParameterValue=xyz-123 ParameterKey=jwksUrl,ParameterValue=xyz-123 ParameterKey=environment,ParameterValue=xyz-123 ParameterKey=clerkApiKey,ParameterValue=xyz-123 --capabilities CAPABILITY_NAMED_IAM
Update Stack
Production
sh
Copy code
aws cloudformation update-stack --stack-name bottest-api-prod-app-us-east-1 --template-body file://code/cfn/stacks/prod/prod-main.yml --parameters ParameterKey=project,ParameterValue=bottest-ai ParameterKey=env,ParameterValue=prod ParameterKey=dBUsername,ParameterValue=postgres ParameterKey=dBPassword,ParameterValue=postgres123 ParameterKey=slackToken,ParameterValue=xyz-123 ParameterKey=openaiApiKey,ParameterValue=xyz-123 ParameterKey=jwksUrl,ParameterValue=xyz-123 ParameterKey=environment,ParameterValue=xyz-123 ParameterKey=clerkApiKey,ParameterValue=xyz-123 --capabilities CAPABILITY_NAMED_IAM
Development
sh
Copy code
aws cloudformation update-stack --stack-name bottest-api-dev-app-us-east-1 --template-body file://code/cfn/stacks/dev/dev-main.yml --parameters ParameterKey=project,ParameterValue=bottest-ai ParameterKey=env,ParameterValue=dev ParameterKey=dBUsername,ParameterValue=postgres ParameterKey=dBPassword,ParameterValue=postgres123 ParameterKey=slackToken,ParameterValue=xyz-123 ParameterKey=openaiApiKey,ParameterValue=xyz-123 ParameterKey=jwksUrl,ParameterValue=xyz-123 ParameterKey=environment,ParameterValue=xyz-123 ParameterKey=clerkApiKey,ParameterValue=xyz-123 --capabilities CAPABILITY_NAMED_IAM
Delete Stack
Production
sh
Copy code
aws cloudformation delete-stack --stack-name bottest-api-prod-app-us-east-1
Development
sh
Copy code
aws cloudformation delete-stack --stack-name bottest-api-dev-app-us-east-1
Environment Specific Instructions
Production (PROD)
Sync Files: Use the S3 sync command under the "Sync - PROD" section.
Create/Update/Delete Stack: Use the appropriate CloudFormation command under the "PROD" section.
Development (DEV)
Sync Files: Use the S3 sync command under the "Sync - DEV" section.
Create/Update/Delete Stack: Use the appropriate CloudFormation command under the "DEV" section.
Notes
Ensure all sensitive parameters (e.g., passwords, API keys) are securely managed and not hard-coded in your scripts or templates.
Adjust the paths and parameters in the commands as needed to fit your specific project structure and requirements.