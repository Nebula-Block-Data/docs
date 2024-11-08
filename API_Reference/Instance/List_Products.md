---
# title: List Available Products By Product Type
description: List Available Products By Product Type.
---

# List Products

Returns a list of available GPU virtual machine hardware configurations, which include GPUs, CPUs, RAM, and system disk.
These virtual machine configurations are referred to as products.

## HTTP Request

`GET` `{API_URL}/computing/products`

## Response Attributes

#### data `array`

An array containing information about products organized by GPU model and region:
  - `id`: The unique identifier for the product.
  - `dc_id`: The unique identifier of data center.
  - `region`: The region where the GPU product is available.
  - `price_per_hour`: Price value for the GPU per hour.
  - `cpu`: The number of CPU cores in the product.
  - `ram`: The amount of RAM in gigabytes for the product.
  - `gpu`: The GPU model name for the GPU product.
  - `gpu_type`: The GPU serial name for the GPU product.
  - `gpu_count`: The number of GPUs included in the GPU product.
  - `disk_size`: The root disk size of the GPU flavor in gigabytes.
  - `ephemeral`: The ephemeral disk storage capacity for the product in gigabytes. Ephemeral storage is a temporary drive that is attached to a virtual machine (VM) during its runtime for storage of the active workload.
  - `stock`: The number of GPU product is currently in stock.
  - `cycle`: New billing cycle, the default is hourly.
  - `is_available`: Indicates whether the GPU product is currently available. True indicates that the product is available.

#### status `string`

Indicates the result of the request. `success` signifies success, while `failed` indicates an error.

#### message `string`

A message confirming the successful retrieval of regions.

## Example

#### Request

```bash
curl -X GET '{API_URL}/computing/products' \
-H 'Authorization: Bearer {TOKEN/KEY}' \
-H 'Content-Type: application/json'
```

#### Response

```json
{
    "data": {
        "CANADA": {
            "Nvidia H100": [
                {
                    "id": 1,
                    "dc_id": 1,
                    "region": "CANADA",
                    "price_per_hour": 1.0,
                    "cpu": 16,
                    "ram": 200,
                    "gpu": "Nvidia H100",
                    "gpu_type": "Nvidia H100",
                    "gpu_count": 1,
                    "disk_size": 200,
                    "ephemeral": 1500,
                    "stock": 1,
                    "cycle": null,
                    "is_available": true
                }
            ],
            "A100": [
                {
                    "id": 59556,
                    "dc_id": 2,
                    "region": "CANADA",
                    "price_per_hour": 1.867,
                    "cpu": 28,
                    "ram": 120,
                    "gpu": "A100-80G-PCIe",
                    "gpu_type": "A100",
                    "gpu_count": 1,
                    "disk_size": 100,
                    "ephemeral": 750,
                    "stock": 99,
                    "cycle": "hourly",
                    "is_available": true
                },
                {
                    "id": 59557,
                    "dc_id": 2,
                    "region": "CANADA",
                    "price_per_hour": 3.727,
                    "cpu": 60,
                    "ram": 240,
                    "gpu": "A100-80G-PCIe",
                    "gpu_type": "A100",
                    "gpu_count": 2,
                    "disk_size": 100,
                    "ephemeral": 1500,
                    "stock": 99,
                    "cycle": "hourly",
                    "is_available": true
                },
                {
                    "id": 59558,
                    "dc_id": 2,
                    "region": "CANADA",
                    "price_per_hour": 7.447,
                    "cpu": 124,
                    "ram": 480,
                    "gpu": "A100-80G-PCIe",
                    "gpu_type": "A100",
                    "gpu_count": 4,
                    "disk_size": 100,
                    "ephemeral": 3200,
                    "stock": 99,
                    "cycle": "hourly",
                    "is_available": true
                },
                {
                    "id": 59559,
                    "dc_id": 2,
                    "region": "CANADA",
                    "price_per_hour": 14.887,
                    "cpu": 252,
                    "ram": 1440,
                    "gpu": "A100-80G-PCIe",
                    "gpu_type": "A100",
                    "gpu_count": 8,
                    "disk_size": 100,
                    "ephemeral": 6500,
                    "stock": 99,
                    "cycle": "hourly",
                    "is_available": true
                },
                {
                    "id": 59560,
                    "dc_id": 2,
                    "region": "CANADA",
                    "price_per_hour": 15.447,
                    "cpu": 252,
                    "ram": 1920,
                    "gpu": "A100-80G-PCIe-NVLink",
                    "gpu_type": "A100",
                    "gpu_count": 8,
                    "disk_size": 100,
                    "ephemeral": 6500,
                    "stock": 99,
                    "cycle": "hourly",
                    "is_available": true
                }
            ],
            "H100": [
                {
                    "id": 59561,
                    "dc_id": 2,
                    "region": "CANADA",
                    "price_per_hour": 21.527,
                    "cpu": 252,
                    "ram": 1440,
                    "gpu": "H100-80G-PCIe-NVLink",
                    "gpu_type": "H100",
                    "gpu_count": 8,
                    "disk_size": 100,
                    "ephemeral": 6500,
                    "stock": 99,
                    "cycle": "hourly",
                    "is_available": true
                }
            ],
            "L40": [
                {
                    "id": 59562,
                    "dc_id": 2,
                    "region": "CANADA",
                    "price_per_hour": 1.387,
                    "cpu": 28,
                    "ram": 58,
                    "gpu": "L40",
                    "gpu_type": "L40",
                    "gpu_count": 1,
                    "disk_size": 100,
                    "ephemeral": 725,
                    "stock": 99,
                    "cycle": "hourly",
                    "is_available": true
                },
                {
                    "id": 59563,
                    "dc_id": 2,
                    "region": "CANADA",
                    "price_per_hour": 2.767,
                    "cpu": 60,
                    "ram": 116,
                    "gpu": "L40",
                    "gpu_type": "L40",
                    "gpu_count": 2,
                    "disk_size": 100,
                    "ephemeral": 1550,
                    "stock": 99,
                    "cycle": "hourly",
                    "is_available": true
                },
                {
                    "id": 59564,
                    "dc_id": 2,
                    "region": "CANADA",
                    "price_per_hour": 5.527,
                    "cpu": 124,
                    "ram": 232,
                    "gpu": "L40",
                    "gpu_type": "L40",
                    "gpu_count": 4,
                    "disk_size": 100,
                    "ephemeral": 3200,
                    "stock": 99,
                    "cycle": "hourly",
                    "is_available": true
                },
                {
                    "id": 59565,
                    "dc_id": 2,
                    "region": "CANADA",
                    "price_per_hour": 11.047,
                    "cpu": 252,
                    "ram": 464,
                    "gpu": "L40",
                    "gpu_type": "L40",
                    "gpu_count": 8,
                    "disk_size": 100,
                    "ephemeral": 6500,
                    "stock": 99,
                    "cycle": "hourly",
                    "is_available": true
                }
            ],
            "RTX": [
                {
                    "id": 59566,
                    "dc_id": 2,
                    "region": "CANADA",
                    "price_per_hour": 0.697,
                    "cpu": 28,
                    "ram": 58,
                    "gpu": "RTX-A6000",
                    "gpu_type": "RTX",
                    "gpu_count": 1,
                    "disk_size": 100,
                    "ephemeral": 0,
                    "stock": 99,
                    "cycle": "hourly",
                    "is_available": true
                },
                {
                    "id": 59567,
                    "dc_id": 2,
                    "region": "CANADA",
                    "price_per_hour": 1.387,
                    "cpu": 60,
                    "ram": 116,
                    "gpu": "RTX-A6000",
                    "gpu_type": "RTX",
                    "gpu_count": 2,
                    "disk_size": 100,
                    "ephemeral": 200,
                    "stock": 99,
                    "cycle": "hourly",
                    "is_available": true
                },
                {
                    "id": 59568,
                    "dc_id": 2,
                    "region": "CANADA",
                    "price_per_hour": 2.767,
                    "cpu": 124,
                    "ram": 232,
                    "gpu": "RTX-A6000",
                    "gpu_type": "RTX",
                    "gpu_count": 4,
                    "disk_size": 100,
                    "ephemeral": 650,
                    "stock": 99,
                    "cycle": "hourly",
                    "is_available": true
                },
                {
                    "id": 59569,
                    "dc_id": 2,
                    "region": "CANADA",
                    "price_per_hour": 5.527,
                    "cpu": 252,
                    "ram": 464,
                    "gpu": "RTX-A6000",
                    "gpu_type": "RTX",
                    "gpu_count": 8,
                    "disk_size": 100,
                    "ephemeral": 1400,
                    "stock": 99,
                    "cycle": "hourly",
                    "is_available": true
                }
            ]
        }
    },
    "message": "All products retrieved successfully",
    "status": "success"
}
```