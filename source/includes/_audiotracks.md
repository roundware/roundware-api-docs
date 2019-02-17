# audiotracks/

### Definition:
A linear assemblage of alternating audio assets and silence (‘dead air’) which dynamically forms part of each stream by incorporating audio assets into the stream. There can be multiple audiotracks for each project which determine how many simultaneous audio assets can ever play back. Audiotracks can be filtered by tag such that an audiotrack only plays assets that have certain tags associated with them.

## GET audiotracks/

```python
import requests

url = "http://localhost:8888/api/2/audiotracks/"

querystring = {"project_id":"1","minduration__lte":"10","minduration__gte":"20","maxduration__lte":"30","maxduration__gte":"40"}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/audiotracks/?project_id=1&minduration__lte=10&minduration__gte=20&maxduration__lte=30&maxduration__gte=40' \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/audiotracks/?project_id=1&minduration__lte=10&minduration__gte=20&maxduration__lte=30&maxduration__gte=40",
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
    "minvolume": 1,
    "maxvolume": 1,
    "minduration": 5.5555,
    "maxduration": 10,
    "mindeadair": 1,
    "maxdeadair": 3,
    "minfadeintime": 0.1,
    "maxfadeintime": 0.5,
    "minfadeouttime": 0.1,
    "maxfadeouttime": 2,
    "minpanpos": 0,
    "maxpanpos": 0,
    "minpanduration": 5,
    "maxpanduration": 10,
    "repeatrecordings": false,
    "project_id": 1,
    "tag_filters": [1,6,12],
    "banned_duration": 60,
    "active": true,
    "start_with_silence": true
  },
  {
    "id": 4,
    "minvolume": 0,
    "maxvolume": 1,
    "minduration": 2.5,
    "maxduration": 10,
    "mindeadair": 1,
    "maxdeadair": 3,
    "minfadeintime": 0.6,
    "maxfadeintime": 5,
    "minfadeouttime": 0.1,
    "maxfadeouttime": 2,
    "minpanpos": -0.5,
    "maxpanpos": 0.75,
    "minpanduration": 5,
    "maxpanduration": 17,
    "repeatrecordings": false,
    "project_id": 3,
    "tag_filters": [3,5,23],
    "banned_duration": 600,
    "active": true,
    "start_with_silence": false
  }
]
```

Get list of Audiotracks.

### HTTP Request

`GET localhost:8888/api/2/audiotracks/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
project_id | integer |
minduration__lte | integer | less than or equal to in seconds
minduration__gte | integer | greater than or equal to in seconds
maxduration__lte | integer | less than or equal to in seconds
maxduration__gte | integer | greater than or equal to in seconds
mindeadair__lte | integer | less than or equal to in seconds
mindeadair__gte | integer | greater than or equal to in seconds
maxdeadair__lte | integer | less than or equal to in seconds
maxdeadair__gte | integer | greater than or equal to in seconds


## GET audiotracks/:id/

```python
import requests

url = "http://localhost:8888/api/2/audiotracks/1/"

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/audiotracks/1/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/audiotracks/1/",
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
  "minvolume": 1,
  "maxvolume": 1,
  "minduration": 5.5555,
  "maxduration": 10,
  "mindeadair": 1,
  "maxdeadair": 3,
  "minfadeintime": 0.1,
  "maxfadeintime": 0.5,
  "minfadeouttime": 0.1,
  "maxfadeouttime": 2,
  "minpanpos": 0,
  "maxpanpos": 0,
  "minpanduration": 5,
  "maxpanduration": 10,
  "repeatrecordings": false,
  "project_id": 1,
  "tag_filters": [1,6,12],
  "banned_duration": 60,
  "active": true,
  "start_with_silence": true
}
```

Get specific Audiotrack.

### HTTP Request

`GET localhost:8888/api/2/audiotracks/1/`

## POST audiotracks/

```python
import requests

url = "http://localhost:8888/api/2/audiotracks/"

payload = '{"project_id": 1,"minvolume": 0,"maxvolume": 1,"minduration": 2.5,"maxduration": 10,"mindeadair": 1,"maxdeadair": 3,"minfadeintime": 0.6,"maxfadeintime":5,"minfadeouttime":0.1,"maxfadeouttime": 2,"minpanpos": -0.5,"maxpanpos": 0.75,"minpanduration": 5,"maxpanduration": 17,"repeatrecordings": false,
"tag_filters":[2,3], "banned_duration":60, "active": true, "start_with_silence": false}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url http://localhost:8888/api/2/audiotracks/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "project_id": 1,
  "minvolume": 0,
  "maxvolume": 1,
  "minduration": 2.5,
  "maxduration": 10,
  "mindeadair": 1,
  "maxdeadair": 3,
  "minfadeintime": 0.6,
  "maxfadeintime": 5,
  "minfadeouttime": 0.1,
  "maxfadeouttime": 2,
  "minpanpos": -0.5,
  "maxpanpos": 0.75,
  "minpanduration": 5,
  "maxpanduration": 17,
  "repeatrecordings": false,
  "tag_filters": [2,3],
  "banned_duration": 60,
  "active": true,
  "start_with_silence": true
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/audiotracks/",
  "method": "POST",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"project_id": 1,"minvolume": 0,"maxvolume": 1,"minduration": 2.5,"maxduration": 10,"mindeadair": 1,"maxdeadair": 3,"minfadeintime": 0.6,"maxfadeintime": 5,"minfadeouttime": 0.1,"maxfadeouttime": 2,"minpanpos": -0.5,"maxpanpos": 0.75,"minpanduration": 5,"maxpanduration": 17,"repeatrecordings": false,"tag_filters":[2,3], "banned_duration":60, "active": true, "start_with_silence": false'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 1,
  "minvolume": 0,
  "maxvolume": 1,
  "minduration": 2.5,
  "maxduration": 10,
  "mindeadair": 1,
  "maxdeadair": 3,
  "minfadeintime": 0.6,
  "maxfadeintime": 5,
  "minfadeouttime": 0.1,
  "maxfadeouttime": 2,
  "minpanpos": -0.5,
  "maxpanpos": 0.75,
  "minpanduration": 5,
  "maxpanduration": 17,
  "repeatrecordings": false,
  "project_id": 1,
  "tag_filters": [2,3],
  "banned_duration": 60,
  "active": true,
  "start_with_silence": false
}
```

Create new Audiotrack.

### HTTP Request

`POST localhost:8888/api/2/audiotracks/`

### Required Parameters
Data format: `application/json`

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
project_id | integer | 1 |
minvolume | float | 0.5 |
maxvolume | float | 1.0 |
minduration | float | 10 |
maxduration | float | 30 |
mindeadair | float | 5 |
maxdeadair | float | 10 |
minfadeintime | float | 1.5 |
maxfadeintime | float | 3.0 |
minfadeouttime | float | 1.0 |
maxfadeouttime | float | 2.5 |
minpanpos | float | -0.5 | must be between -1.0 and 1.0
maxpanpos | float | 0.5 | must be between -1.0 and 1.0
minpanduration | float | 10 |
maxpanduration | float | 20 |

### Optional Parameters

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
active | `boolean` | `true` | defaults to `true`
repeatrecordings | `boolean` | `true` | defaults to `true`
tag_filters | array of integers | [3,4,5] |
start_with_silence | `boolean`| `false` | defaults to `false` ie start with asset
banned_duration | integer | 600 | elapsed time before asset can repeat (seconds)


## PATCH audiotracks/:id/

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
  --url http://localhost:8888/api/2/audiotracks/2/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "minvolume": 0,
  "maxvolume": 1,
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/audiotracks/2/",
  "method": "PATCH",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"minvolume": 0.5,"maxvolume": 0.8}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 2,
  "minvolume": 0.5,
  "maxvolume": 0.8,
  "minduration": 2.5,
  "maxduration": 10,
  "mindeadair": 1,
  "maxdeadair": 3,
  "minfadeintime": 0.6,
  "maxfadeintime": 5,
  "minfadeouttime": 0.1,
  "maxfadeouttime": 2,
  "minpanpos": -0.5,
  "maxpanpos": 0.75,
  "minpanduration": 5,
  "maxpanduration": 17,
  "repeatrecordings": false,
  "project_id": 1,
  "tag_filters": [2,3],
  "banned_duration": 60,
  "active": true,
  "start_with_silence": false
}
```

Update Audiotrack.

### HTTP Request

`PATCH localhost:8888/api/2/audiotracks/:id/`

### Optional Parameters
Data format: `application/json`

Partial update allowed; params not included will leave field values unchanged.

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
project_id | integer | 1 |
minvolume | float | 0.5 |
maxvolume | float | 1.0 |
minduration | float | 10 |
maxduration | float | 30 |
mindeadair | float | 5 |
maxdeadair | float | 10 |
minfadeintime | float | 1.5 |
maxfadeintime | float | 3.0 |
minfadeouttime | float | 1.0 |
maxfadeouttime | float | 2.5 |
minpanpos | float | -0.5 | must be between -1.0 and 1.0
maxpanpos | float | 0.5 | must be between -1.0 and 1.0
minpanduration | float | 10 |
maxpanduration | float | 20 |
repeatrecordings | `boolean` | `true` | defaults to `true`
tag_filters | array of integers | [3,4,5] |
active | `boolean` | `true` |
start_with_silence | `boolean`| `false` |
banned_duration | integer | 600 |


## DELETE audiotracks/:id/

```python
import requests

url = "http://localhost:8888/api/2/audiotracks/3/"

payload = ""
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
    }

response = requests.request("DELETE", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request DELETE \
  --url http://localhost:8888/api/2/audiotracks/3/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/audiotracks/3/",
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

Delete Audiotrack

### HTTP Request

`DELETE localhost:8888/api/2/audiotracks/:id/`
