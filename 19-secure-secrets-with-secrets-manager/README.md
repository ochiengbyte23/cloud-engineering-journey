<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Secure Secrets with Secrets Manager

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-secretsmanager)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-secretsmanager_r7s8t9u0)

---

## Introducing Today's Project!

In this project, I will demonstrate how to secure secrets with AWS secret manager. I'm doing this project to learn how to protect sensitive data.

### Tools and concepts

Services I used were Secret Manager, S3, GitHub,  IAM. Key concepts I learnt include GitHub secret scanning, the risk of hardcoding credentials and not deleting their commits .

### Project reflection

This project took me approximately 3 hours including the documentation. The most challenging part was getting rid of the specific commit history of hardcoded credentials without any merging errors. It was most rewarding to finally update my commit history to remove the hardcoded credentials.

I chose to do this project today because it is part of AWS cloud engineering journey and to also learn about securing code using AWS Secret Manager. 

---

## Hardcoding credentials

In this project, a sample web app is exposing AWS credentials. It is unsafe to hardcode credentials because the can be used to access the AWS account and delete, steal or damage resources.

I've set up the initial configuration with  fake AWS credential in cofig.py. These credentials are just examples because using my actual credentials would expose my account to security risks.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-secretsmanager_j2k3l4m5)

---

## Using my own AWS credentials

As an extension for this project, I also decided to open a virtual environment to store the packages in the requirement file. to set up my virtual environment, I installed fastapi, boto3, uvicorn and many other packages in requirement.txt .

When I first ran the app, I ran into an 'InvalidAccesskeyId' error because the placeholder AWS credentials hardcoded in cofig.py were invalid.

To resolve the 'InvalidAccessKeyId' error, I updated the config.py with my real AWS credentials. It now contains access key ID, secret access key and region matching my real AWS account.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-secretsmanager_wghjteykut)

---

## Pushing Insecure Code to GitHub

Once I updated the web app code with credentials, I forked the repository because i wanted to push the updated code to my own copy of the repository in GitHub. A fork is different from a clone since it create the copy in GitHub account unlike a clone which is stored offline in the local device.

To connect my local repository to the forked repository, I ran 'git remote set-url origin' command . Then I used git add and git commit to save the changes i made to config.py. Finally, git push uploads the changes to the forked repository.

GitHub blocked my push because it scanned it and found secrets in my code. This is a good security feature because it prevents accidental pushing of security features.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-secretsmanager_o2p3q4r5)

---

## Secrets Manager

Secrets Manager is an AWS service for storing and managing secrets I'm using it to store my AWS access key credentials. Other common use cases include securing database credentials, API keys and more.

Another feature in Secrets Manager is Secret rotation. which means to regularly change the secrets. It's useful in situations where the secrets have been compromised since it makes it valid for a limited time.

Secrets Manager provides sample code in various languages, like Java, python, ruby and javascript. This is helpful because it shows how to retrieve secrets from secret manager in the application code.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-secretsmanager_h2i3j4k5)

---

## Updating the web app code

I updated the config.py file to retrieve secrets from AWS secret manager instead of the previously hardcoded credentials. The get_secret() function will create a client that interacts with secret manager to retrieve secrets securely.

I also added code to config.py to extract the credentials from the get_secret() function into global variables. This is important because the get_secret() function only fetches the secret from Secrets Manager, but we need to assign those values to the specific variables (like AWS_ACCESS_KEY_ID) that app.py imports to run the web app.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-secretsmanager_v0w1x2y3)

---

## Rebasing the repository

Git rebasing is rewriting my commit history. I used it to drop the commit history of the hardcoded AWS credentials. This was necessary because pushing code to github that still contains this history will not only fail github's scanning but is also a major security risk.

A merge conflict occurred during rebasing because I change the same lines of code in different commits. I resolved the merge conflict by accepting incoming changes which did not contain hardcoded credentials. '

Once the merge conflict was resolved, I verified that by looking at commit history of config.py in GitHub and confirming that the commit containing the hardcoded credentials was missing.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-secretsmanager_t5u6v7w8)

---

---
