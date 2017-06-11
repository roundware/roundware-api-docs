# listenevents/

### Definition:
Listen events are essentially database logs of each asset that has played in the audio stream for each session. Information on the asset as well as the sequence is included such that sessions can be reconstructed after the fact for debugging and analysis.

## GET listenevents/

```python
import requests

url = "http://localhost:8888/api/2/listenevents/"

querystring = {"session":"35", "asset":"11"}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/listenevents/?session=35&asset=11' \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/listenevents/?session=35&asset=11",
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
    "id": 39,
    "duration_in_seconds": 28.41,
    "start_time": "2017-04-21T14:57:05.979645",
    "session_id": 35,
    "asset_id": 11
  },
  {
    "id": 41,
    "duration_in_seconds": 10.36,
    "start_time": "2017-04-21T14:58:55.979936",
    "session_id": 35,
    "asset_id": 11
  }
]
```

Get list of Listen Events.

### HTTP Request

`GET localhost:8888/api/2/listenevents/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
session | integer |
asset | integer |
duration__lte | integer | currently in nanoseconds
duration__gte | integer | currently in nanoseconds
start_time__lte | datetime | format: `2017-04-21T14:58:55.979936`
start_time__gte | datetime | format: `2017-04-21T14:58:55.979936`


## GET listenevents/:id/

```python
import requests

url = "http://localhost:8888/api/2/listenevents/2/"

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/listenevents/2/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/listenevents/2/",
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
  "duration_in_seconds": 10.36,
  "start_time": "2017-04-21T14:58:55.979936",
  "session_id": 35,
  "asset_id": 11
}
```

Get specific Listen Event.

### HTTP Request

`GET localhost:8888/api/2/listenevents/2/`
