# List API Keys

Retrieves a list of your API keys.

## HTTP Request

`GET` `{API_URL}/api-keys`

## Response Attributes

#### data `list`

Returns the `data` array of objects, each containing details about your API keys.

Each API key has the following properties:
- `id`: The ID of the API key. This is the ID field that is used for the [Delete API Key](Delete_API_Key.md) endpoint.
- `name`: The name of the API key.
- `description`: An optional description of the API key.
- `partial_key_data`: The prefix of each API key. This is the same across all API keys and doesn't show the raw API key value for security reasons.

#### status `string`

Indicates the result of the request to list your API keys. `success` signifies success, while `failed` indicates an error.

#### message `string`

A description of the status of the request.

## Example

#### Request

```bash
curl -X GET '{API_URL}/api-keys' \
-H 'Authorization: Bearer {TOKEN/KEY}'
```

#### Response

```json
{
    "data": [
        {
            "id": 5,
            "name": "api-test-key",
            "description": "This is the test API key",
            "partial_key_data": "ak_..."
        },
        {
            "id": 6,
            "name": "api-test-key2",
            "description": "This is the test API key #2",
            "partial_key_data": "ak_..."
        }
    ],
    "message": "API keys successfully retrieved",
    "status": "success"
}
```