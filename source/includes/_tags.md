# tags/

### Definition:
Tags are metadata used to describe Assets. Tags are arranged by Tag Category. For example, the tags within the `age` Tag Category could be `young` and `old`. Tags are very flexible and allow for collecting many different types of metadata to be used for filtering the assets at a later time.

## GET tags/

```python
import requests

url = "http://localhost:8888/api/2/tags/"

querystring = {"description": "male"}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/tags/?description=male' \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/tags/?description=male",
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
  "tags": [
    {
      "id": 3,
      "value": "male",
      "description": "male",
      "data": "class=tag-one",
      "filter": "",
      "location": null,
      "project_id": 1,
      "tag_category_id": 3,
      "description_loc": null,
      "msg_loc": "male",
      "relationships": [
        {
          "id": 2,
          "tag_id": 3,
          "parent_id": null
        },
        {
          "id": 17,
          "tag_id": 3,
          "parent_id": null
        }
      ]
    },
    {
      "id": 4,
      "value": "female",
      "description": "female",
      "data": "class=tag-one",
      "filter": "",
      "location": null,
      "project_id": 1,
      "tag_category_id": 3,
      "description_loc": null,
      "msg_loc": "female",
      "relationships": [
        {
          "id": 1,
          "tag_id": 4,
          "parent_id": null
        }
      ]
    }
  ]
}
```

Get list of Tags.

### HTTP Request

`GET localhost:8888/api/2/tags/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
project_id | integer |
description | string | contains and case-insensitive
data | string | contains and case-insensitive


## GET tags/:id/

```python
import requests

url = "http://localhost:8888/api/2/tags/2/"

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/tags/2/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/tags/2/",
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
  "id": 4,
  "value": "female",
  "description": "female",
  "data": "class=tag-one",
  "filter": "",
  "location": null,
  "project_id": 1,
  "tag_category_id": 3,
  "description_loc": null,
  "msg_loc": "female",
  "relationships": [
    {
      "id": 1,
      "tag_id": 4,
      "parent_id": null
    }
  ]
}
```

Get specific Tag.

### HTTP Request

`GET localhost:8888/api/2/tags/2/`


## POST tags/

```python
import requests

url = "http://localhost:8888/api/2/tags/"

payload = '{"value": "male","description": "male","data": "class=tag-one","project_id": 1,"tag_category_id": 3,"description_loc_ids": [44,43], "msg_loc_ids": [5,6]}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url http://localhost:8888/api/2/tags/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "value": "male",
  "description": "male",
  "data": "class=tag-one",
  "filter": "",
  "location": null,
  "project_id": 1,
  "tag_category_id": 3,
  "description_loc_ids": [44,43],
  "msg_loc_ids": [5,6]
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/tags/",
  "method": "POST",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"value": "male","description": "male","data": "class=tag-one","project_id": 1,"tag_category_id": 3,"description_loc_ids": [44,43], "msg_loc_ids": [5,6]}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 7,
  "value": "male",
  "description": "male",
  "data": "class=tag-one",
  "filter": "",
  "location": null,
  "project_id": 1,
  "tag_category_id": 3,
  "description_loc": [44,43],
  "msg_loc": "female",
  "relationships": []
}
```

Create new Tag.

### HTTP Request

`POST localhost:8888/api/2/tags/`

### Required Parameters
Data format: application/json

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
value | string | new tag category |
project_id | integer | 1 |
tag_category_id | integer | 2 |

### Optional Parameters

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
description | string | more info |
description_loc_ids | list of localized_string_ids | 3,4 |
msg_loc_ids | list of localized_string_ids | 6,7 |
data | string | more data | useful place to store additional tag info
filter | enum | \_ten_most_recent_days | untested functionality allows for pseudo tags to be created by filtering rather than directly assigning
location | shape | --- | Tags will be filterable by location in the future, but aren't yet


## PATCH tags/:id/

```python
import requests

url = "http://localhost:8888/api/2/tags/7/"

payload = '{"value": "male"}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("PATCH", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request PATCH \
  --url http://localhost:8888/api/2/tags/7/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "value": "male"
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/tags/7/",
  "method": "PATCH",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"value": "male"}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 7,
  "value": "female",
  "description": "male",
  "data": "class=tag-one",
  "filter": "",
  "location": null,
  "project_id": 1,
  "tag_category_id": 3,
  "description_loc": [44,43],
  "msg_loc": "female",
  "relationships": []
}
```

Update Tag.

### HTTP Request

`PATCH localhost:8888/api/2/tags/:id/`

### Optional Parameters
Data format: `application/json`

Partial update allowed; params not included will leave field values unchanged.

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
value | string | new tag category |
project_id | integer | 1 |
tag_category_id | integer | 2 |
description | string | more info |
description_loc_ids | list of localized_string_ids | 3,4 |
msg_loc_ids | list of localized_string_ids | 6,7 |
data | string | more data | useful place to store additional tag info
filter | enum | \_ten_most_recent_days | untested functionality allows for pseudo tags to be created by filtering rather than directly assigning
location | shape | --- | Tags will be filterable by location in the future, but aren't yet


## DELETE tags/:id/

```python
import requests

url = "http://localhost:8888/api/2/tags//"

payload = ""
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
    }

response = requests.request("DELETE", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request DELETE \
  --url http://localhost:8888/api/2/tags/5/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/tags/5/",
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

`DELETE localhost:8888/api/2/tags/:id/`
