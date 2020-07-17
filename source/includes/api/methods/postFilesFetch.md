## Fetch URL

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

payload = "[{\"url\":\"https://demo.sirv.com/aurora.jpg\",\"filename\":\"/REST API Examples/aurora.jpg\"}]"

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("POST", "/v2/files/fetch", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request POST \
  --url https://api.sirv.com/v2/files/fetch \
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \
  --header 'content-type: application/json' \
  --data '[{"url":"https://demo.sirv.com/aurora.jpg","filename":"/REST API Examples/aurora.jpg"}]'
```

```javascript--node
var http = require("https");

var options = {
  "method": "POST",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/files/fetch",
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

req.write("[{\"url\":\"https://demo.sirv.com/aurora.jpg\",\"filename\":\"/REST API Examples/aurora.jpg\"}]");
req.end();
```

```javascript
var data = "[{\"url\":\"https://demo.sirv.com/aurora.jpg\",\"filename\":\"/REST API Examples/aurora.jpg\"}]";

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.sirv.com/v2/files/fetch");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.post("https://api.sirv.com/v2/files/fetch")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .body("[{\"url\":\"https://demo.sirv.com/aurora.jpg\",\"filename\":\"/REST API Examples/aurora.jpg\"}]")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.sirv.com/v2/files/fetch",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "[{\"url\":\"https://demo.sirv.com/aurora.jpg\",\"filename\":\"/REST API Examples/aurora.jpg\"}]",
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

Use this API method to fetch a file from a URL via HTTP and save it to your Sirv account. This can be any URL, either public or private (via HTTP authentication). In the url parameter, enter the full URL of the remote file. In the filename parameter, enter the folder path and filename where it should be saved e.g. /path/to/folder/new-filename.jpg.

### Query string


None


### Body payload


JSON Schema:
<div class="center-column"></div>

```json
{
  "type": "array",
  "maxItems": 20,
  "items": {
    "type": "object",
    "properties": {
      "url": {
        "examples": [
          "https://demo.sirv.com/aurora.jpg"
        ],
        "example": "https://demo.sirv.com/aurora.jpg",
        "type": "string",
        "maxLength": 1024
      },
      "filename": {
        "examples": [
          "/REST API Examples/aurora.jpg"
        ],
        "example": "/REST API Examples/aurora.jpg",
        "type": "string",
        "pattern": "^\\/",
        "maxLength": 1024
      },
      "auth": {
        "type": "object",
        "properties": {
          "username": {
            "type": "string",
            "maxLength": 256
          },
          "password": {
            "type": "string",
            "maxLength": 256
          }
        },
        "additionalProperties": false,
        "patterns": []
      },
      "wait": {
        "type": "boolean"
      }
    },
    "additionalProperties": false,
    "patterns": [],
    "required": [
      "url",
      "filename"
    ]
  }
}
```


### Response

Example response:

```
< HTTP/1.1 200
< date: Fri, 17 Jul 2020 15:49:57 GMT
< content-type: application/json; charset=utf-8
< content-length: 1681
< connection: close
< x-ratelimit-limit: 2000
< x-ratelimit-remaining: 1997
< x-ratelimit-reset: 1595004455
< x-ratelimit-type: rest:post:files:fetch
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< vary: accept-encoding
< server: Sirv.API
< strict-transport-security: max-age=31536000

[
  {
    "filename": "/REST API Examples/aurora.jpg",
    "success": true,
    "attempted": false,
    "attempts": [
      {
        "url": "https://demo.sirv.com/aurora.jpg",
        "initiator": {
          "type": "api",
          "remoteAddr": "176.105.166.4",
          "date": "2020-07-17T15:47:35.316Z"
        },
        "statusCode": 200,
        "headers": {
          "result": {
            "version": "HTTP/1.1",
            "code": 200,
            "reason": "OK"
          },
          "Date": "Fri, 17 Jul 2020 15:47:36 GMT",
          "Content-Type": "image/webp",
          "Content-Length": "201846",
          "Connection": "keep-alive",
          "Last-Modified": "Fri, 17 Jul 2020 15:47:36 GMT",
          "ETag": "\"5f11c818-31476\"",
          "Server": "Sirv.Imagination",
          "X-Sirv-Server": "c1-extra1-fireball-13",
          "X-Sirv-Cache": "MISS",
          "Access-Control-Allow-Origin": "*",
          "Access-Control-Allow-Headers": "*",
          "Expires": "Sun, 16 Aug 2020 15:47:36 GMT",
          "Cache-Control": "max-age=2592000",
          "X-Sirv-Meta-Width": "2500",
          "X-Sirv-Meta-Height": "1667",
          "X-Sirv-Shard": "c1-riak1",
          "X-Account-Id": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
          "X-File-VersionId": "5evxYG8lnBgeA7cGBRTZzq7JQolRYviN:0",
          "X-Account-Serial": "2020-06-15T19:18:53.901Z",
          "Accept-Ranges": "bytes"
        },
        "timing": {
          "ns": 0.007514,
          "connect": 0.007912,
          "start": 0.48724,
          "total": 0.489622
        },
        "date": "2020-07-17T15:47:36.712Z"
      }
    ],
    "retryAfter": "2020-07-18T15:47:36.712Z"
  }
]
```
