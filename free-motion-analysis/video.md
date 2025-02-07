---
description: API for analyzing user's free motion by receiving video input.
---

# Request Free Motion Video Analysis

## Request Free Motion Video Analysis

<mark style="color:green;">`POST`</mark> `http://api.remo.re.kr/api/analysis-walking`

Returns the waiting time until analysis completion after receiving a free motion video input.

**Parameters(json)**

| Name           | Type                   | Description                             | Required |
| -------------- | ---------------------- | --------------------------------------- | -------- |
| `base64_video` | string(base64 encoded) | Base64 encoded free motion video string | true     |
| `id`           | string                 | User email address                      | true     |
| `height`       | string                 | Height of the analysis subject          | true     |

**Response(json)**

| Name        | Type   | Description                                         |
| ----------- | ------ | --------------------------------------------------- |
| `state`     | int    | 1 for success, 0 for failure                        |
| `message`   | string | Success or failure related guidance message         |
| `uuid`      | string | Video uuid                                          |
| `wait_time` | int    | Waiting time until result generation after response |

**Request Example**

```json
{
    "base64_video": "AAAAIGZ0eXBpc29tAAACAGlzb21pc28yYXZjMW1wNDEAAAAIZnJlZQAK/7BtZGF0AAACugYF … (truncated)",
    "id": "example@example.com",
    "height": "170"
}
```

**Response Example**

{% tabs %}
{% tab title="200" %}
```json
{
  "state": 1,
  "wait_time": 13,
  "uuid": "d4147f2c-b5cc-4289-9325-94dbbef26d67",
  "message": "success"
}
```
{% endtab %}

{% tab title="400" %}
```json
{
  "state": 0,
  "message": "person not detected"
}
```
{% endtab %}

{% tab title="400" %}
```json
{
  "state": 0,
  "message": "keypoint estimation error"
}
```
{% endtab %}
{% endtabs %}
