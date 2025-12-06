# Create Chat Completion
Generate a completion for chat-based conversations

## Language Examples



=== "CURL"

    ```shell
    curl https://api.apigo.ai/v1/chat/completions \
      -H "Authorization: Bearer YOUR_API_KEY" \
      -H "Content-Type: application/json" \
      -H "vendor: API_VENDOR" \
      -d '{"model": "gpt-4o", "messages": [{"role": "user", "content": "Hello!"}]}'
    ```

=== "Python(requests)"

    ```python
    import requests
    import json
    
    API_URL = "https://api.apigo.ai/v1/chat/completions"
    API_KEY = "YOUR_API_KEY"
    VENDOR = "API_VENDOR"
    
    payload = {
        "model": "gpt-4o",
        "messages": [{"role": "user", "content": "Hello!"}]
    }
    
    headers = {
        "Authorization": f"Bearer {API_KEY}",
        "Content-Type": "application/json",
        "vendor": VENDOR
    }
    
    resp = requests.post(API_URL, headers=headers, json=payload, timeout=30)
    print("Status:", resp.status_code)
    # try to parse Json Response
    try:
        print(json.dumps(resp.json(), indent=2, ensure_ascii=False))
    except Exception:
        print(resp.text)
    ```

=== "Node.js"
    ```javascript
    // Node 18+ built-in fetch
    const API_URL = "https://api.apigo.ai/v1/chat/completions";
    const API_KEY = "YOUR_API_KEY";
    const VENDOR = "API_VENDOR";
    
    const body = {
      model: "gpt-4o",
      messages: [{ role: "user", content: "Hello!" }]
    };
    
    (async () => {
      const res = await fetch(API_URL, {
        method: "POST",
        headers: {
          "Authorization": `Bearer `,
          "Content-Type": "application/json",
          "vendor": VENDOR
        },
        body: JSON.stringify(body),
        // signal: abortController.signal // 可选：支持取消
      });
    
      console.log("Status:", res.status);
      const text = await res.text();
      try {
        console.log(JSON.stringify(JSON.parse(text), null, 2));
      } catch (e) {
        console.log(text);
      }
    })();
    ```
    
=== "golang"
    
    ```go
    package main
    
    import (
        "bytes"
        "encoding/json"
        "fmt"
        "io"
        "net/http"
        "time"
    )
    
    func main() {
        apiURL := "https://api.apigo.ai/v1/chat/completions"
        apiKey := "YOUR_API_KEY"
        vendor := "API_VENDOR"
    
        payload := map[string]interface{}{
            "model": "gpt-4o",
            "messages": []map[string]string{
                {"role": "user", "content": "Hello!"},
            },
        }
        b, _ := json.Marshal(payload)
        req, _ := http.NewRequest("POST", apiURL, bytes.NewReader(b))
        req.Header.Set("Authorization", "Bearer "+apiKey)
        req.Header.Set("Content-Type", "application/json")
        req.Header.Set("vendor", vendor)
    
        client := &http.Client{Timeout: 30 * time.Second}
        resp, err := client.Do(req)
        if err != nil {
            fmt.Println("Request error:", err)
            return
        }
        defer resp.Body.Close()
        fmt.Println("Status:", resp.StatusCode)
        body, _ := io.ReadAll(resp.Body)
        // 尝试解析 JSON
        var obj interface{}
        if err := json.Unmarshal(body, &obj); err == nil {
            out, _ := json.MarshalIndent(obj, "", "  ")
            fmt.Println(string(out))
        } else {
            fmt.Println(string(body))
        }
    }
    ```

=== "Java"

    ```java
    import java.net.URI;
    import java.net.http.*;
    import java.time.Duration;
    import com.fasterxml.jackson.databind.ObjectMapper;
    import java.util.Map;
    
    public class ApigoExample {
      public static void main(String[] args) throws Exception {
        String apiUrl = "https://api.apigo.ai/v1/chat/completions";
        String apiKey = "YOUR_API_KEY";
        String vendor = "API_VENDOR";
    
        Map payload = Map.of(
          "model", "gpt-4o",
          "messages", new Object[] { Map.of("role","user","content","Hello!") }
        );
    
        ObjectMapper mapper = new ObjectMapper();
        String body = mapper.writeValueAsString(payload);
    
        HttpRequest req = HttpRequest.newBuilder()
          .uri(URI.create(apiUrl))
          .timeout(Duration.ofSeconds(30))
          .header("Authorization", "Bearer " + apiKey)
          .header("Content-Type", "application/json")
          .header("vendor", vendor)
          .POST(HttpRequest.BodyPublishers.ofString(body))
          .build();
    
        HttpClient client = HttpClient.newHttpClient();
        HttpResponse resp = client.send(req, HttpResponse.BodyHandlers.ofString());
        System.out.println("Status: " + resp.statusCode());
        System.out.println(resp.body());
      }
    }
    ```

=== "C#"

    ```c
    using System;
    using System.Net.Http;
    using System.Text;
    using System.Text.Json;
    using System.Threading.Tasks;
    
    class Program {
      static async Task Main() {
        var apiUrl = "https://api.apigo.ai/v1/chat/completions";
        var apiKey = "YOUR_API_KEY";
        var vendor = "API_VENDOR";
    
        var payload = new {
          model = "gpt-4o",
          messages = new[] { new { role = "user", content = "Hello!" } }
        };
    
        var json = JsonSerializer.Serialize(payload);
        using var client = new HttpClient { Timeout = TimeSpan.FromSeconds(30) };
        var req = new HttpRequestMessage(HttpMethod.Post, apiUrl);
        req.Headers.Add("Authorization", $"Bearer {apiKey}");
        req.Headers.Add("vendor", vendor);
        req.Content = new StringContent(json, Encoding.UTF8, "application/json");
    
        var resp = await client.SendAsync(req);
        Console.WriteLine("Status: " + (int)resp.StatusCode);
        var body = await resp.Content.ReadAsStringAsync();
        Console.WriteLine(body);
      }
    }
    ```


## Header

| Name | Type | Required | Description                                                       |
| --- | --- | --- |-------------------------------------------------------------------|
| Authorization | string | required | Include your API key in the Authorization header of your requests |
| Content-Type | string | required | application/json                                                  |
| vendor | string |  | API_VENDOR                                                  |

## Query Parameters
| Name | Type | Required | Description                              |
| --- | --- | --- |------------------------------------------|
| model | string | required | The model ID to use for the completion.  |
| messages | array | required | Array of chat messages describing the conversation so far.  |
| model | string | required | The model ID to use for the completion.  |
| model | string | required | The model ID to use for the completion.  |

##  Responses Parameters
| Name                                            | Type | Description                                                                                                                                                                                                                                                                  | Example                            |
|-------------------------------------------------| --- |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------|
| id                                              | string | unique identifier for the request                                                                                                                                                                                                                                            | "8096df8781e547f38cc2c24ed0de4a28" |
| object                                          | string | Object type, typically chat.completion                                                                                                                                                                                                                                       | "chat.completion"                  |
| created                                         | integer | Timestamp when the request was created (Unix timestamp)                                                                                                                                                                                                                      | 1741570283                         |
| model                                           | string | Name of the model used                                                                                                                                                                                                                                                       | "gemini-2.5-flash"                 |
| choices                                         | object[] | List of generated text options                                                                                                                                                                                                                                               |                                    |
| &nbsp;&nbsp;index                               | integer | Index of the option, starting from 0                                                                                                                                                                                                                                         | 0                                  |
| &nbsp;&nbsp;message                             | object |                                                                                                                                                                                                                                                                              |                                    |
| &nbsp;&nbsp;&nbsp;&nbsp;message.role            | enum | Message role; "assistant" indicates an assistant message，Available options: assistant                                                                                                                                                                                        | "assistant"                        |
| &nbsp;&nbsp;&nbsp;&nbsp;message.content         | string | Generated text content                                                                                                                                                                                                                                                       | "assistant"                        |
| &nbsp;&nbsp;&nbsp;&nbsp;message.reasoning_content | string | Content of the model's reasoning process when generating text                                                                                                                                                                                                                | ""                                 |
| &nbsp;&nbsp;finish_reason                             | enum | "stop" indicates that the model stops generating further content when it encounters the string specified in the "stop" field; "length" indicates that the model stops generating when it reaches the maximum length; "null" indicates that no termination reason is specified. | Available options: stop, length    |
| usage | object | Token usage for the current request                                                                                                                                                                                                                                          |                                    |
| &nbsp;&nbsp;usage.prompt_tokens                             | integer | Token count of the input message | 1117                               |
| &nbsp;&nbsp;usage.completion_tokens                             | integer | Token count of the generated text | 46                                 |
| &nbsp;&nbsp;usage.total_tokens                             | integer | Total token count for the current request (input + output) | 1163                               |
| &nbsp;&nbsp;usage.prompt_tokens_details                             | object | Detailed token information of the input message |                                    |
| &nbsp;&nbsp;&nbsp;&nbsp;usage.prompt_tokens_details.audio_tokens                             | integer | Token count of the input audio | 0                                  |
| &nbsp;&nbsp;&nbsp;&nbsp;usage.prompt_tokens_details.cached_tokens                             | integer | Token count of cache hits | 0                                  |
| &nbsp;&nbsp;usage.completion_tokens_details                             | object | Detailed token information of the generated text |                                    |
| &nbsp;&nbsp;&nbsp;&nbsp;usage.completion_tokens_details.audio_tokens                             | integer | Token count of the output audio | 0                                  |
| &nbsp;&nbsp;&nbsp;&nbsp;usage.completion_tokens_details.reasoning_tokens                             | integer | Token count of the output reasoning process | 0                                  |

## Responses Result
| Code | Description |
| --- | --- |
| 200 | chat completion response<br> **Example Response:**<pre><code>{<br>&nbsp;&nbsp;"id": "8096df8781e547f38cc2c24ed0de4a28",<br>&nbsp;&nbsp;"object": "chat.completion",<br>&nbsp;&nbsp;"created": 1741570283,<br>&nbsp;&nbsp;"model": "gemini-2.5-flash",<br>&nbsp;&nbsp;"choices": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"index": 0,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"message": {<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"role": "assistant",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"content": "hello！",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"reasoning_content": ""<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"finish_reason": "stop"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;],<br>&nbsp;&nbsp;"usage": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"prompt_tokens": 1117,<br>&nbsp;&nbsp;&nbsp;&nbsp;"completion_tokens": 46,<br>&nbsp;&nbsp;&nbsp;&nbsp;"total_tokens": 1163,<br>&nbsp;&nbsp;&nbsp;&nbsp;"prompt_tokens_details": {<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"audio_tokens": 0,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"cached_tokens": 0<br>&nbsp;&nbsp;&nbsp;&nbsp;},<br>&nbsp;&nbsp;&nbsp;&nbsp;"completion_tokens_details": {<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"audio_tokens": 0,<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"reasoning_tokens": 0<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;}<br>}</code></pre> |
| 400 | Bad Request - Invalid query parameters. |
| 500 | 500	Internal Server Error. |
