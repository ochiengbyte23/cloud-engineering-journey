<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Website Delivery with CloudFront

**Project Link:** [View Project](http://nextwork.ai/projects/aws-networks-cloudfront)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

## Website Delivery with CloudFront

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-networks-cloudfront_1dddddwe)

---

## Introducing Today's Project!

In this project, I will demonstrate how to set up a website globally using S3 and  CloudFront. I'm doing this project to learn about the three tier architecture series of an application which includes presentation, logic and data. Today's project focuses on presentation.

### Tools and concepts

Services I used were AWS CloudFront and S3. Key concepts I learnt include content delivery network (CDN), distributions, Origin Access Control, Load times and, Webhosting using both S3 and CloudFront.

### Project reflection

This project took me approximately 1.5 hours including documentation and demo. The most challenging part was understanding Origin Access Control(OAC). It was most rewarding to compare performance load time between CloudFront and S3. 

I chose to do this project today because as part 3 part application architecture with a focus on the first part which is presentation. 

---

## Set Up S3 and Website Files

I started the project by creating an S3 bucket to store the files that make up my website. I can't use CloudFront for this task because it simply a content delivery network that hosts content stored somewhere else which in this case is the S3 bucket.

The three files that make up my website are index.html, which organises the contents of the website. style.css, which controls visual elements of the HTML and script.js, which adds interaction to the website.

I validated that my website files work by opening the HTML file in the browser and viewed the webpage.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-networks-cloudfront_qgo7wcd3)

---

## Exploring Amazon CloudFront

Amazon CloudFront is a content delivery network, which means it speeds up the distribution of static and dynamic web content. Businesses and developers use CloudFront because it caches the website content in multiple servers all over the world which causes low latency.

To use Amazon CloudFront, you set up distributions, which are instructions that tell CloudFront how to deliver the website content such as storage, caching and security settings . I set up a distribution for my static webpage. The origin is S3.

My CloudFront distribution's default root object is index.html. This means contents in the index.html file will be displayed first by default when the webpage is opened.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-networks-cloudfront_qgo7wcdt)

---

## Handling Access Issues

When I tried visiting my distributed website, I expected to run into an access denied error because it is in the tutorial but due a new AWS update the Origin Access Control (OAC) settings were automatically configured .

My distribution's origin access settings were set to public while the S3 storage was still private. This was supposed to cause the access denied error but it did not because my settings were automatically configured to use Origin access control settings (recommended) by the simplified AWS wizard

To resolve the error, I set up origin access control (OAC). OAC is a special user for CloudFront that allows access to a private S3 bucket and gives control of how the content is accessed.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-networks-cloudfront_egrhntyu)

---

## Updating S3 Permissions

Once I set up my OAC, I still needed to update my bucket policy because it still needs to explicitly allow OAC to access the bucket content.

Creating an OAC automatically gives me a policy I could copy, which grants CloudFront service principle permission to perform the "s3:GetObject" action on my bucket.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-networks-cloudfront_eg98ntyu)

---

## S3 vs CloudFront for Hosting

For my project extension, I'm comparing S3's static web hosting to CloudFront. I initially had an error with static website hosting because my bucket policy is private and set to allow only CloudFront access at the moment.

I tried resolving this by unblocking all public access. I still ran into an error because I only unblocked traffic to S3 but the permission to access the files using S3 hosting is still disabled .

I could finally see my S3 hosted website when I refreshed my page. This worked because I changed my bucket policy to allow all public access to my files.

Compared to the permission settings for my CloudFront distribution, using S3 meant giving up my security feature which blocks public access. I preferred to use CloudFront because I could access my S3 while still keeping my bucket private.

---

## S3 vs CloudFront Load Times

Load time means how fast the website content loads. The load times for the CloudFront site were faster than the S3 site because it is distributed globally through caching enabling the user to receive the data from the nearest server unlike S3 which draws files from a single region.

A business would prefer CloudFront when handling users from multiple locations since the data is cached in multiple servers in different regions. S3 static website hosting might be sufficient when only users from one particular region use the website.

![Image](http://nextwork.ai/loving_rose_daring_rose_apple/uploads/aws-networks-cloudfront_12verpuh)

---

---
