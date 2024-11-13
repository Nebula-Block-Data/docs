# Create API Key

Create a new API key for use in authenticating API requests. To learn how to authenticate requests with API keys,
see the [Authentication section](../../Getting_Started/Authentication.md).

## HTTP Request

`POST` `{API_URL}/api-keys`

## Body Parameters

| Parameters  | Requirements | Type     | Description                            |
|-------------|--------------|----------|----------------------------------------|
| name        | Required     | `string` | The name of the API key                |
| description | Optional     | `string` | An optional description of the API key |

## Response Attributes

#### data `dict`

Returns the `data` object, containing details of the new API key.

Each API key specifies the following properties:
- `id`: The ID of the API key.
- `key`: The API key value that is used to authenticate API requests.
- `name`: The name of the API key.
- `description`: An optional description of the API key.


> **Important:** The API key value `key` is shown only once in the response body when creating an API key.
> It can't be viewed again for security reasons. The [List API Keys](List_API_Keys.md) endpoint shows only the IDs + 
> names of your API keys for deletion. If you lose your API key, create a new one and delete the old one.


#### status `string`

Indicates the result of the request to create an API key. `success` signifies success, while `failed` indicates an error.

#### message `string`

A description of the status of the request.

## Example

#### Request

```bash
curl -X POST '{API_URL}/api-keys' \
-H 'Authorization: Bearer {TOKEN/KEY}' \
-d '{
    "name": "test-api-key",
    "description": "This is a test API key",
}'
```

#### Response

```json
{
    "data": {
        "id": "9a4d7961-3274-4479-a20b-10f57f9bc75a",
        "key": "ak_WT2l5Rw8Rv8Mp7Q7fLh7dFgEDl_EMAntCsqlxhEsu-0",
        "name": "test-api-key",
        "description": "This is a test API key"
    },
    "message": "API key successfully created",
    "status": "success"
}
```