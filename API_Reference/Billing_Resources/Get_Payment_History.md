---
# title: User Transaction History
description: Retrieve the user's transaction history.
---

# Get Payment History

This API retrieves your payment history/transactions, including 
purchased credits (using card or crypto) and 
consumed credits (updated hourly).

## HTTP Request

`GET` `{API_URL}/users/credits/history`
  - `limit`: Specifies the number of records to display per page.
  - `offset`: Specifies the starting point for record retrieval (i.e., how many records to skip before starting to display).

## Response Attributes

#### data `dict`

  - **credit_balance**: User available credit amount.
  - **credit_history**: List of credits transaction history.
  - **total_credit_histories**: Total history count.

#### status `string`

Indicates the result of the request. **success** signifies success, while **failed** indicates an error.

#### message `string`

A message confirming the successful retrieval of user transactions.

## Example

#### Request

```bash
curl -X GET '{API_URL}/users/credits/history?limit=2&offset=0'
-H 'Authorization: Bearer {TOKEN/KEY}'
```

#### Response

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

