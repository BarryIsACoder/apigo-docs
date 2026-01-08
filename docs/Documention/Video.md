# Video
## Create Video
Call OpenAI's video generation API (supporting models like Sora) to generate videos.

### Language Examples

=== "CURL"

    ```shell
     curl https://api.apigo.ai/v1/videos \
      -H "Authorization: Bearer YOUR_API_KEY" \
      -F "model=sora-2" \
      -F "prompt=A calico cat playing a piano on stage"
    ```


### Header

| Name | Type | Required | Description                                                       |
| --- | --- | --- |-------------------------------------------------------------------|
| Authorization | string | required | Include your API key in the Authorization header of your requests |
| Content-Type | string | required | application/json                                                  |

### Query Parameters
| Name | Type   | Required | Description                              |
| --- |--------| --- |------------------------------------------|
| prompt | string | required | The text prompt describing the video to be generated.  |
| model | string | required | Video generation model, defaulting to sora-2.  |
| seconds | string |  | Video duration (in seconds), defaulting to 10 seconds.  |
| size | string |  | Output resolution, formatted as width×height, defaulting to 720×1280.  |
| input_reference | file   |  | Optional image reference, used to guide generation.  |

### Responses Parameters
| Name                                            | Type    | Description                                                                                                                                                                                                                                                                    | Example                         |
|-------------------------------------------------|---------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------|
| id                                              | string  | Video task ID                                                                                                                                                                                                                                                                  | video_123                       |
| object                                          | string  | Object type, fixed as "video"                                                                                                                                                                                                                                                  | video |
| model                                           | string  | Name of the model used                                                                                                                                                                                                                                                         | sora-2              |
| status                                         | string  | Task status (queued: in queue, processing: in processing, completed: completed, failed: failed)                                                                                                                                                                                | queued |
| progress | integer | Processing progress (0-100)                                                                                                                                                                                                                                                    | 0                               |
| created_at                             | integer | Creation timestamp                                                                                                                                                                                                                                                             | 1712697600                                |
| size | string  | Video resolution | 1024x1808 |
| seconds | string  | Video duration (in seconds) | 10 |
| quality | string  | Video quality | standard |


### Responses Result
| Code | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| --- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 200 | video completion response<br> **Example Response:**<pre><code>{<br>&nbsp;&nbsp;"id": "video_123",<br>&nbsp;&nbsp;"object": "video",<br>&nbsp;&nbsp;"model": "sora-2",<br>&nbsp;&nbsp;"status": "queued",<br>&nbsp;&nbsp;"progress": 0,<br>&nbsp;&nbsp;"created_at": 1712697600,<br>&nbsp;&nbsp;"size": "1024x1808",<br>&nbsp;&nbsp;"seconds": "8",<br>&nbsp;&nbsp;"quality": "standard"<br>}</code></pre> |
| 400 | Bad Request - Invalid query parameters.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| 500 | 500	Internal Server Error.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |


## Search Videos
Query the status and result of a video generation task using the task ID.

### Language Examples

=== "CURL"

    ```shell
    curl 'https://api.apigo.ai/v1/videos/video_123' \
      -H "Authorization: Bearer YOUR_API_KEY"
    ```

### Path Parameter

| Name | Type   | Required | Description                              |
| --- |--------| --- |------------------------------------------|
| video_id | string | required | Video task ID |

### Responses Parameters

| Name | Type | Description | Example |
| --- | --- | --- | --- |
| id | string | Video task ID | video_123 |
| object | string | Object type, fixed as "video" | video |
| model | string | Name of the model used | sora-2 |
| status | string | Task status (queued: in queue, processing: in processing, completed: completed, failed: failed) | queued |
| progress | integer | Processing progress (0-100) | 0 |
| created_at | integer | Creation timestamp | 1712697600 |
| size | string | Video resolution | 1024x1808 |
| seconds | string | Video duration (in seconds) | 10 |
| quality | string | Video quality | standard |
| url | string | Video url | https://example.com/video.mp4 |

### Responses Result
| Code | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| --- |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 200 | video completion response<br> **Example Response:**<pre><code>{<br>&nbsp;&nbsp;"id": "video_123",<br>&nbsp;&nbsp;"object": "video",<br>&nbsp;&nbsp;"model": "sora-2",<br>&nbsp;&nbsp;"status": "completed",<br>&nbsp;&nbsp;"progress": 100,<br>&nbsp;&nbsp;"created_at": 1712697600,<br>&nbsp;&nbsp;"size": "1024x1808",<br>&nbsp;&nbsp;"seconds": "8",<br>&nbsp;&nbsp;"quality": "standard",<br>&nbsp;&nbsp;"url": "https://example.com/video.mp4" <br>}</code></pre> |
| 400 | Bad Request - Invalid query parameters.                                                                                                                                                                                                                                                                                                                                                                                                                                |
| 500 | 500	Internal Server Error.                                                                                                                                                                                                                                                                                                                                                                                                                                             |

## Doubao Seedance 视频生成
Seedance 模型具备出色的语义理解能力，可根据用户输入的文本、图片等内容，快速生成优质的视频片段。该教程主要讲解如何调用 Video Generation API 生成视频。

### 创建视频生成任务
`/contents/generations/tasks` 创建视频生成任务

### Language Examples

=== "CURL"

    ```shell

    curl https://api.apigo.ai/api/v3/contents/generations/tasks \
      -H "Content-Type: application/json" \
      -H "Authorization: Bearer $ARK_API_KEY" \
      -d '{
        "model": "doubao-seedance-1-0-pro-250528",
        "content": [
            {
                "type": "text",
                "text": "女孩抱着狐狸，女孩睁开眼，温柔地看向镜头，狐狸友善地抱着，镜头缓缓拉出，女孩的头发被风吹动  --ratio adaptive  --dur 5"
            },
            {
                "type": "image_url",
                "image_url": {
                    "url": "https://ark-project.tos-cn-beijing.volces.com/doc_image/i2v_foxrgirl.png"
                }
            }
        ]
    }'

    ```


