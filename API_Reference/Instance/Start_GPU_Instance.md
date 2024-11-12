---
# title: Create GPU Instance
description: Start Instance.
---

# User Instance Details

Initiates the startup of an instance. Provide the instance ID in the path to start the specified instance.

## HTTP Request

`GET` `{API_URL}/computing/instance/{id}/start`

## Path parameters

| Parameters     | Requirements      | Type       | Description      |
|---------------|--------------------|----------------|----------------|
| id      | Required    | `string`       | The unique identifier of the instance. `{id} comes from <List User Instances API>` |

## Response Attributes

#### message `string`

A description of the status of the request.

#### status `string`

Indicates the result of the request. `success` signifies success, while `failed` indicates an error.

## Example

#### Request

```bash
curl -X GET '{API_URL}/computing/instance/{id}/start' \
-H 'Authorization: Bearer {ACCESS_TOKEN}' \
-H 'Content-Type: application/json' \

```

#### Response

```json
{
    "message": "Instance started successfully",
    "status": "success"
}
```
