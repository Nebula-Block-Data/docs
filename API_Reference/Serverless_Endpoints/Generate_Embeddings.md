---
# title: Generate Embeddings 
description: Generate Embeddings From Text.
---

# Generte Serverless Images

Return the generated embeddings based on the given inputs. 

## HTTP Request

`POST` `{API_URL}/embeddings`

where `API_URL = https://inference.nebulablock.com/v1`.

## Response Attributes

#### model `model`

A string representing the AI model used to generate the response.

#### data `array`

An array containing the embeddings, represented by dictionaries with the following key-value pairs: 

- **embedding** `list of floats`: 
- **index** `integer`: An index to identify the position of the embedding in the response, relative to the input.
- **object** `string`: An object label to describe the data. 

#### object `string`



#### usage `dict`

A dictionary containing the following key-value pairs: 

- **completion_tokens** `integer`: The number of tokens generated in the completion.
- **prompt_tokens** `integer`: The number of tokens in the prompt.
- **total_tokens** `integer`: The total number of tokens generated.
- **completion_tokens_details** `null`: Additional details about the completion tokens, if applicable.
- **prompt_tokens_details** `null`: Additional details about the prompt tokens.

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

```json
data: {
    "id": "chatcmpl-3061dfd6d9170825ba0fb54086c4dad3",
    "created": 1740081592,
    "model": "meta-llama/Llama-3.1-8B-Instruct",
    "object": "chat.completion.chunk",
    "choices": [
        {
            "index": 0,
            "delta": {
                "content": "It",
                "role": "assistant"
            }
        }
    ]
}

data: {
    "id": "chatcmpl-3061dfd6d9170825ba0fb54086c4dad3",
    "created": 1740081592,
    "model": "meta-llama/Llama-3.1-8B-Instruct",
    "object": "chat.completion.chunk",
    "choices": [
        {
            "index": 0,
            "delta": {
                "content": " looks"
            }
        }
    ]
}
...
data: [DONE]
```
