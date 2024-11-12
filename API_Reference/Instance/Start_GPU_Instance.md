---
# title: Create GPU Instance
description: Start Instance.
---

# User Instance Details

Initiates the startup of a virtual machine. Supply the virtual machine ID in the path to initiate the starting of the specified virtual machine.

## HTTP Request

`GET` `{API_URL}/computing/instance/{id}/start`

## Path parameters

| Parameters     | Requirements      | Type       | Description      |
|---------------|--------------------|----------------|----------------|
| id      | Required    | `string`       | The unique identifier of the instance. `{id} comes from <List User Instances API>` |

## Response Attributes

#### message `string`

  A message confirming the successful retrieval of regions.

#### status `string`

  Indicates the result of the request.  
  **success** signifies success, while **failed** indicates an error.

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
