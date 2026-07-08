<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Query Data with DynamoDB

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-databases-query)

**Author:** Bildad Masaga  
**Email:** bijasoto@gmail.com

---

## Query Data with DynamoDB

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-databases-query_733d9399)

---

## Introducing Today's Project!

### What is Amazon DynamoDB?

Amazon DynamoDB is a non-relational database which stores items with different attributes. It is useful due to its flexibility since items are able to have varying attributes and its speed since it uses of partition keys which splits the table when searching for data.

### How I used Amazon DynamoDB in this project

In today's project, I used Amazon DynamoDB to to query the database and handle transactional operations.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project is the lack of transaction option using the console like the AWS CloudShell.

### This project took me...

This project took me 1 hour including the documentation.

---

## Querying DynamoDB Tables

A partition key is used to split the DynamoDB table to find a value.

A sort key is a secondary key used to filter through a DynamoDB table again after the partition key. Sort keys are optional.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-databases-query_d105b0b0)

---

## Limits of Using DynamoDB

I ran into an error when I queried for all comments posted by "User Abdulrahman". This was because the data modelling for the table makes it essential for a partition key to be available during any query which my query lacked.

Insights we could extract from our Comment table includes comments left on a post, comment made by a specific user and sort comments be time and date. Insights we can't easily extract from the Comment table includes all comments made by a specific user.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-databases-query_cb3e260c)

---

## Running Queries with CLI

A query I ran in CloudShell was "aws dynamodb get-item". This query will get a single item from the table based on my table, key and other specifications.

Query options I could add to my query are "--consistent-read" which provides the most recent version of the item, "--projection-expression" if i need only some attributes and "returned-consumed-capacity" if i want to know how much capacity was consumed by my request.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-databases-query_733d9399)

---

## Transactions

A transaction is a group of operations that all have to succeed for a command to be implemented. If any operation fails none of the changes is applied.

I ran a transaction using "aws dynamodb transact-write -item".  This transaction did two things that is update the Forum and Comment tables.

![Image](http://learn.nextwork.org/loving_rose_daring_rose_apple/uploads/aws-databases-query_2f65f83e)

---

---
