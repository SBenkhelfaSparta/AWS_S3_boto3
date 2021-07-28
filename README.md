## Installing Python 3.9 and the Latest pip Version on Linux
```
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt-get update
apt list | grep python3.9
sudo apt-get install python3.9
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.9 1
sudo update-alternatives --config python3
alias python=python3
sudo apt install python3.9-distutils
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python3.9 get-pip.py
```
## Installing awscli and boto3
```
sudo pip3 install awscli
sudo pip3 install boto3
OR
pip install awscli
pip install boto3
```
## Connecting to AWS
Run `aws configure` and enter the required details on your native OS or VM. Test it by running `aws s3 ls` to see all buckets.

## Creating a boto3 Script
Create a .py file and enter in this code:
```
import boto3

s3 = boto3.client('s3')

response = s3.list_buckets()

# Output the bucket names
print('Existing buckets:')
for bucket in response['Buckets']:
    print(f'  {bucket["Name"]}')
```
Have your terminal/cmd open in the folder of the script and run it. Your output should be the same as the `aws s3 ls` line.

## boto3 Commands
### Create a Bucket
```
s3_client = boto3.client('s3')
s3_client.create_bucket(Bucket=bucket_name)
```
### Upload a File
```
s3_client = boto3.client('s3')
s3_client.upload_file(file_name, bucket, object_name)
```
### Download a File
```
s3 = boto3.client('s3')
s3.download_file('BUCKET_NAME', 'OBJECT_NAME', 'FILE_NAME')
```
### Delete a File
```
s3 = boto3.resource("s3")
obj = s3.Object("aniketbucketpython", "abcd.txt")
obj.delete()
```
### Delete a Bucket
```
client = boto3.client('s3')
client.delete_bucket(Bucket='forrandall2',)
```
