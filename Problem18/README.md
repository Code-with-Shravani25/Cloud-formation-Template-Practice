## Export Import Stack
---
- Used when one stack needs to share values with another stack
- Export and import are two seperate stacks.
- Used when independent CloudFormation stacks need to share resources.
- One stack exports a value through outputs and another stack imports it using Fn::!ImportValue
