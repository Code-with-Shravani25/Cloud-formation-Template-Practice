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
## to update stack
```bash
aws cloudformation update-stack \
  --stack-name my-stack \
  --template-body file://template.yaml
```
