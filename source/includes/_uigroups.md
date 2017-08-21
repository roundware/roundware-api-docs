# uigroups/

### Definition:
UI Groups are used to group UI Items together in RW client user interfaces. UI Groups typically correspond to a Tag Category with UI Items corresponding to Tags within that Category.

## GET uigroups/

```python
import requests

url = "http://localhost:8888/api/2/uigroups/"

querystring = {"project_id": "1"}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/uigroups/?project_id=1' \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/uigroups/?project_id=1",
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
  "ui_groups": [
    {
      "id": 1,
      "name": "What genders do you want to listen to?",
      "ui_mode": "listen",
      "select": "min_one",
      "active": true,
      "index": 1,
      "header_text_loc": "What genders do you want to listen to?",
      "tag_category_id": 3,
      "project_id": 1,
      "ui_items": [
        {
          "id": 1,
          "index": 2,
          "default": true,
          "active": true,
          "ui_group_id": 1,
          "tag_id": 3,
          "parent_id": null
        },
        {
          "id": 2,
          "index": 1,
          "default": true,
          "active": true,
          "ui_group_id": 1,
          "tag_id": 4,
          "parent_id": null
        }
      ]
    },
    {
      "id": 7,
      "name": "Who do you want to hear?",
      "ui_mode": "listen",
      "select": "min_one",
      "active": true,
      "index": 2,
      "header_text_loc": "Who do you want to hear?",
      "tag_category_id": 4,
      "project_id": 1,
      "ui_items": [
        {
          "id": 15,
          "index": 1,
          "default": true,
          "active": true,
          "ui_group_id": 7,
          "tag_id": 8,
          "parent_id": null
        },
        {
          "id": 16,
          "index": 2,
          "default": true,
          "active": true,
          "ui_group_id": 7,
          "tag_id": 9,
          "parent_id": null
        }
      ]
    }
  ]
}
```

Get list of UI Groups.

### HTTP Request

`GET localhost:8888/api/2/uigroups/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
project_id | integer |
name | string | startswith filter
ui_mode | enum | OPTIONS: listen, speak, browse
tag_category_id | integer |
select | enum | OPTIONS: single, multi, min_one
active | boolean |
index | integer | imposes ordering in client UI

<aside class="success">
Note — Adding GET param <code>admin=1</code> to this request will provide all localized strings in response, not only English.
</aside>


## GET uigroups/:id/

```python
import requests

url = "http://localhost:8888/api/2/uigroups/2/"

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/uigroups/2/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/uigroups/2/",
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
  "name": "Who do you want to hear?",
  "ui_mode": "listen",
  "select": "min_one",
  "active": true,
  "index": 2,
  "header_text_loc": "Who do you want to hear?",
  "tag_category_id": 4,
  "project_id": 1,
  "ui_items": [
    {
      "id": 15,
      "index": 1,
      "default": true,
      "active": true,
      "ui_group_id": 2,
      "tag_id": 8,
      "parent_id": null
    },
    {
      "id": 16,
      "index": 2,
      "default": true,
      "active": true,
      "ui_group_id": 2,
      "tag_id": 9,
      "parent_id": null
    }
  ]
}
```

Get specific UI Group.

### HTTP Request

`GET localhost:8888/api/2/uigroups/2/`


## POST uigroups/

```python
import requests

url = "http://localhost:8888/api/2/uigroups/"

payload = '{"name": "What genders do you want to listen to?"","ui_mode": "listen","select": "min_one","active": true,"index": 1,"header_text_loc_ids": [42,41],"tag_category_id": 3,"project_id": 1}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url http://localhost:8888/api/2/uigroups/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
    "name": "What genders do you want to listen to?",
    "ui_mode": "listen",
    "select": "min_one",
    "active": true,
    "index": 1,
    "header_text_loc_ids": [42,41],
    "tag_category_id": 3,
    "project_id": 1
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/uigroups/",
  "method": "POST",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"name": "What genders do you want to listen to?"","ui_mode": "listen","select": "min_one","active": true,"index": 1,"header_text_loc_ids": [42,41],"tag_category_id": 3,"project_id": 1}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 15,
  "name": "What genders do you want to listen to?",
  "ui_mode": "listen",
  "select": "min_one",
  "active": true,
  "index": 1,
  "header_text_loc": "Leave feedback",
  "tag_category_id": 3,
  "project_id": 1,
  "ui_items": []
}
```

Create new UI Group.

### HTTP Request

`POST localhost:8888/api/2/uigroups/`

### Required Parameters
Data format: `application/json`

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
project_id | integer | 1 |
name | string | Name |
ui_mode | enum | listen | OPTIONS: listen, speak, browse
tag_category_id | integer | 2 |
select | enum | single | OPTIONS: single, multi, min_one
index | integer | 1 | imposes ordering in client UI

### Optional Parameters
Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
header_text_loc_ids | list of integers | 4,7 |
active | boolean | true | defaults to true


## PATCH uigroups/:id/

```python
import requests

url = "http://localhost:8888/api/2/uigroups/15/"

payload = '{"ui_mode": "speak"}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("PATCH", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request PATCH \
  --url http://localhost:8888/api/2/uigroups/15/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "ui_mode": "speak"
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/uigroups/15/",
  "method": "PATCH",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"ui_mode": "speak"}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 15,
  "name": "What genders do you want to listen to?",
  "ui_mode": "speak",
  "select": "min_one",
  "active": true,
  "index": 1,
  "header_text_loc": "Leave feedback",
  "tag_category_id": 3,
  "project_id": 1,
  "ui_items": []
}
```

Update UI Group.

### HTTP Request

`PATCH localhost:8888/api/2/uigroups/:id/`

### Optional Parameters
Data format: `application/json`

Partial update allowed; params not included will leave field values unchanged.

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
project_id | integer | 1 |
name | string | Name |
ui_mode | enum | listen | OPTIONS: listen, speak, browse
tag_category | integer | 2 |
select | enum | single | OPTIONS: single, multi, min_one
index | integer | 1 | imposes ordering in client UI
header_text_loc | string | Header text |
active | boolean | true | defaults to true


## DELETE uigroups/:id/

```python
import requests

url = "http://localhost:8888/api/2/uigroups/5/"

payload = ""
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
    }

response = requests.request("DELETE", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request DELETE \
  --url http://localhost:8888/api/2/uigroups/5/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/uigroups/5/",
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

Delete UI Group.

### HTTP Request

`DELETE localhost:8888/api/2/uigroups/:id/`
