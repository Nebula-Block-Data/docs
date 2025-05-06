# Nebula Block Storage Python SDK Example

This example demonstrates how to interact with Nebula Block's S3-compatible storage service using the AWS SDK for Python (boto3). The example includes connecting to the service, listing buckets, and generating a presigned URL using the AWS SDK for Python [`boto3`](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html).

## Prerequisites

1. Python 3.6 or later installed
2. AWS SDK for Python (boto3) installed:
```bash
pip install boto3
```
3. Your Nebula Block credentials:
   - Access Key ID
   - Secret Access Key
   - Endpoint URL

## Example Code

```python
import boto3
from botocore.client import Config

# Configuration
ACCESS_KEY = 'your_access_key'
SECRET_KEY = 'your_secret_key'
ENDPOINT_URL = 'your_endpoint'  # Replace with your endpoint

# Create an S3 client
s3_client = boto3.client(
    's3',
    aws_access_key_id=ACCESS_KEY,
    aws_secret_access_key=SECRET_KEY,
    endpoint_url=ENDPOINT_URL,
    config=Config(signature_version='s3v4')
)

def list_buckets():
    """List all buckets in your account"""
    try:
        response = s3_client.list_buckets()
        print("Your buckets:")
        for bucket in response['Buckets']:
            print(f"- {bucket['Name']}")
    except Exception as e:
        print(f"Error listing buckets: {e}")

def upload_file(bucket_name, file_path, object_name):
    """Upload a file to S3"""
    try:
        s3_client.upload_file(file_path, bucket_name, object_name)
        print(f"Successfully uploaded {file_path} to {bucket_name}/{object_name}")
    except Exception as e:
        print(f"Error uploading file: {e}")

def generate_presigned_url(bucket_name, object_name, expiration=3600):
    """Generate a presigned URL for an object"""
    try:
        url = s3_client.generate_presigned_url(
            'get_object',
            Params={
                'Bucket': bucket_name,
                'Key': object_name
            },
            ExpiresIn=expiration
        )
        print(f"Presigned URL: {url}")
        return url
    except Exception as e:
        print(f"Error generating presigned URL: {e}")
        return None

if __name__ == '__main__':
    # Example usage
    list_buckets()
    
    # Upload a file
    upload_file('my-bucket', 'local_file.txt', 'remote_file.txt')
    
    # Generate a presigned URL
    generate_presigned_url('my-bucket', 'remote_file.txt')
```

## Usage

1. Replace the placeholder credentials with your actual Nebula Block credentials
2. Update the endpoint URL if necessary
3. Run the script:
```bash
python storage_example.py
```

## Additional Features

The boto3 SDK provides many more features for working with S3-compatible storage:
- Multipart uploads
- Object versioning
- Bucket policies
- Access control lists (ACLs)
- Server-side encryption
- Object tagging

For more information, refer to the [boto3 documentation](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/s3.html). 