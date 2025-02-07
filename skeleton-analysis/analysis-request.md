---
description: API for analyzing the skeleton of subjects in images.
---

# Request Skeleton Analysis

### Request Skeleton Analysis

<mark style="color:green;">`POST`</mark> `http://api.remo.re.kr/api/analysis-skeleton`

Analyzes body skeleton by receiving front and side photos.

**Parameters(json)**

| Name | Type | Description | Required |
|------|------|-------------|-----------|
| `Email` | string | User email address | true |
| `UserKey` | string | Issued user key value | true |
| `APIKey` | string | Issued API key value | true |
| `forigimg` | string(base64) | Base64 encoded front photo | true |
| `sorigimg` | string(base64) | Base64 encoded side photo | true |

**Response(json)**

*Left and right are based on the subject in the photo

| Name | Type | Description |
|------|------|-------------|
| `state` | bool | True for success, False for failure |
| `status_code` | int | 200 for success, error code for failure |
| `uuid` | string | UUID received as parameter |
| `credit_change` | int | Number of credits used in analysis |
| `credit` | int | Current credit balance |
| `forigimg` | string | Front photo with results drawn, base64 encoded |
| `sorigimg` | string | Side photo with results drawn, base64 encoded |
| `far_coords` | string | Front view 2D skeleton coordinates converted to JSON string |
| `far_head_bal_m_` | float | Head balance (head tilt). In degrees. |
| `far_head_bal_grade` | int | Head balance (head tilt) grade:<br>-2: Dangerous tilt to right (value<=-4)<br>-1: Warning tilt to right (-4<value<=-1)<br>0: Normal (-1<value<1)<br>1: Warning tilt to left (1<=value<4)<br>2: Dangerous tilt to left (value>=4) |
| `far_pelvic_bal_m_` | float | Pelvic balance (pelvic tilt). In degrees. |
| `far_pelvic_bal_grade` | int | Pelvic balance (pelvic tilt) grade:<br>-2: Dangerous tilt to right (value<=-4)<br>-1: Warning tilt to right (-4<value<=-1)<br>0: Normal (-1<value<1)<br>1: Warning tilt to left (1<=value<4)<br>2: Dangerous tilt to left (value>=4) |
| `far_shoulder_bal_m_` | float | Shoulder balance (shoulder tilt). In degrees. |
| `far_shoulder_bal_grade` | int | Shoulder balance (shoulder tilt) grade:<br>-2: Dangerous tilt to right (value<=-4)<br>-1: Warning tilt to right (-4<value<=-1)<br>0: Normal (-1<value<1)<br>1: Warning tilt to left (1<=value<4)<br>2: Dangerous tilt to left (value>=4) |
| `far_left_qang_m_` | float | Left bowleg value. In degrees. |
| `far_left_qang_grade` | int | Left bowleg evaluation:<br>-2: Severe knock knees (value<=-12)<br>-1: Mild knock knees (-12<value<=-6)<br>0: Normal (-6<value<6)<br>1: Mild bowlegs (6<=value<12)<br>2: Severe bowlegs (value>=12) |
| `far_right_qang_m_` | float | Right bowleg value. In degrees. |
| `far_right_qang_grade` | int | Right bowleg evaluation:<br>-2: Severe knock knees (value<=-12)<br>-1: Mild knock knees (-12<value<=-6)<br>0: Normal (-6<value<6)<br>1: Mild bowlegs (6<=value<12)<br>2: Severe bowlegs (value>=12) |
| `far_knee_bal_m_` | float | Knee balance (knee tilt). In degrees. |
| `far_knee_bal_grade` | int | Knee balance (knee tilt) evaluation:<br>-2: Dangerous tilt to right (value<=-4)<br>-1: Warning tilt to right (-4<value<=-1)<br>0: Normal (-1<value<1)<br>1: Warning tilt to left (1<=value<4)<br>2: Dangerous tilt to left (value>=4) |
| `far_tilt_m_` | float | Front axis tilt (lateral tilt). In degrees. |
| `far_tilt_grade` | int | Front axis tilt (lateral tilt) evaluation:<br>-2: Dangerous tilt to right (value<=-4)<br>-1: Warning tilt to right (-4<value<=-1)<br>0: Normal (-1<value<1)<br>1: Warning tilt to left (1<=value<4)<br>2: Dangerous tilt to left (value>=4) |
| `round_shoulder_m_` | float | Rounded shoulder tilt. In degrees. |
| `round_shoulder_grade` | int | Rounded shoulder evaluation:<br>0: Normal (value<=8)<br>1: Warning (8<value<15)<br>2: Danger (value>=15) |
| `sar_coords` | string | Side view 2D skeleton coordinates converted to JSON string |
| `sar_head_tilt_grade` | int | Side head balance (side head tilt) evaluation:<br>-2: Dangerous backward tilt (value<=-4)<br>-1: Warning backward tilt (-4<value<=-1)<br>0: Normal (-1<value<1)<br>1: Warning forward tilt (1<=value<4)<br>2: Dangerous forward tilt (value>=4) |
| `sar_head_tilt_m_` | float | Side head balance (head forward/backward tilt). In degrees. |
| `sar_tilt_m_` | float | Side tilt (whole body forward/backward tilt). In degrees. |
| `sar_tilt_grade` | int | Side tilt (whole body forward/backward tilt) evaluation:<br>-2: Dangerous backward tilt (value<=-4)<br>-1: Warning backward tilt (-4<value<=-1)<br>0: Normal (-1<value<1)<br>1: Warning forward tilt (1<=value<4)<br>2: Dangerous forward tilt (value>=4) |
| `turtle_neck_m_` | float | Forward head posture tilt. In degrees. |
| `turtle_neck_grade` | int | Forward head posture evaluation:<br>0: Normal (value<=34)<br>1: Warning (34<value<40)<br>2: Danger (value>=40) |

[Rest of the document includes example requests, responses, error codes, and image viewing code, which I'll continue in the next part due to length...]