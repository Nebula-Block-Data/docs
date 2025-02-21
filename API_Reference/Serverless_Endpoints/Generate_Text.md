---
# title: Generate Serverless Text 
description: Generate Serverless Text.
---

# Generate Serverless Text

Return the generated text based on the given inputs. 

## HTTP Request

`POST` `{API_URL}/chat/completions`

## Response Attributes

#### data `dict`

A dict containing the data of the generated text output. It contains the following fields:  

- **id** `string`: A unique identifier for the completion request.
- **created** `integer`: A Unix timestamp representing when the response was generated.
- **model** `string`: The specific AI model used to generate the response.
- **object** `string`: The type of response object (e.g., `"chat.completion.chunk"` for a streamed chunk).
- **choices** `array`: An array containing response segments. Each entry represents a part of the response.
  - **index** `integer`:  The position of this choice in the response (useful for multi-choice responses).
  - **delta** `dict`: Contains data on the generated output. 
    - **content** `string`: The generated text for this chunk.
    - **role** `string`: Specifies the role of the AI (e.g., "assistant").

## Example

#### Request

```bash
curl -X GET '{API_URL}/api/v1/chat/completions' \
-H 'Authorization: Bearer {TOKEN/KEY}' \
-H 'Content-Type: application/json' \
-d '{
    "messages": [
        {
            "role": "user",
            "content": "insert your prompt here"
        }
    ],
    "model": "meta-llama/Llama-3.1-8B-Instruct",
    "max_tokens": null,
    "temperature": 1,
    "top_p": 0.9,
    "stream": true
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
