---
# title: List User Instances
description: List Deleted User Instances.
---

# List User Instances

Return a list of all deleted instances.

## HTTP Request

`GET` `{API_URL}/computing/deleted-instances`

## Query string parameters

| Parameters     | Requirements      | Type       | Description      |
|---------------|--------------------|----------------|----------------|
|`limit`| Optional | `int` | The number of items to return |
|`offset`|  Optional | `int` | The number of items to skip before starting to collect the result set|

## Response Attributes

#### data `array`

An array containing information about products organized by GPU model and region:

- **id** `string`: The unique identifier for the product.
- **region** `string`: The region where the GPU product is available.
- **product_type** `string`: The type of instance,like GPU and CPU.
- **host_name** `string`: The user defined name of the instance.
- **cpu_cores** `number`: The number of CPU cores in the product.
- **ram** `number`: The amount of RAM in gigabytes for the product.
- **gpu** `string`: The GPU model name for the GPU product.
- **gpu_type** `string`: The GPU serial name for the GPU product.
- **gpu_count**: The number of GPUs included in the GPU product.
- **disk_size** `number`: The root disk size of the GPU instance in gigabytes.
- **ephemeral** `number`: The ephemeral disk size of the GPU instance in gigabytes.
- **public_ipv4** `string`: New billing cycle, the default is hourly.
- **price_per_hour** `string`: The price per hour of the instance.
- **os** `string`: The operation system of the instance.
- **status** `string`: The status of the instance.

#### message `string`

A description of the status of the request.

#### status `string`

  Indicates the result of the request.  
  **success** signifies success, while **failed** indicates an error.

## Example

#### Request

```bash
curl -X GET '{API_URL}/computing/deleted-instances' \
-H 'Authorization: Bearer {ACCESS_TOKEN}' \
-H 'Content-Type: application/json' \
```

#### Response

```json
{
    "data": [
        {
            "id": "102cade84ea-e703-4400-b77d-8ed545d198ee",
            "region": "CANADA",
            "product_type": "GPU",
            "host_name": "demo",
            "cpu_cores": 28,
            "ram": 58,
            "gpu_type": "RTX-A6000",
            "gpu_count": 1,
            "disk_size": 100,
            "ephemeral": 1500,
            "public_ipv4": "38.80.81.128",
            "price_per_hour": 0.679,
            "os": "Ubuntu Server 20.04 LTS (Focal Fossa)",
            "status": "Deleted"
        }
    ],
    "total_instance": 1,
    "message": "All deleted instances retrieved successfully",
    "status": "success"
}

```
