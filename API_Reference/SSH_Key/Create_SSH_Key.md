# Create SSH Key

Creates an SSH key for use in your instances.

## HTTP Request

`POST` `{API_URL}/ssh-keys`

## Body Parameters

| Parameters | Requirements | Type     | Description             |
|------------|--------------|----------|-------------------------|
| key_name   | Required     | `string` | The name of the SSH key |
| key_data   | Required     | `string` | The SSH key value       |

## Response Attributes

#### data `dict`

Returns the `data` object, containing details of the new SSH Key.

Each SSH key specifies the following properties:
- `id`: The ID of the SSH key.
- `key_name`: The name of the SSH key.
- `key_data`: The SSH key value.
- `create_time`: The UNIX timestamp of when the SSH Key was created.

#### status `string`

Indicates the result of the request to create a SSH key. `success` signifies success, while `failed` indicates an error.

#### message `string`

A description of the status of the request.

## Example

#### Request

```bash
curl -X POST '{API_URL}/ssh-keys' \
-H 'Authorization: Bearer {TOKEN/KEY}' \
-d '{
    "name": "My Personal SSH Key",
    "key_data": "ssh-rsa AAADB3NzaC1yc2EBBACCAQABAAABAQD5",
}'
```

#### Response

```json
{
    "data": {
        "id": "7902904e-48b3-4bc6-8b63-bfbb19ff4ff8",
        "key_name": "My Personal SSH Key",
        "key_data": "ssh-rsa AAADB3NzaC1yc2EBBACCAQABAAABAQD5",
        "create_time": "1730847667"
    },
    "message": "SSH key created successfully",
    "status": "success"
}
```