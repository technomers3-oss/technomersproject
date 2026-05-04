```python
import json

def lambda_handler(event, context):
    # TODO: Implement your Lambda function logic here
    return {
        'statusCode': 200,
        'body': json.dumps('Hello, World!')
    }
```