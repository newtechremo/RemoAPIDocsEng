# Front Image Skeleton Analysis Request

### Front Image Skeleton Analysis Request

<mark style="color:green;">`POST`</mark> `http://api.remo.re.kr/api/analysis-skeleton-v2-front`

Analyzes body skeleton from a front photo.

**Parameters(json)**

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td><code>Email</code></td><td>string</td><td>User email address</td><td>true</td></tr><tr><td><code>UserKey</code></td><td>string</td><td>Issued user key value</td><td>true</td></tr><tr><td><code>APIKey</code></td><td>string</td><td>Issued API key value</td><td>true</td></tr><tr><td><code>forigimg</code></td><td>string(base64)</td><td>Base64 encoded front photo</td><td>true</td></tr></tbody></table>

**Response(json)**

\*Left and right are based on the subject in the photo

<table><thead><tr><th width="282">Name</th><th width="94">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>state</code></td><td>bool</td><td>True if successful, False if failed</td></tr><tr><td><code>status_code</code></td><td>int</td><td>200 if successful, error code if failed</td></tr><tr><td><code>uuid</code></td><td>string</td><td>UUID received as parameter</td></tr><tr><td><code>credit_change</code></td><td>int</td><td>Amount of credits used for analysis</td></tr><tr><td><code>credit</code></td><td>int</td><td>Current credits owned</td></tr><tr><td><code>forigimg</code></td><td>string</td><td>Base64 encoded image with results drawn on the front photo</td></tr><tr><td><code>far_coords</code></td><td>string</td><td>Front 2D skeleton coordinates converted to JSON string</td></tr><tr><td><code>far_head_bal_m_</code></td><td>float</td><td>Head balance (head tilt). In degree units.</td></tr><tr><td><code>far_head_bal_grade</code></td><td>int</td><td><p>Head balance (head tilt) assessment.</p><p>-2 : Dangerous tilt to upper right (value&#x3C;=-4)</p><p>-1 : Caution tilt to upper right (-4&#x3C;value&#x3C;=-1)</p><p>0 : Normal (-1&#x3C;value&#x3C;1)</p><p>1 : Caution tilt to upper left (1&#x3C;=value&#x3C;4)</p><p>2 : Dangerous tilt to upper left (value>=4)</p></td></tr><tr><td><code>far_pelvic_bal_m_</code></td><td>float</td><td>Pelvic balance (pelvic tilt). In degree units.</td></tr><tr><td><code>far_pelvic_bal_grade</code></td><td>int</td><td><p>Pelvic balance (pelvic tilt).<br>-2 : Dangerous tilt to upper right (value&#x3C;=-4)</p><p>-1 : Caution tilt to upper right (-4&#x3C;value&#x3C;=-1)</p><p>0 : Normal (-1&#x3C;value&#x3C;1)</p><p>1 : Caution tilt to upper left (1&#x3C;=value&#x3C;4)</p><p>2 : Dangerous tilt to upper left (value>=4)</p></td></tr><tr><td><code>far_shoulder_bal_m_</code></td><td>float</td><td>Shoulder balance (shoulder tilt). In degree units.</td></tr><tr><td><code>far_shoulder_bal_grade</code></td><td>int</td><td><p>Shoulder balance (shoulder tilt).<br>-2 : Dangerous tilt to upper right (value&#x3C;=-4)</p><p>-1 : Caution tilt to upper right (-4&#x3C;value&#x3C;=-1)</p><p>0 : Normal (-1&#x3C;value&#x3C;1)</p><p>1 : Caution tilt to upper left (1&#x3C;=value&#x3C;4)</p><p>2 : Dangerous tilt to upper left (value>=4)</p></td></tr><tr><td><code>far_left_qang_m_</code></td><td>float</td><td>Left bow leg value. In degree units.</td></tr><tr><td><code>far_left_qang_grade</code></td><td>int</td><td><p>Left bow leg value assessment.<br>-2 : Knock-knee risk (value&#x3C;=-12)</p><p>-1 : Knock-knee caution (-12&#x3C;value&#x3C;=-6)</p><p>0 : Normal (-6&#x3C;value&#x3C;6)</p><p>1 : Bow-leg caution (6&#x3C;=value&#x3C;12)</p><p>2 : Bow-leg risk (value>=12)</p></td></tr><tr><td><code>far_right_qang_m_</code></td><td>float</td><td>Right bow leg value. In degree units.</td></tr><tr><td><code>far_right_qang_grade</code></td><td>int</td><td><p>Right bow leg value assessment.<br>-2 : Knock-knee risk (value&#x3C;=-12)</p><p>-1 : Knock-knee caution (-12&#x3C;value&#x3C;=-6)</p><p>0 : Normal (-6&#x3C;value&#x3C;6)</p><p>1 : Bow-leg caution (6&#x3C;=value&#x3C;12)</p><p>2 : Bow-leg risk (value>=12)</p></td></tr><tr><td><code>far_knee_bal_m_</code></td><td>float</td><td>Knee balance (knee tilt). In degree units.</td></tr><tr><td><code>far_knee_bal_grade</code></td><td>int</td><td><p>Knee balance (knee tilt) assessment.<br>-2 : Dangerous tilt to upper right (value&#x3C;=-4)</p><p>-1 : Caution tilt to upper right (-4&#x3C;value&#x3C;=-1)</p><p>0 : Normal (-1&#x3C;value&#x3C;1)</p><p>1 : Caution tilt to upper left (1&#x3C;=value&#x3C;4)</p><p>2 : Dangerous tilt to upper left (value>=4)</p></td></tr><tr><td><code>far_tilt_m_</code></td><td>float</td><td>Front axis tilt (lateral tilt). In degree units.</td></tr><tr><td><code>far_tilt_grade</code></td><td>int</td><td><p>Front axis tilt (lateral tilt) assessment.<br>-2 : Dangerous tilt to upper right (value&#x3C;=-4)</p><p>-1 : Caution tilt to upper right (-4&#x3C;value&#x3C;=-1)</p><p>0 : Normal (-1&#x3C;value&#x3C;1)</p><p>1 : Caution tilt to upper left (1&#x3C;=value&#x3C;4)</p><p>2 : Dangerous tilt to upper left (value>=4)</p></td></tr></tbody></table>

**Request Example**

```json
{
  "Email": "example@email.com",
  "UserKey": "userkey",
  "APIKey": "apikey",
  "forigimg": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAIBAQEBAQIBAQECAgICAgQDAgICAgUEBAMEBgUGBgYFBgYGBw ... (omitted)(result of converting image to bytes)"
 }
```

**Example Code**

{% tabs %}
{% tab title="curl" %}
```bash
curl -X POST "http://api.remo.re.kr/api/analysis-skeleton-v2-front" \
-H "Content-Type: application/json" \
-d '{
    "Email": "your_email",
    "UserKey": "your_user_key",
    "APIKey": "your_api_key",
    "forigimg": "'$(base64 -w 0 path/to/your/front/image)'"
}'
```
{% endtab %}

{% tab title="Python" %}
```python
import requests
import uuid
import base64

fimg_path = "path/to/your/front/image"

with open(fimg_path, "rb") as img_file:
    fimg_b64 = base64.b64encode(img_file.read()).decode('utf-8')

task_uuid = str(uuid.uuid4())
rq_dict = {'Email': "your_email", "UserKey": "your_user_key", "APIKey": "your_api_key", "forigimg": fimg_b64}

res = requests.post("http://api.remo.re.kr/api/analysis-skeleton-v2-front", json=rq_dict)
```
{% endtab %}

{% tab title="javascript" %}
```javascript
import fetch from 'node-fetch';
import fs from 'fs';
import { v4 as uuidv4 } from 'uuid';

const fimg_path = "path/to/your/front/image";

const fimg_b64 = fs.readFileSync(fimg_path, { encoding: 'base64' });

const task_uuid = uuidv4();
const rq_dict = {
  Email: "your_email",
  UserKey: "your_user_key",
  APIKey: "your_api_key",
  forigimg: fimg_b64
};

fetch("http://api.remo.re.kr/api/analysis-skeleton-v2-front", {
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
  'APIName': 'Analysis-skeleton-v2-front',
  'credit_change': -1,
  'credit': 99984228,
  'uuid': '59e9a3a1-a8d2-42a1-b2af-3a87cd01f682',
  'forigimg': 'data:image/jpeg;base64,/9j/4A ... (abbreviated) ... A8x//2Q==',
  'far_coords': '[[431, 258], [432, 403], [360, 432], [301, 595], [246, 720], [505, 434], [566, 598], [621, 723], [370, 675], [387, 953], [392, 1151], [499, 674], [485, 951], [473, 1152], [435, 676], [432, 545], [432, 356], [472, 328], [452, 304], [433, 329], [391, 328], [413, 308]]',
  'far_head_bal_grade': 1,
  'far_head_bal_m_': 1.393,
  'far_knee_bal_grade': 0,
  'far_knee_bal_m_': 0.57,
  'far_left_qang_grade': 0,
  'far_left_qang_m_': -2.529,
  'far_pelvic_bal_grade': 1,
  'far_pelvic_bal_m_': 1.153,
  'far_right_qang_grade': 0,
  'far_right_qang_m_': -4.368,
  'far_shoulder_bal_grade': 0,
  'far_shoulder_bal_m_': 0.483,
  'far_tilt_grade': 0,
  'far_tilt_m_': 0.958,
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
  "message": 'In the front image, the model is not facing side ',
  "status": 515
}
```
{% endtab %}
{% endtabs %}

**Error Code Guide**

| Main Category    | Sub-Category                                 | Code |
| ---------------- | -------------------------------------------- | ---- |
| Input Data Issue | Protocol Error                               | 400  |
|                  | No Input Data                                | 411  |
|                  | Attached Image Error                         | 412  |
|                  | Attached Image Error (Front)                 | 413  |
|                  | Photo is tilted more than 10 degrees (Front) | 418  |
| Other Issues     | User Not Verified                            | 420  |
|                  | Incorrect APIKey                             | 421  |
|                  | Insufficient Credit                          | 422  |
| Analysis Issues  | Person Not Detected in Front Photo           | 511  |
|                  | Incorrect Angle in Front Photo               | 514  |
|                  | Front Image Not in A-pose                    | 517  |
| Process Errors   | Process Handling Error                       | 550  |
|                  | Other Process Handling Error                 | 559  |

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

fimg_path = "path/to/your/front/image"

with open(fimg_path, "rb") as img_file:
    fimg_b64 = base64.b64encode(img_file.read()).decode('utf-8')

task_uuid = str(uuid.uuid4())
rq_dict = {'Email': "your_email", "UserKey": "your_user_key", "APIKey": "your_api_key", 'uuid': task_uuid, "forigimg": fimg_b64}
res = requests.post("http://api.remo.re.kr/api/analysis-skeleton-v2-front", json=rq_dict).json()

fimg_b64 = res["forigimg"] 
f_bytes = base64.b64decode(split_b64_video(fimg_b64).encode('utf-8'))
front_nparr = np.frombuffer(f_bytes, np.uint8)
front_img = cv2.imdecode(front_nparr, cv2.IMREAD_COLOR)

cv2.imshow('front_img', front_img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
{% endtab %}
{% endtabs %}

**Result Image**

<figure><img src="../.gitbook/assets/image (7).png" alt="" width="375"><figcaption><p>forigimg</p></figcaption></figure>
