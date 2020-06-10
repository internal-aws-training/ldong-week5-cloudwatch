
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
