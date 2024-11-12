---
# title: Delete GPU Instance
description: Delete GPU Instance.
---

# Delete GPU Instance

Permanently deletes a virtual machine. Supply the virtual machine ID in the path to delete that specified virtual machine.

## HTTP Request

`DELETE` `{API_URL}/computing/instance/{id}`

## Path parameters

| Parameters     | Requirements      | Type  | Description      |
|---------------|--------------------|-------|----------------|
| id      | Required    | `string` | The unique identifier of the instance. `{id} comes from <List User Instances API>` |

## Response Attributes

#### status `string`

Indicates the result of the request. `success` signifies success, while `failed` indicates an error.

#### message `string`

A message confirming the successful retrieval of regions.

## Example

#### Request

```bash
curl -X DELETE '{API_URL}/computing/instance/{id}' \
-H 'Authorization: Bearer {TOKEN/KEY}' \
-H 'Content-Type: application/json' \
```

#### Response

```json
{
    "message": "Instance deleted successfully",
    "status": "success"
}

```
