# Go AWS SDK Example

This Go program demonstrates how to interact with an S3-compatible service using the AWS SDK for Go. The program lists all available S3 buckets.
Please use aws-sdk-go V1 version as follows.

## Prerequisites

1. Go installed on your system
2. AWS SDK for Go installed. You can get it using:
```bash
go get github.com/aws/aws-sdk-go
```

## Example Code

```go
package main

import (
    "fmt"
    "log"

    "github.com/aws/aws-sdk-go/aws"
    "github.com/aws/aws-sdk-go/aws/credentials"
    "github.com/aws/aws-sdk-go/aws/session"
    "github.com/aws/aws-sdk-go/service/s3"
)

func main() {
    // Replace with your credentials and endpoint
    accessKey := "your_access_key"
    secretKey := "your_secret_key"
    endpoint := "your_endpoint"
    region := "us-east-1" // Use appropriate region

    // Create custom credentials
    creds := credentials.NewStaticCredentials(accessKey, secretKey, "")

    // Create custom AWS config
    config := &aws.Config{
        Credentials:      creds,
        Endpoint:        aws.String(endpoint),
        Region:          aws.String(region),
        S3ForcePathStyle: aws.Bool(true), // Required for S3-compatible services
    }

    // Create session
    sess, err := session.NewSession(config)
    if err != nil {
        log.Fatalf("Failed to create session: %v", err)
    }

    // Create S3 service client
    svc := s3.New(sess)

    // List buckets
    result, err := svc.ListBuckets(nil)
    if err != nil {
        log.Fatalf("Failed to list buckets: %v", err)
    }

    fmt.Println("Buckets:")
    for _, bucket := range result.Buckets {
        fmt.Printf("- %s created on %s\n",
            aws.StringValue(bucket.Name), aws.TimeValue(bucket.CreationDate))
    }
}
```

## Additional Operations

Here are some common operations you can perform with the SDK:

### Upload an Object

```go
func uploadObject(svc *s3.S3, bucket, key string, body io.Reader) error {
    input := &s3.PutObjectInput{
        Bucket: aws.String(bucket),
        Key:    aws.String(key),
        Body:   body,
    }

    _, err := svc.PutObject(input)
    return err
}
```

### Download an Object

```go
func downloadObject(svc *s3.S3, bucket, key string) ([]byte, error) {
    input := &s3.GetObjectInput{
        Bucket: aws.String(bucket),
        Key:    aws.String(key),
    }

    result, err := svc.GetObject(input)
    if err != nil {
        return nil, err
    }
    defer result.Body.Close()

    return ioutil.ReadAll(result.Body)
}
```

### Generate Presigned URL

```go
func generatePresignedURL(svc *s3.S3, bucket, key string, duration time.Duration) (string, error) {
    req, _ := svc.GetObjectRequest(&s3.GetObjectInput{
        Bucket: aws.String(bucket),
        Key:    aws.String(key),
    })

    return req.Presign(duration)
}
```

## Usage

1. Save the code in a file (e.g., `main.go`)
2. Replace the placeholder credentials with your actual credentials
3. Run the program:
```bash
go run main.go
```

For more information, refer to the [AWS SDK for Go Documentation](https://docs.aws.amazon.com/sdk-for-go/api/service/s3/) 