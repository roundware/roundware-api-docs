# speakers/

### Definition:
A polygonal geographic zone within which a specific audio track or stream "broadcasts" continuously to listeners. Speakers can overlap, causing their audio to be mixed together accordingly. Volume attenuation happens linearly over a specified distance from the edge of the Speaker's defined zone.

## GET speakers/

```python
import requests

url = "http://localhost:8888/api/2/speakers/"

querystring = {"project_id":"1","activeyn":"true"}

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl --request GET \
  --url 'http://localhost:8888/api/2/speakers/?project_id=1&activeyn=true' \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/speakers/?project_id=1&activeyn=true",
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
    "activeyn": true,
    "code": "new",
    "maxvolume": 0.4,
    "minvolume": 0,
    "uri": "http://roundware.org:8000/scapes1.mp3",
    "backupuri": "http://roundware.org:8000/scapes3.mp3",
    "shape": {
      "type": "MultiPolygon",
      "coordinates": [
        [
          [
            [0,0],
            [0,10],
            [10,10],
            [10,0],
            [0,0]
          ]
        ]
      ]
    },
    "boundary": {
      "type": "MultiLineString",
      "coordinates": [
        [
          [0,0],
          [0,10],
          [10,10],
          [10,0],
          [0,0]
        ]
      ]
    },
    "attenuation_distance": 100,
    "attenuation_border": {
      "type": "LineString",
      "coordinates": [
        [ 0.0009131518699371853,0.0009205455301594167],
        [0.0009337239271925088,9.99912146712889],
        [9.99909287711822,9.999114357169784],
        [9.999113564532946,0.0009270542067677345],
        [0.0009131518699371853,0.0009205455301594167]
      ]
    },
    "project_id": 1
  }
]
```

Get list of Speakers.

### HTTP Request

`GET localhost:8888/api/2/speakers/`

### Optional Filters

Parameter | Format | Description/Notes
--------- | ------ | -----------------
project_id | integer |
activeyn | boolean |


## GET speakers/:id/

```python
import requests

url = "http://localhost:8888/api/2/speakers/1/"

headers = {'authorization': 'token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url http://localhost:8888/api/2/speakers/1/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/speakers/1/",
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
  "activeyn": true,
  "code": "new",
  "maxvolume": 0.4,
  "minvolume": 0,
  "uri": "http://roundware.org:8000/scapes1.mp3",
  "backupuri": "http://roundware.org:8000/scapes3.mp3",
  "shape": {
    "type": "MultiPolygon",
    "coordinates": [
      [
        [
          [0,0],
          [0,10],
          [10,10],
          [10,0],
          [0,0]
        ]
      ]
    ]
  },
  "boundary": {
    "type": "MultiLineString",
    "coordinates": [
      [
        [0,0],
        [0,10],
        [10,10],
        [10,0],
        [0,0]
      ]
    ]
  },
  "attenuation_distance": 100,
  "attenuation_border": {
    "type": "LineString",
    "coordinates": [
      [ 0.0009131518699371853,0.0009205455301594167],
      [0.0009337239271925088,9.99912146712889],
      [9.99909287711822,9.999114357169784],
      [9.999113564532946,0.0009270542067677345],
      [0.0009131518699371853,0.0009205455301594167]
    ]
  },
  "project_id": 1
}
```

Get specific Speaker.

### HTTP Request

`GET localhost:8888/api/2/speakers/1/`

## POST speakers/

```python
import requests

url = "http://localhost:8888/api/2/speakers/"

payload = '{"activeyn": true,"code": "new","maxvolume": 0.4,"minvolume": 0,"uri": "http://roundware.org:8000/scapes2.mp3","backupuri": "http://roundware.org:8000/scapes3.mp3","shape": {"type": "MultiPolygon","coordinates": [ [ [ [ 0, 0 ],[ 0, 10 ],[ 10, 10 ],[ 10, 0 ],[ 0, 0 ]] ] ]},"attenuation_distance": 100,"project_id": 1}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url http://localhost:8888/api/2/speakers/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "activeyn": true,
  "code": "new",
  "maxvolume": 0.4,
  "minvolume": 0,
  "uri": "http://roundware.org:8000/scapes2.mp3",
  "backupuri": "http://roundware.org:8000/scapes3.mp3",
  "shape": {
    "type": "MultiPolygon",
    "coordinates": [
      [
        [
          [ 0, 0 ],
          [ 0, 10 ],
          [ 10, 10 ],
          [ 10, 0 ],
          [ 0, 0 ]
        ]
      ]
    ]
  },
  "attenuation_distance": 100,
  "project_id": 1
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/speakers/",
  "method": "POST",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"activeyn": true,"code": "new","maxvolume": 0.4,"minvolume": 0,"uri": "http://roundware.org:8000/scapes2.mp3","backupuri": "http://roundware.org:8000/scapes3.mp3","shape": {"type": "MultiPolygon","coordinates": [ [ [ [ 0, 0 ],[ 0, 10 ],[ 10, 10 ],[ 10, 0 ],[ 0, 0 ]] ] ]},"attenuation_distance": 100,"project_id": 1}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 2,
  "activeyn": true,
  "code": "new",
  "maxvolume": 0.4,
  "minvolume": 0,
  "uri": "http://roundware.org:8000/scapes1.mp3",
  "backupuri": "http://roundware.org:8000/scapes3.mp3",
  "shape": {
    "type": "MultiPolygon",
    "coordinates": [
      [
        [
          [0,0],
          [0,10],
          [10,10],
          [10,0],
          [0,0]
        ]
      ]
    ]
  },
  "boundary": {
    "type": "MultiLineString",
    "coordinates": [
      [
        [0,0],
        [0,10],
        [10,10],
        [10,0],
        [0,0]
      ]
    ]
  },
  "attenuation_distance": 100,
  "attenuation_border": {
    "type": "LineString",
    "coordinates": [
      [ 0.0009131518699371853,0.0009205455301594167],
      [0.0009337239271925088,9.99912146712889],
      [9.99909287711822,9.999114357169784],
      [9.999113564532946,0.0009270542067677345],
      [0.0009131518699371853,0.0009205455301594167]
    ]
  },
  "project_id": 1
}
```

Create new Speaker.

### HTTP Request

`POST localhost:8888/api/2/speakers/`

### Required Parameters
Data format: application/json

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
project_id | integer | 1 |
code | string | CENTER | explanatory label
maxvolume | float | 0.5 | volume of speaker audio when unattenuated in relation to source volume
minvolume | float | 0.0 | volume of speaker audio when fully attenuated in relation to source volume
uri | string | http://my.site.com/audio.mp3 | location of speaker audio source
backupuri | string | http://my.site.com/backup.mp3 | if `uri` not available, this source will be used
shape | MultiPolygon | see sample code | must be closed shape, but can contain as many points as necessary
attenuation_distance | integer | 100 | in meters

### Optional Parameters

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
activeyn | boolean | true | defaults to false


## PATCH speakers/:id/

```python
import requests

url = "http://localhost:8888/api/2/speakers/2/"

payload = '{"maxvolume": 0.8}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("PATCH", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request PATCH \
  --url http://localhost:8888/api/2/speakers/2/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "maxvolume": 0.8
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/speakers/2/",
  "method": "PATCH",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"maxvolume": 0.8}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "id": 2,
  "activeyn": true,
  "code": "new",
  "maxvolume": 0.8,
  "minvolume": 0,
  "uri": "http://roundware.org:8000/scapes1.mp3",
  "backupuri": "http://roundware.org:8000/scapes3.mp3",
  "shape": {
    "type": "MultiPolygon",
    "coordinates": [
      [
        [
          [0,0],
          [0,10],
          [10,10],
          [10,0],
          [0,0]
        ]
      ]
    ]
  },
  "boundary": {
    "type": "MultiLineString",
    "coordinates": [
      [
        [0,0],
        [0,10],
        [10,10],
        [10,0],
        [0,0]
      ]
    ]
  },
  "attenuation_distance": 100,
  "attenuation_border": {
    "type": "LineString",
    "coordinates": [
      [ 0.0009131518699371853,0.0009205455301594167],
      [0.0009337239271925088,9.99912146712889],
      [9.99909287711822,9.999114357169784],
      [9.999113564532946,0.0009270542067677345],
      [0.0009131518699371853,0.0009205455301594167]
    ]
  },
  "project_id": 1
}
```

Update Speaker.

### HTTP Request

`PATCH localhost:8888/api/2/speakers/:id/`

### Optional Parameters
Data format: `application/json`

Partial update allowed; params not included will leave field values unchanged.

Parameter | Format | Sample | Description/Notes
--------- | ------ | ------ | -----------------
project_id | integer | 1 |
code | string | CENTER | explanatory label
maxvolume | float | 0.5 | volume of speaker audio when unattenuated in relation to source volume
minvolume | float | 0.0 | volume of speaker audio when fully attenuated in relation to source volume
uri | string | http://my.site.com/audio.mp3 | location of speaker audio source
backupuri | string | http://my.site.com/backup.mp3 | if `uri` not available, this source will be used
shape | MultiPolygon | see sample code | must be closed shape, but can contain as many points as necessary
attenuation_distance | integer | 100 | in meters
activeyn | boolean | true | defaults to false


## DELETE speakers/:id/

```python
import requests

url = "http://localhost:8888/api/2/speakers/3/"

payload = ""
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
    }

response = requests.request("DELETE", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request DELETE \
  --url http://localhost:8888/api/2/speakers/3/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/speakers/3/",
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

Delete Speaker

### HTTP Request

`DELETE localhost:8888/api/2/speakers/:id/`
