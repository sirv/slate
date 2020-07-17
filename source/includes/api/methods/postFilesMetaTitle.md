## Set meta title

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

payload = "{\"title\":\"Blue Lake\"}"

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("POST", "/v2/files/meta/title?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request POST \
  --url 'https://api.sirv.com/v2/files/meta/title?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg' \
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \
  --header 'content-type: application/json' \
  --data '{"title":"Blue Lake"}'
```

```javascript--node
var http = require("https");

var options = {
  "method": "POST",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/files/meta/title?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg",
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

req.write("{\"title\":\"Blue Lake\"}");
req.end();
```

```javascript
var data = "{\"title\":\"Blue Lake\"}";

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.sirv.com/v2/files/meta/title?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.post("https://api.sirv.com/v2/files/meta/title?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .body("{\"title\":\"Blue Lake\"}")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.sirv.com/v2/files/meta/title?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"title\":\"Blue Lake\"}",
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

Use this API method to set the meta title of a file or folder.

### Query string


Parameter | Type | Description | Example
--------- | ---- | ----------- | ------- 
filename | string |  | /REST API Examples/blue-lake.jpg


### Body payload


JSON Schema:
<div class="center-column"></div>
```json
{
  "type": "object",
  "properties": {
    "title": {
      "examples": [
        "Blue Lake"
      ],
      "example": "Blue Lake",
      "type": "string"
    }
  },
  "additionalProperties": false,
  "patterns": [],
  "required": [
    "title"
  ]
}
```


### Response

Example response:

<div class="center-column"></div>
```
< HTTP/1.1 200
< date: Fri, 17 Jul 2020 16:28:30 GMT
< content-length: 0
< connection: close
< x-ratelimit-limit: 7000
< x-ratelimit-remaining: 6979
< x-ratelimit-reset: 1595006894
< x-ratelimit-type: rest:global
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< server: Sirv.API
< strict-transport-security: max-age=31536000


```
