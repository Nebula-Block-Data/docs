---
# title: Generate Embeddings 
description: Generate Embeddings From Text.
---

# Embeddings API

Generate vector embeddings from text using our embedding models. These embeddings can be used for semantic search, clustering, and other machine learning tasks.

## Endpoint

```
POST https://inference.nebulablock.com/v1/embeddings
```

## Request Headers

| Header | Value |
|--------|-------|
| Authorization | Bearer YOUR_API_KEY |
| Content-Type | application/json |

## Request Body

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| model | string | Yes | Model ID (e.g., "WhereIsAI/UAE-Large-V1") |
| input | string or array | Yes | Text to embed (string or array of strings) |
| encoding_format | string | No | Output format: "float" or "base64" (default: "float") |
| normalize | boolean | No | Whether to L2-normalize the embeddings (default: true) |

### Example Request

```bash
curl https://api.inference.nebulablock.com/v1/embeddings/generate \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "ada-002",
    "input": ["Hello world", "How are you?"],
    "encoding_format": "float"
  }'
```

## Response

### Success Response

```json
{
  "status": "success",
  "data": {
    "embeddings": [
      {
        "embedding": [0.0023, -0.0141, 0.0262, ...],
        "index": 0
      },
      {
        "embedding": [-0.0076, 0.0179, 0.0121, ...],
        "index": 1
      }
    ],
    "usage": {
      "prompt_tokens": 6,
      "total_tokens": 6
    },
    "model": "ada-002",
    "dimensions": 1536
  }
}
```

### Error Response

```json
{
  "status": "error",
  "error": {
    "code": "invalid_input",
    "message": "Input text is too long",
    "details": {
      "max_tokens": 8191,
      "input_tokens": 10000
    }
  }
}
```

## Rate Limits

Rate limits apply based on your tier level. See [Rate Limits](../Overview.md#rate-limits) for details.

## Models

Available models for generating embeddings:

| Model | Best For |
|-------|----------|
| UAE-Large-V1 | General-purpose text embeddings with high accuracy |
| BGE Large EN v1.5 | Optimized English text embeddings |

For detailed information about each model and their latest updates, see [Model List](Model_List.md).

## Embedding Formats

Embeddings can be returned in two formats:

1. **Float Array**: Default format, returns embeddings as arrays of floating-point numbers
2. **Base64**: Compressed format, useful for efficient storage and transmission

### Base64 Format Example

```json
{
  "status": "success",
  "data": {
    "embeddings": [
      {
        "embedding": "base64_encoded_string",
        "index": 0
      }
    ]
  }
}
```

## Error Codes

| Code | Description |
|------|-------------|
| invalid_input | Input text is invalid or too long |
| invalid_model | Specified model doesn't exist |
| batch_size_exceeded | Too many inputs in single request |
| rate_limit_exceeded | Too many requests |
| insufficient_quota | Not enough credits or quota |

## Code Examples

### Python

```python
from nebula_block import NebulaClient
import numpy as np

client = NebulaClient(api_key="YOUR_API_KEY")

# Generate embeddings for multiple texts
response = client.generate_embeddings(
    model="ada-002",
    input=["Hello world", "How are you?"]
)

# Convert to numpy arrays
embeddings = np.array([e["embedding"] for e in response.data["embeddings"]])

# Calculate similarity
similarity = np.dot(embeddings[0], embeddings[1])
print(f"Similarity: {similarity}")
```

### JavaScript

```javascript
const { NebulaClient } = require('nebula-block');

const client = new NebulaClient({ apiKey: 'YOUR_API_KEY' });

async function generateEmbeddings() {
  const response = await client.generateEmbeddings({
    model: 'ada-002',
    input: ['Hello world', 'How are you?']
  });
  
  // Get embeddings
  const embeddings = response.data.embeddings.map(e => e.embedding);
  
  // Calculate similarity (using dot product)
  const similarity = dotProduct(embeddings[0], embeddings[1]);
  console.log(`Similarity: ${similarity}`);
}

function dotProduct(a, b) {
  return a.reduce((sum, val, i) => sum + val * b[i], 0);
}

generateEmbeddings();
```

## Common Use Cases

1. **Semantic Search**
```python
# Create an index of documents
docs = ["First document", "Second document", "Third document"]
doc_embeddings = client.generate_embeddings(model="ada-002", input=docs)

# Search query
query = "Find similar documents"
query_embedding = client.generate_embeddings(model="ada-002", input=[query])

# Find similar documents using cosine similarity
similarities = np.dot(doc_embeddings, query_embedding.T)
```

2. **Clustering**
```python
from sklearn.cluster import KMeans

# Generate embeddings for your texts
embeddings = client.generate_embeddings(model="ada-002", input=texts)

# Perform clustering
kmeans = KMeans(n_clusters=3)
clusters = kmeans.fit_predict(embeddings)
```

## See Also

- [Model List](Model_List.md)
- [Rate Limits](../Overview.md#rate-limits)
- [Authentication](../Authentication.md)
- [Best Practices](../Best_Practices.md)
