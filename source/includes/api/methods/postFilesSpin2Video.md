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
curl --request POST \\
  --url https://api.sirv.com/v2/files/spin2video \\
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \\
  --header 'content-type: application/json' \\
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

```ruby
require 'uri'
require 'net/http'
require 'openssl'

url = URI("https://api.sirv.com/v2/files/spin2video")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer BEARER_TOKEN_HERE'
request.body = "{\"filename\":\"/REST API Examples/coin/coin.spin\",\"options\":{\"width\":1920,\"height\":1080,\"loops\":3}}"

response = http.request(request)
puts response.read_body
```

```swift
import Foundation

let headers = [
  "content-type": "application/json",
  "authorization": "Bearer BEARER_TOKEN_HERE"
]

let postData = NSData(data: "{"filename":"/REST API Examples/coin/coin.spin","options":{"width":1920,"height":1080,"loops":3}}".data(using: String.Encoding.utf8)!)

let request = NSMutableURLRequest(url: NSURL(string: "https://api.sirv.com/v2/files/spin2video")! as URL,
                                        cachePolicy: .useProtocolCachePolicy,
                                    timeoutInterval: 10.0)
request.httpMethod = "POST"
request.allHTTPHeaderFields = headers
request.httpBody = postData as Data

let session = URLSession.shared
let dataTask = session.dataTask(with: request as URLRequest, completionHandler: { (data, response, error) -> Void in
  if (error != nil) {
    print(error)
  } else {
    let httpResponse = response as? HTTPURLResponse
    print(httpResponse)
  }
})

dataTask.resume()
```

```csharp
var client = new RestClient("https://api.sirv.com/v2/files/spin2video");
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("authorization", "Bearer BEARER_TOKEN_HERE");
request.AddParameter("application/json", "{\"filename\":\"/REST API Examples/coin/coin.spin\",\"options\":{\"width\":1920,\"height\":1080,\"loops\":3}}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://api.sirv.com/v2/files/spin2video"

	payload := strings.NewReader("{\"filename\":\"/REST API Examples/coin/coin.spin\",\"options\":{\"width\":1920,\"height\":1080,\"loops\":3}}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("content-type", "application/json")
	req.Header.Add("authorization", "Bearer BEARER_TOKEN_HERE")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

Use this API method to convert a 360 spin into an MP4 video. You can specify the width/height of the video and the number of rotations. If it is a multi-row spin, you can also specify which row should be converted.

### Query string


None


### Body payload


Example:

<div class="center-column"></div>
```json
{
  "filename": "/REST API Examples/coin/coin.spin",
  "options": {
    "width": 1920,
    "height": 1080,
    "loops": 3
  }
}
```



JSON Schema:

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

<div class="center-column"></div>
```
< HTTP/1.1 200
< date: Sat, 18 Jul 2020 11:46:04 GMT
< content-type: application/json; charset=utf-8
< content-length: 69
< connection: close
< x-ratelimit-limit: 200
< x-ratelimit-remaining: 196
< x-ratelimit-reset: 1595075486
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
