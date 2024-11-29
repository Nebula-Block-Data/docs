---
# title: Delete GPU Instances
description: Delete GPU Instances.
---

# Delete GPU Instance

Permanently delete an instance by specifying the instance ID in the path to delete the selected instance.

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

A description of the status of the request.

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
    "message": "Instances deleted successfully",
    "status": "success"
}

```
