# uiitems/

### Definition:
UI Items represent Tags in client user interfaces. UI Items are grouped into UI Groups in the user interface and are displayed together to allow for user selections.

## GET uiitems/

```python
import requests

url = "http://localhost:8888/api/2/uiitems/"

querystring = {"ui_group_id": "1","active":"true"}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/uiitems/?ui_group_id=3&active=true' \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/uiitems/?ui_group_id=3&active=true'",
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
    "id": 5,
    "index": 1,
    "default": true,
    "active": true,
    "ui_group_id": 3,
    "tag_id": 5,
    "parent_id": null
  },
  {
    "id": 54,
    "index": 2,
    "default": true,
    "active": true,
    "ui_group_id": 3,
    "tag_id": 22,
    "parent_id": null
  }
]
```

Get list of UI Items.

### HTTP Request

`GET localhost:8888/api/2/uiitems/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
ui_group_id | integer |
tag_id | integer |
active | boolean |
parent_id | integer |
default | boolean |
index | integer | imposes ordering in client UI


## GET uiitems/:id/

```python
import requests

url = "http://localhost:8888/api/2/uiitems/2/"

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/uiitems/2/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/uiitems/2/",
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
  "index": 2,
  "default": true,
  "active": true,
  "ui_group_id": 3,
  "tag_id": 22,
  "parent_id": null
}
```

Get specific UI Item.

### HTTP Request

`GET localhost:8888/api/2/uiitems/2/`


## POST uiitems/

```python
import requests

url = "http://localhost:8888/api/2/uiitems/"

payload = '{"index": 2,"default": true,"active": true,"ui_group_id": 3,"tag_id": 8,"parent_id": null}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url http://localhost:8888/api/2/uiitems/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
    "index": 2,
    "default": true,
    "active": true,
    "ui_group_id": 3,
    "tag_id": 8,
    "parent_id": null
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/uiitems/",
  "method": "POST",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"index": 2,"default": true,"active": true,"ui_group_id": 3,"tag_id": 8,"parent_id": null}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 61,
  "index": 2,
  "default": true,
  "active": true,
  "ui_group_id": 3,
  "tag_id": 8,
  "parent_id": null
}
```

Create new UI Item.

### HTTP Request

`POST localhost:8888/api/2/uiitems/`

### Required Parameters
Data format: `application/json`

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
ui_group_id | integer | 7 |
tag_id | integer | 9 |
parent_id | integer | 18 |
index | integer | 2 | imposes ordering in client UI

### Optional Parameters
Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
default | boolean | true | defaults to false
active | boolean | true | defaults to false


## PATCH uiitems/:id/

```python
import requests

url = "http://localhost:8888/api/2/uiitems/15/"

payload = '{"active": "false"}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("PATCH", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request PATCH \
  --url http://localhost:8888/api/2/uiitems/15/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "active": "false"
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/uiitems/15/",
  "method": "PATCH",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"active": "false"}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 61,
  "index": 2,
  "default": true,
  "active": false,
  "ui_group_id": 3,
  "tag_id": 8,
  "parent_id": null
}
```

Update UI Item.

### HTTP Request

`PATCH localhost:8888/api/2/uiitems/:id/`

### Optional Parameters
Data format: `application/json`

Partial update allowed; params not included will leave field values unchanged.

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
ui_group_id | integer | 7 |
tag_id | integer | 9 |
parent_id | integer | 18 |
index | integer | 2 | imposes ordering in client UI
default | boolean | true | defaults to false
active | boolean | true | defaults to false


## DELETE uiitems/:id/

```python
import requests

url = "http://localhost:8888/api/2/uiitems/5/"

payload = ""
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
    }

response = requests.request("DELETE", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request DELETE \
  --url http://localhost:8888/api/2/uiitems/5/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/uiitems/5/",
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

Delete UI Item.

### HTTP Request

`DELETE localhost:8888/api/2/uiitems/:id/`
