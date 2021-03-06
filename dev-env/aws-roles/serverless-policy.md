# IAM Policy for Serverless Framework Deployment

Serverless Framework deploys using the policy attached to the IAM credentials in your AWS CLI profile.

[Read the document from serverless-slack.com](https://serverless-stack.com/#table-of-contents)

## The permissions required can be categorized into the following areas:

1. Permissions required by Serverless Framework
2. Permissions required by your Serverless Framework plugins
3. Permissions required by your Lambda code

Granting AdministratorAccess policy ensures that your project will always have the necessary permissions. But if you want to create an IAM policy that grants the minimal set of permissions, you need to customize your IAM policy.

### A basic serverless project needs permissions to the following AWS services:

1. CloudFormation to create change set and update stack
2. S3 to upload and store serverless artifacts and Lambda source code
3. CloudWatch Logs to store Lambda execution logs
4. IAM to manage policies for the Lambda IAM Role
5. API Gateway to manage API endpoints
6. Lambda to manage Lambda functions
7. EC2 to execute Lambda in VPC
8. CloudWatch Events to manage CloudWatch event triggers

### A simple IAM Policy. We can attach this policy to the IAM user

``` json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "cloudformation:*",
        "s3:*",
        "logs:*",
        "iam:*",
        "apigateway:*",
        "lambda:*",
        "ec2:DescribeSecurityGroups",
        "ec2:DescribeSubnets",
        "ec2:DescribeVpcs",
        "events:*"
      ],
      "Resource": [
        "*"
      ]
    }
  ]
}
```

### An advanced IAM Policy
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "cloudformation:Describe*",
        "cloudformation:List*",
        "cloudformation:Get*",
        "cloudformation:CreateStack",
        "cloudformation:UpdateStack",
        "cloudformation:DeleteStack"
      ],
      "Resource": "arn:aws:cloudformation:<region>:<account_no>:stack/<service_name>*/*"
    },
    {
      "Effect": "Allow",
      "Action": [
        "cloudformation:ValidateTemplate"
      ],
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": [
        "s3:CreateBucket",
        "s3:DeleteBucket",
        "s3:Get*",
        "s3:List*"
      ],
      "Resource": [
        "arn:aws:s3:::<service_name>*"
      ]
    },
    {
      "Effect": "Allow",
      "Action": [
        "s3:*"
      ],
      "Resource": [
        "arn:aws:s3:::<service_name>*/*"
      ]
    },
    {
      "Effect": "Allow",
      "Action": [
        "logs:DescribeLogGroups"
      ],
      "Resource": "arn:aws:logs:<region>:<account_no>:log-group::log-stream:*"
    },
    {
      "Action": [
        "logs:CreateLogGroup",
        "logs:CreateLogStream",
        "logs:DeleteLogGroup",
        "logs:DeleteLogStream",
        "logs:DescribeLogStreams",
        "logs:FilterLogEvents"
      ],
      "Resource": "arn:aws:logs:<region>:<account_no>:log-group:/aws/lambda/<service_name>*:log-stream:*",
      "Effect": "Allow"
    },
    {
      "Effect": "Allow",
      "Action": [
        "iam:GetRole",
        "iam:PassRole",
        "iam:CreateRole",
        "iam:DeleteRole",
        "iam:DetachRolePolicy",
        "iam:PutRolePolicy",
        "iam:AttachRolePolicy",
        "iam:DeleteRolePolicy"
      ],
      "Resource": [
        "arn:aws:iam::<account_no>:role/<service_name>*-lambdaRole"
      ]
    },
    {
      "Effect": "Allow",
      "Action": [
        "apigateway:GET",
        "apigateway:PATCH",
        "apigateway:POST",
        "apigateway:PUT",
        "apigateway:DELETE"
      ],
      "Resource": [
        "arn:aws:apigateway:<region>::/restapis"
      ]
    },
    {
      "Effect": "Allow",
      "Action": [
        "apigateway:GET",
        "apigateway:PATCH",
        "apigateway:POST",
        "apigateway:PUT",
        "apigateway:DELETE"
      ],
      "Resource": [
        "arn:aws:apigateway:<region>::/restapis/*"
      ]
    },
    {
      "Effect": "Allow",
      "Action": [
        "lambda:GetFunction",
        "lambda:CreateFunction",
        "lambda:DeleteFunction",
        "lambda:UpdateFunctionConfiguration",
        "lambda:UpdateFunctionCode",
        "lambda:ListVersionsByFunction",
        "lambda:PublishVersion",
        "lambda:CreateAlias",
        "lambda:DeleteAlias",
        "lambda:UpdateAlias",
        "lambda:GetFunctionConfiguration",
        "lambda:AddPermission",
        "lambda:RemovePermission",
        "lambda:InvokeFunction"
      ],
      "Resource": [
        "arn:aws:lambda:*:<account_no>:function:<service_name>*"
      ]
    },
    {
      "Effect": "Allow",
      "Action": [
        "ec2:DescribeSecurityGroups",
        "ec2:DescribeSubnets",
        "ec2:DescribeVpcs"
      ],
      "Resource": [
        "*"
      ]
    },
    {
      "Effect": "Allow",
      "Action": [
        "events:Put*",
        "events:Remove*",
        "events:Delete*",
        "events:Describe*"
      ],
      "Resource": "arn:aws:events:<region>:<account_no>:rule/<service_name>*"
    }
  ]
}
```
