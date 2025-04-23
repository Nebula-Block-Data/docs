# Python AWS S3 SDK Example

This example demonstrates how to connect to an S3-compatible service and list all buckets using the AWS SDK for Python (`boto3`).

## Prerequisites

Before running the code, ensure you have the following:

1. **Python** installed.
2. **boto3** library installed. You can install it using pip:
   ```bash
   pip install boto3
   ```
3. Replace `YOUR_ACCESS_KEY` and `YOUR_SECRET_KEY` with your actual AWS credentials.

## Python Code

```python
import boto3
from botocore.client import Config
import logging

# Enable debug logging (optional, useful for troubleshooting)
logging.basicConfig(level=logging.INFO)  # Change to DEBUG for more request details

# Set your NebulaBlock object storage information
ENDPOINT_URL = "HOST_NAME"  #Use the Hostname from the Details page.
ACCESS_KEY = 'YOUR_ACCESS_KEY'
SECRET_KEY = 'YOUR_SECRET_KEY'
REGION_NAME = 'US'

def list_buckets():
    try:
        # Create S3 client
        s3 = boto3.client(
            's3',
            aws_access_key_id=ACCESS_KEY,
            aws_secret_access_key=SECRET_KEY,
            endpoint_url=ENDPOINT_URL,
            region_name=REGION_NAME,
            config=Config(signature_version='s3v4')  # Use S3 v4 signature
        )

        # List buckets
        response = s3.list_buckets()
        print("Successfully connected! Current buckets:")
        for bucket in response['Buckets']:
            print(f"  - {bucket['Name']}")

    except Exception as e:
        print("Request failed:", str(e))

def main():
    list_buckets()

if __name__ == "__main__":
    main()
```

## Explanation

### Steps in the Code

1. **Credentials**:
   The program uses `boto3.client()` to authenticate with the S3-compatible service using the provided access key and secret key. Ensure to replace `YOUR_ACCESS_KEY` and `YOUR_SECRET_KEY` with your actual credentials.

2. **Client Configuration**:
   The `boto3.client()` is configured with the endpoint and region of the S3-compatible service. The `signature_version='s3v4'` ensures the use of S3 v4 signature for secure requests.

3. **List Buckets**:
   The `list_buckets()` method is called on the `s3` client to retrieve all the available buckets. The bucket names are then printed to the console.

4. **Error Handling**:
   If an error occurs during the process, it is caught in the `except` block, and the error message is printed.

## Run the Code

To run the program, simply execute the script as a standard Python application. Make sure to have the `boto3` library installed and the AWS credentials correctly configured.

---

**Note**: Ensure that you replace the placeholders for access key and secret key with your own credentials. These credentials should be securely stored and not hardcoded in production applications.

