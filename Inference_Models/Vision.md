# Text Generation (Vision)

**Vision models** behave similarly to text models, but they can accept and interpret images as well. 

## Models available

Available text models:

- Qwen2.5-VL-7B-Instruct: An advanced vision-lanauge model designed to understand and process both visual and textual inputs.

## Using the Models

1. Go to the [Nebula Block](https://www.nebulablock.com) website.
2. Log in, and ensure you have enough credits. 
3. Click on the "Inference Models" tab and select your model.
4. Select your parameters, enter your text (and image, if applicable) and just press Enter! 

The parameters to tweak are the same as in [Text Generation](Text_Generation.md), with the addition of the following:

- **Image**: The image to be processed by the model.

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
		{"role":"user","content":[
		{"type":"image_url","image_url":
		{"url":"https://qianwen-res.oss-cn-beijing.aliyuncs.com/Qwen-VL/assets/demo.jpeg"}},
		{"type":"text","text":"What is this image?"}
	]}],
    "model":"Qwen/Qwen2.5-VL-7B-Instruct",
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
    "Authorization": `Bearer sk-kmlKFCXGBZl-PS0MLnpzAw`
};

const data = {
    messages: [
        {"role":"user","content":[
        {"type":"image_url","image_url":
        {"url":"https://qianwen-res.oss-cn-beijing.aliyuncs.com/Qwen-VL/assets/demo.jpeg"}},
        {"type":"text","text":"What is this image?"}
    ]}],
    model: 'Qwen/Qwen2.5-VL-7B-Instruct',
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

- Qwen2.5-VL-7B-Instruct: `Qwen/Qwen2.5-VL-7B-Instruct`

#### Response Example 

A successful generation response (non-streaming) will contain a `chat.completion` object, and should look like this:

```json
    {
    "id": "chatcmpl-7ba48f119a564f4ea02b6a41386a3e40",
    "created": 1740689977,
    "model": "Qwen/Qwen2.5-VL-7B-Instruct",
    "object": "chat.completion",
    "system_fingerprint": null,
    "choices": [
        {
            "finish_reason": "stop",
            "index": 0,
            "message": {
                "content": "This image shows ....",
                "role": "assistant",
                "tool_calls": null,
                "function_call": null
            }
        }
    ],
    "usage": {
        "completion_tokens": 91,
        "prompt_tokens": 3604,
        "total_tokens": 3695,
        "completion_tokens_details": null,
        "prompt_tokens_details": null
    },
    "service_tier": null,
    "prompt_logprobs": null
}
```

As is the case with text generation, this represents the entire generated response, and setting the `stream` parameter to `True` will return the response in chunks: 

```json
{
    "id": "chatcmpl-3812731562554b23a32dd80fbb7d0d09",
    "created": 1740692435,
    "model": "Qwen/Qwen2.5-VL-7B-Instruct",
    "object": "chat.completion.chunk",
    "choices": [
        {
            "index": 0,
            "delta": {
                "content": " setting"
            }
        }
    ]
}
{ 
  ...
}
...
```

with the collection of chunks forming the entire response.

Feel free to explore refer to the [API Reference](../API_Reference/Inference_Models/Vision.md) for more details.