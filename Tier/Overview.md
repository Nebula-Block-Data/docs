# Overview

This page outlines the different tiers available in the system, their requirements, and the corresponding benefits. All
users have access to our serverless endpoints. The tiers dictate your request and token rates, as well as
whether you have access to GPU instances.

### **Tier Levels and Benefits**
| Tier Level          | Requirement     | GPU Access | CPU Access | Request Rate | Token Rate  |
|---------------------|-----------------|------------|------------|--------------|-------------|
| **Engineer Tier 1** | Sign Up         | No         | No         | 60 RPM       | 60,000 TPM  |
| **Engineer Tier 2** | Add Credit Card | No         | Yes        | 300 RPM      | 150,000 TPM |
| **Engineer Tier 3** | Deposit $10     | Yes        | Yes        | 600 RPM      | 200,000 TPM |
| **Expert Tier 1**   | Spend $30       | Yes        | Yes        | 1,500 RPM    | 500,000 TPM |
| **Expert Tier 2**   | Spend $50       | Yes        | Yes        | 3,000 RPM    | 800,000 TPM |

### **Tier Descriptions**

1. **Engineer Tier 1**
   - Available to all users upon sign-up.
   - Provides a request rate limit of **60 requests per minute (RPM)** for using serverless endpoints.
   - Token Rate: **60,000 tokens per minute (TPM)** for using serverless endpoints.
   - No CPU and GPU access.

2. **Engineer Tier 2**
   - Requires adding a credit card.
   - Increases request rate to **300 RPM**.
   - Token Rate: **150,000 TPM**.
   - No GPU access.

3. **Engineer Tier 3**
   - Requires a **$10 deposit**.
   - Grants GPU access.
   - Increases request rate to **600 RPM**.
   - Token Rate: **200,000 TPM**.

4. **Expert Tier 1**
   - Requires a **$30 spend**.
   - Grants GPU access.
   - Increases request rate to **1,500 RPM**.
   - Token Rate: **500,000 TPM**.

5. **Expert Tier 2**
   - Requires a **$50 spend**.
   - Grants GPU access.
   - Highest request rate of **3,000 RPM**.
   - Token Rate: **800,000 TPM**.

### **Upgrade Process**
- Users can upgrade their tier by meeting the respective requirements.
- The "Upgrade" or "Deposit" button in the interface allows users to progress to higher tiers.
- Higher tiers provide increased computational power and request capabilities.

For further assistance, see the [Contact Us](../Contact_Us/README.md) section.

# Pricing

Nebula Block offers transparent, competitive pricing across all our services. Pay only for what you use with no hidden fees.

## GPU Instances

### On-Demand Pricing Starting From
| GPU Type | Price per Hour|
|----------|---------------|
| H200 | $1.95 |
| H100 | $1.25 |
| A100 | $0.89 |
| L40S | $0.75 |
| 5090 | $0.65 |

Custom configurations available for enterprise customers.

## Serverless AI Endpoints

### Language Models (per 1M tokens)
| Model | Price |
|-------|-------|
| Llama 3.3 70B | $0.35 |
| Qwen QwQ 32B | $1.08 |
| Qwen 2.5 Coder 32B | $0.15 |
| DeepSeek Models | Free tier available |

DeepSeek Models include:
- DeepSeek-V3-0324
- DeepSeek-R1-Distill-Llama-70B
- DeepSeek-R1-Distill-Qwen-32B

### Image Generation
| Model | Price |
|-------|-------|
| Stable Diffusion XL 1.0 | $0.009 per image |
| FLUX.1 [schnell] | $0.0019 per image |
| FLUX.1 Fill | Free tier available |

### Vision Models
| Model | Price |
|-------|-------|
| Qwen 2.5 VL 7B | $0.10 per 1M tokens |

### Embedding Models
| Model | Price |
|-------|-------|
| UAE-Large-V1 | $0.012 per 1M tokens |
| BGE-large-en-v1.5 | $0.006 per 1M tokens |
| M2-BERT-Retrieval-32k | Free tier available |

## Object Storage
| Service | Price |
|---------|-------|
| Standard Storage | $0.02 per GB/month |
| Data Transfer OUT | $0.08 per GB |
| Data Transfer IN | Free |

## Enterprise Features

Enterprise customers receive:
- Custom pricing for high-volume usage
- Dedicated support team
- SLA guarantees (up to 99.99% uptime)
- Private deployments
- Custom security configurations
- Flexible billing options

For enterprise pricing and custom solutions, [contact our sales team](../Contact_Us/README.md).
