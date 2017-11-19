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
    "owner": "Test Company",
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
    "description": "This is a test project description.",
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
  "owner": "Test Company",
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
  "description": "This is a test project description.",
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

<aside class="success">
Note — Adding GET param <code>admin=1</code> to this request will provide all localized strings in response, not only English.
</aside>


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
[
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
```

Get Tags associated with specific Project.

### HTTP Request

`GET localhost:8888/api/2/projects/1/tags/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
description | string | contains, case-insensitive
data | string | contains, case-insensitive

<aside class="success">
Note — Adding GET param <code>admin=1</code> to this request will provide all localized strings in response, not only English.
</aside>


## GET projects/:id/uiconfig/

```python
import requests

url = "http:///localhost:8888/api/2/projects/1/uiconfig/"

querystring = {"session_id": 1}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/projects/1/uiconfig/?session_id=1 \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/projects/1/uiconfig/?session_id=1",
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
    "speak": [
        {
            "select": "single",
            "group_short_name": "Gender",
            "header_display_text": "What gender are you?",
            "display_items": [
                {
                    "id": 8,
                    "tag_id": 3,
                    "parent_id": null,
                    "default_state": false,
                    "tag_display_text": "male"
                },
                {
                    "id": 171,
                    "tag_id": 4,
                    "parent_id": null,
                    "default_state": false,
                    "tag_display_text": "female"
                }
            ]
        },
        {
            "select": "single",
            "group_short_name": "Usertype",
            "header_display_text": "Who are you?",
            "display_items": [
                {
                    "id": 173,
                    "tag_id": 23,
                    "parent_id": 171,
                    "default_state": false,
                    "tag_display_text": "Curator"
                },
                {
                    "id": 143,
                    "tag_id": 9,
                    "parent_id": 8,
                    "default_state": false,
                    "tag_display_text": "Visitor"
                },
                {
                    "id": 172,
                    "tag_id": 9,
                    "parent_id": 171,
                    "default_state": false,
                    "tag_display_text": "Visitor"
                },
                {
                    "id": 142,
                    "tag_id": 8,
                    "parent_id": 8,
                    "default_state": false,
                    "tag_display_text": "Artist"
                },
                {
                    "id": 180,
                    "tag_id": 8,
                    "parent_id": 171,
                    "default_state": false,
                    "tag_display_text": "Artist"
                }
            ]
        },
        {
            "select": "single",
            "group_short_name": "Question",
            "header_display_text": "What do you want to talk about?",
            "display_items": [
                {
                    "id": 178,
                    "tag_id": 26,
                    "parent_id": 172,
                    "default_state": false,
                    "tag_display_text": "Who are you?"
                },
                {
                    "id": 174,
                    "tag_id": 26,
                    "parent_id": 173,
                    "default_state": false,
                    "tag_display_text": "Who are you?"
                },
                {
                    "id": 148,
                    "tag_id": 5,
                    "parent_id": 143,
                    "default_state": false,
                    "tag_display_text": "Why are you using Roundware?"
                },
                {
                    "id": 175,
                    "tag_id": 22,
                    "parent_id": 173,
                    "default_state": false,
                    "tag_display_text": "Respond to something you've heard."
                },
                {
                    "id": 177,
                    "tag_id": 22,
                    "parent_id": 172,
                    "default_state": false,
                    "tag_display_text": "Respond to something you've heard."
                },
                {
                    "id": 152,
                    "tag_id": 22,
                    "parent_id": 142,
                    "default_state": false,
                    "tag_display_text": "Respond to something you've heard."
                },
                {
                    "id": 149,
                    "tag_id": 22,
                    "parent_id": 143,
                    "default_state": false,
                    "tag_display_text": "Respond to something you've heard."
                },
                {
                    "id": 155,
                    "tag_id": 26,
                    "parent_id": 142,
                    "default_state": false,
                    "tag_display_text": "Who are you?"
                },
                {
                    "id": 176,
                    "tag_id": 5,
                    "parent_id": 173,
                    "default_state": false,
                    "tag_display_text": "Why are you using Roundware?"
                },
                {
                    "id": 179,
                    "tag_id": 5,
                    "parent_id": 172,
                    "default_state": false,
                    "tag_display_text": "Why are you using Roundware?"
                }
            ]
        }
    ],
    "listen": [
        {
            "select": "min_one",
            "group_short_name": "Gender",
            "header_display_text": "What genders do you want to listen to?",
            "display_items": [
                {
                    "id": 79,
                    "tag_id": 3,
                    "parent_id": null,
                    "default_state": true,
                    "tag_display_text": "male"
                },
                {
                    "id": 164,
                    "tag_id": 4,
                    "parent_id": null,
                    "default_state": false,
                    "tag_display_text": "female"
                }
            ]
        },
        {
            "select": "min_one",
            "group_short_name": "Usertype",
            "header_display_text": "Who do you want to hear?",
            "display_items": [
                {
                    "id": 165,
                    "tag_id": 23,
                    "parent_id": null,
                    "default_state": false,
                    "tag_display_text": "Curator"
                },
                {
                    "id": 166,
                    "tag_id": 9,
                    "parent_id": null,
                    "default_state": false,
                    "tag_display_text": "Visitor"
                },
                {
                    "id": 167,
                    "tag_id": 8,
                    "parent_id": null,
                    "default_state": false,
                    "tag_display_text": "Artist"
                }
            ]
        },
        {
            "select": "min_one",
            "group_short_name": "Question",
            "header_display_text": "What do you want to listen to?",
            "display_items": [
                {
                    "id": 168,
                    "tag_id": 26,
                    "parent_id": null,
                    "default_state": false,
                    "tag_display_text": "Who are you?"
                },
                {
                    "id": 169,
                    "tag_id": 5,
                    "parent_id": null,
                    "default_state": false,
                    "tag_display_text": "Why are you using Roundware?"
                },
                {
                    "id": 170,
                    "tag_id": 22,
                    "parent_id": null,
                    "default_state": false,
                    "tag_display_text": "Respond to something you've heard."
                }
            ]
        }
    ]
}
```

This is a convenience request to facilitate client UI construction. Rather than having to make `projects/:id/uiconfig/`, `projects/:id/tags/` and `projects/:id/tagcategories/` requests and then weaving them together, this request returns all and the only data a client needs to setup both listen and speak tag filtering screens. Ordering is enforced in response.

Default behavior is for Listen `display_items` to show one per `tag_id` since default Listen tag filtering will not filter `display_items` by user selections since there is no imposed order of user interaction as in Speak. For Speak, multiple `display_items` with the same `tag_id` can be included as they will have different `parent_ids`, allowing the client to filter the available `display_items` in each group based on previous user selections. For more complicated or non-standard client implementations, the lower level model api request can be used.

### HTTP Request

`GET localhost:8888/api/2/projects/1/uiconfig/`

### Parameters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
session_id | integer | used to localize response strings

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
[
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

<aside class="success">
Note — Adding GET param <code>admin=1</code> to this request will provide all localized strings in response, not only English.
</aside>


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
  "owner": "New Company",
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
  "demo_stream_message_loc": [47,48],
  "description_loc": [3,4]
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
  "data": '{"name":"New Project","owner": "New Company","latitude": 40,"longitude": -80,"pub_date":"2015-01-01T00:00:00","audio_format":"mp3","auto_submit": true,"max_recording_length": 35,"listen_questions_dynamic": false,"speak_questions_dynamic": false,"sharing_url": "http://roundware.org/r/eid=[id]","out_of_range_url": "http://roundware.dyndns.org:8000/outofrange.mp3","recording_radius": 10,"listen_enabled": true,"geo_listen_enabled": false,"speak_enabled": true,"geo_speak_enabled": true,"reset_tag_defaults_on_startup": false,"timed_asset_priority": false,"repeat_mode": "continuous","files_url": "http://roundware.dyndns.org/rw.zip","files_version": "1","audio_stream_bitrate": "128","ordering": "random","demo_stream_enabled": false,"demo_stream_url": "http://roundware.dyndns.org:8000/stream.mp3","out_of_range_distance": 5000,"language_ids": [1,2],"sharing_message_loc": [49,50],"out_of_range_message_loc": [47,48],"legal_agreement_loc": [53,54],"demo_stream_message_loc": [47,48], "description_loc": [3,4]}'
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
  "owner": "New Company",
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
  "description": "Project description.",
  "language_ids": [2,1]
}
```

Create new Project.

### HTTP Request

`POST localhost:8888/api/2/projects/`

### Required Parameters
Data format: `application/json`

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
owner | string | New owner |
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
description_loc | list of localized_string_ids | 5,6 | project description
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
  "owner": "New Company",
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
  "description": "Project description.",
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
owner | string | New owner |
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
description_loc | list of localized_string_ids | 5,6 | project description
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
