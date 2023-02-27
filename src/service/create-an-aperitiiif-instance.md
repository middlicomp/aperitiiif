---
layout: page
title: '1: Set up the AWS Stack'
nav_order: 1
parent: Set up an Aperitiiif service instance
---
# {{ page.title }} <span class="label label-purple">Work in Progress!</span>
{: .fs-9 }

Last Updated: 2/27/2023  
Approximate time to complete: ~1hr

## Role <span class="label label-green">Admin</span>


- The user following these guides should be a core staff member and must have admin access to both the AWS account and the GitHub Org mentioned above.


## Steps

### 1. Create AWS IAM Groups and Users
- [ ] Log into your AWS account.
- [ ] Search "IAM" and navigiate to the IAM Dashboard.
- [ ] Navigate to "User Groups" under "Access Management"
- [ ] Click the "Create group" button.
- [ ] Name the group `serverless-iiif-sam-service-access` and scroll down to "Attach permissions policies - Optional." Then search for and add the following policies:
    - `IAMFullAccess`
    - `AmazonS3FullAccess`
    - `AWSLambda_FullAccess`
    - `AWSCloudFormationFullAccess`
    - `CloudFrontFullAccess`
- [ ] Click "Create group"
- [ ] Still within the IAM Dashboard, navigate to "Users" under "Access Management"
- [ ] Click the "Add users" button.
- [ ] Create a user named `aperitiiif-sam-deploy` and click "Next"
- [ ] Under "Set permissions" select "Add user to group" and check the `serverless-iiif-sam-service-access` group you just created. Then click "Next"
- [ ] Scroll down and click "Create user"
- [ ] Click on your new `aperitiiif-sam-deploy` user and navigate to the "Security credentials" tab.
- [ ] Scroll down to "Access keys" and click the "Create access key" button.
- [ ] Select "Command Line Interface (CLI)" option, check the "I understand...." box and click "Next"
- [ ] Click "create access key"
- [ ] Scroll down and IMMEDIATELY click "Download .csv file". Make sure you save these credentials somewhere secure and reliable (e.g., a secure Box account)! You won't be able to see these values on this page again.

## 2. Create S3 Buckets for Source Images and IIIF manifests.

- [ ] Still in AWS, search "S3" and navigate to the Amazon S3 Dashboard.
- [ ] Go to "Buckets" and click the "Create Bucket" button.
- [ ] Create S3 source bucket for source images named something like `aperitiiif-source-images`. 
  + Select the region `us-east-1`
  + Select the `ACLs enabled` option 
  + Unselect `Block all public access`
  + Acknowledge the settings checkbox
  + Scroll to the bottom and click the "Create bucket" button.
- [ ] Click the "Create Bucket" button again.
- [ ] Create S3 bucket for IIIF presentation API JSON files named something like `aperitiiif-presentation-api-store` with the same options as the same settings as the previous bucket:
  + Select the region `us-east-1`
  + Select the `ACLs enabled` option 
  + Unselect `Block all public access`
  + Acknowledge the settings checkbox
  + Scroll to the bottom and click the "Create bucket" button.
- [ ] Click on the name of your IIIF presentation API bucket, (e.g., `aperitiiif-presentation-api-store`).
- [ ] Click on the "Permissions" tab and sroll down to the "Cross-origin resource sharing (CORS)" section.
- [ ] Click the "Edit" button, paste in the following JSON and then click "Save Changes"

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


## 3. Set up local development enviroment to use AWS CLI
- [ ] Navigate to your local shell of choice (e.g., Terminal, Zsh)
- [ ] Check if Git is installed: `git --verison`; if not install it: `brew install git`
- [ ] Check if AWS-CLI is installed: `aws --version`; if not, install it: `brew install awscli`.
- [ ] Check if AWS SAM CLI is installed: `sam --version`; if not, install it: 
    ```
    brew tap aws/tap
    brew install aws-sam-cli
    ```
- [ ] Check if Docker is installed: `docker --version`; if not, [install it](https://docs.docker.com/desktop/install/mac-install/).
- [ ] Make sure that Docker is running by opening the application icon.

## 4. Deploy the Serverless-IIIF intance.
- [ ] Clone the Serverless-IIIF repository you forked into your GitHub Org to your local machine & cd into it.
- [ ] Run `aws configure --profile aperitiiif-sam-deploy` with the AWS user credentials you saved, plus `us-east-1` as the default region and `json` as default output format.
- [ ] Run `cd sam/cloudfront && sam build --use-container`
- [ ] Run `sam deploy --capabilities CAPABILITY_IAM CAPABILITY_AUTO_EXPAND --guided --profile aperitiiif-sam-deploy`. Default values can be used except those mentioned below. (This will take several minutes)
  - Stack Name: `serverless-iiif-stack`
  - SourceBucket: `(the source image bucket you created)`
  - IiifFunction Function Url may not have authorization defined, Is this okay?: `y`
- [ ] When the above process is complete, it will output the IIIF Endpoint URL. Copy this url somewhere safe.