
# Image Generation

Use these models to generate whatever images you can (or can't!) imagine. Each model will support some combination of the following
parameters: 

- prompt: The prompt to guide the model's generation.
- negative_prompt: A prompt to guide the model away from generating certain content.
- width, height: The resolution of the output image. 
- steps: Number of inference steps that the model will take. A higher number of steps typically 
leads to better quality but costs more. 
- guidance scale: A high value encourages the model adhere closely to the prompt, but may result in a lower image quality.
- seed: A number to seed the generation. Using the same value ensures reproducibility. 

`prompt` is the only mandatory parameter. The rest are given default values for optimal performance.

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



### Using the Models

##### Through our website UI 

1. Go to the [Nebula Block](https://nebula-block.com) website.
2. Log in, and ensure you have enough credits. 
3. Click on the "Serverless Endpoints" tab and select your model.
4. Choose your parameters, enter your prompt and just press Enter! 

##### Through API Endpoint

This option is great if you want to use our API endpoint directly in your projects.

To specify the desired model, use this mapping for the `model_name`: 
- StableDiffusion XL 1.0: `stabilityai/stable-diffusion-xl-base-1.0` 
- Flux.1 schnell: `black-forest-labs/FLUX.1-schnell`

Below are some code snippets (using StableDiffusion XL 1.0) to get you started. A successful response body will return the image in this format: 

```json
{
  "image_b64": "iVBORw0KGgoAAAANSUhEUgAAB..."
}
```

## Using cURL
```bash
curl -X POST "https://api.nebulablock.com/api/v1/images/generation" \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $NEBULA_API_KEY" \
    --data-raw '{
      "model_name":"stabilityai/stable-diffusion-xl-base-1.0",
      "prompt":"",
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
    "prompt":"",
    "num_steps":25,
    "guidance_scale":9,
    "negative_prompt": null,
    "width":1024,
    "height":1024
}

response = requests.post(url, headers=headers, json=data) 
print(response.json())
```

## Using JavaScript

```javascript
const fetchImage = async () => { 

const url = 'https://api.nebulablock.com/api/v1/images/generation'; 

const response = await fetch(url, {
  method: 'POST',  

  headers: {  
    'Content-Type': 'application/json',  
    'Authorization': 'Bearer ${process.env.NEBULA_API_KEY}',  
  },  

  body: JSON.stringify({  
      "model_name":"stabilityai/stable-diffusion-xl-base-1.0",
      "prompt":"",
      "num_steps":25,
      "guidance_scale":9,
      "negative_prompt":null,
      "width":1024,
      "height":1024
  })
}); 

const json = await response.json();
```

For more information on our API, please see the [API Reference docs](API_Reference/).