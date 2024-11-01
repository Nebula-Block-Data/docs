---
title: User Transaction History
description: Retrieve the user's transaction history.
---

# User Credit Balance

This API will retrieve all user's transaction including 
credits purchase payment (money payment and crypto payment), 
credits consume(update once an hour).

## HTTP Request

`GET` `{API_URL}/api/v1/users/credits/history?limit={limit}&offset={offset}`
  - `limit`: Specifies the number of records to display per page.
  - `offset`: Specifies the starting point for record retrieval (i.e., how many records to skip before starting to display).

## Response Attributes

### `data`

- **Type**: Dict
  - **credit_balance**: User available credit amount.
  - **credit_history**: List of credits transaction history.
  - **total_credit_histories**: Total history count.

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
curl -X GET '{API_URL}/api/v1/users/credits/history?limit=2&offset=0'
-H 'Authorization: Bearer {ACCESS_TOKEN}'
-H 'Content-Type: application/json'
```

### Response

```json
{
    "data": {
        "credit_balance": 375.0,
        "credit_history": [
            {
                "id": 16230,
                "user_id": 266,
                "transaction_type": "purchase",
                "credit_amount": 250.0,
                "created_at": "2024-01-01 01:00:00",
                "status": "success",
                "expire_time": null
            },
            {
                "id": 16229,
                "user_id": 266,
                "transaction_type": "purchase",
                "credit_amount": 10.0,
                "created_at": "2024-01-01 00:00:00",
                "status": "success",
                "expire_time": null
            }
        ],
        "total_credit_histories": 4
    },
    "message": "User credit history successfully retrieved",
    "status": "success"
}
```


