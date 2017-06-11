# localizedstrings/

### Definition:
A string and corresponding language. Roundware supports multiple languages by assigning strings for each language to all text that requires localization.

## GET localizedstrings/

```python
import requests

url = "http://localhost:8888/api/2/localizedstrings/"

querystring = {"localized_string":"roundware","language":"en"}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/localizedstrings/?localized_string=roundware&language=en' \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/localizedstrings/?localized_string=roundware&language=en",
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
    "language": "en",
    "text": "Why are you using Roundware?"
  },
  {
    "id": 47,
    "language": "en",
    "text": "You are out of range of this Roundware project.  Please go somewhere within range and try again.  Thank you."
  }
]
```

Get list of Localized Strings.

### HTTP Request

`GET localhost:8888/api/2/localizedstrings/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
language | string | contains, case-insensitive
localized_string | string | contains, case-insensitive


## GET localizedstrings/:id/

```python
import requests

url = "http://localhost:8888/api/2/localizedstrings/2/"

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/localizedstrings/2/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/localizedstrings/2/",
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
  "language": "en",
  "text": "Why are you using Roundware?"
}
```

Get specific Localized String.

### HTTP Request

`GET localhost:8888/api/2/localizedstrings/2/`


## POST localizedstrings/

```python
import requests

url = "http://localhost:8888/api/2/localizedstrings/"

payload = '{"localized_string":"This is a new localized string.", "language":"en"}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url http://localhost:8888/api/2/localizedstrings/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "localized_string": "This is a new localized string.",
  "language": "en",
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/localizedstrings/",
  "method": "POST",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"localized_string":"This is a new localized string.", "language":"en"}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 3,
  "language": "en",
  "text": "This is a new localized string."
}
```

Create new Localized String.

### HTTP Request

`POST localhost:8888/api/2/localizedstrings/`

### Required Parameters
Data format: application/json

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
localized_string | string | Hello |
language | string | en | Validates to existing


## PATCH languages/:id/

```python
import requests

url = "http://localhost:8888/api/2/localizedstrings/3/"

payload = '{"localized_string":"This is an updated localized string."}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("PATCH", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request PATCH \
  --url http://localhost:8888/api/2/localizedstrings/3/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{"localized_string":"This is an updated localized string."}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/localizedstrings/3/",
  "method": "PATCH",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"localized_string":"This is an updated localized string."}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 3,
  "language": "en",
  "text": "This is an updated localized string."
}
```

Update Localized String.

### HTTP Request

`PATCH localhost:8888/api/2/localizedstrings/:id/`

### Optional Parameters
Data format: `application/json`

Partial update allowed; params not included will leave field values unchanged.

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
localized_string | string | Hello |
language | string | en | Validates to existing


## DELETE localizedstrings/:id/

```python
import requests

url = "http://localhost:8888/api/2/localizedstrings/3/"

payload = ""
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
    }

response = requests.request("DELETE", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request DELETE \
  --url http://localhost:8888/api/2/localizedstrings/3/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/localizedstrings/3/",
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

Delete Localized String

### HTTP Request

`DELETE localhost:8888/api/2/localizedstrings/:id/`
