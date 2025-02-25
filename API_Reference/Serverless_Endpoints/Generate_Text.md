---
# title: Generate Serverless Text 
description: Generate Serverless Text.
---

# Generate Serverless Text

Return the generated text based on the given inputs. 

## HTTP Request

`POST` `{API_URL}/chat/completions`

where the `API_URL = https://inference.nebulablock.com/v1`. The body has the following parameters:

- **messages** `array`: An array of message objects. Each object should have:
  - **role** `string`: The role of the message sender (e.g., "user").
  - **content** `string`: The content of the message.
- **model** `string`: The model to use for generating the response.
- **max_tokens** `integer or null`: The maximum number of tokens to generate. If null, the model's default will be used.
- **temperature** `float`: Sampling temperature. Higher values make the output more random, while lower values make it more focused and deterministic.
- **top_p** `float`: Nucleus sampling probability. The model will consider the results of the tokens with top_p probability mass. In other words, a higher value will result in more diverse outputs, while a lower value will result in more repetitive outputs.
- **stream** `boolean`: Whether to stream the response in chunks or not. 

## Response Attributes

#### id `string`
A unique identifier for the completion request.

#### created `integer`
A Unix timestamp representing when the response was generated.

#### model `string`
The specific AI model used to generate the response.

#### object `string`
The type of response object (e.g., `"chat.completion.chunk"` for a streamed chunk or `chat.completion` for a non-chunked completion).

#### system_fingerprint `string`
A unique identifier for the system that generated the response, if available.

#### choices `array`
An array containing completion objects. Each object has the following fields:
- **finish_reason** `string`: The reason the completion finished.
- **index** `integer`:  An index demarking this completion object. 
- **message** `dict`: Contains data on the generated output. 
  - **content** `string`: The generated text for this completion object.
  - **role** `string`: Specifies the role of the AI (e.g., "assistant").
  - **tool_calls** `array`: Contains information about the tools used in generating the completion, if available. 
  - **function_calls** `array`: Contains information about the functions used in generating the completion, if available.

#### usage `dict`
A dictionary containing information about the inference request, in key-value pairs:
- **completion_tokens** `integer`: The number of tokens generated in the completion for a completion action.
- **prompt_tokens** `integer`: The number of tokens in the prompt.
- **total_tokens** `integer`: The total number of tokens (prompt and completion combined).
- **completion_tokens_details** `null`: Additional details about the completion tokens, if available.
- **prompt_tokens_details** `null`: Additional details about the prompt tokens, if available.

#### service_tier `string`
The service tier used for the completion request.

#### prompt_logprobs `array`
An array containing the log probabilities of the tokens in the prompt, if available.

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
