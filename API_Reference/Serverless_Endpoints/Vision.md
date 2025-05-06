---
# title: Generate Serverless Text (Vision)
description: Generate Serverless Text (Vision).
---

# Vision API

Generate text responses from images using our multimodal AI models.

## Endpoint

```
POST https://api.inference.nebulablock.com/v1/vision/generate
```

## Request Headers

| Header | Value |
|--------|-------|
| Authorization | Bearer YOUR_API_KEY |
| Content-Type | application/json |

## Request Body

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| model | string | Yes | Model ID (e.g., "gpt-4-vision", "claude-3-vision") |
| image | string or object | Yes | Image data (URL or base64) or image object |
| prompt | string | Yes | The text prompt describing what to analyze in the image |
| max_tokens | integer | No | Maximum number of tokens to generate (default: 300) |
| temperature | float | No | Sampling temperature between 0 and 2 (default: 0.7) |
| detail | string | No | Image analysis detail level: "low", "medium", or "high" (default: "medium") |

### Image Input Formats

You can provide the image in several formats:

```json
{
  // Option 1: Direct URL
  "image": "https://example.com/image.jpg"
}

{
  // Option 2: Base64 encoded image
  "image": {
    "data": "base64_encoded_image_data",
    "type": "image/jpeg"
  }
}

{
  // Option 3: Multiple image parts
  "image": [
    { "url": "https://example.com/image1.jpg" },
    { "data": "base64_encoded_image_data" }
  ]
}
```

### Example Request

```bash
curl https://api.inference.nebulablock.com/v1/vision/generate \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "gpt-4-vision",
    "image": "https://example.com/image.jpg",
    "prompt": "Describe what you see in this image",
    "max_tokens": 300,
    "detail": "high"
  }'
```

## Response

### Success Response

```json
{
  "status": "success",
  "data": {
    "text": "The image shows a scenic mountain landscape...",
    "usage": {
      "prompt_tokens": 50,
      "completion_tokens": 150,
      "total_tokens": 200
    }
  }
}
```

### Error Response

```json
{
  "status": "error",
  "error": {
    "code": "invalid_image",
    "message": "Unable to process image",
    "details": {
      "reason": "Image format not supported"
    }
  }
}
```

## Rate Limits

Rate limits apply based on your tier level. See [Rate Limits](../Overview.md#rate-limits) for details.

## Models

Available models for vision tasks:

| Model | Best For |
|-------|----------|
| Qwen2.5-VL-7B-Instruct | Advanced vision-language tasks, image understanding and analysis |

For detailed information about the model capabilities and latest updates, see [Model List](Model_List.md).

## Error Codes

| Code | Description |
|------|-------------|
| invalid_image | Image cannot be processed |
| image_too_large | Image exceeds size limits |
| unsupported_format | Image format not supported |
| rate_limit_exceeded | Too many requests |
| insufficient_quota | Not enough credits or quota |

## Code Examples

### Python

```python
from nebula_block import NebulaClient

client = NebulaClient(api_key="YOUR_API_KEY")

response = client.generate_vision(
    model="gpt-4-vision",
    image="https://example.com/image.jpg",
    prompt="Describe what you see in this image",
    max_tokens=300
)

print(response.text)
```

### JavaScript

```javascript
const { NebulaClient } = require('nebula-block');

const client = new NebulaClient({ apiKey: 'YOUR_API_KEY' });

async function analyzeImage() {
  const response = await client.generateVision({
    model: 'gpt-4-vision',
    image: 'https://example.com/image.jpg',
    prompt: 'Describe what you see in this image',
    maxTokens: 300
  });
  
  console.log(response.text);
}

analyzeImage();
```

## See Also

- [Model List](Model_List.md)
- [Text Generation API](Generate_Text.md)
- [Rate Limits](../Overview.md#rate-limits)
- [Authentication](../Authentication.md)
