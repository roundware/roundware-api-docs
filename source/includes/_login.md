# login/

### Definition
In addition to the built-in Django Admin, Roundware uses an Angular-based web admin system that is designed to provide a more user-friendly interface to the higher-level Roundware features. Web Admin users can do all the basic setup and content management required to initiate and maintain a Roundware installation, but may still need the Django admin for certain lower-level tasks.

The RW Web Admin uses the standard Django Authorization system, so the `login/` endpoint was created to authorize users by taking `username` and `password` and returning the associated `token` which is used for future api requests. Users must be designated as Staff in the auth system in order to login into the Web Admin. Code for the Web Admin is in a separate repository and can be found here: [GitHub - Roundware Admin](https://github.com/roundware/roundware-admin)

## POST login/

```python
import requests

url = "http://localhost:8888/api/2/login/"

payload = '{"username": "round","password": "round"}'
headers = {
    'authorization': "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    'content-type': "application/json"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url http://localhost:8888/api/2/login/ \
  --header 'authorization: token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4' \
  --header 'content-type: application/json' \
  --data '{
  "username": "round",
  "password": "round"
}'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/login/",
  "method": "POST",
  "headers": {
    "authorization": "token 4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4",
    "content-type": "application/json"
  },
  "processData": false,
  "data": '{"username": "round","password": "round"}'
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "token": "4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
}
```

### HTTP Request

`POST localhost:8888/api/2/login/`

### Required Parameters
Data format: `application/json`

Parameter | Sample Data | Default | Description/Notes
--------- | ----------- | ------- | -----------------
username | round | string | as found in Django auth
password | round | string | as found in Django auth
