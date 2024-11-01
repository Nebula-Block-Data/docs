---
title: User Invoices List
description: Get invoice list fot the current user.
---

# User Invoices List

This API retrieves a paginated list of user invoices, including details like invoice ID, price, invoiced time, and download URL.

## HTTP Request

`GET` `{API_URL}/api/v1/users/invoices?limit=2&offset=0`
  - `limit`: Specifies the number of records to display per page.
  - `offset`: Specifies the starting point for record retrieval (i.e., how many records to skip before starting to display).

## Response Attributes

### `data`

- **Type**: Dict
  - **invoices**: List of user invoices objects.
  - **total_invoices**: total records count of user invoices.

### `message`

- **Type**: String
  A message confirming the successful retrieval of user invoices.

### `status`

- **Type**: String
  Indicates the result of the request.
  **success** signifies success, while **failed** indicates an error.

## Example

### Request

```bash
curl -X GET '{API_URL}/api/v1/users/invoices?limit=2&offset=0'
-H 'Authorization: Bearer {ACCESS_TOKEN}'
-H 'Content-Type: application/json'
```

### Response

```json
{
    "data": {
        "invoices": [
            {
                "invoice_id": "#NB-20241030102751-266",
                "price": 0.0,
                "invoiced_time": "1730298491",
                "download_url": "PDF_File_PATH",
                "id": 3703,
                "user_id": 266
            },
            {
                "invoice_id": "#NB-20241029140714-266",
                "price": 141.94,
                "invoiced_time": "1730225240",
                "download_url": "PDF_File_PATH",
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


