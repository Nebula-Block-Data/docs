---
# title: Create GPU Instance
description: Create GPU Instance.
---

# Create GPU Instance

Creates an instance with the specified custom configuration and features provided in the request body.

## HTTP Request

`POST` `{API_URL}/computing/instance`

## Body parameters

| Parameters     | Requirements      | Type       | Description      |
|---------------|--------------------|----------------|----------------|
| instance_name | Required    | `string`       | Name of the virtual machine being deployed.  |
|product_id| Required| `string`| The unique identifier of products. `The product_id comes from <List Products API>`.|
| image_id      | Required    | `string`       | The unique identifier of the operating system image to be installed on your virtual machine. Use the GET /images endpoint to retrieve a list of images offered by API.  |
| ssh_key_id    | Required    | `number`       | The unique identifier of the SSH keypair to be used in gaining secure access to the virtual machine.|

> **NOTE:** `image_id` and `product_id` must be from the same data center (`dc_id`) and region. 

## Response Attributes

#### message `string`

A description of the status of the request.

#### status `string`

Indicates the result of the request. **success** signifies success, while **failed** indicates an error.

## Example

#### Request

```bash
curl -X POST '{API_URL}/computing/instance' \
-H 'Authorization: Bearer {TOKEN/KEY}' \
-H 'Content-Type: application/json' \
-d '{
    "instance_name":"testname",
    "product_id":"fcp66d566c43a9501001256",
    "image_id":"fcp66d566c93a95010012",
    "ssh_key_id":2
}'
```

#### Response

```json
{
    "message": "Instance created successfully",
    "status": "success"
}

```
