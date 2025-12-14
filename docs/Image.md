# Create Image
Call OpenAI's image generation API (supporting models like Sora) to generate images.

## Language Examples



=== "CURL"

    ```shell
     curl https://api.apigo.ai/v1/images/generations \
      -H "Content-Type: application/json" \
      -H "Authorization: Bearer $NEWAPI_API_KEY" \
      -d '{
        "model": "dall-e-3",
        "prompt": "一只可爱的小海獭",
        "n": 1,
        "size": "1024x1024"
      }'
    ```


## Header

| Name | Type | Required | Description                                                       |
| --- | --- | --- |-------------------------------------------------------------------|
| Authorization | string | required | Include your API key in the Authorization header of your requests |
| Content-Type | string | required | application/json                                                  |

## Query Parameters
| Name            | Type    | Required | Description                              |
|-----------------|---------| --- |------------------------------------------ |
| prompt          | string  | required | The text prompt describing the video to be generated.  |
| model           | string  | required | Video generation model, defaulting to sora-2.  |
| n               | integer |  |  |
| size            | string  |  | Output resolution, formatted as width×height, defaulting to 720×1280.  |

##  Responses Parameters
| Name                                            | Type    | Description                                                                                                                                                                                                                                                                    | Example    |
|-------------------------------------------------|---------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|
| id                                              | string  | image ID                                                                                                                                                                                                                                                               | image_123  |
| data                                          | string  |                                                                                                                                                                                                                                                | image      |
| data.b64_json                                           | string  | Name of the model used                                                                                                                                                                                                                                                         | sora-2     |
| created                             | integer | Creation timestamp                                                                                                                                                                                                                                                          | 1712697600 |

## Responses Result
| Code | Description                                                                                                                                                                                                                                                                                                                                                                                                              |
| --- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 200 | image completion response<br> **Example Response:**<pre><code>{<br>&nbsp;&nbsp;"created": "1589478378",<br>&nbsp;&nbsp;"data": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"url": "https://...",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"revised_prompt": "一只可爱的小海獭在水中嬉戏,它有着圆圆的眼睛和毛茸茸的皮毛"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;]<br>}</code></pre> |
| 400 | Bad Request - Invalid query parameters.                                                                                                                                                                                                                                                                                                                                                                                  |
| 500 | 500	Internal Server Error.                                                                                                                                                                                                                                                                                                                                                                                               |
