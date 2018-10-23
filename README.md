# ECS Service Discovery

This demo deploys Randall Hunt's ECS Service Discovery example using CloudFormation. The example provides two docker containers: `backend` and `worker`. Both run simple flask apps. The ".corp" domain name is assumed for discovery purposes. Full details can be found in his [blog post](https://aws.amazon.com/blogs/aws/amazon-ecs-service-discovery/).

[Click here](SETUP.md) for setup steps to run **prior to launching the CloudFormation stack**. Please ensure you push the container images to ECR repositories in the same AWS account as you deploy the CloudFormation stacks below, otherwise the ECS services will fail to launch.

You can launch this CloudFormation stack in your account:

| AWS Region | Short name | Launch | 
| ---------- | ---------- | ------ |
| US East (Ohio) | us-east-2 | [![cloudformation-launch-button](images/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=us-east-2#/stacks/new?stackName=ecs-sd-demo&templateURL=https://s3-eu-west-1.amazonaws.com/pjlewis-aws-ecs-service-discovery-demo/master.yaml) |
| US East (N. Virginia) | us-east-1 | [![cloudformation-launch-button](images/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=ecs-sd-demo&templateURL=https://s3-eu-west-1.amazonaws.com/pjlewis-aws-ecs-service-discovery-demo/master.yaml) |
| US West (Oregon) | us-west-2 | [![cloudformation-launch-button](images/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=ecs-sd-demo&templateURL=https://s3-eu-west-1.amazonaws.com/pjlewis-aws-ecs-service-discovery-demo/master.yaml) |
| EU (Ireland) | eu-west-1 | [![cloudformation-launch-button](images/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/new?stackName=ecs-sd-demo&templateURL=https://s3-eu-west-1.amazonaws.com/pjlewis-aws-ecs-service-discovery-demo/master.yaml) |
| EU (Frankfurt) | eu-central-1 | [![cloudformation-launch-button](images/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=eu-central-1#/stacks/new?stackName=ecs-sd-demo&templateURL=https://s3-eu-west-1.amazonaws.com/pjlewis-aws-ecs-service-discovery-demo/master.yaml) |
| Asia Pacific (Singapore) | ap-southeast-1 | [![cloudformation-launch-button](images/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=ecs-sd-demo&templateURL=https://s3-eu-west-1.amazonaws.com/pjlewis-aws-ecs-service-discovery-demo/master.yaml) |
| Asia Pacific (Tokyo) | ap-northeast-1 | [![cloudformation-launch-button](images/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/new?stackName=ecs-sd-demo&templateURL=https://s3-eu-west-1.amazonaws.com/pjlewis-aws-ecs-service-discovery-demo/master.yaml) |
| Asia Pacific (Sydney) | ap-southeast-2 | [![cloudformation-launch-button](images/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-2#/stacks/new?stackName=ecs-sd-demo&templateURL=https://s3-eu-west-1.amazonaws.com/pjlewis-aws-ecs-service-discovery-demo/master.yaml) |

Launching one of the stacks above will provide a simplified version of the following architecture, with only two services: `backend` to serve requests, with a single `worker` microservice to provide responses. You can find the web endpoint where the service is hosted on the 'Output' tab of the main CloudFormation stack that was created, or by running the following command:  
``aws cloudformation describe-stacks --stack-name ecs-sd-demo --query 'Stacks[0].Outputs[?OutputKey==`DemoServiceUrl`].OutputValue' --output text``

![Architecture](https://github.com/ranman/ecs-service-discovery-demo/raw/master/backend/static/sd.png)

To update the CloudFormation deployment to add more services, simply select "Update Stack" from the Actions menu with the master stack selected, continue using the current template, then change the `DeployAdditionalServices` parameter to `True` and click through to finish the wizard. To do this via the CLI run the following command:  
`aws cloudformation update-stack --stack-name ecs-sd-demo --template-url https://s3-eu-west-1.amazonaws.com/pjlewis-aws-ecs-service-discovery-demo/master.yaml --parameters ParameterKey=DeployAdditionalServices,ParameterValue=true`

After a few minutes the additional services will be deployed and when you refresh the page you will see them listed under the services found via service discovery.
