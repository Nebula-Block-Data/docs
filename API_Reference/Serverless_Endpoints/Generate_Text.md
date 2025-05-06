---
# title: Generate Serverless Text 
description: Generate Serverless Text.
---

# Text Generation API

Generate text using our serverless AI models.

## Endpoint

```
POST https://api.inference.nebulablock.com/v1/text/generate
```

## Request Headers

| Header | Value |
|--------|-------|
| Authorization | Bearer YOUR_API_KEY |
| Content-Type | application/json |

## Request Body

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| model | string | Yes | Model ID (e.g., "gpt-4", "claude-2", "llama-2-70b") |
| prompt | string | Yes | The input prompt for text generation |
| max_tokens | integer | No | Maximum number of tokens to generate (default: 256) |
| temperature | float | No | Sampling temperature between 0 and 2 (default: 0.7) |
| top_p | float | No | Nucleus sampling parameter between 0 and 1 (default: 1) |
| stop | array | No | Array of strings that will stop generation when encountered |
| stream | boolean | No | Whether to stream the response (default: false) |

### Example Request

```bash
curl https://api.inference.nebulablock.com/v1/text/generate \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "gpt-4",
    "prompt": "Write a hello world program in Python",
    "max_tokens": 100,
    "temperature": 0.7
  }'
```

## Response

### Success Response

```json
{
  "status": "success",
  "data": {
    "text": "Here's a simple Hello World program in Python:\n\nprint(\"Hello, World!\")",
    "usage": {
      "prompt_tokens": 8,
      "completion_tokens": 12,
      "total_tokens": 20
    }
  }
}
```

### Error Response

```json
{
  "status": "error",
  "error": {
    "code": "invalid_request",
    "message": "Invalid model specified",
    "details": {
      "model": "Model 'invalid-model' not found"
    }
  }
}
```

## Streaming Response

When `stream: true` is set, the response will be streamed as server-sent events:

```bash
curl https://api.inference.nebulablock.com/v1/text/generate \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "gpt-4",
    "prompt": "Write a hello world program",
    "stream": true
  }'
```

Each event will contain a chunk of the generated text:

```
data: {"text": "Here's", "finish_reason": null}

data: {"text": " a", "finish_reason": null}

data: {"text": " simple", "finish_reason": null}

data: {"text": " Hello", "finish_reason": null}

data: {"text": " World", "finish_reason": null}

data: {"text": " program", "finish_reason": null}

data: {"text": ":", "finish_reason": null}

data: {"text": "\n\nprint(\"Hello, World!\")", "finish_reason": "stop"}
```

## Rate Limits

Rate limits apply based on your tier level. See [Rate Limits](../Overview.md#rate-limits) for details.

## Models

Available models for text generation:

| Model | Best For |
|-------|----------|
| DeepSeek-V3-0324 | General text generation with high accuracy |
| DeepSeek-R1-Distill-Llama-70B | Complex queries requiring detailed responses |
| DeepSeek-R1-Distill-Qwen-32B | Efficient text generation with lower latency |
| Llama3.3-70B | Advanced conversational AI and knowledge tasks |
| Qwen-QwQ-32B | Reasoning and problem-solving tasks |
| Qwen2.5-Coder-32B | Code generation and technical documentation |

For detailed information about each model and their latest updates, see [Model List](Model_List.md).

## Error Codes

| Code | Description |
|------|-------------|
| invalid_request | Invalid parameters in the request |
| model_not_found | Specified model doesn't exist |
| context_length_exceeded | Input prompt is too long |
| rate_limit_exceeded | Too many requests |
| insufficient_quota | Not enough credits or quota |

## Code Examples

### Python

```python
from nebula_block import NebulaClient

client = NebulaClient(api_key="YOUR_API_KEY")

response = client.generate_text(
    model="gpt-4",
    prompt="Write a hello world program in Python",
    max_tokens=100
)

print(response.text)
```

### JavaScript

```javascript
const { NebulaClient } = require('nebula-block');

const client = new NebulaClient({ apiKey: 'YOUR_API_KEY' });

async function generateText() {
  const response = await client.generateText({
    model: 'gpt-4',
    prompt: 'Write a hello world program in Python',
    maxTokens: 100
  });
  
  console.log(response.text);
}

generateText();
```

## See Also

- [Model List](Model_List.md)
- [Vision API](Vision.md)
- [Rate Limits](../Overview.md#rate-limits)
- [Authentication](../Authentication.md)
