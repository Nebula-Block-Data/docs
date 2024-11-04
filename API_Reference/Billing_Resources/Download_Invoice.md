---
# title: Invoice Download
description: User download invoice by id.
---

# User Invoices List

This API endpoint enables users to download a specific invoice by including the invoice ID in the URL path. 
Authentication is required via a Bearer token obtained through user login.

## HTTP Request

`GET` `{API_URL}/api/v1/users/invoice-download/{invoice_id}`
  - `invoice_id`: The invoice_id can be obtained from the response of the "List Invoices" endpoint, `{API_URL}/api/v1/users/invoices?limit=2&offset=0`, where it appears as `id`.

## Example

### Request

```bash
curl -X GET '{API_URL}/api/v1/users/invoice-download/{invoice_id}'
-H 'Authorization: Bearer {ACCESS_TOKEN}'
```

### Response
The invoice PDF file will be downloaded automaticlly.