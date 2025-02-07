---
description: >-
  API for generating predicted images of body shape changes for subjects in
  images.
---

# Request Future Body Shape Image Generation

## Request Future Body Shape Image Generation

<mark style="color:green;">`POST`</mark> `/generate-image`

Generates images showing weight loss and weight gain appearances based on the subject's photo.

**Parameters(json)**

| Name             | Type   | Description                                                     | Required |
| ---------------- | ------ | --------------------------------------------------------------- | -------- |
| `imagePath`      | string | Image path                                                      | true     |
| `requestMessage` | string | "best": weight loss appearance, "worst": weight gain appearance | true     |
| `gender`         | string | "male": male, "female": female                                  | true     |

**Response(json)**

| Name          | Type   | Description                                           |
| ------------- | ------ | ----------------------------------------------------- |
| `state`       | bool   | True for analysis success, False for analysis failure |
| `message`     | string | Indicates the problematic area when analysis fails    |
| `resultImage` | string | Result image (Base64 format)                          |

**Request Example**

```json
{
    "imagePath": "path/to/image.jpg",
    "requestMessage": "best",
    "gender": "male"
}
```

**Response Example**

{% tabs %}
{% tab title="200" %}
```json
{
    'state': True,
    'result_image': 'iVBORw0KGgoAAAANSUhEUgAAAgAAAAIACAIAAAB7GkOtAAAgAElEQVR4AdTBS49t23ne9//zvmPOtapq73P2uYhiFDDSoURT1AUw7VDOxTKgIBEEJTZsmvCl5e+QjoE03BEQIN9BffUFw24EBpLIUpwgaSWQaFEyFVMSEZ4rz6ldtdacY7xPag9q2bXNLQNp7t9P/83f+3u81iJtA7YB20y9d17FNq/Se2eSBEhiurm5kQToEUASj9hm0hittYioKkmZabtPmriwDSiDV7m+vu6939/f995ba9fX1xHRy+14Fbm01iIC0CMR0abMtF1Ta4eIyExJQFy01mxXlW1JEZGZEYFSUkyZqQmwHRdAXSxL+qKqfNFaO5/Pp9NpjBFTPfCgbA/bY4ze+77vvfeqkmR7TPu+96mqGn5QLwMioibbkmzXFBG2xxi2AUkRIWmMYbsmQFJEOHQ+ … (후략)'
}
```
{% endtab %}

{% tab title="400" %}
```json
{
    'state': False,
    'message': 'wrong image'
}
```
{% endtab %}

{% tab title="400" %}
```json
{
    'state': False,
    'message': 'keypoint inference error'
}
```
{% endtab %}
{% endtabs %}
