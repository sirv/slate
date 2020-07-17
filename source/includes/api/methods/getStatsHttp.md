## Get transfer stats

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("GET", "/v2/stats/http?from=2020-07-01T00%3A00%3A00.000&to=2020-07-05T00%3A00%3A00.000", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url 'https://api.sirv.com/v2/stats/http?from=2020-07-01T00%3A00%3A00.000&to=2020-07-05T00%3A00%3A00.000' \
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \
  --header 'content-type: application/json'
```

```javascript--node
var http = require("https");

var options = {
  "method": "GET",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/stats/http?from=2020-07-01T00%3A00%3A00.000&to=2020-07-05T00%3A00%3A00.000",
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

xhr.open("GET", "https://api.sirv.com/v2/stats/http?from=2020-07-01T00%3A00%3A00.000&to=2020-07-05T00%3A00%3A00.000");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.get("https://api.sirv.com/v2/stats/http?from=2020-07-01T00%3A00%3A00.000&to=2020-07-05T00%3A00%3A00.000")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.sirv.com/v2/stats/http?from=2020-07-01T00%3A00%3A00.000&to=2020-07-05T00%3A00%3A00.000",
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

Use this API method to check how much data was transferred per day during a certain period (date from/to). The request returns aggregated HTTP log data.

### Query string


Parameter | Type | Description | Example
--------- | ---- | ----------- | ------- 
from | date | Default: 1 month ago, rounded to start of day | 2020-07-01T00:00:00.000
to | date | Default: now, rounded to end of day | 2020-07-05T00:00:00.000


### Body payload


None


### Response

Example response:

<div class="center-column"></div>
```
< HTTP/1.1 200
< date: Fri, 17 Jul 2020 16:28:17 GMT
< content-type: application/json; charset=utf-8
< content-length: 470
< connection: close
< x-ratelimit-limit: 100
< x-ratelimit-remaining: 99
< x-ratelimit-reset: 1595006896
< x-ratelimit-type: rest:get:stats:http
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< accept-ranges: bytes
< server: Sirv.API
< strict-transport-security: max-age=31536000

{
  "1593561600000": {
    "total": {
      "count": 47619,
      "size": 1440222650
    }
  },
  "1593648000000": {
    "total": {
      "count": 75944,
      "size": 2078130246
    }
  },
  "1593734400000": {
    "total": {
      "count": 44928,
      "size": 1248801543
    }
  },
  "1593820800000": {
    "total": {
      "count": 26472,
      "size": 727094151
    }
  },
  "1593907200000": {
    "total": {
      "count": 30528,
      "size": 877886049
    }
  }
}
```
