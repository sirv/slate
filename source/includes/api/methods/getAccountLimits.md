## Get API limits

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("GET", "/v2/account/limits", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url https://api.sirv.com/v2/account/limits \
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \
  --header 'content-type: application/json'
```

```javascript--node
var http = require("https");

var options = {
  "method": "GET",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/account/limits",
  "headers": {
    "content-type": "application/json",
    "authorization": "Bearer BEARER_TOKEN_HERE"
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

```javascript
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "https://api.sirv.com/v2/account/limits");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.get("https://api.sirv.com/v2/account/limits")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.sirv.com/v2/account/limits",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "authorization: Bearer BEARER_TOKEN_HERE",
    "content-type: application/json"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

Use this method to check the allowed number of API requests and the number of requests used in the past 60 minutes.

### Query string


None


### Body payload


None


### Response

Example response:

<div class="center-column"></div>
```
< HTTP/1.1 200
< date: Fri, 17 Jul 2020 16:28:15 GMT
< content-type: application/json; charset=utf-8
< content-length: 2893
< connection: close
< x-ratelimit-limit: 7000
< x-ratelimit-remaining: 6995
< x-ratelimit-reset: 1595006894
< x-ratelimit-type: rest:global
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< vary: accept-encoding
< accept-ranges: bytes
< server: Sirv.API
< strict-transport-security: max-age=31536000

{
  "s3:global": {
    "count": 0,
    "limit": 7000,
    "remaining": 7000,
    "reset": 1595006895
  },
  "s3:PUT": {
    "count": 0,
    "limit": 2000,
    "remaining": 2000,
    "reset": 1595006895
  },
  "s3:GET": {
    "count": 0,
    "limit": 3000,
    "remaining": 3000,
    "reset": 1595006895
  },
  "s3:DELETE": {
    "count": 0,
    "limit": 3000,
    "remaining": 3000,
    "reset": 1595006895
  },
  "rest:global": {
    "count": 5,
    "limit": 7000,
    "remaining": 6995,
    "reset": 1595006894
  },
  "rest:post:files:search": {
    "count": 0,
    "limit": 1000,
    "remaining": 1000,
    "reset": 1595006895
  },
  "rest:post:files:search:scroll": {
    "count": 0,
    "limit": 2000,
    "remaining": 2000,
    "reset": 1595006895
  },
  "rest:post:files:video2spin": {
    "count": 5,
    "limit": 200,
    "remaining": 195,
    "reset": 1595003668
  },
  "rest:post:files:spin2video": {
    "count": 4,
    "limit": 200,
    "remaining": 196,
    "reset": 1595003813
  },
  "rest:post:files:fetch": {
    "count": 5,
    "limit": 2000,
    "remaining": 1995,
    "reset": 1595004455
  },
  "rest:post:files:upload": {
    "count": 0,
    "limit": 2000,
    "remaining": 2000,
    "reset": 1595006895
  },
  "rest:post:files:delete": {
    "count": 0,
    "limit": 3000,
    "remaining": 3000,
    "reset": 1595006895
  },
  "rest:post:account": {
    "count": 1,
    "limit": 50,
    "remaining": 49,
    "reset": 1595006894
  },
  "rest:post:account:fetching": {
    "count": 0,
    "limit": 50,
    "remaining": 50,
    "reset": 1595006895
  },
  "rest:get:stats:http": {
    "count": 0,
    "limit": 100,
    "remaining": 100,
    "reset": 1595006895
  },
  "rest:get:stats:storage": {
    "count": 0,
    "limit": 100,
    "remaining": 100,
    "reset": 1595006895
  },
  "rest:post:account:new": {
    "count": 0,
    "limit": 5,
    "remaining": 5,
    "reset": 1595006895
  },
  "rest:post:user:accounts": {
    "count": 0,
    "limit": 20,
    "remaining": 20,
    "reset": 1595006895
  },
  "rest:get:rest:credentials": {
    "count": 0,
    "limit": 50,
    "remaining": 50,
    "reset": 1595006895
  },
  "rest:post:video:toSpin": {
    "count": 0,
    "limit": 400,
    "remaining": 400,
    "reset": 1595006895
  },
  "rest:post:upload:toSirv": {
    "count": 0,
    "limit": 2000,
    "remaining": 2000,
    "reset": 1595006895
  },
  "ftp:global": {
    "count": 0,
    "limit": 10000,
    "remaining": 10000,
    "reset": 1595006895
  },
  "ftp:STOR": {
    "count": 0,
    "limit": 2000,
    "remaining": 2000,
    "reset": 1595006895
  },
  "ftp:RETR": {
    "count": 0,
    "limit": 3000,
    "remaining": 3000,
    "reset": 1595006895
  },
  "ftp:DELE": {
    "count": 0,
    "limit": 3000,
    "remaining": 3000,
    "reset": 1595006895
  },
  "fetch:file": {
    "count": 1,
    "limit": 2000,
    "remaining": 1999,
    "reset": 1595004456
  }
}
```
