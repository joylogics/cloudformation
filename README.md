# Joylogics CloudFormation Templates

## S3_Website_for_WP2Static.yaml
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
### Launcher
This template creates an S3 bucket to host a simple static website over HTTP
[![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=build-s3-website-for-wp2static&templateURL=https://s3.amazonaws.com/my-great-stack.json)


