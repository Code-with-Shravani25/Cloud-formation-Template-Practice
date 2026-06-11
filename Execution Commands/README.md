# Commands
---
## To create stack
```bash
aws cloudformation create-stack \
  --stack-name my-stack \
  --template-body file://template.yaml
```
## To delete stack
```bash
aws cloudformation delete-stack \
  --stack-name myec2
```
## To update stack
```bash
aws cloudformation update-stack \
  --stack-name my-stack \
  --template-body file://template.yaml
```
## To create stack of IAM service
```bash
aws cloudformation create-stack \
  --stack-name iam-stack \
  --template-body file://iam-template.yaml \
  --capabilities CAPABILITY_NAMED_IAM
```
- Why CAPABILITY_NAMED_IAM?

CloudFormation requires explicit acknowledgment before creating or modifying IAM resources because they affect permissions and security.

## To create stack and pass parameters
```bash
aws cloudformation create-stack \
  --stack-name my-stack \
  --template-body file://ec2.yaml \
  --parameters ParameterKey=InstanceType,ParameterValue=t3.micro
```
