## Add file meta tags

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

payload = "{\"tags\":[\"blue\",\"lake\",\"winter\",\"cold\",\"water\"]}"

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("POST", "/v2/files/meta/tags?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request POST \
  --url 'https://api.sirv.com/v2/files/meta/tags?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg' \
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \
  --header 'content-type: application/json' \
  --data '{"tags":["blue","lake","winter","cold","water"]}'
```

```javascript--node
var http = require("https");

var options = {
  "method": "POST",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/files/meta/tags?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg",
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

req.write("{\"tags\":[\"blue\",\"lake\",\"winter\",\"cold\",\"water\"]}");
req.end();
```

```javascript
var data = "{\"tags\":[\"blue\",\"lake\",\"winter\",\"cold\",\"water\"]}";

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.sirv.com/v2/files/meta/tags?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.post("https://api.sirv.com/v2/files/meta/tags?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .body("{\"tags\":[\"blue\",\"lake\",\"winter\",\"cold\",\"water\"]}")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.sirv.com/v2/files/meta/tags?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"tags\":[\"blue\",\"lake\",\"winter\",\"cold\",\"water\"]}",
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

Use this API method to add a meta tag to a file or folder.

### Query string


Parameter | Type | Description | Example
--------- | ------- | ----------- 
filename | string |  | /REST API Examples/blue-lake.jpg


### Body payload


<div class="center-column"></div>

```json
{
  "type": "object",
  "properties": {
    "tags": {
      "examples": [
        [
          "blue",
          "lake",
          "winter",
          "cold",
          "water"
        ]
      ],
      "example": [
        "blue",
        "lake",
        "winter",
        "cold",
        "water"
      ],
      "type": "array",
      "maxItems": 50,
      "items": {
        "type": "string"
      }
    }
  },
  "additionalProperties": false,
  "patterns": [],
  "required": [
    "tags"
  ]
}
```


### Response

Example response:

```
< HTTP/1.1 200
< date: Fri, 17 Jul 2020 15:39:36 GMT
< content-length: 0
< connection: close
< x-ratelimit-limit: 7000
< x-ratelimit-remaining: 6862
< x-ratelimit-reset: 1595003234
< x-ratelimit-type: rest:global
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< server: Sirv.API
< strict-transport-security: max-age=31536000


```
