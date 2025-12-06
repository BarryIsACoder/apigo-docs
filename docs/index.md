# Introduction

is a commercialized model service aggregation platform dedicated to providing domestic AIGC application innovation teams with commercial model API services featuring lower costs, greater diversity, and higher stability. It aims to reduce the model integration costs for AIGC application innovation teams and make AIGC application development more efficient.

All API requests should be made over HTTPS to the endpoint: https://api.apigo.ai

Responses are returned in JSON format.


# Quick Start
Get started with the API·GO API in minutes

The Api·Go API provides OpenAI-compatible endpoints that give you access to advanced language models. Get started with just a few lines of code using your preferred SDK or framework.

Looking for your API key? Get it from the API·GO Dashboard.
## 1. Authentication
Most endpoints require authentication via an API key. Include your API key in the request header:
```
Authorization: Bearer YOUR_API_KEY
```

## 2. Make a Request
Here's how to get a list of users:
```shell
curl -H "Authorization: Bearer YOUR_API_KEY" https://api.example.com/api/v1/users
```

## 3. Handle the Response
The API will respond with a JSON object containing the requested data or an error message.


# Guides
Detailed guides on how to use specific features of the API.

## Chat Management
Learn how to create chat

* Create Chat Completion
* Create Message

## Rate Limiting
API·GO operates on a prepaid balance model and does not impose any hard limits on request rate or concurrency. As long as your account has a sufficient balance, you can continue to send requests.

This flexible approach allows you to scale your usage according to your needs without being constrained by platform-level restrictions.

* While API·GO does not limit your request rate, the underlying AI providers (e.g., OpenAI, Anthropic, Google) may enforce their own rate or concurrency limits on a per-API-key basis.
* If you are sending a high volume of concurrent requests, you must still adhere to the usage policies of the upstream provider you are routing to. We recommend implementing robust retry and error-handling logic in your application to manage potential rate limit errors from providers.
