## Convert spin to video

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

payload = "{\"filename\":\"/REST API Examples/coin/coin.spin\",\"options\":{\"width\":1920,\"height\":1080,\"loops\":3}}"

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("POST", "/v2/files/spin2video", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request POST \
  --url https://api.sirv.com/v2/files/spin2video \
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \
  --header 'content-type: application/json' \
  --data '{"filename":"/REST API Examples/coin/coin.spin","options":{"width":1920,"height":1080,"loops":3}}'
```

```javascript--node
var http = require("https");

var options = {
  "method": "POST",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/files/spin2video",
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

req.write("{\"filename\":\"/REST API Examples/coin/coin.spin\",\"options\":{\"width\":1920,\"height\":1080,\"loops\":3}}");
req.end();
```

```javascript
var data = "{\"filename\":\"/REST API Examples/coin/coin.spin\",\"options\":{\"width\":1920,\"height\":1080,\"loops\":3}}";

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.sirv.com/v2/files/spin2video");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.post("https://api.sirv.com/v2/files/spin2video")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .body("{\"filename\":\"/REST API Examples/coin/coin.spin\",\"options\":{\"width\":1920,\"height\":1080,\"loops\":3}}")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.sirv.com/v2/files/spin2video",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"filename\":\"/REST API Examples/coin/coin.spin\",\"options\":{\"width\":1920,\"height\":1080,\"loops\":3}}",
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

Use this API method to convert a 360 spin into an MP4 video. You can specify the width/height of the video and the number of rotations. If it is a multi-row spin, you can also specify which row should be converted.

### Query string


None


### Body payload


<div class="center-column"></div>

```json
{
  "type": "object",
  "properties": {
    "filename": {
      "examples": [
        "/REST API Examples/coin/coin.spin"
      ],
      "example": "/REST API Examples/coin/coin.spin",
      "type": "string",
      "pattern": "^\\/",
      "maxLength": 1024
    },
    "options": {
      "type": "object",
      "properties": {
        "width": {
          "examples": [
            1920
          ],
          "example": 1920,
          "type": "number",
          "maximum": 1920
        },
        "height": {
          "examples": [
            1080
          ],
          "example": 1080,
          "type": "number",
          "maximum": 1080
        },
        "loops": {
          "examples": [
            3
          ],
          "example": 3,
          "type": "number",
          "maximum": 20
        },
        "row": {
          "enum": [
            "single",
            "all"
          ],
          "type": "string"
        }
      },
      "additionalProperties": false,
      "patterns": []
    }
  },
  "additionalProperties": false,
  "patterns": [],
  "required": [
    "filename"
  ]
}
```


### Response

Example response:

```
< HTTP/1.1 200
< date: Fri, 17 Jul 2020 15:39:33 GMT
< content-type: application/json; charset=utf-8
< content-length: 69
< connection: close
< x-ratelimit-limit: 200
< x-ratelimit-remaining: 198
< x-ratelimit-reset: 1595003813
< x-ratelimit-type: rest:post:files:spin2video
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< server: Sirv.API
< strict-transport-security: max-age=31536000

{
  "filename": "/REST API Examples/coin/coin_single_1920x1080.mp4"
}
```
