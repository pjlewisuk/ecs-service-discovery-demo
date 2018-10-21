# ECS Service Discovery

![Architecture](https://github.com/ranman/ecs-service-discovery-demo/raw/master/backend/static/sd.png)

Full details in the [blog post](https://aws.amazon.com/blogs/aws/amazon-ecs-service-discovery/)!

This provides two docker containers: backend and worker. Both run simple flask apps. The ".corp" domain name is assumed.

Click [here](SETUP.md) for setup steps to run **prior to launching the CloudFormation stack**. Please ensure you push the container images to ECR repositories in the same AWS account as you deploy the CloudFormation stacks below, otherwise the ECS services will fail to launch.

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
