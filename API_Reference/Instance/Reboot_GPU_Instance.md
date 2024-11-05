---
# title: Create GPU Instance
description: Reboot Instance.
---

# User Instance Details

Reboot User Instance.

## HTTP Request

`GET` `{API_URL}/api/v1/computing/instance/{id}/reboot`

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
curl -X GET '{API_URL}/api/v1/computing/instance/{id}/reboot' \
-H 'Authorization: Bearer {ACCESS_TOKEN}' \
-H 'Content-Type: application/json' \

```

### Response

```json
{
    "message": "Instance rebooted successfully",
    "status": "success"
}
```
