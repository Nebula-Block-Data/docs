# List SSH Keys

## HTTP Request

`GET` `{API_URL}/ssh-keys`

## Response Attributes

#### data `array`

Returns the `data` array of objects, each containing details about your SSH keys.

Each SSH key has the following properties:
- `id`: The ID of the SSH key. This is the ID field that is used for the [Delete SSH Key](Delete_SSH_Key.md) endpoint.
- `key_name`: The name of the SSH key.
- `key_data`: The SSH key value.
- `create_time`: The UTC time of when the SSH Key was created.

#### status `string`

Indicates the result of the request to list your SSH keys. `success` signifies success, while `failed` indicates an error.

#### message `string`

A description of the status of the request.

## Example

#### Request

```bash
curl -X GET '{API_URL}/ssh-keys' \
-H 'Authorization: Bearer {token/key}'
```

#### Response

```json
{
    "data": [
        {
            "id": 76,
            "key_name": "My Personal SSH Key",
            "key_data": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQD5",
            "create_time": "UTC: 2024-11-05 23:05:56"
        },
        {
            "id": 77,
            "key_name": "My Personal SSH Keys",
            "key_data": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQD5",
            "create_time": "UTC: 2024-11-05 23:05:56"
        }
    ],
    "message": "SSH keys retrieved successfully",
    "status": "success"
}
```