---
# title: List Available OS Images
description: List Available OS Images.
---

# List Images

Return a list of all available operating system images, including details about each image's version and driver, if applicable.

## HTTP Request

`GET` `{API_URL}/computing/images`

## Response Attributes

#### data `array`

An array containing information about operating system images:

- **id** `string`: The unique identifier of the operating system image.
- **dc_id** `number`: The unique identifier of data center.
- **os_name** `string`: Name of the operating system.
- **os_type** `string`: The operating system brand.
- **region** `string`: Name of the region associated with the operating system image.

#### status `string`

Indicates the result of the request. `success` signifies success, while `failed` indicates an error.

#### message `string`

A description of the status of the request.

## Example

#### Request

```bash
curl -X GET '{API_URL}/api/v1/computing/images' \
-H 'Authorization: Bearer {TOKEN/KEY}' \
-H 'Content-Type: application/json'
```

#### Response

```json

{
    "data": {
        "CANADA": [
            {
                "id": "fcp66d566c93a95010012",
                "dc_id": 1,
                "os_name": "Ubuntu Server 22.04 LTS",
                "os_type": "Ubuntu",
                "region": "CANADA"
            },
            {
                "id": "exoscee6e762-1d11-4f65-a7d6-8c0670b603b2",
                "dc_id": 2,
                "os_name": "Ubuntu Server 22.04 LTS R535 CUDA 12.2",
                "os_type": "Ubuntu",
                "region": "CANADA"
            }
        ],
        "NORWAY": [
            {
                "id": "exos60da1d80-a58b-4ff3-8a33-b566b65f3e6e",
                "dc_id": 2,
                "os_name": "Ubuntu Server 22.04 LTS R535 CUDA 12.2",
                "os_type": "Ubuntu",
                "region": "NORWAY"
            },
            {
                "id": "exos63884cc9-2119-43db-b6d5-093fb4036586",
                "dc_id": 2,
                "os_name": "Ubuntu Server 22.04 LTS",
                "os_type": "Ubuntu",
                "region": "NORWAY"
            }
        ]
    },
    "message": "All OS retrieved successfully",
    "status": "success"
}

```
