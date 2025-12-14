# FAQ
### What is API·GO?
API·GO is a unified AI API gateway that allows you to access multiple leading AI models (like ChatGPT, Claude, Gemini, etc.) through a single endpoint, simplifying your development workflow with intelligent load balancing and reliable API call experience.

### Which AI models does Api·Go support?
We support models from major AI providers including OpenAI (GPT-3.5, GPT-4 series), Anthropic (Claude series), Google (Gemini series), Azure OpenAI, AWS Bedrock, DeepSeek, Mistral, and more. We continuously add support for new models.

### How do I get started with Api·Go?
Simply sign up for an account, get your API key, and replace your existing AI API endpoints with Api·Go's unified endpoint. We provide comprehensive documentation and SDKs supporting multiple programming languages.

### What are the advantages of using Api·Go?
Key advantages include: unified API interface reducing integration complexity, intelligent load balancing for higher availability, automatic failover ensuring service stability, cost optimization with usage analytics, and global CDN acceleration.

### How does Api·Go pricing work?
We use a pay-as-you-go model with transparent pricing structure. Our basic plan includes free credits suitable for development and testing. Enterprise users enjoy volume discounts and dedicated support services.

### How is data security and privacy protected?
We implement enterprise-grade security standards including end-to-end encryption, no data retention policy, SOC2 compliance certification, and more. All API calls are encrypted in transit with full protection of user data privacy.

# Errors
The API uses standard HTTP status codes to indicate the success or failure of a request.

## Client Errors (4xx)
| Code | Description |
|------| --- |
| 400  | Bad Request - The request was unacceptable, often due to missing a required parameter. |
| 401  | Unauthorized - No valid API key provided. |
| 403  | Forbidden - The API key doesn't have permissions to perform the request. |
| 404  | Not Found - The requested resource doesn't exist. |
| 409  | Conflict - The request conflicts with another request (perhaps due to using the same idempotent key). |
| 429  | Too Many Requests - Too many requests hit the API too quickly. We recommend an exponential backoff. |


## Server Errors (5xx)
| Code | Description |
|------| --- |
| 500  | Internal Server Error - We had a problem with our server. Try again later. |
| 503  | Service Unavailable - The server is temporarily unavailable (e.g., for maintenance). Try again later. |
