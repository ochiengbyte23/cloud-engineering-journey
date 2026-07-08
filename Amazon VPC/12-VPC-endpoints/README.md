<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Endpoints

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-endpoints)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

## VPC Endpoints

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-endpoints_09bcaa8a)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a networking service provided by AWS  and it is useful because it enables  isolation our resources from the internet, setting up secure connections between our resources and controlling traffic security.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to set up a VPC endpoint to provide my VPC direct private access to other AWS services i.e S3.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was being able to edit the endpoint policy which controls service access of the endpoint. 

### This project took me...

This project took me 2 hours to complete.

---

## In the first part of my project...

### Step 1 - Architecture set up

In this step, I will set up a VPC, EC2 instance and s3 bucket because it is the foundation for my project for privately accessing AWS services.

### Step 2 - Connect to EC2 instance

In this step, I will connect directly to my EC2 instance using EC2 instance connect because this will help in accessing s3 and running commands later in the project.

### Step 3 - Set up access keys

In this step, I will create access keys because it gives my EC2 instance access to my AWS environment.

### Step 4 - Interact with S3 bucket

In this step, I will use my access key credentials to my EC2 instance because it confirms if my AWS CLI and EC2 instance can access my Amazon s3.

---

## Architecture set up

I started my project by launching a VPC with one public subnet and an EC2 instance.

I also set up an s3 bucket and uploaded two files into the bucket.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-endpoints_4334d777)

---

## Access keys

### Credentials

To set up my EC2 instance to interact with my AWS environment, I configured the access key ID ,secret key, region and the output format.

Access keys are credentials for my applications and servers to login into AWS and talk to my AWS services or resources.

Secret access keys are is part of credential paired with access key and is used for access

### Best practice

Although I'm using access keys in this project, a best practice alternative is to use IAM admin roles instead. This means the necessary permissions will be attached to an IAM role and the role will be associated with the relevant resources.

---

## Connecting to my S3 bucket

The command I ran was 'aws s3 ls'. This command is used to list all my available s3 buckets.

The terminal responded with a list of my s3 bucket. This indicated that the access keys I set up correctly gave my EC2 instance access to my AWS environment.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-endpoints_4334d778)

---

## Connecting to my S3 bucket

I also tested the command 'aws s3 ls s3://nextwork-vpc-project-bildad' which returned a list of files inside my s3 bucket.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-endpoints_4334d779)

---

## Uploading objects to S3

To upload a new file to my bucket, I first ran the command 'sudo touch /tmp/nextwork.txt'. This command creates an empty file called nextwork.txt and saves it locally in the EC2 instance.

The second command I ran was 'aws s3 cp /tmp/nextwork.txt s3://nextwork-vpc-project-bildad'. This command will copy the created file and pload it to my s3 bucket.

The third command I ran was 'aws s3 ls s3://nextwork-vpc-project-bildad' which validated that a new file was created and uploaded into my s3 bucket successfully. 

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-endpoints_3e1e79a2)

---

## In the second part of my project...

### Step 5 - Set up a Gateway

In this step, I will set up a VPC endpoint  because it enables direct and secure communication between VPC and AWS services like s3.

### Step 6 - Bucket policies

In this step i am going to block off all S3 bucket traffic  except the traffic from my endpoint. I am doing this to confirm that my endpoint can access S3.

### Step 7 - Update route tables

In this step, I will test my VPC endpoint setup because it confirms troubleshoot if there is a connectivity issue.

### Step 8 - Validate endpoint conection

In this step, I will i will validate my VPC endpoint set up one more time because it confirms if my troubleshoot solved the traffic access permissions.

---

## Setting up a Gateway

I set up an S3 Gateway, which is a type of endpoint specifically for S3 and DynamoDB. It simply directs traffic from the VPC route table to the gateway.

### What are endpoints?

An endpoint is an AWS service that allows private connection between a VPC and other AWS service without going over the internet.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-endpoints_09bcaa8a)

---

## Bucket policies

A bucket policy is a type of IAM policy designed for setting access permission to an S3 bucket. It determines who can visit the bucket and what they can do in the bucket.

My bucket policy will deny all actions on my S3 bucket and its object to everyone unless the access is from my VPC endpoint.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-endpoints_7316a13d)

---

## Bucket policies

Right after saving my bucket policy, my S3 bucket page showed 'denied access' warnings. This was because my bucket policy denies all actions unless they are from a VPC endpoint.

I also had to update my route table because it did not provide a route for traffic in my public subnet to the VPC endpoint.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-endpoints_4ec7821f)

---

## Route table updates

To update my route table, I modified my route table from the VPC endpoint console to accept traffic from my public subnet.

After updating my public subnet's route table, my terminal could return all the objects available in my S3 bucket. This means my EC2 instance could now connect to the S3 bucket successfully.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-endpoints_d116818e)

---

## Endpoint policies

An endpoint policy is a type of IAM policy designed for specifying the range of resources and actions denied or permitted by the policy.

I updated my endpoint's policy by denying all actions  I could see the effect of this right away, because my EC2 instance command to list all objects in my S3 bucket was denied access. 

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-networks-endpoints_3e1e79a3)

---

---
