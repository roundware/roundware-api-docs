# tagcategories/

### Definition:
Tag Categories are used to group Tags. For example, for Tag Category `Age`, the Tags might be `Young` and `Old`. Typically Tags of a specific Tag Category form the UI Items within a single UI Group.

## GET tagcategories/

```python
import requests

url = "http://localhost:8888/api/2/tagcategories/"

querystring = {}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/tagcategories/' \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/tagcategories/",
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
    "name": "question",
    "data": ""
  },
  {
    "id": 3,
    "name": "gender",
    "data": ""
  },
  {
    "id": 4,
    "name": "usertype",
    "data": ""
  }
]
```

Get list of Tag Categories.

### HTTP Request

`GET localhost:8888/api/2/tagcategories/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
name | string | contains and case-insensitive


## GET tagcategories/:id/

```python
import requests

url = "http://localhost:8888/api/2/tagcategories/2/"

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/tagcategories/2/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/tagcategories/2/",
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
  "name": "question",
  "data": ""
}
```

Get specific Tag Category.

### HTTP Request

`GET localhost:8888/api/2/tagcategories/2/`


## POST tagcategories/

```python
import requests

url = "http://localhost:8888/api/2/tagcategories/"

payload = '{"name": "new tag category", "data": "some useful further info"}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url http://localhost:8888/api/2/tagcategories/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "name": "new tag category",
  "data": "some useful further info"
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/tagcategories/",
  "method": "POST",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"name": "new tag category", "data": "some useful further info"}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 5,
  "name": "new tag category",
  "data": "some useful further info"
}
```

Create new Tag Category.

### HTTP Request

`POST localhost:8888/api/2/tagcategories/`

### Required Parameters
Data format: application/json

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
name | string | new tag category |

### Optional Parameters

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
data | string | more info |


## PATCH tagcategories/:id/

```python
import requests

url = "http://localhost:8888/api/2/tagcategories/5/"

payload = '{"name": "updated name"}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("PATCH", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request PATCH \
  --url http://localhost:8888/api/2/tagcategories/5/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "name": "updated name"
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/tagcategories/5/",
  "method": "PATCH",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"name": "updated name"}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 5,
  "name": "updated name",
  "data": "some useful further info"
}
```

Update Tag Category.

### HTTP Request

`PATCH localhost:8888/api/2/tagcategories/:id/`

### Optional Parameters
Data format: `application/json`

Partial update allowed; params not included will leave field values unchanged.

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
name | string | new tag category |
data | string | more info |


## DELETE tagcategories/:id/

```python
import requests

url = "http://localhost:8888/api/2/tagcategories/5/"

payload = ""
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
    }

response = requests.request("DELETE", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request DELETE \
  --url http://localhost:8888/api/2/tagcategories/5/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/tagcategories/5/",
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

Delete Tag Category

### HTTP Request

`DELETE localhost:8888/api/2/tagcategories/:id/`
