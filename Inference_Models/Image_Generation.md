
# Image Generation

Use these models to generate whatever images you can (or can't!) imagine. 

## Models available

Here's a table for the models available, and the parameters they support. 

| Parameter         | StableDiffusion XL | Flux.1 schnell | Flux.1 Fill Dev | 
|-------------------|--------------------|----------------|-----------------|
| `prompt`          | ✓                  | ✓              | ✓               | 
| `negative_prompt` | ✓                  |                |                 | 
| `width`           | ✓                  | ✓              | ✓               | 
| `height`          | ✓                  | ✓              | ✓               | 
| `num_steps`       | ✓                  | ✓              | ✓               | 
| `guidance_scale`  | ✓                  | ✓              | ✓               | 
| `seed`            |                    | ✓              |                 | 
| `input_image`     |                    |                | ✓               | 
| `mask_image`      |                    |                | ✓               |

##### Parameters 

- Prompt: The prompt to guide the model's generation.
- Negative Prompt: A prompt to guide the model away from generating certain content.
- Width, Height: The resolution of the output image. 
- Steps: Number of inference steps that the model will take. A higher number of steps typically 
leads to better quality but costs more. 
- Guidance Scale: A high value encourages the model adhere closely to the prompt, but may result in a lower image quality.
- Seed: A number to seed the generation. Using the same value ensures reproducibility.
- Input Image: The image to use as a base for the generation. When using our API, this should be a base64 encoded image.
- Mask Image: The mask to use for the generation. In other words, a mask to specify which areas of the image should be modified. White pixels in the mask are repainted (preserved from the input image) while black pixels are preserved. When using our API, this should be a base64 encoded image.

> **NOTE:** For best results, ensure that the mask dimensions are the same as the image. 
> **NOTE:** The Flux.1 Fill Dev model requires that the height and width are divisible by 16. If not, it will automatically resize the dimensions accordingly. 

##### Text-to-Image models

Text-to-Image models generate an image based on the prompt input. We currently support: 

- **StableDiffusion XL 1.0**: Generates images by iteratively updating with noise, guided by a prompt.
- **Flux.1 schnell**: Quickly generates images efficiently, based on the Flux model.

##### Image-to-Image models
Image-to-Image models generate images based on the input image and mask image in addition to the prompt. We currently support:

- **Flux.1 Fill Dev**: Fills in missing parts of an image using a provided mask.

## Using the Models

### Through Our Website UI 

Our website UI is the easiest and fastest way to use our endpoints. 

1. Go to the [Nebula Block](https://www.nebulablock.com) website.
2. Log in, and ensure you have enough credits. 
3. Click on the "Inference Models" tab and select your model.
4. Choose your parameters, enter your prompt (and image + mask if applicable) and just press Enter!

> **NOTE:** We support JPG, JPEG, PNG, and WebP image formats. 

### Through API Endpoint

This option is to use our API endpoint directly in your projects. Below are some code snippets to get you started!

> **NOTE:**  Don't forget to use **your** API key. See the [API Reference](../API_Reference/Authentication.md) and the [Overview](../API_Key/Overview.md) for more details on authentication.

#### Using cURL

##### Text-to-Image Model

```bash
curl -X POST "https://api.nebulablock.com/api/v1/images/generation" \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $NEBULA_API_KEY" \
    --data-raw '{
      "model":"stabilityai/stable-diffusion-xl-base-1.0",
      "prompt":"a flying cat",
      "num_steps":25,
      "guidance_scale":9,
      "negative_prompt":null,
      "width":1024,
      "height":1024
    }'
```

##### Image-to-Image Model

```bash
curl -X POST "https://api.nebulablock.com/api/v1/images/generation" \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $NEBULA_API_KEY" \
    --data-raw '{
    "model":"black-forest-labs/FLUX.1-Fill-dev",
    "prompt": "a red baseball cap",
    "num_steps": 40,
    "guidance_scale": 4.5,
    "width": 1024,
    "height": 1024,
    "image": "/9j/4…/Z", 
    "mask": "/9j/4…ACgD/9k="
}'
```

where `"input_image"` and `"mask_image"` are base64 encoded images.

#### Using Python

##### Text-to-Image Model

```python
import requests 
import os

url = "https://api.nebulablock.com/api/v1/images/generation" 

headers = {  
    "Content-Type": "application/json",  
    "Authorization": f"Bearer {os.environ.get('NEBULA_API_KEY')}" 
} 

data = {
    "model":"stabilityai/stable-diffusion-xl-base-1.0",
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

##### Image-to-Image Model

```python
import requests 
import os

url = "https://api.nebulablock.com/api/v1/images/generation" 

headers = {  
    "Content-Type": "application/json",  
    "Authorization": f"Bearer {os.environ.get('NEBULA_API_KEY')}" 
} 

data = {
    "model":"black-forest-labs/FLUX.1-Fill-dev",
    "prompt":"a flying cat",
    "num_steps":25,
    "guidance_scale":9,
    "negative_prompt": None,
    "width":1024,
    "height":1024, 
    "image":"/9j/4…/Z", 
    "mask":"/9j/4…ACgD/9k="
}

response = requests.post(url, headers=headers, json=data) 
print(response.json())
```

#### Using JavaScript

##### Text-to-Image Model

```javascript
const url = 'https://api.nebulablock.com/api/v1/images/generation';

const headers = {
    "Content-Type": "application/json",
    "Authorization": `Bearer ${process.env.NEBULA_API_KEY}`
};

const data = {
    "model": "stabilityai/stable-diffusion-xl-base-1.0",
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

##### Image-to-Image Model

```javascript
const url = 'https://api.nebulablock.com/api/v1/images/generation';

const headers = {
    "Content-Type": "application/json",
    "Authorization": `Bearer ${process.env.NEBULA_API_KEY}`
};

const data =  {
    "model": "black-forest-labs/FLUX.1-Fill-dev",
    "prompt": "a flying cat",
    "num_steps": 25,
    "guidance_scale": 9,
    "negative_prompt": null,
    "width": 1024,
    "height": 1024, 
    "image": "/9j/4…/Z", 
    "mask": "/9j/4…ACgD/9k="
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
- StableDiffusion XL 1.0: `stabilityai/stable-diffusion-xl-base-1.0` 
- Flux.1 schnell: `black-forest-labs/FLUX.1-schnell`
- Flux.1 Fill Dev: `black-forest-labs/FLUX.1-Fill-dev`

#### Response Example

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

Feel free to explore refer to the [API Reference](../API_Reference/Inference_Models/Generate_Images.md) for more details.