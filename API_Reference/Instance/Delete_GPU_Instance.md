---
# title: Delete GPU Instance
description: Delete GPU Instance.
---

# Delete GPU Instance

Permanently deletes a virtual machine. Supply the virtual machine ID in the path to delete the specified virtual machine.

## HTTP Request

`Delete` `{API_URL}/computing/instance/{id}`

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
curl -X DELETE '{API_URL}/computing/instance/{id}' \
-H 'Authorization: Bearer {ACCESS_TOKEN}' \
-H 'Content-Type: application/json' \
```

### Response

```json
{
    "message": "Instance deleted successfully",
    "status": "success"
}

```
