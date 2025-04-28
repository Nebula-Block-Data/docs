# Java AWS S3 SDK Example

This example demonstrates how to connect to an S3 compatible service and list all buckets using the AWS SDK for Java.

## Prerequisites

Before running the code, ensure you have the following:

1. **Java Development Kit (JDK)** installed.
2. **AWS SDK for Java** added as a dependency.
3. Replace `YOUR_ACCESS_KEY` and `YOUR_SECRET_KEY` with your actual AWS credentials.

## Maven Dependency

If you're using Maven, you need to add the following dependency in your `pom.xml`:

```xml
<dependency>
    <groupId>com.amazonaws</groupId>
    <artifactId>aws-java-sdk-s3</artifactId>
    <version>1.12.664</version>
</dependency>
```

## Java Code

```java
import com.amazonaws.auth.AWSStaticCredentialsProvider;
import com.amazonaws.auth.BasicAWSCredentials;
import com.amazonaws.client.builder.AwsClientBuilder;
import com.amazonaws.services.s3.AmazonS3;
import com.amazonaws.services.s3.AmazonS3ClientBuilder;
import com.amazonaws.services.s3.model.Bucket;

import java.util.List;

public class Main {
    public static void main(String[] args) {
        // S3 credentials and endpoint
        String accessKey = "YOUR_ACCESS_KEY"; // Replace with your access key
        String secretKey = "YOUR_SECRET_KEY"; // Replace with your secret key
        String endpoint = "HOST_NAME" //Use the Hostname from the Details page.
        String region = "US";

        // Create S3 client
        AmazonS3 s3 = AmazonS3ClientBuilder.standard()
            .withEndpointConfiguration(new AwsClientBuilder.EndpointConfiguration(endpoint, region))
            .withCredentials(new AWSStaticCredentialsProvider(new BasicAWSCredentials(accessKey, secretKey)))
            .withPathStyleAccessEnabled(true)
            .build();

        try {
            List<Bucket> buckets = s3.listBuckets();
            System.out.println("Buckets:");
            for (Bucket bucket : buckets) {
                System.out.println("  - " + bucket.getName());
            }
        } catch (Exception e) {
            System.err.println("Error: " + e.getMessage());
        }
    }
}
```

## Explanation

### Steps in the Code

1. **Credentials**: 
   The program uses `BasicAWSCredentials` to provide the access key and secret key. Make sure to replace `YOUR_ACCESS_KEY` and `YOUR_SECRET_KEY` with your actual credentials.

2. **Client Configuration**: 
   The `AmazonS3ClientBuilder` is configured with the endpoint and region of the S3-compatible service. The `.withPathStyleAccessEnabled(true)` ensures path-style access to the buckets.

3. **List Buckets**: 
   The `listBuckets` method is called on the `AmazonS3` client to retrieve all the available buckets. These buckets are then printed to the console.

4. **Error Handling**: 
   If an error occurs during the process, it is caught in the `catch` block, and the error message is printed.

## Run the Code

To run the program, you can compile and execute it as a standard Java application. Make sure to have the AWS SDK for Java dependency correctly added to your project.

---

**Note**: Ensure that you replace the placeholders for access key and secret key with your own credentials. These credentials should be securely stored and not hardcoded in production applications.
