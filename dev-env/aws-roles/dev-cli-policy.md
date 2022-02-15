# dev-cli Policy

The policy should be given to the IAM user that will be used to deploy web app and lambda APIs
The AWS credential type of the user should ideally only be "Access Key - Programatic Access".

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "apigateway:*",
                "ec2:DescribeVpcs",
                "ec2:DescribeSubnets",
                "ec2:DescribeSecurityGroups",
                "logs:*",
                "events:*",
                "kinesis:*",
                "qldb:*",
                "cloudwatch:*",
                "sqs:*",
                "lambda:*",
                "s3:*"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "route53:ListHostedZones",
                "route53:ChangeResourceRecordSets",
                "route53:GetHostedZone",
                "route53:ListResourceRecordSets"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "acm:ListCertificates"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "cloudfront:CreateCloudFrontOriginAccessIdentity",
                "cloudfront:CreateDistribution",
                "cloudfront:CreateInvalidation",
                "cloudfront:GetDistribution",
                "cloudfront:GetDistributionConfig",
                "cloudfront:ListCloudFrontOriginAccessIdentities",
                "cloudfront:ListDistributions",
                "cloudfront:ListDistributionsByLambdaFunction",
                "cloudfront:ListDistributionsByWebACLId",
                "cloudfront:ListFieldLevelEncryptionConfigs",
                "cloudfront:ListFieldLevelEncryptionProfiles",
                "cloudfront:ListInvalidations",
                "cloudfront:ListPublicKeys",
                "cloudfront:ListStreamingDistributions",
                "cloudfront:UpdateDistribution"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "secretsmanager:GetResourcePolicy",
                "secretsmanager:GetSecretValue",
                "secretsmanager:DescribeSecret",
                "secretsmanager:ListSecretVersionIds"
            ],
            "Resource": [
                "arn:aws:secretsmanager:*:*:secret:bandup-*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "iam:GetRole",
                "iam:PassRole",
                "iam:CreateServiceLinkedRole",
                "iam:AttachRolePolicy",
                "iam:PutRolePolicy",
                "iam:CreateRole"
            ],
            "Resource": [
                "arn:aws:iam::*:role/*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:*"
            ],
            "Resource": [
                "arn:aws:s3:::bandup-*",
                "arn:aws:s3:::douhub-*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "sqs:*"
            ],
            "Resource": [
                "arn:aws:sqs:*:*:bandup-*",
                "arn:aws:sqs:*:*:douhub-*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "sns:*"
            ],
            "Resource": [
                "arn:aws:sns:*:*:bandup-*",
                "arn:aws:sns:*:*:douhub-*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "cloudformation:CancelUpdateStack",
                "cloudformation:ContinueUpdateRollback",
                "cloudformation:CreateChangeSet",
                "cloudformation:CreateStack",
                "cloudformation:CreateUploadBucket",
                "cloudformation:DeleteStack",
                "cloudformation:Describe*",
                "cloudformation:EstimateTemplateCost",
                "cloudformation:ExecuteChangeSet",
                "cloudformation:Get*",
                "cloudformation:List*",
                "cloudformation:UpdateStack",
                "cloudformation:UpdateTerminationProtection"
            ],
            "Resource": [
                "arn:aws:cloudformation:*:*:stack/bandup-*/*",
                "arn:aws:cloudformation:*:*:stack/douhub-*/*"
            ]
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
                "lambda:CreateFunction",
                "lambda:CreateEventSourceMapping",
                "lambda:EnableReplication",
                "lambda:DeleteFunction",
                "lambda:PublishVersion",
                "lambda:TagResource",
                "lambda:UntagResource",
                "lambda:AddPermission",
                "lambda:CreateAlias",
                "lambda:DeleteAlias",
                "lambda:DeleteEventSourceMapping",
                "lambda:Get*",
                "lambda:List*",
                "lambda:RemovePermission",
                "lambda:Update*"
            ],
            "Resource": [
                "arn:aws:lambda:*:*:function:*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": "dynamodb:*",
            "Resource": [
                "arn:aws:dynamodb:*:*:table/bandup-*",
                "arn:aws:dynamodb:*:*:table/douhub-*"
            ]
        }
    ]
}
```
