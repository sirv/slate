## Export spin to Grainger

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

payload = "{\"filename\":\"/REST API Examples/coin/coin.spin\",\"sku\":\"SKU1234\"}"

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("POST", "/v2/files/spin2grainger360", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request POST \\
  --url https://api.sirv.com/v2/files/spin2grainger360 \\
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \\
  --header 'content-type: application/json' \\
  --data '{"filename":"/REST API Examples/coin/coin.spin","sku":"SKU1234"}'
```

```javascript--node
var http = require("https");

var options = {
  "method": "POST",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/files/spin2grainger360",
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

req.write("{\"filename\":\"/REST API Examples/coin/coin.spin\",\"sku\":\"SKU1234\"}");
req.end();
```

```javascript
var data = "{\"filename\":\"/REST API Examples/coin/coin.spin\",\"sku\":\"SKU1234\"}";

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.sirv.com/v2/files/spin2grainger360");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.post("https://api.sirv.com/v2/files/spin2grainger360")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .body("{\"filename\":\"/REST API Examples/coin/coin.spin\",\"sku\":\"SKU1234\"}")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.sirv.com/v2/files/spin2grainger360",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"filename\":\"/REST API Examples/coin/coin.spin\",\"sku\":\"SKU1234\"}",
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

url = URI("https://api.sirv.com/v2/files/spin2grainger360")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer BEARER_TOKEN_HERE'
request.body = "{\"filename\":\"/REST API Examples/coin/coin.spin\",\"sku\":\"SKU1234\"}"

response = http.request(request)
puts response.read_body
```

```swift
import Foundation

let headers = [
  "content-type": "application/json",
  "authorization": "Bearer BEARER_TOKEN_HERE"
]

let postData = NSData(data: "{"filename":"/REST API Examples/coin/coin.spin","sku":"SKU1234"}".data(using: String.Encoding.utf8)!)

let request = NSMutableURLRequest(url: NSURL(string: "https://api.sirv.com/v2/files/spin2grainger360")! as URL,
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
var client = new RestClient("https://api.sirv.com/v2/files/spin2grainger360");
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("authorization", "Bearer BEARER_TOKEN_HERE");
request.AddParameter("application/json", "{\"filename\":\"/REST API Examples/coin/coin.spin\",\"sku\":\"SKU1234\"}", ParameterType.RequestBody);
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

	url := "https://api.sirv.com/v2/files/spin2grainger360"

	payload := strings.NewReader("{\"filename\":\"/REST API Examples/coin/coin.spin\",\"sku\":\"SKU1234\"}")

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

This API method will generate a zip file containing 360 spin images that meet Grainger's requirements for format and file naming. The response will contain the zip file URL.

You must know the Grainger SKU to use this 360 spin zip method.

### Query string


None


### Body payload


Example:

<div class="center-column"></div>
```json
{
  "filename": "/REST API Examples/coin/coin.spin",
  "sku": "SKU1234"
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
    "sku": {
      "description": "Grainger SKU",
      "examples": [
        "SKU1234"
      ],
      "example": "SKU1234",
      "type": "string",
      "maxLength": 64
    }
  },
  "additionalProperties": false,
  "patterns": [],
  "required": [
    "filename",
    "sku"
  ]
}
```


### Response

Example response:

<div class="center-column"></div>
```
< HTTP/1.1 200
< date: Thu, 26 Aug 2021 14:04:41 GMT
< content-type: application/json; charset=utf-8
< content-length: 55
< connection: close
< x-ratelimit-limit: 7000
< x-ratelimit-remaining: 6959
< x-ratelimit-reset: 1629990234
< x-ratelimit-type: rest:global
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< server: Sirv.API
< strict-transport-security: max-age=31536000

{
  "filename": "/REST API Examples/coin/SKU1234.zip"
}
```
