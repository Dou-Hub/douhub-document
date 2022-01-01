1. appname-us-prod-action

Access policy
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "allow-s3-action-trigger",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "SQS:SendMessage",
      "Resource": "arn:aws:sqs:us-east-1:110064165845:appname-us-prod-action",
      "Condition": {
        "ArnEquals": {
          "aws:SourceArn": "arn:aws:s3:*:*:appname-us-prod-action"
        }
      }
    }
  ]
}
```

2. appname-us-prod-message

Access policy
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "allow-s3-action-trigger",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "SQS:SendMessage",
      "Resource": "arn:aws:sqs:us-east-1:110064165845:appname-us-prod-message",
      "Condition": {
        "ArnEquals": {
          "aws:SourceArn": "arn:aws:s3:*:*:appname-us-prod-message"
        }
      }
    }
  ]
}
```


