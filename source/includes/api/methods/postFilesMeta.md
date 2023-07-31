## Set file meta all at once

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

payload = "{\"tags\":[\"lake\",\"water\"],\"title\":\"Blue Lake\",\"description\":\"Blue Lake in the Winter\",\"product\":{\"id\":\"LLBB77\",\"name\":\"Blue Lake Card\",\"brand\":\"BLUE LAKE LLC\",\"category1\":\"Cards\",\"category2\":\"Lakes\"},\"approval\":{\"approved\":false,\"comment\":\"It looks too cold!\"}}"

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("POST", "/v2/files/meta", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request POST \\
  --url https://api.sirv.com/v2/files/meta \\
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \\
  --header 'content-type: application/json' \\
  --data '{"tags":["lake","water"],"title":"Blue Lake","description":"Blue Lake in the Winter","product":{"id":"LLBB77","name":"Blue Lake Card","brand":"BLUE LAKE LLC","category1":"Cards","category2":"Lakes"},"approval":{"approved":false,"comment":"It looks too cold!"}}'
```

```javascript--node
const http = require("https");

const options = {
  "method": "POST",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/files/meta",
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

req.write("{\"tags\":[\"lake\",\"water\"],\"title\":\"Blue Lake\",\"description\":\"Blue Lake in the Winter\",\"product\":{\"id\":\"LLBB77\",\"name\":\"Blue Lake Card\",\"brand\":\"BLUE LAKE LLC\",\"category1\":\"Cards\",\"category2\":\"Lakes\"},\"approval\":{\"approved\":false,\"comment\":\"It looks too cold!\"}}");
req.end();
```

```javascript
const data = "{\"tags\":[\"lake\",\"water\"],\"title\":\"Blue Lake\",\"description\":\"Blue Lake in the Winter\",\"product\":{\"id\":\"LLBB77\",\"name\":\"Blue Lake Card\",\"brand\":\"BLUE LAKE LLC\",\"category1\":\"Cards\",\"category2\":\"Lakes\"},\"approval\":{\"approved\":false,\"comment\":\"It looks too cold!\"}}";

const xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.sirv.com/v2/files/meta");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.post("https://api.sirv.com/v2/files/meta")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .body("{\"tags\":[\"lake\",\"water\"],\"title\":\"Blue Lake\",\"description\":\"Blue Lake in the Winter\",\"product\":{\"id\":\"LLBB77\",\"name\":\"Blue Lake Card\",\"brand\":\"BLUE LAKE LLC\",\"category1\":\"Cards\",\"category2\":\"Lakes\"},\"approval\":{\"approved\":false,\"comment\":\"It looks too cold!\"}}")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "https://api.sirv.com/v2/files/meta",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"tags\":[\"lake\",\"water\"],\"title\":\"Blue Lake\",\"description\":\"Blue Lake in the Winter\",\"product\":{\"id\":\"LLBB77\",\"name\":\"Blue Lake Card\",\"brand\":\"BLUE LAKE LLC\",\"category1\":\"Cards\",\"category2\":\"Lakes\"},\"approval\":{\"approved\":false,\"comment\":\"It looks too cold!\"}}",
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

url = URI("https://api.sirv.com/v2/files/meta")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer BEARER_TOKEN_HERE'
request.body = "{\"tags\":[\"lake\",\"water\"],\"title\":\"Blue Lake\",\"description\":\"Blue Lake in the Winter\",\"product\":{\"id\":\"LLBB77\",\"name\":\"Blue Lake Card\",\"brand\":\"BLUE LAKE LLC\",\"category1\":\"Cards\",\"category2\":\"Lakes\"},\"approval\":{\"approved\":false,\"comment\":\"It looks too cold!\"}}"

response = http.request(request)
puts response.read_body
```

```swift
import Foundation

let headers = [
  "content-type": "application/json",
  "authorization": "Bearer BEARER_TOKEN_HERE"
]

let postData = NSData(data: "{"tags":["lake","water"],"title":"Blue Lake","description":"Blue Lake in the Winter","product":{"id":"LLBB77","name":"Blue Lake Card","brand":"BLUE LAKE LLC","category1":"Cards","category2":"Lakes"},"approval":{"approved":false,"comment":"It looks too cold!"}}".data(using: String.Encoding.utf8)!)

let request = NSMutableURLRequest(url: NSURL(string: "https://api.sirv.com/v2/files/meta")! as URL,
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
var client = new RestClient("https://api.sirv.com/v2/files/meta");
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("authorization", "Bearer BEARER_TOKEN_HERE");
request.AddParameter("application/json", "{\"tags\":[\"lake\",\"water\"],\"title\":\"Blue Lake\",\"description\":\"Blue Lake in the Winter\",\"product\":{\"id\":\"LLBB77\",\"name\":\"Blue Lake Card\",\"brand\":\"BLUE LAKE LLC\",\"category1\":\"Cards\",\"category2\":\"Lakes\"},\"approval\":{\"approved\":false,\"comment\":\"It looks too cold!\"}}", ParameterType.RequestBody);
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

	url := "https://api.sirv.com/v2/files/meta"

	payload := strings.NewReader("{\"tags\":[\"lake\",\"water\"],\"title\":\"Blue Lake\",\"description\":\"Blue Lake in the Winter\",\"product\":{\"id\":\"LLBB77\",\"name\":\"Blue Lake Card\",\"brand\":\"BLUE LAKE LLC\",\"category1\":\"Cards\",\"category2\":\"Lakes\"},\"approval\":{\"approved\":false,\"comment\":\"It looks too cold!\"}}")

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

Use this API method to set various meta fields at once.

### Query string


Parameter | Type | Description | Example
--------- | ---- | ----------- | ------- 
filename | string |  | /REST API Examples/blue-lake.jpg


### Body payload


Example:

<div class="center-column"></div>
```json
{
  "tags": [
    "lake",
    "water"
  ],
  "title": "Blue Lake",
  "description": "Blue Lake in the Winter",
  "product": {
    "id": "LLBB77",
    "name": "Blue Lake Card",
    "brand": "BLUE LAKE LLC",
    "category1": "Cards",
    "category2": "Lakes"
  },
  "approval": {
    "approved": false,
    "comment": "It looks too cold!"
  }
}
```




JSON Schema:

<div class="center-column"></div>
```json
{
  "type": "object",
  "properties": {
    "tags": {
      "type": "array",
      "examples": [
        [
          [
            "lake",
            "water"
          ]
        ]
      ],
      "maxItems": 50,
      "items": {
        "type": "string",
        "maxLength": 32
      }
    },
    "title": {
      "type": "string",
      "examples": [
        "Blue Lake"
      ],
      "maxLength": 256
    },
    "description": {
      "type": "string",
      "examples": [
        "Blue Lake in the Winter"
      ],
      "maxLength": 1024
    },
    "product": {
      "type": "object",
      "properties": {
        "id": {
          "type": "string",
          "examples": [
            "LLBB77"
          ],
          "maxLength": 256
        },
        "name": {
          "type": "string",
          "examples": [
            "Blue Lake Card"
          ],
          "maxLength": 256
        },
        "brand": {
          "type": "string",
          "examples": [
            "BLUE LAKE LLC"
          ],
          "maxLength": 256
        },
        "category1": {
          "type": "string",
          "examples": [
            "Cards"
          ],
          "maxLength": 256
        },
        "category2": {
          "type": "string",
          "examples": [
            "Lakes"
          ],
          "maxLength": 256
        }
      },
      "additionalProperties": false
    },
    "approval": {
      "type": "object",
      "properties": {
        "approved": {
          "type": "boolean",
          "examples": [
            false
          ]
        },
        "comment": {
          "type": "string",
          "examples": [
            "It looks too cold!"
          ],
          "maxLength": 256
        }
      },
      "required": [
        "approved"
      ],
      "additionalProperties": false
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
< date: Mon, 31 Jul 2023 10:36:06 GMT
< content-length: 0
< connection: close
< x-global-ratelimit-limit: 7000
< x-global-ratelimit-remaining: 6477
< x-global-ratelimit-reset: 1690800935
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< server: Sirv.API
< strict-transport-security: max-age=31536000

/ no response body: HTTP status 200 means SUCCESS /
```
