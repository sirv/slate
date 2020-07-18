## Fetch URL

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

payload = "[{\"url\":\"https://demo.sirv.com/aurora.jpg\",\"filename\":\"/REST API Examples/aurora.jpg\"},{\"url\":\"https://demo.sirv.com/missing.jpg\",\"filename\":\"/REST API Examples/missing.jpg\"}]"

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("POST", "/v2/files/fetch", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request POST \\
  --url https://api.sirv.com/v2/files/fetch \\
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \\
  --header 'content-type: application/json' \\
  --data '[{"url":"https://demo.sirv.com/aurora.jpg","filename":"/REST API Examples/aurora.jpg"},{"url":"https://demo.sirv.com/missing.jpg","filename":"/REST API Examples/missing.jpg"}]'
```

```javascript--node
var http = require("https");

var options = {
  "method": "POST",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/files/fetch",
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

req.write("[{\"url\":\"https://demo.sirv.com/aurora.jpg\",\"filename\":\"/REST API Examples/aurora.jpg\"},{\"url\":\"https://demo.sirv.com/missing.jpg\",\"filename\":\"/REST API Examples/missing.jpg\"}]");
req.end();
```

```javascript
var data = "[{\"url\":\"https://demo.sirv.com/aurora.jpg\",\"filename\":\"/REST API Examples/aurora.jpg\"},{\"url\":\"https://demo.sirv.com/missing.jpg\",\"filename\":\"/REST API Examples/missing.jpg\"}]";

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.sirv.com/v2/files/fetch");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.post("https://api.sirv.com/v2/files/fetch")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .body("[{\"url\":\"https://demo.sirv.com/aurora.jpg\",\"filename\":\"/REST API Examples/aurora.jpg\"},{\"url\":\"https://demo.sirv.com/missing.jpg\",\"filename\":\"/REST API Examples/missing.jpg\"}]")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.sirv.com/v2/files/fetch",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "[{\"url\":\"https://demo.sirv.com/aurora.jpg\",\"filename\":\"/REST API Examples/aurora.jpg\"},{\"url\":\"https://demo.sirv.com/missing.jpg\",\"filename\":\"/REST API Examples/missing.jpg\"}]",
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

url = URI("https://api.sirv.com/v2/files/fetch")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer BEARER_TOKEN_HERE'
request.body = "[{\"url\":\"https://demo.sirv.com/aurora.jpg\",\"filename\":\"/REST API Examples/aurora.jpg\"},{\"url\":\"https://demo.sirv.com/missing.jpg\",\"filename\":\"/REST API Examples/missing.jpg\"}]"

response = http.request(request)
puts response.read_body
```

```swift
import Foundation

let headers = [
  "content-type": "application/json",
  "authorization": "Bearer BEARER_TOKEN_HERE"
]

let postData = NSData(data: "[{"url":"https://demo.sirv.com/aurora.jpg","filename":"/REST API Examples/aurora.jpg"},{"url":"https://demo.sirv.com/missing.jpg","filename":"/REST API Examples/missing.jpg"}]".data(using: String.Encoding.utf8)!)

let request = NSMutableURLRequest(url: NSURL(string: "https://api.sirv.com/v2/files/fetch")! as URL,
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
var client = new RestClient("https://api.sirv.com/v2/files/fetch");
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("authorization", "Bearer BEARER_TOKEN_HERE");
request.AddParameter("application/json", "[{\"url\":\"https://demo.sirv.com/aurora.jpg\",\"filename\":\"/REST API Examples/aurora.jpg\"},{\"url\":\"https://demo.sirv.com/missing.jpg\",\"filename\":\"/REST API Examples/missing.jpg\"}]", ParameterType.RequestBody);
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

	url := "https://api.sirv.com/v2/files/fetch"

	payload := strings.NewReader("[{\"url\":\"https://demo.sirv.com/aurora.jpg\",\"filename\":\"/REST API Examples/aurora.jpg\"},{\"url\":\"https://demo.sirv.com/missing.jpg\",\"filename\":\"/REST API Examples/missing.jpg\"}]")

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

Use this API method to fetch a file(s) from a URL via HTTP and save it to your Sirv account. This can be any URL, either public or private (via HTTP authentication). In the url parameter, enter the full URL of the remote file. In the filename parameter, enter the folder path and filename where it should be saved e.g. /path/to/folder/new-filename.jpg.

### Query string


None


### Body payload


JSON Schema:

<div class="center-column"></div>
```json
{
  "examples": [
    [
      {
        "url": "https://demo.sirv.com/aurora.jpg",
        "filename": "/REST API Examples/aurora.jpg"
      },
      {
        "url": "https://demo.sirv.com/missing.jpg",
        "filename": "/REST API Examples/missing.jpg"
      }
    ]
  ],
  "example": [
    {
      "url": "https://demo.sirv.com/aurora.jpg",
      "filename": "/REST API Examples/aurora.jpg"
    },
    {
      "url": "https://demo.sirv.com/missing.jpg",
      "filename": "/REST API Examples/missing.jpg"
    }
  ],
  "type": "array",
  "maxItems": 20,
  "items": {
    "type": "object",
    "properties": {
      "url": {
        "type": "string",
        "maxLength": 1024
      },
      "filename": {
        "type": "string",
        "pattern": "^\\/",
        "maxLength": 1024
      },
      "auth": {
        "type": "object",
        "properties": {
          "username": {
            "type": "string",
            "maxLength": 256
          },
          "password": {
            "type": "string",
            "maxLength": 256
          }
        },
        "additionalProperties": false,
        "patterns": []
      },
      "wait": {
        "type": "boolean"
      }
    },
    "additionalProperties": false,
    "patterns": [],
    "required": [
      "url",
      "filename"
    ]
  }
}
```


### Response

Example response:

<div class="center-column"></div>
```
< HTTP/1.1 200
< date: Sat, 18 Jul 2020 09:52:04 GMT
< content-type: application/json; charset=utf-8
< content-length: 8542
< connection: close
< x-ratelimit-limit: 2000
< x-ratelimit-remaining: 1996
< x-ratelimit-reset: 1595068863
< x-ratelimit-type: rest:post:files:fetch
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< vary: accept-encoding
< server: Sirv.API
< strict-transport-security: max-age=31536000

[
  {
    "filename": "/REST API Examples/aurora.jpg",
    "success": true,
    "attempted": false,
    "attempts": [
      {
        "url": "https://demo.sirv.com/aurora.jpg",
        "initiator": {
          "type": "api",
          "remoteAddr": "176.105.166.4",
          "date": "2020-07-17T15:47:35.316Z"
        },
        "statusCode": 200,
        "headers": {
          "result": {
            "version": "HTTP/1.1",
            "code": 200,
            "reason": "OK"
          },
          "Date": "Fri, 17 Jul 2020 15:47:36 GMT",
          "Content-Type": "image/webp",
          "Content-Length": "201846",
          "Connection": "keep-alive",
          "Last-Modified": "Fri, 17 Jul 2020 15:47:36 GMT",
          "ETag": "\"5f11c818-31476\"",
          "Server": "Sirv.Imagination",
          "X-Sirv-Server": "c1-extra1-fireball-13",
          "X-Sirv-Cache": "MISS",
          "Access-Control-Allow-Origin": "*",
          "Access-Control-Allow-Headers": "*",
          "Expires": "Sun, 16 Aug 2020 15:47:36 GMT",
          "Cache-Control": "max-age=2592000",
          "X-Sirv-Meta-Width": "2500",
          "X-Sirv-Meta-Height": "1667",
          "X-Sirv-Shard": "c1-riak1",
          "X-Account-Id": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
          "X-File-VersionId": "5evxYG8lnBgeA7cGBRTZzq7JQolRYviN:0",
          "X-Account-Serial": "2020-06-15T19:18:53.901Z",
          "Accept-Ranges": "bytes"
        },
        "timing": {
          "ns": 0.007514,
          "connect": 0.007912,
          "start": 0.48724,
          "total": 0.489622
        },
        "date": "2020-07-17T15:47:36.712Z"
      }
    ],
    "retryAfter": "2020-07-18T15:47:36.712Z"
  },
  {
    "filename": "/REST API Examples/missing.jpg",
    "success": false,
    "attempted": false,
    "attempts": [
      {
        "url": "https://demo.sirv.com/missing.jpg",
        "initiator": {
          "type": "api",
          "remoteAddr": "176.105.166.4",
          "date": "2020-07-18T08:35:51.026Z"
        },
        "statusCode": 404,
        "headers": {
          "result": {
            "version": "HTTP/1.1",
            "code": 404,
            "reason": "Not Found"
          },
          "Date": "Sat, 18 Jul 2020 08:35:52 GMT",
          "Content-Type": "text/html; charset=utf-8",
          "Content-Length": "4140",
          "Connection": "keep-alive",
          "Vary": "Accept-Encoding",
          "X-Account-Id": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
          "X-Account-Serial": "2020-06-15T19:18:53.901Z",
          "ETag": "W/\"102c-wKpRt+Cg9Cnw/NpTSkF5+w\"",
          "X-Sirv-Cache": "MISS",
          "Server": "Sirv.Imagination",
          "X-Sirv-Server": "c1-extra1-fireball-15",
          "Access-Control-Allow-Origin": "*",
          "Access-Control-Allow-Headers": "*"
        },
        "timing": {
          "ns": 0.018986,
          "connect": 0.019303,
          "start": 0.103774,
          "total": 0.103829
        },
        "error": {
          "name": "Error",
          "message": "Request not successful: expected status code 200 but got 404"
        },
        "date": "2020-07-18T08:35:52.089Z"
      }
    ],
    "retryAfter": "2020-07-18T10:06:04.160Z"
  }
]
```
