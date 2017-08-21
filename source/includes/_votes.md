# votes/

### Definition:
Votes provide a way for users to register their opinion with respect to particular Assets. There are certain Vote types (like, flag, etc) which can be exposed to users to allow them to cast.

## GET votes/

```python
import requests

url = "http://localhost:8888/api/2/votes/"

querystring = {"asset_id": "1"}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/votes/?asset_id=1' \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/votes/?asset_id=1'",
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
    "value": 5,
    "type": "like",
    "voter_id": 1,
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
  },
  {
    "id": 2,
    "value": 3,
    "type": "like",
    "voter_id": 1,
    "asset_id": 1,
    "session_id": 2,
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
  },
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
]
```

Get list of Votes.

### HTTP Request

`GET localhost:8888/api/2/votes/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
session_id | integer |
voter_id | integer | corresponds to user.id in database
asset_id | integer |
type | enum | OPTIONS: flag, like, rate, block_asset, block_user
value | integer | certain vote types require further info ie `rate`


## GET votes/:id/

```python
import requests

url = "http://localhost:8888/api/2/votes/2/"

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/votes/2/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/votes/2/",
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
  "value": 5,
  "type": "like",
  "voter_id": 1,
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

Get specific Vote.

### HTTP Request

`GET localhost:8888/api/2/votes/2/`


## POST votes/

```python
import requests

url = "http://localhost:8888/api/2/votes/"

payload = '{"type": "rate","value": 5,"asset_id" : 3,"session_id": 1}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url http://localhost:8888/api/2/votes/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
    "type": "rate",
    "value": 5,
    "asset_id" : 3,
    "session_id": 1
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/votes/",
  "method": "POST",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"type": "rate","value": 5,"asset_id" : 3,"session_id": 1}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 10,
  "value": 5,
  "type": "rate",
  "voter_id": null,
  "asset_id": 3,
  "session_id": 1,
  "asset_votes": [
    {
      "total": 1,
      "type": "like"
    },
    {
      "total": 3,
      "type": "rate",
      "avg": 5
    }
  ]
}
```

Create new Vote.

### HTTP Request

`POST localhost:8888/api/2/votes/`

### Required Parameters
Data format: `application/json`

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
session_id | integer | 7 |
asset_id | integer | 9 |
type | integer | 18 | OPTIONS: flag, like, rate, block_asset, block_user

### Optional Parameters
Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
value | integer | 3 | only used with `rate` currently


## PATCH votes/:id/

```python
import requests

url = "http://localhost:8888/api/2/votes/15/"

payload = '{"value": "4"}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("PATCH", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request PATCH \
  --url http://localhost:8888/api/2/votes/15/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "value": "4"
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/votes/15/",
  "method": "PATCH",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"value": "4"}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 10,
  "value": 4,
  "type": "rate",
  "voter_id": null,
  "asset_id": 3,
  "session_id": 1,
  "asset_votes": [
    {
      "total": 1,
      "type": "like"
    },
    {
      "total": 2,
      "type": "rate",
      "avg": 4.5
    }
  ]
}
```

Update Vote.

### HTTP Request

`PATCH localhost:8888/api/2/votes/:id/`

### Optional Parameters
Data format: `application/json`

Partial update allowed; params not included will leave field values unchanged.

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
session_id | integer | 7 |
asset_id | integer | 9 |
type | integer | 18 | OPTIONS: flag, like, rate, block_asset, block_user
value | integer | 3 | only used with `rate` currently


## DELETE votes/:id/

```python
import requests

url = "http://localhost:8888/api/2/votes/5/"

payload = ""
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
    }

response = requests.request("DELETE", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request DELETE \
  --url http://localhost:8888/api/2/votes/5/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/votes/5/",
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

Delete Vote.

### HTTP Request

`DELETE localhost:8888/api/2/votes/:id/`
