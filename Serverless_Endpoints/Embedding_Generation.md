
# Embedding Generation

Embedding models are machine learning models that convert data (such as text, images, or code) into dense numerical 
vectors in a continuous space. These vectors, called embeddings, capture the semantic relationships between different 
pieces of data, enabling efficient comparison and retrieval.

## Models available

- UAE-Large-V1: `WhereIsAI/UAE-Large-V1`
- BGE Large EN v1.5: `BAAI/bge-large-en-v1.5`

## Using the Models

##### Through API Endpoint

This option is to use our API endpoint directly in your projects. Below are some code snippets to get you started!

## Using cURL
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

## Using Python

```python
import requests 
import os

url = "https://inference.nebulablock.com/v1/embeddings" 

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

## Using JavaScript

```javascript

```

> **NOTE:**  Don't forget to use **your** API key. See [here](../API_Reference/Authentication.md) and [here](../API_Key/Overview.md) for more details on authentication. 

To specify the desired model, use this mapping for the `model`: 

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

>> **NOTE:** Notice that there are 2 embeddings, each with its own index number. These embeddings correspond to the given input sentences, 
> of which there are 2. You can choose how many sentences to create embeddings for, this is just an example. 

Feel free to explore refer to the [API Reference](../API_Reference/Serverless_Endpoints/Generate_Embeddings.md) for more details.