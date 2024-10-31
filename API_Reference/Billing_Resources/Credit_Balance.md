---
title: User Credit Balance
description: Retrieve the user's current credit balance.
---

# User Credit Balance

This API endpoint allows you to retrieve the user's current credit balance. The request requires authentication using a bearer token, which can be obtained from the login API.

## HTTP Request

{API_URL}/api/v1/users/credits

## Response Attributes

### `data`

- **Type**: Dict
  - **available_balance**: User credit amount.

### `message`

- **Type**: String
  A message confirming the successful retrieval of user credit.

### `status`

- **Type**: String
  Indicates the result of the request.
  **success** signifies success, while **failed** indicates an error.

## Example

### Request

```bash
curl -X GET '{API_URL}/api/v1/users/credits'
-H 'Authorization: Bearer {ACCESS_TOKEN}'
-H 'Content-Type: application/json'
```

### Response

```json
{
    "data": {
        "available_balance": "1228.55600"
    },
    "message": "User credit balance successfully retrieved",
    "status": "success"
}
```


