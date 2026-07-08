<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Access S3 from a VPC

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-s3)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

## Access S3 from a VPC

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-s3_3e1e79a2)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is an AWS foundational networking service and it is useful because it allows us to create our own isolated networks within an AWS region and control network traffic and security e.t.c 

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to to launch an EC2 instance, directly access and manage an Amazon s3 bucket through the EC2 instance using AWS CLI.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was that credentials were required to get access to my AWS environment despite already logging in.

### This project took me...

This project took me 1 hour.

---

## In the first part of my project...

### Step 1 - Architecture set up

In this step, I will set up a VCPC with an EC2 instance from scratch because it the first step to accessing my Amazon S3 through my instance.

### Step 2 - Connect to my EC2 instance

In this step, I will connect my EC2 instance because it will enable me to access an AWS service which is S3 in my case.

### Step 3 - Set up access keys

In this step, I will set up access keys for my EC2 instance because it gives it access to my AWS services in this case s3.

---

## Architecture set up

I started my project by launching a VPC with one pubblic subnet and an EC2 instance.

I also set up an S3 bucket and added two files into the bucket.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-s3_4334d777)

---

## Running CLI commands

AWS CLI is is a tool for controlling AWS services directly from the command line i.e the terminal. I have access to AWS CLI because it comes pre-installed by default with my EC2 instance.

The first command I ran was AWS s3 ls This command is used to list all the available s3 buckets in my EC2 instance.

The second command I ran was 'aws configure'. This command is used to set up my Credentials which includes access key ID as part of the credentials.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-s3_e7fa8776)

---

## Access keys

### Credentials

To set up my EC2 instance to interact with my AWS environment, I configured access key ID, secret key, region and default output format.

Access keys are are part of my credential and equivalent to a username. They are used by my application and servers for logging into AWS and talking to my AWS services or resources.

Secret access keys are are part of Credential that pairs with access key ID to access AWS services.

### Best practice

Although I'm using access keys in this project, a best practice alternative is to use IAM roles with permissions attached. This is more secure because its easier to track, attach and detach policies.

---

## In the second part of my project...

### Step 4 - Set up an S3 bucket

In this step, I will launch an s3 bucket because it will be used to test my EC2 instance connection with services outside its VPC.

### Step 5 - Connecting to my S3 bucket

In this step, I will use the AWS CLI to interact with the s3 bucket  because it shows s3 interaction with EC2 instance.

---

## Connecting to my S3 bucket

The first command I ran was AWS s3 ls This command is used to list all the available s3 buckets in my EC2 instance.

When I ran the command AWS s3 ls again, the terminal responded with my s3 bucket. This indicated my access key works i.e my EC2 instance has access to my AWS environment

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-s3_4334d778)

---

## Connecting to my S3 bucket

Another CLI command I ran was 'aws s3 ls s3://nextwork-vpc-project-bildad' which returned a list of objects in my s3 bucket.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-s3_4334d779)

---

## Uploading objects to S3

To upload a new file to my bucket, I first ran the command 'sudo touch /tmp/test.txt' . This command creates a blank file called test.txt in my EC2 instance local directory.

The second command I ran was 'aws s3 cp /tmp/test.txt s3://nextwork-vpc-project-bildad'. This command will copy the blank file created into my s3 bucket.

The third command I ran was 'aws s3 ls s3://nextwork-vpc-project-bildad' which validated that my EC2 instance through AWS CLI command can get access to other AWS services like s3.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-s3_3e1e79a2)

---

---
