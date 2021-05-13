## Search files

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

payload = "{\"query\":\"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\\\/.Trash\",\"sort\":{\"filename.raw\":\"asc\"},\"from\":0,\"size\":5}"

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
  --data '{"query":"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\\\/.Trash","sort":{"filename.raw":"asc"},"from":0,"size":5}'
```

```javascript--node
var http = require("https");

var options = {
  "method": "POST",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/files/search",
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

req.write("{\"query\":\"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\\\/.Trash\",\"sort\":{\"filename.raw\":\"asc\"},\"from\":0,\"size\":5}");
req.end();
```

```javascript
var data = "{\"query\":\"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\\\/.Trash\",\"sort\":{\"filename.raw\":\"asc\"},\"from\":0,\"size\":5}";

var xhr = new XMLHttpRequest();
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
  .body("{\"query\":\"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\\\/.Trash\",\"sort\":{\"filename.raw\":\"asc\"},\"from\":0,\"size\":5}")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.sirv.com/v2/files/search",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"query\":\"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\\\/.Trash\",\"sort\":{\"filename.raw\":\"asc\"},\"from\":0,\"size\":5}",
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

url = URI("https://api.sirv.com/v2/files/search")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer BEARER_TOKEN_HERE'
request.body = "{\"query\":\"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\\\/.Trash\",\"sort\":{\"filename.raw\":\"asc\"},\"from\":0,\"size\":5}"

response = http.request(request)
puts response.read_body
```

```swift
import Foundation

let headers = [
  "content-type": "application/json",
  "authorization": "Bearer BEARER_TOKEN_HERE"
]

let postData = NSData(data: "{"query":"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\/.Trash","sort":{"filename.raw":"asc"},"from":0,"size":5}".data(using: String.Encoding.utf8)!)

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
request.AddParameter("application/json", "{\"query\":\"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\\\/.Trash\",\"sort\":{\"filename.raw\":\"asc\"},\"from\":0,\"size\":5}", ParameterType.RequestBody);
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

	payload := strings.NewReader("{\"query\":\"extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\\\/.Trash\",\"sort\":{\"filename.raw\":\"asc\"},\"from\":0,\"size\":5}")

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
  "sort": {
    "filename.raw": "asc"
  },
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
      "examples": [
        "extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\/.Trash"
      ],
      "example": "extension:.jpg AND mtime:[now-30d TO now] AND -dirname:\\/.Trash",
      "type": "string",
      "maxLength": 1024
    },
    "sort": {
      "examples": [
        {
          "filename.raw": "asc"
        }
      ],
      "example": {
        "filename.raw": "asc"
      },
      "type": "object",
      "properties": {},
      "additionalProperties": true,
      "patterns": []
    },
    "from": {
      "examples": [
        0
      ],
      "example": 0,
      "type": "number",
      "maximum": 1000
    },
    "size": {
      "examples": [
        5
      ],
      "example": 5,
      "type": "number",
      "maximum": 100
    },
    "scroll": {
      "description": "Start a scrolling search.",
      "type": "boolean"
    }
  },
  "additionalProperties": false,
  "patterns": []
}
```


### Response

Example response:

<div class="center-column"></div>
```
< HTTP/1.1 200
< date: Thu, 13 May 2021 08:21:31 GMT
< content-type: application/json; charset=utf-8
< content-length: 4441
< connection: close
< x-ratelimit-limit: 1000
< x-ratelimit-remaining: 999
< x-ratelimit-reset: 1620897691
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
      "_index": "sirvfs-v3",
      "_type": "_doc",
      "_id": "248e197b4546afd4da9ccdb2ee0d30cf844ecf44",
      "_score": null,
      "_routing": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
      "_source": {
        "accountId": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
        "filename": "/REST API Examples/aurora-copy.jpg",
        "dirname": "/REST API Examples",
        "basename": "aurora-copy.jpg",
        "extension": ".jpg",
        "id": "RaxZM3sxunjRxsH7dUOU1KmBqASp3weH",
        "ctime": "2021-05-12T09:30:08.895Z",
        "mtime": "2021-05-12T09:30:09.806Z",
        "size": 201846,
        "contentType": "image/webp",
        "meta": {
          "width": 2500,
          "height": 1667,
          "format": "WEBP",
          "duration": 0,
          "EXIF": {
            "ModifyDate": "2020-01-29T17:12:45Z"
          }
        }
      },
      "sort": [
        "/REST API Examples/aurora-copy.jpg"
      ]
    },
    {
      "_index": "sirvfs-v3",
      "_type": "_doc",
      "_id": "4b57cdf35a3568220bb9ad7a6f62f0048c8b4ae1",
      "_score": null,
      "_routing": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
      "_source": {
        "accountId": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
        "filename": "/REST API Examples/aurora.jpg",
        "dirname": "/REST API Examples",
        "basename": "aurora.jpg",
        "extension": ".jpg",
        "id": "tkLbo0YuHJuBIEYj40lEUYRZZ8cLBGnF",
        "ctime": "2020-07-17T13:31:39.348Z",
        "mtime": "2021-05-12T09:30:05.386Z",
        "size": 201846,
        "contentType": "image/webp",
        "meta": {
          "width": 2500,
          "height": 1667,
          "format": "WEBP",
          "duration": 0,
          "EXIF": {
            "ModifyDate": "2020-01-29T17:12:45Z"
          }
        }
      },
      "sort": [
        "/REST API Examples/aurora.jpg"
      ]
    },
    {
      "_index": "sirvfs-v3",
      "_type": "_doc",
      "_id": "1945fa0032fbcc5df46e4af56ac1f75fc71ff38d",
      "_score": null,
      "_routing": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
      "_source": {
        "accountId": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
        "filename": "/REST API Examples/video/001.jpg",
        "dirname": "/REST API Examples/video",
        "basename": "001.jpg",
        "extension": ".jpg",
        "id": "IfnjioVCkRxIWPXrKi6gpHEVKx0KvFm4",
        "ctime": "2020-07-17T15:36:52.528Z",
        "mtime": "2021-05-12T09:29:49.907Z",
        "size": 279982,
        "contentType": "image/jpeg",
        "meta": {
          "width": 1372,
          "height": 1080,
          "format": "JPEG",
          "duration": 0
        }
      },
      "sort": [
        "/REST API Examples/video/001.jpg"
      ]
    },
    {
      "_index": "sirvfs-v3",
      "_type": "_doc",
      "_id": "61ebc8bf5a8ad3c092f29846afb14e988c4bddaa",
      "_score": null,
      "_routing": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
      "_source": {
        "accountId": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
        "filename": "/REST API Examples/video/002.jpg",
        "dirname": "/REST API Examples/video",
        "basename": "002.jpg",
        "extension": ".jpg",
        "id": "F100f2RQYtqc4lu8RE5DCKn2GvXqkuov",
        "ctime": "2020-07-17T15:36:52.520Z",
        "mtime": "2021-05-12T09:29:50.109Z",
        "size": 266295,
        "contentType": "image/jpeg",
        "meta": {
          "width": 1372,
          "height": 1080,
          "format": "JPEG",
          "duration": 0
        }
      },
      "sort": [
        "/REST API Examples/video/002.jpg"
      ]
    },
    {
      "_index": "sirvfs-v3",
      "_type": "_doc",
      "_id": "1f9171cb31bcc108a9df664b3ad60a495cc3c4f8",
      "_score": null,
      "_routing": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
      "_source": {
        "accountId": "sdulth0oi0t9zxpxqtxwkwvgipjgv6ud",
        "filename": "/REST API Examples/video/003.jpg",
        "dirname": "/REST API Examples/video",
        "basename": "003.jpg",
        "extension": ".jpg",
        "id": "To1IfJ0lftonDG6U2cI4IVTCU2LgNI4e",
        "ctime": "2020-07-17T15:36:52.551Z",
        "mtime": "2021-05-12T09:29:49.510Z",
        "size": 259954,
        "contentType": "image/jpeg",
        "meta": {
          "width": 1372,
          "height": 1080,
          "format": "JPEG",
          "duration": 0
        }
      },
      "sort": [
        "/REST API Examples/video/003.jpg"
      ]
    }
  ],
  "total": 256,
  "_relation": "eq"
}
```
