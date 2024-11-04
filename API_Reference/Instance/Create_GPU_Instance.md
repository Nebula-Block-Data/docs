---
title: Create GPU Instance
description: Create GPU Instance.
---

# Create GPU Instance

Creates one virtual machines with the specified custom configuration and features provided in the request body.

## HTTP Request

`POST` `{API_URL}/computing/instance`

## Body parameters

| Parameters     | Requirements      | Type       | Description      |
|---------------|--------------------|----------------|----------------|
| instance_name | Required    | `string`       | Name of the virtual machine being deployed.  |
|product_id| Required| `number`| The unique identifier of products. `The product_id comes from <List Products API>`.|
| image_id      | Required    | `number`       | The unique identifier of the operating system image to be installed on your virtual machine. Use the GET /images endpoint to retrieve a list of images offered by API.  |
| ssh_key_id    | Required    | `number`       | The unique identifier of the SSH keypair to be used in gaining secure access to the virtual machine.|

## Response Attributes

### `message`

- **Type**: String  
  A message confirming the successful retrieval of regions.

### `status`

- **Type**: String  
  Indicates the result of the request.  
  **success** signifies success, while **failed** indicates an error.

## Example

### Request

```bash
curl -X POST '{API_URL}/computing/instance' \
-H 'Authorization: Bearer {ACCESS_TOKEN}' \
-H 'Content-Type: application/json' \
-d '{
    "instance_name":"testname",
    "product_id":5335
    "image_id":1,
    "ssh_key_id":2 (your ssh key id of Nebulablock portal)
}'
```

### Response

```json
{
    "message": "Instance created successfully",
    "status": "success"
}

```
