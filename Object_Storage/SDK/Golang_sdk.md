# Go AWS SDK Example

This Go program demonstrates how to interact with an S3-compatible service using the AWS SDK for Go. The program lists all available S3 buckets.
Please use aws-sdk-go V1 version as follows.

## Prerequisites

To run this program, you'll need:

- Go installed on your machine (https://golang.org/doc/install).
- AWS SDK for Go installed. You can get it using:

  ```bash
  go get github.com/aws/aws-sdk-go
  ```

- Access credentials (Access Key ID and Secret Access Key) for the S3-compatible service you are connecting to.

## Code

```go
package main

import (
	"fmt"
	"log"

	"github.com/aws/aws-sdk-go/aws"
	"github"github.com/aws/aws-sdk-go/aws/credentials"
	"github.com/aws/aws-sdk-go/aws/session"
	"github.com/aws/aws-sdk-go/service/s3"
)

func main() {
	// Set the S3 compatible service information
	accessKey := "YOUR_ACCESS_KEY"
	secretKey := "YOUR_SECRET_KEY"
	endpoint := "HOST_NAME" //Use the Hostname from the Details page.
	region := "US"

	// Create a session
	s3Config := &aws.Config{
		Credentials:      credentials.NewStaticCredentials(accessKey, secretKey, ""),
		Endpoint:         aws.String(endpoint),
		Region:           aws.String(region),
		S3ForcePathStyle: aws.Bool(true), // Use path-style instead of virtual host style
	}

	sess, err := session.NewSession(s3Config)
	if err != nil {
		log.Fatalf("Failed to create session: %v", err)
	}

	// Create S3 service client
	svc := s3.New(sess)

	// List all buckets
	fmt.Println("Attempting to list buckets...")
	result, err := svc.ListBuckets(nil)
	if err != nil {
		log.Fatalf("Failed to list buckets: %v", err)
	}

	fmt.Println("Successfully connected! Current buckets:")
	for _, bucket := range result.Buckets {
		fmt.Printf("  - %s
", *bucket.Name)
	}
}
```

## Explanation

1. **Setting up the S3 Configuration:**
   - The program starts by setting the AWS access key, secret key, and endpoint of the S3-compatible service. The region is also set to `us`.
   - `S3ForcePathStyle` is set to `true` to use path-style addressing rather than virtual host style.

2. **Creating a Session:**
   - A new session is created using the configuration parameters. If the session creation fails, the program logs an error and exits.

3. **Listing Buckets:**
   - The program uses the `ListBuckets` API to retrieve all available buckets. If the request is successful, it prints out the names of the buckets.

## Running the Program

1. Save the above code to a file, for example, `main.go`.
2. Run the program using the following command:

   ```bash
   go run main.go
   ```

3. The output will display the names of the S3 buckets.

### Example Output

```
Attempting to list buckets...
Successfully connected! Current buckets:
  - my-bucket-name-1
  - my-bucket-name-2
  - my-bucket-name-3
```

## Notes

- Make sure your AWS credentials (Access Key and Secret Key) are correctly set.
- The program will list the buckets available at the specified S3-compatible service endpoint.
