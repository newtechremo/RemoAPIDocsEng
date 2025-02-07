---
description: API for requesting completed walking analysis results.
---

# Request Walking Analysis Result

## Request Walking Analysis Result

<mark style="color:green;">`POST`</mark> `http://api.remo.re.kr/api/analysis-walking-result`

Returns walking analysis results by receiving user id (email) and analyzed video uuid as parameters.

**Parameters(json)**

| Name   | Type   | Description        | Required |
| ------ | ------ | ------------------ | -------- |
| `id`   | string | User email address | true     |
| `uuid` | string | Video uuid         | true     |

**Response(json)**

| Name      | Type   | Description                                                                                                                            |
| --------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------- |
| `state`   | int    | 1 for success, 0 for failure                                                                                                           |
| `message` | string | Success or failure related guidance message                                                                                            |
| `uuid`    | string | UUID received as parameter                                                                                                             |
| `result`  | list   | Contains dict values for cadence, gait velocity(m/s), step length(cm), stance phase(%), swing phase(%), and double support(%) in order |
| `total`   | float  | Average of left and right values                                                                                                       |
| `left`    | float  | Left side value                                                                                                                        |
| `right`   | float  | Right side value                                                                                                                       |

**Request Example**

```json
/get-result/example@example.com/bc692864-0243-4d41-bce3-7658c92ef0c5
```

**Response Example**

{% tabs %}
{% tab title="200" %}
```json
{
  "state": 1,
  "result": [
    {
      "total": 89.1473000683527,
      "left": 86.3961038961039,
      "right": 91.8984962406015
    },
    {
      "total": 0.3213670029837894,
      "left": 0.2981104250341651,
      "right": 0.34462358093341366
    },
    {
      "total": 21.573702360911454,
      "left": 20.658755943773752,
      "right": 22.488648778049154
    },
    {
      "total": 61.49912039714671,
      "left": 63.38291642567958,
      "right": 59.61532436861384
    },
    {
      "total": 38.50087960285329,
      "left": 36.61708357432042,
      "right": 40.38467563138616
    },
    {
      "total": 26.8069512724118,
      "left": 26.797582899556588,
      "right": 26.816319645267015
    }
  ],
  "uuid": "bc692864-0243-4d41-bce3-7658c92ef0c5",
  "message": "success"
}
```
{% endtab %}

{% tab title="400" %}
```json
{
  "state": 0,
  "message": "file does not exist"
}
```
{% endtab %}

{% tab title="400" %}
```json
{
  "state": 0,
  "message": "not a walking video"
}
```
{% endtab %}
{% endtabs %}

<figure><img src="../.gitbook/assets/Screenshot from 2024-05-10 17-29-33.png" alt=""><figcaption></figcaption></figure>
