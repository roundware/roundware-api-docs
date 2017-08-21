# languages/

### Definition:
Roundware supports multiple languages. The ISO 2-character language code (i.e. `en`, `fr`, `es` etc) is used. Projects are assigned languages as part of their configuration and sessions are assigned languages based on that of the device initiating the session. Default is English `en`.

## GET languages/

```python
import requests

url = "http://localhost:8888/api/2/languages/"

querystring = {}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/languages/' \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/languages/",
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
    "name": "Spanish",
    "language_code": "es"
  },
  {
    "id": 3,
    "name": "French",
    "language_code": "fr"
  },
  {
    "id": 1,
    "name": "English",
    "language_code": "en"
  }
]
```

Get list of Languages.

### HTTP Request

`GET localhost:8888/api/2/languages/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
name | string | contains, case-insensitive
language_code | string |


## GET languages/:id/

```python
import requests

url = "http://localhost:8888/api/2/languages/2/"

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/languages/2/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/languages/2/",
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
  "name": "Spanish",
  "language_code": "es"
}
```

Get specific Language.

### HTTP Request

`GET localhost:8888/api/2/languages/2/`


## POST languages/

```python
import requests

url = "http://localhost:8888/api/2/languages/"

payload = '{"name": "French", "language_code": "fr"}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url http://localhost:8888/api/2/languages/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "name": "French",
  "language_code": "fr",
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/languages/",
  "method": "POST",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"name": "French", "language_code": "fr"}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 3,
  "name": "French",
  "language_code": "fr"
}
```

Create new Language.

### HTTP Request

`POST localhost:8888/api/2/languages/`

### Required Parameters
Data format: `application/json`

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
language_code | string | fr | Validates to 2-characters and non-existing

### Optional Parameters

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
name | string | French | used only for display purposes


## PATCH languages/:id/

```python
import requests

url = "http://localhost:8888/api/2/languages/3/"

payload = '{"name": "French!"}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("PATCH", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request PATCH \
  --url http://localhost:8888/api/2/languages/3/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{"name": "French!"}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/languages/3/",
  "method": "PATCH",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"name": "French!"}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 3,
  "name": "French!",
  "language_code": "fr"
}
```

Update Language.

### HTTP Request

`PATCH localhost:8888/api/2/languages/:id/`

### Optional Parameters
Data format: `application/json`

Partial update allowed; params not included will leave field values unchanged.

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
language_code | string | fr | Validates to 2-characters and non-existing
name | string | French | used only for display purposes


## DELETE languages/:id/

```python
import requests

url = "http://localhost:8888/api/2/languages/3/"

payload = ""
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
    }

response = requests.request("DELETE", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request DELETE \
  --url http://localhost:8888/api/2/languages/3/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/languages/3/",
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

Delete Language

### HTTP Request

`DELETE localhost:8888/api/2/languages/:id/`
