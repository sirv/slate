## Delete a batch of files or directories

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

payload = "{\"filenames\":[\"/REST API Examples/filename.jpg\",\"/REST API Examples/directory/\"]}"

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("POST", "/v2/files/batch/delete", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request POST \\
  --url https://api.sirv.com/v2/files/batch/delete \\
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \\
  --header 'content-type: application/json' \\
  --data '{"filenames":["/REST API Examples/filename.jpg","/REST API Examples/directory/"]}'
```

```javascript--node
const http = require("https");

const options = {
  "method": "POST",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/files/batch/delete",
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

req.write("{\"filenames\":[\"/REST API Examples/filename.jpg\",\"/REST API Examples/directory/\"]}");
req.end();
```

```javascript
const data = "{\"filenames\":[\"/REST API Examples/filename.jpg\",\"/REST API Examples/directory/\"]}";

const xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.sirv.com/v2/files/batch/delete");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.post("https://api.sirv.com/v2/files/batch/delete")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .body("{\"filenames\":[\"/REST API Examples/filename.jpg\",\"/REST API Examples/directory/\"]}")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "https://api.sirv.com/v2/files/batch/delete",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"filenames\":[\"/REST API Examples/filename.jpg\",\"/REST API Examples/directory/\"]}",
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

url = URI("https://api.sirv.com/v2/files/batch/delete")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer BEARER_TOKEN_HERE'
request.body = "{\"filenames\":[\"/REST API Examples/filename.jpg\",\"/REST API Examples/directory/\"]}"

response = http.request(request)
puts response.read_body
```

```swift
import Foundation

let headers = [
  "content-type": "application/json",
  "authorization": "Bearer BEARER_TOKEN_HERE"
]

let postData = NSData(data: "{"filenames":["/REST API Examples/filename.jpg","/REST API Examples/directory/"]}".data(using: String.Encoding.utf8)!)

let request = NSMutableURLRequest(url: NSURL(string: "https://api.sirv.com/v2/files/batch/delete")! as URL,
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
var client = new RestClient("https://api.sirv.com/v2/files/batch/delete");
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("authorization", "Bearer BEARER_TOKEN_HERE");
request.AddParameter("application/json", "{\"filenames\":[\"/REST API Examples/filename.jpg\",\"/REST API Examples/directory/\"]}", ParameterType.RequestBody);
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

	url := "https://api.sirv.com/v2/files/batch/delete"

	payload := strings.NewReader("{\"filenames\":[\"/REST API Examples/filename.jpg\",\"/REST API Examples/directory/\"]}")

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

Use this method to delete the list of filenames

### Query string


None


### Body payload


Example:

<div class="center-column"></div>
```json
{
  "filenames": [
    "/REST API Examples/filename.jpg",
    "/REST API Examples/directory/"
  ]
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
            "/REST API Examples/filename.jpg",
            "/REST API Examples/directory/"
          ]
        ]
      ],
      "maxItems": 1000,
      "items": {
        "type": "string",
        "maxLength": 1024
      }
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
< date: Thu, 24 Oct 2024 06:53:45 GMT
< content-type: application/json; charset=utf-8
< content-length: 46
< connection: close
< x-global-ratelimit-limit: 7000
< x-global-ratelimit-remaining: 6945
< x-global-ratelimit-reset: 1729756400
< x-ratelimit-limit: 25
< x-ratelimit-remaining: 24
< x-ratelimit-reset: 1729756425
< x-ratelimit-type: rest:post:files:batch:delete
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< server: Sirv.API
< strict-transport-security: max-age=31536000

{
  "id": "h02KtybW8LPV4MBaNFtqVswFybm0AQAl"
}
```
