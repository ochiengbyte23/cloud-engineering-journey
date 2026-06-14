<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Cloud Security with AWS IAM

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-iam)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-iam_1c864649)

---

## Introducing Today's Project!

### Project overview

In this project, I will demonstrate how to implement IAM services to control access and permission in my AWS account. I'm doing this project to learn  about cloud security from the basic level.

### Tools and concepts

Services I used were Amazon EC2 and AWS IAM. Key concepts I learnt include IAM users, policies, user groups and account aliases. I also leant how to use  a policy simulator, how to launch an instance, how to tag an instance and how to login as another user.

### Project reflection

This project took me approximately 2 hours including demo time. The most challenging part was understanding the IAM policy since it was written in JSON and it contained multiple statements. It was most rewarding to that the set policies worked as set.

---

## Tags

### What I did in this step

In this step, I will launch two Amazon EC2 instances in order to boost NextWorks's computing power because we need to match the increased traffic to the website.

### Understanding tags

Tags are are key value pair labels used to organise AWS resources. They ease identification and cost tracking. Tags can also be used to apply specific IAM policies to a specific environment

### My tag configuration

The tag I’ve used on my EC2 instances is called environment(Env).The value I’ve assigned for my instances are production and development which typically used in software development . They are intuitive and easier to remember.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-iam_2e0e5a5d)

---

## IAM Policies

### What I did in this step

In this step, I will create an IAM policy in order to give the intern access to the development instance only because they might accidentally push their tests to the production environment which is not ideal

### Understanding IAM policies

IAM Policies are are rules that control who can access the AWS resources and what they can and not access. I am using policies to control access to the production and development environment.

### The policy I set up

For this project, I’ve set up a policy using JSON.

### Policy effect

I’ve created a policy that that allows the intern to full access to the development environment at any instance . They can also see information for any instance but deleting any ec2 tags is blocked.

### Understanding Effect, Action, and Resource

The Effect, Action, and Resource attributes of a JSON policy means that you can allow or deny policy actions on AWS resources in a controlled manner

---

## My JSON Policy

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-iam_1c864649)

---

## Account Alias

### What I did in this step

In this step, I will create an AWS account alias because it simplifies user login to the AWS account.

### Understanding account aliases

An account alias is a user friendly name used to login to the AWS console insted of the default ID which is a bunch of digits

### Setting up my account alias

Creating an account alias took me a  minute. Now, my new AWS console sign-in URL is https://nextwork-alias-bildad.signin.aws.amazon.com/console


![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-iam_0eb4439b)

---

## IAM Users and User Groups

### What I did in this step

In this step, I will set up a dedicated IAM group and user  because the interns need a way to login to the console and permissions should be controlled from one point

### Understanding user groups

IAM user groups are are a collections or folders of users that will get access to the AWS account for easier user management

### Attaching policies to user groups

I attached the policy I created to this user group, which means all users in the group will have to abide by the attached policy.

### Understanding IAM users

IAM users are people who can login into the AWS account.

---

## Logging in as an IAM User

### Sharing sign-in details

The first way is is to email sign-in instructions to the user and the second way is to download the csv file.

### Observations from the IAM user dashboard

Once I logged in as my IAM user, I noticed some of the panels were denied access. This was because of the IAM policy i created earlier to restrict user activities to EC2  instance

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-iam_6f2ab446)

---

## Testing IAM Policies

### What I did in this step

In this step, I will login to AWS using the intern's IAM user and tests the intern's access to the production and development environment because it will confirm if the access has been set per the requirements

### Testing policy actions

I tested my JSON IAM policy by trying to stop both the production and development instances.

### Stopping the production instance

When I tried to stop the production instance but was met with an error. This was because the production instance is tagged with the "production" label which is outside the scope of our permission policy. Only the development instance was allowed access.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-iam_0e7a9d6a)

### Stopping the development instance

Next, when I tried to stop the development instance, the instance state change to stopping and finally stopped. This was because our permission policy allows the intern to stop instances in development

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-iam_1811801c)

---

## IAM Policy Simulator

To extend my project, I'm going to use the IAM policy simulator to test user access in a controlled manner . I'm doing this because testing instances directly can be disruptive to other users.

### Understanding the IAM Policy Simulator

The IAM Policy Simulator is a tool to test and simulate user policy permissions setting by defining a specific user/group/role we run the test for. It's useful for saving time when testing permission setting.

### How I used the simulator

I set up a simulation for whether the development user group has permission to stop instances or delete tags. The results were denied for both. I had to adjust the scope of the ec2 instances to ones that are tagged with development. Once the tag was applied permission was allowed

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-iam_069d8a621)

---

---
