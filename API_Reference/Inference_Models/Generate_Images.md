---
# title: Generate Images 
description: Generate Images.
---

# Generate Images

Return the generated image based on the given inputs. 

## HTTP Request

`POST` `{API_URL}/images/generation`

where `API_URL = https://api.nebulablock.com/api/v1`. For more details on the parameters, see the [Inference Models](../../Inference_Models/Image_Generation.md) section.

## Response Attributes

#### model `string`
The specific AI model used to generate the response.

#### object `string`
The type of the data. 

#### data `list`

A list of dictionaries containing the generated image data. Each dictionary contains the following fields:
- **timings** `dict`: Contains the time taken for inference.
  - **inference** `float`: The time taken for inference in seconds.
- **index** `integer`: The index of the generated image (if more than 1 image is generated).
- **b64_json** `string`: The base64-encoded JSON data of the generated image.

#### message `string`
A message indicating the status of the request.

#### status `string`
The status of the request.

## Example

#### Request

##### Text-to-Image Generation

```bash
curl -X GET '{API_URL}/api/v1/images/generation' \
-H 'Authorization: Bearer {TOKEN/KEY}' \
-H 'Content-Type: application/json' \
-d '{
    "model": "stabilityai/stable-diffusion-xl-base-1.0",
    "prompt": "insert your prompt here",
    "num_steps": 25,
    "guidance_scale": 9,
    "width": 1024,
    "height": 1024,
    "negative_prompt": null
}'
```

##### Image-to-Image Generation

```bash
curl -X POST "https://api.nebulablock.com/api/v1/images/generation" \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $NEBULA_API_KEY" \
    --data-raw '{
    "model":"black-forest-labs/FLUX.1-Fill-dev",
    "prompt": "a red baseball cap",
    "num_steps": 40,
    "guidance_scale": 4.5,
    "width": 1024,
    "height": 1024,
    "image": "/9j/4…/Z", 
    "mask": "/9j/4…ACgD/9k="
}'
```

#### Response

Here's an example of a successful response. Note that you need to decode the b64 json data with a decoder of your choice to 
see the image. 

```json
{
    "model": "black-forest-labs/FLUX.1-schnell",
    "object": "list",
    "data": [
        {
            "timings": {
                "inference": 13.366829872131348
            },
            "index": 0,
            "b64_json": "sdj23kjjk2..."
        }
    ],
    "message": "Image generated successfully",
    "status": "success"
}
```

For more examples, see the [Inference Models](../../Inference_Models/Image_Generation.md) section.