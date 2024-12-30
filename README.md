Step-by-Step Guide to Building Blog/Book Audio Converter using AWS Polly

Project Description:
The Blog/Book Narrator project leverages AWS services to convert text files (such as blog posts, articles, newsletters, or book excerpts) into speech. This is particularly useful for creating audio versions of written content, making it accessible to a wider audience, including those who prefer listening over reading.

Use Cases:

Content Accessibility: Provides audio versions of written content for visually impaired users.
Learning: Enables users to listen to educational materials, enhancing learning experiences.
Content Distribution: Offers an additional medium for content consumption, increasing engagement.
Convenience: Allows users to listen to articles or books while multitasking, such as during commutes or workouts.

Project Architecture:


<img width="1104" alt="340108899-5c799fd1-d4d7-4eae-923a-2b8320678463" src="https://github.com/user-attachments/assets/bf676b3b-234c-412b-ab5f-9518322b293b" />












Steps to Build the Project:
Step 1: Set Up an AWS Account

Step 2: Create two S3 Buckets (Source S3 Bucket Name: amc-polly-source-bucket-11, Destination S3 Bucket Name: amc-polly-destination-bucket-11)

Step 3: Create an IAM Policy (IAM Policy Name: amc-polly-lambda-policy-11)
Policy Defination:

{
  "Version": "2012-10-17",
  "Statement": [
      {
          "Effect": "Allow",
          "Action": [
              "s3:GetObject",
              "s3:PutObject"
          ],
          "Resource": [
              "arn:aws:s3:::amc-polly-source-bucket/*",
              "arn:aws:s3:::amc-polly-destination-bucket/*"
          ]
      },
      {
          "Effect": "Allow",
          "Action": [
              "polly:SynthesizeSpeech"
          ],
          "Resource": "*"
      }
  ]
}


   
Step 4: Create an IAM Role (IAM Role Name: amc-polly-lambda-role-12) and attach amc-polly-lambda-policy and AWSLambdaBasicExecutionRole Policies

Step 5: Create and Configure the Lambda Function (Lambda Function Name: TextToSpeechFunction)

Set the runtime to Python 3.8.
Set the execution role with necessary permissions for S3 and Polly. (Step 4)
Add Environment Variables (SOURCE_BUCKET: Name of your source S3 bucket and DESTINATION_BUCKET: Name of your destination S3 bucket.
Step 6: Configure S3 Event Notification

Set up an event notification in the source S3 bucket to trigger the Lambda function on new object creation events with the .txt suffix.
Step 7: Write Lambda Function Code

Step 8: Test the System

