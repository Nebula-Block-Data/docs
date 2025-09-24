# Overview
This guide will help you get set up with the Nebula Block APIs. 

## Getting Your API Key
API keys are automatically generated for each user upon account creation. You can view, renew, or revoke your API key in the Nebula Block user dashboard:
- **View/Renew API Key:** Log in to your [user dashboard](https://console.nebulablock.com/home) to view or renew your API key. If you renew your key, the old one will be invalidated.
- **Security Note:** Keep your API key secure. If you suspect it has been compromised, renew it immediately.

## Adding an SSH Key
To access GPU instances securely, you need to add your SSH public key:
- **Add SSH Key:** Log in to your [user dashboard](https://console.nebulablock.com/home) and navigate to the SSH Keys section to add or manage your SSH public keys.
- **API Management:** You can also use the [Create SSH Key](SSH_Keys/Create_SSH_Key.md) endpoint to register your SSH public key with your account, or [List SSH Keys](SSH_Keys/List_SSH_Keys.md) and [Delete SSH Key](SSH_Keys/Delete_SSH_Key.md) for management.

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

> **Note:** This section provides detailed reference for all API endpoints, including authentication, usage, and request/response formats.

## See Also
- [Glossary](../glossary.md)
- [Overview](../Overview.md)
