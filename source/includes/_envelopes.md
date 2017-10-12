# envelopes/

### Definition:
A collection of assets submitted by a user/participant. Envelopes can contain multiple assets (several audio recordings, audio and photo, etc) collected at the same time by the same user. This is useful when there is a desire to bundle assets related to the same moment together, such as an audio recording with a photo of what was discussed in the recording.

## GET envelopes/

```python
import requests

url = "http://localhost:8888/api/2/envelopes/"

querystring = {"project_id":"1"}

headers = {'authorization': 'token aed40ccd8bbc291bf04ccea20627cd8f83eee9ca'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/envelopes/?project_id=1' \
  --header 'authorization: token aed40ccd8bbc291bf04ccea20627cd8f83eee9ca'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/envelopes/?project_id=1",
  "method": "GET",
  "headers": {
    "authorization": "token aed40ccd8bbc291bf04ccea20627cd8f83eee9ca"
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
[
    {
        "id": 2,
        "session_id": 3,
        "created": "2017-09-30T22:57:09.446813",
        "asset_ids": [1]
    },
    {
        "id": 1,
        "session_id": 1,
        "created": "2013-01-21T10:36:44",
        "asset_ids": [2, 3, 4, 5]
    }
]
```

Get list of Envelopes.

### HTTP Request

`GET localhost:8888/api/2/envelopes/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
project_id | integer |
session_id | integer |
asset_id | integer |

## GET envelopes/:id/

```python
import requests

url = "http://localhost:8888/api/2/envelopes/1/"

headers = {'authorization': 'token aed40ccd8bbc291bf04ccea20627cd8f83eee9ca'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/envelopes/1/' \
  --header 'authorization: token aed40ccd8bbc291bf04ccea20627cd8f83eee9ca'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/envelopes/1/",
  "method": "GET",
  "headers": {
    "authorization": "token aed40ccd8bbc291bf04ccea20627cd8f83eee9ca"
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
    "id": 1,
    "session_id": 1,
    "created": "2013-01-21T10:36:44",
    "asset_ids": [2, 3, 4, 5]
}
```

Get specific Envelope.

### HTTP Request

`GET localhost:8888/api/2/envelopes/1/`


## POST envelopes/

```python
import requests

url = "http://localhost:8888/api/2/envelopes/"

querystring = {"session_id":"1"}

payload = ""
headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("POST", url, data=payload, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request POST \
  --url http://localhost:8888/api/2/envelopes/ \
  --header 'authorization: token {{token}}' \
  --header 'content-type: application/json' \
  --data '{
  "session_id": 3
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/envelopes/",
  "method": "POST",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"session_id": 3}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "session_id": 3,
  "created": "2017-06-07T13:07:58.247988",
  "asset_ids": [],
  "id": 5
}
```

Create new Envelope.

### HTTP Request

`POST localhost:8888/api/2/envelopes/`

### Required Parameters
Data format: `application/json`

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
session_id | integer | 1 |


## PATCH envelopes/:id/

```python
import requests

url = "http://localhost:8888/api/2/audiotracks/2/"

payload = '{"minvolume": 0.5,"maxvolume": 0.8}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("PATCH", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request PATCH \
  --url http:///localhost:8888/api/2/envelopes/13/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
```

```javascript
var form = new FormData();

var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/envelopes/13/",
  "method": "PATCH",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
  },
  "processData": false,
  "contentType": false,
  "mimeType": "multipart/form-data",
  "data": form
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "description": "",
  "latitude": 1,
  "longitude": 1,
  "shape": null,
  "filename": "20170607-144505-1319.wav",
  "file": "/rwmedia/20170607-144505-1319.wav",
  "volume": 1,
  "submitted": true,
  "created": "2017-06-07T14:45:05.988692",
  "weight": 50,
  "loc_caption": null,
  "project": 2,
  "language": null,
  "loc_description": [],
  "loc_alt_text": [],
  "asset_id": 9991,
  "media_type": "audio",
  "audio_length_in_seconds": 11.76,
  "tag_ids": [3,5,4],
  "session_id": 1319,
  "envelope_ids": [1]
}
```

Update Envelope.

This is the preferred method for adding a new Asset to the system as this adds an Asset to the Envelope and creates the new Asset simultaneously.

`asset.submitted` is set automatically according to the following cascading set of checks:

* is `submitted` parameter passed in request?
    * if YES, `asset.submitted` set to this value
    * if NO, then check if `latitude` and `longitude` parameters are both passed
        * if NO, `asset.submitted False` and `latitude = project.latitude` and `longitude = project.longitude`
        * if YES, then check if location in range of Project
            * if NO, `asset.submitted = False`
            * if YES, `asset.submitted = project.auto_submit`

### HTTP Request

`GET localhost:8888/api/2/envelopes/:id/`

### Optional Parameters
Data format: `application/json`

Partial update allowed; params not included will leave field values unchanged.

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
session_id | integer | 1 |
file | binary |  | new Asset created with file
latitude | double | 1.2345 | assigned to newly created Asset
longitude | double | 2.3456 | assigned to newly created Asset
tag_ids | comma-separated list of integers | 3,4,5 | assigned to newly created Asset
media_type | enum | audio,photo,text,video | default is audio
