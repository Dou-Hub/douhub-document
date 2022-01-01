# {appname}-{stage}-site Role

e.g. douhub-prod-site

This role will be used to run Serverless Next.JS Web Lambda Edge
It will be configured in the serverless.yml

```yml
inputs:
  runtime:
    defaultLambda: "nodejs14.x"
  bucketName: appname-us-dev-web
  name:
    defaultLambda: appname-us-prod-web
  roleArn: "arn:aws:iam::your-aws-account:role/appname-stage-site"
```

## {appname}-{stage}-site Policy

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Resource": "*",
      "Action": [
        "logs:CreateLogGroup",
        "logs:CreateLogStream",
        "logs:PutLogEvents"
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
