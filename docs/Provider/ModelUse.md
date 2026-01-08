# Model Use Guide
## OpenAI 示例

### Response API
OpenAI's most advanced interface for generating model responses. Supports text and image inputs, and text outputs. Create stateful interactions with the model, using the output of previous responses as input. Extend the model's capabilities with built-in tools for file search, web search, computer use, and more. Allow the model access to external systems and data using function calling.

**官方链接**: https://platform.openai.com/docs/api-reference/responses

=== "CURL"
    
    ```shell

    curl https://api.openai.com/v1/responses \
      -H "Content-Type: application/json" \
      -H "Authorization: Bearer $OPENAI_API_KEY" \
      -d '{
        "model": "gpt-4.1",
        "input": "Tell me a three sentence bedtime story about a unicorn."
      }'

    ```

=== "Python"

    ```python

    from openai import OpenAI

    client = OpenAI()
    
    response = client.responses.create(
      model="gpt-4.1",
      input="Tell me a three sentence bedtime story about a unicorn."
    )
    
    print(response)

    ```

=== "Stream(CURL)"

    ```shell
    
    curl https://api.openai.com/v1/responses \
      -H "Content-Type: application/json" \
      -H "Authorization: Bearer $OPENAI_API_KEY" \
      -d '{
        "model": "gpt-4.1",
        "instructions": "You are a helpful assistant.",
        "input": "Hello!",
        "stream": true
      }'
    
    ```

=== "Stream(Python)"

    ```python
    
    from openai import OpenAI
    
    client = OpenAI()
    
    response = client.responses.create(
      model="gpt-4.1",
      instructions="You are a helpful assistant.",
      input="Hello!",
      stream=True
    )
    
    for event in response:
      print(event)
    
    ```

**响应结果结构如下：**

=== "Non Stream"

    ```json

    {
      "id": "resp_67ccd2bed1ec8190b14f964abc0542670bb6a6b452d3795b",
      "object": "response",
      "created_at": 1741476542,
      "status": "completed",
      "completed_at": 1741476543,
      "error": null,
      "incomplete_details": null,
      "instructions": null,
      "max_output_tokens": null,
      "model": "gpt-4.1-2025-04-14",
      "output": [
        {
          "type": "message",
          "id": "msg_67ccd2bf17f0819081ff3bb2cf6508e60bb6a6b452d3795b",
          "status": "completed",
          "role": "assistant",
          "content": [
            {
              "type": "output_text",
              "text": "In a peaceful grove beneath a silver moon, a unicorn named Lumina discovered a hidden pool that reflected the stars. As she dipped her horn into the water, the pool began to shimmer, revealing a pathway to a magical realm of endless night skies. Filled with wonder, Lumina whispered a wish for all who dream to find their own hidden magic, and as she glanced back, her hoofprints sparkled like stardust.",
              "annotations": []
            }
          ]
        }
      ],
      "parallel_tool_calls": true,
      "previous_response_id": null,
      "reasoning": {
        "effort": null,
        "summary": null
      },
      "store": true,
      "temperature": 1.0,
      "text": {
        "format": {
          "type": "text"
        }
      },
      "tool_choice": "auto",
      "tools": [],
      "top_p": 1.0,
      "truncation": "disabled",
      "usage": {
        "input_tokens": 36,
        "input_tokens_details": {
          "cached_tokens": 0
        },
        "output_tokens": 87,
        "output_tokens_details": {
          "reasoning_tokens": 0
        },
        "total_tokens": 123
      },
      "user": null,
      "metadata": {}
    }
    
    ```

=== "Stream"

    ```json
    
    event: response.created
    data: {"type":"response.created","response":{"id":"resp_67c9fdcecf488190bdd9a0409de3a1ec07b8b0ad4e5eb654","object":"response","created_at":1741290958,"status":"in_progress","error":null,"incomplete_details":null,"instructions":"You are a helpful assistant.","max_output_tokens":null,"model":"gpt-4.1-2025-04-14","output":[],"parallel_tool_calls":true,"previous_response_id":null,"reasoning":{"effort":null,"summary":null},"store":true,"temperature":1.0,"text":{"format":{"type":"text"}},"tool_choice":"auto","tools":[],"top_p":1.0,"truncation":"disabled","usage":null,"user":null,"metadata":{}}}
    
    event: response.in_progress
    data: {"type":"response.in_progress","response":{"id":"resp_67c9fdcecf488190bdd9a0409de3a1ec07b8b0ad4e5eb654","object":"response","created_at":1741290958,"status":"in_progress","error":null,"incomplete_details":null,"instructions":"You are a helpful assistant.","max_output_tokens":null,"model":"gpt-4.1-2025-04-14","output":[],"parallel_tool_calls":true,"previous_response_id":null,"reasoning":{"effort":null,"summary":null},"store":true,"temperature":1.0,"text":{"format":{"type":"text"}},"tool_choice":"auto","tools":[],"top_p":1.0,"truncation":"disabled","usage":null,"user":null,"metadata":{}}}
    
    event: response.output_item.added
    data: {"type":"response.output_item.added","output_index":0,"item":{"id":"msg_67c9fdcf37fc8190ba82116e33fb28c507b8b0ad4e5eb654","type":"message","status":"in_progress","role":"assistant","content":[]}}
    
    event: response.content_part.added
    data: {"type":"response.content_part.added","item_id":"msg_67c9fdcf37fc8190ba82116e33fb28c507b8b0ad4e5eb654","output_index":0,"content_index":0,"part":{"type":"output_text","text":"","annotations":[]}}
    
    event: response.output_text.delta
    data: {"type":"response.output_text.delta","item_id":"msg_67c9fdcf37fc8190ba82116e33fb28c507b8b0ad4e5eb654","output_index":0,"content_index":0,"delta":"Hi"}
    
    ...
    
    event: response.output_text.done
    data: {"type":"response.output_text.done","item_id":"msg_67c9fdcf37fc8190ba82116e33fb28c507b8b0ad4e5eb654","output_index":0,"content_index":0,"text":"Hi there! How can I assist you today?"}
    
    event: response.content_part.done
    data: {"type":"response.content_part.done","item_id":"msg_67c9fdcf37fc8190ba82116e33fb28c507b8b0ad4e5eb654","output_index":0,"content_index":0,"part":{"type":"output_text","text":"Hi there! How can I assist you today?","annotations":[]}}
    
    event: response.output_item.done
    data: {"type":"response.output_item.done","output_index":0,"item":{"id":"msg_67c9fdcf37fc8190ba82116e33fb28c507b8b0ad4e5eb654","type":"message","status":"completed","role":"assistant","content":[{"type":"output_text","text":"Hi there! How can I assist you today?","annotations":[]}]}}
    
    event: response.completed
    data: {"type":"response.completed","response":{"id":"resp_67c9fdcecf488190bdd9a0409de3a1ec07b8b0ad4e5eb654","object":"response","created_at":1741290958,"status":"completed","error":null,"incomplete_details":null,"instructions":"You are a helpful assistant.","max_output_tokens":null,"model":"gpt-4.1-2025-04-14","output":[{"id":"msg_67c9fdcf37fc8190ba82116e33fb28c507b8b0ad4e5eb654","type":"message","status":"completed","role":"assistant","content":[{"type":"output_text","text":"Hi there! How can I assist you today?","annotations":[]}]}],"parallel_tool_calls":true,"previous_response_id":null,"reasoning":{"effort":null,"summary":null},"store":true,"temperature":1.0,"text":{"format":{"type":"text"}},"tool_choice":"auto","tools":[],"top_p":1.0,"truncation":"disabled","usage":{"input_tokens":37,"output_tokens":11,"output_tokens_details":{"reasoning_tokens":0},"total_tokens":48},"user":null,"metadata":{}}}
    
    ```


### Chat Completion
The Chat Completions API endpoint will generate a model response from a list of messages comprising a conversation.

**官方链接**: https://platform.openai.com/docs/api-reference/chat/create

=== "CURL"

    ```shell
    curl https://api.openai.com/v1/chat/completions \
      -H "Content-Type: application/json" \
      -H "Authorization: Bearer $OPENAI_API_KEY" \
      -d '{
        "model": "gpt-5.2",
        "messages": [
          {
            "role": "developer",
            "content": "You are a helpful assistant."
          },
          {
            "role": "user",
            "content": "Hello!"
          }
        ]
      }'

    ```

=== "Python"

    ```python

    from openai import OpenAI
    client = OpenAI()
    
    completion = client.chat.completions.create(
      model="gpt-5.2",
      messages=[
        {"role": "developer", "content": "You are a helpful assistant."},
        {"role": "user", "content": "Hello!"}
      ]
    )
    
    print(completion.choices[0].message)

    ```

=== "Stream(CURL)"

    ```shell

    curl https://api.openai.com/v1/chat/completions \
      -H "Content-Type: application/json" \
      -H "Authorization: Bearer $OPENAI_API_KEY" \
      -d '{
        "model": "gpt-5.2",
        "messages": [
          {
            "role": "developer",
            "content": "You are a helpful assistant."
          },
          {
            "role": "user",
            "content": "Hello!"
          }
        ],
        "stream": true
      }'

    ```

=== "Stream(Python)"

    ```python

    from openai import OpenAI
    client = OpenAI()
    
    completion = client.chat.completions.create(
      model="gpt-5.2",
      messages=[
        {"role": "developer", "content": "You are a helpful assistant."},
        {"role": "user", "content": "Hello!"}
      ],
      stream=True
    )
    
    for chunk in completion:
      print(chunk.choices[0].delta)

    ```

**响应结果结构如下：**

=== "Non Stream"

    ```json

    {
      "id": "chatcmpl-B9MBs8CjcvOU2jLn4n570S5qMJKcT",
      "object": "chat.completion",
      "created": 1741569952,
      "model": "gpt-4.1-2025-04-14",
      "choices": [
        {
          "index": 0,
          "message": {
            "role": "assistant",
            "content": "Hello! How can I assist you today?",
            "refusal": null,
            "annotations": []
          },
          "logprobs": null,
          "finish_reason": "stop"
        }
      ],
      "usage": {
        "prompt_tokens": 19,
        "completion_tokens": 10,
        "total_tokens": 29,
        "prompt_tokens_details": {
          "cached_tokens": 0,
          "audio_tokens": 0
        },
        "completion_tokens_details": {
          "reasoning_tokens": 0,
          "audio_tokens": 0,
          "accepted_prediction_tokens": 0,
          "rejected_prediction_tokens": 0
        }
      },
      "service_tier": "default"
    }

    ```

=== "Stream"
    
    ```json
    {"id":"chatcmpl-123","object":"chat.completion.chunk","created":1694268190,"model":"gpt-4o-mini", "system_fingerprint": "fp_44709d6fcb", "choices":[{"index":0,"delta":{"role":"assistant","content":""},"logprobs":null,"finish_reason":null}]}

    {"id":"chatcmpl-123","object":"chat.completion.chunk","created":1694268190,"model":"gpt-4o-mini", "system_fingerprint": "fp_44709d6fcb", "choices":[{"index":0,"delta":{"content":"Hello"},"logprobs":null,"finish_reason":null}]}
    
    ....
    
    {"id":"chatcmpl-123","object":"chat.completion.chunk","created":1694268190,"model":"gpt-4o-mini", "system_fingerprint": "fp_44709d6fcb", "choices":[{"index":0,"delta":{},"logprobs":null,"finish_reason":"stop"}]}

    ```

## Anthropic 示例
### Messages API
Send a structured list of input messages with text and/or image content, and the model will generate the next message in the conversation.

The Messages API can be used for either single queries or stateless multi-turn conversations.

**官方链接**: https://platform.claude.com/docs/en/api/python/messages/create

=== "CURL"

    ```shell
    
    curl https://api.anthropic.com/v1/messages \
        -H 'Content-Type: application/json' \
        -H 'anthropic-version: 2023-06-01' \
        -H "X-Api-Key: $ANTHROPIC_API_KEY" \
        -d '{
              "max_tokens": 1024,
              "messages": [
                {
                  "content": "Hello, world",
                  "role": "user"
                }
              ],
              "model": "claude-sonnet-4-5-20250929"
            }'
    
    ```

=== "Python"

    ```Python
    
    import os
    from anthropic import Anthropic
    
    client = Anthropic(
        api_key=os.environ.get("ANTHROPIC_API_KEY"),  # This is the default and can be omitted
    )
    message = client.messages.create(
        max_tokens=1024,
        messages=[{
            "content": "Hello, world",
            "role": "user",
        }],
        model="claude-sonnet-4-5-20250929",
    )
    print(message)
    
    ```

**响应结果结构如下：**

```json
{
  "id": "msg_013Zva2CMHLNnXjNJJKqJ2EF",
  "content": [
    {
      "citations": [
        {
          "cited_text": "cited_text",
          "document_index": 0,
          "document_title": "document_title",
          "end_char_index": 0,
          "file_id": "file_id",
          "start_char_index": 0,
          "type": "char_location"
        }
      ],
      "text": "Hi! My name is Claude.",
      "type": "text"
    }
  ],
  "model": "claude-sonnet-4-5-20250929",
  "role": "assistant",
  "stop_reason": "end_turn",
  "stop_sequence": null,
  "type": "message",
  "usage": {
    "cache_creation": {
      "ephemeral_1h_input_tokens": 0,
      "ephemeral_5m_input_tokens": 0
    },
    "cache_creation_input_tokens": 2051,
    "cache_read_input_tokens": 2051,
    "input_tokens": 2095,
    "output_tokens": 503,
    "server_tool_use": {
      "web_search_requests": 0
    },
    "service_tier": "standard"
  }
}
```

## Vertex Gemini 示例
### GenerateContent API
Build production-ready generative AI agents and applications using Vertex AI using Google's advanced models and infrastructure.

**官方文档**: https://docs.cloud.google.com/vertex-ai/generative-ai/docs/start/quickstart?hl=zh-cn

**官方示例**: https://docs.cloud.google.com/vertex-ai/generative-ai/docs/cookbook?hl=zh-cn

**生成方法**: https://docs.cloud.google.com/vertex-ai/generative-ai/docs/reference/express-mode/rest/v1/publishers.models/generateContent

=== "CURL"

    ```shell
    
    cat << EOF > request.json
    {
        "contents": [
            {
                "role": "user",
                "parts": [
                    {
                        "text": "hello"
                    }
                ]
            }
        ]
        , "generationConfig": {
            "temperature": 1
            ,"maxOutputTokens": 32768
            ,"responseModalities": ["TEXT", "IMAGE"]
            ,"topP": 0.95
            ,"imageConfig": {
                "aspectRatio": "1:1"
                ,"imageSize": "1K"
                ,"imageOutputOptions": {
                    "mimeType": "image/png"
                }
                ,"personGeneration": "ALLOW_ALL"
            }
        },
        "safetySettings": [
            {
                "category": "HARM_CATEGORY_HATE_SPEECH",
                "threshold": "OFF"
            },
            {
                "category": "HARM_CATEGORY_DANGEROUS_CONTENT",
                "threshold": "OFF"
            },
            {
                "category": "HARM_CATEGORY_SEXUALLY_EXPLICIT",
                "threshold": "OFF"
            },
            {
                "category": "HARM_CATEGORY_HARASSMENT",
                "threshold": "OFF"
            }
        ]
    }
    EOF
    
    API_KEY="<YOUR_API_KEY>"
    API_ENDPOINT="aiplatform.googleapis.com"
    MODEL_ID="gemini-2.5-flash-image"
    GENERATE_CONTENT_API="streamGenerateContent"
    
    curl \
    -X POST \
    -H "Content-Type: application/json" \
    "https://${API_ENDPOINT}/v1/publishers/google/models/${MODEL_ID}:${GENERATE_CONTENT_API}?key=${API_KEY}" -d '@request.json'
    
    ```

=== "Python"

    ```python
    
    from google import genai
    from google.genai import types
    import base64
    import os
    
    def generate():
      client = genai.Client(
          vertexai=True,
          api_key=os.environ.get("GOOGLE_CLOUD_API_KEY"),
      )
    
    
      model = "gemini-2.5-flash-image"
      contents = [
        types.Content(
          role="user",
          parts=[
            types.Part.from_text(text="""hello""")
          ]
        ),
      ]
    
      generate_content_config = types.GenerateContentConfig(
        temperature = 1,
        top_p = 0.95,
        max_output_tokens = 32768,
        response_modalities = ["TEXT", "IMAGE"],
        safety_settings = [types.SafetySetting(
          category="HARM_CATEGORY_HATE_SPEECH",
          threshold="OFF"
        ),types.SafetySetting(
          category="HARM_CATEGORY_DANGEROUS_CONTENT",
          threshold="OFF"
        ),types.SafetySetting(
          category="HARM_CATEGORY_SEXUALLY_EXPLICIT",
          threshold="OFF"
        ),types.SafetySetting(
          category="HARM_CATEGORY_HARASSMENT",
          threshold="OFF"
        )],
        image_config=types.ImageConfig(
          aspect_ratio="1:1",
          image_size="1K",
          output_mime_type="image/png",
        ),
      )
    
      for chunk in client.models.generate_content_stream(
        model = model,
        contents = contents,
        config = generate_content_config,
        ):
        print(chunk.text, end="")
    
    generate()
    
    ```

**响应结果结构如下**:

**结构说明**: https://docs.cloud.google.com/vertex-ai/generative-ai/docs/reference/rest/v1/GenerateContentResponse

```json
{
  "candidates": [
    {
      object (Candidate)
    }
  ],
  "modelVersion": string,
  "createTime": string,
  "responseId": string,
  "promptFeedback": {
    object (PromptFeedback)
  },
  "usageMetadata": {
    object (UsageMetadata)
  }
}
```