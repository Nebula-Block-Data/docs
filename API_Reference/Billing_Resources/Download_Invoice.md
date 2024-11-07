---
# title: Invoice Download
description: User download invoice by id.
---

# Download Invoice

This API endpoint enables users to download a specific invoice by including the invoice ID in the URL path. 
Authentication is required via a Bearer token obtained through user login.

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