---
# title: Generate Serverless Images 
description: Generate Serverless Images.
---

# Generate Serverless Images

Return the generated image based on the given inputs. 

## HTTP Request

`POST` `{API_URL}/images/generation`

where `API_URL = https://api.nebulablock.com/api/v1`. For more details on the parameters, see the [Serverless Endpoints](../../Serverless_Endpoints/Image_Generation.md) section.

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

For more examples, see the [Serverless Endpoints](../../Serverless_Endpoints/Image_Generation.md) section.

# Image Generation API

Generate images from text descriptions using our state-of-the-art image generation models.

## Endpoint

```
POST https://api.inference.nebulablock.com/v1/images/generate
```

## Request Headers

| Header | Value |
|--------|-------|
| Authorization | Bearer YOUR_API_KEY |
| Content-Type | application/json |

## Request Body

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| model | string | Yes | Model ID (e.g., "dall-e-3", "sdxl") |
| prompt | string | Yes | Text description of the image to generate |
| n | integer | No | Number of images to generate (default: 1, max: 10) |
| size | string | No | Image size (e.g., "1024x1024", "512x512") |
| quality | string | No | Image quality: "standard" or "hd" (default: "standard") |
| style | string | No | Style preset: "natural", "vivid", "artistic" (default: "natural") |
| negative_prompt | string | No | Things to avoid in the generated image |

### Example Request

```bash
curl https://api.inference.nebulablock.com/v1/images/generate \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "dall-e-3",
    "prompt": "A serene mountain lake at sunset",
    "n": 1,
    "size": "1024x1024",
    "quality": "hd",
    "style": "natural"
  }'
```

## Response

### Success Response

```json
{
  "status": "success",
  "data": {
    "images": [
      {
        "url": "https://storage.nebulablock.com/generated/abc123.png",
        "b64_json": null
      }
    ],
    "usage": {
      "images_generated": 1,
      "resolution": "1024x1024"
    }
  }
}
```

### Error Response

```json
{
  "status": "error",
  "error": {
    "code": "content_policy_violation",
    "message": "Your request was rejected as it violates our content policy",
    "details": {
      "reason": "Contains prohibited content"
    }
  }
}
```

## Rate Limits

Rate limits apply based on your tier level. See [Rate Limits](../Overview.md#rate-limits) for details.

## Models

Available models for image generation:

### Text-to-Image Models
| Model | Best For |
|-------|----------|
| StableDiffusion XL 1.0 | High-quality images with detailed control |
| Flux.1 schnell | Fast generation with efficient processing |

### Image-to-Image Models
| Model | Best For |
|-------|----------|
| Flux.1 Fill Dev | Image inpainting and selective area modification |

For detailed information about each model and their latest updates, see [Model List](Model_List.md).

## Image Formats and Delivery

Images can be returned in two formats:
1. **URL**: A temporary URL to download the generated image (default)
2. **Base64**: The image encoded as a base64 string (set `response_format: "b64_json"`)

URLs are valid for 1 hour after generation.

## Content Policy

All images must comply with our content policy. We do not allow:
- Adult or explicit content
- Violence or gore
- Hate speech or discrimination
- Copyright infringement
- Personal information

## Error Codes

| Code | Description |
|------|-------------|
| invalid_prompt | Prompt is empty or invalid |
| content_policy_violation | Prompt violates content policy |
| invalid_size | Requested size not supported |
| rate_limit_exceeded | Too many requests |
| insufficient_quota | Not enough credits or quota |

## Code Examples

### Python

```python
from nebula_block import NebulaClient

client = NebulaClient(api_key="YOUR_API_KEY")

response = client.generate_image(
    model="dall-e-3",
    prompt="A serene mountain lake at sunset",
    size="1024x1024",
    quality="hd"
)

# Download the image
import requests
image_url = response.data["images"][0]["url"]
image_data = requests.get(image_url).content
with open("generated_image.png", "wb") as f:
    f.write(image_data)
```

### JavaScript

```javascript
const { NebulaClient } = require('nebula-block');

const client = new NebulaClient({ apiKey: 'YOUR_API_KEY' });

async function generateImage() {
  const response = await client.generateImage({
    model: 'dall-e-3',
    prompt: 'A serene mountain lake at sunset',
    size: '1024x1024',
    quality: 'hd'
  });
  
  // Download the image
  const imageUrl = response.data.images[0].url;
  const imageResponse = await fetch(imageUrl);
  const blob = await imageResponse.blob();
  // Save or display the image
}

generateImage();
```

## See Also

- [Model List](Model_List.md)
- [Content Policy](../Content_Policy.md)
- [Rate Limits](../Overview.md#rate-limits)
- [Authentication](../Authentication.md)