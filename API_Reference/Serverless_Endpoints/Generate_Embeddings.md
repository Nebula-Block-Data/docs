---
# title: Generate Embeddings 
description: Generate Embeddings From Text.
---

# Generate Serverless Embeddings

Return the generated embeddings based on the given inputs. 

## HTTP Request

`POST` `{API_URL}/embeddings`

where `API_URL = https://inference.nebulablock.com/v1`. The body requires: 

- `model`: The model to use for generating embeddings.
- `input`: A list of strings to generate embeddings from.

For authentication, see the [Authentication](../Authentication.md) section. For an example, see the [Serverless Endpoints](../../Serverless_Endpoints/Embedding_Generation.md) section.

## Response Attributes

#### model `model`
A string representing the AI model used to generate the response.

#### data `array`
An array containing the embeddings, represented by dictionaries with the following key-value pairs: 

- **embedding** `list of floats`: The generated embedding for input at index `index`. 
- **index** `integer`: An index to identify the position of the embedding in the response, relative to the ordering of the input.
- **object** `string`: An object label to describe the data. 

#### object `string`
Describes the type of data returned.

#### usage `dict`
A dictionary containing information about the inference request, in key-value pairs: 

- **completion_tokens** `integer`: The number of tokens generated in the completion for a completion action (not applicable for embeddings).
- **prompt_tokens** `integer`: The number of tokens in the prompt.
- **total_tokens** `integer`: The total number of tokens (prompt and completion combined).
- **completion_tokens_details** `null`: Additional details about the completion tokens, if available. 
- **prompt_tokens_details** `null`: Additional details about the prompt tokens, if available. 

## Example

#### Request

```bash
curl -X GET '{API_URL}/api/v1/images/generation' \
-H 'Authorization: Bearer {TOKEN/KEY}' \
-H 'Content-Type: application/json' \
-d '{
    "model": "WhereIsAI/UAE-Large-V1",
    "input": [
        "Bananas are berries, but strawberries are not, according to botanical classifications.",
        "The Eiffel Tower in Paris was originally intended to be a temporary structure."
    ]
}'
```

#### Response

Here's an example of a successful response. It consists of a stream of `data` dictionaries, each containing the data for 
a generated token. The entire collection of dictionaries represents the complete generated response. 

```json{
    "model": "WhereIsAI/UAE-Large-V1",
    "data": [
        {
            "embedding": [
                -0.373046875,
                ...,
                -0.10302734375
            ],
            "index": 0,
            "object": "embedding"
        },
        {
            "embedding": [
                -0.50390625,
                ...,
                -0.03564453125,
                0.01409912109375
            ],
            "index": 1,
            "object": "embedding"
        }
    ],
    "object": "list",
    "usage": {
        "completion_tokens": 0,
        "prompt_tokens": 33,
        "total_tokens": 33,
        "completion_tokens_details": null,
        "prompt_tokens_details": null
    }
}
```

For more examples, see the [Serverless Endpoints](../../Serverless_Endpoints/Embedding_Generation.md) section.
