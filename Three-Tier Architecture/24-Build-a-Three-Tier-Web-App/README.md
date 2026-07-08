<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Three-Tier Web App

**Project Link:** [View Project](http://nextwork.ai/projects/aws-compute-threetier)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

## Build a Three-Tier Web App

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-threetier_2b3c4d5e)

---

## Introducing Today's Project!

In this project, I will demonstrate how to create a bucket storage for my website with S3, distributes the website's content globally with CloudFront, use a serverless function with Lambda, create an API to handle all the requests with an API Gateway, store and retrieve data with DynamoDB , and connect all these services together. I'm doing this project to learn about the three tier architecture of an application which includes presentation, logic and data.

### Tools and concepts

Services I used were Amazon S3 for frontend hosting, CloudFront for CDN routing, API Gateway, Lambda for serverless backend execution, and DynamoDB for database storage. Key concepts I learnt include building a secure three-tier architecture, restricting bucket access with OAC, and configuring CORS headers manually in Python since API Gateway was set up with Lambda Proxy Integration. This hands-on integration of presentation, logic, and data tiers taught me how modern serverless cloud applications securely communicate.

### Project reflection

This project took me approximately 2.5 hours including the documentation. The most challenging part was updating the cache to make sure my changes were deployed. It was most rewarding to. fetch data from the database using the CloudFront URL

I chose to do this project today because it was part of the application architecture plan which is in line with my cloud engineering journey. 

---

## Presentation tier

For the presentation tier, I will set up an S3 bucket storage and fill it with an html file before distributing it globally with CloudFront because it completes the presentation layer of the application.

I accessed my delivered website by updating my S3 bucket policy to allow requests from CloudFront and testing the distribution domain name in the browser successfully.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-threetier_3a4b5c6d)

---

## Logic tier

For the logic tier, I will set up a Lambda function to retrieve data from a DynamoDB table, write code for the Lambda function, Create an API Gateway REST API, create a resource and method to handle GET requests and deploy the API to make it accessible because it completes the logic layer of my web app.

The Lambda function retrieves data by triggering events in the code such as a HTTP request. The code is executed in the runtime environment picked which in this case is the Node.js.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-threetier_6a7b8c9d)

---

## Data tier

For the data tier, I will set up a DynamoDB table and add data into it because completes the data layer of the web app architecture.

The partition key for my DynamoDB table is userId which means data will be fetched based on userId and all data related to the specific id will be returned.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-threetier_u1v2w3x4)

---

## Logic and Data tier

Once all three layers of my three-tier architecture are set up, the next step is to intergrate them by first updating my javascript code in the presentation layer to accept API requests because it will enable me to confirm that the presentation, logic and data layers can all communicate successfully.

To test my API, I sent request "https://lrx83xqxx0.execute-api.af-south-1.amazonaws.com/prod/users?userId=1" through my browser. The results were all the data related to userId: 1. This confirmed that my logic and data tier were successfully integrated

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-threetier_a112c3d5)

---

## Console Errors

The CloudFront distributed website failed to fetch user data because the JavaScript in script.js was pointing to a placeholder '[YOUR-PROD-API-URL]' on line 9. To fix this, I need to replace the placeholder with the real API Gateway Invoke URL so the presentation tier can successfully communicate with our backend Lambda functio

To resolve the error, I updated script.js by relacing the placeholder URL with the actual API Gateway URL. I then reuploaded it into S3 because it will now resolve the error caused by the file initially in the S3 which had the placeholder API URL.

I ran into a second error because of browser-side CORS security. The browser blocked my website (hosted on CloudFront) from sending request traffic to API Gateway because the API has not been configured to trust or allow requests from my CloudFront domain.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-threetier_a1b2c3d5)

---

## Resolving CORS Errors

To resolve the CORS error, I first clicked on the enable CORS in the API resource , I then allowed GET method and OPTION(use by the browser to do a pre-check of the CORS setting) method in the Access-Control-Allow-Methods. configuration. Before saving the seeting I input the CloudFront distribution domain in the  Access-Control-Allow-Origin configuration to allow requests from the CloudFront domain to my API.

I also updated my Lambda function because it lacked the code to process CORS header with incoming API requests from CloudFront. The changes I made were adding "'Access-Control-Allow-Origin':'https://d1gj4bay5l11y.cloudfront.net'" which allows the CloudFront request to be processed by Lambda.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-threetier_1qthryj2)

---

## Fixed Solution

I verified the fixed connection between API Gateway and CloudFront by opening my live CloudFront URL, entering a User ID, and clicking 'Get User Data', the frontend successfully bypassed CORS restrictions because the browser received the necessary access headers. The user data from my DynamoDB database loaded instantly on the screen, and my browser developer console remained completely clean with zero 403 Forbidden or CORS errors.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-compute-threetier_2b3c4d5e)

---

---
