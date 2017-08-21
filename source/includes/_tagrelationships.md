# tagrelationships/

### Definition:
Tag Relationships define a hierarchy of Tags via parent-child relationships. This can be used to create useful filtering opportunities such as assigning an artist as parent of a painting which would allow filtering by the artist to include the painting.

## GET tagrelationships/

```python
import requests

url = "http://localhost:8888/api/2/tagrelationships/"

querystring = {"tag_id":"1"}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/tagrelationships/?tag_id=1' \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/tagrelationships/?tag_id=1",
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
    "tag_id": 8,
    "parent_id": 1
  },
  {
    "id": 6,
    "tag_id": 22,
    "parent_id": 1
  }
]
```

Get list of Tag Relationships.

### HTTP Request

`GET localhost:8888/api/2/tagrelationships/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
tag_id | integer |
parent_id | integer | tag_id of parent tag


## GET tagrelationships/:id/

```python
import requests

url = "http://localhost:8888/api/2/tagrelationships/2/"

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/tagrelationships/2/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/tagrelationships/2/",
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
  "id": 3,
  "tag_id": 8,
  "parent_id": 1
}
```

Get specific Tag Relationship.

### HTTP Request

`GET localhost:8888/api/2/tagrelationships/2/`


## POST tagrelationships/

```python
import requests

url = "http://localhost:8888/api/2/tagrelationships/"

payload = '{"tag_id": 1, "parent_id": 5}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url http://localhost:8888/api/2/tagrelationships/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "tag_id": 1,
  "parent_id": 5
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/tagrelationships/",
  "method": "POST",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"tag_id": 1, "parent_id": 5}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 3,
  "tag_id": 1,
  "parent_id": 5
}
```

Create new Tag Relationship.

### HTTP Request

`POST localhost:8888/api/2/tagrelationships/`

### Required Parameters
Data format: `application/json`

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
tag_id | integer | 1 |
parent_id | integer | 5 |


## PATCH tagrelationships/:id/

```python
import requests

url = "http://localhost:8888/api/2/tagrelationships/5/"

payload = '{"tag_id": 2, "parent_id": 8}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("PATCH", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request PATCH \
  --url http://localhost:8888/api/2/tagrelationships/5/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "tag_id": 2,
  "parent_id": 8
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/tagrelationships/5/",
  "method": "PATCH",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"tag_id": 2, "parent_id": 8}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 5,
  "tag_id": 2,
  "parent_id": 8
}
```

Update Tag Relationship.

### HTTP Request

`PATCH localhost:8888/api/2/tagrelationships/:id/`

### Optional Parameters
Data format: `application/json`

Partial update allowed; params not included will leave field values unchanged.

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
tag_id | integer | 1 |
parent_id | integer | 5 |


## DELETE tagrelationships/:id/

```python
import requests

url = "http://localhost:8888/api/2/tagrelationships/5/"

payload = ""
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
    }

response = requests.request("DELETE", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request DELETE \
  --url http://localhost:8888/api/2/tagrelationships/5/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/tagrelationships/5/",
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

Delete Tag Relationship

### HTTP Request

`DELETE localhost:8888/api/2/tagrelationships/:id/`
