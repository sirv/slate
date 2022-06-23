## Read folder contents

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("GET", "/v2/files/readdir?dirname=%2FREST%20API%20Examples", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \\
  --url 'https://api.sirv.com/v2/files/readdir?dirname=%2FREST%20API%20Examples' \\
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \\
  --header 'content-type: application/json'
```

```javascript--node
var http = require("https");

var options = {
  "method": "GET",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/files/readdir?dirname=%2FREST%20API%20Examples",
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

req.end();
```

```javascript
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "https://api.sirv.com/v2/files/readdir?dirname=%2FREST%20API%20Examples");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.get("https://api.sirv.com/v2/files/readdir?dirname=%2FREST%20API%20Examples")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.sirv.com/v2/files/readdir?dirname=%2FREST%20API%20Examples",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
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

url = URI("https://api.sirv.com/v2/files/readdir?dirname=%2FREST%20API%20Examples")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer BEARER_TOKEN_HERE'

response = http.request(request)
puts response.read_body
```

```swift
import Foundation

let headers = [
  "content-type": "application/json",
  "authorization": "Bearer BEARER_TOKEN_HERE"
]

let request = NSMutableURLRequest(url: NSURL(string: "https://api.sirv.com/v2/files/readdir?dirname=%2FREST%20API%20Examples")! as URL,
                                        cachePolicy: .useProtocolCachePolicy,
                                    timeoutInterval: 10.0)
request.httpMethod = "GET"
request.allHTTPHeaderFields = headers

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
var client = new RestClient("https://api.sirv.com/v2/files/readdir?dirname=%2FREST%20API%20Examples");
var request = new RestRequest(Method.GET);
request.AddHeader("content-type", "application/json");
request.AddHeader("authorization", "Bearer BEARER_TOKEN_HERE");
IRestResponse response = client.Execute(request);
```

```go
package main

import (
  "fmt"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "https://api.sirv.com/v2/files/readdir?dirname=%2FREST%20API%20Examples"

  req, _ := http.NewRequest("GET", url, nil)

  req.Header.Add("content-type", "application/json")
  req.Header.Add("authorization", "Bearer BEARER_TOKEN_HERE")

  res, _ := http.DefaultClient.Do(req)

  defer res.Body.Close()
  body, _ := ioutil.ReadAll(res.Body)

  fmt.Println(res)
  fmt.Println(string(body))

}
```

Use this API method to get a list of all the files/folders within a folder. It will return the filename, mimetype, content type and file size. It will also return any folders that exist. A page of up to 100 results will be returned - use the 'continuation' field to request additional pages.

### Query string


Parameter | Type | Description | Example
--------- | ---- | ----------- | -------
dirname | string |  | /REST API Examples
continuation | string | Send it to get next page of results |


### Body payload




None


### Response

Example response:

<div class="center-column"></div>
```
< HTTP/1.1 200
< date: Thu, 23 Jun 2022 17:17:35 GMT
< content-type: application/json; charset=utf-8
< content-length: 2250
< connection: close
< x-ratelimit-limit: 7000
< x-ratelimit-remaining: 6967
< x-ratelimit-reset: 1656008218
< x-ratelimit-type: rest:global
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< vary: accept-encoding
< accept-ranges: bytes
< server: Sirv.API
< strict-transport-security: max-age=31536000

{
  "contents": [
    {
      "filename": "aurora3.jpg",
      "mtime": "2020-11-18T19:55:13.459Z",
      "contentType": "image/webp",
      "size": 201846,
      "isDirectory": false,
      "meta": {
        "width": 2500,
        "height": 1667,
        "duration": 0
      }
    },
    {
      "filename": "aurora.jpg",
      "mtime": "2022-06-23T17:17:32.585Z",
      "contentType": "image/webp",
      "size": 201846,
      "isDirectory": false,
      "meta": {
        "width": 2500,
        "height": 1667,
        "duration": 0
      }
    },
    {
      "filename": "birdbath.jpg",
      "mtime": "2020-07-17T13:31:39.385Z",
      "contentType": "image/jpeg",
      "size": 73151,
      "isDirectory": false,
      "meta": {
        "width": 620,
        "height": 372,
        "duration": 0
      }
    },
    {
      "filename": "video.mp4",
      "mtime": "2020-07-17T15:35:20.375Z",
      "contentType": "video/mp4",
      "size": 12860989,
      "isDirectory": false,
      "meta": {
        "width": 1372,
        "height": 1080,
        "duration": 33.434
      }
    },
    {
      "filename": "video",
      "mtime": "2020-07-17T15:36:52.477Z",
      "size": 0,
      "isDirectory": true,
      "meta": {}
    },
    {
      "filename": "uploaded.txt",
      "mtime": "2022-06-23T17:17:34.898Z",
      "contentType": "text/plain",
      "size": 0,
      "isDirectory": false,
      "meta": {}
    },
    {
      "filename": "coin",
      "mtime": "2020-07-17T13:31:08.833Z",
      "size": 0,
      "isDirectory": true,
      "meta": {}
    },
    {
      "filename": "copies",
      "mtime": "2020-12-09T09:40:13.049Z",
      "size": 0,
      "isDirectory": true,
      "meta": {}
    },
    {
      "filename": "blue-lake.jpg",
      "mtime": "2020-07-17T13:31:39.450Z",
      "contentType": "image/jpeg",
      "size": 587065,
      "isDirectory": false,
      "meta": {
        "width": 1578,
        "height": 1002,
        "duration": 0
      }
    },
    {
      "filename": "aurora-copy.jpg",
      "mtime": "2022-06-23T17:17:35.452Z",
      "contentType": "image/webp",
      "size": 201846,
      "isDirectory": false,
      "meta": {
        "width": 2500,
        "height": 1667,
        "duration": 0
      }
    }
  ]
}
```
