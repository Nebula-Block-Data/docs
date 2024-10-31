---

# List Images

Returns a list of all available operating system (OS) images, providing details about each image's corresponding virtual machine operating system.

## HTTP Request

`{API_URL}/api/v1/cloud/images/{product_type}`

`product_type` has 3 values: `vm`, `vm-gpu` and `rpc`

- `vm` is a CPU virtual machine.
- `vm-gpu` is a GPU virtual machine.
- `rpc` is a web3 RPC virtual machine.

## Response Attributes

### `data`

**Type**: Array  

An array containing information about operating system images:

- **image_name**: Name of the operating system image.
- **image_detail**: Detail information of the image.
- **id**: Id of the operating system image.
- **version**: Version of the operating system image.
- **coin_type**: Coin name of Web3 virtual machine.

### `message`

**Type**: String  
A message confirming the successful retrieval of images.

### `status`

**Type**: String  
Indicates the result of the request.  
**success** signifies success, while **failed** indicates an error.

## Example

### Request

```bash
curl -X GET '{API_URL}/api/v1/cloud/images/{product_type}' \
-H 'Authorization: Bearer {ACCESS_TOKEN}' \
-H 'Content-Type: application/json'
```

### Response

{API_URL}/api/v1/cloud/images/vm

```json
{
    "data": [
        {
            "image_type": "Ubuntu",
            "image_list": [
                {
                    "id": 1,
                    "name": "22.04 LTS x64",
                    "coin_type": ""
                },
                {
                    "id": 2,
                    "name": "20.04 LTS x64",
                    "coin_type": ""
                }
            ],
            "coin_type": ""
        },
        {
            "image_type": "Centos",
            "image_list": [
                {
                    "id": 3,
                    "name": "9 x64",
                    "coin_type": ""
                }
            ],
            "coin_type": ""
        },
        {
            "image_type": "Fedora",
            "image_list": [
                {
                    "id": 4,
                    "name": "40.1.14 x64",
                    "coin_type": ""
                }
            ],
            "coin_type": ""
        },
        {
            "image_type": "Debian",
            "image_list": [
                {
                    "id": 5,
                    "name": "12.5.0 x64",
                    "coin_type": ""
                }
            ],
            "coin_type": ""
        }
    ],
    "message": "Fetch all images success",
    "status": "success"
}
```

{API_URL}/api/v1/cloud/images/rpc

```json
{
    "data": [
        {
            "image_type": "Swan Chain",
            "image_list": [
                {
                    "id": 7,
                    "name": "Mainnet",
                    "coin_type": "SWAN"
                },
                {
                    "id": 9,
                    "name": "Proxima",
                    "coin_type": "SWAN"
                }
            ],
            "coin_type": "SWAN"
        },
        {
            "image_type": "Ethereum",
            "image_list": [
                {
                    "id": 13,
                    "name": "Mainnet",
                    "coin_type": "ETH"
                },
                {
                    "id": 14,
                    "name": "Sepolia",
                    "coin_type": "ETH"
                }
            ],
            "coin_type": "ETH"
        },
        {
            "image_type": "Optimism",
            "image_list": [
                {
                    "id": 15,
                    "name": "Mainnet",
                    "coin_type": "OP"
                },
                {
                    "id": 16,
                    "name": "Sepolia",
                    "coin_type": "OP"
                }
            ],
            "coin_type": "OP"
        },
        {
            "image_type": "Zksync",
            "image_list": [
                {
                    "id": 17,
                    "name": "Mainnet",
                    "coin_type": "ZK"
                },
                {
                    "id": 18,
                    "name": "Sepolia",
                    "coin_type": "ZK"
                }
            ],
            "coin_type": "ZK"
        },
        {
            "image_type": "Base",
            "image_list": [
                {
                    "id": 19,
                    "name": "Mainnet",
                    "coin_type": "BASE"
                },
                {
                    "id": 20,
                    "name": "Sepolia",
                    "coin_type": "BASE"
                }
            ],
            "coin_type": "BASE"
        },
        {
            "image_type": "opBNB",
            "image_list": [
                {
                    "id": 21,
                    "name": "Mainnet",
                    "coin_type": "OPBNB"
                },
                {
                    "id": 22,
                    "name": "Testnet",
                    "coin_type": "OPBNB"
                }
            ],
            "coin_type": "OPBNB"
        }
    ],
    "message": "Fetch all images success",
    "status": "success"
}
```

{API_URL}/api/v1/cloud/images/vm-gpu

```json
{
    "data": [
        {
            "image_type": "Ubuntu",
            "image_list": [
                {
                    "id": 6,
                    "name": "22.04 LTS x64",
                    "coin_type": ""
                }
            ],
            "coin_type": ""
        }
    ],
    "message": "Fetch all images success",
    "status": "success"
}
```

---
