check your region is us east 1 /2 
go to your aws cloud shell
then 
run : aws s3 cp s3://cc-lab-share-79050/cc_lab.zip . && unzip -o cc_lab.zip && chmod +x scripts/.sh cleanup/.sh && ls scripts/ cleanup/ .

to run experiment  :
ls
cd scripts
bash  expname.sh

it will automatically run the script and then create your experiment

for sns sqs run : bash expname.sh youremail@gmail.com


in order to  clear all the setup of experiment :
cd ..
cd cleanup
run :
bash expname.sh


----------------------------------------------------------------------
s3 dynamodb integration code
import json
def lambda_handler(event, context): s3 = boto3.client("s3") dynamodb = boto3.resource('dynamodb')

# Check if the 'Records' key is present in the event
if 'Records' in event:
    # Iterate over each record in the event
    for record in event['Records']:
        bucket_name = record['s3']['bucket']['name']
        object_key = record['s3']['object']['key']
        size = record['s3']['object'].get('size', -1)
        event_name = record.get('eventName', 'Unknown')
        event_time = record.get('eventTime', 'Unknown')
        
        dynamoTable = dynamodb.Table('table-name')
        dynamoTable.put_item(
            Item={
                'id': str(uuid4()), 
                'Bucket': bucket_name, 
                'Object': object_key,
                'Size': size, 
                'Event': event_name, 
                'EventTime': event_time
            })
else:
    # Log a message indicating that the 'Records' key is missing
    print("No 'Records' key found in the event.")
----------------------------------------------------------------------
CDN

https://cdn.jsdelivr.net/gh/technomers3-oss/technomersproject@main/WEEK-7-LAMBDA.pdf

https://cdn.jsdelivr.net/gh/technomers3-oss/technomersproject@main/week-8.pdf

https://cdn.jsdelivr.net/gh/technomers3-oss/technomersproject@main/week9.pdf

https://cdn.jsdelivr.net/gh/technomers3-oss/technomersproject@main/WEEK-10.pdf

https://cdn.jsdelivr.net/gh/technomers3-oss/technomersproject@main/Experiment-11.pdf

https://cdn.jsdelivr.net/gh/technomers3-oss/technomersproject@main/week-12.pdf

https://cdn.jsdelivr.net/gh/technomers3-oss/technomersproject@main/week-13.pdf







https://scam-pied.vercel.app/
