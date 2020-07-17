## Convert video to spin

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

payload = "{}"

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("POST", "/v2/video/toSpin", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request POST \
  --url https://api.sirv.com/v2/video/toSpin \
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \
  --header 'content-type: application/json' \
  --data '{}'
```

```javascript--node
var http = require("https");

var options = {
  "method": "POST",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/video/toSpin",
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

req.write("{}");
req.end();
```

```javascript
var data = "{}";

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.sirv.com/v2/video/toSpin");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.post("https://api.sirv.com/v2/video/toSpin")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .body("{}")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.sirv.com/v2/video/toSpin",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{}",
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

Use this API method to convert uploaded video file to spin

### Query string


None


### Body payload


<div class="center-column"></div>

```json
{
  "type": "object",
  "properties": {
    "uploadId": {
      "description": "ID of the file that was uploaded via resumable /v2/upload endpoint",
      "type": "string",
      "maxLength": 256
    },
    "spinDirname": {
      "description": "Target dirname for the spin files",
      "type": "string",
      "maxLength": 1024
    },
    "frames": {
      "description": "Number of frames in the spin",
      "type": "number",
      "maximum": 512
    },
    "stabilisation": {
      "description": "Enable video stabilisation",
      "type": "boolean"
    },
    "stabilisationVariant": {
      "description": "Select stabilisation algorithm v1 or v2",
      "default": 1,
      "type": "number",
      "minimum": 1,
      "maximum": 2
    },
    "wait": {
      "description": "Wait for final phase to complete",
      "default": true,
      "type": "boolean"
    },
    "v1fill": {
      "description": "Canvas fill method for stabilisation v1",
      "enum": [
        "crop",
        "mirror",
        "crystall",
        "ribs",
        "mix"
      ],
      "type": "string"
    },
    "v1smoothscale": {
      "description": "Smoothing of scale for stabilisation v1",
      "default": true,
      "type": "boolean"
    },
    "v1smoothangle": {
      "description": "Smoothing of angle for stabilisation v1",
      "default": true,
      "type": "boolean"
    },
    "v2accuracy": {
      "description": "Accuracy of shakiness detection for stabilisation v2",
      "default": 15,
      "type": "number",
      "minimum": 1,
      "maximum": 15
    },
    "v2smoothing": {
      "description": "Smoothing of camera movements for stabilisation v2",
      "default": 30,
      "type": "number",
      "minimum": 1,
      "maximum": 50
    }
  },
  "additionalProperties": false,
  "patterns": [],
  "required": [
    "uploadId",
    "spinDirname"
  ]
}
```


### Response

Example response:

```

```
