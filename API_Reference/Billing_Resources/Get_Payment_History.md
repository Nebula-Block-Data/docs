---
# title: User Transaction History
description: Retrieve the user's transaction history.
---

# Get Payment History

This API retrieves your payment history and transaction details related to consumed credits, updated every hour.

## HTTP Request

`GET` `{API_URL}/users/credits/history?limit=limit&offset=offset`
  - `limit`: Specifies the number of records to display per page.
  - `offset`: Specifies the starting point for record retrieval (i.e., how many records to skip before starting to display).

## Response Attributes

#### data `dict`

  - **credit_balance**: User available credit amount.
  - **credit_history**: List of credits hourly transaction history.
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
        "credit_balance": 9.8682,
        "credit_history": [
            {
                "user_id": 266,
                "computing_amount": 2.004,
                "serverless_amount": 0.0,
                "create_time": "EST 2024-11-10 06:54:58",
                "update_time": "EST 2024-11-10 07:54:58",
                "total": 2.004
            },
            {
                "user_id": 266,
                "computing_amount": 2.004,
                "serverless_amount": 0.0,
                "create_time": "EST 2024-11-10 05:54:58",
                "update_time": "EST 2024-11-10 06:54:58",
                "total": 2.004
            }
        ],
        "total_credit_histories": 2
    },
    "message": "User credit history successfully retrieved",
    "status": "success"
}
```


