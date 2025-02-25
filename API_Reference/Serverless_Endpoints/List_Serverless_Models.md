---
# title: List Available Serverless Models
description: List Available Serverless Models.
---

# List Serverless Models

Return a list of all available serverless models and their details. 

## HTTP Request

`GET` `{API_URL}/serverless/models`

## Response Attributes

#### data `dict`

A dict containing a key-value pair of `models: [list of models]`. Each model in this list is represented as a `dict`, 
containing the following model information: 

- **model_name** `string`: The unique name for the model. Use this value when specifying the desired models in API calls.
- **model_alias** `string`: An name for the model that is easy to interpret. 
- **model_type** `string`: The type of data output by the model. 
- **context_length** `string`: The length of the context required by the model.
- **max_completion_tokens** `string`: The maximum number of tokens that will be generated for each response, if applicable.
- **description**: A brief description of the model.
- **price**: The price of the model.
- **huggingface_url**: The URL of the model on hugging face, if applicable.
- 
#### status `string`

Indicates the result of the request. `success` signifies success, while `failed` indicates an error.

#### message `string`

A description of the status of the request.

## Example

#### Request

```bash
curl -X GET '{API_URL}/api/v1/serverless/models' \
-H 'Authorization: Bearer {TOKEN/KEY}' \
-H 'Content-Type: application/json'
```

#### Response

Here's an example of a successful response. 

```json
{
    "data": {
        "models": [
            {
                "model_name": "deepseek-ai/DeepSeek-R1-Distill-Llama-70B",
                "model_alias": "DeepSeek-R1-Distill-Llama-70B",
                "model_type": "Text",
                "context_length": 32768,
                "max_completion_tokens": 10000,
                "description": "A highly advanced, distilled version of the LLaMA 70B model developed by DeepSeek, optimized for efficiency and performance",
                "price": 0,
                "huggingface_url": "https://huggingface.co/deepseek-ai/DeepSeek-R1-Distill-Llama-70B"
            },
            {
                "model_name": "stabilityai/stable-diffusion-xl-base-1.0",
                "model_alias": "SD-XL 1.0-base",
                "model_type": "Image",
                "context_length": null,
                "max_completion_tokens": 10000,
                "description": "A high-resolution latent diffusion model designed for generating detailed and high-quality images",
                "price": 0.009,
                "huggingface_url": "https://huggingface.co/stabilityai/stable-diffusion-xl-base-1.0"
            },
            {
                "model_name": "WhereIsAI/UAE-Large-V1",
                "model_alias": "UAE-Large-V1",
                "model_type": "Embedding",
                "context_length": 512,
                "max_completion_tokens": 10000,
                "description": "A universal English sentence embedding model by WhereIsAI with 1024-dim embeddings and 512 context length support",
                "price": 0.012,
                "huggingface_url": "https://huggingface.co/WhereIsAI/UAE-Large-V1"
            }
        ]
    },
    "message": "Get models list successfully.",
    "status": "success"
}
```
