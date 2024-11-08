---
# title: Create GPU Instance
description: Reboot Instance.
---

# User Instance Details

Initiates a hard reboot for a virtual machine, simulating the process of unplugging and rebooting a physical machine. Provide the virtual machine ID in the path to execute a hard reboot for the specified virtual machine.

## HTTP Request

`GET` `{API_URL}/computing/instance/{id}/reboot`

## Path parameters

| Parameters     | Requirements      | Type       | Description      |
|---------------|--------------------|----------------|----------------|
| id      | Required    | `number`       | The unique identifier of the instance. `{id} comes from <List User Instances API>` |

## Response Attributes

#### message `string`

  A message confirming the successful retrieval of regions.

#### status `string`

  Indicates the result of the request.  
  **success** signifies success, while **failed** indicates an error.

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
