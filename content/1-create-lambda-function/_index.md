+++
title = "CREATING A LAMBDA FUNCTION"
date = 2024
weight = 1
chapter = false
pre = "<b>1. </b>"
+++
#### CREATING A LAMBDA FUNCTION

#### Overview
In this section, you will learn how to create an **AWS Lambda function**. AWS Lambda allows you to run code in response to events without provisioning or managing servers. This step is crucial as it will enable you to process the requests that come from your API Gateway.

#### What is AWS Lambda?
**AWS Lambda** is a serverless computing service provided by AWS that executes your code only when needed and scales automatically. It eliminates the need to manage infrastructure, allowing you to focus solely on your code. Lambda functions can be triggered by various AWS services, such as API Gateway, S3, DynamoDB, and more.

#### Creating a Lambda Function

1. **Log in to the AWS Management Console**: Go to the [AWS Management Console](https://aws.amazon.com/console/) and sign in with your credentials.

2. **Navigate to the Lambda Service**: In the AWS Management Console, search for and select **Lambda** from the list of services.

3. **Create a New Lambda Function**:
   - Click the **Create function** button.
   - Choose **Author from scratch**. This option lets you start with a blank function.
   - Enter a name for your function in the **Function name** field. For example, `MyApiLambdaFunction`.
   - Select a runtime for your function from the **Runtime** dropdown. You can choose from various languages such as Node.js, Python, Java, and more.
   - Under **Permissions**, choose **Create a new role with basic Lambda permissions** to allow Lambda to execute your code and write logs to CloudWatch.

4. **Write or Upload Your Code**:
   - In the **Function code** section, you can write your code directly in the inline editor or upload a .zip file containing your code and dependencies.
   - For demonstration, here's a simple Node.js example that returns a "Hello, World!" message:
     ```javascript
     exports.handler = async (event) => {
         return {
             statusCode: 200,
             body: JSON.stringify('Hello, World!'),
         };
     };
     ```

5. **Configure Function Settings**:
   - Set up your function’s **Handler** (for example, `index.handler` for Node.js).
   - Adjust **Memory** and **Timeout** settings as needed, depending on the requirements of your function.

6. **Test Your Lambda Function**:
   - Click the **Test** button to create a test event. Provide a name for the test event and use the default event template.
   - Click **Create** to save the test event and then **Test** to execute your Lambda function. Verify that the output matches your expectations.

7. **Save Your Function**:
   - Click **Deploy** to save your changes.

#### Main Content

1. [Log in to the AWS Management Console](#)
2. [Navigate to the Lambda Service](#)
3. [Create a New Lambda Function](#)
4. [Write or Upload Your Code](#)
5. [Configure Function Se
