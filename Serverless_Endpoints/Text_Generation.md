
# Image Generation

Use these models to generate text. Each model will support these parameters: 

- messages: The current dialogue between the user and the model. 
- system prompt: Set of instructions, guidelines, and contextual information, which tell the AI how to respond to the queries.
- output length: The maximum number of tokens that will be generated for each response. 
- temperature: Temperature controls randomness, higher values increase diversity.
- top_p: A higher value will result in more diverse outputs, while a lower value will result in more repetitive outputs.

`messages` is the only mandatory parameter. The rest are given default values.

## Models available

Listed below are the available models (each supporting the parameters above): 

- DeepSeek-R1-Distill-Llama-70B
- DeepSeek-R1-Distill-Qwen-32B 
- Llama3.3-70B
- Llama3.1-8B
- Qwen2.5-Coder-32B

### Using the Models

##### Through our website UI 

1. Go to the [Nebula Block](https://nebula-block.com) website.
2. Log in, and ensure you have enough credits. 
3. Click on the "Serverless Endpoints" tab and select your model.
4. Select your parameters, enter your text and just press Enter! 

##### Through API Endpoint

This option is great if you want to use our API endpoint directly in your projects. To specify the desired model, use this mapping for the `model_name`: 

- DeepSeek-R1-Distill-Llama-70B: `deepseek-ai/DeepSeek-R1-Distill-Llama-70B`
- DeepSeek-R1-Distill-Qwen-32B: `deepseek-ai/DeepSeek-R1-Distill-Qwen-32B`
- Llama3.3-70B: `meta-llama/Llama-3.3-70B-Instruct`
- Llama3.1-8B: `meta-llama/Llama-3.1-8B-Instruct`
- Qwen2.5-Coder-32B: `Qwen/Qwen2.5-Coder-32B-Instruct`

A successful generation consists of a stream of responses: 

```json
{
    "id": "chatcmpl-86800105604e81c7918d10b45fd46fa3",
    "created": 1740006821,
    "model": "meta-llama/Llama-3.1-8B-Instruct",
    "object": "chat.completion.chunk",
    "choices": [
        {
            "index": 0,
            "delta": {
                "content": "Yes",
                "role": "assistant"
            }
        }
    ]
}
```

where the content of each response will contain the generated token. These tokens put together form the complete response.

Below are some code snippets to get you started!

## Using cURL
```bash
curl -X POST "https://inference.nebulablock.com/v1/chat/completions" \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $NEBULA_API_KEY" \
    --data-raw '{
        "messages": [
			{"role":"user","content":"Is Montreal a thriving hub for the AI industry?"}
		],
        "model": "meta-llama/Llama-3.1-8B-Instruct",
        "max_tokens": null, 
        "temperature": 1,
        "top_p": 0.9,
        "stream": false
    }'
```

## Using Python

```python
import requests 
import os
 
url = "https://inference.nebulablock.com/v1/chat/completions"

headers = { 
    "Content-Type": "application/json", 
    "Authorization": f"Bearer {os.environ.get('NEBULA_API_KEY')}" 
} 
 
data = {
    "messages":[
		{"role":"user","content":"Is Montreal a thriving hub for the AI industry?"}
	],
    "model":"meta-llama/Llama-3.1-8B-Instruct",
    "max_tokens":None,
    "temperature":1,
    "top_p":0.9,
    "stream":False
}

response = requests.post(url, headers=headers, json=data) 
print(response.json())
```

## Using JavaScript
```javascript
import OpenAI from 'openai'; 

const openai = new OpenAI({ 
  apiKey: process.env.NEBULA_API_TOKEN, 
  baseURL: 'https://inference.nebulablock.com/v1/chat/completions'
}); 

async function main() { 
  const completion = await openai.chat.completions.create({ 
    messages=[
			{"role":"user","content":"Is Montreal a thriving hub for the AI industry?"}
		], 
    model: 'meta-llama/Llama-3.1-8B-Instruct',  
    max_tokens: null, 
    temperature: 1,
    top_p: 0.9,
    stream: false
  }); 
  console.log(completion.choices); 
} 

main(); 
```

For more information on API access, refer to the [API Reference](API_Reference/).