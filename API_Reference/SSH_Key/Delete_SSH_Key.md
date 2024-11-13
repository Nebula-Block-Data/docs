# Delete SSH Key

Deletes a specified SSH key by including the ID of the SSH key in the endpoint path.
To retrieve your SSH key IDs, see the [List SSH Keys API](List_SSH_Keys.md).

## HTTP Request

`DELETE` `{API_URL}/ssh-keys/{id}`

## Path Parameters

| Parameters | Requirements | Type     | Description                                        |
|------------|--------------|----------|----------------------------------------------------|
| id         | Required     | `string` | The unique identifier of the SSH key to be deleted |

## Response Attributes

#### data `dict`

Empty `data` object

#### status `string`

Indicates the result of the request to delete a SSH key. `success` signifies success, while `failed` indicates an error.

#### message `string`

A description of the status of the request.

## Example

#### Request

```bash
curl -X DELETE '{API_URL}/ssh-keys/7902904e-48b3-4bc6-8b63-bfbb19ff4ff8' \
-H 'Authorization: Bearer {TOKEN/KEY}'
```

#### Response

```json
{
    "data": {},
    "message": "SSH key deleted successfully",
    "status": "success"
}
```