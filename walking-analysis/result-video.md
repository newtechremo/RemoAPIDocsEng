---
description: API for requesting completed walking analysis result videos.
---

# Request Walking Analysis Result Video

## Request Walking Analysis Result Video

<mark style="color:green;">`POST`</mark> `http://api.remo.re.kr/api/analysis-walking-draw`

Returns a base64 encoded video with analysis results drawn on the original video by receiving user id (email) and analyzed video uuid as parameters.

**Parameters(json)**

| Name   | Type   | Description        | Required |
| ------ | ------ | ------------------ | -------- |
| `id`   | string | User email address | true     |
| `uuid` | string | Video uuid         | true     |

**Response(json)**

| Name           | Type   | Description                                                   |
| -------------- | ------ | ------------------------------------------------------------- |
| `state`        | int    | 1 for success, 0 for failure                                  |
| `message`      | string | Success or failure related guidance message                   |
| `base64_video` | string | Base64 encoded video with results drawn on the original video |

**Request Example**

```json
/get-draw/example@example.com/bc692864-0243-4d41-bce3-7658c92ef0c5
```

**Response Example**

{% tabs %}
{% tab title="200" %}
```json
{
  "state": 1,
  "base64_video": "AAAAIGZ0eXBpc29tAAACAGlzb21pc28yYXZjMW1wNDEAAAAIZnJlZQAK/7BtZGF0AAACugYF … (truncated)",
  "message": "success"
}
```
{% endtab %}

{% tab title="400" %}
```json
{
  "state": 0,
  "message": "An error occurred in returning results due to video file being created"
}
```
{% endtab %}

{% tab title="400" %}
```json
{
  "state": 0,
  "message": "base64 encoding error"
}
```
{% endtab %}
{% endtabs %}
