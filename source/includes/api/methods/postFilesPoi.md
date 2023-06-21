## Set point of interest

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

payload = "{\"name\":\"BlueLake\",\"x\":0.5,\"y\":0.5,\"width\":0.5,\"height\":0.5}"

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("POST", "/v2/files/poi", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request POST \\
  --url https://api.sirv.com/v2/files/poi \\
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \\
  --header 'content-type: application/json' \\
  --data '{"name":"BlueLake","x":0.5,"y":0.5,"width":0.5,"height":0.5}'
```

```javascript--node
const http = require("https");

const options = {
  "method": "POST",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/files/poi",
  "headers": {
    "content-type": "application/json",
    "authorization": "Bearer BEARER_TOKEN_HERE"
  }
};

const req = http.request(options, function (res) {
  const chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function () {
    const body = Buffer.concat(chunks);
    console.log(body.toString());
  });
});

req.write("{\"name\":\"BlueLake\",\"x\":0.5,\"y\":0.5,\"width\":0.5,\"height\":0.5}");
req.end();
```

```javascript
const data = "{\"name\":\"BlueLake\",\"x\":0.5,\"y\":0.5,\"width\":0.5,\"height\":0.5}";

const xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.sirv.com/v2/files/poi");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.post("https://api.sirv.com/v2/files/poi")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .body("{\"name\":\"BlueLake\",\"x\":0.5,\"y\":0.5,\"width\":0.5,\"height\":0.5}")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "https://api.sirv.com/v2/files/poi",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"name\":\"BlueLake\",\"x\":0.5,\"y\":0.5,\"width\":0.5,\"height\":0.5}",
  CURLOPT_HTTPHEADER => [
    "authorization: Bearer BEARER_TOKEN_HERE",
    "content-type: application/json"
  ],
]);

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

url = URI("https://api.sirv.com/v2/files/poi")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer BEARER_TOKEN_HERE'
request.body = "{\"name\":\"BlueLake\",\"x\":0.5,\"y\":0.5,\"width\":0.5,\"height\":0.5}"

response = http.request(request)
puts response.read_body
```

```swift
import Foundation

let headers = [
  "content-type": "application/json",
  "authorization": "Bearer BEARER_TOKEN_HERE"
]

let postData = NSData(data: "{"name":"BlueLake","x":0.5,"y":0.5,"width":0.5,"height":0.5}".data(using: String.Encoding.utf8)!)

let request = NSMutableURLRequest(url: NSURL(string: "https://api.sirv.com/v2/files/poi")! as URL,
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
var client = new RestClient("https://api.sirv.com/v2/files/poi");
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("authorization", "Bearer BEARER_TOKEN_HERE");
request.AddParameter("application/json", "{\"name\":\"BlueLake\",\"x\":0.5,\"y\":0.5,\"width\":0.5,\"height\":0.5}", ParameterType.RequestBody);
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

	url := "https://api.sirv.com/v2/files/poi"

	payload := strings.NewReader("{\"name\":\"BlueLake\",\"x\":0.5,\"y\":0.5,\"width\":0.5,\"height\":0.5}")

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

Use this API method to set coordinates of the POI (point of interest) on the image.

### Query string


Parameter | Type | Description | Example
--------- | ---- | ----------- | ------- 
filename | string |  | /REST API Examples/blue-lake.jpg


### Body payload


Example:

<div class="center-column"></div>
```json
{
  "name": "BlueLake",
  "x": 0.5,
  "y": 0.5,
  "width": 0.5,
  "height": 0.5
}
```




JSON Schema:

<div class="center-column"></div>
```json
{
  "type": "object",
  "properties": {
    "name": {
      "type": "string",
      "examples": [
        "BlueLake"
      ],
      "description": "Name of the POI",
      "maxLength": 16
    },
    "x": {
      "type": "number",
      "examples": [
        0.5
      ],
      "description": "Relative X coordinate of the center of the POI",
      "minimum": 0,
      "maximum": 1
    },
    "y": {
      "type": "number",
      "examples": [
        0.5
      ],
      "description": "Relative Y coordinate of the center of the POI",
      "minimum": 0,
      "maximum": 1
    },
    "width": {
      "type": "number",
      "examples": [
        0.5
      ],
      "description": "Relative width of the POI",
      "minimum": 0,
      "maximum": 1
    },
    "height": {
      "type": "number",
      "examples": [
        0.5
      ],
      "description": "Relative height of the POI",
      "minimum": 0,
      "maximum": 1
    }
  },
  "additionalProperties": false
}
```


### Response

Example response:

<div class="center-column"></div>
```
< HTTP/1.1 200
< date: Wed, 21 Jun 2023 15:47:23 GMT
< content-length: 0
< connection: close
< x-global-ratelimit-limit: 7000
< x-global-ratelimit-remaining: 6888
< x-global-ratelimit-reset: 1687364368
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< server: Sirv.API
< strict-transport-security: max-age=31536000

/ no response body: HTTP status 200 means SUCCESS /
```
