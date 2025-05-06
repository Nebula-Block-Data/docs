# Overview
This guide will help you get set up with the Nebula Block APIs. 

## Getting Your API Key
To authenticate with the Nebula Block APIs, you need an API key. You can create and manage API keys via the Platform API:
- **Create an API Key:** Use the [Create API Key](API_Keys/Create_API_Key.md) endpoint to generate a new key. The key will be shown only once in the response—store it securely.
- **List/Delete API Keys:** See [List API Keys](API_Keys/List_API_Keys.md) and [Delete API Key](API_Keys/Delete_API_Key.md) for management.

## Adding an SSH Key
To access GPU instances securely, you need to add your SSH public key:
- **Create an SSH Key:** Use the [Create SSH Key](SSH_Keys/Create_SSH_Key.md) endpoint to register your SSH public key with your account.
- **List/Delete SSH Keys:** See [List SSH Keys](SSH_Keys/List_SSH_Keys.md) and [Delete SSH Key](SSH_Keys/Delete_SSH_Key.md) for management.

## API Types

Nebula Block provides two main APIs:

### Platform API
- For managing GPU instances, object storage, billing, and account resources.
- **BASE URL:** `https://api.nebulablock.com`
- **BASE PATH:** `/api/v1`
- **API_URL:** `https://api.nebulablock.com/api/v1`

### Inference API (OpenAI Compatible)
- For running inference (text, vision, image, embeddings) using serverless endpoints.
- **BASE URL:** `https://inference.nebulablock.com/v1`
- **OpenAI compatible**: Use OpenAI SDKs and tools.

> [!NOTE]
> This section provides detailed reference for all API endpoints, including authentication, usage, and request/response formats.

## See Also
- [Glossary](../glossary.md)
- [Overview](../Overview.md)
