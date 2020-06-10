
# Steps

## ClouldFormation

Create Stack

```bash
WORK_PATH="$(cd "$(dirname "${BASH_SOURCE[0]}")"  && pwd)"

aws cloudformation create-stack --stack-name ldong-cf-lambda-stack --template-body file://$WORK_PATH/aws/template01.yaml
```

```bash
WORK_PATH="$(cd "$(dirname "${BASH_SOURCE[0]}")"  && pwd)"
aws cloudformation update-stack --stack-name ldong-cf-lambda-stack --template-body file://$WORK_PATH/aws/template01.yaml
```

Delete Stack

```bash
aws cloudformation delete-stack --stack-name ldong-cf-lambda-stack
```

## Lambda - Boto3

Create a Lambda function use [Boto3](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html) to [send metric data](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/cloudwatch.html#CloudWatch.Client.put_metric_data) to metrics.

## Practice

1. ClouldWatch trigger lambda to send metrics

```bash
./run_couldwatch_send_metrics.sh ldong-cf-lambda-stack
```

2. CouldWatch trigger lambda to send log

```bash
./run_couldwatch_send_metrics.sh ldong-cf-lambda-log-stack
```
