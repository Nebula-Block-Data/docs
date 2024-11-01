---
title: List Available Regions
description: List Available Regions.
---

# List Regions

Lists the currently available regions, each representing a distinct geographic location housing a data center.

## HTTP Request

`GET` `{API_URL}/api/v1/cloud/regions`

## Response Attributes

### `data`

- **Type**: Array  
  An array of region objects containing details about the available regions.  
  Each region specifies the following properties:
  - **continent**: the name of the continent.
  - **regions**: the name of the region.

### `message`

- **Type**: String  
  A message confirming the successful retrieval of regions.

### `status`

- **Type**: String  
  Indicates the result of the request.  
  **success** signifies success, while **failed** indicates an error.

## Example

### Request

```bash
curl -X GET '{API_URL}/api/v1/cloud/regions' \
-H 'Authorization: Bearer {ACCESS_TOKEN}' \
-H 'Content-Type: application/json'
```

### Response

```json
{
    "data": [
        {
            "continent": "America",
            "regions": [
                "Montreal"
            ]
        }
    ],
    "message": "All regions retrieved successfully.",
    "status": "success"
}
```
