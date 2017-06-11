# timedassets/

### Definition:
Assets that are made available based on session length rather than location. This allows for a loose linear narrative to be imposed on top of the otherwise unpredictable experience based on the path that a user wanders.

## GET timedassets/

```python
import requests

url = "http://localhost:8888/api/2/timedassets/"

querystring = {"project_id": "1"}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/timedassets/?project_id=1' \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/timedassets/?project_id=1",
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
    "start": 50,
    "end": 100,
    "asset_id": 1,
    "project_id": 1
  },
  {
    "id": 3,
    "start": 55,
    "end": 100,
    "asset_id": 1,
    "project_id": 1
  },
  {
    "id": 5,
    "start": 50,
    "end": 100,
    "asset_id": 2,
    "project_id": 1
  }
]
```

Get list of Timed Assets.

### HTTP Request

`GET localhost:8888/api/2/timedassets/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
project_id | integer |
start__gte | integer | in seconds, greater than or equal
start__lte | integer | in seconds, less than or equal
end__gte | integer | in seconds, greater than or equal
end__lte | integer | in seconds, less than or equal


## GET timedassets/:id/

```python
import requests

url = "http://localhost:8888/api/2/timedassets/2/"

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/timedassets/2/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/timedassets/2/",
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
  "id": 2,
  "start": 55,
  "end": 100,
  "asset_id": 1,
  "project_id": 1
}
```

Get specific Timed Assets.

### HTTP Request

`GET localhost:8888/api/2/timedassets/2/`


## POST timedassets/

```python
import requests

url = "http://localhost:8888/api/2/timedassets/"

payload = '{"start": 50,"end": 100,"asset_id" : 2,"project_id": 1}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url http://localhost:8888/api/2/timedassets/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "start": 50,
  "end": 100,
  "asset_id" : 2,
  "project_id": 1
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/timedassets/",
  "method": "POST",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"start": 50,"end": 100,"asset_id" : 2,"project_id": 1}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 7,
  "start": 50,
  "end": 100,
  "asset_id": 2,
  "project_id": 1
}
```

Create new Timed Asset.

### HTTP Request

`POST localhost:8888/api/2/timedassets/`

### Required Parameters
Data format: application/json

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
project_id | integer | 1 |
asset_id | integer | 5 |
start | integer | 50 | when Asset becomes available to playlist
end | integer | 100 | when Asset becomes unavailable to playlist


## PATCH timedassets/:id/

```python
import requests

url = "http://localhost:8888/api/2/timedassets/7/"

payload = '{"start": 10}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("PATCH", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request PATCH \
  --url http://localhost:8888/api/2/timedassets/7/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "start": 10
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/timedassets/7/",
  "method": "PATCH",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"start": 10}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 7,
  "start": 10,
  "end": 100,
  "asset_id": 2,
  "project_id": 1
}
```

Update Timed Asset.

### HTTP Request

`PATCH localhost:8888/api/2/timedassets/:id/`

### Optional Parameters
Data format: `application/json`

Partial update allowed; params not included will leave field values unchanged.

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
project_id | integer | 1 |
asset_id | integer | 5 |
start | integer | 50 | when Asset becomes available to playlist
end | integer | 100 | when Asset becomes unavailable to playlist


## DELETE timedassets/:id/

```python
import requests

url = "http://localhost:8888/api/2/timedassets/5/"

payload = ""
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
    }

response = requests.request("DELETE", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request DELETE \
  --url http://localhost:8888/api/2/timedassets/5/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/timedassets/5/",
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

Delete Timed Asset

### HTTP Request

`DELETE localhost:8888/api/2/timedassets/:id/`
