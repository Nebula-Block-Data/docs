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

- **id** `string`: The unique identifier for the product.
- **dc_id** `number`: The unique identifier of data center.
- **product_type** : The region where the GPU product is available.
- **region** `string`: Name of the region associated with the product location.
- **price_per_hour** `decimal`: Price value for the GPU per hour.
- **cpu** `number`: The number of CPU cores in the product.
- **ram** `number`: The amount of RAM in gigabytes for the product.
- **gpu** `string`: The GPU model name for the GPU product.
- **gpu_type** `string`: The GPU serial name for the GPU product.
- **gpu_count** `number`: The number of GPUs included in the GPU product.
- **disk_size** `number`: The root disk size of the GPU flavor in gigabytes.
- **ephemeral** `number`: The ephemeral disk storage capacity for the product in gigabytes. Ephemeral storage is a temporary drive that is attached to a virtual machine (VM) during its runtime for storage of the active workload.
- **stock** `number`: The number of GPU product is currently in stock.
- **cycle** `string`: New billing cycle, the default is hourly.
- **is_available** `boolean`: Indicates whether the GPU product is currently available. True indicates that the product is available.

#### status `string`

Indicates the result of the request. `success` signifies success, while `failed` indicates an error.

#### message `string`

A message confirming the successful retrieval of regions.

## Example

#### Request

```bash
curl -X GET '{API_URL}/api/v1/computing/products' \
-H 'Authorization: Bearer {TOKEN/KEY}' \
-H 'Content-Type: application/json'
```

#### Response

```json

{
    "data": {
        "CANADA": {
            "H100": [
                {
                    "id": "fcp66d566c43a9501001256",
                    "dc_id": 1,
                    "product_type": "Container",
                    "region": "CANADA",
                    "price_per_hour": 1.0,
                    "cpu": 16,
                    "ram": 200,
                    "gpu": "H100",
                    "gpu_type": "H100",
                    "gpu_count": 1,
                    "disk_size": 200,
                    "ephemeral": 1500,
                    "stock": 1,
                    "cycle": "hourly",
                    "is_available": true
                },
                {
                    "id": "expde8da3529-f08d-4f86-8456-04094d19fbc4",
                    "dc_id": 2,
                    "product_type": "Virtual Machine",
                    "region": "CANADA",
                    "price_per_hour": 2.627,
                    "cpu": 28,
                    "ram": 180,
                    "gpu": "H100-80G-PCIe",
                    "gpu_type": "H100",
                    "gpu_count": 1,
                    "disk_size": 100,
                    "ephemeral": 750,
                    "stock": 99,
                    "cycle": "hourly",
                    "is_available": true
                },
                {
                    "id": "expd0939da10-8ad6-4edd-9d2d-5d1acb49f136",
                    "dc_id": 2,
                    "product_type": "Virtual Machine",
                    "region": "CANADA",
                    "price_per_hour": 5.247,
                    "cpu": 60,
                    "ram": 360,
                    "gpu": "H100-80G-PCIe",
                    "gpu_type": "H100",
                    "gpu_count": 2,
                    "disk_size": 100,
                    "ephemeral": 1500,
                    "stock": 99,
                    "cycle": "hourly",
                    "is_available": true
                },
                {
                    "id": "expddc5af4c0-8d62-42e1-8970-a76a72db3acc",
                    "dc_id": 2,
                    "product_type": "Virtual Machine",
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
                },
                {
                    "id": "expd170c4fe5-7bf4-431b-a9d3-dd42f77cc19b",
                    "dc_id": 2,
                    "product_type": "Virtual Machine",
                    "region": "CANADA",
                    "price_per_hour": 27.607,
                    "cpu": 192,
                    "ram": 1800,
                    "gpu": "H100-80G-SXM5",
                    "gpu_type": "H100",
                    "gpu_count": 8,
                    "disk_size": 100,
                    "ephemeral": 32000,
                    "stock": 99,
                    "cycle": "hourly",
                    "is_available": true
                }
            ],
            "A100": [
                {
                    "id": "expd4b024f34-c9f3-4c41-ade4-4b56bbe3c64b",
                    "dc_id": 2,
                    "product_type": "Virtual Machine",
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
                    "id": "expde1bf5c0b-83d2-44f9-bb5f-0064f949e7eb",
                    "dc_id": 2,
                    "product_type": "Virtual Machine",
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
                    "id": "expdd5499bbf-07b8-45e2-9756-d9cd8ec52c0f",
                    "dc_id": 2,
                    "product_type": "Virtual Machine",
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
                }
            ],
            "L40": [
                {
                    "id": "expdc33ebb4d-07bc-4e3b-b719-727cd3456629",
                    "dc_id": 2,
                    "product_type": "Virtual Machine",
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
                    "id": "expdb61aafcd-a09f-48a9-b267-cedc57f57d50",
                    "dc_id": 2,
                    "product_type": "Virtual Machine",
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
                    "id": "expd49281edf-6ba4-4c42-b1d9-a05faa9e6233",
                    "dc_id": 2,
                    "product_type": "Virtual Machine",
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
                    "id": "expd039a5631-1247-4dec-8bb5-04e77dc6aa96",
                    "dc_id": 2,
                    "product_type": "Virtual Machine",
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
                    "id": "expd0ce88325-aeb0-48d0-8216-09506b58f1dd",
                    "dc_id": 2,
                    "product_type": "Virtual Machine",
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
                }
            ]
        }
    },
    "message": "All products retrieved successfully",
    "status": "success"
}

```
