# Text Generation

Use these models to generate text, whether it's to review code, write a story, etc.

## Models available

Available text models:

- DeepSeek-R1-Distill-Llama-70B: High-quality text generation for complex queries.
- DeepSeek-R1-Distill-Qwen-32B: Efficient text generation with lower resource usage.
- Llama3.3-70B: Advanced conversational AI with extensive knowledge.
- Llama3.1-8B: General-purpose text generation at low cost.
- Qwen2.5-Coder-32B: Specialized in code generation and completion.

## Using the Models

1. Go to the [Nebula Block](https://www.nebulablock.com) website.
2. Log in, and ensure you have enough credits. 
3. Click on the "Serverless Endpoints" tab and select your model.
4. Select your parameters, enter your text (and image, if applicable) and just press Enter! 

The parameters you can tweak are outlined below: 

- Messages: The current dialogue between the user and the model. 
- System Prompt: Set of instructions, guidelines, and contextual information, which tell the AI how to respond to the queries.
- Output Length: The maximum number of tokens that will be generated for each response. 
- Temperature: Temperature controls randomness. Higher values increase diversity.
- Top P: A higher value will result in more diverse outputs, while a lower value will result in more repetitive outputs.
- Stream: If set to `true`, the response will be streamed in chunks. If False, the entire generation will be returned in one response.

### Through API Endpoint

This option is to use our API endpoint directly in your projects. Below are some code snippets to get you started!

> **NOTE:**  Don't forget to use **your** API key. See the [API Reference](../API_Reference/Authentication.md) and the [Overview](../API_Key/Overview.md) for more details on authentication.

#### Using cURL
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

#### Using Python
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

#### Using JavaScript
```javascript
const url = "https://inference.nebulablock.com/v1/chat/completions";

const headers = {
    "Content-Type": "application/json",
    "Authorization": `Bearer ${process.env.NEBULA_API_KEY}`
};

const data = {
    messages: [
        { role: "user", content: "Is Montreal a thriving hub for the AI industry?" }
    ],
    model: "meta-llama/Llama-3.1-8B-Instruct",
    max_tokens: null,
    temperature: 1,
    top_p: 0.9,
    stream: false
};

fetch(url, {
    method: 'POST',
    headers: headers,
    body: JSON.stringify(data)
})
    .then(response => response.json())
    .then(data => {
        console.log(JSON.stringify(data, null, 2));
    })
    .catch(error => console.error('Error:', error));
```

#### Selecting a Model 

To specify the desired model, use this mapping for the `model_name`: 

- DeepSeek-R1-Distill-Llama-70B: `deepseek-ai/DeepSeek-R1-Distill-Llama-70B`
- DeepSeek-R1-Distill-Qwen-32B: `deepseek-ai/DeepSeek-R1-Distill-Qwen-32B`
- Llama3.3-70B: `meta-llama/Llama-3.3-70B-Instruct`
- Llama3.1-8B: `meta-llama/Llama-3.1-8B-Instruct`
- Qwen2.5-Coder-32B: `Qwen/Qwen2.5-Coder-32B-Instruct`

#### Response Example 

A successful generation response (non-streaming) will contain a `chat.completion` object, and should look like this: 

```json
{
    "id": "chatcmpl-ec0014bc38e2cad1e45d47f7f01f6569",
    "created": 1740432179,
    "model": "meta-llama/Llama-3.1-8B-Instruct",
    "object": "chat.completion",
    "system_fingerprint": null,
    "choices": [
        {
            "finish_reason": "stop",
            "index": 0,
            "message": {
                "content": "Yes! Montreal is the home of cutting edge ... research.",
                "role": "assistant",
                "tool_calls": null,
                "function_call": null
            }
        }
    ],
    "usage": {
        "completion_tokens": 695,
        "prompt_tokens": 42,
        "total_tokens": 737,
        "completion_tokens_details": null,
        "prompt_tokens_details": null
    },
    "service_tier": null,
    "prompt_logprobs": null
}
```

This represents the entire generated response from the inference. Alternatively, the streaming option (`stream: true` in the request body) will return several responses, each containing a `chat.completion.chunk` object, and will look like this: 

```json
{
    "id": "chatcmpl-289eb1f670a58c5cde47ddb634aad595",
    "created": 1740432271,
    "model": "meta-llama/Llama-3.1-8B-Instruct",
    "object": "chat.completion.chunk",
    "choices": [
        {
            "index": 0,
            "delta": {
                "content": " everyone"
            }
        }
    ]
}
{ 
  ...
}
...
```

where the content of each response will contain the generated token. These tokens put together form the complete response.

Feel free to explore refer to the [API Reference](../API_Reference/Serverless_Endpoints/Generate_Text.md) for more details.