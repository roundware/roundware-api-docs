# projects/

### Definition:
The highest level of segmentation/grouping for all RW data. One RW instance can run many projects simultaneously, governed by CPU, bandwidth and memory resources.

## GET projects/

```python
import requests

url = "http:///localhost:8888/api/2/projects/"

querystring = {"name":"test","listen_enabled":"true","geo_listen_enabled":"true"}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/projects/?name=test&listen_enabled=true&geo_listen_enabled=true' \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/projects/?name=test&listen_enabled=true&geo_listen_enabled=true",
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
    "name": "Test Project",
    "latitude": 1,
    "longitude": 1,
    "pub_date": "2011-12-06T16:06:32",
    "audio_format": "mp3",
    "auto_submit": true,
    "max_recording_length": 30,
    "listen_questions_dynamic": false,
    "speak_questions_dynamic": false,
    "sharing_url": "http://roundware.org/r/eid=[id]",
    "out_of_range_url": "http://scapesaudio.dyndns.org:8000/mg_outofrange.mp3",
    "recording_radius": 200000,
    "listen_enabled": true,
    "geo_listen_enabled": true,
    "speak_enabled": true,
    "geo_speak_enabled": true,
    "reset_tag_defaults_on_startup": true,
    "timed_asset_priority": true,
    "repeat_mode": "stop",
    "files_url": "http://halseyburgund.com/dev/rw-base/webview/rw.zip",
    "files_version": "1",
    "audio_stream_bitrate": "128",
    "ordering": "random",
    "demo_stream_enabled": false,
    "demo_stream_url": "http://scapesaudio.dyndns.org:8000/scapes1.mp3",
    "out_of_range_distance": 10000,
    "sharing_message": "Check out this awesome recording I made using Roundware!",
    "out_of_range_message": "You are out of range of this Roundware project.  Please go somewhere within range and try again.  Thank you.",
    "legal_agreement": "Herein should be the brief legal agreement that participants need to agree to in order to make and submit a recording to a Roundware project.",
    "demo_stream_message": "You are out of range of this Roundware project.  Please go somewhere within range and try again.  Thank you.",
    "language_ids": [1]
  }
]
```

Get list of Projects.

### HTTP Request

`GET localhost:8888/api/2/projects/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
name | string | contains, case-insensitive
listen_enabled | boolean | can the Project generate audio streams?
geo_listen_enabled | boolean | is the audio stream filtered by location?
speak_enabled | boolean | can the Project capture Assets from users?
geo_speak_enabled | boolean | do Assets uploaded by users have a location?


## GET projects/:id/

```python
import requests

url = "http://localhost:8888/api/2/projects/1/"

querystring = {"session_id": "1"}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/projects/1/?session_id=1 \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/projects/1/?session_id=1",
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
  "name": "Test Project",
  "latitude": 1,
  "longitude": 1,
  "pub_date": "2011-12-06T16:06:32",
  "audio_format": "mp3",
  "auto_submit": true,
  "max_recording_length": 30,
  "listen_questions_dynamic": false,
  "speak_questions_dynamic": false,
  "sharing_url": "http://roundware.org/r/eid=[id]",
  "out_of_range_url": "http://scapesaudio.dyndns.org:8000/mg_outofrange.mp3",
  "recording_radius": 200000,
  "listen_enabled": true,
  "geo_listen_enabled": true,
  "speak_enabled": true,
  "geo_speak_enabled": true,
  "reset_tag_defaults_on_startup": true,
  "timed_asset_priority": true,
  "repeat_mode": "stop",
  "files_url": "http://halseyburgund.com/dev/rw-base/webview/rw.zip",
  "files_version": "1",
  "audio_stream_bitrate": "128",
  "ordering": "random",
  "demo_stream_enabled": false,
  "demo_stream_url": "http://scapesaudio.dyndns.org:8000/scapes1.mp3",
  "out_of_range_distance": 10000,
  "sharing_message": "Check out this awesome recording I made using Roundware!",
  "out_of_range_message": "You are out of range of this Roundware project. Please go somewhere within range and try again. Thank you.",
  "legal_agreement": "Herein should be the brief legal agreement that participants need to agree to in order to make and submit a recording to a Roundware project.",
  "demo_stream_message": "You are out of range of this Roundware project. Please go somewhere within range and try again.  Thank you.",
  "language_ids": [1]
}
```

Get specific Project.

### HTTP Request

`GET localhost:8888/api/2/projects/1/?session_id=1`

### Required Parameters

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
session_id | integer | 1 | this parameter is required to provide localization in theory, but not working currently

<aside class="success">
Note — Adding GET param <code>admin=1</code> to this request will provide all localized strings in response, not only English.
</aside>

## GET projects/:id/assets/

```python
import requests

url = "http://localhost:8888/api/2/projects/1/assets/"

querystring = {"session_id":"1","submitted":"true"}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/projects/1/assets/?session_id=1&submitted=true \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/projects/1/assets/?session_id=1&submitted=true",
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
    "loc_description": [47],
    "loc_alt_text": [],
    "media_type": "audio",
    "audio_length_in_seconds": 24.81,
    "tag_ids": [3,8],
    "session_id": 1
  }
]
```

Get Assets associated with specific Project.

### HTTP Request

`GET localhost:8888/api/2/projects/1/assets/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
session_id | integer |
tag_ids | list of integers |
media_type | string | OPTIONS: audio, photo, text, video
language | string | 2-character language code
envelope_id | integer |
latitude | float |
longitude | float |
submitted | boolean |
audiolength__lte | float | in seconds less than or equal
audiolength__gte | float | in seconds greater than or equal
created__lte | datetime |
created__gte | datetime |


## GET projects/:id/tags/

```python
import requests

url = "http://localhost:8888/api/2/projects/1/tags/"

querystring = {"description":"male"}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/projects/1/tags/?description=male \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/projects/1/tags/?description=male",
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
  "tags": [
    {
      "id": 3,
      "value": "male",
      "description": "male",
      "data": "class=tag-one",
      "filter": "",
      "location": null,
      "project_id": 1,
      "tag_category_id": 3,
      "description_loc": null,
      "msg_loc": "male",
      "relationships": [
        {
          "id": 2,
          "tag_id": 3,
          "parent_id": null
        },
        {
          "id": 17,
          "tag_id": 3,
          "parent_id": null
        }
      ]
    },
    {
      "id": 4,
      "value": "female",
      "description": "female",
      "data": "class=tag-one",
      "filter": "",
      "location": null,
      "project_id": 1,
      "tag_category_id": 3,
      "description_loc": null,
      "msg_loc": "female",
      "relationships": [
        {
          "id": 1,
          "tag_id": 4,
          "parent_id": null
        }
      ]
    }
  ]
}
```

Get Tags associated with specific Project.

### HTTP Request

`GET localhost:8888/api/2/projects/1/tags/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
description | string | contains, case-insensitive
data | string | contains, case-insensitive


## GET projects/:id/uigroups/

```python
import requests

url = "http:///localhost:8888/api/2/projects/1/uigroups/"

querystring = {"ui_mode":"listen","active":"true"}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/projects/1/uigroups/?ui_mode=listen&active=true \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/projects/1/uigroups/?ui_mode=listen&active=true",
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
  "ui_groups": [
    {
      "id": 1,
      "name": "What genders do you want to listen to?",
      "ui_mode": "listen",
      "select": "min_one",
      "active": true,
      "index": 1,
      "header_text_loc": "What genders do you want to listen to?",
      "tag_category_id": 3,
      "project_id": 1,
      "ui_items": [
        {
          "id": 1,
          "index": 2,
          "default": true,
          "active": true,
          "ui_group_id": 1,
          "tag_id": 3,
          "parent_id": null
        },
        {
          "id": 2,
          "index": 1,
          "default": true,
          "active": true,
          "ui_group_id": 1,
          "tag_id": 4,
          "parent_id": null
        }
      ]
    },
    {
      "id": 7,
      "name": "Who do you want to hear?",
      "ui_mode": "listen",
      "select": "min_one",
      "active": true,
      "index": 2,
      "header_text_loc": "Who do you want to hear?",
      "tag_category_id": 4,
      "project_id": 1,
      "ui_items": [
        {
          "id": 15,
          "index": 1,
          "default": true,
          "active": true,
          "ui_group_id": 7,
          "tag_id": 8,
          "parent_id": null
        },
        {
          "id": 16,
          "index": 2,
          "default": true,
          "active": true,
          "ui_group_id": 7,
          "tag_id": 9,
          "parent_id": null
        }
      ]
    }
  ]
}
```

Get UIGroups associated with specific Project.

### HTTP Request

`GET localhost:8888/api/2/projects/1/uigroups/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
name | string |
ui_mode | string | OPTIONS: listen, speak, browse
tag_category_id | integer |
select | string | OPTIONS: single, multi, min_one
active | boolean |
index | integer |


## POST projects/

```python
import requests

url = "http://localhost:8888/api/2/projects/"

payload = '{"name":"New Project","latitude": 40,"longitude": -80,"pub_date":"2015-01-01T00:00:00","audio_format":"mp3","auto_submit": true,"max_recording_length": 35,"listen_questions_dynamic": false,"speak_questions_dynamic": false,"sharing_url": "http://roundware.org/r/eid=[id]","out_of_range_url": "http://roundware.dyndns.org:8000/outofrange.mp3","recording_radius": 10,"listen_enabled": true,"geo_listen_enabled": false,"speak_enabled": true,"geo_speak_enabled": true,"reset_tag_defaults_on_startup": false,"timed_asset_priority": false,"repeat_mode": "continuous","files_url": "http://roundware.dyndns.org/rw.zip","files_version": "1","audio_stream_bitrate": "128","ordering": "random","demo_stream_enabled": false,"demo_stream_url": "http://roundware.dyndns.org:8000/stream.mp3","out_of_range_distance": 5000,"language_ids": [1,2],"sharing_message_loc": [49,50],"out_of_range_message_loc": [47,48],"legal_agreement_loc": [53,54],"demo_stream_message_loc": [47,48]}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url http:///localhost:8888/api/2/projects/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "name": "New Project",
  "latitude": 40,
  "longitude": -80,
  "pub_date": "2015-01-01T00:00:00",
  "audio_format": "mp3",
  "auto_submit": true,
  "max_recording_length": 35,
  "listen_questions_dynamic": false,
  "speak_questions_dynamic": false,
  "sharing_url": "http://roundware.org/r/eid=[id]",
  "out_of_range_url": "http://roundware.dyndns.org:8000/mg_outofrange.mp3",
  "recording_radius": 10,
  "listen_enabled": true,
  "geo_listen_enabled": false,
  "speak_enabled": true,
  "geo_speak_enabled": true,
  "reset_tag_defaults_on_startup": false,
  "timed_asset_priority": false,
  "repeat_mode": "continuous",
  "files_url": "http://halseyburgund.com/dev/rw-base/webview/rw.zip",
  "files_version": "1",
  "audio_stream_bitrate": "128",
  "ordering": "random",
  "demo_stream_enabled": false,
  "demo_stream_url": "http://roundware.dyndns.org:8000/scapes1.mp3",
  "out_of_range_distance": 5000,
  "language_ids": [1,2],
  "sharing_message_loc": [49,50],
  "out_of_range_message_loc": [47,48],
  "legal_agreement_loc": [53,54],
  "demo_stream_message_loc": [47,48]
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/projects/",
  "method": "POST",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"name":"New Project","latitude": 40,"longitude": -80,"pub_date":"2015-01-01T00:00:00","audio_format":"mp3","auto_submit": true,"max_recording_length": 35,"listen_questions_dynamic": false,"speak_questions_dynamic": false,"sharing_url": "http://roundware.org/r/eid=[id]","out_of_range_url": "http://roundware.dyndns.org:8000/outofrange.mp3","recording_radius": 10,"listen_enabled": true,"geo_listen_enabled": false,"speak_enabled": true,"geo_speak_enabled": true,"reset_tag_defaults_on_startup": false,"timed_asset_priority": false,"repeat_mode": "continuous","files_url": "http://roundware.dyndns.org/rw.zip","files_version": "1","audio_stream_bitrate": "128","ordering": "random","demo_stream_enabled": false,"demo_stream_url": "http://roundware.dyndns.org:8000/stream.mp3","out_of_range_distance": 5000,"language_ids": [1,2],"sharing_message_loc": [49,50],"out_of_range_message_loc": [47,48],"legal_agreement_loc": [53,54],"demo_stream_message_loc": [47,48]}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 9,
  "name": "New Project",
  "latitude": 40,
  "longitude": -80,
  "pub_date": "2015-01-01T00:00:00",
  "audio_format": "mp3",
  "auto_submit": true,
  "max_recording_length": 35,
  "listen_questions_dynamic": false,
  "speak_questions_dynamic": false,
  "sharing_url": "http://roundware.org/r/eid=[id]",
  "out_of_range_url": "http://roundware.dyndns.org:8000/outofrange.mp3",
  "recording_radius": 10,
  "listen_enabled": true,
  "geo_listen_enabled": false,
  "speak_enabled": true,
  "geo_speak_enabled": true,
  "reset_tag_defaults_on_startup": false,
  "timed_asset_priority": false,
  "repeat_mode": "continuous",
  "files_url": "http://roundware.dyndns.org/rw.zip",
  "files_version": "1",
  "audio_stream_bitrate": "128",
  "ordering": "random",
  "demo_stream_enabled": false,
  "demo_stream_url": "http://roundware.dyndns.org:8000/stream.mp3",
  "out_of_range_distance": 5000,
  "sharing_message": "Check out this awesome recording I made using Roundware!",
  "out_of_range_message": "You are out of range of this Roundware project.  Please go somewhere within range and try again.  Thank you.",
  "legal_agreement": "Herein should be the brief legal agreement that participants need to agree to in order to make and submit a recording to a Roundware project.",
  "demo_stream_message": "You are out of range of this Roundware project.  Please go somewhere within range and try again.  Thank you.",
  "language_ids": [2,1]
}
```

Create new Project.

### HTTP Request

`POST localhost:8888/api/2/projects/`

### Required Parameters
Data format: application/json

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
name | string | New Project |
latitude | float | 1.234 | "central" location for Project
longitude | float | 2.345 | "central" location for Project
pub_date | datetime | 2015-01-01T00:00:00 | auto-generated
audio_format | string | mp3 | always mp3 for now
max_recording_length | integer | 30 | max time users can speak
sharing_url | string | http://roundware.org/sharing.html | url of web sharing page
out_of_range_url | string | http://roundware.org/outofrange.mp3 | default static stream that plays when listener is out of range upon opening client
recording_radius | integer | 5 | radius in meters of active range each Asset in Project will have as default
repeat_mode | string | stop | OPTIONS: continuous, stop
audio_stream_bitrate | varchar | 128 | bitrate of audio streams generated by Project
ordering | string | random | OPTIONS: random, by_like, by_weight
out_of_range_distance | float | 100.5 | distance in meters outside of Project Speaker ranges beyond which listener is considered out of range
language_ids | list of language_ids | 1,2 | Projects can have multiple Languages assigned to them

### Optional Parameters

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
auto_submit | boolean | true | will Project Assets by default be immediately available to streams?
listen_enabled | boolean | true | can the Project generate audio streams?
geo_listen_enabled | boolean | true | is the audio stream filtered by location?
speak_enabled | boolean | true | can the Project capture Assets from users?
geo_speak_enabled | boolean | true | do Assets uploaded by users have a location?
reset_tag_defaults_on_startup | boolean | true |
timed_asset_priority | boolean | true | will timed Assets take priority over location Assets in playlist?
demo_stream_enabled | boolean | false | should Project default all listeners to demo stream?
demo_stream_url | string | http://roundware.org/demo.mp3 |
files_url | string | http://roundware.dyndns.org/rw.zip | zip file containing webview files for iOS and Android clients (to be deprecated)
files_version | integer | 1 |
sharing_message_loc | list of localized_string_ids | 5,6 | default text for sharing message
out_of_range_message_loc | list of localized_string_ids | 7,8 | listener is out of range notification text
legal_agreement_loc | list of localized_string_ids | 9,10 | legal agreement text for contributions
demo_stream_message_loc | list of localized_string_ids | 11,12 | notification text when demo stream is playing instead of dynamic stream
listen_questions_dynamic | boolean | false | not currently used
speak_questions_dynamic | boolean | false | not currently used


## PATCH projects/:id/

```python
import requests

url = "http://localhost:8888/api/2/projects/3/"

payload = '{"name":"Renamed Project"}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("PATCH", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request PATCH \
  --url http://localhost:8888/api/2/projects/3/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{"name":"Renamed Project"}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/projects/3/",
  "method": "PATCH",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"name":"Renamed Project"}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 9,
  "name": "Renamed Project",
  "latitude": 40,
  "longitude": -80,
  "pub_date": "2015-01-01T00:00:00",
  "audio_format": "mp3",
  "auto_submit": true,
  "max_recording_length": 35,
  "listen_questions_dynamic": false,
  "speak_questions_dynamic": false,
  "sharing_url": "http://roundware.org/r/eid=[id]",
  "out_of_range_url": "http://roundware.dyndns.org:8000/outofrange.mp3",
  "recording_radius": 10,
  "listen_enabled": true,
  "geo_listen_enabled": false,
  "speak_enabled": true,
  "geo_speak_enabled": true,
  "reset_tag_defaults_on_startup": false,
  "timed_asset_priority": false,
  "repeat_mode": "continuous",
  "files_url": "http://roundware.dyndns.org/rw.zip",
  "files_version": "1",
  "audio_stream_bitrate": "128",
  "ordering": "random",
  "demo_stream_enabled": false,
  "demo_stream_url": "http://roundware.dyndns.org:8000/stream.mp3",
  "out_of_range_distance": 5000,
  "sharing_message": "Check out this awesome recording I made using Roundware!",
  "out_of_range_message": "You are out of range of this Roundware project.  Please go somewhere within range and try again.  Thank you.",
  "legal_agreement": "Herein should be the brief legal agreement that participants need to agree to in order to make and submit a recording to a Roundware project.",
  "demo_stream_message": "You are out of range of this Roundware project.  Please go somewhere within range and try again.  Thank you.",
  "language_ids": [2,1]
}
```

Update Project.

### HTTP Request

`PATCH localhost:8888/api/2/projects/:id/`

### Optional Parameters
Data format: `application/json`

Partial update allowed; params not included will leave field values unchanged.

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
name | string | New Project |
latitude | float | 1.234 | "central" location for Project
longitude | float | 2.345 | "central" location for Project
pub_date | datetime | 2015-01-01T00:00:00 | auto-generated
audio_format | string | mp3 | always mp3 for now
max_recording_length | integer | 30 | max time users can speak
sharing_url | string | http://roundware.org/sharing.html | url of web sharing page
out_of_range_url | string | http://roundware.org/outofrange.mp3 | default static stream that plays when listener is out of range upon opening client
recording_radius | integer | 5 | radius in meters of active range each Asset in Project will have as default
repeat_mode | string | stop | OPTIONS: continuous, stop
audio_stream_bitrate | varchar | 128 | bitrate of audio streams generated by Project
ordering | string | random | OPTIONS: random, by_like, by_weight
out_of_range_distance | float | 100.5 | distance in meters outside of Project Speaker ranges beyond which listener is considered out of range
language_ids | list of language_ids | 1,2 | Projects can have multiple Languages assigned to them
auto_submit | boolean | true | will Project Assets by default be immediately available to streams?
listen_enabled | boolean | true | can the Project generate audio streams?
geo_listen_enabled | boolean | true | is the audio stream filtered by location?
speak_enabled | boolean | true | can the Project capture Assets from users?
geo_speak_enabled | boolean | true | do Assets uploaded by users have a location?
reset_tag_defaults_on_startup | boolean | true |
timed_asset_priority | boolean | true | will timed Assets take priority over location Assets in playlist?
demo_stream_enabled | boolean | false | should Project default all listeners to demo stream?
demo_stream_url | string | http://roundware.org/demo.mp3 |
files_url | string | http://roundware.dyndns.org/rw.zip | zip file containing webview files for iOS and Android clients (to be deprecated)
files_version | integer | 1 |
sharing_message_loc | list of localized_string_ids | 5,6 | default text for sharing message
out_of_range_message_loc | list of localized_string_ids | 7,8 | listener is out of range notification text
legal_agreement_loc | list of localized_string_ids | 9,10 | legal agreement text for contributions
demo_stream_message_loc | list of localized_string_ids | 11,12 | notification text when demo stream is playing instead of dynamic stream
listen_questions_dynamic | boolean | false | not currently used
speak_questions_dynamic | boolean | false | not currently used


## DELETE projects/:id/

```python
import requests

url = "http://localhost:8888/api/2/projects/3/"

payload = ""
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
    }

response = requests.request("DELETE", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request DELETE \
  --url http://localhost:8888/api/2/projects/3/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/projects/3/",
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

Delete Project

### HTTP Request

`DELETE localhost:8888/api/2/projects/:id/`
