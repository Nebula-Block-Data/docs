# Rename SSH Key

Updates the name of a specified SSH key. Include the ID of the SSH key in the endpoint path
and the new name in the body of the request. To retrieve your SSH key IDs, see the [List SSH Keys API](List_SSH_Keys.md).

## HTTP Request

`PUT` `{API_URL}/ssh-keys/{id}`

## Path Parameters

| Parameters | Requirements | Type     | Description                                        |
|------------|--------------|----------|----------------------------------------------------|
| id         | Required     | `string` | The unique identifier of the SSH key to be renamed |

## Body Parameters

| Parameters | Requirements | Type     | Description                 |
|------------|--------------|----------|-----------------------------|
| key_name   | Required     | `string` | The new name of the SSH key |

## Response Attributes

#### data `dict`

Returns the `data` object, containing details of the updated SSH Key.

Each updated SSH key specifies the following properties:
- `id`: The ID of the SSH key.
- `key_name`: The new name of the SSH key.
- `key_data`: The SSH key value.
- `create_time`: The UNIX timestamp of when the SSH Key was created.

#### status `string`

Indicates the result of the request to rename a SSH key. `success` signifies success, while `failed` indicates an error.

#### message `string`

A description of the status of the request.

## Example

#### Request

```bash
curl -X PUT '{API_URL}/ssh-keys/9a4d7961-3274-4479-a20b-10f57f9bc75a' \
-H 'Authorization: Bearer {TOKEN/KEY}' \
-d '{
    "key_name": "Test user was here",
}'
```

#### Response

```json
{
    "data": {
        "id": "9a4d7961-3274-4479-a20b-10f57f9bc75a",
        "key_name": "Test user was here",
        "key_data": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQD5",
        "create_time": "1730847956"
    },
    "message": "SSH key updated successfully",
    "status": "success"
}
```