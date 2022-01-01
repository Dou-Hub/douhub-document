## Design Concept

1. Action Request will be dropped as a Action Request File into a S3 bucket ${self:custom.prefix}-action
2. S3 bucket will have one event notification ${self:custom.prefix}-action-queue for "All object create events". The event will be dropped into SQS queue ${self:custom.prefix}-action
3. SQS queue will call a Lambda that will parse and handle the Action Request S3 File and forward the request to a SNS (defined in the request)
4. There maybe one or multiple Lambda subscribe to the SNS, these Lambda will be called and run.

NOTE: ${self:custom.prefix}-action queue need to be configured to the ${self:custom.prefix}-action bucket manually

## Example for a System Action - Record Backup and Version 

NOTE: In the example below, the app name is bandup

CosmosDB is the main database that is used to keep all records. When a record is created or updated in the CosmosDB, a backup has to be kept in the bandup-us-prod-data S3 bucket. By the using the Version feature in the S3 bucket, the version of each update will be kept as well.


### Send Action Example
1. When creating a record, the create API will save a record in CosmoDB and then call _.sendAction function to drop a file into the S3 bucket bandup-us-prod-action

```JSON
    //_.sendAction(cx, snsTopic, data, settings)
    //s3BucketName = `${process.env.PREFIX}-${settings.type}`;
    //s3FileName = `${solutionId}/${organizationId}/${snsTopic}/${_.isNonEmptyString(name) ? name + '/' : ''}${guid}.json`;
    await _.sendAction('data', data, { ignoreOrganizationId: true, ignoreUserId: true, name: 'create', type: 'action' });
```

2. S3 bucket bandup-us-prod-action has one Event Notification named bandup-us-prod-action-queue
3. bandup-us-prod-action-queue will send notification to the SQS queue arn:aws:sqs:us-east-1:{aws-account-id}:bandup-us-prod-action when the "All object create events" event is triggered
4. The SQS queue arn:aws:sqs:us-east-1:{account-id}:bandup-us-prod-action will call arn:aws:lambda:us-east-1:{aws-account-id}:function:bandup-us-prod-action-prod-handleSQS Lambda
5. The arn:aws:lambda:us-east-1:{aws-account-id}:function:bandup-us-prod-action-prod-handleSQS Lambda will get the S3 event in the format below
```json
{
    "bucketName": "bandup-us-prod-action",
    "fileName": "2409e25b-29c4-42d0-8371-e25175be5fbb/cd0390a2-d905-4068-a1ac-9d2f1cc9aa96/data/create/5c97b7da-2ea3-46a9-85b7-f16579414612.json"
}
```
6. The bandup-us-prod-action-prod-handleSQS lambda will forwarded this even to a SNS Topic 
The name of the SNS topic comes from fileName.split('/')[2], in this case the SNS Topic will be arn:aws:sns:us-east-1:{aws-account-id}:bandup-us-prod-data

7. There will be one or more subscriptions to arn:aws:sns:us-east-1:{aws-account-id}:bandup-us-prod-data, by default, we have two to this SNS topic.

8. In this case the Lambda arn:aws:lambda:us-east-1:{aws-account-id}:function:bandup-us-prod-data-prod-processSNSDataToS3 subscribes to arn:aws:sns:us-east-1:{aws-account-id}:bandup-us-prod-data SNS topic.

9. The Lambda function bandup-us-prod-data-prod-processSNSDataToS3 will read the data in the S3 file and create a file in the S3 bucket bandup-us-prod-data 

