# assets/

### Definition:
An individual piece of media contributed by a user or by project administrators. Roundware currently handles audio, photo and text assets.

## GET assets/

```python
import requests

url = "http://localhost:8888/api/2/assets/"

querystring = {"session_id":"1","project_id":"1","tag_ids":"3,4,5","media_type":"audio","language":"en"}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/assets/?session_id=1&project_id=1&tag_ids=3,4,5&media_type=audio&language=en' \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/assets/?session_id=1&project_id=1&tag_ids=3,4,5&media_type=audio&language=en",
  "method": "GET",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
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
    "id": 1,
    "description": "",
    "latitude": 1,
    "longitude": 1,
    "filename": "rw_test_audio1.wav",
    "file": null,
    "volume": 1,
    "submitted": true,
    "created": "2012-07-24T18:06:40",
    "weight": 50,
    "loc_caption": null,
    "project": 1,
    "language": "en",
    "loc_description": [],
    "loc_alt_text": [],
    "media_type": "audio",
    "audio_length_in_seconds": 30,
    "tag_ids": [8,3,5],
    "session_id": 1
  },
  {
    "id": 2,
    "description": "",
    "latitude": 1,
    "longitude": 1,
    "filename": "20170415-163557-1.wav",
    "file": "/rwmedia/20170415-163557-1.wav",
    "volume": 1,
    "submitted": true,
    "created": "2017-04-15T16:35:57.616822",
    "weight": 50,
    "loc_caption": null,
    "project": 1,
    "language": "en",
    "loc_description": [],
    "loc_alt_text": [],
    "media_type": "audio",
    "audio_length_in_seconds": 24.81,
    "tag_ids": [3,8],
    "session_id": 1
  }
]
```

Get list of Assets.

### HTTP Request

`GET localhost:8888/api/2/assets/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
session_id | integer |
project_id | integer |
tag_ids | comma separated list |
media_type | string | audio, photo, text, video
language | string | 2-character language shortcode
envelope_id | integer |
longitude | double |
latitude | double |
submitted | boolean | determines whether or not asset will be available to streams etc
audiolength__lte | double | in seconds
audiolength__gte | double | in seconds
created__lte | datetime |
created__gte | datetime |

<aside class="success">
Note — Adding GET param <code>admin=1</code> to this request will provide all localized strings in response, not only English.
</aside>


## GET assets/:id/

```python
import requests

url = "http://localhost:8888/api/2/assets/1/"

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/assets/1/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/assets/1/",
  "method": "GET",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
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
  "description": "",
  "latitude": 1,
  "longitude": 1,
  "filename": "rw_test_audio1.wav",
  "file": null,
  "volume": 1,
  "submitted": true,
  "created": "2012-07-24T18:06:40",
  "weight": 50,
  "loc_caption": null,
  "project": 1,
  "language": "en",
  "loc_description": [],
  "loc_alt_text": [],
  "media_type": "audio",
  "audio_length_in_seconds": 30,
  "tag_ids": [8,3,5],
  "session_id": 1
}
```

Get specific Asset.

### HTTP Request

`GET localhost:8888/api/2/assets/1/`

## POST assets/

```python
import requests

url = "http://localhost:8888/api/2/assets/"

payload = ""
headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url http://localhost:8888/api/2/assets/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
```

```javascript
var form = new FormData();

var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/assets/",
  "method": "POST",
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
  "id": 1,
  "description": "",
  "latitude": 1,
  "longitude": 1,
  "filename": "rw_test_audio1.wav",
  "file": null,
  "volume": 1,
  "submitted": true,
  "created": "2012-07-24T18:06:40",
  "weight": 50,
  "loc_caption": null,
  "project": 1,
  "language": "en",
  "loc_description": [47,48],
  "loc_alt_text": [49,50],
  "media_type": "audio",
  "audio_length_in_seconds": 30,
  "tag_ids": [8,3,5],
  "session_id": 1
}
```

Create new Asset.

If asset_id param is set, replace existing asset.

<aside class="warning">
Currently not functioning; <code>PATCH envelopes/</code> works to add asset though.
</aside>

### HTTP Request

`POST localhost:8888/api/2/assets/`

### Required Parameters

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
session_id | integer (required) | 1 |
file | mp3, wav, jpeg, png, txt |  | basic mimetype checking done by server on upload
mediatype | audio, photo, text, video | audio | defaults to audio


### Optional Parameters

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
asset_id | integer | 1 | only required to replace existing asset
description | string | this is a transcript of the audio or other useful info |
latitude | double | 1.12345 | defaults to project latitude
longitude | double | 2.34567 | defaults to project longitude
submitted | boolean | true | defaults to `project.auto_submit` value

## GET assets/:id/votes/

```python
import requests

url = "http://localhost:8888/api/2/assets/1/votes/"

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/assets/1/votes/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/assets/1/votes/",
  "method": "GET",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
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
    "total": 1,
    "type": "rate",
    "avg": 5
  },
  {
    "total": 2,
    "type": "like"
  }
]
```

Get Votes associated with specific Asset, subtotaled by `vote.vote_type`.

### HTTP Request

`GET localhost:8888/api/2/assets/:id/votes/`

## POST assets/:id/votes/

```python
import requests

url = "http://localhost:8888/api/2/assets/1/votes/"

payload = '{"session_id": 1, "vote_type": "rate", "value": 5}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url http://localhost:8888/api/2/assets/1/votes/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "voter_id": 1,
  "session_id": 1,
  "vote_type": "rate",
  "value": 5
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/assets/1/votes/",
  "method": "POST",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"session_id": 1, "vote_type": "rate", "value": 5}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 8,
  "value": 5,
  "type": "rate",
  "voter_id": null,
  "asset_id": 1,
  "session_id": 1,
  "asset_votes": [
    {
      "total": 1,
      "type": "rate",
      "avg": 5
    },
    {
      "total": 2,
      "type": "like"
    }
  ]
}
```

Register Vote on specific Asset.

### HTTP Request

`POST localhost:8888/api/2/assets/:id/votes/`

### Required Parameters
Data format: `application/json`

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
session_id | integer | 1 | must exist
vote_type | string | like | OPTIONS: like, flag, rate, block_asset, block_user

### Optional Parameters

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
value | integer | 4 | mainly applies to `vote_type = rate` currently


## GET assets/random/

```python
import requests

url = "http://localhost:8888/api/2/assets/random/"

querystring = {"limit":"2", "project_id":"1", "submitted":"true", "media_type":"audio", "audiolength__lte":"30", "audiolength__gte":"10"}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/assets/?limit=2&mediatype=audio&submitted=true&project_id=1&audiolength__lte=30&audiolength__gte=15' \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/assets/?limit=2&mediatype=audio&submitted=true&project_id=1&audiolength__lte=30&audiolength__gte=15",
  "method": "GET",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
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
        "id": 7786,
        "description": "waldman-66",
        "latitude": 42.3746271119689,
        "longitude": -71.1146264076236,
        "filename": "20150502-163007.wav",
        "file": "/rwmedia/20150502-163007.wav",
        "volume": 1,
        "submitted": true,
        "created": "2015-05-02T16:30:08",
        "weight": 50,
        "loc_caption": null,
        "project": 19,
        "language": "en",
        "loc_description": [],
        "loc_alt_text": [],
        "media_type": "audio",
        "audio_length_in_seconds": 15.16,
        "tag_ids": [
            222,
            226
        ],
        "session_id": -10
    },
    {
        "id": 8107,
        "description": "",
        "latitude": 42.37447,
        "longitude": -71.116654,
        "filename": "20151026-225822.wav",
        "file": "/rwmedia/20151026-225822.m4a",
        "volume": 1,
        "submitted": true,
        "created": "2015-10-26T22:58:22",
        "weight": 50,
        "loc_caption": null,
        "project": 19,
        "language": "en",
        "loc_description": [],
        "loc_alt_text": [],
        "media_type": "audio",
        "audio_length_in_seconds": 19.48,
        "tag_ids": [
            219
        ],
        "session_id": 23111
    }
]
```

Get random list of Assets.

### HTTP Request

`GET localhost:8888/api/2/assets/random/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
limit | integer | how many Assets included in response?
project_id | integer |
media_type | string | audio, photo, text, video
submitted | boolean |
audiolength__lte | double | in seconds
audiolength__gte | double | in seconds
