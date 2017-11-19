# projectgroups/

### Definition:
Project Groups are used to group Projects for use in the transformer app. Instead of a single Project like traditional RW apps, the transformer app will have a single Project Group containing multiple projects, the availability of which are determined by the client's physical location.

## GET projectgroups/

```python
import requests

url = "http://localhost:8888/api/2/projectgroups/"

querystring = {"active":"true"}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/projectgroups/active=true' \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/projectgroups/?active=true",
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
        "name": "Smithsonian",
        "active": true,
        "description": "All projects managed by Smithsonian and included in the Smithsonian Roundware app.",
        "project_ids": [3,6,9,13,2]
    },
    {
        "id": 3,
        "name": "Halsey's Art Projects",
        "active": true,
        "description": "A group of cool art projects.",
        "project_ids": [1,4,5]
    },
]
```

Get list of Project Groups.

### HTTP Request

`GET localhost:8888/api/2/projectgroups/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
active | boolean |
name | string | contains and case-insensitive


## GET projectgroups/:id/

```python
import requests

url = "http://localhost:8888/api/2/projectgroups/3/"

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/projectgroups/3/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/projectgroups/3/",
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
    "id": 3,
    "name": "Halsey's Art Projects",
    "active": true,
    "description": "A group of cool art projects.",
    "project_ids": [1,4,5]
}
```

Get specific Project Group.

### HTTP Request

`GET localhost:8888/api/2/projectgroups/2/`


## POST projectgroups/

```python
import requests

url = "http://localhost:8888/api/2/projectgroups/"

payload = '{"name": "new project group", "active": "true", "description": "new project group description", "project_ids": [1,4,5]}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url http://localhost:8888/api/2/projectgroups/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "name": "new project group",
  "active": "true",
  "description": "new project group description",
  "project_ids": [1,4,5]
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/projectgroups/",
  "method": "POST",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"name": "new project group", "active": "true", "description": "new project group description", "project_ids": [1,4,5]}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
    "id": 3,
    "name": "new project group",
    "active": true,
    "description": "new project group description",
    "project_ids": [1,4,5]
}
```

Create new Project Group.

### HTTP Request

`POST localhost:8888/api/2/projectgroups/`

### Required Parameters
Data format: `application/json`

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
name | string | new project group |

### Optional Parameters

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
active | boolean | false | default = true
description | string | cool group |
project_ids | array of ids |


## PATCH projectgroups/:id/

```python
import requests

url = "http://localhost:8888/api/2/projectgroups/5/"

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
  --url http://localhost:8888/api/2/projectgroups/5/ \
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
  "url": "http://localhost:8888/api/2/projectgroups/5/",
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
    "active": true,
    "description": "new project group description",
    "project_ids": [2,7,8,9]
}
```

Update Project Group.

### HTTP Request

`PATCH localhost:8888/api/2/projectgroups/:id/`

### Optional Parameters
Data format: `application/json`

Partial update allowed; params not included will leave field values unchanged.

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
name | string | new project group |
active | boolean | false | default = true
description | string | cool group |
project_ids | array of ids |


## DELETE projectgroups/:id/

```python
import requests

url = "http://localhost:8888/api/2/projectgroups/5/"

payload = ""
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
    }

response = requests.request("DELETE", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request DELETE \
  --url http://localhost:8888/api/2/projectgroups/5/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/projectgroups/5/",
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

Delete Project Group

### HTTP Request

`DELETE localhost:8888/api/2/projectgroups/:id/`


## GET projectgroups/:id/projects/

```python
import requests

url = "http://localhost:8888/api/2/projectgroups/3/projects/"

querystring = {"latitude":"1.2345","longitude":"1.3456","language_code":"es"}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/projectgroups/3/projects/?latitude=1.2345&longitude=1.3456&language_code=es \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/projectgroups/3/projects/?latitude=1.2345&longitude=1.3456&language_code=es",
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
        "name": "Stories from Main Street",
        "owner": "Museums on Main Street",
        "description_loc": "Life in small town America.",
        "project_id": 6,
        "thumbnail_url": "rwmedia/project-6-thumb.png"
    },
    {
        "name": "World Heritage",
        "owner": "UNESCO",
        "description_loc": "UNESCO sites.",
        "project_id": 13,
        "thumbnail_url": "rwmedia/project-13-thumb.png"
    },
    {
        "name": "Access American Stories",
        "owner": "National Museum of American History",
        "description_loc": "Visual descriptions.",
        "project_id": 2,
        "thumbnail_url": "rwmedia/project-2-thumb.png"
    }
]
```

Get list of available Projects in specified Project Group at client location. Global listen Projects in Project Group are included regardless of location.

### HTTP Request

`GET localhost:8888/api/2/projectgroups/2/projects/`
