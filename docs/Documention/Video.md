# Create Video
Call OpenAI's video generation API (supporting models like Sora) to generate videos.

## Language Examples



=== "CURL"

    ```shell
     curl https://api.apigo.ai/v1/videos \
      -H "Authorization: Bearer YOUR_API_KEY" \
      -F "model=sora-2" \
      -F "prompt=A calico cat playing a piano on stage"
    ```



## Header

| Name | Type | Required | Description                                                       |
| --- | --- | --- |-------------------------------------------------------------------|
| Authorization | string | required | Include your API key in the Authorization header of your requests |
| Content-Type | string | required | application/json                                                  |

## Query Parameters
| Name | Type   | Required | Description                              |
| --- |--------| --- |------------------------------------------|
| prompt | string | required | The text prompt describing the video to be generated.  |
| model | string | required | Video generation model, defaulting to sora-2.  |
| seconds | string |  | Video duration (in seconds), defaulting to 10 seconds.  |
| size | string |  | Output resolution, formatted as width×height, defaulting to 720×1280.  |
| input_reference | file   |  | Optional image reference, used to guide generation.  |

##  Responses Parameters
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


## Responses Result
| Code | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| --- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 200 | video completion response<br> **Example Response:**<pre><code>{<br>&nbsp;&nbsp;"id": "video_123",<br>&nbsp;&nbsp;"object": "video",<br>&nbsp;&nbsp;"model": "sora-2",<br>&nbsp;&nbsp;"status": "queued",<br>&nbsp;&nbsp;"progress": 0,<br>&nbsp;&nbsp;"created_at": 1712697600,<br>&nbsp;&nbsp;"size": "1024x1808",<br>&nbsp;&nbsp;"seconds": "8",<br>&nbsp;&nbsp;"quality": "standard"<br>}</code></pre> |
| 400 | Bad Request - Invalid query parameters.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| 500 | 500	Internal Server Error.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
