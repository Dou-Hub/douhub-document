# {appname}-lambda-basic Role & Policy

## lambda-basic Policy

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "logs:*",
                "events:*",
                "kinesis:*",
                "qldb:*",
                "cloudwatch:*",
                "sns:*",
                "sqs:*"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "cloudfront:*"
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
                "arn:aws:secretsmanager:*:*:secret:douhub-*",
                "arn:aws:secretsmanager:*:*:secret:bandup-*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:*"
            ],
            "Resource": [
                "arn:aws:s3:::douhub-*",
                "arn:aws:s3:::bandup-*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "sqs:*"
            ],
            "Resource": [
                "arn:aws:sqs:*:*:douhub-*",
                "arn:aws:sqs:*:*:bandup-*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": "dynamodb:*",
            "Resource": [
                "arn:aws:dynamodb:*:*:table/douhub-*",
                "arn:aws:dynamodb:*:*:table/bandup-*"
            ]
        }
    ]
}
```

## Trust Relationships of the Role

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": ["edgelambda.amazonaws.com", "lambda.amazonaws.com"]
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```