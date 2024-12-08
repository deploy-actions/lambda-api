# Deploy API Server on Lambda

## About

GitHub Action for deploying API servers on AWS Lambda using AWS SAM (Serverless Application Model). This action provides a simple way to deploy your API server with AWS Lambda. Based on AWS SAM, it supports CloudFront integration and custom domain configuration with minimal setup.

## Simple Example of Usage

```yml
- name: Configure AWS credentials 🔑
  uses: aws-actions/configure-aws-credentials@main
  with:
    role-to-assume: ${{ vars.AWS_ROLE_ARN }}
    aws-region: ${{ vars.AWS_REGION }}

- uses: deploy-actions/lambda-api@v1
  with:
    Name: my-api
    CodeUri: ./dist
    Handler: index.handler
    Environment: |
      Variables:
        STAGE: production
```

## Inputs

| Name | Description | Mandatory |
|------|-------------|-----------|
| Name | AWS::Serverless::Function FunctionName and Cloudformation `LambdaAPI-{Name}` | ✅ |
| SAMSourceBucket | AWS S3 bucket where artifacts referenced in the template are uploaded |  |
| SAMToken | GitHub Authentication token for API calls |  |
| Architectures | Lambda function architecture (x86_64, arm64) |  |
| AutoPublishAliasAllProperties | Properties for auto-publishing new versions |  |
| CodeUri | Path to your Lambda function code |  |
| Description | Description of your Lambda function |  |
| Environment | Environment variables for your Lambda function |  |
| EphemeralStorage | Size of the /tmp directory |  |
| Cors | CORS configuration for Lambda URL |  |
| InvokeMode | Lambda URL invoke mode (BUFFERED or RESPONSE_STREAM) |  |
| Handler | Lambda function handler |  |
| ImageConfig | Container image configuration |  |
| ImageUri | URI of container image |  |
| InlineCode | Inline function code |  |
| KmsKeyArn | KMS key ARN for Lambda function |  |
| Layers | List of Lambda Layer versions |  |
| LoggingConfig | Lambda function logging configuration |  |
| MemorySize | Memory size in MB |  |
| Policies | IAM policies for Lambda function |  |
| ProvisionedConcurrencyConfig | Provisioned concurrency configuration |  |
| ReservedConcurrentExecutions | Reserved concurrent executions |  |
| Runtime | Lambda function runtime |  |
| RuntimeManagementConfig | Runtime management configuration |  |
| Timeout | Function timeout in seconds |  |
| VersionDescription | Description for this version |  |
| VpcConfig | VPC configuration |  |
| Aliases | CloudFront distribution aliases (domain names). Required with AcmCertificateArn and HostedZoneId |  |
| AcmCertificateArn | ACM certificate ARN for custom domain. Required with Aliases and HostedZoneId |  |
| HostedZoneId | Route 53 hosted zone ID. Required with Aliases and AcmCertificateArn |  |
