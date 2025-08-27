# AWS Lambda Monitoring and Secure Logging Setup

This repository demonstrates deploying a basic AWS Lambda function monitored by AWS CloudWatch, along with implementing a secure IAM policy for safe logging practices.

---

## Table of Contents

- [Lambda CloudWatch Monitoring](#lambda-cloudwatch-monitoring)
- [IAM Policy for Secure CloudWatch Logging](#iam-policy-for-secure-cloudwatch-logging)
- [Deploying and Testing](#deploying-and-testing)
- [Summary](#summary)
- [References](#references)

---

## Lambda CloudWatch Monitoring

- A basic AWS Lambda function is created to log output to CloudWatch Logs.
- The function automatically publishes key metrics such as Invocations, Duration, and Errors.
- CloudWatch Dashboard widgets are configured to visualize these real-time metrics including error counts.
- Errors can be simulated in the function code for testing and monitoring purposes.

---

## IAM Policy for Secure CloudWatch Logging

To allow your Lambda function to write logs securely to CloudWatch, attach the following **least privilege** IAM policy to the Lambda execution role:

{
"Version": "2012-10-17",
"Statement": [
{
"Effect": "Allow",
"Action": [
"logs:CreateLogGroup",
"logs:CreateLogStream",
"logs:PutLogEvents"
],
"Resource": "arn:aws:logs:::*"
}
]
}

- This policy permits creation of log groups and streams, and sending log events.
- It adheres to AWS best practices for minimum required permissions.

---

## Deploying and Testing

1. Deploy the Lambda function through AWS Console.
2. Attach the above IAM logging policy to the Lambda execution role.
3. Invoke the Lambda manually or via test events.
4. View logs and metrics in CloudWatch Console and dashboards.
5. Modify the Lambda function to throw errors to verify error metric tracking.

---

## Summary

This project highlights:

- Simple Lambda functions monitored automatically by AWS CloudWatch.
- Use of IAM policies to secure log writing with least privilege.
- Building effective dashboards and simulating error conditions for monitoring validation.

---

## References

- [AWS Lambda Monitoring with CloudWatch](https://docs.aws.amazon.com/lambda/latest/dg/monitoring-cloudwatchlogs.html)
- [IAM policies for CloudWatch logging](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/iam-identity-based-access-control-cwl.html)
- [AWS Lambda Execution Role Best Practices](https://docs.aws.amazon.com/lambda/latest/dg/lambda-intro-execution-role.html)

---


