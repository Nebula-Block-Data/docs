---
title: List Available Products By Product Type
description: List Available Products By Product Type.
---

# List Products

Returns a list of available GPU virtual machine hardware configurations, comprising combinations of GPUs, CPUs, RAM, and system disk. These virtual machine configurations are referred to as products.

## HTTP Request

`GET` `{API_URL}/api/v1/computing/products`

## Response Attributes

### `data`

- **Type**: Array  
  An array containing information about products organized by GPU model and region:
  - **id** `number`: The unique identifier for the product.
  - **dc_id** `number`: The unique identifier for the vendor.
  - **region** `string`: The region where the GPU product is available.
  - **price_per_hour** `decimal`: Price value for the GPU per hour.
  - **cpu** `number`: The number of CPU cores in the product.
  - **ram** `number`: The amount of RAM in gigabytes for the product.
  - **gpu** `string`: The GPU model name for the GPU product.
  - **gpu_type** `string`: The GPU serial name for the GPU product.
  - **gpu_count**: The number of GPUs included in the GPU product.
  - **disk_size** `number`: The root disk size of the GPU flavor in gigabytes.
  - **ephemeral** `number`: The ephemeral disk storage capacity for the product in gigabytes. Ephemeral storage is a temporary drive that is attached to a virtual machine (VM) during its runtime for storage of the active workload.
  - **stock** `number`: The number of GPU product is currently in stock.
  - **cycle** `string`: New billing cycle, the default is hourly.
  - **is_available** `boolean`: Indicates whether the GPU product is currently available. True indicates that the product is available.

### `message`

- **Type**: String  
  A message confirming the successful retrieval of regions.

### `status`

- **Type**: String  
  Indicates the result of the request.  
  **success** signifies success, while **failed** indicates an error.

## Example

### Request

```bash
curl -X GET '{API_URL}/api/v1/computing/products' \
-H 'Authorization: Bearer {ACCESS_TOKEN}' \
-H 'Content-Type: application/json'
```

### Response

```json
{
    "data": {
        "CANADA": {
            "Nvidia H100": [
                {
                    "id": 1,
                    "vendor_id": 1,
                    "external_product_id": "59",
                    "name": "T2az.8xlarge",
                    "product_type": "AI GPU",
                    "description": "Nvidia H100 · 12 vCPU · 128 GiB",
                    "nbfs_region": "CANADA",
                    "vendor_region_id": "66d777c93a9501001256d804",
                    "vendor_region_name": "CANADA-1",
                    "price_per_hour": 1.0,
                    "cpu": 16,
                    "ram": 200,
                    "gpu": "Nvidia H100",
                    "gpu_type": "Nvidia H100",
                    "gpu_count": 1,
                    "disk_size": 200,
                    "ephemeral": 1500,
                    "stock": 1,
                    "bandwidth": 300,
                    "is_available": true,
                    "created_at": "1729085500"
                }
            ],
            "A100": [
                {
                    "id": 58401,
                    "vendor_id": 2,
                    "external_product_id": "66d566c43a9501001256d7ab",
                    "name": "n3-A100x1",
                    "nbfs_region": "CANADA",
                    "vendor_region_id": "66d566ba3a9501001256d6e4",
                    "vendor_region_name": "CANADA-1",
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
                    "is_available": true,
                    "created_at": "1730479999"
                },
                {
                    "id": 58402,
                    "vendor_id": 2,
                    "external_product_id": "66d566c43a9501001256d7ad",
                    "name": "n3-A100x2",
                    "nbfs_region": "CANADA",
                    "vendor_region_id": "66d566ba3a9501001256d6e4",
                    "vendor_region_name": "CANADA-1",
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
                    "is_available": true,
                    "created_at": "1730479999"
                },
                {
                    "id": 58403,
                    "vendor_id": 2,
                    "external_product_id": "66d566c43a9501001256d7af",
                    "name": "n3-A100x4",
                    "nbfs_region": "CANADA",
                    "vendor_region_id": "66d566ba3a9501001256d6e4",
                    "vendor_region_name": "CANADA-1",
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
                    "is_available": true,
                    "created_at": "1730479999"
                },
                {
                    "id": 58404,
                    "vendor_id": 2,
                    "external_product_id": "66d566c43a9501001256d7b1",
                    "name": "n3-A100x8",
                    "nbfs_region": "CANADA",
                    "vendor_region_id": "66d566ba3a9501001256d6e4",
                    "vendor_region_name": "CANADA-1",
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
                    "is_available": true,
                    "created_at": "1730479999"
                },
                {
                    "id": 58405,
                    "vendor_id": 2,
                    "external_product_id": "66d566c43a9501001256d7c1",
                    "name": "n2-A100x8-NVLink-v2",
                    "nbfs_region": "CANADA",
                    "vendor_region_id": "66d566ba3a9501001256d6e4",
                    "vendor_region_name": "CANADA-1",
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
                    "is_available": true,
                    "created_at": "1730479999"
                }
            ],
            "H100": [
                {
                    "id": 58406,
                    "vendor_id": 2,
                    "external_product_id": "66d566c43a9501001256d7b7",
                    "name": "n3-H100x8-NVLink",
                    "nbfs_region": "CANADA",
                    "vendor_region_id": "66d566ba3a9501001256d6e4",
                    "vendor_region_name": "CANADA-1",
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
                    "is_available": true,
                    "created_at": "1730479999"
                }
            ],
            "L40": [
                {
                    "id": 58407,
                    "vendor_id": 2,
                    "external_product_id": "66d566c43a9501001256d7b9",
                    "name": "n3-L40x1",
                    "nbfs_region": "CANADA",
                    "vendor_region_id": "66d566ba3a9501001256d6e4",
                    "vendor_region_name": "CANADA-1",
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
                    "is_available": true,
                    "created_at": "1730479999"
                },
                {
                    "id": 58408,
                    "vendor_id": 2,
                    "external_product_id": "66d566c43a9501001256d7bb",
                    "name": "n3-L40x2",
                    "nbfs_region": "CANADA",
                    "vendor_region_id": "66d566ba3a9501001256d6e4",
                    "vendor_region_name": "CANADA-1",
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
                    "is_available": true,
                    "created_at": "1730479999"
                },
                {
                    "id": 58409,
                    "vendor_id": 2,
                    "external_product_id": "66d566c43a9501001256d7bd",
                    "name": "n3-L40x4",
                    "nbfs_region": "CANADA",
                    "vendor_region_id": "66d566ba3a9501001256d6e4",
                    "vendor_region_name": "CANADA-1",
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
                    "is_available": true,
                    "created_at": "1730479999"
                },
                {
                    "id": 58410,
                    "vendor_id": 2,
                    "external_product_id": "66d566c43a9501001256d7bf",
                    "name": "n3-L40x8",
                    "nbfs_region": "CANADA",
                    "vendor_region_id": "66d566ba3a9501001256d6e4",
                    "vendor_region_name": "CANADA-1",
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
                    "is_available": true,
                    "created_at": "1730479999"
                }
            ],
            "RTX": [
                {
                    "id": 58411,
                    "vendor_id": 2,
                    "external_product_id": "66d566c43a9501001256d7e1",
                    "name": "n3-RTX-A6000x1",
                    "nbfs_region": "CANADA",
                    "vendor_region_id": "66d566ba3a9501001256d6e4",
                    "vendor_region_name": "CANADA-1",
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
                    "is_available": true,
                    "created_at": "1730479999"
                },
                {
                    "id": 58412,
                    "vendor_id": 2,
                    "external_product_id": "66d566c43a9501001256d7e3",
                    "name": "n3-RTX-A6000x2",
                    "nbfs_region": "CANADA",
                    "vendor_region_id": "66d566ba3a9501001256d6e4",
                    "vendor_region_name": "CANADA-1",
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
                    "is_available": true,
                    "created_at": "1730479999"
                },
                {
                    "id": 58413,
                    "vendor_id": 2,
                    "external_product_id": "66d566c43a9501001256d7e5",
                    "name": "n3-RTX-A6000x4",
                    "nbfs_region": "CANADA",
                    "vendor_region_id": "66d566ba3a9501001256d6e4",
                    "vendor_region_name": "CANADA-1",
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
                    "is_available": true,
                    "created_at": "1730479999"
                },
                {
                    "id": 58414,
                    "vendor_id": 2,
                    "external_product_id": "66d566c43a9501001256d7e7",
                    "name": "n3-RTX-A6000x8",
                    "nbfs_region": "CANADA",
                    "vendor_region_id": "66d566ba3a9501001256d6e4",
                    "vendor_region_name": "CANADA-1",
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
                    "is_available": true,
                    "created_at": "1730479999"
                }
            ]
        }
    },
    "message": "All products retrieved successfully",
    "status": "success"
}
```
