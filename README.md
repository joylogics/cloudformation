# Joylogics CloudFormation Templates

## S3_Website_for_WP2Static.yaml
[![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=build-s3-website-for-wp2static&templateURL=https://jl-cloudformation.s3.us-east-1.amazonaws.com/S3_Website_for_WP2Static.yaml)
### Usecase
Create a simple, low-cost static website hosted on S3 to be used with WP2Static (WordPress plugin).
### Prerequisites
* Route 53 Hosted Zone to place the DNS record for the website's URL.
### Parameters
* HostedZone - The DNS name of an existing Amazon Route 53 hosted zone (E.g., "joylogics.com")
* SubdomainName - The subdomain name of the website (E.g, "www")
### Creates
* S3 bucket for hosting - named from the URL. (E.g., "www.joylogics.com")
* An IAM User in this account specifically for uploading content to the S3 bucket.
* DNS record in the HostedZone.
### Outputs
* WebsiteURL: The URL of the website
* BucketName: Name of S3 bucket for the website
* S3BucketUser: IAM User for pushing data to the S3 bucket
* S3UserAccessKeyID: Access Key ID for the IAM User
* S3UserSecretAccessKey: Secret Access Key for the IAM User

## WordPress_Single_Instance.yaml
From [awslabs cloudformation templates repo](https://github.com/awslabs/aws-cloudformation-templates). 
This [version](https://github.com/awslabs/aws-cloudformation-templates/blob/e5362c99375ca49d4da56973c95dda81742667e0/aws/solutions/WordPress_Single_Instance.yaml) was copied.
[![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=build-s3-website-for-wp2static&templateURL=https://jl-cloudformation.s3.us-east-1.amazonaws.com/WordPress_Single_Instance.yaml)
### Usecase
Create an EC2 instance with WordPress installed on it.
### Prerequisites
If you have not done so, create an EC2 KeyPair which is needed for accessing the EC2 instance via SSH.
This is needed in those cases you'll want to maintain/manage the OS and the software installed on it.
For example, you would want to apply security patches. 
Note the SSHLocation can be used to lock down the source IP address for the EC2 instance as well.
### Parameters
* DBName: The WordPress database name
* DBPassword: The WordPress database admin account password
* DBRootPassword: MySQL root password
* DBUser: The WordPress database admin account username
* InstanceType: WebServer EC2 instance type
* KeyName: Name of an existing EC2 KeyPair to enable SSH access to the instances
* SSHLocation: The IP address range that can be used to SSH to the EC2 instances
### Creates
* An EC2 instance with WordPress installed in it.
* Security Group for the EC2 instance
### Outputs
* PublicIP: EC2 public IP
* WebsiteURL: WordPress Website

