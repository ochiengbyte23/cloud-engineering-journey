<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Load Data into DynamoDB

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-databases-dynamodb)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

## Load Data into a DynamoDB Table

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-databases-dynamodb_b481c730)

---

## Introducing Today's Project!

### What is Amazon DynamoDB?

Amazon DynamoDB is a non-relational database that is preferred when flexibility is a priority since each item in the database can have a unique attribute. It also improves performance speed using partition keys which split the table to find an item instead of searching through the whole table.

### How I used Amazon DynamoDB in this project

In today's project, I used Amazon DynamoDB to create a non-relational database from scratch, load data into it both manually  and through the AWS CloudShell using AWS CLI.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project is how accessible the database would be in the AWS console.

### This project took me...

This project took me 1 hours to complete including the documentation.

---

## Create a DynamoDB table

DynamoDB tables organises data using lists of items each with their own attributes. Each item in the list can have a different attribute.

An attribute is a piece of data about an item. In DynamoDB each item can have its unique set of attributes.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-databases-dynamodb_a3cefee0)

---

## Read and Write Capacity

Read capacity units (RCUs) and write capacity units (WCUs) are a way to measure how many engines the DynamoDB is using.

Amazon DynamoDB's Free Tier covers 25GB of data storage meaning 25 RCU and WCU which is enough to cover 200 requests per month. I turned off auto scaling because it maintains low cost settings as the auto scaling can push Dynamo DB beyond the free tier limit if not monitored.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-databases-dynamodb_ef47dd8f)

---

## Using CLI and CloudShell

AWS CloudShell is a space to run code using AWS CLI.

AWS CLI is a software that lets you create, delete and update resources using commands instead of clicking through the console.

I ran a CLI command in AWS CloudShell that created 4 new tables in AWS DynamoDB each with specific sttribute and setting. The tables are Catalog Table, Forum Table,Post Table, Comment Table.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-databases-dynamodb_81e0258b)

---

## Loading Data with CLI

I ran a CLI command(batch-write-item) in AWS CloudShell that loaded and inserted multiple items in the DynamoDB tables.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-databases-dynamodb_791c600b)

---

## Observing Item Attributes

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-databases-dynamodb_b481c731)

I checked a ContentCatalog item, which had the following attributes: Authors, ContentType, Difficulty, Price, ProjectCategory, Title, and URL.

I checked another ContentCatalog item, which had a different set of attributes: ContentType, Price, Services, Title, URL, Videoype. 

---

## Benefits of DynamoDB

A benefit of DynamoDB over relational databases is flexibility, because each item can have its own unique set of attributes unlike relational databases where all items would require uniform columns even if they do not apply.

Another benefit over relational databases is speed, because DynamoDB can use partition keys to filter a table and quickly search for an item. Relational database on the other hand have to scan the entire table which can be slow.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-databases-dynamodb_b481c730)

---

---
