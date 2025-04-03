# How to Setup s3cmd in Windows

## 1. Install s3cmd

### Step 1: Check Python Installation
Ensure Python is installed by running:

```sh
python --version
```

If Python is not installed, download and install it from [Python Official Website](https://www.python.org/downloads/).

### Step 2: Upgrade pip
Run the following command to upgrade `pip`:

```sh
python -m pip install --upgrade pip
```

### Step 3: Install s3cmd
Run the following command to install `s3cmd`:

```sh
pip install s3cmd
```

### Step 4: Ensure s3cmd is Executable
By default, Windows may recognize `s3cmd` as a file without an extension instead of a Python script. Navigate to the following path:

```
C:\Users\<Username>\AppData\Local\Programs\Python\PythonXX\Scripts\
```

- If `s3cmd` is present without a `.py` extension, rename it to `s3cmd.py`.
- Add this location to your system environment variables (`Path`).

### Step 5: Verify Installation
Run:

```sh
s3cmd --version
```

If `s3cmd` does not execute correctly, open the `s3cmd` file and ensure the first two lines are:

```
#!C:\Python310\python.exe
#coding: utf-8 -
```

If necessary, run `s3cmd` using:

```sh
python C:\Python310\Scripts\s3cmd.py --version
```

Alternatively, create a `s3cmd.bat` file in the same directory as `s3cmd.py` with the following content:

```
@echo off
python C:\Python310\Scripts\s3cmd %*
```

Then, retry running:

```sh
s3cmd --version
```

## 2. Configure s3cmd

Run:

```sh
s3cmd --configure
```

You will be prompted to enter the following details:

```
Access Key: your_ak
Secret Key: your_sk
Default Region: cn-east-1
S3 Endpoint: http://s3-qos.xy-jnd-3.qiniu-solutions.com/
DNS-style bucket+hostname: http://s3-qos.xy-jnd-3.qiniu-solutions.com/
Encryption password: (press Enter to pass)
Path to GPG program: (press Enter to pass)
Use HTTPS protocol: No
HTTP Proxy server name: (press Enter to pass)
```

Test access with supplied credentials:

```
Test access with supplied credentials? [Y/n]: Y
```

If the connection is successful, you will see:

```
Please wait, attempting to list all buckets...
Success. Your access key and secret key worked fine :-)
```

Save settings:

```
Save settings? [y/N]: y
```

Your configuration will be saved at:

```
C:\Users\<Username>\AppData\Roaming\s3cmd.ini
```

## 3. Usage Examples

### List Buckets
```sh
s3cmd ls
```

### Create a Bucket
```sh
s3cmd mb s3://my-bucket-name
```

### Delete an Empty Bucket
```sh
s3cmd rb s3://my-bucket-name
```

### List Files in a Bucket
```sh
s3cmd ls s3://my-bucket-name
```

### Upload a File to a Bucket
```sh
s3cmd put <local_file_path> s3://my-bucket-name/<remote_file_name>
```
Example:
```sh
s3cmd put C:\Users\Username\Desktop\files\mv-test.mp4 s3://test-bucket/upload_test.mp4
```
### Upload a folder to a Bucket
```sh
s3cmd put --recursive <local_file_path> s3://my-bucket-name
```
Example:
```sh
s3cmd put --recursive C:\Users\Username\Desktop\files s3://test-bucket
```

### Download a File from a Bucket
```sh
s3cmd get s3://my-bucket-name/<remote_file_name> <local_file_path>
```
Example:
```sh
s3cmd get s3://test-bucket/upload_test.mp4 C:\Users\Username\Desktop\mv_download.mp4
```

### Delete a File
```sh
s3cmd del s3://my-bucket-name/<remote_file_name>
```

### Batch Upload Files Example
```sh
s3cmd put C:\Users\Username\Desktop\video1.mp4 C:\Users\Username\Desktop\video2.mp4 C:\Users\Username\Desktop\video3.mp4 s3://test-bucket/
```

### Batch Download Files Example
```sh
s3cmd sync s3://test-bucket/video1.mp4 s3://test-bucket/video2.mp4 s3://test-bucket/video3.mp4 C:\Users\Username\Desktop\download_temp\
```
or
```sh
s3cmd get s3://test-bucket/video1.mp4 s3://test-bucket/video2.mp4 s3://test-bucket/video3.mp4 C:\Users\Username\Desktop\download_temp\
```

### Batch Delete Files Example
```sh
s3cmd del s3://test-bucket/video1.mp4 s3://test-bucket/video2.mp4 s3://test-bucket/video3.mp4
```

