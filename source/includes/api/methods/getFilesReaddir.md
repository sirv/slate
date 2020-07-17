## Read folder contents

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("GET", "/v2/files/readdir?dirname=%2FREST%20API%20Examples", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \
  --url 'https://api.sirv.com/v2/files/readdir?dirname=%2FREST%20API%20Examples' \
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \
  --header 'content-type: application/json'
```

```javascript--node
var http = require("https");

var options = {
  "method": "GET",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/files/readdir?dirname=%2FREST%20API%20Examples",
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

xhr.open("GET", "https://api.sirv.com/v2/files/readdir?dirname=%2FREST%20API%20Examples");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.get("https://api.sirv.com/v2/files/readdir?dirname=%2FREST%20API%20Examples")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.sirv.com/v2/files/readdir?dirname=%2FREST%20API%20Examples",
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

Use this API method to check all the files within a folder. It will return the filename, mimetype, content type and file size. It will also return any folders that exist.

### Query string


Parameter | Type | Description | Example
--------- | ------- | ----------- 
dirname | string |  | /REST API Examples
continuation | string | Send it to get next page of results | 


### Body payload


None


### Response

Example response:

```
< HTTP/1.1 200
< date: Fri, 17 Jul 2020 15:39:38 GMT
< content-type: application/json; charset=utf-8
< content-length: 1380
< connection: close
< x-ratelimit-limit: 7000
< x-ratelimit-remaining: 6860
< x-ratelimit-reset: 1595003234
< x-ratelimit-type: rest:global
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< vary: accept-encoding
< accept-ranges: bytes
< server: Sirv.API
< strict-transport-security: max-age=31536000

{
  "contents": [
    {
      "filename": "blue-lake.jpg",
      "mtime": "2020-07-17T13:31:39.450Z",
      "contentType": "image/jpeg",
      "size": 587065,
      "isDirectory": false,
      "meta": {
        "width": 1578,
        "height": 1002,
        "duration": 0
      }
    },
    {
      "filename": "coin",
      "mtime": "2020-07-17T13:31:08.833Z",
      "size": 0,
      "isDirectory": true,
      "meta": {}
    },
    {
      "filename": "aurora.jpg",
      "mtime": "2020-07-17T13:31:39.464Z",
      "contentType": "image/jpeg",
      "size": 788807,
      "isDirectory": false,
      "meta": {
        "width": 2500,
        "height": 1667,
        "duration": 0
      }
    },
    {
      "filename": "birdbath.jpg",
      "mtime": "2020-07-17T13:31:39.385Z",
      "contentType": "image/jpeg",
      "size": 73151,
      "isDirectory": false,
      "meta": {
        "width": 620,
        "height": 372,
        "duration": 0
      }
    },
    {
      "filename": "video.mp4",
      "mtime": "2020-07-17T15:35:20.375Z",
      "contentType": "video/mp4",
      "size": 12860989,
      "isDirectory": false,
      "meta": {
        "width": 1372,
        "height": 1080,
        "duration": 33.434
      }
    },
    {
      "filename": "video",
      "mtime": "2020-07-17T15:36:52.477Z",
      "size": 0,
      "isDirectory": true,
      "meta": {}
    }
  ]
}
```
