## Get API limits

```python
import http.client

conn = http.client.HTTPSConnection("api.sirv.com")

headers = {
    'content-type': "application/json",
    'authorization': "Bearer BEARER_TOKEN_HERE"
    }

conn.request("GET", "/v2/account/limits", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```shell
curl --request GET \\
  --url https://api.sirv.com/v2/account/limits \\
  --header 'authorization: Bearer BEARER_TOKEN_HERE' \\
  --header 'content-type: application/json'
```

```javascript--node
const http = require("https");

const options = {
  "method": "GET",
  "hostname": "api.sirv.com",
  "port": null,
  "path": "/v2/account/limits",
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

req.end();
```

```javascript
const data = null;

const xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "https://api.sirv.com/v2/account/limits");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("authorization", "Bearer BEARER_TOKEN_HERE");

xhr.send(data);
```

```java
HttpResponse<String> response = Unirest.get("https://api.sirv.com/v2/account/limits")
  .header("content-type", "application/json")
  .header("authorization", "Bearer BEARER_TOKEN_HERE")
  .asString();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, [
  CURLOPT_URL => "https://api.sirv.com/v2/account/limits",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
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

url = URI("https://api.sirv.com/v2/account/limits")

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

let request = NSMutableURLRequest(url: NSURL(string: "https://api.sirv.com/v2/account/limits")! as URL,
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
var client = new RestClient("https://api.sirv.com/v2/account/limits");
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

	url := "https://api.sirv.com/v2/account/limits"

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

Use this method to check the allowed number of API requests and the number of requests used in the past 60 minutes.

### Query string


None


### Body payload




None


### Response

Example response:

<div class="center-column"></div>
```
< HTTP/1.1 200
< date: Mon, 23 Feb 2026 14:07:32 GMT
< content-type: application/json; charset=utf-8
< content-length: 3593
< connection: close
< x-global-ratelimit-limit: 7000
< x-global-ratelimit-remaining: 6936
< x-global-ratelimit-reset: 1771858410
< access-control-allow-origin: *
< access-control-expose-headers: *
< cache-control: no-cache
< vary: accept-encoding
< accept-ranges: bytes
< server: Sirv.API
< strict-transport-security: max-age=31536000

{
  "s3:global": {
    "count": 0,
    "limit": 7000,
    "remaining": 7000,
    "reset": 1771859252
  },
  "s3:PUT": {
    "count": 0,
    "limit": 2000,
    "remaining": 2000,
    "reset": 1771859252
  },
  "s3:GET": {
    "count": 0,
    "limit": 3000,
    "remaining": 3000,
    "reset": 1771859252
  },
  "s3:DELETE": {
    "count": 0,
    "limit": 3000,
    "remaining": 3000,
    "reset": 1771859252
  },
  "rest:global": {
    "count": 64,
    "limit": 7000,
    "remaining": 6936,
    "reset": 1771858410
  },
  "rest:post:files:search": {
    "count": 1,
    "limit": 1000,
    "remaining": 999,
    "reset": 1771858422
  },
  "rest:post:files:search:scroll": {
    "count": 0,
    "limit": 2000,
    "remaining": 2000,
    "reset": 1771859252
  },
  "rest:post:files:video2spin": {
    "count": 1,
    "limit": 200,
    "remaining": 199,
    "reset": 1771858423
  },
  "rest:post:files:spin2video": {
    "count": 1,
    "limit": 200,
    "remaining": 199,
    "reset": 1771858426
  },
  "rest:post:files:upload": {
    "count": 0,
    "limit": 2000,
    "remaining": 2000,
    "reset": 1771859252
  },
  "rest:post:files:delete": {
    "count": 1,
    "limit": 3000,
    "remaining": 2999,
    "reset": 1771858504
  },
  "rest:post:files:batch:delete": {
    "count": 1,
    "limit": 25,
    "remaining": 24,
    "reset": 1771858518
  },
  "rest:post:account": {
    "count": 2,
    "limit": 50,
    "remaining": 48,
    "reset": 1771858410
  },
  "rest:post:account:fetching": {
    "count": 0,
    "limit": 50,
    "remaining": 50,
    "reset": 1771859252
  },
  "rest:get:stats:http": {
    "count": 1,
    "limit": 100,
    "remaining": 99,
    "reset": 1771858419
  },
  "rest:get:stats:storage": {
    "count": 1,
    "limit": 100,
    "remaining": 99,
    "reset": 1771858420
  },
  "rest:post:account:new": {
    "count": 0,
    "limit": 5,
    "remaining": 5,
    "reset": 1771859252
  },
  "rest:post:user:accounts": {
    "count": 0,
    "limit": 20,
    "remaining": 20,
    "reset": 1771859252
  },
  "rest:get:rest:credentials": {
    "count": 0,
    "limit": 50,
    "remaining": 50,
    "reset": 1771859252
  },
  "rest:post:video:toSpin": {
    "count": 0,
    "limit": 400,
    "remaining": 400,
    "reset": 1771859252
  },
  "rest:post:upload:toSirv": {
    "count": 0,
    "limit": 2000,
    "remaining": 2000,
    "reset": 1595076350
  },
  "ftp:global": {
    "count": 0,
    "limit": 10000,
    "remaining": 10000,
    "reset": 1771859252
  },
  "ftp:STOR": {
    "count": 0,
    "limit": 2000,
    "remaining": 2000,
    "reset": 1771859252
  },
  "ftp:RETR": {
    "count": 0,
    "limit": 3000,
    "remaining": 3000,
    "reset": 1771859252
  },
  "ftp:DELE": {
    "count": 0,
    "limit": 3000,
    "remaining": 3000,
    "reset": 1771859252
  },
  "fetch:file": {
    "count": 2,
    "limit": 1000,
    "remaining": 998,
    "reset": 1771858429
  },
  "fetch:largefile": {
    "count": 0,
    "limit": 10,
    "remaining": 10,
    "reset": 1771859252
  },
  "fetch:largetimeout": {
    "count": 0,
    "limit": 10,
    "remaining": 10,
    "reset": 1771859252
  },
  "zips2:create": {
    "count": 276737,
    "limit": 536870912000,
    "remaining": 536870635263,
    "reset": 1771858513
  }
}
```
