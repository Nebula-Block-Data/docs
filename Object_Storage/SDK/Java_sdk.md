# Java AWS S3 SDK Example

This example demonstrates how to connect to an S3 compatible service and list all buckets using the AWS SDK for Java.

## Prerequisites

1. Java Development Kit (JDK) 8 or later
2. **AWS SDK for Java** added as a dependency.

For Maven, add this to your `pom.xml`:
```xml
<dependencies>
    <dependency>
        <groupId>com.amazonaws</groupId>
        <artifactId>aws-java-sdk-s3</artifactId>
        <version>1.12.261</version>
    </dependency>
</dependencies>
```

## Example Code

```java
import com.amazonaws.auth.AWSStaticCredentialsProvider;
import com.amazonaws.auth.BasicAWSCredentials;
import com.amazonaws.client.builder.AwsClientBuilder.EndpointConfiguration;
import com.amazonaws.services.s3.AmazonS3;
import com.amazonaws.services.s3.AmazonS3ClientBuilder;
import com.amazonaws.services.s3.model.*;

import java.io.File;
import java.net.URL;
import java.util.List;

public class S3Example {
    private final AmazonS3 s3Client;

    public S3Example(String accessKey, String secretKey, String endpoint, String region) {
        // Create credentials
        BasicAWSCredentials credentials = new BasicAWSCredentials(accessKey, secretKey);

        // Create endpoint configuration
        EndpointConfiguration endpointConfig = new EndpointConfiguration(endpoint, region);

        // Create S3 client
        this.s3Client = AmazonS3ClientBuilder.standard()
                .withEndpointConfiguration(endpointConfig)
                .withCredentials(new AWSStaticCredentialsProvider(credentials))
                .withPathStyleAccessEnabled(true)  // Required for S3-compatible services
                .build();
    }

    public void listBuckets() {
        try {
            List<Bucket> buckets = s3Client.listBuckets();
            System.out.println("Your buckets:");
            for (Bucket bucket : buckets) {
                System.out.println("* " + bucket.getName());
            }
        } catch (Exception e) {
            System.err.println("Error listing buckets: " + e.getMessage());
        }
    }

    public void uploadFile(String bucketName, String keyName, String filePath) {
        try {
            s3Client.putObject(bucketName, keyName, new File(filePath));
            System.out.println("Successfully uploaded " + keyName + " to " + bucketName);
        } catch (Exception e) {
            System.err.println("Error uploading file: " + e.getMessage());
        }
    }

    public void downloadFile(String bucketName, String keyName, String destinationPath) {
        try {
            S3Object object = s3Client.getObject(bucketName, keyName);
            object.getObjectContent().transferTo(new File(destinationPath).toPath());
            System.out.println("Successfully downloaded " + keyName + " to " + destinationPath);
        } catch (Exception e) {
            System.err.println("Error downloading file: " + e.getMessage());
        }
    }

    public URL generatePresignedUrl(String bucketName, String keyName, int expirationInMinutes) {
        try {
            java.util.Date expiration = new java.util.Date();
            long expTimeMillis = expiration.getTime();
            expTimeMillis += 1000 * 60 * expirationInMinutes;
            expiration.setTime(expTimeMillis);

            GeneratePresignedUrlRequest request = new GeneratePresignedUrlRequest(bucketName, keyName)
                    .withMethod(HttpMethod.GET)
                    .withExpiration(expiration);

            URL url = s3Client.generatePresignedUrl(request);
            System.out.println("Pre-signed URL: " + url.toString());
            return url;
        } catch (Exception e) {
            System.err.println("Error generating pre-signed URL: " + e.getMessage());
            return null;
        }
    }

    public static void main(String[] args) {
        // Replace these with your actual credentials and endpoint
        String accessKey = "your_access_key";
        String secretKey = "your_secret_key";
        String endpoint = "your_endpoint";
        String region = "us-east-1";

        S3Example example = new S3Example(accessKey, secretKey, endpoint, region);

        // List buckets
        example.listBuckets();

        // Upload a file
        example.uploadFile("my-bucket", "test.txt", "local_file.txt");

        // Download a file
        example.downloadFile("my-bucket", "test.txt", "downloaded_file.txt");

        // Generate pre-signed URL (expires in 60 minutes)
        example.generatePresignedUrl("my-bucket", "test.txt", 60);
    }
}
```

## Usage

1. Create a new Java project
2. Add the AWS SDK dependency to your project
3. Copy the example code into a new file
4. Replace the placeholder credentials with your actual credentials
5. Compile and run the program

## Additional Features

The AWS SDK for Java provides many more features for working with S3:
- Multipart uploads
- Server-side encryption
- Access control lists (ACLs)
- Bucket policies
- Object tagging
- Versioning

For more information, refer to the [AWS SDK for Java Documentation](https://docs.aws.amazon.com/sdk-for-java/latest/developer-guide/examples-s3.html) 