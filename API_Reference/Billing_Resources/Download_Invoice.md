---
# title: Invoice Download
description: User download invoice by id.
---

# Download Invoice

This API endpoint allows users to download a specific invoice by including the invoice_id in the URL path. 
The `invoice_id` can be obtained from the response of the List_Invoices endpoint, where it is returned as the `id` field. 
Authentication is required via a Bearer token, which is obtained through user login.

## HTTP Request

`GET` `{API_URL}/users/invoice-download/{invoice_id}`

## Path Parameters

| Parameters | Requirements | Type  | Description                                           |
|------------|--------------|-------|-------------------------------------------------------|
| invoice_id | Required     | `int` | The unique identifier of the invoice to be deleted    |

[comment]: <> (TODO: Include the "Response Attributes" section)

## Example

#### Request

```bash
curl -X GET '{API_URL}/users/invoice-download/{invoice_id}'
-H 'Authorization: Bearer {TOKEN/KEY}'
```

#### Response

The invoice PDF file will be downloaded automatically.