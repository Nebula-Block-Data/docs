
# Image Generation

Use these models to generate whatever images you can (or can't!) imagine. Bolded parameters are supported across all models, 
while unbolded paramters are specific to certain models: 

- **Prompt**: The prompt to guide the model's generation.
- Negative Prompt: A prompt to guide the model away from generating certain content.
- **Width, Height**: The resolution of the output image. 
- **Steps**: Number of inference steps that the model will take. A higher number of steps typically 
leads to better quality but costs more. 
- **Guidance Scale**: A high value encourages the model adhere closely to the prompt, but may result in a lower image quality.
- Seed: A number to seed the generation. Using the same value ensures reproducibility. 

`prompt` is the only mandatory parameter (the rest are given standard defaults).

## Models available

Here's a table for the models available, and the parameters they support. 

| Parameter         | StableDiffusion XL | Flux.1 schnell |
|-------------------|--------------------|----------------|
| `prompt`          | ✓                  | ✓              |
| `negative_prompt` | ✓                  |                |
| `width`           | ✓                  | ✓              |
| `height`          | ✓                  | ✓              |
| `num_steps`       | ✓                  | ✓              |
| `guidance_scale`  | ✓                  | ✓              |
| `seed`            |                    | ✓              |



## Using the Models

##### Through Our Website UI 

1. Go to the [Nebula Block](https://www.nebulablock.com) website.
2. Log in, and ensure you have enough credits. 
3. Click on the "Serverless Endpoints" tab and select your model.
4. Choose your parameters, enter your prompt and just press Enter! 

##### Through API Endpoint

This option is to use our API endpoint directly in your projects. Below are some code snippets to get you started! 

## Using cURL
```bash
curl -X POST "https://api.nebulablock.com/api/v1/images/generation" \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $NEBULA_API_KEY" \
    --data-raw '{
      "model_name":"stabilityai/stable-diffusion-xl-base-1.0",
      "prompt":"a flying cat",
      "num_steps":25,
      "guidance_scale":9,
      "negative_prompt":null,
      "width":1024,
      "height":1024
    }'
```

## Using Python

```python
import requests 
import os

url = "https://api.nebulablock.com/api/v1/images/generation" 

headers = {  
    "Content-Type": "application/json",  
    "Authorization": f"Bearer {os.environ.get('NEBULA_API_KEY')}" 
} 

data = {
    "model_name":"stabilityai/stable-diffusion-xl-base-1.0",
    "prompt":"a flying cat",
    "num_steps":25,
    "guidance_scale":9,
    "negative_prompt": None,
    "width":1024,
    "height":1024
}

response = requests.post(url, headers=headers, json=data) 
print(response.json())
```

## Using JavaScript

```javascript
const url = 'https://api.nebulablock.com/api/v1/images/generation';

const headers = {
    "Content-Type": "application/json",
    "Authorization": `Bearer ${process.env.NEBULA_API_KEY}`
};

const data = {
    "model_name": "stabilityai/stable-diffusion-xl-base-1.0",
    "prompt": "",
    "num_steps": 25,
    "guidance_scale": 9,
    "negative_prompt": null,
    "width": 1024,
    "height": 1024
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

> **NOTE:**  Don't forget to use **your** API key. See [here](../API_Reference/Authentication.md) and [here](../API_Key/Overview.md) for more details on authentication. 

A successful response body will return the image in this format: 

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
            "b64_json": "sjkkc9j34m..."
        }
    ],
    "message": "Image generated successfully",
    "status": "success"
}
```

> **NOTE:** You'll need to use an image b64 decoder to view the result. Just pass in the b64_json value to the decoder of your choice.

To specify the desired model, use this mapping for the `model_name`: 
- StableDiffusion XL 1.0: `stabilityai/stable-diffusion-xl-base-1.0` 
- Flux.1 schnell: `black-forest-labs/FLUX.1-schnell`

Feel free to explore refer to the [API Reference](../API_Reference/Serverless_Endpoints/Generate_Images.md) for more details.