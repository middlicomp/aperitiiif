---
layout: page
title: 'Create an Aperitiiif instance'
nav_order: 1
parent: Admin Guides
---
# {{ page.title }} <span class="label label-purple">Work in Progress!</span>
{: .fs-9 }

## Prerequisites
- An AWS Account
- A GitHub Organization
- A local development environment (these instructions assume Mac with Homebrew) with sudo access

## Role <span class="label label-green">Admin</span>


- The user following these guides should be a core staff member and must have admin access to both the AWS account and the GitHub Org mentioned above.


## Steps

### 1. Create AWS IAM Groups and Users
- [ ] Log into your AWS account.
- [ ] Search "IAM" and navigiate to the IAM Dashboard.
- [ ] Navigate to "User Groups" under "Access Management"
- [ ] Click the "Create group" button.
- [ ] Name the group `sam-service-access` and scroll down to "Attach permissions policies - Optional." Then search for and add the following policies:
    - `IAMFullAccess`
    - `AmazonS3FullAccess`
    - `AWSLambda_FullAccess`
    - `AWSCloudFormationFullAccess`
    - `CloudFrontFullAccess`
- [ ] Click "Create group"
- [ ] Still within the IAM Dashboard, navigate to "Users" under "Access Management"
- [ ] Click the "Add users" button.
- [ ] Create a user named `aperitiiif-sam-deploy` and click "Next"
- [ ] Under "Set permissions" select "Add user to group" and check the `sam-service-access` group you just created. Then click "Next"
- [ ] Scroll down and click "Create user"
- [ ] Click on your new `aperitiiif-sam-deploy` user and navigate to the "Security credentials" tab.
- [ ] Scroll down to "Access keys" and click the "Create access key" button.
- [ ] Select "Command Line Interface (CLI)" option, check the "I understand...." box and click "Next"
- [ ] Click "create access key"
- [ ] Scroll down and IMMEDIATELY click "Download .csv file". Make sure you save these credentials somewhere secure and reliable (e.g., a secure Box account)! You won't be able to see these values on this page again.

## Set up local development enviroment to use AWS CLI
- [ ] Check if AWS-CLI is installed `aws --version` if not, install it: `brew install awscli`.
- [ ] Check if AWS SAM CLI is installed `sam --version` if not, install it: 
    ```
    brew tap aws/tap
    brew install aws-sam-cli
    ```
- [ ] Check if Docker is installed `docker --version` if not, [install it](https://docs.docker.com/desktop/install/mac-install/).
- [ ] Make sure that Docker is running by opening the App.
- [ ] Run `aws configure --profile aperitiiif-sam-deploy` with credentials plus `us-east-1` as the default region and `json` as default output format.
- [ ] Run `cd sam/cloudfront && sam build --use-container`
- [ ] Run `sam deploy --capabilities CAPABILITY_IAM CAPABILITY_AUTO_EXPAND --guided --profile aperitiiif-sam-deploy`
  - Stack Name: `aperitiiif-serverless-iiif`
  - SourceBucket: `aperitiiif-serverless-iiif-source-images`
  - Managed S3 bucket: `aws-sam-cli-managed-default-samclisourcebucket-1er0it3bgmcdy`
- [ ] Create S3 source bucket `aperitiiif-serverless-iiif-source-images`

-------
WiP

Additional Aperitiiif stuff:
- [ ] Create S3 bucket for IIIF presentation API JSON `aperitiiif-presentation-api-store` 
  - [ ] Enable ACLs on the bucket (in GUI)
  - [ ] Add the following CORS policy (in GUI)
      ``` json
        [
          {
            "AllowedHeaders": [
              "Authorization"
            ],
            "AllowedMethods": [
              "GET",
              "HEAD"
            ],
            "AllowedOrigins": [
              "*"
            ],
            "ExposeHeaders": [
              "Access-Control-Allow-Origin"
            ]
          }
        ]
      ```
