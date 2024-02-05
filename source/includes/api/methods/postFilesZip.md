## Zip a batch of files or directories

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

payload = "{\"filenames\":[\"/REST API Examples/coin/coin_01.jpg\",\"/REST API Examples/coin/coin_02.jpg\"],\"zipFilename\":\"Sirv January 18, 2023.zip\"}"

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("POST", "/v2/files/zip", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request POST \\
  --url https://api.sirv.com/v2/files/zip \\
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \\
  --header 'content-type: application/json' \\
  --data '{"filenames":["/REST API Examples/coin/coin_01.jpg","/REST API Examples/coin/coin_02.jpg"],"zipFilename":"Sirv January 18, 2023.zip"}'
```

```javascript--node
const http = require("https");

const options = {
  "method": "POST",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/files/zip",
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

req.write("{\"filenames\":[\"/REST API Examples/coin/coin_01.jpg\",\"/REST API Examples/coin/coin_02.jpg\"],\"zipFilename\":\"Sirv January 18, 2023.zip\"}");
req.end();
```

```javascript
const data = "{\"filenames\":[\"/REST API Examples/coin/coin_01.jpg\",\"/REST API Examples/coin/coin_02.jpg\"],\"zipFilename\":\"Sirv January 18, 2023.zip\"}";

const xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.sirv.com/v2/files/zip");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.post("https://api.sirv.com/v2/files/zip")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .body("{\"filenames\":[\"/REST API Examples/coin/coin_01.jpg\",\"/REST API Examples/coin/coin_02.jpg\"],\"zipFilename\":\"Sirv January 18, 2023.zip\"}")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "https://api.sirv.com/v2/files/zip",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"filenames\":[\"/REST API Examples/coin/coin_01.jpg\",\"/REST API Examples/coin/coin_02.jpg\"],\"zipFilename\":\"Sirv January 18, 2023.zip\"}",
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

url = URI("https://api.sirv.com/v2/files/zip")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer BEARER_TOKEN_HERE'
request.body = "{\"filenames\":[\"/REST API Examples/coin/coin_01.jpg\",\"/REST API Examples/coin/coin_02.jpg\"],\"zipFilename\":\"Sirv January 18, 2023.zip\"}"

response = http.request(request)
puts response.read_body
```

```swift
import Foundation

let headers = [
  "content-type": "application/json",
  "authorization": "Bearer BEARER_TOKEN_HERE"
]

let postData = NSData(data: "{"filenames":["/REST API Examples/coin/coin_01.jpg","/REST API Examples/coin/coin_02.jpg"],"zipFilename":"Sirv January 18, 2023.zip"}".data(using: String.Encoding.utf8)!)

let request = NSMutableURLRequest(url: NSURL(string: "https://api.sirv.com/v2/files/zip")! as URL,
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
var client = new RestClient("https://api.sirv.com/v2/files/zip");
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("authorization", "Bearer BEARER_TOKEN_HERE");
request.AddParameter("application/json", "{\"filenames\":[\"/REST API Examples/coin/coin_01.jpg\",\"/REST API Examples/coin/coin_02.jpg\"],\"zipFilename\":\"Sirv January 18, 2023.zip\"}", ParameterType.RequestBody);
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

	url := "https://api.sirv.com/v2/files/zip"

	payload := strings.NewReader("{\"filenames\":[\"/REST API Examples/coin/coin_01.jpg\",\"/REST API Examples/coin/coin_02.jpg\"],\"zipFilename\":\"Sirv January 18, 2023.zip\"}")

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

Use this method to create a ZIP archive from the list of filenames

### Query string


None


### Body payload


Example:

<div class="center-column"></div>
```json
{
  "filenames": [
    "/REST API Examples/coin/coin_01.jpg",
    "/REST API Examples/coin/coin_02.jpg"
  ],
  "zipFilename": "Sirv January 18, 2023.zip"
}
```




JSON Schema:

<div class="center-column"></div>
```json
{
  "type": "object",
  "properties": {
    "filenames": {
      "type": "array",
      "examples": [
        [
          [
            "/REST API Examples/coin/coin_01.jpg",
            "/REST API Examples/coin/coin_02.jpg"
          ]
        ]
      ],
      "maxItems": 1000,
      "items": {
        "type": "string",
        "maxLength": 1024
      }
    },
    "zipFilename": {
      "type": "string",
      "examples": [
        "Sirv January 18, 2023.zip"
      ],
      "maxLength": 64
    }
  },
  "required": [
    "filenames"
  ],
  "additionalProperties": false
}
```


### Response

Example response:

<div class="center-column"></div>
```
< HTTP/1.1 200
< date: Mon, 05 Feb 2024 13:30:28 GMT
< content-type: application/json; charset=utf-8
< content-length: 46
< connection: close
< x-global-ratelimit-limit: 7000
< x-global-ratelimit-remaining: 6682
< x-global-ratelimit-reset: 1707142905
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< server: Sirv.API
< strict-transport-security: max-age=31536000

{
  "id": "emrXdtsZrBjPYlDawmhRDqWCXKSeqGUG"
}
```
