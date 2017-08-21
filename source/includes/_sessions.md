# sessions/

### Definition:
A client server connection established when the client is started and terminated when the client app is closed. `session_id` is established by the server and is used to keep track of multiple simultaneous sessions.

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
  "language": "fr",
  "project_id": 1,
  "starttime": "2017-06-09T02:42:03.939255",
  "stoptime": null,
  "timezone": "0000",
  "session_id": 104
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
demo_stream_enabled | boolean | false | defaults to false
geo_listen_enabled | boolean | true | defaults to `project.geo_listen_enabled`
language | 2-character code | es | defaults to en
timezone | string | "-5000" | ISO timezone standard
