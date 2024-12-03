---
# title: Create GPU Instances
description: Stop Instances.
---

# User Instance Details

Shut down an instance. Provide the instance ID in the path to initiate the shutdown process for that instance.

## HTTP Request

`GET` `{API_URL}/computing/instance/{id}/stop`

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
curl -X GET '{API_URL}/computing/instance/{id}/stop' \
-H 'Authorization: Bearer {ACCESS_TOKEN}' \
-H 'Content-Type: application/json' \

```

#### Response

```json
{
    "message": "Instances stopped successfully",
    "status": "success"
}
```
