# users/

### Definition
Roundware uses Django Rest Framework token authorization. Roundware clients generate initial anonymous user accounts in order to retain the ease of use of not requiring an account sign-up process while benefitting from some of the security measures tokened accounts provide.

Users will be able to claim their accounts or register on initial startup in the future.

## POST users/

```python
import requests

url = "http://localhost:8888/api/2/users/"

payload = '{"device_id": "12345","client_type": "iPhone"}'
response = requests.request("POST", url, data=payload)

print(response.text)
```

```shell
curl --request POST \
  --url http://localhost:8888/api/2/users/ \
  --header 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
```

```javascript
var form = new FormData();

var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:8888/api/2/users/",
  "method": "POST",
  "headers": {},
  "processData": false,
  "contentType": false,
  "mimeType": "multipart/form-data",
  "data": form
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Sample JSON response:

```json
{
  "username": "14922898319281",
  "token": "4ee0fc210823c2c2f72f06e3fe862c0f6740d3b4"
}
```

This request either creates a new anonymous Roundware User and associated token if the provided `device_id` does not already exist, or otherwise returns the username and token already associated with the provided `device_id`.

### HTTP Request

`POST localhost:8888/api/2/users/`

### Request Parameters

Parameter | Sample Data | Default | Description/Notes
--------- | ----------- | ------- | -----------------
device_id* | 123456 | none | unique id generated on client and preferably consistent between sessions
client_type | iPhone | none |
client_system | iOS 10.2 | none |

<aside class="notice">
Remember — all other API requests require token authorization.
</aside>
