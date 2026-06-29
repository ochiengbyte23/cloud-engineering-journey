<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Security Monitoring System

**Project Link:** [View Project](http://nextwork.ai/projects/aws-security-monitoring)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-security-monitoring_reghtjy)

---

## Introducing Today's Project!

In this project, I will demonstrate how to track if my secrets have been accessed in secret manager, record logs and send notifications to notify me. I'm doing this project to learn to learn more about cloud security as part of my cloud engineering journey.

### Tools and concepts

Services I used were CloudTrail, CloudWatch, S3, Simple Notification Service(SNS) and Secret Manager. Key concepts I learnt include secret storage, CloudWatch vs CloudTrail and their notifications and  CloudWatch alarm filtering.

### Project reflection

This project took me approximately. 3 hours. The most challenging part was troubleshooting to check why I was not receiving the email notification. It was most rewarding to be able to compare CloudTrail and CloudWatch notifications method and see why one might be better than the other depending on the requirements.

---

## Create a Secret

Secrets Manager is an AWS service for storing secrets which could be passwords, API keys, credentials or just any sensitive information. You could use Secrets Manager to safely access secrets in my code without revealing them.

To set up for my project, I created a secret called 'TopSecretInfo' that contains a hot take from me: rice is the best carb.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-security-monitoring_o5p6q7r8)

---

## Set Up CloudTrail

CloudTrail is a service used to monitor activity throughout an AWS account. I set up a trail to monitor the access to my secrets in Secret Manager.

CloudTrail events include types like management events which track configuration and creation activities , data events which track actions ON my events, insight events for unusual activities and network activity events for network related patterns.

### Read vs Write Activity

Read API activity involves viewing without changing anything. Write API activity involves actual changes being made. For this project, we need to use 'write API activity' for the secret trail log so that any viewing of secrets is treated with caution as much as changing it.

---

## Verifying CloudTrail

I retrieved the secret in two ways: First through through clicking in the AWS console. Second using the command 'aws secretsmanager get-secret-value --secret-id "TopSecretInfo" --region af-south-1'.

To analyze my CloudTrail events, I visited Event History in the CloudTrail console. I found 'GetSecretValue' events using the Event Source attribute filter. This tells me my actions to access the secret in Secret Manager were successfully recorded by CloudTrail.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-security-monitoring_s8t9u0v1)

---

## CloudWatch Metrics

CloudWatch Logs is a service that brings together logs from different AWS services like CloudTrail for visibility, analysis and troubleshooting. It's important for monitoring because it can create alert based on a specific pattern, visualise trends or trigger automated responses.

CloudTrail's Event History is useful for brief overview on recent events while CloudWatch Logs are better for a detailed overview, longer storage, powerful log filtering, and creating alerts and automated responses.

A CloudWatch metric is used to filter logs based on specific patterns. When setting up a metric, the metric value represents how many times the metric counter is increased with access . Default value is used when the metric was unused to give the complete picture instead of just completely omitting it.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-security-monitoring_a9b0c1d2)

---

## CloudWatch Alarm

A CloudWatch alarm is a notification sent when a specific metric is triggered. I set my CloudWatch alarm threshold to 1 minutes so the alarm will trigger when the metric is greater than or equal to 1 in a 5 minute period .

I created an SNS topic along the way. An SNS topic is like a broadcast channel with subscribers who can receive messages through emails, phone numbers and apps. My SNS topic is set up to send an email when my secret is accessed.

AWS requires email confirmation because it needs to confirm if I want to really receive the alarm notifications. This helps prevent receiving unwanted messages.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-security-monitoring_fsdghstt)

---

## Troubleshooting Notification Errors

To test my monitoring system, I accessed the secret in Secret Manager. The results were unsuccessful. I  expected to receive an email notification about this access. 

When troubleshooting the notification issues I checked for CloudTrail  to see if the "GetSecretValue event" was being recorded in EventHistory, CloudTrail to confirm if it was sending sending logs to CloudWatch, CloudWatch's metric filter  to confirm it is filtering logs correctly, CloudWatch's Alarm to check if it was triggering an action and SNS to check if it wasn't delivering emails to me.

I initially didn't receive an email before because  CloudWatch's alarm statistics was set to an average rate which was not being met . The key solution was changing the statistics to sum.

---

## Success!

To validate that the monitoring system can successfully detect an alert when my secret is accessed I checked my secrets value one more time. I received an email with 1-3 minutes of the event. The alarm in CloudWatch is also in alarm state.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-security-monitoring_ageraergearge)

---

## Comparing CloudWatch with CloudTrail Notifications

In a project extension, I will configure direct SNS notification from CloudTrail and compare with the notification method in CloudWatch because it helps me understand architecture decisions when building cloud solutions..

After enabling CloudTrail SNS notifications, my inbox was flooded with new emails. In terms of the usefulness of these emails, I thought I was receiving too much emails with vague logs which only show new logs being stored in the bucket.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-security-monitoring_d7e8f9g0)

---

---
