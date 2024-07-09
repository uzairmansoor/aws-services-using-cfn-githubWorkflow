# Bottest AI Application Deployment

This document provides instructions for deploying the Bottest AI application in both production (PROD) and development (DEV) environments using AWS S3 and AWS CloudFormation.

## Table of Contents
1. [Syncing Files to S3](#syncing-files-to-s3)
2. [CloudFormation Stack Operations](#cloudformation-stack-operations)
    - [Create Stack](#create-stack)
    - [Update Stack](#update-stack)
    - [Delete Stack](#delete-stack)
3. [Environment Specific Instructions](#environment-specific-instructions)
    - [Production (PROD)](#production-prod)
    - [Development (DEV)](#development-dev)

## Syncing Files to S3

Before deploying the CloudFormation stack, ensure the necessary files are synced to the appropriate S3 bucket.

### Production
```sh
aws s3 sync . s3://bottest-ai-app-prod-us-east-1-122253718099/ --exclude ".git/*" --exclude "LICENSE" --exclude "README.md"
