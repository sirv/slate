## Get bearer token

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

payload = "{\"clientId\":\"ZcnZNfzwRhQExoHFoGpxWJ4p2R\",\"clientSecret\":\"TM3d0CfXxusKMpH3x7kHJYD40qJIR3omTIGXP6wPPkXpIUKLEz/dOJ9v6LbXra3y67XsaGK7iQPmnAuD+fzj+Q==\"}"

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("POST", "/v2/token", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request POST \\
  --url https://api.sirv.com/v2/token \\
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \\
  --header 'content-type: application/json' \\
  --data '{"clientId":"ZcnZNfzwRhQExoHFoGpxWJ4p2R","clientSecret":"TM3d0CfXxusKMpH3x7kHJYD40qJIR3omTIGXP6wPPkXpIUKLEz/dOJ9v6LbXra3y67XsaGK7iQPmnAuD+fzj+Q=="}'
```

```javascript--node
const http = require("https");

const options = {
  "method": "POST",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/token",
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

req.write("{\"clientId\":\"ZcnZNfzwRhQExoHFoGpxWJ4p2R\",\"clientSecret\":\"TM3d0CfXxusKMpH3x7kHJYD40qJIR3omTIGXP6wPPkXpIUKLEz/dOJ9v6LbXra3y67XsaGK7iQPmnAuD+fzj+Q==\"}");
req.end();
```

```javascript
const data = "{\"clientId\":\"ZcnZNfzwRhQExoHFoGpxWJ4p2R\",\"clientSecret\":\"TM3d0CfXxusKMpH3x7kHJYD40qJIR3omTIGXP6wPPkXpIUKLEz/dOJ9v6LbXra3y67XsaGK7iQPmnAuD+fzj+Q==\"}";

const xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.sirv.com/v2/token");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.post("https://api.sirv.com/v2/token")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .body("{\"clientId\":\"ZcnZNfzwRhQExoHFoGpxWJ4p2R\",\"clientSecret\":\"TM3d0CfXxusKMpH3x7kHJYD40qJIR3omTIGXP6wPPkXpIUKLEz/dOJ9v6LbXra3y67XsaGK7iQPmnAuD+fzj+Q==\"}")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "https://api.sirv.com/v2/token",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"clientId\":\"ZcnZNfzwRhQExoHFoGpxWJ4p2R\",\"clientSecret\":\"TM3d0CfXxusKMpH3x7kHJYD40qJIR3omTIGXP6wPPkXpIUKLEz/dOJ9v6LbXra3y67XsaGK7iQPmnAuD+fzj+Q==\"}",
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

url = URI("https://api.sirv.com/v2/token")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer BEARER_TOKEN_HERE'
request.body = "{\"clientId\":\"ZcnZNfzwRhQExoHFoGpxWJ4p2R\",\"clientSecret\":\"TM3d0CfXxusKMpH3x7kHJYD40qJIR3omTIGXP6wPPkXpIUKLEz/dOJ9v6LbXra3y67XsaGK7iQPmnAuD+fzj+Q==\"}"

response = http.request(request)
puts response.read_body
```

```swift
import Foundation

let headers = [
  "content-type": "application/json",
  "authorization": "Bearer BEARER_TOKEN_HERE"
]

let postData = NSData(data: "{"clientId":"ZcnZNfzwRhQExoHFoGpxWJ4p2R","clientSecret":"TM3d0CfXxusKMpH3x7kHJYD40qJIR3omTIGXP6wPPkXpIUKLEz/dOJ9v6LbXra3y67XsaGK7iQPmnAuD+fzj+Q=="}".data(using: String.Encoding.utf8)!)

let request = NSMutableURLRequest(url: NSURL(string: "https://api.sirv.com/v2/token")! as URL,
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
var client = new RestClient("https://api.sirv.com/v2/token");
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("authorization", "Bearer BEARER_TOKEN_HERE");
request.AddParameter("application/json", "{\"clientId\":\"ZcnZNfzwRhQExoHFoGpxWJ4p2R\",\"clientSecret\":\"TM3d0CfXxusKMpH3x7kHJYD40qJIR3omTIGXP6wPPkXpIUKLEz/dOJ9v6LbXra3y67XsaGK7iQPmnAuD+fzj+Q==\"}", ParameterType.RequestBody);
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

	url := "https://api.sirv.com/v2/token"

	payload := strings.NewReader("{\"clientId\":\"ZcnZNfzwRhQExoHFoGpxWJ4p2R\",\"clientSecret\":\"TM3d0CfXxusKMpH3x7kHJYD40qJIR3omTIGXP6wPPkXpIUKLEz/dOJ9v6LbXra3y67XsaGK7iQPmnAuD+fzj+Q==\"}")

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

Every API call will be authenticated with a bearer token, so your first step is to obtain a bearer token.
Bearer tokens expire after 20 minutes (1200 seconds). If your token expires, request a new one, then continue with your work. After each API request you submit, you'll receive a response that contains useful information, including an expiresIn field (in seconds) telling you  how long remains before your bearer token expires.

### Query string


None


### Body payload


Example:

<div class="center-column"></div>
```json
{
  "clientId": "ZcnZNfzwRhQExoHFoGpxWJ4p2R",
  "clientSecret": "TM3d0CfXxusKMpH3x7kHJYD40qJIR3omTIGXP6wPPkXpIUKLEz/dOJ9v6LbXra3y67XsaGK7iQPmnAuD+fzj+Q=="
}
```




JSON Schema:

<div class="center-column"></div>
```json
{
  "type": "object",
  "properties": {
    "clientId": {
      "type": "string",
      "examples": [
        "ZcnZNfzwRhQExoHFoGpxWJ4p2R"
      ],
      "description": "API client ID"
    },
    "clientSecret": {
      "type": "string",
      "examples": [
        "TM3d0CfXxusKMpH3x7kHJYD40qJIR3omTIGXP6wPPkXpIUKLEz/dOJ9v6LbXra3y67XsaGK7iQPmnAuD+fzj+Q=="
      ],
      "description": "API client secret"
    }
  },
  "required": [
    "clientId",
    "clientSecret"
  ],
  "additionalProperties": false
}
```


### Response

Example response:

<div class="center-column"></div>
```
< HTTP/1.1 200
< date: Tue, 27 Jun 2023 10:09:54 GMT
< content-type: application/json; charset=utf-8
< content-length: 697
< connection: close
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< server: Sirv.API
< strict-transport-security: max-age=31536000

{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjbGllbnRJZCI6IlpjblpOZnp3UmhRRXhvSEZvR3B4V0o0cDJSIiwiY2xpZW50TmFtZSI6Ik15IHdlYnNpdGUiLCJzY29wZSI6WyJhY2NvdW50OnJlYWQiLCJhY2NvdW50OndyaXRlIiwidXNlcjpyZWFkIiwidXNlcjp3cml0ZSIsImJpbGxpbmc6cmVhZCIsImJpbGxpbmc6d3JpdGUiLCJmaWxlczpyZWFkIiwiZmlsZXM6d3JpdGUiLCJ2aWRlb3MiLCJpbWFnZXMiXSwiaWF0IjoxNjg3ODYwNTk0LCJleHAiOjE2ODc4NjE3OTQsImF1ZCI6Ijk1cnR2cGxuY3p1Y25sZ2llNm1qdXUyaWI3Z29ncXoyIn0.jnFixXD4uWOXq4qiDk7yvXyNfso2fv0VUUlubbMlfD4",
  "expiresIn": 1200,
  "scope": [
    "account:read",
    "account:write",
    "user:read",
    "user:write",
    "billing:read",
    "billing:write",
    "files:read",
    "files:write",
    "videos",
    "images"
  ]
}
```
