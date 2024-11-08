---
# title: List Available OS Images
description: List Available OS Images.
---

# List Images

Returns a list of all available operating system (OS) images, providing details about each image's corresponding virtual machine operating system.

## HTTP Request

`GET` `{API_URL}/computing/images`

## Response Attributes

#### data `array`

An array containing information about operating system images:

- `id`: The unique identifier of the operating system image.
- `dc_id`: The unique identifier of data center.
- `dc_region_id`: The unique identifier of the data center region.
- `os_id`: The unique identifier of the operating system image.
- `os_name`: Name of the operating system.
- `os_type`: The operating system brand.
- `region`: Name of the region associated with the operating system image.

#### status `string`

Indicates the result of the request. `success` signifies success, while `failed` indicates an error.

#### message `string`

A message confirming the successful retrieval of regions.

## Example

#### Request

```bash
curl -X GET '{API_URL}/computing/images' \
-H 'Authorization: Bearer {TOKEN/KEY}' \
-H 'Content-Type: application/json'
```

#### Response

```json

{
    "data": {
        "CANADA": [
            {
                "id": 1,
                "dc_id": 1,
                "dc_region_id": "66d566ba6a7771001256d6e2",
                "os_id": "987766c93a9501001256d804",
                "os_name": "Ubuntu Server 22.04 LTS",
                "os_type": "Ubuntu",
                "region": "CANADA"
            },
            {
                "id": 42654,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e4",
                "os_id": "66d566c93a9501001256d810",
                "os_name": "Ubuntu Server 22.04 LTS R535 CUDA 12.2",
                "os_type": "Ubuntu",
                "region": "CANADA"
            }
        ],
        "NORWAY": [
            {
                "id": 42643,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e2",
                "os_id": "66d566c93a9501001256d804",
                "os_name": "Windows Server 2022",
                "os_type": "Windows",
                "region": "NORWAY"
            },
            {
                "id": 42644,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e2",
                "os_id": "66d566c93a9501001256d806",
                "os_name": "Windows Server 2019",
                "os_type": "Windows",
                "region": "NORWAY"
            }
        ]
    },
    "message": "All OS retrieved successfully",
    "status": "success"
}

```
