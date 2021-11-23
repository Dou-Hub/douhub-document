# The index of all DouHub GitHub repositories

The list of repos below contains the helper functions for utility, lambda, AWS services, Azure Services, Other cloud services (such as Elastic Search, Twillio ...) and basic/generic functions that can be used in  most of SaaS applications 

## Open source Repos (public MIT license)

### Utility Repos

1. [douhub-helper-util](https://github.com/Dou-Hub/douhub-helper-util)
The basic helper functions that can be used in Lambda, React JS and React Native
Such as isEmail, newGuid, ...

2. [douhub-helper-lambda](https://github.com/Dou-Hub/douhub-helper-lambda)
The basic helper functions that can be used in AWS Lambda
such as constants, onSuccess, onError, encrypt/decrypt. apiToken, authToken, context ...

3. [douhub-helper-web](https://github.com/Dou-Hub/douhub-helper-web)
The basic functions that can be used in Next.js web app. 
such has render HTML metadata in head, server code, multi-lang code ...

### Cloud Services Repos

1. [douhub-helper-services](https://github.com/Dou-Hub/douhub-helper-services)
The handy functions to work with AWS cloud services, Azure cloud services ...
Such as Secret Manager, S3, DynamoDB, CosmosDB, SNS, SQS ...

2. [douhub-helper-search](https://github.com/Dou-Hub/douhub-helper-search)
The handy functions to work with Elastic Search

3. [douhub-helper-message](https://github.com/Dou-Hub/douhub-helper-message)
The functions that are used to send SMS, In-app Notification & Emails

4. [douhub-helper-message](https://github.com/Dou-Hub/douhub-helper-realtime)
The functions that are used to handle realtime pub/sub websocket message


### UI repos

1. [douhub-ui-store](https://github.com/Dou-Hub/douhub-ui-store)
The mobx stores for context, message & enviroment on React JS and React Native app.

2. [douhub-ui-web](https://github.com/Dou-Hub/douhub-ui-web)
The React JS UI components for web app 

3. [douhub-ui-mobile](https://github.com/Dou-Hub/douhub-ui-mobile)
The React Native UI components for mobile app 

### Lamnda REST APIs

1. [douhub-api-video-create](https://github.com/Dou-Hub/douhub-api-video-create)
triggered when a video is created in S3 and will send it to AWS video transcoding service to make it ready for streaming

2. [douhub-api-video-delete](https://github.com/Dou-Hub/douhub-api-video-delete)
triggered when a video is deleted in S3 and will delete all related streaming video segment files

3. [douhub-api-photo-create](https://github.com/Dou-Hub/douhub-api-photo-create)
triggered when a video is created in S3 and will send it to AWS video transcoding service to make it ready for streaming

4. [douhub-api-photo-delete](https://github.com/Dou-Hub/douhub-api-photo-delete)
triggered when a video is deleted in S3 and will delete all related streaming video segment files

5. [douhub-api-warmup](https://github.com/Dou-Hub/douhub-api-warmup)
The auto cross region crawler for web app warm up 


## Platform Repos (Private)

1. [douhub-platform-context](https://github.com/Dou-Hub/douhub-platform-context)
The functions that are used for authentication, authorization and context related features

2. [douhub-platform-data](https://github.com/Dou-Hub/douhub-platform-data)
The functions that are used for business data management

3. [douhub-platform-content](https://github.com/Dou-Hub/douhub-platform-content)
The functions that are used for web feed crawler, content parsing ...

4. [douhub-platform-ui](https://github.com/Dou-Hub/douhub-platform-ui)
The UI components that is cross platform (web & mobile)

5. [douhub-api-user](https://github.com/Dou-Hub/douhub-api-user)
The functions to manage user profile

6. [douhub-api-action](https://github.com/Dou-Hub/douhub-api-action)
The action distrbutor to control actions