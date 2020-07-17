## Set product meta

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

payload = "{\"id\":\"LLBB77\",\"name\":\"Blue Lake Card\",\"brand\":\"BLUE LAKE LLC\",\"category1\":\"Cards\",\"category2\":\"Lakes\"}"

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("POST", "/v2/files/meta/product?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request POST \
  --url 'https://api.sirv.com/v2/files/meta/product?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg' \
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \
  --header 'content-type: application/json' \
  --data '{"id":"LLBB77","name":"Blue Lake Card","brand":"BLUE LAKE LLC","category1":"Cards","category2":"Lakes"}'
```

```javascript--node
var http = require("https");

var options = {
  "method": "POST",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/files/meta/product?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg",
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

req.write("{\"id\":\"LLBB77\",\"name\":\"Blue Lake Card\",\"brand\":\"BLUE LAKE LLC\",\"category1\":\"Cards\",\"category2\":\"Lakes\"}");
req.end();
```

```javascript
var data = "{\"id\":\"LLBB77\",\"name\":\"Blue Lake Card\",\"brand\":\"BLUE LAKE LLC\",\"category1\":\"Cards\",\"category2\":\"Lakes\"}";

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.sirv.com/v2/files/meta/product?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.post("https://api.sirv.com/v2/files/meta/product?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .body("{\"id\":\"LLBB77\",\"name\":\"Blue Lake Card\",\"brand\":\"BLUE LAKE LLC\",\"category1\":\"Cards\",\"category2\":\"Lakes\"}")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.sirv.com/v2/files/meta/product?filename=%2FREST%20API%20Examples%2Fblue-lake.jpg",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"id\":\"LLBB77\",\"name\":\"Blue Lake Card\",\"brand\":\"BLUE LAKE LLC\",\"category1\":\"Cards\",\"category2\":\"Lakes\"}",
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

Use this API method to set product meta fields for an image. This can be used by retailers for organizing images into product groups for an ecommerce store.

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
    "id": {
      "examples": [
        "LLBB77"
      ],
      "example": "LLBB77",
      "type": "string",
      "maxLength": 256
    },
    "name": {
      "examples": [
        "Blue Lake Card"
      ],
      "example": "Blue Lake Card",
      "type": "string",
      "maxLength": 256
    },
    "brand": {
      "examples": [
        "BLUE LAKE LLC"
      ],
      "example": "BLUE LAKE LLC",
      "type": "string",
      "maxLength": 256
    },
    "category1": {
      "examples": [
        "Cards"
      ],
      "example": "Cards",
      "type": "string",
      "maxLength": 256
    },
    "category2": {
      "examples": [
        "Lakes"
      ],
      "example": "Lakes",
      "type": "string",
      "maxLength": 256
    }
  },
  "additionalProperties": false,
  "patterns": []
}
```


### Response

Example response:

<div class="center-column"></div>

```
< HTTP/1.1 200
< date: Fri, 17 Jul 2020 16:23:57 GMT
< content-length: 0
< connection: close
< x-ratelimit-limit: 7000
< x-ratelimit-remaining: 6798
< x-ratelimit-reset: 1595003234
< x-ratelimit-type: rest:global
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< server: Sirv.API
< strict-transport-security: max-age=31536000


```
