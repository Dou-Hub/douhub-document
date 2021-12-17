{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "cloudfront:ListCloudFrontOriginAccessIdentities",
                "dynamodb:BatchGet*",
                "s3:PutAccelerateConfiguration",
                "cloudfront:ListFieldLevelEncryptionConfigs",
                "dynamodb:Get*",
                "logs:*",
                "s3:CreateBucket",
                "s3:ListBucket",
                "s3:GetAccelerateConfiguration",
                "cloudfront:CreateInvalidation",
                "cloudfront:CreateCloudFrontOriginAccessIdentity",
                "cloudfront:GetDistribution",
                "dynamodb:DescribeTable",
                "dynamodb:Delete*",
                "kinesis:*",
                "cloudfront:UpdateDistribution",
                "dynamodb:Update*",
                "cloudfront:GetDistributionConfig",
                "events:*",
                "dynamodb:PutItem",
                "apigateway:*",
                "cloudfront:ListDistributionsByLambdaFunction",
                "dynamodb:Scan",
                "dynamodb:Query",
                "dynamodb:DescribeStream",
                "cloudfront:CreateDistribution",
                "ec2:DescribeSecurityGroups",
                "cloudformation:Describe*",
                "dynamodb:CreateTable",
                "s3:PutObject",
                "s3:GetObject",
                "cloudfront:ListPublicKeys",
                "ec2:DescribeVpcs",
                "cloudfront:ListInvalidations",
                "cloudfront:ListDistributions",
                "cloudfront:ListFieldLevelEncryptionProfiles",
                "dynamodb:BatchWrite*",
                "s3:PutBucketPolicy",
                "cloudfront:ListStreamingDistributions",
                "ec2:DescribeSubnets",
                "qldb:*",
                "cloudformation:ValidateTemplate",
                "cloudfront:ListDistributionsByWebACLId"
            ],
            "Resource": "*"
        },
        {
            "Sid": "VisualEditor1",
            "Effect": "Allow",
            "Action": [
                "lambda:CreateFunction",
                "lambda:TagResource",
                "cloudformation:CancelUpdateStack",
                "secretsmanager:DescribeSecret",
                "cloudformation:UpdateTerminationProtection",
                "iam:CreateRole",
                "lambda:GetFunctionConfiguration",
                "iam:AttachRolePolicy",
                "cloudformation:CreateChangeSet",
                "iam:PutRolePolicy",
                "lambda:UntagResource",
                "secretsmanager:ListSecretVersionIds",
                "lambda:EnableReplication",
                "cloudformation:ContinueUpdateRollback",
                "iam:PassRole",
                "secretsmanager:GetSecretValue",
                "lambda:ListTags",
                "cloudformation:UpdateStack",
                "lambda:DeleteFunction",
                "cloudformation:ExecuteChangeSet",
                "iam:GetRole",
                "lambda:GetFunction",
                "lambda:UpdateFunctionConfiguration",
                "lambda:UpdateFunctionCode",
                "secretsmanager:GetResourcePolicy",
                "iam:CreateServiceLinkedRole",
                "cloudformation:CreateStack",
                "cloudformation:DeleteStack",
                "lambda:PublishVersion",
                "cloudformation:Get*"
            ],
            "Resource": [
                "arn:aws:lambda:*:*:function:*",
                "arn:aws:secretsmanager:*:*:secret:perkhero-*",
                "arn:aws:cloudformation:*:*:stack/perkhero-*/*",
                "arn:aws:iam::*:role/*"
            ]
        },
        {
            "Sid": "VisualEditor2",
            "Effect": "Allow",
            "Action": [
                "cloudformation:CreateUploadBucket",
                "cloudformation:EstimateTemplateCost",
                "cloudformation:List*",
                "cloudformation:Describe*"
            ],
            "Resource": "arn:aws:cloudformation:*:*:stack/perkhero-*/*"
        },
        {
            "Sid": "VisualEditor3",
            "Effect": "Allow",
            "Action": [
                "cloudformation:CreateUploadBucket",
                "cloudformation:EstimateTemplateCost",
                "cloudformation:CancelUpdateStack",
                "cloudformation:CreateStack",
                "cloudformation:DeleteStack",
                "cloudformation:UpdateTerminationProtection",
                "cloudformation:UpdateStack",
                "cloudformation:CreateChangeSet",
                "cloudformation:List*",
                "cloudformation:ExecuteChangeSet",
                "cloudformation:Get*",
                "cloudformation:ContinueUpdateRollback"
            ],
            "Resource": "arn:aws:cloudformation:*:*:stack/perkhero-*/*"
        },
        {
            "Sid": "VisualEditor4",
            "Effect": "Allow",
            "Action": [
                "lambda:ListEventSourceMappings",
                "lambda:CreateEventSourceMapping"
            ],
            "Resource": "arn:aws:lambda:*:*:function:*"
        }
    ]
}