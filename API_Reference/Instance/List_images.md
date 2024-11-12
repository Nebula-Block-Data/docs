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

- **id** `string`: The unique identifier of the operating system image.
- **dc_id** `number`: The unique identifier of data center.
- **os_name** `string`: Name of the operating system.
- **os_type** `string`: The operating system brand.
- **region** `string`: Name of the region associated with the operating system image.

#### status `string`

Indicates the result of the request. `success` signifies success, while `failed` indicates an error.

#### message `string`

A message confirming the successful retrieval of regions.

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
            },
            {
                "id": "exos7d786427-35dc-4517-94f6-26a57fa5597e",
                "dc_id": 2,
                "os_name": "Ubuntu Server 22.04 LTS (Jammy Jellyfish)",
                "os_type": "Ubuntu",
                "region": "CANADA"
            },
            {
                "id": "exos27c75a98-a95e-4d30-90c2-586c28bbca22",
                "dc_id": 2,
                "os_name": "Ubuntu Server 20.04 LTS R535 CUDA 12.2",
                "os_type": "Ubuntu",
                "region": "CANADA"
            },
            {
                "id": "exos1f077dca-89c0-4460-969c-6da3dc411e4f",
                "dc_id": 2,
                "os_name": "Ubuntu Server 20.04 LTS (Focal Fossa)",
                "os_type": "Ubuntu",
                "region": "CANADA"
            },
            {
                "id": "exos8de46794-c4db-451f-9dc2-c3dc07a50da2",
                "dc_id": 2,
                "os_name": "Ubuntu Server 22.04 LTS R550 CUDA 12.4",
                "os_type": "Ubuntu",
                "region": "CANADA"
            },
            {
                "id": "exoseee32e5d-9e41-449a-926b-23e627cabfb2",
                "dc_id": 2,
                "os_name": "Ubuntu Server 22.04 LTS R535 CUDA 12.2 with Docker",
                "os_type": "Ubuntu",
                "region": "CANADA"
            },
            {
                "id": "exos3fc74028-8ef5-419d-8c89-7fd058c5b8bf",
                "dc_id": 2,
                "os_name": "Ubuntu Server 20.04 LTS R550 CUDA 12.4 with Docker",
                "os_type": "Ubuntu",
                "region": "CANADA"
            },
            {
                "id": "exos3d6d552c-0917-450b-876b-5e66f00de003",
                "dc_id": 2,
                "os_name": "Ubuntu Server 22.04 LTS R550 CUDA 12.4 with Docker",
                "os_type": "Ubuntu",
                "region": "CANADA"
            },
            {
                "id": "exosc60cba64-feff-4597-ad1c-1fc561230796",
                "dc_id": 2,
                "os_name": "Ubuntu Server 20.04 LTS R550 CUDA 12.4",
                "os_type": "Ubuntu",
                "region": "CANADA"
            },
            {
                "id": "exos1a4d169d-2c60-48d3-ad00-cde532f3e910",
                "dc_id": 2,
                "os_name": "Ubuntu Server 20.04 LTS R535 CUDA 12.2 with Docker",
                "os_type": "Ubuntu",
                "region": "CANADA"
            }
        ],
        "NORWAY": [
            {
                "id": "exos272cce87-14ec-4582-9a25-17c97221dbdc",
                "dc_id": 2,
                "os_name": "Debian 10",
                "os_type": "Debian",
                "region": "NORWAY"
            },
            {
                "id": "exos071ffabb-b07c-4823-b73f-3fbf3dcf5f96",
                "dc_id": 2,
                "os_name": "CentOS 9",
                "os_type": "CentOS",
                "region": "NORWAY"
            },
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
            },
            {
                "id": "exos2abb0d0b-28ba-4fdb-85c2-4fd207c3885c",
                "dc_id": 2,
                "os_name": "Fedora 36",
                "os_type": "Fedora",
                "region": "NORWAY"
            },
            {
                "id": "exosf7cd3c11-7ced-45e5-a370-15c6b1b4f5a8",
                "dc_id": 2,
                "os_name": "Ubuntu Server 20.04 LTS R535 CUDA 12.2",
                "os_type": "Ubuntu",
                "region": "NORWAY"
            },
            {
                "id": "exos9a17ef0f-b056-4d3d-bd4d-d0a76b42894b",
                "dc_id": 2,
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
