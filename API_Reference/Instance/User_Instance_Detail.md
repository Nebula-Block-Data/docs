---
# title: Create GPU Instance
description: User Instance Details.
---

# User Instance Details

Return user instance detail information, like cpu, gpu, ram, total running time and etc.

## HTTP Request

`GET` `{API_URL}/computing/instance/{id}`

## Path parameters

| Parameters     | Requirements      | Type       | Description      |
|---------------|--------------------|----------------|----------------|
| id      | Required    | `number`       | The unique identifier of the instance. `{id} comes from <List User Instances API>` |

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
  - **login_method** `string`: The login method of the instance.
  - **os** `string`: The operation system of the instance.
  - **exposed_ports** `string`: The exposed ports of the container instance.
  - **user_name** `string`: The user name of the container instance.
  - **password** `string`: The password of the container instance.
  - **status** `string`: The status of the instance.
  - **start_time** `string`: The time that instance started.
  - **running_time** `string`: The total running time of the instance.
  - **total_cost** `string`: The total cost of the instance.

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
            "region": "CANADA",
            "instance_type": "GPU",
            "host_name": "mike-1001",
            "cpu_cores": "28",
            "ram": "58",
            "gpu_type": "RTX-A6000",
            "gpu_count": 1,
            "disk_size": 100,
            "public_ipv4": "62.169.158.214",
            "login_method": "",
            "os": "Ubuntu Server 20.04 LTS (Focal Fossa)",
            "exposed_ports": "",
            "vm_name": "mike-1001",
            "vm_password": "qZ3!Xukz=I-Xv_ya",
            "status": "Running",
            "start_time": "EST 2024-11-04 10:11:50",
            "running_time": "0.0000 hours",
            "total_cost": "$0.0000"
        }
    ],
    "message": "Get instance detail successfully",
    "status": "success"
}

```
