## Set approval flag

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

payload = "{\"approved\":false,\"comment\":\"It looks too cold!\"}"

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("POST", "/v2/files/meta/approval?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request POST \
  --url 'https://api.sirv.com/v2/files/meta/approval?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg' \
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \
  --header 'content-type: application/json' \
  --data '{"approved":false,"comment":"It looks too cold!"}'
```

```javascript--node
var http = require("https");

var options = {
  "method": "POST",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/files/meta/approval?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg",
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

req.write("{\"approved\":false,\"comment\":\"It looks too cold!\"}");
req.end();
```

```javascript
var data = "{\"approved\":false,\"comment\":\"It looks too cold!\"}";

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.sirv.com/v2/files/meta/approval?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.post("https://api.sirv.com/v2/files/meta/approval?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .body("{\"approved\":false,\"comment\":\"It looks too cold!\"}")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.sirv.com/v2/files/meta/approval?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"approved\":false,\"comment\":\"It looks too cold!\"}",
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

Use this API method to set the file approval tag (approved or not) and an optional comment. Used as part of an image review and approval process.

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
    "approved": {
      "examples": [
        false
      ],
      "example": false,
      "type": "boolean"
    },
    "comment": {
      "examples": [
        "It looks too cold!"
      ],
      "example": "It looks too cold!",
      "oneOf": [
        {
          "type": "string",
          "maxLength": 256
        }
      ]
    }
  },
  "additionalProperties": false,
  "patterns": [],
  "required": [
    "approved"
  ]
}
```


### Response

Example response:

<div class="center-column"></div>
```
< HTTP/1.1 200
< date: Fri, 17 Jul 2020 16:28:31 GMT
< content-length: 0
< connection: close
< x-ratelimit-limit: 7000
< x-ratelimit-remaining: 6974
< x-ratelimit-reset: 1595006894
< x-ratelimit-type: rest:global
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< server: Sirv.API
< strict-transport-security: max-age=31536000


```
