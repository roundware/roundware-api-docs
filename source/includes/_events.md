# events/

### Definition:
A record of each time a client pings the server with an API call or internal server action occurs as a result of client activity. All events are tagged with an `event_type` such as `start_session`, `start_listen`, `upload_recording`, etc. Event data provides the core source for all RW system analysis.

## GET events/

```python
import requests

url = "http://localhost:8888/api/2/events/"

querystring = {"session_id":"1"}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/events/?session_id=1' \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/events/?session_id=1",
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
    "server_time": "2017-04-15T16:35:57.295461",
    "client_time": null,
    "event_type": "start_upload",
    "data": null,
    "latitude": null,
    "longitude": null,
    "session_id": 1,
    "tag_ids": "3,8"
  },
  {
    "id": 2,
    "server_time": "2017-04-15T16:36:04.916135",
    "client_time": null,
    "event_type": "start_upload",
    "data": null,
    "latitude": null,
    "longitude": null,
    "session_id": 1,
    "tag_ids": "4,8"
  }
]
```

Get list of Events.

### HTTP Request

`GET localhost:8888/api/2/events/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
session_id | integer |
event_type | string | `start_listen` `upload_recording` etc
server_time | datetime |
server_time__gt | datetime | greater than specified datetime
server_time__lt | datetime | less than specified datetime
latitude | double | where event occurred
longitude | double | where event occurred
tag_ids | list of integers | certain `event_types` have tags associated with them


## GET events/:id/

```python
import requests

url = "http://localhost:8888/api/2/events/1/"

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/events/1/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/events/1/",
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
  "server_time": "2017-05-06T22:55:15.114568",
  "client_time": null,
  "event_type": "start_upload",
  "data": null,
  "latitude": "40.75921249389648",
  "longitude": "-73.98463439941406",
  "session_id": 1,
  "tag_ids": "3,22,8"
}
```

Get specific Event.

### HTTP Request

`GET localhost:8888/api/2/events/1/`


## POST events/

```python
import requests

url = "http://localhost:8888/api/2/events/"

payload = '{"session_id": 1, "event_type": "heartbeat", "client_time": "2017-05-06T22:55:15.114568", "latitude": 1.2345, "longitude": 2.3456, "tag_ids": "3,8", "data": "some random data"}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url http://localhost:8888/api/2/events/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "session_id": 1,
  "event_type": "heartbeat",
  "client_time": "2017-05-06T22:55:15.114568",
  "latitude": 1.2345,
  "longitude": 2.3456,
  "tag_ids": "3,8",
  "data": "some random data"
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/events/",
  "method": "POST",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"session_id": 1, "event_type": "heartbeat", "client_time": "2017-05-06T22:55:15.114568", "latitude": 1.2345, "longitude": 2.3456, "tag_ids": "3,8", "data": "some random data"}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 10,
  "server_time": "2017-06-07T22:41:50.556694",
  "client_time": "2017-05-06T22:55:15.114568",
  "event_type": "heartbeat",
  "data": "some random data",
  "latitude": "1.2345",
  "longitude": "2.3456",
  "session_id": 1,
  "tag_ids": "3,8"
}
```

Create new Event.

### HTTP Request

`POST localhost:8888/api/2/events/`

### Required Parameters
Data format: `application/json`

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
session_id | integer | 1 |
event_type | string | 0.5 | `start_listen` `upload_recording` etc

### Optional Parameters

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
client_time | `boolean` | `true` | defaults to `true`
latitude | string | | will be changed to double in future release
longitude | string | | will be changed to double in future release
tag_ids | string | 3,4,5 |
data | string | "some random data" | whatever you want
