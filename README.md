## Installing Python 3.9 and the Latest pip Version
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
```
## Connecting to AWS
Run `aws configure` and enter the required details on your native OS or on a VM. Test it by running `aws s3 ls` to see all buckets.

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
