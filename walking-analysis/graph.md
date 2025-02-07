---
description: API for requesting completed gait analysis graph values.
---

# Request Gait Analysis Graph

## Request Gait Analysis Graph

<mark style="color:green;">`POST`</mark> `http://api.remo.re.kr/api/analysis-walking-angle`

Returns angle values needed to draw graphs by receiving user id (email) and analyzed video uuid as parameters.

**Parameters(json)**

| Name | Type | Description | Required |
|------|------|-------------|-----------|
| `id` | string | User email address | true |
| `uuid` | string | Video uuid | true |

**Response(json)**

| Name | Type | Description |
|------|------|-------------|
| `state` | int | 1 for success, 0 for failure |
| `message` | string | Success or failure related guidance message |
| `hip` | dict | Hip joint. Contains Sagittal, Coronal, Transverse as keys |
| `knee` | dict | Knee joint. Contains Sagittal, Coronal, Transverse as keys |
| `ankle` | dict | Ankle joint. Contains Sagittal, Coronal, Transverse as keys |
| `Sagittal` | dict | Sagittal plane. Contains range, left, right as keys |
| `Coronal` | dict | Coronal plane. Contains range, left, right as keys |
| `Transverse` | dict | Transverse plane. Contains range, left, right as keys |
| `range` | list | Graph axis range. Sets axis range from first value to second value |
| `left` | dict | Left side. Contains mean as key |
| `right` | dict | Right side. Contains mean as key |
| `mean` | list | List of joint angle values |

**Request Example**

```json
/get-angle/example@example.com/bc692864-0243-4d41-bce3-7658c92ef0c5
```

**Response Example**

{% tabs %}
{% tab title="200" %}
```json
{
  "hip": {
    "Sagittal": {
      "range": [-30, 30],
      "left": {
        "mean": [
          33.51917, 33.46679, ..., 32.01168, 32.21679
        ]
      },
      "right": {
        "mean": [
          24.58494, 24.49458, ..., 24.13248, 24.09185
        ]
      }
    },
    "Coronal": {
      "range": [-10, 30],
      "left": {
        "mean": [
          5.11125, 4.98427, ..., 7.69327, 7.41942
        ]
      },
      "right": {
        "mean": [
          2.69405, 2.44131, ..., 4.99395, 4.70155
        ]
      }
    },
    "Transverse": {
      "range": [-90, 20],
      "left": {
        "mean": [
          0.27234, 0.15604, ..., -0.07908, -0.08991
        ]
      },
      "right": {
        "mean": [
          2.62555, 2.66186, ..., 2.39876, 2.47905
        ]
      }
    }
  },
  "knee": {
    "Sagittal": {
      "range": [0, 70],
      "left": {
        "mean": [
          17.55313, 17.86393, ..., 14.62733, 14.41221
        ]
      },
      "right": {
        "mean": [
          13.89033, 13.13457, ..., 13.69133, 12.58434
        ]
      }
    },
    "Coronal": {
      "range": [-5, 5],
      "left": {
        "mean": [
          -7.38343, -7.26108, ..., -5.30595, -5.25075
        ]
      },
      "right": {
        "mean": [
          -13.48968, -13.73512, ..., -12.81147, -13.10944
        ]
      }
    },
    "Transverse": {
      "range": [-5, 5],
      "left": {
        "mean": [
          -27.87897, -27.81244, ..., -26.02685, -26.07673
        ]
      },
      "right": {
        "mean": [
          -20.35731, -20.24204, ..., -20.10835, -20.35162
        ]
      }
    }
  },
  "ankle": {
    "Sagittal": {
      "range": [-30, 20],
      "left": {
        "mean": [
          -3.91493, -3.84959, ..., -7.71493, -7.68264
        ]
      },
      "right": {
        "mean": [
          -0.98987, -0.74556, ..., -3.16904, -2.96793
        ]
      }
    },
    "Coronal": {
      "range": [-20, 20],
      "left": {
        "mean": [
          -0.77926, -0.83188, ..., -4.14389, -3.82192
        ]
      },
      "right": {
        "mean": [
          4.87106, 5.38434, ..., 2.74012, 3.34569
        ]
      }
    },
    "Transverse": {
      "range": [-20, 60],
      "left": {
        "mean": [
          5.92304, 5.62899, ..., 8.1099, 7.72117
        ]
      },
      "right": {
        "mean": [
          17.80345, 18.07364, ..., 16.68639, 17.17034
        ]
      }
    }
  }
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
{% endtabs %}

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>