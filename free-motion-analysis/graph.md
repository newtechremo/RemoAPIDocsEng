---
description: API for requesting completed free motion analysis graph values.
---

# Request Free Motion Analysis Graph

## Request Free Motion Analysis Graph

<mark style="color:green;">`POST`</mark> `http://api.remo.re.kr/api/analysis-FreeMotion-angle`

Returns angle values needed to draw a graph by receiving user id (email), analyzed video uuid, and joint (body part where angle output is desired) as parameters.

**Parameters(json)**

| Name    | Type   | Description                                                                           | Required |
| ------- | ------ | ------------------------------------------------------------------------------------- | -------- |
| `id`    | string | User email address                                                                    | true     |
| `uuid`  | string | Video uuid                                                                            | true     |
| `joint` | string | Choose one from "Hip", "Knee", "Ankle", "Shoulder", "Elbow", "Wrist", "Spine", "Neck" | true     |

**Response(json)**

| Name         | Type   | Description                                                        |
| ------------ | ------ | ------------------------------------------------------------------ |
| `state`      | int    | 1 for success, 0 for failure                                       |
| `message`    | string | Success or failure related guidance message                        |
| `Hip`        | dict   | Hip joint. Contains Sagittal, Coronal, Transverse as keys.         |
| `Knee`       | dict   | Knee. Contains Sagittal, Coronal, Transverse as keys.              |
| `Ankle`      | dict   | Ankle. Contains Sagittal, Coronal, Transverse as keys.             |
| `Shoulder`   | dict   | Shoulder. Contains Sagittal, Coronal, Transverse as keys.          |
| `Elbow`      | dict   | Elbow. Contains Sagittal, Coronal, Transverse as keys.             |
| `Wrist`      | dict   | Wrist. Contains Sagittal, Coronal, Transverse as keys.             |
| `Spine`      | dict   | Spine. Contains Sagittal, Coronal, Transverse as keys.             |
| `Neck`       | dict   | Neck. Contains Sagittal, Coronal, Transverse as keys.              |
| `Sagittal`   | dict   | Sagittal plane. Contains range, left, right as keys.               |
| `Coronal`    | dict   | Coronal plane. Contains range, left, right as keys.                |
| `Transverse` | dict   | Transverse plane. Contains range, left, right as keys.             |
| `range`      | list   | Graph axis range. Sets axis range from first value to second value |
| `left`       | dict   | Left. Contains mean as key.                                        |
| `right`      | dict   | Right. Contains mean as key.                                       |
| `mean`       | list   | List of joint angle values                                         |
| `min`        | int    | Minimum value of mean                                              |
| `max`        | int    | Maximum value of mean                                              |

**Request Example**

```json
{
  "id": "example@example.com",
  "uuid": "d4147f2c-b5cc-4289-9325-94dbbef26d67"
  "joint": "Hip"
}
```

**Response Example**

Success Response (200):

```json
{
  "state": 1,
  "message": success,
  "Hip": {
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
  }
}
```

Error Response (400):

```json
{
  "state": 0,
  "message": "file does not exist"
}
```
