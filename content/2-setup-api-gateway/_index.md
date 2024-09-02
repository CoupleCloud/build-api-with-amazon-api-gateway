+++
title = "SETTING UP API GATEWAY"
date = 2024
weight = 2
chapter = false
pre = "<b>2. </b>"
+++

#### SETTING UP API GATEWAY

#### Overview
In this section, you will learn how to set up **AWS API Gateway** to expose your Lambda function as a REST API. API Gateway allows you to create, deploy, and manage APIs at any scale. This setup will enable your Lambda function to handle HTTP requests and respond to API calls from clients.

#### What is AWS API Gateway?
**AWS API Gateway** is a fully managed service that makes it easy to create, publish, maintain, monitor, and secure APIs. API Gateway acts as an interface between your backend services (such as Lambda functions) and your clients, handling tasks such as request routing, authorization, and traffic management.

#### Setting Up API Gateway

1. **Log in to the AWS Management Console**:
   - Navigate to the [AWS Management Console](https://aws.amazon.com/console/) and log in with your credentials.

2. **Navigate to API Gateway**:
   - In the AWS Management Console, search for and select **API Gateway** from the list of services.

3. **Create a New API**:
   - Click on the **Create API** button.
   - Choose **HTTP API** (for simplicity) or **REST API** (for more advanced features). In this tutorial, we will use **HTTP API**.
  
