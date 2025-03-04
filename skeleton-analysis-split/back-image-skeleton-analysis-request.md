# Back Image Skeleton Analysis Request

### Back Image Skeleton Analysis Request

<mark style="color:green;">`POST`</mark> `http://api.remo.re.kr/api/analysis-skeleton-v2-back`

Analyzes body skeleton by receiving a back photo.

**Parameters(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>Email</code></td><td>string</td><td>User email address</td><td>true</td></tr><tr><td><code>UserKey</code></td><td>string</td><td>Issued user key value</td><td>true</td></tr><tr><td><code>APIKey</code></td><td>string</td><td>Issued API key value</td><td>true</td></tr><tr><td><code>borigimg</code></td><td>string(base64)</td><td>Base64 encoded back photo</td><td>true</td></tr></tbody></table>

**Response(json)**

\*Left and right standards are based on the subject in the photo

<table><thead><tr><th width="282">Name</th><th width="94">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>state</code></td><td>bool</td><td>True on success, False on failure</td></tr><tr><td><code>status_code</code></td><td>int</td><td>200 on success, error code on failure</td></tr><tr><td><code>uuid</code></td><td>string</td><td>UUID received as parameter</td></tr><tr><td><code>credit_change</code></td><td>int</td><td>Amount of credit used in analysis</td></tr><tr><td><code>credit</code></td><td>int</td><td>Current credit balance</td></tr><tr><td><code>forigimg</code></td><td>string</td><td>Front photo with results drawn, base64 encoded image</td></tr><tr><td><code>sorigimg</code></td><td>string</td><td>Side photo with results drawn, base64 encoded image</td></tr><tr><td><code>borigimg</code></td><td>string</td><td>Back photo with results drawn, base64 encoded image</td></tr><tr><td><code>bar_coords</code></td><td>string</td><td>Back 2D skeleton coordinates converted to JSON string</td></tr><tr><td><code>bar_head_bal_m_</code></td><td>float</td><td>Head balance (head tilt). In degree units.</td></tr><tr><td><code>bar_head_bal_grade</code></td><td>int</td><td><p>Head balance (head tilt) evaluation.</p><p>-2 : Dangerously tilted up to the right (value&#x3C;=-4)</p><p>-1 : Caution for tilt up to the right (-4&#x3C;value&#x3C;=-1)</p><p>0 : Normal (-1&#x3C;value&#x3C;1)</p><p>1 : Caution for tilt up to the left (1&#x3C;=value&#x3C;4)</p><p>2 : Dangerously tilted up to the left (value>=4)</p></td></tr><tr><td><code>bar_pelvic_bal_m_</code></td><td>float</td><td>Pelvic balance (pelvic tilt). In degree units.</td></tr><tr><td><code>bar_pelvic_bal_grade</code></td><td>int</td><td><p>Pelvic balance (pelvic tilt) evaluation.<br>-2 : Dangerously tilted up to the right (value&#x3C;=-4)</p><p>-1 : Caution for tilt up to the right (-4&#x3C;value&#x3C;=-1)</p><p>0 : Normal (-1&#x3C;value&#x3C;1)</p><p>1 : Caution for tilt up to the left (1&#x3C;=value&#x3C;4)</p><p>2 : Dangerously tilted up to the left (value>=4)</p></td></tr><tr><td><code>bar_shoulder_bal_m_</code></td><td>float</td><td>Shoulder balance (shoulder tilt). In degree units.</td></tr><tr><td><code>bar_shoulder_bal_grade</code></td><td>int</td><td><p>Shoulder balance (shoulder tilt) evaluation.<br>-2 : Dangerously tilted up to the right (value&#x3C;=-4)</p><p>-1 : Caution for tilt up to the right (-4&#x3C;value&#x3C;=-1)</p><p>0 : Normal (-1&#x3C;value&#x3C;1)</p><p>1 : Caution for tilt up to the left (1&#x3C;=value&#x3C;4)</p><p>2 : Dangerously tilted up to the left (value>=4)</p></td></tr><tr><td><code>bar_left_qang_m_</code></td><td>float</td><td>Left bow leg value. In degree units.</td></tr><tr><td><code>bar_left_qang_grade</code></td><td>int</td><td><p>Left bow leg value evaluation.<br>-2 : X-leg dangerous (value&#x3C;=-12)</p><p>-1 : X-leg caution (-12&#x3C;value&#x3C;=-6)</p><p>0 : Normal (-6&#x3C;value&#x3C;6)</p><p>1 : O-leg caution (6&#x3C;=value&#x3C;12)</p><p>2 : O-leg dangerous (value>=12)</p></td></tr><tr><td><code>bar_right_qang_m_</code></td><td>float</td><td>Right bow leg value. In degree units.</td></tr><tr><td><code>bar_right_qang_grade</code></td><td>int</td><td><p>Right bow leg value evaluation.<br>-2 : X-leg dangerous (value&#x3C;=-12)</p><p>-1 : X-leg caution (-12&#x3C;value&#x3C;=-6)</p><p>0 : Normal (-6&#x3C;value&#x3C;6)</p><p>1 : O-leg caution (6&#x3C;=value&#x3C;12)</p><p>2 : O-leg dangerous (value>=12)</p></td></tr><tr><td><code>bar_knee_bal_m_</code></td><td>float</td><td>Knee balance (knee tilt). In degree units.</td></tr><tr><td><code>bar_knee_bal_grade</code></td><td>int</td><td><p>Knee balance (knee tilt) evaluation.<br>-2 : Dangerously tilted up to the right (value&#x3C;=-4)</p><p>-1 : Caution for tilt up to the right (-4&#x3C;value&#x3C;=-1)</p><p>0 : Normal (-1&#x3C;value&#x3C;1)</p><p>1 : Caution for tilt up to the left (1&#x3C;=value&#x3C;4)</p><p>2 : Dangerously tilted up to the left (value>=4)</p></td></tr><tr><td><code>bar_tilt_m_</code></td><td>float</td><td>Back axis tilt (lateral tilt). In degree units.</td></tr><tr><td><code>bar_tilt_grade</code></td><td>int</td><td><p>Back axis tilt (lateral tilt) evaluation.<br>-2 : Dangerously tilted up to the right (value&#x3C;=-4)</p><p>-1 : Caution for tilt up to the right (-4&#x3C;value&#x3C;=-1)</p><p>0 : Normal (-1&#x3C;value&#x3C;1)</p><p>1 : Caution for tilt up to the left (1&#x3C;=value&#x3C;4)</p><p>2 : Dangerously tilted up to the left (value>=4)</p></td></tr></tbody></table>

**Request Example**

```json
{
  "Email": "example@email.com",
  "UserKey": "userkey",
  "APIKey": "apikey",
  "borigimg": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAIBAQEBAQIBAQECAgICAgQDAgICAgUEBAMEBgUGBgYFBgYGBw ... (omitted)(result of converting image to bytes)"
 }
```

**Example Code**

{% tabs %}
{% tab title="curl" %}
```bash
curl -X POST "http://api.remo.re.kr/api/analysis-skeleton-v2-back" \
-H "Content-Type: application/json" \
-d '{
    "Email": "your_email",
    "UserKey": "your_user_key",
    "APIKey": "your_api_key",
    "borigimg": "'$(base64 -w 0 path/to/your/back/image)'"
}'
```
{% endtab %}

{% tab title="Python" %}
```python
import requests
import uuid
import base64

bimg_path = "path/to/your/back/image"

with open(bimg_path, "rb") as img_file:
    bimg_b64 = base64.b64encode(img_file.read()).decode('utf-8')

task_uuid = str(uuid.uuid4())
rq_dict = {'Email': "your_email", "UserKey": "your_user_key", "APIKey": "your_api_key", "borigimg": bimg_b64}

res = requests.post("http://api.remo.re.kr/api/analysis-skeleton-v2-back", json=rq_dict)
```
{% endtab %}

{% tab title="javascript" %}
```javascript
import fetch from 'node-fetch';
import fs from 'fs';
cv2.imshow('front_img', front_img)
cv2.imshow('side_img', side_img)
import { v4 as uuidv4 } from 'uuid';

const bimg_path = "path/to/your/back/image";

const bimg_b64 = fs.readFileSync(bimg_path, { encoding: 'base64' });

const task_uuid = uuidv4();
const rq_dict = {
  Email: "your_email",
  UserKey: "your_user_key",
  APIKey: "your_api_key",
  borigimg: bimg_b64,
};

fetch("http://api.remo.re.kr/api/analysis-skeleton-v2-back", {
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
  'borigimg': 'data:image/jpeg;base64,/9j/4A ... (abbreviated) ... A8x//2Q==',
  'bar_coords': '[[1060, 816], [1053, 1079], [1199, 1134], [1417, 1340], [1609, 1465], [903, 1121], [661, 1301], [448, 1397], [1162, 1605], [1156, 2076], [1159, 2449], [899, 1595], [873, 2069], [861, 2438], [1028, 1586], [1042, 1358], [1054, 991], [983, 943], [1007, 937], [1034, 979], [1128, 950], [1075, 940]]',
  'bar_head_bal_grade': 0,
  'bar_head_bal_m_': -0.011,
  'bar_knee_bal_grade': 0,
  'bar_knee_bal_m_': -0.312,
  'bar_left_qang_grade': 0,
  'bar_left_qang_m_': 0.665,
  'bar_pelvic_bal_grade': 0,
  'bar_pelvic_bal_m_': 0.299,
  'bar_right_qang_grade': 0,
  'bar_right_qang_m_': 2.109,
  'bar_shoulder_bal_grade': 0,
  'bar_shoulder_bal_m_': 0.544,
  'bar_tilt_grade': 0,
  'bar_tilt_m_': -0.125
}
```
{% endtab %}

{% tab title="400 ~" %}
```json
{
  "state": False,
  "credit": 100,
  "message": 'error from back image decoding b64',
  "status":413
}
```
{% endtab %}

{% tab title="500 ~" %}
```json
{
  "state": False,
  "credit": 100,
  "message": 'In the back image, the model is not facing side ',
  "status": 515
}
```
{% endtab %}
{% endtabs %}

**Error Code Guide**

| Main Category      | Sub Category                      | Code |
| ------------------ | --------------------------------- | ---- |
| Input Data Problem | Protocol Error                    | 400  |
|                    | Input Data Missing                | 411  |
|                    | Attached Image Error              | 412  |
| Other Issues       | User Not Identified               | 420  |
|                    | Incorrect APIKey                  | 421  |
|                    | Insufficient Credit               | 422  |
| Analysis Issues    | Person Not Detected in Back Image | 518  |
|                    | Incorrect Angle in Back Image     | 522  |
| Process Error      | Process Handling Error            | 550  |
|                    | Other Process Error               | 559  |

**View Request Image Results**

{% tabs %}
{% tab title="Python" %}
```python
import requests
import uuid
import base64
import cv2
import numpy as np
import uuid

bimg_path = "path/to/your/back/image"

with open(bimg_path, "rb") as img_file:
    bimg_b64 = base64.b64encode(img_file.read()).decode('utf-8')

task_uuid = str(uuid.uuid4())
rq_dict = {'Email': "your_email", "UserKey": "your_user_key", "APIKey": "your_api_key", 'uuid': task_uuid, "borigimg": bimg_b64}
res = requests.post("http://api.remo.re.kr/api/analysis-skeleton", json=rq_dict).json()

# Convert back image analysis result data from byte data to array data
bimg_b64 = res["borigimg"] #Back image analysis result data
b_bytes = base64.b64decode(split_b64_video(bimg_b64).encode('utf-8'))
back_nparr = np.frombuffer(b_bytes, np.uint8)
back_img = cv2.imdecode(back_nparr, cv2.IMREAD_COLOR)

# Display the image using OpenCV
cv2.imshow('back_img', back_img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
{% endtab %}
{% endtabs %}

**Result Image**

<figure><img src="../.gitbook/assets/out (1).jpg" alt="" width="375"><figcaption><p>borigimg</p></figcaption></figure>
