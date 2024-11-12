---
# title: User Invoices List
description: Get invoice list fot the current user.
---

# List Invoices

This API retrieves a paginated list of user invoices, including details such as the invoice ID, price, invoiced time, and download URL.

## HTTP Request

`GET` `{API_URL}/users/invoices?limit=limit&offset=offset`

| Parameters | Requirements | Type  | Description                                                                                         |
|------------|--------------|-------|-----------------------------------------------------------------------------------------------------|
| limit      | Optional     | `int` | The number of records to display per page                                                           |
| offset     | Optional     | `int` | The starting point for record retrieval (i.e., how many records to skip before starting to display) |

## Response Attributes

#### data `dict`

  - **invoices**: List of user invoices objects.
  - **total_invoices**: total records count of user invoices.

#### status `string`

Indicates the result of the request. **success** signifies success, while **failed** indicates an error.

#### message `string`

A message confirming the successful retrieval of user invoices.

## Example

#### Request

```bash
curl -X GET '{API_URL}/users/invoices?limit=2&offset=0'
-H 'Authorization: Bearer {TOKEN/KEY}'
```

#### Response

```json
{
    "data": {
        "invoices": [
            {
                "invoiced_time": "EST 2024-10-29 14:19:32",
                "invoice_id": "#NB-20241029181932-266",
                "price": 229.95,
                "type": "Reload",
                "id": 3688,
                "user_id": 266
            },
            {
                "invoiced_time": "EST 2024-10-29 14:18:54",
                "invoice_id": "#NB-20241029181853-266",
                "price": 11.5,
                "type": "Reload",
                "id": 3687,
                "user_id": 266
            },
            {
                "invoiced_time": "EST 2024-10-29 14:15:29",
                "invoice_id": "#NB-20241029181528-266",
                "price": 114.98,
                "type": "Reload",
                "id": 3686,
                "user_id": 266
            }
        ],
        "total_invoices": 3
    },
    "message": "User invoices retrieved successfully",
    "status": "success"
}
```


