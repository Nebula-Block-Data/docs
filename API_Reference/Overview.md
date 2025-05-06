# API Reference

Welcome to the Nebula Block API documentation. Our APIs are organized into different services, each with its own base URL and authentication methods.

## Base URLs

Different Nebula Block services use different base URLs:

| Service | Base URL | Description |
|---------|----------|-------------|
| Inference API | `https://inference.nebulablock.com/v1` | For all AI model inference (text, vision, embeddings) |
| Management API | `https://api.nebulablock.com/v1` | For managing instances, storage, billing, and other resources |

## Authentication

All API requests require authentication using your API key. You can obtain an API key from the [Nebula Block Dashboard](https://dashboard.nebulablock.com/settings/api-keys).

### Using API Keys

Add your API key to the request headers:

```bash
Authorization: Bearer YOUR_API_KEY
```

Example request:
```bash
curl https://inference.nebulablock.com/v1/chat/completions \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "meta-llama/Llama-3.3-70B-Instruct",
    "messages": [
      {"role":"user","content":"Is Montreal a thriving hub for the AI industry?"}
    ],
  }'
```

## Rate Limits

Please refer to your plan's documentation for specific rate limit information.

## API Services

### Inference API
- [Text Generation](Serverless_Endpoints/Generate_Text.md)
- [Vision Models](Serverless_Endpoints/Vision.md)
- [Image Generation](Serverless_Endpoints/Generate_Images.md)
- [Embeddings](Serverless_Endpoints/Generate_Embeddings.md)
- [List Available Models](Serverless_Endpoints/List_Serverless_Models.md)

### Instance Management API
- [List Images](Instances/List_images.md)
- [List Products](Instances/List_Products.md)
- [Create GPU Instance](Instances/Create_GPU_Instance.md)
- [List User Instances](Instances/List_User_Instances.md)
- [Instance Operations](Instances/Instance_Operations.md)

### Storage API
- [Bucket Operations](Storage/Buckets.md)
- [Object Operations](Storage/Objects.md)
- [Presigned URLs](Storage/Presigned_URLs.md)

### Billing API
- [Get Credit Balance](Billing/Get_Credit_Balance.md)
- [List Invoices](Billing/List_Invoices.md)
- [Payment History](Billing/Get_Payment_History.md)

## Response Formats

All API endpoints return responses in JSON format. A successful response includes:

```json
{
  "status": "success",
  "data": {
    // Response data
  }
}
```

Error responses follow this format:

```json
{
  "status": "error",
  "error": {
    "code": "error_code",
    "message": "Human-readable error message",
    "details": {
      // Additional error details
    }
  }
}
```

## Common Error Codes

| Code | Description |
|------|-------------|
| 400 | Bad Request - Invalid parameters |
| 401 | Unauthorized - Invalid API key |
| 403 | Forbidden - Insufficient permissions |
| 404 | Not Found - Resource doesn't exist |
| 429 | Too Many Requests - Rate limit exceeded |
| 500 | Internal Server Error |