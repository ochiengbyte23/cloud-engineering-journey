<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Threat Detection with GuardDuty

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-guardduty)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-guardduty_v1w2x3y4)

---

## Introducing Today's Project!

### Tools and concepts

The services I used were AWS CloudFormation, GuardDuty, S3  and and OWASP. Key concepts I learnt include SQL injection and  command injection.

### Project reflection

This project took me approximately 2.5 hours including the documentation. The most challenging part was accessing the AWS environment using a different profile. It was most rewarding to be able to display the secret data from the attack.

I did this project as part of my Cloud engineering learning journey.

---

## Project Setup

To set up for this project, I deployed a CloudFormation template that launches web app with 27 resources. The three main components are web app infrastructure, S3 storage and GuardDuty. The Web infrastructure handles the server, networking and cloud front distribution, S3 storage stores sensitive data file while GuardDuty id for security monitoring.

The web app deployed is called OWASP Juice shop. To practice my GuardDuty skills, I will hack the web app and check whether the attack is picked up by the GuardDuty.

GuardDuty is an AWS threat detection service which is used to detect attacks or potential security risks. It uses machine learning to detect unusual activity in the AWS account like network traffic or CloudTrail activity logs. In this project, it will use GuardDuty to detect attack to my web app(OWASP).

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-guardduty_n1o2p3q4)

---

## SQL Injection

The first attack I performed on the web app is SQL injection, which means I inserted malicious SQL code into the database query. SQL injection is a security risk because it can let the attacker bypass authentication, steal data or even change the database structure.

My SQL injection attack involved ' or 1=1;-- as the email. This means the query will always evaluate to true letting me  avoid the authentication check.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-guardduty_h1i2j3k4)

---

## Command Injection

Next, I used command injection, which is a security vulnerability where a web server mistakenly executes a commands where it should have been storing it. The Juice Shop app is vulnerable to this because it has no sanitization protection which blocks or strips out harmful commands or scripts allowing only the harmless intended data to be processed.

To run the command injection, I input malicious code in the username field. The server failed to properly validate the input and treated it as a legitimate code to run. Instead of displaying the whole malicious code as the username it defaults to "[object Object]" which confirms a javascript file has been created as required by the malicious script.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-guardduty_t3u4v5w6)

---

## Attack Verification

To verify the attack's success, I used the web app URL to view the access keys in the javascript file created as the injected command required. The credentials page showed me AccessKeyID and SecretAccessKey which are the main keys for accessing AWS services, Token for extra security during my session, Expiration to show when the credentials stop working, code to show the status of credentials and type to show type of credentials.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-guardduty_x7y8z9a0)

---

## Using CloudShell for Advanced Attacks

The attack continues in CloudShell because AWS assigns the session a temporary AWS account with a different account id then the main one enabling a simulation of two separate accounts efficient for testing this attack.

In CloudShell, I used wget to download the credentials.json file from the web app. Next, I ran a command using cat and jq to display the credentials.json and process the JSON data to make the contents easier to read.

I then set up a profile, called stolen to use credentials stolen from the web app attack. I had to create a new profile because I need to hack into my AWS environment from a different account.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-guardduty_j9k0l1m2)

---

## GuardDuty's Findings

After performing the attack, GuardDuty reported a finding within 15 minutes in my AWS environment. Findings are notifications that tell what attack happened, who did the attack and how they did it

GuardDuty's finding was called "UnauthorizedAccess:IAMUser/InstanceCredentialExfiltration.InsideAWS" which means someone with a different AWS account accessed my EC2 instance despite lacking the proper permissions. Anomaly detection used was because there was an unusual use of my EC2 instance credentials(copying an S3 bucket object) in comparison to the typical use of AWS credentials .

GuardDuty's detailed finding reported that the attacker used an IAM role to access my S3 storage whose data was copied. It also shows the location and IP address of the attacker.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-guardduty_v1w2x3y4)

---

## Extra: Malware Protection

For my project extension, I enabled S3 bucket malware protection. Malware is a type of software that cam harm, steal data and disrupt operations in computers.

To test malware protection, I uploaded a malware EICAR test file. The uploaded file won't actually cause damage because it contains a fake virus that test if the antivirus feature is working correctly without using an actual virus.

Once I uploaded the file, Guard Duty instantly triggered Malware protection of S3 bucket to show finding of Object:S3/MaliciousFile . This verified that GuardDuty can successfully detect malwares.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-security-guardduty_sm42x3y4)

---
