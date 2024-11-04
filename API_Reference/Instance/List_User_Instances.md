---
# title: List User Instances
description: List User Instances.
---

# List User Instances

Return a list user instances including virtual machine and serverless products.

## HTTP Request

`GET` `{API_URL}/computing/instances`

## Response Attributes

### `data`

- **Type**: Array  
  An array containing information about products organized by GPU model and region:
  - **id** `number`: The unique identifier for the product.
  - **region** `string`: The region where the GPU product is available.
  - **instance_type** `string`: The type of instance,like GPU and CPU.
  - **host_name** `string`: The user defined name of the instance.
  - **cpu_cores** `number`: The number of CPU cores in the product.
  - **ram** `number`: The amount of RAM in gigabytes for the product.
  - **gpu** `string`: The GPU model name for the GPU product.
  - **gpu_type** `string`: The GPU serial name for the GPU product.
  - **gpu_count**: The number of GPUs included in the GPU product.
  - **disk_size** `number`: The root disk size of the GPU instance in gigabytes.
  - **ephemeral** `number`: The ephemeral disk size of the GPU instance in gigabytes.
  - **public_ipv4** `string`: New billing cycle, the default is hourly.
  - **os** `string`: The operation system of the instance.
  - **status** `string`: The status of the instance.

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
curl -X GET '{API_URL}/computing/instances' \
-H 'Authorization: Bearer {ACCESS_TOKEN}' \
-H 'Content-Type: application/json' \
```

### Response

```json
{
    "data": [
        {
            "id": 41,
            "region": "CANADA-1",
            "instance_type": "GPU",
            "host_name": "mike-1001",
            "cpu_cores": "28",
            "ram": "58",
            "gpu_type": "RTX-A6000",
            "gpu_count": 1,
            "disk_size": 100,
            "public_ipv4": "62.169.158.214",
            "os": "Ubuntu Server 20.04 LTS (Focal Fossa)",
            "vm_name": "mike-1001",
            "vm_password": "qZ3!Xukz=I-Xv_ya",
            "status": "Running"
        }
    ],
    "total_instance": 1,
    "message": "All instances retrieved successfully",
    "status": "success"
}

```
