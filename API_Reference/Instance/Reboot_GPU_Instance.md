---
# title: Create GPU Instance
description: Reboot Instance.
---

# User Instance Details

Initiate a reboot of an instance. Provide the instance ID in the path to reboot the specified instance.

## HTTP Request

`GET` `{API_URL}/computing/instance/{id}/reboot`

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
curl -X GET '{API_URL}/computing/instance/{id}/reboot' \
-H 'Authorization: Bearer {ACCESS_TOKEN}' \
-H 'Content-Type: application/json' \

```

#### Response

```json
{
    "message": "Instance rebooted successfully",
    "status": "success"
}
```
