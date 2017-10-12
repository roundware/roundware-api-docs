# sessions/

### Definition:
A client server connection established when the client is started and terminated when the client app is closed. `session_id` is established by the server and is used to keep track of multiple simultaneous sessions.

## GET sessions/

```python
import requests

url = "http://localhost:8888/api/2/sessions/"

querystring = {"project_id":"1","language_id":"2","language":"en","geo_listen_enabled":"false","demo_stream_enabled":"true"}

headers = {'authorization': 'token aed40ccd8bbc291bf04ccea20627cd8f83eee9ca'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/sessions/?project_id=1&language_id=2&language=en&geo_listen_enabled=false&demo_stream_enabled=true' \
  --header 'authorization: token aed40ccd8bbc291bf04ccea20627cd8f83eee9ca'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/sessions/?project_id=1&language_id=2&language=en&geo_listen_enabled=false&demo_stream_enabled=true",
  "method": "GET",
  "headers": {
    "authorization": "token aed40ccd8bbc291bf04ccea20627cd8f83eee9ca"
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
        "id": 109,
        "device_id": null,
        "starttime": "2017-09-06T15:43:35.947761",
        "stoptime": null,
        "client_type": null,
        "client_system": "iOS 8.1",
        "demo_stream_enabled": true,
        "geo_listen_enabled": false,
        "timezone": "-8000",
        "project_id": 1,
        "language_id": 2
    },
    {
        "id": 111,
        "device_id": null,
        "starttime": "2017-09-06T16:24:32.647751",
        "stoptime": null,
        "client_type": null,
        "client_system": "iOS 8.1",
        "demo_stream_enabled": true,
        "geo_listen_enabled": false,
        "timezone": "-8000",
        "project_id": 1,
        "language_id": 2
    }
]
```

Get list of Sessions.

### HTTP Request

`GET localhost:8888/api/2/sessions/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
project_id | integer |
language_id | integer |
language | string | 2-char ISO shortcode
geo_listen_enabled | boolean |
demo_stream_enabled | boolean |


## GET sessions/:id/

```python
import requests

url = "http://localhost:8888/api/2/sessions/1/"

headers = {'authorization': 'token aed40ccd8bbc291bf04ccea20627cd8f83eee9ca'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/sessions/1/' \
  --header 'authorization: token aed40ccd8bbc291bf04ccea20627cd8f83eee9ca'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/sessions/1/",
  "method": "GET",
  "headers": {
    "authorization": "token aed40ccd8bbc291bf04ccea20627cd8f83eee9ca"
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
    "device_id": null,
    "starttime": "2017-09-06T16:24:32.647751",
    "stoptime": null,
    "client_type": null,
    "client_system": "iOS 8.1",
    "demo_stream_enabled": true,
    "geo_listen_enabled": false,
    "timezone": "-8000",
    "project_id": 1,
    "language_id": 2
}
```

Get specific Session.

### HTTP Request

`GET localhost:8888/api/2/sessions/1/`


## POST sessions/

```python
import requests

url = "http://localhost:8888/api/2/sessions/"

payload = '{"project_id": 1,"client_system": "iOS 8.1","geo_listen_enabled": true,"demo_stream_enabled": false,"language": "fr","timezone": "-8000"}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url http://localhost:8888/api/2/sessions/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "project_id": 1,
  "client_system": "iOS 8.1",
  "geo_listen_enabled": true,
  "demo_stream_enabled": false,
  "language": "fr",
  "timezone": "-8000"
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/sessions/",
  "method": "POST",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"project_id": 1,"client_system": "iOS 8.1","geo_listen_enabled": true,"demo_stream_enabled": false,"language": "fr","timezone": "-8000"}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "client_system": "iOS 8.1",
  "client_type": "iPhone",
  "demo_stream_enabled": false,
  "device_id": "12891038109281",
  "geo_listen_enabled": true,
  "language_id": 1,
  "project_id": 1,
  "starttime": "2017-06-09T02:42:03.939255",
  "stoptime": null,
  "timezone": "0000",
  "id": 104
}
```

Create new Session.

### HTTP Request

`POST localhost:8888/api/2/sessions/`

### Required Parameters
Data format: `application/json`

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
project_id | integer | 1 |
client_system | string | iOS 10.2 |

### Optional Parameters

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
client_type | string | | defaults to value in related session if not passed
demo_stream_enabled | boolean | false | defaults to false
geo_listen_enabled | boolean | true | defaults to `project.geo_listen_enabled`
language | 2-character code | es | defaults to en
language_id | integer | 1 | if both language and language_id are passed, language takes precedence
timezone | string | "-5000" | ISO timezone standard
