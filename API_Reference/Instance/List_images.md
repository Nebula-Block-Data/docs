---
# title: List Available OS Images
description: List Available OS Images.
---

# List Images

Returns a list of all available operating system (OS) images, providing details about each image's corresponding virtual machine operating system.

## HTTP Request

`GET` `{API_URL}/api/v1/computing/images`

## Response Attributes

### `data`

**Type**: Array  

An array containing information about operating system images:

- **id** `number`: The unique identifier of the operating system image.
- **dc_id** `number`: The unique identifier of data center.
- **dc_region_id** `string`: The unique identifier of the data center region.
- **os_id** `string`: The unique identifier of the operating system image.
- **os_name** `string`: Name of the operating system.
- **os_type** `string`: The operating system brand.
- **region** `string`: Name of the region associated with the operating system image.

### `message`

**Type**: String  
A message confirming the successful retrieval of images.

### `status`

**Type**: String  
Indicates the result of the request.  
**"success"** signifies success, while **"failed"** indicates an error.

## Example

### Request

```bash
curl -X GET '{API_URL}/api/v1/computing/images' \
-H 'Authorization: Bearer {ACCESS_TOKEN}' \
-H 'Content-Type: application/json'
```

### Response

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
            },
            {
                "id": 42655,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e4",
                "os_id": "66d566c93a9501001256d812",
                "os_name": "Ubuntu Server 22.04 LTS (Jammy Jellyfish)",
                "os_type": "Ubuntu",
                "region": "CANADA"
            },
            {
                "id": 42656,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e4",
                "os_id": "66d566c93a9501001256d814",
                "os_name": "Ubuntu Server 20.04 LTS R535 CUDA 12.2",
                "os_type": "Ubuntu",
                "region": "CANADA"
            },
            {
                "id": 42657,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e4",
                "os_id": "66d566c93a9501001256d816",
                "os_name": "Ubuntu Server 20.04 LTS (Focal Fossa)",
                "os_type": "Ubuntu",
                "region": "CANADA"
            },
            {
                "id": 42658,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e4",
                "os_id": "66d566c93a9501001256d81c",
                "os_name": "Windows Server 2022",
                "os_type": "Windows",
                "region": "CANADA"
            },
            {
                "id": 42659,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e4",
                "os_id": "66d566c93a9501001256d81e",
                "os_name": "Windows Server 2019",
                "os_type": "Windows",
                "region": "CANADA"
            },
            {
                "id": 42660,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e4",
                "os_id": "66d566c93a9501001256d822",
                "os_name": "Windows 10 Pro",
                "os_type": "Windows",
                "region": "CANADA"
            },
            {
                "id": 42661,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e4",
                "os_id": "66fb14345c85bc0011042734",
                "os_name": "Ubuntu Server 22.04 LTS R550 CUDA 12.4",
                "os_type": "Ubuntu",
                "region": "CANADA"
            },
            {
                "id": 42662,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e4",
                "os_id": "66fb14345c85bc0011042736",
                "os_name": "Ubuntu Server 22.04 LTS R535 CUDA 12.2 with Docker",
                "os_type": "Ubuntu",
                "region": "CANADA"
            },
            {
                "id": 42663,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e4",
                "os_id": "66fb14345c85bc0011042738",
                "os_name": "Ubuntu Server 20.04 LTS R550 CUDA 12.4 with Docker",
                "os_type": "Ubuntu",
                "region": "CANADA"
            },
            {
                "id": 42664,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e4",
                "os_id": "66fb14345c85bc001104273a",
                "os_name": "Ubuntu Server 22.04 LTS R550 CUDA 12.4 with Docker",
                "os_type": "Ubuntu",
                "region": "CANADA"
            },
            {
                "id": 42665,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e4",
                "os_id": "66fb14345c85bc001104273c",
                "os_name": "Ubuntu Server 20.04 LTS R550 CUDA 12.4",
                "os_type": "Ubuntu",
                "region": "CANADA"
            },
            {
                "id": 42666,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e4",
                "os_id": "66fb14345c85bc001104273e",
                "os_name": "Ubuntu Server 20.04 LTS R535 CUDA 12.2 with Docker",
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
            },
            {
                "id": 42645,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e2",
                "os_id": "66d566c93a9501001256d808",
                "os_name": "Windows 11 Pro",
                "os_type": "Windows",
                "region": "NORWAY"
            },
            {
                "id": 42646,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e2",
                "os_id": "66d566c93a9501001256d80a",
                "os_name": "Windows 10 Pro",
                "os_type": "Windows",
                "region": "NORWAY"
            },
            {
                "id": 42647,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e2",
                "os_id": "66d566c93a9501001256d80c",
                "os_name": "Debian 10",
                "os_type": "Debian",
                "region": "NORWAY"
            },
            {
                "id": 42648,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e2",
                "os_id": "66d566c93a9501001256d80e",
                "os_name": "CentOS 9",
                "os_type": "CentOS",
                "region": "NORWAY"
            },
            {
                "id": 42649,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e2",
                "os_id": "66d566c93a9501001256d818",
                "os_name": "Ubuntu Server 22.04 LTS R535 CUDA 12.2",
                "os_type": "Ubuntu",
                "region": "NORWAY"
            },
            {
                "id": 42650,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e2",
                "os_id": "66d566c93a9501001256d81a",
                "os_name": "Ubuntu Server 22.04 LTS",
                "os_type": "Ubuntu",
                "region": "NORWAY"
            },
            {
                "id": 42651,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e2",
                "os_id": "66d566c93a9501001256d820",
                "os_name": "Fedora 36",
                "os_type": "Fedora",
                "region": "NORWAY"
            },
            {
                "id": 42652,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e2",
                "os_id": "66d566c93a9501001256d824",
                "os_name": "Ubuntu Server 20.04 LTS R535 CUDA 12.2",
                "os_type": "Ubuntu",
                "region": "NORWAY"
            },
            {
                "id": 42653,
                "dc_id": 2,
                "dc_region_id": "66d566ba3a9501001256d6e2",
                "os_id": "66d566c93a9501001256d826",
                "os_name": "Ubuntu Server 20.04 LTS",
                "os_type": "Ubuntu",
                "region": "NORWAY"
            }
        ]
    },
    "message": "All OS retrieved successfully",
    "status": "success"
}

```
