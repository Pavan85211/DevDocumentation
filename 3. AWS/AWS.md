Hey,
It’s Sarvar Nadaf again, a senior developer at Luxoft. I worked on several technologies like Cloud Ops (Azure and AWS), Data Ops, Serverless Analytics, and Dev Ops for various clients across the globe.

Today, we’ll look into AWS EKS’s fundamentals. This post will assist you in setting up the various command-line interfaces that will enable you to communicate with the AWS EKS cluster from a laptop or other Linux-based device. Today, we will configure ESKCTL, Kubectl, and the AWS CLI. With each Linux distribution, there are a few minimal requirements and differences. I’m setting up all of these command-line tools on an Amazon Linux 2 machine today. Simply, I’ll obtain a free tier Amazon Linux 2 server and let's begin configuring command-line interfaces.

AWS CLI -
The open-source AWS CLI is a really powerful resource. This enables our interaction with the entire AWS service. Just by doing a few simple steps, we may operate our AWS account from anywhere.

Prerequisite -
AWS Account
IAM User
Access key ID and Secret access key
1. Use the following command to become the root user. so no extra sudo command for each step.

[ec2-user ~]$ sudo su -
