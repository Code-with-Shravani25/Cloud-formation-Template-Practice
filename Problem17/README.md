- In AWS CloudFormation (CFT), Conditions are used to control whether a resource, property, output, or metadata is created based on some logic.

- Think of Conditions as if-else statements in CloudFormation.

## Why Use Conditions?

Suppose:

Create an EC2 instance only in Production.
Enable Multi-AZ only in Production.
Attach a specific Security Group only in Dev.

- Instead of maintaining multiple templates, you can use a single template with conditions.

## Step 1: Create a parameter
```bash
Parameters:
  Environment:
    Type: String
    AllowedValues:
      - Dev
      - Prod
```
## Step 2: Define Conditions
```bash
Conditions:
  IsProd: !Equals [!Ref Environment, Prod]
```
This means
```bash
If Environment = Prod
    IsProd = true
Else
    IsProd = false
```
## Step 3: Use Condition on Resource
```bash
Resources:
  MyEC2:
    Type: AWS::EC2::Instance
    Condition: IsProd
    Properties:
      ImageId: ami-123456
      InstanceType: t2.micro
```
# Condition Functions
1. !Equals

Checks whether two values are equal.
```bash
Conditions:
  IsProd: !Equals [!Ref Environment, Prod]
```

2. !And

Both conditions must be true.
```bash
Conditions:
  CreateResource: !And
    - !Equals [!Ref Environment, Prod]
    - !Equals [!Ref Region, us-east-1]
```
3. !Or

At least one condition must be true.
```bash
Conditions:
  IsDevOrProd: !Or
    - !Equals [!Ref Environment, Dev]
    - !Equals [!Ref Environment, Prod]
```
4. !Not

Negates a condition.
```bash
Conditions:
  IsNotProd: !Not
    - !Equals [!Ref Environment, Prod]
```
