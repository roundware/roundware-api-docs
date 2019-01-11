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
    "shape": {
        "type": "MultiPolygon",
        "coordinates": [[[[0,0], [0,1], [1,1], [1,0], [0,0]]]]
    },
    "filename": "rw_test_audio1.wav",
    "file": null,
    "volume": 1,
    "submitted": true,
    "created": "2012-07-24T18:06:40",
    "weight": 50,
    "project_id": 1,
    "language_id": 1,
    "description_loc_ids": [],
    "alt_text_loc_ids": [],
    "media_type": "audio",
    "audio_length_in_seconds": 30,
    "tag_ids": [8,3,5],
    "session_id": 1,
    "envelope_ids": [1]
  },
  {
    "id": 2,
    "description": "",
    "latitude": 1,
    "longitude": 1,
    "shape": null,
    "filename": "20170415-163557-1.wav",
    "file": "/rwmedia/20170415-163557-1.wav",
    "volume": 1,
    "submitted": true,
    "created": "2017-04-15T16:35:57.616822",
    "weight": 50,
    "project_id": 1,
    "language_id": 1,
    "description_loc_ids": [],
    "alt_text_loc_ids": [],
    "media_type": "audio",
    "audio_length_in_seconds": 24.81,
    "tag_ids": [3,8],
    "session_id": 1,
    "envelope_ids": [2]
  }
]
```

Get list of Assets.

### HTTP Request

`GET localhost:8888/api/2/assets/`

### Optional Filters

Parameter       | Format                | Description/Notes
--------------- | --------------------- | -----------------
session_id      | integer               |
project_id      | integer               |
tag_ids         | comma separated list  |
media_type      | string                | audio, photo, text, video
language        | string                | 2-character language shortcode
envelope        | integer               |
longitude       | double                |
latitude        | double                |
submitted       | boolean               | determines whether or not asset will be available to streams etc
audiolength__lte| double                | in seconds
audiolength__gte| double                | in seconds
created__lte    | datetime              |
created__gte    | datetime              |

### Optional Ordering Parameters

Adding the `ordering` parameter to the request will order the returned results by the specified field either ascending or descending.

Value       | Sample                    | Description
---------   | ------------------------- | ----------------------------
id          | `ordering=id`             | ascending by `id`
session_id  | `ordering=session_id`     | ascending by `session_id`
audiolength | `ordering=audiolength`    | ascending by `audiolength`
weight      | `ordering=-weight`        | descending by `weight`
volume      | `ordering=-volume`        | descending by `volume`

<aside class="success">
Note — Adding GET param <code>admin=1</code> to this request will provide all localized strings in response, not only English.
</aside>


## GET assets/?paginate=True

```python
import requests

url = "http://localhost:8888/api/2/assets/"

querystring = {"project_id":"1","media_type":"audio","language":"en","paginate":"True","page_size":2}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/assets/?project_id=1&media_type=audio&language=en&paginate=True&page_size=2' \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/assets/?project_id=1&media_type=audio&language=en&paginate=True&page_size=2",
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
    "count": 20,
    "next": "http://localhost:8888/api/2/assets/?page=2&page_size=2&paginate=True&project_id=1",
    "previous": null,
    "results":
        [
          {
            "id": 1,
            "description": "",
            "latitude": 1,
            "longitude": 1,
            "shape": {
                "type": "MultiPolygon",
                "coordinates": [[[[0,0], [0,1], [1,1], [1,0], [0,0]]]]
            },
            "filename": "rw_test_audio1.wav",
            "file": null,
            "volume": 1,
            "submitted": true,
            "created": "2012-07-24T18:06:40",
            "weight": 50,
            "project_id": 1,
            "language_id": 1,
            "description_loc_ids": [],
            "alt_text_loc_ids": [],
            "media_type": "audio",
            "audio_length_in_seconds": 30,
            "tag_ids": [8,3,5],
            "session_id": 1,
            "envelope_ids": [1]
          },
          {
            "id": 2,
            "description": "",
            "latitude": 1,
            "longitude": 1,
            "shape": null,
            "filename": "20170415-163557-1.wav",
            "file": "/rwmedia/20170415-163557-1.wav",
            "volume": 1,
            "submitted": true,
            "created": "2017-04-15T16:35:57.616822",
            "weight": 50,
            "project_id": 1,
            "language_id": 1,
            "description_loc_ids": [],
            "alt_text_loc_ids": [],
            "media_type": "audio",
            "audio_length_in_seconds": 24.81,
            "tag_ids": [3,8],
            "session_id": 1,
            "envelope_ids": [2]
          }
        ]
}
```

Get paginated list of Assets.
Same filters and ordering as above apply.

### HTTP Request

`GET localhost:8888/api/2/assets/?paginate=True`

### Optional Parameters

Parameter | Format              | Description/Notes
--------- | ------------------- | -----------------
paginate  | integer or string   | True, 1, true all work; default is False
page_size | integer             | sets number of results per page


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
  "shape": {
      "type": "MultiPolygon",
      "coordinates": [[[[0,0], [0,1], [1,1], [1,0], [0,0]]]]
  },
  "filename": "rw_test_audio1.wav",
  "file": null,
  "volume": 1,
  "submitted": true,
  "created": "2012-07-24T18:06:40",
  "weight": 50,
  "project_id": 1,
  "language_id": 1,
  "description_loc_ids": [],
  "alt_text_loc_ids": [],
  "media_type": "audio",
  "audio_length_in_seconds": 30,
  "tag_ids": [8,3,5],
  "session_id": 1,
  "envelope_ids": [1]
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
  "shape": {
      "type": "MultiPolygon",
      "coordinates": [[[[0,0], [0,1], [1,1], [1,0], [0,0]]]]
  },
  "filename": "rw_test_audio1.wav",
  "file": "/rwmedia/rw_test_audio1.wav",
  "volume": 1,
  "submitted": true,
  "created": "2012-07-24T18:06:40",
  "weight": 50,
  "project_id": 1,
  "language_id": 1,
  "description_loc_ids": [47,48],
  "alt_text_loc_ids": [49,50],
  "media_type": "audio",
  "audio_length_in_seconds": 30,
  "tag_ids": [8,3,5],
  "session_id": 1,
  "envelope_ids": [1]
}
```

Create new Asset.

Asset must be added to pre-existing Envelope.

### HTTP Request

`POST localhost:8888/api/2/assets/`

### Required Parameters

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
envelope_id | integer | 1 |
file | mp3, wav, jpeg, png, txt |  | basic mimetype checking done by server on upload
media_type | audio, photo, text, video | audio | defaults to audio

### Optional Parameters

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
description | string | this is a transcript of the audio or other useful info |
latitude | double | 1.12345 | defaults to project latitude
longitude | double | 2.34567 | defaults to project longitude
submitted | boolean | true | defaults to `project.auto_submit` value
tag_ids | comma-separated list | 3,4 |
volume | float | 1.234 | default = 1.0
weight | integer | 34 | must be between 0-99; default = 50
description_loc_ids | comma-separated list | 6,7 | ids of localized strings
alt_text_loc_ids comma-separated list | 9,10 | ids of localized strings


## PATCH assets/:id/

```python
import requests

url = "http://localhost:8888/api/2/assets/24/"

payload = "{"latitude": 2.789,"longitude": 2.1,"tag_ids": [3,4,5],"submitted": false,"description": "","description_loc_ids": [5,7],"alt_text_loc_ids": [7,9],"volume": 0.543,"weight": 89,"language_id": 1,"project_id": 1}"
headers = {
    'authorization': "token aed40ccd8bbc291bf04ccea20627cd8f83eee9ca",
    'content-type': "application/json"
    }

response = requests.request("PATCH", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request PATCH \
  --url 'http://localhost:8888/api/2/assets/24/' \
  --header 'authorization: token aed40ccd8bbc291bf04ccea20627cd8f83eee9ca' \
  --header 'content-type: application/json' \
  --data '{
	  "latitude": 2.789,
	  "longitude": 2.1,
    "tag_ids": [3,4,5],
    "submitted": false,
    "description": "",
    "description_loc_ids": [5,7],
    "alt_text_loc_ids": [7,9],
    "volume": 0.543,
    "weight": 89,
    "language_id": 1,
    "project_id": 1
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/assets/24/",
  "method": "PATCH",
  "headers": {
    "authorization": "token aed40ccd8bbc291bf04ccea20627cd8f83eee9ca",
    "content-type": "application/json"
  },
  "processData": false,
  "data": "{"latitude": 2.789,"longitude": 2.1,"tag_ids": [3,4,5],"submitted": false,"description": "","description_loc_ids": [5,7],"alt_text_loc_ids": [7,9],"volume": 0.543,"weight": 89,"language_id": 1,"project_id": 1}"
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
  "latitude": 2.789,
  "longitude": 2.1,
  "shape": {
      "type": "MultiPolygon",
      "coordinates": [[[[0,0], [0,1], [1,1], [1,0], [0,0]]]]
  },
  "filename": "rw_test_audio1.wav",
  "file": "/rwmedia/rw_test_audio1.wav",
  "volume": 1,
  "submitted": false,
  "created": "2012-07-24T18:06:40",
  "weight": 50,
  "caption_loc_ids": null,
  "project_id": 1,
  "language_id": 1,
  "description_loc_ids": [5,7],
  "alt_text_loc_ids": [7,9],
  "media_type": "audio",
  "audio_length_in_seconds": 30,
  "tag_ids": [3,4,5],
  "session_id": 1,
  "envelope_ids": [1]
}
```

Update Asset.

Not all fields are available for update for various reasons.

### HTTP Request

`PATCH localhost:8888/api/2/assets/:id/`

### Optional Parameters
Data format: `application/json`

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
latitude | double | 1.12345 | defaults to project latitude
longitude | double | 2.34567 | defaults to project longitude
submitted | boolean | true | defaults to `project.auto_submit` value
tag_ids | array of integers | [1,2,3] |
volume | float | 1.45 |
weight | integer | 80 | range: 0-99
language_id | integer | 2 |
project_id | integer | 1 |
description | string | this is a transcript of the audio or other useful info |
description_loc_ids | array of integers | [10,21] |
alt_text_loc_ids | array of integers | [32,2] |


## DELETE assets/:id/

```python
import requests

url = "http://localhost:8888/api/2/assets/5/"

payload = ""
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
    }

response = requests.request("DELETE", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request DELETE \
  --url http://localhost:8888/api/2/assets/5/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/assets/5/",
  "method": "DELETE",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
  },
  "processData": false,
  "data": ""
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Returns 204 No Content if successful

Delete Asset

### HTTP Request

`DELETE localhost:8888/api/2/assets/:id/`


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
        "shape": null,
        "filename": "20150502-163007.wav",
        "file": "/rwmedia/20150502-163007.wav",
        "volume": 1,
        "submitted": true,
        "created": "2015-05-02T16:30:08",
        "weight": 50,
        "caption_loc_ids": null,
        "project_id": 19,
        "language_id": 1,
        "description_loc_ids": [],
        "alt_text_loc_ids": [],
        "media_type": "audio",
        "audio_length_in_seconds": 15.16,
        "tag_ids": [
            222,
            226
        ],
        "session_id": -10,
        "envelope_ids": [1]
    },
    {
        "id": 8107,
        "description": "",
        "latitude": 42.37447,
        "longitude": -71.116654,
        "shape": null,
        "filename": "20151026-225822.wav",
        "file": "/rwmedia/20151026-225822.m4a",
        "volume": 1,
        "submitted": true,
        "created": "2015-10-26T22:58:22",
        "weight": 50,
        "caption_loc_ids": null,
        "project_id": 19,
        "language_id": 1,
        "description_loc_ids": [],
        "alt_text_loc_ids": [],
        "media_type": "audio",
        "audio_length_in_seconds": 19.48,
        "tag_ids": [
            219
        ],
        "session_id": 23111,
        "envelope_ids": [2]
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
