## Delete API Token

## HTTP Request

`DELETE` `{API_URL}/api-keys/{id}`

## Path Parameters

| Parameters | Requirements | Type  | Description                                        |
|------------|--------------|-------|----------------------------------------------------|
| id         | Required     | `int` | The unique identifier of the API key to be deleted |

## Response Attributes

### data `dict`

Empty `data` object

### status `string`

Indicates the result of the request to delete an API key. `success` signifies success, while `failed` indicates an error.

### message `string`

A description of the status of the request.

## Example

### Request

```bash
curl -X DELETE '{API_URL}/api-keys/5' \
-H 'Authorization: Bearer {token/key}'
```

### Response

```json
{
    "data": {},
    "message": "API key successfully deleted",
    "status": "success"
}
```