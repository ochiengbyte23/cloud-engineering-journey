<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# APIs with Lambda + API Gateway

**Project Link:** [View Project](http://nextwork.ai/projects/aws-compute-api)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-api_c9d0e1f2)

---

## Introducing Today's Project!

In this project, I will demonstrate how to develop a serverless Lambda function, configure an API gateway, connect the Lambda with API gateway and write a JSON documentation for my API. I'm doing this project to learn about the logic part of application architecture as part of a three part series(presentation, logic data).

### Tools and concepts

Services I used were Lambda function and API Gateway. Key concepts I learnt include Lambda functions, API resources, API Gateway and deployment, and API documentation.

### Project reflection

This project took me approximately 1.5 hour including the documentation and demo. The most challenging part was understanding the Lambda function code. It was most rewarding to create resources and methods.

I chose to do this project today because as the second part of my three part application architecture series. 

---

## Lambda functions

AWS Lambda is an AWS service that lets you run code without the need to manage any computers or servers. I'm using Lambda in this project to retrieve data from a database and to also learn how to configure it.

The code I added to my function will retrieve data from a DynamoDB table based on 'userID'. I f there is an error or the data does not exist in the table it returns an error.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-api_a1b2c3d5)

---

## API Gateway

APIs are means of communication between software systems. There are different types of APIs, like REST, WebSocket and HTTP. My API is REST API which uses HTTP methods to interact with resources.

Amazon API Gateway is an AWS service used to create, publish, maintain, monitor and secure APS's at any scale. I'm using API Gateway in this project to communicate with the Lambda function.

When a user makes a request it is received by an API gateway which authenticates and authorises the request before forwarding it to Lambda function for processing. Processed requests are sent back to the user through the API gateway again.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-api_m3n4o5p6)

---

## API Resources and Methods

An API is made up of resources, which are individual endpoints of the API that handle parts of its functionality.

Each resource consists of methods, which are actions that can be performed on a resource. Methods are based on standard HTTP methods which are GET, PUT, POST and DELETE.

I created a GET method for my API gateway and integrated it with my Lambda function.  I will use it in my /users resource to retrieve data from my database.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-api_c9d0e1f2)

---

## API Deployment

When you deploy an API, you deploy it to a specific stage. A stage is a snapshot of the API at a specific point. I deployed to production stage where the API ids fully working in a live environment.

To visit my API, I opened the invoke URL from the prod stage console in a new tab in my browser. The API displayed an error because I have not yet connected up a DynamoDB to the API .

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-api_3ethryj2)

---

## API Documentation

For my project's extension, I am writing API documentation because it describes the API's functionality including its endpoints, methods, parameters and responses. You can do this in the API Gateway console in AWS.

Once I prepared my documentation, I can publish it to external tools like Swagger UI and ReDoc to generate interactive web pages about my API where other developers can explore it. You have to publish your API to a specific stage because the documentation need to be consistent with API version deployed at that stage.

My published and downloaded documentation showed me. my API's version, tittle, resources with their paths and methods.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-api_z9a0b1c2)

---

---
