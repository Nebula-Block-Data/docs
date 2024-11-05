# Authentication

All endpoints under the Nebula Block API require user authentication to validate a user's identity 
and know whose resource to access/create/alter/delete. For authentication, there are two options:
- [Access tokens](#access-tokens)
- [API keys](#api-keys)

Regardless of the method, Bearer authentication is used and requires the following header be specified in an HTTP request:
```
Authorization: Bearer <token/key>
```

## Access Tokens

Access tokens are obtained by logging in with a username and password via the [login endpoint](#login), and retrieving
the `jwtToken` field in the response body. Once obtained, the following authorization header can be specified in each
request:

```
Authorization: Bearer <access_token>
```

For example:

```
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJiZWJlZXJtaW5nQDEyNi5jb20iLCJyb2xlcyI6WyJHVUVTVCJdLCJleHAiOjE3MzAzOTM5NTMsInNjb3BlcyI6WyJHVUVTVCJdfQ.IVMMITYihqkMszTo_x7uP6gocxgN5RLfLZiJY8VqEyk
```

> **NOTE:**  Access tokens expire after 2 hours, in which case you need to log in again to get a new access token

## API Keys

Alternative to access tokens, API keys can be used to authenticate requests. The plus side to using API keys is there 
being no expiration date, so users can use them for a much longer time. To learn how to create and manage API keys, see the
[API Key Section Documentation](../API_Reference/API_Key/Create_API_Key.md). Once an API key is obtained, the following
authorization header can be specified in each request:

```
Authorization: Bearer <api_key>
```

For example:

```
Authorization: Bearer ak_W4KL0Rw8Rv6Mp7h7fY77dFgHDl_EMAojslklxhMI9-0
```

> **INFO:** API keys are always prefixed with `ak_`. The prefix is how they are differentiated from access tokens.

## Login

## HTTP Request

`POST` `{API_URL}/login`

## Body Parameters

| Parameters | Requirements      | Type     | Description          |
|------------|--------------------|----------|----------------------|
| username   | Required    | `string` | Login username/email |
| password   | Required| `string` | Login password       |

## Response Attributes

### data `dict`

A dictionary that contains the access token (`jwtToken`)

### status `string`

Indicates the result of the request to log in. `success` signifies success, while `failed` indicates an error.

### message `string`

A description of the status of the request.

## Example

### Request

```bash
curl -X POST '{API_URL}/login' \
-H 'Content-Type: application/x-www-form-urlencoded' \
-d '{
    "username": "testemail@gmail.com",
    "password": "123456789",
}'
```

### Response

```json
{
    "data": {
        "id": 18,
        "name": "Test User",
        "email": "testemail@gmail.com",
        "is_staff": false,
        "is_active": true,
        "jwtToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJhZG1pbkBnbWFpbC5jb20iLCJyb2xlcyI6WyJBRE1JTiJdLCJleHAiOjE3MzA3NTg2MzYsInNjb3BlcyI6WyJBRE1JTiJdfQ.QwXYFII5y_V_9bIRQ3R-9W-jATjHa2yfklLaTQzVwS8"
    },
    "message": "Login successful",
    "status": "success"
}
```

