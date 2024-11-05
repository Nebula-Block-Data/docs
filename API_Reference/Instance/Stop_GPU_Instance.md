---
# title: Create GPU Instance
description: Stop Instance.
---

# User Instance Details

Shuts down a virtual machine. Provide the virtual machine ID in the path to initiate the shutdown process for the specified virtual machine.

## HTTP Request

`GET` `{API_URL}/api/v1/computing/instance/{id}/stop`

## Path parameters

| Parameters     | Requirements      | Type       | Description      |
|---------------|--------------------|----------------|----------------|
| id      | Required    | `number`       | The unique identifier of the instance. `{id} comes from <List User Instances API>` |

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
curl -X GET '{API_URL}/api/v1/computing/instance/{id}/stop' \
-H 'Authorization: Bearer {ACCESS_TOKEN}' \
-H 'Content-Type: application/json' \

```

### Response

```json
{
    "message": "Instance stopped successfully",
    "status": "success"
}
```
