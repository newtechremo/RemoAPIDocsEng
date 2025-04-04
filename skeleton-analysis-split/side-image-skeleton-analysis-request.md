# Side Image Skeleton Analysis Request

### Side Image Skeleton Analysis Request

<mark style="color:green;">`POST`</mark> `http://api.remo.re.kr/api/analysis-skeleton-v2-side`

Analyzes body skeleton from a side view photo.

**Parameters(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>Email</code></td><td>string</td><td>User email address</td><td>true</td></tr><tr><td><code>UserKey</code></td><td>string</td><td>Issued user key value</td><td>true</td></tr><tr><td><code>APIKey</code></td><td>string</td><td>Issued API key value</td><td>true</td></tr><tr><td><code>sorigimg</code></td><td>string(base64)</td><td>Base64 encoded side view photo</td><td>true</td></tr></tbody></table>

**Response(json)**

\*Left and right standards are based on the subject in the photo

<table><thead><tr><th width="282">Name</th><th width="94">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>state</code></td><td>bool</td><td>True on success, False on failure</td></tr><tr><td><code>status_code</code></td><td>int</td><td>200 on success, error code on failure</td></tr><tr><td><code>uuid</code></td><td>string</td><td>UUID received as parameter</td></tr><tr><td><code>credit_change</code></td><td>int</td><td>Amount of credits used in the analysis</td></tr><tr><td><code>credit</code></td><td>int</td><td>Current credit balance</td></tr><tr><td><code>sorigimg</code></td><td>string</td><td>Base64 encoded image with results drawn on the side view photo</td></tr><tr><td><code>round_shoulder_m_</code></td><td>float</td><td>Rounded shoulder slope. In degree units.</td></tr><tr><td><code>round_shoulder_grade</code></td><td>int</td><td>Rounded shoulder slope evaluation.<br>0 : Normal(value&#x3C;5)<br>1 : Caution(5&#x3C;=value&#x3C;15)<br>2 : Risk(value>=15)</td></tr><tr><td><code>sar_coords</code></td><td>string</td><td>Side view 2D skeleton coordinates converted to JSON string</td></tr><tr><td><code>sar_head_tilt_grade</code></td><td>int</td><td><p>Side view head balance (side head tilt) evaluation.<br>-2 : Backward tilt risk(value&#x3C;=-5)</p><p>-1 : Backward tilt caution(-5&#x3C;value&#x3C;=-1.5)</p><p>0 : Normal(-1.5&#x3C;value&#x3C;1.5)</p><p>1 : Forward tilt caution(1.5&#x3C;=value&#x3C;5)</p><p>2 : Forward tilt risk(value>=5)</p></td></tr><tr><td><code>sar_head_tilt_m_</code></td><td>float</td><td>Side view head balance (front-back head tilt). In degree units.</td></tr><tr><td><code>sar_tilt_m_</code></td><td>float</td><td>Side view tilt (full body front-back tilt). In degree units.</td></tr><tr><td><code>sar_tilt_grade</code></td><td>int</td><td><p>Side view tilt (full body front-back tilt) evaluation.<br>-2 : Backward tilt risk(value&#x3C;=-5)</p><p>-1 : Backward tilt caution(-5&#x3C;value&#x3C;=-1.5)</p><p>0 : Normal(-1.5&#x3C;value&#x3C;3)</p><p>1 : Forward tilt caution(3&#x3C;=value&#x3C;10)</p><p>2 : Forward tilt risk(value>=10)</p></td></tr><tr><td><code>turtle_neck_m_</code></td><td>float</td><td>Turtle neck tilt. In degree units.</td></tr><tr><td><code>turtle_neck_grade</code></td><td>int</td><td>Turtle neck tilt evaluation.<br>0 : Normal(value&#x3C;=30)<br>1 : Caution(30&#x3C;value&#x3C;40)<br>2 : Risk(value>=40)</td></tr></tbody></table>

**Request Example**

```json
{
  "Email": "example@email.com",
  "UserKey": "userkey",
  "APIKey": "apikey",
  "sorigimg": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAIBAQEBAQIBAQECAgICAgQDAgICAgUEBAMEBgUGBgYFBgYGBw ... (omitted)(result of converting image to bytes)"
 }
```

**Example Code**

{% tabs %}
{% tab title="curl" %}
```bash
curl -X POST "http://api.remo.re.kr/api/analysis-skeleton-v2-side" \
-H "Content-Type: application/json" \
-d '{
    "Email": "your_email",
    "UserKey": "your_user_key",
    "APIKey": "your_api_key",
    "sorigimg": "'$(base64 -w 0 path/to/your/side/image)'"
}'
```
{% endtab %}

{% tab title="Python" %}
```python
import requests
import uuid
import base64

simg_path = "path/to/your/side/image"

with open(simg_path, "rb") as img_file:
    simg_b64 = base64.b64encode(img_file.read()).decode('utf-8')

task_uuid = str(uuid.uuid4())
rq_dict = {'Email': "your_email", "UserKey": "your_user_key", "APIKey": "your_api_key", "sorigimg": simg_b64}

res = requests.post("http://api.remo.re.kr/api/analysis-skeleton-v2-side", json=rq_dict)
```
{% endtab %}

{% tab title="javascript" %}
```javascript
import fetch from 'node-fetch';
import fs from 'fs';
import { v4 as uuidv4 } from 'uuid';

const simg_path = "path/to/your/side/image";

const simg_b64 = fs.readFileSync(simg_path, { encoding: 'base64' });

const task_uuid = uuidv4();
const rq_dict = {
  Email: "your_email",
  UserKey: "your_user_key",
  APIKey: "your_api_key",
  sorigimg: simg_b64,
};

fetch("http://api.remo.re.kr/api/analysis-skeleton-v2-side", {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify(rq_dict)
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));

```
{% endtab %}
{% endtabs %}

**Response Example**

{% tabs %}
{% tab title="200" %}
```json
{
  'state': True,
  'status_code': 200,
  'APIName': 'Analysis-skeleton-v2',
  'credit_change': -1,
  'credit': 99984228,
  'uuid': '59e9a3a1-a8d2-42a1-b2af-3a87cd01f682',
  'sorigimg': 'data:image/jpeg;base64,/9j/4A ... (omitted) ... A8x//2Q==',
  'round_shoulder_grade': 0,
  'round_shoulder_m_': 2.698,
  'sar_coords': '[[424, 210], [418, 365], [419, 382], [435, 527], [437, 659], [423, 406], [434, 550], [448, 649], [435, 651], [437, 952], [395, 1174], [439, 650], [431, 931], [398, 1143], [445, 647], [425, 517], [426, 314], [433, 293], [485, 275], [503, 293], [430, 274], [484, 266]]',
  'sar_head_tilt_grade': -1,
  'sar_head_tilt_m_': -2.227,
  'sar_tilt_grade': 2,
  'sar_tilt_m_': 6.37,
  'turtle_neck_grade': 0,
  'turtle_neck_m_': 29.711
}
```
{% endtab %}

{% tab title="400 ~" %}
```json
{
  "state": False,
  "credit": 100,
  "message": 'error from front image decoding b64',
  "status":413
}
```
{% endtab %}

{% tab title="500 ~" %}
```json
{
  "state": False,
  "credit": 100,
  "message": 'In the side image, the model is not facing side ',
  "status": 515
}
```
{% endtab %}
{% endtabs %}

**Error Code Guide**

| Main Category      | Sub Category                      | Code |
| ------------------ | --------------------------------- | ---- |
| Input Data Problem | Protocol Error                    | 400  |
|                    | No Input Data                     | 411  |
|                    | Attached Image Error              | 412  |
|                    | Attached Image Error (Side)       | 414  |
| Other Issues       | User Not Verified                 | 420  |
|                    | Incorrect APIKey                  | 421  |
|                    | Insufficient Credit               | 422  |
| Analysis Issues    | Person Not Detected in Side Photo | 512  |
|                    | Incorrect Angle in Side Photo     | 515  |
| Process Errors     | Process Handling Error            | 550  |
|                    | Other Process Handling Error      | 559  |

**Viewing Request Image Results**

{% tabs %}
{% tab title="Python" %}
```python
import requests
import uuid
import base64
import cv2
import numpy as np
import uuid

simg_path = "path/to/your/side/image"

with open(simg_path, "rb") as img_file:
    simg_b64 = base64.b64encode(img_file.read()).decode('utf-8')

task_uuid = str(uuid.uuid4())
rq_dict = {'Email': "your_email", "UserKey": "your_user_key", "APIKey": "your_api_key", 'uuid': task_uuid, "sorigimg": simg_b64}
res = requests.post("http://api.remo.re.kr/api/analysis-skeleton-v2-side", json=rq_dict).json()

simg_b64 = res["sorigimg"]
s_bytes = base64.b64decode(split_b64_video(simg_b64).encode('utf-8'))
side_nparr = np.frombuffer(s_bytes, np.uint8)
side_img = cv2.imdecode(side_nparr, cv2.IMREAD_COLOR)

cv2.imshow('side_img', side_img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
{% endtab %}
{% endtabs %}

**Result Image**

<figure><img src="../.gitbook/assets/image (6).png" alt="" width="375"><figcaption><p>sorigimg</p></figcaption></figure>
