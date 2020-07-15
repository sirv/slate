## Get storage info

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://api.sirv.com/v2/account/storage');
$request->setRequestMethod('GET');
$request->setHeaders(array(
  'authorization' => 'Bearer BEARER_TOKEN'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://api.sirv.com/v2/account/storage"

payload = ""
headers = {'authorization': 'Bearer BEARER_TOKEN'}

response = requests.request("GET", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request GET \
  --url https://api.sirv.com/v2/account/storage \
  --header 'authorization: Bearer BEARER_TOKEN'
```

```javascript
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "https://api.sirv.com/v2/account/storage");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN");

xhr.send(data);
```

```http
GET /v2/account/storage HTTP/1.1
Authorization: Bearer BEARER_TOKEN
Host: api.sirv.com
```

```javascript--node
var http = require("https");

var options = {
  "method": "GET",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/account/storage",
  "headers": {
    "content-length": "0",
    "authorization": "Bearer BEARER_TOKEN"
  }
};

var req = http.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function () {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });
});

req.end();
```

```java
HttpResponse<String> response = Unirest.get("https://api.sirv.com/v2/account/storage")
  .header("authorization", "Bearer BEARER_TOKEN")
  .asString();
```

Use this to check the current storage usage of an account. It will also return the total allowed storage; any extra storage provided; the temporary 30-day burstable storage allowance; the total files stored. If the account has exceeded its storage allowance, it will state the when that happened. If the account is one of a <a href="https://sirv.com/help/resources/multiple-sirv-accounts/"\>multi-account group</a>, it will show the total storage used by all accounts.

### Query Parameters

None

### Response:

Example JSON response:

<div class="center-column"></div>

```json
{
  "plan": 5000000000,
  "burstable": 0,
  "extra": 0,
  "used": 416569459,
  "files": 178,
  "quotaExceededDate": null
}
```
