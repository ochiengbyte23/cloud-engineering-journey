<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Fetch Data with AWS Lambda

**Project Link:** [View Project](http://nextwork.ai/projects/aws-compute-lambda)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

## Fetch Data with AWS Lambda

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-lambda_p9thryj2)

---

## Introducing Today's Project!

In this project, I will demonstrate how to build a scalable and serverless AWS Lambda function and use it to retrieve data from a Dynamo DB table. I'm doing this project  as the final part of my application architecture series which includes the presentation, logic and data tier.

### Tools and concepts

Services I used were Lambda function, Dynamo DB and IAM role. Key concepts I learnt include Lambda functions, IAM role permission policies and Dynamo DB attribute storage.

### Project reflection

This project took me approximately 1.5 hours including documentation. The most challenging part was writing the JSON permissions policies. It was most rewarding to test my policies and see that they worked as set.

I chose to do this project today because it is the final part of my 3-tier application architecture series which includes presentation, logic and data. 

---

## Project Setup

To set up my project, I created a database using Dynamo DB with "UserData" as the table name . The partition key is "userId" which means I will user id to group similar values together and ease fetching the data.

In my DynamoDB table, I added name and email attribute. DynamoDB is schemaless, which means every item can have  a varying set of attributes making the database very flexible.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-lambda_a112c3d5)

### AWS Lambda

AWS Lambda is is a service that will enable me to run code without having to manage a computer or server. I'm using Lambda in this project to to fetch data from the Dynamo DB table.

---

## AWS Lambda Function

My Lambda function has an execution role, which is an IAM role from my Lambda function. By default, the role grants permission for writing logs to CloudWatch.

My Lambda function will fetch userId as input with its corresponding data from the UserData table. It also handles potential errors during the database operation. .

The code uses AWS SDK, which is a tool with pre-written code that enables AWS service connection without having to manually write code. My code uses SDK to interact with the Dynamo DB.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-lambda_a1b2c3d5)

---

## Function Testing

To test whether my Lambda function works, I clicked the Test tab in my Lambda function. The test is written in JSON format because it is easy for Lambda to understand and work with. If the test is successful, I'd see data related to the userId attribute which is the partition key.

The test displayed a 'success' because the function could successfully run but the function's response was actually contained an access denied error because the default IAM role created with Lambda only has access permission to AWS CloudWatch for log recording. The Lambda has no permission from the IAM role to access the Dynamo DB hence the denied access.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-lambda_u1v2w3x4)

---

## Function Permissions

To resolve the AccessDenied error I will review the error to see which permission the Lambda function lacks because it helps me to be specific about which permission I need to add to resolve the error.

There were four DynamoDB permission policies I could choose from, but I didn't pick AWSLambdaDynamoDBExecutionRole and AWSLambdaInvocation-DynamoDB because their actions are outside the range of what permissionI need to resolve my GetItem error.

I also didn't pick AmazonDynamoDBFullAccess because it lets me do mo that read the data in Dynamo DB and this can make my service less secure since I will only be reading the data. AmazonDynamoDBReadOnlyAccess was the right choice because it is very specific to my requirement which is only to read data in Dynamo DB.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-lambda_3ethryj2)

---

## Final Testing and Reflection

To validate my new permission settings, I reran the test to fetch data from Dynamo DB. The results were attributes and values from the table successfully returned because the IAM role created by Lambda function now had the permission to access the Dynamo DB.

Web apps are a popular use case of using Lambda and DynamoDB. For example, I could use Lambda in helping customers find products or order history from Dynamo DB, help social media users retrieve content linked with a profile and help blogs fetch articles based on user queries among other uses.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-lambda_p9thryj2)

---

## Enahancing Security

For my project extension, I challenged myself to replace AmazonDynamoDBReadOnlyAccess policy with a more granular inline policy . This will my database more secure since AmazonDynamoDBReadOnlyAccess still had some permissions I was not using.

To create the permission policy, I used JSON format because it provides a direct access compared to the visual editor.

When updating a Lambda function's permission policies, you could risk a possibility of it not working as intended. I validated that my Lambda function still works by going back to my Lambda function's Test tab and running the test again successfully.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-lambda_1qthryj2)

---

---
