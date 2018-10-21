# ECS Service Discovery - Setup

## Set environment variables
```
export AWS_ACCOUNT_ID=<your_aws_account_id>
export AWS_REGION=<your_preferred_region>
```

## Clone the repository:
```
git clone https://github.com/pjlewisuk/ecs-service-discovery-demo
cd ecs-service-discovery-demo
```

## Create ECR repositories:
Be sure to use the repository names listed below (`flask-backend` and `flask-worker`) as CloudFormation will look for these later
```
$(aws ecr get-login --no-include-email --region ${AWS_REGION})
aws ecr create-repository --repository-name flask-backend
aws ecr create-repository --repository-name flask-worker
```

## Build, label and push the backend container image
```
cd backend
export BUILDTAG=$(date +%s)
docker build -t flask-backend .
docker tag flask-backend flask-backend:${BUILDTAG}
docker tag flask-backend ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_REGION}.amazonaws.com/flask-backend
docker tag flask-backend ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_REGION}.amazonaws.com/flask-backend:${BUILDTAG}
docker push ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_REGION}.amazonaws.com/flask-backend
docker push ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_REGION}.amazonaws.com/flask-backend:${BUILDTAG}
cd ..
```

## Build, label and push the worker container image
```
cd workers
export BUILDTAG=$(date +%s)
docker build -t flask-worker .
docker tag flask-worker flask-worker:${BUILDTAG}
docker tag flask-worker ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_REGION}.amazonaws.com/flask-worker
docker tag flask-worker ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_REGION}.amazonaws.com/flask-worker:${BUILDTAG}
docker push ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_REGION}.amazonaws.com/flask-worker
docker push ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_REGION}.amazonaws.com/flask-worker:${BUILDTAG}
cd ..
```