**Boto 3 Notes**
# setting Boto3 up

- Install pip `sudo apt install python-pip`
-Install boto3 `python -m pip install boto3`
-Run python `python`
- Import Boto `import boto3` 

# Creating s3 Bucket

Python code:

```
s3_client = boto3.client('s3', region_name="eu-west-1")
location = {'LocationConstraint': "eu-west-1"}
s3_client.create_bucket(Bucket="eng99-delwar", CreateBucketConfiguration=location)
```
- Change `eu-west-1` to your region
- change `eng99-delwar` to the name you want the s3 bucket to be called

# adding file to s3 Bucket
```
s3 = boto3.client('s3')
s3.upload_file("/home/ubuntu/ReadMe.md", "eng99-delwar", "ReadMe.md")
```
- Change `/home/ubuntu/ReadMe.md` to the path of the file you want to add
- change `eng99-delwar` to the  name of the s3 bucket you want to add the file to
- change `ReadMe.md` to what you want the file to be called on the s3 bucket 

# Download file from bucket
```
s3 = boto3.client('s3')
s3.download_file(<bucket>, <location_on_bucket>, '<disired_location>')
```

# Delete file from bucket
```
s3 = boto3.client('s3')
s3.delete_object(<bucket_name>, <file_pathon_bucket>)
```

# Delete Bucket
```
s3 = boto3.client('s3')
s3.delete_bucket(<bucket_name>
```