---
# title: Generate Serverless Text (Vision Model)
description: Generate Serverless Text (Vision Model).
---

# Generate Serverless Text (Vision Model)

Return the generated text based on the given textual and image inputs. 

## HTTP Request

`POST` `{API_URL}/chat/completions`

where the `API_URL = https://inference.nebulablock.com/v1`. The body has the following parameters:

- **messages** `array`: An array of message objects. Each object should have:
  - **role** `string`: The role of the message sender (e.g., "user").
  - **content** `list`: A list containing the different inputs (recall an input can be either text or image). Each input is represented as a dict with the following key-value pairs: 
    - **type** `string`: The type of input (e.g., "text" or "image_url").
    - **image_url** `dict`: If type is "image_url", this contains a dict representing the URL of the image with the following key-value pair: 
      - **url** `string`: The URL of the image. 
    - **text** `string`: If type is "text", the text input.

Note that only one of `url` or `text` can be provided in the input dict, and depends on the `type`.

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
curl -X POST "https://inference.nebulablock.com/v1/chat/completions" \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $NEBULA_API_KEY" \
    --data-raw '{
        "messages": [
			{"role":"user","content":[
			{"type":"image_url","image_url":
			{"url":"https://qianwen-res.oss-cn-beijing.aliyuncs.com/Qwen-VL/assets/demo.jpeg"}},
			{"type":"text","text":"What is this image?"}
		]}],
        "model": "Qwen/Qwen2.5-VL-7B-Instruct",
        "max_tokens": null, 
        "temperature": 1,
        "top_p": 0.9,
        "stream": false
    }'
```

#### Response
A successful generation response (non-streaming) will contain a `chat.completion` object, and should look like this:

```json
    {
    "id": "chatcmpl-7ba48f119a564f4ea02b6a41386a3e40",
    "created": 1740689977,
    "model": "Qwen/Qwen2.5-VL-7B-Instruct",
    "object": "chat.completion",
    "system_fingerprint": null,
    "choices": [
        {
            "finish_reason": "stop",
            "index": 0,
            "message": {
                "content": "This image shows ....",
                "role": "assistant",
                "tool_calls": null,
                "function_call": null
            }
        }
    ],
    "usage": {
        "completion_tokens": 91,
        "prompt_tokens": 3604,
        "total_tokens": 3695,
        "completion_tokens_details": null,
        "prompt_tokens_details": null
    },
    "service_tier": null,
    "prompt_logprobs": null
}
```

As is the case with text generation, if you set `stream` to True you can get the entire generated completion in 1 `chat.completion` object: 

```json
{
    "id": "chatcmpl-3812731562554b23a32dd80fbb7d0d09",
    "created": 1740692435,
    "model": "Qwen/Qwen2.5-VL-7B-Instruct",
    "object": "chat.completion.chunk",
    "choices": [
        {
            "index": 0,
            "delta": {
                "content": " setting"
            }
        }
    ]
}
{ 
  ...
}
...
```

For more examples, see the [Serverless Endpoints](../../Serverless_Endpoints/Text_Generation.md) section.
