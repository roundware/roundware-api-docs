# uielementnames/

### Definition:
UI Element Names stores a standardized list of names for UI Elements that link up with all of the dynamic graphic elements in the various app screens of a transformer app.

## GET uielementnames/

```python
import requests

url = "http://localhost:8888/api/2/uielementnames/"

querystring = {"view":"home","name":"btn"}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/uielementnames/?view=home&name=btn' \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/uielementnames/?view=home&name=btn",
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
        "id": 2,
        "name": "home-speak-btn",
        "description": "",
        "view": "home"
    },
    {
        "id": 3,
        "name": "home-listen-btn",
        "description": "",
        "view": "home"
    },
    {
        "id": 4,
        "name": "home-info-btn",
        "description": "",
        "view": "home"
    }
]
```

Get list of UI Element Names.

### HTTP Request

`GET localhost:8888/api/2/uielementnames/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
view | string | corresponds to the screen/view the element is used in
name | string | contains and case-insensitive


## GET uielementnames/:id/

```python
import requests

url = "http://localhost:8888/api/2/uielementnames/2/"

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/uielementnames/2/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/uielementnames/2/",
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
    "name": "home-speak-btn",
    "description": "",
    "view": "home"
}
```

Get specific UI Element Name.

### HTTP Request

`GET localhost:8888/api/2/uielementnames/2/`


## POST uielementnames/

```python
import requests

url = "http://localhost:8888/api/2/uielementnames/"

payload = '{"name": "listen-filter-btn", "view": "listen"}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url http://localhost:8888/api/2/uielementnames/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{"name": "listen-filter-btn", "view": "listen"}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/uielementnames/",
  "method": "POST",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"name": "listen-filter-btn", "view": "listen"}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
    "id": 8,
    "name": "listen-filter-btn",
    "description": "",
    "view": "listen"
}
```

Create new UI Element Name.

### HTTP Request

`POST localhost:8888/api/2/uielementnames/`

### Required Parameters
Data format: `application/json`

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
view | string | listen
name | string | listen-filter-btn |

### Optional Parameters

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
description | string | this button is used to start the audio stream |


## PATCH uielementnames/:id/

```python
import requests

url = "http://localhost:8888/api/2/uielementnames/5/"

payload = '{"name": "listen-speak-btn"}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("PATCH", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request PATCH \
  --url http://localhost:8888/api/2/uielementnames/5/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "name": "listen-speak-btn"
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/uielementnames/5/",
  "method": "PATCH",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"name": "listen-speak-btn"}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
    "id": 5,
    "name": "listen-speak-btn",
    "description": "",
    "view": "speak"
}
```

Update UI Element Name.

### HTTP Request

`PATCH localhost:8888/api/2/uielementnames/:id/`

### Optional Parameters
Data format: `application/json`

Partial update allowed; params not included will leave field values unchanged.

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
view | string | listen
name | string | listen-filter-btn |
description | string | this button is used to start the audio stream |


## DELETE uielementnames/:id/

```python
import requests

url = "http://localhost:8888/api/2/uielementnames/5/"

payload = ""
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
    }

response = requests.request("DELETE", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request DELETE \
  --url http://localhost:8888/api/2/uielementnames/5/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/uielementnames/5/",
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

Delete UI Element Name

### HTTP Request

`DELETE localhost:8888/api/2/uielementnames/:id/`
