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

![Image](../../images/1-create-lambda-function/0_overview.png?width=300pc)

2. **Navigate to the Lambda Service**: In the AWS Management Console, search for and select **Lambda** from the list of services.

![Image](../../images/1-create-lambda-function/1_lambda.png?width=300pc)

3. **Create a New Lambda Function**:
   - Click the **Create function** button.
   - Choose **Author from scratch**. This option lets you start with a blank function.
   - Enter a name for your function in the **Function name** field. For example, `MyApiLambdaFunction`.
   - Select a runtime for your function from the **Runtime** dropdown. You can choose from various languages such as Node.js, Python, Java, and more.
   - Under **Permissions**, choose **Create a new role with basic Lambda permissions** to allow Lambda to execute your code and write logs to CloudWatch.

![Image](../../images/1-create-lambda-function/1_create_function.png?width=300pc)

4. **Write or Upload Your Code**:
   - In the **Function code** section, you should see the code editor where you can edit your Lambda function's code.
   - If the **index.mjs** tab is not visible in the code editor, select it from the file explorer. This file contains the code for your Lambda function.

   ![Image](../../images/1-create-lambda-function/1_index.mjs.png?width=300pc)

   - Paste the following code into the **index.mjs** tab, replacing any existing code:
     ```javascript
     export const handler = async (event, context) => {
       
       const length = event.length;
       const width = event.width;
       let area = calculateArea(length, width);
       console.log(`The area is ${area}`);
         
       console.log('CloudWatch log group: ', context.logGroupName);
       
       let data = {
         "area": area,
       };
       return JSON.stringify(data);
       
       function calculateArea(length, width) {
         return length * width;
       }
     };
     ```
   - Click **Deploy** to update your function's code. Once Lambda has successfully deployed the changes, you will see a banner confirming that your function has been updated.

5. **Configure Function Settings**:
   - Set up your function’s **Handler** (for example, `index.handler` for Node.js).
   - Adjust **Memory** and **Timeout** settings as needed, depending on the requirements of your function.

6. **Test Your Lambda Function**:
   - To invoke your Lambda function using the console, you first need to create a test event:
     1. In the **Code source** pane of the Lambda console, click **Test**.
     2. Select **Create new event**.
     3. For **Event name**, enter `myTestEvent`.
     4. In the **Event JSON** panel, replace the default values with the following:
        ```json
        {
          "length": 6,
          "width": 7
        }
        ```
     5. Click **Save** to create the test event.

   - To run the test and view the results:
     1. In the **Code source** pane, click **Test** again.
     2. After the function executes, you will see the response and logs displayed in the **Execution results** tab. The expected results should be similar to:
        ```
        Test Event Name: myTestEvent

        Response:
        "{\"area\":42}"

        Function Logs:
        START RequestId: 5c012b0a-18f7-4805-b2f6-40912935034a Version: $LATEST
        2023-08-31T23:39:45.313Z 5c012b0a-18f7-4805-b2f6-40912935034a INFO The area is 42
        2023-08-31T23:39:45.331Z 5c012b0a-18f7-4805-b2f6-40912935034a INFO CloudWatch log group: /aws/lambda/myLambdaFunction
        END RequestId: 5c012b0a-18f7-4805-b2f6-40912935034a
        REPORT RequestId: 5c012b0a-18f7-4805-b2f6-40912935034a Duration: 20.67 ms Billed Duration: 21 ms Memory Size: 128 MB Max Memory Used: 66 MB Init Duration: 163.87 ms
        ```

   - To view the invocation records in **CloudWatch Logs**:
     1. Open the **Log groups** page of the CloudWatch console.
     2. Select the log group for your function, which is `/aws/lambda/myLambdaFunction`.
     3. In the **Log streams** tab, choose the log stream corresponding to your function's invocation.
     4. You should see output similar to:
        ```
        INIT_START Runtime Version: nodejs:20.v13 Runtime Version ARN: arn:aws:lambda:us-west-2::runtime:e3aaabf6b92ef8755eaae2f4bfdcb7eb8c4536a5e044900570a42bdba7b869d9
        START RequestId: aba6c0fc-cf99-49d7-a77d-26d805dacd20 Version: $LATEST
        2023-08-23T22:04:15.809Z 5c012b0a-18f7-4805-b2f6-40912935034a INFO The area is 42
        2023-08-23T22:04:15.810Z aba6c0fc-cf99-49d7-a77d-26d805dacd20 INFO CloudWatch log group: /aws/lambda/myLambdaFunction
        END RequestId: aba6c0fc-cf99-49d7-a77d-26d805dacd20
        REPORT RequestId: aba6c0fc-cf99-49d7-a77d-26d805dacd20 Duration: 17.77 ms Billed Duration: 18 ms Memory Size: 128 MB Max Memory Used: 67 MB Init Duration: 178.85 ms
        ```

In this process, you create a test event, execute the function, and verify the output both in the Lambda console and CloudWatch Logs.


7. **Save Your Function**:
   - Click **Deploy** to save your changes.

