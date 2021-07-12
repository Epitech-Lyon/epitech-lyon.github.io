---
layout: post
title:  "Experiencing the AWS lambda functions"
author: lkaroubi
categories: [ experience ]
image: assets/images/thunderbolt/affiche.jpg
published: true
comments: false
---

[Thunderbolt][1] is a set of AWS lambda functions for AWS resources scheduling. It is part of a bigger AWS project I am working on, named [ParadigmShift](https://github.com/le0kar0ub1/ParadigmShift), which was intended to be a global and high level AWS resources scheduler, it is well documented in the link above.

## First things first : AWS

AWS is a [cloud provider](https://fr.wikipedia.org/wiki/Cloud_computing) which provides a large list of services (databases/server/IA/storage/...).

AWS Lambda is a FAAS (Function As A Service) which allows you to run small code with a total abstraction of the under-layers. To be clear, you can put your code in the service and then trigger it by multiple ways. Lambda is the core of the serverless model on AWS.

![serverless_asw_lambda](https://ucarecdn.com/889eff87-74c6-4447-907a-0feb2fc041d8/-/resize/1050/)

## Thunderbolt

### What is it?

Thunderbolt is a set of 3 lambda functions --- because that were the three functions I needed when I created the project --- used to manipulate Amazon RDS (SQL database), Amazon EC2 (Server), Amazon AppStream (application streaming). The manipulations are basically, *power on/off* and *change instance type* (number of cpus, memory allocated, ...) when relevant.

### Why ?

In fact Thunderbolt is used as a git submodule in a bigger AWS project named [ParadigmShift](https://github.com/le0kar0ub1/ParadigmShift). *ParadigmShift* was intended to be a global and high level AWS resources scheduler, it is well documented in the link above.

### How ?

Even if it is included in a bigger scheme, the project actually can be deployed as is. The deployment is insured by AWS cloudformation which is a powerful IaC (Infrastructure as code) integrator. So pragmatically you can describe your resources in a text file and the CloudFormation service will interpret and generate your requests.

![cfm](https://blogs.vmware.com/management/files/2019/10/image002.png)

## Technical side

A sample of the deployment script which uses an AWS Cloudformation template (SAM template to be accurate, but this is in the same idea).

```sh
...
echo "-------- Create SAM bucket --------"

# Create the S3 bucket (storage in cloud as filesystem) which will be used for the deployment
aws s3api create-bucket                                         \
    --bucket $bucket                                            \
    --region $region                                            \
    --create-bucket-configuration LocationConstraint=$region    \
    --profile $awsprofile

echo "-------- Deploy lambas --------"

# Create the build
sam build --profile $awsprofile

# Package the build in the created bucket
sam package                                     \
    --s3-bucket $bucket                         \
    --output-template-file build/package.yml    \
    --profile $awsprofile

# Finally deploy the resources on the targeted AWS account
sam deploy                                      \
    --template-file build/package.yml           \
    --stack-name $project                       \
    --capabilities CAPABILITY_NAMED_IAM         \
    --region $region                            \
    --tags Project=$project                     \
    --profile $awsprofile                       \
    --parameter-overrides                       \
        Project=$project                        \

CLEANUP

trap - EXIT
```

A sample of the template which describes the lambda that handles the RDS and its role.
The role is assigned to the lambda and allows the manipulation of other AWS services.

```yml
  # describe the role: the rights on others AWS services and resources which can be affected
  rdsLamdaRole:
    Type: AWS::IAM::Role
    Properties:
      RoleName: !Sub "${Project}-rds-LambdaRole"
      AssumeRolePolicyDocument:
        Version: '2012-10-17'
        Statement:
          - Effect: Allow
            Principal:
              Service:
                - lambda.amazonaws.com
            Action: sts:AssumeRole
      Policies:
        - PolicyName: LogsPolicy
          PolicyDocument:
            Version: '2012-10-17'
            Statement:
              - Effect: Allow
                Action:
                  - logs:CreateLogGroup
                  - logs:CreateLogStream
                  - logs:PutLogEvents
                Resource: "*"
        # The important one, right to start/stop/modify RDS instance
        - PolicyName: rdsPolicy
          PolicyDocument:
            Version: '2012-10-17'
            Statement:
              - Effect: Allow
                Action:
                  - rds:startDBInstance,
                  - rds:stopDBInstance,
                  - rds:modifyDBInstance
                Resource: "*"
  # describe the function and give the source code path
  rdsLambdaFunction:
      Type: AWS::Serverless::Function
      Properties:
          FunctionName: !Sub "${Project}-rds-handler"
          Description: rds start/stop/modify
          CodeUri: src
          Handler: rds-handler.handler
          Role: !GetAtt rdsLamdaRole.Arn
          Environment:
            Variables:
              Project: !Sub "${Project}"
```

An example of function in this RDS lambda which stops a RDS instance. The lambda is written in node.js.

```js
function rds_stop(id)
{
    return new Promise((resolve, reject) => {
        const params = {
            DBInstanceIdentifier: id
        };
        /* 
         * call to AWS SDK
         **/
        rds.stopDBInstance(params, function(err, data) {
            if (err)
                return reject(err);
            else
                return resolve("Success")
        });
    });
}
```

For those who whant to go further, [follow the repository page](https://github.com/le0kar0ub1/Thunderbolt/tree/master/aws).

### Improve ?

Handle more services and manipulations, if they are relevant for ParadigmShift project.
