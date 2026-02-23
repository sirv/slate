## Search files

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

payload = "{\"query\":\"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\\\/.Trash\",\"from\":0,\"size\":5}"

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("POST", "/v2/files/search", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request POST \\
  --url https://api.sirv.com/v2/files/search \\
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \\
  --header 'content-type: application/json' \\
  --data '{"query":"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\\\/.Trash","from":0,"size":5}'
```

```javascript--node
const http = require("https");

const options = {
  "method": "POST",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/files/search",
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

req.write("{\"query\":\"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\\\/.Trash\",\"from\":0,\"size\":5}");
req.end();
```

```javascript
const data = "{\"query\":\"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\\\/.Trash\",\"from\":0,\"size\":5}";

const xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.sirv.com/v2/files/search");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.post("https://api.sirv.com/v2/files/search")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .body("{\"query\":\"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\\\/.Trash\",\"from\":0,\"size\":5}")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "https://api.sirv.com/v2/files/search",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"query\":\"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\\\/.Trash\",\"from\":0,\"size\":5}",
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

url = URI("https://api.sirv.com/v2/files/search")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer BEARER_TOKEN_HERE'
request.body = "{\"query\":\"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\\\/.Trash\",\"from\":0,\"size\":5}"

response = http.request(request)
puts response.read_body
```

```swift
import Foundation

let headers = [
  "content-type": "application/json",
  "authorization": "Bearer BEARER_TOKEN_HERE"
]

let postData = NSData(data: "{"query":"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\/.Trash","from":0,"size":5}".data(using: String.Encoding.utf8)!)

let request = NSMutableURLRequest(url: NSURL(string: "https://api.sirv.com/v2/files/search")! as URL,
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
var client = new RestClient("https://api.sirv.com/v2/files/search");
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("authorization", "Bearer BEARER_TOKEN_HERE");
request.AddParameter("application/json", "{\"query\":\"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\\\/.Trash\",\"from\":0,\"size\":5}", ParameterType.RequestBody);
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

	url := "https://api.sirv.com/v2/files/search"

	payload := strings.NewReader("{\"query\":\"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\\\/.Trash\",\"from\":0,\"size\":5}")

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

Use this API method to search for files based on one or more criteria: file name; folder path; file extension; content type; created/modified time; or with some specific meta information.

Up to 1000 results can be returned. If you need more results, use the scroll API method.

### Query string


None


### Body payload


Example:

<div class="center-column"></div>
```json
{
  "query": "extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\/.Trash",
  "from": 0,
  "size": 5
}
```




JSON Schema:

<div class="center-column"></div>
```json
{
  "type": "object",
  "properties": {
    "query": {
      "type": "string",
      "examples": [
        "extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\/.Trash"
      ],
      "maxLength": 1024
    },
    "sort": {
      "oneOf": [
        {
          "type": "object",
          "examples": [
            {
              "filename.raw": "asc"
            }
          ],
          "properties": {},
          "additionalProperties": false
        },
        {
          "type": "array",
          "items": {}
        }
      ]
    },
    "from": {
      "type": "number",
      "examples": [
        0
      ],
      "maximum": 1000
    },
    "size": {
      "type": "number",
      "examples": [
        5
      ],
      "maximum": 100
    },
    "scroll": {
      "type": "boolean",
      "description": "Start a scrolling search."
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
< date: Mon, 23 Feb 2026 14:07:47 GMT
< content-type: application/json; charset=utf-8
< content-length: 7705
< connection: close
< x-global-ratelimit-limit: 7000
< x-global-ratelimit-remaining: 6926
< x-global-ratelimit-reset: 1771858410
< x-ratelimit-limit: 1000
< x-ratelimit-remaining: 998
< x-ratelimit-reset: 1771858422
< x-ratelimit-type: rest:post:files:search
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< vary: accept-encoding
< server: Sirv.API
< strict-transport-security: max-age=31536000

{
  "hits": [
    {
      "_index": "sirvfs-v4",
      "_type": "_doc",
      "_id": "248e197b4546afd4da9ccdb2ee0d30cf844ecf44",
      "_score": 1.3096726,
      "_routing": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
      "_source": {
        "accountId": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
        "filename": "/REST API Examples/aurora-copy.jpg",
        "dirname": "/REST API Examples",
        "basename": "aurora-copy.jpg",
        "extension": ".jpg",
        "id": "boW27K3kkyWK5LbGvxeOb0Sx3IOO0JoU",
        "ctime": "2026-02-23T13:55:04.615Z",
        "mtime": "2026-02-23T13:55:04.653Z",
        "size": 260864,
        "contentType": "image/jpeg",
        "meta": {
          "width": 2500,
          "height": 1667,
          "format": "JPEG",
          "duration": 0,
          "EXIF": {
            "ModifyDate": "2020-01-29T17:12:45Z"
          },
          "ICC_Profile": {
            "ProfileDescription": "GIMP built-in sRGB"
          }
        }
      },
      "sort": [
        1.3096726,
        "/REST API Examples/aurora-copy.jpg",
        ".jpg"
      ]
    },
    {
      "_index": "sirvfs-v4",
      "_type": "_doc",
      "_id": "4b57cdf35a3568220bb9ad7a6f62f0048c8b4ae1",
      "_score": 1.3096726,
      "_routing": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
      "_source": {
        "accountId": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
        "filename": "/REST API Examples/aurora.jpg",
        "dirname": "/REST API Examples",
        "basename": "aurora.jpg",
        "extension": ".jpg",
        "id": "tkLbo0YuHJuBIEYj40lEUYRZZ8cLBGnF",
        "ctime": "2020-07-17T13:31:39.348Z",
        "mtime": "2026-02-23T10:22:34.659Z",
        "atime": "2026-02-12T07:43:18.986Z",
        "size": 260864,
        "contentType": "image/jpeg",
        "meta": {
          "width": 2500,
          "height": 1667,
          "format": "JPEG",
          "duration": 0,
          "EXIF": {
            "ModifyDate": "2020-01-29T17:12:45Z"
          },
          "ICC_Profile": {
            "ProfileDescription": "GIMP built-in sRGB"
          }
        }
      },
      "sort": [
        1.3096726,
        "/REST API Examples/aurora.jpg",
        ".jpg"
      ]
    },
    {
      "_index": "sirvfs-v4",
      "_type": "_doc",
      "_id": "1945fa0032fbcc5df46e4af56ac1f75fc71ff38d",
      "_score": 1.3096726,
      "_routing": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
      "_source": {
        "accountId": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
        "filename": "/REST API Examples/video/001.jpg",
        "dirname": "/REST API Examples/video",
        "basename": "001.jpg",
        "extension": ".jpg",
        "id": "IfnjioVCkRxIWPXrKi6gpHEVKx0KvFm4",
        "ctime": "2020-07-17T15:36:52.528Z",
        "mtime": "2026-02-23T13:53:45.111Z",
        "atime": "2025-07-11T12:09:49.940Z",
        "size": 264184,
        "contentType": "image/jpeg",
        "meta": {
          "width": 1372,
          "height": 1080,
          "format": "JPEG",
          "duration": 0
        }
      },
      "sort": [
        1.3096726,
        "/REST API Examples/video/001.jpg",
        ".jpg"
      ]
    }
  ],
  "total": 455,
  "_relation": "eq"
}
```
