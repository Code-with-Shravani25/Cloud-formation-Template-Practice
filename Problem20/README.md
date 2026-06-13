## What is Drift Detection in CloudFormation?

- Drift occurs when a resource managed by CloudFormation is changed manually outside of CloudFormation.
- CloudFormation stores the expected configuration in the template.
- If someone changes the actual resource directly from the AWS Console, CLI, or SDK, the resource configuration may no longer match the template.

## How to Check Drift
---
## Method 1: AWS Console
- Open CloudFormation.
- Select your stack.
- Click Actions → Detect drift.
- Wait for the scan to complete.
- Check: View Stack Drift Status

## Method 2: AWS CLI

- Start Drift Detection
```bash
aws cloudformation detect-stack-drift --stack-name MyStack
```

- Check Detection Status
```bash
aws cloudformation describe-stack-drift-detection-status --stack-drift-detection-id abcd-1234
```

- View Resource Drift Details
```bash
aws cloudformation describe-stack-resource-drifts --stack-name MyStack
```

## How to Fix Drift

Option 1: Restore Resource to Match Template
- Run a stack update using the original template.

```bash
aws cloudformation update-stack --stack-name MyStack --template-body file://template.yaml
```

Option 2: Update Template to Match Actual Resource
- If the manual change is correct and should be retained then update template and then apply

```bash
aws cloudformation update-stack --stack-name MyStack --template-body file://template.yaml
```
