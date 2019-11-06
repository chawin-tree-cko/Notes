# AWS

## Acronyms

* Elastic Container Registry (ECR) - a Docker container registry to store, manage and deploy container images
* Elastic Compute Cloud (EC2) - web service that provides secure, resizable compute capacity in the cloud

----

## Useful commands

[Download the AWS Command Line Interface](https://aws.amazon.com/cli/)

* `aws configure` - sets the credentials to be used for the AWS CLI; requires an account with an access key to have been set up
* `aws ecr get-login --no-include-email` - returns a login command for Docker
* `Invoke-Expression -Command (aws ecr get-login --region us-east-2 --no-include-email)` *(Powershell)* - completes a Docker login in one command


----

## Pushing an image to an AWS ECR

1. Tag the the Docker image - `docker tag hello-world aws_account_id.dkr.ecr.region.amazonaws.com/hello-repository`
1. Login to Docker - `Invoke-Expression -Command (aws ecr get-login --region us-east-2 --no-include-email)`
1. Push tagged images to ECR - `docker push aws_account_id.dkr.ecr.region.amazonaws.com/hello-repository`
