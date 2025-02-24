---
# title: Generate Serverless Images 
description: Generate Serverless Images.
---

# Generte Serverless Images

Return the generated image based on the given inputs. 

## HTTP Request

`POST` `{API_URL}/images/generation`

where `API_URL = https://api.nebulablock.com/api/v1`. 

> **Note**: As a reminder, the only mandatory parameter in the request body is "prompt", so your request could look as 
> simple as this: 
> ```json 
> {"prompt": "a flying cat"}
> ```
> To specify more parameters, see the ones available at the [Serverless Endpoints](../../Serverless_Endpoints/Image_Generation.md) section.

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
curl -X GET '{API_URL}/api/v1/images/generation' \
-H 'Authorization: Bearer {TOKEN/KEY}' \
-H 'Content-Type: application/json' \
-d '{
    "model_name": "stabilityai/stable-diffusion-xl-base-1.0",
    "prompt": "insert your prompt here",
    "num_steps": 25,
    "guidance_scale": 9,
    "width": 1024,
    "height": 1024,
    "negative_prompt": null
}'
```

#### Response

Here's an example of a successful response. It consists of a stream of `data` dictionaries, each containing the data for 
a generated token. The entire collection of dictionaries represents the complete generated response. 

```json
{
    "model": "black-forest-labs/FLUX.1-schnell",
    "object": "list",
    "data": [
        {
            "timings": {
                "inference": 4.76837158203125e-07
            },
            "index": 0,
            "b64_json": "3hfjsd..."
        }
    ]
}
```
