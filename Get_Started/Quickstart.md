# Quickstart Guide

This guide will help you get started with Nebula Block in minutes. Follow these steps to begin using our AI cloud platform.

## 1. Create Your Account

1. Visit [nebulablock.com](https://nebulablock.com)
2. Click "Sign Up" in the top right corner
3. Enter your email and create a password
4. Verify your email address

## 2. Set Up Billing

1. Navigate to Account Settings → Billing
2. Add a payment method
3. Configure Auto-Pay

## 3. Get Your API Key

```bash
# Get an API key from the dashboard
Account Settings → API Keys

# Store it securely in your environment
export NEBULA_API_KEY='your_api_key'
```

## 4. Making API Requests

Our API endpoints are organized by service:

- Inference API: https://inference.nebulablock.com/v1
- Management API: https://api.nebulablock.com/v1

Here are some examples using curl:

### Text Generation

```bash
curl -X POST "https://inference.nebulablock.com/v1/chat/completions" \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $NEBULA_API_KEY" \
    --data-raw '{
        "messages": [
			{"role":"user","content":"Is Montreal a thriving hub for the AI industry?"}
		],
        "model": "Qwen/Qwen2.5-Coder-32B-Instruct",
        "max_tokens": null, 
        "temperature": 1,
        "top_p": 0.9,
        "stream": false
    }'
```

### Image Generation

```bash
curl -X POST "https://api.nebulablock.com/api/v1/images/generation" \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $NEBULA_API_KEY" \
    --data-raw '{
      "model":"stabilityai/stable-diffusion-xl-base-1.0",
      "prompt":"A futuristic city with flying cars",
      "num_steps":25,
      "guidance_scale":9,
      "negative_prompt":null,
      "width":1024,
      "height":1024
    }'
```

### Vision

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

### Embeddings

```bash
curl -X POST "https://inference.nebulablock.com/v1/embeddings" \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $NEBULA_API_KEY" \
    --data-raw '{
      "model":"WhereIsAI/UAE-Large-V1",
      "input":[ 
            "Bananas are berries, but strawberries are not, according to botanical classifications.",  
            "The Eiffel Tower in Paris was originally intended to be a temporary structure." 
        ] 
    }'
```

## 5. Next Steps

- [Explore available models](../Serverless_Endpoints/Model_List.md)
- [Learn about GPU instances](../GPU_Instances/Overview.md)
- [Set up object storage](../Object_Storage/Getting_Started.md)
- [View API documentation](../API_Reference/Overview.md)

## Need Help?

- Check our [documentation](../Overview.md)
- Contact [support](../Contact_Us/README.md)

