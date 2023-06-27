## Get JWT protected URL

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

payload = "{\"filename\":\"/REST API Examples/aurora.jpg\",\"key\":\"cIxWUYfCjRHAy1BpcoIVNI5TivXszVPq\",\"alias\":\"demo-jwt\",\"secureParams\":{\"w\":300,\"h\":300},\"expiresIn\":300}"

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("POST", "/v2/files/jwt", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request POST \\
  --url https://api.sirv.com/v2/files/jwt \\
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \\
  --header 'content-type: application/json' \\
  --data '{"filename":"/REST API Examples/aurora.jpg","key":"cIxWUYfCjRHAy1BpcoIVNI5TivXszVPq","alias":"demo-jwt","secureParams":{"w":300,"h":300},"expiresIn":300}'
```

```javascript--node
const http = require("https");

const options = {
  "method": "POST",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/files/jwt",
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

req.write("{\"filename\":\"/REST API Examples/aurora.jpg\",\"key\":\"cIxWUYfCjRHAy1BpcoIVNI5TivXszVPq\",\"alias\":\"demo-jwt\",\"secureParams\":{\"w\":300,\"h\":300},\"expiresIn\":300}");
req.end();
```

```javascript
const data = "{\"filename\":\"/REST API Examples/aurora.jpg\",\"key\":\"cIxWUYfCjRHAy1BpcoIVNI5TivXszVPq\",\"alias\":\"demo-jwt\",\"secureParams\":{\"w\":300,\"h\":300},\"expiresIn\":300}";

const xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.sirv.com/v2/files/jwt");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.post("https://api.sirv.com/v2/files/jwt")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .body("{\"filename\":\"/REST API Examples/aurora.jpg\",\"key\":\"cIxWUYfCjRHAy1BpcoIVNI5TivXszVPq\",\"alias\":\"demo-jwt\",\"secureParams\":{\"w\":300,\"h\":300},\"expiresIn\":300}")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "https://api.sirv.com/v2/files/jwt",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"filename\":\"/REST API Examples/aurora.jpg\",\"key\":\"cIxWUYfCjRHAy1BpcoIVNI5TivXszVPq\",\"alias\":\"demo-jwt\",\"secureParams\":{\"w\":300,\"h\":300},\"expiresIn\":300}",
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

url = URI("https://api.sirv.com/v2/files/jwt")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer BEARER_TOKEN_HERE'
request.body = "{\"filename\":\"/REST API Examples/aurora.jpg\",\"key\":\"cIxWUYfCjRHAy1BpcoIVNI5TivXszVPq\",\"alias\":\"demo-jwt\",\"secureParams\":{\"w\":300,\"h\":300},\"expiresIn\":300}"

response = http.request(request)
puts response.read_body
```

```swift
import Foundation

let headers = [
  "content-type": "application/json",
  "authorization": "Bearer BEARER_TOKEN_HERE"
]

let postData = NSData(data: "{"filename":"/REST API Examples/aurora.jpg","key":"cIxWUYfCjRHAy1BpcoIVNI5TivXszVPq","alias":"demo-jwt","secureParams":{"w":300,"h":300},"expiresIn":300}".data(using: String.Encoding.utf8)!)

let request = NSMutableURLRequest(url: NSURL(string: "https://api.sirv.com/v2/files/jwt")! as URL,
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
var client = new RestClient("https://api.sirv.com/v2/files/jwt");
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("authorization", "Bearer BEARER_TOKEN_HERE");
request.AddParameter("application/json", "{\"filename\":\"/REST API Examples/aurora.jpg\",\"key\":\"cIxWUYfCjRHAy1BpcoIVNI5TivXszVPq\",\"alias\":\"demo-jwt\",\"secureParams\":{\"w\":300,\"h\":300},\"expiresIn\":300}", ParameterType.RequestBody);
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

	url := "https://api.sirv.com/v2/files/jwt"

	payload := strings.NewReader("{\"filename\":\"/REST API Examples/aurora.jpg\",\"key\":\"cIxWUYfCjRHAy1BpcoIVNI5TivXszVPq\",\"alias\":\"demo-jwt\",\"secureParams\":{\"w\":300,\"h\":300},\"expiresIn\":300}")

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

JWT protection is a powerful way to protect your files from being seen without permission. Use this API method to generate a token that can be appended to a URL or set of URLs, allowing a file to be served. Without a valid token, requests for any file within a JWT protected folder will be denied.
Before using this method, you must enable JWT folder protection and obtain a key.
Read the documentation to learn how to enable and use JWT protection: https://sirv.com/help/json-web-token-protected-signed-url#enable-jwt-protection

### Query string


None


### Body payload


Example:

<div class="center-column"></div>
```json
{
  "filename": "/REST API Examples/aurora.jpg",
  "key": "cIxWUYfCjRHAy1BpcoIVNI5TivXszVPq",
  "alias": "demo-jwt",
  "secureParams": {
    "w": 300,
    "h": 300
  },
  "expiresIn": 300
}
```




JSON Schema:

<div class="center-column"></div>
```json
{
  "type": "object",
  "properties": {
    "filename": {
      "type": "string",
      "examples": [
        "/REST API Examples/aurora.jpg"
      ],
      "pattern": "^\\/",
      "maxLength": 1024
    },
    "key": {
      "type": "string",
      "examples": [
        "cIxWUYfCjRHAy1BpcoIVNI5TivXszVPq"
      ],
      "description": "Specify JWT secret"
    },
    "alias": {
      "type": "string",
      "examples": [
        "demo-jwt"
      ],
      "description": "Specify account alias if your account has multiple aliases"
    },
    "insecureParams": {
      "type": "object",
      "properties": {},
      "additionalProperties": false
    },
    "secureParams": {
      "type": "object",
      "examples": [
        {
          "w": 300,
          "h": 300
        }
      ],
      "properties": {},
      "additionalProperties": false
    },
    "expiresIn": {
      "type": "number",
      "examples": [
        300
      ],
      "description": "Token expiration time in seconds"
    }
  },
  "required": [
    "filename",
    "key",
    "expiresIn"
  ],
  "additionalProperties": false
}
```


### Response

Example response:

<div class="center-column"></div>
```
< HTTP/1.1 200
< date: Tue, 27 Jun 2023 10:10:19 GMT
< content-type: application/json; charset=utf-8
< content-length: 286
< connection: close
< x-global-ratelimit-limit: 7000
< x-global-ratelimit-remaining: 6967
< x-global-ratelimit-reset: 1687864194
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< server: Sirv.API
< strict-transport-security: max-age=31536000

{
  "url": "https://demo-jwt.sirv.com/REST API Examples/aurora.jpg?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhcmdzIjp7InciOjMwMCwiaCI6MzAwfSwiaWF0IjoxNjg3ODYwNjE5LCJleHAiOjE2ODc4NjA5MTksImF1ZCI6Ii9SRVNUIEFQSSBFeGFtcGxlcy9hdXJvcmEuanBnIn0.-6wTZUlW-8kp43lU8_MxSuSlx8MHf8XYtS8lSXRjtU0"
}
```
