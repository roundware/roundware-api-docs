# uielements/

### Definition:
UI Elements represent the various graphic asset in the transformer app that are swappable based on Project selection by the user.

## GET uielements/

```python
import requests

url = "http://localhost:8888/api/2/uielements/"

querystring = {"project_id":"1"}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/uielements/?project_id=1' \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/uielements/?project_id=1",
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
        "variant": "@2x",
        "file_extension": "png",
        "label_text_color": "#123456",
        "label_position": "text_below",
        "label_text_loc_ids": [ 2,1 ],
        "uielementname_id": 1,
        "project_id": 1
    },
    {
        "id": 2,
        "variant": "@2x",
        "file_extension": "jpg",
        "label_text_color": "#ffffff",
        "label_position": "text_below",
        "label_text_loc_ids": [ 6,5 ],
        "uielementname_id": 3,
        "project_id": 1
    }
]
```

Get list of UI Elements.

### HTTP Request

`GET localhost:8888/api/2/uielements/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
project_id | integer |
variant | string | @2x, xxhdpi etc
file_extension | string | png, jpg typically
uielementname | string | contains and case-insensitive


## GET uielements/:id/

```python
import requests

url = "http://localhost:8888/api/2/uielements/2/"

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/uielements/2/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/uielements/2/",
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
    "variant": "@2x",
    "file_extension": "png",
    "label_text_color": "",
    "label_position": "",
    "label_text_loc_ids": [],
    "uielementname_id": 1,
    "project_id": 1
}
```

Get specific UI Element.

### HTTP Request

`GET localhost:8888/api/2/uielements/2/`


## POST uielements/

```python
import requests

url = "http://localhost:8888/api/2/uielements/"

payload = '{"variant": "@2x","file_extension": "png","label_text_color": "#000000","label_position": "text_overlay","label_text_loc_ids": [3,4],"uielementname_id": 2,"project_id": 1}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url http://localhost:8888/api/2/uielements/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{"variant": "@2x","file_extension": "png","label_text_color": "#000000","label_position": "text_overlay","label_text_loc_ids": [3,4],"uielementname_id": 2,"project_id": 1}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/uielements/",
  "method": "POST",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"variant": "@2x","file_extension": "png","label_text_color": "#000000","label_position": "text_overlay","label_text_loc_ids": [3,4],"uielementname_id": 2,"project_id": 1}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
    "id": 3,
    "variant": "@2x",
    "file_extension": "png",
    "label_text_color": "#000000",
    "label_position": "text_overlay",
    "label_text_loc_ids": [ 4,3 ],
    "uielementname_id": 2,
    "project_id": 1
}
```

Create new UI Element.

### HTTP Request

`POST localhost:8888/api/2/uielements/`

### Required Parameters
Data format: `application/json`

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
project_id | integer | 1 | ForeignKey
uielementname_id | integer | 4 | ForeignKey
variant | string | @2x |
file_extension | string | png |

### Optional Parameters

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
label_text_loc_ids | list of integers | 2,3 |
label_position | enum | text-overlay |
label_text_color | string | #123456 | hex color value

## PATCH uielements/:id/

```python
import requests

url = "http://localhost:8888/api/2/uielements/5/"

payload = '{"variant": "@3x"}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("PATCH", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request PATCH \
  --url http://localhost:8888/api/2/uielements/5/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{"variant": "@3x"}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/uielements/5/",
  "method": "PATCH",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"variant": "@3x"}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
    "id": 2,
    "variant": "@3x",
    "file_extension": "jpg",
    "label_text_color": "#ffffff",
    "label_position": "text_below",
    "label_text_loc_ids": [ 6,5 ],
    "uielementname_id": 3,
    "project_id": 3
}
```

Update UI Element.

### HTTP Request

`PATCH localhost:8888/api/2/uielements/:id/`

### Optional Parameters
Data format: `application/json`

Partial update allowed; params not included will leave field values unchanged.

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
project_id | integer | 1 | ForeignKey
uielementname_id | integer | 4 | ForeignKey
variant | string | @2x |
file_extension | string | png |
label_text_loc_ids | list of integers | 2,3 |
label_position | enum | text-overlay |
label_text_color | string | #123456 | hex color value


## DELETE uielements/:id/

```python
import requests

url = "http://localhost:8888/api/2/uielements/5/"

payload = ""
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
    }

response = requests.request("DELETE", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request DELETE \
  --url http://localhost:8888/api/2/uielements/5/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/uielements/5/",
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

Delete UI Element.

### HTTP Request

`DELETE localhost:8888/api/2/uielements/:id/`
