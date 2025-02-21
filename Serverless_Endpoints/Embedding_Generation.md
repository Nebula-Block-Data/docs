
# Embedding Generation

Embedding models are machine learning models that convert data (such as text, images, or code) into dense numerical 
vectors in a continuous space. These vectors, called embeddings, capture the semantic relationships between different 
pieces of data, enabling efficient comparison and retrieval.

## Models available

- UAE-Large-V1: `WhereIsAI/UAE-Large-V1`
- BGE Large EN v1.5: `BAAI/bge-large-en-v1.5`

### Using the Models

##### Through API Endpoint

This option is great if you want to use our API endpoint directly in your projects. To specify the desired model, use 
this mapping for the `model`: 

- UAE-Large-V1: `WhereIsAI/UAE-Large-V1`
- BGE Large EN v1.5: `BAAI/bge-large-en-v1.5`

A successful response body will return the embeddings in this format: 

```json
{
    "model": "WhereIsAI/UAE-Large-V1",
    "data": [
        
      {
            "embedding": [
                -0.373046875,
                -0.5546875,
                -0.033203125,
                ..., 
                0.248046875
            ],
            "index": 0,
            "object": "embedding"
        },
        {
            "embedding": [
                -0.50390625,
                -0.462890625,
                0.294921875,
                ...,
                0.01409912109375
            ],
            "index": 1,
            "object": "embedding"
        }
    ],
    "object": "list",
    "usage": {
        "completion_tokens": 0,
        "prompt_tokens": 33,
        "total_tokens": 33,
        "completion_tokens_details": null,
        "prompt_tokens_details": null
    }
}
```

Below are some examples to get you started!

## Using cURL
```bash
curl -X POST "https://dev-llm-proxy.nebulablock.com/v1/embeddings" \
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

## Using Python

```python
import requests 
import os

url = "https://dev-llm-proxy.nebulablock.com/v1/embeddings" 

headers = {  
    "Content-Type": "application/json",  
    "Authorization": f"Bearer {os.environ.get('NEBULA_API_KEY')}" 
} 

data = {
    "model":"WhereIsAI/UAE-Large-V1",
    "input":[ 
        "Bananas are berries, but strawberries are not, according to botanical classifications.", 
        "The Eiffel Tower in Paris was originally intended to be a temporary structure." 
    ] 
}

response = requests.post(url, headers=headers, json=data) 
print(response.json())
```

See our [API Reference]() for more details on API use.