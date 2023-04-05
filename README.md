
Getting Alerts when Apache hudi Delta Streamer Fails with Event Driven Approach using Lambdas and Event Bridge 


![1](https://user-images.githubusercontent.com/39345855/230165531-9bd8c5b6-a559-445c-8e5b-8e24c084b663.JPG)

## Solution Overview 
* Whenever the state changes for EMR job that event shall be sent to AWS Event Bridge and where we shall have a rule if the event matches with given rule then event shall be passed to Lambda function which will process and send details to SNS Topic where subscribed candidates can be notified via email

# Steps 

##### Step 1: Download the repository

```
git clone https://github.com/soumilshah1995/How-to-receive-notifications-when-your-Glue-ETl-scripts-fail-Email-Alerts.git
```

##### Step 2: change the Env Values
```
ACCOUNT=XXXXX
TopicName=emr-jobs-topics
DEV_ACCESS_KEY=XXXXXXXXX
DEV_SECRET_KEY=XXX
DEV_REGION=us-east-1
```

* replace where it says XXXX with your AWS Account ID

##### Step 3: Add your Email Address

```
    MySubscription:
      Type: AWS::SNS::Subscription
      Properties:
        Endpoint: <ADD YOUR EMAIL ADDRESS HERE>
        Protocol: email
        TopicArn: !Ref 'SNSTopic'
```


##### Step 4 Deploy

```
serverless config credentials --provider aws --key <ACCESS KEY>  --secret <SECRET KEY>  -o
serverless config credentials --provider aws --key <AKIAQUOMZI4GIZ4PHGL4  --secret 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  -o


sls deploy
OR
npx sls deploy

```