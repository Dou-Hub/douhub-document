# dev-console Policy

The policy should be given to the IAM user who has permission to sign into AWS Console Online
The dev-cli policy should be given to this consoel user as well

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "secretsmanager:ListSecrets",
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": "s3:ListAllMyBuckets",
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": "resource-groups:ListGroups",
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": ["dynamodb:ListTables", "dynamodb:DescribeTable"],
      "Resource": "*"
    }
  ]
}

```
