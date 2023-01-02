# Project Title - Deploy a high-availability web app using CloudFormation
This repo is targetted at gaining hands n experience on Infrastructure as Code @ Udacity - ND9991 - C2- Infrastructure as Code.
This repo contains the following files:

* network-infrastructure.yml: This file together with network-parameters.json creates the network infrascture for the system
* udagramServers.yml: together with server-parameter.json provisions and scales horizontally or vertically servers and some other underlying resources to meet the requirements of the system.
* Udagram Sys Arch.png: System architectural diagram. 


## Project Scenario / Problem Statements

* Your company is creating an Instagram clone called Udagram.

* Developers want to deploy a new application to the AWS infrastructure.

* You have been tasked with provisioning the required infrastructure and deploying a dummy application, along with the necessary supporting software.

* This needs to be automated so that the infrastructure can be discarded as soon as the testing team finishes their tests and gathers their results.

* Optional - To add more challenge to the project, once the project is completed, you can try deploying sample website files located in a public S3 Bucket to the Apache Web Server running on an EC2 instance. Though, it is not the part of the project rubric.

## System Architectural Diagram
![system_architecture](/Udagram%20Sys%20Arch.png)

## Server Specs

* A  Launch Configuration for the application servers in order to deploy four servers, two located in each private subnets. The launch configuration will be used by an auto-scaling group.

* Two vCPUs and at least 4GB of RAM. The Operating System to be used is Ubuntu 18. An Instance size and Machine Image (AMI) that best fits this spec is to be choosed.

* At least 10GB of disk space is to be allocated.


## Security Groups and Roles

* Since the application archive wil be fetched from an S3 Bucket, there is need to create an IAM Role that will allow instances to use the S3 Service.

* Udagram communicates on the default HTTP Port: 80, so your servers will need this inbound port open since it will be used with the Load Balancer and the Load Balancer Health Check. As for outbound, the servers will need unrestricted internet access to be able to download and update their software.

* The load balancer should allow all public traffic (0.0.0.0/0) on port 80 for inbound traffic, which is the default HTTP port. For outbound traffic, it will only be using port 80 to reach the internal servers.

* The application needs to be deployed into private subnets with a Load Balancer located in a public subnet.
One of the output exports of the CloudFormation script should be the public URL of the LoadBalancer. 
Bonus point: one can add http:// in front of the load balancer DNS Name in the output, for convenience.

