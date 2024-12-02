
# API Integration
Once you’ve tested the live chat, you can integrate the endpoints into your applications.

## API Endpoint
`https://inference.nebulablock.com`

## Using cURL
```bash
curl -X POST "https://inference.nebulablock.com/v1/chat/completions" \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer YOUR_SERVERLESS_API_KEY" \
    --data-raw '{
        "messages": [
			{"role":"user","content":"Is Montreal a thriving hub for the AI industry?"}
		],
        "model": "llama3.1-70b",
        "max_tokens": 512, 
        "temperature": 1,
        "top_p": 0.9,
        "stream": false
    }'

```

## Using Python

```python
import openai
 
OPENAI_BASE_URL = "https://inference.nebulablock.com"
OPENAI_API_KEY = "YOUR_SERVERLESS_API_KEY"
 
client = openai.OpenAI(
    api_key=OPENAI_API_KEY,
    base_url=OPENAI_BASE_URL,
)
 
response = client.chat.completions.create(
    messages=[
		{"role":"user","content":"Is Montreal a thriving hub for the AI industry?"}
	],
    model="llama3.1-70b",
    max_tokens=512,
    temperature=1,
    top_p=0.9,
    stream=False
)
print(response)
```

## Using JavaScript
```javascript
import OpenAI from 'openai'; 

const openai = new OpenAI({ 
  apiKey: 'YOUR_SERVERLESS_API_KEY', 
  baseURL: 'https://inference.nebulablock.com'
}); 

async function main() { 
  const completion = await openai.chat.completions.create({ 
    messages=[
			{"role":"user","content":"Is Montreal a thriving hub for the AI industry?"}
		], 
    model: 'llama3.1-70b',  
    max_tokens: 512, 
    temperature: 1,
    top_p: 0.9,
    stream: false
  }); 
  console.log(completion.choices); 
} 

main(); 
```