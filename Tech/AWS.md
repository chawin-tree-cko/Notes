# AWS

## Links

* [AWS Online Console](https://console.aws.amazon.com/console/home)
* [AWS Command Line Interface](https://aws.amazon.com/cli/)

----

## Acronyms

* Elastic Container Registry (ECR) - a Docker container registry to store, manage and deploy container images
* Elastic Compute Cloud (EC2) - web service that provides secure, resizable compute capacity in the cloud
* Elastic Container Service (ECS) - a regional grouping of one or more container instances on which you can run task requests
* Elastic Load Balancing (ELB) - automatically distributes incoming application traffic across multiple targets
* Elastic Block Store (EBS) - high performance block storage service designed for use with EC2
* Elastic File System (EFS) - a simple, scalable, fully managed elastic network file system (NFS)
* Relational Database Service (RDS) -  simple, scalable, fully managed relational database
* Network Access Conctrol Layer (NACL) - an optional layer of security for your VPC that acts as a firewall for controlling traffic in and out of one or more subnets
* Virtual Private Cloud (VPC) - a virtual network hosted in AWS
* Amazon Machine Images (AMI) - provides the information required to launch an instance

----

## Useful commands

### Admin

* `aws configure` - sets the credentials to be used for the AWS CLI; requires an account with an access key to have been set up

### ECR

* `aws ecr create-repository --repository-name hello-repository --region us-east-2` - creates an ECR repository called *hello-repository* with the region *us-east-2*
* `aws ecr delete-repository --repository-name hello-repository --region region --force` -  deletes an ECR repository called *hello-repository* with the region *us-east-2*
* `aws ecr get-login --no-include-email` - returns a login command for Docker
* `Invoke-Expression -Command (aws ecr get-login --region us-east-2 --no-include-email)` *(Powershell)* - completes a Docker login in one command

----

## Pushing an image to an AWS ECR

1. Tag the the Docker image - `docker tag hello-world aws_account_id.dkr.ecr.region.amazonaws.com/hello-repository`
1. Login to Docker - `Invoke-Expression -Command (aws ecr get-login --region us-east-2 --no-include-email)`
1. Push tagged images to ECR - `docker push aws_account_id.dkr.ecr.region.amazonaws.com/hello-repository`
