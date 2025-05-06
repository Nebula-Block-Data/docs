# Overview

When users sign up for Nebula Block, they are automatically issued a unique API key. This key allows users to 
authenticate and interact with the platform's API endpoints, including those related to Serverless AI. 
Each user is permitted to have only one API key at a time.

## Key Features

- **One API Key Per User**: Each user can only have one API key, which is assigned upon registration.
- **API Key Renewal**: Users can renew their API key whenever necessary.
- **Authentication**: The API key is used to authenticate API requests. It is required for accessing all endpoints, including serverless models.

## Using and Managing Your API Key
1. **Obtaining the API Key**: Upon sign-up, an API key will be provided to you.
2. **Renewing the API Key**:
   - If you need to renew your API key, you can do so via your user account dashboard.
   - Once renewed, your old key will become invalid, and the valid key for API authentication will be the new one. 
3. **Using the API Key:**
   - Include your API key in the request header for authentication:

```Authorization: Bearer YOUR_API_KEY```

  - This is required for all API requests, including interacting with serverless endpoints and managing resources.
4. **Security Considerations**:
   - Keep your API key secure. Do not expose it publicly (eg. in client-side code or version control).
   - If you suspect your API key has been compromised, renew it immediately to avoid unexpected charges. 

## See Also
- [Glossary](../glossary.md)
- [API Reference - API Keys](../API_Reference/API_Keys/Create_API_Key.md)
