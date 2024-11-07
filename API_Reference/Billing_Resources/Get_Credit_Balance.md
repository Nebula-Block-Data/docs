---
# title: User Credit Balance
description: Retrieve the user's current credit balance.
---

# User Credit Balance

This API endpoint allows you to retrieve the user's current credit balance. The request requires authentication using a bearer token, which can be obtained from the login API.

## HTTP Request

`GET` `{API_URL}/users/credits`

## Response Attributes

#### data `dict`

Returns the `data` object, containing the user credit balance in the field `available_balance`.

#### status `string`

Indicates the result of the request to get your credit balance. success signifies success, while failed indicates an error.

#### message `string`

A description of the status of the request.

## Example

#### Request

```bash
curl -X GET '{API_URL}/users/credits'
-H 'Authorization: Bearer {TOKEN/KEY}'
```

#### Response

```json
{
    "data": {
        "available_balance": "1228.55600"
    },
    "message": "User credit balance successfully retrieved",
    "status": "success"
}
```


