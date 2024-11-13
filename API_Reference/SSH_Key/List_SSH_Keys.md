# List SSH Keys

Retrieves a list of your SSH keys.

## HTTP Request

`GET` `{API_URL}/ssh-keys`

## Query Parameters

| Parameters | Requirements | Type  | Description                                                   |
|------------|--------------|-------|---------------------------------------------------------------|
| limit      | Optional     | `int` | The limit to the number of SSH keys returned. Defaults to 100 |
| offset     | Optional     | `int` | The offset of the returned SSH key response. Defaults to 0    |

## Response Attributes

#### data `dict`

Returns the `data` dictionary containing the total number of your SSH keys `total_ssh_keys` and the details of each SSH
key as per your `limit` and `offset` in `ssh_keys`.

Each SSH key in `ssh_keys` has the following properties:
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
-H 'Authorization: Bearer {TOKEN/KEY}'
```

#### Response

```json
{
    "data": {
        "total_ssh_keys": 1,
        "ssh_keys": [
            {
                "id": "7902904e-48b3-4bc6-8b63-bfbb19ff4ff8",
                "key_name": "My Personal SSH Key 1",
                "key_data": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQD5",
                "create_time": "EST 2024-10-23 10:24:21"
            },
            {
                "id": "9a4d7961-3274-4479-a20b-10f57f9bc75a",
                "key_name": "My Personal SSH Key 2",
                "key_data": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQD5",
                "create_time": "EST 2024-10-24 10:24:21"
            }
        ]
    },
    "message": "SSH keys retrieved successfully",
    "status": "success"
}
```