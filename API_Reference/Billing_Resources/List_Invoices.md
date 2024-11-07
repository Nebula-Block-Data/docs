---
# title: User Invoices List
description: Get invoice list fot the current user.
---

# List Invoices

This API retrieves a paginated list of user invoices, including details such as the invoice ID, price, invoiced time, and download URL.

## HTTP Request

`GET` `{API_URL}/users/invoices`

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
                "invoice_id": "#NB-20241030102751-266",
                "price": 0.0,
                "invoiced_time": "1730298491",
                "id": 3703,
                "user_id": 266
            },
            {
                "invoice_id": "#NB-20241029140714-266",
                "price": 141.94,
                "invoiced_time": "1730225240",
                "id": 3702,
                "user_id": 266
            }
        ],
        "total_invoices": 18
    },
    "message": "User invoices retrieved successfully",
    "status": "success"
}
```


